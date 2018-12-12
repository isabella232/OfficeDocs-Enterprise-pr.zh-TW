---
title: 存取圖表-內部部署 eDiscovery 流程
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b9dcd692-0485-4eec-870d-87ab6b89d97b
description: 本文是名為內部部署 eDiscovery 流程圖表可存取的文字版本。
ms.openlocfilehash: e137a75fb80c9198a332144d82fe405c6884aa52
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
ms.locfileid: "17503056"
---
# <a name="accessible-diagram---on-premises-ediscovery-flow"></a><span data-ttu-id="9c12b-103">存取圖表-內部部署 eDiscovery 流程</span><span class="sxs-lookup"><span data-stu-id="9c12b-103">Accessible diagram - On-premises eDiscovery Flow</span></span>

<span data-ttu-id="9c12b-104">**摘要：** 本文是名為內部部署 eDiscovery 流程圖表可存取的文字版本。</span><span class="sxs-lookup"><span data-stu-id="9c12b-104">**Summary:** This article is an accessible text version of the diagram named On-premises eDiscovery Flow.</span></span>
  
<span data-ttu-id="9c12b-105">此海報提供詳細資訊架構及流程資料的伺服器產品。</span><span class="sxs-lookup"><span data-stu-id="9c12b-105">This poster provides details about the architecture and flow of data across server products.</span></span> 
  
## <a name="across-sharepoint-exchange-lync-and-file-shares"></a><span data-ttu-id="9c12b-106">整個 SharePoint、 Exchange、 Lync 與檔案共用</span><span class="sxs-lookup"><span data-stu-id="9c12b-106">Across SharePoint, Exchange, Lync, and file shares</span></span>

<span data-ttu-id="9c12b-p101">此圖顯示使用者傳送存取兩個伺服器陣列、 SharePoint 2013 企業應用程式伺服器陣列，並在 SharePoint 2013 服務伺服器陣列的查詢。SharePoint 2013 服務伺服器陣列與 SharePoint 2013 內容伺服器陣列、 Exchange Server 2013 （這會與 Lync 2013 的通訊）、 通訊及 Windows 檔案共用。</span><span class="sxs-lookup"><span data-stu-id="9c12b-p101">The diagram shows a user sending a query that accesses two server farms, a SharePoint 2013 Enterprise App Farm, and a SharePoint 2013 Services Farm. The SharePoint 2013 Services Farm communicates with a SharePoint 2013 Content Farm, Exchange Server 2013 (which communicates with Lync 2013), and Windows File Shares.</span></span> 
  
<span data-ttu-id="9c12b-109">EDiscovery 流程清單說明資料和順序中的 eDisovery 查詢動作發生跨 SharePoint、 Exchange、 Lync 與檔案共用的流程。</span><span class="sxs-lookup"><span data-stu-id="9c12b-109">The eDiscovery Flow List describes the flow of data and the order in which eDisovery query actions occur across SharePoint, Exchange, Lync, and file shares.</span></span> 
  
<span data-ttu-id="9c12b-110">EDiscovery 流程清單會詳細描述於第一次，後面所述之圖表中的功能的詳細說明。</span><span class="sxs-lookup"><span data-stu-id="9c12b-110">The eDiscovery flow list is described in detail first, followed by a detailed description of the features depicted in the diagram.</span></span> 
  
### <a name="ediscovery-flow-list"></a><span data-ttu-id="9c12b-111">eDiscovery 流程的清單</span><span class="sxs-lookup"><span data-stu-id="9c12b-111">eDiscovery Flow List</span></span>

<span data-ttu-id="9c12b-p102">這份清單中所述的步驟的每個號碼與圖表中所述的步驟。本文稍後的詳細說明圖表。</span><span class="sxs-lookup"><span data-stu-id="9c12b-p102">The numbers for each of the steps described in this list pertain to a step depicted in the diagram. The diagram is described in detail later in this document.</span></span> 
  
1. <span data-ttu-id="9c12b-p103">eDiscovery 案例所建立、 管理及 eDiscovery 中心 (EDC) 中所使用。EDC 為 SharePoint 2013 網站集合。這是其中的情況下所定義、 識別來源來追蹤、 發出查詢、 查詢結果的檢閱，以及保留中的內容會置於或移除。</span><span class="sxs-lookup"><span data-stu-id="9c12b-p103">eDiscovery cases are created, managed, and used in the eDiscovery center (EDC). The EDC is a SharePoint 2013 site collection. This is where cases are defined, sources to be tracked are identified, queries are issued, query results are reviewed, and holds on content are placed or removed.</span></span> 
    
2. <span data-ttu-id="9c12b-p104">EDiscovery 查詢或巨集指令，例如就地保留、 ReleaseHold 或 GetStatus、 從轉送 EDC 至企業應用程式伺服器陣列中的 Search Service 應用程式 (SSA) proxy。然後 SSA proxy 會轉送至服務應用程式伺服器陣列中的 SSA 流量。在這個範例中，要求是將任何項目放入含有"CONTOSO"SharePoint 內容伺服器陣列中保留的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="9c12b-p104">The eDiscovery query or action, such as place a Hold, ReleaseHold, or GetStatus, is relayed from the EDC to the Search Service Application (SSA) proxy in the Enterprise App Farm. The SSA proxy then relays the traffic to the SSA in the Services App Farm. In this example, the request is to place anything in the SharePoint Content Farm with "CONTOSO" in the file name on hold.</span></span> 
    
3. <span data-ttu-id="9c12b-p105">如果要求，以查詢案例 SSA 查閱搜尋索引。然後，eDiscovery 查詢結果集傳回給 EDC 透過使用者。</span><span class="sxs-lookup"><span data-stu-id="9c12b-p105">If the request is to query a case, the SSA consults the search index. Then, the eDiscovery query result set returns to the user through the EDC.</span></span> 
    
4. <span data-ttu-id="9c12b-p106">如果要求的動作，例如就地保留或 ReleaseHold，該動作會寫入 Actions_Table SSA 管理資料庫中。在這個範例中，保留要求以"CONTOSO"SharePoint 內容伺服器陣列中的任何項目會寫入 Actions_Table。</span><span class="sxs-lookup"><span data-stu-id="9c12b-p106">If the request is an action, such as place a Hold or ReleaseHold, that action is written to the Actions_Table in the SSA Administrative database. In this example, a hold request for anything in the SharePoint Content Farm with "CONTOSO" is written to the Actions_Table.</span></span> 
    
5. <span data-ttu-id="9c12b-124">在固定間隔內容伺服器陣列 eDiscovery 就地保留計時器工作喚醒及產生擱置動作要求並傳送到 SSA proxy 的狀態更新至 SSA。</span><span class="sxs-lookup"><span data-stu-id="9c12b-124">At regular intervals the Content Farm eDiscovery in-place hold timer job wakes up and generates a request for pending actions and sends status updates through the SSA proxy to the SSA.</span></span> 
    
6. <span data-ttu-id="9c12b-p107">擱置動作的查詢轉送至中央的 SSA 查閱 Action_Table 以取得所有暫止的內容伺服器陣列的動作。就地保留計時器服務內容的伺服器陣列也會傳送物件和動作已接收到，會寫入至 ActionsTable 的狀態更新。</span><span class="sxs-lookup"><span data-stu-id="9c12b-p107">The query for pending actions is relayed to the central SSA, which consults the Action_Table for any pending actions for the Content Farm. The Content Farm in-place hold timer job also sends status updates for objects and actions it has received, which are written to the ActionsTable.</span></span> 
    
7. <span data-ttu-id="9c12b-127">保留要求的 SharePoint 2013 內容伺服器陣列中的名稱以"CONTOSO"任何內容 SSA 來傳送至內容伺服器陣列中的 eDiscovery 就地保留計時器工作。</span><span class="sxs-lookup"><span data-stu-id="9c12b-127">The hold request for any content with "CONTOSO" in the name in the SharePoint 2013 Content Farm is sent by the SSA to the eDiscovery in-place hold timer job in the Content Farm.</span></span> 
    
8. <span data-ttu-id="9c12b-128">EDiscovery 就地保留計時器工作 places"CONTOSO Site"和"CONTOSO content"上的保留。</span><span class="sxs-lookup"><span data-stu-id="9c12b-128">The eDiscovery in-place hold timer job places the "CONTOSO Site" and "CONTOSO content" on hold.</span></span> 
    
9. <span data-ttu-id="9c12b-129">企業應用程式伺服器陣列以檢查探索動作的狀態和更新狀態中定期執行 eDiscovery 就地保留計時器工作。</span><span class="sxs-lookup"><span data-stu-id="9c12b-129">The eDiscovery in-place hold timer job periodically runs in the Enterprise App Farm to check the status of discovery actions and to update the status.</span></span> 
    
10. <span data-ttu-id="9c12b-130">狀態查詢轉送至 SharePoint Services 伺服器陣列 SSA 的企業應用程式伺服器陣列 SSA proxy 透過。</span><span class="sxs-lookup"><span data-stu-id="9c12b-130">The status query is relayed through the Enterprise App Farm SSA proxy to the SharePoint Services Farm SSA.</span></span> 
    
11. <span data-ttu-id="9c12b-131">SSA 動作資料表擷取狀態，並傳回將狀態更新至 EDC 推入企業應用程式伺服器陣列中的計時器工作。</span><span class="sxs-lookup"><span data-stu-id="9c12b-131">The SSA retrieves the status from the Actions table and returns it to the timer job in the Enterprise App Farm, which pushes the status updates to the EDC.</span></span> 
    
12. <span data-ttu-id="9c12b-p108">當 eDiscovery 使用者會搜尋 （或執行的動作） Exchange 來源，例如信箱或封存的 Lync 內容中央 SSA 使用 Exchange Web 服務 (EWS) 來查詢 Exchange Web 服務的 proxy。Exchange 有其專屬搜尋和 eDiscovery 的基礎結構，以及適用於內部管理 eDiscovery 的所有通話。</span><span class="sxs-lookup"><span data-stu-id="9c12b-p108">When the eDiscovery user is searching (or performing an action) for Exchange sources, such as a mailbox or archived Lync content, the central SSA uses Exchange Web Services (EWS) proxy to query Exchange Web Services. Exchange has its own search and eDiscovery infrastructure and manages all eDiscovery calls internally.</span></span> 
    
13. <span data-ttu-id="9c12b-134">Exchange Web 服務回應 SSA 與 eDiscovery 搜尋結果或查詢式保留，它會依次取得轉送至 EDC 狀態要求回應。</span><span class="sxs-lookup"><span data-stu-id="9c12b-134">Exchange Web Services responds to SSA with eDiscovery search results or a response to a status request for a query-based hold, which, in turn, gets relayed to the EDC.</span></span> 
    
#### <a name="prerequisites"></a><span data-ttu-id="9c12b-135">必要條件</span><span class="sxs-lookup"><span data-stu-id="9c12b-135">Prerequisites</span></span>

- <span data-ttu-id="9c12b-136">SharePoint 企業搜尋必須設定、 成功出現在 [內容來源 （SharePoint 及 Windows 檔案共用） 上的搜尋編目及索引中的所有內容來源。</span><span class="sxs-lookup"><span data-stu-id="9c12b-136">SharePoint Enterprise Search must be configured, search crawls on content sources (SharePoint and Windows file shares) are successfully occurring, and all content sources are in the index.</span></span> 
    
- <span data-ttu-id="9c12b-137">SharePoint Services 伺服器陣列與 Exchange 之間及 Exchange 與 Lync 之間必須設定伺服器對伺服器信任和驗證。</span><span class="sxs-lookup"><span data-stu-id="9c12b-137">Server-to-server trust and authentication must be configured between the SharePoint Services Farm and Exchange and also between Exchange and Lync.</span></span> 
    
### <a name="description-of-components-in-the-diagram"></a><span data-ttu-id="9c12b-138">圖表中的元件的描述</span><span class="sxs-lookup"><span data-stu-id="9c12b-138">Description of components in the diagram</span></span>

<span data-ttu-id="9c12b-p109">此圖顯示使用者傳送的查詢時，會存取有關兩個伺服器陣列，在 SharePoint 2013 企業應用程式伺服器陣列與 SharePoint 2013 服務伺服器陣列。SharePoint Services 伺服器陣列介面 （英文） 與 SharePoint 2013 內容伺服器陣列、 Exchange Server 2013 （此介面搭配 Lync 2013） 和 Windows 檔案共用。</span><span class="sxs-lookup"><span data-stu-id="9c12b-p109">The diagram shows a user sending a query, which accesses two server farms, a SharePoint 2013 Enterprise App Farm and a SharePoint 2013 Services Farm. The SharePoint Services Farm interfaces with a SharePoint 2013 Content Farm, Exchange Server 2013 (which interfaces with Lync 2013), and Windows File Shares.</span></span> 
  
#### <a name="sharepoint-2013-enterprise-app-farm"></a><span data-ttu-id="9c12b-141">SharePoint 2013 企業應用程式伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="9c12b-141">SharePoint 2013 Enterprise App Farm</span></span>

<span data-ttu-id="9c12b-142">SharePoint 2013 企業應用程式伺服器陣列包含下列元件：</span><span class="sxs-lookup"><span data-stu-id="9c12b-142">The SharePoint 2013 Enterprise App Farm contains the following components:</span></span> 
  
- <span data-ttu-id="9c12b-143">EDC</span><span class="sxs-lookup"><span data-stu-id="9c12b-143">EDC</span></span>
    
- <span data-ttu-id="9c12b-144">SSA proxy</span><span class="sxs-lookup"><span data-stu-id="9c12b-144">SSA proxy</span></span> 
    
- <span data-ttu-id="9c12b-145">計時器工作</span><span class="sxs-lookup"><span data-stu-id="9c12b-145">Timer job</span></span> 
    
<span data-ttu-id="9c12b-p110">以查詢或使用者所傳送的動作會傳送至企業應用程式伺服器陣列中 EDC。發生下列動作：</span><span class="sxs-lookup"><span data-stu-id="9c12b-p110">A query or action sent by the user is sent to the EDC in the Enterprise App Farm. The following actions occur:</span></span> 
  
- <span data-ttu-id="9c12b-148">以查詢或巨集指令會前往 SSA proxy。</span><span class="sxs-lookup"><span data-stu-id="9c12b-148">The query or action goes to the SSA proxy.</span></span> 
    
- <span data-ttu-id="9c12b-p111">企業應用程式伺服器陣列中的 SSA proxy 傳送狀態以查詢或回應的計時器工作及它也會傳送狀態以查詢或 SSA 服務回應 SharePoint Services 伺服器陣列中。動作所產生的這節所述有關 SharePoint Services 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="9c12b-p111">The SSA proxy sends a status query or response to the Timer job in the Enterprise App Farm, and it also sends a status query or response to the SSA service in the SharePoint Services Farm. The actions that result from this are described in the section about the SharePoint Services Farm.</span></span> 
    
- <span data-ttu-id="9c12b-151">它會收到回應，計時器工作會傳送 SSA proxy 並 EDC 回應。</span><span class="sxs-lookup"><span data-stu-id="9c12b-151">When it receives a response, the Timer job sends the response to the SSA proxy and to the EDC.</span></span> 
    
- <span data-ttu-id="9c12b-152">從 EDC 查詢或巨集指令的任何結果傳送給使用者。</span><span class="sxs-lookup"><span data-stu-id="9c12b-152">Any results from the query or action are sent to the user from the EDC.</span></span> 
    
#### <a name="sharepoint-2013-services-farm"></a><span data-ttu-id="9c12b-153">SharePoint 2013 服務伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="9c12b-153">SharePoint 2013 Services Farm</span></span>

<span data-ttu-id="9c12b-154">SharePoint 2013 服務伺服器陣列包含下列元件：</span><span class="sxs-lookup"><span data-stu-id="9c12b-154">The SharePoint 2013 Services Farm contains the following components:</span></span> 
  
- <span data-ttu-id="9c12b-155">SSA 服務</span><span class="sxs-lookup"><span data-stu-id="9c12b-155">SSA Service</span></span> 
    
- <span data-ttu-id="9c12b-156">搜尋索引資料庫</span><span class="sxs-lookup"><span data-stu-id="9c12b-156">Search index database</span></span> 
    
- <span data-ttu-id="9c12b-p112">SSA admin_db 資料庫。此資料庫中的 [動作] 表格包含： 保留版本保留 GetStatus</span><span class="sxs-lookup"><span data-stu-id="9c12b-p112">SSA admin_db database. The Actions Table in this database contains: Hold Release Hold GetStatus</span></span> 
    
- <span data-ttu-id="9c12b-159">EWS proxy</span><span class="sxs-lookup"><span data-stu-id="9c12b-159">EWS proxy</span></span> 
    
<span data-ttu-id="9c12b-160">當 SharePoint 企業應用程式伺服器陣列中的 SSA proxy 傳送至 SharePoint Services 伺服器陣列中的 SSA 狀態查詢時，便會發生下列動作：</span><span class="sxs-lookup"><span data-stu-id="9c12b-160">When the SSA proxy in the SharePoint Enterprise App Farm sends a status query to the SSA in the SharePoint Services Farm, the following actions occur:</span></span> 
  
- <span data-ttu-id="9c12b-p113">如果查詢要求，SSA 查閱搜尋索引。探索回應傳回 SSA]、 [使用者通過 EDC。</span><span class="sxs-lookup"><span data-stu-id="9c12b-p113">If the request is a query, the SSA consults the search index. The discovery response is returned to the SSA and then to the user through the EDC.</span></span> 
    
- <span data-ttu-id="9c12b-163">如果寫入動作要求，SSA 服務會將寫入動作傳送至 SSA admin_db。</span><span class="sxs-lookup"><span data-stu-id="9c12b-163">If the request is a write action, the SSA service sends the write action to the SSA admin_db.</span></span> 
    
- <span data-ttu-id="9c12b-164">編目及回應結果要求從 SSA 傳送至 SharePoint 2013 內容伺服器陣列和回應傳回至 SSA。</span><span class="sxs-lookup"><span data-stu-id="9c12b-164">A crawl and responding results request is sent from the SSA to the SharePoint 2013 Content Farm and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="9c12b-165">編目及回應結果要求從 SSA 傳送至 Windows 檔案共用，並將回應傳回至 SSA。</span><span class="sxs-lookup"><span data-stu-id="9c12b-165">A crawl and responding results request is sent from the SSA to the Windows File Shares, and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="9c12b-166">擱置的動作、 回應或狀態更新的查詢 SSA 從傳送到 SharePoint 內容伺服器陣列中的 SSA proxy 並將回應傳回至 SSA。</span><span class="sxs-lookup"><span data-stu-id="9c12b-166">A query for pending action(s), responses, or status updates is sent from the SSA to the SSA proxy in the SharePoint Content Farm, and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="9c12b-167">Exchange 巨集指令/狀態要求從 SSA 傳送到 EWS proxy、 將 Exchange 查詢巨集指令/狀態要求傳送至 Exchange 2013 伺服器上的 Exchange Web 服務。</span><span class="sxs-lookup"><span data-stu-id="9c12b-167">An Exchange action/status request is sent from the SSA to the EWS proxy, which sends an Exchange Query action/status request to the Exchange Web Service on the Exchange 2013 server.</span></span> 
    
- <span data-ttu-id="9c12b-168">狀態查詢回應從 SSA 傳送到 SSA admin_db 並傳回至 SSA。</span><span class="sxs-lookup"><span data-stu-id="9c12b-168">A status query/response is sent from the SSA to the SSA admin_db and is returned to the SSA.</span></span> 
    
- <span data-ttu-id="9c12b-169">擱置巨集指令查詢回應從 SSA 傳送到 SSA admin_db 並傳回至 SSA。</span><span class="sxs-lookup"><span data-stu-id="9c12b-169">A pending action query/response is sent from the SSA to the SSA admin_db and is returned to the SSA.</span></span> 
    
#### <a name="sharepoint-2013-content-farm"></a><span data-ttu-id="9c12b-170">SharePoint 2013 內容伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="9c12b-170">SharePoint 2013 Content Farm</span></span>

<span data-ttu-id="9c12b-171">SharePoint 2013 內容伺服器陣列包含下列元件：</span><span class="sxs-lookup"><span data-stu-id="9c12b-171">The SharePoint 2013 Content Farm contains the following components:</span></span> 
  
- <span data-ttu-id="9c12b-172">SSA proxy</span><span class="sxs-lookup"><span data-stu-id="9c12b-172">SSA proxy</span></span> 
    
- <span data-ttu-id="9c12b-173">計時器工作</span><span class="sxs-lookup"><span data-stu-id="9c12b-173">Timer job</span></span> 
    
- <span data-ttu-id="9c12b-174">Contoso SharePoint 網站</span><span class="sxs-lookup"><span data-stu-id="9c12b-174">Contoso SharePoint site</span></span> 
    
- <span data-ttu-id="9c12b-175">Contoso SharePoint 內容</span><span class="sxs-lookup"><span data-stu-id="9c12b-175">Contoso SharePoint content</span></span> 
    
<span data-ttu-id="9c12b-176">當 SharePoint Services 伺服器陣列中的 SSA 將狀態查詢 SSA Proxy SharePoint 內容伺服器陣列中時，會發生下列動作：</span><span class="sxs-lookup"><span data-stu-id="9c12b-176">When the SSA in the SharePoint Services Farm sends a status query to the SSA Proxy in the SharePoint Content Farm, the following actions occur:</span></span> 
  
- <span data-ttu-id="9c12b-177">SharePoint 內容伺服器陣列中的 SSA proxy 會擱置的計時器工作狀態動作/回應將查詢傳送。</span><span class="sxs-lookup"><span data-stu-id="9c12b-177">The SSA proxy in the SharePoint Content Farm sends a query for pending actions/status response to the Timer job.</span></span> 
    
- <span data-ttu-id="9c12b-178">計時器工作會將要求傳送至 Contoso SharePoint 網站中，檢閱 Contoso SharePoint 內容。</span><span class="sxs-lookup"><span data-stu-id="9c12b-178">The Timer job sends a request to the Contoso SharePoint site, which reviews the Contoso SharePoint content.</span></span> 
    
- <span data-ttu-id="9c12b-179">計時器工作已傳送回應等候中的動作狀態查詢 SSA proxy SharePoint 內容伺服器陣列，然後它會傳送至 SharePoint Services 伺服器陣列中的 SSA 服務</span><span class="sxs-lookup"><span data-stu-id="9c12b-179">The response to the pending actions/status query is sent from the Timer job to the SSA proxy in the SharePoint Content Farm, and then it is sent to the SSA service in the SharePoint Services Farm</span></span> 
    
#### <a name="exchange-2013"></a><span data-ttu-id="9c12b-180">Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="9c12b-180">Exchange 2013</span></span>

<span data-ttu-id="9c12b-181">Exchange 2013 伺服器元件包含 Exchange Web 服務並提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="9c12b-181">The Exchange 2013 server component contains the Exchange Web Service and provides the following:</span></span> 
  
- <span data-ttu-id="9c12b-182">伺服器對伺服器信任/OAuth 的 SharePoint 2013 內容伺服器陣列與 Exchange 2013 間處理方式。</span><span class="sxs-lookup"><span data-stu-id="9c12b-182">Server-to-server Trust/OAuth is handled between the SharePoint 2013 Content Farm and Exchange 2013.</span></span> 
    
- <span data-ttu-id="9c12b-183">伺服器對伺服器信任/OAuth 會處理 Exchange 2013 和 Lync 2013 之間。</span><span class="sxs-lookup"><span data-stu-id="9c12b-183">Server-to-server Trust/OAuth is handled between Exchange 2013 and Lync 2013.</span></span> 
    
#### <a name="lync-2013"></a><span data-ttu-id="9c12b-184">Lync 2013</span><span class="sxs-lookup"><span data-stu-id="9c12b-184">Lync 2013</span></span>

<span data-ttu-id="9c12b-185">Lync 2013 元件封存在 Exchange 2013 的 Lync 內容。</span><span class="sxs-lookup"><span data-stu-id="9c12b-185">The Lync 2013 component archives Lync content in Exchange 2013.</span></span> 
  
#### <a name="windows-file-shares"></a><span data-ttu-id="9c12b-186">Windows 檔案共用</span><span class="sxs-lookup"><span data-stu-id="9c12b-186">Windows File Shares</span></span>

<span data-ttu-id="9c12b-187">[Windows 檔案共用元件提供 SharePoint Services 伺服器陣列中的 SSA 編目結果。</span><span class="sxs-lookup"><span data-stu-id="9c12b-187">The Windows File Shares component provides crawl results to the SSA in the SharePoint Services Farm.</span></span> 
  
### <a name="legend"></a><span data-ttu-id="9c12b-188">圖例</span><span class="sxs-lookup"><span data-stu-id="9c12b-188">Legend</span></span>

<span data-ttu-id="9c12b-189">這個圖表的圖例以圖形顯示不同類型的流量所述之不同的彩色行元件之間，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9c12b-189">The legend for this diagram graphically shows the different types of traffic depicted among the components in different colored lines as follows:</span></span> 
  
- <span data-ttu-id="9c12b-190">淺藍色線條： 查詢/動作-eDiscovery 查詢或巨集指令的資料</span><span class="sxs-lookup"><span data-stu-id="9c12b-190">Light blue line: Query/action - eDiscovery query or action data</span></span> 
    
- <span data-ttu-id="9c12b-191">橘色線條： eDisovery 回應-eDiscovery 查詢回應資料</span><span class="sxs-lookup"><span data-stu-id="9c12b-191">Orange line: eDisovery response - eDiscovery query response data</span></span> 
    
- <span data-ttu-id="9c12b-192">綠色線條： 狀態查詢/回應-eDiscovery 狀態查詢/回應資料</span><span class="sxs-lookup"><span data-stu-id="9c12b-192">Green line: Status query/response - eDiscovery status query/response data</span></span> 
    
- <span data-ttu-id="9c12b-193">紫色線條： Exchange 巨集指令/狀態要求 eDiscovery 要求的動作狀態的 Exchange 流量。</span><span class="sxs-lookup"><span data-stu-id="9c12b-193">Purple line: Exchange action/status request - eDiscovery request for action status for Exchange traffic.</span></span> 
    
- <span data-ttu-id="9c12b-194">紅色線： Exchange 資料/狀態回應-從 Exchange 的 eDiscovery 查詢或狀態回應。</span><span class="sxs-lookup"><span data-stu-id="9c12b-194">Red line: Exchange data/status response - eDiscovery query or status response from Exchange.</span></span> 
    
- <span data-ttu-id="9c12b-195">點線黑色線條： 伺服器對伺服器信任/Oauth</span><span class="sxs-lookup"><span data-stu-id="9c12b-195">Dotted black line: Server-to-Server Trust/Oauth</span></span> 
    
- <span data-ttu-id="9c12b-196">黑色實線： 編目/結果</span><span class="sxs-lookup"><span data-stu-id="9c12b-196">Solid black line: Crawl/results</span></span> 
    

