---
title: "利用適用於委派存取權限 (DAP) 合作夥伴的遠端 Windows PowerShell 連線至 Exchange Online 租用戶"
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: 
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: "摘要：使用遠端 Windows PowerShell 搭配 DelegatedOrg 參數連接 Exchange Online。"
ms.openlocfilehash: 857c97e5d3374f293b98298419932af4ce2dfa19
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2018
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="26127-103">利用適用於委派存取權限 (DAP) 合作夥伴的遠端 Windows PowerShell 連線至 Exchange Online 租用戶</span><span class="sxs-lookup"><span data-stu-id="26127-103">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="26127-104">**摘要：**使用遠端 Windows PowerShell 搭配 _DelegatedOrg_ 參數連線至 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="26127-104">**Summary:** Use remote Windows PowerShell to connect to Exchange Online by using the _DelegatedOrg_ parameter.</span></span>
  
<span data-ttu-id="26127-p101">遠端 Windows PowerShell 可讓您從命令列管理 Exchange Online 設定。您可以在本機電腦上使用 Windows PowerShell 建立連往 Exchange Online 的遠端工作階段。這是個包含三個步驟的程序：輸入您的 Exchange Online 認證、提供必要的連線設定，然後將 Exchange Online Cmdlet 匯入本機 Windows PowerShell 工作階段中，以供使用。</span><span class="sxs-lookup"><span data-stu-id="26127-p101">Remote Windows PowerShell lets you manage your Exchange Online settings from the command line. You use Windows PowerShell on your local computer to create a remote session to Exchange Online. It's a three-step process where you enter your Exchange Online credentials, provide the required connection settings, and then import the Exchange Online cmdlets into your local Windows PowerShell session so that you can use them.</span></span>
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="26127-108">開始之前有哪些須知？</span><span class="sxs-lookup"><span data-stu-id="26127-108">What do you need to know before you begin?</span></span>

- <span data-ttu-id="26127-109">預估完成時間：5 分鐘</span><span class="sxs-lookup"><span data-stu-id="26127-109">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="26127-110">您可以使用下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="26127-110">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="26127-111">Windows 10</span><span class="sxs-lookup"><span data-stu-id="26127-111">Windows 10</span></span>
    
  - <span data-ttu-id="26127-112">Windows 8.1 或 Windows 8</span><span class="sxs-lookup"><span data-stu-id="26127-112">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="26127-113">Windows Server 2012 R2 或 Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="26127-113">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="26127-114">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="26127-114">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="26127-115">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="26127-115">Windows Server 2008 R2 SP1\*</span></span>
    
    * <span data-ttu-id="26127-p102">您必須安裝.NET Framework 4.5.1 或.NET Framework 4.5，然後安裝任一 Windows Management Framework 4.0 或 Windows Management Framework 3.0。如需詳細資訊，請參閱下列資源︰</span><span class="sxs-lookup"><span data-stu-id="26127-p102">You need to install the .NET Framework 4.5.1 or the .NET Framework 4.5 and then either the Windows Management Framework 4.0 or the Windows Management Framework 3.0 . For more information, see the following resources:</span></span>
    
  - [<span data-ttu-id="26127-118">安裝 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="26127-118">Installing the .NET Framework</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=257868)
    
  - <span data-ttu-id="26127-119">[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) 或[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)</span><span class="sxs-lookup"><span data-stu-id="26127-119">[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)</span></span>
    
- <span data-ttu-id="26127-120">如需適用於本主題之程序的鍵盤快速鍵相關資訊，請參閱 [Exchange 系統管理中心的鍵盤快速鍵](https://go.microsoft.com/fwlink/p/?LinkId=534017)。</span><span class="sxs-lookup"><span data-stu-id="26127-120">For information about keyboard shortcuts that might apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](https://go.microsoft.com/fwlink/p/?LinkId=534017).</span></span>
    
## 

> [!IMPORTANT]
> <span data-ttu-id="26127-p103">此程序僅適用於委派存取權限 (DAP) 合作夥伴。如果您不是 DAP 合作夥伴，請勿使用此程序。</span><span class="sxs-lookup"><span data-stu-id="26127-p103">This procedure is only for Delegated Access Permission (DAP) partners. If you are not a DAP partner, do not use this procedure.</span></span> 
  
<span data-ttu-id="26127-p104">DAP 合作夥伴是新聞訂閱方式和雲端解決方案提供者 (CSP) 合作夥伴。他們通常是其他公司的網路或電信服務提供者。他們會在提供給客戶的服務方案中搭售 訂閱。他們擁有的合作夥伴租用會自動獲得其 Office 365客戶租用的管理代表 (AOBO) 權限，因此能夠管理所有的客戶租用並提出報告。</span><span class="sxs-lookup"><span data-stu-id="26127-p104">DAP partners are Syndication and Cloud Solution Providers (CSP) partners. They are frequently network or telecom providers to other companies. They bundle subscriptions into their service offerings to their customers. They own a partner tenancy that is automatically granted Administer On Behalf Of (AOBO) permissions to their Office 365customer tenancies so they can administer and report on all of their customer tenancies.</span></span>
  
## <a name="connect-to-exchange-online"></a><span data-ttu-id="26127-127">連線至 Exchange Online</span><span class="sxs-lookup"><span data-stu-id="26127-127">Connect to Exchange Online</span></span>

1. <span data-ttu-id="26127-128">在您的本機電腦上開啟 Windows PowerShell，並執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="26127-128">On your local computer, open Windows PowerShell and run the following command.</span></span>
    
  ```
  $UserCredential = Get-Credential
  ```

    <span data-ttu-id="26127-129">在 **[Windows PowerShell 認證要求]** 對話方塊中，輸入您的 DAP 系統管理員使用者名稱和密碼，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="26127-129">In the **Windows PowerShell Credential Request** dialog box, enter your DAP administrator user name and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="26127-130">執行下列命令，並將 _<customer tenant domain name>_ 取代為要連線的租用戶網域名稱。</span><span class="sxs-lookup"><span data-stu-id="26127-130">Run the following command, replacing  _<customer tenant domain name>_ with the name of the tenant domain that you want to connect to.</span></span>
    
  ```
  $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name>-Credential $UserCredential -Authentication Basic -AllowRedirection
  ```

    <span data-ttu-id="26127-p105">此命令中的重要步驟是指定可存取報告資訊的客戶。您可以透過  _ConnectionURI_ 參數來達成目標，藉由提供初始網域名稱的 FQDN 來做為 _DelegatedOrg_ 參數的值。如此能告知遠端 Windows PowerShell for Exchange Online PowerShell 遠端 Windows PowerShell 要連接的端點。每次執行報告時，遠端 Windows PowerShell 必須連接特定客戶環境中的 Office 365 報告。指定此客戶後，以下所有命令都會在客戶的環境中執行。這可讓合作夥伴存取該客戶所有可用的報告。</span><span class="sxs-lookup"><span data-stu-id="26127-p105">The key step in this command is specifying which customer to access for the reporting information. You do this in the  _ConnectionURI_ parameter, where you provide the FQDN of the initial domain name as the value to the _DelegatedOrg_ parameter. This tells remote Windows PowerShell for Exchange Online PowerShell remote Windows PowerShell the endpoint to connect to. remote Windows PowerShell must connect to Office 365 reporting in the context of a specific customer each time a report is run. After this customer is specified, all of the following commands are run in the context of that customer. This lets the partner to access all the available reports for this customer.</span></span>
    
3. <span data-ttu-id="26127-137">執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="26127-137">Run the following command.</span></span>
    
  ```
  Import-PSSession $Session
  ```

> [!NOTE]
> <span data-ttu-id="26127-p106">每個帳戶有同時執行三個工作階段的限制。完成時，請務必中斷遠端 Windows PowerShell 工作階段連線。如果未先中斷工作階段連線即關閉 Windows PowerShell 視窗，您可能會用完您可以使用的所有遠端 Windows PowerShell 工作階段，而需要等待這些工作階段到期。若要中斷遠端 Windows PowerShell 工作階段連線，請執行下列命令。 >  `Remove-PSSession $Session`</span><span class="sxs-lookup"><span data-stu-id="26127-p106">There is a limit of three simultaneous sessions that can run under one account. Be sure to disconnect the remote Windows PowerShell session when you're finished. If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote Windows PowerShell sessions available to you, and you'll need to wait for the sessions to expire. To disconnect the remote Windows PowerShell session, run the following command. >  `Remove-PSSession $Session`</span></span>
  
## <a name="how-do-you-know-this-worked"></a><span data-ttu-id="26127-142">如何知道這是否正常運作？</span><span class="sxs-lookup"><span data-stu-id="26127-142">How do you know this worked?</span></span>

<span data-ttu-id="26127-p107">執行步驟 3 後，Exchange Online Cmdlet 會匯入您的本機 Windows PowerShell 工作階段中，且會有進度列追蹤此作業。如果您未收到任何錯誤，便已順利連線。若要做快速測試，您可以執行一個 Exchange Online Cmdlet (例如 **Get-Mailbox** )，然後檢視結果。</span><span class="sxs-lookup"><span data-stu-id="26127-p107">After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar. If you don't receive any errors, you connected successfully. A quick test is to run an Exchange Online cmdlet—for example, **Get-Mailbox** —and see the results.</span></span>
  
<span data-ttu-id="26127-146">如果出現錯誤，請檢查下列需求：</span><span class="sxs-lookup"><span data-stu-id="26127-146">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="26127-p108">密碼錯誤是常見的問題。再次執行這三個步驟，並特別留意您在步驟 1 中輸入的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="26127-p108">A common problem is an incorrect password. Run the three steps again and pay close attention to the user name and password you enter in Step 1.</span></span>
    
- <span data-ttu-id="26127-149">為防止拒絕服務 (DoS) 攻擊，您最多只能對您的 Exchange Online 組織建立三個遠端 Windows PowerShell 連線。</span><span class="sxs-lookup"><span data-stu-id="26127-149">To help prevent denial-of-service (DoS) attacks, you're limited to three open remote Windows PowerShell connections to your Exchange Online organization.</span></span>
    
- <span data-ttu-id="26127-p109">您必須設定 Windows PowerShell 才能執行指令碼。您只需在電腦上設定此設定一次，而不用在每次連線時進行設定。若要讓 Windows PowerShell 執行經過簽署的指令碼，請在提高權限的 Windows PowerShell 視窗 (藉由選取 **[以管理員身分執行]** 開啟的 Windows PowerShell 視窗) 中執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="26127-p109">Windows PowerShell needs to be configured to run scripts. You need to configure this setting only once on your computer, not every time you connect. To enable Windows PowerShell to run signed scripts, run the following command in an elevated Windows PowerShell window (a Windows PowerShell window you opened by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

- <span data-ttu-id="26127-p110">用來連線至 Exchange Online 的帳戶必須能夠使用遠端 Windows PowerShell。如需詳細資訊，請參閱[管理 Exchange Online 中的遠端 PowerShell 存取權限](https://go.microsoft.com/fwlink/p/?LinkId=534018)。</span><span class="sxs-lookup"><span data-stu-id="26127-p110">The account you use to connect to Exchange Online must be enabled for remote Windows PowerShell. For more information, see [Manage Remote PowerShell Access in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span></span>
    
- <span data-ttu-id="26127-p111">本機電腦與 Exchange Online 之間必須開啟 TCP 連接埠 80 流量。該連接埠可能已開啟，但必須考量您的組織是否有限制性網際網路存取原則。</span><span class="sxs-lookup"><span data-stu-id="26127-p111">TCP port 80 traffic needs to be open between your local computer and Exchange Online. It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.</span></span>
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a><span data-ttu-id="26127-157">利用 Invoke-Command 直接呼叫 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="26127-157">Call the cmdlet directly with Invoke-Command</span></span>

<span data-ttu-id="26127-p112">匯入遠端 Windows PowerShell 工作階段可能會是冗長的程序，因為它會帶入所有 Exchange Online Cmdlet。在批次處理中這可能會造成問題 (例如，當您執行報告或針對不同租用戶進行大量變更時)。除了使用 **Import-PSSession** 之外，您還可以利用 **Invoke-Command** 直接呼叫要使用的 Cmdlet。例如，若要呼叫 **get-mailbox** Cmdlet，請以下列語法取代 `Import-PSSession $Session`。</span><span class="sxs-lookup"><span data-stu-id="26127-p112">Importing a remote Windows PowerShell session can be a lengthy process because it brings in all Exchange Online cmdlets. This can be an issue in batch processing—for example, when you are running reports or making bulk changes for different tenants. As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**. For example, to call the **get-mailbox** cmdlet, substitute this syntax for `Import-PSSession $Session`.</span></span>
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a><span data-ttu-id="26127-162">其他報告 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="26127-162">More reporting cmdlets</span></span>

<span data-ttu-id="26127-p113">本主題中所使用的 Cmdlet 是 Windows PowerShell Cmdlet。如需這些 Cmdlet 的詳細資訊，請參閱下列主題。</span><span class="sxs-lookup"><span data-stu-id="26127-p113">The cmdlets that you used in this topic are Windows PowerShell cmdlets. For more information about these cmdlets, see the following topics:</span></span>
  
- [<span data-ttu-id="26127-165">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="26127-165">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [<span data-ttu-id="26127-166">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="26127-166">New-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [<span data-ttu-id="26127-167">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="26127-167">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [<span data-ttu-id="26127-168">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="26127-168">Remove-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [<span data-ttu-id="26127-169">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="26127-169">Set-ExecutionPolicy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

