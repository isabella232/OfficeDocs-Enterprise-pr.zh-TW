---
title: SharePoint Online 中的縮製和統合
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 3/1/2017
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
ms.assetid: 87a52468-994e-43a2-b155-7229ed659291
description: 本文說明如何使用縮製及統合技術搭配 Web Essentials 來減少 HTTP 要求數目，並降低 SharePoint Online 中載入頁面所花費的時間。
ms.openlocfilehash: ca0ad53f2c854226b729a94e345a553850517eaf
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844894"
---
# <a name="minification-and-bundling-in-sharepoint-online"></a><span data-ttu-id="16105-103">SharePoint Online 中的縮製和統合</span><span class="sxs-lookup"><span data-stu-id="16105-103">Minification and bundling in SharePoint Online</span></span>

<span data-ttu-id="16105-104">本文說明如何使用縮製及統合技術搭配 Web Essentials 來減少 HTTP 要求數目，並降低 SharePoint Online 中載入頁面所花費的時間。</span><span class="sxs-lookup"><span data-stu-id="16105-104">This article describes how to use minification and bundling techniques with Web Essentials to reduce the number of HTTP requests and to reduce the time it takes to load pages in SharePoint Online.</span></span>
  
<span data-ttu-id="16105-105">當您自訂您的網站時您可以最終將大量的額外檔案新增至伺服器，以支援自訂。</span><span class="sxs-lookup"><span data-stu-id="16105-105">When you customize your website you can end up adding a large number of extra files to the server to support the customization.</span></span> <span data-ttu-id="16105-106">新增額外的 JavaScript、 CSS 及影像會增加接著會增加的時間的伺服器就會出現在網頁上的 HTTP 要求數目。</span><span class="sxs-lookup"><span data-stu-id="16105-106">Adding extra JavaScript, CSS, and images increases the number of HTTP requests to the server which in turn increases the time it takes to display a web page.</span></span> <span data-ttu-id="16105-107">如果您有多個相同類型的檔案，您可以將彙整這些檔案以進行更快速地下載這些檔案。</span><span class="sxs-lookup"><span data-stu-id="16105-107">If you have multiple files of the same type, you can bundle these files to make downloading these files faster.</span></span>
  
<span data-ttu-id="16105-108">對於 JavaScript 和 CSS 檔案，您也可以使用稱為縮製，其中移除空白字元和其他不必要的字元以減少檔案的總大小方法。</span><span class="sxs-lookup"><span data-stu-id="16105-108">For JavaScript and CSS files, you can also use an approach called minification, where you reduce the total size of files by removing whitespace and other characters that aren't necessary.</span></span>
  
## <a name="minification-and-bundling-javascript-and-css-files-with-web-essentials"></a><span data-ttu-id="16105-109">縮製及統合 JavaScript 和 CSS 檔案搭配 Web Essentials</span><span class="sxs-lookup"><span data-stu-id="16105-109">Minification and bundling JavaScript and CSS files with Web Essentials</span></span>

<span data-ttu-id="16105-110">您可以使用協力廠商軟體如 Web Essentials 來統合 CSS 和 JavaScript 檔案。</span><span class="sxs-lookup"><span data-stu-id="16105-110">You can use third-party software such as Web Essentials to bundle CSS and JavaScript files.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="16105-111">Web Essentials 是協力廠商、 開放原始碼、 社群為基礎的專案。</span><span class="sxs-lookup"><span data-stu-id="16105-111">Web Essentials is a third-party, open-source, community-based project.</span></span> <span data-ttu-id="16105-112">軟體會延伸至 Visual Studio 2012 和 Visual Studio 2013 和 Microsoft 並不支援。</span><span class="sxs-lookup"><span data-stu-id="16105-112">The software is an extension to Visual Studio 2012 and Visual Studio 2013 and is not supported by Microsoft.</span></span> <span data-ttu-id="16105-113">若要下載 Web Essentials，請瀏覽網站， [https://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629)。</span><span class="sxs-lookup"><span data-stu-id="16105-113">To download Web Essentials, visit the website at [https://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629).</span></span> 
  
<span data-ttu-id="16105-114">Web Essentials 提供兩種統合形式：</span><span class="sxs-lookup"><span data-stu-id="16105-114">Web Essentials offers two forms of bundling:</span></span>
  
- <span data-ttu-id="16105-115">.bundle: CSS 和 JavaScript 檔案</span><span class="sxs-lookup"><span data-stu-id="16105-115">.bundle: for CSS and JavaScript files</span></span>
    
- <span data-ttu-id="16105-116">.sprite： 影像 （僅適用於 Visual Studio 2013）</span><span class="sxs-lookup"><span data-stu-id="16105-116">.sprite: for images (only available in Visual Studio 2013)</span></span>
    
<span data-ttu-id="16105-117">您可以使用 Web Essentials，如果您有現有的功能含有一些內自訂的主版頁面，例如參考的品牌元素：</span><span class="sxs-lookup"><span data-stu-id="16105-117">You can use Web Essentials if you have an existing feature with some branding elements that are referenced inside a custom master page, such as:</span></span>
  
![自訂主版頁面中的品牌元素螢幕擷取畫面](media/3a6eba36-973d-482b-8556-a9394b8ba19f.png)
  
 <span data-ttu-id="16105-119">**若要在 Web Essentials 中建立 TE000127218 和 CSS 統合包**</span><span class="sxs-lookup"><span data-stu-id="16105-119">**To create a TE000127218 and CSS bundle in Web Essentials**</span></span>
  
1. <span data-ttu-id="16105-120">在 Visual Studio 中，在 [方案總管] 中，選取您想要併入統合包檔案。</span><span class="sxs-lookup"><span data-stu-id="16105-120">In Visual Studio, in Solution Explorer, select the files that you want to include in the bundle.</span></span>
    
2. <span data-ttu-id="16105-121">以滑鼠右鍵按一下選取的檔案，然後選取 [ **Web Essentials** \> **建立 JavaScript 統合包檔案**從快顯功能表。</span><span class="sxs-lookup"><span data-stu-id="16105-121">Right-click the selected files and then select **Web Essentials** \> **Create JavaScript bundle file** from the context menu.</span></span> <span data-ttu-id="16105-122">例如：</span><span class="sxs-lookup"><span data-stu-id="16105-122">For example:</span></span> 
    
    ![顯示 Web 基本功能功能表選項的螢幕擷取畫面](media/41aac84c-4538-4f78-b454-46e651f868a3.png)
  
## <a name="viewing-the-results-of-bundling-javascript-and-css-files"></a><span data-ttu-id="16105-124">檢視統合 JavaScript 和 CSS 檔案的結果</span><span class="sxs-lookup"><span data-stu-id="16105-124">Viewing the results of bundling JavaScript and CSS files</span></span>

<span data-ttu-id="16105-125">當您建立 JavaScript 和 CSS 統合包時，Web Essentials 會建立名為識別 JavaScript 及 CSS 檔案，以及一些其他組態資訊配方檔的 XML 檔案：</span><span class="sxs-lookup"><span data-stu-id="16105-125">When you create a JavaScript and CSS bundle, Web Essentials creates an XML file called a recipe file that identifies the JavaScript and CSS files as well as some other configuration information:</span></span> 
  
![JavaScript 和 CSS 配方檔的螢幕擷取畫面](media/7ba891f8-52d8-467b-a0f6-b062dd1137a4.png)
  
<span data-ttu-id="16105-127">此外，如果 minify 旗標設定為 true 中統合配方檔的大小，以及一起降低。</span><span class="sxs-lookup"><span data-stu-id="16105-127">In addition, if the minify flag is set to true in the bundling recipe the files are reduced in size as well as bundled together.</span></span> <span data-ttu-id="16105-128">這表示已建立您可以參照您主版頁面中的 JavaScript 檔案的新、 minified 版本。</span><span class="sxs-lookup"><span data-stu-id="16105-128">This means that new, minified versions of the JavaScript files were created that you can reference in your master page.</span></span>
  
![Minify 旗標設定為 true 的螢幕擷取畫面](media/50523af2-6412-4117-ac3d-5bd26f6d562e.png)
  
<span data-ttu-id="16105-130">當您從網站載入頁面時，您可用於開發人員工具從網頁瀏覽器，例如 Internet Explorer 11，請參閱傳送至伺服器] 與 [多久每個檔案所需載入的要求數目。</span><span class="sxs-lookup"><span data-stu-id="16105-130">When you load a page from your web site, you can use the developer tools from your web browser, such as Internet Explorer 11, to see the number of requests sent to the server and how long each file took to load.</span></span>
  
<span data-ttu-id="16105-131">下圖是載入 JavaScript 和 CSS 檔案的縮製前的結果。</span><span class="sxs-lookup"><span data-stu-id="16105-131">The following figure is the result of loading the JavaScript and CSS files before minification.</span></span>
  
![顯示正在下載 80 個項目的螢幕擷取畫面](media/e2df3912-1923-46e6-8cf2-3015a31554e1.png)
  
<span data-ttu-id="16105-133">之後一起統合 CSS 和 JavaScript 檔案，要求數目下降至 74 與每個檔案只需要稍微超過個別下載原始檔案：</span><span class="sxs-lookup"><span data-stu-id="16105-133">After bundling the CSS and JavaScript files together, the number of requests dropped to 74 and each file took only slightly longer than the original files to download individually:</span></span>
  
![顯示正在下載 74 個項目的螢幕擷取畫面](media/686c4387-70e8-4a74-9d45-059f33a91184.png)
  
<span data-ttu-id="16105-135">統合後，JavaScript 統合包檔案會從 815kb 大幅減少到 365KB:</span><span class="sxs-lookup"><span data-stu-id="16105-135">After bundling, the JavaScript bundle file is reduced significantly from 815KB to 365KB:</span></span>
  
![顯示降低下載大小的螢幕擷取畫面](media/5e7dbd98-faff-4f68-b320-108fb252e395.png)
  
## <a name="bundling-images-by-creating-an-image-sprite"></a><span data-ttu-id="16105-137">建立影像精靈來統合影像</span><span class="sxs-lookup"><span data-stu-id="16105-137">Bundling images by creating an image sprite</span></span>

<span data-ttu-id="16105-138">類似於如何將彙整 JavaScript 及 CSS 檔案，您可以將許多小型圖示和其他一般影像合併到較大的小精靈工作表，然後使用 CSS 來顯示個別的影像。</span><span class="sxs-lookup"><span data-stu-id="16105-138">Similar to how you bundle JavaScript and CSS files, you can combine many small icons and other common images into a larger sprite sheet and then use CSS to reveal the individual images.</span></span> <span data-ttu-id="16105-139">而非下載每個個別的影像，使用者的網頁瀏覽器一次下載精靈工作表，並再將其快取的本機電腦上。</span><span class="sxs-lookup"><span data-stu-id="16105-139">Instead of downloading each individual image, the user's web browser downloads the sprite sheet once and then caches it on the local computer.</span></span> <span data-ttu-id="16105-140">這是透過剪下向下的下載套件和網頁伺服器的來回行程數目改善頁面載入效能。</span><span class="sxs-lookup"><span data-stu-id="16105-140">This improves page load performance by cutting down on the number of downloads and round trips to the web server.</span></span>
  
 <span data-ttu-id="16105-141">**若要在 Web Essentials 中建立影像精靈**</span><span class="sxs-lookup"><span data-stu-id="16105-141">**To create an image sprite in Web Essentials**</span></span>
  
1. <span data-ttu-id="16105-142">在 Visual Studio 中，在 [方案總管] 中，選取您想要併入統合包檔案。</span><span class="sxs-lookup"><span data-stu-id="16105-142">In Visual Studio, in Solution Explorer, select the files that you want to include in the bundle.</span></span>
    
2. <span data-ttu-id="16105-143">以滑鼠右鍵按一下選取的檔案，然後選取 [ **Web Essentials** \> **建立影像精靈**從快顯功能表。</span><span class="sxs-lookup"><span data-stu-id="16105-143">Right-click the selected files and then select **Web Essentials** \> **Create image sprite** from the context menu.</span></span> <span data-ttu-id="16105-144">例如：</span><span class="sxs-lookup"><span data-stu-id="16105-144">For example:</span></span> 
    
    ![顯示如何建立影像精靈的螢幕擷取畫面](media/de0fe741-4ef7-4e3b-bafa-ef9f4822dac6.png)
  
3. <span data-ttu-id="16105-146">選擇 [儲存精靈檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="16105-146">Choose a location to save the sprite file.</span></span> <span data-ttu-id="16105-147">.Sprite 檔案是說明設定 XML 檔案和小精靈中的檔案。</span><span class="sxs-lookup"><span data-stu-id="16105-147">The .sprite file is an XML file that describes the settings and files in the sprite.</span></span> <span data-ttu-id="16105-148">下列圖表顯示小精靈 PNG 檔案和其對應的.sprite XML 檔案的範例。</span><span class="sxs-lookup"><span data-stu-id="16105-148">The following figures show an example of a sprite PNG file and its corresponding .sprite XML file.</span></span>
    
    ![精靈檔案的螢幕擷取畫面](media/0876bb2a-d1b9-4169-8e95-9c290d628d90.png)
  
    ![精靈 XML 檔案的螢幕擷取畫面](media/d1f94776-280d-4d56-abb5-384f145d9989.png)
  

