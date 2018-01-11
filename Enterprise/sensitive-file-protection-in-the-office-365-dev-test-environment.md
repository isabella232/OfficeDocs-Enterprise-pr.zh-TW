---
title: "Office 365 開發人員/測試環境中的機密檔案保護"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: "摘要： 設定及示範如何 Office 365 資訊版權管理會保護敏感性檔案，甚至是當他們會張貼至錯誤的 SharePoint Online 網站集合。"
ms.openlocfilehash: eb456c86b118556abde6a887fe8b9ab68300740b
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2018
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a><span data-ttu-id="1b37b-103">Office 365 開發人員/測試環境中的機密檔案保護</span><span class="sxs-lookup"><span data-stu-id="1b37b-103">Sensitive file protection in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="1b37b-104">**摘要：**設定及示範如何 Office 365 資訊版權管理會保護敏感性檔案，甚至是當他們會張貼至錯誤的 SharePoint Online 網站集合。</span><span class="sxs-lookup"><span data-stu-id="1b37b-104">**Summary:** Configure and demonstrate how Office 365 Information Rights Management protects your sensitive files, even when they are posted to the wrong SharePoint Online site collection.</span></span>
  
<span data-ttu-id="1b37b-p101">資訊版權管理 (IRM) 設定在 Office 365 是一組的保護從 SharePoint Online 的文件庫及清單下載的文件的功能。下載的檔案加密及儲存 」、 「 包含開啟複本，且列印反映已儲存的 SharePoint Online 文件庫的權限。</span><span class="sxs-lookup"><span data-stu-id="1b37b-p101">Information Rights Management (IRM) in Office 365 is a set of capabilities to protect documents that are downloaded from SharePoint Online libraries and lists. Downloaded files are encrypted and contain the open, copy, save, and print permissions that reflect the SharePoint Online library in which they were stored.</span></span>
  
<span data-ttu-id="1b37b-107">使用本文中的指示，啟用並測試 IRM 在 Office 365 中包含在您的 Office 365 試用版訂閱可能敏感資訊的檔案。</span><span class="sxs-lookup"><span data-stu-id="1b37b-107">With the instructions in this article, you enable and test IRM in Office 365 for files containing possible sensitive information in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="1b37b-108">按一下[此處](http://aka.ms/catlgstack)的視覺對應至一個 Microsoft Cloud 測試實驗室指南堆疊中所有的文章。</span><span class="sxs-lookup"><span data-stu-id="1b37b-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="1b37b-109">階段 1： 建立 Office 365 開發人員/測試環境</span><span class="sxs-lookup"><span data-stu-id="1b37b-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="1b37b-110">如果您只想要測試機密檔案保護的基本需求的輕量型方式，請在階段 2 和 3 的[Office 365 開發人員/測試環境](office-365-dev-test-environment.md)中遵循的指示。</span><span class="sxs-lookup"><span data-stu-id="1b37b-110">If you just want to test sensitive file protection in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="1b37b-111">如果您想要測試機密檔案保護模擬 enterprise 中，請遵循[DirSync Office 365 開發人員/測試環境](dirsync-for-your-office-365-dev-test-environment.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="1b37b-111">If you want to test sensitive file protection in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="1b37b-p102">測試機密檔案保護不需要模擬的 enterprise 開發人員/測試環境中，其中包含連線至網際網路模擬內部網路和 Windows Server AD 樹系目錄同步處理。它會提供這裡是做為選項可以測試機密檔案保護和代表的典型組織的環境中實驗。</span><span class="sxs-lookup"><span data-stu-id="1b37b-p102">Testing sensitive file protection does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test sensitive file protection and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a><span data-ttu-id="1b37b-114">階段 2： 示範如何可以洩露從權限保護之網站的文件</span><span class="sxs-lookup"><span data-stu-id="1b37b-114">Phase 2: Demonstrate how documents from permissions-protected sites can be leaked</span></span>

<span data-ttu-id="1b37b-115">在此階段中，您會示範某個人可以從權限保護網站下載文件並再將其上傳至網站具有廣泛開放的權限。</span><span class="sxs-lookup"><span data-stu-id="1b37b-115">In this phase, you demonstrate that someone can download a document from a permissions-protected site and then upload it to a site that has wide-open permissions.</span></span>
  
<span data-ttu-id="1b37b-116">首先，您可以新增三個新的使用者帳戶的代表高階主管並且指派 Office 365 E5 授權。</span><span class="sxs-lookup"><span data-stu-id="1b37b-116">First, you add three new user accounts that represent executives and assign them Office 365 E5 licenses.</span></span>
  
<span data-ttu-id="1b37b-117">使用[Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx)中的指示安裝的 PowerShell 模組 （如果需要） 並連線至您從新的 Office 365 訂閱：</span><span class="sxs-lookup"><span data-stu-id="1b37b-117">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules (if needed) and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="1b37b-118">您的電腦 (適用於輕量型 Office 365 開發/測試環境)。</span><span class="sxs-lookup"><span data-stu-id="1b37b-118">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="1b37b-119">CLIENT1 虛擬機器 （適用於模擬的企業版 Office 365 開發人員/測試環境中）。</span><span class="sxs-lookup"><span data-stu-id="1b37b-119">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
<span data-ttu-id="1b37b-120">在 [ **Windows PowerShell 認證要求**] 對話方塊中，輸入 Office 365 全域管理員名稱 (範例： jdoe@contosotoycompany.onmicrosoft.com) 和 Office 365 試用版訂閱的密碼。</span><span class="sxs-lookup"><span data-stu-id="1b37b-120">In the **Windows PowerShell Credential Request** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password of your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="1b37b-121">填入您的組織名稱 (範例： contosotoycompany) 和雙字元國家位置、 程式碼與 Windows Azure Active Directory Module for Windows PowerShell 提示字元執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="1b37b-121">Fill in your organization name (example: contosotoycompany) and the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="1b37b-122">從**New-msoluser**命令顯示，請注意 CEO 帳戶產生的密碼並將其記錄在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="1b37b-122">From the display of the **New-MsolUser** command, note the generated password for the CEO account and record it in a safe location.</span></span>
  
<span data-ttu-id="1b37b-123">從適用於 Windows PowerShell 的 Windows Azure Active Directory 模組提示字元中執行下列命令︰</span><span class="sxs-lookup"><span data-stu-id="1b37b-123">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="1b37b-124">從**New-msoluser**命令顯示，請注意 CFO 帳戶產生的密碼並將其記錄在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="1b37b-124">From the display of the **New-MsolUser** command, note the generated password for the CFO account and record it in a safe location.</span></span>
  
<span data-ttu-id="1b37b-125">從適用於 Windows PowerShell 的 Windows Azure Active Directory 模組提示字元中執行下列命令︰</span><span class="sxs-lookup"><span data-stu-id="1b37b-125">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="1b37b-126">從**New-msoluser**命令顯示，請注意 COO 帳戶產生的密碼並將其記錄在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="1b37b-126">From the display of the **New-MsolUser** command, note the generated password for the COO account and record it in a safe location.</span></span>
  
<span data-ttu-id="1b37b-127">接下來，您建立專用的高階主管群組並將新的高階主管帳戶新增至其。</span><span class="sxs-lookup"><span data-stu-id="1b37b-127">Next, you create a private Executives group and add the new executive accounts to it.</span></span>
  
1. <span data-ttu-id="1b37b-128">在瀏覽器中移至[http://portal.office.com](http://portal.office.com) Office 入口網站並登入您的 Office 365 試用版訂閱以全域管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="1b37b-128">In your browser, go to the Office portal at [http://portal.office.com](http://portal.office.com) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="1b37b-129">如果您使用輕量型 Office 365 開發人員/測試環境，開啟 Internet Explorer 或瀏覽器中的私人工作階段並登入從本機電腦。</span><span class="sxs-lookup"><span data-stu-id="1b37b-129">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer or your browser and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="1b37b-130">如果您使用模擬的企業版 Office 365 開發人員/測試環境，使用 Azure 入口網站連線到 CLIENT1 虛擬機器，並從 CLIENT1 登入。</span><span class="sxs-lookup"><span data-stu-id="1b37b-130">If you are using the simulated enterprise Office 365 dev/test environment, use the Azure portal to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="1b37b-131">在 [ **Microsoft Office Home** ] 索引標籤上按一下 [ **Admin > 群組 > 群組**，然後按一下 [**新增群組**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-131">On the **Microsoft Office Home** tab, click **Admin > Groups > Groups**, and then click **Add a group**.</span></span>
    
3. <span data-ttu-id="1b37b-132">在**加入群組**]，選取**Office 365 群組**的群組類型、 輸入**高階主管**[**名稱**] 及 [**群組識別碼**，針對**隱私權**，選取 [**私人**，然後按一下 [**選取擁有者**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-132">In **Add a group**, select **Office 365 group** for the group type, type **Executives** in **Name** and **Group Id**, select **Private** for **Privacy**, and then click **Select Owner**.</span></span>
    
4. <span data-ttu-id="1b37b-133">在清單中，按一下 [全域管理員帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="1b37b-133">In the list, click your global administrator account name.</span></span>
    
5. <span data-ttu-id="1b37b-134">按一下 [**新增**] 和 [**關閉**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-134">Click **Add**, and then click **Close**.</span></span>
    
6. <span data-ttu-id="1b37b-135">在 [群組] 清單中，按一下 [**高階主管**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-135">In the groups list, click **Executives**.</span></span>
    
7. <span data-ttu-id="1b37b-136">按一下 [**編輯的成員**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-136">Click **Edit for Members**.</span></span>
    
8. <span data-ttu-id="1b37b-p103">按一下 [**新增成員**。在 [成員] 清單中，選取下列的使用者帳戶：</span><span class="sxs-lookup"><span data-stu-id="1b37b-p103">Click **Add members**. In the member list, select the following user accounts:</span></span>
    
  - <span data-ttu-id="1b37b-139">執行長</span><span class="sxs-lookup"><span data-stu-id="1b37b-139">Chief Executive Officer</span></span>
    
  - <span data-ttu-id="1b37b-140">主要的財務主管人員</span><span class="sxs-lookup"><span data-stu-id="1b37b-140">Chief Financial Officer</span></span>
    
  - <span data-ttu-id="1b37b-141">首席作業人員</span><span class="sxs-lookup"><span data-stu-id="1b37b-141">Chief Operations Officer</span></span>
    
9. <span data-ttu-id="1b37b-142">按一下 [**儲存**] 及 [**關閉**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-142">Click **Save**, and then click **Close**.</span></span>
    
10. <span data-ttu-id="1b37b-143">關閉**Office 系統管理中心**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1b37b-143">Close the **Office Admin center** tab.</span></span>
    
<span data-ttu-id="1b37b-144">接著，您建立高階主管的網站集合並允許對其進行存取的高階主管群組成員。</span><span class="sxs-lookup"><span data-stu-id="1b37b-144">Next, you create an Executives site collection and allow just the members of the Executives group to access it.</span></span>
  
1. <span data-ttu-id="1b37b-145">在 [ **Microsoft Office Home** ] 索引標籤上按一下**系統管理**磚。</span><span class="sxs-lookup"><span data-stu-id="1b37b-145">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="1b37b-146">在 [ **Office 系統管理中心**] 索引標籤上按一下 [**系統中心 > SharePoint**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-146">On the **Office Admin center** tab, click **Admin centers > SharePoint**.</span></span>
    
3. <span data-ttu-id="1b37b-147">在**SharePoint 管理中心**] 索引標籤上，按一下 [**新增 > 私用網站集合**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-147">On the **SharePoint admin center** tab, click **New > Private site collection**.</span></span>
    
4. <span data-ttu-id="1b37b-148">在 [新網站集合] 窗格中輸入**標題**] 中 [URL] 方塊中的高階主管的**高階主管****管理員**中指定全域管理員帳戶的名稱，然後按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-148">In the new site collection pane, type **Executives** in **Title**, executives in the URL box, specify the name of your global administrator account in **Administrator**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="1b37b-p104">等到已建立新的網站集合。完成後，將複製新的高階主管網站集合的 URL 並將它貼到新的索引標籤的瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="1b37b-p104">Wait until the new site collection has been created. When complete, copy the URL of the new Executives site collection and paste it into a new tab of your browser.</span></span>
    
6. <span data-ttu-id="1b37b-151">在右上角**高階主管**的網站集合中，按一下 [設定] 圖示，然後按一下 [**共用對象**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-151">In the upper right of the **Executives** site collection, click the settings icon, and then click **Shared with**.</span></span>
    
7. <span data-ttu-id="1b37b-152">在**共用 'Executives'**，按一下 [**進階**]。</span><span class="sxs-lookup"><span data-stu-id="1b37b-152">In **Share 'Executives'**, click **Advanced**.</span></span>
    
8. <span data-ttu-id="1b37b-153">在 SharePoint 群組的清單中，按一下 [**高階主管成員**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-153">In the list of SharePoint groups, click **Executives Members**.</span></span>
    
9. <span data-ttu-id="1b37b-154">在 [**人員與群組**] 頁面上按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="1b37b-154">On the **People and Groups** page, click **New**.</span></span>
    
10. <span data-ttu-id="1b37b-155">在**共用 'Executives'**輸入**高階主管**、**高階主管**] 群組中，按一下 [，然後按一下 [**共用**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-155">In **Share 'Executives'**, type **Executives**, click the **Executives** group, and then click **Share**.</span></span>
    
11. <span data-ttu-id="1b37b-156">關閉 [**人員與群組**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1b37b-156">Close the **People and groups** tab.</span></span>
    
<span data-ttu-id="1b37b-157">接下來，您讓所有人存取業務部網站集合。</span><span class="sxs-lookup"><span data-stu-id="1b37b-157">Next, you allow everyone to access the Sales site collection.</span></span>
  
1. <span data-ttu-id="1b37b-158">從 [ **SharePoint 管理中心**] 索引標籤複製業務部網站集合的 URL，並將它貼到新的索引標籤的瀏覽器.</span><span class="sxs-lookup"><span data-stu-id="1b37b-158">From the **SharePoint admin center** tab, copy the URL of the Sales site collection and paste it into a new tab of your browser..</span></span>
    
2. <span data-ttu-id="1b37b-159">在右上方，按一下 [設定] 圖示，和 [**共用對象**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-159">In the upper right, click the settings icon, and then click **Shared with**.</span></span>
    
3. <span data-ttu-id="1b37b-160">在**共用 'Sales 網站集合'**，按一下 [**進階**]。</span><span class="sxs-lookup"><span data-stu-id="1b37b-160">In **Share 'Sales site collection'**, click **Advanced**.</span></span>
    
4. <span data-ttu-id="1b37b-161">在 SharePoint 群組的清單中，按一下 [**銷售網站集合的成員**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-161">In the list of SharePoint groups, click **Sales site collection Members**.</span></span>
    
5. <span data-ttu-id="1b37b-162">在 [**人員與群組**] 頁面上按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="1b37b-162">On the **People and Groups** page, click **New**.</span></span>
    
6. <span data-ttu-id="1b37b-163">在**共用 'Sales 網站集合 」**，輸入**所有人**、 按一下 [**所有人以外的外部使用者**，和 [**共用**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-163">In **Share 'Sales site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share**.</span></span>
    
7. <span data-ttu-id="1b37b-164">關閉 [**銷售網站集合**和**SharePoint** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1b37b-164">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="1b37b-165">接下來，您使用高階主管的帳戶登入和主管網站集合中建立的文件。</span><span class="sxs-lookup"><span data-stu-id="1b37b-165">Next, you sign in with an executive account and create a document in the Executives site collection.</span></span>
  
1. <span data-ttu-id="1b37b-166">在 [ **Microsoft Office Home** ] 索引標籤上按一下 [使用者] 圖示的右上角和 [**登出**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-166">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="1b37b-167">移至[http://portal.office.com](http://portal.office.com)。</span><span class="sxs-lookup"><span data-stu-id="1b37b-167">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="1b37b-168">按一下 [ **Office 365 登入**] 索引標籤的 [**使用其他帳戶**]。</span><span class="sxs-lookup"><span data-stu-id="1b37b-168">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="1b37b-169">輸入**CEO**帳戶名稱和它的密碼，然後按一下 [**登入**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-169">Type the **CEO** account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="1b37b-170">在瀏覽器的新] 索引標籤上輸入高階主管的網站集合的 URL ( **https://**\<組織名稱 >**.sharepoint.com/sites/executives**)。</span><span class="sxs-lookup"><span data-stu-id="1b37b-170">On a new tab of your browser, type the URL to the Executives site collection ( **https://**\<organization name>**.sharepoint.com/sites/executives**).</span></span>
    
6. <span data-ttu-id="1b37b-171">按一下 [**文件**、 按一下 [**新增]**和 [ **Word 文件**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-171">Click **Documents**, click **New,** and then click **Word Document**.</span></span>
    
7. <span data-ttu-id="1b37b-172">按一下標題列中，輸入**SensitiveData BeforeIRM**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-172">Click in the title bar and type **SensitiveData-BeforeIRM**.</span></span>
    
8. <span data-ttu-id="1b37b-173">按一下 [內文件和輸入**從最新的佈告欄會議分鐘**，和 [**高階主管**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-173">Click in the document body and type **Minutes from the latest board meeting**, and then click **Executives**.</span></span>
    
     <span data-ttu-id="1b37b-174">您應該會看到**SensitiveData BeforeIRM.docx** **文件**] 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="1b37b-174">You should see **SensitiveData-BeforeIRM.docx** in the **Documents** folder.</span></span>
    
<span data-ttu-id="1b37b-175">接下來，您下載 SensitiveData BeforeIRM.docx 文件的本機複本與意外將張貼至銷售網站集合。</span><span class="sxs-lookup"><span data-stu-id="1b37b-175">Next, you download a local copy of the SensitiveData-BeforeIRM.docx document and then accidentally post it to the Sales site collection.</span></span>
  
1. <span data-ttu-id="1b37b-176">在您的本機電腦上建立新的資料夾 (例如 c:\\Tlg\\SensitiveDataTestFiles)。</span><span class="sxs-lookup"><span data-stu-id="1b37b-176">On your local computer, create a new folder (for example, C:\\TLGs\\SensitiveDataTestFiles).</span></span>
    
2. <span data-ttu-id="1b37b-177">在瀏覽器的**文件**] 索引標籤上選取**SensitiveData BeforeIRM.docx**文件、 按一下省略符號，並再按一下 [**下載**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-177">On the **Documents** tab of your browser, select the **SensitiveData-BeforeIRM.docx** document, click the ellipses, and then click **Download**.</span></span>
    
3. <span data-ttu-id="1b37b-178">步驟 1 中建立的資料夾中儲存的**SensitiveData BeforeIRM.docx**文件。</span><span class="sxs-lookup"><span data-stu-id="1b37b-178">Store the **SensitiveData-BeforeIRM.docx** document in the folder created in step 1.</span></span>
    
4. <span data-ttu-id="1b37b-179">新增索引標籤上的瀏覽器中，輸入 [業務部網站集合的 URL ( **https://**\<組織名稱 >**.sharepoint.com/sites/sales**)。</span><span class="sxs-lookup"><span data-stu-id="1b37b-179">On a new tab of your browser, type the URL to the Sales site collection ( **https://**\<organization name>**.sharepoint.com/sites/sales**).</span></span>
    
5. <span data-ttu-id="1b37b-180">按一下 [**文件**] 資料夾的**銷售網站集合**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-180">Click the **Documents** folder of the **Sales site collection**.</span></span>
    
6. <span data-ttu-id="1b37b-181">按一下 [**上傳**，然後指定**SensitiveData BeforeIRM.docx**文件中的步驟 1 中建立的資料夾，然後按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-181">Click **Upload**, and then specify **SensitiveData-BeforeIRM.docx** document in the folder created in step 1, and then click **OK**.</span></span>
    
7. <span data-ttu-id="1b37b-182">確認**SensitiveData BeforeIRM.docx**文件是在**文件**] 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="1b37b-182">Verify that the **SensitiveData-BeforeIRM.docx** document is in the **Documents** folder.</span></span>
    
8. <span data-ttu-id="1b37b-183">關閉 [**銷售**及**SharePoint**索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1b37b-183">Close the **Sales** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="1b37b-184">接著，您 User5 身分，登入並嘗試在業務部網站集合中開啟 SensitiveData BeforeIRM.docx 文件。</span><span class="sxs-lookup"><span data-stu-id="1b37b-184">Next, you sign in as User5 and try to open the SensitiveData-BeforeIRM.docx document in the Sales site collection.</span></span>
  
1. <span data-ttu-id="1b37b-185">在 [ **Microsoft Office Home** ] 索引標籤上按一下 [使用者] 圖示的右上角和 [**登出**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-185">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="1b37b-186">移至[http://portal.office.com](http://portal.office.com)。</span><span class="sxs-lookup"><span data-stu-id="1b37b-186">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="1b37b-187">按一下 [ **Office 365 登入**] 索引標籤的 [**使用其他帳戶**]。</span><span class="sxs-lookup"><span data-stu-id="1b37b-187">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="1b37b-188">輸入 User5 帳戶名稱和它的密碼，然後按一下 [**登入**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-188">Type the User5 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="1b37b-189">在瀏覽器的新] 索引標籤上輸入業務部網站集合的 URL。</span><span class="sxs-lookup"><span data-stu-id="1b37b-189">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
6. <span data-ttu-id="1b37b-190">在 [**文件**] 資料夾的**銷售網站集合**，按一下 [ **SensitiveData BeforeIRM.docx**文件。</span><span class="sxs-lookup"><span data-stu-id="1b37b-190">In the **Documents** folder of the **Sales site collection**, click the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
    <span data-ttu-id="1b37b-191">您應該查看其內容。</span><span class="sxs-lookup"><span data-stu-id="1b37b-191">You should see its contents.</span></span>
    
7. <span data-ttu-id="1b37b-192">關閉**文件**和**銷售網站集合**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1b37b-192">Close the **Documents** and **Sales site collection** tabs.</span></span>
    
<span data-ttu-id="1b37b-193">意外張貼 SensitiveData BeforeIRM.docx 文件業務部網站集合中，執行長略過的高階主管的網站集合的權限安全性。</span><span class="sxs-lookup"><span data-stu-id="1b37b-193">By accidentally posting the SensitiveData-BeforeIRM.docx document on the Sales site collection, the CEO bypassed the permissions security of the Executives site collection.</span></span>
  
<span data-ttu-id="1b37b-194">若要準備 Office 365 階段 3 和 4，啟用 IRM 的 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="1b37b-194">To prepare Office 365 for Phases 3 and 4, enable IRM for SharePoint Online.</span></span>
  
1. <span data-ttu-id="1b37b-195">在 [ **Microsoft Office Home** ] 索引標籤上按一下 [使用者] 圖示的右上角和 [**登出**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-195">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="1b37b-196">移至[http://portal.office.com](http://portal.office.com)。</span><span class="sxs-lookup"><span data-stu-id="1b37b-196">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="1b37b-197">在**Office 365 登入**] 頁面上按一下 [全域管理員帳戶名稱、 並輸入其密碼，然後按一下 [**登入**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-197">On the **Office 365 sign in** page, click the global administrator account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="1b37b-198">在 [ **Microsoft Office Home** ] 索引標籤上按一下 [ **Admin > 系統中心 > SharePoint**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-198">On the **Microsoft Office Home** tab, click **Admin > Admin centers > SharePoint**.</span></span>
    
5. <span data-ttu-id="1b37b-199">在 [ **SharePoint 管理中心**] 索引標籤上按一下 [**設定**]。</span><span class="sxs-lookup"><span data-stu-id="1b37b-199">On the **SharePoint admin center** tab, click **Settings**.</span></span>
    
6. <span data-ttu-id="1b37b-200">在 [**設定**] 頁面上的 [**資訊版權管理 (IRM)** ] 區段中選取 [**使用您的設定中指定的 IRM 服務**]，然後選取**重新整理 IRM 設定**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-200">On the **Settings** page, in the **Information Rights Management (IRM)** section, select **Use the IRM service specified in your configuration**, and then select **Refresh IRM Settings**.</span></span>
    
7. <span data-ttu-id="1b37b-201">關閉 [ **SharePoint 管理中心**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1b37b-201">Close the **SharePoint admin center** tab.</span></span>
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a><span data-ttu-id="1b37b-202">階段 3： 使用 SharePoint 資訊版權管理與 Office 365 私人群組</span><span class="sxs-lookup"><span data-stu-id="1b37b-202">Phase 3: Use SharePoint Information Rights Management with an Office 365 private group</span></span>

<span data-ttu-id="1b37b-203">在此階段中，您使用 SharePoint 資訊版權管理與 Office 365 私人群組會張貼站台的與開啟的權限，即使保護敏感資訊的文件的存取。</span><span class="sxs-lookup"><span data-stu-id="1b37b-203">In this phase, you use SharePoint Information Rights Management with an Office 365 private group to protect access to a document with sensitive information, even when it is posted on a site with open permissions.</span></span>
  
<span data-ttu-id="1b37b-204">首先，啟用並設定 IRM 的高階主管的網站集合的文件庫。</span><span class="sxs-lookup"><span data-stu-id="1b37b-204">First, you enable and configure IRM for the documents library of the Executives site collection.</span></span> 
  
1. <span data-ttu-id="1b37b-205">在瀏覽器的新] 索引標籤上輸入高階主管的網站集合的 URL。</span><span class="sxs-lookup"><span data-stu-id="1b37b-205">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
2. <span data-ttu-id="1b37b-206">按一下 [**文件**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-206">Click **Documents**.</span></span>
    
3. <span data-ttu-id="1b37b-207">右上角的 [設定] 圖示，和 [**文件庫設定**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-207">In the upper-right, click the settings icon, and then click **Library settings**.</span></span>
    
4. <span data-ttu-id="1b37b-208">在 [**設定**] 頁面**的權限與管理**] 下按一下 [**資訊版權管理**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-208">On the **Settings** page, under **Permissions and Management**, click **Information Rights Management**.</span></span>
    
5. <span data-ttu-id="1b37b-209">在 [**資訊版權管理設定**] 頁面上：</span><span class="sxs-lookup"><span data-stu-id="1b37b-209">On the **Information Rights Management Settings** page:</span></span>
    
  - <span data-ttu-id="1b37b-210">選取 [**限制下載此文件庫中的文件的權限**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-210">Select **Restrict permission to documents in this library on download**.</span></span>
    
  - <span data-ttu-id="1b37b-211">**建立權限原則標題**、 輸入**高階主管**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-211">For **Create a permission policy title**, type **Executives**.</span></span>
    
  - <span data-ttu-id="1b37b-212">**新增權限原則描述**]，輸入**IRM 的高階主管**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-212">For **Add a permission policy description**, type **IRM for executives**.</span></span>
    
6. <span data-ttu-id="1b37b-213">按一下 [**顯示選項**]。</span><span class="sxs-lookup"><span data-stu-id="1b37b-213">Click **Show Options**.</span></span>
    
7. <span data-ttu-id="1b37b-214">**設定其他 IRM 文件庫設定**] 下選取 [**不允許使用者上傳的不支援 IRM 的文件**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-214">Under **Set additional IRM library settings**, select **Do not allow users to upload documents that do not support IRM**.</span></span>
    
8. <span data-ttu-id="1b37b-215">[**設定文件存取權**，選取**要列印的允許檢視器**並**允許寫入已下載的文件的複本上的檢視器**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-215">Under **Configure document access rights**, select **Allow viewers to print** and **Allow viewers to write on a copy of the downloaded document**.</span></span>
    
9. <span data-ttu-id="1b37b-216">**設定群組保護和認證的時間間隔**] 下選取 [**允許群組保護**和**預設群組**中，輸入**高階主管**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-216">Under **Set group protection and credentials interval**, select **Allow group protection** and for **Default group**, type **Executives**.</span></span>
    
10. <span data-ttu-id="1b37b-217">按一下 [確定]****。</span><span class="sxs-lookup"><span data-stu-id="1b37b-217">Click **OK**.</span></span>
    
<span data-ttu-id="1b37b-218">下一步] 做為執行長，您將新的文件上傳至高階主管的文件資料夾、 下載、 然後意外將其上傳至銷售文件資料夾。</span><span class="sxs-lookup"><span data-stu-id="1b37b-218">Next, acting as the CEO, you upload a new document to the Executives document folder, download it, then accidentally upload it to the Sales document folder.</span></span>
  
1. <span data-ttu-id="1b37b-219">開啟您儲存**SensitiveData BeforeIRM.docx**文件的本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="1b37b-219">Open the local folder where you stored the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
2. <span data-ttu-id="1b37b-220">以滑鼠右鍵按一下**SensitiveData BeforeIRM.docx**，並再按一下 [**複製**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-220">Right-click **SensitiveData-BeforeIRM.docx**, and then click **Copy**.</span></span>
    
3. <span data-ttu-id="1b37b-221">以滑鼠右鍵按一下資料夾內並再按一下 [**貼**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-221">Right-click within the folder, and then click **Paste**.</span></span>
    
4. <span data-ttu-id="1b37b-222">新**SensitiveData-BeforeIRM-Copy.docx**檔案重新命名**SensitiveData AfterIRM.docx**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-222">Rename the new **SensitiveData-BeforeIRM - Copy.docx** file to **SensitiveData-AfterIRM.docx**.</span></span>
    
5. <span data-ttu-id="1b37b-223">從您的瀏覽器的 [ **Microsoft Office Home** ] 索引標籤按一下 [在右上角的 [使用者] 圖示] 和 [**登出**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-223">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
6. <span data-ttu-id="1b37b-224">移至[http://portal.office.com](http://portal.office.com)。</span><span class="sxs-lookup"><span data-stu-id="1b37b-224">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
7. <span data-ttu-id="1b37b-225">在**Office 365 登入**] 頁面上按一下 [CEO 帳戶名稱、 並輸入其密碼，然後按一下 [**登入**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-225">On the **Office 365 sign in** page, click the CEO account name, type its password, and then click **Sign in**.</span></span>
    
8. <span data-ttu-id="1b37b-226">在瀏覽器的新] 索引標籤上輸入高階主管的網站集合的 URL。</span><span class="sxs-lookup"><span data-stu-id="1b37b-226">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
9. <span data-ttu-id="1b37b-227">在 [**文件**] 頁面上，按一下 [**上傳**、 指定**SensitiveData AfterIRM.docx**文件您在本機資料夾、，然後按一下 [**開啟**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-227">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
10. <span data-ttu-id="1b37b-228">在**文件**] 頁面中選取新的**SensitiveData AfterIRM.docx**文件、 按一下 [功能表] 列中的省略符號 （...） 和 [**下載**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-228">Select the new **SensitiveData-AfterIRM.docx** document in the **Documents** page, click the ellipsis (…) in the menu bar, and then click **Download**.</span></span>
    
11. <span data-ttu-id="1b37b-229">出現提示時，將**SensitiveData AfterIRM.docx**文件儲存在本機資料夾，並覆寫原始版本。</span><span class="sxs-lookup"><span data-stu-id="1b37b-229">When prompted, save the **SensitiveData-AfterIRM.docx** document in your local folder, overwriting the original version.</span></span>
    
12. <span data-ttu-id="1b37b-230">關閉**文件**頁面] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1b37b-230">Close the tab for the **Documents** page.</span></span>
    
13. <span data-ttu-id="1b37b-231">在瀏覽器的新] 索引標籤上輸入業務部網站集合的 URL。</span><span class="sxs-lookup"><span data-stu-id="1b37b-231">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
14. <span data-ttu-id="1b37b-232">按一下 [**文件**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-232">Click **Documents**.</span></span>
    
15. <span data-ttu-id="1b37b-233">在 [**文件**] 頁面上，按一下 [**上傳**、 指定**SensitiveData AfterIRM.docx**文件您在本機資料夾、，然後按一下 [**開啟**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-233">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
16. <span data-ttu-id="1b37b-234">關閉 [**銷售網站集合**和**SharePoint** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1b37b-234">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="1b37b-235">下一步] 做為一般使用者，嘗試存取**SensitiveData AfterIRM.docx**文件的銷售文件資料夾中。</span><span class="sxs-lookup"><span data-stu-id="1b37b-235">Next, acting as a normal user, you try to access the **SensitiveData-AfterIRM.docx** document in the Sales document folder.</span></span>
  
1. <span data-ttu-id="1b37b-236">從您的瀏覽器的 [ **Microsoft Office Home** ] 索引標籤按一下 [在右上角的 [使用者] 圖示] 和 [**登出**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-236">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="1b37b-237">移至[http://portal.office.com](http://portal.office.com)。</span><span class="sxs-lookup"><span data-stu-id="1b37b-237">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="1b37b-238">在**Office 365 登入**] 頁面上按一下 [User5 帳戶名稱，並輸入其密碼，然後按一下 [**登入**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-238">On the **Office 365 sign in** page, click the User5 account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="1b37b-239">在瀏覽器的新] 索引標籤上輸入業務部網站集合的 URL。</span><span class="sxs-lookup"><span data-stu-id="1b37b-239">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
5. <span data-ttu-id="1b37b-240">按一下 [**文件**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-240">Click **Documents**.</span></span>
    
6. <span data-ttu-id="1b37b-241">在 [**文件**] 頁面開啟**SensitiveData AfterIRM.docx**文件。</span><span class="sxs-lookup"><span data-stu-id="1b37b-241">On the **Documents** page, open the **SensitiveData-AfterIRM.docx** document.</span></span>
    
    <span data-ttu-id="1b37b-242">您應該會看到訊息指出 「 很抱歉，因為它會受到資訊版權管理 (IRM) Word Online 無法開啟此文件。 」</span><span class="sxs-lookup"><span data-stu-id="1b37b-242">You should see a message that states "Sorry, Word Online can't open this document because it's protected by Information Rights Management (IRM)."</span></span> 
    
7. <span data-ttu-id="1b37b-p105">按一下 [**在 Word 中編輯**]。系統提示您若要開啟的檔案。按一下 [**是]**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-p105">Click **Edit in Word**. You are prompted if you want to open the file. Click **Yes**.</span></span>
    
8. <span data-ttu-id="1b37b-p106">登入提示您輸入 User5 帳戶的帳戶名稱，然後按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-p106">You are prompted to sign-in. Type the account name of the User5 account, and then click **Next**.</span></span>
    
9. <span data-ttu-id="1b37b-p107">系統提示您提供密碼。輸入 User5 帳戶的密碼，然後按一下 [**登入**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-p107">You are prompted to provide the password. Type the password for the User5 account and then click **Sign in**.</span></span> 
    
    <span data-ttu-id="1b37b-250">您應該會看到訊息表示： 「 您沒有可讓您開啟此文件的認證。 」</span><span class="sxs-lookup"><span data-stu-id="1b37b-250">You should see the a message that states: "You do not have the credentials that allow you to open this document."</span></span>
    
10. <span data-ttu-id="1b37b-251">按一下 [**否]**。</span><span class="sxs-lookup"><span data-stu-id="1b37b-251">Click **No**.</span></span>
    
<span data-ttu-id="1b37b-p108">若要查看 IRM 保護的另一種方式是要查看您的本機資料夾中的檔案。**SensitiveData AfterIRM.docx**應該更加大於**SensitiveData BeforeIRM.docx**檔案。加密**SensitiveData AfterIRM.docx**檔案，而且已新增 IRM 保護資訊。</span><span class="sxs-lookup"><span data-stu-id="1b37b-p108">Another way to see the IRM protection is to look at the files in your local folder. The **SensitiveData-AfterIRM.docx** should be much larger than the **SensitiveData-BeforeIRM.docx** file. The **SensitiveData-AfterIRM.docx** file is encrypted and has the IRM protection information added to it.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1b37b-255">請參閱</span><span class="sxs-lookup"><span data-stu-id="1b37b-255">See Also</span></span>

[<span data-ttu-id="1b37b-256">雲端採用測試實驗室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="1b37b-256">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="1b37b-257">基底組態開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="1b37b-257">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="1b37b-258">Office 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="1b37b-258">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="1b37b-259">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="1b37b-259">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


