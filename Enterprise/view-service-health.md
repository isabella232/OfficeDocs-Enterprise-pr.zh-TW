---
title: 如何檢查 Office 365 服務健康狀況
ms.author: kfollis
author: kfollis
manager: scotv
ms.date: 6/15/2018
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365P_ServiceHealthModern
- O365M_ServiceHealthModern
- O365E_ViewStatusServices
- O365E_ServiceHealthModern
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
- IWA160
ms.assetid: 932ad3ad-533c-418a-b938-6e44e8bc33b0
description: 檢視 Office 365 服務的健康狀態之前呼叫支援以查看是否有作用中服務中斷
ms.openlocfilehash: d01fe8e269ace922ab92cca779d6f8fea8b6802e
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539991"
---
# <a name="how-to-check-office-365-service-health"></a><span data-ttu-id="ebe1d-103">如何檢查 Office 365 服務健康狀況</span><span class="sxs-lookup"><span data-stu-id="ebe1d-103">How to check Office 365 service health</span></span>

<span data-ttu-id="ebe1d-p101">您可以在 Office 365 中檢視 Office 365、 Yammer、 Microsoft Dynamics CRM、 及 Microsoft Intune 雲端服務的健康狀況 * * 服務健康狀況 * * 在管理中心頁面。如果您遭遇到雲端服務的問題，您可以檢查服務健康狀況來判斷再連絡支援或花費時間疑難排解這是進行中的解析度的已知的問題。</span><span class="sxs-lookup"><span data-stu-id="ebe1d-p101">You can view the health of Office 365, Yammer, Microsoft Dynamics CRM, and Microsoft Intune cloud services on the Office 365 ** Service health ** page in the admin center. If you are experiencing problems with a cloud service, you can check the service health to determine whether this is a known issue with a resolution in progress before you call support or spend time troubleshooting.</span></span> 
  
### <a name="how-to-check-service-health"></a><span data-ttu-id="ebe1d-106">如何檢查服務健康狀況</span><span class="sxs-lookup"><span data-stu-id="ebe1d-106">How to check service health</span></span>

1. <span data-ttu-id="ebe1d-107">移至 [[https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage)和登入管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="ebe1d-107">Go to [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) and sign in with an admin account.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="ebe1d-p102">全域管理員或服務系統管理員角色指派的人可以檢視服務健康狀況。若要允許 Exchange、 SharePoint 和 Skype 的商務系統管理員檢視服務健康狀況，他們必須也指派服務系統管理員角色。</span><span class="sxs-lookup"><span data-stu-id="ebe1d-p102">People who are assigned the global admin or service administrator role can view service health. To allow Exchange, SharePoint, and Skype for Business admins to view service health, they must also be assigned the Service admin role.</span></span> 
  
2. <span data-ttu-id="ebe1d-p103">若要開啟 [服務健康狀況系統管理中心中，移至 [**健康情況** \> **服務健康狀況**或按一下 [服務健康狀況卡片首頁儀表板。儀表板卡片會指出是否有作用中服務問題以及詳細的服務健康狀況] 頁面的連結。</span><span class="sxs-lookup"><span data-stu-id="ebe1d-p103">To open service health, in the admin center, go to **Health** \> **Service health**, or click the Service health card on the Home dashboard. The dashboard card indicates whether there is an active service issue and links to the detailed service health page.</span></span>
    
    ![服務健康狀況的儀表板卡片](media/8ae3de43-7bd5-4ee9-90ed-8b5ba5f9b474.png)
  
3. <span data-ttu-id="ebe1d-113">圖示的表格格式顯示每個雲端服務的健全狀況狀態指出可能的狀態。</span><span class="sxs-lookup"><span data-stu-id="ebe1d-113">The health state of each cloud service is shown in a table format with an icon to indicate possible states.</span></span>
    
> [!TIP]
> <span data-ttu-id="ebe1d-114">您也可以使用行動裝置上的[Office 365 系統應用程式](https://go.microsoft.com/fwlink/p/?linkid=627216)來檢視這是更好的方式來保持最新的推入通知服務健康狀況。</span><span class="sxs-lookup"><span data-stu-id="ebe1d-114">You can also use the [Office 365 Admin app](https://go.microsoft.com/fwlink/p/?linkid=627216) on your mobile device to view Service health, which is a great way to stay current with push notifications.</span></span> 
  
### <a name="view-details-of-posted-service-health"></a><span data-ttu-id="ebe1d-115">檢視已發佈的服務健康狀況的詳細資料</span><span class="sxs-lookup"><span data-stu-id="ebe1d-115">View details of posted service health</span></span>

<span data-ttu-id="ebe1d-p104">在預設檢視中，會顯示所有服務和及其目前健全狀態。若要篩選服務目前遭遇事件您檢視，請從在左邊的灰色列選取**事件**。選取 [**摘要報告**會顯示目前已發佈的摘要報告的服務。從**所有服務**] 檢視中，按一下顯示的服務狀態將會開啟諮詢或事件的摘要檢視。</span><span class="sxs-lookup"><span data-stu-id="ebe1d-p104">In the default view, all services and their current health state are displayed. To filter your view to services currently experiencing an incident, select **Incidents** from the shaded bar on the left. Selecting **Advisories** will show only services that currently have an advisory posted. From the **All services** view, clicking the displayed service state will open a summary view of the advisory or incident.</span></span> 
  
![服務健康狀況中的目前問題的檢視](media/f829a3af-1aca-4dc2-97eb-15d805349b24.png)
  
<span data-ttu-id="ebe1d-121">諮詢或摘要事件會提供下列資訊：</span><span class="sxs-lookup"><span data-stu-id="ebe1d-121">The advisory or incident summary provides the following information:</span></span> 
  
![螢幕擷取畫面顯示標籤服務摘要報告中的欄位](media/0dd6065c-1381-4a5c-8ca0-854c3e043a5c.png)
  
1. <span data-ttu-id="ebe1d-123">問題識別碼和摘要陳述式的問題。</span><span class="sxs-lookup"><span data-stu-id="ebe1d-123">An issue identifier and summary statement of the problem.</span></span>
    
2. <span data-ttu-id="ebe1d-p105">目前的狀態。請參閱本文中的每個可能的狀態說明中的狀態定義。</span><span class="sxs-lookup"><span data-stu-id="ebe1d-p105">The current status. See status definitions in this article for an explanation of each potential status.</span></span>
    
3. <span data-ttu-id="ebe1d-126">此問題影響使用者描述。</span><span class="sxs-lookup"><span data-stu-id="ebe1d-126">A description of how this issue can affect users.</span></span>
    
4. <span data-ttu-id="ebe1d-p106">問題已開始時間和上次更新服務健康狀況訊息。整個持續時間內發生問題我們張貼經常訊息可讓您知道我們正在進行中套用解決方案的進度。</span><span class="sxs-lookup"><span data-stu-id="ebe1d-p106">The time that the issue was started and the last time that the service health message was updated. Throughout the duration of an issue we post frequent messages to let you know the progress that we're making in applying a solution.</span></span>
    
5. <span data-ttu-id="ebe1d-129">選取 [**顯示詳細資料**] 連結以查看問題，包括所有從張貼的訊息時我們將解決方案上工作的歷程記錄的相關詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="ebe1d-129">Select the **Show details** link to see more details about the issue, including the history of all messages posted while we work on a solution.</span></span> 
    
### <a name="translate-service-health-details"></a><span data-ttu-id="ebe1d-130">翻譯服務健康狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="ebe1d-130">Translate service health details</span></span>

<span data-ttu-id="ebe1d-p107">因為服務健康狀況說明會張貼在即時、 至您的語言不自動翻譯服務事件的詳細資訊僅都會以英文顯示。若要翻譯的說明，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="ebe1d-p107">Because service health explanations are posted in real-time, they are not automatically translated to your language and the details of a service event are in English only. To translate the explanation, follow these steps:</span></span>
  
1. <span data-ttu-id="ebe1d-133">移至[轉譯器](https://www.bing.com/translator/)。</span><span class="sxs-lookup"><span data-stu-id="ebe1d-133">Go to [Translator](https://www.bing.com/translator/).</span></span>
    
2. <span data-ttu-id="ebe1d-p108">在 [**服務健康狀況**] 頁面上選取的事件或摘要報告。在 [**顯示詳細資料**] 將複製的相關問題的文字。</span><span class="sxs-lookup"><span data-stu-id="ebe1d-p108">On the **Service health** page, select an incident or advisory. Under **Show details**, copy the text about the issue.</span></span>
    
3. <span data-ttu-id="ebe1d-136">轉譯器，在貼上文字，並選擇**翻譯**。</span><span class="sxs-lookup"><span data-stu-id="ebe1d-136">In Translator, paste the text and choose **Translate**.</span></span>
    
### <a name="definitions"></a><span data-ttu-id="ebe1d-137">定義</span><span class="sxs-lookup"><span data-stu-id="ebe1d-137">Definitions</span></span>

<span data-ttu-id="ebe1d-p109">大部分的時間服務沒有進一步資訊會顯示為狀況良好。當服務有問題時，問題識別為 [諮詢] 或 [事件並顯示目前的狀態。</span><span class="sxs-lookup"><span data-stu-id="ebe1d-p109">Most of the time services will appear as healthy with no further information. When a service is having a problem, the issue is identified as either an advisory or an incident and shows a current status.</span></span>
  
> [!TIP]
> <span data-ttu-id="ebe1d-p110">計劃的維護事件不會顯示在 [服務健康狀況。您可以藉由保持最新**訊息中心**追蹤計劃的維護事件。篩選郵件分類為 「 了解變更時要發生、 其生效及如何準備其變更的規劃。如需詳細資訊，請參閱[Office 365 中的訊息中心](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093)。</span><span class="sxs-lookup"><span data-stu-id="ebe1d-p110">Planned maintenance events aren't shown in service health. You can track planned maintenance events by staying up to date with the **Message center**. Filter to messages categorized as Plan for change to find out when the change is going to happen, its effect, and how to prepare for it. See [Message center in Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) for more details.</span></span> 
  
### <a name="incidents-and-advisories"></a><span data-ttu-id="ebe1d-144">事件與摘要報告</span><span class="sxs-lookup"><span data-stu-id="ebe1d-144">Incidents and advisories</span></span>

|||
|:-----|:-----|
|![資訊圖示的摘要報告](media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|<span data-ttu-id="ebe1d-p111">如果服務有顯示摘要報告，我們要知道有問題影響某些使用者，但是仍然可以使用服務。在摘要報告，通常是因應措施之問題並問題可能是間歇性或限制在範圍和使用者的影響。</span><span class="sxs-lookup"><span data-stu-id="ebe1d-p111">If a service has an advisory shown, we are aware of a problem that is affecting some users, but the service is still available. In an advisory, there is often a workaround to the problem and the problem may be intermittent or is limited in scope and user impact.</span></span>  <br/> |
|![驚嘆號圖示的事件](media/a636db57-6083-44dc-bbd5-556850804f17.png)|<span data-ttu-id="ebe1d-p112">服務若沒有顯示作用中事件，它的重大問題且服務] 或 [服務的主要函數則無法使用。例如，使用者可能無法傳送及接收電子郵件或無法登入事件不會有明顯影響的使用者。如果進行中事件，我們會提供有關將正在調查、 減輕工作及服務健康狀況儀表板中的解決方法確認更新。</span><span class="sxs-lookup"><span data-stu-id="ebe1d-p112">If a service has an active incident shown, it's a critical issue and the service or a major function of the service is unavailable. For example, users may be unable to send and receive email or unable to sign-in. Incidents will have noticeable impact to users. When there is an incident in progress, we will provide updates regarding the investigation, mitigation efforts, and confirmation of resolution in the Service health dashboard.</span></span>  <br/> |
   
### <a name="status-definitions"></a><span data-ttu-id="ebe1d-153">狀態定義</span><span class="sxs-lookup"><span data-stu-id="ebe1d-153">Status definitions</span></span>

<span data-ttu-id="ebe1d-154">| |</span><span class="sxs-lookup"><span data-stu-id="ebe1d-154"></span></span>
|<span data-ttu-id="ebe1d-155">**狀態**</span><span class="sxs-lookup"><span data-stu-id="ebe1d-155">**Status**</span></span>|<span data-ttu-id="ebe1d-156">**定義**</span><span class="sxs-lookup"><span data-stu-id="ebe1d-156">**Definition**</span></span>|
|:-----|:-----|
|<span data-ttu-id="ebe1d-157">調查</span><span class="sxs-lookup"><span data-stu-id="ebe1d-157">Investigating</span></span>  <br/> |<span data-ttu-id="ebe1d-158">我們知道潛在的問題，所收集項目將要及影響的範圍的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="ebe1d-158">We're aware of a potential issue and are gathering more information about what's going on and the scope of impact.</span></span>  <br/> |
|<span data-ttu-id="ebe1d-159">服務衰退</span><span class="sxs-lookup"><span data-stu-id="ebe1d-159">Service degradation</span></span>  <br/> |<span data-ttu-id="ebe1d-p113">我們已確認有可能會影響服務或功能的使用發生問題。如果服務正在執行較平日緩慢，您可能會看到此狀態、 有間歇性中斷或如果功能無法運作，例如。</span><span class="sxs-lookup"><span data-stu-id="ebe1d-p113">We've confirmed that there is an issue that may affect use of a service or feature. You might see this status if a service is performing more slowly than usual, there are intermittent interruptions, or if a feature isn't working, for example.</span></span>  <br/> |
|<span data-ttu-id="ebe1d-162">服務中斷</span><span class="sxs-lookup"><span data-stu-id="ebe1d-162">Service interruption</span></span>  <br/> |<span data-ttu-id="ebe1d-p114">如果我們判斷問題影響使用者存取之服務的功能將會看到此狀態。在此例中問題重要及可一致地重現。</span><span class="sxs-lookup"><span data-stu-id="ebe1d-p114">You'll see this status if we determine that an issue affects the ability for users to access the service. In this case, the issue is significant and can be reproduced consistently.</span></span>  <br/> |
|<span data-ttu-id="ebe1d-165">還原服務</span><span class="sxs-lookup"><span data-stu-id="ebe1d-165">Restoring service</span></span>  <br/> |<span data-ttu-id="ebe1d-166">已識別問題的原因，我們知道要採取、 的更正動作及正在將服務移回至狀況良好狀態。</span><span class="sxs-lookup"><span data-stu-id="ebe1d-166">The cause of the issue has been identified, we know what corrective action to take, and are in the process of bringing the service back to a healthy state.</span></span>  <br/> |
|<span data-ttu-id="ebe1d-167">延伸的復原</span><span class="sxs-lookup"><span data-stu-id="ebe1d-167">Extended recovery</span></span>  <br/> |<span data-ttu-id="ebe1d-p115">此狀態表示更正動作還原 service 大部分的使用者進行中，但會花一些時間來達到所有受影響的系統。如果我們已進行修正時要套用的永久修正我們等候減少影響是暫時性，您也可能會看到此狀態。</span><span class="sxs-lookup"><span data-stu-id="ebe1d-p115">This status indicates that corrective action is in progress to restore service to most users but will take some time to reach all the affected systems. You might also see this status if we've made a temporary fix to reduce impact while we wait to apply a permanent fix.</span></span>  <br/> |
|<span data-ttu-id="ebe1d-170">將正在調查暫停</span><span class="sxs-lookup"><span data-stu-id="ebe1d-170">Investigation suspended</span></span>  <br/> |<span data-ttu-id="ebe1d-p116">如果我們詳細將正在調查的潛在的問題會產生可讓我們進一步調查從客戶的其他資訊的要求，您會看見此狀態。如果我們需要您採取動作，我們會讓您知道我們需要何種資料或記錄檔。</span><span class="sxs-lookup"><span data-stu-id="ebe1d-p116">If our detailed investigation of a potential issue results in a request for additional information from customers to allow us to investigate further, you'll see this status. If we need you to act, we'll let you know what data or logs we need.</span></span>  <br/> |
|<span data-ttu-id="ebe1d-173">還原服務</span><span class="sxs-lookup"><span data-stu-id="ebe1d-173">Service restored</span></span>  <br/> |<span data-ttu-id="ebe1d-p117">我們已確認更正動作已解決基礎問題及服務還原為正常狀態。若要瞭解什麼發生錯誤，檢視問題詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ebe1d-p117">We've confirmed that corrective action has resolved the underlying problem and the service has been restored to a healthy state. To find out what went wrong, view the issue details.</span></span>  <br/> |
   
## <a name="history"></a><span data-ttu-id="ebe1d-176">[歷程記錄] </span><span class="sxs-lookup"><span data-stu-id="ebe1d-176">History</span></span>

<span data-ttu-id="ebe1d-p118">服務健康狀況可讓您查看目前的健全狀況狀態及檢視過去 30 天中的任何服務摘要報告和事件的歷程記錄。若要檢視所有服務的過去狀況，選取 [**服務健康狀況**] 頁面上的 [**檢視歷程記錄**]。</span><span class="sxs-lookup"><span data-stu-id="ebe1d-p118">Service health lets you look at current health status and view the history of any service advisories and incidents in the past 30 days. To view the past health of all services, select **View history** on the **Service health** page.</span></span> 
  
![顯示連結至狀況歷程記錄](media/12a3e484-1eb4-497f-8cab-8064bccc2ef5.png)
  
<span data-ttu-id="ebe1d-180">發佈選定的時間範圍中的所有服務狀況訊息清單隨即顯示，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ebe1d-180">A list of all service health messages posted in the selected timeframe is displayed, as shown below:</span></span>
  
![檢視服務健康狀況歷程記錄](media/5ed20247-121c-4abe-9fe7-9025e26a2d0e.png)
  
<span data-ttu-id="ebe1d-p119">您可能會過去 7 天或過去 30 天內檢視狀況歷程記錄。選取 [檢視有關該問題的詳細資訊的任何資料列。</span><span class="sxs-lookup"><span data-stu-id="ebe1d-p119">You may view the health history for either the last 7 days or last 30 days. Select any row to view more details about that issue.</span></span>
  
<span data-ttu-id="ebe1d-184">如需上線時間百分比我們承諾的詳細資訊，請參閱[透明作業來自 Office 365](https://go.microsoft.com/fwlink/?linkid=848695)。</span><span class="sxs-lookup"><span data-stu-id="ebe1d-184">For more information about our commitment to uptime, see [Transparent operations from Office 365](https://go.microsoft.com/fwlink/?linkid=848695).</span></span>
  
## <a name="leave-feedback"></a><span data-ttu-id="ebe1d-185">保留意見反應</span><span class="sxs-lookup"><span data-stu-id="ebe1d-185">Leave feedback</span></span>

<span data-ttu-id="ebe1d-p120">我們的目標是確定我們提供給您的進行中的問題的相關資訊的即時、 正確，且很有用。若要告訴我們如何我們進行中，選取星星評等。您提供給我們分數介於 1 至 5 顆星之後，您可以在任何特定的詳細資訊提供意見反應。我們將使用您的意見反應來微調我們服務健康狀況的系統。</span><span class="sxs-lookup"><span data-stu-id="ebe1d-p120">Our goal is to make sure that the information we provide to you about an ongoing issue is timely, accurate, and useful. To tell us how we're doing, select a star rating. After you give us a score from 1 to 5 stars, you can give feedback on any specific details. We'll use your feedback to fine-tune our service health system.</span></span>
  
![服務健康狀況問題的意見反應表單](media/fd083fdb-fde8-47b4-9136-b90d1d003864.png)
  
## <a name="see-also"></a><span data-ttu-id="ebe1d-191">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ebe1d-191">See also</span></span>

[<span data-ttu-id="ebe1d-192">Office 365 系統管理中心中的活動報告</span><span class="sxs-lookup"><span data-stu-id="ebe1d-192">Activity Reports in the Office 365 admin center</span></span>](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)

