---
title: Office 365 用戶端應用程式支援人員-單一登入
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
description: Office 365 用戶端應用程式支援單一登入。
ms.openlocfilehash: 1ab1a2d7c461c1ae44f0fefba4b9a3663753fb97
ms.sourcegitcommit: 9c6e31204aa326c31d60befe80e610f702e65800
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "33990907"
---
# <a name="office-365-client-app-support--single-sign-on"></a>Office 365 用戶端應用程式支援人員-單一登入

單一登入 (SSO) 時，新增安全和方便您的使用者登入 Azure Active Directory (Azure AD) 中的應用程式。 搭配單一登入，使用者一次使用一個帳戶登入服務 (SaaS) 應用程式存取已加入網域的裝置，公司資源，軟體與 web 應用程式。

深入了解[單一登入](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on)。

## <a name="supported-platforms"></a>支援的平台

 - Windows 10 桌面
 - Windows 10 新式應用程式
 - 網頁瀏覽器
 - Android
 - iOS<sup>1</sup>
 - macOS

如需 Office 365 中的平台支援的詳細資訊，請參閱 < <b0>Office 365 的系統需求</b0>。

## <a name="supported-clients"></a>支援的用戶端

最新版的下列用戶端支援單一登入：

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Access 圖示](media/o365-access-64x64.png) <br> [存取](https://products.office.com/access) | ![公司入口網站圖示](media/o365-microsoft-64x64.png) <br> [公司<br>入口網站](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) | ![Edge 圖示](media/o365-edge-64x64.png) <br> [銳利](https://www.microsoft.com/windows/microsoft-edge) | ![Excel 圖示](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![流程圖示](media/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) 
| ![透鏡圖示](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![OneDrive 商務圖示](media/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) |  ![OneNote 圖示](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Outlook 圖示](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![規劃圖示](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) 
| ![PowerBI 圖示](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com)| ![PowerPoint 圖示](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![[專案] 圖示](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![Publisher 圖示](media/o365-publisher-64x64.png) <br> [Publisher](https://products.office.com/publisher) | ![SharePoint 圖示](media/o365-sharepoint-64x64.png) <br> [Sharepoint](https://products.office.com/sharepoint) 
| ![Skype 商務圖示](media/o365-skypeforbusiness-64x64.png) <br> [商務用 Skype<br>商務](https://www.skype.com/business/) | ![自黏便箋圖示](media/o365-stickynotes-64x64.png) <br> [自黏便箋](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![Sway 圖示](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Teams 圖示](media/o365-teams-64x64.png) <br> [Teams<sup>1</sup>](https://products.office.com/microsoft-teams/group-chat-software) | ![待辦事項] 圖示](media/o365-todo-64x64.png) <br> [To-Do](https://todo.microsoft.com) 
| ![Visio 圖示](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Word 圖示](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Yammer 圖示](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview) |

## <a name="supported-powershell-modules"></a>支援的 PowerShell 模組

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Azure 的圖示](media/o365-azure-64x64.png) <br> [Azure AD <br> PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Exchange 圖示](media/o365-exchange-64x64.png) <br> [Exchange Online <br> PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![SharePoint 圖示](media/o365-sharepoint-64x64.png) <br> [SharePoint Online <br> PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)

> [!NOTE]
> 只有在 iOS 上的團隊<sup>1</sup>支援。 <br>