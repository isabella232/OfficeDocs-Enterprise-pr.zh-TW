---
title: 使用 Office 365 案例 ExpressRoute BGP 社群 （英文）
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/26/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099
description: 連線至 Office 365 使用 Azure ExpressRoute 根據 BGP 廣告的特定代表的網路之部署 Office 365 端點的 IP 子網路。Office 365 及構成 Office 365 服務的號碼的全域性質，因為客戶通常有管理它們接受其網路廣告需要。減少 IP 子網路; 數目稱為 IP 首碼整個本文，以符合的 BGP 網路管理術語的其餘部分中做的客戶端下列目標：
ms.openlocfilehash: c6e40dc29df55aa87e8d40c6203100fa1e7ad38f
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539952"
---
# <a name="using-bgp-communities-in-expressroute-for-office-365-scenarios"></a>使用 Office 365 案例 ExpressRoute BGP 社群 （英文）

連線至 Office 365 使用 Azure ExpressRoute 根據 BGP 廣告的特定代表的網路之部署 Office 365 端點的 IP 子網路。Office 365 及構成 Office 365 服務的號碼的全域性質，因為客戶通常有管理它們接受其網路廣告需要。減少 IP 子網路; 數目稱為 IP 首碼整個本文，以符合的 BGP 網路管理術語的其餘部分中做的客戶端下列目標：
  
- **管理電話公告所接受的 IP 首碼**-內部網路基礎結構或僅支援 IP 前置字元數目有限的網路電信業者的客戶與具有網路電訊廠商該收費接受前置詞的客戶上面的有限的數字會想要評估的前置詞已對其網路通告總數然後選取 [哪些 Office 365 應用程式是適合 ExpressRoute。

- **管理的 Azure ExpressRoute 電路上所需的頻寬量**-客戶可能會想要控制 ExpressRoute 路徑與網際網路路徑比較 Office 365 服務頻寬信封。這可讓客戶齊備等 Skype 適用於企業的特定應用程式的 ExpressRoute 頻寬和透過網際網路路徑來路由其餘的 Office 365 應用程式。

若要協助客戶這些目標，透過 ExpressRoute 通告的 Office 365 IP 前置詞標示服務特定 BGP 社群值如以下範例所示。
  
> [!NOTE]
> 您應可預期一些要包含在社群值中的其他應用程式相關聯的網路流量。這是通用軟體的預期的行為以提供資料中心的共用的服務與服務。請儘可能使用上述兩個目標、 管理前置字元計數和/或頻寬記住，這有已最小化。

|**服務**|**BGP 社群值**|**附註**|
|:-----|:-----|:-----|
|exchange\*  <br/> |12076:5010  <br/> |包含 Exchange 和 EOP 服務\*  <br/> |
|sharepoint\*  <br/> |12076:5020  <br/> |SharePoint Online  <br/> |
|skype 企業版\*  <br/> |12076:5030  <br/> |商務用 Skype Online  <br/> |
|其他 Office 365 服務\*  <br/> |12076:5100  <br/> |包含 Office 365 入口網站服務以及 Azure Active Directory （驗證和目錄同步處理案例）  <br/> |
|\*包含在 ExpressRoute 服務案例的範圍所記載的[Office 365 端點](https://aka.ms/o365endpoints)文章。  <br/> \*\*可能未來新增其他服務和 BGP 社群值。[請參閱目前 BGP 社群 （英文） 的清單](https://azure.microsoft.com/documentation/articles/expressroute-routing/)。<br/> |

## <a name="what-are-the-most-common-scenarios-for-using-bgp-communities"></a>最常見的案例使用 BGP 社群有哪些？

客戶可能會使用 BGP 社群 （英文） 來管理群組的其網路進行 Azure ExpressRoute，因此影響的前置字元總數 IP 與預期的頻寬信封的特定 Office 365 服務可接受的 IP 前置字元。請務必了解所有 Office 365 作業都需要網際網路繫結不論使用 Azure ExpressRoute 或 BGP 社群的流量。下列三種案例是最常見的這項功能。
  
### <a name="scenario-1-minimizing-the-number-of-office-365-ip-prefixes"></a>案例 1： 最小化 Office 365 IP 前置字元的數

Contoso Corporation 為目前使用的 Exchange Online 與 SharePoint Online 的 Office 365 50000 人員公司。檢閱 ExpressRoute 需求 Contoso 會決定在許多區域性位置其網路裝置無法處理 100 個額外的路由項目上方的路由表格大小。Contoso 檢閱 ExpressRoute 就 advertise for Office 365 服務的完整且做出定案超過 100 IP 前置字元總數。若要保持下的 100 其他路由項目，Contoso 範圍使用 ExpressRoute 為 Office 365 剛的 SharePoint Online BGP 社群值、 12076:5020、 接收透過 ExpressRoute Microsoft 對等。

|**使用 BGP 社群標記**|**透過 Azure ExpressRoute 路由傳送的功能**|**所需的網際網路路由**|
|:-----|:-----|:-----|
|SharePoint  <br/> (12076:5020)  <br/> |SharePoint Online &amp; OneDrive for Business  <br/> | DNS、 CRL、 &amp; CDN 要求  <br/>  未特別透過 Azure ExpressRoute 支援所有其他 Office 365 服務  <br/>  所有其他 Microsoft 雲端服務  <br/>  Office 365 入口網站、 Office 365 驗證&amp;Office Online  <br/>  Exchange Online、 Exchange Online Protection 和 Skype for Business 線上  <br/> |

> [!NOTE]
> 若要達到每個服務的較低前置字元計數，將保存服務之間的重疊最少數量。此為預期的行為。
  
### <a name="scenario-2-scoping-expressroute-and-internal-bandwidth-use-to-some-office-365-services"></a>案例 2： 範圍 ExpressRoute 和內部的頻寬使用某些 Office 365 服務

Fabrikam Inc、 分散式異質網路大型多重國民 enterprise 會包括; 許多 Office 365 服務的訂閱者Exchange Online、 SharePoint Online、 和 Skype Online 企業版。Fabrikam 的內部路由基礎結構可以處理數千個 IP 首碼的其路由表;不過，Fabrikam 只想要佈建 ExpressRoute 和寫網路效能及使用其現有的網際網路頻寬的所有其他 Office 365 應用程式的 Office 365 應用程式的內部頻寬。
  
有該原因 Fabrikam 範圍只 Skype 商務 Online BGP 社群值、 12076:5030，透過 ExpressRoute Microsoft 對等接收其 Azure ExpressRoute 頻寬。Office 365 相關聯的其餘網路流量會繼續使用網際網路的輸出點。

|**使用 BGP 社群標記**|**透過 Azure ExpressRoute 路由傳送的功能**|**所需的網際網路路由**|
|:-----|:-----|:-----|
|商務用 Skype  <br/> (12076:5030)  <br/> |Skype SIP 訊號、 下載、 語音、 視訊和桌面共用  <br/> | DNS、 CRL、 &amp; CDN 要求  <br/>  未特別透過 Azure ExpressRoute 支援所有其他 Office 365 服務  <br/>  所有其他 Microsoft 雲端服務  <br/>  Office 365 入口網站、 Office 365 驗證&amp;Office Online  <br/>  Skype 商務遙測、 Skype 用戶端瀏覽的秘訣、 公用 IM 連線  <br/>  Exchange Online、 Exchange Online Protection 和 SharePoint Online  <br/> |

### <a name="scenario-3-scoping-azure-expressroute-for-office-365-services-only"></a>案例 3： 設定 Azure ExpressRoute 範圍只 Office 365 服務

Woodgrove Bank 是數個 Microsoft 雲端服務包括 Office 365 的客戶。之後評估其網路容量與耗用 Woodgrove Bank 決定部署 Azure ExpressRoute 為受支援的 Office 365 服務的慣用路徑。路由表可支援完整的 Office 365 IP 前置詞與他們已佈建 Azure ExpressRoute 電路支援所有的預計的頻寬和延遲需求。
  
若要確保比其他 Office 365、 Woodgrove Bank 範圍 ExpressRoute 可 for Office 365 使用所有 IP 前置字元與 Microsoft 雲端服務相關聯的網路流量已標記與 Office 365 特定 BGP 社群值、 12076:5010、 12076:5020、 12076:5030、12076:5100。

|**使用 BGP 社群標記**|**透過 Azure ExpressRoute 路由傳送的功能**|**所需的網際網路路由**|
|:-----|:-----|:-----|
|Exchange、 for Business、 SharePoint、 Skype&amp;其他服務  <br/> （12076:5010、 12076:5020、 12076:5030、 12076:5100）  <br/> |Exchange Online &amp; Exchange Online Protection  <br/> SharePoint Online &amp; OneDrive for Business  <br/> Skype SIP 訊號、 下載、 語音、 視訊和桌面共用  <br/> Office 365 入口網站、 Office 365 驗證&amp;Office Online  <br/> | DNS、 CRL、 &amp; CDN 要求  <br/>  未特別透過 Azure ExpressRoute 支援所有其他 Office 365 服務  <br/>  所有其他 Microsoft 雲端服務  <br/> |

## <a name="key-planning-considerations-to-using-bgp-communities"></a>重要的規劃考量使用 BGP 社群 （英文）

選擇以充分運用影響方式 ExpressRoute 通告且傳播到客戶網路 BGP 社群的客戶應該採取下列事項：
  
- 請務必確定在網路設計中使用 BGP 社群 （英文） 時仍會維護路由對稱性來看。在某些情況下，新增或移除 BGP 社群可能會造成其中對稱路由會中斷並重新建立對稱路由必須更新您的路由組態的狀況。

- 設定 Azure ExpressRoute 範圍 BGP 社群值是客戶巨集指令。Microsoft 會通知所有 IP 前置字元相關都聯的對等關係不論由客戶設定任何範圍。

- Azure ExpressRoute 不支援客戶指派 BGP 社群 （英文） 為基礎的 Microsoft 的網路上的任何動作。

- Office 365are 所使用的 IP 前置詞只會標示服務特定 BGP 社群值、 特定 BGP 社群不受支援的位置。Office 365 服務都通用的性質，篩選根據位置的租用戶的前置字元或不支援的 Office 365 雲端內的資料。建議的方法是設定您的網路協調最短或從使用者的網路位置，將 Microsoft 通用網路不論 Office 365 服務的 IP 位址的實體位置最慣用的網路路徑他們要求。

- 包含在每個 BGP 社群值的 IP 前置詞表示包含值相關聯的 Office 365 應用程式的 IP 位址的子網路。在某些情況下，多個 Office 365 應用程式都有一個以上的社群值中現有的 IP 前置字中所產生的子網路內的 IP 位址。這是預期，但是很少，因為配置分散情形的行為，不會影響前置字元計數或頻寬管理目標。客戶是建議使用 [允許需要什麼] 而非"拒絕項目，則不需要"方法時善加利用 BGP 社群的影響降到 Office 365。

- 使用 BGP 社群 （英文） 不會變更基礎的網路連線需求或使用 Office 365 所需的設定。要存取 Office 365 的客戶所列仍能存取網際網路。

- 設定 Azure ExpressRoute 範圍與 BGP 社群 （英文） 只會影響內部網路可以看到透過 Microsoft 對等關係的路由。您可能需要進行其他應用程式層級的設定等使用 PAC 或 WPAD 設定搭配範圍的路由。

- 除了使用 Microsoft 指派 BGP 社群，客戶可以選擇將自己 BGP 社群 （英文） 指派給透過影響內部路由的 Azure ExpressRoute 學到的 Office 365 IP 前置詞。熱門的使用案例將位置型 BGP 社群指派給每個對等位置，然後在協調最短的客戶網路中使用該資訊傳輸的特定 ExpressRoute 透過學到的所有路由或最慣用的網路路徑到Microsoft 的網路。使用指派 BGP 社群 （英文） ExpressRoute 與 Office 365 案例是客戶的 Microsoft 控制項或可見性的範圍外。

以下是您可以使用回來的簡短連結： [https://aka.ms/bgpexpressroute365](https://aka.ms/bgpexpressroute365)。
  
## <a name="related-topics"></a>相關主題

[對 Office 365 的網路連線](network-connectivity.md)
  
[Azure ExpressRoute for Office 365](azure-expressroute.md)
  
[管理 ExpressRoute for Office 365 連線](managing-expressroute-for-connectivity.md)
  
[使用 ExpressRoute for Office 365 進行路由傳送](routing-with-expressroute.md)
  
[使用 ExpressRoute for Office 365 進行網路規劃](network-planning-with-expressroute.md)
  
[媒體品質和 Skype 的線上商務的網路連線效能](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[ExpressRoute 和 Skype Online 企業版的 QoS](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[使用 ExpressRoute 通話流程](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[實作 ExpressRoute for Office 365](implementing-expressroute.md)
  
[支援 BGP 社群 （英文）](https://azure.microsoft.com/documentation/articles/expressroute-routing/)
  
[使用基準與效能歷程記錄進行 Office 365 效能調整](performance-tuning-using-baselines-and-history.md)
  
[Office 365 的效能疑難排解規劃](performance-troubleshooting-plan.md)
  
[Azure ExpressRoute for Office 365 訓練](https://channel9.msdn.com/series/aer)
