---
title: SharePoint Online 效能調整的簡介
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/22/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 81c4be5f-327e-435d-a568-526d68cffef0
description: 本文將告訴您需要考慮當設計的 SharePoint Online 中的最佳效能頁面的特定事項。
ms.openlocfilehash: 07938770d711477126f78fc583e8d2533ba5c1d1
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487155"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a>SharePoint Online 效能調整的簡介

本文將告訴您需要考慮當設計的 SharePoint Online 中的最佳效能頁面的特定事項。
     
## <a name="sharepoint-online-metrics"></a>SharePoint Online 度量資訊

SharePoint online 的廣泛計量提供有關效能的實際環境資料：
  
- 頁面載入速度
    
- 每頁所需來回行程次數
    
- 服務的問題
    
- 會導致效能降低的其他事項
    
### <a name="conclusions-reached-because-of-the-data"></a>結論資料

資料會告訴我們：
  
- 大部分頁面以及 SharePoint Online 上執行。
    
- 非自訂頁面載入速度很快。
    
- 商務用 OneDrive、 小組網站和系統頁面，例如 _layouts 等是所有快速載入。
    
- 速度最慢的 1%SharePoint Online 頁面需要載入超過 5000 毫秒。
    
您可以使用一個簡單的基準測試是測量效能藉由比較針對商務首頁 OneDrive 的載入時間自己入口網站的載入時間，因為它會使用幾個自訂的功能。 這通常是支援會要求您完成疑難排解網路效能問題時的第一個步驟。
  
## <a name="use-a-standard-user-account-when-checking-performance"></a>檢查效能時，使用標準的使用者帳戶

網站集合管理員、 網站擁有人、 編輯器或參與者隸屬於其他安全性群組，具有其他權限，因此 SharePoint 載入頁面的其他項目。
  
這是適用於 SharePoint 內部部署和 SharePoint Online，但在內部部署案例差異便不會為輕鬆地發現如 SharePoint Online 所示。
  
才能正確地評估的使用者] 頁面上會執行方式，您應該使用標準的使用者帳戶，以避免載入安全性群組與相關的其他流量與製作的控制項。
  
## <a name="connection-categories-for-performance-tuning"></a>效能調整的連線類別

您可以將伺服器和使用者之間的連線到三個主要元件加以分類。 設計 SharePoint Online 的深入的頁面載入時間時，請考慮這些選項。
  
- **伺服器**Microsoft 會代管的資料中心伺服器。
    
- **網路**Microsoft 網路、 網際網路及您的內部網路之間的資料中心和您的使用者。
    
- **瀏覽器**其中載入頁面。
    
下列三個連線有通常會導致 95%的速度很慢的頁面的五個原因。 本文將討論每個這些原因是：
  
- 瀏覽問題
    
- 內容彙總
    
- 大型檔案
    
- 伺服器的要求太多
    
- 網頁組件處理
    
### <a name="server-connection"></a>伺服器連線

許多影響 SharePoint 內部部署效能的問題也適用於 SharePoint Online。
  
如您所預期，您會有更多控制權伺服器如何執行與內部部署 SharePoint。 使用 SharePoint Online 事項會稍微不同。 多工作您，讓伺服器執行的時間就越長轉譯頁面。 SharePoint 中，在這方面的最大發生錯誤之有複雜的頁面，具有多個網頁組件。
  
SharePoint Server 內部部署
  
![內部部署伺服器的螢幕擷取畫面](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
SharePoint Online
  
![伺服器連線的螢幕擷取畫面](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
使用 SharePoint Online，某些頁面要求可能會實際最後呼叫多部伺服器。 您無法結尾的個別要求的伺服器之間的要求矩陣。 這些互動從] 頁面上的負載觀點昂貴且會讓事情變慢。
  
這些伺服器對伺服器互動的範例如下：
  
- Web 對 SQL Server
    
- Web 對應用程式伺服器
    
可以減慢伺服器互動的其他一件事是快取遺漏。 不同內部部署 SharePoint，沒有就會叫用相同的伺服器] 頁面上，瀏覽過先前; 非常輕型機率這會讓物件快取已過時。
  
### <a name="network-connection"></a>網路連線

不會讓使用 WAN 的內部部署 sharepoint，您可以使用資料中心與使用者之間的高速連線。 一般而言，項目皆可輕鬆地從網路的觀點來管理。
  
使用 SharePoint Online，有幾個因素考慮;例如：
  
- Microsoft 網路
    
- 網際網路
    
- ISP
    
不論哪一個版本的 SharePoint （和那個網路） 使用，通常會導致網路忙碌的時間，包括：
  
- 承載過大
    
- 許多檔案
    
- 伺服器的實體距離太
    
您可以利用 SharePoint Online 中的一項功能是 Microsoft CDN 內容傳遞網路 （）。 CDN 基本上是跨多個資料中心部署的伺服器的分散式的集合。 使用 CDN，頁面上的內容可以主控接近用戶端伺服器上即使用戶端是遠從原始的 SharePoint Server。 Microsoft 會使用此多未來要儲存的頁面無法加以自訂，例如 SharePoint Online 的系統管理首頁上的本機執行個體。 如需 Cdn 的詳細資訊，請參閱 <<c0>內容傳遞網路。
  
您需要知悉的但不是能執行許多動作相關的內容是您的 ISP 的連線速度。 簡單的速度測試工具會告訴您的連線速度。
  
### <a name="browser-connection"></a>瀏覽器連線

有幾個因素来考慮使用網頁瀏覽器效能的觀點而言。
  
造訪複雜的頁面會影響效能。 大部分的瀏覽器只需要使用小型的快取 (大約 90 MB)，同時平均網頁通常是大約 1.6 MB。 這不會採取長，取得用於。
  
頻寬可能也會發生問題。 例如，如果使用者觀賞影片，另一個工作階段中，這會影響您的 SharePoint 網頁的效能。 雖然您無法防止使用者媒體資料流，您可以控制使用者會載入頁面的方式。
  
請參閱以下文章中的不同的 SharePoint Online 頁面自訂技術和其他最佳作法，以協助您達到最佳效能。
  
- [SharePoint Online 的導覽選項](navigation-options-for-sharepoint-online.md)
    
- [使用 SharePoint Online 頁面診斷工具](page-diagnostics-for-spo.md)
    
- [SharePoint Online 的影像最佳化](image-optimization-for-sharepoint-online.md)
    
- [延遲載入 SharePoint Online 中的影像和 JavaScript](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [縮製及統合在 SharePoint Online](minification-and-bundling-in-sharepoint-online.md)
    
- [使用內容傳遞網路](using-content-delivery-networks-with-sharepoint-online.md)
    
- [使用內容搜尋網頁組件而不內容查詢網頁組件，來改善 SharePoint Online 中的效能](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [容量規劃和負載測試 SharePoint Online](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [診斷 SharePoint Online 的效能問題](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [使用 SharePoint Online 的物件快取](using-the-object-cache-with-sharepoint-online.md)
    
- [操作方法：如何避免在 SharePoint Online 中受到節流控制或封鎖](https://msdn.microsoft.com/en-us/library/office/dn889829.aspx)
    

