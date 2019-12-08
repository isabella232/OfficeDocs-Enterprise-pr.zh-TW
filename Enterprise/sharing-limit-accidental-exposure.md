---
title: 限制意外暴露
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Priority
description: 深入了解如何在與來賓共用檔案時，限制資訊意外暴露。
ms.openlocfilehash: 3a5a99e96207e407f15abb17d9e1903c8ba52339
ms.sourcegitcommit: 7e65640fb1a86858a95c9ef0edbb58d0f171c5ee
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/06/2019
ms.locfileid: "39886472"
---
# <a name="limit-accidental-exposure-to-files-when-sharing-with-guests"></a><span data-ttu-id="0ad1c-103">與來賓共用時限制意外暴露檔案</span><span class="sxs-lookup"><span data-stu-id="0ad1c-103">Limit accidental exposure to files when sharing with guests</span></span>

<span data-ttu-id="0ad1c-104">與來賓共用檔案和資料夾時，有許多選項可以降低意外共用機密資訊的機會。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-104">When sharing files and folders with guests, there are a variety of options to reduce the chances of accidentally sharing confidential information.</span></span> <span data-ttu-id="0ad1c-105">您可以從本文中選擇最符合貴組織需求的選項。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-105">You can choose from the options in this article to best meet the needs of your organization.</span></span>

## <a name="use-best-practices-for-anyone-links"></a><span data-ttu-id="0ad1c-106">使用適用於 [任何人] 連結的最佳做法</span><span class="sxs-lookup"><span data-stu-id="0ad1c-106">Use best practices for Anyone links</span></span>

<span data-ttu-id="0ad1c-107">如果組織的人員需要進行未驗證共用，但是您擔心未驗證的來賓修改內容，請參閱[未驗證共用的最佳做法](best-practices-anonymous-sharing.md)，以取得如何在組織中使用未驗證共用的指導方針。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-107">If people in your organization need to do anonymous sharing, but you're concerned about unauthenticated guests modifying content, read [Best practices for anonymous sharing](best-practices-anonymous-sharing.md) for guidance on how to work with anonymous sharing in your organization.</span></span>

## <a name="turn-off-anyone-links"></a><span data-ttu-id="0ad1c-108">關閉 [任何人] 連結</span><span class="sxs-lookup"><span data-stu-id="0ad1c-108">Turn off Anyone links</span></span>

<span data-ttu-id="0ad1c-109">我們建議針對適當的內容讓 [任何人]\*\* 連結啟用，因為這是最簡單的共用方式，而且可以協助減少使用者尋求您的 IT 部門掌握外其他解決方案的風險。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-109">We recommend leaving *Anyone* links enabled for appropriate content because it's the easiest way to share and can help reduce the risk of users seeking other solutions that are outside the control of your IT department.</span></span> <span data-ttu-id="0ad1c-110">[任何人]\*\* 連結可以轉寄給其他人，但是檔案存取權僅限擁有連結的人員使用。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-110">*Anyone* links can be forwarded to others, but file access is only available to those who have the link.</span></span>

<span data-ttu-id="0ad1c-111">如果您要來賓一律在存取 SharePoint、群組或 Teams 中的內容時經過驗證，您可以關閉 [任何人]\*\* 共用。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-111">If you always want guests to authenticate when accessing content in SharePoint, Groups, or Teams, you can turn off *Anyone* sharing.</span></span> <span data-ttu-id="0ad1c-112">這會防止使用者未經驗證而共用內容。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-112">This will prevent users from sharing content anonymously.</span></span>

<span data-ttu-id="0ad1c-113">如果您停用 [任何人]\*\* 連結，使用者仍然可以使用 [特定人員]\*\* 連結，輕易地與來賓共用。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-113">If you disable *Anyone* links, users can still easily share with guests using *Specific people* links.</span></span> <span data-ttu-id="0ad1c-114">在此情況下，所有來賓都必須先經過驗證，才能存取共用的內容。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-114">In this case, all guests will be required to authenticate before they can access the shared content.</span></span>

<span data-ttu-id="0ad1c-115">視您的需求而定，您可以針對特定網站或整個組織停用 [任何人]\*\* 連結。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-115">Depending on your needs, you can disable *Anyone* links for specific sites, or for your whole organization.</span></span>

<span data-ttu-id="0ad1c-116">若要關閉貴組織的 [任何人]\*\* 連結</span><span class="sxs-lookup"><span data-stu-id="0ad1c-116">To turn off *Anyone* links for your organization</span></span>
1. <span data-ttu-id="0ad1c-117">在 SharePoint 管理中心中，按一下左側導覽窗格中的 [共用]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-117">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
2. <span data-ttu-id="0ad1c-118">將 SharePoint 外部共用設定設為 [新的及現有來賓]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-118">Set the SharePoint external sharing settings to **New and existing guests**.</span></span></br>
   <span data-ttu-id="0ad1c-119">![SharePoint 網站外部共用設定的螢幕擷取畫面](media/sharepoint-organization-external-sharing-controls-new-users.png)</span><span class="sxs-lookup"><span data-stu-id="0ad1c-119">![Screenshot of SharePoint site external sharing settings](media/sharepoint-organization-external-sharing-controls-new-users.png)</span></span>
3. <span data-ttu-id="0ad1c-120">按一下 [儲存]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-120">Click **Save**.</span></span>

<span data-ttu-id="0ad1c-121">若要關閉網站的 [任何人]\*\* 連結</span><span class="sxs-lookup"><span data-stu-id="0ad1c-121">To turn off *Anyone* links for a site</span></span>
1. <span data-ttu-id="0ad1c-122">在 SharePoint 管理中心中，在左側導覽窗格中展開 [網站]\*\*\*\*，然後按一下 [使用中網站]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-122">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="0ad1c-123">為您剛建立的小組選取網站。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-123">Select the site for the team that you just created.</span></span>
3. <span data-ttu-id="0ad1c-124">在功能區中，按一下 [共用]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-124">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="0ad1c-125">請確認共用設為 [新的及現有來賓]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-125">Ensure that sharing is set to **New and existing guests**.</span></span></br>
   <span data-ttu-id="0ad1c-126">![SharePoint 網站外部共用設定的螢幕擷取畫面](media/sharepoint-site-external-sharing-settings.png)</span><span class="sxs-lookup"><span data-stu-id="0ad1c-126">![Screenshot of SharePoint site external sharing settings](media/sharepoint-site-external-sharing-settings.png)</span></span>
5. <span data-ttu-id="0ad1c-127">如果您做了任何變更，請按一下 [儲存]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-127">If you made changes, click **Save**.</span></span>

## <a name="domain-filtering"></a><span data-ttu-id="0ad1c-128">網域篩選</span><span class="sxs-lookup"><span data-stu-id="0ad1c-128">Domain filtering</span></span>

<span data-ttu-id="0ad1c-129">您可以使用網域允許或拒絕清單，來決定您的使用者可以從哪些網域邀請來賓。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-129">You can use domain allow or deny lists to determine which domains your users can invite guests from.</span></span>

<span data-ttu-id="0ad1c-130">使用允許清單，您可以指定網域清單，貴組織使用者可以從哪些網域邀請來賓。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-130">With an allow list, you can specify a list of domains from which users in your organization can invite guests.</span></span> <span data-ttu-id="0ad1c-131">其他網域的來賓邀請會遭到封鎖。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-131">Guest invitations to other domains are blocked.</span></span> <span data-ttu-id="0ad1c-132">如果貴組織只會與來自特定網域清單的來賓共同作業，您可以使用此功能來防止與其他網域共用。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-132">If your organization only collaborates with guests from a list of specific domains, you can use this feature to prevent sharing with other domains.</span></span>

<span data-ttu-id="0ad1c-133">使用拒絕清單，您可以指定網域清單，貴組織使用者無法從哪些網域邀請來賓。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-133">With a deny list, you can specify a list of domains from which users in your organization cannot invite guests.</span></span> <span data-ttu-id="0ad1c-134">列出網域的來賓邀請會遭到封鎖。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-134">Guest invitations to the listed domains are blocked.</span></span> <span data-ttu-id="0ad1c-135">如果您有競爭對手，例如您想要阻止成為貴組織來賓的人員，這個功能很有用。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-135">This can be useful if you have competitors, for example, who you want to prevent from becoming guests in your organization.</span></span>

<span data-ttu-id="0ad1c-136">允許和拒絕清單只會影響與已驗證來賓的共用。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-136">The allow and deny lists only affect sharing with authenticated guests.</span></span> <span data-ttu-id="0ad1c-137">如果您未停用 [任何人]\*\* 連結，使用者仍然可以使用這個連結，與來自禁止網域的來賓共用。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-137">Users can still share with guests from prohibited domains by using *Anyone* links if you haven't disabled them.</span></span> <span data-ttu-id="0ad1c-138">若要達到使用網域允許和拒絕清單的最佳結果，請考量停用 [任何人]\*\* 連結，如上所述。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-138">For best results with domain allow and deny lists, consider disabling *Anyone* links as described above.</span></span>

<span data-ttu-id="0ad1c-139">若要針對來賓共用設定網域允許或拒絕清單</span><span class="sxs-lookup"><span data-stu-id="0ad1c-139">To set up a domain allow or deny list for guest sharing</span></span>
1. <span data-ttu-id="0ad1c-140">在 SharePoint 管理中心中，按一下左側導覽窗格中的 [共用]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-140">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
2. <span data-ttu-id="0ad1c-141">在 [外部共用的進階設定]\*\*\*\* 底下，選取 [依網域限制外部共用]\*\*\*\* 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-141">Under **Advanced settings for external sharing**, select the **Limit external sharing by domain** check box.</span></span>
3. <span data-ttu-id="0ad1c-142">按一下 [新增網域]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-142">Click **Add domains**.</span></span>
4. <span data-ttu-id="0ad1c-143">選取您是否想要封鎖網域，輸入網域，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-143">Select whether you want to block domains, type the domains, and click **OK**.</span></span></br>
   <span data-ttu-id="0ad1c-144">![依網域的 SharePoint 限制外部共用設定的螢幕擷取畫面](media/sharepoint-sharing-block-domain.png)</span><span class="sxs-lookup"><span data-stu-id="0ad1c-144">![Screenshot of SharePoint limit external sharing by domain setting](media/sharepoint-sharing-block-domain.png)</span></span>
5. <span data-ttu-id="0ad1c-145">按一下 [儲存]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-145">Click **Save**.</span></span>

<span data-ttu-id="0ad1c-146">如果您想要依據比 SharePoint 和 OneDrive 還要高層級的網域限制共用，您可以在 Azure Active Directory 中[允許或封鎖對特定組織的 B2B 使用者的邀請](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list)。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-146">If you want to limit sharing by domain at a higher level than SharePoint and OneDrive, you can [allow or block invitations to B2B users from specific organizations](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list) in Azure Active Directory.</span></span> <span data-ttu-id="0ad1c-147">(您必須設定 [SharePoint 和 OneDrive 與 Azure AD B2B 整合 (預覽版)](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview)，讓這些設定影響 SharePoint 和 OneDrive。)</span><span class="sxs-lookup"><span data-stu-id="0ad1c-147">(You must configure the [SharePoint and OneDrive integration with Azure AD B2B Preview](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview) for these settings to affect SharePoint and OneDrive.)</span></span>

## <a name="limit-guest-sharing-of-files-folders-and-sites-to-specified-security-groups"></a><span data-ttu-id="0ad1c-148">將檔案、資料夾和網站的來賓共用限制為特定安全性群組</span><span class="sxs-lookup"><span data-stu-id="0ad1c-148">Limit guest sharing of files, folders, and sites to specified security groups</span></span>

<span data-ttu-id="0ad1c-149">您可以將檔案、資料夾和網站的來賓共用限制為特定安全性群組的成員。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-149">You can restrict guest sharing of files, folders, and sites to members of a specific security group.</span></span> <span data-ttu-id="0ad1c-150">如果您想要啟用來賓共用，但是有核准工作流程或要求程序，這個選項相當有用。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-150">This is useful if you want to enable guest sharing, but with an approval workflow or request process.</span></span>

<span data-ttu-id="0ad1c-151">若要將來賓共用限制為安全性群組的成員</span><span class="sxs-lookup"><span data-stu-id="0ad1c-151">To limit guest sharing to members of a security group</span></span>
1. <span data-ttu-id="0ad1c-152">在 SharePoint 管理中心中，按一下左側導覽窗格中的 [共用]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-152">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
2. <span data-ttu-id="0ad1c-153">在 [其他設定]\*\*\*\* 底下，</span><span class="sxs-lookup"><span data-stu-id="0ad1c-153">Under **Other settings**.</span></span> <span data-ttu-id="0ad1c-154">遵循 [將外部共用限制為特定安全性群組]\*\*\*\* 連結。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-154">follow the **Limit external sharing to specific security groups** link.</span></span>
3. <span data-ttu-id="0ad1c-155">在 [誰可以與組織外進行共用]\*\*\*\* 底下，選取其中一個核取方塊，或同時選取：a.</span><span class="sxs-lookup"><span data-stu-id="0ad1c-155">Under **Who can share outside your organization**, select one or both of the check boxes: a.</span></span> <span data-ttu-id="0ad1c-156">[只讓所選安全性群組中的使用者與已驗證的外部使用者共用]\*\*\*\*，指定可以與已驗證使用者共用的安全性群組 b.</span><span class="sxs-lookup"><span data-stu-id="0ad1c-156">**Let only users in selected security groups share with authenticated external users** to specify a security group that can share with authenticated users b.</span></span> <span data-ttu-id="0ad1c-157">[只有所選安全性群組中的使用者可以與已驗證之外部使用者和使用匿名連結的使用者進行共用]\*\*\*\*，指定可以與已驗證使用者共用和使用 [任何人] 連結的安全性群組</span><span class="sxs-lookup"><span data-stu-id="0ad1c-157">**Let only users in selected security groups share with authenticated external users and using anonymous links** to specify a security group that can share with authenticated users and by using Anyone links</span></span>
4. <span data-ttu-id="0ad1c-158">按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-158">Click **OK**.</span></span>

<span data-ttu-id="0ad1c-159">請注意，這會影響檔案、資料夾和網站，但是不會影響 Office 365 群組或 Teams。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-159">Note that this affects files, folders, and sites, but not Office 365 groups or Teams.</span></span> <span data-ttu-id="0ad1c-160">當成員邀請來賓加入私人 Office 365 群組或 Microsoft Teams 中的私人小組時，邀請會傳送給群組或小組擁有者進行核准。</span><span class="sxs-lookup"><span data-stu-id="0ad1c-160">When members invite guests to a private Office 365 group or a private team in Microsoft Teams, the invitation is sent to the group or team owner for approval.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ad1c-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ad1c-161">See Also</span></span>

[<span data-ttu-id="0ad1c-162">建立安全的來賓共用環境</span><span class="sxs-lookup"><span data-stu-id="0ad1c-162">Create a secure guest sharing environment</span></span>](create-a-secure-guest-sharing-environment.md)

[<span data-ttu-id="0ad1c-163">與匿名使用者共用檔案和資料夾的最佳做法</span><span class="sxs-lookup"><span data-stu-id="0ad1c-163">Best practices for sharing files and folders with anonymous users</span></span>](best-practices-anonymous-sharing.md)