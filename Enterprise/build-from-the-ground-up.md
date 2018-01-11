---
title: "為基礎而建置"
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
ms.assetid: 84348d0c-d9d1-4a98-9b99-8433f9b70e45
description: "摘要： 取得雲端一組的詳細資料儲存區可用來建立您自己的存放服務或解決方案的建置組塊。"
ms.openlocfilehash: eabf38e0ccef3335b2d198a33f5622d0d449589a
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2018
---
# <a name="build-from-the-ground-up"></a><span data-ttu-id="31a0f-103">為基礎而建置</span><span class="sxs-lookup"><span data-stu-id="31a0f-103">Build from the ground up</span></span>

 <span data-ttu-id="31a0f-104">**摘要：**取得在雲端的詳細資訊可用來建立您自己的存放服務或解決方案的儲存空間建置組塊。</span><span class="sxs-lookup"><span data-stu-id="31a0f-104">**Summary:** Get the details on the set of cloud storage building blocks that you can use to create your own storage service or solution.</span></span>
  
<span data-ttu-id="31a0f-105">"從頭開始建置"儲存解決方案：</span><span class="sxs-lookup"><span data-stu-id="31a0f-105">"Build from the ground up" storage solutions:</span></span>
  
- <span data-ttu-id="31a0f-106">可讓您從頭開始建立您自己的儲存解決方案。</span><span class="sxs-lookup"><span data-stu-id="31a0f-106">Allow you to create your own storage solution from scratch.</span></span> 
    
- <span data-ttu-id="31a0f-107">需要使用 REST Api 的程式設計 （英文）。</span><span class="sxs-lookup"><span data-stu-id="31a0f-107">Requires programming using the REST APIs.</span></span>
    
- <span data-ttu-id="31a0f-108">提供最終的自訂和彈性。</span><span class="sxs-lookup"><span data-stu-id="31a0f-108">Provide the ultimate in customization and flexibility.</span></span>
    
<span data-ttu-id="31a0f-109">下列各節說明每個"從頭開始建置"存放區選項的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="31a0f-109">The following sections describe the details of each "Build from the ground up" storage option.</span></span>
  
## <a name="azure-storage-files"></a><span data-ttu-id="31a0f-110">Azure 存放區 （檔案）</span><span class="sxs-lookup"><span data-stu-id="31a0f-110">Azure Storage (files)</span></span>

### <a name="features"></a><span data-ttu-id="31a0f-111">功能</span><span class="sxs-lookup"><span data-stu-id="31a0f-111">Features</span></span>

- <span data-ttu-id="31a0f-112">容易移至雲端的舊版應用程式</span><span class="sxs-lookup"><span data-stu-id="31a0f-112">Makes it easier to move legacy applications to the cloud</span></span>
    
- <span data-ttu-id="31a0f-113">慣用的新應用程式的 blob 儲存</span><span class="sxs-lookup"><span data-stu-id="31a0f-113">Blob storage preferred for new applications</span></span>
    
- <span data-ttu-id="31a0f-114">可以從 Azure 虛擬機器裝載</span><span class="sxs-lookup"><span data-stu-id="31a0f-114">Can mount from an Azure virtual machine</span></span>
    
- <span data-ttu-id="31a0f-115">可以裝載內部部署與 SMB 3.0</span><span class="sxs-lookup"><span data-stu-id="31a0f-115">Can mount on-premises with SMB 3.0</span></span>
    
- <span data-ttu-id="31a0f-116">Linux 與 Windows 運作</span><span class="sxs-lookup"><span data-stu-id="31a0f-116">Works with Linux and Windows</span></span>
    
- <span data-ttu-id="31a0f-117">不支援 Azure AD 驗證或 Acl （Azure 儲存帳戶索引鍵可提供驗證和授權的存取權的檔案共用）</span><span class="sxs-lookup"><span data-stu-id="31a0f-117">Doesn't support Azure AD-based authentication or ACLs (Azure Storage account keys provide authentication and authorized access to the file share)</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="31a0f-118">一般用途</span><span class="sxs-lookup"><span data-stu-id="31a0f-118">Common uses</span></span>

- <span data-ttu-id="31a0f-119">移轉至雲端舊版依賴檔案共用的應用程式</span><span class="sxs-lookup"><span data-stu-id="31a0f-119">Migrating legacy applications to the cloud that rely on file shares</span></span>
    
- <span data-ttu-id="31a0f-120">共用開發及測試工具</span><span class="sxs-lookup"><span data-stu-id="31a0f-120">Share development and testing tools</span></span>
    
- <span data-ttu-id="31a0f-121">分散式應用程式來儲存記錄檔，診斷資料和損毀傾印</span><span class="sxs-lookup"><span data-stu-id="31a0f-121">Distributed apps can store logs, diagnostic data, and crash dumps</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="31a0f-122">主要儲存案例</span><span class="sxs-lookup"><span data-stu-id="31a0f-122">Key storage scenarios</span></span>

- <span data-ttu-id="31a0f-123">備份檔案</span><span class="sxs-lookup"><span data-stu-id="31a0f-123">Backup files</span></span>
    
### <a name="resources"></a><span data-ttu-id="31a0f-124">資源</span><span class="sxs-lookup"><span data-stu-id="31a0f-124">Resources</span></span>

<span data-ttu-id="31a0f-125">如需詳細資訊，請按一下[這裡](https://msdn.microsoft.com/library/azure/dn166972.aspx)。</span><span class="sxs-lookup"><span data-stu-id="31a0f-125">For additional information, click [here](https://msdn.microsoft.com/library/azure/dn166972.aspx).</span></span>
  
<span data-ttu-id="31a0f-126">成本資訊，請按一下[這裡](http://azure.microsoft.com/pricing/details/storage/)。</span><span class="sxs-lookup"><span data-stu-id="31a0f-126">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-blobs"></a><span data-ttu-id="31a0f-127">Azure 存放區 (blob)</span><span class="sxs-lookup"><span data-stu-id="31a0f-127">Azure Storage (blobs)</span></span>

### <a name="features"></a><span data-ttu-id="31a0f-128">功能</span><span class="sxs-lookup"><span data-stu-id="31a0f-128">Features</span></span>

- <span data-ttu-id="31a0f-129">儲存的每一個帳戶可以保留最多 500 TB （一個訂閱可以有多個儲存區帳戶）</span><span class="sxs-lookup"><span data-stu-id="31a0f-129">Each storage account can hold up to 500 TB (one subscription can have multiple storage accounts)</span></span>
    
- <span data-ttu-id="31a0f-130">儲存帳戶分成容器] 中，可以套用至他們的安全性，並可包含 blob</span><span class="sxs-lookup"><span data-stu-id="31a0f-130">Storage accounts are organized into containers, which can have security applied to them and can contain blobs</span></span>
    
- <span data-ttu-id="31a0f-131">封鎖 blob 最佳化的資料流和儲存雲端物件最多 200 GB 的大小</span><span class="sxs-lookup"><span data-stu-id="31a0f-131">Block blobs are optimized for streaming and storing cloud objects, up to 200 GB in size</span></span>
    
- <span data-ttu-id="31a0f-132">用來代表 PaaS 磁碟的最佳化頁面 blob 和支援隨機寫入多達 1 TB 的大小</span><span class="sxs-lookup"><span data-stu-id="31a0f-132">Page blobs are optimized for representing PaaS disks and supporting random writes, up to 1 TB in size</span></span>
    
- <span data-ttu-id="31a0f-133">附加的最佳化 blob 附加作業 195 GB</span><span class="sxs-lookup"><span data-stu-id="31a0f-133">Append blobs are optimized for append operations, up to 195 GB</span></span>
    
- <span data-ttu-id="31a0f-134">Premium 儲存體提供更快的 IOPS 透過 SSD 儲存</span><span class="sxs-lookup"><span data-stu-id="31a0f-134">Premium Storage provides faster IOPS through SSD storage</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="31a0f-135">一般用途</span><span class="sxs-lookup"><span data-stu-id="31a0f-135">Common uses</span></span>

- <span data-ttu-id="31a0f-136">檔案、 電腦、 資料庫及裝置影像和文字的 web 應用程式的備份</span><span class="sxs-lookup"><span data-stu-id="31a0f-136">Backups of files, computers, databases, and devices Images and text for web applications</span></span>
    
- <span data-ttu-id="31a0f-137">雲端應用程式的組態資料</span><span class="sxs-lookup"><span data-stu-id="31a0f-137">Configuration data for cloud applications</span></span>
    
- <span data-ttu-id="31a0f-138">大的資料，例如記錄及其他大型資料集</span><span class="sxs-lookup"><span data-stu-id="31a0f-138">Big data, such as logs and other large datasets</span></span>
    
- <span data-ttu-id="31a0f-139">Azure 用途 blob 其本身服務，例如 HDInsight 和虛擬機器的磁碟儲存空間</span><span class="sxs-lookup"><span data-stu-id="31a0f-139">Azure uses blob storage for its own services, such as HDInsight and virtual machine disks</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="31a0f-140">主要儲存案例</span><span class="sxs-lookup"><span data-stu-id="31a0f-140">Key storage scenarios</span></span>

- <span data-ttu-id="31a0f-141">管理資料</span><span class="sxs-lookup"><span data-stu-id="31a0f-141">Manage data</span></span>
    
### <a name="resources"></a><span data-ttu-id="31a0f-142">資源</span><span class="sxs-lookup"><span data-stu-id="31a0f-142">Resources</span></span>

<span data-ttu-id="31a0f-143">如需詳細資訊，請按一下[這裡](https://msdn.microsoft.com/library/azure/dd179376.aspx)。</span><span class="sxs-lookup"><span data-stu-id="31a0f-143">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179376.aspx).</span></span>
  
<span data-ttu-id="31a0f-144">成本資訊，請按一下[這裡](http://azure.microsoft.com/pricing/details/storage/)。</span><span class="sxs-lookup"><span data-stu-id="31a0f-144">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-queues"></a><span data-ttu-id="31a0f-145">Azure 存放區 （佇列）</span><span class="sxs-lookup"><span data-stu-id="31a0f-145">Azure Storage (queues)</span></span>

### <a name="features"></a><span data-ttu-id="31a0f-146">功能</span><span class="sxs-lookup"><span data-stu-id="31a0f-146">Features</span></span>

- <span data-ttu-id="31a0f-147">儲存帳戶可以包含任何數目的佇列</span><span class="sxs-lookup"><span data-stu-id="31a0f-147">Storage account can contain any number of queues</span></span>
    
- <span data-ttu-id="31a0f-148">佇列可以包含任何數目的郵件 （直到儲存帳戶已滿）</span><span class="sxs-lookup"><span data-stu-id="31a0f-148">Queue can contain any number of messages (until the storage account is full)</span></span>
    
- <span data-ttu-id="31a0f-149">佇列的郵件自動的七天後刪除若未擷取和刪除應用程式</span><span class="sxs-lookup"><span data-stu-id="31a0f-149">Queue messages are automatically deleted after seven days if not retrieved and deleted by an application</span></span>
    
- <span data-ttu-id="31a0f-150">郵件可能是最多 64 KB 的大小</span><span class="sxs-lookup"><span data-stu-id="31a0f-150">Messages may be up to 64 KB in size</span></span>
    
- <span data-ttu-id="31a0f-151">安全儲存帳戶層級</span><span class="sxs-lookup"><span data-stu-id="31a0f-151">Secured at storage account level</span></span>
    
- <span data-ttu-id="31a0f-152">佇列都是要將控制項的郵件未原始資料</span><span class="sxs-lookup"><span data-stu-id="31a0f-152">Queues are intended to pass control messages, not raw data</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="31a0f-153">一般用途</span><span class="sxs-lookup"><span data-stu-id="31a0f-153">Common uses</span></span>

- <span data-ttu-id="31a0f-154">建立傳送處理的非同步處理的工作項目</span><span class="sxs-lookup"><span data-stu-id="31a0f-154">Create a backlog of work to process asynchronously</span></span>
    
- <span data-ttu-id="31a0f-155">處理記錄訊息</span><span class="sxs-lookup"><span data-stu-id="31a0f-155">Processing log messages</span></span>
    
- <span data-ttu-id="31a0f-156">將分離應用程式</span><span class="sxs-lookup"><span data-stu-id="31a0f-156">Decouple applications</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="31a0f-157">主要儲存案例</span><span class="sxs-lookup"><span data-stu-id="31a0f-157">Key storage scenarios</span></span>

- <span data-ttu-id="31a0f-158">散佈事件</span><span class="sxs-lookup"><span data-stu-id="31a0f-158">Distribute events</span></span>
    
### <a name="resources"></a><span data-ttu-id="31a0f-159">資源</span><span class="sxs-lookup"><span data-stu-id="31a0f-159">Resources</span></span>

<span data-ttu-id="31a0f-160">如需詳細資訊，請按一下[這裡](https://msdn.microsoft.com/library/azure/dd179353.aspx)。</span><span class="sxs-lookup"><span data-stu-id="31a0f-160">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179353.aspx).</span></span>
  
<span data-ttu-id="31a0f-161">成本資訊，請按一下[這裡](http://azure.microsoft.com/pricing/details/storage/)。</span><span class="sxs-lookup"><span data-stu-id="31a0f-161">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-tables"></a><span data-ttu-id="31a0f-162">Azure 存放區 （表格）</span><span class="sxs-lookup"><span data-stu-id="31a0f-162">Azure Storage (tables)</span></span>

### <a name="features"></a><span data-ttu-id="31a0f-163">功能</span><span class="sxs-lookup"><span data-stu-id="31a0f-163">Features</span></span>

- <span data-ttu-id="31a0f-164">適合半結構化資料集</span><span class="sxs-lookup"><span data-stu-id="31a0f-164">Best for semi-structured datasets</span></span>
    
- <span data-ttu-id="31a0f-165">繁體中文 SQL 比通常較低成本</span><span class="sxs-lookup"><span data-stu-id="31a0f-165">Typically lower cost than traditional SQL</span></span>
    
- <span data-ttu-id="31a0f-166">如果查詢值的索引鍵查詢慢的非常快速</span><span class="sxs-lookup"><span data-stu-id="31a0f-166">Very fast if querying for key, slow if querying for value</span></span>
    
- <span data-ttu-id="31a0f-167">大大可擴充;最多個儲存區帳戶的限制資料表的任何數量</span><span class="sxs-lookup"><span data-stu-id="31a0f-167">Massively scalable; any amount of tables up to the limits of the storage account</span></span>
    
- <span data-ttu-id="31a0f-168">可透過 REST API、 有限的 oData 通訊協定、.NET</span><span class="sxs-lookup"><span data-stu-id="31a0f-168">Accessible through REST API, limited oData protocol, .NET</span></span>
    
- <span data-ttu-id="31a0f-169">值必須序列化</span><span class="sxs-lookup"><span data-stu-id="31a0f-169">Values must be serialized</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="31a0f-170">一般用途</span><span class="sxs-lookup"><span data-stu-id="31a0f-170">Common uses</span></span>

- <span data-ttu-id="31a0f-171">Web 應用程式的使用者資料</span><span class="sxs-lookup"><span data-stu-id="31a0f-171">User data for web applications</span></span>
    
- <span data-ttu-id="31a0f-172">通訊錄</span><span class="sxs-lookup"><span data-stu-id="31a0f-172">Address books</span></span>
    
- <span data-ttu-id="31a0f-173">裝置資訊</span><span class="sxs-lookup"><span data-stu-id="31a0f-173">Device information</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="31a0f-174">主要儲存案例</span><span class="sxs-lookup"><span data-stu-id="31a0f-174">Key storage scenarios</span></span>

- <span data-ttu-id="31a0f-175">管理資料</span><span class="sxs-lookup"><span data-stu-id="31a0f-175">Manage data</span></span>
    
### <a name="resources"></a><span data-ttu-id="31a0f-176">資源</span><span class="sxs-lookup"><span data-stu-id="31a0f-176">Resources</span></span>

<span data-ttu-id="31a0f-177">如需詳細資訊，請按一下[這裡](https://msdn.microsoft.com/library/azure/dd179463.aspx)。</span><span class="sxs-lookup"><span data-stu-id="31a0f-177">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179463.aspx).</span></span>
  
<span data-ttu-id="31a0f-178">成本資訊，請按一下[這裡](http://azure.microsoft.com/pricing/details/storage/)。</span><span class="sxs-lookup"><span data-stu-id="31a0f-178">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="microsoft-azure-storage-recommendations"></a><span data-ttu-id="31a0f-179">Microsoft Azure 儲存裝置建議</span><span class="sxs-lookup"><span data-stu-id="31a0f-179">Microsoft Azure Storage recommendations</span></span>

<span data-ttu-id="31a0f-180">設計與 Azure 儲存自訂的儲存解決方案時, 請謹記下列事項：</span><span class="sxs-lookup"><span data-stu-id="31a0f-180">When designing your custom storage solution with Azure Storage, keep the following in mind:</span></span>
  
- <span data-ttu-id="31a0f-181">利用更大的延展性增加大小 (> 100 TB) 或多個輸送量 （每秒 > 5000 個作業） 的多個儲存區帳戶。</span><span class="sxs-lookup"><span data-stu-id="31a0f-181">Leverage multiple storage accounts for greater scalability, either for increased size (> 100 TB) or for more throughput (> 5,000 operations per second).</span></span>
    
- <span data-ttu-id="31a0f-182">設計新增額外儲存空間帳戶組態變更為而非的程式碼變更的功能。</span><span class="sxs-lookup"><span data-stu-id="31a0f-182">Design the ability for adding additional storage accounts as a configuration change, not as a code change.</span></span>
    
- <span data-ttu-id="31a0f-183">謹慎選取來啟用想要的比例就插入及查詢效能的表格儲存的資料分割功能。</span><span class="sxs-lookup"><span data-stu-id="31a0f-183">Carefully select partitioning functions for table storage to enable the desired scale in terms of insert and query performance.</span></span>
    
- <span data-ttu-id="31a0f-184">選擇 [表格內容的中繼資料 （屬性名稱） 為簡短的欄名稱是預存頻內 （資料行名稱也 [計算向表格列大小上限 1 mb）。</span><span class="sxs-lookup"><span data-stu-id="31a0f-184">Choose short column names for table properties as the metadata (property names) are stored in-band (the column names also count towards the maximum row size of 1 MB).</span></span>
    
- <span data-ttu-id="31a0f-185">請儘可能批次到儲存作業。</span><span class="sxs-lookup"><span data-stu-id="31a0f-185">When possible, batch operations into storage.</span></span>
    
- <span data-ttu-id="31a0f-186">積極地快取設定資料庫中將分散式快取的資訊。</span><span class="sxs-lookup"><span data-stu-id="31a0f-186">Aggressively cache information in the configuration database into a distributed cache.</span></span>
    
- <span data-ttu-id="31a0f-187">如果應用程式效能及可靠性是取決於快取中擁有的資料可用的特定區段，您的應用程式應該拒絕傳入的要求之前快取已預先填入。</span><span class="sxs-lookup"><span data-stu-id="31a0f-187">If application performance or reliability is dependent on having a certain segment of data available in the cache, your application should refuse incoming requests until the cache has been pre-populated.</span></span>
    
- <span data-ttu-id="31a0f-188">在垂直 （由表格） 或水平 （跨多個擊碎線段資料表） 資料分割負載分散到多個資料庫。</span><span class="sxs-lookup"><span data-stu-id="31a0f-188">Partition the data in either vertically (by table) or horizontally (segment table across multiple shards) to spread the load across multiple databases.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="31a0f-189">請參閱</span><span class="sxs-lookup"><span data-stu-id="31a0f-189">See Also</span></span>

[<span data-ttu-id="31a0f-190">Microsoft Cloud Storage for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="31a0f-190">Microsoft Cloud Storage for Enterprise Architects</span></span>](microsoft-cloud-storage-for-enterprise-architects.md)
  
[<span data-ttu-id="31a0f-191">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="31a0f-191">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="31a0f-192">Microsoft 的 Enterprise Cloud 藍圖：IT 決策者的資源</span><span class="sxs-lookup"><span data-stu-id="31a0f-192">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



