---
title: Office 365 用戶端應用程式支援設定格式化的條件的存取
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 7/17/2018
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: None
ms.collection: Strat_O365_Enterprise
description: 了解 Office 365 用戶端應用程式支援的設定格式化的條件的存取
ms.openlocfilehash: f9a1b4c022b00569a392d7f50bfcae583847ea3c
ms.sourcegitcommit: 4e654517825b74a3bbe171b915b134ba49231e2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2018
ms.locfileid: "21541963"
---
# <a name="office-365-client-app-support---conditional-access"></a>Office 365 用戶端應用程式支援設定格式化的條件的存取

現代工作地點的使用者可以存取您的組織資源使用各種裝置和應用程式從任何虛擬位置。因此，只著重在可存取資源的人員不敷招架。您的組織必須也支援提供如何在其中正在資源存取到您的存取控制基礎結構和。使用 Azure AD 裝置、 位置及多重要素驗證設定格式化的條件存取，您可以符合此新的需求。設定格式化的條件存取是的可讓您在環境中，所有根據特定條件的應用程式存取上的控制項，強制執行並從集中位置管理 Azure Active Directory 的功能。 

深入了解[以裝置為基礎](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-policy-connected-applications)、[位置型](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-locations)，及[MFA 型](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-conditions#users-and-groups)設定格式化的條件的存取。

## <a name="supported-platforms"></a>支援的平台

 - Windows 10 桌面
 - Windows 10 現代應用程式
 - Web 瀏覽器
 - Android
 - iOS
 - macOS<sup>1</sup>

## <a name="supported-clients"></a>支援的用戶端

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![探索圖示](images/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Excel 圖示](images/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![流程圖示](images/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![表單圖示](images/o365-forms-64x64.png) <br> [Forms](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Kaizala 圖示](images/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) 
| ![Office 365 Admin 圖示](images/o365-o365admin-64x64.png) <br> [Office 365<br>系統](https://products.office.com/business/manage-office-365-admin-app) | ![OneDrive for Business 圖示](images/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) | ![OneNote 圖示](images/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Outlook 圖示](images/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![規劃圖示](images/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) 
| ![PowerBI 圖示](images/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com) | ![PowerPoint 圖示](images/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![專案圖示](images/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![SharePoint 圖示](images/o365-sharepoint-64x64.png) <br> [Sharepoint<sup>1</sup>](https://products.office.com/sharepoint) | ![Skype 商務圖示](images/o365-skypeforbusiness-64x64.png) <br> [針對 Skype<br>商務](https://www.skype.com/business/) 
| ![StaffHub 圖示](images/o365-staffhub-64x64.png) <br> [StaffHub](https://products.office.com/microsoft-staffhub/staff-scheduling-software) | ![資料流圖示](images/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![Sway 圖示](images/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![小組圖示](images/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![待辦事項] 圖示](images/o365-todo-64x64.png) <br> [To-Do](https://todo.microsoft.com) 
| ![Visio 圖示](images/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Word 圖示](images/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Yammer 圖示](images/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview)

> [!NOTE]
> <sup>1</sup> SharePoint 應用程式支援在 macOS 即將推出。