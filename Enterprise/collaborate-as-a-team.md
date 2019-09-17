---
title: 與來賓小組共同作業
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: 了解如何在小組中的來賓與共同作業。
ms.openlocfilehash: 9a169e33a9cbd8f079966443bd3d830aa79f4971
ms.sourcegitcommit: 3bba97053caf5f9cff0ef3205afb7869535f38bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2019
ms.locfileid: "36992412"
---
# <a name="collaborate-with-guests-in-a-team"></a><span data-ttu-id="4d4a0-103">與來賓小組共同作業</span><span class="sxs-lookup"><span data-stu-id="4d4a0-103">Collaborate with guests in a team</span></span>

<span data-ttu-id="4d4a0-104">如果您需要整個文件、 工作和交談來賓與共同作業，我們建議使用 Microsoft Teams。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-104">If you need to collaborate with guests across documents, tasks, and conversations, we recommend using Microsoft Teams.</span></span> <span data-ttu-id="4d4a0-105">Teams 提供所有的 Office 和 SharePoint 與常設聊天室中可用的共同作業功能和一組可自訂且可擴充的統一的使用者經驗中的共同作業工具。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-105">Teams provides all of the collaboration features available in Office and SharePoint with persistent chat and a customizable and extensible set of collaboration tools in a unified user experience.</span></span>

<span data-ttu-id="4d4a0-106">在本文中，我們會逐步設定來賓與共同作業小組所需的 Microsoft 365 組態步驟。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-106">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up a team for collaboration with guests.</span></span>

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="4d4a0-107">Azure 的組織關聯性設定</span><span class="sxs-lookup"><span data-stu-id="4d4a0-107">Azure Organizational relationships settings</span></span>

<span data-ttu-id="4d4a0-108">Microsoft 365 中共用是由控管最高層級 Azure Active Directory 中的組織關聯性設定。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-108">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="4d4a0-109">如果共用的來賓已停用，或限制在 Azure AD 中，這會覆寫任何您在 Microsoft 365 中設定的共用設定。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-109">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="4d4a0-110">檢查以確保未封鎖來賓與共用的組織關聯性設定。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-110">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![螢幕擷取畫面的 Azure Active Directory 組織關聯性設定頁面](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="4d4a0-112">若要設定組織關聯性設定</span><span class="sxs-lookup"><span data-stu-id="4d4a0-112">To set organizational relationship settings</span></span>

1. <span data-ttu-id="4d4a0-113">登入 Microsoft Azure 在[https://portal.azure.com](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-113">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="4d4a0-114">在左導覽中，按一下 [ **Azure Active Directory**]。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-114">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="4d4a0-115">在 [**概觀**] 窗格中，按一下 [**組織關聯性**。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-115">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="4d4a0-116">在**組織關聯性**] 窗格中，按一下 [**設定**]。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-116">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="4d4a0-117">確保**系統管理員和來賓邀請者角色中的使用者可以邀請**和**成員可以邀請**都會設**為 [是]**。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-117">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="4d4a0-118">如果您所做的變更，請按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-118">If you made changes, click **Save**.</span></span>

<span data-ttu-id="4d4a0-119">請注意 [**共同作業限制**] 區段中的設定。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-119">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="4d4a0-120">請確定不封鎖的網域的來賓，您想要與共同作業。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-120">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="teams-guest-access-settings"></a><span data-ttu-id="4d4a0-121">Teams 來賓存取設定</span><span class="sxs-lookup"><span data-stu-id="4d4a0-121">Teams guest access settings</span></span>

<span data-ttu-id="4d4a0-122">小組已開啟/關閉的來賓存取，且各種不同的設定可控制來賓可以做什麼小組中切換到主圖形。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-122">Teams has a master on/off switch for guest access and a variety of settings available to control what guests can do in a team.</span></span> <span data-ttu-id="4d4a0-123">主版參數時，**允許小組中的來賓存取**必須**上**的來賓存取在小組中運作。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-123">The master switch, **Allow guest access in Teams** must be **On** for guest access to work in Teams.</span></span>

<span data-ttu-id="4d4a0-124">請檢查可確保 Teams 中的來賓存取已啟用，以根據貴公司的來賓設定任何調整需求。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-124">Check to ensure that guest access is enabled in Teams and make any adjustment to the guest settings based on your business needs.</span></span> <span data-ttu-id="4d4a0-125">請記住，這些設定會影響所有的 microsoft teams。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-125">Keep in mind that these settings affect all teams.</span></span>

![螢幕擷取畫面的 Teams 來賓存取切換](media/teams-guest-access-toggle-on.png)

<span data-ttu-id="4d4a0-127">若要設定 microsoft Teams 來賓存取設定</span><span class="sxs-lookup"><span data-stu-id="4d4a0-127">To set Teams guest access settings</span></span>

1. <span data-ttu-id="4d4a0-128">登入 Microsoft 365 系統管理中心， [https://admin.microsoft.com](https://admin.microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-128">Log in to the Microsoft 365 admin center at [https://admin.microsoft.com](https://admin.microsoft.com).</span></span>
2. <span data-ttu-id="4d4a0-129">在左導覽中，按一下 [**全部顯示**]。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-129">In the left navigation, click **Show all**.</span></span>
3. <span data-ttu-id="4d4a0-130">**系統管理中心**中，按一下 [ **microsoft Teams**。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-130">Under **Admin centers**, click **Teams**.</span></span>
4. <span data-ttu-id="4d4a0-131">在 microsoft Teams 系統管理中心中，在左側導覽中，依序展開 [**全組織的設定**，按一下 [**來賓存取**。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-131">In the Teams admin center, in the left navigation, expand **Org-wide settings** and click **Guest access**.</span></span>
5. <span data-ttu-id="4d4a0-132">確定**允許小組中的來賓存取**設定為**上**。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-132">Ensure that **Allow guest access in Teams** is set to **On**.</span></span>
6. <span data-ttu-id="4d4a0-133">額外的來賓設定，讓任何想要的變更，然後按一下 [**儲存**。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-133">Make any desired changes to the additional guest settings, and then click **Save**.</span></span>

> [!NOTE]
> <span data-ttu-id="4d4a0-134">設定後將它開啟成為作用中的 Teams 來賓的可能需要最多 24 個小時。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-134">It may take up to twenty-four hours for the Teams guest setting to become active after you turn it on.</span></span>

## <a name="office-365-groups-guest-settings"></a><span data-ttu-id="4d4a0-135">Office 365 群組的來賓設定</span><span class="sxs-lookup"><span data-stu-id="4d4a0-135">Office 365 Groups guest settings</span></span>

<span data-ttu-id="4d4a0-136">小組會使用 Office 365 群組的小組成員資格。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-136">Teams uses Office 365 Groups for team membership.</span></span> <span data-ttu-id="4d4a0-137">為了讓小組中的來賓存取運作，必須在開啟 Office 365 群組來賓設定。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-137">The Office 365 Groups guest settings must be turned on in order for guest access in Teams to work.</span></span>

![Office 365 群組的螢幕擷取畫面 guest Microsoft 365 系統管理中心中的設定](media/office-365-groups-guest-settings.png)

<span data-ttu-id="4d4a0-139">若要設定 Office 365 群組的來賓</span><span class="sxs-lookup"><span data-stu-id="4d4a0-139">To set Office 365 Groups guest settings</span></span>

1. <span data-ttu-id="4d4a0-140">在 Microsoft 365 系統管理中心，在左側導覽中，展開 [**設定**]。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-140">In the Microsoft 365 admin center, in the left navigation, expand **Settings**.</span></span>
2. <span data-ttu-id="4d4a0-141">按一下 [**服務 & 增益集**]。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-141">Click **Services & add-ins**.</span></span>
3. <span data-ttu-id="4d4a0-142">在清單中，按一下 [ **Office 365 群組**。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-142">In the list, click **Office 365 Groups**.</span></span>
4. <span data-ttu-id="4d4a0-143">請確定，**讓外部組織存取群組內容的群組成員**，**讓群組擁有者新增至群組在組織外的人員**] 核取方塊會同時檢查。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-143">Ensure that the **Let group members outside your organization access group content** and **Let group owners add people outside your organization to groups** check boxes are both checked.</span></span>
5. <span data-ttu-id="4d4a0-144">如果您所做的變更，按一下 [**儲存變更**。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-144">If you made changes, click **Save changes**.</span></span>


## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="4d4a0-145">共用設定的 SharePoint 組織層級</span><span class="sxs-lookup"><span data-stu-id="4d4a0-145">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="4d4a0-146">為了讓訪客能夠存取 Teams 中的檔案，SharePoint 組織層級共用設定必須允許與來賓共用。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-146">In order for guests to have access to files in Teams, the SharePoint organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="4d4a0-147">組織層級設定會決定哪些設定可供個別的網站，包括 microsoft teams 相關聯的網站。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-147">The organization-level settings determine what settings are available for individual sites, including sites associated with teams.</span></span> <span data-ttu-id="4d4a0-148">網站設定不能更寬鬆比組織層級的設定。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-148">Site settings cannot be more permissive than the organization-level settings.</span></span>

<span data-ttu-id="4d4a0-149">如果您想要允許的檔案和資料夾與匿名使用者共用，選擇 [**任何人**]。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-149">If you want to allow file and folder sharing with anonymous users, choose **Anyone**.</span></span> <span data-ttu-id="4d4a0-150">如果您想要確定所有來賓都需要驗證，請選擇 [**新增] 和 [現有的來賓**。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-150">If you want to ensure that all guests have to authenticate, choose **New and existing guests**.</span></span> <span data-ttu-id="4d4a0-151">選擇 [將您的組織中任何網站所需的最寬鬆] 設定。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-151">Choose the most permissive setting that will be needed by any site in your organization.</span></span>

![螢幕擷取畫面的 SharePoint 組織層級共用設定](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="4d4a0-153">若要設定共用設定的 SharePoint 組織層級</span><span class="sxs-lookup"><span data-stu-id="4d4a0-153">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="4d4a0-154">在 Microsoft 365 系統管理中心，在左側導覽中，[**系統管理中心**中，按一下 [ **SharePoint**]。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-154">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="4d4a0-155">在 SharePoint 系統管理中心中，在左側導覽中，按一下 [**共用**]。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-155">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="4d4a0-156">請確定該外部共用 SharePoint 設為**任何人**或**新增和現有的來賓**。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-156">Ensure that external sharing for SharePoint is set to **Anyone** or **New and existing guests**.</span></span>
4. <span data-ttu-id="4d4a0-157">如果您所做的變更，請按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-157">If you made changes, click **Save**.</span></span>


## <a name="sharepoint-organization-level-default-link-settings"></a><span data-ttu-id="4d4a0-158">SharePoint 組織層級預設連結設定</span><span class="sxs-lookup"><span data-stu-id="4d4a0-158">SharePoint organization level default link settings</span></span>

<span data-ttu-id="4d4a0-159">預設檔案和資料夾連結設定會決定哪一個連結選項向使用者顯示預設情況下使用者共用的檔案或資料夾時。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-159">The default file and folder link settings determine which link option is shown to the user by default when they share a file or folder.</span></span> <span data-ttu-id="4d4a0-160">使用者可以將連結類型變更為下列其中一個其他選項共用視之前。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-160">Users can change the link type to one of the other options before sharing if desired.</span></span>

<span data-ttu-id="4d4a0-161">請記住此設定會影響所有的 microsoft teams 和貴組織中的 SharePoint 網站。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-161">Keep in mind that this setting affects all teams and SharePoint sites in your organization.</span></span>

<span data-ttu-id="4d4a0-162">選擇 [當使用者共用檔案及資料夾，依預設會選取連結的類型：</span><span class="sxs-lookup"><span data-stu-id="4d4a0-162">Choose the type of link that's selected by default when users share files and folders:</span></span>

- <span data-ttu-id="4d4a0-163">**任何人] 連結**-如果您預期在具有匿名使用者共用檔案和資料夾的許多選擇此選項。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-163">**Anyone with the link** - Choose this option if you expect to share a lot of files and folders with anonymous users.</span></span> <span data-ttu-id="4d4a0-164">如果您想要允許*任何人*的連結，但擔心意外匿名共用，請考慮下列其中一個其他選項為預設值。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-164">If you want to allow *Anyone* links but are concerned about accidental anonymous sharing, consider one of the other options as the default.</span></span> <span data-ttu-id="4d4a0-165">如果您已啟用**的任何人**共用，此連結類型只有。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-165">This link type is only available if you've enabled **Anyone** sharing.</span></span>
- <span data-ttu-id="4d4a0-166">**只有在您的組織中的人員**-如果您預期大部分的檔案和資料夾共用您的組織內的人員都必須選擇此選項。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-166">**Only people in your organization** - Choose this option if you expect most file and folder sharing to be with people inside your organization.</span></span>
- <span data-ttu-id="4d4a0-167">**特定人員**-如果您預期執行許多檔案和資料夾與來賓共用，請考慮此選項。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-167">**Specific people** - Consider this option if you expect to do a lot of file and folder sharing with guests.</span></span> <span data-ttu-id="4d4a0-168">這種類型的連結與來賓運作，以及需要進行驗證。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-168">This type of link works with guests and requires them to authenticate.</span></span>
 
![螢幕擷取畫面的 SharePoint 組織層級檔案和資料夾共用設定](media/sharepoint-organization-files-folders-sharing-settings.png)


<span data-ttu-id="4d4a0-170">若要設定 SharePoint 組織層級預設值] 連結</span><span class="sxs-lookup"><span data-stu-id="4d4a0-170">To set the SharePoint organization level default link settings</span></span>

1. <span data-ttu-id="4d4a0-171">瀏覽至 SharePoint 系統管理中心的 [共用] 頁面上。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-171">Navigate to the Sharing page in the SharePoint admin center.</span></span>
2. <span data-ttu-id="4d4a0-172">[**檔案] 和 [資料夾] 連結**，選取預設共用您想要使用的連結。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-172">Under **File and folder links**, select the default sharing link that you want to use.</span></span>
3. <span data-ttu-id="4d4a0-173">如果您所做的變更，請按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-173">If you made changes, click **Save**.</span></span>

## <a name="create-a-team"></a><span data-ttu-id="4d4a0-174">建立小組</span><span class="sxs-lookup"><span data-stu-id="4d4a0-174">Create a team</span></span>

<span data-ttu-id="4d4a0-175">下一步是建立您計劃要用於來賓與共同作業小組。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-175">The next step is to create the team that you plan to use for collaborating with guests.</span></span>

<span data-ttu-id="4d4a0-176">若要建立小組</span><span class="sxs-lookup"><span data-stu-id="4d4a0-176">To create a team</span></span>
1. <span data-ttu-id="4d4a0-177">在小組，[ **Teams** ] 索引標籤中，按一下 [**加入或建立小組**在左邊窗格的底部。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-177">In Teams, on the **Teams** tab, click **Join or create a team** at the bottom of the left pane.</span></span>
2. <span data-ttu-id="4d4a0-178">按一下 [**建立小組**]。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-178">Click **Create a team**.</span></span>
3. <span data-ttu-id="4d4a0-179">按一下 [**建立從頭小組**]。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-179">Click **Build a team from scratch**.</span></span>
4. <span data-ttu-id="4d4a0-180">選擇 [**私人**或**公開**。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-180">Choose **Private** or **Public**.</span></span>
5. <span data-ttu-id="4d4a0-181">輸入的名稱和描述小組、，然後按一下 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-181">Type a name and description for the team, and then click **Create**.</span></span>
6. <span data-ttu-id="4d4a0-182">按一下 [**略過**。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-182">Click **Skip**.</span></span>

<span data-ttu-id="4d4a0-183">我們將稍後邀請使用者。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-183">We'll invite users later.</span></span> <span data-ttu-id="4d4a0-184">接下來，務必檢查小組與相關聯的 SharePoint 網站的網站層級共用設定。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-184">Next, it's important to check the site-level sharing settings for the SharePoint site that is associated with the team.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="4d4a0-185">SharePoint 網站層級共用設定</span><span class="sxs-lookup"><span data-stu-id="4d4a0-185">SharePoint site level sharing settings</span></span>

<span data-ttu-id="4d4a0-186">請檢查以確保它們允許您想要此小組的存取類型的網站層級共用設定。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-186">Check the site-level sharing settings to make sure that they allow the type of access that you want for this team.</span></span> <span data-ttu-id="4d4a0-187">例如，如果您設定組織層級設定為**任何人**，但您想要為此小組進行驗證的所有來賓，然後進行確認網站層級共用設定設為 [**新增] 和 [現有的來賓**。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-187">For example, if you set the organization-level settings to **Anyone**, but you want all guests to authenticate for this team, then make sure the site-level sharing settings are set to **New and existing guests**.</span></span>

![螢幕擷取畫面的 SharePoint 網站外部共用設定](media/sharepoint-site-external-sharing-settings.png)


<span data-ttu-id="4d4a0-189">若要設定網站層級共用設定</span><span class="sxs-lookup"><span data-stu-id="4d4a0-189">To set site-level sharing settings</span></span>
1. <span data-ttu-id="4d4a0-190">在 SharePoint 系統管理中心中，在左側導覽中，展開 [**站台**，按一下 [**作用中網站**。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-190">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="4d4a0-191">選取您剛建立小組網站。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-191">Select the site for the team that you just created.</span></span>
3. <span data-ttu-id="4d4a0-192">在功能區中，按一下 [**共用**]。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-192">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="4d4a0-193">請確定該共用設為**任何人**或**新增和現有的來賓**。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-193">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="4d4a0-194">如果您所做的變更，請按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-194">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="4d4a0-195">邀請使用者</span><span class="sxs-lookup"><span data-stu-id="4d4a0-195">Invite users</span></span>

<span data-ttu-id="4d4a0-196">來賓共用設定現在會進行設定，讓您可以開始將內部使用者和訪客新增至您的小組。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-196">Guest sharing settings are now configured, so you can start adding internal users and guests to your team.</span></span> 

<span data-ttu-id="4d4a0-197">若要邀請給小組的內部使用者</span><span class="sxs-lookup"><span data-stu-id="4d4a0-197">To invite internal users to a team</span></span>
1. <span data-ttu-id="4d4a0-198">在 [小組成員，按一下 [**更多選項]** (**\*\***)，然後按一下 [**新增成員**。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-198">In the team, click **More options** (**\*\*\***), and then click **Add member**.</span></span>
2. <span data-ttu-id="4d4a0-199">輸入您想要邀請的人員名稱。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-199">Type the name of the person who you want to invite.</span></span>
3. <span data-ttu-id="4d4a0-200">Click **Add**, and then click **Close**.</span><span class="sxs-lookup"><span data-stu-id="4d4a0-200">Click **Add**, and then click **Close**.</span></span>

<span data-ttu-id="4d4a0-201">若要邀請給小組的來賓</span><span class="sxs-lookup"><span data-stu-id="4d4a0-201">To invite guests to a team</span></span>
1. <span data-ttu-id="4d4a0-202">在 [小組成員，按一下 [**更多選項]** (**\*\***)，然後按一下 [**新增成員**。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-202">In the team, click **More options** (**\*\*\***), and then click **Add member**.</span></span>
2. <span data-ttu-id="4d4a0-203">輸入您想要邀請來賓顯示的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-203">Type the email address of the guest who you want to invite.</span></span>
3. <span data-ttu-id="4d4a0-204">按一下 [**編輯來賓資訊**。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-204">Click **Edit guest information**.</span></span>
4. <span data-ttu-id="4d4a0-205">輸入來賓顯示的完整名稱，然後按一下 [核取記號。</span><span class="sxs-lookup"><span data-stu-id="4d4a0-205">Type the guest's full name and click the check mark.</span></span>
5. <span data-ttu-id="4d4a0-206">Click **Add**, and then click **Close**.</span><span class="sxs-lookup"><span data-stu-id="4d4a0-206">Click **Add**, and then click **Close**.</span></span>

## <a name="see-also"></a><span data-ttu-id="4d4a0-207">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d4a0-207">See Also</span></span>

