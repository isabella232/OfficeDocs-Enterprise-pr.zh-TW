---
title: 使用 BGP 社群中 ExpressRoute for Office 365 案例
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/26/2018
audience: Admin
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
description: 連線至 Office 365 使用 Azure ExpressRoute 根據特定代表其中部署 Office 365 端點的網路的 IP 子網路的 BGP 廣告。 由於 Office 365 和構成 Office 365 服務數目的全域性質，客戶通常需要來管理他們接受其網路的廣告。 減少的 IP 子網路。稱為 IP 首碼整個本文，以配合 BGP 網路管理術語的其餘部分客戶做結尾下列目標：
ms.openlocfilehash: 2cce550aa4c14eb0de9daa6eac85cde6d1754add
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068179"
---
# <a name="using-bgp-communities-in-expressroute-for-office-365-scenarios"></a>使用 BGP 社群中 ExpressRoute for Office 365 案例

連線至 Office 365 使用 Azure ExpressRoute 根據特定代表其中部署 Office 365 端點的網路的 IP 子網路的 BGP 廣告。 由於 Office 365 和構成 Office 365 服務數目的全域性質，客戶通常需要來管理他們接受其網路的廣告。 減少的 IP 子網路。稱為 IP 首碼整個本文，以配合 BGP 網路管理術語的其餘部分客戶做結尾下列目標：
  
- **管理公告的 IP 首碼接受**-內部網路基礎結構或網路電信業者只支援 IP 電話首碼數目有限的客戶和客戶網路電訊廠商接受前置詞的該費用上方的有限的數字將想要評估已通告其網路前置詞的總數，並選取哪些 Office 365 應用程式是適合用在 ExpressRoute。

- **管理的 Azure ExpressRoute 線路上所需的頻寬量**-客戶可能會想要控制對網際網路路徑的 ExpressRoute 路徑的頻寬信封的 Office 365 服務。 這可讓客戶保留特定的應用程式，例如商務用 Skype 的 ExpressRoute 頻寬，並透過網際網路路徑來路由其餘的 Office 365 應用程式。

為了協助客戶與這些目標，透過 ExpressRoute 通告的 Office 365 IP 電話首碼標記服務特定 BGP 社群值與下面範例所示。
  
> [!NOTE]
> 您應可預期一些其他的應用程式可能包含在社群值相關聯的網路流量。 這是全域軟體的預期的行為以提供共用的服務與資料中心的服務。 請儘可能使用上述兩個目標，管理前置詞計數和/或記住的頻寬，這有已最小化。

|**服務**|**BGP 社群值**|**附註**|
|:-----|:-----|:-----|
|exchange\*  <br/> |12076:5010  <br/> |包含 Exchange 和 EOP 服務\*  <br/> |
|sharepoint\*  <br/> |12076:5020  <br/> |SharePoint Online  <br/> |
|商務用 skype\*  <br/> |12076:5030  <br/> |商務用 Skype Online  <br/> |
|其他 Office 365 服務\*  <br/> |12076:5100  <br/> |Read Office 365 入口網站服務包含 Azure Active Directory （驗證和目錄同步處理案例）  <br/> |
|\*[Office 365 端點](https://aka.ms/o365endpoints)文章會詳細說明包含在 ExpressRoute 服務案例的範圍。  <br/> \*\*其他服務和 BGP 社群值可能在未來新增。 [請參閱 BGP 社群的目前的清單](https://azure.microsoft.com/documentation/articles/expressroute-routing/)。  <br/> |

## <a name="what-are-the-most-common-scenarios-for-using-bgp-communities"></a>什麼是最常見的情況中使用 BGP 社群？

客戶可能會使用 BGP 社群來調整可接受的 Azure ExpressRoute，因而影響的前置詞總數 IP 和某些 Office 365 服務的預期的頻寬信封透過其網路的 IP 前置詞的群組。 請務必了解所有 Office 365 會都需要網際網路繫結不論使用 Azure ExpressRoute 或 BGP 社群的流量。 下列三個案例是最常使用這項功能。
  
### <a name="scenario-1-minimizing-the-number-of-office-365-ip-prefixes"></a>案例 1： 減少 Office 365 IP 前置詞的次數

Contoso 公司是目前的 Exchange Online 和 SharePoint Online 中使用 Office 365 50000 人員公司。 檢閱 ExpressRoute Contoso 決定其在多個區域的位置的網路裝置的需求無法處理路由表大小大於 100 個額外的路由項目。 Contoso 檢閱 IP 首碼的 ExpressRoute for Office 365 服務一組完整會通告和上完成它超過 100 的總數。 若要保持在 100 個額外的路由項目，Contoso 範圍使用 ExpressRoute for Office 365 只是 SharePoint Online BGP 社群值，12076:5020，透過 ExpressRoute Microsoft 對等接收。

|**使用 BGP 社群標記**|**透過 Azure ExpressRoute 路由傳送的功能**|**所需的網際網路路由**|
|:-----|:-----|:-----|
|SharePoint  <br/> (12076:5020)  <br/> |SharePoint Online&amp;商務用 OneDrive  <br/> | DNS、 CRL， &amp; CDN 要求  <br/>  其他所有未特別透過 Azure ExpressRoute 支援的 Office 365 服務  <br/>  所有其他 Microsoft 雲端服務  <br/>  Office 365 入口網站、 Office 365 驗證、 &amp; Office Online  <br/>  Exchange Online、 Exchange Online 保護，與 Skype for Business Online  <br/> |

> [!NOTE]
> 若要達到較低的前置詞計數的每項服務，將會保留最少的服務之間的重疊。 這是預期的行為。
  
### <a name="scenario-2-scoping-expressroute-and-internal-bandwidth-use-to-some-office-365-services"></a>案例 2： 範圍的 ExpressRoute 與內部頻寬使用某些 Office 365 服務

Fabrikam Inc 大型的跨國企業，與分散式異質網路，是訂戶的許多 Office 365 服務，包括;Exchange Online、 SharePoint Online 和商務用 Skype。 Fabrikam 的內部路由基礎結構可以處理上千個其路由表格; 中的 IP 前置詞不過，Fabrikam 只想要佈建的 ExpressRoute 與內部網路效能及使用其現有的網際網路頻寬的所有其他 Office 365 應用程式最機密的 Office 365 應用程式的頻寬。
  
基於這個理由，Fabrikam 範圍只是商務用 Skype 商務 Online BGP 社群值，12076:5030，透過 ExpressRoute Microsoft 對等接收其 Azure ExpressRoute 頻寬。 Office 365 相關聯的其餘網路流量會繼續使用網際網路輸出點。

|**使用 BGP 社群標記**|**透過 Azure ExpressRoute 路由傳送的功能**|**所需的網際網路路由**|
|:-----|:-----|:-----|
|商務用 Skype  <br/> (12076:5030)  <br/> |Skype SIP 信號，下載項目，voice、 視訊及桌面共用  <br/> | DNS、 CRL， &amp; CDN 要求  <br/>  其他所有未特別透過 Azure ExpressRoute 支援的 Office 365 服務  <br/>  所有其他 Microsoft 雲端服務  <br/>  Office 365 入口網站、 Office 365 驗證、 &amp; Office Online  <br/>  Skype 商務遙測、 Skype 用戶端瀏覽的秘訣、 公用 IM 連線  <br/>  Exchange Online、 Exchange Online Protection 和 SharePoint Online  <br/> |

### <a name="scenario-3-scoping-azure-expressroute-for-office-365-services-only"></a>案例 3： 設定 Azure ExpressRoute 範圍僅限 Office 365 服務

Woodgrove Bank 是數個 Microsoft 雲端服務，包括 Office 365 的客戶。 之後評估其網路容量和耗用 Woodgrove Bank 決定部署 Azure ExpressRoute 支援的 Office 365 服務的慣用路徑。 路由表可支援完整的 Office 365 IP 前置詞組，它們有佈建 Azure ExpressRoute 電路支援所有的預計的頻寬和延遲性需求。
  
使用 Office 365 特定 BGP 社群值、 12076:5010、 12076:5020、 12076:5030，來標記以確保比其他 Office 365，Woodgrove Bank 範圍使用 ExpressRoute for Office 365 用於所有 IP 首碼與 Microsoft 雲端服務相關聯的網路流量12076:5100。

|**使用 BGP 社群標記**|**透過 Azure ExpressRoute 路由傳送的功能**|**所需的網際網路路由**|
|:-----|:-----|:-----|
|Exchange、 SharePoint、 商務用 Skype&amp;其他服務  <br/> （12076:5010、 12076:5020、 12076:5030、 12076:5100）  <br/> |Exchange Online &amp; Exchange Online Protection  <br/> SharePoint Online&amp;商務用 OneDrive  <br/> Skype SIP 信號，下載項目，voice、 視訊及桌面共用  <br/> Office 365 入口網站、 Office 365 驗證、 &amp; Office Online  <br/> | DNS、 CRL， &amp; CDN 要求  <br/>  其他所有未特別透過 Azure ExpressRoute 支援的 Office 365 服務  <br/>  所有其他 Microsoft 雲端服務  <br/> |

## <a name="key-planning-considerations-to-using-bgp-communities"></a>主要的規劃考量，以使用 BGP 社群

選擇利用 BGP 社群影響如何 ExpressRoute 通告且傳播到客戶網路的客戶應該考慮的下列考量：
  
- 請務必確定您網路設計中使用 BGP 社群時仍維護路由對稱性來看。 在某些情況下，新增或移除的 BGP 社群可能建立的情況下，其中對稱路由是中斷，而必須更新您路由組態，以重新建立 [對稱路由。

- 設定 Azure ExpressRoute BGP 社群值的範圍是客戶巨集指令。 Microsoft 會通知所有 IP 首碼相關都聯不論由客戶設定任何範圍設定的對等關係。

- Azure ExpressRoute 不支援根據指派給 BGP 社群的客戶的 Microsoft 的網路上的任何動作。

- Office 365are 所使用的 IP 前置詞只標示服務特定 BGP 社群的值，不支援特定的 BGP 社群的位置。 Office 365 服務都通用的性質，篩選依據租用戶的位置的前置詞或不支援在 Office 365 雲端內的資料。 建議的方法是設定您的網路，以協調最短或最慣用的網路路徑，從使用者的網路位置，成 Microsoft 全球網路，不論的實體位置的 Office 365 服務的 IP 位址他們正在要求。

- 包含在每個 BGP 社群值中的 IP 前置詞代表包含值相關聯的 Office 365 應用程式的 IP 位址的子網路。 在某些情況下，多個 Office 365 應用程式都有內產生的 IP 子網路的 IP 位址的前置詞存在於一個以上的社群值中。 這是預期，但是很少，因為配置分散情形的行為，並不會影響前置詞計數或頻寬管理目標。 客戶可以鼓勵使用 「 允許所需 」 方法而不是 「 拒絕什麼，就不需要 「 時善用 BGP 社群的 Office 365 的影響降到最低。

- 使用 BGP 社群並不會變更基礎的網路連線能力需求或使用 Office 365 所需的設定。 想要存取 Office 365 的客戶會仍然需要能夠存取網際網路。

- 設定 Azure ExpressRoute 範圍使用 BGP 社群只會影響您的內部網路可以看到透過 Microsoft 對等關係的路由。 您可能需要進行額外的應用程式層級的設定等使用的 PAC 或 WPAD 組態搭配範圍的路由。

- 除了使用 Microsoft 指派 BGP 社群，客戶可以選擇將自己 BGP 社群指派給 Office 365 IP 電話首碼學會透過 Azure ExpressRoute 影響內部路由。 常用的使用案例將按照位置 BGP 社群指派給所有路由學會透過對等的位置，然後使用該資訊傳輸客戶網路中，協調最短每個指定 ExpressRoute 或最慣用的插入的網路路徑Microsoft 的網路。 客戶指派使用 ExpressRoute for Office 365 案例的 BGP 社群的用途是 Microsoft 控制項或可見性的範圍外。

以下是您可以使用返回下列短連結： [https://aka.ms/bgpexpressroute365](https://aka.ms/bgpexpressroute365)。
  
## <a name="related-topics"></a>相關主題

[對 Office 365 的網路連線](network-connectivity.md)
  
[Azure ExpressRoute for Office 365](azure-expressroute.md)
  
[管理 ExpressRoute for Office 365 連線](managing-expressroute-for-connectivity.md)
  
[使用 ExpressRoute for Office 365 進行路由傳送](routing-with-expressroute.md)
  
[使用 ExpressRoute for Office 365 進行網路規劃](network-planning-with-expressroute.md)
  
[商務用 Skype Online 中的媒體品質和網路連線效能](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917) (英文)
  
[ExpressRoute 與 QoS skype for Business Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[使用 ExpressRoute 的通話流程](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[實作 ExpressRoute for Office 365](implementing-expressroute.md)
  
[支援的 BGP 社群](https://azure.microsoft.com/documentation/articles/expressroute-routing/)
  
[使用基準與效能歷程記錄進行 Office 365 效能調整](performance-tuning-using-baselines-and-history.md)
  
[Office 365 的效能疑難排解規劃](performance-troubleshooting-plan.md)
  
[Azure ExpressRoute for Office 365 訓練](https://channel9.msdn.com/series/aer)
