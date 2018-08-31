---
title: 在 Office 365 中檢視目錄同步處理狀態
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: 了解如何停用目錄同步作業。您也可以檢視其狀態。
ms.openlocfilehash: c843fa4d71976cbdd0d6d3d10720e2845b26796c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540237"
---
# <a name="view-directory-synchronization-status-in-office-365"></a><span data-ttu-id="c0603-104">在 Office 365 中檢視目錄同步處理狀態</span><span class="sxs-lookup"><span data-stu-id="c0603-104">View directory synchronization status in Office 365</span></span>
<span data-ttu-id="c0603-105">如果您已整合 Azure AD 您在內部部署 Active Directory 來使用 Office 365 同步處理內部部署環境，您也可以檢查您同步處理的狀態。</span><span class="sxs-lookup"><span data-stu-id="c0603-105">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="c0603-106">檢視目錄同步處理狀態</span><span class="sxs-lookup"><span data-stu-id="c0603-106">View directory synchronization status</span></span>
- <span data-ttu-id="c0603-107">登入 Office 365 系統管理中心和在 [首頁] 頁面上選擇 [ **DirSync 狀態**。</span><span class="sxs-lookup"><span data-stu-id="c0603-107">Sign in to the Office 365 admin center and choose **DirSync Status** on the home page.</span></span> 
- <span data-ttu-id="c0603-p102">或者，您可以前往 ＜ 給**使用者** \> **作用中使用者**，在**作用中使用者**] 頁面上，選擇 [**更多** \> **目錄同步處理**。在 [**目錄同步處理**] 窗格中，選擇 [**移至 [DirSync 管理**。</span><span class="sxs-lookup"><span data-stu-id="c0603-p102">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**. On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>
    
## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="c0603-110">在 [管理目錄同步處理] 頁面上的資訊</span><span class="sxs-lookup"><span data-stu-id="c0603-110">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="c0603-111">下表列出您可以取得資訊] 頁面的功能。</span><span class="sxs-lookup"><span data-stu-id="c0603-111">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="c0603-p103">以目錄同步作業問題時，發生之錯誤會列在此頁面上。如需不同可能遇到的錯誤的詳細資訊，請參閱[Office 365 中的身分識別目錄同步處理錯誤](identify-directory-synchronization-errors.md)。</span><span class="sxs-lookup"><span data-stu-id="c0603-p103">If there is a problem with your directory synchronization, the errors are listed on this page as well. For more information about different errors you might encounter, see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="c0603-114">**項目**</span><span class="sxs-lookup"><span data-stu-id="c0603-114">**Item**</span></span>|<span data-ttu-id="c0603-115">**它的功能**</span><span class="sxs-lookup"><span data-stu-id="c0603-115">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="c0603-116">**已驗證的網域**</span><span class="sxs-lookup"><span data-stu-id="c0603-116">**Domains verified**</span></span> | <span data-ttu-id="c0603-117">您已驗證您的 Office 365 租用中的網域數目的擁有人。</span><span class="sxs-lookup"><span data-stu-id="c0603-117">Number of domains in your Office 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="c0603-118">**未驗證的網域**</span><span class="sxs-lookup"><span data-stu-id="c0603-118">**Domains not verified**</span></span> | <span data-ttu-id="c0603-119">您已新增，但未驗證的網域。</span><span class="sxs-lookup"><span data-stu-id="c0603-119">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="c0603-120">**啟用目錄同步處理**</span><span class="sxs-lookup"><span data-stu-id="c0603-120">**Directory sync enabled**</span></span> |<span data-ttu-id="c0603-p104">True 或 False。會指定您是否已啟用目錄同步處理。</span><span class="sxs-lookup"><span data-stu-id="c0603-p104">True or False. Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="c0603-123">**最新的目錄同步處理**</span><span class="sxs-lookup"><span data-stu-id="c0603-123">**Latest directory sync**</span></span> | <span data-ttu-id="c0603-p105">上次執行目錄同步處理。將會顯示一則警告訊息和連結的疑難排解工具如果上次同步處理成功三天以上。</span><span class="sxs-lookup"><span data-stu-id="c0603-p105">Last time directory sync ran. Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="c0603-126">**啟用密碼同步處理**</span><span class="sxs-lookup"><span data-stu-id="c0603-126">**Password sync enabled**</span></span> | <span data-ttu-id="c0603-p106">True 或 False。會指定是否必須我們內部部署與您的 Office 365 租用戶之間的密碼雜湊同步處理。</span><span class="sxs-lookup"><span data-stu-id="c0603-p106">True or False. Specifies whether you have password hash sync between our on-premises and your Office 365 tenant.</span></span> |
|<span data-ttu-id="c0603-129">**最後一個密碼同步處理**</span><span class="sxs-lookup"><span data-stu-id="c0603-129">**Last Password Sync**</span></span> | <span data-ttu-id="c0603-p107">最後一次密碼雜湊同步處理已執行。將會顯示一則警告訊息和連結的疑難排解工具如果上次同步處理成功三天以上。</span><span class="sxs-lookup"><span data-stu-id="c0603-p107">Last time password hash sync ran. Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="c0603-132">**目錄同步處理用戶端版本**</span><span class="sxs-lookup"><span data-stu-id="c0603-132">**Directory sync client version**</span></span> | <span data-ttu-id="c0603-133">如果發行 Azure AD 連線的新版本會包含下載連結。</span><span class="sxs-lookup"><span data-stu-id="c0603-133">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="c0603-134">**IDFix 工具**</span><span class="sxs-lookup"><span data-stu-id="c0603-134">**IDFix Tool**</span></span> | <span data-ttu-id="c0603-135">下載[IDFix](install-and-run-idfix.md)，您可以使用來檢查本機 Active Directory 工具的連結。</span><span class="sxs-lookup"><span data-stu-id="c0603-135">Download link to [IDFix](install-and-run-idfix.md), a tool you can use to check you local Active Directory.</span></span> |
|<span data-ttu-id="c0603-136">**目錄同步處理服務帳戶**</span><span class="sxs-lookup"><span data-stu-id="c0603-136">**Directory sync service account**</span></span> | <span data-ttu-id="c0603-137">會顯示您的 Office 365 目錄同步處理服務帳戶的名稱。</span><span class="sxs-lookup"><span data-stu-id="c0603-137">Displays the name of you Office 365 directory sync service account.</span></span> |