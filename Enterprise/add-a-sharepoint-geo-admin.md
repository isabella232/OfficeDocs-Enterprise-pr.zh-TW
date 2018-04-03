---
title: 新增或移除的地理位置管理員
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: 了解如何在新增或移除的地理位置管理員 OneDrive for Business 多-地理位置。
ms.openlocfilehash: 0007f1ac3c73fa7a2ada562f8da65215f80744ca
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2018
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a>新增或移除的地理位置管理員的 onedrive for Busniess 多-地理位置

您可以設定不同的系統管理員必須在您的租用戶中每個地理位置。這些系統管理員必須 SharePoint Online 和 OneDrive 設定所特有及其地理位置的存取權。

某些服務-例如之字詞儲存區-是從集中管理位置管理並複寫至衛星位置。集中管理位置地理系統管理員具有存取這些，而衛星位置的地理位置 admins 不。

全域管理員與 SharePoint Online 管理員繼續所有地理位置中有權限設定。

## <a name="configuring-geo-administrators"></a>設定地理管理員

設定地理 admins 需要 SharePoint Online PowerShell 模組。

使用[Connect-sposervice](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService)連線至系統管理中心的地理位置您要新增地理位置管理]。（例如 Connect-sposervicehttps://ContosoEUR-admin.sharepoint.com.)

若要將使用者新增為地理位置管理、 執行`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`

若要檢視現有地理 admins 的位置，請執行`Get-SPOGeoAdministrators`

若要移除使用者以地理位置的系統管理員位置、 執行`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`

## <a name="see-also"></a>另請參閱

[新增 SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[取得 SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[移除 SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)