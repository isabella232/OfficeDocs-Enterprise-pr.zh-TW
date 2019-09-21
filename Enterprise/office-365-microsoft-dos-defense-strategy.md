---
title: Office 365 DoS 攻擊防禦策略
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: None
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: Microsoft 的拒絕服務 (DoS) 攻擊防禦策略的概觀。
ms.openlocfilehash: eacfd9d908eb8408d592fc70cd1a888c7c44aff2
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067278"
---
# <a name="office-365-denial-of-service-defense-strategy"></a>Office 365 拒絕服務攻擊防禦策略

Microsoft 的策略，以防範網路為基礎的拒絕服務 (DoS) 攻擊而言是唯一因為我們的規模和全域磁碟使用量。 此擴充允許 Microsoft，以利用策略和技術少數的組織，提供者，或客戶組織可以比對。 DoS 策略的基石是我們全域顯示狀態。 Microsoft 凝聚網際網路提供者、 對等的提供者 （公用和私人），與私人世界各地的公司。 這可讓 Microsoft 重大的網際網路平台服務，並可讓 Microsoft，以跨大型的表面區域吸收攻擊。

指定此獨特性質，Microsoft 會使用偵測和補救跟和大型企業所使用的程序。 透過多個網路邊緣，策略根據偵測和全域分散式緩和措施的區隔。 許多企業使用協力廠商解決方案以偵測並降低在邊緣的攻擊。 Microsoft edge 容量成長，因為它變成清除太低，個別或特定的邊緣任何攻擊的意義。 由於此唯一的組態中，Microsoft 會分隔偵測和補救元件。 Microsoft 會部署多層偵測系統來偵測其飽和度點來攻擊更接近維持在邊緣全域緩和措施。 這項策略可確保我們可以處理多個同時的攻擊。

下列其中一個最有效且低成本的防禦措施採用 microsoft DoS 攻擊會降低服務的攻擊面。 不想要的流量會遭捨棄，而不是分析、 處理，並清除資料內嵌的網路邊緣。

在公用網路的介面，Microsoft 會使用特殊用途安全性裝置防火牆、 網路位址轉譯及 IP 篩選函式。 Microsoft 也會使用全域等於成本多重路徑 (ECMP) 路由。 全域 ECMP 路由是網路架構，以確保達到服務的多個全域路徑。 這些多個路徑，與服務攻擊僅限於攻擊的來源的區域。 其他區域應該受到此類攻擊，使用者會使用其他路徑來連絡這些區域中的服務。 Microsoft 也開發內部 DoS 相互關聯及偵測系統的使用流量資料、 效能評量，以及其他資訊。 這是在 Microsoft Azure，分析資料收集從各種點上 Microsoft 網路中獲得認證的超大型雲端服務與服務。 跨工作負載 DoS 事件回應小組會識別跨小組、 擴大、 準則和吸引各種小組與事件處理的通訊協定的角色和責任。 這些解決方案提供網路為基礎的保護，不受 DoS 攻擊。

最後，最佳化其通訊協定為基礎的臨界值來設定雲端工作負載和頻寬使用量需要唯一保護該工作負載。
