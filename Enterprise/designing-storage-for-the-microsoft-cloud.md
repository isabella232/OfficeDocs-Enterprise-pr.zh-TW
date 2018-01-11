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
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 7e511118-1b75-413a-b959-ad0d3ffc9516
description: "摘要： 了解為何需要雲端儲存空間和檢閱 Microsoft 雲端儲存選項和主要儲存區案例的清單。"
ms.openlocfilehash: 199e385ea0238e8fb27c04153faf177df07e1025
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2018
---
# <a name="designing-storage-for-the-microsoft-cloud"></a><span data-ttu-id="dbdff-103">設計 Microsoft 雲端儲存空間</span><span class="sxs-lookup"><span data-stu-id="dbdff-103">Designing storage for the Microsoft cloud</span></span>

 <span data-ttu-id="dbdff-104">**摘要：**了解為何需要雲端儲存並檢閱 Microsoft 雲端儲存選項和主要儲存區案例的清單。</span><span class="sxs-lookup"><span data-stu-id="dbdff-104">**Summary:** Understand why you need cloud storage and review the list of Microsoft's cloud storage options and the key storage scenarios.</span></span>
  
<span data-ttu-id="dbdff-105">整合您儲存與 Microsoft 雲端服務可讓您存取多種服務與雲端平台選項。</span><span class="sxs-lookup"><span data-stu-id="dbdff-105">Integrating your storage with Microsoft cloud services gives you access to a broad range of services and cloud platform options.</span></span>
  
## <a name="why-cloud-storage"></a><span data-ttu-id="dbdff-106">為什麼要選擇雲端儲存空間？</span><span class="sxs-lookup"><span data-stu-id="dbdff-106">Why cloud storage?</span></span>

<span data-ttu-id="dbdff-107">原因有兩個重要使用雲端儲存。</span><span class="sxs-lookup"><span data-stu-id="dbdff-107">There are two key reasons to use cloud storage.</span></span>
  
1. <span data-ttu-id="dbdff-108">市場的速度：</span><span class="sxs-lookup"><span data-stu-id="dbdff-108">Speed to market:</span></span>
    
  - <span data-ttu-id="dbdff-109">高可用性和嚴重損壞復原速度較快的組態</span><span class="sxs-lookup"><span data-stu-id="dbdff-109">Faster configuration for high availability and disaster recovery</span></span>
    
  - <span data-ttu-id="dbdff-110">若要購買沒有儲存硬體</span><span class="sxs-lookup"><span data-stu-id="dbdff-110">No storage hardware to purchase</span></span>
    
  - <span data-ttu-id="dbdff-111">Microsoft 雲端方案所提供的內建基層</span><span class="sxs-lookup"><span data-stu-id="dbdff-111">Built-in plumbing provided by Microsoft's cloud offerings</span></span>
    
  - <span data-ttu-id="dbdff-112">提供從任何地方世界</span><span class="sxs-lookup"><span data-stu-id="dbdff-112">Available from anywhere in the world</span></span>
    
2. <span data-ttu-id="dbdff-113">若要維護的較低成本：</span><span class="sxs-lookup"><span data-stu-id="dbdff-113">Lower costs to maintain:</span></span>
    
  - <span data-ttu-id="dbdff-114">Elasticity 擴充向上及向下儲存需求</span><span class="sxs-lookup"><span data-stu-id="dbdff-114">Elasticity to scale up and down your storage demands</span></span>
    
  - <span data-ttu-id="dbdff-115">維護或移轉未儲存硬體</span><span class="sxs-lookup"><span data-stu-id="dbdff-115">No storage hardware to maintain or migrate</span></span>
    
  - <span data-ttu-id="dbdff-116">Microsoft 是您內建管道工來維護和改善基礎結構</span><span class="sxs-lookup"><span data-stu-id="dbdff-116">Microsoft is your built-in plumber to maintain and improve infrastructure</span></span>
    
  - <span data-ttu-id="dbdff-117">在具有持續的改良功能的市場的最佳儲存安全性</span><span class="sxs-lookup"><span data-stu-id="dbdff-117">Best storage security in the marketplace with ongoing improvements</span></span>
    
## <a name="microsoft-cloud-storage-options"></a><span data-ttu-id="dbdff-118">Microsoft 雲端儲存選項</span><span class="sxs-lookup"><span data-stu-id="dbdff-118">Microsoft cloud storage options</span></span>

<span data-ttu-id="dbdff-119">為了協助您了解各種不同的雲端存放區選項，我們使用情況下比喻。</span><span class="sxs-lookup"><span data-stu-id="dbdff-119">To help you understand the wide variety of cloud storage options, we use a construction analogy.</span></span>
  
### <a name="move-in-ready"></a><span data-ttu-id="dbdff-120">移入就緒</span><span class="sxs-lookup"><span data-stu-id="dbdff-120">Move-in ready</span></span>

<span data-ttu-id="dbdff-p101">會於這些預先套裝的解決方案中使用現有的服務。使用立即和最少的設定。</span><span class="sxs-lookup"><span data-stu-id="dbdff-p101">Use these prepackaged solutions that are bundled with existing services. Use immediately and with minimal configuration.</span></span>
  
- <span data-ttu-id="dbdff-123">Office 365</span><span class="sxs-lookup"><span data-stu-id="dbdff-123">Office 365</span></span>
    
- <span data-ttu-id="dbdff-124">Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="dbdff-124">Microsoft Intune</span></span>
    
- <span data-ttu-id="dbdff-125">商務用 OneDrive</span><span class="sxs-lookup"><span data-stu-id="dbdff-125">OneDrive for Business</span></span>
    
- <span data-ttu-id="dbdff-126">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="dbdff-126">Dynamics 365</span></span>
    
- <span data-ttu-id="dbdff-127">Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="dbdff-127">Visual Studio Team Services</span></span>
    
- <span data-ttu-id="dbdff-128">Azure 網站復原</span><span class="sxs-lookup"><span data-stu-id="dbdff-128">Azure Site Recovery</span></span>
    
- <span data-ttu-id="dbdff-129">Yammer 網站共用</span><span class="sxs-lookup"><span data-stu-id="dbdff-129">Yammer Site Sharing</span></span>
    
- <span data-ttu-id="dbdff-130">Azure 備份</span><span class="sxs-lookup"><span data-stu-id="dbdff-130">Azure Backup</span></span>
    
<span data-ttu-id="dbdff-131">這每一項的詳細資料的雲端存放區選項，請參閱[移入就緒](move-in-ready.md)。</span><span class="sxs-lookup"><span data-stu-id="dbdff-131">For the details of each of these cloud storage options, see [Move-in ready](move-in-ready.md).</span></span>
  
### <a name="some-assembly-required"></a><span data-ttu-id="dbdff-132">有部分組件</span><span class="sxs-lookup"><span data-stu-id="dbdff-132">Some assembly required</span></span>

<span data-ttu-id="dbdff-133">使用這些現有服務以與其他設定起始點的儲存解決方案或自訂調整的編碼。</span><span class="sxs-lookup"><span data-stu-id="dbdff-133">Use these existing services as a starting point for your storage solution with additional configuration or coding for a custom fit.</span></span>
  
- <span data-ttu-id="dbdff-134">Azure 內容傳遞網路</span><span class="sxs-lookup"><span data-stu-id="dbdff-134">Azure Content Delivery Network</span></span>
    
- <span data-ttu-id="dbdff-135">Azure 媒體服務</span><span class="sxs-lookup"><span data-stu-id="dbdff-135">Azure Media Services</span></span>
    
- <span data-ttu-id="dbdff-136">HdInsight</span><span class="sxs-lookup"><span data-stu-id="dbdff-136">HdInsight</span></span>
    
- <span data-ttu-id="dbdff-137">Azure 意指快取</span><span class="sxs-lookup"><span data-stu-id="dbdff-137">Azure Redis Cache</span></span>
    
- <span data-ttu-id="dbdff-138">Azure SQL Database</span><span class="sxs-lookup"><span data-stu-id="dbdff-138">Azure SQL Database</span></span>
    
- <span data-ttu-id="dbdff-139">在 Azure 虛擬機器上的 SQL Server</span><span class="sxs-lookup"><span data-stu-id="dbdff-139">SQL Server on an Azure VM</span></span>
    
- <span data-ttu-id="dbdff-140">Azure 宇宙 DB</span><span class="sxs-lookup"><span data-stu-id="dbdff-140">Azure Cosmos DB</span></span>
    
- <span data-ttu-id="dbdff-141">StorSimple</span><span class="sxs-lookup"><span data-stu-id="dbdff-141">StorSimple</span></span>
    
- <span data-ttu-id="dbdff-142">Azure SQL 資料倉儲</span><span class="sxs-lookup"><span data-stu-id="dbdff-142">Azure SQL Data Warehouse</span></span>
    
- <span data-ttu-id="dbdff-143">Azure 資料湖存放區</span><span class="sxs-lookup"><span data-stu-id="dbdff-143">Azure Data Lake Store</span></span>
    
<span data-ttu-id="dbdff-144">如上述每個雲端儲存選項的詳細資訊，請參閱[部分組件所需](some-assembly-required.md)。</span><span class="sxs-lookup"><span data-stu-id="dbdff-144">For the details of each of these cloud storage options, see [Some assembly required](some-assembly-required.md).</span></span>
  
### <a name="build-from-the-ground-up"></a><span data-ttu-id="dbdff-145">為基礎而建置</span><span class="sxs-lookup"><span data-stu-id="dbdff-145">Build from the ground up</span></span>

<span data-ttu-id="dbdff-146">使用這些儲存建置組塊，與撰寫程式碼、 從頭開始建立您自己的儲存解決方案或應用程式。</span><span class="sxs-lookup"><span data-stu-id="dbdff-146">Use these storage building blocks, along with coding, to create your own storage solution or apps from scratch.</span></span>
  
- <span data-ttu-id="dbdff-147">Azure 存放區 （檔案）</span><span class="sxs-lookup"><span data-stu-id="dbdff-147">Azure Storage (files)</span></span>
    
- <span data-ttu-id="dbdff-148">Azure 存放區 (blob)</span><span class="sxs-lookup"><span data-stu-id="dbdff-148">Azure Storage (blobs)</span></span>
    
- <span data-ttu-id="dbdff-149">Azure 存放區 （佇列）</span><span class="sxs-lookup"><span data-stu-id="dbdff-149">Azure Storage (queues)</span></span>
    
- <span data-ttu-id="dbdff-150">Azure 存放區 （表格）</span><span class="sxs-lookup"><span data-stu-id="dbdff-150">Azure Storage (tables)</span></span>
    
<span data-ttu-id="dbdff-151">如上述每個雲端儲存選項的詳細資訊，請參閱[設定為基礎而建置](build-from-the-ground-up.md)。</span><span class="sxs-lookup"><span data-stu-id="dbdff-151">For the details of each of these cloud storage options, see [Build from the ground up](build-from-the-ground-up.md).</span></span>
  
## <a name="key-storage-scenarios"></a><span data-ttu-id="dbdff-152">主要儲存案例</span><span class="sxs-lookup"><span data-stu-id="dbdff-152">Key storage scenarios</span></span>

<span data-ttu-id="dbdff-153">以下是需要雲端儲存空間的主要案例：</span><span class="sxs-lookup"><span data-stu-id="dbdff-153">Here are the key scenarios that require cloud-based storage:</span></span>
  
- <span data-ttu-id="dbdff-154">快取資料</span><span class="sxs-lookup"><span data-stu-id="dbdff-154">Cache data</span></span>
    
    <span data-ttu-id="dbdff-155">加速最常使用的資料存取由儲存在高速快取。</span><span class="sxs-lookup"><span data-stu-id="dbdff-155">Accelerate access to commonly used data by storing it in a high-speed cache.</span></span>
    
- <span data-ttu-id="dbdff-156">小組成員與共同作業</span><span class="sxs-lookup"><span data-stu-id="dbdff-156">Collaborate with team members</span></span>
    
    <span data-ttu-id="dbdff-157">授與權限給多位使用者可在雲端儲存資料的存取權。</span><span class="sxs-lookup"><span data-stu-id="dbdff-157">Grant permission to multiple users to allow access to data in cloud storage.</span></span>
    
- <span data-ttu-id="dbdff-158">管理資料</span><span class="sxs-lookup"><span data-stu-id="dbdff-158">Manage data</span></span>
    
    <span data-ttu-id="dbdff-159">儲存、 移動或刪除內部或外部大量資料。</span><span class="sxs-lookup"><span data-stu-id="dbdff-159">Store, move, or delete internal or external bulk data.</span></span>
    
- <span data-ttu-id="dbdff-160">管理原始程式碼</span><span class="sxs-lookup"><span data-stu-id="dbdff-160">Manage source code</span></span>
    
    <span data-ttu-id="dbdff-161">上傳、 共同處理及雲端中執行應用程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="dbdff-161">Upload, collaborate, and run application code files in the cloud.</span></span>
    
- <span data-ttu-id="dbdff-162">備份檔案</span><span class="sxs-lookup"><span data-stu-id="dbdff-162">Backup files</span></span>
    
    <span data-ttu-id="dbdff-163">將內部或外部資料離站的複本儲存在多個雲端位置。</span><span class="sxs-lookup"><span data-stu-id="dbdff-163">Store copies of internal or external data offsite in multiple cloud locations.</span></span>
    
- <span data-ttu-id="dbdff-164">發佈的公司通訊</span><span class="sxs-lookup"><span data-stu-id="dbdff-164">Publish company communications</span></span>
    
    <span data-ttu-id="dbdff-165">建立發佈的內部或外部郵件的單一資料點。</span><span class="sxs-lookup"><span data-stu-id="dbdff-165">Create a single point of publication for internal or external messages.</span></span>
    
- <span data-ttu-id="dbdff-166">散佈數百萬的事件</span><span class="sxs-lookup"><span data-stu-id="dbdff-166">Distribute millions of events</span></span>
    
    <span data-ttu-id="dbdff-167">從網站、 應用程式] 與裝置建立遙測擷取的儲存空間。</span><span class="sxs-lookup"><span data-stu-id="dbdff-167">Create storage for telemetry ingestion from websites, apps, and devices.</span></span>
    
- <span data-ttu-id="dbdff-168">管理/服務影片</span><span class="sxs-lookup"><span data-stu-id="dbdff-168">Manage/serve videos</span></span>
    
    <span data-ttu-id="dbdff-169">儲存及客戶或組織中使用者提供視訊內容。</span><span class="sxs-lookup"><span data-stu-id="dbdff-169">Store and serve video content to customers or organization users.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="dbdff-170">下一步</span><span class="sxs-lookup"><span data-stu-id="dbdff-170">Next step</span></span>

<span data-ttu-id="dbdff-171">檢閱[準備移入](move-in-ready.md)雲端儲存選項。</span><span class="sxs-lookup"><span data-stu-id="dbdff-171">Review the [Move-in ready](move-in-ready.md) cloud storage options.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="dbdff-172">請參閱</span><span class="sxs-lookup"><span data-stu-id="dbdff-172">See Also</span></span>

[<span data-ttu-id="dbdff-173">Microsoft Cloud Storage for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="dbdff-173">Microsoft Cloud Storage for Enterprise Architects</span></span>](microsoft-cloud-storage-for-enterprise-architects.md)
  
[<span data-ttu-id="dbdff-174">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="dbdff-174">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="dbdff-175">Microsoft 的 Enterprise Cloud 藍圖：IT 決策者的資源</span><span class="sxs-lookup"><span data-stu-id="dbdff-175">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)


