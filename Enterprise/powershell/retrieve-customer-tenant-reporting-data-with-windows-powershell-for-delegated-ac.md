---
title: 利用適用於委派存取權限 (DAP) 合作夥伴的 Windows PowerShell 擷取客戶租用戶報告資料
ms.author: chrfox
author: chrfox
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
ms.openlocfilehash: e3e6b0ac86e2ee6479378d2eecc0c8b3cfbb6096
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004546"
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>利用適用於委派存取權限 (DAP) 合作夥伴的 Windows PowerShell 擷取客戶租用戶報告資料

 **摘要：** 使用遠端 Windows PowerShell for Microsoft Exchange Online 從個別客戶租用戶擷取報告。
  
新聞訂閱方式和雲端解決方案提供者 (CSP) 合作夥伴可透過遠端 Windows PowerShell for Exchange Online PowerShell 直接存取構成客戶租用戶報告的資料。這可讓合作夥伴收集和儲存報告資料，再據此執行其他作業。開啟遠端連線之後，擷取客戶租用相關報告資料的程序與針對客戶租用執行任何 Cmdlet 相同。
  
在本文中，您可以使用遠端 Windows PowerShell for Exchange Online 來連接單一客戶租用及擷取報告。依預設，Windows PowerShell 不支援從多個客戶租用彙集資料。使用此程序擷取的報告僅限您連接的  _DelegatedOrg_。
  
 
## <a name="before-you-begin"></a>開始之前

- 您需要使用遠端 Windows PowerShell 連接 Exchange Online 租用戶。如需詳細指示，請參閱[利用適用於委派存取權限 (DAP) 合作夥伴的遠端 Windows PowerShell 連線至 Exchange Online 租用戶](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)。
    
## <a name="run-the-get-stalemailboxreport-sample"></a>執行 Get-StaleMailboxReport 範例

在開啟連接 Exchange Online 的遠端工作階段後，執行此命令以擷取日期範圍介於 2015/03/25 到 2015/03/31/ 之間的 **Get-StaleMailboxReport** 。
  
```
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

Exchange Online、Lync Online 及 SharePoint Online 另有其他許多適用的報告 Cmdlet，以及其他可用來追蹤訊息的 Cmdlet。若要尋找其他可用之報告 Cmdlet 和 Office 365 報告 Web 服務的相關資訊，請參閱以下小節中的主題。
  
## <a name="see-also"></a>另請參閱

#### 

[Office 365 報告 Web 服務](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[Exchange Online 中的報告 Cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=526430)
  
[合作夥伴說明](https://go.microsoft.com/fwlink/p/?LinkID=533477)

