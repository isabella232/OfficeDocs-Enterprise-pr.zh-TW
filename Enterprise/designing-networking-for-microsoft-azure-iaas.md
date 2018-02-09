---
title: "設計 Microsoft Azure IaaS 的網路"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 9cb70c9d-9ed9-47cc-af5a-6403d87d3372
description: "摘要： 了解如何設計的 Microsoft Azure IaaS 中的工作負載最佳化的網路。"
ms.openlocfilehash: 2430b62e04392ddd4266d37797b18ae7e890c092
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="designing-networking-for-microsoft-azure-iaas"></a>設計 Microsoft Azure IaaS 的網路

 **摘要：**了解如何設計的 Microsoft Azure IaaS 中的工作負載最佳化的網路。
  
最佳化網路的 IT 工作量架設在 Azure IaaS 需要瞭解 Azure 虛擬網路 (VNets) 地址空格、 路由、 DNS、 和負載平衡。
  
## <a name="planning-steps-for-any-vnet"></a>規劃步驟任何 VNet

任何類型的 VNet 遵循下列步驟。
  
### <a name="step-1-prepare-your-intranet-for-microsoft-cloud-services"></a>步驟 1： 準備您的內部網路的 Microsoft 雲端服務。

經歷中[常見的元素 Microsoft cloud 連線的](common-elements-of-microsoft-cloud-connectivity.md)**步驟來準備您的 Microsoft 雲端服務的網路**區段。
  
### <a name="step-2-optimize-your-internet-bandwidth"></a>步驟 2： 最佳化您的網際網路頻寬。

最佳化您的網際網路頻寬使用中[設計的 Microsoft saas 和網路](designing-networking-for-microsoft-saas.md)的**步驟來準備您的網路 Microsoft saas 和服務的**一節的步驟 2 到 4。
  
### <a name="step-3-determine-the-type-of-vnet-cloud-only-or-cross-premises"></a>步驟 3： 判斷 VNet 類型 (僅限雲端或跨部門)。

僅限雲端 VNet 有未連線至內部網路。以下是範例。
  
**圖 1： 僅限雲端 VNet**

![圖 1：Azure 中只存在於雲端的虛擬網路](images/8be19104-02b3-4a7f-b0a0-30d6fcf8890b.png)
  
圖 1 顯示虛擬機器的一的組中僅限雲端 VNet。
  
A 跨部署 VNet 具有至網站 (S2S) 透過 Azure 閘道的內部網路的 VPN 或 ExpressRoute 連線。以下是範例。
  
**圖 2： 跨部署 VNet**

![圖 2：Azure 中跨部署的虛擬網路](images/caacf007-e0dc-45d3-9531-441109776d25.png)
  
圖 2 顯示一組的虛擬機器在跨部署 VNet，連線至內部網路中。
  
請參閱其他本文中[的跨單位 VNet 的規劃步驟](designing-networking-for-microsoft-azure-iaas.md#cross_prem)一節。
  
### <a name="step-4-determine-the-address-space-of-the-vnet"></a>步驟 4： 決定 VNet 位址空間。

表 1 顯示的位址空間 VNets 不同類型。
  
|**VNet 的類型**|**虛擬網路位址空間**|
|:-----|:-----|
|僅雲端  <br/> |任意私人位址空間  <br/> |
|僅限雲端彼此互相  <br/> |任意私人，但不是重疊與其他連線 VNets  <br/> |
|跨單位  <br/> |私人，但不是重疊與內部部署  <br/> |
|互連的跨部署  <br/> |私人，但不是重疊與內部部署與其他連線 VNets  <br/> |
   
 **表 1： 類型的 VNets 和其對應的位址空間**
  
虛擬機器時的 DHCP 指派之子網路的位址空間的地址組態：
  
- 位址/子網路遮罩
    
- 預設閘道
    
- DNS 伺服器 IP 位址
    
您也可以保留靜態 IP 位址。
  
虛擬機器可以也指派公用 IP 位址，個別或從包含雲端服務 （適用於僅限傳統部署機器）。
  
### <a name="step-5-determine-the-subnets-within-the-vnet-and-the-address-spaces-assigned-to-each"></a>步驟 5： 決定 VNet 和指派給每個位址空間內的子網路。

有兩種類型的子網路中 VNet、 閘道子網路和虛擬機器裝載的子網路。
  
**圖 3： 兩種類型的 Azure 中的子網路**

![圖 3：Azure 中的兩種子網路類型](images/2eaa512d-1293-4e9b-b927-6bfe0fc0acb4.png)
  
圖 3 是含有包含 Azure 閘道與一組的虛擬機器裝載含有虛擬機器時的子網路的閘道子網路 VNet。
  
Azure 閘道子網路會需要 Azure 主控兩個虛擬機器的 Azure 的閘道。使用至少 29 位元前置詞長度指定位址空間 (範例： 192.168.15.248/29)。建議的 28 位元或較小的前置詞長度，特別是如果您打算使用 ExpressRoute。
  
決定 Azure 閘道子網路的位址空間的最佳作法是下列：
  
1. 決定閘道子網路的大小。
    
2. VNet 的位址空間中變數的位元，設為 0 的閘道子網路所使用的位元，並將剩餘的位元設定為 1。
    
3. 轉換成十進位和 express 位址空間為具有前置詞長度設為閘道子網路的大小。
    
使用此方法之後，閘道子網路的位址空間一律為結尾處的最遠 VNet 位址空間。
  
以下是定義閘道子網路的地址前置字的範例： VNet 位址空間是 10.119.0.0/16。組織一開始會使用網站 VPN 連線，但將最後取得 ExpressRoute。表 2 顯示的步驟及決定閘道的子網路位址前置詞的網路前置詞表示法 (也稱為 CIDR) 的結果。

以下是步驟與範例判斷閘道的子網路位址前置詞：

1. 決定閘道子網路的大小。用於此範例中，我們在 [選擇 /28。
2. 設定位元 VNet 位址空間 (b) 的可變部分為 0 閘道的子網路位元 (G)，否則為 1 (V)。我們的範例中，我們使用 10.119.0.0/16 位址空間的 VNet。<br/>
<br/>10.119。 bbbbbbbb。bbbbbbbb<br/>10.119。 VVVVVVVV。VVVVGGGG<br/>10.119。 11111111。11110000<br/><br/>
3. 步驟 2 的結果轉換成十進位和 express 為位址空間。例如我們 10.119。11111111。11110000 是 10.119.255.240，並從步驟 1，(在我們的範例 28) 前置詞長度] 中，所產生的閘道的子網路位址首碼是 10.119.255.240/28。
  
如需詳細資訊，請參閱[Azure 閘道的子網路的位址空間計算器](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed)。
  
虛擬機器裝載的子網路會放置 Azure 虛擬機器，您可以根據內部一般指導方針，例如一般角色或應用程式或子網路隔離層中執行的位置。
  
Azure 每個子網路上使用的前 3 的地址。因此，可能 Azure 的子網路上的地址的數目是 2<sup>n</sup> -5，其中 n 是主機位元數。表 3 顯示的虛擬機器時所需、 數目範圍主控需要的位元和相對應的子網路大小。
  
|**所需的虛擬機器**|**主機位元**|**子網路大小**|
|:-----|:-----|:-----|
|1-3  <br/> |3  <br/> |/29  <br/> |
|4-11  <br/> |4  <br/> |/28  <br/> |
|12-27  <br/> |5  <br/> |/27  <br/> |
|28-59  <br/> |6  <br/> |/26  <br/> |
|60-123  <br/> |7  <br/> |/25  <br/> |
   
 **表 3： 虛擬機器的需求和其子網路大小**
  
如需虛擬機器上的子網路或 VNet 最大數量的詳細資訊，請參閱[網路限制](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits)。
  
如需詳細資訊，請參閱[＜ Plan and design Azure 虛擬網路](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/)。
  
### <a name="step-6-determine-the-dns-server-configuration-and-the-addresses-of-the-dns-servers-to-assign-to-vms-in-the-vnet"></a>步驟 6： 決定 DNS 伺服器設定和指派給 VNet Vm DNS 伺服器的位址。

Azure 指派虛擬機器時的 DHCP 的 DNS 伺服器的位址。DNS 伺服器可以是：
  
- 提供由 Azure： 提供本機名稱登錄與本機與網際網路名稱解析
    
- 提供您： 提供本機或網路名稱登錄與內部網路或網際網路名稱解析
    
表 4 顯示每種類型的 VNet 的 DNS 伺服器的不同設定。
    
|**VNet 的類型**|**DNS 伺服器**|
|:-----|:-----|
|僅雲端  <br/> |Azure 提供本機和網際網路名稱解析  <br/> Azure 虛擬機器的本機與網際網路名稱解析 （DNS 轉接）  <br/> |
|跨單位  <br/> |在內部的本機與內部網路名稱解析  <br/> Azure 虛擬機器的本機與內部網路名稱解析 （DNS 複寫和轉寄）  <br/> |
   
 **表 4: VNets 兩種不同類型的 DNS 伺服器選項**
  
如需詳細資訊，請參閱[Vm 和角色執行個體的名稱解析](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances)。
  
### <a name="step-7-determine-the-load-balancing-configuration-internet-facing-or-internal"></a>步驟 7： 決定負載平衡設定 （網際網路或內部）。

在某些情況下，您想要散佈的一組具有相同角色的伺服器到的傳入流量。Azure IaaS 若要這樣做為網際網路對向內建設備且內部流量負載。
  
Azure 的網際網路對向負載平衡隨機分散每個來路不明傳入流量從網際網路到負載平衡的一組的成員。
  
**圖 4： 外部負載平衡器 Azure 中**

![圖 4：Azure 中的外部負載平衡器](images/eb5945e5-0c2b-40f1-b9ed-54bb2b0f9e59.png)
  
圖 4 顯示分散每個撥入的 NAT 規則或一組負載平衡集內的虛擬機器時的端點上的內送流量的 Azure 中的外部負載平衡器。
  
Azure 內部的負載平衡隨機分散每個來自其他 Azure Vm 或從內部網路負載平衡的一組的成員電腦的來路不明傳入流量。 
  
**圖 5： 內部負載平衡器 Azure 中**

![圖 5：Azure 中的內部負載平衡器](images/d1451b73-6465-449d-b3e6-22160ce51f35.png)
  
圖 5 顯示分散每個撥入的 NAT 規則或一組負載平衡集內的虛擬機器時的端點上的內送流量的 Azure 中的內部負載平衡器。
  
如需詳細資訊，請參閱[Azure 負載平衡器](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview)。
  
### <a name="step-8-determine-the-use-of-virtual-appliances-and-user-defined-routes"></a>步驟 8： 決定使用虛擬設備和使用者定義的路由。

如果您需要轉寄至虛擬設備中您 VNet 流量，您可能需要將一或多個使用者定義的路由新增至子網路。
  
**圖 6： 虛擬設備和 Azure 中的使用者定義路由**

![圖 6：Azure 中的虛擬設備和使用者定義路由](images/f181d0f4-ebf9-439e-9c98-dec17428c32b.png)
  
圖 6 顯示跨部署 VNet 和使用者定義的路由指派給指向虛擬 appliance 的虛擬機器裝載子網路。
  
如需詳細資訊，請參閱[使用者定義的路由和 IP 轉寄](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview)。
  
### <a name="step-9-determine-how-computers-from-the-internet-will-connect-to-virtual-machines"></a>步驟 9： 決定如何從網際網路的電腦會連線至虛擬機器。

有多個提供存取網際網路才能虛擬機器上 VNet，其中包含從您組織的網路透過 proxy 伺服器或其他 edge 裝置存取的方式。
  
表 5 列出篩選或檢查來路不明的傳入流量的方法。
  
|**方法**|**部署模型**|
|:-----|:-----|
|1.端點和雲端服務上設定的 Acl  <br/> |傳統  <br/> |
|2.網路安全性群組  <br/> |資源管理員與傳統  <br/> |
|3.網際網路對向的負載平衡器以輸入 NAT 規則  <br/> |資源管理員  <br/> |
|4.網路安全性設備中 （不會顯示） Azure Marketplace  <br/> |資源管理員與傳統  <br/> |
   
 **連線至虛擬機器和其對應的 Azure 部署模型的表 5： 方法**
  
**圖 7： 透過網際網路連線至 Azure 虛擬機器**

![圖 7：透過網際網路連線到 Azure 虛擬機器](images/c5e3531b-170a-4482-a6ff-fb8fbbe81b35.png)
  
圖 7 顯示網際網路連線的電腦連線至虛擬機器使用端點的雲端服務、 使用網路安全性] 群組中，將子網路上的虛擬機器及虛擬機器上使用外部負載平衡器和撥入的 NAT 規則的子網路。
  
提供其他安全性：
  
- 遠端桌面和 SSH 連線，這會驗證與加密。
    
- 遠端 PowerShell 工作階段，這會驗證與加密。
    
- IPsec 傳輸模式，您可以使用端對端加密。
    
- Azure DDOS 保護，有助於防止外部和內部攻擊
    
如需詳細資訊，請參閱[Microsoft 雲端 Security for Enterprise 架構師](https://aka.ms/cloudarchsecurity)和[Azure 網路安全性](https://azure.microsoft.com/blog/azure-network-security/)。
  
### <a name="step-10-for-multiple-vnets-determine-the-vnet-to-vnet-connection-topology"></a>步驟 10： 針對多個 VNets 決定 VNet-VNet 連線拓撲。

VNets 可以使用類似用來連接組織的站台的拓撲彼此進行連線。
  
雛菊鏈結設定連接中一系列 VNets。
  
**圖 8： Daisy 鏈結設定 VNets**

![圖 8：Azure 虛擬網路的菊輪鍊設定](images/264d5dd4-06c5-483f-9428-a18cc1f68ac1.png)
  
圖 8 顯示五個 VNets 連線使用 daisy 鏈結組態的數列。
  
支點和中樞設定連線至中央 VNets，連線至彼此本身是一組多個 VNets。
  
**圖 9： 支點和中樞設定 VNets**

![圖 9：Azure 虛擬網路的輪輻和中樞設定](images/dd442a38-5b76-4ac5-b743-8fc7711a91ba.png)
  
圖 9 顯示六個 VNets 兩個 VNets 連接至彼此和也兩個其他支點 VNets 的集線器。
  
完整網狀設定連接至彼此的每個 VNet。
  
**圖 10： 完整網狀結構 VNets 組態**

![圖 10：Azure 虛擬網路的網狀設定](images/9dda0738-10db-4a63-95b3-79851a399b71.png)
  
圖 10 說明四種 VNets 連接至彼此、 使用六個 VNet-VNet 連線的總。
  
## <a name="planning-steps-for-a-cross-premises-vnet"></a>跨部署 VNet 的規劃步驟
<a name="cross_prem"> </a>

針對跨部署 VNet 遵循下列步驟。
  
> [!TIP]
> 若要建立模擬的跨部署的開發人員/測試環境，請參閱[Simulated 跨部署在 Azure 虛擬網路](simulated-cross-premises-virtual-network-in-azure.md)。 
  
### <a name="step-1-determine-the-cross-premises-connection-to-the-vnet-s2s-vpn-or-expressroute"></a>步驟 1： 判斷 VNet （S2S VPN 或 ExpressRoute） 跨部署的連線。

表 6 列出不同類型的連線。
  
|**連線類型**|**用途**|
|:-----|:-----|
|若要網站 (S2S) VPN  <br/> |以單一 VNet 連線 1-10 網站 （包括其他 VNets）。  <br/> |
|ExpressRoute  <br/> |透過網際網路 Exchange 提供者 (IXP) 或網路服務提供者 (NSP) Azure 私人的安全連結。  <br/> |
|若要網站點 (P2S) VPN  <br/> |會在單一電腦連線至 VNet。  <br/> |
|VNet 對等或 VNet VNet (V2V) VPN  <br/> |連接至另一個 VNet 資訊 VNet。  <br/> |
   
 **表 6： 連線類型的跨單位 VNets**
  
如需詳細的連線數目上限的詳細資訊，請參閱[網路限制](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits)。
  
如需 VPN 裝置的詳細資訊，請參閱[網站虛擬網路連線的 VPN 裝置](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices)。
  
如需 VNet 對等的詳細資訊，請參閱[VNet 對等](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview)。
  
**圖 11： 四種方式連線至跨部署 VNet**

![圖 11：連線到跨部署 Azure 虛擬網路的三種方式](images/d5d4a625-cfbd-4a77-9159-eaca69d07e93.png)
  
圖 11 顯示 VNet 與四種類型的連線： P2S 連線的電腦、 從內部網路 S2S VPN 連線、 從內部網路、 ExpressRoute 連線及來自另一個 VNet VNet-VNet 連線。 
  
您可以透過下列方式連線至 Vm VNet：
  
- 管理的 VNet Vm 從您的內部網路或網際網路
    
- 從內部網路的 IT 工作量存取
    
- 透過其他 VNets 您網路的延伸模組
    
由下列提供連線安全性：
  
- P2S 使用安全通訊端通訊協定通道通訊協定 (SSTP) 
    
- S2S 和 VNet-VNet VPN 連線會使用 IPsec 通道模式與 AES256
    
- ExpressRoute 是私人的 WAN 連線
    
如需詳細資訊，請參閱[Microsoft 雲端 Security for Enterprise 架構師](https://aka.ms/cloudarchsecurity)和[Azure 網路安全性](https://azure.microsoft.com/blog/azure-network-security/)。
  
### <a name="step-2-determine-the-on-premises-vpn-device-or-router"></a>步驟 2： 決定在內部部署 VPN 裝置或路由器。

您的內部部署 VPN 裝置或路由器做為：
  
- 終止 Azure 閘道的 S2S VPN 連線 IPsec 等。
    
- 私人的對等 ExpressRoute 連線 BPG 對等和終止點。
    
**圖 12： 內部部署 VPN 路由器或裝置**

![圖 12：內部部署 VPN 路由器或裝置](images/bd221468-a660-4730-aa55-0426986480b9.png)
  
圖 12 顯示跨部署 VNet 連線至內部部署 VPN 路由器或裝置。
  
如需詳細資訊，請參閱 ＜[關於 VPN 閘道](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways)。
  
### <a name="step-3-add-routes-to-your-intranet-to-make-the-address-space-of-the-vnet-reachable"></a>步驟 3： 將路由新增至您的內部網路進行連至 VNet 位址空間。

從內部部署路由傳送至 VNets 包含下列：
  
1. Points 正面 VPN 裝置 VNet 位址空間的路由。
    
2. 在您跨 S2S VPN 或 ExpressRoute 連接點的 VPN 裝置 VNet 位址空間路由
    
**圖 13： 內部部署路由所需進行 VNet 連至**

![圖 13：內部部署路由需要讓 Azure VNet 可以連線](images/7a1e20c1-fbc4-4cb9-9961-735da4e23307.png)
  
圖 13 顯示內部路由器和 VPN 路由器或代表 VNet 位址空間的裝置所需的路由資訊。
  
### <a name="step-4-for-expressroute-plan-for-the-new-connection-with-your-provider"></a>步驟 4： ExpressRoute，規劃的提供者的新連線。

您可以使用私人對等之間的內部網路和 Microsoft cloud 三個不同的方式建立 ExpressRoute 連線：
  
- 共同位於雲端 exchange
    
- 點對點乙太網路連線
    
- 任何-任何 (IP VPN) 網路
    
**圖 14： 使用 ExpressRoute 連線至跨部署 VNet**

![圖 14：使用 ExpressRoute 連線到跨部署 Azure 虛擬網路](images/7030bd39-69a6-4283-8567-3434e1ab6ba6.png)
  
圖 14 顯示跨部署 VNet 和 ExpressRoute 由內部路由器連線至 Microsoft Azure。
  
如需詳細資訊，請參閱[Microsoft 雲端連線 ExpressRoute](expressroute-for-microsoft-cloud-connectivity.md)。
  
### <a name="step-5-determine-the-local-network-address-space-for-the-azure-gateway"></a>步驟 5： 決定 Azure 閘道的區域網路位址空間。

路由傳送至內部部署或其他 VNets 從 VNet、 Azure 會將流量轉送跨找出指派給閘道之本機網路位址空間 Azure 閘道。
  
**圖 15： 本機網路位址空間以便跨部署 VNet**

![圖 15：跨部署 Azure 虛擬網路的區域網路位址空間](images/e3af2652-8b8e-4551-9a0b-b550e6e7e3c0.png)
  
圖 15 會顯示在 Azure 的閘道，代表在內部網路上的連至位址空間跨部署 VNet 與區域網路位址空間。 
  
您可以透過下列方式定義的區域網路位址空間：
  
- 做法 1： 目前所需的位址空間或 （更新時可能需要新增新的子網路時） 的使用中的前置詞的清單。
    
- 選項 2： 整個內部位址空間 （只需要新增新的位址空間時的更新）。
    
因為 Azure 閘道不允許摘要的路由，您必須定義選項 2 的區域網路位址空間，讓它不會納入 VNet 位址空間。
  
**圖 16: 位址空間內徑建立 VNet 位址空間**

![圖 16：虛擬網路的位址空間所建立的地址空間漏洞](images/e79c4840-f9e3-4741-9b72-59db6043aefa.png)
  
圖 16 顯示與根空間的位址空間和 VNet 位址空間的表示法。
  
以下是定義使用者的周圍的位址空間"內徑"VNet 所建立的區域網路位址空間的前置詞的範例：
  
- 組織會使用透過其內部網路中某些部分的私人位址空間 （10.0.0.0/8、 172.16.0.0/12、 / 8 以及 192.168.0.0/16）。他們選擇選項 2 和 10.100.100.0/24 作為其 VNet 位址空間。
    
表 7 示範中的步驟及產生定義此範例的區域網路位址空間的前置詞。
  
|**步驟**|**結果**|
|:-----|:-----|
|1.清單不是 VNet 位址空間根空間的前置詞。  <br/> |172.16.0.0/12 和 192.168.0.0/16  <br/> |
|2.清單變數八位元，但不包括 VNet 位址空間的最後一個使用八位元的不重疊前置詞。  <br/> |10.0.0.0/16、 10.1.0.0/16...]10.99.0.0/16、 10.101.0.0/16...]10.254.0.0/16、 10.255.0.0/16 （255 的首碼，已略過 10.100.0.0/16）  <br/> |
|3.清單內的最後一個使用八位元 VNet 位址空間的不重疊前置詞。  <br/> |10.100.0.0/24、 10.100.1.0/24...]10.100.99.0/24、 10.100.101.0/24...]10.100.254.0/24、 10.100.0.255.0/24 （255 的首碼，已略過 10.100.100.0/24）  <br/> |
   
 **表 7： 範例本機位址網路空間**
  
### <a name="step-6-configure-on-premises-dns-servers-for-dns-replication-with-dns-servers-hosted-in-azure"></a>步驟 6： 設定具有裝載在 Azure 中的 DNS 伺服器的內部 DNS 伺服器的 DNS 複寫。

若要確保內部部署電腦可以解析 Azure 型伺服器的名稱和 Azure 型伺服器可以解析內部電腦的名稱，來設定：
  
- 在您 VNet 以轉送至內部 DNS 伺服器之 DNS 伺服器
    
- DNS 複寫的適當的區域之間 DNS 伺服器的內部及 VNet
    
**圖 17： DNS 複寫及轉寄跨部署 VNet 的 DNS 伺服器**

![圖 17：跨部署 Azure 虛擬網路中 DNS 伺服器的 DNS 複寫和轉送](images/ab55e5ce-ccb0-49d4-a301-657a727f97b2.png)
  
圖 17 顯示具有 DNS 伺服器跨部署 VNet 在內部網路及 VNet 中的子網路。DNS 複寫及轉寄已設定兩部 DNS 伺服器之間。
  
### <a name="step-7-determine-the-use-of-forced-tunneling"></a>步驟 7： 決定使用強制通道。

Azure 的子網路的預設系統路由會指向網際網路。若要確保從虛擬機器時的所有流量一起都出差之間的跨部署的連線，建立路由表格與預設路由使用 Azure 閘道作為其下個躍點位址。然後將路由表建立關聯與子網路。這就是所謂強制通道。如需詳細資訊，請參閱 ＜ [Configure 強制通道](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm)。
  
**圖 18： 使用者定義的路由和強制通道的跨單位 VNet**

![圖 18：跨部署 Azure 虛擬網路的使用者定義路由和強制通道](images/1e545ec6-c2d9-48d2-bb5e-e0a581fee004.png)
  
圖 18 顯示以指向 Azure 閘道的子網路的使用者定義路由跨部署 VNet。
  
## <a name="sharepoint-server-2016-farm-in-azure"></a>SharePoint Server 2016 Azure 中的伺服器陣列
<a name="cross_prem"> </a>

IT 工作負載架設在 Azure IaaS 內部網路的範例是高可用性、 多層的 SharePoint Server 2016 伺服器陣列。
  
**圖 19： 高度可用的內部網路 SharePoint Server 2016 中的伺服器陣列 Azure IaaS**

![Azure IaaS 中高可用性的 SharePoint Server 2016 伺服器陣列](images/3a922e21-df91-455f-ba90-78abdd48d98d.png)
  
圖 19 顯示部署中使用內部負載平衡器的前端和資料層跨部署 VNet 的 SharePoint Server 2016 伺服器陣列的九個伺服器。如需詳細資訊，包括逐步設計及部署指示，請參閱[Microsoft Azure 中的 SharePoint Server 2016](https://technet.microsoft.com/library/mt779107%28v=office.16%29.aspx)。
  
> [!TIP]
> 若要建立單一伺服器的 SharePoint Server 2016 伺服器陣列中模擬的跨部署 VNet，請參閱[Azure 的開發人員測試環境中的內部網路 SharePoint Server 2016](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)。 
  
如需其他範例虛擬跨部署 Azure 中的虛擬機器上部署的 IT 工作負載的網路，請參閱[Azure IaaS 的混合式雲端案例](https://technet.microsoft.com/library/mt750502.aspx)。
  
## <a name="see-also"></a>另請參閱

<a name="cross_prem"> </a>

[Microsoft Cloud Networking for Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)

[Microsoft 的 Enterprise Cloud 藍圖：IT 決策者的資源](https://sway.com/FJ2xsyWtkJc2taRD)



