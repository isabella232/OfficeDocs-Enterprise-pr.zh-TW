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
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a><span data-ttu-id="cefa1-103">延遲載入 SharePoint Online 中的影像和 JavaScript</span><span class="sxs-lookup"><span data-stu-id="cefa1-103">Delay loading images and JavaScript in SharePoint Online</span></span>

<span data-ttu-id="cefa1-104">本文說明如何降低 SharePoint Online 頁面載入時間，透過使用 JavaScript 延遲載入影像以及頁面載入後再載入非必要 JavaScript，直到。</span><span class="sxs-lookup"><span data-stu-id="cefa1-104">This article describes how you can decrease the load time for SharePoint Online pages by using JavaScript to delay loading images and also by waiting to load non-essential JavaScript until after the page loads.</span></span>
  
<span data-ttu-id="cefa1-105">影像可以造成負面的影響 SharePoint Online 上的頁面載入速度。</span><span class="sxs-lookup"><span data-stu-id="cefa1-105">Images can negatively affect page load speeds on SharePoint Online.</span></span> <span data-ttu-id="cefa1-106">根據預設，大部分現代的網際網路瀏覽器預先擷取影像載入的 HTML 網頁時。</span><span class="sxs-lookup"><span data-stu-id="cefa1-106">By default, most modern Internet browsers pre-fetch images when loading an HTML page.</span></span> <span data-ttu-id="cefa1-107">這可能會導致是不必要地載入速度緩慢，如果影像不顯示在螢幕上，直到使用者會向下捲動頁面。</span><span class="sxs-lookup"><span data-stu-id="cefa1-107">This can cause the page to be unnecessarily slow to load if the images are not visible on the screen until the user scrolls down.</span></span> <span data-ttu-id="cefa1-108">影像可以封鎖瀏覽器中載入網頁的可見的一部分。</span><span class="sxs-lookup"><span data-stu-id="cefa1-108">The images can block the browser from loading the visible part of the page.</span></span> <span data-ttu-id="cefa1-109">若要解決此問題，您可以使用 JavaScript 以略過第一次載入影像。</span><span class="sxs-lookup"><span data-stu-id="cefa1-109">To work around this problem, you can use JavaScript to skip loading the images first.</span></span> <span data-ttu-id="cefa1-110">此外，載入非必要 JavaScript 可以減慢 SharePoint 頁面上的載入時間太。</span><span class="sxs-lookup"><span data-stu-id="cefa1-110">Also, loading non-essential JavaScript can slow down load times on your SharePoint pages too.</span></span> <span data-ttu-id="cefa1-111">本主題說明您可以用來改善頁面載入時間與 SharePoint Online 中的 JavaScript 一些方法。</span><span class="sxs-lookup"><span data-stu-id="cefa1-111">This topic describes some methods you can use to improve page load times with JavaScript in SharePoint Online.</span></span>
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a><span data-ttu-id="cefa1-112">在 SharePoint Online 頁面載入透過使用 JavaScript 延遲映像來改善頁面載入時間</span><span class="sxs-lookup"><span data-stu-id="cefa1-112">Improve page load times by delaying image loading in SharePoint Online pages by using JavaScript</span></span>

<span data-ttu-id="cefa1-113">您可以使用 JavaScript 來防止從預先擷取映像在網頁瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="cefa1-113">You can use JavaScript to prevent a web browser from pre-fetching images.</span></span> <span data-ttu-id="cefa1-114">這會加快整體的文件呈現。</span><span class="sxs-lookup"><span data-stu-id="cefa1-114">This speeds up overall document rendering.</span></span> <span data-ttu-id="cefa1-115">若要執行這項操作您移除從 src 屬性的值\<img\>標記並取代為資料屬性中的檔案路徑如下： 資料來源。</span><span class="sxs-lookup"><span data-stu-id="cefa1-115">To do this you remove the value of the src attribute from the \<img\> tag and replace it with the path to a file in a data attribute such as: data-src.</span></span> <span data-ttu-id="cefa1-116">例如：</span><span class="sxs-lookup"><span data-stu-id="cefa1-116">For example:</span></span>
  
```html
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

<span data-ttu-id="cefa1-117">使用此方法，在瀏覽器不會立即下載影像。</span><span class="sxs-lookup"><span data-stu-id="cefa1-117">By using this method, the browser doesn't download the images immediately.</span></span> <span data-ttu-id="cefa1-118">如果影像位於帶正負號，JavaScript 會告訴瀏覽器並前往從資料屬性擷取 URL，並將它插入為 src 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="cefa1-118">If the image is already in the viewport, JavaScript tells the browser to retrieve the URL from the data attribute and insert it as the value for the src attribute.</span></span> <span data-ttu-id="cefa1-119">影像只會載入為使用者捲動和提到到檢視。</span><span class="sxs-lookup"><span data-stu-id="cefa1-119">The image only loads as the user scrolls and it comes into view.</span></span>
  
<span data-ttu-id="cefa1-120">若要讓這一切發生，您需要使用 JavaScript。</span><span class="sxs-lookup"><span data-stu-id="cefa1-120">To make all of this happen, you'll need to use JavaScript.</span></span>
  
<span data-ttu-id="cefa1-121">在文字檔案中，定義**Iselementinviewport** （） 函數來檢查元素是在組件中的使用者可以看見的瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="cefa1-121">In a text file, define the **isElementInViewport()** function to check whether or not an element is in the part of the browser that is visible to the user.</span></span>
  
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

<span data-ttu-id="cefa1-122">接下來，使用**Iselementinviewport** **loadItemsInView()** 函式中。</span><span class="sxs-lookup"><span data-stu-id="cefa1-122">Next, use **isElementInViewport()** in the **loadItemsInView()** function.</span></span> <span data-ttu-id="cefa1-123">**LoadItemsInView()** 函式會載入具有資料 src 屬性的值，如果他們是在組件中的使用者可以看見的瀏覽器的所有影像。</span><span class="sxs-lookup"><span data-stu-id="cefa1-123">The **loadItemsInView()** function will load all images that have a value for the data-src attribute if they are in the part of the browser that is visible to the user.</span></span> <span data-ttu-id="cefa1-124">文字檔案中加入下列函式：</span><span class="sxs-lookup"><span data-stu-id="cefa1-124">Add the following function to the text file:</span></span>
  
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

<span data-ttu-id="cefa1-125">最後，呼叫**loadItemsInView()** 從**window.onscroll()** 內，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="cefa1-125">Finally, call **loadItemsInView()** from within **window.onscroll()** as shown in the following example.</span></span> <span data-ttu-id="cefa1-126">這可確保當使用者需要它們，但是不之前，就會載入任何處於帶正負號的影像。</span><span class="sxs-lookup"><span data-stu-id="cefa1-126">This ensures that any images that are in the viewport are loaded as the user needs them, but not before.</span></span> <span data-ttu-id="cefa1-127">文字檔案中加入下列：</span><span class="sxs-lookup"><span data-stu-id="cefa1-127">Add the following to the text file:</span></span>
  
```javascript
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

<span data-ttu-id="cefa1-128">若是 SharePoint Online，您需要將下列函式附加至捲軸事件上 #s4-workspace \<div\>標記。</span><span class="sxs-lookup"><span data-stu-id="cefa1-128">For SharePoint Online, you need to attach the following function to the scroll event on the #s4-workspace \<div\> tag.</span></span> <span data-ttu-id="cefa1-129">這是因為視窗事件會被覆寫，才能確保在功能區會維持附加至頁面頂端。</span><span class="sxs-lookup"><span data-stu-id="cefa1-129">This is because the window events are overridden in order to ensure the ribbon remains attached to the top of the page.</span></span>
  
```javascript
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

<span data-ttu-id="cefa1-130">將文字檔儲存為副檔名是.js，例如 delayLoadImages.js JavaScript 檔案。</span><span class="sxs-lookup"><span data-stu-id="cefa1-130">Save the text file as a JavaScript file with the extension .js, for example delayLoadImages.js.</span></span>
  
<span data-ttu-id="cefa1-131">一旦您已完成的撰寫 delayLoadImages.js 後，您可以將檔案的內容新增至 SharePoint Online 中的主版頁面。</span><span class="sxs-lookup"><span data-stu-id="cefa1-131">Once you've finished writing delayLoadImages.js, you can add the contents of the file to a master page in SharePoint Online.</span></span> <span data-ttu-id="cefa1-132">要這麼做，藉由將指令碼連結新增至主版頁面中的標頭。</span><span class="sxs-lookup"><span data-stu-id="cefa1-132">You do this by adding a script link to the header in the master page.</span></span> <span data-ttu-id="cefa1-133">一旦主版頁面中的範例，JavaScript 將套用到您的 SharePoint Online 網站中使用該主版頁面版面配置的所有頁面。</span><span class="sxs-lookup"><span data-stu-id="cefa1-133">Once it's in a master page, the JavaScript will be applied to all pages in your SharePoint Online site that use that master page layout.</span></span> <span data-ttu-id="cefa1-134">或者，如果您想要只使用此網站的一個頁面上，請將 JavaScript 嵌入] 頁面上使用指令碼編輯器網頁組件。</span><span class="sxs-lookup"><span data-stu-id="cefa1-134">Alternatively, if you intend to only use this on one page of your site, use the script editor Web Part to embed the JavaScript into the page.</span></span> <span data-ttu-id="cefa1-135">這些主題以取得詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="cefa1-135">See these topics for more information:</span></span>
  
- [<span data-ttu-id="cefa1-136">如何： 將主版頁面套用至 SharePoint 2013 中的網站</span><span class="sxs-lookup"><span data-stu-id="cefa1-136">How to: Apply a master page to a site in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525627)

- [<span data-ttu-id="cefa1-137">如何： 在 SharePoint 2013 中建立網頁版面配置</span><span class="sxs-lookup"><span data-stu-id="cefa1-137">How to: Create a page layout in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525628)

### <a name="example-referencing-the-javascript-delayloadimagesjs-file-from-a-master-page-in-sharepoint-online"></a><span data-ttu-id="cefa1-138">範例： 從 SharePoint Online 中的主版頁面參照 JavaScript delayLoadImages.js 檔案</span><span class="sxs-lookup"><span data-stu-id="cefa1-138">Example: Referencing the JavaScript delayLoadImages.js file from a master page in SharePoint Online</span></span>
  
<span data-ttu-id="cefa1-139">為了讓此功能才能運作，您也需要參照 jQuery 主版頁面中。</span><span class="sxs-lookup"><span data-stu-id="cefa1-139">In order for this to work, you also need to reference jQuery in the master page.</span></span> <span data-ttu-id="cefa1-140">在下列範例中，您可以看到的初始頁面載入沒有只有一個影像載入，但有好幾種多個頁面上。</span><span class="sxs-lookup"><span data-stu-id="cefa1-140">In the following example, you can see in the initial page load that there is only one image loaded but there are several more on the page.</span></span>
  
![顯示頁面上載入一個影像的螢幕擷取畫面](media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
<span data-ttu-id="cefa1-142">下列螢幕擷取畫面顯示的其餘部分，之後在捲動至檢視下載的影像。</span><span class="sxs-lookup"><span data-stu-id="cefa1-142">The following screen shot shows the rest of the images that are downloaded after they scroll into view.</span></span>
  
![顯示頁面上載入數個影像的螢幕擷取畫面](media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
<span data-ttu-id="cefa1-144">透過使用 JavaScript 延遲載入影像可以是有效的技術，以提升效能;不過，如果技術會套用至公用網站然後搜尋引擎不能夠以相同方式編目影像它們會編目定期組成的影像。</span><span class="sxs-lookup"><span data-stu-id="cefa1-144">Delaying image loading by using JavaScript can be an effective technique in increasing performance; however, if the technique is applied on a public website then search engines are not able to crawl the images in the same way they would crawl a regularly formed image.</span></span> <span data-ttu-id="cefa1-145">這會影響在搜尋引擎排名，因為本身的映像上的中繼資料不是真的有等到頁面載入。</span><span class="sxs-lookup"><span data-stu-id="cefa1-145">This can affect rankings on search engines because metadata on the image itself is not really there until the page loads.</span></span> <span data-ttu-id="cefa1-146">搜尋引擎編目程式只能讀取 HTML，因此將不會看到圖像為頁面上的內容。</span><span class="sxs-lookup"><span data-stu-id="cefa1-146">Search engine crawlers only read the HTML and therefore will not see the images as content on the page.</span></span> <span data-ttu-id="cefa1-147">影像是用來在搜尋結果的排名頁面的因素之一。</span><span class="sxs-lookup"><span data-stu-id="cefa1-147">Images are one of the factors used to rank pages in search results.</span></span> <span data-ttu-id="cefa1-148">若要解決此問題的一種方式是使用為您的影像的簡介文字。</span><span class="sxs-lookup"><span data-stu-id="cefa1-148">One way to work around this is to use introductory text for your images.</span></span>
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a><span data-ttu-id="cefa1-149">GitHub 程式碼範例： 插入 JavaScript 以改善效能</span><span class="sxs-lookup"><span data-stu-id="cefa1-149">GitHub code sample: Injecting JavaScript to improve performance</span></span>

<span data-ttu-id="cefa1-150">請不要遺漏有關 GitHub 所提供[JavaScript 插入](https://go.microsoft.com/fwlink/p/?LinkId=524759)上的文章和程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="cefa1-150">Don't miss the article and code sample on [JavaScript injection](https://go.microsoft.com/fwlink/p/?LinkId=524759) provided on GitHub.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="cefa1-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cefa1-151">See also</span></span>

[<span data-ttu-id="cefa1-152">在 Office 2013 和 Office 365 專業增強版支援的瀏覽器</span><span class="sxs-lookup"><span data-stu-id="cefa1-152">Supported browsers in Office 2013 and Office 365 ProPlus</span></span>](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[<span data-ttu-id="cefa1-153">如何： 將主版頁面套用至 SharePoint 2013 中的網站</span><span class="sxs-lookup"><span data-stu-id="cefa1-153">How to: Apply a master page to a site in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525627)
  
[<span data-ttu-id="cefa1-154">如何： 在 SharePoint 2013 中建立網頁版面配置</span><span class="sxs-lookup"><span data-stu-id="cefa1-154">How to: Create a page layout in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525628)
