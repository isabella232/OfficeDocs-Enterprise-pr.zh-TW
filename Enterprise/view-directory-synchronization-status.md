---
title: 檢視 Office 365 中的目錄同步處理狀態
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: 了解如何停用目錄同步作業。 您也可以檢視其狀態。
ms.openlocfilehash: a38b723db6f5bafe246e774972ca89c65bc9c846
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33492099"
---
# <a name="view-directory-synchronization-status-in-office-365"></a><span data-ttu-id="4b1e1-104">檢視 Office 365 中的目錄同步處理狀態</span><span class="sxs-lookup"><span data-stu-id="4b1e1-104">View directory synchronization status in Office 365</span></span>

<span data-ttu-id="4b1e1-105">如果您已經與 Office 365 同步內部部署環境，與 Azure AD 整合您的內部部署 Active Directory，您也可以檢查您同步處理的狀態。</span><span class="sxs-lookup"><span data-stu-id="4b1e1-105">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="4b1e1-106">檢視目錄同步處理狀態</span><span class="sxs-lookup"><span data-stu-id="4b1e1-106">View directory synchronization status</span></span>

- <span data-ttu-id="4b1e1-107">登入[Microsoft 365 系統管理中心](https://admin.microsoft.com)，選擇 [**目錄同步狀態**]，請在 [首頁] 頁面上。</span><span class="sxs-lookup"><span data-stu-id="4b1e1-107">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) and choose **DirSync Status** on the home page.</span></span>
- <span data-ttu-id="4b1e1-108">或者，您可以移至 [**使用者** \> **作用中的使用者**，並在 [**作用中使用者**] 頁面上，選擇 [**更多** \> **目錄同步處理**。</span><span class="sxs-lookup"><span data-stu-id="4b1e1-108">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span> <span data-ttu-id="4b1e1-109">在 [**目錄同步處理**] 窗格中，選擇 [**移至 [目錄同步管理**。</span><span class="sxs-lookup"><span data-stu-id="4b1e1-109">On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>

## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="4b1e1-110">在 [管理目錄同步處理] 頁面上的資訊</span><span class="sxs-lookup"><span data-stu-id="4b1e1-110">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="4b1e1-111">下表列出您可以取得資訊] 頁面的功能。</span><span class="sxs-lookup"><span data-stu-id="4b1e1-111">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="4b1e1-112">如果沒有您的目錄同步處理的問題，錯誤會列在此頁面上。</span><span class="sxs-lookup"><span data-stu-id="4b1e1-112">If there is a problem with your directory synchronization, the errors are listed on this page as well.</span></span> <span data-ttu-id="4b1e1-113">如需不同，可能會遇到的錯誤的詳細資訊，請參閱 <<c0>在 Office 365 中的身分識別目錄同步處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="4b1e1-113">For more information about different errors you might encounter, see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="4b1e1-114">**Item**</span><span class="sxs-lookup"><span data-stu-id="4b1e1-114">**Item**</span></span>|<span data-ttu-id="4b1e1-115">**功能**</span><span class="sxs-lookup"><span data-stu-id="4b1e1-115">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="4b1e1-116">**驗證的網域**</span><span class="sxs-lookup"><span data-stu-id="4b1e1-116">**Domains verified**</span></span> | <span data-ttu-id="4b1e1-117">您已經驗證您的 Office 365 租用戶中的網域數目的擁有人。</span><span class="sxs-lookup"><span data-stu-id="4b1e1-117">Number of domains in your Office 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="4b1e1-118">**未驗證的網域**</span><span class="sxs-lookup"><span data-stu-id="4b1e1-118">**Domains not verified**</span></span> | <span data-ttu-id="4b1e1-119">您可以新增，但卻未驗證的網域。</span><span class="sxs-lookup"><span data-stu-id="4b1e1-119">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="4b1e1-120">**啟用目錄同步處理**</span><span class="sxs-lookup"><span data-stu-id="4b1e1-120">**Directory sync enabled**</span></span> |<span data-ttu-id="4b1e1-121">則為 true 或 False。</span><span class="sxs-lookup"><span data-stu-id="4b1e1-121">True or False.</span></span> <span data-ttu-id="4b1e1-122">會指定是否已啟用目錄同步處理。</span><span class="sxs-lookup"><span data-stu-id="4b1e1-122">Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="4b1e1-123">**最新的目錄同步處理**</span><span class="sxs-lookup"><span data-stu-id="4b1e1-123">**Latest directory sync**</span></span> | <span data-ttu-id="4b1e1-124">目錄同步處理執行的時間。</span><span class="sxs-lookup"><span data-stu-id="4b1e1-124">Last time directory sync ran.</span></span> <span data-ttu-id="4b1e1-125">如果會顯示一則警告，並連結至疑難排解工具上次同步處理已三天以上。</span><span class="sxs-lookup"><span data-stu-id="4b1e1-125">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="4b1e1-126">**啟用密碼同步處理**</span><span class="sxs-lookup"><span data-stu-id="4b1e1-126">**Password sync enabled**</span></span> | <span data-ttu-id="4b1e1-127">則為 true 或 False。</span><span class="sxs-lookup"><span data-stu-id="4b1e1-127">True or False.</span></span> <span data-ttu-id="4b1e1-128">會指定是否必須讓我們內部部署與您的 Office 365 租用戶之間的密碼雜湊同步處理。</span><span class="sxs-lookup"><span data-stu-id="4b1e1-128">Specifies whether you have password hash sync between our on-premises and your Office 365 tenant.</span></span> |
|<span data-ttu-id="4b1e1-129">**最後一個密碼同步處理**</span><span class="sxs-lookup"><span data-stu-id="4b1e1-129">**Last Password Sync**</span></span> | <span data-ttu-id="4b1e1-130">密碼雜湊同步處理執行的時間。</span><span class="sxs-lookup"><span data-stu-id="4b1e1-130">Last time password hash sync ran.</span></span> <span data-ttu-id="4b1e1-131">如果會顯示一則警告，並連結至疑難排解工具上次同步處理已三天以上。</span><span class="sxs-lookup"><span data-stu-id="4b1e1-131">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="4b1e1-132">**目錄同步處理用戶端版本**</span><span class="sxs-lookup"><span data-stu-id="4b1e1-132">**Directory sync client version**</span></span> | <span data-ttu-id="4b1e1-133">如果已釋放 Azure AD Connect 的新版本會包含的下載連結。</span><span class="sxs-lookup"><span data-stu-id="4b1e1-133">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="4b1e1-134">**IDFix 工具**</span><span class="sxs-lookup"><span data-stu-id="4b1e1-134">**IDFix Tool**</span></span> | <span data-ttu-id="4b1e1-135">[IDFix](install-and-run-idfix.md)，您可以使用來檢查本機 Active Directory 工具來下載連結。</span><span class="sxs-lookup"><span data-stu-id="4b1e1-135">Download link to [IDFix](install-and-run-idfix.md), a tool you can use to check you local Active Directory.</span></span> |
|<span data-ttu-id="4b1e1-136">**目錄同步處理服務帳戶**</span><span class="sxs-lookup"><span data-stu-id="4b1e1-136">**Directory sync service account**</span></span> | <span data-ttu-id="4b1e1-137">會顯示您 Office 365 目錄同步處理服務帳戶的名稱。</span><span class="sxs-lookup"><span data-stu-id="4b1e1-137">Displays the name of you Office 365 directory sync service account.</span></span> |