---
title: 透過適用於委派存取權限 (DAP) 合作夥伴的 Windows PowerShell 彙總客戶報告資料
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 0f946b46-200a-4bdd-9b1b-019a554ddcc6
description: 摘要：使用 Windows PowerShell for Office 365 來擷取有關所有客戶租用的報告，以及將資料彙集到單一位置。
ms.openlocfilehash: eba2c3be848b878670321485718317b5552b2db3
ms.sourcegitcommit: 8ff1cd7733dba438697b68f90189d4da72bbbefd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-permission-dap-partners"></a>透過適用於委派存取權限 (DAP) 合作夥伴的 Windows PowerShell 彙總客戶報告資料

 **摘要：**使用 Windows PowerShell for Office 365 來擷取有關所有客戶租用的報告，以及將資料彙集到單一位置。
  
依預設，Windows PowerShell for Office 365 沒有從多個客戶租用彙總報告資料的內建功能。不過，您可以使用這個範例 Windows PowerShell for Office 365 指令碼，逐一查看所有客戶租用以針對每位客戶擷取單一報告，再將報告資料彙集到單一位置。最後您將擁有一份涵蓋所有客戶租用戶的報告。 
  
委派的存取權限 (DAP) 合作夥伴就是新聞訂閱方式和雲端解決方案提供者 (CSP) 合作夥伴。他們通常是其他公司的網路或電信服務提供者。他們會在提供給客戶的服務方案中搭售 Office 365 訂閱。 當他們銷售 Office 365 訂閱時，會自動將管理代理者 (AOBO) 權限授與「客戶租用」，讓他們能夠管理和報告客戶租用。
## <a name="before-you-begin"></a>開始之前

若要使用此指令碼，請將以下變數替代為您的值：
  
- **$UserName** - 這是合作夥伴系統管理員使用者名稱。這些認證將用來連接所有客戶租用。
    
- **$OutputFile** - 這是用來彙總報告資料的逗點分隔值檔案。
    
- **$ErrorFile** - 這是錯誤的文字記錄檔。
    
- **$ScriptBlock** - 此範例指令碼使用 **Get-MailboxActivityReport** 和參數 (如開始和結束日期) 來協助您開始使用。如果您需要其他報告，請將 **Get-MailboxActivityReport** 替代為所需的報告名稱和參數。
    
- 使用[利用適用於委派存取權限 (DAP) 合作夥伴的遠端 Windows PowerShell 連線至 Exchange Online 租用戶](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)中的步驟開啟連往 Exchange Online 的遠端 Windows PowerShell 工作階段
    
## <a name="use-windows-powershell-to-aggregate-customer-tenant-reports-to-a-single-location"></a>使用 Windows PowerShell 將客戶租用戶報告彙集到單一位置

1. 複製此指令碼，並將其貼入 [記事本]。
    
  ```
  # Import the MSOnline module to allow connectivity to Office 365.

Import-Module MSOnline

# This is the partner admin user name to be used to run the report.

$UserName = "admin@contoso.onmicrosoft.com"

# These are the locations for the report output and error log.

$OutputFile = ".\ReportOutput.csv"

$ErrorFile = ".\Errors.txt"

# This is the report to run and all the necessary parameters.

$ScriptBlock = {Get-MailboxActivityReport -ReportType Daily -StartDate 03/18/2015 -EndDate 03/18/2015}

$LinesToSkip = 0

# This is the prompt for the password of the partner admin user name.

$Cred = get-credential -Credential $UserName

# Establish a Windows PowerShell session with Office 365.

Connect-MsolService -Credential $Cred

# Get all the contracts for the signed-in partner.  
# Contracts define the AOBO/DAP relationship between the partner and the customers.

$Contracts = Get-MsolPartnerContract -All

Write-Host "Found $($Contracts.Count) customers for this Partner."

# For each of the contracts (customers), run the specified report and output the information.

foreach ($c in $contracts) { 

    # Get the initial domain for the customer.

    $InitialDomain = Get-MsolDomain -TenantId $c.TenantId | Where {$_.IsInitial -eq $true}

    # Construct the URL with the DelegatedOrg parameter.
    
    $DelegatedOrgURL = "https://ps.outlook.com/powershell-liveid?DelegatedOrg=" + $InitialDomain.Name
        
    Write-Host "Running report for $($InitialDomain.Name)"

    # Invoke-Command establishes a Windows PowerShell session based on the URL,
    # runs the command, and closes the Windows PowerShell session.
    
    $ReportInfo = Invoke-Command -ConnectionUri $DelegatedOrgURL -Credential $Cred -Authentication Basic -ConfigurationName Microsoft.Exchange -AllowRedirection -ScriptBlock $ScriptBlock -HideComputerName

    # If Invoke-Command returned information (that is, it's not NULL), format and output the information.
    
    If ($ReportInfo) {

        Write-Host "Writing report information for $($InitialDomain.Name) to $OutputFile"  -foregroundcolor green

        # Convert the report data to CSV format.
        # For the first time, don't skip any lines, so include the header.
        # For all other times, skip the first line (so don't rewrite the header).
        
        $OutputInfo = $ReportInfo |  ConvertTo-CSV -NoTypeInformation | Select -Skip $LinesToSkip

        Out-File $OutputFile -InputObject $OutputInfo -Append

        $LinesToSkip = 1

    } else {

        # If Invoke-Command didn't return and report data, log an error.
        
        Write-Host "No report information for $($InitialDomain.Name)." -foregroundcolor yellow
           
        Out-File $ErrorFile  -InputObject @("No report information for $($InitialDomain.Name).") -Append
    }

}

  ```

2. 將指令碼以 GetMailboxActivityReport.ps1 儲存至容易找到的位置。例如，檔案會儲存在 C:\\O365 Scripts。 
    
3. 遵循以下語法在遠端 Windows PowerShell 中執行指令碼。
    
  ```
  &amp; "C:\O365 Scripts\GetMailboxActivityReport.ps1"
  ```

此範例指令碼會將彙總報告放置在 ReportOutput.csv 檔案中。
  
## <a name="see-also"></a>另請參閱

#### 

[合作夥伴說明](https://go.microsoft.com/fwlink/p/?LinkID=533477)
  
[Office 365 報告 Web 服務](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[Exchange Online 中的報告 Cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=526430)

