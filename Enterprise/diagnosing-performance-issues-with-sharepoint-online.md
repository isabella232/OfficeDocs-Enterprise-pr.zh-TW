---
title: 診斷 SharePoint Online 的效能問題
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 2/23/2018
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 3c364f9e-b9f6-4da4-a792-c8e8c8cd2e86
description: 本文說明您可以如何診斷一般問題與 SharePoint Online 網站使用 Internet Explorer 開發人員工具。
ms.openlocfilehash: 89d4544bfabf6424b5f401bad7d63bd7fa41b5ca
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540084"
---
# <a name="diagnosing-performance-issues-with-sharepoint-online"></a><span data-ttu-id="983f4-103">診斷 SharePoint Online 的效能問題</span><span class="sxs-lookup"><span data-stu-id="983f4-103">Diagnosing performance issues with SharePoint Online</span></span>

<span data-ttu-id="983f4-104">本文說明您可以如何診斷一般問題與 SharePoint Online 網站使用 Internet Explorer 開發人員工具。</span><span class="sxs-lookup"><span data-stu-id="983f4-104">This article shows you how you can diagnose common issues with your SharePoint Online site using Internet Explorer developer tools.</span></span>
  
<span data-ttu-id="983f4-105">有三種不同方法可供識別 SharePoint Online 網站頁面發生自訂效能問題。</span><span class="sxs-lookup"><span data-stu-id="983f4-105">There are three different ways that you can identify that a page on a SharePoint Online site has a performance problem with the customizations.</span></span>
  
- <span data-ttu-id="983f4-106">F12 工具列網路監視器</span><span class="sxs-lookup"><span data-stu-id="983f4-106">The F12 tool bar network monitor</span></span>
    
- <span data-ttu-id="983f4-107">與非自訂基準比較</span><span class="sxs-lookup"><span data-stu-id="983f4-107">Comparison to a non-customized baseline</span></span>
    
- <span data-ttu-id="983f4-108">SharePoint Online 回應標頭度量</span><span class="sxs-lookup"><span data-stu-id="983f4-108">SharePoint Online response header metrics</span></span>
    
<span data-ttu-id="983f4-p101">本主題說明如何使用這些方法來診斷的效能問題。一旦您已經知道問題的原因，您就能使用改進您可以找到的 SharePoint 效能的相關文章方案正面http://aka.ms/tune。</span><span class="sxs-lookup"><span data-stu-id="983f4-p101">This topic describes how to use each of these methods to diagnose performance issues. Once you've figured out the cause of the problem, you can work toward a solution using the articles about improving SharePoint performance that you can find on http://aka.ms/tune.</span></span>
  
## <a name="using-the-f12-tool-bar-to-diagnose-performance-in-sharepoint-online"></a><span data-ttu-id="983f4-111">使用 F12 工具列來診斷 SharePoint Online 中的效能</span><span class="sxs-lookup"><span data-stu-id="983f4-111">Using the F12 tool bar to diagnose performance in SharePoint Online</span></span>
<span data-ttu-id="983f4-112"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="983f4-112"></span></span>

<span data-ttu-id="983f4-p102">在本文中，我們使用 Internet Explorer 11。其他瀏覽器上的 F12 開發人員工具版本有類似功能，但外觀可能稍有不同。如需有關 F12 開發人員工具的資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="983f4-p102">In this article we use Internet Explorer 11. Versions of the F12 developer tools on other browsers have similar features though they may look slightly different. For information on the F12 developer tools, see:</span></span>
  
- [<span data-ttu-id="983f4-116">F12 工具中的新功能</span><span class="sxs-lookup"><span data-stu-id="983f4-116">What's new in F12 Tools</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=522545)
    
- [<span data-ttu-id="983f4-117">使用 F12 開發人員工具</span><span class="sxs-lookup"><span data-stu-id="983f4-117">Using the F12 developer tools</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=522546)
    
<span data-ttu-id="983f4-118">若要顯示開發人員工具，請按 **[F12]**，然後按一下 Wi-Fi 圖示： 
</span><span class="sxs-lookup"><span data-stu-id="983f4-118">To bring up the developer tools press **F12** and then click the Wi-Fi icon:</span></span> 
  
![F12 開發人員工具 WIFI 圖示的螢幕擷取畫面](media/27acacbb-5688-459a-aa2f-5c8c5f17b76e.png)
  
<span data-ttu-id="983f4-p103">在 **[網路]** 索引標籤上，按一下綠色播放按鈕載入頁面。此工具會傳回所有瀏覽器要求的檔案，以取得您需要的頁面。下列螢幕擷取畫面顯示一份此類清單。</span><span class="sxs-lookup"><span data-stu-id="983f4-p103">On the **Network** tab, press the green play button to load a page. The tool returns all of the files that the browser requests in order to get the page you asked for. The following screen shot shows one such list.</span></span> 
  
![使用頁面要求所傳回之檔案清單的螢幕擷取畫面。](media/247a9422-76da-4b0c-bed3-ce77b05e4560.png)
  
<span data-ttu-id="983f4-124">您也可在右邊看到檔案下載時間，如螢幕擷取畫面中所示。</span><span class="sxs-lookup"><span data-stu-id="983f4-124">You can also see the download times of the files on the right side as shown in this screen shot.</span></span>
  
![圖表顯示從 SharePoint 載入要求頁面所需的時間](media/d71ad1fa-9018-4fae-82eb-c1838e7db0ff.png)
  
<span data-ttu-id="983f4-p104">這能讓您以圖形方式看見檔案載入所需時間。綠色線條代表瀏覽器已可呈現頁面。這可讓您快速檢視可能造成網站頁面載入緩慢的不同檔案。

</span><span class="sxs-lookup"><span data-stu-id="983f4-p104">This gives you a visual representation of how long the file took to load. The green line represents when the page is ready to be rendered by the browser. This can give you a quick view of the different files that might be causing slow page loads on your site.</span></span>
  
## <a name="setting-up-a-non-customized-baseline-for-sharepoint-online"></a><span data-ttu-id="983f4-129">設定 SharePoint online 的非自訂的比較基準</span><span class="sxs-lookup"><span data-stu-id="983f4-129">Setting up a non-customized baseline for SharePoint Online</span></span>
<span data-ttu-id="983f4-130"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="983f4-130"></span></span>

<span data-ttu-id="983f4-p105">若要判斷您的網站效能弱式點的最佳方式是設定在 SharePoint Online 中完全--現成的網站集合。這種方式可以比較所有的各個層面與您會收到] 頁面上沒有自訂的網站。OneDrive for Business 的首頁上為良好不太可能會有任何自訂個別網站集合的範例。</span><span class="sxs-lookup"><span data-stu-id="983f4-p105">The best way to determine your site's performance weak points is to set up a completely out-of-the-box site collection in SharePoint Online. This way you can compare all the various aspects of your site with what you would get with no customization on the page. The OneDrive for Business home page is a good example of a separate site collection that is unlikely to have any customizations.</span></span>
  
## <a name="viewing-sharepoint-response-header-information"></a><span data-ttu-id="983f4-134">檢視 SharePoint 回應標頭資訊</span><span class="sxs-lookup"><span data-stu-id="983f4-134">Viewing SharePoint response header information</span></span>
<span data-ttu-id="983f4-135"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="983f4-135"></span></span>

<span data-ttu-id="983f4-p106">在 SharePoint Online 和 SharePoint Server 2013 中，您可以在每個檔案的回應標頭中存取傳回到瀏覽器的資訊。最有用的兩個效能問題診斷值分別是 SPRequestDuration 和 X SharePointHealthScore：</span><span class="sxs-lookup"><span data-stu-id="983f4-p106">In SharePoint Online and SharePoint Server 2013 you can access the information that is sent back to the browser in the response header for each file. The two most useful values for diagnosing performance issues are SPRequestDuration and X-SharePointHealthScore:</span></span>
  
- <span data-ttu-id="983f4-138">**SPRequestDuration**</span><span class="sxs-lookup"><span data-stu-id="983f4-138">**SPRequestDuration**</span></span>
    
    <span data-ttu-id="983f4-p107">這是要求在伺服器上等待處理所花費的時間量。這有助於判斷要求是否非常龐大而需要耗用大量資源。這能讓您確實了解伺服器為服務頁面做了多少事。</span><span class="sxs-lookup"><span data-stu-id="983f4-p107">This is the amount of time that the request took on the server to be processed. This can help determine if the request is very heavy and resource intensive. This is the best insight you have into how much work the server is doing to serve the page.</span></span>
    
- <span data-ttu-id="983f4-142">**X-SharePointHealthScore**</span><span class="sxs-lookup"><span data-stu-id="983f4-142">**X-SharePointHealthScore**</span></span>
    
    <span data-ttu-id="983f4-p108">這會指出伺服器或 CPU、 SharePoint 執行個體執行所在的使用情況。此號碼範圍從 0 到 10 其中 0 表示伺服器處於閒置狀態和 10 指出伺服器是非常忙碌。持續 9 或 10 HealthScore 可能會露出伺服器進行中的效能問題。其他任何數字表示該伺服器作業系統預期的範圍內。</span><span class="sxs-lookup"><span data-stu-id="983f4-p108">This indicates the utilization of the server, or CPU, on which your SharePoint instance runs. This number ranges from 0 to 10 where 0 indicates the server is idle and 10 indicates the server is very busy. A HealthScore that is consistently 9 or 10 might indicate an ongoing performance issue with the server. Any other number indicates that server is operating within the expected range.</span></span>
    
 <span data-ttu-id="983f4-147">**若要檢視 SharePoint 回應標頭資訊**</span><span class="sxs-lookup"><span data-stu-id="983f4-147">**To view SharePoint response header information**</span></span>
  
1. <span data-ttu-id="983f4-p109">請確定您已安裝 F12 工具。如需有關下載並安裝這些工具的詳細資訊，請參閱 ＜ [What's new in F12 工具](https://go.microsoft.com/fwlink/p/?LinkId=522545)。</span><span class="sxs-lookup"><span data-stu-id="983f4-p109">Ensure that you have the F12 tools installed. For more information on downloading and installing these tools, see [What's new in F12 tools](https://go.microsoft.com/fwlink/p/?LinkId=522545).</span></span>
    
2. <span data-ttu-id="983f4-150">在 F12 工具中的 **[網路]** 索引標籤上，按一下綠色播放按鈕載入頁面。</span><span class="sxs-lookup"><span data-stu-id="983f4-150">In the F12 tools, on the **Network** tab, press the green play button to load a page.</span></span> 
    
3. <span data-ttu-id="983f4-151">按一下工具所傳回的其中一個 .aspx 檔案，然後按一下 **[詳細資料]**。</span><span class="sxs-lookup"><span data-stu-id="983f4-151">Click one of the .aspx files returned by the tool and then click **DETAILS**.</span></span> 
    
    ![顯示回應標頭的詳細資料](media/1f8a044a-caf8-4613-be2b-7e064141ac8a.png)
  
4. <span data-ttu-id="983f4-153">按一下 **[回應標頭]**。</span><span class="sxs-lookup"><span data-stu-id="983f4-153">Click **Response headers**.</span></span> 
    
    ![圖表顯示回應標頭的 URL](media/efc7076e-447e-447e-882a-ae3aa721e2c3.png)
  
## <a name="whats-causing-performance-issues-in-sharepoint-online"></a><span data-ttu-id="983f4-155">導致 SharePoint Online 發生效能問題的原因為何？</span><span class="sxs-lookup"><span data-stu-id="983f4-155">What's causing performance issues in SharePoint Online?</span></span>
<span data-ttu-id="983f4-156"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="983f4-156"></span></span>

<span data-ttu-id="983f4-p110">本文[的 SharePoint Online 的導覽選項](navigation-options-for-sharepoint-online.md)顯示範例使用 SPRequestDuration 值來決定複雜的結構化導覽所造成耗時處理伺服器上的頁面。利用 [比較基準網站 （不含自訂） 的值，則有可能決定任何指定的檔案利用載入時間。在 [[導覽選項的 SharePoint Online](navigation-options-for-sharepoint-online.md)中使用的範例是主要.aspx 檔案。該檔案包含大部分的頁面負載執行 ASP.NET 程式碼。根據您所使用的網站範本，這可能是 start.aspx、 home.aspx、 default.aspx 或其他名稱如果您在自訂 [首頁] 頁面。如果此數目是許多高於基準網站，則有某些項目複雜下來您造成效能問題的頁面中的動作的良好指示。</span><span class="sxs-lookup"><span data-stu-id="983f4-p110">The article [Navigation options for SharePoint Online](navigation-options-for-sharepoint-online.md) shows an example of using the SPRequestDuration value to determine that the complicated structural navigation was causing the page to take a long time to process on the server. By taking a value for a baseline site (without customization), it is possible to determine if any given file is taking a long time to load. The example used in [Navigation options for SharePoint Online](navigation-options-for-sharepoint-online.md) is the main .aspx file. That file contains most of the ASP.NET code that runs for your page load. Depending on the site template you use, this could be start.aspx, home.aspx, default.aspx, or another name if you customize the home page. If this number is considerably higher than your baseline site, then it's a good indication that there is something complex going on in your page that is causing performance issues.</span></span> 
  
<span data-ttu-id="983f4-p111">一旦您識別出網站特有的問題，要瞭解效能不佳成因的建議方法是消除所有可能原因 (如頁面自訂)，然後將這些原因逐一新增回網站。一旦您移除了足夠的自訂而使得頁面執行效能良好，您就可逐一將特定自訂項目新增回去。</span><span class="sxs-lookup"><span data-stu-id="983f4-p111">Once you have identified that an issue specific to your site, the recommended way to figure out what is causing poor performance is to eliminate all of the possible causes, like page customizations, and then add them back to the site one by one. Once you have removed enough customizations that the page is performing well, you can then add back specific customizations one by one.</span></span>
  
<span data-ttu-id="983f4-p112">例如，如果您有非常複雜的導覽，請嘗試將導覽變更為不顯示子網站，然後查看開發人員工具以了解這麼做是否有影響。或者如果您有大量累積的內容，請嘗試將其從頁面中移除，看看這麼做是否能改善效能。如果您先去除所有可能原因，再將這些原因逐一加回去，您就能輕鬆識別最大問題所在是哪些功能，然後找出解決方案。 
</span><span class="sxs-lookup"><span data-stu-id="983f4-p112">For example, if you have a very complex navigation try changing the navigation to not show sub-sites then check the developer tools to see if this makes a difference. Or if you have a large amount of content roll-ups try removing them from your page and see if this improves things. If you eliminate all of the possible causes and add them back in one at a time, you can easily identify which features are the biggest problem and then work towards a solution.</span></span>
  

