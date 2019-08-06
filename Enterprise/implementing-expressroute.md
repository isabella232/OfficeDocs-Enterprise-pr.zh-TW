---
title: 實作 ExpressRoute for Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/5/2017
audience: ITPro
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
description: 適用於 Office 365 提供替代的路由路徑許多網際網路對向 Office 365 服務。 ExpressRoute for Office 365 的架構根據公告已可存取網際網路上插入到這些 IP 前置詞的後續重新發佈您佈建 ExpressRoute 電路的 Office 365 服務的公用 IP 電話首碼您的網路。 使用 ExpressRoute 有效率地啟用數個不同路由路徑，透過網際網路，以及透過 ExpressRoute，許多 Office 365 服務。 在您的網路路由此狀態可能代表了重大改變您的內部網路拓撲設計的方式。
ms.openlocfilehash: 3e3171c3058b485ef644af3f1d33a9f80c71345c
ms.sourcegitcommit: 0449c6f854c682719cac1bd0d086f2e3b20078b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "34722722"
---
# <a name="implementing-expressroute-for-office-365"></a>實作 ExpressRoute for Office 365

適用於 Office 365 提供替代的路由路徑許多網際網路對向 Office 365 服務。 ExpressRoute for Office 365 的架構根據公告已可存取網際網路上插入到這些 IP 前置詞的後續重新發佈您佈建 ExpressRoute 電路的 Office 365 服務的公用 IP 電話首碼您的網路。 使用 ExpressRoute 有效率地啟用數個不同路由路徑，透過網際網路，以及透過 ExpressRoute，許多 Office 365 服務。 在您的網路路由此狀態可能代表了重大改變您的內部網路拓撲設計的方式。
  
 **狀態：** 完整指南 v2
  
您必須謹慎規劃您 ExpressRoute for Office 365 實作以容納的需要使用路由插入核心網路和網際網路路由可透過這兩個專用的電路網路複雜性的。 如果您和您的小組成員不執行詳細的規劃並測試本指南中，有高風險，您將遇到間歇性或總遺失連線至 Office 365 服務時啟用 ExpressRoute 線路。
  
若要讓成功實作，您必須分析您的基礎結構需求、 通過詳細的網路評估和設計、 仔細規劃導入分段且受控制的方式，及建立詳細的驗證和測試計劃。 在大型、 分散的環境不常見看見 span 幾個月的實作。 本指南旨在協助您規劃。
  
大型成功部署可能需要規劃的六個月及通常包括網路、 防火牆和 Proxy 伺服器系統管理員、 Office 365 系統管理員、 安全性、 使用者支援、 專案在組織中包含的許多層面的小組成員管理和主管贊助。 您在規劃程序的投資會降低您將遇到停機時間或複雜且最耗費成本疑難排解中所產生的部署失敗的可能性。
  
我們預期會啟動此實作指南之前完成下列先決條件。
  
1. 您已完成網路評估，以判斷 ExpressRoute 是否是建議，並核准。

2. 您已選取的 ExpressRoute 網路服務提供者。 尋找關於[ExpressRoute 合作夥伴和對等位置](https://azure.microsoft.com/documentation/articles/expressroute-locations/)的詳細資訊。

3. 您已閱讀並瞭解[ExpressRoute 文件](https://azure.microsoft.com/documentation/services/expressroute/)和您的內部網路是能夠符合 ExpressRoute 先決條件端對端。

4. 您的小組具備讀取的所有公用的指導方針和文件[https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)、 [https://aka.ms/ert](https://aka.ms/ert)，和保存的[Azure ExpressRoute for Office 365 訓練](https://channel9.msdn.com/series/aer)數列上 Channel 9，要如何因應了解的重要技術的詳細資訊，包括：

      - SaaS 服務網際網路相依性。

      - 如何避免非對稱式路由及處理複雜路由。

      - 如何納入周邊安全性、 可用性及應用程式層級的控制項。

## <a name="begin-by-gathering-requirements"></a>首先請收集需求
<a name="requirements"> </a>

首先，決定哪些功能和您打算採用您組織內的服務。 您必須決定將使用不同的 Office 365 服務的功能和您網路上的位置將裝載人員使用這些功能。 您需要將網路屬性 (attribute) 與目錄的案例中，每個這些案例需要;等輸入和輸出的網路流量流向 Office 365 端點是否可透過 ExpressRoute 與否。
  
收集貴組織的需求：
  
- 型錄，您的組織使用 Office 365 服務的輸入和輸出網路流量。 如需不同 Office 365 案例需要的流量的說明，請參閱 Office 365 Url 和 IP 位址範圍] 頁面。

- 收集現有顯示您的內部 WAN 骨幹和拓撲的詳細資料、 衛星站台，最後一個哩的使用者連線能力，路由傳送至網路周邊出口點和 proxy 服務連線的網路拓撲的文件。

  - 找出在 Office 365 和其他 Microsoft 服務會連線到，顯示網際網路和建議的 ExpressRoute 連線路徑的網路圖表上的輸入的服務端點。

  - 找出所有地理使用者位置，以及哪些位置目前沒有通往網際網路和建議讓輸出至 ExpressRoute 對等位置的哪個位置的位置之間的 WAN 連線。

  - 找出所有的邊緣裝置，例如 proxy、 防火牆、 等等並型錄，其關係給分批 ExpressRoute 與網際網路的流量。

  - 文件是否使用者會存取 Office 365 服務透過直接路由或間接的應用程式 proxy 的網際網路和 ExpressRoute 流程。

- 新增您的租用戶的位置，且符合-我網狀圖的位置。

- 估計預期及觀察到的網路效能和延遲特性從主要使用者位置，複製到 Office 365。 請記住，Office 365 是一組通用且分散式的服務，使用者將連線到可能和其租用戶的位置不同的位置。 基於這個理由，建議測量和透過 ExpressRoute 和網際網路連線最佳化使用者與最接近的 Microsoft 全球網路邊緣之間的延遲。 您可以使用從網路評估所發現的錯誤來完成這項作業幫助。

- 列出公司網路安全性及必須符合新的 ExpressRoute 連線的高可用性需求。 例如，如何使用者繼續以取得網際網路輸出或 ExpressRoute 線路失敗發生存取 Office 365。

- 文件的輸入和輸出的 Office 365 網路流向會使用網際網路路徑，然後使用 ExpressRoute 的哪。 地理位置的使用者與您的內部網路拓撲的詳細資料的詳細規可能需要從一位使用者的位置到另一個不同的計劃。

### <a name="catalog-your-outbound-and-inbound-network-traffic"></a>型錄，輸出和輸入網路流量
<a name="trafficCatalog"> </a>

路由和其他網路複雜度降至最低，我們建議您只使用 ExpressRoute for Office 365 的網路流量流程前往透過專用連線由於法規需求或網路評估的結果所需。 此外，我們建議您為不同且不同階段實作專案的階段 ExpressRoute 路由和方法輸出和輸入網路流量的範圍。 部署 ExpressRoute for Office 365，只是使用者起始輸出的網路流量流向與跨網際網路的輸入的網路流量可協助控制增加拓撲複雜性和其他的 [的簡介風險中保留的非對稱路由的可能性。
  
您的網路流量目錄應該包含您必須在內部網路與 Microsoft 之間的所有輸入和輸出網路連線的清單。
  
- 輸出的網路流量是任何位置連線從您的內部部署環境，例如從起始內部用戶端或伺服器，與 Microsoft 服務的目的地的案例。 這些連線可能是 Office 365 直接或間接，例如當連線會通過 proxy 伺服器、 防火牆或其他網路裝置的路徑上至 Office 365。

- 輸入的網路流量流向是從 Microsoft cloud 初始連線是其中，內部部署主機任何案例。 這些連線通常需要通過防火牆和客戶安全性原則需要外部起始之流向的其他安全性基礎結構。

請閱讀**確保路由對稱性來看**一節的文章[使用 ExpressRoute for Office 365 路由](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408)至判斷哪些服務將會傳送的輸入的流量，並尋找在[Office 365 中標示**ExpressRoute for Office 365**的資料行端點](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)參考文章，以判斷其餘的連線資訊。
  
每個服務所需的輸出連線，您會想要說明計劃的連線能力，包括網路路由、 proxy 組態、 封包檢查服務與頻寬需求。
  
每個服務所需的輸入的連線，您需要一些額外的資訊。 Microsoft cloud 中的伺服器將會建立連線至您的內部部署網路。 若要確保正確地進行連線，您會想要說明此連線，包括; 的所有層面會接受這些輸入的連線服務的公用 DNS 項目，CIDR 格式化 IPv4 IP 位址，涉及哪些 ISP 設備，以及如何輸入的 NAT 或來源 NAT 處理這些連線。
  
輸入的連線應該檢閱不論是否他們透過網際網路連線，或以確保非對稱式路由的 ExpressRoute 尚未已引進。 在某些情況下，內部部署端點 Office 365 服務啟動的傳入的連線可以可能也需要由其他 Microsoft 與非 Microsoft 服務。 很重要，啟用 ExpressRoute 路由傳送至 Office 365 進行這些服務不會中斷其他案例。 在許多情況下，客戶可能需要實作特定變更他們的內部網路，例如來源基礎 NAT，以確保來自 Microsoft 的輸入的流量保持對稱，啟用 ExpressRoute 之後。
  
以下是詳細資料所需的層級的範例。 在此情況下 Exchange 混合式會透過 ExpressRoute 路由至內部部署系統。

|**Connection 屬性**|**Value**|
|:-----|:-----|
|**網路流量方向** <br/> |輸入  <br/> |
|**服務** <br/> |Exchange 混合式  <br/> |
|**公用 Office 365 端點 （來源）** <br/> |Exchange Online （IP 位址）  <br/> |
|**公用內部端點 （目的地）** <br/> |5.5.5.5  <br/> |
|**公用 （網際網路） DNS 項目** <br/> |Autodiscover.contoso.com  <br/> |
|**將此內部部署端點用於其他 (非 Office 365) 的 Microsoft 服務** <br/> |否  <br/> |
|**將此內部部署端點可供網際網路上的使用者/系統** <br/> |是  <br/> |
|**透過公用的端點發佈的內部系統** <br/> |Exchange Server 用戶端存取角色 （內部） 192.168.101、 192.168.102、 192.168.103  <br/> |
|**IP 通告的公開端點** <br/> |**網際網路**： 5.5.0.0/16  <br/> **以 ExpressRoute**: 5.5.5.0/24  <br/> |
|**安全性/周邊控制項** <br/> |**網際網路路徑**： DeviceID_002  <br/> **ExpressRoute 路徑**： DeviceID_003  <br/> |
|**高可用性** <br/> |主動/主動跨 2 異地備援  <br/> ExpressRoute 電路-芝加哥與 Dallas  <br/> |
|**路徑對稱性來看控制項** <br/> |**方法**： 來源 NAT  <br/> **網際網路路徑**： 來源 NAT 輸入 192.168.5.5 的連線  <br/> |**ExpressRoute 路徑**： 192.168.1.0 （芝加哥） 與 192.168.2.0 (Dallas) 的來源 NAT 連線  <br/> |

以下是一種服務，只有輸出範例：

|**Connection 屬性**|**Value**|
|:-----|:-----|
|**網路流量方向** <br/> |輸出  <br/> |
|**服務** <br/> |SharePoint Online  <br/> |
|**內部部署端點 （來源）** <br/> |使用者工作站  <br/> |
|**公用 Office 365 端點 （目的地）** <br/> |SharePoint Online （IP 位址）  <br/> |
|**公用 （網際網路） DNS 項目** <br/> |\*。 sharepoint.com （和其他 Fqdn）  <br/> |
|**CDN 轉介** <br/> |cdn.sharepointonline.com （和其他 Fqdn）-CDN 提供者所維護的 IP 位址)  <br/> |
|**IP 廣告和使用中的 NAT** <br/> |**網際網路路徑/來源 NAT**: 1.1.1.0/24  <br/> **ExpressRoute 路徑/來源 NAT**: 1.1.2.0/24 （芝加哥） 和 1.1.3.0/24 (Dallas)  <br/> |
|**連線方法** <br/> |**網際網路**： 透過第 7 層 proxy （.pac 檔案）  <br/> **ExpressRoute**： 直接路由 (沒有 proxy)  <br/> |
|**安全性/周邊控制項** <br/> |**網際網路路徑**： DeviceID_002  <br/> **ExpressRoute 路徑**： DeviceID_003  <br/> |
|**高可用性** <br/> |**網際網路路徑**： 備援網際網路輸出  <br/> **ExpressRoute 路徑**： 主動/主動 '作用馬鈴薯' 路由跨 2 異地備援的 ExpressRoute 電路-芝加哥與 Dallas  <br/> |
|**路徑對稱性來看控制項** <br/> |**方法**： 來源的所有連線的 NAT  <br/> |

### <a name="your-network-topology-design-with-regional-connectivity"></a>您的網路拓撲設計，區域的連線
<a name="topology"> </a>

一旦您了解 services 和其相關聯的網路流量流程，您可以建立網狀圖，各有這些新的連線能力需求，並且說明您要使用 ExpressRoute for Office 365 進行的變更。 您的圖表應包含：
  
1. 其中從存取 Office 365 和其他服務的所有使用者位置。

2. 所有的網際網路和 ExpressRoute 出口點。

3. 所有輸出和輸入裝置管理內部和外部網路，包括路由器、 防火牆、 應用程式 proxy 伺服器，以及入侵偵測/防護的連線。

4. 所有的輸入流量，例如接受來自 ADFS 連線的內部 ADFS 伺服器的內部目的地 web 應用程式 proxy 伺服器。

5. 會通告的所有 IP 子網路的型錄

6. 識別人員會存取來自 Office 365 和列出符合每個位置-我將使用 ExpressRoute 的位置。

7. 位置和您的內部網路拓撲，其中會接受來自 ExpressRoute 學到 Microsoft IP 前置詞，部分的過濾並傳播至。

8. 網路拓撲應說明每個網路區段的地理位置，以及如何連線至 Microsoft network 透過 ExpressRoute 及/或網際網路。

下方圖表顯示每個位置其中人員將會使用從 Office 365 與 Office 365 的輸入和輸出路由廣告。
  
![ExpressRoute 區域地理符合-我](media/d866b36b-49bf-416b-af1b-d054e24989d2.png)
  
輸出的流量，人員存取 Office 365 中有三種：
  
1. 透過 meet-我中 「 北美地區 」 中的人員加州的位置。

2. 透過 meet-我香港] 中的位置中的人員香港。

3. 透過孟加拉其中有較少的人員，且沒有 ExpressRoute 線路佈建在網際網路。

![輸出連線的區域圖](media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
同樣地，從 Office 365 的輸入的網路流量會傳回下列三種方式之一：
  
1. 透過 meet-我中 「 北美地區 」 中的人員加州的位置。

2. 透過 meet-我香港] 中的位置中的人員香港。

3. 透過孟加拉其中有較少的人員，且沒有 ExpressRoute 線路佈建在網際網路。

![輸入的連線的區域圖](media/d6d6160d-bf28-4de3-a787-186c7432b306.png)
  
### <a name="determine-the-appropriate-meet-me-location"></a>決定適當的符合-我的位置

符合選取範圍-我的位置，也就是其中 ExpressRoute 線路連接至 Microsoft 網路的網路的實體位置，會受到其中人員會存取來自 Office 365 的位置。 為提供 SaaS，Office 365 不會運作 IaaS 或 PaaS 地區模型下 Azure 沒有相同的方式。 相反地，Office 365 是分散式的一組共同作業服務，使用者可能需要跨多個資料中心和區域，這可能不一定是相同的位置或主控使用者的租用戶的區域中連接至端點。
  
這表示您必須先選取符合時的最重要考量-我的 ExpressRoute for Office 365 的位置是在您的組織中的人員從的連接位置。 一般建議的最佳的 Office 365 連線是實作路由，使 Office 365 服務的使用者要求會交由關閉成 Microsoft 網路的最短的網路路徑，這通常也會被稱為 '作用馬鈴薯' 路由。 例如，如果大部分的 Office 365 使用者在一或兩個位置中，選取 [符合-我最接近的鄰近，以這些使用者的位置中的位置會建立最佳的設計。 如果貴公司有大量的使用者人數許多不同的區域中，您可能要考慮建立多個 ExpressRoute 電路符合-我的位置。 針對某些您使用者的位置，到 Microsoft 網路和 Office 365 的最短/最最佳路徑可能無法透過您內部的 WAN 和 ExpressRoute 符合-我點，但是透過網際網路。
  
通常時間有多個符合-我無法選取與您的使用者的相對近似值區域內的位置。 填寫下列表格來引導您決策。

|**計劃的 ExpressRoute 符合-我加州和 New York 中的位置**||
|:-----|:-----|
|位置  <br/> |人數  <br/> |透過網際網路輸出預期 Microsoft 網路延遲  <br/> |預期的延遲，Microsoft 網路，透過 ExpressRoute  <br/> |
|Los Angeles  <br/> |10,000  <br/> |~ 15ms  <br/> |~ 10 毫秒 （透過矽谷）  <br/> |
|華盛頓 DC  <br/> |15000  <br/> |~ 20 毫秒  <br/> |~ 10 毫秒 （透過 New York)  <br/> |
|Dallas  <br/> |5,000  <br/> |~ 15ms  <br/> |~ 40ms （透過 New York)  <br/> |

一旦顯示 Office 365 地區的全球網路架構，ExpressRoute 的網路服務提供者符合-我已開發位置，以及由位置的人員數量，它可以用來識別是否可以進行任何最佳化。 它也可以顯示全域髮夾網路連線其中流量路由傳送到遠端位置以取得符合-我的位置。 如果在全球網路髮夾找到它應該進行修復才能繼續執行。 尋找另一個符合-我的位置或使用選擇性網際網路上下文出口點，以避免發生髮夾。
  
第一個圖表中，「 北美地區 」 中顯示兩個實體位置與客戶的範例。 您可以看到的資訊辦公室的位置，Office 365 租用戶的位置，以及 ExpressRoute 的幾種選擇符合-我的位置。 在這個範例中，客戶已選取符合-我位置根據兩個原則，順序：
  
1. 最接近接近其組織中的人員。

2. 最接近中 Microsoft 資料中心主控 Office 365 的近似值。

![ExpressRoute 美國地理符合-我](media/5ec38274-b317-4ec1-91c8-90c2a7fd32ca.png)
  
稍微擴充此概念進一步範例跨國客戶面臨類似的資訊和決策第二個圖顯示。 此客戶有中孟加拉十個人員著重於得其使用量的區域中的小型小組使用小型的 office。 沒有符合-我辰內和 Microsoft 資料中心與 Office 365 中的位置中裝載辰內因此符合-我的位置就能明白;不過，十個人員，是各家其他電路費用。 為您查看您的網路時，您需要決定是否比消費以取得其他 ExpressRoute 線路首都更有效參與您網路上傳送您的網路流量的延遲。
  
或者，在孟加拉十個人員可能會遇到更好的效能其比會在他們的內部網路上中路由，我們示範簡介圖表及重現時，透過網際網路傳送至 Microsoft 網路的網路流量下面。
  
![輸出連線的區域圖](media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
## <a name="create-your-expressroute-for-office-365-implementation-plan"></a>建立您 ExpressRoute for Office 365 實作計劃
<a name="implementation"> </a>

您實作計劃應該包含這兩種技術的詳細資訊設定 ExpressRoute，以及設定所有其他基礎結構上您的網路，如下所示的詳細資料。
  
- 規劃 ExpressRoute 與網際網路之間分割的服務。

- 規劃頻寬、 安全性、 高可用性和容錯移轉。

- 設計輸入和輸出路由，包括適當的不同位置的路由路徑最佳化

- 決定 ExpressRoute 路由傳送到您網路的通告花費多少時間以及 「 什麼是以選取 [網際網路] 或 [ExpressRoute 路徑; 用戶端的機制例如，直接路由或應用程式 proxy。

- 規劃 DNS 記錄的變更，包括[寄件者原則架構](https://technet.microsoft.com/library/dn789058%28v=exchg.150%29.aspx)項目。

- 規劃 NAT 策略包括輸出和輸入來源 nat。

### <a name="plan-your-routing-with-both-internet-and-expressroute-network-paths"></a>規劃您的路由與網際網路和 ExpressRoute 的網路路徑
<a name="paths"> </a>

- 初始部署，所有輸入的服務，例如內送電子郵件或混合式連線，建議使用網際網路。

- 規劃使用者用戶端 LAN 路由，例如[設定 PAC/WPAD 檔案](https://aka.ms/manageo365endpoints)、 預設路由，proxy 伺服器及 BGP 路由廣告。

- 規劃外圍路由，包括 proxy 伺服器、 防火牆和雲端 proxy。

### <a name="plan-your-bandwidth-security-high-availability-and-failover"></a>規劃您的頻寬、 安全性、 高可用性和容錯移轉
<a name="availability"> </a>

建立計劃每個主要的 Office 365 工作負載所需的頻寬。 分開估計 Exchange Online、 SharePoint Online，與 Skype for Business Online 頻寬需求。 您可以使用我們提供 Exchange Online 和作為起點; 商務用 Skype 估計計算器不過，試驗測試與使用者設定檔及位置的代表性樣本才充分了解您組織的頻寬需求。
  
新增安全性，在每個網際網路和您的計劃的 ExpressRoute 輸出位置的處理方式，請記住所有 ExpressRoute 連線到 Office 365 使用公用對等，而且必須仍受到保護，根據連接至外部的您公司的安全性原則網路。
  
新增至相關的人員將會受到何種類型的中斷，這些人員如何將能夠最簡單的方式執行容量滿載其工作您計劃的詳細資訊。
  
#### <a name="plan-bandwidth-requirements-including-skype-for-business-requirements-on-jitter-latency-congestion-and-headroom"></a>規劃包括 Skype 抖動、 延遲、 擁塞、 和發揮空間的商務需求的頻寬需求
  
Skype 商務 Online 也有特定的其他網路需求[媒體品質和網路連線效能 Skype for Business Online 中](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)的文章會詳細說明。
  
請閱讀**頻寬規劃 Azure ExpressRoute 的**[網路規劃使用 ExpressRoute for Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd)一節。
  
執行時的頻寬評定，與您的試驗使用者，您可以使用我們的指南。[Office 365 效能調整使用基準與效能歷程記錄](https://support.office.com/article/Office-365-performance-tuning-using-baselines-and-performance-history-1492cb94-bd62-43e6-b8d0-2a61ed88ebae)。
  
#### <a name="plan-for-high-availability-requirements"></a>規劃高可用性需求
  
建立計畫，以符合您的需求與這併入更新的網路拓撲圖表的高可用性。 閱讀 [] 區段中**的高可用性和容錯移轉進行 Azure ExpressRoute**的[網路規劃使用 ExpressRoute for Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd)。
  
#### <a name="plan-for-network-security-requirements"></a>如需網路安全性需求的計劃
  
建立計畫，以符合您的網路安全性需求與這併入更新的網路拓撲圖表。 閱讀 [] 區段中**套用安全性控制，以便 Azure ExpressRoute for Office 365 案例**中[使用 ExpressRoute for Office 365 的網路規劃](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd)。
  
### <a name="design-outbound-service-connectivity"></a>設計輸出服務連線
<a name="outbound"> </a>

ExpressRoute for Office 365 有可能不太熟悉的*輸出*網路需求。 具體而言，IP 位址，代表您的使用者與網路到 Office 365，且作為給 Microsoft 的輸出網路連線的來源端點必須遵循以下所述的特定需求。
  
1. 端點必須是公用 IP 位址，已註冊您的公司或電訊廠商提供給您的 ExpressRoute 連線。

2. 由 ExpressRoute 必須通告給 Microsoft 及驗證/接受端點。

3. 端點必須不會通告到具有相同或更多的慣用路由公制網際網路。

4. 端點必須不用於未設定透過 ExpressRoute 的 Microsoft 服務的連線。

如果您的網路設計不符合這些需求，則您的使用者會體驗到 Office 365 和其他 Microsoft 服務，因為路由黑色 holing 或非對稱式路由的連線失敗高風險。 會發生這種情況時要求送至 Microsoft 服務透過 ExpressRoute，路由傳送，但回應會路由傳送回跨網際網路，或反之，以及回應會捨棄封狀態的網路裝置，例如防火牆。
  
您可以使用符合上述需求的常見方法是網路的使用來源實作為您的一部分，或您 ExpressRoute 電訊廠商所提供的 NAT。 來源 NAT 可讓您擷取的詳細資訊與私人 IP 位址設定網際網路網路的 ExpressRoute 從和;搭配適當 IP 路由廣告，提供簡單的機制，以確保路徑對稱性。 如果您正在使用 ExpressRoute 對等位置特有的設定狀態的網路裝置，您必須實作不同的 NAT 集區的每個對等以確定路徑對稱性來看的 ExpressRoute。
  
閱讀的有關[ExpressRoute NAT 需求](https://azure.microsoft.com/documentation/articles/expressroute-nat/)的詳細資訊。
  
網路拓撲圖表中新增的輸出連線的變更。
  
### <a name="design-inbound-service-connectivity"></a>設計輸入的服務連線
<a name="inbound"> </a>

大部分的 Office 365 企業版部署假設在某種形式的輸入連線從 Office 365 的內部服務，例如 Exchange、 SharePoint 和 Skype for Business 的混合式案例、 信箱移轉和使用 ADFS 的驗證基礎結構。 當啟用您的內部網路與 Microsoft 之間的輸出連線其他路由路徑的 ExpressRoute，這些輸入的連線可能會不小心受到非對稱式路由，即使您想要有這些流程繼續使用網際網路。 若要確保有不會影響到網際網路型從 Office 365 與內部部署系統的輸入的流量建議如下所述的一些預防措施。
  
最小化的非對稱式路由內送的網路流量的風險，所有的輸入連線應該使用來源 NAT 之前他們正在路由傳送到您的網路區段有 ExpressRoute 路由的可視性。 如果傳入的連線至網路區段中所允許的沒有來源 NAT ExpressRoute 路由查看，來自 Office 365 的要求會進入從網際網路，但回到 Office 365 的回應會偏好 ExpressRoute回到 Microsoft 網路，而造成非對稱式路由的網路路徑。
  
您可能會考慮下列其中一個下列實作模式以滿足此需求：
  
1. 要求路由傳送到您的內部網路使用網路設備，例如防火牆之前執行來源 NAT 或負載平衡器的路徑上從網際網路至您的內部部署系統。

2. 請確定 ExpressRoute 路由不會傳播到其中輸入的服務，例如前方端伺服器或反向 proxy 系統，處理的網際網路連線位於網路區段。

明確 accounting 對這些案例中您的網路，並保留所有內送的網路流量會透過網際網路協助部署和操作的非對稱式路由的風險降至最低。
  
可能會有您可以選擇將某些輸入的流量導向透過 ExpressRoute 連線的情況。 這些情況下，需要考慮下列額外考量。
  
1. Office 365 可以只目標內部部署端點，使用公用 Ip。 這表示即使內部輸入的端點只會公開給 Office 365 透過 ExpressRoute，仍然需要有與它相關聯的公用 IP。

2. 若要解決內部部署端點，執行 Office 365 服務的所有 DNS 名稱解析都發生使用公用 DNS。 這表示您必須註冊輸入的服務端點的 FQDN，以在網際網路上的 IP 對應。

3. 若要透過 ExpressRoute 接收內送的網路連線，這些端點的公用 IP 子網路必須透過 ExpressRoute 通告給 Microsoft。

4. 仔細評估，以確保該適當的安全性這些輸入的網路流量流量和網路控制項時，會套用至其上，根據您的公司安全性和網路原則。

5. 一次您在內部部署輸入的端點會通告給 Microsoft，透過 ExpressRoute、 ExpressRoute 將有效成為那些端點的所有 Microsoft 服務，包括 Office 365 的慣用路由路徑。 這表示，這些端點子網路必須僅可用於與 Office 365 服務和 Microsoft 網路上的任何其他服務的通訊。 否則，您的設計會導致其中來自其他 Microsoft 服務偏好路由傳送的輸入的連線輸入透過 ExpressRoute，雖然傳回路徑將會使用網際網路的非對稱式路由。

6. 在事件 ExpressRoute 電路或符合-我位置已關閉，您需要確定內部輸入的端點是仍可接受要求透過不同的網路路徑。 這可能表示廣告子網路，透過多重 ExpressRoute 電路這些端點。

7. 我們建議您套用來源 NAT 輸入您的網路，透過 ExpressRoute，尤其是當這些流量跨設定狀態的網路裝置，例如防火牆的所有內送的網路流量流程。

8. 某些內部服務，例如 ADFS proxy 或 Exchange 自動探索，可能會收到輸入的要求從 Office 365 服務，以及來自網際網路的使用者。 這些要求的 Office 365 會透過網際網路目標相同的 FQDN，因為使用者要求。 時強制使用 ExpressRoute，Office 365 連線到這些內部部署端點，允許輸入的使用者的連線從網際網路代表重大路由的複雜性。 對於大多數的客戶透過 ExpressRoute 實作這類複雜的案例建議您不要由於操作考量。 此額外的負荷量包含，管理風險的非對稱式路由，並且需要您仔細跨多個維度中管理路由廣告和原則。

### <a name="update-your-network-topology-plan-to-show-how-you-would-avoid-asymmetric-routes"></a>更新您的網路拓撲計劃，以顯示您想要如何避免非對稱式路由
<a name="asymmetric"> </a>

您想要避免以確保您組織中的人員可以順暢地使用 Office 365，以及其他重要服務在網際網路上的非對稱式路由。 有兩種常見設定客戶可有非對稱式路由會造成。 現在是很好的時間才能檢閱您計劃要使用並檢查其中一個這些非對稱的路由案例可能存在於網路組態。
  
若要開始，我們將檢查幾個不同的情況下的網狀圖相關聯。 在此圖表中，所有伺服器接收傳入的要求，例如 ADFS 或內部部署混合伺服器皆紐澤西資料中心，並通知給網際網路。
  
1. 周邊網路安全時，沒有任何來源 NAT 可用的傳入要求。

2. 紐澤西資料中心中的伺服器都能看到網際網路和 ExpressRoute 路由。

![ExpressRoute 連線概觀](media/8f074af6-ef38-44e8-bc5a-8b4d981fbb20.png)
  
我們也會有如何修正它們的建議。
  
#### <a name="problem-1-cloud-to-on-premises-connection-over-the-internet"></a>問題 1： 雲端與在網際網路上的內部部署連線
  
下圖說明當您的網路組態不會透過網際網路的輸入要求從 Microsoft cloud 中提供 NAT 時採取的非對稱的網路路徑。
  
1. 從 Office 365 的輸入的要求從公用 DNS 擷取內部部署端點的 IP 位址，並將要求傳送至您的周邊網路。

2. 在此無效的組態中，沒有設定任何來源 NAT 或可在周邊網路流量所在傳送產生的實際的來源 IP 位址被用來作為傳回目的地。

  - 您網路上的伺服器會透過任何可用的 ExpressRoute 網路連線，將傳回流量路由到 Office 365。

  - 結果是該流向 Office 365，導致中斷連線的非對稱路徑。

![ExpressRoute Asymetric 路由問題 1](media/9c210c2a-e0ea-4180-8ede-1bf41746ce7a.png)
  
##### <a name="solution-1a-source-nat"></a>解決方案 1a： 來源 NAT
  
只要將 NAT 的來源加入到的傳入要求解析此設定錯誤的網路。 在此圖表中：
  
1. 傳入的要求會繼續輸入透過紐澤西資料中心的周邊網路。 這段時間來源 NAT 使用。

2. 從回聚集 nat 來源而不是原始的 IP 位址，傳回相同的網路路徑在回應中產生關聯的 IP 伺服器路由傳送回應。

![ExpressRoute Asymetric 路由方案 1](media/0e87a155-f8de-48ed-92ac-27367b727a82.png)
  
##### <a name="solution-1b-route-scoping"></a>解決方案 1b： 路由範圍設定
  
或者，您可以選擇不允許前置詞才能被公告 ExpressRoute BGP 移除這些電腦的替代的網路路徑。 在此圖表中：
  
1. 傳入的要求會繼續輸入透過紐澤西資料中心的周邊網路。 這一次透過 ExpressRoute 線路通告來自 Microsoft 的前置詞不到紐澤西資料中心。

2. 從伺服器路由傳送的回應備份聚集傳回相同的網路路徑在回應中所產生的 IP 上可用的唯一路由相關聯的原始 IP 位址。

![ExpressRoute Asymetric 路由方案 2](media/9cb4b2bf-7aa6-487a-bc02-e02af8a979f6.png)
  
#### <a name="problem-2-cloud-to-on-premises-connection-over-expressroute"></a>問題 2： 雲端與內部連線透過 ExpressRoute
  
下圖說明當您的網路組態不會提供從 Microsoft cloud 的輸入要求的 NAT 透過 ExpressRoute 時採取的非對稱的網路路徑。
  
1. 從 Office 365 的輸入的要求從 DNS 擷取的 IP 位址，並將要求傳送至您的周邊網路。

2. 在此無效的組態中，沒有設定任何來源 NAT 或可在周邊網路流量所在傳送產生的實際的來源 IP 位址被用來作為傳回目的地。

  - 在您的網路上的電腦將傳回流量路由到 Office 365 透過任何可用的 ExpressRoute 網路連線。

  - 結果是 Office 365 的非對稱式連線。

![ExpressRoute Asymetric 路由問題 2](media/f6fd155b-bbb7-472a-846e-039a99f09913.png)
  
##### <a name="solution-2-source-nat"></a>解決方案 2： 來源 NAT
  
只要將 NAT 的來源加入到的傳入要求解析此設定錯誤的網路。 在此圖表中：
  
1. 傳入的要求會繼續輸入透過紐約資料中心的周邊網路。 這段時間來源 NAT 使用。

2. 從回聚集 nat 來源而不是原始的 IP 位址，傳回相同的網路路徑在回應中產生關聯的 IP 伺服器路由傳送回應。

![ExpressRoute Asymetric 路由方案 3](media/a5d2b90d-a3ec-4047-afbf-6e6e99f376a7.png)
  
### <a name="paper-verify-that-the-network-design-has-path-symmetry"></a>紙張確認網路設計具有路徑對稱性來看

此時，您必須確認在紙張上實作計劃提供路由對稱性來看，不同案例中您要使用 Office 365。 您將識別預期會在使用服務的不同功能時所要採取的特定網路路由。 從內部網路和 WAN 路由至周邊裝置，來連線的路徑。ExpressRoute 或網際網路，並登入 online 端點的連線。
  
您需要這麼做的所有 Office 365 網路服務先前已識別為您的組織將採用的服務。
  
很有幫助不要使用另一位使用者路由此白皮書逐一檢查。 說明這些其中每個網路躍點預計需要取得從其下一個路由，並確定您熟悉的路由路徑。 請記住 ExpressRoute 一律會提供更多範圍的路由，以提供比網際網路預設路由的路由成本較低的 Microsoft 伺服器 IP 位址。
  
### <a name="design-client-connectivity-configuration"></a>設計用戶端連線設定
<a name="asymmetric"> </a>

![使用 ExpressRoute 的 PAC 檔案](media/7cfa6482-dbae-416a-ae6f-a45e5f4de23b.png)
  
如果您正在使用網際網路 proxy 伺服器繫結的流量，然後您要調整任何 PAC 或用戶端設定檔，以確保您網路上的用戶端電腦已正確設定為您想要的 ExpressRoute 流量傳送至 Office 365，而不 transiting您的 proxy 伺服器，以及剩餘的流量，包括一些 Office 365 流量，會傳送至相關的 proxy。 閱讀我們的指南，在[管理 Office 365 端點](https://aka.ms/manageo365endpoints)，例如 PAC 檔案。
  
> [!NOTE]
> 端點變更經常、 每週的頻率。 您只應該進行變更為基礎的服務和功能貴組織已採用以減少您需要對保持最新變更的數目。 關閉必須注意宣佈所做的變更，並記錄會保留的所有變更，IP 過去宣佈的地址的 RSS 摘要中的**有效日期**可能未通告，或移除通告，直到達到有效的日期。
  
## <a name="build-your-deployment-and-testing-procedures"></a>建立您的部署和測試程序
<a name="testing"> </a>

您實作計劃應該包含測試及復原計劃。 如果您實作未如預期般運作中，為了影響最少計劃的人員之前探索到的問題。 以下是您的計劃應該考慮一些高階原則。
  
1. 階段網路區段和使用者服務上架干擾降至最低。

2. 規劃測試使用 traceroute 路由和 TCP 連線從不同的網際網路連線的主機。

3. 最好的輸入和輸出服務測試應與測試 Office 365 租用戶隔離的測試網路上。

      - 或者，測試可執行生產網路若還不使用 Office 365 客戶，或位於試驗。

      - 或者，測試可以執行測試放在一旁設定實際執行中斷期間和監控僅。

      - 或者，測試可透過檢查每個第 3 層路由器節點上每個服務的路由。 此改回應該只用於如果沒有其他測試可能是因為缺少的實體測試介紹風險。

### <a name="build-your-deployment-procedures"></a>建立您的部署程序

您的部署程序應該推行至小群人分階段以供測試，再部署至較大群人。 以下是幾種方式可以階段 ExpressRoute 的部署。
  
1. 設定與 Microsoft 對等的 ExpressRoute 和已轉寄給僅適用於單一主機的路由通告分段測試之用。

2. 通告路由到單一網路區段第一次 ExpressRoute 網路，並展開路由廣告網路區段或區域。

3. 如果第一次部署 Office 365，請使用 ExpressRoute 網路部署試驗為數目更少的人員。

4. 如果使用 proxy 伺服器，您可以另外設定測試 PAC 檔案之前新增更多導向少數幾個受損人士 ExpressRoute 來測試和意見反應。

您實作計劃應列出每個必須採取的部署程序或要用來部署的網路組態的命令。 當網路中斷時間會進入的所有變更，這是 arbutus solutions 事先撰寫的部署計劃和對等應該進行都檢閱。 ExpressRoute 技術組態，請參閱指導方針。
  
- 如果您已經變更的任何仍會繼續傳送電子郵件的內部部署伺服器的 IP 位址，請更新您的 SPF TXT 記錄。

- 如果您已經變更以容納新的 NAT 設定的 IP 位址，請更新內部部署伺服器的任何 DNS 項目。

- 請確定您已訂閱 rss 摘要，以維持任何路由或 proxy 設定的 Office 365 端點通知。

ExpressRoute 部署完成之後，應該要執行的測試計劃中的程序。 每個程序的結果應該會記錄。 您必須包含復原到原始的實際執行環境事件中的測試計劃結果指出實作未成功的程序。
  
### <a name="build-your-test-procedures"></a>建立測試程序

您測試的程序應該包含對於 Office 365 每個輸出和輸入網路服務將會使用 ExpressRoute 和則不會測試。 這些程序應該包括測試從每個唯一的網路位置，包括不是在內部公司的 LAN 中的使用者。
  
測試活動的一些範例包括：
  
1. 從您的內部路由器 ping 到您網路的運算子路由器。

2. 驗證 500 + Office 365 和 CRM Online IP 位址廣告會接收到您的內部路由器。

3. 驗證您輸入和輸出的 NAT ExpressRoute 和內部部署網路間運作。

4. 驗證您的 nat 路由會被通告從您的路由器。

5. 驗證 ExpressRoute 已接受您公告的前置詞。

      - 若要確認對等的廣告使用下列 cmdlet:

      ```PowerShell
      Get-AzureRmExpressRouteCircuitRouteTable -DevicePath Primary -ExpressRouteCircuitName TestER -ResourceGroupName RG -PeeringType MicrosoftPeering
      ```

6. 驗證公用 NAT IP 範圍未通知伺服器向 Microsoft 透過 ExpressRoute 或公用的網際網路網路電路除非它是較大的範圍，如上述範例所示的特定子集合。

7. ExpressRoute 電路成對出現，驗證執行這兩個 BGP 工作階段。

8. 設定您的 NAT 的內部單一主機，使用 ping、 tracert 及 tcpping 跨至主機 outlook.office365.com 的新電路測試連線。 或者，您可以使用 Wireshark 之類的工具，或若要驗證您 MSEE 鏡像連接埠上的 Microsoft Network Monitor 3.4 是能夠連線至 outlook.office365.com 相關聯的 IP 位址。

9. Exchange Online 的測試應用程式層級的功能。

  - 測試 Outlook 是能夠連線到 Exchange Online，並傳送/接收電子郵件。

  - 測試 Outlook 是能夠使用線上模式。

  - 測試智慧型手機連線和收發能力。

10. SharePoint Online 的測試應用程式層級功能

  - 測試 OneDrive for Business 同步處理用戶端。

  - 測試 SharePoint Online web access。

11. 測試應用程式層級的功能，skype 商務呼叫案例：

  - 加入電話會議，以驗證的使用者 [由使用者起始的邀請]。

  - 邀請使用者電話會議 [寄件者 MCU 邀請]。

  - 使用 Skype for Business web 應用程式的匿名使用者加入會議。

  - 加入從有線的電腦連線、 IP 電話和行動裝置的通話。

  - 呼叫以同盟的使用者 o PSTN 驗證的呼叫： 呼叫完成，是可接受的通話品質，是可接受的連線時間。

  - 確認連絡人的目前狀態更新這兩個成員的租用戶和同盟使用者。

### <a name="common-problems"></a>常見的問題

非對稱式路由是最常見的實作問題。 以下是一些常見的來源，以尋找：
  
- 使用 open 或平面網路路由拓撲不來源就地 NAT。

- 不使用 SNAT 來路由傳送至輸入服務透過網際網路與 ExpressRoute 連線。

- 不測試上 ExpressRoute 廣泛部署之前先測試網路上的內送的服務。

## <a name="deploying-expressroute-connectivity-through-your-network"></a>部署 ExpressRoute 連線到您的網路
<a name="testing"> </a>

階段您一次，逐漸推出至不同的組件的計劃將回復為每個新的網路區段的網路連線網路的一條線段的部署。 如果您的部署與 Office 365 部署對齊，第一次部署至您的 Office 365 試驗使用者，並從該處擴充。
  
第一個測試然後為了建立生產環境：
  
- 執行啟用 ExpressRoute 的部署步驟。

- 測試您的網路路由已如預期般地看到。

- 執行測試每個輸入和輸出的服務。

- 如果您發現任何問題，復原。

### <a name="set-up-a-test-connection-to-expressroute-with-a-test-network-segment"></a>測試網路區段，使用 ExpressRoute 的測試連線設定

現在，您必須在紙張上的已完成計劃該是時候來在小規模地測試。 此測試中您將內部部署網路上建立測試子網路與 Microsoft Peering 單一 ExpressRoute 連線。 您可以連線到及傳送自測試子網路設定[試用版的 Office 365 租用戶](https://go.microsoft.com/fwlink/p/?LinkID=403802)，並在生產環境中測試子網路中包含您要使用的所有輸出和輸入服務。 設定 DNS 進行測試網路區段，並建立輸入和輸出的所有服務。 執行測試計劃，請確定您已熟悉針對每個服務和路由傳播路由傳送。
  
### <a name="execute-the-deployment-and-test-plans"></a>執行部署和測試計劃

完成上述的項目之後，請關閉區域您已完成，並確定您和您的小組檢閱它們之前執行您的部署和測試計劃。
  
- 輸出和輸入網路變更相關的服務清單。

- 全球網路架構圖中顯示網際網路輸出及 ExpressRoute 符合-我的位置。

- 路由網狀示範部署每個服務使用不同的網路路徑。

- 部署計劃與實作的變更和復原，如有需要的步驟。

- 測試每個 Office 365 和網路服務測試計劃。

- 完成輸入和輸出服務的實際執行路由紙張驗證。

- 跨測試網路區段，包括可用性測試完成的測試。

選擇 [中斷時間長度可透過在整個部署規劃和測試計劃執行，有一些疑難排解可用的時間和復原回如有需要的時間。
  
> [!CAUTION]
> 由於透過網際網路與 ExpressRoute 路由複雜的性質，最好是其他緩衝區時間會新增此視窗以處理疑難排解複雜路由。
  
### <a name="configure-qos-for-skype-for-business-online"></a>QoS skype for Business Online 設定

QoS 是必要商務用 Skype 取得語音和會議的優點。 您必須確定滿足 ExpressRoute 的網路連線不會封鎖任何您其他 Office 365 服務存取權之後，您可以設定 QoS。 設定 QoS 所述[的 ExpressRoute 與 QoS Skype for Business Online 中](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d)的文章。
  
## <a name="troubleshooting-your-implementation"></a>疑難排解您實作
<a name="troubleshooting"> </a>

若要尋找的第一個位置位於此實作指南 》 中的步驟是任何未接在您實作計劃嗎？ 請返回並執行進一步小型網路複寫錯誤和偵錯它那里盡可能測試。
  
識別可輸入或輸出 services 無法在測試期間。 每個失敗之服務取得特別的 IP 位址和子網路。 得出引導紙張上的網路拓撲圖表並驗證的路由。 驗證特別其中 ExpressRoute 路由會通知給、 測試該路由中斷期間盡可能與追蹤項目。
  
使用網路追蹤執行 PSPing，為每個客戶端點，並評估來源及目的地 IP 位址，以驗證其如預期般。 執行您在通訊埠 25 上公開，並確認 SNAT 隱藏的原始來源 IP 位址，是否這可預期的任何郵件主機 telnet。
  
請記住，同時部署 Office 365 具有您需要確保這兩個網路組態的 ExpressRoute ExpressRoute 連線的最佳方式設計，而且您也已最佳化其他元件您的網路，例如用戶端電腦上。 除了使用這個規劃指南來疑難排解您可能會有未接的步驟，我們也已寫入[效能疑難排解規劃 Office 365](https://support.office.com/article/Performance-troubleshooting-plan-for-Office-365-e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c) 。
  
您可以使用下列短連結返回這裡：[https://aka.ms/implementexpressroute365](https://aka.ms/implementexpressroute365)
  
## <a name="related-topics"></a>相關主題

[評估 Office 365 網路連線](assessing-network-connectivity.md)
  
[Azure ExpressRoute for Office 365](azure-expressroute.md)
  
[管理 ExpressRoute for Office 365 連線](managing-expressroute-for-connectivity.md)
  
[使用 ExpressRoute for Office 365 進行路由傳送](routing-with-expressroute.md)
  
[使用 ExpressRoute for Office 365 進行網路規劃](network-planning-with-expressroute.md)
  
[使用 BGP 社群中 ExpressRoute for Office 365 案例 （預覽）](bgp-communities-in-expressroute.md)
  
[商務用 Skype Online 中的媒體品質和網路連線效能](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917) (英文)
  
[針對商務用 Skype Online 最佳化您的網路](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43) (英文)
  
[ExpressRoute 與 QoS skype for Business Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[使用 ExpressRoute 的通話流程](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[使用基準與效能歷程記錄進行 Office 365 效能調整](performance-tuning-using-baselines-and-history.md)
  
[Office 365 的效能疑難排解規劃](performance-troubleshooting-plan.md)
  
[Office 365 URL 與 IP 位址範圍](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) (英文)
  
[Office 365 網路與效能調整](network-planning-and-performance.md)
