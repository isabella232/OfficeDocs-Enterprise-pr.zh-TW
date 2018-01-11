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
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a>利用適用於委派存取權限 (DAP) 合作夥伴的遠端 Windows PowerShell 連線至 Exchange Online 租用戶

 **摘要：**使用遠端 Windows PowerShell 搭配 _DelegatedOrg_ 參數連線至 Exchange Online。
  
遠端 Windows PowerShell 可讓您從命令列管理 Exchange Online 設定。您可以在本機電腦上使用 Windows PowerShell 建立連往 Exchange Online 的遠端工作階段。這是個包含三個步驟的程序：輸入您的 Exchange Online 認證、提供必要的連線設定，然後將 Exchange Online Cmdlet 匯入本機 Windows PowerShell 工作階段中，以供使用。
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>開始之前有哪些須知？

- 預估完成時間：5 分鐘
    
- 您可以使用下列 Windows 版本：
    
  - Windows 10
    
  - Windows 8.1 或 Windows 8
    
  - Windows Server 2012 R2 或 Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    * 您必須安裝.NET Framework 4.5.1 或.NET Framework 4.5，然後安裝任一 Windows Management Framework 4.0 或 Windows Management Framework 3.0。如需詳細資訊，請參閱下列資源︰
    
  - [安裝 .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868)
    
  - [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) 或[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)
    
- 如需適用於本主題之程序的鍵盤快速鍵相關資訊，請參閱 [Exchange 系統管理中心的鍵盤快速鍵](https://go.microsoft.com/fwlink/p/?LinkId=534017)。
    
## 

> [!IMPORTANT]
> 此程序僅適用於委派存取權限 (DAP) 合作夥伴。如果您不是 DAP 合作夥伴，請勿使用此程序。 
  
DAP 合作夥伴是新聞訂閱方式和雲端解決方案提供者 (CSP) 合作夥伴。他們通常是其他公司的網路或電信服務提供者。他們會在提供給客戶的服務方案中搭售 訂閱。他們擁有的合作夥伴租用會自動獲得其 Office 365客戶租用的管理代表 (AOBO) 權限，因此能夠管理所有的客戶租用並提出報告。
  
## <a name="connect-to-exchange-online"></a>連線至 Exchange Online

1. 在您的本機電腦上開啟 Windows PowerShell，並執行下列命令。
    
  ```
  $UserCredential = Get-Credential
  ```

    在 **[Windows PowerShell 認證要求]** 對話方塊中，輸入您的 DAP 系統管理員使用者名稱和密碼，然後按一下 **[確定]**。
    
2. 執行下列命令，並將 _<customer tenant domain name>_ 取代為要連線的租用戶網域名稱。
    
  ```
  $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name>-Credential $UserCredential -Authentication Basic -AllowRedirection
  ```

    此命令中的重要步驟是指定可存取報告資訊的客戶。您可以透過  _ConnectionURI_ 參數來達成目標，藉由提供初始網域名稱的 FQDN 來做為 _DelegatedOrg_ 參數的值。如此能告知遠端 Windows PowerShell for Exchange Online PowerShell 遠端 Windows PowerShell 要連接的端點。每次執行報告時，遠端 Windows PowerShell 必須連接特定客戶環境中的 Office 365 報告。指定此客戶後，以下所有命令都會在客戶的環境中執行。這可讓合作夥伴存取該客戶所有可用的報告。
    
3. 執行下列命令。
    
  ```
  Import-PSSession $Session
  ```

> [!NOTE]
> 每個帳戶有同時執行三個工作階段的限制。完成時，請務必中斷遠端 Windows PowerShell 工作階段連線。如果未先中斷工作階段連線即關閉 Windows PowerShell 視窗，您可能會用完您可以使用的所有遠端 Windows PowerShell 工作階段，而需要等待這些工作階段到期。若要中斷遠端 Windows PowerShell 工作階段連線，請執行下列命令。 >  `Remove-PSSession $Session`
  
## <a name="how-do-you-know-this-worked"></a>如何知道這是否正常運作？

執行步驟 3 後，Exchange Online Cmdlet 會匯入您的本機 Windows PowerShell 工作階段中，且會有進度列追蹤此作業。如果您未收到任何錯誤，便已順利連線。若要做快速測試，您可以執行一個 Exchange Online Cmdlet (例如 **Get-Mailbox** )，然後檢視結果。
  
如果出現錯誤，請檢查下列需求：
  
- 密碼錯誤是常見的問題。再次執行這三個步驟，並特別留意您在步驟 1 中輸入的使用者名稱和密碼。
    
- 為防止拒絕服務 (DoS) 攻擊，您最多只能對您的 Exchange Online 組織建立三個遠端 Windows PowerShell 連線。
    
- 您必須設定 Windows PowerShell 才能執行指令碼。您只需在電腦上設定此設定一次，而不用在每次連線時進行設定。若要讓 Windows PowerShell 執行經過簽署的指令碼，請在提高權限的 Windows PowerShell 視窗 (藉由選取 **[以管理員身分執行]** 開啟的 Windows PowerShell 視窗) 中執行下列命令。
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

- 用來連線至 Exchange Online 的帳戶必須能夠使用遠端 Windows PowerShell。如需詳細資訊，請參閱[管理 Exchange Online 中的遠端 PowerShell 存取權限](https://go.microsoft.com/fwlink/p/?LinkId=534018)。
    
- 本機電腦與 Exchange Online 之間必須開啟 TCP 連接埠 80 流量。該連接埠可能已開啟，但必須考量您的組織是否有限制性網際網路存取原則。
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a>利用 Invoke-Command 直接呼叫 Cmdlet

匯入遠端 Windows PowerShell 工作階段可能會是冗長的程序，因為它會帶入所有 Exchange Online Cmdlet。在批次處理中這可能會造成問題 (例如，當您執行報告或針對不同租用戶進行大量變更時)。除了使用 **Import-PSSession** 之外，您還可以利用 **Invoke-Command** 直接呼叫要使用的 Cmdlet。例如，若要呼叫 **get-mailbox** Cmdlet，請以下列語法取代 `Import-PSSession $Session`。
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a>其他報告 Cmdlet

本主題中所使用的 Cmdlet 是 Windows PowerShell Cmdlet。如需這些 Cmdlet 的詳細資訊，請參閱下列主題。
  
- [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [Import-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [Remove-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [Set-ExecutionPolicy](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

