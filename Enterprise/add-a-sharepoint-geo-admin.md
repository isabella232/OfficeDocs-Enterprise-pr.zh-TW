---
title: 新增或移除異地系統管理員
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: 了解如何在新增或移除的地理位置管理員 OneDrive for Business 多-地理位置。
ms.openlocfilehash: 4e8c8bec148d5a4e7e55ffa2b08a49cd2ea6aa0a
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849809"
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a>新增或移除的地理位置管理員的 onedrive for Busniess 多-地理位置

您可以設定不同的系統管理員必須在您的租用戶中每個地理位置。這些系統管理員必須 SharePoint Online 和 OneDrive 設定所特有及其地理位置的存取權。

某些服務-例如之字詞儲存區-是從集中管理位置管理並複寫至衛星位置。集中管理位置地理系統管理員具有存取這些，而衛星位置的地理位置 admins 不。

全域管理員與 SharePoint Online 管理員繼續執行集中管理位置和附屬的所有位置中設定的存取權。

## <a name="configuring-geo-administrators"></a>設定地理管理員

設定地理 admins 需要 SharePoint Online PowerShell 模組。

使用[Connect-sposervice](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService)連線至系統管理中心的地理位置您要新增地理位置管理]。（例如 Connect-sposervicehttps://ContosoEUR-admin.sharepoint.com.)

若要檢視現有地理 admins 的位置，請執行`Get-SPOGeoAdministrator`

### <a name="adding-a-user-as-a-geo-admin"></a>將使用者新增為地理位置管理

若要將使用者新增為地理位置管理、 執行`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`

若要移除使用者以地理位置的系統管理員位置、 執行`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`

### <a name="adding-a-group-as-a-geo-admin"></a>新增的地理位置系統管理員群組

您可以將安全群組或擁有郵件功能的安全性群組新增為地理位置管理]。（通訊群組與 Office 365 群組不支援。）

若要將群組新增地理系統管理員身分、 執行`Add-SPOGeoAdministrator -GroupAlias <alias>`

若要移除群組地理系統管理員身分執行`Remove-SPOGeoAdministrator -GroupAlias <alias>`

請注意不是所有安全性群組都有群組的別名。如果您想要新增安全性群組沒有指定別名，執行[Get MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup)來擷取群組的清單，尋找您安全性群組 ObjectID，然後執行：

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

若要移除群組使用 ObjectID、 執行`Remove-SPOGeoAdministrator -ObjectID <ObjectID>`

### <a name="accessing-the-admin-center-for-a-specific-geo-location"></a>存取特定的地理位置的系統管理中心

若要管理其地理位置的 OneDrive 設定，系統管理員必須存取 OneDrive 系統管理中心直接使用 URL 格式如下：

https://admin.onedrive.com/?geo=<*地理位置*>

例如，加拿大 OneDrive 系統中心位於： https://admin.onedrive.com/?geo=CAN。

## <a name="see-also"></a>另請參閱

[新增 SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[取得 SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[移除 SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[設定別名 (MailNickName) 的安全性群組](https://docs.microsoft.com/en-us/powershell/module/azuread/set-azureadgroup)