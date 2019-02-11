---
title: Office 365 開發/測試環境
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/09/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 4f6035b8-2da3-4cf9-9657-5284d6364f7a
description: 摘要：使用此測試實驗室指南來建立 Office 365 試用訂閱以進行評估或開發/測試。
ms.openlocfilehash: 1606f30e28a482e60610d15b2f1643b9dd5b3240
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897266"
---
# <a name="office-365-devtest-environment"></a><span data-ttu-id="208bb-103">Office 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="208bb-103">Office 365 dev/test environment</span></span>

 <span data-ttu-id="208bb-104">**摘要：** 使用此測試實驗室指南來建立 Office 365 試用訂閱以進行評估或開發/測試。</span><span class="sxs-lookup"><span data-stu-id="208bb-104">**Summary:** Use this Test Lab Guide to create an Office 365 trial subscription for evaluation or dev/test.</span></span>
  
<span data-ttu-id="208bb-p101">您可以使用 Office 365 試用訂閱，並建立適用於應用程式的 Office 365 開發/測試環境或示範 Office 365 功能及能力。有兩種版本：</span><span class="sxs-lookup"><span data-stu-id="208bb-p101">You can use an Office 365 trial subscription and create an Office 365 dev/test environment for applications or to demonstrate features and capabilities of Office 365. There are two versions:</span></span>
  
- <span data-ttu-id="208bb-107">輕量型 Office 365 開發/測試環境包含您從主要電腦存取的 Office 365 試用訂閱。</span><span class="sxs-lookup"><span data-stu-id="208bb-107">The lightweight Office 365 dev/test environment consists of an Office 365 trial subscription that you access from your main computer.</span></span>
    
    <span data-ttu-id="208bb-p102">當您想要快速地示範一項功能時，請使用此環境。針對輕量型 Office 365 開發/測試環境，僅需完成這篇文章中的階段 2 和 3。</span><span class="sxs-lookup"><span data-stu-id="208bb-p102">Use this environment when you want to quickly demonstrate a feature. For the lightweight Office 365 dev/test environment, complete only phases 2 and 3 of this article.</span></span>
    
- <span data-ttu-id="208bb-p103">模擬的企業 Office 365 開發/測試環境包含 Office 365 試用訂閱，以及連線到網際網路的簡化組織之內部網路，此會在 Microsoft Azure 基礎結構服務中進行主控。您可以在 Microsoft 雲端中完整建置此組態。</span><span class="sxs-lookup"><span data-stu-id="208bb-p103">The simulated enterprise Office 365 dev/test environment consists of an Office 365 trial subscription and a simplified organization intranet connected to the Internet, which is hosted in Microsoft Azure infrastructure services. You can build this configuration completely in the Microsoft cloud.</span></span>
    
    <span data-ttu-id="208bb-p104">當您想要在與連接至網際網路之一般組織網路類似的環境中，或是針對需要此類環境的功能示範某項功能或某個應用程式時，請使用此環境。針對模擬企業 Office 365 開發/測試環境，請完成此文章的階段 1、2 和 3。</span><span class="sxs-lookup"><span data-stu-id="208bb-p104">Use this environment when you want to demonstrate a feature or an app in an environment that resembles a typical organization network connected to the Internet, or for features that require this type of environment. For the simulated enterprise Office 365 dev/test environment, complete phases 1, 2, and 3 of this article.</span></span>
    
> [!NOTE]
> <span data-ttu-id="208bb-p105">您可能會想要列印此文章來記錄此環境在 Office 365 試用訂閱的 30 天期間所需的特定值。您可以輕鬆地延長試用訂閱額外 30 天的時間。針對永久開發/測試環境，新建含少量授權的付費訂閱。</span><span class="sxs-lookup"><span data-stu-id="208bb-p105">You might want to print this article to record the specific values that you will need for this environment over the 30 days of the Office 365 trial subscription. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
![Microsoft Cloud 中的測試實驗室指南](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="208bb-118">按一下[這裡](http://aka.ms/catlgstack)，可查看 One Microsoft Cloud 測試實驗室指南堆疊中文件的所有視覺對應。</span><span class="sxs-lookup"><span data-stu-id="208bb-118">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-base-configuration-in-azure"></a><span data-ttu-id="208bb-119">階段 1：Azure 中建立基本設定</span><span class="sxs-lookup"><span data-stu-id="208bb-119">Phase 1: Create the base configuration in Azure</span></span>

<span data-ttu-id="208bb-120">遵循在[基底組態開發/測試環境](base-configuration-dev-test-environment.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="208bb-120">Follow the instructions in [Base Configuration dev/test environment](base-configuration-dev-test-environment.md).</span></span>
  
<span data-ttu-id="208bb-p106">您將需要 Azure 訂閱。您可以將 [Azure 免費試用版](https://azure.microsoft.com/pricing/free-trial/)用於此組態。如果您擁有 MSDN 或 Visual Studio 訂閱，請參閱 [Visual Studio 訂閱者的每月 Azure 點數](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/)。</span><span class="sxs-lookup"><span data-stu-id="208bb-p106">You will need an Azure subscription. You can use the [Azure Free Trial](https://azure.microsoft.com/pricing/free-trial/) for this configuration. If you have an MSDN or Visual Studio subscription, see [Monthly Azure credit for Visual Studio subscribers](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span></span>
  
<span data-ttu-id="208bb-124">以下是所產生的組態。</span><span class="sxs-lookup"><span data-stu-id="208bb-124">Here is the resulting configuration.</span></span>
  
![Azure 基底組態開發/測試環境](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)


  
<span data-ttu-id="208bb-126">此組態包含 DC1、APP1 和在 Azure 虛擬網路子網路上的 CLIENT1 虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="208bb-126">This configuration consists of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
  
## <a name="phase-2-create-an-office-365-trial-subscription"></a><span data-ttu-id="208bb-127">階段 2：建立 Office 365 試用訂閱</span><span class="sxs-lookup"><span data-stu-id="208bb-127">Phase 2: Create an Office 365 trial subscription</span></span>

<span data-ttu-id="208bb-128">若要開始 Office 365 E5 試用訂閱，您需要虛構的公司名稱和新 Microsoft 帳戶。</span><span class="sxs-lookup"><span data-stu-id="208bb-128">To start your Office 365 E5 trial subscription, you first need a fictitious company name and a new Microsoft account.</span></span>
  
1. <span data-ttu-id="208bb-p107">我們建議您使用公司名稱 Contoso 的變種作為公司名稱，也就是 Microsoft 範例內容中使用的虛構公司，但此為非必要的動作。在此處記錄您虛構公司名稱：![](./media/Common-Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="208bb-p107">We recommend that you use a variant of the company name Contoso for your company name, which is a fictitious company used in Microsoft sample content, but it isn't required. Record your fictitious company name here: ![](./media/Common-Images/TableLine.png)</span></span>
    
2. <span data-ttu-id="208bb-p108">若要註冊新 Microsoft 帳戶，請移至 [https://outlook.com ](https://outlook.com)，並使用新電子郵件帳戶以及地址建立帳戶。您會使用這個帳戶來登入 Office 365。</span><span class="sxs-lookup"><span data-stu-id="208bb-p108">To sign up for a new Microsoft account, go to [https://outlook.com](https://outlook.com) and create an account with a new email account and address. You will use this account to sign up for Office 365.</span></span>
    
  - <span data-ttu-id="208bb-133">在此處記錄您新帳戶的名字和姓氏：![](./media/Common-Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="208bb-133">Record the first and last name of your new account here: ![](./media/Common-Images/TableLine.png)</span></span>
    
  - <span data-ttu-id="208bb-134">在此處記錄新電子郵件帳戶地址：![](./media/Common-Images/TableLine.png)@outlook.com</span><span class="sxs-lookup"><span data-stu-id="208bb-134">Record the new email account address here: ![](./media/Common-Images/TableLine.png)@outlook.com</span></span>
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a><span data-ttu-id="208bb-135">註冊 Office 365 E5 試用訂閱</span><span class="sxs-lookup"><span data-stu-id="208bb-135">Sign up for an Office 365 E5 trial subscription</span></span>

1. <span data-ttu-id="208bb-136">針對輕量型 Office 365 開發/測試環境，開啟您電腦上的網際網路瀏覽器，然後移至 [https://aka.ms/e5trial](https://aka.ms/e5trial)。</span><span class="sxs-lookup"><span data-stu-id="208bb-136">For the lightweight Office 365 dev/test environment, open the Internet browser on your computer and go to [https://aka.ms/e5trial](https://aka.ms/e5trial).</span></span> 
    
    <span data-ttu-id="208bb-137">針對模擬的企業 Office 365 開發/測試環境，使用來自 Azure 入口網站的 CORP\User1 帳戶連接至 CLIENT1。</span><span class="sxs-lookup"><span data-stu-id="208bb-137">For the simulated enterprise Office 365 dev/test environment, connect to CLIENT1 with the CORP\User1 account from the Azure portal.</span></span>

    <span data-ttu-id="208bb-138">從 [開始] 畫面中，執行 Microsoft Edge，然後移至 [https://aka.ms/e5trial](https://aka.ms/e5trial)。</span><span class="sxs-lookup"><span data-stu-id="208bb-138">From the Start screen, run Microsoft Edge and go to [https://aka.ms/e5trial](https://aka.ms/e5trial).</span></span>
    
2. <span data-ttu-id="208bb-139">在 [歡迎，讓我們認識您]\*\*\*\* 頁面上，指定：</span><span class="sxs-lookup"><span data-stu-id="208bb-139">On the **Welcome, let's get to know you** page, specify:</span></span>
    
  - <span data-ttu-id="208bb-140">您的實際位置</span><span class="sxs-lookup"><span data-stu-id="208bb-140">Your physical location</span></span>
    
  - <span data-ttu-id="208bb-141">新 Microsoft 帳戶的名字和姓氏</span><span class="sxs-lookup"><span data-stu-id="208bb-141">The first and last name of your new Microsoft account</span></span>
    
  - <span data-ttu-id="208bb-142">新電子郵件帳戶地址</span><span class="sxs-lookup"><span data-stu-id="208bb-142">Your new email account address</span></span>
    
  - <span data-ttu-id="208bb-143">公司電話號碼</span><span class="sxs-lookup"><span data-stu-id="208bb-143">A business phone number</span></span>
    
  - <span data-ttu-id="208bb-144">虛構公司名稱</span><span class="sxs-lookup"><span data-stu-id="208bb-144">Your fictional company name</span></span>
    
  - <span data-ttu-id="208bb-145">250-999 名人員的組織規模</span><span class="sxs-lookup"><span data-stu-id="208bb-145">An organization size of 250-999 people</span></span>
    
3. <span data-ttu-id="208bb-146">按一下 [再多一個步驟]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="208bb-146">Click **Just one more step**.</span></span>
    
4. <span data-ttu-id="208bb-147">在 [建立使用者識別碼]\*\*\*\* 頁面上，根據新電子郵件地址輸入使用者名稱、在 @ 符號之後接上虛構公司 (移除名稱中的所有空格)，接著是此新 Office 365 帳戶的密碼 (兩次)。</span><span class="sxs-lookup"><span data-stu-id="208bb-147">On the **Create your user ID** page, type a user name based on your new email address, your fictional company after the @ sign (remove all spaces in the name), then a password (twice) for this new Office 365 account.</span></span>
    
    <span data-ttu-id="208bb-148">在安全位置中記錄您輸入的密碼。</span><span class="sxs-lookup"><span data-stu-id="208bb-148">Record the password that you typed in a secure location.</span></span>
    
    <span data-ttu-id="208bb-149">在這裡輸入虛構公司的名稱：![](./media/Common-Images/TableLine.png) (此將稱為**組織名稱**)</span><span class="sxs-lookup"><span data-stu-id="208bb-149">Record your fictional company name, to be referred to as the **organization name**, here: ![](./media/Common-Images/TableLine.png)</span></span>
    
5. <span data-ttu-id="208bb-150">按一下 [建立我的帳戶] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="208bb-150">Click **Create my account**.</span></span>
    
6. <span data-ttu-id="208bb-p109">在 [證明您不是機器人。]\*\*\*\* 頁面中，輸入能夠傳送簡訊的手機號碼，然後按一下 [傳送簡訊給我]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="208bb-p109">On the **Prove. You're. Not. A. Robot.** page, type the phone number of your text-capable phone, and then click **Text me**.</span></span>
    
7. <span data-ttu-id="208bb-153">輸入已接收簡訊訊息中的驗證代碼，然後按 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="208bb-153">Type the verification code from the received text message, and then click **Next**.</span></span>
    
8. <span data-ttu-id="208bb-154">在此記錄登入頁面 URL (選取並複製)：![](./media/Common-Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="208bb-154">Record the sign-in page URL here (select and copy): ![](./media/Common-Images/TableLine.png)</span></span>
    
9. <span data-ttu-id="208bb-155">在此記錄使用者識別碼 (選取與複製)：![](./media/Common-Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="208bb-155">Record the user ID here (select and copy): ![](./media/Common-Images/TableLine.png).onmicrosoft.com</span></span>
    
    <span data-ttu-id="208bb-156">此值將被稱為 **Office 365 全域系統管理員名稱**。</span><span class="sxs-lookup"><span data-stu-id="208bb-156">This value will be referred to as the **Office 365 global administrator name**.</span></span>
    
10. <span data-ttu-id="208bb-157">當您看到 [您已準備就緒]\*\*\*\*，對其按一下。</span><span class="sxs-lookup"><span data-stu-id="208bb-157">When you see **You're ready to go**, click it.</span></span>
    
11. <span data-ttu-id="208bb-158">在下一頁中，請稍候直到 Office 365 完成設定且所有的圖標皆可供使用。</span><span class="sxs-lookup"><span data-stu-id="208bb-158">On the next page, wait until Office 365 completes setting up and all the tiles are available.</span></span>
    
<span data-ttu-id="208bb-159">您應會看到主要 Office 365 入口網站頁面，您可以從其中存取 Office 線上服務和 Office 365 系統管理中心。</span><span class="sxs-lookup"><span data-stu-id="208bb-159">You should see main Office 365 portal page from which you can access Office Online services and the Office 365 Admin center.</span></span>
  
<span data-ttu-id="208bb-160">針對模擬的企業 Office 365 開發/測試環境，此為產生的組態。</span><span class="sxs-lookup"><span data-stu-id="208bb-160">For the simulated enterprise Office 365 dev/test environment, here is your resulting configuration.</span></span>
  
![Office 365 開發/測試環境](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="208bb-162">此組態組成為：</span><span class="sxs-lookup"><span data-stu-id="208bb-162">This configuration consists of:</span></span> 
  
- <span data-ttu-id="208bb-163">DC1、APP1 和在 Azure 虛擬網路子網路上的 CLIENT1 虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="208bb-163">The DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
- <span data-ttu-id="208bb-164">Office 365 E5 試用訂閱。</span><span class="sxs-lookup"><span data-stu-id="208bb-164">An Office 365 E5 Trial Subscription.</span></span>
    
## <a name="phase-3-configure-your-office-365-trial-subscription"></a><span data-ttu-id="208bb-165">階段 3：設定 Office 365 試用訂閱</span><span class="sxs-lookup"><span data-stu-id="208bb-165">Phase 3: Configure your Office 365 trial subscription</span></span>

<span data-ttu-id="208bb-166">在這個階段中，您可以使用其他使用者與 Sharepoint 小組網站設定 Office 365 訂閱。</span><span class="sxs-lookup"><span data-stu-id="208bb-166">In this phase, you configure your Office 365 subscription with additional users and SharePoint Online team sites.</span></span>
  
<span data-ttu-id="208bb-167">首先，請新增四個使用者，並將 E5 授權指派給他們。</span><span class="sxs-lookup"><span data-stu-id="208bb-167">First, you add four new users and assign them E5 licenses.</span></span>
  
<span data-ttu-id="208bb-168">使用「[連線到 Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx)」中的指示來安裝 PowerShell 模組，並從以下位置連線到新 Office 365 訂閱：</span><span class="sxs-lookup"><span data-stu-id="208bb-168">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="208bb-169">您的電腦 (適用於輕量型 Office 365 開發/測試環境)。</span><span class="sxs-lookup"><span data-stu-id="208bb-169">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="208bb-170">CLIENT1 虛擬機器 (適用於模擬的企業 Office 365 開發/測試環境)。</span><span class="sxs-lookup"><span data-stu-id="208bb-170">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
 <span data-ttu-id="208bb-171">在 [Windows PowerShell 認證要求] 對話方塊中，輸入 Office 365 全域管理員帳戶的使用者名稱 (例如：jdoe@contosotoycompany.onmicrosoft.com) 和密碼。</span><span class="sxs-lookup"><span data-stu-id="208bb-171">In the Windows PowerShell Credential Request dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password.</span></span>
  
<span data-ttu-id="208bb-172">填入您的組織名稱 (範例︰contosotoycompany)，位置的兩個字元國家/地區代碼，再從適用於 Windows PowerShell 的 Windows Azure Active Directory 模組提示字元中執行下列命令︰</span><span class="sxs-lookup"><span data-stu-id="208bb-172">Fill in your organization name (example: contosotoycompany), the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "user2@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 2" -FirstName User -LastName 2 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```
> [!TIP]
> <span data-ttu-id="208bb-173">按一下[這裡](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34)以取得包含本文中所有 PowerShell 命令的文字檔案。</span><span class="sxs-lookup"><span data-stu-id="208bb-173">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34) to get a text file that contains all the PowerShell commands in this article.</span></span>

<span data-ttu-id="208bb-174">從 **New-MsolUser** 命令的顯示畫面中，記下針對使用者 2 帳戶產生的密碼，並且將密碼記錄在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="208bb-174">From the display of the **New-MsolUser** command, note the generated password for the User 2 account and record it in a safe location.</span></span>
  
<span data-ttu-id="208bb-175">從適用於 Windows PowerShell 的 Windows Azure Active Directory 模組提示字元中執行下列命令︰</span><span class="sxs-lookup"><span data-stu-id="208bb-175">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user3@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 3" -FirstName User -LastName 3 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="208bb-176">從 **New-MsolUser** 命令的顯示畫面中，記下針對使用者 3 帳戶產生的密碼，並且將密碼記錄在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="208bb-176">From the display of the **New-MsolUser** command, note the generated password for the User 3 account and record it in a safe location.</span></span>
  
<span data-ttu-id="208bb-177">從適用於 Windows PowerShell 的 Windows Azure Active Directory 模組提示字元中執行下列命令︰</span><span class="sxs-lookup"><span data-stu-id="208bb-177">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user4@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 4" -FirstName User -LastName 4 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="208bb-178">從 **New-MsolUser** 命令的顯示畫面中，記下針對使用者 4 帳戶產生的密碼，並且將密碼記錄在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="208bb-178">From the display of the **New-MsolUser** command, note the generated password for the User 4 account and record it in a safe location.</span></span>
  
<span data-ttu-id="208bb-179">從適用於 Windows PowerShell 的 Windows Azure Active Directory 模組提示字元中執行下列命令︰</span><span class="sxs-lookup"><span data-stu-id="208bb-179">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user5@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 5" -FirstName User -LastName 5 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="208bb-180">從 **New-MsolUser** 命令的顯示畫面中，記下針對使用者 5 帳戶產生的密碼，並且將密碼記錄在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="208bb-180">From the display of the **New-MsolUser** command, note the generated password for the User 5 account and record it in a safe location.</span></span>
  
<span data-ttu-id="208bb-181">接下來，您為銷售、產品與支援部門建立三個新 SharePoint Online 小組網站。</span><span class="sxs-lookup"><span data-stu-id="208bb-181">Next, you create three new SharePoint Online team sites for the Sales, Production, and Support departments.</span></span>
  
## <a name="phase-4-create-three-new-sharepoint-online-team-sites-optional"></a><span data-ttu-id="208bb-182">階段 4：建立三個新 SharePoint Online 小組網站 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="208bb-182">Create three new SharePoint Online team sites</span></span>

<span data-ttu-id="208bb-183">您可以在這個階段設定一組 Sharepoint 小組網站。</span><span class="sxs-lookup"><span data-stu-id="208bb-183">In this phase, you configure a set of SharePoint Online team sites.</span></span>
  
1. <span data-ttu-id="208bb-184">安裝 [SharePoint Online 管理命令介面](https://go.microsoft.com/fwlink/p/?LinkId=255251) (x64 版本)。</span><span class="sxs-lookup"><span data-stu-id="208bb-184">Install the [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251) (the x64 version).</span></span>
    
2. <span data-ttu-id="208bb-185">按一下 [開始]\*\*\*\*，輸入 [sharepoint]\*\*\*\*，然後按一下 [SharePoint Online 管理命令介面]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="208bb-185">Click **Start**, type **sharepoint**, and then click **SharePoint Online Management Shell**.</span></span>
    
3. <span data-ttu-id="208bb-186">填入您組織名稱 (範例：contosotoycompany)，然後從 SharePoint Online 管理命令介面提示字元中執行下列命令，以連線至 SharePoint Online 服務</span><span class="sxs-lookup"><span data-stu-id="208bb-186">Fill in your organization name (example: contosotoycompany), and then run the following commands from the SharePoint Online Management Shell prompt to connect to the SharePoint Online service</span></span>
```
$orgName="<organization name>"
$spURL="https://" + $orgName + "-admin.sharepoint.com"
Connect-SPOService -Url $spURL
```

4. <span data-ttu-id="208bb-187">在 [Microsoft SharePoint Online 管理命令介面] \*\*\*\* 對話方塊中，輸入 Office 365 全域管理員帳戶名稱 (例如：jdoe@contosotoycompany.onmicrosoft.com) 和密碼，然後按一下 [登入]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="208bb-187">In the **Microsoft SharePoint Online Management Shell** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="208bb-188">若要建立三個新的小組網站 (銷售、產品和支援)，請填寫 Office 365 全域系統管理員名稱，並再從 SharePoint Online 管理命令介面提示字元中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="208bb-188">To create three new team sites (Sales, Production, and Support), fill in the Office 365 global administrator name, and then run the following commands from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  $owner = "<global administrator account name>"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/sales"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Sales site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/production"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Production site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/support"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Support site collection" -Template "STS#0"
  ```

6. <span data-ttu-id="208bb-189">執行此命令以列出這些新網站的 URL：</span><span class="sxs-lookup"><span data-stu-id="208bb-189">Run this command to list the URLs of these new sites:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

7. <span data-ttu-id="208bb-190">在 Internet Explorer 中，輸入產品網站的 URL　以查看生產部門的預設 Sharepoint Online 小組網站。</span><span class="sxs-lookup"><span data-stu-id="208bb-190">In Internet Explorer, enter the URL of the Production site to see the default SharePoint Online team site for the Production department.</span></span>
    
## <a name="record-values-for-future-reference"></a><span data-ttu-id="208bb-191">記錄值，以便日後參考</span><span class="sxs-lookup"><span data-stu-id="208bb-191">Record values for future reference</span></span>

<span data-ttu-id="208bb-192">記錄這些值，以便在此測試環境中處理或部署其他測試實驗室指南：</span><span class="sxs-lookup"><span data-stu-id="208bb-192">Record these values for working with or deploying additional Test Lab Guides in this test environment:</span></span>
  
- <span data-ttu-id="208bb-193">Office 365 全域系統管理員名稱：![](./media/Common-Images/TableLine.png).onmicrosoft.com (在階段 2 的步驟 9)</span><span class="sxs-lookup"><span data-stu-id="208bb-193">Office 365 global administrator name: ![](./media/Common-Images/TableLine.png).onmicrosoft.com (from step 9 of Phase 2)</span></span>
    
    <span data-ttu-id="208bb-194">將此帳戶的密碼記錄在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="208bb-194">Also record the password for this account in a secure location.</span></span>
    
- <span data-ttu-id="208bb-195">您的試用訂閱組織名稱：![](./media/Common-Images/TableLine.png) (從階段 2 的步驟 4)</span><span class="sxs-lookup"><span data-stu-id="208bb-195">Your trial subscription organization name: ![](./media/Common-Images/TableLine.png) (from step 4 of Phase 2)</span></span>
    
- <span data-ttu-id="208bb-196">若要列出使用者 2、使用者 3、使用者 4 和使用者 5 的帳戶，從適用於 Windows PowerShell 的 Windows Azure Active Directory 模組提示字元中執行下列命令︰</span><span class="sxs-lookup"><span data-stu-id="208bb-196">To list the accounts for User 2, User 3, User 4, and User 5, run the following command from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
    
  ```
  Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    <span data-ttu-id="208bb-197">在此記錄帳戶名稱：</span><span class="sxs-lookup"><span data-stu-id="208bb-197">Record the account names here:</span></span>
    
  - <span data-ttu-id="208bb-198">使用者 2 的帳戶名稱：user2 @![](./media/Common-Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="208bb-198">User 2 account name: user2@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span></span>
    
  - <span data-ttu-id="208bb-199">使用者 3 的帳戶名稱：user3 @![](./media/Common-Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="208bb-199">User 3 account name: user3@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span></span>
    
  - <span data-ttu-id="208bb-200">使用者 4 的帳戶名稱：user4 @![](./media/Common-Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="208bb-200">User 4 account name: user4@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span></span>
    
  - <span data-ttu-id="208bb-201">使用者 5 的帳戶名稱：user5 @![](./media/Common-Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="208bb-201">User 5 account name: user5@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span></span>
    
    <span data-ttu-id="208bb-202">將這些帳戶的密碼記錄於安全的位置。</span><span class="sxs-lookup"><span data-stu-id="208bb-202">Also record the passwords for these accounts in a secure location.</span></span>
    
- <span data-ttu-id="208bb-203">(選擇性) 若要列出銷售、生產和支援小組網站的 URL，請從 SharePoint Online 管理命令介面提示字元執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="208bb-203">To list the URLs for the Sales, Production, and Support team sites, run the following command from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

  - <span data-ttu-id="208bb-204">產品網站 URL：https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/production</span><span class="sxs-lookup"><span data-stu-id="208bb-204">Production site URL: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/production</span></span>
    
  - <span data-ttu-id="208bb-205">銷售網站 URL：https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/sales</span><span class="sxs-lookup"><span data-stu-id="208bb-205">Sales site URL: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/sales</span></span>
    
  - <span data-ttu-id="208bb-206">支援網站 URL：https://![](./media/Common-Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="208bb-206">Support site URL: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/support</span></span>
    
## <a name="next-steps"></a><span data-ttu-id="208bb-207">後續步驟</span><span class="sxs-lookup"><span data-stu-id="208bb-207">Next steps</span></span>

<span data-ttu-id="208bb-208">在 Office 365 開發/測試環境中使用這些額外文章：</span><span class="sxs-lookup"><span data-stu-id="208bb-208">Use these additional articles in your Office 365 dev/test environment:</span></span>
  
- [<span data-ttu-id="208bb-209">適用於 Office 365 開發/測試環境的目錄同步作業</span><span class="sxs-lookup"><span data-stu-id="208bb-209">Directory Synchronization for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="208bb-210">適用於您的 Office 365 開發/測試環境的多重要素驗證</span><span class="sxs-lookup"><span data-stu-id="208bb-210">Multi-factor authentication for your Office 365 dev/test environment</span></span>](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="208bb-211">Office 365 開發人員/測試環境的同盟身分識別</span><span class="sxs-lookup"><span data-stu-id="208bb-211">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="208bb-212">Office 365 開發人員/測試環境的雲端 App 安全性</span><span class="sxs-lookup"><span data-stu-id="208bb-212">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="208bb-213">適用於 Office 365 開發/測試環境的進階威脅防護</span><span class="sxs-lookup"><span data-stu-id="208bb-213">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="208bb-214">適用於 Office 365 開發/測試環境的進階電子文件探索</span><span class="sxs-lookup"><span data-stu-id="208bb-214">Advanced eDiscovery for your Office 365 dev/test environment</span></span>](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="208bb-215">Office 365 開發/測試環境中的機密檔案保護</span><span class="sxs-lookup"><span data-stu-id="208bb-215">Sensitive file protection in the Office 365 dev/test environment</span></span>](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="208bb-216">獨立的 SharePoint Online 小組網站開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="208bb-216">Isolated SharePoint Online team site dev/test environment</span></span>](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
- [<span data-ttu-id="208bb-217">Office 365 開發/測試環境中的資料分類和標示</span><span class="sxs-lookup"><span data-stu-id="208bb-217">Data classification and labeling in the Office 365 dev/test environment</span></span>](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
<span data-ttu-id="208bb-218">擴充 Office 365 開發/測試環境中以包含其他 Microsoft 雲端供應項目：</span><span class="sxs-lookup"><span data-stu-id="208bb-218">Extend your Office 365 dev/test environment to include additional Microsoft cloud offerings:</span></span>
  
- [<span data-ttu-id="208bb-219">Microsoft 365 企業版開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="208bb-219">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
    
- [<span data-ttu-id="208bb-220">Office 365 和 Dynamics 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="208bb-220">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
    
## <a name="see-also"></a><span data-ttu-id="208bb-221">另請參閱</span><span class="sxs-lookup"><span data-stu-id="208bb-221">See Also</span></span>

- [<span data-ttu-id="208bb-222">雲端採用測試實驗室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="208bb-222">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
- [<span data-ttu-id="208bb-223">Office 365 和 Dynamics 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="208bb-223">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
  
- [<span data-ttu-id="208bb-224">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="208bb-224">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


