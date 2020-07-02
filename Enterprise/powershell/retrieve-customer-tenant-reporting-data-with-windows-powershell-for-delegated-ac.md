---
title: 利用適用於委派存取權限 (DAP) 合作夥伴的 Windows PowerShell 擷取客戶租用戶報告資料
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
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
ms.assetid: 893e5275-30b3-433f-8ecd-644f78f513e2
description: 摘要：使用遠端 Windows PowerShell for Microsoft Exchange Online 從個別客戶租用戶擷取報告。
ms.openlocfilehash: d4b8d931b6b8ea8c7b8467dd70326e1b0fbfc3d5
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998622"
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>利用適用於委派存取權限 (DAP) 合作夥伴的 Windows PowerShell 擷取客戶租用戶報告資料

使用 Microsoft Exchange Online 的遠端 Windows PowerShell，從個別客戶承租人取得報告。
  
Syndication and Cloud Solution Provider (CSP) partners can access the data that makes up customer tenant reports directly via remoteWindows PowerShell for Exchange Online PowerShell. This lets partners collect and save the reporting data and then perform other operations on it. After you open a remote connection, retrieving reporting data about a customer tenancy is identical to running any cmdlet against a customer tenancy.
  
In this article, you use remoteWindows PowerShell for Exchange Online to connect to a single customer tenancy and retrieve a report. By default, Windows PowerShell does not support aggregating reporting data from multiple customer tenancies. The reports you retrieve with this procedure are only for the  _DelegatedOrg_ that you connect to.
  
 
## <a name="before-you-begin"></a>開始之前

- You need to connect to your Exchange Online tenant by using remote Windows PowerShell. For instructions, see [Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)
    
## <a name="run-the-get-stalemailboxreport-sample"></a>執行 Get-StaleMailboxReport 範例

在開啟連接 Exchange Online 的遠端工作階段後，執行此命令以擷取日期範圍介於 2015/03/25 到 2015/03/31/ 之間的 **Get-StaleMailboxReport** 。
  
```
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

There are many other reporting cmdlets available for Exchange Online, Lync Online, and SharePoint Online as well as others for message tracing that you can use. To find out more about the available reporting cmdlets and the Office 365 Reporting web service, see the topics in the following section.
  
## <a name="see-also"></a>另請參閱

#### 

[Office 365 報告 Web 服務](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[Exchange Online 中的報告 Cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=526430)
  
[合作夥伴說明](https://go.microsoft.com/fwlink/p/?LinkID=533477)

