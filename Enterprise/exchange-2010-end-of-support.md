---
title: Exchange 2010 結尾的支援藍圖
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.assetid: e150e7b9-c432-4c8d-a0ae-c11847129a7d
description: Exchange 2010 已接近支援結束。用於此規劃藍圖做為指南準備升級到 Exchange Online 或 Exchange Server 內部部署的較新版本。
ms.openlocfilehash: e655edcc38723acd622fc6abc62a00d3f3e36738
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915188"
---
# <a name="exchange-2010-end-of-support-roadmap"></a><span data-ttu-id="e1c00-104">Exchange 2010 結尾的支援藍圖</span><span class="sxs-lookup"><span data-stu-id="e1c00-104">Exchange 2010 end of support roadmap</span></span>

<span data-ttu-id="e1c00-p102">在**2020 年 1 月 14、**、 Exchange Server 2010 會連絡支援結束。如果您已經尚未開始移轉至 Office 365 的 Exchange 2010 或 Exchange 2016、 現在是以啟動您進行規劃的時間。</span><span class="sxs-lookup"><span data-stu-id="e1c00-p102">On **January 14, 2020**, Exchange Server 2010 will reach end of support. If you haven't already begun your migration from Exchange 2010 to Office 365 or Exchange 2016, now's the time to start your planning.</span></span> 
  
## <a name="what-does-end-of-support-mean"></a><span data-ttu-id="e1c00-107">支援平均數何種實務結尾？</span><span class="sxs-lookup"><span data-stu-id="e1c00-107">What does end of support mean?</span></span>

<span data-ttu-id="e1c00-p103">Exchange Server 幾乎所有的 Microsoft 產品，例如有支援週期的期間我們提供的新功能、 修正錯誤、 安全性修正程式等等。此技術支援週期通常是一個工期 10 年度從產品的初始版本，日期的此技術支援週期的結尾就所謂的產品支援結束。Exchange 2010 達到支援 2020 年 1 月 14、 在其結束時將不再提供 Microsoft：</span><span class="sxs-lookup"><span data-stu-id="e1c00-p103">Exchange Server, like almost all Microsoft products, has a support lifecycle during which we provide new features, bug fixes, security fixes, and so on. This lifecycle typically lasts for 10 years from the date of the product's initial release, and the end of this lifecycle is known as the product's end of support. When Exchange 2010 reaches its end of support on January 14, 2020, Microsoft will no longer provide:</span></span>
  
- <span data-ttu-id="e1c00-111">技術支援問題，可能會發生;</span><span class="sxs-lookup"><span data-stu-id="e1c00-111">Technical support for problems that may occur;</span></span>
    
- <span data-ttu-id="e1c00-112">錯誤修正的問題會發現及，可能會影響穩定性及可用性的伺服器;</span><span class="sxs-lookup"><span data-stu-id="e1c00-112">Bug fixes for issues that are discovered and that may impact the stability and usability of the server;</span></span>
    
- <span data-ttu-id="e1c00-113">安全性弱點的探索和可能會提出伺服器安全性缺口; 容易受到的修正</span><span class="sxs-lookup"><span data-stu-id="e1c00-113">Security fixes for vulnerabilities that are discovered and that may make the server vulnerable to security breaches;</span></span>
    
- <span data-ttu-id="e1c00-114">時間的時區更新。</span><span class="sxs-lookup"><span data-stu-id="e1c00-114">Time zone updates.</span></span>
    
<span data-ttu-id="e1c00-p104">Exchange 2010 的安裝會繼續執行這個日期之後。但是，由於上述變更，我們強烈建議您盡移轉從 Exchange 2010。</span><span class="sxs-lookup"><span data-stu-id="e1c00-p104">Your installation of Exchange 2010 will continue to run after this date. However, because of the changes listed above, we strongly recommend that you migrate from Exchange 2010 as soon as possible.</span></span>
  
<span data-ttu-id="e1c00-117">如需接近支援結束的 Office 2010 伺服器的詳細資訊，請參閱[資源以協助您升級從 Office 2010 伺服器和用戶端](upgrade-from-office-2010-servers-and-products.md)。</span><span class="sxs-lookup"><span data-stu-id="e1c00-117">For more information about Office 2010 servers nearing the end of support, see [Resources to help you upgrade from Office 2010 servers and clients](upgrade-from-office-2010-servers-and-products.md).</span></span>
  
## <a name="what-are-my-options"></a><span data-ttu-id="e1c00-118">我的選項為何？</span><span class="sxs-lookup"><span data-stu-id="e1c00-118">What are my options?</span></span>

<span data-ttu-id="e1c00-p105">即將達到其結尾支援 Exchange 2010，這是更好的時間來探索您的選項和準備的移轉規劃。您可以：</span><span class="sxs-lookup"><span data-stu-id="e1c00-p105">With Exchange 2010 reaching its end of support, this is a great time to explore your options and prepare a migration plan. You can:</span></span>
  
- <span data-ttu-id="e1c00-121">移轉至 Office 365 使用轉換、 express 或混合式遷移;</span><span class="sxs-lookup"><span data-stu-id="e1c00-121">Migrate to Office 365 using cutover, express, or hybrid migration;</span></span> 
    
- <span data-ttu-id="e1c00-122">將 Exchange 2010 伺服器移轉至新版 Exchange 內部部署伺服器上。</span><span class="sxs-lookup"><span data-stu-id="e1c00-122">Migrate your Exchange 2010 servers to a newer version of Exchange on your on-premises servers.</span></span>
    
<span data-ttu-id="e1c00-123">下列各節探索更詳細地每個選項。</span><span class="sxs-lookup"><span data-stu-id="e1c00-123">The following sections explore each option in more detail.</span></span>
  
### <a name="migrate-to-office-365"></a><span data-ttu-id="e1c00-124">移轉至 Office 365</span><span class="sxs-lookup"><span data-stu-id="e1c00-124">Migrate to Office 365</span></span>

<span data-ttu-id="e1c00-p106">將您的電子郵件移轉至 Office 365 是您最佳與最簡單的選項可幫助您淘汰 Exchange 2010 部署。使用 Office 365 遷移，可以進行單一一個躍點從舊的技術先進的功能類似：</span><span class="sxs-lookup"><span data-stu-id="e1c00-p106">Migrating your email to Office 365 is your best and simplest option to help you retire your Exchange 2010 deployment. With a migration to Office 365, you can make a single hop from old technology to state of the art features, like:</span></span>
  
- <span data-ttu-id="e1c00-127">規範功能保留原則，就地與訴訟暫止狀態，例如就地 eDiscovery 及多;</span><span class="sxs-lookup"><span data-stu-id="e1c00-127">Compliance capabilities such as Retention Policies, In-Place and Litigation Hold, in-place eDiscovery, and more;</span></span>
    
- <span data-ttu-id="e1c00-128">Microsoft 小組;</span><span class="sxs-lookup"><span data-stu-id="e1c00-128">Microsoft Teams;</span></span>
    
- <span data-ttu-id="e1c00-129">Power BI;</span><span class="sxs-lookup"><span data-stu-id="e1c00-129">Power BI;</span></span>
    
- <span data-ttu-id="e1c00-130">具有焦點的收件匣;</span><span class="sxs-lookup"><span data-stu-id="e1c00-130">Focused Inbox;</span></span>
    
- <span data-ttu-id="e1c00-131">探索分析;</span><span class="sxs-lookup"><span data-stu-id="e1c00-131">Delve Analytics;</span></span>
    
- <span data-ttu-id="e1c00-132">以程式設計方式存取電子郵件、 行事曆、 連絡人、 等等的 REST Api。</span><span class="sxs-lookup"><span data-stu-id="e1c00-132">REST APIs for programmatic access to email, calendars, contacts, and so on.</span></span>
    
<span data-ttu-id="e1c00-p107">Office 365 也會取得新功能與經驗第一個和您和使用者可以通常是啟動立即使用這些。除了新功能，您將不會有擔心：</span><span class="sxs-lookup"><span data-stu-id="e1c00-p107">Office 365 also gets new features and experiences first and you and your users can usually start using them right away. In addition to new features, you won't have to worry about:</span></span>
  
- <span data-ttu-id="e1c00-135">購買和維護硬體;</span><span class="sxs-lookup"><span data-stu-id="e1c00-135">Purchasing and maintaining hardware;</span></span>
    
- <span data-ttu-id="e1c00-136">支付加熱及冷卻一部伺服器 ；</span><span class="sxs-lookup"><span data-stu-id="e1c00-136">Paying for heating and cooling of your servers;</span></span>
    
- <span data-ttu-id="e1c00-137">在安全性、 產品及時間的時區修正; 保持最新</span><span class="sxs-lookup"><span data-stu-id="e1c00-137">Keeping up to date on security, product, and time zone fixes;</span></span>
    
- <span data-ttu-id="e1c00-138">維護儲存空間和軟體以支援規範需求 ；</span><span class="sxs-lookup"><span data-stu-id="e1c00-138">Maintaining storage and software to support compliance requirements;</span></span>
    
- <span data-ttu-id="e1c00-139">升級至新版本的 Exchange-你一律在最新版的 Office 365 中的 Exchange。</span><span class="sxs-lookup"><span data-stu-id="e1c00-139">Upgrading to a new version of Exchange - you're always on the latest version of Exchange in Office 365.</span></span>
    
#### <a name="how-should-i-migrate-to-office-365"></a><span data-ttu-id="e1c00-140">我應該在如何移轉至 Office 365？</span><span class="sxs-lookup"><span data-stu-id="e1c00-140">How should I migrate to Office 365?</span></span>

<span data-ttu-id="e1c00-p108">根據您的組織，您必須將協助您做好至 Office 365 的一些選項。選擇移轉選項、 時需要考慮一些事項 like 基座或您要移動的信箱、 長您想要移轉至最後一個，以及您是否需要內部部署安裝及期間的 Office 365 之間順利整合的數目移轉。下表顯示您的移轉選項和將決定您要使用哪一種方法最重要因素。</span><span class="sxs-lookup"><span data-stu-id="e1c00-p108">Depending on your organization, you have a few options that'll help you get to Office 365. When choosing a migration option, you need to consider a few things like the number of seats or mailboxes you need to move, how long you want the migration to last, and whether you need a seamless integration between your on-premises installation and Office 365 during the migration. This table shows your migration options and the most important factors that'll determine which method you'll use.</span></span>
  
|<span data-ttu-id="e1c00-144">**遷移選項**</span><span class="sxs-lookup"><span data-stu-id="e1c00-144">**Migration option**</span></span>|<span data-ttu-id="e1c00-145">**組織大小**</span><span class="sxs-lookup"><span data-stu-id="e1c00-145">**Organization size**</span></span>|<span data-ttu-id="e1c00-146">**期間**</span><span class="sxs-lookup"><span data-stu-id="e1c00-146">**Duration**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="e1c00-147">轉換移轉</span><span class="sxs-lookup"><span data-stu-id="e1c00-147">Cutover migration</span></span>  <br/> |<span data-ttu-id="e1c00-148">少於 150 基座</span><span class="sxs-lookup"><span data-stu-id="e1c00-148">Fewer than 150 seats</span></span>  <br/> |<span data-ttu-id="e1c00-149">一週或更少</span><span class="sxs-lookup"><span data-stu-id="e1c00-149">A week or less</span></span>  <br/> |
|<span data-ttu-id="e1c00-150">Express 移轉</span><span class="sxs-lookup"><span data-stu-id="e1c00-150">Express migration</span></span>  <br/> |<span data-ttu-id="e1c00-151">少於 150 基座</span><span class="sxs-lookup"><span data-stu-id="e1c00-151">Fewer than 150 seats</span></span>  <br/> |<span data-ttu-id="e1c00-152">幾週或更少</span><span class="sxs-lookup"><span data-stu-id="e1c00-152">A couple weeks or less</span></span>  <br/> |
|<span data-ttu-id="e1c00-153">完整的混合式遷移</span><span class="sxs-lookup"><span data-stu-id="e1c00-153">Full hybrid migration</span></span>  <br/> |<span data-ttu-id="e1c00-154">多個 150 基座</span><span class="sxs-lookup"><span data-stu-id="e1c00-154">More than 150 seats</span></span>  <br/> |<span data-ttu-id="e1c00-155">幾週或更多</span><span class="sxs-lookup"><span data-stu-id="e1c00-155">A few weeks or more</span></span>  <br/> |
   
<span data-ttu-id="e1c00-p109">下列各節提供這些方法的概觀。取出[決定移轉路徑](https://support.office.com/en-us/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27)以了解各方法的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="e1c00-p109">The following sections give you an overview of these methods. Check out [Decide on a migration path](https://support.office.com/en-us/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27) to learn the details of each method.</span></span> 
  
#### <a name="cutover-migration"></a><span data-ttu-id="e1c00-158">轉換移轉</span><span class="sxs-lookup"><span data-stu-id="e1c00-158">Cutover migration</span></span>

<span data-ttu-id="e1c00-159">轉換遷移是其中一個位置，在預先選取的日期和時間，您將移轉所有您的信箱、 通訊群組、 連絡人、 等等，至 Office 365;當您已完成，您將會關閉您的內部部署 Exchange 伺服器並開始使用 Office 365 以獨佔模式。</span><span class="sxs-lookup"><span data-stu-id="e1c00-159">A cutover migration is one where, at a pre-selected date and time, you'll migrate all your mailboxes, distribution groups, contacts, and so on, to Office 365; when you've finished, you'll shut down your on-premises Exchange servers and start using Office 365 exclusively.</span></span>
  
<span data-ttu-id="e1c00-p110">一次完成式遷移方法是更好沒有非常許多信箱的小型組織想要快速地取得 Office 365 和不想要處理一些其他方法的複雜性。不過它的也有點受限於因為它應該完成中一週或更少，且因為它需要重新設定其 Outlook 設定檔的使用者。雖然次完成式遷移可以處理最多 2000 個信箱，我們強烈建議您藉由這個方法移轉的 150 信箱的最大值。如果您嘗試將多個 150 信箱遷移、 無法用盡傳輸所有的信箱在到達期限時之前, 的時間和人員可能會得到您 IT 支援被協助使用者重新設定 Outlook。</span><span class="sxs-lookup"><span data-stu-id="e1c00-p110">The cutover migration method is great for small organizations that don't have very many mailboxes, want to get to Office 365 quickly, and don't want to deal with some of the complexities of the other methods. But it's also somewhat limited because it should be completed in a week or less and because it requires users to reconfigure their Outlook profiles. While cutover migration can handle up to 2,000 mailboxes, we strongly recommend you migrate a maximum of 150 mailboxes with this method. If you try to migrate more than 150 mailboxes, you could run out of time to transfer all the mailboxes before your deadline, and your IT support staff may get overwhelmed helping users reconfigure Outlook.</span></span>
  
<span data-ttu-id="e1c00-164">如果您考慮進行一次完成式遷移，以下是一些考量的事項，請考慮：</span><span class="sxs-lookup"><span data-stu-id="e1c00-164">If you're thinking about doing a cutover migration, here are a few things to think consider:</span></span>
  
- <span data-ttu-id="e1c00-165">Office 365 必須連線至 Exchange 2010 伺服器使用 「 Outlook 無所不在 」 over TCP 連接埠 443;</span><span class="sxs-lookup"><span data-stu-id="e1c00-165">Office 365 will need to connect to your Exchange 2010 servers using Outlook Anywhere over TCP port 443;</span></span>
    
- <span data-ttu-id="e1c00-166">所有的內部部署信箱要移至 Office 365;</span><span class="sxs-lookup"><span data-stu-id="e1c00-166">All on-premises mailboxes will be moved to Office 365;</span></span>
    
- <span data-ttu-id="e1c00-167">您將需要內部部署管理員帳戶具有您的使用者信箱 ； 的內容的讀取權限</span><span class="sxs-lookup"><span data-stu-id="e1c00-167">You'll need an on-premises administrator account that has access to read the contents of your users' mailboxes;</span></span>
    
- <span data-ttu-id="e1c00-168">Exchange 2010 公認的網域想要使用的 Office 365 需要新增為服務 ； 中已驗證網域</span><span class="sxs-lookup"><span data-stu-id="e1c00-168">The Exchange 2010 accepted domains that you want to use in Office 365 need to be added as verified domains in the service;</span></span>
    
- <span data-ttu-id="e1c00-p111">之間的時間開始移轉和時開始完成階段、 Office 365 會定期同步處理 Office 365 與內部部署信箱。這可讓您完成移轉而不用擔心正在留在您的內部部署信箱 ； 電子郵件</span><span class="sxs-lookup"><span data-stu-id="e1c00-p111">Between the time you start the migration and when you begin the completion phase, Office 365 will periodically synchronize the Office 365 and on-premises mailboxes. This lets you complete the migration without worrying about email being left behind in your on-premises mailboxes;</span></span>
    
- <span data-ttu-id="e1c00-171">使用者會收到新暫時他們將需要變更登入其信箱的第一次 ； 其 Office 365 帳戶密碼</span><span class="sxs-lookup"><span data-stu-id="e1c00-171">Users will receive new temporary passwords for their Office 365 account that they'll need to change when they log in to their mailboxes for the first time;</span></span>
    
- <span data-ttu-id="e1c00-172">您將需要包含 Exchange Online 移轉 ； 每個使用者信箱的 Office 365 授權</span><span class="sxs-lookup"><span data-stu-id="e1c00-172">You'll need an Office 365 license that includes Exchange Online for each user mailbox you migrate;</span></span>
    
- <span data-ttu-id="e1c00-p112">使用者必須設定新的 Outlook 設定檔上每個裝置，然後再下載的電子郵件。將下載 Outlook 的電子郵件數量可能會有所不同。如需詳細資訊，請查看[變更多少郵件保留離線](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1)。</span><span class="sxs-lookup"><span data-stu-id="e1c00-p112">Users will need to set up a new Outlook profile on each of their devices and download their email again. The amount of email that Outlook will download can vary. For more information, take a look at [Change how much mail to keep offline](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1).</span></span>
    
<span data-ttu-id="e1c00-176">若要深入了解完全移轉，請查看：</span><span class="sxs-lookup"><span data-stu-id="e1c00-176">To learn more about cutover migration, take a look at:</span></span>
  
- [<span data-ttu-id="e1c00-177">您需要了解轉換電子郵件移轉至 Office 365</span><span class="sxs-lookup"><span data-stu-id="e1c00-177">What you need to know about a cutover email migration to Office 365</span></span>](https://support.office.com/en-us/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)
    
- [<span data-ttu-id="e1c00-178">執行轉換遷移至 Office 365 的電子郵件</span><span class="sxs-lookup"><span data-stu-id="e1c00-178">Perform a cutover migration of email to Office 365</span></span>](https://support.office.com/en-us/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)
    
#### <a name="express-migration"></a><span data-ttu-id="e1c00-179">Express 移轉</span><span class="sxs-lookup"><span data-stu-id="e1c00-179">Express migration</span></span>

<span data-ttu-id="e1c00-180">Express 移轉是其中包含您要移轉至 Office 365、 可以完成幾個星期內移轉並不需要任何進階的混合式遷移功能，例如共用空閒/忙碌行事曆資訊的一些好幾百種信箱。</span><span class="sxs-lookup"><span data-stu-id="e1c00-180">An express migration is one where you have a few hundred mailboxes that you want to migrate to Office 365, can complete the migration within a couple weeks, and don't need any of the advanced hybrid migration features like shared Free/Busy calendar information.</span></span>
  
<span data-ttu-id="e1c00-p113">Express 移轉是更好的組織需要花更多時間來將其信箱遷移至 Office 365 中，但仍要在完成幾個星期內移轉。您要取得沒有許多不同的複雜度更進階的完整的混合式移轉的一些優點。您可以控制多少，且哪一個、 信箱在指定的時間 ； 移轉Office 365 信箱將建立的使用者名稱與密碼的內部部署帳戶 ；與不同轉換遷移使用者不需要重新建立其 Outlook 設定檔。</span><span class="sxs-lookup"><span data-stu-id="e1c00-p113">Express migration is great for organizations that need to take more time to migrate their mailboxes to Office 365, but still plan to complete the migration within a couple weeks. You get some benefits of the more advanced full hybrid migration without many of the complexities. You can control how many, and which, mailboxes are migrated at a given time; Office 365 mailboxes will be created with the username and passwords of their on-premises accounts; and, unlike cutover migrations, your users won't need to recreate their Outlook profiles.</span></span>
  
<span data-ttu-id="e1c00-184">如果您需執行分段的遷移的想法，以下是要考慮的一些事項：</span><span class="sxs-lookup"><span data-stu-id="e1c00-184">If you're thinking about doing a staged migration, here are a few things to consider:</span></span>
  
- <span data-ttu-id="e1c00-185">Office 365 必須連線至 Exchange 2010 伺服器使用 「 Outlook 無所不在 」 over TCP 連接埠 443;</span><span class="sxs-lookup"><span data-stu-id="e1c00-185">Office 365 will need to connect to your Exchange 2010 servers using Outlook Anywhere over TCP port 443;</span></span>
    
- <span data-ttu-id="e1c00-186">您需要執行一次性目錄之間同步處理您的內部部署 Active Directory 伺服器和 Office 365;</span><span class="sxs-lookup"><span data-stu-id="e1c00-186">You'll need to perform a one-time directory synchronization between your on-premises Active Directory servers and Office 365;</span></span>
    
- <span data-ttu-id="e1c00-187">使用者將能夠登入 Office 365 信箱使用相同的使用者名稱和密碼時使用他們的信箱已移轉;</span><span class="sxs-lookup"><span data-stu-id="e1c00-187">Users will be able to log in to their Office 365 mailbox using the same username and password they were using when their mailbox was migrated;</span></span>
    
- <span data-ttu-id="e1c00-188">您將需要包含 Exchange Online 移轉 ； 每個使用者信箱的 Office 365 授權</span><span class="sxs-lookup"><span data-stu-id="e1c00-188">You'll need an Office 365 license that includes Exchange Online for each user mailbox you migrate;</span></span>
    
- <span data-ttu-id="e1c00-189">使用者不需要設定新的 Outlook 設定檔在大部分的裝置 （一些較舊的 Android 電話可能會需要新的設定檔） 並不需要重新下載電子郵件。</span><span class="sxs-lookup"><span data-stu-id="e1c00-189">Users don't need to set up a new Outlook profile on most of their devices (some older Android phones might need a new profile) and won't need to re-download their email.</span></span>
    
<span data-ttu-id="e1c00-190">若要深入了解分段遷移，仔細[快速移轉 Exchange 信箱移轉至 Office 365 使用最少的混合式](https://support.office.com/article/Use-Minimal-Hybrid-to-quickly-migrate-Exchange-mailboxes-to-Office-365-fdecceed-0702-4af3-85be-f2a0013937ef)</span><span class="sxs-lookup"><span data-stu-id="e1c00-190">To learn more about staged migration, take a look at [Use Minimal Hybrid to quickly migrate Exchange mailboxes to Office 365](https://support.office.com/article/Use-Minimal-Hybrid-to-quickly-migrate-Exchange-mailboxes-to-Office-365-fdecceed-0702-4af3-85be-f2a0013937ef)</span></span>
  
#### <a name="full-hybrid"></a><span data-ttu-id="e1c00-191">完整的混合式</span><span class="sxs-lookup"><span data-stu-id="e1c00-191">Full hybrid</span></span>

<span data-ttu-id="e1c00-p114">完整的混合式遷移是一個其中您的組織有許多百，最多個數萬個、 信箱，而您想要移至 Office 365 的部分或所有這些。因為這些移轉通常長期、 混合移轉可讓您可以：</span><span class="sxs-lookup"><span data-stu-id="e1c00-p114">A full hybrid migration is one where your organization has many hundreds, up to tens of thousands, of mailboxes and you want to move some or all of them to Office 365. Because these migrations are typically longer-term, hybrid migrations make it possible to:</span></span>
  
- <span data-ttu-id="e1c00-194">Office 365 中顯示內部使用者之使用者的空閒/忙碌行事曆資訊，反之亦然;</span><span class="sxs-lookup"><span data-stu-id="e1c00-194">Show on-premises users the free/busy calendar information for users in Office 365, and vice versa;</span></span>
    
- <span data-ttu-id="e1c00-195">請參閱包含在內部部署和 Office 365; 中的收件者的整合全域通訊清單</span><span class="sxs-lookup"><span data-stu-id="e1c00-195">See a unified global address list that contains recipients in both on-premises and Office 365;</span></span>
    
- <span data-ttu-id="e1c00-196">檢視完整的 Outlook 收件者卡不論它們是否是在內部或 Office 365; 中的所有使用者</span><span class="sxs-lookup"><span data-stu-id="e1c00-196">View full Outlook recipient cards for all users, regardless of whether they're on-premises or in Office 365;</span></span>
    
- <span data-ttu-id="e1c00-197">在內部部署 Exchange 伺服器與 Office 365 使用 TLS 和憑證 ； 之間的安全的電子郵件通訊</span><span class="sxs-lookup"><span data-stu-id="e1c00-197">Secure email communication between on-premises Exchange servers and Office 365 using TLS and certificates;</span></span>
    
- <span data-ttu-id="e1c00-198">將傳送的郵件在內部部署 Exchange 伺服器和 Office 365 之間作為內部，讓：</span><span class="sxs-lookup"><span data-stu-id="e1c00-198">Treat messages sent between on-premises Exchange servers and Office 365 as internal, enabling them to:</span></span>
    
  - <span data-ttu-id="e1c00-199">適當評估並處理目標 ； 的內部郵件的傳輸和規範代理程式</span><span class="sxs-lookup"><span data-stu-id="e1c00-199">Be properly evaluated and processed by transport and compliance agents targeting internal messages;</span></span>
    
  - <span data-ttu-id="e1c00-200">略過反垃圾郵件篩選器。</span><span class="sxs-lookup"><span data-stu-id="e1c00-200">Bypass anti-spam filters.</span></span>
    
<span data-ttu-id="e1c00-p115">完整的混合式遷移是最適合的預計會保持在多個月或更多的混合式組態的組織。您將取得稍早在本節中，加上目錄同步處理、 較佳的整合式的符合性功能和能夠將信箱移到與 Office 365 所列的功能使用線上信箱移動。Office 365 會變成在內部部署組織的副檔名。</span><span class="sxs-lookup"><span data-stu-id="e1c00-p115">Full hybrid migrations are best for organizations that expect to stay in a hybrid configuration for many months or more. You'll get the features listed earlier in this section, plus directory synchronization, better integrated compliance features, and the ability to move mailboxes to and from Office 365 using online mailbox moves. Office 365 becomes an extension of your on-premises organization.</span></span>
  
<span data-ttu-id="e1c00-204">如果您考慮進行完整的混合式遷移，以下是要考慮的一些事項：</span><span class="sxs-lookup"><span data-stu-id="e1c00-204">If you're thinking about doing a full hybrid migration, here are a few things to consider:</span></span>
  
- <span data-ttu-id="e1c00-p116">完整的混合式遷移並不適合組織的所有類型。完整的混合式遷移的複雜性，因為具有小於一些好幾百種信箱組織看不到通常 justify 人力和一個設定所需的成本的優點。若此聲音您的組織，強烈建議您改用; 考慮 Cutover 或分段移轉</span><span class="sxs-lookup"><span data-stu-id="e1c00-p116">Full hybrid migrations aren't suited to all types of organizations. Due to the complexity of full hybrid migrations, organizations with less than a few hundred mailboxes don't typically see benefits that justify the effort and cost needed to set one up. If this sounds like your organization, we strongly recommend that you consider Cutover or Staged migrations instead;</span></span>
    
- <span data-ttu-id="e1c00-208">Office 365 必須連線到 Exchange 2010 伺服器使用 「 Outlook 無所不在 」 over TCP 連接埠 443;</span><span class="sxs-lookup"><span data-stu-id="e1c00-208">Office 365 will need to connect to an Exchange 2010 server using Outlook Anywhere over TCP port 443;</span></span>
    
- <span data-ttu-id="e1c00-209">您需要設定目錄同步處理內部部署 Active Directory 伺服器與 Office 365; 之間使用 Azure Active Directory 連線 (AADConnect)</span><span class="sxs-lookup"><span data-stu-id="e1c00-209">You'll need to set up directory synchronization using Azure Active Directory Connect (AADConnect) between your on-premises Active Directory servers and Office 365;</span></span>
    
- <span data-ttu-id="e1c00-210">使用者將能夠登入 Office 365 信箱使用相同的使用者名稱和密碼時登入區域網路 （需要 Azure [Active Directory 連線使用密碼同步處理及/或 Active Directory Federation Services）;</span><span class="sxs-lookup"><span data-stu-id="e1c00-210">Users will be able to log in to their Office 365 mailbox using the same username and password they use when they log into the local network (requires Azure Active Directory Connect with password synchronization and/or Active Directory Federation Services);</span></span>
    
- <span data-ttu-id="e1c00-211">您將需要包含 Exchange Online 移轉 ； 每個使用者信箱的 Office 365 授權</span><span class="sxs-lookup"><span data-stu-id="e1c00-211">You'll need an Office 365 license that includes Exchange Online for each user mailbox you migrate;</span></span>
    
- <span data-ttu-id="e1c00-212">使用者不需要設定新的 Outlook 設定檔在大部分的裝置 （一些較舊的 Android 電話可能會需要新的設定檔） 並不需要重新下載電子郵件。</span><span class="sxs-lookup"><span data-stu-id="e1c00-212">Users don't need to set up a new Outlook profile on most of their devices (some older Android phones might need a new profile) and won't need to re-download their email.</span></span>
    
<span data-ttu-id="e1c00-213">如果完整的混合式遷移聲音適合您仔細下列資源以協助您進行移轉：</span><span class="sxs-lookup"><span data-stu-id="e1c00-213">If a full hybrid migration sounds right for you, take a look at the following resources to help you with your migration:</span></span>
  
- [<span data-ttu-id="e1c00-214">Exchange server 部署助理</span><span class="sxs-lookup"><span data-stu-id="e1c00-214">Exchange Deployment Assistant</span></span>](https://aka.ms/exdeploy)
    
- [<span data-ttu-id="e1c00-215">Exchange Server 混合部署</span><span class="sxs-lookup"><span data-stu-id="e1c00-215">Exchange Server Hybrid Deployments</span></span>](https://technet.microsoft.com/en-us/library/jj200581%28v=exchg.150%29.aspx)
    
- [<span data-ttu-id="e1c00-216">混合組態精靈</span><span class="sxs-lookup"><span data-stu-id="e1c00-216">Hybrid Configuration wizard</span></span>](https://technet.microsoft.com/en-us/library/hh529921%28v=exchg.150%29.aspx)
    
- [<span data-ttu-id="e1c00-217">混合組態精靈常見問題集</span><span class="sxs-lookup"><span data-stu-id="e1c00-217">Hybrid Configuration wizard FAQs</span></span>](https://technet.microsoft.com/en-us/library/mt488940%28v=exchg.150%29.aspx)
    
- [<span data-ttu-id="e1c00-218">混合式部署必要條件</span><span class="sxs-lookup"><span data-stu-id="e1c00-218">Hybrid deployment prerequisites</span></span>](https://technet.microsoft.com/en-us/library/hh534377%28v=exchg.150%29.aspx)
    
### <a name="migrate-to-a-newer-version-of-exchange-server"></a><span data-ttu-id="e1c00-219">移轉至新版 Exchange Server</span><span class="sxs-lookup"><span data-stu-id="e1c00-219">Migrate to a newer version of Exchange Server</span></span>

<span data-ttu-id="e1c00-p117">當我們強烈相信您可透過移轉至 Office 365 來獲得最佳的值與使用者經驗時，我們也瞭解某些組織需要保留其電子郵件的內部。這可能是因為法規需求、 以保證資料不儲存在資料中心位於另一個國家/地區，依此類推。如果您選擇要保留電子郵件內部，您可以移轉至 Exchange 2013 或 Exchange 2016 的 Exchange 2010 環境。</span><span class="sxs-lookup"><span data-stu-id="e1c00-p117">While we strongly believe that you can achieve the best value and user experience by migrating to Office 365, we also understand that some organizations need to keep their email on-premises. This could be because of regulatory requirements, to guarantee data isn't stored in a datacenter located in another country, and so on. If you choose to keep your email on-premises, you can migrate your Exchange 2010 environment to Exchange 2013 or Exchange 2016.</span></span>
  
<span data-ttu-id="e1c00-p118">我們建議您先移轉至 Exchange 2016 如果無法移轉至 Office 365。Exchange 2016 包含所有的功能和改進隨附於舊版的 Exchange 和其最符合適用 Office 365 的經驗 （雖然某些功能只適用於 Office 365）。查看只是一些您已被錯過的事項：</span><span class="sxs-lookup"><span data-stu-id="e1c00-p118">We recommend that you migrate to Exchange 2016 if you can't migrate to Office 365. Exchange 2016 includes all the features and advancements included with previous releases of Exchange, and it most closely matches the experience available with Office 365 (although some features are available only in Office 365). Check out just a few of the things you've been missing out on:</span></span>
  
|<span data-ttu-id="e1c00-226">**Exchange 版本**</span><span class="sxs-lookup"><span data-stu-id="e1c00-226">**Exchange release**</span></span>|<span data-ttu-id="e1c00-227">**功能**</span><span class="sxs-lookup"><span data-stu-id="e1c00-227">**Features**</span></span>|
|:-----|:-----|
|<span data-ttu-id="e1c00-228">Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="e1c00-228">Exchange 2013</span></span>  <br/> | <span data-ttu-id="e1c00-229">簡化的架構三降低伺服器角色的數字 (Mailbox、 Client Access Edge Transport)</span><span class="sxs-lookup"><span data-stu-id="e1c00-229">Simplified architecture reducing the number of server roles to three (Mailbox, Client Access, Edge Transport)</span></span>  <br/>  <span data-ttu-id="e1c00-230">資料外洩防護原則 (DLP) 協助保護機密資訊洩漏</span><span class="sxs-lookup"><span data-stu-id="e1c00-230">Data loss prevention policies (DLP) that help keep sensitive information from leaking</span></span>  <br/>  <span data-ttu-id="e1c00-231">大幅改善的 Outlook Web App 功能</span><span class="sxs-lookup"><span data-stu-id="e1c00-231">Significantly improved Outlook Web App Experience</span></span>  <br/> |
|<span data-ttu-id="e1c00-232">Exchange 2016</span><span class="sxs-lookup"><span data-stu-id="e1c00-232">Exchange 2016</span></span>  <br/> | <span data-ttu-id="e1c00-233">*從 Exchange 2013 的功能和...]*</span><span class="sxs-lookup"><span data-stu-id="e1c00-233">*Features from Exchange 2013 and…*</span></span>  <br/>  <span data-ttu-id="e1c00-234">進一步剛信箱及 Edge Transport 簡化的伺服器角色</span><span class="sxs-lookup"><span data-stu-id="e1c00-234">Further simplified server roles to just Mailbox and Edge Transport</span></span>  <br/>  <span data-ttu-id="e1c00-235">改善的 DLP 整合及與 SharePoint</span><span class="sxs-lookup"><span data-stu-id="e1c00-235">Improved DLP along with integration with SharePoint</span></span>  <br/>  <span data-ttu-id="e1c00-236">改良的資料庫台回復性</span><span class="sxs-lookup"><span data-stu-id="e1c00-236">Improved database resilience</span></span>  <br/>  <span data-ttu-id="e1c00-237">線上文件共同作業</span><span class="sxs-lookup"><span data-stu-id="e1c00-237">Online document collaboration</span></span>  <br/> |
   
#### <a name="which-version-should-i-migrate-to"></a><span data-ttu-id="e1c00-238">若要應移轉版本？</span><span class="sxs-lookup"><span data-stu-id="e1c00-238">Which version should I migrate to?</span></span>

<span data-ttu-id="e1c00-p119">我們建議您一開始假設您要移轉至 Exchange 2016。然後，使用下列資訊以確認您假設或出 Exchange 2016 規則。如果您無法移轉至 Exchange 2016 原因之一或另一個，執行相同程序與 Exchange 2013 等等。</span><span class="sxs-lookup"><span data-stu-id="e1c00-p119">We recommend that you initially assume that you'll migrate to Exchange 2016. Then, use the following information to confirm your assumption or to rule out Exchange 2016. If you can't migrate to Exchange 2016 for one reason or another, do the same process with Exchange 2013, and so on.</span></span>
  
|<span data-ttu-id="e1c00-242">**考量**</span><span class="sxs-lookup"><span data-stu-id="e1c00-242">**Consideration**</span></span>|<span data-ttu-id="e1c00-243">**其他資訊**</span><span class="sxs-lookup"><span data-stu-id="e1c00-243">**More Info**</span></span>|
|:-----|:-----|
|<span data-ttu-id="e1c00-244">支援日期的結尾</span><span class="sxs-lookup"><span data-stu-id="e1c00-244">End of support dates</span></span>  <br/> | <span data-ttu-id="e1c00-245">類似 Exchange 2010，每個版本的 Exchange 會有其專屬結尾支援日期：</span><span class="sxs-lookup"><span data-stu-id="e1c00-245">Like Exchange 2010, each version of Exchange has its own end of support date:</span></span>  <br/> <span data-ttu-id="e1c00-246">**Exchange 2013**年 4 月 2023</span><span class="sxs-lookup"><span data-stu-id="e1c00-246">**Exchange 2013** - April 2023</span></span>  <br/> <span data-ttu-id="e1c00-247">**Exchange 2016**年 10 月 2025</span><span class="sxs-lookup"><span data-stu-id="e1c00-247">**Exchange 2016** - October 2025</span></span>  <br/>  <span data-ttu-id="e1c00-p120">稍早結尾的支援日期、 更快您需要執行其他移轉。4 月 2023年會比您想像的還很接近 ！</span><span class="sxs-lookup"><span data-stu-id="e1c00-p120">The earlier the end of support date, the sooner you'll need to perform another migration. April 2023 is a lot closer than you think!  </span></span><br/> |
|<span data-ttu-id="e1c00-250">Exchange 2013 或 2016年的移轉路徑</span><span class="sxs-lookup"><span data-stu-id="e1c00-250">Migration path to Exchange 2013 or 2016</span></span>  <br/> |<span data-ttu-id="e1c00-251">以下是移轉至 Exchange 2013 的一般階段：</span><span class="sxs-lookup"><span data-stu-id="e1c00-251">Here are the general phases for migrating to Exchange 2013:</span></span>  <br/> <span data-ttu-id="e1c00-252">安裝 Exchange 2013 或 2016年至現有的 Exchange 2010 組織移動服務與 Exchange 2013 或 2016年移動信箱的其他基礎結構與公用資料夾遷移至 Exchange 2013 或 2016年解除委任剩餘的 Exchange 2010 伺服器</span><span class="sxs-lookup"><span data-stu-id="e1c00-252">Install Exchange 2013 or 2016 into your existing Exchange 2010 organization Move services and other infrastructure to Exchange 2013 or 2016 Move mailboxes and public folders to Exchange 2013 or 2016 Decommission remaining Exchange 2010 servers</span></span> |
|<span data-ttu-id="e1c00-253">版本共存</span><span class="sxs-lookup"><span data-stu-id="e1c00-253">Version coexistence</span></span>  <br/> |<span data-ttu-id="e1c00-p121">移轉至 Exchange 2013 或 Exchange 2016 時，您可以安裝到現有的 Exchange 2010 組織的其中一個版本。這可讓您安裝一或多個 Exchange 2013 或 Exchange 2016 伺服器以及執行移轉。</span><span class="sxs-lookup"><span data-stu-id="e1c00-p121">When migrating to Exchange 2013 or Exchange 2016, you can install either version into an existing Exchange 2010 organization. This enables you to install one or more Exchange 2013 or Exchange 2016 servers and perform your migration.</span></span>  <br/> |
|<span data-ttu-id="e1c00-256">伺服器硬體</span><span class="sxs-lookup"><span data-stu-id="e1c00-256">Server hardware</span></span>  <br/> | <span data-ttu-id="e1c00-p122">伺服器硬體需求已從 Exchange 2010 變更。您將需要確定您要使用的硬體相容。您可以找到更多有關以下每個版本的硬體需求：</span><span class="sxs-lookup"><span data-stu-id="e1c00-p122">Server hardware requirements have changed from Exchange 2010. You'll need to make sure the hardware you're going to use is compatible. You can find out more about hardware requirements for each version here:  </span></span><br/> [<span data-ttu-id="e1c00-260">Exchange 2016 系統需求</span><span class="sxs-lookup"><span data-stu-id="e1c00-260">Exchange 2016 System Requirements</span></span>](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx) <br/> [<span data-ttu-id="e1c00-261">Exchange 2013 系統需求</span><span class="sxs-lookup"><span data-stu-id="e1c00-261">Exchange 2013 System Requirements</span></span>](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx) <br/>  <span data-ttu-id="e1c00-262">您可以找到大幅改善 Exchange 效能與運算動力和較新的伺服器中的儲存容量，您可能需要較少的伺服器可支援相同的信箱數目。</span><span class="sxs-lookup"><span data-stu-id="e1c00-262">You'll find that with the significant improvements in Exchange performance, and the increased computing power and storage capacity in newer servers, you'll likely need fewer servers to support the same number of mailboxes.</span></span>  <br/> |
|<span data-ttu-id="e1c00-263">作業系統版本</span><span class="sxs-lookup"><span data-stu-id="e1c00-263">Operating system version</span></span>  <br/> | <span data-ttu-id="e1c00-264">每個版本的最小支援的作業系統版本是：</span><span class="sxs-lookup"><span data-stu-id="e1c00-264">The minimum supported operating system versions for each version are:</span></span>  <br/> <span data-ttu-id="e1c00-265">**Exchange 2016**Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="e1c00-265">**Exchange 2016** Windows Server 2012</span></span>  <br/> <span data-ttu-id="e1c00-266">**Exchange 2013**Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="e1c00-266">**Exchange 2013** Windows Server 2008 R2 SP1</span></span>  <br/>  <span data-ttu-id="e1c00-267">您可以在[Exchange 支援性一覽表](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx)尋找作業系統支援的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e1c00-267">You can find more information about operating system support at [Exchange Supportability Matrix](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).</span></span>  <br/> |
|<span data-ttu-id="e1c00-268">Active Directory 樹系功能等級</span><span class="sxs-lookup"><span data-stu-id="e1c00-268">Active Directory forest functional level</span></span>  <br/> | <span data-ttu-id="e1c00-269">基本支援 Active Directory 樹系功能等級每個版本是：</span><span class="sxs-lookup"><span data-stu-id="e1c00-269">The minimum supported Active Directory forest functional levels for each version are:</span></span>  <br/> <span data-ttu-id="e1c00-270">**Exchange 2016**Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="e1c00-270">**Exchange 2016** Windows Server 2008 R2 SP1</span></span>  <br/> <span data-ttu-id="e1c00-271">**Exchange 2013**Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="e1c00-271">**Exchange 2013** Windows Server 2003</span></span>  <br/>  <span data-ttu-id="e1c00-272">您可以在[Exchange 支援性一覽表](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx)尋找樹系功能層級支援的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e1c00-272">You can find more information about forest functional level support at [Exchange Supportability Matrix](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).</span></span>  <br/> |
|<span data-ttu-id="e1c00-273">Office 用戶端版本</span><span class="sxs-lookup"><span data-stu-id="e1c00-273">Office client versions</span></span>  <br/> | <span data-ttu-id="e1c00-274">每個版本的最小支援的 Office 用戶端版本是：</span><span class="sxs-lookup"><span data-stu-id="e1c00-274">The minimum supported Office client versions for each version are:</span></span>  <br/> <span data-ttu-id="e1c00-275">**Exchange 2016**Office 2010 （含最新的更新）</span><span class="sxs-lookup"><span data-stu-id="e1c00-275">**Exchange 2016** Office 2010 (with the latest updates)</span></span>  <br/> <span data-ttu-id="e1c00-276">**Exchange 2013**Office 2007 SP3</span><span class="sxs-lookup"><span data-stu-id="e1c00-276">**Exchange 2013** Office 2007 SP3</span></span>  <br/>  <span data-ttu-id="e1c00-277">您可以在[Exchange 支援性一覽表](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx)尋找 Office 用戶端支援的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e1c00-277">You can find more information about Office client support at [Exchange Supportability Matrix](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).</span></span>  <br/> |
   
#### <a name="how-do-i-migrate"></a><span data-ttu-id="e1c00-278">我該如何移轉？</span><span class="sxs-lookup"><span data-stu-id="e1c00-278">How do I migrate?</span></span>

<span data-ttu-id="e1c00-279">如果您已決定您要保留電子郵件內部，您可以使用下列資源以協助您進行移轉：</span><span class="sxs-lookup"><span data-stu-id="e1c00-279">If you've decided that you want to keep your email on-premises, you can use the following resources to help you with your migration:</span></span>
  
- [<span data-ttu-id="e1c00-280">Exchange server 部署助理</span><span class="sxs-lookup"><span data-stu-id="e1c00-280">Exchange Deployment Assistant</span></span>](https://aka.ms/exdeploy)
    
- <span data-ttu-id="e1c00-281">Exchange [2016年](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.160%29.aspx)、 [2013年](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.150%29.aspx)的 active Directory 架構變更</span><span class="sxs-lookup"><span data-stu-id="e1c00-281">Active Directory schema changes for Exchange [2016](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.150%29.aspx)</span></span>
    
- <span data-ttu-id="e1c00-282">Exchange [2016年](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx)、 [2013年](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx)的系統需求</span><span class="sxs-lookup"><span data-stu-id="e1c00-282">System requirements for Exchange [2016](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx)</span></span>
    
- <span data-ttu-id="e1c00-283">Exchange [2016年](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.160%29.aspx)、 [2013年](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.150%29.aspx)的必要條件</span><span class="sxs-lookup"><span data-stu-id="e1c00-283">Prerequisites for Exchange [2016](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.150%29.aspx)</span></span>
    
## <a name="what-if-i-need-help"></a><span data-ttu-id="e1c00-284">如果我需要說明嗎？</span><span class="sxs-lookup"><span data-stu-id="e1c00-284">What if I need help?</span></span>

<span data-ttu-id="e1c00-p123">如果您要移轉至 Office 365，您可能會是合格使用我們 Microsoft FastTrack 服務。FastTrack 提供最佳作法、 工具及資源以提升移轉至 Office 365 儘可能以一致。最適合所有，您必須實際支援工程師將會帶領您完成移轉，從規劃及設計到您的最後一個信箱移轉。如果您想要更了解 FastTrack，仔細[Microsoft FastTrack](https://fasttrack.microsoft.com/)。</span><span class="sxs-lookup"><span data-stu-id="e1c00-p123">If you're migrating to Office 365, you might be eligible to use our Microsoft FastTrack service. FastTrack provides best practices, tools, and resources to make your migration to Office 365 as seamless as possible. Best of all, you'll have a real support engineer that will walk you through your migration, from planning and design all the way to migrating your last mailbox. If you want to know more about FastTrack, take a look at [Microsoft FastTrack](https://fasttrack.microsoft.com/).</span></span>
  
<span data-ttu-id="e1c00-p124">如果您將任何問題期間執行移轉至 Office 365，您不使用 FastTrack 或移轉至新版 Exchange Server 在此為您服務協助。以下是一些您可以使用的資源：</span><span class="sxs-lookup"><span data-stu-id="e1c00-p124">If you run into any problems during your migration to Office 365 and you aren't using FastTrack, or your migration to a newer version of Exchange Server, we're here to help. Here are some resources you can use:</span></span>
  
- [<span data-ttu-id="e1c00-291">技術社群</span><span class="sxs-lookup"><span data-stu-id="e1c00-291">Technical community</span></span>](https://social.technet.microsoft.com/Forums/office/en-US/home?category=exchangeserver)
    
- [<span data-ttu-id="e1c00-292">客戶支援</span><span class="sxs-lookup"><span data-stu-id="e1c00-292">Customer support</span></span>](https://support.microsoft.com/en-us/gp/support-options-for-business)
    
## <a name="related-topics"></a><span data-ttu-id="e1c00-293">相關主題</span><span class="sxs-lookup"><span data-stu-id="e1c00-293">Related topics</span></span>

[<span data-ttu-id="e1c00-294">可協助您升級從 Office 2010 伺服器和用戶端的資源</span><span class="sxs-lookup"><span data-stu-id="e1c00-294">Resources to help you upgrade from Office 2010 servers and clients</span></span>](upgrade-from-office-2010-servers-and-products.md)
  
[<span data-ttu-id="e1c00-295">Office 退休群組 （Microsoft 技術社群）</span><span class="sxs-lookup"><span data-stu-id="e1c00-295">Office Retirement Group (Microsoft Tech Community)</span></span>](https://go.microsoft.com/fwlink/?linkid=842065)
  

