---
title: SharePoint Server 2007 終止支援藍圖
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 01/28/2019
audience: ITPro
ms.topic: conceptual
f1_keywords:
- vsemail
- MS_WSS_DirectoryManagement
- MS_WSS_ConfigEmail
- globalemailconfig
- configssc
- AppDefToBDC
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- OFU120
- SPS150
- OSU140
- WSU120
- OSR120
- SPO160
- PJW120
- SPB160
- OSI150
- OSI160
- BSA160
- OSU160
ms.assetid: ba124775-d5c0-4d68-b88d-8458ad4c3717
description: 於 2017 年 10 月 10 日，支援結束 for SharePoint Server 2007。 閱讀本篇文章以了解升級的選項，進行疑難排解，最佳作法、 系統需求、 升級的步驟，以及如何取得 Microsoft 合作夥伴提供的協助。
ms.openlocfilehash: 5e5f697f64c520ec1be2b055be0fd42e1742a9ed
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070719"
---
# <a name="sharepoint-server-2007-end-of-support-roadmap"></a><span data-ttu-id="edd15-104">SharePoint Server 2007 終止支援藍圖</span><span class="sxs-lookup"><span data-stu-id="edd15-104">SharePoint Server 2007 end of support roadmap</span></span>

<span data-ttu-id="edd15-105">於**2017 年 10 月 10 日**，Microsoft Office SharePoint Server 2007 會達到終止支援。</span><span class="sxs-lookup"><span data-stu-id="edd15-105">On **October 10, 2017**, Microsoft Office SharePoint Server 2007 reached end of support.</span></span> <span data-ttu-id="edd15-106">如果您還沒有開始從 SharePoint Server 2007 移轉至 Office 365 或較新版本的 SharePoint Server 內部部署，現在是以開始規劃的時間。</span><span class="sxs-lookup"><span data-stu-id="edd15-106">If you haven't begun your migration from SharePoint Server 2007 to Office 365 or a newer version of SharePoint Server on-premises, now's the time to start planning.</span></span> <span data-ttu-id="edd15-107">本文詳述資源以協助將資料移轉至 SharePoint Online，或升級 SharePoint Server 內部的人員。</span><span class="sxs-lookup"><span data-stu-id="edd15-107">This article details resources to help people migrate data to SharePoint Online, or upgrade your SharePoint Server on-premises.</span></span> 
  
## <a name="what-does-end-of-support-mean"></a><span data-ttu-id="edd15-108">支援平均數的哪些並結束？</span><span class="sxs-lookup"><span data-stu-id="edd15-108">What does end of support mean?</span></span>

<span data-ttu-id="edd15-109">SharePoint Server 一樣幾乎所有的 Microsoft 產品中，有支援週期期間 Microsoft 提供的新功能、 錯誤修正程式、 安全性修正程式、 等等。</span><span class="sxs-lookup"><span data-stu-id="edd15-109">SharePoint Server, like almost all Microsoft products, has a support lifecycle during which Microsoft provides new features, bug fixes, security fixes, and so on.</span></span> <span data-ttu-id="edd15-110">此生命週期通常會持續 10 年起的產品的初始版本，與此生命週期結束稱為 「 支援的產品的結尾。</span><span class="sxs-lookup"><span data-stu-id="edd15-110">This lifecycle typically lasts for 10 years from the date of the product's initial release, and the end of this lifecycle is known as the product's end of support.</span></span> <span data-ttu-id="edd15-111">在結尾的支援，Microsoft 不再提供：</span><span class="sxs-lookup"><span data-stu-id="edd15-111">At end of support, Microsoft no longer provides:</span></span>
  
- <span data-ttu-id="edd15-112">技術支援問題，可能會發生;</span><span class="sxs-lookup"><span data-stu-id="edd15-112">Technical support for problems that may occur;</span></span>
    
- <span data-ttu-id="edd15-113">錯誤修正問題，會發現及，可能會影響 exchange 的穩定性與可用性的伺服器;</span><span class="sxs-lookup"><span data-stu-id="edd15-113">Bug fixes for issues that are discovered and that may impact the stability and usability of the server;</span></span>
    
- <span data-ttu-id="edd15-114">安全性問題修正，會發現及，可能會讓伺服器受到安全性弱點; 的弱點和</span><span class="sxs-lookup"><span data-stu-id="edd15-114">Security fixes for vulnerabilities that are discovered and that may make the server vulnerable to security breaches; and</span></span> 
    
- <span data-ttu-id="edd15-115">時間的時區更新。</span><span class="sxs-lookup"><span data-stu-id="edd15-115">Time zone updates.</span></span>
    
<span data-ttu-id="edd15-116">雖然您的 SharePoint Server 2007 伺服器陣列還是會正常運作之後年 10 月 10，2017，沒有進一步更新及修補程式，或修正會出貨產品 （包括安全性修補程式/修正），以及 Microsoft 支援服務將會完全移至其支援人員的協助較新版本的產品。</span><span class="sxs-lookup"><span data-stu-id="edd15-116">Though your SharePoint Server 2007 farm will still be operational after October 10, 2017, no further updates, patches, or fixes will be shipped for the product (including security patches/fixes), and Microsoft Support will have fully shifted its support efforts to more recent versions of the product.</span></span> <span data-ttu-id="edd15-117">因為不再支援或修補，將會安裝，支援方法的結尾為您應該升級、 產品或移轉重要的資料。</span><span class="sxs-lookup"><span data-stu-id="edd15-117">Because your installation will no longer supported or patched, as end of support approaches you should upgrade the product, or migrate important data.</span></span>
  
> [!TIP]
> <span data-ttu-id="edd15-118">如果您已經尚未規劃升級或移轉，請參閱：[要考慮 SharePoint 2007 移轉選項](sharepoint-2007-migration-options.md)，若要開始的位置的一些範例。</span><span class="sxs-lookup"><span data-stu-id="edd15-118">If you haven't already planned for upgrade or migration, please see: [SharePoint 2007 migration options to consider](sharepoint-2007-migration-options.md), for some examples of where to begin.</span></span> <span data-ttu-id="edd15-119">您也可以搜尋[的 Microsoft 合作夥伴](https://go.microsoft.com/fwlink/?linkid=841249)可協助進行升級或 Office 365 移轉 （或兩者）。</span><span class="sxs-lookup"><span data-stu-id="edd15-119">You can also search for [Microsoft Partners](https://go.microsoft.com/fwlink/?linkid=841249) who can help with upgrade or Office 365 migration (or both).</span></span> 
  
<span data-ttu-id="edd15-120">如需達到終止支援的 Office 2007 伺服器的詳細資訊，請參閱 <<c0>資源可以幫助您升級從 Office 2007 伺服器和用戶端。</span><span class="sxs-lookup"><span data-stu-id="edd15-120">For more information about Office 2007 servers reaching the end of support, see [Resources to help you upgrade from Office 2007 servers and clients](upgrade-from-office-2007-servers-and-products.md).</span></span>
  
## <a name="what-are-my-options"></a><span data-ttu-id="edd15-121">我的選項為何？</span><span class="sxs-lookup"><span data-stu-id="edd15-121">What are my options?</span></span>

<span data-ttu-id="edd15-122">您第一張停駐點應是[產品生命週期網站](https://go.microsoft.com/fwlink/?linkid=843148)。</span><span class="sxs-lookup"><span data-stu-id="edd15-122">Your first stop should be the [Product Lifecycle site](https://go.microsoft.com/fwlink/?linkid=843148).</span></span> <span data-ttu-id="edd15-123">如果您有已過時内部署 Microsoft 產品，您應檢查其支援日期結尾因此，一年或操作出-或，只要您移轉通常都需要-您可以排程升級或移轉。</span><span class="sxs-lookup"><span data-stu-id="edd15-123">If you have an on-premises Microsoft product that is aging, you should check for its end of support date so that, a year or so out - or as long as your migrations generally require - you can schedule upgrade or migrations.</span></span> <span data-ttu-id="edd15-124">當選擇 [下一步]，它可能協助認為方面功能可能會不夠好，更好的而且最佳過濾的產品功能。</span><span class="sxs-lookup"><span data-stu-id="edd15-124">When choosing the next step, it might help to think in terms of what would be good enough, better, and best when it comes to product features.</span></span> <span data-ttu-id="edd15-125">以下為範例：</span><span class="sxs-lookup"><span data-stu-id="edd15-125">Here's an example:</span></span>
  
|<span data-ttu-id="edd15-126">**良好**</span><span class="sxs-lookup"><span data-stu-id="edd15-126">**Good**</span></span>|<span data-ttu-id="edd15-127">**更佳**</span><span class="sxs-lookup"><span data-stu-id="edd15-127">**Better**</span></span>|<span data-ttu-id="edd15-128">**最佳**</span><span class="sxs-lookup"><span data-stu-id="edd15-128">**Best**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="edd15-129">SharePoint Server 2010</span><span class="sxs-lookup"><span data-stu-id="edd15-129">SharePoint Server 2010</span></span>  <br/> |<span data-ttu-id="edd15-130">SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="edd15-130">SharePoint Server 2013</span></span>  <br/> |<span data-ttu-id="edd15-131">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="edd15-131">SharePoint Online</span></span>  <br/> |
||<span data-ttu-id="edd15-132">SharePoint 混合式</span><span class="sxs-lookup"><span data-stu-id="edd15-132">SharePoint Hybrid</span></span>  <br/> |<span data-ttu-id="edd15-133">SharePoint Server 2016</span><span class="sxs-lookup"><span data-stu-id="edd15-133">SharePoint Server 2016</span></span>  <br/> |
|||<span data-ttu-id="edd15-134">SharePoint 混合式</span><span class="sxs-lookup"><span data-stu-id="edd15-134">SharePoint Hybrid</span></span>  <br/> |
   
<span data-ttu-id="edd15-135">如果您選擇 [選項] 的低刻度的上方 （不夠好），請記得您想要開始從 SharePoint Server 2007 的移轉後很快規劃升級已完成。</span><span class="sxs-lookup"><span data-stu-id="edd15-135">If you choose options on the low end of the scale (good enough), remember you will need to begin planning for upgrade very soon after migration from SharePoint Server 2007 is complete.</span></span> <span data-ttu-id="edd15-136">（SharePoint Server 2007 支援的結尾是 2017 年 10 月 10 日。</span><span class="sxs-lookup"><span data-stu-id="edd15-136">(end of support for SharePoint Server 2007 is October 10, 2017.</span></span> <span data-ttu-id="edd15-137">請注意，這些日期會受到變更，並檢查[產品生命週期網站](https://support.microsoft.com/en-us/lifecycle)）。</span><span class="sxs-lookup"><span data-stu-id="edd15-137">Please note that these dates are subject to change and check the [Product Lifecycle site](https://support.microsoft.com/en-us/lifecycle).)</span></span>
  
## <a name="where-can-i-go-next"></a><span data-ttu-id="edd15-138">我移其中下一個？</span><span class="sxs-lookup"><span data-stu-id="edd15-138">Where can I go next?</span></span>

<span data-ttu-id="edd15-139">SharePoint Server 可以是安裝於內部上您自己的伺服器，或您可以使用 SharePoint Online，也就是屬於 Microsoft Office 365 線上服務。</span><span class="sxs-lookup"><span data-stu-id="edd15-139">SharePoint Server can be installed on-premises on your own servers, or you can use SharePoint Online, which is an online service that is part of Microsoft Office 365.</span></span> <span data-ttu-id="edd15-140">您可以選擇：</span><span class="sxs-lookup"><span data-stu-id="edd15-140">You can choose to:</span></span>
  
- <span data-ttu-id="edd15-141">移轉至 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="edd15-141">Migrate to SharePoint Online</span></span>
    
- <span data-ttu-id="edd15-142">升級 SharePoint Server 內部部署</span><span class="sxs-lookup"><span data-stu-id="edd15-142">Upgrade SharePoint Server on-premises</span></span>
    
- <span data-ttu-id="edd15-143">執行這兩個以上</span><span class="sxs-lookup"><span data-stu-id="edd15-143">Do both of the above</span></span>
    
- <span data-ttu-id="edd15-144">實作[SharePoint 混合式](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)解決方案</span><span class="sxs-lookup"><span data-stu-id="edd15-144">Implement a [SharePoint hybrid](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) solution</span></span> 
    
<span data-ttu-id="edd15-145">請注意的隱藏的成本與維護接下來，在伺服器陣列相關聯維護或移轉自訂項目，並升級 SharePoint Server 所依存的硬體。</span><span class="sxs-lookup"><span data-stu-id="edd15-145">Be aware of hidden costs associated with maintaining a server farm going forward, maintaining or migrating customizations, and upgrading the hardware upon which SharePoint Server depends.</span></span> <span data-ttu-id="edd15-146">如果是必要性; 具有內部部署 SharePoint Server 伺服器陣列薪水否則，如果您在舊版的 SharePoint 伺服器，不需要大量的自訂，執行您的伺服器陣列您可以受益於計劃性遷移到 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="edd15-146">Having an on-premises SharePoint Server farm is rewarding if it is a necessity; otherwise, if you run your farm on legacy SharePoint Servers, without heavy customization, you can benefit from a planned migration to SharePoint Online.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="edd15-147">如果不常使用 SharePoint 2007 中的內容，則，沒有另一個選項。</span><span class="sxs-lookup"><span data-stu-id="edd15-147">There is another option if the content in SharePoint 2007 is infrequently used.</span></span> <span data-ttu-id="edd15-148">某些 SharePoint 系統管理員可以選擇[建立 Office 365 訂閱](https://go.microsoft.com/fwlink/?linkid=843152)，請設定全新的 SharePoint Online 網站，，然後執行全新，地開 SharePoint 2007 剪下只最重要的文件帶到最新的 SharePoint Online 網站。</span><span class="sxs-lookup"><span data-stu-id="edd15-148">Some SharePoint Administrators may choose to [create an Office 365 Subscription](https://go.microsoft.com/fwlink/?linkid=843152), set up a brand new SharePoint Online site, and then cut away from SharePoint 2007, cleanly, taking only the most essential documents to the fresh SharePoint Online sites.</span></span> <span data-ttu-id="edd15-149">從那裡，資料可能會耗盡從 SharePoint 2007 網站到封存。</span><span class="sxs-lookup"><span data-stu-id="edd15-149">From there, data may be drained from the SharePoint 2007 site into archives.</span></span> <span data-ttu-id="edd15-150">授與使用者的運作方式與資料 SharePoint 2007 安裝的思考。</span><span class="sxs-lookup"><span data-stu-id="edd15-150">Give thought to how users work with data your SharePoint 2007 installation.</span></span> <span data-ttu-id="edd15-151">可能有創意方法若要解決此問題 ！</span><span class="sxs-lookup"><span data-stu-id="edd15-151">There may be creative ways to resolve this problem!</span></span> 
  
|<span data-ttu-id="edd15-152">**SharePoint Online (SPO)**</span><span class="sxs-lookup"><span data-stu-id="edd15-152">**SharePoint Online (SPO)**</span></span>|<span data-ttu-id="edd15-153">**SharePoint Server 內部部署**</span><span class="sxs-lookup"><span data-stu-id="edd15-153">**SharePoint Server on-premises**</span></span>|
|:-----|:-----|
|<span data-ttu-id="edd15-154">高成本的時間 (計劃 / 執行 / 驗證)</span><span class="sxs-lookup"><span data-stu-id="edd15-154">High cost in time (plan / execution / verification)</span></span>  <br/> |<span data-ttu-id="edd15-155">高成本的時間 (計劃 / 執行 / 驗證)</span><span class="sxs-lookup"><span data-stu-id="edd15-155">High cost in time (plan / execution / verification)</span></span>  <br/> |
|<span data-ttu-id="edd15-156">成本較低的資金 （沒有硬體購買）</span><span class="sxs-lookup"><span data-stu-id="edd15-156">Lower cost in funds (no hardware purchases)</span></span>  <br/> |<span data-ttu-id="edd15-157">在 [資金成本較高 (硬體 + 適用於開發人員 / 管理員)</span><span class="sxs-lookup"><span data-stu-id="edd15-157">Higher cost in funds (hardware + devs / admins)</span></span>  <br/> |
|<span data-ttu-id="edd15-158">在移轉的一次性成本</span><span class="sxs-lookup"><span data-stu-id="edd15-158">One-time cost in migration</span></span>  <br/> |<span data-ttu-id="edd15-159">未來移轉每重複的一次性成本</span><span class="sxs-lookup"><span data-stu-id="edd15-159">One-time cost repeated per future migration</span></span>  <br/> |
|<span data-ttu-id="edd15-160">低的整體擁有成本 / 維護</span><span class="sxs-lookup"><span data-stu-id="edd15-160">Low total cost of ownership / maintenance</span></span>  <br/> |<span data-ttu-id="edd15-161">高的整體擁有成本 / 維護</span><span class="sxs-lookup"><span data-stu-id="edd15-161">High total cost of ownership / maintenance</span></span>  <br/> |
   
<span data-ttu-id="edd15-162">當您移轉到 Office 365 時，一次移動會有預付，粗成本時您正在組織資料，並決定要採取至雲端的項目以及要留下項目。</span><span class="sxs-lookup"><span data-stu-id="edd15-162">When you migrate to Office 365, the one-time move will have a heavier cost up-front, while you're organizing data and deciding what to take to the cloud and what to leave behind.</span></span> <span data-ttu-id="edd15-163">不過，就會自動從該點開始升級、 您不再需要管理的硬體和軟體更新，並執行時間的伺服器陣列會備份由 Microsoft 服務層級協議 ([SLA](https://go.microsoft.com/fwlink/?linkid=843153))。</span><span class="sxs-lookup"><span data-stu-id="edd15-163">However, upgrades will be automatic from that point, you will no longer need to manage hardware and software updates, and the up-time of your farm will be backed by a Microsoft Service Level Agreement ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)).</span></span>
  
### <a name="migrate-to-sharepoint-online"></a><span data-ttu-id="edd15-164">移轉至 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="edd15-164">Migrate to SharePoint Online</span></span>

<span data-ttu-id="edd15-165">請確定 SharePoint Online 具有您需要檢閱相關聯的服務描述的所有功能。</span><span class="sxs-lookup"><span data-stu-id="edd15-165">Make sure that SharePoint Online has all the features you need by reviewing the associated service description.</span></span> <span data-ttu-id="edd15-166">以下是所有 Office 365 服務描述的連結：</span><span class="sxs-lookup"><span data-stu-id="edd15-166">Here's the link to all Office 365 Service Descriptions:</span></span>
  
[<span data-ttu-id="edd15-167">Office 365 服務描述</span><span class="sxs-lookup"><span data-stu-id="edd15-167">Office 365 Service Descriptions</span></span>](https://go.microsoft.com/fwlink/?linkid=272060)
  
<span data-ttu-id="edd15-168">沒有直接從 SharePoint 2007 移轉至 SharePoint Online; 方法會以手動方式完成您移至 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="edd15-168">There is no direct way to migrate from SharePoint 2007 to SharePoint Online; your move to SharePoint Online would be done manually.</span></span> <span data-ttu-id="edd15-169">如果您升級至 SharePoint Server 2013 或 SharePoint Server 2016，您移動可能也需要使用 SharePoint 移轉 API （例如移轉到商務用 OneDrive 的資訊）。</span><span class="sxs-lookup"><span data-stu-id="edd15-169">If you upgrade to SharePoint Server 2013 or SharePoint Server 2016, your move might also involve using the SharePoint Migration API (to migrate information into OneDrive for Business, for example).</span></span>
  
|<span data-ttu-id="edd15-170">**線上 Pro**</span><span class="sxs-lookup"><span data-stu-id="edd15-170">**Online Pro**</span></span>|<span data-ttu-id="edd15-171">**線上詐騙**</span><span class="sxs-lookup"><span data-stu-id="edd15-171">**Online Con**</span></span>|
|:-----|:-----|
|<span data-ttu-id="edd15-172">Microsoft 提供 SPO 硬體和所有硬體管理。</span><span class="sxs-lookup"><span data-stu-id="edd15-172">Microsoft supplies SPO hardware and all hardware administration.</span></span>  <br/> |<span data-ttu-id="edd15-173">可用的功能可能會不同 SharePoint Server 內部部署和 SPO 之間。</span><span class="sxs-lookup"><span data-stu-id="edd15-173">Available features may be different between SharePoint Server on-premises and SPO.</span></span>  <br/> |
|<span data-ttu-id="edd15-174">您是全域系統管理員的您的訂閱，並可能會將系統管理員指派給 SPO 網站。</span><span class="sxs-lookup"><span data-stu-id="edd15-174">You are the global administrator of your subscription, and may assign administrators to SPO sites.</span></span>  <br/> |<span data-ttu-id="edd15-175">某些 SharePoint Server 內部部署不存在 （或不是必要的） 中的伺服器陣列管理員可用的動作包含在 Office 365 中的 SharePoint 系統管理員角色。</span><span class="sxs-lookup"><span data-stu-id="edd15-175">Some actions available to a Farm Administrator in SharePoint Server on-premises do not exist (or are not necessary) included in the SharePoint Administrator role in Office 365.</span></span>  <br/> |
|<span data-ttu-id="edd15-176">Microsoft 會套用修補程式、 修正和更新為基礎的硬體及軟體。</span><span class="sxs-lookup"><span data-stu-id="edd15-176">Microsoft applies patches, fixes and updates to underlying hardware and software.</span></span>  <br/> |<span data-ttu-id="edd15-177">因為無法存取服務中的基礎檔案系統，有一些自訂項目。</span><span class="sxs-lookup"><span data-stu-id="edd15-177">Because there is no access to the underlying file system in the service, some customizations are limited.</span></span>  <br/> |
|<span data-ttu-id="edd15-178">Microsoft 會發佈[服務層級協議](https://go.microsoft.com/fwlink/?linkid=843153)，並快速地移到解決服務層級事件。</span><span class="sxs-lookup"><span data-stu-id="edd15-178">Microsoft publishes [Service Level Agreements](https://go.microsoft.com/fwlink/?linkid=843153) and moves quickly to resolve service level incidents.</span></span>  <br/> |<span data-ttu-id="edd15-179">備份及還原其他復原選項會自動完成的 SharePoint Online 中的服務-備份會覆寫如果沒有提供使用。</span><span class="sxs-lookup"><span data-stu-id="edd15-179">Backup and restore and other recovery options are automated by the service in SharePoint Online - backups are overwritten if not used.</span></span>  <br/> |
|<span data-ttu-id="edd15-180">安全性測試及伺服器的效能調整會持續在服務中由執行 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="edd15-180">Security testing and server performance tuning are carried out on an ongoing basis in the service by Microsoft.</span></span>  <br/> |<span data-ttu-id="edd15-181">變更使用者介面與其他 SharePoint 功能會安裝服務，以及可能需要重新開啟或關閉切換。</span><span class="sxs-lookup"><span data-stu-id="edd15-181">Changes to the user interface and other SharePoint features are installed by the service and may need to be toggled on or off.</span></span>  <br/> |
|<span data-ttu-id="edd15-182">Office 365 符合許多業界標準： [Office 365 合規性](https://go.microsoft.com/fwlink/?linkid=843165)。</span><span class="sxs-lookup"><span data-stu-id="edd15-182">Office 365 meets many industry standards: [Office 365 Compliance](https://go.microsoft.com/fwlink/?linkid=843165).</span></span>  <br/> |<span data-ttu-id="edd15-183">僅限於[FastTrack](https://go.microsoft.com/fwlink/?linkid=518597)協助進行移轉。</span><span class="sxs-lookup"><span data-stu-id="edd15-183">[FastTrack](https://go.microsoft.com/fwlink/?linkid=518597) assistance for migration is limited.</span></span>  <br/> <span data-ttu-id="edd15-184">大部分的升級會手動，或透過 SPO 移轉 API 所述的[SharePoint Online 和 OneDrive 移轉內容藍圖](https://go.microsoft.com/fwlink/?linkid=843184)。</span><span class="sxs-lookup"><span data-stu-id="edd15-184">Much of the upgrade will be manual, or via the SPO Migration API described in the [SharePoint Online and OneDrive Migration Content Roadmap](https://go.microsoft.com/fwlink/?linkid=843184).</span></span>  <br/> |
|<span data-ttu-id="edd15-185">Microsoft 技術支援工程師和資料中心內的員工都有不受限制系統管理員存取您的訂閱。</span><span class="sxs-lookup"><span data-stu-id="edd15-185">Neither Microsoft Support Engineers nor employees in the datacenter have unrestricted admin access to your subscription.</span></span>  <br/> |<span data-ttu-id="edd15-186">如果要升級以支援較新版本的 SharePoint，就必須硬體基礎結構或次要伺服器陣列是需要升級時，則可以是其他成本。</span><span class="sxs-lookup"><span data-stu-id="edd15-186">There can be additional costs if hardware infrastructure needs to be upgraded to support the newer version of SharePoint, or if a secondary farm is required for upgrade.</span></span>  <br/> |
|<span data-ttu-id="edd15-187">合作夥伴可協助進行一次性作業的資料移轉至 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="edd15-187">Partners can assist with the one-time job of migrating your data to SharePoint Online.</span></span>  <br/> ||
|<span data-ttu-id="edd15-188">線上產品會自動更新，這可能會取代功能，但是沒有支援沒有，則為 true 結束的服務。</span><span class="sxs-lookup"><span data-stu-id="edd15-188">Online products are updated automatically across the service meaning that though features may deprecate, there is no true end of support.</span></span>  <br/> ||
   
<span data-ttu-id="edd15-189">如果您已決定要建立新的 Office 365 網站，並會以手動方式將資料移轉至其所需，您可以查看您的 Office 365 選項權限：</span><span class="sxs-lookup"><span data-stu-id="edd15-189">If you've decided to create a new Office 365 site, and will manually migrate data to it as is needed, you can look at your Office 365 options right here:</span></span>
  
[<span data-ttu-id="edd15-190">Office 365 方案選項</span><span class="sxs-lookup"><span data-stu-id="edd15-190">Office 365 Plan Options</span></span>](https://go.microsoft.com/fwlink/?linkid=843151)
  
### <a name="upgrade-sharepoint-server-on-premises"></a><span data-ttu-id="edd15-191">升級 SharePoint Server 內部部署</span><span class="sxs-lookup"><span data-stu-id="edd15-191">Upgrade SharePoint Server on-premises</span></span>

<span data-ttu-id="edd15-192">沒有在過去略過至少起版本的 SharePoint Server 2016 中 SharePoint 升級，版本方法。</span><span class="sxs-lookup"><span data-stu-id="edd15-192">There is historically no way to skip versions in SharePoint Upgrades, at least not as of the release of SharePoint Server 2016.</span></span> <span data-ttu-id="edd15-193">這表示升級循序移：</span><span class="sxs-lookup"><span data-stu-id="edd15-193">That means upgrades go serially:</span></span>
  
|||
|:-----|:-----|
||<span data-ttu-id="edd15-194">SharePoint 2007</span><span class="sxs-lookup"><span data-stu-id="edd15-194">SharePoint 2007</span></span> | <span data-ttu-id="edd15-195">SharePoint Server 2010</span><span class="sxs-lookup"><span data-stu-id="edd15-195">SharePoint Server 2010</span></span> | <span data-ttu-id="edd15-196">SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="edd15-196">SharePoint Server 2013</span></span> | <span data-ttu-id="edd15-197">SharePoint Server 2016</span><span class="sxs-lookup"><span data-stu-id="edd15-197">SharePoint Server 2016</span></span> |
   
<span data-ttu-id="edd15-198">要從 SharePoint 2007 中取用的完整路徑 SharePoint Server 2016 會表示時間大量投資，並會牽涉成本方面 （請注意 SQL 伺服器也必須升級） 的升級硬體、 軟體和管理。</span><span class="sxs-lookup"><span data-stu-id="edd15-198">To take the entire path from SharePoint 2007 to SharePoint Server 2016 will mean a significant investment of time and will involve a cost in terms of upgraded hardware (be aware that SQL servers must also be upgraded), software, and administration.</span></span> <span data-ttu-id="edd15-199">自訂項目將會需要升級或因此而棄置，根據功能的重要性。</span><span class="sxs-lookup"><span data-stu-id="edd15-199">Customizations will need to be upgraded or abandoned, according to the criticality of the feature.</span></span>
  
> [!NOTE]
> <span data-ttu-id="edd15-200">很可能維護週期結束 SharePoint 2007 伺服器陣列、 在新硬體上 （因此不同的伺服器陣列執行並排顯示），安裝 SharePoint Server 2016 伺服器陣列，然後計劃和執行內容 （適用於下載與重新上傳內容，如手動移轉範例）。</span><span class="sxs-lookup"><span data-stu-id="edd15-200">It's possible to maintain your end-of-life SharePoint 2007 farm, install a SharePoint Server 2016 farm on new hardware (so the separate farms run side-by-side), and then plan and execute a manual migration of content (for downloading and re-uploading content, for example).</span></span> <span data-ttu-id="edd15-201">請注意一些問題 （例如移動的文件的上次修改的帳戶取代執行手動移動之帳戶的別名） 手動移動和必須事先 （例如重新建立網站、 子網站、 權限和清單完成的工時結構）。</span><span class="sxs-lookup"><span data-stu-id="edd15-201">Be aware of some of the gotchas of manual moves (such as moves of documents replacing the last modified account with the alias of the account doing the manual move), and the work that must be done ahead of time (such as recreating sites, sub-sites, permissions and list structures).</span></span> <span data-ttu-id="edd15-202">同樣地，這是要考慮您可以將移至存放區，或不再需要，可以減少移轉的影響動作何種資料的時間。</span><span class="sxs-lookup"><span data-stu-id="edd15-202">Again, this is the time to consider what data you can move into storage, or no longer need, an action that can reduce the impact of migration.</span></span>
  
<span data-ttu-id="edd15-203">無論如何，清除您要升級的環境之前。</span><span class="sxs-lookup"><span data-stu-id="edd15-203">Either way, clean your environment prior to upgrade.</span></span> <span data-ttu-id="edd15-204">是您現有的伺服器陣列正常運作，再升級，您和您解除委任 （確定） 之前 ！</span><span class="sxs-lookup"><span data-stu-id="edd15-204">Be certain your existing farm is functional before you upgrade, and (for sure) before you decommission!</span></span> 
  
<span data-ttu-id="edd15-205">檢閱**支援與不支援的升級路徑**，請記得：</span><span class="sxs-lookup"><span data-stu-id="edd15-205">Remember to review the **supported and unsupported upgrade paths**:</span></span> 
  
- <span data-ttu-id="edd15-206">
  [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843156)</span><span class="sxs-lookup"><span data-stu-id="edd15-206">[SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843156)</span></span>
    
- [<span data-ttu-id="edd15-207">SharePoint Server 2010</span><span class="sxs-lookup"><span data-stu-id="edd15-207">SharePoint Server 2010</span></span>](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [<span data-ttu-id="edd15-208">SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="edd15-208">SharePoint Server 2013</span></span>](https://go.microsoft.com/fwlink/?linkid=843157)
    
<span data-ttu-id="edd15-209">如果您有**自訂項目**，則務必您的移轉路徑中有計劃升級每個步驟：</span><span class="sxs-lookup"><span data-stu-id="edd15-209">If you have **customizations**, it's critical you have a plan your upgrade for each step in the migration path:</span></span> 
  
- [<span data-ttu-id="edd15-210">SharePoint 2007</span><span class="sxs-lookup"><span data-stu-id="edd15-210">SharePoint 2007</span></span>](https://go.microsoft.com/fwlink/?linkid=843158)
    
- [<span data-ttu-id="edd15-211">SharePoint Server 2010</span><span class="sxs-lookup"><span data-stu-id="edd15-211">SharePoint Server 2010</span></span>](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [<span data-ttu-id="edd15-212">SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="edd15-212">SharePoint Server 2013</span></span>](https://go.microsoft.com/fwlink/?linkid=843162)
    
|<span data-ttu-id="edd15-213">**內部 Pro**</span><span class="sxs-lookup"><span data-stu-id="edd15-213">**On-premises Pro**</span></span>|<span data-ttu-id="edd15-214">**在內部詐騙**</span><span class="sxs-lookup"><span data-stu-id="edd15-214">**On-premises Con**</span></span>|
|:-----|:-----|
|<span data-ttu-id="edd15-215">SharePoint 伺服器陣列，從備份的伺服器硬體的各個層面的完全控制權。</span><span class="sxs-lookup"><span data-stu-id="edd15-215">Full control of all aspects of your SharePoint Farm, from the server hardware up.</span></span>  <br/> |<span data-ttu-id="edd15-216">是 （可參與付費的 Microsoft 支援服務如果您的產品不支援的結尾處） 貴公司的責任的所有符號和修正程式：</span><span class="sxs-lookup"><span data-stu-id="edd15-216">All breaks and fixes are the responsibility of your company (can engage paid Microsoft Support if your product is not at end of support):</span></span>  <br/> |
|<span data-ttu-id="edd15-217">SharePoint Server 內部部署與您的內部部署伺服器陣列連線到 SharePoint Online 訂閱透過混合式選項的完整功能集。</span><span class="sxs-lookup"><span data-stu-id="edd15-217">Full feature set of SharePoint Server on-premises with the option to connect your on-premises farm to a SharePoint Online subscription via hybrid.</span></span>  <br/> |<span data-ttu-id="edd15-218">升級、 修補程式、 安全性修正程式和所有維護 SharePoint Server 受管理的內部。</span><span class="sxs-lookup"><span data-stu-id="edd15-218">Upgrade, patches, security fixes, and all maintenance of SharePoint Server managed on-premises.</span></span>  <br/> |
|<span data-ttu-id="edd15-219">更大的自訂的完整存取權。</span><span class="sxs-lookup"><span data-stu-id="edd15-219">Full access for greater customization.</span></span>  <br/> |<span data-ttu-id="edd15-220">[Office 365 所支援的合規性標準](https://go.microsoft.com/fwlink/?linkid=843165)必須以手動方式設定內部部署。</span><span class="sxs-lookup"><span data-stu-id="edd15-220">[Compliance standards supported by Office 365](https://go.microsoft.com/fwlink/?linkid=843165) must be manually configured on-premises.</span></span>  <br/> |
|<span data-ttu-id="edd15-221">測試安全性，與伺服器效能調整，實行您內部部署 （位於您的控制下）。</span><span class="sxs-lookup"><span data-stu-id="edd15-221">Security testing, and server performance tuning, carried out on your premises (is under your control).</span></span>  <br/> |<span data-ttu-id="edd15-222">Office 365 可能提供功能給 SharePoint Online 無法搭配 SharePoint Server 內部交互操作</span><span class="sxs-lookup"><span data-stu-id="edd15-222">Office 365 may make features available to SharePoint Online that do not interoperate with SharePoint Server on-premises</span></span>  <br/> |
|<span data-ttu-id="edd15-223">合作夥伴可協助進行移轉至下一個版本的 SharePoint Server （以及超過） 的資料。</span><span class="sxs-lookup"><span data-stu-id="edd15-223">Partners can assist with migrating data to the next version of SharePoint Server (and beyond).</span></span>  <br/> |<span data-ttu-id="edd15-224">SharePoint Server 網站不會自動使用[SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167)憑證視為是 SharePoint Online 中。</span><span class="sxs-lookup"><span data-stu-id="edd15-224">Your SharePoint Server sites will not automatically use [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) certificates as is seen in SharePoint Online.</span></span>  <br/> |
|<span data-ttu-id="edd15-225">完整的命名慣例、 備份及還原 SharePoint Server 內部部署中的其他復原選項的控制項。</span><span class="sxs-lookup"><span data-stu-id="edd15-225">Full control of naming conventions, backup and restore and other recovery options in SharePoint Server on-premises.</span></span>  <br/> |<span data-ttu-id="edd15-226">SharePoint Server 內部部署是機密產品週期。</span><span class="sxs-lookup"><span data-stu-id="edd15-226">SharePoint Server on-premises is sensitive to product lifecycles.</span></span>  <br/> |
   
### <a name="upgrade-resources"></a><span data-ttu-id="edd15-227">升級的資源</span><span class="sxs-lookup"><span data-stu-id="edd15-227">Upgrade Resources</span></span>

<span data-ttu-id="edd15-228">先知道您符合硬體和軟體需求，然後遵循支援升級方法。</span><span class="sxs-lookup"><span data-stu-id="edd15-228">Begin by knowing that you meet hardware and software requirements, then follow supported upgrade methods.</span></span>
  
- <span data-ttu-id="edd15-229">**軟硬體需求**：</span><span class="sxs-lookup"><span data-stu-id="edd15-229">**Hardware/software requirements for**:</span></span> 
    
    <span data-ttu-id="edd15-230">[SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)</span><span class="sxs-lookup"><span data-stu-id="edd15-230">[SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)</span></span>
    
- <span data-ttu-id="edd15-231">**軟體界限及限制**：</span><span class="sxs-lookup"><span data-stu-id="edd15-231">**Software boundaries and limits for**:</span></span> 
    
    <span data-ttu-id="edd15-232">[SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843245) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)</span><span class="sxs-lookup"><span data-stu-id="edd15-232">[SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843245) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)</span></span>
    
- <span data-ttu-id="edd15-233">**升級程序概觀**：</span><span class="sxs-lookup"><span data-stu-id="edd15-233">**The upgrade process overview for**:</span></span> 
    
    <span data-ttu-id="edd15-234">[SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843250) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)</span><span class="sxs-lookup"><span data-stu-id="edd15-234">[SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843250) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)</span></span>
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a><span data-ttu-id="edd15-235">建立 SharePoint Online 與內部部署之間的 SharePoint 混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="edd15-235">Create a SharePoint hybrid solution between SharePoint Online and on-premises</span></span>

<span data-ttu-id="edd15-236">如果您的移轉需求的答案某處之間提供內部部署，並提供 SharePoint online 的擁有權的低成本並非指自我控制，您可以連線 SharePoint Server 2013 或 2016年伺服器陣列至 SharePoint Online 中，透過混合。</span><span class="sxs-lookup"><span data-stu-id="edd15-236">If the answer to your migration needs is somewhere between the self-control offered by on-premises, and the lower cost of ownership offered by SharePoint Online, you can connect SharePoint Server 2013 or 2016 farms to SharePoint Online, through hybrids.</span></span> [<span data-ttu-id="edd15-237">了解 SharePoint 混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="edd15-237">Learn about SharePoint hybrid solutions</span></span>](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)
  
<span data-ttu-id="edd15-238">如果您決定混合式 SharePoint Server 伺服器陣列會對您的業務，熟悉現有的混合式以及如何設定您的內部部署 SharePoint 伺服器陣列與 Office 365 訂閱之間的連線類型。</span><span class="sxs-lookup"><span data-stu-id="edd15-238">If you decide that a hybrid SharePoint Server farm will benefit your business, familiarize yourself with the existing types of hybrid and how to configure the connection between your on-premises SharePoint farm and your Office 365 subscription.</span></span>
  
<span data-ttu-id="edd15-239">若要查看如何進行此作業的一個好方法是藉由建立[Office 365 開發/測試環境](https://go.microsoft.com/fwlink/?linkid=843152)。</span><span class="sxs-lookup"><span data-stu-id="edd15-239">One good way to see how this works is by creating an [Office 365 dev/test environment](https://go.microsoft.com/fwlink/?linkid=843152).</span></span> <span data-ttu-id="edd15-240">一旦您有試用或購買 Office 365 訂閱，您就可以在您要在 SharePoint Online 中的您可以將資料移轉建立的網站集合、 web、 及文件庫 ([以手動方式，藉由使用移轉 API，或-如果您想要移轉我網站內容，商務用 OneDrive-透過混合式精靈使用）。</span><span class="sxs-lookup"><span data-stu-id="edd15-240">Once you have a trial or purchased Office 365 subscription, you'll be on your way to creating the site collections, webs, and document libraries in SharePoint Online to which you can migrate data (either manually, by use of the Migration API, or - if you want to migrate My Site content to OneDrive for Business - through the hybrid wizard).</span></span>
  
> [!NOTE]
> <span data-ttu-id="edd15-241">請記住，您的 SharePoint 2007 伺服器陣列需要升級，在內部部署、 SharePoint Server 2013 或 SharePoint Server 2016 以使用混合式選項</span><span class="sxs-lookup"><span data-stu-id="edd15-241">Remember that your SharePoint 2007 farm will need to be upgraded, on-premises, to either SharePoint Server 2013 or SharePoint Server 2016 to use the hybrid option</span></span> 
  
## <a name="related-topics"></a><span data-ttu-id="edd15-242">相關主題</span><span class="sxs-lookup"><span data-stu-id="edd15-242">Related topics</span></span>

[<span data-ttu-id="edd15-243">疑難排解，並繼續升級 (Office SharePoint Server 2007)</span><span class="sxs-lookup"><span data-stu-id="edd15-243">Troubleshoot and resume upgrade (Office SharePoint Server 2007)</span></span>](https://go.microsoft.com/fwlink/?linkid=843192)
  
[<span data-ttu-id="edd15-244">疑難排解升級問題 (SharePoint Server 2010)</span><span class="sxs-lookup"><span data-stu-id="edd15-244">Troubleshoot upgrade issues (SharePoint Server 2010)</span></span>](https://go.microsoft.com/fwlink/?linkid=843194)
  
[<span data-ttu-id="edd15-245">在 SharePoint 2013 中針對資料庫的升級問題進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="edd15-245">Troubleshoot database upgrade issues in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/?linkid=843195)
  
[<span data-ttu-id="edd15-246">適用於 Microsoft 合作夥伴以協助進行升級的搜尋</span><span class="sxs-lookup"><span data-stu-id="edd15-246">Search for Microsoft Partners to help with Upgrade</span></span>](https://go.microsoft.com/fwlink/?linkid=841249)
  
[<span data-ttu-id="edd15-247">資源可以幫助您升級從 Office 2007 伺服器和用戶端</span><span class="sxs-lookup"><span data-stu-id="edd15-247">Resources to help you upgrade from Office 2007 servers and clients</span></span>](upgrade-from-office-2007-servers-and-products.md)
  

