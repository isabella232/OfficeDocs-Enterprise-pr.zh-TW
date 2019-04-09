---
title: Office 365 用戶端應用程式支援人員-條件式存取
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_Enterprise
- M365-subscription-management
description: 了解條件式存取的 Office 365 用戶端應用程式支援
ms.openlocfilehash: 3212d15f2df68256fc80e4544fc7e61cdccc82c2
ms.sourcegitcommit: 80bc767a9c88a259facb3894b9a168c85d35eb70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "31517557"
---
# <a name="office-365-client-app-support---conditional-access"></a>Office 365 用戶端應用程式支援人員-條件式存取

在現代的工作場所，使用者可以存取貴組織的資源從幾乎可以使用各種不同的裝置和應用程式。 因此，只將重點放在誰可以存取資源不足適用。 如何及其中資源正在存取您的存取控制基礎結構，也必須支援您的組織。 使用 Azure AD 裝置、 位置及多重要素驗證型條件式存取，您可以符合此新的需求。 條件式存取是的可讓您以強制執行您在環境中，所有根據特定條件的應用程式的存取上的控制項，並從集中位置管理 Azure Active Directory 的功能。

深入了解[條件式存取](https://docs.microsoft.com/azure/active-directory/conditional-access/)。

## <a name="supported-platforms"></a>支援的平台

 - Windows 10 桌面
 - Windows 10 新式應用程式
 - 網頁瀏覽器
 - Android<sup>1</sup>
 - iOS
 - macOS<sup>2</sup>

如需 Office 365 中的平台支援的詳細資訊，請參閱 < <b0>Office 365 的系統需求</b0>。

## <a name="supported-clients"></a>支援的用戶端

最新版的下列用戶端支援條件式存取：

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Azure 的圖示](media/o365-azure-64x64.png) <br> [Azure AD<br>入口網站 ](https://azure.microsoft.com/features/azure-portal/) | ![Access 圖示](media/o365-access-64x64.png) <br> [Access](https://products.office.com/access) | ![Delve 圖示](media/o365-delve-64x64.png) <br> [Delve<sup>1</sup>](https://products.office.com/business/intelligent-search) | ![Dynamics 365 圖示](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) | ![Edge 圖示](media/o365-edge-64x64.png) <br> [銳利](https://www.microsoft.com/windows/microsoft-edge) 
| ![Exchange 圖示](media/o365-exchange-64x64.png) <br> [Exchange](https://products.office.com/exchange/exchange-online) | ![Excel 圖示](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![流程圖示](media/o365-flow-64x64.png) <br> [流程](https://flow.microsoft.com) | ![表單圖示](media/o365-forms-64x64.png) <br> [表單](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Kaizala 圖示](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) 
| ![透鏡圖示](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![Office 365 系統管理員圖示](media/o365-o365admin-64x64.png) <br> [Office 365<br>系統](https://products.office.com/business/manage-office-365-admin-app) | ![OneDrive 商務圖示](media/o365-OneDrive-64x64.png) <br> [OneDrive<sup>2</sup>](https://products.office.com/onedrive-for-business/online-cloud-storage) | ![OneNote 圖示](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Outlook 圖示](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) |
| ![規劃圖示](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![PowerBI 圖示](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com) | ![PowerPoint 圖示](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![[專案] 圖示](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![Publisher 圖示](media/o365-publisher-64x64.png) <br> [出版者](https://products.office.com/publisher)
| ![SharePoint 圖示](media/o365-sharepoint-64x64.png) <br> [Sharepoint](https://products.office.com/sharepoint) | ![Skype 商務圖示](media/o365-skypeforbusiness-64x64.png) <br> [商務用 Skype<br>商務](https://www.skype.com/business/) | ![自黏便箋圖示](media/o365-stickynotes-64x64.png) <br> [自黏便箋](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![資料流圖示](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![Sway 圖示](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) 
| ![Teams 圖示](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![待辦事項] 圖示](media/o365-todo-64x64.png) <br> [To-Do](https://todo.microsoft.com) | ![Visio 圖示](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Word 圖示](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Yammer 圖示](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview)

> [!NOTE]
> <sup>1</sup>支援 Delve 上 Android 即將推出。 <br>
> 在即將推出的 macOS 上 onedrive <sup>2</sup>支援。