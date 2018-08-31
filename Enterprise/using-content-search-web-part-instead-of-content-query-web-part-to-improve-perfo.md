---
title: 使用，而不內容查詢網頁組件的內容搜尋網頁組件來增進效能的 SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: e8ce6b72-745b-464a-85c7-cbf6eb53391b
description: 本文說明如何在 SharePoint Server 2013 和 SharePoint Online 內容搜尋網頁組件以取代 「 內容查詢網頁組件以提升效能。
ms.openlocfilehash: f86a4b75c4bf75ebaa99924411d017c7eb7b6760
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540247"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a>使用，而不內容查詢網頁組件的內容搜尋網頁組件來增進效能的 SharePoint Online

本文說明如何在 SharePoint Server 2013 和 SharePoint Online 內容搜尋網頁組件以取代 「 內容查詢網頁組件以提升效能。
  
其中一個最強大的新功能的 SharePoint Server 2013 和 SharePoint Online 是內容搜尋網頁組件 (CSWP)。此網頁組件會使用搜尋索引快速地擷取會向使用者顯示的結果。用於內容搜尋網頁組件，而不是內容查詢網頁組件 (CQWP) 頁面中的使用者提升效能。
  
透過 「 內容查詢網頁組件中使用 「 內容搜尋網頁組件幾乎一定會產生大幅改善 SharePoint Online 上的頁面負載效能。有一點的其他設定即可使用取得正確的查詢，但獎賞改善的效能而且滿足使用者。
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a>比較您取得無法使用內容搜尋網頁組件而不內容查詢網頁組件的效能提升

下列範例顯示當您使用 「 內容搜尋網頁組件而不是 「 內容查詢網頁組件可能會收到相對的效能提升。效果會更明顯與複雜的網站結構和非常廣泛的內容查詢。
  
此範例網站都具有下列特性：
  
- 8 的層級的子網站。
    
- 列出使用自訂"水果 」 內容類型。
    
- 在 [網頁組件中的內容查詢是廣泛，傳回所有的項目與"水果 」 內容類型。
    
- 範例只會使用 8 網站之間的 50 項目。效果會為更為明顯的網站具有多個內容之用。
    
以下是內容查詢網頁組件的結果的螢幕擷取畫面。
  
![顯示網頁組件內容查詢的圖形](media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
在 Internet Explorer 中，使用 F12 開發人員工具的 [**網路**] 索引標籤來查看回應標頭的詳細資料。下列螢幕擷取畫面中，載入此頁面**SPRequestDuration**的值會是 924 （毫秒）。 
  
![顯示 924 要求期間的螢幕擷取畫面](media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 **SPRequestDuration**表示要準備] 頁面上的伺服器上的已完成的工作數量。切換內容搜尋網頁組件的內容查詢網頁組件可大幅減少轉譯頁面所花費的時間。相較之下，對等的內容搜尋網頁組件] 頁面上，傳回相同的結果數具有 106 （毫秒） 此螢幕擷取畫面所示的**SPRequestDuration**值： 
  
![顯示 106 要求期間的螢幕擷取畫面](media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a>新增內容搜尋網頁組件在 SharePoint Online

新增內容搜尋網頁組件是非常類似於在規則的內容查詢網頁組件。請參閱] 區段中[設定內容搜尋網頁組件在 SharePoint 中](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a)的 *「 新增內容搜尋網頁組件 」* 。
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a>建立正確的搜尋查詢的內容搜尋網頁組件

一旦您已經新增內容搜尋網頁組件，您可精簡搜尋及傳回您想要的項目。如需如何執行這項作業的詳細指示，請參閱] 區段中，[設定內容搜尋網頁組件在 SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a)中的 *「 設定內容搜尋網頁組件的進階的查詢顯示內容 」* 。
  
## <a name="query-building-and-testing-tool"></a>查詢建立及測試工具

建立及測試複雜查詢工具，請參閱 Codeplex 上的[搜尋查詢工具](https://sp2013searchtool.codeplex.com/)。 
  

