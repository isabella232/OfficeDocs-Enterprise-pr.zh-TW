---
title: 評估 Office 365 網路連線
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 8/7/2019
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
ms.assetid: 64b420ef-0218-48f6-8a34-74bb27633b10
description: Office 365 被為了讓使得全球客戶服務使用的網際網路連線的連線。 隨著服務發展，安全性、 效能和可靠性的 Office 365 已獲得改善根據上使用網際網路來建立連線至服務的客戶。
ms.openlocfilehash: 2f58bf71c292f57ccef79f7f0f79e1cd474c681d
ms.sourcegitcommit: 2e6fadb5b2b16619ad141b6293d3466460720cb4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2019
ms.locfileid: "37428070"
---
# <a name="assessing-office-365-network-connectivity"></a>評估 Office 365 網路連線

*本文適用於 Office 365 企業版和 Microsoft 365 企業版*

Office 365 被為了讓使得全球客戶服務使用的網際網路連線的連線。 隨著服務發展，安全性、 效能和可靠性的 Office 365 已獲得改善根據上使用網際網路來建立連線至服務的客戶。
  
規劃使用 Office 365 的客戶應該評估其現有和預測的網際網路連線能力需求作為部署專案的一部分。 對於企業類別部署可靠並適當地調整大小的網際網路連線能力屬於重要耗用 Office 365 的功能與案例。
  
網路評估可以執行由許多不同的人員或組織根據您的大小和喜好設定。 評估網路範圍也可以視其中您正在閱讀在您的部署程序而異。 若要可協助您開始的花費執行網路評估更深入了解，我們已產生的網路評估指南，協助您了解您可用的選項。 此評定會決定哪些步驟和資源需要新增至部署專案，使您能夠成功地採用 Office 365。
  
完整的網路評估會提供可能的解決方案，以及實作詳細資料的網路設計質詢。 某些網路 「 評估 」 會顯示可容納最佳化網路連線至 Office 365 與次要設定或現有的網路和網際網路輸出基礎結構的設計變更。

某些評估會指出對 Office 365 的網路連線時，需要在 [網路元件的額外投資。 例如，橫跨分公司和多個地理區域的企業網路可能需要 SD WAN 解決方案或最佳化的路由基礎結構，以支援網際網路連線到 Office 365 中的投資。 有時會評估會指出對 Office 365 的網路連線受到法規或效能需求，例如[Skype for Business Online 媒體品質](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)的案例。 這些額外的需求可能會導致網際網路連線能力基礎結構、 路由最佳化及特殊直接連線的投資。

若要協助您評估您的網路一些資源：

- 如需 Office 365 網路功能概念資訊，請參閱[Office 365 網路連線能力概觀](office-365-networking-overview.md)。
- 請參閱[Office 365 網路連線原則](https://aka.ms/o365networkingprinciples)來了解安全地管理 Office 365 流量，並取得獲得最佳效能的連線能力原則。
- 註冊的[Microsoft FastTrack](https://www.microsoft.com/en-us/fasttrack)引導式協助 Office 365 的規劃、 設計及部署。 
- 請參閱[Office 365 網路上架工具](assessing-network-connectivity.md#the-office-365-network-onboarding-tool)下一節，以執行基本的連線測試可提供網路連線能力增強功能，可以指定的使用者的位置與 Office 365 之間進行的特定指導。

> [!NOTE]
> Microsoft 授權，才能使用 ExpressRoute for Office 365。 Microsoft 會檢閱每個客戶要求，並僅授權 ExpressRoute for Office 365 流量，當客戶的法規需求所要求的直接連線。 如果您有這類需求，請提供規定您解讀表示直接連線需要在[ExpressRoute for Office 365 要求表單](https://aka.ms/O365ERReview)中，若要開始 Microsoft 檢閱其文字摘錄與網頁連結。 未經授權嘗試建立 Office 365 路由篩選器的訂用帳戶會收到[錯誤訊息](https://support.microsoft.com/kb/3181709)。
  
規劃您的 Office 365 的網路評估時需要考量重點：
  
- Office 365 是安全、 可靠、 高效能執行的服務，透過公用的網際網路。 我們繼續投入以增強服務的下列層面。 所有 Office 365 服務都可透過網際網路連線能力。

- 我們會不斷最佳化的核心的 Office 365 的各個層面，例如可用性、 全域達到，與效能的網際網路連線。 例如，有許多 Office 365 服務利用網際網路對向 edge 節點的延伸集。 此 edge 網路提供最佳的近似值和即將透過網際網路連線的效能。

- 客戶時考慮使用 Office 365 任何包含服務例如 Teams 或 Skype 商務 Online voice、 視訊或會議功能，應該完成端對端網路評估，並符合使用[Microsoft 的連線能力需求FastTrack](https://www.microsoft.com/en-us/fasttrack)。

如果您正在評估 Office 365，並不確定要開始使用您的網路評估或已找到網路設計挑戰，您必須取得協助若要克服，請使用您的 Microsoft 客戶團隊。

## <a name="the-office-365-network-onboarding-tool"></a>Office 365 網路上架工具

[Office 365 網路上架工具](https://aka.ms/netonboard)是概念證明 (POC) 網路評定工具執行基本的連線測試對您的 Office 365 租用戶，並讓特定網路設計建議，Office 365 的最佳效能。 此工具會醒目提示一般大型企業網路周邊的設計選擇也就是有用的網際網路網站瀏覽]，但影響大型的 SaaS 應用程式，例如 Office 365 的效能。

網路上架工具會執行下列動作：

- 偵測到您的位置，或者您可以指定要測試的位置
- 檢查您的網路輸出的位置
- 測試最接近的 Office 365 服務前哨的網路路徑
- 提供進階的測試使用可下載的 Windows 10 應用程式能夠讓相關 proxy 伺服器、 防火牆和 DNS 周邊網路設計建議。 此工具也執行效能測試 skype 商務 Online、 Microsoft Teams、 SharePoint Online 和 Exchange Online。

此工具有兩個元件： 瀏覽器型的使用者介面，收集基本連線資訊和可下載的 Windows 10 應用程式，就會執行進階的測試並傳回額外的評估資料。

瀏覽器型的工具會顯示下列資訊：

- 結果和影響] 索引標籤
  - 在地圖上的使用中的服務的前哨位置
  - 在地圖上的其他服務前方門會提供最佳的連線能力的位置
  - 相較於其他靠近您的 Office 365 客戶的相關效能
- 詳細資料與方案] 索引標籤
  - 縣/市以及國家/地區的使用者位置
  - 縣/市、 狀態及國家/地區的網路輸出位置
  - 使用者網路輸出距離
  - Office 365 Exchange Online 服務的前哨位置
  - 最佳的 Office 365 Exchange Online 服務 front door(s) 使用者位置
  - 在您地鐵] 區域中具有較佳效能的客戶

進階測試可下載應用程式提供下列的額外資訊：

- 詳細資料和解決方案] 索引標籤 （附加）
  - 使用者的預設閘道
  - 用戶端 DNS 伺服器
  - 用戶端 DNS 遞迴解析程式
  - Exchange Online DNS 伺服器
  - SharePoint Online 的 DNS 伺服器
  - Proxy 伺服器識別碼
  - 媒體連線檢查
  - 媒體品質封包遺失
  - 媒體品質延遲
  - 媒體品質抖動
  - 媒體品質封包重新排列
- 多個特定功能的端點的連線測試
- 包含 tracert 及延遲的 Exchange Online、 SharePoint Online 和 microsoft Teams 服務資料的網路路徑診斷

您可以了解 Office 365 網路上架工具，並提供意見反應在[更新 Office 365 網路上架工具 POC 新網路設計建議](https://techcommunity.microsoft.com/t5/Office-365-Networking/Updated-Office-365-Network-Onboarding-Tool-POC-with-new-network/m-p/711130#M130)部落格文章。 這項工具的未來更新和其他 Office 365 網路更新相關資訊會張貼到[Office 365 網路](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)的部落格。
  
以下是您可以使用返回下列短連結： [ https://aka.ms/o365networkconnectivity。](https://aka.ms/o365networkconnectivity)
  
## <a name="see-also"></a>另請參閱

[Office 365 網路連線能力概觀](office-365-networking-overview.md)

[Office 365 網路連線原則](https://aka.ms/o365networkingprinciples)

[管理 Office 365 端點](managing-office-365-endpoints.md)

[Office 365 URL 與 IP 位址範圍](urls-and-ip-address-ranges.md) (英文)

[Office 365 IP 位址和 URL Web 服務](office-365-ip-web-service.md)

[Office 365 網路與效能調整](network-planning-and-performance.md)

[Microsoft 365 企業版概觀](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
