<properties
	pageTitle="Web API を使用した現在のユーザーのプッシュ通知への登録 | Microsoft Azure"
	description="ASP.NET Web API により登録が実行されるときに、iOS アプリケーションで Azure Notification Hubs へのプッシュ通知登録を要求する方法について説明します。"
	services="notification-hubs"
	documentationCenter="ios"
	authors="wesmc7777"
	manager="erikre"
	editor=""/>

<tags
	ms.service="notification-hubs"
	ms.workload="mobile"
	ms.tgt_pltfrm="ios"
	ms.devlang="objective-c"
	ms.topic="article"
	ms.date="06/29/2016"
	ms.author="wesmc"/>

# ASP.NET を使用した現在のユーザーのプッシュ通知への登録

> [AZURE.SELECTOR]
- [iOS](notification-hubs-ios-aspnet-register-user-push-notifications.md)



##概要

このトピックでは、ASP.NET Web API により登録が実行されるときに Azure Notification Hubs を使用してプッシュ通知登録を要求する方法について説明します。このトピックは、チュートリアル「[Notification Hubs によるユーザーへの通知]」を拡張したものです。認証されたモバイル サービスを作成するには、このチュートリアルの必要な手順を既に完了している必要があります。ユーザー通知シナリオの詳細については、「[Notification Hubs によるユーザーへの通知]」を参照してください。

##アプリケーションを更新する  

1. MainStoryboard\_iPhone.storyboard で、オブジェクト ライブラリから次のコンポーネントを追加します。

	+ **ラベル**: "Push to User with Notification Hubs"
	+ **ラベル**: "InstallationId"
	+ **ラベル**: "User"
	+ **テキスト フィールド**: "User"
	+ **ラベル**: "Password"
	+ **テキスト フィールド**: "Password"
	+ **ボタン**: "Login"

	この時点で、ストーリーボードは次のようになります。

   	![][0]

2. アシスタント エディターで、すべての switched コントロールのアウトレットを作成してそれらを呼び出し、テキスト フィールドとビュー コントローラー (デリゲート) を接続して、**ログイン** ボタンの**アクション**を作成します。

   	![][1]

   	この時点で、BreakingNewsViewController.h ファイルには次のコードが含まれています。

		@property (weak, nonatomic) IBOutlet UILabel *installationId;
		@property (weak, nonatomic) IBOutlet UITextField *User;
		@property (weak, nonatomic) IBOutlet UITextField *Password;

		- (IBAction)login:(id)sender;

5. **DeviceInfo** という名前のクラスを作成し、次のコードを DeviceInfo.h ファイルの interface セクションにコピーします。

		@property (readonly, nonatomic) NSString* installationId;
		@property (nonatomic) NSData* deviceToken;

6. DeviceInfo.m ファイルの implementation セクションに次のコードをコピーします。

			@synthesize installationId = _installationId;

			- (id)init {
			    if (!(self = [super init]))
					return nil;

			    NSUserDefaults *defaults = [NSUserDefaults standardUserDefaults];
			    _installationId = [defaults stringForKey:@"PushToUserInstallationId"];
			    if(!_installationId) {
			        CFUUIDRef newUUID = CFUUIDCreate(kCFAllocatorDefault);
			        _installationId = (__bridge_transfer NSString *)CFUUIDCreateString(kCFAllocatorDefault, newUUID);
			        CFRelease(newUUID);

			        //store the install ID so we don't generate a new one next time
			        [defaults setObject:_installationId forKey:@"PushToUserInstallationId"];
			        [defaults synchronize];
			    }

			    return self;
			}

			- (NSString*)getDeviceTokenInHex {
			    const unsigned *tokenBytes = [[self deviceToken] bytes];
			    NSString *hexToken = [NSString stringWithFormat:@"%08X%08X%08X%08X%08X%08X%08X%08X",
			                          ntohl(tokenBytes[0]), ntohl(tokenBytes[1]), ntohl(tokenBytes[2]),
			                          ntohl(tokenBytes[3]), ntohl(tokenBytes[4]), ntohl(tokenBytes[5]),
			                          ntohl(tokenBytes[6]), ntohl(tokenBytes[7])];
			    return hexToken;
			}

7. PushToUserAppDelegate.h で、次のプロパティ シングルトンを追加します。

		@property (strong, nonatomic) DeviceInfo* deviceInfo;

8. PushToUserAppDelegate.m の **didFinishLaunchingWithOptions** メソッドで、次のコードを追加します。

		self.deviceInfo = [[DeviceInfo alloc] init];

		[[UIApplication sharedApplication] registerForRemoteNotificationTypes: UIRemoteNotificationTypeAlert | UIRemoteNotificationTypeBadge | UIRemoteNotificationTypeSound];

	最初の行では、**DeviceInfo** シングルトンが初期化されます。2 行目では、プッシュ通知の登録が開始されます。チュートリアル「[Notification Hubs の使用]」を既に終えている場合、この登録は既に存在しています。

9. PushToUserAppDelegate.m で、AppDelegate に **didRegisterForRemoteNotificationsWithDeviceToken** メソッドを実装し、次のコードを追加します。

		self.deviceInfo.deviceToken = deviceToken;

	これにより、要求のデバイス トークンが設定されます。

	> [AZURE.NOTE] この時点では、このメソッドに他のコードは存在しません。チュートリアル「[Notification Hubs の使用](/manage/services/notification-hubs/get-started-notification-hubs-ios/)」を完了したときに追加された **registerNativeWithDeviceToken** メソッドへの呼び出しが既にある場合、その呼び出しをコメント解除するか、削除する必要があります。

10.	PushToUserAppDelegate.m ファイルで、次のハンドラー メソッドを追加します。

		- (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo {
		    NSLog(@"%@", userInfo);
		    UIAlertView *alert = [[UIAlertView alloc] initWithTitle:@"Notification" message:
		                          [userInfo objectForKey:@"inAppMessage"] delegate:nil cancelButtonTitle:
		                          @"OK" otherButtonTitles:nil, nil];
		    [alert show];
		}

	 アプリケーションが実行中に通知を受信すると、このメソッドは UI にアラートを表示します。

9. PushToUserViewController.m ファイルを開き、次の実装でキーボードを返します。

		- (BOOL)textFieldShouldReturn:(UITextField *)theTextField {
		    if (theTextField == self.User || theTextField == self.Password) {
		        [theTextField resignFirstResponder];
		    }
		    return YES;
		}

9. PushToUserViewController.m ファイルの **viewDidLoad** メソッドで、次のように installationId ラベルを初期化します。

		DeviceInfo* deviceInfo = [(PushToUserAppDelegate*)[[UIApplication sharedApplication]delegate] deviceInfo];
		Self.installationId.text = deviceInfo.installationId;

10. PushToUserViewController.m の interface に次のプロパティを追加します。

		@property (readonly) NSOperationQueue* downloadQueue;
		- (NSString*)base64forData:(NSData*)theData;

11. その後、次の実装を追加します。

			- (NSOperationQueue *)downloadQueue {
			    if (!_downloadQueue) {
			        _downloadQueue = [[NSOperationQueue alloc] init];
			        _downloadQueue.name = @"Download Queue";
			        _downloadQueue.maxConcurrentOperationCount = 1;
			    }
			    return _downloadQueue;
			}

			// base64 encoding
			- (NSString*)base64forData:(NSData*)theData
			{
			    const uint8_t* input = (const uint8_t*)[theData bytes];
			    NSInteger length = [theData length];

			    static char table[] = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/=";

			    NSMutableData* data = [NSMutableData dataWithLength:((length + 2) / 3) * 4];
			    uint8_t* output = (uint8_t*)data.mutableBytes;

			    NSInteger i;
			    for (i=0; i < length; i += 3) {
			        NSInteger value = 0;
			        NSInteger j;
			        for (j = i; j < (i + 3); j++) {
			            value <<= 8;

			            if (j < length) {
			                value |= (0xFF & input[j]);
			            }
			        }

			        NSInteger theIndex = (i / 3) * 4;
			        output[theIndex + 0] =                    table[(value >> 18) & 0x3F];
			        output[theIndex + 1] =                    table[(value >> 12) & 0x3F];
			        output[theIndex + 2] = (i + 1) < length ? table[(value >> 6)  & 0x3F] : '=';
			        output[theIndex + 3] = (i + 2) < length ? table[(value >> 0)  & 0x3F] : '=';
			    }

			    return [[NSString alloc] initWithData:data encoding:NSASCIIStringEncoding];
			}


12. XCode により作成された **login** ハンドラー メソッドに次のコードをコピーします。

			DeviceInfo* deviceInfo = [(PushToUserAppDelegate*)[[UIApplication sharedApplication]delegate] deviceInfo];

		    // build JSON
		    NSString* json = [NSString stringWithFormat:@"{"platform":"ios", "instId":"%@", "deviceToken":"%@"}", deviceInfo.installationId, [deviceInfo getDeviceTokenInHex]];

		    // build auth string
		    NSString* authString = [NSString stringWithFormat:@"%@:%@", self.User.text, self.Password.text];

		    NSMutableURLRequest* request = [NSMutableURLRequest requestWithURL:[NSURL URLWithString:@"http://nhnotifyuser.azurewebsites.net/api/register"]];
		    [request setHTTPMethod:@"POST"];
		    [request setHTTPBody:[json dataUsingEncoding:NSUTF8StringEncoding]];
		    [request addValue:[@([json lengthOfBytesUsingEncoding:NSUTF8StringEncoding]) description] forHTTPHeaderField:@"Content-Length"];
		    [request addValue:@"application/json" forHTTPHeaderField:@"Content-Type"];
		    [request addValue:[NSString stringWithFormat:@"Basic %@",[self base64forData:[authString dataUsingEncoding:NSUTF8StringEncoding]]] forHTTPHeaderField:@"Authorization"];

		    // connect with POST
		    [NSURLConnection sendAsynchronousRequest:request queue:[self downloadQueue] completionHandler:^(NSURLResponse* response, NSData* data, NSError* error) {
		        // add UIAlert depending on response.
		        if (error != nil) {
		            NSHTTPURLResponse* httpResponse = (NSHTTPURLResponse*)response;
		            if ([httpResponse statusCode] == 200) {
		                UIAlertView *alert = [[UIAlertView alloc] initWithTitle:@"Back-end registration" message:@"Registration successful" delegate:nil cancelButtonTitle: @"OK" otherButtonTitles:nil, nil];
		                [alert show];
		            } else {
		                NSLog(@"status: %ld", (long)[httpResponse statusCode]);
		            }
		        } else {
		            NSLog(@"error: %@", error);
		        }
		    }];

	このメソッドは、プッシュ通知のインストール ID とチャネルの両方を取得します。これらの ID とチャネルは、デバイスの種類と共に、Notification Hubs で登録を作成する認証済みの Web API メソッドに送信されます。この Web API は、「[Notification Hubs によるユーザーへの通知]」で定義されたものです。

これで、クライアント アプリケーションが更新されました。「[Notification Hubs によるユーザーへの通知]」に戻り、Notification Hubs を使用することで通知を送信するようにモバイル サービスを更新します。

<!-- Anchors. -->

<!-- Images. -->
[0]: ./media/notification-hubs-ios-aspnet-register-user-push-notifications/notification-hub-user-aspnet-ios1.png
[1]: ./media/notification-hubs-ios-aspnet-register-user-push-notifications/notification-hub-user-aspnet-ios2.png

<!-- URLs. -->
[Notification Hubs によるユーザーへの通知]: /manage/services/notification-hubs/notify-users-aspnet

[Notification Hubs の使用]: /manage/services/notification-hubs/get-started-notification-hubs-ios

<!---HONumber=AcomDC_0706_2016-->