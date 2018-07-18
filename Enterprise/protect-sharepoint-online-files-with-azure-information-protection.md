---
title: 使用 Azure 資訊保護來保護 SharePoint Online 檔案
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: 摘要：套用 Azure 資訊保護來保護高度機密 SharePoint Online 小組網站中的檔案。
ms.openlocfilehash: 2c4776f5795a5a0b07be0f04b4872abadb4d31ca
ms.sourcegitcommit: b39b8ae3b4268d6475b54e2fdb62982b2c7d9943
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2018
ms.locfileid: "20319284"
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a><span data-ttu-id="c5ea0-103">使用 Azure 資訊保護來保護 SharePoint Online 檔案</span><span class="sxs-lookup"><span data-stu-id="c5ea0-103">Protect SharePoint Online files with Azure Information Protection</span></span>

 <span data-ttu-id="c5ea0-104">**摘要：** 套用 Azure 資訊保護來保護高度機密 SharePoint Online 小組網站中的檔案。</span><span class="sxs-lookup"><span data-stu-id="c5ea0-104">**Summary:** Apply Azure Information Protection to protect files in a highly confidential SharePoint Online team site.</span></span>
  
<span data-ttu-id="c5ea0-p101">使用本文中的步驟來設定 Azure 資訊保護，為檔案提供加密和權限。這些檔案可新增至針對高度機密保護所設定的 SharePoint 文件庫。或者，您可以直接從網站開啟檔案，並使用 Azure 資訊保護用戶端來新增加密。此加密和權限保護會與檔案一起移動，即使是從網站下載檔案也一樣。</span><span class="sxs-lookup"><span data-stu-id="c5ea0-p101">Use the steps in this article to configure Azure Information Protection to provide encryption and permissions for files. These files can be added to a SharePoint library configured for highly confidential protection. Or, you can open a file directly from the site and use the Azure Information Protection client to add encryption. The encryption and permissions protection travels with a file even when it is downloaded from the site.</span></span> 

<span data-ttu-id="c5ea0-p102">這些步驟是屬於較大的解決方案，用於設定 SharePoint 網站和這些網站中檔案的高度機密保護。如需詳細資訊，請參閱[保護 SharePoint Online 網站與檔案](secure-sharepoint-online-sites-and-files.md)。</span><span class="sxs-lookup"><span data-stu-id="c5ea0-p102">These steps are part of a larger solution for configuring highly confidential protection for SharePoint sites and the files within these sites. For more information, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span> 

<span data-ttu-id="c5ea0-111">不建議針對所有的客戶在 SharePoint Online 中的檔案使用 Azure 資訊保護，但可供需要此檔案子集合保護層級的客戶選擇使用。</span><span class="sxs-lookup"><span data-stu-id="c5ea0-111">Using Azure Information Protection for files in SharePoint Online is not recommended for all customers, but is an option for customers who need this level of protection for a subset of files.</span></span>

<span data-ttu-id="c5ea0-112">這套解決方案的一些相關重要注意事項：</span><span class="sxs-lookup"><span data-stu-id="c5ea0-112">Some important notes about this solution:</span></span>
- <span data-ttu-id="c5ea0-p103">將 Azure 資訊保護加密套用至儲存於 Office 365 中的檔案時，服務會無法處理這些檔案的內容。 共同撰寫、eDiscovery、搜尋、Delve 和其他共同作業功能無法運作。 此外，資料外洩防護 (DLP) 原則只可用於中繼資料 (包括 Office 365 標籤)，但無法用於這些檔案的內容 (例如檔案中的信用卡號碼)。</span><span class="sxs-lookup"><span data-stu-id="c5ea0-p103">When Azure Information Protection encryption is applied to files stored in Office 365, the service cannot process the contents of these files. Co-authoring, eDiscovery, search, Delve, and other collaborative features do not work. Data Loss Prevention (DLP) policies can only work with the metadata (including Office 365 labels) but not the contents of these files (such as credit card numbers within files).</span></span>
- <span data-ttu-id="c5ea0-p104">此解決方案需要使用者選取標籤，適用 Azure 資訊保護所提供的保護。如果您需要自動加密，以及 SharePoint 編製索引並檢查檔案的功能，請考慮使用 SharePoint Online 中的資訊版權管理 (IRM)。當您設定 IRM 的 SharePoint 文件庫時，下載檔案以進行編輯時，會自動進行加密。SharePoint IRM 包含可能會影響決策的限制。如需詳細資訊，請參閱[在 SharePoint 系統管理中心中設定資訊版權管理 (IRM)](https://support.office.com/zh-TW/article/Set-up-Information-Rights-Management-IRM-in-SharePoint-admin-center-239CE6EB-4E81-42DB-BF86-A01362FED65C)。</span><span class="sxs-lookup"><span data-stu-id="c5ea0-p104">This solution requires a user to select a label that applies the protection from Azure Information Protection. If you require automatic encryption and the ability for SharePoint to index and inspect the files, consider using Information Rights Management (IRM) in SharePoint Online. When you configure a SharePoint library for IRM, files are automatically encrypted when they are downloaded for editing.  SharePoint IRM includes limitations that might influence your decision. For more information, see [Set up Information Rights Management (IRM) in SharePoint admin center](https://support.office.com/zh-TW/article/Set-up-Information-Rights-Management-IRM-in-SharePoint-admin-center-239CE6EB-4E81-42DB-BF86-A01362FED65C).</span></span>

##<a name="admin-setup"></a><span data-ttu-id="c5ea0-121">系統管理員設定</span><span class="sxs-lookup"><span data-stu-id="c5ea0-121">Admin setup</span></span>
<span data-ttu-id="c5ea0-122">首先，針對您的 Office 365 訂閱，使用[如何從 Office 365 系統管理中心啟用 Azure Rights Management](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) 中的指示。</span><span class="sxs-lookup"><span data-stu-id="c5ea0-122">First, use the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) for your Office 365 subscription.</span></span>
  
<span data-ttu-id="c5ea0-123">接著，為 Azure 資訊保護設定新的限域原則和子標籤，為高度機密 SharePoint Online 小組網站提供保護與權限。</span><span class="sxs-lookup"><span data-stu-id="c5ea0-123">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions of your highly confidential SharePoint Online team site.</span></span>
  
1. <span data-ttu-id="c5ea0-p105">使用具有安全性系統管理員或公司系統管理員角色的帳戶登入 Office 365 入口網站。 如需說明，請參閱[在何處登入 Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="c5ea0-p105">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="c5ea0-126">在您瀏覽器的個別索引標籤中，移至 Azure 入口網站 ([https://portal.azure.com](https://portal.azure.com))。</span><span class="sxs-lookup"><span data-stu-id="c5ea0-126">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="c5ea0-127">如果這是您第一次設定 Azure 資訊保護，請參閱這些[指示](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time)。</span><span class="sxs-lookup"><span data-stu-id="c5ea0-127">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="c5ea0-128">在清單窗格中，按一下 [所有服務]****，輸入**資訊**，然後按一下 [Azure 資訊保護]****。</span><span class="sxs-lookup"><span data-stu-id="c5ea0-128">In the list pane, click **All services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="c5ea0-129">在 [Azure 資訊保護]**** 刀鋒視窗中，按一下 [限域原則] > [+ 新增原則]****。</span><span class="sxs-lookup"><span data-stu-id="c5ea0-129">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="c5ea0-130">在 [原則名稱]**** 中輸入新原則的名稱，並在 [描述]**** 中輸入描述。</span><span class="sxs-lookup"><span data-stu-id="c5ea0-130">Type a name for the new policy in **Policy name** and a description in **Description**.</span></span>
    
7. <span data-ttu-id="c5ea0-131">按一下 [選取取得此原則的使用者或群組] > [使用者/群組]****，然後選取極機密 SharePoint Online 小組網站的網站成員存取群組。</span><span class="sxs-lookup"><span data-stu-id="c5ea0-131">Click **Select which users or groups get this policy > User/Groups**, and then select the site members access group for your highly sensitive SharePoint Online team site.</span></span> 
    
8. <span data-ttu-id="c5ea0-132">按一下 [選取] > [確定]****。</span><span class="sxs-lookup"><span data-stu-id="c5ea0-132">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="c5ea0-133">針對 [高度機密]**** 標籤，按一下省略符號 (...)，然後再按一下 [新增子標籤]****。</span><span class="sxs-lookup"><span data-stu-id="c5ea0-133">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="c5ea0-134">在 [名稱]**** 中鍵入子標籤的名稱，並在 [描述]**** 中鍵入標籤的描述。</span><span class="sxs-lookup"><span data-stu-id="c5ea0-134">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="c5ea0-135">在 [為包含此標籤的文件與電子郵件設定權限]**** 中，按一下 [保護]****。</span><span class="sxs-lookup"><span data-stu-id="c5ea0-135">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="c5ea0-136">在 [保護]**** 區段中，按一下 [Azure (雲端金鑰)]****。</span><span class="sxs-lookup"><span data-stu-id="c5ea0-136">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="c5ea0-137">在 [保護]**** 刀鋒視窗中，按一下 [保護設定]**** 下的 [+ 新增權限]****。</span><span class="sxs-lookup"><span data-stu-id="c5ea0-137">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="c5ea0-138">在 [新增權限]**** 刀鋒視窗中，按一下 [指定使用者與群組]**** 下的 [+ 瀏覽目錄]****。</span><span class="sxs-lookup"><span data-stu-id="c5ea0-138">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="c5ea0-139">在 [AAD 使用者與群組]**** 窗格中，選取您高度機密 SharePoint Online 小組網站的網站成員存取群組，然後按一下 [選取]****。</span><span class="sxs-lookup"><span data-stu-id="c5ea0-139">On the **AAD Users and Groups** pane, select the site members access group for your highly sensitive SharePoint Online team site, and then click **Select**.</span></span>
    
16. <span data-ttu-id="c5ea0-140">在 [從預設選擇權限]**** 下，清除 [列印]****、[複製並擷取內容]**** 和 [轉寄]**** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="c5ea0-140">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="c5ea0-141">按兩次 [確定]****。</span><span class="sxs-lookup"><span data-stu-id="c5ea0-141">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="c5ea0-142">在 [子標籤]**** 刀鋒視窗中，按一下 [儲存]****。</span><span class="sxs-lookup"><span data-stu-id="c5ea0-142">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="c5ea0-143">關閉新的限域原則刀鋒視窗。</span><span class="sxs-lookup"><span data-stu-id="c5ea0-143">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="c5ea0-144">在 [Azure 資訊保護 – 限域原則]**** 刀鋒視窗中，按一下 [發佈]****。</span><span class="sxs-lookup"><span data-stu-id="c5ea0-144">On the **Azure Information protection - Scoped policies** blade, click **Publish**.</span></span>
    
 
##<a name="client-setup"></a><span data-ttu-id="c5ea0-145">用戶端設定</span><span class="sxs-lookup"><span data-stu-id="c5ea0-145">Client setup</span></span>
<span data-ttu-id="c5ea0-146">現在您已可開始建立文件，並利用 Azure 資訊保護和新標籤進行保護。</span><span class="sxs-lookup"><span data-stu-id="c5ea0-146">You are now ready to begin creating documents and protecting them with Azure Information Protection and your new label.</span></span>
  
<span data-ttu-id="c5ea0-p106">您必須在自己的裝置或以 Windows 為基礎的電腦上[安裝 Azure 資訊保護用戶端](https://docs.microsoft.com/information-protection/rms-client/install-client-app)。您可以編寫指令碼並自動化安裝，使用者也可以手動安裝用戶端。請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="c5ea0-p106">You must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on your device or Windows-based computer. You can script and automate the installation, or users can install the client manually. See the following resources:</span></span>
  
- [<span data-ttu-id="c5ea0-150">Azure 資訊保護的用戶端</span><span class="sxs-lookup"><span data-stu-id="c5ea0-150">The client side of Azure Information Protection</span></span>](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [<span data-ttu-id="c5ea0-151">安裝 Azure 資訊保護用戶端</span><span class="sxs-lookup"><span data-stu-id="c5ea0-151">Installing the Azure Information Protection client</span></span>](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [<span data-ttu-id="c5ea0-152">手動安裝的下載頁面</span><span class="sxs-lookup"><span data-stu-id="c5ea0-152">Download page for manual installation</span></span>](https://www.microsoft.com/download/details.aspx?id=53018)
    
<span data-ttu-id="c5ea0-p107">安裝之後，您的使用者會加以執行，然後使用其 Office 365 帳戶從 Office 應用程式登入 (例如 Microsoft Word)。新的 [資訊保護]**** 列可讓使用者選取新的標籤。請確定您的使用者知道 SharePoint Online 小組網站以及要使用哪個標籤來保護其高度機密檔案。</span><span class="sxs-lookup"><span data-stu-id="c5ea0-p107">Once installed, your users run and then sign-in from an Office application (such as Microsoft Word) with their Office 365 account. A new **Information Protection** bar allows users to select the new label. Make sure that your users know the SharePoint Online team site and which label to use, to protect their highly confidential files.</span></span>
  
> [!NOTE]
> <span data-ttu-id="c5ea0-156">如果您有多個極機密 SharePoint Online 小組網站，應利用上述設定來建立多個 Azure 資訊保護限域原則，並設定子標籤，再將每個子標籤的權限設為特定 SharePoint Online 小組網站的網站成員存取群組。</span><span class="sxs-lookup"><span data-stu-id="c5ea0-156">If you have multiple highly sensitive SharePoint Online team sites, you should create multiple Azure Information Protection scoped policies with sub-labels with the above settings, with the permissions for each sub-label set to the site members access group of a specific SharePoint Online team site.</span></span> 
  
##<a name="adding-permissions-for-external-users"></a><span data-ttu-id="c5ea0-157">新增外部使用者的權限</span><span class="sxs-lookup"><span data-stu-id="c5ea0-157">Adding permissions for external users</span></span>
<span data-ttu-id="c5ea0-p108">您可以使用兩種方式，將 Azure 資訊保護所保護的檔案存取權授與外部使用者。在這兩種情況下，外部使用者皆必須擁有 Azure AD 帳戶。如果外部使用者不屬於使用 Azure AD 的組織成員，則可以使用下列註冊頁面以個人身分取得 Azure AD 帳戶：[https://aka.ms/aip-signup](https://aka.ms/aip-signup)。</span><span class="sxs-lookup"><span data-stu-id="c5ea0-p108">There are two ways you can grant external users access to files protected with Azure Information Protection. In both these cases, external users must have an Azure AD account. If external users aren't members of an organization that uses Azure AD, they can obtain an Azure AD account as an individual by using this sign-up page: [https://aka.ms/aip-signup](https://aka.ms/aip-signup).</span></span>

 - <span data-ttu-id="c5ea0-p109">將外部使用者新增至用來設定保護標籤的 Azure AD 群組。您必須先新增帳戶作為目錄中的 B2B 使用者。[Azure 資訊保護快取的群組成員資格](https://docs.microsoft.com/zh-TW/azure/information-protection/plan-design/prepare#group-membership-caching-by-azure-information-protection)可能需要幾個小時的時間。</span><span class="sxs-lookup"><span data-stu-id="c5ea0-p109">Add external users to an Azure AD group that is used to configure protection for a label. You’ll need to first add the account as a B2B user in your directory. It can take a couple of hours for group membership caching by Azure Rights Management. With this method, permissions are granted to all existing files protected with the label (even files protected before a user is added to the Azure AD group).</span></span>  
 - <span data-ttu-id="c5ea0-p110">將外部使用者直接新增至標籤保護。您可以從組織 (例如 Fabrikam.com)、Azure AD 群組 (例如組織內的財務部門) 或使用者，新增所有使用者。例如，您可以將外部的監理人員小組新增至標籤保護。</span><span class="sxs-lookup"><span data-stu-id="c5ea0-p110">Add external users directly to the label protection. You can add all users from an organization (e.g. Fabrikam.com), an Azure AD group (such as a finance group within an organization), or an individual user. For example, you can add an external team of regulators to the protection for a label. With this method, permissions are granted only to files protected with the label after the external entity is added to the protection.</span></span>

## <a name="see-also"></a><span data-ttu-id="c5ea0-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5ea0-167">See Also</span></span>

[<span data-ttu-id="c5ea0-168">保護 SharePoint Online 網站與檔案</span><span class="sxs-lookup"><span data-stu-id="c5ea0-168">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="c5ea0-169">在開發/測試環境中保護 SharePoint Online 網站</span><span class="sxs-lookup"><span data-stu-id="c5ea0-169">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="c5ea0-170">適用於政治活動、非營利組織和其他彈性組織的 Microsoft 安全性指南</span><span class="sxs-lookup"><span data-stu-id="c5ea0-170">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="c5ea0-171">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="c5ea0-171">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




