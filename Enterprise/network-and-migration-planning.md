---
title: Office 365 的網路和移轉規劃
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132
description: 包含資訊的網路規劃與測試、 連結和移轉到 Office 365。
ms.openlocfilehash: 02576933a1be615e65b695a7dd72c19eed311c91
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487272"
---
# <a name="network-and-migration-planning-for-office-365"></a><span data-ttu-id="2ab6e-103">Office 365 的網路和移轉規劃</span><span class="sxs-lookup"><span data-stu-id="2ab6e-103">Network and migration planning for Office 365</span></span>

<span data-ttu-id="2ab6e-104">本文章包含有關網路規劃和測試資訊的連結和移轉到 Office 365。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-104">This article contains links to information about network planning and testing, and migration to Office 365.</span></span>
  
<span data-ttu-id="2ab6e-105">在第一次部署或移轉至 Office 365 之前，您可以使用這些主題的資訊來評估您需要的頻寬，然後測試並確認您有足夠頻寬可部署或移轉至 Office 365。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-105">Before you deploy for the first time or migrate to Office 365, you can use the information in these topics to estimate the bandwidth you need and then to test and verify that you have enough bandwidth to deploy or migrate to Office 365.</span></span>

||
|:-----|
| <span data-ttu-id="2ab6e-106">本文是[網路規劃和效能調整的 Office 365](https://aka.ms/tune)的一部分。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-106">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

|||
|:-----|:-----|
|![請參閱 Microsoft Cloud Networking for Enterprise Architects 海報](media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)|<span data-ttu-id="2ab6e-108">如需 Office 365 和其他 Microsoft 雲端平台及服務最佳化您的網路的步驟，請參閱 < <b0>Microsoft Cloud Networking for Enterprise Architects</b0>海報。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-108">For the steps to optimize your network for Office 365 and other Microsoft cloud platforms and services, see the [Microsoft Cloud Networking for Enterprise Architects](https://aka.ms/cloudarchnetworking) poster.</span></span> |
   
## <a name="estimate-network-bandwidth-requirements"></a><span data-ttu-id="2ab6e-109">預估網路頻寬需求</span><span class="sxs-lookup"><span data-stu-id="2ab6e-109">Estimate network bandwidth requirements</span></span>
<span data-ttu-id="2ab6e-110"><a name="EstimateBandwidthRequirements"> </a></span><span class="sxs-lookup"><span data-stu-id="2ab6e-110"></span></span>

<span data-ttu-id="2ab6e-111">使用 Office 365 可能會增加您的組織網際網路電路的使用率。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-111">Using Office 365 may increase the utilization of your organization's internet circuit.</span></span> <span data-ttu-id="2ab6e-112">請務必判斷目前可用的頻寬量是否足以同時至少 20%完整部署 Office 365 之後處理預估的增加容量，以處理最忙碌的天數。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-112">It's important to determine if the amount of bandwidth currently available is enough to handle the estimated increase once Office 365 is fully deployed while leaving at least 20% capacity to handle the busiest of days.</span></span>
  
<span data-ttu-id="2ab6e-113">若要估計頻寬，請使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="2ab6e-113">To estimate the bandwidth, use the following steps:</span></span>
  
1. <span data-ttu-id="2ab6e-114">評估會使用每個網際網路輸出的用戶端數目。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-114">Assess the number of clients that will use each Internet egress.</span></span> <span data-ttu-id="2ab6e-115">讓我們處理最多的連線設定為可能的多 tb 網路。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-115">Let our multi-terabit network handle as much of the connection as possible.</span></span> 
    
2. <span data-ttu-id="2ab6e-116">判斷哪些 Office 365 服務和功能可供用戶端使用。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-116">Determine which Office 365 services and features will be available for clients to use.</span></span> <span data-ttu-id="2ab6e-117">您可能需要一組不同的服務或使用設定檔的人。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-117">You will likely have groups of people with different services or usage profiles.</span></span>
    
3. <span data-ttu-id="2ab6e-118">測量網路使用試驗群組的用戶端。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-118">Measure the network use for a pilot group of clients.</span></span> <span data-ttu-id="2ab6e-119">確認試驗用戶端都代表一個不同的組織，以及不同的地理位置中的人員設定檔。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-119">Ensure the pilot clients are representative of the different profiles of people in the organization as well as the different geographic locations.</span></span> <span data-ttu-id="2ab6e-120">您可以跨-檢查您對我們舊計算器的結果[Exchange](https://go.microsoft.com/fwlink/p/?LinkId=321550)和[商務用 Skype](https://go.microsoft.com/fwlink/p/?LinkId=321551)或我們執行自己的網路的[案例研究](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365)。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-120">You can cross-check your results against our old calculators for [Exchange ](https://go.microsoft.com/fwlink/p/?LinkId=321550)and [Skype for Business](https://go.microsoft.com/fwlink/p/?LinkId=321551) or the [case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) we performed on our own network.</span></span> 
    
4. <span data-ttu-id="2ab6e-121">使用的度量單位從試驗群組推斷整個組織的需求和重新測試來驗證您的網路進行任何變更之前的數量的估計值。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-121">Use the measurements from the pilot group to extrapolate the entire organization's needs and re-test to validate the estimations before making any changes to your network.</span></span>
    
## <a name="test-your-existing-network"></a><span data-ttu-id="2ab6e-122">測試您現有的網路</span><span class="sxs-lookup"><span data-stu-id="2ab6e-122">Test your existing network</span></span>
<span data-ttu-id="2ab6e-123"><a name="calculators"> </a></span><span class="sxs-lookup"><span data-stu-id="2ab6e-123"></span></span>

 <span data-ttu-id="2ab6e-124">**網路工具。**</span><span class="sxs-lookup"><span data-stu-id="2ab6e-124">**Network tools.**</span></span> <span data-ttu-id="2ab6e-125">測試及驗證您的網際網路頻寬，以判斷下載、 上載及延遲的條件約束。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-125">Test and validate your Internet bandwidth to determine download, upload, and latency constraints.</span></span> <span data-ttu-id="2ab6e-126">這些工具可協助您決定您的網路進行移轉，以及完整部署之後的功能。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-126">These tools will help you determine the capabilities of your network for migration as well as after you're fully deployed.</span></span> 
  
- <span data-ttu-id="2ab6e-127">[Microsoft 郵件分析器](https://technet.microsoft.com/library/jj649776.aspx)： 郵件分析器是有效的工具，如網路問題的疑難排解。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-127">[Microsoft Message Analyzer](https://technet.microsoft.com/library/jj649776.aspx): Message Analyzer is an effective tool for troubleshooting network issues.</span></span> <span data-ttu-id="2ab6e-128">郵件分析器擷取、 會顯示，並分析通訊協定為基礎的郵件流量和系統訊息。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-128">Message Analyzer captures, displays, and analyzes protocol-based messaging traffic and system messages.</span></span> <span data-ttu-id="2ab6e-129">郵件分析器也可讓您匯入、 彙總，並分析記錄檔和追蹤檔案中的資料。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-129">Message Analyzer also lets you import, aggregate, and analyze data from log and trace files.</span></span>
    
- <span data-ttu-id="2ab6e-130">[Microsoft Remote Connectivity Analyzer](https://go.microsoft.com/fwlink/p/?LinkId=517243): Exchange Online 環境中測試連線。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-130">[Microsoft Remote Connectivity Analyzer](https://go.microsoft.com/fwlink/p/?LinkId=517243): Tests connectivity in your Exchange Online environment.</span></span>
    
- <span data-ttu-id="2ab6e-131">使用[Microsoft 的支援及修復小幫手的 Office 365](https://diagnostics.office.com/#/Download?env=SOC)來修正 Outlook 與 Office 365 的問題。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-131">Use the [Microsoft Support and Recovery Assistant for Office 365](https://diagnostics.office.com/#/Download?env=SOC) to fix Outlook and Office 365 problems.</span></span> 
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a><span data-ttu-id="2ab6e-132">網路規劃和改善的 Office 365 移轉效能的最佳做法</span><span class="sxs-lookup"><span data-stu-id="2ab6e-132">Best practices for network planning and improving migration performance for Office 365</span></span>
<span data-ttu-id="2ab6e-133"><a name="BestPractices"> </a></span><span class="sxs-lookup"><span data-stu-id="2ab6e-133"></span></span>

<span data-ttu-id="2ab6e-134">深入探討稍微改善您的 Office 365 使用經驗的詳細資訊的這些最佳作法。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-134">Dig a little deeper into these best practices for more information about improving your Office 365 experience.</span></span>
  
1. <span data-ttu-id="2ab6e-135">要開始立即幫助您的使用者？</span><span class="sxs-lookup"><span data-stu-id="2ab6e-135">Want to get started helping your users right away?</span></span> <span data-ttu-id="2ab6e-136">使用 Office 365，包括 SharePoint Online、 Exchange Online 和 Lync Online 中，當您的網路只要不合作的秘訣，請參閱[使用慢速網路上的 Office 365 的最佳作法](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166)。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-136">See [Best practices for using Office 365 on a slow network](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) for tips on using Office 365, including SharePoint Online, Exchange Online, and Lync Online, when your network just isn't cooperating.</span></span> <span data-ttu-id="2ab6e-137">本文會連結至 TechNet，Support.office.com 上的內容的負載最佳化您的 Office 365 使用經驗，並包含簡單的方法來自訂您的網頁以及如何設定 Internet Explorer 設定為最佳的 Office 365 經驗的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-137">This article links out to loads of content on TechNet and Support.office.com for optimizing your Office 365 experience and includes information on easy ways to customize your web pages and how to set your Internet Explorer settings for the best Office 365 experience.</span></span> 
    
2. <span data-ttu-id="2ab6e-138">閱讀[Office 365 網路連線原則](https://aka.ms/o365networkingprinciples)來了解安全地管理 Office 365 流量，並取得獲得最佳效能的連線能力原則。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-138">Read [Office 365 Network Connectivity Principles](https://aka.ms/o365networkingprinciples) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span> <span data-ttu-id="2ab6e-139">本文可協助您了解安全地最佳化 Office 365 網路連線的最新的指引。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-139">This article will help you understand the most recent guidance for securely optimizing Office 365 network connectivity.</span></span> 
    
3. <span data-ttu-id="2ab6e-140">透過謹慎地管理 Windows 更新的排程來改善郵件移轉效能。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-140">Improve mail migration performance by carefully managing the schedule for Windows Updates.</span></span> <span data-ttu-id="2ab6e-141">您可以更新批次中的用戶端電腦，並確定所有用戶端電腦會更新之前先移轉到 Office 365 來調整的網路頻寬使用。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-141">You can update your client computers in batches and ensure that all client computers are updated before migrating to Office 365 to regulate the use of network bandwidth.</span></span> <span data-ttu-id="2ab6e-142">如需詳細資訊，請參閱[手動更新及設定桌面的 Office 365 的最新的更新](https://support.microsoft.com/gp/office-2013-365-update)。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-142">For more information, see [Manually update and configure desktops for Office 365 for the latest updates](https://support.microsoft.com/gp/office-2013-365-update).</span></span>
    
4. <span data-ttu-id="2ab6e-143">當已被視為受信任的網際網路服務，並允許略過大部分的傳統篩選和掃描，有些組織置於不受信任的網際網路服務的網路流量可獲得最佳執行 office 365 的網路流量。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-143">Office 365 network traffic performs best when it's treated as a trusted Internet service and allowed to bypass much of the traditional filtering and scanning that some organizations place on network traffic to untrusted Internet services.</span></span> <span data-ttu-id="2ab6e-144">這通常包括移除輸出 proxy 使用者驗證及封包檢查，例如處理，以及確保本機通往網際網路頻寬容量足以處理增加與適當的網路位址轉譯 (NAT)網路要求。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-144">This typically includes removing outbound processing such as proxy user authentication and packet inspection, as well as ensuring local egress to the Internet with the proper Network Address Translation (NAT) and enough bandwidth capacity to handle the increased network requests.</span></span> <span data-ttu-id="2ab6e-145">如需設定您的網路以處理 Office 365 為您的網路上之信任的網際網路服務的其他指引，請參閱[管理 Office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-145">Refer to [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)for additional guidance on configuring your network to handle Office 365 as a trusted Internet service on your network.</span></span>
    
1. <span data-ttu-id="2ab6e-146">請確定[管理 Office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-146">Ensure [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).</span></span> <span data-ttu-id="2ab6e-147">移至 Office 365 的其他流量會產生輸出 proxy 連線的增加以及增加的安全流量透過 TLS/SSL。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-147">The additional traffic going to Office 365 results in an increase of outbound proxy connections as well as an increase in secure traffic over TLS/SSL.</span></span>
    
2. <span data-ttu-id="2ab6e-148">如果您的輸出 proxy 需要使用者驗證您可能會遇到慢速連線或遺失的功能。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-148">If your outbound proxies require user authentication you may experience slow connectivity or a loss of functionality.</span></span> <span data-ttu-id="2ab6e-149">略過的 Office 365 網域驗證需求，可以降低此額外負荷。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-149">Bypassing the authentication requirement for the Office 365 domains can reduce this overhead.</span></span>
    
3. <span data-ttu-id="2ab6e-150">如果您有大量的共用行事曆及信箱，您可能會看到從 Outlook 連線至 Exchange 數目增加。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-150">If you have a large number of shared calendars and mailboxes, you may see an increase in the number of connections from Outlook to Exchange.</span></span> <span data-ttu-id="2ab6e-151">比方說，Outlook 用戶端可能開啟使用中每個共用行事曆達兩個額外的連線。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-151">For instance, the Outlook client may open up to two additional connections for each shared calendar in use.</span></span> <span data-ttu-id="2ab6e-152">在此情況下，確定 [輸出 proxy 可以處理的連線，或略過的 proxy 連線至 outlook 的 Office 365]。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-152">In this situation, ensure that the egress proxy can handle the connections, or bypass the proxy for connections to Office 365 for Outlook.</span></span>
    
4. <span data-ttu-id="2ab6e-153">決定公用 IP 位址支援的裝置數目上限，以及如何負載平衡跨多個 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-153">Determine the maximum number of supported devices for a public IP address and how to load balance across multiple IP addresses.</span></span> <span data-ttu-id="2ab6e-154">如需詳細資訊，請參閱[使用 Office 365 的 NAT 支援](nat-support-with-office-365.md)。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-154">For more information, see [NAT support with Office 365](nat-support-with-office-365.md).</span></span>
    
5. <span data-ttu-id="2ab6e-155">如果您在您網路上檢查從電腦的輸出連線，略過此篩選至 Office 365 網域會改善連線能力與效能。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-155">If you're inspecting outbound connections from computers on your network, bypassing this filtering to the Office 365 domains will improve connectivity and performance.</span></span> <span data-ttu-id="2ab6e-156">此外，略過輸出檢查通常會移除單一的網際網路輸出的需求，並啟用的目的地是 Office 365 的網路要求的本機網際網路輸出。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-156">Additionally, bypassing outbound inspection often removes the need for a single Internet egress and enables local Internet egress for Office 365 destined network requests.</span></span>
    
6. <span data-ttu-id="2ab6e-157">有些客戶尋找內部網路設定可能會影響效能。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-157">Some customers find internal network settings may affect performance.</span></span> <span data-ttu-id="2ab6e-158">設定最大傳輸單位 (MTU) 大小，例如網路自動交涉或自動偵測和子最佳路由傳送至網際網路是常見的位置可尋找。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-158">Settings such as maximum transmission unit (MTU) size, network auto-negotiation or auto-detection, and sub-optimal routes to the Internet are common places to look.</span></span>
    
## <a name="network-planning-reference-for-office-365"></a><span data-ttu-id="2ab6e-159">Office 365 的網路規劃參考</span><span class="sxs-lookup"><span data-stu-id="2ab6e-159">Network planning reference for Office 365</span></span>
<span data-ttu-id="2ab6e-160"><a name="NetReference"> </a></span><span class="sxs-lookup"><span data-stu-id="2ab6e-160"></span></span>

<span data-ttu-id="2ab6e-161">這些主題包含詳細的 Office 365 網路參考資訊。</span><span class="sxs-lookup"><span data-stu-id="2ab6e-161">These topics contain detailed Office 365 network reference information.</span></span>
  
- [<span data-ttu-id="2ab6e-162">管理 Office 365 端點</span><span class="sxs-lookup"><span data-stu-id="2ab6e-162">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [<span data-ttu-id="2ab6e-163">用戶端連線</span><span class="sxs-lookup"><span data-stu-id="2ab6e-163">Client connectivity</span></span>](client-connectivity.md)
    
- [<span data-ttu-id="2ab6e-164">內容傳遞網路</span><span class="sxs-lookup"><span data-stu-id="2ab6e-164">Content delivery networks</span></span>](content-delivery-networks.md)
    
- [<span data-ttu-id="2ab6e-165">Office 365 的外部網域名稱系統記錄</span><span class="sxs-lookup"><span data-stu-id="2ab6e-165">External Domain Name System records for Office 365</span></span>](external-domain-name-system-records.md)
    
- [<span data-ttu-id="2ab6e-166">Office 365 服務中的 IPv6 支援</span><span class="sxs-lookup"><span data-stu-id="2ab6e-166">IPv6 support in Office 365 services</span></span>](ipv6-support.md)
    
- [<span data-ttu-id="2ab6e-167">Office 365 網路連線原則</span><span class="sxs-lookup"><span data-stu-id="2ab6e-167">Office 365 Network Connectivity Principles</span></span>](https://aka.ms/o365networkingprinciples)
    
- [<span data-ttu-id="2ab6e-168">Office 365 影片網路常見問題集 (FAQ)</span><span class="sxs-lookup"><span data-stu-id="2ab6e-168">Office 365 video networking Frequently Asked Questions (FAQ)</span></span>](office-365-video-networking-faq.md)
    
- [<span data-ttu-id="2ab6e-169">連線到 Office 365 服務的網路裝置的計劃</span><span class="sxs-lookup"><span data-stu-id="2ab6e-169">Plan for network devices that connect to Office 365 services</span></span>](plan-for-network-devices.md)
    
- [<span data-ttu-id="2ab6e-170">Office 365 服務的部署建議</span><span class="sxs-lookup"><span data-stu-id="2ab6e-170">Deployment advisors for Office 365 services</span></span>](deployment-advisors-for-office-365.md)
    

