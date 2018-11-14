---
title: 使用基準與效能歷程記錄進行 Office 365 效能調整
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 8/31/2017
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 1492cb94-bd62-43e6-b8d0-2a61ed88ebae
description: 有一些簡單的方法來檢查 Office 365 與業務，將可讓您建立您的連線能力的粗略基準之間的連線效能。了解效能歷程記錄的用戶端電腦連線可協助您偵測新問題早期、 識別及預測的問題。
ms.openlocfilehash: 30a0903d95ccfcd2018d8971c74c7f80223c005d
ms.sourcegitcommit: e334616f1b357365b380990eda63f6e63d52ec5b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2018
ms.locfileid: "26024685"
---
# <a name="office-365-performance-tuning-using-baselines-and-performance-history"></a><span data-ttu-id="b94fd-104">使用基準與效能歷程記錄進行 Office 365 效能調整</span><span class="sxs-lookup"><span data-stu-id="b94fd-104">Office 365 performance tuning using baselines and performance history</span></span>

<span data-ttu-id="b94fd-p102">有一些簡單的方法來檢查 Office 365 與業務，將可讓您建立您的連線能力的粗略基準之間的連線效能。了解效能歷程記錄的用戶端電腦連線可協助您偵測新問題早期、 識別及預測的問題。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p102">There are some simple ways to check the connection performance between Office 365 and your business that will let you establish a rough baseline of your connectivity. Knowing the performance history of your client computer connections can help you detect emerging issues early, identify, and predict problems.</span></span>
  
<span data-ttu-id="b94fd-p103">如果您不是用來處理效能問題，本文會幫助您考慮一些常見的問題，像是如何知道的效能問題及未 Office 365 服務事件是您正在看不到的問題？您規劃良好的效能、 如何長字詞？您要如何對效能保留眼？如果您的小組或用戶端會看見使用 Office 365 時的效能低落，您不知道有關所有這些問題的閱讀。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p103">If you're not used to working on performance issues, this article is designed to help you consider some common questions, like How do you know the problem you're seeing is a performance issue and not an Office 365 service incident? How can you plan for good performance, long term? How can you keep an eye on performance? If your team or clients are seeing slow performance while using Office 365, and you wonder about any of these questions, read on.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="b94fd-p104">**來說已用戶端和 Office 365 之間的效能問題吗？** 請遵循下文概述的[效能疑難排解 Office 365 計劃](performance-troubleshooting-plan.md)中的步驟。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p104">**Have a performance issue between your client and Office 365 right now?** Follow the steps outlined in the [Performance troubleshooting plan for Office 365](performance-troubleshooting-plan.md).</span></span> 
    
## <a name="something-you-should-know-about-office-365-performance"></a><span data-ttu-id="b94fd-113">您應該了解 Office 365 效能的某個項目</span><span class="sxs-lookup"><span data-stu-id="b94fd-113">Something you should know about Office 365 performance</span></span>

<span data-ttu-id="b94fd-p105">Office 365 儲存而不只是由 「 自動化，但實際的人為穩定受監控高容量、 專用的 Microsoft 網路內。維護 Office 365 雲端角色的一部分是建置在效能調整及簡化很可能。自 Office 365 雲端的用戶端可以經由網際網路連線，有太跨 Office 365 服務微調效能連續位置。效能改進永遠不會真的停止雲端中，並有許多累積經驗保持雲端正常且快速。它應該發生與您位置連線至 Office 365 的效能問題，最適合未開始使用，並等待上支援案例。但是，您應該開始調查從 '內外精通' 問題。也就是啟動內部網路及運作解說至 Office 365。當您開啟案例與 Office 365 支援之前，您可以收集資料，並採取動作會瀏覽、 且可能會解決您的問題。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p105">Office 365 lives inside a high-capacity, dedicated Microsoft network that is steadily monitored not just by automation, but by real people. Part of the role of maintaining the Office 365 cloud is building-in performance tuning and streamlining where it's possible. Since clients of the Office 365 cloud have to connect across the Internet, there is a continuous effort to fine-tune the performance across Office 365 services too. Performance improvements never really stop in the cloud, and there is a lot of accumulated experience with keeping the cloud healthy and quick. Should you experience a performance issue connecting from your location to Office 365, it's best not to start with, and wait on, a Support case. Instead, you should begin investigating the problem from 'the inside out'. That is, start inside of your network, and work your way out to Office 365. Before you open a case with Office 365 Support, you can gather data and take actions that will explore, and may resolve, your problem.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="b94fd-p106">請注意的容量規劃與 Office 365 中的限制。該資訊會讓您將在內曲線，嘗試解決效能問題時。以下是[Office 365 平台服務說明](https://technet.microsoft.com/en-us/library/office-365-service-descriptions.aspx)連結。這是中央的集區，並提供 Office 365 的所有服務都從這裡會移至其專屬服務說明連結。這表示，應必須請參閱標準 limits for SharePoint Online，例如，您就按一下 [ [SharePoint Online 服務說明](https://technet.microsoft.com/en-us/library/sharepoint-online-service-description.aspx)並找出其[SharePoint Online 限制] 區段中](https://go.microsoft.com/fwlink/p/?LinkID=856113)。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p106">Be aware of capacity planning and limits in Office 365. That information will put you ahead of the curve when trying to resolve a performance issue. Here's a link to the [Office 365 Platform Service Description](https://technet.microsoft.com/en-us/library/office-365-service-descriptions.aspx). This is a central hub, and all the services offered by Office 365 have a link that goes to their own Service Descriptions from here. That means, should you need to see the standard limits for SharePoint Online, for example, you would click [SharePoint Online Service Description](https://technet.microsoft.com/en-us/library/sharepoint-online-service-description.aspx) and locate its [SharePoint Online Limits section](https://go.microsoft.com/fwlink/p/?LinkID=856113).</span></span> 
  
<span data-ttu-id="b94fd-p107">請確定您移到了解與您疑難排解效能會滑動規模、 不需達成理想化的值和永久維護 (如果您認為這是，則會爾高頻寬工作 like 上佈建大量的使用者，或執行大型資料移轉作業將會是非常壓力--所以不要規劃的效能影響然後)。您可以且應、 您效能目標、 粗略想法但許多的效能，因此，效能到變數播放而異。這是效能的性質。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p107">Make sure you go into your troubleshooting with the understanding that performance is a sliding scale, it's not about achieving an idealized value and maintaining it permanently (if you believe this is so, then occasional high-bandwidth tasks like on-boarding a large number of users, or doing large data migrations will be very stressful -- so do plan for performance impacts then). You can, and should, have a rough idea of your performance targets, but a lot of variables play into performance, therefore, performance varies. That's the nature of performance.</span></span> 
  
<span data-ttu-id="b94fd-130">效能疑難排解不需符合特定目標很無限期維護這些號碼相關改善現有活動授與所有的變數。</span><span class="sxs-lookup"><span data-stu-id="b94fd-130">Performance troubleshooting isn't about meeting specific goals and maintaining those numbers indefinitely, it's about improving existing activities, given all the variables.</span></span> 
  
## <a name="okay-what-does-a-performance-problem-look-like"></a><span data-ttu-id="b94fd-131">好，效能問題外觀如何？</span><span class="sxs-lookup"><span data-stu-id="b94fd-131">Okay, what does a performance problem look like?</span></span>

<span data-ttu-id="b94fd-p108">首先，您必須確定您遭遇確實的效能問題及未建立服務事件。不同 Office 365 中建立服務事件是效能問題。以下是如何告知他們分開。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p108">First, you need to make sure that what you are experiencing is indeed a performance issue and not a service incident. A performance problem is different from a service incident in Office 365. Here's how to tell them apart.</span></span>
  
<span data-ttu-id="b94fd-p109">如果 Office 365 服務問題的服務事件的問題。您會看到紅色或黃色圖示在 Office 365 系統管理中心的**目前健全狀況**下，您也可能會發現連線至 Office 365 的用戶端電腦上的效能低落。例如，如果目前健全狀況報告的紅色圖示，請參閱**Investigating**旁邊 Exchange 可能再也收到之呼叫的一組從您組織中抱怨使用 Exchange Online 的用戶端信箱執行錯誤的人員。在此情況下，它是合理假設您的 Exchange Online 效能剛變成服務內的問題的受害者。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p109">If the Office 365 service is having issues, that's a service incident. You will see red or yellow icons under **Current health** in the Office 365 admin center, you may also notice slow performance on client computers connecting to Office 365. For example, if Current health reports a red icon and you see **Investigating** beside Exchange, you might then also receive a bunch of calls from people in your organization who complain that client mailboxes that use Exchange Online are performing badly. In that case, it's reasonable to assume that your Exchange Online performance just became a victim of issues within the Service.</span></span> 
  
![Office 365 狀況儀表板以顯示綠色、 Exchange、 顯示服務還原以外的所有工作量。](media/ec7f0325-9e61-4e1a-bec0-64b87f4469be.PNG)
  
<span data-ttu-id="b94fd-p110">此時，Office 365 系統管理員應該檢查**目前健全狀況**，然後**檢視詳細資料和記錄**，經常，我們在系統執行的維護上保留最新。**目前健全狀況**儀表板進行更新您需、 變更及服務中的問題。附註及說明寫入狀況歷程記錄管理員可以管理、 有可以協助您量測貴影響，並保留您張貼需持續運作。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p110">At this point, you, the Office 365 admin, should check **Current health** and then **View details and history**, frequently, to keep up to date on maintenance we perform on the system. The **Current health** dashboard was made to update you about changes to, and problems in, the service. The notes and explanations written to health history, admin to admin, are there to help you gauge your impact, and to keep you posted about ongoing work.</span></span> 
  
![圖片的 Office 365 狀況儀表板解釋已還原 Exchange Online 服務，以及為何。](media/66609554-426a-4448-8be6-ea09817f41ba.PNG)
  
<span data-ttu-id="b94fd-p111">效能問題不是建立服務事件，即使事件可能會造成效能緩慢。效能問題看起來如下：</span><span class="sxs-lookup"><span data-stu-id="b94fd-p111">A performance issue isn't a service incident, even though incidents can cause slow performance. A performance issue looks like this:</span></span>
  
- <span data-ttu-id="b94fd-146">不論在 Office 365 系統管理中心**目前健全狀況**報告服務發生的效能問題。</span><span class="sxs-lookup"><span data-stu-id="b94fd-146">A performance issue occurs no matter what the Office 365 admin center **Current health** is reporting for the service.</span></span> 
    
-  <span data-ttu-id="b94fd-147">用來為相當順暢行為採用甚久才完成或從未完成。</span><span class="sxs-lookup"><span data-stu-id="b94fd-147">A behavior that used to be relatively seamless takes a long time to complete or never completes.</span></span> 
    
- <span data-ttu-id="b94fd-148">您可以複製問題，或至少，在您知道情形是否右邊的一系列的步驟。</span><span class="sxs-lookup"><span data-stu-id="b94fd-148">You can replicate the problem too, or, at least, you know it will happen if you do the right series of steps.</span></span>
    
-  <span data-ttu-id="b94fd-149">如果間歇性問題，仍然是圖樣，例如您知道根據 10:00 AM 您將具備可靠無法存取 Office 365 使用者的電話和通話將會繞中午死向下。</span><span class="sxs-lookup"><span data-stu-id="b94fd-149">If the problem is intermittent, there is still a pattern, for example, you know that by 10:00 AM you will have calls from users who can't reliably access Office 365, and that the calls will die down around noon.</span></span> 
    
<span data-ttu-id="b94fd-p112">這可能是聲音熟悉;也許太熟悉。一旦您知道是效能問題，會成為問題，「 什麼？ 下一步]"本文的其餘部分可協助您決定完全的。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p112">This probably sounds familiar; maybe too familiar. Once you know it's a performance problem, the question becomes, "What do you do next?" The rest of this article helps you determine exactly that.</span></span>
  
## <a name="how-to-define-and-test-the-performance-problem"></a><span data-ttu-id="b94fd-153">如何定義及測試的效能問題</span><span class="sxs-lookup"><span data-stu-id="b94fd-153">How to define and test the performance problem</span></span>

<span data-ttu-id="b94fd-p113">效能問題通常出現一段時間，讓它可以是面對定義實際的問題。您需要建立好問題陳述式及問題內容的不錯的選項，然後您需要鎖死測試的步驟為 win 一天。否則請到您自己的任何錯誤，您可能會遺失。為何？以下是一些範例問題陳述式不提供足夠的資訊：</span><span class="sxs-lookup"><span data-stu-id="b94fd-p113">Performance issues often emerge over time, so it can be challenging to define the actual problem. You need to create a good problem statement and a good idea of issue context, and then you need to repeatable testing steps to win the day. Otherwise, through no fault of your own, you may be lost. Why? Well, here are some examples of problems statements that don't provide enough information:</span></span>
  
- <span data-ttu-id="b94fd-p114">從 「 我的收件匣切換到我的行事曆用來能夠我沒注意到，很現在咖啡符號。您可以讓它像其用來處理吗？</span><span class="sxs-lookup"><span data-stu-id="b94fd-p114">Switching from my Inbox to my Calendar used to be something I didn't notice, and now it's a coffee-break. Can you make it act like it used to?</span></span>
    
- <span data-ttu-id="b94fd-p115">將 「 我的檔案上傳至 SharePoint Online 的利用不限次數。為什麼會很慢下午，但任何其他時間，則較快？它只是無法 fast 吗？</span><span class="sxs-lookup"><span data-stu-id="b94fd-p115">Uploading my files to SharePoint Online is taking forever. Why is it slow in the afternoon, but any other time, it's fast? Can't it just be fast?</span></span>
    
<span data-ttu-id="b94fd-p116">有數個大型的挑戰上述問題陳述式來防範。尤其是有許多的來處理的混淆。例如：</span><span class="sxs-lookup"><span data-stu-id="b94fd-p116">There are several large challenges posed by the problem statements above. Specifically, there are a lot of ambiguities to deal with. for example:</span></span>
  
- <span data-ttu-id="b94fd-167">它是不清楚如何收件匣和行事曆之間切換用來處理膝上型電腦。</span><span class="sxs-lookup"><span data-stu-id="b94fd-167">It's unclear how switching between Inbox and Calendar used to act on the laptop.</span></span>
    
- <span data-ttu-id="b94fd-168">當使用者選取時，"無法它只是 fast"，什麼是 「 快速 」？</span><span class="sxs-lookup"><span data-stu-id="b94fd-168">When the user says, "Can't it just be fast", what's "fast"?</span></span>
    
- <span data-ttu-id="b94fd-p117">多久 「 永遠 」 吗？是的幾秒或幾分鐘，或無法移至 lunch 的使用者和它會完成十分鐘之後使用者 got back up 吗？</span><span class="sxs-lookup"><span data-stu-id="b94fd-p117">How long is "forever"? Is that several seconds, or minutes, or could the user go to lunch and it would finish up ten minutes after the user got back?</span></span>
    
<span data-ttu-id="b94fd-p118">所有這些都是不考量的管理及疑難排解員無法注意從思考下列問題陳述式的許多詳細資料。例如，新鮮事; 開始出現問題時使用者運作從首頁和只會看到首頁網路; 上慢速切換使用者必須在本機用戶端或使用者上執行數個其他 RAM 密集應用程式執行更舊的作業系統或尚未執行新版更新。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p118">All of this is without considering that the admin and troubleshooter can't be aware of many details from problem statements like these. For example, when the problem started happening; That the user works from home and only ever sees slow switching while on a home network; That the user must run several other RAM intensive applications on the local client, or the user is running an older operating system or hasn't run recent updates.</span></span>
  
<span data-ttu-id="b94fd-p119">當使用者報告效能問題時，有許多要收集的資訊。收集此資訊是呼叫設定議題、 範圍或調查該程序的一部分。以下是您可以使用收集的效能問題的相關資訊的基本範圍清單。這份清單不夠詳盡，但是啟動您自己的其中一個位置：</span><span class="sxs-lookup"><span data-stu-id="b94fd-p119">When users report a performance problem, there's a lot of information to collect. Collecting this information is part of a process called scoping the issue, or investigating it. The following is a basic scoping list you can use to collect information about your performance issue. This list is not exhaustive, but it's a place to start one of your own:</span></span> 
  
- <span data-ttu-id="b94fd-177">在哪些日期沒有問題發生，與周圍白天或晚上什麼時候？</span><span class="sxs-lookup"><span data-stu-id="b94fd-177">On what date did the issue happen, and around what time of day or night?</span></span>
    
- <span data-ttu-id="b94fd-178">您已使用何種用戶端電腦，及如何加以沒有連線至公司網路 （VPN、 有線、 無線）？</span><span class="sxs-lookup"><span data-stu-id="b94fd-178">What kind of client computer were you using, and how does it connect to the business network (VPN, Wired, Wireless)?</span></span>
    
- <span data-ttu-id="b94fd-179">您已從遠端工作或您已在 office 中吗？</span><span class="sxs-lookup"><span data-stu-id="b94fd-179">Were you working remotely or were you in the office?</span></span>
    
- <span data-ttu-id="b94fd-180">您沒有嘗試在另一部電腦上的相同動作並查看同樣的行為吗？</span><span class="sxs-lookup"><span data-stu-id="b94fd-180">Did you try the same actions on another computer and see the same behavior?</span></span>
    
- <span data-ttu-id="b94fd-181">逐步解說會給予您發生問題，因此您可以寫入向下時採取的動作的步驟。</span><span class="sxs-lookup"><span data-stu-id="b94fd-181">Walk through the steps that are giving you the trouble so that you can write the actions you take down.</span></span>
    
- <span data-ttu-id="b94fd-182">如何秒或幾分鐘的速度過慢是效能？</span><span class="sxs-lookup"><span data-stu-id="b94fd-182">How slow in seconds or minutes is the performance?</span></span>
    
- <span data-ttu-id="b94fd-183">在全球您位於何處？</span><span class="sxs-lookup"><span data-stu-id="b94fd-183">Where in the world are you located?</span></span>
    
<span data-ttu-id="b94fd-p120">這些問題的部分是更明顯比其他人。最多人將會了解疑難排解員需要重現問題的確切步驟。畢竟如何其他可記錄功能錯誤，與其他方式可以測試如果修正此問題？較不明顯是之類的 」 功能的日期和時間沒有您查看問題？"、 和"其中世界中您位於？"] 下，可使用於 tandem 的資訊。根據使用者所運作時，幾個小時的時間差異可能表示維護技巧已經在公司網路的部分。如果您的公司具有混合實作，例如混合式 SharePoint 搜尋查詢的例如搜尋索引中 SharePoint Online 和內部 SharePoint Server 2013 的執行個體、 更新可能技巧內部部署伺服器陣列中。如果您的公司所有位於雲端，系統維護可能包括新增或移除 [啟用全公司或了修訂 DNS、 或其他核心基礎結構更新的網路硬體。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p120">Some of these questions are more obvious than others. Most everyone will understand a troubleshooter needs the exact steps to reproduce the issue. After all, how else can you record what's wrong, and how else can you test if the issue is fixed? Less obvious are things like "What date and time did you see the issue?", and "Where in the world are you located?", information that can be used in tandem. Depending on when the user was working, a few hours of time difference may mean maintenance is already underway on parts of your company's network. If, for example, your company has a hybrid implementation, like a hybrid SharePoint Search, which can query search indexes in both SharePoint Online and an On-premises SharePoint Server 2013 instance, updates may be underway in the on-premises farm. If your company is all in the cloud, system maintenance may include adding or removing network hardware, rolling out updates that are company-wide, or making changes to DNS, or other core infrastructure.</span></span>
  
<span data-ttu-id="b94fd-p121">當您正在進行疑難排解效能問題時，有點像犯罪場景，您必須是很精確和 observant 繪製任何結論從證據。若要這樣做，您必須取得良好的問題陳述式來收集證據。它應該包含之電腦的內容、 使用者的內容問題開始時, 及公開效能問題的確切步驟。這個問題陳述式應該是的並保持在您的附註中最頂端的頁面。帶您逐步完成一次問題陳述式之後您處理解析度，您會進行測試及證明您採取的動作是否有解決問題的步驟。這是關鍵知道您的工作，有，已完成。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p121">When you're troubleshooting a performance problem, it's a bit like a crime scene, you need to be precise and observant to draw any conclusions from the evidence. In order to do this, you must get a good problem statement by gathering evidence. It should include the computer's context, the user's context, when the problem began, and the exact steps that exposed the performance issue. This problem statement should be, and stay, the topmost page in your notes. By walking through the problem statement again after you work on the resolution, you are taking the steps to test and prove whether the actions you take have resolved the issue. This is critical to knowing when your work, there, is done.</span></span>
  
## <a name="do-you-know-how-performance-used-to-look-when-it-was-good"></a><span data-ttu-id="b94fd-197">您知道時它很好的效能如何使用？</span><span class="sxs-lookup"><span data-stu-id="b94fd-197">Do you know how performance used to look when it was good?</span></span>

<span data-ttu-id="b94fd-p122">如果您是背，沒有人知道。有空有數字。這表示沒有人可以接聽簡單的問題 [關於多少秒沒有其用來採用以相反 Office 365 中的收件匣？ 」，或"長沒有其用來取得時高階主管鎖 Lync Online 會議？"，這是常見的案例的許多公司。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p122">If you're unlucky, nobody knows. Nobody had numbers. That means nobody can answer the simple question "About how many seconds did it used to take to bring up an Inbox in Office 365?", or "How long did it used to take when the Executives had a Lync Online meeting?", which is a common scenario for many companies.</span></span>
  
<span data-ttu-id="b94fd-201">什麼是遺失以下是效能基準線。</span><span class="sxs-lookup"><span data-stu-id="b94fd-201">What's missing here is a performance baseline.</span></span>
  
<span data-ttu-id="b94fd-p123">比較基準提供您將內容以在效能。您應採取比較基準有時會為經常，視您的公司的需求而定。如果您是較大的公司、 作業小組可能已經需要內部部署環境的基準線。例如，如果您的月份和您所有的 SharePoint 伺服器上的第三個星期一的第一個星期一修補所有 Exchange 伺服器，作業小組可能具有的任務清單和案例執行後修補，以證明所重要的功能操作。例如，開啟收件匣、 按一下 [傳送/接收及確定資料夾更新或 SharePoint、 瀏覽網站] 的 [主要] 頁面中進入企業搜尋] 頁面上，並執行搜尋會傳回結果。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p123">Baselines give you a context for your performance. You should take a baseline occasionally to frequently, depending on the needs of your company. If you are a larger company, your Operations team may take baselines for your on-premises environment already. For example, if you patch all the Exchange servers on the first Monday of the month, and all your SharePoint servers on the third Monday, your Operations team probably has a list of tasks and scenarios it runs post-patching, to prove that critical functions are operational. For example, opening the Inbox, clicking Send/Receive, and making sure the folders update, or, in SharePoint, browsing the main page of the site, going into the enterprise Search page, and doing a search that returns results.</span></span>
  
<span data-ttu-id="b94fd-p124">如果您的應用程式是在 Office 365，最基本的比較基準可採取的一些測量的時間 （以毫秒為單位） 從您的網路內的用戶端電腦的輸出點，或您保留您的網路並前往 Office 365 的點。以下是一些很有幫助您調查的比較基準和記錄：</span><span class="sxs-lookup"><span data-stu-id="b94fd-p124">If your applications are in Office 365, some of the most fundamental baselines you can take measure the time (in milliseconds) from a client computer inside your network, to an egress point, or the point where you leave your network and go out to Office 365. Here are some helpful baselines that you can investigate and record:</span></span>
  
- <span data-ttu-id="b94fd-209">識別您的用戶端電腦與您的輸出點，例如 proxy 伺服器間的裝置。</span><span class="sxs-lookup"><span data-stu-id="b94fd-209">Identify the devices between your client computer and your egress point, for example, your proxy server.</span></span>
    
  - <span data-ttu-id="b94fd-210">您必須知道您的裝置，讓您有內容 (et cetera 類型的裝置的 IP 位址) 的發生的效能問題。</span><span class="sxs-lookup"><span data-stu-id="b94fd-210">You need to know your devices so that you have context (IP addresses, type of device, et cetera) for performance problems that arise.</span></span>
    
  - <span data-ttu-id="b94fd-211">Proxy 伺服器是常見的輸出點，因此您可以檢查網頁瀏覽器中查看它設定為使用，如果有任何何種 proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="b94fd-211">Proxy servers are common egress points, so you can check your web browser to see what proxy server it is set to use, if any.</span></span>
    
  - <span data-ttu-id="b94fd-212">第三方工具可探索並對應您的網路，但最安全的方式來了解您裝置會詢問您網路的小組成員。</span><span class="sxs-lookup"><span data-stu-id="b94fd-212">There are third party tools that can discover and map your network, but the safest way to know your devices is to ask a member of your network team.</span></span>
    
- <span data-ttu-id="b94fd-213">識別網際網路服務提供者 (ISP)、 寫下連絡資訊，並要求多少 circuits 有多少頻寬。</span><span class="sxs-lookup"><span data-stu-id="b94fd-213">Identify your Internet service provider (ISP), write down their contact information, and ask how many circuits how much bandwidth you have.</span></span>
    
- <span data-ttu-id="b94fd-214">公司內部識別您的用戶端和輸出點之間，裝置的資源或識別緊急電話的連絡人以會談到網路問題。</span><span class="sxs-lookup"><span data-stu-id="b94fd-214">Inside your company, identify resources for the devices between your client and the egress point, or identify an emergency contact to talk to about networking issues.</span></span>
    
<span data-ttu-id="b94fd-215">以下是一些基準亦簡單測試與工具可以計算您：</span><span class="sxs-lookup"><span data-stu-id="b94fd-215">Here are some baselines that simple testing with tools can calculate for you:</span></span>
  
- <span data-ttu-id="b94fd-216">從用戶端電腦時間 （毫秒） 您輸出點</span><span class="sxs-lookup"><span data-stu-id="b94fd-216">Time from your client computer to your egress point in milliseconds</span></span>
    
- <span data-ttu-id="b94fd-217">從時間輸出點至 Office 365 （毫秒）</span><span class="sxs-lookup"><span data-stu-id="b94fd-217">Time from your egress point to Office 365 in milliseconds</span></span>
    
- <span data-ttu-id="b94fd-218">解析 URL 為 Office 365 的瀏覽時之伺服器的內容中的位置</span><span class="sxs-lookup"><span data-stu-id="b94fd-218">Location in the world of the server that resolves the URLS for Office 365 when you browse</span></span>
    
- <span data-ttu-id="b94fd-219">您的 ISP 以毫秒為單位、 封包抵達 （網路抖動） 中的不一致的 DNS 解析的速度上傳與下載時間 （毫秒）</span><span class="sxs-lookup"><span data-stu-id="b94fd-219">The speed of your ISP's DNS resolution in milliseconds, inconsistencies in packet arrival (network jitter), upload and download times in milliseconds</span></span>
    
<span data-ttu-id="b94fd-220">如果您還不熟悉如何執行這些步驟，我們將會移到本文中的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="b94fd-220">If you're unfamiliar with how to carry out these steps, we'll go into more detail in this article.</span></span> 
  
## <a name="what-is-a-baseline"></a><span data-ttu-id="b94fd-221">[比較基準為何？</span><span class="sxs-lookup"><span data-stu-id="b94fd-221">What is a baseline?</span></span>

<span data-ttu-id="b94fd-p125">您會知道影響移故障，但如果您不知道您的歷程記錄的效能資料，它不是可能有如何故障它可能會有成為、 內容及時。比較基準，而您正在遺失拼圖主要線索讓： 拼圖方塊上的圖片。在疑難排解效能，您需要的*比較*點。簡單的效能基準線不需要很難。作業小組可以使用的排程執行這些無間。例如，假設您的連線看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="b94fd-p125">You'll know the impact when it goes bad, but if you don't know your historical performance data, it's not possible to have a context for how bad it may have become, and when. So without a baseline, you're missing the key clue to solve the puzzle: the picture on the puzzle box. In performance troubleshooting, you need a point of  *comparison*  . Simple performance baselines aren't difficult to take. Your Operations team can be tasked with carrying these out on a schedule. For example, let's say your connection looks like this:</span></span> 
  
![基本網路圖形顯示用戶端、 proxy 與 Office 365 雲端。](media/c6ca7140-09f9-4c2d-a775-dbf2820eaa0c.PNG)
  
<span data-ttu-id="b94fd-p126">這表示您已與網路團隊檢查並找離開貴公司的 proxy 伺服器，透過網際網路與該 proxy 處理用戶端電腦傳送至雲端的所有要求。在此例中，您應該繪製列出所有的中間裝置連線的簡化的版本。現在，插入可用於測試之間的用戶端 （位置保留您網路的網際網路） 輸出點、 效能及 Office 365 雲端的工具。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p126">That means you've checked with your network team and found out that you leave your company for the Internet through a proxy server, and that proxy handles all the requests your client computer sends to the cloud. In this case, you should draw a simplified version of your connection that lists all the intervening devices. Now, insert tools that you can use to test the performance between the client, the egress point (where you leave your network for the Internet), and the Office 365 cloud.</span></span>
  
![基本網路與用戶端、 proxy 與雲端及工具建議 PSPing、 TraceTCP，以及網路追蹤。](media/627bfb77-abf7-4ef1-bbe8-7f8cbe48e1d2.png)
  
<span data-ttu-id="b94fd-p127">選項列為 「**簡單**] 和 [**進階**因為您需要以找出效能資料的專業知識的數量。網路追蹤所需的時間，相較於執行命令列工具像是 PsPing 和 TraceTCP 許多的時間。因為它們不使用 ICMP 封包，將會封鎖的 Office 365 中，選擇下列兩個命令列工具及因為他們提供的時間 （毫秒） 的花費保留的用戶端電腦或 proxy 伺服器 （如果您可以存取） 和 Office 365 在送達。到另一部電腦從每個個別躍點將會會結束時間值，也就是更好的基準 ！就如同重要的是，這些命令列工具可讓您新增到此命令的連接埠號碼、 這很有用因為 Office 365 會透過連接埠 443，這是使用安全通訊端階層和傳輸層安全性 （SSL 與 TLS） 的連接埠通訊。不過，其他協力廠商工具可能現況較佳的解決方案。Microsoft 不支援所有這些工具，因此如果因一些原因而無法取得 PsPing 和 TraceTCP 工作，請移至網路追蹤 Netmon 類似的工具。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p127">The options are listed as **Simple** and **Advanced** because of the amount of expertise you need in order to find the performance data. A network trace will take a lot of time, compared to running command-line tools like PsPing and TraceTCP. These two command-line tools were chosen because they don't use ICMP packets, which will be blocked by Office 365, and because they give the time in milliseconds that it takes to leave the client computer, or proxy server (if you have access) and arrive at Office 365. Each individual hop from one computer to another will end up with a time value, and that's great for baselines! Just as importantly, these command-line tools allow you to add a port number onto the command, this is useful because Office 365 communicates over port 443, which is the port used by Secure Sockets Layer and Transport Layer Security (SSL and TLS). However, other third-party tools may be better solutions for your situation. Microsoft doesn't support all of these tools, so if, for some reason, you can't get PsPing and TraceTCP working, move on to a network trace with a tool like Netmon.</span></span> 
  
<span data-ttu-id="b94fd-p128">您可以採取基準前一次期間大量使用的上班時間] 然後下班後再次。這表示您可能必須在結尾處的位元起來像這樣的資料夾結構：</span><span class="sxs-lookup"><span data-stu-id="b94fd-p128">You can take a baseline before business hours, again during heavy use, and then again after hours. This means you may have a folder structure that looks a bit like this in the end:</span></span>
  
![提供將效能資料組織到資料夾之方法的圖形。](media/13e01ffa-f0f2-4d10-b89d-d5980ec89fae.png)
  
<span data-ttu-id="b94fd-p129">您也應該挑選的命名慣例檔案。以下是一些範例：</span><span class="sxs-lookup"><span data-stu-id="b94fd-p129">You should also pick a naming convention your files. Here are some examples:</span></span>
  
- <span data-ttu-id="b94fd-245">Feb_09_2015_9amPST_PerfBaseline_Netmon_ClientToEgress_Normal</span><span class="sxs-lookup"><span data-stu-id="b94fd-245">Feb_09_2015_9amPST_PerfBaseline_Netmon_ClientToEgress_Normal</span></span>
    
- <span data-ttu-id="b94fd-246">Jan_10_2015_3pmCST_PerfBaseline_PsPing_ClientToO365_bypassProxy_SLOW</span><span class="sxs-lookup"><span data-stu-id="b94fd-246">Jan_10_2015_3pmCST_PerfBaseline_PsPing_ClientToO365_bypassProxy_SLOW</span></span>
    
- <span data-ttu-id="b94fd-247">Feb_08_2015_2pmEST_PerfBaseline_BADPerf</span><span class="sxs-lookup"><span data-stu-id="b94fd-247">Feb_08_2015_2pmEST_PerfBaseline_BADPerf</span></span>
    
- <span data-ttu-id="b94fd-248">Feb_08_2015_8 30amEST_PerfBaseline_GoodPerf</span><span class="sxs-lookup"><span data-stu-id="b94fd-248">Feb_08_2015_8-30amEST_PerfBaseline_GoodPerf</span></span>
    
<span data-ttu-id="b94fd-p130">有許多不同的方式達成此目的，但使用格式**\<dateTime\>\<測試中有什麼新鮮事\>** 啟動的理想位置。正在嚴有關此有助於許多當您嘗試要稍後疑難排解問題。稍後，您將能夠說"我萬一兩項追蹤上年 2 月 8 日，其中顯示良好的效能和一個顯示不正確的因此我們可以進行比較"。這是非常有用的疑難排解。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p130">There are lots of different ways to do this, but using the format **\<dateTime\>\<what's happening in the test\>** is a good place to start. Being diligent about this will help a lot when you are trying to troubleshoot issues later. Later, you'll be able to say "I took two traces on February 8th, one showed good performance and one showed bad, so we can compare them". This is extremely helpful for troubleshooting.</span></span> 
  
<span data-ttu-id="b94fd-p131">您需要有可保留在歷程記錄的比較基準組織的方式。在這個範例中，簡單的方法產生三個命令列輸出和結果收集為螢幕擷取畫面，但可能網路擷取檔案而。使用最適合您的方法。會儲存在歷程記錄的比較基準和於您注意到的線上服務的行為變更的時間點參照。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p131">You need to have an organized way to keep your historical baselines. In this example, the simple methods produced three command line outputs and the results were collected as screen shots, but you may have network capture files instead. Use the method that works best for you. Store your historical baselines and refer to them at points where you notice changes in the behavior of online services.</span></span> 
  
## <a name="why-collect-performance-data-during-a-pilot"></a><span data-ttu-id="b94fd-257">為何在試驗期間收集效能資料？</span><span class="sxs-lookup"><span data-stu-id="b94fd-257">Why collect performance data during a pilot?</span></span>

<span data-ttu-id="b94fd-p132">沒有較佳時間来啟動的 Office 365 服務試驗期間進行比基準線。您的 office 可能會有數千個使用者、 數百千分位，也可能會有五個，但即使有少數使用者，您可以執行測試以測量變動效能。但如果是大型的公司、 代表性樣本的試驗部署 Office 365 的數個好幾百種使用者可以被預估向外數個數以千計讓您知道之前所發生的問題可能發生的位置。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p132">There is no better time to start making baselines than during a pilot of the Office 365 service. Your office may have thousands of users, hundreds of thousands, or it may have five, but even with a small number of users, you can perform tests to measure fluctuations in performance. In the case of a large company, a representative sample of several hundred users piloting Office 365 can be projected outward to several thousands so you know where issues might arise before they happen.</span></span>
  
<span data-ttu-id="b94fd-p133">但如果是小型公司、 其中上佈建表示所有使用者都移至服務同時且有無試驗、 保留效能測量，讓您要顯示給任何人來疑難排解錯誤執行的作業可能會有資料。例如，如果您注意到的突然可以逐步花費的時間要上傳的中型圖形其用以非常快速發生在您建立周圍。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p133">In the case of a small company, where on-boarding means that all users go to the service at the same time and there is no pilot, keep performance measures so that you have data to show to anyone who may have to troubleshoot a badly performing operation. For example, if you notice that all of a sudden you can walk around your building in the time it takes to upload a medium-sized graphic where it used to happen very quickly.</span></span>
  
## <a name="how-to-collect-baselines"></a><span data-ttu-id="b94fd-263">如何收集基準線</span><span class="sxs-lookup"><span data-stu-id="b94fd-263">How to collect baselines</span></span>

<span data-ttu-id="b94fd-264">為所有的疑難排解計劃您需要識別至少下列事項：</span><span class="sxs-lookup"><span data-stu-id="b94fd-264">For all troubleshooting plans you need to identify these things at a minimum:</span></span>
  
- <span data-ttu-id="b94fd-265">用戶端電腦正在使用 （的電腦或裝置、 IP 位址、 及造成問題的動作類型）</span><span class="sxs-lookup"><span data-stu-id="b94fd-265">The client computer you're using (the type of computer or device, an IP address, and the actions that caused the issue)</span></span>
    
- <span data-ttu-id="b94fd-266">其中用戶端電腦位於全球 (例如是否在遠端工作的網路的 VPN 或公司內部網路上這位使用者)</span><span class="sxs-lookup"><span data-stu-id="b94fd-266">Where the client computer is located in the world (for example, whether this user on a VPN to the network, working remotely, or on the company intranet)</span></span>
    
- <span data-ttu-id="b94fd-267">輸出點用戶端電腦使用從您的網路 （流量的 ISP 或網際網路離開貴公司的點）</span><span class="sxs-lookup"><span data-stu-id="b94fd-267">The egress point the client computer uses from your network (the point at which traffic leaves your business for an ISP or the Internet)</span></span>
    
 <span data-ttu-id="b94fd-p134">您可以從網路管理員了解您的網路上的版面配置。如果您是小型網路上，查看如何在您連線至網際網路的裝置和呼叫您的 ISP 如果您有關於版面配置的問題。建立您參考 （英文） 的最後一個配置的圖形。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p134">You can find out the layout of your network from the network administrator. If you're on a small network, take a look at the devices connecting you to the Internet, and call your ISP if you have questions about the layout. Create a graphic of the final layout for your reference.</span></span> 
  
<span data-ttu-id="b94fd-p135">本節會分成簡單的命令列工具和方法，並更進階的工具選項。我們將會涵蓋簡單的方法。但如果您已來說 got 效能問題，您應該跳至進階方法並試用範例效能疑難排解動作計劃。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p135">This section is broken into simple command-line tools and methods, and more advanced tools options. We'll cover simple methods first. But if you've got a performance problem right now, you should jump to advanced methods and try out the sample performance-troubleshooting action plan.</span></span>
  
### <a name="simple-methods"></a><span data-ttu-id="b94fd-274">簡單的方法</span><span class="sxs-lookup"><span data-stu-id="b94fd-274">Simple methods</span></span>

<span data-ttu-id="b94fd-p136">這些簡單的方法的目標是了解如何取得、 了解，並適當地儲存簡單效能比較基準一段時間，以便會隨時了 Office 365 效能。以下是簡單非常簡單圖表如您所見之前：</span><span class="sxs-lookup"><span data-stu-id="b94fd-p136">The objective of these simple methods is to learn to take, understand, and properly store simple performance baselines over time so that you are informed about Office 365 performance. Here's the very simple diagram for simple, as you've seen before:</span></span>
  
![基本網路與用戶端、 proxy 與雲端及工具建議 PSPing、 TraceTCP，以及網路追蹤。](media/627bfb77-abf7-4ef1-bbe8-7f8cbe48e1d2.png)
  
> [!NOTE]
> <span data-ttu-id="b94fd-p137">TraceTCP 隨附於此螢幕擷取畫面很有用的工具的顯示，以毫秒為單位，多久要求所需程序和多少網路躍點或連線至下一步]，一部電腦從要求採用以到達目的地。TraceTCP 也可以授與伺服器旋入可支援的 Microsoft Office 365 疑難排解員有用期間使用的名稱。> TraceTCP 命令可以是非常簡單，例如： > `tracetcp.exe outlook.office365.com:443`> 命令中包含的連接埠號碼，請記得 ！> [TraceTCP](http://simulatedsimian.github.io/tracetcp_download.html)免費下載，但依賴 Wincap。Wincap 是一種工具，也用於及安裝 Netmon。我們也會使用 Netmon 進階的方法 ＞ 一節中。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p137">TraceTCP is included in this screen shot because it's a useful tool for showing, in milliseconds, how long a request takes to process, and how many network hops, or connections from one computer to the next, that the request takes to reach a destination. TraceTCP can also give the names of servers used during hops, which can be useful to a Microsoft Office 365 troubleshooter in Support. > TraceTCP commands can be very simple, such as: >  `tracetcp.exe outlook.office365.com:443`> Remember to include the port number in the command! > [TraceTCP](http://simulatedsimian.github.io/tracetcp_download.html) is a free download, but relies on Wincap. Wincap is a tool that is also used and installed by Netmon. We also use Netmon in the advanced methods section.</span></span> 
  
 <span data-ttu-id="b94fd-p138">如果您有多個辦公室，您需要從用戶端的每個這些位置，以及保留的資料集。這項測試會測量延遲，這在此例中是說明將要求傳送至 Office 365 與 Office 365 的回應要求用戶端之間的時間量的數值。測試內部網域的用戶端電腦上，於並尋找測量從您的網路內來回輸出點，透過網際網路到 Office 365 及備份。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p138">If you have multiple offices, you'll need to keep a set of data from a client in each of those locations as well. This test measures latency, which, in this case, is a number value that describes the amount of time between a client sending a request to Office 365, and Office 365 responding to the request. The testing originates inside your domain on a client computer, and looks to measure a round trip from inside your network, out through an egress point, across the Internet to Office 365, and back.</span></span> 
  
<span data-ttu-id="b94fd-p139">有幾種處理輸出點，在此例中之 proxy 伺服器。您可以追蹤介於 1 到 2，然後 2 到 3，並接著新增若要取得您網路的邊緣的最後一個總計的毫秒數字。或者，您可以設定為近端網址不 Office 365 地址的 proxy 連線。在較大網路防火牆、 反向 proxy 或兩者的組合中，您可能需要將允許將傳遞的許多 Url 的流量的 proxy 伺服器上進行例外狀況。Office 365 所使用的端點清單中，請參閱[Office 365 Url 和 IP 位址範圍](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)。如果您已驗證的 proxy]，開始測試下列例外：</span><span class="sxs-lookup"><span data-stu-id="b94fd-p139">There are a few ways to deal with the egress point, in this case, the proxy server. You can either trace from 1 to 2 and then 2 to 3, and then add the numbers in milliseconds to get a final total to the edge of your network. Or, you can configure the connection to bypass the proxy for Office 365 addresses. In a larger network with a firewall, reverse proxy, or some combination of the two, you may need to make exceptions on the proxy server that will allow traffic to pass for a lot of URLs. For the list of endpoints used by Office 365, see [Office 365 URLs and IP address ranges](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2). If you have an authenticating proxy, begin by testing exceptions for the following:</span></span>
  
- <span data-ttu-id="b94fd-293">連接埠 80 和 443</span><span class="sxs-lookup"><span data-stu-id="b94fd-293">Ports 80 and 443</span></span>
    
- <span data-ttu-id="b94fd-294">TCP 及 HTTPs</span><span class="sxs-lookup"><span data-stu-id="b94fd-294">TCP and HTTPs</span></span>
    
- <span data-ttu-id="b94fd-295">會輸出至任何這些 Url 的連線：</span><span class="sxs-lookup"><span data-stu-id="b94fd-295">Connections that are outbound to any of these URLs:</span></span>
    
- <span data-ttu-id="b94fd-296">\*。 microsoftonline.com</span><span class="sxs-lookup"><span data-stu-id="b94fd-296">\*.microsoftonline.com</span></span>
    
- <span data-ttu-id="b94fd-297">\*.microsoftonline p.com</span><span class="sxs-lookup"><span data-stu-id="b94fd-297">\*.microsoftonline-p.com</span></span>
    
- <span data-ttu-id="b94fd-298">\*。 sharepoint.com</span><span class="sxs-lookup"><span data-stu-id="b94fd-298">\*.sharepoint.com</span></span>
    
- <span data-ttu-id="b94fd-299">\*。 outlook.com</span><span class="sxs-lookup"><span data-stu-id="b94fd-299">\*.outlook.com</span></span>
    
- <span data-ttu-id="b94fd-300">\*。 建立與 lync.com</span><span class="sxs-lookup"><span data-stu-id="b94fd-300">\*.lync.com</span></span>
    
- <span data-ttu-id="b94fd-301">osub.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="b94fd-301">osub.microsoft.com</span></span>
    
<span data-ttu-id="b94fd-p140">所有使用者都必須允許以取得這些不含任何 proxy 干擾] 或 [驗證地址。在較小的網路中，您應該新增這些至您的 proxy 略過您的網頁瀏覽器中的清單。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p140">All users need to be allowed to get to these addresses without any proxy interference or authentication. On a smaller network, you should add these to your proxy bypass list in your web browser.</span></span> 
  
<span data-ttu-id="b94fd-p141">若要新增至 proxy 略過清單這些 Internet Explorer 中，移至**工具** \> **網際網路選項** \> **連線** \> **LAN 設定** \> **進階**。[進階] 索引標籤也是找到您的 proxy 伺服器和 proxy 伺服器連接埠。您可能需要按一下核取方塊，請**使用您的區域網路使用 proxy 伺服器**，來存取 [**進階**] 按鈕。想要確定已核取 [**近端網址不使用 proxy 伺服器**。一旦您按一下 [**進階**]，您會看見您可以在此輸入例外規則] 文字方塊。分隔上列以分號分隔，例如萬用子元 Url：</span><span class="sxs-lookup"><span data-stu-id="b94fd-p141">To add these to your proxy bypass list in Internet Explorer, go to **Tools** \> **Internet Options** \> **Connections** \> **LAN settings** \> **Advanced**. The advanced tab is also where you will find your proxy server and proxy server port. You may need to click the checkbox **Use a proxy server for your LAN**, to access the **Advanced** button. You'll want to make sure that **Bypass proxy server for local addresses** is checked. Once you click **Advanced**, you'll see a text box where you can enter exceptions. Separate the wildcard URLs listed above with semi-colons, for example:</span></span>
  
<span data-ttu-id="b94fd-310">\*。 microsoftonline.com;\*。 sharepoint.com</span><span class="sxs-lookup"><span data-stu-id="b94fd-310">\*.microsoftonline.com; \*.sharepoint.com</span></span>
  
<span data-ttu-id="b94fd-p142">一旦您略過您 proxy，您應該能夠使用 ping 或 PsPing 直接在 Office 365 URL。下一個步驟會測試 ping **outlook.office365.com**。或者，如果您使用 PsPing 或另一項工具，將可讓您提供的命令，以查看平均來回時間 （毫秒） 針對**portal.microsoftonline.com:443** PsPing 連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p142">Once you bypass your proxy, you should be able to use ping or PsPing directly on an Office 365 URL. The next step will be to test ping **outlook.office365.com**. Or, if you're using PsPing or another tool that will let you supply a port number to the command, PsPing against **portal.microsoftonline.com:443** to see the average round trip time in milliseconds.</span></span> 
  
<span data-ttu-id="b94fd-p143">來回時間或 RTT 是措施需花費 like outlook.office365.com 伺服器傳送 HTTP 要求並取得回應回認可伺服器知道您並未號碼值。您有時會看見此縮寫成 RTT。這應該是較短時間量。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p143">The round trip time, or RTT, is a number value that measures how long it takes to send a HTTP request to a server like outlook.office365.com and get a response back that acknowledges the server knows that you did it. You'll sometimes see this abbreviated as RTT. This should be a relatively short amount of time.</span></span>
  
<span data-ttu-id="b94fd-317">您必須使用[PSPing](https://technet.microsoft.com/en-us/sysinternals/jj729731.aspx)或另一項工具在未使用 ICMP 封包的情況下所封鎖 Office 365 為了執行這項測試。</span><span class="sxs-lookup"><span data-stu-id="b94fd-317">You have to use [PSPing](https://technet.microsoft.com/en-us/sysinternals/jj729731.aspx) or another tool that does not use ICMP packets which are blocked by Office 365 in order to do this test.</span></span> 
  
 <span data-ttu-id="b94fd-318">**如何使用 PsPing 直接從 Office 365 URL 取得整體往返時間 （毫秒）**</span><span class="sxs-lookup"><span data-stu-id="b94fd-318">**How to use PsPing to get an overall round trip time in milliseconds directly from an Office 365 URL**</span></span>
  
1. <span data-ttu-id="b94fd-319">提高權限的命令提示字元執行，請完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="b94fd-319">Run an elevated command prompt by completing these steps:</span></span>
    
1. <span data-ttu-id="b94fd-320">按一下 [開始]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b94fd-320">Click **Start**.</span></span>
    
2. <span data-ttu-id="b94fd-321">在**開始搜尋**] 方塊中輸入 cmd，並按 CTRL + SHIFT + enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="b94fd-321">In the **Start Search** box, type cmd, and then press CTRL+SHIFT+ENTER.</span></span>
    
3. <span data-ttu-id="b94fd-322">如果**使用者帳戶控制**] 對話方塊隨即出現，確認顯示的動作是什麼，和 [**繼續]**。</span><span class="sxs-lookup"><span data-stu-id="b94fd-322">If the **User Account Control** dialog box appears, confirm that the action it displays is what you want, and then click **Continue**.</span></span>
    
2. <span data-ttu-id="b94fd-323">瀏覽至 （在此案例的 PsPing) 工具安裝所在的資料夾及測試這些 Office 365 Url：</span><span class="sxs-lookup"><span data-stu-id="b94fd-323">Navigate to the folder where the tool (in this case PsPing) is installed and test these Office 365 URLs:</span></span>
    
  - <span data-ttu-id="b94fd-324">psping portal.office.com:443</span><span class="sxs-lookup"><span data-stu-id="b94fd-324">psping portal.office.com:443</span></span>
    
  - <span data-ttu-id="b94fd-325">psping microsoft my.sharepoint.com:443</span><span class="sxs-lookup"><span data-stu-id="b94fd-325">psping microsoft-my.sharepoint.com:443</span></span>
    
  - <span data-ttu-id="b94fd-326">psping outlook.office365.com:443</span><span class="sxs-lookup"><span data-stu-id="b94fd-326">psping outlook.office365.com:443</span></span>
    
  - <span data-ttu-id="b94fd-327">psping www.yammer.com:443</span><span class="sxs-lookup"><span data-stu-id="b94fd-327">psping www.yammer.com:443</span></span>
    
    ![移至 microsoft my.sharepoint.com 連接埠 443 PSPing 命令。](media/3258f620-4513-4e82-95c9-06b387fc3a82.PNG)
  
<span data-ttu-id="b94fd-p144">請務必包含 443 的連接埠號碼。請記住 Office 365 適用於加密的通道。如果您沒有連接埠號碼 PsPing，您的要求將會失敗。一旦您已經 ping 貴少數、 尋找毫秒 (ms) 的平均時間。這是您想要記錄 ！</span><span class="sxs-lookup"><span data-stu-id="b94fd-p144">Be sure to include the port number of 443. Remember that Office 365 works on an encrypted channel. If you PsPing without the port number, your request will fail. Once you've pinged your short list, look for the Average time in milliseconds (ms). That is what you want to record!</span></span>
  
![圖形顯示圖例的用戶端 proxy PSPing 的 2.8 毫秒的來回時間。](media/96901aea-1093-4f1b-b5a3-6078e9035e6c.png)
  
<span data-ttu-id="b94fd-p145">如果您不熟悉 proxy 旁路閱讀並希望逐步的事項，必須先了解 proxy 伺服器的名稱。在 Internet Explorer 中移至**工具** \> **網際網路選項** \> **連線** \> **LAN 設定** \> **進階**。[**進階**] 索引標籤是您將會看到您所列的 proxy 伺服器的位置。Ping 命令提示字元的 proxy 伺服器來完成這項工作：</span><span class="sxs-lookup"><span data-stu-id="b94fd-p145">If you're not familiar with proxy bypass, and prefer to take things step-by-step, you need to first find out the name of your proxy server. In Internet Explorer go to **Tools** \> **Internet Options** \> **Connections** \> **LAN settings** \> **Advanced**. The **Advanced** tab is where you will see your proxy server listed. Ping that proxy server at a command prompt by completing this task:</span></span> 
  
 <span data-ttu-id="b94fd-339">**Ping proxy 伺服器並取得階段 1 到 2 以毫秒為單位的來回值**</span><span class="sxs-lookup"><span data-stu-id="b94fd-339">**To ping the proxy server and get a round trip value in milliseconds for stage 1 to 2**</span></span>
  
1. <span data-ttu-id="b94fd-340">提高權限的命令提示字元執行，請完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="b94fd-340">Run an elevated command prompt by completing these steps:</span></span>
    
1. <span data-ttu-id="b94fd-341">按一下 [開始]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b94fd-341">Click **Start**.</span></span>
    
2. <span data-ttu-id="b94fd-342">在**開始搜尋**] 方塊中輸入 cmd，並按 CTRL + SHIFT + enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="b94fd-342">In the **Start Search** box, type cmd, and then press CTRL+SHIFT+ENTER.</span></span>
    
3. <span data-ttu-id="b94fd-343">如果**使用者帳戶控制**] 對話方塊隨即出現，確認顯示的動作是什麼，和 [**繼續]**。</span><span class="sxs-lookup"><span data-stu-id="b94fd-343">If the **User Account Control** dialog box appears, confirm that the action it displays is what you want, and then click **Continue**.</span></span>
    
2. <span data-ttu-id="b94fd-p146">輸入 ping \<proxy 伺服器的名稱在瀏覽器使用或 proxy 伺服器的 IP 位址\>，然後按 ENTER。如果您有 PsPing 或一些其他工具，安裝，您可以選擇改用該工具。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p146">Type ping \<the name of the proxy server your browser uses, or the IP address of the proxy server\> and then press ENTER. If you have PsPing, or some other tool, installed, you can choose to use that tool instead.</span></span> 
    
    <span data-ttu-id="b94fd-346">您的命令可能看起來任何這些範例：</span><span class="sxs-lookup"><span data-stu-id="b94fd-346">Your command may look like any of these examples:</span></span> 
    
  - <span data-ttu-id="b94fd-347">ping ourproxy.ourdomain.industry.business.com</span><span class="sxs-lookup"><span data-stu-id="b94fd-347">ping ourproxy.ourdomain.industry.business.com</span></span>
    
  - <span data-ttu-id="b94fd-348">ping 155.55.121.55</span><span class="sxs-lookup"><span data-stu-id="b94fd-348">ping 155.55.121.55</span></span>
    
  - <span data-ttu-id="b94fd-349">ping ourproxy</span><span class="sxs-lookup"><span data-stu-id="b94fd-349">ping ourproxy</span></span>
    
  - <span data-ttu-id="b94fd-350">psping ourproxy.ourdomain.industry.business.com:80</span><span class="sxs-lookup"><span data-stu-id="b94fd-350">psping ourproxy.ourdomain.industry.business.com:80</span></span>
    
  - <span data-ttu-id="b94fd-351">psping 155.55.121.55:80</span><span class="sxs-lookup"><span data-stu-id="b94fd-351">psping 155.55.121.55:80</span></span>
    
  - <span data-ttu-id="b94fd-352">psping ourproxy:80</span><span class="sxs-lookup"><span data-stu-id="b94fd-352">psping ourproxy:80</span></span>
    
3. <span data-ttu-id="b94fd-p147">當追蹤停止傳送測試封包時，您將取得小型摘要列出平均 （毫秒），而您正在後的值。採取的螢幕擷取畫面提示並儲存其使用您的命名慣例。此時它也可能會說明在圖表中的值填滿。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p147">When the trace stops sending test packets, you'll get a small summary that lists an average, in milliseconds, and that's the value you're after. Take a screen shot of the prompt and save it using your naming convention. At this point it may also help to fill in the diagram with the value.</span></span>
    
<span data-ttu-id="b94fd-p148">也許您已在早期早上、 過追蹤與您的用戶端可以快速取得 proxy （或任何輸出伺服器結束網際網路）。在此例中，您的號碼可能看起來如下：</span><span class="sxs-lookup"><span data-stu-id="b94fd-p148">Maybe you've taken a trace in the early morning, and your client can get to the proxy (or whatever egress server exits to the Internet) quickly. In this case, your numbers may look like this:</span></span>
  
![圖形所顯示的來回時間從用戶端的 2.8 毫秒 proxy。](media/1bd03544-23fc-47d4-bbae-c1feb466a5d8.PNG)
  
<span data-ttu-id="b94fd-p149">如果您的用戶端電腦是其中一個選取的一些 proxy （或輸出） 伺服器的存取權，您可以將測試下一個計量執行透過遠端連線到該電腦，以從該處至 Office 365 URL PsPing 執行命令提示字元。如果您沒有該電腦的存取權，您可以連絡您的網路資源的下一個 leg 的說明及取得確切數字的方式。如果不可行，需要有問題 PsPing 針對 Office 365 URL 和比較 proxy 伺服器 PsPing 或 Ping 時間。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p149">If your client computer is one of the select few with access to the proxy (or egress) server, you can run the next leg of the test by remotely connecting to that computer, running the command prompt to PsPing to an Office 365 URL from there. If you don't have access to that computer, you can contact your network resources for help with the next leg and get exact numbers that way. If that's not possible, take a PsPing against the Office 365 URL in question and compare it to the PsPing or Ping time against your proxy server.</span></span> 
  
<span data-ttu-id="b94fd-p150">例如，如果您有 51.84 （毫秒） 從用戶端至 Office 365 URL，且您具有 2.8 （毫秒） 從用戶端 proxy （或輸出點），然後您必須 49.04 （毫秒） 從輸出至 Office 365。同樣地，如果您有的 12.25 （毫秒） 從用戶端 proxy PsPing 期間日和 62.01 （毫秒） 從用戶端的 Office 365 url 的高度，然後 proxy 輸出至 Office 365 URL 您平均值為 49.76 （毫秒）。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p150">For example, if you have 51.84 milliseconds from the client to the Office 365 URL, and you have 2.8 milliseconds from the client to the proxy (or egress point), then you have 49.04 milliseconds from the egress to Office 365. Likewise, if you have a PsPing of 12.25 milliseconds from the client to the proxy during the height of the day, and 62.01 milliseconds from the client to the Office 365 URL, then your average value for the proxy egress to the Office 365 URL is 49.76 milliseconds.</span></span>
  
![其他張顯示圖形 ping （毫秒） 從用戶端 proxy 旁邊至 Office 365 的用戶端讓會減去值。](media/cd764e77-5154-44ba-a5cd-443a628eb2d9.PNG)
  
<span data-ttu-id="b94fd-p151">方面的疑難排解，您可能會發現只從保留這些基準有趣的某個項目。例如，如果您發現通常有關於 40 至 59 毫秒的延遲 proxy 或輸出指向 Office 365 URL 且 proxy 或輸出點延遲約 3 到 7 （毫秒） 的用戶端 (根據量網路流量您正在 seein在一天中的這段期間 g) 那麼您一定會知道有問題如果 proxy 或輸出基準線最後三個用戶端顯示的 45 毫秒延遲。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p151">In terms of troubleshooting, you may find something interesting just from keeping these baselines. For example, if you find that you generally have about 40 to 59 milliseconds of latency from the proxy or egress point to the Office 365 URL, and have a client to proxy or egress point latency of about 3 to 7 milliseconds (depending on the amount network traffic you're seeing during that time of day) then you will surely know something is problematic if your last three client to proxy or egress baselines show a latency of 45 milliseconds.</span></span>
  
### <a name="advanced-methods"></a><span data-ttu-id="b94fd-367">進階的方法</span><span class="sxs-lookup"><span data-stu-id="b94fd-367">Advanced methods</span></span>

<span data-ttu-id="b94fd-p152">如果您真的要知道有什麼新鮮事網際網路要求至 Office 365，您需要熟悉網路追蹤。不拘您偏好的這些追蹤 HTTPWatch、 Netmon、 訊息 Analyzer、 Wireshark、 Fiddler、 開發人員儀表板工具哪些工具或其他任何將執行只要該工具可擷取及篩選網路流量。您會看到此區段中它是執行多個這些工具，以取得更完整的問題圖片有用。當您正在測試時，這些工具的一些也會充當他們自己的右邊的 proxy。[效能疑難排解 Office 365 計劃](performance-troubleshooting-plan.md)、 隨附文章中所使用的工具包括[Netmon 3.4](https://www.microsoft.com/en-us/download/details.aspx?id=4865)、 [HTTPWatch](https://www.httpwatch.com/download/)或[WireShark](https://www.wireshark.org/)。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p152">If you really want to know what is happening with your Internet requests to Office 365, you need to become familiar with network traces. It does not matter which tools you prefer for these traces, HTTPWatch, Netmon, Message Analyzer, Wireshark, Fiddler, Developer Dashboard tool or any other will do as long as that tool can capture and filter network traffic. You'll see in this section that it's beneficial to run more than one of these tools to get a more complete picture of the problem. When you're testing, some of these tools also act as proxies in their own right. Tools used in the companion article, [Performance troubleshooting plan for Office 365](performance-troubleshooting-plan.md), include [Netmon 3.4](https://www.microsoft.com/en-us/download/details.aspx?id=4865), [HTTPWatch](https://www.httpwatch.com/download/), or [WireShark](https://www.wireshark.org/).</span></span>
  
<span data-ttu-id="b94fd-p153">利用效能比較基準是這種方法的簡單一部分且的許多步驟相同時疑難排解效能問題。建立效能的基準線的更進階的方法需要進行並儲存網路追蹤。充分運用本文中的範例使用 SharePoint Online、 但您應該跨您訂閱測試並記錄在 Office 365 服務開發的常見的動作清單。以下是基準範例：</span><span class="sxs-lookup"><span data-stu-id="b94fd-p153">Taking a performance baseline is the simple part of this method, and many of the steps are the same as when you troubleshoot a performance issue. The more advanced methods of creating baselines for performance requires you to take and store network traces. Most of the examples in this article use SharePoint Online, but you should develop a list of common actions across the Office 365 services to which you subscribe to test and record. Here is a baseline example:</span></span>
  
- <span data-ttu-id="b94fd-p154">[比較基準清單以進行 SPO-\* \* 步驟 1： \* \* 瀏覽] 首頁的 SPO 網站並執行網路追蹤。儲存追蹤。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p154">Baseline list for SPO - \*\* Step 1: \*\* Browse the home page of the SPO website and do a network trace. Save the trace.</span></span> 
    
- <span data-ttu-id="b94fd-p155">[比較基準清單以進行 SPO-**步驟 2：** 搜尋字詞 （例如您公司的名稱） 透過企業搜尋及執行網路追蹤。儲存追蹤。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p155">Baseline list for SPO - **Step 2:** Search for a term (such as your company name) via Enterprise Search and do a network trace. Save the trace.</span></span> 
    
- <span data-ttu-id="b94fd-p156">[比較基準清單以進行 SPO-**步驟 3:** 上傳至 SharePoint Online 的文件庫及執行網路追蹤的大型檔案。儲存追蹤。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p156">Baseline list for SPO - **Step 3:** Upload a large file to a SharePoint Online document library and do a network trace. Save the trace.</span></span> 
    
- <span data-ttu-id="b94fd-p157">[比較基準清單以進行 SPO-**步驟 4:** 瀏覽] 首頁的 OneDrive 網站並執行網路追蹤。儲存追蹤。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p157">Baseline list for SPO - **Step 4:** Browse the home page of the OneDrive website and do a network trace. Save the trace.</span></span> 
    
<span data-ttu-id="b94fd-p158">這份清單應該包含使用者採取針對 SharePoint Online 的最重要常見動作。請注意最後一個步驟中的，以追蹤移至 OneDrive for Business，組建入 SharePoint Online 首頁 （這通常自訂的公司） 的負載及比較 OneDrive for Business 首頁上，而很少自訂。這是非常基本測試而言慢載入 SharePoint Online 網站。您可以將您的測試建置記錄的此差異。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p158">This list should include the most important common actions that users take against SharePoint Online. Notice that the last step, to trace going to OneDrive for Business, builds-in a comparison between the load of the SharePoint Online home page (which is often customized by companies) and OneDrive for Business home page, which is seldom customized. This is a very basic test when it comes to a slow-loading SharePoint Online site. You can build a record of this difference into your testing.</span></span>
  
<span data-ttu-id="b94fd-p159">如果您是中間效能問題，許多項步驟都相同時進行比較基準。網路追蹤會成為重要，因此我們將會*如何*要採取的重要追蹤後續處理。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p159">If you are in the middle of a performance problem, many of the steps are the same as when taking a baseline. Network traces become critical, so we'll handle  *how*  to take the important traces next.</span></span> 
  
<span data-ttu-id="b94fd-p160">若要解決效能問題，*現在*，您需要在您遭遇效能問題的時間進行追蹤。您需要有適當的工具可收集記錄，請與您需要的動作計劃，亦即疑難排解清單來收集最佳資訊可以協助您需要採取的動作。首先要為記錄的日期和時間的測試，以便反映 timing 資料夾中可以儲存檔案。接下來，縮小至其本身的問題步驟。這些是您要用於測試的確切步驟。記得基本概念： 只能與 Outlook 問題時，請確定只有一個 Office 365 服務中發生的問題行為的記錄。關閉此問題的範圍縮小可協助您以專注於您可以解決所發生的某個項目。</span><span class="sxs-lookup"><span data-stu-id="b94fd-p160">To tackle a performance problem,  *right now*  , you need to be taking a trace at the time you are experiencing the performance issue. You need to have the proper tools available to gather logs, and you need an action plan, that is, a list of troubleshooting actions to take to gather the best information that you can. The first thing to do is record the date and time of the test so that the files can be saved in a folder that reflect the timing. Next, narrow down to the problem steps themselves. These are the exact steps you will use for testing. Don't forget the basics: if the issue is only with Outlook, make sure to record that the problem behavior happens in only one Office 365 service. Narrowing down the scope of this issue will help you to focus on something you can resolve.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="b94fd-398">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b94fd-398">See also</span></span>

[<span data-ttu-id="b94fd-399">管理 Office 365 端點</span><span class="sxs-lookup"><span data-stu-id="b94fd-399">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)

