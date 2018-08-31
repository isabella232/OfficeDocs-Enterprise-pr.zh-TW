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
description: 本文說明設計的 SharePoint Online 中的最佳效能頁面時需要考量您需要何種特定部分。
ms.openlocfilehash: 96aeec19a6b582d0dc8701cd2e99329ec8ce156b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539937"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a>SharePoint Online 效能調整的簡介

本文說明設計的 SharePoint Online 中的最佳效能頁面時需要考量您需要何種特定部分。
  
## <a name="in-this-article"></a>本文內容

- [SharePoint Online 的評量](introduction-to-performance-tuning-for-sharepoint-online.md#spometrics)和[結論達到因為資料](introduction-to-performance-tuning-for-sharepoint-online.md#data)
    
- [檢查效能時使用的標準使用者帳戶](introduction-to-performance-tuning-for-sharepoint-online.md#standuser)
    
- [連線類別的效能調整](introduction-to-performance-tuning-for-sharepoint-online.md#connect)：[伺服器的連線](introduction-to-performance-tuning-for-sharepoint-online.md#server)、[網路連線](introduction-to-performance-tuning-for-sharepoint-online.md#network)和[瀏覽器連線](introduction-to-performance-tuning-for-sharepoint-online.md#browser)
    
## <a name="sharepoint-online-metrics"></a>SharePoint Online 度量資訊
<a name="spometrics"> </a>

下列廣泛的 SharePoint Online 度量值提供有關效能的實際環境資料：
  
- 頁面載入速度
    
- 每頁所需來回行程次數
    
- 服務的問題
    
- 導致效能降低的其他事項
    
### <a name="conclusions-reached-because-of-the-data"></a>資料所導出的結論
<a name="data"> </a>

資料會告訴我們：
  
- 大部分頁面在 SharePoint Online 上的執行狀況良好。
    
- 非自訂頁面載入速度很快。
    
- 商務用 OneDrive、小組網站和系統頁面 (如 _layouts 等) 載入速度都很快。
    
- 最慢的 1% SharePoint Online 頁面載入時間需要超過 5000 毫秒。
    
您可使用的一項簡單基準測試是透過比較您的入口網站載入時間和商務用 OneDrive 首頁載入時間來測量效能，因其使用的自訂功能不多。在進行網路效能問題疑難排解時，這通常是支援人員要求您完成的第一個步驟。
  
## <a name="use-a-standard-user-account-when-checking-performance"></a>檢查效能時使用的標準使用者帳戶
<a name="standuser"> </a>

網站集合管理員、 網站擁有者、 編輯器或參與者屬於其他安全性群組、 具有其他權限，且因此 SharePoint 會載入頁面的其他元素。
  
這是適用於 SharePoint 內部部署和 SharePoint Online 但內部部署案例中的差異便不會輕鬆發現如 SharePoint Online 所示。
  
才能正確地評估] 頁面上將如何執行使用者，您應該使用標準的使用者帳戶以避免載入撰寫控制項與其他安全性群組與相關的流量。
  
## <a name="connection-categories-for-performance-tuning"></a>效能調整的連線類別
<a name="connect"> </a>

您可將伺服器與使用者之間的連線分類成三種主要元件。在設計 SharePoint Online 頁面以深入瞭解載入時間時，請將這些元件納入考量。
  
- **伺服器。** Microsoft 主控的資料中心伺服器。
    
- **網路。** Microsoft network、 網際網路及內部網路之間的資料中心與您的使用者。
    
- **瀏覽器。** 其中載入頁面。
    
在這三種連線中，通常有五個原因會造成 95% 的頁面緩滿情形。本文將討論這些原因：
  
- 瀏覽問題
    
- 內容彙總
    
- 大型檔案
    
- 對伺服器的要求太多
    
- 網頁組件處理
    
### <a name="server-connection"></a>伺服器連線
<a name="server"> </a>

許多影響 SharePoint 內部部署效能的問題也會在 SharePoint Online 上出現。
  
一如預期，您有許多手段可控制伺服器在內部部署 SharePoint 中的執行效能。但在 SharePoint Online 上，情形略有不同。您讓伺服器執行的工作越多，呈現頁面所需的時間就越長。而在 SharePoint 中，含有多個網頁組件的複雜頁面才是造成這方面問題的最大禍首。
  
SharePoint Online
  
![伺服器連線的螢幕擷取畫面](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
SharePoint
  
![內部部署伺服器的螢幕擷取畫面](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
在 SharePoint Online 上，某些網頁要求可能實際上最後會呼叫多部伺服器。原本只是一個要求，最後卻可能演變成涉及多部伺服器的多個要求。從頁面載入的觀點來看，這些互動不僅成本昂貴且會讓效率變慢。
  
這些伺服器對伺服器的互動範例如下：
  
- Web 對 SQL Server
    
- Web 對應用程式伺服器
    
另一個導致伺服器互動速度變慢的因素是快取遺漏。不同於內部部署 SharePoint，雖然機率微乎其微，但您有可能會叫用相同伺服器來取得之前造訪的頁面；這個情形會讓物件快取過時。
  
### <a name="network-connection"></a>網路連線
<a name="network"> </a>

使用不會利用的 WAN 的內部部署 SharePoint，您可能會使用資料中心及使用者之間的高速連線。一般而言，事項很容易管理觀點的網路。
  
在 SharePoint Online 上，則還要再考慮幾個因素，例如：
  
- Microsoft 網路
    
- 網際網路
    
- ISP
    
不論您使用哪個 SharePoint (和那個網路) 版本，會導致網路忙碌的因素通常包括：
  
- 承載過大
    
- 檔案太多
    
- 與伺服器的實體距離太遠
    
您可以運用 SharePoint Online 中的其中一個功能是 Microsoft CDN （內容傳遞網路）。CDN 基本上是跨多個資料中心部署伺服器的分散式的集合。CDN 與頁面上的內容可以架設在接近用戶端的伺服器上即使用戶端遠從原始的 SharePoint 伺服器。Microsoft 將會使用此更未來來儲存的頁面以無法自訂，例如 SharePoint Online 的管理首頁上的本機執行個體。如需 Cdn 的詳細資訊，請參閱 ＜[內容傳遞網路](https://support.office.com/article/Content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)。
  
您必須注意但可能無能為力的因素是您的 ISP 連線速度。簡單的速度測試工具會告訴您連線速度。
  
### <a name="browser-connection"></a>瀏覽器連線
<a name="browser"> </a>

從效能的觀點來看，有幾個與網頁瀏覽器有關的因素要考慮進去。
  
非常複雜的頁面都會影響效能。大多數的瀏覽器只能有小快取 (筆 90 MB)，同時平均網頁通常是筆 1.6 MB。這不需要長取得用於。
  
頻寬也可能發生問題。例如，如果使用者觀看這支影片另一個工作階段中，這會影響您的 SharePoint 頁面的效能。雖然您無法防止使用者媒體資料流，您可以控制的使用者會載入頁面的方式。
  
請參閱下列文章的不同的 SharePoint Online 頁面自訂技巧及其他最佳作法，協助您達到最佳效能。
  
- [SharePoint Online 的導覽選項](navigation-options-for-sharepoint-online.md)
    
- [使用 SharePoint Online 頁面診斷工具](page-diagnostics-for-spo.md)
    
- [SharePoint Online 的影像最佳化](image-optimization-for-sharepoint-online.md)
    
- [延遲載入 SharePoint Online 中的影像和 JavaScript](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [SharePoint Online 中的縮製及統合技術](minification-and-bundling-in-sharepoint-online.md)
    
- [使用內容傳遞網路](using-content-delivery-networks-with-sharepoint-online.md)
    
- [使用，而不內容查詢網頁組件的內容搜尋網頁組件來增進效能的 SharePoint Online](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [容量規劃和測試 SharePoint Online 的負載](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [診斷 SharePoint Online 的效能問題](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [使用 SharePoint Online 的物件快取](using-the-object-cache-with-sharepoint-online.md)
    
- [操作方法：如何避免在 SharePoint Online 中受到節流控制或封鎖](https://msdn.microsoft.com/en-us/library/office/dn889829.aspx)
    

