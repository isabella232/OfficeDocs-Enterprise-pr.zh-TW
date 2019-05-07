---
title: 連線至 Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: 摘要： 連線至 Office 365 組織使用 Office 365 PowerShell 來從命令列執行系統管理中心工作。
ms.openlocfilehash: 4c70f067558773ce7e2a6e27bab78f5c64965872
ms.sourcegitcommit: 0516a15c72f4bc8423a1d8112fd4d3e5f69896c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2019
ms.locfileid: "33639774"
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="1bcde-103">連線至 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1bcde-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="1bcde-104">**摘要：** 連線至 Office 365 組織使用 Office 365 PowerShell 來從命令列執行管理工作。</span><span class="sxs-lookup"><span data-stu-id="1bcde-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform administration tasks from the command line.</span></span>
  
<span data-ttu-id="1bcde-105">Office 365 PowerShell 可讓您從命令列管理您的 Office 365 設定。</span><span class="sxs-lookup"><span data-stu-id="1bcde-105">Office 365 PowerShell lets you manage your Office 365 settings from the command line.</span></span> <span data-ttu-id="1bcde-106">連線至 Office 365 PowerShell 是簡單的程序其中安裝必要的軟體，然後連線到 Office 365 組織。</span><span class="sxs-lookup"><span data-stu-id="1bcde-106">Connecting to Office 365 PowerShell is a simple process where you install the required software and then connect to your Office 365 organization.</span></span> 

<span data-ttu-id="1bcde-107">有兩個版本的您用來連線到 Office 365 及管理使用者帳戶、 群組和授權的 PowerShell 模組：</span><span class="sxs-lookup"><span data-stu-id="1bcde-107">There are two versions of the PowerShell module that you use to connect to Office 365 and administer user accounts, groups, and licenses:</span></span>

- <span data-ttu-id="1bcde-108">Azure Active Directory PowerShell 的圖表 （cmdlet 名稱中包含**AzureAD** ）</span><span class="sxs-lookup"><span data-stu-id="1bcde-108">Azure Active Directory PowerShell for Graph (cmdlets include **AzureAD** in their name)</span></span> 
- <span data-ttu-id="1bcde-109">Microsoft Azure Active Directory 模組的 Windows PowerShell （cmdlet 名稱中包含**MSol** ）</span><span class="sxs-lookup"><span data-stu-id="1bcde-109">Microsoft Azure Active Directory Module for Windows PowerShell (cmdlets include **MSol** in their name)</span></span> 

<span data-ttu-id="1bcde-110">本文章的日期，PowerShell 的 Azure Active Directory 針對 Graph 模組不會完全取代中的使用者、 群組和授權管理的 Microsoft Azure Active Directory 模組的 Windows PowerShell 模組之 cmdlet 的功能.</span><span class="sxs-lookup"><span data-stu-id="1bcde-110">As of the date of this article, the Azure Active Directory PowerShell for Graph module does not completely replace the functionality in the cmdlets of Microsoft Azure Active Directory Module for Windows PowerShell module for user, group, and license administration.</span></span> <span data-ttu-id="1bcde-111">在許多情況下，您需要使用兩個版本。</span><span class="sxs-lookup"><span data-stu-id="1bcde-111">In many cases, you need to use both versions.</span></span> <span data-ttu-id="1bcde-112">您安全地可以在同一部電腦上安裝這兩個版本。</span><span class="sxs-lookup"><span data-stu-id="1bcde-112">You can safely install both versions on the same computer.</span></span>

> [!TIP]
> <span data-ttu-id="1bcde-p103">**第一次使用 PowerShell？** 請參閱 LinkedIn Learning 為您提供的 [PowerShell 概觀影片](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx)。</span><span class="sxs-lookup"><span data-stu-id="1bcde-p103">**New to PowerShell?** See a [video Overview of PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="1bcde-115">開始之前有哪些須知？</span><span class="sxs-lookup"><span data-stu-id="1bcde-115">What do you need to know before you begin?</span></span>

- <span data-ttu-id="1bcde-116">預估完成時間：5 分鐘</span><span class="sxs-lookup"><span data-stu-id="1bcde-116">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="1bcde-117">您可以使用下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="1bcde-117">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="1bcde-118">Windows 10、 Windows 8.1、 Windows 8 或 Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="1bcde-118">Windows 10, Windows 8.1, Windows 8, or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="1bcde-119">Windows Server 2019、 Windows Server 2016、 Windows Server 2012 R2、 Windows Server 2012 或 Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="1bcde-119">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="1bcde-p104">請使用 64 位元的 Windows 版本。對 Windows PowerShell 的 Microsoft Azure Active Directory 模組 32 位元版本的支援已在 2014 年 10 月終止。</span><span class="sxs-lookup"><span data-stu-id="1bcde-p104">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="1bcde-122">這些程序被適用於使用者身為 Office 365 系統管理員角色的成員。</span><span class="sxs-lookup"><span data-stu-id="1bcde-122">These procedures are intended for users who are members of an Office 365 admin role.</span></span> <span data-ttu-id="1bcde-123">如需詳細資訊，請參閱[關於 Office 365 系統管理員角色](https://go.microsoft.com/fwlink/p/?LinkId=532367)。</span><span class="sxs-lookup"><span data-stu-id="1bcde-123">For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="1bcde-124">使用 PowerShell 的 Azure Active Directory 針對 Graph 模組連線</span><span class="sxs-lookup"><span data-stu-id="1bcde-124">Connect with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="1bcde-125">\*\* [Azure Active Directory PowerShell 的 Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)模組中的命令 azuread 指令程式名稱。\*\*</span><span class="sxs-lookup"><span data-stu-id="1bcde-125">Commands in the [Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) module have **AzureAD** in their cmdlet name.</span></span>

<span data-ttu-id="1bcde-126">如需針對 Graph 模組需要 Active Directory PowerShell 的 Azure 中的新 cmdlet 的程序，使用下列步驟來安裝模組，並連線至您的 Office 365 訂閱。</span><span class="sxs-lookup"><span data-stu-id="1bcde-126">For procedures that require the new cmdlets in the Azure Active Directory PowerShell for Graph module, use these steps to install the module and connect to your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="1bcde-127">如需不同版本的 Microsoft Windows 支援的相關資訊，請參閱[Azure Active Directory PowerShell 針對 Graph 模組](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)。</span><span class="sxs-lookup"><span data-stu-id="1bcde-127">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="1bcde-128">步驟 1：安裝必要的軟體</span><span class="sxs-lookup"><span data-stu-id="1bcde-128">Step 1: Install required software</span></span>

<span data-ttu-id="1bcde-p106">這些步驟只需您在電腦上執行一次，而不必在每次連線時執行。不過，您可能需要定期安裝較新的軟體版本。</span><span class="sxs-lookup"><span data-stu-id="1bcde-p106">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1. <span data-ttu-id="1bcde-131">開啟提升權限的 Windows PowerShell 命令提示字元 (以系統管理員身分執行 Windows PowerShell)。</span><span class="sxs-lookup"><span data-stu-id="1bcde-131">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="1bcde-132">在 [系統管理員：Windows PowerShell] 命令視窗中，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="1bcde-132">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD
  ```

<span data-ttu-id="1bcde-133">如果出現提示，指出需安裝來自不受信任存放庫的模組，請輸入 **Y**，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="1bcde-133">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="1bcde-134">步驟 2： 連線到 Office 365 訂閱的 Azure AD</span><span class="sxs-lookup"><span data-stu-id="1bcde-134">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="1bcde-135">若要連接至 Office 365 訂用帳戶使用的帳戶名稱和密碼或*多重要素驗證 (MFA)* 與 Azure AD，請執行這些命令的其中一個從 Windows PowerShell 命令提示字元 （不需要為提高權限）。</span><span class="sxs-lookup"><span data-stu-id="1bcde-135">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="1bcde-136">**Office 365 雲端**</span><span class="sxs-lookup"><span data-stu-id="1bcde-136">**Office 365 cloud**</span></span> | <span data-ttu-id="1bcde-137">**Command**</span><span class="sxs-lookup"><span data-stu-id="1bcde-137">**Command**</span></span> |
| <span data-ttu-id="1bcde-138">Office 365 全球 （+ GCC）</span><span class="sxs-lookup"><span data-stu-id="1bcde-138">Office 365 Worldwide (+GCC)</span></span> | `Connect-AzureAD` |
| <span data-ttu-id="1bcde-139">21 Vianet 所運作的 office 365</span><span class="sxs-lookup"><span data-stu-id="1bcde-139">Office 365 operated by 21 Vianet</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| <span data-ttu-id="1bcde-140">Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="1bcde-140">Office 365 Germany</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| <span data-ttu-id="1bcde-141">Office 365 美國政府 DoD 和 Office 365 US Government GCC 高</span><span class="sxs-lookup"><span data-stu-id="1bcde-141">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

<span data-ttu-id="1bcde-142">在 [**登入您的帳戶**] 對話方塊中，輸入您的 Office 365 工作或學校帳戶使用者名稱和密碼，，然後按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="1bcde-142">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="1bcde-143">如果您使用 MFA，請遵循額外的對話方塊中的指示，提供更多的驗證資訊，例如驗證碼。</span><span class="sxs-lookup"><span data-stu-id="1bcde-143">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>


<span data-ttu-id="1bcde-144">連線之後，您可以使用新的 cmdlet 的[Azure Active Directory PowerShell 針對 Graph 模組](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)。</span><span class="sxs-lookup"><span data-stu-id="1bcde-144">After connecting, you can use the new cmdlets for the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="1bcde-145">與適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組連線</span><span class="sxs-lookup"><span data-stu-id="1bcde-145">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="1bcde-146">在適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組中，命令的 Cmdlet 名稱會包含 **Msol**。</span><span class="sxs-lookup"><span data-stu-id="1bcde-146">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="1bcde-147">步驟 1：安裝必要的軟體</span><span class="sxs-lookup"><span data-stu-id="1bcde-147">Step 1: Install required software</span></span>

<span data-ttu-id="1bcde-p107">這些步驟只需您在電腦上執行一次，而不必在每次連線時執行。不過，您可能需要定期安裝較新的軟體版本。</span><span class="sxs-lookup"><span data-stu-id="1bcde-p107">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="1bcde-150">安裝 64 位元版本的 Microsoft Online Services 登入小幫手：[適用於 IT 專業人員的 Microsoft Online Services 登入小幫手 RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152)。</span><span class="sxs-lookup"><span data-stu-id="1bcde-150">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="1bcde-151">以下列步驟安裝適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組：</span><span class="sxs-lookup"><span data-stu-id="1bcde-151">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="1bcde-152">開啟提升權限的 Windows PowerShell 命令提示字元 (以系統管理員身分執行 Windows PowerShell)。</span><span class="sxs-lookup"><span data-stu-id="1bcde-152">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
  - <span data-ttu-id="1bcde-153">執行 **Install-Module MSOnline** 命令。</span><span class="sxs-lookup"><span data-stu-id="1bcde-153">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="1bcde-154">如果系統提示您安裝 NuGet 提供者，請輸入 **Y**，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="1bcde-154">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="1bcde-155">如果系統提示您從 PSGallery 安裝模組，請輸入 **Y**，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="1bcde-155">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="1bcde-156">步驟 2： 連線到 Office 365 訂閱的 Azure AD</span><span class="sxs-lookup"><span data-stu-id="1bcde-156">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="1bcde-157">若要連接至 Office 365 訂用帳戶使用的帳戶名稱和密碼或*多重要素驗證 (MFA)* 與 Azure AD，請執行這些命令的其中一個從 Windows PowerShell 命令提示字元 （不需要為提高權限）。</span><span class="sxs-lookup"><span data-stu-id="1bcde-157">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="1bcde-158">**Office 365 雲端**</span><span class="sxs-lookup"><span data-stu-id="1bcde-158">**Office 365 cloud**</span></span> | <span data-ttu-id="1bcde-159">**Command**</span><span class="sxs-lookup"><span data-stu-id="1bcde-159">**Command**</span></span> |
| <span data-ttu-id="1bcde-160">Office 365 全球 （+ GCC）</span><span class="sxs-lookup"><span data-stu-id="1bcde-160">Office 365 Worldwide (+GCC)</span></span> | `Connect-MsolService` |
| <span data-ttu-id="1bcde-161">21 Vianet 所運作的 office 365</span><span class="sxs-lookup"><span data-stu-id="1bcde-161">Office 365 operated by 21 Vianet</span></span> | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| <span data-ttu-id="1bcde-162">Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="1bcde-162">Office 365 Germany</span></span> | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| <span data-ttu-id="1bcde-163">Office 365 美國政府 DoD 和 Office 365 US Government GCC 高</span><span class="sxs-lookup"><span data-stu-id="1bcde-163">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

<span data-ttu-id="1bcde-164">在 [**登入您的帳戶**] 對話方塊中，輸入您的 Office 365 工作或學校帳戶使用者名稱和密碼，，然後按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="1bcde-164">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="1bcde-165">如果您使用 MFA，請遵循額外的對話方塊中的指示，提供更多的驗證資訊，例如驗證碼。</span><span class="sxs-lookup"><span data-stu-id="1bcde-165">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="1bcde-166">如何知道這是否正常運作？</span><span class="sxs-lookup"><span data-stu-id="1bcde-166">How do you know this worked?</span></span>

<span data-ttu-id="1bcde-p108">如果您未收到任何錯誤，便已順利連線。若要做快速測試，您可以執行一個 Office 365 Cmdlet (例如 **Get-MsolUser** )，然後檢視結果。</span><span class="sxs-lookup"><span data-stu-id="1bcde-p108">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="1bcde-169">如果出現錯誤，請檢查下列需求：</span><span class="sxs-lookup"><span data-stu-id="1bcde-169">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="1bcde-170">**常見的問題是不正確的密碼**。</span><span class="sxs-lookup"><span data-stu-id="1bcde-170">**A common problem is an incorrect password**.</span></span> <span data-ttu-id="1bcde-171">再次執行步驟 2。</span><span class="sxs-lookup"><span data-stu-id="1bcde-171">Run Step 2 again.</span></span> <span data-ttu-id="1bcde-172">和密切注意您輸入使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="1bcde-172">and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="1bcde-173">\* *Microsoft Azure Active Directory 的 Windows PowerShell 模組需要 Microsoft.NET Framework 3.5。* 啟用上您的電腦 \* \* x \* 功能。可能的電腦上已安裝的較新版本 (例如 4 或 4.5。\* x \*），但與.NET Framework 的較舊版本的相容性回溯可以啟用或停用。</span><span class="sxs-lookup"><span data-stu-id="1bcde-173">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.* x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.* x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled.</span></span> <span data-ttu-id="1bcde-174">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="1bcde-174">For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="1bcde-175">針對 Windows Server 2012 或 Windows Server 2012 R2，請參閱[使用新增角色及功能精靈來啟用 .NET Framework 3.5](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span><span class="sxs-lookup"><span data-stu-id="1bcde-175">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="1bcde-176">針對 Windows 7 或 Windows Server 2008 R2，請參閱[您無法開啟 Windows PowerShell 的 Azure Active Directory 模組](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span><span class="sxs-lookup"><span data-stu-id="1bcde-176">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>

  - <span data-ttu-id="1bcde-177">Windows 10、 Windows 8.1 和 Windows 8，請參閱 <<c0>安裝 Windows 10、 Windows 8.1 和 Windows 8 上.NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="1bcde-177">For Windows 10, Windows 8.1, and Windows 8, see [Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)</span></span>

  
- <span data-ttu-id="1bcde-p111">**您的 Windows PowerShell 的 Microsoft Azure Active Directory 模組 版本可能已過期。** 若要檢查，請在 Office 365 PowerShell 或 Windows PowerShell 的 Microsoft Azure Active Directory 模組 中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="1bcde-p111">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="1bcde-180">如果傳回的版本號碼低於 1.0.8070.2 值，請將 Windows PowerShell 的 Microsoft Azure Active Directory 模組 解除安裝，然後從步驟 1 中的連結安裝最新版本。</span><span class="sxs-lookup"><span data-stu-id="1bcde-180">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="1bcde-181">**如果您收到連線錯誤，請參閱本主題：** [「Connect-MsolService：擲回類型例外狀況」錯誤](https://go.microsoft.com/fwlink/p/?LinkId=532377)。</span><span class="sxs-lookup"><span data-stu-id="1bcde-181">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="1bcde-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bcde-182">See also</span></span>

- [<span data-ttu-id="1bcde-183">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="1bcde-183">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="1bcde-184">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1bcde-184">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="1bcde-185">在單一 Windows PowerShell 視窗中連線至所有 Office 365 服務</span><span class="sxs-lookup"><span data-stu-id="1bcde-185">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [<span data-ttu-id="1bcde-186">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="1bcde-186">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [<span data-ttu-id="1bcde-187">Connect-MsolService</span><span class="sxs-lookup"><span data-stu-id="1bcde-187">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

