---
title: Office 365 網路效能觀點 （預覽）
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
description: Office 365 網路效能觀點 （預覽）
ms.openlocfilehash: 2e57ffabec5b2172cb36f10135406ddda95bc1c5
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106288"
---
# <a name="office-365-network-performance-insights-preview"></a><span data-ttu-id="90fd2-103">Office 365 網路效能觀點 （預覽）</span><span class="sxs-lookup"><span data-stu-id="90fd2-103">Office 365 network performance insights (preview)</span></span>

<span data-ttu-id="90fd2-104">在 Microsoft 365 系統管理中心網路效能頁會顯示 Office 365 網路 insights，可協助在設計網路周邊的辦公室位置。</span><span class="sxs-lookup"><span data-stu-id="90fd2-104">The Microsoft 365 Admin Center network performance pages show Office 365 network insights which can help in designing network perimeters for your office locations.</span></span> <span data-ttu-id="90fd2-105">有五個可能會顯示每個辦公室地點的特定網路觀點。</span><span class="sxs-lookup"><span data-stu-id="90fd2-105">There are five specific network insights that may be shown for each office location.</span></span>

>[!IMPORTANT]
><span data-ttu-id="90fd2-106">網路效能建議、 深入了解 Microsoft 365 系統管理中心中的評估目前處於預覽狀態，並只適用於具有已註冊功能預覽計畫的 Office 365 租用戶。</span><span class="sxs-lookup"><span data-stu-id="90fd2-106">Network performance recommendations, insights and assessments in the Microsoft 365 Admin Center is currently in preview status, and is only available for Office 365 tenants that have been enrolled in the feature preview program.</span></span>

## <a name="backhauled-network-egress"></a><span data-ttu-id="90fd2-107">Backhauled 網路輸出</span><span class="sxs-lookup"><span data-stu-id="90fd2-107">Backhauled network egress</span></span>

<span data-ttu-id="90fd2-108">從使用者的位置到網路輸出距離大於 500 英哩 （800 公里），這預期會影響效能。</span><span class="sxs-lookup"><span data-stu-id="90fd2-108">The distance from the user location to the network egress is greater than 500 miles (800 kilometers) and this is expected to be impacting performance.</span></span> <span data-ttu-id="90fd2-109">建議使用本機輸出更接近給使用者。</span><span class="sxs-lookup"><span data-stu-id="90fd2-109">Local egress closer to the user is recommended.</span></span>

<span data-ttu-id="90fd2-110">如此可識別的辦公室位置與網路輸出之間的距離是超過 500 英哩。</span><span class="sxs-lookup"><span data-stu-id="90fd2-110">This identifies that the distance between the office location and the network egress is more than 500 miles.</span></span> <span data-ttu-id="90fd2-111">模糊化的用戶端電腦位置所識別的辦公室位置及網路輸出位置由使用反向的 IP 位址至位置資料庫。</span><span class="sxs-lookup"><span data-stu-id="90fd2-111">The office location is identified by an obfuscated client machine location and the network egress location is identified by using reverse IP Address to location databases.</span></span> <span data-ttu-id="90fd2-112">辦公室位置可能不正確，如果 Windows 位置服務已停用在機器上。</span><span class="sxs-lookup"><span data-stu-id="90fd2-112">The office location may be inaccurate if Windows Location Services is disabled on machines.</span></span> <span data-ttu-id="90fd2-113">網路輸出位置可能有不精準的反向的 IP 位址資料庫資訊不正確。</span><span class="sxs-lookup"><span data-stu-id="90fd2-113">The network egress location may be inaccurate if the reverse IP Address database information is inaccurate.</span></span>

<span data-ttu-id="90fd2-114">此深入了解詳細資料包含辦公室地點、 網路輸出位置，以及它們之間的距離。</span><span class="sxs-lookup"><span data-stu-id="90fd2-114">Details for this insight include the office location, the network egress location, and the distance between them.</span></span>

<span data-ttu-id="90fd2-115">針對此深入了解我們建議更接近網路輸出的辦公室位置來使連線可以完備傳閱給 Microsoft 的網路上網際網路和到 Office 365 服務前方門。</span><span class="sxs-lookup"><span data-stu-id="90fd2-115">For this insight we would recommend network egress closer to the office location so that connectivity can route optimally to Microsoft's network on the Internet and onto Office 365 service front doors.</span></span> <span data-ttu-id="90fd2-116">需要關閉網路輸出辦公室位置也可讓以改善效能在未來為 Microsoft 的使用者在未來展開目前狀態和 Office 365 服務前方門這兩個網路資料的點。</span><span class="sxs-lookup"><span data-stu-id="90fd2-116">Having close network egress to users office locations also allows for improved performance in the future as Microsoft expands both network points of presence and Office 365 service front doors in the future.</span></span>

<span data-ttu-id="90fd2-117">此深入了解是為 「 輸出"縮寫某些摘要檢視中。</span><span class="sxs-lookup"><span data-stu-id="90fd2-117">This insight is abbreviated as "Egress" in some summary views.</span></span>

## <a name="better-performance-detected-for-customers-near-you"></a><span data-ttu-id="90fd2-118">偵測到您附近的客戶獲得較佳效能</span><span class="sxs-lookup"><span data-stu-id="90fd2-118">Better performance detected for customers near you</span></span>

<span data-ttu-id="90fd2-119">自相當數量的地鐵區域中的客戶在組織中有更好的效能，比使用者此辦公室位置。</span><span class="sxs-lookup"><span data-stu-id="90fd2-119">Since a significant number of customers in your metro area have better performance than users in your organization at this office location.</span></span>

<span data-ttu-id="90fd2-120">這會尋找在 Office 365 客戶中為此辦公室位置的相同市/鎮彙總效能。</span><span class="sxs-lookup"><span data-stu-id="90fd2-120">This looks at the aggregate performance of Office 365 customers in the same city as this office location.</span></span>

![相對的網路效能](Media/m365-mac-perf/m365-mac-perf-relative-perf.png)

<span data-ttu-id="90fd2-122">我們計算較佳效能 bucket 的相同市/鎮中的 Office 365 客戶的百分比。</span><span class="sxs-lookup"><span data-stu-id="90fd2-122">We calculate the percentage of Office 365 customers in the same city in better performance buckets.</span></span> <span data-ttu-id="90fd2-123">如果此數字] 如果 10%的多個接著，我們示範網路深入解析。</span><span class="sxs-lookup"><span data-stu-id="90fd2-123">If this number if 10% of more then we show the network insight.</span></span>

<span data-ttu-id="90fd2-124">此深入了解是為 「 對等 」 縮寫某些摘要檢視中。</span><span class="sxs-lookup"><span data-stu-id="90fd2-124">This insight is abbreviated as "Peers" in some summary views.</span></span>

## <a name="use-of-a-non-optimal-exchange-online-service-front-door"></a><span data-ttu-id="90fd2-125">使用的非最佳 Exchange Online 服務的前哨</span><span class="sxs-lookup"><span data-stu-id="90fd2-125">Use of a non-optimal Exchange Online service front door</span></span>

<span data-ttu-id="90fd2-126">使用者無法連線至最佳的 Office 365 服務前哨，這預期會影響效能。</span><span class="sxs-lookup"><span data-stu-id="90fd2-126">The user is not connecting to an optimal Office 365 service front door and this is expected to be impacting performance.</span></span>

<span data-ttu-id="90fd2-127">我們列出 Exchange Online 服務前方門這是適用於從具有良好效能的辦公室位置市/鎮。</span><span class="sxs-lookup"><span data-stu-id="90fd2-127">We list Exchange Online service front doors which are suitable for use from the office location city with good performance.</span></span> <span data-ttu-id="90fd2-128">如果目前的測試顯示不在此清單上使用 Exchange Online 服務前哨，我們呼叫出這個建議。</span><span class="sxs-lookup"><span data-stu-id="90fd2-128">If the current test shows use of an Exchange Online service front door not on this list, then we call out this recommendation.</span></span>

<span data-ttu-id="90fd2-129">使用非最佳 Exchange Online 服務的前哨可能被因網路 backhaul 公司網路輸出之前在此情況下建議本機和直接的網路輸出。</span><span class="sxs-lookup"><span data-stu-id="90fd2-129">Use of a non-optimal Exchange Online service front door could be caused by network backhaul before the corporate network egress in which case we recommend local and direct network egress.</span></span> <span data-ttu-id="90fd2-130">它也可能被造成所使用的遠端 DNS 遞迴解析程式伺服器在此情況下建議對齊 DNS 遞迴解析程式伺服器具有網路輸出。</span><span class="sxs-lookup"><span data-stu-id="90fd2-130">It could also be caused by use of a remote DNS Recursive Resolver server in which case we recommend aligning the DNS Recursive Resolver server with the network egress.</span></span>

<span data-ttu-id="90fd2-131">此深入了解為某些摘要檢視中會縮寫成 「 路徑 」。</span><span class="sxs-lookup"><span data-stu-id="90fd2-131">This insight is abbreviated as "Routing" in some summary views.</span></span>

## <a name="use-of-non-optimal-sharepoint-online-service-front-door"></a><span data-ttu-id="90fd2-132">使用的非最佳 SharePoint Online 服務的前哨</span><span class="sxs-lookup"><span data-stu-id="90fd2-132">Use of non-optimal SharePoint Online service front door</span></span>

<span data-ttu-id="90fd2-133">使用者不連線至最接近 SharePoint Online 服務的前哨。</span><span class="sxs-lookup"><span data-stu-id="90fd2-133">The user is not connecting to the closest SharePoint Online service front door.</span></span> <span data-ttu-id="90fd2-134">這被預期會影響效能。</span><span class="sxs-lookup"><span data-stu-id="90fd2-134">This is expected to be impacting performance.</span></span>

<span data-ttu-id="90fd2-135">我們找出測試用戶端連線至 SharePoint Online 服務前哨。</span><span class="sxs-lookup"><span data-stu-id="90fd2-135">We identify the SharePoint Online service front door that the test client is connecting to.</span></span> <span data-ttu-id="90fd2-136">然後針對的辦公室位置市/鎮我們比較，必須是 SharePoint Online 服務的前哨針對該縣/市。</span><span class="sxs-lookup"><span data-stu-id="90fd2-136">Then for the office location city we compare that to the expected SharePoint Online service front door for that city.</span></span> <span data-ttu-id="90fd2-137">如果它不符合，我們做此建議。</span><span class="sxs-lookup"><span data-stu-id="90fd2-137">If it doesn't match, then we make this recommendation.</span></span>

<span data-ttu-id="90fd2-138">此深入了解為某些摘要檢視中會縮寫成 「 Afd 」。</span><span class="sxs-lookup"><span data-stu-id="90fd2-138">This insight is abbreviated as "Afd" in some summary views.</span></span>

## <a name="low-download-speed-from-sharepoint-front-door"></a><span data-ttu-id="90fd2-139">從 SharePoint 前哨低的下載速度</span><span class="sxs-lookup"><span data-stu-id="90fd2-139">Low download speed from SharePoint front door</span></span>

<span data-ttu-id="90fd2-140">Sub 最佳化網路下載速度偵測到這會影響從商務用 OneDrive 載入文件所需的時間長度。</span><span class="sxs-lookup"><span data-stu-id="90fd2-140">Sub optimal network download speed detected which impacts how long it takes to load documents from OneDrive for Business.</span></span>

<span data-ttu-id="90fd2-141">使用者可以取得從 SharePoint Online 和 OneDrive for Business 服務前方門測量單位為 mb (mbps) 的下載速度。</span><span class="sxs-lookup"><span data-stu-id="90fd2-141">The download speed that a user can get from SharePoint Online and OneDrive for Business service front doors is measured in megabytes per second (MBps).</span></span> <span data-ttu-id="90fd2-142">如果這個值是小於 1 MBps 我們會提供此深入了解。</span><span class="sxs-lookup"><span data-stu-id="90fd2-142">If this value is less than 1 MBps then we provide this insight.</span></span>

<span data-ttu-id="90fd2-143">若要改善下載速度的使用者都可以取得頻寬可能需要增加。</span><span class="sxs-lookup"><span data-stu-id="90fd2-143">To improve download speed that a user can get bandwidth may need to be increased.</span></span> <span data-ttu-id="90fd2-144">或者，可能是網路壅塞之間的辦公室位置的使用者機器和 SharePoint Online 服務前哨。</span><span class="sxs-lookup"><span data-stu-id="90fd2-144">Alternatively, there may be network congestion between user machines at the office location and the SharePoint Online service front door.</span></span> <span data-ttu-id="90fd2-145">這有時稱為 congestive 遺失，而且它將限制可用的下載速度給使用者，即使有足夠的頻寬。</span><span class="sxs-lookup"><span data-stu-id="90fd2-145">This is sometimes called congestive loss and it restricts the download speed available to users even if sufficient bandwidth is available.</span></span>

<span data-ttu-id="90fd2-146">此深入了解為某些摘要檢視中會縮寫成 「 輸送量 」。</span><span class="sxs-lookup"><span data-stu-id="90fd2-146">This insight is abbreviated as "Throughput" in some summary views.</span></span>

## <a name="related-topics"></a><span data-ttu-id="90fd2-147">相關主題</span><span class="sxs-lookup"><span data-stu-id="90fd2-147">Related topics</span></span>

[<span data-ttu-id="90fd2-148">在 Microsoft 365 系統管理中心 （預覽） 的網路效能建議</span><span class="sxs-lookup"><span data-stu-id="90fd2-148">Network performance recommendations in the Microsoft 365 Admin Center (preview)</span></span>](office-365-network-mac-perf-overview.md)

[<span data-ttu-id="90fd2-149">Office 365 網路評估 （預覽）</span><span class="sxs-lookup"><span data-stu-id="90fd2-149">Office 365 network assessment (preview)</span></span>](office-365-network-mac-perf-score.md)

[<span data-ttu-id="90fd2-150">Office 365 網路上架工具 M365 系統管理中心 （預覽）</span><span class="sxs-lookup"><span data-stu-id="90fd2-150">Office 365 Network Onboarding Tool in the M365 Admin Center (preview)</span></span>](office-365-network-mac-perf-onboarding-tool.md)
