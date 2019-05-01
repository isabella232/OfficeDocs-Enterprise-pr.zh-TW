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
description: 了解如何使用轉譯和精靈加快來改善您的 SharePoint Online 網站上的影像效能。
ms.openlocfilehash: 313046dec885a38062635254699301bcf556d698
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487351"
---
# <a name="image-optimization-for-sharepoint-online"></a><span data-ttu-id="d2278-103">SharePoint Online 的影像最佳化</span><span class="sxs-lookup"><span data-stu-id="d2278-103">Image optimization for SharePoint Online</span></span>

<span data-ttu-id="d2278-104">網頁載入執行速度取決於呈現包括影像、 HTML、 JavaScript 和 CSS] 頁面上所需要的所有元件的總計大小。</span><span class="sxs-lookup"><span data-stu-id="d2278-104">The loading speed of a webpage depends on the combined size of all the components required to render the page including images, HTML, JavaScript, and CSS.</span></span> <span data-ttu-id="d2278-105">影像很棒的方法讓您的網站更吸引人，但其大小可能會影響效能。</span><span class="sxs-lookup"><span data-stu-id="d2278-105">Images are a great way to make your site more appealing, but their size can affect performance.</span></span> <span data-ttu-id="d2278-106">最佳化您的影像壓縮和調整大小，以及使用精靈加快，您可以位移龐大的影像的效果。</span><span class="sxs-lookup"><span data-stu-id="d2278-106">By optimizing your images with compression and resizing, and using sprites, you can offset the effects of very large images.</span></span> <span data-ttu-id="d2278-107">使用 SharePoint 影像轉譯，您可以上傳單一大型圖像，並顯示讓它可重複使用，而非重新載入之圖像的章節。</span><span class="sxs-lookup"><span data-stu-id="d2278-107">Using SharePoint image renditions, you can upload a single large image, and display sections of the image allowing it to be reused rather than reloaded.</span></span>
  
## <a name="using-sprites-to-speed-up-image-loading-in-sharepoint-online"></a><span data-ttu-id="d2278-108">使用精靈加快 SharePoint Online 中的影像載入速度</span><span class="sxs-lookup"><span data-stu-id="d2278-108">Using sprites to speed up image loading in SharePoint Online</span></span>

|||
|:-----|:-----|
| <span data-ttu-id="d2278-109">影像精靈包含多個較小的圖像。</span><span class="sxs-lookup"><span data-stu-id="d2278-109">An image sprite contains many smaller images.</span></span> <span data-ttu-id="d2278-110">使用 CSS 您選取要與絕對位置] 頁面上的特定組件上顯示的複合圖像的一部分。</span><span class="sxs-lookup"><span data-stu-id="d2278-110">Using CSS you select a part of the composite image to display on a particular part of the page with absolute positioning.</span></span> <span data-ttu-id="d2278-111">基本上，您將移動的單一的圖像，而不是載入多個影像，頁面四周並對該圖像的一小部分可見透過其中精靈影像的必要組件會顯示在小型視窗使用者。</span><span class="sxs-lookup"><span data-stu-id="d2278-111">Basically, you move a single image around the page instead of loading multiple images, and make a small part of that image visible through a small window where the required part of the sprite image is shown to the end user.</span></span> <span data-ttu-id="d2278-112">SharePoint Online 使用精靈加快其各種圖示中顯示精靈 spcommon.png。</span><span class="sxs-lookup"><span data-stu-id="d2278-112">SharePoint Online uses sprites to display its various icons in the sprite spcommon.png.</span></span>  <br/>  <span data-ttu-id="d2278-113">涵蓋了以下：</span><span class="sxs-lookup"><span data-stu-id="d2278-113">What's covered here:</span></span>  <br/>  <span data-ttu-id="d2278-114">影像壓縮</span><span class="sxs-lookup"><span data-stu-id="d2278-114">Image compression</span></span>  <br/>  <span data-ttu-id="d2278-115">影像最佳化</span><span class="sxs-lookup"><span data-stu-id="d2278-115">Image optimization</span></span>  <br/>  <span data-ttu-id="d2278-116">SharePoint 影像轉譯</span><span class="sxs-lookup"><span data-stu-id="d2278-116">SharePoint image renditions</span></span>  <br/> |![Spcommon 的螢幕擷取畫面](media/cc5cdee1-8e54-4537-9a8a-8854f4ee849f.png)|
   
<span data-ttu-id="d2278-118">這可以提升效能，因為您下載只有一個圖像，而不是數個然後快取和重複使用該影像。</span><span class="sxs-lookup"><span data-stu-id="d2278-118">This can increase performance because you download only one image instead of several and then cache and reuse that image.</span></span> <span data-ttu-id="d2278-119">即使映像不維持不快取，所需要的單一的圖像，而不是多個影像，此方法可減少伺服器來減少頁面載入時間的 HTTP 要求總數。</span><span class="sxs-lookup"><span data-stu-id="d2278-119">Even if the image does not remain cached, by having a single image instead of multiple images, this method reduces the total number of HTTP requests to the server which will reduce page loading times.</span></span> <span data-ttu-id="d2278-120">這確實是一種統合影像。</span><span class="sxs-lookup"><span data-stu-id="d2278-120">This is really a form of image bundling.</span></span> <span data-ttu-id="d2278-121">這是很有用技術如果影像不會變更通常，例如圖示，上面所提供的 SharePoint 範例所示。</span><span class="sxs-lookup"><span data-stu-id="d2278-121">This is a very useful technique if the images are not changing very often, for example, icons, as shown in the SharePoint example provided above.</span></span> <span data-ttu-id="d2278-122">您可以如何使用[Web Essentials](http://vswebessentials.com/)，來達成這個目的輕鬆地在 Microsoft Visual Studio 中的第三方、 開放原始碼、 社群式專案。</span><span class="sxs-lookup"><span data-stu-id="d2278-122">You can how to use [Web Essentials](http://vswebessentials.com/), a third-party, open-source, community-based project to achieve this easily in Microsoft Visual Studio.</span></span> <span data-ttu-id="d2278-123">如需詳細資訊，請參閱[縮製及統合在 SharePoint Online 中](https://go.microsoft.com/fwlink/?LinkId=708698)。</span><span class="sxs-lookup"><span data-stu-id="d2278-123">For more information, see [Minification and bundling in SharePoint Online](https://go.microsoft.com/fwlink/?LinkId=708698).</span></span>
  
## <a name="using-image-compression-and-optimization-to-speed-up-page-loading-in-sharepoint"></a><span data-ttu-id="d2278-124">使用影像壓縮和最佳化以加快 SharePoint 中的頁面載入</span><span class="sxs-lookup"><span data-stu-id="d2278-124">Using image compression and optimization to speed up page loading in SharePoint</span></span>

<span data-ttu-id="d2278-125">影像壓縮和最佳化是關於減少您網站使用的影像的檔案大小。</span><span class="sxs-lookup"><span data-stu-id="d2278-125">Image compression and optimization is about reducing the file size of the images you use on your site.</span></span> <span data-ttu-id="d2278-126">通常，減少圖像的大小最佳的技巧，就是調整為它將可在網站上檢視之最大尺寸圖像的大小。</span><span class="sxs-lookup"><span data-stu-id="d2278-126">Often, the best technique to reduce the size of an image is to resize the image to the maximum dimensions that it will be viewed on the site.</span></span> <span data-ttu-id="d2278-127">在具有比以往可檢視較大圖像是沒有意義。</span><span class="sxs-lookup"><span data-stu-id="d2278-127">There is no sense in having an image larger than it will ever be viewed.</span></span> <span data-ttu-id="d2278-128">確定影像屬於正確使用影像這類編輯器中的維度是頁面的快速又簡單的方法，以減少您大小。</span><span class="sxs-lookup"><span data-stu-id="d2278-128">Making sure images are of the correct dimensions using an image editor is a quick and easy way to reduce the size of your page.</span></span>
  
<span data-ttu-id="d2278-129">圖像會正確的大小下, 一步是以最佳化這些映像的壓縮。</span><span class="sxs-lookup"><span data-stu-id="d2278-129">Once images are the right size, the next step is to optimize the compression of these images.</span></span> <span data-ttu-id="d2278-130">有各種工具可供您使用壓縮和最佳化，包括相片藝廊和協力廠商工具。</span><span class="sxs-lookup"><span data-stu-id="d2278-130">There are various tools available to use for compression and optimization, including Photo Gallery and third-party tools.</span></span> <span data-ttu-id="d2278-131">壓縮的關鍵在於減少檔案大小儘可能不會遺失任何辨別品質的使用者。</span><span class="sxs-lookup"><span data-stu-id="d2278-131">The key to compression is to reduce the file size as much as possible without losing any discernible quality for end users.</span></span> <span data-ttu-id="d2278-132">請確定您測試以確定它們仍好看高畫質顯示在您壓縮的檔案。</span><span class="sxs-lookup"><span data-stu-id="d2278-132">Make sure you test your compressed files on a high-definition display to ensure they will still look good.</span></span>
  
## <a name="speed-up-page-downloads-by-using-sharepoint-image-renditions"></a><span data-ttu-id="d2278-133">使用 SharePoint 影像轉譯加快頁面下載速度</span><span class="sxs-lookup"><span data-stu-id="d2278-133">Speed up page downloads by using SharePoint image renditions</span></span>

<span data-ttu-id="d2278-134">影像轉譯是 SharePoint Online 中，可讓您以提供不同版本的映像根據預先定義的影像維度功能。</span><span class="sxs-lookup"><span data-stu-id="d2278-134">Image renditions are a feature in SharePoint Online that allows you to serve up different versions of images based on pre-defined image dimensions.</span></span> <span data-ttu-id="d2278-135">沒有使用者產生的圖像內容或影像維度，例如寬度和高度所修正網站上的 CSS 時，這是特別重要。</span><span class="sxs-lookup"><span data-stu-id="d2278-135">This is especially important when there is user-generated image content or the image dimensions such as width and height are fixed by the CSS on the site.</span></span> <span data-ttu-id="d2278-136">即使所 CSS 修正映像，完整的解析度影像是仍載入。</span><span class="sxs-lookup"><span data-stu-id="d2278-136">Even if an image is fixed by CSS, the full resolution image is still loaded.</span></span> <span data-ttu-id="d2278-137">在此情況下可藉由使用影像轉譯降低檔案大小。</span><span class="sxs-lookup"><span data-stu-id="d2278-137">In this case the file size can be reduced by using image renditions.</span></span>
  
> [!NOTE]
> <span data-ttu-id="d2278-138">啟用發佈功能時，僅適用於 SharePoint 轉譯。</span><span class="sxs-lookup"><span data-stu-id="d2278-138">Renditions are only available for SharePoint when publishing is enabled.</span></span> <span data-ttu-id="d2278-139">您可以啟用 [設定] 下的發佈\>站台設定\>管理網站功能\>SharePoint Server 發佈。</span><span class="sxs-lookup"><span data-stu-id="d2278-139">You can enable publishing under Settings \> Site Settings \> Manage site features \> SharePoint Server Publishing.</span></span> <span data-ttu-id="d2278-140">否則不會出現 [] 選項。</span><span class="sxs-lookup"><span data-stu-id="d2278-140">The option will not appear otherwise.</span></span> 
  
<span data-ttu-id="d2278-141">您定義的最小維度 = 389917 調整 works 影像轉譯，不論是寬度或高度與然後調整影像大小，以便與其他維度自動調整大小根據鎖定長寬比例。</span><span class="sxs-lookup"><span data-stu-id="d2278-141">The image rendition resizing works by taking the smallest dimension you define, either width or height, and then resizing the image so that the other dimension is automatically resized based on the locked aspect ratio.</span></span> <span data-ttu-id="d2278-142">根據預設，它將剩餘的維度裁剪圖像的中心點。</span><span class="sxs-lookup"><span data-stu-id="d2278-142">By default, it will crop the image from the center by the remaining dimensions.</span></span> <span data-ttu-id="d2278-143">例如，如果您定義 100px 寬及 50px 高及您原始映像的轉譯為 1000px 寬及 800px 高，它將會調整大小，使 800px 維度現在是 50px 和 1000px 維度 (現在 62.5px) 裁剪之圖像的中心。</span><span class="sxs-lookup"><span data-stu-id="d2278-143">For example, if you define a rendition of 100px wide and 50px high and your original image is 1000px wide and 800px high, it will be resized so that the 800px dimension is now 50px and the 1000px dimension (now 62.5px) is cropped from the center of the image.</span></span>
  
<span data-ttu-id="d2278-144">是相當簡單的步驟，但若要使用的轉譯的影像，轉譯需要在 SharePoint 網站上，才能新增影像。</span><span class="sxs-lookup"><span data-stu-id="d2278-144">The steps are relatively simple but for images to use the renditions, the renditions need to be on the SharePoint site before you add the images.</span></span> <span data-ttu-id="d2278-145">此外，您也需要有開啟的 SharePoint Server 發佈 （網站層級） 功能與 SharePoint Server 發佈基礎結構 （網站集合層級）。</span><span class="sxs-lookup"><span data-stu-id="d2278-145">In addition, you also need to have the SharePoint Server Publishing Infrastructure (Site Collection Level) and SharePoint Server Publishing (Site Level) features turned on.</span></span>
  
 <span data-ttu-id="d2278-146">**新增影像轉譯以加快載入頁面**</span><span class="sxs-lookup"><span data-stu-id="d2278-146">**Add an image rendition to speed up page loading**</span></span>
  
1. <span data-ttu-id="d2278-147">確認執行此程序的使用者帳戶具備，在最低限度下，最上層網站的 「 設計 」 權限，網站集合，並且網站要發佈至網頁。</span><span class="sxs-lookup"><span data-stu-id="d2278-147">Verify that the user account that is performing this procedure has, at minimum, Design permissions to the top-level site of the site collection, and that the site is being published to a webpage.</span></span>
    
2. <span data-ttu-id="d2278-148">在網頁瀏覽器中，移至發佈網站集合的頂層網站。</span><span class="sxs-lookup"><span data-stu-id="d2278-148">In a web browser, go to the top-level site of the publishing site collection.</span></span>
    
3. <span data-ttu-id="d2278-149">選擇 [**設定**] 圖示。</span><span class="sxs-lookup"><span data-stu-id="d2278-149">Choose the **Settings** icon.</span></span> 
    
4. <span data-ttu-id="d2278-150">在**網站設定**] 頁面的 [**外觀與風格**] 區段中，您會看到內建的影像轉譯。</span><span class="sxs-lookup"><span data-stu-id="d2278-150">On the **Site Settings** page, in the **Look and Feel** section, you will see the built-in image renditions.</span></span> 
    
    <span data-ttu-id="d2278-151">您可以使用現成可用的轉譯或選擇 [**影像轉譯**] 來建立一個新。</span><span class="sxs-lookup"><span data-stu-id="d2278-151">You can use the out of the box renditions or choose **Image Renditions** to create a new one.</span></span> 
    
    ![影像轉譯的螢幕擷取畫面](media/eaae0d53-657d-47ef-b687-65c5167eae4d.PNG)
  
5. <span data-ttu-id="d2278-153">在 [**影像轉譯**] 頁面上，選擇 [**新增項目**。</span><span class="sxs-lookup"><span data-stu-id="d2278-153">On the **Image Renditions** page, choose **Add new item**.</span></span>
    
    ![新增項目的螢幕擷取畫面](media/8cede22e-52bf-4d9d-99cb-162f2f6ce92b.PNG)
  
6. <span data-ttu-id="d2278-155">在 [**新影像轉譯**] 頁面上，在 [**名稱**] 方塊中，輸入轉譯名稱。</span><span class="sxs-lookup"><span data-stu-id="d2278-155">On the **New Image Rendition** page, in the **Name** box, enter a name for the rendition.</span></span> 
    
7. <span data-ttu-id="d2278-156">中**寬度**和**高度**] 文字方塊中，輸入的寬度和高度，以像素，轉譯，然後選擇 [**儲存**。</span><span class="sxs-lookup"><span data-stu-id="d2278-156">In the **Width** and **Height** text boxes, enter the width and height, in pixels, of the rendition, and then choose **Save**.</span></span>
    
    ![影像轉譯名稱的螢幕擷取畫面](media/5a6119ed-c163-40df-a4db-ec629d15607d.PNG)
  
## <a name="custom-cropping-with-image-renditions-in-sharepoint"></a><span data-ttu-id="d2278-158">SharePoint 中影像轉譯的自訂裁剪</span><span class="sxs-lookup"><span data-stu-id="d2278-158">Custom cropping with image renditions in SharePoint</span></span>

<span data-ttu-id="d2278-159">根據預設，從之圖像的中心產生影像轉譯。</span><span class="sxs-lookup"><span data-stu-id="d2278-159">By default, an image rendition is generated from the center of the image.</span></span> <span data-ttu-id="d2278-160">您可以調整個別圖像影像轉譯的部分您想要使用之圖像的裁剪。</span><span class="sxs-lookup"><span data-stu-id="d2278-160">You can adjust the image rendition for individual images by cropping the portion of the image that you want to use.</span></span> <span data-ttu-id="d2278-161">您可以裁剪個別，每個轉譯的影像。</span><span class="sxs-lookup"><span data-stu-id="d2278-161">You can crop the images on an individual basis, per rendition.</span></span> <span data-ttu-id="d2278-162">裁剪影像會加快頁面載入藉由使用 SharePoint 的 blob 快取建立的每個轉譯的影像版本。</span><span class="sxs-lookup"><span data-stu-id="d2278-162">Cropping the images speeds up page loading by using SharePoint's blob cache to create a version of the image for each rendition.</span></span> <span data-ttu-id="d2278-163">如此一來伺服器負載會減少，因為圖像只調整大小時一次，並再已準備好要提供給使用者多次。</span><span class="sxs-lookup"><span data-stu-id="d2278-163">This way the server load is reduced because the image is only resized once and is then ready to serve to end users multiple times.</span></span> <span data-ttu-id="d2278-164">如需有關如何裁剪影像轉譯的詳細資訊，請參閱[裁剪影像轉譯](https://go.microsoft.com/fwlink/p/?LinkId=525626)。</span><span class="sxs-lookup"><span data-stu-id="d2278-164">For more information on how to crop an image rendition, see [Crop an image rendition](https://go.microsoft.com/fwlink/p/?LinkId=525626).</span></span>
  

