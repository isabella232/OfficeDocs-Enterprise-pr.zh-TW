---
title: 在多地理位置環境中的使用者體驗
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 深入了解多地理位置環境中 SharePoint 和 OneDrive 使用者經驗。
ms.openlocfilehash: 3c7e4b6802bddc78db016c9c282f5add0c71c491
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="user-experience-in-a-multi-geo-environment"></a><span data-ttu-id="8c22c-103">在多地理位置環境中的使用者體驗</span><span class="sxs-lookup"><span data-stu-id="8c22c-103">User experience in a multi-geo environment</span></span>

<span data-ttu-id="8c22c-104">以下是您的使用者在 OneDrive 多地理位置組態中看到的項目：</span><span class="sxs-lookup"><span data-stu-id="8c22c-104">Here’s what your users will see in a OneDrive Multi-Geo configuration:</span></span>

#### <a name="users-onedrive-for-business-location"></a><span data-ttu-id="8c22c-105">使用者的商務用 OneDrive 位置</span><span class="sxs-lookup"><span data-stu-id="8c22c-105">User’s OneDrive for Business location</span></span>

<span data-ttu-id="8c22c-p101">使用者會將其商務用 OneDrive 佈建在其慣用的資料位置。如果使用者瀏覽至包含不正確地理位置的 OneDrive URL (例如從先前地理位置的書籤)，系統就會將他們自動重新導向至適當地理位置中的 OneDrive。</span><span class="sxs-lookup"><span data-stu-id="8c22c-p101">Users will have their OneDrive for Business provisioned in their preferred data location. If a user navigates to a OneDrive URL that contains an incorrect geo-location (such as a bookmark from a previous geo-location), they are automatically redirected to the OneDrive in the appropriate geo-location.</span></span>

#### <a name="sharing"></a><span data-ttu-id="8c22c-108">共用</span><span class="sxs-lookup"><span data-stu-id="8c22c-108">Sharing</span></span>

<span data-ttu-id="8c22c-p102">人員選擇器體驗會顯示所有使用者 (不論其地理位置為何)。這可讓使用者與在其相同地理位置或在任何其他租用戶之地理位置的其他使用者共用。來自不同地理位置的內容會顯示在使用者商務用 OneDrive 中 [與我共用]**** 檢視中，並可透過單一登入體驗來存取 (無論其在哪一個地理位置受到主控)。</span><span class="sxs-lookup"><span data-stu-id="8c22c-p102">The People Picker experience shows all users regardless of their geo location. This allows a user to share with another user in their same geo or in any other of your tenant’s geo locations. Content from different geo locations will show up in the **Shared with Me** view in the user's OneDrive for Business and can be accessed with Single-Sign-On experience regardless of which geo-location it is hosted in.</span></span>

#### <a name="office-applications"></a><span data-ttu-id="8c22c-112">Office 應用程式</span><span class="sxs-lookup"><span data-stu-id="8c22c-112">Office applications</span></span>

<span data-ttu-id="8c22c-p103">Office 應用程式 (例如 Word、 Excel 及 PowerPoint) 會在每個使用者登入時，自動為他們偵測正確的商務用 OneDrive 地理位置。使用者不需要輸入 OneDrive 的特定地理位置 URL。</span><span class="sxs-lookup"><span data-stu-id="8c22c-p103">Office applications such as Word, Excel, and PowerPoint will automatically detect the correct OneDrive for Business geo-location for each user when they log in. Users do not need to enter the geo-specific URL for their OneDrive.</span></span>

#### <a name="onedrive-for-business-sync-client"></a><span data-ttu-id="8c22c-115">商務用 OneDrive 同步處理用戶端</span><span class="sxs-lookup"><span data-stu-id="8c22c-115">OneDrive for Business Windows Sync client</span></span>

<span data-ttu-id="8c22c-116">商務用 OneDrive 同步處理用戶端 (版本 17.3.6943.0625 和更新版本) 將會自動偵測該使用者的正確商務用 OneDrive 地理位置。</span><span class="sxs-lookup"><span data-stu-id="8c22c-116">The OneDrive for Business Sync Client (version 17.3.6943.0625 and later) will automatically detect the correct OneDrive for Business geo location for the user.</span></span>

#### <a name="office-365-app-launcher"></a><span data-ttu-id="8c22c-117">Office 365 應用程式啟動器</span><span class="sxs-lookup"><span data-stu-id="8c22c-117">Office 365 app launcher</span></span>

<span data-ttu-id="8c22c-p104">應用程式啟動器是具多地理位置意識的，且會將每個圖標導向至工作負載的適當地理位置。OneDrive 圖標指向該使用者 OneDrive 文件庫主控所在的正確地理位置，而 SharePoint 圖標會將所有使用者指向中央位置，因為小組網站仍在該處進行主控。</span><span class="sxs-lookup"><span data-stu-id="8c22c-p104">The app launcher is Multi-Geo aware and will direct each tile to the appropriate geo location of the workload. The OneDrive tile points to the correct geo location where the user’s OneDrive library is hosted, while the SharePoint tile will point all users to the central location, as team sites are still hosted there.</span></span>

#### <a name="delve-user-profiles"></a><span data-ttu-id="8c22c-120">Delve 使用者設定檔</span><span class="sxs-lookup"><span data-stu-id="8c22c-120">Delve User profiles</span></span>

<span data-ttu-id="8c22c-p105">系統會在使用者地理位置中管理使用者的設定檔資訊。選取使用者時，系統會將您導向至使用者的適當地理位置，您在其中可看到他們完整的設定檔詳細資料。</span><span class="sxs-lookup"><span data-stu-id="8c22c-p105">User profile information is mastered in the user's geo location. When selecting a user, you will be directed to the appropriate geo location for the user, where you will see their full profile details.</span></span>

<span data-ttu-id="8c22c-123">如果將 Delve 關閉，您會在 SharePoint 中看到傳統設定檔經驗，這並不具備地理位置意識。</span><span class="sxs-lookup"><span data-stu-id="8c22c-123">If Delve is turned off, you will see the classic profile experience in SharePoint, which is not multi-geo aware.</span></span>

#### <a name="delve"></a><span data-ttu-id="8c22c-124">Delve</span><span class="sxs-lookup"><span data-stu-id="8c22c-124">Delve</span></span>

<span data-ttu-id="8c22c-125">針對在衛星情況下的 Office 365 使用者，Delve 多地理位置是受到支援的，但具有以下限制：Delve 不會連結至使用者在其他區域中撰寫的 SharePoint 部落格文章，僅會連結至他們的 SharePoint 部落格網站。</span><span class="sxs-lookup"><span data-stu-id="8c22c-125">For Office 365 users who are in the satellite instances, Delve Multi-Geo is supported, with the limitation that Delve doesn’t link to SharePoint blog posts written by users in other regions, only to their SharePoint blog sites.</span></span>

#### <a name="search"></a><span data-ttu-id="8c22c-126">搜尋</span><span class="sxs-lookup"><span data-stu-id="8c22c-126">Search</span></span>

<span data-ttu-id="8c22c-p106">每個地理位置有其專屬的搜尋索引和搜尋中心。當使用者搜尋時，系統會將查詢傳送給所有的地理位置，且傳回的結果會經過合併並加以排名，讓使用者獲得一致的結果。使用者會取得來自所有地理位置的結果 (無論他們自身的地理位置為何)。請參閱[設定適用於商務用 OneDrive 多地理位置的搜尋](configure-search-for-multi-geo.md)以了解詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="8c22c-p106">Each geo location has its own search index and Search Center. When a user searches, the query is sent to all the geo locations, and the returned results are merged and then ranked so the user gets unified results. Users get results from all geo locations regardless of their own geo location. See [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for specifics.</span></span>

<span data-ttu-id="8c22c-131">支援以下搜尋用戶端：</span><span class="sxs-lookup"><span data-stu-id="8c22c-131">The following search clients are supported:</span></span>

-   <span data-ttu-id="8c22c-132">商務用 OneDrive</span><span class="sxs-lookup"><span data-stu-id="8c22c-132">OneDrive for Business</span></span>

-   <span data-ttu-id="8c22c-133">Delve</span><span class="sxs-lookup"><span data-stu-id="8c22c-133">Delve</span></span>

-   <span data-ttu-id="8c22c-134">SharePoint 首頁</span><span class="sxs-lookup"><span data-stu-id="8c22c-134">SharePoint Home</span></span>

-   <span data-ttu-id="8c22c-135">搜尋中心</span><span class="sxs-lookup"><span data-stu-id="8c22c-135">The Search Center</span></span>

-   <span data-ttu-id="8c22c-136">會使用 SharePoint 搜尋 API 的自訂搜尋應用程式</span><span class="sxs-lookup"><span data-stu-id="8c22c-136">Custom search applications that use the SharePoint Search API</span></span>

#### <a name="onedrive-ios-and-android"></a><span data-ttu-id="8c22c-137">OneDrive iOS 和 Android</span><span class="sxs-lookup"><span data-stu-id="8c22c-137">OneDrive iOS and Android</span></span> 

<span data-ttu-id="8c22c-p107">OneDrive iOS 和 Android 的行動裝置應用程式會顯示您的 OneDrive 檔案及與您共用的檔案 (無論其地理位置為何)。透過 OneDrive 行動裝置應用程式的搜尋會顯示來自所有地理位置的相關結果。請下載這些應用程式的最新版本。</span><span class="sxs-lookup"><span data-stu-id="8c22c-p107">The OneDrive iOS and Android mobile apps will show you your OneDrive files and files shared with you regardless of their geo location. Search from the OneDrive mobile apps will show relevant results from all geo locations. Please download the latest version of these apps.</span></span>

<span data-ttu-id="8c22c-141">請參閱使用「[在 iOS 上的 OneDrive](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247)」和「[使用適用於 Android 的 OneDrive](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36)」以了解詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="8c22c-141">See Use [OneDrive on iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) and [Use OneDrive for Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) for more information.</span></span>

#### <a name="teams-experience"></a><span data-ttu-id="8c22c-142">小組體驗</span><span class="sxs-lookup"><span data-stu-id="8c22c-142">Teams Experience</span></span>

<span data-ttu-id="8c22c-p108">小組是具備多地理位置意識的。無論使用者的地理位置為何，系統都會顯示 OneDrive 檔案及最近檢視過的檔案。@ 提及與來自所有地理位置使用者合作的工作。</span><span class="sxs-lookup"><span data-stu-id="8c22c-p108">Teams is multi-geo aware. OneDrive files and recently viewed files are shown regardless of the user’s geo location. @ mentions work with users from all geo-locations.</span></span>
