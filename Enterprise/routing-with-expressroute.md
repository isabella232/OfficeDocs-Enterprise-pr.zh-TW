---
title: 使用 ExpressRoute for Office 365 進行路由傳送
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/14/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: e1da26c6-2d39-4379-af6f-4da213218408
description: 若要適當地了解路由至 Azure ExpressRoute Office 365 流量，您需要的核心 ExpressRoute 路由需求和 ExpressRoute 電路及路由網域的公司掌握。 使用 ExpressRoute 的 Office 365 客戶將會依賴的基本概念版面配置這些設定。
ms.openlocfilehash: 01251880eba2051d8839f7c08e244398906c75ed
ms.sourcegitcommit: 0449c6f854c682719cac1bd0d086f2e3b20078b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "34722712"
---
# <a name="routing-with-expressroute-for-office-365"></a>使用 ExpressRoute for Office 365 進行路由傳送

若要正確地了解路由至 Azure ExpressRoute Office 365 流量，您需要核心[ExpressRoute 路由需求](https://azure.microsoft.com/documentation/articles/expressroute-routing/)和[ExpressRoute 電路及路由網域](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/)公司的掌握。 使用 ExpressRoute 的 Office 365 客戶將會依賴的基本概念版面配置這些設定。
  
一些您需要了解上述文章中的主要項目包括：
  
- ExpressRoute 電路未對應至特定的實體基礎結構，但在單一的對等位置由 Microsoft 和對等的提供者，代表您所做的邏輯連接。

- 沒有 ExpressRoute 線路與客戶的鍵之間的 1:1 對應。

- 每個電路可支援 2 獨立的對等關係 （Azure 私人對等，以及 Microsoft 對等）;Office 365 需要 Microsoft 對等。

- 每個電路具有固定的頻寬共用跨所有對等關係。

- 任何公用 IPv4 位址，並為將使用的數字公用的 ExpressRoute 電路必須驗證為其擁有者，或以獨佔方式由指派的位址範圍的擁有者。

- 虛擬 ExpressRoute 電路備援全域且需要遵循標準的 BGP 路由的作法。 這也是為什麼我們建議您在主動/主動組態中的提供者輸出每兩個實體電路。

請參閱[常見問題集網頁](https://azure.microsoft.com/documentation/articles/expressroute-faqs/)如需詳細的 services 支援的詳細資訊，成本，以及設定詳細資料。 在提供 Microsoft 對等支援的連線供應商的清單，請參閱[ExpressRoute 位置文章](https://azure.microsoft.com/documentation/articles/expressroute-locations/)的資訊。 我們也已記錄以協助說明的概念更徹底 Channel 9 10 部分的[Azure ExpressRoute for Office 365 訓練](https://channel9.msdn.com/series/aer)系列。
  
## <a name="ensuring-route-symmetry"></a>確保路由對稱性來看

Office 365 前端伺服器都可存取網際網路和 ExpressRoute 上。 這些伺服器會路由傳送回至內部部署透過 ExpressRoute 電路兩者都可供使用時偏好。 因為這會封路由為中心不對稱如果從您的網路流量偏好透過網際網路電路路由傳送。 非對稱路由是問題，因為裝置執行設定狀態的封包檢查可以封鎖傳回流量，後面接著輸出封包不同的路徑。
  
不論是否初始透過網際網路或 ExpressRoute 連線到 Office 365，此來源必須是公開可路由的地址。 直接與 Microsoft 對等的許多客戶，與具有私人位址重複所在客戶之間可能不可行的情況下。
  
以下是的案例進行初始化來自 Office 365 到您的內部網路的通訊。 為了簡化您的網路設計，我們建議路由傳送這些透過網際網路路徑。
  
- SMTP 服務，例如郵件從 Exchange Online 租用戶至內部部署主機或 SharePoint Online 的郵件，從 SharePoint Online 傳送至內部部署主機。 Microsoft 的網路內，比路由首碼共用透過 ExpressRoute 電路和廣告內部 SMTP 伺服器透過 ExpressRoute 會導致失敗與這些其他服務 SMTP 通訊協定是更廣泛地使用。

- 在 [密碼驗證登入期間 ADFS。

- [Exchange Server Hybrid deployments](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx)。

- [SharePoint 同盟混合式搜尋](https://technet.microsoft.com/library/dn197174.aspx)。

- [SharePoint 混合式 BCS](https://technet.microsoft.com/library/dn197239.aspx )。

- [混合式商務用 Skype](https://technet.microsoft.com/en-us/library/jj205403.aspx)和/或[商務用 Skype 商務同盟](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx)。

- [Skype 商務雲端連接器](https://technet.microsoft.com/library/mt605227.aspx )。

Microsoft 回您的網路以這些雙向流量流量路由傳送，則必須與 Microsoft 共用 BGP 路由到您內部部署的裝置。 當您透過 ExpressRoute 通告路由傳送給 Microsoft 的前置詞時，您應該遵循這些最佳作法：

1) 未通告相同公用 IP 位址路由首碼到公用網際網路，透過 ExpressRoute。 強烈建議您透過 ExpressRoute Microsoft IP BGP 路由首碼廣告是來自未到網際網路，所有通知的範圍。 如果這是不可能達到因為可用的 IP 位址空間，則必須確定透過 ExpressRoute 通告更多特定範圍比任何網際網路電路。

2) 使用個別的 NAT IP 集區，每個 ExpressRoute 線路和個別的設為您的網際網路電路。

3) 請注意任何通知給 Microsoft 的路由會吸引來自 Microsoft 的網路，不僅那些，路由會通知給您的網路透過 ExpressRoute 中任何伺服器的網路流量。 僅通告路由傳送至伺服器的路由案例定義，而充分了解您的小組。 通告個別 IP 位址路由前置詞，在每個多重 ExpressRoute 電路從您的網路。 
  
## <a name="deciding-which-applications-and-features-route-over-expressroute"></a>決定哪些應用程式和功能透過 ExpressRoute 路由

當您設定使用 Microsoft 對等路由網域的對等關係，都會被核准適當的存取權時，您將能夠看到可用的所有 PaaS 和 SaaS 服務透過 ExpressRoute。 設計 for ExpressRoute Office 365 服務可以管理與[BGP 社群](https://aka.ms/bgpexpressroute365)或[路由傳送的篩選器](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal)。
  
其他應用程式，例如 Office 365 影片，為 Office 365 應用程式。不過，Office 365 影片被組成三個不同的元件、 入口網站、 資料流的服務，以及內容傳遞網路。 在入口網站都位於內 SharePoint Online 中，資料流服務生活內 Azure 媒體服務，而內容傳遞網路都位於 Azure CDN 內。 下表概述這些元件。
  
| |
|**元件**|**基礎應用程式**|**包含 SharePoint Online 的 BGP 社群中？**|**使用**|
|:-----|:-----|:-----|:-----|
|Office 365 影片入口網站  <br/> |SharePoint Online  <br/> |是  <br/> |設定、 上傳  <br/> |
|Office 365 視訊資料流服務  <br/> |Azure 媒體服務  <br/> |否  <br/> |使用事件中影片是從 CDN 無法使用服務的資料流  <br/> |
|Office 365 影片內容傳遞網路  <br/> |Azure CDN  <br/> |否  <br/> |來源主要視訊下載/資料流。 [解更多關於 Office 365 影片網路](https://support.office.com/article/Office-365-Video-networking-Frequently-Asked-Questions-FAQ-2bed67a1-4052-49ff-a4ce-b7e6530eb98e)。  <br/> |

每個 Office 365 功能，可使用 Microsoft 對等會列在[Office 365 端點文章](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)的應用程式類型和 FQDN。 在資料表中使用 FQDN 的原因，是為了讓客戶能夠管理流量使用的 PAC 檔案或其他 proxy 設定，請參閱[管理 Office 365 端點](https://aka.ms/manageo365endpoints)，例如 PAC 檔案我們指南。
  
在某些情況下，我們已使用不同的較高的層級萬用字元網域通告一或多個 sub Fqdn 是萬用字元網域。 這通常是因為當萬用字元表示所有通知給 ExpressRoute 與網際網路，而子少數的目的地僅通告到網際網路或反向的伺服器的完整清單。 請參閱了解其中差異在於下列資料表。
  
此表會顯示到網際網路並 Azure ExpressRoute 萬用字元會通告的 Fqdn，以及到網際網路僅通告 sub Fqdn。

|**萬用字元網域通知給 ExpressRoute 和網際網路電路**|**Sub FQDN 到網際網路迴路僅通告**|
|:-----|:-----|
|\*。 microsoftonline.com  <br/> |click.email.microsoftonline.com  <br/> portal.microsoftonline.com  <br/> provisioningapi.microsoftonline.com  <br/> adminwebservice.microsoftonline.com  <br/> |
|\*。 officeapps.live.com  <br/> |nexusRules.officeapps.live.com  <br/> nexus.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> cdn.odc.officeapps.live.com  <br/> ols.officeapps.live.com  <br/> ocsredir.officeapps.live.com  <br/> ocws.officeapps.live.com  <br/> ocsa.officeapps.live.com  <br/> |

通常是主要的 PAC 檔案在將網路要求傳送至 ExpressRoute 通告直接對電路端點和所有其他網路要求您的 proxy。 如果您正在設定這樣的 PAC 檔案，撰寫您依下列順序的 PAC 檔案：
  
1. 在您傳送的流量，向您的 proxy 的 PAC 檔案頂端在上述表格中包含從兩個資料行 sub Fqdn。 我們已內建供您管理[Office 365 端點](https://aka.ms/manageexpressroute365)文章中所使用的範例 PAC 檔案。

2. 包含所有 Fqdn 標示公告第一個區段中下, 面[這篇文章](https://aka.ms/o365endpoints)中的 ExpressRoute ExpressRoute 線路來直接傳送的流量。

3. 包含任何其他網路端點或傳送的流量，向您的 proxy 這些兩個項目下方的規則。

此表格顯示僅通告至 Azure ExpressRoute sub Fqdn 旁的網際網路電路和網際網路電路會通告萬用字元網域。 上面兩欄中的 Fqdn 您 PAC 檔案表格下方列為 「 正在通知給 ExpressRoute 的連結參照，這表示它們會包含第二個群組中的檔案中的項目。

|**萬用字元網域至網際網路迴路僅通告**|**Sub FQDN 通知給 ExpressRoute 和網際網路電路**|
|:-----|:-----|
|\*。 office.com  <br/> |\*。 outlook.office.com  <br/> home.office.com  <br/> outlook.office.com  <br/> portal.office.com  <br/> www.office.com  <br/> |
|\*。 office.net  <br/> |agent.office.net  <br/> |
|\*。.office365.com  <br/> |outlook.office365.com  <br/> smtp.office365.com  <br/> |
|\*。 outlook.com  <br/> |\*。 protection.outlook.com  <br/> \*。 mail.protection.outlook.com  <br/> 自動探索-\<租用戶\>。 outlook.com  <br/> |
|\*。 windows.net  <br/> |login.windows.net  <br/> |

## <a name="routing-office-365-traffic-over-the-internet-and-expressroute"></a>透過網際網路與 ExpressRoute 路由的 Office 365 流量

若要傳送到 Office 365 選擇您的應用程式需要至判斷數個重要因素。
  
1. 應用程式需要多少頻寬。 取樣現有的使用方式是判斷這在您的組織中唯一可靠的方法。

2. 您想要的網路流量查看輸出位置保留網路。 您應該規劃連線至 Office 365 的網路延遲降至最低，因為這會影響效能。 商務用 Skype 會使用即時語音和視訊因為它受到特別不佳的網路延遲。

3. 如果您想要的所有或您要運用 ExpressRoute 的網路位置的子集。

4. 什麼位置您所選擇的網路提供者提供從 ExpressRoute。

一旦您判斷這些問題的答案，您可以佈建 ExpressRoute 線路可滿足頻寬和位置。 規劃協助更多的網路，請參閱[調整指南的 Office 365 網路](https://aka.ms/tune)和[案例研究上 Microsoft 控點網路效能規劃](https://aka.ms/tunemsit)。
  
### <a name="example-1-single-geographic-location"></a>範例 1： 單一地理位置
  
這則範例是對虛構公司名為 Trey Research 具有單一地理位置的案例。
  
在 Trey Research 的員工只能連線到服務及明確允許坐在公司網路和其 ISP 之間的輸出 proxy 配對的 「 安全性 」 部門的網際網路上的網站。
  
Trey Research 計劃使用 Azure ExpressRoute for Office 365，並會辨識某些流量，例如目的地內容傳遞網路流量將無法透過 Office 365 連線的 ExpressRoute 路由傳送。 因為所有已經流量預設的 proxy 裝置的路由，這些要求會繼續從前般運作。 Trey Research 決定他們可以符合 Azure ExpressRoute 路由需求之後，他們會繼續建立電路，請設定 [路由]，並將新的 ExpressRoute 線路連結至虛擬網路。 就地基礎 Azure ExpressRoute 設定之後，Trey Research 使用[#2 PAC 檔案我們發佈](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies)到路由傳送流量與客戶特定資料透過直接 ExpressRoute for Office 365 連線。
  
下圖所示，Trey Research 便能夠滿足需求透過網際網路和流量的子集合的 Office 365 流量路由傳送透過 ExpressRoute 路由和輸出 proxy 組態變更的組合。
  
1. 使用 Office 365 Azure ExpressRoute 路由傳輸透過不同的網際網路輸出點[我們發佈 #2 PAC 檔案](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies)。

2. 用戶端設定了預設的路由向 Trey Research 的 proxy。

在此範例案例中，Trey Research 使用輸出 proxy 裝置。 同樣地，不使用 Azure ExpressRoute for Office 365 的客戶可能會想要使用這項技術，以根據檢查已知的大量端點流量的成本的路由傳送流量。
  
適用於 Exchange Online、 SharePoint Online 和商務用 Skype Fqdn 的最大量如下所示：
  
![ExpressRoute 客戶邊緣網路](media/dab8cc42-b1d6-46d6-b2f6-d70f9e16d5ea.png)
  
- outlook.office365.com、 outlook.office.com

- \<租用戶名稱\>。.sharepoint.com，\<租用戶名稱\>-my.sharepoint.com，\<租用戶名稱\>-\<app\>。 sharepoint.com

- \*.Lync.com 以及非 TCP 流量 IP 範圍

- \*broadcast.officeapps.live.com， \*excel.officeapps.live.com， \*onenote.officeapps.live.com， \*powerpoint.officeapps.live.com， \*view.officeapps.live.com， \*visio.officeapps.live.com， \*word edit.officeapps.live.com， \*word view.officeapps.live.com、 office.live.com

深入了解[部署及管理在 Windows 8 的 proxy 設定](https://blogs.technet.com/b/deploymentguys/archive/2013/05/08/windows-8-supporting-proxy-services-with-static-configurations-web-hosted-pac-files-and-domain-policy-configured-proxy.aspx)並[確保 Office 365 不 proxy 進行節流](https://blogs.technet.com/b/onthewire/archive/2014/03/28/ensuring-your-office-365-network-connection-isn-t-throttled-by-your-proxy.aspx)。
  
使用單一的 ExpressRoute 線路，沒有任何 Trey Research 的高可用性。 在事件會提供服務的 ExpressRoute 連線的邊緣裝置 Trey 的備援配對失敗，沒有容錯移轉至其他 ExpressRoute 線路。 在 [predicament 中，為容錯移轉至網際網路時，需要手動重新設定和新的 IP 位址，在某些情況下，這會使 Trey Research。 如果 Trey 想要新增的高可用性，最簡單的解決方案是為每個位置的其他 ExpressRoute 電路在新增及設定的電路主動/主動方式。
  
## <a name="routing-expressroute-for-office-365-with-multiple-locations"></a>Office 365 搭配多個位置的路由 ExpressRoute

最後一個案例中，透過 ExpressRoute 路由 Office 365 流量是更複雜的路由架構的基礎。 不論的位置數目、 continents 這些位置所在的數目、 數目 ExpressRoute 迴路等等，能夠將某些流量路由傳送至網際網路及一些流量透過 ExpressRoute 將會需要。
  
具有多個位置中多個地區的客戶必須回答的其他問題包括：
  
1. 您需要在每個位置 ExpressRoute 線路嗎？ 如果您正在使用商務用 Skype 或不在意 SharePoint Online 或 Exchange Online 的延遲敏感度，建議使用主動/主動 ExpressRoute 電路重複配對中每個位置。 Skype for Business 的媒體品質和網路連線能力指南如需詳細資訊，請參閱。

2. 如果 ExpressRoute 線路不在特定區域中，應該目的地是 Office 365 流量會路由傳送方式？

3. 在具有許多小型位置的網路的情況下的合併資料傳輸的慣用的方法為何？

每一種呈現唯一的挑戰，需要評估您自己的網路，以及由 Microsoft 提供的選項。

|**考量**|**若要評估的網路元件**|
|:-----|:-----|
|在多個位置的電路  <br/> |我們建議您至少要有兩個主動/主動方式設定的電路。  <br/> 成本、 延遲和頻寬需求必須與相比較。  <br/> 使用 BGP 路由成本、 PAC 檔案和 NAT 來管理使用多個電路路由。  <br/> |
|從沒有 ExpressRoute 線路位置路由  <br/> |我們建議輸出和 DNS 解析為接近起始的要求，Office 365 的人員。  <br/> DNS 轉寄可以用來允許遠端辦公室，找出適當的端點。  <br/> 遠端 office 的用戶端必須要有路由，以提供存取權 ExpressRoute 線路。  <br/> |
|小型辦公室彙總  <br/> |可用的頻寬和資料使用量應該仔細比較。  <br/> |

> [!NOTE]
> Microsoft 會透過網際網路偏好 ExpressRoute，如果路由是使用無論實體位置。
  
每個這些考慮事項必須納入考量的每個唯一的網路。 以下是範例。
  
### <a name="example-2-multi-geographic-locations"></a>範例 2： 多地理位置
  
這則範例是對虛構公司呼叫大保險具有多個地理位置的案例。
  
大保險地理世界各地辦公室。 他們想要實作 Azure ExpressRoute for Office 365 來保留其 Office 365 流量大部分直接的網路連線。 大保險也有兩個其他 continents 辦公室。 ExpressRoute 不可行的情況下的遠端辦公室中的員工將需要回復至一或兩個主要的設施，以使用 ExpressRoute 連線路由傳送。
  
指導原則是要儘速取得 Microsoft 資料中心的目的地是 Office 365 流量。 在這個範例中，大保險必須決定其遠端辦公室是否應透過前往 Microsoft 資料中心透過任何連線好] 或 [如果其遠端辦公室應透過內部網路，以取得 microsoft 路由快速網際網路路由透過 ExpressRoute 連線的資料中心盡快。
  
Microsoft 的資料中心、 網路和應用程式的架構設計全域全數通訊並加以服務以最有效率的方式。 這是下列其中一個領域中的最大網路。 目的地是 Office 365 保持在超過所需的客戶網路的要求無法利用這種架構。
  
在大保險的情況下，他們應該前進根據他們想要使用透過 ExpressRoute 的應用程式。 例如，如果他們是商務用 Skype Online 客戶，或利用 ExpressRoute 連線，連線至外部商務用 Skype 商務線上會議，建議您在 Skype for Business Online 媒體品質和網路中的設計時計劃連線指南是佈建額外 ExpressRoute 線路的第三個位置。 這可能是較為昂貴從網路的觀點;不過，路由傳送要求從一個大陸至另一個之前傳遞到 Microsoft 資料中心可能會造成不佳或無法使用經驗期間 Skype 商務線上會議和通訊。
  
如果大保險未使用或不計劃要運用 Skype for Business Online 以任何方式，回到大陸使用 ExpressRoute 連線可能是路由目的地是 Office 365 的網路流量可行的情況下雖然可能會造成不必要的延遲或 TCP壅塞。 在這兩種情況下，建議使用預定在本機站台中網際網路流量，可利用內容傳遞網路的 Office 365 的路由網際網路依賴。
  
![ExpressRoute 多地理位置](media/98fdd883-2c5a-4df7-844b-bd28cd0b9f50.png)
  
大保險規劃其多地理位置的策略時, 有許多事項周圍的電路、 迴路容錯移轉，數目大小，請考慮等等。
  
使用 ExpressRoute 與嘗試使用電路的多個區域在單一位置，大保險想要確定連線到 Office 365 從遠端辦公室已傳送至最接近的總部在 Office 365 資料中心，並由接收總部位置。 若要這麼做，大保險實作 DNS 轉寄功能，以減少來回行程及建立適當的連線與總部網際網路輸出點最接近的 Office 365 環境所需的 DNS 查閱的數目。 這解決本機前端伺服器時，防止用戶端，並確保人員連接至前端伺服器是大保險外面與 Microsoft 總部附近。 您也可以了解如何[指派條件轉寄站的網域名稱](https://technet.microsoft.com/library/Cc794735%28v=WS.10%29.aspx)。
  
在此案例中，從遠端辦公室的流量會解析 「 北美地區 」 中的 Office 365 前端基礎結構，並利用 Office 365 連線到 Office 365 應用程式的架構根據的後端伺服器。 例如，Exchange Online 會終止 「 北美地區 」 中的連線，而這些前端伺服器會連線至後端的 mailbox server，儘租用戶常駐。 所有服務都組成單點傳播與任何傳播目的地廣泛分散式的前哨服務。
  
如果 Humongous 上有多個 continents 主要辦公室，建議使用最少的每個地區的兩個主動/主動電路以減少延遲機密的應用程式例如 Skype for Business Online。 如果所有辦公室都位於單一的大陸，或不使用即時共同作業，需要指向合併或分散式輸出為客戶特定決策。 當多個電路可用時，BGP 路由可確保容錯移轉任何單一電路變成無法使用。
  
深入了解範例[路由組態](https://azure.microsoft.com/documentation/articles/expressroute-config-samples-routing/)和[https://azure.microsoft.com/en-us/documentation/articles/expressroute-config-samples-nat/](https://azure.microsoft.com/documentation/articles/expressroute-config-samples-nat/)。
  
## <a name="selective-routing-with-expressroute"></a>選擇性使用 ExpressRoute 路由

使用 ExpressRoute 的選擇性路由所需的各種不同的原因，例如測試，推行 ExpressRoute 至使用者的子集。 有各種工具客戶可選擇性地將 Office 365 的網路流量透過 ExpressRoute 路由傳送：
  
1. **篩選路由責任/分隔**-透過 ExpressRoute 允許 BGP 路由至 Office 365 為您的子網路或路由器的子集。 這選擇性地路由傳送客戶網路區段或實體的辦公室位置。 這是很常見的 ExpressRoute for Office 365 錯開導入，且已設定 BGP 裝置上。

2. **PAC 檔案/Url** -將導向 Office 365 目的地是特定的 Fqdn，若要在特定路徑路由傳送的網路流量。 這選擇性地路由傳送用戶端電腦所識別的[PAC 檔案部署](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies)。

3. **路由篩選** - [路由篩選器](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal)是一種方法會耗用透過 Microsoft 對等的支援服務的子集。

4. **BGP 社群**-篩選根據[BGP 社群標記](https://aka.ms/bgpexpressroute365)可讓客戶判斷哪些 Office 365 應用程式會周遊 ExpressRoute，這會周遊網際網路。

您可以使用下列短連結返回這裡：[https://aka.ms/erorouting](https://aka.ms/erorouting)
  
## <a name="related-topics"></a>相關主題

[評估 Office 365 網路連線](assessing-network-connectivity.md)
  
[Azure ExpressRoute for Office 365](azure-expressroute.md)
  
[管理 ExpressRoute for Office 365 連線](managing-expressroute-for-connectivity.md)
  
[使用 ExpressRoute for Office 365 進行網路規劃](network-planning-with-expressroute.md)
  
[實作 ExpressRoute for Office 365](implementing-expressroute.md)
  
[商務用 Skype Online 中的媒體品質和網路連線效能](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917) (英文)
  
[針對商務用 Skype Online 最佳化您的網路](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43) (英文)
  
[ExpressRoute 與 QoS skype for Business Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[使用 ExpressRoute 的通話流程](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[使用 BGP 社群中 ExpressRoute for Office 365 案例](bgp-communities-in-expressroute.md)
  
[使用基準與效能歷程記錄進行 Office 365 效能調整](performance-tuning-using-baselines-and-history.md)
  
[Office 365 的效能疑難排解規劃](performance-troubleshooting-plan.md)
  
[Office 365 URL 與 IP 位址範圍](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) (英文)
  
[Office 365 網路與效能調整](network-planning-and-performance.md)
