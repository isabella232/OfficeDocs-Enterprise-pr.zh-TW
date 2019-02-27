---
title: Office 365 用戶端應用程式支援摩登的驗證
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: Normal
ms.collection:
- Strat_O365_Enterprise
- M365-subscription-management
search.appverid:
- MET150
description: Office 365 用戶端應用程式支援經過驗證。
ms.openlocfilehash: f4eb3282140bd1b722698ec0fa4a4f3f51366c2e
ms.sourcegitcommit: fd137a68c516379a9f09e06987e8d45d92de7ed6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2019
ms.locfileid: "30303607"
---
# <a name="office-365-client-app-support---modern-authentication"></a>Office 365 用戶端應用程式支援摩登的驗證

Microsoft 的現代驗證功能可讓跨不同平台的 [Active Directory 驗證文件庫 ADAL 型登入 Office 用戶端應用程式。這可讓登入功能，例如多重要素驗證 (MFA)、 智慧卡及憑證型驗證。

了解更多關於的[多重要素驗證](https://docs.microsoft.com/azure/active-directory/authentication/multi-factor-authentication)和[憑證型驗證](https://docs.microsoft.com/azure/active-directory/active-directory-certificate-based-authentication-get-started)。

## <a name="supported-platforms"></a>支援的平台

 - Windows 10 桌面
 - Windows 10 現代應用程式
 - Web 瀏覽器
 - Android
 - iOS
 - macOS

如需在 Office 365 平台支援的詳細資訊，請參閱[Office 365 系統需求](https://products.office.com/office-system-requirements)。

## <a name="supported-clients"></a>支援的用戶端

下列用戶端的最新版本支援現代驗證：

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Azure 圖示](media/o365-azure-64x64.png) <br> [Azure AD<br>入口網站](https://azure.microsoft.com/features/azure-portal/) | ![公司入口網站圖示](media/o365-microsoft-64x64.png) <br> [公司<br>入口網站](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) | ![探索圖示](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Dynamics 365 圖示](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) | ![Excel 圖示](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) |
| ![流程圖示](media/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![表單圖示](media/o365-forms-64x64.png) <br> [表單](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Kaizala 圖示](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) | ![Office 365 Admin 圖示](media/o365-o365admin-64x64.png) <br> [Office 365<br>系統](https://products.office.com/business/manage-office-365-admin-app) | ![透鏡圖示](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | 
| ![OneDrive for Business 圖示](media/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) |  ![OneNote 圖示](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Outlook 圖示](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![規劃圖示](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![PowerBI 圖示](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com)
| ![PowerPoint 圖示](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![專案圖示](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![SharePoint 圖示](media/o365-sharepoint-64x64.png) <br> [Sharepoint](https://products.office.com/sharepoint) | ![Skype 商務圖示](media/o365-skypeforbusiness-64x64.png) <br> [針對 Skype<br>商務](https://www.skype.com/business/) | ![StaffHub 圖示](media/o365-staffhub-64x64.png) <br> [StaffHub](https://products.office.com/microsoft-staffhub/staff-scheduling-software)
| ![自黏便箋圖示](media/o365-stickynotes-64x64.png) <br> [自黏便箋](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![資料流圖示](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![Sway 圖示](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![小組圖示](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![待辦事項] 圖示](media/o365-todo-64x64.png) <br> [To-Do](https://todo.microsoft.com)
| ![Visio 圖示](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Word 圖示](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) |![Yammer 圖示](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview) | ![Yammer 圖示](media/o365-yammer-64x64.png) <br> [Yammer<br>通知程式](https://products.office.com/yammer/yammer-overview) |  |

## <a name="supported-powershell-modules"></a>支援的 PowerShell 模組

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Azure 圖示](media/o365-azure-64x64.png) <br> [Azure AD <br> PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Exchange 圖示](media/o365-exchange-64x64.png) <br> [Exchange Online <br> PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![SharePoint 圖示](media/o365-sharepoint-64x64.png) <br> [SharePoint Online <br> PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)