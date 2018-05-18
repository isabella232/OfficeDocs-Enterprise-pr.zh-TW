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
ms.openlocfilehash: a5df4d7289ec31686ad74f78a4797e1aa3eaa447
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a><span data-ttu-id="55f17-103">使用 Azure 資訊保護來保護 SharePoint Online 檔案</span><span class="sxs-lookup"><span data-stu-id="55f17-103">Protect SharePoint Online files with Azure Information Protection</span></span>

 <span data-ttu-id="55f17-104">**摘要：** 套用 Azure 資訊保護來保護高度機密 SharePoint Online 小組網站中的檔案。</span><span class="sxs-lookup"><span data-stu-id="55f17-104">**Summary:** Apply Azure Information Protection to protect files in a highly confidential SharePoint Online team site.</span></span>
  
<span data-ttu-id="55f17-p101">使用本文中的步驟來設定 Azure 資訊保護，為高度機密 SharePoint Online 小組網站中的檔案提供加密和權限。從網站下載檔案時，加密和權限保護會隨附於檔案。如需高度機密 SharePoint Online 小組網站的詳細資訊，請參閱＜[ SharePoint Online 網站和檔案](secure-sharepoint-online-sites-and-files.md)＞。</span><span class="sxs-lookup"><span data-stu-id="55f17-p101">Use the steps in this article to configure Azure Information Protection to provide encryption and permissions for files in a highly confidential SharePoint Online team site. The encryption and permissions protection travels with a file even when it is downloaded from the site. For more information about highly confidential SharePoint Online team sites, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="55f17-p102">將 Azure 資訊保護加密套用至儲存於 Office 365 中的檔案時，服務會無法處理這些檔案的內容。 共同撰寫、eDiscovery、搜尋、Delve 和其他共同作業功能無法運作。 此外，資料外洩防護 (DLP) 原則只可用於中繼資料 (包括 Office 365 標籤)，但無法用於這些檔案的內容 (例如檔案中的信用卡號碼)。</span><span class="sxs-lookup"><span data-stu-id="55f17-p102">When Azure Information Protection encryption is applied to files stored in Office 365, the service cannot process the contents of these files. Co-authoring, eDiscovery, search, Delve, and other collaborative features do not work. Data Loss Prevention (DLP) policies can only work with the metadata (including Office 365 labels) but not the contents of these files (such as credit card numbers within files).</span></span> 
  
<span data-ttu-id="55f17-111">首先，針對您的 Office 365 訂閱使用＜[使用 Office 365 系統管理中心啟用 Azure RMS](https://docs.microsoft.com/information-protection/deploy-use/activate-office365)＞中的指示。</span><span class="sxs-lookup"><span data-stu-id="55f17-111">First, follow the instructions in [Activate Azure RMS with the Office 365 admin center for your Office 365 subscription](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span></span>
  
<span data-ttu-id="55f17-112">接著，為 Azure 資訊保護設定新的限域原則和子標籤，為高度機密 SharePoint Online 小組網站提供保護與權限。</span><span class="sxs-lookup"><span data-stu-id="55f17-112">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions for your highly confidential SharePoint Online team site by following these steps:</span></span>
  
1. <span data-ttu-id="55f17-p103">使用具有安全性系統管理員或公司系統管理員角色的帳戶登入 Office 365 入口網站。 如需說明，請參閱[在何處登入 Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="55f17-p103">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="55f17-115">在您瀏覽器的個別索引標籤中，移至 Azure 入口網站 ([https://portal.azure.com](https://portal.azure.com))。</span><span class="sxs-lookup"><span data-stu-id="55f17-115">In a separate tab of your browser, go to the Azure portal (https://portal.azure.com).</span></span>
    
3. <span data-ttu-id="55f17-116">如果這是您第一次設定 Azure 資訊保護，請參閱這些[指示](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time)。</span><span class="sxs-lookup"><span data-stu-id="55f17-116">If this is the first time you are configuring Azure Information Protection, see [these instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="55f17-117">在清單窗格中，按一下 [更多服務]****，輸入**資訊**，然後按一下 [Azure 資訊保護]****。</span><span class="sxs-lookup"><span data-stu-id="55f17-117">In the list pane, click **More services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="55f17-118">在 [Azure 資訊保護]**** 刀鋒視窗中，按一下 [限域原則] > [+ 新增原則]****。</span><span class="sxs-lookup"><span data-stu-id="55f17-118">On the **Azure Information protection** blade, click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="55f17-119">在 [原則名稱]**** 中輸入新原則的名稱，並在 [描述]**** 中輸入描述。</span><span class="sxs-lookup"><span data-stu-id="55f17-119">Type a name for the new policy in **Policy name** and a description in **Description**.</span></span>
    
7. <span data-ttu-id="55f17-120">按一下 [選取取得此原則的使用者或群組] > [使用者/群組]****，然後選取極機密 SharePoint Online 小組網站的網站成員存取群組。</span><span class="sxs-lookup"><span data-stu-id="55f17-120">Click **Select which users or groups get this policy > User/Groups**, and then select the site members access group for your highly sensitive SharePoint Online team site.</span></span> 
    
8. <span data-ttu-id="55f17-121">按一下 [選取] > [確定]****。</span><span class="sxs-lookup"><span data-stu-id="55f17-121">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="55f17-122">針對 [高度機密]**** 標籤，按一下省略符號 (...)，然後再按一下 [新增子標籤]****。</span><span class="sxs-lookup"><span data-stu-id="55f17-122">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="55f17-123">在 [名稱]**** 中鍵入子標籤的名稱，並在 [描述]**** 中鍵入標籤的描述。</span><span class="sxs-lookup"><span data-stu-id="55f17-123">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="55f17-124">在 [為包含此標籤的文件與電子郵件設定權限]**** 中，按一下 [保護]****。</span><span class="sxs-lookup"><span data-stu-id="55f17-124">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="55f17-125">在 [保護]**** 區段中，按一下 [Azure (雲端金鑰)]****。</span><span class="sxs-lookup"><span data-stu-id="55f17-125">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="55f17-126">在 [保護]**** 刀鋒視窗中，按一下 [保護設定]**** 下的 [+ 新增權限]****。</span><span class="sxs-lookup"><span data-stu-id="55f17-126">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="55f17-127">在 [新增權限]**** 刀鋒視窗中，按一下 [指定使用者與群組]**** 下的 [+ 瀏覽目錄]****。</span><span class="sxs-lookup"><span data-stu-id="55f17-127">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="55f17-128">在 [AAD 使用者與群組]**** 窗格中，選取您高度機密 SharePoint Online 小組網站的網站成員存取群組，然後按一下 [選取]****。</span><span class="sxs-lookup"><span data-stu-id="55f17-128">On the **AAD Users and Groups** pane, select the site members access group for your highly sensitive SharePoint Online team site, and click **Select**.</span></span>
    
16. <span data-ttu-id="55f17-129">在 [從預設選擇權限]**** 下，清除 [列印]****、[複製並擷取內容]**** 和 [轉寄]**** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="55f17-129">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="55f17-130">按兩次 [確定]****。</span><span class="sxs-lookup"><span data-stu-id="55f17-130">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="55f17-131">在 [子標籤]**** 刀鋒視窗中，按一下 [儲存]****。</span><span class="sxs-lookup"><span data-stu-id="55f17-131">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="55f17-132">關閉新的限域原則刀鋒視窗。</span><span class="sxs-lookup"><span data-stu-id="55f17-132">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="55f17-133">在 [Azure 資訊保護 – 限域原則]**** 刀鋒視窗中，按一下 [發佈]****。</span><span class="sxs-lookup"><span data-stu-id="55f17-133">On the **Azure Information Protection – Scoped policies** blade, click **Publish**, and then click Yes.</span></span>
    
<span data-ttu-id="55f17-134">以下是高度機密 SharePoint Online 小組網站的設定結果。</span><span class="sxs-lookup"><span data-stu-id="55f17-134">This is the resulting configuration for your highly confidential SharePoint Online team site.</span></span>
  
![適用於隔離 SharePoint Online 小組網站的 Azure 資訊保護。](images/8cc92aa4-e7bc-4c2f-a4a4-3b034b21aebf.png)
  
<span data-ttu-id="55f17-136">現在您已可開始建立文件，並利用 Azure 資訊保護和新標籤進行保護。</span><span class="sxs-lookup"><span data-stu-id="55f17-136">You are now ready to begin creating documents and protecting them with Azure Information Protection and your new label.</span></span>
  
<span data-ttu-id="55f17-p104">您必須在自己的裝置或以 Windows 為基礎的電腦上[安裝 Azure 資訊保護用戶端](https://docs.microsoft.com/information-protection/rms-client/install-client-app)。您可以編寫指令碼並自動化安裝，使用者也可以手動安裝用戶端。請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="55f17-p104">You must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on your device or Windows-based computer. You can script and automate the installation, or users can install the client manually.</span></span>
  
- [<span data-ttu-id="55f17-140">Azure 資訊保護的用戶端</span><span class="sxs-lookup"><span data-stu-id="55f17-140">The client side of Azure Information Protection</span></span>](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [<span data-ttu-id="55f17-141">安裝 Azure 資訊保護用戶端</span><span class="sxs-lookup"><span data-stu-id="55f17-141">Installing the Azure Information Protection client</span></span>](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [<span data-ttu-id="55f17-142">手動安裝的下載頁面</span><span class="sxs-lookup"><span data-stu-id="55f17-142">Download page for manual installation</span></span>](https://www.microsoft.com/download/details.aspx?id=53018)
    
<span data-ttu-id="55f17-p105">安裝之後，您的使用者會加以執行，然後使用其 Office 365 帳戶從 Office 應用程式登入 (例如 Microsoft Word)。新的 [資訊保護]**** 列可讓使用者選取新的標籤。請確定您的使用者知道 SharePoint Online 小組網站以及要使用哪個標籤來保護其高度機密檔案。</span><span class="sxs-lookup"><span data-stu-id="55f17-p105">Once installed, your users run and then sign-in from an Office application (such as Microsoft Word) with their Office 365 account. A new **Information Protection** bar allows users to select the new label. Make sure that your users know the SharePoint Online team site and which label to use, to protect their highly confidential files.</span></span>
  
> [!NOTE]
> <span data-ttu-id="55f17-146">如果您有多個極機密 SharePoint Online 小組網站，應利用上述設定來建立多個 Azure 資訊保護限域原則，並設定子標籤，再將每個子標籤的權限設為特定 SharePoint Online 小組網站的網站成員存取群組。</span><span class="sxs-lookup"><span data-stu-id="55f17-146">If you have multiple highly sensitive SharePoint Online team sites, you should create multiple Azure Information Protection scoped policies with sub-labels with the above settings, with the permissions for each sub-label set to the site members access group of a specific SharePoint Online team site.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="55f17-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55f17-147">See Also</span></span>

[<span data-ttu-id="55f17-148">保護 SharePoint Online 網站與檔案</span><span class="sxs-lookup"><span data-stu-id="55f17-148">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="55f17-149">在開發/測試環境中保護 SharePoint Online 網站</span><span class="sxs-lookup"><span data-stu-id="55f17-149">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="55f17-150">適用於政治活動、非營利組織和其他彈性組織的 Microsoft 安全性指南</span><span class="sxs-lookup"><span data-stu-id="55f17-150">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="55f17-151">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="55f17-151">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




