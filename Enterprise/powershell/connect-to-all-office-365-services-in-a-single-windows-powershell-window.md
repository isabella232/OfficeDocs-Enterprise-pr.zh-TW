---
title: 在單一 Windows PowerShell 視窗中連線至所有 Office 365 服務
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/04/2018
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
description: 摘要： 連線至單一 Windows PowerShell 視窗中的所有 Office 365 服務的 Windows PowerShell。
ms.openlocfilehash: ccd8ed1dc53d306aa77d79ac0270f5bd24dd9298
ms.sourcegitcommit: 21cc62118b78b76d16ef12e2c3eff2c0c789e3d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2018
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="9591e-103">在單一 Windows PowerShell 視窗中連線至所有 Office 365 服務</span><span class="sxs-lookup"><span data-stu-id="9591e-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

 <span data-ttu-id="9591e-104">**摘要：**而不是管理在個別的 PowerShell 主控台視窗中的不同 Office 365 服務，您可以連線至 Office 365 的所有服務和管理它們從單一主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="9591e-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span></span>
  
<span data-ttu-id="9591e-p101">當您使用 PowerShell 管理 Office 365 時，有可能有最多可以有五個不同 Windows PowerShell 工作階段，同時對應至 Office 365 系統管理中心、 SharePoint Online、 Exchange Online、 商務 online Skype 及安全性&amp;規範中心。使用個別的 Windows PowerShell 工作階段中的五個不同的連接方法，您的桌面可能看起來如下：</span><span class="sxs-lookup"><span data-stu-id="9591e-p101">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Office 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center. With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![一次執行五個 Windows PowerShell 主控台](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="9591e-p102">這不是因為您不能交換資料之間的跨服務管理那些五個 windows 管理 Office 365 的最佳。本主題說明如何使用單一執行個體您可以從中管理 Office 365、 商務 Online、 Exchange Online、 SharePoint online、 Skype 和安全性的 Windows PowerShell&amp;規範中心。</span><span class="sxs-lookup"><span data-stu-id="9591e-p102">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management. This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span></span>

>[!Note]
><span data-ttu-id="9591e-110">本文是程序正在更新，以使用 Azure Active Directory V2 PowerShell 模組及多重要素驗證 (MFA)。</span><span class="sxs-lookup"><span data-stu-id="9591e-110">This article is in the process of being updated to use the Azure Active Directory V2 PowerShell module and for multifactor authentication (MFA).</span></span>
>
  
## <a name="before-you-begin"></a><span data-ttu-id="9591e-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="9591e-111">Before you begin</span></span>
<span data-ttu-id="9591e-112"><a name="BeforeYouBegin"> </a></span><span class="sxs-lookup"><span data-stu-id="9591e-112"></span></span>

<span data-ttu-id="9591e-113">您可以從單一執行個體的 Windows PowerShell 管理 Office 365 的所有之前，請考慮下列先決條件：</span><span class="sxs-lookup"><span data-stu-id="9591e-113">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="9591e-p103">Office 365 搭配使用或學校您使用這些程序需求是 Office 365 系統管理員角色成員的帳戶。如需詳細資訊，請參閱 ＜[關於 Office 365 系統管理員角色](https://go.microsoft.com/fwlink/p/?LinkId=532367)。此為 Office 365 PowerShell、 不一定所有其他 Office 365 服務的需求。</span><span class="sxs-lookup"><span data-stu-id="9591e-p103">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367). This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="9591e-117">您可以使用下列 Windows 64 位元版本：</span><span class="sxs-lookup"><span data-stu-id="9591e-117">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="9591e-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="9591e-118">Windows 10</span></span>
    
  - <span data-ttu-id="9591e-119">Windows 8.1 或 Windows 8</span><span class="sxs-lookup"><span data-stu-id="9591e-119">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="9591e-120">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="9591e-120">Windows Server 2016</span></span>
    
  - <span data-ttu-id="9591e-121">Windows Server 2012 R2 或 Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="9591e-121">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="9591e-122">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="9591e-122">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="9591e-123">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="9591e-123">Windows Server 2008 R2 SP1\*</span></span>
    
    * <span data-ttu-id="9591e-p104">您需要安裝 Microsoft.NET Framework 4.5。*x* ，然後任一 Windows Management Framework 3.0 或 Windows Management Framework 4.0。如需詳細資訊，請參閱[安裝.NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868)和[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757)或[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)。</span><span class="sxs-lookup"><span data-stu-id="9591e-p104">You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0. For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="9591e-126">您需要用於 64 位元版本的 Windows 因為 Skype 的需求而商務線上模組及其中一個 Office 365 模組。</span><span class="sxs-lookup"><span data-stu-id="9591e-126">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="9591e-127">您必須安裝所需的 Office 365、 SharePoint Online 和 Skype 的商務 Online 模組：</span><span class="sxs-lookup"><span data-stu-id="9591e-127">You need to install the modules that are required for Office 365, SharePoint Online, and Skype for Business Online:</span></span>
    
   - [<span data-ttu-id="9591e-128">Microsoft Online Services 登入小幫手，適用於 IT 專業人員 RTW</span><span class="sxs-lookup"><span data-stu-id="9591e-128">Microsoft Online Service Sign-in Assistant for IT Professionals RTW</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=286152)
   - <span data-ttu-id="9591e-129">Windows Azure Active Directory Module for Windows PowerShell （64 位元版本） 具有較高的 PowerShell 命令提示字元處**安裝模組 MSOnline**命令。</span><span class="sxs-lookup"><span data-stu-id="9591e-129">Windows Azure Active Directory Module for Windows PowerShell (64-bit version) with the **Install-Module MSOnline** command at an elevated PowerShell command prompt.</span></span>
   - [<span data-ttu-id="9591e-130">SharePoint Online 管理命令介面</span><span class="sxs-lookup"><span data-stu-id="9591e-130">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="9591e-131">Skype Online，企業版 Windows PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="9591e-131">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  <span data-ttu-id="9591e-p105">Windows PowerShell 需要為 Skype 的已簽署的指令碼執行商務 Online、 Exchange Online 與安全性設定&amp;規範中心。若要這樣做，請執行下列命令在提升權限的 Windows PowerShell 工作階段 （您可以選取 [**執行系統管理員身分**開啟 Windows PowerShell 視窗）。</span><span class="sxs-lookup"><span data-stu-id="9591e-p105">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center. To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps"></a><span data-ttu-id="9591e-134">連線步驟</span><span class="sxs-lookup"><span data-stu-id="9591e-134">Connection steps</span></span>
<span data-ttu-id="9591e-135"><a name="BeforeYouBegin"> </a></span><span class="sxs-lookup"><span data-stu-id="9591e-135"></span></span>

<span data-ttu-id="9591e-136">以下是連線至單一 PowerShell 視窗中的所有服務的步驟。</span><span class="sxs-lookup"><span data-stu-id="9591e-136">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="9591e-137">（使用**系統管理員身分執行**） 以管理員身分開啟 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="9591e-137">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="9591e-138">執行此命令中，並輸入您的 Office 365 工作或學校帳戶認證。</span><span class="sxs-lookup"><span data-stu-id="9591e-138">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```
  $credential = Get-Credential
  ```

3. <span data-ttu-id="9591e-139">執行下列命令以連線至 Office 365。</span><span class="sxs-lookup"><span data-stu-id="9591e-139">Run these commands to connect to Office 365.</span></span>
    
  ```
  Import-Module MsOnline
  Connect-MsolService -Credential $credential
  ```

4. <span data-ttu-id="9591e-p106">執行下列命令以連接至 SharePoint Online。取代_\<domainhost >_網域的實際值。例如，用於`litwareinc.onmicrosoft.com`、 _ \<domainhost >_值是`litwareinc`。</span><span class="sxs-lookup"><span data-stu-id="9591e-p106">Run these commands to connect to SharePoint Online. Replace  _\<domainhost>_ with the actual value for your domain. For example, for `litwareinc.onmicrosoft.com`, the  _\<domainhost>_ value is `litwareinc`.</span></span>
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="9591e-p107">執行下列命令以連線至 Skype 商務線上。增加的警告`WSMan NetworkDelayms`值預期會在第一次連線和應忽略。</span><span class="sxs-lookup"><span data-stu-id="9591e-p107">Run these commands to connect to Skype for Business Online. A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="9591e-145">執行下列命令以連線至 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="9591e-145">Run these commands to connect to Exchange Online.</span></span>
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

7. <span data-ttu-id="9591e-146">執行下列命令以連線至安全性&amp;規範中心。</span><span class="sxs-lookup"><span data-stu-id="9591e-146">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```
  $ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
  Import-PSSession $ccSession -Prefix cc
  ```
> [!NOTE]
> <span data-ttu-id="9591e-p108">文字前置詞"cc"新增至*所有*安全性&amp;規範中心指令程式名稱，可以執行指令程式可讓存在於 Exchange Online 與安全性&amp;規範中心] 中相同的 Windows PowerShell 工作階段。例如， **Get-rolegroup**變成**Get ccRoleGroup**安全性&amp;規範中心。</span><span class="sxs-lookup"><span data-stu-id="9591e-p108">The text prefix "cc" is added to  *all*  Security &amp; Compliance Center cmdlet names so you can run cmdlets that exist in both Exchange Online and the Security &amp; Compliance Center in the same Windows PowerShell session. For example, **Get-RoleGroup** becomes **Get-ccRoleGroup** in the Security &amp; Compliance Center.</span></span>
  
<span data-ttu-id="9591e-p109">以下是單一區塊中的所有命令。指定您的網域主機名稱和一次執行所有它們。</span><span class="sxs-lookup"><span data-stu-id="9591e-p109">Here are all the commands in a single block. Specify the name of your domain host, and then run them all at one time.</span></span>
  
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
<span data-ttu-id="9591e-151">當您準備好關閉 Windows PowerShell 視窗時，執行此命令以移除 Skype 作用中的工作階段的商務 Online、 Exchange Online、 SharePoint Online 和安全性&amp;規範中心：</span><span class="sxs-lookup"><span data-stu-id="9591e-151">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $ccSession ; Disconnect-SPOService
```

## <a name="new-to-office-365"></a><span data-ttu-id="9591e-152">初次使用 Office 365 嗎？</span><span class="sxs-lookup"><span data-stu-id="9591e-152">New to Office 365?</span></span>
<span data-ttu-id="9591e-153"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="9591e-153"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="9591e-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9591e-154">See also</span></span>

- [<span data-ttu-id="9591e-155">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="9591e-155">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="9591e-156">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="9591e-156">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="9591e-157">使用 Office 365 PowerShell 管理 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9591e-157">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="9591e-158">使用 Office 365 PowerShell 管理使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="9591e-158">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="9591e-159">使用 Windows PowerShell 在 Office 365 中建立報告</span><span class="sxs-lookup"><span data-stu-id="9591e-159">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
