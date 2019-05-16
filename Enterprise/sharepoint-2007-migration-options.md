---
title: 若要考慮 SharePoint 2007 遷移選項
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 1/31/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- SPS150
- OSU140
- SPO160
- SPB160
- OSI150
- OSI160
- BSA160
- OSU160
ms.assetid: 66325a43-5816-4f8e-81ba-c11b71345b7c
description: SharePoint Server 2007 已達到終止支援，及該是時候來升級。 使用這篇文章可協助您建立您的計劃。
ms.openlocfilehash: 98151ecd32f0066f583da1142d6010d46e120a43
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070699"
---
# <a name="sharepoint-2007-migration-options-to-consider"></a><span data-ttu-id="8b04b-104">若要考慮 SharePoint 2007 遷移選項</span><span class="sxs-lookup"><span data-stu-id="8b04b-104">SharePoint 2007 migration options to consider</span></span>

<span data-ttu-id="8b04b-105">Microsoft SharePoint 2007 與 SharePoint Server 2007 已達到終止支援。</span><span class="sxs-lookup"><span data-stu-id="8b04b-105">Microsoft SharePoint 2007 and SharePoint Server 2007 have reached end of support.</span></span> <span data-ttu-id="8b04b-106">該是時候來升級 ！</span><span class="sxs-lookup"><span data-stu-id="8b04b-106">It's time to upgrade!</span></span> <span data-ttu-id="8b04b-107">本文提供您的遷移選項的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8b04b-107">This article provides information about your migration options.</span></span>
  
## <a name="common-upgrade-strategies-for-sharepoint"></a><span data-ttu-id="8b04b-108">SharePoint 的一般升級策略</span><span class="sxs-lookup"><span data-stu-id="8b04b-108">Common upgrade strategies for SharePoint</span></span>

<span data-ttu-id="8b04b-109">有多種方法來升級 SharePoint Server 環境。</span><span class="sxs-lookup"><span data-stu-id="8b04b-109">There are multiple methods to upgrade a SharePoint Server environment.</span></span> <span data-ttu-id="8b04b-110">如果您有 Microsoft Office SharePoint Server 2007 伺服器陣列時，以下是升級方法的一些範例：</span><span class="sxs-lookup"><span data-stu-id="8b04b-110">If you have a Microsoft Office SharePoint Server 2007 farm, here are some examples of the upgrade methods:</span></span>
  
- <span data-ttu-id="8b04b-111">資料庫附加</span><span class="sxs-lookup"><span data-stu-id="8b04b-111">Database attach</span></span>
    
- <span data-ttu-id="8b04b-112">並排顯示升級</span><span class="sxs-lookup"><span data-stu-id="8b04b-112">Side-by-side upgrade</span></span>
    
- <span data-ttu-id="8b04b-113">就地升級 </span><span class="sxs-lookup"><span data-stu-id="8b04b-113">In-place upgrade</span></span>
    
- <span data-ttu-id="8b04b-114">混合式升級 (就地升級以卸離資料庫 / 不同資料庫附加)</span><span class="sxs-lookup"><span data-stu-id="8b04b-114">Hybrid upgrade (in-place with detached databases / separate database attach)</span></span>
    
- <span data-ttu-id="8b04b-115">SharePoint 混合 （連線至內部部署 SharePoint）</span><span class="sxs-lookup"><span data-stu-id="8b04b-115">SharePoint hybrids (connect online to on-premises SharePoint)</span></span>
    
- <span data-ttu-id="8b04b-116">以手動方式將資料移之間的網站集合或文件庫</span><span class="sxs-lookup"><span data-stu-id="8b04b-116">Manually move data between site collections or libraries</span></span>
    
- <span data-ttu-id="8b04b-117">FastTrack 精靈升級到 Office 365 ([SharePoint Online 部署建議程式](https://aka.ms/spoguidance))</span><span class="sxs-lookup"><span data-stu-id="8b04b-117">FastTrack Wizard upgrade to Office 365 ([SharePoint Online deployment advisor](https://aka.ms/spoguidance))</span></span>
    
- <span data-ttu-id="8b04b-118">移轉至 SharePoint Online (SPO) 中 Office 365 API</span><span class="sxs-lookup"><span data-stu-id="8b04b-118">Migration API to SharePoint Online (SPO) in Office 365</span></span>
    
<span data-ttu-id="8b04b-119">項目最適合您？</span><span class="sxs-lookup"><span data-stu-id="8b04b-119">What works best for you?</span></span>
  
<span data-ttu-id="8b04b-120">您的伺服器陣列的項目並未以及用於知識時提到升級策略強度。</span><span class="sxs-lookup"><span data-stu-id="8b04b-120">Your knowledge of what your farm does and is used for is a tactical strength when it comes to upgrade.</span></span> <span data-ttu-id="8b04b-121">人員使用的 SharePoint 伺服器陣列的方式可協助您選擇的選項。</span><span class="sxs-lookup"><span data-stu-id="8b04b-121">The way people use the SharePoint Farm will help you choose from your options.</span></span>
  
> [!TIP]
> <span data-ttu-id="8b04b-122">Microsoft Office SharePoint Server 2007 也有未深入涵蓋以下逐步升級。</span><span class="sxs-lookup"><span data-stu-id="8b04b-122">Microsoft Office SharePoint Server 2007 also has a gradual upgrade not covered here.</span></span> <span data-ttu-id="8b04b-123">若要查看特定步驟的升級的文章會看到[SharePoint Server 2007 終止支援藍圖](sharepoint-2007-end-of-support.md)。</span><span class="sxs-lookup"><span data-stu-id="8b04b-123">To see a list of step-specific upgrade articles see the [SharePoint Server 2007 end of support Roadmap](sharepoint-2007-end-of-support.md).</span></span> 
  
<span data-ttu-id="8b04b-124">請記得檢查任何版本的升級至 SharePoint[產品生命週期](https://support.microsoft.com/en-us/lifecycle/search)與系統需求。</span><span class="sxs-lookup"><span data-stu-id="8b04b-124">Remember to check the [Product Lifecycle](https://support.microsoft.com/en-us/lifecycle/search) and System Requirements for whatever version of SharePoint you're upgrading to.</span></span> <span data-ttu-id="8b04b-125">這是讓您將會注意時 （例如，如果您在 SharePoint Server 2010 規劃多個升級，請確定您知道其支援日期結尾，如舊版產品暫停），則必須進行下一次升級，以確保您有支援您的計劃的硬體。</span><span class="sxs-lookup"><span data-stu-id="8b04b-125">This is so you'll be aware when the next upgrade will be necessary (for example, if you pause at a legacy product like SharePoint Server 2010 to plan for more upgrades, be sure you know its end of support date), and to be certain you have hardware that supports your plan.</span></span> 
  
<span data-ttu-id="8b04b-126">如果您計劃轉換部分，或全部，您的 SharePoint 網站至 Office 365，在雲端中，這是書籤連結至[Office 365 服務說明](https://technet.microsoft.com/en-us/library/office-365-service-descriptions.aspx)的時間。</span><span class="sxs-lookup"><span data-stu-id="8b04b-126">If you're planning to transition some, or all, of your SharePoint sites to Office 365 in the Cloud, this is a time to bookmark a link to the [Service Descriptions for Office 365](https://technet.microsoft.com/en-us/library/office-365-service-descriptions.aspx).</span></span> <span data-ttu-id="8b04b-127">您需要的服務描述以深入了解 SharePoint Online 的功能以及它們可能之間的差異從內部部署 SharePoint Server。</span><span class="sxs-lookup"><span data-stu-id="8b04b-127">You'll need the Service Descriptions to learn about SharePoint Online features and how they might differ from on-premises SharePoint Server.</span></span> <span data-ttu-id="8b04b-128">升級功能的 Microsoft Office SharePoint Server 2007 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="8b04b-128">Upgrade functional Microsoft Office SharePoint Server 2007 farms.</span></span> <span data-ttu-id="8b04b-129">如果您安裝已損毀的網站，修正它們，在升級之前。</span><span class="sxs-lookup"><span data-stu-id="8b04b-129">If your installation has sites that are broken, fix them prior to upgrade.</span></span>
  
## <a name="a-note-about-managing-risk"></a><span data-ttu-id="8b04b-130">附註的相關風險管理</span><span class="sxs-lookup"><span data-stu-id="8b04b-130">A note about managing risk</span></span>

<span data-ttu-id="8b04b-131">'-並存' 類似的方法很重要的升級的邏輯配置中。</span><span class="sxs-lookup"><span data-stu-id="8b04b-131">Methods like 'side-by-side' are important in the scheme of upgrade logic.</span></span> <span data-ttu-id="8b04b-132">當您升級並排顯示時，您維護您的 Microsoft Office SharePoint Server 2007 伺服器陣列，但建置在伺服器陣列的下一個版本 (SharePoint Server 2010) 從新硬體上。</span><span class="sxs-lookup"><span data-stu-id="8b04b-132">When you upgrade side-by-side, you maintain your Microsoft Office SharePoint Server 2007 farm, but build a farm the next version up from it (SharePoint Server 2010) on new hardware.</span></span> <span data-ttu-id="8b04b-133">這三種方式可以幫助：</span><span class="sxs-lookup"><span data-stu-id="8b04b-133">This helps in three ways:</span></span>
  
1. <span data-ttu-id="8b04b-134">您必須進行 Microsoft Office SharePoint Server 2007 資料庫的備份分開升級，請使用資料庫附加的位置。</span><span class="sxs-lookup"><span data-stu-id="8b04b-134">You have a place to take backups of your Microsoft Office SharePoint Server 2007 databases to upgrade them separately, by using database attach.</span></span>
    
2. <span data-ttu-id="8b04b-135">如果您找出只有少數重要的文件庫及其他資訊會在您的 Microsoft Office SharePoint Server 2007 伺服器陣列上使用，您可以選擇以手動方式將資料從 Microsoft Office SharePoint Server 2007 移至 SharePoint Server 2010否則只有特定的網站與 web 的下一個版本 （這可以讓您的工作更容易）。</span><span class="sxs-lookup"><span data-stu-id="8b04b-135">If you figure out that only a small number of critical document libraries and other information are in use on your Microsoft Office SharePoint Server 2007 farm, you can choose to manually move data from Microsoft Office SharePoint Server 2007 to SharePoint Server 2010, or take only specific sites and webs to the next version (which can make your job easier).</span></span>
    
3. <span data-ttu-id="8b04b-136">較少您執行 Microsoft Office SharePoint Server 2007 伺服器陣列，直接，更安全的伺服器陣列的資料包含作為您升級。</span><span class="sxs-lookup"><span data-stu-id="8b04b-136">The less you do to the Microsoft Office SharePoint Server 2007 server farm, directly, the safer the data that farm contains as you upgrade.</span></span>
    
<span data-ttu-id="8b04b-137">方法，例如就地升級將擔任直接在 Microsoft Office SharePoint Server 2007 伺服器陣列，提供您放棄路徑，並再次開頭提出環境較少簡單選項。</span><span class="sxs-lookup"><span data-stu-id="8b04b-137">Methods like In-Place upgrade will act directly on your Microsoft Office SharePoint Server 2007 farm, giving you fewer easy options to abandon a path and begin again with your pristine environment.</span></span> <span data-ttu-id="8b04b-138">盡可能，建立一些安全措施，（例如，以及測試原始環境的備份）。</span><span class="sxs-lookup"><span data-stu-id="8b04b-138">As much as possible, build in some safety measures (like taking and testing backups of the original environment).</span></span> <span data-ttu-id="8b04b-139">例如，如果您的 Microsoft Office SharePoint Server 2007 伺服器陣列虛擬，且基於備份與還原為重複項目，然後備份和還原您的服務窗口升級前的最新資料庫。</span><span class="sxs-lookup"><span data-stu-id="8b04b-139">For example, if your Microsoft Office SharePoint Server 2007 farm is virtual, and is duplicated for the purposes of backup and restore, then back-up and restore the most current databases prior to your service window for the upgrade.</span></span> <span data-ttu-id="8b04b-140">了解您可以還原資料庫備份不會選擇只提供保全，它可讓您的想法和平。</span><span class="sxs-lookup"><span data-stu-id="8b04b-140">Knowing that you have the option to restore database backups will not only give you a failsafe, it can give you peace of mind.</span></span>
  
> [!TIP]
> <span data-ttu-id="8b04b-141">升級的最佳做法文件存在[Microsoft Office SharePoint Server 2007](https://technet.microsoft.com/en-us/library/cc261992%28v=office.12%29.aspx)、 [SharePoint Server 2010](https://technet.microsoft.com/en-us/library/cc261992%28v=office.14%29.aspx)、 [SharePoint Server 2013](https://technet.microsoft.com/en-us/library/cc261992%28v=office.15%29.aspx)和[SharePoint Server 2016](https://technet.microsoft.com/en-us/library/cc261992%28v=office.16%29.aspx)。</span><span class="sxs-lookup"><span data-stu-id="8b04b-141">Best practices documents for upgrade exist for [Microsoft Office SharePoint Server 2007](https://technet.microsoft.com/en-us/library/cc261992%28v=office.12%29.aspx), [SharePoint Server 2010](https://technet.microsoft.com/en-us/library/cc261992%28v=office.14%29.aspx), [SharePoint Server 2013](https://technet.microsoft.com/en-us/library/cc261992%28v=office.15%29.aspx), and [SharePoint Server 2016](https://technet.microsoft.com/en-us/library/cc261992%28v=office.16%29.aspx).</span></span> <span data-ttu-id="8b04b-142">您也可以搜尋適用於[Microsoft 合作夥伴](https://partnercenter.microsoft.com/en-us/pcv/search)擁有升級或 Office 365 移轉的經驗。</span><span class="sxs-lookup"><span data-stu-id="8b04b-142">You can also search for [Microsoft Partners](https://partnercenter.microsoft.com/en-us/pcv/search) who have experience with upgrades or Office 365 migrations.</span></span> 
  
## <a name="make-your-plan"></a><span data-ttu-id="8b04b-143">讓您的計劃</span><span class="sxs-lookup"><span data-stu-id="8b04b-143">Make your plan</span></span>

<span data-ttu-id="8b04b-144">如果您需要升級，則必須計劃，以及一個大小不符合所有在這些情況下。</span><span class="sxs-lookup"><span data-stu-id="8b04b-144">If you need to upgrade, you need a plan, and one-size doesn't fit all in these cases.</span></span> <span data-ttu-id="8b04b-145">您的計劃可能 '與 SharePoint Online 中建立 Office 365 訂閱、 註冊的網域，並重新導向人員來儲存其檔案有' 一樣簡單。</span><span class="sxs-lookup"><span data-stu-id="8b04b-145">Your plan may be as simple as 'Create an Office 365 subscription with SharePoint Online, register a domain, and redirect people to save their files there'.</span></span> <span data-ttu-id="8b04b-146">它可能不是。</span><span class="sxs-lookup"><span data-stu-id="8b04b-146">And it may not be.</span></span> <span data-ttu-id="8b04b-147">決定是你，而且下您和您的使用者確實需要的項目。</span><span class="sxs-lookup"><span data-stu-id="8b04b-147">That decision is yours, and it's down to what you and your users really need.</span></span>
  
> [!NOTE]
> <span data-ttu-id="8b04b-148">它是風險軟體其生命週期結束上執行。</span><span class="sxs-lookup"><span data-stu-id="8b04b-148">It's risky to run on software whose lifecycle has ended.</span></span> <span data-ttu-id="8b04b-149">發現問題時，不再被修補超出支援的產品。</span><span class="sxs-lookup"><span data-stu-id="8b04b-149">Products that are out of support are no longer patched when issues are found.</span></span> <span data-ttu-id="8b04b-150">這也表示，如果出現新的安全性威脅，會有任何安全性修補程式或修正因為不再支援的生命週期的結束產品。</span><span class="sxs-lookup"><span data-stu-id="8b04b-150">This also means that if new security threats arise, there will be no security patches or fixes because the end-of-lifecycle products are no longer supported.</span></span> <span data-ttu-id="8b04b-151">請避免這種情況 ！</span><span class="sxs-lookup"><span data-stu-id="8b04b-151">Please avoid that situation!</span></span> 
  
### <a name="first-know-your-farm"></a><span data-ttu-id="8b04b-152">首先，了解您的伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="8b04b-152">First, know your farm</span></span>

<span data-ttu-id="8b04b-153">升級時，您做決定應該根據您的伺服器陣列並為您的組織。</span><span class="sxs-lookup"><span data-stu-id="8b04b-153">When upgrading, your decision-making should be based on what your farm does for your organization.</span></span> <span data-ttu-id="8b04b-154">它並未滿足哪些需求？</span><span class="sxs-lookup"><span data-stu-id="8b04b-154">What need does it satisfy?</span></span> <span data-ttu-id="8b04b-155">其角色是什麼？</span><span class="sxs-lookup"><span data-stu-id="8b04b-155">What's its role?</span></span> <span data-ttu-id="8b04b-156">在您的公司中每個伺服器陣列可能會有不同的角色。</span><span class="sxs-lookup"><span data-stu-id="8b04b-156">Each farm in your company may have a different role.</span></span> <span data-ttu-id="8b04b-157">您的 SharePoint 伺服器陣列的一些可能*重要*，有些可能是檔案封存-以便安全保存該處。</span><span class="sxs-lookup"><span data-stu-id="8b04b-157">Some of your SharePoint farms may be  *critical*  , some may be file archives -- there for safe-keeping.</span></span> <span data-ttu-id="8b04b-158">或者，如果您的伺服器陣列會一次填滿多個角色，然後您可能需要知道哪些網站集合、 網站或甚至是文件庫，任何自訂項目，以及它們是重要程度。</span><span class="sxs-lookup"><span data-stu-id="8b04b-158">Or, if your farm fills many roles at once, then you may need to know what site collections, webs, or even document libraries do, any customizations, and how important they are.</span></span> <span data-ttu-id="8b04b-159">分析您的資料，在此層級看起來好像許多工作，但它會儲存時間和精力精通您的網域，再升級，或遷移時，它。</span><span class="sxs-lookup"><span data-stu-id="8b04b-159">Analyzing your data at this level may seem like a lot of work, but it saves time and effort to master your domain before you upgrade, or migrate, it.</span></span> <span data-ttu-id="8b04b-160">一旦您知道所有移動的組件，並將最重要的位元，也會知道的項目已 outgrown 以及可能會留下。</span><span class="sxs-lookup"><span data-stu-id="8b04b-160">Once you know all the moving parts, and the most important bits, you'll also know what you've outgrown and can leave behind.</span></span> <span data-ttu-id="8b04b-161">該知識只會受益您接下來。</span><span class="sxs-lookup"><span data-stu-id="8b04b-161">That knowledge will only benefit you going forward.</span></span> 
  
<span data-ttu-id="8b04b-162">因此，哪些使用者說最重要的 SharePoint Server 伺服器陣列的相關？</span><span class="sxs-lookup"><span data-stu-id="8b04b-162">So, what are users saying is most important about your SharePoint Server farm?</span></span>
  
- <span data-ttu-id="8b04b-163">內建的 SharePoint 功能</span><span class="sxs-lookup"><span data-stu-id="8b04b-163">Built-in SharePoint features</span></span>
    
- <span data-ttu-id="8b04b-164">大型資料主體 （例如封存的檔案）</span><span class="sxs-lookup"><span data-stu-id="8b04b-164">The large data corpus (such as an archive of files)</span></span>
    
- <span data-ttu-id="8b04b-165">可用性</span><span class="sxs-lookup"><span data-stu-id="8b04b-165">Availability</span></span>
    
- <span data-ttu-id="8b04b-166">重要的應用程式、 網頁組件或伺服器陣列 （任務重要伺服器陣列） 中的文件</span><span class="sxs-lookup"><span data-stu-id="8b04b-166">Critical apps, web parts, or docs in the farm (Mission critical farm)</span></span>
    
- <span data-ttu-id="8b04b-167">符合規範標準</span><span class="sxs-lookup"><span data-stu-id="8b04b-167">The Compliance standards met</span></span>
    
- <span data-ttu-id="8b04b-168">自訂</span><span class="sxs-lookup"><span data-stu-id="8b04b-168">Customizations</span></span>
    
<span data-ttu-id="8b04b-169">如果您執行的基本貴公司從 SharePoint 伺服器陣列的某個項目，請說它就像用戶端服務需求的相關重要資料的大型目錄時，您可能會讓刻度旁邊 '重要應用程式'，但也就是 '可用性'-亦即您的業務如果您無法使用 SharePoint 一段時間的，影響。</span><span class="sxs-lookup"><span data-stu-id="8b04b-169">If you run something essential to your business from your SharePoint farm, say it acts like a large catalog of critical data about client service requirements, you may put a tick beside 'Critical apps', but also 'Availability' -- that is, your business would be impacted if you couldn't use SharePoint for a while.</span></span> <span data-ttu-id="8b04b-170">同樣地，您可能會檢查 '自訂'，因為重要服務伺服器陣列提供取決於自訂程式碼、 網站定義或自訂項目會一起運作的數字。</span><span class="sxs-lookup"><span data-stu-id="8b04b-170">Likewise, you might check 'Customizations' because the critical services your farm offers are based on custom code, site definitions, or a number of customizations that work together.</span></span>
  
<span data-ttu-id="8b04b-171">如果 SharePoint 符合這些需求，而不用執行任何外部使用什麼內建至軟體，以及您通常會更新，並執行一般管理以及維護、 您選擇 「 內建的 SharePoint' 的成員，這也可能是您坐在較舊版本的 SharePoint 上的理由。</span><span class="sxs-lookup"><span data-stu-id="8b04b-171">If SharePoint met those needs without your having to do anything outside of using what's built-in to the software, and you generally update it and carry out normal administration and maintenance, you may have chosen 'Built-in SharePoint' -- this may also be your reason for sitting on an older version of SharePoint.</span></span> <span data-ttu-id="8b04b-172">換句話說，它已經沒有您需要它，且您尚未需要升級直到現在，在 Microsoft Office SharePoint Server 2007 終止支援。</span><span class="sxs-lookup"><span data-stu-id="8b04b-172">In other words, it already does what you need it to and you haven't needed to upgrade until now, at Microsoft Office SharePoint Server 2007 end of support.</span></span>
  
<span data-ttu-id="8b04b-173">當您項目符號清單這些項目，您建立準則您的升級。</span><span class="sxs-lookup"><span data-stu-id="8b04b-173">When you bullet-list these things, you create criteria for your upgrade.</span></span> <span data-ttu-id="8b04b-174">換句話說，任何升級必須符合才會視為此列。</span><span class="sxs-lookup"><span data-stu-id="8b04b-174">In other words, any upgrade would have to meet this bar to be considered.</span></span> <span data-ttu-id="8b04b-175">這可以讓您用來排除目前不符合您需求的方法。</span><span class="sxs-lookup"><span data-stu-id="8b04b-175">This gives you a way to rule out methods that don't currently fit your needs.</span></span>
  
### <a name="a-simple-sample-plan"></a><span data-ttu-id="8b04b-176">簡單的範例方案</span><span class="sxs-lookup"><span data-stu-id="8b04b-176">A simple sample plan</span></span>

<span data-ttu-id="8b04b-177">那里可能需要與領導寬共識和其他系統管理員在 SharePoint 升級將所採取的路徑。</span><span class="sxs-lookup"><span data-stu-id="8b04b-177">There may need to be wider consensus with leadership and other admins on the path your SharePoint Upgrade will take.</span></span> <span data-ttu-id="8b04b-178">SharePoint Server 系統管理員通常與 Microsoft SQL Server 系統管理員合作，搭配網路與安全性小組，等等。</span><span class="sxs-lookup"><span data-stu-id="8b04b-178">SharePoint Server Administrators often cooperate with Microsoft SQL Server admins, work with Networking and Security teams, and more.</span></span> <span data-ttu-id="8b04b-179">其中有許多專案關係人，您可能需要建立合約，或調整您的升級與移轉計劃。</span><span class="sxs-lookup"><span data-stu-id="8b04b-179">Where there are a lot of stakeholders, you may need to build agreement for, or adjust, your upgrade and migration plan.</span></span> <span data-ttu-id="8b04b-180">例如，如果您要遷移的資料，使您公司的一部分使用 SharePoint Online 的 Office 365 中，那里可能需要為效能調整或測試您的網路內。</span><span class="sxs-lookup"><span data-stu-id="8b04b-180">For example, if you migrate data so that part of your company uses SharePoint Online in Office 365, there will likely need to be performance tuning or testing inside your network.</span></span> <span data-ttu-id="8b04b-181">受影響的小組應該事先通知。</span><span class="sxs-lookup"><span data-stu-id="8b04b-181">Affected teams should be informed ahead of time.</span></span>
  
<span data-ttu-id="8b04b-182">在 「 我的簡單範例中，我會顯示 SharePoint 系統管理員的提案，並再列出所有專案關係人同意計劃。</span><span class="sxs-lookup"><span data-stu-id="8b04b-182">In my simple sample, I show a SharePoint administrator's proposal and then list out the plan that all the stakeholders agreed upon.</span></span> <span data-ttu-id="8b04b-183">為了清楚起見，文件協議與決策。</span><span class="sxs-lookup"><span data-stu-id="8b04b-183">For clarity, document your agreements and decisions.</span></span>
  
<span data-ttu-id="8b04b-184">規劃伺服器陣列，深入分析後啟動，並嘗試識別角色的伺服器陣列、 痛點及縮小下某些升級選項將會導致其他重要資訊。</span><span class="sxs-lookup"><span data-stu-id="8b04b-184">The plan starts after an in-depth analysis of a farm, and tries to identify the role of the farm, pain points, and other important information that will lead to narrowing down some upgrade options.</span></span> <span data-ttu-id="8b04b-185">之後，由 SharePoint 系統管理員進行升級的提案，以及專案關係人同意的行動計劃。</span><span class="sxs-lookup"><span data-stu-id="8b04b-185">Afterward, an upgrade proposal is made by SharePoint administrator, and stakeholders agree on an action plan.</span></span>
  
<span data-ttu-id="8b04b-186">我 '最重要' 的項目符號清單：</span><span class="sxs-lookup"><span data-stu-id="8b04b-186">My 'most important' bullet list:</span></span>
  
- <span data-ttu-id="8b04b-187">可用性、 內建至 SharePoint 的功能和合規性標準。</span><span class="sxs-lookup"><span data-stu-id="8b04b-187">Availability, features built-in to SharePoint, and Compliance standards.</span></span>
    
- <span data-ttu-id="8b04b-188">大部分的資料是在三個網站集合，與開發小組特別重要和粗用於多個時區中使用世界各地的一個會議工作區。</span><span class="sxs-lookup"><span data-stu-id="8b04b-188">Most of the data is on three site collections, with one Meeting Workspace used by a Dev team particularly important and in heavy use in multiple time-zones worldwide.</span></span>
    
- <span data-ttu-id="8b04b-189">有十七廣泛使用其他網站。</span><span class="sxs-lookup"><span data-stu-id="8b04b-189">There are seventeen other sites that are widely used.</span></span>
    
- <span data-ttu-id="8b04b-190">兩個文件庫 （會議工作區和根網站集合上的文件） 是最大 (超過 8000 docs 每個)。</span><span class="sxs-lookup"><span data-stu-id="8b04b-190">Two document libraries (Meeting Workspace and Documents on the root site collection) are largest (over 8000 docs each).</span></span> <span data-ttu-id="8b04b-191">我們有大量的已封存的文件和試算表附件清單。</span><span class="sxs-lookup"><span data-stu-id="8b04b-191">We have a large number of archived docs and list with spreadsheet attachments.</span></span>
    
- <span data-ttu-id="8b04b-192">有十四清單有必須保持在合規性的敏感資料的文件庫。</span><span class="sxs-lookup"><span data-stu-id="8b04b-192">There are fourteen lists of libraries that have sensitive data that MUST stay in Compliance.</span></span>
    
- <span data-ttu-id="8b04b-193">我們必須能夠執行保留和 e-探索儘我們移。</span><span class="sxs-lookup"><span data-stu-id="8b04b-193">We MUST have the ability to do holds and e-discovery wherever we go.</span></span>
    
- <span data-ttu-id="8b04b-194">有些資料必須保持內部部署，因為常見規則。</span><span class="sxs-lookup"><span data-stu-id="8b04b-194">Some of this data MUST stay on-premises, due to InfoSec rules.</span></span>
    
 <span data-ttu-id="8b04b-195">**我的升級與移轉選項：**</span><span class="sxs-lookup"><span data-stu-id="8b04b-195">**My upgrade and migration choices:**</span></span>
  
|||
|:-----|:-----|
|<span data-ttu-id="8b04b-196">**是**</span><span class="sxs-lookup"><span data-stu-id="8b04b-196">**Yes**</span></span> <br/> |<span data-ttu-id="8b04b-197">**否**</span><span class="sxs-lookup"><span data-stu-id="8b04b-197">**No**</span></span> <br/> |
|<span data-ttu-id="8b04b-198">附加資料庫的升級資料庫</span><span class="sxs-lookup"><span data-stu-id="8b04b-198">Upgrade databases with database attach</span></span>  <br/> |<span data-ttu-id="8b04b-199">就地升級 </span><span class="sxs-lookup"><span data-stu-id="8b04b-199">In-place upgrade</span></span>  <br/> |
|<span data-ttu-id="8b04b-200">升級伺服器陣列-並存</span><span class="sxs-lookup"><span data-stu-id="8b04b-200">Upgrade with farms side-by-side</span></span>  <br/> |<span data-ttu-id="8b04b-201">混合式升級</span><span class="sxs-lookup"><span data-stu-id="8b04b-201">Hybrid Upgrade</span></span>  <br/> |
|<span data-ttu-id="8b04b-202">移轉 API 到 Office 365 中的 SPO （適用於個人網站資料）</span><span class="sxs-lookup"><span data-stu-id="8b04b-202">Migration API to SPO in Office 365 (for personal site data)</span></span>  <br/> |<span data-ttu-id="8b04b-203">SharePoint 混合式 （尚未不需要）</span><span class="sxs-lookup"><span data-stu-id="8b04b-203">SharePoint Hybrid (not needed yet)</span></span>  <br/> |
|<span data-ttu-id="8b04b-204">到 SharePoint Online 重要資料的一些手動資料移轉</span><span class="sxs-lookup"><span data-stu-id="8b04b-204">Some manual data migrations to SharePoint Online for critical data</span></span>  <br/> |<span data-ttu-id="8b04b-205">FastTrack 精靈升級至 Office 365</span><span class="sxs-lookup"><span data-stu-id="8b04b-205">FastTrack wizard upgrade to Office 365</span></span>  <br/> |
   
 <span data-ttu-id="8b04b-206">**我提議的計劃：**</span><span class="sxs-lookup"><span data-stu-id="8b04b-206">**My proposed plan:**</span></span>
  
<span data-ttu-id="8b04b-207">升級，具有內部版本的 SharePoint-並存，某些虛擬化，以便我們可以先升級資料庫。</span><span class="sxs-lookup"><span data-stu-id="8b04b-207">Upgrade on-premises, with versions of SharePoint side-by-side, some virtualized, so that we can upgrade the databases first.</span></span> <span data-ttu-id="8b04b-208">從 SharePoint 2007 前往 SharePoint 2010。</span><span class="sxs-lookup"><span data-stu-id="8b04b-208">Go from SharePoint 2007 to SharePoint 2010.</span></span> <span data-ttu-id="8b04b-209">系統管理員和適用於開發人員測試所產生的伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="8b04b-209">Admins and Devs test the resulting farm.</span></span> <span data-ttu-id="8b04b-210">使用者測試所產生的伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="8b04b-210">Users test the resulting farm.</span></span> <span data-ttu-id="8b04b-211">在這段時間修正任何顯示停止問題。</span><span class="sxs-lookup"><span data-stu-id="8b04b-211">Fix any show-stopping issues during this time.</span></span> <span data-ttu-id="8b04b-212">同樣地，並排顯示、 升級 SharePoint 2010 資料庫至 SharePoint 2013。</span><span class="sxs-lookup"><span data-stu-id="8b04b-212">Again, side-by-side, upgrade SharePoint 2010 databases to SharePoint 2013.</span></span> <span data-ttu-id="8b04b-213">測試。</span><span class="sxs-lookup"><span data-stu-id="8b04b-213">Test.</span></span> <span data-ttu-id="8b04b-214">使用者測試/試驗。</span><span class="sxs-lookup"><span data-stu-id="8b04b-214">User test/pilot.</span></span> <span data-ttu-id="8b04b-215">在這段時間修正任何顯示停止問題。</span><span class="sxs-lookup"><span data-stu-id="8b04b-215">Fix any show-stopping issues during this time.</span></span>
  
- <span data-ttu-id="8b04b-216">請考慮使用 SPO 搜尋同盟混合是否符合您的需求。</span><span class="sxs-lookup"><span data-stu-id="8b04b-216">Consider if a Search Federated Hybrid with SPO meets your needs.</span></span>
    
- <span data-ttu-id="8b04b-217">如果您想要從這裡升級至 SharePoint Online，請考慮[FastTrack 協助](https://fasttrack.microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="8b04b-217">Consider [FastTrack assistance](https://fasttrack.microsoft.com) if you would like to upgrade to SharePoint Online from here.</span></span> 
    
- <span data-ttu-id="8b04b-218">決定任何網站集合是否可以卸載到 Office 365 訂閱。</span><span class="sxs-lookup"><span data-stu-id="8b04b-218">Determine if any site collections can be offloaded to an Office 365 Subscription.</span></span> <span data-ttu-id="8b04b-219">（office 365 符合許多[合規性標準](https://technet.microsoft.com/library/office-365-compliance.aspx)。</span><span class="sxs-lookup"><span data-stu-id="8b04b-219">(Office 365 meets many [Compliance standards](https://technet.microsoft.com/library/office-365-compliance.aspx).</span></span> <span data-ttu-id="8b04b-220">Office 365 具有[eDiscovery](https://support.office.com/article/edea80d6-20a7-40fb-b8c4-5e8c8395f6da)而且可以透過合規性中心的 [[保留](https://support.office.com/article/A18F8975-AA7F-43B4-A7D6-001D14744D8E)。）</span><span class="sxs-lookup"><span data-stu-id="8b04b-220">Office 365 has [eDiscovery](https://support.office.com/article/edea80d6-20a7-40fb-b8c4-5e8c8395f6da) and can do [Holds](https://support.office.com/article/A18F8975-AA7F-43B4-A7D6-001D14744D8E) through the Compliance Centre.)</span></span> 
    
<span data-ttu-id="8b04b-221">否則，請繼續並排顯示升級至 SharePoint Server 2016。</span><span class="sxs-lookup"><span data-stu-id="8b04b-221">Otherwise, continue with a side-by-side upgrade to SharePoint Server 2016.</span></span>
  
> [!NOTE]
> <span data-ttu-id="8b04b-222">規劃系統管理員所做的建議傳來升級和實際的程序是發生與升級所仰賴其他專案關係人交談。</span><span class="sxs-lookup"><span data-stu-id="8b04b-222">In between recommendations made by the administrators planning the upgrade and the actual process are the conversations that happen with other stakeholders on which the upgrade relies.</span></span> <span data-ttu-id="8b04b-223">例如，有時經濟強制執行系統管理員可以變更其計劃。</span><span class="sxs-lookup"><span data-stu-id="8b04b-223">For example, sometimes economics force administrators to change their plans.</span></span> <span data-ttu-id="8b04b-224">任何的最終決策是，您應該記錄同意計劃的是，接下來。</span><span class="sxs-lookup"><span data-stu-id="8b04b-224">Whatever the final decision is, you should document what the agreed-upon plan is, going forward.</span></span> <span data-ttu-id="8b04b-225">它看起來可能像這樣：</span><span class="sxs-lookup"><span data-stu-id="8b04b-225">It might look something like this:</span></span> 
  
 <span data-ttu-id="8b04b-226">**我的行動計劃：**</span><span class="sxs-lookup"><span data-stu-id="8b04b-226">**My action plan:**</span></span>
  
<span data-ttu-id="8b04b-227">內部，我們用來建立預設 SharePoint Server 2010 和 2013年的虛擬環境。</span><span class="sxs-lookup"><span data-stu-id="8b04b-227">On-premises, we use a virtual environment to build default SharePoint Server 2010, and 2013.</span></span> <span data-ttu-id="8b04b-228">SharePoint Server 2016 會建置 2016 符合系統需求的新硬體上。</span><span class="sxs-lookup"><span data-stu-id="8b04b-228">SharePoint Server 2016 will be built on new hardware that meets system requirements for 2016.</span></span> <span data-ttu-id="8b04b-229">我們會執行資料庫附加升級的資料庫從 SharePoint 2007 透過它與 SharePoint Server 2016 之間的所有版本。</span><span class="sxs-lookup"><span data-stu-id="8b04b-229">We will do database attaches to upgrade databases from SharePoint 2007 through all versions between it and SharePoint Server 2016.</span></span> <span data-ttu-id="8b04b-230">核心自訂項目會重新建立為和測試 SharePoint server 2016 環境在這個階段中，如果原生功能已不符合我們的需求。</span><span class="sxs-lookup"><span data-stu-id="8b04b-230">Core customizations are being recreated for and tested in the SharePoint Server 2016 environment at this time, if native features don't already meet our needs.</span></span> <span data-ttu-id="8b04b-231">如果我們已成功，就必須在新硬體上已升級的資料庫，與內部部署伺服器陣列與較少的自訂項目。</span><span class="sxs-lookup"><span data-stu-id="8b04b-231">If we are successful, we will have an on-premises farm on new hardware with upgraded databases, and fewer customizations.</span></span> <span data-ttu-id="8b04b-232">我們會將已升級的內容資料庫附加到新的網站集合，在 SharePoint Server 2013 中，測試、 使用者測試/試驗，，然後執行 DNS 剪下移轉至新的 SharePoint Server 2016 環境，供 live 使用。</span><span class="sxs-lookup"><span data-stu-id="8b04b-232">We'll attach the upgraded content databases to new site collections in SharePoint Server 2013, test, user test/pilot, and then do a DNS cut-over to the new SharePoint Server 2016 environment for live use.</span></span>
  
- <span data-ttu-id="8b04b-233">我們不會立即考慮同盟混合式 SharePoint Server 2016 和 SharePoint Online 之間。</span><span class="sxs-lookup"><span data-stu-id="8b04b-233">We will not consider Federated Hybrid between SharePoint Server 2016 and SharePoint Online right now.</span></span>
    
- <span data-ttu-id="8b04b-234">我們網站預估的 35%可以轉換成新的 SPO 網站使用虛名網域或者，最終，成為 OneDrive for Business 儲存。</span><span class="sxs-lookup"><span data-stu-id="8b04b-234">An estimated 35% of our sites can be turned into new SPO sites with vanity domains, or, ultimately, become OneDrive for Business storage.</span></span> <span data-ttu-id="8b04b-235">尋找其他機會轉換網站，或將新的站台路由傳送到 SPO。</span><span class="sxs-lookup"><span data-stu-id="8b04b-235">Looking for other opportunities to convert sites, or route new sites to SPO.</span></span>
    
- <span data-ttu-id="8b04b-236">這部分的移轉部分將會手動，拖放到 OneDrive for Business 個人網站，以及一些是由移轉 API。</span><span class="sxs-lookup"><span data-stu-id="8b04b-236">Some of this part of the migration will be manual, by drag-and-drop to OneDrive for Business personal sites, and some by migration API.</span></span>
    
<span data-ttu-id="8b04b-237">詳細步驟，或升級的特定指示的連結的數目應遵循計劃。</span><span class="sxs-lookup"><span data-stu-id="8b04b-237">More detailed steps, or a number of links to specific upgrade directions should follow a plan.</span></span> <span data-ttu-id="8b04b-238">MOSS 2007 電腦應該不會解除委任，和虛擬環境維護時，這是因為比較;不過，在升級時，會完整使用者重新導向至 SharePoint Server 2016。</span><span class="sxs-lookup"><span data-stu-id="8b04b-238">The MOSS 2007 computer should not be decommissioned, and virtual environments should be maintained for the sake of comparison; however, the upgrade will be complete when users are redirected to SharePoint Server 2016.</span></span>
  
<span data-ttu-id="8b04b-239">在 [選擇方法通常主要因素是升級的總成本和時間 （您會看到有更多 SharePoint 移轉藍圖文章中） 的成本。</span><span class="sxs-lookup"><span data-stu-id="8b04b-239">Often major factors in choosing a method are the total cost of the upgrade and the cost in time (you'll see more on this in the SharePoint Migration Roadmap article).</span></span> <span data-ttu-id="8b04b-240">不過，規劃向前會受益您大幅中設定期望、 明智，選擇與框架哪些成功看起來像。</span><span class="sxs-lookup"><span data-stu-id="8b04b-240">However, planning ahead will benefit you greatly in setting expectations, choosing wisely, and framing what success will look like.</span></span>
  
## <a name="related-links"></a><span data-ttu-id="8b04b-241">相關連結</span><span class="sxs-lookup"><span data-stu-id="8b04b-241">Related links</span></span>

[<span data-ttu-id="8b04b-242">資源可以幫助您升級從 Office 2007 伺服器和用戶端</span><span class="sxs-lookup"><span data-stu-id="8b04b-242">Resources to help you upgrade from Office 2007 servers and clients</span></span>](upgrade-from-office-2007-servers-and-products.md)
  
[<span data-ttu-id="8b04b-243">搜尋 Microsoft 週期原則和生命週期</span><span class="sxs-lookup"><span data-stu-id="8b04b-243">Microsoft Lifecycle Policy and Lifecycle search</span></span>](https://support.microsoft.com/en-us/lifecycle)
  
[<span data-ttu-id="8b04b-244">適用於 Microsoft 合作夥伴可以協助進行升級或移轉搜尋</span><span class="sxs-lookup"><span data-stu-id="8b04b-244">Search for Microsoft Partners who can help with upgrade or migration</span></span>](https://partnercenter.microsoft.com/en-us/pcv/search)
  

