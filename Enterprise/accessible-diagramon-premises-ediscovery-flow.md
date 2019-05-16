---
title: 易於存取的圖表-內部 eDiscovery 流程
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b9dcd692-0485-4eec-870d-87ab6b89d97b
description: 本文是名為內部部署 eDiscovery 流程圖表易於存取的文字版本。
ms.openlocfilehash: bdaf46c552b346d0e6966cd3589f239146ddadc5
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068529"
---
# <a name="accessible-diagram---on-premises-ediscovery-flow"></a><span data-ttu-id="76784-103">易於存取的圖表-內部 eDiscovery 流程</span><span class="sxs-lookup"><span data-stu-id="76784-103">Accessible diagram - On-premises eDiscovery Flow</span></span>

<span data-ttu-id="76784-104">**摘要：** 本文是名為內部部署 eDiscovery 流程圖表易於存取的文字版本。</span><span class="sxs-lookup"><span data-stu-id="76784-104">**Summary:** This article is an accessible text version of the diagram named On-premises eDiscovery Flow.</span></span>
  
<span data-ttu-id="76784-105">此海報提供數個伺服器產品的詳細資訊架構及資料流。</span><span class="sxs-lookup"><span data-stu-id="76784-105">This poster provides details about the architecture and flow of data across server products.</span></span> 
  
## <a name="across-sharepoint-exchange-lync-and-file-shares"></a><span data-ttu-id="76784-106">跨 SharePoint、 Exchange、 Lync 與檔案共用</span><span class="sxs-lookup"><span data-stu-id="76784-106">Across SharePoint, Exchange, Lync, and file shares</span></span>

<span data-ttu-id="76784-107">此圖顯示使用者傳送的查詢來存取兩個伺服器陣列、 SharePoint 2013 企業應用程式伺服器陣列，並在 SharePoint 2013 服務伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="76784-107">The diagram shows a user sending a query that accesses two server farms, a SharePoint 2013 Enterprise App Farm, and a SharePoint 2013 Services Farm.</span></span> <span data-ttu-id="76784-108">SharePoint 2013 服務伺服器陣列與 SharePoint 2013 內容伺服器陣列，Exchange Server 2013 （這會與 Lync 2013 通訊） 進行通訊及 Windows 檔案共用。</span><span class="sxs-lookup"><span data-stu-id="76784-108">The SharePoint 2013 Services Farm communicates with a SharePoint 2013 Content Farm, Exchange Server 2013 (which communicates with Lync 2013), and Windows File Shares.</span></span> 
  
<span data-ttu-id="76784-109">EDiscovery 流程清單說明資料和哪些 eDisovery 查詢動作發生跨 SharePoint、 Exchange、 Lync 和檔案共用的順序的流程。</span><span class="sxs-lookup"><span data-stu-id="76784-109">The eDiscovery Flow List describes the flow of data and the order in which eDisovery query actions occur across SharePoint, Exchange, Lync, and file shares.</span></span> 
  
<span data-ttu-id="76784-110">EDiscovery 流程清單會詳細說明首先，後面接著在圖表中所述的功能的詳細說明。</span><span class="sxs-lookup"><span data-stu-id="76784-110">The eDiscovery flow list is described in detail first, followed by a detailed description of the features depicted in the diagram.</span></span> 
  
### <a name="ediscovery-flow-list"></a><span data-ttu-id="76784-111">eDiscovery 流程清單</span><span class="sxs-lookup"><span data-stu-id="76784-111">eDiscovery Flow List</span></span>

<span data-ttu-id="76784-112">每個步驟中此清單所述的號碼適用於在圖表中所述的步驟。</span><span class="sxs-lookup"><span data-stu-id="76784-112">The numbers for each of the steps described in this list pertain to a step depicted in the diagram.</span></span> <span data-ttu-id="76784-113">本文件稍後詳細說明圖表。</span><span class="sxs-lookup"><span data-stu-id="76784-113">The diagram is described in detail later in this document.</span></span> 
  
1. <span data-ttu-id="76784-114">建立、 管理和 eDiscovery 中心 (EDC) 中使用 eDiscovery 案例。</span><span class="sxs-lookup"><span data-stu-id="76784-114">eDiscovery cases are created, managed, and used in the eDiscovery center (EDC).</span></span> <span data-ttu-id="76784-115">EDC 是 SharePoint 2013 網站集合。</span><span class="sxs-lookup"><span data-stu-id="76784-115">The EDC is a SharePoint 2013 site collection.</span></span> <span data-ttu-id="76784-116">這是其中定義案例、 要追蹤的來源識別、 發出查詢、 檢閱查詢結果，以及進行內容保留或移除暫停。</span><span class="sxs-lookup"><span data-stu-id="76784-116">This is where cases are defined, sources to be tracked are identified, queries are issued, query results are reviewed, and holds on content are placed or removed.</span></span> 
    
2. <span data-ttu-id="76784-117">EDiscovery 查詢或動作，例如就地保留、 ReleaseHold 或 GetStatus，從轉送 EDC 至企業應用程式伺服器陣列中的 Search Service 應用程式 (SSA) proxy。</span><span class="sxs-lookup"><span data-stu-id="76784-117">The eDiscovery query or action, such as place a Hold, ReleaseHold, or GetStatus, is relayed from the EDC to the Search Service Application (SSA) proxy in the Enterprise App Farm.</span></span> <span data-ttu-id="76784-118">SSA proxy 再轉送至服務應用程式伺服器陣列中的 SSA 的流量。</span><span class="sxs-lookup"><span data-stu-id="76784-118">The SSA proxy then relays the traffic to the SSA in the Services App Farm.</span></span> <span data-ttu-id="76784-119">在這個範例中，要求在具有 「 CONTOSO 」 的 SharePoint 內容伺服器陣列中放置的任何項目會保留的檔案名稱中。</span><span class="sxs-lookup"><span data-stu-id="76784-119">In this example, the request is to place anything in the SharePoint Content Farm with "CONTOSO" in the file name on hold.</span></span> 
    
3. <span data-ttu-id="76784-120">如果要求来查詢的情況下，SSA 查閱搜尋索引。</span><span class="sxs-lookup"><span data-stu-id="76784-120">If the request is to query a case, the SSA consults the search index.</span></span> <span data-ttu-id="76784-121">然後，eDiscovery 查詢結果集傳回給使用者透過 EDC。</span><span class="sxs-lookup"><span data-stu-id="76784-121">Then, the eDiscovery query result set returns to the user through the EDC.</span></span> 
    
4. <span data-ttu-id="76784-122">如果要求的動作，例如就地保留或 ReleaseHold，該巨集指令寫入 Actions_Table SSA 管理資料庫中。</span><span class="sxs-lookup"><span data-stu-id="76784-122">If the request is an action, such as place a Hold or ReleaseHold, that action is written to the Actions_Table in the SSA Administrative database.</span></span> <span data-ttu-id="76784-123">在這個範例中，在具有 「 CONTOSO 」 的 SharePoint 內容伺服器陣列中的任何項目保留要求會寫入 Actions_Table。</span><span class="sxs-lookup"><span data-stu-id="76784-123">In this example, a hold request for anything in the SharePoint Content Farm with "CONTOSO" is written to the Actions_Table.</span></span> 
    
5. <span data-ttu-id="76784-124">在固定間隔內容伺服器陣列 eDiscovery 就地保留計時器工作喚醒要求擱置中的動作將會產生並將狀態更新，透過 SSA proxy 傳送到 SSA。</span><span class="sxs-lookup"><span data-stu-id="76784-124">At regular intervals the Content Farm eDiscovery in-place hold timer job wakes up and generates a request for pending actions and sends status updates through the SSA proxy to the SSA.</span></span> 
    
6. <span data-ttu-id="76784-125">擱置中的動作的查詢轉送至中央的 SSA 查閱 Action_Table 以取得任何擱置中的內容伺服器陣列的動作。</span><span class="sxs-lookup"><span data-stu-id="76784-125">The query for pending actions is relayed to the central SSA, which consults the Action_Table for any pending actions for the Content Farm.</span></span> <span data-ttu-id="76784-126">內容伺服器陣列的就地保留計時器工作也會傳送狀態更新的物件和它已收到，寫入至 ActionsTable 的動作。</span><span class="sxs-lookup"><span data-stu-id="76784-126">The Content Farm in-place hold timer job also sends status updates for objects and actions it has received, which are written to the ActionsTable.</span></span> 
    
7. <span data-ttu-id="76784-127">「 CONTOSO 」 與 SharePoint 2013 內容伺服器陣列中的名稱中的所有內容保留要求是由 SSA 傳送給內容伺服器陣列中的 eDiscovery 就地保留計時器工作。</span><span class="sxs-lookup"><span data-stu-id="76784-127">The hold request for any content with "CONTOSO" in the name in the SharePoint 2013 Content Farm is sent by the SSA to the eDiscovery in-place hold timer job in the Content Farm.</span></span> 
    
8. <span data-ttu-id="76784-128">EDiscovery 就地保留計時器工作位置上的 「 CONTOSO 內容 」 與 「 CONTOSO 網站 」 保留。</span><span class="sxs-lookup"><span data-stu-id="76784-128">The eDiscovery in-place hold timer job places the "CONTOSO Site" and "CONTOSO content" on hold.</span></span> 
    
9. <span data-ttu-id="76784-129">若要檢查探索動作的狀態，並更新狀態企業應用程式伺服器陣列中定期執行 eDiscovery 就地保留計時器工作。</span><span class="sxs-lookup"><span data-stu-id="76784-129">The eDiscovery in-place hold timer job periodically runs in the Enterprise App Farm to check the status of discovery actions and to update the status.</span></span> 
    
10. <span data-ttu-id="76784-130">狀態查詢轉送至 SharePoint Services 伺服器陣列 SSA 的企業應用程式伺服器陣列 SSA proxy 透過。</span><span class="sxs-lookup"><span data-stu-id="76784-130">The status query is relayed through the Enterprise App Farm SSA proxy to the SharePoint Services Farm SSA.</span></span> 
    
11. <span data-ttu-id="76784-131">SSA 動作資料表中擷取狀態，並傳回的狀態更新發送至 EDC 企業應用程式伺服器陣列中的計時器工作。</span><span class="sxs-lookup"><span data-stu-id="76784-131">The SSA retrieves the status from the Actions table and returns it to the timer job in the Enterprise App Farm, which pushes the status updates to the EDC.</span></span> 
    
12. <span data-ttu-id="76784-132">當 eDiscovery 使用者搜尋 （或執行巨集指令） 對於 Exchange 來源，例如信箱或封存的 Lync 內容，中央 SSA 使用查詢 Exchange Web 服務的 Exchange Web 服務 (EWS) proxy。</span><span class="sxs-lookup"><span data-stu-id="76784-132">When the eDiscovery user is searching (or performing an action) for Exchange sources, such as a mailbox or archived Lync content, the central SSA uses Exchange Web Services (EWS) proxy to query Exchange Web Services.</span></span> <span data-ttu-id="76784-133">Exchange 有其專屬搜尋和 eDiscovery 的基礎結構，並在內部管理電子文件探索的所有呼叫。</span><span class="sxs-lookup"><span data-stu-id="76784-133">Exchange has its own search and eDiscovery infrastructure and manages all eDiscovery calls internally.</span></span> 
    
13. <span data-ttu-id="76784-134">Exchange Web 服務回應 SSA 與 eDiscovery 搜尋結果或查詢式保留，其中，接下來取得轉送至 EDC 狀態要求的回應。</span><span class="sxs-lookup"><span data-stu-id="76784-134">Exchange Web Services responds to SSA with eDiscovery search results or a response to a status request for a query-based hold, which, in turn, gets relayed to the EDC.</span></span> 
    
#### <a name="prerequisites"></a><span data-ttu-id="76784-135">必要條件</span><span class="sxs-lookup"><span data-stu-id="76784-135">Prerequisites</span></span>

- <span data-ttu-id="76784-136">SharePoint 企業搜尋必須設定，成功出現在 [內容來源 （SharePoint 及 Windows 檔案共用） 上的搜尋編目和索引中有所有內容來源。</span><span class="sxs-lookup"><span data-stu-id="76784-136">SharePoint Enterprise Search must be configured, search crawls on content sources (SharePoint and Windows file shares) are successfully occurring, and all content sources are in the index.</span></span> 
    
- <span data-ttu-id="76784-137">SharePoint Services 伺服器陣列與 Exchange 之間，以及 Exchange 與 Lync 之間，必須設定伺服器對伺服器信任和驗證。</span><span class="sxs-lookup"><span data-stu-id="76784-137">Server-to-server trust and authentication must be configured between the SharePoint Services Farm and Exchange and also between Exchange and Lync.</span></span> 
    
### <a name="description-of-components-in-the-diagram"></a><span data-ttu-id="76784-138">元件圖表中的描述</span><span class="sxs-lookup"><span data-stu-id="76784-138">Description of components in the diagram</span></span>

<span data-ttu-id="76784-139">此圖顯示使用者傳送的查詢時，會存取兩個伺服器陣列，在 SharePoint 2013 企業應用程式伺服器陣列與 SharePoint 2013 服務伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="76784-139">The diagram shows a user sending a query, which accesses two server farms, a SharePoint 2013 Enterprise App Farm and a SharePoint 2013 Services Farm.</span></span> <span data-ttu-id="76784-140">SharePoint 服務伺服器陣列介面與 SharePoint 2013 內容伺服器陣列，Exchange Server 2013 （這介面搭配 Lync 2013），及 Windows 檔案共用。</span><span class="sxs-lookup"><span data-stu-id="76784-140">The SharePoint Services Farm interfaces with a SharePoint 2013 Content Farm, Exchange Server 2013 (which interfaces with Lync 2013), and Windows File Shares.</span></span> 
  
#### <a name="sharepoint-2013-enterprise-app-farm"></a><span data-ttu-id="76784-141">SharePoint 2013 企業應用程式伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="76784-141">SharePoint 2013 Enterprise App Farm</span></span>

<span data-ttu-id="76784-142">在 SharePoint 2013 企業應用程式伺服器陣列包含下列元件：</span><span class="sxs-lookup"><span data-stu-id="76784-142">The SharePoint 2013 Enterprise App Farm contains the following components:</span></span> 
  
- <span data-ttu-id="76784-143">EDC</span><span class="sxs-lookup"><span data-stu-id="76784-143">EDC</span></span>
    
- <span data-ttu-id="76784-144">SSA proxy</span><span class="sxs-lookup"><span data-stu-id="76784-144">SSA proxy</span></span> 
    
- <span data-ttu-id="76784-145">計時器作業</span><span class="sxs-lookup"><span data-stu-id="76784-145">Timer job</span></span> 
    
<span data-ttu-id="76784-146">以查詢或使用者所傳送的巨集指令會傳送至企業應用程式伺服器陣列中 EDC。</span><span class="sxs-lookup"><span data-stu-id="76784-146">A query or action sent by the user is sent to the EDC in the Enterprise App Farm.</span></span> <span data-ttu-id="76784-147">會發生下列動作：</span><span class="sxs-lookup"><span data-stu-id="76784-147">The following actions occur:</span></span> 
  
- <span data-ttu-id="76784-148">查詢或巨集指令移至 SSA proxy。</span><span class="sxs-lookup"><span data-stu-id="76784-148">The query or action goes to the SSA proxy.</span></span> 
    
- <span data-ttu-id="76784-149">SSA proxy 傳送企業應用程式伺服器陣列中的狀態查詢或回應的計時器工作，它也會傳送狀態以查詢或 SSA 服務回應 SharePoint Services 伺服器陣列中。</span><span class="sxs-lookup"><span data-stu-id="76784-149">The SSA proxy sends a status query or response to the Timer job in the Enterprise App Farm, and it also sends a status query or response to the SSA service in the SharePoint Services Farm.</span></span> <span data-ttu-id="76784-150">動作所產生的這一節所述有關 SharePoint 服務伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="76784-150">The actions that result from this are described in the section about the SharePoint Services Farm.</span></span> 
    
- <span data-ttu-id="76784-151">它會收到回應，計時器工作會傳送 SSA proxy，並 EDC 回應。</span><span class="sxs-lookup"><span data-stu-id="76784-151">When it receives a response, the Timer job sends the response to the SSA proxy and to the EDC.</span></span> 
    
- <span data-ttu-id="76784-152">任何來自查詢或巨集指令的結果是從 EDC 傳送給使用者。</span><span class="sxs-lookup"><span data-stu-id="76784-152">Any results from the query or action are sent to the user from the EDC.</span></span> 
    
#### <a name="sharepoint-2013-services-farm"></a><span data-ttu-id="76784-153">SharePoint 2013 服務伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="76784-153">SharePoint 2013 Services Farm</span></span>

<span data-ttu-id="76784-154">SharePoint 2013 服務伺服器陣列包含下列元件：</span><span class="sxs-lookup"><span data-stu-id="76784-154">The SharePoint 2013 Services Farm contains the following components:</span></span> 
  
- <span data-ttu-id="76784-155">SSA 服務</span><span class="sxs-lookup"><span data-stu-id="76784-155">SSA Service</span></span> 
    
- <span data-ttu-id="76784-156">搜尋索引資料庫</span><span class="sxs-lookup"><span data-stu-id="76784-156">Search index database</span></span> 
    
- <span data-ttu-id="76784-157">SSA admin_db 資料庫。</span><span class="sxs-lookup"><span data-stu-id="76784-157">SSA admin_db database.</span></span> <span data-ttu-id="76784-158">此資料庫中的 [動作] 表格包含： 保留版本保留 GetStatus</span><span class="sxs-lookup"><span data-stu-id="76784-158">The Actions Table in this database contains: Hold Release Hold GetStatus</span></span> 
    
- <span data-ttu-id="76784-159">EWS proxy</span><span class="sxs-lookup"><span data-stu-id="76784-159">EWS proxy</span></span> 
    
<span data-ttu-id="76784-160">當 SharePoint 企業應用程式伺服器陣列中的 SSA proxy 會將狀態查詢傳送至 SharePoint Services 伺服器陣列中的 SSA 時，就會發生下列動作：</span><span class="sxs-lookup"><span data-stu-id="76784-160">When the SSA proxy in the SharePoint Enterprise App Farm sends a status query to the SSA in the SharePoint Services Farm, the following actions occur:</span></span> 
  
- <span data-ttu-id="76784-161">如果要求的查詢，SSA 查閱搜尋索引。</span><span class="sxs-lookup"><span data-stu-id="76784-161">If the request is a query, the SSA consults the search index.</span></span> <span data-ttu-id="76784-162">探索會將回應傳回至 SSA，然後透過 EDC 使用者。</span><span class="sxs-lookup"><span data-stu-id="76784-162">The discovery response is returned to the SSA and then to the user through the EDC.</span></span> 
    
- <span data-ttu-id="76784-163">如果要求是寫入巨集指令，SSA 服務會將寫入巨集指令傳送至 SSA admin_db。</span><span class="sxs-lookup"><span data-stu-id="76784-163">If the request is a write action, the SSA service sends the write action to the SSA admin_db.</span></span> 
    
- <span data-ttu-id="76784-164">編目和回應結果要求會從 SSA 傳送至 SharePoint 2013 內容伺服器陣列，並將回應傳回至 SSA。</span><span class="sxs-lookup"><span data-stu-id="76784-164">A crawl and responding results request is sent from the SSA to the SharePoint 2013 Content Farm and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="76784-165">編目和回應結果要求會從 SSA 傳送至 Windows 檔案共用，並將回應傳回至 SSA。</span><span class="sxs-lookup"><span data-stu-id="76784-165">A crawl and responding results request is sent from the SSA to the Windows File Shares, and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="76784-166">暫止的動作、 回覆或狀態更新的查詢 SSA 從傳送至 SharePoint 內容伺服器陣列中的 SSA proxy 並將回應傳回至 SSA。</span><span class="sxs-lookup"><span data-stu-id="76784-166">A query for pending action(s), responses, or status updates is sent from the SSA to the SSA proxy in the SharePoint Content Farm, and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="76784-167">Exchange 巨集指令/狀態要求會從 SSA 傳送到 EWS proxy，將 Exchange 查詢巨集指令/狀態要求傳送至 Exchange 2013 伺服器上的 Exchange Web 服務。</span><span class="sxs-lookup"><span data-stu-id="76784-167">An Exchange action/status request is sent from the SSA to the EWS proxy, which sends an Exchange Query action/status request to the Exchange Web Service on the Exchange 2013 server.</span></span> 
    
- <span data-ttu-id="76784-168">狀態查詢回應從 SSA 傳送至 SSA admin_db，而且會傳回至 SSA。</span><span class="sxs-lookup"><span data-stu-id="76784-168">A status query/response is sent from the SSA to the SSA admin_db and is returned to the SSA.</span></span> 
    
- <span data-ttu-id="76784-169">擱置中的巨集指令查詢回應從 SSA 傳送至 SSA admin_db，而且會傳回至 SSA。</span><span class="sxs-lookup"><span data-stu-id="76784-169">A pending action query/response is sent from the SSA to the SSA admin_db and is returned to the SSA.</span></span> 
    
#### <a name="sharepoint-2013-content-farm"></a><span data-ttu-id="76784-170">SharePoint 2013 內容伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="76784-170">SharePoint 2013 Content Farm</span></span>

<span data-ttu-id="76784-171">在 SharePoint 2013 內容伺服器陣列包含下列元件：</span><span class="sxs-lookup"><span data-stu-id="76784-171">The SharePoint 2013 Content Farm contains the following components:</span></span> 
  
- <span data-ttu-id="76784-172">SSA proxy</span><span class="sxs-lookup"><span data-stu-id="76784-172">SSA proxy</span></span> 
    
- <span data-ttu-id="76784-173">計時器作業</span><span class="sxs-lookup"><span data-stu-id="76784-173">Timer job</span></span> 
    
- <span data-ttu-id="76784-174">Contoso SharePoint 網站</span><span class="sxs-lookup"><span data-stu-id="76784-174">Contoso SharePoint site</span></span> 
    
- <span data-ttu-id="76784-175">Contoso SharePoint 內容</span><span class="sxs-lookup"><span data-stu-id="76784-175">Contoso SharePoint content</span></span> 
    
<span data-ttu-id="76784-176">當 SharePoint Services 伺服器陣列中的 SSA 將狀態查詢傳送至 SharePoint 內容伺服器陣列中的 SSA Proxy 時，則會發生下列動作：</span><span class="sxs-lookup"><span data-stu-id="76784-176">When the SSA in the SharePoint Services Farm sends a status query to the SSA Proxy in the SharePoint Content Farm, the following actions occur:</span></span> 
  
- <span data-ttu-id="76784-177">SharePoint 內容伺服器陣列中的 SSA proxy 會將查詢傳送暫止的動作/狀態回應計時器工作。</span><span class="sxs-lookup"><span data-stu-id="76784-177">The SSA proxy in the SharePoint Content Farm sends a query for pending actions/status response to the Timer job.</span></span> 
    
- <span data-ttu-id="76784-178">計時器工作將要求傳送至 Contoso SharePoint 網站中，檢閱 Contoso SharePoint 內容。</span><span class="sxs-lookup"><span data-stu-id="76784-178">The Timer job sends a request to the Contoso SharePoint site, which reviews the Contoso SharePoint content.</span></span> 
    
- <span data-ttu-id="76784-179">回應等候中的動作狀態查詢從計時器工作傳送到 SharePoint 內容伺服器陣列中的 SSA proxy，然後它會傳送至 SharePoint Services 伺服器陣列中的 SSA 服務</span><span class="sxs-lookup"><span data-stu-id="76784-179">The response to the pending actions/status query is sent from the Timer job to the SSA proxy in the SharePoint Content Farm, and then it is sent to the SSA service in the SharePoint Services Farm</span></span> 
    
#### <a name="exchange-2013"></a><span data-ttu-id="76784-180">Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="76784-180">Exchange 2013</span></span>

<span data-ttu-id="76784-181">Exchange 2013 伺服器元件包含 Exchange Web 服務，並提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="76784-181">The Exchange 2013 server component contains the Exchange Web Service and provides the following:</span></span> 
  
- <span data-ttu-id="76784-182">伺服器對伺服器信任/OAuth 是 Exchange 2013 與 SharePoint 2013 內容伺服器陣列之間進行處理。</span><span class="sxs-lookup"><span data-stu-id="76784-182">Server-to-server Trust/OAuth is handled between the SharePoint 2013 Content Farm and Exchange 2013.</span></span> 
    
- <span data-ttu-id="76784-183">伺服器對伺服器信任/OAuth 是 Exchange 2013 和 Lync 2013 之間進行處理。</span><span class="sxs-lookup"><span data-stu-id="76784-183">Server-to-server Trust/OAuth is handled between Exchange 2013 and Lync 2013.</span></span> 
    
#### <a name="lync-2013"></a><span data-ttu-id="76784-184">Lync 2013</span><span class="sxs-lookup"><span data-stu-id="76784-184">Lync 2013</span></span>

<span data-ttu-id="76784-185">Lync 2013 元件封存在 Exchange 2013 的 Lync 內容。</span><span class="sxs-lookup"><span data-stu-id="76784-185">The Lync 2013 component archives Lync content in Exchange 2013.</span></span> 
  
#### <a name="windows-file-shares"></a><span data-ttu-id="76784-186">Windows 檔案共用</span><span class="sxs-lookup"><span data-stu-id="76784-186">Windows File Shares</span></span>

<span data-ttu-id="76784-187">Windows 檔案共用元件提供 SharePoint Services 伺服器陣列中的 SSA 編目結果。</span><span class="sxs-lookup"><span data-stu-id="76784-187">The Windows File Shares component provides crawl results to the SSA in the SharePoint Services Farm.</span></span> 
  
### <a name="legend"></a><span data-ttu-id="76784-188">圖例</span><span class="sxs-lookup"><span data-stu-id="76784-188">Legend</span></span>

<span data-ttu-id="76784-189">這個圖表的圖例以圖形方式顯示不同類型的流量所描述之不同的彩色行中元件之間，如下所示：</span><span class="sxs-lookup"><span data-stu-id="76784-189">The legend for this diagram graphically shows the different types of traffic depicted among the components in different colored lines as follows:</span></span> 
  
- <span data-ttu-id="76784-190">淺藍色線條： 查詢/動作-eDiscovery 查詢或巨集指令的資料</span><span class="sxs-lookup"><span data-stu-id="76784-190">Light blue line: Query/action - eDiscovery query or action data</span></span> 
    
- <span data-ttu-id="76784-191">橘色線條： eDisovery 回應-eDiscovery 查詢回應資料</span><span class="sxs-lookup"><span data-stu-id="76784-191">Orange line: eDisovery response - eDiscovery query response data</span></span> 
    
- <span data-ttu-id="76784-192">綠色線條： 狀態查詢/回應-eDiscovery 狀態查詢/回應資料</span><span class="sxs-lookup"><span data-stu-id="76784-192">Green line: Status query/response - eDiscovery status query/response data</span></span> 
    
- <span data-ttu-id="76784-193">紫色線條： Exchange 巨集指令/狀態要求-eDiscovery 要求 Exchange 流量的巨集指令狀態。</span><span class="sxs-lookup"><span data-stu-id="76784-193">Purple line: Exchange action/status request - eDiscovery request for action status for Exchange traffic.</span></span> 
    
- <span data-ttu-id="76784-194">紅色列： Exchange 資料/狀態回應-從 Exchange 的 eDiscovery 查詢或狀態回應。</span><span class="sxs-lookup"><span data-stu-id="76784-194">Red line: Exchange data/status response - eDiscovery query or status response from Exchange.</span></span> 
    
- <span data-ttu-id="76784-195">點狀黑色線條： 伺服器對伺服器信任/Oauth</span><span class="sxs-lookup"><span data-stu-id="76784-195">Dotted black line: Server-to-Server Trust/Oauth</span></span> 
    
- <span data-ttu-id="76784-196">黑色實線： 編目/結果</span><span class="sxs-lookup"><span data-stu-id="76784-196">Solid black line: Crawl/results</span></span> 
    

