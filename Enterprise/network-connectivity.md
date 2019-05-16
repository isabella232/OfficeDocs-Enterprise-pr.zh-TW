---
title: Office 365 的網路連線能力
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/01/2018
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
ms.openlocfilehash: 4510cb073c0fde64abc4ee796a55d7ef32662f8c
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069869"
---
# <a name="network-connectivity-to-office-365"></a>Office 365 的網路連線能力

Office 365 被為了讓使得全球客戶服務使用的網際網路連線的連線。 隨著服務發展，安全性、 效能和可靠性的 Office 365 已獲得改善根據上使用網際網路來建立連線至服務的客戶。
  
規劃使用 Office 365 的客戶應該評估其現有和預測的網際網路連線能力需求作為部署專案的一部分。 對於企業類別部署可靠並適當地調整大小的網際網路連線能力屬於重要耗用 Office 365 的功能與案例。
  
網路評估可以執行由許多不同的人員或組織根據您的大小和喜好設定。 評估網路範圍也可以視其中您正在閱讀在您的部署程序而異。 若要可協助您開始的花費執行網路評估更深入了解，我們已產生的網路評估指南，協助您了解您可用的選項。 此評定會決定哪些步驟和資源需要新增至部署專案，使您能夠成功地採用 Office 365。
  
完整網路評估，像是[Skype 操作架構](https://www.skypeoperationsframework.com/)中所述會提供給網路實作細節以及設計挑戰可能的解決方案。 大部分的網路評估會指出對 Office 365 的網路連線可以容納與[次要的設定] 或 [設計變更](https://aka.ms/manageo365endpoints)現有的網路和網際網路輸出基礎結構。

某些評估會指出對 Office 365 的網路連線時，需要在 [網路元件的額外投資。 WAN 頻寬或最佳化的路由基礎結構，以支援網際網路連線到 Office 365 中的例如投資。 有時會評估會指出對 Office 365 的網路連線受到法規或效能需求，例如[Skype for Business Online 媒體品質](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)的案例。 這些額外的需求可能會導致網際網路連線能力基礎結構、 路由最佳化及特殊直接連線的投資。
  
> [!NOTE]
> Microsoft 授權，才能使用 ExpressRoute for Office 365。 Microsoft 會檢閱每個客戶要求，並僅授權 ExpressRoute for Office 365 流量，當客戶的法規需求所要求的直接連線。 如果您有這類需求，請提供規定您解讀表示直接連線需要在[ExpressRoute for Office 365 要求表單](https://aka.ms/O365ERReview)中，若要開始 Microsoft 檢閱其文字摘錄與網頁連結。 未經授權嘗試建立 Office 365 路由篩選器的訂用帳戶會收到[錯誤訊息](https://support.microsoft.com/kb/3181709)。
  
規劃您的 Office 365 的網路評估時需要考量重點：
  
- Office 365 是安全、 可靠、 高效能執行的服務，透過公用的網際網路。 我們繼續投入以增強服務的下列層面。 所有 Office 365 服務都可透過網際網路連線能力。

- 我們會不斷最佳化的核心的 Office 365 的各個層面，例如可用性、 全域達到，與效能的網際網路連線。 例如，有許多 Office 365 服務利用網際網路對向 edge 節點的延伸集。 此 edge 網路提供最佳的近似值和即將透過網際網路連線的效能。

- 考慮使用 Office 365 任何包含服務例如 Skype 商務 Online voice、 視訊或會議功能，客戶必須完成端對端網路評估，並符合使用我們 Skype Operations Framework 的需求。 這些客戶會有數個選項可以符合雲端連線能力，包括 ExpressRoute 的特定需求。

看看 Microsoft 的案例研究[的 Microsoft Office 365 的最佳化網路效能](https://msdn.microsoft.com/en-us/library/mt450488.aspx)。 如果您正在評估 Office 365，並不確定要開始使用您的網路評估或已找到網路設計挑戰，您必須取得協助若要克服，請使用您的 Microsoft 客戶團隊。
  
此外，請閱讀[Office 365 網路連線原則](https://aka.ms/o365networkingprinciples)來了解安全地管理 Office 365 流量，並取得獲得最佳效能的連線能力原則。 本文可協助您了解安全地最佳化 Office 365 網路連線的最新的指引。
  
以下是您可以使用返回下列短連結： [ https://aka.ms/o365networkconnectivity。](https://aka.ms/o365networkconnectivity)
  
## <a name="see-also"></a>另請參閱

[管理 Office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Office 365 端點常見問題集](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) (機器翻譯)
  
[Office 365 網路與效能調整](network-planning-and-performance.md)
  
[Azure ExpressRoute for Office 365](azure-expressroute.md)
  
[使用 ExpressRoute for Office 365 進行路由傳送](routing-with-expressroute.md)
  
[使用 ExpressRoute for Office 365 進行網路規劃](network-planning-with-expressroute.md)
  
[使用 BGP 社群中 ExpressRoute for Office 365 案例 （預覽）](bgp-communities-in-expressroute.md)
  
[商務用 Skype Online 中的媒體品質和網路連線效能](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917) (英文)
  
[Office 365 URL 與 IP 位址範圍](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) (英文)
  
[Office 365 網路連線原則](https://aka.ms/o365networkingprinciples)
