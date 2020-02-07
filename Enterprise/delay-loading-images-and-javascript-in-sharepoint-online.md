---
title: 延遲載入 SharePoint Online 中的影像和 JavaScript
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 74d327e5-755f-4135-b9a5-7b79578c1bf9
description: 本文說明如何降低 SharePoint Online 頁面載入時間，透過使用 JavaScript 延遲載入影像以及頁面載入後再載入非必要 JavaScript，直到。
ms.openlocfilehash: 86efb767e80927f7d3f5d8055676e6d99da4d667
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840560"
---
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a>延遲載入 SharePoint Online 中的影像和 JavaScript

本文說明如何降低 SharePoint Online 頁面載入時間，透過使用 JavaScript 延遲載入影像以及頁面載入後再載入非必要 JavaScript，直到。
  
影像可以造成負面的影響 SharePoint Online 上的頁面載入速度。 根據預設，大部分現代的網際網路瀏覽器預先擷取影像載入的 HTML 網頁時。 這可能會導致是不必要地載入速度緩慢，如果影像不顯示在螢幕上，直到使用者會向下捲動頁面。 影像可以封鎖瀏覽器中載入網頁的可見的一部分。 若要解決此問題，您可以使用 JavaScript 以略過第一次載入影像。 此外，載入非必要 JavaScript 可以減慢 SharePoint 頁面上的載入時間太。 本主題說明您可以用來改善頁面載入時間與 SharePoint Online 中的 JavaScript 一些方法。
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a>在 SharePoint Online 頁面載入透過使用 JavaScript 延遲映像來改善頁面載入時間

您可以使用 JavaScript 來防止從預先擷取映像在網頁瀏覽器。 這會加快整體的文件呈現。 若要執行這項操作您移除從 src 屬性的值\<img\>標記並取代為資料屬性中的檔案路徑如下： 資料來源。 例如：
  
```html
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

使用此方法，在瀏覽器不會立即下載影像。 如果影像位於帶正負號，JavaScript 會告訴瀏覽器並前往從資料屬性擷取 URL，並將它插入為 src 屬性的值。 影像只會載入為使用者捲動和提到到檢視。
  
若要讓這一切發生，您需要使用 JavaScript。
  
在文字檔案中，定義**Iselementinviewport** （） 函數來檢查元素是在組件中的使用者可以看見的瀏覽器。
  
```javascript
function isElementInViewport(el) {
  if (!el)
    return false;
  var rect = el.getBoundingClientRect();
  return (
    rect.top >= 0 &amp;&amp;
    rect.left >= 0 &amp;&amp;
    rect.bottom <= (window.innerHeight || document.documentElement.clientHeight) &amp;&amp;
    rect.right <= (window.innerWidth || document.documentElement.clientWidth)
  );
}
```

接下來，使用**Iselementinviewport** **loadItemsInView()** 函式中。 **LoadItemsInView()** 函式會載入具有資料 src 屬性的值，如果他們是在組件中的使用者可以看見的瀏覽器的所有影像。 文字檔案中加入下列函式：
  
```javascript
function loadItemsInView() {
  //Select elements by the row id.
  $("#row [data-src]").each(function () {
      var isVisible = isElementInViewport(this);
      if (isVisible) {
          if ($(this).attr("src") == undefined) {
              $(this).attr("src", $(this).data("src"));
          }
      }
  });
}
```

最後，呼叫**loadItemsInView()** 從**window.onscroll()** 內，如下列範例所示。 這可確保當使用者需要它們，但是不之前，就會載入任何處於帶正負號的影像。 文字檔案中加入下列：
  
```javascript
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

若是 SharePoint Online，您需要將下列函式附加至捲軸事件上 #s4-workspace \<div\>標記。 這是因為視窗事件會被覆寫，才能確保在功能區會維持附加至頁面頂端。
  
```javascript
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

將文字檔儲存為副檔名是.js，例如 delayLoadImages.js JavaScript 檔案。
  
一旦您已完成的撰寫 delayLoadImages.js 後，您可以將檔案的內容新增至 SharePoint Online 中的主版頁面。 要這麼做，藉由將指令碼連結新增至主版頁面中的標頭。 一旦主版頁面中的範例，JavaScript 將套用到您的 SharePoint Online 網站中使用該主版頁面版面配置的所有頁面。 或者，如果您想要只使用此網站的一個頁面上，請將 JavaScript 嵌入] 頁面上使用指令碼編輯器網頁組件。 這些主題以取得詳細資訊，請參閱：
  
- [如何： 將主版頁面套用至 SharePoint 2013 中的網站](https://go.microsoft.com/fwlink/p/?LinkId=525627)

- [如何： 在 SharePoint 2013 中建立網頁版面配置](https://go.microsoft.com/fwlink/p/?LinkId=525628)

### <a name="example-referencing-the-javascript-delayloadimagesjs-file-from-a-master-page-in-sharepoint-online"></a>範例： 從 SharePoint Online 中的主版頁面參照 JavaScript delayLoadImages.js 檔案
  
為了讓此功能才能運作，您也需要參照 jQuery 主版頁面中。 在下列範例中，您可以看到的初始頁面載入沒有只有一個影像載入，但有好幾種多個頁面上。
  
![顯示頁面上載入一個影像的螢幕擷取畫面](media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
下列螢幕擷取畫面顯示的其餘部分，之後在捲動至檢視下載的影像。
  
![顯示頁面上載入數個影像的螢幕擷取畫面](media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
透過使用 JavaScript 延遲載入影像可以是有效的技術，以提升效能;不過，如果技術會套用至公用網站然後搜尋引擎不能夠以相同方式編目影像它們會編目定期組成的影像。 這會影響在搜尋引擎排名，因為本身的映像上的中繼資料不是真的有等到頁面載入。 搜尋引擎編目程式只能讀取 HTML，因此將不會看到圖像為頁面上的內容。 影像是用來在搜尋結果的排名頁面的因素之一。 若要解決此問題的一種方式是使用為您的影像的簡介文字。
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a>GitHub 程式碼範例： 插入 JavaScript 以改善效能

請不要遺漏有關 GitHub 所提供[JavaScript 插入](https://go.microsoft.com/fwlink/p/?LinkId=524759)上的文章和程式碼範例。
  
## <a name="see-also"></a>另請參閱

[在 Office 2013 和 Office 365 專業增強版支援的瀏覽器](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[如何： 將主版頁面套用至 SharePoint 2013 中的網站](https://go.microsoft.com/fwlink/p/?LinkId=525627)
  
[如何： 在 SharePoint 2013 中建立網頁版面配置](https://go.microsoft.com/fwlink/p/?LinkId=525628)
