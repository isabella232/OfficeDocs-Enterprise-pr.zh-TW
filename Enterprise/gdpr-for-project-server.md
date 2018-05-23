---
title: 適用於 Project Server 的 GDPR
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: 深入了解如何在內部部署 Project Server 中解決 GDPR 需求。
ms.openlocfilehash: 6a630dc4cef2c4117e0ba25497f898d0b8da221b
ms.sourcegitcommit: aabd369fc8b397f9e738374d42d8afd18b96d469
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="gdpr-for-project-server"></a><span data-ttu-id="13acc-103">適用於 Project Server 的 GDPR</span><span class="sxs-lookup"><span data-stu-id="13acc-103">Plan for Project Server</span></span>

<span data-ttu-id="13acc-p101">Project Server 會使用自訂指令碼來匯出及編輯 Project Web App 中的使用者資料。基本程序為：</span><span class="sxs-lookup"><span data-stu-id="13acc-p101">Project Server uses custom scripts to export and redact user data in Project Web App. The basic process is:</span></span>

1.  <span data-ttu-id="13acc-106">在您的伺服器陣列中尋找 Project Web App 網站。</span><span class="sxs-lookup"><span data-stu-id="13acc-106">Find the Project Web App sites in your farm.</span></span>

2.  <span data-ttu-id="13acc-107">在包含使用者的每個網站中尋找專案。</span><span class="sxs-lookup"><span data-stu-id="13acc-107">Find the projects in each site that contain the user.</span></span>

3.  <span data-ttu-id="13acc-108">匯出及檢閱您想要檢閱的資料類型。</span><span class="sxs-lookup"><span data-stu-id="13acc-108">Export and review the types of data that you want to review.</span></span>

4.  <span data-ttu-id="13acc-109">視需要編輯資料。</span><span class="sxs-lookup"><span data-stu-id="13acc-109">Redact data as needed.</span></span>

<span data-ttu-id="13acc-110">下列文章會詳細說明這些步驟：</span><span class="sxs-lookup"><span data-stu-id="13acc-110">These three scenarios are covered in detail in the following articles:</span></span>

- [<span data-ttu-id="13acc-111">從 Project Server 匯出使用者資料</span><span class="sxs-lookup"><span data-stu-id="13acc-111">Export user data from Project Server</span></span>](/Project/export-user-data-from-project-server?toc=/Office365/Enterprise/toc.json)

- [<span data-ttu-id="13acc-112">從 Project Server 刪除使用者資料</span><span class="sxs-lookup"><span data-stu-id="13acc-112">Delete user data from Project Server</span></span>](/Project/delete-user-data-from-project-server?toc=/Office365/Enterprise/toc.json)


<span data-ttu-id="13acc-113">請注意，Project Server 是以 SharePoint Server 為基礎來建置的，並且會將事件記錄到 SharePoint ULS 記錄和使用狀況資料庫。</span><span class="sxs-lookup"><span data-stu-id="13acc-113">Note that Project Server is built on top of SharePoint Server and logs events to the SharePoint ULS logs and Usage database.</span></span>
