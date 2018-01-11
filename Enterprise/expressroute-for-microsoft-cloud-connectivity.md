---
title: "Microsoft 雲端連線 ExpressRoute"
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
ms.assetid: bf2295c4-d411-49cd-aaa5-116a4a456c5a
description: "摘要： 了解如何 ExpressRoute 可協助您更快且更可靠連線至 Microsoft 雲端服務和平台。"
ms.openlocfilehash: 4534f06e5d4eca759aadb9b589e39f0c8cdeffb1
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2018
---
# <a name="expressroute-for-microsoft-cloud-connectivity"></a>Microsoft 雲端連線 ExpressRoute

 **摘要：**了解如何 ExpressRoute 可協助您更快且更可靠連線至 Microsoft 雲端服務和平台。
  
ExpressRoute 可提供連線至 Microsoft 雲端服務的隱私、專屬、高輸送量網路連線。
  
## <a name="expressroute-to-the-microsoft-cloud"></a>以 Microsoft cloud ExpressRoute

以下是 Microsoft cloud ExpressRoute 連線的網路路徑。
  
**圖 1： 網路路徑不 ExpressRoute**

![圖 1：不使用 ExpressRoute 的網路路徑](images/Network_Poster/ExpressRoute.png)
  
圖 1 顯示的內部網路與 Microsoft cloud 之間的一般路徑。在內部網路邊緣連線至網際網路透過 WAN 連結的 ISP。流量然後一起出差經由網際網路 Microsoft cloud 的邊緣。Microsoft 雲端中的雲端方案包含 Office 365、 Microsoft Azure、 Microsoft Intune 及 Dynamics 365。組織中的使用者可以是位在內部網路或網際網路上。
  
沒有 ExpressRoute 連線，僅部分的 Microsoft cloud 流量路徑您可以控制 （且與服務提供者的關係） 是您在內部網路邊緣和您的 ISP 之間的連結。 
  
您的 ISP 與 Microsoft cloud 邊緣間的路徑是適合投入比傳遞系統中斷、 流量壅塞以及監控惡意使用者在網際網路上。
  
漫遊或遠端使用者，例如，在網際網路上的使用者透過網際網路傳送至 Microsoft cloud 其流量。
  
以下是 Microsoft cloud ExpressRoute 連線的網路路徑。
  
**圖 2： 網路路徑與 ExpressRoute**

![圖 2：使用 ExpressRoute 的網路路徑](images/Network_Poster/ExpressRoute_post.png)
  
圖 2 顯示兩個網路路徑。Microsoft Intune 流量一起出差標準網際網路流量為相同的路徑。Office 365、 Microsoft Azure 和 Dynamics 365 達成跨 ExpressRoute 連線、 專用的路徑與內部網路的 edge 和 Microsoft cloud 緣之間的流量。
  
包含 ExpressRoute 連線，您現在可控制，透過與服務提供者的關係，透過 Microsoft 自您的整個流量路徑雲端 edge。可預測的效能與達 99.9%執行時間 SLA 可以提供此連線。
  
您現在可以計算上可預測的輸送量和延遲，根據到 Office 365、 Azure、 和 Dynamics 365 服務的服務提供者的連線。Microsoft Intune ExpressRoute 連線不支援這一次。
  
受限於網際網路中斷、 流量壅塞及監視不再有透過 ExpressRoute 連線傳送的流量。
  
漫遊或遠端使用者，例如，在網際網路上的使用者仍會傳送給 Microsoft cloud 其流量透過網際網路。有一個例外是架設在 Azure IaaS，透過遠端存取連線至內部網路 ExpressRoute 連傳送的商務應用程式的內部網路線條的流量。
  
即使具有 ExpressRoute 連線，某些流量仍傳送網際網路 DNS 查詢，例如憑證撤銷清單檢查，而且內容傳遞網路 (CDN) 要求。
  
請參閱如需詳細資訊下列額外資源：
  
- [Office 365 ExpressRoute](https://aka.ms/expressrouteoffice365)
    
- [Azure ExpressRoute](https://azure.microsoft.com/services/expressroute/)
    
## <a name="advantages-of-expressroute-for-azure"></a>Azure ExpressRoute 的優點

以下是使用 ExpressRoute Azure 型雲端服務的部分優點：
  
- **可預測的效能：**包含 Microsoft cloud 緣專用路徑，您的效能不會受限於網際網路提供者中斷與暴增在網際網路的流量。您可以決定並保留以 Microsoft cloud 努力輸送量和延遲 SLA 來提供者。
    
- **您流量資料隱私權：**透過專用的 ExpressRoute 連線傳送的流量不會受限於網際網路監控或封包擷取及分析惡意使用者。它會為安全使用多重通訊協定標籤切換 MPLS 為基礎的 WAN 連結。
    
- **高輸送量連線：**整體 ExpressRoute 連線 exchange 提供者及網路服務提供者支援，您可以取得最多 10 個 Gbps 連結到 Microsoft 雲端。
    
- **降低成本的一些設定：**雖然 ExpressRoute 連線的其他成本，但在某些情況下的單一 ExpressRoute 連線可以成本小於增加提供適當輸送量 Microsoft 雲端服務在多個位置貴組織的網際網路容量。
    
ExpressRoute 連線不保證郵件可以在每個設定較高的效能。有可能已透過低頻寬 ExpressRoute 連線比為只從地區的 Microsoft 資料中心幾個躍點高頻寬網際網路連線的較低的效能。
  
搭配 Office 365 使用 ExpressRoute 的最新建議，請參閱[Office 365 ExpressRoute](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd)。
  
## <a name="expressroute-connectivity-models"></a>ExpressRoute connectivity 模型

表 1 顯示 ExpressRoute 連線的三個主要 connectivity 的模型。
  
|**共同位於雲端 exchange**|**點對點乙太網路**|**任何-任何 (IP VPN) 連線**|
|:-----|:-----|:-----|
|![ExpressRoute 連接模型：共置在雲端 Exchange 中](images/Network_Poster/ER_Conn1.png)|![ExpressRoute 連接模型：點對點乙太網路](images/Network_Poster/ER_Conn2.png)|![ExpressRoute 連接模型：多點對多點 (IP VPN) 連線](images/Network_Poster/ER_Conn3.png)|
|如果您的資料中心共同位於與雲端 exchange 設備、 可排序虛擬跨連線至 Microsoft 雲端透過代管提供者的乙太網路交換。  <br/> |如果您的資料中心位於您內部部署，您可以使用的點對點乙太網路連結來連線至 Microsoft cloud。  <br/> |如果您已經在使用的 IP VPN (MPLS) 提供者連接組織的網站、 Microsoft cloud ExpressRoute 連線 bot 通常在私人的 WAN 的另一個位置。  <br/> |
   
 **表 1: ExpressRoute connectivity 模型**
  
## <a name="expressroute-peering-relationships-to-microsoft-cloud-services"></a>Microsoft 雲端服務的 ExpressRoute 對等關係

單一 ExpressRoute 連線支援多達三個不同框線閘道通訊協定 (BGP) 對等關聯至 Microsoft cloud 的不同組件。BPG 使用對等的關聯性建立信任及 exchange 路由資訊。
  
**圖 3: 三個不同 BGP 關係中的單一 ExpressRoute 連線**

![圖 3：單一的 ExpressRoute 連線中三種不同的 BGP關係](images/Network_Poster/ERPeering.png)
  
圖 3 是從內部網路 ExpressRoute 連線。ExpressRoute 連線包含三個邏輯的對等關係。Microsoft 對等關係前往 Microsoft saas 和服務，包括 Office 365 和 Dynamcs CRM Online。公用的對等關係會移至 Azure PaaS 服務。私人的對等關係會移至 Azure IaaS 以及主控虛擬機器時的虛擬網路閘道。
  
Microsoft 對等 BGP 關係： 
  
- 在您 DMZ 路由器從 Office 365 和 Dynamics 365 服務公用地址。 
    
- 支援雙向起始的通訊。
    
公用的對等 BGP 關係：
  
- 在您 DMZ 路由器從 Azure 服務公用 IP 位址。
    
- 支援單向起始通訊從僅內部部署系統。對等關係不支援從 Azure PaaS 服務起始的通訊。
    
私人的對等 BGP 關係：
  
- 從您組織的網路邊緣上的路由器指派給 Azure VNets 的私人 IP 位址。
    
- 支援雙向起始的通訊。
    
- 為副檔名為 Microsoft cloud 完成與內部一致的處理和路由傳送至您組織的網路。
    
## <a name="example-of-application-deployment-and-traffic-flow-with-expressroute"></a>使用 ExpressRoute 的應用程式部署和流量流程的範例

流量一起出差 ExpressRoute 連線和 Microsoft cloud 內是在路徑的來源與目的地及應用程式的行為之間旋入之路由的函數。以下是透過網站 VPN 連線存取內部部署 SharePoint 伺服器陣列 Azure 虛擬機器上執行的應用程式的範例。
  
**圖 4： 應用程式存取內部部署 SharePoint 伺服器陣列 Azure 虛擬機器上**

![圖 4：Azure 虛擬機器上的應用程式，會存取內部部署 Sharepoint 伺服器陣列](images/Network_Poster/ER_App_Flow1.png)

  
圖 4 顯示內部部署 SharePoint 伺服器陣列、 網站 VPN 連線與內部網路和虛擬網路以 Azure IaaS、 Azure IaaS 虛擬機器與流量所執行的應用程式伺服器之間的應用程式伺服器之間的流程和SharePoint 伺服器陣列。
  
會找出應用程式使用的內部 DNS 的 SharePoint 伺服器陣列的 IP 位址及所有流量會都移至網站 VPN 連線。
  
此組織移轉至 SharePoint Online 在 Office 365 中的其內部部署 SharePoint 伺服器陣列並部署 ExpressRoute 連線。
  
**圖 5： 將內部部署 SharePoint 伺服器陣列移至 SharePoint Online**

![圖 5：將內部部署 SharePoint 伺服器陣列移動到 SharePoint Online](images/Network_Poster/Hairpin1.png)
  
圖 5 顯示的對等相關聯的 ExpressRoute 連線至 Microsoft saas 和與 Office 365 和 Azure IaaS 包含應用程式伺服器上的虛擬網路。SharePoint 內部部署伺服器陣列已移轉至 Office 365。
  
Microsoft 與私人的對等關係：
  
- Azure 虛擬網路閘道，從內部部署位置中都是可用的 ExpressRoute 連線。
    
- 從 Office 365 訂閱的 edge 裝置，例如 proxy 伺服器的公用 IP 位址是透過提供 ExpressRoute 連線。
    
- 從內部網路邊緣、 Azure VNet 的私人 IP 位址與 Office 365 的公用 IP 位址是透過提供 ExpressRoute 連線。
    
時之應用程式存取 Url 的 SharePoint Online，它會跨 ExpressRoute 連線到 proxy 伺服器中的 edge 轉寄其流量。 
  
時使用 proxy 伺服器尋找 SharePoint Online 的 IP 位址，它會回復 ExpressRoute 連轉送流量。回應流量一起出差反向的路徑。
  
**圖 6： 流量已移轉至 SharePoint Online 在 Office 365 中的 SharePoint 伺服器陣列**

![圖 6：當 SharePoint 伺服器陣列已移轉至 Office 365 的 SharePoint Online 時的流量](images/Network_Poster/Hairpin2.png)

  
圖 6 顯示應用程式伺服器與 SharePoint Online 在 Office 365 之間的流量透過 Microsoft 對等關係流向透過私人對等關係從應用程式伺服器的內部網路邊緣，然後從邊緣Office 365。
  
結果是行為的字形固定的路由和應用程式的後果。
  
## <a name="expressroute-and-microsofts-cloud-network"></a>ExpressRoute 與 Microsoft 的雲端網路

ExpressRoute 連線會提供兩種不同的版本： ExpressRoute 與 ExpressRoute Premium。
  
### <a name="expressroute"></a>ExpressRoute

如何組織網路與 Microsoft 資料中心是組合之間一起出差的流量：
  
- 您的位置。
    
- Microsoft 雲端對等的位置 （以連線至 Microsoft edge 的實體位置）。
    
- Microsoft 資料中心位置。
    
Microsoft 資料中心及雲端對等位置所有連線至 Microsoft cloud 網路。
  
當您建立 ExpressRoute 連線至 Microsoft cloud 對等位置時，您會連線到 Microsoft cloud 網路和同一個大陸中的所有 Microsoft 資料中心位置。透過 Microsoft 雲端網路執行是雲端對等位置與目的地 Microsoft 資料中心之間的流量。
  
這可能會導致非最佳傳遞到任何-任何 connectivity 模型的本機 Microsoft 資料中心。
  
**地理位置分散之組織所使用的單一 ExpressRoute 連線的圖 7： 範例**

![圖 7：地理位置分散的組織使用單一 ExpressRoute 連線的範例](images/Network_Poster/MSNet1.png)
  
圖 7 顯示兩個位置與組織中的美國西北位置 1 和東北中的位置 2。他們是透過任何-任何 WAN 提供者連接。此組織也有 ExpressRoute 連線到西岸上的 Microsoft 對等位置。東北目的地東岸 datacenter 位置 2 流量必須旅行社一直跨組織的 WAN 西岸到 Microsoft 對等的位置並再回到跨國家透過 Microsoft 雲端網路東岸資料中心。
  
最佳傳遞的使用多個 ExpressRoute 連線至區域 Microsoft cloud 對等的位置。 
  
**圖 8： 使用多個 ExpressRoute 連線到地區資料中心的最佳傳遞**

![圖 8：使用多重 ExpressRoute 連線，以求對區域資料中心傳遞的最佳化](images/Network_Poster/MSNet2.png)
  
圖 8 顯示含有兩個 ExpressRoute 連線，一個用於每個位置、 地域本機 Microsoft 對等位置相同組織。在此組態中，位置 2 東北目的地東岸資料中心中的流量會移至東岸對等位置直接、 Microsoft cloud 網路]、 [東岸資料中心。
  
多個 ExpressRoute 連線可以提供：
  
- 更好的效能與地域本機 Microsoft 資料中心位置。
    
- 以 Microsoft cloud 本機 ExpressRoute 連線變成無法使用時的較高可用性。
    
這項措施適用於在同一個大陸的組織。不過，透過網際網路一起出差到外部組織的大陸 Microsoft 資料中心的流量。
  
對於洲際透過 Microsoft 雲端網路流量，您必須使用 ExpressRoute 高階的連線。
  
### <a name="expressroute-premium"></a>ExpressRoute Premium

對於全域分散於 continents 的組織而言，您可以使用 ExpressRoute Premium。 
  
使用 ExpressRoute Premium 您可以達到任何大陸從任何大陸上任何 Microsoft 對等位置上的任何 Microsoft 資料中心。透過 Microsoft 雲端網路執行是 continents 之間的流量。
  
含有多個 ExpressRoute Premium 連線，您可以：
  
- Continentally 本機 Microsoft 資料中心來提升效能。
    
- 以全域 Microsoft cloud 本機 ExpressRoute 連線變成無法使用時的較高可用性。
    
ExpressRoute Premium 是必要的 Office 365 型 ExpressRoute 連線。不過，是企業版與 500 或更多授權使用者的其他成本。
  
**圖 9： World wide Microsoft cloud 網路**

![圖 9：全球 Microsoft 雲端網路](images/Network_Poster/MSNet3.png)
  
圖 9 顯示組成的全球 Microsoft 雲端網路涵蓋 continents 與全球和其相對的區域網路的邏輯圖。與 Microsoft cloud 網路中每一個大陸的部分全域企業 ExpressRoute Premium 連線從建立其區域 hub 辦公室本機 Microsoft 對等的位置。
  
區域的 office、 適用 Office 365 流量：
  
- 透過 Microsoft 雲端網路內大陸一起出差大陸 Office 365 資料中心。
    
- Office 365 資料中心中另一個大陸一起出差洲際 Microsoft cloud 網路。
    
如需詳細資訊，請參閱：
  
- [Azure ExpressRoute for Office 365 訓練](https://channel9.msdn.com/series/aer/)
    
- [網路規劃和 Office 365 的效能調整](https://aka.ms/tune)
    
- [Office 365 績效管理](https://mva.microsoft.com/en-US/training-courses/office-365-performance-management-8416)
    
## <a name="expressroute-options"></a>ExpressRoute 選項

您也可以將下列選項併入 ExpressRoute 部署中：
  
- **您邊緣的安全性：**若要提供進階的安全性的流量傳送和接收透過 ExpressRoute 連線，例如流量檢查或入侵/惡意程式碼偵測置於您 DMZ 內或在您的內部網路的框線的流量路徑中的安全性設備。
    
    若要防止 Azure Vm 初始化直接與網際網路位置流量的 Vm 的網際網路流量 advertise 預設路由給 Microsoft。跨 ExpressRoute 連線及透過您的內部部署 proxy 伺服器路由傳送至網際網路的流量。Azure Vm Azure PaaS 服務或 Office 365 的流量路由傳送回跨 ExpressRoute 連線。
    
- **WAN 最佳化程式：**您可以部署在私人的對等連線的兩側 WAN 最佳化程式跨部署 azure 虛擬網路 (VNet)。Azure VNet、 內使用 Azure marketplace 和使用者定義路由的 WAN 最佳化網路 appliance 透過 appliance 的流量路由傳送。
    
- **服務品質：**使用您的流量 IPv4 標頭中的區別服務代碼點 (DSCP) 值標示語音、 互動式視訊/，或最大的努力傳遞。這是特別重要的 Microsoft 對等關係與 Skype 商務 Online 流量。
    
請參閱如需詳細資訊下列額外資源：
  
- [Office 365 ExpressRoute](https://aka.ms/expressrouteoffice365)
    
- [Azure ExpressRoute for Office 365 訓練](https://channel9.msdn.com/series/aer/)
    
- [Azure ExpressRoute](https://azure.microsoft.com/services/expressroute/)
    
## <a name="see-also"></a>請參閱

[Microsoft Cloud Networking for Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)

[Microsoft 的 Enterprise Cloud 藍圖：IT 決策者的資源](https://sway.com/FJ2xsyWtkJc2taRD)



