---
title: 設計 Microsoft SaaS 的網路
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: 摘要： 了解如何最佳化您的網路存取 Microsoft saas 和服務，包括 Office 365 和 Microsoft Intune Dynamics 365。
ms.openlocfilehash: 94118022b86a5e732467599632e30c058827468f
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915468"
---
# <a name="designing-networking-for-microsoft-saas"></a><span data-ttu-id="5d2fd-103">設計 Microsoft SaaS 的網路</span><span class="sxs-lookup"><span data-stu-id="5d2fd-103">Designing networking for Microsoft SaaS</span></span>

 <span data-ttu-id="5d2fd-104">**摘要：** 了解如何最佳化您的網路存取 Microsoft saas 和服務，包括 Office 365 和 Microsoft Intune Dynamics 365。</span><span class="sxs-lookup"><span data-stu-id="5d2fd-104">**Summary:** Understand how to optimize your network for access to Microsoft's SaaS services, including Office 365, Microsoft Intune, and Dynamics 365.</span></span>
  
<span data-ttu-id="5d2fd-105">若要針對 Microsoft SaaS 服務最佳化您的網路，需要仔細分析您的網際網路邊緣、用戶端裝置以及一般 IT 作業。</span><span class="sxs-lookup"><span data-stu-id="5d2fd-105">Optimizing your network for Microsoft SaaS services requires careful analysis of your Internet edge, your client devices, and typical IT operations.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a><span data-ttu-id="5d2fd-106">準備您的網路 Microsoft saas 和服務的步驟</span><span class="sxs-lookup"><span data-stu-id="5d2fd-106">Steps to prepare your network for Microsoft SaaS services</span></span>

<span data-ttu-id="5d2fd-107">請遵循這些步驟以最佳化您的網路 Microsoft saas 和服務：</span><span class="sxs-lookup"><span data-stu-id="5d2fd-107">Follow these steps to optimize your network for Microsoft SaaS services:</span></span>
  
1. <span data-ttu-id="5d2fd-108">經歷中[常見的元素 Microsoft cloud 連線的](common-elements-of-microsoft-cloud-connectivity.md)**步驟來準備您的 Microsoft 雲端服務的網路**區段。</span><span class="sxs-lookup"><span data-stu-id="5d2fd-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="5d2fd-109">最佳化 Microsoft saas 和服務使用的 proxy 伺服器建議您網際網路的輸出。</span><span class="sxs-lookup"><span data-stu-id="5d2fd-109">Optimize your Internet egress for Microsoft SaaS services using the proxy server recommendations.</span></span>
    
3. <span data-ttu-id="5d2fd-110">最佳化的鄰近和位置建議您網際網路輸送量。</span><span class="sxs-lookup"><span data-stu-id="5d2fd-110">Optimize your Internet throughput using the proximity and location recommendations.</span></span>
    
4. <span data-ttu-id="5d2fd-111">最佳化效能的用戶端電腦與內部網路位，都使用的用戶端流量考量。</span><span class="sxs-lookup"><span data-stu-id="5d2fd-111">Optimize the performance of your client computers and the intranet on which they are located using the client usage considerations.</span></span>
    
5. <span data-ttu-id="5d2fd-112">依需要最佳化資料移轉及同步處理使用 IT 作業考量的效能。</span><span class="sxs-lookup"><span data-stu-id="5d2fd-112">As needed, optimize the performance of data migrations and synchronization using the IT operations considerations.</span></span>
    
## <a name="internet-edge-considerations"></a><span data-ttu-id="5d2fd-113">網際網路 edge 考量</span><span class="sxs-lookup"><span data-stu-id="5d2fd-113">Internet edge considerations</span></span>

<span data-ttu-id="5d2fd-114">以下是一些考量事項最佳化您的網際網路 edge 和 Microsoft saas 和服務的輸送量。</span><span class="sxs-lookup"><span data-stu-id="5d2fd-114">Here are some things to consider optimize your Internet edge and throughput to Microsoft SaaS services.</span></span>
  
<span data-ttu-id="5d2fd-115">**圖 1：Microsoft SaaS 服務的連線選項**</span><span class="sxs-lookup"><span data-stu-id="5d2fd-115">**Figure 1: Connection options for Microsoft SaaS services**</span></span>

![圖 1：Microsoft SaaS 服務的連線選項](media/Network-Poster/SaaS1.png)
  
<span data-ttu-id="5d2fd-117">圖 1 顯示透過網際網路管道或 ExpressRoute 連線至 Microsoft saas 和服務的內部網路。</span><span class="sxs-lookup"><span data-stu-id="5d2fd-117">Figure 1 shows an on-premises network connecting to Microsoft SaaS services over an Internet pipe or ExpressRoute.</span></span>
  
<span data-ttu-id="5d2fd-118">以下是一些最佳化您的 proxy 伺服器的建議：</span><span class="sxs-lookup"><span data-stu-id="5d2fd-118">Here are some recommendations to optimize your proxy server:</span></span>
  
- <span data-ttu-id="5d2fd-119">設定 web 用戶端使用 WPAD、 PAC 或 GPO</span><span class="sxs-lookup"><span data-stu-id="5d2fd-119">Configure web clients using WPAD, PAC, or GPO</span></span>
    
- <span data-ttu-id="5d2fd-120">不使用 SSL 攔截</span><span class="sxs-lookup"><span data-stu-id="5d2fd-120">Don't use SSL interception</span></span>
    
- <span data-ttu-id="5d2fd-121">使用 PAC 檔案略過 Microsoft saas 和服務 DNS 名稱的 proxy</span><span class="sxs-lookup"><span data-stu-id="5d2fd-121">Use a PAC file to bypass the proxy for Microsoft SaaS service DNS names</span></span>
    
- <span data-ttu-id="5d2fd-122">允許 CRL/OCSP 驗證的流量</span><span class="sxs-lookup"><span data-stu-id="5d2fd-122">Allow traffic for CRL/OCSP verification</span></span>
    
<span data-ttu-id="5d2fd-123">以下是一些要檢查的 proxy 伺服器瓶頸：</span><span class="sxs-lookup"><span data-stu-id="5d2fd-123">Here are some proxy server bottlenecks to check:</span></span>
  
- <span data-ttu-id="5d2fd-124">沒有足夠的持續連線 (Outlook)</span><span class="sxs-lookup"><span data-stu-id="5d2fd-124">Insufficient persistent connections (Outlook)</span></span>
    
- <span data-ttu-id="5d2fd-125">沒有足夠的容量</span><span class="sxs-lookup"><span data-stu-id="5d2fd-125">Insufficient capacity</span></span>
    
- <span data-ttu-id="5d2fd-126">這麼做關閉網路評估</span><span class="sxs-lookup"><span data-stu-id="5d2fd-126">Doing off-network evaluation</span></span>
    
- <span data-ttu-id="5d2fd-127">需要驗證</span><span class="sxs-lookup"><span data-stu-id="5d2fd-127">Requiring authentication</span></span>
    
- <span data-ttu-id="5d2fd-128">不支援的 UDP 流量 (Skype 企業版)</span><span class="sxs-lookup"><span data-stu-id="5d2fd-128">No support for UDP traffic (Skype for Business)</span></span>
    
<span data-ttu-id="5d2fd-129">以下是一些鄰近和位置的建議：</span><span class="sxs-lookup"><span data-stu-id="5d2fd-129">Here are some proximity and location recommendations:</span></span>
  
- <span data-ttu-id="5d2fd-130">不要在網際網路的流量路由傳送透過私人 WAN</span><span class="sxs-lookup"><span data-stu-id="5d2fd-130">Don't route your Internet traffic over the private WAN</span></span>
    
- <span data-ttu-id="5d2fd-131">使用的區域 （英文） 使用者的區域中 DNS 和網際網路流量</span><span class="sxs-lookup"><span data-stu-id="5d2fd-131">Use in-region DNS and Internet traffic flow for out-of-region users</span></span>
    
- <span data-ttu-id="5d2fd-132">ExpressRoute 用於高頻寬至 Office 365 和 Azure 服務並行連線</span><span class="sxs-lookup"><span data-stu-id="5d2fd-132">Use ExpressRoute for high bandwidth to Office 365 and concurrent connectivity with Azure services</span></span>
    
<span data-ttu-id="5d2fd-133">以下是輸出所需的 Office 365 流量的連接埠：</span><span class="sxs-lookup"><span data-stu-id="5d2fd-133">Here are the outbound ports needed for Office 365 traffic:</span></span>
  
- <span data-ttu-id="5d2fd-134">TCP 80 （適用於 CRL/OCSP 檢查）</span><span class="sxs-lookup"><span data-stu-id="5d2fd-134">TCP 80 (for CRL/OCSP checks)</span></span>
    
- <span data-ttu-id="5d2fd-135">TCP 443</span><span class="sxs-lookup"><span data-stu-id="5d2fd-135">TCP 443</span></span>
    
- <span data-ttu-id="5d2fd-136">UDP 3478</span><span class="sxs-lookup"><span data-stu-id="5d2fd-136">UDP 3478</span></span>
    
- <span data-ttu-id="5d2fd-137">TCP 5223</span><span class="sxs-lookup"><span data-stu-id="5d2fd-137">TCP 5223</span></span>
    
- <span data-ttu-id="5d2fd-138">TCP 50000-59999</span><span class="sxs-lookup"><span data-stu-id="5d2fd-138">TCP 50000-59999</span></span>
    
- <span data-ttu-id="5d2fd-139">UDP 50000-59999</span><span class="sxs-lookup"><span data-stu-id="5d2fd-139">UDP 50000-59999</span></span>
    
## <a name="client-usage-considerations"></a><span data-ttu-id="5d2fd-140">用戶端流量考量</span><span class="sxs-lookup"><span data-stu-id="5d2fd-140">Client usage considerations</span></span>

<span data-ttu-id="5d2fd-141">首先，設定一組服務的用戶端將會使用，例如：</span><span class="sxs-lookup"><span data-stu-id="5d2fd-141">First, configure the set of services that your clients will be using, such as:</span></span>
  
- <span data-ttu-id="5d2fd-142">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="5d2fd-142">Azure Active Directory</span></span>
    
- <span data-ttu-id="5d2fd-143">Office 365</span><span class="sxs-lookup"><span data-stu-id="5d2fd-143">Office 365</span></span>
    
  - <span data-ttu-id="5d2fd-144">Office 用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="5d2fd-144">Office client apps</span></span>
    
  - <span data-ttu-id="5d2fd-145">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5d2fd-145">SharePoint Online</span></span>
    
  - <span data-ttu-id="5d2fd-146">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="5d2fd-146">Exchange Online</span></span>
    
  - <span data-ttu-id="5d2fd-147">商務用 Skype</span><span class="sxs-lookup"><span data-stu-id="5d2fd-147">Skype for Business</span></span>
    
- <span data-ttu-id="5d2fd-148">Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="5d2fd-148">Microsoft Intune</span></span>
    
- <span data-ttu-id="5d2fd-149">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="5d2fd-149">Dynamics 365</span></span>
    
<span data-ttu-id="5d2fd-150">您的用戶端電腦，決定下列項目：</span><span class="sxs-lookup"><span data-stu-id="5d2fd-150">For your client computers, determine the following:</span></span>
  
- <span data-ttu-id="5d2fd-151">任何一個時間 （時間日、 虛擬主機、 尖峰流量 troughs） 的數目上限</span><span class="sxs-lookup"><span data-stu-id="5d2fd-151">Maximum number at any one time (time of day, seasonal, peaks and troughs in usage)</span></span>
    
- <span data-ttu-id="5d2fd-152">尖峰量所需的總頻寬</span><span class="sxs-lookup"><span data-stu-id="5d2fd-152">Total bandwidth needed for peaks</span></span>
    
- <span data-ttu-id="5d2fd-153">延遲到網際網路的輸出裝置</span><span class="sxs-lookup"><span data-stu-id="5d2fd-153">Latency to the Internet egress device</span></span>
    
- <span data-ttu-id="5d2fd-154">國家/地區和國家/地區資料中心代管的比較</span><span class="sxs-lookup"><span data-stu-id="5d2fd-154">Country of origin vs. country of datacenter co-location</span></span>
    
<span data-ttu-id="5d2fd-155">每一種用戶端 （PC、 smartphone 與平板電腦），請確定目前：</span><span class="sxs-lookup"><span data-stu-id="5d2fd-155">For each type of client (PC, smartphone, tablet), ensure the current:</span></span>
  
- <span data-ttu-id="5d2fd-156">作業系統</span><span class="sxs-lookup"><span data-stu-id="5d2fd-156">Operating system</span></span>
    
- <span data-ttu-id="5d2fd-157">網際網路瀏覽器</span><span class="sxs-lookup"><span data-stu-id="5d2fd-157">Internet browser</span></span>
    
- <span data-ttu-id="5d2fd-158">TCP/IP 堆疊</span><span class="sxs-lookup"><span data-stu-id="5d2fd-158">TCP/IP stack</span></span>
    
- <span data-ttu-id="5d2fd-159">網路硬體</span><span class="sxs-lookup"><span data-stu-id="5d2fd-159">Network hardware</span></span>
    
- <span data-ttu-id="5d2fd-160">網路硬體的作業系統驅動程式</span><span class="sxs-lookup"><span data-stu-id="5d2fd-160">OS drivers for network hardware</span></span>
    
- <span data-ttu-id="5d2fd-161">更新及修補程式安裝</span><span class="sxs-lookup"><span data-stu-id="5d2fd-161">Updates and patches are installed</span></span>
    
<span data-ttu-id="5d2fd-162">此外，最佳化內部網路連線輸送量 (有線、 無線、 或 VPN)。</span><span class="sxs-lookup"><span data-stu-id="5d2fd-162">Additionally, optimize intranet connection throughput (wired, wireless, or VPN).</span></span>
  
<span data-ttu-id="5d2fd-163">如需詳細資訊，請參閱[Office 365 的 NAT 支援](https://support.office.com/article/NAT-support-with-Office-365-170e96ea-d65d-4e51-acac-1de56abe39b9)。</span><span class="sxs-lookup"><span data-stu-id="5d2fd-163">For more information, see [NAT support with Office 365](https://support.office.com/article/NAT-support-with-Office-365-170e96ea-d65d-4e51-acac-1de56abe39b9).</span></span>
  
<span data-ttu-id="5d2fd-164">搭配 Office 365 使用 ExpressRoute 的最新建議，請參閱[Office 365 ExpressRoute](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd)。</span><span class="sxs-lookup"><span data-stu-id="5d2fd-164">For the latest recommendations for using ExpressRoute with Office 365, see [ExpressRoute for Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span></span>
  
<span data-ttu-id="5d2fd-165">最佳化您的內部網路效能，請執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="5d2fd-165">To optimize your intranet performance, do the following:</span></span>
  
- <span data-ttu-id="5d2fd-166">使用工具來往返時間 (RTTs) 量測貴網際網路 edge 裝置 （PsPing、 Ping、 Tracert、 TraceTCP、 網路監視器）</span><span class="sxs-lookup"><span data-stu-id="5d2fd-166">Use tools to gauge round trip times (RTTs) to your Internet edge devices (PsPing, Ping, Tracert, TraceTCP, Network Monitor)</span></span>
    
- <span data-ttu-id="5d2fd-167">執行使用流程通訊協定的輸出路徑分析</span><span class="sxs-lookup"><span data-stu-id="5d2fd-167">Perform egress path analysis using flow protocols</span></span>
    
- <span data-ttu-id="5d2fd-168">執行中繼裝置 （保留時間下限、 健康情況） 分析</span><span class="sxs-lookup"><span data-stu-id="5d2fd-168">Perform analysis of intermediate devices (age, health, etc.)</span></span>
    
<span data-ttu-id="5d2fd-169">如需詳細資訊，請參閱[PsPing 工具](https://technet.microsoft.com/sysinternals/jj729731.aspx)。</span><span class="sxs-lookup"><span data-stu-id="5d2fd-169">For more information, see the [PsPing tool](https://technet.microsoft.com/sysinternals/jj729731.aspx).</span></span>
  
## <a name="it-operations-considerations"></a><span data-ttu-id="5d2fd-170">IT 作業考量</span><span class="sxs-lookup"><span data-stu-id="5d2fd-170">IT operations considerations</span></span>

<span data-ttu-id="5d2fd-171">以下是一些操作 Microsoft saas 和服務中的 IT 工作負載時要考慮的事項。</span><span class="sxs-lookup"><span data-stu-id="5d2fd-171">Here are some things to consider when operating an IT workload in a Microsoft SaaS service.</span></span>
  
### <a name="one-time-migrations"></a><span data-ttu-id="5d2fd-172">一次性移轉</span><span class="sxs-lookup"><span data-stu-id="5d2fd-172">One-time migrations</span></span>

<span data-ttu-id="5d2fd-173">一次性移轉的範例是大量資料傳輸的雲端應用程式] 或 [封存存放區。</span><span class="sxs-lookup"><span data-stu-id="5d2fd-173">Examples of one-time migrations are bulk data transfer for cloud-based applications or archival storage.</span></span>
  
<span data-ttu-id="5d2fd-174">若要最佳化您的網路上時間移轉：</span><span class="sxs-lookup"><span data-stu-id="5d2fd-174">To optimize your network for on-time migrations:</span></span>
  
- <span data-ttu-id="5d2fd-175">避免尖峰網路使用率和修補次數的電腦</span><span class="sxs-lookup"><span data-stu-id="5d2fd-175">Avoid peak network usage and computer patching times</span></span>
    
- <span data-ttu-id="5d2fd-176">應該已建立基準和來試驗、 評估網路狀況並解決問題才可嘗試實際移轉</span><span class="sxs-lookup"><span data-stu-id="5d2fd-176">Should be baselined and piloted, assess network health and resolve issues before attempting actual migration</span></span>
    
- <span data-ttu-id="5d2fd-177">執行事後的未來移轉</span><span class="sxs-lookup"><span data-stu-id="5d2fd-177">Perform post-mortem for future migrations</span></span>
    
### <a name="ongoing-synchronizations"></a><span data-ttu-id="5d2fd-178">進行中的同步處理</span><span class="sxs-lookup"><span data-stu-id="5d2fd-178">Ongoing synchronizations</span></span>

<span data-ttu-id="5d2fd-179">進行中的同步處理的範例是目錄資訊、 設定或檔案。</span><span class="sxs-lookup"><span data-stu-id="5d2fd-179">Examples of ongoing synchronizations are directory information, settings, or files.</span></span>
  
<span data-ttu-id="5d2fd-180">若要最佳化您的進行中的同步處理的網路：</span><span class="sxs-lookup"><span data-stu-id="5d2fd-180">To optimize your network for ongoing synchronizations:</span></span>
  
- <span data-ttu-id="5d2fd-181">確定已備妥監視系統網路頻寬、 解決或關閉收集的錯誤</span><span class="sxs-lookup"><span data-stu-id="5d2fd-181">Ensure that a network bandwidth monitoring system is in place, resolve or dismiss collected errors</span></span>
    
- <span data-ttu-id="5d2fd-182">使用以決定需要網路變更 （擴充/向上、 新電路或新增裝置） 的頻寬監控結果</span><span class="sxs-lookup"><span data-stu-id="5d2fd-182">Use bandwidth monitoring results to determine need for network changes (scale-up/out, new circuits, or adding devices)</span></span>
    
<span data-ttu-id="5d2fd-183">如需詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="5d2fd-183">For more information, see:</span></span>
  
- [<span data-ttu-id="5d2fd-184">Office 365 的網路和移轉規劃</span><span class="sxs-lookup"><span data-stu-id="5d2fd-184">Network and migration planning for Office 365</span></span>](https://aka.ms/tune)
    
- [<span data-ttu-id="5d2fd-185">ExpressRoute for Office 365</span><span class="sxs-lookup"><span data-stu-id="5d2fd-185">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)

## <a name="next-step"></a><span data-ttu-id="5d2fd-186">下一步</span><span class="sxs-lookup"><span data-stu-id="5d2fd-186">Next step</span></span>

[<span data-ttu-id="5d2fd-187">設計 Microsoft Azure PaaS 的網路</span><span class="sxs-lookup"><span data-stu-id="5d2fd-187">Designing networking for Microsoft Azure PaaS</span></span>](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a><span data-ttu-id="5d2fd-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d2fd-188">See also</span></span>

[<span data-ttu-id="5d2fd-189">Microsoft Cloud Networking for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="5d2fd-189">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="5d2fd-190">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="5d2fd-190">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="5d2fd-191">Microsoft 的 Enterprise Cloud 藍圖：IT 決策者的資源</span><span class="sxs-lookup"><span data-stu-id="5d2fd-191">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



