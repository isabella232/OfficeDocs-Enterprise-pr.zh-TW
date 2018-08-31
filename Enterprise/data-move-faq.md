---
title: 資料移動一般常見問題集
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 9/14/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 1f01bc6f-5d37-4d14-bdd3-9d94a1e23e14
description: 以下是對一般問題的回答關於將核心資料移至新的資料中心地理位置。
ms.openlocfilehash: 40f83ee94aaa7c919f08d91d888ff131da02df67
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540096"
---
# <a name="data-move-general-faq"></a><span data-ttu-id="2f3ae-103">資料移動一般常見問題集</span><span class="sxs-lookup"><span data-stu-id="2f3ae-103">Data move general FAQ</span></span>

<span data-ttu-id="2f3ae-104">以下是對一般問題的回答關於將核心資料移至新的資料中心地理位置。</span><span class="sxs-lookup"><span data-stu-id="2f3ae-104">Here are answers to general questions about moving core data to a new datacenter geo.</span></span>
  
 <span data-ttu-id="2f3ae-105">**問： 如何您確定 「 我的客戶資料移動期間的安全且我將不會遇到的停機時間？**</span><span class="sxs-lookup"><span data-stu-id="2f3ae-105">**Q. How do you make sure my customer data is safe during the move and that I won't experience downtime?**</span></span>
  
<span data-ttu-id="2f3ae-p101">A.資料移動是以使用者影響最小的後端服務作業。[期間和之後資料移動](during-and-after-your-data-move.md)列出可以受影響的功能。我們將遵守[Microsoft Online Services 服務層級協議 (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897)可用性讓沒有客戶需要準備或移動作業期間監視。</span><span class="sxs-lookup"><span data-stu-id="2f3ae-p101">A. Data moves are a back-end service operation with minimal impact to end-users. Features that can be impacted are listed in [During and after your data move](during-and-after-your-data-move.md). We adhere to the [Microsoft Online Services Service Level Agreement (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897) for availability so there is nothing that customers need to prepare for or to monitor during the move.</span></span> 
  
<span data-ttu-id="2f3ae-p102">所有 Office 365 服務會都執行相同的版本的資料中心，因此您可以確保的一致的功能。您的服務已完全支援整個程序。</span><span class="sxs-lookup"><span data-stu-id="2f3ae-p102">All Office 365 services run the same versions in the datacenters, so you can be assured of consistent functionality. Your service is fully supported throughout the process.</span></span>
  
 <span data-ttu-id="2f3ae-112">**問都位於不同 geos 的不同服務的影響為何？**</span><span class="sxs-lookup"><span data-stu-id="2f3ae-112">**Q. What is the impact of having different services located in different geos?**</span></span>
  
<span data-ttu-id="2f3ae-p103">A.的一些現有的客戶和中間移動程序的客戶，可能位於 Office 365 服務的部分不同 geos。我們服務執行獨立彼此並沒有任何使用者的影響如果是這樣。</span><span class="sxs-lookup"><span data-stu-id="2f3ae-p103">A. For some existing customers and customers in the middle of the move process, some of the Office 365 services may be located in different geos. Our services run independently of each other and there is no user impact if this is the case.</span></span>
  
 <span data-ttu-id="2f3ae-116">**問將新的 Office 365 客戶可自動佈建在新的資料中心 geos 吗？**</span><span class="sxs-lookup"><span data-stu-id="2f3ae-116">**Q. Will new Office 365 customers be automatically provisioned in the new datacenter geos?**</span></span>
  
<span data-ttu-id="2f3ae-p104">A.[是]。一旦提供新的資料中心地理位置，作為其國家選取適合新的地理位置國家期間註冊的企業客戶的新 Office 365 必須裝載於新的資料中心地理其核心資料。</span><span class="sxs-lookup"><span data-stu-id="2f3ae-p104">A. Yes. Once a new datacenter geo is available, new Office 365 for business customers who select a country eligible for the new geo as their country during sign-up will have their core data hosted in the new datacenter geo.</span></span>
  
 <span data-ttu-id="2f3ae-120">**問其中是 [我的資料位於？**</span><span class="sxs-lookup"><span data-stu-id="2f3ae-120">**Q. Where is my data is located?**</span></span>
  
<span data-ttu-id="2f3ae-p105">我們將發佈的資料中心 geos、 資料中心和位置上的[Office 365 互動式資料中心對應](https://o365datacentermap.azurewebsites.net)的客戶資料的位置。2010 年 8 月 1 日到您將能夠確認透過您的組織設定檔 Office 365 系統管理中心的 [資料位置] 區段的靜態客戶資料的位置。</span><span class="sxs-lookup"><span data-stu-id="2f3ae-p105">We publish the location of datacenter geos, datacenters, and location of customer data on the [ Office 365 interactive datacenter maps ](https://o365datacentermap.azurewebsites.net). As of August 1, you will be able to verify the location of your customer data at rest via the Data Location section under your Organization Profile in the Office 365 Admin Center.</span></span>
  
 <span data-ttu-id="2f3ae-123">**問現有的 Office 365 客戶要移至新的資料中心 geos 吗？**</span><span class="sxs-lookup"><span data-stu-id="2f3ae-123">**Q. Will existing Office 365 customers be moved to the new datacenter geos?**</span></span>
  
<span data-ttu-id="2f3ae-p106">A.合格的 Office 365 客戶可以請求已移至新的 geos 其核心資料。客戶必須以參與送出要求之前其地理位置的期限。</span><span class="sxs-lookup"><span data-stu-id="2f3ae-p106">A. Eligible Office 365 customers can request to have their core data moved to the new geos. Customers will need to submit a request before the deadline for their geo in order to participate.</span></span> 
  
 <span data-ttu-id="2f3ae-127">**問哪些客戶是合格要求的移動？**</span><span class="sxs-lookup"><span data-stu-id="2f3ae-127">**Q. What customers are eligible to request a move?**</span></span>
  
<span data-ttu-id="2f3ae-p107">A.現有的 Office 365 選取適合新的資料中心地理國家/地區的商業客戶可以要求移動。</span><span class="sxs-lookup"><span data-stu-id="2f3ae-p107">A. Existing Office 365 commercial customers who selected a country eligible for the new datacenter geo will be able to request a move.</span></span> 
  
 <span data-ttu-id="2f3ae-130">**問時將我可以要求的移動？**</span><span class="sxs-lookup"><span data-stu-id="2f3ae-130">**Q. When will I be able to request a move?**</span></span>
  
<span data-ttu-id="2f3ae-p108">A.要求期間將宣佈[如何要求資料移動](request-your-data-move.md)頁面上。</span><span class="sxs-lookup"><span data-stu-id="2f3ae-p108">A. The request period will be announced on the [How to request your data move](request-your-data-move.md) page.</span></span> 
  
 <span data-ttu-id="2f3ae-133">**問如何要求要移動？**</span><span class="sxs-lookup"><span data-stu-id="2f3ae-133">**Q. How can I request to be moved?**</span></span>
  
<span data-ttu-id="2f3ae-p109">A.合格的客戶會看到其[Office 365 系統管理入口網站](https://portal.office.com/)中的頁面。請參閱[How to 要求資料移動](request-your-data-move.md)如需如何移動要求的指示。</span><span class="sxs-lookup"><span data-stu-id="2f3ae-p109">A. Eligible customers will see a page in their [Office 365 Admin Portal](https://portal.office.com/). Please see [How to request your data move](request-your-data-move.md) for instructions on how to request a move.</span></span> 
  
 <span data-ttu-id="2f3ae-137">**問變更我要求移動後的選取項目吗？**</span><span class="sxs-lookup"><span data-stu-id="2f3ae-137">**Q. Can I change my selection after requesting a move?**</span></span>
  
<span data-ttu-id="2f3ae-p110">A.它即無法再利用之後，移除您程序提交您的要求。</span><span class="sxs-lookup"><span data-stu-id="2f3ae-p110">A. It is not possible for us to remove you from the process after you submit your request.</span></span>
  
 <span data-ttu-id="2f3ae-140">**問什麼事不要求之前期限的移動？**</span><span class="sxs-lookup"><span data-stu-id="2f3ae-140">**Q. What happens if I do not request a move before the deadline?**</span></span>
  
<span data-ttu-id="2f3ae-p111">A.我們目前無法接受要移動的每個地理期限之後的要求。</span><span class="sxs-lookup"><span data-stu-id="2f3ae-p111">A. We are unable to accept requests to be moved after the deadline in each geo.</span></span>
  
 <span data-ttu-id="2f3ae-143">**問怎麼辦？ 若要取得較佳的網路效能移動 「 我的資料**</span><span class="sxs-lookup"><span data-stu-id="2f3ae-143">**Q. What if I want to move my data in order to get better network performance?**</span></span>
  
<span data-ttu-id="2f3ae-p112">正在接近 Office 365 datacenter 位置並不保證郵件的較佳的網路效能。有許多因素及影響使用者和 Office 365 服務之間的網路效能的元件。如需有關此資訊和效能調整請參閱[網路規劃和 Office 365 的效能調整](network-planning-and-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="2f3ae-p112">Being close to an Office 365 datacenter is not a guarantee for a better networking performance. There are many factors and components that impact the network performance between the end user and the Office 365 service. For more information about this and performance tuning see [Network planning and performance tuning for Office 365](network-planning-and-performance.md).</span></span>
  
 <span data-ttu-id="2f3ae-147">**問： 所有服務不要在同一天都移動其資料吗？**</span><span class="sxs-lookup"><span data-stu-id="2f3ae-147">**Q. Do all the services move their data on the same day?**</span></span>
  
<span data-ttu-id="2f3ae-p113">A.服務不會同時移動自己的資料。每項服務分別移並在不同時間可能會移動自己的資料。</span><span class="sxs-lookup"><span data-stu-id="2f3ae-p113">A. The services do not move their data at the same time. Each service will move independently and will likely move their data at different times.</span></span>
  
 <span data-ttu-id="2f3ae-151">**問可以選擇當我想要移動我資料？**</span><span class="sxs-lookup"><span data-stu-id="2f3ae-151">**Q. Can I choose when I want my data to be moved?**</span></span>
  
<span data-ttu-id="2f3ae-p114">A.客戶不能夠選取特定日期、 他們無法延遲其移動，且我們無法共用的特定日期或時間範圍內移動。</span><span class="sxs-lookup"><span data-stu-id="2f3ae-p114">A. Customers are not able to select a specific date, they cannot delay their move, and we cannot share a specific date or timeframe for the moves.</span></span>
  
 <span data-ttu-id="2f3ae-154">**問您可以共用時將會移動 「 我的資料？**</span><span class="sxs-lookup"><span data-stu-id="2f3ae-154">**Q. Can you share when my data will be be moved?**</span></span>
  
<span data-ttu-id="2f3ae-p115">A.資料移動是以使用者影響最小的後端作業。複雜性、 整數和小我們需要在執行全域操作及自動化環境內的資料移動禁止我們共用時的資料移動預期完成您的租用戶或任何其他單一租用戶。客戶會收到一個確認訊息中心中每一個參與服務時已完成其資料移動。</span><span class="sxs-lookup"><span data-stu-id="2f3ae-p115">A. Data moves are a back-end operation with minimal impact to end-users. The complexity, precision and scale at which we need to perform data moves within a globally operated and automated environment prohibit us from sharing when a data move is expected to complete for your tenant or any other single tenant. Customers will receive one confirmation in Message Center per participating service when its data move has completed.</span></span> 
  
 <span data-ttu-id="2f3ae-159">**問如果使用者存取服務時要移動資料發生什麼情況？**</span><span class="sxs-lookup"><span data-stu-id="2f3ae-159">**Q. What happens if users access services while the data is being moved?**</span></span>
  
<span data-ttu-id="2f3ae-p116">A.請參閱[期間和之後資料移動](during-and-after-your-data-move.md)的某些部分的每個服務的資料移動期間可能有限的功能的完整清單。</span><span class="sxs-lookup"><span data-stu-id="2f3ae-p116">A. See [During and after your data move](during-and-after-your-data-move.md) for a complete list of features that may be limited during portions of the data move for each service.</span></span> 
  
 <span data-ttu-id="2f3ae-162">**問： 要如何知道移動已完成**</span><span class="sxs-lookup"><span data-stu-id="2f3ae-162">**Q. How do I know the move is complete?**</span></span>
  
<span data-ttu-id="2f3ae-p117">A.觀賞 Office 365 郵件內的每個服務資料移動已完成的確認。每個服務資料移動時，我們將會讓您將取得三個完成通知張貼完成通知： 供每個 Exchange Online、 SharePoint Online 和 Skype 的商務 Online。</span><span class="sxs-lookup"><span data-stu-id="2f3ae-p117">A. Watch the Office 365 message center for confirmation that the move of each service's data is complete. When each service's data is moved, we'll post a completion notice so you'll get three completion notices: one each for Exchange Online, SharePoint Online, and Skype for Business Online.</span></span>
  
<span data-ttu-id="2f3ae-166">如果您看到移動後的任何問題，請連絡[Office 365 支援](https://go.microsoft.com/fwlink/p/?LinkID=522459)以取得協助。</span><span class="sxs-lookup"><span data-stu-id="2f3ae-166">If you see any issues after the move, contact [Office 365 Support](https://go.microsoft.com/fwlink/p/?LinkID=522459) to get assistance.</span></span> 
  
 <span data-ttu-id="2f3ae-167">**問 Office 365 哪些資料會儲存在新的資料中心 geos？**</span><span class="sxs-lookup"><span data-stu-id="2f3ae-167">**Q. What data for Office 365 is stored in the new datacenter geos?**</span></span>
  
<span data-ttu-id="2f3ae-p118">A.如果客戶佈建其中一個新的資料中心 geos Microsoft 其租用戶會儲存在地理位置中的其餘部分的下列客戶資料：</span><span class="sxs-lookup"><span data-stu-id="2f3ae-p118">A. If a customer provisions its tenant in one of the new datacenter geos, Microsoft stores the following customer data at rest within the geo:</span></span>
  
- <span data-ttu-id="2f3ae-170">Exchange Online 信箱內容 （電子郵件內文、 行事曆項目和電子郵件附件的內容）</span><span class="sxs-lookup"><span data-stu-id="2f3ae-170">Exchange Online mailbox content (e-mail body, calendar entries, and the content of email attachments)</span></span>
    
- <span data-ttu-id="2f3ae-171">SharePoint Online 網站內容與該網站，包含 Project Online 及存取線上內容中所儲存的檔案。</span><span class="sxs-lookup"><span data-stu-id="2f3ae-171">SharePoint Online site content and the files stored within that site, including Project Online and Access Online content.</span></span>
    
<span data-ttu-id="2f3ae-172">此外，此資料不會複寫以外的地理位置。</span><span class="sxs-lookup"><span data-stu-id="2f3ae-172">In addition, this data is not replicated outside of the geo.</span></span>
  
 <span data-ttu-id="2f3ae-173">**問： 我已經在其中一個新的資料中心 geos、 Office 365 客戶，但我我註冊時選取不同的國家/地區。如何可以我要移至新的資料中心地理位置？**</span><span class="sxs-lookup"><span data-stu-id="2f3ae-173">**Q. I am an Office 365 customer in one of the new datacenter geos, but when I signed up, I selected a different country. How can I be moved to the new datacenter geo?**</span></span>
  
<span data-ttu-id="2f3ae-p119">A 但是、 不可以變更您的租用戶相關聯的國家/地區。而您需要建立新的訂閱新的 Office 365 租用戶和手動將您的使用者和資料移至新的承租人。</span><span class="sxs-lookup"><span data-stu-id="2f3ae-p119">A. Unfortunately, it is not possible to change the country associated with your tenant. Instead, you need to create a new Office 365 tenant with a new subscription and manually move your users and data to the new tenant.</span></span>
  
 <span data-ttu-id="2f3ae-177">**問會有我 bill 上的任何變更吗？**</span><span class="sxs-lookup"><span data-stu-id="2f3ae-177">**Q. Will there be any changes on my bill?**</span></span>
  
<span data-ttu-id="2f3ae-p120">A.在大多數情況下有其帳務陳述式會看到客戶的任何變更。</span><span class="sxs-lookup"><span data-stu-id="2f3ae-p120">A. In most cases there are no changes that customers in will see on their billing statement.</span></span>
  
<span data-ttu-id="2f3ae-p121">Microsoft 會等於 for Office 365 服務澳大利亞 GST 其他量收費的 Office 365 的所有澳大利亞客戶與將會發出稅發票。因為澳大利亞 GST 息上的貨品應課稅供應且 services 提供和提供澳洲中就會發生這項變更。</span><span class="sxs-lookup"><span data-stu-id="2f3ae-p121">Microsoft will charge all Australian customers of Office 365 an additional amount equal to the Australian GST for Office 365 services and will issue tax invoices. This change will occur because Australian GST is payable on taxable supplies of goods and services provided and offered in Australia.</span></span>
  
 <span data-ttu-id="2f3ae-182">**問如果我們 in process of 電子郵件資料移轉至 Office 365 Exchange Online 移動作業期間發生什麼情況？**</span><span class="sxs-lookup"><span data-stu-id="2f3ae-182">**Q. What happens if we are in process of email data migration to Office 365 during the Exchange Online move?**</span></span>
  
<span data-ttu-id="2f3ae-p122">A.如果電子郵件移轉正在進行中，目前移轉任何個別信箱會取消此事件租用戶移動完成，以及這些信箱移轉會自動重新啟動後的目標資料中心是租用戶時。</span><span class="sxs-lookup"><span data-stu-id="2f3ae-p122">A. If email migrations are in progress, any individual mailboxes that are currently being migrated will be canceled while the tenant move finalizes, and migration of those mailboxes will automatically restart once the tenant is in the target datacenters.</span></span>
  
 <span data-ttu-id="2f3ae-185">**問資料移動後不在先前的資料中心地理位置，它已從這些資料中心？**</span><span class="sxs-lookup"><span data-stu-id="2f3ae-185">**Q. After data is moved out of the previous datacenter geo, is it removed from those datacenters?**</span></span>
  
<span data-ttu-id="2f3ae-p123">A 是，舊的資料將會清除在一段時間之後。</span><span class="sxs-lookup"><span data-stu-id="2f3ae-p123">A. Yes, the old data will be purged after a period of time.</span></span>
  
 <span data-ttu-id="2f3ae-188">**問我可以試驗某些使用者吗？**</span><span class="sxs-lookup"><span data-stu-id="2f3ae-188">**Q. Can I pilot some users?**</span></span>
  
<span data-ttu-id="2f3ae-p124">A.時您的 Office 365 租用戶移至新的資料中心地理位置時，所有使用者都移一次。您可以建立不同的試用版租用戶測試連線，但試用承租人不能以任何方法結合您現有的租用戶。</span><span class="sxs-lookup"><span data-stu-id="2f3ae-p124">A. When your Office 365 tenant is moved to a new datacenter geo, all users are moved at once. You can create a separate trial tenant to test connectivity, but the trial tenant can't be combined in any way with your existing tenant.</span></span>
  
 <span data-ttu-id="2f3ae-192">**如何將我會收到通知有關移動和誰在我的公司問將會收到通知？**</span><span class="sxs-lookup"><span data-stu-id="2f3ae-192">**Q. How will I be notified about the move and who at my company will be notified?**</span></span>
  
<span data-ttu-id="2f3ae-p125">A.我們將使用 Office 365 郵件內，這是與 Office 365 中的任何管理員權限的任何人都看得到。</span><span class="sxs-lookup"><span data-stu-id="2f3ae-p125">A. We'll use the Office 365 message center, which is visible to anyone with any admin permissions in Office 365.</span></span>
  
 <span data-ttu-id="2f3ae-195">**問我不想要等到的 Microsoft 移動 「 我的資料。可以只建立新的租用戶和移動自行吗？**</span><span class="sxs-lookup"><span data-stu-id="2f3ae-195">**Q. I don't want to wait for Microsoft to move my data. Can I just create a new tenant and move myself?**</span></span>
  
<span data-ttu-id="2f3ae-p126">A.是，不過無法順暢一樣 Microsoft 執行資料移動程序。</span><span class="sxs-lookup"><span data-stu-id="2f3ae-p126">A. Yes, however the process will not be as seamless as if Microsoft were to perform the data move.</span></span>
  
<span data-ttu-id="2f3ae-p127">如果您建立新的用戶提供新的資料中心地理位置之後，新的承租人主控新的地理位置中。這個新的租用戶是從上一個租用完全不同，您就是負責移動所有使用者信箱、 網站內容、 網域名稱及任何其他資料。請注意您無法到另一個承租人將租用戶名稱。我們建議您等候為我們採取的移動所有設定、 資料及使用者的訂閱注意 Microsoft 提供的移動程式。</span><span class="sxs-lookup"><span data-stu-id="2f3ae-p127">If you create a new tenant after the new datacenter geo is available, the new tenant will be hosted in the new geo. This new tenant is completely separate from your previous tenant and you would be responsible for moving all user mailboxes, site content, domain names, and any other data. Note that you can't move the tenant name from one tenant to another. We recommend that you wait for the move program provided by Microsoft as we'll take care of moving all settings, data, and subscriptions for your users.</span></span>
  
 <span data-ttu-id="2f3ae-202">**問我準備好不會移動，我可以挑選特定 move date 嗎？**</span><span class="sxs-lookup"><span data-stu-id="2f3ae-202">**Q. I'm not ready to be moved, can I pick a specific move date?**</span></span>
  
<span data-ttu-id="2f3ae-p128">A.它不能讓您變更時將移動的每個服務的客戶資料。資料移動是以使用者影響最小的後端作業。</span><span class="sxs-lookup"><span data-stu-id="2f3ae-p128">A. It is not possible for you to change when each service's customer data will be moved. Data moves are a back-end operation with minimal impact to end-users.</span></span>
  
 <span data-ttu-id="2f3ae-206">**問： 我的客戶資料已經已移至新的資料中心地理位置。可以將移回吗？**</span><span class="sxs-lookup"><span data-stu-id="2f3ae-206">**Q. My customer data has already been moved to a new datacenter geo. Can I move back?**</span></span>
  
<span data-ttu-id="2f3ae-p129">A.這即無法再。移至新的地理位置資料中心的客戶無法移回。為所有地理位置的客戶，您會遇到相同的服務、 效能及安全性控管品質如同前。</span><span class="sxs-lookup"><span data-stu-id="2f3ae-p129">A. This is not possible. Customers who have been moved to new geo datacenters cannot be moved back. As a customer in any geo, you will experience the same quality of service, performance, and security controls as you did before.</span></span>
  
 <span data-ttu-id="2f3ae-211">**問新的資料中心 geos do 為目前的資料中心 geos 使用相同的版本的 Office 365 服務功能**</span><span class="sxs-lookup"><span data-stu-id="2f3ae-211">**Q. Do the new datacenter geos use the same versions of Office 365 services as the current datacenter geos?**</span></span>
  
<span data-ttu-id="2f3ae-p130">A.[是]。</span><span class="sxs-lookup"><span data-stu-id="2f3ae-p130">A. Yes.</span></span>
  
 <span data-ttu-id="2f3ae-214">**問將 Office 365 租用戶的新資料中心主控以外的國家/地區的使用者可以使用吗？**</span><span class="sxs-lookup"><span data-stu-id="2f3ae-214">**Q. Will Office 365 tenants hosted in the new datacenters be available to users outside of the country?**</span></span>
  
<span data-ttu-id="2f3ae-p131">A.[是]。Microsoft 維護含有超過 50 個位置中具有超過 1500 個網際網路服務提供者 (Isp) 使用的對等協議全球各地 23 國家/地區中的公用網際網路連線的大型通用網路。使用者無法從他們是在網際網路上的任何位置存取資料中心。</span><span class="sxs-lookup"><span data-stu-id="2f3ae-p131">A. Yes. Microsoft maintains a large global network with public Internet connections in more than 50 locations in 23 countries around the world with peering agreements with more than 1,500 Internet Service Providers (ISPs). Users will be able to access the datacenters from wherever they are on the Internet.</span></span>
  

