---
title: 在 Microsoft 365 中查看目錄同步處理狀態
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: 在本文中，您可以瞭解如何檢查 Office 365 中目錄同步處理的狀態。
ms.openlocfilehash: 9aaad085854326ebb6542f03256ae851b27f0980
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605859"
---
# <a name="view-directory-synchronization-status-in-microsoft-365"></a><span data-ttu-id="e87a6-103">在 Microsoft 365 中查看目錄同步處理狀態</span><span class="sxs-lookup"><span data-stu-id="e87a6-103">View directory synchronization status in Microsoft 365</span></span>

<span data-ttu-id="e87a6-104">如果您已整合內部部署 Active Directory 與 Azure AD，請同步處理內部部署環境與 Microsoft 365，您也可以檢查同步處理的狀態。</span><span class="sxs-lookup"><span data-stu-id="e87a6-104">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Microsoft 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="e87a6-105">視目錄同步處理狀態</span><span class="sxs-lookup"><span data-stu-id="e87a6-105">View directory synchronization status</span></span>

- <span data-ttu-id="e87a6-106">登入[Microsoft 365 系統管理中心](https://admin.microsoft.com)，然後選擇首頁上的**DirSync 狀態**。</span><span class="sxs-lookup"><span data-stu-id="e87a6-106">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) and choose **DirSync Status** on the home page.</span></span>
- <span data-ttu-id="e87a6-107">或者，您可以移至 [**使用者**作用中使用者]， \> **Active users**然後在 [作用中**使用者**] 頁面上，選擇 [**更多** \> **目錄同步**處理]。</span><span class="sxs-lookup"><span data-stu-id="e87a6-107">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span> <span data-ttu-id="e87a6-108">在 [**目錄同步**處理] 窗格中，選擇 [**移至 DirSync 管理**]。</span><span class="sxs-lookup"><span data-stu-id="e87a6-108">On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>

## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="e87a6-109">「管理目錄同步處理」頁面上的資訊</span><span class="sxs-lookup"><span data-stu-id="e87a6-109">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="e87a6-110">下表列出您可以在頁面上取得相關資訊的功能。</span><span class="sxs-lookup"><span data-stu-id="e87a6-110">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="e87a6-111">如果您的目錄同步處理有問題，錯誤也會列在此頁面上。</span><span class="sxs-lookup"><span data-stu-id="e87a6-111">If there is a problem with your directory synchronization, the errors are listed on this page as well.</span></span> <span data-ttu-id="e87a6-112">如需您可能會遇到之不同錯誤的詳細資訊，請參閱[識別 Microsoft 365 中的目錄同步處理錯誤](identify-directory-synchronization-errors.md)。</span><span class="sxs-lookup"><span data-stu-id="e87a6-112">For more information about different errors you might encounter, see [Identify directory synchronization errors in Microsoft 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="e87a6-113">**項目**</span><span class="sxs-lookup"><span data-stu-id="e87a6-113">**Item**</span></span>|<span data-ttu-id="e87a6-114">**功能**</span><span class="sxs-lookup"><span data-stu-id="e87a6-114">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="e87a6-115">**已驗證網域**</span><span class="sxs-lookup"><span data-stu-id="e87a6-115">**Domains verified**</span></span> | <span data-ttu-id="e87a6-116">您已驗證您的 Microsoft 365 租使用者中的網域數目。</span><span class="sxs-lookup"><span data-stu-id="e87a6-116">Number of domains in your Microsoft 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="e87a6-117">**未驗證的網域**</span><span class="sxs-lookup"><span data-stu-id="e87a6-117">**Domains not verified**</span></span> | <span data-ttu-id="e87a6-118">您已新增但未驗證的網域。</span><span class="sxs-lookup"><span data-stu-id="e87a6-118">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="e87a6-119">**已啟用目錄同步處理**</span><span class="sxs-lookup"><span data-stu-id="e87a6-119">**Directory sync enabled**</span></span> |<span data-ttu-id="e87a6-120">True 或 False。</span><span class="sxs-lookup"><span data-stu-id="e87a6-120">True or False.</span></span> <span data-ttu-id="e87a6-121">指定是否已啟用目錄同步處理。</span><span class="sxs-lookup"><span data-stu-id="e87a6-121">Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="e87a6-122">**最新目錄同步處理**</span><span class="sxs-lookup"><span data-stu-id="e87a6-122">**Latest directory sync**</span></span> | <span data-ttu-id="e87a6-123">上次執行目錄同步處理的時間。</span><span class="sxs-lookup"><span data-stu-id="e87a6-123">Last time directory sync ran.</span></span> <span data-ttu-id="e87a6-124">若上次同步處理超過三天以上，將會顯示警告及疑難排解工具的連結。</span><span class="sxs-lookup"><span data-stu-id="e87a6-124">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="e87a6-125">**已啟用密碼同步處理**</span><span class="sxs-lookup"><span data-stu-id="e87a6-125">**Password sync enabled**</span></span> | <span data-ttu-id="e87a6-126">True 或 False。</span><span class="sxs-lookup"><span data-stu-id="e87a6-126">True or False.</span></span> <span data-ttu-id="e87a6-127">指定您的內部部署與 Microsoft 365 租使用者之間是否有密碼雜湊同步處理。</span><span class="sxs-lookup"><span data-stu-id="e87a6-127">Specifies whether you have password hash sync between our on-premises and your Microsoft 365 tenant.</span></span> |
|<span data-ttu-id="e87a6-128">**上次密碼同步處理**</span><span class="sxs-lookup"><span data-stu-id="e87a6-128">**Last Password Sync**</span></span> | <span data-ttu-id="e87a6-129">上次執行密碼雜湊同步處理的時間。</span><span class="sxs-lookup"><span data-stu-id="e87a6-129">Last time password hash sync ran.</span></span> <span data-ttu-id="e87a6-130">若上次同步處理超過三天以上，將會顯示警告及疑難排解工具的連結。</span><span class="sxs-lookup"><span data-stu-id="e87a6-130">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="e87a6-131">**目錄同步處理用戶端版本**</span><span class="sxs-lookup"><span data-stu-id="e87a6-131">**Directory sync client version**</span></span> | <span data-ttu-id="e87a6-132">會包含下載連結，如果已發行新版本的 Azure AD Connect。</span><span class="sxs-lookup"><span data-stu-id="e87a6-132">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="e87a6-133">**目錄同步處理服務帳戶**</span><span class="sxs-lookup"><span data-stu-id="e87a6-133">**Directory sync service account**</span></span> | <span data-ttu-id="e87a6-134">顯示 Microsoft 365 目錄同步服務帳戶的名稱。</span><span class="sxs-lookup"><span data-stu-id="e87a6-134">Displays the name of your Microsoft 365 directory sync service account.</span></span> |