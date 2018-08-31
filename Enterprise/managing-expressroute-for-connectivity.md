---
title: 管理 ExpressRoute for Office 365 連線
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/13/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid:
- MET150
- BCS160
ms.assetid: e4468915-15e1-4530-9361-cd18ce82e231
description: Office 365 ExpressRoute 提供而不需要到網際網路的輸出至所有流量到達許多 Office 365 服務的替代路由路徑。雖然仍需要網際網路連線至 Office 365 時，Microsoft 通告 BGP 透過您的網路特定路由會讓直接 ExpressRoute 基礎的電路慣用除非有您網路中的其他設定。要設定來管理此路由包含三個一般區域首碼篩選、 安全性及規範。
ms.openlocfilehash: 5345c4067f4ecf9b1b1bc1a0ad20d6e1f5273f65
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539988"
---
# <a name="managing-expressroute-for-office-365-connectivity"></a>管理 ExpressRoute for Office 365 連線

Office 365 ExpressRoute 提供而不需要到網際網路的輸出至所有流量到達許多 Office 365 服務的替代路由路徑。雖然仍需要網際網路連線至 Office 365 時，Microsoft 通告 BGP 透過您的網路特定路由會讓直接 ExpressRoute 基礎的電路慣用除非有您網路中的其他設定。要設定來管理此路由包含三個一般區域首碼篩選、 安全性及規範。
  
> [!NOTE]
> Microsoft 變更 Microsoft Peering 路由網域檢閱的 Azure ExpressRoute 的方式。啟動 2017 年 7 月 31 所有 Azure ExpressRoute 客戶可以都啟用 Microsoft Peering Azure 系統管理主控台從直接或透過 PowerShell。啟用 Microsoft Peering 之後, 任何客戶可以建立路由篩選器以接收 BGP 路由廣告 Dynamics 365 客戶參與應用程式 （前身為 CRM Online）。他們可以建立路由篩選 for Office 365 之前需要 Azure ExpressRoute for Office 365 的客戶必須從 Microsoft 取得檢閱。請連絡您的 Microsoft 帳戶小組來了解如何要求啟用 Office 365 ExpressRoute 檢閱。未經授權嘗試建立 Office 365 路由篩選的訂閱將收到[錯誤訊息](https://support.microsoft.com/kb/3181709)
  
## <a name="prefix-filtering"></a>字首篩選

Microsoft 建議客戶接受所有 BGP 路由如 microsoft 通告、 所提供之路由、 經歷嚴密的檢閱和驗證的程序移除無法新增至任何好處。ExpressRoute 原本就會提供與篩選在客戶端沒有輸入路由的 IP 前置詞擁有權、 完整性和規模-例如建議的控制項。
  
如果您需要的路由擁有權的其他驗證跨 ExpressRoute 公用對等，您可以檢查針對所有 IPv4 和 IPv6 IP 前置字元的清單，表示[Microsoft 的公用 IP 範圍](https://www.microsoft.com/download/details.aspx?id=53602)的公告所的路由。這些範圍涵蓋的完整 Microsoft 位址空間，並提供可靠的一組篩選依據的範圍，也提供其他保護擔心非 Microsoft 擁有路由到遺漏的客戶常，變更其環境。事件沒有變更，則會由上個月第 1 和] 頁面上的 [**詳細資料**] 區段的版本號碼會變更每次更新檔案。
  
有許多避免產生前置詞篩選清單的[Office 365 Url 和 IP 位址範圍](https://aka.ms/o365endpoints)使用的原因。包括下列：
  
- Office 365 IP 前置詞、 經歷許多常用為基礎的變更。

- Office 365 Url 和 IP 位址範圍的設計用來管理防火牆允許清單與 Proxy 基礎結構、 未傳送。

- Office 365 Url 和 IP 位址範圍涵蓋其他 Microsoft 服務可能會涵蓋 ExpressRoute 連線。

| |
|**選項**|**複雜性**|**變更控制項**|
|:-----|:-----|:-----|
|接受所有的 Microsoft 路由  <br/> |**低：** 客戶會依賴 Microsoft 控制項以確保正確且擁有的所有路由。  <br/> |無  <br/> |
|篩選 Microsoft 擁有 supernets  <br/> |**中型：** 客戶實作允許擁有路由的 Microsoft 摘要的前置詞篩選清單。  <br/> |客戶必須確定非經常性更新便會反映在路由篩選器。  <br/> |
|篩選 Office 365 IP 範圍  <br/> [!CAUTION] 不建議使用
|**高：** 客戶篩選根據已定義的 Office 365 IP 前置詞的路由。  <br/> |客戶必須實作完善變更管理程序的每月的更新。  <br/> [!CAUTION]此解決方案需要持續進行的重大變更。尚未實行的時間可能會導致服務中斷的變更。   |

連線至 Office 365 使用 Azure ExpressRoute 根據 BGP 廣告的特定代表的網路之部署 Office 365 端點的 IP 子網路。Office 365 與 Office 365 所組成的服務號碼的全域性質，因為客戶通常有管理它們接受其網路廣告需要。如果您擔心與通告到您的環境的前置字元的數字， [BGP 社群](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099)功能可讓您篩選到特定的一段 Office 365 服務廣告。此功能目前處於預覽。
  
不論您管理來自 Microsoft BGP 路由廣告方式，您將不會獲得任何特殊公開給 Office 365 服務相較於透過網際網路基礎的電路表達連線至 Office 365。Microsoft 維護同一個安全性、 規範、 及效能層級的客戶用來連線到 Office 365 的電路型別無關。
  
### <a name="security"></a>安全性

Microsoft 建議您維護自己網路和安全性周邊控制項連線移到與 ExpressRoute 公用和 Microsoft 對等，其中包含與 Office 365 服務的連線。安全性控管應網路要求之旅行社輸出從您的網路到 Microsoft 的網路，以及從 Microsoft 的網路輸入您的網路位置。
  
#### <a name="outbound-from-customer-to-microsoft"></a>從客戶輸出到 Microsoft
  
當電腦連線到 Office 365 時，可連至相同的一組不論是否透過網際網路或 ExpressRoute 電路進行連線的端點。無論所使用的電路，Microsoft 建議您將 Office 365 服務，視為多信任比一般網際網路目的地的電話。輸出安全性控管您應著重於的連接埠和通訊協定以減少衝擊並持續維護最小化。使用[Office 365 端點](https://aka.ms/o365endpoints)參考文章中所需的連接埠資訊。
  
已新增的控制項，您可以使用 FQDN 層級的 proxy 基礎結構內篩選限制或檢查目的地的網際網路或 Office 365 的部分或所有網路要求。隨著發行功能和 Office 365 方案仍有發展空間維護的 Fqdn 清單需要更完善的變更管理與追蹤的變更到已發佈的[Office 365 端點](https://aka.ms/o365endpoints)。
  
> [!CAUTION]
> Microsoft 建議您不要察覺依賴 IP 前置詞來管理輸出至 Office 365 的安全性。

|**選項**|**複雜性**|**變更控制項**|
|:-----|:-----|:-----|
|無限制  <br/> |**低：** 客戶允許無限制的輸出存取給 Microsoft。  <br/> |無  <br/> |
|連接埠限制  <br/> |**低：** 客戶限制輸出存取 Microsoft 所預期的連接埠。  <br/> |非經常性。  <br/> |
|FQDN 限制  <br/> |**高：** 客戶輸出存取限制的已發佈的 fqdn 均為基礎的 Office 365。  <br/> |每月的變更。  <br/> |

#### <a name="inbound-from-microsoft-to-customer"></a>輸入 microsoft 客戶
  
有數個選用的案例需要 Microsoft 啟動您的網路連線。
  
- 在 [密碼驗證登入期間 ADFS。

- [Exchange Server 混合式部署](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx)。

- 將郵件從 Exchange Online 租用戶至內部部署主機。

- SharePoint Online 郵件將傳送至內部部署主機的 [從 SharePoint Online。

- [ [SharePoint 同盟混合式搜尋](https://technet.microsoft.com/library/dn197174.aspx)]。

- [SharePoint 混合式 BCS](https://technet.microsoft.com/library/dn197239.aspx )。

- [用於商業的混合式 Skype](https://technet.microsoft.com/en-us/library/jj205403.aspx)和/或[Skype 商務同盟](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx)。

- [Skype Business Cloud 連接器](https://technet.microsoft.com/library/mt605227.aspx )。

Microsoft 建議您接受這些連線透過網際網路電路而不是以降低複雜度您 ExpressRoute 電路。如果您的規範或效能需求支配哪些必須透過 ExpressRoute 電路接受這些輸入的連線，，建議使用防火牆或反向 proxy 的範圍公認的連線。您可以使用[Office 365 端點](https://aka.ms/o365endpoints)來了解右 Fqdn 和 IP 前置詞。
  
### <a name="compliance"></a>法規符合性

我們不依賴您用於任何我們規範控制項的路由路徑。不論是否連線到 Office 365 服務透過 ExpressRoute 或網際網路電路，我們規範控制項將不會變更。您應該檢閱的不同規範和找出符合您的組織需求的最佳選擇 Office 365 的安全性憑證層級。
  
以下是您可以使用回來的簡短連結：[https://aka.ms/manageexpressroute365](https://aka.ms/manageexpressroute365)
  
## <a name="related-topics"></a>相關主題

[內容傳遞網路](content-delivery-networks.md)
  
[Office 365 URL 與 IP 位址範圍](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[管理 Office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Azure ExpressRoute for Office 365 訓練](https://channel9.msdn.com/series/aer)
