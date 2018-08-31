---
title: 連線到 Office 365 服務的網路裝置的計劃
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
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
ms.assetid: 073433ca-3511-4db9-b173-7a2edca57691
description: 摘要：說明連線到 Office 365 時所用之網路容量、WAN 加速器和負載平衡裝置的注意事項。
ms.openlocfilehash: c384ba043e64ec83eda74b234937efaf72f29815
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223065"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a>連線到 Office 365 服務的網路裝置的計劃

 **摘要**：說明連線到 Office 365 時所用之網路容量、WAN 加速器和負載平衡裝置的注意事項。
  
某些網路硬體可能會有限制同時支援的工作階段的數目而定。對於擁有超過 2000 位使用者的組織而言，我們建議他們監視網路裝置以確保它們能夠處理的其他 Office 365 服務流量。簡易網路管理通訊協定 (SNMP) 監視軟體可協助您達成此目的。

||
|:-----|
| 本文是[網路規劃和 Office 365 的效能調整](https://aka.ms/tune)的一部分。|

內部傳出網際網路 proxy 設定也會影響連線到 Office 365 服務的用戶端應用程式。您也必須設定網路 proxy 裝置，允許 Microsoft 雲端服務 Url 和應用程式的連線。每個組織的不同。若要取得 Microsoft 管理此程序及頻寬量的方式粗略我們佈建、[讀取案例研究](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365)。
  
商務說明文章的下列 Skype 具備商務設定 Skype 的詳細資訊：
  
- [疑難排解 Skype 商務登入錯誤 （管理員）](https://go.microsoft.com/fwlink/p/?LinkID=243624)

- [您無法連線至 Skype for Business，或某些功能無法運作，因為在內部部署防火牆封鎖連線](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> 雖然這些設定的許多商務特有的 Skype，網路設定的一般指導的適用於所有的 Office 365 服務。
  
## <a name="determining-network-capacity"></a>判斷網路容量

連線上存在的每一個網路裝置都有自己的容量限制。這些裝置包括用戶端與伺服器，以及將其互連的網路介面卡、路由器、交換器和集線器。適當的網路容量是指以上裝置都尚未飽和。監視網路活動是確保所有網路裝置的實際負載低於其最高容量的必要工作。網路容量會影響 Proxy 裝置的效能。
  
在大多數情況下，網際網路連線的頻寬設定預設流量限制。弱式離峰流量的效能可能造成過度使用的 [網際網路] 連結。Branch office proxy 伺服器電腦連線到 proxy 裝置在該分支 headquarters 透過慢速廣域網路 (WAN) 連結其中 branch office 案例也適用於此情況。
  
若要測試的網路容量，監視上 proxy 網路介面的網路活動。如果是多個 75%的任何網路介面的最大頻寬，請考慮增加不足的網路基礎結構的頻寬。或者，請考慮使用進階的功能，例如 HTTP 壓縮。
  
## <a name="wan-accelerators"></a>廣域網路 (WAN) 加速器

如果貴組織使用廣域網路 (wan) 加速 proxy 設備、 存取 Office 365 服務時可能會遇到問題。您可能需要最佳化您的網路裝置或裝置能夠確定您的使用者存取 Office 365 時有一致的體驗。例如，Office 365 服務加密某些 Office 365 內容和 TCP 標頭。您的裝置可能無法處理這種流量。
  
閱讀有關[使用 WAN 的最佳化控制器或流量/檢查裝置搭配 Office 365](https://support.microsoft.com/kb/2690045)我們支援陳述式。
  
## <a name="hardware-and-software-load-balancing-devices"></a>硬體和軟體負載平衡裝置

您的組織需要使用硬體負載平衡器 (HLB) 或網路負載平衡 (NLB) 解決方案，以將要求發佈至 Active Directory Federation Services (AD FS) 伺服器和/或 Exchange 混合伺服器。負載平衡裝置會控制前往內部部署伺服器的網路流量。這些伺服器對於確保單一登入和 Exchange 混合部署的可用性很重要。
  
我們提供內建於 Windows Server 軟體為基礎的 NLB 解決方案。Office 365 支援此解決方案以達到負載平衡。
  
## <a name="firewalls-and-proxies"></a>防火牆及 proxy

如需設定防火牆及 proxy 連線至 Office 365，請閱讀[管理 Office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)、[網路連線至 Office 365](network-connectivity.md)和[Office 365 端點常見問題集](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)若要深入了解裝置和電路選取範圍的詳細資訊。
  
## <a name="see-also"></a>另請參閱

[Office 365 服務的部署建議](deployment-advisors-for-office-365.md)
