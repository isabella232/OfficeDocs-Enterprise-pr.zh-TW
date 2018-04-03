---
title: Multgeo 環境中的使用者經驗
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: 了解在多個地理位置環境中的 SharePoint 和 OneDrive 使用者經驗。
ms.openlocfilehash: 91837883ef7c970674a500afa4fda9adfafc6d5b
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2018
---
# <a name="user-experience-in-a-multi-geo-environment"></a><span data-ttu-id="16e0c-103">在多個地理位置環境中的使用者經驗</span><span class="sxs-lookup"><span data-stu-id="16e0c-103">User experience in a multi-geo environment</span></span>

<span data-ttu-id="16e0c-104">以下是您的使用者會看到 OneDrive 多重地理組態中：</span><span class="sxs-lookup"><span data-stu-id="16e0c-104">Here’s what your users will see in a OneDrive Multi-Geo configuration:</span></span>

#### <a name="users-onedrive-for-business-location"></a><span data-ttu-id="16e0c-105">使用者的 OneDrive for Business 位置</span><span class="sxs-lookup"><span data-stu-id="16e0c-105">User’s OneDrive for Business location</span></span>

<span data-ttu-id="16e0c-p101">使用者會擁有其 OneDrive for Business 佈建在其偏好的資料位置。如果使用者瀏覽至包含不正確地理位置 （例如從先前的地理位置的書籤） OneDrive URL，其會自動重新導向至適當的地理位置中的 OneDrive。</span><span class="sxs-lookup"><span data-stu-id="16e0c-p101">Users will have their OneDrive for Business provisioned in their preferred data location. If a user navigates to a OneDrive URL that contains an incorrect geo-location (such as a bookmark from a previous geo-location), they are automatically redirected to the OneDrive in the appropriate geo-location.</span></span>

#### <a name="sharing"></a><span data-ttu-id="16e0c-108">共用</span><span class="sxs-lookup"><span data-stu-id="16e0c-108">Sharing</span></span>

<span data-ttu-id="16e0c-p102">人員選擇經驗顯示所有的使用者不論其地理位置。這可讓使用者在其相同的地理位置或其他任何您的租用戶地理位置的共用與另一位使用者。不同地理位置會檢視中顯示**與我共用**使用者的 onedrive for Business 和可以存取與單一登入經驗的地理位置不論它裝載於中的內容。</span><span class="sxs-lookup"><span data-stu-id="16e0c-p102">The People Picker experience shows all users regardless of their geo location. This allows a user to share with another user in their same geo or in any other of your tenant’s geo locations. Content from different geo locations will show up in the **Shared with Me** view in the user's OneDrive for Business and can be accessed with Single-Sign-On experience regardless of which geo-location it is hosted in.</span></span>

#### <a name="office-applications"></a><span data-ttu-id="16e0c-112">Office 應用程式</span><span class="sxs-lookup"><span data-stu-id="16e0c-112">Office applications</span></span>

<span data-ttu-id="16e0c-p103">如 Word、 Excel 及 PowerPoint 的 office 應用程式將自動會偵測正確 OneDrive for Business 地理位置的每位使用者登入。使用者不需要輸入其 OneDrive 的特定地理位置的 URL。</span><span class="sxs-lookup"><span data-stu-id="16e0c-p103">Office applications such as Word, Excel, and PowerPoint will automatically detect the correct OneDrive for Business geo-location for each user when they log in. Users do not need to enter the geo-specific URL for their OneDrive.</span></span>

#### <a name="onedrive-for-business-sync-client"></a><span data-ttu-id="16e0c-115">OneDrive for Business Sync 用戶端</span><span class="sxs-lookup"><span data-stu-id="16e0c-115">OneDrive for Business Sync Client</span></span>

<span data-ttu-id="16e0c-116">OneDrive for Business Sync 用戶端 (版本 17.3.6943.0625 及更新版本) 將會自動偵測正確 OneDrive for Business 地理位置的使用者。</span><span class="sxs-lookup"><span data-stu-id="16e0c-116">The OneDrive for Business Sync Client (version 17.3.6943.0625 and later) will automatically detect the correct OneDrive for Business geo location for the user.</span></span>

#### <a name="office-365-app-launcher"></a><span data-ttu-id="16e0c-117">Office 365 應用程式啟動器</span><span class="sxs-lookup"><span data-stu-id="16e0c-117">Office 365 app launcher</span></span>

<span data-ttu-id="16e0c-p104">應用程式啟動器是多重地理注意，會指示每一個並排顯示適當的地理位置的工作負載。OneDrive 並排顯示使用者的 OneDrive 文件庫裝載在哪裡，雖然 SharePoint 磚會指向 [所有使用者集中管理位置，為小組網站架設仍那里正確的地理位置的點。</span><span class="sxs-lookup"><span data-stu-id="16e0c-p104">The app launcher is Multi-Geo aware and will direct each tile to the appropriate geo location of the workload. The OneDrive tile points to the correct geo location where the user’s OneDrive library is hosted, while the SharePoint tile will point all users to the central location, as team sites are still hosted there.</span></span>

#### <a name="delve-user-profiles"></a><span data-ttu-id="16e0c-120">探索使用者設定檔</span><span class="sxs-lookup"><span data-stu-id="16e0c-120">Delve User profiles</span></span>

<span data-ttu-id="16e0c-p105">在使用者的地理位置對應使用者設定檔資訊。當選取的使用者，您會將您導向至適當的地理位置的使用者、 其中您會看到其完整的設定檔的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="16e0c-p105">User profile information is mastered in the user's geo location. When selecting a user, you will be directed to the appropriate geo location for the user, where you will see their full profile details.</span></span>

<span data-ttu-id="16e0c-123">如果 Delve 已關閉，您會看到傳統這不是多重地理注意體驗 SharePoint 中的設定檔。</span><span class="sxs-lookup"><span data-stu-id="16e0c-123">If Delve is turned off, you will see the classic profile experience in SharePoint, which is not multi-geo aware.</span></span>

#### <a name="delve"></a><span data-ttu-id="16e0c-124">Delve</span><span class="sxs-lookup"><span data-stu-id="16e0c-124">Delve</span></span>

<span data-ttu-id="16e0c-125">Office 365 使用者衛星執行個體中，探索多重地理位置支援，Delve 不會連結至 SharePoint 部落格文章只將其 SharePoint 部落格網站的其他區域的使用者所撰寫的限制。</span><span class="sxs-lookup"><span data-stu-id="16e0c-125">For Office 365 users who are in the satellite instances, Delve Multi-Geo is supported, with the limitation that Delve doesn’t link to SharePoint blog posts written by users in other regions, only to their SharePoint blog sites.</span></span>

#### <a name="search"></a><span data-ttu-id="16e0c-126">搜尋</span><span class="sxs-lookup"><span data-stu-id="16e0c-126">Search</span></span>

<span data-ttu-id="16e0c-p106">每個地理位置有其專屬的搜尋索引和搜尋中心。當使用者搜尋時、 查詢傳送給所有地理位置，並傳回的結果會合併並再排名讓使用者取得整合的結果。使用者從不論他們自己的地理位置的所有地理位置取得結果。請參閱[設定搜尋 OneDrive for Business 多-地理位置的](configure-search-for-multi-geo.md)特定資訊。</span><span class="sxs-lookup"><span data-stu-id="16e0c-p106">Each geo location has its own search index and Search Center. When a user searches, the query is sent to all the geo locations, and the returned results are merged and then ranked so the user gets unified results. Users get results from all geo locations regardless of their own geo location. See [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for specifics.</span></span>

<span data-ttu-id="16e0c-131">下列的搜尋用戶端可支援：</span><span class="sxs-lookup"><span data-stu-id="16e0c-131">The following search clients are supported:</span></span>

-   <span data-ttu-id="16e0c-132">商務用 OneDrive</span><span class="sxs-lookup"><span data-stu-id="16e0c-132">OneDrive for Business</span></span>

-   <span data-ttu-id="16e0c-133">Delve</span><span class="sxs-lookup"><span data-stu-id="16e0c-133">Delve</span></span>

-   <span data-ttu-id="16e0c-134">SharePoint 首頁</span><span class="sxs-lookup"><span data-stu-id="16e0c-134">SharePoint Home</span></span>

-   <span data-ttu-id="16e0c-135">搜尋中心</span><span class="sxs-lookup"><span data-stu-id="16e0c-135">The Search Center</span></span>

-   <span data-ttu-id="16e0c-136">使用 SharePoint 搜尋 API 的自訂搜尋應用程式</span><span class="sxs-lookup"><span data-stu-id="16e0c-136">Custom search applications that use the SharePoint Search API</span></span>

#### <a name="onedrive-ios-and-android"></a><span data-ttu-id="16e0c-137">OneDrive iOS 及 android （英文）</span><span class="sxs-lookup"><span data-stu-id="16e0c-137">OneDrive iOS and Android</span></span> 

<span data-ttu-id="16e0c-p107">OneDrive iOS 及 Android 行動應用程式將為您示範您 OneDrive 和不論其地理位置與您共用的檔案。從 OneDrive 行動應用程式的搜尋將會顯示來自所有地理位置相關的結果。請下載最新版的這些應用程式。</span><span class="sxs-lookup"><span data-stu-id="16e0c-p107">The OneDrive iOS and Android mobile apps will show you your OneDrive files and files shared with you regardless of their geo location. Search from the OneDrive mobile apps will show relevant results from all geo locations. Please download the latest version of these apps.</span></span>

<span data-ttu-id="16e0c-141">如需詳細資訊，請參閱使用[iOS 上的 OneDrive](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247)和[使用 OneDrive for android （英文)](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) 。</span><span class="sxs-lookup"><span data-stu-id="16e0c-141">See Use [OneDrive on iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) and [Use OneDrive for Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) for more information.</span></span>

#### <a name="teams-experience"></a><span data-ttu-id="16e0c-142">小組經驗</span><span class="sxs-lookup"><span data-stu-id="16e0c-142">Teams Experience</span></span>

<span data-ttu-id="16e0c-p108">小組是多重地理注意。不論使用者的地理位置顯示 OneDrive 檔案及最近檢視過的檔案。@ 提及來自所有地理位置的使用者使用。</span><span class="sxs-lookup"><span data-stu-id="16e0c-p108">Teams is multi-geo aware. OneDrive files and recently viewed files are shown regardless of the user’s geo location. @ mentions work with users from all geo-locations.</span></span>
