---
title: 在單一 Windows PowerShell 視窗中連線至所有 Office 365 服務
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
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
ms.openlocfilehash: f863879fd83fb09fc748066fb25ca4b73895eb98
ms.sourcegitcommit: c6efb42ffa0e81122152b67a3568a1ad1ff30aba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2019
ms.locfileid: "27521669"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="7576d-103">在單一 Windows PowerShell 視窗中連線至所有 Office 365 服務</span><span class="sxs-lookup"><span data-stu-id="7576d-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

 <span data-ttu-id="7576d-104">**摘要：** 而不是管理在個別的 PowerShell 主控台視窗中的不同 Office 365 服務，您可以連線至 Office 365 的所有服務和管理它們從單一主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="7576d-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span></span>
  
<span data-ttu-id="7576d-p101">當您使用 PowerShell 管理 Office 365 時，有可能有最多可以有五個不同 Windows PowerShell 工作階段，同時對應至 Office 365 系統管理中心、 SharePoint Online、 Exchange Online、 商務 online Skype 及安全性&amp;規範中心。使用個別的 Windows PowerShell 工作階段中的五個不同的連接方法，您的桌面可能看起來如下：</span><span class="sxs-lookup"><span data-stu-id="7576d-p101">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Office 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center. With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![一次執行五個 Windows PowerShell 主控台](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="7576d-p102">這不是因為您不能交換資料之間的跨服務管理那些五個 windows 管理 Office 365 的最佳。本主題說明如何使用單一執行個體您可以從中管理 Office 365、 商務 Online、 Exchange Online、 SharePoint online、 Skype 和安全性的 Windows PowerShell&amp;規範中心。</span><span class="sxs-lookup"><span data-stu-id="7576d-p102">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management. This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span></span>

>[!Note]
><span data-ttu-id="7576d-p103">目前本文僅包含該命令以連線至 Office 365 Worldwide （+ GCC） 雲端。其他附註，提供有關連線至其他 Office 365 雲朵資訊的文章連結。</span><span class="sxs-lookup"><span data-stu-id="7576d-p103">This article currently only contains the commands to connect to the Office 365 Worldwide (+GCC) cloud. Additional notes provide links to articles with information about connecting to the other Office 365 clouds.</span></span>
>

## <a name="before-you-begin"></a><span data-ttu-id="7576d-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="7576d-112">Before you begin</span></span>

<span data-ttu-id="7576d-113">您可以從單一執行個體的 Windows PowerShell 管理 Office 365 的所有之前，請考慮下列先決條件：</span><span class="sxs-lookup"><span data-stu-id="7576d-113">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="7576d-p104">Office 365 搭配使用或學校您使用這些程序需求是 Office 365 系統管理員角色成員的帳戶。如需詳細資訊，請參閱 ＜[關於 Office 365 系統管理員角色](https://go.microsoft.com/fwlink/p/?LinkId=532367)。此為 Office 365 PowerShell、 不一定所有其他 Office 365 服務的需求。</span><span class="sxs-lookup"><span data-stu-id="7576d-p104">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367). This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="7576d-117">您可以使用下列 Windows 64 位元版本：</span><span class="sxs-lookup"><span data-stu-id="7576d-117">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="7576d-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="7576d-118">Windows 10</span></span>
    
  - <span data-ttu-id="7576d-119">Windows 8.1 或 Windows 8</span><span class="sxs-lookup"><span data-stu-id="7576d-119">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="7576d-120">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="7576d-120">Windows Server 2019</span></span>
    
  - <span data-ttu-id="7576d-121">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="7576d-121">Windows Server 2016</span></span>
    
  - <span data-ttu-id="7576d-122">Windows Server 2012 R2 或 Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="7576d-122">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="7576d-123">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="7576d-123">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="7576d-124">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="7576d-124">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="7576d-p105">\*您需要安裝 Microsoft.NET Framework 4.5。*x* ，然後任一 Windows Management Framework 3.0 或 Windows Management Framework 4.0。如需詳細資訊，請參閱[安裝.NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868)和[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757)或[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)。</span><span class="sxs-lookup"><span data-stu-id="7576d-p105">\* You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0. For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="7576d-127">您需要用於 64 位元版本的 Windows 因為 Skype 的需求而商務線上模組及其中一個 Office 365 模組。</span><span class="sxs-lookup"><span data-stu-id="7576d-127">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="7576d-128">您需要安裝所需的 Azure AD 模組 SharePoint Online 和 Skype 的商務 Online：</span><span class="sxs-lookup"><span data-stu-id="7576d-128">You need to install the modules that are required for Azure AD, SharePoint Online, and Skype for Business Online:</span></span>
    
   - [<span data-ttu-id="7576d-129">Azure Active Directory V2</span><span class="sxs-lookup"><span data-stu-id="7576d-129">Azure Active Directory V2</span></span>](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [<span data-ttu-id="7576d-130">SharePoint Online 管理命令介面</span><span class="sxs-lookup"><span data-stu-id="7576d-130">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="7576d-131">Skype Online，企業版 Windows PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="7576d-131">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  <span data-ttu-id="7576d-p106">Windows PowerShell 需要為 Skype 的已簽署的指令碼執行商務 Online、 Exchange Online 與安全性設定&amp;規範中心。若要這樣做，請執行下列命令在提升權限的 Windows PowerShell 工作階段 （您可以選取 [**執行系統管理員身分**開啟 Windows PowerShell 視窗）。</span><span class="sxs-lookup"><span data-stu-id="7576d-p106">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center. To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a><span data-ttu-id="7576d-134">連線步驟時使用的密碼</span><span class="sxs-lookup"><span data-stu-id="7576d-134">Connection steps when using a password</span></span>

<span data-ttu-id="7576d-135">以下是連線至單一 PowerShell 視窗中的所有服務的步驟。</span><span class="sxs-lookup"><span data-stu-id="7576d-135">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="7576d-136">（使用**系統管理員身分執行**） 以管理員身分開啟 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="7576d-136">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="7576d-137">執行此命令中，並輸入您的 Office 365 工作或學校帳戶認證。</span><span class="sxs-lookup"><span data-stu-id="7576d-137">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```
  $credential = Get-Credential
  ```

3. <span data-ttu-id="7576d-138">執行此命令以連線至 Azure Active Directory (AD) 圖模組的使用 Azure Active Directory PowerShell。</span><span class="sxs-lookup"><span data-stu-id="7576d-138">Run this command to connect to Azure Active Directory (AD) using the Azure Active Directory PowerShell for Graph module.</span></span>
    
  ```
  Connect-AzureAD -Credential $credential
  ```
  
  <span data-ttu-id="7576d-139">或者，如果您使用 Microsoft Azure Active Directory Module for Windows PowerShell 模組，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="7576d-139">Alternately, if you are using the Microsoft Azure Active Directory Module for Windows PowerShell module, run this command.</span></span>
      
  ```
  Connect-MsolService -Credential $credential
 ```

4. <span data-ttu-id="7576d-p107">執行下列命令以連接至 SharePoint Online。取代_\<domainhost >_ 網域的實際值。例如，如"litwareinc.onmicrosoft.com" _ \<domainhost >_ 值是"litwareinc"。</span><span class="sxs-lookup"><span data-stu-id="7576d-p107">Run these commands to connect to SharePoint Online. Replace  _\<domainhost>_ with the actual value for your domain. For example, for "litwareinc.onmicrosoft.com", the  _\<domainhost>_ value is "litwareinc".</span></span>
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="7576d-p108">執行下列命令以連線至 Skype 商務線上。增加的警告`WSMan NetworkDelayms`值預期會在第一次連線和應忽略。</span><span class="sxs-lookup"><span data-stu-id="7576d-p108">Run these commands to connect to Skype for Business Online. A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="7576d-145">執行下列命令以連線至 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="7576d-145">Run these commands to connect to Exchange Online.</span></span>
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

>[!Note]
><span data-ttu-id="7576d-146">若要連線至 Exchange Online for Office 365 雲朵 Worldwide 以外，請參閱[Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)。</span><span class="sxs-lookup"><span data-stu-id="7576d-146">To connect to Exchange Online for Office 365 clouds other than Worldwide, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span>
>

7. <span data-ttu-id="7576d-147">執行下列命令以連線至安全性&amp;規範中心。</span><span class="sxs-lookup"><span data-stu-id="7576d-147">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
><span data-ttu-id="7576d-148">若要連線至安全性&amp;規範中心的 Office 365 雲朵以外的全球網站，請參閱[Connect to Office 365 的安全性與規範中心 PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell)。</span><span class="sxs-lookup"><span data-stu-id="7576d-148">To connect to the Security &amp; Compliance Center for Office 365 clouds other than Worldwide, see [Connect to Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span></span>
>

<span data-ttu-id="7576d-p109">以下是所有命令單一區塊圖模組的使用 Azure Active Directory PowerShell 時。指定您的網域主機名稱和一次執行所有它們。</span><span class="sxs-lookup"><span data-stu-id="7576d-p109">Here are all the commands in a single block when using the Azure Active Directory PowerShell for Graph module. Specify the name of your domain host, and then run them all at one time.</span></span>
  
```
$domainHost="<domain host name, such as litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

<span data-ttu-id="7576d-p110">或者，以下是所有的命令會在單一區塊時使用 Microsoft Azure Active Directory Module for Windows PowerShell 模組。指定您的網域主機名稱和一次執行所有它們。</span><span class="sxs-lookup"><span data-stu-id="7576d-p110">Alternately, here are all the commands in a single block when using the Microsoft Azure Active Directory Module for Windows PowerShell module. Specify the name of your domain host, and then run them all at one time.</span></span>
  
```
$domainHost="<domain host name, such as litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

<span data-ttu-id="7576d-153">當您準備好關閉 Windows PowerShell 視窗時，執行此命令以移除 Skype 作用中的工作階段的商務 Online、 Exchange Online、 SharePoint Online 和安全性&amp;規範中心：</span><span class="sxs-lookup"><span data-stu-id="7576d-153">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="7576d-154">使用多重要素驗證時的連線步驟</span><span class="sxs-lookup"><span data-stu-id="7576d-154">Connection steps when using multi-factor authentication</span></span>

<span data-ttu-id="7576d-p111">以下是連線至 Azure AD 單一區塊中的所有命令 SharePoint Online 和 Skype 的 Buiness 使用單一視窗中的多重要素驗證。指定全域管理員帳戶的使用者主要名稱 (UPN) 名稱與您的網域主機名稱和一次執行所有它們。</span><span class="sxs-lookup"><span data-stu-id="7576d-p111">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, and Skype for Buiness using multi-factor authentication in a single window. Specify the user principal name (UPN) name of a global administrator account and your domain host name, and then run them all at one time.</span></span>

````
$acctName="<UPN of a global administrator account>"
$domainHost="<domain host name, such as litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

<span data-ttu-id="7576d-157">或者，以下是所有命令時使用 Microsoft Azure Active Directory Module for Windows PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="7576d-157">Alternately, here are all the commands when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span>

````
$acctName="<UPN of a global administrator account>"
$domainHost="<domain host name, such as litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

<span data-ttu-id="7576d-158">Exchange Online 和安全性&amp;規範中心，請參閱下列主題使用多重要素驗證連線：</span><span class="sxs-lookup"><span data-stu-id="7576d-158">For Exchange Online and the Security &amp; Compliance Center, see the following topics to connect using multi-factor authentication:</span></span>

- [<span data-ttu-id="7576d-159">使用多重要素驗證連線至 Exchange Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="7576d-159">Connect to Exchange Online PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell)
- [<span data-ttu-id="7576d-160">連線至 Office 365 的安全性與規範中心 PowerShell 使用多重要素驗證</span><span class="sxs-lookup"><span data-stu-id="7576d-160">Connect to Office 365 Security & Compliance Center PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
<span data-ttu-id="7576d-161">請注意，在這兩種情況下，您必須使用不同的 Exchange Online 遠端 PowerShell 模組的工作階段進行連線。</span><span class="sxs-lookup"><span data-stu-id="7576d-161">Note that in both cases, you must connect using separate sessions of the Exchange Online Remote PowerShell Module.</span></span>


## <a name="see-also"></a><span data-ttu-id="7576d-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7576d-162">See also</span></span>

- [<span data-ttu-id="7576d-163">連線至 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7576d-163">Connect to Office 365 PowerShell</span></span>](connect-to-office-365-powershell.md)
- [<span data-ttu-id="7576d-164">使用 Office 365 PowerShell 管理 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7576d-164">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="7576d-165">使用 Office 365 PowerShell 管理使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="7576d-165">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="7576d-166">使用 Windows PowerShell 在 Office 365 中建立報告</span><span class="sxs-lookup"><span data-stu-id="7576d-166">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
