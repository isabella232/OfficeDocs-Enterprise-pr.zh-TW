---
title: 連線到 Office 365 服務的網路裝置的計劃
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
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
ms.assetid: 073433ca-3511-4db9-b173-7a2edca57691
description: 摘要： 說明的網路容量、 WAN 加速器和負載平衡裝置用來連線到 Office 365 的考量。
ms.openlocfilehash: 2a38fd7dad23b41aa31dcf9ace7ebee6ed69c0f6
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747066"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a>連線到 Office 365 服務的網路裝置的計劃

*本文適用於 Office 365 企業版和 Microsoft 365 企業版。*
  
**摘要**： 說明的網路容量、 WAN 加速器和負載平衡裝置用來連線到 Office 365 的考量。

某些網路硬體可能會有所限制所支援的並行工作階段數目。 針對具有超過 2000 位使用者的組織，建議他們監視其網路裝置，以確保它們能夠處理其他的 Office 365 服務流量。 簡易網路管理通訊協定 (SNMP) 監視軟體可協助您執行這項操作。

||
|:-----|
| 本文是 [Office 365 的網路規劃與效能調整](https://aka.ms/tune)的一部分。|

內部部署的外寄的網際網路 proxy 設定也會影響您的用戶端應用程式的 Office 365 服務的連線。 您也必須設定網路 proxy 裝置以允許 Microsoft 雲端服務 Url 和應用程式的連線。 每個組織是不同。 若要取得了解 Microsoft 如何管理這項程序和頻寬量我們佈建，[讀取案例研究](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365)。
  
下列的 Skype for Business 說明文章有需 Skype for Business 設定的詳細資訊：
  
- [疑難排解商務用 Skype 系統管理員的商務 Online 登入錯誤](https://docs.microsoft.com/skypeforbusiness/set-up-skype-for-business-online/troubleshooting-sign-in-errors-for-admins)

- [您無法連線至商務用 Skype 或某些功能無法運作，因為內部部署防火牆封鎖連線](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> 許多這些設定都是特定的商務用 Skype，網路設定的一般指導方針是適用於所有 Office 365 服務。
  
## <a name="determining-network-capacity"></a>判斷網路容量

每一個連接存在的網路裝置有其容量限制。 這些裝置包括用戶端和伺服器網路介面卡、 路由器、 交換器及 interconnect 它們的中樞。 適當的網路容量表示沒有任何一個它們飽和。 監控網路活動是以協助確保所有的網路裝置上實際負載有小於其最大的容量。 網路容量影響 proxy 裝置的效能。
  
在大部分情況下，網際網路連線的頻寬設定預設流量的限制。 在尖峰流量時間的弱式效能可能因過度使用的 [網際網路] 連結。 這種情況下也適用於 branch office 案例中，其中 branch office proxy 伺服器電腦會連線至 proxy 裝置的分支總部慢速廣域網路 (WAN) 連結。
  
若要測試的網路容量，監視 proxy 網路介面的網路活動。 如果它的任何網路介面的最大頻寬超過 75%，請考慮增加的頻寬不足的網路基礎結構。 或者，請考慮使用進階的功能，例如 HTTP 壓縮。
  
## <a name="wan-accelerators"></a>WAN 加速器

如果您的組織使用廣域網路 (wan) 加速器 proxy 設備，可能會遇到問題，當您存取 Office 365 服務中。 您可能需要最佳化您的網路裝置或裝置，以確保您的使用者在存取 Office 365 時，會有一致的體驗。 例如，Office 365 服務加密某些 Office 365 內容和 TCP 標頭。 您的裝置可能無法處理這類的流量。
  
閱讀有關[使用 WAN 最佳化控制器或與 Office 365 流量/檢查裝置](https://support.microsoft.com/kb/2690045)我們支援陳述式。
  
## <a name="hardware-and-software-load-balancing-devices"></a>硬體與軟體負載平衡裝置

您的組織需要使用硬體負載平衡器 (HLB) 或網路負載平衡 (NLB) 解決方案來散發要求至您的 Active Directory Federation Services (AD FS) 伺服器及/或您的 Exchange 混合式伺服器。 負載平衡裝置控制到內部部署伺服器的網路流量。 這些伺服器都很重要，以協助確保單一登入與 Exchange 混合式部署的可用性。
  
我們將提供內建於 Windows Server 軟體為基礎的 NLB 解決方案。 Office 365 支援此解決方案，以達到負載平衡。
  
## <a name="firewalls-and-proxies"></a>防火牆和 proxy

如需設定防火牆和 proxy 連線至 Office 365，請閱讀[管理 Office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)、[評估 Office 365 網路連線](assessing-network-connectivity.md)性和[Office 365 端點常見問題集](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)若要深入了解裝置和電路選取範圍的詳細資訊。
  
## <a name="see-also"></a>請參閱

[Office 365 服務的部署建議程式](deployment-advisors-for-office-365.md)

[Microsoft 365 企業版概觀](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
