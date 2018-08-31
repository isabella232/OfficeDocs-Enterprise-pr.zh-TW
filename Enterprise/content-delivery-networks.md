---
title: 內容傳遞網路
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/26/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 0140f704-6614-49bb-aa6c-89b75dcd7f1f
description: 使用此資訊以了解內容傳遞網路 (Cdn) 與 Office 365 如何使用它們。Cdn 協助保護使用者的 Office 365 快速且可靠。使用 Cdn，例如 Office 365 雲端服務快速下載一般內容、 like 圖示，至使用者的瀏覽器他們正在使用透過 web 用戶端服務時。
ms.openlocfilehash: bcbab3256a0c1ce601abaf3f8b80e998db4bcece
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540189"
---
# <a name="content-delivery-networks"></a><span data-ttu-id="5440b-105">內容傳遞網路</span><span class="sxs-lookup"><span data-stu-id="5440b-105">Content delivery networks</span></span>

<span data-ttu-id="5440b-p102">使用此資訊以了解內容傳遞網路 (Cdn) 與 Office 365 如何使用它們。Cdn 協助保護使用者的 Office 365 快速且可靠。使用 Cdn，例如 Office 365 雲端服務快速下載一般內容、 like 圖示，至使用者的瀏覽器他們正在使用透過 web 用戶端服務時。</span><span class="sxs-lookup"><span data-stu-id="5440b-p102">Use this information to learn about Content Delivery Networks (CDNs) and how Office 365 leverages them. CDNs help keep Office 365 fast and reliable for end users. With CDNs, cloud services like Office 365 quickly download generic content, like icons, to your users' browser when they're using the service through a web client.</span></span>
  
 <span data-ttu-id="5440b-109">**若要備份的標題**[網路規劃和 Office 365 的效能調整](https://aka.ms/tune)。</span><span class="sxs-lookup"><span data-stu-id="5440b-109">**Head back to**[Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>
  
## <a name="how-should-i-set-up-my-network-so-that-cdns-work-best-with-office-365"></a><span data-ttu-id="5440b-110">如何應設定我的網路才能讓 Cdn 與 Office 365 搭配運作？</span><span class="sxs-lookup"><span data-stu-id="5440b-110">How should I set up my network so that CDNs work best with Office 365?</span></span>

<span data-ttu-id="5440b-p103">如果您打算使用[網路連線至 Office 365](network-connectivity.md)，最好是很有幫助了解 Cdn 的運作方式。它也務必了解您無法使用 IP 位址篩選 Cdn 的連線。我們提供最佳的工作清單的 Ip 在 Office 365，例如 Exchange Online 中的服務。深入了解[管理 Office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)我們建議。</span><span class="sxs-lookup"><span data-stu-id="5440b-p103">If you're planning [Network connectivity to Office 365](network-connectivity.md), it's helpful to understand how CDNs work. It is also important to understand that you can't filter connectivity to the CDNs by IP address. We provide a best effort list of IPs for the services within Office 365, such as Exchange Online. Learn more about our recommendations for [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).</span></span>
  
## <a name="how-do-cdns-make-services-work-faster"></a><span data-ttu-id="5440b-115">CDN 如何讓服務運作得更快？</span><span class="sxs-lookup"><span data-stu-id="5440b-115">How do CDNs make services work faster?</span></span>

<span data-ttu-id="5440b-p104">下載圖示之類的常見反覆可以需要更妥善地可用的下載重要個人的內容，例如電子郵件或文件的網路頻寬。由於 Office 365 使用架構包含 Cdn、 圖示、 指令碼及其他一般內容可從伺服器更接近下載至用戶端電腦，進行下載速度。這表示您個人的內容，其可安全地儲存在 Office 365 資料中心的快速存取。</span><span class="sxs-lookup"><span data-stu-id="5440b-p104">Downloading common things like icons over and over again can take up network bandwidth that can be better used for downloading important personal content, like email or documents. Because Office 365 uses an architecture that includes CDNs, the icons, scripts, and other generic content can be downloaded from servers closer to client computers, making the downloads faster. This means faster access to your personal content, which is securely stored in Office 365 datacenters.</span></span>
  
## <a name="what-exactly-is-a-cdn"></a><span data-ttu-id="5440b-119">CDN 究竟是什麼？</span><span class="sxs-lookup"><span data-stu-id="5440b-119">What exactly is a CDN?</span></span>

<span data-ttu-id="5440b-p105">Cdn 使用大部分的企業雲端服務。例如 Office 365 雲端服務有數百萬的客戶一次下載混合專屬的內容 （例如電子郵件） 和一般內容 （例如圖示）。它會使圖像所有人使用 like 圖示，接近使用者的電腦盡位置更有效率。尚未、 未建立 CDN 資料中心來儲存此泛型內容中每個都會] 區域中，或甚至是在每個主要的網際網路中樞全世界讓這些 Cdn 的一些共用的每個雲端服務的實用。</span><span class="sxs-lookup"><span data-stu-id="5440b-p105">CDNs are used by most enterprise cloud services. Cloud services like Office 365 have millions of customers downloading a mix of proprietary content (such as emails) and generic content (such as icons) at one time. It's more efficient to put images everyone uses, like icons, as close to the user's computer as possible. Yet, it isn't practical for every cloud service to build CDN datacenters that store this generic content in every metropolitan area, or even in every major Internet hub around the world, so some of these CDNs are shared.</span></span>
  
<span data-ttu-id="5440b-p106">Cdn 可以是私人或公開。擁有私人 Cdn 且 21vianet 由單一的公司、 以及僅該公司的應用程式及服務使用它。公用 Cdn 會執行租用多家客戶公司的流量的公司。根據您所處，可能最有效率的 Office 365 下載您從 Office 365 擁有 CDN 與執行、 公用 CDN 或兩者的組合一般圖像。不論使用何種類型的 CDN，以擷取資料的步驟都相同。</span><span class="sxs-lookup"><span data-stu-id="5440b-p106">CDNs can be private or public. Private CDNs are owned and operated by a single company, and only that company's applications and services can use it. Public CDNs are run by companies who lease usage to multiple companies. Depending on where you're located, it might be most efficient for Office 365 to download generic images for you from a CDN that Office 365 owns and runs, a public CDN, or a combination of the two. Regardless of what type of CDN is used, the steps to retrieve the data are the same.</span></span>
  
1. <span data-ttu-id="5440b-129">您的用戶端要求資料來自 Office 365。</span><span class="sxs-lookup"><span data-stu-id="5440b-129">Your client requests data from Office 365.</span></span>

2. <span data-ttu-id="5440b-130">Office 365 傳回資料至您的用戶端直接或引導您以 CDN 的用戶端。</span><span class="sxs-lookup"><span data-stu-id="5440b-130">Office 365 either returns the data directly to your client or directs your client to a CDN.</span></span>

3. <span data-ttu-id="5440b-131">如果在 CDN 已經快取資料，則您的用戶端會下載直接從最接近的 CDN 位置資料至您在網際網路上的用戶端。</span><span class="sxs-lookup"><span data-stu-id="5440b-131">If the data is already cached at the CDN, your client downloads the data directly from the nearest CDN location to your client on the internet.</span></span>

4. <span data-ttu-id="5440b-132">如果資料不在 CDN 快取、 CDN 節點要求將資料從 Office 365 與快取然後一段時間之後，您的用戶端下載資料的資料。</span><span class="sxs-lookup"><span data-stu-id="5440b-132">If the data isn't cached at the CDN, the CDN node requests the data from Office 365 and then cache's the data for a period of time after your client downloads the data.</span></span>

<span data-ttu-id="5440b-p107">Cdn 中取出的檔案及從最接近的 Office 365 資料中心的圖像，並接著，您的用戶端的檔案及影像從提取接近 CDN。當使用者皆可存取雲端服務，如讀取 Outlook Web App 中的電子郵件使用者的瀏覽器會嘗試從 Office 365 datacenter 擷取的檔案及圖像。花的時間與頻寬遞送檔案，而不是 Office 365 將瀏覽器重新導向至 CDN。CDN 找出使用者的瀏覽器至最接近的資料中心及使用重新導向，從該處下載一般的圖像。使用此 CDN 重新導向做為快速，並就會儲存使用者大量負荷沉重的下載時間。</span><span class="sxs-lookup"><span data-stu-id="5440b-p107">The CDNs pull the files and images from the nearest Office 365 datacenter and in turn, your client pulls the files and images from the nearest CDN. When users are accessing a cloud service, like reading email in Outlook Web App, the user's browser attempts to retrieve the files and images from the Office 365 datacenter. Instead of spending the time and bandwidth delivering the files, Office 365 redirects the browser to the CDN. The CDN figures out the closest datacenter to the user's browser and, using redirection, downloads the generic images from there. Using this CDN redirection is quick, and it saves users a lot of download time.</span></span>
  
## <a name="is-there-a-list-of-all-the-fqdns-that-leverage-cdns"></a><span data-ttu-id="5440b-138">是否有運用 Cdn 的所有 Fqdn 的清單吗？</span><span class="sxs-lookup"><span data-stu-id="5440b-138">Is there a list of all the FQDNs that leverage CDNs?</span></span>

<span data-ttu-id="5440b-139">我們已發佈的[Office 365 端點] 頁面上](https://go.microsoft.com/fwlink/p/?LinkID=293744)以取得最新運用 Cdn 最新 Fqdn，請參閱 Fqdn 以及它們如何運用 Cdn 變更一段時間的清單。</span><span class="sxs-lookup"><span data-stu-id="5440b-139">The list of FQDNs and how they leverage CDNs change over time, refer to our published [Office 365 endpoints page](https://go.microsoft.com/fwlink/p/?LinkID=293744) to get up to date on the latest FQDNs that leverage CDNs.</span></span>
  
## <a name="is-there-a-list-of-all-the-cdns-that-office-365-uses"></a><span data-ttu-id="5440b-140">是否有的 Office 365 使用的所有 Cdn 清單吗？</span><span class="sxs-lookup"><span data-stu-id="5440b-140">Is there a list of all the CDNs that Office 365 uses?</span></span>

<span data-ttu-id="5440b-p108">使用 Office 365 Cdn 一定都可能隨時變更並在許多情況下有多個設定一個已無法使用可行的 CDN 協力廠商。使用兩種常見 Cdn 是[Akamai](https://www.akamai.com/us/en/cdn.jsp)和[Microsoft Azure](https://azure.microsoft.com/documentation/services/cdn/)。這兩個這些 CDN 解決方案已增強的全球的多個角落服務連接到全域範圍。那里儲存的內容包含一般 Office 365 指令碼、 檔案及圖像。例如當您登入 portal.office.com、 從最接近的 CDN 加速頁面載入次數已取出的圖像。其他包括 Office 365 ProPlus 安裝個位元儲存在 CDN 以加速下載最新版本的 Office 所花費的時間量。也有某些儲存於 Cdn 如視訊檔案的 Office 365 視訊的專屬內容。一旦您上傳影片檔案加密，然後儲存在與 Azure 媒體服務及其加密的格式。當 Office 365 影片播放程式會擷取影片它先快取至最接近 CDN 之前下載至加速下載影片所花費的時間量。</span><span class="sxs-lookup"><span data-stu-id="5440b-p108">The CDNs in use by Office 365 are always subject to change and in many cases there are multiple CDN partners configured in the event one is unavailable. The two most common CDNs in use are [Akamai](https://www.akamai.com/us/en/cdn.jsp) and [Microsoft Azure](https://azure.microsoft.com/documentation/services/cdn/). Both of these CDN solutions have a global reach enhancing the reach of the service to more corners of the world. The content that is stored there includes general Office 365 scripts, files, and images. For example, when you logon to portal.office.com, the images are pulled from the nearest CDN to speed up the page load times. Other examples include Office 365 ProPlus storing the installation bits on a CDN to speed up the amount of time it takes to download the latest version of Office. There is also some proprietary content that is stored on CDNs such as the video files for Office 365 Video. Once you upload the videos, the files are encrypted and then stored in their encrypted format with Azure Media Services. When the Office 365 video player retrieves the video it is first cached to the nearest CDN before being downloaded to speed up the amount of time it takes to download the video.</span></span>
  
## <a name="does-office-365-offer-a-cdn-that-i-can-use-for-my-own-files"></a><span data-ttu-id="5440b-150">Office 365 是否提供 CDN 可用我自己檔案吗？</span><span class="sxs-lookup"><span data-stu-id="5440b-150">Does Office 365 offer a CDN that I can use for my own files?</span></span>

<span data-ttu-id="5440b-p109">是 ！您的 Office 365 訂閱現在包含您可以使用專屬的 SharePoint Online 的資產的 Azure 不同 CDN。如需如何使用 Office 365 CDN 資訊，請參閱[使用 Office 365 內容傳遞網路與 SharePoint Online](use-office-365-cdn-with-spo.md)。</span><span class="sxs-lookup"><span data-stu-id="5440b-p109">Yes! Your Office 365 subscription now includes a CDN that is separate from Azure that you can use specifically for your SharePoint Online assets. For information on how to use the Office 365 CDN, see [Use the Office 365 content delivery network with SharePoint Online](use-office-365-cdn-with-spo.md).</span></span>
  
## <a name="can-i-use-my-own-cdn-and-cache-content-on-my-local-network"></a><span data-ttu-id="5440b-154">在 「 我的區域網路是否可以使用我自己 CDN 與快取的內容吗？</span><span class="sxs-lookup"><span data-stu-id="5440b-154">Can I use my own CDN and cache content on my local network?</span></span>

<span data-ttu-id="5440b-155">我們要持續尋找新方法，以支援我們客戶需求與目前所探索使用快取 proxy 解決方案及其他內部部署 CDN 解決方案。</span><span class="sxs-lookup"><span data-stu-id="5440b-155">We're continually looking for new ways to support our customers needs and are currently exploring the use of caching proxy solutions and other on-premises CDN solutions.</span></span>
  
## <a name="is-my-data-safe"></a><span data-ttu-id="5440b-156">我的資料安全嗎？</span><span class="sxs-lookup"><span data-stu-id="5440b-156">Is my data safe?</span></span>

<span data-ttu-id="5440b-p110">我們採用小心以協助確保我們保護執行您的業務資料。其加密儲存在我們的內容傳遞網路協力廠商的項目 ；例如與[Office 365 影片](https://support.office.com/article/2bed67a1-4052-49ff-a4ce-b7e6530eb98e)或不客戶特定;例如 Office 365 ProPlus 的安裝檔案。Head 上移轉至[Office 365 信任中心](https://go.microsoft.com/fwlink/p/?LinkId=397383)以深入了解我們深入致力於保護您的資料與您的隱私。</span><span class="sxs-lookup"><span data-stu-id="5440b-p110">We take great care to help ensure that we protect the data that runs your business. The items stored at our content delivery network partners is either encrypted; such as with [Office 365 Video](https://support.office.com/article/2bed67a1-4052-49ff-a4ce-b7e6530eb98e), or not customer specific; such as the Office 365 ProPlus installation files. Head on over to the [Office 365 Trust Center](https://go.microsoft.com/fwlink/p/?LinkId=397383) to learn more about our in-depth efforts to protect your data and your privacy.</span></span>
  
## <a name="how-can-i-secure-my-network-with-all-these-3rd-party-services"></a><span data-ttu-id="5440b-160">如何保護這些 3rd 的廠商服務與我網路？</span><span class="sxs-lookup"><span data-stu-id="5440b-160">How can I secure my network with all these 3rd party services?</span></span>

<span data-ttu-id="5440b-p111">運用合作夥伴服務廣泛組允許擴充和符合可用性需求以及增強的使用者經驗時使用的 Office 365 的 Office 365。Office 365 使用 3rd 廠商服務包括兩個憑證撤銷清單 ；例如 crl.microsoft.com 或 sa.symcb.com，並 Cdn;例如 r3.res.outlook.com。每個 CDN FQDN Office 365 使用 Office 365 的自訂 FQDN，如果您正在傳送到 Office 365 要求的 FQDN 您可以確保我們控制 FQDN 和基礎內容在該位置。</span><span class="sxs-lookup"><span data-stu-id="5440b-p111">Leveraging an extensive set of partner services allows Office 365 to scale and meet availability requirements as well as enhance the user experience when using Office 365. The 3rd party services Office 365 leverages include both certificate revocation lists; such as crl.microsoft.com or sa.symcb.com, and CDNs; such as r3.res.outlook.com. Every CDN FQDN Office 365 uses is a custom FQDN for Office 365, if you're sent to a FQDN at the request of Office 365 you can be assured that we control the FQDN and the underlying content at that location.</span></span>
  
<span data-ttu-id="5440b-164">客戶的仍要隔離目的地 3rd 廠商目的地的要求從 Microsoft 或 Office 365 資料中心的要求我們已[管理 Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)端點寫入設定指導。</span><span class="sxs-lookup"><span data-stu-id="5440b-164">For customers that still want to segregate requests destined for a Microsoft or Office 365 datacenter from requests that are destined for a 3rd party, we've written up guidance on [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).</span></span>
  
## <a name="im-using-azure-expressroute-for-office-365-does-that-change-things"></a><span data-ttu-id="5440b-165">我正在使用 Azure ExpressRoute for Office 365、，並不會變更的事項嗎？</span><span class="sxs-lookup"><span data-stu-id="5440b-165">I'm using Azure ExpressRoute for Office 365, does that change things?</span></span>

<span data-ttu-id="5440b-p112">[Office 365 的 azure ExpressRoute](azure-expressroute.md)提供從公用網際網路隔離的 Office 365 基礎結構的專用的連線。這表示用戶端將仍需要透過非 ExpressRoute 連線以連線到 Cdn 與其他 Microsoft 基礎架構不明確包含在 ExpressRoute 所支援的服務清單中的連線。如需如何例如目的地 Cdn 要求特定流量路由的詳細資訊，請參閱[Office 365 網路流量管理](routing-with-expressroute.md)。</span><span class="sxs-lookup"><span data-stu-id="5440b-p112">[Azure ExpressRoute for Office 365](azure-expressroute.md) provides a dedicated connection to Office 365 infrastructure that is segregated from the public internet. This means that clients will still need to connect over non-ExpressRoute connections to connect to CDNs and other Microsoft infrastructure that is not explicitly included in the list of services supported by ExpressRoute. For more information about how to route specific traffic such as requests destined for CDNs, refer to [Office 365 network traffic management](routing-with-expressroute.md).</span></span>
  
<span data-ttu-id="5440b-169">以下是您可以使用回來的簡短連結：[https://aka.ms/o365cdns](https://aka.ms/o365cdns)</span><span class="sxs-lookup"><span data-stu-id="5440b-169">Here's a short link you can use to come back: [https://aka.ms/o365cdns](https://aka.ms/o365cdns)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5440b-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5440b-170">See also</span></span>

[<span data-ttu-id="5440b-171">Office 365 端點常見問題集</span><span class="sxs-lookup"><span data-stu-id="5440b-171">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
