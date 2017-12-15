---
title: "設計 Microsoft 雲端儲存空間"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 7e511118-1b75-413a-b959-ad0d3ffc9516
description: "摘要： 了解為何需要雲端儲存空間和檢閱 Microsoft 雲端儲存選項和主要儲存區案例的清單。"
ms.openlocfilehash: 3501f6a39498276d02fe4178f701a06dfb6a3e93
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="designing-storage-for-the-microsoft-cloud"></a><span data-ttu-id="ae6fd-103">設計 Microsoft 雲端儲存空間</span><span class="sxs-lookup"><span data-stu-id="ae6fd-103">Designing storage for the Microsoft cloud</span></span>

 <span data-ttu-id="ae6fd-104">**摘要：**了解為何需要雲端儲存並檢閱 Microsoft 雲端儲存選項和主要儲存區案例的清單。</span><span class="sxs-lookup"><span data-stu-id="ae6fd-104">**Summary:** Understand why you need cloud storage and review the list of Microsoft's cloud storage options and the key storage scenarios.</span></span>
  
<span data-ttu-id="ae6fd-105">整合您儲存與 Microsoft 雲端服務可讓您存取多種服務與雲端平台選項。</span><span class="sxs-lookup"><span data-stu-id="ae6fd-105">Integrating your storage with Microsoft cloud services gives you access to a broad range of services and cloud platform options.</span></span>
  
## <a name="why-cloud-storage"></a><span data-ttu-id="ae6fd-106">為什麼要選擇雲端儲存空間？</span><span class="sxs-lookup"><span data-stu-id="ae6fd-106">Why cloud storage?</span></span>

<span data-ttu-id="ae6fd-107">原因有兩個重要使用雲端儲存。</span><span class="sxs-lookup"><span data-stu-id="ae6fd-107">There are two key reasons to use cloud storage.</span></span>
  
1. <span data-ttu-id="ae6fd-108">市場的速度：</span><span class="sxs-lookup"><span data-stu-id="ae6fd-108">Speed to market:</span></span>
    
  - <span data-ttu-id="ae6fd-109">高可用性和嚴重損壞復原速度較快的組態</span><span class="sxs-lookup"><span data-stu-id="ae6fd-109">Faster configuration for high availability and disaster recovery</span></span>
    
  - <span data-ttu-id="ae6fd-110">若要購買沒有儲存硬體</span><span class="sxs-lookup"><span data-stu-id="ae6fd-110">No storage hardware to purchase</span></span>
    
  - <span data-ttu-id="ae6fd-111">Microsoft 雲端方案所提供的內建基層</span><span class="sxs-lookup"><span data-stu-id="ae6fd-111">Built-in plumbing provided by Microsoft's cloud offerings</span></span>
    
  - <span data-ttu-id="ae6fd-112">提供從任何地方世界</span><span class="sxs-lookup"><span data-stu-id="ae6fd-112">Available from anywhere in the world</span></span>
    
2. <span data-ttu-id="ae6fd-113">若要維護的較低成本：</span><span class="sxs-lookup"><span data-stu-id="ae6fd-113">Lower costs to maintain:</span></span>
    
  - <span data-ttu-id="ae6fd-114">Elasticity 擴充向上及向下儲存需求</span><span class="sxs-lookup"><span data-stu-id="ae6fd-114">Elasticity to scale up and down your storage demands</span></span>
    
  - <span data-ttu-id="ae6fd-115">維護或移轉未儲存硬體</span><span class="sxs-lookup"><span data-stu-id="ae6fd-115">No storage hardware to maintain or migrate</span></span>
    
  - <span data-ttu-id="ae6fd-116">Microsoft 是您內建管道工來維護和改善基礎結構</span><span class="sxs-lookup"><span data-stu-id="ae6fd-116">Microsoft is your built-in plumber to maintain and improve infrastructure</span></span>
    
  - <span data-ttu-id="ae6fd-117">在具有持續的改良功能的市場的最佳儲存安全性</span><span class="sxs-lookup"><span data-stu-id="ae6fd-117">Best storage security in the marketplace with ongoing improvements</span></span>
    
## <a name="microsoft-cloud-storage-options"></a><span data-ttu-id="ae6fd-118">Microsoft 雲端儲存選項</span><span class="sxs-lookup"><span data-stu-id="ae6fd-118">Microsoft cloud storage options</span></span>

<span data-ttu-id="ae6fd-119">為了協助您了解各種不同的雲端存放區選項，我們使用情況下比喻。</span><span class="sxs-lookup"><span data-stu-id="ae6fd-119">To help you understand the wide variety of cloud storage options, we use a construction analogy.</span></span>
  
### <a name="move-in-ready"></a><span data-ttu-id="ae6fd-120">移入就緒</span><span class="sxs-lookup"><span data-stu-id="ae6fd-120">Move-in ready</span></span>

<span data-ttu-id="ae6fd-p101">會於這些預先套裝的解決方案中使用現有的服務。使用立即和最少的設定。</span><span class="sxs-lookup"><span data-stu-id="ae6fd-p101">Use these prepackaged solutions that are bundled with existing services. Use immediately and with minimal configuration.</span></span>
  
- <span data-ttu-id="ae6fd-123">Office 365</span><span class="sxs-lookup"><span data-stu-id="ae6fd-123">Office 365</span></span>
    
- <span data-ttu-id="ae6fd-124">Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="ae6fd-124">Microsoft Intune</span></span>
    
- <span data-ttu-id="ae6fd-125">商務用 OneDrive</span><span class="sxs-lookup"><span data-stu-id="ae6fd-125">OneDrive for Business</span></span>
    
- <span data-ttu-id="ae6fd-126">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="ae6fd-126">Dynamics 365</span></span>
    
- <span data-ttu-id="ae6fd-127">Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="ae6fd-127">Visual Studio Team Services</span></span>
    
- <span data-ttu-id="ae6fd-128">Azure 網站復原</span><span class="sxs-lookup"><span data-stu-id="ae6fd-128">Azure Site Recovery</span></span>
    
- <span data-ttu-id="ae6fd-129">Yammer 網站共用</span><span class="sxs-lookup"><span data-stu-id="ae6fd-129">Yammer Site Sharing</span></span>
    
- <span data-ttu-id="ae6fd-130">Azure 備份</span><span class="sxs-lookup"><span data-stu-id="ae6fd-130">Azure Backup</span></span>
    
<span data-ttu-id="ae6fd-131">這每一項的詳細資料的雲端存放區選項，請參閱[移入就緒](move-in-ready.md)。</span><span class="sxs-lookup"><span data-stu-id="ae6fd-131">For the details of each of these cloud storage options, see [Move-in ready](move-in-ready.md).</span></span>
  
### <a name="some-assembly-required"></a><span data-ttu-id="ae6fd-132">有部分組件</span><span class="sxs-lookup"><span data-stu-id="ae6fd-132">Some assembly required</span></span>

<span data-ttu-id="ae6fd-133">使用這些現有服務以與其他設定起始點的儲存解決方案或自訂調整的編碼。</span><span class="sxs-lookup"><span data-stu-id="ae6fd-133">Use these existing services as a starting point for your storage solution with additional configuration or coding for a custom fit.</span></span>
  
- <span data-ttu-id="ae6fd-134">Azure 內容傳遞網路</span><span class="sxs-lookup"><span data-stu-id="ae6fd-134">Azure Content Delivery Network</span></span>
    
- <span data-ttu-id="ae6fd-135">Azure 媒體服務</span><span class="sxs-lookup"><span data-stu-id="ae6fd-135">Azure Media Services</span></span>
    
- <span data-ttu-id="ae6fd-136">HdInsight</span><span class="sxs-lookup"><span data-stu-id="ae6fd-136">HdInsight</span></span>
    
- <span data-ttu-id="ae6fd-137">Azure 意指快取</span><span class="sxs-lookup"><span data-stu-id="ae6fd-137">Azure Redis Cache</span></span>
    
- <span data-ttu-id="ae6fd-138">Azure SQL Database</span><span class="sxs-lookup"><span data-stu-id="ae6fd-138">Azure SQL Database</span></span>
    
- <span data-ttu-id="ae6fd-139">在 Azure 虛擬機器上的 SQL Server</span><span class="sxs-lookup"><span data-stu-id="ae6fd-139">SQL Server on an Azure VM</span></span>
    
- <span data-ttu-id="ae6fd-140">Azure 宇宙 DB</span><span class="sxs-lookup"><span data-stu-id="ae6fd-140">Azure Cosmos DB</span></span>
    
- <span data-ttu-id="ae6fd-141">StorSimple</span><span class="sxs-lookup"><span data-stu-id="ae6fd-141">StorSimple</span></span>
    
- <span data-ttu-id="ae6fd-142">Azure SQL 資料倉儲</span><span class="sxs-lookup"><span data-stu-id="ae6fd-142">Azure SQL Data Warehouse</span></span>
    
- <span data-ttu-id="ae6fd-143">Azure 資料湖存放區</span><span class="sxs-lookup"><span data-stu-id="ae6fd-143">Azure Data Lake Store</span></span>
    
<span data-ttu-id="ae6fd-144">如上述每個雲端儲存選項的詳細資訊，請參閱[部分組件所需](some-assembly-required.md)。</span><span class="sxs-lookup"><span data-stu-id="ae6fd-144">For the details of each of these cloud storage options, see [Some assembly required](some-assembly-required.md).</span></span>
  
### <a name="build-from-the-ground-up"></a><span data-ttu-id="ae6fd-145">為基礎而建置</span><span class="sxs-lookup"><span data-stu-id="ae6fd-145">Build from the ground up</span></span>

<span data-ttu-id="ae6fd-146">使用這些儲存建置組塊，與撰寫程式碼、 從頭開始建立您自己的儲存解決方案或應用程式。</span><span class="sxs-lookup"><span data-stu-id="ae6fd-146">Use these storage building blocks, along with coding, to create your own storage solution or apps from scratch.</span></span>
  
- <span data-ttu-id="ae6fd-147">Azure 存放區 （檔案）</span><span class="sxs-lookup"><span data-stu-id="ae6fd-147">Azure Storage (files)</span></span>
    
- <span data-ttu-id="ae6fd-148">Azure 存放區 (blob)</span><span class="sxs-lookup"><span data-stu-id="ae6fd-148">Azure Storage (blobs)</span></span>
    
- <span data-ttu-id="ae6fd-149">Azure 存放區 （佇列）</span><span class="sxs-lookup"><span data-stu-id="ae6fd-149">Azure Storage (queues)</span></span>
    
- <span data-ttu-id="ae6fd-150">Azure 存放區 （表格）</span><span class="sxs-lookup"><span data-stu-id="ae6fd-150">Azure Storage (tables)</span></span>
    
<span data-ttu-id="ae6fd-151">如上述每個雲端儲存選項的詳細資訊，請參閱[設定為基礎而建置](build-from-the-ground-up.md)。</span><span class="sxs-lookup"><span data-stu-id="ae6fd-151">For the details of each of these cloud storage options, see [Build from the ground up](build-from-the-ground-up.md).</span></span>
  
## <a name="key-storage-scenarios"></a><span data-ttu-id="ae6fd-152">主要儲存案例</span><span class="sxs-lookup"><span data-stu-id="ae6fd-152">Key storage scenarios</span></span>

<span data-ttu-id="ae6fd-153">以下是需要雲端儲存空間的主要案例：</span><span class="sxs-lookup"><span data-stu-id="ae6fd-153">Here are the key scenarios that require cloud-based storage:</span></span>
  
- <span data-ttu-id="ae6fd-154">快取資料</span><span class="sxs-lookup"><span data-stu-id="ae6fd-154">Cache data</span></span>
    
    <span data-ttu-id="ae6fd-155">加速最常使用的資料存取由儲存在高速快取。</span><span class="sxs-lookup"><span data-stu-id="ae6fd-155">Accelerate access to commonly used data by storing it in a high-speed cache.</span></span>
    
- <span data-ttu-id="ae6fd-156">小組成員與共同作業</span><span class="sxs-lookup"><span data-stu-id="ae6fd-156">Collaborate with team members</span></span>
    
    <span data-ttu-id="ae6fd-157">授與權限給多位使用者可在雲端儲存資料的存取權。</span><span class="sxs-lookup"><span data-stu-id="ae6fd-157">Grant permission to multiple users to allow access to data in cloud storage.</span></span>
    
- <span data-ttu-id="ae6fd-158">管理資料</span><span class="sxs-lookup"><span data-stu-id="ae6fd-158">Manage data</span></span>
    
    <span data-ttu-id="ae6fd-159">儲存、 移動或刪除內部或外部大量資料。</span><span class="sxs-lookup"><span data-stu-id="ae6fd-159">Store, move, or delete internal or external bulk data.</span></span>
    
- <span data-ttu-id="ae6fd-160">管理原始程式碼</span><span class="sxs-lookup"><span data-stu-id="ae6fd-160">Manage source code</span></span>
    
    <span data-ttu-id="ae6fd-161">上傳、 共同處理及雲端中執行應用程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="ae6fd-161">Upload, collaborate, and run application code files in the cloud.</span></span>
    
- <span data-ttu-id="ae6fd-162">備份檔案</span><span class="sxs-lookup"><span data-stu-id="ae6fd-162">Backup files</span></span>
    
    <span data-ttu-id="ae6fd-163">將內部或外部資料離站的複本儲存在多個雲端位置。</span><span class="sxs-lookup"><span data-stu-id="ae6fd-163">Store copies of internal or external data offsite in multiple cloud locations.</span></span>
    
- <span data-ttu-id="ae6fd-164">發佈的公司通訊</span><span class="sxs-lookup"><span data-stu-id="ae6fd-164">Publish company communications</span></span>
    
    <span data-ttu-id="ae6fd-165">建立發佈的內部或外部郵件的單一資料點。</span><span class="sxs-lookup"><span data-stu-id="ae6fd-165">Create a single point of publication for internal or external messages.</span></span>
    
- <span data-ttu-id="ae6fd-166">散佈數百萬的事件</span><span class="sxs-lookup"><span data-stu-id="ae6fd-166">Distribute millions of events</span></span>
    
    <span data-ttu-id="ae6fd-167">從網站、 應用程式] 與裝置建立遙測擷取的儲存空間。</span><span class="sxs-lookup"><span data-stu-id="ae6fd-167">Create storage for telemetry ingestion from websites, apps, and devices.</span></span>
    
- <span data-ttu-id="ae6fd-168">管理/服務影片</span><span class="sxs-lookup"><span data-stu-id="ae6fd-168">Manage/serve videos</span></span>
    
    <span data-ttu-id="ae6fd-169">儲存及客戶或組織中使用者提供視訊內容。</span><span class="sxs-lookup"><span data-stu-id="ae6fd-169">Store and serve video content to customers or organization users.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="ae6fd-170">下一步</span><span class="sxs-lookup"><span data-stu-id="ae6fd-170">Next step</span></span>

<span data-ttu-id="ae6fd-171">檢閱[準備移入](move-in-ready.md)雲端儲存選項。</span><span class="sxs-lookup"><span data-stu-id="ae6fd-171">Review the [Move-in ready](move-in-ready.md) cloud storage options.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ae6fd-172">See Also</span><span class="sxs-lookup"><span data-stu-id="ae6fd-172">See Also</span></span>

[<span data-ttu-id="ae6fd-173">Microsoft 雲端儲存為企業架構師的</span><span class="sxs-lookup"><span data-stu-id="ae6fd-173">Microsoft Cloud Storage for Enterprise Architects</span></span>](microsoft-cloud-storage-for-enterprise-architects.md)
  
[<span data-ttu-id="ae6fd-174">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="ae6fd-174">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="ae6fd-175">Microsoft 的 Enterprise Cloud 藍圖：IT 決策者的資源</span><span class="sxs-lookup"><span data-stu-id="ae6fd-175">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)


