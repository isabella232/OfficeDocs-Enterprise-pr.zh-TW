---
title: 在單一 Windows PowerShell 視窗中連線至所有 Office 365 服務
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: 摘要：將 Windows PowerShell 連線到單一 Windows PowerShell 視窗中的所有 Office 365 服務。
ms.openlocfilehash: d47f4dab4938bd02be25525d2912604f676079db
ms.sourcegitcommit: 58aa8b2e89685490f849e0392d566b7bfb7b933e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2020
ms.locfileid: "43547751"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="2f5f0-103">在單一 Windows PowerShell 視窗中連線至所有 Office 365 服務</span><span class="sxs-lookup"><span data-stu-id="2f5f0-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

<span data-ttu-id="2f5f0-104">當您使用 PowerShell 來管理 Office 365 時，最多可以同時開啟五個不同的 Windows PowerShell 會話，其對應于 Microsoft 365 系統管理中心、SharePoint 線上、Exchange Online、商務用 Skype Online、Microsoft 團隊及安全性&amp;與合規性中心。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-104">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Microsoft 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, Microsoft Teams, and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="2f5f0-105">您的桌面可以在不同的 Windows PowerShell 會話中使用五種不同的連接方法，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2f5f0-105">With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![一次執行五個 Windows PowerShell 主控台](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="2f5f0-107">這在管理 Office 365 時並不是最佳的，因為您無法在這五個 windows 間交換資料，以進行跨服務管理。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-107">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management.</span></span> <span data-ttu-id="2f5f0-108">本主題說明如何使用單一 Windows PowerShell 實例，從中管理 Office 365、商務用 Skype Online、Exchange Online、SharePoint 線上、Microsoft 團隊及安全性&amp;與合規性中心。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-108">This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, Microsoft Teams, and the Security &amp; Compliance Center.</span></span>

>[!Note]
><span data-ttu-id="2f5f0-109">本文目前只包含連接到 Office 365 全球（+ GCC）雲端的命令。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-109">This article currently only contains the commands to connect to the Office 365 Worldwide (+GCC) cloud.</span></span> <span data-ttu-id="2f5f0-110">其他附注提供與其他 Office 365 雲端相關之相關資訊的文章連結。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-110">Additional notes provide links to articles with information about connecting to the other Office 365 clouds.</span></span>
>

## <a name="before-you-begin"></a><span data-ttu-id="2f5f0-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="2f5f0-111">Before you begin</span></span>

<span data-ttu-id="2f5f0-112">在您可以從單一 Windows PowerShell 實例管理所有 Office 365 之前，請考慮下列必要條件：</span><span class="sxs-lookup"><span data-stu-id="2f5f0-112">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="2f5f0-113">您用於這些程序的 Office 365工作或學校帳戶 必須是 Office 365 系統管理員角色的成員。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-113">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role.</span></span> <span data-ttu-id="2f5f0-114">如需詳細資訊，請參閱[關於 Office 365 系統管理員角色](https://go.microsoft.com/fwlink/p/?LinkId=532367)。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-114">For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span> <span data-ttu-id="2f5f0-115">這是 Office 365 PowerShell 的需求，不一定是所有其他 Office 365 服務。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-115">This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="2f5f0-116">您可以使用下列 Windows 64 位元版本：</span><span class="sxs-lookup"><span data-stu-id="2f5f0-116">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="2f5f0-117">Windows 10</span><span class="sxs-lookup"><span data-stu-id="2f5f0-117">Windows 10</span></span>
    
  - <span data-ttu-id="2f5f0-118">Windows 8.1 或 Windows 8</span><span class="sxs-lookup"><span data-stu-id="2f5f0-118">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="2f5f0-119">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="2f5f0-119">Windows Server 2019</span></span>
    
  - <span data-ttu-id="2f5f0-120">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="2f5f0-120">Windows Server 2016</span></span>
    
  - <span data-ttu-id="2f5f0-121">Windows Server 2012 R2 或 Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="2f5f0-121">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="2f5f0-122">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="2f5f0-122">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="2f5f0-123">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="2f5f0-123">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="2f5f0-124">\*您必須安裝 Microsoft .NET Framework 4.5。*x* ，然後是 Windows management framework 3.0 或 Windows management framework 4.0。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-124">\* You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0.</span></span> <span data-ttu-id="2f5f0-125">如需詳細資訊，請參閱[安裝 .Net Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868)和[windows management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757)或[windows management framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-125">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="2f5f0-126">您必須使用64位版本的 Windows，因為商務用 Skype Online 模組和其中一個 Office 365 模組的需求。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-126">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="2f5f0-127">您需要安裝 Azure AD、Exchange Online、SharePoint Online、商務用 Skype Online 及小組所需的模組：</span><span class="sxs-lookup"><span data-stu-id="2f5f0-127">You need to install the modules that are required for Azure AD, Exchange Online, SharePoint Online, Skype for Business Online and Teams:</span></span>
    
   - [<span data-ttu-id="2f5f0-128">Azure Active Directory V2</span><span class="sxs-lookup"><span data-stu-id="2f5f0-128">Azure Active Directory V2</span></span>](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [<span data-ttu-id="2f5f0-129">SharePoint 線上管理命令介面</span><span class="sxs-lookup"><span data-stu-id="2f5f0-129">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="2f5f0-130">商務用 Skype Online、Windows PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="2f5f0-130">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
   - [<span data-ttu-id="2f5f0-131">Exchange Online PowerShell V2</span><span class="sxs-lookup"><span data-stu-id="2f5f0-131">Exchange Online PowerShell V2</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell-v2/exchange-online-powershell-v2?view=exchange-ps#install-and-maintain-the-exchange-online-powershell-v2-module)
   - [<span data-ttu-id="2f5f0-132">小組 PowerShell 概述</span><span class="sxs-lookup"><span data-stu-id="2f5f0-132">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
    
-  <span data-ttu-id="2f5f0-133">Windows PowerShell 必須設定為為商務用 Skype Online 和安全性&amp;與合規性中心執行已簽署的腳本。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-133">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="2f5f0-134">若要這麼做，請在已提升許可權的 Windows PowerShell 會話中執行下列命令（您可以選取 [以**系統管理員身分執行**] 視窗 PowerShell 視窗）。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-134">To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```powershell
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a><span data-ttu-id="2f5f0-135">使用密碼時的連接步驟</span><span class="sxs-lookup"><span data-stu-id="2f5f0-135">Connection steps when using a password</span></span>

<span data-ttu-id="2f5f0-136">以下是連接至單一 PowerShell 視窗中所有服務的步驟。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-136">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="2f5f0-137">開啟 [Windows PowerShell]。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-137">Open Windows PowerShell.</span></span>
    
2. <span data-ttu-id="2f5f0-138">執行這個命令，並輸入您的 Office 365 工作或學校帳號憑證。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-138">Run this command and enter your Office 365 work or school account credentials.</span></span>
    
  ```powershell
  $credential = Get-Credential
  ```

3. <span data-ttu-id="2f5f0-139">使用此命令，使用適用于 Graph 模組的 Azure Active Directory PowerShell，連線到 Azure Active Directory （AD）。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-139">Run this command to connect to Azure Active Directory (AD) using the Azure Active Directory PowerShell for Graph module.</span></span>
    
  ```powershell
  Connect-AzureAD -Credential $credential
  ```
  
  <span data-ttu-id="2f5f0-140">或者，如果您是使用 Microsoft Azure Active Directory Module for Windows PowerShell module，請執行此命令。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-140">Alternately, if you are using the Microsoft Azure Active Directory Module for Windows PowerShell module, run this command.</span></span>
      
  ```powershell
  Connect-MsolService -Credential $credential
 ```

>[!Note]
><span data-ttu-id="2f5f0-141">PowerShell Core 不支援適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組和名稱有 **Msol** 的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-141">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="2f5f0-142">若要繼續使用這些 Cmdlet，您必須從 Windows PowerShell 執行。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-142">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

4. <span data-ttu-id="2f5f0-143">執行這些命令，以連線至 SharePoint 線上。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-143">Run these commands to connect to SharePoint Online.</span></span> <span data-ttu-id="2f5f0-144">以您的網域的實際值取代_ \<domainhost>_ 。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-144">Replace  _\<domainhost>_ with the actual value for your domain.</span></span> <span data-ttu-id="2f5f0-145">例如，若為 "litwareinc.onmicrosoft.com"，則_ \<domainhost>_ 值為 "litwareinc"。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-145">For example, for "litwareinc.onmicrosoft.com", the  _\<domainhost>_ value is "litwareinc".</span></span>
    
  ```powershell
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="2f5f0-146">執行這些命令，以連線至商務用 Skype Online。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-146">Run these commands to connect to Skype for Business Online.</span></span> <span data-ttu-id="2f5f0-147">您第一次連線`WSMan NetworkDelayms`時預計會增加值，而且應該忽略此警告。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-147">A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="2f5f0-148">執行下列命令以連線至 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-148">Run this command to connect to Exchange Online.</span></span>
    
  ```powershell
  Connect-ExchangeOnline -Credential $credential -ShowProgress $true
  ```

>[!Note]
><span data-ttu-id="2f5f0-149">若要連接至全球以外的 Office 365 雲端的 Exchange Online，請使用 **-ExchangeEnvironmentName**參數。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-149">To connect to Exchange Online for Office 365 clouds other than Worldwide, use the **-ExchangeEnvironmentName** parameter.</span></span> <span data-ttu-id="2f5f0-150">如需詳細資訊，請參閱[Connect-ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps) 。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-150">See [Connect-ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps) for more information.</span></span>
>

7. <span data-ttu-id="2f5f0-151">執行這些命令，以連線至小組 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-151">Run these commands to connect to Teams PowerShell.</span></span>
    
  ```powershell
  Import-Module MicrosoftTeams
  Connect-MicrosoftTeams -Credential $credential
  ```
  
>[!Note]
><span data-ttu-id="2f5f0-152">若要連線至全球以外的 Microsoft 團隊雲彩，請參閱[MicrosoftTeams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps)。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-152">To connect to Microsoft Teams clouds other than Worldwide, see [Connect-MicrosoftTeams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps).</span></span>
>

8. <span data-ttu-id="2f5f0-153">執行這些命令，以連線至安全性&amp;與合規性中心。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-153">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```powershell
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
><span data-ttu-id="2f5f0-154">若要連接至全球&amp;以外的 Office 365 雲端的安全性與合規性中心，請參閱[connect To Office 365 Security & 合規性中心 PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell)。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-154">To connect to the Security &amp; Compliance Center for Office 365 clouds other than Worldwide, see [Connect to Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span></span>
>

<span data-ttu-id="2f5f0-155">以下是使用適用于 Graph 模組的 Azure Active Directory PowerShell 時，單一區塊中的所有命令。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-155">Here are all the commands in a single block when using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="2f5f0-156">指定您的功能變數名稱主機名稱稱，然後一次執行一次。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-156">Specify the name of your domain host, and then run them all at one time.</span></span>
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
Connect-ExchangeOnline -Credential $credential -ShowProgress $true
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

<span data-ttu-id="2f5f0-157">此外，在使用 Microsoft Azure Active Directory Module for Windows PowerShell Module 時，以下是單一區塊中的所有命令。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-157">Alternately, here are all the commands in a single block when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span> <span data-ttu-id="2f5f0-158">指定您的功能變數名稱主機名稱稱，然後一次執行一次。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-158">Specify the name of your domain host, and then run them all at one time.</span></span>
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
Connect-ExchangeOnline -Credential $credential -ShowProgress $true
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

<span data-ttu-id="2f5f0-159">當您準備好關閉 [Windows PowerShell] 視窗時，請執行下列命令，以移除使用中的商務用 Skype Online、SharePoint 線上、安全性&amp;與合規性中心及小組的會話：</span><span class="sxs-lookup"><span data-stu-id="2f5f0-159">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, SharePoint Online, the Security &amp; Compliance Center, and Teams:</span></span>
  
```powershell
Remove-PSSession $sfboSession ; Remove-PSSession $SccSession ; Disconnect-SPOService ; Disconnect-MicrosoftTeams 
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="2f5f0-160">使用多重要素驗證時的連接步驟</span><span class="sxs-lookup"><span data-stu-id="2f5f0-160">Connection steps when using multi-factor authentication</span></span>

<span data-ttu-id="2f5f0-161">以下是單一區塊中的所有命令，可透過使用圖形模組之 Azure Active Directory PowerShell，在單一視窗中使用多重要素驗證連線至 Azure AD、SharePoint 線上、商務用 Skype、Exchange Online 和團隊。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-161">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, Skype for Business, Exchange Online, and Teams using multi-factor authentication in a single window using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="2f5f0-162">指定使用者帳戶的使用者主要名稱（UPN）名稱和您的網域主機名稱，然後一次執行全部。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-162">Specify the user principal name (UPN) name of a user account and your domain host name, and then run them all at one time.</span></span>

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
#Exchange Online
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Teams
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

<span data-ttu-id="2f5f0-163">或者，您也可以使用 Microsoft Azure Active Directory Module for Windows PowerShell module] 模組時使用的所有命令。</span><span class="sxs-lookup"><span data-stu-id="2f5f0-163">Alternately, here are all the commands when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span>

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
#Exchange Online
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Teams
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

<span data-ttu-id="2f5f0-164">如需安全&amp;規範中心，請參閱[connect To Office 365 Security & 合規性中心 PowerShell 使用多重要素驗證](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)連線以使用多重要素驗證：</span><span class="sxs-lookup"><span data-stu-id="2f5f0-164">For the Security &amp; Compliance Center, see [Connect to Office 365 Security & Compliance Center PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) to connect using multi-factor authentication:</span></span>

## <a name="see-also"></a><span data-ttu-id="2f5f0-165">請參閱</span><span class="sxs-lookup"><span data-stu-id="2f5f0-165">See also</span></span>

- [<span data-ttu-id="2f5f0-166">連線至 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2f5f0-166">Connect to Office 365 PowerShell</span></span>](connect-to-office-365-powershell.md)
- [<span data-ttu-id="2f5f0-167">使用 Office 365 PowerShell 管理 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="2f5f0-167">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="2f5f0-168">使用 Office 365 管理使用者帳戶、授權和群組 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2f5f0-168">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="2f5f0-169">使用 Windows PowerShell 在 Office 365 中建立報告</span><span class="sxs-lookup"><span data-stu-id="2f5f0-169">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
