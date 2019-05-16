---
title: Microsoft Azure 中的 SharePoint Server 2013 災害復原
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 04/17/2018
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Deployment
ms.assetid: e9d14cb2-ff28-4a18-a444-cebf891880ea
description: 摘要： 使用 Azure，您可以建立的災害復原環境的內部部署 SharePoint 伺服器陣列。 本文說明如何設計和實作本解決方案。
ms.openlocfilehash: a302f86e97cd7b61236a92f51a043258882991f7
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070439"
---
# <a name="sharepoint-server-2013-disaster-recovery-in-microsoft-azure"></a><span data-ttu-id="33645-104">Microsoft Azure 中的 SharePoint Server 2013 災害復原</span><span class="sxs-lookup"><span data-stu-id="33645-104">SharePoint Server 2013 Disaster Recovery in Microsoft Azure</span></span>

 <span data-ttu-id="33645-105">**摘要：** 使用 Azure，您可以建立的災害復原環境的內部部署 SharePoint 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="33645-105">**Summary:** Using Azure, you can create a disaster-recovery environment for your on-premises SharePoint farm.</span></span> <span data-ttu-id="33645-106">本文說明如何設計和實作本解決方案。</span><span class="sxs-lookup"><span data-stu-id="33645-106">This article describes how to design and implement this solution.</span></span>

 <span data-ttu-id="33645-107">**觀賞 SharePoint Server 2013 災害復原概觀影片**</span><span class="sxs-lookup"><span data-stu-id="33645-107">**Watch the SharePoint Server 2013 disaster recovery overview video**</span></span>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/1b73ec8f-29bd-44eb-aa3a-f7932784bfd9?autoplay=false]
  
 <span data-ttu-id="33645-108">當發生災害事件 SharePoint 內部部署環境時，您的首要是為了讓執行一次迅速系統。</span><span class="sxs-lookup"><span data-stu-id="33645-108">When disaster strikes your SharePoint on-premises environment, your top priority is to get the system running again quickly.</span></span> <span data-ttu-id="33645-109">與 SharePoint 嚴重損壞修復時更快且更容易必須已在 Microsoft Azure 中執行的備份環境。</span><span class="sxs-lookup"><span data-stu-id="33645-109">Disaster recovery with SharePoint is quicker and easier when you have a backup environment already running in Microsoft Azure.</span></span> <span data-ttu-id="33645-110">這段影片說明 SharePoint 暖容錯移轉環境的主要概念，並輔助本文中提供的完整詳細資料。</span><span class="sxs-lookup"><span data-stu-id="33645-110">This video explains the main concepts of a SharePoint warm failover environment and complements the full details available in this article.</span></span>
  
<span data-ttu-id="33645-111">下列方案模型搭配使用這篇文章：**在 Microsoft Azure 中的 SharePoint 嚴重損壞修復**。</span><span class="sxs-lookup"><span data-stu-id="33645-111">Use this article with the following solution model: **SharePoint Disaster Recovery in Microsoft Azure**.</span></span>
  
<span data-ttu-id="33645-112">[![SharePoint 到 Azure 的災害復原程序](media/SP-DR-Azure.png)](https://go.microsoft.com/fwlink/p/?LinkId=392555)</span><span class="sxs-lookup"><span data-stu-id="33645-112">[![SharePoint disaster-recovery process to Azure](media/SP-DR-Azure.png)](https://go.microsoft.com/fwlink/p/?LinkId=392555)</span></span>
  
 <span data-ttu-id="33645-113">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555) |  [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)</span><span class="sxs-lookup"><span data-stu-id="33645-113">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555) |  [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)</span></span>
  
<span data-ttu-id="33645-114">本文內容：</span><span class="sxs-lookup"><span data-stu-id="33645-114">In this article:</span></span>
  
- [<span data-ttu-id="33645-115">使用 Azure 基礎結構服務的嚴重損壞修復</span><span class="sxs-lookup"><span data-stu-id="33645-115">Use Azure Infrastructure Services for disaster recovery</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#AZ)
    
- [<span data-ttu-id="33645-116">解決方案說明</span><span class="sxs-lookup"><span data-stu-id="33645-116">Solution description</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#SOL)
    
- [<span data-ttu-id="33645-117">詳細架構</span><span class="sxs-lookup"><span data-stu-id="33645-117">Detailed architecture</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#arch)
    
- [<span data-ttu-id="33645-118">嚴重損壞修復藍圖</span><span class="sxs-lookup"><span data-stu-id="33645-118">Disaster recovery roadmap</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#RDmap)
    
- [<span data-ttu-id="33645-119">階段 1： 設計災害復原環境</span><span class="sxs-lookup"><span data-stu-id="33645-119">Phase 1: Design the disaster recovery environment</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase1)
    
- [<span data-ttu-id="33645-120">階段 2： 建立 Azure 虛擬網路和 VPN 連線</span><span class="sxs-lookup"><span data-stu-id="33645-120">Phase 2: Create the Azure virtual network and VPN connection</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase2)
    
- [<span data-ttu-id="33645-121">階段 3： 將 Active Directory 和網域名稱服務部署到 Azure 虛擬網路</span><span class="sxs-lookup"><span data-stu-id="33645-121">Phase 3: Deploy Active Directory and Domain Name Services to the Azure virtual network</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase3)
    
- [<span data-ttu-id="33645-122">階段 4： 部署在 Azure 中的 SharePoint 復原伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="33645-122">Phase 4: Deploy the SharePoint recovery farm in Azure</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase4)
    
- [<span data-ttu-id="33645-123">階段 5： 設定伺服器陣列之間 DFSR</span><span class="sxs-lookup"><span data-stu-id="33645-123">Phase 5: Set up DFSR between the farms</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase5)
    
- [<span data-ttu-id="33645-124">階段 6： 設定記錄傳送至復原伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="33645-124">Phase 6: Set up log shipping to the recovery farm</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase6)
    
- [<span data-ttu-id="33645-125">階段 7： 驗證容錯移轉和復原</span><span class="sxs-lookup"><span data-stu-id="33645-125">Phase 7: Validate failover and recovery</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase7)
    
- [<span data-ttu-id="33645-126">Microsoft 概念證明的環境</span><span class="sxs-lookup"><span data-stu-id="33645-126">Microsoft proof-of-concept environment</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#POC)
    
- [<span data-ttu-id="33645-127">疑難排解提示</span><span class="sxs-lookup"><span data-stu-id="33645-127">Troubleshooting tips</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Troubleshooting)
    
## <a name="use-azure-infrastructure-services-for-disaster-recovery"></a><span data-ttu-id="33645-128">使用 Azure 基礎結構服務的嚴重損壞修復</span><span class="sxs-lookup"><span data-stu-id="33645-128">Use Azure Infrastructure Services for disaster recovery</span></span>

<span data-ttu-id="33645-129">許多組織不需要在災害復原環境 for SharePoint，可以是昂貴來建置及維護內部部署。</span><span class="sxs-lookup"><span data-stu-id="33645-129">Many organizations do not have a disaster recovery environment for SharePoint, which can be expensive to build and maintain on-premises.</span></span> <span data-ttu-id="33645-130">Azure 基礎結構服務提供完美選項災害復原環境，且更有彈性的內部部署替代方式成本低於。</span><span class="sxs-lookup"><span data-stu-id="33645-130">Azure Infrastructure Services provides compelling options for disaster recovery environments that are more flexible and less expensive than the on-premises alternatives.</span></span>
  
<span data-ttu-id="33645-131">使用 Azure 基礎結構服務的優點包括：</span><span class="sxs-lookup"><span data-stu-id="33645-131">The advantages for using Azure Infrastructure Services include:</span></span>
  
- <span data-ttu-id="33645-132">**較少的高成本資源**維護及支付資源少於內部災害復原環境。</span><span class="sxs-lookup"><span data-stu-id="33645-132">**Fewer costly resources** Maintain and pay for fewer resources than on-premises disaster recovery environments.</span></span> <span data-ttu-id="33645-133">資源數目取決於哪些嚴重損壞修復環境在您選擇： 冷待命、 暖待命或熱待命。</span><span class="sxs-lookup"><span data-stu-id="33645-133">The number of resources depends on which disaster-recovery environment you choose: cold standby, warm standby, or hot standby.</span></span>
    
- <span data-ttu-id="33645-134">**更好的資源彈性**發生災害時，輕易地向外擴充復原 SharePoint 伺服器陣列以符合負載需求。</span><span class="sxs-lookup"><span data-stu-id="33645-134">**Better resource flexibility** In the event of a disaster, easily scale out your recovery SharePoint farm to meet load requirements.</span></span> <span data-ttu-id="33645-135">當您不再需要資源中比例調整。</span><span class="sxs-lookup"><span data-stu-id="33645-135">Scale in when you no longer need the resources.</span></span>
    
- <span data-ttu-id="33645-136">**較低的資料中心承諾**使用 Azure 基礎結構服務，而非投資位於不同地區的次要資料中心內。</span><span class="sxs-lookup"><span data-stu-id="33645-136">**Lower datacenter commitment** Use Azure Infrastructure Services instead of investing in a secondary datacenter in a different region.</span></span>
    
<span data-ttu-id="33645-137">有較不複雜組織只快速入門災害復原選項和進階選項具有高可靠度需求的組織。</span><span class="sxs-lookup"><span data-stu-id="33645-137">There are less-complex options for organizations just getting started with disaster recovery and advanced options for organizations with high-resilience requirements.</span></span> <span data-ttu-id="33645-138">在雲端平台上主控環境時，有點不同冷、 暖，及熱待命環境的定義。</span><span class="sxs-lookup"><span data-stu-id="33645-138">The definitions for cold, warm, and hot standby environments are a little different when the environment is hosted on a cloud platform.</span></span> <span data-ttu-id="33645-139">下表說明這些環境建置在 Azure 中的 SharePoint 復原伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="33645-139">The following table describes these environments for building a SharePoint recovery farm in Azure.</span></span>
  
<span data-ttu-id="33645-140">**表格： 復原環境**</span><span class="sxs-lookup"><span data-stu-id="33645-140">**Table: Recovery environments**</span></span>

|<span data-ttu-id="33645-141">**復原環境的類型**</span><span class="sxs-lookup"><span data-stu-id="33645-141">**Type of recovery environment**</span></span>|<span data-ttu-id="33645-142">**描述**</span><span class="sxs-lookup"><span data-stu-id="33645-142">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="33645-143">熱</span><span class="sxs-lookup"><span data-stu-id="33645-143">Hot</span></span>  <br/> |<span data-ttu-id="33645-144">完全調整大小的伺服器陣列已佈建、 更新，並執行處於待命狀態。</span><span class="sxs-lookup"><span data-stu-id="33645-144">A fully sized farm is provisioned, updated, and running on standby.</span></span>  <br/> |
|<span data-ttu-id="33645-145">暖</span><span class="sxs-lookup"><span data-stu-id="33645-145">Warm</span></span>  <br/> |<span data-ttu-id="33645-146">內建在伺服器陣列和虛擬機器執行及更新。</span><span class="sxs-lookup"><span data-stu-id="33645-146">The farm is built and virtual machines are running and updated.</span></span>  <br/> <span data-ttu-id="33645-147">復原作業包含附加內容資料庫、 佈建服務應用程式，以及編目的內容。</span><span class="sxs-lookup"><span data-stu-id="33645-147">Recovery includes attaching content databases, provisioning service applications, and crawling content.</span></span>  <br/> <span data-ttu-id="33645-148">在伺服器陣列可以是實際執行伺服器陣列較小版本，且再向外延展到完整的使用者提供服務。</span><span class="sxs-lookup"><span data-stu-id="33645-148">The farm can be a smaller version of the production farm and then scaled out to serve the full user base.</span></span>  <br/> |
|<span data-ttu-id="33645-149">冷</span><span class="sxs-lookup"><span data-stu-id="33645-149">Cold</span></span>  <br/> |<span data-ttu-id="33645-150">完全建置在伺服器陣列，但會停止虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="33645-150">The farm is fully built, but the virtual machines are stopped.</span></span>  <br/> <span data-ttu-id="33645-151">維護環境包含隨時啟動虛擬機器、 修補程式、 更新及驗證環境。</span><span class="sxs-lookup"><span data-stu-id="33645-151">Maintaining the environment includes starting the virtual machines from time to time, patching, updating, and verifying the environment.</span></span>  <br/> <span data-ttu-id="33645-152">啟動完整的環境發生嚴重損壞。</span><span class="sxs-lookup"><span data-stu-id="33645-152">Start the full environment in the event of a disaster.</span></span>  <br/> |
   
<span data-ttu-id="33645-153">請務必評估貴組織的復原時間目標 (Rto) 和復原點目標 (Rpo)。</span><span class="sxs-lookup"><span data-stu-id="33645-153">It's important to evaluate your organization's Recovery Time Objectives (RTOs) and Recovery Point Objectives (RPOs).</span></span> <span data-ttu-id="33645-154">這些需求，決定哪些環境是最適合貴組織的投資。</span><span class="sxs-lookup"><span data-stu-id="33645-154">These requirements determine which environment is the most appropriate investment for your organization.</span></span>
  
<span data-ttu-id="33645-155">本文中的指引說明如何實作暖待命環境。</span><span class="sxs-lookup"><span data-stu-id="33645-155">The guidance in this article describes how to implement a warm standby environment.</span></span> <span data-ttu-id="33645-156">您可以也適應它冷待命環境中，雖然您必須遵循額外的程序，以支援這類環境。</span><span class="sxs-lookup"><span data-stu-id="33645-156">You can also adapt it to a cold standby environment, although you need to follow additional procedures to support this kind of environment.</span></span> <span data-ttu-id="33645-157">本文不會說明如何實作熱待命環境。</span><span class="sxs-lookup"><span data-stu-id="33645-157">This article does not describe how to implement a hot standby environment.</span></span>
  
<span data-ttu-id="33645-158">如需災害復原解決方案的詳細資訊，請參閱[高可用性和 SharePoint 2013 的災害復原概念](https://go.microsoft.com/fwlink/p/?LinkID=393114)和[選擇 SharePoint 2013 的災害復原策略](https://go.microsoft.com/fwlink/p/?linkid=203228)。</span><span class="sxs-lookup"><span data-stu-id="33645-158">For more information about disaster recovery solutions, see [High availability and disaster recovery concepts in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkID=393114) and [Choose a disaster recovery strategy for SharePoint 2013](https://go.microsoft.com/fwlink/p/?linkid=203228).</span></span>
  
## <a name="solution-description"></a><span data-ttu-id="33645-159">解決方案說明</span><span class="sxs-lookup"><span data-stu-id="33645-159">Solution description</span></span>

<span data-ttu-id="33645-160">暖待命災害復原解決方案需要下列環境：</span><span class="sxs-lookup"><span data-stu-id="33645-160">The warm standby disaster-recovery solution requires the following environment:</span></span>
  
- <span data-ttu-id="33645-161">內部部署 SharePoint 實際執行伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="33645-161">An on-premises SharePoint production farm</span></span>
    
- <span data-ttu-id="33645-162">在 Azure 中復原 SharePoint 伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="33645-162">A recovery SharePoint farm in Azure</span></span>
    
- <span data-ttu-id="33645-163">兩個環境之間的站台對站 VPN 連線</span><span class="sxs-lookup"><span data-stu-id="33645-163">A site-to-site VPN connection between the two environments</span></span>
    
<span data-ttu-id="33645-164">下圖說明這三個元素。</span><span class="sxs-lookup"><span data-stu-id="33645-164">The following figure illustrates these three elements.</span></span>
  
<span data-ttu-id="33645-165">**圖： 在 Azure 中暖待命解決方案的項目**</span><span class="sxs-lookup"><span data-stu-id="33645-165">**Figure: Elements of a warm standby solution in Azure**</span></span>

![Azure 中 SharePoint 暖待命解決方案的元素](media/AZarch-AZWarmStndby.png)
  
<span data-ttu-id="33645-167">SQL Server 記錄傳送與分散式檔案系統複寫 (DFSR) 用於將資料庫備份和交易記錄檔複製到在 Azure 中的復原伺服器陣列：</span><span class="sxs-lookup"><span data-stu-id="33645-167">SQL Server log shipping with Distributed File System Replication (DFSR) is used to copy database backups and transaction logs to the recovery farm in Azure:</span></span> 
  
- <span data-ttu-id="33645-168">DFSR 會將記錄從實際執行環境傳送至復原環境。</span><span class="sxs-lookup"><span data-stu-id="33645-168">DFSR transfers logs from the production environment to the recovery environment.</span></span> <span data-ttu-id="33645-169">在 WAN 案例中，DFSR 比直接將記錄傳送至 Azure 中的次要伺服器更為有效率。</span><span class="sxs-lookup"><span data-stu-id="33645-169">In a WAN scenario, DFSR is more efficient than shipping the logs directly to the secondary server in Azure.</span></span>
    
- <span data-ttu-id="33645-170">記錄檔會重新顯示到 Azure 中在復原環境中的 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="33645-170">Logs are replayed to the SQL Server in the recovery environment in Azure.</span></span>
    
- <span data-ttu-id="33645-171">除非執行復原練習，否則，您不附加記錄傳送 SharePoint 內容資料庫在復原環境中。</span><span class="sxs-lookup"><span data-stu-id="33645-171">You don't attach log-shipped SharePoint content databases in the recovery environment until a recovery exercise is performed.</span></span>
    
<span data-ttu-id="33645-172">執行下列步驟，以復原伺服器陣列：</span><span class="sxs-lookup"><span data-stu-id="33645-172">Perform the following steps to recover the farm:</span></span>
  
1. <span data-ttu-id="33645-173">停止記錄傳送。</span><span class="sxs-lookup"><span data-stu-id="33645-173">Stop log shipping.</span></span>
    
2. <span data-ttu-id="33645-174">停止接受主要伺服器陣列的流量。</span><span class="sxs-lookup"><span data-stu-id="33645-174">Stop accepting traffic to the primary farm.</span></span>
    
3. <span data-ttu-id="33645-175">重新顯示的最後一筆交易記錄檔。</span><span class="sxs-lookup"><span data-stu-id="33645-175">Replay the final transaction logs.</span></span>
    
4. <span data-ttu-id="33645-176">將內容資料庫附加至伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="33645-176">Attach the content databases to the farm.</span></span>
    
5. <span data-ttu-id="33645-177">複寫的服務資料庫還原服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="33645-177">Restore service applications from the replicated services databases.</span></span>
    
6. <span data-ttu-id="33645-178">更新以指到復原伺服器陣列的網域名稱系統 (DNS) 記錄。</span><span class="sxs-lookup"><span data-stu-id="33645-178">Update Domain Name System (DNS) records to point to the recovery farm.</span></span>
    
7. <span data-ttu-id="33645-179">開始完整編目。</span><span class="sxs-lookup"><span data-stu-id="33645-179">Start a full crawl.</span></span>
    
<span data-ttu-id="33645-180">我們建議您定期排練這些步驟，並記錄以協助確保您 live 復原順暢執行。</span><span class="sxs-lookup"><span data-stu-id="33645-180">We recommend that you rehearse these steps regularly and document them to help ensure that your live recovery runs smoothly.</span></span> <span data-ttu-id="33645-181">附加內容資料庫並還原服務應用程式可能需要一些時間，而且通常牽涉到某些手動設定。</span><span class="sxs-lookup"><span data-stu-id="33645-181">Attaching content databases and restoring service applications can take some time and typically involves some manual configuration.</span></span>
  
<span data-ttu-id="33645-182">執行復原之後，此解決方案會提供下列表格所列出的項目。</span><span class="sxs-lookup"><span data-stu-id="33645-182">After a recovery is performed, this solution provides the items listed in the following table.</span></span>
  
<span data-ttu-id="33645-183">**表格： 方案復原目標**</span><span class="sxs-lookup"><span data-stu-id="33645-183">**Table: Solution recovery objectives**</span></span>

|<span data-ttu-id="33645-184">**項目**</span><span class="sxs-lookup"><span data-stu-id="33645-184">**Item**</span></span>|<span data-ttu-id="33645-185">**描述**</span><span class="sxs-lookup"><span data-stu-id="33645-185">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="33645-186">網站和內容</span><span class="sxs-lookup"><span data-stu-id="33645-186">Sites and content</span></span>  <br/> |<span data-ttu-id="33645-187">網站和內容可在復原環境中。</span><span class="sxs-lookup"><span data-stu-id="33645-187">Sites and content are available in the recovery environment.</span></span>  <br/> |
|<span data-ttu-id="33645-188">搜尋的新執行個體</span><span class="sxs-lookup"><span data-stu-id="33645-188">A new instance of search</span></span>  <br/> |<span data-ttu-id="33645-189">在此暖待命解決方案，不會從搜尋資料庫還原搜尋。</span><span class="sxs-lookup"><span data-stu-id="33645-189">In this warm standby solution, search is not restored from search databases.</span></span> <span data-ttu-id="33645-190">復原伺服器陣列中的搜尋元件設定為 [同樣地，儘可能在實際執行伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="33645-190">Search components in the recovery farm are configured as similarly as possible to the production farm.</span></span> <span data-ttu-id="33645-191">還原網站與內容後，啟動完整編目時將搜尋索引重建。</span><span class="sxs-lookup"><span data-stu-id="33645-191">After the sites and content are restored, a full crawl is started to rebuild the search index.</span></span> <span data-ttu-id="33645-192">您不需要等待完成要提供的網站和內容編目。</span><span class="sxs-lookup"><span data-stu-id="33645-192">You do not need to wait for the crawl to complete to make the sites and content available.</span></span>  <br/> |
|<span data-ttu-id="33645-193">服務</span><span class="sxs-lookup"><span data-stu-id="33645-193">Services</span></span>  <br/> | <span data-ttu-id="33645-194">從記錄傳送的資料庫還原資料儲存在資料庫的服務。</span><span class="sxs-lookup"><span data-stu-id="33645-194">Services that store data in databases are restored from the log-shipped databases.</span></span> <span data-ttu-id="33645-195">只要啟動服務，請勿在資料庫中儲存的資料。</span><span class="sxs-lookup"><span data-stu-id="33645-195">Services that do not store data in databases are simply started.</span></span> <br/>  <span data-ttu-id="33645-196">並非所有的服務與資料庫需要進行還原。</span><span class="sxs-lookup"><span data-stu-id="33645-196">Not all services with databases need to be restored.</span></span> <span data-ttu-id="33645-197">下列服務不需要還原的資料庫，且只可以啟動容錯移轉後：</span><span class="sxs-lookup"><span data-stu-id="33645-197">The following services do not need to be restored from databases and can simply be started after failover:</span></span> <br/>  <span data-ttu-id="33645-198">Usage and Health Data Collection</span><span class="sxs-lookup"><span data-stu-id="33645-198">Usage and Health Data Collection</span></span> <br/>  <span data-ttu-id="33645-199">State service</span><span class="sxs-lookup"><span data-stu-id="33645-199">State service</span></span> <br/>  <span data-ttu-id="33645-200">Word automation</span><span class="sxs-lookup"><span data-stu-id="33645-200">Word automation</span></span> <br/>  <span data-ttu-id="33645-201">不使用資料庫的任何其他服務</span><span class="sxs-lookup"><span data-stu-id="33645-201">Any other service that doesn't use a database</span></span> <br/> |
   
<span data-ttu-id="33645-202">您可以使用 Microsoft 諮詢服務 (MCS) 或協力廠商地址較複雜復原目標。</span><span class="sxs-lookup"><span data-stu-id="33645-202">You can work with Microsoft Consulting Services (MCS) or a partner to address more-complex recovery objectives.</span></span> <span data-ttu-id="33645-203">下表摘要說明。</span><span class="sxs-lookup"><span data-stu-id="33645-203">These are summarized in the following table.</span></span>
  
<span data-ttu-id="33645-204">**表格： 其他項目可以 MCS 或協力廠商所提到**</span><span class="sxs-lookup"><span data-stu-id="33645-204">**Table: Other items that can be addressed by MCS or a partner**</span></span>

|<span data-ttu-id="33645-205">**項目**</span><span class="sxs-lookup"><span data-stu-id="33645-205">**Item**</span></span>|<span data-ttu-id="33645-206">**描述**</span><span class="sxs-lookup"><span data-stu-id="33645-206">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="33645-207">同步處理自訂伺服器陣列解決方案</span><span class="sxs-lookup"><span data-stu-id="33645-207">Synchronizing custom farm solutions</span></span>  <br/> |<span data-ttu-id="33645-208">理想狀況下，復原伺服器陣列設定為相同的實際執行伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="33645-208">Ideally, the recovery farm configuration is identical to the production farm.</span></span> <span data-ttu-id="33645-209">您可以使用顧問或協力廠商評估自訂伺服器陣列解決方案會複寫以及是否程序已經保持同步處理兩個環境準備就緒。</span><span class="sxs-lookup"><span data-stu-id="33645-209">You can work with a consultant or partner to evaluate whether custom farm solutions are replicated and whether the process is in place for keeping the two environments synchronized.</span></span>  <br/> |
|<span data-ttu-id="33645-210">連線至資料來源內部部署</span><span class="sxs-lookup"><span data-stu-id="33645-210">Connections to data sources on-premises</span></span>  <br/> |<span data-ttu-id="33645-211">它可能不是實際複寫至後端資料系統，例如備份網域控制站 (BDC) 連線及搜尋內容來源的連線。</span><span class="sxs-lookup"><span data-stu-id="33645-211">It might not be practical to replicate connections to back-end data systems, such as backup domain controller (BDC) connections and search content sources.</span></span>  <br/> |
|<span data-ttu-id="33645-212">搜尋還原案例</span><span class="sxs-lookup"><span data-stu-id="33645-212">Search restore scenarios</span></span>  <br/> |<span data-ttu-id="33645-213">企業搜尋部署通常是相當唯一且複雜，因為從資料庫還原搜尋需要更多投資。</span><span class="sxs-lookup"><span data-stu-id="33645-213">Because enterprise search deployments tend to be fairly unique and complex, restoring search from databases requires a greater investment.</span></span> <span data-ttu-id="33645-214">您可以使用顧問或協力廠商，以找出並實作您的組織可能需要的搜尋還原案例。</span><span class="sxs-lookup"><span data-stu-id="33645-214">You can work with a consultant or partner to identify and implement search restore scenarios that your organization might require.</span></span>  <br/> |
   
<span data-ttu-id="33645-215">本文中提供的指導假設在內部部署伺服器陣列已設計及部署。</span><span class="sxs-lookup"><span data-stu-id="33645-215">The guidance provided in this article assumes that the on-premises farm is already designed and deployed.</span></span>
  
## <a name="detailed-architecture"></a><span data-ttu-id="33645-216">詳細架構</span><span class="sxs-lookup"><span data-stu-id="33645-216">Detailed architecture</span></span>

<span data-ttu-id="33645-217">理想狀況下，在 Azure 中的復原伺服器陣列設定為相同的實際執行伺服器陣列上部署，包括下列：</span><span class="sxs-lookup"><span data-stu-id="33645-217">Ideally, the recovery farm configuration in Azure is identical to the production farm on-premises, including the following:</span></span>
  
- <span data-ttu-id="33645-218">伺服器角色之相同的表示法</span><span class="sxs-lookup"><span data-stu-id="33645-218">The same representation of server roles</span></span>
    
- <span data-ttu-id="33645-219">自訂項目的相同的設定</span><span class="sxs-lookup"><span data-stu-id="33645-219">The same configuration of customizations</span></span>
    
- <span data-ttu-id="33645-220">搜尋元件的相同的設定</span><span class="sxs-lookup"><span data-stu-id="33645-220">The same configuration of search components</span></span>
    
<span data-ttu-id="33645-221">在 Azure 中的環境可以是實際執行伺服器陣列較小版本。</span><span class="sxs-lookup"><span data-stu-id="33645-221">The environment in Azure can be a smaller version of the production farm.</span></span> <span data-ttu-id="33645-222">如果您打算向外擴充的復原伺服器陣列容錯移轉之後，請務必最初以表示每一種伺服器角色。</span><span class="sxs-lookup"><span data-stu-id="33645-222">If you plan to scale out the recovery farm after failover, it's important that each type of server role be initially represented.</span></span>
  
<span data-ttu-id="33645-223">某些組態中可能不是實際容錯移轉環境中複寫。</span><span class="sxs-lookup"><span data-stu-id="33645-223">Some configurations might not be practical to replicate in the failover environment.</span></span> <span data-ttu-id="33645-224">請務必測試環境，以協助確保容錯移轉伺服器陣列提供預期的服務層級與容錯移轉程序。</span><span class="sxs-lookup"><span data-stu-id="33645-224">Be sure to test the failover procedures and environment to help ensure that the failover farm provides the expected service level.</span></span>
  
<span data-ttu-id="33645-225">此方案，不會擬定 SharePoint 伺服器陣列的特定拓撲。</span><span class="sxs-lookup"><span data-stu-id="33645-225">This solution doesn't prescribe a specific topology for a SharePoint farm.</span></span> <span data-ttu-id="33645-226">此解決方案的重點是 Azure 用於容錯移轉伺服器陣列，並實作在兩個環境之間的記錄傳送和 DFSR。</span><span class="sxs-lookup"><span data-stu-id="33645-226">The focus of this solution is to use Azure for the failover farm and to implement log shipping and DFSR between the two environments.</span></span>
  
### <a name="warm-standby-environments"></a><span data-ttu-id="33645-227">暖待命環境</span><span class="sxs-lookup"><span data-stu-id="33645-227">Warm standby environments</span></span>

<span data-ttu-id="33645-228">在暖待命環境中，執行的 Azure 環境中的所有虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="33645-228">In a warm standby environment, all virtual machines in the Azure environment are running.</span></span> <span data-ttu-id="33645-229">環境可供容錯移轉執行或事件。</span><span class="sxs-lookup"><span data-stu-id="33645-229">The environment is ready for a failover exercise or event.</span></span>
  
<span data-ttu-id="33645-230">下圖說明從內部部署 SharePoint 伺服器陣列已設定為暖待命環境，以 Azure 為基礎的 SharePoint 伺服器陣列的災害復原解決方案。</span><span class="sxs-lookup"><span data-stu-id="33645-230">The following figure illustrates a disaster recovery solution from an on-premises SharePoint farm to an Azure-based SharePoint farm that is configured as a warm standby environment.</span></span>
  
<span data-ttu-id="33645-231">**圖： 拓撲和重要元素的實際執行伺服器陣列和暖待命復原伺服器陣列**</span><span class="sxs-lookup"><span data-stu-id="33645-231">**Figure: Topology and key elements of a production farm and a warm standby recovery farm**</span></span>

![SharePoint 伺服器陣列和暖待命復原伺服器陣列的拓撲](media/AZarch-AZWarmStndby.png)
  
<span data-ttu-id="33645-233">在此圖表中：</span><span class="sxs-lookup"><span data-stu-id="33645-233">In this diagram:</span></span>
  
- <span data-ttu-id="33645-234">並排說明兩個環境： 內部部署 SharePoint 伺服器陣列以及 Azure 中的暖待命伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="33645-234">Two environments are illustrated side by side: the on-premises SharePoint farm and the warm standby farm in Azure.</span></span>
    
- <span data-ttu-id="33645-235">每個環境都包括檔案共用。</span><span class="sxs-lookup"><span data-stu-id="33645-235">Each environment includes a file share.</span></span>
    
- <span data-ttu-id="33645-236">每個伺服器陣列包含四個層級。</span><span class="sxs-lookup"><span data-stu-id="33645-236">Each farm includes four tiers.</span></span> <span data-ttu-id="33645-237">若要達到高可用性，每一層包含兩個伺服器或特定角色，例如前端服務、 分散式快取、 後端服務，以及資料庫的設定都相同的虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="33645-237">To achieve high availability, each tier includes two servers or virtual machines that are configured identically for a specific role, such as front-end services, distributed cache, back-end services, and databases.</span></span> <span data-ttu-id="33645-238">它不重要對外特定元件呼叫此圖例中。</span><span class="sxs-lookup"><span data-stu-id="33645-238">It isn't important in this illustration to call out specific components.</span></span> <span data-ttu-id="33645-239">兩個伺服器陣列的設定都相同。</span><span class="sxs-lookup"><span data-stu-id="33645-239">The two farms are configured identically.</span></span>
    
- <span data-ttu-id="33645-240">第四個層是資料庫層。</span><span class="sxs-lookup"><span data-stu-id="33645-240">The fourth tier is the database tier.</span></span> <span data-ttu-id="33645-241">記錄傳送用來將記錄從內部部署環境中的次要資料庫伺服器複製到相同的環境中的檔案共用。</span><span class="sxs-lookup"><span data-stu-id="33645-241">Log shipping is used to copy logs from the secondary database server in the on-premises environment to the file share in the same environment.</span></span>
    
- <span data-ttu-id="33645-242">DFSR 會將檔案從內部部署環境中的檔案共用複製至 Azure 環境中的檔案共用。</span><span class="sxs-lookup"><span data-stu-id="33645-242">DFSR copies files from the file share in the on-premises environment to the file share in the Azure environment.</span></span>
    
- <span data-ttu-id="33645-243">記錄傳送會將記錄從 Azure 環境中的檔案共用重新執行至復原環境的 SQL Server AlwaysOn 可用性群組中的主要複本。</span><span class="sxs-lookup"><span data-stu-id="33645-243">Log shipping replays the logs from the file share in the Azure environment to the primary replica in the SQL Server AlwaysOn availability group in the recovery environment.</span></span>
    
### <a name="cold-standby-environments"></a><span data-ttu-id="33645-244">冷待命環境</span><span class="sxs-lookup"><span data-stu-id="33645-244">Cold standby environments</span></span>

<span data-ttu-id="33645-245">在冷待命環境中，大部分的 SharePoint 伺服器陣列虛擬機器可以關閉。</span><span class="sxs-lookup"><span data-stu-id="33645-245">In a cold standby environment, most of the SharePoint farm virtual machines can be shut down.</span></span> <span data-ttu-id="33645-246">（建議有時會啟動虛擬機器，例如每兩週或月，一次，讓每個虛擬機器可以與網域同步處理）。在 Azure 復原環境中的下列虛擬機器必須保持執行以協助確保記錄傳送及 DFSR 連續作業：</span><span class="sxs-lookup"><span data-stu-id="33645-246">(We recommend occasionally starting the virtual machines, such as every two weeks or once a month, so that each virtual machine can sync with the domain.) The following virtual machines in the Azure recovery environment must remain running to help ensure continuous operations of log shipping and DFSR:</span></span>
  
- <span data-ttu-id="33645-247">檔案共用</span><span class="sxs-lookup"><span data-stu-id="33645-247">The file share</span></span>
    
- <span data-ttu-id="33645-248">主要資料庫伺服器</span><span class="sxs-lookup"><span data-stu-id="33645-248">The primary database server</span></span>
    
- <span data-ttu-id="33645-249">執行 Windows Server Active Directory 網域服務和 DNS 的至少一部虛擬機器</span><span class="sxs-lookup"><span data-stu-id="33645-249">At least one virtual machine running Windows Server Active Directory Domain Services and DNS</span></span>
    
<span data-ttu-id="33645-250">下圖顯示 Azure 容錯移轉環境中執行檔案共用虛擬機器和主要的 SharePoint 資料庫虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="33645-250">The following figure shows an Azure failover environment in which the file share virtual machine and the primary SharePoint database virtual machine are running.</span></span> <span data-ttu-id="33645-251">所有其他 SharePoint 虛擬機器會停止。</span><span class="sxs-lookup"><span data-stu-id="33645-251">All other SharePoint virtual machines are stopped.</span></span> <span data-ttu-id="33645-252">正在執行 Windows Server Active Directory 和 DNS 虛擬機器時不會顯示。</span><span class="sxs-lookup"><span data-stu-id="33645-252">The virtual machine that is running Windows Server Active Directory and DNS is not shown.</span></span>
  
<span data-ttu-id="33645-253">**圖： 冷待命復原伺服器陣列與執行虛擬機器**</span><span class="sxs-lookup"><span data-stu-id="33645-253">**Figure: Cold standby recovery farm with running virtual machines**</span></span>

![Azure 中 SharePoint 冷待命解決方案的元素](media/AZarch-AZColdStndby.png)
  
<span data-ttu-id="33645-255">容錯移轉之後以冷待命環境，並啟動所有虛擬機器，和方法來達到高可用性的資料庫伺服器必須設定，例如 SQL Server AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="33645-255">After failover to a cold standby environment, all virtual machines are started, and the method to achieve high availability of the database servers must be configured, such as SQL Server AlwaysOn availability groups.</span></span>
  
<span data-ttu-id="33645-256">如果已實作多個儲存群組 （資料庫分散於多個 SQL Server 高可用性設定組），每個儲存群組的主要資料庫都必須執行接受其儲存群組相關聯的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="33645-256">If multiple storage groups are implemented (databases are spread across more than one SQL Server high availability set), the primary database for each storage group must be running to accept the logs associated with its storage group.</span></span>
  
### <a name="skills-and-experience"></a><span data-ttu-id="33645-257">技能與經驗</span><span class="sxs-lookup"><span data-stu-id="33645-257">Skills and experience</span></span>

<span data-ttu-id="33645-258">在這個災害復原解決方案可用多重技術。</span><span class="sxs-lookup"><span data-stu-id="33645-258">Multiple technologies are used in this disaster recovery solution.</span></span> <span data-ttu-id="33645-259">為了協助確保這些技術互動如預期般，必須安裝並正確設定內部部署和 Azure 環境中的每個元件。</span><span class="sxs-lookup"><span data-stu-id="33645-259">To help ensure that these technologies interact as expected, each component in the on-premises and Azure environment must be installed and configured correctly.</span></span> <span data-ttu-id="33645-260">建議的人員或團隊會設定此解決方案，使用下列文章所述的技術也有的強式工作知識與實機操作技能：</span><span class="sxs-lookup"><span data-stu-id="33645-260">We recommend that the person or team who sets up this solution have a strong working knowledge of and hands-on skills with the technologies described in the following articles:</span></span>
  
- [<span data-ttu-id="33645-261">分散式的檔案系統 (DFS) 複寫服務</span><span class="sxs-lookup"><span data-stu-id="33645-261">Distributed File System (DFS) Replication Services</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392698)
    
- [<span data-ttu-id="33645-262">Windows Server 容錯移轉叢集 (WSFC) 和 SQL Server</span><span class="sxs-lookup"><span data-stu-id="33645-262">Windows Server Failover Clustering (WSFC) with SQL Server</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392701)
    
- [<span data-ttu-id="33645-263">AlwaysOn 可用性群組 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="33645-263">AlwaysOn Availability Groups (SQL Server)</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392725)
    
- [<span data-ttu-id="33645-264">備份及還原的 SQL Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="33645-264">Back Up and Restore of SQL Server Databases</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392728)
    
- [<span data-ttu-id="33645-265">SharePoint Server 2013 安裝和伺服器陣列部署</span><span class="sxs-lookup"><span data-stu-id="33645-265">SharePoint Server 2013 installation and farm deployment</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=393119)
    
- [<span data-ttu-id="33645-266">Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="33645-266">Microsoft Azure</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392729)
    
<span data-ttu-id="33645-267">最後，我們建議指令碼，您可以使用這些技術相關聯的工作自動化的技術。</span><span class="sxs-lookup"><span data-stu-id="33645-267">Finally, we recommend scripting skills that you can use to automate tasks associated with these technologies.</span></span> <span data-ttu-id="33645-268">就可以使用可用的使用者介面來完成此解決方案所述的所有工作。</span><span class="sxs-lookup"><span data-stu-id="33645-268">It's possible to use the available user interfaces to complete all the tasks described in this solution.</span></span> <span data-ttu-id="33645-269">不過，手動的方式可耗用的時間和出錯，並將傳遞不一致的結果。</span><span class="sxs-lookup"><span data-stu-id="33645-269">However, a manual approach can be time consuming and error prone and delivers inconsistent results.</span></span>
  
<span data-ttu-id="33645-270">除了 Windows PowerShell 中，也有 SQL Server、 SharePoint Server 中，和 Azure 的 Windows PowerShell 文件庫。</span><span class="sxs-lookup"><span data-stu-id="33645-270">In addition to Windows PowerShell, there are also Windows PowerShell libraries for SQL Server, SharePoint Server, and Azure.</span></span> <span data-ttu-id="33645-271">別忘了 T-SQL，這也有助於減少來設定和維護您的災害復原環境的時間。</span><span class="sxs-lookup"><span data-stu-id="33645-271">Don't forget T-SQL, which can also help reduce the time to configure and maintain your disaster-recovery environment.</span></span>
  
## <a name="disaster-recovery-roadmap"></a><span data-ttu-id="33645-272">嚴重損壞修復藍圖</span><span class="sxs-lookup"><span data-stu-id="33645-272">Disaster recovery roadmap</span></span>

![SharePoint 嚴重損壞修復藍圖的視覺表示法。](media/Azure-DRroadmap.png)
  
<span data-ttu-id="33645-274">此藍圖假設您已部署在生產環境中的 SharePoint Server 2013 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="33645-274">This roadmap assumes that you already have a SharePoint Server 2013 farm deployed in production.</span></span>
  
<span data-ttu-id="33645-275"><b0>表格: < Roadmap for 嚴重損壞修復</b0></span><span class="sxs-lookup"><span data-stu-id="33645-275">**Table: Roadmap for disaster recovery**</span></span>

|<span data-ttu-id="33645-276">**階段**</span><span class="sxs-lookup"><span data-stu-id="33645-276">**Phase**</span></span>|<span data-ttu-id="33645-277">**描述**</span><span class="sxs-lookup"><span data-stu-id="33645-277">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="33645-278">階段 1</span><span class="sxs-lookup"><span data-stu-id="33645-278">Phase 1</span></span>  <br/> |<span data-ttu-id="33645-279">設計災害復原環境。</span><span class="sxs-lookup"><span data-stu-id="33645-279">Design the disaster recovery environment.</span></span>  <br/> |
|<span data-ttu-id="33645-280">階段 2</span><span class="sxs-lookup"><span data-stu-id="33645-280">Phase 2</span></span>  <br/> |<span data-ttu-id="33645-281">建立 Azure 虛擬網路和 VPN 連線。</span><span class="sxs-lookup"><span data-stu-id="33645-281">Create the Azure virtual network and VPN connection.</span></span>  <br/> |
|<span data-ttu-id="33645-282">階段 3</span><span class="sxs-lookup"><span data-stu-id="33645-282">Phase 3</span></span>  <br/> |<span data-ttu-id="33645-283">將 Windows Active Directory 和網域名稱服務部署到 Azure 虛擬網路。</span><span class="sxs-lookup"><span data-stu-id="33645-283">Deploy Windows Active Directory and Domain Name Services to the Azure virtual network.</span></span>  <br/> |
|<span data-ttu-id="33645-284">階段 4</span><span class="sxs-lookup"><span data-stu-id="33645-284">Phase 4</span></span>  <br/> |<span data-ttu-id="33645-285">部署在 Azure 中的 SharePoint 復原伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="33645-285">Deploy the SharePoint recovery farm in Azure.</span></span>  <br/> |
|<span data-ttu-id="33645-286">階段 5</span><span class="sxs-lookup"><span data-stu-id="33645-286">Phase 5</span></span>  <br/> |<span data-ttu-id="33645-287">設定伺服器陣列之間的 DFSR。</span><span class="sxs-lookup"><span data-stu-id="33645-287">Set up DFSR between the farms.</span></span>  <br/> |
|<span data-ttu-id="33645-288">階段 6</span><span class="sxs-lookup"><span data-stu-id="33645-288">Phase 6</span></span>  <br/> |<span data-ttu-id="33645-289">設定記錄傳送至復原伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="33645-289">Set up log shipping to the recovery farm.</span></span>  <br/> |
|<span data-ttu-id="33645-290">第 7 階段</span><span class="sxs-lookup"><span data-stu-id="33645-290">Phase 7</span></span>  <br/> | <span data-ttu-id="33645-291">驗證容錯移轉和復原解決方案。</span><span class="sxs-lookup"><span data-stu-id="33645-291">Validate failover and recovery solutions.</span></span> <span data-ttu-id="33645-292">這包括下列程序和技術：</span><span class="sxs-lookup"><span data-stu-id="33645-292">This includes the following procedures and technologies:</span></span> <br/>  <span data-ttu-id="33645-293">停止記錄傳送。</span><span class="sxs-lookup"><span data-stu-id="33645-293">Stop log shipping.</span></span> <br/>  <span data-ttu-id="33645-294">還原的備份。</span><span class="sxs-lookup"><span data-stu-id="33645-294">Restore the backups.</span></span> <br/>  <span data-ttu-id="33645-295">編目內容。</span><span class="sxs-lookup"><span data-stu-id="33645-295">Crawl content.</span></span> <br/>  <span data-ttu-id="33645-296">復原服務。</span><span class="sxs-lookup"><span data-stu-id="33645-296">Recover services.</span></span> <br/>  <span data-ttu-id="33645-297">管理 DNS 記錄。</span><span class="sxs-lookup"><span data-stu-id="33645-297">Manage DNS records.</span></span> <br/> |
   
## <a name="phase-1-design-the-disaster-recovery-environment"></a><span data-ttu-id="33645-298">階段 1： 設計災害復原環境</span><span class="sxs-lookup"><span data-stu-id="33645-298">Phase 1: Design the disaster recovery environment</span></span>

<span data-ttu-id="33645-299">使用[Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)中的指導方針，來設計嚴重損壞修復環境，包括 SharePoint 復原伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="33645-299">Use the guidance in [Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) to design the disaster-recovery environment, including the SharePoint recovery farm.</span></span> <span data-ttu-id="33645-300">您可以使用[Azure 中的 SharePoint 災害復原解決方案](https://go.microsoft.com/fwlink/p/?LinkId=392554)Visio 檔案中的圖形，開始設計程序。</span><span class="sxs-lookup"><span data-stu-id="33645-300">You can use the graphics in the [SharePoint Disaster Recovery Solution in Azure](https://go.microsoft.com/fwlink/p/?LinkId=392554) Visio file to start the design process.</span></span> <span data-ttu-id="33645-301">我們建議您設計整個環境再開始 Azure 環境中的任何工作。</span><span class="sxs-lookup"><span data-stu-id="33645-301">We recommend that you design the entire environment before beginning any work in the Azure environment.</span></span>
  
<span data-ttu-id="33645-302">除了設計虛擬網路、 VPN 連線、 Active Directory，以及 SharePoint 伺服器陣列的[Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)中提供的指導，請務必將檔案共用角色新增至 Azure 環境。</span><span class="sxs-lookup"><span data-stu-id="33645-302">In addition to the guidance provided in [Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) for designing the virtual network, VPN connection, Active Directory, and SharePoint farm, be sure to add a file share role to the Azure environment.</span></span>
  
<span data-ttu-id="33645-303">若要支援災害復原解決方案中的記錄傳送，檔案共用虛擬機器新增至資料庫角色的所在位置的子網路。</span><span class="sxs-lookup"><span data-stu-id="33645-303">To support log shipping in a disaster-recovery solution, a file share virtual machine is added to the subnet where the database roles reside.</span></span> <span data-ttu-id="33645-304">檔案共用也可以做為 SQL Server AlwaysOn 可用性群組節點多數 」 的第三個節點。</span><span class="sxs-lookup"><span data-stu-id="33645-304">The file share also serves as the third node of a Node Majority for the SQL Server AlwaysOn availability group.</span></span> <span data-ttu-id="33645-305">這是使用 SQL Server AlwaysOn 可用性群組的標準 SharePoint 伺服器陣列的建議的組態。</span><span class="sxs-lookup"><span data-stu-id="33645-305">This is the recommended configuration for a standard SharePoint farm that uses SQL Server AlwaysOn availability groups.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="33645-306">請務必檢閱資料庫以參與的 SQL Server AlwaysOn 可用性群組的必要條件。</span><span class="sxs-lookup"><span data-stu-id="33645-306">It is important to review the prerequisites for a database to participate in a SQL Server AlwaysOn availability group.</span></span> <span data-ttu-id="33645-307">如需詳細資訊，請參閱[必要條件、 限制和建議 AlwaysOn 可用性群組](https://go.microsoft.com/fwlink/p/?LinkId=510870)。</span><span class="sxs-lookup"><span data-stu-id="33645-307">For more information, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups](https://go.microsoft.com/fwlink/p/?LinkId=510870).</span></span> 
  
<span data-ttu-id="33645-308">**圖： 用於災害復原解決方案的檔案伺服器的位置**</span><span class="sxs-lookup"><span data-stu-id="33645-308">**Figure: Placement of a file server used for a disaster recovery solution**</span></span>

![顯示新增至含有 SharePoint 資料庫伺服器角色之相同雲端服務的檔案共用 VM。](media/AZenv-FSforDFSRandWSFC.png)
  
<span data-ttu-id="33645-310">在此圖表中，在檔案共用虛擬機器新增至相同的子網路，在 Azure 中含有資料庫伺服器角色。</span><span class="sxs-lookup"><span data-stu-id="33645-310">In this diagram, a file share virtual machine is added to the same subnet in Azure that contains the database server roles.</span></span> <span data-ttu-id="33645-311">不要將檔案共用虛擬機器加入的可用性設定組與其他伺服器角色，例如 SQL Server 角色。</span><span class="sxs-lookup"><span data-stu-id="33645-311">Do not add the file share virtual machine to an availability set with other server roles, such as the SQL Server roles.</span></span>
  
<span data-ttu-id="33645-312">如果您擔心記錄檔的高可用性，請考慮使用[SQL Server 備份及還原與 Azure Blob 儲存體服務](https://go.microsoft.com/fwlink/p/?LinkId=393113)採取不同的方法。</span><span class="sxs-lookup"><span data-stu-id="33645-312">If you are concerned about the high availability of the logs, consider taking a different approach by using [SQL Server backup and restore with Azure Blob Storage Service](https://go.microsoft.com/fwlink/p/?LinkId=393113).</span></span> <span data-ttu-id="33645-313">這是記錄直接儲存到 blob 存放區 URL 的 Azure 中的新功能。</span><span class="sxs-lookup"><span data-stu-id="33645-313">This is a new feature in Azure that saves logs directly to a blob storage URL.</span></span> <span data-ttu-id="33645-314">此解決方案不包括使用這項功能的相關指引。</span><span class="sxs-lookup"><span data-stu-id="33645-314">This solution does not include guidance about using this feature.</span></span>
  
<span data-ttu-id="33645-315">當您設計的復原伺服器陣列時，請記住，成功的災害復原環境才會正確反映實際執行伺服器陣列，您想要復原。</span><span class="sxs-lookup"><span data-stu-id="33645-315">When you design the recovery farm, keep in mind that a successful disaster recovery environment accurately reflects the production farm that you want to recover.</span></span> <span data-ttu-id="33645-316">復原伺服器陣列的大小不是最重要的是在復原伺服器陣列設計、 部署及測試。</span><span class="sxs-lookup"><span data-stu-id="33645-316">The size of the recovery farm is not the most important thing in the recovery farm's design, deployment, and testing.</span></span> <span data-ttu-id="33645-317">伺服器陣列規模而異從組織中，根據商務需求的組織。</span><span class="sxs-lookup"><span data-stu-id="33645-317">Farm scale varies from organization to organization based on business requirements.</span></span> <span data-ttu-id="33645-318">它可能會出現短暫的中斷，或直到效能和容量需求需要擴充伺服器陣列使用縮小的伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="33645-318">It might be possible to use a scaled-down farm for a short outage or until performance and capacity demands require you to scale the farm.</span></span>
  
<span data-ttu-id="33645-319">至實際執行伺服器陣列儘可能具有相同設定復原伺服器陣列，使其符合您的服務等級協定 (SLA) 需求，並提供您需要支援貴公司的功能。</span><span class="sxs-lookup"><span data-stu-id="33645-319">Configure the recovery farm as identically as possible to the production farm so that it meets your service level agreement (SLA) requirements and provides the functionality that you need to support your business.</span></span> <span data-ttu-id="33645-320">當您設計損毀修復環境時，也請查看變更管理處理程序，為您的實際執行環境。</span><span class="sxs-lookup"><span data-stu-id="33645-320">When you design the disaster recovery environment, also look at your change management process for your production environment.</span></span> <span data-ttu-id="33645-321">我們建議您延伸至復原環境的變更管理程序來更新在復原環境的同一個的間隔為實際執行環境。</span><span class="sxs-lookup"><span data-stu-id="33645-321">We recommend that you extend the change management process to the recovery environment by updating the recovery environment at the same interval as the production environment.</span></span> <span data-ttu-id="33645-322">變更管理程序的一部分，建議您維護詳細的清查您的伺服器陣列設定、 應用程式和使用者。</span><span class="sxs-lookup"><span data-stu-id="33645-322">As part of the change management process, we recommend maintaining a detailed inventory of your farm configuration, applications, and users.</span></span> 
  
## <a name="phase-2-create-the-azure-virtual-network-and-vpn-connection"></a><span data-ttu-id="33645-323">階段 2： 建立 Azure 虛擬網路和 VPN 連線</span><span class="sxs-lookup"><span data-stu-id="33645-323">Phase 2: Create the Azure virtual network and VPN connection</span></span>

<span data-ttu-id="33645-324">[Microsoft Azure 虛擬網路的連線內部部署網路](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)說明如何規劃及部署 Azure 虛擬網路，以及如何建立的 VPN 連線。</span><span class="sxs-lookup"><span data-stu-id="33645-324">[Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md) shows you how to plan and deploy the virtual network in Azure and how to create the VPN connection.</span></span> <span data-ttu-id="33645-325">請依照下列完成下列程序主題中的指引：</span><span class="sxs-lookup"><span data-stu-id="33645-325">Follow the guidance in the topic to complete the following procedures:</span></span>
  
- <span data-ttu-id="33645-326">規劃虛擬網路的私人 IP 位址空間。</span><span class="sxs-lookup"><span data-stu-id="33645-326">Plan the private IP address space of the Virtual Network.</span></span>
    
- <span data-ttu-id="33645-327">規劃虛擬網路的路由基礎結構的變更。</span><span class="sxs-lookup"><span data-stu-id="33645-327">Plan the routing infrastructure changes for the Virtual Network.</span></span>
    
- <span data-ttu-id="33645-328">規劃將與從內部部署 VPN 裝置的流量的防火牆規則。</span><span class="sxs-lookup"><span data-stu-id="33645-328">Plan firewall rules for traffic to and from the on-premises VPN device.</span></span>
    
- <span data-ttu-id="33645-329">在 Azure 中建立跨單位部署虛擬網路。</span><span class="sxs-lookup"><span data-stu-id="33645-329">Create the cross-premises virtual network in Azure.</span></span>
    
- <span data-ttu-id="33645-330">設定內部網路和虛擬網路間的路由。</span><span class="sxs-lookup"><span data-stu-id="33645-330">Configure routing between your on-premises network and the Virtual Network.</span></span>
    
## <a name="phase-3-deploy-active-directory-and-domain-name-services-to-the-azure-virtual-network"></a><span data-ttu-id="33645-331">階段 3： 將 Active Directory 和網域名稱服務部署到 Azure 虛擬網路</span><span class="sxs-lookup"><span data-stu-id="33645-331">Phase 3: Deploy Active Directory and Domain Name Services to the Azure virtual network</span></span>

<span data-ttu-id="33645-332">此階段包含 Windows Server Active Directory 和 DNS 部署虛擬網路中的混合式案例，並在[Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)中所述，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="33645-332">This phase includes deploying both Windows Server Active Directory and DNS to the Virtual Network in a hybrid scenario as described in [Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) and as illustrated in the following figure.</span></span>
  
<span data-ttu-id="33645-333">**圖： 混合式 Active Directory 網域組態**</span><span class="sxs-lookup"><span data-stu-id="33645-333">**Figure: Hybrid Active Directory domain configuration**</span></span>

![STwo 虛擬機器部署到 Azure 虛擬網路和 SharePoint 伺服器陣列子網路是複本網域控制站和 DNS 伺服器](media/AZarch-HyADdomainConfig.png)
  
<span data-ttu-id="33645-335">在圖中，兩部虛擬機器部署至相同的子網路。</span><span class="sxs-lookup"><span data-stu-id="33645-335">In the illustration, two virtual machines are deployed to the same subnet.</span></span> <span data-ttu-id="33645-336">這些虛擬機器是每部主控的兩個角色： Active Directory 和 DNS。</span><span class="sxs-lookup"><span data-stu-id="33645-336">These virtual machines are each hosting two roles: Active Directory and DNS.</span></span>
  
<span data-ttu-id="33645-337">之前部署在 Azure 中的 Active Directory，請參閱[部署 Windows Server Active Directory Azure 虛擬機器上的指導方針](https://go.microsoft.com/fwlink/p/?linkid=392681)。</span><span class="sxs-lookup"><span data-stu-id="33645-337">Before deploying Active Directory in Azure, read [Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines](https://go.microsoft.com/fwlink/p/?linkid=392681).</span></span> <span data-ttu-id="33645-338">這些指導方針可協助您判斷您是否需要不同的架構或不同的組態設定您的解決方案。</span><span class="sxs-lookup"><span data-stu-id="33645-338">These guidelines help you determine whether you need a different architecture or different configuration settings for your solution.</span></span>
  
<span data-ttu-id="33645-339">在 Azure 中的網域控制站設定的詳細指引，請參閱[安裝複本 Active Directory 網域控制站的 Azure 虛擬網路](https://go.microsoft.com/fwlink/p/?LinkId=392687)。</span><span class="sxs-lookup"><span data-stu-id="33645-339">For detailed guidance on setting up a domain controller in Azure, see [Install a Replica Active Directory Domain Controller in Azure Virtual Networks](https://go.microsoft.com/fwlink/p/?LinkId=392687).</span></span>
  
<span data-ttu-id="33645-340">在這個階段中之前, 您未部署虛擬機器至虛擬網路。</span><span class="sxs-lookup"><span data-stu-id="33645-340">Before this phase, you didn't deploy virtual machines to the Virtual Network.</span></span> <span data-ttu-id="33645-341">虛擬機器來架設 Active Directory 和 DNS 不可能最大的虛擬機器，您需要的解決方案。</span><span class="sxs-lookup"><span data-stu-id="33645-341">The virtual machines for hosting Active Directory and DNS are likely not the largest virtual machines you need for the solution.</span></span> <span data-ttu-id="33645-342">部署這些虛擬機器之前，先建立想要使用您的虛擬網路中的最大虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="33645-342">Before you deploy these virtual machines, first create the largest virtual machine that you plan to use in your Virtual Network.</span></span> <span data-ttu-id="33645-343">這有助於確保您的解決方案落在可讓您需要的最大的 Azure 中的標記。</span><span class="sxs-lookup"><span data-stu-id="33645-343">This helps ensure that your solution lands on a tag in Azure that allows the largest size you need.</span></span> <span data-ttu-id="33645-344">您不需要這一次設定此虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="33645-344">You do not need to configure this virtual machine at this time.</span></span> <span data-ttu-id="33645-345">只需建立，並將它放在一旁設定。</span><span class="sxs-lookup"><span data-stu-id="33645-345">Simply create it, and set it aside.</span></span> <span data-ttu-id="33645-346">如果不這麼做，您可能會遇到當您嘗試更新版本中，建立較大的虛擬機器時的限制這是此問題： 在撰寫本文時的時間。</span><span class="sxs-lookup"><span data-stu-id="33645-346">If you do not do this, you might run into a limitation when you try to create larger virtual machines later, which was an issue at the time this article was written.</span></span> 
  
## <a name="phase-4-deploy-the-sharepoint-recovery-farm-in-azure"></a><span data-ttu-id="33645-347">階段 4： 部署在 Azure 中的 SharePoint 復原伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="33645-347">Phase 4: Deploy the SharePoint recovery farm in Azure</span></span>

<span data-ttu-id="33645-348">部署您根據設計計劃的虛擬網路中的 SharePoint 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="33645-348">Deploy the SharePoint farm in your Virtual Network according to your design plans.</span></span> <span data-ttu-id="33645-349">它可能會有幫助您部署在 Azure 中 SharePoint 角色之前，先檢閱[Planning for SharePoint 2013 在 Azure 基礎結構服務上](https://go.microsoft.com/fwlink/p/?LinkId=400984)。</span><span class="sxs-lookup"><span data-stu-id="33645-349">It might be helpful to review [Planning for SharePoint 2013 on Azure Infrastructure Services](https://go.microsoft.com/fwlink/p/?LinkId=400984) before you deploy SharePoint roles in Azure.</span></span>
  
<span data-ttu-id="33645-350">請考慮下列我們學會建置我們概念證明環境的作法：</span><span class="sxs-lookup"><span data-stu-id="33645-350">Consider the following practices that we learned by building our proof of concept environment:</span></span>
  
- <span data-ttu-id="33645-351">使用 Azure 入口網站或 PowerShell 建立虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="33645-351">Create virtual machines by using the Azure portal or PowerShell.</span></span>
    
- <span data-ttu-id="33645-352">Azure 和 HYPER-V 不支援動態記憶體。</span><span class="sxs-lookup"><span data-stu-id="33645-352">Azure and Hyper-V do not support dynamic memory.</span></span> <span data-ttu-id="33645-353">請確定這作為因素納入您的效能與容量計劃。</span><span class="sxs-lookup"><span data-stu-id="33645-353">Be sure this is factored into your performance and capacity plans.</span></span>
    
- <span data-ttu-id="33645-354">重新啟動虛擬機器，透過 Azure 介面，而不是由本身的虛擬機器登入。</span><span class="sxs-lookup"><span data-stu-id="33645-354">Restart virtual machines through the Azure interface, not from the virtual machine logon itself.</span></span> <span data-ttu-id="33645-355">使用 Azure 介面更妥善地運作，則較容易預測。</span><span class="sxs-lookup"><span data-stu-id="33645-355">Using the Azure interface works better and is more predictable.</span></span>
    
- <span data-ttu-id="33645-356">如果您想要關閉虛擬機器儲存成本，使用 Azure 的介面。</span><span class="sxs-lookup"><span data-stu-id="33645-356">If you want to shut down a virtual machine to save costs, use the Azure interface.</span></span> <span data-ttu-id="33645-357">如果您從關閉虛擬機器登入，費用繼續累算。</span><span class="sxs-lookup"><span data-stu-id="33645-357">If you shut down from the virtual machine logon, charges continue to accrue.</span></span>
    
- <span data-ttu-id="33645-358">使用虛擬機器的命名慣例。</span><span class="sxs-lookup"><span data-stu-id="33645-358">Use a naming convention for the virtual machines.</span></span>
    
- <span data-ttu-id="33645-359">請的注意到哪一個資料中心位置部署虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="33645-359">Pay attention to which datacenter location the virtual machines are being deployed.</span></span>
    
- <span data-ttu-id="33645-360">SharePoint 角色不支援在 Azure 中的自動調整功能。</span><span class="sxs-lookup"><span data-stu-id="33645-360">The automatic scaling feature in Azure is not supported for SharePoint roles.</span></span>
    
- <span data-ttu-id="33645-361">不會還原，例如網站集合之伺服器陣列中設定的項目。</span><span class="sxs-lookup"><span data-stu-id="33645-361">Do not configure items in the farm that will be restored, such as site collections.</span></span> 
    
## <a name="phase-5-set-up-dfsr-between-the-farms"></a><span data-ttu-id="33645-362">階段 5： 設定伺服器陣列之間 DFSR</span><span class="sxs-lookup"><span data-stu-id="33645-362">Phase 5: Set up DFSR between the farms</span></span>

<span data-ttu-id="33645-363">若要設定檔複寫使用 DFSR，使用 [DNS 管理] 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="33645-363">To set up file replication by using DFSR, use the DNS Management snap-in.</span></span> <span data-ttu-id="33645-364">不過，DFSR 安裝程式之前登入您的內部部署檔案伺服器和 Azure 檔案伺服器並啟用 Windows 中的服務。</span><span class="sxs-lookup"><span data-stu-id="33645-364">However, before the DFSR setup, log on to your on-premises file server and Azure file server and enable the service in Windows.</span></span>
  
<span data-ttu-id="33645-365">從 [伺服器管理員儀表板中，完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="33645-365">From the Server Manager Dashboard, complete the following steps:</span></span>
  
- <span data-ttu-id="33645-366">設定本機伺服器。</span><span class="sxs-lookup"><span data-stu-id="33645-366">Configure the local server.</span></span>
    
- <span data-ttu-id="33645-367">啟動 [**新增角色及功能精靈**]。</span><span class="sxs-lookup"><span data-stu-id="33645-367">Start the **Add Roles and Features Wizard**.</span></span>
    
- <span data-ttu-id="33645-368">開啟 [**檔案和存放服務**] 節點。</span><span class="sxs-lookup"><span data-stu-id="33645-368">Open the **File and Storage Services** node.</span></span>
    
- <span data-ttu-id="33645-369">選取 [ **DFS 命名空間**和**DFS 複寫**。</span><span class="sxs-lookup"><span data-stu-id="33645-369">Select **DFS Namespaces** and **DFS replication**.</span></span>
    
- <span data-ttu-id="33645-370">按 [**下一步**完成精靈的步驟。</span><span class="sxs-lookup"><span data-stu-id="33645-370">Click **Next** to finish the wizard steps.</span></span>
    
<span data-ttu-id="33645-371">下表提供 DFSR 參考文章和部落格文章的連結。</span><span class="sxs-lookup"><span data-stu-id="33645-371">The following table provides links to DFSR reference articles and blog posts.</span></span>
  
<span data-ttu-id="33645-372">**表格： DFSR 的參考文章**</span><span class="sxs-lookup"><span data-stu-id="33645-372">**Table: Reference articles for DFSR**</span></span>

|<span data-ttu-id="33645-373">**標題**</span><span class="sxs-lookup"><span data-stu-id="33645-373">**Title**</span></span>|<span data-ttu-id="33645-374">**描述**</span><span class="sxs-lookup"><span data-stu-id="33645-374">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="33645-375">複寫</span><span class="sxs-lookup"><span data-stu-id="33645-375">Replication</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392732) <br/> |<span data-ttu-id="33645-376">DFS 管理 TechNet 主題的連結進行複寫</span><span class="sxs-lookup"><span data-stu-id="33645-376">DFS Management TechNet topic with links for replication</span></span>  <br/> |
|[<span data-ttu-id="33645-377">DFS 複寫： 生存指南</span><span class="sxs-lookup"><span data-stu-id="33645-377">DFS Replication: Survival Guide</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392737) <br/> |<span data-ttu-id="33645-378">Wiki DFS 資訊的連結</span><span class="sxs-lookup"><span data-stu-id="33645-378">Wiki with links to DFS information</span></span>  <br/> |
|[<span data-ttu-id="33645-379">DFS 複寫： 常見問題集</span><span class="sxs-lookup"><span data-stu-id="33645-379">DFS Replication: Frequently Asked Questions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392738) <br/> |<span data-ttu-id="33645-380">DFS 複寫 TechNet 主題</span><span class="sxs-lookup"><span data-stu-id="33645-380">DFS Replication TechNet topic</span></span>  <br/> |
|[<span data-ttu-id="33645-381">Jose Barreto 部落格</span><span class="sxs-lookup"><span data-stu-id="33645-381">Jose Barreto's Blog</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392739) <br/> |<span data-ttu-id="33645-382">寫入由主體 Program Manager microsoft 在檔案伺服器小組部落格</span><span class="sxs-lookup"><span data-stu-id="33645-382">Blog written by a Principal Program Manager on the File Server team at Microsoft</span></span>  <br/> |
|[<span data-ttu-id="33645-383">在 Microsoft-檔案封包部落格儲存小組</span><span class="sxs-lookup"><span data-stu-id="33645-383">The Storage Team at Microsoft - File Cabinet Blog</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392740) <br/> |<span data-ttu-id="33645-384">檔案服務和 Windows Server 中的儲存空間功能相關的部落格</span><span class="sxs-lookup"><span data-stu-id="33645-384">Blog about file services and storage features in Windows Server</span></span>  <br/> |
   
## <a name="phase-6-set-up-log-shipping-to-the-recovery-farm"></a><span data-ttu-id="33645-385">階段 6： 設定記錄傳送至復原伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="33645-385">Phase 6: Set up log shipping to the recovery farm</span></span>

<span data-ttu-id="33645-386">記錄傳送是設定在此環境中的嚴重損壞修復的重要元件。</span><span class="sxs-lookup"><span data-stu-id="33645-386">Log shipping is the critical component for setting up disaster recovery in this environment.</span></span> <span data-ttu-id="33645-387">您可以使用記錄傳送至自動從主要資料庫伺服器執行個體的資料庫交易記錄檔傳送至次要資料庫伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="33645-387">You can use log shipping to automatically send transaction log files for databases from a primary database server instance to a secondary database server instance.</span></span> <span data-ttu-id="33645-388">若要設定記錄傳送，請參閱 <<c0>在 SharePoint 2013 中傳送設定記錄檔。</span><span class="sxs-lookup"><span data-stu-id="33645-388">To set up log shipping, see [Configure log shipping in SharePoint 2013](https://docs.microsoft.com/sharepoint/administration/configure-log-shipping).</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="33645-389">記錄傳送支援 SharePoint Server 中受限於特定資料庫。</span><span class="sxs-lookup"><span data-stu-id="33645-389">Log shipping support in SharePoint Server is limited to certain databases.</span></span> <span data-ttu-id="33645-390">如需詳細資訊，請參閱[支援的高可用性和災害復原 SharePoint 資料庫 (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=393121)。</span><span class="sxs-lookup"><span data-stu-id="33645-390">For more information, see [Supported high availability and disaster recovery options for SharePoint databases (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=393121).</span></span> 
  
## <a name="phase-7-validate-failover-and-recovery"></a><span data-ttu-id="33645-391">階段 7： 驗證容錯移轉和復原</span><span class="sxs-lookup"><span data-stu-id="33645-391">Phase 7: Validate failover and recovery</span></span>

<span data-ttu-id="33645-392">此最終階段的目標是確認災害復原解決方案規劃般運作。</span><span class="sxs-lookup"><span data-stu-id="33645-392">The goal of this final phase is to verify that the disaster recovery solution works as planned.</span></span> <span data-ttu-id="33645-393">若要這麼做，請建立容錯移轉事件，關閉 [實際執行伺服器陣列，並啟動復原伺服器陣列的替代文字。</span><span class="sxs-lookup"><span data-stu-id="33645-393">To do this, create a failover event that shuts down the production farm and starts up the recovery farm as a replacement.</span></span> <span data-ttu-id="33645-394">您可以開始在容錯移轉案例，以手動方式或使用指令碼。</span><span class="sxs-lookup"><span data-stu-id="33645-394">You can start a failover scenario manually or by using scripts.</span></span>
  
<span data-ttu-id="33645-395">第一個步驟是以停止傳入的使用者要求的伺服器陣列服務或內容。</span><span class="sxs-lookup"><span data-stu-id="33645-395">The first step is to stop incoming user requests for farm services or content.</span></span> <span data-ttu-id="33645-396">藉由停用 DNS 項目或關閉前端網頁伺服器，您可以這麼做。</span><span class="sxs-lookup"><span data-stu-id="33645-396">You can do this by disabling DNS entries or by shutting down the front-end web servers.</span></span> <span data-ttu-id="33645-397">「 向下 」 伺服器陣列之後，您可以在容錯移轉到復原伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="33645-397">After the farm is "down," you can fail over to the recovery farm.</span></span>
  
### <a name="stop-log-shipping"></a><span data-ttu-id="33645-398">停止記錄傳送</span><span class="sxs-lookup"><span data-stu-id="33645-398">Stop log shipping</span></span>

<span data-ttu-id="33645-399">您必須停止伺服器陣列復原之前的記錄傳送。</span><span class="sxs-lookup"><span data-stu-id="33645-399">You must stop log shipping before farm recovery.</span></span> <span data-ttu-id="33645-400">停止記錄前，傳送在 Azure 中的次要伺服器，然後停止在主要伺服器的內部。</span><span class="sxs-lookup"><span data-stu-id="33645-400">Stop log shipping on the secondary server in Azure first, and then stop it on the primary server on-premises.</span></span> <span data-ttu-id="33645-401">使用下列指令碼上第一個次要伺服器，然後在主要伺服器上停止記錄傳送。</span><span class="sxs-lookup"><span data-stu-id="33645-401">Use the following script to stop log shipping on the secondary server first and then on the primary server.</span></span> <span data-ttu-id="33645-402">指令碼中的資料庫名稱可能不同，根據您的環境。</span><span class="sxs-lookup"><span data-stu-id="33645-402">The database names in the script might be different, depending on your environment.</span></span>
  
```
-- This script removes log shipping from the server.
-- Commands must be executed on the secondary server first and then on the primary server.

SET NOCOUNT ON
DECLARE  @PriDB nvarchar(max)
,@SecDB nvarchar(250)
,@PriSrv nvarchar(250)
,@SecSrv nvarchar(250)

Set @PriDB= ''
SET @PriDB = UPPER(@PriDB)
SET @PriDB = REPLACE(@PriDB, ' ', '')
SET @PriDB = '''' + REPLACE(@PriDB, ',', ''', ''') + ''''

Set @SecDB = @PriDB

Exec ( 'Select  ''exec master..sp_delete_log_shipping_secondary_database '' + '''''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_primary_secondary '' + '''''''' + prm.Primary_Database + '''''', '''''' + sec.Secondary_Server + '''''', '''''' + sec.Secondary_database + ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_primary_database '' + '''''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_secondary_primary '' + '''''''' + prm.primary_server + '''''', '''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

```

### <a name="restore-the-backups"></a><span data-ttu-id="33645-403">還原的備份</span><span class="sxs-lookup"><span data-stu-id="33645-403">Restore the backups</span></span>

<span data-ttu-id="33645-404">備份必須還原中所建立的順序。</span><span class="sxs-lookup"><span data-stu-id="33645-404">Backups must be restored in the order in which they were created.</span></span> <span data-ttu-id="33645-405">您可以還原特定的交易記錄備份之前，您必須先沒有回復未認可的交易還原下列先前的備份 (也就使用`WITH NORECOVERY`):</span><span class="sxs-lookup"><span data-stu-id="33645-405">Before you can restore a particular transaction log backup, you must first restore the following previous backups without rolling back uncommitted transactions (that is, by using  `WITH NORECOVERY`):</span></span>
  
- <span data-ttu-id="33645-406">完整資料庫備份和上次的差異備份對這些備份還原，如果有的話，在特定交易記錄備份之前進行。</span><span class="sxs-lookup"><span data-stu-id="33645-406">The full database backup and the last differential backup - Restore these backups, if any exist, taken before the particular transaction log backup.</span></span> <span data-ttu-id="33645-407">已建立的最新的完整或差異資料庫備份之前，資料庫所使用的完整復原模式或大量記錄復原模式。</span><span class="sxs-lookup"><span data-stu-id="33645-407">Before the most recent full or differential database backup was created, the database was using the full recovery model or bulk-logged recovery model.</span></span>
    
- <span data-ttu-id="33645-408">所有的交易記錄備份的還原採取之後的完整資料庫備份或差異備份 （如果您還原一個），並在特定交易記錄檔之前備份任何交易記錄檔備份。</span><span class="sxs-lookup"><span data-stu-id="33645-408">All transaction log backups - Restore any transaction log backups taken after the full database backup or the differential backup (if you restore one) and before the particular transaction log backup.</span></span> <span data-ttu-id="33645-409">記錄檔備份必須在其中建立它們沒有任何間距記錄鏈結中的順序套用。</span><span class="sxs-lookup"><span data-stu-id="33645-409">Log backups must be applied in the sequence in which they were created, without any gaps in the log chain.</span></span>
    
<span data-ttu-id="33645-410">若要使網站轉譯，請復原次要伺服器上的內容資料庫，移除所有資料庫連線之前修復。</span><span class="sxs-lookup"><span data-stu-id="33645-410">To recover the content database on the secondary server so that the sites render, remove all database connections before recovery.</span></span> <span data-ttu-id="33645-411">若要還原的資料庫，請執行下列 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="33645-411">To restore the database, run the following SQL statement.</span></span>
  
```
restore database WSS_Content with recovery

```

> [!IMPORTANT]
> <span data-ttu-id="33645-412">當您使用 T-SQL 明確時，指定 [ **WITH NORECOVERY** ] 或 [ **WITH RECOVERY**中每個還原陳述式，以消除模稜兩可 — 撰寫指令碼時，這是非常重要。</span><span class="sxs-lookup"><span data-stu-id="33645-412">When you use T-SQL explicitly, specify either **WITH NORECOVERY** or **WITH RECOVERY** in every RESTORE statement to eliminate ambiguity—this is very important when writing scripts.</span></span> <span data-ttu-id="33645-413">還原完整及差異備份之後，可以還原的交易記錄檔在 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="33645-413">After the full and differential backups are restored, the transaction logs can be restored in SQL Server Management Studio.</span></span> <span data-ttu-id="33645-414">此外，因為已經停止記錄傳送，內容資料庫是處於待命狀態，因此您必須將狀態變更為完整存取權。</span><span class="sxs-lookup"><span data-stu-id="33645-414">Also, because log shipping is already stopped, the content database is in a standby state, so you must change the state to full access.</span></span>
  
<span data-ttu-id="33645-415">在 SQL Server Management Studio 中，以滑鼠右鍵按一下 [ **WSS_Content** ] 資料庫，指向 [**工作** > **還原**，然後按一下 [**交易記錄檔**（如果您無法還原完整備份，這是不提供）。</span><span class="sxs-lookup"><span data-stu-id="33645-415">In SQL Server Management Studio, right-click the **WSS_Content** database, point to **Tasks** > **Restore**, and then click **Transaction Log** (if you have not restored the full backup, this is not available).</span></span> <span data-ttu-id="33645-416">如需詳細資訊，請參閱 <<c0>還原交易記錄檔備份 (SQL Server)>。</span><span class="sxs-lookup"><span data-stu-id="33645-416">For more information, see[Restore a Transaction Log Backup (SQL Server)](https://go.microsoft.com/fwlink/p/?LinkId=392778).</span></span>
  
### <a name="crawl-the-content-source"></a><span data-ttu-id="33645-417">編目內容來源</span><span class="sxs-lookup"><span data-stu-id="33645-417">Crawl the content source</span></span>

<span data-ttu-id="33645-418">您必須啟動完整編目每個內容來源，以還原搜尋服務。</span><span class="sxs-lookup"><span data-stu-id="33645-418">You must start a full crawl for each content source to restore the Search Service.</span></span> <span data-ttu-id="33645-419">請注意，您會失去從內部部署伺服器陣列，例如搜尋建議某些分析資訊。</span><span class="sxs-lookup"><span data-stu-id="33645-419">Note that you lose some analytics information from the on-premises farm, such as search recommendations.</span></span> <span data-ttu-id="33645-420">在您開始完整編目，使用 Windows PowerShell cmdlet **Restore-spenterprisesearchserviceapplication**並指定記錄傳送和複製的搜尋管理資料庫之前, **Search_Service__DB_<GUID>**。</span><span class="sxs-lookup"><span data-stu-id="33645-420">Before you start the full crawls, use the Windows PowerShell cmdlet **Restore-SPEnterpriseSearchServiceApplication** and specify the log-shipped and replicated Search Administration database, **Search_Service__DB_<GUID>**.</span></span> <span data-ttu-id="33645-421">此 cmdlet 可讓搜尋組態、 結構描述、 受管理的內容、 規則和來源，並建立一組預設的其他元件。</span><span class="sxs-lookup"><span data-stu-id="33645-421">This cmdlet gives the search configuration, schema, managed properties, rules, and sources and creates a default set of the other components.</span></span>
  
<span data-ttu-id="33645-422">若要啟動完整編目，請完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="33645-422">To start a full crawl, complete the following steps:</span></span>
  
1. <span data-ttu-id="33645-423">在 SharePoint 2013 管理中心，移至 [**應用程式管理** > **服務應用程式** > **管理服務應用程式**，然後按一下 [您想要編目的 Search Service 應用程式。</span><span class="sxs-lookup"><span data-stu-id="33645-423">In the SharePoint 2013 Central Administration, go to **Application Management** > **Service Applications** > **Manage service applications**, and then click the Search Service application that you want to crawl.</span></span>
    
2. <span data-ttu-id="33645-424">在 [**搜尋管理**] 頁面上，按一下 [**內容來源**]，指向您想，按一下箭號，，然後按一下 [**啟動完整編目**的內容來源。</span><span class="sxs-lookup"><span data-stu-id="33645-424">On the **Search Administration** page, click **Content Sources**, point to the content source that you want, click the arrow, and then click **Start Full Crawl**.</span></span>
    
### <a name="recover-farm-services"></a><span data-ttu-id="33645-425">復原伺服器陣列服務</span><span class="sxs-lookup"><span data-stu-id="33645-425">Recover farm services</span></span>

<span data-ttu-id="33645-426">下表顯示如何復原具有記錄傳送資料庫，資料庫但不建議還原記錄傳送，並沒有資料庫的服務與服務的服務。</span><span class="sxs-lookup"><span data-stu-id="33645-426">The following table shows how to recover services that have log-shipped databases, the services that have databases but are not recommended to restore with log shipping, and the services that do not have databases.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="33645-427">內部部署 SharePoint 資料庫還原至 Azure 環境將不會復原您沒有已安裝在 Azure 中手動任何 SharePoint 服務。</span><span class="sxs-lookup"><span data-stu-id="33645-427">Restoring an on-premises SharePoint database into the Azure environment will not recover any SharePoint services that you did not already install in Azure manually.</span></span> 
  
<span data-ttu-id="33645-428">**表格： 服務應用程式資料庫參考**</span><span class="sxs-lookup"><span data-stu-id="33645-428">**Table: Service application database reference**</span></span>

|<span data-ttu-id="33645-429">**記錄傳送資料庫還原這些服務**</span><span class="sxs-lookup"><span data-stu-id="33645-429">**Restore these services from log-shipped databases**</span></span>|<span data-ttu-id="33645-430">**這些服務有資料庫，但是我們建議您啟動這些服務，但不還原其資料庫**</span><span class="sxs-lookup"><span data-stu-id="33645-430">**These services have databases, but we recommend that you start these services without restoring their databases**</span></span>|<span data-ttu-id="33645-431">**這些服務未執行動作將資料儲存在資料庫;容錯移轉後啟動這些服務**</span><span class="sxs-lookup"><span data-stu-id="33645-431">**These services do not store data in databases; start these services after failover**</span></span>|
|:-----|:-----|:-----|
| <span data-ttu-id="33645-432">機器翻譯服務</span><span class="sxs-lookup"><span data-stu-id="33645-432">Machine Translation Service</span></span> <br/>  <span data-ttu-id="33645-433">Managed Metadata Service</span><span class="sxs-lookup"><span data-stu-id="33645-433">Managed Metadata Service</span></span> <br/>  <span data-ttu-id="33645-434">Secure Store Service</span><span class="sxs-lookup"><span data-stu-id="33645-434">Secure Store Service</span></span> <br/>  <span data-ttu-id="33645-435">使用者設定檔。</span><span class="sxs-lookup"><span data-stu-id="33645-435">User Profile.</span></span> <span data-ttu-id="33645-436">（僅限設定檔及社交標記資料庫可支援。</span><span class="sxs-lookup"><span data-stu-id="33645-436">(Only the Profile and Social Tagging databases are supported.</span></span> <span data-ttu-id="33645-437">同步處理資料庫不支援。）</span><span class="sxs-lookup"><span data-stu-id="33645-437">The Synchronization database is not supported.)</span></span> <br/>  <span data-ttu-id="33645-438">Microsoft SharePoint Foundation 訂閱設定服務</span><span class="sxs-lookup"><span data-stu-id="33645-438">Microsoft SharePoint Foundation Subscription Settings Service</span></span> <br/> | <span data-ttu-id="33645-439">Usage and Health Data Collection</span><span class="sxs-lookup"><span data-stu-id="33645-439">Usage and Health Data Collection</span></span> <br/>  <span data-ttu-id="33645-440">State service</span><span class="sxs-lookup"><span data-stu-id="33645-440">State service</span></span> <br/>  <span data-ttu-id="33645-441">Word automation</span><span class="sxs-lookup"><span data-stu-id="33645-441">Word automation</span></span> <br/> | <span data-ttu-id="33645-442">Excel Services</span><span class="sxs-lookup"><span data-stu-id="33645-442">Excel Services</span></span> <br/>  <span data-ttu-id="33645-443">PerformancePoint Services</span><span class="sxs-lookup"><span data-stu-id="33645-443">PerformancePoint Services</span></span> <br/>  <span data-ttu-id="33645-444">PowerPoint 轉換</span><span class="sxs-lookup"><span data-stu-id="33645-444">PowerPoint Conversion</span></span> <br/>  <span data-ttu-id="33645-445">Visio Graphics Service</span><span class="sxs-lookup"><span data-stu-id="33645-445">Visio Graphics Service</span></span> <br/>  <span data-ttu-id="33645-446">Work Management</span><span class="sxs-lookup"><span data-stu-id="33645-446">Work Management</span></span> <br/> |
   
<span data-ttu-id="33645-447">下列範例會示範如何從資料庫還原 Managed Metadata service。</span><span class="sxs-lookup"><span data-stu-id="33645-447">The following example shows how to restore the Managed Metadata service from a database.</span></span>
  
<span data-ttu-id="33645-448">這是使用現有的 Managed_Metadata_DB 資料庫。</span><span class="sxs-lookup"><span data-stu-id="33645-448">This uses the existing Managed_Metadata_DB database.</span></span> <span data-ttu-id="33645-449">此資料庫是記錄傳送，但沒有作用中服務應用程式次要伺服器陣列上，因此需要的服務應用程式已經準備就緒之後會保持連線。</span><span class="sxs-lookup"><span data-stu-id="33645-449">This database is log shipped, but there is no active service application on the secondary farm, so it needs to be connected after the service application is in place.</span></span>
  
<span data-ttu-id="33645-450">首先，使用`New-SPMetadataServiceApplication`，並指定`DatabaseName`切換的已還原的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="33645-450">First, use  `New-SPMetadataServiceApplication`, and specify the  `DatabaseName` switch with the name of the restored database.</span></span>
  
<span data-ttu-id="33645-451">接下來，設定次要伺服器上的新的 Managed Metadata Service 應用程式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="33645-451">Next, configure the new Managed Metadata Service Application on the secondary server, as follows:</span></span>
  
- <span data-ttu-id="33645-452">名稱： Managed Metadata Service</span><span class="sxs-lookup"><span data-stu-id="33645-452">Name: Managed Metadata Service</span></span>
    
- <span data-ttu-id="33645-453">資料庫伺服器： 從運送的交易記錄檔的資料庫名稱</span><span class="sxs-lookup"><span data-stu-id="33645-453">Database server: The database name from the shipped transaction log</span></span>
    
- <span data-ttu-id="33645-454">資料庫名稱： Managed_Metadata_DB</span><span class="sxs-lookup"><span data-stu-id="33645-454">Database name: Managed_Metadata_DB</span></span>
    
- <span data-ttu-id="33645-455">應用程式集區： SharePoint 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="33645-455">Application pool: SharePoint Service Applications</span></span> 
    
### <a name="manage-dns-records"></a><span data-ttu-id="33645-456">管理 DNS 記錄</span><span class="sxs-lookup"><span data-stu-id="33645-456">Manage DNS records</span></span>

<span data-ttu-id="33645-457">您必須手動建立 DNS 記錄以指向 SharePoint 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="33645-457">You must manually create DNS records to point to your SharePoint farm.</span></span>
  
<span data-ttu-id="33645-458">在大多數情況下您有多部前端網頁伺服器的位置，合理的利用 Windows Server 2012 或硬體負載平衡器來散發要求在伺服器陣列中的 web 前端伺服器之間的網路負載平衡功能。</span><span class="sxs-lookup"><span data-stu-id="33645-458">In most cases where you have multiple front-end web servers, it makes sense to take advantage of the Network Load Balancing feature in Windows Server 2012 or a hardware load balancer to distribute requests among the web-front-end servers in your farm.</span></span> <span data-ttu-id="33645-459">網路負載平衡還可協助降低風險散發要求送至其他伺服器，如果其中一部 web 前端伺服器失敗。</span><span class="sxs-lookup"><span data-stu-id="33645-459">Network load balancing can also help reduce risk by distributing requests to the other servers if one of your web-front-end servers fails.</span></span> 
  
<span data-ttu-id="33645-460">一般而言，當您設定網路負載平衡，您的叢集指派單一 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="33645-460">Typically, when you set up network load balancing, your cluster is assigned a single IP address.</span></span> <span data-ttu-id="33645-461">您然後建立 DNS 主機記錄的 DNS 提供者中為您指向叢集的網路。</span><span class="sxs-lookup"><span data-stu-id="33645-461">You then create a DNS host record in the DNS provider for your network that points to the cluster.</span></span> <span data-ttu-id="33645-462">（此專案中，我們將放的 DNS 伺服器在 Azure 中的恢復能力以防內部部署資料中心失敗。）比方說，您可以建立 DNS 記錄，在 「 DNS 管理員在 Active Directory，例如，名為`http://sharepoint.contoso.com`，，指向您的負載平衡叢集的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="33645-462">(For this project, we put a DNS server in Azure for resiliency in case of an on-premises datacenter failure.) For instance, you can create a DNS record, in DNS Manager in Active Directory, for example, called  `http://sharepoint.contoso.com`, that points to the IP address for your load-balanced cluster.</span></span>
  
<span data-ttu-id="33645-463">外部存取您的 SharePoint 伺服器陣列，您可以建立主機記錄在外部 DNS 伺服器與用戶端使用內部網路的相同 URL (例如， `http://sharepoint.contoso.com`)，指向您的防火牆的外部 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="33645-463">For external access to your SharePoint farm, you can create a host record on an external DNS server with the same URL that clients use on your intranet (for example, `http://sharepoint.contoso.com`) that points to an external IP address in your firewall.</span></span> <span data-ttu-id="33645-464">(的最佳作法是，使用這個範例中，是要設定分割 DNS，以便將內部 DNS 伺服器的授權`contoso.com`並將要求路由傳送直接對 SharePoint 伺服器陣列叢集中，而不是路由的 DNS 要求至外部 DNS 伺服器。)您然後可以將的外部 IP 位址對應至您的內部部署叢集的內部 IP 位址，讓用戶端找到他們要尋找的資源。</span><span class="sxs-lookup"><span data-stu-id="33645-464">(A best practice, using this example, is to set up split DNS so that the internal DNS server is authoritative for `contoso.com` and routes requests directly to the SharePoint farm cluster, rather than routing DNS requests to your external DNS server.) You can then map the external IP address to the internal IP address of your on-premises cluster so that clients find the resources they are looking for.</span></span>
  
<span data-ttu-id="33645-465">從這裡開始，您可能會遇到幾個不同的災害復原案例：</span><span class="sxs-lookup"><span data-stu-id="33645-465">From here, you might run into a couple of different disaster-recovery scenarios:</span></span>
  
 <span data-ttu-id="33645-466">**範例案例： 在內部部署 SharePoint 伺服器陣列是無法使用，因為在內部部署 SharePoint 伺服器陣列的硬體故障。**</span><span class="sxs-lookup"><span data-stu-id="33645-466">**Example scenario: The on-premises SharePoint farm is unavailable because of hardware failure in the on-premises SharePoint farm.**</span></span> <span data-ttu-id="33645-467">在此情況下，您已完成容錯移轉至 Azure 的 SharePoint 伺服器陣列的步驟之後，您可以設定網路上的負載平衡復原 SharePoint 伺服器陣列的 web 前端伺服器，您並未與內部部署伺服器陣列的方式相同。</span><span class="sxs-lookup"><span data-stu-id="33645-467">In this case, after you have completed the steps for failover to the Azure SharePoint farm, you can configure network load balancing on the recovery SharePoint farm's web-front-end servers, the same way you did with the on-premises farm.</span></span> <span data-ttu-id="33645-468">然後可以將主機記錄重新導向到復原伺服器陣列的叢集 IP 位址指向內部 DNS 提供者。</span><span class="sxs-lookup"><span data-stu-id="33645-468">You can then redirect the host record in your internal DNS provider to point to the recovery farm's cluster IP address.</span></span> <span data-ttu-id="33645-469">請注意，它可能需要一些時間之前快取的 DNS 記錄在用戶端上會重新整理，並指向 [復原伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="33645-469">Note that it can take some time before cached DNS records on clients are refreshed and point to the recovery farm.</span></span>
  
 <span data-ttu-id="33645-470">**範例案例： 在內部部署資料中心是完全遺失。**</span><span class="sxs-lookup"><span data-stu-id="33645-470">**Example scenario: The on-premises datacenter is lost completely.**</span></span> <span data-ttu-id="33645-471">此案例中可能會因自然災害，例如火災或濫記而發生。</span><span class="sxs-lookup"><span data-stu-id="33645-471">This scenario might occur due to a natural disaster, such as a fire or flood.</span></span> <span data-ttu-id="33645-472">在此情況下，適用於企業，您可能必須裝載於另一個區域，以及有它自己的目錄服務和 DNS 您 Azure 子網路的次要資料中心。</span><span class="sxs-lookup"><span data-stu-id="33645-472">In this case, for an enterprise, you would likely have a secondary datacenter hosted in another region as well as your Azure subnet that has its own directory services and DNS.</span></span> <span data-ttu-id="33645-473">如同先前的災害案例中，您可以重新導向內部和外部 DNS 記錄以指向 Azure SharePoint 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="33645-473">As in the previous disaster scenario, you can redirect your internal and external DNS records to point to the Azure SharePoint farm.</span></span> <span data-ttu-id="33645-474">同樣地，記下的 DNS 記錄傳播可能需要一些時間。</span><span class="sxs-lookup"><span data-stu-id="33645-474">Again, take note that DNS-record propagation can take some time.</span></span>
  
<span data-ttu-id="33645-475">如果您使用主機命名型網站集合，[主機命名型網站集合架構與部署 (SharePoint 2013)](https://docs.microsoft.com/SharePoint/administration/host-named-site-collection-architecture-and-deployment)中建議的方式，您可能必須在 SharePoint 伺服器陣列，以唯一相同 web 應用程式所裝載的數個網站集合DNS 名稱 (例如，`http://sales.contoso.com`和`http://marketing.contoso.com`)。</span><span class="sxs-lookup"><span data-stu-id="33645-475">If you are using host-named site collections, as recommended in [Host-named site collection architecture and deployment (SharePoint 2013)](https://docs.microsoft.com/SharePoint/administration/host-named-site-collection-architecture-and-deployment), you might have several site collections hosted by the same web application in your SharePoint farm, with unique DNS names (for example, `http://sales.contoso.com` and `http://marketing.contoso.com`).</span></span> <span data-ttu-id="33645-476">在此情況下，您可以建立指向您的叢集 IP 位址的 DNS 記錄每個網站集合。</span><span class="sxs-lookup"><span data-stu-id="33645-476">In this case, you can create DNS records for each site collection that point to your cluster IP address.</span></span> <span data-ttu-id="33645-477">要求達到您的 SharePoint web 前端伺服器之後，他們會處理路由到適當的網站集合的每個要求。</span><span class="sxs-lookup"><span data-stu-id="33645-477">After a request reaches your SharePoint web-front-end servers, they handle routing each request to the appropriate site collection.</span></span>
  
## <a name="microsoft-proof-of-concept-environment"></a><span data-ttu-id="33645-478">Microsoft 概念證明的環境</span><span class="sxs-lookup"><span data-stu-id="33645-478">Microsoft proof-of-concept environment</span></span>

<span data-ttu-id="33645-479">我們所設計，並測試此解決方案的概念證明的環境。</span><span class="sxs-lookup"><span data-stu-id="33645-479">We designed and tested a proof-of-concept environment for this solution.</span></span> <span data-ttu-id="33645-480">我們的測試環境的設計目標是要部署和復原我們可能會發現在客戶的環境中的 SharePoint 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="33645-480">The design goal for our test environment was to deploy and recover a SharePoint farm that we might find in a customer environment.</span></span> <span data-ttu-id="33645-481">我們有幾項假設，但是我們知道伺服器陣列所需的所有沒有任何自訂的方塊擴充功能提供。</span><span class="sxs-lookup"><span data-stu-id="33645-481">We made several assumptions, but we knew that the farm needed to provide all of the out-of-the-box functionality without any customizations.</span></span> <span data-ttu-id="33645-482">拓樸的高可用性設計，藉由從欄位及產品群組中的最佳作法指導。</span><span class="sxs-lookup"><span data-stu-id="33645-482">The topology was designed for high availability by using best practice guidance from the field and product group.</span></span>
  
<span data-ttu-id="33645-483">下表說明 HYPER-V 虛擬機器，我們已建立並設定適用於內部部署測試環境。</span><span class="sxs-lookup"><span data-stu-id="33645-483">The following table describes the Hyper-V virtual machines that we created and configured for the on-premises test environment.</span></span>
  
<span data-ttu-id="33645-484">**表格： 虛擬機器內部部署測試**</span><span class="sxs-lookup"><span data-stu-id="33645-484">**Table: Virtual machines for on-premises test**</span></span>

|<span data-ttu-id="33645-485">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="33645-485">**Server name**</span></span>|<span data-ttu-id="33645-486">**Role**</span><span class="sxs-lookup"><span data-stu-id="33645-486">**Role**</span></span>|<span data-ttu-id="33645-487">**設定**</span><span class="sxs-lookup"><span data-stu-id="33645-487">**Configuration**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="33645-488">DC1</span><span class="sxs-lookup"><span data-stu-id="33645-488">DC1</span></span>  <br/> |<span data-ttu-id="33645-489">與 Active Directory 網域控制站。</span><span class="sxs-lookup"><span data-stu-id="33645-489">Domain controller with Active Directory.</span></span>  <br/> |<span data-ttu-id="33645-490">2 個處理器</span><span class="sxs-lookup"><span data-stu-id="33645-490">Two processors</span></span>  <br/> <span data-ttu-id="33645-491">從 512 MB 到 4 GB 的 RAM</span><span class="sxs-lookup"><span data-stu-id="33645-491">From 512 MB through 4 GB of RAM</span></span>  <br/> <span data-ttu-id="33645-492">1 x 127 GB 硬碟</span><span class="sxs-lookup"><span data-stu-id="33645-492">1 x 127-GB hard disk</span></span>  <br/> |
|<span data-ttu-id="33645-493">RRAS</span><span class="sxs-lookup"><span data-stu-id="33645-493">RRAS</span></span>  <br/> |<span data-ttu-id="33645-494">設定路由及遠端存取服務 (RRAS) 角色的伺服器。</span><span class="sxs-lookup"><span data-stu-id="33645-494">Server configured with the Routing and Remote Access Service (RRAS) role.</span></span>  <br/> |<span data-ttu-id="33645-495">2 個處理器</span><span class="sxs-lookup"><span data-stu-id="33645-495">Two processors</span></span>  <br/> <span data-ttu-id="33645-496">2-8 GB 的 RAM</span><span class="sxs-lookup"><span data-stu-id="33645-496">2-8 GB of RAM</span></span>  <br/> <span data-ttu-id="33645-497">1 x 127 GB 硬碟</span><span class="sxs-lookup"><span data-stu-id="33645-497">1 x 127-GB hard disk</span></span>  <br/> |
|<span data-ttu-id="33645-498">FS1</span><span class="sxs-lookup"><span data-stu-id="33645-498">FS1</span></span>  <br/> |<span data-ttu-id="33645-499">要備份的共用位置與 DFSR 結束點的檔案伺服器。</span><span class="sxs-lookup"><span data-stu-id="33645-499">File server with shares for backups and an end point for DFSR.</span></span>  <br/> |<span data-ttu-id="33645-500">四個處理器</span><span class="sxs-lookup"><span data-stu-id="33645-500">Four processors</span></span>  <br/> <span data-ttu-id="33645-501">2-12 GB 的 RAM</span><span class="sxs-lookup"><span data-stu-id="33645-501">2-12 GB of RAM</span></span>  <br/> <span data-ttu-id="33645-502">1 x 127 GB 硬碟</span><span class="sxs-lookup"><span data-stu-id="33645-502">1 x 127-GB hard disk</span></span>  <br/> <span data-ttu-id="33645-503">1 x 1 TB 的硬碟 (SAN)</span><span class="sxs-lookup"><span data-stu-id="33645-503">1 x 1-TB hard disk (SAN)</span></span>  <br/> <span data-ttu-id="33645-504">1 x 750 GB 硬碟</span><span class="sxs-lookup"><span data-stu-id="33645-504">1 x 750-GB hard disk</span></span>  <br/> |
|<span data-ttu-id="33645-505">SP-WFE1，SP-WFE2</span><span class="sxs-lookup"><span data-stu-id="33645-505">SP-WFE1, SP-WFE2</span></span>  <br/> |<span data-ttu-id="33645-506">前端網頁伺服器。</span><span class="sxs-lookup"><span data-stu-id="33645-506">Front-end web servers.</span></span>  <br/> |<span data-ttu-id="33645-507">四個處理器</span><span class="sxs-lookup"><span data-stu-id="33645-507">Four processors</span></span>  <br/> <span data-ttu-id="33645-508">16 GB RAM</span><span class="sxs-lookup"><span data-stu-id="33645-508">16 GB of RAM</span></span>  <br/> |
|<span data-ttu-id="33645-509">SP-APP1，SP-APP2 SP APP3</span><span class="sxs-lookup"><span data-stu-id="33645-509">SP-APP1, SP-APP2, SP-APP3</span></span>  <br/> |<span data-ttu-id="33645-510">應用程式伺服器。</span><span class="sxs-lookup"><span data-stu-id="33645-510">Application servers.</span></span>  <br/> |<span data-ttu-id="33645-511">四個處理器</span><span class="sxs-lookup"><span data-stu-id="33645-511">Four processors</span></span>  <br/> <span data-ttu-id="33645-512">2-16 GB 的 RAM</span><span class="sxs-lookup"><span data-stu-id="33645-512">2-16 GB of RAM</span></span>  <br/> |
|<span data-ttu-id="33645-513">SP-SQL-HA1，SP-SQL-HA2</span><span class="sxs-lookup"><span data-stu-id="33645-513">SP-SQL-HA1, SP-SQL-HA2</span></span>  <br/> |<span data-ttu-id="33645-514">使用 SQL Server 2012 AlwaysOn 可用性群組，以提供高可用性設定的資料庫伺服器。</span><span class="sxs-lookup"><span data-stu-id="33645-514">Database servers, configured with SQL Server 2012 AlwaysOn availability groups to provide high availability.</span></span> <span data-ttu-id="33645-515">此設定會使用預存程序-sql-ha1 和 SP sql-ha2 作為主要和次要複本。</span><span class="sxs-lookup"><span data-stu-id="33645-515">This configuration uses SP-SQL-HA1 and SP-SQL-HA2 as the primary and secondary replicas.</span></span>  <br/> |<span data-ttu-id="33645-516">四個處理器</span><span class="sxs-lookup"><span data-stu-id="33645-516">Four processors</span></span>  <br/> <span data-ttu-id="33645-517">2-16 GB 的 RAM</span><span class="sxs-lookup"><span data-stu-id="33645-517">2-16 GB of RAM</span></span>  <br/> |
   
<span data-ttu-id="33645-518">下表說明 HYPER-V 虛擬機器，我們已建立並設定的前端網頁伺服器和內部部署測試環境的應用程式伺服器的磁碟機組態。</span><span class="sxs-lookup"><span data-stu-id="33645-518">The following table describes drive configurations for the Hyper-V virtual machines that we created and configured for the front-end web and application servers for the on-premises test environment.</span></span>
  
<span data-ttu-id="33645-519">**表格： 虛擬機器的磁碟機需求 Front End 網頁和應用程式伺服器與內部測試**</span><span class="sxs-lookup"><span data-stu-id="33645-519">**Table: Virtual machine drive requirements for the Front End Web and Application servers for the on-premises test**</span></span>

|<span data-ttu-id="33645-520">**磁碟機代號**</span><span class="sxs-lookup"><span data-stu-id="33645-520">**Drive letter**</span></span>|<span data-ttu-id="33645-521">**大小**</span><span class="sxs-lookup"><span data-stu-id="33645-521">**Size**</span></span>|<span data-ttu-id="33645-522">**目錄名稱**</span><span class="sxs-lookup"><span data-stu-id="33645-522">**Directory name**</span></span>|<span data-ttu-id="33645-523">**Path**</span><span class="sxs-lookup"><span data-stu-id="33645-523">**Path**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="33645-524">C</span><span class="sxs-lookup"><span data-stu-id="33645-524">C</span></span>  <br/> |<span data-ttu-id="33645-525">80</span><span class="sxs-lookup"><span data-stu-id="33645-525">80</span></span>  <br/> |<span data-ttu-id="33645-526">系統磁碟機</span><span class="sxs-lookup"><span data-stu-id="33645-526">System drive</span></span>  <br/> |<span data-ttu-id="33645-527"><DriveLetter>:\\程式檔案\\Microsoft SQL Server\\</span><span class="sxs-lookup"><span data-stu-id="33645-527"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\</span></span>  <br/> |
|<span data-ttu-id="33645-528">E</span><span class="sxs-lookup"><span data-stu-id="33645-528">E</span></span>  <br/> |<span data-ttu-id="33645-529">80</span><span class="sxs-lookup"><span data-stu-id="33645-529">80</span></span>  <br/> |<span data-ttu-id="33645-530">記錄檔磁碟 (40 GB)</span><span class="sxs-lookup"><span data-stu-id="33645-530">Log drive (40 GB)</span></span>  <br/> |<span data-ttu-id="33645-531"><DriveLetter>:\\程式檔案\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\資料</span><span class="sxs-lookup"><span data-stu-id="33645-531"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA</span></span>  <br/> |
|<span data-ttu-id="33645-532">F</span><span class="sxs-lookup"><span data-stu-id="33645-532">F</span></span>  <br/> |<span data-ttu-id="33645-533">80</span><span class="sxs-lookup"><span data-stu-id="33645-533">80</span></span>  <br/> |<span data-ttu-id="33645-534">頁面 (36 GB)</span><span class="sxs-lookup"><span data-stu-id="33645-534">Page (36 GB)</span></span>  <br/> |<span data-ttu-id="33645-535"><DriveLetter>:\\程式檔案\\Microsoft SQL Server\\MSSQL\\資料</span><span class="sxs-lookup"><span data-stu-id="33645-535"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL\\DATA</span></span>  <br/> |
   
<span data-ttu-id="33645-536">下表說明 HYPER-V 虛擬機器建立並設定做為內部部署資料庫伺服器的磁碟機組態。</span><span class="sxs-lookup"><span data-stu-id="33645-536">The following table describes drive configurations for the Hyper-V virtual machines created and configured to serve as the on-premises database servers.</span></span> <span data-ttu-id="33645-537">在 [**資料庫引擎組態**] 頁面上，存取**資料目錄**] 索引標籤來設定，並確認，如下表所示的設定。</span><span class="sxs-lookup"><span data-stu-id="33645-537">On the **Database Engine Configuration** page, access the **Data Directories** tab to set and confirm the settings shown in the following table.</span></span>
  
<span data-ttu-id="33645-538">**表格： 內部部署的資料庫伺服器的虛擬機器的磁碟機需求測試**</span><span class="sxs-lookup"><span data-stu-id="33645-538">**Table: Virtual machine drive requirements for the database server for the on-premises test**</span></span>

|<span data-ttu-id="33645-539">**磁碟機代號**</span><span class="sxs-lookup"><span data-stu-id="33645-539">**Drive letter**</span></span>|<span data-ttu-id="33645-540">**大小**</span><span class="sxs-lookup"><span data-stu-id="33645-540">**Size**</span></span>|<span data-ttu-id="33645-541">**目錄名稱**</span><span class="sxs-lookup"><span data-stu-id="33645-541">**Directory name**</span></span>|<span data-ttu-id="33645-542">**Path**</span><span class="sxs-lookup"><span data-stu-id="33645-542">**Path**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="33645-543">C</span><span class="sxs-lookup"><span data-stu-id="33645-543">C</span></span>  <br/> |<span data-ttu-id="33645-544">80</span><span class="sxs-lookup"><span data-stu-id="33645-544">80</span></span>  <br/> |<span data-ttu-id="33645-545">資料根目錄</span><span class="sxs-lookup"><span data-stu-id="33645-545">Data root directory</span></span>  <br/> |<span data-ttu-id="33645-546"><DriveLetter>:\\程式檔案\\Microsoft SQL Server\\</span><span class="sxs-lookup"><span data-stu-id="33645-546"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\</span></span>  <br/> |
|<span data-ttu-id="33645-547">E</span><span class="sxs-lookup"><span data-stu-id="33645-547">E</span></span>  <br/> |<span data-ttu-id="33645-548">500</span><span class="sxs-lookup"><span data-stu-id="33645-548">500</span></span>  <br/> |<span data-ttu-id="33645-549">使用者資料庫目錄</span><span class="sxs-lookup"><span data-stu-id="33645-549">User database directory</span></span>  <br/> |<span data-ttu-id="33645-550"><DriveLetter>:\\程式檔案\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\資料</span><span class="sxs-lookup"><span data-stu-id="33645-550"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA</span></span>  <br/> |
|<span data-ttu-id="33645-551">F</span><span class="sxs-lookup"><span data-stu-id="33645-551">F</span></span>  <br/> |<span data-ttu-id="33645-552">500</span><span class="sxs-lookup"><span data-stu-id="33645-552">500</span></span>  <br/> |<span data-ttu-id="33645-553">使用者資料庫記錄檔目錄</span><span class="sxs-lookup"><span data-stu-id="33645-553">User database log directory</span></span>  <br/> |<span data-ttu-id="33645-554"><DriveLetter>:\\程式檔案\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\資料</span><span class="sxs-lookup"><span data-stu-id="33645-554"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA</span></span>  <br/> |
|<span data-ttu-id="33645-555">G</span><span class="sxs-lookup"><span data-stu-id="33645-555">G</span></span>  <br/> |<span data-ttu-id="33645-556">500</span><span class="sxs-lookup"><span data-stu-id="33645-556">500</span></span>  <br/> |<span data-ttu-id="33645-557">Temp DB 目錄</span><span class="sxs-lookup"><span data-stu-id="33645-557">Temp DB directory</span></span>  <br/> |<span data-ttu-id="33645-558"><DriveLetter>:\\程式檔案\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\資料</span><span class="sxs-lookup"><span data-stu-id="33645-558"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA</span></span>  <br/> |
|<span data-ttu-id="33645-559">H</span><span class="sxs-lookup"><span data-stu-id="33645-559">H</span></span>  <br/> |<span data-ttu-id="33645-560">500</span><span class="sxs-lookup"><span data-stu-id="33645-560">500</span></span>  <br/> |<span data-ttu-id="33645-561">Temp DB 記錄檔目錄</span><span class="sxs-lookup"><span data-stu-id="33645-561">Temp DB log directory</span></span>  <br/> |<span data-ttu-id="33645-562"><DriveLetter>:\\程式檔案\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\資料</span><span class="sxs-lookup"><span data-stu-id="33645-562"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA</span></span>  <br/> |
   
### <a name="setting-up-the-test-environment"></a><span data-ttu-id="33645-563">設定測試環境</span><span class="sxs-lookup"><span data-stu-id="33645-563">Setting up the test environment</span></span>

<span data-ttu-id="33645-564">在不同的部署階段，測試小組通常正常運作的第一個的內部部署架構上，然後在對應的 Azure 環境。</span><span class="sxs-lookup"><span data-stu-id="33645-564">During the different deployment phases, the test team typically worked on the on-premises architecture first and then on the corresponding Azure environment.</span></span> <span data-ttu-id="33645-565">這會反映在一般的真實世界情況下，選擇其中內部實際執行伺服器陣列已在執行。</span><span class="sxs-lookup"><span data-stu-id="33645-565">This reflects the general real-world cases where in-house production farms are already running.</span></span> <span data-ttu-id="33645-566">什麼是更重要的是您應該了解目前的生產工作負載、 容量及一般的效能。</span><span class="sxs-lookup"><span data-stu-id="33645-566">What is even more important is that you should know the current production workload, capacity, and typical performance.</span></span> <span data-ttu-id="33645-567">除了建置災害復原模式可以符合業務需求，您應該大小復原伺服器陣列的伺服器以傳遞服務的最低層級。</span><span class="sxs-lookup"><span data-stu-id="33645-567">In addition to building a disaster recovery model that can meet business requirements, you should size the recovery farm servers to deliver a minimum level of service.</span></span> <span data-ttu-id="33645-568">在冷或暖待命環境中，復原伺服器陣列是一般會小於實際執行伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="33645-568">In a cold or warm standby environment, a recovery farm is typically smaller than a production farm.</span></span> <span data-ttu-id="33645-569">之後復原伺服器陣列的穩定性及在生產中，在伺服器陣列可以擴充出，並以符合工作負載的需求。</span><span class="sxs-lookup"><span data-stu-id="33645-569">After the recovery farm is stable and in production, the farm can be scaled up and out to meet workload requirements.</span></span>
  
<span data-ttu-id="33645-570">我們部署了我們的測試環境中下列三個階段：</span><span class="sxs-lookup"><span data-stu-id="33645-570">We deployed our test environment in the following three phases:</span></span>
  
- <span data-ttu-id="33645-571">設定混合式基礎結構</span><span class="sxs-lookup"><span data-stu-id="33645-571">Set up the hybrid infrastructure</span></span>
    
- <span data-ttu-id="33645-572">佈建伺服器</span><span class="sxs-lookup"><span data-stu-id="33645-572">Provision the servers</span></span>
    
- <span data-ttu-id="33645-573">部署為 SharePoint 伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="33645-573">Deploy the SharePoint farms</span></span>
    
#### <a name="set-up-the-hybrid-infrastructure"></a><span data-ttu-id="33645-574">設定混合式基礎結構</span><span class="sxs-lookup"><span data-stu-id="33645-574">Set up the hybrid infrastructure</span></span>

<span data-ttu-id="33645-575">此階段牽涉到內部部署伺服器陣列和在 Azure 中的復原伺服器陣列的網域環境的設定。</span><span class="sxs-lookup"><span data-stu-id="33645-575">This phase involved setting up a domain environment for the on-premises farm and for the recovery farm in Azure.</span></span> <span data-ttu-id="33645-576">除了設定 Active Directory 相關聯的一般工作，測試小組會實作路由解決方案和兩個環境之間的 VPN 連線。</span><span class="sxs-lookup"><span data-stu-id="33645-576">In addition to the normal tasks associated with configuring Active Directory, the test team implemented a routing solution and a VPN connection between the two environments.</span></span>
  
#### <a name="provision-the-servers"></a><span data-ttu-id="33645-577">佈建伺服器</span><span class="sxs-lookup"><span data-stu-id="33645-577">Provision the servers</span></span>

<span data-ttu-id="33645-578">除了伺服器陣列的伺服器，它是所需的網域控制站佈建伺服器，且設定來處理 RRAS 為站台對站 VPN 伺服器。</span><span class="sxs-lookup"><span data-stu-id="33645-578">In addition to the farm servers, it was necessary to provision servers for the domain controllers and configure a server to handle RRAS as well as the site-to-site VPN.</span></span> <span data-ttu-id="33645-579">兩個檔案伺服器已佈建 DFSR 服務，以及數個用戶端電腦已佈建測試人員。</span><span class="sxs-lookup"><span data-stu-id="33645-579">Two file servers were provisioned for the DFSR service, and several client computers were provisioned for testers.</span></span>
  
#### <a name="deploy-the-sharepoint-farms"></a><span data-ttu-id="33645-580">部署為 SharePoint 伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="33645-580">Deploy the SharePoint farms</span></span>

<span data-ttu-id="33645-581">為 SharePoint 伺服器陣列已為了簡化環境穩定性及疑難排解帳戶部署在兩個階段中如有必要。</span><span class="sxs-lookup"><span data-stu-id="33645-581">The SharePoint farms were deployed in two stages in order to simplify environment stabilization and troubleshooting, if required.</span></span> <span data-ttu-id="33645-582">在第一階段中，每個伺服器陣列已部署在每一層的拓撲以支援所需的功能的伺服器的最小數目。</span><span class="sxs-lookup"><span data-stu-id="33645-582">During the first stage, each farm was deployed on the minimum number of servers for each tier of the topology to support the required functionality.</span></span>
  
<span data-ttu-id="33645-583">我們建立之前建立的 SharePoint 2013 伺服器已安裝的 SQL Server 資料庫伺服器。</span><span class="sxs-lookup"><span data-stu-id="33645-583">We created the database servers with SQL Server installed before creating the SharePoint 2013 servers.</span></span> <span data-ttu-id="33645-584">因為這是新的部署，我們會建立可用性群組，再部署 SharePoint。</span><span class="sxs-lookup"><span data-stu-id="33645-584">Because this was a new deployment, we created the availability groups before deploying SharePoint.</span></span> <span data-ttu-id="33645-585">我們建立最佳作法指導 MCS 為基礎的三個群組。</span><span class="sxs-lookup"><span data-stu-id="33645-585">We created three groups based on MCS best practice guidance.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="33645-586">建立版面配置區資料庫，以便您可以建立可用性群組在安裝 SharePoint 之前。</span><span class="sxs-lookup"><span data-stu-id="33645-586">Create placeholder databases so that you can create availability groups before the SharePoint installation.</span></span> <span data-ttu-id="33645-587">如需詳細資訊，請參閱 <<c0>設定 SQL Server 2012 AlwaysOn 可用性群組的 SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="33645-587">For more information, see [Configure SQL Server 2012 AlwaysOn Availability Groups for SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=517626)</span></span>
  
<span data-ttu-id="33645-588">我們會建立伺服器陣列，並加入額外的伺服器，依下列順序：</span><span class="sxs-lookup"><span data-stu-id="33645-588">We created the farm and joined additional servers in the following order:</span></span>
  
- <span data-ttu-id="33645-589">佈建 SP-sql-ha1 和 SP sql-ha2。</span><span class="sxs-lookup"><span data-stu-id="33645-589">Provision SP-SQL-HA1 and SP-SQL-HA2.</span></span>
    
- <span data-ttu-id="33645-590">將 AlwaysOn 設定，並建立伺服器陣列的三個可用性群組。</span><span class="sxs-lookup"><span data-stu-id="33645-590">Configure AlwaysOn and create the three availability groups for the farm.</span></span> 
    
- <span data-ttu-id="33645-591">佈建 sp-app1 到主機管理中心。</span><span class="sxs-lookup"><span data-stu-id="33645-591">Provision SP-APP1 to host Central Administration.</span></span>
    
- <span data-ttu-id="33645-592">佈建 SP WFE1 和 SP WFE2 裝載分散式快取。</span><span class="sxs-lookup"><span data-stu-id="33645-592">Provision SP-WFE1 and SP-WFE2 to host the distributed cache.</span></span> 
    
<span data-ttu-id="33645-593">我們在命令列執行**psconfig.exe**時，我們會使用_skipRegisterAsDistributedCachehost_參數。</span><span class="sxs-lookup"><span data-stu-id="33645-593">We used the  _skipRegisterAsDistributedCachehost_ parameter when we ran **psconfig.exe** at the command line.</span></span> <span data-ttu-id="33645-594">如需詳細資訊，請參閱 <<c0>規劃摘要及 SharePoint Server 2013 中的分散式快取服務。</span><span class="sxs-lookup"><span data-stu-id="33645-594">For more information, see [Plan for feeds and the Distributed Cache service in SharePoint Server 2013](https://docs.microsoft.com/sharepoint/administration/plan-for-feeds-and-the-distributed-cache-service).</span></span> 
  
<span data-ttu-id="33645-595">我們重複在復原環境中的下列步驟：</span><span class="sxs-lookup"><span data-stu-id="33645-595">We repeated the following steps in the recovery environment:</span></span>
  
- <span data-ttu-id="33645-596">佈建亞利桑那州-sql-ha1 和亞利桑那州 sql-ha2。</span><span class="sxs-lookup"><span data-stu-id="33645-596">Provision AZ-SQL-HA1 and AZ-SQL-HA2.</span></span>
    
- <span data-ttu-id="33645-597">將 AlwaysOn 設定，並建立伺服器陣列的三個可用性群組。</span><span class="sxs-lookup"><span data-stu-id="33645-597">Configure AlwaysOn and create the three availability groups for the farm.</span></span>
    
- <span data-ttu-id="33645-598">佈建亞利桑那州-APP1 架設管理中心網站。</span><span class="sxs-lookup"><span data-stu-id="33645-598">Provision AZ-APP1 to host Central Administration.</span></span>
    
- <span data-ttu-id="33645-599">佈建亞利桑那州 WFE1 和亞利桑那州 WFE2 裝載分散式快取。</span><span class="sxs-lookup"><span data-stu-id="33645-599">Provision AZ-WFE1 and AZ-WFE2 to host the distributed cache.</span></span>
    
<span data-ttu-id="33645-600">我們設定分散式快取及新增的測試使用者，以及測試內容之後，我們會啟動第二個階段的部署。</span><span class="sxs-lookup"><span data-stu-id="33645-600">After we configured the distributed cache and added test users and test content, we started stage two of the deployment.</span></span> <span data-ttu-id="33645-601">這需要向外延展層及設定伺服器陣列的伺服器可支援在伺服器陣列架構中所述的高可用性拓撲。</span><span class="sxs-lookup"><span data-stu-id="33645-601">This required scaling out the tiers and configuring the farm servers to support the high-availability topology described in the farm architecture.</span></span>
  
<span data-ttu-id="33645-602">下表說明虛擬機器、 子網路，以及我們為我們的復原伺服器陣列設定的可用性設定組。</span><span class="sxs-lookup"><span data-stu-id="33645-602">The following table describes the virtual machines, subnets, and availability sets we set up for our recovery farm.</span></span>
  
<span data-ttu-id="33645-603">**表格： 復原伺服器陣列基礎結構**</span><span class="sxs-lookup"><span data-stu-id="33645-603">**Table: Recovery farm infrastructure**</span></span>

|<span data-ttu-id="33645-604">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="33645-604">**Server name**</span></span>|<span data-ttu-id="33645-605">**Role**</span><span class="sxs-lookup"><span data-stu-id="33645-605">**Role**</span></span>|<span data-ttu-id="33645-606">**設定**</span><span class="sxs-lookup"><span data-stu-id="33645-606">**Configuration**</span></span>|<span data-ttu-id="33645-607">**子網路**</span><span class="sxs-lookup"><span data-stu-id="33645-607">**Subnet**</span></span>|<span data-ttu-id="33645-608">**可用性設定組**</span><span class="sxs-lookup"><span data-stu-id="33645-608">**Availability set**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="33645-609">spDRAD</span><span class="sxs-lookup"><span data-stu-id="33645-609">spDRAD</span></span>  <br/> |<span data-ttu-id="33645-610">使用 Active Directory 網域控制站</span><span class="sxs-lookup"><span data-stu-id="33645-610">Domain controller with Active Directory</span></span>  <br/> |<span data-ttu-id="33645-611">2 個處理器</span><span class="sxs-lookup"><span data-stu-id="33645-611">Two processors</span></span>  <br/> <span data-ttu-id="33645-612">從 512 MB 到 4 GB 的 RAM</span><span class="sxs-lookup"><span data-stu-id="33645-612">From 512 MB through 4 GB of RAM</span></span>  <br/> <span data-ttu-id="33645-613">1 x 127 GB 硬碟</span><span class="sxs-lookup"><span data-stu-id="33645-613">1 x 127-GB hard disk</span></span>  <br/> |<span data-ttu-id="33645-614">sp ADservers</span><span class="sxs-lookup"><span data-stu-id="33645-614">sp-ADservers</span></span>  <br/> ||
|<span data-ttu-id="33645-615">亞利桑那州-SP-FS</span><span class="sxs-lookup"><span data-stu-id="33645-615">AZ-SP-FS</span></span>  <br/> |<span data-ttu-id="33645-616">要備份的共用位置與 DFSR 端點的檔案伺服器</span><span class="sxs-lookup"><span data-stu-id="33645-616">File server with shares for backups and an endpoint for DFSR</span></span>  <br/> | <span data-ttu-id="33645-617">A5 組態：</span><span class="sxs-lookup"><span data-stu-id="33645-617">A5 configuration:</span></span> <br/>  <span data-ttu-id="33645-618">2 個處理器</span><span class="sxs-lookup"><span data-stu-id="33645-618">Two processors</span></span> <br/>  <span data-ttu-id="33645-619">14 GB 的 RAM</span><span class="sxs-lookup"><span data-stu-id="33645-619">14 GB of RAM</span></span> <br/>  <span data-ttu-id="33645-620">1 x 127 GB 硬碟</span><span class="sxs-lookup"><span data-stu-id="33645-620">1 x 127-GB hard disk</span></span> <br/>  <span data-ttu-id="33645-621">1 x 135 GB 硬碟</span><span class="sxs-lookup"><span data-stu-id="33645-621">1 x 135-GB hard disk</span></span> <br/>  <span data-ttu-id="33645-622">1 x 127 GB 硬碟</span><span class="sxs-lookup"><span data-stu-id="33645-622">1 x 127-GB hard disk</span></span> <br/>  <span data-ttu-id="33645-623">1 x 150 GB 的硬碟</span><span class="sxs-lookup"><span data-stu-id="33645-623">1 x 150-GB hard disk</span></span> <br/> |<span data-ttu-id="33645-624">sp databaseservers</span><span class="sxs-lookup"><span data-stu-id="33645-624">sp-databaseservers</span></span>  <br/> |<span data-ttu-id="33645-625">DATA_SET</span><span class="sxs-lookup"><span data-stu-id="33645-625">DATA_SET</span></span>  <br/> |
|<span data-ttu-id="33645-626">亞利桑那州 WFE1、 亞利桑那州-WFE2</span><span class="sxs-lookup"><span data-stu-id="33645-626">AZ-WFE1, AZ -WFE2</span></span>  <br/> |<span data-ttu-id="33645-627">Front End 網頁伺服器</span><span class="sxs-lookup"><span data-stu-id="33645-627">Front End Web servers</span></span>  <br/> | <span data-ttu-id="33645-628">A5 組態：</span><span class="sxs-lookup"><span data-stu-id="33645-628">A5 configuration:</span></span> <br/>  <span data-ttu-id="33645-629">2 個處理器</span><span class="sxs-lookup"><span data-stu-id="33645-629">Two processors</span></span> <br/>  <span data-ttu-id="33645-630">14 GB 的 RAM</span><span class="sxs-lookup"><span data-stu-id="33645-630">14 GB of RAM</span></span> <br/>  <span data-ttu-id="33645-631">1 x 127 GB 硬碟</span><span class="sxs-lookup"><span data-stu-id="33645-631">1 x 127-GB hard disk</span></span> <br/> |<span data-ttu-id="33645-632">sp webservers</span><span class="sxs-lookup"><span data-stu-id="33645-632">sp-webservers</span></span>  <br/> |<span data-ttu-id="33645-633">WFE_SET</span><span class="sxs-lookup"><span data-stu-id="33645-633">WFE_SET</span></span>  <br/> |
|<span data-ttu-id="33645-634">亞利桑那州-APP1、 亞利桑那州-APP2、 亞利桑那州-APP3</span><span class="sxs-lookup"><span data-stu-id="33645-634">AZ -APP1, AZ -APP2, AZ -APP3</span></span>  <br/> |<span data-ttu-id="33645-635">應用程式伺服器</span><span class="sxs-lookup"><span data-stu-id="33645-635">Application servers</span></span>  <br/> | <span data-ttu-id="33645-636">A5 組態：</span><span class="sxs-lookup"><span data-stu-id="33645-636">A5 configuration:</span></span> <br/>  <span data-ttu-id="33645-637">2 個處理器</span><span class="sxs-lookup"><span data-stu-id="33645-637">Two processors</span></span> <br/>  <span data-ttu-id="33645-638">14 GB 的 RAM</span><span class="sxs-lookup"><span data-stu-id="33645-638">14 GB of RAM</span></span> <br/>  <span data-ttu-id="33645-639">1 x 127 GB 硬碟</span><span class="sxs-lookup"><span data-stu-id="33645-639">1 x 127-GB hard disk</span></span> <br/> |<span data-ttu-id="33645-640">sp applicationservers</span><span class="sxs-lookup"><span data-stu-id="33645-640">sp-applicationservers</span></span>  <br/> |<span data-ttu-id="33645-641">APP_SET</span><span class="sxs-lookup"><span data-stu-id="33645-641">APP_SET</span></span>  <br/> |
|<span data-ttu-id="33645-642">亞利桑那州-SQL-HA1，亞利桑那州-SQL-HA2</span><span class="sxs-lookup"><span data-stu-id="33645-642">AZ -SQL-HA1, AZ -SQL-HA2</span></span>  <br/> |<span data-ttu-id="33645-643">資料庫伺服器和 AlwaysOn 可用性群組的主要和次要複本</span><span class="sxs-lookup"><span data-stu-id="33645-643">Database servers and primary and secondary replicas for AlwaysOn availability groups</span></span>  <br/> | <span data-ttu-id="33645-644">A5 組態：</span><span class="sxs-lookup"><span data-stu-id="33645-644">A5 configuration:</span></span> <br/>  <span data-ttu-id="33645-645">2 個處理器</span><span class="sxs-lookup"><span data-stu-id="33645-645">Two processors</span></span> <br/>  <span data-ttu-id="33645-646">14 GB 的 RAM</span><span class="sxs-lookup"><span data-stu-id="33645-646">14 GB of RAM</span></span> <br/> |<span data-ttu-id="33645-647">sp databaseservers</span><span class="sxs-lookup"><span data-stu-id="33645-647">sp-databaseservers</span></span>  <br/> |<span data-ttu-id="33645-648">DATA_SET</span><span class="sxs-lookup"><span data-stu-id="33645-648">DATA_SET</span></span>  <br/> |
   
### <a name="operations"></a><span data-ttu-id="33645-649">營運</span><span class="sxs-lookup"><span data-stu-id="33645-649">Operations</span></span>

<span data-ttu-id="33645-650">這些測試小組穩定的伺服器陣列環境，並完成功能測試之後，開始下列作業來設定內部復原環境所需的工作：</span><span class="sxs-lookup"><span data-stu-id="33645-650">After the test team stabilized the farm environments and completed functional testing, they started the following operations tasks required to configure the on-premises recovery environment:</span></span>
  
- <span data-ttu-id="33645-651">設定完整及差異備份。</span><span class="sxs-lookup"><span data-stu-id="33645-651">Configure full and differential backups.</span></span>
    
- <span data-ttu-id="33645-652">在內部部署環境與 Azure 環境之間傳送交易記錄檔的檔案伺服器上設定 DFSR。</span><span class="sxs-lookup"><span data-stu-id="33645-652">Configure DFSR on the file servers that transfer transaction logs between the on-premises environment and the Azure environment.</span></span>
    
- <span data-ttu-id="33645-653">設定記錄傳送之主要資料庫伺服器上。</span><span class="sxs-lookup"><span data-stu-id="33645-653">Configure log shipping on the primary database server.</span></span>
    
- <span data-ttu-id="33645-654">穩定、 驗證及疑難排解記錄傳送，視需要。</span><span class="sxs-lookup"><span data-stu-id="33645-654">Stabilize, validate, and troubleshoot log shipping, as required.</span></span> <span data-ttu-id="33645-655">這包含用來識別和記載任何可能會造成問題，例如網路延遲造成記錄傳送或 DFSR 檔案同步處理失敗的行為。</span><span class="sxs-lookup"><span data-stu-id="33645-655">This included identifying and documenting any behavior that might cause issues, such as network latency, which would cause log shipping or DFSR file synchronization failures.</span></span>
    
### <a name="databases"></a><span data-ttu-id="33645-656">資料庫</span><span class="sxs-lookup"><span data-stu-id="33645-656">Databases</span></span>

<span data-ttu-id="33645-657">容錯移轉測試涉及下列資料庫：</span><span class="sxs-lookup"><span data-stu-id="33645-657">Our failover tests involved the following databases:</span></span> 
  
- <span data-ttu-id="33645-658">WSS_Content</span><span class="sxs-lookup"><span data-stu-id="33645-658">WSS_Content</span></span>
    
- <span data-ttu-id="33645-659">ManagedMetadata</span><span class="sxs-lookup"><span data-stu-id="33645-659">ManagedMetadata</span></span>
    
- <span data-ttu-id="33645-660">設定檔資料庫</span><span class="sxs-lookup"><span data-stu-id="33645-660">Profile DB</span></span>
    
- <span data-ttu-id="33645-661">同步處理資料庫</span><span class="sxs-lookup"><span data-stu-id="33645-661">Sync DB</span></span>
    
- <span data-ttu-id="33645-662">社交資料庫</span><span class="sxs-lookup"><span data-stu-id="33645-662">Social DB</span></span>
    
- <span data-ttu-id="33645-663">內容類型中樞 （專用的內容類型整合中樞的資料庫）</span><span class="sxs-lookup"><span data-stu-id="33645-663">Content Type Hub (a database for a dedicated Content Type Syndication Hub)</span></span>
    
## <a name="troubleshooting-tips"></a><span data-ttu-id="33645-664">疑難排解提示</span><span class="sxs-lookup"><span data-stu-id="33645-664">Troubleshooting tips</span></span>

<span data-ttu-id="33645-665">本節說明我們在我們的測試和其解決方案期間遇到的問題。</span><span class="sxs-lookup"><span data-stu-id="33645-665">The section explains the problems we encountered during our testing and their solutions.</span></span> 
  
### <a name="using-the-term-store-management-tool-caused-the-error-the-managed-metadata-store-or-connection-is-currently-not-available"></a><span data-ttu-id="33645-666">使用字詞庫管理工具造成錯誤，「 受管理中繼資料儲存區或連線目前無法使用。 」</span><span class="sxs-lookup"><span data-stu-id="33645-666">Using the Term Store Management Tool caused the error, "The Managed Metadata Store or Connection is currently not available."</span></span>

<span data-ttu-id="33645-667">確定 web 應用程式所使用的應用程式集區帳戶具有字詞儲存區權限的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="33645-667">Ensure that the application pool account used by the web application has the Read Access to Term Store permission.</span></span>
  
### <a name="custom-term-sets-are-not-available-in-the-site-collection"></a><span data-ttu-id="33645-668">自訂字詞組中沒有提供網站集合</span><span class="sxs-lookup"><span data-stu-id="33645-668">Custom term sets are not available in the site collection</span></span>

<span data-ttu-id="33645-669">檢查遺失的服務應用程式相關聯，您的內容的網站集合與內容類型中樞之間。</span><span class="sxs-lookup"><span data-stu-id="33645-669">Check for a missing service application association between your content site collection and your content type hub.</span></span> <span data-ttu-id="33645-670">此外，[**受管理的中繼資料-<site collection name>連線**屬性畫面中，確定已啟用此選項：**此服務應用程式是特定詞彙集的預設儲存位置。**</span><span class="sxs-lookup"><span data-stu-id="33645-670">In addition, under the **Managed Metadata - <site collection name> Connection** properties screen, make sure this option is enabled: **This service application is the default storage location for column specific term sets.**</span></span>
  
### <a name="the-get-adforest-windows-powershell-command-generates-the-error-the-term-get-adforest-is-not-recognized-as-the-name-of-a-cmdlet-function-script-file-or-operable-program"></a><span data-ttu-id="33645-671">取得 ADForest Windows PowerShell 命令將會產生錯誤、 」 字詞 ' Get-ADForest' 無法辨識為指令程式、 函式、 指令碼檔案或可執行的程式名稱 」。</span><span class="sxs-lookup"><span data-stu-id="33645-671">The Get-ADForest Windows PowerShell command generates the error, "The term 'Get-ADForest' is not recognized as the name of a cmdlet, function, script file, or operable program."</span></span>

<span data-ttu-id="33645-672">當設定使用者設定檔，您會需要 Active Directory 樹系名稱。</span><span class="sxs-lookup"><span data-stu-id="33645-672">When setting up user profiles, you need the Active Directory forest name.</span></span> <span data-ttu-id="33645-673">在 [新增角色及功能精靈，請確定您已啟用 Active Directory 模組的 Windows PowerShell （在 [**遠端伺服器管理 Tools>Role 管理 Tools>AD DS 與 AD LDS 工具**] 區段中）。</span><span class="sxs-lookup"><span data-stu-id="33645-673">In the Add Roles and Features Wizard, ensure that you have enabled the Active Directory Module for Windows PowerShell (under the **Remote Server Administration Tools>Role Administration Tools>AD DS and AD LDS Tools** section).</span></span> <span data-ttu-id="33645-674">此外，執行下列命令，以協助確保您會在載入相依性的軟體使用**Get-ADForest**之前。</span><span class="sxs-lookup"><span data-stu-id="33645-674">In addition, run the following commands before using **Get-ADForest** to help ensure that your software dependencies are loaded.</span></span>
  
```
Import-module servermanager
Import-module activedirectory

```

### <a name="availability-group-creation-fails-at-starting-the-alwaysonhealth-xevent-session-on-server-name"></a><span data-ttu-id="33645-675">建立可用性群組在啟動 'AlwaysOn_health' XEvent 工作階段失敗 '<server name>'</span><span class="sxs-lookup"><span data-stu-id="33645-675">Availability group creation fails at Starting the 'AlwaysOn_health' XEvent session on '<server name>'</span></span>

<span data-ttu-id="33645-676">請確定您的容錯移轉叢集的兩個節點的中] 狀態 」 最多 」 和未 「 暫停 」 或 「 已停止 」。</span><span class="sxs-lookup"><span data-stu-id="33645-676">Ensure that both nodes of your failover cluster are in the Status "Up" and not "Paused" or "Stopped".</span></span> 
  
### <a name="sql-server-log-shipping-job-fails-with-access-denied-error-trying-to-connect-to-the-file-share"></a><span data-ttu-id="33645-677">SQL Server 記錄傳送工作會失敗並拒絕存取嘗試連接到的檔案共用的錯誤</span><span class="sxs-lookup"><span data-stu-id="33645-677">SQL Server log shipping job fails with access denied error trying to connect to the file share</span></span>

<span data-ttu-id="33645-678">確定您的 SQL Server 代理程式正在執行網路認證，而不是預設的認證。</span><span class="sxs-lookup"><span data-stu-id="33645-678">Ensure that your SQL Server Agent is running under network credentials, instead of the default credentials.</span></span>
  
### <a name="sql-server-log-shipping-job-indicates-success-but-no-files-are-copied"></a><span data-ttu-id="33645-679">SQL Server 記錄傳送工作表示成功，但不會複製檔</span><span class="sxs-lookup"><span data-stu-id="33645-679">SQL Server log shipping job indicates success, but no files are copied</span></span>

<span data-ttu-id="33645-680">這是因為可用性群組的預設備份喜好設定為**次要偏好**。</span><span class="sxs-lookup"><span data-stu-id="33645-680">This happens because the default backup preference for an availability group is **Prefer Secondary**.</span></span> <span data-ttu-id="33645-681">請確定您從可用性群組，而不是主要; 的次要伺服器執行記錄傳送工作否則，工作會以無訊息方式失敗。</span><span class="sxs-lookup"><span data-stu-id="33645-681">Ensure that you run the log shipping job from the secondary server for the availability group instead of the primary; otherwise, the job will fail silently.</span></span> 
  
### <a name="managed-metadata-service-or-other-sharepoint-service-fails-to-start-automatically-after-installation"></a><span data-ttu-id="33645-682">受管理的中繼資料服務 （或其他 SharePoint 服務） 失敗安裝後會自動啟動</span><span class="sxs-lookup"><span data-stu-id="33645-682">Managed Metadata service (or other SharePoint service) fails to start automatically after installation</span></span>

<span data-ttu-id="33645-683">服務可能需要數分鐘才能啟動，請根據效能及目前的 SharePoint Server 的負載。</span><span class="sxs-lookup"><span data-stu-id="33645-683">Services might take several minutes to start, depending on the performance and current load of your SharePoint Server.</span></span> <span data-ttu-id="33645-684">以手動方式 service 按一下 [**開始]** ，並提供適當時間為啟動時偶爾會重新整理伺服器] 畫面上的服務，來監視其狀態。</span><span class="sxs-lookup"><span data-stu-id="33645-684">Manually click **Start** for the service and provide adequate time for startup while occasionally refreshing the Services on Server screen to monitor its status.</span></span> <span data-ttu-id="33645-685">萬一服務仍然維持停止，啟用 SharePoint 診斷記錄，請嘗試再次啟動服務，然後再查看錯誤記錄檔。</span><span class="sxs-lookup"><span data-stu-id="33645-685">In case the service remains stopped, enable SharePoint diagnostic logging, attempt to start the service again, and then check the log for errors.</span></span> <span data-ttu-id="33645-686">如需詳細資訊，請參閱 < <b0>SharePoint 2013 中設定診斷記錄</b0></span><span class="sxs-lookup"><span data-stu-id="33645-686">For more information, see [Configure diagnostic logging in SharePoint 2013](https://docs.microsoft.com/sharepoint/administration/configure-diagnostic-logging)</span></span>
  
### <a name="after-changing-dns-to-the-azure-failover-environment-client-browsers-continue-to-use-the-old-ip-address-for-the-sharepoint-site"></a><span data-ttu-id="33645-687">變更後 DNS 至 Azure 的容錯移轉環境，用戶端瀏覽器繼續使用舊的 IP 位址的 SharePoint 網站</span><span class="sxs-lookup"><span data-stu-id="33645-687">After changing DNS to the Azure failover environment, client browsers continue to use the old IP address for the SharePoint site</span></span>

<span data-ttu-id="33645-688">您的 DNS 變更可能不會顯示所有的用戶端立即。</span><span class="sxs-lookup"><span data-stu-id="33645-688">Your DNS change might not be visible to all clients immediately.</span></span> <span data-ttu-id="33645-689">測試用戶端上從提升權限的命令提示字元執行下列命令，嘗試再次存取網站。</span><span class="sxs-lookup"><span data-stu-id="33645-689">On a test client, perform the following command from an elevated command prompt and attempt to access the site again.</span></span>
  
```
Ipconfig /flushdns
```

## <a name="additional-resources"></a><span data-ttu-id="33645-690">其他資源</span><span class="sxs-lookup"><span data-stu-id="33645-690">Additional resources</span></span>

[<span data-ttu-id="33645-691">SharePoint 資料庫支援的高可用性和災害復原選項</span><span class="sxs-lookup"><span data-stu-id="33645-691">Supported high availability and disaster recovery options for SharePoint databases</span></span>](https://docs.microsoft.com/sharepoint/administration/supported-high-availability-and-disaster-recovery-options-for-sharepoint-databas)
  
[<span data-ttu-id="33645-692">設定 SQL Server 2012 AlwaysOn 可用性群組的 SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="33645-692">Configure SQL Server 2012 AlwaysOn Availability Groups for SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=393122)
  
## <a name="see-also"></a><span data-ttu-id="33645-693">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33645-693">See Also</span></span>

[<span data-ttu-id="33645-694">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="33645-694">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)



