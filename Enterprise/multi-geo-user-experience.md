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
# <a name="user-experience-in-a-multi-geo-environment"></a>在多個地理位置環境中的使用者經驗

以下是您的使用者會看到 OneDrive 多重地理組態中：

#### <a name="users-onedrive-for-business-location"></a>使用者的 OneDrive for Business 位置

使用者會擁有其 OneDrive for Business 佈建在其偏好的資料位置。如果使用者瀏覽至包含不正確地理位置 （例如從先前的地理位置的書籤） OneDrive URL，其會自動重新導向至適當的地理位置中的 OneDrive。

#### <a name="sharing"></a>共用

人員選擇經驗顯示所有的使用者不論其地理位置。這可讓使用者在其相同的地理位置或其他任何您的租用戶地理位置的共用與另一位使用者。不同地理位置會檢視中顯示**與我共用**使用者的 onedrive for Business 和可以存取與單一登入經驗的地理位置不論它裝載於中的內容。

#### <a name="office-applications"></a>Office 應用程式

如 Word、 Excel 及 PowerPoint 的 office 應用程式將自動會偵測正確 OneDrive for Business 地理位置的每位使用者登入。使用者不需要輸入其 OneDrive 的特定地理位置的 URL。

#### <a name="onedrive-for-business-sync-client"></a>OneDrive for Business Sync 用戶端

OneDrive for Business Sync 用戶端 (版本 17.3.6943.0625 及更新版本) 將會自動偵測正確 OneDrive for Business 地理位置的使用者。

#### <a name="office-365-app-launcher"></a>Office 365 應用程式啟動器

應用程式啟動器是多重地理注意，會指示每一個並排顯示適當的地理位置的工作負載。OneDrive 並排顯示使用者的 OneDrive 文件庫裝載在哪裡，雖然 SharePoint 磚會指向 [所有使用者集中管理位置，為小組網站架設仍那里正確的地理位置的點。

#### <a name="delve-user-profiles"></a>探索使用者設定檔

在使用者的地理位置對應使用者設定檔資訊。當選取的使用者，您會將您導向至適當的地理位置的使用者、 其中您會看到其完整的設定檔的詳細資訊。

如果 Delve 已關閉，您會看到傳統這不是多重地理注意體驗 SharePoint 中的設定檔。

#### <a name="delve"></a>Delve

Office 365 使用者衛星執行個體中，探索多重地理位置支援，Delve 不會連結至 SharePoint 部落格文章只將其 SharePoint 部落格網站的其他區域的使用者所撰寫的限制。

#### <a name="search"></a>搜尋

每個地理位置有其專屬的搜尋索引和搜尋中心。當使用者搜尋時、 查詢傳送給所有地理位置，並傳回的結果會合併並再排名讓使用者取得整合的結果。使用者從不論他們自己的地理位置的所有地理位置取得結果。請參閱[設定搜尋 OneDrive for Business 多-地理位置的](configure-search-for-multi-geo.md)特定資訊。

下列的搜尋用戶端可支援：

-   商務用 OneDrive

-   Delve

-   SharePoint 首頁

-   搜尋中心

-   使用 SharePoint 搜尋 API 的自訂搜尋應用程式

#### <a name="onedrive-ios-and-android"></a>OneDrive iOS 及 android （英文） 

OneDrive iOS 及 Android 行動應用程式將為您示範您 OneDrive 和不論其地理位置與您共用的檔案。從 OneDrive 行動應用程式的搜尋將會顯示來自所有地理位置相關的結果。請下載最新版的這些應用程式。

如需詳細資訊，請參閱使用[iOS 上的 OneDrive](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247)和[使用 OneDrive for android （英文)](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) 。

#### <a name="teams-experience"></a>小組經驗

小組是多重地理注意。不論使用者的地理位置顯示 OneDrive 檔案及最近檢視過的檔案。@ 提及來自所有地理位置的使用者使用。
