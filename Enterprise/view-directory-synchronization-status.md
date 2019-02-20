---
title: 在 Office 365 中檢視目錄同步處理狀態
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: 了解如何停用目錄同步作業。您也可以檢視其狀態。
ms.openlocfilehash: 4803cbadd17dbc1ee23d019f39144ff1ffaefd9a
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085052"
---
# <a name="view-directory-synchronization-status-in-office-365"></a>在 Office 365 中檢視目錄同步處理狀態
如果您已整合 Azure AD 您在內部部署 Active Directory 來使用 Office 365 同步處理內部部署環境，您也可以檢查您同步處理的狀態。
  
## <a name="view-directory-synchronization-status"></a>檢視目錄同步處理狀態
- 登入 Office 365 系統管理中心和在 [首頁] 頁面上選擇 [ **DirSync 狀態**。 
- 或者，您可以前往 ＜ 給**使用者** \> **作用中使用者**，在**作用中使用者**] 頁面上，選擇 [**更多** \> **目錄同步處理**。在 [**目錄同步處理**] 窗格中，選擇 [**移至 [DirSync 管理**。
    
## <a name="information-on-the-manage-directory-synchronization-page"></a>在 [管理目錄同步處理] 頁面上的資訊

下表列出您可以取得資訊] 頁面的功能。
  
以目錄同步作業問題時，發生之錯誤會列在此頁面上。如需不同可能遇到的錯誤的詳細資訊，請參閱[Office 365 中的身分識別目錄同步處理錯誤](identify-directory-synchronization-errors.md)。
  
|**項目**|**功能**|
|:-----|:-----|
|**已驗證的網域** | 您已驗證您的 Office 365 租用中的網域數目的擁有人。 |
|**未驗證的網域** | 您已新增，但未驗證的網域。 |
|**啟用目錄同步處理** |True 或 False。會指定您是否已啟用目錄同步處理。 |
|**最新的目錄同步處理** | 上次執行目錄同步處理。將會顯示一則警告訊息和連結的疑難排解工具如果上次同步處理成功三天以上。 |
|**啟用密碼同步處理** | True 或 False。會指定是否必須我們內部部署與您的 Office 365 租用戶之間的密碼雜湊同步處理。 |
|**最後一個密碼同步處理** | 最後一次密碼雜湊同步處理已執行。將會顯示一則警告訊息和連結的疑難排解工具如果上次同步處理成功三天以上。 |
|**目錄同步處理用戶端版本** | 如果發行 Azure AD 連線的新版本會包含下載連結。 |
|**IDFix 工具** | 下載[IDFix](install-and-run-idfix.md)，您可以使用來檢查本機 Active Directory 工具的連結。 |
|**目錄同步處理服務帳戶** | 會顯示您的 Office 365 目錄同步處理服務帳戶的名稱。 |