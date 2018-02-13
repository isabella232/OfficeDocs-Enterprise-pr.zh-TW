---
title: "資料分類和 Office 365 開發人員/測試環境中顯示標籤"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: TLG, Ent_TLGs
ms.assetid: 919b8fc7-b0bc-46db-91f5-37342564e01b
description: "摘要： 設定與示範資料分類和 Office 365 開發人員/測試環境中使用 Azure 資訊保護 (AIP) 用戶端顯示標籤。"
ms.openlocfilehash: 84dc3b8d86a53f7c91d5c226b5c745f5d39731a9
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2018
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a><span data-ttu-id="b3d68-103">資料分類和 Office 365 開發人員/測試環境中顯示標籤</span><span class="sxs-lookup"><span data-stu-id="b3d68-103">Data classification and labeling in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="b3d68-104">**摘要：**設定與示範資料分類和 Office 365 開發人員/測試環境中使用 Azure 資訊保護 (AIP) 用戶端顯示標籤。</span><span class="sxs-lookup"><span data-stu-id="b3d68-104">**Summary:** Configure and demonstrate data classification and labeling using the Azure Information Protection (AIP) client in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="b3d68-p101">Azure 資訊保護用戶端可讓您將分類文件之前您將其上傳至 Office 365 中的 SharePoint Online 資料夾。使用本文中的指示、 安裝 Azure 資訊保護用戶端及示範資料分類。如需詳細資訊，請參閱[Azure 資訊保護](https://www.microsoft.com/cloud-platform/azure-information-protection)。</span><span class="sxs-lookup"><span data-stu-id="b3d68-p101">The Azure Information Protection client allows you to classify a document before you upload it to a SharePoint Online folder in Office 365. With the instructions in this article, you install the Azure Information Protection client and demonstrate data classification. For more information, see [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection).</span></span>
  
> [!TIP]
> <span data-ttu-id="b3d68-108">按一下[此處](http://aka.ms/catlgstack)的視覺對應至一個 Microsoft Cloud 測試實驗室指南堆疊中所有的文章。</span><span class="sxs-lookup"><span data-stu-id="b3d68-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="b3d68-109">階段 1： 建立 Office 365 開發人員/測試環境</span><span class="sxs-lookup"><span data-stu-id="b3d68-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="b3d68-110">遵循在[Office 365 開發人員/測試環境](office-365-dev-test-environment.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="b3d68-110">Follow the instructions in [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a><span data-ttu-id="b3d68-111">階段 2： 新增 Azure 資訊保護試用訂閱</span><span class="sxs-lookup"><span data-stu-id="b3d68-111">Phase 2: Add the Azure Information Protection trial subscription</span></span>

<span data-ttu-id="b3d68-p102">在此階段中，您可以新增至 Office 365 開發人員/測試環境的 Azure 資訊保護及啟用的使用者帳戶。如果您已設定的[Office 365 和 EMS 開發/測試環境](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)，請略過此階段中。Enterprise 行動性套件試用訂閱包括 Azure Information Protection 授權。</span><span class="sxs-lookup"><span data-stu-id="b3d68-p102">In this phase, you add Azure Information Protection to your Office 365 dev/test environment and enable it for your user accounts. If you have configured the [Office 365 and EMS dev/test environment](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), skip this phase. The Enterprise Mobility Suite trial subscription includes Azure Information Protection licenses.</span></span>
  
<span data-ttu-id="b3d68-115">首先，註冊 Azure 資訊保護試用訂閱。</span><span class="sxs-lookup"><span data-stu-id="b3d68-115">First, sign up for an Azure Information Protection trial subscription.</span></span>
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a><span data-ttu-id="b3d68-116">註冊 Azure 資訊保護試用訂閱</span><span class="sxs-lookup"><span data-stu-id="b3d68-116">Sign up for an Azure Information Protection trial subscription</span></span>

1. <span data-ttu-id="b3d68-117">在 Internet Explorer 或瀏覽器中，移至[http://portal.office.com](http://portal.office.com)並使用您的 Office 365 全域管理員帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="b3d68-117">In Internet Explorer or your browser, go to [http://portal.office.com](http://portal.office.com) and sign in with your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="b3d68-118">在 [ **Microsoft Office Home** ] 索引標籤上按一下**系統管理**磚。</span><span class="sxs-lookup"><span data-stu-id="b3d68-118">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="b3d68-119">在 Office 365 系統管理員] 索引標籤的 [在左導覽列中，按一下 [**帳務 > 購買服務**。</span><span class="sxs-lookup"><span data-stu-id="b3d68-119">On the Office 365 Admin tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="b3d68-p103">在 [**購買服務**] 頁面上尋找**Azure 資訊保護 Premium P2**項目。將滑鼠停留並按一下 [**開始免費試用版**。</span><span class="sxs-lookup"><span data-stu-id="b3d68-p103">On the **Purchase services** page, find the **Azure Information Protection Premium P2** item. Hover your mouse over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="b3d68-122">在 [**確認您的訂單**] 頁面上按一下 [**立即試用**。</span><span class="sxs-lookup"><span data-stu-id="b3d68-122">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="b3d68-123">在 [**順序回條**] 頁面上按一下 [**繼續**]。</span><span class="sxs-lookup"><span data-stu-id="b3d68-123">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="b3d68-124">接下來，您可讓所有使用者帳戶的 Azure 資訊保護授權。</span><span class="sxs-lookup"><span data-stu-id="b3d68-124">Next, you enable the Azure Information Protection license for all user accounts.</span></span>
  
1. <span data-ttu-id="b3d68-125">在 [Office 365 系統管理中心] 索引標籤上按一下 [**使用者**]。</span><span class="sxs-lookup"><span data-stu-id="b3d68-125">On the Office 365 admin center tab, click **Users**.</span></span>
    
2.  <span data-ttu-id="b3d68-126">在 [使用者帳戶] 清單選取您的全域管理員帳戶] 和 [**編輯****產品**授權。</span><span class="sxs-lookup"><span data-stu-id="b3d68-126">In the list of user accounts, select your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="b3d68-127">開啟以**在** **Azure 資訊保護 Premium P2**產品授權、 按一下 [**儲存]**和 [**關閉**兩次。</span><span class="sxs-lookup"><span data-stu-id="b3d68-127">Turn the product license for **Azure Information Protection Premium P2** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="b3d68-128">針對其他使用者帳戶 (使用者 1 到使用者 5) 重複步驟 2 和 3。</span><span class="sxs-lookup"><span data-stu-id="b3d68-128">Repeat steps 2 and 3 for your other user accounts (User 1 through User 5).</span></span>
    
<span data-ttu-id="b3d68-129">Office 365 開發人員/測試環境現在有：</span><span class="sxs-lookup"><span data-stu-id="b3d68-129">Your Office 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="b3d68-130">Office 365 E5 企業版及 Azure 資訊保護試用版訂閱。</span><span class="sxs-lookup"><span data-stu-id="b3d68-130">Office 365 E5 Enterprise and Azure Information Protection trial subscriptions.</span></span>
    
- <span data-ttu-id="b3d68-131">所有的使用者帳戶能夠使用 Office 365 E5 Enterprise 和 Azure 資訊保護。</span><span class="sxs-lookup"><span data-stu-id="b3d68-131">All of your user accounts enabled to use both Office 365 E5 Enterprise and Azure Information Protection.</span></span>
    
## <a name="phase-3-demonstrate-data-classification"></a><span data-ttu-id="b3d68-132">階段 3： 示範資料分類</span><span class="sxs-lookup"><span data-stu-id="b3d68-132">Phase 3: Demonstrate data classification</span></span>

<span data-ttu-id="b3d68-133">在此階段中，您會示範使用 Azure 資訊保護用戶端及預設 Azure 資訊保護原則的資料分類。</span><span class="sxs-lookup"><span data-stu-id="b3d68-133">In this phase, you demonstrate data classification using the Azure Information Protection client and the default Azure Information Protection policy.</span></span>
  
<span data-ttu-id="b3d68-134">如果您使用模擬的企業版 Office 365 開發人員/測試環境，所以您必須先在 CLIENT1 上安裝 Office 2016。</span><span class="sxs-lookup"><span data-stu-id="b3d68-134">If you are using the simulated enterprise Office 365 dev/test environment, you must first install Office 2016 on CLIENT1.</span></span>
  
1. <span data-ttu-id="b3d68-135">使用您的瀏覽器，並移至[Azure 入口網站](http://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="b3d68-135">Use your browser and go to the [Azure portal](http://portal.azure.com).</span></span>
    
2. <span data-ttu-id="b3d68-136">按一下 [**資源群組 >** [您資源群組名稱] **> CLIENT1 > Connect**。</span><span class="sxs-lookup"><span data-stu-id="b3d68-136">Click **Resource Groups >** [your resource group name] **> CLIENT1 > Connect**.</span></span>
    
3. <span data-ttu-id="b3d68-137">在 CLIENT1 中，執行 Internet Explorer、 移至[http://portal.office.com](http://portal.office.com)、 Office 入口網站並再登入 User5 帳戶名稱及密碼。</span><span class="sxs-lookup"><span data-stu-id="b3d68-137">From CLIENT1, run Internet Explorer, go to the Office portal at [http://portal.office.com](http://portal.office.com), and then sign in with the User5 account name and password.</span></span>
    
4. <span data-ttu-id="b3d68-138">在 [ **Microsoft Office Home** ] 索引標籤上按一下 [**安裝 Office 2016**。</span><span class="sxs-lookup"><span data-stu-id="b3d68-138">On the **Microsoft Office Home** tab, click **Install Office 2016**.</span></span>
    
5. <span data-ttu-id="b3d68-p104">執行時提示並且**是**由使用者帳戶控制提示時按一下下載。等候安裝 Office。完成後，按一下 [**關閉**兩次。</span><span class="sxs-lookup"><span data-stu-id="b3d68-p104">Run the download when prompted and click **Yes** when prompted by User Account Control. Wait for Office to install. When complete, click **Close** twice.</span></span>
    
<span data-ttu-id="b3d68-142">下一步] 安裝 Azure 資訊保護用戶端。</span><span class="sxs-lookup"><span data-stu-id="b3d68-142">Next, you install the Azure Information Protection client.</span></span>
  
1. <span data-ttu-id="b3d68-143">在瀏覽器或 Internet Explorer 中，移至[Microsoft Azure 資訊保護下載頁面](https://www.microsoft.com/download/details.aspx?id=53018)。</span><span class="sxs-lookup"><span data-stu-id="b3d68-143">In your browser or Internet Explorer, go to the [Microsoft Azure Information Protection download page](https://www.microsoft.com/download/details.aspx?id=53018).</span></span>
    
  - <span data-ttu-id="b3d68-144">如果您使用 Office 365 開發人員/測試環境的輕量型版本，請在您的本機電腦上使用瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="b3d68-144">If you are using the lightweight version of the Office 365 dev/test environment, use the browser on your local computer.</span></span>
    
  - <span data-ttu-id="b3d68-145">如果您使用模擬的企業版 Office 365 開發人員/測試環境，請從 CLIENT1 執行 Internet Explorer。</span><span class="sxs-lookup"><span data-stu-id="b3d68-145">If you are using the simulated enterprise Office 365 dev/test environment, run Internet Explorer from CLIENT1.</span></span>
    
2. <span data-ttu-id="b3d68-146">在**Microsoft Azure 資訊保護**下載] 頁面上，按一下 [**下載**]、 按一下**AzInfoProtection.exe**、，然後按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="b3d68-146">On the **Microsoft Azure Information Protection** download page, click **Download**, click **AzInfoProtection.exe**, and then click **Next**.</span></span>
    
3. <span data-ttu-id="b3d68-147">出現提示時，執行 AzInfoProtection.exe。</span><span class="sxs-lookup"><span data-stu-id="b3d68-147">When prompted, run AzInfoProtection.exe.</span></span>
    
4. <span data-ttu-id="b3d68-148">在 [**安裝 Azure 資訊保護**用戶端] 方塊中，按一下 [**我同意**] 並再按一下**[是]**的使用者帳戶控制提示時。</span><span class="sxs-lookup"><span data-stu-id="b3d68-148">In the **Install the Azure Information Protection** client box, click **I agree**, and then click **Yes** when prompted by User Account Control.</span></span>
    
5. <span data-ttu-id="b3d68-149">在 [**成功**] 方塊中按一下 [ **Close。**</span><span class="sxs-lookup"><span data-stu-id="b3d68-149">In the **Completed successfully** box, click **Close.**</span></span>
    
<span data-ttu-id="b3d68-150">接下來，您會示範文件分類。</span><span class="sxs-lookup"><span data-stu-id="b3d68-150">Next, you demonstrate document classification.</span></span>
  
1. <span data-ttu-id="b3d68-151">按一下工作列上的**Word**圖示。</span><span class="sxs-lookup"><span data-stu-id="b3d68-151">Click the **Word** icon in the taskbar.</span></span>
    
2. <span data-ttu-id="b3d68-152">出現提示時，使用 User5 帳戶名稱和密碼登入。</span><span class="sxs-lookup"><span data-stu-id="b3d68-152">When prompted, sign in with the User5 account name and password.</span></span>
    
3. <span data-ttu-id="b3d68-153">如果您只是安裝在 CLIENT1 中，Office 2016**第一個事項第一個**] 方塊中，按一下 [**接受**]。</span><span class="sxs-lookup"><span data-stu-id="b3d68-153">If you just installed Office 2016 on CLIENT1, in the **First things first** box, click **Accept**.</span></span>
    
4. <span data-ttu-id="b3d68-154">按一下 [**空白文件**。</span><span class="sxs-lookup"><span data-stu-id="b3d68-154">Click **Blank document**.</span></span> 
    
    <span data-ttu-id="b3d68-155">請注意 [**保護**] 區段中的功能區的 [**首頁**] 索引標籤和文件分類的資料列。</span><span class="sxs-lookup"><span data-stu-id="b3d68-155">Note the **Protection** section of the ribbon on the **Home** tab and the row of document classifications.</span></span>
    
5. <span data-ttu-id="b3d68-156">在空白的文件中，輸入一些文字。</span><span class="sxs-lookup"><span data-stu-id="b3d68-156">In the blank document, type some text.</span></span>
    
6. <span data-ttu-id="b3d68-157">按一下 [**檔 > 儲存**且輸入名稱**BeforeAIP**，然後按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="b3d68-157">Click **File > Save**, type the name **BeforeAIP**, and then click **OK**.</span></span> 
    
7. <span data-ttu-id="b3d68-158">在文件類別的資料列的**密碼**，按一下向下箭頭和 [**全部公司**。</span><span class="sxs-lookup"><span data-stu-id="b3d68-158">In the row of document classes, click the down arrow for **Secret**, and then click **All Company**.</span></span>
    
8. <span data-ttu-id="b3d68-159">按一下 [**檔 > 另存新檔**且輸入名稱**AfterAIP**，然後按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="b3d68-159">Click **File > Save As**, type the name **AfterAIP**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="b3d68-160">在工作列上，按一下 [**檔案總管]** ，然後開啟 [**文件**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="b3d68-160">Click **File Explorer** in the taskbar, and then open the **Documents** folder.</span></span>
    
    <span data-ttu-id="b3d68-p105">請注意**BeforeAIP**和**AfterAIP**文件不同的檔案大小。因為包含分類資訊，AfterAIP 文件是更大。</span><span class="sxs-lookup"><span data-stu-id="b3d68-p105">Note the different file sizes of the **BeforeAIP** and **AfterAIP** documents. The AfterAIP document is larger because it contains the classification information.</span></span>
    
<span data-ttu-id="b3d68-163">接下來，您讓所有人存取支援網站集合。</span><span class="sxs-lookup"><span data-stu-id="b3d68-163">Next, you allow everyone to access the Support site collection.</span></span>
  
1. <span data-ttu-id="b3d68-164">在 [ **Microsoft Office Home** ] 索引標籤上按一下 [ **SharePoint**]。</span><span class="sxs-lookup"><span data-stu-id="b3d68-164">On the **Microsoft Office Home** tab, click **SharePoint**.</span></span>
    
2. <span data-ttu-id="b3d68-165">從**SharePoint** ] 索引標籤上，按一下 [**支援網站集合**]。</span><span class="sxs-lookup"><span data-stu-id="b3d68-165">From the **SharePoint** tab, click **Support site collection**.</span></span>
    
3. <span data-ttu-id="b3d68-166">在右上方，按一下 [**設定**] 圖示，和 [**共用對象**。</span><span class="sxs-lookup"><span data-stu-id="b3d68-166">In the upper right, click the **Settings** icon, and then click **Shared with**.</span></span>
    
4. <span data-ttu-id="b3d68-167">在**共用 '支援網站集合'**，按一下 [**進階**]。</span><span class="sxs-lookup"><span data-stu-id="b3d68-167">In **Share 'Support site collection'**, click **Advanced**.</span></span>
    
5. <span data-ttu-id="b3d68-168">在 SharePoint 群組的清單中，按一下**支援網站集合的成員**。</span><span class="sxs-lookup"><span data-stu-id="b3d68-168">In the list of SharePoint groups, click **Support site collection Members**.</span></span>
    
6. <span data-ttu-id="b3d68-169">在 [**人員與群組**] 頁面上按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="b3d68-169">On the **People and Groups** page, click **New**.</span></span>
    
7. <span data-ttu-id="b3d68-170">在**共用 '支援網站集合 」**，輸入**所有人**、 [**所有人以外的外部使用者**，和 [**共用。**</span><span class="sxs-lookup"><span data-stu-id="b3d68-170">In **Share 'Support site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share.**</span></span>
    
8. <span data-ttu-id="b3d68-171">關閉 [**人員與群組**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b3d68-171">Close the **People and Groups** tab.</span></span>
    
<span data-ttu-id="b3d68-172">接著，您使用 User5 帳戶登入並將 AIP 受保護文件上傳至支援網站集合的文件] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="b3d68-172">Next, you sign in with your User5 account and upload the AIP-protected document to the Documents folder of the Support site collection.</span></span>
  
1. <span data-ttu-id="b3d68-173">在 [ **Microsoft Office Home** ] 索引標籤中右上方，按一下 [使用者] 圖示及 [**登出**。</span><span class="sxs-lookup"><span data-stu-id="b3d68-173">On the **Microsoft Office Home** tab, in the upper right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="b3d68-174">移至[http://portal.office.com](http://portal.office.com)。</span><span class="sxs-lookup"><span data-stu-id="b3d68-174">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="b3d68-175">在 * * Office 365 登入 * *] 頁面上，按一下 User5 帳戶名稱及登入。</span><span class="sxs-lookup"><span data-stu-id="b3d68-175">On the ** Office 365 sign in** page, click the User5 account name and sign in.</span></span>
    
4. <span data-ttu-id="b3d68-176">在 [ **Microsoft Office Home** ] 索引標籤上按一下 [ **SharePoint > 支援網站集合**。</span><span class="sxs-lookup"><span data-stu-id="b3d68-176">On the **Microsoft Office Home** tab, click **SharePoint > Support site collection**.</span></span>
    
5. <span data-ttu-id="b3d68-177">按一下 [**文件**、 按一下 [**上載**]、 [ **AfterAIP**文件和 [**開啟**。</span><span class="sxs-lookup"><span data-stu-id="b3d68-177">Click **Documents**, click **Upload**, click the **AfterAIP** document, and then click **Open**.</span></span>
    
    <span data-ttu-id="b3d68-178">您應該會看到 [文件] 資料夾中的 AfterAIP.docx 支援網站集合中。</span><span class="sxs-lookup"><span data-stu-id="b3d68-178">You should see AfterAIP.docx in the Documents folder on the Support site collection.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="b3d68-179">請參閱</span><span class="sxs-lookup"><span data-stu-id="b3d68-179">See Also</span></span>

[<span data-ttu-id="b3d68-180">雲端採用測試實驗室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="b3d68-180">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="b3d68-181">Office 365 和 EMS 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="b3d68-181">Office 365 and EMS dev/test environment</span></span>](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[<span data-ttu-id="b3d68-182">Azure 的資訊保護</span><span class="sxs-lookup"><span data-stu-id="b3d68-182">Azure Information Protection</span></span>](https://www.microsoft.com/cloud-platform/azure-information-protection)


