---
title: Office 365 網路評估（預覽）
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/04/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Office 365 網路評估（預覽）
ms.openlocfilehash: 24ecea73d9ecb6ae73b26e42a25749c846e3a281
ms.sourcegitcommit: 1c3aa0654336acec14098241f785ea1d8c6caf50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "42890356"
---
# <a name="office-365-network-assessment-preview"></a><span data-ttu-id="911cf-103">Office 365 網路評估（預覽）</span><span class="sxs-lookup"><span data-stu-id="911cf-103">Office 365 network assessment (preview)</span></span>

<span data-ttu-id="911cf-104">在 Microsoft 365 系統管理中心連線至 Microsoft 365 頁面時，**網路評估**會將許多網路效能度量的匯總，提煉成商業網路健康情況的快照，以點值從 1-100 來表示。</span><span class="sxs-lookup"><span data-stu-id="911cf-104">In the Microsoft 365 Admin Center's Connectivity to Microsoft 365 page, **network assessments** distill an aggregate of many network performance metrics into a snapshot of your enterprise network health, represented by a points value from 1 - 100.</span></span> <span data-ttu-id="911cf-105">網路評估同時適用于整個承租人和每個地理位置，使用者會從該位置連線到您的租使用者，並提供 Office 365 系統管理員輕鬆地抓住商業網路健康情況的 gestalt，並快速進行鑽取的方式向內移動至任何全球辦公室位置的詳細報告。</span><span class="sxs-lookup"><span data-stu-id="911cf-105">Network assessments are scoped to both the entire tenant and for each geographic location from which users connect to your tenant, providing Office 365 administrators with an easy way to instantly grasp a gestalt of the enterprise's network health and quickly drill down into a detailed report for any global office location.</span></span>

<span data-ttu-id="911cf-106">網路評估點值是在查看時所整理的延遲、頻寬、下載速度及連線品質度量平均測量值。</span><span class="sxs-lookup"><span data-stu-id="911cf-106">The network assessment points value is an average measurement of latency, bandwidth, download speed and connection quality metrics compiled live at the time they are viewed.</span></span> <span data-ttu-id="911cf-107">Microsoft 所擁有網路的效能度量會從這些測量值中排除，以確保評估結果對於公司網路明確且特定。</span><span class="sxs-lookup"><span data-stu-id="911cf-107">Performance metrics for Microsoft-owned networks are excluded from these measurements to ensure that assessment results are unambiguous and specific to the corporate network.</span></span>

![網路評估價值](Media/m365-mac-perf/m365-mac-perf-overview-score-top.png)

<span data-ttu-id="911cf-109">「非常低的網路評估」價值會建議 Office 365 用戶端在連線至租使用者時發生重大問題，或維持回應的使用者體驗，而高值則表示設定正確的網路，且持續效能很低問題。</span><span class="sxs-lookup"><span data-stu-id="911cf-109">A very low network assessment value suggests that Office 365 clients will have significant problems connecting to the tenant or maintaining a responsive user experience, while a high value indicates a properly configured network with few ongoing performance issues.</span></span> <span data-ttu-id="911cf-110">80% 的值代表正常的基準，您不應預期會因網路效能而收到有關 Office 365 連線或回應回應的一般使用者意見。</span><span class="sxs-lookup"><span data-stu-id="911cf-110">A value of 80% represents a healthy baseline where you should not expect to receive regular user complaints about Office 365 connectivity or responsiveness due to network performance.</span></span> <span data-ttu-id="911cf-111">隨著重複網路連線能力的增強，此值會隨著使用者經驗而增加。</span><span class="sxs-lookup"><span data-stu-id="911cf-111">As iterative network connectivity improvements are made, this value will increase along with user experience.</span></span>

>[!IMPORTANT]
><span data-ttu-id="911cf-112">Microsoft 365 系統管理中心的網路洞察力、效能建議和評估目前處於預覽狀態，只適用于已在功能預覽計畫中註冊的 Office 365 承租人。</span><span class="sxs-lookup"><span data-stu-id="911cf-112">Network insights, performance recommendations and assessments in the Microsoft 365 Admin Center is currently in preview status, and is only available for Office 365 tenants that have been enrolled in the feature preview program.</span></span>

## <a name="network-assessment-panel"></a><span data-ttu-id="911cf-113">網路評估面板</span><span class="sxs-lookup"><span data-stu-id="911cf-113">Network assessment panel</span></span>

<span data-ttu-id="911cf-114">每個網路評估，不論是限定在租使用者或特定辦公室位置，都會顯示一個包含評估詳細資料的面板。</span><span class="sxs-lookup"><span data-stu-id="911cf-114">Each network assessment, whether scoped to the tenant or to a specific office location, shows a panel with details about the assessment.</span></span> <span data-ttu-id="911cf-115">這個面板顯示評估的橫條圖，其百分比和每個元件工作負載的總點數，包括只接收度量資料的工作負載。</span><span class="sxs-lookup"><span data-stu-id="911cf-115">This panel shows a bar chart of the assessment both as a percentage and as the total points for each component workload including only workloads where measurement data was received.</span></span> <span data-ttu-id="911cf-116">若為 office 位置網路評估，我們也會顯示一個基準，此基準是在相同城市中報告與您辦公室位置之資料的所有 Office 365 用戶端。</span><span class="sxs-lookup"><span data-stu-id="911cf-116">For an office location network assessment, we also show a benchmark which is the median of all Office 365 clients that reported data in the same city as your office location.</span></span>

![範例網路評估價值](Media/m365-mac-perf/m365-mac-perf-overview-score.png)

<span data-ttu-id="911cf-118">面板中的**評估分解**會顯示每個元件工作負載的評估。</span><span class="sxs-lookup"><span data-stu-id="911cf-118">The **Assessment breakdown** in the panel shows the assessment for each of the component workloads.</span></span>

<span data-ttu-id="911cf-119">**評估記錄**會顯示過去30天的評估和基準。</span><span class="sxs-lookup"><span data-stu-id="911cf-119">The **Assessment history** shows the past 30 days of the assessment and the benchmark.</span></span>

## <a name="tenant-network-assessments-and-office-location-network-assessments"></a><span data-ttu-id="911cf-120">租使用者網路評估與 office 位置網路評估</span><span class="sxs-lookup"><span data-stu-id="911cf-120">Tenant network assessments and office location network assessments</span></span>

<span data-ttu-id="911cf-121">網路評估會將辦公位置的網路周邊環境設計，評定為 Microsoft 的網路。</span><span class="sxs-lookup"><span data-stu-id="911cf-121">A network assessment measures the design of the network perimeter of an office location to Microsoft’s network.</span></span> <span data-ttu-id="911cf-122">對網路周邊的增強功能最適合於每個辦公室位置，或會影響多個位置的增強功能。</span><span class="sxs-lookup"><span data-stu-id="911cf-122">Improvements to the network perimeter is best done at each office location, or where network connectivity is aggregated there may be improvements that impact multiple locations.</span></span>

<span data-ttu-id="911cf-123">我們會在 [網路效能一覽表] 頁面上，顯示整個 Office 365 租使用者的網路評估值，以及該位置 [摘要] 頁面上每個偵測到之 Office 位置的特定值。</span><span class="sxs-lookup"><span data-stu-id="911cf-123">We show a network assessment value for the whole Office 365 tenant on the network performance overview page and a specific value for each detected office location on that location’s summary page.</span></span>

## <a name="exchange-online"></a><span data-ttu-id="911cf-124">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="911cf-124">Exchange Online</span></span>

<span data-ttu-id="911cf-125">針對 Exchange Online，從用戶端電腦到 Exchange 前端伺服器的 TCP 延遲是測量。</span><span class="sxs-lookup"><span data-stu-id="911cf-125">For Exchange Online the TCP latency from the client machine to the Exchange front end server is measured.</span></span> <span data-ttu-id="911cf-126">這可能會受到網路透過客戶局域網和 WAN 的距離所影響。</span><span class="sxs-lookup"><span data-stu-id="911cf-126">This can be impacted by the distance the network travels over the customers LAN and WAN.</span></span> <span data-ttu-id="911cf-127">這種情況也可能會受到網路仲介裝置或服務的影響，以延遲連線或造成封包重發。</span><span class="sxs-lookup"><span data-stu-id="911cf-127">It can also be impacted by network intermediary devices or services which delay the connectivity or cause packets to be resent.</span></span>

## <a name="sharepoint-online"></a><span data-ttu-id="911cf-128">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="911cf-128">SharePoint Online</span></span>

<span data-ttu-id="911cf-129">針對 SharePoint 線上，可供使用者存取檔的下載速度進行度量。</span><span class="sxs-lookup"><span data-stu-id="911cf-129">For SharePoint Online the download speed available for a user to access a document is measured.</span></span> <span data-ttu-id="911cf-130">這可能會受到用戶端電腦與 Microsoft 網路之間網路環路上可用頻寬的影響。</span><span class="sxs-lookup"><span data-stu-id="911cf-130">This can be impacted by the bandwidth available on network circuits between the client machine and Microsoft’s network.</span></span> <span data-ttu-id="911cf-131">這通常是因為網路擁塞存在於複雜網路裝置或不良覆蓋 Wi-Fi 區域中的網路擁塞所影響。</span><span class="sxs-lookup"><span data-stu-id="911cf-131">It is also often impacted by network congestion that exists in bottlenecks in complex network devices or in poor coverage Wi-Fi areas.</span></span>

## <a name="microsoft-teams"></a><span data-ttu-id="911cf-132">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="911cf-132">Microsoft Teams</span></span>

<span data-ttu-id="911cf-133">針對 Microsoft 小組，網路品質是指 UDP 延遲、UDP 抖動及 UDP 封包遺失。</span><span class="sxs-lookup"><span data-stu-id="911cf-133">For Microsoft Teams the Network quality is measured as UDP latency, UDP jitter, and UDP packet loss.</span></span> <span data-ttu-id="911cf-134">UDP 可用於 Microsoft 小組的通話和會議音訊和影片媒體連線。</span><span class="sxs-lookup"><span data-stu-id="911cf-134">UDP is used for call and conferencing audio and video media connectivity for Microsoft Teams.</span></span> <span data-ttu-id="911cf-135">這可能會受到延遲和下載速度相同的因素所影響，除了 UDP 是分別設定為較為常見的 TCP 通訊協定以外，其他情況也是在網路的 UDP 支援中使用網路中斷性。</span><span class="sxs-lookup"><span data-stu-id="911cf-135">This can be impacted by the same factors as for latency and download speed in addition to connectivity gaps in a network’s UDP support since UDP is configured separately to the more common TCP protocol.</span></span>

## <a name="related-topics"></a><span data-ttu-id="911cf-136">相關主題</span><span class="sxs-lookup"><span data-stu-id="911cf-136">Related topics</span></span>

[<span data-ttu-id="911cf-137">Microsoft 365 系統管理中心的網路效能建議（預覽）</span><span class="sxs-lookup"><span data-stu-id="911cf-137">Network performance recommendations in the Microsoft 365 Admin Center (preview)</span></span>](office-365-network-mac-perf-overview.md)

[<span data-ttu-id="911cf-138">Office 365 網路效能深入瞭解（預覽）</span><span class="sxs-lookup"><span data-stu-id="911cf-138">Office 365 network performance insights (preview)</span></span>](office-365-network-mac-perf-insights.md)

[<span data-ttu-id="911cf-139">M365 系統管理中心的 Office 365 網路上架工具（預覽）</span><span class="sxs-lookup"><span data-stu-id="911cf-139">Office 365 Network Onboarding Tool in the M365 Admin Center (preview)</span></span>](office-365-network-mac-perf-onboarding-tool.md)

[<span data-ttu-id="911cf-140">Office 365 網路洞察力隱私權和使用條款（預覽）</span><span class="sxs-lookup"><span data-stu-id="911cf-140">Office 365 Network Insights Privacy and Terms of Use (preview)</span></span>](office-365-network-mac-perf-privacy.md)
