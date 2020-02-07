---
title: Office 365 防禦拒絕服務攻擊的核心原則
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: 如何使用 Microsoft 利用吸收、 偵測和補救中其防禦拒絕服務 (DoS) 攻擊的核心原則。
ms.openlocfilehash: 82957dd1b863e14c13e86b63888e2b1374beb73b
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844524"
---
# <a name="core-principles-of-defense-against-denial-of-service-attacks"></a>防禦拒絕服務攻擊的核心原則

三個核心原則時防禦網路型 DoS 攻擊吸收、 偵測和補救。 吸收會發生情況之前偵測，以及偵測緩和措施之前發生。 吸收是 DoS 攻擊的最佳防範。 如果無法偵測到的攻擊，它不能降低。 但是，如果無法相同甚至是最小的 DoS 攻擊的命運，然後服務不會學到承受長，才能偵測到攻擊。

它不是經濟可行的情況下用於大多數的組織購買過多的容量，以吸收 DoS 攻擊，因為這需要相當長的投資的技術和專門技術。 這會醒目提示使用 Microsoft 雲端服務的安全性優點之一。 Microsoft 服務的真正的縮放比例，提供強式網路保護雲端的客戶符合成本效益的方式。 但即使是在大型，必須是吸收、 偵測和補救之間取得平衡。 若要尋找的平衡，Microsoft 研究攻擊來估計多少 Microsoft 需要吸收的成長率。

偵測是 cat-and-mouse 遊戲。 您必須經常尋找人員攻擊並且嘗試擊敗您系統的新方法。 偵測-> 降低-> 偵測-等 > 降低，是會繼續無限期的永久、 持續性狀態。

## <a name="defending-against-dos-attacks"></a>防禦拒絕服務攻擊

成功，以防範 DoS 攻擊，早期偵測是不可或缺的。 藉由之前淹沒了系統偵測攻擊，防禦者可以執行回應計畫。

下列公式可協助大約時間 DoS 攻擊的影響：

   **最大容量 （以位元組/秒） / 成長率 （以位元組/秒） = 影響時間 （以位元組/秒）**

如果要偵測時間發生時間的影響後，它可能是 DoS 攻擊會成功。 如果要偵測時間發生時間-影響之前，受攻擊的服務應保持 online 與減輕策略可用才可存取。 因此，有可執行以抵禦拒絕服務攻擊的只有兩件事：

- 若要引發的最大容量 （可輪流提供更多時間來偵測攻擊）; ceiling 增加容量或
- 減少偵測的時間。

增加容量有直接的會計影響。 Microsoft 建議的客戶開發至少基本吸收容量，以確保它們可以承受某種程度的 DoS 攻擊。 實際吸收容量而異客戶，為每個客戶有自己的曝光度、 風險和財務 outlay 閾值。 基於經濟原因，研究和時間的方式來減少時間-偵測的投資通常是最符合成本效益的措施。
