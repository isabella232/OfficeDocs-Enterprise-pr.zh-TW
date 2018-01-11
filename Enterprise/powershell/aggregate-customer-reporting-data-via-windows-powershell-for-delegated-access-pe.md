---
title: "透過適用於委派存取權限 (DAP) 合作夥伴的 Windows PowerShell 彙總客戶報告資料"
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
ms.assetid: 0f946b46-200a-4bdd-9b1b-019a554ddcc6
description: "摘要：使用 Windows PowerShell for Office 365 來擷取有關所有客戶租用的報告，以及將資料彙集到單一位置。"
ms.openlocfilehash: 825f0519b97522f664c34462c441d190cac4bb8e
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2018
---
# <a name="aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-permission-dap-partners"></a><span data-ttu-id="9d080-103">透過適用於委派存取權限 (DAP) 合作夥伴的 Windows PowerShell 彙總客戶報告資料</span><span class="sxs-lookup"><span data-stu-id="9d080-103">Aggregate customer reporting data via Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>

 <span data-ttu-id="9d080-104">**摘要：**使用 Windows PowerShell for Office 365 來擷取有關所有客戶租用的報告，以及將資料彙集到單一位置。</span><span class="sxs-lookup"><span data-stu-id="9d080-104">**Summary:** Use Windows PowerShell for Office 365 to retrieve reports on all customer tenancies and aggregate the data into a single location.</span></span>
  
<span data-ttu-id="9d080-p101">依預設，Windows PowerShell for Office 365 沒有從多個客戶租用彙總報告資料的內建功能。不過，您可以使用這個範例 Windows PowerShell for Office 365 指令碼，逐一查看所有客戶租用以針對每位客戶擷取單一報告，再將報告資料彙集到單一位置。最後您將擁有一份涵蓋所有客戶租用戶的報告。</span><span class="sxs-lookup"><span data-stu-id="9d080-p101">By default, Windows PowerShell for Office 365 does not have a built-in aggregation of reporting data from multiple customer tenancies. However, you can use this sample Windows PowerShell for Office 365 script to iterate through all your customer tenancies to retrieve a single report for each of your customers and then aggregate the reporting data into a single location. The result is that you'll have a single report for all your customer tenants.</span></span> 
  
<span data-ttu-id="9d080-p102">委派的存取權限 (DAP) 合作夥伴就是新聞訂閱方式和雲端解決方案提供者 (CSP) 合作夥伴。他們通常是其他公司的網路或電信服務提供者。他們會在提供給客戶的服務方案中搭售 Office 365 訂閱。 當他們銷售 Office 365 訂閱時，會自動將管理代理者 (AOBO) 權限授與「客戶租用」，讓他們能夠管理和報告客戶租用。</span><span class="sxs-lookup"><span data-stu-id="9d080-p102">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners. They are frequently network or telecom providers to other companies. They bundle Office 365 subscriptions into their service offerings to their customers. When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to thecustomer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="before-you-begin"></a><span data-ttu-id="9d080-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="9d080-112">Before you begin</span></span>

<span data-ttu-id="9d080-113">若要使用此指令碼，請將以下變數替代為您的值：</span><span class="sxs-lookup"><span data-stu-id="9d080-113">To use this script, substitute your particular values in for these variables:</span></span>
  
- <span data-ttu-id="9d080-p103">**$UserName** - 這是合作夥伴系統管理員使用者名稱。這些認證將用來連接所有客戶租用。</span><span class="sxs-lookup"><span data-stu-id="9d080-p103">**$UserName** - This is your partner administrator user name. These credentials will be used to connect to all your customer tenancies.</span></span>
    
- <span data-ttu-id="9d080-116">**$OutputFile** - 這是用來彙總報告資料的逗點分隔值檔案。</span><span class="sxs-lookup"><span data-stu-id="9d080-116">**$OutputFile** - This is the comma-separated value file that reporting data will be aggregated to.</span></span>
    
- <span data-ttu-id="9d080-117">**$ErrorFile** - 這是錯誤的文字記錄檔。</span><span class="sxs-lookup"><span data-stu-id="9d080-117">**$ErrorFile** - This is the text log file for errors.</span></span>
    
- <span data-ttu-id="9d080-p104">**$ScriptBlock** - 此範例指令碼使用 **Get-MailboxActivityReport** 和參數 (如開始和結束日期) 來協助您開始使用。如果您需要其他報告，請將 **Get-MailboxActivityReport** 替代為所需的報告名稱和參數。</span><span class="sxs-lookup"><span data-stu-id="9d080-p104">**$ScriptBlock** - This sample script uses **Get-MailboxActivityReport** and parameters (such as start and end dates) so you have a way to get started. If you want other reports, substitute the report name that you want and necessary parameters for **Get-MailboxActivityReport**.</span></span>
    
- <span data-ttu-id="9d080-120">使用[利用適用於委派存取權限 (DAP) 合作夥伴的遠端 Windows PowerShell 連線至 Exchange Online 租用戶](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)中的步驟開啟連往 Exchange Online 的遠端 Windows PowerShell 工作階段</span><span class="sxs-lookup"><span data-stu-id="9d080-120">Open a remote Windows PowerShell session to Exchange Online by using the steps in [Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span></span>
    
## <a name="use-windows-powershell-to-aggregate-customer-tenant-reports-to-a-single-location"></a><span data-ttu-id="9d080-121">使用 Windows PowerShell 將客戶租用戶報告彙集到單一位置</span><span class="sxs-lookup"><span data-stu-id="9d080-121">Use Windows PowerShell to aggregate customer tenant reports to a single location</span></span>

1. <span data-ttu-id="9d080-122">複製此指令碼，並將其貼入 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="9d080-122">Copy and paste this script into Notepad.</span></span>
    
  ```
  # Import the MSOnline module to allow connectivity to Office 365.

Import-Module MSOnline

# This is the partner admin user name to be used to run the report.

$UserName = "admin@contoso.onmicrosoft.com"

# These are the locations for the report output and error log.

$OutputFile = ".\\ReportOutput.csv"

$ErrorFile = ".\\Errors.txt"

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

2. <span data-ttu-id="9d080-p105">將指令碼以 GetMailboxActivityReport.ps1 儲存至容易找到的位置。例如，檔案會儲存在 C:\\O365 Scripts。</span><span class="sxs-lookup"><span data-stu-id="9d080-p105">Save the script as GetMailboxActivityReport.ps1 in a location that's easy for you to find. For the example, the file is saved in C:\\O365 Scripts.</span></span> 
    
3. <span data-ttu-id="9d080-125">遵循以下語法在遠端 Windows PowerShell 中執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="9d080-125">Run the script in remote Windows PowerShell by following this syntax.</span></span>
    
  ```
  &amp; "C:\\O365 Scripts\\GetMailboxActivityReport.ps1"
  ```

<span data-ttu-id="9d080-126">此範例指令碼會將彙總報告放置在 ReportOutput.csv 檔案中。</span><span class="sxs-lookup"><span data-stu-id="9d080-126">This sample script places the aggregated report in the ReportOutput.csv file.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="9d080-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d080-127">See also</span></span>

#### 

[<span data-ttu-id="9d080-128">合作夥伴說明</span><span class="sxs-lookup"><span data-stu-id="9d080-128">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)
  
[<span data-ttu-id="9d080-129">Office 365 報告 Web 服務</span><span class="sxs-lookup"><span data-stu-id="9d080-129">Office 365 Reporting web service</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[<span data-ttu-id="9d080-130">Exchange Online 中的報告 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9d080-130">Reporting cmdlets in Exchange Online</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=526430)

