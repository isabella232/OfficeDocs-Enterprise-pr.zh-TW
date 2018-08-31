---
title: SharePoint Online 中的縮製及統合技術
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 3/1/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 87a52468-994e-43a2-b155-7229ed659291
description: 本文說明如何使用縮小並搭配 Web Essentials 與技巧 （英文） 以減少的 HTTP 要求數目，並減少在 SharePoint Online 中的頁面載入所花費的時間。
ms.openlocfilehash: edc959e881b0f22b72fba64969e5984f30bce696
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539915"
---
# <a name="minification-and-bundling-in-sharepoint-online"></a><span data-ttu-id="89bbd-103">SharePoint Online 中的縮製及統合技術</span><span class="sxs-lookup"><span data-stu-id="89bbd-103">Minification and bundling in SharePoint Online</span></span>

<span data-ttu-id="89bbd-104">本文說明如何使用縮小並搭配 Web Essentials 與技巧 （英文） 以減少的 HTTP 要求數目，並減少在 SharePoint Online 中的頁面載入所花費的時間。</span><span class="sxs-lookup"><span data-stu-id="89bbd-104">This article describes how to use minification and bundling techniques with Web Essentials to reduce the number of HTTP requests and to reduce the time it takes to load pages in SharePoint Online.</span></span>
  
<span data-ttu-id="89bbd-p101">在自訂網站時，為了支援自訂，您最終可能會將大量額外檔案新增至伺服器。新增額外的 JavaScript、CSS 和影像會增加對伺服器發出的 HTTP 要求數目，進而增加顯示網頁所需要的時間。如果您有多個相同類型的檔案，您可統合這些檔案以讓這些檔案的下載速度更快。</span><span class="sxs-lookup"><span data-stu-id="89bbd-p101">When you customize your website you can end up adding a large number of extra files to the server to support the customization. Adding extra JavaScript, CSS, and images increases the number of HTTP requests to the server which in turn increases the time it takes to display a web page. If you have multiple files of the same type, you can bundle these files to make downloading these files faster.</span></span>
  
<span data-ttu-id="89bbd-108">JavaScript 與 CSS 檔案，您也可以使用稱為縮小，其中移除空白字元和其他不必要的字元降低檔案的總大小方法。</span><span class="sxs-lookup"><span data-stu-id="89bbd-108">For JavaScript and CSS files, you can also use an approach called minification, where you reduce the total size of files by removing whitespace and other characters that aren't necessary.</span></span>
  
## <a name="minification-and-bundling-javascript-and-css-files-with-web-essentials"></a><span data-ttu-id="89bbd-109">透過 Web Essentials 縮製及統合 JavaScript 和 CSS 檔案</span><span class="sxs-lookup"><span data-stu-id="89bbd-109">Minification and bundling JavaScript and CSS files with Web Essentials</span></span>

<span data-ttu-id="89bbd-110">您可使用協力廠商軟體如 Web Essentials 來統合 CSS 和 JavaScript 檔案。</span><span class="sxs-lookup"><span data-stu-id="89bbd-110">You can use third-party software such as Web Essentials to bundle CSS and JavaScript files.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="89bbd-p102">Web Essentials 是協力廠商、 開放原始碼、 社群式專案。軟體是以 Visual Studio 2012 和 Visual Studio 2013 擴充功能與 Microsoft 不支援。若要下載 Web Essentials，請瀏覽網站， [http://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629)。</span><span class="sxs-lookup"><span data-stu-id="89bbd-p102">Web Essentials is a third-party, open-source, community-based project. The software is an extension to Visual Studio 2012 and Visual Studio 2013 and is not supported by Microsoft. To download Web Essentials, visit the website at [http://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629).</span></span> 
  
<span data-ttu-id="89bbd-114">Web Essentials 提供兩種統合形式：</span><span class="sxs-lookup"><span data-stu-id="89bbd-114">Web Essentials offers two forms of bundling:</span></span>
  
- <span data-ttu-id="89bbd-115">.bundle：適用於 CSS 和 JavaScript 檔案</span><span class="sxs-lookup"><span data-stu-id="89bbd-115">.bundle: for CSS and JavaScript files</span></span>
    
- <span data-ttu-id="89bbd-116">.sprite：適用於影像 (僅可在 Visual Studio 2013 中使用)</span><span class="sxs-lookup"><span data-stu-id="89bbd-116">.sprite: for images (only available in Visual Studio 2013)</span></span>
    
<span data-ttu-id="89bbd-117">如果您現有的功能含有一些在自訂主版頁面內參考的品牌項目，您可使用 Web Essentials，例如：</span><span class="sxs-lookup"><span data-stu-id="89bbd-117">You can use Web Essentials if you have an existing feature with some branding elements that are referenced inside a custom master page, such as:</span></span>
  
![自訂主版頁面中的品牌元素螢幕擷取畫面](media/3a6eba36-973d-482b-8556-a9394b8ba19f.png)
  
 <span data-ttu-id="89bbd-119">**在 Web Essentials 中建立 TE000127218 與 CSS 組合**</span><span class="sxs-lookup"><span data-stu-id="89bbd-119">**To create a TE000127218 and CSS bundle in Web Essentials**</span></span>
  
1. <span data-ttu-id="89bbd-120">在 Visual Studio 中，選取方案總管中您要併入統合包中的檔案。</span><span class="sxs-lookup"><span data-stu-id="89bbd-120">In Visual Studio, in Solution Explorer, select the files that you want to include in the bundle.</span></span>
    
2. <span data-ttu-id="89bbd-p103">以滑鼠右鍵按一下選取的檔案，然後選取 [ **Web Essentials** \> **建立 JavaScript 組合檔案**從快顯功能表。例如：</span><span class="sxs-lookup"><span data-stu-id="89bbd-p103">Right-click the selected files and then select **Web Essentials** \> **Create JavaScript bundle file** from the context menu. For example:</span></span> 
    
    ![顯示 Web 基本功能功能表選項的螢幕擷取畫面](media/41aac84c-4538-4f78-b454-46e651f868a3.png)
  
## <a name="viewing-the-results-of-bundling-javascript-and-css-files"></a><span data-ttu-id="89bbd-124">檢視 JavaScript 及 CSS 檔案的統合結果</span><span class="sxs-lookup"><span data-stu-id="89bbd-124">Viewing the results of bundling JavaScript and CSS files</span></span>

<span data-ttu-id="89bbd-125">當您建立 JavaScript 和 CSS 統合包時，Web Essentials 會建立名為配方檔的 XML 檔案，其能識別 JavaScript 與 CSS 檔案及一些其他組態資訊：</span><span class="sxs-lookup"><span data-stu-id="89bbd-125">When you create a JavaScript and CSS bundle, Web Essentials creates an XML file called a recipe file that identifies the JavaScript and CSS files as well as some other configuration information:</span></span> 
  
![JavaScript 和 CSS 配方檔的螢幕擷取畫面](media/7ba891f8-52d8-467b-a0f6-b062dd1137a4.png)
  
<span data-ttu-id="89bbd-p104">此外，如果在統合配方中將 minify 旗標設為 true，則檔案會縮減大小並統合在一起。這表示已建立可在主版頁面中參考的新的縮製版本 JavaScript 檔案。</span><span class="sxs-lookup"><span data-stu-id="89bbd-p104">In addition, if the minify flag is set to true in the bundling recipe the files are reduced in size as well as bundled together. This means that new, minified versions of the JavaScript files were created that you can reference in your master page.</span></span>
  
![Minify 旗標設定為 true 的螢幕擷取畫面](media/50523af2-6412-4117-ac3d-5bd26f6d562e.png)
  
<span data-ttu-id="89bbd-130">當您從網站載入頁面時，您可使用 Internet Explorer 11 等 Web 瀏覽器的開發人員工具，查看傳送至伺服器的要求數目以及每個檔案的所需載入時間。</span><span class="sxs-lookup"><span data-stu-id="89bbd-130">When you load a page from your web site, you can use the developer tools from your web browser, such as Internet Explorer 11, to see the number of requests sent to the server and how long each file took to load.</span></span>
  
<span data-ttu-id="89bbd-131">下圖為縮製前載入 JavaScript 及 CSS 檔案的結果。</span><span class="sxs-lookup"><span data-stu-id="89bbd-131">The following figure is the result of loading the JavaScript and CSS files before minification.</span></span>
  
![顯示正在下載 80 個項目的螢幕擷取畫面](media/e2df3912-1923-46e6-8cf2-3015a31554e1.png)
  
<span data-ttu-id="89bbd-133">將 CSS 和 JavaScript 檔案統合在一起之後，要求數目下降至 74 個且每個檔案所需要的時間只略多於個別下載原始檔案的時間：</span><span class="sxs-lookup"><span data-stu-id="89bbd-133">After bundling the CSS and JavaScript files together, the number of requests dropped to 74 and each file took only slightly longer than the original files to download individually:</span></span>
  
![顯示正在下載 74 個項目的螢幕擷取畫面](media/686c4387-70e8-4a74-9d45-059f33a91184.png)
  
<span data-ttu-id="89bbd-135">統合後，JavaScript 統合包檔案從 815KB 大幅減少到 365KB：</span><span class="sxs-lookup"><span data-stu-id="89bbd-135">After bundling, the JavaScript bundle file is reduced significantly from 815KB to 365KB:</span></span>
  
![顯示降低下載大小的螢幕擷取畫面](media/5e7dbd98-faff-4f68-b320-108fb252e395.png)
  
## <a name="bundling-images-by-creating-an-image-sprite"></a><span data-ttu-id="89bbd-137">建立影像精靈來統合影像</span><span class="sxs-lookup"><span data-stu-id="89bbd-137">Bundling images by creating an image sprite</span></span>

<span data-ttu-id="89bbd-p105">類似如何將彙整 JavaScript 和 CSS 檔案，您可以將許多小型圖示及其他一般圖像結合成較小精靈工作表，然後使用 CSS 顯示個別的圖像。而非下載每個個別的圖像，使用者的網頁瀏覽器中一次下載小精靈工作表，然後快本機電腦上。這頁面負載效能提升剪下向下的下載項目及網頁伺服器的來回數目而定。</span><span class="sxs-lookup"><span data-stu-id="89bbd-p105">Similar to how you bundle JavaScript and CSS files, you can combine many small icons and other common images into a larger sprite sheet and then use CSS to reveal the individual images. Instead of downloading each individual image, the user's web browser downloads the sprite sheet once and then caches it on the local computer. This improves page load performance by cutting down on the number of downloads and round trips to the web server.</span></span>
  
 <span data-ttu-id="89bbd-141">**在 Web Essentials 中建立影像精靈**</span><span class="sxs-lookup"><span data-stu-id="89bbd-141">**To create an image sprite in Web Essentials**</span></span>
  
1. <span data-ttu-id="89bbd-142">在 Visual Studio 中，選取方案總管中您要併入統合包中的檔案。</span><span class="sxs-lookup"><span data-stu-id="89bbd-142">In Visual Studio, in Solution Explorer, select the files that you want to include in the bundle.</span></span>
    
2. <span data-ttu-id="89bbd-p106">以滑鼠右鍵按一下選取的檔案，然後選取 [ **Web Essentials** \> **建立映像小精靈**從快顯功能表。例如：</span><span class="sxs-lookup"><span data-stu-id="89bbd-p106">Right-click the selected files and then select **Web Essentials** \> **Create image sprite** from the context menu. For example:</span></span> 
    
    ![顯示如何建立影像精靈的螢幕擷取畫面](media/de0fe741-4ef7-4e3b-bafa-ef9f4822dac6.png)
  
3. <span data-ttu-id="89bbd-p107">選擇精靈檔案的儲存位置。.sprite 檔案為說明精靈之設定和檔案的 XML 檔案。下圖顯示精靈 PNG 檔案及其對應的 .sprite XML 檔案的範例。</span><span class="sxs-lookup"><span data-stu-id="89bbd-p107">Choose a location to save the sprite file. The .sprite file is an XML file that describes the settings and files in the sprite. The following figures show an example of a sprite PNG file and its corresponding .sprite XML file.</span></span>
    
    ![精靈檔案的螢幕擷取畫面](media/0876bb2a-d1b9-4169-8e95-9c290d628d90.png)
  
    ![精靈 XML 檔案的螢幕擷取畫面](media/d1f94776-280d-4d56-abb5-384f145d9989.png)
  

