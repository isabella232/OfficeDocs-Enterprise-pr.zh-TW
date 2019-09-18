---
title: 與網站中的來賓共同作業
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: 了解如何在 SharePoint 網站中的來賓與共同作業。
ms.openlocfilehash: 4b68b50fec4322f12c24969bdd71e7d9c0fda245
ms.sourcegitcommit: d388c76d25ca67f240db97f7bfc90f0991b0e7f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "37017311"
---
# <a name="collaborate-with-guests-in-a-site"></a><span data-ttu-id="b2376-103">與網站中的來賓共同作業</span><span class="sxs-lookup"><span data-stu-id="b2376-103">Collaborate with guests in a site</span></span>

<span data-ttu-id="b2376-104">如果您需要整個文件、 資料和清單與來賓共同作業，您可以使用 SharePoint 網站。</span><span class="sxs-lookup"><span data-stu-id="b2376-104">If you need to collaborate with guests across documents, data, and lists, you can use a SharePoint site.</span></span> <span data-ttu-id="b2376-105">新式的 SharePoint 網站連線到 Office 365 群組以管理站台成員資格，並提供其他共同作業工具，例如共用的信箱和行事曆。</span><span class="sxs-lookup"><span data-stu-id="b2376-105">Modern SharePoint sites are connected to Office 365 Groups which can manage the site membership and provide additional collaboration tools such as a shared mailbox and calendar.</span></span>

<span data-ttu-id="b2376-106">在本文中，我們會逐步設定來賓與共同作業的 SharePoint 網站所需的 Microsoft 365 組態步驟。</span><span class="sxs-lookup"><span data-stu-id="b2376-106">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up a SharePoint site for collaboration with guests.</span></span>

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="b2376-107">Azure 的組織關聯性設定</span><span class="sxs-lookup"><span data-stu-id="b2376-107">Azure Organizational relationships settings</span></span>

<span data-ttu-id="b2376-108">Microsoft 365 中共用是由控管最高層級 Azure Active Directory 中的組織關聯性設定。</span><span class="sxs-lookup"><span data-stu-id="b2376-108">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="b2376-109">如果共用的來賓已停用，或限制在 Azure AD 中，這會覆寫任何您在 Microsoft 365 中設定的共用設定。</span><span class="sxs-lookup"><span data-stu-id="b2376-109">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="b2376-110">檢查以確保未封鎖來賓與共用的組織關聯性設定。</span><span class="sxs-lookup"><span data-stu-id="b2376-110">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![螢幕擷取畫面的 Azure Active Directory 組織關聯性設定頁面](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="b2376-112">若要設定組織關聯性設定</span><span class="sxs-lookup"><span data-stu-id="b2376-112">To set organizational relationship settings</span></span>

1. <span data-ttu-id="b2376-113">登入 Microsoft Azure 在[https://portal.azure.com](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="b2376-113">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="b2376-114">在左導覽中，按一下 [ **Azure Active Directory**]。</span><span class="sxs-lookup"><span data-stu-id="b2376-114">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="b2376-115">在 [**概觀**] 窗格中，按一下 [**組織關聯性**。</span><span class="sxs-lookup"><span data-stu-id="b2376-115">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="b2376-116">在**組織關聯性**] 窗格中，按一下 [**設定**]。</span><span class="sxs-lookup"><span data-stu-id="b2376-116">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="b2376-117">確保**系統管理員和來賓邀請者角色中的使用者可以邀請**和**成員可以邀請**都會設**為 [是]**。</span><span class="sxs-lookup"><span data-stu-id="b2376-117">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="b2376-118">如果您所做的變更，請按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="b2376-118">If you made changes, click **Save**.</span></span>

<span data-ttu-id="b2376-119">請注意 [**共同作業限制**] 區段中的設定。</span><span class="sxs-lookup"><span data-stu-id="b2376-119">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="b2376-120">請確定不封鎖的網域的來賓，您想要與共同作業。</span><span class="sxs-lookup"><span data-stu-id="b2376-120">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="office-365-groups-guest-settings"></a><span data-ttu-id="b2376-121">Office 365 群組的來賓設定</span><span class="sxs-lookup"><span data-stu-id="b2376-121">Office 365 Groups guest settings</span></span>

<span data-ttu-id="b2376-122">新式的 SharePoint 網站使用 Office 365 群組來控制網站存取權。</span><span class="sxs-lookup"><span data-stu-id="b2376-122">Modern SharePoint sites use Office 365 Groups to control site access.</span></span> <span data-ttu-id="b2376-123">Office 365 群組的來賓設定必須開啟 SharePoint 網站中的來賓存取工作的順序。</span><span class="sxs-lookup"><span data-stu-id="b2376-123">The Office 365 Groups guest settings must be turned on in order for guest access in SharePoint sites to work.</span></span>

![Office 365 群組的螢幕擷取畫面 guest Microsoft 365 系統管理中心中的設定](media/office-365-groups-guest-settings.png)

<span data-ttu-id="b2376-125">若要設定 Office 365 群組的來賓</span><span class="sxs-lookup"><span data-stu-id="b2376-125">To set Office 365 Groups guest settings</span></span>

1. <span data-ttu-id="b2376-126">在 Microsoft 365 系統管理中心，在左側導覽中，展開 [**設定**]。</span><span class="sxs-lookup"><span data-stu-id="b2376-126">In the Microsoft 365 admin center, in the left navigation, expand **Settings**.</span></span>
2. <span data-ttu-id="b2376-127">按一下 [**服務 & 增益集**]。</span><span class="sxs-lookup"><span data-stu-id="b2376-127">Click **Services & add-ins**.</span></span>
3. <span data-ttu-id="b2376-128">在清單中，按一下 [ **Office 365 群組**。</span><span class="sxs-lookup"><span data-stu-id="b2376-128">In the list, click **Office 365 Groups**.</span></span>
4. <span data-ttu-id="b2376-129">請確定，**讓外部組織存取群組內容的群組成員**，**讓群組擁有者新增至群組在組織外的人員**] 核取方塊會同時檢查。</span><span class="sxs-lookup"><span data-stu-id="b2376-129">Ensure that the **Let group members outside your organization access group content** and **Let group owners add people outside your organization to groups** check boxes are both checked.</span></span>
5. <span data-ttu-id="b2376-130">如果您所做的變更，按一下 [**儲存變更**。</span><span class="sxs-lookup"><span data-stu-id="b2376-130">If you made changes, click **Save changes**.</span></span>


## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="b2376-131">共用設定的 SharePoint 組織層級</span><span class="sxs-lookup"><span data-stu-id="b2376-131">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="b2376-132">為了讓訪客能夠存取 SharePoint 網站，SharePoint 組織層級共用設定必須允許與來賓共用。</span><span class="sxs-lookup"><span data-stu-id="b2376-132">In order for guests to have access to SharePoint sites, the SharePoint organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="b2376-133">組織層級設定會決定哪些設定可供個別的網站。</span><span class="sxs-lookup"><span data-stu-id="b2376-133">The organization-level settings determine what settings are available for individual sites.</span></span> <span data-ttu-id="b2376-134">網站設定不能更寬鬆比組織層級的設定。</span><span class="sxs-lookup"><span data-stu-id="b2376-134">Site settings cannot be more permissive than the organization-level settings.</span></span>

<span data-ttu-id="b2376-135">如果您想要允許的檔案和資料夾與匿名使用者共用，選擇 [**任何人**]。</span><span class="sxs-lookup"><span data-stu-id="b2376-135">If you want to allow file and folder sharing with anonymous users, choose **Anyone**.</span></span> <span data-ttu-id="b2376-136">如果您想要確定所有來賓都需要驗證，請選擇 [**新增] 和 [現有的來賓**。</span><span class="sxs-lookup"><span data-stu-id="b2376-136">If you want to ensure that all guests have to authenticate, choose **New and existing guests**.</span></span> <span data-ttu-id="b2376-137">選擇 [將您的組織中任何網站所需的最寬鬆] 設定。</span><span class="sxs-lookup"><span data-stu-id="b2376-137">Choose the most permissive setting that will be needed by any site in your organization.</span></span>

![螢幕擷取畫面的 SharePoint 組織層級共用設定](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="b2376-139">若要設定共用設定的 SharePoint 組織層級</span><span class="sxs-lookup"><span data-stu-id="b2376-139">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="b2376-140">在 Microsoft 365 系統管理中心，在左側導覽中，[**系統管理中心**中，按一下 [ **SharePoint**]。</span><span class="sxs-lookup"><span data-stu-id="b2376-140">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="b2376-141">在 SharePoint 系統管理中心中，在左側導覽中，按一下 [**共用**]。</span><span class="sxs-lookup"><span data-stu-id="b2376-141">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="b2376-142">請確定該外部共用 SharePoint 設為**任何人**或**新增和現有的來賓**。</span><span class="sxs-lookup"><span data-stu-id="b2376-142">Ensure that external sharing for SharePoint is set to **Anyone** or **New and existing guests**.</span></span>
4. <span data-ttu-id="b2376-143">如果您所做的變更，請按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="b2376-143">If you made changes, click **Save**.</span></span>

## <a name="create-a-site"></a><span data-ttu-id="b2376-144">建立網站</span><span class="sxs-lookup"><span data-stu-id="b2376-144">Create a site</span></span>

<span data-ttu-id="b2376-145">下一步是建立您計劃要用於來賓與共同作業網站。</span><span class="sxs-lookup"><span data-stu-id="b2376-145">The next step is to create the site that you plan to use for collaborating with guests.</span></span>

<span data-ttu-id="b2376-146">若要建立網站</span><span class="sxs-lookup"><span data-stu-id="b2376-146">To create a site</span></span>
1. <span data-ttu-id="b2376-147">在 SharePoint 系統管理中心中，[**網站**]，按一下 [**作用中網站**。</span><span class="sxs-lookup"><span data-stu-id="b2376-147">In the SharePoint admin center, under **Sites**, click **Active sites**.</span></span>
2. <span data-ttu-id="b2376-148">按一下 [建立]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b2376-148">Click **Create**.</span></span>
3. <span data-ttu-id="b2376-149">按一下 [**小組網站**。</span><span class="sxs-lookup"><span data-stu-id="b2376-149">Click **Team site**.</span></span>
4. <span data-ttu-id="b2376-150">輸入網站名稱，然後輸入群組擁有者 （網站擁有者） 的名稱。</span><span class="sxs-lookup"><span data-stu-id="b2376-150">Type a site name and enter a name for the Group owner (site owner).</span></span>
5. <span data-ttu-id="b2376-151">[**進階設定**]，選擇 [是否您想要這是公用或私用網站。</span><span class="sxs-lookup"><span data-stu-id="b2376-151">Under **Advanced settings**, choose if you want this to be a public or private site.</span></span>
6. <span data-ttu-id="b2376-152">按 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b2376-152">Click **Next**.</span></span>
7. <span data-ttu-id="b2376-153">按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="b2376-153">Click **Finish**.</span></span>

<span data-ttu-id="b2376-154">我們將稍後邀請使用者。</span><span class="sxs-lookup"><span data-stu-id="b2376-154">We'll invite users later.</span></span> <span data-ttu-id="b2376-155">接下來，務必要檢查此網站的網站層級共用設定。</span><span class="sxs-lookup"><span data-stu-id="b2376-155">Next, it's important to check the site-level sharing settings for this site.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="b2376-156">SharePoint 網站層級共用設定</span><span class="sxs-lookup"><span data-stu-id="b2376-156">SharePoint site level sharing settings</span></span>

<span data-ttu-id="b2376-157">請檢查以確保它們允許您要用於此網站的存取類型的網站層級共用設定。</span><span class="sxs-lookup"><span data-stu-id="b2376-157">Check the site-level sharing settings to make sure that they allow the type of access that you want for this site.</span></span> <span data-ttu-id="b2376-158">例如，如果您設定組織層級設定為**任何人**，但您想要驗證這個網站的所有來賓，然後進行確認網站層級共用設定設為 [**新增] 和 [現有的來賓**。</span><span class="sxs-lookup"><span data-stu-id="b2376-158">For example, if you set the organization-level settings to **Anyone**, but you want all guests to authenticate for this site, then make sure the site-level sharing settings are set to **New and existing guests**.</span></span>

<span data-ttu-id="b2376-159">請注意，無法共用網站，在具有匿名使用者 （**任何人都**設定），但是可以個別檔案和資料夾。</span><span class="sxs-lookup"><span data-stu-id="b2376-159">Note that the site cannot be shared with anonymous users (**Anyone** setting), but individual files and folders can.</span></span>

![螢幕擷取畫面的 SharePoint 網站外部共用設定](media/sharepoint-site-external-sharing-settings.png)

<span data-ttu-id="b2376-161">若要設定網站層級共用設定</span><span class="sxs-lookup"><span data-stu-id="b2376-161">To set site-level sharing settings</span></span>
1. <span data-ttu-id="b2376-162">在 SharePoint 系統管理中心中，在左側導覽中，展開 [**站台**，按一下 [**作用中網站**。</span><span class="sxs-lookup"><span data-stu-id="b2376-162">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="b2376-163">選取您剛建立的網站。</span><span class="sxs-lookup"><span data-stu-id="b2376-163">Select the site that you just created.</span></span>
3. <span data-ttu-id="b2376-164">在功能區中，按一下 [**共用**]。</span><span class="sxs-lookup"><span data-stu-id="b2376-164">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="b2376-165">請確定該共用設為**任何人**或**新增和現有的來賓**。</span><span class="sxs-lookup"><span data-stu-id="b2376-165">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="b2376-166">如果您所做的變更，請按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="b2376-166">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="b2376-167">邀請使用者</span><span class="sxs-lookup"><span data-stu-id="b2376-167">Invite users</span></span>

<span data-ttu-id="b2376-168">來賓共用設定現在會進行設定，讓您可以開始將內部使用者和訪客新增至您的網站。</span><span class="sxs-lookup"><span data-stu-id="b2376-168">Guest sharing settings are now configured, so you can start adding internal users and guests to your site.</span></span> <span data-ttu-id="b2376-169">讓我們將持續加入那里使用者網站存取權是透過相關聯的 Office 365 群組，來控制。</span><span class="sxs-lookup"><span data-stu-id="b2376-169">Site access is controlled through the associated Office 365 Group, so we'll be adding users there.</span></span>

<span data-ttu-id="b2376-170">若要邀請內部使用者至群組</span><span class="sxs-lookup"><span data-stu-id="b2376-170">To invite internal users to a group</span></span>
1. <span data-ttu-id="b2376-171">瀏覽至您要新增使用者的網站。</span><span class="sxs-lookup"><span data-stu-id="b2376-171">Navigate to the site where you want to add users.</span></span>
2. <span data-ttu-id="b2376-172">按一下右上角的 [**成員**]。</span><span class="sxs-lookup"><span data-stu-id="b2376-172">Click **Members** in the upper right.</span></span>
3. <span data-ttu-id="b2376-173">按一下 [新增成員]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b2376-173">Click **Add members**.</span></span>
4. <span data-ttu-id="b2376-174">輸入的名稱或電子郵件地址，您想要邀請至網站的使用者，然後按一下 [**儲存**。</span><span class="sxs-lookup"><span data-stu-id="b2376-174">Type the names or email addresses of the users that you want to invite to the site, and then click **Save**.</span></span>

<span data-ttu-id="b2376-175">來賓使用者無法新增從站台。</span><span class="sxs-lookup"><span data-stu-id="b2376-175">Guest users can't be added from the site.</span></span> <span data-ttu-id="b2376-176">您必須將它們新增使用網頁型 Outlook。</span><span class="sxs-lookup"><span data-stu-id="b2376-176">You need to add them using Outlook on the web.</span></span>

<span data-ttu-id="b2376-177">若要邀請來賓至網站</span><span class="sxs-lookup"><span data-stu-id="b2376-177">To invite guests to a site</span></span>
1. <span data-ttu-id="b2376-178">在 Outlook 網頁版、 在 [**群組**] 中按一下您要新增成員的群組。</span><span class="sxs-lookup"><span data-stu-id="b2376-178">In Outlook on the web, under **Groups**, click the group where you want to add members.</span></span>
2. <span data-ttu-id="b2376-179">開啟群組連絡人卡片、，然後按一下 [**更多選項]** （...）] 下的 [**新增成員**。</span><span class="sxs-lookup"><span data-stu-id="b2376-179">Open the group contact card, and then, under **More options** (...), click **Add members**.</span></span>
3. <span data-ttu-id="b2376-180">輸入您想要邀請，來賓電子郵件地址，然後按一下 [**新增]**。</span><span class="sxs-lookup"><span data-stu-id="b2376-180">Type the email addresses of the guests that you want to invite, and then click **Add**.</span></span>
4. <span data-ttu-id="b2376-181">按一下 [關閉]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b2376-181">Click **Close**.</span></span>

## <a name="see-also"></a><span data-ttu-id="b2376-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2376-182">See Also</span></span>
