---
title: 檢視 Office 365 中的目錄同步處理狀態
ms.author: robmazz
author: robmazz
manager: laurawi
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
description: 了解如何停用目錄同步作業。 您也可以檢視其狀態。
ms.openlocfilehash: a38b723db6f5bafe246e774972ca89c65bc9c846
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33492099"
---
# <a name="view-directory-synchronization-status-in-office-365"></a>檢視 Office 365 中的目錄同步處理狀態

如果您已經與 Office 365 同步內部部署環境，與 Azure AD 整合您的內部部署 Active Directory，您也可以檢查您同步處理的狀態。
  
## <a name="view-directory-synchronization-status"></a>檢視目錄同步處理狀態

- 登入[Microsoft 365 系統管理中心](https://admin.microsoft.com)，選擇 [**目錄同步狀態**]，請在 [首頁] 頁面上。
- 或者，您可以移至 [**使用者** \> **作用中的使用者**，並在 [**作用中使用者**] 頁面上，選擇 [**更多** \> **目錄同步處理**。 在 [**目錄同步處理**] 窗格中，選擇 [**移至 [目錄同步管理**。

## <a name="information-on-the-manage-directory-synchronization-page"></a>在 [管理目錄同步處理] 頁面上的資訊

下表列出您可以取得資訊] 頁面的功能。
  
如果沒有您的目錄同步處理的問題，錯誤會列在此頁面上。 如需不同，可能會遇到的錯誤的詳細資訊，請參閱 <<c0>在 Office 365 中的身分識別目錄同步處理錯誤。
  
|**Item**|**功能**|
|:-----|:-----|
|**驗證的網域** | 您已經驗證您的 Office 365 租用戶中的網域數目的擁有人。 |
|**未驗證的網域** | 您可以新增，但卻未驗證的網域。 |
|**啟用目錄同步處理** |則為 true 或 False。 會指定是否已啟用目錄同步處理。 |
|**最新的目錄同步處理** | 目錄同步處理執行的時間。 如果會顯示一則警告，並連結至疑難排解工具上次同步處理已三天以上。 |
|**啟用密碼同步處理** | 則為 true 或 False。 會指定是否必須讓我們內部部署與您的 Office 365 租用戶之間的密碼雜湊同步處理。 |
|**最後一個密碼同步處理** | 密碼雜湊同步處理執行的時間。 如果會顯示一則警告，並連結至疑難排解工具上次同步處理已三天以上。 |
|**目錄同步處理用戶端版本** | 如果已釋放 Azure AD Connect 的新版本會包含的下載連結。 |
|**IDFix 工具** | [IDFix](install-and-run-idfix.md)，您可以使用來檢查本機 Active Directory 工具來下載連結。 |
|**目錄同步處理服務帳戶** | 會顯示您 Office 365 目錄同步處理服務帳戶的名稱。 |