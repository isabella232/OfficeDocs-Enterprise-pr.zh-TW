---
title: "在單一 Windows PowerShell 視窗中連線至所有 Office 365 服務"
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
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: "摘要： 連線至單一 Windows PowerShell 視窗中的所有 Office 365 服務的 Windows PowerShell。"
ms.openlocfilehash: d11487ae1c95cb0d36221e7ce572ed55052d98eb
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="cec2c-103">在單一 Windows PowerShell 視窗中連線至所有 Office 365 服務</span><span class="sxs-lookup"><span data-stu-id="cec2c-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

 <span data-ttu-id="cec2c-104">**摘要：**而不是管理在個別的 PowerShell 主控台視窗中的不同 Office 365 服務，您可以連線至 Office 365 的所有服務和管理它們從單一主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="cec2c-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span></span>
  
<span data-ttu-id="cec2c-p101">當您使用 PowerShell 管理 Office 365 時，有可能有最多可以有五個不同 Windows PowerShell 工作階段，同時對應至 Office 365 系統管理中心、 SharePoint Online、 Exchange Online、 商務 online Skype 及安全性&amp;規範中心。使用個別的 Windows PowerShell 工作階段中的五個不同的連接方法，您的桌面可能看起來如下：</span><span class="sxs-lookup"><span data-stu-id="cec2c-p101">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Office 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center. With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![一次執行五個 Windows PowerShell 主控台](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="cec2c-p102">這不是因為您不能交換資料之間的跨服務管理那些五個 windows 管理 Office 365 的最佳。本主題說明如何使用單一執行個體您可以從中管理 Office 365、 商務 Online、 Exchange Online、 SharePoint online、 Skype 和安全性的 Windows PowerShell&amp;規範中心。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p102">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management. This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="cec2c-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="cec2c-110">Before you begin</span></span>
<span data-ttu-id="cec2c-111"><a name="BeforeYouBegin"> </a></span><span class="sxs-lookup"><span data-stu-id="cec2c-111"></span></span>

<span data-ttu-id="cec2c-112">您可以從單一執行個體的 Windows PowerShell 管理 Office 365 的所有之前，請考慮下列先決條件：</span><span class="sxs-lookup"><span data-stu-id="cec2c-112">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="cec2c-p103">Office 365 搭配使用或學校您使用這些程序需求是 Office 365 系統管理員角色成員的帳戶。如需詳細資訊，請參閱 ＜[關於 Office 365 系統管理員角色](https://go.microsoft.com/fwlink/p/?LinkId=532367)。此為 Office 365 PowerShell、 不一定所有其他 Office 365 服務的需求。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p103">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367). This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="cec2c-116">您可以使用下列 Windows 64 位元版本：</span><span class="sxs-lookup"><span data-stu-id="cec2c-116">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="cec2c-117">Windows 10</span><span class="sxs-lookup"><span data-stu-id="cec2c-117">Windows 10</span></span>
    
  - <span data-ttu-id="cec2c-118">Windows 8.1 或 Windows 8</span><span class="sxs-lookup"><span data-stu-id="cec2c-118">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="cec2c-119">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="cec2c-119">Windows Server 2016</span></span>
    
  - <span data-ttu-id="cec2c-120">Windows Server 2012 R2 或 Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="cec2c-120">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="cec2c-121">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="cec2c-121">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="cec2c-122">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="cec2c-122">Windows Server 2008 R2 SP1\*</span></span>
    
    * <span data-ttu-id="cec2c-p104">您需要安裝 Microsoft.NET Framework 4.5。_x_ ，然後任一 Windows Management Framework 3.0 或 Windows Management Framework 4.0。如需詳細資訊，請參閱[安裝.NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868)和[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757)或[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p104">You need to install the Microsoft .NET Framework 4.5. _x_ and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0. For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="cec2c-126">您需要用於 64 位元版本的 Windows 因為 Skype 的需求而商務線上模組及其中一個 Office 365 模組。</span><span class="sxs-lookup"><span data-stu-id="cec2c-126">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="cec2c-127">您必須安裝所需的 Office 365、 SharePoint Online 和 Skype 的商務 Online 模組：</span><span class="sxs-lookup"><span data-stu-id="cec2c-127">You need to install the modules that are required for Office 365, SharePoint Online, and Skype for Business Online:</span></span>
    
  - [<span data-ttu-id="cec2c-128">Microsoft Online Services 登入小幫手，適用於 IT 專業人員 RTW</span><span class="sxs-lookup"><span data-stu-id="cec2c-128">Microsoft Online Service Sign-in Assistant for IT Professionals RTW</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=286152)
    
  - [<span data-ttu-id="cec2c-129">Windows Azure Active Directory Module for Windows PowerShell （64 位元版本）</span><span class="sxs-lookup"><span data-stu-id="cec2c-129">Windows Azure Active Directory Module for Windows PowerShell (64-bit version)</span></span>](https://go.microsoft.com/fwlink/p/?linkid=236297)
    
  - [<span data-ttu-id="cec2c-130">SharePoint Online 管理命令介面</span><span class="sxs-lookup"><span data-stu-id="cec2c-130">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
    
  - [<span data-ttu-id="cec2c-131">Skype Online，企業版 Windows PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="cec2c-131">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  <span data-ttu-id="cec2c-p105">Windows PowerShell 需要為 Skype 的已簽署的指令碼執行商務 Online、 Exchange Online 與安全性設定&amp;規範中心。若要這樣做，請執行下列命令在提升權限的 Windows PowerShell 工作階段 （您可以選取 [**執行系統管理員身分**開啟 Windows PowerShell 視窗）。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p105">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center. To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="cec2c-134">簡短版本 (不含說明的指示)</span><span class="sxs-lookup"><span data-stu-id="cec2c-134">The short version (instructions without explanations)</span></span>
<span data-ttu-id="cec2c-135"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="cec2c-135"></span></span>

<span data-ttu-id="cec2c-p106">本節將展示連線步驟而不作深入說明。如果您有任何問題或需要詳細資訊，您可以閱讀本主題的其餘部分。此處的步驟號碼，會符合該主題的其餘部分中，以步驟編號的小節︰</span><span class="sxs-lookup"><span data-stu-id="cec2c-p106">This section presents the connection steps without in-depth explanations. If you have questions or want more information, you can read rest of the topic. The step numbers here match the step-numbered sections in the rest of the topic:</span></span>
  
1. <span data-ttu-id="cec2c-139">（使用**系統管理員身分執行**） 以管理員身分開啟 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="cec2c-139">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="cec2c-140">執行此命令中，並輸入您的 Office 365 工作或學校帳戶認證。</span><span class="sxs-lookup"><span data-stu-id="cec2c-140">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```
  $credential = Get-Credential
  ```

3. <span data-ttu-id="cec2c-141">執行下列命令以連線至 Office 365。</span><span class="sxs-lookup"><span data-stu-id="cec2c-141">Run these commands to connect to Office 365.</span></span>
    
  ```
  Import-Module MsOnline
  Connect-MsolService -Credential $credential
  ```

4. <span data-ttu-id="cec2c-p107">執行下列命令以連接至 SharePoint Online。取代_\<domainhost >_網域的實際值。例如，用於`litwareinc.onmicrosoft.com`、 _ \<domainhost >_值是`litwareinc`。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p107">Run these commands to connect to SharePoint Online. Replace  _\<domainhost>_ with the actual value for your domain. For example, for `litwareinc.onmicrosoft.com`, the  _\<domainhost>_ value is `litwareinc`.</span></span>
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="cec2c-p108">執行下列命令以連線至 Skype 商務線上。增加的警告`WSMan NetworkDelayms`值預期會在第一次連線和應忽略。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p108">Run these commands to connect to Skype for Business Online. A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="cec2c-147">執行下列命令以連線至 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="cec2c-147">Run these commands to connect to Exchange Online.</span></span>
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

7. <span data-ttu-id="cec2c-148">執行下列命令以連線至安全性&amp;規範中心。</span><span class="sxs-lookup"><span data-stu-id="cec2c-148">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```
  $ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
  Import-PSSession $ccSession -Prefix cc
  ```
> [!NOTE]
> <span data-ttu-id="cec2c-p109">文字前置詞"cc"新增至*所有*安全性&amp;規範中心指令程式名稱，可以執行指令程式可讓存在於 Exchange Online 與安全性&amp;規範中心] 中相同的 Windows PowerShell 工作階段。例如， **Get-rolegroup**變成**Get ccRoleGroup**安全性&amp;規範中心。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p109">The text prefix "cc" is added to  *all*  Security &amp; Compliance Center cmdlet names so you can run cmdlets that exist in both Exchange Online and the Security &amp; Compliance Center in the same Windows PowerShell session. For example, **Get-RoleGroup** becomes **Get-ccRoleGroup** in the Security &amp; Compliance Center.</span></span>
  
<span data-ttu-id="cec2c-p110">以下是單一區塊中的所有命令。指定您的網域主機名稱和一次執行所有它們。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p110">Here are all the commands in a single block. Specify the name of your domain host, and then run them all at one time.</span></span>
  
```
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Import-Module MsOnline
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
Import-PSSession $ccSession -Prefix cc
```

<span data-ttu-id="cec2c-153">當您準備好關閉 Windows PowerShell 視窗時，執行此命令以移除 Skype 作用中的工作階段的商務 Online、 Exchange Online、 SharePoint Online 和安全性&amp;規範中心：</span><span class="sxs-lookup"><span data-stu-id="cec2c-153">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $ccSession ; Disconnect-SPOService
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="cec2c-154">冗長版本 (包含詳細說明的指示)</span><span class="sxs-lookup"><span data-stu-id="cec2c-154">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="cec2c-155"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="cec2c-155"></span></span>

### <a name="step-1-open-windows-powershell-as-an-administrator"></a><span data-ttu-id="cec2c-156">步驟 1︰以系統管理員身分開啟 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="cec2c-156">Step 1: Open Windows PowerShell as an administrator</span></span>
<span data-ttu-id="cec2c-157"><a name="Step1"> </a></span><span class="sxs-lookup"><span data-stu-id="cec2c-157"></span></span>

<span data-ttu-id="cec2c-158">如果您正在執行 Windows 10、 Windows 8、 Windows 8.1、 Windows Server 2016、 Windows Server 2012 R2 或 Windows Server 2012 R2、 執行這項作業：</span><span class="sxs-lookup"><span data-stu-id="cec2c-158">If you're running Windows 10, Windows 8, Windows 8.1, Windows Server 2016, Windows Server 2012 R2, or Windows Server 2012 R2, do this:</span></span>
  
1. <span data-ttu-id="cec2c-159">使用任何一種方法來尋找捷徑的**Windows PowerShell**：</span><span class="sxs-lookup"><span data-stu-id="cec2c-159">Use any of these methods to find the shortcut for **Windows PowerShell**:</span></span>
    
  - <span data-ttu-id="cec2c-160">在 [開始] 畫面上按一下 [空白] 區域中，然後輸入 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="cec2c-160">On the Start screen, click an empty area, and type Windows PowerShell.</span></span>
    
  - <span data-ttu-id="cec2c-p111">在桌面或 [開始] 畫面中，按 Windows 鍵 + Q。在 [搜尋左中，輸入 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p111">On the desktop or the Start screen, press the Windows key+Q. In the Search charm, type Windows PowerShell.</span></span>
    
  - <span data-ttu-id="cec2c-p112">在桌面或 [開始] 畫面，將游標移至右上角或往撥動以顯示圖標螢幕的右邊緣從左。選取 [搜尋左，然後輸入 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p112">On the desktop or the Start screen, move your cursor to the upper-right corner, or swipe left from the right edge of the screen to show the charms. Select the Search charm, and enter Windows PowerShell.</span></span>
    
2. <span data-ttu-id="cec2c-165">結果中以滑鼠右鍵按一下 [ **Windows PowerShell**]，然後選取 [**以管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="cec2c-165">In the results, right-click **Windows PowerShell**, and select **Run as administrator**.</span></span>
    
3. <span data-ttu-id="cec2c-166">如果出現 [**使用者帳戶控制**] 對話方塊，請選取**[是]**以確認您想要執行 Windows PowerShell 系統管理員認證。</span><span class="sxs-lookup"><span data-stu-id="cec2c-166">If the **User Account Control** dialog box appears, select **Yes** to verify that you want to run Windows PowerShell under administrator credentials.</span></span>
    
<span data-ttu-id="cec2c-167">如果您正在執行 Windows 7 SP1 （或 Windows Server 2008 R2 SP1），執行這項作業：</span><span class="sxs-lookup"><span data-stu-id="cec2c-167">If you're running Windows 7 SP1 (or Windows Server 2008 R2 SP1), do this:</span></span>
  
1. <span data-ttu-id="cec2c-p113">在 [**開始**] 功能表上選取 [**所有程式]** > **附屬應用程式** > **Windows PowerShell**。**Windows PowerShell**] 上按一下滑鼠右鍵，然後選取 [**以系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p113">On the **Start** menu, select **All Programs** > **Accessories** > **Windows PowerShell**. Right-click **Windows PowerShell**, and then select **Run as administrator**.</span></span>
    
2. <span data-ttu-id="cec2c-170">如果出現 [**使用者帳戶控制**] 對話方塊，請選取**[是]**以確認您想要執行 Windows PowerShell 系統管理員認證。</span><span class="sxs-lookup"><span data-stu-id="cec2c-170">If the **User Account Control** dialog box appears, select **Yes** to verify that you want to run Windows PowerShell under administrator credentials.</span></span>
    
<span data-ttu-id="cec2c-p114">您必須以系統管理員身分執行 Windows PowerShell。如果您不進入當您嘗試匯入其中一個必要模組時收到的錯誤訊息是類似。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p114">You must run Windows PowerShell as an administrator. If you don't, you're going to get an error message similar to this when you try to import one of the required modules.</span></span>
  
```
The specified module 'Microsoft.Online.SharePoint.Online.PowerShell' was not loaded because no valid module file was found in any directory.
```

<span data-ttu-id="cec2c-p115">若要補救這種情況的唯一方式是關閉 Windows PowerShell 和系統管理員身分來重新啟動。以下是告訴是否您正在以系統管理員身分執行 Windows PowerShell 快速又簡單的方法： 提示`PS C:\Windows\System32>`、 不`PS C:\Users\YourUserName>`。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p115">The only way to remedy the situation is to close Windows PowerShell and restart it as an administrator. Here's a quick and easy way to tell if you're running Windows PowerShell as an administrator: the prompt is  `PS C:\Windows\System32>`, not  `PS C:\Users\YourUserName>`.</span></span>

  
### <a name="step-2-create-a-windows-powershell-credentials-object"></a><span data-ttu-id="cec2c-175">步驟 2：建立 Windows PowerShell 認證物件</span><span class="sxs-lookup"><span data-stu-id="cec2c-175">Step 2: Create a Windows PowerShell credentials object</span></span>
<span data-ttu-id="cec2c-176"><a name="Step2"> </a></span><span class="sxs-lookup"><span data-stu-id="cec2c-176"></span></span>

<span data-ttu-id="cec2c-p116">認證物件會提供做為 Windows powershell 將您的使用者名稱和密碼的加密的方法。若要建立的認證物件，請在 Windows PowerShell 中執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p116">The credentials object provides an encrypted way to pass your user name and password to Windows PowerShell. To create a credentials object, run the following command in Windows PowerShell.</span></span>
  
```
$credential = Get-Credential
```

> [!NOTE]
>  <span data-ttu-id="cec2c-p117">`$credential`會將儲存的認證物件的變數。您不需要命名變數`$credential`，但是這麼做讓容易記住的變數中包含的認證物件。（和這很重要，因為我們將多次重複使用此變數）。會將也讓更容易您依照我們的範例，因為這篇文章將會一律使用`$credential`來代表認證物件。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p117">`$credential` is a variable that will store the credentials object. You don't have to name the variable `$credential`, but doing so makes it easier to remember which variable contains the credentials object. (And that's important, because we'll reuse this variable several times.) That will also make it easier for you to follow our examples, because this article will always use  `$credential` to represent the credentials object.</span></span>
  
<span data-ttu-id="cec2c-182">Windows PowerShell 會顯示對話方塊看起來像這樣。</span><span class="sxs-lookup"><span data-stu-id="cec2c-182">Windows PowerShell will then display a dialog box that looks like this.</span></span>
  
![空白認證要求對話方塊。](images/o365_powershell_empty_credentials_box.png)
  
<span data-ttu-id="cec2c-184">輸入您的工作或學校帳戶使用者名稱的**使用者名稱**] 方塊中，使用格式_username@domainname_ (例如，kenmyer@litwareinc.onmicrosoft.com);在 [**密碼**] 方塊中，輸入您的密碼並再按一下 [**確定]**：</span><span class="sxs-lookup"><span data-stu-id="cec2c-184">Type your work or school account user name in the **User name** box, using the format _username@domainname_ (for example, kenmyer@litwareinc.onmicrosoft.com); type your password in the **Password** box; and then click **OK**:</span></span>
  
![完成的認證要求對話方塊。](images/o365_powershell_completed_credentials_box.png)
  
<span data-ttu-id="cec2c-p118">請注意如通常是這樣，您將不會看到確認已建立的認證物件的任何排序。（Windows PowerShell 通常會告訴您何時事項出錯，但不一定要告訴您何時事項往右。）若要確認已建立的認證物件，請在 Windows PowerShell 中輸入下列命令並按 Enter。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p118">Note that, as is often the case, you won't see any sort of confirmation that the credentials object was created. (Windows PowerShell typically tells you when things go wrong but doesn't always tell you when things go right.) If you want to verify that the credentials object was created, type the following in Windows PowerShell and then press Enter.</span></span>
  
```
$credential
```

<span data-ttu-id="cec2c-188">接著您應該可以看到類似此螢幕的畫面。</span><span class="sxs-lookup"><span data-stu-id="cec2c-188">You should then see something similar to this on the screen.</span></span>
  
```
UserName                               Password
--------                               --------
kenmyer@litwareinc.onmicrosoft.com     System.Security.SecureString
```

<span data-ttu-id="cec2c-p119">請記住以下一回事是[Get-credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)指令程式只會建立認證物件它不驗證您或否則請確認使用者名稱與您所提供的密碼正確無誤。例如，假設您拼錯 kenmyer@litwareinc.onmicrosoft.com 身分的使用者名稱。如果您這樣做， **Get-credential**會建立認證物件並使用該使用者名稱，且不檢查查看是否有該實際的有效使用者名稱。您不知道是否在您建立確實有效認證物件直到您真的要連線至 Office 365 服務嘗試使用該物件。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p119">One thing to keep in mind here is that the [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618) cmdlet only creates the credentials object; it does not authenticate you or otherwise verify that the user name and password you supplied are correct. For example, suppose you mistyped the user name as kenmyer@litwareinc.onmicrosoft.com. If you do that, **Get-Credential** will create a credentials object using that user name, and without checking to see if that is actually a valid user name. You won't know whether you have created a truly valid credentials object until you actually use that object to try to connect to the Office 365 services.</span></span>
  
### <a name="step-3-connect-to-office-365"></a><span data-ttu-id="cec2c-192">步驟 3：連線至 Office 365</span><span class="sxs-lookup"><span data-stu-id="cec2c-192">Step 3: Connect to Office 365</span></span>
<span data-ttu-id="cec2c-193"><a name="Step3"> </a></span><span class="sxs-lookup"><span data-stu-id="cec2c-193"></span></span>

<span data-ttu-id="cec2c-194">我們將啟動連線至 Office 365 本身擷取。</span><span class="sxs-lookup"><span data-stu-id="cec2c-194">We'll start by connecting to Office 365 itself.</span></span> 
  
<span data-ttu-id="cec2c-p120">我們需要執行以下動作的第一個項重點是匯入 Office 365 模組 (Microsoft Azure Active Directory Module for Windows PowerShell)。若要這樣做，請在 Windows PowerShell 中執行此命令。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p120">The first thing we need to do here is import the Office 365 module (the Microsoft Azure Active Directory Module for Windows PowerShell). To do that, run this command in Windows PowerShell.</span></span>
  
```
Import-Module MsOnline
```

<span data-ttu-id="cec2c-197">若要驗證模組確實已經匯入，請執行此命令。</span><span class="sxs-lookup"><span data-stu-id="cec2c-197">If you want to verify that the module was imported, run this command.</span></span>
  
```
Get-Module
```

<span data-ttu-id="cec2c-198">您應該會看到內容看起來像這樣這個命令所傳回的模組清單中的某處： `Manifest 1.0 MSOnline {Add-MsolForeignGroupToRole, Add-MsolG...}`。</span><span class="sxs-lookup"><span data-stu-id="cec2c-198">Somewhere in the list of modules that are returned by this command you should see something that looks like this:  `Manifest 1.0 MSOnline {Add-MsolForeignGroupToRole, Add-MsolG...}`.</span></span>
  
<span data-ttu-id="cec2c-199">如果您看到`MSOnline`列出，這表示一切皆依計劃。</span><span class="sxs-lookup"><span data-stu-id="cec2c-199">If you see  `MSOnline` listed, that means that everything went according to plan.</span></span>
  
<span data-ttu-id="cec2c-200">建立的認證物件 (請參閱[步驟 2： 建立 Windows PowerShell 認證物件](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)) 和其`MsOnline`載入模組，我們現在可以連線到 Office 365 使用[Connect-msolservice](https://go.microsoft.com/fwlink/p/?LinkId=532375) cmdlet 及下列命令。</span><span class="sxs-lookup"><span data-stu-id="cec2c-200">With the credentials object created (see [Step 2: Create a Windows PowerShell credentials object](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)) and with the  `MsOnline` module loaded, we can now connect to Office 365 by using the [Connect-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375) cmdlet and the following command.</span></span>
  
```
Connect-MsolService -Credential $credential
```

<span data-ttu-id="cec2c-p121">所有您需要提供的注意事項是認證物件 ( `$credential`)。根據所需的認證，Office 365 將會自動連線到正確的網域。您沒有執行**Connect-msolservice**時指定您的網域名稱。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p121">Notice that all you have to provide is the credentials object ( `$credential`). Based on those credentials, Office 365 will automatically connect you to the correct domain. You do not have to specify your domain name when running **Connect-MsolService**.</span></span>
  
<span data-ttu-id="cec2c-204">若要確認您確實*會*連線至 Office 365，請執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="cec2c-204">To verify that you really  *are*  connected to Office 365, run this command.</span></span>
  
```
Get-MsolDomain
```

<span data-ttu-id="cec2c-205">接著，我們應該會得到如下的內容。</span><span class="sxs-lookup"><span data-stu-id="cec2c-205">In return, you should get back something similar to this.</span></span>
  
```
Name                         Status          Authentication
----                         ------          --------------
litwareinc.onmicrosoft.com   Verified        Managed
```

### <a name="step-4-connect-to-sharepoint-online"></a><span data-ttu-id="cec2c-206">步驟 4：連線至 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="cec2c-206">Step 4: Connect to SharePoint Online</span></span>
<span data-ttu-id="cec2c-207"><a name="Step4"> </a></span><span class="sxs-lookup"><span data-stu-id="cec2c-207"></span></span>

<span data-ttu-id="cec2c-208">匯入 SharePoint Online 模組採用下列命令：</span><span class="sxs-lookup"><span data-stu-id="cec2c-208">Import the SharePoint Online module with the following command:</span></span>
  
```
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
```

<span data-ttu-id="cec2c-209">_DisableNameChecking_參數會隱藏這個警告。</span><span class="sxs-lookup"><span data-stu-id="cec2c-209">The  _DisableNameChecking_ switch suppresses this warning.</span></span>
  
```
WARNING: The names of some imported commands from the module 'Microsoft.Online.SharePoint.PowerShell' include unapproved verbs that might make them less discoverable. To find the commands with unapproved verbs, run the Import-Module command again with the Verbose parameter. For a list of approved verbs, type Get-Verb.
```

<span data-ttu-id="cec2c-p122">若要連接至 SharePoint Online，您需要提供資訊的兩個部分： 您的認證和 SharePoint Online 系統管理網站的 URL。認證組件很簡單： 我們已儲存的變數中`$credential`(請參閱[步驟 2： 建立 Windows PowerShell 認證物件](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2))。針對很容易足夠，以及決定系統管理網站的 URL。假設您的 Office 365 的網域名稱是`litwareinc.onmicrosoft.com`。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p122">In order to connect to SharePoint Online, you need to supply two pieces of information: your credentials and the URL of your SharePoint Online admin site. The credentials part is easy: we've already stored that in the variable  `$credential` (see [Step 2: Create a Windows PowerShell credentials object](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)). As for the URL of your admin site, that's easy enough to determine, as well. Suppose your Office 365 domain name is  `litwareinc.onmicrosoft.com`.</span></span>
  
<span data-ttu-id="cec2c-214">若要判斷系統管理網站的 URL，請執行此動作：</span><span class="sxs-lookup"><span data-stu-id="cec2c-214">To determine the admin site URL, do this:</span></span>
  
1. <span data-ttu-id="cec2c-215">使用前置詞啟動`https://`。</span><span class="sxs-lookup"><span data-stu-id="cec2c-215">Start by using the prefix  `https://`.</span></span>
    
2. <span data-ttu-id="cec2c-p123">新增您的網域名稱的網域主機部分。例如，用於`litwareinc.onmicrosoft.com`、 網域主機名稱是`litwareinc`。針對`contoso.onmicrosoft.com`、 網域主機名稱是`contoso`。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p123">Add the domain host portion of your domain name. For example, for  `litwareinc.onmicrosoft.com`, the domain host name is  `litwareinc`. For  `contoso.onmicrosoft.com`, the domain host name is  `contoso`.</span></span>
    
3. <span data-ttu-id="cec2c-219">新增連字號 （-） 後面加上`admin.sharepoint.com`。</span><span class="sxs-lookup"><span data-stu-id="cec2c-219">Add a hyphen (-) followed by  `admin.sharepoint.com`.</span></span>
    
<span data-ttu-id="cec2c-220">換句話說：</span><span class="sxs-lookup"><span data-stu-id="cec2c-220">In other words:</span></span>
  
 `https://` + `litwareinc` + `-admin.sharepoint.com` = `https://litwareinc-admin.sharepoint.com`
  
<span data-ttu-id="cec2c-p124">您已建構 URL 後，然後可以連線至 SharePoint Online 使用該 URL 及認證物件。呼叫[Connect-sposervice](https://go.microsoft.com/fwlink/p/?LinkId=532436) cmdlet，使用類似的命令。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p124">After you've constructed the URL, you can then use that URL and your credentials object to connect to SharePoint Online. Just call the [Connect-SPOService](https://go.microsoft.com/fwlink/p/?LinkId=532436) cmdlet, using a command similar to this one.</span></span>
  
```
Connect-SPOService -Url https://litwareinc-admin.sharepoint.com -credential $credential
```

<span data-ttu-id="cec2c-223">若要確認已建立連線，請在 Windows PowerShell 中執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="cec2c-223">To verify that the connection has been made, run the following command in Windows PowerShell.</span></span>
  
```
Get-SPOSite
```

<span data-ttu-id="cec2c-p125">您應該要取得所有 SharePoint Online 網站的清單。以下是範例：</span><span class="sxs-lookup"><span data-stu-id="cec2c-p125">You should get a list of all your SharePoint Online sites. Here is an example:</span></span>
  
```
Url                                       Owner          Storage Quota
---                                       -----          -------------
http://litwareinc-public.sharepoint.com/                 1000
https://litwareinc.sharepoint.com/                       1000
https://litwareinc.sharepoint.com/search                 1000
```

<span data-ttu-id="cec2c-p126">Office 365 命令 (過述[步驟 3： 連線至 Office 365](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step3)) 將仍在運作。（嘗試執行**Get-msoluser**，並以親眼）。也就是說您現在可以管理 Office 365 與 SharePoint Online 的 Windows PowerShell 相同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p126">Your Office 365 commands (the ones described in [Step 3: Connect to Office 365](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step3)) will still work. (Try running **Get-MsolUser**, and see for yourself.) That means that you can now manage both Office 365 and SharePoint Online from the same instance of Windows PowerShell.</span></span>
  
### <a name="step-5-connect-to-skype-for-business-online"></a><span data-ttu-id="cec2c-228">步驟 5：連線到商務用 Skype Online</span><span class="sxs-lookup"><span data-stu-id="cec2c-228">Step 5: Connect to Skype for Business Online</span></span>
<span data-ttu-id="cec2c-229"><a name="Step5"> </a></span><span class="sxs-lookup"><span data-stu-id="cec2c-229"></span></span>

<span data-ttu-id="cec2c-p127">連線到 Skype 商務 Online (與 Exchange Online 或安全性&amp;規範中心) 不同於連線至 Office 365 或 SharePoint Online。那是因為商務 Online 和 Exchange Online cmdlet Skype 不取得安裝在電腦上像是 Office 365 與 SharePoint Online cmdlet 執行動作。而您登入，每次適當指令程式會暫時複製到您的電腦。當您登入時，這些指令程式然後已從您的電腦。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p127">Connecting to Skype for Business Online (and to Exchange Online or the Security &amp; Compliance Center) is different than connecting to Office 365 or to SharePoint Online. That's because the Skype for Business Online and Exchange Online cmdlets don't get installed on your computer like the Office 365 and the SharePoint Online cmdlets do. Instead, each time you sign in, the appropriate cmdlets are temporarily copied to your computer. When you sign off, those cmdlets are then removed from your computer.</span></span>
  
<span data-ttu-id="cec2c-p128">以連線至 Skype 商務線上，您必須匯入商務線上模組的 Skype。若要這樣做，執行此命令。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p128">In order to connect to Skype for Business Online, you need to import the Skype for Business Online module. To do that, run this command.</span></span>
  
```
Import-Module SkypeOnlineConnector
```

<span data-ttu-id="cec2c-236">第一次這麼做時，您可能會看到下列警告訊息，可以放心地忽略。</span><span class="sxs-lookup"><span data-stu-id="cec2c-236">The first time you do this, you might see the following warning message, which you can safely ignore.</span></span>
  
```
WARNING: WSMan NetworkDelayms has been set to 30000 milliseconds. The previous value was 5000 milliseconds.
WARNING: To improve the performance of the Lync Online Connector, it is recommended that the network delay be set to
30000 milliseconds (30 seconds). However, you can use Set-WinRMNetworkDelayMS to change the network delay to any
integer value.
```

<span data-ttu-id="cec2c-237">在匯入模組之後，請執行此命令。</span><span class="sxs-lookup"><span data-stu-id="cec2c-237">After the module has been imported, run this command.</span></span>
  
```
$sfboSession = New-CsOnlineSession -Credential $credential
```

<span data-ttu-id="cec2c-p129">我們已建立的遠端 PowerShell 工作階段。在此例中，這表示我們已連線的 Windows PowerShell 執行個體其中一個 Office 365 的伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p129">We have created a remote PowerShell session. In this case, that means that we've connected to an instance of Windows PowerShell running on one of the Office 365 servers.</span></span> 
  
<span data-ttu-id="cec2c-p130">我們已對 Office 365 的連線，雖然我們尚未下載指令碼、 cmdlet 和 Skype 管理商務 online 所需的其他項目。若要這樣做，我們必須執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p130">Although we've made a connection to Office 365, we haven't downloaded the scripts, cmdlets, and other items needed to manage Skype for Business Online. To do that, we have to run this command.</span></span>
  
```
Import-PSSession $sfboSession
```

<span data-ttu-id="cec2c-242">當您匯入 Windows PowerShell 工作階段時，您應該會看到類似下列項目，報告商務 Online cmdlet 匯入至電腦的所有 Skype 進度列進度列。</span><span class="sxs-lookup"><span data-stu-id="cec2c-242">When you import the Windows PowerShell session, you should see a progress bar similar to the following, a progress bar that reports on all the Skype for Business Online cmdlets being imported to your computer.</span></span>
  
![Lync Online 進度列。](images/o365_powershell_lync_progress_bar.png)
  
<span data-ttu-id="cec2c-244">當進度列消失後，您應該會看到如下所示的輸出。</span><span class="sxs-lookup"><span data-stu-id="cec2c-244">When the progress bar disappears, you should then see output similar to the following.</span></span>
  
```
ModuleType Version    Name               ExportedCommands
---------- -------    ----               ----------------
Script     1.0        tmp_swc5mp4v.1ck  {Copy-CsVoicePolicy, Disabl...
```

### <a name="step-6-connect-to-exchange-online"></a><span data-ttu-id="cec2c-245">步驟 6：連線至 Exchange Online</span><span class="sxs-lookup"><span data-stu-id="cec2c-245">Step 6: Connect to Exchange Online</span></span>
<span data-ttu-id="cec2c-246"><a name="Step6"> </a></span><span class="sxs-lookup"><span data-stu-id="cec2c-246"></span></span>

<span data-ttu-id="cec2c-247">執行此命令以建立遠端 Windows PowerShell 工作階段與 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="cec2c-247">Run this command, which creates a remote Windows PowerShell session with Exchange Online.</span></span>
  
```
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
```

> [!NOTE]
> <span data-ttu-id="cec2c-p131">為什麼一定要連線至 Exchange Online 比命令會連線至 Skype 商務線上更複雜的命令？嚴格來說，不： 這兩個命令執行完全同樣的事情。但如商務 Online 小組 Skype 建立自己指令程式 —**新增 CsOnlineSession** — 的隱藏一些連接至 Exchange Online 時所使用的參數 （例如_驗證_和_AllowRedirection_）。而不需要您自行輸入該資訊、_驗證_及_AllowRedirection_參數會有效地內建**新增 CsOnlineSession**指令程式。您必須連線至 Exchange Online 因為 Exchange Online 使用標準[新 PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621)指令程式來連線至 Office 365 時輸入這些參數。缺點是您必須執行一點點輸入。優點是您不需要下載並安裝 Exchange Online 的模組。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p131">Why is the command for connecting to Exchange Online more complicated than the command to connect to Skype for Business Online? Technically, it's not: both commands do the exact same thing. However, the Skype for Business Online team created its own cmdlet— **New-CsOnlineSession** —that hides some of the parameters (like _Authentication_ and _AllowRedirection_) that are used when connecting to Exchange Online. Instead of requiring you to type that information yourself, the  _Authentication_ and _AllowRedirection_ parameters are effectively built in to the **New-CsOnlineSession** cmdlet. You have to type those parameters when connecting to Exchange Online because Exchange Online uses the standard [New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621) cmdlet to connect to Office 365. The disadvantage is that you have a little more typing to do. The advantage is that you don't have to download and install an Exchange Online module.</span></span>
  
<span data-ttu-id="cec2c-255">您只需要現在是匯入此遠端工作階段，就像我們進行了商務 online 與 Skype。</span><span class="sxs-lookup"><span data-stu-id="cec2c-255">All you have to do now is import this remote session, just like we did with Skype for Business Online.</span></span>
  
```
Import-PSSession $exchangeSession -DisableNameChecking
```

<span data-ttu-id="cec2c-256">您應該可以看到類似此螢幕的畫面。</span><span class="sxs-lookup"><span data-stu-id="cec2c-256">You should see something similar to this on the screen.</span></span>
  
```
ModuleType Version  Name             ExportedCommands
---------- -------  ----             ----------------
Script     1.0      tmp_nweiqjvl.geu {Add-AvailabilityAddressSpace...
```

<span data-ttu-id="cec2c-257">現在請嘗試執行此命令。</span><span class="sxs-lookup"><span data-stu-id="cec2c-257">Now try running this command.</span></span>
  
```
Get-AcceptedDomain
```

<span data-ttu-id="cec2c-258">您應看見所傳回的資訊有關您所設定的電子郵件地址在 Exchange Online 的 Office 365 網域。</span><span class="sxs-lookup"><span data-stu-id="cec2c-258">In return, you should see information about your Office 365 domains that are configured for email addresses in Exchange Online.</span></span>
  
```
Name            DomainName          DomainType      Default
----            ----------          ----------      -------
litwareinc.com  litwareinc.com      Authoritative   True
```

### <a name="step-7-connect-to-the-security-amp-compliance-center"></a><span data-ttu-id="cec2c-259">步驟 7： 連線至安全性&amp;規範中心</span><span class="sxs-lookup"><span data-stu-id="cec2c-259">Step 7: Connect to the Security &amp; Compliance Center</span></span>
<span data-ttu-id="cec2c-260"><a name="Step7"> </a></span><span class="sxs-lookup"><span data-stu-id="cec2c-260"></span></span>

<span data-ttu-id="cec2c-p132">安全性&amp;規範中心是可讓您從某個位置管理的符合性功能的 Office 365 中的服務。如需詳細資訊，請參閱[Office 365 規範中心](http://technet.microsoft.com/library/fde83656-f136-448d-b250-6fa17b503e4e.aspx)。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p132">The Security &amp; Compliance Center is a service in Office 365 that lets you to manage compliance features from one location. For more information, see [Office 365 compliance center](http://technet.microsoft.com/library/fde83656-f136-448d-b250-6fa17b503e4e.aspx).</span></span>
  
<span data-ttu-id="cec2c-263">證券的連線指示&amp;規範中心時非常類似的 Exchange Online 中，但具有新增變化，您會看見中可用。</span><span class="sxs-lookup"><span data-stu-id="cec2c-263">The connection instructions for the Security &amp; Compliance Center are very similar to those for Exchange Online, but with an added twist, which you'll see in a moment.</span></span>
  
<span data-ttu-id="cec2c-264">執行此命令以建立遠端 PowerShell 工作階段與安全性&amp;規範中心。</span><span class="sxs-lookup"><span data-stu-id="cec2c-264">Run this command, which creates a remote PowerShell session with the Security &amp; Compliance Center.</span></span>
  
```
$ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
```

<span data-ttu-id="cec2c-265">現在執行此命令︰</span><span class="sxs-lookup"><span data-stu-id="cec2c-265">Now run this command:</span></span>
  
```
Import-PSSession $ccSession -Prefix cc
```

<span data-ttu-id="cec2c-p133">同樣地，此命令會非常類似於 Exchange Online 的命令。因為安全性中不有任何未的動詞_DisableNameChecking_參數不是必要&amp;規範中心。但不住亦其他`-Prefix cc`參數和值吗？這就是我們說過您需新增的變化。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p133">Again, this command is very similar to the command for Exchange Online. The  _DisableNameChecking_ switch isn't required because there are no unapproved verbs in the Security &amp; Compliance Center. But what about that additional `-Prefix cc` parameter and value? That's the added twist we told you about.</span></span>
  
<span data-ttu-id="cec2c-p134">Exchange Online 與安全性&amp;規範中心共用部分具有完全相同的名稱，並提供相同功能的 cmdlet。**Get-rolegroup**是範例。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p134">Exchange Online and the Security &amp; Compliance Center share some cmdlets that have exactly the same names and provide the same functionality. **Get-RoleGroup** is an example.</span></span>
  
<span data-ttu-id="cec2c-p135">因此，有什麼如果您嘗試匯入包含具有相同名稱的指令程式的兩個工作階段？他們會發生衝突。您將取得 big 黃色警告訊息，`WARNING: Proxy creation has been skipped for the following command:`後面接著無法匯入的衝突 cmdlet 的清單。最終結果？您可以執行**Get-rolegroup** in Exchange Online，因為您連接那里第一次，但您無法執行**Get-rolegroup**安全性&amp;規範中心因為連接那里上一次及衝突的指令程式匯入遭到拒絕。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p135">So what happens if you try to import two sessions that contain cmdlets with the same name? They collide. You'll get a big yellow warning message that says,  `WARNING: Proxy creation has been skipped for the following command:` followed by the list of conflicting cmdlets that couldn't be imported. The end result? You can run **Get-RoleGroup** in Exchange Online because you connected there first, but you can't run **Get-RoleGroup** in the Security &amp; Compliance Center because you connected there last and the conflicting cmdlets refused to import.</span></span>
  
<span data-ttu-id="cec2c-p136">處理這個問題的最簡單方式是將任意文字首碼新增至匯入安全性&amp;規範中心指令程式。我們沒有該使用的_前置詞_參數值"cc" **Import-pssession**指令程式上。沒有可為什麼？ 我們它淘汰衝突 （稍微） 變更安全性&amp;此工作階段的規範中心指令程式名稱。所有匯入安全性&amp;規範中心 cmdlet 立即開始使用"cc"在依名詞或組件中的指令程式名稱 (右邊的"-")。例如，產生爭議**Get-rolegroup**指令程式會變成**Get ccRoleGroup** security&amp;規範中心讓它不會與**Get-rolegroup** Exchange Online 的衝突。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p136">The easiest way to deal with this problem is to add an arbitrary text prefix to the imported Security &amp; Compliance Center cmdlets. We did that using the  _Prefix_ parameter with the value "cc" on the **Import-PSSession** cmdlet. What did that do for us? It eliminated the conflicts by (slightly) changing the Security &amp; Compliance Center cmdlet names for this session. All of the imported Security &amp; Compliance Center cmdlets now start with "cc" in the noun part of the cmdlet name (to the right of the "-"). For example, the contentious **Get-RoleGroup** cmdlet becomes **Get-ccRoleGroup** for the Security &amp; Compliance Center so it doesn't conflict with **Get-RoleGroup** for Exchange Online.</span></span>
  
<span data-ttu-id="cec2c-p137">缺點為何？ *所有* 安全性&amp;規範中心 cmdlet 名稱接收"cc"前置詞 — 是用完就不需要它的唯一指令程式。例如， **Get ComplianceSearch**變成**Get ccComplianceSearch**即使發生這類指令程式在 Exchange Online。它是元設計師，但不是太故障時您考慮在單一 Windows PowerShell 工作階段管理所有 Office 365 服務的優點。請記得安全性中的所有程序的 cmdlet 名稱來新增"cc"&amp;規範中心。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p137">The downside?  *All*  Security &amp; Compliance Center cmdlet names receive the "cc" prefix—even unique cmdlets that don't need it. For example, **Get-ComplianceSearch** becomes **Get-ccComplianceSearch** even though there is no such cmdlet in Exchange Online. It's a bit of a pain, but not too bad when you consider the benefits of managing all Office 365 services in a single Windows PowerShell session. Just remember to add "cc" to the cmdlet names for all procedures in the Security &amp; Compliance Center.</span></span>
  
<span data-ttu-id="cec2c-288">如果一切順利，您會看見類似這樣的內容：</span><span class="sxs-lookup"><span data-stu-id="cec2c-288">If all goes well, you'll see something similar to this:</span></span>
  
```
ModuleType Version  Name             ExportedCommands
---------- -------  ----             ----------------
Script     1.0      tmp_xbbx5exr.ehm {Add-ccRoleGroupMember, Get-ccAdminAuditLogConfig, Get-ccA...
```

<span data-ttu-id="cec2c-289">現在您就可以在單一 Windows PowerShell 工作階段管理所有 Office 365 服務自由。</span><span class="sxs-lookup"><span data-stu-id="cec2c-289">Now you are free to manage all Office 365 services in a single Windows PowerShell session.</span></span>
  
### <a name="step-8-gracefully-end-your-powershell-sessions"></a><span data-ttu-id="cec2c-290">步驟 8：依正常程序結束 PowerShell 工作階段</span><span class="sxs-lookup"><span data-stu-id="cec2c-290">Step 8: Gracefully end your PowerShell sessions</span></span>
<span data-ttu-id="cec2c-291"><a name="Step8"> </a></span><span class="sxs-lookup"><span data-stu-id="cec2c-291"></span></span>

<span data-ttu-id="cec2c-p138">如果您只是關閉 Windows PowerShell 視窗，商務線上遠端連線您 Skype 會保持使用中的下一個 15 分鐘或能力。因為 Skype 商務 online 限制同時進行的任何一個人或任何一個網域都可以有開啟的連線數目、，可能是問題。具有商務 online Skype，個別的系統管理員可以、 最有三個開啟的連線一次且網域可以的九個開啟的連線的最大值。如果您的業務 Online 登入 Skype 並再結束，但不正常關閉工作階段，該工作階段的下一個 15 分鐘或賣保持開啟。因此，這是一個較少的連線可以在您或其他管理員可以在您的網域。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p138">If you just close the Windows PowerShell window, your Skype for Business Online remote connection will remain active for the next 15 minutes or so. Because Skype for Business Online limits the number of simultaneous connections that any one person or any one domain can have open, that could be a problem. With Skype for Business Online, an individual administrator can have, at most, three open connections at one time, and a domain can have a maximum of nine open connections. If you sign in to Skype for Business Online and then exit without properly closing the session, that session remains open for the next 15 minutes or so. As a result, that's one fewer connection available to you or to other administrators in your domain.</span></span>
  
<span data-ttu-id="cec2c-p139">而我們關閉遠端工作階段的 Skype 商務 Online、 Exchange Online 與安全性&amp;規範中心正常。這麼做之前，請執行此命令。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p139">Instead, let's close the remote sessions for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center gracefully. Before we do that, run this command.</span></span>
  
```
Get-PSSession
```

<span data-ttu-id="cec2c-p140">[Get-pssession](https://go.microsoft.com/fwlink/p/?LinkId=532437) cmdlet 應為您示範您必須至少三個遠端工作階段開啟、 另一個適用於商務 online Skype、 另一個適用於 Exchange Online 及其中的安全性&amp;（有可能您可以有多個三個遠端規範中心工作階段執行，視您是否已使用 Windows PowerShell 執行個體來連線至 Office 365 服務除了其他人的某個項目）。您應該會看到類似以下的內容。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p140">The [Get-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=532437) cmdlet should show you that you have at least three remote sessions open, one for Skype for Business Online, one for Exchange Online and one for the Security &amp; Compliance Center (it's possible you could have more than three remote sessions running, depending on whether you've used this instance of Windows PowerShell to connect to something else besides the Office 365 services). You should see something similar to the following.</span></span>
  
```
Id Name     ComputerName     State   ConfigurationName    Availability
-- ----     ------------     -----   -----------------    ------------
 1 Session1 webdir0a.onl...  Opened  Microsoft.PowerShell    Available
 2 Session2 outlook.offi...  Opened  Microsoft.Exchange      Available
 3 Session3 ps.complianc...  Opened  Microsoft.Exchange      Available
```

<span data-ttu-id="cec2c-p141">若要關閉這三個工作階段，請執行下列命令一次一個。第一個命令會關閉 Skype 商務線上工作階段，第二個關閉 Exchange Online 的工作階段，及第三個關閉 [安全性]&amp;規範中心工作階段。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p141">To close these three sessions, run these commands one at a time. The first command closes the Skype for Business Online session, the second closes the Exchange Online session, and the third closes the Security &amp; Compliance Center session.</span></span>
  
```
Remove-PSSession $sfboSession
Remove-PSSession $exchangeSession
Remove-PSSession $ccSession
```

<span data-ttu-id="cec2c-303">如果您現在執行**Get-pssession** cmdlet，您應該會看到 nothing 所有 （除非您有其他遠端工作階段啟動且正在執行）。</span><span class="sxs-lookup"><span data-stu-id="cec2c-303">If you now run the **Get-PSSession** cmdlet, you should see nothing at all (unless you have other remote sessions up and running).</span></span>
  
![沒有遠端工作階段的 Windows PowerShell 主控台](images/o365_powershell_no_remote_sessions.png)
  
> [!NOTE]
> <span data-ttu-id="cec2c-305">如果您想要關閉所有的遠端工作階段的同一時間，您可以使用此命令： >`Get-PSSession | Remove-PSSession`</span><span class="sxs-lookup"><span data-stu-id="cec2c-305">If you'd prefer to close all your remote sessions at the same time, you can use this command: >  `Get-PSSession | Remove-PSSession`</span></span>
  
<span data-ttu-id="cec2c-306">您現在嘗試執行指令程式從任何這些關閉工作階段 (例如， **Get-csmeetingconfiguration**中的商務 Online Skype) 如果您將取得會類似的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="cec2c-306">If you now try running a cmdlet from any of these closed sessions (for example, **Get-CsMeetingConfiguration** in Skype for Business Online) you'll get an error message that's similar to this one.</span></span>
  
```
Get-CsMeetingConfiguration : The term 'Get-CsMeetingConfiguration' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
```

<span data-ttu-id="cec2c-307">我們要取得這個錯誤訊息因為 Skype 商務 Online、 Exchange Online 和安全性的 cmdlet&amp;我們關閉遠端工作階段時刪除規範中心。</span><span class="sxs-lookup"><span data-stu-id="cec2c-307">We get that error message because the cmdlets for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center were deleted when we closed the remote sessions.</span></span>
  
<span data-ttu-id="cec2c-308">若要關閉 SharePoint Online 的工作階段，請輸入下列命令。</span><span class="sxs-lookup"><span data-stu-id="cec2c-308">To close the SharePoint Online session, type this command.</span></span>
  
```
Disconnect-SPOService
```

<span data-ttu-id="cec2c-309">如果您現在嘗試執行**Get-sposite** cmdlet，您將取得類似的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="cec2c-309">If you now try to run the **Get-SPOSite** cmdlet, you'll get an error message like this.</span></span>
  
```
get-sposite : No connection available. Use Connect-SPOService before running this CmdLet.
```

<span data-ttu-id="cec2c-310">因為您不再連線至 SharePoint Online 無法擷取站台資訊。</span><span class="sxs-lookup"><span data-stu-id="cec2c-310">You can't retrieve site information because you're no longer connected to SharePoint Online.</span></span>
  
<span data-ttu-id="cec2c-p142">與 Office 365 連線，雖然**Connect-msolservice**指令程式沒有任何對應的**中斷 MsolService**指令程式。讓 Office 365 剛關閉 Windows PowerShell 視窗。不過，它仍是不錯的選項為達成此目的最後讓您可以正確中斷 SharePoint Online、 Skype 商務 Online、 Exchange Online 與安全性&amp;規範中心。</span><span class="sxs-lookup"><span data-stu-id="cec2c-p142">As for your connection to Office 365, although there's a **Connect-MsolService** cmdlet, there's no corresponding **Disconnect-MsolService** cmdlet. So for Office 365, just close the Windows PowerShell window. Nevertheless, it's still a good idea to do this last so you can properly disconnect from SharePoint Online, Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center.</span></span>
  
## <a name="new-to-office-365"></a><span data-ttu-id="cec2c-314">初次使用 Office 365 嗎？</span><span class="sxs-lookup"><span data-stu-id="cec2c-314">New to Office 365?</span></span>
<span data-ttu-id="cec2c-315"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="cec2c-315"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="cec2c-316">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cec2c-316">See also</span></span>

#### 

[<span data-ttu-id="cec2c-317">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="cec2c-317">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="cec2c-318">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="cec2c-318">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="cec2c-319">使用 Office 365 PowerShell 管理 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="cec2c-319">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
  
[<span data-ttu-id="cec2c-320">使用 Office 365 PowerShell 管理使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="cec2c-320">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="cec2c-321">使用 Windows PowerShell 在 Office 365 中建立報告</span><span class="sxs-lookup"><span data-stu-id="cec2c-321">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)

