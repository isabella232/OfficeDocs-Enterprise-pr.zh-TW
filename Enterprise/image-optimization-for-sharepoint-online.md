---
title: SharePoint Online 的影像最佳化
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/19/2018
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c7edb02a-fdab-4f91-9a20-cba01dad28ef
description: 了解如何使用轉譯和小精靈來提升您的 SharePoint Online 網站上的圖像效能。
ms.openlocfilehash: 313046dec885a38062635254699301bcf556d698
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539950"
---
# <a name="image-optimization-for-sharepoint-online"></a><span data-ttu-id="5bf37-103">SharePoint Online 的影像最佳化</span><span class="sxs-lookup"><span data-stu-id="5bf37-103">Image optimization for SharePoint Online</span></span>

<span data-ttu-id="5bf37-p101">網頁載入速度轉譯包括圖像和 HTML、 JavaScript、 CSS] 頁面上所需的所有元件的合併大小而定。圖像是更好的方式進行更多吸引網站，但其大小可能會影響效能。藉由最佳化壓縮及調整大小、 和使用小圖像，您可以位移非常大的影像的效果。您可以使用 SharePoint 影像轉譯上, 傳的單一大型圖像，並顯示讓它可重複使用，而重新載入之圖像的章節。</span><span class="sxs-lookup"><span data-stu-id="5bf37-p101">The loading speed of a webpage depends on the combined size of all the components required to render the page including images, HTML, JavaScript, and CSS. Images are a great way to make your site more appealing, but their size can affect performance. By optimizing your images with compression and resizing, and using sprites, you can offset the effects of very large images. Using SharePoint image renditions, you can upload a single large image, and display sections of the image allowing it to be reused rather than reloaded.</span></span>
  
## <a name="using-sprites-to-speed-up-image-loading-in-sharepoint-online"></a><span data-ttu-id="5bf37-108">使用精靈加快 SharePoint Online 中的影像載入速度</span><span class="sxs-lookup"><span data-stu-id="5bf37-108">Using sprites to speed up image loading in SharePoint Online</span></span>

|||
|:-----|:-----|
| <span data-ttu-id="5bf37-p102">映像小精靈包含許多較小的圖像。使用 CSS 選取要顯示在具有絕對位置] 頁面上的特定部分的複合式圖像的一部分。基本上，您移動單一的圖像，而不是載入多個影像頁面四周並進行該映像小部分可見透過小精靈映像的必要的部分所示的其中一個小視窗以將一般使用者。SharePoint Online 使用小小精靈 spcommon.png 中顯示其各種圖示。</span><span class="sxs-lookup"><span data-stu-id="5bf37-p102">An image sprite contains many smaller images. Using CSS you select a part of the composite image to display on a particular part of the page with absolute positioning. Basically, you move a single image around the page instead of loading multiple images, and make a small part of that image visible through a small window where the required part of the sprite image is shown to the end user. SharePoint Online uses sprites to display its various icons in the sprite spcommon.png.</span></span>  <br/>  <span data-ttu-id="5bf37-113">此處所涵蓋項目：</span><span class="sxs-lookup"><span data-stu-id="5bf37-113">What's covered here:</span></span>  <br/>  <span data-ttu-id="5bf37-114">影像壓縮</span><span class="sxs-lookup"><span data-stu-id="5bf37-114">Image compression</span></span>  <br/>  <span data-ttu-id="5bf37-115">圖像最佳化</span><span class="sxs-lookup"><span data-stu-id="5bf37-115">Image optimization</span></span>  <br/>  <span data-ttu-id="5bf37-116">SharePoint 圖像轉譯</span><span class="sxs-lookup"><span data-stu-id="5bf37-116">SharePoint image renditions</span></span>  <br/> |![Spcommon 的螢幕擷取畫面](media/cc5cdee1-8e54-4537-9a8a-8854f4ee849f.png)|
   
<span data-ttu-id="5bf37-p103">因為您下載而不是數個只有一個圖像，然後快取及重複使用的圖像加重效能。即使映像不維持不快取，藉由單一的圖像，而不是多個影像，此方法可減少伺服器來減少頁面載入時間的 HTTP 要求總數。這是真正的圖像正在連結。這是非常有用的技巧如果圖像不變更經常，例如圖示，上面所提供的 SharePoint 範例所示。您可以使用[Web Essentials](http://vswebessentials.com/)，若要達到此輕鬆地在 Microsoft Visual Studio 的協力廠商、 開放原始碼、 社群式專案的方式。如需詳細資訊，請參閱[縮小和 SharePoint Online 中正在連結](https://go.microsoft.com/fwlink/?LinkId=708698)。</span><span class="sxs-lookup"><span data-stu-id="5bf37-p103">This can increase performance because you download only one image instead of several and then cache and reuse that image. Even if the image does not remain cached, by having a single image instead of multiple images, this method reduces the total number of HTTP requests to the server which will reduce page loading times. This is really a form of image bundling. This is a very useful technique if the images are not changing very often, for example, icons, as shown in the SharePoint example provided above. You can how to use [Web Essentials](http://vswebessentials.com/), a third-party, open-source, community-based project to achieve this easily in Microsoft Visual Studio. For more information, see [Minification and bundling in SharePoint Online](https://go.microsoft.com/fwlink/?LinkId=708698).</span></span>
  
## <a name="using-image-compression-and-optimization-to-speed-up-page-loading-in-sharepoint"></a><span data-ttu-id="5bf37-124">使用影像壓縮和最佳化以加快 SharePoint 中的頁面載入速度</span><span class="sxs-lookup"><span data-stu-id="5bf37-124">Using image compression and optimization to speed up page loading in SharePoint</span></span>

<span data-ttu-id="5bf37-p104">影像壓縮和最佳化是要減少您在網站上使用的影像檔案大小。要縮小影像大小，最好的方法通常是將影像調整為可在網站上看清楚的最大尺寸。讓影像大於可以看清楚的尺寸毫無意義。使用影像編輯器確保影像有正確尺寸是快速又簡單的頁面大小縮減方式。</span><span class="sxs-lookup"><span data-stu-id="5bf37-p104">Image compression and optimization is about reducing the file size of the images you use on your site. Often, the best technique to reduce the size of an image is to resize the image to the maximum dimensions that it will be viewed on the site. There is no sense in having an image larger than it will ever be viewed. Making sure images are of the correct dimensions using an image editor is a quick and easy way to reduce the size of your page.</span></span>
  
<span data-ttu-id="5bf37-p105">一旦圖像的右邊的大小下, 一步是以最佳化的這些影像壓縮。有各種工具可用於壓縮及最佳化，包括相片藝廊和協力廠商工具。要壓縮的索引鍵是不含適用於使用者遺失任何差別品質降低儘可能的檔案大小。請確定您測試以確定它們仍美觀高畫質顯示您壓縮的檔案。</span><span class="sxs-lookup"><span data-stu-id="5bf37-p105">Once images are the right size, the next step is to optimize the compression of these images. There are various tools available to use for compression and optimization, including Photo Gallery and third-party tools. The key to compression is to reduce the file size as much as possible without losing any discernible quality for end users. Make sure you test your compressed files on a high-definition display to ensure they will still look good.</span></span>
  
## <a name="speed-up-page-downloads-by-using-sharepoint-image-renditions"></a><span data-ttu-id="5bf37-133">使用 SharePoint 影像轉譯加快頁面下載速度</span><span class="sxs-lookup"><span data-stu-id="5bf37-133">Speed up page downloads by using SharePoint image renditions</span></span>

<span data-ttu-id="5bf37-p106">圖像轉譯為 SharePoint Online 中，可讓您以不同版本的預先定義的圖像尺寸為基礎的圖像設定服務的功能。這是特別重要時沒有使用者產生的圖像內容或網站上的 CSS 修正圖像維度例如寬度與高度。即使映像已修正 CSS、 完整的解析度圖像是仍載入。在此例中可藉由使用影像轉譯降低檔案大小。</span><span class="sxs-lookup"><span data-stu-id="5bf37-p106">Image renditions are a feature in SharePoint Online that allows you to serve up different versions of images based on pre-defined image dimensions. This is especially important when there is user-generated image content or the image dimensions such as width and height are fixed by the CSS on the site. Even if an image is fixed by CSS, the full resolution image is still loaded. In this case the file size can be reduced by using image renditions.</span></span>
  
> [!NOTE]
> <span data-ttu-id="5bf37-p107">啟用發佈時，僅可用於 SharePoint 轉譯。您可以啟用 [設定] 下的發佈\>網站設定\>管理網站功能\>SharePoint Server 發佈。否則不會出現的選項。</span><span class="sxs-lookup"><span data-stu-id="5bf37-p107">Renditions are only available for SharePoint when publishing is enabled. You can enable publishing under Settings \> Site Settings \> Manage site features \> SharePoint Server Publishing. The option will not appear otherwise.</span></span> 
  
<span data-ttu-id="5bf37-p108">影像轉譯在調整大小時，其作用方式會先採用您定義的最小尺寸 (寬度或高度)，然後再調整影像大小，讓另一個尺寸根據鎖定的長寬比自動調整大小。根據預設，它會從影像中心點裁剪下剩餘尺寸大小。例如，如果您定義的轉譯寬 100px、高 50px，而原始影像為寬 1000px、高 800px，那麼影像將會調整大小，原本 800px 的尺寸現在會變成 50px，原本 1000px 的尺寸現在會變成 62.5px，然後從影像中心點裁剪下此大小。</span><span class="sxs-lookup"><span data-stu-id="5bf37-p108">The image rendition resizing works by taking the smallest dimension you define, either width or height, and then resizing the image so that the other dimension is automatically resized based on the locked aspect ratio. By default, it will crop the image from the center by the remaining dimensions. For example, if you define a rendition of 100px wide and 50px high and your original image is 1000px wide and 800px high, it will be resized so that the 800px dimension is now 50px and the 1000px dimension (now 62.5px) is cropped from the center of the image.</span></span>
  
<span data-ttu-id="5bf37-p109">步驟相當簡單，但想要讓影像使用轉譯，您必須在新增影像前，先在 SharePoint 網站上定義好轉譯。此外，您也需要開啟 SharePoint Server 發佈基礎結構 (網站集合層級) 和 SharePoint Server 發佈 (網站層級) 功能。</span><span class="sxs-lookup"><span data-stu-id="5bf37-p109">The steps are relatively simple but for images to use the renditions, the renditions need to be on the SharePoint site before you add the images. In addition, you also need to have the SharePoint Server Publishing Infrastructure (Site Collection Level) and SharePoint Server Publishing (Site Level) features turned on.</span></span>
  
 <span data-ttu-id="5bf37-146">**新增以加速頁面載入影像轉譯**</span><span class="sxs-lookup"><span data-stu-id="5bf37-146">**Add an image rendition to speed up page loading**</span></span>
  
1. <span data-ttu-id="5bf37-147">確認執行此程序的使用者帳戶具有，在最小值、 最上層網站的 「 設計 」 權限的網站集合] 並網站要發佈至網頁。</span><span class="sxs-lookup"><span data-stu-id="5bf37-147">Verify that the user account that is performing this procedure has, at minimum, Design permissions to the top-level site of the site collection, and that the site is being published to a webpage.</span></span>
    
2. <span data-ttu-id="5bf37-148">在網頁瀏覽器中，移至發佈網站集合的頂層網站。</span><span class="sxs-lookup"><span data-stu-id="5bf37-148">In a web browser, go to the top-level site of the publishing site collection.</span></span>
    
3. <span data-ttu-id="5bf37-149">選擇 **[設定]** 圖示。</span><span class="sxs-lookup"><span data-stu-id="5bf37-149">Choose the **Settings** icon.</span></span> 
    
4. <span data-ttu-id="5bf37-150">在 **[網站設定]** 頁面上，您會在 **[外觀與風格]** 區段中看到內建的影像轉譯。</span><span class="sxs-lookup"><span data-stu-id="5bf37-150">On the **Site Settings** page, in the **Look and Feel** section, you will see the built-in image renditions.</span></span> 
    
    <span data-ttu-id="5bf37-151">您可使用現成可用的轉譯或選擇 **[影像轉譯]** 來建立新的轉譯。</span><span class="sxs-lookup"><span data-stu-id="5bf37-151">You can use the out of the box renditions or choose **Image Renditions** to create a new one.</span></span> 
    
    ![圖像轉譯的螢幕擷取畫面](media/eaae0d53-657d-47ef-b687-65c5167eae4d.PNG)
  
5. <span data-ttu-id="5bf37-153">在 **[影像轉譯]** 頁面上，選擇 **[新增項目]**。</span><span class="sxs-lookup"><span data-stu-id="5bf37-153">On the **Image Renditions** page, choose **Add new item**.</span></span>
    
    ![新增項目的螢幕擷取畫面](media/8cede22e-52bf-4d9d-99cb-162f2f6ce92b.PNG)
  
6. <span data-ttu-id="5bf37-155">在 **[新影像轉譯]** 頁面上的 **[名稱]** 方塊中輸入轉譯名稱。</span><span class="sxs-lookup"><span data-stu-id="5bf37-155">On the **New Image Rendition** page, in the **Name** box, enter a name for the rendition.</span></span> 
    
7. <span data-ttu-id="5bf37-156">在 **[寬度]** 和 **[高度]** 文字方塊中，以像素為單位輸入轉譯的寬度和高度，然後選擇 **[儲存]**。</span><span class="sxs-lookup"><span data-stu-id="5bf37-156">In the **Width** and **Height** text boxes, enter the width and height, in pixels, of the rendition, and then choose **Save**.</span></span>
    
    ![影像轉譯名稱的螢幕擷取畫面](media/5a6119ed-c163-40df-a4db-ec629d15607d.PNG)
  
## <a name="custom-cropping-with-image-renditions-in-sharepoint"></a><span data-ttu-id="5bf37-158">SharePoint 中影像轉譯的自訂裁剪</span><span class="sxs-lookup"><span data-stu-id="5bf37-158">Custom cropping with image renditions in SharePoint</span></span>

<span data-ttu-id="5bf37-p110">根據預設，從之圖像的中心產生圖像轉譯。您可以調整個別圖像圖像轉譯裁剪您想要使用之圖像的部分。您可以裁剪上個別的基礎，每個轉譯的圖像。裁剪圖像加快載入所建立的每個轉譯影像的版本中使用 SharePoint 的 blob 快取的頁面。如此一來伺服器負載會降低因為映像只調整大小時一次，然後可供多次做為一般使用者。如需如何裁剪圖像轉譯的詳細資訊，請參閱[裁剪圖像轉譯](https://go.microsoft.com/fwlink/p/?LinkId=525626)。</span><span class="sxs-lookup"><span data-stu-id="5bf37-p110">By default, an image rendition is generated from the center of the image. You can adjust the image rendition for individual images by cropping the portion of the image that you want to use. You can crop the images on an individual basis, per rendition. Cropping the images speeds up page loading by using SharePoint's blob cache to create a version of the image for each rendition. This way the server load is reduced because the image is only resized once and is then ready to serve to end users multiple times. For more information on how to crop an image rendition, see [Crop an image rendition](https://go.microsoft.com/fwlink/p/?LinkId=525626).</span></span>
  

