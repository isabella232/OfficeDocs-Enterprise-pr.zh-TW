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
description: ExpressRoute for Office 365 提供了替代的路由路徑，而不需要所有輸出至網際網路的流量到達許多 Office 365 服務。 雖然仍需要網際網路連線到 Office 365，Microsoft 會通告 BGP 透過您的網路特定路由可以讓您直接的 ExpressRoute 線路慣用除非有其他網路中的設定。 您可能想要設定來管理此路由包含三個一般區域首碼篩選、 安全性和合規性。
ms.openlocfilehash: 5345c4067f4ecf9b1b1bc1a0ad20d6e1f5273f65
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487729"
---
# <a name="managing-expressroute-for-office-365-connectivity"></a>管理 ExpressRoute for Office 365 連線

ExpressRoute for Office 365 提供了替代的路由路徑，而不需要所有輸出至網際網路的流量到達許多 Office 365 服務。 雖然仍需要網際網路連線到 Office 365，Microsoft 會通告 BGP 透過您的網路特定路由可以讓您直接的 ExpressRoute 線路慣用除非有其他網路中的設定。 您可能想要設定來管理此路由包含三個一般區域首碼篩選、 安全性和合規性。
  
> [!NOTE]
> Microsoft 會變更 Microsoft Peering 路由網域檢閱 Azure ExpressRoute 的方式。 啟動 2017 年 7 月 31 日，所有 Azure ExpressRoute 客戶可以都啟用 Microsoft Peering 直接從 Azure 系統管理主控台或透過 PowerShell。 啟用 Microsoft Peering 之後, 任何客戶可以建立路由篩選器，以接收 BGP 路由廣告 Dynamics 365 客戶參與應用程式 （前身為 CRM Online）。 需要 Azure ExpressRoute for Office 365 的客戶必須從 Microsoft 取得檢閱，他們可以建立 Office 365 路由篩選之前。 請連絡您的 Microsoft 帳戶小組，以了解如何要求啟用 Office 365 ExpressRoute 檢閱。 未經授權嘗試建立 Office 365 路由篩選器的訂用帳戶會收到[錯誤訊息](https://support.microsoft.com/kb/3181709)
  
## <a name="prefix-filtering"></a>篩選的前置詞

Microsoft 建議客戶接受所有 BGP 路由所通告從 Microsoft、 提供路由經過嚴格的檢閱及驗證的程序移除任何優點，以新增審查。 ExpressRoute 原本就會提供建議的控制項，例如 IP 前置詞擁有權、 完整性和小數位數-與客戶端篩選沒有內送路由。
  
如果您需要額外的路由擁有權的驗證跨 ExpressRoute 公用對等時，您可以檢查清單中的所有 IPv4 與 IPv6 IP 前置詞，代表[Microsoft 公用 IP 範圍](https://www.microsoft.com/download/details.aspx?id=53602)依據公告的路由。 這些範圍涵蓋完整的 Microsoft 位址空間，並變更很少，提供可靠組範圍篩選器也擔心非 Microsoft 擁有路由到遺漏的客戶提供額外保護其環境。 事件中已變更，將會對第 1 個月及頁面的 [**詳細資料**] 區段中的版本號碼將會變更每次更新檔案。
  
有許多若要避免使用的[Office 365 Url 和 IP 位址範圍](https://aka.ms/o365endpoints)，用於產生前置詞篩選清單的原因。 包括下列：
  
- Office 365 IP 電話首碼經歷大量上頻繁地變更。

- Office 365 Url 與 IP 位址範圍專為管理防火牆允許清單與 Proxy 基礎結構，無法路由傳送。

- Office 365 Url 和 IP 位址範圍不包含可能會在您的 ExpressRoute 連線的範圍內其他 Microsoft 服務。

| |
|**選項**|**複雜性**|**變更控制項**|
|:-----|:-----|:-----|
|接受所有 Microsoft 路由  <br/> |**低：** 客戶會依賴 Microsoft 控制，以確保正確且擁有所有路由。  <br/> |無  <br/> |
|篩選 Microsoft 擁有 supernets  <br/> |**中型：** 客戶會實作以允許只擁有路由的 Microsoft 摘錄的前置詞的篩選器清單。  <br/> |客戶必須確保非經常性更新會反映在路由篩選器。  <br/> |
|篩選的 Office 365 IP 範圍  <br/> [!CAUTION] 不建議
|**高：** 客戶篩選根據定義的 Office 365 IP 前置詞的路由。  <br/> |客戶必須實作的每月更新健全的變更管理程序。  <br/> [!CAUTION] 此解決方案需要在後續的重大變更。 尚未實作中的時間可能會導致服務中斷的變更。   |

連線至 Office 365 使用 Azure ExpressRoute 根據特定代表其中部署 Office 365 端點的網路的 IP 子網路的 BGP 廣告。 由於 Office 365 和 Office 365 構成服務數目的全域性質，客戶通常需要來管理他們接受其網路的廣告。 如果您擔心數目的首碼通告至您的環境， [BGP 社群](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099)功能可讓您篩選至一組特定的 Office 365 服務廣告。 此功能目前正在預覽。
  
不論您如何管理來自 Microsoft 的 BGP 路由通告，您將不會獲得任何特殊暴露於 Office 365 服務時相較於透過單獨 internet 電路連線到 Office 365。 Microsoft 的維護同一個安全性、 規範和效能層級的客戶用來連線到 Office 365 的電路類型為何。
  
### <a name="security"></a>安全性

Microsoft 建議您維護自己的網路和安全性周邊控制項連線移到及傳送自 ExpressRoute 公用和 Microsoft 對等，其中包含連線到及傳送自 Office 365 服務。 安全性控制應該是中的位置往外從您的網路與 Microsoft 的網路，以及來自 Microsoft 的網路輸入到您網路的網路要求。
  
#### <a name="outbound-from-customer-to-microsoft"></a>從客戶輸出到 Microsoft
  
當電腦連線到 Office 365 時，他們連線至相同的端點，不論是否已連線透過網際網路或 ExpressRoute 線路集合。 無論所使用的電路，Microsoft 建議您將 Office 365 服務，視為更泛型網際網路目的地比信任。 您的撥出的安全性控制應該專注於的連接埠和通訊協定以減少曝光度，並持續維護降至最低。 使用[Office 365 端點](https://aka.ms/o365endpoints)參考文件中的必要連接埠資訊。
  
已新增的控制項，您可以使用 FQDN 層級的 proxy 基礎結構內篩選來限制或檢查部分或所有目的地網際網路或 Office 365 的網路要求。 維護 Fqdn 的清單，隨著功能發行和 Office 365 方案仍有發展需要更強固的變更管理和追蹤修訂的已發佈的[Office 365 端點](https://aka.ms/o365endpoints)。
  
> [!CAUTION]
> Microsoft 建議您不要察覺依賴 IP 首碼若要管理輸出至 Office 365 的安全性。

|**選項**|**複雜性**|**變更控制項**|
|:-----|:-----|:-----|
|無限制  <br/> |**低：** 客戶允許不受限制的輸出存取，給 Microsoft。  <br/> |無  <br/> |
|連接埠限制  <br/> |**低：** 客戶會限制輸出存取 Microsoft 所預期的連接埠。  <br/> |非經常性。  <br/> |
|FQDN 限制  <br/> |**高：** 客戶會限制輸出存取已發佈的 Fqdn 為基礎的 Office 365。  <br/> |每月的變更。  <br/> |

#### <a name="inbound-from-microsoft-to-customer"></a>輸入來自 Microsoft 客戶
  
有數個需要 Microsoft，以啟動連線到您網路的選用案例。
  
- 在 [密碼驗證登入期間 ADFS。

- [Exchange Server Hybrid deployments](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx)。

- 郵件從 Exchange Online 租用戶至內部部署主機。

- SharePoint Online 的郵件將傳送至內部部署主機的 [從 SharePoint Online。

- [SharePoint 同盟混合式搜尋](https://technet.microsoft.com/library/dn197174.aspx)。

- [SharePoint 混合式 BCS](https://technet.microsoft.com/library/dn197239.aspx )。

- [混合式商務用 Skype](https://technet.microsoft.com/en-us/library/jj205403.aspx)和/或[商務用 Skype 商務同盟](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx)。

- [Skype 商務雲端連接器](https://technet.microsoft.com/library/mt605227.aspx )。

Microsoft 建議透過網際網路電路接受這些連線，而不是您的 ExpressRoute 線路若要降低複雜度。 如果您的合規性或效能需要為了滿足這些輸入的連線必須接受透過 ExpressRoute 線路，建議使用防火牆或反向 proxy 的範圍可接受的連線。 您可以使用[Office 365 端點](https://aka.ms/o365endpoints)以找出右 Fqdn 及 IP 前置詞。
  
### <a name="compliance"></a>合規性

我們不依賴您用於任何我們相容性控制的路由路徑。 不論是否您連線至 Office 365 服務透過 ExpressRoute 或網際網路電路，也不會變更我們相容性控制。 您應檢閱的不同的合規性和安全性憑證的層級 for Office 365 來找出符合您的組織需求的最佳選擇。
  
您可以使用下列短連結返回這裡：[https://aka.ms/manageexpressroute365](https://aka.ms/manageexpressroute365)
  
## <a name="related-topics"></a>相關主題

[內容傳遞網路](content-delivery-networks.md)
  
[Office 365 URL 與 IP 位址範圍](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[管理 Office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Azure ExpressRoute for Office 365 訓練](https://channel9.msdn.com/series/aer)
