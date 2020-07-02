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
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a>利用適用於委派存取權限 (DAP) 合作夥伴的遠端 Windows PowerShell 連線至 Exchange Online 租用戶

> [!IMPORTANT]
> The procedures in this topic are only for Delegated Access Permission (DAP) partners. If you aren't a DAP partner, don't use the procedures in this topic. 
  
DAP 合作夥伴是新聞訂閱方式和雲端解決方案提供者 (CSP) 合作夥伴。 他們通常是其他公司的網路或電信服務提供者。 他們會在提供給客戶的服務方案中搭售 訂閱。 他們擁有一個合作夥伴租使用者，它會自動授與其 Microsoft 365 客戶租用的「管理」（AOBO）許可權，讓他們能管理及報告其所有客戶租用。

「合作合作夥伴」可以使用 Exchange Online PowerShell 管理客戶 Exchange Online 設定，並從命令列取得 Microsoft 365 報告。 您可在本機電腦上使用 Windows PowerShell 建立對 Exchange Online 的遠端 PowerShell 工作階段。 這是一個簡單的三步驟程式，您可以在其中輸入您的認證、提供必要的連線設定，然後將 Exchange Online Cmdlet 匯入您的本機 Windows PowerShell 會話，讓您可以使用這些程式。

> [!NOTE]
> DAP partners can't use the procedures in [Connect to Exchange Online PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell) to connect to their customer tenant organizations in Exchange Online PowerShell. MFA and the Exchange Online Remote PowerShell Module don't work with delegated authentication.
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>開始之前有哪些須知？

- 預估完成時間：5 分鐘

- 您可以使用下列 Windows 版本：
    
  - Windows 10

  - Windows 8.1

  - Windows Server 2016

  - Windows Server 2012 或 Windows Server 2012 R2

  - Windows 7 Service Pack 1 (SP1)<sup>*</sup>

  - Windows Server 2008 R2 SP1<sup>*</sup>

    <sup>*</sup> For older versions of Windows, you need to install the Microsoft.NET Framework 4.5 or later and then an updated version of the Windows Management Framework: 3.0, 4.0, or 5.1 (only one). For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868), [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757), [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344), and [Windows Management Framework 5.1](https://aka.ms/wmf5download).

- Windows PowerShell needs to be configured to run scripts, and by default, it isn't. You'll get the following error when you try to connect:

  `Files cannot be loaded because running scripts is disabled on this system. Provide a valid certificate with which to sign the files.`

  若要要求您從網際網路下載的所有 Windows PowerShell 指令碼都是由信任的發行者簽署，請在提高權限的 Windows PowerShell 視窗 (透過選取 [以系統管理員身分執行]**** 而開啟的 Windows PowerShell 視窗) 中執行下列命令：

    ```
    Set-ExecutionPolicy RemoteSigned
    ```

  您只需在電腦上設定此設定一次，而不用在每次連線時進行設定。

- 如需適用於本主題之程序的鍵盤快速鍵相關資訊，請參閱 [Exchange 系統管理中心的鍵盤快速鍵](https://go.microsoft.com/fwlink/p/?LinkId=534017)。

## <a name="connect-to-exchange-online-for-customer-organizations"></a>連線到客戶組織的 Exchange Online

1. 在您的本機電腦上開啟 Windows PowerShell，並執行下列命令。
    
    ```
    $UserCredential = Get-Credential
    ```

    在 [Windows PowerShell 認證要求]**** 對話方塊中，輸入您的 DAP 系統管理員使用者名稱和密碼，然後按一下 [確定]****。
    
2. _\<customer tenant domain name\>_ 以您想要連線的租使用者功能變數名稱取代，並執行下列命令：
    
    ```
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name> -Credential $UserCredential -Authentication Basic -AllowRedirection
    ```

    此命令中的重要步驟是指定可存取報告資訊的客戶。 您可以在_ConnectionURI_參數中，以的值提供初始功能變數名稱的 FQDN `?DelegatedOrg=` 。 此值表示要連接的正確 Exchange Online PowerShell 端點。 在每次執行報告時，遠端 PowerShell 都必須在特定客戶的內容中連接至 Microsoft 365 報告。 在您連線至 Exchange Online PowerShell 之後，所有後續命令都會在客戶的上下文中執行，讓您可以存取客戶的所有可用報告。
    
3. 執行下列命令。
    
    ```
    Import-PSSession $Session
    ```

> [!NOTE]
> There's a limit of three simultaneous sessions that can run under one account. Be sure to disconnect the remote PowerShell session when you're finished. If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote PowerShell sessions available to you, and you'll need to wait for the sessions to expire. To disconnect the remote PowerShell session, run the following command:

```
Remove-PSSession $Session
```
  
## <a name="how-do-you-know-this-worked"></a>如何知道這是否正常運作？

After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar. If you don't receive any errors, you connected successfully. A quick test is to run an Exchange Online cmdlet (for example, **Get-Mailbox**) and see the results.
  
如果出現錯誤，請檢查下列需求：
  
- A common problem is an incorrect password. Run the three steps again and pay close attention to the user name and password you enter in Step 1.
    
- The account you use to connect to Exchange Online must be enabled for remote PowerShell. For more information, see [Enable or disable access to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534018).
    
- TCP port 80 traffic needs to be open between your local computer and Exchange Online. It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a>利用 Invoke-Command 直接呼叫 Cmdlet

Importing a remote PowerShell session (Step 3) can be a lengthy process because it brings in _all_ Exchange Online cmdlets. This can be an issue in batch processing (for example, when you're running reports or making bulk changes for different tenants). As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**. For example, to call the **Get-Milbox** cmdlet, substitute this syntax for the `Import-PSSession $Session` command in Step 3:
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a>其他報告 Cmdlet

The cmdlets that you used in this topic are Windows PowerShell cmdlets. For more information about these cmdlets, see the following topics:
  
- [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [Import-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [Remove-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [Set-ExecutionPolicy](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

