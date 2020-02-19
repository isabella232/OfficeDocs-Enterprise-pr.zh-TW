---
title: Office 365 網路評估 （預覽）
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 02/04/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Office 365 網路評估 （預覽）
ms.openlocfilehash: f919eeb2771095502865b4a5079b91eb8d7efe36
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106281"
---
# <a name="office-365-network-assessment-preview"></a><span data-ttu-id="c5bf8-103">Office 365 網路評估 （預覽）</span><span class="sxs-lookup"><span data-stu-id="c5bf8-103">Office 365 network assessment (preview)</span></span>

<span data-ttu-id="c5bf8-104">Office 365 網路評估會指出從客戶網路連線相對的使用者體驗的影響。</span><span class="sxs-lookup"><span data-stu-id="c5bf8-104">The Office 365 network assessment indicates the relative user experience impact from customer network connectivity.</span></span> <span data-ttu-id="c5bf8-105">任何 Microsoft 的影響所擁有的網路連線能力排除此選項可讓客戶能夠最佳化他們所負責的網路設計。</span><span class="sxs-lookup"><span data-stu-id="c5bf8-105">The impact of any Microsoft owned network connectivity is excluded from this to enable customers to optimize network designs for which they are responsible.</span></span>

<span data-ttu-id="c5bf8-106">它是影響使用者經驗中重要的 Office 365 工作負載的度量單位從計算並顯示為 0 到 100 個範圍的百分比表示。</span><span class="sxs-lookup"><span data-stu-id="c5bf8-106">It is calculated from measurements that impact user experience in key Office 365 workloads and shown as a percentage with a range of 0 to 100.</span></span>

<span data-ttu-id="c5bf8-107">非常低的網路分數建議 Office 365 用戶端會有連線或剩餘使用者回應的重大問題。</span><span class="sxs-lookup"><span data-stu-id="c5bf8-107">A very low network score suggests that Office 365 clients will have significant problems connecting or remaining user responsive.</span></span> <span data-ttu-id="c5bf8-108">分數的 80%表示網路連線，您應該不預期會有接收使用者抱怨您的 Office 365 使用者體驗由於網路效能。</span><span class="sxs-lookup"><span data-stu-id="c5bf8-108">A score of 80% represents network connectivity where you should not expect to receive user complaints about your Office 365 user experience due to your network performance.</span></span> <span data-ttu-id="c5bf8-109">對網路連線能力增強功能，此分數會增加以及使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="c5bf8-109">As network connectivity improvements are made, this score will increase along with user experience.</span></span>

>[!IMPORTANT]
><span data-ttu-id="c5bf8-110">網路效能建議、 深入了解 Microsoft 365 系統管理中心中的評估目前處於預覽狀態，並只適用於具有已註冊功能預覽計畫的 Office 365 租用戶。</span><span class="sxs-lookup"><span data-stu-id="c5bf8-110">Network performance recommendations, insights and assessments in the Microsoft 365 Admin Center is currently in preview status, and is only available for Office 365 tenants that have been enrolled in the feature preview program.</span></span>

## <a name="exchange-online"></a><span data-ttu-id="c5bf8-111">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="c5bf8-111">Exchange Online</span></span>

<span data-ttu-id="c5bf8-112">Exchange online TCP 被測量至 Exchange 前端伺服器與用戶端機器延遲。</span><span class="sxs-lookup"><span data-stu-id="c5bf8-112">For Exchange Online the TCP latency from the client machine to the Exchange front end server is measured.</span></span> <span data-ttu-id="c5bf8-113">這會受到網路，透過 LAN 及 WAN 的客戶的距離。</span><span class="sxs-lookup"><span data-stu-id="c5bf8-113">This can be impacted by the distance the network travels over the customers LAN and WAN.</span></span> <span data-ttu-id="c5bf8-114">它可以也會受到網路介裝置或服務延遲連線或會造成重新傳送的封包。</span><span class="sxs-lookup"><span data-stu-id="c5bf8-114">It can also be impacted by network intermediary devices or services which delay the connectivity or cause packets to be resent.</span></span>

## <a name="sharepoint-online"></a><span data-ttu-id="c5bf8-115">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="c5bf8-115">SharePoint Online</span></span>

<span data-ttu-id="c5bf8-116">SharePoint Online 的計算，供使用者存取的文件的下載速度。</span><span class="sxs-lookup"><span data-stu-id="c5bf8-116">For SharePoint Online the download speed available for a user to access a document is measured.</span></span> <span data-ttu-id="c5bf8-117">這可以在用戶端電腦與 Microsoft 的網路之間的網路電路上可用的頻寬受到影響。</span><span class="sxs-lookup"><span data-stu-id="c5bf8-117">This can be impacted by the bandwidth available on network circuits between the client machine and Microsoft’s network.</span></span> <span data-ttu-id="c5bf8-118">通常也會受到網路壅塞存在於中不佳的涵蓋範圍 Wi-fi 區域或複雜的網路裝置中的瓶頸。</span><span class="sxs-lookup"><span data-stu-id="c5bf8-118">It is also often impacted by network congestion that exists in bottlenecks in complex network devices or in poor coverage Wi-Fi areas.</span></span>

## <a name="microsoft-teams"></a><span data-ttu-id="c5bf8-119">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="c5bf8-119">Microsoft Teams</span></span>

<span data-ttu-id="c5bf8-120">對於 Microsoft Teams 的網路品質被測量 UDP 延遲、 UDP 抖動和 UDP 封包遺失。</span><span class="sxs-lookup"><span data-stu-id="c5bf8-120">For Microsoft Teams the Network quality is measured as UDP latency, UDP jitter, and UDP packet loss.</span></span> <span data-ttu-id="c5bf8-121">UDP 用於通話和會議的音訊和視訊媒體連線，對於 Microsoft Teams。</span><span class="sxs-lookup"><span data-stu-id="c5bf8-121">UDP is used for call and conferencing audio and video media connectivity for Microsoft Teams.</span></span> <span data-ttu-id="c5bf8-122">這會受到與除了網路 UDP 支援的連線間隔的延遲和下載速度的相同因素自 UDP 分別設定為較常見的 TCP 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="c5bf8-122">This can be impacted by the same factors as for latency and download speed in addition to connectivity gaps in a network’s UDP support since UDP is configured separately to the more common TCP protocol.</span></span>

## <a name="tenant-network-score-and-office-location-network-score"></a><span data-ttu-id="c5bf8-123">租用戶網路分數和辦公室位置網路分數</span><span class="sxs-lookup"><span data-stu-id="c5bf8-123">Tenant network score and office location network score</span></span>

<span data-ttu-id="c5bf8-124">網路分數測量的周邊網路與 Microsoft 的網路辦公室位置的設計。</span><span class="sxs-lookup"><span data-stu-id="c5bf8-124">A network score measures the design of the network perimeter of an office location to Microsoft’s network.</span></span> <span data-ttu-id="c5bf8-125">在每個辦公室的位置，最好的做法周邊網路的改善，是或其中彙總的網路連線可能會影響多個位置的增強功能。</span><span class="sxs-lookup"><span data-stu-id="c5bf8-125">Improvements to the network perimeter is best done at each office location, or where network connectivity is aggregated there may be improvements that impact multiple locations.</span></span>
<span data-ttu-id="c5bf8-126">我們會顯示在 [網路效能概觀] 頁面上整個的 Office 365 租用戶的網路分數並在該位置的摘要] 頁面上每個偵測到的辦公室位置的特定網路分數。</span><span class="sxs-lookup"><span data-stu-id="c5bf8-126">We show a network score for the whole Office 365 tenant on the network performance overview page and a specific network score for each detected office location on that location’s summary page.</span></span>

## <a name="network-score-panel"></a><span data-ttu-id="c5bf8-127">網路分數面板</span><span class="sxs-lookup"><span data-stu-id="c5bf8-127">Network score panel</span></span>

<span data-ttu-id="c5bf8-128">是否針對租用戶或特定 office 位置會顯示與詳細資料，分數的面板，每個網路分數。</span><span class="sxs-lookup"><span data-stu-id="c5bf8-128">Each network score whether for the tenant or for a specific office location shows a panel with details about the score.</span></span> <span data-ttu-id="c5bf8-129">此面板顯示分數的橫條圖的百分比，為每個元件工作負載，包括僅工作負載的總點收到度量單位的資料。</span><span class="sxs-lookup"><span data-stu-id="c5bf8-129">This panel shows a bar chart of the score both as a percentage and as the total points for each component workload including only workloads where measurement data was received.</span></span> <span data-ttu-id="c5bf8-130">對於 office 位置網路分數我們也會顯示這是報告中為您的辦公室位置的相同市/鎮資料的所有 Office 365 用戶端的中位數的基準。</span><span class="sxs-lookup"><span data-stu-id="c5bf8-130">For an office location network score we also show a benchmark which is the median of all Office 365 clients that reported data in the same City as your office location.</span></span>

<span data-ttu-id="c5bf8-131">分數分解為面板中的顯示每個元件工作負載的分數。</span><span class="sxs-lookup"><span data-stu-id="c5bf8-131">The score breakdown in the panel shows the score for each of the component workloads.</span></span>

<span data-ttu-id="c5bf8-132">分數歷程記錄會顯示分數和基準在過去 30 天。</span><span class="sxs-lookup"><span data-stu-id="c5bf8-132">The score history shows the past 30 days of the score and the benchmark.</span></span>

## <a name="related-topics"></a><span data-ttu-id="c5bf8-133">相關主題</span><span class="sxs-lookup"><span data-stu-id="c5bf8-133">Related topics</span></span>

[<span data-ttu-id="c5bf8-134">在 Microsoft 365 系統管理中心 （預覽） 的網路效能建議</span><span class="sxs-lookup"><span data-stu-id="c5bf8-134">Network performance recommendations in the Microsoft 365 Admin Center (preview)</span></span>](office-365-network-mac-perf-overview.md)

[<span data-ttu-id="c5bf8-135">Office 365 網路效能觀點 （預覽）</span><span class="sxs-lookup"><span data-stu-id="c5bf8-135">Office 365 network performance insights (preview)</span></span>](office-365-network-mac-perf-insights.md)

[<span data-ttu-id="c5bf8-136">Office 365 網路上架工具 M365 系統管理中心 （預覽）</span><span class="sxs-lookup"><span data-stu-id="c5bf8-136">Office 365 Network Onboarding Tool in the M365 Admin Center (preview)</span></span>](office-365-network-mac-perf-onboarding-tool.md)
