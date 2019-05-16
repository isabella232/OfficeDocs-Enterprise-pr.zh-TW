---
title: Office 365 開發/測試環境中的資料分類和標示
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 919b8fc7-b0bc-46db-91f5-37342564e01b
description: 摘要： 設定並示範資料分類和標記您的 Office 365 開發/測試環境中使用 Azure 資訊保護 (AIP) 用戶端。
ms.openlocfilehash: cf369894eb87381e3837a52946a0ba2b9705bf70
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067930"
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a><span data-ttu-id="e9b17-103">Office 365 開發/測試環境中的資料分類和標示</span><span class="sxs-lookup"><span data-stu-id="e9b17-103">Data classification and labeling in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="e9b17-104">**摘要：** 設定並示範資料分類和標記您的 Office 365 開發/測試環境中使用 Azure 資訊保護 (AIP) 用戶端。</span><span class="sxs-lookup"><span data-stu-id="e9b17-104">**Summary:** Configure and demonstrate data classification and labeling using the Azure Information Protection (AIP) client in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="e9b17-105">Azure 資訊保護用戶端可讓您之前您將其上傳至 Office 365 中的 SharePoint Online 資料夾分類文件。</span><span class="sxs-lookup"><span data-stu-id="e9b17-105">The Azure Information Protection client lets you classify a document before you upload it to a SharePoint Online folder in Office 365.</span></span> <span data-ttu-id="e9b17-106">透過本文中的指示，您可以安裝 Azure 資訊保護用戶端，並示範資料分類。</span><span class="sxs-lookup"><span data-stu-id="e9b17-106">With the instructions in this article, you install the Azure Information Protection client and demonstrate data classification.</span></span> <span data-ttu-id="e9b17-107">如需詳細資訊，請參閱[Azure 資訊保護](https://www.microsoft.com/cloud-platform/azure-information-protection)。</span><span class="sxs-lookup"><span data-stu-id="e9b17-107">For more information, see [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection).</span></span>
  
> [!TIP]
> <span data-ttu-id="e9b17-108">按一下[這裡](http://aka.ms/catlgstack)，可查看 Office 365 測試實驗室指南堆疊中文章的所有視覺對應。</span><span class="sxs-lookup"><span data-stu-id="e9b17-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="e9b17-109">階段 1： 建置 Office 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="e9b17-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="e9b17-110">請遵循[Office 365 開發/測試環境](office-365-dev-test-environment.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="e9b17-110">Follow the instructions in [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a><span data-ttu-id="e9b17-111">階段 2： 新增 Azure 資訊保護試用版訂閱</span><span class="sxs-lookup"><span data-stu-id="e9b17-111">Phase 2: Add the Azure Information Protection trial subscription</span></span>

<span data-ttu-id="e9b17-112">在這個階段，您新增至您的 Office 365 開發/測試環境的 Azure 資訊保護，並啟用的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="e9b17-112">In this phase, you add Azure Information Protection to your Office 365 dev/test environment and enable it for your user accounts.</span></span> <span data-ttu-id="e9b17-113">如果您已設定的[Office 365 和 EMS 開發/測試環境](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)，請跳過這個階段中。</span><span class="sxs-lookup"><span data-stu-id="e9b17-113">If you have configured the [Office 365 and EMS dev/test environment](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), skip this phase.</span></span> <span data-ttu-id="e9b17-114">Enterprise Mobility Suite 試用版訂閱包含 Azure 資訊保護授權。</span><span class="sxs-lookup"><span data-stu-id="e9b17-114">The Enterprise Mobility Suite trial subscription includes Azure Information Protection licenses.</span></span>
  
<span data-ttu-id="e9b17-115">首先，登入 Azure 資訊保護試用訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="e9b17-115">First, sign up for an Azure Information Protection trial subscription.</span></span>
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a><span data-ttu-id="e9b17-116">Azure 資訊保護試用訂用帳戶註冊</span><span class="sxs-lookup"><span data-stu-id="e9b17-116">Sign up for an Azure Information Protection trial subscription</span></span>

1. <span data-ttu-id="e9b17-117">在 Internet Explorer 或您的瀏覽器中，移至[http://admin.microsoft.com](http://admin.microsoft.com)並以您的 Office 365 全域系統管理員帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="e9b17-117">In Internet Explorer or your browser, go to [http://admin.microsoft.com](http://admin.microsoft.com) and sign in with your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="e9b17-118">在**Microsoft Office 的首頁**] 索引標籤上，按一下 [**管理**] 磚。</span><span class="sxs-lookup"><span data-stu-id="e9b17-118">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="e9b17-119">在 Office 365 系統管理員] 索引標籤的 [在左側導覽中，按一下 [**帳單 > 購買服務**]。</span><span class="sxs-lookup"><span data-stu-id="e9b17-119">On the Office 365 Admin tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="e9b17-120">在 [**購買服務**] 頁面上，尋找 [ **Azure 資訊保護高階 P2**項目]。</span><span class="sxs-lookup"><span data-stu-id="e9b17-120">On the **Purchase services** page, find the **Azure Information Protection Premium P2** item.</span></span> <span data-ttu-id="e9b17-121">將滑鼠游標，然後按一下 [**開始免費試用版**。</span><span class="sxs-lookup"><span data-stu-id="e9b17-121">Hover your mouse over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="e9b17-122">在 [確認訂單]\*\*\*\* 頁面上，按一下 [立即試用]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e9b17-122">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="e9b17-123">在 [訂單收據]\*\*\*\* 頁面上，按一下 [繼續]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e9b17-123">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="e9b17-124">接下來，您可以啟用所有使用者帳戶的 Azure 資訊保護授權。</span><span class="sxs-lookup"><span data-stu-id="e9b17-124">Next, you enable the Azure Information Protection license for all user accounts.</span></span>
  
1. <span data-ttu-id="e9b17-125">在 Microsoft 365 系統管理中心] 索引標籤上按一下 [**使用者**]。</span><span class="sxs-lookup"><span data-stu-id="e9b17-125">On the Microsoft 365 admin center tab, click **Users**.</span></span>
    
2.  <span data-ttu-id="e9b17-126">在使用者帳戶的清單中，選取您的全域系統管理員帳戶，然後按一下**編輯\*\*\*\*產品**授權。</span><span class="sxs-lookup"><span data-stu-id="e9b17-126">In the list of user accounts, select your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="e9b17-127">開啟產品授權的**Azure 資訊保護高階 P2**到**上**按一下 [**儲存]** ，然後按兩次 [**關閉**。</span><span class="sxs-lookup"><span data-stu-id="e9b17-127">Turn the product license for **Azure Information Protection Premium P2** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="e9b17-128">針對其他使用者帳戶 (使用者 1 到使用者 5) 重複步驟 2 和 3。</span><span class="sxs-lookup"><span data-stu-id="e9b17-128">Repeat steps 2 and 3 for your other user accounts (User 1 through User 5).</span></span>
    
<span data-ttu-id="e9b17-129">Office 365 開發/測試環境現在擁有：</span><span class="sxs-lookup"><span data-stu-id="e9b17-129">Your Office 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="e9b17-130">Office 365 E5 Enterprise 和 Azure 資訊保護試用訂閱。</span><span class="sxs-lookup"><span data-stu-id="e9b17-130">Office 365 E5 Enterprise and Azure Information Protection trial subscriptions.</span></span>
    
- <span data-ttu-id="e9b17-131">您的所有使用者帳戶啟用，可使用 Office 365 E5 Enterprise 和 Azure 資訊保護。</span><span class="sxs-lookup"><span data-stu-id="e9b17-131">All of your user accounts enabled to use both Office 365 E5 Enterprise and Azure Information Protection.</span></span>
    
## <a name="phase-3-demonstrate-data-classification"></a><span data-ttu-id="e9b17-132">階段 3： 展示資料分類</span><span class="sxs-lookup"><span data-stu-id="e9b17-132">Phase 3: Demonstrate data classification</span></span>

<span data-ttu-id="e9b17-133">在這個階段，您會示範使用 Azure 資訊保護用戶端及預設的 Azure 資訊保護原則的資料分類。</span><span class="sxs-lookup"><span data-stu-id="e9b17-133">In this phase, you demonstrate data classification using the Azure Information Protection client and the default Azure Information Protection policy.</span></span>
  
<span data-ttu-id="e9b17-134">如果您使用模擬的企業 Office 365 開發/測試環境，您必須先在 CLIENT1 上安裝 Office 2016。</span><span class="sxs-lookup"><span data-stu-id="e9b17-134">If you are using the simulated enterprise Office 365 dev/test environment, you must first install Office 2016 on CLIENT1.</span></span>
  
1. <span data-ttu-id="e9b17-135">使用您的瀏覽器並移至[Azure 入口網站](http://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="e9b17-135">Use your browser and go to the [Azure portal](http://portal.azure.com).</span></span>
    
2. <span data-ttu-id="e9b17-136">按一下 [**資源群組 >** [您的資源群組名稱] **> CLIENT1 > 連線**]。</span><span class="sxs-lookup"><span data-stu-id="e9b17-136">Click **Resource Groups >** [your resource group name] **> CLIENT1 > Connect**.</span></span>
    
3. <span data-ttu-id="e9b17-137">從 CLIENT1，執行 [Internet Explorer，請移至 Office 入口網站，網址[http://admin.microsoft.com](http://admin.microsoft.com)，然後使用 User5 帳戶名稱和密碼登入。</span><span class="sxs-lookup"><span data-stu-id="e9b17-137">From CLIENT1, run Internet Explorer, go to the Office portal at [http://admin.microsoft.com](http://admin.microsoft.com), and then sign in with the User5 account name and password.</span></span>
    
4. <span data-ttu-id="e9b17-138">在 [Microsoft Office 首頁]\*\*\*\* 索引標籤上，按一下 [安裝 Office 2016]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e9b17-138">On the **Microsoft Office Home** tab, click **Install Office 2016**.</span></span>
    
5. <span data-ttu-id="e9b17-139">執行時出現提示，請按一下 [ **]** 時提示使用者帳戶控制下載。</span><span class="sxs-lookup"><span data-stu-id="e9b17-139">Run the download when prompted and click **Yes** when prompted by User Account Control.</span></span> <span data-ttu-id="e9b17-140">等待安裝 Office。</span><span class="sxs-lookup"><span data-stu-id="e9b17-140">Wait for Office to install.</span></span> <span data-ttu-id="e9b17-141">完成後，按一下 [**關閉**兩次。</span><span class="sxs-lookup"><span data-stu-id="e9b17-141">When complete, click **Close** twice.</span></span>
    
<span data-ttu-id="e9b17-142">接下來，您安裝 Azure 資訊保護用戶端。</span><span class="sxs-lookup"><span data-stu-id="e9b17-142">Next, you install the Azure Information Protection client.</span></span>
  
1. <span data-ttu-id="e9b17-143">在瀏覽器或 Internet Explorer 中，移至[Microsoft Azure 資訊保護下載頁面](https://www.microsoft.com/download/details.aspx?id=53018)。</span><span class="sxs-lookup"><span data-stu-id="e9b17-143">In your browser or Internet Explorer, go to the [Microsoft Azure Information Protection download page](https://www.microsoft.com/download/details.aspx?id=53018).</span></span>
    
  - <span data-ttu-id="e9b17-144">如果您使用 Office 365 開發/測試環境的輕量版本，請在本機電腦上使用瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="e9b17-144">If you are using the lightweight version of the Office 365 dev/test environment, use the browser on your local computer.</span></span>
    
  - <span data-ttu-id="e9b17-145">如果您使用模擬的企業 Office 365 開發/測試環境，請從 CLIENT1 執行 Internet Explorer。</span><span class="sxs-lookup"><span data-stu-id="e9b17-145">If you are using the simulated enterprise Office 365 dev/test environment, run Internet Explorer from CLIENT1.</span></span>
    
2. <span data-ttu-id="e9b17-146">在**Microsoft Azure 資訊保護**下載頁面上，按一下 [**下載**] 按一下 [ **AzInfoProtection.exe**，，然後按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="e9b17-146">On the **Microsoft Azure Information Protection** download page, click **Download**, click **AzInfoProtection.exe**, and then click **Next**.</span></span>
    
3. <span data-ttu-id="e9b17-147">出現提示時，執行 AzInfoProtection.exe。</span><span class="sxs-lookup"><span data-stu-id="e9b17-147">When prompted, run AzInfoProtection.exe.</span></span>
    
4. <span data-ttu-id="e9b17-148">在 [**安裝 Azure 資訊保護**用戶端中，按一下 [**我同意**]，然後按一下 **[是]** 時提示使用者帳戶控制。</span><span class="sxs-lookup"><span data-stu-id="e9b17-148">In the **Install the Azure Information Protection** client box, click **I agree**, and then click **Yes** when prompted by User Account Control.</span></span>
    
5. <span data-ttu-id="e9b17-149">在 [**成功**] 方塊中，按一下 [ **] [關閉。**</span><span class="sxs-lookup"><span data-stu-id="e9b17-149">In the **Completed successfully** box, click **Close.**</span></span>
    
<span data-ttu-id="e9b17-150">接下來，您會示範在文件分類。</span><span class="sxs-lookup"><span data-stu-id="e9b17-150">Next, you demonstrate document classification.</span></span>
  
1. <span data-ttu-id="e9b17-151">按一下 [在工作列上的 [ **Word** ] 圖示。</span><span class="sxs-lookup"><span data-stu-id="e9b17-151">Click the **Word** icon in the taskbar.</span></span>
    
2. <span data-ttu-id="e9b17-152">出現提示時，使用 User5 帳戶名稱和密碼登入。</span><span class="sxs-lookup"><span data-stu-id="e9b17-152">When prompted, sign in with the User5 account name and password.</span></span>
    
3. <span data-ttu-id="e9b17-153">如果您剛安裝 Office 2016 在 CLIENT1 中，在**第一件事第一個**方塊中，按一下 [**接受**]。</span><span class="sxs-lookup"><span data-stu-id="e9b17-153">If you just installed Office 2016 on CLIENT1, in the **First things first** box, click **Accept**.</span></span>
    
4. <span data-ttu-id="e9b17-154">按一下 [**空白文件**。</span><span class="sxs-lookup"><span data-stu-id="e9b17-154">Click **Blank document**.</span></span> 
    
    <span data-ttu-id="e9b17-155">請注意 [**保護**] 區段中的功能區上 [**首頁**] 索引標籤和文件分類的資料列。</span><span class="sxs-lookup"><span data-stu-id="e9b17-155">Note the **Protection** section of the ribbon on the **Home** tab and the row of document classifications.</span></span>
    
5. <span data-ttu-id="e9b17-156">在空白的文件中，輸入一些文字。</span><span class="sxs-lookup"><span data-stu-id="e9b17-156">In the blank document, type some text.</span></span>
    
6. <span data-ttu-id="e9b17-157">按一下 [**儲存檔案 >**，輸入名稱**BeforeAIP**，，然後按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="e9b17-157">Click **File > Save**, type the name **BeforeAIP**, and then click **OK**.</span></span> 
    
7. <span data-ttu-id="e9b17-158">在文件類別的列中，按一下向下箭號的**密碼**，，，然後按一下 [**所有公司**。</span><span class="sxs-lookup"><span data-stu-id="e9b17-158">In the row of document classes, click the down arrow for **Secret**, and then click **All Company**.</span></span>
    
8. <span data-ttu-id="e9b17-159">按一下 [**另存新檔的檔案 >**，輸入名稱**AfterAIP**，，然後按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="e9b17-159">Click **File > Save As**, type the name **AfterAIP**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="e9b17-160">在工作列上，按一下 [**檔案總管]** ，然後開啟 [**文件**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="e9b17-160">Click **File Explorer** in the taskbar, and then open the **Documents** folder.</span></span>
    
    <span data-ttu-id="e9b17-161">請注意**BeforeAIP**和**AfterAIP**文件的不同的檔案大小。</span><span class="sxs-lookup"><span data-stu-id="e9b17-161">Note the different file sizes of the **BeforeAIP** and **AfterAIP** documents.</span></span> <span data-ttu-id="e9b17-162">AfterAIP 文件是較大，因為它已分類資訊。</span><span class="sxs-lookup"><span data-stu-id="e9b17-162">The AfterAIP document is larger because it has the classification information.</span></span>
    
<span data-ttu-id="e9b17-163">接下來，您允許所有人都支援網站集合的存取。</span><span class="sxs-lookup"><span data-stu-id="e9b17-163">Next, you allow everyone to access the Support site collection.</span></span>
  
1. <span data-ttu-id="e9b17-164">在 [ **Microsoft Office 的首頁**] 索引標籤中，按一下 [ **SharePoint**]。</span><span class="sxs-lookup"><span data-stu-id="e9b17-164">On the **Microsoft Office Home** tab, click **SharePoint**.</span></span>
    
2. <span data-ttu-id="e9b17-165">從**SharePoint** ] 索引標籤上，按一下 [**支援網站集合**]。</span><span class="sxs-lookup"><span data-stu-id="e9b17-165">From the **SharePoint** tab, click **Support site collection**.</span></span>
    
3. <span data-ttu-id="e9b17-166">在右上方，按一下 [**設定**] 圖示，然後按一下**與共用]**。</span><span class="sxs-lookup"><span data-stu-id="e9b17-166">In the upper right, click the **Settings** icon, and then click **Shared with**.</span></span>
    
4. <span data-ttu-id="e9b17-167">在 [**共用 '支援網站集合]**，按一下 [**進階**]。</span><span class="sxs-lookup"><span data-stu-id="e9b17-167">In **Share 'Support site collection'**, click **Advanced**.</span></span>
    
5. <span data-ttu-id="e9b17-168">在 SharePoint 群組的清單中，按一下 [**支援網站集合的成員**。</span><span class="sxs-lookup"><span data-stu-id="e9b17-168">In the list of SharePoint groups, click **Support site collection Members**.</span></span>
    
6. <span data-ttu-id="e9b17-169">在 [人員與群組]\*\*\*\* 頁面上，按一下 [新增]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e9b17-169">On the **People and Groups** page, click **New**.</span></span>
    
7. <span data-ttu-id="e9b17-170">在 [**共用 '支援網站集合]**，輸入**所有人**，請按一下 [**外部使用者以外的所有人**，和 [**共用。**</span><span class="sxs-lookup"><span data-stu-id="e9b17-170">In **Share 'Support site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share.**</span></span>
    
8. <span data-ttu-id="e9b17-171">關閉 [**人員與群組**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e9b17-171">Close the **People and Groups** tab.</span></span>
    
<span data-ttu-id="e9b17-172">接下來，您使用 User5 帳戶登入，並將 AIP 受保護的文件上傳至支援網站集合的文件資料夾。</span><span class="sxs-lookup"><span data-stu-id="e9b17-172">Next, you sign in with your User5 account and upload the AIP-protected document to the Documents folder of the Support site collection.</span></span>
  
1. <span data-ttu-id="e9b17-173">在**Microsoft Office 的首頁**] 索引標籤右上方，按一下 [使用者] 圖示，然後按一下 [**登出]**。</span><span class="sxs-lookup"><span data-stu-id="e9b17-173">On the **Microsoft Office Home** tab, in the upper right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="e9b17-174">請移至 [http://admin.microsoft.com](http://admin.microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="e9b17-174">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="e9b17-175">在**Office 365 登入**頁面上，按一下 User5 帳戶名稱和登入。</span><span class="sxs-lookup"><span data-stu-id="e9b17-175">On the **Office 365 sign in** page, click the User5 account name and sign in.</span></span>
    
4. <span data-ttu-id="e9b17-176">在 [ **Microsoft Office 的首頁**] 索引標籤中，按一下 [ **SharePoint > 支援網站集合**。</span><span class="sxs-lookup"><span data-stu-id="e9b17-176">On the **Microsoft Office Home** tab, click **SharePoint > Support site collection**.</span></span>
    
5. <span data-ttu-id="e9b17-177">按一下 [**文件**，按一下 [**上傳**、 按一下**AfterAIP**文件，，然後按一下 [**開啟**。</span><span class="sxs-lookup"><span data-stu-id="e9b17-177">Click **Documents**, click **Upload**, click the **AfterAIP** document, and then click **Open**.</span></span>
    
    <span data-ttu-id="e9b17-178">您應該支援網站集合上看到 AfterAIP.docx Documents 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="e9b17-178">You should see AfterAIP.docx in the Documents folder on the Support site collection.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="e9b17-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9b17-179">See Also</span></span>

[<span data-ttu-id="e9b17-180">雲端採用測試實驗室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="e9b17-180">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="e9b17-181">Office 365 和 EMS 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="e9b17-181">Office 365 and EMS dev/test environment</span></span>](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[<span data-ttu-id="e9b17-182">Azure 資訊保護</span><span class="sxs-lookup"><span data-stu-id="e9b17-182">Azure Information Protection</span></span>](https://www.microsoft.com/cloud-platform/azure-information-protection)


