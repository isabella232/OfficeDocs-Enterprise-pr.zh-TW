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
# <a name="core-principles-of-defense-against-denial-of-service-attacks"></a><span data-ttu-id="2c26f-103">防禦拒絕服務攻擊的核心原則</span><span class="sxs-lookup"><span data-stu-id="2c26f-103">Core Principles of Defense Against Denial-of-Service Attacks</span></span>

<span data-ttu-id="2c26f-104">三個核心原則時防禦網路型 DoS 攻擊吸收、 偵測和補救。</span><span class="sxs-lookup"><span data-stu-id="2c26f-104">The three core principles when defending against network-based DoS attacks are Absorption, Detection, and Mitigation.</span></span> <span data-ttu-id="2c26f-105">吸收會發生情況之前偵測，以及偵測緩和措施之前發生。</span><span class="sxs-lookup"><span data-stu-id="2c26f-105">Absorption happens before detection, and detection happens before mitigation.</span></span> <span data-ttu-id="2c26f-106">吸收是 DoS 攻擊的最佳防範。</span><span class="sxs-lookup"><span data-stu-id="2c26f-106">Absorption is the best defense against a DoS attack.</span></span> <span data-ttu-id="2c26f-107">如果無法偵測到的攻擊，它不能降低。</span><span class="sxs-lookup"><span data-stu-id="2c26f-107">If the attack can't be detected, it can't be mitigated.</span></span> <span data-ttu-id="2c26f-108">但是，如果無法相同甚至是最小的 DoS 攻擊的命運，然後服務不會學到承受長，才能偵測到攻擊。</span><span class="sxs-lookup"><span data-stu-id="2c26f-108">But if even the smallest DoS attack can't be absorbed, then services aren't going to survive long enough for the attack to be detected.</span></span>

<span data-ttu-id="2c26f-109">它不是經濟可行的情況下用於大多數的組織購買過多的容量，以吸收 DoS 攻擊，因為這需要相當長的投資的技術和專門技術。</span><span class="sxs-lookup"><span data-stu-id="2c26f-109">It is not economically feasible for most organizations to purchase excess capacity to absorb DoS attacks, as this requires a considerable investment in technology and technical skills.</span></span> <span data-ttu-id="2c26f-110">這會醒目提示使用 Microsoft 雲端服務的安全性優點之一。</span><span class="sxs-lookup"><span data-stu-id="2c26f-110">This highlights one of the security benefits of using Microsoft cloud services.</span></span> <span data-ttu-id="2c26f-111">Microsoft 服務的真正的縮放比例，提供強式網路保護雲端的客戶符合成本效益的方式。</span><span class="sxs-lookup"><span data-stu-id="2c26f-111">The sheer scale of Microsoft services provides strong network protection to cloud customers in a cost-effective manner.</span></span> <span data-ttu-id="2c26f-112">但即使是在大型，必須是吸收、 偵測和補救之間取得平衡。</span><span class="sxs-lookup"><span data-stu-id="2c26f-112">But even at a large scale, there must be a balance between absorption, detection, and mitigation.</span></span> <span data-ttu-id="2c26f-113">若要尋找的平衡，Microsoft 研究攻擊來估計多少 Microsoft 需要吸收的成長率。</span><span class="sxs-lookup"><span data-stu-id="2c26f-113">To find that balance, Microsoft studies attack growth rates to estimate how much Microsoft needs to absorb.</span></span>

<span data-ttu-id="2c26f-114">偵測是 cat-and-mouse 遊戲。</span><span class="sxs-lookup"><span data-stu-id="2c26f-114">Detection is a cat-and-mouse game.</span></span> <span data-ttu-id="2c26f-115">您必須經常尋找人員攻擊並且嘗試擊敗您系統的新方法。</span><span class="sxs-lookup"><span data-stu-id="2c26f-115">You must constantly look for new ways people are attack and try to defeat your systems.</span></span> <span data-ttu-id="2c26f-116">偵測-> 降低-> 偵測-等 > 降低，是會繼續無限期的永久、 持續性狀態。</span><span class="sxs-lookup"><span data-stu-id="2c26f-116">Detect -> Mitigate -> Detect -> Mitigate, etc., is a perpetual, persistent state that continues indefinitely.</span></span>

## <a name="defending-against-dos-attacks"></a><span data-ttu-id="2c26f-117">防禦拒絕服務攻擊</span><span class="sxs-lookup"><span data-stu-id="2c26f-117">Defending Against DoS Attacks</span></span>

<span data-ttu-id="2c26f-118">成功，以防範 DoS 攻擊，早期偵測是不可或缺的。</span><span class="sxs-lookup"><span data-stu-id="2c26f-118">To successfully defend against a DoS attack, early detection is essential.</span></span> <span data-ttu-id="2c26f-119">藉由之前淹沒了系統偵測攻擊，防禦者可以執行回應計畫。</span><span class="sxs-lookup"><span data-stu-id="2c26f-119">By detecting an attack before the system is overwhelmed, defenders can execute a response plan.</span></span>

<span data-ttu-id="2c26f-120">下列公式可協助大約時間 DoS 攻擊的影響：</span><span class="sxs-lookup"><span data-stu-id="2c26f-120">The following formula helps approximate the time to impact of a DoS attack:</span></span>

   <span data-ttu-id="2c26f-121">**最大容量 （以位元組/秒） / 成長率 （以位元組/秒） = 影響時間 （以位元組/秒）**</span><span class="sxs-lookup"><span data-stu-id="2c26f-121">**Maximum Capacity (in bytes/sec) / Growth Rate (in bytes/sec) = Time to Impact (in bytes/sec)**</span></span>

<span data-ttu-id="2c26f-122">如果要偵測時間發生時間的影響後，它可能是 DoS 攻擊會成功。</span><span class="sxs-lookup"><span data-stu-id="2c26f-122">If the time-to-detection occurs after time-to-impact, it is likely the DoS attack will be successful.</span></span> <span data-ttu-id="2c26f-123">如果要偵測時間發生時間-影響之前，受攻擊的服務應保持 online 與減輕策略可用才可存取。</span><span class="sxs-lookup"><span data-stu-id="2c26f-123">If the time-to-detection occurs before time-to-impact, the attacked services should remain online and accessible if mitigation strategies are used.</span></span> <span data-ttu-id="2c26f-124">因此，有可執行以抵禦拒絕服務攻擊的只有兩件事：</span><span class="sxs-lookup"><span data-stu-id="2c26f-124">Thus, there are only two things that can be done to defend against DoS attacks:</span></span>

- <span data-ttu-id="2c26f-125">若要引發的最大容量 （可輪流提供更多時間來偵測攻擊）; ceiling 增加容量或</span><span class="sxs-lookup"><span data-stu-id="2c26f-125">Increase capacity to raise the ceiling of maximum capacity (which in turn provides more time to detect an attack); or</span></span>
- <span data-ttu-id="2c26f-126">減少偵測的時間。</span><span class="sxs-lookup"><span data-stu-id="2c26f-126">Decrease the time to detect.</span></span>

<span data-ttu-id="2c26f-127">增加容量有直接的會計影響。</span><span class="sxs-lookup"><span data-stu-id="2c26f-127">Increasing capacity has a direct fiscal impact.</span></span> <span data-ttu-id="2c26f-128">Microsoft 建議的客戶開發至少基本吸收容量，以確保它們可以承受某種程度的 DoS 攻擊。</span><span class="sxs-lookup"><span data-stu-id="2c26f-128">Microsoft recommends that customers develop at least basic absorption capacity to ensure that they can survive some level of DoS attack.</span></span> <span data-ttu-id="2c26f-129">實際吸收容量而異客戶，為每個客戶有自己的曝光度、 風險和財務 outlay 閾值。</span><span class="sxs-lookup"><span data-stu-id="2c26f-129">The actual absorption capacity varies from customer to customer, as each customer has their own thresholds for exposure, risk, and financial outlay.</span></span> <span data-ttu-id="2c26f-130">基於經濟原因，研究和時間的方式來減少時間-偵測的投資通常是最符合成本效益的措施。</span><span class="sxs-lookup"><span data-stu-id="2c26f-130">For economic reasons, investments in research and time for ways to decrease time-to-detection are usually the most cost-effective defense.</span></span>
