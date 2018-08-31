---
title: 延遲載入 SharePoint Online 中的影像和 JavaScript
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/29/2016
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 74d327e5-755f-4135-b9a5-7b79578c1bf9
description: 本文說明如何減少 SharePoint Online 頁面載入時間，延遲載入影像使用 JavaScript 及等候直到非必要 JavaScript 載入頁面載入之後。
ms.openlocfilehash: b8b052d85c99e51dff4b0fc747b3b52c17de8d8b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540165"
---
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a><span data-ttu-id="6a29b-103">延遲載入 SharePoint Online 中的影像和 JavaScript</span><span class="sxs-lookup"><span data-stu-id="6a29b-103">Delay loading images and JavaScript in SharePoint Online</span></span>

<span data-ttu-id="6a29b-104">本文說明如何減少 SharePoint Online 頁面載入時間，延遲載入影像使用 JavaScript 及等候直到非必要 JavaScript 載入頁面載入之後。</span><span class="sxs-lookup"><span data-stu-id="6a29b-104">This article describes how you can decrease the load time for SharePoint Online pages by using JavaScript to delay loading images and also by waiting to load non-essential JavaScript until after the page loads.</span></span> 
  
<span data-ttu-id="6a29b-p101">影像會對 SharePoint Online 上的頁面載入速度造成負面影響。根據預設，現今大部分網際網路瀏覽器在載入 HTML 網頁時會預先擷取影像。若影像要等到使用者向下捲動畫面後才會顯現，預先擷取影像會導致頁面載入速度太慢。影像會妨礙瀏覽器載入頁面的可見部分。若要解決此問題，您可使用 JavaScript 先略過影像載入作業。此外，載入非必要 JavaScript 也會讓 SharePoint 頁面載入時間變慢。本主題說明一些方法供您在 SharePoint Online 中使用 JavaScript 改善頁面載入時間。</span><span class="sxs-lookup"><span data-stu-id="6a29b-p101">Images can negatively affect page load speeds on SharePoint Online. By default, most modern Internet browsers pre-fetch images when loading an HTML page. This can cause the page to be unnecessarily slow to load if the images are not visible on the screen until the user scrolls down. The images can block the browser from loading the visible part of the page. To work around this problem, you can use JavaScript to skip loading the images first. Also, loading non-essential JavaScript can slow down load times on your SharePoint pages too. This topic describes some methods you can use to improve page load times with JavaScript in SharePoint Online.</span></span> 
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a><span data-ttu-id="6a29b-112">透過使用 JavaScript 延遲 SharePoint Online 頁面的影像載入來改善頁面載入時間</span><span class="sxs-lookup"><span data-stu-id="6a29b-112">Improve page load times by delaying image loading in SharePoint Online pages by using JavaScript</span></span>

<span data-ttu-id="6a29b-p102">您可以使用 JavaScript 來防止從預先擷取圖像在網頁瀏覽器。加快整體文件呈現。若要執行這項作業您移除 src 屬性的值\<img\>標記並取代為在屬性中的資料檔案的路徑例如： 資料 src。例如：</span><span class="sxs-lookup"><span data-stu-id="6a29b-p102">You can use JavaScript to prevent a web browser from pre-fetching images. This speeds up overall document rendering. To do this you remove the value of the src attribute from the \<img\> tag and replace it with the path to a file in a data attribute such as: data-src. For example:</span></span>
  
```
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

<span data-ttu-id="6a29b-p103">使用此方法，在瀏覽器不會立即下載圖像。如果映像位於檢視區、 JavaScript 會告知擷取資料屬性的 URL 並將它插入 src 屬性的值為瀏覽器。映像只會載入為使用者捲動並專職入檢視。</span><span class="sxs-lookup"><span data-stu-id="6a29b-p103">By using this method, the browser doesn't download the images immediately. If the image is already in the viewport, JavaScript tells the browser to retrieve the URL from the data attribute and insert it as the value for the src attribute. The image only loads as the user scrolls and it comes into view.</span></span>
  
<span data-ttu-id="6a29b-119">若要讓所有發生，您需要使用 JavaScript。</span><span class="sxs-lookup"><span data-stu-id="6a29b-119">To make all of this happen, you'll need to use JavaScript.</span></span>
  
<span data-ttu-id="6a29b-120">在文字檔案中，定義 **isElementInViewport()** 函數來檢查元素是否位在使用者可見的瀏覽器部分。</span><span class="sxs-lookup"><span data-stu-id="6a29b-120">In a text file, define the **isElementInViewport()** function to check whether or not an element is in the part of the browser that is visible to the user.</span></span> 
  
```
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

<span data-ttu-id="6a29b-p104">接下來，將 **isElementInViewport()** 用於 **loadItemsInView()** 函數。**LoadItemsInView()** 函數會載入使用者可見的瀏覽器部分中，所有具有 data-src 屬性值的影像。將下列函數新增至文字檔：</span><span class="sxs-lookup"><span data-stu-id="6a29b-p104">Next, use **isElementInViewport()** in the **loadItemsInView()** function. The **loadItemsInView()** function will load all images that have a value for the data-src attribute if they are in the part of the browser that is visible to the user. Add the following function to the text file:</span></span> 
  
```
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

<span data-ttu-id="6a29b-p105">最後，從 **window.onscroll()** 呼叫 **loadItemsInView()**，如下列範例所示。這會確保檢視區中的影像是在使用者需要時才載入，而非在需要前就載入。將下列內容新增至文字檔：</span><span class="sxs-lookup"><span data-stu-id="6a29b-p105">Finally, call **loadItemsInView()** from within **window.onscroll()** as shown in the following example. This ensures that any images that are in the viewport are loaded as the user needs them, but not before. Add the following to the text file:</span></span> 
  
```
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

<span data-ttu-id="6a29b-p106">SharePoint Online、 您需要對捲軸事件上 #s4-workspace 附加下列函數\<div\>標籤。這是因為視窗事件會覆寫為確保功能區仍會保留附加至頁面頂端。</span><span class="sxs-lookup"><span data-stu-id="6a29b-p106">For SharePoint Online, you need to attach the following function to the scroll event on the #s4-workspace \<div\> tag. This is because the window events are overridden in order to ensure the ribbon remains attached to the top of the page.</span></span>
  
```
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

<span data-ttu-id="6a29b-129">將文字檔儲存為副檔名是 .js 的 JavaScript 檔案，例如 delayLoadImages.js。</span><span class="sxs-lookup"><span data-stu-id="6a29b-129">Save the text file as a JavaScript file with the extension .js, for example delayLoadImages.js.</span></span>
  
<span data-ttu-id="6a29b-p107">您已完成撰寫 delayLoadImages.js，您可以新增之檔案的內容以在 SharePoint Online 中的主版頁面。您執行方法是將指令碼連結新增至主版頁面中的頁首。一旦處於主版頁面、 JavaScript 會套用至 SharePoint Online 網站中使用該主版頁面版面配置的所有頁面。或者，如果您想要僅使用此網站的一個頁面上，使用指令碼編輯器網頁組件到頁面中內嵌 JavaScript。請參閱下列主題的詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="6a29b-p107">Once you've finished writing delayLoadImages.js, you can add the contents of the file to a master page in SharePoint Online. You do this by adding a script link to the header in the master page. Once it's in a master page, the JavaScript will be applied to all pages in your SharePoint Online site that use that master page layout. Alternatively, if you intend to only use this on one page of your site, use the script editor Web Part to embed the JavaScript into the page. See these topics for more information:</span></span>
  
- [<span data-ttu-id="6a29b-135">操作方法： 將主版頁面套用到 SharePoint 2013 中的網站</span><span class="sxs-lookup"><span data-stu-id="6a29b-135">How to: Apply a master page to a site in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525627)
    
- [<span data-ttu-id="6a29b-136">操作方法： 在 SharePoint 2013 中建立頁面配置</span><span class="sxs-lookup"><span data-stu-id="6a29b-136">How to: Create a page layout in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525628)
    
 <span data-ttu-id="6a29b-137">**範例：從 SharePoint Online 中的主版頁面參照 JavaScript delayLoadImages.js 檔案**</span><span class="sxs-lookup"><span data-stu-id="6a29b-137">**Example: Referencing the JavaScript delayLoadImages.js file from a master page in SharePoint Online**</span></span>
  
<span data-ttu-id="6a29b-p108">為讓此範例有效，您也需要參照主版頁面中的 jQuery。在下列範例中，您可看到初始頁面載入中只有載入一個影像，但頁面上還有好幾個影像。</span><span class="sxs-lookup"><span data-stu-id="6a29b-p108">In order for this to work, you also need to reference jQuery in the master page. In the following example, you can see in the initial page load that there is only one image loaded but there are several more on the page.</span></span>
  
![顯示頁面上載入一個影像的螢幕擷取畫面](media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
<span data-ttu-id="6a29b-141">下列螢幕擷取畫面顯示在捲動至檢視範圍後會下載的其餘影像。</span><span class="sxs-lookup"><span data-stu-id="6a29b-141">The following screen shot shows the rest of the images that are downloaded after they scroll into view.</span></span>
  
![顯示頁面上載入數個影像的螢幕擷取畫面](media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
<span data-ttu-id="6a29b-p109">使用 JavaScript 來延遲影像載入的技術可有效提升效能；但若將該技術套用在公用網站上，搜尋引擎將無法像編目一般形式的影像一樣地對這些影像進行編目。這會影響搜尋引擎排名，因為影像本身的中繼資料要到頁面載入後才真的存在。搜尋引擎編目程式只會讀取 HTML，因此不會將影像視為頁面上的內容。影像是用來在搜尋結果排名頁面的因素之一。解決此問題的方法之一是對影像使用介紹文字。</span><span class="sxs-lookup"><span data-stu-id="6a29b-p109">Delaying image loading by using JavaScript can be an effective technique in increasing performance; however, if the technique is applied on a public website then search engines are not able to crawl the images in the same way they would crawl a regularly formed image. This can affect rankings on search engines because metadata on the image itself is not really there until the page loads. Search engine crawlers only read the HTML and therefore will not see the images as content on the page. Images are one of the factors used to rank pages in search results. One way to work around this is to use introductory text for your images.</span></span>
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a><span data-ttu-id="6a29b-148">GitHub 程式碼範例：插入 JavaScript 以改善效能</span><span class="sxs-lookup"><span data-stu-id="6a29b-148">GitHub code sample: Injecting JavaScript to improve performance</span></span>

<span data-ttu-id="6a29b-149">千萬別錯過在[JavaScript 插入](https://go.microsoft.com/fwlink/p/?LinkId=524759)GitHub 上所提供的文章和程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="6a29b-149">Don't miss the article and code sample on [JavaScript injection](https://go.microsoft.com/fwlink/p/?LinkId=524759) provided on GitHub.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="6a29b-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a29b-150">See also</span></span>

[<span data-ttu-id="6a29b-151">支援的瀏覽器在 Office 2013 與 Office 365 ProPlus</span><span class="sxs-lookup"><span data-stu-id="6a29b-151">Supported browsers in Office 2013 and Office 365 ProPlus</span></span>](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[<span data-ttu-id="6a29b-152">操作方法： 將主版頁面套用到 SharePoint 2013 中的網站</span><span class="sxs-lookup"><span data-stu-id="6a29b-152">How to: Apply a master page to a site in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525627)
  
[<span data-ttu-id="6a29b-153">操作方法： 在 SharePoint 2013 中建立頁面配置</span><span class="sxs-lookup"><span data-stu-id="6a29b-153">How to: Create a page layout in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525628)

