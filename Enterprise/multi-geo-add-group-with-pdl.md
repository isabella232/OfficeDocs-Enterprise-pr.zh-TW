---
title: 使用特定 PDL 建立 Office 365 群組
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 了解如何使用指定的慣用資料位置在多地理位置環境中建立 Office 365 群組。
ms.openlocfilehash: fb512478d69502eafd633b552d1db2acbec43ef4
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069999"
---
# <a name="create-an-office-365-group-with-a-specific-pdl"></a>使用特定 PDL 建立 Office 365 群組

在位於多地理位置環境中的使用者建立 Office 365 群組時，群組慣用資料位置將自動設定為使用者的位置。 如果需要建立具有特定 PDL 的群組，則可以使用 Exchange Online New-UnifiedGroup Microsoft PowerShell cmdlet 來建立。 如此一來，將在指定的 PDL 中佈建與該群組關聯的群組信箱和 SharePoint 網站。

您必須是全域系統管理員或 SharePoint Online 或 Exchange Online 系統管理員才能進行此操作。

若要使用您指定的 PDL 建立 Office 365 群組，請連線至 Exchange Online PowerShell，並傳遞參數 *-MailBoxRegion* 與地理位置代碼。

例如： 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![New-UnifiedGroup PowerShell cmdlet 以及語法的螢幕擷取畫面](media/multi-geo-new-group-with-pdl-powershell.png)

請注意，SharePoint 群組網站佈建將依照需求。 在群組擁有者或成員首次嘗試存取網站時，會對該網站進行佈建。

## <a name="geo-location-codes"></a>地理位置代碼

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="see-also"></a>另請參閱

[連線到 Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)