---
title: "Office 365 開發/測試環境"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365, Strat_O365_Enterprise
ms.custom: Strat_O365_Enterprise, Ent_TLGs
ms.assetid: 4f6035b8-2da3-4cf9-9657-5284d6364f7a
description: "摘要： 使用此測試實驗室指南建立評估或開發人員/測試的 Office 365 試用版訂閱。"
ms.openlocfilehash: b3c9e83dfab3aaf02ad598021e11965657e877bb
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2018
---
# <a name="office-365-devtest-environment"></a><span data-ttu-id="e39f0-103">Office 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="e39f0-103">Office 365 dev/test environment</span></span>

 <span data-ttu-id="e39f0-104">**摘要：**使用此測試實驗室指南建立評估或開發人員/測試的 Office 365 試用版訂閱。</span><span class="sxs-lookup"><span data-stu-id="e39f0-104">**Summary:** Use this Test Lab Guide to create an Office 365 trial subscription for evaluation or dev/test.</span></span>
  
<span data-ttu-id="e39f0-p101">您可以使用 Office 365 試用版訂閱及建立 Office 365 開發人員/測試環境的應用程式或示範 Office 365 的特性與功能。有兩種版本：</span><span class="sxs-lookup"><span data-stu-id="e39f0-p101">You can use an Office 365 trial subscription and create an Office 365 dev/test environment for applications or to demonstrate features and capabilities of Office 365. There are two versions:</span></span>
  
- <span data-ttu-id="e39f0-107">輕量型 Office 365 開發人員/測試環境包含您從主要的電腦存取 Office 365 試用版訂閱。</span><span class="sxs-lookup"><span data-stu-id="e39f0-107">The lightweight Office 365 dev/test environment consists of an Office 365 trial subscription that you access from your main computer.</span></span>
    
    <span data-ttu-id="e39f0-p102">當您想要快速示範功能使用此環境。輕量型 Office 365 開發人員/測試環境中，完成階段 2 和 3 的本文。</span><span class="sxs-lookup"><span data-stu-id="e39f0-p102">Use this environment when you want to quickly demonstrate a feature. For the lightweight Office 365 dev/test environment, complete phases 2 and 3 of this article.</span></span>
    
- <span data-ttu-id="e39f0-p103">模擬的企業版 Office 365 開發人員/測試環境包含 Office 365 試用版訂閱] 與 [連線至網際網路，則會在 Microsoft Azure 基礎結構服務裝載簡化的組織內部網路。您可以建立 Microsoft 雲端中完全這個設定。</span><span class="sxs-lookup"><span data-stu-id="e39f0-p103">The simulated enterprise Office 365 dev/test environment consists of an Office 365 trial subscription and a simplified organization intranet connected to the Internet, which is hosted in Microsoft Azure infrastructure services. You can build this configuration completely in the Microsoft cloud.</span></span>
    
    <span data-ttu-id="e39f0-p104">使用此環境時要示範格式類似於連線至網際網路、 或功能需要這種類型的環境的典型組織網路環境中的應用程式或功能。模擬企業版 Office 365 開發人員/測試環境中，完成階段 1、 2 及 3 的本文。</span><span class="sxs-lookup"><span data-stu-id="e39f0-p104">Use this environment when you want to demonstrate a feature or an app in an environment that resembles a typical organization network connected to the Internet, or for features that require this type of environment. For the simulated enterprise Office 365 dev/test environment, complete phases 1, 2, and 3 of this article.</span></span>
    
> [!NOTE]
> <span data-ttu-id="e39f0-p105">您可能會想要列印本文章來記錄您需要對此環境的 Office 365 試用版訂閱 30 天的特定值。您可以輕鬆地擴充另一個 30 天的軌跡訂閱。在永久的開發人員測試環境中建立新付費少量的授權與訂閱。</span><span class="sxs-lookup"><span data-stu-id="e39f0-p105">You might want to print this article to record the specific values that you will need for this environment over the 30 days of the Office 365 trial subscription. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
![Microsoft 雲端中的測試實驗室指南](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="e39f0-118">按一下[此處](http://aka.ms/catlgstack)的視覺對應至一個 Microsoft Cloud 測試實驗室指南堆疊中所有的文章。</span><span class="sxs-lookup"><span data-stu-id="e39f0-118">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-base-configuration-in-azure"></a><span data-ttu-id="e39f0-119">階段 1： 在 Azure 中建立基本組態</span><span class="sxs-lookup"><span data-stu-id="e39f0-119">Phase 1: Create the base configuration in Azure</span></span>

<span data-ttu-id="e39f0-120">請遵循[基本設定開發/測試環境](base-configuration-dev-test-environment.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="e39f0-120">Follow the instructions in [Base Configuration dev/test environment](base-configuration-dev-test-environment.md).</span></span>
  
<span data-ttu-id="e39f0-p106">您將需要 Azure 訂閱。您可以使用[Azure 免費試用版](https://azure.microsoft.com/pricing/free-trial/)這個設定。如果您有 MSDN 或 Visual Studio 訂閱，請參閱[Visual Studio 訂閱者的每月 Azure 信用](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/)。</span><span class="sxs-lookup"><span data-stu-id="e39f0-p106">You will need an Azure subscription. You can use the [Azure Free Trial](https://azure.microsoft.com/pricing/free-trial/) for this configuration. If you have an MSDN or Visual Studio subscription, see [Monthly Azure credit for Visual Studio subscribers](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span></span>
  
<span data-ttu-id="e39f0-124">以下是所產生的設定。</span><span class="sxs-lookup"><span data-stu-id="e39f0-124">Here is the resulting configuration.</span></span>
  
![Azure 基底組態開發/測試環境](images/63108214-f716-46ae-9974-072ff15b44a2.png)
  
<span data-ttu-id="e39f0-126">此設定是由 DC1、 APP1 和 CLIENT1 虛擬機器上的 Azure 虛擬網路子網路所組成。</span><span class="sxs-lookup"><span data-stu-id="e39f0-126">This configuration consists of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
  
## <a name="phase-2-create-an-office-365-trial-subscription"></a><span data-ttu-id="e39f0-127">階段 2： 建立 Office 365 試用版訂閱</span><span class="sxs-lookup"><span data-stu-id="e39f0-127">Phase 2: Create an Office 365 trial subscription</span></span>

<span data-ttu-id="e39f0-128">若要啟動您的 Office 365 E5 試用版訂閱，您首先需要虛構公司名稱和新的 Microsoft 帳戶。</span><span class="sxs-lookup"><span data-stu-id="e39f0-128">To start your Office 365 E5 trial subscription, you first need a fictitious company name and a new Microsoft account.</span></span>
  
1. <span data-ttu-id="e39f0-p107">我們建議您的公司名稱 Contoso variant 用於您公司的名稱，也就是使用中 Microsoft 範例內容虛構公司，但並非必要。記錄您的虛構公司名稱： ___</span><span class="sxs-lookup"><span data-stu-id="e39f0-p107">We recommend that you use a variant of the company name Contoso for your company name, which is a fictitious company used in Microsoft sample content, but it isn't required. Record your fictitious company name here: _____________________________________</span></span>
    
2. <span data-ttu-id="e39f0-p108">若要註冊新的 Microsoft 帳戶，移至[https://outlook.com](https://outlook.com)並建立新的電子郵件帳戶和地址的帳戶。此帳戶會用於註冊 Office 365。</span><span class="sxs-lookup"><span data-stu-id="e39f0-p108">To sign up for a new Microsoft account, go to [https://outlook.com](https://outlook.com) and create an account with a new email account and address. You will use this account to sign up for Office 365.</span></span>
    
  - <span data-ttu-id="e39f0-133">您新增的帳戶的第一個及最後一個名稱記錄： ___</span><span class="sxs-lookup"><span data-stu-id="e39f0-133">Record the first and last name of your new account here: _______________________________</span></span>
    
  - <span data-ttu-id="e39f0-134">記錄的新電子郵件帳戶地址這裡： ___@outlook.com</span><span class="sxs-lookup"><span data-stu-id="e39f0-134">Record the new email account address here: _____________________________@outlook.com</span></span>
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a><span data-ttu-id="e39f0-135">註冊 Office 365 E5 試用訂閱</span><span class="sxs-lookup"><span data-stu-id="e39f0-135">Sign up for an Office 365 E5 trial subscription</span></span>

1. <span data-ttu-id="e39f0-136">輕量型 Office 365 開發人員/測試環境中，開啟您電腦上的 [網際網路瀏覽器並移至[https://aka.ms/e5trial](https://aka.ms/e5trial)。</span><span class="sxs-lookup"><span data-stu-id="e39f0-136">For the lightweight Office 365 dev/test environment, open the Internet browser on your computer and go to [https://aka.ms/e5trial](https://aka.ms/e5trial).</span></span> 
    
    <span data-ttu-id="e39f0-137">模擬企業版 Office 365 開發人員/測試環境中：</span><span class="sxs-lookup"><span data-stu-id="e39f0-137">For the simulated enterprise Office 365 dev/test environment:</span></span>
    
  - <span data-ttu-id="e39f0-138">從[Azure 入口網站](https://portal.azure.com)連線到與公司 CLIENT1\\User1 帳戶。</span><span class="sxs-lookup"><span data-stu-id="e39f0-138">From the [Azure portal](https://portal.azure.com), connect to CLIENT1 with the CORP\\User1 account.</span></span>
    
  - <span data-ttu-id="e39f0-139">開啟系統管理員層級 Windows PowerShell 命令提示字元處，並再執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="e39f0-139">Open an administrator-level Windows PowerShell command prompt, and then run these commands:</span></span>
    
  ```
  Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force
  ```

    > [!TIP]
    > <span data-ttu-id="e39f0-140">按一下[這裡](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34)以取得包含在本文中的所有 PowerShell 命令的文字檔案。</span><span class="sxs-lookup"><span data-stu-id="e39f0-140">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34) to get a text file that contains all the PowerShell commands in this article.</span></span>
  
  - <span data-ttu-id="e39f0-141">從 [開始] 畫面中，按一下 [ **Internet Explorer** ，並移至[https://aka.ms/e5trial](https://aka.ms/e5trial)。</span><span class="sxs-lookup"><span data-stu-id="e39f0-141">From the Start screen, click **Internet Explorer** and go to [https://aka.ms/e5trial](https://aka.ms/e5trial).</span></span>
    
2. <span data-ttu-id="e39f0-142">在 [**歡迎使用，讓我們知道您取得**] 頁面上指定：</span><span class="sxs-lookup"><span data-stu-id="e39f0-142">On the **Welcome, let's get to know you** page, specify:</span></span>
    
  - <span data-ttu-id="e39f0-143">實體位置</span><span class="sxs-lookup"><span data-stu-id="e39f0-143">Your physical location</span></span>
    
  - <span data-ttu-id="e39f0-144">在新的 Microsoft 帳戶的第一個及最後一個名稱</span><span class="sxs-lookup"><span data-stu-id="e39f0-144">The first and last name of your new Microsoft account</span></span>
    
  - <span data-ttu-id="e39f0-145">新的電子郵件帳戶地址</span><span class="sxs-lookup"><span data-stu-id="e39f0-145">Your new email account address</span></span>
    
  - <span data-ttu-id="e39f0-146">商務電話號碼</span><span class="sxs-lookup"><span data-stu-id="e39f0-146">A business phone number</span></span>
    
  - <span data-ttu-id="e39f0-147">虛構公司名稱</span><span class="sxs-lookup"><span data-stu-id="e39f0-147">Your fictional company name</span></span>
    
  - <span data-ttu-id="e39f0-148">組織大小 250 999 人</span><span class="sxs-lookup"><span data-stu-id="e39f0-148">An organization size of 250-999 people</span></span>
    
3. <span data-ttu-id="e39f0-149">按一下 [**只是一個詳細步驟**。</span><span class="sxs-lookup"><span data-stu-id="e39f0-149">Click **Just one more step**.</span></span>
    
4. <span data-ttu-id="e39f0-150">在 [**建立您的使用者識別碼**] 頁面上輸入您新的電子郵件地址之後, 虛構公司為基礎的使用者名稱 @ 符號 （移除所有分隔名稱中），後面接著密碼 （按兩次） 這個新的 Office 365 帳戶。</span><span class="sxs-lookup"><span data-stu-id="e39f0-150">On the **Create your user ID** page, type a user name based on your new email address, your fictional company after the @ sign (remove all spaces in the name), then a password (twice) for this new Office 365 account.</span></span>
    
    <span data-ttu-id="e39f0-151">記錄您在安全的位置中輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="e39f0-151">Record the password that you typed in a secure location.</span></span>
    
    <span data-ttu-id="e39f0-152">記錄您虛構公司名稱，以作為**組織名稱**，此處參照： ___</span><span class="sxs-lookup"><span data-stu-id="e39f0-152">Record your fictional company name, to be referred to as the **organization name**, here: ________________________________________</span></span>
    
5. <span data-ttu-id="e39f0-153">按一下 [**建立我的帳號**。</span><span class="sxs-lookup"><span data-stu-id="e39f0-153">Click **Create my account**.</span></span>
    
6. <span data-ttu-id="e39f0-p109">在**證明。您正在文章。不。A.機器人。**] 頁面上，輸入您文字可使用電話的電話號碼和 [**文字我**。</span><span class="sxs-lookup"><span data-stu-id="e39f0-p109">On the **Prove. You're. Not. A. Robot.** page, type the phone number of your text-capable phone, and then click **Text me**.</span></span>
    
7. <span data-ttu-id="e39f0-156">輸入從已接收之的文字郵件驗證碼，然後按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="e39f0-156">Type the verification code from the received text message, and then click **Next**.</span></span>
    
8. <span data-ttu-id="e39f0-157">登入頁面 URL 記錄以下 （選取和複本）： ___</span><span class="sxs-lookup"><span data-stu-id="e39f0-157">Record the sign-in page URL here (select and copy): ___________________________________________</span></span>
    
9. <span data-ttu-id="e39f0-158">記錄使用者識別碼此處 （選取和複本）： ___.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="e39f0-158">Record the user ID here (select and copy): __________________________________.onmicrosoft.com</span></span>
    
    <span data-ttu-id="e39f0-159">這個值將被稱為**Office 365 全域管理員名稱**。</span><span class="sxs-lookup"><span data-stu-id="e39f0-159">This value will be referred to as the **Office 365 global administrator name**.</span></span>
    
10. <span data-ttu-id="e39f0-160">當您看到**您準備好要移**時，請按一下它。</span><span class="sxs-lookup"><span data-stu-id="e39f0-160">When you see **You're ready to go**, click it.</span></span>
    
11. <span data-ttu-id="e39f0-161">在 [下一步] 頁面上等到 Office 365 設定完成設定和所有並排顯示可用。</span><span class="sxs-lookup"><span data-stu-id="e39f0-161">On the next page, wait until Office 365 completes setting up and all the tiles are available.</span></span>
    
<span data-ttu-id="e39f0-162">您應該會看到您可以從中存取 Office Online 服務及 Office 365 系統管理中心的主要 Office 365 入口網站頁面。</span><span class="sxs-lookup"><span data-stu-id="e39f0-162">You should see main Office 365 portal page from which you can access Office Online services and the Office 365 Admin center.</span></span>
  
<span data-ttu-id="e39f0-163">模擬的企業版 Office 365 開發人員/測試環境，以下是您所產生的設定。</span><span class="sxs-lookup"><span data-stu-id="e39f0-163">For the simulated enterprise Office 365 dev/test environment, here is your resulting configuration.</span></span>
  
![Office 365 開發/測試環境](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="e39f0-165">此組態組成為：</span><span class="sxs-lookup"><span data-stu-id="e39f0-165">This configuration consists of:</span></span> 
  
- <span data-ttu-id="e39f0-166">DC1、 APP1 和 CLIENT1 虛擬機器上的 Azure 虛擬網路子網路。</span><span class="sxs-lookup"><span data-stu-id="e39f0-166">The DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
- <span data-ttu-id="e39f0-167">Office 365 E5 列印試用訂閱。</span><span class="sxs-lookup"><span data-stu-id="e39f0-167">An Office 365 E5 Trial Subscription.</span></span>
    
## <a name="phase-3-configure-your-office-365-trial-subscription"></a><span data-ttu-id="e39f0-168">階段 3： 設定您的 Office 365 試用版訂閱</span><span class="sxs-lookup"><span data-stu-id="e39f0-168">Phase 3: Configure your Office 365 trial subscription</span></span>

<span data-ttu-id="e39f0-169">在此階段中，您可以設定您的 Office 365 訂閱與其他使用者和 SharePoint Online 小組網站。</span><span class="sxs-lookup"><span data-stu-id="e39f0-169">In this phase, you configure your Office 365 subscription with additional users and SharePoint Online team sites.</span></span>
  
<span data-ttu-id="e39f0-170">首先，您新增四個新的使用者並指派它們 E5 授權。</span><span class="sxs-lookup"><span data-stu-id="e39f0-170">First, you add four new users and assign them E5 licenses.</span></span>
  
<span data-ttu-id="e39f0-171">使用[Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx)中的指示安裝的 PowerShell 模組並連線至您從新的 Office 365 訂閱：</span><span class="sxs-lookup"><span data-stu-id="e39f0-171">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="e39f0-172">您的電腦 (適用於輕量型 Office 365 開發/測試環境)。</span><span class="sxs-lookup"><span data-stu-id="e39f0-172">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="e39f0-173">CLIENT1 虛擬機器 （適用於模擬的企業版 Office 365 開發人員/測試環境中）。</span><span class="sxs-lookup"><span data-stu-id="e39f0-173">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
 <span data-ttu-id="e39f0-174">在 [Windows PowerShell 認證要求] 對話方塊中，輸入 Office 365 全域管理員名稱 (範例： jdoe@contosotoycompany.onmicrosoft.com) 和密碼。</span><span class="sxs-lookup"><span data-stu-id="e39f0-174">In the Windows PowerShell Credential Request dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password.</span></span>
  
<span data-ttu-id="e39f0-175">填入您的組織名稱 (範例︰contosotoycompany)，位置的兩個字元國家/地區代碼，再從適用於 Windows PowerShell 的 Windows Azure Active Directory 模組提示字元中執行下列命令︰</span><span class="sxs-lookup"><span data-stu-id="e39f0-175">Fill in your organization name (example: contosotoycompany), the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "user2@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 2" -FirstName User -LastName 2 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="e39f0-176">從**New-msoluser**命令顯示，記下所產生的使用者 2 帳戶的密碼並將其記錄在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="e39f0-176">From the display of the **New-MsolUser** command, note the generated password for the User 2 account and record it in a safe location.</span></span>
  
<span data-ttu-id="e39f0-177">從適用於 Windows PowerShell 的 Windows Azure Active Directory 模組提示字元中執行下列命令︰</span><span class="sxs-lookup"><span data-stu-id="e39f0-177">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user3@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 3" -FirstName User -LastName 3 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="e39f0-178">從**New-msoluser**命令顯示，記下所產生的使用者 3 帳戶的密碼並將其記錄在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="e39f0-178">From the display of the **New-MsolUser** command, note the generated password for the User 3 account and record it in a safe location.</span></span>
  
<span data-ttu-id="e39f0-179">從適用於 Windows PowerShell 的 Windows Azure Active Directory 模組提示字元中執行下列命令︰</span><span class="sxs-lookup"><span data-stu-id="e39f0-179">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user4@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 4" -FirstName User -LastName 4 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="e39f0-180">從**New-msoluser**命令顯示，記下所產生的使用者 4 帳戶的密碼並將其記錄在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="e39f0-180">From the display of the **New-MsolUser** command, note the generated password for the User 4 account and record it in a safe location.</span></span>
  
<span data-ttu-id="e39f0-181">從適用於 Windows PowerShell 的 Windows Azure Active Directory 模組提示字元中執行下列命令︰</span><span class="sxs-lookup"><span data-stu-id="e39f0-181">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user5@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 5" -FirstName User -LastName 5 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="e39f0-182">從**New-msoluser**命令顯示，記下所產生的使用者 5 帳戶的密碼並將其記錄在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="e39f0-182">From the display of the **New-MsolUser** command, note the generated password for the User 5 account and record it in a safe location.</span></span>
  
<span data-ttu-id="e39f0-183">接下來，您建立三個新的 SharePoint Online 小組網站的銷售、 實際執行，並支援部門。</span><span class="sxs-lookup"><span data-stu-id="e39f0-183">Next, you create three new SharePoint Online team sites for the Sales, Production, and Support departments.</span></span>
  
### <a name="create-three-new-sharepoint-online-team-sites"></a><span data-ttu-id="e39f0-184">建立三個新的 SharePoint Online 小組網站</span><span class="sxs-lookup"><span data-stu-id="e39f0-184">Create three new SharePoint Online team sites</span></span>

1. <span data-ttu-id="e39f0-185">安裝[SharePoint Online 管理命令介面](https://go.microsoft.com/fwlink/p/?LinkId=255251)(x64 版)。</span><span class="sxs-lookup"><span data-stu-id="e39f0-185">Install the [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251) (the x64 version).</span></span>
    
2. <span data-ttu-id="e39f0-186">按一下 [**開始]**、 輸入**sharepoint**、 及 [ **SharePoint Online 管理命令介面**。</span><span class="sxs-lookup"><span data-stu-id="e39f0-186">Click **Start**, type **sharepoint**, and then click **SharePoint Online Management Shell**.</span></span>
    
3. <span data-ttu-id="e39f0-187">填入您的組織名稱 (範例： contosotoycompany)，然後連線至 SharePoint Online 服務在 SharePoint Online 管理命令介面提示字元處執行下列命令</span><span class="sxs-lookup"><span data-stu-id="e39f0-187">Fill in your organization name (example: contosotoycompany), and then run the following commands from the SharePoint Online Management Shell prompt to connect to the SharePoint Online service</span></span>
```
$orgName="<organization name>"
$spURL="https://" + $orgName + "-admin.sharepoint.com"
Connect-SPOService -Url $spURL
```

4. <span data-ttu-id="e39f0-188">在 [ **Microsoft SharePoint Online 管理命令介面**] 對話方塊中，輸入 Office 365 全域管理員名稱 (範例： jdoe@contosotoycompany.onmicrosoft.com) 和密碼，然後按一下 [**登入**。</span><span class="sxs-lookup"><span data-stu-id="e39f0-188">In the **Microsoft SharePoint Online Management Shell** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="e39f0-189">若要建立三個新的小組網站 （銷售、 實際執行與支援） 填滿 Office 365 全域管理員名稱] 中，並從 SharePoint Online 管理命令介面提示字元執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="e39f0-189">To create three new team sites (Sales, Production, and Support), fill in the Office 365 global administrator name, and then run the following commands from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  $owner = "<global administrator account name>"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/sales"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Sales site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/production"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Production site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/support"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Support site collection" -Template "STS#0"
  ```

6. <span data-ttu-id="e39f0-190">執行此命令以列出這些新網站的 Url：</span><span class="sxs-lookup"><span data-stu-id="e39f0-190">Run this command to list the URLs of these new sites:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

7. <span data-ttu-id="e39f0-191">在 Internet Explorer 中，輸入來查看預設 SharePoint Online 小組網站的實際執行部門實際執行網站的 URL。</span><span class="sxs-lookup"><span data-stu-id="e39f0-191">In Internet Explorer, enter the URL of the Production site to see the default SharePoint Online team site for the Production department.</span></span>
    
## <a name="record-values-for-future-reference"></a><span data-ttu-id="e39f0-192">以供未來參照的記錄值</span><span class="sxs-lookup"><span data-stu-id="e39f0-192">Record values for future reference</span></span>

<span data-ttu-id="e39f0-193">記錄使用或其他測試實驗室指南此測試環境中部署這些值：</span><span class="sxs-lookup"><span data-stu-id="e39f0-193">Record these values for working with or deploying additional Test Lab Guides in this test environment:</span></span>
  
- <span data-ttu-id="e39f0-194">Office 365 全域管理員名稱： ___.onmicrosoft.com （從階段 2 的步驟 9）</span><span class="sxs-lookup"><span data-stu-id="e39f0-194">Office 365 global administrator name: ____________________________________.onmicrosoft.com (from step 9 of Phase 2)</span></span>
    
    <span data-ttu-id="e39f0-195">也在安全的位置記錄此帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="e39f0-195">Also record the password for this account in a secure location.</span></span>
    
- <span data-ttu-id="e39f0-196">您的試用版訂閱的組織名稱： ___ （從步驟 4 的階段 2）</span><span class="sxs-lookup"><span data-stu-id="e39f0-196">Your trial subscription organization name: _______________________________________________ (from step 4 of Phase 2)</span></span>
    
- <span data-ttu-id="e39f0-197">若要列出之帳戶的使用者 2、 3 使用者、 使用者 4 和使用者 5，請在 Windows Azure Active Directory Module for Windows PowerShell 提示字元處執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="e39f0-197">To list the accounts for User 2, User 3, User 4, and User 5, run the following command from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
    
  ```
  Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    <span data-ttu-id="e39f0-198">記錄的帳戶名稱：</span><span class="sxs-lookup"><span data-stu-id="e39f0-198">Record the account names here:</span></span>
    
  - <span data-ttu-id="e39f0-199">使用者 2 帳戶名稱： user2@___.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="e39f0-199">User 2 account name: user2@_______________________________________________.onmicrosoft.com</span></span>
    
  - <span data-ttu-id="e39f0-200">3 的使用者帳戶名稱： user3@___.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="e39f0-200">User 3 account name: user3@_______________________________________________.onmicrosoft.com</span></span>
    
  - <span data-ttu-id="e39f0-201">4 的使用者帳戶名稱： user4@___.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="e39f0-201">User 4 account name: user4@_______________________________________________.onmicrosoft.com</span></span>
    
  - <span data-ttu-id="e39f0-202">5 的使用者帳戶名稱： user5@___.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="e39f0-202">User 5 account name: user5@_______________________________________________.onmicrosoft.com</span></span>
    
    <span data-ttu-id="e39f0-203">也在安全的位置記錄這些帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="e39f0-203">Also record the passwords for these accounts in a secure location.</span></span>
    
- <span data-ttu-id="e39f0-204">若要列出的 Url 的銷售、 實際執行，並支援小組網站，執行下列命令從 SharePoint Online 管理命令介面提示：</span><span class="sxs-lookup"><span data-stu-id="e39f0-204">To list the URLs for the Sales, Production, and Support team sites, run the following command from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

  - <span data-ttu-id="e39f0-205">實際執行網站 URL： https://___.sharepoint.com/sites/production</span><span class="sxs-lookup"><span data-stu-id="e39f0-205">Production site URL: https://______________________________________________.sharepoint.com/sites/production</span></span>
    
  - <span data-ttu-id="e39f0-206">銷售網站 URL： https://___.sharepoint.com/sites/sales</span><span class="sxs-lookup"><span data-stu-id="e39f0-206">Sales site URL: https://______________________________________________.sharepoint.com/sites/sales</span></span>
    
  - <span data-ttu-id="e39f0-207">支援的網站 URL： https://___.sharepoint.com/sites/support</span><span class="sxs-lookup"><span data-stu-id="e39f0-207">Support site URL: https://______________________________________________.sharepoint.com/sites/support</span></span>
    
## <a name="next-steps"></a><span data-ttu-id="e39f0-208">後續步驟</span><span class="sxs-lookup"><span data-stu-id="e39f0-208">Next steps</span></span>

<span data-ttu-id="e39f0-209">Office 365 開發人員/測試環境中使用這些額外的文章：</span><span class="sxs-lookup"><span data-stu-id="e39f0-209">Use these additional articles in your Office 365 dev/test environment:</span></span>
  
- [<span data-ttu-id="e39f0-210">Office 365 開發/測試環境的 DirSync</span><span class="sxs-lookup"><span data-stu-id="e39f0-210">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="e39f0-211">Office 365 開發人員/測試環境的多重要素驗證</span><span class="sxs-lookup"><span data-stu-id="e39f0-211">Multi-factor authentication for your Office 365 dev/test environment</span></span>](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="e39f0-212">Office 365 開發人員/測試環境的同盟身分識別</span><span class="sxs-lookup"><span data-stu-id="e39f0-212">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="e39f0-213">Office 365 開發人員/測試環境的雲端應用程式安全性</span><span class="sxs-lookup"><span data-stu-id="e39f0-213">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="e39f0-214">Office 365 開發人員/測試環境的進階威脅保護</span><span class="sxs-lookup"><span data-stu-id="e39f0-214">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="e39f0-215">Office 365 開發人員/測試環境的進階的 eDiscovery</span><span class="sxs-lookup"><span data-stu-id="e39f0-215">Advanced eDiscovery for your Office 365 dev/test environment</span></span>](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="e39f0-216">Office 365 開發人員/測試環境中的機密檔案保護</span><span class="sxs-lookup"><span data-stu-id="e39f0-216">Sensitive file protection in the Office 365 dev/test environment</span></span>](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="e39f0-217">隔離的 SharePoint Online 小組網站開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="e39f0-217">Isolated SharePoint Online team site dev/test environment</span></span>](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
- [<span data-ttu-id="e39f0-218">資料分類和 Office 365 開發人員/測試環境中顯示標籤</span><span class="sxs-lookup"><span data-stu-id="e39f0-218">Data classification and labeling in the Office 365 dev/test environment</span></span>](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
<span data-ttu-id="e39f0-219">擴充 Office 365 開發人員/測試環境包含其他 Microsoft cloud 方案：</span><span class="sxs-lookup"><span data-stu-id="e39f0-219">Extend your Office 365 dev/test environment to include additional Microsoft cloud offerings:</span></span>
  
- [<span data-ttu-id="e39f0-220">Microsoft 365 Enterprise 開發人員/測試環境</span><span class="sxs-lookup"><span data-stu-id="e39f0-220">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
    
- [<span data-ttu-id="e39f0-221">Office 365 和 Dynamics 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="e39f0-221">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
    
## <a name="see-also"></a><span data-ttu-id="e39f0-222">請參閱</span><span class="sxs-lookup"><span data-stu-id="e39f0-222">See Also</span></span>

[<span data-ttu-id="e39f0-223">雲端採用測試實驗室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="e39f0-223">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="e39f0-224">Office 365 和 Dynamics 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="e39f0-224">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
  
[<span data-ttu-id="e39f0-225">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="e39f0-225">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


