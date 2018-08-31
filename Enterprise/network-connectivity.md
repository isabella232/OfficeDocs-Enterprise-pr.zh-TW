---
title: 對 Office 365 的網路連線
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/2/2018
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
ms.assetid: 64b420ef-0218-48f6-8a34-74bb27633b10
description: Office 365 的設計啟用全世界的客戶使用網際網路連線服務的連線。隨著服務發展、 安全性、 效能及可靠性的 Office 365 改善根據上客戶使用網際網路來建立服務的連線。
ms.openlocfilehash: b72b0a4584542e4c8673c7cf009c66aa97c6b81c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540172"
---
# <a name="network-connectivity-to-office-365"></a>對 Office 365 的網路連線

Office 365 的設計啟用全世界的客戶使用網際網路連線服務的連線。隨著服務發展、 安全性、 效能及可靠性的 Office 365 改善根據上客戶使用網際網路來建立服務的連線。
  
計劃使用 Office 365 的客戶應該評估使用者現有和預測的網際網路連線能力需求的部署專案的一部分。企業類別部署可靠和大小適當的網際網路連線是 Office 365 功能與案例中取用的重要部分。
  
網路評估可執行許多不同的人員和組織視您的大小和喜好設定。評估網路範圍可以有所不同其中您是在您的部署程序中。為了協助您做好花費執行網路評估的改善了解，我們已產生網路評估指南 》 可協助您了解您可用的選項。此評估決定步驟及資源需要什麼新增至以讓您能夠順利採用 Office 365 部署專案。
  
像這些指定的事[Skype Operations Framework](https://www.skypeoperationsframework.com/)會提供可能的解決方案及實作詳細資料的網路設計挑戰全方位網路評估。大部分的網路評估會表示網路連線至 Office 365 可以容納與[次要設定] 或 [設計變更](https://aka.ms/manageo365endpoints)現有的網路及網際網路輸出基礎結構。

某些評估會表示網路連線至 Office 365 需要額外的投資在網路的元件。例如投資在 WAN 頻寬或最佳化路由的基礎結構以支援透過網際網路連線到 Office 365。有時會評估會表示網路連線至 Office 365 會影響法規或效能需求例如[Skype 商務線上媒體品質](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)的案例。投資在網際網路連線基礎結構、 傳閱最佳化與特定的直接連線可能會導致下列額外需求。
  
> [!NOTE]
> Microsoft 變更 Microsoft Peering 路由網域檢閱的 Azure ExpressRoute 的方式。啟動 2017 年 7 月 31 所有 Azure ExpressRoute 客戶可以都啟用 Microsoft Peering Azure 系統管理主控台從直接或透過 PowerShell。啟用 Microsoft Peering 之後, 任何客戶可以建立路由篩選器以接收 BGP 路由廣告 Dynamics 365 客戶參與應用程式 （前身為 CRM Online）。他們可以建立路由篩選 for Office 365 之前需要 Azure ExpressRoute for Office 365 的客戶必須從 Microsoft 取得檢閱。請連絡您的 Microsoft 帳戶小組來了解如何要求啟用 Office 365 ExpressRoute 檢閱。未經授權的訂閱嘗試建立 Office 365 路由篩選將會收到[錯誤訊息](https://support.microsoft.com/kb/3181709)。
  
規劃您網路的評估 Office 365 時需要考量重點：
  
- Office 365 是執行透過公用網際網路的安全、 可靠、 高效能服務。我們繼續投資來加強這些方面的服務。所有的 Office 365 服務是透過網際網路連線能力。

- 我們會持續最佳化的核心方面的 Office 365 例如可用性、 全域到達、 和效能的網際網路連線。例如，許多 Office 365 服務運用網際網路對向 edge 節點展開組。此 edge 網路提供最佳接近度以及傳入透過網際網路連線的效能。

- 當考慮使用 Office 365 任何包含服務例如 Skype 商務線上語音、 視訊、 或會議功能，客戶必須完成的端對端網路評估且符合使用我們 Skype 操作架構的需求。這些客戶會有一些選項以符合雲端連線、 包括 ExpressRoute 的特定需求。

有 Microsoft 的案例研究[的 Microsoft Office 365 的最佳化網路效能](https://msdn.microsoft.com/en-us/library/mt450488.aspx)的資訊。如果您正在評估 Office 365，則不是確定網路評估的開頭或網路設計時所發現的位置質詢您需要取得協助若要克服，請使用 Microsoft 帳戶小組。
  
此外，請閱讀[Office 365 網路連線準則](https://aka.ms/o365networkingprinciples)了安全地管理 Office 365 流量和快速獲得最佳效能連線原則。本文可協助您了解可安全地最佳化 Office 365 網路連線的最新的指引。
  
以下是您可以使用回來的簡短連結： [ https://aka.ms/o365networkconnectivity。](https://aka.ms/o365networkconnectivity)
  
## <a name="see-also"></a>另請參閱

[管理 Office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Office 365 端點常見問題集](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
  
[Office 365 網路和效能調整](network-planning-and-performance.md)
  
[Azure ExpressRoute for Office 365](azure-expressroute.md)
  
[使用 ExpressRoute for Office 365 進行路由傳送](routing-with-expressroute.md)
  
[使用 ExpressRoute for Office 365 進行網路規劃](network-planning-with-expressroute.md)
  
[使用 Office 365 案例 （預覽） ExpressRoute BGP 社群 （英文）](bgp-communities-in-expressroute.md)
  
[媒體品質和 Skype 的線上商務的網路連線效能](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Office 365 URL 與 IP 位址範圍](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 網路連線原則](https://aka.ms/o365networkingprinciples)
