---
title: 使用 SharePoint Online 使用內容傳遞網路
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 5/8/2017
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: 9a64268c-0b74-4eaa-b971-fb6380b1b165
description: 摘要： 本文說明內容傳遞網路 (Cdn) 以及如何使用它們來增加 SharePoint Online 效能。
ms.openlocfilehash: 24b12ae60a8c089d8e32d2609957e8b0e3420510
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070579"
---
# <a name="using-content-delivery-networks-with-sharepoint-online"></a>使用 SharePoint Online 使用內容傳遞網路

 **摘要：** 本文說明內容傳遞網路 (Cdn) 以及如何使用它們來增加 SharePoint Online 效能。 
  
在現今的 web 開發社群，有許多常用程式庫 （例如 JavaScript 和 CSS 檔案），您可能會包含在您的 SharePoint 解決方案中。 多個 Microsoft 其 ASP CDN 上所主控。 這表示您可以從這些分散式伺服器參照這些文件庫，並允許網際網路的內建 DNS 路由系統找不到您的使用者最接近的伺服器。 本文中的範例會示範如何從 SharePoint Online 伺服器與 ASP CDN 下載常用的文件庫 jQuery 的時間差異是相當重要。 使用者也可能已在本機電腦上快取，如此他們沒有下載檔案的 CDN 版本。 這可以是重要如果您有分散式世界各地和遠從資料中心主控您的 SharePoint Online 網站的使用者。
  
在建立頁面的 SharePoint Online 時，延遲可能受到您的使用者和 SharePoint Online 的執行個體的位置之間的實體距離。 這是特別重要，全域顯示狀態可能會主控網站有一個大陸時世界另一邊的使用者存取其內容的組織。 Cdn 協助減輕這種情況下所架設在不同的位置接近使用者特定常用的網站資產。
  
由於 CDN 是伺服器的全球性網路相同的檔案，檔案儲存在 Cdn 的網際網路 Url 會被解譯由用戶端機器，以便將伺服器的最接近使用者該主機做檔案。 這麼做會大幅減少延遲所導致的網路來回行程。
  
## <a name="the-challenge-of-hosting-sharepoint-online-sites-for-a-global-audience"></a>之所有對象的主控 SharePoint Online 網站所面臨的挑戰

SharePoint Online 網站都架設在資料中心相對於選取當您使用 Office 365 註冊的位置 （由使用者指定）。 例如，如果您的網站是在美國境內的伺服器上，且必須從東亞存取網站的使用者，延遲問題可能會發生由於資料已通過光纖線之間的距離。
  
預設 SharePoint 使用者介面所使用的許多靜態檔案已裝載的 Cdn Microsoft 全球網路上。 這樣會增進效能經過一段時間。 不過，如果您使用任何常用的 JavaScript 和 CSS 資產 （例如，JQuery、 Modernizr、 啟動安裝程式或 ASP.NET Ajax） 您可以使用免費提供 Cdn 改善這些檔案的載入時間。
  
## <a name="advantages-of-using-cdns-to-improve-download-speed"></a>優點使用 Cdn 改善下載速度

使用 Cdn 可以改善頁面載入時間各種不同的原因。 其中一個原因是 CDN 與使用者之間的距離，可能會小於到 SharePoint Online 的執行個體之間的距離。 這些網路高度分散和設計也可以有極高可用性和回應的時間。 另一個原因是，如果您使用 CSS 檔案的常用程式庫、 CDN 搭配，使用者可能已快取的文件庫，而且它們甚至是不需要完全下載。
  
下列螢幕擷取畫面會說明使用 Cdn 的優點。 下列螢幕擷取畫面會從 Internet Explorer 11 開發人員工具中的 [**網路**] 索引標籤。 下列螢幕擷取畫面顯示常用的文件庫 jQuery 延遲。 若要以相反此畫面中，Internet Explorer 中，按**F12**並選取 Wi-fi 圖示來表示 [**網路**] 索引標籤。 
  
![F12 網路的螢幕擷取畫面](media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
這個螢幕擷取畫面顯示文件庫上傳至主版頁面圖庫，SharePoint Online 網站本身。 上傳文件庫所花的時間為 1.51 秒。
  
![載入時間為 1.51 秒的螢幕擷取畫面](media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
第二個螢幕擷取畫面顯示由 Microsoft 傳遞的相同檔案 CDN。 這段時間延遲是大約 496 毫秒。 這是較大型的改善，並顯示整個第二個 shaved 關閉下載頁面內容的總時間。
  
![載入時間為 469 毫秒的螢幕擷取畫面](media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)
  
## <a name="using-cdns-with-sharepoint-server-2013"></a>與 SharePoint Server 2013 使用 Cdn

使用 Cdn 只合理的 SharePoint Online 內容中，但應避免使用，與 SharePoint Server 2013。 這是因為所有周圍的地理位置的優點不保留 true 是表示如果伺服器是位於的內部或地理位置還是關閉。 此外，如果沒有網路連線至架設所在的伺服器，然後網站可能使用的網際網路連線並因此無法擷取 CDN 檔案。 否則，您應該使用 CDN，如果沒有一個可用，而且您的網站需要穩定的文件庫和檔案。
  
## <a name="popular-cdns-and-how-to-use-them"></a>常用 Cdn 及其使用方式

Microsoft 的 Ajax CDN 提供大部分的常用程式庫，包括 jQuery （及其所有的其他程式庫），ASP.NET Ajax、 Bootstrap、 Knockout.js，以及其他更多選項。
  
若要在專案中包含這些指令碼，只要取代任何這些公開提供的文件庫的參照的 CDN 地址，而不是包含在您本身的專案中的參照。 若要連結至 jQuery，例如，使用下列程式碼：
  
```
<script src=http://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

如需 Cdn 的詳細資訊，請參閱 <<c0>內容傳遞網路。
  
## <a name="more-topics-about-using-cdns-with-sharepoint"></a>使用 Cdn 與 SharePoint 相關的其他主題

[從 Office 365 CDN 裝載用戶端網頁組件](https://dev.office.com/sharepoint/docs/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)
  

