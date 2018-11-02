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
ms.openlocfilehash: 951efb636ce00f59393f624687d44a406fcf3fc0
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849829"
---
# <a name="user-experience-in-a-multi-geo-environment"></a>在多地理位置環境中的使用者體驗

以下是您的使用者在 OneDrive 多地理位置組態中看到的項目：

#### <a name="users-onedrive-for-business-location"></a>使用者的商務用 OneDrive 位置

使用者會將其商務用 OneDrive 佈建在其慣用的資料位置。如果使用者瀏覽至包含不正確地理位置的 OneDrive URL (例如從先前地理位置的書籤)，系統就會將他們自動重新導向至適當地理位置中的 OneDrive。

#### <a name="sharing"></a>共用

人員選擇器體驗會顯示所有使用者 (不論其地理位置為何)。這可讓使用者與在其相同地理位置或在任何其他租用戶之地理位置的其他使用者共用。來自不同地理位置的內容會顯示在使用者商務用 OneDrive 中 [**與我共用**] 檢視中，並可透過單一登入體驗來存取 (無論其在哪一個地理位置受到主控)。

#### <a name="office-applications"></a>Office 應用程式

Office 應用程式 (例如 Word、 Excel 及 PowerPoint) 會在每個使用者登入時，自動為他們偵測正確的商務用 OneDrive 地理位置。使用者不需要輸入 OneDrive 的特定地理位置 URL。

#### <a name="onedrive-for-business-sync-client"></a>商務用 OneDrive 同步處理用戶端

商務用 OneDrive 同步處理用戶端 (版本 17.3.6943.0625 和更新版本) 將會自動偵測該使用者的正確商務用 OneDrive 地理位置。

#### <a name="office-365-app-launcher"></a>Office 365 應用程式啟動器

應用程式啟動器是具多地理位置意識的，且會將每個圖標導向至工作負載的適當地理位置。OneDrive 圖標指向該使用者 OneDrive 文件庫主控所在的正確地理位置，而 SharePoint 圖標會將所有使用者指向中央位置，因為小組網站仍在該處進行主控。

#### <a name="delve-user-profiles"></a>Delve 使用者設定檔

系統會在使用者地理位置中管理使用者的設定檔資訊。選取使用者時，系統會將您導向至使用者的適當地理位置，您在其中可看到他們完整的設定檔詳細資料。

如果將 Delve 關閉，您會在 SharePoint 中看到傳統設定檔經驗，這並不具備地理位置意識。

#### <a name="delve"></a>Delve

針對在衛星情況下的 Office 365 使用者，Delve 多地理位置是受到支援的，但具有以下限制：Delve 不會連結至使用者在其他區域中撰寫的 SharePoint 部落格文章，僅會連結至他們的 SharePoint 部落格網站。

#### <a name="search"></a>搜尋

每個地理位置有其專屬的搜尋索引和搜尋中心。當使用者搜尋時，系統會將查詢傳送給所有的地理位置，且傳回的結果會經過合併並加以排名，讓使用者獲得一致的結果。使用者會取得來自所有地理位置的結果 (無論他們自身的地理位置為何)。請參閱[設定適用於商務用 OneDrive 多地理位置的搜尋](configure-search-for-multi-geo.md)以了解詳細資訊。

支援以下搜尋用戶端：

-   商務用 OneDrive

-   Delve

-   SharePoint 首頁

-   搜尋中心

-   會使用 SharePoint 搜尋 API 的自訂搜尋應用程式

#### <a name="onedrive-ios-and-android"></a>OneDrive iOS 和 Android 

OneDrive iOS 和 Android 的行動裝置應用程式會顯示您的 OneDrive 檔案及與您共用的檔案 (無論其地理位置為何)。透過 OneDrive 行動裝置應用程式的搜尋會顯示來自所有地理位置的相關結果。請下載這些應用程式的最新版本。

請參閱使用「[在 iOS 上的 OneDrive](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247)」和「[使用適用於 Android 的 OneDrive](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36)」以了解詳細資訊。

#### <a name="teams-experience"></a>小組體驗

小組是具備多地理位置意識的。無論使用者的地理位置為何，系統都會顯示 OneDrive 檔案及最近檢視過的檔案。@ 提及與來自所有地理位置使用者合作的工作。
