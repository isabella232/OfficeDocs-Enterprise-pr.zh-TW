---
title: "利用適用於委派存取權限 (DAP) 合作夥伴的 Windows PowerShell 擷取客戶租用戶報告資料"
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
ms.assetid: 893e5275-30b3-433f-8ecd-644f78f513e2
description: "摘要：使用遠端 Windows PowerShell for Microsoft Exchange Online 從個別客戶租用戶擷取報告。"
ms.openlocfilehash: d764f34b89ee55fd7015f01c0c48446fc73a6ac0
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2018
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="736cd-103">利用適用於委派存取權限 (DAP) 合作夥伴的 Windows PowerShell 擷取客戶租用戶報告資料</span><span class="sxs-lookup"><span data-stu-id="736cd-103">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="736cd-104">**摘要：**使用遠端 Windows PowerShell for Microsoft Exchange Online 從個別客戶租用戶擷取報告。</span><span class="sxs-lookup"><span data-stu-id="736cd-104">**Summary:** Use remoteWindows PowerShell for Microsoft Exchange Online to retrieve reports from individual customer tenants.</span></span>
  
<span data-ttu-id="736cd-p101">新聞訂閱方式和雲端解決方案提供者 (CSP) 合作夥伴可透過遠端 Windows PowerShell for Exchange Online PowerShell 直接存取構成客戶租用戶報告的資料。這可讓合作夥伴收集和儲存報告資料，再據此執行其他作業。開啟遠端連線之後，擷取客戶租用相關報告資料的程序與針對客戶租用執行任何 Cmdlet 相同。</span><span class="sxs-lookup"><span data-stu-id="736cd-p101">Syndication and Cloud Solution Provider (CSP) partners can access the data that makes up customer tenant reports directly via remoteWindows PowerShell for Exchange Online PowerShell. This lets partners collect and save the reporting data and then perform other operations on it. After you open a remote connection, retrieving reporting data about a customer tenancy is identical to running any cmdlet against a customer tenancy.</span></span>
  
<span data-ttu-id="736cd-p102">在本文中，您可以使用遠端 Windows PowerShell for Exchange Online 來連接單一客戶租用及擷取報告。依預設，Windows PowerShell 不支援從多個客戶租用彙集資料。使用此程序擷取的報告僅限您連接的  _DelegatedOrg_。</span><span class="sxs-lookup"><span data-stu-id="736cd-p102">In this article, you use remoteWindows PowerShell for Exchange Online to connect to a single customer tenancy and retrieve a report. By default, Windows PowerShell does not support aggregating reporting data from multiple customer tenancies. The reports you retrieve with this procedure are only for the  _DelegatedOrg_ that you connect to.</span></span>
  
<span data-ttu-id="736cd-111">如果您想要為所有客戶租用擷取單一報告，可以在[透過適用於委派存取權限 (DAP) 合作夥伴的 Windows PowerShell 彙總客戶報告資料](aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-pe.md)中找到適用的範例指令碼。</span><span class="sxs-lookup"><span data-stu-id="736cd-111">If you want to retrieve a single report for all your customer tenancies, a sample script to do this can be found in [Aggregate customer reporting data via Windows PowerShell for Delegated Access Permission (DAP) partners](aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-pe.md) .</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="736cd-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="736cd-112">Before you begin</span></span>

- <span data-ttu-id="736cd-p103">您需要使用遠端 Windows PowerShell 連接 Exchange Online 租用戶。如需詳細指示，請參閱[利用適用於委派存取權限 (DAP) 合作夥伴的遠端 Windows PowerShell 連線至 Exchange Online 租用戶](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)。</span><span class="sxs-lookup"><span data-stu-id="736cd-p103">You need to connect to your Exchange Online tenant by using remote Windows PowerShell. For instructions, see [Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span></span>
    
## <a name="run-the-get-stalemailboxreport-sample"></a><span data-ttu-id="736cd-115">執行 Get-StaleMailboxReport 範例</span><span class="sxs-lookup"><span data-stu-id="736cd-115">Run the Get-StaleMailboxReport sample</span></span>

<span data-ttu-id="736cd-116">在開啟連接 Exchange Online 的遠端工作階段後，執行此命令以擷取日期範圍介於 2015/03/25 到 2015/03/31/ 之間的 **Get-StaleMailboxReport** 。</span><span class="sxs-lookup"><span data-stu-id="736cd-116">After you have opened a remote session to Exchange Online, run this command to retrieve the **Get-StaleMailboxReport** for the date range 03/25/2015 through 03/31/2015.</span></span>
  
```
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

<span data-ttu-id="736cd-p104">Exchange Online、Lync Online 及 SharePoint Online 另有其他許多適用的報告 Cmdlet，以及其他可用來追蹤訊息的 Cmdlet。若要尋找其他可用之報告 Cmdlet 和 Office 365 報告 Web 服務的相關資訊，請參閱以下小節中的主題。</span><span class="sxs-lookup"><span data-stu-id="736cd-p104">There are many other reporting cmdlets available for Exchange Online, Lync Online, and SharePoint Online as well as others for message tracing that you can use. To find out more about the available reporting cmdlets and the Office 365 Reporting web service, see the topics in the following section.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="736cd-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="736cd-119">See also</span></span>

#### 

[<span data-ttu-id="736cd-120">Office 365 報告 Web 服務</span><span class="sxs-lookup"><span data-stu-id="736cd-120">Office 365 Reporting web service</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[<span data-ttu-id="736cd-121">Exchange Online 中的報告 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="736cd-121">Reporting cmdlets in Exchange Online</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=526430)
  
[<span data-ttu-id="736cd-122">合作夥伴說明</span><span class="sxs-lookup"><span data-stu-id="736cd-122">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

