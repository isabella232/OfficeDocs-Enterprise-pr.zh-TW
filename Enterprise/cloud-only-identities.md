---
title: Office 365 僅限雲端身分識別
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: 說明如何建立使用者和群組，您的 Office 365 訂閱使用僅限雲端身分識別時。
ms.openlocfilehash: 0c066ca22f372c10b04c60f9bd44cf24300b6492
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844664"
---
# <a name="office-365-cloud-only-identities"></a>Office 365 僅限雲端身分識別

*本文適用於 Office 365 企業版和 Microsoft 365 企業版。*

僅限雲端身分識別，所有您的使用者、 群組和連絡人會儲存在您的 Office 365 訂閱的 Azure Active Directory (Azure AD) 租用戶。 以下是僅限雲端身分識別的基本元件。
 
![僅限雲端身分識別的基本元件](./media/about-office-365-identity/cloud-only-identity.png)

使用者和其組織中的使用者帳戶可以數種方式進行分類。 例如，有些是員工，而且已永久的狀態。 有些是廠商、 承包商或協力廠商的暫時狀態。 有些是不有任何使用者帳戶，但必須仍可存取權授與特定的服務和資源，以支援互動與共同作業的外部使用者。 例如：

- 租用戶帳戶代表您為雲端服務授權之組織內的使用者

- 企業對企業 (B2B) 帳戶代表您邀請參與共同作業採取庫存類型的使用者至您的組織中您組織外的使用者。 什麼是群組？ 例如，您可以至您的組織群組的使用者使用高階的函數或用途。

此外，某些雲端服務可以與組織外的使用者共用，而不需使用任何使用者帳戶。您也必須識別使用者的這些群組。

您可以使用群組為了簡化管理雲端環境的幾個 Azure AD 中。 例如，Azure AD 群組，您可以進行下列作業：

- 使用以群組為基礎來指派授權運作的 Office 365 到您的使用者帳戶會自動為他們新增授權。
- 根據使用者帳戶屬性 (例如部門) 以動態方式將使用者帳戶新增至特定群組。
- 為軟體即服務 (SaaS) 應用程式自動佈建使用者，並透過多重要素驗證和其他條件式存取規則來保護對這些應用程式的存取權。
- 佈建權限和 SharePoint Online 小組網站的存取層級。

您可以建立新的***使用者***使用：

- [Microsoft 365 系統管理中心](https://docs.microsoft.com/office365/admin/add-users/add-users)
- [Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)

您可以建立新的***群組***與：

- [Microsoft 365 系統管理中心](https://docs.microsoft.com/office365/admin/create-groups/create-groups)
- [Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-groups-with-powershell)


## <a name="next-step-for-cloud-only-identities"></a>僅限雲端身分識別的下一個步驟

[將授權指派給使用者帳戶](assign-licenses-to-user-accounts.md)
