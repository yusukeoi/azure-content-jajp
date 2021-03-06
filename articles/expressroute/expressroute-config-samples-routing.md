<properties
   pageTitle="ExpressRoute の顧客のルーター構成のサンプル |Microsoft Azure"
   description="このページでは、Cisco と Juniper のルーター構成のサンプルを示します。"
   documentationCenter="na"
   services="expressroute"
   authors="cherylmc"
   manager="carmonm"
   editor="" />
<tags
   ms.service="expressroute"
   ms.devlang="na"
   ms.topic="article" 
   ms.tgt_pltfrm="na"
   ms.workload="infrastructure-services"
   ms.date="07/19/2016"
   ms.author="cherylmc"/>

# ルーティングをセットアップして管理するためのルーター構成のサンプル

このページでは、Cisco IOS-XE と Juniper MX シリーズ ルーターのインターフェイスとルーティングを構成するサンプルを示します。これらはガイダンスとしてのみ使用することを目的としたサンプルであり、現状のまま使用することはできません。ベンダーと協力して、ネットワークに適した構成を考えてください。

>[AZURE.IMPORTANT] このページのサンプルは、ガイダンスとしてのみ使用することを目的としています。ベンダーの販売/技術チームおよび自社のネットワーク チームと協力して、ニーズに対応する適切な構成を考える必要があります。Microsoft では、このページに示す構成に関連する問題には対応できません。サポートの問題については、デバイス ベンダーに問い合わせる必要があります。

以下のルーター構成サンプルは、すべてのピアリングを対象としています。詳細については、「[ExpressRoute のピアリング](expressroute-circuit-peerings.md)」および「[ExpressRoute のルーティングの要件](expressroute-routing.md)」をご覧ください。

## Cisco IOS-XE ベースのルーター

このセクションのサンプルは、IOS-XE OS ファミリを実行するルーターを対象としています。

### 1\.インターフェイスとサブインターフェイスの構成

マイクロソフトに接続するすべてのルーターには、ピアリングごとにサブインターフェイスが必要となります。サブインターフェイスの識別には、VLAN ID を使用するか、または VLAN ID と IP アドレスの組み合わせを使用できます。

#### Dot1Q インターフェイスの定義

これはサブインターフェイスの定義サンプルです。単一の VLAN ID を持つサブインターフェイスを想定しています。VLAN ID はピアリングごとに一意となります。IPv4 アドレスの最終オクテットは常に奇数です。

    interface GigabitEthernet<Interface_Number>.<Number>
     encapsulation dot1Q <VLAN_ID>
     ip address <IPv4_Address><Subnet_Mask>

#### QinQ インターフェイスの定義

これはサブインターフェイスの定義サンプルです。2 つの VLAN ID を持つサブインターフェイスを想定しています。外側 VLAN ID (s-tag) が使用されている場合、すべてのピアリングでそのまま維持されます。内側 VLAN ID (c-tag) はピアリングごとに一意となります。IPv4 アドレスの最終オクテットは常に奇数です。

    interface GigabitEthernet<Interface_Number>.<Number>
     encapsulation dot1Q <s-tag> seconddot1Q <c-tag>
     ip address <IPv4_Address><Subnet_Mask>
    
### 2\.eBGP セッションの設定

すべてのピアリングについて、マイクロソフトとの BGP セッションを設定する必要があります。マイクロソフトとの BGP セッションは、以下のサンプルで設定できます。サブインターフェイスに使用されている IPv4 アドレスが a.b.c.d である場合、BGP 近隣ノード (マイクロソフト) の IP アドレスは a.b.c.d+1 になります。BGP 近隣ノードの IPv4 アドレスの最終オクテットは常に偶数です。

	router bgp <Customer_ASN>
	 bgp log-neighbor-changes
	 neighbor <IP#2_used_by_Azure> remote-as 12076
	 !        
	 address-family ipv4
	 neighbor <IP#2_used_by_Azure> activate
	 exit-address-family
	!

### 3\.BGP セッションでアドバタイズするプレフィックスの設定

特定のプレフィックスをマイクロソフトにアドバタイズするようにルーターを構成することができます。その方法を紹介したのが以下のサンプルです。

	router bgp <Customer_ASN>
	 bgp log-neighbor-changes
	 neighbor <IP#2_used_by_Azure> remote-as 12076
	 !        
	 address-family ipv4
	  network <Prefix_to_be_advertised> mask <Subnet_mask>
	  neighbor <IP#2_used_by_Azure> activate
	 exit-address-family
	!

### 4\.ルート マップ

ネットワークに伝播されるプレフィックスは、ルート マップとプレフィックス リストを使用してフィルタリングできます。このタスクは、以下のサンプルで実現できます。適切なプレフィックス リストが設定されていることを確認してください。

	router bgp <Customer_ASN>
	 bgp log-neighbor-changes
	 neighbor <IP#2_used_by_Azure> remote-as 12076
	 !        
	 address-family ipv4
	  network <Prefix_to_be_advertised> mask <Subnet_mask>
	  neighbor <IP#2_used_by_Azure> activate
	  neighbor <IP#2_used_by_Azure> route-map <MS_Prefixes_Inbound> in
	 exit-address-family
	!
	route-map <MS_Prefixes_Inbound> permit 10
	 match ip address prefix-list <MS_Prefixes>
	!


## Juniper MX シリーズ ルーター 

このセクションのサンプルは、Juniper MX シリーズのルーターを対象としています。

### 1\.インターフェイスとサブインターフェイスの構成

#### Dot1Q インターフェイスの定義

これはサブインターフェイスの定義サンプルです。単一の VLAN ID を持つサブインターフェイスを想定しています。VLAN ID はピアリングごとに一意となります。IPv4 アドレスの最終オクテットは常に奇数です。

    interfaces {
    	vlan-tagging;
    	<Interface_Number> {
    		unit <Number> {
    			vlan-id <VLAN_ID>;
    			family inet {
    				address <IPv4_Address/Subnet_Mask>;
    			}
    		}
    	}
    }


#### QinQ インターフェイスの定義

これはサブインターフェイスの定義サンプルです。2 つの VLAN ID を持つサブインターフェイスを想定しています。外側 VLAN ID (s-tag) が使用されている場合、すべてのピアリングでそのまま維持されます。内側 VLAN ID (c-tag) はピアリングごとに一意となります。IPv4 アドレスの最終オクテットは常に奇数です。

	interfaces {
	    <Interface_Number> {
	        flexible-vlan-tagging;
	        unit <Number> {
	            vlan-tags outer <S-tag> inner <C-tag>;
	            family inet {
	                address <IPv4_Address/Subnet_Mask>;
	            }                           
	        }                               
	    }                                   
	}                           

### 2\.eBGP セッションの設定

すべてのピアリングについて、マイクロソフトとの BGP セッションを設定する必要があります。マイクロソフトとの BGP セッションは、以下のサンプルで設定できます。サブインターフェイスに使用されている IPv4 アドレスが a.b.c.d である場合、BGP 近隣ノード (マイクロソフト) の IP アドレスは a.b.c.d+1 になります。BGP 近隣ノードの IPv4 アドレスの最終オクテットは常に偶数です。

	routing-options {
	    autonomous-system <Customer_ASN>;
	}
	}
	protocols {
	    bgp { 
	        group <Group_Name> { 
	            peer-as 12076;              
	            neighbor <IP#2_used_by_Azure>;
	        }                               
	    }                                   
	}

### 3\.BGP セッションでアドバタイズするプレフィックスの設定

特定のプレフィックスをマイクロソフトにアドバタイズするようにルーターを構成することができます。その方法を紹介したのが以下のサンプルです。

	policy-options {
	    policy-statement <Policy_Name> {
	        term 1 {
	            from protocol OSPF;
		route-filter <Prefix_to_be_advertised/Subnet_Mask> exact;
	            then {
	                accept;
	            }
	        }
	    }
	}
	protocols {
	    bgp { 
	        group <Group_Name> { 
	            export <Policy_Name>
	            peer-as 12076;              
	            neighbor <IP#2_used_by_Azure>;
	        }                               
	    }                                   
	}


### 4\.ルート マップ

ネットワークに伝播されるプレフィックスは、ルート マップとプレフィックス リストを使用してフィルタリングできます。このタスクは、以下のサンプルで実現できます。適切なプレフィックス リストが設定されていることを確認してください。

	policy-options {
	    prefix-list MS_Prefixes {
	        <IP_Prefix_1/Subnet_Mask>;
	        <IP_Prefix_2/Subnet_Mask>;
	    }
	    policy-statement <MS_Prefixes_Inbound> {
	        term 1 {
	            from {
		prefix-list MS_Prefixes;
	            }
	            then {
	                accept;
	            }
	        }
	    }
	}
	protocols {
	    bgp { 
	        group <Group_Name> { 
	            export <Policy_Name>
	            import <MS_Prefixes_Inbound>
	            peer-as 12076;              
	            neighbor <IP#2_used_by_Azure>;
	        }                               
	    }                                   
	}

## 次のステップ

詳細については、[ExpressRoute の FAQ](expressroute-faqs.md) を参照してください。

<!---HONumber=AcomDC_0720_2016-->