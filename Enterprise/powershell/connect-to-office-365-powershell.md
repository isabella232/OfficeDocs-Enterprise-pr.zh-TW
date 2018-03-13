---
title: "連線至 Office 365 PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/02/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: "摘要：使用 Office 365 PowerShell 連線到您的 Office 365 組織，以從命令列執行 Office 365 系統管理中心工作。"
ms.openlocfilehash: a13fcc401a4d00f49dcc4eec2a5acba36075233f
ms.sourcegitcommit: 2cfb30dd7c7a6bc9fa97a98f56ab8fe008504f41
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2018
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="c6974-103">連線至 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c6974-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="c6974-104">**摘要：**使用 Office 365 PowerShell 連線到您的 Office 365 組織，以從命令列執行 Office 365 系統管理工作。</span><span class="sxs-lookup"><span data-stu-id="c6974-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform Office 365 administration tasks from the command line.</span></span>
  
<span data-ttu-id="c6974-p101">Office 365 PowerShell 可讓您從命令列管理 Office 365 的設定。Office 365 PowerShell 是包含三個步驟的簡單程序，您可以在其中安裝必要的軟體、執行必要的軟體，然後連線至您的 Office 365 組織。</span><span class="sxs-lookup"><span data-stu-id="c6974-p101">Office 365 PowerShell lets you to manage your Office 365 settings from the command line. Connecting to Office 365 PowerShell is a simple three-step process where you install the required software, run the required software, and then connect to your Office 365 organization.</span></span> 

<span data-ttu-id="c6974-107">請注意，這些連線指示與 [Azure ActiveDirectory (MSOnline)](https://go.microsoft.com/fwlink/p/?LinkId=528113) 主題中的指示相同。</span><span class="sxs-lookup"><span data-stu-id="c6974-107">Note that these connection instructions are the same as those in the topic [Azure ActiveDirectory (MSOnline)](https://go.microsoft.com/fwlink/p/?LinkId=528113).</span></span>
  
> [!TIP]
> <span data-ttu-id="c6974-p102">**第一次使用 PowerShell？**請參閱 LinkedIn Learning 為您提供的 [PowerShell 概觀影片](http://technet.microsoft.com/library/https://support.office.com/zh-TW/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx)。</span><span class="sxs-lookup"><span data-stu-id="c6974-p102">**New to PowerShell?** See a [video Overview of PowerShell](http://technet.microsoft.com/library/https://support.office.com/zh-TW/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="c6974-110">開始之前有哪些須知？</span><span class="sxs-lookup"><span data-stu-id="c6974-110">What do you need to know before you begin?</span></span>

- <span data-ttu-id="c6974-111">預估完成時間：5 分鐘</span><span class="sxs-lookup"><span data-stu-id="c6974-111">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="c6974-112">您可以使用下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="c6974-112">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="c6974-113">Windows 10、Windows 8.1、Windows 8 或 Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="c6974-113">Windows 10, Windows 8.1, Windows 8 or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="c6974-114">Windows Server 2016、Windows Server 2012 R2、Windows Server 2012 或 Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="c6974-114">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="c6974-p103">請使用 64 位元的 Windows 版本。對 Windows PowerShell 的 Microsoft Azure Active Directory 模組 32 位元版本的支援已在 2014 年 10 月終止。</span><span class="sxs-lookup"><span data-stu-id="c6974-p103">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="c6974-p104">您用於這些程序的 Office 365工作或學校帳戶必須是 Office 365 系統管理員角色的成員。如需詳細資訊，請參閱[關於 Office 365 系統管理員角色](https://go.microsoft.com/fwlink/p/?LinkId=532367)。</span><span class="sxs-lookup"><span data-stu-id="c6974-p104">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="c6974-119">與適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組連線</span><span class="sxs-lookup"><span data-stu-id="c6974-119">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="c6974-120">在適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組中，命令的 Cmdlet 名稱會包含 **Msol**。</span><span class="sxs-lookup"><span data-stu-id="c6974-120">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="c6974-121">步驟 1：安裝必要的軟體</span><span class="sxs-lookup"><span data-stu-id="c6974-121">Step 1: Install required software</span></span>

<span data-ttu-id="c6974-p105">這些步驟只需您在電腦上執行一次，而不必在每次連線時執行。不過，您可能需要定期安裝較新的軟體版本。</span><span class="sxs-lookup"><span data-stu-id="c6974-p105">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="c6974-124">安裝 64 位元版本的 Microsoft Online Services 登入小幫手：[適用於 IT 專業人員的 Microsoft Online Services 登入小幫手 RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152)。</span><span class="sxs-lookup"><span data-stu-id="c6974-124">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="c6974-125">以下列步驟安裝適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組：</span><span class="sxs-lookup"><span data-stu-id="c6974-125">Install the the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="c6974-126">開啟管理員層級的 PowerShell 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="c6974-126">Open an administrator-level PowerShell command prompt.</span></span>
  - <span data-ttu-id="c6974-127">執行 **Install-Module MSOnline** 命令。</span><span class="sxs-lookup"><span data-stu-id="c6974-127">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="c6974-128">如果系統提示您安裝 NuGet 提供者，請輸入 **Y**，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="c6974-128">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="c6974-129">如果系統提示您從 PSGallery 安裝模組，請輸入 **Y**，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="c6974-129">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="c6974-130">安裝完成後，請關閉 PowerShell 命令視窗。</span><span class="sxs-lookup"><span data-stu-id="c6974-130">After installation, close the PowerShell command window.</span></span>
    
### <a name="step-2-connect-to-your-office-365-subscription"></a><span data-ttu-id="c6974-131">步驟 2：連線至您的 Office 365 訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="c6974-131">Step 2: Connect to your Office 365 subscription</span></span>
<span data-ttu-id="c6974-132"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="c6974-132"><a name="step3"> </a></span></span>

<span data-ttu-id="c6974-133">若要僅以*帳戶名稱和密碼*進行連線：</span><span class="sxs-lookup"><span data-stu-id="c6974-133">To connect with just an *account name and password*:</span></span>
  
1. <span data-ttu-id="c6974-134">執行 Windows PowerShell 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="c6974-134">Run a Windows PowerShell command prompt.</span></span>
2. <span data-ttu-id="c6974-135">在 [Windows PowerShell]**** 命令視窗中，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="c6974-135">In the **Windows PowerShell** command window, run the following commands:</span></span>
    
```
$UserCredential = Get-Credential
Connect-MsolService -Credential $UserCredential
```

3. <span data-ttu-id="c6974-136">在 [Windows PowerShell 認證要求] ****對話方塊中，輸入您的 Office 365工作或學校帳戶 使用者名稱和密碼，然後按一下 [確定]****。</span><span class="sxs-lookup"><span data-stu-id="c6974-136">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
<span data-ttu-id="c6974-137">若要以*多重要素驗證 (MFA)* 進行連線：</span><span class="sxs-lookup"><span data-stu-id="c6974-137">To connect with *multi-factor authentication (MFA)*:</span></span>
  
1. <span data-ttu-id="c6974-138">執行 Windows PowerShell 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="c6974-138">Run a Windows PowerShell command prompt.</span></span>
2. <span data-ttu-id="c6974-139">在 [Windows PowerShell 的 Microsoft Azure Active Directory 模組]**** 命令視窗中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="c6974-139">In the **Microsoft Azure Active Directory Module for Windows PowerShell** command window, run the following command.</span></span>
    
```
Connect-MsolService
```

3. <span data-ttu-id="c6974-140">在 [Azure Active Directory PowerShell] ****對話方塊中，鍵入您的 Office 365工作或學校帳戶 使用者名稱和密碼，然後按一下 [登入]****。</span><span class="sxs-lookup"><span data-stu-id="c6974-140">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="c6974-141">遵循 [Azure Active Directory PowerShell] 對話方塊中的指示，提供其他驗證資訊 (例如驗證碼)，然後按一下 [登入]。</span><span class="sxs-lookup"><span data-stu-id="c6974-141">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="c6974-142">如何知道這是否正常運作？</span><span class="sxs-lookup"><span data-stu-id="c6974-142">How do you know this worked?</span></span>
<span data-ttu-id="c6974-143"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="c6974-143"><a name="step3"> </a></span></span>

<span data-ttu-id="c6974-p106">如果您未收到任何錯誤，便已順利連線。若要做快速測試，您可以執行一個 Office 365 Cmdlet (例如 **Get-MsolUser** )，然後檢視結果。</span><span class="sxs-lookup"><span data-stu-id="c6974-p106">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="c6974-146">如果出現錯誤，請檢查下列需求：</span><span class="sxs-lookup"><span data-stu-id="c6974-146">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="c6974-p107">**密碼錯誤是常見的問題** 。再次執行步驟 3，並密切注意您輸入的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="c6974-p107">**A common problem is an incorrect password**. Run Step 3 again. and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="c6974-p108">**Windows PowerShell 的 Microsoft Azure Active Directory 模組 要求在您的電腦上啟用 Microsoft .NET Framework 3.5. _x_ 功能** 。您的電腦可能已安裝了較新的版本 (例如 4 或 4.5. _x_)，但可以啟用或停用舊版 .NET Framework 的回溯相容性。如需相關資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="c6974-p108">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5. _x_ feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5. _x_), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="c6974-154">針對 Windows Server 2012 或 Windows Server 2012 R2，請參閱[使用新增角色及功能精靈來啟用 .NET Framework 3.5](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span><span class="sxs-lookup"><span data-stu-id="c6974-154">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="c6974-155">針對 Windows 8 或 Windows 8.1，請參閱[在 Windows 8 或 8.1 上安裝 .NET Framework 3.5](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span><span class="sxs-lookup"><span data-stu-id="c6974-155">For Windows 8 or Windows 8.1, see [Installing the .NET Framework 3.5 on Windows 8 or 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span></span>
    
  - <span data-ttu-id="c6974-156">針對 Windows 7 或 Windows Server 2008 R2，請參閱[您無法開啟 Windows PowerShell 的 Azure Active Directory 模組](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span><span class="sxs-lookup"><span data-stu-id="c6974-156">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>
    
- <span data-ttu-id="c6974-p109">**您的 Windows PowerShell 的 Microsoft Azure Active Directory 模組 版本可能已過期。** 若要檢查，請在 Office 365 PowerShell 或 Windows PowerShell 的 Microsoft Azure Active Directory 模組 中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="c6974-p109">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="c6974-159">如果傳回的版本號碼低於 1.0.8070.2 值，請將 Windows PowerShell 的 Microsoft Azure Active Directory 模組 解除安裝，然後從步驟 1 中的連結安裝最新版本。</span><span class="sxs-lookup"><span data-stu-id="c6974-159">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="c6974-160">**如果您收到連線錯誤，請參閱本主題：** [「Connect-MsolService：擲回類型例外狀況」錯誤](https://go.microsoft.com/fwlink/p/?LinkId=532377)。</span><span class="sxs-lookup"><span data-stu-id="c6974-160">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    
## <a name="connect-with-the-azure-active-directory-v2-powershell-module"></a><span data-ttu-id="c6974-161">與 Azure Active Directory V2 PowerShell 模組連接</span><span class="sxs-lookup"><span data-stu-id="c6974-161">Connect with the Azure Active Directory V2 PowerShell module</span></span>
<span data-ttu-id="c6974-162"><a name="ConnectV2"> </a></span><span class="sxs-lookup"><span data-stu-id="c6974-162"><a name="ConnectV2"> </a></span></span>

<span data-ttu-id="c6974-163">在 Azure Active Directory V2 PowerShell 模組中，命令的 Cmdlet 名稱會包含 "AzureAD"。</span><span class="sxs-lookup"><span data-stu-id="c6974-163">Commands in the Azure Active Directory V2 PowerShell module have "AzureAD" in their cmdlet name.</span></span>

<span data-ttu-id="c6974-164">如果執行程序時需要 [Azure Active Directory V2 PowerShell 模組](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)中的新 Cmdlet，請使用下列步驟來安裝模組，並連線至您的 Office 365 訂用帳戶：</span><span class="sxs-lookup"><span data-stu-id="c6974-164">For procedures that require the new cmdlets in the [Azure Active Directory V2 PowerShell module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory), use these steps to install the module and connect to your Office 365 subscription.</span></span>

### <a name="step-1-install-required-software"></a><span data-ttu-id="c6974-165">步驟 1：安裝必要的軟體</span><span class="sxs-lookup"><span data-stu-id="c6974-165">Step 1: Install required software</span></span>

<span data-ttu-id="c6974-p110">這些步驟只需您在電腦上執行一次，而不必在每次連線時執行。不過，您可能需要定期安裝較新的軟體版本。</span><span class="sxs-lookup"><span data-stu-id="c6974-p110">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>

  
1. <span data-ttu-id="c6974-168">開啟提升權限的 Windows PowerShell 命令提示字元 (以系統管理員身分執行 Windows PowerShell)。</span><span class="sxs-lookup"><span data-stu-id="c6974-168">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="c6974-169">在 [系統管理員：Windows PowerShell] 命令視窗中，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="c6974-169">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD 
  ```

<span data-ttu-id="c6974-170">如果出現提示，指出需安裝來自不受信任存放庫的模組，請輸入 **Y**，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="c6974-170">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>


### <a name="step-2-connect-to-office-365"></a><span data-ttu-id="c6974-171">步驟 2：連線至 Office 365</span><span class="sxs-lookup"><span data-stu-id="c6974-171">Step 2: Connect to Office 365</span></span>

<span data-ttu-id="c6974-172">若要以*帳戶名稱和密碼*連線至您的 Office 365 訂用帳戶：</span><span class="sxs-lookup"><span data-stu-id="c6974-172">To connect to your Office 365 subscription with an *account name and password*:</span></span>
    
```
$UserCredential = Get-Credential
Connect-AzureAD -Credential $UserCredential
```

<span data-ttu-id="c6974-173">在 [Windows PowerShell 認證要求] ****對話方塊中，輸入您的 Office 365工作或學校帳戶 使用者名稱和密碼，然後按一下 [確定]****。</span><span class="sxs-lookup"><span data-stu-id="c6974-173">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
<span data-ttu-id="c6974-174">若要以*多重要素驗證 (MFA)* 連線至您的 Office 365 訂用帳戶：</span><span class="sxs-lookup"><span data-stu-id="c6974-174">To connect to your Office 365 subscription with *multi-factor authentication (MFA)*:</span></span>

```
Connect-AzureAD
```

<span data-ttu-id="c6974-175">在 [Azure Active Directory PowerShell] ****對話方塊中，鍵入您的 Office 365工作或學校帳戶 使用者名稱和密碼，然後按一下 [登入]****。</span><span class="sxs-lookup"><span data-stu-id="c6974-175">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
<span data-ttu-id="c6974-176">遵循 [Azure Active Directory PowerShell] 對話方塊中的指示，提供其他驗證資訊 (例如驗證碼)，然後按一下 [登入]。</span><span class="sxs-lookup"><span data-stu-id="c6974-176">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
<span data-ttu-id="c6974-177">連線之後，您可以對 [Azure Active Directory V2 PowerShell 模組](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)使用新的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c6974-177">After connecting, you can use the new cmdlets for the [Azure Active Directory V2 PowerShell module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c6974-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6974-178">See also</span></span>

[<span data-ttu-id="c6974-179">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="c6974-179">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="c6974-180">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c6974-180">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="c6974-181">在單一 Windows PowerShell 視窗中連線至所有 Office 365 服務</span><span class="sxs-lookup"><span data-stu-id="c6974-181">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)

[<span data-ttu-id="c6974-182">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="c6974-182">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
  
[<span data-ttu-id="c6974-183">Connect-MsolService</span><span class="sxs-lookup"><span data-stu-id="c6974-183">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

