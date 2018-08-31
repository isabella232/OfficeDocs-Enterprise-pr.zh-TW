---
title: Microsoft Azure 中的 SharePoint Server 2013 災害復原
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 04/17/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Deployment
ms.assetid: e9d14cb2-ff28-4a18-a444-cebf891880ea
description: 摘要： 使用 Azure，您可以為您的內部部署 SharePoint 伺服器陣列建立嚴重損壞修復環境。本文說明如何設計及實作此解決方案。
ms.openlocfilehash: 56d9fa039bfe533afbc5ac7c1e060d43c0801aef
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915798"
---
# <a name="sharepoint-server-2013-disaster-recovery-in-microsoft-azure"></a><span data-ttu-id="cd252-104">Microsoft Azure 中的 SharePoint Server 2013 災害復原</span><span class="sxs-lookup"><span data-stu-id="cd252-104">SharePoint Server 2013 Disaster Recovery in Microsoft Azure</span></span>

 <span data-ttu-id="cd252-p102">**摘要：** 使用 Azure，您可以為您的內部部署 SharePoint 伺服器陣列建立嚴重損壞修復環境。本文說明如何設計及實作此解決方案。</span><span class="sxs-lookup"><span data-stu-id="cd252-p102">**Summary:** Using Azure, you can create a disaster-recovery environment for your on-premises SharePoint farm. This article describes how to design and implement this solution.</span></span>

 <span data-ttu-id="cd252-107">**觀賞 SharePoint Server 2013 嚴重損壞修復概觀影片**</span><span class="sxs-lookup"><span data-stu-id="cd252-107">**Watch the SharePoint Server 2013 disaster recovery overview video**</span></span>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/1b73ec8f-29bd-44eb-aa3a-f7932784bfd9?autoplay=false]
  
 <span data-ttu-id="cd252-p103">發生災害事件 SharePoint 內部部署環境，您最高的優先順序時若要取得執行一次迅速系統。與 SharePoint 的嚴重損壞修復時更快速且更容易必須已在執行 Microsoft Azure 中的備份環境。本影片說明 SharePoint 暖容錯移轉環境的主要概念及補充本文中提供的完整詳細資料。</span><span class="sxs-lookup"><span data-stu-id="cd252-p103">When disaster strikes your SharePoint on-premises environment, your top priority is to get the system running again quickly. Disaster recovery with SharePoint is quicker and easier when you have a backup environment already running in Microsoft Azure. This video explains the main concepts of a SharePoint warm failover environment and complements the full details available in this article.</span></span>
  
<span data-ttu-id="cd252-111">使用本文使用下列解決方案模型： **SharePoint Disaster Recovery in Microsoft Azure**。</span><span class="sxs-lookup"><span data-stu-id="cd252-111">Use this article with the following solution model: **SharePoint Disaster Recovery in Microsoft Azure**.</span></span>
  
<span data-ttu-id="cd252-112">[![SharePoint 到 Azure 的災害復原程序](media/SP-DR-Azure.png)](https://go.microsoft.com/fwlink/p/?LinkId=392555)</span><span class="sxs-lookup"><span data-stu-id="cd252-112">[![SharePoint disaster-recovery process to Azure](media/SP-DR-Azure.png)](https://go.microsoft.com/fwlink/p/?LinkId=392555)</span></span>
  
 <span data-ttu-id="cd252-113">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555) |  [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)</span><span class="sxs-lookup"><span data-stu-id="cd252-113">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555) |  [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)</span></span>
  
<span data-ttu-id="cd252-114">本文內容：</span><span class="sxs-lookup"><span data-stu-id="cd252-114">In this article:</span></span>
  
- [<span data-ttu-id="cd252-115">使用 Azure 基礎結構服務的嚴重損壞修復</span><span class="sxs-lookup"><span data-stu-id="cd252-115">Use Azure Infrastructure Services for disaster recovery</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#AZ)
    
- [<span data-ttu-id="cd252-116">解決方案描述</span><span class="sxs-lookup"><span data-stu-id="cd252-116">Solution description</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#SOL)
    
- [<span data-ttu-id="cd252-117">詳細架構</span><span class="sxs-lookup"><span data-stu-id="cd252-117">Detailed architecture</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#arch)
    
- [<span data-ttu-id="cd252-118">嚴重損壞復原藍圖</span><span class="sxs-lookup"><span data-stu-id="cd252-118">Disaster recovery roadmap</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#RDmap)
    
- [<span data-ttu-id="cd252-119">階段 1： 設計嚴重損壞修復環境</span><span class="sxs-lookup"><span data-stu-id="cd252-119">Phase 1: Design the disaster recovery environment</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase1)
    
- [<span data-ttu-id="cd252-120">階段 2： 建立 Azure 虛擬網路和 VPN 連線</span><span class="sxs-lookup"><span data-stu-id="cd252-120">Phase 2: Create the Azure virtual network and VPN connection</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase2)
    
- [<span data-ttu-id="cd252-121">階段 3： 部署 Active Directory 及網域名稱服務以 Azure 虛擬網路</span><span class="sxs-lookup"><span data-stu-id="cd252-121">Phase 3: Deploy Active Directory and Domain Name Services to the Azure virtual network</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase3)
    
- [<span data-ttu-id="cd252-122">階段 4： 部署在 Azure 中的 SharePoint 復原伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="cd252-122">Phase 4: Deploy the SharePoint recovery farm in Azure</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase4)
    
- [<span data-ttu-id="cd252-123">階段 5： 設定伺服器陣列之間 DFSR</span><span class="sxs-lookup"><span data-stu-id="cd252-123">Phase 5: Set up DFSR between the farms</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase5)
    
- [<span data-ttu-id="cd252-124">階段 6： 設定記錄傳送至修復伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="cd252-124">Phase 6: Set up log shipping to the recovery farm</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase6)
    
- [<span data-ttu-id="cd252-125">階段 7： 驗證容錯移轉及復原</span><span class="sxs-lookup"><span data-stu-id="cd252-125">Phase 7: Validate failover and recovery</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase7)
    
- [<span data-ttu-id="cd252-126">Microsoft 概念證明環境</span><span class="sxs-lookup"><span data-stu-id="cd252-126">Microsoft proof-of-concept environment</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#POC)
    
- [<span data-ttu-id="cd252-127">疑難排解提示</span><span class="sxs-lookup"><span data-stu-id="cd252-127">Troubleshooting tips</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Troubleshooting)
    
## <a name="use-azure-infrastructure-services-for-disaster-recovery"></a><span data-ttu-id="cd252-128">使用 Azure 基礎結構服務的嚴重損壞修復</span><span class="sxs-lookup"><span data-stu-id="cd252-128">Use Azure Infrastructure Services for disaster recovery</span></span>

<span data-ttu-id="cd252-p104">許多組織沒有損毀修復環境 for SharePoint，可以是昂貴建立及維護的內部。Azure 基礎結構服務提供強大嚴重損壞復原環境的更多彈性、 較不昂貴比內部替代項目。</span><span class="sxs-lookup"><span data-stu-id="cd252-p104">Many organizations do not have a disaster recovery environment for SharePoint, which can be expensive to build and maintain on-premises. Azure Infrastructure Services provides compelling options for disaster recovery environments that are more flexible and less expensive than the on-premises alternatives.</span></span>
  
<span data-ttu-id="cd252-131">使用 Azure 基礎結構服務的優點包括：</span><span class="sxs-lookup"><span data-stu-id="cd252-131">The advantages for using Azure Infrastructure Services include:</span></span>
  
- <span data-ttu-id="cd252-p105">**較少的高成本資源**維護及工資資源少於內部嚴重損壞修復環境。資源數目取決於您選擇的嚴重損壞修復環境： 冷待命、 暖待命或熱待命。</span><span class="sxs-lookup"><span data-stu-id="cd252-p105">**Fewer costly resources** Maintain and pay for fewer resources than on-premises disaster recovery environments. The number of resources depends on which disaster-recovery environment you choose: cold standby, warm standby, or hot standby.</span></span>
    
- <span data-ttu-id="cd252-p106">**更好的資源彈性**在發生災害時輕鬆地向外延展負載要求修復 SharePoint 伺服器陣列。當您不再需要資源的向外。</span><span class="sxs-lookup"><span data-stu-id="cd252-p106">**Better resource flexibility** In the event of a disaster, easily scale out your recovery SharePoint farm to meet load requirements. Scale in when you no longer need the resources.</span></span>
    
- <span data-ttu-id="cd252-136">**較低的資料中心承諾**使用 Azure 基礎結構服務而不是在不同的區域中的次要資料中心內演變。</span><span class="sxs-lookup"><span data-stu-id="cd252-136">**Lower datacenter commitment** Use Azure Infrastructure Services instead of investing in a secondary datacenter in a different region.</span></span>
    
<span data-ttu-id="cd252-p107">有較不複雜組織剛入門嚴重損壞修復選項及進階具有高可靠度需求的組織的選項。在雲端平台上主控環境時，有點不同冷、 暖，以及熱待命環境中的定義。下表說明這些建置在 Azure 中的 SharePoint 復原伺服器陣列的環境。</span><span class="sxs-lookup"><span data-stu-id="cd252-p107">There are less-complex options for organizations just getting started with disaster recovery and advanced options for organizations with high-resilience requirements. The definitions for cold, warm, and hot standby environments are a little different when the environment is hosted on a cloud platform. The following table describes these environments for building a SharePoint recovery farm in Azure.</span></span>
  
<span data-ttu-id="cd252-140">**表格： 復原環境**</span><span class="sxs-lookup"><span data-stu-id="cd252-140">**Table: Recovery environments**</span></span>

|<span data-ttu-id="cd252-141">**復原環境的類型**</span><span class="sxs-lookup"><span data-stu-id="cd252-141">**Type of recovery environment**</span></span>|<span data-ttu-id="cd252-142">**描述**</span><span class="sxs-lookup"><span data-stu-id="cd252-142">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="cd252-143">熱</span><span class="sxs-lookup"><span data-stu-id="cd252-143">Hot</span></span>  <br/> |<span data-ttu-id="cd252-144">完全大小的伺服器陣列已佈建、 更新及執行處於待命狀態。</span><span class="sxs-lookup"><span data-stu-id="cd252-144">A fully sized farm is provisioned, updated, and running on standby.</span></span>  <br/> |
|<span data-ttu-id="cd252-145">暖</span><span class="sxs-lookup"><span data-stu-id="cd252-145">Warm</span></span>  <br/> |<span data-ttu-id="cd252-146">在伺服器陣列內建和虛擬機器都在執行並更新。</span><span class="sxs-lookup"><span data-stu-id="cd252-146">The farm is built and virtual machines are running and updated.</span></span>  <br/> <span data-ttu-id="cd252-147">復原作業包含附加內容資料庫、 佈建服務應用程式和編目的內容。</span><span class="sxs-lookup"><span data-stu-id="cd252-147">Recovery includes attaching content databases, provisioning service applications, and crawling content.</span></span>  <br/> <span data-ttu-id="cd252-148">在伺服器陣列可以是實際執行伺服器陣列較小版本，然後向外延展到完整的使用者提供服務。</span><span class="sxs-lookup"><span data-stu-id="cd252-148">The farm can be a smaller version of the production farm and then scaled out to serve the full user base.</span></span>  <br/> |
|<span data-ttu-id="cd252-149">冷</span><span class="sxs-lookup"><span data-stu-id="cd252-149">Cold</span></span>  <br/> |<span data-ttu-id="cd252-150">在伺服器陣列完全建置基礎，但已停止虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="cd252-150">The farm is fully built, but the virtual machines are stopped.</span></span>  <br/> <span data-ttu-id="cd252-151">維護環境包含隨時啟動虛擬機器、 修補、 更新及驗證環境。</span><span class="sxs-lookup"><span data-stu-id="cd252-151">Maintaining the environment includes starting the virtual machines from time to time, patching, updating, and verifying the environment.</span></span>  <br/> <span data-ttu-id="cd252-152">開始在發生災害時完整的環境。</span><span class="sxs-lookup"><span data-stu-id="cd252-152">Start the full environment in the event of a disaster.</span></span>  <br/> |
   
<span data-ttu-id="cd252-p108">請務必評估貴組織的復原時間目標 (Rto) 及復原點目標 (RPOs)。這些需求決定哪些環境是最適合組織的投資。</span><span class="sxs-lookup"><span data-stu-id="cd252-p108">It's important to evaluate your organization's Recovery Time Objectives (RTOs) and Recovery Point Objectives (RPOs). These requirements determine which environment is the most appropriate investment for your organization.</span></span>
  
<span data-ttu-id="cd252-p109">本文的指示說明如何實作暖待命環境。您可以也適應該冷待命環境中，但您必須遵循以支援這種環境的其他程序。本文不會說明如何實作熱待命環境。</span><span class="sxs-lookup"><span data-stu-id="cd252-p109">The guidance in this article describes how to implement a warm standby environment. You can also adapt it to a cold standby environment, although you need to follow additional procedures to support this kind of environment. This article does not describe how to implement a hot standby environment.</span></span>
  
<span data-ttu-id="cd252-158">如需嚴重損壞修復解決方案的詳細資訊，請參閱[高可用性和災害復原概念 in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkID=393114)和[選擇 SharePoint 2013 的災害復原策略](https://go.microsoft.com/fwlink/p/?linkid=203228)。</span><span class="sxs-lookup"><span data-stu-id="cd252-158">For more information about disaster recovery solutions, see [High availability and disaster recovery concepts in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkID=393114) and [Choose a disaster recovery strategy for SharePoint 2013](https://go.microsoft.com/fwlink/p/?linkid=203228).</span></span>
  
## <a name="solution-description"></a><span data-ttu-id="cd252-159">解決方案描述</span><span class="sxs-lookup"><span data-stu-id="cd252-159">Solution description</span></span>

<span data-ttu-id="cd252-160">暖待命嚴重損壞修復解決方案需要下列環境：</span><span class="sxs-lookup"><span data-stu-id="cd252-160">The warm standby disaster-recovery solution requires the following environment:</span></span>
  
- <span data-ttu-id="cd252-161">內部部署 SharePoint 實際執行伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="cd252-161">An on-premises SharePoint production farm</span></span>
    
- <span data-ttu-id="cd252-162">在 Azure 中復原 SharePoint 伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="cd252-162">A recovery SharePoint farm in Azure</span></span>
    
- <span data-ttu-id="cd252-163">兩個環境之間的網站 VPN 連線</span><span class="sxs-lookup"><span data-stu-id="cd252-163">A site-to-site VPN connection between the two environments</span></span>
    
<span data-ttu-id="cd252-164">下圖說明下列三個元素。</span><span class="sxs-lookup"><span data-stu-id="cd252-164">The following figure illustrates these three elements.</span></span>
  
<span data-ttu-id="cd252-165">**圖： 元素的 Azure 中暖待命解決方案**</span><span class="sxs-lookup"><span data-stu-id="cd252-165">**Figure: Elements of a warm standby solution in Azure**</span></span>

![Azure 中 SharePoint 暖待命解決方案的元素](media/AZarch-AZWarmStndby.png)
  
<span data-ttu-id="cd252-167">SQL Server 記錄傳送與分散式檔案系統複寫 (DFSR) 用於將資料庫備份和交易記錄檔複製到 Azure 中的復原伺服器陣列：</span><span class="sxs-lookup"><span data-stu-id="cd252-167">SQL Server log shipping with Distributed File System Replication (DFSR) is used to copy database backups and transaction logs to the recovery farm in Azure:</span></span> 
  
- <span data-ttu-id="cd252-p110">DFSR 會傳送到復原環境的實際執行環境中的記錄檔。在 WAN 案例中，DFSR 會比在 Azure 中傳送直接至次要伺服器的記錄檔更有效率。</span><span class="sxs-lookup"><span data-stu-id="cd252-p110">DFSR transfers logs from the production environment to the recovery environment. In a WAN scenario, DFSR is more efficient than shipping the logs directly to the secondary server in Azure.</span></span>
    
- <span data-ttu-id="cd252-170">記錄檔會在 Azure 中的復原環境的 SQL server 重新顯示。</span><span class="sxs-lookup"><span data-stu-id="cd252-170">Logs are replayed to the SQL Server in the recovery environment in Azure.</span></span>
    
- <span data-ttu-id="cd252-171">除非執行復原練習，未附加傳送記錄 SharePoint 內容資料庫復原環境中。</span><span class="sxs-lookup"><span data-stu-id="cd252-171">You don't attach log-shipped SharePoint content databases in the recovery environment until a recovery exercise is performed.</span></span>
    
<span data-ttu-id="cd252-172">執行下列步驟來復原伺服器陣列：</span><span class="sxs-lookup"><span data-stu-id="cd252-172">Perform the following steps to recover the farm:</span></span>
  
1. <span data-ttu-id="cd252-173">停止記錄傳送。</span><span class="sxs-lookup"><span data-stu-id="cd252-173">Stop log shipping.</span></span>
    
2. <span data-ttu-id="cd252-174">停止接受主要伺服器陣列的流量。</span><span class="sxs-lookup"><span data-stu-id="cd252-174">Stop accepting traffic to the primary farm.</span></span>
    
3. <span data-ttu-id="cd252-175">重新顯示的最後一個交易記錄檔。</span><span class="sxs-lookup"><span data-stu-id="cd252-175">Replay the final transaction logs.</span></span>
    
4. <span data-ttu-id="cd252-176">將內容資料庫附加至伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="cd252-176">Attach the content databases to the farm.</span></span>
    
5. <span data-ttu-id="cd252-177">複寫的服務資料庫還原服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="cd252-177">Restore service applications from the replicated services databases.</span></span>
    
6. <span data-ttu-id="cd252-178">更新為指向的復原伺服器陣列的網域名稱系統 (DNS) 記錄。</span><span class="sxs-lookup"><span data-stu-id="cd252-178">Update Domain Name System (DNS) records to point to the recovery farm.</span></span>
    
7. <span data-ttu-id="cd252-179">開始完整編目。</span><span class="sxs-lookup"><span data-stu-id="cd252-179">Start a full crawl.</span></span>
    
<span data-ttu-id="cd252-p111">我們建議您定期排練這些步驟與文件它們可以協助確保您 live 復原順利執行。附加內容資料庫還原服務應用程式可能需要一些時間和通常需要一些手動設定。</span><span class="sxs-lookup"><span data-stu-id="cd252-p111">We recommend that you rehearse these steps regularly and document them to help ensure that your live recovery runs smoothly. Attaching content databases and restoring service applications can take some time and typically involves some manual configuration.</span></span>
  
<span data-ttu-id="cd252-182">執行復原後，此解決方案會提供下表列出的項目。</span><span class="sxs-lookup"><span data-stu-id="cd252-182">After a recovery is performed, this solution provides the items listed in the following table.</span></span>
  
<span data-ttu-id="cd252-183">**表格： 解決方案復原目標**</span><span class="sxs-lookup"><span data-stu-id="cd252-183">**Table: Solution recovery objectives**</span></span>

|<span data-ttu-id="cd252-184">**項目**</span><span class="sxs-lookup"><span data-stu-id="cd252-184">**Item**</span></span>|<span data-ttu-id="cd252-185">**描述**</span><span class="sxs-lookup"><span data-stu-id="cd252-185">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="cd252-186">網站和內容</span><span class="sxs-lookup"><span data-stu-id="cd252-186">Sites and content</span></span>  <br/> |<span data-ttu-id="cd252-187">網站和內容都可以在復原環境。</span><span class="sxs-lookup"><span data-stu-id="cd252-187">Sites and content are available in the recovery environment.</span></span>  <br/> |
|<span data-ttu-id="cd252-188">搜尋的新執行個體</span><span class="sxs-lookup"><span data-stu-id="cd252-188">A new instance of search</span></span>  <br/> |<span data-ttu-id="cd252-p112">此暖待命解決方案，不會從搜尋資料庫還原搜尋。復原伺服器陣列中的搜尋元件設定為 [同樣盡可能實際執行伺服器陣列。還原網站與內容之後，搜尋索引重建啟動完整編目。您不需要等候完成提供網站及內容編目。</span><span class="sxs-lookup"><span data-stu-id="cd252-p112">In this warm standby solution, search is not restored from search databases. Search components in the recovery farm are configured as similarly as possible to the production farm. After the sites and content are restored, a full crawl is started to rebuild the search index. You do not need to wait for the crawl to complete to make the sites and content available.</span></span>  <br/> |
|<span data-ttu-id="cd252-193">服務</span><span class="sxs-lookup"><span data-stu-id="cd252-193">Services</span></span>  <br/> | <span data-ttu-id="cd252-p113">從記錄傳送資料庫還原資料儲存在資料庫的服務。只被啟動請勿在資料庫中儲存資料的服務。</span><span class="sxs-lookup"><span data-stu-id="cd252-p113">Services that store data in databases are restored from the log-shipped databases. Services that do not store data in databases are simply started.</span></span> <br/>  <span data-ttu-id="cd252-p114">並非所有的服務與資料庫必須還原。下列服務不必從資料庫還原並只可啟動容錯移轉後：</span><span class="sxs-lookup"><span data-stu-id="cd252-p114">Not all services with databases need to be restored. The following services do not need to be restored from databases and can simply be started after failover:</span></span> <br/>  <span data-ttu-id="cd252-198">Usage and Health Data Collection</span><span class="sxs-lookup"><span data-stu-id="cd252-198">Usage and Health Data Collection</span></span> <br/>  <span data-ttu-id="cd252-199">State Service</span><span class="sxs-lookup"><span data-stu-id="cd252-199">State service</span></span> <br/>  <span data-ttu-id="cd252-200">Word automation</span><span class="sxs-lookup"><span data-stu-id="cd252-200">Word automation</span></span> <br/>  <span data-ttu-id="cd252-201">不會使用資料庫的任何其他服務</span><span class="sxs-lookup"><span data-stu-id="cd252-201">Any other service that doesn't use a database</span></span> <br/> |
   
<span data-ttu-id="cd252-p115">您可以使用 Microsoft 諮詢服務 (ATL-MCS-001) 或協力廠商工具來處理更複雜復原目標。下表摘要說明這些。</span><span class="sxs-lookup"><span data-stu-id="cd252-p115">You can work with Microsoft Consulting Services (MCS) or a partner to address more-complex recovery objectives. These are summarized in the following table.</span></span>
  
<span data-ttu-id="cd252-204">**表格： 其他項目可以定址的 ATL-MCS-001 或協力廠商**</span><span class="sxs-lookup"><span data-stu-id="cd252-204">**Table: Other items that can be addressed by MCS or a partner**</span></span>

|<span data-ttu-id="cd252-205">**項目**</span><span class="sxs-lookup"><span data-stu-id="cd252-205">**Item**</span></span>|<span data-ttu-id="cd252-206">**描述**</span><span class="sxs-lookup"><span data-stu-id="cd252-206">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="cd252-207">同步處理自訂伺服器陣列方案</span><span class="sxs-lookup"><span data-stu-id="cd252-207">Synchronizing custom farm solutions</span></span>  <br/> |<span data-ttu-id="cd252-p116">理想狀況下，復原伺服器陣列設定為與實際執行伺服器陣列相同。您可以使用顧問或協力廠商用來評估已複寫自訂伺服器陣列方案以及是否為位置保持同步的兩個環境的程序。</span><span class="sxs-lookup"><span data-stu-id="cd252-p116">Ideally, the recovery farm configuration is identical to the production farm. You can work with a consultant or partner to evaluate whether custom farm solutions are replicated and whether the process is in place for keeping the two environments synchronized.</span></span>  <br/> |
|<span data-ttu-id="cd252-210">連線至資料來源內部</span><span class="sxs-lookup"><span data-stu-id="cd252-210">Connections to data sources on-premises</span></span>  <br/> |<span data-ttu-id="cd252-211">它可能不是實際複寫至後端資料系統，如備份網域控制站 (BDC) 連線及搜尋內容來源的連線。</span><span class="sxs-lookup"><span data-stu-id="cd252-211">It might not be practical to replicate connections to back-end data systems, such as backup domain controller (BDC) connections and search content sources.</span></span>  <br/> |
|<span data-ttu-id="cd252-212">搜尋還原案例</span><span class="sxs-lookup"><span data-stu-id="cd252-212">Search restore scenarios</span></span>  <br/> |<span data-ttu-id="cd252-p117">企業搜尋部署往往許多唯一和複雜，因為還原搜尋資料庫需要更大的投資。您可以使用識別及實作您的組織可能需要的搜尋還原案例 （英文） 或協力廠商。</span><span class="sxs-lookup"><span data-stu-id="cd252-p117">Because enterprise search deployments tend to be fairly unique and complex, restoring search from databases requires a greater investment. You can work with a consultant or partner to identify and implement search restore scenarios that your organization might require.</span></span>  <br/> |
   
<span data-ttu-id="cd252-215">本文中提供的指導假設內部部署伺服器陣列已設計及部署。</span><span class="sxs-lookup"><span data-stu-id="cd252-215">The guidance provided in this article assumes that the on-premises farm is already designed and deployed.</span></span>
  
## <a name="detailed-architecture"></a><span data-ttu-id="cd252-216">詳細架構</span><span class="sxs-lookup"><span data-stu-id="cd252-216">Detailed architecture</span></span>

<span data-ttu-id="cd252-217">理想狀況下，在 Azure 中的復原伺服器陣列設定為實際執行伺服器陣列上部署，包括下列與相同：</span><span class="sxs-lookup"><span data-stu-id="cd252-217">Ideally, the recovery farm configuration in Azure is identical to the production farm on-premises, including the following:</span></span>
  
- <span data-ttu-id="cd252-218">伺服器角色相同的表示法</span><span class="sxs-lookup"><span data-stu-id="cd252-218">The same representation of server roles</span></span>
    
- <span data-ttu-id="cd252-219">相同的設定的自訂項目</span><span class="sxs-lookup"><span data-stu-id="cd252-219">The same configuration of customizations</span></span>
    
- <span data-ttu-id="cd252-220">搜尋元件的相同的設定</span><span class="sxs-lookup"><span data-stu-id="cd252-220">The same configuration of search components</span></span>
    
<span data-ttu-id="cd252-p118">在 Azure 環境可以是實際執行伺服器陣列較小版本。如果您打算容錯移轉後的向外延展的復原伺服器陣列，務必要最初代表每一種伺服器角色。</span><span class="sxs-lookup"><span data-stu-id="cd252-p118">The environment in Azure can be a smaller version of the production farm. If you plan to scale out the recovery farm after failover, it's important that each type of server role be initially represented.</span></span>
  
<span data-ttu-id="cd252-p119">某些組態中可能不是實際複寫容錯移轉環境中。請務必測試容錯移轉程序和環境以協助確保容錯移轉伺服器陣列提供預期的服務層級。</span><span class="sxs-lookup"><span data-stu-id="cd252-p119">Some configurations might not be practical to replicate in the failover environment. Be sure to test the failover procedures and environment to help ensure that the failover farm provides the expected service level.</span></span>
  
<span data-ttu-id="cd252-p120">此解決方案不擬定特定拓撲的 SharePoint 伺服器陣列。此解決方案的重點是使用 Azure 容錯移轉伺服器陣列並實作記錄傳送和 DFSR 兩個環境之間。</span><span class="sxs-lookup"><span data-stu-id="cd252-p120">This solution doesn't prescribe a specific topology for a SharePoint farm. The focus of this solution is to use Azure for the failover farm and to implement log shipping and DFSR between the two environments.</span></span>
  
### <a name="warm-standby-environments"></a><span data-ttu-id="cd252-227">暖待命環境</span><span class="sxs-lookup"><span data-stu-id="cd252-227">Warm standby environments</span></span>

<span data-ttu-id="cd252-p121">在暖待命環境中，執行 Azure 環境中的所有虛擬機器。環境已備妥可供容錯移轉練習或事件。</span><span class="sxs-lookup"><span data-stu-id="cd252-p121">In a warm standby environment, all virtual machines in the Azure environment are running. The environment is ready for a failover exercise or event.</span></span>
  
<span data-ttu-id="cd252-230">下圖說明從內部部署 SharePoint 伺服器陣列至 Azure 型 SharePoint 伺服器陣列設定為暖待命環境的災害復原解決方案。</span><span class="sxs-lookup"><span data-stu-id="cd252-230">The following figure illustrates a disaster recovery solution from an on-premises SharePoint farm to an Azure-based SharePoint farm that is configured as a warm standby environment.</span></span>
  
<span data-ttu-id="cd252-231">**圖： 拓撲和實際執行伺服器陣列及暖待命復原伺服器陣列的主要元素**</span><span class="sxs-lookup"><span data-stu-id="cd252-231">**Figure: Topology and key elements of a production farm and a warm standby recovery farm**</span></span>

![在 SharePoint 伺服器陣列及暖待命復原伺服器陣列的拓撲](media/AZarch-AZWarmStndby.png)
  
<span data-ttu-id="cd252-233">在此圖表中：</span><span class="sxs-lookup"><span data-stu-id="cd252-233">In this diagram:</span></span>
  
- <span data-ttu-id="cd252-234">並排說明兩個環境： 內部部署 SharePoint 伺服器陣列和 Azure 中的暖待命伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="cd252-234">Two environments are illustrated side by side: the on-premises SharePoint farm and the warm standby farm in Azure.</span></span>
    
- <span data-ttu-id="cd252-235">每個環境都包括檔案共用。</span><span class="sxs-lookup"><span data-stu-id="cd252-235">Each environment includes a file share.</span></span>
    
- <span data-ttu-id="cd252-p122">每個伺服器陣列包含四個層。若要達到高可用性，每一層包含兩個伺服器或針對特定角色，例如前端服務、 分散式快取、 後端伺服器的服務，以及資料庫進行完全相同設定的虛擬機器。未在此圖中以圖說文字特定元件的重要。設定兩個伺服器陣列進行完全相同。</span><span class="sxs-lookup"><span data-stu-id="cd252-p122">Each farm includes four tiers. To achieve high availability, each tier includes two servers or virtual machines that are configured identically for a specific role, such as front-end services, distributed cache, back-end services, and databases. It isn't important in this illustration to call out specific components. The two farms are configured identically.</span></span>
    
- <span data-ttu-id="cd252-p123">第四層是資料庫層。記錄傳送用來將記錄從內部部署環境中的次要資料庫伺服器複製至相同的環境中的檔案共用。</span><span class="sxs-lookup"><span data-stu-id="cd252-p123">The fourth tier is the database tier. Log shipping is used to copy logs from the secondary database server in the on-premises environment to the file share in the same environment.</span></span>
    
- <span data-ttu-id="cd252-242">DFSR 會將檔案從內部部署環境中的檔案共用複製至 Azure 環境中的檔案共用。</span><span class="sxs-lookup"><span data-stu-id="cd252-242">DFSR copies files from the file share in the on-premises environment to the file share in the Azure environment.</span></span>
    
- <span data-ttu-id="cd252-243">記錄傳送會將記錄從 Azure 環境中的檔案共用重新執行至復原環境的 SQL Server AlwaysOn 可用性群組中的主要複本。</span><span class="sxs-lookup"><span data-stu-id="cd252-243">Log shipping replays the logs from the file share in the Azure environment to the primary replica in the SQL Server AlwaysOn availability group in the recovery environment.</span></span>
    
### <a name="cold-standby-environments"></a><span data-ttu-id="cd252-244">冷待命環境</span><span class="sxs-lookup"><span data-stu-id="cd252-244">Cold standby environments</span></span>

<span data-ttu-id="cd252-p124">在冷待命環境中，大部分的 SharePoint 伺服器陣列虛擬機器可以為關閉。（建議有時會啟動虛擬機器，例如每兩週或一個月一次使每部虛擬機器可以與網域同步處理。）Azure 復原環境中的下列虛擬機器必須保持執行以協助確保記錄傳送和 DFSR 連續作業：</span><span class="sxs-lookup"><span data-stu-id="cd252-p124">In a cold standby environment, most of the SharePoint farm virtual machines can be shut down. (We recommend occasionally starting the virtual machines, such as every two weeks or once a month, so that each virtual machine can sync with the domain.) The following virtual machines in the Azure recovery environment must remain running to help ensure continuous operations of log shipping and DFSR:</span></span>
  
- <span data-ttu-id="cd252-247">檔案共用</span><span class="sxs-lookup"><span data-stu-id="cd252-247">The file share</span></span>
    
- <span data-ttu-id="cd252-248">主要的資料庫伺服器</span><span class="sxs-lookup"><span data-stu-id="cd252-248">The primary database server</span></span>
    
- <span data-ttu-id="cd252-249">至少一個執行 Windows Server Active Directory 網域服務與 DNS 的虛擬機器</span><span class="sxs-lookup"><span data-stu-id="cd252-249">At least one virtual machine running Windows Server Active Directory Domain Services and DNS</span></span>
    
<span data-ttu-id="cd252-p125">下圖顯示 Azure 容錯移轉環境中執行檔案共用虛擬機器和主要的 SharePoint 資料庫虛擬機器。所有其他 SharePoint 虛擬機器已停止。Windows Server Active Directory 和 DNS 執行的虛擬機器時不會顯示。</span><span class="sxs-lookup"><span data-stu-id="cd252-p125">The following figure shows an Azure failover environment in which the file share virtual machine and the primary SharePoint database virtual machine are running. All other SharePoint virtual machines are stopped. The virtual machine that is running Windows Server Active Directory and DNS is not shown.</span></span>
  
<span data-ttu-id="cd252-253">**圖： 使用虛擬機器中執行的冷待命復原伺服器陣列**</span><span class="sxs-lookup"><span data-stu-id="cd252-253">**Figure: Cold standby recovery farm with running virtual machines**</span></span>

![Azure 中 SharePoint 冷待命解決方案的元素](media/AZarch-AZColdStndby.png)
  
<span data-ttu-id="cd252-255">容錯移轉之後冷待命環境中，所有虛擬機器已都啟用，且方法，以達到高可用性的資料庫伺服器必須設定，例如 SQL Server AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="cd252-255">After failover to a cold standby environment, all virtual machines are started, and the method to achieve high availability of the database servers must be configured, such as SQL Server AlwaysOn availability groups.</span></span>
  
<span data-ttu-id="cd252-256">如果已實作多個儲存群組 （資料庫遍佈多個 SQL Server 高可用性設定），每個儲存群組的主要資料庫必須執行接受其儲存群組相關聯的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="cd252-256">If multiple storage groups are implemented (databases are spread across more than one SQL Server high availability set), the primary database for each storage group must be running to accept the logs associated with its storage group.</span></span>
  
### <a name="skills-and-experience"></a><span data-ttu-id="cd252-257">技能與經驗</span><span class="sxs-lookup"><span data-stu-id="cd252-257">Skills and experience</span></span>

<span data-ttu-id="cd252-p126">此嚴重損壞復原解決方案使用多個技術。為了協助確保這些技術互動如預期般運作，必須安裝並已正確設定內部部署和 Azure 環境中的每個元件。建議的人員或小組會設定此解決方案的強式使用知識與實機操作技巧與下列文章所述的技術：</span><span class="sxs-lookup"><span data-stu-id="cd252-p126">Multiple technologies are used in this disaster recovery solution. To help ensure that these technologies interact as expected, each component in the on-premises and Azure environment must be installed and configured correctly. We recommend that the person or team who sets up this solution have a strong working knowledge of and hands-on skills with the technologies described in the following articles:</span></span>
  
- [<span data-ttu-id="cd252-261">分散式的檔案系統 (DFS) 複寫服務</span><span class="sxs-lookup"><span data-stu-id="cd252-261">Distributed File System (DFS) Replication Services</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392698)
    
- [<span data-ttu-id="cd252-262">Windows Server 容錯移轉叢集 (WSFC) 與 SQL Server</span><span class="sxs-lookup"><span data-stu-id="cd252-262">Windows Server Failover Clustering (WSFC) with SQL Server</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392701)
    
- [<span data-ttu-id="cd252-263">AlwaysOn 可用性群組 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="cd252-263">AlwaysOn Availability Groups (SQL Server)</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392725)
    
- [<span data-ttu-id="cd252-264">備份及還原的 SQL Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="cd252-264">Back Up and Restore of SQL Server Databases</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392728)
    
- [<span data-ttu-id="cd252-265">SharePoint Server 2013 的安裝與伺服器陣列部署</span><span class="sxs-lookup"><span data-stu-id="cd252-265">SharePoint Server 2013 installation and farm deployment</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=393119)
    
- [<span data-ttu-id="cd252-266">Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="cd252-266">Microsoft Azure</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392729)
    
<span data-ttu-id="cd252-p127">最後，我們建議指令碼可用來自動化工作與這些技術相關聯的技巧。有可能使用可用的使用者介面完成此解決方案所述的所有工作。不過，手動方法時間取用及出錯可與提供一致的結果。</span><span class="sxs-lookup"><span data-stu-id="cd252-p127">Finally, we recommend scripting skills that you can use to automate tasks associated with these technologies. It's possible to use the available user interfaces to complete all the tasks described in this solution. However, a manual approach can be time consuming and error prone and delivers inconsistent results.</span></span>
  
<span data-ttu-id="cd252-p128">除了 Windows PowerShell 中也有 SQL Server、 SharePoint Server 及 Azure 的 Windows PowerShell 文件庫。記得 T-SQL，這也有助於減少設定及維護嚴重損壞修復環境的時間。</span><span class="sxs-lookup"><span data-stu-id="cd252-p128">In addition to Windows PowerShell, there are also Windows PowerShell libraries for SQL Server, SharePoint Server, and Azure. Don't forget T-SQL, which can also help reduce the time to configure and maintain your disaster-recovery environment.</span></span>
  
## <a name="disaster-recovery-roadmap"></a><span data-ttu-id="cd252-272">嚴重損壞復原藍圖</span><span class="sxs-lookup"><span data-stu-id="cd252-272">Disaster recovery roadmap</span></span>

![SharePoint 嚴重損壞修復藍圖的視覺表示法。](media/Azure-DRroadmap.png)
  
<span data-ttu-id="cd252-274">此藍圖假設您已在生產環境中部署的 SharePoint Server 2013 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="cd252-274">This roadmap assumes that you already have a SharePoint Server 2013 farm deployed in production.</span></span>
  
<span data-ttu-id="cd252-275">**表格： 藍圖嚴重損壞修復**</span><span class="sxs-lookup"><span data-stu-id="cd252-275">**Table: Roadmap for disaster recovery**</span></span>

|<span data-ttu-id="cd252-276">**階段**</span><span class="sxs-lookup"><span data-stu-id="cd252-276">**Phase**</span></span>|<span data-ttu-id="cd252-277">**描述**</span><span class="sxs-lookup"><span data-stu-id="cd252-277">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="cd252-278">階段 1</span><span class="sxs-lookup"><span data-stu-id="cd252-278">Phase 1</span></span>  <br/> |<span data-ttu-id="cd252-279">設計嚴重損壞修復環境。</span><span class="sxs-lookup"><span data-stu-id="cd252-279">Design the disaster recovery environment.</span></span>  <br/> |
|<span data-ttu-id="cd252-280">階段 2</span><span class="sxs-lookup"><span data-stu-id="cd252-280">Phase 2</span></span>  <br/> |<span data-ttu-id="cd252-281">建立 Azure 虛擬網路和 VPN 連線。</span><span class="sxs-lookup"><span data-stu-id="cd252-281">Create the Azure virtual network and VPN connection.</span></span>  <br/> |
|<span data-ttu-id="cd252-282">階段 3</span><span class="sxs-lookup"><span data-stu-id="cd252-282">Phase 3</span></span>  <br/> |<span data-ttu-id="cd252-283">Azure 虛擬網路中部署 Windows Active Directory 及網域名稱服務。</span><span class="sxs-lookup"><span data-stu-id="cd252-283">Deploy Windows Active Directory and Domain Name Services to the Azure virtual network.</span></span>  <br/> |
|<span data-ttu-id="cd252-284">階段 4</span><span class="sxs-lookup"><span data-stu-id="cd252-284">Phase 4</span></span>  <br/> |<span data-ttu-id="cd252-285">部署在 Azure 中的 SharePoint 復原伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="cd252-285">Deploy the SharePoint recovery farm in Azure.</span></span>  <br/> |
|<span data-ttu-id="cd252-286">第 5 階段</span><span class="sxs-lookup"><span data-stu-id="cd252-286">Phase 5</span></span>  <br/> |<span data-ttu-id="cd252-287">設定伺服器陣列之間的 DFSR。</span><span class="sxs-lookup"><span data-stu-id="cd252-287">Set up DFSR between the farms.</span></span>  <br/> |
|<span data-ttu-id="cd252-288">階段 6</span><span class="sxs-lookup"><span data-stu-id="cd252-288">Phase 6</span></span>  <br/> |<span data-ttu-id="cd252-289">設定記錄傳送至修復伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="cd252-289">Set up log shipping to the recovery farm.</span></span>  <br/> |
|<span data-ttu-id="cd252-290">第 7 階段</span><span class="sxs-lookup"><span data-stu-id="cd252-290">Phase 7</span></span>  <br/> | <span data-ttu-id="cd252-p129">驗證容錯移轉和復原解決方案。這包括下列程序和技術：</span><span class="sxs-lookup"><span data-stu-id="cd252-p129">Validate failover and recovery solutions. This includes the following procedures and technologies:</span></span> <br/>  <span data-ttu-id="cd252-293">停止記錄傳送。</span><span class="sxs-lookup"><span data-stu-id="cd252-293">Stop log shipping.</span></span> <br/>  <span data-ttu-id="cd252-294">將備份還原。</span><span class="sxs-lookup"><span data-stu-id="cd252-294">Restore the backups.</span></span> <br/>  <span data-ttu-id="cd252-295">內容編目時間。</span><span class="sxs-lookup"><span data-stu-id="cd252-295">Crawl content.</span></span> <br/>  <span data-ttu-id="cd252-296">復原服務。</span><span class="sxs-lookup"><span data-stu-id="cd252-296">Recover services.</span></span> <br/>  <span data-ttu-id="cd252-297">管理 DNS 記錄。</span><span class="sxs-lookup"><span data-stu-id="cd252-297">Manage DNS records.</span></span> <br/> |
   
## <a name="phase-1-design-the-disaster-recovery-environment"></a><span data-ttu-id="cd252-298">階段 1： 設計嚴重損壞修復環境</span><span class="sxs-lookup"><span data-stu-id="cd252-298">Phase 1: Design the disaster recovery environment</span></span>

<span data-ttu-id="cd252-p130">若要設計嚴重損壞修復環境，包括 SharePoint 復原伺服器陣列中使用[Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)中的指導。您可以使用[Azure 中的 SharePoint 災害復原解決方案](https://go.microsoft.com/fwlink/p/?LinkId=392554)Visio 檔案中的圖形開始設計程序。我們建議您在開始 Azure 環境中的任何工作之前設計整個環境。</span><span class="sxs-lookup"><span data-stu-id="cd252-p130">Use the guidance in [Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) to design the disaster-recovery environment, including the SharePoint recovery farm. You can use the graphics in the [SharePoint Disaster Recovery Solution in Azure](https://go.microsoft.com/fwlink/p/?LinkId=392554) Visio file to start the design process. We recommend that you design the entire environment before beginning any work in the Azure environment.</span></span>
  
<span data-ttu-id="cd252-302">除了[Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)設計虛擬網路、 VPN 連線、 Active Directory 及 SharePoint 伺服器陣列所提供的指導，請務必將檔案共用角色新增至 Azure 環境。</span><span class="sxs-lookup"><span data-stu-id="cd252-302">In addition to the guidance provided in [Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) for designing the virtual network, VPN connection, Active Directory, and SharePoint farm, be sure to add a file share role to the Azure environment.</span></span>
  
<span data-ttu-id="cd252-p131">若要支援記錄傳送的嚴重損壞修復解決方案，檔案共用虛擬機器新增至所在的資料庫角色的子網路。檔案共用也做為 SQL Server AlwaysOn 可用性群組的節點多數 」 的第三個節點。這是建議使用 SQL Server AlwaysOn 可用性群組的標準 SharePoint 伺服器陣列的設定。</span><span class="sxs-lookup"><span data-stu-id="cd252-p131">To support log shipping in a disaster-recovery solution, a file share virtual machine is added to the subnet where the database roles reside. The file share also serves as the third node of a Node Majority for the SQL Server AlwaysOn availability group. This is the recommended configuration for a standard SharePoint farm that uses SQL Server AlwaysOn availability groups.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="cd252-p132">請務必檢閱資料庫以參與的 SQL Server AlwaysOn 可用性群組的必要條件。如需詳細資訊，請參閱[必要條件、 限制和 Recommendations for AlwaysOn Availability Groups](https://go.microsoft.com/fwlink/p/?LinkId=510870)。</span><span class="sxs-lookup"><span data-stu-id="cd252-p132">It is important to review the prerequisites for a database to participate in a SQL Server AlwaysOn availability group. For more information, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups](https://go.microsoft.com/fwlink/p/?LinkId=510870).</span></span> 
  
<span data-ttu-id="cd252-308">**圖： 位置的嚴重損壞復原解決方案所使用的檔案伺服器**</span><span class="sxs-lookup"><span data-stu-id="cd252-308">**Figure: Placement of a file server used for a disaster recovery solution**</span></span>

![顯示新增至含有 SharePoint 資料庫伺服器角色之相同雲端服務的檔案共用 VM。](media/AZenv-FSforDFSRandWSFC.png)
  
<span data-ttu-id="cd252-p133">在此圖表、 檔案共用虛擬機器新增至包含資料庫伺服器角色的 Azure 中相同的子網路。請勿加檔案共用虛擬機器設定與其他伺服器角色，例如 SQL Server 角色的可用性。</span><span class="sxs-lookup"><span data-stu-id="cd252-p133">In this diagram, a file share virtual machine is added to the same subnet in Azure that contains the database server roles. Do not add the file share virtual machine to an availability set with other server roles, such as the SQL Server roles.</span></span>
  
<span data-ttu-id="cd252-p134">如果您擔心記錄檔的高可用性，請考慮使用[SQL Server 備份與還原 Azure Blob Storage service](https://go.microsoft.com/fwlink/p/?LinkId=393113)考慮以不同的方法。這是記錄檔會直接儲存到 blob 存放區 URL 的 Azure 中的新功能。此解決方案不包括使用這項功能的相關指引。</span><span class="sxs-lookup"><span data-stu-id="cd252-p134">If you are concerned about the high availability of the logs, consider taking a different approach by using [SQL Server backup and restore with Azure Blob Storage Service](https://go.microsoft.com/fwlink/p/?LinkId=393113). This is a new feature in Azure that saves logs directly to a blob storage URL. This solution does not include guidance about using this feature.</span></span>
  
<span data-ttu-id="cd252-p135">當您設計的復原伺服器陣列時，請記住，成功損毀修復環境正確地反映實際執行伺服器陣列要復原。復原伺服器陣列的大小不是最重要的是在復原伺服器陣列的設計、 部署及測試。伺服器陣列規模而異從組織根據業務需求的組織。它可能會出現短暫的中斷或效能和容量需求需要擴充伺服器陣列之前使用劍橋伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="cd252-p135">When you design the recovery farm, keep in mind that a successful disaster recovery environment accurately reflects the production farm that you want to recover. The size of the recovery farm is not the most important thing in the recovery farm's design, deployment, and testing. Farm scale varies from organization to organization based on business requirements. It might be possible to use a scaled-down farm for a short outage or until performance and capacity demands require you to scale the farm.</span></span>
  
<span data-ttu-id="cd252-p136">設定復原伺服器陣列至實際執行伺服器陣列盡可能同名使其符合您的服務層次協議 (SLA) 需求並提供您需要以支援您的業務的功能。當您設計嚴重損壞修復環境時，也查看您的變更管理程序的實際執行環境。我們建議您擴充至復原環境的變更管理程序來更新在相同的時間間隔的復原環境與實際執行環境。變更管理程序的一部分，建議您維護伺服器陣列設定、 應用程式和使用者的詳細的清查。</span><span class="sxs-lookup"><span data-stu-id="cd252-p136">Configure the recovery farm as identically as possible to the production farm so that it meets your service level agreement (SLA) requirements and provides the functionality that you need to support your business. When you design the disaster recovery environment, also look at your change management process for your production environment. We recommend that you extend the change management process to the recovery environment by updating the recovery environment at the same interval as the production environment. As part of the change management process, we recommend maintaining a detailed inventory of your farm configuration, applications, and users.</span></span> 
  
## <a name="phase-2-create-the-azure-virtual-network-and-vpn-connection"></a><span data-ttu-id="cd252-323">階段 2： 建立 Azure 虛擬網路和 VPN 連線</span><span class="sxs-lookup"><span data-stu-id="cd252-323">Phase 2: Create the Azure virtual network and VPN connection</span></span>

<span data-ttu-id="cd252-p137">[Microsoft Azure 虛擬網路的連線與內部網路](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)教您如何規劃及部署在 Azure 虛擬網路以及如何建立 VPN 連線。請遵循，才可完成下列程序主題中的指引：</span><span class="sxs-lookup"><span data-stu-id="cd252-p137">[Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md) shows you how to plan and deploy the virtual network in Azure and how to create the VPN connection. Follow the guidance in the topic to complete the following procedures:</span></span>
  
- <span data-ttu-id="cd252-326">規劃虛擬網路的私人 IP 位址空間。</span><span class="sxs-lookup"><span data-stu-id="cd252-326">Plan the private IP address space of the Virtual Network.</span></span>
    
- <span data-ttu-id="cd252-327">規劃虛擬網路的路由的基礎結構變更。</span><span class="sxs-lookup"><span data-stu-id="cd252-327">Plan the routing infrastructure changes for the Virtual Network.</span></span>
    
- <span data-ttu-id="cd252-328">規劃內部部署 VPN 裝置的流量的防火牆規則。</span><span class="sxs-lookup"><span data-stu-id="cd252-328">Plan firewall rules for traffic to and from the on-premises VPN device.</span></span>
    
- <span data-ttu-id="cd252-329">在 Azure 中建立跨內部虛擬網路。</span><span class="sxs-lookup"><span data-stu-id="cd252-329">Create the cross-premises virtual network in Azure.</span></span>
    
- <span data-ttu-id="cd252-330">設定您的內部網路和虛擬網路間的路由。</span><span class="sxs-lookup"><span data-stu-id="cd252-330">Configure routing between your on-premises network and the Virtual Network.</span></span>
    
## <a name="phase-3-deploy-active-directory-and-domain-name-services-to-the-azure-virtual-network"></a><span data-ttu-id="cd252-331">階段 3： 部署 Active Directory 及網域名稱服務以 Azure 虛擬網路</span><span class="sxs-lookup"><span data-stu-id="cd252-331">Phase 3: Deploy Active Directory and Domain Name Services to the Azure virtual network</span></span>

<span data-ttu-id="cd252-332">此階段包括部署 Windows Server Active Directory 和 DNS 中混合式案例的虛擬網路和[Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)中所述，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="cd252-332">This phase includes deploying both Windows Server Active Directory and DNS to the Virtual Network in a hybrid scenario as described in [Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) and as illustrated in the following figure.</span></span>
  
<span data-ttu-id="cd252-333">**圖： 混合式 Active Directory 網域組態**</span><span class="sxs-lookup"><span data-stu-id="cd252-333">**Figure: Hybrid Active Directory domain configuration**</span></span>

![STwo 虛擬機器部署到 Azure 虛擬網路和 SharePoint 伺服器陣列子網路是複本網域控制站和 DNS 伺服器](media/AZarch-HyADdomainConfig.png)
  
<span data-ttu-id="cd252-p138">在圖中，兩個虛擬機器部署至相同的子網路。這些虛擬機器時的每個主控的兩種角色： Active Directory 和 DNS。</span><span class="sxs-lookup"><span data-stu-id="cd252-p138">In the illustration, two virtual machines are deployed to the same subnet. These virtual machines are each hosting two roles: Active Directory and DNS.</span></span>
  
<span data-ttu-id="cd252-p139">部署在 Azure 中的 Active Directory 之前，先閱讀[部署 Windows Server Active directory Azure 虛擬機器上的指導方針](https://go.microsoft.com/fwlink/p/?linkid=392681)。這些指導方針可協助您決定您是否需要不同的架構或不同的組態設定的解決方案。</span><span class="sxs-lookup"><span data-stu-id="cd252-p139">Before deploying Active Directory in Azure, read [Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines](https://go.microsoft.com/fwlink/p/?linkid=392681). These guidelines help you determine whether you need a different architecture or different configuration settings for your solution.</span></span>
  
<span data-ttu-id="cd252-339">如需詳細指導設定 Azure 中的網域控制站的詳細資訊，請參閱[安裝複本 Active Directory 網域控制站在 Azure 虛擬網路](https://go.microsoft.com/fwlink/p/?LinkId=392687)。</span><span class="sxs-lookup"><span data-stu-id="cd252-339">For detailed guidance on setting up a domain controller in Azure, see [Install a Replica Active Directory Domain Controller in Azure Virtual Networks](https://go.microsoft.com/fwlink/p/?LinkId=392687).</span></span>
  
<span data-ttu-id="cd252-p140">此階段中之前, 沒有將虛擬機器部署至虛擬網路。虛擬機器架設 Active Directory 和 DNS 不可能是最大的虛擬機器所需的解決方案。您將這些虛擬機器的部署之前，請先建立想要使用虛擬網路的最大虛擬機器。這有助於確保您的解決方案落在可讓您需要的最大大小的 Azure 中的標籤。您不需要在此時間設定此虛擬機器。只需建立，而使用它。如果不這麼做，您可能會執行到當您嘗試更新版本、 建立較大的虛擬機器時的限制這在本文撰寫時的問題。</span><span class="sxs-lookup"><span data-stu-id="cd252-p140">Before this phase, you didn't deploy virtual machines to the Virtual Network. The virtual machines for hosting Active Directory and DNS are likely not the largest virtual machines you need for the solution. Before you deploy these virtual machines, first create the largest virtual machine that you plan to use in your Virtual Network. This helps ensure that your solution lands on a tag in Azure that allows the largest size you need. You do not need to configure this virtual machine at this time. Simply create it, and set it aside. If you do not do this, you might run into a limitation when you try to create larger virtual machines later, which was an issue at the time this article was written.</span></span> 
  
## <a name="phase-4-deploy-the-sharepoint-recovery-farm-in-azure"></a><span data-ttu-id="cd252-347">階段 4： 部署在 Azure 中的 SharePoint 復原伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="cd252-347">Phase 4: Deploy the SharePoint recovery farm in Azure</span></span>

<span data-ttu-id="cd252-p141">部署 SharePoint 伺服器陣列的虛擬網路根據您的設計計劃。可能是部署在 Azure 中的 SharePoint 角色之前，先檢閱[Planning for SharePoint 2013 在 Azure 基礎結構服務上](https://go.microsoft.com/fwlink/p/?LinkId=400984)幫助。</span><span class="sxs-lookup"><span data-stu-id="cd252-p141">Deploy the SharePoint farm in your Virtual Network according to your design plans. It might be helpful to review [Planning for SharePoint 2013 on Azure Infrastructure Services](https://go.microsoft.com/fwlink/p/?LinkId=400984) before you deploy SharePoint roles in Azure.</span></span>
  
<span data-ttu-id="cd252-350">請考慮下列我們所建置我們證明概念環境學到的作法：</span><span class="sxs-lookup"><span data-stu-id="cd252-350">Consider the following practices that we learned by building our proof of concept environment:</span></span>
  
- <span data-ttu-id="cd252-351">使用 Azure 入口網站或 PowerShell 建立虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="cd252-351">Create virtual machines by using the Azure portal or PowerShell.</span></span>
    
- <span data-ttu-id="cd252-p142">Azure 和 HYPER-V 不支援動態記憶體。請確定此納入效能與容量計劃。</span><span class="sxs-lookup"><span data-stu-id="cd252-p142">Azure and Hyper-V do not support dynamic memory. Be sure this is factored into your performance and capacity plans.</span></span>
    
- <span data-ttu-id="cd252-p143">重新啟動虛擬機器透過 Azure 介面，不會從虛擬機器登入本身擷取。使用 Azure 介面更妥善地運作且更容易預測。</span><span class="sxs-lookup"><span data-stu-id="cd252-p143">Restart virtual machines through the Azure interface, not from the virtual machine logon itself. Using the Azure interface works better and is more predictable.</span></span>
    
- <span data-ttu-id="cd252-p144">如果您想要關閉虛擬機器儲存成本，使用 Azure 介面。如果您關閉從虛擬機器登入、 費繼續累。</span><span class="sxs-lookup"><span data-stu-id="cd252-p144">If you want to shut down a virtual machine to save costs, use the Azure interface. If you shut down from the virtual machine logon, charges continue to accrue.</span></span>
    
- <span data-ttu-id="cd252-358">使用虛擬機器的命名慣例。</span><span class="sxs-lookup"><span data-stu-id="cd252-358">Use a naming convention for the virtual machines.</span></span>
    
- <span data-ttu-id="cd252-359">請的注意到哪一個資料中心位置部署虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="cd252-359">Pay attention to which datacenter location the virtual machines are being deployed.</span></span>
    
- <span data-ttu-id="cd252-360">SharePoint 角色不支援在 Azure 中的自動縮放比例功能。</span><span class="sxs-lookup"><span data-stu-id="cd252-360">The automatic scaling feature in Azure is not supported for SharePoint roles.</span></span>
    
- <span data-ttu-id="cd252-361">請勿將會還原，例如網站集合之伺服器陣列中設定的項目。</span><span class="sxs-lookup"><span data-stu-id="cd252-361">Do not configure items in the farm that will be restored, such as site collections.</span></span> 
    
## <a name="phase-5-set-up-dfsr-between-the-farms"></a><span data-ttu-id="cd252-362">階段 5： 設定伺服器陣列之間 DFSR</span><span class="sxs-lookup"><span data-stu-id="cd252-362">Phase 5: Set up DFSR between the farms</span></span>

<span data-ttu-id="cd252-p145">若要使用 DFSR 設定檔複寫，使用 [DNS 管理] 嵌入式管理單元。不過，DFSR 安裝程式之前登入您的內部部署檔案伺服器和 Azure 檔案伺服器並啟用 Windows 中的服務。</span><span class="sxs-lookup"><span data-stu-id="cd252-p145">To set up file replication by using DFSR, use the DNS Management snap-in. However, before the DFSR setup, log on to your on-premises file server and Azure file server and enable the service in Windows.</span></span>
  
<span data-ttu-id="cd252-365">從 [伺服器管理員儀表板中，完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="cd252-365">From the Server Manager Dashboard, complete the following steps:</span></span>
  
- <span data-ttu-id="cd252-366">設定本機伺服器。</span><span class="sxs-lookup"><span data-stu-id="cd252-366">Configure the local server.</span></span>
    
- <span data-ttu-id="cd252-367">啟動 [**新增角色及功能精靈]**。</span><span class="sxs-lookup"><span data-stu-id="cd252-367">Start the **Add Roles and Features Wizard**.</span></span>
    
- <span data-ttu-id="cd252-368">開啟 [**檔案與存放服務**] 節點。</span><span class="sxs-lookup"><span data-stu-id="cd252-368">Open the **File and Storage Services** node.</span></span>
    
- <span data-ttu-id="cd252-369">選取 [ **DFS 命名空間**和**DFS 複寫**。</span><span class="sxs-lookup"><span data-stu-id="cd252-369">Select **DFS Namespaces** and **DFS replication**.</span></span>
    
- <span data-ttu-id="cd252-370">按 [**下一步**完成精靈指示的步驟。</span><span class="sxs-lookup"><span data-stu-id="cd252-370">Click **Next** to finish the wizard steps.</span></span>
    
<span data-ttu-id="cd252-371">下表提供 DFSR 參考文章與部落格文章的連結。</span><span class="sxs-lookup"><span data-stu-id="cd252-371">The following table provides links to DFSR reference articles and blog posts.</span></span>
  
<span data-ttu-id="cd252-372">**表格： DFSR 的參考文章**</span><span class="sxs-lookup"><span data-stu-id="cd252-372">**Table: Reference articles for DFSR**</span></span>

|<span data-ttu-id="cd252-373">**標題**</span><span class="sxs-lookup"><span data-stu-id="cd252-373">**Title**</span></span>|<span data-ttu-id="cd252-374">**描述**</span><span class="sxs-lookup"><span data-stu-id="cd252-374">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="cd252-375">複寫</span><span class="sxs-lookup"><span data-stu-id="cd252-375">Replication</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392732) <br/> |<span data-ttu-id="cd252-376">DFS 管理 TechNet 主題的連結複寫</span><span class="sxs-lookup"><span data-stu-id="cd252-376">DFS Management TechNet topic with links for replication</span></span>  <br/> |
|[<span data-ttu-id="cd252-377">DFS 複寫： 生存指南</span><span class="sxs-lookup"><span data-stu-id="cd252-377">DFS Replication: Survival Guide</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392737) <br/> |<span data-ttu-id="cd252-378">使用 DFS 資訊的連結 wiki （英文)</span><span class="sxs-lookup"><span data-stu-id="cd252-378">Wiki with links to DFS information</span></span>  <br/> |
|[<span data-ttu-id="cd252-379">DFS 複寫： 常見問題集</span><span class="sxs-lookup"><span data-stu-id="cd252-379">DFS Replication: Frequently Asked Questions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392738) <br/> |<span data-ttu-id="cd252-380">DFS 複寫 TechNet 主題</span><span class="sxs-lookup"><span data-stu-id="cd252-380">DFS Replication TechNet topic</span></span>  <br/> |
|[<span data-ttu-id="cd252-381">曼 Barreto 部落格</span><span class="sxs-lookup"><span data-stu-id="cd252-381">Jose Barreto's Blog</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392739) <br/> |<span data-ttu-id="cd252-382">撰寫由主要程式總監 microsoft 檔案伺服器團隊部落格</span><span class="sxs-lookup"><span data-stu-id="cd252-382">Blog written by a Principal Program Manager on the File Server team at Microsoft</span></span>  <br/> |
|[<span data-ttu-id="cd252-383">在 Microsoft-檔案封包部落格儲存區小組</span><span class="sxs-lookup"><span data-stu-id="cd252-383">The Storage Team at Microsoft - File Cabinet Blog</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=392740) <br/> |<span data-ttu-id="cd252-384">檔案服務和 Windows Server 中的儲存功能的相關部落格</span><span class="sxs-lookup"><span data-stu-id="cd252-384">Blog about file services and storage features in Windows Server</span></span>  <br/> |
   
## <a name="phase-6-set-up-log-shipping-to-the-recovery-farm"></a><span data-ttu-id="cd252-385">階段 6： 設定記錄傳送至修復伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="cd252-385">Phase 6: Set up log shipping to the recovery farm</span></span>

<span data-ttu-id="cd252-p146">記錄傳送是設定此環境中的嚴重損壞修復的重要元件。您可以使用記錄傳送會自動將資料庫的交易記錄檔從主要資料庫伺服器執行個體傳送到次要資料庫伺服器執行個體。若要設定記錄傳送，請參閱 ＜[設定記錄在 SharePoint 2013 中傳送](https://docs.microsoft.com/sharepoint/administration/configure-log-shipping)。</span><span class="sxs-lookup"><span data-stu-id="cd252-p146">Log shipping is the critical component for setting up disaster recovery in this environment. You can use log shipping to automatically send transaction log files for databases from a primary database server instance to a secondary database server instance. To set up log shipping, see [Configure log shipping in SharePoint 2013](https://docs.microsoft.com/sharepoint/administration/configure-log-shipping).</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="cd252-p147">記錄傳送支援 SharePoint Server 中僅限於特定資料庫。如需詳細資訊，請參閱[支援的高可用性和嚴重損壞修復 SharePoint 資料庫 (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=393121)。</span><span class="sxs-lookup"><span data-stu-id="cd252-p147">Log shipping support in SharePoint Server is limited to certain databases. For more information, see [Supported high availability and disaster recovery options for SharePoint databases (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=393121).</span></span> 
  
## <a name="phase-7-validate-failover-and-recovery"></a><span data-ttu-id="cd252-391">階段 7： 驗證容錯移轉及復原</span><span class="sxs-lookup"><span data-stu-id="cd252-391">Phase 7: Validate failover and recovery</span></span>

<span data-ttu-id="cd252-p148">此階段中最後的目標是驗證嚴重損壞復原解決方案運作如預期進行。若要這樣做，建立容錯移轉事件關閉實際執行伺服器陣列並啟動取代的復原伺服器陣列。您可以啟動容錯移轉案例以手動方式或使用指令碼。</span><span class="sxs-lookup"><span data-stu-id="cd252-p148">The goal of this final phase is to verify that the disaster recovery solution works as planned. To do this, create a failover event that shuts down the production farm and starts up the recovery farm as a replacement. You can start a failover scenario manually or by using scripts.</span></span>
  
<span data-ttu-id="cd252-p149">第一個步驟是以停止傳入伺服器陣列服務或內容的使用者要求。停用 DNS 項目或關閉前端網頁伺服器您可以這麼做。在伺服器陣列已 「 關閉 」 之後，您可以容錯移轉的復原伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="cd252-p149">The first step is to stop incoming user requests for farm services or content. You can do this by disabling DNS entries or by shutting down the front-end web servers. After the farm is "down," you can fail over to the recovery farm.</span></span>
  
### <a name="stop-log-shipping"></a><span data-ttu-id="cd252-398">停止記錄傳送</span><span class="sxs-lookup"><span data-stu-id="cd252-398">Stop log shipping</span></span>

<span data-ttu-id="cd252-p150">您必須先停止在伺服器陣列復原之前的記錄傳送。停止記錄前，傳送 Azure 中的次要伺服器上，並再停止於主要伺服器內部。若要停止記錄傳送次要的第一部伺服器上，然後在主要伺服器上使用下列指令碼。指令碼中的資料庫名稱可能會不同，根據您的環境。</span><span class="sxs-lookup"><span data-stu-id="cd252-p150">You must stop log shipping before farm recovery. Stop log shipping on the secondary server in Azure first, and then stop it on the primary server on-premises. Use the following script to stop log shipping on the secondary server first and then on the primary server. The database names in the script might be different, depending on your environment.</span></span>
  
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

### <a name="restore-the-backups"></a><span data-ttu-id="cd252-403">還原的備份</span><span class="sxs-lookup"><span data-stu-id="cd252-403">Restore the backups</span></span>

<span data-ttu-id="cd252-p151">備份必須還原他們所建立的順序。您可以還原至特定的交易記錄檔備份之前，您必須先不含回復未認可的交易還原下列先前的備份 (也就使用`WITH NORECOVERY`)：</span><span class="sxs-lookup"><span data-stu-id="cd252-p151">Backups must be restored in the order in which they were created. Before you can restore a particular transaction log backup, you must first restore the following previous backups without rolling back uncommitted transactions (that is, by using  `WITH NORECOVERY`):</span></span>
  
- <span data-ttu-id="cd252-p152">完整資料庫備份和上次的差異備份-如果有的話之前的特定交易記錄備份, 進行還原這些備份。建立最近的完整或差異資料庫備份之前，資料庫所使用的完整復原模式或大量記錄的復原模式。</span><span class="sxs-lookup"><span data-stu-id="cd252-p152">The full database backup and the last differential backup - Restore these backups, if any exist, taken before the particular transaction log backup. Before the most recent full or differential database backup was created, the database was using the full recovery model or bulk-logged recovery model.</span></span>
    
- <span data-ttu-id="cd252-p153">所有交易記錄備份-都還原所需的完整資料庫備份或差異備份 （如果您都還原一個） 之後和之前的特定的交易記錄檔的備份所有交易記錄檔。記錄檔備份必須在其中建立時，不含任何間距記錄鏈結中順序套用。</span><span class="sxs-lookup"><span data-stu-id="cd252-p153">All transaction log backups - Restore any transaction log backups taken after the full database backup or the differential backup (if you restore one) and before the particular transaction log backup. Log backups must be applied in the sequence in which they were created, without any gaps in the log chain.</span></span>
    
<span data-ttu-id="cd252-p154">若要使網站轉譯復原次要伺服器上的內容資料庫，移除在復原之前的所有資料庫連線。若要還原之資料庫，請執行下列 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="cd252-p154">To recover the content database on the secondary server so that the sites render, remove all database connections before recovery. To restore the database, run the following SQL statement.</span></span>
  
```
restore database WSS_Content with recovery

```

> [!IMPORTANT]
> <span data-ttu-id="cd252-p155">當您明確地使用 T-SQL 時，指定 [ **WITH NORECOVERY** ] 或 [ **WITH RECOVERY**以消除模稜兩可每個還原陳述式 — 這是非常重要撰寫指令碼時。還原完整及差異備份之後，可以在 SQL Server Management Studio 還原的交易記錄檔。此外，因為已經停止記錄傳送，內容資料庫是處於待命狀態，因此您必須將狀態變更為完整存取權。</span><span class="sxs-lookup"><span data-stu-id="cd252-p155">When you use T-SQL explicitly, specify either **WITH NORECOVERY** or **WITH RECOVERY** in every RESTORE statement to eliminate ambiguity—this is very important when writing scripts. After the full and differential backups are restored, the transaction logs can be restored in SQL Server Management Studio. Also, because log shipping is already stopped, the content database is in a standby state, so you must change the state to full access.</span></span>
  
<span data-ttu-id="cd252-p156">在 SQL Server Management Studio 中，以滑鼠右鍵按一下 [ **WSS_Content** ] 資料庫、 指向 [**工作** > **還原**，然後按一下 [**交易記錄檔**（如果您不具有還原完整備份，這不是使用）。如需詳細資訊，請參閱[還原交易記錄備份 (SQL Server)](https://go.microsoft.com/fwlink/p/?LinkId=392778)。</span><span class="sxs-lookup"><span data-stu-id="cd252-p156">In SQL Server Management Studio, right-click the **WSS_Content** database, point to **Tasks** > **Restore**, and then click **Transaction Log** (if you have not restored the full backup, this is not available). For more information, see[Restore a Transaction Log Backup (SQL Server)](https://go.microsoft.com/fwlink/p/?LinkId=392778).</span></span>
  
### <a name="crawl-the-content-source"></a><span data-ttu-id="cd252-417">編目的內容來源</span><span class="sxs-lookup"><span data-stu-id="cd252-417">Crawl the content source</span></span>

<span data-ttu-id="cd252-p157">您必須啟動還原搜尋服務的每個內容來源的完整編目。請注意您會失去從內部部署伺服器陣列，例如搜尋建議一些分析資訊。開始完整編目、 使用 Windows PowerShell cmdlet **Restore-spenterprisesearchserviceapplication**及指定的記錄傳送資料庫並複製搜尋管理資料庫之前**Search_Service__DB_<GUID>**。此指令程式提供搜尋組態、 結構描述、 managed 的屬性、 規則及來源，並建立一組預設其他元件。</span><span class="sxs-lookup"><span data-stu-id="cd252-p157">You must start a full crawl for each content source to restore the Search Service. Note that you lose some analytics information from the on-premises farm, such as search recommendations. Before you start the full crawls, use the Windows PowerShell cmdlet **Restore-SPEnterpriseSearchServiceApplication** and specify the log-shipped and replicated Search Administration database, **Search_Service__DB_<GUID>**. This cmdlet gives the search configuration, schema, managed properties, rules, and sources and creates a default set of the other components.</span></span>
  
<span data-ttu-id="cd252-422">若要啟動完整編目，請完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="cd252-422">To start a full crawl, complete the following steps:</span></span>
  
1. <span data-ttu-id="cd252-423">在 SharePoint 2013 管理中心，移至 [**應用程式管理** > **服務應用程式** > **管理服務應用程式**，然後按一下 [您要編目之搜尋服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="cd252-423">In the SharePoint 2013 Central Administration, go to **Application Management** > **Service Applications** > **Manage service applications**, and then click the Search Service application that you want to crawl.</span></span>
    
2. <span data-ttu-id="cd252-424">在 [**搜尋管理**] 頁面上，按一下 [**內容來源**]，指向您想，請按一下的箭頭，然後再按一下 [**啟動完整編目**的內容來源。</span><span class="sxs-lookup"><span data-stu-id="cd252-424">On the **Search Administration** page, click **Content Sources**, point to the content source that you want, click the arrow, and then click **Start Full Crawl**.</span></span>
    
### <a name="recover-farm-services"></a><span data-ttu-id="cd252-425">復原伺服器陣列服務</span><span class="sxs-lookup"><span data-stu-id="cd252-425">Recover farm services</span></span>

<span data-ttu-id="cd252-426">下表顯示如何復原有記錄傳送資料庫、 服務資料庫但不建議還原與記錄傳送和不具有資料庫的服務的服務。</span><span class="sxs-lookup"><span data-stu-id="cd252-426">The following table shows how to recover services that have log-shipped databases, the services that have databases but are not recommended to restore with log shipping, and the services that do not have databases.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="cd252-427">內部部署 SharePoint 資料庫還原至 Azure 環境會無法復原您沒有已安裝在 Azure 中手動任何 SharePoint 服務。</span><span class="sxs-lookup"><span data-stu-id="cd252-427">Restoring an on-premises SharePoint database into the Azure environment will not recover any SharePoint services that you did not already install in Azure manually.</span></span> 
  
<span data-ttu-id="cd252-428">**表格： 服務應用程式資料庫參考 （英文）**</span><span class="sxs-lookup"><span data-stu-id="cd252-428">**Table: Service application database reference**</span></span>

|<span data-ttu-id="cd252-429">**記錄傳送資料庫還原這些服務**</span><span class="sxs-lookup"><span data-stu-id="cd252-429">**Restore these services from log-shipped databases**</span></span>|<span data-ttu-id="cd252-430">**這些服務已在資料庫，但建議您在不含還原其資料庫啟動這些服務**</span><span class="sxs-lookup"><span data-stu-id="cd252-430">**These services have databases, but we recommend that you start these services without restoring their databases**</span></span>|<span data-ttu-id="cd252-431">**這些服務不資料儲存在資料庫 ；容錯移轉後啟動這些服務**</span><span class="sxs-lookup"><span data-stu-id="cd252-431">**These services do not store data in databases; start these services after failover**</span></span>|
|:-----|:-----|:-----|
| <span data-ttu-id="cd252-432">機器翻譯服務</span><span class="sxs-lookup"><span data-stu-id="cd252-432">Machine Translation Service</span></span> <br/>  <span data-ttu-id="cd252-433">Managed Metadata Service</span><span class="sxs-lookup"><span data-stu-id="cd252-433">Managed Metadata Service</span></span> <br/>  <span data-ttu-id="cd252-434">Secure Store Service</span><span class="sxs-lookup"><span data-stu-id="cd252-434">Secure Store Service</span></span> <br/>  <span data-ttu-id="cd252-p158">使用者設定檔。（僅限設定檔及社交標記資料庫的支援。同步處理資料庫不支援。）</span><span class="sxs-lookup"><span data-stu-id="cd252-p158">User Profile. (Only the Profile and Social Tagging databases are supported. The Synchronization database is not supported.)</span></span> <br/>  <span data-ttu-id="cd252-438">Microsoft SharePoint Foundation 訂閱設定服務</span><span class="sxs-lookup"><span data-stu-id="cd252-438">Microsoft SharePoint Foundation Subscription Settings Service</span></span> <br/> | <span data-ttu-id="cd252-439">Usage and Health Data Collection</span><span class="sxs-lookup"><span data-stu-id="cd252-439">Usage and Health Data Collection</span></span> <br/>  <span data-ttu-id="cd252-440">State Service</span><span class="sxs-lookup"><span data-stu-id="cd252-440">State service</span></span> <br/>  <span data-ttu-id="cd252-441">Word automation</span><span class="sxs-lookup"><span data-stu-id="cd252-441">Word automation</span></span> <br/> | <span data-ttu-id="cd252-442">Excel Services</span><span class="sxs-lookup"><span data-stu-id="cd252-442">Excel Services</span></span> <br/>  <span data-ttu-id="cd252-443">PerformancePoint Services</span><span class="sxs-lookup"><span data-stu-id="cd252-443">PerformancePoint Services</span></span> <br/>  <span data-ttu-id="cd252-444">PowerPoint 轉換</span><span class="sxs-lookup"><span data-stu-id="cd252-444">PowerPoint Conversion</span></span> <br/>  <span data-ttu-id="cd252-445">Visio Graphics Service</span><span class="sxs-lookup"><span data-stu-id="cd252-445">Visio Graphics Service</span></span> <br/>  <span data-ttu-id="cd252-446">Work Management</span><span class="sxs-lookup"><span data-stu-id="cd252-446">Work Management</span></span> <br/> |
   
<span data-ttu-id="cd252-447">下列範例會示範如何將資料庫還原的受管理的中繼資料服務。</span><span class="sxs-lookup"><span data-stu-id="cd252-447">The following example shows how to restore the Managed Metadata service from a database.</span></span>
  
<span data-ttu-id="cd252-p159">使用現有的 Managed_Metadata_DB 資料庫。此資料庫會記錄傳送、 但有任何作用中 service 應用程式次要伺服器陣列，因此它需要後的服務應用程式中進行連線。</span><span class="sxs-lookup"><span data-stu-id="cd252-p159">This uses the existing Managed_Metadata_DB database. This database is log shipped, but there is no active service application on the secondary farm, so it needs to be connected after the service application is in place.</span></span>
  
<span data-ttu-id="cd252-450">首先，使用`New-SPMetadataServiceApplication`，並指定`DatabaseName`切換還原資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="cd252-450">First, use  `New-SPMetadataServiceApplication`, and specify the  `DatabaseName` switch with the name of the restored database.</span></span>
  
<span data-ttu-id="cd252-451">下一步]，如下所示的次要伺服器上，設定新的受管理的中繼資料服務應用程式：</span><span class="sxs-lookup"><span data-stu-id="cd252-451">Next, configure the new Managed Metadata Service Application on the secondary server, as follows:</span></span>
  
- <span data-ttu-id="cd252-452">名稱： 受管理的中繼資料服務</span><span class="sxs-lookup"><span data-stu-id="cd252-452">Name: Managed Metadata Service</span></span>
    
- <span data-ttu-id="cd252-453">資料庫伺服器： 從隨附的交易記錄檔的資料庫名稱</span><span class="sxs-lookup"><span data-stu-id="cd252-453">Database server: The database name from the shipped transaction log</span></span>
    
- <span data-ttu-id="cd252-454">資料庫名稱： Managed_Metadata_DB</span><span class="sxs-lookup"><span data-stu-id="cd252-454">Database name: Managed_Metadata_DB</span></span>
    
- <span data-ttu-id="cd252-455">應用程式集區： SharePoint Service 應用程式</span><span class="sxs-lookup"><span data-stu-id="cd252-455">Application pool: SharePoint Service Applications</span></span> 
    
### <a name="manage-dns-records"></a><span data-ttu-id="cd252-456">管理 DNS 記錄</span><span class="sxs-lookup"><span data-stu-id="cd252-456">Manage DNS records</span></span>

<span data-ttu-id="cd252-457">您必須手動建立 DNS 記錄以指向 SharePoint 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="cd252-457">You must manually create DNS records to point to your SharePoint farm.</span></span>
  
<span data-ttu-id="cd252-p160">在大多數情況下包含多部前端網頁伺服器，其合理利用 Windows Server 2012 或硬體負載平衡器分散要求在伺服器陣列中 web 前端伺服器之間的網路負載平衡功能。網路負載平衡也可以協助減少風險如果其中一部 web 前端伺服器失敗散佈到其他伺服器的要求。</span><span class="sxs-lookup"><span data-stu-id="cd252-p160">In most cases where you have multiple front-end web servers, it makes sense to take advantage of the Network Load Balancing feature in Windows Server 2012 or a hardware load balancer to distribute requests among the web-front-end servers in your farm. Network load balancing can also help reduce risk by distributing requests to the other servers if one of your web-front-end servers fails.</span></span> 
  
<span data-ttu-id="cd252-p161">一般而言，當您設定好的網路負載平衡，您的叢集指派單一 IP 位址。您再建立 DNS 主機記錄中的 DNS 提供者為您指向叢集中的網路。（這個專案中，我們放入的 DNS 伺服器 Azure 中的 [恢復能力以防內部部署資料中心失敗。）例如，您可以在其中建立 DNS 記錄，在 DNS 管理員中 Active Directory 中，例如呼叫`http://sharepoint.contoso.com`、 指引您負載平衡叢集中的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="cd252-p161">Typically, when you set up network load balancing, your cluster is assigned a single IP address. You then create a DNS host record in the DNS provider for your network that points to the cluster. (For this project, we put a DNS server in Azure for resiliency in case of an on-premises datacenter failure.) For instance, you can create a DNS record, in DNS Manager in Active Directory, for example, called  `http://sharepoint.contoso.com`, that points to the IP address for your load-balanced cluster.</span></span>
  
<span data-ttu-id="cd252-p162">外部存取您的 SharePoint 伺服器陣列，您可以建立主機記錄您的內部網路的用戶端使用的相同 URL 的外部 DNS 伺服器 (例如`http://sharepoint.contoso.com`) 指引防火牆的外部 IP 位址。(最佳作法是使用此範例中，會使內部 DNS 伺服器為進行系統授權設定分割 DNS`contoso.com`並將要求直接至 SharePoint 伺服器陣列叢集，而不是外部 DNS 伺服器路由的 DNS 要求。)外部 IP 位址然後可以對應內部 IP 位址的內部部署叢集，讓用戶端找到他們所尋找的資源。</span><span class="sxs-lookup"><span data-stu-id="cd252-p162">For external access to your SharePoint farm, you can create a host record on an external DNS server with the same URL that clients use on your intranet (for example, `http://sharepoint.contoso.com`) that points to an external IP address in your firewall. (A best practice, using this example, is to set up split DNS so that the internal DNS server is authoritative for `contoso.com` and routes requests directly to the SharePoint farm cluster, rather than routing DNS requests to your external DNS server.) You can then map the external IP address to the internal IP address of your on-premises cluster so that clients find the resources they are looking for.</span></span>
  
<span data-ttu-id="cd252-465">從這裡，您可能會執行到幾個不同的嚴重損壞修復案例：</span><span class="sxs-lookup"><span data-stu-id="cd252-465">From here, you might run into a couple of different disaster-recovery scenarios:</span></span>
  
 <span data-ttu-id="cd252-p163">**範例案例： 內部部署 SharePoint 伺服器陣列是無法使用，因為在內部部署 SharePoint 伺服器陣列的硬體故障。** 在此例中完成 Azure SharePoint 伺服器陣列的容錯移轉的步驟之後，您可以設定網路上的負載平衡復原 SharePoint 伺服器陣列的 web 前端伺服器，您並未與內部部署伺服器陣列的方式相同。然後可以將主機記錄重新導向內部 DNS 提供者以指向復原伺服器陣列的叢集 IP 位址。請注意，它可能需要一些時間快取的 DNS 記錄之前用戶端上會重新整理並指向 [復原伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="cd252-p163">**Example scenario: The on-premises SharePoint farm is unavailable because of hardware failure in the on-premises SharePoint farm.** In this case, after you have completed the steps for failover to the Azure SharePoint farm, you can configure network load balancing on the recovery SharePoint farm's web-front-end servers, the same way you did with the on-premises farm. You can then redirect the host record in your internal DNS provider to point to the recovery farm's cluster IP address. Note that it can take some time before cached DNS records on clients are refreshed and point to the recovery farm.</span></span>
  
 <span data-ttu-id="cd252-p164">**範例案例： 內部部署資料中心是完全遺失。** 此案例中可能會由於天然災害時，例如消防或泛光 」。在此例中為 enterprise 中，您可能必須裝載於另一個區域，以及您有其專屬的目錄服務和 DNS 的 Azure 子網路的次要資料中心。如同前一個災害案例中，您可以重新導向內部和外部 DNS 記錄以指向 Azure SharePoint 伺服器陣列。同樣地，記下的 DNS 記錄傳播可能需要一些時間。</span><span class="sxs-lookup"><span data-stu-id="cd252-p164">**Example scenario: The on-premises datacenter is lost completely.** This scenario might occur due to a natural disaster, such as a fire or flood. In this case, for an enterprise, you would likely have a secondary datacenter hosted in another region as well as your Azure subnet that has its own directory services and DNS. As in the previous disaster scenario, you can redirect your internal and external DNS records to point to the Azure SharePoint farm. Again, take note that DNS-record propagation can take some time.</span></span>
  
<span data-ttu-id="cd252-p165">如果您的[主機命名型網站集合架構與部署 (SharePoint 2013)](https://docs.microsoft.com/SharePoint/administration/host-named-site-collection-architecture-and-deployment)建議使用主機命名型網站集合，您可能必須在 SharePoint 伺服器陣列，以唯一相同的 web 應用程式所主控的數個網站集合DNS 名稱 (例如`http://sales.contoso.com`和`http://marketing.contoso.com`)。在此例中，您可以建立指向您的叢集 IP 位址的 DNS 記錄每個網站集合。要求達到您的 SharePoint web 前端伺服器之後，他們處理每個要求路由到適當的網站集合。</span><span class="sxs-lookup"><span data-stu-id="cd252-p165">If you are using host-named site collections, as recommended in [Host-named site collection architecture and deployment (SharePoint 2013)](https://docs.microsoft.com/SharePoint/administration/host-named-site-collection-architecture-and-deployment), you might have several site collections hosted by the same web application in your SharePoint farm, with unique DNS names (for example, `http://sales.contoso.com` and `http://marketing.contoso.com`). In this case, you can create DNS records for each site collection that point to your cluster IP address. After a request reaches your SharePoint web-front-end servers, they handle routing each request to the appropriate site collection.</span></span>
  
## <a name="microsoft-proof-of-concept-environment"></a><span data-ttu-id="cd252-478">Microsoft 概念證明環境</span><span class="sxs-lookup"><span data-stu-id="cd252-478">Microsoft proof-of-concept environment</span></span>

<span data-ttu-id="cd252-p166">我們設計及測試此解決方案的概念證明環境。我們測試環境的設計目標是部署和復原我們可能會發現客戶環境中的 SharePoint 伺服器陣列。我們所做的數個假設，但我們知道伺服器陣列所需提供的所有不含任何自訂的方塊 （英文） 功能。拓撲的設計是高可用性使用從欄位和產品] 群組中的最佳作法指導。</span><span class="sxs-lookup"><span data-stu-id="cd252-p166">We designed and tested a proof-of-concept environment for this solution. The design goal for our test environment was to deploy and recover a SharePoint farm that we might find in a customer environment. We made several assumptions, but we knew that the farm needed to provide all of the out-of-the-box functionality without any customizations. The topology was designed for high availability by using best practice guidance from the field and product group.</span></span>
  
<span data-ttu-id="cd252-483">下表說明我們建立及設定內部部署測試環境的 HYPER-V 虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="cd252-483">The following table describes the Hyper-V virtual machines that we created and configured for the on-premises test environment.</span></span>
  
<span data-ttu-id="cd252-484">**表格： 虛擬機器的內部部署測試**</span><span class="sxs-lookup"><span data-stu-id="cd252-484">**Table: Virtual machines for on-premises test**</span></span>

|<span data-ttu-id="cd252-485">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="cd252-485">**Server name**</span></span>|<span data-ttu-id="cd252-486">**角色**</span><span class="sxs-lookup"><span data-stu-id="cd252-486">**Role**</span></span>|<span data-ttu-id="cd252-487">**組態**</span><span class="sxs-lookup"><span data-stu-id="cd252-487">**Configuration**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="cd252-488">DC1</span><span class="sxs-lookup"><span data-stu-id="cd252-488">DC1</span></span>  <br/> |<span data-ttu-id="cd252-489">使用 Active Directory 網域控制站。</span><span class="sxs-lookup"><span data-stu-id="cd252-489">Domain controller with Active Directory.</span></span>  <br/> |<span data-ttu-id="cd252-490">2 個處理器</span><span class="sxs-lookup"><span data-stu-id="cd252-490">Two processors</span></span>  <br/> <span data-ttu-id="cd252-491">從 512 MB 透過 4 GB 的 RAM</span><span class="sxs-lookup"><span data-stu-id="cd252-491">From 512 MB through 4 GB of RAM</span></span>  <br/> <span data-ttu-id="cd252-492">1 x 127 GB 硬碟</span><span class="sxs-lookup"><span data-stu-id="cd252-492">1 x 127-GB hard disk</span></span>  <br/> |
|<span data-ttu-id="cd252-493">RRAS</span><span class="sxs-lookup"><span data-stu-id="cd252-493">RRAS</span></span>  <br/> |<span data-ttu-id="cd252-494">設定與路由及遠端存取服務 (RRAS) 角色的伺服器。</span><span class="sxs-lookup"><span data-stu-id="cd252-494">Server configured with the Routing and Remote Access Service (RRAS) role.</span></span>  <br/> |<span data-ttu-id="cd252-495">2 個處理器</span><span class="sxs-lookup"><span data-stu-id="cd252-495">Two processors</span></span>  <br/> <span data-ttu-id="cd252-496">2-8 GB 的 RAM</span><span class="sxs-lookup"><span data-stu-id="cd252-496">2-8 GB of RAM</span></span>  <br/> <span data-ttu-id="cd252-497">1 x 127 GB 硬碟</span><span class="sxs-lookup"><span data-stu-id="cd252-497">1 x 127-GB hard disk</span></span>  <br/> |
|<span data-ttu-id="cd252-498">FS1</span><span class="sxs-lookup"><span data-stu-id="cd252-498">FS1</span></span>  <br/> |<span data-ttu-id="cd252-499">檔案伺服器與共用的備份和 DFSR 結束點。</span><span class="sxs-lookup"><span data-stu-id="cd252-499">File server with shares for backups and an end point for DFSR.</span></span>  <br/> |<span data-ttu-id="cd252-500">四個處理器</span><span class="sxs-lookup"><span data-stu-id="cd252-500">Four processors</span></span>  <br/> <span data-ttu-id="cd252-501">2-12 GB 的 RAM</span><span class="sxs-lookup"><span data-stu-id="cd252-501">2-12 GB of RAM</span></span>  <br/> <span data-ttu-id="cd252-502">1 x 127 GB 硬碟</span><span class="sxs-lookup"><span data-stu-id="cd252-502">1 x 127-GB hard disk</span></span>  <br/> <span data-ttu-id="cd252-503">1 x 1 TB 硬碟 (SAN)</span><span class="sxs-lookup"><span data-stu-id="cd252-503">1 x 1-TB hard disk (SAN)</span></span>  <br/> <span data-ttu-id="cd252-504">1 x 750 GB 硬碟</span><span class="sxs-lookup"><span data-stu-id="cd252-504">1 x 750-GB hard disk</span></span>  <br/> |
|<span data-ttu-id="cd252-505">SP-WFE1，SP-WFE2</span><span class="sxs-lookup"><span data-stu-id="cd252-505">SP-WFE1, SP-WFE2</span></span>  <br/> |<span data-ttu-id="cd252-506">前端網頁伺服器。</span><span class="sxs-lookup"><span data-stu-id="cd252-506">Front-end web servers.</span></span>  <br/> |<span data-ttu-id="cd252-507">四個處理器</span><span class="sxs-lookup"><span data-stu-id="cd252-507">Four processors</span></span>  <br/> <span data-ttu-id="cd252-508">16 GB RAM</span><span class="sxs-lookup"><span data-stu-id="cd252-508">16 GB of RAM</span></span>  <br/> |
|<span data-ttu-id="cd252-509">SP-SP-APP2 APP1 SP APP3</span><span class="sxs-lookup"><span data-stu-id="cd252-509">SP-APP1, SP-APP2, SP-APP3</span></span>  <br/> |<span data-ttu-id="cd252-510">應用程式伺服器。</span><span class="sxs-lookup"><span data-stu-id="cd252-510">Application servers.</span></span>  <br/> |<span data-ttu-id="cd252-511">四個處理器</span><span class="sxs-lookup"><span data-stu-id="cd252-511">Four processors</span></span>  <br/> <span data-ttu-id="cd252-512">2-16 GB 的 RAM</span><span class="sxs-lookup"><span data-stu-id="cd252-512">2-16 GB of RAM</span></span>  <br/> |
|<span data-ttu-id="cd252-513">SP-SQL-HA1，SP-SQL-HA2</span><span class="sxs-lookup"><span data-stu-id="cd252-513">SP-SQL-HA1, SP-SQL-HA2</span></span>  <br/> |<span data-ttu-id="cd252-p167">設定 SQL Server 2012 AlwaysOn 可用性群組來提供高可用性的資料庫伺服器。這個設定使用 SP-sql-ha1 和 SP-SQL-HA2 做為主要和次要複本。</span><span class="sxs-lookup"><span data-stu-id="cd252-p167">Database servers, configured with SQL Server 2012 AlwaysOn availability groups to provide high availability. This configuration uses SP-SQL-HA1 and SP-SQL-HA2 as the primary and secondary replicas.</span></span>  <br/> |<span data-ttu-id="cd252-516">四個處理器</span><span class="sxs-lookup"><span data-stu-id="cd252-516">Four processors</span></span>  <br/> <span data-ttu-id="cd252-517">2-16 GB 的 RAM</span><span class="sxs-lookup"><span data-stu-id="cd252-517">2-16 GB of RAM</span></span>  <br/> |
   
<span data-ttu-id="cd252-518">下表說明我們建立及設定的前端網頁伺服器和應用程式伺服器的內部測試環境的 HYPER-V 虛擬機器的磁碟機設定。</span><span class="sxs-lookup"><span data-stu-id="cd252-518">The following table describes drive configurations for the Hyper-V virtual machines that we created and configured for the front-end web and application servers for the on-premises test environment.</span></span>
  
<span data-ttu-id="cd252-519">**表格： Front End 網頁的虛擬機器的磁碟機需求與內部部署的應用程式伺服器測試**</span><span class="sxs-lookup"><span data-stu-id="cd252-519">**Table: Virtual machine drive requirements for the Front End Web and Application servers for the on-premises test**</span></span>

|<span data-ttu-id="cd252-520">**磁碟機代號**</span><span class="sxs-lookup"><span data-stu-id="cd252-520">**Drive letter**</span></span>|<span data-ttu-id="cd252-521">**大小**</span><span class="sxs-lookup"><span data-stu-id="cd252-521">**Size**</span></span>|<span data-ttu-id="cd252-522">**目錄名稱**</span><span class="sxs-lookup"><span data-stu-id="cd252-522">**Directory name**</span></span>|<span data-ttu-id="cd252-523">**路徑**</span><span class="sxs-lookup"><span data-stu-id="cd252-523">**Path**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="cd252-524">C</span><span class="sxs-lookup"><span data-stu-id="cd252-524">C</span></span>  <br/> |<span data-ttu-id="cd252-525">80</span><span class="sxs-lookup"><span data-stu-id="cd252-525">80</span></span>  <br/> |<span data-ttu-id="cd252-526">系統磁碟機</span><span class="sxs-lookup"><span data-stu-id="cd252-526">System drive</span></span>  <br/> |<span data-ttu-id="cd252-527"><DriveLetter>：\\程式檔案\\Microsoft SQL Server\\</span><span class="sxs-lookup"><span data-stu-id="cd252-527"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\</span></span>  <br/> |
|<span data-ttu-id="cd252-528">E</span><span class="sxs-lookup"><span data-stu-id="cd252-528">E</span></span>  <br/> |<span data-ttu-id="cd252-529">80</span><span class="sxs-lookup"><span data-stu-id="cd252-529">80</span></span>  <br/> |<span data-ttu-id="cd252-530">記錄檔磁碟 (40 GB)</span><span class="sxs-lookup"><span data-stu-id="cd252-530">Log drive (40 GB)</span></span>  <br/> |<span data-ttu-id="cd252-531"><DriveLetter>：\\程式檔案\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\資料</span><span class="sxs-lookup"><span data-stu-id="cd252-531"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA</span></span>  <br/> |
|<span data-ttu-id="cd252-532">F</span><span class="sxs-lookup"><span data-stu-id="cd252-532">F</span></span>  <br/> |<span data-ttu-id="cd252-533">80</span><span class="sxs-lookup"><span data-stu-id="cd252-533">80</span></span>  <br/> |<span data-ttu-id="cd252-534">頁面 (36 GB)</span><span class="sxs-lookup"><span data-stu-id="cd252-534">Page (36 GB)</span></span>  <br/> |<span data-ttu-id="cd252-535"><DriveLetter>：\\程式檔案\\Microsoft SQL Server\\MSSQL\\資料</span><span class="sxs-lookup"><span data-stu-id="cd252-535"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL\\DATA</span></span>  <br/> |
   
<span data-ttu-id="cd252-p168">下表說明 HYPER-V 虛擬機器建立及設定以做為內部資料庫伺服器的磁碟機設定。在 [**資料庫引擎組態**] 頁面存取**資料目錄**] 索引標籤來設定並加以確認，如下表所示的設定。</span><span class="sxs-lookup"><span data-stu-id="cd252-p168">The following table describes drive configurations for the Hyper-V virtual machines created and configured to serve as the on-premises database servers. On the **Database Engine Configuration** page, access the **Data Directories** tab to set and confirm the settings shown in the following table.</span></span>
  
<span data-ttu-id="cd252-538">**表格： 內部部署的資料庫伺服器的虛擬機器的磁碟機需求測試**</span><span class="sxs-lookup"><span data-stu-id="cd252-538">**Table: Virtual machine drive requirements for the database server for the on-premises test**</span></span>

|<span data-ttu-id="cd252-539">**磁碟機代號**</span><span class="sxs-lookup"><span data-stu-id="cd252-539">**Drive letter**</span></span>|<span data-ttu-id="cd252-540">**大小**</span><span class="sxs-lookup"><span data-stu-id="cd252-540">**Size**</span></span>|<span data-ttu-id="cd252-541">**目錄名稱**</span><span class="sxs-lookup"><span data-stu-id="cd252-541">**Directory name**</span></span>|<span data-ttu-id="cd252-542">**路徑**</span><span class="sxs-lookup"><span data-stu-id="cd252-542">**Path**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="cd252-543">C</span><span class="sxs-lookup"><span data-stu-id="cd252-543">C</span></span>  <br/> |<span data-ttu-id="cd252-544">80</span><span class="sxs-lookup"><span data-stu-id="cd252-544">80</span></span>  <br/> |<span data-ttu-id="cd252-545">資料根目錄</span><span class="sxs-lookup"><span data-stu-id="cd252-545">Data root directory</span></span>  <br/> |<span data-ttu-id="cd252-546"><DriveLetter>：\\程式檔案\\Microsoft SQL Server\\</span><span class="sxs-lookup"><span data-stu-id="cd252-546"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\</span></span>  <br/> |
|<span data-ttu-id="cd252-547">E</span><span class="sxs-lookup"><span data-stu-id="cd252-547">E</span></span>  <br/> |<span data-ttu-id="cd252-548">500 個</span><span class="sxs-lookup"><span data-stu-id="cd252-548">500</span></span>  <br/> |<span data-ttu-id="cd252-549">使用者資料庫目錄</span><span class="sxs-lookup"><span data-stu-id="cd252-549">User database directory</span></span>  <br/> |<span data-ttu-id="cd252-550"><DriveLetter>：\\程式檔案\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\資料</span><span class="sxs-lookup"><span data-stu-id="cd252-550"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA</span></span>  <br/> |
|<span data-ttu-id="cd252-551">F</span><span class="sxs-lookup"><span data-stu-id="cd252-551">F</span></span>  <br/> |<span data-ttu-id="cd252-552">500 個</span><span class="sxs-lookup"><span data-stu-id="cd252-552">500</span></span>  <br/> |<span data-ttu-id="cd252-553">使用者資料庫記錄檔目錄</span><span class="sxs-lookup"><span data-stu-id="cd252-553">User database log directory</span></span>  <br/> |<span data-ttu-id="cd252-554"><DriveLetter>：\\程式檔案\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\資料</span><span class="sxs-lookup"><span data-stu-id="cd252-554"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA</span></span>  <br/> |
|<span data-ttu-id="cd252-555">G</span><span class="sxs-lookup"><span data-stu-id="cd252-555">G</span></span>  <br/> |<span data-ttu-id="cd252-556">500 個</span><span class="sxs-lookup"><span data-stu-id="cd252-556">500</span></span>  <br/> |<span data-ttu-id="cd252-557">Temp DB 目錄</span><span class="sxs-lookup"><span data-stu-id="cd252-557">Temp DB directory</span></span>  <br/> |<span data-ttu-id="cd252-558"><DriveLetter>：\\程式檔案\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\資料</span><span class="sxs-lookup"><span data-stu-id="cd252-558"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA</span></span>  <br/> |
|<span data-ttu-id="cd252-559">H</span><span class="sxs-lookup"><span data-stu-id="cd252-559">H</span></span>  <br/> |<span data-ttu-id="cd252-560">500 個</span><span class="sxs-lookup"><span data-stu-id="cd252-560">500</span></span>  <br/> |<span data-ttu-id="cd252-561">Temp DB 記錄檔目錄</span><span class="sxs-lookup"><span data-stu-id="cd252-561">Temp DB log directory</span></span>  <br/> |<span data-ttu-id="cd252-562"><DriveLetter>：\\程式檔案\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\資料</span><span class="sxs-lookup"><span data-stu-id="cd252-562"><DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA</span></span>  <br/> |
   
### <a name="setting-up-the-test-environment"></a><span data-ttu-id="cd252-563">設定測試環境</span><span class="sxs-lookup"><span data-stu-id="cd252-563">Setting up the test environment</span></span>

<span data-ttu-id="cd252-p169">不同的部署階段測試小組通常正常運作之第一個的內部部署架構，然後在相對應的 Azure 環境。這會反映已執行內部的實際執行伺服器陣列的一般真實世界案例。什麼是更重要的是您應知道目前實際作業工作量、 容量及一般效能。除了建立符合業務需求嚴重損壞復原模式，您應該大小復原伺服器陣列的伺服器來傳送服務的最低層級。冷或暖待命環境中，復原伺服器陣列是一般會小於實際執行伺服器陣列。之後復原伺服器陣列的穩定性及實際執行，伺服器陣列可以擴充向上及向外延展來滿足工作量需求。</span><span class="sxs-lookup"><span data-stu-id="cd252-p169">During the different deployment phases, the test team typically worked on the on-premises architecture first and then on the corresponding Azure environment. This reflects the general real-world cases where in-house production farms are already running. What is even more important is that you should know the current production workload, capacity, and typical performance. In addition to building a disaster recovery model that can meet business requirements, you should size the recovery farm servers to deliver a minimum level of service. In a cold or warm standby environment, a recovery farm is typically smaller than a production farm. After the recovery farm is stable and in production, the farm can be scaled up and out to meet workload requirements.</span></span>
  
<span data-ttu-id="cd252-570">我們部署了我們的測試環境中下列三個階段：</span><span class="sxs-lookup"><span data-stu-id="cd252-570">We deployed our test environment in the following three phases:</span></span>
  
- <span data-ttu-id="cd252-571">設定混合式基礎結構</span><span class="sxs-lookup"><span data-stu-id="cd252-571">Set up the hybrid infrastructure</span></span>
    
- <span data-ttu-id="cd252-572">佈建伺服器</span><span class="sxs-lookup"><span data-stu-id="cd252-572">Provision the servers</span></span>
    
- <span data-ttu-id="cd252-573">部署 SharePoint 伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="cd252-573">Deploy the SharePoint farms</span></span>
    
#### <a name="set-up-the-hybrid-infrastructure"></a><span data-ttu-id="cd252-574">設定混合式基礎結構</span><span class="sxs-lookup"><span data-stu-id="cd252-574">Set up the hybrid infrastructure</span></span>

<span data-ttu-id="cd252-p170">此階段牽涉到內部部署伺服器陣列和 Azure 中的復原伺服器陣列在網域環境的設定。設定 Active Directory 相關聯的一般工作，以及測試小組會實作路由的方案和兩個環境之間的 VPN 連線。</span><span class="sxs-lookup"><span data-stu-id="cd252-p170">This phase involved setting up a domain environment for the on-premises farm and for the recovery farm in Azure. In addition to the normal tasks associated with configuring Active Directory, the test team implemented a routing solution and a VPN connection between the two environments.</span></span>
  
#### <a name="provision-the-servers"></a><span data-ttu-id="cd252-577">佈建伺服器</span><span class="sxs-lookup"><span data-stu-id="cd252-577">Provision the servers</span></span>

<span data-ttu-id="cd252-p171">伺服器陣列的伺服器，以及遭到所需的網域控制站佈建伺服器並設定來處理 RRAS 為網站 VPN 伺服器。兩個檔案伺服器已佈建 DFSR 服務與數個用戶端電腦已佈建測試人員。</span><span class="sxs-lookup"><span data-stu-id="cd252-p171">In addition to the farm servers, it was necessary to provision servers for the domain controllers and configure a server to handle RRAS as well as the site-to-site VPN. Two file servers were provisioned for the DFSR service, and several client computers were provisioned for testers.</span></span>
  
#### <a name="deploy-the-sharepoint-farms"></a><span data-ttu-id="cd252-580">部署 SharePoint 伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="cd252-580">Deploy the SharePoint farms</span></span>

<span data-ttu-id="cd252-p172">SharePoint 伺服器陣列是為了簡化環境穩定和疑難排解、 帳戶部署在兩個階段中如有需要。在第一階段中，每個伺服器陣列已部署在各層的拓撲以支援所需的功能的伺服器數目最小值。</span><span class="sxs-lookup"><span data-stu-id="cd252-p172">The SharePoint farms were deployed in two stages in order to simplify environment stabilization and troubleshooting, if required. During the first stage, each farm was deployed on the minimum number of servers for each tier of the topology to support the required functionality.</span></span>
  
<span data-ttu-id="cd252-p173">我們建立之前建立的 SharePoint 2013 伺服器安裝 SQL Server 資料庫伺服器。因為這是新部署時，我們會建立可用性群組才能部署 SharePoint。我們建立三個群組依據 ATL-MCS-001 最佳作法指導。</span><span class="sxs-lookup"><span data-stu-id="cd252-p173">We created the database servers with SQL Server installed before creating the SharePoint 2013 servers. Because this was a new deployment, we created the availability groups before deploying SharePoint. We created three groups based on MCS best practice guidance.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="cd252-p174">建立版面配置區的資料庫，讓您可以建立可用性群組安裝 SharePoint 之前。如需詳細資訊，請參閱 ＜[設定 SQL Server 2012 AlwaysOn 可用性群組的 SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=517626)</span><span class="sxs-lookup"><span data-stu-id="cd252-p174">Create placeholder databases so that you can create availability groups before the SharePoint installation. For more information, see [Configure SQL Server 2012 AlwaysOn Availability Groups for SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=517626)</span></span>
  
<span data-ttu-id="cd252-588">我們建立伺服器陣列，並依下列順序加入額外的伺服器：</span><span class="sxs-lookup"><span data-stu-id="cd252-588">We created the farm and joined additional servers in the following order:</span></span>
  
- <span data-ttu-id="cd252-589">佈建 SP-sql-ha1 和 SP-SQL-HA2。</span><span class="sxs-lookup"><span data-stu-id="cd252-589">Provision SP-SQL-HA1 and SP-SQL-HA2.</span></span>
    
- <span data-ttu-id="cd252-590">設定 AlwaysOn 並建立伺服器陣列的三個可用性群組。</span><span class="sxs-lookup"><span data-stu-id="cd252-590">Configure AlwaysOn and create the three availability groups for the farm.</span></span> 
    
- <span data-ttu-id="cd252-591">佈建 SP-APP1 以主控管理中心。</span><span class="sxs-lookup"><span data-stu-id="cd252-591">Provision SP-APP1 to host Central Administration.</span></span>
    
- <span data-ttu-id="cd252-592">佈建 SP WFE1 及 SP WFE2 主機分散式快取。</span><span class="sxs-lookup"><span data-stu-id="cd252-592">Provision SP-WFE1 and SP-WFE2 to host the distributed cache.</span></span> 
    
<span data-ttu-id="cd252-p175">我們使用_skipRegisterAsDistributedCachehost_參數在命令列執行**psconfig.exe**時。如需詳細資訊，請參閱[規劃摘要及 SharePoint Server 2013 中的分散式快取服務](https://docs.microsoft.com/sharepoint/administration/plan-for-feeds-and-the-distributed-cache-service)。</span><span class="sxs-lookup"><span data-stu-id="cd252-p175">We used the  _skipRegisterAsDistributedCachehost_ parameter when we ran **psconfig.exe** at the command line. For more information, see [Plan for feeds and the Distributed Cache service in SharePoint Server 2013](https://docs.microsoft.com/sharepoint/administration/plan-for-feeds-and-the-distributed-cache-service).</span></span> 
  
<span data-ttu-id="cd252-595">我們重複復原環境中的下列步驟：</span><span class="sxs-lookup"><span data-stu-id="cd252-595">We repeated the following steps in the recovery environment:</span></span>
  
- <span data-ttu-id="cd252-596">佈建亞利桑那州-sql-ha1 和亞利桑那州-SQL-HA2。</span><span class="sxs-lookup"><span data-stu-id="cd252-596">Provision AZ-SQL-HA1 and AZ-SQL-HA2.</span></span>
    
- <span data-ttu-id="cd252-597">設定 AlwaysOn 並建立伺服器陣列的三個可用性群組。</span><span class="sxs-lookup"><span data-stu-id="cd252-597">Configure AlwaysOn and create the three availability groups for the farm.</span></span>
    
- <span data-ttu-id="cd252-598">佈建亞利桑那州-APP1 以主控管理中心。</span><span class="sxs-lookup"><span data-stu-id="cd252-598">Provision AZ-APP1 to host Central Administration.</span></span>
    
- <span data-ttu-id="cd252-599">佈建亞利桑那州 WFE1 及亞利桑那州 WFE2 主機分散式快取。</span><span class="sxs-lookup"><span data-stu-id="cd252-599">Provision AZ-WFE1 and AZ-WFE2 to host the distributed cache.</span></span>
    
<span data-ttu-id="cd252-p176">我們設定分散式快取及新增的測試使用者和測試內容後，我們會啟動之部署的兩個階段。此支援所需向外延展層和設定伺服器陣列的伺服器陣列架構中所述的高可用性拓撲。</span><span class="sxs-lookup"><span data-stu-id="cd252-p176">After we configured the distributed cache and added test users and test content, we started stage two of the deployment. This required scaling out the tiers and configuring the farm servers to support the high-availability topology described in the farm architecture.</span></span>
  
<span data-ttu-id="cd252-602">下表說明虛擬機器、 子網路及我們設定復原伺服器陣列的可用性設定。</span><span class="sxs-lookup"><span data-stu-id="cd252-602">The following table describes the virtual machines, subnets, and availability sets we set up for our recovery farm.</span></span>
  
<span data-ttu-id="cd252-603">**表格： 復原伺服器陣列基礎結構**</span><span class="sxs-lookup"><span data-stu-id="cd252-603">**Table: Recovery farm infrastructure**</span></span>

|<span data-ttu-id="cd252-604">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="cd252-604">**Server name**</span></span>|<span data-ttu-id="cd252-605">**角色**</span><span class="sxs-lookup"><span data-stu-id="cd252-605">**Role**</span></span>|<span data-ttu-id="cd252-606">**組態**</span><span class="sxs-lookup"><span data-stu-id="cd252-606">**Configuration**</span></span>|<span data-ttu-id="cd252-607">**子網路**</span><span class="sxs-lookup"><span data-stu-id="cd252-607">**Subnet**</span></span>|<span data-ttu-id="cd252-608">**可用性設定組**</span><span class="sxs-lookup"><span data-stu-id="cd252-608">**Availability set**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="cd252-609">spDRAD</span><span class="sxs-lookup"><span data-stu-id="cd252-609">spDRAD</span></span>  <br/> |<span data-ttu-id="cd252-610">使用 Active Directory 網域控制站</span><span class="sxs-lookup"><span data-stu-id="cd252-610">Domain controller with Active Directory</span></span>  <br/> |<span data-ttu-id="cd252-611">2 個處理器</span><span class="sxs-lookup"><span data-stu-id="cd252-611">Two processors</span></span>  <br/> <span data-ttu-id="cd252-612">從 512 MB 透過 4 GB 的 RAM</span><span class="sxs-lookup"><span data-stu-id="cd252-612">From 512 MB through 4 GB of RAM</span></span>  <br/> <span data-ttu-id="cd252-613">1 x 127 GB 硬碟</span><span class="sxs-lookup"><span data-stu-id="cd252-613">1 x 127-GB hard disk</span></span>  <br/> |<span data-ttu-id="cd252-614">sp ADservers</span><span class="sxs-lookup"><span data-stu-id="cd252-614">sp-ADservers</span></span>  <br/> ||
|<span data-ttu-id="cd252-615">亞利桑那州-SP-FS</span><span class="sxs-lookup"><span data-stu-id="cd252-615">AZ-SP-FS</span></span>  <br/> |<span data-ttu-id="cd252-616">檔案伺服器與共用的備份和 DFSR 的端點</span><span class="sxs-lookup"><span data-stu-id="cd252-616">File server with shares for backups and an endpoint for DFSR</span></span>  <br/> | <span data-ttu-id="cd252-617">A5 組態：</span><span class="sxs-lookup"><span data-stu-id="cd252-617">A5 configuration:</span></span> <br/>  <span data-ttu-id="cd252-618">2 個處理器</span><span class="sxs-lookup"><span data-stu-id="cd252-618">Two processors</span></span> <br/>  <span data-ttu-id="cd252-619">14 GB 的 RAM</span><span class="sxs-lookup"><span data-stu-id="cd252-619">14 GB of RAM</span></span> <br/>  <span data-ttu-id="cd252-620">1 x 127 GB 硬碟</span><span class="sxs-lookup"><span data-stu-id="cd252-620">1 x 127-GB hard disk</span></span> <br/>  <span data-ttu-id="cd252-621">1 x 135 GB 硬碟</span><span class="sxs-lookup"><span data-stu-id="cd252-621">1 x 135-GB hard disk</span></span> <br/>  <span data-ttu-id="cd252-622">1 x 127 GB 硬碟</span><span class="sxs-lookup"><span data-stu-id="cd252-622">1 x 127-GB hard disk</span></span> <br/>  <span data-ttu-id="cd252-623">1 x 150 GB 硬碟</span><span class="sxs-lookup"><span data-stu-id="cd252-623">1 x 150-GB hard disk</span></span> <br/> |<span data-ttu-id="cd252-624">sp databaseservers</span><span class="sxs-lookup"><span data-stu-id="cd252-624">sp-databaseservers</span></span>  <br/> |<span data-ttu-id="cd252-625">DATA_SET</span><span class="sxs-lookup"><span data-stu-id="cd252-625">DATA_SET</span></span>  <br/> |
|<span data-ttu-id="cd252-626">亞利桑那州 WFE1、 亞利桑那州-WFE2</span><span class="sxs-lookup"><span data-stu-id="cd252-626">AZ-WFE1, AZ -WFE2</span></span>  <br/> |<span data-ttu-id="cd252-627">Front End 網頁伺服器</span><span class="sxs-lookup"><span data-stu-id="cd252-627">Front End Web servers</span></span>  <br/> | <span data-ttu-id="cd252-628">A5 組態：</span><span class="sxs-lookup"><span data-stu-id="cd252-628">A5 configuration:</span></span> <br/>  <span data-ttu-id="cd252-629">2 個處理器</span><span class="sxs-lookup"><span data-stu-id="cd252-629">Two processors</span></span> <br/>  <span data-ttu-id="cd252-630">14 GB 的 RAM</span><span class="sxs-lookup"><span data-stu-id="cd252-630">14 GB of RAM</span></span> <br/>  <span data-ttu-id="cd252-631">1 x 127 GB 硬碟</span><span class="sxs-lookup"><span data-stu-id="cd252-631">1 x 127-GB hard disk</span></span> <br/> |<span data-ttu-id="cd252-632">sp webservers</span><span class="sxs-lookup"><span data-stu-id="cd252-632">sp-webservers</span></span>  <br/> |<span data-ttu-id="cd252-633">WFE_SET</span><span class="sxs-lookup"><span data-stu-id="cd252-633">WFE_SET</span></span>  <br/> |
|<span data-ttu-id="cd252-634">亞利桑那州-APP1、 亞利桑那州-APP2、 亞利桑那州-APP3</span><span class="sxs-lookup"><span data-stu-id="cd252-634">AZ -APP1, AZ -APP2, AZ -APP3</span></span>  <br/> |<span data-ttu-id="cd252-635">應用程式伺服器</span><span class="sxs-lookup"><span data-stu-id="cd252-635">Application servers</span></span>  <br/> | <span data-ttu-id="cd252-636">A5 組態：</span><span class="sxs-lookup"><span data-stu-id="cd252-636">A5 configuration:</span></span> <br/>  <span data-ttu-id="cd252-637">2 個處理器</span><span class="sxs-lookup"><span data-stu-id="cd252-637">Two processors</span></span> <br/>  <span data-ttu-id="cd252-638">14 GB 的 RAM</span><span class="sxs-lookup"><span data-stu-id="cd252-638">14 GB of RAM</span></span> <br/>  <span data-ttu-id="cd252-639">1 x 127 GB 硬碟</span><span class="sxs-lookup"><span data-stu-id="cd252-639">1 x 127-GB hard disk</span></span> <br/> |<span data-ttu-id="cd252-640">sp applicationservers</span><span class="sxs-lookup"><span data-stu-id="cd252-640">sp-applicationservers</span></span>  <br/> |<span data-ttu-id="cd252-641">APP_SET</span><span class="sxs-lookup"><span data-stu-id="cd252-641">APP_SET</span></span>  <br/> |
|<span data-ttu-id="cd252-642">亞利桑那州-SQL-HA1、 亞利桑那州-SQL HA2</span><span class="sxs-lookup"><span data-stu-id="cd252-642">AZ -SQL-HA1, AZ -SQL-HA2</span></span>  <br/> |<span data-ttu-id="cd252-643">資料庫伺服器和 AlwaysOn 可用性群組的主要和次要複本</span><span class="sxs-lookup"><span data-stu-id="cd252-643">Database servers and primary and secondary replicas for AlwaysOn availability groups</span></span>  <br/> | <span data-ttu-id="cd252-644">A5 組態：</span><span class="sxs-lookup"><span data-stu-id="cd252-644">A5 configuration:</span></span> <br/>  <span data-ttu-id="cd252-645">2 個處理器</span><span class="sxs-lookup"><span data-stu-id="cd252-645">Two processors</span></span> <br/>  <span data-ttu-id="cd252-646">14 GB 的 RAM</span><span class="sxs-lookup"><span data-stu-id="cd252-646">14 GB of RAM</span></span> <br/> |<span data-ttu-id="cd252-647">sp databaseservers</span><span class="sxs-lookup"><span data-stu-id="cd252-647">sp-databaseservers</span></span>  <br/> |<span data-ttu-id="cd252-648">DATA_SET</span><span class="sxs-lookup"><span data-stu-id="cd252-648">DATA_SET</span></span>  <br/> |
   
### <a name="operations"></a><span data-ttu-id="cd252-649">Operations</span><span class="sxs-lookup"><span data-stu-id="cd252-649">Operations</span></span>

<span data-ttu-id="cd252-650">這些測試小組穩定的伺服器陣列環境並完成功能測試之後，啟動下列作業設定在內部復原環境所需的工作：</span><span class="sxs-lookup"><span data-stu-id="cd252-650">After the test team stabilized the farm environments and completed functional testing, they started the following operations tasks required to configure the on-premises recovery environment:</span></span>
  
- <span data-ttu-id="cd252-651">設定完整及差異備份。</span><span class="sxs-lookup"><span data-stu-id="cd252-651">Configure full and differential backups.</span></span>
    
- <span data-ttu-id="cd252-652">在內部部署環境及 Azure 環境之間傳送交易記錄檔的檔案伺服器上設定 DFSR。</span><span class="sxs-lookup"><span data-stu-id="cd252-652">Configure DFSR on the file servers that transfer transaction logs between the on-premises environment and the Azure environment.</span></span>
    
- <span data-ttu-id="cd252-653">設定記錄傳送的主要資料庫伺服器上。</span><span class="sxs-lookup"><span data-stu-id="cd252-653">Configure log shipping on the primary database server.</span></span>
    
- <span data-ttu-id="cd252-p177">穩定、 驗證及疑難排解所需的記錄傳送。這包含用來識別並記錄任何可能造成問題，例如網路延遲造成記錄傳送或 DFSR 檔案同步處理失敗的行為。</span><span class="sxs-lookup"><span data-stu-id="cd252-p177">Stabilize, validate, and troubleshoot log shipping, as required. This included identifying and documenting any behavior that might cause issues, such as network latency, which would cause log shipping or DFSR file synchronization failures.</span></span>
    
### <a name="databases"></a><span data-ttu-id="cd252-656">資料庫</span><span class="sxs-lookup"><span data-stu-id="cd252-656">Databases</span></span>

<span data-ttu-id="cd252-657">容錯移轉測試涉及下列資料庫：</span><span class="sxs-lookup"><span data-stu-id="cd252-657">Our failover tests involved the following databases:</span></span> 
  
- <span data-ttu-id="cd252-658">WSS_Content</span><span class="sxs-lookup"><span data-stu-id="cd252-658">WSS_Content</span></span>
    
- <span data-ttu-id="cd252-659">ManagedMetadata</span><span class="sxs-lookup"><span data-stu-id="cd252-659">ManagedMetadata</span></span>
    
- <span data-ttu-id="cd252-660">設定檔資料庫</span><span class="sxs-lookup"><span data-stu-id="cd252-660">Profile DB</span></span>
    
- <span data-ttu-id="cd252-661">同步處理資料庫</span><span class="sxs-lookup"><span data-stu-id="cd252-661">Sync DB</span></span>
    
- <span data-ttu-id="cd252-662">社交資料庫</span><span class="sxs-lookup"><span data-stu-id="cd252-662">Social DB</span></span>
    
- <span data-ttu-id="cd252-663">內容類型中樞 （專用的內容類型整合中樞的資料庫）</span><span class="sxs-lookup"><span data-stu-id="cd252-663">Content Type Hub (a database for a dedicated Content Type Syndication Hub)</span></span>
    
## <a name="troubleshooting-tips"></a><span data-ttu-id="cd252-664">疑難排解提示</span><span class="sxs-lookup"><span data-stu-id="cd252-664">Troubleshooting tips</span></span>

<span data-ttu-id="cd252-665">本節說明我們我們測試和其解決方案過程中遇到的問題。</span><span class="sxs-lookup"><span data-stu-id="cd252-665">The section explains the problems we encountered during our testing and their solutions.</span></span> 
  
### <a name="using-the-term-store-management-tool-caused-the-error-the-managed-metadata-store-or-connection-is-currently-not-available"></a><span data-ttu-id="cd252-666">使用字詞庫管理工具會導致錯誤發生、 」 的受管理的中繼資料存放區或連線目前無法使用。 」</span><span class="sxs-lookup"><span data-stu-id="cd252-666">Using the Term Store Management Tool caused the error, "The Managed Metadata Store or Connection is currently not available."</span></span>

<span data-ttu-id="cd252-667">確定 web 應用程式所使用的應用程式集區帳戶具有字詞儲存區權限的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="cd252-667">Ensure that the application pool account used by the web application has the Read Access to Term Store permission.</span></span>
  
### <a name="custom-term-sets-are-not-available-in-the-site-collection"></a><span data-ttu-id="cd252-668">自訂的字詞組中沒有提供網站集合</span><span class="sxs-lookup"><span data-stu-id="cd252-668">Custom term sets are not available in the site collection</span></span>

<span data-ttu-id="cd252-p178">檢查您的內容的網站集合與內容類型中樞之間遺失服務應用程式關聯。此外下,**受管理的中繼資料-<site collection name>連線**屬性螢幕，確定已啟用此選項：**此服務應用程式是欄特定字詞組的預設儲存位置。**</span><span class="sxs-lookup"><span data-stu-id="cd252-p178">Check for a missing service application association between your content site collection and your content type hub. In addition, under the **Managed Metadata - <site collection name> Connection** properties screen, make sure this option is enabled: **This service application is the default storage location for column specific term sets.**</span></span>
  
### <a name="the-get-adforest-windows-powershell-command-generates-the-error-the-term-get-adforest-is-not-recognized-as-the-name-of-a-cmdlet-function-script-file-or-operable-program"></a><span data-ttu-id="cd252-671">取得 ADForest Windows PowerShell 命令將會產生錯誤、"字詞 ' Get-ADForest' 不會被視為指令程式、 函數、 指令碼檔案或可執行的程式的名稱"。</span><span class="sxs-lookup"><span data-stu-id="cd252-671">The Get-ADForest Windows PowerShell command generates the error, "The term 'Get-ADForest' is not recognized as the name of a cmdlet, function, script file, or operable program."</span></span>

<span data-ttu-id="cd252-p179">設定經過使用者設定檔時，您需要 Active Directory 樹系名稱。在 [新增角色及功能精靈]，請確認您是否已啟用 Active Directory 的 Windows PowerShell 模組 (底下**遠端伺服器管理工具] > 角色系統管理工具] > AD DS 與 AD LDS 工具**] 區段中)。此外，執行下列命令，然後再使用**Get ADForest**以協助確保您會載入相依性的軟體。</span><span class="sxs-lookup"><span data-stu-id="cd252-p179">When setting up user profiles, you need the Active Directory forest name. In the Add Roles and Features Wizard, ensure that you have enabled the Active Directory Module for Windows PowerShell (under the **Remote Server Administration Tools>Role Administration Tools>AD DS and AD LDS Tools** section). In addition, run the following commands before using **Get-ADForest** to help ensure that your software dependencies are loaded.</span></span>
  
```
Import-module servermanager
Import-module activedirectory

```

### <a name="availability-group-creation-fails-at-starting-the-alwaysonhealth-xevent-session-on-server-name"></a><span data-ttu-id="cd252-675">在啟動上的 'AlwaysOn_health' XEvent 工作階段失敗的可用性群組建立 '<server name>'</span><span class="sxs-lookup"><span data-stu-id="cd252-675">Availability group creation fails at Starting the 'AlwaysOn_health' XEvent session on '<server name>'</span></span>

<span data-ttu-id="cd252-676">確保這兩個節點的容錯移轉叢集狀態"最多"並不"Paused"或"已停止 」。</span><span class="sxs-lookup"><span data-stu-id="cd252-676">Ensure that both nodes of your failover cluster are in the Status "Up" and not "Paused" or "Stopped".</span></span> 
  
### <a name="sql-server-log-shipping-job-fails-with-access-denied-error-trying-to-connect-to-the-file-share"></a><span data-ttu-id="cd252-677">SQL Server 記錄傳送工作失敗，拒絕存取錯誤嘗試連線的檔案共用</span><span class="sxs-lookup"><span data-stu-id="cd252-677">SQL Server log shipping job fails with access denied error trying to connect to the file share</span></span>

<span data-ttu-id="cd252-678">確定您的 SQL Server Agent 正在執行網路認證，而不是預設的認證。</span><span class="sxs-lookup"><span data-stu-id="cd252-678">Ensure that your SQL Server Agent is running under network credentials, instead of the default credentials.</span></span>
  
### <a name="sql-server-log-shipping-job-indicates-success-but-no-files-are-copied"></a><span data-ttu-id="cd252-679">SQL Server 記錄傳送工作表示成功，但沒有檔案複製</span><span class="sxs-lookup"><span data-stu-id="cd252-679">SQL Server log shipping job indicates success, but no files are copied</span></span>

<span data-ttu-id="cd252-p180">這是因為可用性群組的預設備份喜好設定為**次要偏好**。請確定您從可用性群組，而不是主要; 的次要伺服器執行記錄傳送工作否則，工作會以無訊息方式失敗。</span><span class="sxs-lookup"><span data-stu-id="cd252-p180">This happens because the default backup preference for an availability group is **Prefer Secondary**. Ensure that you run the log shipping job from the secondary server for the availability group instead of the primary; otherwise, the job will fail silently.</span></span> 
  
### <a name="managed-metadata-service-or-other-sharepoint-service-fails-to-start-automatically-after-installation"></a><span data-ttu-id="cd252-682">若要安裝後自動啟動失敗的受管理的中繼資料服務 （或其他 SharePoint service）</span><span class="sxs-lookup"><span data-stu-id="cd252-682">Managed Metadata service (or other SharePoint service) fails to start automatically after installation</span></span>

<span data-ttu-id="cd252-p181">服務可能需要數分鐘才能啟動，請根據的效能和目前的 SharePoint Server 的負載。手動服務中按一下 [**開始]** ，並提供適當時間啟動時有時會重新整理 [伺服器] 畫面上的服務監視其狀態。此服務會維持已停止，以免讓 SharePoint 診斷記錄、 嘗試重新啟動服務，然後檢查錯誤的記錄檔。如需詳細資訊，請參閱 ＜ [Configure diagnostic logging in SharePoint 2013](https://docs.microsoft.com/sharepoint/administration/configure-diagnostic-logging)</span><span class="sxs-lookup"><span data-stu-id="cd252-p181">Services might take several minutes to start, depending on the performance and current load of your SharePoint Server. Manually click **Start** for the service and provide adequate time for startup while occasionally refreshing the Services on Server screen to monitor its status. In case the service remains stopped, enable SharePoint diagnostic logging, attempt to start the service again, and then check the log for errors. For more information, see [Configure diagnostic logging in SharePoint 2013](https://docs.microsoft.com/sharepoint/administration/configure-diagnostic-logging)</span></span>
  
### <a name="after-changing-dns-to-the-azure-failover-environment-client-browsers-continue-to-use-the-old-ip-address-for-the-sharepoint-site"></a><span data-ttu-id="cd252-687">變更 DNS Azure 容錯移轉環境之後的, 用戶端瀏覽器繼續使用舊的 IP 位址的 SharePoint 網站</span><span class="sxs-lookup"><span data-stu-id="cd252-687">After changing DNS to the Azure failover environment, client browsers continue to use the old IP address for the SharePoint site</span></span>

<span data-ttu-id="cd252-p182">您的 DNS 變更可能不是所有用戶端可以看到立即。在測試用戶端上從提升權限的命令提示字元執行下列命令並嘗試再次存取網站。</span><span class="sxs-lookup"><span data-stu-id="cd252-p182">Your DNS change might not be visible to all clients immediately. On a test client, perform the following command from an elevated command prompt and attempt to access the site again.</span></span>
  
```
Ipconfig /flushdns
```

## <a name="additional-resources"></a><span data-ttu-id="cd252-690">其他資源</span><span class="sxs-lookup"><span data-stu-id="cd252-690">Additional resources</span></span>

[<span data-ttu-id="cd252-691">SharePoint 資料庫支援的高可用性和災害復原選項</span><span class="sxs-lookup"><span data-stu-id="cd252-691">Supported high availability and disaster recovery options for SharePoint databases</span></span>](https://docs.microsoft.com/sharepoint/administration/supported-high-availability-and-disaster-recovery-options-for-sharepoint-databas)
  
[<span data-ttu-id="cd252-692">設定 SharePoint 2013 的 SQL Server 2012 AlwaysOn 可用性群組</span><span class="sxs-lookup"><span data-stu-id="cd252-692">Configure SQL Server 2012 AlwaysOn Availability Groups for SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=393122)
  
## <a name="see-also"></a><span data-ttu-id="cd252-693">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd252-693">See Also</span></span>

[<span data-ttu-id="cd252-694">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="cd252-694">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)



