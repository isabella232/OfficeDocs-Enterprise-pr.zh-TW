---
title: 將 Office 365 授權指派給使用者帳戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: 說明如何將 Office 365 授權指派給使用者帳戶，或是個別或根據群組成員資格。
ms.openlocfilehash: 0f258ef9240239ebdfa695e8c5b214484cfb4db1
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "34164598"
---
# <a name="assign-office-365-licenses-to-user-accounts"></a>將 Office 365 授權指派給使用者帳戶

僅限雲端身分識別模型的可以將 Office 365 授權指派給使用者帳戶為他們所建立，根據您建立的方式。

對於混合式身分識別模型中，第一次同步處理 Active Directory 網域服務 (AD DS) 的使用者帳戶時它們不會自動指派 Office 365 授權。

在任一情況中，您必須指派授權給使用者帳戶讓您的使用者可以存取 Office 365 服務，例如電子郵件和 Microsoft Teams。

您可以透過群組成員資格，個別或自動指派授權給使用者帳戶。

若要將 Office 365 授權指派給個別使用者帳戶，您可以使用：

- [在 Microsoft 365 系統管理中心](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/assign-licenses-to-users)
- [Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell)

自動授權指派]，請參閱[在 Azure AD 群組為基礎的授權](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal)。

## <a name="next-steps"></a>後續步驟

已指派授權的使用者帳戶的完整設定之後，現在已準備要：

- [部署用戶端軟體，例如 Office 365 專業增強版](https://docs.microsoft.com/DeployOffice/deployment-guide-for-office-365-proplus)
- [設定行動裝置管理](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)
- [設定服務及應用程式](configure-services-and-applications.md)