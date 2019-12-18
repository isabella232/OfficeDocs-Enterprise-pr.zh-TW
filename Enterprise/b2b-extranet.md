---
title: 使用受管理的來賓建立 B2B 外部網路
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: 了解如何建立 B2B 外部網路網站或小組，並提出從夥伴組織的受管理的來賓使用者。
ms.openlocfilehash: b314949e97789141bc510554da40409e8bf3b6df
ms.sourcegitcommit: f18f75dba4cbec557fa094bd1cebd8c5cc4752c1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2019
ms.locfileid: "40085416"
---
# <a name="create-a-b2b-extranet-with-managed-guests"></a><span data-ttu-id="cf83c-103">使用受管理的來賓建立 B2B 外部網路</span><span class="sxs-lookup"><span data-stu-id="cf83c-103">Create a B2B extranet with managed guests</span></span>

<span data-ttu-id="cf83c-104">若要建立外部網路 B2B 共同作業與夥伴組織使用 Azure Active Directory，您可以使用[Azure Active Directory 權益 Management](https://docs.microsoft.com/azure/active-directory/governance/entitlement-management-overview) 。</span><span class="sxs-lookup"><span data-stu-id="cf83c-104">You can use [Azure Active Directory Entitlement Management](https://docs.microsoft.com/azure/active-directory/governance/entitlement-management-overview) to create a B2B extranet to collaborate with a partner organization that uses Azure Active Directory.</span></span> <span data-ttu-id="cf83c-105">這可讓使用者自行註冊在外部網路網站或小組及接收存取方式核准工作流程。</span><span class="sxs-lookup"><span data-stu-id="cf83c-105">This allows users to self-enroll in the extranet site or team and receive access via an approval workflow.</span></span>

<span data-ttu-id="cf83c-106">使用此方法的共用資源進行共同作業時，是指夥伴組織可協助維護及核准來賓使用者在其結束時，降低您的 IT 部門的負擔，並且讓這些最熟悉管理使用者共同作業協議存取。</span><span class="sxs-lookup"><span data-stu-id="cf83c-106">With this method of sharing resources for collaboration, the partner organization can help maintain and approve the guest users on their end, reducing the burden on your IT department and allowing those most familiar with the collaboration agreement to manage user access.</span></span>

<span data-ttu-id="cf83c-107">本文會逐步完成步驟來建立套件 （在此情況下、 網站或小組） 您可以透過自助服務存取註冊模型夥伴組織與共用的資源。</span><span class="sxs-lookup"><span data-stu-id="cf83c-107">This article walks through the steps to create a package of resources (in this case, a site or team) that you can share with a partner organization through a self-service access registration model.</span></span> 

<span data-ttu-id="cf83c-108">開始之前，請建立網站或小組，您想要與夥伴組織共用，並啟用的來賓共用。</span><span class="sxs-lookup"><span data-stu-id="cf83c-108">Before you begin, create the site or team that you want to share with the partner organization and enable it for guest sharing.</span></span> <span data-ttu-id="cf83c-109">如需詳細資訊，請參閱[共同作業與網站中的來賓](collaborate-in-a-site.md)或[小組中的來賓與共同作業](collaborate-as-a-team.md)。</span><span class="sxs-lookup"><span data-stu-id="cf83c-109">See [Collaborate with guests in a site](collaborate-in-a-site.md) or [Collaborate with guests in a team](collaborate-as-a-team.md) for more information.</span></span> <span data-ttu-id="cf83c-110">我們也建議您檢閱[建立安全的來賓共用環境](create-a-secure-guest-sharing-environment.md)的安全性與合規性功能，您可用於協助維護與來賓控管原則時進行共同作業的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="cf83c-110">We also recommend that you review [Create a secure guest sharing environment](create-a-secure-guest-sharing-environment.md) for information about security and compliance features that you can use to help maintain your governance policies when collaborating with guests.</span></span>

## <a name="connect-the-partner-organization"></a><span data-ttu-id="cf83c-111">連線到夥伴組織</span><span class="sxs-lookup"><span data-stu-id="cf83c-111">Connect the partner organization</span></span>

<span data-ttu-id="cf83c-112">若要邀請來賓從夥伴組織，您必須新增為連結的組織在 Azure Active Directory 中的協力廠商的網域。</span><span class="sxs-lookup"><span data-stu-id="cf83c-112">In order to invite guests from a partner organization, you need to add the the partner's domain as a connected organization in Azure Active Directory.</span></span>

<span data-ttu-id="cf83c-113">若要新增的已連線的組織</span><span class="sxs-lookup"><span data-stu-id="cf83c-113">To add a connected organization</span></span>
1. <span data-ttu-id="cf83c-114">在[Azure Active Directory](https://aad.portal.azure.com)中，按一下 [**身分識別管理**]。</span><span class="sxs-lookup"><span data-stu-id="cf83c-114">In [Azure Active Directory](https://aad.portal.azure.com), click **Identity Governance**.</span></span>
2. <span data-ttu-id="cf83c-115">按一下 [**連線的組織**。</span><span class="sxs-lookup"><span data-stu-id="cf83c-115">Click **Connected organizations**.</span></span>
4. <span data-ttu-id="cf83c-116">按一下 [**新增連線組織**。</span><span class="sxs-lookup"><span data-stu-id="cf83c-116">Click **Add connected organization**.</span></span>
5. <span data-ttu-id="cf83c-117">輸入的名稱和描述組織，然後再按一下**下一步： 目錄 + 網域**。</span><span class="sxs-lookup"><span data-stu-id="cf83c-117">Type a name and description for the organization, and then click **Next: Directory + domain**.</span></span>
6. <span data-ttu-id="cf83c-118">按一下 [**新增目錄 + 網域**]。</span><span class="sxs-lookup"><span data-stu-id="cf83c-118">Click **Add directory + domain**.</span></span>
7. <span data-ttu-id="cf83c-119">輸入您想要連線，請在組織的網域，然後按一下 [**新增]**。</span><span class="sxs-lookup"><span data-stu-id="cf83c-119">Type the domain for the organization that you want to connect, and then click **Add**.</span></span>
8. <span data-ttu-id="cf83c-120">按一下 [**連線**]，然後按一下 [**下一步： 贊助者**。</span><span class="sxs-lookup"><span data-stu-id="cf83c-120">Click **Connect**, and then click **Next: Sponsors**.</span></span>
9. <span data-ttu-id="cf83c-121">從您的組織或您要連接至您想要核准來賓使用者的存取權的使用者的組織新增人員。</span><span class="sxs-lookup"><span data-stu-id="cf83c-121">Add people from your organization or the organization that you're connecting to who you want to approve access for guest users.</span></span>
10. <span data-ttu-id="cf83c-122">按一下 [**下一步： 檢閱 + 建立**。</span><span class="sxs-lookup"><span data-stu-id="cf83c-122">Click **Next: Review + Create**.</span></span>
11. <span data-ttu-id="cf83c-123">檢閱您選擇，然後按一下 [**建立**的設定。</span><span class="sxs-lookup"><span data-stu-id="cf83c-123">Review the settings that you've chosen and then click **Create**.</span></span>

    ![Azure Active Directory 中的 [連線的組織] 頁面的螢幕擷取畫面](media/identity-governance-connected-organizations.png)

## <a name="choose-the-resources-to-share"></a><span data-ttu-id="cf83c-125">選擇要共用的資源</span><span class="sxs-lookup"><span data-stu-id="cf83c-125">Choose the resources to share</span></span>

<span data-ttu-id="cf83c-126">選取要與夥伴組織的共用資源的第一個步驟是建立來包含這些目錄。</span><span class="sxs-lookup"><span data-stu-id="cf83c-126">The first step in selecting resources to share with a partner organization is to create a catalog to contain them.</span></span>

<span data-ttu-id="cf83c-127">若要建立目錄</span><span class="sxs-lookup"><span data-stu-id="cf83c-127">To create a catalog</span></span>
1. <span data-ttu-id="cf83c-128">在[Azure Active Directory](https://aad.portal.azure.com)中，按一下 [**身分識別管理**]。</span><span class="sxs-lookup"><span data-stu-id="cf83c-128">In [Azure Active Directory](https://aad.portal.azure.com), click **Identity Governance**.</span></span>
2. <span data-ttu-id="cf83c-129">按一下 [**目錄**]。</span><span class="sxs-lookup"><span data-stu-id="cf83c-129">Click **Catalogs**.</span></span>
3. <span data-ttu-id="cf83c-130">按一下 [**新增目錄**]。</span><span class="sxs-lookup"><span data-stu-id="cf83c-130">Click **New catalog**.</span></span>
4. <span data-ttu-id="cf83c-131">輸入的名稱和描述目錄的應用程式，並確定， **Enabled**並**已啟用的外部使用者**都設定為 **[是]**。</span><span class="sxs-lookup"><span data-stu-id="cf83c-131">Type a name and description for the catalog and ensure that **Enabled** and **Enabled for external users** are both set to **Yes**.</span></span>
5. <span data-ttu-id="cf83c-132">按一下 **[建立]**。</span><span class="sxs-lookup"><span data-stu-id="cf83c-132">Click **Create**.</span></span>

   ![在 [Azure Active Directory 身分識別管理 [目錄] 頁面的螢幕擷取畫面](media/identity-governance-catalogs.png)

<span data-ttu-id="cf83c-134">一旦建立目錄的應用程式之後，您可以新增 SharePoint 網站或小組，您想要與夥伴組織共用。</span><span class="sxs-lookup"><span data-stu-id="cf83c-134">Once the catalog has been created, you add the SharePoint site or team that you want to share with the partner organization.</span></span>

<span data-ttu-id="cf83c-135">若要將資源新增至目錄</span><span class="sxs-lookup"><span data-stu-id="cf83c-135">To add resources to a catalog</span></span>
1. <span data-ttu-id="cf83c-136">在 Azure AD Identity 控管，按一下 [**目錄**]，，然後按一下您要將資源新增型的錄。</span><span class="sxs-lookup"><span data-stu-id="cf83c-136">In Azure AD Identity Governance, click **Catalogs**, and then click the catalog where you want to add resources.</span></span>
2. <span data-ttu-id="cf83c-137">按一下 [**資源**]，然後按一下 [**新增資源**。</span><span class="sxs-lookup"><span data-stu-id="cf83c-137">Click **Resources** and then click **Add resources**.</span></span>
3. <span data-ttu-id="cf83c-138">選取的小組或您想要包含在您網路中的 SharePoint 網站，然後按一下 [**新增]**。</span><span class="sxs-lookup"><span data-stu-id="cf83c-138">Select the teams or SharePoint sites that you want to include in your extranet, and then click **Add**.</span></span>

   ![Azure Active Directory 身分識別管理目錄資源] 頁面的螢幕擷取畫面](media/identity-governance-catalog-resource.png)

<span data-ttu-id="cf83c-140">一旦您已經定義您想要共用的資源下, 一步是建立 access 封裝，它所定義的授與協力廠商使用者存取類型和新的合作夥伴使用者要求存取權的核准程序。</span><span class="sxs-lookup"><span data-stu-id="cf83c-140">Once you've defined the resources that you want to share, the next step is to create an access package, which defines the type of access that partner users are granted and the approval process for new partner users requesting access.</span></span>

<span data-ttu-id="cf83c-141">若要建立 access 封裝</span><span class="sxs-lookup"><span data-stu-id="cf83c-141">To create an access package</span></span>
1. <span data-ttu-id="cf83c-142">在 Azure AD Identity 控管，按一下 [**目錄**，，然後按一下 [您要建立 access 封裝的目錄。</span><span class="sxs-lookup"><span data-stu-id="cf83c-142">In Azure AD Identity Governance, click **Catalogs**, and then click the catalog where you want to create an access package.</span></span>
2. <span data-ttu-id="cf83c-143">按一下 [ **Access 套件**]，然後按一下 [**新的 access 封裝**。</span><span class="sxs-lookup"><span data-stu-id="cf83c-143">Click **Access packages**, and then click **New access package**.</span></span>
3. <span data-ttu-id="cf83c-144">輸入的名稱和描述 access 封裝，然後再按一下**下一步： 資源角色**。</span><span class="sxs-lookup"><span data-stu-id="cf83c-144">Type a name and description for the access package, and then click **Next: Resource roles**.</span></span>
4. <span data-ttu-id="cf83c-145">選擇您想要用於您網路的目錄資源。</span><span class="sxs-lookup"><span data-stu-id="cf83c-145">Choose the resources from the catalog that you want to use for your extranet.</span></span>
5. <span data-ttu-id="cf83c-146">針對每個資源，在 [**角色**] 欄中，選擇您想要授與使用外部網路的來賓使用者的使用者角色。</span><span class="sxs-lookup"><span data-stu-id="cf83c-146">For each resource, in the **Role** column, choose the user role you want to grant to the guest users who use the extranet.</span></span>
6. <span data-ttu-id="cf83c-147">按一下 [**下一步： 要求**。</span><span class="sxs-lookup"><span data-stu-id="cf83c-147">Click **Next: Requests**.</span></span>
7. <span data-ttu-id="cf83c-148">在 [**可以要求存取的使用者**，選擇 [**不在您的目錄中的使用者**。</span><span class="sxs-lookup"><span data-stu-id="cf83c-148">Under **Users who can request access**, choose **For users not in your directory**.</span></span>
8. <span data-ttu-id="cf83c-149">確定**特定的連接的組織**選項已選取，然後按一下 [**新增目錄**。</span><span class="sxs-lookup"><span data-stu-id="cf83c-149">Ensure that the **Specific connected organizations** option is selected, and then click **Add directories**.</span></span>
9. <span data-ttu-id="cf83c-150">選擇您稍早，新增連接的組織，然後按一下 [**選取**</span><span class="sxs-lookup"><span data-stu-id="cf83c-150">Choose the connected organization that you add earlier, and then click **Select**</span></span>
10. <span data-ttu-id="cf83c-151">在 [**核准**] 下選擇 [針對**需要核准**的 [**是**]。</span><span class="sxs-lookup"><span data-stu-id="cf83c-151">Under **Approval**, choose **Yes** for **Require approval**.</span></span>
11. <span data-ttu-id="cf83c-152">在 [**第一位核准者**，選擇下列其中一個之前加入贊助者或選擇特定的使用者。</span><span class="sxs-lookup"><span data-stu-id="cf83c-152">Under **First approver**, choose one of the sponsors that you added earlier or choose a specific user.</span></span>
12. <span data-ttu-id="cf83c-153">按一下 [**新增後援**，然後選取 [後援核准者。</span><span class="sxs-lookup"><span data-stu-id="cf83c-153">Click **Add fallback** and select a fallback approver.</span></span>
13. <span data-ttu-id="cf83c-154">[**啟用**，請選擇 [**是**]。</span><span class="sxs-lookup"><span data-stu-id="cf83c-154">Under **Enable**, choose **Yes**.</span></span>
14. <span data-ttu-id="cf83c-155">按一下 [**下一步： 生命週期**。</span><span class="sxs-lookup"><span data-stu-id="cf83c-155">Click **Next: Lifecycle**.</span></span>
15. <span data-ttu-id="cf83c-156">選擇 [到期日及存取檢閱 [設定您想要使用，然後按一下 [**下一步： 檢閱 + 建立**。</span><span class="sxs-lookup"><span data-stu-id="cf83c-156">Choose the expiration and access review settings that you want to use, and then click **Next: Review + Create**.</span></span>
16. <span data-ttu-id="cf83c-157">檢閱設定，然後再按一下 [**建立**。</span><span class="sxs-lookup"><span data-stu-id="cf83c-157">Review your settings, and then click **Create**.</span></span>

    ![在 Azure Active Directory 身分識別管理的存取套件畫面的螢幕擷取畫面](media/identity-governance-access-packages.png)

<span data-ttu-id="cf83c-159">如果您正在與大型組織合作，您可能想要隱藏存取套件。</span><span class="sxs-lookup"><span data-stu-id="cf83c-159">If you're partnering with a large organization, you may want to hide the access package.</span></span> <span data-ttu-id="cf83c-160">如果已隱藏封裝，然後夥伴組織中的使用者不會看到封裝其 *「 我的存取*入口網站上。</span><span class="sxs-lookup"><span data-stu-id="cf83c-160">If the package is hidden, then users in the partner organization will not see the package on their *My Access* portal.</span></span> <span data-ttu-id="cf83c-161">相反地，他們必須傳送註冊套件的直接連結。</span><span class="sxs-lookup"><span data-stu-id="cf83c-161">Instead, they must be sent a direct link to sign up for the package.</span></span> <span data-ttu-id="cf83c-162">隱藏存取套件可以降低不適當的存取要求的數目，也可協助保護組織的夥伴組織的入口網站中的可用的存取套件。</span><span class="sxs-lookup"><span data-stu-id="cf83c-162">Hiding the access package can reduce the number of inappropriate access requests and can also help keep available access packages organized in the partner organization's portal.</span></span>

<span data-ttu-id="cf83c-163">若要將存取套件屬性設定為隱藏</span><span class="sxs-lookup"><span data-stu-id="cf83c-163">To set an access package to hidden</span></span>
1. <span data-ttu-id="cf83c-164">在 Azure AD Identity 控管，按一下 [ **Access 套件**]，然後按一下您存取的套件。</span><span class="sxs-lookup"><span data-stu-id="cf83c-164">In Azure AD Identity Governance, click **Access packages**, and then click your access package.</span></span>
2. <span data-ttu-id="cf83c-165">在 [**概觀**] 頁面上，按一下 [**編輯**]。</span><span class="sxs-lookup"><span data-stu-id="cf83c-165">On the **Overview** page, click **Edit**.</span></span>
3. <span data-ttu-id="cf83c-166">在 [**屬性**] 下的**隱藏**，選擇 [**是]** ，然後按一下 [**儲存**。</span><span class="sxs-lookup"><span data-stu-id="cf83c-166">Under **Properties**, choose **Yes** for **Hidden**, and then click **Save**.</span></span>

   ![編輯存取套件內容] 畫面的螢幕擷取畫面](media/identity-governance-access-package-hidden.png)

## <a name="invite-partner-users"></a><span data-ttu-id="cf83c-168">邀請合作夥伴使用者</span><span class="sxs-lookup"><span data-stu-id="cf83c-168">Invite partner users</span></span>

<span data-ttu-id="cf83c-169">如果您將 access 封裝為隱藏，您需要的直接連結傳送到夥伴組織，以便他們可以要求存取網站或小組。</span><span class="sxs-lookup"><span data-stu-id="cf83c-169">If you set the access package to hidden, you need to send a direct link to the partner organization so that they can request access to your site or team.</span></span>

<span data-ttu-id="cf83c-170">若要尋找存取入口網站連結</span><span class="sxs-lookup"><span data-stu-id="cf83c-170">To find the access portal link</span></span>
1. <span data-ttu-id="cf83c-171">在 Azure AD Identity 控管，按一下 [ **Access 套件**]，然後按一下您存取的套件。</span><span class="sxs-lookup"><span data-stu-id="cf83c-171">In Azure AD Identity Governance, click **Access packages**, and then click your access package.</span></span>
2. <span data-ttu-id="cf83c-172">在 [**概觀**] 頁面上，按一下**複製到剪貼簿**連結**我存取入口網站連結**。</span><span class="sxs-lookup"><span data-stu-id="cf83c-172">On the **Overview** page, click **Copy to clipboard** link for the **My Access portal link**.</span></span>

   ![使用存取入口網站連結即可存取套件屬性的螢幕擷取畫面](media/identity-governance-access-portal-link.png)

<span data-ttu-id="cf83c-174">一旦您已複製連結，您可以將它共用與您的夥伴組織的連絡人，他們可以將它傳送給上共同作業小組的使用者。</span><span class="sxs-lookup"><span data-stu-id="cf83c-174">Once you have copied the link, you can share it with your contact at the partner organization and they can send it to the users on their collaboration team.</span></span>

## <a name="see-also"></a><span data-ttu-id="cf83c-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf83c-175">See Also</span></span>

[<span data-ttu-id="cf83c-176">建立安全的來賓共用環境</span><span class="sxs-lookup"><span data-stu-id="cf83c-176">Create a secure guest sharing environment</span></span>](create-a-secure-guest-sharing-environment.md)

