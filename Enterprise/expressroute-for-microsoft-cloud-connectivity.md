---
title: Microsoft 雲端連線的 ExpressRoute
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/12/2019
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: bf2295c4-d411-49cd-aaa5-116a4a456c5a
description: 摘要： 了解如何 ExpressRoute 可協助您使用速度更快且更可靠連線至 Microsoft 雲端服務與平台。
ms.openlocfilehash: a3b36e98c946bc3ae7281bd38cd4b98820ee8afb
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "30574007"
---
# <a name="expressroute-for-microsoft-cloud-connectivity"></a>Microsoft 雲端連線的 ExpressRoute

 **摘要：** 了解如何 ExpressRoute 可協助您使用速度更快且更可靠連線至 Microsoft 雲端服務與平台。
  
ExpressRoute 可提供連線至 Microsoft 雲端服務的隱私、專屬、高輸送量網路連線。
  
## <a name="expressroute-to-the-microsoft-cloud"></a>Microsoft cloud 的 ExpressRoute

以下是 Microsoft cloud 不含 ExpressRoute 連線的網路路徑。
  
**圖 1：不使用 ExpressRoute 的網路路徑**

![圖 1：不使用 ExpressRoute 的網路路徑](media/Network-Poster/ExpressRoute.png)
  
圖 1 顯示在內部網路與 Microsoft 雲端之間的一般路徑。 在內部網路邊緣連線到網際網路透過 WAN 連結的 ISP。 流量然後一起出差在網際網路上的 Microsoft cloud 邊緣。 在 Microsoft cloud 中的雲端供應項目包括 Office 365、 Microsoft Azure、 Microsoft Intune 和 Dynamics 365。 組織的使用者可以位於內部網路或網際網路上。
  
如果沒有 ExpressRoute 連線，只有部分的 Microsoft 雲端的流量路徑可讓您控制 （與具有與服務提供者的關係） 是您在內部網路邊緣和您的 ISP 之間的連結。 
  
您的 ISP 和 Microsoft 雲端邊緣之間的路徑是受限於中斷、 流量壅塞及監視惡意使用者在網際網路上的最佳傳遞系統。
  
漫遊或遠端使用者，例如，在網際網路上的使用者透過網際網路傳送至 Microsoft cloud 與其流量。
  
以下是以 Microsoft cloud 具有 ExpressRoute 連線的網路路徑。
  
**圖 2：使用 ExpressRoute 的網路路徑**

![圖 2：使用 ExpressRoute 的網路路徑](media/Network-Poster/ExpressRoute-post.png)
  
圖 2 顯示兩個網路路徑。 Microsoft Intune 的流量傳輸路徑相同一般網際網路流量。 Office 365、 Microsoft Azure 和 Dynamics 365 達成跨 ExpressRoute 連線、 內部網路邊緣與 Microsoft 雲端的邊緣之間的專用的路徑流量。
  
使用 ExpressRoute 連線] 中，您現在沒有控制權，透過服務供應商關係，透過 Microsoft 自您的整個流量路徑雲端 edge。 此連線所能提供可預測的效能與[99.95%執行時間 SLA](https://azure.microsoft.com/support/legal/sla/expressroute/v1_3/)。
  
您現在可以倚賴可預測的輸送量和延遲，根據您的服務提供者連線，Office 365、 Azure 和 Dynamics 365 服務。 ExpressRoute 連線至 Microsoft Intune 不支援這一次。
  
ExpressRoute 連線傳送的流量會不再受到網際網路中斷、 流量壅塞和監視。
  
在網際網路上，例如漫遊或遠端使用者，使用者仍會傳送至 Microsoft cloud 與其流量透過網際網路。 其中一個例外是裝載在 Azure IaaS，透過內部部署網路的遠端存取連線 ExpressRoute 連線傳送中的企業營運應用程式內部網路線的流量。
  
即使具有 ExpressRoute 連線，某些流量仍會傳送網際網路 DNS 查詢，例如憑證撤銷清單檢查，以及內容傳遞網路 (CDN) 要求。
  
請參閱這些額外的資源，如需詳細資訊：
  
- [ExpressRoute for Office 365](https://aka.ms/expressrouteoffice365)
    
- [Azure ExpressRoute](https://azure.microsoft.com/services/expressroute/)
    
## <a name="advantages-of-expressroute-for-azure"></a>Azure ExpressRoute 的優點

以下是使用 ExpressRoute 的以 Azure 為基礎的雲端服務的一些優點：
  
- **可預測的效能：** Microsoft cloud 的邊緣專用路徑，您的效能不會受限於網際網路提供者中斷與尖峰中的網際網路流量。 您可以判斷並保留您的提供者至 Microsoft 雲端中負責對輸送量和延遲 SLA。
    
- **為您的流量資料隱私權：** 您專用的 ExpressRoute 連線傳送的流量不會受限於網際網路監控或封包擷取及分析惡意使用者。 它是一樣安全使用多重通訊協定標籤切換 MPLS 架構的 WAN 連結。
    
- **高輸送量連線：** Exchange 提供者和網路服務提供者的 ExpressRoute 連線的整體支援，您可以取得最多 10 個 Gbps 連結至 Microsoft 雲端。
    
- **降低成本的一些設定：** 雖然 ExpressRoute 連線支付額外的費用，在某些情況下單一 ExpressRoute 連線可以成本小於增加網際網路容量在貴組織的多個位置提供給 Microsoft 雲端服務的適當輸送量。
    
ExpressRoute 連線並不保證郵件的較高的效能，每個組態中。 它可能會有較低的效能透過低頻寬 ExpressRoute 連線較高頻寬網際網路連線，則只有幾個躍點開地區的 Microsoft 資料中心。
  
使用 ExpressRoute 與 Office 365 的最新的建議，請參閱[ExpressRoute for Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd)。
  
## <a name="expressroute-connectivity-models"></a>ExpressRoute 連接模型

表 1 顯示 ExpressRoute 連線的三個主要 connectivity 模型。
  
|**共置在雲端 exchange**|**點對點乙太網路**|**任何對多 (IP VPN) 連線**|
|:-----|:-----|:-----|
|![ExpressRoute 連接模型：共置在雲端 Exchange 中](media/Network-Poster/ER-Conn1.png)|![ExpressRoute 連接模型：點對點乙太網路](media/Network-Poster/ER-Conn2.png)|![ExpressRoute 連接模型：多點對多點 (IP VPN) 連線](media/Network-Poster/ER-Conn3.png)|
|如果您的資料中心共同位於設備與雲端 exchange 中，您可以依虛擬跨-連線到代管提供者的乙太網路 exchange 透過 Microsoft 雲端。  <br/> |如果您的資料中心位於您內部部署，您可以使用點對點乙太網路連結來連線至 Microsoft 雲端。  <br/> |如果您已連線您組織的站台使用 IP VPN (MPLS) 提供者，Microsoft cloud ExpressRoute 連線的行為類似您私人 WAN 上的另一個位置。  <br/> |
   
 **表 1: ExpressRoute 連線模型**
  
## <a name="expressroute-peering-relationships-to-microsoft-cloud-services"></a>Microsoft 雲端服務的 ExpressRoute 對等關係

單一 ExpressRoute 連線支援最多兩個不同框線閘道通訊協定 (BGP) 對等關係的 Microsoft cloud 的不同組件。 BPG 使用對等關係來建立信任關係，且 exchange 路由的資訊。
  
**圖 3: 兩個不同的 BGP 關係中的單一的 ExpressRoute 連線**

![圖 3: 兩個不同的 BGP 關係中的單一的 ExpressRoute 連線](media/Network-Poster/ERPeering.png)
  
圖 3 顯示從內部網路的 ExpressRoute 連線。 ExpressRoute 連接有兩個邏輯的對等關係。 Microsoft 對等關係移至 Microsoft SaaS 服務，包括 Office 365、 Dynamcs 365 和 Azure PaaS 服務。 Azure IaaS，並裝載虛擬機器的虛擬網路閘道，則會移私用的對等關係。
  
Microsoft 對等 BGP 關係： 
  
- 從您 DMZ 中的路由器為 Office 365、 Dynamics 365 和 Azure 服務的公用地址。 
    
- 支援雙向起始通訊。
    
私用的對等 BGP 關係：
  
- 從組織網路邊界的路由器為指派給 Azure Vnet 的私人 IP 位址。
    
- 支援雙向起始通訊。
    
- 是您組織網路的 Microsoft cloud，完整的內部一致的處理和路由的擴充功能。

>[!Note]
>在舊版的這篇文章所述的公用對等 BGP 關係已被取代。
>
    
## <a name="example-of-application-deployment-and-traffic-flow-with-expressroute"></a>使用 ExpressRoute 的應用程式部署和流量流程的範例

流量流經 ExpressRoute 連線，並在 Microsoft cloud 中的方式是在路徑的來源與目的地和應用程式行為之間躍點路由的函式。 以下是透過站台對站 VPN 連線會存取內部部署 SharePoint 伺服器陣列的 Azure 虛擬機器上執行應用程式的範例。
  
**圖 4：Azure 虛擬機器上的應用程式，會存取內部部署 SharePoint 伺服器陣列**

![圖 4：Azure 虛擬機器上的應用程式，會存取內部部署 SharePoint 伺服器陣列](media/Network-Poster/ER-App-Flow1.png)

  
圖 4 顯示應用程式伺服器之間流動的內部部署 SharePoint 伺服器陣列、 內部網路與在 Azure IaaS 中，為 Azure IaaS 虛擬機器和流量執行應用程式伺服器的虛擬網路之間的站台對站 VPN 連線和在 SharePoint 伺服器陣列。
  
應用程式找出 SharePoint 伺服器陣列使用內部部署 DNS 的 IP 位址和所有流量透過站台對站 VPN 連線。
  
此組織移轉至 Office 365 中 SharePoint Online 的其內部部署 SharePoint 伺服器陣列，並部署 ExpressRoute 連線。
  
**圖 5：將內部部署 SharePoint 伺服器陣列移動到 SharePoint Online**

![圖 5：將內部部署 SharePoint 伺服器陣列移動到 SharePoint Online](media/Network-Poster/Hairpin1.png)
  
圖 5 顯示與對等關係的 ExpressRoute 連線新增至 Microsoft SaaS 和 Office 365 和 Azure IaaS 包含虛擬網路上的應用程式伺服器。 SharePoint 內部部署伺服器陣列已移轉至 Office 365。
  
與 Microsoft 私用的對等關係：
  
- 從 Azure 虛擬網路閘道，內部部署位置都是可用的 ExpressRoute 連線。
    
- 從 Office 365 訂閱，公用 IP 位址的邊緣裝置，例如 proxy 伺服器，可透過 ExpressRoute 連線。
    
- 從內部網路邊緣，Azure VNet 的私人 IP 位址和 Office 365 的公用 IP 位址都是可用的 ExpressRoute 連線。
    
當應用程式存取 Url 的 SharePoint Online 時，它會透過 ExpressRoute 連線至 edge 中的 proxy 伺服器轉送其流量。 
  
時使用 proxy 伺服器會找出 SharePoint Online 的 IP 位址，它會將流量轉送回透過 ExpressRoute 連線。 回應流量流經反向路徑。
  
**圖 6：當 SharePoint 伺服器陣列已移轉至 Office 365 的 SharePoint Online 時的流量**

![圖 6：當 SharePoint 伺服器陣列已移轉至 Office 365 的 SharePoint Online 時的流量](media/Network-Poster/Hairpin2.png)

  
圖 6 顯示如何應用程式伺服器與 Office 365 中 SharePoint Online 之間的流量透過私人的對等關係，從內部部署網路邊界，應用程式伺服器，然後從 edge 上流通 Microsoft 對等關係Office 365。
  
結果是髮型釘選的路由和應用程式行為的後果。
  
## <a name="expressroute-and-microsofts-cloud-network"></a>ExpressRoute 和 Microsoft 的雲端網路

兩個不同的版本中的 ExpressRoute 連線可用： ExpressRoute 和 ExpressRoute 進階版。
  
### <a name="expressroute"></a>ExpressRoute

如何流量流經之間您組織的網路與 Microsoft 資料中心是組合：
  
- 您的位置。
    
- Microsoft 雲端對等的位置 （連線至 Microsoft edge 的實體位置）。
    
- Microsoft 資料中心位置。
    
Microsoft 資料中心和對等位置的雲端所有連線至 Microsoft 雲端網路。
  
當您建立 ExpressRoute 連線至 Microsoft 雲端的對等位置時，您會連線至 Microsoft 雲端網路與中相同洲的所有 Microsoft 資料中心位置。 雲端對等位置與目的地 Microsoft 資料中心之間的流量會存在於 Microsoft 雲端網路。
  
這可能導致非最佳傳遞至本機 Microsoft 資料中心，任何對多 connectivity 模型。
  
**使用單一 ExpressRoute 連線的地理位置分散的組織圖 7： 範例**

![使用單一 ExpressRoute 連線的地理位置分散的組織圖 7： 範例](media/Network-Poster/MSNet1.png)
  
圖 7 顯示兩個位置，組織中的美國西北位置 1 和東北中的位置 2。 他們是透過任何對多 WAN 提供者連接。 此組織也有 ExpressRoute 連線到西岸上的 Microsoft 對等位置。 東北目的地東西岸資料中心中的來自位置 2 流量必須旅行一路跨組織的 WAN 西岸，Microsoft 對等的位置，然後再回到國內各地透過 Microsoft 雲端網路東西岸資料中心。
  
最佳傳遞，使用多重 ExpressRoute 連線至地區的 Microsoft 雲端對等位置。 
  
**圖 8：使用多重 ExpressRoute 連線，以求對區域資料中心傳遞的最佳化**

![圖 8：使用多重 ExpressRoute 連線，以求對區域資料中心傳遞的最佳化](media/Network-Poster/MSNet2.png)
  
圖 8 顯示相同的組織有兩個 ExpressRoute 連線，其中每個位置，請到當地 Microsoft 對等位置。 在此組態中，從位置 2 在目的地東西岸資料中心東北流量直接至東西岸對等位置、 Microsoft 雲端網路時，然後再到東亞西岸資料中心。
  
多重 ExpressRoute 連線可以提供：
  
- 當地 Microsoft 資料中心位置的較佳效能。
    
- 至 Microsoft 雲端的本機的 ExpressRoute 連線變成無法使用時的高可用性。
    
這非常適合在同一個洲的組織。 不過，在網際網路上移動到 Microsoft 資料中心外部組織的洲的流量。
  
洲際透過 Microsoft 雲端網路流量，您必須使用 ExpressRoute 高階連線。
  
### <a name="expressroute-premium"></a>ExpressRoute 進階版

全域分佈洲的組織，您可以使用 ExpressRoute 進階版。 
  
使用 ExpressRoute 進階版，您可以連線到任何大陸上任何大陸任何 Microsoft 對等位置上的任何 Microsoft 資料中心。 Continents 之間的流量會存在於 Microsoft 雲端網路。
  
使用多重 ExpressRoute 高階連線，您可以：
  
- Continentally 本機 Microsoft 資料中心的較佳效能。
    
- 至全域的 Microsoft cloud 本機的 ExpressRoute 連線變成無法使用時的高可用性。
    
需要 Office 365 型 ExpressRoute 連線 ExpressRoute 進階版。
  
**圖 9： 全球 Microsoft 雲端網路**

![圖 9： 全球 Microsoft 雲端網路](media/Network-Poster/MSNet3.png)
  
圖 9 顯示全球 Microsoft 雲端網路，跨洲和全球和其相對的區域網路使用的邏輯圖表。 與 Microsoft 雲端網路中每個洲的一部分，全域企業會建立 ExpressRoute 高階連線從其地區中心辦公室到本機 Microsoft 對等位置。
  
地區的 office、 適當的 Office 365 流量：
  
- 大陸 Office 365 資料中心，透過 Microsoft 雲端網路內大陸。
    
- 在另一個洲的 office 365 資料中心，透過洲際的 Microsoft 雲端網路。
    
如需詳細資訊，請參閱：
  
- [Azure ExpressRoute for Office 365 訓練](https://channel9.msdn.com/series/aer/)
    
- [Office 365 的網路規劃與效能調整](https://aka.ms/tune)
    
## <a name="expressroute-options"></a>ExpressRoute 選項

您也可以將下列選項併入 ExpressRoute 部署：
  
- **安全性，請參閱您 edge:** 若要流量傳送和接收透過 ExpressRoute 連線，例如流量檢查或入侵/惡意程式碼偵測，提供進階的安全性放置安全性設備中的流量路徑，您 DMZ 中或在您的內部網路的框線。
    
- **Vm 的網際網路流量：** 若要防止 Azure Vm 初始化直接與網際網路位置的流量，通告預設路由傳送給 Microsoft。 透過 ExpressRoute 連線並透過您內部部署 proxy 伺服器，會路由傳送至網際網路的流量。 從 Azure Vm Azure PaaS 服務或 Office 365 的流量路由傳送回透過 ExpressRoute 連線。
    
- **WAN 最佳化程式：** 您可以部署在私人的對等連線的兩邊的 WAN 最佳化程式的跨單位 Azure 虛擬網路 (VNet)。 內部 Azure VNet 中，使用來自 Azure marketplace 和使用者定義路由 WAN 的最佳化網路應用裝置透過裝置所傳入的流量路由傳送。
    
- **的服務品質：** 使用您的流量 IPv4 標頭中的區別服務代碼點 (DSCP) 值，來標示語音、 互動式視訊/，或最佳傳遞。 這是 Microsoft 對等關係與 Skype for Business Online 流量特別重要。
    
請參閱這些額外的資源，如需詳細資訊：
  
- [ExpressRoute for Office 365](https://aka.ms/expressrouteoffice365)
    
- [Azure ExpressRoute for Office 365 訓練](https://channel9.msdn.com/series/aer/)
    
- [Azure ExpressRoute](https://azure.microsoft.com/services/expressroute/)
    
## <a name="next-step"></a>下一步

[設計 Microsoft SaaS 的網路](designing-networking-for-microsoft-saas.md)

## <a name="see-also"></a>請參閱

[Microsoft Cloud Networking for Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)

