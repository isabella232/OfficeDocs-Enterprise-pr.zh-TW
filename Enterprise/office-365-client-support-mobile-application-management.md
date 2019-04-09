---
title: Office 365 用戶端應用程式支援行動應用程式管理
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
description: 了解 Office 365 用戶端應用程式支援的行動應用程式管理
ms.openlocfilehash: b75b992bf45ff1a899e71a9f6b7903e3f78a34d4
ms.sourcegitcommit: 80bc767a9c88a259facb3894b9a168c85d35eb70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "31517547"
---
# <a name="office-365-client-app-support---mobile-application-management"></a><span data-ttu-id="309cb-103">Office 365 用戶端應用程式支援行動應用程式管理</span><span class="sxs-lookup"><span data-stu-id="309cb-103">Office 365 Client App Support - Mobile Application Management</span></span>

<span data-ttu-id="309cb-104">使用 Intune 管理功能的套件，行動應用程式管理 (MAM) 可讓您將發佈、 推入、 設定、 安全、 監視和更新您的使用者的行動應用程式。</span><span class="sxs-lookup"><span data-stu-id="309cb-104">Leveraging the suite of Intune management features, mobile application management (MAM) lets you publish, push, configure, secure, monitor, and update mobile apps for your users.</span></span> <span data-ttu-id="309cb-105">MAM 可以保護公司內所有的裝置，應用程式的資料是否或不在 Intune 中註冊。</span><span class="sxs-lookup"><span data-stu-id="309cb-105">MAM can protect an organization's data within an application for all devices, whether enrolled in Intune or not.</span></span>

<span data-ttu-id="309cb-106">了解更多關於[行動應用程式管理](https://docs.microsoft.com/intune/mam-faq)和[多重 identity MAM](https://docs.microsoft.com/intune/app-protection-policy)。</span><span class="sxs-lookup"><span data-stu-id="309cb-106">Learn more about [mobile application management](https://docs.microsoft.com/intune/mam-faq) and [multi-identity MAM](https://docs.microsoft.com/intune/app-protection-policy).</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="309cb-107">支援的平台</span><span class="sxs-lookup"><span data-stu-id="309cb-107">Supported platforms</span></span>

 - <span data-ttu-id="309cb-108">Android</span><span class="sxs-lookup"><span data-stu-id="309cb-108">Android</span></span>
 - <span data-ttu-id="309cb-109">iOS<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="309cb-109">iOS<sup>1</sup></span></span>

<span data-ttu-id="309cb-110">如需 Office 365 中的平台支援的詳細資訊，請參閱 < <b0>Office 365 的系統需求</b0>。</span><span class="sxs-lookup"><span data-stu-id="309cb-110">For more information about platform support in Office 365, see [System requirements for Office 365](https://products.office.com/office-system-requirements).</span></span>

## <a name="supported-clients"></a><span data-ttu-id="309cb-111">支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="309cb-111">Supported clients</span></span>

<span data-ttu-id="309cb-112">最新版的下列用戶端支援行動應用程式管理：</span><span class="sxs-lookup"><span data-stu-id="309cb-112">The latest versions of the following clients support mobile application management:</span></span>

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Dynamics 365 圖示](media/o365-dynamics365-64x64.png) <br> [<span data-ttu-id="309cb-114">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="309cb-114">Dynamics 365</span></span>](https://dynamics.microsoft.com) | ![Edge 圖示](media/o365-edge-64x64.png) <br> [<span data-ttu-id="309cb-116">銳利</span><span class="sxs-lookup"><span data-stu-id="309cb-116">Edge</span></span>](https://www.microsoft.com/windows/microsoft-edge) | ![Excel 圖示](media/o365-excel-64x64.png) <br> [<span data-ttu-id="309cb-118">Excel</span><span class="sxs-lookup"><span data-stu-id="309cb-118">Excel</span></span>](https://products.office.com/excel) | ![流程圖示](media/o365-flow-64x64.png) <br> [<span data-ttu-id="309cb-120">流程</span><span class="sxs-lookup"><span data-stu-id="309cb-120">Flow</span></span>](https://flow.microsoft.com) | ![Kaizala 圖示](media/o365-kaizala-64x64.png) <br> [<span data-ttu-id="309cb-122">Kaizala</span><span class="sxs-lookup"><span data-stu-id="309cb-122">Kaizala</span></span>](https://products.office.com/en/business/microsoft-kaizala) 
| ![OneDrive 商務圖示](media/o365-OneDrive-64x64.png) <br> [<span data-ttu-id="309cb-124">OneDrive</span><span class="sxs-lookup"><span data-stu-id="309cb-124">OneDrive</span></span>](https://products.office.com/onedrive-for-business/online-cloud-storage) | ![OneNote 圖示](media/o365-OneNote-64x64.png) <br> [<span data-ttu-id="309cb-126">OneNote</span><span class="sxs-lookup"><span data-stu-id="309cb-126">OneNote</span></span>](https://products.office.com/onenote) | ![Outlook 圖示](media/o365-outlook-64x64.png) <br> [<span data-ttu-id="309cb-128">Outlook</span><span class="sxs-lookup"><span data-stu-id="309cb-128">Outlook</span></span>](https://products.office.com/outlook) | ![規劃圖示](media/o365-planner-64x64.png) <br> [<span data-ttu-id="309cb-130">Planner</span><span class="sxs-lookup"><span data-stu-id="309cb-130">Planner</span></span>](https://products.office.com/business/task-management-software) | ![PowerApps 圖示](media/o365-powerapps-64x64.png) <br> [<span data-ttu-id="309cb-132">PowerApps</span><span class="sxs-lookup"><span data-stu-id="309cb-132">PowerApps</span></span> ](https://powerapps.microsoft.com) 
| ![PowerBI 圖示](media/o365-powerbi-64x64.png) <br> [<span data-ttu-id="309cb-134">Power BI</span><span class="sxs-lookup"><span data-stu-id="309cb-134">Power BI</span></span>](https://powerbi.microsoft.com) | ![PowerPoint 圖示](media/o365-powerpoint-64x64.png) <br> [<span data-ttu-id="309cb-136">PowerPoint</span><span class="sxs-lookup"><span data-stu-id="309cb-136">PowerPoint</span></span>](https://products.office.com/powerpoint) | ![SharePoint 圖示](media/o365-sharepoint-64x64.png) <br> [<span data-ttu-id="309cb-138">Sharepoint</span><span class="sxs-lookup"><span data-stu-id="309cb-138">Sharepoint</span></span>](https://products.office.com/sharepoint) | ![Skype 商務圖示](media/o365-skypeforbusiness-64x64.png) <br> [<span data-ttu-id="309cb-140">商務用 Skype<br>商務</span><span class="sxs-lookup"><span data-stu-id="309cb-140">Skype for <br> Business</span></span>](https://www.skype.com/business/) | ![StaffHub 圖示](media/o365-staffhub-64x64.png) <br> [<span data-ttu-id="309cb-142">StaffHub</span><span class="sxs-lookup"><span data-stu-id="309cb-142">StaffHub</span></span>](https://products.office.com/microsoft-staffhub/staff-scheduling-software) 
| ![資料流圖示](media/o365-stream-64x64.png) <br> [<span data-ttu-id="309cb-144">Stream</span><span class="sxs-lookup"><span data-stu-id="309cb-144">Stream</span></span>](https://stream.microsoft.com) | ![Sway 圖示](media/o365-sway-64x64.png) <br> [<span data-ttu-id="309cb-146">Sway<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="309cb-146">Sway<sup>1</sup></span></span>](https://sway.com) | ![Teams 圖示](media/o365-teams-64x64.png) <br> [<span data-ttu-id="309cb-148">Teams</span><span class="sxs-lookup"><span data-stu-id="309cb-148">Teams</span></span>](https://products.office.com/microsoft-teams/group-chat-software) | ![待辦事項] 圖示](media/o365-todo-64x64.png) <br> [<span data-ttu-id="309cb-150">To-Do</span><span class="sxs-lookup"><span data-stu-id="309cb-150">To-Do</span></span>](https://todo.microsoft.com) | ![Visio 圖示](media/o365-visio-64x64.png) <br> [<span data-ttu-id="309cb-152">Visio</span><span class="sxs-lookup"><span data-stu-id="309cb-152">Visio</span></span>](https://products.office.com/visio/flowchart-software) 
| ![Word 圖示](media/o365-word-64x64.png) <br> [<span data-ttu-id="309cb-154">Word</span><span class="sxs-lookup"><span data-stu-id="309cb-154">Word</span></span>](https://products.office.com/word) | ![Yammer 圖示](media/o365-yammer-64x64.png) <br> [<span data-ttu-id="309cb-156">Yammer</span><span class="sxs-lookup"><span data-stu-id="309cb-156">Yammer</span></span>](https://products.office.com/yammer/yammer-overview)

> [!NOTE]
> <span data-ttu-id="309cb-157">即將推出的 iOS 上的 Sway <sup>1</sup>支援。</span><span class="sxs-lookup"><span data-stu-id="309cb-157"><sup>1</sup> Support for Sway on iOS coming soon.</span></span>