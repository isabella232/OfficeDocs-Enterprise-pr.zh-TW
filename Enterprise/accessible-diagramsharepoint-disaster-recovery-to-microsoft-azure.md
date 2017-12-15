---
title: "存取圖表-至 Microsoft Azure 的 SharePoint 災害復原"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 4b855224-8e67-4efa-a3a4-908ee0ca6412
description: "本文是圖表的名為至 Microsoft Azure 的 SharePoint 災害復原可存取的文字版本。"
ms.openlocfilehash: 2babb1910b0cd8dcbfe4cc0bf32de7c714c05fc0
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="accessible-diagram---sharepoint-disaster-recovery-to-microsoft-azure"></a><span data-ttu-id="ffd72-103">存取圖表-至 Microsoft Azure 的 SharePoint 災害復原</span><span class="sxs-lookup"><span data-stu-id="ffd72-103">Accessible diagram - SharePoint Disaster Recovery to Microsoft Azure</span></span>

<span data-ttu-id="ffd72-104">**摘要：**本文是圖表的名為至 Microsoft Azure 的 SharePoint 災害復原可存取的文字版本。</span><span class="sxs-lookup"><span data-stu-id="ffd72-104">**Summary:** This article is an accessible text version of the diagram named SharePoint Disaster Recovery to Microsoft Azure.</span></span>
  
<span data-ttu-id="ffd72-105">此海報提供可用以建置 Azure 中的復原環境架構的範例。</span><span class="sxs-lookup"><span data-stu-id="ffd72-105">This poster provides examples of architectures for building a recovery environment in Azure.</span></span> 
  
## <a name="on-premises-environment-with-an-azure-recovery-environment"></a><span data-ttu-id="ffd72-106">使用 Azure 復原環境的內部部署環境</span><span class="sxs-lookup"><span data-stu-id="ffd72-106">On-premises environment with an Azure recovery environment</span></span>

<span data-ttu-id="ffd72-107">此圖顯示用於復原使用 Azure 的內部部署環境的實際執行環境的架構的範例。</span><span class="sxs-lookup"><span data-stu-id="ffd72-107">The diagram shows an example of architecture used for the production environment of an on-premises environment that uses Azure for recovery.</span></span> 
  
### <a name="on-premises-production-environment"></a><span data-ttu-id="ffd72-108">內部部署實際執行環境</span><span class="sxs-lookup"><span data-stu-id="ffd72-108">On-premises production environment</span></span>

<span data-ttu-id="ffd72-109">隨附顯示 live 實際執行環境的圖表具有四個層的伺服器在伺服器陣列中。</span><span class="sxs-lookup"><span data-stu-id="ffd72-109">The accompanying diagram shows a live production environment with four tiers of servers in a server farm.</span></span> 
  
#### <a name="tier-1"></a><span data-ttu-id="ffd72-110">第 1 層</span><span class="sxs-lookup"><span data-stu-id="ffd72-110">Tier 1</span></span>

<span data-ttu-id="ffd72-p101">有兩部前端服務和查詢處理伺服器。有提供兩部伺服器複本的索引磁碟分割。</span><span class="sxs-lookup"><span data-stu-id="ffd72-p101">There are two servers for front-end services and query processing. There is an index partition that provides a replica of both servers.</span></span> 
  
#### <a name="tier-2"></a><span data-ttu-id="ffd72-113">第 2 層</span><span class="sxs-lookup"><span data-stu-id="ffd72-113">Tier 2</span></span>

<span data-ttu-id="ffd72-114">有兩部伺服器的這一層中的分散式快取。</span><span class="sxs-lookup"><span data-stu-id="ffd72-114">There are two servers for distributed cache in this tier.</span></span> 
  
#### <a name="tier-3"></a><span data-ttu-id="ffd72-115">第 3 層</span><span class="sxs-lookup"><span data-stu-id="ffd72-115">Tier 3</span></span>

<span data-ttu-id="ffd72-p102">在此層中有三部伺服器。每個 server 提供下列服務：</span><span class="sxs-lookup"><span data-stu-id="ffd72-p102">There are three servers in this tier. Each server provides the following services:</span></span> 
  
- <span data-ttu-id="ffd72-118">後端服務</span><span class="sxs-lookup"><span data-stu-id="ffd72-118">Backend services</span></span> 
    
- <span data-ttu-id="ffd72-119">管理員</span><span class="sxs-lookup"><span data-stu-id="ffd72-119">Admin</span></span> 
    
- <span data-ttu-id="ffd72-120">工作流程管理員</span><span class="sxs-lookup"><span data-stu-id="ffd72-120">Workflow manager</span></span> 
    
- <span data-ttu-id="ffd72-121">編目</span><span class="sxs-lookup"><span data-stu-id="ffd72-121">Crawl</span></span> 
    
- <span data-ttu-id="ffd72-122">內容處理</span><span class="sxs-lookup"><span data-stu-id="ffd72-122">Content processing</span></span> 
    
- <span data-ttu-id="ffd72-123">分析</span><span class="sxs-lookup"><span data-stu-id="ffd72-123">Analytics</span></span> 
    
#### <a name="tier-4"></a><span data-ttu-id="ffd72-124">第 4 層</span><span class="sxs-lookup"><span data-stu-id="ffd72-124">Tier 4</span></span>

<span data-ttu-id="ffd72-p103">在此層中有兩部伺服器。這兩個伺服器有三個可用性群組，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ffd72-p103">There are two servers in this tier. Both servers have three availability groups, as follows:</span></span> 
  
- <span data-ttu-id="ffd72-127">可用性群組 #1 可提供搜尋功能。</span><span class="sxs-lookup"><span data-stu-id="ffd72-127">Availability group #1 provides search capabilities.</span></span> 
    
- <span data-ttu-id="ffd72-128">可用性群組 #2 提供內容、 設定及服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="ffd72-128">Availability group #2 provides content, configuration, and service applications.</span></span> 
    
- <span data-ttu-id="ffd72-129">可用性群組 #3 提供內容。</span><span class="sxs-lookup"><span data-stu-id="ffd72-129">Availability group #3 provides content.</span></span> 
    
<span data-ttu-id="ffd72-p104">也有檔案共用中這一層的伺服器。第 4 層的伺服器使用記錄傳送至與此伺服器通訊。此伺服器依次透過分散式檔案系統複寫 (DFSR) 檔案共用與伺服器通訊時在 Azure 暖待命復原環境中下, 一節所述。</span><span class="sxs-lookup"><span data-stu-id="ffd72-p104">There is also a file sharing server in this tier. The tier 4 servers use log shipping to communicate with this server. This server, in turn, communicates over Distributed File System Replication (DFSR) to a file share server in the Azure warm standby recovery environment, as described in the following section.</span></span> 
  
### <a name="azure-recovery-environment"></a><span data-ttu-id="ffd72-133">Azure 復原環境</span><span class="sxs-lookup"><span data-stu-id="ffd72-133">Azure recovery environment</span></span>

#### <a name="warm-standby-environment-running-virtual-machines"></a><span data-ttu-id="ffd72-134">虛擬機器中執行的暖待命環境</span><span class="sxs-lookup"><span data-stu-id="ffd72-134">Warm standby environment running virtual machines</span></span>

<span data-ttu-id="ffd72-p105">隨附圖剛好在 Azure 復原環境中複製的內部部署環境。此環境中的檔案共用伺服器所連結到 DFSR 的內部部署環境。DFSR 會傳送到透過檔案共用伺服器復原環境的實際執行環境中的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="ffd72-p105">The accompanying diagram shows the on-premises environment replicated exactly in the Azure recovery environment. The file share server in this environment is linked to the on-premises environment through DFSR. DFSR transfers logs from the production environment to the recovery environment through the file share server.</span></span> 
  
### <a name="overview"></a><span data-ttu-id="ffd72-138">概觀</span><span class="sxs-lookup"><span data-stu-id="ffd72-138">Overview</span></span>

<span data-ttu-id="ffd72-139">在內部部署 SharePoint 2013 伺服器陣列嚴重損壞修復環境可以裝載於 Azure。</span><span class="sxs-lookup"><span data-stu-id="ffd72-139">The disaster recovery environment for an on-premises SharePoint 2013 farm can be hosted in Azure.</span></span> 
  
-  <span data-ttu-id="ffd72-140">Azure 基礎結構服務提供次要資料中心。</span><span class="sxs-lookup"><span data-stu-id="ffd72-140">Azure Infrastructure Services provides a secondary datacenter.</span></span>
    
- <span data-ttu-id="ffd72-141">僅限工資您使用的資源。</span><span class="sxs-lookup"><span data-stu-id="ffd72-141">Pay only for the resources you use.</span></span> 
    
- <span data-ttu-id="ffd72-142">小型的復原伺服器陣列可以滿足規模和容量目標嚴重損壞之後向外延展。</span><span class="sxs-lookup"><span data-stu-id="ffd72-142">Small recovery farms can be scaled out after a disaster to meet scale and capacity targets.</span></span> 
    
<span data-ttu-id="ffd72-143">在 Azure 中的復原伺服器陣列已設定為 [同名盡可能實際執行內部部署伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="ffd72-143">The recovery farm in Azure is configured as identically as possible to the production on-premises farm.</span></span> 
  
- <span data-ttu-id="ffd72-144">相同的伺服器角色的表示法。</span><span class="sxs-lookup"><span data-stu-id="ffd72-144">Same representation of server roles.</span></span> 
    
- <span data-ttu-id="ffd72-145">相同的自訂的設定。</span><span class="sxs-lookup"><span data-stu-id="ffd72-145">Same configuration of customizations.</span></span> 
    
- <span data-ttu-id="ffd72-146">（這些可以在實際執行伺服器陣列較小版） 的搜尋功能相同的設定。</span><span class="sxs-lookup"><span data-stu-id="ffd72-146">Same configuration of search features (these can be on a smaller version of the production farm).</span></span> 
    
<span data-ttu-id="ffd72-147">記錄傳送和 DFSR 可用來將資料庫備份和交易記錄檔複製到 Azure 的伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="ffd72-147">Log shipping and DFSR are used to copy database backups and transaction logs to the Azure farm.</span></span> 
  
- <span data-ttu-id="ffd72-p106">DFSR 用來記錄轉移至復原環境的實際執行環境。在 WAN 案例中，DFSR 會比在 Azure 中傳送直接至次要伺服器的記錄檔更有效率。</span><span class="sxs-lookup"><span data-stu-id="ffd72-p106">DFSR is used to transfer logs from the production environment to the recovery environment. In a WAN scenario, DFSR is more efficient than shipping the logs directly to the secondary server in Azure.</span></span> 
    
- <span data-ttu-id="ffd72-150">記錄檔會重新 Azure 型 SQL Server 電腦。</span><span class="sxs-lookup"><span data-stu-id="ffd72-150">Logs are replayed to the Azure-based SQL Server computers.</span></span> 
    
- <span data-ttu-id="ffd72-151">除非執行復原練習，記錄傳送資料庫不會附加至伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="ffd72-151">Log-shipped databases are not attached to the farm until a recovery exercise is performed.</span></span> 
    
<span data-ttu-id="ffd72-152">容錯移轉程序：</span><span class="sxs-lookup"><span data-stu-id="ffd72-152">Failover procedures:</span></span> 
  
1. <span data-ttu-id="ffd72-153">停止記錄傳送。</span><span class="sxs-lookup"><span data-stu-id="ffd72-153">Stop log shipping.</span></span> 
    
2. <span data-ttu-id="ffd72-154">停止接受主要伺服器陣列的流量。</span><span class="sxs-lookup"><span data-stu-id="ffd72-154">Stop accepting traffic to the primary farm.</span></span> 
    
3. <span data-ttu-id="ffd72-155">重新顯示的最後一個交易記錄檔。</span><span class="sxs-lookup"><span data-stu-id="ffd72-155">Replay the final transaction logs.</span></span> 
    
4. <span data-ttu-id="ffd72-156">將內容資料庫附加至伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="ffd72-156">Attach the content databases to the farm.</span></span> 
    
5. <span data-ttu-id="ffd72-157">開始完整編目。</span><span class="sxs-lookup"><span data-stu-id="ffd72-157">Start a full crawl.</span></span> 
    
6. <span data-ttu-id="ffd72-158">複寫的服務資料庫還原服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="ffd72-158">Restore service applications from the replicated services databases.</span></span> 
    
<span data-ttu-id="ffd72-159">此解決方案所提供的復原目標包括：</span><span class="sxs-lookup"><span data-stu-id="ffd72-159">Recovery objectives provided by this solution include:</span></span> 
  
- <span data-ttu-id="ffd72-160">網站和內容</span><span class="sxs-lookup"><span data-stu-id="ffd72-160">Sites and content</span></span> 
    
- <span data-ttu-id="ffd72-161">搜尋 （重新編目，沒有搜尋歷程記錄）</span><span class="sxs-lookup"><span data-stu-id="ffd72-161">Search (re-crawled, no search history)</span></span> 
    
- <span data-ttu-id="ffd72-162">服務</span><span class="sxs-lookup"><span data-stu-id="ffd72-162">Services</span></span>
    
<span data-ttu-id="ffd72-163">可以由 Microsoft 諮詢服務或協力廠商定址的其他項目：</span><span class="sxs-lookup"><span data-stu-id="ffd72-163">Additional items that can be addressed by Microsoft Consulting Services or a partner:</span></span> 
  
- <span data-ttu-id="ffd72-164">同步處理自訂伺服器陣列方案</span><span class="sxs-lookup"><span data-stu-id="ffd72-164">Synchronizing custom farm solutions</span></span> 
    
- <span data-ttu-id="ffd72-165">在內部部署 （Business Data Connectivity (BDC) 及搜尋的內容來源） 的資料來源的連線</span><span class="sxs-lookup"><span data-stu-id="ffd72-165">Connections to data sources on premises (Business Data Connectivity (BDC) and search content sources)</span></span> 
    
- <span data-ttu-id="ffd72-166">搜尋還原案例</span><span class="sxs-lookup"><span data-stu-id="ffd72-166">Search restore scenarios</span></span> 
    
- <span data-ttu-id="ffd72-167">復原時間目標 (RTO) 及復原點目標 (RPO)</span><span class="sxs-lookup"><span data-stu-id="ffd72-167">Recovery Time Objectives (RTO) and Recovery Point Objectives (RPO)</span></span> 
    
#### <a name="cold-standby-environment-running-virtual-machines"></a><span data-ttu-id="ffd72-168">虛擬機器中執行的冷待命環境</span><span class="sxs-lookup"><span data-stu-id="ffd72-168">Cold standby environment running virtual machines</span></span>

<span data-ttu-id="ffd72-169">冷待命環境需要較長的時間開始，但較不昂貴。</span><span class="sxs-lookup"><span data-stu-id="ffd72-169">Cold standby environments take longer to start but are less expensive.</span></span> 
  
- <span data-ttu-id="ffd72-p107">在伺服器陣列完全建置基礎，但虛擬機器時處於停止之後建立伺服器陣列。您所僅處理成本時執行的虛擬機器，但是儲存空間及網路資料傳輸成本套用。</span><span class="sxs-lookup"><span data-stu-id="ffd72-p107">The farm is fully built, but the virtual machines are stopped after the farm is created. You pay only processing costs when the virtual machines are running, but storage and network data transfer costs apply.</span></span> 
    
- <span data-ttu-id="ffd72-172">發生災害時，伺服器陣列中的所有虛擬機器已啟動並修正的項目。</span><span class="sxs-lookup"><span data-stu-id="ffd72-172">In the event of a disaster, all the virtual machines in the farm are started and patched.</span></span> 
    
- <span data-ttu-id="ffd72-173">備份和交易記錄檔會套用至伺服器陣列資料庫。</span><span class="sxs-lookup"><span data-stu-id="ffd72-173">Backups and transaction logs are applied to the farm databases.</span></span> 
    
<span data-ttu-id="ffd72-174">下列清單說明冷待命環境中的其他程序：</span><span class="sxs-lookup"><span data-stu-id="ffd72-174">The following list describes additional procedures for cold standby environments:</span></span> 
  
- <span data-ttu-id="ffd72-175">開啟虛擬機器定期修補程式、 更新及驗證環境。</span><span class="sxs-lookup"><span data-stu-id="ffd72-175">Turn on virtual machines regularly to patch, update, and verify the environment.</span></span> 
    
- <span data-ttu-id="ffd72-176">執行程序來重新整理 DNS 和 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="ffd72-176">Run procedures to refresh DNS and IP addresses.</span></span> 
    
- <span data-ttu-id="ffd72-177">設定 SQL AlwaysOn 容錯移轉後。</span><span class="sxs-lookup"><span data-stu-id="ffd72-177">Set up SQL AlwaysOn after a failover.</span></span> 
    
<span data-ttu-id="ffd72-p108">隨附圖複寫的復原環境的虛擬機器上。容錯移轉之後冷待命環境中，所有虛擬機器已都啟用，且可用性群組已設定使用重新顯示記錄檔提供資料庫伺服器。</span><span class="sxs-lookup"><span data-stu-id="ffd72-p108">The accompanying diagram shows a replicated recovery environment on virtual machines. After failover to a cold standby environment, all virtual machines are started, and the availability groups are configured using replay logs to make the database servers available.</span></span> 
  
## <a name="sharepoint-recovery-environment-in-azure"></a><span data-ttu-id="ffd72-180">Azure 中的 SharePoint 復原環境</span><span class="sxs-lookup"><span data-stu-id="ffd72-180">SharePoint recovery environment in Azure</span></span>

<span data-ttu-id="ffd72-181">設計與建置在 Azure 中的容錯移轉環境。</span><span class="sxs-lookup"><span data-stu-id="ffd72-181">Design and build the failover environment in Azure.</span></span> 
  
- <span data-ttu-id="ffd72-182">在 Azure 中建立虛擬網路。</span><span class="sxs-lookup"><span data-stu-id="ffd72-182">Create a virtual network in Azure.</span></span> 
    
- <span data-ttu-id="ffd72-p109">使用 Azure 中使用的網站 VPN 連線虛擬網路連線與內部網路。此連線使用動態閘道 Azure 中使用。</span><span class="sxs-lookup"><span data-stu-id="ffd72-p109">Connect the on-premises network with the virtual network in Azure with a site-to-site VPN connection. This connection uses a dynamic gateway in Azure.</span></span> 
    
- <span data-ttu-id="ffd72-p110">一或多個網域控制站部署至 Azure 虛擬網路，並設定下列使用您的內部網域。這些網域控制站的類別目錄伺服器。</span><span class="sxs-lookup"><span data-stu-id="ffd72-p110">Deploy one or more domain controllers to the Azure virtual network, and configure these to work with your on-premises domain. These domain controllers are catalog servers.</span></span> 
    
- <span data-ttu-id="ffd72-187">採用雲端服務和可用性設定 SharePoint 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="ffd72-187">Adapt the SharePoint farm for cloud services and availability sets.</span></span> 
    
- <span data-ttu-id="ffd72-188">部署 SharePoint 伺服器陣列加上的檔案伺服器至主機檔案共用。</span><span class="sxs-lookup"><span data-stu-id="ffd72-188">Deploy the SharePoint farm plus a file server to host file shares.</span></span> 
    
- <span data-ttu-id="ffd72-189">設定記錄傳送和 DFSR，之間的內部部署環境及 Azure 型復原環境。</span><span class="sxs-lookup"><span data-stu-id="ffd72-189">Set up log shipping and DFSR between the on-premises environment and the Azure-based recovery environment.</span></span> 
    
<span data-ttu-id="ffd72-190">隨附的圖顯示內部部署環境及 Azure 虛擬網路的下列功能：</span><span class="sxs-lookup"><span data-stu-id="ffd72-190">The accompanying diagram shows the on-premises environment and the Azure virtual network with the following features:</span></span> 
  
### <a name="on-premises-environment"></a><span data-ttu-id="ffd72-191">內部部署環境</span><span class="sxs-lookup"><span data-stu-id="ffd72-191">On-premises environment</span></span>

- <span data-ttu-id="ffd72-192">Windows Server 2012 RRAS</span><span class="sxs-lookup"><span data-stu-id="ffd72-192">Windows Server 2012 RRAS</span></span> 
    
- <span data-ttu-id="ffd72-193">Active Directory 伺服器</span><span class="sxs-lookup"><span data-stu-id="ffd72-193">Active Directory server</span></span> 
    
<span data-ttu-id="ffd72-194">與 Azure 虛擬網路透過虛擬私人網路 (VPN) 閘道的內部網路介面。</span><span class="sxs-lookup"><span data-stu-id="ffd72-194">The on-premises network interfaces with the Azure virtual network over a virtual private network (VPN) gateway.</span></span> 
  
### <a name="azure-virtual-network"></a><span data-ttu-id="ffd72-195">Azure 虛擬網路</span><span class="sxs-lookup"><span data-stu-id="ffd72-195">Azure virtual network</span></span>

<span data-ttu-id="ffd72-196">VPN 閘道介面 （英文） 與作用中的 VPN 閘道子網路。</span><span class="sxs-lookup"><span data-stu-id="ffd72-196">The VPN gateway interfaces with an active VPN gateway subnet.</span></span> 
  
<span data-ttu-id="ffd72-197">Azure 虛擬網路中有三個雲端服務：</span><span class="sxs-lookup"><span data-stu-id="ffd72-197">There are three cloud services in the Azure virtual network:</span></span> 
  
- <span data-ttu-id="ffd72-198">第一個雲端服務有兩個 Active Directory 和 DNS 伺服器的可用性與設定。</span><span class="sxs-lookup"><span data-stu-id="ffd72-198">The first cloud service has two Active Directory and DNS servers with an availability set.</span></span> 
    
- <span data-ttu-id="ffd72-p111">第二個雲端服務有三種設定的伺服器： 兩個分散式快取伺服器的可用性設定。與可用性的兩部前端伺服器設定]。與可用性的三個後端伺服器設定]。</span><span class="sxs-lookup"><span data-stu-id="ffd72-p111">The second cloud service has three sets of servers: Two distributed cache servers with an availability set. Two front-end servers with an availability set. Three backend servers with an availability set.</span></span>
    
- <span data-ttu-id="ffd72-p112">第三個雲端服務有三個可用性設定的資料庫伺服器。其中一個這些資料庫伺服器是記錄傳送和第三個節點的 SQL Server AlwaysOn 節點多數 」 的檔案共用。</span><span class="sxs-lookup"><span data-stu-id="ffd72-p112">The third cloud service has three database servers with an availability set. One of these database servers is a file share for log shipping and a third node of a node majority for SQL Server AlwaysOn.</span></span> 
    
### <a name="build-the-ad-ds-hybrid-environment"></a><span data-ttu-id="ffd72-204">建立 AD DS 混合式環境</span><span class="sxs-lookup"><span data-stu-id="ffd72-204">Build the AD DS hybrid environment</span></span>

<span data-ttu-id="ffd72-205">此解決方案的 AD DS 的組態構成 AD DS 是部分部署在內部和部分 Azure 虛擬機器上部署的混合部署案例。</span><span class="sxs-lookup"><span data-stu-id="ffd72-205">The configuration of AD DS for this solution constitutes a hybrid deployment scenario in which AD DS is partly deployed on-premises and partly deployed on Azure virtual machines.</span></span> 
  
<span data-ttu-id="ffd72-206">重要 — 部署在 Azure 中的 AD DS 之前，請閱讀指導方針部署 Windows Server Active directory Microsoft Azure 虛擬機器上 (http://msdn.microsoft.com/en-us/library/windowsazure/jj156090.aspx)。</span><span class="sxs-lookup"><span data-stu-id="ffd72-206">Important — Before you deploy AD DS in Azure, read Guidelines for Deploying Windows Server Active Directory on Microsoft Azure Virtual Machines (http://msdn.microsoft.com/en-us/library/windowsazure/jj156090.aspx).</span></span> 
  
<span data-ttu-id="ffd72-207">完成指導設計與部署 Active Directory 環境的詳細資訊，請參閱 http://TechNet.microsoft.com。</span><span class="sxs-lookup"><span data-stu-id="ffd72-207">For complete guidance on designing and deploying Active Directory environments, see http://TechNet.microsoft.com.</span></span> 
  
<span data-ttu-id="ffd72-p113">本參考架構包含兩個虛擬機器設定為網域控制站。每個設定如下：</span><span class="sxs-lookup"><span data-stu-id="ffd72-p113">This reference architecture includes two virtual machines configured as domain controllers. Each is configured as follows:</span></span> 
  
- <span data-ttu-id="ffd72-210">大小 — 小。</span><span class="sxs-lookup"><span data-stu-id="ffd72-210">Size — Small.</span></span> 
    
- <span data-ttu-id="ffd72-211">作業系統 — Windows Server 2012。</span><span class="sxs-lookup"><span data-stu-id="ffd72-211">Operating system — Windows Server 2012.</span></span> 
    
- <span data-ttu-id="ffd72-p114">角色 — AD DS 網域控制站指定為通用類別目錄伺服器。此設定可透過 VPN 連線減少輸出的流量。在多重網域環境中使用變更速率高，設定網域控制站的內部與 Azure 中的通用類別目錄伺服器不同步。</span><span class="sxs-lookup"><span data-stu-id="ffd72-p114">Role — AD DS domain controller designated as a global catalog server. This configuration reduces egress traffic across the VPN connection. In a multi-domain environment with high rates of change, configure domain controllers on-premises to not sync with the global catalog servers in Azure.</span></span> 
    
- <span data-ttu-id="ffd72-p115">資料磁碟 — 將 AD DS 資料庫、 記錄以及 SYSVOL 放在 Azure 資料磁碟上。不放置這些作業系統磁碟或 Azure 所提供的暫存磁碟上。這點很重要。</span><span class="sxs-lookup"><span data-stu-id="ffd72-p115">Data disks — Place the AD DS database, logs, and SYSVOL on Azure data disks. Do not place these on the operating system disk or the temporary disks provided by Azure. This is important.</span></span> 
    
- <span data-ttu-id="ffd72-218">角色 — 安裝及設定 Windows DNS 網域控制站上。</span><span class="sxs-lookup"><span data-stu-id="ffd72-218">Role — Install and configure Windows DNS on the domain controllers.</span></span> 
    
- <span data-ttu-id="ffd72-p116">IP 位址 — 使用動態 IP 位址。這需要建立 Azure 虛擬網路。</span><span class="sxs-lookup"><span data-stu-id="ffd72-p116">IP addresses — Use dynamic IP addresses. This requires you to create an Azure Virtual Network.</span></span> 
    

