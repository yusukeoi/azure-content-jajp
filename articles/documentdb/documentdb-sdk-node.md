<properties 
	pageTitle="DocumentDB Node.js API と SDK | Microsoft Azure" 
	description="リリース日、提供終了日、DocumentDB Node.js SDK の各バージョン間の変更など、Node.js API と SDK に関するあらゆる詳細を提供します。" 
	services="documentdb" 
	documentationCenter="nodejs" 
	authors="rnagpal" 
	manager="jhubbard" 
	editor="cgronlun"/>

<tags 
	ms.service="documentdb" 
	ms.workload="data-services" 
	ms.tgt_pltfrm="na" 
	ms.devlang="nodejs" 
	ms.topic="article" 
	ms.date="08/09/2016" 
	ms.author="rnagpal"/>

# DocumentDB API と SDK

> [AZURE.SELECTOR]
- [.NET](documentdb-sdk-dotnet.md)
- [Node.JS](documentdb-sdk-node.md)
- [Java](documentdb-sdk-java.md)
- [Python](documentdb-sdk-python.md)
- [REST ()](https://go.microsoft.com/fwlink/?LinkId=402413)
- [SQL](https://msdn.microsoft.com/library/azure/dn782250.aspx)

##DocumentDB Node.js API と SDK

<table>
<tr><td>**SDK のダウンロード**</td><td>[NPM](https://www.npmjs.com/package/documentdb)</td></tr>
<tr><td>**API ドキュメント**</td><td>[Node.js API リファレンス ドキュメント](http://azure.github.io/azure-documentdb-node/DocumentClient.html)</td></tr>
<tr><td>**SDK のインストール手順**</td><td>[インストール手順](http://azure.github.io/azure-documentdb-node/)</td></tr>
<tr><td>**SDK への協力**</td><td>[GitHub](https://github.com/Azure/azure-documentdb-node/tree/master/source)</td></tr>
<tr><td>**サンプル**</td><td>[Node.js コード サンプル](documentdb nodejs samples.md)</td></tr>
<tr><td>**入門チュートリアル**</td><td>[Node.js SDK の概要](documentdb-nodejs-get-started.md)</td></tr>
<tr><td>**Web アプリ チュートリアル**</td><td>[DocumentDB を使用した Node.js Web アプリケーションの作成](documentdb-nodejs-application.md)</td></tr>
<tr><td>**現在サポートされているプラットフォーム**</td><td>[Node.js v0.10](https://nodejs.org/en/blog/release/v0.10.0/)<br/>[Node.js v0.12](https://nodejs.org/en/blog/release/v0.12.0/)<br/>[Node.js v4.2.0](https://nodejs.org/en/blog/release/v4.2.0/)</td></tr>
</table></br>

##リリース ノート

###<a name="1.9.0"/>1.9.0</a>

- スロットルされた要求のための再試行ポリシー サポートを追加しました (スロットルされた要求は、要求レートが大きすぎるという例外をエラー コード 429 で受信します)。 既定では、DocumentDB は、エラー コード 429 が発生した場合に、応答ヘッダーの retryAfter 回数に従って要求ごとに 9 回再試行します。再試行の間にサーバーによって返される retryAfter 回数を無視する場合、固定の再試行間隔の回数を、ConnectionPolicy オブジェクトの RetryOptions プロパティの一部としてここで設定できます。DocumentDB では、(再試行の回数に関係なく) スロットルされる要求ごとに最大 30 秒待機できるようになり、エラー コード 429 と共に応答を返すようになりました。この回数は、ConnectionPolicy オブジェクトの RetryOptions プロパティでオーバーライドすることもできます。

- DocumentDB は、スロットルの再試行の回数と再試行の間の要求の累積待機時間を表すために、すべての要求の応答ヘッダーとして x-ms-throttle-retry-count と x-ms-throttle-retry-wait-time-ms を返すようになりました。

- ConnectionPolicy クラスの RetryOptions プロパティを公開する、RetryOptions クラスが追加されました。これは、一部の既定の再試行オプションをオーバーライドするために使用できます。

###<a name="1.8.0"/>1.8.0</a>

 - 複数リージョンのデータベース アカウントのサポートを追加しました。

###<a name="1.7.0"/>1.7.0</a>

- ドキュメントの有効期限 (TTL) 機能のサポートを追加しました。

###<a name="1.6.0"/>1.6.0</a>

- [パーティション分割コレクション](documentdb-partition-data.md)と[ユーザー定義のパフォーマンス レベル](documentdb-performance-levels.md)を実装しました。

###<a name="1.5.6"/>1.5.6</a>

- 結果の不適切な連結のためにリンクを返していなかった RangePartitionResolver.resolveForRead のバグを修正しました。

###<a name="1.5.5"/>1.5.5</a>

- hashParitionResolver resolveForRead() を修正しました - 登録済みのすべてのリンクの一覧を返す代わりに、指定したパーティション キーが例外をスローしない問題を修正しました。

###<a name="1.5.4"/>1.5.4</a>

- 問題 [#100](https://github.com/Azure/azure-documentdb-node/issues/100) を修正します - 専用 HTTPS エージェント: DocumentDB 目的用のグローバル エージェントが変更されないようにします。lib のすべての要求に対して、専用エージェントを使用します。

###<a name="1.5.3"/>1.5.3</a>

- 問題 [#81](https://github.com/Azure/azure-documentdb-node/issues/81) を修正します - メディア ID のダッシュを正しく処理します。

###<a name="1.5.2"/>1.5.2</a>

- 問題 [#95](https://github.com/Azure/azure-documentdb-node/issues/95) を修正します - EventEmitter リスナー リーク警告の問題を修正します。

###<a name="1.5.1"/>1.5.1</a>

- 問題 [#92](https://github.com/Azure/azure-documentdb-node/issues/90) を修正します - 大文字小文字を区別するシステムのため、Hash フォルダーの名前を hash に変更します。

### <a name="1.5.0"/>1.5.0</a>

- ハッシュと範囲パーティション リゾルバーを追加することでシャーディングのサポートを実装。

### <a name="1.4.0"/>1.4.0</a>

- Upsert を実装します。documentClient の新しい upsertXXX メソッド

### <a name="1.3.0"/>1.3.0</a>

- 他の SDK とバージョン番号をそろえるため、このリリースはスキップされました。

### <a name="1.2.2"/>1.2.2</a>

- Q promises ラッパーを新しいリポジトリに分割します。
- 更新し、npm レジストリのファイルをパッケージ化します。

### <a name="1.2.1"/>1.2.1</a>

- ID ベースのルーティングを実装します。
- 問題 [#49](https://github.com/Azure/azure-documentdb-node/issues/49) を修正します - 現在のプロパティがメソッド current() と競合します。

### <a name="1.2.0"/>1.2.0</a>

- 地理空間インデックスのサポートを追加しました。
- すべてのリソースの id プロパティを検証します。リソースの ID には ?、/、#、&#47;&#47; 文字を使えず、終わりの文字をスペースにできません。
- ResourceResponse に新しいヘッダーの「インデックス変換の進行状況」を追加します。

### <a name="1.1.0"/>1.1.0</a>

- V2 インデックス作成ポリシーを実装します。

### <a name="1.0.3"/>1.0.3</a>

- 問題 [#40](https://github.com/Azure/azure-documentdb-node/issues/40) - core および promise SDK で eslint および grunt 構成を実装しました。

### <a name="1.0.2"/>1.0.2</a>

- 問題 [#45](https://github.com/Azure/azure-documentdb-node/issues/45) - promise ラッパーには、エラーのあるヘッダーが含まれません。

### <a name="1.0.1"/>1.0.1</a>

- readConflicts、readConflictAsync、queryConflicts を追加し、競合に関して問い合わせる機能を実装しました。
- API ドキュメントを更新しました。
- 問題 [#41](https://github.com/Azure/azure-documentdb-node/issues/41) - client.createDocumentAsync エラー。

### <a name="1.0.0"/>1.0.0</a>

- GA SDK。

## リリース日と提供終了日
Microsoft は、新しい/サポートされるバージョンに速やかに移行する目的で、SDK の提供終了を少なくともその **12 か月**前に通知します。

新しい機能と最適化は現在の SDK にのみ追加されます。そのため、常に可能な限り最新の SDK バージョンにアップグレードすることが推奨されます。

提供終了の SDK で DocumentDB に要求した場合、サービスにより却下されます。

> [AZURE.WARNING]
バージョン **1.0.0** 以前のすべてのバージョンの Azure DocumentDB SDK for Node.js は **2016 年 2 月 29 日**で提供が終了します。

<br/>

| バージョン | リリース日 | 提供終了日 
| ---	  | ---	         | ---
| [1\.8.0](#1.8.0) | 2016 年 6 月 14 日 |--- 
| [1\.7.0](#1.7.0) | 2016 年 4 月 26 日 |--- 
| [1\.6.0](#1.6.0) | 2016 年 3 月 29 日 |--- 
| [1\.5.6](#1.5.6) | 2016 年 3 月 08 日 |--- 
| [1\.5.5](#1.5.5) | 2016 年 2 月 02 日 |--- 
| [1\.5.4](#1.5.4) | 2016 年 2 月 01 日 |--- 
| [1\.5.2](#1.5.2) | 2016 年 1 月 26 日 |--- 
| [1\.5.2](#1.5.2) | 2016 年 1 月 22 日 |--- 
| [1\.5.1](#1.5.1) | 2016 年 1 月 04 日 |--- 
| [1\.5.0](#1.5.0) | 2015 年 12 月 31 日 |--- 
| [1\.4.0](#1.4.0) | 2015 年 10 月 06 日 |--- 
| [1\.3.0](#1.3.0) | 2015 年 10 月 06 日 |--- 
| [1\.2.2](#1.2.2) | 2015 年 9 月 10 日 |--- 
| [1\.2.1](#1.2.1) | 2015 年 8 月 15 日 |--- 
| [1\.2.0](#1.2.0) | 2015 年 8 月 05 日 |--- 
| [1\.1.0](#1.1.0) | 2015 年 7 月 09 日 |--- 
| [1\.0.3](#1.0.3) | 2015 年 6 月 04 日 |--- 
| [1\.0.2](#1.0.2) | 2015 年 5 月 23 日 |--- 
| [1\.0.1](#1.0.1) | 2015 年 5 月 15 日 |--- 
| [1\.0.0](#1.0.0) | 2015 年 4 月 08 日 |--- 
|0.9.4-prelease | 2015 年 4 月 06 日 | 2016 年 2 月 29 日 
| 0.9.3-prelease | 2015 年 1 月 14 日 | 2016 年 2 月 29 日 
| 0.9.2-prelease | 2014 年 12 月 18 日 | 2016 年 2 月 29 日 
| 0.9.1-prelease | 2014 年 8 月 22 日 | 2016 年 2 月 29 日 
| 0.9.0-prelease | 2014 年 8 月 21 日 | 2016 年 2 月 29 日


## FAQ
[AZURE.INCLUDE [documentdb-sdk-faq](../../includes/documentdb-sdk-faq.md)]

## 関連項目

DocumentDB に関する詳細は、[Microsoft Azure DocumentDB](https://azure.microsoft.com/services/documentdb/) サービス ページを参照してください。

<!---HONumber=AcomDC_0810_2016-->