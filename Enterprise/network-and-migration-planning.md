---
title: Office 365 的網路和移轉規劃
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132
description: 包含網路規劃與測試以及移轉至 Office 365 的相關資訊連結。
ms.openlocfilehash: 0601775beb3f7e42d3e18de7b85406c02df2f4e8
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844574"
---
# <a name="network-and-migration-planning-for-office-365"></a><span data-ttu-id="896e2-103">Office 365 的網路和移轉規劃</span><span class="sxs-lookup"><span data-stu-id="896e2-103">Network and migration planning for Office 365</span></span>

<span data-ttu-id="896e2-104">*本文適用於 Office 365 企業版和 Microsoft 365 企業版。*</span><span class="sxs-lookup"><span data-stu-id="896e2-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="896e2-105">本文包含網路規劃與測試以及移轉至 Office 365 的相關資訊連結。</span><span class="sxs-lookup"><span data-stu-id="896e2-105">This article contains links to information about network planning and testing, and migration to Office 365.</span></span>
  
<span data-ttu-id="896e2-106">在首次部署或移轉至 Office 365 前，您可使用這些主題的資訊來預估您需要的頻寬，然後測試並確認您有足夠頻寬可部署或移轉至 Office 365。</span><span class="sxs-lookup"><span data-stu-id="896e2-106">Before you deploy for the first time or migrate to Office 365, you can use the information in these topics to estimate the bandwidth you need and then to test and verify that you have enough bandwidth to deploy or migrate to Office 365.</span></span>

||
|:-----|
| <span data-ttu-id="896e2-107">本文是 [Office 365 的網路規劃與效能調整](https://aka.ms/tune)的一部分。</span><span class="sxs-lookup"><span data-stu-id="896e2-107">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

|||
|:-----|:-----|
|![請參閱適用於企業架構的 Microsoft 雲端網路海報](media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)|<span data-ttu-id="896e2-109">如需了解針對 Office 365 和其他 Microsoft 雲端平台及服務最佳化網路的步驟，請參閱[適用於企業架構的 Microsoft 雲端網路](https://aka.ms/cloudarchnetworking)海報。</span><span class="sxs-lookup"><span data-stu-id="896e2-109">For the steps to optimize your network for Office 365 and other Microsoft cloud platforms and services, see the [Microsoft Cloud Networking for Enterprise Architects](https://aka.ms/cloudarchnetworking) poster.</span></span> |
   
## <a name="estimate-network-bandwidth-requirements"></a><span data-ttu-id="896e2-110">預估網路頻寬需求</span><span class="sxs-lookup"><span data-stu-id="896e2-110">Estimate network bandwidth requirements</span></span>
<span data-ttu-id="896e2-111"><a name="EstimateBandwidthRequirements"> </a></span><span class="sxs-lookup"><span data-stu-id="896e2-111"><a name="EstimateBandwidthRequirements"> </a></span></span>

<span data-ttu-id="896e2-112">使用 Office 365 可能會增加貴組織的網際網路電路使用量。</span><span class="sxs-lookup"><span data-stu-id="896e2-112">Using Office 365 may increase the utilization of your organization's internet circuit.</span></span> <span data-ttu-id="896e2-113">請務必確定目前的頻寬是否足以負荷 Office 365 完整部署後的估計增加量，並且至少預留 20% 的頻寬，以因應極度忙碌時期。</span><span class="sxs-lookup"><span data-stu-id="896e2-113">It's important to determine if the amount of bandwidth currently available is enough to handle the estimated increase once Office 365 is fully deployed while leaving at least 20% capacity to handle the busiest of days.</span></span>
  
<span data-ttu-id="896e2-114">若要估計頻寬，請依照下列步驟操作︰</span><span class="sxs-lookup"><span data-stu-id="896e2-114">To estimate the bandwidth, use the following steps:</span></span>
  
1. <span data-ttu-id="896e2-115">評估會使用每個網際網路出口的用戶端數量。</span><span class="sxs-lookup"><span data-stu-id="896e2-115">Assess the number of clients that will use each Internet egress.</span></span> <span data-ttu-id="896e2-116">盡可能地讓我們的多兆位元網路處理連線。</span><span class="sxs-lookup"><span data-stu-id="896e2-116">Let our multi-terabit network handle as much of the connection as possible.</span></span> 
    
2. <span data-ttu-id="896e2-117">決定哪些 Office 365 服務與功能可供用戶端使用。</span><span class="sxs-lookup"><span data-stu-id="896e2-117">Determine which Office 365 services and features will be available for clients to use.</span></span> <span data-ttu-id="896e2-118">您可能需要一組人員搭配不同的服務或使用設定檔。</span><span class="sxs-lookup"><span data-stu-id="896e2-118">You will likely have groups of people with different services or usage profiles.</span></span>
    
3. <span data-ttu-id="896e2-119">針對由用戶端組成的試驗群組測量網路使用狀況。</span><span class="sxs-lookup"><span data-stu-id="896e2-119">Measure the network use for a pilot group of clients.</span></span> <span data-ttu-id="896e2-120">請確保試驗用戶端能代表組織中屬於各種不同設定檔及地理位置的人員。</span><span class="sxs-lookup"><span data-stu-id="896e2-120">Ensure the pilot clients are representative of the different profiles of people in the organization as well as the different geographic locations.</span></span> <span data-ttu-id="896e2-121">您可以交叉檢查 [Exchange](https://go.microsoft.com/fwlink/p/?LinkId=321550) 和[商務用 Skype](https://go.microsoft.com/fwlink/p/?LinkId=321551) 使用舊版計算器的結果，或是我們在自有網路上執行的[案例研究](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365)。</span><span class="sxs-lookup"><span data-stu-id="896e2-121">You can cross-check your results against our old calculators for [Exchange ](https://go.microsoft.com/fwlink/p/?LinkId=321550)and [Skype for Business](https://go.microsoft.com/fwlink/p/?LinkId=321551) or the [case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) we performed on our own network.</span></span> 
    
4. <span data-ttu-id="896e2-122">從試驗群組的測量結果推算整個組織的需求，然後重新測試以驗證估計值，再變更您的網路設定。</span><span class="sxs-lookup"><span data-stu-id="896e2-122">Use the measurements from the pilot group to extrapolate the entire organization's needs and re-test to validate the estimations before making any changes to your network.</span></span>
    
## <a name="test-your-existing-network"></a><span data-ttu-id="896e2-123">測試您現有的網路</span><span class="sxs-lookup"><span data-stu-id="896e2-123">Test your existing network</span></span>
<span data-ttu-id="896e2-124"><a name="calculators"> </a></span><span class="sxs-lookup"><span data-stu-id="896e2-124"><a name="calculators"> </a></span></span>

 <span data-ttu-id="896e2-125">**網路工具：**</span><span class="sxs-lookup"><span data-stu-id="896e2-125">**Network tools.**</span></span> <span data-ttu-id="896e2-126">測試及驗證您的網際網路頻寬，以判斷下載、上傳和延遲限制。</span><span class="sxs-lookup"><span data-stu-id="896e2-126">Test and validate your Internet bandwidth to determine download, upload, and latency constraints.</span></span> <span data-ttu-id="896e2-127">這些工具會協助您確定用於移轉及完整部署後的網路能力。</span><span class="sxs-lookup"><span data-stu-id="896e2-127">These tools will help you determine the capabilities of your network for migration as well as after you're fully deployed.</span></span> 
    
- <span data-ttu-id="896e2-128">[Microsoft 遠端連線能力分析器](https://go.microsoft.com/fwlink/p/?LinkId=517243)：測試您 Exchange Online 環境的連線能力。</span><span class="sxs-lookup"><span data-stu-id="896e2-128">[Microsoft Remote Connectivity Analyzer](https://go.microsoft.com/fwlink/p/?LinkId=517243): Tests connectivity in your Exchange Online environment.</span></span>
    
- <span data-ttu-id="896e2-129">使用 [Microsoft Office 365 支援服務及修復小幫手](https://diagnostics.office.com/#/Download?env=SOC)修正 Outlook 與 Office 365 問題。</span><span class="sxs-lookup"><span data-stu-id="896e2-129">Use the [Microsoft Support and Recovery Assistant for Office 365](https://diagnostics.office.com/#/Download?env=SOC) to fix Outlook and Office 365 problems.</span></span> 
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a><span data-ttu-id="896e2-130">Office 365 的網路規劃和移轉效能改善最佳作法</span><span class="sxs-lookup"><span data-stu-id="896e2-130">Best practices for network planning and improving migration performance for Office 365</span></span>
<span data-ttu-id="896e2-131"><a name="BestPractices"> </a></span><span class="sxs-lookup"><span data-stu-id="896e2-131"><a name="BestPractices"> </a></span></span>

<span data-ttu-id="896e2-132">如需改善 Office 365 體驗的詳細資訊，請進一步閱讀這些最佳做法。</span><span class="sxs-lookup"><span data-stu-id="896e2-132">Dig a little deeper into these best practices for more information about improving your Office 365 experience.</span></span>
  
1. <span data-ttu-id="896e2-133">您想立即開始協助您的使用者嗎？</span><span class="sxs-lookup"><span data-stu-id="896e2-133">Want to get started helping your users right away?</span></span> <span data-ttu-id="896e2-134">如果您在使用包含 SharePoint Online、Exchange Online 和 Lync Online 等 Office 365 產品時網路運作不順暢，請參閱[在網路緩慢的情況下使用 Office 365 的最佳做法](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166)。</span><span class="sxs-lookup"><span data-stu-id="896e2-134">See [Best practices for using Office 365 on a slow network](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) for tips on using Office 365, including SharePoint Online, Exchange Online, and Lync Online, when your network just isn't cooperating.</span></span> <span data-ttu-id="896e2-135">本文含有大量 TechNet 及 Support.office.com 的連結，內容介紹如何最佳化您的 Office 365 體驗，並包含輕鬆自訂網頁的方法，以及如何設定 Internet Explorer 以享受最佳 Office 365 體驗等資訊。</span><span class="sxs-lookup"><span data-stu-id="896e2-135">This article links out to loads of content on TechNet and Support.office.com for optimizing your Office 365 experience and includes information on easy ways to customize your web pages and how to set your Internet Explorer settings for the best Office 365 experience.</span></span> 
    
2. <span data-ttu-id="896e2-136">請閱讀 [Office 365 網路連線原則](https://aka.ms/o365networkingprinciples)，了解安全管理 Office 365 流量以及可能獲取最佳效能的連線原則。</span><span class="sxs-lookup"><span data-stu-id="896e2-136">Read [Office 365 Network Connectivity Principles](https://aka.ms/o365networkingprinciples) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span> <span data-ttu-id="896e2-137">本文將協助您了解以安全方式最佳化 Office 365 的網路連線能力的最新指引。</span><span class="sxs-lookup"><span data-stu-id="896e2-137">This article will help you understand the most recent guidance for securely optimizing Office 365 network connectivity.</span></span> 
    
3. <span data-ttu-id="896e2-138">謹慎管理 Windows Updates 排程來改善郵件移轉效能。</span><span class="sxs-lookup"><span data-stu-id="896e2-138">Improve mail migration performance by carefully managing the schedule for Windows Updates.</span></span> <span data-ttu-id="896e2-139">您可以批次更新用戶端電腦，確定所有用戶端電腦已在移轉至 Office 365 前更新，以管制網路頻寬的使用。</span><span class="sxs-lookup"><span data-stu-id="896e2-139">You can update your client computers in batches and ensure that all client computers are updated before migrating to Office 365 to regulate the use of network bandwidth.</span></span> <span data-ttu-id="896e2-140">如需詳細資訊，請參閱[針對 Office 365 手動更新及設定電腦以取得最新更新](https://support.microsoft.com/gp/office-2013-365-update)。</span><span class="sxs-lookup"><span data-stu-id="896e2-140">For more information, see [Manually update and configure desktops for Office 365 for the latest updates](https://support.microsoft.com/gp/office-2013-365-update).</span></span>
    
4. <span data-ttu-id="896e2-141">有些組織將 Office 365 放置在不受信任網際網路服務的網路流量上，然而，Office 365 網路流量在被視為受信任的網際網路服務而允許略過大部分的篩選和掃描時可以達到最佳效能。</span><span class="sxs-lookup"><span data-stu-id="896e2-141">Office 365 network traffic performs best when it's treated as a trusted Internet service and allowed to bypass much of the traditional filtering and scanning that some organizations place on network traffic to untrusted Internet services.</span></span> <span data-ttu-id="896e2-142">這通常包括移除如 Proxy 使用者驗證和封包檢查等輸出處理，以及確保本機出口至網際網路使用正確的網路位址轉譯 (NAT) 和擁有足夠的頻寬能力可以處理增加的網路需求。</span><span class="sxs-lookup"><span data-stu-id="896e2-142">This typically includes removing outbound processing such as proxy user authentication and packet inspection, as well as ensuring local egress to the Internet with the proper Network Address Translation (NAT) and enough bandwidth capacity to handle the increased network requests.</span></span> <span data-ttu-id="896e2-143">如需有關設定您的網路，將您網路中的 Office 365 視為受信任網際網路服務進行處理的其他指引，請參閱[管理 Office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)。</span><span class="sxs-lookup"><span data-stu-id="896e2-143">Refer to [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)for additional guidance on configuring your network to handle Office 365 as a trusted Internet service on your network.</span></span>
    
1. <span data-ttu-id="896e2-144">務必閱讀[管理 Office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)。</span><span class="sxs-lookup"><span data-stu-id="896e2-144">Ensure [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).</span></span> <span data-ttu-id="896e2-145">移往 Office 365 的其他流量會導致輸出 Proxy 連線的增加以及 TLS/SSL 安全流量的增加。</span><span class="sxs-lookup"><span data-stu-id="896e2-145">The additional traffic going to Office 365 results in an increase of outbound proxy connections as well as an increase in secure traffic over TLS/SSL.</span></span>
    
2. <span data-ttu-id="896e2-146">如果您的輸出 Proxy 需要使用者驗證，您可能會遇到連線速度緩慢或喪失連線能力的狀況。</span><span class="sxs-lookup"><span data-stu-id="896e2-146">If your outbound proxies require user authentication you may experience slow connectivity or a loss of functionality.</span></span> <span data-ttu-id="896e2-147">略過 Office 365 網域的驗證需求可以減少這項負擔。</span><span class="sxs-lookup"><span data-stu-id="896e2-147">Bypassing the authentication requirement for the Office 365 domains can reduce this overhead.</span></span>
    
3. <span data-ttu-id="896e2-148">如果您有大量的共用行事曆和信箱，可能會看見從 Outlook 至 Exchange 的連線數目增加。</span><span class="sxs-lookup"><span data-stu-id="896e2-148">If you have a large number of shared calendars and mailboxes, you may see an increase in the number of connections from Outlook to Exchange.</span></span> <span data-ttu-id="896e2-149">例如，Outlook 用戶端可能會針對每個使用中的共用行事曆，開啟最多兩個額外連線。</span><span class="sxs-lookup"><span data-stu-id="896e2-149">For instance, the Outlook client may open up to two additional connections for each shared calendar in use.</span></span> <span data-ttu-id="896e2-150">在此情況下，請確定出口 Proxy 可以處理連線，或針對 Outlook 對 Office 365 的連線來略過 Proxy。</span><span class="sxs-lookup"><span data-stu-id="896e2-150">In this situation, ensure that the egress proxy can handle the connections, or bypass the proxy for connections to Office 365 for Outlook.</span></span>
    
4. <span data-ttu-id="896e2-151">決定公用 IP 位址的支援裝置數目上限，以及如何平衡多個 IP 位址的負載。</span><span class="sxs-lookup"><span data-stu-id="896e2-151">Determine the maximum number of supported devices for a public IP address and how to load balance across multiple IP addresses.</span></span> <span data-ttu-id="896e2-152">如需詳細資訊，請參閱 [Office 365 的 NAT 支援](nat-support-with-office-365.md)。</span><span class="sxs-lookup"><span data-stu-id="896e2-152">For more information, see [NAT support with Office 365](nat-support-with-office-365.md).</span></span>
    
5. <span data-ttu-id="896e2-153">如果您正在檢查您網路上電腦的輸出連線，針對 Office 365 網域略過此篩選可以改善連線能力及效能。</span><span class="sxs-lookup"><span data-stu-id="896e2-153">If you're inspecting outbound connections from computers on your network, bypassing this filtering to the Office 365 domains will improve connectivity and performance.</span></span> <span data-ttu-id="896e2-154">此外，略過輸出檢查通常不需要單一網際網路出口，而且會啟用 Office 365 的本機網際網路出口目的地為網路的需求。</span><span class="sxs-lookup"><span data-stu-id="896e2-154">Additionally, bypassing outbound inspection often removes the need for a single Internet egress and enables local Internet egress for Office 365 destined network requests.</span></span>
    
6. <span data-ttu-id="896e2-155">有些客戶會發現內部網路設定可能會影響效能。</span><span class="sxs-lookup"><span data-stu-id="896e2-155">Some customers find internal network settings may affect performance.</span></span> <span data-ttu-id="896e2-156">如傳輸單元最大值 (MTU) 的大小、網路自動交涉或自動偵測以及網際網路的次佳路由等設定都是要經常查看的地方。</span><span class="sxs-lookup"><span data-stu-id="896e2-156">Settings such as maximum transmission unit (MTU) size, network auto-negotiation or auto-detection, and sub-optimal routes to the Internet are common places to look.</span></span>
    
## <a name="network-planning-reference-for-office-365"></a><span data-ttu-id="896e2-157">Office 365 的網路規劃參考</span><span class="sxs-lookup"><span data-stu-id="896e2-157">Network planning reference for Office 365</span></span>
<span data-ttu-id="896e2-158"><a name="NetReference"> </a></span><span class="sxs-lookup"><span data-stu-id="896e2-158"><a name="NetReference"> </a></span></span>

<span data-ttu-id="896e2-159">下列主題包含詳細的 Office 365 網路參考資訊。</span><span class="sxs-lookup"><span data-stu-id="896e2-159">These topics contain detailed Office 365 network reference information.</span></span>
  
- [<span data-ttu-id="896e2-160">管理 Office 365 端點</span><span class="sxs-lookup"><span data-stu-id="896e2-160">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [<span data-ttu-id="896e2-161">用戶端連線</span><span class="sxs-lookup"><span data-stu-id="896e2-161">Client connectivity</span></span>](client-connectivity.md)
    
- [<span data-ttu-id="896e2-162">內容傳遞網路</span><span class="sxs-lookup"><span data-stu-id="896e2-162">Content delivery networks</span></span>](content-delivery-networks.md)
    
- [<span data-ttu-id="896e2-163">Office 365 的外部網域名稱系統記錄</span><span class="sxs-lookup"><span data-stu-id="896e2-163">External Domain Name System records for Office 365</span></span>](external-domain-name-system-records.md)
    
- [<span data-ttu-id="896e2-164">Office 365 服務中的 IPv6 支援</span><span class="sxs-lookup"><span data-stu-id="896e2-164">IPv6 support in Office 365 services</span></span>](ipv6-support.md)
    
- [<span data-ttu-id="896e2-165">Office 365 網路連線原則</span><span class="sxs-lookup"><span data-stu-id="896e2-165">Office 365 Network Connectivity Principles</span></span>](https://aka.ms/o365networkingprinciples)
    
- [<span data-ttu-id="896e2-166">Office 365 影片網路常見問題集 (FAQ)</span><span class="sxs-lookup"><span data-stu-id="896e2-166">Office 365 video networking Frequently Asked Questions (FAQ)</span></span>](office-365-video-networking-faq.md)
    
- [<span data-ttu-id="896e2-167">規劃連線到 Office 365 服務的網路裝置</span><span class="sxs-lookup"><span data-stu-id="896e2-167">Plan for network devices that connect to Office 365 services</span></span>](plan-for-network-devices.md)
    
- [<span data-ttu-id="896e2-168">Office 365 服務的部署建議程式</span><span class="sxs-lookup"><span data-stu-id="896e2-168">Deployment advisors for Office 365 services</span></span>](deployment-advisors-for-office-365.md)
 
## <a name="see-also"></a><span data-ttu-id="896e2-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="896e2-169">See also</span></span>

[<span data-ttu-id="896e2-170">Microsoft 365 企業版概觀</span><span class="sxs-lookup"><span data-stu-id="896e2-170">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
