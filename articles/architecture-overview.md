<properties 
	pageTitle="Microsoft Azure のアプリケーション アーキテクチャ | Microsoft Azure" 
	description="一般的な設計パターンを対象とするアーキテクチャの概要" 
	services="" 
	documentationCenter="" 
	authors="Rboucher" 
	manager="jwhit" 
	editor="mattshel"/>

<tags 
	ms.service="multiple" 
	ms.workload="na" 
	ms.tgt_pltfrm="na" 
	ms.devlang="na" 
	ms.topic="article" 
	ms.date="05/19/2016" 
	ms.author="robb"/>

#Microsoft Azure のアプリケーションのアーキテクチャ
Microsoft Azure を使用するアプリケーションを構築するためのリソースです。これには、ソフトウェア システムを視覚的に説明する図を描画するためのツールが含まれます。

##設計パターンのポスター

Microsoft patterns & practices は、MSDN と PDF ダウンロードの両方で利用可能な書籍「[クラウド設計パターン](http://msdn.microsoft.com/library/dn568099.aspx)」を発行しました。すべてのパターンを一覧表示する大型のポスターもあります。

![patterns & practices のクラウド パターンのポスター](./media/architecture-overview/PnPPatternPosterThumb.jpg)

##Microsoft のアーキテクチャの認定コース

Microsoft では、先日マイクロソフト認定資格試験 70-534 をサポートする新しいアーキテクチャ コースをリリースしました。このコースは、[EDX.ORG で無料で利用可能](https://www.edx.org/course/architecting-microsoft-azure-solutions-microsoft-dev205x)です。このコースでは、新しい [3D ブループリントの Visio テンプレート](#3d-blueprint-visio-template)を使用します。

![Microsoft のアーキテクチャの認定コース](./media/architecture-overview/EDXCourse.png)


##Microsoft のアーキテクチャの設計図

Microsoft は、Microsoft 製品を使用する特定の種類のシステム構築方法を示す、大まかな[アーキテクチャ ブループリント](http://aka.ms/azblueprints)を公開しています。

各ブループリントには、以下が含まれています。

- ダウンロードして変更できるフラットな **2D の Visio** 2003 ベースのファイル
- あまり技術に詳しくないユーザーに対してブループリントを紹介する、色鮮やかな **奥行のある 3D PDF** ファイル
- 3D バージョンを紹介する**ビデオ**

ブループリントには、[クラウドおよびエンタープライズ用シンボル セット](#symbol-and-icon-sets)が使用されています。

![[Microsoft アーキテクチャ ブループリント 3D] ダイアグラム](./media/architecture-overview/BluePrintThumb.jpg)



##3D ブループリント Visio テンプレート

3D バージョンの [Microsoft アーキテクチャ ブループリント](http://aka.ms/azblueprints)は、当初は非 Microsoft ツールで作成されました。Visio 2013 (以降) の新しいテンプレートが、2015 年 8 月 5 日に、[EDX.ORG で配信される Microsoft のアーキテクチャの認定コース](#microsoft-architecture-certification-course)の一部として出荷されました。

テンプレートは、このコース以外でも利用もできます。

- 最初に機能を確認するために、[トレーニング ビデオを視聴](http://aka.ms/3dBlueprintTemplateVideo)する
- [Microsoft 3D ブループリント Visio テンプレート](http://aka.ms/3DBlueprintTemplate)をダウンロードする
- 3D テンプレートと一緒に使用する[クラウドとエンタープライズのシンボル](#drawing-symbol-and-icon-sets)をダウンロードする

トレーニング資料で解決できない具体的な質問や、フィードバックの提供については、[CnESymbols@microsoft.com](mailto:CnESymbols@microsoft.com) まで電子メールでご連絡ください。使いやすさは、テンプレートの主な目標の 1 つです。よかった点や問題点についてお知らせください。

![Microsoft 3D ブループリント Visio テンプレート](./media/architecture-overview/3DBlueprintVisioTemplate.jpg)



##シンボルとアイコン セットの描画 

[Visio とシンボルに関するトレーニング ビデオを視聴](http://aka.ms/CnESymbolsVideo)してから、[クラウドおよびエンタープライズ用シンボル セットをダウンロード](http://aka.ms/CnESymbols)すると、Azure、Windows Server、SQL Server、その他について説明する技術資料を作成する際に役に立ちます。これらのシンボルやアイコンは、アーキテクチャ ダイアグラム、トレーニング資料、プレゼンテーション、データシート、インフォグラフィックス、ホワイトペーパーに加え、サード パーティの書籍でも使用できます (Microsoft 製品の使用が想定された書籍の場合)。ただし、ユーザー インターフェイスで使用することは、想定されていません。

CnE シンボルは、Visio 形式と PNG 形式で提供されます。セットには、PowerPoint での PNG ファイルの使用方法に関する追加の手順が含まれています。

シンボル セットは四半期に 1 回発行され、新しいサービスがリリースされるたびに更新されます。

CnE セットのようにアーキテクチャ ダイアグラム向けに最適化されてはいませんが、[Microsoft Office Visio ステンシル](http://www.microsoft.com/ja-JP/download/details.aspx?id=35772)で、Microsoft Office と関連テクノロジの追加のシンボルを入手できます。

**フィードバック:** CnE シンボルを使用した場合は、簡単な 5 つの質問の[アンケート](http://aka.ms/azuresymbolssurveyv2)にご記入いただくか、[CnESymbols@microsoft.com](mailto:CnESymbols@microsoft.com) 宛てに具体的な質問や課題をお送りください。ご意見、ご感想をお寄せください。この機能を継続的に改善できるよう、役立てたいと考えております。

![クラウドおよびエンタープライズ用シンボル/アイコン セット](./media/architecture-overview/CnESymbols.png)


##アーキテクチャのインフォグラフィック

Microsoft は、ポスター/インフォグラフィックに関連するいくつかのアーキテクチャを公開しています。[実際のクラウド アプリケーションの作成](https://azure.microsoft.com/documentation/infographics/building-real-world-cloud-apps/)と[クラウド サービスへの対応](https://azure.microsoft.com/documentation/infographics/cloud-services/)が含まれています。

![Azure Architecture Infographics](./media/architecture-overview/AzureArchInfographicThumb.jpg)

<!---HONumber=AcomDC_0810_2016-->