---
title: 連線至 Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/20/2018
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
description: 摘要： 連線至 Office 365 組織使用 Office 365 PowerShell 從命令列執行 admin center 工作。
ms.openlocfilehash: 96406fbc23adadbf77a3cd02f8c167081f908977
ms.sourcegitcommit: c3869a332512dd1cc25cd5a92a340050f1da0418
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2018
ms.locfileid: "20720399"
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="56ccb-103">連線至 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="56ccb-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="56ccb-104">**摘要：** 連線至 Office 365 組織使用 Office 365 PowerShell 從命令列執行管理工作。</span><span class="sxs-lookup"><span data-stu-id="56ccb-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform administration tasks from the command line.</span></span>
  
<span data-ttu-id="56ccb-p101">Office 365 PowerShell 可讓您從命令列管理 Office 365 的設定。Office 365 PowerShell 是包含三個步驟的簡單程序，您可以在其中安裝必要的軟體、執行必要的軟體，然後連線至您的 Office 365 組織。</span><span class="sxs-lookup"><span data-stu-id="56ccb-p101">Office 365 PowerShell lets you to manage your Office 365 settings from the command line. Connecting to Office 365 PowerShell is a simple three-step process where you install the required software, run the required software, and then connect to your Office 365 organization.</span></span> 

  
> [!TIP]
> <span data-ttu-id="56ccb-p102">**第一次使用 PowerShell？** 請參閱 LinkedIn Learning 為您提供的 [PowerShell 概觀影片](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx)。</span><span class="sxs-lookup"><span data-stu-id="56ccb-p102">**New to PowerShell?** See a [video Overview of PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="56ccb-109">開始之前有哪些須知？</span><span class="sxs-lookup"><span data-stu-id="56ccb-109">What do you need to know before you begin?</span></span>

- <span data-ttu-id="56ccb-110">預估完成時間：5 分鐘</span><span class="sxs-lookup"><span data-stu-id="56ccb-110">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="56ccb-111">您可以使用下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="56ccb-111">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="56ccb-112">Windows 10、Windows 8.1、Windows 8 或 Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="56ccb-112">Windows 10, Windows 8.1, Windows 8 or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="56ccb-113">Windows Server 2016、Windows Server 2012 R2、Windows Server 2012 或 Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="56ccb-113">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="56ccb-p103">請使用 64 位元的 Windows 版本。對 Windows PowerShell 的 Microsoft Azure Active Directory 模組 32 位元版本的支援已在 2014 年 10 月終止。</span><span class="sxs-lookup"><span data-stu-id="56ccb-p103">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="56ccb-p104">這些程序適用於使用者的 Office 365 系統管理員角色的成員。如需詳細資訊，請參閱 ＜[關於 Office 365 系統管理員角色](https://go.microsoft.com/fwlink/p/?LinkId=532367)。</span><span class="sxs-lookup"><span data-stu-id="56ccb-p104">These procedures are intended for users who are members of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>

## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="56ccb-118">使用 Azure Active Directory PowerShell 圖模組的連線</span><span class="sxs-lookup"><span data-stu-id="56ccb-118">Connect with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="56ccb-119">[圖表 Azure Active Directory PowerShell](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)模組中的命令會有**AzureAD**在其指令程式名稱。</span><span class="sxs-lookup"><span data-stu-id="56ccb-119">Commands in the [Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) module have **AzureAD** in their cmdlet name.</span></span>

<span data-ttu-id="56ccb-120">如圖模組的需要在 Azure Active Directory PowerShell 中的新 cmdlet 的程序，使用下列步驟來安裝此模組，並連線至您的 Office 365 訂閱。</span><span class="sxs-lookup"><span data-stu-id="56ccb-120">For procedures that require the new cmdlets in the Azure Active Directory PowerShell for Graph module, use these steps to install the module and connect to your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="56ccb-121">請參閱[Azure Active Directory PowerShell 圖模組的](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)不同版本的 Microsoft Windows 支援的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="56ccb-121">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="56ccb-122">步驟 1：安裝必要的軟體</span><span class="sxs-lookup"><span data-stu-id="56ccb-122">Step 1: Install required software</span></span>

<span data-ttu-id="56ccb-p105">這些步驟只需您在電腦上執行一次，而不必在每次連線時執行。不過，您可能需要定期安裝較新的軟體版本。</span><span class="sxs-lookup"><span data-stu-id="56ccb-p105">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1. <span data-ttu-id="56ccb-125">開啟提升權限的 Windows PowerShell 命令提示字元 (以系統管理員身分執行 Windows PowerShell)。</span><span class="sxs-lookup"><span data-stu-id="56ccb-125">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="56ccb-126">在 [系統管理員：Windows PowerShell] 命令視窗中，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="56ccb-126">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD
  ```

<span data-ttu-id="56ccb-127">如果出現提示，指出需安裝來自不受信任存放庫的模組，請輸入 **Y**，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="56ccb-127">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="56ccb-128">步驟 2： 連線至 Office 365 訂閱的 Azure AD</span><span class="sxs-lookup"><span data-stu-id="56ccb-128">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="56ccb-129">若要連線至 Azure AD 的 Office 365 訂閱使用的帳戶名稱及密碼或*多重要素驗證 (MFA)* 會執行此命令 （它沒有要提高權限） Windows PowerShell 命令提示字元：</span><span class="sxs-lookup"><span data-stu-id="56ccb-129">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)* run this command from a Windows PowerShell command prompt (it does not have to be elevated):</span></span>
    
```
Connect-AzureAD
```

<span data-ttu-id="56ccb-130">在 [**登入您的帳戶**] 對話方塊中，輸入您的 Office 365 工作或學校帳戶使用者名稱和密碼，並再按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="56ccb-130">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="56ccb-131">如果您使用 MFA，請遵循在 [其他] 對話方塊中的指示以提供更多的驗證資訊，例如驗證碼。</span><span class="sxs-lookup"><span data-stu-id="56ccb-131">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>
    
<span data-ttu-id="56ccb-132">連接之後，您可以使用的新 cmdlet 的[Azure Active Directory PowerShell 圖模組的](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)。</span><span class="sxs-lookup"><span data-stu-id="56ccb-132">After connecting, you can use the new cmdlets for the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="56ccb-133">與適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組連線</span><span class="sxs-lookup"><span data-stu-id="56ccb-133">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="56ccb-134">在適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組中，命令的 Cmdlet 名稱會包含 **Msol**。</span><span class="sxs-lookup"><span data-stu-id="56ccb-134">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="56ccb-135">步驟 1：安裝必要的軟體</span><span class="sxs-lookup"><span data-stu-id="56ccb-135">Step 1: Install required software</span></span>

<span data-ttu-id="56ccb-p106">這些步驟只需您在電腦上執行一次，而不必在每次連線時執行。不過，您可能需要定期安裝較新的軟體版本。</span><span class="sxs-lookup"><span data-stu-id="56ccb-p106">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="56ccb-138">安裝 64 位元版本的 Microsoft Online Services 登入小幫手：[適用於 IT 專業人員的 Microsoft Online Services 登入小幫手 RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152)。</span><span class="sxs-lookup"><span data-stu-id="56ccb-138">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="56ccb-139">以下列步驟安裝適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組：</span><span class="sxs-lookup"><span data-stu-id="56ccb-139">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="56ccb-140">開啟提升權限的 Windows PowerShell 命令提示字元 (以系統管理員身分執行 Windows PowerShell)。</span><span class="sxs-lookup"><span data-stu-id="56ccb-140">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
  - <span data-ttu-id="56ccb-141">執行 **Install-Module MSOnline** 命令。</span><span class="sxs-lookup"><span data-stu-id="56ccb-141">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="56ccb-142">如果系統提示您安裝 NuGet 提供者，請輸入 **Y**，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="56ccb-142">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="56ccb-143">如果系統提示您從 PSGallery 安裝模組，請輸入 **Y**，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="56ccb-143">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="56ccb-144">步驟 2： 連線至 Office 365 訂閱的 Azure AD</span><span class="sxs-lookup"><span data-stu-id="56ccb-144">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="56ccb-145">若要連線至您的 Office 365 訂閱使用的帳戶名稱及密碼或*多重要素驗證 (MFA)* 的 Azure AD，請從 Windows PowerShell 命令提示字元 （它沒有要提高權限） 執行此命令：</span><span class="sxs-lookup"><span data-stu-id="56ccb-145">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run this command from a Windows PowerShell command prompt (it does not have to be elevated):</span></span>
    
```
Connect-MsolService
```

<span data-ttu-id="56ccb-146">在 [**登入您的帳戶**] 對話方塊中，輸入您的 Office 365 工作或學校帳戶使用者名稱和密碼，並再按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="56ccb-146">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="56ccb-147">如果您使用 MFA，請遵循在 [其他] 對話方塊中的指示以提供更多的驗證資訊，例如驗證碼。</span><span class="sxs-lookup"><span data-stu-id="56ccb-147">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

    
### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="56ccb-148">如何知道這是否正常運作？</span><span class="sxs-lookup"><span data-stu-id="56ccb-148">How do you know this worked?</span></span>

<span data-ttu-id="56ccb-p107">如果您未收到任何錯誤，便已順利連線。若要做快速測試，您可以執行一個 Office 365 Cmdlet (例如 **Get-MsolUser** )，然後檢視結果。</span><span class="sxs-lookup"><span data-stu-id="56ccb-p107">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="56ccb-151">如果出現錯誤，請檢查下列需求：</span><span class="sxs-lookup"><span data-stu-id="56ccb-151">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="56ccb-p108">**密碼錯誤是常見的問題** 。再次執行步驟 3，並密切注意您輸入的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="56ccb-p108">**A common problem is an incorrect password**. Run Step 3 again. and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="56ccb-p109">* *Microsoft Azure Active Directory Module for Windows PowerShell 需要的 Microsoft.NET Framework 3.5。* 在您電腦 * * 啟用 x * 功能。很有可能您的電腦已安裝的較新版本 (例如 4 或 4.5。* x *），但回溯相容性與較舊版本的.NET Framework 可以啟用或停用。如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="56ccb-p109">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.* x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.* x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="56ccb-157">針對 Windows Server 2012 或 Windows Server 2012 R2，請參閱[使用新增角色及功能精靈來啟用 .NET Framework 3.5](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span><span class="sxs-lookup"><span data-stu-id="56ccb-157">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="56ccb-158">針對 Windows 8 或 Windows 8.1，請參閱[在 Windows 8 或 8.1 上安裝 .NET Framework 3.5](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span><span class="sxs-lookup"><span data-stu-id="56ccb-158">For Windows 8 or Windows 8.1, see [Installing the .NET Framework 3.5 on Windows 8 or 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span></span>
    
  - <span data-ttu-id="56ccb-159">針對 Windows 7 或 Windows Server 2008 R2，請參閱[您無法開啟 Windows PowerShell 的 Azure Active Directory 模組](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span><span class="sxs-lookup"><span data-stu-id="56ccb-159">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>

  - <span data-ttu-id="56ccb-160">Windows 10、 Windows 8.1 及 Windows 8，請參閱[安裝 Windows 10、 Windows 8.1 及 Windows 8 上.NET Framework 3.5](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)</span><span class="sxs-lookup"><span data-stu-id="56ccb-160">For Windows 10, Windows 8.1, and Windows 8, see [Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)</span></span>

  
- <span data-ttu-id="56ccb-p110">**您的 Windows PowerShell 的 Microsoft Azure Active Directory 模組 版本可能已過期。** 若要檢查，請在 Office 365 PowerShell 或 Windows PowerShell 的 Microsoft Azure Active Directory 模組 中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="56ccb-p110">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="56ccb-163">如果傳回的版本號碼低於 1.0.8070.2 值，請將 Windows PowerShell 的 Microsoft Azure Active Directory 模組 解除安裝，然後從步驟 1 中的連結安裝最新版本。</span><span class="sxs-lookup"><span data-stu-id="56ccb-163">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="56ccb-164">**如果您收到連線錯誤，請參閱本主題：** [「Connect-MsolService：擲回類型例外狀況」錯誤](https://go.microsoft.com/fwlink/p/?LinkId=532377)。</span><span class="sxs-lookup"><span data-stu-id="56ccb-164">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="56ccb-165">See also</span><span class="sxs-lookup"><span data-stu-id="56ccb-165">See also</span></span>

- [<span data-ttu-id="56ccb-166">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="56ccb-166">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="56ccb-167">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="56ccb-167">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="56ccb-168">在單一 Windows PowerShell 視窗中連線至所有 Office 365 服務</span><span class="sxs-lookup"><span data-stu-id="56ccb-168">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [<span data-ttu-id="56ccb-169">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="56ccb-169">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [<span data-ttu-id="56ccb-170">Connect-MsolService</span><span class="sxs-lookup"><span data-stu-id="56ccb-170">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

