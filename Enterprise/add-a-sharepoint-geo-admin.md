---
title: 新增或移除地理位置系統管理員
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
description: 了解如何在 Office 365 多地理位置中新增或移除地理位置系統管理員。
ms.openlocfilehash: 54850252d133e3e26b02cabe3ead0900287e832c
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490909"
---
# <a name="add-or-remove-a-geo-administrator-in-office-365-multi-geo"></a>在 Office 365 多地理位置中新增或移除地理位置系統管理員

您可以為租用戶中的每個地理位置設定個別的系統管理員。 這些系統管理員將能存取專為其地理位置設定的 Sharepoint 和 OneDrive 設定。

某些服務 - 例如詞彙儲存庫- 可從中心位置進行管理並會複製到衛星位置。 中央位置的地理位置系統管理員可以存取這些服務，而衛星位置的地理位置系統管理員則無法存取。

全域系統管理員和 SharePoint Online 系統管理員可以繼續存取中心位置和所有衛星位置的設定。

## <a name="configuring-geo-administrators"></a>設定地理位置系統管理員

設定地理位置系統管理員需要 SharePoint Online PowerShell 模組。

使用 [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) 連線到您想新增地理位置系統管理員之地理位置的系統管理中心。(例如，Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)

若要檢視某位置的現有地理位置系統管理員，請執行 `Get-SPOGeoAdministrator`

### <a name="adding-a-user-as-a-geo-admin"></a>將使用者新增為地理位置系統管理員

若要將使用者新增為地理位置系統管理員，請執行 `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`

若要在某位置將使用者的地理位置系統管理員身份移除，請執行 `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`

### <a name="adding-a-group-as-a-geo-admin"></a>將群組新增為地理位置系統管理員

您可以新增安全性群組或擁有郵件功能的安全性群組作為地理位置系統管理員。(不支援通訊群組與 Office 365 群組。)

若要新增群組為地理位置系統管理員，請執行 `Add-SPOGeoAdministrator -GroupAlias <alias>`

若要移除群組的地理位置系統管理員身份，請執行 `Remove-SPOGeoAdministrator -GroupAlias <alias>`

請注意，並非所有安全性群組都有群組別名。 如果您要新增的安全性群組並沒有別名，請執行 [Get-MsolGroup](https://docs.microsoft.com/zh-TW/powershell/module/msonline/get-msolgroup) 擷取群組清單、找出安全性群組 ObjectID，然後再執行：

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

若要使用 ObjectID 移除群組，請執行 `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`

## <a name="see-also"></a>另請參閱

[Add-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[Add-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[Remove-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[為安全性群組設定別名 (MailNickName)](https://docs.microsoft.com/zh-TW/powershell/module/azuread/set-azureadgroup)