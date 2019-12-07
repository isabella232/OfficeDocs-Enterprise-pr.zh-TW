---
title: 在小組中與來賓共同作業
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: 了解如何在小組中的來賓與共同作業。
ms.openlocfilehash: 9920bb57f31a36dcc4f903e2f26eccbf41a522db
ms.sourcegitcommit: 7e65640fb1a86858a95c9ef0edbb58d0f171c5ee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/06/2019
ms.locfileid: "39886522"
---
# <a name="collaborate-with-guests-in-a-team"></a><span data-ttu-id="66539-103">在小組中與來賓共同作業</span><span class="sxs-lookup"><span data-stu-id="66539-103">Collaborate with guests in a team</span></span>

<span data-ttu-id="66539-104">如果您需要整個文件、 工作和交談來賓與共同作業，我們建議使用 Microsoft Teams。</span><span class="sxs-lookup"><span data-stu-id="66539-104">If you need to collaborate with guests across documents, tasks, and conversations, we recommend using Microsoft Teams.</span></span> <span data-ttu-id="66539-105">Teams 提供所有的 Office 和 SharePoint 與常設聊天室中可用的共同作業功能和一組可自訂且可擴充的統一的使用者經驗中的共同作業工具。</span><span class="sxs-lookup"><span data-stu-id="66539-105">Teams provides all of the collaboration features available in Office and SharePoint with persistent chat and a customizable and extensible set of collaboration tools in a unified user experience.</span></span>

<span data-ttu-id="66539-106">在本文中，我們會逐步設定來賓與共同作業小組所需的 Microsoft 365 組態步驟。</span><span class="sxs-lookup"><span data-stu-id="66539-106">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up a team for collaboration with guests.</span></span>

## <a name="video-demonstration"></a><span data-ttu-id="66539-107">影片示範</span><span class="sxs-lookup"><span data-stu-id="66539-107">Video demonstration</span></span>

<span data-ttu-id="66539-108">這段影片顯示本文所述的設定步驟。</span><span class="sxs-lookup"><span data-stu-id="66539-108">This video shows the configuration steps described in this document.</span></span></br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE44NTr?autoplay=false]

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="66539-109">Azure 的組織關聯性設定</span><span class="sxs-lookup"><span data-stu-id="66539-109">Azure Organizational relationships settings</span></span>

<span data-ttu-id="66539-110">Microsoft 365 中共用是由控管最高層級 Azure Active Directory 中的組織關聯性設定。</span><span class="sxs-lookup"><span data-stu-id="66539-110">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="66539-111">如果共用的來賓已停用，或限制在 Azure AD 中，這會覆寫任何您在 Microsoft 365 中設定的共用設定。</span><span class="sxs-lookup"><span data-stu-id="66539-111">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="66539-112">檢查以確保未封鎖來賓與共用的組織關聯性設定。</span><span class="sxs-lookup"><span data-stu-id="66539-112">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Azure Active Directory 組織關聯性設定頁面的螢幕擷取畫面](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="66539-114">若要設定組織關聯性設定</span><span class="sxs-lookup"><span data-stu-id="66539-114">To set organizational relationship settings</span></span>

1. <span data-ttu-id="66539-115">登入 Microsoft Azure 在[https://portal.azure.com](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="66539-115">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="66539-116">在左導覽中，按一下 [ **Azure Active Directory**]。</span><span class="sxs-lookup"><span data-stu-id="66539-116">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="66539-117">在 [**概觀**] 窗格中，按一下 [**組織關聯性**。</span><span class="sxs-lookup"><span data-stu-id="66539-117">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="66539-118">在**組織關聯性**] 窗格中，按一下 [**設定**]。</span><span class="sxs-lookup"><span data-stu-id="66539-118">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="66539-119">確保**系統管理員和來賓邀請者角色中的使用者可以邀請**和**成員可以邀請**都會設**為 [是]**。</span><span class="sxs-lookup"><span data-stu-id="66539-119">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="66539-120">如果您做了任何變更，請按一下 [儲存]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="66539-120">If you made changes, click **Save**.</span></span>

<span data-ttu-id="66539-121">請注意 [**共同作業限制**] 區段中的設定。</span><span class="sxs-lookup"><span data-stu-id="66539-121">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="66539-122">請確定不封鎖的網域的來賓，您想要與共同作業。</span><span class="sxs-lookup"><span data-stu-id="66539-122">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="teams-guest-access-settings"></a><span data-ttu-id="66539-123">Teams 來賓存取設定</span><span class="sxs-lookup"><span data-stu-id="66539-123">Teams guest access settings</span></span>

<span data-ttu-id="66539-124">小組已開啟/關閉的來賓存取，且各種不同的設定可控制來賓可以做什麼小組中切換到主圖形。</span><span class="sxs-lookup"><span data-stu-id="66539-124">Teams has a master on/off switch for guest access and a variety of settings available to control what guests can do in a team.</span></span> <span data-ttu-id="66539-125">主版參數時，**允許小組中的來賓存取**必須**上**的來賓存取在小組中運作。</span><span class="sxs-lookup"><span data-stu-id="66539-125">The master switch, **Allow guest access in Teams** must be **On** for guest access to work in Teams.</span></span>

<span data-ttu-id="66539-126">請檢查可確保 Teams 中的來賓存取已啟用，以根據貴公司的來賓設定任何調整需求。</span><span class="sxs-lookup"><span data-stu-id="66539-126">Check to ensure that guest access is enabled in Teams and make any adjustment to the guest settings based on your business needs.</span></span> <span data-ttu-id="66539-127">請記住，這些設定會影響所有的 microsoft teams。</span><span class="sxs-lookup"><span data-stu-id="66539-127">Keep in mind that these settings affect all teams.</span></span>

![Teams 來賓存取切換的螢幕擷取畫面](media/teams-guest-access-toggle-on.png)

<span data-ttu-id="66539-129">若要設定 microsoft Teams 來賓存取設定</span><span class="sxs-lookup"><span data-stu-id="66539-129">To set Teams guest access settings</span></span>

1. <span data-ttu-id="66539-130">登入 Microsoft 365 系統管理中心， [https://admin.microsoft.com](https://admin.microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="66539-130">Log in to the Microsoft 365 admin center at [https://admin.microsoft.com](https://admin.microsoft.com).</span></span>
2. <span data-ttu-id="66539-131">在左導覽中，按一下 [**全部顯示**]。</span><span class="sxs-lookup"><span data-stu-id="66539-131">In the left navigation, click **Show all**.</span></span>
3. <span data-ttu-id="66539-132">**系統管理中心**中，按一下 [ **microsoft Teams**。</span><span class="sxs-lookup"><span data-stu-id="66539-132">Under **Admin centers**, click **Teams**.</span></span>
4. <span data-ttu-id="66539-133">在 microsoft Teams 系統管理中心中，在左側導覽中，依序展開 [**全組織的設定**，按一下 [**來賓存取**。</span><span class="sxs-lookup"><span data-stu-id="66539-133">In the Teams admin center, in the left navigation, expand **Org-wide settings** and click **Guest access**.</span></span>
5. <span data-ttu-id="66539-134">確定**允許小組中的來賓存取**設定為**上**。</span><span class="sxs-lookup"><span data-stu-id="66539-134">Ensure that **Allow guest access in Teams** is set to **On**.</span></span>
6. <span data-ttu-id="66539-135">額外的來賓設定，讓任何想要的變更，然後按一下 [**儲存**。</span><span class="sxs-lookup"><span data-stu-id="66539-135">Make any desired changes to the additional guest settings, and then click **Save**.</span></span>

> [!NOTE]
> <span data-ttu-id="66539-136">設定後將它開啟成為作用中的 Teams 來賓的可能需要最多 24 個小時。</span><span class="sxs-lookup"><span data-stu-id="66539-136">It may take up to twenty-four hours for the Teams guest setting to become active after you turn it on.</span></span>

## <a name="office-365-groups-guest-settings"></a><span data-ttu-id="66539-137">Office 365 群組的來賓設定</span><span class="sxs-lookup"><span data-stu-id="66539-137">Office 365 Groups guest settings</span></span>

<span data-ttu-id="66539-138">小組會使用 Office 365 群組的小組成員資格。</span><span class="sxs-lookup"><span data-stu-id="66539-138">Teams uses Office 365 Groups for team membership.</span></span> <span data-ttu-id="66539-139">為了讓小組中的來賓存取運作，必須在開啟 Office 365 群組來賓設定。</span><span class="sxs-lookup"><span data-stu-id="66539-139">The Office 365 Groups guest settings must be turned on in order for guest access in Teams to work.</span></span>

![Microsoft 365 系統管理中心中 Office 365 群組來賓設定的螢幕擷取畫面](media/office-365-groups-guest-settings.png)

<span data-ttu-id="66539-141">若要設定 Office 365 群組的來賓</span><span class="sxs-lookup"><span data-stu-id="66539-141">To set Office 365 Groups guest settings</span></span>

1. <span data-ttu-id="66539-142">在 Microsoft 365 系統管理中心，在左側導覽中，展開 [**設定**]。</span><span class="sxs-lookup"><span data-stu-id="66539-142">In the Microsoft 365 admin center, in the left navigation, expand **Settings**.</span></span>
2. <span data-ttu-id="66539-143">按一下 [**服務 & 增益集**]。</span><span class="sxs-lookup"><span data-stu-id="66539-143">Click **Services & add-ins**.</span></span>
3. <span data-ttu-id="66539-144">在清單中，按一下 [ **Office 365 群組**。</span><span class="sxs-lookup"><span data-stu-id="66539-144">In the list, click **Office 365 Groups**.</span></span>
4. <span data-ttu-id="66539-145">請確定，**讓外部組織存取群組內容的群組成員**，**讓群組擁有者新增至群組在組織外的人員**] 核取方塊會同時檢查。</span><span class="sxs-lookup"><span data-stu-id="66539-145">Ensure that the **Let group members outside your organization access group content** and **Let group owners add people outside your organization to groups** check boxes are both checked.</span></span>
5. <span data-ttu-id="66539-146">如果您所做的變更，按一下 [**儲存變更**。</span><span class="sxs-lookup"><span data-stu-id="66539-146">If you made changes, click **Save changes**.</span></span>


## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="66539-147">共用設定的 SharePoint 組織層級</span><span class="sxs-lookup"><span data-stu-id="66539-147">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="66539-148">所有儲存在 SharePoint 小組例如檔案、 資料夾及清單內容。</span><span class="sxs-lookup"><span data-stu-id="66539-148">Teams content such as files, folders, and lists are all stored in SharePoint.</span></span> <span data-ttu-id="66539-149">為了讓小組中有這些項目的存取權的來賓，SharePoint 組織層級共用設定必須允許與來賓共用。</span><span class="sxs-lookup"><span data-stu-id="66539-149">In order for guests to have access to these items in Teams, the SharePoint organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="66539-150">組織層級設定會決定哪些設定可供個別的網站，包括 microsoft teams 相關聯的網站。</span><span class="sxs-lookup"><span data-stu-id="66539-150">The organization-level settings determine what settings are available for individual sites, including sites associated with teams.</span></span> <span data-ttu-id="66539-151">網站設定不能更寬鬆比組織層級的設定。</span><span class="sxs-lookup"><span data-stu-id="66539-151">Site settings cannot be more permissive than the organization-level settings.</span></span>

<span data-ttu-id="66539-152">如果您想要允許的檔案和資料夾共用與未驗證的人員，選擇 [**任何人**]。</span><span class="sxs-lookup"><span data-stu-id="66539-152">If you want to allow file and folder sharing with unauthenticated people, choose **Anyone**.</span></span> <span data-ttu-id="66539-153">如果您想要確定所有來賓都需要驗證，請選擇 [**新增] 和 [現有的來賓**。</span><span class="sxs-lookup"><span data-stu-id="66539-153">If you want to ensure that all guests have to authenticate, choose **New and existing guests**.</span></span> <span data-ttu-id="66539-154">選擇 [將您的組織中任何網站所需的最寬鬆] 設定。</span><span class="sxs-lookup"><span data-stu-id="66539-154">Choose the most permissive setting that will be needed by any site in your organization.</span></span>

![SharePoint 組織層級共用設定的螢幕擷取畫面](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="66539-156">若要設定共用設定的 SharePoint 組織層級</span><span class="sxs-lookup"><span data-stu-id="66539-156">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="66539-157">在 Microsoft 365 系統管理中心，在左側導覽中，[**系統管理中心**中，按一下 [ **SharePoint**]。</span><span class="sxs-lookup"><span data-stu-id="66539-157">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="66539-158">在 SharePoint 管理中心中，按一下左側導覽窗格中的 [共用]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="66539-158">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="66539-159">請確定該外部共用 SharePoint 設為**任何人**或**新增和現有的來賓**。</span><span class="sxs-lookup"><span data-stu-id="66539-159">Ensure that external sharing for SharePoint is set to **Anyone** or **New and existing guests**.</span></span>
4. <span data-ttu-id="66539-160">如果您做了任何變更，請按一下 [儲存]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="66539-160">If you made changes, click **Save**.</span></span>


## <a name="sharepoint-organization-level-default-link-settings"></a><span data-ttu-id="66539-161">SharePoint 組織層級預設連結設定</span><span class="sxs-lookup"><span data-stu-id="66539-161">SharePoint organization level default link settings</span></span>

<span data-ttu-id="66539-162">預設檔案和資料夾連結設定會決定哪一個連結選項向使用者顯示預設情況下使用者共用的檔案或資料夾時。</span><span class="sxs-lookup"><span data-stu-id="66539-162">The default file and folder link settings determine which link option is shown to the user by default when they share a file or folder.</span></span> <span data-ttu-id="66539-163">使用者可以將連結類型變更為下列其中一個其他選項共用視之前。</span><span class="sxs-lookup"><span data-stu-id="66539-163">Users can change the link type to one of the other options before sharing if desired.</span></span>

<span data-ttu-id="66539-164">請記住此設定會影響所有的 microsoft teams 和貴組織中的 SharePoint 網站。</span><span class="sxs-lookup"><span data-stu-id="66539-164">Keep in mind that this setting affects all teams and SharePoint sites in your organization.</span></span>

<span data-ttu-id="66539-165">選擇 [當使用者共用檔案及資料夾，依預設會選取連結的類型：</span><span class="sxs-lookup"><span data-stu-id="66539-165">Choose the type of link that's selected by default when users share files and folders:</span></span>

- <span data-ttu-id="66539-166">**任何人] 連結**-如果您預期與未驗證的人共用大量檔案和資料夾選擇此選項。</span><span class="sxs-lookup"><span data-stu-id="66539-166">**Anyone with the link** - Choose this option if you expect to share a lot of files and folders with unauthenticated people.</span></span> <span data-ttu-id="66539-167">如果您想要允許*任何人*的連結，但擔心意外的未驗證共用，請考慮下列其中一個其他選項為預設值。</span><span class="sxs-lookup"><span data-stu-id="66539-167">If you want to allow *Anyone* links but are concerned about accidental unauthenticated sharing, consider one of the other options as the default.</span></span> <span data-ttu-id="66539-168">如果您已啟用**的任何人**共用，此連結類型只有。</span><span class="sxs-lookup"><span data-stu-id="66539-168">This link type is only available if you've enabled **Anyone** sharing.</span></span>
- <span data-ttu-id="66539-169">**只有在您的組織中的人員**-如果您預期大部分的檔案和資料夾共用您的組織內的人員都必須選擇此選項。</span><span class="sxs-lookup"><span data-stu-id="66539-169">**Only people in your organization** - Choose this option if you expect most file and folder sharing to be with people inside your organization.</span></span>
- <span data-ttu-id="66539-170">**特定人員**-如果您預期執行許多檔案和資料夾與來賓共用，請考慮此選項。</span><span class="sxs-lookup"><span data-stu-id="66539-170">**Specific people** - Consider this option if you expect to do a lot of file and folder sharing with guests.</span></span> <span data-ttu-id="66539-171">這種類型的連結與來賓運作，以及需要進行驗證。</span><span class="sxs-lookup"><span data-stu-id="66539-171">This type of link works with guests and requires them to authenticate.</span></span>
 
![SharePoint 組織層級檔案和資料夾共用設定的螢幕擷取畫面](media/sharepoint-organization-files-folders-sharing-settings.png)


<span data-ttu-id="66539-173">若要設定 SharePoint 組織層級預設值] 連結</span><span class="sxs-lookup"><span data-stu-id="66539-173">To set the SharePoint organization level default link settings</span></span>

1. <span data-ttu-id="66539-174">瀏覽至 SharePoint 系統管理中心的 [共用] 頁面上。</span><span class="sxs-lookup"><span data-stu-id="66539-174">Navigate to the Sharing page in the SharePoint admin center.</span></span>
2. <span data-ttu-id="66539-175">[**檔案] 和 [資料夾] 連結**，選取預設共用您想要使用的連結。</span><span class="sxs-lookup"><span data-stu-id="66539-175">Under **File and folder links**, select the default sharing link that you want to use.</span></span>
3. <span data-ttu-id="66539-176">如果您做了任何變更，請按一下 [儲存]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="66539-176">If you made changes, click **Save**.</span></span>

## <a name="create-a-team"></a><span data-ttu-id="66539-177">建立小組</span><span class="sxs-lookup"><span data-stu-id="66539-177">Create a team</span></span>

<span data-ttu-id="66539-178">下一步是建立您計劃要用於來賓與共同作業小組。</span><span class="sxs-lookup"><span data-stu-id="66539-178">The next step is to create the team that you plan to use for collaborating with guests.</span></span>

<span data-ttu-id="66539-179">若要建立小組</span><span class="sxs-lookup"><span data-stu-id="66539-179">To create a team</span></span>
1. <span data-ttu-id="66539-180">在小組，[ **Teams** ] 索引標籤中，按一下 [**加入或建立小組**在左邊窗格的底部。</span><span class="sxs-lookup"><span data-stu-id="66539-180">In Teams, on the **Teams** tab, click **Join or create a team** at the bottom of the left pane.</span></span>
2. <span data-ttu-id="66539-181">按一下 [**建立小組**]。</span><span class="sxs-lookup"><span data-stu-id="66539-181">Click **Create a team**.</span></span>
3. <span data-ttu-id="66539-182">按一下 [**建立從頭小組**]。</span><span class="sxs-lookup"><span data-stu-id="66539-182">Click **Build a team from scratch**.</span></span>
4. <span data-ttu-id="66539-183">選擇 [**私人**或**公開**。</span><span class="sxs-lookup"><span data-stu-id="66539-183">Choose **Private** or **Public**.</span></span>
5. <span data-ttu-id="66539-184">輸入的名稱和描述小組、，然後按一下 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="66539-184">Type a name and description for the team, and then click **Create**.</span></span>
6. <span data-ttu-id="66539-185">按一下 [**略過**。</span><span class="sxs-lookup"><span data-stu-id="66539-185">Click **Skip**.</span></span>

<span data-ttu-id="66539-186">我們將稍後邀請使用者。</span><span class="sxs-lookup"><span data-stu-id="66539-186">We'll invite users later.</span></span> <span data-ttu-id="66539-187">接下來，務必檢查小組與相關聯的 SharePoint 網站的網站層級共用設定。</span><span class="sxs-lookup"><span data-stu-id="66539-187">Next, it's important to check the site-level sharing settings for the SharePoint site that is associated with the team.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="66539-188">SharePoint 網站層級共用設定</span><span class="sxs-lookup"><span data-stu-id="66539-188">SharePoint site level sharing settings</span></span>

<span data-ttu-id="66539-189">請檢查以確保它們允許您想要此小組的存取類型的網站層級共用設定。</span><span class="sxs-lookup"><span data-stu-id="66539-189">Check the site-level sharing settings to make sure that they allow the type of access that you want for this team.</span></span> <span data-ttu-id="66539-190">例如，如果您設定組織層級設定為**任何人**，但您想要為此小組進行驗證的所有來賓，然後進行確認網站層級共用設定設為 [**新增] 和 [現有的來賓**。</span><span class="sxs-lookup"><span data-stu-id="66539-190">For example, if you set the organization-level settings to **Anyone**, but you want all guests to authenticate for this team, then make sure the site-level sharing settings are set to **New and existing guests**.</span></span>

![SharePoint 網站外部共用設定的螢幕擷取畫面](media/sharepoint-site-external-sharing-settings.png)


<span data-ttu-id="66539-192">若要設定網站層級共用設定</span><span class="sxs-lookup"><span data-stu-id="66539-192">To set site-level sharing settings</span></span>
1. <span data-ttu-id="66539-193">在 SharePoint 管理中心中，在左側導覽窗格中展開 [網站]\*\*\*\*，然後按一下 [使用中網站]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="66539-193">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="66539-194">為您剛建立的小組選取網站。</span><span class="sxs-lookup"><span data-stu-id="66539-194">Select the site for the team that you just created.</span></span>
3. <span data-ttu-id="66539-195">在功能區中，按一下 [共用]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="66539-195">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="66539-196">請確定該共用設為**任何人**或**新增和現有的來賓**。</span><span class="sxs-lookup"><span data-stu-id="66539-196">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="66539-197">如果您做了任何變更，請按一下 [儲存]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="66539-197">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="66539-198">邀請使用者</span><span class="sxs-lookup"><span data-stu-id="66539-198">Invite users</span></span>

<span data-ttu-id="66539-199">來賓共用設定現在會進行設定，讓您可以開始將內部使用者和訪客新增至您的小組。</span><span class="sxs-lookup"><span data-stu-id="66539-199">Guest sharing settings are now configured, so you can start adding internal users and guests to your team.</span></span> 

<span data-ttu-id="66539-200">若要邀請給小組的內部使用者</span><span class="sxs-lookup"><span data-stu-id="66539-200">To invite internal users to a team</span></span>
1. <span data-ttu-id="66539-201">在 [小組成員，按一下 [**更多選項]** (**\*\***)，然後按一下 [**新增成員**。</span><span class="sxs-lookup"><span data-stu-id="66539-201">In the team, click **More options** (**\*\*\***), and then click **Add member**.</span></span>
2. <span data-ttu-id="66539-202">輸入您想要邀請的人員名稱。</span><span class="sxs-lookup"><span data-stu-id="66539-202">Type the name of the person who you want to invite.</span></span>
3. <span data-ttu-id="66539-203">Click **Add**, and then click **Close**.</span><span class="sxs-lookup"><span data-stu-id="66539-203">Click **Add**, and then click **Close**.</span></span>

<span data-ttu-id="66539-204">若要邀請給小組的來賓</span><span class="sxs-lookup"><span data-stu-id="66539-204">To invite guests to a team</span></span>
1. <span data-ttu-id="66539-205">在 [小組成員，按一下 [**更多選項]** (**\*\***)，然後按一下 [**新增成員**。</span><span class="sxs-lookup"><span data-stu-id="66539-205">In the team, click **More options** (**\*\*\***), and then click **Add member**.</span></span>
2. <span data-ttu-id="66539-206">輸入您想要邀請來賓顯示的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="66539-206">Type the email address of the guest who you want to invite.</span></span>
3. <span data-ttu-id="66539-207">按一下 [**編輯來賓資訊**。</span><span class="sxs-lookup"><span data-stu-id="66539-207">Click **Edit guest information**.</span></span>
4. <span data-ttu-id="66539-208">輸入來賓顯示的完整名稱，然後按一下 [核取記號。</span><span class="sxs-lookup"><span data-stu-id="66539-208">Type the guest's full name and click the check mark.</span></span>
5. <span data-ttu-id="66539-209">Click **Add**, and then click **Close**.</span><span class="sxs-lookup"><span data-stu-id="66539-209">Click **Add**, and then click **Close**.</span></span>

## <a name="see-also"></a><span data-ttu-id="66539-210">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66539-210">See Also</span></span>

[<span data-ttu-id="66539-211">最佳做法與未驗證的使用者共用檔案和資料夾</span><span class="sxs-lookup"><span data-stu-id="66539-211">Best practices for sharing files and folders with unauthenticated users</span></span>](best-practices-anonymous-sharing.md)

[<span data-ttu-id="66539-212">與來賓共用時限制意外暴露檔案</span><span class="sxs-lookup"><span data-stu-id="66539-212">Limit accidental exposure to files when sharing with guests</span></span>](sharing-limit-accidental-exposure.md)

<span data-ttu-id="66539-213">[建立安全的來賓共用環境](create-a-secure-guest-sharing-environment.md)）</span><span class="sxs-lookup"><span data-stu-id="66539-213">[Create a secure guest sharing environment](create-a-secure-guest-sharing-environment.md))</span></span>


