---
title: 使用 SharePoint Online 的物件快取
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/20/2015
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 38bc9c14-3826-449c-beb6-b1003bcbeaaf
description: 本文說明使用物件快取 SharePoint Server 2013 內部部署和 SharePoint Online 中的差異。
ms.openlocfilehash: 4c6cd225bf0f7324dcb23c55adb87e2365d35472
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2019
ms.locfileid: "38078022"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a>使用 SharePoint Online 的物件快取

本文說明使用物件快取 SharePoint Server 2013 內部部署和 SharePoint Online 中的差異。
  
沒有顯著的依賴物件快取中 SharePoint Online 部署的負面影響。 在 SharePoint Online 中的物件快取上任何相依性可減少您] 頁面上的可靠性。 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a>如何在 SharePoint Online 和 SharePoint Server 2013 物件快取運作

主控的內部部署 SharePoint Server 2013 時，客戶可以主控物件快取的專用的前端網頁伺服器。 這表示快取專用於一位客戶，而且僅受限於多少記憶體可供使用且配置的物件快取。 因為只有一個客戶提供內部部署案例中前端網頁伺服器通常會有重複提出要求同一個網站的使用者。 這表示快取完整快速取得並保持完整的清單查詢結果和您的使用者要求以規則為基礎的 SharePoint 物件。
  
![顯示到內部部署前端網頁伺服器的流量和負載](media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
因此，使用者造訪] 頁面上，第二次頁面載入時間可改善。 之後的四種負載相同頁面的最低限度下，是快取在所有前端網頁伺服器上的網頁。
  
相反地，在 SharePoint Online 中有更多伺服器，但也很多的多個網站。 每個使用者可能連接至沒有填入快取的其他前端網頁伺服器。 或者，或許快取未填入伺服器，但的下一個使用者] 頁面上的該前端網頁伺服器要求從不同的站台。 或者，即使下一個使用者在其上一個瀏覽上要求同一個頁面，其快取中沒有該頁面的不同的前端網頁伺服器負載平衡。 在最後一個案例中，快取不會協助使用者在所有。
  
在下圖中，每個點會代表] 頁面上的使用者要求該快取的位置。 不同顏色表示不同的客戶共用用法的 SaaS 基礎結構。
  
![顯示 SharePoint Online 中的物件快取結果](media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
您可以看到從圖表，是輕型達到次具有其] 頁面上的快取版本的伺服器的任何特定使用者的機會。 此外，由於大型輸送量與伺服器會在多個網站之間共用的事實，快取不會姓氏 long 因為沒有可用的僅限說空間來快取。
  
對於所有的這些原因，依賴使用者取得快取的物件不是有效的方法，以確保良好使用者經驗和頁面載入 SharePoint Online 中的時間。
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a>如果我們無法依賴物件快取以改善 SharePoint Online 中的效能，我們該用什麼改為？

因為您不應該依賴 SharePoint Online 中快取，您應該評估使用物件快取的 SharePoint 自訂的替代設計方法。 這表示效能問題，請勿依賴物件快取才能產生良好結果提供給使用者的使用方式。 這部分本系列中的其他文章所述，包括：
  
- [SharePoint Online 的瀏覽選項](navigation-options-for-sharepoint-online.md)
    
- [SharePoint Online 中的縮製和統合](minification-and-bundling-in-sharepoint-online.md)
    
- [使用內容傳遞網路](using-content-delivery-networks-with-sharepoint-online.md)
    
- [在 SharePoint Online 中延遲載入圖片與 JavaScript](delay-loading-images-and-javascript-in-sharepoint-online.md)
    

