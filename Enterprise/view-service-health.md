---
title: 如何檢查 Office 365 服務健康情況
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365P_ServiceHealthModern
- O365M_ServiceHealthModern
- O365E_ViewStatusServices
- O365E_ServiceHealthModern
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
- IWA160
ms.assetid: 932ad3ad-533c-418a-b938-6e44e8bc33b0
description: 連絡支援服務以查看是否解決的服務中斷之前，請檢視 Office 365 服務的健康狀態。
ms.openlocfilehash: 2d5b12e4443395d5a9a16fd6934ca68a99601416
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843964"
---
# <a name="how-to-check-office-365-service-health"></a><span data-ttu-id="c3e7a-103">如何檢查 Office 365 服務健康情況</span><span class="sxs-lookup"><span data-stu-id="c3e7a-103">How to check Office 365 service health</span></span>

<span data-ttu-id="c3e7a-104">[![[標籤] 可讓您知道系統管理中心正在變更，您可以在 aka.ms/aboutM365preview 取得更多詳細資料。](media/O365-Admin-AdminCenterChanging.png)](https://docs.microsoft.com/office365/admin/microsoft-365-admin-center-preview?view=o365-worldwide)</span><span class="sxs-lookup"><span data-stu-id="c3e7a-104">[![Label to let you know the admin center is changing and you can find more details at aka.ms/aboutM365preview.](media/O365-Admin-AdminCenterChanging.png)](https://docs.microsoft.com/office365/admin/microsoft-365-admin-center-preview?view=o365-worldwide)</span></span>

<span data-ttu-id="c3e7a-105">您可以檢視您的 Microsoft 服務，包括 Office web、 Yammer、 Microsoft Dynamics CRM 和 Microsoft Intune 雲端服務時，在[系統管理中心](https://go.microsoft.com/fwlink/p/?linkid=2024339)的 Office 365**服務健康情況**] 頁面上的健康狀況。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-105">You can view the health of your Microsoft services, including Office on the web, Yammer, Microsoft Dynamics CRM, and Microsoft Intune cloud services, on the Office 365 **Service health** page in the [admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).</span></span> <span data-ttu-id="c3e7a-106">如果雲端服務發生問題，在您連絡支援人員或花時間進行疑難排解之前，可以查看服務健康情況，以確定是否為正在開發解決方法的已知問題。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-106">If you are experiencing problems with a cloud service, you can check the service health to determine whether this is a known issue with a resolution in progress before you call support or spend time troubleshooting.</span></span>

<span data-ttu-id="c3e7a-107">如果您無法登入服務入口網站，您可以使用[服務狀態] 頁面上](https://status.office365.com)，若要檢查是否有已知問題使您無法登入您的租用戶。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-107">If you are unable to sign in to the service portal, you can use the [service status page](https://status.office365.com) to check for known issues preventing you from logging into your tenant.</span></span>
  
### <a name="how-to-check-service-health"></a><span data-ttu-id="c3e7a-108">如何查看服務健康情況</span><span class="sxs-lookup"><span data-stu-id="c3e7a-108">How to check service health</span></span>

1. <span data-ttu-id="c3e7a-109">移至系統管理中心， [https://admin.microsoft.com](https://go.microsoft.com/fwlink/p/?linkid=2024339)，並以系統管理員帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-109">Go to the admin center at [https://admin.microsoft.com](https://go.microsoft.com/fwlink/p/?linkid=2024339), and sign in with an admin account.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c3e7a-110">被指派全域系統管理員或服務系統管理員角色的人員方可檢視服務健康情況。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-110">People who are assigned the global admin or service administrator role can view service health.</span></span> <span data-ttu-id="c3e7a-111">若要允許 Exchange、SharePoint 以及商務用 Skype 管理員檢視服務健康情況，必須同時將服務系統管理員角色指派給他們。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-111">To allow Exchange, SharePoint, and Skype for Business admins to view service health, they must also be assigned the Service admin role.</span></span> <span data-ttu-id="c3e7a-112">如需角色可以檢視服務健康情況相關的詳細資訊，請參閱[關於系統管理員角色](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles?view=o365-worldwide#roles-available-in-the-microsoft-365-admin-center)。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-112">For more information about roles that can view service health, see [About admin roles](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles?view=o365-worldwide#roles-available-in-the-microsoft-365-admin-center).</span></span>
  
2. <span data-ttu-id="c3e7a-113">如果您不使用新的系統管理中心中，在 [首頁] 頁面上，選取**嘗試在新版系統管理中心**的切換中右上角。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-113">If you are not using the new admin center, on the Home page, select the **Try the new admin center** toggle in the upper-right corner.</span></span>

3. <span data-ttu-id="c3e7a-114">若要檢視服務健康情況，在系統管理中心，移至 [**健康情況** > **服務健康情況**或選取**首頁儀表板**上的 [**服務健康情況**] 卡片。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-114">To view service health, in the admin center, go to **Health** > **Service health**, or select the **Service health** card on the **Home dashboard**.</span></span> <span data-ttu-id="c3e7a-115">儀表板卡片會指出是否有未解決的服務問題，並連結至詳細**服務健康情況**] 頁面。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-115">The dashboard card indicates whether there is an active service issue and links to the detailed **Service health** page.</span></span>
  
4. <span data-ttu-id="c3e7a-116">在 [**服務健康情況**] 頁面以表格格式顯示每個雲端服務的健康狀態。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-116">On the **Service health** page, the health state of each cloud service is shown in a table format.</span></span>

   ![View of current issues in service health](media/service-health-all-services.png)

<span data-ttu-id="c3e7a-118">**所有服務**] 索引標籤 （預設檢視） 顯示所有服務和及其目前健全狀況狀態。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-118">The **All services** tab (the default view) shows all services and their current health state.</span></span> <span data-ttu-id="c3e7a-119">圖示，[**狀態**] 欄表示每個服務的狀態。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-119">An icon and the **Status** column indicate the state of each service.</span></span> <span data-ttu-id="c3e7a-120">若要篩選檢視以顯示目前發生事件的服務，請選取頁面頂端的 [**事件**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-120">To filter your view to services currently experiencing an incident, select the **Incidents** tab at the top of the page.</span></span> <span data-ttu-id="c3e7a-121">選取 [**建議**] 索引標籤會顯示目前已張貼建議的服務。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-121">Selecting the **Advisories** tab will show only services that currently have an advisory posted.</span></span> <span data-ttu-id="c3e7a-122">[**歷程記錄**] 索引標籤顯示事件和已解決的摘要報告歷程的記錄。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-122">The **History** tab shows the history of incidents and advisories that have been resolved.</span></span>

<span data-ttu-id="c3e7a-123">如果您遇到此問題： Office 365 服務，且您沒有看到它列在 [**服務健康情況**] 頁面上，告訴我們藉由選取**報告此問題**，並完成短格式。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-123">If you're experiencing an issue with an Office 365 service and you don’t see it listed on the **Service health** page, tell us about it by selecting **Report an issue**, and completing the short form.</span></span> <span data-ttu-id="c3e7a-124">我們將查看相關資料，且來自其他組織若要查看如何時遇到的普遍問題報告，而且如果它源自與我們的服務。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-124">We’ll look at related data and reports from other organizations to see how widespread the issue is, and if it originated with our service.</span></span> <span data-ttu-id="c3e7a-125">如果有，我們會將它新增為新的事件或建議在**服務健康情況**] 頁面上，您可以在其中追蹤及其解決方法。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-125">If it did, we’ll add it as a new incident or advisory on the **Service health** page, where you can track its resolution.</span></span> <span data-ttu-id="c3e7a-126">如果您沒有看到它出現在清單中，大約 30 分鐘內，請考慮連絡支援，以解決問題。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-126">If you don’t see it appear on the list within about 30 minutes, consider contacting support to resolve the issue.</span></span>

> [!TIP]
> <span data-ttu-id="c3e7a-127">您也可以在行動裝置上使用 [Office 365 Admin App](https://go.microsoft.com/fwlink/p/?linkid=627216) 來檢視服務健康情況，這是藉由推播通知掌握即時資訊的絕佳方式。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-127">You can also use the [Office 365 Admin app](https://go.microsoft.com/fwlink/p/?linkid=627216) on your mobile device to view Service health, which is a great way to stay current with push notifications.</span></span> 
  
### <a name="view-details-of-posted-service-health"></a><span data-ttu-id="c3e7a-128">檢視已張貼的服務健康情況詳細資料</span><span class="sxs-lookup"><span data-stu-id="c3e7a-128">View details of posted service health</span></span>

<span data-ttu-id="c3e7a-129">**所有服務**] 檢視中，選取 [服務狀態將會開啟建議或事件摘要檢視。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-129">On the **All services** view, selecting the service status will open a summary view of advisories or incidents.</span></span>
  
![螢幕擷取畫面顯示諮詢服務](media/service-health-advisory.png)

<span data-ttu-id="c3e7a-131">建議或事件摘要會提供下列資訊：</span><span class="sxs-lookup"><span data-stu-id="c3e7a-131">The advisory or incident summary provides the following information:</span></span>

- <span data-ttu-id="c3e7a-132">**標題**-問題的摘要。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-132">**Title** - A summary of the problem.</span></span>
- <span data-ttu-id="c3e7a-133">**服務**-受影響的服務名稱。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-133">**Service** - The name of the affected service.</span></span>
- <span data-ttu-id="c3e7a-134">**ID** -問題的數值識別碼。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-134">**ID** - A numeric identifier for the problem.</span></span>
- <span data-ttu-id="c3e7a-135">**狀態**-這個問題會如何影響服務。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-135">**Status** - How this problem affects the service.</span></span>
- <span data-ttu-id="c3e7a-136">**開始時間**-此問題： 啟動時的時間。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-136">**Start time** - The time when the issue started.</span></span>
- <span data-ttu-id="c3e7a-137">**上次更新**-服務健康情況訊息的上次更新的最後一個時間。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-137">**Last updated** - The last time that the service health message was updated.</span></span> <span data-ttu-id="c3e7a-138">我們張貼訊息，告知您我們正在進行中套用解決方案的進度。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-138">We post frequent messages to let you know the progress that we're making in applying a solution.</span></span>

<span data-ttu-id="c3e7a-139">選取問題標題，若要查看問題詳細資料] 頁面上，其會顯示關於該問題，包括所有已張貼的訊息時我們運作解決方案上[歷程記錄](#history)的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-139">Select the issue title to see the issue detail page, which shows more information about the issue, including the [history](#history) of all messages posted while we work on a solution.</span></span>

![螢幕擷取畫面顯示問題的詳細資料](media/service-health-advisory-detail.png)

### <a name="translate-service-health-details"></a><span data-ttu-id="c3e7a-141">翻譯服務健康情況詳細資料</span><span class="sxs-lookup"><span data-stu-id="c3e7a-141">Translate service health details</span></span>

<span data-ttu-id="c3e7a-p107">服務健康情況說明都是即時張貼的資訊，因此不會自動翻譯成您的語言，且服務事件的詳細資料僅提供英文版。若要翻譯說明，請依照以下步驟進行：</span><span class="sxs-lookup"><span data-stu-id="c3e7a-p107">Because service health explanations are posted in real-time, they are not automatically translated to your language and the details of a service event are in English only. To translate the explanation, follow these steps:</span></span>
  
1. <span data-ttu-id="c3e7a-144">移至 [Translator](https://www.bing.com/translator/)。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-144">Go to [Translator](https://www.bing.com/translator/).</span></span>

2. <span data-ttu-id="c3e7a-145">在 [**服務健康情況**] 頁面上，選取事件或建議。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-145">On the **Service health** page, select an incident or advisory.</span></span> <span data-ttu-id="c3e7a-146">在 [**顯示詳細資料**，複製有關該問題的文字。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-146">Under **Show details**, copy the text about the issue.</span></span>

3. <span data-ttu-id="c3e7a-147">在 Translator 中，貼上文字，並選擇 [**翻譯**。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-147">In Translator, paste the text and choose **Translate**.</span></span>

### <a name="definitions"></a><span data-ttu-id="c3e7a-148">定義</span><span class="sxs-lookup"><span data-stu-id="c3e7a-148">Definitions</span></span>

<span data-ttu-id="c3e7a-149">大多數情況下，服務會顯示為健康情況良好沒有進一步的資訊。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-149">Most of the time, services will appear as healthy with no further information.</span></span> <span data-ttu-id="c3e7a-150">如果服務發生問題，系統就會以建議或事件的方式表示發生問題，並顯示目前的狀態。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-150">When a service is having a problem, the issue is identified as either an advisory or an incident and shows a current status.</span></span>
  
> [!TIP]
> <span data-ttu-id="c3e7a-151">預定維修事件不會顯示在服務健康情況中。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-151">Planned maintenance events aren't shown in service health.</span></span> <span data-ttu-id="c3e7a-152">您可以保持最新**訊息中心**，以追蹤預定的維修事件。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-152">You can track planned maintenance events by staying up to date with the **Message center**.</span></span> <span data-ttu-id="c3e7a-153">篩選至歸類為「規劃變更」 的訊息，即可了解何時要進行變更、變更的作用以及如何準備因應。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-153">Filter to messages categorized as Plan for change to find out when the change is going to happen, its effect, and how to prepare for it.</span></span> <span data-ttu-id="c3e7a-154">如需詳細資料，請參閱 [Office 365 中的訊息中心](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) (機器翻譯)。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-154">See [Message center in Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) for more details.</span></span>
  
### <a name="incidents-and-advisories"></a><span data-ttu-id="c3e7a-155">事件和建議</span><span class="sxs-lookup"><span data-stu-id="c3e7a-155">Incidents and advisories</span></span>

|||
|:-----|:-----|
|![Information icon for advisory](media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|<span data-ttu-id="c3e7a-p111">如果系統針對某個服務顯示「建議」，表示我們發現了會對部分使用者造成影響的問題，但該服務仍可使用。建議中通常會提供問題的因應措施，且該問題可能是間歇發生，或其波及範圍和對使用者造成的影響並不大。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-p111">If a service has an advisory shown, we are aware of a problem that is affecting some users, but the service is still available. In an advisory, there is often a workaround to the problem and the problem may be intermittent or is limited in scope and user impact.</span></span>  <br/> |
|![Exclamation point icon for incident](media/a636db57-6083-44dc-bbd5-556850804f17.png)|<span data-ttu-id="c3e7a-p112">如果系統針對某個服務顯示有作用中的「事件」，代表這是一個重大問題，且該服務或其主要功能無法使用。例如，使用者可能無法傳送和接收電子郵件，或者無法登入。事件會對使用者造成明顯影響。當有進行中的事件時，我們會在服務健康情況儀表板中提供更新資訊，讓您掌握調查和移轉作業的進度，以及確認解決方案。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-p112">If a service has an active incident shown, it's a critical issue and the service or a major function of the service is unavailable. For example, users may be unable to send and receive email or unable to sign-in. Incidents will have noticeable impact to users. When there is an incident in progress, we will provide updates regarding the investigation, mitigation efforts, and confirmation of resolution in the Service health dashboard.</span></span>  <br/> |

### <a name="status-definitions"></a><span data-ttu-id="c3e7a-164">狀態定義</span><span class="sxs-lookup"><span data-stu-id="c3e7a-164">Status definitions</span></span>

|<span data-ttu-id="c3e7a-165">**狀態**</span><span class="sxs-lookup"><span data-stu-id="c3e7a-165">**Status**</span></span>|<span data-ttu-id="c3e7a-166">**定義**</span><span class="sxs-lookup"><span data-stu-id="c3e7a-166">**Definition**</span></span>|
|:-----|:-----|
|<span data-ttu-id="c3e7a-167">**調查**</span><span class="sxs-lookup"><span data-stu-id="c3e7a-167">**Investigating**</span></span> | <span data-ttu-id="c3e7a-168">我們已發現潛在問題，正在收集關於其原因和影響範圍的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-168">We're aware of a potential issue and are gathering more information about what's going on and the scope of impact.</span></span> |
|<span data-ttu-id="c3e7a-169">**服務效能下降**</span><span class="sxs-lookup"><span data-stu-id="c3e7a-169">**Service degradation**</span></span> | <span data-ttu-id="c3e7a-p113">我們已確認某個問題可能會對服務或功能的使用造成影響。舉例來說，如果某個服務的執行速度比平常慢、出現間歇性中斷，或者某個功能無法正常運作，您就會看見此狀態。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-p113">We've confirmed that there is an issue that may affect use of a service or feature. You might see this status if a service is performing more slowly than usual, there are intermittent interruptions, or if a feature isn't working, for example.</span></span> |
|<span data-ttu-id="c3e7a-172">**服務中斷**</span><span class="sxs-lookup"><span data-stu-id="c3e7a-172">**Service interruption**</span></span> | <span data-ttu-id="c3e7a-p114">如果我們判斷某個問題會影響使用者存取服務的能力，您就會看見此狀態。這種情況表示問題相當嚴重，且在相同條件下會固定發生。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-p114">You'll see this status if we determine that an issue affects the ability for users to access the service. In this case, the issue is significant and can be reproduced consistently.</span></span> |
|<span data-ttu-id="c3e7a-175">**正在恢復服務**</span><span class="sxs-lookup"><span data-stu-id="c3e7a-175">**Restoring service**</span></span> | <span data-ttu-id="c3e7a-176">我們已經找出問題的成因，知道要採取什麼修正動作，且正在讓服務恢復到健康情況良好的狀態。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-176">The cause of the issue has been identified, we know what corrective action to take, and are in the process of bringing the service back to a healthy state.</span></span> |
|<span data-ttu-id="c3e7a-177">**擴充的復原**</span><span class="sxs-lookup"><span data-stu-id="c3e7a-177">**Extended recovery**</span></span> | <span data-ttu-id="c3e7a-p115">此狀態表示我們正在進行矯正措施，以便為大多數使用者恢復服務，但需要一些時間才能讓所有受影響的系統恢復正常運作。如果我們在尚未進行永久修復期間先採用暫時修正方法以降低影響，您也可能會看到此狀態。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-p115">This status indicates that corrective action is in progress to restore service to most users but will take some time to reach all the affected systems. You might also see this status if we've made a temporary fix to reduce impact while we wait to apply a permanent fix.</span></span> |
|<span data-ttu-id="c3e7a-180">**調查暫停**</span><span class="sxs-lookup"><span data-stu-id="c3e7a-180">**Investigation suspended**</span></span> | <span data-ttu-id="c3e7a-p116">在我們詳細調查潛在問題後，如果需要客戶提供額外資訊以進行更深入的調查，您就會看到此狀態。如果我們需要您採取行動，我們會告知您我們所需的資料或記錄。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-p116">If our detailed investigation of a potential issue results in a request for additional information from customers to allow us to investigate further, you'll see this status. If we need you to act, we'll let you know what data or logs we need.</span></span> |
|<span data-ttu-id="c3e7a-183">**服務已恢復**</span><span class="sxs-lookup"><span data-stu-id="c3e7a-183">**Service restored**</span></span> | <span data-ttu-id="c3e7a-p117">我們確認矯正措施已解決根本問題，且服務也已恢復為健康情況良好的狀態。如需了解何處發生錯誤，請檢視問題詳細資料。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-p117">We've confirmed that corrective action has resolved the underlying problem and the service has been restored to a healthy state. To find out what went wrong, view the issue details.</span></span> |
|<span data-ttu-id="c3e7a-186">**誤判**</span><span class="sxs-lookup"><span data-stu-id="c3e7a-186">**False positive**</span></span> | <span data-ttu-id="c3e7a-187">在詳細調查之後, 我們已確認服務狀況良好且為作業系統依設計。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-187">After a detailed investigation, we’ve confirmed the service is healthy and operating as designed.</span></span> <span data-ttu-id="c3e7a-188">觀察到不會影響服務或事件的原因來自外部服務。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-188">No impact to the service was observed or the cause of the incident originated outside of the service.</span></span> |
|<span data-ttu-id="c3e7a-189">**發佈後附隨報告**</span><span class="sxs-lookup"><span data-stu-id="c3e7a-189">**Post-incident report published**</span></span> | <span data-ttu-id="c3e7a-190">我們已發佈之特定問題，其中包含根原因資訊與下一個步驟，以確保不再發生類似的問題張貼附隨報告。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-190">We’ve published a Post Incident Report for a specific issue that includes root cause information and next steps to ensure a similar issue doesn’t reoccur.</span></span> |

### <a name="history"></a><span data-ttu-id="c3e7a-191">歷程記錄</span><span class="sxs-lookup"><span data-stu-id="c3e7a-191">History</span></span>

<span data-ttu-id="c3e7a-192">服務健康情況可讓您查看目前的健康狀態，並檢視所有服務建議和過去 30 天內會影響您的租用戶的事件的歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-192">Service health lets you look at current health status and view the history of any service advisories and incidents that have affected your tenant in the past 30 days.</span></span> <span data-ttu-id="c3e7a-193">若要檢視所有服務的過去健康情況，請選取 [**檢視歷程記錄**問題詳細資料] 頁面上。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-193">To view the past health of all services, select **View history** on the issue detail page.</span></span>
  
![Show link to health history](media/service-health-view-history.png)
  
<span data-ttu-id="c3e7a-195">系統就會以清單顯示在所選時間範圍內張貼的所有服務健康情況訊息，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c3e7a-195">A list of all service health messages posted in the selected timeframe is displayed, as shown below:</span></span>
  
![View service health history](media/service-health-history.png)
  
<span data-ttu-id="c3e7a-197">依序展開 [若要檢視有關該問題的更多詳細資料的任何資料列。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-197">Expand any row to view more details about the issue.</span></span>
  
<span data-ttu-id="c3e7a-198">如需我們致力於上線時間的詳細資訊，請參閱[從 Office 365 的透明化作業](https://go.microsoft.com/fwlink/?linkid=848695)。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-198">For more information about our commitment to uptime, see [Transparent operations from Office 365](https://go.microsoft.com/fwlink/?linkid=848695).</span></span>
  
## <a name="leave-feedback"></a><span data-ttu-id="c3e7a-199">提供意見反應</span><span class="sxs-lookup"><span data-stu-id="c3e7a-199">Leave feedback</span></span>

<span data-ttu-id="c3e7a-p120">我們的目標是為您提供關於當前問題最及時、正確且實用的資訊。請選取星級評等，告訴我們做得好不好。在您以 1 到 5 顆星給我們評分之後，您可以針對任何特定詳細資料提供意見反應。我們將會根據您的意見反應來微調服務健康情況系統。</span><span class="sxs-lookup"><span data-stu-id="c3e7a-p120">Our goal is to make sure that the information we provide to you about an ongoing issue is timely, accurate, and useful. To tell us how we're doing, select a star rating. After you give us a score from 1 to 5 stars, you can give feedback on any specific details. We'll use your feedback to fine-tune our service health system.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c3e7a-204">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3e7a-204">See also</span></span>

[<span data-ttu-id="c3e7a-205">在 Microsoft 365 系統管理中心的活動報告</span><span class="sxs-lookup"><span data-stu-id="c3e7a-205">Activity Reports in the Microsoft 365 admin center</span></span>](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)