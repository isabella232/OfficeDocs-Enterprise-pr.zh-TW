---
title: 使用 ExpressRoute for Office 365 進行路由傳送
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/14/2017
ms.audience: ITPro
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
description: 正確了解 Office 365 使用 Azure ExpressRoute 路由流量，您將需要公司掌握核心 ExpressRoute 路由需求及 ExpressRoute 電路和路由的網域。使用 Office 365 客戶會依賴的 ExpressRoute 基礎版面配置這些設定。
ms.openlocfilehash: d8fa0c606a5aedd3760236cb46bcf9e1c584ecb8
ms.sourcegitcommit: d165aef59fe9a9ef538e6756fb014909a7cf975b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2018
ms.locfileid: "27294473"
---
# <a name="routing-with-expressroute-for-office-365"></a>使用 ExpressRoute for Office 365 進行路由傳送

正確了解 Office 365 使用 Azure ExpressRoute 路由流量，您將需要公司掌握核心[ExpressRoute 路由需求](https://azure.microsoft.com/documentation/articles/expressroute-routing/)及[ExpressRoute 電路和路由的網域](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/)。使用 Office 365 客戶會依賴的 ExpressRoute 基礎版面配置這些設定。
  
一些您需要了解上述文章中的重要項目包括：
  
- ExpressRoute 電路未對應至特定實體的基礎結構，但都位於單一的對等位置進行 Microsoft 和您的對等提供者的邏輯連接。

- 沒有 ExpressRoute 電路與客戶的鍵 1:1 對應。

- 每個電路可支援最多 3 個獨立的對等關係 （Azure 公用對等、 Azure 私人對等和 Microsoft 對等）;Office 365 需要 Microsoft 對等。

- 每個電路具有共用跨所有對等關係固定的頻寬。

- 任何公用 IPv4 位址與公用為將使用的數字 ExpressRoute 為基礎的電路必須是驗證做為其擁有者，或擁有者的地址範圍指派給您以獨佔方式。

- 虛擬 ExpressRoute 電路全域為備援，而且會遵循標準的 BGP 路由的作法。這就是為什麼我們建議每個輸出的兩個實體電路至主動/主動設定中提供者。

請參閱[FAQ 頁面](https://azure.microsoft.com/documentation/articles/expressroute-faqs/)更多資訊在支援的服務、 成本、 及設定的詳細資訊。請參閱[ExpressRoute 位置文章](https://azure.microsoft.com/documentation/articles/expressroute-locations/)以改善資訊提供 Microsoft 對等支援的連線提供者清單。我們也已記錄 10 組件[的 Office 365 訓練 Azure ExpressRoute](https://channel9.msdn.com/series/aer)數列 Channel 9 以協助先徹底更多說明的概念。
  
## <a name="ensuring-route-symmetry"></a>確保路由對稱性來看

Office 365 前端伺服器可存取網際網路和 ExpressRoute 上。這些伺服器將偏好時二者都可透過 ExpressRoute 電路路由。基於此因素沒有路由為中心不對稱的可能性如果從您的網路流量偏好透過網際網路電路路由傳送。因為執行設定狀態的封包檢查裝置可封鎖接後面的輸出封包不同的路徑傳回流量對稱的路由都是發生問題。
  
不論是否透過網際網路或 ExpressRoute 初始 Office 365 的連線、 來源必須是可公開路由傳送的地址。與對等直接與 Microsoft 的許多客戶、 具有私人位址重複所在之間客戶可能不是合適。
  
以下為的案例將起始通訊來自 Office 365 的內部網路的位置。若要簡化您的網路設計、 建議路由這些透過網際網路路徑。
  
- 例如信箱從 Exchange Online 租用戶至內部部署主機或從 SharePoint Online 傳送至內部部署主機的 SharePoint Online 郵件的 SMTP 服務。比透過 ExpressRoute 電路共用的路由前置詞和廣告內部 SMTP 伺服器透過 ExpressRoute 會導致失敗與這些其他服務 SMTP 通訊協定就會更廣泛使用 Microsoft 的網路內。

- 在 [密碼驗證登入期間 ADFS。

- [Exchange Server 混合式部署](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx)。

- [ [SharePoint 同盟混合式搜尋](https://technet.microsoft.com/library/dn197174.aspx)]。

- [SharePoint 混合式 BCS](https://technet.microsoft.com/library/dn197239.aspx )。

- [用於商業的混合式 Skype](https://technet.microsoft.com/en-us/library/jj205403.aspx)和/或[Skype 商務同盟](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx)。

- [Skype Business Cloud 連接器](https://technet.microsoft.com/library/mt605227.aspx )。

針對 Microsoft 路由傳送回至您的網路之這些雙向流量流程、 BGP 路由至內部部署裝置必須與 Microsoft 共用。當您透過 ExpressRoute advertise 路由傳送給 Microsoft 的前置詞時，您應該遵循這些最佳作法：

1) 未通告相同公用 IP 位址路由的前置詞至公用網際網路和透過 ExpressRoute。強烈建議 IP BGP 路由首碼廣告 ExpressRoute 透過 microsoft 是來自未通告網際網路所有的範圍。如果這是不可能達到因為可用的 IP 位址空間，最好是確定透過 ExpressRoute advertise 比任何網際網路電路更多特定範圍的基本。

2) 使用個別 ExpressRoute 電路分開的 NAT IP 集區和個別的網際網路電路。

3) 請注意對 Microsoft 通告任何路由會吸引來自 Microsoft 的網路，不只以外的路由會對您的網路通告透過 ExpressRoute 中任何伺服器的網路流量。僅限 advertise 的伺服器路由案例所定義及了解您的小組所其中的路由。Advertise 每一層的多個 ExpressRoute 電路從您網路的不同 IP 位址路由前置詞。 
  
## <a name="deciding-which-applications-and-features-route-over-expressroute"></a>決定哪些應用程式和功能透過 ExpressRoute 路由

當您設定使用 Microsoft 的對等路由網域的對等關聯並核准的適當的存取權時，您將能夠透過 ExpressRoute 看到可用的所有 PaaS 和 saas 和服務。設計 ExpressRoute Office 365 服務可管理與[BGP 社群 （英文）](https://aka.ms/bgpexpressroute365)或[路由篩選器](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal)。
  
Office 365 視訊、 其他應用程式是 Office 365 應用程式。不過，Office 365 影片 」 包含下列三個不同的元件、 入口網站、 資料流及內容傳遞網路。儲存在 SharePoint Online、 Azure 媒體服務內的資料流服務生活的入口網站及內容傳遞網路都位於 Azure CDN 內。下表概述這些元件。
  
| |
|**元件**|**基礎的應用程式**|**包含在 SharePoint Online BGP 社群吗？**|**使用**|
|:-----|:-----|:-----|:-----|
|Office 365 影片入口網站  <br/> |SharePoint Online  <br/> |是  <br/> |設定、 上傳  <br/> |
|Office 365 視訊資料流服務  <br/> |Azure 媒體服務  <br/> |否  <br/> |串流影片則無法使用從 CDN 可行所使用的服務  <br/> |
|Office 365 視訊內容傳遞網路  <br/> |Azure CDN  <br/> |否  <br/> |主要的影片下載/資料流的來源。[解更多關於 Office 365 影片網路](https://support.office.com/article/Office-365-Video-networking-Frequently-Asked-Questions-FAQ-2bed67a1-4052-49ff-a4ce-b7e6530eb98e)。<br/> |

每個可使用對等 Microsoft Office 365 功能會列在[Office 365 端點本文](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)依應用程式類型和 FQDN。在表格中使用 FQDN 的原因是可以讓客戶能夠管理流量使用 PAC 檔案或其他 proxy 設定，請參閱[管理 Office 365 端點](https://aka.ms/manageo365endpoints)例如 PAC 檔案我們指南。
  
在某些情況下我們使用不同的較高的層級的萬用字元網域通告一或多個 sub Fqdn 是萬用字元網域。這通常是由於萬用字元代表過長的所有通告 ExpressRoute 及網際網路時目的地小型子集只通告網際網路或反向的伺服器清單時所發生的情況。請參閱從而了解差異所在位置的表格。
  
下表顯示萬用字元已通告的 Fqdn 網際網路和 Azure ExpressRoute 旁通告僅到網際網路 sub Fqdn。

|**對 ExpressRoute 和網際網路電路通告萬用字元網域**|**Sub FQDN 對網際網路電路只通告**|
|:-----|:-----|
|\*。 microsoftonline.com  <br/> |click.email.microsoftonline.com  <br/> portal.microsoftonline.com  <br/> provisioningapi.microsoftonline.com  <br/> adminwebservice.microsoftonline.com  <br/> |
|\*。 officeapps.live.com  <br/> |nexusRules.officeapps.live.com  <br/> nexus.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> cdn.odc.officeapps.live.com  <br/> ols.officeapps.live.com  <br/> ocsredir.officeapps.live.com  <br/> ocws.officeapps.live.com  <br/> ocsa.officeapps.live.com  <br/> |

通常是 PAC 檔案都是要將網路要求傳送至 ExpressRoute 通告直接以電路端點和所有其他網路要求至您的 proxy。如果您正在設定類似 PAC 檔案，撰寫下列順序您 PAC 檔案：
  
1. 在您傳送至您的 proxy 接近流量的 PAC 檔案頂端上述表格中包含兩欄從 sub Fqdn。我們已建立您可以使用有關[管理 Office 365 端點](https://aka.ms/manageexpressroute365)我們文章中的範例 PAC 檔案。

2. 包含所有 Fqdn 標示公告 ExpressRoute 至第一個區段中下, 面[這篇文章](https://aka.ms/o365endpoints)中所將流量傳送至 ExpressRoute 電路直接。

3. 包含任何其他網路端點或傳送至您的 proxy 接近流量下列兩個項目下方的規則。

下表會顯示已通告的萬用字元網域僅附加至 Azure ExpressRoute 通告 sub Fqdn 上的網際網路電路及網際網路電路。上述兩欄中的 Fqdn 您 PAC 檔案下表列出做為對 ExpressRoute 中的連結參照，這表示會併入項目的檔案中的第二個群組所通告。

|**僅限網際網路電路對通告的萬用字元網域**|**對 ExpressRoute 和網際網路電路通告 sub FQDN**|
|:-----|:-----|
|\*。 office.com  <br/> |\*。 outlook.office.com  <br/> home.office.com  <br/> outlook.office.com  <br/> portal.office.com  <br/> www.office.com  <br/> |
|\*。 office.net  <br/> |agent.office.net  <br/> |
|\*。 office365.com  <br/> |outlook.office365.com  <br/> smtp.office365.com  <br/> |
|\*。 outlook.com  <br/> |\*。 protection.outlook.com  <br/> \*。 mail.protection.outlook.com  <br/> 自動探索-\<租用戶\>。 outlook.com  <br/> |
|\*。 windows.net  <br/> |login.windows.net  <br/> |

## <a name="routing-office-365-traffic-over-the-internet-and-expressroute"></a>透過網際網路和 ExpressRoute 路由的 Office 365 流量

若要路由傳送至 Office 365 您選擇的應用程式需要決定數目時的關鍵因素。
  
1. 應用程式需要多少頻寬。取樣現有的使用方式是判斷這在組織中僅可靠的方法。

2. 您想要的網路流量何種輸出位置保留從網路。您應該規劃這將會對效能的影響為連線至 Office 365 的網路延遲降至最低。因為 for Business Skype 使用即時語音和視訊它是特別容易受到不佳的網路延遲的影響。

3. 如果您想要的所有或運用 ExpressRoute 您網路位置的子集。

4. 什麼位置您所選擇的網路提供者提供從 ExpressRoute。

一旦您決定這些問題的答案，您可以佈建 ExpressRoute 電路符合頻寬和位置需求。多個網路規劃協助，請參閱[Office 365 網路調校指南](https://aka.ms/tune)和[案例研究上 Microsoft 控點網路效能規劃](https://aka.ms/tunemsit)。
  
### <a name="example-1-single-geographic-location"></a>範例 1： 單一地理位置
  
這個範例是對虛構公司呼叫 Trey Research 具有單一地理位置的案例。
  
在 Trey Research 員工只允許連線至服務和明確允許位於公司網路和其 ISP 之間的輸出 proxy 一組的 「 安全性 」 部門的網際網路上的網站。
  
Trey Research 計劃 Office 365 使用 Azure ExpressRoute 及可辨識一些例如目的地內容傳遞網路流量的流量不會能夠透過 Office 365 連線 ExpressRoute 路由傳送。由於所有已經流量預設的 proxy 裝置的路由，這些要求會繼續運作以之前。Trey Research 決定他們可以符合 Azure ExpressRoute 路由需求之後，他們會繼續建立電路、 設定路由]，並將新的 ExpressRoute 電路連結至虛擬網路。後之基礎的 Azure ExpressRoute 組態備妥，Trey Research 使用[#2 PAC 檔案我們發佈](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies)到路由流量客戶特定資料透過直接 ExpressRoute for Office 365 的連線。
  
下圖所示，Trey Research 能夠滿足，才可透過網際網路與流量的子集的 Office 365 流量路由傳送透過 ExpressRoute 使用路由和輸出 proxy 組態變更的組合。
  
1. 使用[我們發佈 #2 PAC 檔案](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies)到不同的網際網路輸出點路由流量進行 Azure ExpressRoute for Office 365。

2. 預設路由至 Trey Research proxy 接近來設定用戶端。

此範例案例 Trey Research 使用輸出 proxy 裝置。同樣地，不使用 Azure ExpressRoute for Office 365 的客戶可能會想要使用此技巧根據成本檢查已知的大量端點目的地的流量路由流量。
  
最高數量適用於 Exchange Online、 SharePoint Online 和 Skype 商務 Online 的 Fqdn 如下所示：
  
![ExpressRoute 客戶邊緣網路](media/dab8cc42-b1d6-46d6-b2f6-d70f9e16d5ea.png)
  
- outlook.office365.com、 outlook.office.com

- \<租用戶名稱\>。 sharepoint.com、\<租用戶名稱\>-my.sharepoint.com、\<租用戶名稱\>-\<app\>。 sharepoint.com

- \*.建立與 Lync.com 以及非 TCP 流量的 IP 範圍

- \*broadcast.officeapps.live.com、 \*excel.officeapps.live.com、 \*onenote.officeapps.live.com、 \*powerpoint.officeapps.live.com、 \*view.officeapps.live.com、 \*visio.officeapps.live.com、 \*word-edit.officeapps.live.com \*word view.officeapps.live.com、 office.live.com

深入了解及[部署及管理在 Windows 8 的 proxy 設定](https://blogs.technet.com/b/deploymentguys/archive/2013/05/08/windows-8-supporting-proxy-services-with-static-configurations-web-hosted-pac-files-and-domain-policy-configured-proxy.aspx)[確認 Office 365 不會由節流處理您的 proxy](https://blogs.technet.com/b/onthewire/archive/2014/03/28/ensuring-your-office-365-network-connection-isn-t-throttled-by-your-proxy.aspx)。
  
使用單一的 ExpressRoute 電路、 有 Trey Research 沒有高可用性。事件中所服務的 ExpressRoute 連線的邊緣裝置 Trey 的備援一對失敗，是不容錯移轉至其他 ExpressRoute 電路。當容錯移轉至網際網路需要手動重新設定與新的 IP 位址在某些情況下，這使得處於 predicament Trey Research。如果 Trey 想要新增高可用性，最簡單的解決方案是針對每個位置的其他 ExpressRoute 電路中新增及設定電路主動/主動的方式。
  
## <a name="routing-expressroute-for-office-365-with-multiple-locations"></a>Office 365 搭配多個位置的路由 ExpressRoute

過去的案例中，Office 365 的流量路由透過 ExpressRoute 是更為複雜的路由架構基礎。不論位置數目、 continents 在這些位置存在的數目、 數目 ExpressRoute 電路等等，能夠一些將流量路由傳送網際網路和一些流量透過 ExpressRoute 各自需要。
  
必須接聽以具有多個地理位置中的多個位置的客戶的其他問題包括：
  
1. 您是否需要在每個位置 ExpressRoute 電路吗？如果您正在使用 Skype 商務 Online 或擔心使用 SharePoint Online 或 Exchange Online 的延遲敏感度、 備援兩個主動/主動 ExpressRoute 電路建議每個位置中。請參閱 Skype for Business 媒體品質] 及 [網路連線指南如需詳細資訊。

2. 如果 ExpressRoute 電路不在特定的區域中，如何應目的地的 Office 365 流量會路由傳送？

3. 什麼是合併但如果是具有許多小型位置的網路流量的慣用的方法？

這每一項呈現唯一的挑戰要求您用來評估您自己的網路為 Microsoft 提供的選項。

|**考量**|**用來評估網路元件**|
|:-----|:-----|
|在多個位置的電路  <br/> |建議您至少要有兩個電路主動/主動方式設定。  <br/> 必須比較成本、 延遲和頻寬的需求。  <br/> 用於管理使用多個電路路由 BGP 路由成本、 PAC 檔案及 NAT。  <br/> |
|從位置而 ExpressRoute 電路路由  <br/> |我們建議輸出和 DNS 解析為接近初始化之要求的 Office 365 的人員。  <br/> DNS 轉寄可以用來允許遠端辦公室探索適當的端點。  <br/> 遠端 office 的用戶端必須可提供存取權 ExpressRoute 電路路由。  <br/> |
|小型 office 彙總資料  <br/> |應謹慎比較可用頻寬和資料的使用方式。  <br/> |

> [!NOTE]
> Microsoft 會透過網際網路偏好 ExpressRoute，如果路由使用無論實體位置。
  
每個這些考慮事項必須納入為每個唯一的網路的帳戶。以下是範例。
  
### <a name="example-2-multi-geographic-locations"></a>範例 2： 多重地理位置
  
這個範例是對虛構公司呼叫大保險具有多個地理位置的案例。
  
大保險地理區隔與全球各地辦公室中。他們想要實作 Azure ExpressRoute for Office 365 保留其 Office 365 流量的多數 」 直接的網路連線。大保險也具有兩個額外 continents 辦公室。遠端 office ExpressRoute 不合適中的之員工將需要路由傳送回至一或兩個主要設施使用 ExpressRoute 連線。
  
指導原則是儘速取得 Office 365 目的地流量到 Microsoft 資料中心。在這個範例中，大保險必須決定其遠端辦公室是否應透過網際網路，以取得 Microsoft 資料中心任何連線為可能的] 或其遠端辦公室如果應透過供 Microsoft 內部網路路由快速路由透過 ExpressRoute 連線的資料中心盡快。
  
Microsoft 的資料中心、 網路和應用程式架構的設計被用進行全域不同的通訊，並加以服務可能最有效率的方式。這是一個世界中的最大網路。要求目的地 for Office 365 保持在超過所需的客戶網路將不能夠利用此架構。
  
在大保險的情況下，他們應該繼續根據他們想要使用 over ExpressRoute 應用程式。例如，如果它們是 for Business Skype Online 客戶，或連線至外部 Skype 商務線上會議中的商務線上媒體品質] 及 [網路 Skype 建議的設計時運用 ExpressRoute 連線計劃佈建的第三個位置其他 ExpressRoute 電路是連線指南 》。這可能會較昂貴觀點的網路;不過，要求路由傳送從一個大陸至另一個之前傳遞到 Microsoft 資料中心可能會造成不良或無法使用經驗期間 Skype 商務線上會議及通訊。
  
若大保險未使用或不計劃商務 online 運用 Skype 以任何方法，回到與連線可能是 ExpressRoute 大陸路由目的地的 Office 365 網路流量合適上述可能會導致不必要的延遲或 TCP壅塞。在這兩種情況下，路由到網際網路在本機站台的預定的流量建議以充分運用內容傳遞網路 Office 365 的網際網路依賴。
  
![ExpressRoute 多重地理位置](media/98fdd883-2c5a-4df7-844b-bd28cd0b9f50.png)
  
大保險規劃其多重地理策略時，有許多事項考慮周圍的電路、 電路、 容錯移轉的數目大小等等。
  
在單一位置與多個地區嘗試使用電路 ExpressRoute，以大保險想要確定連線至 Office 365 從遠端 office 已傳送至最接近的 headquarters 的 Office 365 資料中心並接收到headquarters 位置。若要這樣做，大保險實作 DNS 轉寄至減少的來回行程和建立適當的連線與 Office 365 環境 headquarters 網際網路輸出點至最接近所需的 DNS 查詢數目。這禁止用戶端解析本機前端伺服器並確保人員連線到前端伺服器是大保險外面與 Microsoft headquarters 附近。您也可以了解如何[指定設定格式化的條件轉寄站網域名稱](https://technet.microsoft.com/library/Cc794735%28v=WS.10%29.aspx)。
  
在此案例中，從遠端 office 流量嗎解析 「 北美地區 」 中的 Office 365 前端基礎結構，以及利用 Office 365 連線至 Office 365 應用程式的架構根據的後端伺服器。例如 Exchange Online 會終止 「 北美地區 」 中的連線和這些前端伺服器會連線至後端 mailbox server 儘租用戶位於。所有服務都廣泛分散式的前方門服務單點傳播和任何傳播目的地所組成。
  
如果 Humongous 中多個 continents 主要辦公室，以減少延遲等 Skype 機密應用程式的商務 Online 的建議每個地區的兩個主動/主動電路最少。如果所有的辦公室位於單一的大陸或未使用即時共同作業、 擁有指向合併或分散式輸出為客戶特定決策。有多個電路時，BGP 路由可確保容錯移轉應任何單一電路變成無法使用。
  
深入了解範例[路由組態](https://azure.microsoft.com/documentation/articles/expressroute-config-samples-routing/)和[https://azure.microsoft.com/en-us/documentation/articles/expressroute-config-samples-nat/](https://azure.microsoft.com/documentation/articles/expressroute-config-samples-nat/)。
  
## <a name="selective-routing-with-expressroute"></a>選擇性使用 ExpressRoute 路由

使用 ExpressRoute 選擇性路由可能需要的原因，例如測試各種 ExpressRoute 啟用之使用者的子集。有客戶可以使用選擇性的 Office 365 網路流量路由傳送 ExpressRoute 透過各種工具：
  
1. **篩選路由程度/隔離**-透過 ExpressRoute 允許 BGP 路由至 Office 365 的子網路或路由器的子集。這選擇性地將客戶的網路區段或實體的辦公室位置。這是常見的 Office 365 ExpressRoute 錯開導入，且已 BGP 裝置上。

2. **PAC 檔案/Url** -導向 Office 365 目的地特定的 Fqdn 來路由傳送的特定路徑上的網路流量。這選擇性地路由傳送的用戶端電腦為識別[PAC 檔案部署](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies)。

3. **路由篩選** - [路由篩選器](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal)是取用透過對等 Microsoft 支援服務的子集的方式。

4. **BGP 社群 （英文）** -篩選根據[BGP 社群標記](https://aka.ms/bgpexpressroute365)可讓客戶來判斷哪些 Office 365 應用程式會周遊 ExpressRoute 和其將周遊網際網路。

您可以使用下列短連結返回這裡：[https://aka.ms/erorouting](https://aka.ms/erorouting)
  
## <a name="related-topics"></a>相關主題

[對 Office 365 的網路連線](network-connectivity.md)
  
[Azure ExpressRoute for Office 365](azure-expressroute.md)
  
[管理 ExpressRoute for Office 365 連線](managing-expressroute-for-connectivity.md)
  
[使用 ExpressRoute for Office 365 進行網路規劃](network-planning-with-expressroute.md)
  
[實作 ExpressRoute for Office 365](implementing-expressroute.md)
  
[商務用 Skype Online 中的媒體品質和網路連線效能](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917) (英文)
  
[針對商務用 Skype Online 最佳化您的網路](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43) (英文)
  
[商務用 Skype Online 中的 ExpressRoute 與 QoS](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d) (英文)
  
[使用 ExpressRoute 的通話流程](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab) (英文)
  
[使用 Office 365 案例 ExpressRoute BGP 社群 （英文）](bgp-communities-in-expressroute.md)
  
[使用基準與效能歷程記錄進行 Office 365 效能調整](performance-tuning-using-baselines-and-history.md)
  
[Office 365 的效能疑難排解規劃](performance-troubleshooting-plan.md)
  
[Office 365 URL 與 IP 位址範圍](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) (英文)
  
[Office 365 網路與效能調整](network-planning-and-performance.md)
