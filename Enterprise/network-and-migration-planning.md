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
description: 包含資訊的網路規劃和測試、 連結以及移轉至 Office 365。
ms.openlocfilehash: e2434a65b48c12f38d7371a569ba8e0bc282ae06
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223055"
---
# <a name="network-and-migration-planning-for-office-365"></a><span data-ttu-id="6faf0-103">Office 365 的網路和移轉規劃</span><span class="sxs-lookup"><span data-stu-id="6faf0-103">Network and migration planning for Office 365</span></span>

<span data-ttu-id="6faf0-104">本文包含網路規劃和測試的相關資訊的連結並移轉至 Office 365。</span><span class="sxs-lookup"><span data-stu-id="6faf0-104">This article contains links to information about network planning and testing, and migration to Office 365.</span></span>
  
<span data-ttu-id="6faf0-105">在首次部署或移轉至 Office 365 前，您可使用這些主題的資訊來預估您需要的頻寬，然後測試並確認您有足夠頻寬可部署或移轉至 Office 365。</span><span class="sxs-lookup"><span data-stu-id="6faf0-105">Before you deploy for the first time or migrate to Office 365, you can use the information in these topics to estimate the bandwidth you need and then to test and verify that you have enough bandwidth to deploy or migrate to Office 365.</span></span>

||
|:-----|
| <span data-ttu-id="6faf0-106">本文是[網路規劃和 Office 365 的效能調整](https://aka.ms/tune)的一部分。</span><span class="sxs-lookup"><span data-stu-id="6faf0-106">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

|||
|:-----|:-----|
|![請參閱 Microsoft 雲端網路的企業架構師海報 （英文）](media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)|<span data-ttu-id="6faf0-108">如需如何最佳化您的網路的 Office 365 與其他 Microsoft cloud 平台及服務的步驟，請參閱[Microsoft 雲端網路的企業架構師](https://aka.ms/cloudarchnetworking)海報。</span><span class="sxs-lookup"><span data-stu-id="6faf0-108">For the steps to optimize your network for Office 365 and other Microsoft cloud platforms and services, see the [Microsoft Cloud Networking for Enterprise Architects](https://aka.ms/cloudarchnetworking) poster.</span></span> |
   
## <a name="estimate-network-bandwidth-requirements"></a><span data-ttu-id="6faf0-109">預估網路頻寬需求</span><span class="sxs-lookup"><span data-stu-id="6faf0-109">Estimate network bandwidth requirements</span></span>
<span data-ttu-id="6faf0-110"><a name="EstimateBandwidthRequirements"> </a></span><span class="sxs-lookup"><span data-stu-id="6faf0-110"></span></span>

<span data-ttu-id="6faf0-p101">使用 Office 365 可能會增加您組織的網際網路電路使用率。請務必判斷目前可用的頻寬量是否足以同時又至少 20%完整部署 Office 365 一旦處理估計的增加產能，處理忙碌的天數。</span><span class="sxs-lookup"><span data-stu-id="6faf0-p101">Using Office 365 may increase the utilization of your organization's internet circuit. It's important to determine if the amount of bandwidth currently available is enough to handle the estimated increase once Office 365 is fully deployed while leaving at least 20% capacity to handle the busiest of days.</span></span>
  
<span data-ttu-id="6faf0-113">若要估算頻寬，請使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="6faf0-113">To estimate the bandwidth, use the following steps:</span></span>
  
1. <span data-ttu-id="6faf0-p102">評估將會使用每個網際網路輸出的用戶端數目。可讓我們處理的連線盡量的多個 tb 網路。</span><span class="sxs-lookup"><span data-stu-id="6faf0-p102">Assess the number of clients that will use each Internet egress. Let our multi-terabit network handle as much of the connection as possible.</span></span> 
    
2. <span data-ttu-id="6faf0-p103">決定哪些 Office 365 服務和功能可供用戶端使用。您可能會有不同的服務或使用設定檔的人員的群組。</span><span class="sxs-lookup"><span data-stu-id="6faf0-p103">Determine which Office 365 services and features will be available for clients to use. You will likely have groups of people with different services or usage profiles.</span></span>
    
3. <span data-ttu-id="6faf0-p104">測量網路使用的用戶端試驗群組。確定試驗用戶端的不同的組織如不同地理位置中的人員設定檔的人。您可以跨檢查您對我們舊計算器的結果[Exchange](https://go.microsoft.com/fwlink/p/?LinkId=321550)和[Skype 的商務](https://go.microsoft.com/fwlink/p/?LinkId=321551)或我們執行我們自己網路的[案例研究](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365)。</span><span class="sxs-lookup"><span data-stu-id="6faf0-p104">Measure the network use for a pilot group of clients. Ensure the pilot clients are representative of the different profiles of people in the organization as well as the different geographic locations. You can cross-check your results against our old calculators for [Exchange ](https://go.microsoft.com/fwlink/p/?LinkId=321550)and [Skype for Business](https://go.microsoft.com/fwlink/p/?LinkId=321551) or the [case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) we performed on our own network.</span></span> 
    
4. <span data-ttu-id="6faf0-121">使用的度量單位從試驗群組推斷結果整個組織的需求和重新測試來驗證估算之前對您的網路進行任何變更。</span><span class="sxs-lookup"><span data-stu-id="6faf0-121">Use the measurements from the pilot group to extrapolate the entire organization's needs and re-test to validate the estimations before making any changes to your network.</span></span>
    
## <a name="test-your-existing-network"></a><span data-ttu-id="6faf0-122">測試您現有的網路</span><span class="sxs-lookup"><span data-stu-id="6faf0-122">Test your existing network</span></span>
<span data-ttu-id="6faf0-123"><a name="calculators"> </a></span><span class="sxs-lookup"><span data-stu-id="6faf0-123"></span></span>

 <span data-ttu-id="6faf0-p105">**網路工具。** 測試及驗證您的網際網路頻寬來決定下載 （英文）、 上傳，並延遲條件約束。這些工具可協助您決定您的網路進行移轉以及在完整部署之後的功能。</span><span class="sxs-lookup"><span data-stu-id="6faf0-p105">**Network tools.** Test and validate your Internet bandwidth to determine download, upload, and latency constraints. These tools will help you determine the capabilities of your network for migration as well as after you're fully deployed.</span></span> 
  
- <span data-ttu-id="6faf0-p106">[Microsoft 訊息 Analyzer](https://technet.microsoft.com/library/jj649776.aspx)： 訊息 Analyzer 是有效的網路問題的疑難排解工具。郵件 Analyzer 擷取、 顯示、 和分析通訊協定式訊息流量和系統訊息。郵件 Analyzer 也可讓您匯入、 總計、 和分析記錄檔和追蹤檔案的資料。</span><span class="sxs-lookup"><span data-stu-id="6faf0-p106">[Microsoft Message Analyzer](https://technet.microsoft.com/library/jj649776.aspx): Message Analyzer is an effective tool for troubleshooting network issues. Message Analyzer captures, displays, and analyzes protocol-based messaging traffic and system messages. Message Analyzer also lets you import, aggregate, and analyze data from log and trace files.</span></span>
    
- <span data-ttu-id="6faf0-130">[Microsoft Remote Connectivity Analyzer](https://go.microsoft.com/fwlink/p/?LinkId=517243): Exchange Online 環境中測試連線。</span><span class="sxs-lookup"><span data-stu-id="6faf0-130">[Microsoft Remote Connectivity Analyzer](https://go.microsoft.com/fwlink/p/?LinkId=517243): Tests connectivity in your Exchange Online environment.</span></span>
    
- <span data-ttu-id="6faf0-131">使用[Microsoft 支援與 Office 365 的助理復原](https://diagnostics.office.com/#/Download?env=SOC)修正 Outlook 與 Office 365 的問題。</span><span class="sxs-lookup"><span data-stu-id="6faf0-131">Use the [Microsoft Support and Recovery Assistant for Office 365](https://diagnostics.office.com/#/Download?env=SOC) to fix Outlook and Office 365 problems.</span></span> 
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a><span data-ttu-id="6faf0-132">Best practices for network planning and improving migration performance for Office 365</span><span class="sxs-lookup"><span data-stu-id="6faf0-132">Best practices for network planning and improving migration performance for Office 365</span></span>
<span data-ttu-id="6faf0-133"><a name="BestPractices"> </a></span><span class="sxs-lookup"><span data-stu-id="6faf0-133"></span></span>

<span data-ttu-id="6faf0-134">深入探討一點這些提升您的 Office 365 功能的詳細資訊的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="6faf0-134">Dig a little deeper into these best practices for more information about improving your Office 365 experience.</span></span>
  
1. <span data-ttu-id="6faf0-p107">想要立即協助使用者開始吗？請參閱使用 Office 365，包括 SharePoint Online、 Exchange Online 與 Lync Online，當您的網路只是不是合作秘訣[使用在慢速網路上的 Office 365 的最佳作法](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166)。本文及最佳化您的 Office 365 功能的連結出載入的 TechNet 和 Support.office.com 內容包含如何輕鬆自訂您的網頁及如何設定您的 Internet Explorer 設定獲得最佳的 Office 365 體驗的方式的資訊。</span><span class="sxs-lookup"><span data-stu-id="6faf0-p107">Want to get started helping your users right away? See [Best practices for using Office 365 on a slow network](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) for tips on using Office 365, including SharePoint Online, Exchange Online, and Lync Online, when your network just isn't cooperating. This article links out to loads of content on TechNet and Support.office.com for optimizing your Office 365 experience and includes information on easy ways to customize your web pages and how to set your Internet Explorer settings for the best Office 365 experience.</span></span> 
    
2. <span data-ttu-id="6faf0-p108">請閱讀[Office 365 網路連線原則](https://aka.ms/o365networkingprinciples)了解連線原則可安全地管理 Office 365 流量和快速獲得最佳效能。本文可協助您了解可安全地最佳化 Office 365 網路連線的最新的指引。</span><span class="sxs-lookup"><span data-stu-id="6faf0-p108">Read [Office 365 Network Connectivity Principles](https://aka.ms/o365networkingprinciples) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance. This article will help you understand the most recent guidance for securely optimizing Office 365 network connectivity.</span></span> 
    
3. <span data-ttu-id="6faf0-p109">改善郵件移轉效能謹慎管理 Windows 更新的排程。您可以更新用戶端電腦的批次並確保所有用戶端電腦進行更新之前移轉至 Office 365 管理網路頻寬的使用。如需詳細資訊，請參閱[手動更新及設定桌上型電腦的 Office 365 的最新的更新](https://support.microsoft.com/gp/office-2013-365-update)。</span><span class="sxs-lookup"><span data-stu-id="6faf0-p109">Improve mail migration performance by carefully managing the schedule for Windows Updates. You can update your client computers in batches and ensure that all client computers are updated before migrating to Office 365 to regulate the use of network bandwidth. For more information, see [Manually update and configure desktops for Office 365 for the latest updates](https://support.microsoft.com/gp/office-2013-365-update).</span></span>
    
4. <span data-ttu-id="6faf0-p110">已被視為信任的網際網路服務，並允許略過量傳統篩選和掃描有些組織放到不受信任的網際網路服務網路流量的最佳執行 office 365 網路流量。這通常包含移除輸出處理如 proxy 使用者驗證及封包檢查、 以及確保本機輸出至適當的網路位址轉譯 (NAT) 與足夠的頻寬容量來處理增加網際網路網路要求。請參閱[管理 Office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)的設定來處理做為信任的網際網路服務網路上的 Office 365 網路的其他指導。</span><span class="sxs-lookup"><span data-stu-id="6faf0-p110">Office 365 network traffic performs best when it's treated as a trusted Internet service and allowed to bypass much of the traditional filtering and scanning that some organizations place on network traffic to untrusted Internet services. This typically includes removing outbound processing such as proxy user authentication and packet inspection, as well as ensuring local egress to the Internet with the proper Network Address Translation (NAT) and enough bandwidth capacity to handle the increased network requests. Refer to [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)for additional guidance on configuring your network to handle Office 365 as a trusted Internet service on your network.</span></span>
    
1. <span data-ttu-id="6faf0-p111">請確定[管理 Office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)。移至 Office 365 的其他流量會產生的輸出 proxy 連線增加時的安全流量增加 over TLS/SSL。</span><span class="sxs-lookup"><span data-stu-id="6faf0-p111">Ensure [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a). The additional traffic going to Office 365 results in an increase of outbound proxy connections as well as an increase in secure traffic over TLS/SSL.</span></span>
    
2. <span data-ttu-id="6faf0-p112">如果您輸出 proxy 需要使用者驗證您可能會遇到慢速連線或遺失的功能。略過的 Office 365 網域驗證要求可能會降低此額外負荷。</span><span class="sxs-lookup"><span data-stu-id="6faf0-p112">If your outbound proxies require user authentication you may experience slow connectivity or a loss of functionality. Bypassing the authentication requirement for the Office 365 domains can reduce this overhead.</span></span>
    
3. <span data-ttu-id="6faf0-p113">如果您有大量的共用行事曆和信箱，可能會看見從 Outlook 至 Exchange 的連線數目增加。例如，Outlook 用戶端可能會針對每個使用中的共用行事曆，開啟最多兩個額外連線。在此情況下，請確定向外的 Proxy 可以處理連線，或針對 Outlook 對 Office 365 的連線來略過 Proxy。</span><span class="sxs-lookup"><span data-stu-id="6faf0-p113">If you have a large number of shared calendars and mailboxes, you may see an increase in the number of connections from Outlook to Exchange. For instance, the Outlook client may open up to two additional connections for each shared calendar in use. In this situation, ensure that the egress proxy can handle the connections, or bypass the proxy for connections to Office 365 for Outlook.</span></span>
    
4. <span data-ttu-id="6faf0-p114">決定的公用 IP 位址支援的裝置數目上限，以及如何跨多個 IP 位址的負載平衡。如需詳細資訊，請參閱[Office 365 的 NAT 支援](nat-support-with-office-365.md)。</span><span class="sxs-lookup"><span data-stu-id="6faf0-p114">Determine the maximum number of supported devices for a public IP address and how to load balance across multiple IP addresses. For more information, see [NAT support with Office 365](nat-support-with-office-365.md).</span></span>
    
5. <span data-ttu-id="6faf0-p115">如果您正在檢查從電腦的輸出連線網路上，略過篩選至 Office 365 網域將可改善連線和效能。此外，略過輸出檢查通常會移除單一的網際網路輸出需要與可讓目的地的 Office 365 網路要求的本機網際網路輸出。</span><span class="sxs-lookup"><span data-stu-id="6faf0-p115">If you're inspecting outbound connections from computers on your network, bypassing this filtering to the Office 365 domains will improve connectivity and performance. Additionally, bypassing outbound inspection often removes the need for a single Internet egress and enables local Internet egress for Office 365 destined network requests.</span></span>
    
6. <span data-ttu-id="6faf0-p116">某些客戶會尋找內部網路設定可能會影響效能。最大傳輸單位 (MTU) 大小，例如設定網路自動交涉或自動偵測和子最佳路由到網際網路常見的位置可尋找。</span><span class="sxs-lookup"><span data-stu-id="6faf0-p116">Some customers find internal network settings may affect performance. Settings such as maximum transmission unit (MTU) size, network auto-negotiation or auto-detection, and sub-optimal routes to the Internet are common places to look.</span></span>
    
## <a name="network-planning-reference-for-office-365"></a><span data-ttu-id="6faf0-159">Office 365 的網路規劃參考</span><span class="sxs-lookup"><span data-stu-id="6faf0-159">Network planning reference for Office 365</span></span>
<span data-ttu-id="6faf0-160"><a name="NetReference"> </a></span><span class="sxs-lookup"><span data-stu-id="6faf0-160"></span></span>

<span data-ttu-id="6faf0-161">這些主題包含詳細的 Office 365 網路參考資訊。</span><span class="sxs-lookup"><span data-stu-id="6faf0-161">These topics contain detailed Office 365 network reference information.</span></span>
  
- [<span data-ttu-id="6faf0-162">管理 Office 365 端點</span><span class="sxs-lookup"><span data-stu-id="6faf0-162">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [<span data-ttu-id="6faf0-163">用戶端連線</span><span class="sxs-lookup"><span data-stu-id="6faf0-163">Client connectivity</span></span>](client-connectivity.md)
    
- [<span data-ttu-id="6faf0-164">內容傳遞網路</span><span class="sxs-lookup"><span data-stu-id="6faf0-164">Content delivery networks</span></span>](content-delivery-networks.md)
    
- [<span data-ttu-id="6faf0-165">Office 365 的外部網域名稱系統記錄</span><span class="sxs-lookup"><span data-stu-id="6faf0-165">External Domain Name System records for Office 365</span></span>](external-domain-name-system-records.md)
    
- [<span data-ttu-id="6faf0-166">Office 365 服務中的 IPv6 支援</span><span class="sxs-lookup"><span data-stu-id="6faf0-166">IPv6 support in Office 365 services</span></span>](ipv6-support.md)
    
- [<span data-ttu-id="6faf0-167">Office 365 網路連線原則</span><span class="sxs-lookup"><span data-stu-id="6faf0-167">Office 365 Network Connectivity Principles</span></span>](https://aka.ms/o365networkingprinciples)
    
- [<span data-ttu-id="6faf0-168">Microsoft 虛擬學院： Office 365 績效管理</span><span class="sxs-lookup"><span data-stu-id="6faf0-168">Microsoft Virtual Academy: Office 365 Performance Management</span></span>](https://mva.microsoft.com/en-us/training-courses/office-365-performance-management-8416)
    
- [<span data-ttu-id="6faf0-169">Office 365 影片網路常見問題集 (FAQ)</span><span class="sxs-lookup"><span data-stu-id="6faf0-169">Office 365 video networking Frequently Asked Questions (FAQ)</span></span>](office-365-video-networking-faq.md)
    
- [<span data-ttu-id="6faf0-170">連線到 Office 365 服務的網路裝置的計劃</span><span class="sxs-lookup"><span data-stu-id="6faf0-170">Plan for network devices that connect to Office 365 services</span></span>](plan-for-network-devices.md)
    
- [<span data-ttu-id="6faf0-171">Office 365 服務的部署建議</span><span class="sxs-lookup"><span data-stu-id="6faf0-171">Deployment advisors for Office 365 services</span></span>](deployment-advisors-for-office-365.md)
    

