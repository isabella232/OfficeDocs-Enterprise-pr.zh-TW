---
title: 實作 ExpressRoute for Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/5/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 77735c9d-8b80-4d2f-890e-a8598547dea6
description: Office 365 ExpressRoute 替代路由路徑為提供許多網際網路對向 Office 365 服務。Office 365 ExpressRoute 的架構根據公告公用 IP 前置詞之已可存取網際網路的後續可轉散發至那些 IP 前置字元的您已佈建 ExpressRoute 電路到的 Office 365 服務您的網路。使用 ExpressRoute 有效地啟用數個不同路由路徑，透過網際網路與透過 ExpressRoute，許多 Office 365 服務。此狀態的路由網路上可能代表重大變更您的內部網路拓撲設計的方式。
ms.openlocfilehash: e535135557f7f2f64077c1d926f120fff78dbd42
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "25715869"
---
# <a name="implementing-expressroute-for-office-365"></a>實作 ExpressRoute for Office 365

Office 365 ExpressRoute 替代路由路徑為提供許多網際網路對向 Office 365 服務。Office 365 ExpressRoute 的架構根據公告公用 IP 前置詞之已可存取網際網路的後續可轉散發至那些 IP 前置字元的您已佈建 ExpressRoute 電路到的 Office 365 服務您的網路。使用 ExpressRoute 有效地啟用數個不同路由路徑，透過網際網路與透過 ExpressRoute，許多 Office 365 服務。此狀態的路由網路上可能代表重大變更您的內部網路拓撲設計的方式。
  
 **狀態：** 完整的指南 v2
  
您必須小心規劃 Office 365 實作您 ExpressRoute 配合如有使用路由插入至核心網路與網際網路路由透過這兩個專用的電路網路複雜性。如果您及您的小組不執行詳細的規劃和測試此指南 》 中，將體驗高風險較間歇性或連線至 Office 365 的總遺失服務啟用 ExpressRoute 電路時指派。
  
若要讓成功實作，您必須分析您的基礎結構需求、 透過詳細的網路評估及設計、 謹慎規劃導入階段性與控制的方式，及建立詳細的驗證和測試計劃。大型、 分散式環境不尋常查看跨越數個月的實作。本指南的設計可協助您規劃繼續進行。
  
大型成功部署可能規劃採取六個月及通常包含組織包括網路、 防火牆及 Proxy 伺服器管理員、 Office 365 系統管理員、 安全性、 使用者支援、 專案中的 [從多個區域的小組成員管理及執行贊助權。您在規劃程序的投資會降低將遭遇停機時間或複雜且最耗費成本疑難排解所產生之部署失敗的可能性。
  
我們預期啟動此實作指南之前必須完成下列先決條件。
  
1. 您已完成決定 ExpressRoute 如果是建議與核准的網路評估。

2. 您已選取 ExpressRoute 網路服務提供者。尋找關於[ExpressRoute 合作夥伴和對等位置](https://azure.microsoft.com/documentation/articles/expressroute-locations/)的詳細資訊。

3. 您已閱讀並瞭解[ExpressRoute 文件](https://azure.microsoft.com/documentation/services/expressroute/)與內部網路能夠符合 ExpressRoute 必要條件端對端。

4. 小組擁有 「 讀取的所有公用指引和文件[https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)、 [https://aka.ms/ert](https://aka.ms/ert)，並保存的[Office 365 訓練的 Azure ExpressRoute](https://channel9.msdn.com/series/aer)數列 Channel 9 來了解重要技術詳細資料包括：

      - Saas 和服務的網際網路相依性。

      - 如何避免非對稱的路由和處理複雜的路由。

      - 若要併入周邊安全性、 可用性及應用程式層級控制項的方式。

## <a name="begin-by-gathering-requirements"></a>首先請收集需求
<a name="requirements"> </a>

啟動決定哪些功能與您要採用在組織內的服務。您需要決定將使用的不同 Office 365 服務的功能和您網路上的位置會裝載使用這些功能的人員。您要新增網路屬性的使用情況的型錄，每個這些案例需要;例如輸入及輸出的網路流量流向與 Office 365 端點是否可透過 ExpressRoute 或不。
  
若要收集組織的需求：
  
- 目錄貴組織要使用的 Office 365 服務的輸入和輸出網路流量。請洽詢 Office 365 Url 和 IP 位址範圍] 頁面上的不同 Office 365 案例需要的流程描述。

- 收集現有的網路拓撲顯示內部 WAN 骨幹和拓撲的詳細資料、 衛星網站，最後一個哩使用者連線，路由傳送至網路外圍輸出點與 proxy 服務連線的文件。

  - 找出在 Office 365 與其他 Microsoft 服務會連線至，顯示網際網路和建議的 ExpressRoute 連線路徑的網路圖表上的輸入的服務端點。

  - 找出所有地理使用者位置和位置的位置目前具有網際網路的輸出和建議讓輸出至 ExpressRoute 對等位置的哪個位置之間的 WAN 連線。

  - 找出所有 edge 裝置，例如 proxy、 防火牆，以此類推以及目錄流程不必透過網際網路和 ExpressRoute 及其關聯性。

  - 文件是否一般使用者可存取之網際網路和 ExpressRoute 流程透過直接路由或間接的應用程式 proxy 的 Office 365 服務。

- 新增您的租用戶的位置，且符合-我網狀圖的位置。

- 評估預期及觀察到的網路效能與延遲特性從主要使用者位置到 Office 365。請記住 Office 365 是一組通用且分散式的服務和使用者會連線至可能其租用戶的位置不同的位置。此原因，建議測量及透過 ExpressRoute 和網際網路連線最佳化的使用者與最接近的 Microsoft 通用網路邊緣之間的延遲。從網路評估您發現項目可用於幫助完成這項作業。

- 列出公司網路安全性及必須符合新 ExpressRoute 連線的高可用性需求。例如，如何使用者繼續取得 Office 365 存取網際網路的輸出或 ExpressRoute 電路失敗的情況下。

- 文件的輸入和輸出的 Office 365 網路流程會使用網際網路的路徑和這將會使用 ExpressRoute。說明如何在使用者的地理位置和您的內部網路拓撲的詳細資料可能需要為一位使用者位置以另一個不同的計劃。

### <a name="catalog-your-outbound-and-inbound-network-traffic"></a>型錄輸出及輸入網路流量
<a name="trafficCatalog"> </a>

降至最低的路由和其他網路複雜性，我們建議您使用僅 ExpressRoute for Office 365 之所需透過專用連線因法規需求或因網路評估移網路流量流程。此外，我們建議您以不同和不同的階段實作專案的階段 ExpressRoute 路由及方法輸出及輸入網路流量流程的範圍。部署 Office 365 ExpressRoute 剛剛使用者起始輸出網路流量流向和離開撥入的網路流量順利通過網際網路可協助控制增加的拓樸的複雜度及其他的 [的簡介 （英文） 風險的非對稱路由的可能性。
  
您的網路流量目錄應該包含您必須在內部網路與 Microsoft 之間的所有輸入及輸出的網路連線的清單。
  
- 輸出網路流量流向是其中連線從內部部署環境，例如從起始內部用戶端或伺服器與 Microsoft 服務的目的地任何案例。這些連線可能至 Office 365 直接或間接，例如時連線會通過 proxy 伺服器、 防火牆或其他網路裝置路徑至 Office 365。

- 輸入的網路流量流向是連接位置從 Microsoft cloud 起始至內部部署主機任何案例。這些連線通常需要透過防火牆和客戶安全性原則需要的外部起始之流程其他安全性基礎結構。

閱讀本文以決定哪些服務會傳送的輸入的流量，並尋找[Office 365 中標示為**Office 365 ExpressRoute**欄[與 Office 365 ExpressRoute 路由](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408)**確保路由對稱性來看**節端點](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)參考文章來決定其餘的連線資訊。
  
每個服務所需的輸出連線，建議您說明包括網路路由、 proxy 設定、 封包檢查服務的計劃的連線和頻寬需求。
  
每個服務所需的輸入的連線，您將需要一些額外的資訊。Microsoft 雲端中的伺服器將會建立您的內部網路的連線。若要確保正確地進行連線，您將想要說明此連線，包括; 的所有層面公用 DNS 項目會接受這些輸入的連線的服務、 CIDR 格式化 IPv4 IP 位址的 ISP 設備的相關資訊及如何輸入的 NAT 或來源 NAT 處理這些連線。
  
輸入的連線應該檢閱不論它們是否連線透過網際網路或以確保非對稱式路由 ExpressRoute 尚未引進。在某些情況下，在內部部署需要的其他 Microsoft 和非 Microsoft 服務可存取 Office 365 服務也啟動 5 到的傳入的連線的端點。很重要的啟用 ExpressRoute 路由傳送至 Office 365 進行這些服務不會自動換行其他案例。在許多情況下，客戶可能需要實作特定變更其內部網路，例如來源架構以確定從 Microsoft 輸入的排列在啟用 ExpressRoute 之後仍然會對稱的 NAT。
  
以下是範例詳細資料所需的層級。在此例中 Exchange 混合式會路由傳送至內部部署系統透過 ExpressRoute。

|**連線屬性**|**值**|
|:-----|:-----|
|**網路流量方向** <br/> |輸入  <br/> |
|**服務** <br/> |Exchange 混合式  <br/> |
|**公用 Office 365 端點 （來源）** <br/> |Exchange Online （IP 位址）  <br/> |
|**公用內部部署端點 （目的地）** <br/> |5.5.5.5  <br/> |
|**公用 （網際網路） DNS 項目** <br/> |Autodiscover.contoso.com  <br/> |
|**這個內部部署端點要使用的其他 (非 Office 365) Microsoft 服務** <br/> |否  <br/> |
|**這個內部部署端點會使用在網際網路上的使用者/系統** <br/> |是  <br/> |
|**透過公開端點發佈的內部系統** <br/> |Exchange Server 用戶端存取角色 （內部） 192.168.101、 192.168.102、 192.168.103  <br/> |
|**IP 通告的公用端點** <br/> |**網際網路**： 5.5.0.0/16  <br/> **以 ExpressRoute**: 5.5.5.0/24  <br/> |
|**安全性/周邊控制項** <br/> |**網際網路路徑**： DeviceID_002  <br/> **ExpressRoute 路徑**： DeviceID_003  <br/> |
|**高可用性** <br/> |主動/主動跨地理冗餘 2  <br/> ExpressRoute 電路-芝加哥與 Dallas  <br/> |
|**路徑對稱性來看控制項** <br/> |**方法**： 來源 NAT  <br/> **網際網路路徑**： 來源 NAT 輸入 192.168.5.5 的連線  <br/> |**ExpressRoute 路徑**： 來源 NAT 連線 192.168.1.0 (Chicago) 和 192.168.2.0 (Dallas)  <br/> |

以下是範例只有在輸出的服務：

|**連線屬性**|**值**|
|:-----|:-----|
|**網路流量方向** <br/> |輸出  <br/> |
|**服務** <br/> |SharePoint Online  <br/> |
|**內部部署端點 （來源）** <br/> |使用者工作站  <br/> |
|**公用 Office 365 端點 （目的地）** <br/> |SharePoint Online （IP 位址）  <br/> |
|**公用 （網際網路） DNS 項目** <br/> |\*。 sharepoint.com （和其他的 Fqdn）  <br/> |
|**CDN 轉介** <br/> |cdn.sharepointonline.com （和其他的 Fqdn）-CDN 提供者所維護的 IP 位址)  <br/> |
|**IP 通告和使用中的 NAT** <br/> |**網際網路路徑/來源 NAT**: 1.1.1.0/24  <br/> **ExpressRoute 路徑/來源 NAT**: 1.1.2.0/24 (Chicago) 和 1.1.3.0/24 (Dallas)  <br/> |
|**連線方法** <br/> |**網際網路**： 透過第 7 層 proxy （.pac 檔案）  <br/> **ExpressRoute**： 直接路由 (沒有 proxy)  <br/> |
|**安全性/周邊控制項** <br/> |**網際網路路徑**： DeviceID_002  <br/> **ExpressRoute 路徑**： DeviceID_003  <br/> |
|**高可用性** <br/> |**網際網路路徑**： 備援網際網路的輸出  <br/> **ExpressRoute 路徑**： 主動/主動 '作用馬鈴薯' 路由跨 2 地理位置設為備援的 ExpressRoute 電路-芝加哥與 Dallas  <br/> |
|**路徑對稱性來看控制項** <br/> |**方法**： 來源的所有連線的 NAT  <br/> |

### <a name="your-network-topology-design-with-regional-connectivity"></a>網路拓撲設計區域的連線
<a name="topology"> </a>

一旦您了解其相關聯的網路流量流向且服務，您可以建立同時這些新的連線需求並說明您在變更將會使用 ExpressRoute for Office 365 的網狀圖。將圖表應該包括：
  
1. 其中 Office 365 及其他服務會從存取的所有使用者位置。

2. 所有網際網路和 ExpressRoute 輸出點。

3. 所有輸出及輸入裝置的管理連線和網路，包括路由器和防火牆、 應用程式 proxy 伺服器入侵偵測/防護登出。

4. 所有的輸入流量，例如接受來自 ADFS 連線的內部 ADFS 伺服器內部目的地 web 應用程式 proxy 伺服器。

5. 將通告的所有 IP 子網路的型錄

6. 識別人員會存取來自 Office 365 及列出開會每個位置-我將用於 ExpressRoute 的位置。

7. 位置中某些部分的內部網路拓撲，其中會接受來自 ExpressRoute 學到的 Microsoft IP 前置詞、 篩選和傳播到。

8. 網路拓撲應說明每個網路區段的地理位置及如何連線到 Microsoft network 透過 ExpressRoute 和/或網際網路。

下圖顯示每個位置其中人員將會使用從 Office 365 與 Office 365 的輸入和輸出路由通告。
  
![ExpressRoute 區域地理開會-我](media/d866b36b-49bf-416b-af1b-d054e24989d2.png)
  
輸出流量的人員來存取 Office 365 中三種方法之一：
  
1. 透過 meet-我北美加利福尼亞中人員的位置。

2. 透過 meet-我在香港特別行政區人員香港特別行政區] 中的位置。

3. 透過孟加拉其中有較少的人員，而沒有 ExpressRoute 電路佈建在網際網路。

![輸出連線的區域圖](media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
同樣地，來自 Office 365 的輸入的網路流量會傳回三種方式之一：
  
1. 透過 meet-我北美加利福尼亞中人員的位置。

2. 透過 meet-我在香港特別行政區人員香港特別行政區] 中的位置。

3. 透過孟加拉其中有較少的人員，而沒有 ExpressRoute 電路佈建在網際網路。

![輸入的連線的區域圖](media/d6d6160d-bf28-4de3-a787-186c7432b306.png)
  
### <a name="determine-the-appropriate-meet-me-location"></a>決定適當的開會-我位置

將選取範圍開會-我位置，亦即其中 ExpressRoute 電路連線到 Microsoft 網路的網路的實體位置、 會影響人員存取 Office 365 中的位置的位置。提供 saas 和，為 Office 365 不會運作下 IaaS 或 PaaS 區域模型 Azure 沒有相同的方式。而是 Office 365 是一分散式共同作業服務的使用者可能需要跨多個資料中心和區域，可能不一定會在相同的位置或主控使用者的租用戶的地區連線到端點。
  
這表示您必須制定選取 meet 時最重要的考量-我的 Office 365 ExpressRoute 位置是要從連線在組織中的人員。一般建議的最佳的 Office 365 連線會實作路由，以便至 Office 365 服務的使用者要求所交由關閉 Microsoft network 到最短的網路路徑，這通常也會被稱為 '作用馬鈴薯' 路由。例如，如果大部分的 Office 365 使用者是在一或兩個位置中，選取 meet-我最接近接近這些使用者的位置中的位置會建立最佳的設計。如果您的公司具有許多不同地區龐大的使用者人數，可能會想要考慮擁有多個 ExpressRoute 電路且符合-我位置。某些使用者位置到 Microsoft network 和 Office 365 的最短/最最佳路徑可能不是透過內部 WAN 和 ExpressRoute 開會-我點，但透過網際網路。
  
通常時間有多個 meet-我無法選取相對接近您的使用者與區域內的位置。填寫以引導您決定下表。

|**計劃的 ExpressRoute 開會-我的 California 和紐約位置**||
|:-----|:-----|
|位置  <br/> |數字的人員  <br/> |透過網際網路輸出預期 Microsoft 網路延遲  <br/> |預期的 ExpressRoute 透過 Microsoft 網路延遲  <br/> |
|洛杉磯  <br/> |10,000  <br/> |~ 15ms  <br/> |~ 10 毫秒 （透過矽谷）  <br/> |
|華盛頓 DC  <br/> |15000  <br/> |~ 20ms  <br/> |~ 10 毫秒 （透過紐約）  <br/> |
|Dallas  <br/> |5,000  <br/> |~ 15ms  <br/> |~ 40ms （透過紐約）  <br/> |

之後顯示 Office 365 區域通用網路架構、 ExpressRoute 網路服務提供者是否符合-我開發位置及位置個人數量、 可用來識別是否可以進行任何最佳化。它可能也會顯示通用髮夾網路連線其中流量路由傳送至距位置以取得開會-我的位置。如果通用網路上的髮夾會發現它應該在於才能繼續執行。尋找其他開會-我的位置或使用選擇性網際網路上下文輸出點，以免發生髮夾。
  
第一張圖表中，會顯示 「 北美地區 」 中的兩個實體位置與客戶的範例。您可以看到辦公室位置、 Office 365 租用戶位置、 資訊及數個 ExpressRoute 選擇符合-我位置。客戶已在此範例中，選取 [開會-我順序中的兩個原則為基礎的位置：
  
1. 最接近接近其組織中的人員。

2. 最接近接近 Microsoft 資料中心主控 Office 365 的。

![ExpressRoute 美國地理開會-我](media/5ec38274-b317-4ec1-91c8-90c2a7fd32ca.png)
  
稍微展開此概念進一步範例多重國民客戶面臨類似的資訊和決策制定的第二個圖顯示。此客戶可以中孟加拉小型小組的十著重於得其之上的區域中的人員與小型的辦公室。沒有開會-我清奈及 Microsoft 資料中心與 Office 365 中的位置裝載於辰內所以開會-我位置就意義;不過，十人員其他電路費用遠遠繁瑣。當您在查看您的網路，您需要決定是否比花以取得其他 ExpressRoute 電路資本高效率參與您的網路之間傳送網路流量的延遲。
  
或者，在孟加拉十人員可能會遇到較佳的效能與比他們會路由傳送內部網路上為我們在簡介圖表中顯示及重現，透過網際網路傳送至 Microsoft network 其網路流量下面。
  
![輸出連線的區域圖](media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
## <a name="create-your-expressroute-for-office-365-implementation-plan"></a>建立您的 Office 365 實作計畫 ExpressRoute
<a name="implementation"> </a>

實作計劃應該包含這兩種技術詳細資料的設定 ExpressRoute 當您在網路上，如下所示設定所有其他基礎結構的詳細資料。
  
- 規劃 ExpressRoute 與網際網路之間分割的服務。

- 規劃頻寬、 安全性、 高可用性和容錯移轉。

- 設計輸入和輸出路由，包括適當的不同位置的路由路徑最佳化

- 決定 ExpressRoute 路由至您的網路的通告最及新功能的用戶端選取網際網路或 ExpressRoute 路徑 ； 機制例如，直接路由或應用程式 proxy。

- 規劃 DNS 記錄變更，包括[寄件者原則架構](https://technet.microsoft.com/library/dn789058%28v=exchg.150%29.aspx)項目。

- 規劃 NAT 策略包括輸出及輸入來源 nat。

### <a name="plan-your-routing-with-both-internet-and-expressroute-network-paths"></a>規劃您的路由與網際網路和 ExpressRoute 網路路徑
<a name="paths"> </a>

- 在初始部署的所有內送的服務，例如內送電子郵件或混合式連線、 建議使用網際網路。

- 規劃使用者用戶端 LAN 路由，例如[設定 PAC/WPAD 檔案](https://aka.ms/manageo365endpoints)、 預設路由、 proxy 伺服器與 BGP 路由廣告。

- 規劃外圍路由傳送，包括 proxy 伺服器、 防火牆和雲端 proxy。

### <a name="plan-your-bandwidth-security-high-availability-and-failover"></a>規劃頻寬、 安全性、 高可用性和容錯移轉
<a name="availability"> </a>

建立所需的每一個主要的 Office 365 工作負載的頻寬的計畫。分開評估 Exchange Online、 SharePoint Online 和 Skype 商務線上的頻寬需求。您可以使用我們提供的 Exchange Online 和 Skype 的業務上進行起始; 估計計算器不過，使用者設定檔及位置的代表性 sample 試驗測試，則需要完全了解您組織的頻寬需求。
  
新增安全性在每個網際網路和您的計劃 ExpressRoute 輸出位置的處理方式，請記住所有 ExpressRoute 連線至 Office 365 使用公用對等和仍必須符合您公司的安全性原則連接至外部的安全網路。
  
加入您解有哪些人員將會受到何種類型的中斷及如何這些人員將能夠以最簡單的方式執行容量滿載其工作的計劃的詳細資訊。
  
#### <a name="plan-bandwidth-requirements-including-skype-for-business-requirements-on-jitter-latency-congestion-and-headroom"></a>規劃頻寬需求包括 Skype 抖動、 延遲、 擁塞、 及發揮空間上的商務需求
  
商務 online Skype 也有特定額外的網路需求[的媒體品質和 Skype 的商務 Online 中的網路連線效能](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)的文章中詳述。
  
請閱讀**頻寬規劃 Azure ExpressRoute** [網路規劃與 Office 365 ExpressRoute](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd)一節。
  
當執行與您的試驗使用者的頻寬評估，您可以使用我們指南;[Office 365 效能調整使用基準和效能歷程記錄](https://support.office.com/article/Office-365-performance-tuning-using-baselines-and-performance-history-1492cb94-bd62-43e6-b8d0-2a61ed88ebae)。
  
#### <a name="plan-for-high-availability-requirements"></a>規劃高可用性需求
  
建立計畫，以符合您的需求及併入此更新的網路拓撲圖表的高可用性。請閱讀**高可用性和容錯移轉與 Azure ExpressRoute** [網路](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd)規劃與 Office 365 ExpressRoute 一節。
  
#### <a name="plan-for-network-security-requirements"></a>如需網路安全性需求的計劃
  
建立計畫，以符合您的網路安全性需求及併入此更新的網路拓撲圖表。請閱讀] 區段中的[網路規劃與 Office 365 ExpressRoute](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd)**正在套用至 Office 365 案例的 Azure ExpressRoute 的安全性控制**。
  
### <a name="design-outbound-service-connectivity"></a>設計外寄的服務連線
<a name="outbound"> </a>

Office 365 ExpressRoute 有可能不熟悉的*輸出*網路需求。主要是針對 IP 位址，代表至 Office 365 的使用者和網路遊歷輸出的網路連線至 Microsoft 來源端點必須依照下列所述的特定需求。
  
1. 端點必須是公用 IP 位址，為您的公司或電訊廠商提供 ExpressRoute 連線至您要登錄。

2. 端點必須向 Microsoft 公告所並驗證/接受供 ExpressRoute。

3. 端點必須不是到同一個或多慣用路由評量與網際網路進行通告。

4. 端點必須不用於未設定透過 ExpressRoute 的 Microsoft 服務的連線。

如果您的網路設計不符合這些需求，有高風險您的使用者會體驗到 Office 365 及其他 Microsoft 服務因為路由黑色 holing 或非對稱式路由的連線失敗。這發生於 ExpressRoute，透過路由傳送至 Microsoft 服務要求但回應會路由傳送回經由網際網路，反之亦然，例如防火牆設定狀態的網路裝置會捨棄回應。
  
您可以使用符合上述需求的常見方法是網路的使用來源 NAT 實作為您的部分或 ExpressRoute 電信業者所提供。來源 NAT 可讓您抽象的詳細資訊與私人 IP 位址處理的網際網路網路 ExpressRoute 從和;搭配適當的 IP 路由廣告，提供簡單的機制來確保路徑對稱性來看。如果您使用專屬 ExpressRoute 對等位置的可設定狀態的網路裝置，您必須實作分開 NAT 集區中的每個 ExpressRoute 以確保路徑對稱性來看對等。
  
閱讀的有關[ExpressRoute NAT 需求](https://azure.microsoft.com/documentation/articles/expressroute-nat/)的詳細資訊。
  
網路拓撲圖表來新增輸出連線的變更。
  
### <a name="design-inbound-service-connectivity"></a>設計輸入的服務連線
<a name="inbound"> </a>

企業版 Office 365 部署的多數 」 假設來自 Office 365 的輸入連線至內部部署服務的一些表單例如 Exchange、 SharePoint、 和 Skype 商務混合式案例、 信箱移轉和使用 ADFS 的驗證基礎結構。當 ExpressRoute 讓您在內部網路與 Microsoft 之間進行輸出連線其他路由路徑，這些輸入的連線可能不經意受到非對稱式路由]，即使您想要有這些流程繼續使用網際網路。若要確保有到網際網路的任何影響基礎輸入的流程來自 Office 365 與內部部署系統建議如下所述的一些預防措施。
  
降至最低的非對稱式路由撥入的網路流量流向風險，輸入連線的所有應使用來源 NAT 他們正在路由傳送到有路由可見性 ExpressRoute 您的網路區段之前。如果路由可見性 ExpressRoute 沒有來源 NAT 與到網路區段允許傳入的連線，要求來自 Office 365 將輸入從網際網路、 但回到 Office 365 的回應會偏好 ExpressRoute回到 Microsoft 網路，而造成非對稱式路由的網路路徑。
  
您可能會考慮下列實作模式來滿足此需求其中一項：
  
1. 要求路由傳送至內部網路使用網路設備如防火牆之前執行來源 NAT 或從網際網路負載平衡器上路徑至內部部署系統。

2. 請確定 ExpressRoute 路由不會傳播到輸入的服務，例如前方結束伺服器的位置或反向 proxy 系統處理的網際網路連線都位於網路區段數。

明確會計這些案例您網路中並保留所有內送的網路流量流向透過網際網路它可協助部署及操作的非對稱式路由的風險降到最低。
  
可能會有您可以選擇直接一些輸入的流程透過 ExpressRoute 連線的情況。這些案例中，採取下列其他考量事項。
  
1. Office 365 可以只目標內部部署端點使用公用 Ip 的。這表示，即使在內部輸入的端點只能透過 ExpressRoute 公開給 Office 365，它仍然需要具有與它相關聯的公用 IP。

2. Office 365 服務執行以解析內部部署端點的所有 DNS 名稱解析都發生使用公用 DNS。這表示您必須註冊在網際網路上的 IP 對應至輸入的服務端點的 FQDN。

3. 若要透過 ExpressRoute 接收傳入的網路連線，這些端點的公用 IP 子網路必須透過 ExpressRoute 通告給 Microsoft。

4. 謹慎評估以確保該適當的安全性這些輸入的網路流量流程和網路控制項符合您的公司安全性和網路原則套用至他們。

5. 一次內部輸入的端點向 Microsoft 通告透過 ExpressRoute、 ExpressRoute 將有效成為那些端點的所有 Microsoft 服務，包括 Office 365 的慣用路由路徑。這表示端點子網路必須只用於與 Office 365 服務和 Microsoft 網站上的任何其他服務通訊。否則，您的設計將會造成其中其他 microsoft 服務偏好來路由傳送的輸入的連線的輸入 ExpressRoute，透過時傳回路徑會使用網際網路的非對稱式路由。

6. 在事件 ExpressRoute 電路或符合-我位置已關閉，則需要確定內部輸入的端點可用仍可接受要求透過不同的網路路徑。這可能會透過多個 ExpressRoute 電路那些端點意見廣告子網路。

7. 建議您將套用之所有內送的網路流量流程輸入您的網路透過 ExpressRoute，尤其是當這些流程跨防火牆等設定狀態的網路裝置時的來源 NAT。

8. 某些內部部署服務，例如 ADFS proxy 或 Exchange 自動探索可能會收到輸入的要求來自 Office 365 服務和來自網際網路的使用者。這些要求的 Office 365 會透過網際網路目標使用者要求相同的 FQDN。從網際網路允許撥入的使用者連線至那些內部部署端點時強制進行 Office 365 的連線使用 ExpressRoute，代表大幅路由的複雜性。對於大多數的客戶透過 ExpressRoute 實作這類複雜的案例不建議因為操作考量。此額外負荷包含管理風險的非對稱式路由，而且需要您謹慎管理跨多個維度的 [路由廣告和原則。

### <a name="update-your-network-topology-plan-to-show-how-you-would-avoid-asymmetric-routes"></a>更新您的網路拓撲計劃来顯示如何將避免發生非對稱式路由
<a name="asymmetric"> </a>

您想要避免以確保您的組織中的人員可以順暢地使用 Office 365，以及其他重要服務在網際網路上的非對稱式路由。有兩種常見設定客戶可以引發非對稱式路由。現在是很好的時間檢閱您打算使用並檢查是否其中一個這些非對稱的路由案例依然存在的網路組態。
  
若要開始，我們將檢查幾個不同的情況下的網狀圖相關聯。在此圖表中，會收到傳入的要求的所有伺服器例如 ADFS 或內部部署混合伺服器紐澤西資料中心中與通知給網際網路。
  
1. 安全周邊網路時，沒有任何來源 NAT 可供傳入要求。

2. 紐澤西資料中心中的伺服器都能看到網際網路和 ExpressRoute 路由。

![ExpressRoute 連線概觀 （英文)](media/8f074af6-ef38-44e8-bc5a-8b4d981fbb20.png)
  
我們也具備如何修正這些建議。
  
#### <a name="problem-1-cloud-to-on-premises-connection-over-the-internet"></a>透過網際網路與內部連線的問題 1： 雲端
  
下圖說明當您的網路設定不會透過網際網路的傳入要求的 Microsoft cloud 中提供 NAT 時採取的非對稱的網路路徑。
  
1. 從 Office 365 的輸入的要求從公用 DNS 擷取內部部署端點的 IP 位址，並將要求傳送至周邊網路中。

2. 這個無效的組態設定中沒有設定任何來源 NAT 或位於周邊網路流量所在傳送產生實際來源 ip 位址作為傳回目的地。

  - 您的網路上的伺服器傳回將流量路由傳送至 Office 365 透過任何可用的 ExpressRoute 網路連線。

  - 結果是 Office 365，則產生的中斷連線的流程非對稱路徑。

![ExpressRoute Asymetric 路由問題 1](media/9c210c2a-e0ea-4180-8ede-1bf41746ce7a.png)
  
##### <a name="solution-1a-source-nat"></a>解決方案 1a： 來源 NAT
  
只新增來源 NAT 以將輸入要求解析為此設定錯誤的網路。在此圖表中：
  
1. 傳入的要求會繼續輸入透過紐澤西資料中心的周邊網路。這次是來源 NAT 使用。

2. 從伺服器路由回正面 nat 來源，而不是原始的 IP 位址，則傳回的相同的網路路徑的回應產生關聯的 IP 回應。

![ExpressRoute Asymetric 路由解決方案 1](media/0e87a155-f8de-48ed-92ac-27367b727a82.png)
  
##### <a name="solution-1b-route-scoping"></a>解決方案 1b： 路由設定範圍
  
或者，您可以選擇不允許將通告的前置詞 ExpressRoute BGP 移除這些電腦的替代的網路路徑。在此圖表中：
  
1. 傳入的要求會繼續輸入透過紐澤西資料中心的周邊網路。這次是透過 ExpressRoute 電路通告使用 microsoft 的前置詞不紐澤西資料中心。

2. 從伺服器路由回應回他們所產生的相同的網路路徑傳回回應 IP 透過唯一可用的路由相關聯的原始 IP 位址。

![ExpressRoute Asymetric 路由解決方案 2](media/9cb4b2bf-7aa6-487a-bc02-e02af8a979f6.png)
  
#### <a name="problem-2-cloud-to-on-premises-connection-over-expressroute"></a>問題 2： 雲端 ExpressRoute 透過內部部署連線
  
下圖說明當您的網路設定不會透過 ExpressRoute 的傳入要求的 Microsoft cloud 中提供 NAT 時採取的非對稱的網路路徑。
  
1. 從 Office 365 的輸入的要求擷取的 IP 位址從 DNS，並將要求傳送至周邊網路中。

2. 這個無效的組態設定中沒有設定任何來源 NAT 或位於周邊網路流量所在傳送產生實際來源 ip 位址作為傳回目的地。

  - 在您的網路上的電腦傳回將流量路由傳送至 Office 365 透過任何可用的 ExpressRoute 網路連線。

  - 結果是 Office 365 的非對稱式連線。

![ExpressRoute Asymetric 路由問題 2](media/f6fd155b-bbb7-472a-846e-039a99f09913.png)
  
##### <a name="solution-2-source-nat"></a>解決方案 2： 來源 NAT
  
只新增來源 NAT 以將輸入要求解析為此設定錯誤的網路。在此圖表中：
  
1. 傳入的要求會繼續輸入透過紐約資料中心的周邊網路。這次是來源 NAT 使用。

2. 從伺服器路由回正面 nat 來源，而不是原始的 IP 位址，則傳回的相同的網路路徑的回應產生關聯的 IP 回應。

![ExpressRoute Asymetric 路由解決方案 3](media/a5d2b90d-a3ec-4047-afbf-6e6e99f376a7.png)
  
### <a name="paper-verify-that-the-network-design-has-path-symmetry"></a>紙張確認網路設計具有路徑對稱性來看

此時，您必須確認紙張上實作計劃提供路由對稱性來看不同案例中您將會使用 Office 365。您將識別預期使用者使用服務的不同功能時要採取的特定網路路由。從內部網路和 WAN 路由至周邊裝置的 [連線路徑 ；ExpressRoute 或網際網路和登入到 online 端點的連線。
  
您需要這麼做的所有先前已被識別為貴組織要採取的服務 Office 365 網路服務。
  
很有幫助執行本白皮書逐一檢查的路由與第二個連絡人。說明這些其中每個網路躍點預期會取得其下一條路由從並確定您已熟悉的路由路徑。請記得 ExpressRoute 永遠會提供更多範圍的路由到 Microsoft 伺服器的 IP 位址給予較低的路由成本比網際網路預設路由。
  
### <a name="design-client-connectivity-configuration"></a>設計用戶端連線設定
<a name="asymmetric"> </a>

![使用 ExpressRoute PAC 檔案](media/7cfa6482-dbae-416a-ae6f-a45e5f4de23b.png)
  
如果您使用 proxy 伺服器的網際網路繫結流量則需要調整任何 PAC 或用戶端設定檔以確保您的網路上的用戶端電腦已正確設定以不 transiting 立即所需的 ExpressRoute 流量傳送至 Office 365proxy 伺服器，與其餘的流量，包括一些的 Office 365 流量傳送至相關的 proxy。閱讀有關[管理 Office 365 端點](https://aka.ms/manageo365endpoints)我們指南例如 PAC 檔案。
  
> [!NOTE]
> 端點變更經常、 通常為 [每週。您只應該進行變更為基礎的服務和功能組織已採用以減少需要對最新資訊已變更的數目。關閉必須注意的 RSS 摘要其中所做的變更會即已宣佈及記錄保留的所有舊 IP 的變更會即已宣佈的地址中的**有效的日期**可能未通告、 或移除通告，直到達到有效的日期。
  
## <a name="build-your-deployment-and-testing-procedures"></a>建置您的部署和測試程序
<a name="testing"> </a>

同時測試及復原規劃應該包括實作計劃。如果您實作未運作如預期般運作，規劃應設計成影響最數目人員之前發現的問題。以下是您計劃應該考慮一些 high 層級原則。
  
1. 階段減少中斷網路區段和使用者服務 onboarding。

2. 規劃測試使用 traceroute 路由和 TCP 連線從不同的網際網路連線的主機。

3. 最好測試的輸入和輸出服務應使用的測試 Office 365 租用戶隔離的測試網路上。

      - 或者，可以被執行測試生產網路上如果客戶尚無法使用 Office 365 或位於試驗。

      - 或者，測試預留測試在實際執行中斷期間執行及可監視僅。

      - 或者，測試可透過檢查每個第 3 層 router 節點上每個服務的路由。此改應該只用於如果沒有其他測試可能因為缺少實體測試介紹風險。

### <a name="build-your-deployment-procedures"></a>建置您的部署程序

部署程序應該導入的人員的小群組分階段可用於測試再部署至較大組群的人。以下是幾種方式階段 ExpressRoute 的部署。
  
1. 與 Microsoft 對等設定 ExpressRoute 並已轉寄給僅針對單一主機路由廣告分段測試目的。

2. Advertise 為單一網路區段第一次 ExpressRoute 網路路由並展開路由廣告網路區段或區域。

3. 如果第一次部署 Office 365，作為 ExpressRoute 網路部署試驗的小型人數。

4. 如果使用 proxy 伺服器，或者可設定將之前加入更多導向少量的測試及意見反應至 ExpressRoute 人員測試 PAC 檔案。

實作計劃應列出每個必須採取的部署程序或需要用來部署的網路組態的命令。當網路中斷時間會進入做應從書寫的部署計劃已事先撰寫和對等的變更的所有檢閱。請參閱 ExpressRoute 技術組態適用的指引。
  
- 如果您已變更的任何仍會繼續傳送電子郵件的內部部署伺服器的 IP 位址，更新 SPF TXT 記錄。

- 如果您已變更以容納新的 NAT 設定的 IP 位址，更新內部部署伺服器的任何 DNS 項目。

- 請確定您已訂閱 rss 摘要的 Office 365 端點通知來維護任何路由或 proxy 設定。

ExpressRoute 部署完成後測試計劃中的程序應該執行。應記錄每個程序的結果。您必須包含復原到原始的實際執行環境的測試計劃結果指出實作未成功可行的程的序。
  
### <a name="build-your-test-procedures"></a>建立測試程序

在測試程序應該包含 Office 365 將會使用 ExpressRoute 每個輸出及輸入網路服務和類不會測試。本節的程序應該包含測試從包含使用者不是在內部公司的 LAN 中每個唯一的網路位置。
  
測試活動的一些範例包括下列項目。
  
1. 從您的內部路由器 ping 到您的網路運算子路由器。

2. 驗證 500 + Office 365 和 CRM Online IP 位址廣告會接收到您的內部路由器。

3. 驗證您輸入及輸出的 NAT 操作 ExpressRoute 與內部網路之間。

4. 驗證您的 NAT 路由會被通告從您的路由器。

5. 驗證 ExpressRoute 已接受通告的前置詞。

      - 若要確認對等的廣告使用下列 cmdlet：

      ```PowerShell
      Get-AzureRmExpressRouteCircuitRouteTable -DevicePath Primary -ExpressRouteCircuitName TestER -ResourceGroupName RG -PeeringType MicrosoftPeering
      ```

6. 驗證其設定為特定先前範例所示的較大範圍的子集範圍不向 Microsoft 透過 ExpressRoute 或公用網際網路網路電路通告您公用 NAT IP。

7. ExpressRoute 電路成對、 驗證執行這兩個 BGP 工作階段。

8. 在您的 NAT 的內部單一主機及使用 ping、 tracert 及 tcpping 不同主機 outlook.office365.com 至新的電路測試連線。或者，您可以使用 Wireshark 之類的工具或 Microsoft Network Monitor 3.4 來驗證您 MSEE 鏡像連接埠上正在能夠連線到 outlook.office365.com 相關聯的 IP 位址。

9. Exchange Online 的測試應用程式層級的功能。

  - 測試 Outlook 能夠連線至 Exchange Online 並傳送/接收電子郵件。

  - 測試 Outlook 在能夠使用 「 線上模式。

  - 測試智慧型手機連線並傳送/接收] 功能。

10. SharePoint Online 的測試應用程式層級功能

  - 測試 OneDrive for Business sync 用戶端。

  - 測試 SharePoint Online web access。

11. 商務電話案例 Skype 測試應用程式層級的功能：

  - 已驗證的使用者 [由使用者起始的邀請] 以加入電話會議。

  - 邀請電話會議 [邀請寄件者 MCU] 的使用者。

  - 使用 Skype 商務 web 應用程式的匿名使用者加入會議。

  - 加入將有線的 PC 連線、 IP 電話與行動裝置的通話。

  - 呼叫以同盟的使用者 o PSTN 驗證呼叫： 完成通話、 通話品質來說相當可接受、 連線時間是在可接受。

  - 確認連絡人的目前狀態更新兩個成員的租用戶和同盟使用者。

### <a name="common-problems"></a>常見問題

非對稱式路由是最常見的實作問題。以下是一些常見的來源來尋找：
  
- 使用 open 或一般網路路由拓撲但未來源位置的 NAT。

- 不使用 SNAT 路由傳送至輸入 services 透過網際網路和 ExpressRoute 連線。

- 不測試輸入的 ExpressRoute 在伺服器上的服務之前先部署廣泛的測試網路。

## <a name="deploying-expressroute-connectivity-through-your-network"></a>部署 ExpressRoute 連線到您的網路
<a name="testing"> </a>

階段，一次漸漸地愈來愈啟用連線至網路回復為每個新的網路區段計劃的不同組件部署至多條線段的網路。如果您部署 Office 365 部署的對齊、 先部署至 Office 365 試驗使用者，並從該處擴充。
  
先測試然後實際執行：
  
- 執行啟用 ExpressRoute 的部署步驟。

- 測試您看不到網路路由已如預期般運作。

- 執行測試每個輸入及輸出的服務。

- 如果您發現任何問題，回復。

### <a name="set-up-a-test-connection-to-expressroute-with-a-test-network-segment"></a>設定與測試網路區段 ExpressRoute 測試連線

現在，您必須完成的計劃的紙張上該是時候來測試小型向外延展。此測試中您會在內部網路上建立的單一 ExpressRoute 連線與 Microsoft Peering 測試子網路。您可以連線到與測試子網路設定[試用 Office 365 租用戶](https://go.microsoft.com/fwlink/p/?LinkID=403802)和在生產環境中測試子網路中包含您要使用的所有輸出及輸入服務。設定 DNS 的測試網路區段並建立所有輸入及輸出的服務。執行測試計劃並確定您熟悉針對每個服務和路由傳播路由傳送。
  
### <a name="execute-the-deployment-and-test-plans"></a>執行部署和測試計劃

當您完成以上所述的項目，檢查關閉區域在完成並確定您和小組檢閱這些之前執行您的部署和測試計劃。
  
- 輸出及輸入變更網路相關的服務清單。

- 顯示 internet 輸出及 ExpressRoute 開會通用網路架構圖表-我位置。

- 網路路由圖示範部署每個服務使用不同的網路路徑。

- 若要實作的變更和 rollback 視部署計畫的步驟。

- 測試每個 Office 365 及網路服務測試計劃。

- 完成輸入和輸出服務的實際執行路由紙張驗證。

- 跨包括可用性測試測試網路區段完整的測試。

選擇 [中斷] 視窗的時間足以執行透過整個部署規劃和測試計劃、 有一些疑難排解可用的時間和啟用回如果所需的時間。
  
> [!CAUTION]
> 因為路由透過網際網路和 ExpressRoute 複雜本質，建議其他緩衝區時間會新增此視窗以處理複雜路由的疑難排解。
  
### <a name="configure-qos-for-skype-for-business-online"></a>設定 QoS Skype for Business 線上

QoS 是必要的商務 Online Skype 取得語音與會議的優點。您可以設定 QoS 之後您擁有可確保 ExpressRoute 網路連線不會封鎖任何您其他 Office 365 服務存取權。[ExpressRoute 和 Skype 的商務 Online 中的 QoS](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d)文章中說明的 QoS 設定。
  
## <a name="troubleshooting-your-implementation"></a>疑難排解您實作
<a name="troubleshooting"> </a>

第一個位置尋找位於此實作指南 》 中的步驟已任何未接的實作計劃中吗？返回並執行進一步測試盡可能複寫錯誤和偵錯該那里的小型網路。
  
識別此輸入或輸出 services 無法在測試期間。取得特別的 IP 位址和子網路的每個服務的失敗。繼續進行的紙張上引導網路拓撲圖表與驗證路由。驗證特別其中 ExpressRoute 路由會對通告、 測試該路由系統中斷期間盡可能與追蹤項目。
  
使用網路追蹤執行 PSPing 至每個客戶端點並評估來源和目的地 IP 位址來驗證其如預期般運作。執行連接埠 25 上公開並確認是否這預期 SNAT 隱藏的原始來源 IP 位址的任何郵件主機 telnet。
  
請記住，則需要確定這兩個網路組態的 ExpressRoute ExpressRoute 連線以部署 Office 365 時的最佳方式設計及也已進行其他元件最佳化網路等用戶端電腦上。除了使用本規劃指南來疑難排解您可能會有未接的步驟，我們也有寫入[效能疑難排解 Office 365 計劃](https://support.office.com/article/Performance-troubleshooting-plan-for-Office-365-e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c)。
  
您可以使用下列短連結返回這裡：[https://aka.ms/implementexpressroute365](https://aka.ms/implementexpressroute365)
  
## <a name="related-topics"></a>相關主題

[對 Office 365 的網路連線](network-connectivity.md)
  
[Azure ExpressRoute for Office 365](azure-expressroute.md)
  
[管理 ExpressRoute for Office 365 連線](managing-expressroute-for-connectivity.md)
  
[使用 ExpressRoute for Office 365 進行路由傳送](routing-with-expressroute.md)
  
[使用 ExpressRoute for Office 365 進行網路規劃](network-planning-with-expressroute.md)
  
[在 ExpressRoute for Office 365 案例中使用 BGP 社群 (預覽)](bgp-communities-in-expressroute.md)
  
[商務用 Skype Online 中的媒體品質和網路連線效能](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917) (英文)
  
[針對商務用 Skype Online 最佳化您的網路](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43) (英文)
  
[商務用 Skype Online 中的 ExpressRoute 與 QoS](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d) (英文)
  
[使用 ExpressRoute 的通話流程](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab) (英文)
  
[使用基準與效能歷程記錄進行 Office 365 效能調整](performance-tuning-using-baselines-and-history.md)
  
[Office 365 的效能疑難排解規劃](performance-troubleshooting-plan.md)
  
[Office 365 URL 與 IP 位址範圍](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 網路與效能調整](network-planning-and-performance.md)
