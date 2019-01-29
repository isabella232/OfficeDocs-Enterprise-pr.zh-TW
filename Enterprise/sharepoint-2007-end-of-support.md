---
title: SharePoint Server 2007 終止支援藍圖
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 01/28/2019
ms.audience: ITPro
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
description: 在 2017 年 10 月 10、 支援的結束 for SharePoint Server 2007。閱讀本文以了解您的升級選項、 疑難排解、 最佳作法、 系統需求、 升級步驟及如何從 Microsoft 協力廠商取得協助。
ms.openlocfilehash: b0d3eda690733b45ee82054e145642a5c76125d5
ms.sourcegitcommit: 792fe2ccc860517fe3dcbc9c668bae97f39ae7c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2019
ms.locfileid: "29604514"
---
# <a name="sharepoint-server-2007-end-of-support-roadmap"></a><span data-ttu-id="2b7b7-104">SharePoint Server 2007 終止支援藍圖</span><span class="sxs-lookup"><span data-stu-id="2b7b7-104">SharePoint Server 2007 end of support roadmap</span></span>

<span data-ttu-id="2b7b7-p102">**2017 年 10 月 10，**，在 Microsoft Office SharePoint Server 2007 達到支援結束。如果您尚未開始從 SharePoint Server 2007 移轉至 Office 365 或較新版本的 SharePoint Server 的內部，現在是以開始規劃的時間。本文詳細說明可協助人員將資料移轉至 SharePoint Online、 或升級 SharePoint Server 內部的資源。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-p102">On **October 10, 2017**, Microsoft Office SharePoint Server 2007 reached end of support. If you haven't begun your migration from SharePoint Server 2007 to Office 365 or a newer version of SharePoint Server on-premises, now's the time to start planning. This article details resources to help people migrate data to SharePoint Online, or upgrade your SharePoint Server on-premises.</span></span> 
  
## <a name="what-does-end-of-support-mean"></a><span data-ttu-id="2b7b7-108">支援平均數何種實務結尾？</span><span class="sxs-lookup"><span data-stu-id="2b7b7-108">What does end of support mean?</span></span>

<span data-ttu-id="2b7b7-p103">SharePoint Server 幾乎所有的 Microsoft 產品，例如有支援週期的期間 Microsoft 提供的新功能、 修正錯誤、 安全性修正程式等等。此技術支援週期通常是一個工期 10 年度從產品的初始版本，日期的此技術支援週期的結尾就所謂的產品支援結束。支援的結尾，Microsoft 不再提供：</span><span class="sxs-lookup"><span data-stu-id="2b7b7-p103">SharePoint Server, like almost all Microsoft products, has a support lifecycle during which Microsoft provides new features, bug fixes, security fixes, and so on. This lifecycle typically lasts for 10 years from the date of the product's initial release, and the end of this lifecycle is known as the product's end of support. At end of support, Microsoft no longer provides:</span></span>
  
- <span data-ttu-id="2b7b7-112">技術支援問題，可能會發生;</span><span class="sxs-lookup"><span data-stu-id="2b7b7-112">Technical support for problems that may occur;</span></span>
    
- <span data-ttu-id="2b7b7-113">錯誤修正的問題會發現及，可能會影響穩定性及可用性的伺服器;</span><span class="sxs-lookup"><span data-stu-id="2b7b7-113">Bug fixes for issues that are discovered and that may impact the stability and usability of the server;</span></span>
    
- <span data-ttu-id="2b7b7-114">安全性弱點的探索和可能會提出伺服器安全性缺口; 容易受到的修正與</span><span class="sxs-lookup"><span data-stu-id="2b7b7-114">Security fixes for vulnerabilities that are discovered and that may make the server vulnerable to security breaches; and</span></span> 
    
- <span data-ttu-id="2b7b7-115">時間的時區更新。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-115">Time zone updates.</span></span>
    
<span data-ttu-id="2b7b7-p104">不過您的 SharePoint Server 2007 伺服器陣列仍能運作後年 10 月 10，2017，沒有進一步更新、 修補程式、 或修正項目將會傳送 （包括安全性修補程式修正程式） 的產品與 Microsoft 技術支援人員會完全移位及其支援致力於較新版的產品。因為您的安裝將不再支援或修補時，做為結尾的支援方法您應該升級、 產品或移轉重要資料。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-p104">Though your SharePoint Server 2007 farm will still be operational after October 10, 2017, no further updates, patches, or fixes will be shipped for the product (including security patches/fixes), and Microsoft Support will have fully shifted its support efforts to more recent versions of the product. Because your installation will no longer supported or patched, as end of support approaches you should upgrade the product, or migrate important data.</span></span>
  
> [!TIP]
> <span data-ttu-id="2b7b7-p105">如果您已經尚未升級或移轉計劃，請參閱： [SharePoint 2007 要考慮的移轉選項](sharepoint-2007-migration-options.md)，以開始的所在位置的一些範例。您也可以搜尋適用於[Microsoft 合作夥伴](https://go.microsoft.com/fwlink/?linkid=841249)可以協助升級或 Office 365 遷移 （或兩者）。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-p105">If you haven't already planned for upgrade or migration, please see: [SharePoint 2007 migration options to consider](sharepoint-2007-migration-options.md), for some examples of where to begin. You can also search for [Microsoft Partners](https://go.microsoft.com/fwlink/?linkid=841249) who can help with upgrade or Office 365 migration (or both).</span></span> 
  
<span data-ttu-id="2b7b7-120">如需即將達到支援結束的 Office 2007 伺服器的詳細資訊，請參閱[資源以協助您升級從 Office 2007 的伺服器和用戶端](upgrade-from-office-2007-servers-and-products.md)。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-120">For more information about Office 2007 servers reaching the end of support, see [Resources to help you upgrade from Office 2007 servers and clients](upgrade-from-office-2007-servers-and-products.md).</span></span>
  
## <a name="what-are-my-options"></a><span data-ttu-id="2b7b7-121">我的選項為何？</span><span class="sxs-lookup"><span data-stu-id="2b7b7-121">What are my options?</span></span>

<span data-ttu-id="2b7b7-p106">在第一個停駐點應[產品生命週期網站](https://go.microsoft.com/fwlink/?linkid=843148)。如果您有已過時的內部部署 Microsoft 產品，就應該檢查其結尾支援日期的因此，一年或賣出層或只要您移轉通常需要-您可以排程升級或移轉。當選擇 [下一步，它可協助認為就會是很好足夠、 搭配成效更佳、 以及最佳而言產品功能。以下是範例：</span><span class="sxs-lookup"><span data-stu-id="2b7b7-p106">Your first stop should be the [Product Lifecycle site](https://go.microsoft.com/fwlink/?linkid=843148). If you have an on-premises Microsoft product that is aging, you should check for its end of support date so that, a year or so out - or as long as your migrations generally require - you can schedule upgrade or migrations. When choosing the next step, it might help to think in terms of what would be good enough, better, and best when it comes to product features. Here's an example:</span></span>
  
|<span data-ttu-id="2b7b7-126">**良好**</span><span class="sxs-lookup"><span data-stu-id="2b7b7-126">**Good**</span></span>|<span data-ttu-id="2b7b7-127">**更好**</span><span class="sxs-lookup"><span data-stu-id="2b7b7-127">**Better**</span></span>|<span data-ttu-id="2b7b7-128">**最佳**</span><span class="sxs-lookup"><span data-stu-id="2b7b7-128">**Best**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="2b7b7-129">SharePoint Server 2010</span><span class="sxs-lookup"><span data-stu-id="2b7b7-129">SharePoint Server 2010</span></span>  <br/> |<span data-ttu-id="2b7b7-130">SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="2b7b7-130">SharePoint Server 2013</span></span>  <br/> |<span data-ttu-id="2b7b7-131">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="2b7b7-131">SharePoint Online</span></span>  <br/> |
||<span data-ttu-id="2b7b7-132">SharePoint 混合式</span><span class="sxs-lookup"><span data-stu-id="2b7b7-132">SharePoint Hybrid</span></span>  <br/> |<span data-ttu-id="2b7b7-133">SharePoint Server 2016</span><span class="sxs-lookup"><span data-stu-id="2b7b7-133">SharePoint Server 2016</span></span>  <br/> |
|||<span data-ttu-id="2b7b7-134">SharePoint 混合式</span><span class="sxs-lookup"><span data-stu-id="2b7b7-134">SharePoint Hybrid</span></span>  <br/> |
   
<span data-ttu-id="2b7b7-p107">如果您選擇低結尾 （良好足夠） 刻度的選項，請記得才能開始規劃升級非常推出從 SharePoint Server 2007 的移轉後已完成。（SharePoint Server 2007 結束是支援的 2017 年 10 月 10。請注意下列日期如有變更恕並檢查[產品生命週期網站](https://support.microsoft.com/en-us/lifecycle)）。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-p107">If you choose options on the low end of the scale (good enough), remember you will need to begin planning for upgrade very soon after migration from SharePoint Server 2007 is complete. (end of support for SharePoint Server 2007 is October 10, 2017. Please note that these dates are subject to change and check the [Product Lifecycle site](https://support.microsoft.com/en-us/lifecycle).)</span></span>
  
## <a name="where-can-i-go-next"></a><span data-ttu-id="2b7b7-138">我移出下一步？</span><span class="sxs-lookup"><span data-stu-id="2b7b7-138">Where can I go next?</span></span>

<span data-ttu-id="2b7b7-p108">SharePoint Server 可以是安裝於內部您自己的伺服器上也可以使用 SharePoint Online，這是一種線上服務是 Microsoft Office 365 的一部分。您可以選擇：</span><span class="sxs-lookup"><span data-stu-id="2b7b7-p108">SharePoint Server can be installed on-premises on your own servers, or you can use SharePoint Online, which is an online service that is part of Microsoft Office 365. You can choose to:</span></span>
  
- <span data-ttu-id="2b7b7-141">移轉至 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="2b7b7-141">Migrate to SharePoint Online</span></span>
    
- <span data-ttu-id="2b7b7-142">升級 SharePoint Server 的內部</span><span class="sxs-lookup"><span data-stu-id="2b7b7-142">Upgrade SharePoint Server on-premises</span></span>
    
- <span data-ttu-id="2b7b7-143">執行兩個以上</span><span class="sxs-lookup"><span data-stu-id="2b7b7-143">Do both of the above</span></span>
    
- <span data-ttu-id="2b7b7-144">實作[SharePoint 混合式](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)解決方案</span><span class="sxs-lookup"><span data-stu-id="2b7b7-144">Implement a [SharePoint hybrid](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) solution</span></span> 
    
<span data-ttu-id="2b7b7-p109">請注意的隱藏成本相關聯維護伺服器陣列移往前，維護或移轉自訂和升級 SharePoint Server 所依存的硬體。具有內部部署 SharePoint 伺服器陣列棒嗎如果它是必要性;否則，如果您沒有頻繁自訂舊版 SharePoint 伺服器上執行伺服器陣列您可以特地列出計劃移轉至 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-p109">Be aware of hidden costs associated with maintaining a server farm going forward, maintaining or migrating customizations, and upgrading the hardware upon which SharePoint Server depends. Having an on-premises SharePoint Server farm is rewarding if it is a necessity; otherwise, if you run your farm on legacy SharePoint Servers, without heavy customization, you can benefit from a planned migration to SharePoint Online.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="2b7b7-p110">如果不常使用 SharePoint 2007 中的內容，有另一個選項。某些 SharePoint 管理員可以選擇[建立 Office 365 訂閱](https://go.microsoft.com/fwlink/?linkid=843152)，設定全新的 SharePoint Online 網站，並執行全新、 cut 從 SharePoint 2007、 僅限最重要的文件帶全新的 SharePoint Online 網站。從該處、 資料可能會清空從 SharePoint 2007 網站將封存。授與使用者的運作方式與資料 SharePoint 2007 安裝的思考。可能會有小小寫的方式來解決這個問題 ！</span><span class="sxs-lookup"><span data-stu-id="2b7b7-p110">There is another option if the content in SharePoint 2007 is infrequently used. Some SharePoint Administrators may choose to [create an Office 365 Subscription](https://go.microsoft.com/fwlink/?linkid=843152), set up a brand new SharePoint Online site, and then cut away from SharePoint 2007, cleanly, taking only the most essential documents to the fresh SharePoint Online sites. From there, data may be drained from the SharePoint 2007 site into archives. Give thought to how users work with data your SharePoint 2007 installation. There may be creative ways to resolve this problem!</span></span> 
  
|<span data-ttu-id="2b7b7-152">**SharePoint Online (SPO)**</span><span class="sxs-lookup"><span data-stu-id="2b7b7-152">**SharePoint Online (SPO)**</span></span>|<span data-ttu-id="2b7b7-153">**SharePoint Server 的內部**</span><span class="sxs-lookup"><span data-stu-id="2b7b7-153">**SharePoint Server on-premises**</span></span>|
|:-----|:-----|
|<span data-ttu-id="2b7b7-154">高成本的時間 (計劃 / 執行 / 驗證)</span><span class="sxs-lookup"><span data-stu-id="2b7b7-154">High cost in time (plan / execution / verification)</span></span>  <br/> |<span data-ttu-id="2b7b7-155">高成本的時間 (計劃 / 執行 / 驗證)</span><span class="sxs-lookup"><span data-stu-id="2b7b7-155">High cost in time (plan / execution / verification)</span></span>  <br/> |
|<span data-ttu-id="2b7b7-156">資金 （沒有硬體購買） 中較低成本</span><span class="sxs-lookup"><span data-stu-id="2b7b7-156">Lower cost in funds (no hardware purchases)</span></span>  <br/> |<span data-ttu-id="2b7b7-157">在資金的較高成本 (硬體 + 適用於開發人員 / 系統管理員)</span><span class="sxs-lookup"><span data-stu-id="2b7b7-157">Higher cost in funds (hardware + devs / admins)</span></span>  <br/> |
|<span data-ttu-id="2b7b7-158">在移轉一次性成本</span><span class="sxs-lookup"><span data-stu-id="2b7b7-158">One-time cost in migration</span></span>  <br/> |<span data-ttu-id="2b7b7-159">一次性成本重複每未來移轉</span><span class="sxs-lookup"><span data-stu-id="2b7b7-159">One-time cost repeated per future migration</span></span>  <br/> |
|<span data-ttu-id="2b7b7-160">低的整體擁有成本 / 維護</span><span class="sxs-lookup"><span data-stu-id="2b7b7-160">Low total cost of ownership / maintenance</span></span>  <br/> |<span data-ttu-id="2b7b7-161">高的整體擁有成本 / 維護</span><span class="sxs-lookup"><span data-stu-id="2b7b7-161">High total cost of ownership / maintenance</span></span>  <br/> |
   
<span data-ttu-id="2b7b7-p111">當您移轉至 Office 365 時，單次移動時，將能夠先期、 加重成本您正在將組織內的資料並決定要採用至雲端的項目以及留下的項目。不過，升級將會自動從這時、 您不再需要管理硬體和軟體更新並將由 Microsoft 服務層級協議 ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)) 備份伺服器陣列最多時間。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-p111">When you migrate to Office 365, the one-time move will have a heavier cost up-front, while you're organizing data and deciding what to take to the cloud and what to leave behind. However, upgrades will be automatic from that point, you will no longer need to manage hardware and software updates, and the up-time of your farm will be backed by a Microsoft Service Level Agreement ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)).</span></span>
  
### <a name="migrate-to-sharepoint-online"></a><span data-ttu-id="2b7b7-164">移轉至 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="2b7b7-164">Migrate to SharePoint Online</span></span>

<span data-ttu-id="2b7b7-p112">請確定 SharePoint Online 有您需要透過檢閱相關聯的服務描述的所有功能。以下是所有的 Office 365 服務說明連結：</span><span class="sxs-lookup"><span data-stu-id="2b7b7-p112">Make sure that SharePoint Online has all the features you need by reviewing the associated service description. Here's the link to all Office 365 Service Descriptions:</span></span>
  
[<span data-ttu-id="2b7b7-167">Office 365 服務描述</span><span class="sxs-lookup"><span data-stu-id="2b7b7-167">Office 365 Service Descriptions</span></span>](https://go.microsoft.com/fwlink/?linkid=272060)
  
<span data-ttu-id="2b7b7-p113">沒有直接從 SharePoint 2007 移轉至 SharePoint Online; 方法在移至 SharePoint Online 會手動完成。如果您升級至 SharePoint Server 2013 或 SharePoint Server 2016、 您移動也可能會涉及使用 SharePoint 移轉 API （例如移轉至 OneDrive for Business，資訊）。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-p113">There is no direct way to migrate from SharePoint 2007 to SharePoint Online; your move to SharePoint Online would be done manually. If you upgrade to SharePoint Server 2013 or SharePoint Server 2016, your move might also involve using the SharePoint Migration API (to migrate information into OneDrive for Business, for example).</span></span>
  
|<span data-ttu-id="2b7b7-170">**線上專業人員**</span><span class="sxs-lookup"><span data-stu-id="2b7b7-170">**Online Pro**</span></span>|<span data-ttu-id="2b7b7-171">**線上詐騙**</span><span class="sxs-lookup"><span data-stu-id="2b7b7-171">**Online Con**</span></span>|
|:-----|:-----|
|<span data-ttu-id="2b7b7-172">Microsoft 提供給 SPO 硬體及所有硬體管理。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-172">Microsoft supplies SPO hardware and all hardware administration.</span></span>  <br/> |<span data-ttu-id="2b7b7-173">可用的功能可能會不同 SharePoint Server 的內部和 SPO 之間。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-173">Available features may be different between SharePoint Server on-premises and SPO.</span></span>  <br/> |
|<span data-ttu-id="2b7b7-174">您在訂閱的全域管理員，且可能會指派 SPO 網站的管理員。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-174">You are the global administrator of your subscription, and may assign administrators to SPO sites.</span></span>  <br/> |<span data-ttu-id="2b7b7-175">SharePoint Server 的內部不存在 （或不需要） 中的伺服器陣列管理員提供某些動作包含在 Office 365 中的 SharePoint 管理員角色。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-175">Some actions available to a Farm Administrator in SharePoint Server on-premises do not exist (or are not necessary) included in the SharePoint Administrator role in Office 365.</span></span>  <br/> |
|<span data-ttu-id="2b7b7-176">Microsoft 套用修補程式、 修正及更新為基礎的硬體和軟體。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-176">Microsoft applies patches, fixes and updates to underlying hardware and software.</span></span>  <br/> |<span data-ttu-id="2b7b7-177">因為沒有存取權之服務中的基礎檔案系統，所以部分自訂功能會受到限制。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-177">Because there is no access to the underlying file system in the service, some customizations are limited.</span></span>  <br/> |
|<span data-ttu-id="2b7b7-178">Microsoft 發佈[服務等級協定](https://go.microsoft.com/fwlink/?linkid=843153)書寫快速解決服務層級事件。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-178">Microsoft publishes [Service Level Agreements](https://go.microsoft.com/fwlink/?linkid=843153) and moves quickly to resolve service level incidents.</span></span>  <br/> |<span data-ttu-id="2b7b7-179">備份及還原及其他復原選項會自動在 SharePoint Online 服務-備份是以覆寫若不使用。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-179">Backup and restore and other recovery options are automated by the service in SharePoint Online - backups are overwritten if not used.</span></span>  <br/> |
|<span data-ttu-id="2b7b7-180">安全性測試及伺服器效能調整會持續在服務中來執行 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-180">Security testing and server performance tuning are carried out on an ongoing basis in the service by Microsoft.</span></span>  <br/> |<span data-ttu-id="2b7b7-181">使用者介面和其他 SharePoint 功能所安裝的服務和切換開啟或關閉可能需要變更。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-181">Changes to the user interface and other SharePoint features are installed by the service and may need to be toggled on or off.</span></span>  <br/> |
|<span data-ttu-id="2b7b7-182">Office 365 符合許多產業標準： [Office 365 規範](https://go.microsoft.com/fwlink/?linkid=843165)。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-182">Office 365 meets many industry standards: [Office 365 Compliance](https://go.microsoft.com/fwlink/?linkid=843165).</span></span>  <br/> |<span data-ttu-id="2b7b7-183">僅限於[FastTrack](https://go.microsoft.com/fwlink/?linkid=518597)協助進行移轉。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-183">[FastTrack](https://go.microsoft.com/fwlink/?linkid=518597) assistance for migration is limited.</span></span>  <br/> <span data-ttu-id="2b7b7-184">有多少升級將會是手動，或透過 SPO 移轉 API 所述的[SharePoint Online 和 OneDrive 移轉內容藍圖](https://go.microsoft.com/fwlink/?linkid=843184)。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-184">Much of the upgrade will be manual, or via the SPO Migration API described in the [SharePoint Online and OneDrive Migration Content Roadmap](https://go.microsoft.com/fwlink/?linkid=843184).</span></span>  <br/> |
|<span data-ttu-id="2b7b7-185">Microsoft 支援工程師和員工資料中心都有不受限制系統存取您的訂閱。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-185">Neither Microsoft Support Engineers nor employees in the datacenter have unrestricted admin access to your subscription.</span></span>  <br/> |<span data-ttu-id="2b7b7-186">如果需要升級以支援較新版的 SharePoint、 硬體基礎結構或次要伺服器陣列所需的升級，可以是其他的成本。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-186">There can be additional costs if hardware infrastructure needs to be upgraded to support the newer version of SharePoint, or if a secondary farm is required for upgrade.</span></span>  <br/> |
|<span data-ttu-id="2b7b7-187">協力廠商可協助進行資料移轉至 SharePoint Online 的單次工作。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-187">Partners can assist with the one-time job of migrating your data to SharePoint Online.</span></span>  <br/> ||
|<span data-ttu-id="2b7b7-188">線上產品會自動更新跨表示功能可能會取代，雖然有支援無則為 true 結束的服務。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-188">Online products are updated automatically across the service meaning that though features may deprecate, there is no true end of support.</span></span>  <br/> ||
   
<span data-ttu-id="2b7b7-189">如果您已決定建立新的 Office 365 網站，並會以手動方式將資料移轉至其會視，您可以查看您的 Office 365 選項權限：</span><span class="sxs-lookup"><span data-stu-id="2b7b7-189">If you've decided to create a new Office 365 site, and will manually migrate data to it as is needed, you can look at your Office 365 options right here:</span></span>
  
[<span data-ttu-id="2b7b7-190">Office 365 方案選項</span><span class="sxs-lookup"><span data-stu-id="2b7b7-190">Office 365 Plan Options</span></span>](https://go.microsoft.com/fwlink/?linkid=843151)
  
### <a name="upgrade-sharepoint-server-on-premises"></a><span data-ttu-id="2b7b7-191">升級 SharePoint Server 的內部</span><span class="sxs-lookup"><span data-stu-id="2b7b7-191">Upgrade SharePoint Server on-premises</span></span>

<span data-ttu-id="2b7b7-p114">沒有在過去略過中 SharePoint 升級的版本至少到版本的 SharePoint Server 2016 方法。這表示升級移依序：</span><span class="sxs-lookup"><span data-stu-id="2b7b7-p114">There is historically no way to skip versions in SharePoint Upgrades, at least not as of the release of SharePoint Server 2016. That means upgrades go serially:</span></span>
  
|||
|:-----|:-----|
||<span data-ttu-id="2b7b7-194">SharePoint 2007</span><span class="sxs-lookup"><span data-stu-id="2b7b7-194">SharePoint 2007</span></span> | <span data-ttu-id="2b7b7-195">SharePoint Server 2010</span><span class="sxs-lookup"><span data-stu-id="2b7b7-195">SharePoint Server 2010</span></span> | <span data-ttu-id="2b7b7-196">SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="2b7b7-196">SharePoint Server 2013</span></span> | <span data-ttu-id="2b7b7-197">SharePoint Server 2016</span><span class="sxs-lookup"><span data-stu-id="2b7b7-197">SharePoint Server 2016</span></span> |
   
<span data-ttu-id="2b7b7-p115">要從 SharePoint 2007 的整個路徑 SharePoint Server 2016 表示可大幅投資的時間和成本方面 （請注意也必須升級 SQL 伺服器） 的已升級硬體、 軟體和管理時需要。自訂項目將會需要升級或放棄，根據功能的重要性。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-p115">To take the entire path from SharePoint 2007 to SharePoint Server 2016 will mean a significant investment of time and will involve a cost in terms of upgraded hardware (be aware that SQL servers must also be upgraded), software, and administration. Customizations will need to be upgraded or abandoned, according to the criticality of the feature.</span></span>
  
> [!NOTE]
> <span data-ttu-id="2b7b7-p116">可以維護您的一般生命週期 SharePoint 2007 伺服器陣列、 新硬體 （讓不同的伺服器陣列執行並排顯示） 上安裝 SharePoint Server 2016 伺服器陣列，然後規劃及執行內容 （如下載並重新上傳內容、 手動移轉範例）。請注意部分 （例如移動文件的上次修改的帳戶取代執行手動移動之帳戶的別名） 手動移動和必須完成時間 （例如重新建立網站、 子網站、 權限及清單在內工時 」 的問題結構）。同樣地，這是移轉的考量您可以將移至存放區，或不再需要、 動作可能會降低影響哪些資料的時間。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-p116">It's possible to maintain your end-of-life SharePoint 2007 farm, install a SharePoint Server 2016 farm on new hardware (so the separate farms run side-by-side), and then plan and execute a manual migration of content (for downloading and re-uploading content, for example). Be aware of some of the gotchas of manual moves (such as moves of documents replacing the last modified account with the alias of the account doing the manual move), and the work that must be done ahead of time (such as recreating sites, sub-sites, permissions and list structures). Again, this is the time to consider what data you can move into storage, or no longer need, an action that can reduce the impact of migration.</span></span>
  
<span data-ttu-id="2b7b7-p117">無論如何，清除您環境前的升級。是您現有的伺服器陣列可正常運作升級之前和解除委任 （確定） 之前 ！</span><span class="sxs-lookup"><span data-stu-id="2b7b7-p117">Either way, clean your environment prior to upgrade. Be certain your existing farm is functional before you upgrade, and (for sure) before you decommission!</span></span> 
  
<span data-ttu-id="2b7b7-205">檢閱**支援及不支援的升級路徑**，請記得：</span><span class="sxs-lookup"><span data-stu-id="2b7b7-205">Remember to review the **supported and unsupported upgrade paths**:</span></span> 
  
- <span data-ttu-id="2b7b7-206">
  [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843156)</span><span class="sxs-lookup"><span data-stu-id="2b7b7-206">[SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843156)</span></span>
    
- [<span data-ttu-id="2b7b7-207">SharePoint Server 2010</span><span class="sxs-lookup"><span data-stu-id="2b7b7-207">SharePoint Server 2010</span></span>](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [<span data-ttu-id="2b7b7-208">SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="2b7b7-208">SharePoint Server 2013</span></span>](https://go.microsoft.com/fwlink/?linkid=843157)
    
<span data-ttu-id="2b7b7-209">如果您有**自訂項目**，則十分重要計劃升級每個步驟中有移轉路徑：</span><span class="sxs-lookup"><span data-stu-id="2b7b7-209">If you have **customizations**, it's critical you have a plan your upgrade for each step in the migration path:</span></span> 
  
- [<span data-ttu-id="2b7b7-210">SharePoint 2007</span><span class="sxs-lookup"><span data-stu-id="2b7b7-210">SharePoint 2007</span></span>](https://go.microsoft.com/fwlink/?linkid=843158)
    
- [<span data-ttu-id="2b7b7-211">SharePoint Server 2010</span><span class="sxs-lookup"><span data-stu-id="2b7b7-211">SharePoint Server 2010</span></span>](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [<span data-ttu-id="2b7b7-212">SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="2b7b7-212">SharePoint Server 2013</span></span>](https://go.microsoft.com/fwlink/?linkid=843162)
    
|<span data-ttu-id="2b7b7-213">**內部專業人員**</span><span class="sxs-lookup"><span data-stu-id="2b7b7-213">**On-premises Pro**</span></span>|<span data-ttu-id="2b7b7-214">**在內部詐騙**</span><span class="sxs-lookup"><span data-stu-id="2b7b7-214">**On-premises Con**</span></span>|
|:-----|:-----|
|<span data-ttu-id="2b7b7-215">SharePoint 伺服器陣列，從伺服器硬體設定的所有層面的完全控制。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-215">Full control of all aspects of your SharePoint Farm, from the server hardware up.</span></span>  <br/> |<span data-ttu-id="2b7b7-216">所有符號與修正項目都是 （可參與付費的 Microsoft 技術支援人員如果您的產品不支援的結尾處） 貴公司的責任：</span><span class="sxs-lookup"><span data-stu-id="2b7b7-216">All breaks and fixes are the responsibility of your company (can engage paid Microsoft Support if your product is not at end of support):</span></span>  <br/> |
|<span data-ttu-id="2b7b7-217">SharePoint Server 的內部使用 [連線至 SharePoint Online 混合式透過訂閱的內部部署伺服器陣列] 選項的完整的功能集。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-217">Full feature set of SharePoint Server on-premises with the option to connect your on-premises farm to a SharePoint Online subscription via hybrid.</span></span>  <br/> |<span data-ttu-id="2b7b7-218">升級、 修補程式、 安全性修正程式及所有維護 SharePoint Server 的受管理的內部。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-218">Upgrade, patches, security fixes, and all maintenance of SharePoint Server managed on-premises.</span></span>  <br/> |
|<span data-ttu-id="2b7b7-219">針對更大的自訂的完整存取。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-219">Full access for greater customization.</span></span>  <br/> |<span data-ttu-id="2b7b7-220">[規範標準支援的 Office 365](https://go.microsoft.com/fwlink/?linkid=843165)必須手動設定內部部署。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-220">[Compliance standards supported by Office 365](https://go.microsoft.com/fwlink/?linkid=843165) must be manually configured on-premises.</span></span>  <br/> |
|<span data-ttu-id="2b7b7-221">安全性測試及伺服器效能調整實現在您內部部署 （是由您控制）。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-221">Security testing, and server performance tuning, carried out on your premises (is under your control).</span></span>  <br/> |<span data-ttu-id="2b7b7-222">Office 365 可能會讓功能可供 SharePoint Online 的不能與 SharePoint Server 的內部互通</span><span class="sxs-lookup"><span data-stu-id="2b7b7-222">Office 365 may make features available to SharePoint Online that do not interoperate with SharePoint Server on-premises</span></span>  <br/> |
|<span data-ttu-id="2b7b7-223">協力廠商可協助進行移轉的 SharePoint Server （和超過） 的下一版的資料。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-223">Partners can assist with migrating data to the next version of SharePoint Server (and beyond).</span></span>  <br/> |<span data-ttu-id="2b7b7-224">SharePoint Server 網站不會自動使用[SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167)憑證視為是 SharePoint Online 中。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-224">Your SharePoint Server sites will not automatically use [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) certificates as is seen in SharePoint Online.</span></span>  <br/> |
|<span data-ttu-id="2b7b7-225">命名慣例、 備份及還原 SharePoint Server 的內部其他復原選項的完全控制。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-225">Full control of naming conventions, backup and restore and other recovery options in SharePoint Server on-premises.</span></span>  <br/> |<span data-ttu-id="2b7b7-226">SharePoint Server 的內部會受到產品生命週期。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-226">SharePoint Server on-premises is sensitive to product lifecycles.</span></span>  <br/> |
   
### <a name="upgrade-resources"></a><span data-ttu-id="2b7b7-227">升級的資源</span><span class="sxs-lookup"><span data-stu-id="2b7b7-227">Upgrade Resources</span></span>

<span data-ttu-id="2b7b7-228">先了解您是否符合硬體和軟體需求，然後遵循支援的升級方法。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-228">Begin by knowing that you meet hardware and software requirements, then follow supported upgrade methods.</span></span>
  
- <span data-ttu-id="2b7b7-229">**硬體/軟體需求**：</span><span class="sxs-lookup"><span data-stu-id="2b7b7-229">**Hardware/software requirements for**:</span></span> 
    
    <span data-ttu-id="2b7b7-230">[SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)</span><span class="sxs-lookup"><span data-stu-id="2b7b7-230">[SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)</span></span>
    
- <span data-ttu-id="2b7b7-231">**軟體界限和限制**：</span><span class="sxs-lookup"><span data-stu-id="2b7b7-231">**Software boundaries and limits for**:</span></span> 
    
    <span data-ttu-id="2b7b7-232">[SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843245) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)</span><span class="sxs-lookup"><span data-stu-id="2b7b7-232">[SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843245) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)</span></span>
    
- <span data-ttu-id="2b7b7-233">**的升級程序概觀**：</span><span class="sxs-lookup"><span data-stu-id="2b7b7-233">**The upgrade process overview for**:</span></span> 
    
    <span data-ttu-id="2b7b7-234">[SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843250) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)</span><span class="sxs-lookup"><span data-stu-id="2b7b7-234">[SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843250) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)</span></span>
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a><span data-ttu-id="2b7b7-235">建立 SharePoint Online 和內部部署之間的 SharePoint 混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="2b7b7-235">Create a SharePoint hybrid solution between SharePoint Online and on-premises</span></span>

<span data-ttu-id="2b7b7-p118">如果移轉需求的答案某處之間提供內部部署，並提供 SharePoint Online 的擁有權的較低成本並非指自我控制，您可以連線 SharePoint Server 2013 或 2016年伺服器陣列至 SharePoint Online、 混合透過。[了解 SharePoint 混合式解決方案](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)</span><span class="sxs-lookup"><span data-stu-id="2b7b7-p118">If the answer to your migration needs is somewhere between the self-control offered by on-premises, and the lower cost of ownership offered by SharePoint Online, you can connect SharePoint Server 2013 or 2016 farms to SharePoint Online, through hybrids. [Learn about SharePoint hybrid solutions](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)</span></span>
  
<span data-ttu-id="2b7b7-238">如果您決定將混合式 SharePoint 伺服器陣列的業務好處，熟悉現有的混合式以及如何設定內部部署 SharePoint 伺服器陣列與您的 Office 365 訂閱之間的連線類型。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-238">If you decide that a hybrid SharePoint Server farm will benefit your business, familiarize yourself with the existing types of hybrid and how to configure the connection between your on-premises SharePoint farm and your Office 365 subscription.</span></span>
  
<span data-ttu-id="2b7b7-p119">請參閱這的運作方式的其中一個好方法是建立[Office 365 開發人員/測試環境](https://go.microsoft.com/fwlink/?linkid=843152)。一旦您有試用版或購買 Office 365 訂閱，您必須在您的方式來建立網站集合、 web、 與文件庫的 SharePoint Online 可移轉資料 (其中一個手動，藉由使用移轉 API 或-如果您想要移轉我網站內容至 OneDrive for Business-透過混合精靈]）。</span><span class="sxs-lookup"><span data-stu-id="2b7b7-p119">One good way to see how this works is by creating an [Office 365 dev/test environment](https://go.microsoft.com/fwlink/?linkid=843152). Once you have a trial or purchased Office 365 subscription, you'll be on your way to creating the site collections, webs, and document libraries in SharePoint Online to which you can migrate data (either manually, by use of the Migration API, or - if you want to migrate My Site content to OneDrive for Business - through the hybrid wizard).</span></span>
  
> [!NOTE]
> <span data-ttu-id="2b7b7-241">請記得在 SharePoint 2007 伺服器陣列需要升級，內部部署、 SharePoint Server 2013 或 SharePoint Server 2016 來使用混合選項</span><span class="sxs-lookup"><span data-stu-id="2b7b7-241">Remember that your SharePoint 2007 farm will need to be upgraded, on-premises, to either SharePoint Server 2013 or SharePoint Server 2016 to use the hybrid option</span></span> 
  
## <a name="related-topics"></a><span data-ttu-id="2b7b7-242">相關主題</span><span class="sxs-lookup"><span data-stu-id="2b7b7-242">Related topics</span></span>

[<span data-ttu-id="2b7b7-243">疑難排解與繼續升級 (Office SharePoint Server 2007)</span><span class="sxs-lookup"><span data-stu-id="2b7b7-243">Troubleshoot and resume upgrade (Office SharePoint Server 2007)</span></span>](https://go.microsoft.com/fwlink/?linkid=843192)
  
[<span data-ttu-id="2b7b7-244">疑難排解升級問題 (SharePoint Server 2010)</span><span class="sxs-lookup"><span data-stu-id="2b7b7-244">Troubleshoot upgrade issues (SharePoint Server 2010)</span></span>](https://go.microsoft.com/fwlink/?linkid=843194)
  
[<span data-ttu-id="2b7b7-245">在 SharePoint 2013 中針對資料庫的升級問題進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="2b7b7-245">Troubleshoot database upgrade issues in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/?linkid=843195)
  
[<span data-ttu-id="2b7b7-246">搜尋功能可協助升級 Microsoft 合作夥伴</span><span class="sxs-lookup"><span data-stu-id="2b7b7-246">Search for Microsoft Partners to help with Upgrade</span></span>](https://go.microsoft.com/fwlink/?linkid=841249)
  
[<span data-ttu-id="2b7b7-247">可協助您升級從 Office 2007 的伺服器和用戶端的資源</span><span class="sxs-lookup"><span data-stu-id="2b7b7-247">Resources to help you upgrade from Office 2007 servers and clients</span></span>](upgrade-from-office-2007-servers-and-products.md)
  

