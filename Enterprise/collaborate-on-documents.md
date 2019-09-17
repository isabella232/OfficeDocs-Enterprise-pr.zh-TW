---
title: 與文件上的 guests 共同作業
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: 了解如何在 SharePoint 和 OneDrive 文件上的 guests 與共同作業。
ms.openlocfilehash: c0c74f2457e9b25b37355c58ed18f120261e3364
ms.sourcegitcommit: 3bba97053caf5f9cff0ef3205afb7869535f38bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2019
ms.locfileid: "36992402"
---
# <a name="collaborate-with-guests-on-a-document"></a><span data-ttu-id="23950-103">與文件上的 guests 共同作業</span><span class="sxs-lookup"><span data-stu-id="23950-103">Collaborate with guests on a document</span></span>

<span data-ttu-id="23950-104">如果您需要在 SharePoint 或 OneDrive 中的文件上的 guests 與共同作業，您可以傳送這些共用連結至文件。</span><span class="sxs-lookup"><span data-stu-id="23950-104">If you need to collaborate with guests on documents in SharePoint or OneDrive, you can send them a sharing link to the document.</span></span> <span data-ttu-id="23950-105">在本文中，我們會逐步設定共用連結 SharePoint 和 OneDrive 所需的 Microsoft 365 組態步驟。</span><span class="sxs-lookup"><span data-stu-id="23950-105">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up sharing links for SharePoint and OneDrive.</span></span>

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="23950-106">Azure 的組織關聯性設定</span><span class="sxs-lookup"><span data-stu-id="23950-106">Azure Organizational relationships settings</span></span>

<span data-ttu-id="23950-107">Microsoft 365 中共用是由控管最高層級 Azure Active Directory 中的組織關聯性設定。</span><span class="sxs-lookup"><span data-stu-id="23950-107">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="23950-108">如果共用的來賓已停用，或限制在 Azure AD 中，這會覆寫任何您在 Microsoft 365 中設定的共用設定。</span><span class="sxs-lookup"><span data-stu-id="23950-108">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="23950-109">檢查以確保未封鎖來賓與共用的組織關聯性設定。</span><span class="sxs-lookup"><span data-stu-id="23950-109">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![螢幕擷取畫面的 Azure Active Directory 組織關聯性設定頁面](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="23950-111">若要設定組織關聯性設定</span><span class="sxs-lookup"><span data-stu-id="23950-111">To set organizational relationship settings</span></span>

1. <span data-ttu-id="23950-112">登入 Microsoft Azure 在[https://portal.azure.com](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="23950-112">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="23950-113">在左導覽中，按一下 [ **Azure Active Directory**]。</span><span class="sxs-lookup"><span data-stu-id="23950-113">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="23950-114">在 [**概觀**] 窗格中，按一下 [**組織關聯性**。</span><span class="sxs-lookup"><span data-stu-id="23950-114">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="23950-115">在**組織關聯性**] 窗格中，按一下 [**設定**]。</span><span class="sxs-lookup"><span data-stu-id="23950-115">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="23950-116">確保**系統管理員和來賓邀請者角色中的使用者可以邀請**和**成員可以邀請**都會設**為 [是]**。</span><span class="sxs-lookup"><span data-stu-id="23950-116">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="23950-117">如果您所做的變更，請按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="23950-117">If you made changes, click **Save**.</span></span>

<span data-ttu-id="23950-118">請注意 [**共同作業限制**] 區段中的設定。</span><span class="sxs-lookup"><span data-stu-id="23950-118">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="23950-119">請確定不封鎖的網域的來賓，您想要與共同作業。</span><span class="sxs-lookup"><span data-stu-id="23950-119">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="23950-120">共用設定的 SharePoint 組織層級</span><span class="sxs-lookup"><span data-stu-id="23950-120">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="23950-121">為了讓訪客能夠存取 SharePoint 或 OneDrive 中的文件，SharePoint 和 OneDrive 組織層級共用設定必須允許與來賓共用。</span><span class="sxs-lookup"><span data-stu-id="23950-121">In order for guests to have access to a document in SharePoint or OneDrive, the SharePoint and OneDrive organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="23950-122">SharePoint 的組織層級設定會決定哪些設定可供個別的 SharePoint 網站。</span><span class="sxs-lookup"><span data-stu-id="23950-122">The organization-level settings for SharePoint determine what settings are available for individual SharePoint sites.</span></span> <span data-ttu-id="23950-123">網站設定不能更寬鬆比組織層級的設定。</span><span class="sxs-lookup"><span data-stu-id="23950-123">Site settings cannot be more permissive than the organization-level settings.</span></span> <span data-ttu-id="23950-124">OneDrive 的組織層級設定會決定在使用者的 OneDrive 文件庫中時可用的共用層級。</span><span class="sxs-lookup"><span data-stu-id="23950-124">The organization-level setting for OneDrive determines what level of sharing is available in users' OneDrive libraries.</span></span>

<span data-ttu-id="23950-125">對於 SharePiont 和 OneDrive，如果您想要允許的檔案和資料夾與匿名使用者共用，選擇 [**任何人**。</span><span class="sxs-lookup"><span data-stu-id="23950-125">For SharePiont and OneDrive, if you want to allow file and folder sharing with anonymous users, choose **Anyone**.</span></span> <span data-ttu-id="23950-126">如果您想要確定所有來賓都需要驗證，請選擇 [**新增] 和 [現有的來賓**。</span><span class="sxs-lookup"><span data-stu-id="23950-126">If you want to ensure that all guests have to authenticate, choose **New and existing guests**.</span></span> 

<span data-ttu-id="23950-127">For SharePoint，選擇 [將您的組織中任何網站所需的最寬鬆] 設定。</span><span class="sxs-lookup"><span data-stu-id="23950-127">For SharePoint, choose the most permissive setting that will be needed by any site in your organization.</span></span>

![螢幕擷取畫面的 SharePoint 組織層級共用設定](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="23950-129">若要設定共用設定的 SharePoint 組織層級</span><span class="sxs-lookup"><span data-stu-id="23950-129">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="23950-130">在 Microsoft 365 系統管理中心，在左側導覽中，[**系統管理中心**中，按一下 [ **SharePoint**]。</span><span class="sxs-lookup"><span data-stu-id="23950-130">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="23950-131">在 SharePoint 系統管理中心中，在左側導覽中，按一下 [**共用**]。</span><span class="sxs-lookup"><span data-stu-id="23950-131">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="23950-132">確定 SharePoint 或 OneDrive 外部共用設定為**任何人**或**新增和現有的來賓**。</span><span class="sxs-lookup"><span data-stu-id="23950-132">Ensure that external sharing for SharePoint or OneDrive is set to **Anyone** or **New and existing guests**.</span></span> <span data-ttu-id="23950-133">（請注意 [OneDrive] 設定不能更寬鬆比 SharePoint 設定）。</span><span class="sxs-lookup"><span data-stu-id="23950-133">(Note that the OneDrive setting cannot be more permissive than the SharePoint setting.)</span></span>
4. <span data-ttu-id="23950-134">如果您所做的變更，請按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="23950-134">If you made changes, click **Save**.</span></span>

## <a name="sharepoint-organization-level-default-link-settings"></a><span data-ttu-id="23950-135">SharePoint 組織層級預設連結設定</span><span class="sxs-lookup"><span data-stu-id="23950-135">SharePoint organization level default link settings</span></span>

<span data-ttu-id="23950-136">預設檔案和資料夾連結設定會決定哪一個連結選項向使用者顯示預設情況下使用者共用的檔案或資料夾時。</span><span class="sxs-lookup"><span data-stu-id="23950-136">The default file and folder link settings determine which link option is shown to the user by default when they share a file or folder.</span></span> <span data-ttu-id="23950-137">使用者可以將連結類型變更為下列其中一個其他選項共用視之前。</span><span class="sxs-lookup"><span data-stu-id="23950-137">Users can change the link type to one of the other options before sharing if desired.</span></span>

<span data-ttu-id="23950-138">請記住，此設定會影響您的組織，以及 OneDrive 中的 SharePoint 網站。</span><span class="sxs-lookup"><span data-stu-id="23950-138">Keep in mind that this setting affects SharePoint sites in your organization, as well as OneDrive.</span></span>

<span data-ttu-id="23950-139">選擇 [當使用者共用檔案及資料夾，依預設會選取連結的類型：</span><span class="sxs-lookup"><span data-stu-id="23950-139">Choose the type of link that's selected by default when users share files and folders:</span></span>

- <span data-ttu-id="23950-140">**任何人] 連結**-如果您預期在具有匿名使用者共用檔案和資料夾的許多選擇此選項。</span><span class="sxs-lookup"><span data-stu-id="23950-140">**Anyone with the link** - Choose this option if you expect to share a lot of files and folders with anonymous users.</span></span> <span data-ttu-id="23950-141">如果您想要允許*任何人*的連結，但擔心意外匿名共用，請考慮下列其中一個其他選項為預設值。</span><span class="sxs-lookup"><span data-stu-id="23950-141">If you want to allow *Anyone* links but are concerned about accidental anonymous sharing, consider one of the other options as the default.</span></span> <span data-ttu-id="23950-142">如果您已啟用**的任何人**共用，此連結類型只有。</span><span class="sxs-lookup"><span data-stu-id="23950-142">This link type is only available if you've enabled **Anyone** sharing.</span></span>
- <span data-ttu-id="23950-143">**只有在您的組織中的人員**-如果您預期大部分的檔案和資料夾共用您的組織內的人員都必須選擇此選項。</span><span class="sxs-lookup"><span data-stu-id="23950-143">**Only people in your organization** - Choose this option if you expect most file and folder sharing to be with people inside your organization.</span></span>
- <span data-ttu-id="23950-144">**特定人員**-如果您預期執行許多檔案和資料夾與來賓共用，請考慮此選項。</span><span class="sxs-lookup"><span data-stu-id="23950-144">**Specific people** - Consider this option if you expect to do a lot of file and folder sharing with guests.</span></span> <span data-ttu-id="23950-145">這種類型的連結與來賓運作，以及需要進行驗證。</span><span class="sxs-lookup"><span data-stu-id="23950-145">This type of link works with guests and requires them to authenticate.</span></span>
 
![螢幕擷取畫面的 SharePoint 組織層級檔案和資料夾共用設定](media/sharepoint-organization-files-folders-sharing-settings.png)


<span data-ttu-id="23950-147">若要設定 SharePoint 和 OneDrive 組織層級預設值] 連結</span><span class="sxs-lookup"><span data-stu-id="23950-147">To set the SharePoint and OneDrive organization level default link settings</span></span>

1. <span data-ttu-id="23950-148">瀏覽至 SharePoint 系統管理中心的 [共用] 頁面上。</span><span class="sxs-lookup"><span data-stu-id="23950-148">Navigate to the Sharing page in the SharePoint admin center.</span></span>
2. <span data-ttu-id="23950-149">[**檔案] 和 [資料夾] 連結**，選取預設共用您想要使用的連結。</span><span class="sxs-lookup"><span data-stu-id="23950-149">Under **File and folder links**, select the default sharing link that you want to use.</span></span>
3. <span data-ttu-id="23950-150">如果您所做的變更，請按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="23950-150">If you made changes, click **Save**.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="23950-151">SharePoint 網站層級共用設定</span><span class="sxs-lookup"><span data-stu-id="23950-151">SharePoint site level sharing settings</span></span>

<span data-ttu-id="23950-152">如果您要共用檔案和 fodlers SharePoint 網站中，您也需要檢查該網站的網站層級共用設定。</span><span class="sxs-lookup"><span data-stu-id="23950-152">If you're sharing files and fodlers that are in a SharePoint site, you also need to check the site-level sharing settings for that site.</span></span>

![螢幕擷取畫面的 SharePoint 網站外部共用設定](media/sharepoint-site-external-sharing-settings.png)

<span data-ttu-id="23950-154">若要設定網站層級共用設定</span><span class="sxs-lookup"><span data-stu-id="23950-154">To set site-level sharing settings</span></span>
1. <span data-ttu-id="23950-155">在 SharePoint 系統管理中心中，在左側導覽中，展開 [**站台**，按一下 [**作用中網站**。</span><span class="sxs-lookup"><span data-stu-id="23950-155">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="23950-156">選取您剛建立的網站。</span><span class="sxs-lookup"><span data-stu-id="23950-156">Select the site that you just created.</span></span>
3. <span data-ttu-id="23950-157">在功能區中，按一下 [**共用**]。</span><span class="sxs-lookup"><span data-stu-id="23950-157">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="23950-158">請確定該共用設為**任何人**或**新增和現有的來賓**。</span><span class="sxs-lookup"><span data-stu-id="23950-158">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="23950-159">如果您所做的變更，請按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="23950-159">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="23950-160">邀請使用者</span><span class="sxs-lookup"><span data-stu-id="23950-160">Invite users</span></span>

<span data-ttu-id="23950-161">來賓共用設定現在會進行設定，讓使用者可以立即與共用檔案和資料夾來賓。</span><span class="sxs-lookup"><span data-stu-id="23950-161">Guest sharing settings are now configured, so users can now share files and folders with guests.</span></span> <span data-ttu-id="23950-162">如需詳細資訊，請參閱[共用 OneDrive 檔案及資料夾](https://support.office.com/article/9fcc2f7d-de0c-4cec-93b0-a82024800c07)和[共用 SharePoint 檔案或資料夾](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c)。</span><span class="sxs-lookup"><span data-stu-id="23950-162">See [Share OneDrive files and folders](https://support.office.com/article/9fcc2f7d-de0c-4cec-93b0-a82024800c07) and [Share SharePoint files or folders](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="23950-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23950-163">See Also</span></span>
