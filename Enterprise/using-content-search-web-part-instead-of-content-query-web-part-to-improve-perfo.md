---
title: 使用內容搜尋網頁組件而不內容查詢網頁組件，來改善 SharePoint Online 中的效能
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: e8ce6b72-745b-464a-85c7-cbf6eb53391b
description: 本文說明如何取代內容搜尋網頁組件，SharePoint Server 2013 和 SharePoint Online 中的 「 內容查詢網頁組件以提升效能。
ms.openlocfilehash: 590cd5f60dedf870d58d053b01e4e1b45469bfa4
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070549"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a>使用內容搜尋網頁組件而不內容查詢網頁組件，來改善 SharePoint Online 中的效能

本文說明如何取代內容搜尋網頁組件，SharePoint Server 2013 和 SharePoint Online 中的 「 內容查詢網頁組件以提升效能。
  
SharePoint Server 2013 和 SharePoint Online 的最強大的新功能之一是內容搜尋網頁組件 (CSWP)。 此網頁組件會使用搜尋索引來快速地擷取向使用者顯示的結果。 用於內容搜尋網頁組件而不是內容查詢網頁組件 (CQWP) 頁面中的使用者提升效能。
  
透過 「 內容查詢網頁組件使用內容搜尋網頁組件會幾乎總是導致 SharePoint Online 上的大幅改善頁面載入效能。 沒有少許額外的設定，以取得正確的查詢，卻報酬改善的效能和滿足使用者。
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a>比較，就無法使用內容搜尋網頁組件，而不內容查詢網頁組件的效能提升

下列範例顯示當您使用內容搜尋網頁組件而不是 「 內容查詢網頁組件時，您可能會收到相對的效能提升。 效果會更明顯的複雜網站結構與非常廣泛的內容查詢。
  
此範例網站具有下列特性：
  
- 8 層級的子網站。
    
- 列出使用自訂 「 水果 」 內容類型。
    
- 在 [網頁組件內容查詢是廣泛，傳回與 「 水果 」 內容類型的所有項目。
    
- 此範例只會使用 50 項目 8 網站之間。 效果，將會更為明顯的網站具有更多的內容之用。
    
以下是 「 內容查詢網頁組件的結果的螢幕擷取畫面。
  
![顯示網頁組件內容查詢的圖形](media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
在 Internet Explorer 中，使用 F12 開發人員工具的 [**網路**] 索引標籤，查看回應標頭的詳細資料。 下列螢幕擷取畫面中，載入此頁面**SPRequestDuration**的值會是 924 毫秒。 
  
![顯示 924 要求期間的螢幕擷取畫面](media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 **SPRequestDuration**指出準備網頁伺服器上完成的工作數量。 切換使用內容搜尋網頁組件內容查詢網頁組件可大幅減少轉譯] 頁面上所花費的時間。 相較之下，對等的內容搜尋網頁組件] 頁面上，傳回相同的結果數目具有**SPRequestDuration**值的 106 毫秒這個螢幕擷取畫面所示： 
  
![顯示 106 要求期間的螢幕擷取畫面](media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a>新增內容搜尋網頁組件中 SharePoint Online

新增內容搜尋網頁組件是非常類似於一般的內容查詢網頁組件。 請參閱[設定內容搜尋網頁組件 SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a)中的 *「 新增內容搜尋網頁組件 」* 一節。
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a>建立正確的搜尋查詢的內容搜尋網頁組件

一旦您已新增內容搜尋網頁組件，您可以縮小搜尋範圍，並傳回您想要的項目。 如需如何執行這項操作的詳細指示，請參閱 <] 區段中，<b1>設定在 SharePoint 中的內容搜尋網頁組件</b1>中的<b0>「 藉由設定內容搜尋網頁組件中的進階的查詢顯示內容 」</b0> 。
  
## <a name="query-building-and-testing-tool"></a>查詢建置和測試工具

一套工具來建置和測試複雜的查詢，請參閱 Codeplex 上的[搜尋查詢工具](https://sp2013searchtool.codeplex.com/)。 
  

