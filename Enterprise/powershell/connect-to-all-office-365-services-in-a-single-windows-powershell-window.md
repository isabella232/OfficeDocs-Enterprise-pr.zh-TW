---
title: 在單一 Windows PowerShell 視窗中連線至所有 Office 365 服務
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/28/2019
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
description: 摘要： 將 Windows PowerShell 連線到單一的 Windows PowerShell 視窗中的所有 Office 365 服務。
ms.openlocfilehash: 38221a2c9b50aaeab217016336cf4d020abd706a
ms.sourcegitcommit: 2e5e2c65a1b785e229f1f7fd5b219f1b3de96f97
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "30339511"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="33acf-103">在單一 Windows PowerShell 視窗中連線至所有 Office 365 服務</span><span class="sxs-lookup"><span data-stu-id="33acf-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

 <span data-ttu-id="33acf-104">**摘要：** 而不是管理個別 PowerShell 主控台視窗中的不同 Office 365 服務，您可以連線至所有 Office 365 服務，並從單一主控台視窗管理它們。</span><span class="sxs-lookup"><span data-stu-id="33acf-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span></span>
  
<span data-ttu-id="33acf-105">當您使用 PowerShell 來管理 Office 365 時，它可能會有最多可以有五個不同 Windows PowerShell 工作階段開啟對應至 Office 365 系統管理中心、 SharePoint Online、 Exchange Online、 商務用 Skype 線上商務和安全性&amp;合規性中心。</span><span class="sxs-lookup"><span data-stu-id="33acf-105">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Office 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="33acf-106">使用個別的 Windows PowerShell 工作階段中的五個不同的連線方法，您的桌面可能看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="33acf-106">With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![一次執行五個 Windows PowerShell 主控台](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="33acf-108">這不是最佳的管理 Office 365，因為您不能交換跨服務管理這些五個視窗之間的資料。</span><span class="sxs-lookup"><span data-stu-id="33acf-108">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management.</span></span> <span data-ttu-id="33acf-109">本主題說明如何使用 Office 365、 Skype for Business Online、 Exchange Online、 SharePoint Online 和安全性，您可以管理的 Windows PowerShell 的單一執行個體&amp;合規性中心。</span><span class="sxs-lookup"><span data-stu-id="33acf-109">This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span></span>

>[!Note]
><span data-ttu-id="33acf-110">目前本文僅包含命令，以連線至 Office 365 全球 （+ GCC） 雲端。</span><span class="sxs-lookup"><span data-stu-id="33acf-110">This article currently only contains the commands to connect to the Office 365 Worldwide (+GCC) cloud.</span></span> <span data-ttu-id="33acf-111">其他附註提供連線至其他 Office 365 定域機組的相關資訊的文章連結。</span><span class="sxs-lookup"><span data-stu-id="33acf-111">Additional notes provide links to articles with information about connecting to the other Office 365 clouds.</span></span>
>

## <a name="before-you-begin"></a><span data-ttu-id="33acf-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="33acf-112">Before you begin</span></span>

<span data-ttu-id="33acf-113">您可以從 Windows PowerShell 的單一執行個體管理所有 Office 365 之前，請考慮下列必要條件：</span><span class="sxs-lookup"><span data-stu-id="33acf-113">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="33acf-114">您用於這些程序的 Office 365工作或學校帳戶 必須是 Office 365 系統管理員角色的成員。</span><span class="sxs-lookup"><span data-stu-id="33acf-114">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role.</span></span> <span data-ttu-id="33acf-115">如需詳細資訊，請參閱[關於 Office 365 系統管理員角色](https://go.microsoft.com/fwlink/p/?LinkId=532367)。</span><span class="sxs-lookup"><span data-stu-id="33acf-115">For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span> <span data-ttu-id="33acf-116">此 Office 365 powershell，不一定所有其他 Office 365 服務的需求。</span><span class="sxs-lookup"><span data-stu-id="33acf-116">This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="33acf-117">您可以使用下列 Windows 64 位元版本：</span><span class="sxs-lookup"><span data-stu-id="33acf-117">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="33acf-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="33acf-118">Windows 10</span></span>
    
  - <span data-ttu-id="33acf-119">Windows 8.1 或 Windows 8</span><span class="sxs-lookup"><span data-stu-id="33acf-119">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="33acf-120">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="33acf-120">Windows Server 2019</span></span>
    
  - <span data-ttu-id="33acf-121">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="33acf-121">Windows Server 2016</span></span>
    
  - <span data-ttu-id="33acf-122">Windows Server 2012 R2 或 Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="33acf-122">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="33acf-123">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="33acf-123">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="33acf-124">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="33acf-124">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="33acf-125">\*您必須安裝 Microsoft.NET Framework 4.5。*x* ，然後任一 Windows Management Framework 3.0 或 Windows Management Framework 4.0。</span><span class="sxs-lookup"><span data-stu-id="33acf-125">\* You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0.</span></span> <span data-ttu-id="33acf-126">如需詳細資訊，請參閱[安裝.NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868)及[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757)或[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)。</span><span class="sxs-lookup"><span data-stu-id="33acf-126">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="33acf-127">您要用於 64 位元版本的 Windows 因為 skype 需求商務 Online 模組和其中一個 Office 365 模組。</span><span class="sxs-lookup"><span data-stu-id="33acf-127">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="33acf-128">您必須安裝 Azure ad，所需的模組 SharePoint Online 和商務用 Skype:</span><span class="sxs-lookup"><span data-stu-id="33acf-128">You need to install the modules that are required for Azure AD, SharePoint Online, and Skype for Business Online:</span></span>
    
   - [<span data-ttu-id="33acf-129">Azure Active Directory V2</span><span class="sxs-lookup"><span data-stu-id="33acf-129">Azure Active Directory V2</span></span>](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [<span data-ttu-id="33acf-130">SharePoint Online 管理命令介面</span><span class="sxs-lookup"><span data-stu-id="33acf-130">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="33acf-131">商務用 Skype Online、 商務 Windows PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="33acf-131">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  <span data-ttu-id="33acf-132">Windows PowerShell 需要執行簽署的指令碼 skype 商務 Online、 Exchange Online 和安全性設定&amp;合規性中心。</span><span class="sxs-lookup"><span data-stu-id="33acf-132">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="33acf-133">若要這麼做，請在提高權限的 Windows PowerShell 工作階段中執行下列命令 （您選取 [**執行系統管理員身分**開啟 Windows PowerShell 視窗）。</span><span class="sxs-lookup"><span data-stu-id="33acf-133">To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a><span data-ttu-id="33acf-134">連線步驟時使用的密碼</span><span class="sxs-lookup"><span data-stu-id="33acf-134">Connection steps when using a password</span></span>

<span data-ttu-id="33acf-135">以下是步驟來連接至單一 PowerShell 視窗中的所有服務。</span><span class="sxs-lookup"><span data-stu-id="33acf-135">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="33acf-136">開啟 Windows PowerShell 以系統管理員身分 （使用**系統管理員身分執行**）。</span><span class="sxs-lookup"><span data-stu-id="33acf-136">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="33acf-137">執行此命令，並輸入您的 Office 365 工作或學校帳戶認證。</span><span class="sxs-lookup"><span data-stu-id="33acf-137">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```
  $credential = Get-Credential
  ```

3. <span data-ttu-id="33acf-138">執行此命令來連接至 Azure Active Directory (AD) 針對 Graph 模組中使用 PowerShell 的 Azure Active Directory。</span><span class="sxs-lookup"><span data-stu-id="33acf-138">Run this command to connect to Azure Active Directory (AD) using the Azure Active Directory PowerShell for Graph module.</span></span>
    
  ```
  Connect-AzureAD -Credential $credential
  ```
  
  <span data-ttu-id="33acf-139">或者，如果您使用 Microsoft Azure Active Directory 模組的 Windows PowerShell 模組，執行此命令。</span><span class="sxs-lookup"><span data-stu-id="33acf-139">Alternately, if you are using the Microsoft Azure Active Directory Module for Windows PowerShell module, run this command.</span></span>
      
  ```
  Connect-MsolService -Credential $credential
 ```

4. <span data-ttu-id="33acf-140">執行這些命令，以連線至 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="33acf-140">Run these commands to connect to SharePoint Online.</span></span> <span data-ttu-id="33acf-141">取代_\<domainhost>_ 與您的網域的實際值。</span><span class="sxs-lookup"><span data-stu-id="33acf-141">Replace  _\<domainhost>_ with the actual value for your domain.</span></span> <span data-ttu-id="33acf-142">例如，針對 「 litwareinc.onmicrosoft.com 「 _ \<domainhost>_ 值是 「 litwareinc 」。</span><span class="sxs-lookup"><span data-stu-id="33acf-142">For example, for "litwareinc.onmicrosoft.com", the  _\<domainhost>_ value is "litwareinc".</span></span>
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="33acf-143">執行這些命令，以連線至 Skype for Business Online。</span><span class="sxs-lookup"><span data-stu-id="33acf-143">Run these commands to connect to Skype for Business Online.</span></span> <span data-ttu-id="33acf-144">關於增加的警告`WSMan NetworkDelayms`值預期會在第一次連線並應忽略。</span><span class="sxs-lookup"><span data-stu-id="33acf-144">A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="33acf-145">執行這些命令，以連線至 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="33acf-145">Run these commands to connect to Exchange Online.</span></span>
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

>[!Note]
><span data-ttu-id="33acf-146">若要連線至 Exchange Online for Office 365 定域機組以外的全球網站，請參閱[Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)。</span><span class="sxs-lookup"><span data-stu-id="33acf-146">To connect to Exchange Online for Office 365 clouds other than Worldwide, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span>
>

7. <span data-ttu-id="33acf-147">執行這些命令，以連線至安全性&amp;合規性中心。</span><span class="sxs-lookup"><span data-stu-id="33acf-147">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
><span data-ttu-id="33acf-148">若要連接到安全性&amp;以外的全球網站，了解 Office 365 雲端的合規性中心，請參閱[Connect to Office 365 安全性 & 合規性中心 PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell)。</span><span class="sxs-lookup"><span data-stu-id="33acf-148">To connect to the Security &amp; Compliance Center for Office 365 clouds other than Worldwide, see [Connect to Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span></span>
>

<span data-ttu-id="33acf-149">針對 Graph 模組中使用 PowerShell 的 Azure Active Directory 時，以下是在單一區塊中的所有命令。</span><span class="sxs-lookup"><span data-stu-id="33acf-149">Here are all the commands in a single block when using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="33acf-150">指定您的網域主機名稱，然後再一次執行全部。</span><span class="sxs-lookup"><span data-stu-id="33acf-150">Specify the name of your domain host, and then run them all at one time.</span></span>
  
```
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

<span data-ttu-id="33acf-151">或者，以下是所有命令在單一區塊時使用 Microsoft Azure Active Directory 模組的 Windows PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="33acf-151">Alternately, here are all the commands in a single block when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span> <span data-ttu-id="33acf-152">指定您的網域主機名稱，然後再一次執行全部。</span><span class="sxs-lookup"><span data-stu-id="33acf-152">Specify the name of your domain host, and then run them all at one time.</span></span>
  
```
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

<span data-ttu-id="33acf-153">當您準備好要關閉 Windows PowerShell 視窗時，執行此命令可移除使用中的工作階段 skype for Business Online、 Exchange Online、 SharePoint Online 和安全性&amp;合規性中心：</span><span class="sxs-lookup"><span data-stu-id="33acf-153">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="33acf-154">連線步驟時使用多重要素驗證</span><span class="sxs-lookup"><span data-stu-id="33acf-154">Connection steps when using multi-factor authentication</span></span>

<span data-ttu-id="33acf-155">以下是在單一的區塊，以連線到 Azure AD 中的 [所有命令 SharePoint Online 和商務用 Skype Buiness 針對 Graph 模組中使用 PowerShell 的 Azure Active Directory 在單一視窗中使用多重要素驗證。</span><span class="sxs-lookup"><span data-stu-id="33acf-155">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, and Skype for Buiness using multi-factor authentication in a single window using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="33acf-156">指定的使用者帳戶的使用者主要名稱 (UPN) 名稱與您的網域主機名稱，然後再一次執行全部。</span><span class="sxs-lookup"><span data-stu-id="33acf-156">Specify the user principal name (UPN) name of a user account and your domain host name, and then run them all at one time.</span></span>

````
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

<span data-ttu-id="33acf-157">或者，以下是所有命令時使用 Microsoft Azure Active Directory 模組的 Windows PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="33acf-157">Alternately, here are all the commands when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span>

````
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

<span data-ttu-id="33acf-158">Exchange Online 和安全性&amp;合規性中心，請參閱下列主題，以使用多重要素驗證連線：</span><span class="sxs-lookup"><span data-stu-id="33acf-158">For Exchange Online and the Security &amp; Compliance Center, see the following topics to connect using multi-factor authentication:</span></span>

- [<span data-ttu-id="33acf-159">使用多重要素驗證連線至 Exchange Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="33acf-159">Connect to Exchange Online PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell)
- [<span data-ttu-id="33acf-160">連線至 Office 365 安全性 & 合規性中心 PowerShell 中使用多重要素驗證</span><span class="sxs-lookup"><span data-stu-id="33acf-160">Connect to Office 365 Security & Compliance Center PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
<span data-ttu-id="33acf-161">請注意，在這兩種情況下，您必須使用不同的工作階段的 Exchange Online 遠端 PowerShell 模組來連線。</span><span class="sxs-lookup"><span data-stu-id="33acf-161">Note that in both cases, you must connect using separate sessions of the Exchange Online Remote PowerShell Module.</span></span>


## <a name="see-also"></a><span data-ttu-id="33acf-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33acf-162">See also</span></span>

- [<span data-ttu-id="33acf-163">連線至 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="33acf-163">Connect to Office 365 PowerShell</span></span>](connect-to-office-365-powershell.md)
- [<span data-ttu-id="33acf-164">使用 Office 365 PowerShell 管理 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="33acf-164">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="33acf-165">使用 Office 365 PowerShell 管理使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="33acf-165">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="33acf-166">使用 Windows PowerShell 在 Office 365 中建立報告</span><span class="sxs-lookup"><span data-stu-id="33acf-166">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
