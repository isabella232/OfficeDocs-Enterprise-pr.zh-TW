---
title: 使用與 SharePoint Online 內容傳遞網路
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 5/8/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: 9a64268c-0b74-4eaa-b971-fb6380b1b165
description: 摘要： 本文說明內容傳遞網路 (Cdn) 以及如何使用它們來增加 SharePoint Online 的效能。
ms.openlocfilehash: 63062c08d0c22518eb36ea0a6faa97106fd394b4
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540040"
---
# <a name="using-content-delivery-networks-with-sharepoint-online"></a><span data-ttu-id="578a3-103">使用與 SharePoint Online 內容傳遞網路</span><span class="sxs-lookup"><span data-stu-id="578a3-103">Using content delivery networks with SharePoint Online</span></span>

 <span data-ttu-id="578a3-104">**摘要：** 本文說明內容傳遞網路 (Cdn) 以及如何使用它們來增加 SharePoint Online 的效能。</span><span class="sxs-lookup"><span data-stu-id="578a3-104">**Summary:** This article describes Content Delivery Networks (CDNs) and how you can use them to increase SharePoint Online performance.</span></span> 
  
<span data-ttu-id="578a3-p101">在今天的 web 開發社群，有許多一般文件庫 （例如 JavaScript 和 CSS 檔案） 可能包含在您的 SharePoint 解決方案中。許多這些都架設在其 ASP CDN microsoft。這表示您可以從這些分散式伺服器參照這些文件庫，並允許網際網路的內建 DNS 路由系統以尋找最接近的伺服器到您的使用者。本文範例將示範如何從 SharePoint Online ASP CDN 與伺服器下載常用的文件庫 jQuery 之間的時差是非常重要。使用者也可能已使其不需要下載檔案之本機電腦上快取的 CDN 版本。這可以是重要如果您有分散式全世界和遠從架設 SharePoint Online 網站的資料中心的使用者。</span><span class="sxs-lookup"><span data-stu-id="578a3-p101">In today's web development communities, there are many common libraries (such as JavaScript and CSS files) that you may include in your SharePoint solution. Many of these are hosted by Microsoft on their ASP CDN. This means you can reference these libraries from these distributed servers and allow the internet's built-in DNS routing systems to find the closest server to your user. The examples in this article demonstrate how the time difference between downloading the popular library jQuery from the SharePoint Online server versus the ASP CDN is quite significant. The user also may already have the CDN version cached on the local computer so that they do not have to download the file. This can be important if you have users distributed all over the world and far away from the datacenter that hosts your SharePoint Online site.</span></span>
  
<span data-ttu-id="578a3-p102">建立 SharePoint Online 的頁面時，使用者與 SharePoint Online 執行個體所在位置之間的實體距離會影響延遲時間。這對在全球各地都有據點且網站可能主控於某大洲，但位於世界另一端的使用者在存取其內容的組織尤其重要。CDN 透過在更接近使用者的其他位置主控某些常用網站資產來協助減輕這種情況。</span><span class="sxs-lookup"><span data-stu-id="578a3-p102">When creating pages for SharePoint Online, latency can be affected by the physical distance between your users and the location of the SharePoint Online instance. This is particularly important for organizations that have a global presence where a site may be hosted on one continent while users on the other side of the world are accessing its content. CDNs help mitigate this situation by hosting certain popular web assets in different locations closer to the end users.</span></span>
  
<span data-ttu-id="578a3-p103">由於 CDN 是主控相同檔案的全球伺服器網路，因此儲存於 CDN 上之檔案的網際網路 URL 是由用戶端機器解譯，讓最接近使用者的伺服器提供檔案。這樣的作法能大幅減少網路往返所造成的延遲。</span><span class="sxs-lookup"><span data-stu-id="578a3-p103">Since a CDN is a worldwide network of servers that host the same files, Internet URLs for files stored on the CDNs are interpreted by the client machine so that the server that is closest to the user serves the file. Doing this significantly reduces delays caused by network round trips.</span></span>
  
## <a name="the-challenge-of-hosting-sharepoint-online-sites-for-a-global-audience"></a><span data-ttu-id="578a3-116">為全球目標使用者主控 SharePoint Online 網站所面臨的挑戰</span><span class="sxs-lookup"><span data-stu-id="578a3-116">The challenge of hosting SharePoint Online sites for a global audience</span></span>

<span data-ttu-id="578a3-p104">當您註冊 Office 365 時，SharePoint Online 網站會主控在相對於所選位置 (由使用者指定) 的資料中心。例如，若您的網站是位於美國境內的伺服器上且使用者從東亞地區存取該網站，則可能會因資料必須透過光纖纜線傳送的距離而發生延遲問題。</span><span class="sxs-lookup"><span data-stu-id="578a3-p104">SharePoint Online sites are hosted at datacenters relative to the location (specified by the user) selected when you signed up with Office 365. For example, if your site is on servers in the United States and you have users accessing the site from East Asia, latency issues might arise due to the distance the data has to travel over fiber optic cable.</span></span>
  
<span data-ttu-id="578a3-p105">預設 SharePoint 使用者介面所使用的許多靜態檔案都已經架設 Cdn 的 Microsoft 的全球性網路上。這將可改善效能一段時間。不過，如果您是使用任何常用的 JavaScript 與 CSS 資產 （例如，JQuery、 Modernizr、 啟動安裝或 ASP.NET Ajax） 您可以使用任意可用 Cdn 來改善這些檔案的載入時間。</span><span class="sxs-lookup"><span data-stu-id="578a3-p105">Many static files used by the default SharePoint user interface are already hosted on Microsoft's worldwide network of CDNs. This will improve performance over time. However, if you use any popular JavaScript and CSS assets (for example; JQuery, Modernizr, Bootstrap, or ASP.NET Ajax) you can improve the loading times of these files by using freely available CDNs.</span></span>
  
## <a name="advantages-of-using-cdns-to-improve-download-speed"></a><span data-ttu-id="578a3-122">使用 CDN 改善下載速度的優點</span><span class="sxs-lookup"><span data-stu-id="578a3-122">Advantages of using CDNs to improve download speed</span></span>

<span data-ttu-id="578a3-p106">使用 Cdn 可以改善原因而各種不同的頁面載入的時間。其中一個原因是 CDN 與使用者之間的距離可能會小於到 SharePoint Online 的執行個體之間的距離。這些網路高度分散式和設計也用來讓更高可用性及回應時間。其他原因而是如果您使用的熱門的 CSS 檔案的文件庫、 CDN 搭配，使用者可能已經具備 「 快取的文件庫並將它們即使不再需要完全下載。</span><span class="sxs-lookup"><span data-stu-id="578a3-p106">Using CDNs can improve page load times for a variety of reasons. One reason is that the distance between the CDN and the user may be shorter than the distance to the SharePoint Online instance. These networks are highly distributed and are also designed to have very high availability and response times. Another reason is that if you are using a popular library of CSS files, in conjunction with a CDN, the user may already have the library cached and they won't even need to download it at all.</span></span>
  
<span data-ttu-id="578a3-p107">下列螢幕擷取畫面說明使用 Cdn 的優點。下列螢幕擷取畫面是來自 [**網路**] 索引標籤中的 Internet Explorer 11 開發人員工具。下列螢幕擷取畫面顯示在常用的文件庫 jQuery 延遲。若要以相反此畫面中，Internet Explorer 中按下**F12**然後選取 [Wi-fi 圖示來表示 [**網路**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="578a3-p107">The following screen shots illustrate the advantages of using CDNs. These screen shots are from the **Network** tab in the Internet Explorer 11 developer tools. These screen shots show the latency on the popular library jQuery. To bring up this screen, in Internet Explorer, press **F12** and select the **Network** tab which is symbolized with a Wi-Fi icon.</span></span> 
  
![F12 網路的螢幕擷取畫面](media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
<span data-ttu-id="578a3-p108">這個螢幕擷取畫面顯示上傳至 SharePoint Online 網站本身主版頁面圖庫的文件庫。上傳文件庫所花的時間為 1.51 秒數。</span><span class="sxs-lookup"><span data-stu-id="578a3-p108">This screen shot shows the library uploaded to the master page gallery on the SharePoint Online site itself. The time it took to upload the library is 1.51 seconds.</span></span>
  
![載入時間為 1.51 秒的螢幕擷取畫面](media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
<span data-ttu-id="578a3-p109">第二個的螢幕擷取畫面顯示由 Microsoft 所傳遞的相同檔案 CDN。這個時間延遲是筆 496 （毫秒）。這是大型改進並顯示整個秒 shaved 關閉下載頁面內容的總時間。</span><span class="sxs-lookup"><span data-stu-id="578a3-p109">The second screen shot shows the same file delivered by Microsoft's CDN. This time the latency is around 496 milliseconds. This is a large improvement and shows that a whole second is shaved off the total time to download the page content.</span></span>
  
![載入時間為 469 毫秒的螢幕擷取畫面](media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)
  
## <a name="using-cdns-with-sharepoint-server-2013"></a><span data-ttu-id="578a3-139">搭配 SharePoint Server 2013 使用 CDN</span><span class="sxs-lookup"><span data-stu-id="578a3-139">Using CDNs with SharePoint Server 2013</span></span>

<span data-ttu-id="578a3-p110">使用 Cdn 只有 SharePoint Online 內容中的合理和應避免使用 with SharePoint Server 2013。這是因為所有地理位置周圍的優點請勿保留伺服器是否位於內部部署，則為 true 或依地理位置還是關閉。此外，如果它由主控所在之伺服器的網路連線，然後網站可以搭配使用沒有網際網路連線與因此無法擷取 CDN 檔案。否則，您應該使用 CDN 如果其中一個可用且穩定的文件庫和檔案所需的網站。</span><span class="sxs-lookup"><span data-stu-id="578a3-p110">Using CDNs only makes sense in a SharePoint Online context and should be avoided with SharePoint Server 2013. This is because all of the advantages around geographic location do not hold true if the server is located on-premises or geographically close anyway. Additionally, if there is a network connection to the servers where it's hosted, then the site may be used without an Internet connection and therefore cannot retrieve the CDN files. Otherwise, you should use a CDN if there is one available and stable for the library and files you need for your site.</span></span>
  
## <a name="popular-cdns-and-how-to-use-them"></a><span data-ttu-id="578a3-144">常用 CDN 及其使用方式</span><span class="sxs-lookup"><span data-stu-id="578a3-144">Popular CDNs and how to use them</span></span>

<span data-ttu-id="578a3-145">Microsoft 的 Ajax CDN 提供大部分的常用的文件庫包含 jQuery （和其其他文件庫的所有）、 ASP.NET Ajax、 啟動安裝程式、 Knockout.js、 及其他更多選項。</span><span class="sxs-lookup"><span data-stu-id="578a3-145">Microsoft's Ajax CDN offers most of the popular libraries including jQuery (and all of its other libraries), ASP.NET Ajax, Bootstrap, Knockout.js, and many more.</span></span>
  
<span data-ttu-id="578a3-p111">若要在您的專案中包括這些指令碼，只要將這些公開可用程式庫的參考取代為 CDN 位址的參考即可，而非將其納入您的專案當中。例如，使用下列程式碼連結至 jQuery：</span><span class="sxs-lookup"><span data-stu-id="578a3-p111">To include these scripts in your project, simply replace any references to these publicly available libraries with references to the CDN address instead of including it in your project itself. For example, use the following code to link to jQuery:</span></span>
  
```
<script src=http://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

<span data-ttu-id="578a3-148">如需 Cdn 的詳細資訊，請參閱 ＜[內容傳遞網路](content-delivery-networks.md)。</span><span class="sxs-lookup"><span data-stu-id="578a3-148">For more information about CDNs, see [Content delivery networks](content-delivery-networks.md).</span></span>
  
## <a name="more-topics-about-using-cdns-with-sharepoint"></a><span data-ttu-id="578a3-149">關於使用 Cdn 與 SharePoint 的其他主題</span><span class="sxs-lookup"><span data-stu-id="578a3-149">More topics about using CDNs with SharePoint</span></span>

[<span data-ttu-id="578a3-150">從 Office 365 CDN 主控的用戶端的網頁組件</span><span class="sxs-lookup"><span data-stu-id="578a3-150">Hosting client-side web part from Office 365 CDN</span></span>](https://dev.office.com/sharepoint/docs/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)
  

