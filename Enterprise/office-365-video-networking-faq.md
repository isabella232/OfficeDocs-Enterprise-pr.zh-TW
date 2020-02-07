---
title: 網路常見問題集的 office 365 影片
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 3/14/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 2bed67a1-4052-49ff-a4ce-b7e6530eb98e
description: Office 365 影片存放庫與資料流的服務，讓儲存及資料流組織內的影片簡單。 有很棒的資訊有關 Office 365 影片;此網路的常見問題集被設計來回答周圍頻寬規劃、 加密，以及服務如何運用內容傳遞網路 (Cdn) 最常見的問題。
ms.openlocfilehash: 21c7327878bc76bc3bbe92d004a26a4704ef8c3d
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841970"
---
# <a name="office-365-video-networking-frequently-asked-questions"></a><span data-ttu-id="d54ed-104">網路常見問題集的 office 365 影片</span><span class="sxs-lookup"><span data-stu-id="d54ed-104">Office 365 Video networking Frequently Asked Questions</span></span>

<span data-ttu-id="d54ed-105">Office 365 影片存放庫與資料流的服務，讓儲存及資料流組織內的影片簡單。</span><span class="sxs-lookup"><span data-stu-id="d54ed-105">The Office 365 Video repository and streaming services make storing and streaming videos within your organization simple.</span></span> <span data-ttu-id="d54ed-106">有很棒的[Office 365 影片的相關資訊](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50);此網路的常見問題集被設計來回答周圍頻寬規劃、 加密，以及服務如何運用[內容傳遞網路](content-delivery-networks.md)(Cdn) 最常見的問題。</span><span class="sxs-lookup"><span data-stu-id="d54ed-106">There's a lot of great [information about Office 365 Video](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50); this networking FAQ is designed to answer the most common questions around bandwidth planning, encryption, and how the service leverages [Content Delivery Networks](content-delivery-networks.md) (CDNs).</span></span>
  
<span data-ttu-id="d54ed-107">如果您不已有充分了解上傳程序的影片時，會發生什麼事，或播放，看看這段影片我們放在一起[上, 傳至 Office 365 影片的視訊檔案會發生什麼事](https://www.youtube.com/watch?v=HXSZ0jYBKlM)。</span><span class="sxs-lookup"><span data-stu-id="d54ed-107">If you don't already have a thorough understanding of what happens when a video is uploaded or played back, have a look at this video we put together, [What happens to a video file when uploaded to Office 365 Video](https://www.youtube.com/watch?v=HXSZ0jYBKlM).</span></span>
  
## <a name="what-are-the-office-365-video-bandwidth-requirements"></a><span data-ttu-id="d54ed-108">Office 365 影片頻寬需求是甚麼？</span><span class="sxs-lookup"><span data-stu-id="d54ed-108">What are the Office 365 Video bandwidth requirements?</span></span>

<span data-ttu-id="d54ed-109">有許多[支援的視訊格式](https://support.office.com/article/dd1af01c-fd8e-4640-b17b-93ee02b9b817)可上傳至 Office 365。</span><span class="sxs-lookup"><span data-stu-id="d54ed-109">There are a numerous [supported video formats](https://support.office.com/article/dd1af01c-fd8e-4640-b17b-93ee02b9b817) that can be uploaded to Office 365.</span></span> <span data-ttu-id="d54ed-110">每個視訊檔案然後編碼為標準格式與數個不同的視訊品質播放。</span><span class="sxs-lookup"><span data-stu-id="d54ed-110">Each video file is then encoded to a standard format with several different video qualities for playback.</span></span> <span data-ttu-id="d54ed-111">Office 365 影片中會使用調適型選取最佳的視訊播放品質的可用網路頻寬和大小的視訊播放程式為基礎的資料流的位元速率。</span><span class="sxs-lookup"><span data-stu-id="d54ed-111">Office 365 Video uses adaptive bitrate streaming to select the best video playback quality based on the available network bandwidth and size of the video player.</span></span> <span data-ttu-id="d54ed-112">若要這麼做，請在播放程式最初要求最低播放品質。</span><span class="sxs-lookup"><span data-stu-id="d54ed-112">To do this, the player initially requests the lowest playback quality.</span></span> <span data-ttu-id="d54ed-113">服務便可開始在影片播放程式來傳送 2 秒視訊的區段。</span><span class="sxs-lookup"><span data-stu-id="d54ed-113">The service then begins sending 2-second video segments to the video player.</span></span> <span data-ttu-id="d54ed-114">播放程式就可以要求較高或較低播放品質根據每一條線段會傳遞速度。</span><span class="sxs-lookup"><span data-stu-id="d54ed-114">The player can then request higher or lower playback quality based on how quickly each segment is delivered.</span></span>
  
<span data-ttu-id="d54ed-115">調適型的位元速率資料流這麼做是所有在幕後時視訊播放中斷或緩衝處理的最小。</span><span class="sxs-lookup"><span data-stu-id="d54ed-115">The adaptive bitrate streaming does all this in the background while the video plays with the least amount of disruption or buffering.</span></span> <span data-ttu-id="d54ed-116">視訊播放時，視訊播放程式可讓手動覆寫自動播放品質]，以選取特定的視訊播放品質檢視器]。</span><span class="sxs-lookup"><span data-stu-id="d54ed-116">During video playback, the video player allows the viewer to manually override the automatic playback quality, to select a specific video playback quality.</span></span>
  
<span data-ttu-id="d54ed-117">以下是每個播放視訊品質的網路需求概述快速資料表。</span><span class="sxs-lookup"><span data-stu-id="d54ed-117">Here's a quick table that outlines the network requirements for each of the video playback qualities.</span></span> <span data-ttu-id="d54ed-118">播放視訊時需要的人的最低頻寬為 802 Kbps。</span><span class="sxs-lookup"><span data-stu-id="d54ed-118">The minimum bandwidth per person needed to play a video is 802Kbps.</span></span>
  
|||
|:-----|:-----|
|<span data-ttu-id="d54ed-119">**播放品質**</span><span class="sxs-lookup"><span data-stu-id="d54ed-119">**Playback Quality**</span></span> <br/> |<span data-ttu-id="d54ed-120">**網路速度**</span><span class="sxs-lookup"><span data-stu-id="d54ed-120">**Network Speed**</span></span> <br/> |
|<span data-ttu-id="d54ed-121">288 p</span><span class="sxs-lookup"><span data-stu-id="d54ed-121">288p</span></span>  <br/> |<span data-ttu-id="d54ed-122">802 kbps</span><span class="sxs-lookup"><span data-stu-id="d54ed-122">802Kbps</span></span>  <br/> |
|<span data-ttu-id="d54ed-123">360 p</span><span class="sxs-lookup"><span data-stu-id="d54ed-123">360p</span></span>  <br/> |<span data-ttu-id="d54ed-124">1.2 Mbps</span><span class="sxs-lookup"><span data-stu-id="d54ed-124">1.2 Mbps</span></span>  <br/> |
|<span data-ttu-id="d54ed-125">576 p</span><span class="sxs-lookup"><span data-stu-id="d54ed-125">576p</span></span>  <br/> |<span data-ttu-id="d54ed-126">2.5 Mbps</span><span class="sxs-lookup"><span data-stu-id="d54ed-126">2.5 Mbps</span></span>  <br/> |
|<span data-ttu-id="d54ed-127">720 p</span><span class="sxs-lookup"><span data-stu-id="d54ed-127">720p</span></span>  <br/> |<span data-ttu-id="d54ed-128">3.8 Mbps</span><span class="sxs-lookup"><span data-stu-id="d54ed-128">3.8 Mbps</span></span>  <br/> |

<span data-ttu-id="d54ed-129">([回到頁首](office-365-video-networking-faq.md))</span><span class="sxs-lookup"><span data-stu-id="d54ed-129">([Back to top](office-365-video-networking-faq.md))</span></span>
  
## <a name="how-do-content-delivery-networks-cdns-help-video-playback"></a><span data-ttu-id="d54ed-130">內容傳遞網路 (Cdn) 如何協助視訊播放？</span><span class="sxs-lookup"><span data-stu-id="d54ed-130">How do Content Delivery Networks (CDNs) help video playback?</span></span>

<span data-ttu-id="d54ed-131">如果從相同的組織內的相同的地理位置的數名人員資料流相同的影片，Cdn 就會儲存一份這些影片中的位置接近該地理區域。</span><span class="sxs-lookup"><span data-stu-id="d54ed-131">If several people from the same organization within the same geographic location are streaming the same video(s), CDNs will store a copy of these videos in a location closer to that geographic region.</span></span> <span data-ttu-id="d54ed-132">與視訊儲存，或快取的最接近的位置，每位人員會串流傳送給他們而不是位置進一步最接近的位置的視訊離開。</span><span class="sxs-lookup"><span data-stu-id="d54ed-132">With the video stored, or cached at the closest location, each person streams the video from the location closest to them instead of a location further away.</span></span> <span data-ttu-id="d54ed-133">Office 365 影片會使用 Azure 媒體服務來管理項目快取中的 Azure Cdn，以及如何長時間。</span><span class="sxs-lookup"><span data-stu-id="d54ed-133">Office 365 Video uses Azure Media Services to manage what is cached in the Azure CDNs, and for how long.</span></span> <span data-ttu-id="d54ed-134">Azure 媒體服務可以使用任何[Azure CDN 位置](https://azure.microsoft.com/documentation/articles/cdn-pop-locations/)來快取視訊片段及幾天的資訊清單。</span><span class="sxs-lookup"><span data-stu-id="d54ed-134">Azure Media Services can use any of the [Azure CDN locations](https://azure.microsoft.com/documentation/articles/cdn-pop-locations/) to cache video fragments and manifests for a few days.</span></span> <span data-ttu-id="d54ed-135">如果您組織中的人員會繼續觀賞快取的視訊留在快取中。</span><span class="sxs-lookup"><span data-stu-id="d54ed-135">If people in your organization continue to watch the cached videos they'll stay in the cache.</span></span> <span data-ttu-id="d54ed-136">如果數天，影片的影片最後也將任何一個存取放置捨棄從快取。</span><span class="sxs-lookup"><span data-stu-id="d54ed-136">If no one accesses the video for several days, the video will eventually drop be dropped from the cache.</span></span> <span data-ttu-id="d54ed-137">下次有人嘗試觀看影片它會再次重申快取的最接近的 CDN 位置。</span><span class="sxs-lookup"><span data-stu-id="d54ed-137">The next time someone attempts to watch the video it's once again cached at the nearest CDN location.</span></span>
  
<span data-ttu-id="d54ed-138">每一位使用者嘗試觀看影片內容時是鄰近的 CDN 優點從視訊正在接近，並在大多數情況下小於躍點，立即在快取。</span><span class="sxs-lookup"><span data-stu-id="d54ed-138">Everyone who attempts to watch the video while the content is cached at a nearby CDN benefits from the video being closer, and in most cases less hops, away.</span></span> <span data-ttu-id="d54ed-139">這樣可以改善視訊播放速度;不過，它不會變更來播放影片的網路需求。</span><span class="sxs-lookup"><span data-stu-id="d54ed-139">This improves video playback speed; however, it doesn't change the network requirement to play the video.</span></span>
  
> [!NOTE]
> <span data-ttu-id="d54ed-140">有某些情況下，例如正在到達，已達三天前，移除影片可能其中我們容量限制。</span><span class="sxs-lookup"><span data-stu-id="d54ed-140">There are some circumstances, such as our capacity limit being reached, where the video may be removed before the three days has been reached.</span></span>
  
<span data-ttu-id="d54ed-141">([回到頁首](office-365-video-networking-faq.md))</span><span class="sxs-lookup"><span data-stu-id="d54ed-141">([Back to top](office-365-video-networking-faq.md))</span></span>
  
## <a name="can-i-cache-the-videos-locally-for-faster-playback"></a><span data-ttu-id="d54ed-142">可以快取到本機的速度播放影片嗎？</span><span class="sxs-lookup"><span data-stu-id="d54ed-142">Can I cache the videos locally for faster playback?</span></span>

<span data-ttu-id="d54ed-143">是。</span><span class="sxs-lookup"><span data-stu-id="d54ed-143">Yes.</span></span> <span data-ttu-id="d54ed-144">Office 365 不會使您無法將影片或其他 Office 365 內容移入進行快速存取您的區域網路使用本機 CDN 或快取的 proxy。</span><span class="sxs-lookup"><span data-stu-id="d54ed-144">Office 365 won't prevent you from using a local CDN or a caching proxy to bring video or other Office 365 content into your local network for faster access.</span></span> <span data-ttu-id="d54ed-145">有幾種方式可以實作您網路上的本機快取解決方案，最常用的方法是使用快取本機內容的 proxy 解決方案。</span><span class="sxs-lookup"><span data-stu-id="d54ed-145">There are several ways to implement a local caching solution on your network, the most common method is to use a proxy solution that caches content locally.</span></span> <span data-ttu-id="d54ed-146">一旦視訊片段和資訊清單的 proxy 或私人 CDN 已快取，未來要求透過 proxy 或私人 CDN 路由傳送這些檔案是提取從本機快取，並不取自網際網路位置。</span><span class="sxs-lookup"><span data-stu-id="d54ed-146">Once a proxy or private CDN has cached the video fragments and manifests, future requests for those files that route through the proxy or private CDN are pulled from the local cache and not pulled from an internet location.</span></span> <span data-ttu-id="d54ed-147">類似解決方案的規劃期間，請考慮網路頻寬、 容量及視訊播放並行數目。</span><span class="sxs-lookup"><span data-stu-id="d54ed-147">Consider network bandwidth, capacity, and video playback concurrency during the planning of a solution like this.</span></span>
  
<span data-ttu-id="d54ed-148">([回到頁首](office-365-video-networking-faq.md))</span><span class="sxs-lookup"><span data-stu-id="d54ed-148">([Back to top](office-365-video-networking-faq.md))</span></span>
  
## <a name="how-videos-are-encrypted-and-secured"></a><span data-ttu-id="d54ed-149">如何影片加密和保護？</span><span class="sxs-lookup"><span data-stu-id="d54ed-149">How videos are encrypted and secured?</span></span>

<span data-ttu-id="d54ed-150">Office 365 影片知道會保護您的資料，安全無虞且私用的重要程度。</span><span class="sxs-lookup"><span data-stu-id="d54ed-150">Office 365 Video knows how important it is to keep your data secure and private.</span></span> <span data-ttu-id="d54ed-151">[Microsoft 信任中心](https://products.office.com/business/office-365-trust-center-welcome)說明我們致力於內容的安全性與隱私權。</span><span class="sxs-lookup"><span data-stu-id="d54ed-151">[Microsoft Trust Center](https://products.office.com/business/office-365-trust-center-welcome) describes our commitment to the privacy and security of your content.</span></span> <span data-ttu-id="d54ed-152">播放視訊時，速度是很重要的良好的體驗。不過，我們不危害安全性或隱私權相信速度。</span><span class="sxs-lookup"><span data-stu-id="d54ed-152">With video playback, speed is important for a good experience; however, we don't compromise your security or privacy in exchange for speed.</span></span> <span data-ttu-id="d54ed-153">以下是我們如何配合速度、 安全性及隱私權。</span><span class="sxs-lookup"><span data-stu-id="d54ed-153">Here's how we accommodate speed, security and privacy.</span></span>
  
<span data-ttu-id="d54ed-154">當您或貴組織中的人員將上傳新的視訊時，視訊是轉碼，使用 AES 128 加密，加密並儲存在 Azure 媒體服務。</span><span class="sxs-lookup"><span data-stu-id="d54ed-154">When you or someone in your organization uploads a new video, that video is transcoded, encrypted with AES-128 encryption, and stored in Azure Media Services.</span></span> <span data-ttu-id="d54ed-155">這表示在傳輸及靜態加密影片。</span><span class="sxs-lookup"><span data-stu-id="d54ed-155">This means the videos are encrypted both in transit and at rest.</span></span>
  
<span data-ttu-id="d54ed-156">當您的組織中的人員嘗試觀看之新視訊時，他們會遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="d54ed-156">When someone in your organization attempts to watch a new video, they follow these steps:</span></span>
  
1. <span data-ttu-id="d54ed-157">要求 SharePoint Online 是否他們有權檢視視訊。</span><span class="sxs-lookup"><span data-stu-id="d54ed-157">Ask SharePoint Online if they have permission to view the video.</span></span>

2. <span data-ttu-id="d54ed-158">SharePoint Online 會使用檔案的權限來決定是否人員可以觀看影片。</span><span class="sxs-lookup"><span data-stu-id="d54ed-158">SharePoint Online uses the file permissions to determine if the person can watch the video.</span></span>

3. <span data-ttu-id="d54ed-159">如果他們正在允許，SharePoint Online 擷取權杖從 Azure 將授與視訊播放程式。</span><span class="sxs-lookup"><span data-stu-id="d54ed-159">If they're allowed, SharePoint Online retrieves a token from Azure to give to the video player.</span></span>

4. <span data-ttu-id="d54ed-160">視訊播放程式接著會使用語彙基元，從 Azure 要求解密金鑰。</span><span class="sxs-lookup"><span data-stu-id="d54ed-160">The video player then uses the token to request the decryption key from Azure.</span></span>

5. <span data-ttu-id="d54ed-161">在手解密金鑰，視訊播放程式是能夠傳送視訊資料流。</span><span class="sxs-lookup"><span data-stu-id="d54ed-161">With the decryption key in hand, the video player is able to stream the video.</span></span>

![O365 視訊播放](media/9d3c6e76-151d-48a3-a30e-ba8dd07db0b7.png)
  
<span data-ttu-id="d54ed-163">([回到頁首](office-365-video-networking-faq.md))</span><span class="sxs-lookup"><span data-stu-id="d54ed-163">([Back to top](office-365-video-networking-faq.md))</span></span>
  
## <a name="what-are-the-requirements-to-playback-office-365-video"></a><span data-ttu-id="d54ed-164">Office 365 影片播放需求是甚麼？</span><span class="sxs-lookup"><span data-stu-id="d54ed-164">What are the requirements to playback Office 365 Video?</span></span>

<span data-ttu-id="d54ed-165">Office 365 影片支援的作業系統和網頁瀏覽器是[Office 365 系統需求](https://support.office.com/article/Office-365-system-requirements-719254c0-2671-4648-9c84-c6a3d4f3be45)中的 SharePoint Online 需求相同。</span><span class="sxs-lookup"><span data-stu-id="d54ed-165">Office 365 Video supported operating systems and web browsers are the same as the SharePoint Online requirements in [Office 365 system requirements](https://support.office.com/article/Office-365-system-requirements-719254c0-2671-4648-9c84-c6a3d4f3be45).</span></span> <span data-ttu-id="d54ed-166">視哪些作業系統和網頁瀏覽器設定，您必須將會決定在影片播放程式的特定需求。</span><span class="sxs-lookup"><span data-stu-id="d54ed-166">Depending on which operating system and web browser configuration you have will determine the specific needs of the video player.</span></span> <span data-ttu-id="d54ed-167">以下是在[影片播放需求](https://support.office.com/article/ca1cc1a9-a615-46e1-b6a3-40dbd99939a6)的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="d54ed-167">Here's more information on [video playback requirements](https://support.office.com/article/ca1cc1a9-a615-46e1-b6a3-40dbd99939a6).</span></span>
  
<span data-ttu-id="d54ed-168">([回到頁首](office-365-video-networking-faq.md))</span><span class="sxs-lookup"><span data-stu-id="d54ed-168">([Back to top](office-365-video-networking-faq.md))</span></span>
  
## <a name="i-cant-get-office-365-video-to-work-where-should-i-start"></a><span data-ttu-id="d54ed-169">無法取得 Office 365 影片運作，其中應該開始？</span><span class="sxs-lookup"><span data-stu-id="d54ed-169">I can't get Office 365 video to work, where should I start?</span></span>

<span data-ttu-id="d54ed-170">疑難排解 Office 365 影片的連線，包括疑難排解您的網路、 您 ISP(s)，與您的 Office 365 的設定。</span><span class="sxs-lookup"><span data-stu-id="d54ed-170">Troubleshooting connectivity to Office 365 Video involves troubleshooting your network, your ISP(s), and your configuration of Office 365.</span></span> <span data-ttu-id="d54ed-171">若要啟動的第一個位置是在服務健康狀況儀表板。</span><span class="sxs-lookup"><span data-stu-id="d54ed-171">The first place to start is the service health dashboard.</span></span> <span data-ttu-id="d54ed-172">這會告知您的 Office 365 影片有問題，或不。</span><span class="sxs-lookup"><span data-stu-id="d54ed-172">This will tell you of Office 365 Video is having a problem or not.</span></span> <span data-ttu-id="d54ed-173">如果一切就很好，以下是一些額外的資源，可以協助您。</span><span class="sxs-lookup"><span data-stu-id="d54ed-173">If everything looks great there, here's some additional resources to help you.</span></span>
  
- <span data-ttu-id="d54ed-174">請確定您可以連線至[Office 365 影片所需的網路端點](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)。</span><span class="sxs-lookup"><span data-stu-id="d54ed-174">Make sure you can connect to the [network endpoints required for Office 365 Video](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).</span></span>

- <span data-ttu-id="d54ed-175">檢查網路連線使用我們的[Office 365 網路疑難排解指南](https://support.office.com/article/Office-365-performance-tuning-and-troubleshooting-Admin-and-IT-Pro-1492cb94-bd62-43e6-b8d0-2a61ed88ebae)。</span><span class="sxs-lookup"><span data-stu-id="d54ed-175">Check your network connectivity using our [Office 365 network troubleshooting guide](https://support.office.com/article/Office-365-performance-tuning-and-troubleshooting-Admin-and-IT-Pro-1492cb94-bd62-43e6-b8d0-2a61ed88ebae).</span></span>

- <span data-ttu-id="d54ed-176">請參閱我們的[使用在慢速網路上的 Office 365 的最佳作法](https://support.office.com/article/Best-practices-for-using-Office-365-on-a-slow-network-fd16c8d2-4799-4c39-8fd7-045f06640166)。</span><span class="sxs-lookup"><span data-stu-id="d54ed-176">See our [best practices for using Office 365 on a slow network](https://support.office.com/article/Best-practices-for-using-Office-365-on-a-slow-network-fd16c8d2-4799-4c39-8fd7-045f06640166).</span></span>

- <span data-ttu-id="d54ed-177">[尋找有關 Office 365 影片設定的說明](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50)。</span><span class="sxs-lookup"><span data-stu-id="d54ed-177">[Find help about Office 365 Video configuration](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50).</span></span>

<span data-ttu-id="d54ed-178">([回到頁首](office-365-video-networking-faq.md))</span><span class="sxs-lookup"><span data-stu-id="d54ed-178">([Back to top](office-365-video-networking-faq.md))</span></span>
  
## <a name="office-365-video-resources"></a><span data-ttu-id="d54ed-179">Office 365 影片資源</span><span class="sxs-lookup"><span data-stu-id="d54ed-179">Office 365 Video resources</span></span>

<span data-ttu-id="d54ed-180">以下是一些其他資源以協助您成功部署及使用 Office 365 影片：</span><span class="sxs-lookup"><span data-stu-id="d54ed-180">Here's a few other resources to help you successfully deploy and use Office 365 Video:</span></span>
  
[<span data-ttu-id="d54ed-181">尋找有關 Office 365 影片設定的說明</span><span class="sxs-lookup"><span data-stu-id="d54ed-181">Find help about Office 365 Video configuration</span></span>](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50)
  
[<span data-ttu-id="d54ed-182">符合 Office 365 影片</span><span class="sxs-lookup"><span data-stu-id="d54ed-182">Meet Office 365 Video</span></span>](https://support.office.com/article/Meet-Office-365-Video-ca1cc1a9-a615-46e1-b6a3-40dbd99939a6)
  
[<span data-ttu-id="d54ed-183">建立及管理 Office 365 影片中的通道</span><span class="sxs-lookup"><span data-stu-id="d54ed-183">Create and manage a channel in Office 365 Video</span></span>](https://support.office.com/article/Create-and-manage-a-channel-in-Office-365-Video-1fede4cc-13c0-435a-b585-e7fbf1c83bb2)
  
[<span data-ttu-id="d54ed-184">管理您的 Office 365 影片入口網站</span><span class="sxs-lookup"><span data-stu-id="d54ed-184">Manage your Office 365 Video portal</span></span>](https://support.office.com/article/Manage-your-Office-365-Video-portal-c059465b-eba9-44e1-b8c7-8ff7793ff5da)
  
[<span data-ttu-id="d54ed-185">在 Office 365 影片中運作的視訊格式</span><span class="sxs-lookup"><span data-stu-id="d54ed-185">Video formats that work in Office 365 Video</span></span>](https://support.office.com/article/Video-formats-that-work-in-Office-365-Video-dd1af01c-fd8e-4640-b17b-93ee02b9b817)
  
<span data-ttu-id="d54ed-186">([回到頁首](office-365-video-networking-faq.md))</span><span class="sxs-lookup"><span data-stu-id="d54ed-186">([Back to top](office-365-video-networking-faq.md))</span></span>
  
<span data-ttu-id="d54ed-187">您可以使用下列短連結返回這裡：[https://aka.ms/video365networkfaq](https://aka.ms/video365networkfaq)</span><span class="sxs-lookup"><span data-stu-id="d54ed-187">Here's a short link you can use to come back: [https://aka.ms/video365networkfaq](https://aka.ms/video365networkfaq)</span></span>
