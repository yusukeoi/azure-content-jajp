<properties
	pageTitle="SharePoint サーバー ファームの作成 | Microsoft Azure"
	description="Azure で SharePoint 2013 または SharePoint 2016 の新しいファームを短時間で作成します。"
	services="virtual-machines-windows"
	documentationCenter=""
	authors="JoeDavies-MSFT"
	manager="timlt"
	editor=""
	tags="azure-resource-manager"/>

<tags
	ms.service="virtual-machines-windows"
	ms.workload="infrastructure-services"
	ms.tgt_pltfrm="vm-windows"
	ms.devlang="na"
	ms.topic="article"
	ms.date="08/08/2016"
	ms.author="josephd"/>

# SharePoint サーバー ファームの作成

[AZURE.INCLUDE [learn-about-deployment-models](../../includes/learn-about-deployment-models-rm-include.md)] 従来のモデル。

## SharePoint 2013 ファーム

Microsoft Azure ポータル Marketplace では、事前に構成された SharePoint Server 2013 ファームを簡単に作成できます。これにより、開発テスト環境で基本または高可用性の SharePoint ファームが必要な場合や、組織のコラボレーション ソリューションとして SharePoint Server 2013 を評価する場合の所要時間を大きく節約できます。

> [AZURE.NOTE] Azure ポータルの Azure Marketplace の **SharePoint サーバー ファーム**項目は削除されました。これは、**SharePoint 2013 非 HA ファーム**項目および **SharePoint 2013 HA ファーム**項目に置き換えられました。

この構成では、次の 3 つの仮想マシンの基本的な SharePoint ファームで構成されます。

![sharepointfarm](./media/virtual-machines-windows-sharepoint-farm/Non-HAFarm.png)

このファーム構成は、SharePoint アプリ開発の簡略化セットアップまたは、SharePoint 2013 の初回の評価で使用することができます。

基本的な (3 サーバー) SharePoint ファームを作成するには:

1. [ここ](https://azure.microsoft.com/marketplace/partners/sharepoint2013/sharepoint2013farmsharepoint2013-nonha/)をクリックしてください。
2. **[デプロイ]** をクリックします。
3. **[SharePoint 2013 非 HA ファーム]** ウィンドウで、**[作成]** をクリックします。
4. **[SharePoint 2013 非 HA ファームの作成]** ウィンドウの手順で設定を指定して、**[作成]** をクリックします。

高可用性 SharePoint ファームは、次に示す構成の 9 台の仮想マシンで構成されます。

![sharepointfarm](./media/virtual-machines-windows-sharepoint-farm/HAFarm.png)

このファーム構成は、より大量のクライアント読み込みや外部の SharePoint サイトの高可用性をテストしたり、SharePoint ファームの SQL Server AlwaysOn 可用性グループをテストしたりする場合に使用できます。この構成は、高可用環境での SharePoint アプリケーション開発でも使用できます。

高可用性 (9 サーバー) の SharePoint ファームを作成するには:

1. [ここ](https://azure.microsoft.com/marketplace/partners/sharepoint2013/sharepoint2013farmsharepoint2013-ha/)をクリックしてください。
2. **[デプロイ]** をクリックします。
3. **[SharePoint 2013 HA ファーム]** ウィンドウで、**[作成]** をクリックします。
4. **[Create SharePoint 2013 HA Farm (SharePoint 2013 HA ファームの作成)]** ウィンドウの 7 つの手順で設定を指定して、**[作成]** をクリックします。

> [AZURE.NOTE] Azure 無料試用版では **SharePoint 2013 非 HA ファーム**または **SharePoint 2013 HA ファーム**を作成することはできません。

Azure ポータルは、インターネットに接続する Web プレゼンスを持つクラウド専用の仮想ネットワークにこれら両ファームを作成します。組織のネットワークに戻るサイト間 VPN 接続や ExpressRoute 接続はありません。

## SharePoint 2016 ファーム

次の SharePoint 2016 単一サーバー ファームの構築については、[こちらの記事](https://technet.microsoft.com/library/mt723354.aspx)をご覧ください。

![sharepointfarm](./media/virtual-machines-windows-sharepoint-farm/SP2016Farm.png)

## SharePoint ファームの管理

これらのファームのサーバーはリモート デスクトップ接続を通じて管理できます。詳細については、「[仮想マシンへのログオン](virtual-machines-windows-hero-tutorial.md#log-on-to-the-virtual-machine)」を参照してください。

SharePoint のサーバーの全体管理サイトで [My Sites]、SharePoint アプリケーション、その他の機能を構成できます。詳細については、[SharePoint の構成](http://technet.microsoft.com/library/ee836142.aspx)に関するページをご覧ください。

## 次のステップ

- Azure インフラストラクチャ サービスで、追加の [SharePoint の構成](https://technet.microsoft.com/library/dn635309.aspx)を検出します。

<!---HONumber=AcomDC_0810_2016-->