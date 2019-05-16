---
title: 易於存取的圖表-Microsoft Azure 的 SharePoint 嚴重損壞修復
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 4b855224-8e67-4efa-a3a4-908ee0ca6412
description: 本文是圖表的名為 Microsoft Azure 的 SharePoint 嚴重損壞修復易於存取的文字版本。
ms.openlocfilehash: d7df0f44dd4e7f0cbb8580029991bc9280892afb
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068519"
---
# <a name="accessible-diagram---sharepoint-disaster-recovery-to-microsoft-azure"></a><span data-ttu-id="c5a0f-103">易於存取的圖表-Microsoft Azure 的 SharePoint 嚴重損壞修復</span><span class="sxs-lookup"><span data-stu-id="c5a0f-103">Accessible diagram - SharePoint Disaster Recovery to Microsoft Azure</span></span>

<span data-ttu-id="c5a0f-104">**摘要：** 本文是圖表的名為 Microsoft Azure 的 SharePoint 嚴重損壞修復易於存取的文字版本。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-104">**Summary:** This article is an accessible text version of the diagram named SharePoint Disaster Recovery to Microsoft Azure.</span></span>
  
<span data-ttu-id="c5a0f-105">此海報提供架構的範例建置在 Azure 中的復原環境。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-105">This poster provides examples of architectures for building a recovery environment in Azure.</span></span> 
  
## <a name="on-premises-environment-with-an-azure-recovery-environment"></a><span data-ttu-id="c5a0f-106">內部部署環境與 Azure 復原環境</span><span class="sxs-lookup"><span data-stu-id="c5a0f-106">On-premises environment with an Azure recovery environment</span></span>

<span data-ttu-id="c5a0f-107">此圖顯示用於復原使用 Azure 的內部部署環境的實際執行環境的架構的範例。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-107">The diagram shows an example of architecture used for the production environment of an on-premises environment that uses Azure for recovery.</span></span> 
  
### <a name="on-premises-production-environment"></a><span data-ttu-id="c5a0f-108">內部部署實際執行環境</span><span class="sxs-lookup"><span data-stu-id="c5a0f-108">On-premises production environment</span></span>

<span data-ttu-id="c5a0f-109">隨附圖表顯示四個層級的伺服器的實際生產環境中伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-109">The accompanying diagram shows a live production environment with four tiers of servers in a server farm.</span></span> 
  
#### <a name="tier-1"></a><span data-ttu-id="c5a0f-110">第 1 層</span><span class="sxs-lookup"><span data-stu-id="c5a0f-110">Tier 1</span></span>

<span data-ttu-id="c5a0f-111">有兩部伺服器的前端服務與查詢處理。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-111">There are two servers for front-end services and query processing.</span></span> <span data-ttu-id="c5a0f-112">沒有提供兩部伺服器複本的索引分割區。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-112">There is an index partition that provides a replica of both servers.</span></span> 
  
#### <a name="tier-2"></a><span data-ttu-id="c5a0f-113">第 2 層</span><span class="sxs-lookup"><span data-stu-id="c5a0f-113">Tier 2</span></span>

<span data-ttu-id="c5a0f-114">有兩部伺服器，在這一層中的分散式快取。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-114">There are two servers for distributed cache in this tier.</span></span> 
  
#### <a name="tier-3"></a><span data-ttu-id="c5a0f-115">第 3 層</span><span class="sxs-lookup"><span data-stu-id="c5a0f-115">Tier 3</span></span>

<span data-ttu-id="c5a0f-116">在這一層中有三部伺服器。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-116">There are three servers in this tier.</span></span> <span data-ttu-id="c5a0f-117">每一部伺服器會提供下列服務：</span><span class="sxs-lookup"><span data-stu-id="c5a0f-117">Each server provides the following services:</span></span> 
  
- <span data-ttu-id="c5a0f-118">後端服務</span><span class="sxs-lookup"><span data-stu-id="c5a0f-118">Backend services</span></span> 
    
- <span data-ttu-id="c5a0f-119">系統管理</span><span class="sxs-lookup"><span data-stu-id="c5a0f-119">Admin</span></span> 
    
- <span data-ttu-id="c5a0f-120">工作流程管理員</span><span class="sxs-lookup"><span data-stu-id="c5a0f-120">Workflow manager</span></span> 
    
- <span data-ttu-id="c5a0f-121">編目</span><span class="sxs-lookup"><span data-stu-id="c5a0f-121">Crawl</span></span> 
    
- <span data-ttu-id="c5a0f-122">內容處理</span><span class="sxs-lookup"><span data-stu-id="c5a0f-122">Content processing</span></span> 
    
- <span data-ttu-id="c5a0f-123">分析</span><span class="sxs-lookup"><span data-stu-id="c5a0f-123">Analytics</span></span> 
    
#### <a name="tier-4"></a><span data-ttu-id="c5a0f-124">第 4 層</span><span class="sxs-lookup"><span data-stu-id="c5a0f-124">Tier 4</span></span>

<span data-ttu-id="c5a0f-125">在這一層中有兩部伺服器。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-125">There are two servers in this tier.</span></span> <span data-ttu-id="c5a0f-126">這兩個伺服器有三個可用性群組，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c5a0f-126">Both servers have three availability groups, as follows:</span></span> 
  
- <span data-ttu-id="c5a0f-127">可用性群組 #1 提供搜尋功能。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-127">Availability group #1 provides search capabilities.</span></span> 
    
- <span data-ttu-id="c5a0f-128">可用性群組 #2 提供內容、 設定及服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-128">Availability group #2 provides content, configuration, and service applications.</span></span> 
    
- <span data-ttu-id="c5a0f-129">可用性群組 #3 提供內容。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-129">Availability group #3 provides content.</span></span> 
    
<span data-ttu-id="c5a0f-130">另外還有檔案共用中這一層的伺服器。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-130">There is also a file sharing server in this tier.</span></span> <span data-ttu-id="c5a0f-131">第 4 層伺服器使用記錄傳送與此伺服器進行通訊。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-131">The tier 4 servers use log shipping to communicate with this server.</span></span> <span data-ttu-id="c5a0f-132">此伺服器]，依序進行通訊透過分散式檔案系統複寫 (DFSR) 檔案共用伺服器在 Azure 暖待命復原環境中下, 一節所述。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-132">This server, in turn, communicates over Distributed File System Replication (DFSR) to a file share server in the Azure warm standby recovery environment, as described in the following section.</span></span> 
  
### <a name="azure-recovery-environment"></a><span data-ttu-id="c5a0f-133">Azure 復原環境</span><span class="sxs-lookup"><span data-stu-id="c5a0f-133">Azure recovery environment</span></span>

#### <a name="warm-standby-environment-running-virtual-machines"></a><span data-ttu-id="c5a0f-134">執行虛擬機器的暖待命環境</span><span class="sxs-lookup"><span data-stu-id="c5a0f-134">Warm standby environment running virtual machines</span></span>

<span data-ttu-id="c5a0f-135">隨附圖顯示 Azure 復原環境中完全複寫內部部署環境。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-135">The accompanying diagram shows the on-premises environment replicated exactly in the Azure recovery environment.</span></span> <span data-ttu-id="c5a0f-136">在此環境中的檔案共用伺服器會連結到 DFSR 透過內部部署環境。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-136">The file share server in this environment is linked to the on-premises environment through DFSR.</span></span> <span data-ttu-id="c5a0f-137">DFSR 會將記錄從實際執行環境傳送到透過檔案共用伺服器在復原環境。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-137">DFSR transfers logs from the production environment to the recovery environment through the file share server.</span></span> 
  
### <a name="overview"></a><span data-ttu-id="c5a0f-138">概觀</span><span class="sxs-lookup"><span data-stu-id="c5a0f-138">Overview</span></span>

<span data-ttu-id="c5a0f-139">內部部署 SharePoint 2013 伺服器陣列的災害復原環境可裝載於 Azure 中。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-139">The disaster recovery environment for an on-premises SharePoint 2013 farm can be hosted in Azure.</span></span> 
  
-  <span data-ttu-id="c5a0f-140">Azure 基礎結構服務提供的次要資料中心。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-140">Azure Infrastructure Services provides a secondary datacenter.</span></span>
    
- <span data-ttu-id="c5a0f-141">僅支付您使用的資源。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-141">Pay only for the resources you use.</span></span> 
    
- <span data-ttu-id="c5a0f-142">小型的復原伺服器陣列可以向外延展以滿足擴充與容量目標的嚴重損壞後。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-142">Small recovery farms can be scaled out after a disaster to meet scale and capacity targets.</span></span> 
    
<span data-ttu-id="c5a0f-143">在 Azure 中的復原伺服器陣列已設定為進行完全相同，儘可能在實際執行內部部署伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-143">The recovery farm in Azure is configured as identically as possible to the production on-premises farm.</span></span> 
  
- <span data-ttu-id="c5a0f-144">相同的伺服器角色的表示法。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-144">Same representation of server roles.</span></span> 
    
- <span data-ttu-id="c5a0f-145">相同的自訂設定的詳細組態。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-145">Same configuration of customizations.</span></span> 
    
- <span data-ttu-id="c5a0f-146">相同的搜尋功能 （這些可以是在實際執行伺服器陣列較小版） 的詳細組態。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-146">Same configuration of search features (these can be on a smaller version of the production farm).</span></span> 
    
<span data-ttu-id="c5a0f-147">記錄傳送和 DFSR 可用來將資料庫備份和交易記錄檔複製到 Azure 的伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-147">Log shipping and DFSR are used to copy database backups and transaction logs to the Azure farm.</span></span> 
  
- <span data-ttu-id="c5a0f-148">DFSR 用來從實際執行環境傳送記錄檔，以在復原環境。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-148">DFSR is used to transfer logs from the production environment to the recovery environment.</span></span> <span data-ttu-id="c5a0f-149">在 WAN 案例中，DFSR 比直接將記錄傳送至 Azure 中的次要伺服器更為有效率。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-149">In a WAN scenario, DFSR is more efficient than shipping the logs directly to the secondary server in Azure.</span></span> 
    
- <span data-ttu-id="c5a0f-150">記錄檔會重新顯示至以 Azure 為基礎的 SQL Server 電腦。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-150">Logs are replayed to the Azure-based SQL Server computers.</span></span> 
    
- <span data-ttu-id="c5a0f-151">除非執行復原練習，否則，記錄傳送資料庫不會附加至伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-151">Log-shipped databases are not attached to the farm until a recovery exercise is performed.</span></span> 
    
<span data-ttu-id="c5a0f-152">容錯移轉程序：</span><span class="sxs-lookup"><span data-stu-id="c5a0f-152">Failover procedures:</span></span> 
  
1. <span data-ttu-id="c5a0f-153">停止記錄傳送。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-153">Stop log shipping.</span></span> 
    
2. <span data-ttu-id="c5a0f-154">停止接受主要伺服器陣列的流量。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-154">Stop accepting traffic to the primary farm.</span></span> 
    
3. <span data-ttu-id="c5a0f-155">重新顯示的最後一筆交易記錄檔。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-155">Replay the final transaction logs.</span></span> 
    
4. <span data-ttu-id="c5a0f-156">將內容資料庫附加至伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-156">Attach the content databases to the farm.</span></span> 
    
5. <span data-ttu-id="c5a0f-157">開始完整編目。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-157">Start a full crawl.</span></span> 
    
6. <span data-ttu-id="c5a0f-158">複寫的服務資料庫還原服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-158">Restore service applications from the replicated services databases.</span></span> 
    
<span data-ttu-id="c5a0f-159">此解決方案所提供的復原目標包括：</span><span class="sxs-lookup"><span data-stu-id="c5a0f-159">Recovery objectives provided by this solution include:</span></span> 
  
- <span data-ttu-id="c5a0f-160">網站和內容</span><span class="sxs-lookup"><span data-stu-id="c5a0f-160">Sites and content</span></span> 
    
- <span data-ttu-id="c5a0f-161">搜尋 （重新編目，沒有搜尋歷程記錄）</span><span class="sxs-lookup"><span data-stu-id="c5a0f-161">Search (re-crawled, no search history)</span></span> 
    
- <span data-ttu-id="c5a0f-162">服務</span><span class="sxs-lookup"><span data-stu-id="c5a0f-162">Services</span></span>
    
<span data-ttu-id="c5a0f-163">可以 Microsoft 諮詢服務或協力廠商所提到的其他項目：</span><span class="sxs-lookup"><span data-stu-id="c5a0f-163">Additional items that can be addressed by Microsoft Consulting Services or a partner:</span></span> 
  
- <span data-ttu-id="c5a0f-164">同步處理自訂伺服器陣列解決方案</span><span class="sxs-lookup"><span data-stu-id="c5a0f-164">Synchronizing custom farm solutions</span></span> 
    
- <span data-ttu-id="c5a0f-165">內部部署 （Business Data Connectivity (BDC) 和搜尋內容來源） 的資料來源的連線</span><span class="sxs-lookup"><span data-stu-id="c5a0f-165">Connections to data sources on premises (Business Data Connectivity (BDC) and search content sources)</span></span> 
    
- <span data-ttu-id="c5a0f-166">搜尋還原案例</span><span class="sxs-lookup"><span data-stu-id="c5a0f-166">Search restore scenarios</span></span> 
    
- <span data-ttu-id="c5a0f-167">復原時間目標 (RTO) 和復原點目標 (RPO)</span><span class="sxs-lookup"><span data-stu-id="c5a0f-167">Recovery Time Objectives (RTO) and Recovery Point Objectives (RPO)</span></span> 
    
#### <a name="cold-standby-environment-running-virtual-machines"></a><span data-ttu-id="c5a0f-168">執行虛擬機器的冷待命環境</span><span class="sxs-lookup"><span data-stu-id="c5a0f-168">Cold standby environment running virtual machines</span></span>

<span data-ttu-id="c5a0f-169">冷待命環境需要較長的時間開始，但會較不昂貴。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-169">Cold standby environments take longer to start but are less expensive.</span></span> 
  
- <span data-ttu-id="c5a0f-170">完全建置在伺服器陣列，但會在建立伺服器陣列之後，會停止虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-170">The farm is fully built, but the virtual machines are stopped after the farm is created.</span></span> <span data-ttu-id="c5a0f-171">當執行虛擬機器，但儲存和網路資料傳輸成本套用支付只處理成本。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-171">You pay only processing costs when the virtual machines are running, but storage and network data transfer costs apply.</span></span> 
    
- <span data-ttu-id="c5a0f-172">發生災害時，伺服器陣列中的所有虛擬機器已啟動並修正的項目。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-172">In the event of a disaster, all the virtual machines in the farm are started and patched.</span></span> 
    
- <span data-ttu-id="c5a0f-173">備份和交易記錄檔會套用至伺服器陣列資料庫。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-173">Backups and transaction logs are applied to the farm databases.</span></span> 
    
<span data-ttu-id="c5a0f-174">下列清單說明冷待命環境的其他程序：</span><span class="sxs-lookup"><span data-stu-id="c5a0f-174">The following list describes additional procedures for cold standby environments:</span></span> 
  
- <span data-ttu-id="c5a0f-175">開啟虛擬機器定期修補程式、 更新及驗證環境。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-175">Turn on virtual machines regularly to patch, update, and verify the environment.</span></span> 
    
- <span data-ttu-id="c5a0f-176">執行程序來重新整理 DNS 和 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-176">Run procedures to refresh DNS and IP addresses.</span></span> 
    
- <span data-ttu-id="c5a0f-177">設定 SQL AlwaysOn 容錯移轉後。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-177">Set up SQL AlwaysOn after a failover.</span></span> 
    
<span data-ttu-id="c5a0f-178">隨附圖表會顯示在虛擬機器上的複寫的復原環境。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-178">The accompanying diagram shows a replicated recovery environment on virtual machines.</span></span> <span data-ttu-id="c5a0f-179">容錯移轉之後以冷待命環境，並啟動所有虛擬機器，並使用重新顯示記錄檔若要使用的資料庫伺服器設定可用性群組。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-179">After failover to a cold standby environment, all virtual machines are started, and the availability groups are configured using replay logs to make the database servers available.</span></span> 
  
## <a name="sharepoint-recovery-environment-in-azure"></a><span data-ttu-id="c5a0f-180">Azure 中 SharePoint 復原環境</span><span class="sxs-lookup"><span data-stu-id="c5a0f-180">SharePoint recovery environment in Azure</span></span>

<span data-ttu-id="c5a0f-181">設計與建置在 Azure 中的容錯移轉環境。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-181">Design and build the failover environment in Azure.</span></span> 
  
- <span data-ttu-id="c5a0f-182">在 Azure 中建立虛擬網路。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-182">Create a virtual network in Azure.</span></span> 
    
- <span data-ttu-id="c5a0f-183">會連接內部部署網路與在 Azure 中的虛擬網路與站台對站 VPN 連線。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-183">Connect the on-premises network with the virtual network in Azure with a site-to-site VPN connection.</span></span> <span data-ttu-id="c5a0f-184">這個連線在 Azure 中使用動態的閘道。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-184">This connection uses a dynamic gateway in Azure.</span></span> 
    
- <span data-ttu-id="c5a0f-185">一或多個網域控制站部署到 Azure 虛擬網路，並設定這些能搭配您的內部部署網域。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-185">Deploy one or more domain controllers to the Azure virtual network, and configure these to work with your on-premises domain.</span></span> <span data-ttu-id="c5a0f-186">這些網域控制站的目錄伺服器。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-186">These domain controllers are catalog servers.</span></span> 
    
- <span data-ttu-id="c5a0f-187">調整雲端服務和可用性設定的 SharePoint 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-187">Adapt the SharePoint farm for cloud services and availability sets.</span></span> 
    
- <span data-ttu-id="c5a0f-188">將 SharePoint 伺服器陣列加上的檔案伺服器部署至主機檔案共用。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-188">Deploy the SharePoint farm plus a file server to host file shares.</span></span> 
    
- <span data-ttu-id="c5a0f-189">設定記錄傳送和 DFSR，內部部署環境與 「 以 Azure 為基礎的復原環境之間。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-189">Set up log shipping and DFSR between the on-premises environment and the Azure-based recovery environment.</span></span> 
    
<span data-ttu-id="c5a0f-190">隨附的圖顯示內部部署環境及 Azure 虛擬網路，包含下列功能：</span><span class="sxs-lookup"><span data-stu-id="c5a0f-190">The accompanying diagram shows the on-premises environment and the Azure virtual network with the following features:</span></span> 
  
### <a name="on-premises-environment"></a><span data-ttu-id="c5a0f-191">內部部署環境</span><span class="sxs-lookup"><span data-stu-id="c5a0f-191">On-premises environment</span></span>

- <span data-ttu-id="c5a0f-192">Windows Server 2012 RRAS</span><span class="sxs-lookup"><span data-stu-id="c5a0f-192">Windows Server 2012 RRAS</span></span> 
    
- <span data-ttu-id="c5a0f-193">Active Directory 伺服器</span><span class="sxs-lookup"><span data-stu-id="c5a0f-193">Active Directory server</span></span> 
    
<span data-ttu-id="c5a0f-194">透過虛擬私人網路 (VPN) 閘道的 Azure 虛擬網路與在內部網路介面。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-194">The on-premises network interfaces with the Azure virtual network over a virtual private network (VPN) gateway.</span></span> 
  
### <a name="azure-virtual-network"></a><span data-ttu-id="c5a0f-195">Azure 虛擬網路</span><span class="sxs-lookup"><span data-stu-id="c5a0f-195">Azure virtual network</span></span>

<span data-ttu-id="c5a0f-196">VPN 閘道介面與作用中的 VPN 閘道子網路。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-196">The VPN gateway interfaces with an active VPN gateway subnet.</span></span> 
  
<span data-ttu-id="c5a0f-197">在 Azure 虛擬網路中有三個雲端服務：</span><span class="sxs-lookup"><span data-stu-id="c5a0f-197">There are three cloud services in the Azure virtual network:</span></span> 
  
- <span data-ttu-id="c5a0f-198">第一個雲端服務有兩個 Active Directory 和 DNS 伺服器的可用性與設定。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-198">The first cloud service has two Active Directory and DNS servers with an availability set.</span></span> 
    
- <span data-ttu-id="c5a0f-199">第二個雲端服務有三個一組伺服器： 兩個分散式快取伺服器的可用性設定組。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-199">The second cloud service has three sets of servers: Two distributed cache servers with an availability set.</span></span> <span data-ttu-id="c5a0f-200">可用性設定組與兩部前端伺服器。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-200">Two front-end servers with an availability set.</span></span> <span data-ttu-id="c5a0f-201">具有一個可用性設定組的三個後端伺服器。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-201">Three backend servers with an availability set.</span></span>
    
- <span data-ttu-id="c5a0f-202">第三個雲端服務有三個具有一個可用性設定組的資料庫伺服器。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-202">The third cloud service has three database servers with an availability set.</span></span> <span data-ttu-id="c5a0f-203">一種資料庫伺服器是記錄傳送和第三個節點的 SQL Server AlwaysOn 節點多數 」 的檔案共用。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-203">One of these database servers is a file share for log shipping and a third node of a node majority for SQL Server AlwaysOn.</span></span> 
    
### <a name="build-the-ad-ds-hybrid-environment"></a><span data-ttu-id="c5a0f-204">建立在 AD DS 混合式環境</span><span class="sxs-lookup"><span data-stu-id="c5a0f-204">Build the AD DS hybrid environment</span></span>

<span data-ttu-id="c5a0f-205">針對此解決方案的 AD ds 設定構成了 AD DS 是部分是部署在內部和部分是在 Azure 虛擬機器上部署的混合式部署案例。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-205">The configuration of AD DS for this solution constitutes a hybrid deployment scenario in which AD DS is partly deployed on-premises and partly deployed on Azure virtual machines.</span></span> 
  
<span data-ttu-id="c5a0f-206">重要事項 — 部署在 Azure 中的 AD DS 之前，請閱讀指導方針部署 Windows Server Active directory 上的 Microsoft Azure 虛擬機器 (http://msdn.microsoft.com/en-us/library/windowsazure/jj156090.aspx)。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-206">Important — Before you deploy AD DS in Azure, read Guidelines for Deploying Windows Server Active Directory on Microsoft Azure Virtual Machines (http://msdn.microsoft.com/en-us/library/windowsazure/jj156090.aspx).</span></span> 
  
<span data-ttu-id="c5a0f-207">如需設計及部署 Active Directory 環境的完整指導，請參閱http://TechNet.microsoft.com。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-207">For complete guidance on designing and deploying Active Directory environments, see http://TechNet.microsoft.com.</span></span> 
  
<span data-ttu-id="c5a0f-208">本參考架構包含兩部虛擬機器設定為網域控制站。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-208">This reference architecture includes two virtual machines configured as domain controllers.</span></span> <span data-ttu-id="c5a0f-209">每個已設定為，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c5a0f-209">Each is configured as follows:</span></span> 
  
- <span data-ttu-id="c5a0f-210">大小 — 小。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-210">Size — Small.</span></span> 
    
- <span data-ttu-id="c5a0f-211">作業系統： Windows Server 2012。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-211">Operating system — Windows Server 2012.</span></span> 
    
- <span data-ttu-id="c5a0f-212">角色 — AD DS 網域控制站指定為通用類別目錄伺服器。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-212">Role — AD DS domain controller designated as a global catalog server.</span></span> <span data-ttu-id="c5a0f-213">此組態會減少輸出流量透過 VPN 連線。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-213">This configuration reduces egress traffic across the VPN connection.</span></span> <span data-ttu-id="c5a0f-214">在變更速率高的多重網域環境，設定網域控制站上內部與在 Azure 中的通用類別目錄伺服器不同步。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-214">In a multi-domain environment with high rates of change, configure domain controllers on-premises to not sync with the global catalog servers in Azure.</span></span> 
    
- <span data-ttu-id="c5a0f-215">資料磁碟 — 將 AD DS 資料庫、 記錄檔及 SYSVOL 放在 Azure 的資料磁碟上。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-215">Data disks — Place the AD DS database, logs, and SYSVOL on Azure data disks.</span></span> <span data-ttu-id="c5a0f-216">不放置這些作業系統的磁碟或 Azure 所提供的暫存磁碟上。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-216">Do not place these on the operating system disk or the temporary disks provided by Azure.</span></span> <span data-ttu-id="c5a0f-217">這是很重要。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-217">This is important.</span></span> 
    
- <span data-ttu-id="c5a0f-218">角色 — 上安裝及設定 Windows DNS 網域控制站。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-218">Role — Install and configure Windows DNS on the domain controllers.</span></span> 
    
- <span data-ttu-id="c5a0f-219">IP 位址-使用動態 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-219">IP addresses — Use dynamic IP addresses.</span></span> <span data-ttu-id="c5a0f-220">這需要您建立 Azure 虛擬網路。</span><span class="sxs-lookup"><span data-stu-id="c5a0f-220">This requires you to create an Azure Virtual Network.</span></span> 
    

