---
title: 診斷 SharePoint Online 的效能問題
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 2/23/2018
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 3c364f9e-b9f6-4da4-a792-c8e8c8cd2e86
description: 本文將告訴您如何診斷常見的問題，以及在 SharePoint Online 網站使用 Internet Explorer 開發人員工具。
ms.openlocfilehash: dfc66822a98ce26bfd9fd94d9d58882b8b140831
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067859"
---
# <a name="diagnosing-performance-issues-with-sharepoint-online"></a><span data-ttu-id="f5557-103">診斷 SharePoint Online 的效能問題</span><span class="sxs-lookup"><span data-stu-id="f5557-103">Diagnosing performance issues with SharePoint Online</span></span>

<span data-ttu-id="f5557-104">本文將告訴您如何診斷常見的問題，以及在 SharePoint Online 網站使用 Internet Explorer 開發人員工具。</span><span class="sxs-lookup"><span data-stu-id="f5557-104">This article shows you how you can diagnose common issues with your SharePoint Online site using Internet Explorer developer tools.</span></span>
  
<span data-ttu-id="f5557-105">有三個不同的方式，您可以識別 SharePoint Online 網站上的頁面，具有自訂效能問題。</span><span class="sxs-lookup"><span data-stu-id="f5557-105">There are three different ways that you can identify that a page on a SharePoint Online site has a performance problem with the customizations.</span></span>
  
- <span data-ttu-id="f5557-106">F12 工具列網路監視器</span><span class="sxs-lookup"><span data-stu-id="f5557-106">The F12 tool bar network monitor</span></span>
    
- <span data-ttu-id="f5557-107">非自訂基準比較</span><span class="sxs-lookup"><span data-stu-id="f5557-107">Comparison to a non-customized baseline</span></span>
    
- <span data-ttu-id="f5557-108">SharePoint Online 回應標頭度量</span><span class="sxs-lookup"><span data-stu-id="f5557-108">SharePoint Online response header metrics</span></span>
    
<span data-ttu-id="f5557-109">本主題說明如何使用這些方法來診斷效能問題。</span><span class="sxs-lookup"><span data-stu-id="f5557-109">This topic describes how to use each of these methods to diagnose performance issues.</span></span> <span data-ttu-id="f5557-110">一旦您已猜問題的原因，您就能使用文章提升 SharePoint 效能，您可以在找到解決方案聚集http://aka.ms/tune。</span><span class="sxs-lookup"><span data-stu-id="f5557-110">Once you've figured out the cause of the problem, you can work toward a solution using the articles about improving SharePoint performance that you can find on http://aka.ms/tune.</span></span>
  
## <a name="using-the-f12-tool-bar-to-diagnose-performance-in-sharepoint-online"></a><span data-ttu-id="f5557-111">使用 F12 工具列來診斷 SharePoint Online 中的效能</span><span class="sxs-lookup"><span data-stu-id="f5557-111">Using the F12 tool bar to diagnose performance in SharePoint Online</span></span>
<span data-ttu-id="f5557-112"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="f5557-112"></span></span>

<span data-ttu-id="f5557-113">在本文中，我們使用 Internet Explorer 11。</span><span class="sxs-lookup"><span data-stu-id="f5557-113">In this article we use Internet Explorer 11.</span></span> <span data-ttu-id="f5557-114">版本的 F12 開發人員工具，在其他瀏覽器上具有類似的功能，但是它們看起來可能稍有不同。</span><span class="sxs-lookup"><span data-stu-id="f5557-114">Versions of the F12 developer tools on other browsers have similar features though they may look slightly different.</span></span> <span data-ttu-id="f5557-115">F12 開發人員工具的詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="f5557-115">For information on the F12 developer tools, see:</span></span>
  
- [<span data-ttu-id="f5557-116">What's new in F12 工具</span><span class="sxs-lookup"><span data-stu-id="f5557-116">What's new in F12 Tools</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=522545)
    
- [<span data-ttu-id="f5557-117">使用 F12 開發人員工具</span><span class="sxs-lookup"><span data-stu-id="f5557-117">Using the F12 developer tools</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=522546)
    
<span data-ttu-id="f5557-118">若要顯示開發人員工具按**F12** ，，然後按一下 Wi-fi 圖示：</span><span class="sxs-lookup"><span data-stu-id="f5557-118">To bring up the developer tools press **F12** and then click the Wi-Fi icon:</span></span> 
  
![F12 開發人員工具 WIFI 圖示的螢幕擷取畫面](media/27acacbb-5688-459a-aa2f-5c8c5f17b76e.png)
  
<span data-ttu-id="f5557-120">在 [**網路**] 索引標籤上按下綠色播放按鈕載入頁面。</span><span class="sxs-lookup"><span data-stu-id="f5557-120">On the **Network** tab, press the green play button to load a page.</span></span> <span data-ttu-id="f5557-121">此工具會傳回所有瀏覽器要求以取得您要求] 頁面上的檔案。</span><span class="sxs-lookup"><span data-stu-id="f5557-121">The tool returns all of the files that the browser requests in order to get the page you asked for.</span></span> <span data-ttu-id="f5557-122">下列螢幕擷取畫面顯示一個這類清單。</span><span class="sxs-lookup"><span data-stu-id="f5557-122">The following screen shot shows one such list.</span></span> 
  
![使用頁面要求所傳回之檔案清單的螢幕擷取畫面。](media/247a9422-76da-4b0c-bed3-ce77b05e4560.png)
  
<span data-ttu-id="f5557-124">這個螢幕擷取畫面所示，您也可以查看在右側的檔案下載時間。</span><span class="sxs-lookup"><span data-stu-id="f5557-124">You can also see the download times of the files on the right side as shown in this screen shot.</span></span>
  
![圖表顯示從 SharePoint 載入要求頁面所需的時間](media/d71ad1fa-9018-4fae-82eb-c1838e7db0ff.png)
  
<span data-ttu-id="f5557-126">這可以讓您多久檔案所需載入的視覺表示法。</span><span class="sxs-lookup"><span data-stu-id="f5557-126">This gives you a visual representation of how long the file took to load.</span></span> <span data-ttu-id="f5557-127">綠色行代表可由瀏覽器轉譯頁面時。</span><span class="sxs-lookup"><span data-stu-id="f5557-127">The green line represents when the page is ready to be rendered by the browser.</span></span> <span data-ttu-id="f5557-128">這可讓您快速檢視的可能原因包括速度很慢的頁面載入網站的不同檔案。</span><span class="sxs-lookup"><span data-stu-id="f5557-128">This can give you a quick view of the different files that might be causing slow page loads on your site.</span></span>
  
## <a name="setting-up-a-non-customized-baseline-for-sharepoint-online"></a><span data-ttu-id="f5557-129">設定 SharePoint Online 的非自訂基準</span><span class="sxs-lookup"><span data-stu-id="f5557-129">Setting up a non-customized baseline for SharePoint Online</span></span>
<span data-ttu-id="f5557-130"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="f5557-130"></span></span>

<span data-ttu-id="f5557-131">若要判斷您的網站效能弱式點的最佳方式是設定在 SharePoint Online 中完全--現成的網站集合。</span><span class="sxs-lookup"><span data-stu-id="f5557-131">The best way to determine your site's performance weak points is to set up a completely out-of-the-box site collection in SharePoint Online.</span></span> <span data-ttu-id="f5557-132">如此一來，您可以比較與將得到的結果頁面上沒有自訂網站的所有的各個方面。</span><span class="sxs-lookup"><span data-stu-id="f5557-132">This way you can compare all the various aspects of your site with what you would get with no customization on the page.</span></span> <span data-ttu-id="f5557-133">OneDrive for Business 首頁頁面是很好的範例不太可能會有任何自訂個別網站集合。</span><span class="sxs-lookup"><span data-stu-id="f5557-133">The OneDrive for Business home page is a good example of a separate site collection that is unlikely to have any customizations.</span></span>
  
## <a name="viewing-sharepoint-response-header-information"></a><span data-ttu-id="f5557-134">檢視 SharePoint 回應標頭資訊</span><span class="sxs-lookup"><span data-stu-id="f5557-134">Viewing SharePoint response header information</span></span>
<span data-ttu-id="f5557-135"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="f5557-135"></span></span>

<span data-ttu-id="f5557-136">在 SharePoint Online 和 SharePoint Server 2013 中，您可以存取傳送回的瀏覽器中的每個檔案的回應標頭的資訊。</span><span class="sxs-lookup"><span data-stu-id="f5557-136">In SharePoint Online and SharePoint Server 2013 you can access the information that is sent back to the browser in the response header for each file.</span></span> <span data-ttu-id="f5557-137">SPRequestDuration 和 X SharePointHealthScore 診斷效能問題的兩個最有用值︰</span><span class="sxs-lookup"><span data-stu-id="f5557-137">The two most useful values for diagnosing performance issues are SPRequestDuration and X-SharePointHealthScore:</span></span>
  
- <span data-ttu-id="f5557-138">**SPRequestDuration**</span><span class="sxs-lookup"><span data-stu-id="f5557-138">**SPRequestDuration**</span></span>
    
    <span data-ttu-id="f5557-139">這是時間的要求在伺服器進行處理量。</span><span class="sxs-lookup"><span data-stu-id="f5557-139">This is the amount of time that the request took on the server to be processed.</span></span> <span data-ttu-id="f5557-140">這可協助判斷要求是否非常大量和大量的資源。</span><span class="sxs-lookup"><span data-stu-id="f5557-140">This can help determine if the request is very heavy and resource intensive.</span></span> <span data-ttu-id="f5557-141">這是最佳的深入解析到多少工作有 server 服務] 頁面上所做的動作。</span><span class="sxs-lookup"><span data-stu-id="f5557-141">This is the best insight you have into how much work the server is doing to serve the page.</span></span>
    
- <span data-ttu-id="f5557-142">**X-SharePointHealthScore**</span><span class="sxs-lookup"><span data-stu-id="f5557-142">**X-SharePointHealthScore**</span></span>
    
    <span data-ttu-id="f5557-143">這表示伺服器或您的 SharePoint 執行個體執行所在的 CPU 的使用率。</span><span class="sxs-lookup"><span data-stu-id="f5557-143">This indicates the utilization of the server, or CPU, on which your SharePoint instance runs.</span></span> <span data-ttu-id="f5557-144">此數字的範圍從 0 到 10，其中 0 表示伺服器處於閒置狀態而 10 表示伺服器是非常忙碌。</span><span class="sxs-lookup"><span data-stu-id="f5557-144">This number ranges from 0 to 10 where 0 indicates the server is idle and 10 indicates the server is very busy.</span></span> <span data-ttu-id="f5557-145">持續 9 或 10 HealthScore 可能會指出與伺服器進行中的效能問題。</span><span class="sxs-lookup"><span data-stu-id="f5557-145">A HealthScore that is consistently 9 or 10 might indicate an ongoing performance issue with the server.</span></span> <span data-ttu-id="f5557-146">其他任何數字表示該伺服器作業系統預期的範圍內。</span><span class="sxs-lookup"><span data-stu-id="f5557-146">Any other number indicates that server is operating within the expected range.</span></span>
    
 <span data-ttu-id="f5557-147">**若要檢視 SharePoint 回應標頭資訊**</span><span class="sxs-lookup"><span data-stu-id="f5557-147">**To view SharePoint response header information**</span></span>
  
1. <span data-ttu-id="f5557-148">請確定您已安裝 F12 工具。</span><span class="sxs-lookup"><span data-stu-id="f5557-148">Ensure that you have the F12 tools installed.</span></span> <span data-ttu-id="f5557-149">如需有關下載並安裝這些工具的詳細資訊，請參閱 < <b0>What's new in F12 工具</b0>。</span><span class="sxs-lookup"><span data-stu-id="f5557-149">For more information on downloading and installing these tools, see [What's new in F12 tools](https://go.microsoft.com/fwlink/p/?LinkId=522545).</span></span>
    
2. <span data-ttu-id="f5557-150">在 F12 工具，在 [**網路**] 索引標籤上按綠色播放按鈕載入頁面。</span><span class="sxs-lookup"><span data-stu-id="f5557-150">In the F12 tools, on the **Network** tab, press the green play button to load a page.</span></span> 
    
3. <span data-ttu-id="f5557-151">按一下下列其中一個工具所傳回的.aspx 檔案，然後按一下 [**詳細資料**。</span><span class="sxs-lookup"><span data-stu-id="f5557-151">Click one of the .aspx files returned by the tool and then click **DETAILS**.</span></span> 
    
    ![顯示回應標頭的詳細資料](media/1f8a044a-caf8-4613-be2b-7e064141ac8a.png)
  
4. <span data-ttu-id="f5557-153">按一下 [**回應標頭**]。</span><span class="sxs-lookup"><span data-stu-id="f5557-153">Click **Response headers**.</span></span> 
    
    ![圖表顯示回應標頭的 URL](media/efc7076e-447e-447e-882a-ae3aa721e2c3.png)
  
## <a name="whats-causing-performance-issues-in-sharepoint-online"></a><span data-ttu-id="f5557-155">什麼 SharePoint Online 中導致效能問題？</span><span class="sxs-lookup"><span data-stu-id="f5557-155">What's causing performance issues in SharePoint Online?</span></span>
<span data-ttu-id="f5557-156"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="f5557-156"></span></span>

<span data-ttu-id="f5557-157">[SharePoint Online 的導覽選項](navigation-options-for-sharepoint-online.md)的文章顯示至判斷複雜的結構式導覽所造成要花很長的時間處理程序在伺服器上的頁面使用 SPRequestDuration 值的範例。</span><span class="sxs-lookup"><span data-stu-id="f5557-157">The article [Navigation options for SharePoint Online](navigation-options-for-sharepoint-online.md) shows an example of using the SPRequestDuration value to determine that the complicated structural navigation was causing the page to take a long time to process on the server.</span></span> <span data-ttu-id="f5557-158">= 389917 的值 （不含自訂） 的基準網站，很可能至判斷指定的任何檔案是否正在載入很長的時間。</span><span class="sxs-lookup"><span data-stu-id="f5557-158">By taking a value for a baseline site (without customization), it is possible to determine if any given file is taking a long time to load.</span></span> <span data-ttu-id="f5557-159">[SharePoint Online 的導覽選項](navigation-options-for-sharepoint-online.md)中所使用的範例是主要的.aspx 檔案。</span><span class="sxs-lookup"><span data-stu-id="f5557-159">The example used in [Navigation options for SharePoint Online](navigation-options-for-sharepoint-online.md) is the main .aspx file.</span></span> <span data-ttu-id="f5557-160">該檔案包含大部分的 ASP.NET 程式碼執行您] 頁面上的負載。</span><span class="sxs-lookup"><span data-stu-id="f5557-160">That file contains most of the ASP.NET code that runs for your page load.</span></span> <span data-ttu-id="f5557-161">根據您使用的網站範本，這可能是 start.aspx、 home.aspx、 default.aspx 或另一個名稱如果您自訂 [首頁] 頁面。</span><span class="sxs-lookup"><span data-stu-id="f5557-161">Depending on the site template you use, this could be start.aspx, home.aspx, default.aspx, or another name if you customize the home page.</span></span> <span data-ttu-id="f5557-162">如果此數字是相當高於基準網站，它是很好的指標，還有一些複雜您會造成效能問題的頁面中。</span><span class="sxs-lookup"><span data-stu-id="f5557-162">If this number is considerably higher than your baseline site, then it's a good indication that there is something complex going on in your page that is causing performance issues.</span></span> 
  
<span data-ttu-id="f5557-163">一旦您已識別您網站特有的問題，以找出項目會導致效能不佳的建議的方式是消除所有可能的原因，像是頁面自訂項目，，然後將其新增回網站逐一。</span><span class="sxs-lookup"><span data-stu-id="f5557-163">Once you have identified that an issue specific to your site, the recommended way to figure out what is causing poor performance is to eliminate all of the possible causes, like page customizations, and then add them back to the site one by one.</span></span> <span data-ttu-id="f5557-164">一旦您已移除足夠良好執行 [] 頁面上的自訂，接著您可以新增回特定自訂項目的一個接著一個。</span><span class="sxs-lookup"><span data-stu-id="f5557-164">Once you have removed enough customizations that the page is performing well, you can then add back specific customizations one by one.</span></span>
  
<span data-ttu-id="f5557-165">例如，如果您有非常複雜的導覽會嘗試變更瀏覽至未顯示子網站，然後檢查以查看是否會有不同的開發人員工具。</span><span class="sxs-lookup"><span data-stu-id="f5557-165">For example, if you have a very complex navigation try changing the navigation to not show sub-sites then check the developer tools to see if this makes a difference.</span></span> <span data-ttu-id="f5557-166">如果您有大量的內容彙總套件或嘗試移除程式] 頁面上，並查看如果這樣可以改善項目。</span><span class="sxs-lookup"><span data-stu-id="f5557-166">Or if you have a large amount of content roll-ups try removing them from your page and see if this improves things.</span></span> <span data-ttu-id="f5557-167">如果您關閉所有可能的原因，並將其新增中一次，您可以輕易地識別哪些功能的最大問題以及然後使用向解決方案。</span><span class="sxs-lookup"><span data-stu-id="f5557-167">If you eliminate all of the possible causes and add them back in one at a time, you can easily identify which features are the biggest problem and then work towards a solution.</span></span>
  

