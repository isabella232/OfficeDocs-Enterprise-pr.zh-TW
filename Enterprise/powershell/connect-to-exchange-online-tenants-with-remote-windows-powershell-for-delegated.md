---
title: 利用適用於委派存取權限 (DAP) 合作夥伴的遠端 Windows PowerShell 連線至 Exchange Online 租用戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: 摘要：使用遠端 Windows PowerShell 搭配 DelegatedOrg 值連線至 Exchange Online。
ms.openlocfilehash: 4a9f08325fc56308b27467423b047375985562c5
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997369"
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="da1b9-103">利用適用於委派存取權限 (DAP) 合作夥伴的遠端 Windows PowerShell 連線至 Exchange Online 租用戶</span><span class="sxs-lookup"><span data-stu-id="da1b9-103">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

> [!IMPORTANT]
> <span data-ttu-id="da1b9-104">The procedures in this topic are only for Delegated Access Permission (DAP) partners.</span><span class="sxs-lookup"><span data-stu-id="da1b9-104">The procedures in this topic are only for Delegated Access Permission (DAP) partners.</span></span> <span data-ttu-id="da1b9-105">If you aren't a DAP partner, don't use the procedures in this topic.</span><span class="sxs-lookup"><span data-stu-id="da1b9-105">If you aren't a DAP partner, don't use the procedures in this topic.</span></span> 
  
<span data-ttu-id="da1b9-106">DAP 合作夥伴是新聞訂閱方式和雲端解決方案提供者 (CSP) 合作夥伴。</span><span class="sxs-lookup"><span data-stu-id="da1b9-106">DAP partners are Syndication and Cloud Solution Providers (CSP) partners.</span></span> <span data-ttu-id="da1b9-107">他們通常是其他公司的網路或電信服務提供者。</span><span class="sxs-lookup"><span data-stu-id="da1b9-107">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="da1b9-108">他們會在提供給客戶的服務方案中搭售 訂閱。</span><span class="sxs-lookup"><span data-stu-id="da1b9-108">They bundle subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="da1b9-109">他們擁有一個合作夥伴租使用者，它會自動授與其 Microsoft 365 客戶租用的「管理」（AOBO）許可權，讓他們能管理及報告其所有客戶租用。</span><span class="sxs-lookup"><span data-stu-id="da1b9-109">They own a partner tenancy that is automatically granted Administer On Behalf Of (AOBO) permissions to their Microsoft 365 customer tenancies so they can administer and report on all of their customer tenancies.</span></span>

<span data-ttu-id="da1b9-110">「合作合作夥伴」可以使用 Exchange Online PowerShell 管理客戶 Exchange Online 設定，並從命令列取得 Microsoft 365 報告。</span><span class="sxs-lookup"><span data-stu-id="da1b9-110">DAP partners can use Exchange Online PowerShell to manage customer Exchange Online settings and get Microsoft 365 reports from the command line.</span></span> <span data-ttu-id="da1b9-111">您可在本機電腦上使用 Windows PowerShell 建立對 Exchange Online 的遠端 PowerShell 工作階段。</span><span class="sxs-lookup"><span data-stu-id="da1b9-111">You use Windows PowerShell on your local computer to create a remote PowerShell session to Exchange Online.</span></span> <span data-ttu-id="da1b9-112">這是一個簡單的三步驟程式，您可以在其中輸入您的認證、提供必要的連線設定，然後將 Exchange Online Cmdlet 匯入您的本機 Windows PowerShell 會話，讓您可以使用這些程式。</span><span class="sxs-lookup"><span data-stu-id="da1b9-112">It's a simple three-step process where you enter your credentials, provide the required connection settings, and then import the Exchange Online cmdlets into your local Windows PowerShell session so that you can use them.</span></span>

> [!NOTE]
> <span data-ttu-id="da1b9-113">DAP partners can't use the procedures in [Connect to Exchange Online PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell) to connect to their customer tenant organizations in Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="da1b9-113">DAP partners can't use the procedures in [Connect to Exchange Online PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell) to connect to their customer tenant organizations in Exchange Online PowerShell.</span></span> <span data-ttu-id="da1b9-114">MFA and the Exchange Online Remote PowerShell Module don't work with delegated authentication.</span><span class="sxs-lookup"><span data-stu-id="da1b9-114">MFA and the Exchange Online Remote PowerShell Module don't work with delegated authentication.</span></span>
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="da1b9-115">開始之前有哪些須知？</span><span class="sxs-lookup"><span data-stu-id="da1b9-115">What do you need to know before you begin?</span></span>

- <span data-ttu-id="da1b9-116">預估完成時間：5 分鐘</span><span class="sxs-lookup"><span data-stu-id="da1b9-116">Estimated time to complete: 5 minutes</span></span>

- <span data-ttu-id="da1b9-117">您可以使用下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="da1b9-117">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="da1b9-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="da1b9-118">Windows 10</span></span>

  - <span data-ttu-id="da1b9-119">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="da1b9-119">Windows 8.1</span></span>

  - <span data-ttu-id="da1b9-120">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="da1b9-120">Windows Server 2016</span></span>

  - <span data-ttu-id="da1b9-121">Windows Server 2012 或 Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="da1b9-121">Windows Server 2012 or Windows Server 2012 R2</span></span>

  - <span data-ttu-id="da1b9-122">Windows 7 Service Pack 1 (SP1)<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="da1b9-122">Windows 7 Service Pack 1 (SP1)<sup>\*</sup></span></span>

  - <span data-ttu-id="da1b9-123">Windows Server 2008 R2 SP1<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="da1b9-123">Windows Server 2008 R2 SP1<sup>\*</sup></span></span>

    <span data-ttu-id="da1b9-124"><sup>\*</sup> For older versions of Windows, you need to install the Microsoft.NET Framework 4.5 or later and then an updated version of the Windows Management Framework: 3.0, 4.0, or 5.1 (only one).</span><span class="sxs-lookup"><span data-stu-id="da1b9-124"><sup>\*</sup> For older versions of Windows, you need to install the Microsoft.NET Framework 4.5 or later and then an updated version of the Windows Management Framework: 3.0, 4.0, or 5.1 (only one).</span></span> <span data-ttu-id="da1b9-125">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868), [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757), [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344), and [Windows Management Framework 5.1](https://aka.ms/wmf5download).</span><span class="sxs-lookup"><span data-stu-id="da1b9-125">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868), [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757), [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344), and [Windows Management Framework 5.1](https://aka.ms/wmf5download).</span></span>

- <span data-ttu-id="da1b9-126">Windows PowerShell needs to be configured to run scripts, and by default, it isn't.</span><span class="sxs-lookup"><span data-stu-id="da1b9-126">Windows PowerShell needs to be configured to run scripts, and by default, it isn't.</span></span> <span data-ttu-id="da1b9-127">You'll get the following error when you try to connect:</span><span class="sxs-lookup"><span data-stu-id="da1b9-127">You'll get the following error when you try to connect:</span></span>

  `Files cannot be loaded because running scripts is disabled on this system. Provide a valid certificate with which to sign the files.`

  <span data-ttu-id="da1b9-128">若要要求您從網際網路下載的所有 Windows PowerShell 指令碼都是由信任的發行者簽署，請在提高權限的 Windows PowerShell 視窗 (透過選取 [以系統管理員身分執行]\*\*\*\* 而開啟的 Windows PowerShell 視窗) 中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="da1b9-128">To require all PowerShell scripts that you download from the internet are signed by a trusted publisher, run the following command in an elevated Windows PowerShell window (a Windows PowerShell window you open by selecting **Run as administrator**):</span></span>

    ```
    Set-ExecutionPolicy RemoteSigned
    ```

  <span data-ttu-id="da1b9-129">您只需在電腦上設定此設定一次，而不用在每次連線時進行設定。</span><span class="sxs-lookup"><span data-stu-id="da1b9-129">You need to configure this setting only once on your computer, not every time you connect.</span></span>

- <span data-ttu-id="da1b9-130">如需適用於本主題之程序的鍵盤快速鍵相關資訊，請參閱 [Exchange 系統管理中心的鍵盤快速鍵](https://go.microsoft.com/fwlink/p/?LinkId=534017)。</span><span class="sxs-lookup"><span data-stu-id="da1b9-130">For information about keyboard shortcuts that might apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](https://go.microsoft.com/fwlink/p/?LinkId=534017).</span></span>

## <a name="connect-to-exchange-online-for-customer-organizations"></a><span data-ttu-id="da1b9-131">連線到客戶組織的 Exchange Online</span><span class="sxs-lookup"><span data-stu-id="da1b9-131">Connect to Exchange Online for customer organizations</span></span>

1. <span data-ttu-id="da1b9-132">在您的本機電腦上開啟 Windows PowerShell，並執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="da1b9-132">On your local computer, open Windows PowerShell and run the following command.</span></span>
    
    ```
    $UserCredential = Get-Credential
    ```

    <span data-ttu-id="da1b9-133">在 [Windows PowerShell 認證要求]\*\*\*\* 對話方塊中，輸入您的 DAP 系統管理員使用者名稱和密碼，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="da1b9-133">In the **Windows PowerShell Credential Request** dialog box, enter your DAP administrator user name and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="da1b9-134">_\<customer tenant domain name\>_ 以您想要連線的租使用者功能變數名稱取代，並執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="da1b9-134">Replace _\<customer tenant domain name\>_ with the name of the tenant domain that you want to connect to, and run the following command:</span></span>
    
    ```
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name> -Credential $UserCredential -Authentication Basic -AllowRedirection
    ```

    <span data-ttu-id="da1b9-135">此命令中的重要步驟是指定可存取報告資訊的客戶。</span><span class="sxs-lookup"><span data-stu-id="da1b9-135">The key step in this command is specifying which customer to access for the reporting information.</span></span> <span data-ttu-id="da1b9-136">您可以在_ConnectionURI_參數中，以的值提供初始功能變數名稱的 FQDN `?DelegatedOrg=` 。</span><span class="sxs-lookup"><span data-stu-id="da1b9-136">You do this in the  _ConnectionURI_ parameter, where you provide the FQDN of the initial domain name as the value for `?DelegatedOrg=`.</span></span> <span data-ttu-id="da1b9-137">此值表示要連接的正確 Exchange Online PowerShell 端點。</span><span class="sxs-lookup"><span data-stu-id="da1b9-137">This value indicates the correct Exchange Online PowerShell endpoint to connect to.</span></span> <span data-ttu-id="da1b9-138">在每次執行報告時，遠端 PowerShell 都必須在特定客戶的內容中連接至 Microsoft 365 報告。</span><span class="sxs-lookup"><span data-stu-id="da1b9-138">Remote PowerShell must connect to Microsoft 365 reporting in the context of a specific customer each time a report is run.</span></span> <span data-ttu-id="da1b9-139">在您連線至 Exchange Online PowerShell 之後，所有後續命令都會在客戶的上下文中執行，讓您可以存取客戶的所有可用報告。</span><span class="sxs-lookup"><span data-stu-id="da1b9-139">After you connect to Exchange Online PowerShell, all subsequent commands are run in the context of the customer, which gives you access to all of the available reports for the customer.</span></span>
    
3. <span data-ttu-id="da1b9-140">執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="da1b9-140">Run the following command.</span></span>
    
    ```
    Import-PSSession $Session
    ```

> [!NOTE]
> <span data-ttu-id="da1b9-141">There's a limit of three simultaneous sessions that can run under one account.</span><span class="sxs-lookup"><span data-stu-id="da1b9-141">There's a limit of three simultaneous sessions that can run under one account.</span></span> <span data-ttu-id="da1b9-142">Be sure to disconnect the remote PowerShell session when you're finished.</span><span class="sxs-lookup"><span data-stu-id="da1b9-142">Be sure to disconnect the remote PowerShell session when you're finished.</span></span> <span data-ttu-id="da1b9-143">If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote PowerShell sessions available to you, and you'll need to wait for the sessions to expire.</span><span class="sxs-lookup"><span data-stu-id="da1b9-143">If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote PowerShell sessions available to you, and you'll need to wait for the sessions to expire.</span></span> <span data-ttu-id="da1b9-144">To disconnect the remote PowerShell session, run the following command:</span><span class="sxs-lookup"><span data-stu-id="da1b9-144">To disconnect the remote PowerShell session, run the following command:</span></span>

```
Remove-PSSession $Session
```
  
## <a name="how-do-you-know-this-worked"></a><span data-ttu-id="da1b9-145">如何知道這是否正常運作？</span><span class="sxs-lookup"><span data-stu-id="da1b9-145">How do you know this worked?</span></span>

<span data-ttu-id="da1b9-146">After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar.</span><span class="sxs-lookup"><span data-stu-id="da1b9-146">After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar.</span></span> <span data-ttu-id="da1b9-147">If you don't receive any errors, you connected successfully.</span><span class="sxs-lookup"><span data-stu-id="da1b9-147">If you don't receive any errors, you connected successfully.</span></span> <span data-ttu-id="da1b9-148">A quick test is to run an Exchange Online cmdlet (for example, **Get-Mailbox**) and see the results.</span><span class="sxs-lookup"><span data-stu-id="da1b9-148">A quick test is to run an Exchange Online cmdlet (for example, **Get-Mailbox**) and see the results.</span></span>
  
<span data-ttu-id="da1b9-149">如果出現錯誤，請檢查下列需求：</span><span class="sxs-lookup"><span data-stu-id="da1b9-149">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="da1b9-150">A common problem is an incorrect password.</span><span class="sxs-lookup"><span data-stu-id="da1b9-150">A common problem is an incorrect password.</span></span> <span data-ttu-id="da1b9-151">Run the three steps again and pay close attention to the user name and password you enter in Step 1.</span><span class="sxs-lookup"><span data-stu-id="da1b9-151">Run the three steps again and pay close attention to the user name and password you enter in Step 1.</span></span>
    
- <span data-ttu-id="da1b9-152">The account you use to connect to Exchange Online must be enabled for remote PowerShell.</span><span class="sxs-lookup"><span data-stu-id="da1b9-152">The account you use to connect to Exchange Online must be enabled for remote PowerShell.</span></span> <span data-ttu-id="da1b9-153">For more information, see [Enable or disable access to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span><span class="sxs-lookup"><span data-stu-id="da1b9-153">For more information, see [Enable or disable access to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span></span>
    
- <span data-ttu-id="da1b9-154">TCP port 80 traffic needs to be open between your local computer and Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="da1b9-154">TCP port 80 traffic needs to be open between your local computer and Exchange Online.</span></span> <span data-ttu-id="da1b9-155">It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.</span><span class="sxs-lookup"><span data-stu-id="da1b9-155">It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.</span></span>
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a><span data-ttu-id="da1b9-156">利用 Invoke-Command 直接呼叫 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="da1b9-156">Call the cmdlet directly with Invoke-Command</span></span>

<span data-ttu-id="da1b9-157">Importing a remote PowerShell session (Step 3) can be a lengthy process because it brings in _all_ Exchange Online cmdlets.</span><span class="sxs-lookup"><span data-stu-id="da1b9-157">Importing a remote PowerShell session (Step 3) can be a lengthy process because it brings in _all_ Exchange Online cmdlets.</span></span> <span data-ttu-id="da1b9-158">This can be an issue in batch processing (for example, when you're running reports or making bulk changes for different tenants).</span><span class="sxs-lookup"><span data-stu-id="da1b9-158">This can be an issue in batch processing (for example, when you're running reports or making bulk changes for different tenants).</span></span> <span data-ttu-id="da1b9-159">As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**.</span><span class="sxs-lookup"><span data-stu-id="da1b9-159">As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**.</span></span> <span data-ttu-id="da1b9-160">For example, to call the **Get-Milbox** cmdlet, substitute this syntax for the `Import-PSSession $Session` command in Step 3:</span><span class="sxs-lookup"><span data-stu-id="da1b9-160">For example, to call the **Get-Milbox** cmdlet, substitute this syntax for the `Import-PSSession $Session` command in Step 3:</span></span>
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a><span data-ttu-id="da1b9-161">其他報告 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="da1b9-161">More reporting cmdlets</span></span>

<span data-ttu-id="da1b9-162">The cmdlets that you used in this topic are Windows PowerShell cmdlets.</span><span class="sxs-lookup"><span data-stu-id="da1b9-162">The cmdlets that you used in this topic are Windows PowerShell cmdlets.</span></span> <span data-ttu-id="da1b9-163">For more information about these cmdlets, see the following topics:</span><span class="sxs-lookup"><span data-stu-id="da1b9-163">For more information about these cmdlets, see the following topics:</span></span>
  
- [<span data-ttu-id="da1b9-164">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="da1b9-164">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [<span data-ttu-id="da1b9-165">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="da1b9-165">New-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [<span data-ttu-id="da1b9-166">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="da1b9-166">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [<span data-ttu-id="da1b9-167">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="da1b9-167">Remove-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [<span data-ttu-id="da1b9-168">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="da1b9-168">Set-ExecutionPolicy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

