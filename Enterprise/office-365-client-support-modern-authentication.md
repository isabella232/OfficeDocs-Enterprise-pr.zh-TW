---
title: Office 365 用戶端應用程式支援-新式驗證
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
description: 適用于新式驗證的 Office 365 用戶端應用程式支援。
ms.openlocfilehash: 603cc34e449b11efcacb8802c21cd3b4d08f37bb
ms.sourcegitcommit: 346fde563ad598598a9832f8a0a6f7cc0a802306
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "34704195"
---
# <a name="office-365-client-app-support---modern-authentication"></a>Office 365 用戶端應用程式支援-新式驗證

新式驗證可為不同平臺上的 Office 用戶端應用程式啟用 Active Directory 驗證程式庫 (ADAL) 型登入。 這會啟用登入功能, 例如多重要素驗證 (MFA)、智慧卡和憑證型驗證。

深入瞭解[多重要素驗證](https://docs.microsoft.com/azure/active-directory/authentication/multi-factor-authentication)和[憑證型驗證](https://docs.microsoft.com/azure/active-directory/active-directory-certificate-based-authentication-get-started)。

## <a name="supported-platforms"></a>支援的平台

 - Windows 10 桌上出版
 - Windows 10 新式應用程式
 - 網頁瀏覽器
 - Android
 - 適用
 - macOS

如需 Office 365 平臺支援的詳細資訊, 請參閱[office 365 的系統需求](https://products.office.com/office-system-requirements)。

## <a name="supported-clients"></a>支援的用戶端

下列用戶端的最新版本支援新式驗證:

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![存取圖示](media/o365-access-64x64.png) <br> [存取](https://products.office.com/access) | ![Azure 圖示](media/o365-azure-64x64.png) <br> [Azure <br>入口網站](https://azure.microsoft.com/features/azure-portal/) | ![公司入口網站圖示](media/o365-microsoft-64x64.png) <br> [公司<br>入口網站](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) | ![Delve 圖示](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Dynamics 365 圖示](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) 
| ![Edge 圖示](media/o365-edge-64x64.png) <br> [銳利](https://www.microsoft.com/windows/microsoft-edge) | ![Excel 圖示](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![流程圖標](media/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![表單圖示](media/o365-forms-64x64.png) <br> [表單](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Kaizala 圖示](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) 
| ![Office 365 系統管理員圖示](media/o365-o365admin-64x64.png) <br> [Office 365 <br>系統管理員](https://products.office.com/business/manage-office-365-admin-app) | ![鏡頭圖示](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![商務用 OneDrive 圖示](media/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) |  ![OneNote 圖示](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Outlook 圖示](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) 
| ![Planner 圖示](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![PowerBI 圖示](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com)| ![PowerPoint 圖示](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![專案圖示](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![SharePoint 圖示](media/o365-sharepoint-64x64.png) <br> [Sharepoint](https://products.office.com/sharepoint) 
| ![商務用 Skype 圖示](media/o365-skypeforbusiness-64x64.png) <br> [<br>商務用 Skype](https://www.skype.com/business/) | ![StaffHub 圖示](media/o365-staffhub-64x64.png) <br> [StaffHub](https://products.office.com/microsoft-staffhub/staff-scheduling-software)| ![粘滯便箋圖示](media/o365-stickynotes-64x64.png) <br> [粘滯便箋](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![資料流程圖示](media/o365-stream-64x64.png) <br> [資料流](https://stream.microsoft.com) | ![Sway 圖示](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) 
| ![小組圖示](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![待辦事項圖示](media/o365-todo-64x64.png) <br> [To-Do](https://todo.microsoft.com) | ![Visio 圖示](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Word 圖示](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Yammer 圖示](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview) 
| ![Yammer 圖示](media/o365-yammer-64x64.png) <br> [Yammer <br>通告程式](https://products.office.com/yammer/yammer-overview) |  |

## <a name="supported-powershell-modules"></a>支援的 PowerShell 模組

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Azure 圖示](media/o365-azure-ad-64x64.png) <br> [Azure AD <br> PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Exchange 圖示](media/o365-exchange-64x64.png) <br> [Exchange Online <br> PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![SharePoint 圖示](media/o365-sharepoint-64x64.png) <br> [SharePoint Online <br> PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)