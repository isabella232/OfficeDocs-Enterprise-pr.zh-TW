---
title: "保護與 Azure 資訊保護的 SharePoint Online 檔案"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365, Strat_O365_Enterprise
ms.custom: Strat_O365_Enterprise, Ent_Solutions
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: "摘要： 適用於 Azure 資訊保護保護高度機密的 SharePoint Online 小組網站中的檔案。"
ms.openlocfilehash: f1a063f07b6e7488cf7512472631d0d2cae09733
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2018
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a><span data-ttu-id="6dd69-103">保護與 Azure 資訊保護的 SharePoint Online 檔案</span><span class="sxs-lookup"><span data-stu-id="6dd69-103">Protect SharePoint Online files with Azure Information Protection</span></span>

 <span data-ttu-id="6dd69-104">**摘要：**適用於 Azure 資訊保護保護高度機密的 SharePoint Online 小組網站中的檔案。</span><span class="sxs-lookup"><span data-stu-id="6dd69-104">**Summary:** Apply Azure Information Protection to protect files in a highly confidential SharePoint Online team site.</span></span>
  
<span data-ttu-id="6dd69-p101">使用本文中的步驟來設定 Azure 資訊保護提供加密和權限高度機密的 SharePoint Online 小組網站中的檔案。從網站下載時，即使與檔案一起出差加密和權限保護。如需高度機密的 SharePoint Online 小組網站的詳細資訊，請參閱[Secure SharePoint Online 網站及檔案](secure-sharepoint-online-sites-and-files.md)。</span><span class="sxs-lookup"><span data-stu-id="6dd69-p101">Use the steps in this article to configure Azure Information Protection to provide encryption and permissions for files in a highly confidential SharePoint Online team site. The encryption and permissions protection travels with a file even when it is downloaded from the site. For more information about highly confidential SharePoint Online team sites, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="6dd69-p102">當 Azure 資訊保護加密套用至檔案儲存在 Office 365 服務無法處理這些檔案的內容。共同撰寫 」、 「 eDiscovery 」、 「 搜尋 」、 「 Delve、 和 「 其他共同作業功能無法運作。資料外洩防護 (DLP) 原則僅可用於 （包括 Office 365 標籤） 的中繼資料，但不是 （例如檔案內的信用卡號碼） 這些檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="6dd69-p102">When Azure Information Protection encryption is applied to files stored in Office 365, the service cannot process the contents of these files. Co-authoring, eDiscovery, search, Delve, and other collaborative features do not work. Data Loss Prevention (DLP) policies can only work with the metadata (including Office 365 labels) but not the contents of these files (such as credit card numbers within files).</span></span> 
  
<span data-ttu-id="6dd69-111">首先，使用中[與 Office 365 系統管理中心啟動 Azure RMS](https://docs.microsoft.com/information-protection/deploy-use/activate-office365)的指示為您的 Office 365 訂閱。</span><span class="sxs-lookup"><span data-stu-id="6dd69-111">First, use the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) for your Office 365 subscription.</span></span>
  
<span data-ttu-id="6dd69-112">接下來，設定新範圍的原則與保護和高度機密 SharePoint Online 小組網站的權限的子標籤 Azure 資訊保護。</span><span class="sxs-lookup"><span data-stu-id="6dd69-112">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions of your highly confidential SharePoint Online team site.</span></span>
  
1. <span data-ttu-id="6dd69-p103">Office 365 入口網站與有安全性管理員或公司管理員角色的帳戶登入。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="6dd69-p103">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="6dd69-115">在瀏覽器中的個別] 索引標籤移至 Azure 入口網站 ([https://portal.azure.com](https://portal.azure.com))。</span><span class="sxs-lookup"><span data-stu-id="6dd69-115">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="6dd69-116">如果這是您要設定 Azure 資訊保護第一次，請參閱這些[指示](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time)。</span><span class="sxs-lookup"><span data-stu-id="6dd69-116">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="6dd69-117">在 [清單] 窗格中，按一下 [**更多的服務**、 輸入**資訊**，和 [ **Azure 資訊保護**。</span><span class="sxs-lookup"><span data-stu-id="6dd69-117">In the list pane, click **More services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="6dd69-118">**Azure 資訊保護**blade、 上，按一下 [**範圍設定的原則 > + 新增原則**。</span><span class="sxs-lookup"><span data-stu-id="6dd69-118">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="6dd69-119">輸入 [**原則名稱**] 及 [ **Description**中的描述的新原則的名稱。</span><span class="sxs-lookup"><span data-stu-id="6dd69-119">Type a name for the new policy in **Policy name** and a description in **Description**.</span></span>
    
7. <span data-ttu-id="6dd69-120">按一下 [**選取哪些使用者或群組取得此原則 > 使用者/群組**，然後選取 [網站成員存取的極高機密 SharePoint Online 小組網站的群組。</span><span class="sxs-lookup"><span data-stu-id="6dd69-120">Click **Select which users or groups get this policy > User/Groups**, and then select the site members access group for your highly sensitive SharePoint Online team site.</span></span> 
    
8. <span data-ttu-id="6dd69-121">按一下 [**選取 > [確定]**。</span><span class="sxs-lookup"><span data-stu-id="6dd69-121">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="6dd69-122">**高度機密**標籤中，按一下省略符號 （...）] 和 [**新增子標籤**。</span><span class="sxs-lookup"><span data-stu-id="6dd69-122">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="6dd69-123">輸入**名稱**與**描述**標籤的描述的子標籤名稱。</span><span class="sxs-lookup"><span data-stu-id="6dd69-123">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="6dd69-124">在**設定文件及包含此標籤的電子郵件的權限**，請按一下 [**保護**]。</span><span class="sxs-lookup"><span data-stu-id="6dd69-124">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="6dd69-125">在 [**保護**] 區段中，按一下 [ **Azure （雲端索引鍵）**。</span><span class="sxs-lookup"><span data-stu-id="6dd69-125">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="6dd69-126">在**保護**blade，**保護設定**] 下按一下 [ **+ 新增權限**。</span><span class="sxs-lookup"><span data-stu-id="6dd69-126">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="6dd69-127">在**新增權限**blade 中，**指定使用者與群組**] 下按一下 [ **+ 瀏覽目錄]**。</span><span class="sxs-lookup"><span data-stu-id="6dd69-127">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="6dd69-128">在**AAD 使用者與群組**] 窗格中，選取您極高機密的 SharePoint Online 小組網站、 網站成員存取群組及 [**選取**。</span><span class="sxs-lookup"><span data-stu-id="6dd69-128">On the **AAD Users and Groups** pane, select the site members access group for your highly sensitive SharePoint Online team site, and then click **Select**.</span></span>
    
16. <span data-ttu-id="6dd69-129">在**預設選擇權限**] 下方清除**列印**、**複製及擷取內容**以及**轉寄**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="6dd69-129">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="6dd69-130">按兩次 [**確定]** 。</span><span class="sxs-lookup"><span data-stu-id="6dd69-130">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="6dd69-131">在**子標籤**blade 中，按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="6dd69-131">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="6dd69-132">關閉新範圍的原則 blade。</span><span class="sxs-lookup"><span data-stu-id="6dd69-132">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="6dd69-133">在**Azure 資訊保護-範圍的原則**blade 中，按一下 [**發佈**]。</span><span class="sxs-lookup"><span data-stu-id="6dd69-133">On the **Azure Information protection - Scoped policies** blade, click **Publish**.</span></span>
    
<span data-ttu-id="6dd69-134">這是您所產生的設定以便高度機密 SharePoint Online 小組網站。</span><span class="sxs-lookup"><span data-stu-id="6dd69-134">This is your resulting configuration for your highly confidential SharePoint Online team site.</span></span>
  
![適用於隔離 SharePoint Online 小組網站的 Azure 資訊保護。](images/8cc92aa4-e7bc-4c2f-a4a4-3b034b21aebf.png)
  
<span data-ttu-id="6dd69-136">您現在準備開始建立文件及保護其 Azure 資訊保護及新的標籤。</span><span class="sxs-lookup"><span data-stu-id="6dd69-136">You are now ready to begin creating documents and protecting them with Azure Information Protection and your new label.</span></span>
  
<span data-ttu-id="6dd69-p104">您必須[安裝 Azure 資訊保護用戶端](https://docs.microsoft.com/information-protection/rms-client/install-client-app)裝置或 Windows 電腦上。您可以使用指令碼及自動化安裝，或使用者可以手動安裝用戶端。請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="6dd69-p104">You must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on your device or Windows-based computer. You can script and automate the installation, or users can install the client manually. See the following resources:</span></span>
  
- [<span data-ttu-id="6dd69-140">Azure 資訊保護用戶端</span><span class="sxs-lookup"><span data-stu-id="6dd69-140">The client side of Azure Information Protection</span></span>](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [<span data-ttu-id="6dd69-141">安裝 Azure 資訊保護用戶端</span><span class="sxs-lookup"><span data-stu-id="6dd69-141">Installing the Azure Information Protection client</span></span>](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- <span data-ttu-id="6dd69-142">[下載] 頁面上的手動安裝](https://www.microsoft.com/download/details.aspx?id=53018)</span><span class="sxs-lookup"><span data-stu-id="6dd69-142">[Download page for manual installation](https://www.microsoft.com/download/details.aspx?id=53018)</span></span>
    
<span data-ttu-id="6dd69-p105">安裝之後，您的使用者執行並再登入的 Office 應用程式 （例如 Microsoft Word) 以其 Office 365 帳戶。將新的**資訊保護**列可讓使用者選取新的標籤。請確定您的使用者了解 SharePoint Online 小組網站和其標籤使用，來保護其高度機密檔案。</span><span class="sxs-lookup"><span data-stu-id="6dd69-p105">Once installed, your users run and then sign-in from an Office application (such as Microsoft Word) with their Office 365 account. A new **Information Protection** bar allows users to select the new label. Make sure that your users know the SharePoint Online team site and which label to use, to protect their highly confidential files.</span></span>
  
> [!NOTE]
> <span data-ttu-id="6dd69-146">如果您有多個極高機密的 SharePoint Online 小組網站，您應該具有上述設定、 使用每個子標籤設為網站成員存取群組的權限子標籤建立多個 Azure 資訊保護範圍的原則特定的 SharePoint Online 小組網站。</span><span class="sxs-lookup"><span data-stu-id="6dd69-146">If you have multiple highly sensitive SharePoint Online team sites, you should create multiple Azure Information Protection scoped policies with sub-labels with the above settings, with the permissions for each sub-label set to the site members access group of a specific SharePoint Online team site.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="6dd69-147">請參閱</span><span class="sxs-lookup"><span data-stu-id="6dd69-147">See Also</span></span>

[<span data-ttu-id="6dd69-148">安全的 SharePoint Online 網站及檔案</span><span class="sxs-lookup"><span data-stu-id="6dd69-148">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="6dd69-149">安全的開發人員/測試環境中的 SharePoint Online 網站</span><span class="sxs-lookup"><span data-stu-id="6dd69-149">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="6dd69-150">Microsoft 安全性指導政治活動、 非營利機構，以及其他靈活的組織</span><span class="sxs-lookup"><span data-stu-id="6dd69-150">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="6dd69-151">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="6dd69-151">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




