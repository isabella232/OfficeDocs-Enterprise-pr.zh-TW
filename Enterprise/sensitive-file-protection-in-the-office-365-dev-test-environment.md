---
title: Office 365 開發/測試環境中的機密檔案保護
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/01/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: 摘要： 設定並示範如何 Office 365 資訊版權管理保護機密檔案，即使公佈到錯誤的 SharePoint Online 網站集合。
ms.openlocfilehash: 4b65df7fe194d543acaf1c3ba6f104681a998dc6
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741299"
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a><span data-ttu-id="472ee-103">Office 365 開發/測試環境中的機密檔案保護</span><span class="sxs-lookup"><span data-stu-id="472ee-103">Sensitive file protection in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="472ee-104">**摘要：** 設定並示範如何 Office 365 資訊版權管理保護機密檔案，即使公佈到錯誤的 SharePoint Online 網站集合。</span><span class="sxs-lookup"><span data-stu-id="472ee-104">**Summary:** Configure and demonstrate how Office 365 Information Rights Management protects your sensitive files, even when they are posted to the wrong SharePoint Online site collection.</span></span>
  
<span data-ttu-id="472ee-105">資訊版權管理 (IRM) 設定 Office 365 是一組的功能來保護 SharePoint Online 文件庫和清單從下載的文件。</span><span class="sxs-lookup"><span data-stu-id="472ee-105">Information Rights Management (IRM) in Office 365 is a set of capabilities to protect documents that are downloaded from SharePoint Online libraries and lists.</span></span> <span data-ttu-id="472ee-106">下載的檔案加密儲存，包含開啟的複本，並列印反映 SharePoint Online 的文件庫中所儲存的權限。</span><span class="sxs-lookup"><span data-stu-id="472ee-106">Downloaded files are encrypted and contain the open, copy, save, and print permissions that reflect the SharePoint Online library in which they were stored.</span></span>
  
<span data-ttu-id="472ee-107">透過本文中的指示，您可以啟用並測試 Office 365 中的 IRM，包含可能在您的 Office 365 試用版訂閱中的敏感資訊的檔案。</span><span class="sxs-lookup"><span data-stu-id="472ee-107">With the instructions in this article, you enable and test IRM in Office 365 for files containing possible sensitive information in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="472ee-108">按一下[這裡](http://aka.ms/catlgstack)取得 Office 365 測試實驗室指南堆疊中所有文章的視覺對應。</span><span class="sxs-lookup"><span data-stu-id="472ee-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="472ee-109">階段 1： 建置 Office 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="472ee-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="472ee-110">如果您只想以具有最小需求的輕量型方式測試敏感性檔案保護，請遵循指示，以在階段 2 和 3 的[Office 365 開發/測試環境](office-365-dev-test-environment.md)中。</span><span class="sxs-lookup"><span data-stu-id="472ee-110">If you just want to test sensitive file protection in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="472ee-111">如果您想要在模擬的企業中測試敏感性檔案保護，請遵循[Office 365 開發/測試環境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="472ee-111">If you want to test sensitive file protection in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="472ee-112">測試敏感性檔案保護不需要模擬的企業版開發/測試環境，其中包含連線至網際網路的模擬內部網路和目錄同步處理 Active Directory 網域服務 (AD DS) 樹系中。</span><span class="sxs-lookup"><span data-stu-id="472ee-112">Testing sensitive file protection does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Active Directory Domain Services (AD DS) forest.</span></span> <span data-ttu-id="472ee-113">它提供了此選項，讓您可以測試敏感性檔案保護與代表典型組織的環境中實驗。</span><span class="sxs-lookup"><span data-stu-id="472ee-113">It is provided here as an option so that you can test sensitive file protection and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a><span data-ttu-id="472ee-114">階段 2： 展示如何可以遺漏文件中的權限受保護的網站</span><span class="sxs-lookup"><span data-stu-id="472ee-114">Phase 2: Demonstrate how documents from permissions-protected sites can be leaked</span></span>

<span data-ttu-id="472ee-115">在這個階段，您會示範某人可以用來從權限保護的網站下載文件，並再將其上傳至網站，具有廣泛開放的權限。</span><span class="sxs-lookup"><span data-stu-id="472ee-115">In this phase, you demonstrate that someone can download a document from a permissions-protected site and then upload it to a site that has wide-open permissions.</span></span>
  
<span data-ttu-id="472ee-116">首先，您會新增三個新的使用者帳戶代表主管和對其指派 Office 365 E5 授權。</span><span class="sxs-lookup"><span data-stu-id="472ee-116">First, you add three new user accounts that represent executives and assign them Office 365 E5 licenses.</span></span>
  
<span data-ttu-id="472ee-117">使用[連線到 Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx)中的指示，安裝 PowerShell 模組 （如果需要），並連線至您從新的 Office 365 訂閱：</span><span class="sxs-lookup"><span data-stu-id="472ee-117">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules (if needed) and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="472ee-118">您的電腦 (適用於輕量型 Office 365 開發/測試環境)。</span><span class="sxs-lookup"><span data-stu-id="472ee-118">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="472ee-119">CLIENT1 虛擬機器 (適用於模擬的企業 Office 365 開發/測試環境)。</span><span class="sxs-lookup"><span data-stu-id="472ee-119">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
<span data-ttu-id="472ee-120">在 [ **Windows PowerShell 認證要求**] 對話方塊中，輸入 Office 365 全域系統管理員名稱 (範例： jdoe@contosotoycompany.onmicrosoft.com) 和 Office 365 試用版訂閱的密碼。</span><span class="sxs-lookup"><span data-stu-id="472ee-120">In the **Windows PowerShell Credential Request** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password of your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="472ee-121">填入您的組織名稱 (範例： contosotoycompany) 和兩個字元國家/地區適用於您位置中，程式碼，然後在 Windows Azure Active Directory 模組的 Windows PowerShell 提示字元執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="472ee-121">Fill in your organization name (example: contosotoycompany) and the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="472ee-122">從**New-msoluser**命令的顯示畫面，請注意 CEO 帳戶產生的密碼並且將密碼記錄在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="472ee-122">From the display of the **New-MsolUser** command, note the generated password for the CEO account and record it in a safe location.</span></span>
  
<span data-ttu-id="472ee-123">從適用於 Windows PowerShell 的 Windows Azure Active Directory 模組提示字元中執行下列命令︰</span><span class="sxs-lookup"><span data-stu-id="472ee-123">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="472ee-124">從**New-msoluser**命令的顯示畫面，請注意 CFO 帳戶產生的密碼並且將密碼記錄在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="472ee-124">From the display of the **New-MsolUser** command, note the generated password for the CFO account and record it in a safe location.</span></span>
  
<span data-ttu-id="472ee-125">從適用於 Windows PowerShell 的 Windows Azure Active Directory 模組提示字元中執行下列命令︰</span><span class="sxs-lookup"><span data-stu-id="472ee-125">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="472ee-126">從**New-msoluser**命令的顯示畫面，請注意 COO 帳戶產生的密碼並且將密碼記錄在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="472ee-126">From the display of the **New-MsolUser** command, note the generated password for the COO account and record it in a safe location.</span></span>
  
<span data-ttu-id="472ee-127">接下來，您建立私人的主管群組，並將新的高階主管帳戶新增至它。</span><span class="sxs-lookup"><span data-stu-id="472ee-127">Next, you create a private Executives group and add the new executive accounts to it.</span></span>
  
1. <span data-ttu-id="472ee-128">在瀏覽器中，移至 Office 入口網站，網址[http://admin.microsoft.com](http://admin.microsoft.com)並登入 Office 365 試用訂閱以全域管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="472ee-128">In your browser, go to the Office portal at [http://admin.microsoft.com](http://admin.microsoft.com) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="472ee-129">如果您使用輕量型 Office 365 開發/測試環境，開啟 Internet Explorer 或您的瀏覽器的私人工作階段，並從您本機電腦登入。</span><span class="sxs-lookup"><span data-stu-id="472ee-129">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer or your browser and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="472ee-130">如果您使用模擬的企業 Office 365 開發/測試環境，使用 Azure 入口網站連線至 CLIENT1 虛擬機器，然後從 CLIENT1 登入。</span><span class="sxs-lookup"><span data-stu-id="472ee-130">If you are using the simulated enterprise Office 365 dev/test environment, use the Azure portal to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="472ee-131">在 [ **Microsoft Office 的首頁**] 索引標籤中，按一下 [**系統 > 群組 > 群組**，然後按一下 [**新增群組**。</span><span class="sxs-lookup"><span data-stu-id="472ee-131">On the **Microsoft Office Home** tab, click **Admin > Groups > Groups**, and then click **Add a group**.</span></span>
    
3. <span data-ttu-id="472ee-132">在**加入群組**]，選取**Office 365 群組**的群組類型、 輸入**主管**[**名稱**] 及 [**群組識別碼**，選取 [**私用\*\*\*\*的隱私權**、，然後按一下 [**選取擁有者**。</span><span class="sxs-lookup"><span data-stu-id="472ee-132">In **Add a group**, select **Office 365 group** for the group type, type **Executives** in **Name** and **Group Id**, select **Private** for **Privacy**, and then click **Select Owner**.</span></span>
    
4. <span data-ttu-id="472ee-133">在清單中，按一下 [您的全域系統管理員帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="472ee-133">In the list, click your global administrator account name.</span></span>
    
5. <span data-ttu-id="472ee-134">Click **Add**, and then click **Close**.</span><span class="sxs-lookup"><span data-stu-id="472ee-134">Click **Add**, and then click **Close**.</span></span>
    
6. <span data-ttu-id="472ee-135">在 [群組] 清單中，按一下 [**主管**]。</span><span class="sxs-lookup"><span data-stu-id="472ee-135">In the groups list, click **Executives**.</span></span>
    
7. <span data-ttu-id="472ee-136">按一下 [**編輯成員**]。</span><span class="sxs-lookup"><span data-stu-id="472ee-136">Click **Edit for Members**.</span></span>
    
8. <span data-ttu-id="472ee-137">按一下 [新增成員]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="472ee-137">Click **Add members**.</span></span> <span data-ttu-id="472ee-138">在 [成員] 清單中，選取下列使用者帳戶：</span><span class="sxs-lookup"><span data-stu-id="472ee-138">In the member list, select the following user accounts:</span></span>
    
  - <span data-ttu-id="472ee-139">執行長</span><span class="sxs-lookup"><span data-stu-id="472ee-139">Chief Executive Officer</span></span>
    
  - <span data-ttu-id="472ee-140">主要的財務長</span><span class="sxs-lookup"><span data-stu-id="472ee-140">Chief Financial Officer</span></span>
    
  - <span data-ttu-id="472ee-141">首席作業長</span><span class="sxs-lookup"><span data-stu-id="472ee-141">Chief Operations Officer</span></span>
    
9. <span data-ttu-id="472ee-142">按一下 [**儲存**]，然後按一下 [**關閉**]。</span><span class="sxs-lookup"><span data-stu-id="472ee-142">Click **Save**, and then click **Close**.</span></span>
    
10. <span data-ttu-id="472ee-143">關閉 [ **Office 系統管理中心**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="472ee-143">Close the **Office Admin center** tab.</span></span>
    
<span data-ttu-id="472ee-144">接下來，建立主管網站集合，並允許只對其進行存取的主管群組的成員。</span><span class="sxs-lookup"><span data-stu-id="472ee-144">Next, you create an Executives site collection and allow just the members of the Executives group to access it.</span></span>
  
1. <span data-ttu-id="472ee-145">在**Microsoft Office 的首頁**] 索引標籤上，按一下 [**管理**] 磚。</span><span class="sxs-lookup"><span data-stu-id="472ee-145">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="472ee-146">在 [ **Office 系統管理中心**] 索引標籤中，按一下 [**系統管理中心 > SharePoint**。</span><span class="sxs-lookup"><span data-stu-id="472ee-146">On the **Office Admin center** tab, click **Admin centers > SharePoint**.</span></span>
    
3. <span data-ttu-id="472ee-147">在**SharePoint 系統管理中心**] 索引標籤上，按一下 [**新 > 私用網站集合**。</span><span class="sxs-lookup"><span data-stu-id="472ee-147">On the **SharePoint admin center** tab, click **New > Private site collection**.</span></span>
    
4. <span data-ttu-id="472ee-148">在 [新網站集合] 窗格中，**標題**，主管在 [URL] 方塊中輸入**高階主管**指定的全域管理員帳戶名稱在**系統管理員**，，然後按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="472ee-148">In the new site collection pane, type **Executives** in **Title**, executives in the URL box, specify the name of your global administrator account in **Administrator**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="472ee-149">請稍候，直到已建立新的網站集合。</span><span class="sxs-lookup"><span data-stu-id="472ee-149">Wait until the new site collection has been created.</span></span> <span data-ttu-id="472ee-150">完成時，複製新主管網站集合的 URL，並將它貼到您的瀏覽器的新索引標籤。</span><span class="sxs-lookup"><span data-stu-id="472ee-150">When complete, copy the URL of the new Executives site collection and paste it into a new tab of your browser.</span></span>
    
6. <span data-ttu-id="472ee-151">在右上角的**主管**網站集合中，按一下 [設定] 圖示，然後按一下**與共用]**。</span><span class="sxs-lookup"><span data-stu-id="472ee-151">In the upper right of the **Executives** site collection, click the settings icon, and then click **Shared with**.</span></span>
    
7. <span data-ttu-id="472ee-152">在 [**共用 '高階主管]**，按一下 [**進階**]。</span><span class="sxs-lookup"><span data-stu-id="472ee-152">In **Share 'Executives'**, click **Advanced**.</span></span>
    
8. <span data-ttu-id="472ee-153">在 SharePoint 群組的清單中，按一下 [**高階主管成員**。</span><span class="sxs-lookup"><span data-stu-id="472ee-153">In the list of SharePoint groups, click **Executives Members**.</span></span>
    
9. <span data-ttu-id="472ee-154">在 [人員與群組]\*\*\*\* 頁面上，按一下 [新增]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="472ee-154">On the **People and Groups** page, click **New**.</span></span>
    
10. <span data-ttu-id="472ee-155">在 [**共用 '高階主管]**，輸入**高階主管**，按一下 [**主管**] 群組中，，然後按一下**共用**。</span><span class="sxs-lookup"><span data-stu-id="472ee-155">In **Share 'Executives'**, type **Executives**, click the **Executives** group, and then click **Share**.</span></span>
    
11. <span data-ttu-id="472ee-156">關閉 [**人員與群組**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="472ee-156">Close the **People and groups** tab.</span></span>
    
<span data-ttu-id="472ee-157">接下來，您允許所有人存取業務部網站集合。</span><span class="sxs-lookup"><span data-stu-id="472ee-157">Next, you allow everyone to access the Sales site collection.</span></span>
  
1. <span data-ttu-id="472ee-158">從**SharePoint 系統管理中心**] 索引標籤上，複製業務部網站集合的 URL，並將它貼到您的瀏覽器的新索引標籤..</span><span class="sxs-lookup"><span data-stu-id="472ee-158">From the **SharePoint admin center** tab, copy the URL of the Sales site collection and paste it into a new tab of your browser..</span></span>
    
2. <span data-ttu-id="472ee-159">在右上方，按一下 [設定] 圖示，然後按一下**與共用]**。</span><span class="sxs-lookup"><span data-stu-id="472ee-159">In the upper right, click the settings icon, and then click **Shared with**.</span></span>
    
3. <span data-ttu-id="472ee-160">在 [**共用 '業務部網站集合]**，按一下 [**進階**]。</span><span class="sxs-lookup"><span data-stu-id="472ee-160">In **Share 'Sales site collection'**, click **Advanced**.</span></span>
    
4. <span data-ttu-id="472ee-161">在 SharePoint 群組的清單中，按一下 [**銷售網站集合的成員**。</span><span class="sxs-lookup"><span data-stu-id="472ee-161">In the list of SharePoint groups, click **Sales site collection Members**.</span></span>
    
5. <span data-ttu-id="472ee-162">在 [人員與群組]\*\*\*\* 頁面上，按一下 [新增]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="472ee-162">On the **People and Groups** page, click **New**.</span></span>
    
6. <span data-ttu-id="472ee-163">在**共用 '業務部網站集合]**，輸入**Everyone**、 按一下 [**外部使用者以外的所有人**，，然後按一下 [**共用**。</span><span class="sxs-lookup"><span data-stu-id="472ee-163">In **Share 'Sales site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share**.</span></span>
    
7. <span data-ttu-id="472ee-164">關閉 [**銷售網站集合**和**SharePoint**索引標籤。</span><span class="sxs-lookup"><span data-stu-id="472ee-164">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="472ee-165">接下來，您使用高階主管的帳戶登入和主管網站集合中建立文件。</span><span class="sxs-lookup"><span data-stu-id="472ee-165">Next, you sign in with an executive account and create a document in the Executives site collection.</span></span>
  
1. <span data-ttu-id="472ee-166">在 [ **Microsoft Office 的首頁**] 索引標籤中，按一下右上角的使用者圖示，然後按一下 [**登出]**。</span><span class="sxs-lookup"><span data-stu-id="472ee-166">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="472ee-167">請移至 [http://admin.microsoft.com](http://admin.microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="472ee-167">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="472ee-168">在**Office 365 登入**] 頁面上，按一下 [**使用另一個帳戶**。</span><span class="sxs-lookup"><span data-stu-id="472ee-168">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="472ee-169">輸入**CEO**帳戶名稱和密碼，然後再按一下 [**登入**。</span><span class="sxs-lookup"><span data-stu-id="472ee-169">Type the **CEO** account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="472ee-170">在瀏覽器的新索引標籤上，輸入 [高階主管的網站集合的 URL ( **https://**\<組織 name>**.sharepoint.com/sites/executives**)。</span><span class="sxs-lookup"><span data-stu-id="472ee-170">On a new tab of your browser, type the URL to the Executives site collection ( **https://**\<organization name>**.sharepoint.com/sites/executives**).</span></span>
    
6. <span data-ttu-id="472ee-171">按一下 [**文件**，按一下 [**新增]** ，然後按一下 [ **Word 文件**。</span><span class="sxs-lookup"><span data-stu-id="472ee-171">Click **Documents**, click **New,** and then click **Word Document**.</span></span>
    
7. <span data-ttu-id="472ee-172">按一下標題列中，輸入**SensitiveData BeforeIRM**。</span><span class="sxs-lookup"><span data-stu-id="472ee-172">Click in the title bar and type **SensitiveData-BeforeIRM**.</span></span>
    
8. <span data-ttu-id="472ee-173">按一下 [文件內文中並輸入**從最新協調會議的分鐘**，，然後按一下 [**主管**。</span><span class="sxs-lookup"><span data-stu-id="472ee-173">Click in the document body and type **Minutes from the latest board meeting**, and then click **Executives**.</span></span>
    
     <span data-ttu-id="472ee-174">您應該會看到**SensitiveData BeforeIRM.docx** **Documents**資料夾中。</span><span class="sxs-lookup"><span data-stu-id="472ee-174">You should see **SensitiveData-BeforeIRM.docx** in the **Documents** folder.</span></span>
    
<span data-ttu-id="472ee-175">接下來，您下載 SensitiveData BeforeIRM.docx 文件的本機複本，並再不小心張貼至業務部網站集合。</span><span class="sxs-lookup"><span data-stu-id="472ee-175">Next, you download a local copy of the SensitiveData-BeforeIRM.docx document and then accidentally post it to the Sales site collection.</span></span>
  
1. <span data-ttu-id="472ee-176">在您的本機電腦上建立新的資料夾 (例如 c:\\Tlg\\SensitiveDataTestFiles)。</span><span class="sxs-lookup"><span data-stu-id="472ee-176">On your local computer, create a new folder (for example, C:\\TLGs\\SensitiveDataTestFiles).</span></span>
    
2. <span data-ttu-id="472ee-177">在瀏覽器的 [**文件**] 索引標籤中，選取**SensitiveData BeforeIRM.docx**文件，請按一下省略符號，和 [**下載**。</span><span class="sxs-lookup"><span data-stu-id="472ee-177">On the **Documents** tab of your browser, select the **SensitiveData-BeforeIRM.docx** document, click the ellipses, and then click **Download**.</span></span>
    
3. <span data-ttu-id="472ee-178">**SensitiveData BeforeIRM.docx**文件儲存在步驟 1 中建立的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="472ee-178">Store the **SensitiveData-BeforeIRM.docx** document in the folder created in step 1.</span></span>
    
4. <span data-ttu-id="472ee-179">在瀏覽器的新索引標籤上，輸入 [業務部網站集合的 URL ( **https://**\<組織 name>**.sharepoint.com/sites/sales**)。</span><span class="sxs-lookup"><span data-stu-id="472ee-179">On a new tab of your browser, type the URL to the Sales site collection ( **https://**\<organization name>**.sharepoint.com/sites/sales**).</span></span>
    
5. <span data-ttu-id="472ee-180">按一下 [**銷售網站集合**的**文件**資料夾。</span><span class="sxs-lookup"><span data-stu-id="472ee-180">Click the **Documents** folder of the **Sales site collection**.</span></span>
    
6. <span data-ttu-id="472ee-181">按一下 [**上傳**，並再指定在步驟 1 所建立的資料夾中的 [ **SensitiveData BeforeIRM.docx**文件，然後按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="472ee-181">Click **Upload**, and then specify **SensitiveData-BeforeIRM.docx** document in the folder created in step 1, and then click **OK**.</span></span>
    
7. <span data-ttu-id="472ee-182">確認**SensitiveData BeforeIRM.docx**文件中的**文件**資料夾。</span><span class="sxs-lookup"><span data-stu-id="472ee-182">Verify that the **SensitiveData-BeforeIRM.docx** document is in the **Documents** folder.</span></span>
    
8. <span data-ttu-id="472ee-183">關閉 [**銷售**及**SharePoint**索引標籤。</span><span class="sxs-lookup"><span data-stu-id="472ee-183">Close the **Sales** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="472ee-184">接下來，您 User5 身分，登入，並嘗試開啟 SensitiveData BeforeIRM.docx 該文件業務部網站集合。</span><span class="sxs-lookup"><span data-stu-id="472ee-184">Next, you sign in as User5 and try to open the SensitiveData-BeforeIRM.docx document in the Sales site collection.</span></span>
  
1. <span data-ttu-id="472ee-185">在 [ **Microsoft Office 的首頁**] 索引標籤中，按一下右上角的使用者圖示，然後按一下 [**登出]**。</span><span class="sxs-lookup"><span data-stu-id="472ee-185">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="472ee-186">請移至 [http://admin.microsoft.com](http://admin.microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="472ee-186">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="472ee-187">在**Office 365 登入**] 頁面上，按一下 [**使用另一個帳戶**。</span><span class="sxs-lookup"><span data-stu-id="472ee-187">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="472ee-188">輸入 User5 帳戶名稱和密碼，然後再按一下 [**登入**。</span><span class="sxs-lookup"><span data-stu-id="472ee-188">Type the User5 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="472ee-189">在瀏覽器的新索引標籤上，輸入業務部網站集合的 URL。</span><span class="sxs-lookup"><span data-stu-id="472ee-189">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
6. <span data-ttu-id="472ee-190">在 [**銷售網站集合**的**文件**資料夾，按一下 [ **SensitiveData BeforeIRM.docx**文件。</span><span class="sxs-lookup"><span data-stu-id="472ee-190">In the **Documents** folder of the **Sales site collection**, click the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
    <span data-ttu-id="472ee-191">您應該會看到其內容。</span><span class="sxs-lookup"><span data-stu-id="472ee-191">You should see its contents.</span></span>
    
7. <span data-ttu-id="472ee-192">關閉**文件**和**銷售網站集合**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="472ee-192">Close the **Documents** and **Sales site collection** tabs.</span></span>
    
<span data-ttu-id="472ee-193">藉由不小心張貼 SensitiveData BeforeIRM.docx 文件上業務部網站集合，CEO 略過主管網站集合的權限安全性。</span><span class="sxs-lookup"><span data-stu-id="472ee-193">By accidentally posting the SensitiveData-BeforeIRM.docx document on the Sales site collection, the CEO bypassed the permissions security of the Executives site collection.</span></span>
  
<span data-ttu-id="472ee-194">若要準備階段 3 和 4 的 Office 365，請針對 SharePoint Online 中啟用 IRM。</span><span class="sxs-lookup"><span data-stu-id="472ee-194">To prepare Office 365 for Phases 3 and 4, enable IRM for SharePoint Online.</span></span>
  
1. <span data-ttu-id="472ee-195">在 [ **Microsoft Office 的首頁**] 索引標籤中，按一下右上角的使用者圖示，然後按一下 [**登出]**。</span><span class="sxs-lookup"><span data-stu-id="472ee-195">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="472ee-196">請移至 [http://admin.microsoft.com](http://admin.microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="472ee-196">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="472ee-197">在**Office 365 登入**頁面上，按一下 [全域管理員帳戶名稱，輸入其密碼，然後按一下 [**登入**。</span><span class="sxs-lookup"><span data-stu-id="472ee-197">On the **Office 365 sign in** page, click the global administrator account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="472ee-198">在 [ **Microsoft Office 的首頁**] 索引標籤中，按一下 [**系統 > 系統管理員中心 > SharePoint**。</span><span class="sxs-lookup"><span data-stu-id="472ee-198">On the **Microsoft Office Home** tab, click **Admin > Admin centers > SharePoint**.</span></span>
    
5. <span data-ttu-id="472ee-199">在**SharePoint 系統管理中心**] 索引標籤上，按一下 [**設定**]。</span><span class="sxs-lookup"><span data-stu-id="472ee-199">On the **SharePoint admin center** tab, click **Settings**.</span></span>
    
6. <span data-ttu-id="472ee-200">在頁面上，在 [**資訊版權管理 (IRM)** ] 區段中，選取 [**使用在您的組態中指定的 IRM 服務**]，然後選取 [**重新整理 IRM 設定**。</span><span class="sxs-lookup"><span data-stu-id="472ee-200">On the page, in the **Information Rights Management (IRM)** section, select **Use the IRM service specified in your configuration**, and then select **Refresh IRM Settings**.</span></span>
    
7. <span data-ttu-id="472ee-201">關閉 [ **SharePoint 系統管理中心**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="472ee-201">Close the **SharePoint admin center** tab.</span></span>
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a><span data-ttu-id="472ee-202">階段 3： 使用 SharePoint 資訊版權管理與 Office 365 私人群組</span><span class="sxs-lookup"><span data-stu-id="472ee-202">Phase 3: Use SharePoint Information Rights Management with an Office 365 private group</span></span>

<span data-ttu-id="472ee-203">在這個階段，您使用 SharePoint 資訊版權管理與 Office 365 私人群組保護敏感資訊，與文件存取的即使它開啟的權限與網站上張貼。</span><span class="sxs-lookup"><span data-stu-id="472ee-203">In this phase, you use SharePoint Information Rights Management with an Office 365 private group to protect access to a document with sensitive information, even when it is posted on a site with open permissions.</span></span>
  
<span data-ttu-id="472ee-204">首先，您會啟用，並將 IRM 設定主管網站集合的文件庫。</span><span class="sxs-lookup"><span data-stu-id="472ee-204">First, you enable and configure IRM for the documents library of the Executives site collection.</span></span> 
  
1. <span data-ttu-id="472ee-205">在瀏覽器的新索引標籤上，輸入高階主管的網站集合的 URL。</span><span class="sxs-lookup"><span data-stu-id="472ee-205">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
2. <span data-ttu-id="472ee-206">按一下 [文件]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="472ee-206">Click **Documents**.</span></span>
    
3. <span data-ttu-id="472ee-207">在右上角，按一下 [設定] 圖示，然後按一下**文件庫設定**。</span><span class="sxs-lookup"><span data-stu-id="472ee-207">In the upper-right, click the settings icon, and then click **Library settings**.</span></span>
    
4. <span data-ttu-id="472ee-208">在 [**設定**] 頁面上的**權限與管理**] 下按一下 [**資訊版權管理**]。</span><span class="sxs-lookup"><span data-stu-id="472ee-208">On the **Settings** page, under **Permissions and Management**, click **Information Rights Management**.</span></span>
    
5. <span data-ttu-id="472ee-209">在 [**資訊版權管理設定**] 頁面上：</span><span class="sxs-lookup"><span data-stu-id="472ee-209">On the **Information Rights Management Settings** page:</span></span>
    
  - <span data-ttu-id="472ee-210">選取 [**限制下載此文件庫中的文件的權限**]。</span><span class="sxs-lookup"><span data-stu-id="472ee-210">Select **Restrict permission to documents in this library on download**.</span></span>
    
  - <span data-ttu-id="472ee-211">**建立權限原則標題**]，輸入 [**主管**]。</span><span class="sxs-lookup"><span data-stu-id="472ee-211">For **Create a permission policy title**, type **Executives**.</span></span>
    
  - <span data-ttu-id="472ee-212">[**新增權限原則描述**] 中，輸入**高階主管的 IRM**。</span><span class="sxs-lookup"><span data-stu-id="472ee-212">For **Add a permission policy description**, type **IRM for executives**.</span></span>
    
6. <span data-ttu-id="472ee-213">按一下 [顯示選項]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="472ee-213">Click **Show Options**.</span></span>
    
7. <span data-ttu-id="472ee-214">**設定其他 IRM 文件庫設定**] 下選取 [**不允許使用者上傳文件，並不支援 IRM**。</span><span class="sxs-lookup"><span data-stu-id="472ee-214">Under **Set additional IRM library settings**, select **Do not allow users to upload documents that do not support IRM**.</span></span>
    
8. <span data-ttu-id="472ee-215">[**設定文件的存取權限**，選取**要列印的允許檢視**和**寫入在下載文件的複本上的允許檢視**。</span><span class="sxs-lookup"><span data-stu-id="472ee-215">Under **Configure document access rights**, select **Allow viewers to print** and **Allow viewers to write on a copy of the downloaded document**.</span></span>
    
9. <span data-ttu-id="472ee-216">**設定群組保護和認證間隔**] 下選取 [**允許群組保護]。預設群組**，然後輸入**高階主管**。</span><span class="sxs-lookup"><span data-stu-id="472ee-216">Under **Set group protection and credentials interval**, select **Allow group protection. Default group**, and then type **Executives**.</span></span>
    
10. <span data-ttu-id="472ee-217">按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="472ee-217">Click **OK**.</span></span>
    
<span data-ttu-id="472ee-218">接下來，做為 CEO，您將新的文件上傳至行政人員文件資料夾，下載，然後不小心將其上傳到銷售文件資料夾。</span><span class="sxs-lookup"><span data-stu-id="472ee-218">Next, acting as the CEO, you upload a new document to the Executives document folder, download it, then accidentally upload it to the Sales document folder.</span></span>
  
1. <span data-ttu-id="472ee-219">開啟您儲存**SensitiveData BeforeIRM.docx**文件的本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="472ee-219">Open the local folder where you stored the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
2. <span data-ttu-id="472ee-220">**SensitiveData BeforeIRM.docx**，以滑鼠右鍵按一下，然後按一下 [**複製]**。</span><span class="sxs-lookup"><span data-stu-id="472ee-220">Right-click **SensitiveData-BeforeIRM.docx**, and then click **Copy**.</span></span>
    
3. <span data-ttu-id="472ee-221">在資料夾中，以滑鼠右鍵按一下，然後按一下 [**貼**。</span><span class="sxs-lookup"><span data-stu-id="472ee-221">Right-click within the folder, and then click **Paste**.</span></span>
    
4. <span data-ttu-id="472ee-222">新的**SensitiveData-BeforeIRM-Copy.docx**檔案重新命名為**SensitiveData AfterIRM.docx**。</span><span class="sxs-lookup"><span data-stu-id="472ee-222">Rename the new **SensitiveData-BeforeIRM - Copy.docx** file to **SensitiveData-AfterIRM.docx**.</span></span>
    
5. <span data-ttu-id="472ee-223">從瀏覽器的 [ **Microsoft Office 的首頁**] 索引標籤按一下右上角的使用者圖示，然後按一下 [**登出]**。</span><span class="sxs-lookup"><span data-stu-id="472ee-223">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
6. <span data-ttu-id="472ee-224">請移至 [http://admin.microsoft.com](http://admin.microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="472ee-224">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
7. <span data-ttu-id="472ee-225">在**Office 365 登入**頁面上，按一下 [CEO 帳戶名稱，輸入其密碼，然後按一下 [**登入**。</span><span class="sxs-lookup"><span data-stu-id="472ee-225">On the **Office 365 sign in** page, click the CEO account name, type its password, and then click **Sign in**.</span></span>
    
8. <span data-ttu-id="472ee-226">在瀏覽器的新索引標籤上，輸入高階主管的網站集合的 URL。</span><span class="sxs-lookup"><span data-stu-id="472ee-226">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
9. <span data-ttu-id="472ee-227">在 [**文件**] 頁面上，按一下 [**上傳**、 指定**SensitiveData AfterIRM.docx**文件在本機資料夾中，，然後按一下 [**開啟**。</span><span class="sxs-lookup"><span data-stu-id="472ee-227">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
10. <span data-ttu-id="472ee-228">選取新**SensitiveData AfterIRM.docx**文件中**的文件**] 頁面上，按一下 [功能表列中的省略符號 （...），然後按一下 [**下載**。</span><span class="sxs-lookup"><span data-stu-id="472ee-228">Select the new **SensitiveData-AfterIRM.docx** document in the **Documents** page, click the ellipsis (…) in the menu bar, and then click **Download**.</span></span>
    
11. <span data-ttu-id="472ee-229">出現提示時，將**SensitiveData AfterIRM.docx**文件儲存您的本機資料夾，並覆寫原始版本。</span><span class="sxs-lookup"><span data-stu-id="472ee-229">When prompted, save the **SensitiveData-AfterIRM.docx** document in your local folder, overwriting the original version.</span></span>
    
12. <span data-ttu-id="472ee-230">關閉 [**文件**] 頁面上的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="472ee-230">Close the tab for the **Documents** page.</span></span>
    
13. <span data-ttu-id="472ee-231">在瀏覽器的新索引標籤上，輸入業務部網站集合的 URL。</span><span class="sxs-lookup"><span data-stu-id="472ee-231">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
14. <span data-ttu-id="472ee-232">按一下 [文件]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="472ee-232">Click **Documents**.</span></span>
    
15. <span data-ttu-id="472ee-233">在 [**文件**] 頁面上，按一下 [**上傳**、 指定**SensitiveData AfterIRM.docx**文件在本機資料夾中，，然後按一下 [**開啟**。</span><span class="sxs-lookup"><span data-stu-id="472ee-233">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
16. <span data-ttu-id="472ee-234">關閉 [**銷售網站集合**和**SharePoint**索引標籤。</span><span class="sxs-lookup"><span data-stu-id="472ee-234">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="472ee-235">接下來，做為一般使用者，您嘗試存取**SensitiveData AfterIRM.docx**文件中的銷售文件資料夾。</span><span class="sxs-lookup"><span data-stu-id="472ee-235">Next, acting as a normal user, you try to access the **SensitiveData-AfterIRM.docx** document in the Sales document folder.</span></span>
  
1. <span data-ttu-id="472ee-236">從瀏覽器的 [ **Microsoft Office 的首頁**] 索引標籤按一下右上角的使用者圖示，然後按一下 [**登出]**。</span><span class="sxs-lookup"><span data-stu-id="472ee-236">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="472ee-237">請移至 [http://admin.microsoft.com](http://admin.microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="472ee-237">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="472ee-238">在**Office 365 登入**頁面上，按一下 [User5 帳戶名稱，輸入其密碼，然後按一下 [**登入**。</span><span class="sxs-lookup"><span data-stu-id="472ee-238">On the **Office 365 sign in** page, click the User5 account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="472ee-239">在瀏覽器的新索引標籤上，輸入業務部網站集合的 URL。</span><span class="sxs-lookup"><span data-stu-id="472ee-239">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
5. <span data-ttu-id="472ee-240">按一下 [文件]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="472ee-240">Click **Documents**.</span></span>
    
6. <span data-ttu-id="472ee-241">在 [**文件**] 頁面上，開啟**SensitiveData AfterIRM.docx**文件。</span><span class="sxs-lookup"><span data-stu-id="472ee-241">On the **Documents** page, open the **SensitiveData-AfterIRM.docx** document.</span></span>
    
    <span data-ttu-id="472ee-242">您應該會看到訊息指出 「 很抱歉，Word Online 無法開啟這份文件，因為它受到資訊版權管理 (IRM) 保護。 」</span><span class="sxs-lookup"><span data-stu-id="472ee-242">You should see a message that states "Sorry, Word Online can't open this document because it's protected by Information Rights Management (IRM)."</span></span> 
    
7. <span data-ttu-id="472ee-243">按一下 [**在 Word 中編輯**]。</span><span class="sxs-lookup"><span data-stu-id="472ee-243">Click **Edit in Word**.</span></span> <span data-ttu-id="472ee-244">如果您想要開啟的檔案，會提示您。</span><span class="sxs-lookup"><span data-stu-id="472ee-244">You are prompted if you want to open the file.</span></span> <span data-ttu-id="472ee-245">按一下 [**是**]。</span><span class="sxs-lookup"><span data-stu-id="472ee-245">Click **Yes**.</span></span>
    
8. <span data-ttu-id="472ee-246">系統提示您登入。</span><span class="sxs-lookup"><span data-stu-id="472ee-246">You are prompted to sign-in.</span></span> <span data-ttu-id="472ee-247">輸入帳戶的 User5 帳戶名稱，然後再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="472ee-247">Type the account name of the User5 account, and then click **Next**.</span></span>
    
9. <span data-ttu-id="472ee-248">系統會提示您提供的密碼。</span><span class="sxs-lookup"><span data-stu-id="472ee-248">You are prompted to provide the password.</span></span> <span data-ttu-id="472ee-249">輸入 User5 帳戶的密碼，然後按一下 [**登入**。</span><span class="sxs-lookup"><span data-stu-id="472ee-249">Type the password for the User5 account and then click **Sign in**.</span></span> 
    
    <span data-ttu-id="472ee-250">您應該會看到訊息，說明如下: 「 您沒有可讓您開啟此文件的認證。 」</span><span class="sxs-lookup"><span data-stu-id="472ee-250">You should see the a message that states: "You do not have the credentials that allow you to open this document."</span></span>
    
10. <span data-ttu-id="472ee-251">按一下 [**否**]。</span><span class="sxs-lookup"><span data-stu-id="472ee-251">Click **No**.</span></span>
    
<span data-ttu-id="472ee-252">若要查看的 IRM 保護的另一個方式是要查看您的本機資料夾中的檔案。</span><span class="sxs-lookup"><span data-stu-id="472ee-252">Another way to see the IRM protection is to look at the files in your local folder.</span></span> <span data-ttu-id="472ee-253">**SensitiveData AfterIRM.docx**應該遠大於**SensitiveData BeforeIRM.docx**檔案。</span><span class="sxs-lookup"><span data-stu-id="472ee-253">The **SensitiveData-AfterIRM.docx** should be much larger than the **SensitiveData-BeforeIRM.docx** file.</span></span> <span data-ttu-id="472ee-254">**SensitiveData AfterIRM.docx**檔案進行加密，並已新增的 IRM 保護資訊。</span><span class="sxs-lookup"><span data-stu-id="472ee-254">The **SensitiveData-AfterIRM.docx** file is encrypted and has the IRM protection information added to it.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="472ee-255">另請參閱</span><span class="sxs-lookup"><span data-stu-id="472ee-255">See Also</span></span>

[<span data-ttu-id="472ee-256">雲端採用測試實驗室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="472ee-256">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="472ee-257">基底組態開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="472ee-257">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="472ee-258">Office 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="472ee-258">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="472ee-259">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="472ee-259">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


