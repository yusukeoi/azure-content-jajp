<properties
   pageTitle="FAQ"
   description="Power BI Embedded FAQ"
   services="power-bi-embedded"
   documentationCenter=""
   authors="minewiskan"
   manager="NA"
   editor=""
   tags=""/>
<tags
   ms.service="power-bi-embedded"
   ms.devlang="NA"
   ms.topic="article"
   ms.tgt_pltfrm="NA"
   ms.workload="powerbi"
   ms.date="07/05/2016"
   ms.author="owend"/>

# Power BI Embedded FAQ

## Power BI Embedded に関する最新情報は何ですか。

標準の GA SLA が適用された Microsoft Power BI Embedded サービスが一般公開されました。このリリースの詳細については、[新機能](power-bi-embedded-whats-new.md)に関する記事をご覧ください。

## Microsoft Power BI Embedded とは何ですか?

Microsoft Power BI Embedded が一般公開されました。Power BI Embedded は、アプリケーション開発者が時間とコストをかけて独自のコントロールをゼロから構築しなくても、完全に対話型の魅力的なレポートや視覚エフェクトを顧客向けアプリケーションに埋め込むことができる Azure サービスです。世界 9 か所のデータ センターで、SLA が適用された Power BI Embedded が提供されるようになりました。高度なフィルター処理を実現する Power BI Embedded の行レベルのセキュリティ (RLS) によるデータ セキュリティのサポートなど、サービスの機能も強化されています。また、Power BI Embedded の価格モデルが簡素化され、更新されました。詳細については、「[Power BI Embedded](https://azure.microsoft.com/services/power-bi-embedded/)」をご覧ください。

## 誰が Microsoft Power BI Embedded を使用するのですか? また、その理由を教えてください。

Microsoft Power BI Embedded は、視覚エフェクトを独自に構築することなく、あらゆるデバイスで魅力的な対話型のデータ視覚エフェクト エクスペリエンスを提供したいと考えているアプリケーション開発者を対象としています。Power BI Embedded を使用することで、開発者は直接クエリで常に最新のビューを提供できます。また、開発者は、Azure ARM API や Power BI API を使用して、Power BI をプログラムによってデプロイ、管理、自動化することもできます。その他のサービスと同様に、Power BI Embedded サービスは、使用状況とアプリケーションのニーズに応じて、自動的に拡張します。Power BI Embedded サービスは、従量課金ベースの価格モデルを特徴としています。

## Power BI Embedded は Power BI サービスとどのように関連していますか?

Power BI Embedded と Power BI サービスは別個のサービスです。Power BI Embedded は、Azure ポータルを通じてデプロイされる、使用量ベースの課金モデルを特徴としており、ISV がデータの視覚エフェクトを顧客向けのアプリケーションへ埋め込むことを可能にするよう設計されています。Power BI サービスは O365 ポータルを通して請求およびデプロイが行われ、主に企業による内部使用を対象とするスタンドアロンの汎用 BI サービスです。Power BI サービスの詳細については、[https://powerbi.microsoft.com/ja-jp/](https://powerbi.microsoft.com) をご覧ください。

## Power BI Embedded はどのようにアプリを強化するのですか?

魅力的な対話型のデータ視覚エフェクトを活用して、アプリケーション内でユーザーに決定事項を直接通知できれば、アプリケーションは大幅に強化されます。Power BI Embedded を使用することで、対話形式の、常に最新かつ豊富なデータの視覚エフェクトを使用してアプリケーションを強化できます。これにより、アプリの有用性、ユーザーの満足度とロイヤルティを向上させ、容易に任意のデバイスへコンテキスト分析機能を提供します。

## Power BI Embedded をアプリで使用するにあたって、規則または制限はありますか。

Power BI Embedded は、サード パーティ向けに提供されるアプリケーションを対象としています。Power BI Embedded サービスを使用して社内のビジネス アプリケーションを作成する場合は、各内部ユーザーに Power BI Pro の USL が必要であり、組織には Power BI Pro の USL の料金に加え、Power BI Embedded サービスの使用分が課金されます。内部アプリケーションに対して Power BI Pro の USL の料金と Power BI Embedded の使用コストの両方が発生するのを防ぐために、Power BI サービスには、Power BI の USL の所有者に追加コストがかからない Power BI Embedded 外部の独自のコンテンツ埋め込み機能が用意されています (dev.powerbi.com)。

## Power BI Embedded は社内アプリケーションの作成に使用できますか?

いいえ。Power BI Embedded は外部ユーザーのみを対象としており、社内のビジネス アプリケーション内では使用できません。社内のビジネス アプリケーションで使用する Power BI コンテンツを埋め込むには、Power BI サービスを使用し、そのコンテンツを使用するすべてのユーザーが、有効な Power BI Free または Power BI Pro のユーザー サブスクリプション ライセンスを保有している必要があります。社内アプリケーションを Power BI サービスと統合する方法の詳細については、[https://dev.powerbi.com](https://dev.powerbi.com) をご覧ください。

## このサービスは世界中で使用できますか?

Power BI Embedded サービスは、ほとんどのデータ センターで提供されるようになりました。最新の提供状況については、[こちら](https://azure.microsoft.com/status/)で常に確認できます。

## サービスで利用可能な SLA は何ですか。

Power BI Embedded には、Azure 標準 SLA が適用されます。詳細については、「[サービス レベル アグリーメント](https://azure.microsoft.com/support/legal/sla/)」をご覧ください。

## このサービスはどのように課金されますか?

価格については、「[Power BI Embedded の価格](http://go.microsoft.com/fwlink/?LinkId=760527)」をご覧ください。

## レンダーとは何ですか? また、レンダーはどのように請求されますか?

>[AZURE.NOTE] Power BI Embedded のプレビュー期間中には、レンダーごとの割引価格が適用されていましたが、ユーザーのフィードバックではセッションごとの価格が好評だったため、これは終了します。レンダーごとの価格からセッションごとの価格への移行は、2016 年 9 月 1 日に実施されます。

レンダーとは、エンド ユーザーに表示される視覚要素であり、サービスに対するクエリです。たとえば、ユーザーが 4 つの視覚要素を含むレポートを表示した場合、レンダーは 4 つになります。そのユーザーがレポートの表示を更新し、クエリがさらにサービスに送信されると、レンダーはさらに 4 つ増えます。サービス所有者は、エンドユーザーが有料のレンダーにつながる新しいクエリを実行する範囲を制御し、コストの公開を限定し、静的データのシナリオにおけるコストを最小化することができます。

レンダーは 1,000 レンダー単位で請求されます。1,000 未満のレンダー量の請求は按分計算されます。月々 1,000 レンダーは無料で使用できます。ボリューム ライセンス契約から購入された場合、料金情報については Microsoft パートナーまたは販売元にお問い合わせください。

## レポート セッションとは何ですか。また、どのように課金されますか。

セッションとは、エンド ユーザーと Power BI Embedded レポートとの一連のやり取りです。Power BI Embedded レポートがユーザーに表示されるたびに、セッションが開始され、サブスクリプション所有者にセッション分が課金されます。セッションは、レポート内の視覚要素の数やレポート コンテンツの更新頻度に関係なく、均一料金で請求されます。セッションは、ユーザーがレポートを閉じたときか、1 時間後にセッションがタイムアウトになったときに終了します。

## レンダー数やセッション数の見積もりに役立つツールまたはガイダンスは提供されていますか。 また、完了したレンダーの数を確認するにはどうすればよいですか。

Azure ポータルでは、サブスクリプションに対して実行されたレンダー/レポート セッションの数についての課金の詳細が提供されます。

## Power BI Embedded を使用してアプリケーションを開発するには、Power BI サブスクリプションが必要ですか。 開始するには?

アプリケーション開発者は、アプリケーションで使用するレポートや視覚エフェクトを作成するために、Power BI サブスクリプションを所有している必要はありません。Microsoft Azure サブスクリプションと無料の Power BI Desktop アプリケーションが必要になります。

Power BI Embedded サービスを使用する方法の詳細については、サービスのドキュメントを参照してください。

## Azure サブスクリプションを持っています。既存のサブスクリプションを使用して Power BI Embedded を使用できますか。

はい。既存の Azure サブスクリプションを使用して、Microsoft Power BI Embedded サービスをプロビジョニングし、使用することができます。

## アプリケーションのエンドユーザーに Power BI ライセンスは必要ですか。

いいえ。アプリケーションのエンドユーザーは、アプリ内のデータ視覚エフェクトを利用するために、Power BI サブスクリプションを別途購入する必要はありません。Power BI Embedded モデルでは、Azure の従量課金メーターを使用して、アプリケーション プロバイダーにサービス料金が請求されます。詳細については、[料金とライセンス](http://go.microsoft.com/fwlink/?LinkId=760527)に関するページをご覧ください。

## どのように Power BI Embedded のユーザー認証は処理されますか?

Power BI Embedded サービスでは、明示的なエンドユーザー認証ではなく、アプリケーション トークンを使用して認証と承認を行います。アプリケーション トークン モデルでは、アプリケーションがエンドユーザーの認証と承認を管理します。次に、アプリケーションは、必要に応じて

アプリケーション トークンを作成して送信し、要求されたレポートをレンダリングするようサービスに伝えます。この設計では、アプリケーションでユーザーの認証と承認に Azure AD を使用する必要はありません (ただし、Azure AD を使用することもできます)。アプリケーション トークンの詳細については、[こちら](power-bi-embedded-app-token-flow.md)をご覧ください。Power BI Embedded では、高度なセキュリティ フィルター処理シナリオに対応するために、行レベルのセキュリティ機能 (RLS) も導入されました。

## Power BI Embedded では現在どのようなデータ ソースがサポートされていますか?

基本的な資格情報を使用するクラウド データ ソースへの直接クエリによるアクセスがサポートされます。これは、Azure SQL DB や Azure SQL DW などのソースが現在サポートされていることを意味します。今後数か月で、その他のデータ ソースのサポートおよびアクセスの種類を追加します。新たにサポートされるデータ ソースについては、Power BI 開発者フォーラム ([http://dev.powerbi.com](https://dev.powerbi.com/)) でお知らせします。

## Power BI Embedded において、テナント モデルはどのように機能しますか?

Power BI Embedded モデルでは、Azure AD テナントを顧客向けに使用するための明示的な要件はありません。顧客向けに Azure AD を提供するかどうか選択することができます。結果として、アプリケーションとインフラストラクチャのアーキテクチャによって、Power BI Embedded でテナント モデルが必要となるかが決定されます。

アプリケーションの開発に取り組んでいる開発者や従業員は、Azure ポータルを使用して Azure サブスクリプションとワークスペース コレクションを管理する場合に、AAD ユーザー アカウントが必要になります。プログラムの API を使用すると、開発者はレポートをインポートし、接続文字列を変更することができます。また、代わりに、埋め込み用 URL を取得し、認証にアプリケーション トークンを利用することもできます。そのため、AAD は不要になります。API と Azure ポータルの使用方法の詳細については、Azure.com の「[Power BI Embedded のドキュメント](https://azure.microsoft.com/documentation/services/power-bi-embedded/)」をご覧ください。

## 詳細情報を得るには?

[Power BI Embedded ドキュメント ページ](http://go.microsoft.com/fwlink/?LinkId=760526)をご覧ください。このサービスの最新情報については、[Power BI の開発者向けブログ](http://blogs.msdn.com/powerbidev)または Power BI デベロッパー センター (dev.powerbi.com) をご覧ください。[Stackoverflow](http://stackoverflow.com/questions/tagged/powerbi) で質問することもできます。

## 開始するには?

今すぐ無料で開始できます。 Azure サブスクリプションを所有している場合は、Azure ポータルから直接 Power BI Embedded をプロビジョニングできます。また、[無料の Azure アカウント](https://azure.microsoft.com/free/)を作成することも可能です。Power BI Embedded サービスをプロビジョニングしたら、簡単に Power BI REST API を直接使用したり、[GitHub](http://go.microsoft.com/fwlink/?LinkID=746472) で提供されている Developer SDK を使用したりできます。Developer SDK を活用する方法については、サンプルが提供されます。

## 関連項目

- [Microsoft Power BI Embedded とは](power-bi-embedded-what-is-power-bi-embedded.md)
- [Microsoft Power BI Embedded の概要](power-bi-embedded-get-started.md)

<!---HONumber=AcomDC_0713_2016-->