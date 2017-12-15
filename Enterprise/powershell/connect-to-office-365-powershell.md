---
title: "連線至 Office 365 PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- DecEntMigration
- apr17entnews
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: "摘要： 連線至 Office 365 組織使用 Office 365 PowerShell 從命令列執行 Office 365 admin center 工作。"
ms.openlocfilehash: 3ac368a3d3584c15e1d0c26104616e8258a78e7b
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="45928-103">連線至 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="45928-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="45928-104">**摘要：**連線至 Office 365 組織使用 Office 365 PowerShell 從命令列執行 Office 365 管理工作。</span><span class="sxs-lookup"><span data-stu-id="45928-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform Office 365 administration tasks from the command line.</span></span>
  
<span data-ttu-id="45928-p101">Office 365 PowerShell 可讓您可以從命令列管理您的 Office 365 設定。連線至 Office 365 PowerShell 是個簡單三個步驟程序安裝必要的軟體、 執行必要的軟體，然後連線至 Office 365 組織其中。</span><span class="sxs-lookup"><span data-stu-id="45928-p101">Office 365 PowerShell lets you to manage your Office 365 settings from the command line. Connecting to Office 365 PowerShell is a simple three-step process where you install the required software, run the required software, and then connect to your Office 365 organization.</span></span> 

<span data-ttu-id="45928-107">請注意這些連線指示主題[Azure ActiveDirectory (MSOnline)](https://go.microsoft.com/fwlink/p/?LinkId=528113)相同。</span><span class="sxs-lookup"><span data-stu-id="45928-107">Note that these connection instructions are the same as those in the topic [Azure ActiveDirectory (MSOnline)](https://go.microsoft.com/fwlink/p/?LinkId=528113).</span></span>
  
> [!TIP]
> <span data-ttu-id="45928-p102">**PowerShell 的新功能吗？**請參閱[視訊 PowerShell 概觀 （英文)](http://technet.microsoft.com/library/https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx)、 LinkedIn 學習由致力提供給您。</span><span class="sxs-lookup"><span data-stu-id="45928-p102">**New to PowerShell?** See a [video Overview of PowerShell](http://technet.microsoft.com/library/https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="45928-110">開始之前有哪些須知？</span><span class="sxs-lookup"><span data-stu-id="45928-110">What do you need to know before you begin?</span></span>

- <span data-ttu-id="45928-111">預估完成時間：5 分鐘</span><span class="sxs-lookup"><span data-stu-id="45928-111">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="45928-112">您可以使用下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="45928-112">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="45928-113">Windows 10、Windows 8.1、Windows 8 或 Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="45928-113">Windows 10, Windows 8.1, Windows 8 or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="45928-114">Windows Server 2016、Windows Server 2012 R2、Windows Server 2012 或 Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="45928-114">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="45928-p103">使用 Windows 的 64 位元版本。支援 32 位元版本 Microsoft Azure Active Directory Module for Windows PowerShell 已停用在 2014 年 10 月。</span><span class="sxs-lookup"><span data-stu-id="45928-p103">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="45928-p104">Office 365 搭配使用或學校您使用這些程序需求是 Office 365 系統管理員角色成員的帳戶。如需詳細資訊，請參閱 ＜[關於 Office 365 系統管理員角色](https://go.microsoft.com/fwlink/p/?LinkId=532367)。</span><span class="sxs-lookup"><span data-stu-id="45928-p104">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>
    
## <a name="step-1-install-required-software"></a><span data-ttu-id="45928-119">步驟 1：安裝必要的軟體</span><span class="sxs-lookup"><span data-stu-id="45928-119">Step 1: Install required software</span></span>

<span data-ttu-id="45928-p105">這些步驟只需您在電腦上執行一次，而不必在每次連線時執行。不過，您可能需要定期安裝較新的軟體版本。</span><span class="sxs-lookup"><span data-stu-id="45928-p105">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="45928-122">安裝 64 位元版本的 Microsoft Online Services 登入小幫手： [Microsoft Online Services 登入小幫手的 IT 專業人員 RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152)。</span><span class="sxs-lookup"><span data-stu-id="45928-122">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="45928-123">以這些步驟安裝 64 位元版本的 Windows PowerShell 的 Microsoft Azure Active Directory 模組：</span><span class="sxs-lookup"><span data-stu-id="45928-123">Install the 64-bit version of the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="45928-124">開啟 [Azure Active Directory 連線](http://connect.microsoft.com/site1164/Downloads/DownloadDetails.aspx?DownloadID=59185)網頁。</span><span class="sxs-lookup"><span data-stu-id="45928-124">Open the [Azure Active Directory Connection](http://connect.microsoft.com/site1164/Downloads/DownloadDetails.aspx?DownloadID=59185) web page.</span></span>
    
  - <span data-ttu-id="45928-125">在 [**檔案下載**] 頁面底部，對於**AdministrationConfig-V1.1.166.0-GA.msi**檔案中，按一下 [**下載**並安裝它。</span><span class="sxs-lookup"><span data-stu-id="45928-125">In **Files in Download** at the bottom of the page, click **Download** for the **AdministrationConfig-V1.1.166.0-GA.msi** file, and then install it.</span></span>
    
## <a name="step-2-open-the-windows-azure-active-directory-module"></a><span data-ttu-id="45928-126">步驟 2︰開啟 Windows Azure Active Directory 模組</span><span class="sxs-lookup"><span data-stu-id="45928-126">Step 2: Open the Windows Azure Active Directory Module</span></span>

1. <span data-ttu-id="45928-127">根據您的 Windows 版本，使用下列其中一種方法，尋找並開啟 Windows PowerShell 的 Microsoft Azure Active Directory 模組：</span><span class="sxs-lookup"><span data-stu-id="45928-127">Find and open the Microsoft Azure Active Directory Module for Windows PowerShell by using one of the following methods based on your version of Windows:</span></span>
    
  - <span data-ttu-id="45928-128">**[開始] 功能表**從桌面，按一下 [**開始**]，然後輸入 Azure。</span><span class="sxs-lookup"><span data-stu-id="45928-128">**Start menu** From the desktop, click **Start**, and then type Azure.</span></span>
    
  - <span data-ttu-id="45928-129">**沒有 [開始] 功能表** 使用以下任何一種方法，搜尋Azure：</span><span class="sxs-lookup"><span data-stu-id="45928-129">**No Start menu** Search forAzure using any of these methods:</span></span>
    
  - <span data-ttu-id="45928-130">在 [開始] 畫面上，按一下空白區域，然後輸入 Azure。</span><span class="sxs-lookup"><span data-stu-id="45928-130">On the Start screen, click an empty area, and type Azure.</span></span>
    
  - <span data-ttu-id="45928-p106">在桌面或 [開始] 畫面上，按 Windows 鍵 + Q。在 [搜尋] 快速鍵中，輸入 Azure。</span><span class="sxs-lookup"><span data-stu-id="45928-p106">On the desktop or the Start screen, press the Windows key+Q. In the Search charm, type Azure.</span></span>
    
  - <span data-ttu-id="45928-p107">在桌面或 [開始] 畫面，將游標移至右上角或往撥動以顯示圖標螢幕的右邊緣從左。選取搜尋左，然後輸入**Azure**。</span><span class="sxs-lookup"><span data-stu-id="45928-p107">On the desktop or the Start screen, move your cursor to the upper-right corner, or swipe left from the right edge of the screen to show the charms. Select the Search charm, and type **Azure**.</span></span>
    
2. <span data-ttu-id="45928-135">在結果中，按一下 **Windows PowerShell 的 Microsoft Azure Active Directory 模組**。</span><span class="sxs-lookup"><span data-stu-id="45928-135">In the results, click **Microsoft Azure Active Directory Module for Windows PowerShell**.</span></span>
    
## <a name="step-3-connect-to-your-office-365-subscription"></a><span data-ttu-id="45928-136">步驟 3：步驟 3：連線到您的 Office 365 訂閱</span><span class="sxs-lookup"><span data-stu-id="45928-136">Step 3: Connect to your Office 365 subscription</span></span>
<span data-ttu-id="45928-137"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="45928-137"><a name="step3"> </a></span></span>

<span data-ttu-id="45928-138">只以「帳戶名稱和密碼」進行連線：</span><span class="sxs-lookup"><span data-stu-id="45928-138">To connect with just an  *account name and password*  :</span></span>
  
1. <span data-ttu-id="45928-139">在 **Windows PowerShell 的 Microsoft Azure Active Directory 模組** 命令視窗中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="45928-139">In the **Microsoft Azure Active Directory Module for Windows PowerShell** command window, run the following commands.</span></span>
    
  ```
  $UserCredential = Get-Credential
Connect-MsolService -Credential $UserCredential
  ```

2. <span data-ttu-id="45928-140">在 [Windows PowerShell 認證要求] 對話方塊中，輸入您的 Office 365工作或學校帳戶 使用者名稱和密碼，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="45928-140">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
<span data-ttu-id="45928-141">以「多重要素驗證 (MFA)」進行連線：</span><span class="sxs-lookup"><span data-stu-id="45928-141">To connect with  *multi-factor authentication (MFA)*  :</span></span>
  
1. <span data-ttu-id="45928-142">在 **Windows PowerShell 的 Microsoft Azure Active Directory 模組** 命令視窗中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="45928-142">In the **Microsoft Azure Active Directory Module for Windows PowerShell** command window, run the following command.</span></span>
    
  ```
  Connect-MsolService
  ```

2. <span data-ttu-id="45928-143">在 [Azure Active Directory PowerShell] 對話方塊中，鍵入您的 Office 365工作或學校帳戶 使用者名稱和密碼，然後按一下 [登入]。</span><span class="sxs-lookup"><span data-stu-id="45928-143">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
3. <span data-ttu-id="45928-144">遵循 [Azure Active Directory PowerShell] 對話方塊中的指示，提供其他驗證資訊 (例如驗證碼)，然後按一下 [登入]。</span><span class="sxs-lookup"><span data-stu-id="45928-144">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
## <a name="how-do-you-know-this-worked"></a><span data-ttu-id="45928-145">如何知道這是否正常運作？</span><span class="sxs-lookup"><span data-stu-id="45928-145">How do you know this worked?</span></span>
<span data-ttu-id="45928-146"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="45928-146"><a name="step3"> </a></span></span>

<span data-ttu-id="45928-p108">如果您未收到任何錯誤，便已順利連線。若要做快速測試，您可以執行一個 Office 365 Cmdlet (例如 **Get-MsolUser** )，然後檢視結果。</span><span class="sxs-lookup"><span data-stu-id="45928-p108">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="45928-149">如果出現錯誤，請檢查下列需求：</span><span class="sxs-lookup"><span data-stu-id="45928-149">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="45928-p109">**密碼錯誤是常見的問題** 。再次執行步驟 3，並密切注意您輸入的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="45928-p109">**A common problem is an incorrect password**. Run Step 3 again. and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="45928-p110">**Windows PowerShell 的 Microsoft Azure Active Directory 模組 要求在您的電腦上啟用 Microsoft .NET Framework 3.5. _x_ 功能** 。您的電腦可能已安裝了較新的版本 (例如 4 或 4.5. _x_)，但可以啟用或停用舊版 .NET Framework 的回溯相容性。如需相關資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="45928-p110">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5. _x_ feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5. _x_), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="45928-157">Windows Server 2012 或 Windows Server 2012 R2，請參閱[使用 [新增角色及功能精靈] 來啟用.NET Framework 3.5](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span><span class="sxs-lookup"><span data-stu-id="45928-157">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="45928-158">Windows 8 或 Windows 8.1，請參閱[安裝 Windows 8 或 8.1.NET Framework 3.5](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span><span class="sxs-lookup"><span data-stu-id="45928-158">For Windows 8 or Windows 8.1, see [Installing the .NET Framework 3.5 on Windows 8 or 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span></span>
    
  - <span data-ttu-id="45928-159">Windows 7 或 Windows Server 2008 R2，請參閱[您無法開啟 Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span><span class="sxs-lookup"><span data-stu-id="45928-159">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>
    
- <span data-ttu-id="45928-p111">**您的 Windows PowerShell 的 Microsoft Azure Active Directory 模組 版本可能已過期。** 若要檢查，請在 Office 365 PowerShell 或 Windows PowerShell 的 Microsoft Azure Active Directory 模組 中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="45928-p111">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="45928-162">如果傳回的版本號碼低於 1.0.8070.2 值，請將 Windows PowerShell 的 Microsoft Azure Active Directory 模組 解除安裝，然後從步驟 1 中的連結安裝最新版本。</span><span class="sxs-lookup"><span data-stu-id="45928-162">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="45928-163">**如果您收到連線錯誤，請參閱本主題：**["Connect-msolservice： 類型的例外狀況 」 錯誤](https://go.microsoft.com/fwlink/p/?LinkId=532377)。</span><span class="sxs-lookup"><span data-stu-id="45928-163">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    
## <a name="connect-with-the-azure-active-directory-v2-powershell-module"></a><span data-ttu-id="45928-164">與 Azure Active Directory V2 PowerShell 模組連接</span><span class="sxs-lookup"><span data-stu-id="45928-164">Connect with the Azure Active Directory V2 PowerShell module</span></span>
<span data-ttu-id="45928-165"><a name="ConnectV2"> </a></span><span class="sxs-lookup"><span data-stu-id="45928-165"><a name="ConnectV2"> </a></span></span>

<span data-ttu-id="45928-166">針對需要 [Azure Active Directory V2 PowerShell 模組](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)中新 Cmdlet 的程序，使用這些步驟來安裝模組，並連接至您的 Office 365 訂閱：</span><span class="sxs-lookup"><span data-stu-id="45928-166">For procedures that require the new cmdlets in the [Azure Active Directory V2 PowerShell module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory), use these steps to install the module and connect to your Office 365 subscription:</span></span>
  
1. <span data-ttu-id="45928-167">開啟提升權限的 Windows PowerShell 命令提示字元 (以系統管理員身分執行 Windows PowerShell)。</span><span class="sxs-lookup"><span data-stu-id="45928-167">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="45928-168">在 [系統管理員：Windows PowerShell] 命令視窗中，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="45928-168">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD 
  ```

<span data-ttu-id="45928-169">如果出現提示，指出需安裝來自不受信任存放庫的模組，請輸入 **Y**，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="45928-169">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>
    
3. <span data-ttu-id="45928-170">新的模組安裝完成時，使用這些命令連接至您的 Office 365 訂閱：</span><span class="sxs-lookup"><span data-stu-id="45928-170">When the installation of the new module is complete, use these commands to connect to your Office 365 subscription:</span></span>
    
  -  <span data-ttu-id="45928-171">使用帳戶名稱和密碼：</span><span class="sxs-lookup"><span data-stu-id="45928-171">With an *account name and password*  :</span></span>
    
  ```
  $UserCredential = Get-Credential
Connect-AzureAD -Credential $UserCredential
  ```

 <span data-ttu-id="45928-172">在 [Windows PowerShell 認證要求] 對話方塊中，輸入您的 Office 365工作或學校帳戶 使用者名稱和密碼，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="45928-172">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
  - <span data-ttu-id="45928-173">使用 Multi-Factor Authentication (MFA)：</span><span class="sxs-lookup"><span data-stu-id="45928-173">With  *multi-factor authentication (MFA)*  :</span></span>
    
  ```
  Connect-AzureAD
  ```

<span data-ttu-id="45928-174">在 [Azure Active Directory PowerShell] 對話方塊中，鍵入您的 Office 365工作或學校帳戶 使用者名稱和密碼，然後按一下 [登入]。</span><span class="sxs-lookup"><span data-stu-id="45928-174">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
<span data-ttu-id="45928-175">遵循 [Azure Active Directory PowerShell] 對話方塊中的指示，提供其他驗證資訊 (例如驗證碼)，然後按一下 [登入]。</span><span class="sxs-lookup"><span data-stu-id="45928-175">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
<span data-ttu-id="45928-176">連線之後，您可以對 [Azure Active Directory V2 PowerShell 模組](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)使用新的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="45928-176">After connecting, you can use the new cmdlets for the [Azure Active Directory V2 PowerShell module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="45928-177">See also</span><span class="sxs-lookup"><span data-stu-id="45928-177">See also</span></span>

#### 

[<span data-ttu-id="45928-178">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="45928-178">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="45928-179">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="45928-179">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="45928-180">在單一 Windows PowerShell 視窗中連線至所有 Office 365 服務</span><span class="sxs-lookup"><span data-stu-id="45928-180">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
#### 

[<span data-ttu-id="45928-181">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="45928-181">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
  
[<span data-ttu-id="45928-182">連線 MsolService</span><span class="sxs-lookup"><span data-stu-id="45928-182">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

