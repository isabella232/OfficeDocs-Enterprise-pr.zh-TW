---
title: 設計 Microsoft Azure IaaS 的網路
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 9cb70c9d-9ed9-47cc-af5a-6403d87d3372
description: 摘要： 了解如何設計 Microsoft Azure IaaS 中工作負載的最佳化網路功能。
ms.openlocfilehash: b06564c8a86c59dac4ac9a5380cd88cf9d045974
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068129"
---
# <a name="designing-networking-for-microsoft-azure-iaas"></a>設計 Microsoft Azure IaaS 的網路

 **摘要：** 了解如何設計 Microsoft Azure IaaS 中工作負載的最佳化網路功能。
  
最佳化的裝載在 Azure IaaS 中的 IT 工作負載的網路功能需要瞭解的 Azure 虛擬網路 (Vnet)、 位址空間，路由、 DNS 及負載平衡。
  
## <a name="planning-steps-for-any-vnet"></a>規劃任何 VNet 中的步驟

任何類型的 VNet，請遵循下列步驟。
  
### <a name="step-1-prepare-your-intranet-for-microsoft-cloud-services"></a>步驟 1： 準備您的內部網路的 Microsoft 雲端服務。

經過[Microsoft 雲端連線能力的共同元素](common-elements-of-microsoft-cloud-connectivity.md)中的**步驟來準備您的 Microsoft 雲端服務的網路**區段。
  
### <a name="step-2-optimize-your-internet-bandwidth"></a>步驟 2： 最佳化您的網際網路頻寬。

最佳化網際網路頻寬使用步驟 2 到 4 的**步驟來準備您的網路以 Microsoft SaaS 服務**] 區段中，在[設計 Microsoft SaaS 的網路](designing-networking-for-microsoft-saas.md)。
  
### <a name="step-3-determine-the-type-of-vnet-cloud-only-or-cross-premises"></a>步驟 3： 決定 VNet 的類型 (僅限雲端或跨部門)。

僅雲端 VNet 有沒有連線至內部部署網路。 以下是範例。
  
**圖 1: 僅雲端 VNet**

![圖 1：Azure 中只存在於雲端的虛擬網路](media/8be19104-02b3-4a7f-b0a0-30d6fcf8890b.png)
  
圖 1 顯示僅雲端 VNet 中的一組的虛擬機器。
  
跨單位 VNet 具有站台對站 (S2S) VPN 或 ExpressRoute 連線到 Azure 閘道在內部網路。 以下是範例。
  
**圖 2: 跨單位 VNet**

![圖 2：Azure 中跨部署的虛擬網路](media/caacf007-e0dc-45d3-9531-441109776d25.png)
  
圖 2 顯示一組的虛擬機器中的跨單位 VNet，連線到內部部署網路。
  
請參閱其他本文中[的跨單位 VNet 的規劃步驟](designing-networking-for-microsoft-azure-iaas.md#cross_prem)一節。
  
### <a name="step-4-determine-the-address-space-of-the-vnet"></a>步驟 4： 決定 VNet 位址空間。

表 1 顯示不同類型的 Vnet 位址空間。
  
|**VNet 的類型**|**虛擬網路位址空間**|
|:-----|:-----|
|僅雲端  <br/> |任意私人位址空間  <br/> |
|互連僅雲端  <br/> |任意的私用]，但不是重疊與其他連線 Vnet  <br/> |
|跨單位  <br/> |私用]，但不是重疊與內部部署  <br/> |
|互連的跨單位部署  <br/> |私用]，但不是重疊的內部部署及其他連線 Vnet  <br/> |
   
 **表 1： 類型的 Vnet 和其對應的位址空間**
  
虛擬機器由 DHCP 指派位址空間的子網路的位址組態：
  
- 位址/子網路遮罩
    
- 預設閘道
    
- DNS 伺服器 IP 位址
    
您也可以保留的靜態 IP 位址。
  
虛擬機器也可以指派公用 IP 位址，個別或從包含雲端服務 （適用於僅傳統的部署機器）。
  
### <a name="step-5-determine-the-subnets-within-the-vnet-and-the-address-spaces-assigned-to-each"></a>步驟 5： 決定 VNet 和指派給每個位址空間內的子網路。

有兩種類型的 VNet 中的子網路、 閘道子網路和虛擬機器裝載的子網路。
  
**圖 3：Azure 中的兩種子網路類型**

![圖 3：Azure 中的兩種子網路類型](media/2eaa512d-1293-4e9b-b927-6bfe0fc0acb4.png)
  
圖 3 顯示包含有 Azure 閘道和一組包含虛擬機器的虛擬機器裝載子網路的閘道子網路的 VNet。
  
Azure 時需要 Azure 閘道子網路，裝載兩部虛擬機器的 Azure 閘道。 至少要有 29 位元前置詞長度與指定的位址空間 (範例： 192.168.15.248/29)。 建議的 27 位元或較小的前置詞長度，尤其是如果您打算使用 ExpressRoute。
  
決定 Azure 閘道子網路的位址空間的最佳作法是：
  
1. 決定的閘道子網路大小。
    
2. 在位址空間的 VNet 中變數的位元，設定用於設為 0，閘道子網路的位元，其餘位元數設為 1。
    
3. 轉換成十進位及 express 的位址空間為具有前置詞長度設為閘道子網路大小。
    
使用此方法之後，閘道子網路的位址空間一定是 VNet 位址空間的邊界最遠的結尾。
  
以下是定義閘道子網路的位址前置詞的範例： VNet 位址空間是 10.119.0.0/16。 組織一開始會使用站台對站 VPN 連線，但最終會收到 ExpressRoute。 表 2 示範的步驟和結果判斷網路前置詞表示法 (也稱為 CIDR) 中的閘道子網路位址前置字元。

以下是步驟和範例判斷閘道子網路位址前置詞：

1. 決定的閘道子網路大小。 我們的範例，我們會選擇 /28。
2. 設定位元 VNet 位址空間 (b) 部分變數設為 0 閘道子網路位元 (G)，否則 1 (V)。 我們的範例，我們使用 10.119.0.0/16 位址空間的 VNet。
<br/>
<br/>10.119。 bbbbbbbb。 bbbbbbbb
<br/>10.119。 VVVVVVVV。 VVVVGGGG
<br/>10.119。 11111111。 11110000
<br/><br/>
3. 步驟 2 中將結果轉換成十進位及快速為位址空間。 我們的範例，10.119。 11111111。 11110000 10.119.255.240，且從步驟 1，(在我們的範例 28) 前置詞長度，產生的閘道子網路位址前置詞是 10.119.255.240/28。
  
如需詳細資訊，請參閱[Azure 閘道子網路的位址空間計算機](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed)。
  
虛擬機器裝載的子網路會放置 Azure 的虛擬機器，您可以根據內部一般指導方針，例如一般角色或應用程式或子網路隔離層的位置。
  
Azure 每個子網路上使用的第一次 3 的地址。 因此，在 Azure 的子網路上可能地址的數目是 2<sup>n</sup> -5，其中 n 是主機位元數。 表 3 顯示的虛擬機器有需要的號碼範圍主控個位元所需，與對應的子網路大小。
  
|**所需的虛擬機器**|**主機位元**|**子網路大小**|
|:-----|:-----|:-----|
|1-3  <br/> |3  <br/> |/29  <br/> |
|4-11  <br/> |4  <br/> |/28  <br/> |
|12-27  <br/> |5  <br/> |/27  <br/> |
|28-59  <br/> |6  <br/> |/26  <br/> |
|60-123  <br/> |7  <br/> |/25  <br/> |
   
 **表 3： 虛擬機器需求和其子網路大小**
  
如需虛擬機器上的子網路或 VNet 的最大數量的詳細資訊，請參閱[網路功能的限制](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits)。
  
如需詳細資訊，請參閱[ Plan and design Azure 虛擬網路](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/)。
  
### <a name="step-6-determine-the-dns-server-configuration-and-the-addresses-of-the-dns-servers-to-assign-to-vms-in-the-vnet"></a>步驟 6： 決定 DNS 伺服器設定，以及指派給 VNet 中 Vm 的 DNS 伺服器位址。

Azure 會指派虛擬機器由 DHCP 的 DNS 伺服器的位址。 可以是 DNS 伺服器：
  
- 提供 Azure： 提供本機名稱登錄和本機網際網路名稱解析
    
- 您所提供： 提供本機或網路名稱登錄與內部網路或網際網路名稱解析
    
表 4 顯示每種類型的 VNet 的 DNS 伺服器的不同設定。
    
|**VNet 的類型**|**DNS 伺服器**|
|:-----|:-----|
|僅雲端  <br/> |Azure 提供的本機與網際網路名稱解析  <br/> Azure 虛擬機器的本機與網際網路名稱解析 （DNS 轉寄）  <br/> |
|跨單位  <br/> |在內部的本機複本與內部網路的名稱解析  <br/> Azure 虛擬機器的本機複本與內部網路名稱解析 （DNS 複寫和轉送）  <br/> |
   
 **表 4： 兩個不同類型的 Vnet 的 DNS 伺服器選項**
  
如需詳細資訊，請參閱 <<c0>的 Vm 及角色執行個體的名稱解析。
  
### <a name="step-7-determine-the-load-balancing-configuration-internet-facing-or-internal"></a>步驟 7： 決定負載平衡組態 （網際網路對向或內部）。

在某些情況下，您要將一組具有相同角色之伺服器的傳入流量分散。 Azure IaaS 具有內建的設備，若要這麼做為網際網路對向和內部流量負載。
  
Azure 網際網路對向負載平衡會隨機分散來路不明連入網際網路的流量負載平衡集的成員。
  
**圖 4：Azure 中的外部負載平衡器**

![圖 4：Azure 中的外部負載平衡器](media/eb5945e5-0c2b-40f1-b9ed-54bb2b0f9e59.png)
  
圖 4 顯示將輸入的 NAT 規則或一組負載平衡集內的虛擬機器的端點上的內送流量的 Azure 中的外部負載平衡器。
  
Azure 內部負載平衡會隨機分散來路不明的連入流量從其他 Azure Vm 或內部網路負載平衡集的成員電腦。 
  
**圖 5：Azure 中的內部負載平衡器**

![圖 5：Azure 中的內部負載平衡器](media/d1451b73-6465-449d-b3e6-22160ce51f35.png)
  
圖 5 顯示將輸入的 NAT 規則或一組負載平衡集內的虛擬機器的端點上的內送流量的 Azure 內部負載平衡器。
  
如需詳細資訊，請參閱 < <b0>Azure 負載平衡器</b0>。
  
### <a name="step-8-determine-the-use-of-virtual-appliances-and-user-defined-routes"></a>步驟 8： 決定使用虛擬設備和使用者定義路由。

如果您需要轉送到您的 VNet 中的虛擬設備的流量，您可能需要新增一或多個使用者定義路由至子網路。
  
**圖 6：Azure 中的虛擬設備和使用者定義路由**

![圖 6：Azure 中的虛擬設備和使用者定義路由](media/f181d0f4-ebf9-439e-9c98-dec17428c32b.png)
  
圖 6 顯示跨單位 VNet 和指派給指向虛擬 appliance 虛擬機器裝載子網路的使用者定義路由。
  
如需詳細資訊，請參閱[使用者定義路由和 IP 轉寄功能](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview)。
  
### <a name="step-9-determine-how-computers-from-the-internet-will-connect-to-virtual-machines"></a>步驟 9： 決定如何從網際網路的電腦會連線至虛擬機器。

有多種方式來提供網際網路存取虛擬機器上的 VNet，包括透過 proxy 伺服器或其他邊緣裝置對組織網路的存取。
  
表 5 會列出篩選或檢查來路不明的連入流量的方法。
  
|**方法**|**部署模型**|
|:-----|:-----|
|1.端點和設定雲端服務上的 Acl  <br/> |傳統  <br/> |
|2.網路安全性群組  <br/> |資源管理員與傳統  <br/> |
|3.網際網路對向負載平衡器使用 NAT 的輸入規則  <br/> |資源管理員  <br/> |
|4.網路安全性設備 Azure marketplace （不會顯示）  <br/> |資源管理員與傳統  <br/> |
   
 **表 5： 方法的連接至虛擬機器和其對應的 Azure 的部署模型**
  
**圖 7：透過網際網路連線到 Azure 虛擬機器**

![圖 7：透過網際網路連線到 Azure 虛擬機器](media/c5e3531b-170a-4482-a6ff-fb8fbbe81b35.png)
  
圖 7 顯示連接中使用端點的雲端服務的虛擬機器上使用網路安全性] 群組中，子網路的虛擬機器，使用外部負載平衡器和 NAT 的輸入的規則的子網路上的虛擬機器連線到網際網路的電腦。
  
額外的安全性提供者：
  
- 遠端桌面] 和 [SSH 連線，這是經過驗證及加密。
    
- 遠端 PowerShell 工作階段，這是經過驗證及加密。
    
- IPsec 傳輸模式，您可以使用的端對端加密。
    
- Azure DDOS 防護，這有助於防止外部及內部攻擊
    
如需詳細資訊，請參閱[Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity)和[Azure 網路安全性](https://azure.microsoft.com/blog/azure-network-security/)。
  
### <a name="step-10-for-multiple-vnets-determine-the-vnet-to-vnet-connection-topology"></a>步驟 10： 針對多個 Vnet，決定 VNet 對 VNet 連線拓樸。

Vnet 可以使用類似用於連接組織的站台拓撲彼此連線。
  
菊輪鍊設定連接中一系列 Vnet。
  
**圖 8: 菊組態 Vnet**

![圖 8：Azure 虛擬網路的菊輪鍊設定](media/264d5dd4-06c5-483f-9428-a18cc1f68ac1.png)
  
圖 8 顯示連線使用菊設定數列中的五個 Vnet。
  
輪輻和中樞設定連接至中央 Vnet、 連線至彼此本身是一組多個 Vnet。
  
**圖 9: 輪輻和中樞設定 Vnet**

![圖 9：Azure 虛擬網路的輪輻和中樞設定](media/dd442a38-5b76-4ac5-b743-8fc7711a91ba.png)
  
圖 9 顯示六個 Vnet、 兩個 Vnet 會連線至彼此與也兩個其他支點 Vnet 的中樞。
  
完整網狀設定連接至彼此的每個 VNet。
  
**圖 10： 完整網狀結構 Vnet 的設定**

![圖 10：Azure 虛擬網路的網狀設定](media/9dda0738-10db-4a63-95b3-79851a399b71.png)
  
圖 10 顯示四個 Vnet 所有連接至彼此，使用六個 VNet 對 VNet 連線總數。
  
## <a name="planning-steps-for-a-cross-premises-vnet"></a>規劃跨單位 VNet 中的步驟
<a name="cross_prem"> </a>

針對跨單位 VNet，請遵循下列步驟。
  
> [!TIP]
> 若要建立模擬的跨單位部署開發/測試環境，請參閱 < <b0>Simulated 跨單位 azure 虛擬網路</b0>。 
  
### <a name="step-1-determine-the-cross-premises-connection-to-the-vnet-s2s-vpn-or-expressroute"></a>步驟 1： 判定 VNet （S2S VPN 或 ExpressRoute） 的跨單位連線。

表 6 列出不同類型的連線。
  
|**連線類型**|**用途**|
|:-----|:-----|
|站台對站 (S2S) VPN  <br/> |若要在單一 VNet 連線 1-10 個網站 （包括其他 Vnet）。  <br/> |
|ExpressRoute  <br/> |透過網際網路 Exchange 提供者 (IXP) 或網路服務提供者 (NSP) Azure 私用、 安全連結。  <br/> |
|點網站 (P2S) VPN  <br/> |將單一電腦連接到 VNet。  <br/> |
|VNet 對等或 VNet 對 VNet (V2V) VPN  <br/> |連接至另一個 VNet 的 VNet。  <br/> |
   
 **表 6: 類型之連線的跨單位 Vnet**
  
如需有關連線數目上限的詳細資訊，請參閱[網路功能的限制](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits)。
  
如需 VPN 裝置的詳細資訊，請參閱 <<c0>的站台對站虛擬網路連線的 VPN 裝置。
  
如需 VNet 對等的詳細資訊，請參閱[VNet 對等](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview)。
  
**圖 11: 四種方法來連線至跨單位 VNet**

![圖 11：連線到跨部署 Azure 虛擬網路的三種方式](media/d5d4a625-cfbd-4a77-9159-eaca69d07e93.png)
  
圖 11 顯示具有連線四種類型的 VNet: P2S 連線從電腦、 從內部網路的 S2S VPN 連線、 從內部部署網路，ExpressRoute 連線並從另一個 VNet 的 VNet 對 VNet 連線。 
  
您可以連線至 Vm VNet 中以下列方式：
  
- 從您的內部網路或網際網路的 VNet Vm 的系統管理
    
- 從您的內部網路的 IT 工作負載存取
    
- 透過其他 Vnet 網路的分機號碼
    
連線的安全性是由下列提供：
  
- P2S 使用安全通訊端通道通訊協定 (SSTP) 
    
- S2S 和 VNet 對 VNet 的 VPN 連線使用 AES256 IPsec 通道模式
    
- ExpressRoute 是私人 WAN 連線
    
如需詳細資訊，請參閱[Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity)和[Azure 網路安全性](https://azure.microsoft.com/blog/azure-network-security/)。
  
### <a name="step-2-determine-the-on-premises-vpn-device-or-router"></a>步驟 2： 決定在內部部署 VPN 裝置或路由器。

您在內部部署 VPN 裝置或路由器，做為：
  
- IPsec 對等網路，終止 Azure 閘道的 S2S VPN 連線。
    
- 私用的對等 ExpressRoute 連線 BPG 對等和終止點。
    
**圖 12：內部部署 VPN 路由器或裝置**

![圖 12：內部部署 VPN 路由器或裝置](media/bd221468-a660-4730-aa55-0426986480b9.png)
  
圖 12 顯示跨單位 VNet 連接到內部部署 VPN 路由器或裝置。
  
如需詳細資訊，請參閱 <<c0>關於 VPN 閘道。
  
### <a name="step-3-add-routes-to-your-intranet-to-make-the-address-space-of-the-vnet-reachable"></a>步驟 3： 新增至您的內部網路進行 VNet 位址空間可以到達路由。

從內部部署路由傳送至 Vnet 包含下列任一動作：
  
1. 指向您的 VPN 裝置的 VNet 位址空間的路由。
    
2. 在您點之間的 S2S VPN 或 ExpressRoute 連線的 VPN 裝置的 VNet 位址空間路由
    
**圖 13: 內部部署路由需要讓 VNet 可以到達**

![圖 13：內部部署路由需要讓 Azure VNet 可以連線](media/7a1e20c1-fbc4-4cb9-9961-735da4e23307.png)
  
圖 13 顯示內部路由器和 VPN 路由器或代表 VNet 位址空間裝置所需的路由資訊。
  
### <a name="step-4-for-expressroute-plan-for-the-new-connection-with-your-provider"></a>步驟 4: ExpressRoute，如規劃與您的提供者的新連線。

您可以使用私人對等之間您的內部網路與 Microsoft 雲端中三個不同的方式建立 ExpressRoute 連線：
  
- 共置在雲端 exchange
    
- 點對點乙太網路連線
    
- 任何對多 (IP VPN) 網路
    
**圖 14： 使用 ExpressRoute 連線至跨單位 VNet**

![圖 14：使用 ExpressRoute 連線到跨部署 Azure 虛擬網路](media/7030bd39-69a6-4283-8567-3434e1ab6ba6.png)
  
圖 14 顯示跨單位 VNet，以及從內部路由器到 Microsoft Azure ExpressRoute 連線。
  
如需詳細資訊，請參閱 <<c0>適用於 Microsoft 雲端連線能力。
  
### <a name="step-5-determine-the-local-network-address-space-for-the-azure-gateway"></a>步驟 5： 決定 Azure 閘道的區域網路位址空間。

進行路由傳送至內部部署或其他 Vnet 從 VNet，Azure 會比對區域網路位址空間指派給閘道 Azure 閘道之間轉送流量。
  
**圖 15: 區域網路位址空間的跨單位 VNet**

![圖 15：跨部署 Azure 虛擬網路的區域網路位址空間](media/e3af2652-8b8e-4551-9a0b-b550e6e7e3c0.png)
  
圖 15 顯示跨單位 VNet 和區域網路位址空間，在 Azure 閘道，表示在內部部署網路上的可連線的位址空間。 
  
您可以下列方式定義的區域網路位址空間：
  
- 選項 1： 目前所需的位址空間或 （當您新增新的子網路時，可能需要更新） 的使用中的前置詞的清單。
    
- 選項 2： 整個內部地址空間 （只有當您新增新的位址空間的更新）。
    
因為 Azure 閘道不允許摘錄的路由，您必須先定義選項 2 的區域網路位址空間，以便它不會納入 VNet 位址空間。
  
**圖 16: 地址空間漏洞建立 VNet 位址空間**

![圖 16：虛擬網路的位址空間所建立的地址空間漏洞](media/e79c4840-f9e3-4741-9b72-59db6043aefa.png)
  
圖 16 顯示的位址空間] 根空間和 VNet 位址空間的表示法。
  
以下是定義為 「 漏洞 」 建立 VNet 的位址空間周圍的區域網路位址空間的前置詞的範例：
  
- 組織使用私人位址空間 （10.0.0.0/8、 172.16.0.0/12，/8 以及 192.168.0.0/16） 部分，其內部部署網路上。 他們選擇選項 2 和 10.100.100.0/24 作為其 VNet 位址空間。
    
表 7 會顯示的步驟和結果定義此範例的區域網路位址空間的前置詞。
  
|**步驟**|**Results**|
|:-----|:-----|
|1.清單不是 VNet 位址空間的根空間的前置詞。  <br/> |172.16.0.0/12 和 192.168.0.0/16  <br/> |
|2.列出變數的八位元，但不包括最後的使用八位元的 VNet 位址空間中的不重疊前置詞。  <br/> |10.0.0.0/16、 10.1.0.0/16...]10.99.0.0/16、 10.101.0.0/16...]10.254.0.0/16，10.255.0.0/16 （255 的首碼，已略過 10.100.0.0/16）  <br/> |
|3.清單內的最後一個使用八位元 VNet 位址空間的不重疊前置詞。  <br/> |10.100.0.0/24、 10.100.1.0/24...]10.100.99.0/24、 10.100.101.0/24...]10.100.254.0/24，10.100.0.255.0/24 （255 的首碼，已略過 10.100.100.0/24）  <br/> |
   
 **表 7： 範例本機位址網路空間**
  
### <a name="step-6-configure-on-premises-dns-servers-for-dns-replication-with-dns-servers-hosted-in-azure"></a>步驟 6： 設定內部 DNS 伺服器的 DNS 複寫裝載於 Azure 中的 DNS 伺服器。

若要確保內部電腦可以解析的以 Azure 為基礎的伺服器名稱，以及以 Azure 為基礎的伺服器可以解析的內部電腦名稱，設定：
  
- 轉寄至內部 DNS 伺服器 VNet 中的 DNS 伺服器
    
- 適當的區域之間 DNS 伺服器的內部和 VNet 中的 DNS 複寫
    
**圖 17: DNS 複寫和轉送的跨單位 VNet 的 DNS 伺服器**

![圖 17：跨部署 Azure 虛擬網路中 DNS 伺服器的 DNS 複寫和轉送](media/ab55e5ce-ccb0-49d4-a301-657a727f97b2.png)
  
圖 17 顯示跨單位 VNet 的 DNS 伺服器，在內部部署網路和 VNet 中子網路上。 DNS 複寫和轉送已設定兩部 DNS 伺服器。
  
### <a name="step-7-determine-the-use-of-forced-tunneling"></a>步驟 7： 決定使用強制通道。

Azure 的子網路的預設系統路由指向網際網路。 若要確保從虛擬機器中的所有流量都會透過跨單位連線，請使用預設路由，使用 Azure 閘道作為其下一個躍點的位址建立路由表。 您然後關聯子網路的路由表。 這稱為 「 強制通道。 如需詳細資訊，請參閱 < <b0>Configure 強制通道</b0>。
  
**圖 18： 使用者定義路由和強制通道跨單位 VNet**

![圖 18：跨部署 Azure 虛擬網路的使用者定義路由和強制通道](media/1e545ec6-c2d9-48d2-bb5e-e0a581fee004.png)
  
圖 18 顯示跨單位 VNet，以指向 Azure 閘道子網路的使用者定義路由。
  
## <a name="sharepoint-server-2016-farm-in-azure"></a>Azure 中的 SharePoint Server 2016 伺服器陣列
<a name="cross_prem"> </a>

內部網路裝載在 Azure IaaS 中的 IT 工作負載的範例為高可用性、 多層式 SharePoint Server 2016 伺服器陣列。
  
**圖 19: 高可用性內部網路 SharePoint Server 2016 伺服器陣列 Azure IaaS 中**

![Azure IaaS 中的高可用性 SharePoint Server 2016 伺服器陣列](media/3a922e21-df91-455f-ba90-78abdd48d98d.png)
  
圖 19 顯示部署前端和資料層級會使用內部負載平衡器跨單位 VNet 中的 SharePoint Server 2016 伺服器陣列的九個伺服器。 如需詳細資訊，包括逐步設計和部署的指示，請參閱 < <b0>Microsoft Azure 中的 SharePoint Server 2016</b0>。
  
> [!TIP]
> 若要在模擬的跨單位 VNet 中建立單一伺服器 SharePoint Server 2016 伺服器陣列，請參閱[Azure 開發/測試環境中的內部網路 SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment)。 
  
如需其他範例虛擬跨單位 azure 虛擬機器上部署的 IT 工作負載的網路，請參閱[Azure IaaS 的混合式雲端案例](https://docs.microsoft.com/office365/enterprise/hybrid-cloud-scenarios-for-azure-iaas)。
  
## <a name="see-also"></a>另請參閱

[Microsoft Cloud Networking for Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)


