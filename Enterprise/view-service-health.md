---
title: 如何檢查 Office 365 服務健康情況
ms.author: robmazz
author: robmazz
manager: laurawi
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
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
- IWA160
ms.assetid: 932ad3ad-533c-418a-b938-6e44e8bc33b0
description: 檢視 Office 365 服務的健康狀態之前呼叫支援以查看是否有作用中服務中斷
ms.openlocfilehash: 7a8d6c028caa72d332a51123233b2d0642311da0
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085292"
---
# <a name="how-to-check-office-365-service-health"></a><span data-ttu-id="812c1-103">如何檢查 Office 365 服務健康情況</span><span class="sxs-lookup"><span data-stu-id="812c1-103">How to check Office 365 service health</span></span>

<span data-ttu-id="812c1-p101">您可以檢視系統管理中心的 [Office 365**服務健康狀況**] 頁面上的 Office 365、 Yammer、 Microsoft Dynamics CRM、 及 Microsoft Intune 雲端服務的狀況。如果您遭遇到雲端服務的問題，您可以檢查服務健康狀況來判斷再連絡支援或花費時間疑難排解這是進行中的解析度的已知的問題。</span><span class="sxs-lookup"><span data-stu-id="812c1-p101">You can view the health of Office 365, Yammer, Microsoft Dynamics CRM, and Microsoft Intune cloud services on the Office 365 **Service health** page in the admin center. If you are experiencing problems with a cloud service, you can check the service health to determine whether this is a known issue with a resolution in progress before you call support or spend time troubleshooting.</span></span> 

<span data-ttu-id="812c1-106">如果您無法登入服務入口網站，您可以使用[服務狀態] 頁面](https://status.office365.com)以檢查防止您無法登入您的租用戶的已知問題。</span><span class="sxs-lookup"><span data-stu-id="812c1-106">If you are unable to sign in to the service portal, you can use the [service status page](https://status.office365.com) to check for known issues preventing you from logging into your tenant.</span></span>
  
### <a name="how-to-check-service-health"></a><span data-ttu-id="812c1-107">如何查看服務健康情況</span><span class="sxs-lookup"><span data-stu-id="812c1-107">How to check service health</span></span>

1. <span data-ttu-id="812c1-108">移至 [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage)，並以系統管理員帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="812c1-108">Go to [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) and sign in with an admin account.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="812c1-p102">被指派全域系統管理員或服務系統管理員角色的人員方可檢視服務健康情況。若要允許 Exchange、SharePoint 以及商務用 Skype 管理員檢視服務健康情況，必須同時將服務系統管理員角色指派給他們。</span><span class="sxs-lookup"><span data-stu-id="812c1-p102">People who are assigned the global admin or service administrator role can view service health. To allow Exchange, SharePoint, and Skype for Business admins to view service health, they must also be assigned the Service admin role.</span></span>
  
2. <span data-ttu-id="812c1-p103">若要開啟 [服務健康狀況系統管理中心中，移至 [**健康情況** > **服務健康狀況**，或按一下 [**服務健康狀況卡片\*\*\*\*首頁儀表板**上。儀表板卡片會指出是否有作用中服務問題以及詳細的服務健康狀況] 頁面的連結。</span><span class="sxs-lookup"><span data-stu-id="812c1-p103">To open service health, in the admin center, go to **Health** > **Service health**, or click the **Service health card** on the **Home dashboard**. The dashboard card indicates whether there is an active service issue and links to the detailed service health page.</span></span>
    
    ![Dashboard card for service health](media/8ae3de43-7bd5-4ee9-90ed-8b5ba5f9b474.png)
  
3. <span data-ttu-id="812c1-114">各個雲端服務的健康情況狀態是以表格格式呈現，並以圖示代表該服務的可能狀態。</span><span class="sxs-lookup"><span data-stu-id="812c1-114">The health state of each cloud service is shown in a table format with an icon to indicate possible states.</span></span>
    
> [!TIP]
> <span data-ttu-id="812c1-115">您也可以在行動裝置上使用 [Office 365 Admin App](https://go.microsoft.com/fwlink/p/?linkid=627216) 來檢視服務健康情況，這是藉由推播通知掌握即時資訊的絕佳方式。</span><span class="sxs-lookup"><span data-stu-id="812c1-115">You can also use the [Office 365 Admin app](https://go.microsoft.com/fwlink/p/?linkid=627216) on your mobile device to view Service health, which is a great way to stay current with push notifications.</span></span> 
  
### <a name="view-details-of-posted-service-health"></a><span data-ttu-id="812c1-116">檢視已張貼的服務健康情況詳細資料</span><span class="sxs-lookup"><span data-stu-id="812c1-116">View details of posted service health</span></span>

<span data-ttu-id="812c1-p104">在預設檢視中，會顯示所有服務和及其目前健全狀態。若要篩選服務目前遭遇事件您檢視，請從在左邊的灰色列選取**事件**。選取 [**摘要報告**會顯示目前已發佈的摘要報告的服務。從**所有服務**] 檢視中，按一下顯示的服務狀態將會開啟諮詢或事件的摘要檢視。</span><span class="sxs-lookup"><span data-stu-id="812c1-p104">In the default view, all services and their current health state are displayed. To filter your view to services currently experiencing an incident, select **Incidents** from the shaded bar on the left. Selecting **Advisories** will show only services that currently have an advisory posted. From the **All services** view, clicking the displayed service state will open a summary view of the advisory or incident.</span></span> 
  
![View of current issues in service health](media/f829a3af-1aca-4dc2-97eb-15d805349b24.png)
  
<span data-ttu-id="812c1-122">建議或事件摘要會提供下列資訊：</span><span class="sxs-lookup"><span data-stu-id="812c1-122">The advisory or incident summary provides the following information:</span></span> 
  
![螢幕擷取畫面顯示標籤服務摘要報告中的欄位](media/0dd6065c-1381-4a5c-8ca0-854c3e043a5c.png)
  
1. <span data-ttu-id="812c1-124">問題識別碼和問題的摘要敘述。</span><span class="sxs-lookup"><span data-stu-id="812c1-124">An issue identifier and summary statement of the problem.</span></span>
    
2. <span data-ttu-id="812c1-p105">目前的狀態。請參閱本文的狀態定義以取得各個可能狀態的說明。</span><span class="sxs-lookup"><span data-stu-id="812c1-p105">The current status. See status definitions in this article for an explanation of each potential status.</span></span>
    
3. <span data-ttu-id="812c1-127">描述此問題對使用者造成的影響。</span><span class="sxs-lookup"><span data-stu-id="812c1-127">A description of how this issue can affect users.</span></span>
    
4. <span data-ttu-id="812c1-p106">此問題開始發生的時間，以及服務健康情況訊息的上次更新時間。在問題發生期間，我們會持續張貼訊息，讓您知道目前套用解決方案的進度。</span><span class="sxs-lookup"><span data-stu-id="812c1-p106">The time that the issue was started and the last time that the service health message was updated. Throughout the duration of an issue we post frequent messages to let you know the progress that we're making in applying a solution.</span></span>
    
5. <span data-ttu-id="812c1-130">選取 [**顯示詳細資料**] 連結以查看問題，包括所有從張貼的訊息時我們將解決方案上工作的歷程記錄的相關詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="812c1-130">Select the **Show details** link to see more details about the issue, including the history of all messages posted while we work on a solution.</span></span> 
    
### <a name="translate-service-health-details"></a><span data-ttu-id="812c1-131">翻譯服務健康情況詳細資料</span><span class="sxs-lookup"><span data-stu-id="812c1-131">Translate service health details</span></span>

<span data-ttu-id="812c1-p107">服務健康情況說明都是即時張貼的資訊，因此不會自動翻譯成您的語言，且服務事件的詳細資料僅提供英文版。若要翻譯說明，請依照以下步驟進行：</span><span class="sxs-lookup"><span data-stu-id="812c1-p107">Because service health explanations are posted in real-time, they are not automatically translated to your language and the details of a service event are in English only. To translate the explanation, follow these steps:</span></span>
  
1. <span data-ttu-id="812c1-134">移至 [Translator](https://www.bing.com/translator/)。</span><span class="sxs-lookup"><span data-stu-id="812c1-134">Go to [Translator](https://www.bing.com/translator/).</span></span>
    
2. <span data-ttu-id="812c1-p108">在 [**服務健康狀況**] 頁面上選取的事件或摘要報告。在 [**顯示詳細資料**] 將複製的相關問題的文字。</span><span class="sxs-lookup"><span data-stu-id="812c1-p108">On the **Service health** page, select an incident or advisory. Under **Show details**, copy the text about the issue.</span></span>
    
3. <span data-ttu-id="812c1-137">轉譯器，在貼上文字，並選擇**翻譯**。</span><span class="sxs-lookup"><span data-stu-id="812c1-137">In Translator, paste the text and choose **Translate**.</span></span>
    
### <a name="definitions"></a><span data-ttu-id="812c1-138">定義</span><span class="sxs-lookup"><span data-stu-id="812c1-138">Definitions</span></span>

<span data-ttu-id="812c1-p109">在大多數的情況下，服務都會顯示為健康情況良好，沒有進一步的資訊。如果服務發生問題，系統就會以建議或事件的方式表示發生問題，並顯示目前的狀態。</span><span class="sxs-lookup"><span data-stu-id="812c1-p109">Most of the time services will appear as healthy with no further information. When a service is having a problem, the issue is identified as either an advisory or an incident and shows a current status.</span></span>
  
> [!TIP]
> <span data-ttu-id="812c1-p110">計劃的維護事件不會顯示在 [服務健康狀況。您可以藉由保持最新**訊息中心**追蹤計劃的維護事件。篩選郵件分類為 「 了解變更時要發生、 其生效及如何準備其變更的規劃。如需詳細資訊，請參閱[Office 365 中的訊息中心](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093)。</span><span class="sxs-lookup"><span data-stu-id="812c1-p110">Planned maintenance events aren't shown in service health. You can track planned maintenance events by staying up to date with the **Message center**. Filter to messages categorized as Plan for change to find out when the change is going to happen, its effect, and how to prepare for it. See [Message center in Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) for more details.</span></span> 
  
### <a name="incidents-and-advisories"></a><span data-ttu-id="812c1-145">事件和建議</span><span class="sxs-lookup"><span data-stu-id="812c1-145">Incidents and advisories</span></span>

|||
|:-----|:-----|
|![Information icon for advisory](media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|<span data-ttu-id="812c1-p111">如果系統針對某個服務顯示「建議」，表示我們發現了會對部分使用者造成影響的問題，但該服務仍可使用。建議中通常會提供問題的因應措施，且該問題可能是間歇發生，或其波及範圍和對使用者造成的影響並不大。</span><span class="sxs-lookup"><span data-stu-id="812c1-p111">If a service has an advisory shown, we are aware of a problem that is affecting some users, but the service is still available. In an advisory, there is often a workaround to the problem and the problem may be intermittent or is limited in scope and user impact.</span></span>  <br/> |
|![Exclamation point icon for incident](media/a636db57-6083-44dc-bbd5-556850804f17.png)|<span data-ttu-id="812c1-p112">如果系統針對某個服務顯示有作用中的「事件」，代表這是一個重大問題，且該服務或其主要功能無法使用。例如，使用者可能無法傳送和接收電子郵件，或者無法登入。事件會對使用者造成明顯影響。當有進行中的事件時，我們會在服務健康情況儀表板中提供更新資訊，讓您掌握調查和移轉作業的進度，以及確認解決方案。</span><span class="sxs-lookup"><span data-stu-id="812c1-p112">If a service has an active incident shown, it's a critical issue and the service or a major function of the service is unavailable. For example, users may be unable to send and receive email or unable to sign-in. Incidents will have noticeable impact to users. When there is an incident in progress, we will provide updates regarding the investigation, mitigation efforts, and confirmation of resolution in the Service health dashboard.</span></span>  <br/> |
   
### <a name="status-definitions"></a><span data-ttu-id="812c1-154">狀態定義</span><span class="sxs-lookup"><span data-stu-id="812c1-154">Status definitions</span></span>

|<span data-ttu-id="812c1-155">**狀態**</span><span class="sxs-lookup"><span data-stu-id="812c1-155">**Status**</span></span>|<span data-ttu-id="812c1-156">**定義**</span><span class="sxs-lookup"><span data-stu-id="812c1-156">**Definition**</span></span>|
|:-----|:-----|
|<span data-ttu-id="812c1-157">**調查中**</span><span class="sxs-lookup"><span data-stu-id="812c1-157">**Investigating**</span></span> | <span data-ttu-id="812c1-158">我們已發現潛在問題，正在收集關於其原因和影響範圍的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="812c1-158">We're aware of a potential issue and are gathering more information about what's going on and the scope of impact.</span></span> |
|<span data-ttu-id="812c1-159">**服務效能下降**</span><span class="sxs-lookup"><span data-stu-id="812c1-159">**Service degradation**</span></span> | <span data-ttu-id="812c1-p113">我們已確認某個問題可能會對服務或功能的使用造成影響。舉例來說，如果某個服務的執行速度比平常慢、出現間歇性中斷，或者某個功能無法正常運作，您就會看見此狀態。</span><span class="sxs-lookup"><span data-stu-id="812c1-p113">We've confirmed that there is an issue that may affect use of a service or feature. You might see this status if a service is performing more slowly than usual, there are intermittent interruptions, or if a feature isn't working, for example.</span></span> |
|<span data-ttu-id="812c1-162">**服務中斷**</span><span class="sxs-lookup"><span data-stu-id="812c1-162">**Service interruption**</span></span> | <span data-ttu-id="812c1-p114">如果我們判斷某個問題會影響使用者存取服務的能力，您就會看見此狀態。這種情況表示問題相當嚴重，且在相同條件下會固定發生。</span><span class="sxs-lookup"><span data-stu-id="812c1-p114">You'll see this status if we determine that an issue affects the ability for users to access the service. In this case, the issue is significant and can be reproduced consistently.</span></span> |
|<span data-ttu-id="812c1-165">**正在恢復服務**</span><span class="sxs-lookup"><span data-stu-id="812c1-165">**Restoring service**</span></span> | <span data-ttu-id="812c1-166">我們已經找出問題的成因，知道要採取什麼修正動作，且正在讓服務恢復到健康情況良好的狀態。</span><span class="sxs-lookup"><span data-stu-id="812c1-166">The cause of the issue has been identified, we know what corrective action to take, and are in the process of bringing the service back to a healthy state.</span></span> |
|<span data-ttu-id="812c1-167">**擴充的復原**</span><span class="sxs-lookup"><span data-stu-id="812c1-167">**Extended recovery**</span></span> | <span data-ttu-id="812c1-p115">此狀態表示我們正在進行矯正措施，以便為大多數使用者恢復服務，但需要一些時間才能讓所有受影響的系統恢復正常運作。如果我們在尚未進行永久修復期間先採用暫時修正方法以降低影響，您也可能會看到此狀態。</span><span class="sxs-lookup"><span data-stu-id="812c1-p115">This status indicates that corrective action is in progress to restore service to most users but will take some time to reach all the affected systems. You might also see this status if we've made a temporary fix to reduce impact while we wait to apply a permanent fix.</span></span> |
|<span data-ttu-id="812c1-170">**調查暫停**</span><span class="sxs-lookup"><span data-stu-id="812c1-170">**Investigation suspended**</span></span> | <span data-ttu-id="812c1-p116">在我們詳細調查潛在問題後，如果需要客戶提供額外資訊以進行更深入的調查，您就會看到此狀態。如果我們需要您採取行動，我們會告知您我們所需的資料或記錄。</span><span class="sxs-lookup"><span data-stu-id="812c1-p116">If our detailed investigation of a potential issue results in a request for additional information from customers to allow us to investigate further, you'll see this status. If we need you to act, we'll let you know what data or logs we need.</span></span> |
|<span data-ttu-id="812c1-173">**服務已恢復**</span><span class="sxs-lookup"><span data-stu-id="812c1-173">**Service restored**</span></span> | <span data-ttu-id="812c1-p117">我們確認矯正措施已解決根本問題，且服務也已恢復為健康情況良好的狀態。如需了解何處發生錯誤，請檢視問題詳細資料。</span><span class="sxs-lookup"><span data-stu-id="812c1-p117">We've confirmed that corrective action has resolved the underlying problem and the service has been restored to a healthy state. To find out what went wrong, view the issue details.</span></span> |
|<span data-ttu-id="812c1-176">**發佈後附隨報告**</span><span class="sxs-lookup"><span data-stu-id="812c1-176">**Post-incident report published**</span></span> | <span data-ttu-id="812c1-177">我們已發佈的特定問題包含根原因資訊及下一個步驟以確保不會再度發生類似的問題張貼附隨報告。</span><span class="sxs-lookup"><span data-stu-id="812c1-177">We’ve published a Post Incident Report for a specific issue that includes root cause information and next steps to ensure a similar issue doesn’t reoccur.</span></span> |
   
## <a name="history"></a><span data-ttu-id="812c1-178">[歷程記錄] </span><span class="sxs-lookup"><span data-stu-id="812c1-178">History</span></span>

<span data-ttu-id="812c1-p118">服務健康狀況可讓您查看目前的健全狀況狀態和檢視歷程任何的記錄服務摘要報告及有影響您的租用戶在過去 30 天的事件。若要檢視所有服務的過去狀況，選取 [**服務健康狀況**] 頁面上的 [**檢視歷程記錄**]。</span><span class="sxs-lookup"><span data-stu-id="812c1-p118">Service health lets you look at current health status and view the history of any service advisories and incidents that have impacted your tenant in the past 30 days. To view the past health of all services, select **View history** on the **Service health** page.</span></span> 
  
![Show link to health history](media/12a3e484-1eb4-497f-8cab-8064bccc2ef5.png)
  
<span data-ttu-id="812c1-182">系統就會以清單顯示在所選時間範圍內張貼的所有服務健康情況訊息，如下所示：</span><span class="sxs-lookup"><span data-stu-id="812c1-182">A list of all service health messages posted in the selected timeframe is displayed, as shown below:</span></span>
  
![View service health history](media/5ed20247-121c-4abe-9fe7-9025e26a2d0e.png)
  
<span data-ttu-id="812c1-p119">您可能會過去 7 天或過去 30 天內檢視狀況歷程記錄。選取 [檢視有關該問題的詳細資訊的任何資料列。</span><span class="sxs-lookup"><span data-stu-id="812c1-p119">You may view the health history for either the last 7 days or last 30 days. Select any row to view more details about that issue.</span></span>
  
<span data-ttu-id="812c1-186">如需上線時間百分比我們承諾的詳細資訊，請參閱[透明作業來自 Office 365](https://go.microsoft.com/fwlink/?linkid=848695)。</span><span class="sxs-lookup"><span data-stu-id="812c1-186">For more information about our commitment to uptime, see [Transparent operations from Office 365](https://go.microsoft.com/fwlink/?linkid=848695).</span></span>
  
## <a name="leave-feedback"></a><span data-ttu-id="812c1-187">提供意見反應</span><span class="sxs-lookup"><span data-stu-id="812c1-187">Leave feedback</span></span>

<span data-ttu-id="812c1-p120">我們的目標是為您提供關於當前問題最及時、正確且實用的資訊。請選取星級評等，告訴我們做得好不好。在您以 1 到 5 顆星給我們評分之後，您可以針對任何特定詳細資料提供意見反應。我們將會根據您的意見反應來微調服務健康情況系統。</span><span class="sxs-lookup"><span data-stu-id="812c1-p120">Our goal is to make sure that the information we provide to you about an ongoing issue is timely, accurate, and useful. To tell us how we're doing, select a star rating. After you give us a score from 1 to 5 stars, you can give feedback on any specific details. We'll use your feedback to fine-tune our service health system.</span></span>
  
![Feedback form for service health issues](media/fd083fdb-fde8-47b4-9136-b90d1d003864.png)
  
## <a name="see-also"></a><span data-ttu-id="812c1-193">另請參閱</span><span class="sxs-lookup"><span data-stu-id="812c1-193">See also</span></span>

[<span data-ttu-id="812c1-194">Office 365 系統管理中心的活動報告</span><span class="sxs-lookup"><span data-stu-id="812c1-194">Activity Reports in the Office 365 admin center</span></span>](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)

