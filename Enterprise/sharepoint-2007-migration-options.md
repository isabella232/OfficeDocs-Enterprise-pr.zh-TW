---
title: SharePoint 2007 的移轉選項考量
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 1/31/2018
ms.audience: ITPro
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
description: SharePoint Server 2007 已到達結尾的支援，因此該是時候來升級。使用本文以協助您建立您的計劃。
ms.openlocfilehash: 4395bc330efd97ae8865e0fb75f93f04fd162ecd
ms.sourcegitcommit: a9c84d02e94c99ff6b1099b4a9ae695be08210e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2018
ms.locfileid: "21169875"
---
# <a name="sharepoint-2007-migration-options-to-consider"></a><span data-ttu-id="e95e5-104">SharePoint 2007 的移轉選項考量</span><span class="sxs-lookup"><span data-stu-id="e95e5-104">SharePoint 2007 migration options to consider</span></span>

<span data-ttu-id="e95e5-p102">SharePoint Server 2007 與 Microsoft SharePoint 2007 已達到支援結束。該是時候來升級 ！本文提供您的移轉選項的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e95e5-p102">Microsoft SharePoint 2007 and SharePoint Server 2007 have reached end of support. It's time to upgrade! This article provides information about your migration options.</span></span>
  
## <a name="common-upgrade-strategies-for-sharepoint"></a><span data-ttu-id="e95e5-108">SharePoint 一般升級策略</span><span class="sxs-lookup"><span data-stu-id="e95e5-108">Common upgrade strategies for SharePoint</span></span>

<span data-ttu-id="e95e5-p103">有多個 SharePoint Server 環境升級方法。如果您有 Microsoft Office SharePoint Server 2007 伺服器陣列時，以下是升級方法的一些範例：</span><span class="sxs-lookup"><span data-stu-id="e95e5-p103">There are multiple methods to upgrade a SharePoint Server environment. If you have a Microsoft Office SharePoint Server 2007 farm, here are some examples of the upgrade methods:</span></span>
  
- <span data-ttu-id="e95e5-111">資料庫附加</span><span class="sxs-lookup"><span data-stu-id="e95e5-111">Database attach</span></span>
    
- <span data-ttu-id="e95e5-112">並排顯示升級</span><span class="sxs-lookup"><span data-stu-id="e95e5-112">Side-by-side upgrade</span></span>
    
- <span data-ttu-id="e95e5-113">就地升級</span><span class="sxs-lookup"><span data-stu-id="e95e5-113">In-place upgrade</span></span>
    
- <span data-ttu-id="e95e5-114">混合式升級 (就地升級以卸離資料庫 / 不同資料庫附加)</span><span class="sxs-lookup"><span data-stu-id="e95e5-114">Hybrid upgrade (in-place with detached databases / separate database attach)</span></span>
    
- <span data-ttu-id="e95e5-115">SharePoint 混合 （連線 online 至內部部署 SharePoint）</span><span class="sxs-lookup"><span data-stu-id="e95e5-115">SharePoint hybrids (connect online to on-premises SharePoint)</span></span>
    
- <span data-ttu-id="e95e5-116">手動移動網站集合或文件庫之間的資料</span><span class="sxs-lookup"><span data-stu-id="e95e5-116">Manually move data between site collections or libraries</span></span>
    
- <span data-ttu-id="e95e5-117">FastTrack 精靈升級至 Office 365 （[SharePoint Online 部署顧問](https://aka.ms/spoguidance)）</span><span class="sxs-lookup"><span data-stu-id="e95e5-117">FastTrack Wizard upgrade to Office 365 ([SharePoint Online deployment advisor](https://aka.ms/spoguidance))</span></span>
    
- <span data-ttu-id="e95e5-118">SharePoint Online (SPO) Office 365 中移轉 API</span><span class="sxs-lookup"><span data-stu-id="e95e5-118">Migration API to SharePoint Online (SPO) in Office 365</span></span>
    
<span data-ttu-id="e95e5-119">項目最適合您？</span><span class="sxs-lookup"><span data-stu-id="e95e5-119">What works best for you?</span></span>
  
<span data-ttu-id="e95e5-p104">您的伺服器陣列與項目的用於知識專職升級時策略性強度。使用 SharePoint 伺服器陣列的方式可協助您選擇 [從您的選項。</span><span class="sxs-lookup"><span data-stu-id="e95e5-p104">Your knowledge of what your farm does and is used for is a tactical strength when it comes to upgrade. The way people use the SharePoint Farm will help you choose from your options.</span></span>
  
> [!TIP]
> <span data-ttu-id="e95e5-p105">Microsoft Office SharePoint Server 2007 也有未涵蓋以下逐步升級。若清單中的特定步驟的升級文章請參閱[SharePoint Server 2007 結尾支援藍圖](sharepoint-2007-end-of-support.md)。</span><span class="sxs-lookup"><span data-stu-id="e95e5-p105">Microsoft Office SharePoint Server 2007 also has a gradual upgrade not covered here. To see a list of step-specific upgrade articles see the [SharePoint Server 2007 end of support Roadmap](sharepoint-2007-end-of-support.md).</span></span> 
  
<span data-ttu-id="e95e5-p106">請記得要檢查您正在升級為 SharePoint 列傳版[產品生命週期](https://support.microsoft.com/en-us/lifecycle/search)與系統需求。此為必須知道時下一次升級需要 （例如，如果您在 SharePoint Server 2010 規劃多個升級，請先確定您知道其結尾支援日期像舊版產品暫停），並確定您有支援您的計劃的硬體。</span><span class="sxs-lookup"><span data-stu-id="e95e5-p106">Remember to check the [Product Lifecycle](https://support.microsoft.com/en-us/lifecycle/search) and System Requirements for whatever version of SharePoint you're upgrading to. This is so you'll be aware when the next upgrade will be necessary (for example, if you pause at a legacy product like SharePoint Server 2010 to plan for more upgrades, be sure you know its end of support date), and to be certain you have hardware that supports your plan.</span></span> 
  
<span data-ttu-id="e95e5-p107">如果您打算要轉換成部分，或的 SharePoint 網站至 Office 365 雲端中的所有這是時間設為書籤[的 Office 365 服務說明](https://technet.microsoft.com/en-us/library/office-365-service-descriptions.aspx)連結。您需要了解 SharePoint Online 功能的相關服務說明及如何與可能會不同內部部署 SharePoint Server。升級功能的 Microsoft Office SharePoint Server 2007 伺服器陣列。如果您的安裝會中斷的網站，修正那些升級前的。</span><span class="sxs-lookup"><span data-stu-id="e95e5-p107">If you're planning to transition some, or all, of your SharePoint sites to Office 365 in the Cloud, this is a time to bookmark a link to the [Service Descriptions for Office 365](https://technet.microsoft.com/en-us/library/office-365-service-descriptions.aspx). You'll need the Service Descriptions to learn about SharePoint Online features and how they might differ from on-premises SharePoint Server. Upgrade functional Microsoft Office SharePoint Server 2007 farms. If your installation has sites that are broken, fix them prior to upgrade.</span></span>
  
## <a name="a-note-about-managing-risk"></a><span data-ttu-id="e95e5-130">有關管理風險的附註</span><span class="sxs-lookup"><span data-stu-id="e95e5-130">A note about managing risk</span></span>

<span data-ttu-id="e95e5-p108">Like '--並排 ' 的方法是邏輯的重要的升級配置中。當您升級並排顯示時，您維護在 Microsoft Office SharePoint Server 2007 伺服器陣列但建置在伺服器陣列下一版從其 (SharePoint Server 2010) 於新硬體上。這有助於方式有三種：</span><span class="sxs-lookup"><span data-stu-id="e95e5-p108">Methods like 'side-by-side' are important in the scheme of upgrade logic. When you upgrade side-by-side, you maintain your Microsoft Office SharePoint Server 2007 farm, but build a farm the next version up from it (SharePoint Server 2010) on new hardware. This helps in three ways:</span></span>
  
1. <span data-ttu-id="e95e5-134">您必須採取分別進行升級，請使用資料庫附加的 Microsoft Office SharePoint Server 2007 資料庫備份的位置。</span><span class="sxs-lookup"><span data-stu-id="e95e5-134">You have a place to take backups of your Microsoft Office SharePoint Server 2007 databases to upgrade them separately, by using database attach.</span></span>
    
2. <span data-ttu-id="e95e5-135">如果您了解小型數字的重要的文件庫及其他資訊是使用 Microsoft Office SharePoint Server 2007 伺服器陣列中，您可以選擇手動將資料從 Microsoft Office SharePoint Server 2007 移至 SharePoint Server 2010或採取只有特定的網站和 web 的下一版 （這可讓您工作更易於）。</span><span class="sxs-lookup"><span data-stu-id="e95e5-135">If you figure out that only a small number of critical document libraries and other information are in use on your Microsoft Office SharePoint Server 2007 farm, you can choose to manually move data from Microsoft Office SharePoint Server 2007 to SharePoint Server 2010, or take only specific sites and webs to the next version (which can make your job easier).</span></span>
    
3. <span data-ttu-id="e95e5-136">較不您執行 Microsoft Office SharePoint Server 2007 伺服器陣列，直接更安全伺服器陣列的資料包含做為升級。</span><span class="sxs-lookup"><span data-stu-id="e95e5-136">The less you do to the Microsoft Office SharePoint Server 2007 server farm, directly, the safer the data that farm contains as you upgrade.</span></span>
    
<span data-ttu-id="e95e5-p109">像在就地升級方法將會處理直接在 Microsoft Office SharePoint Server 2007 伺服器陣列上，讓您輕鬆選項減少放棄路徑並再次開頭面貌還和環境。盡、 建置在某些 （例如利用和測試原始環境的備份） 的安全措施。例如，如果您的 Microsoft Office SharePoint Server 2007 伺服器陣列虛擬，且重複基於的備份與還原，然後備份和還原您的服務窗口升級前的最新資料庫。了解您可以還原資料庫備份不會選擇只提供保全，它可提供您和平的事項。</span><span class="sxs-lookup"><span data-stu-id="e95e5-p109">Methods like In-Place upgrade will act directly on your Microsoft Office SharePoint Server 2007 farm, giving you fewer easy options to abandon a path and begin again with your pristine environment. As much as possible, build in some safety measures (like taking and testing backups of the original environment). For example, if your Microsoft Office SharePoint Server 2007 farm is virtual, and is duplicated for the purposes of backup and restore, then back-up and restore the most current databases prior to your service window for the upgrade. Knowing that you have the option to restore database backups will not only give you a failsafe, it can give you peace of mind.</span></span>
  
> [!TIP]
> <span data-ttu-id="e95e5-p110">升級的最佳做法文件存在[Microsoft Office SharePoint Server 2007](https://technet.microsoft.com/en-us/library/cc261992%28v=office.12%29.aspx)、 [SharePoint Server 2010](https://technet.microsoft.com/en-us/library/cc261992%28v=office.14%29.aspx)、 [SharePoint Server 2013](https://technet.microsoft.com/en-us/library/cc261992%28v=office.15%29.aspx)及[SharePoint Server 2016](https://technet.microsoft.com/en-us/library/cc261992%28v=office.16%29.aspx)。您也可以搜尋適用於[Microsoft 合作夥伴](https://partnercenter.microsoft.com/en-us/pcv/search)具有與升級或 Office 365 移轉經驗。</span><span class="sxs-lookup"><span data-stu-id="e95e5-p110">Best practices documents for upgrade exist for [Microsoft Office SharePoint Server 2007](https://technet.microsoft.com/en-us/library/cc261992%28v=office.12%29.aspx), [SharePoint Server 2010](https://technet.microsoft.com/en-us/library/cc261992%28v=office.14%29.aspx), [SharePoint Server 2013](https://technet.microsoft.com/en-us/library/cc261992%28v=office.15%29.aspx), and [SharePoint Server 2016](https://technet.microsoft.com/en-us/library/cc261992%28v=office.16%29.aspx). You can also search for [Microsoft Partners](https://partnercenter.microsoft.com/en-us/pcv/search) who have experience with upgrades or Office 365 migrations.</span></span> 
  
## <a name="make-your-plan"></a><span data-ttu-id="e95e5-143">讓您計劃</span><span class="sxs-lookup"><span data-stu-id="e95e5-143">Make your plan</span></span>

<span data-ttu-id="e95e5-p111">如果您需要升級，您需要規劃與所有的這些情況下不會符合其中一個大小。您的計劃可能一樣簡單 '建立 Office 365 訂閱與 SharePoint Online、 註冊的網域和重新導向至儲存其檔案有人員'。而且可能無法。決定其他，而且可相當下您和使用者確實需要什麼。</span><span class="sxs-lookup"><span data-stu-id="e95e5-p111">If you need to upgrade, you need a plan, and one-size doesn't fit all in these cases. Your plan may be as simple as 'Create an Office 365 subscription with SharePoint Online, register a domain, and redirect people to save their files there'. And it may not be. That decision is yours, and it's down to what you and your users really need.</span></span>
  
> [!NOTE]
> <span data-ttu-id="e95e5-p112">它是 risky 在其生命週期結束的軟體上執行。發現問題時不會再修補不支援的產品。這也表示新的安全性威脅發生時，會有任何安全性修補程式或修正因為不再支援的一般生命週期產品。請避免發生該情況下 ！</span><span class="sxs-lookup"><span data-stu-id="e95e5-p112">It's risky to run on software whose lifecycle has ended. Products that are out of support are no longer patched when issues are found. This also means that if new security threats arise, there will be no security patches or fixes because the end-of-lifecycle products are no longer supported. Please avoid that situation!</span></span> 
  
### <a name="first-know-your-farm"></a><span data-ttu-id="e95e5-152">首先，了解您的伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="e95e5-152">First, know your farm</span></span>

<span data-ttu-id="e95e5-p113">在升級時，以協助您做決定應該根據您的伺服器陣列沒有您的組織。則沒有滿足為何需要？什麼是其角色？公司內的每個伺服器陣列可能會有不同的角色。SharePoint 伺服器陣列的一些可能*要徑*、 部分可能會部署封存檔案-安全保存該處。或者，如果您的伺服器陣列會一次填滿許多角色，然後您可能需要知道哪些網站集合、 web 或甚至是文件庫，任何自訂項目，以及他們的重要程度。分析您的資料在此層級似乎許多工作，但它會儲存時間與位置，再升級，或移轉，主要網域它。一旦您知道所有移動的組件，以及最重要的位元，您也將知道什麼已 outgrown 和可以留下。該知識僅受益向前移。</span><span class="sxs-lookup"><span data-stu-id="e95e5-p113">When upgrading, your decision-making should be based on what your farm does for your organization. What need does it satisfy? What's its role? Each farm in your company may have a different role. Some of your SharePoint farms may be  *critical*  , some may be file archives -- there for safe-keeping. Or, if your farm fills many roles at once, then you may need to know what site collections, webs, or even document libraries do, any customizations, and how important they are. Analyzing your data at this level may seem like a lot of work, but it saves time and effort to master your domain before you upgrade, or migrate, it. Once you know all the moving parts, and the most important bits, you'll also know what you've outgrown and can leave behind. That knowledge will only benefit you going forward.</span></span> 
  
<span data-ttu-id="e95e5-162">如此，使用者說關於在 SharePoint 伺服器陣列最重要？</span><span class="sxs-lookup"><span data-stu-id="e95e5-162">So, what are users saying is most important about your SharePoint Server farm?</span></span>
  
- <span data-ttu-id="e95e5-163">內建的 SharePoint 功能</span><span class="sxs-lookup"><span data-stu-id="e95e5-163">Built-in SharePoint features</span></span>
    
- <span data-ttu-id="e95e5-164">大型資料主體 （例如封存的檔案）</span><span class="sxs-lookup"><span data-stu-id="e95e5-164">The large data corpus (such as an archive of files)</span></span>
    
- <span data-ttu-id="e95e5-165">可用性</span><span class="sxs-lookup"><span data-stu-id="e95e5-165">Availability</span></span>
    
- <span data-ttu-id="e95e5-166">要徑應用程式、 網頁組件或伺服器陣列 （任務關鍵伺服器陣列） 中的文件</span><span class="sxs-lookup"><span data-stu-id="e95e5-166">Critical apps, web parts, or docs in the farm (Mission critical farm)</span></span>
    
- <span data-ttu-id="e95e5-167">符合規範標準</span><span class="sxs-lookup"><span data-stu-id="e95e5-167">The Compliance standards met</span></span>
    
- <span data-ttu-id="e95e5-168">自訂</span><span class="sxs-lookup"><span data-stu-id="e95e5-168">Customizations</span></span>
    
<span data-ttu-id="e95e5-p114">如果要執行的基本業務 SharePoint 伺服器陣列中的某個項目，說它就像用戶端的服務需求的相關的重要資料的大型目錄，您可能會放入旁邊 '關鍵應用程式' 刻度但也就是 '可用性'-亦即您的業務如果您無法使用 SharePoint 一段的，影響。同樣地，您可能會檢查 '自訂' 因為緊急服務提供為基礎的自訂程式碼、 網站定義或數目可以搭配使用的自訂伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="e95e5-p114">If you run something essential to your business from your SharePoint farm, say it acts like a large catalog of critical data about client service requirements, you may put a tick beside 'Critical apps', but also 'Availability' -- that is, your business would be impacted if you couldn't use SharePoint for a while. Likewise, you might check 'Customizations' because the critical services your farm offers are based on custom code, site definitions, or a number of customizations that work together.</span></span>
  
<span data-ttu-id="e95e5-p115">如果 SharePoint 符合這些需求而不需要執行任何動作以外的地方使用內建軟體和通常其更新為與執行一般管理與維護、 您選擇 ' 內建 SharePoint'--也可能是您坐在舊版 SharePoint 的原因。換句話說，它已經沒有您需要它和尚未需要升級之前立即、 結尾 Microsoft Office SharePoint Server 2007 的支援。</span><span class="sxs-lookup"><span data-stu-id="e95e5-p115">If SharePoint met those needs without your having to do anything outside of using what's built-in to the software, and you generally update it and carry out normal administration and maintenance, you may have chosen 'Built-in SharePoint' -- this may also be your reason for sitting on an older version of SharePoint. In other words, it already does what you need it to and you haven't needed to upgrade until now, at Microsoft Office SharePoint Server 2007 end of support.</span></span>
  
<span data-ttu-id="e95e5-p116">當您項目符號清單您升級的欄位建立準則這些的事項。換句話說，升級程序必須符合必須考量此列。這可讓您能夠在規則出目前不符合您需求的方法。</span><span class="sxs-lookup"><span data-stu-id="e95e5-p116">When you bullet-list these things, you create criteria for your upgrade. In other words, any upgrade would have to meet this bar to be considered. This gives you a way to rule out methods that don't currently fit your needs.</span></span>
  
### <a name="a-simple-sample-plan"></a><span data-ttu-id="e95e5-176">簡單範例計劃</span><span class="sxs-lookup"><span data-stu-id="e95e5-176">A simple sample plan</span></span>

<span data-ttu-id="e95e5-p117">那里可能會需要較多共識與領導與 SharePoint 升級所需的時間的路徑上其他系統管理員。SharePoint Server 管理員通常與 Microsoft SQL Server 系統管理員合作、 網路與安全性小組及其他與搭配使用。其中有許多的專案關係人，您可能需要建立協議，或調整您的升級與移轉的計劃。例如，如果使您公司的一部分使用 SharePoint Online 在 Office 365 中移轉資料，那里可能必須是效能調整或測試您的網路內。受影響的小組應該隨時通知。</span><span class="sxs-lookup"><span data-stu-id="e95e5-p117">There may need to be wider consensus with leadership and other admins on the path your SharePoint Upgrade will take. SharePoint Server Administrators often cooperate with Microsoft SQL Server admins, work with Networking and Security teams, and more. Where there are a lot of stakeholders, you may need to build agreement for, or adjust, your upgrade and migration plan. For example, if you migrate data so that part of your company uses SharePoint Online in Office 365, there will likely need to be performance tuning or testing inside your network. Affected teams should be informed ahead of time.</span></span>
  
<span data-ttu-id="e95e5-p118">在簡單的範例中，我顯示 SharePoint 管理員手冊提案]，然後列出所有專案關係人同意計劃。為避免混淆，文件協議和決策。</span><span class="sxs-lookup"><span data-stu-id="e95e5-p118">In my simple sample, I show a SharePoint administrator's proposal and then list out the plan that all the stakeholders agreed upon. For clarity, document your agreements and decisions.</span></span>
  
<span data-ttu-id="e95e5-p119">規劃伺服器陣列中的深入分析後啟動，嘗試找出在伺服器陣列、 設計師點及其他重要的資訊，將會導致某些升級選項關閉縮小角色。認知，升級提案進行 SharePoint 管理員與專案關係人同意動作計劃。</span><span class="sxs-lookup"><span data-stu-id="e95e5-p119">The plan starts after an in-depth analysis of a farm, and tries to identify the role of the farm, pain points, and other important information that will lead to narrowing down some upgrade options. Afterward, an upgrade proposal is made by SharePoint administrator, and stakeholders agree on an action plan.</span></span>
  
<span data-ttu-id="e95e5-186">我 '最重要' 的項目符號清單：</span><span class="sxs-lookup"><span data-stu-id="e95e5-186">My 'most important' bullet list:</span></span>
  
- <span data-ttu-id="e95e5-187">可用性、 sharepoint、 內建的功能及規範標準。</span><span class="sxs-lookup"><span data-stu-id="e95e5-187">Availability, features built-in to SharePoint, and Compliance standards.</span></span>
    
- <span data-ttu-id="e95e5-188">大部分的資料為一個會議工作區及大量使用多個時區中特別重要的開發人員小組所使用全世界加上三個網站集合。</span><span class="sxs-lookup"><span data-stu-id="e95e5-188">Most of the data is on three site collections, with one Meeting Workspace used by a Dev team particularly important and in heavy use in multiple time-zones worldwide.</span></span>
    
- <span data-ttu-id="e95e5-189">沒有十七廣泛使用其他網站。</span><span class="sxs-lookup"><span data-stu-id="e95e5-189">There are seventeen other sites that are widely used.</span></span>
    
- <span data-ttu-id="e95e5-p120">兩個文件庫 （會議工作區和根網站集合的文件） 的最大 （超過 8000 文件每一個）。我們有大量的封存的文件和清單試算表附件。</span><span class="sxs-lookup"><span data-stu-id="e95e5-p120">Two document libraries (Meeting Workspace and Documents on the root site collection) are largest (over 8000 docs each). We have a large number of archived docs and list with spreadsheet attachments.</span></span>
    
- <span data-ttu-id="e95e5-192">有十四清單包含機密資料必須保持在最符合性中的文件庫。</span><span class="sxs-lookup"><span data-stu-id="e95e5-192">There are fourteen lists of libraries that have sensitive data that MUST stay in Compliance.</span></span>
    
- <span data-ttu-id="e95e5-193">我們必須能夠執行保留及電子探索儘我們移。</span><span class="sxs-lookup"><span data-stu-id="e95e5-193">We MUST have the ability to do holds and e-discovery wherever we go.</span></span>
    
- <span data-ttu-id="e95e5-194">此資料的一些必須保持在最內部部署，因為常見規則。</span><span class="sxs-lookup"><span data-stu-id="e95e5-194">Some of this data MUST stay on-premises, due to InfoSec rules.</span></span>
    
 <span data-ttu-id="e95e5-195">**「 我的升級與移轉的選項：**</span><span class="sxs-lookup"><span data-stu-id="e95e5-195">**My upgrade and migration choices:**</span></span>
  
|||
|:-----|:-----|
|<span data-ttu-id="e95e5-196">**是**</span><span class="sxs-lookup"><span data-stu-id="e95e5-196">**Yes**</span></span> <br/> |<span data-ttu-id="e95e5-197">**無**</span><span class="sxs-lookup"><span data-stu-id="e95e5-197">**No**</span></span> <br/> |
|<span data-ttu-id="e95e5-198">附加資料庫以升級資料庫</span><span class="sxs-lookup"><span data-stu-id="e95e5-198">Upgrade databases with database attach</span></span>  <br/> |<span data-ttu-id="e95e5-199">就地升級</span><span class="sxs-lookup"><span data-stu-id="e95e5-199">In-place upgrade</span></span>  <br/> |
|<span data-ttu-id="e95e5-200">升級伺服器陣列的並行</span><span class="sxs-lookup"><span data-stu-id="e95e5-200">Upgrade with farms side-by-side</span></span>  <br/> |<span data-ttu-id="e95e5-201">混合式升級</span><span class="sxs-lookup"><span data-stu-id="e95e5-201">Hybrid Upgrade</span></span>  <br/> |
|<span data-ttu-id="e95e5-202">移轉 API 至 Office 365 中的 SPO （適用於個人網站資料）</span><span class="sxs-lookup"><span data-stu-id="e95e5-202">Migration API to SPO in Office 365 (for personal site data)</span></span>  <br/> |<span data-ttu-id="e95e5-203">SharePoint 混合式 （尚不需要）</span><span class="sxs-lookup"><span data-stu-id="e95e5-203">SharePoint Hybrid (not needed yet)</span></span>  <br/> |
|<span data-ttu-id="e95e5-204">部分的手動資料移轉至 SharePoint Online 的重要資料。</span><span class="sxs-lookup"><span data-stu-id="e95e5-204">Some manual data migrations to SharePoint Online for critical data</span></span>  <br/> |<span data-ttu-id="e95e5-205">FastTrack 精靈] 升級至 Office 365</span><span class="sxs-lookup"><span data-stu-id="e95e5-205">FastTrack wizard upgrade to Office 365</span></span>  <br/> |
   
 <span data-ttu-id="e95e5-206">**我提議的計劃：**</span><span class="sxs-lookup"><span data-stu-id="e95e5-206">**My proposed plan:**</span></span>
  
<span data-ttu-id="e95e5-p121">升級，以內部 SharePoint-並排，某些虛擬化，如此我們先升級資料庫的版本。從 SharePoint 2007 移至 [SharePoint 2010。系統管理員和適用於開發人員測試所產生的伺服器陣列。使用者測試所產生的伺服器陣列。在這段時間修正任何顯示停止問題。同樣地，並排顯示、 升級 SharePoint 2010 資料庫至 SharePoint 2013。Test 使用者測試/試驗。在這段時間修正任何顯示停止問題。</span><span class="sxs-lookup"><span data-stu-id="e95e5-p121">Upgrade on-premises, with versions of SharePoint side-by-side, some virtualized, so that we can upgrade the databases first. Go from SharePoint 2007 to SharePoint 2010. Admins and Devs test the resulting farm. Users test the resulting farm. Fix any show-stopping issues during this time. Again, side-by-side, upgrade SharePoint 2010 databases to SharePoint 2013. Test. User test/pilot. Fix any show-stopping issues during this time.</span></span>
  
- <span data-ttu-id="e95e5-216">請考慮使用 SPO 搜尋同盟混合式是否符合您的需求。</span><span class="sxs-lookup"><span data-stu-id="e95e5-216">Consider if a Search Federated Hybrid with SPO meets your needs.</span></span>
    
- <span data-ttu-id="e95e5-217">如果您想要從這裡升級至 SharePoint Online，請考慮[FastTrack 尋求協助](https://fasttrack.microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="e95e5-217">Consider [FastTrack assistance](https://fasttrack.microsoft.com) if you would like to upgrade to SharePoint Online from here.</span></span> 
    
- <span data-ttu-id="e95e5-p122">決定任何網站集合是否可以卸載到 Office 365 訂閱。（office 365 符合許多[規範標準 （英文）](https://technet.microsoft.com/library/office-365-compliance.aspx)。Office 365 具有[eDiscovery](https://support.office.com/article/edea80d6-20a7-40fb-b8c4-5e8c8395f6da)往往可以透過規範中心的 [[保留](https://support.office.com/article/A18F8975-AA7F-43B4-A7D6-001D14744D8E)。）</span><span class="sxs-lookup"><span data-stu-id="e95e5-p122">Determine if any site collections can be offloaded to an Office 365 Subscription. (Office 365 meets many [Compliance standards](https://technet.microsoft.com/library/office-365-compliance.aspx). Office 365 has [eDiscovery](https://support.office.com/article/edea80d6-20a7-40fb-b8c4-5e8c8395f6da) and can do [Holds](https://support.office.com/article/A18F8975-AA7F-43B4-A7D6-001D14744D8E) through the Compliance Centre.)</span></span> 
    
<span data-ttu-id="e95e5-221">否則請繼續執行 SharePoint Server 2016 的並排顯示升級。</span><span class="sxs-lookup"><span data-stu-id="e95e5-221">Otherwise, continue with a side-by-side upgrade to SharePoint Server 2016.</span></span>
  
> [!NOTE]
> <span data-ttu-id="e95e5-p123">規劃系統管理員所做的建議傳來的升級與實際的程序是發生與其他專案關係人在其升級依賴的交談。例如，有時經濟強制管理員變更其計劃。列傳的最終決策是，您應該記錄同意計劃的功能和向前移。它可能具有的外觀類似如下：</span><span class="sxs-lookup"><span data-stu-id="e95e5-p123">In between recommendations made by the administrators planning the upgrade and the actual process are the conversations that happen with other stakeholders on which the upgrade relies. For example, sometimes economics force administrators to change their plans. Whatever the final decision is, you should document what the agreed-upon plan is, going forward. It might look something like this:</span></span> 
  
 <span data-ttu-id="e95e5-226">**我巨集指令的計劃：**</span><span class="sxs-lookup"><span data-stu-id="e95e5-226">**My action plan:**</span></span>
  
<span data-ttu-id="e95e5-p124">內部，我們用來建立預設 SharePoint Server 2010 與 2013年的虛擬環境。SharePoint Server 2016 會建立新的 2016年符合系統需求的硬體上。我們將會執行資料庫附加至資料庫從 SharePoint 2007 升級到它與 SharePoint Server 2016 之間的所有版本。核心自訂項目正在重新建立的及測試 SharePoint Server 中 2016年環境在此階段中，如果原生功能已不符合我們的需求。如果我們都成功，我們將會有已升級的資料庫，以在新硬體上的內部部署伺服器陣列及較少的自訂項目。我們將已升級內容資料庫附加至新的網站集合的 SharePoint Server 2013，測試、 使用者測試/試驗並再執行 DNS 剪下容錯移轉至新的 SharePoint Server 2016 環境 live 使用。</span><span class="sxs-lookup"><span data-stu-id="e95e5-p124">On-premises, we use a virtual environment to build default SharePoint Server 2010, and 2013. SharePoint Server 2016 will be built on new hardware that meets system requirements for 2016. We will do database attaches to upgrade databases from SharePoint 2007 through all versions between it and SharePoint Server 2016. Core customizations are being recreated for and tested in the SharePoint Server 2016 environment at this time, if native features don't already meet our needs. If we are successful, we will have an on-premises farm on new hardware with upgraded databases, and fewer customizations. We'll attach the upgraded content databases to new site collections in SharePoint Server 2013, test, user test/pilot, and then do a DNS cut-over to the new SharePoint Server 2016 environment for live use.</span></span>
  
- <span data-ttu-id="e95e5-233">我們不會來說考量同盟混合式 SharePoint Server 2016 與 SharePoint Online 之間。</span><span class="sxs-lookup"><span data-stu-id="e95e5-233">We will not consider Federated Hybrid between SharePoint Server 2016 and SharePoint Online right now.</span></span>
    
- <span data-ttu-id="e95e5-p125">我們網站估計的 35%可轉換成與虛名網域的新 SPO 網站或者，最終，成為 OneDrive for Business 存放區。尋找其他需要在轉換的網站，或路由傳送給 o SPO 的新網站。</span><span class="sxs-lookup"><span data-stu-id="e95e5-p125">An estimated 35% of our sites can be turned into new SPO sites with vanity domains, or, ultimately, become OneDrive for Business storage. Looking for other opportunities to convert sites, or route new sites to SPO.</span></span>
    
- <span data-ttu-id="e95e5-236">此部分的遷移的一些會手動-拖至 OneDrive for Business 的個人網站，並某些由移轉 API。</span><span class="sxs-lookup"><span data-stu-id="e95e5-236">Some of this part of the migration will be manual, by drag-and-drop to OneDrive for Business personal sites, and some by migration API.</span></span>
    
<span data-ttu-id="e95e5-p126">詳細步驟，或特定的升級指示要連結的數目應遵循計劃。MOSS 2007 電腦應該不會解除委任、 和虛擬環境應該維護這是因為比較;不過，將會完成升級時使用者重新導向至 SharePoint Server 2016。</span><span class="sxs-lookup"><span data-stu-id="e95e5-p126">More detailed steps, or a number of links to specific upgrade directions should follow a plan. The MOSS 2007 computer should not be decommissioned, and virtual environments should be maintained for the sake of comparison; however, the upgrade will be complete when users are redirected to SharePoint Server 2016.</span></span>
  
<span data-ttu-id="e95e5-p127">選擇方法通常主要因素是升級的總成本和時間 （您會看到有更多 SharePoint 移轉藍圖文章中） 的成本。不過，規劃事先將在方面獲益您大幅設定期望、 選擇 [，和框架何種成功看起來。</span><span class="sxs-lookup"><span data-stu-id="e95e5-p127">Often major factors in choosing a method are the total cost of the upgrade and the cost in time (you'll see more on this in the SharePoint Migration Roadmap article). However, planning ahead will benefit you greatly in setting expectations, choosing wisely, and framing what success will look like.</span></span>
  
## <a name="related-links"></a><span data-ttu-id="e95e5-241">相關連結</span><span class="sxs-lookup"><span data-stu-id="e95e5-241">Related links</span></span>

[<span data-ttu-id="e95e5-242">可協助您升級從 Office 2007 的伺服器和用戶端的資源</span><span class="sxs-lookup"><span data-stu-id="e95e5-242">Resources to help you upgrade from Office 2007 servers and clients</span></span>](upgrade-from-office-2007-servers-and-products.md)
  
[<span data-ttu-id="e95e5-243">搜尋 Microsoft 技術支援週期原則和生命週期</span><span class="sxs-lookup"><span data-stu-id="e95e5-243">Microsoft Lifecycle Policy and Lifecycle search</span></span>](https://support.microsoft.com/en-us/lifecycle)
  
[<span data-ttu-id="e95e5-244">Microsoft 合作夥伴可以協助升級或移轉搜尋</span><span class="sxs-lookup"><span data-stu-id="e95e5-244">Search for Microsoft Partners who can help with upgrade or migration</span></span>](https://partnercenter.microsoft.com/en-us/pcv/search)
  

