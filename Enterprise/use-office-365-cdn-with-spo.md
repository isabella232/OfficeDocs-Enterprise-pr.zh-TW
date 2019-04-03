---
title: 使用 Office 365 內容傳遞網路 (CDN) 搭配 SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/2/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: bebb285f-1d54-4f79-90a5-94985afc6af8
description: 說明如何使用 Office 365 內容傳遞網路 (CDN) 來加快 SharePoint Online 的資產傳遞至您的所有使用者不論它們的所在位置，或使用者如何存取您的內容。
ms.openlocfilehash: a718c30a40209a8ee0c8e78700ed3eae72c8347c
ms.sourcegitcommit: 43d2b7e1d9932182c6cca5164d4d9096dcf4ed36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "31039500"
---
# <a name="use-the-office-365-content-delivery-network-cdn-with-sharepoint-online"></a><span data-ttu-id="98e13-103">使用 Office 365 內容傳遞網路 (CDN) 搭配 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="98e13-103">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>

<span data-ttu-id="98e13-104">您可以使用內建的 Office 365 內容傳遞網路 (CDN) 來主控靜態資產，為您的 SharePoint網頁提供更佳的效能。</span><span class="sxs-lookup"><span data-stu-id="98e13-104">You can use the built-in Office 365 Content Delivery Network (CDN) to host static assets to provide better performance for your SharePoint Online pages.</span></span> <span data-ttu-id="98e13-105">Office 365 CDN 透過將靜態資產快取到更靠近提出要求之瀏覽器的位置 (這有助於加速下載以及減少延遲)，藉此改善效能。</span><span class="sxs-lookup"><span data-stu-id="98e13-105">The Office 365 CDN improves performance by caching static assets closer to the browsers requesting them, which helps to speed up downloads and reduce latency.</span></span> <span data-ttu-id="98e13-106">此外，Office 365 CDN 改善的壓縮和 HTTP 管線使用[HTTP/2 通訊協定](https://en.wikipedia.org/wiki/HTTP/2)。</span><span class="sxs-lookup"><span data-stu-id="98e13-106">Also, the Office 365 CDN uses the [HTTP/2 protocol](https://en.wikipedia.org/wiki/HTTP/2) for improved compression and HTTP pipelining.</span></span> <span data-ttu-id="98e13-107">Office 365 CDN 服務包含在 SharePoint Online 訂閱的一部分。</span><span class="sxs-lookup"><span data-stu-id="98e13-107">The Office 365 CDN service is included as part of your SharePoint Online subscription.</span></span>

<span data-ttu-id="98e13-108">Office 365 CDN 是由可讓您在多個位置或_來源_主控靜態資產的多個 CDN 組成，並透過全球高速網路提供資產。</span><span class="sxs-lookup"><span data-stu-id="98e13-108">The Office 365 CDN is composed of multiple CDNs that allow you to host static assets in multiple locations, or _origins_, and serve them from global high-speed networks.</span></span> <span data-ttu-id="98e13-109">根據您要在 Office 365 CDN 中主控的內容類型而定，您可以新增**公用**來源、**私人**來源或兩者。</span><span class="sxs-lookup"><span data-stu-id="98e13-109">Depending on the kind of content you want to host in the Office 365 CDN, you can add **public** origins, **private** origins or both.</span></span> <span data-ttu-id="98e13-110">如需公用和私人原點之間的差異的詳細資訊，請參閱[選擇每個原始來源是否應該是公用或私人](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)。</span><span class="sxs-lookup"><span data-stu-id="98e13-110">See [Choose whether each origin should be public or private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate) for more information on the difference between public and private origins.</span></span>

<span data-ttu-id="98e13-111">![Office 365 CDN 概念圖](media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN 概念圖")</span><span class="sxs-lookup"><span data-stu-id="98e13-111">![Office 365 CDN conceptual diagram](media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN conceptual diagram")</span></span>

<span data-ttu-id="98e13-112">如果您已熟悉 Cdn 的方式，您只需要完成啟用 CDN 將 Office 365 租用戶的幾個步驟。</span><span class="sxs-lookup"><span data-stu-id="98e13-112">If you are already familiar with the way that CDNs work, you only need to complete a few steps to enable the Office 365 CDN for your tenant.</span></span> <span data-ttu-id="98e13-113">本主題說明如何。</span><span class="sxs-lookup"><span data-stu-id="98e13-113">This topic describes how.</span></span> <span data-ttu-id="98e13-114">閱讀如何開始主控您的靜態資產的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="98e13-114">Read on for information about how to get started hosting your static assets.</span></span>

> [!TIP]
> <span data-ttu-id="98e13-115">有其他 Microsoft 主控的 Cdn 可用於 Office 365 的特殊的使用情況，但會在因為他們屬於超出 Office 365 CDN 的範圍不在本主題討論。</span><span class="sxs-lookup"><span data-stu-id="98e13-115">There are other Microsoft-hosted CDNs that can be used with Office 365 for specialized usage scenarios, but are not discussed in this topic because they fall outside the scope of the Office 365 CDN.</span></span> <span data-ttu-id="98e13-116">如需詳細資訊，請參閱 <<c0>其他 Microsoft Cdn。</span><span class="sxs-lookup"><span data-stu-id="98e13-116">For more information, see [Other Microsoft CDNs](content-delivery-networks.md#other-microsoft-cdns).</span></span>

 **<span data-ttu-id="98e13-117">Head 回[網路規劃和效能調整的 Office 365](https://aka.ms/tune)。</span><span class="sxs-lookup"><span data-stu-id="98e13-117">Head back to [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>**

## <a name="overview-of-working-with-the-office-365-cdn-in-sharepoint-online"></a><span data-ttu-id="98e13-118">使用 SharePoint Online 中 CDN 將 Office 365 的概觀</span><span class="sxs-lookup"><span data-stu-id="98e13-118">Overview of working with the Office 365 CDN in SharePoint Online</span></span>

<span data-ttu-id="98e13-119">若要設定為您的組織 CDN 將 Office 365，您可以遵循下列基本步驟：</span><span class="sxs-lookup"><span data-stu-id="98e13-119">To set up the Office 365 CDN for your organization, you follow these basic steps:</span></span>

- [<span data-ttu-id="98e13-120">規劃部署 Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="98e13-120">Plan for deployment of the Office 365 CDN</span></span>](use-office-365-cdn-with-spo.md#plan-for-deployment-of-the-office-365-cdn)

  - <span data-ttu-id="98e13-121">[決定您想要在 CDN 上裝載的靜態資產](use-office-365-cdn-with-spo.md#CDNAssets)。</span><span class="sxs-lookup"><span data-stu-id="98e13-121">[Determine which static assets you want to host on the CDN](use-office-365-cdn-with-spo.md#CDNAssets).</span></span>
  - <span data-ttu-id="98e13-122">[決定您想要用來儲存您的資產](use-office-365-cdn-with-spo.md#CDNStoreAssets)。</span><span class="sxs-lookup"><span data-stu-id="98e13-122">[Determine where you want to store your assets](use-office-365-cdn-with-spo.md#CDNStoreAssets).</span></span> <span data-ttu-id="98e13-123">此位置可以是 SharePoint 網站、 文件庫或資料夾，並呼叫_原點_。</span><span class="sxs-lookup"><span data-stu-id="98e13-123">This location can be a SharePoint site, library or folder and is called an _origin_.</span></span>
  - <span data-ttu-id="98e13-124">[選擇 [每個原始來源是否應該是公用或私人](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)。</span><span class="sxs-lookup"><span data-stu-id="98e13-124">[Choose whether each origin should be public or private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate).</span></span> <span data-ttu-id="98e13-125">您可以新增多個公用和私人類型的原點。</span><span class="sxs-lookup"><span data-stu-id="98e13-125">You can add multiple origins of both public and private types.</span></span>

- <span data-ttu-id="98e13-126">安裝及設定 CDN，使用 PowerShell 或 SharePoint Online CLI</span><span class="sxs-lookup"><span data-stu-id="98e13-126">Set up and configure the CDN, using either PowerShell or the SharePoint Online CLI</span></span>

  - [<span data-ttu-id="98e13-127">安裝及使用 SharePoint Online 管理命令介面設定 CDN</span><span class="sxs-lookup"><span data-stu-id="98e13-127">Set up and configure the CDN by using the SharePoint Online Management Shell</span></span>](use-office-365-cdn-with-spo.md#CDNSetupinPShell)
  - [<span data-ttu-id="98e13-128">安裝及使用 Office 365 CLI 設定 CDN</span><span class="sxs-lookup"><span data-stu-id="98e13-128">Set up and configure the CDN by using the Office 365 CLI</span></span>](use-office-365-cdn-with-spo.md#CDNSetupinCLI)

  <span data-ttu-id="98e13-129">當您完成此步驟時，您必須：</span><span class="sxs-lookup"><span data-stu-id="98e13-129">When you complete this step, you will have:</span></span>

  - <span data-ttu-id="98e13-130">啟用組織 CDN。</span><span class="sxs-lookup"><span data-stu-id="98e13-130">Enabled the CDN for your organization.</span></span>
  - <span data-ttu-id="98e13-131">新增您的原點，用來識別為公用或私人每個原始來源。</span><span class="sxs-lookup"><span data-stu-id="98e13-131">Added your origins, identifying each origin as public or private.</span></span>

<span data-ttu-id="98e13-132">一旦您完成安裝程式，您可以[管理 Office 365 CDN](use-office-365-cdn-with-spo.md#CDNManage)經過一段時間的：</span><span class="sxs-lookup"><span data-stu-id="98e13-132">Once you're done with setup, you can [Manage the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNManage) over time by:</span></span>
  
- <span data-ttu-id="98e13-133">新增、 更新及移除資產</span><span class="sxs-lookup"><span data-stu-id="98e13-133">Adding, updating, and removing assets</span></span>
- <span data-ttu-id="98e13-134">新增及移除原點</span><span class="sxs-lookup"><span data-stu-id="98e13-134">Adding and removing origins</span></span>
- <span data-ttu-id="98e13-135">設定 CDN 原則</span><span class="sxs-lookup"><span data-stu-id="98e13-135">Configuring CDN policies</span></span>
- <span data-ttu-id="98e13-136">如有必要，停用 CDN</span><span class="sxs-lookup"><span data-stu-id="98e13-136">If necessary, disabling the CDN</span></span>

<span data-ttu-id="98e13-137">最後，請參閱 < 若要了解公用及私人原點從存取 CDN 資產<b0>使用 CDN 資產</b0>。</span><span class="sxs-lookup"><span data-stu-id="98e13-137">Finally, see [Using your CDN assets](use-office-365-cdn-with-spo.md#using-your-cdn-assets) to learn about accessing your CDN assets from both public and private origins.</span></span>

<span data-ttu-id="98e13-138">如需解決一般問題的指導，請參閱[疑難排解 Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) 。</span><span class="sxs-lookup"><span data-stu-id="98e13-138">See [Troubleshooting the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) for guidance on resolving common issues.</span></span>

## <a name="plan-for-deployment-of-the-office-365-cdn"></a><span data-ttu-id="98e13-139">規劃部署 Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="98e13-139">Plan for deployment of the Office 365 CDN</span></span>

<span data-ttu-id="98e13-140">您的 Office 365 租用戶部署 Office 365 CDN 之前，您應該考量下列因素規劃程序的一部分。</span><span class="sxs-lookup"><span data-stu-id="98e13-140">Before you deploy the Office 365 CDN for your Office 365 tenant, you should consider the following factors as part of your planning process.</span></span>

  - [<span data-ttu-id="98e13-141">決定您想要在 CDN 上裝載的靜態資產</span><span class="sxs-lookup"><span data-stu-id="98e13-141">Determine which static assets you want to host on the CDN</span></span>](use-office-365-cdn-with-spo.md#CDNAssets)
  - [<span data-ttu-id="98e13-142">決定您想要用來儲存您的資產</span><span class="sxs-lookup"><span data-stu-id="98e13-142">Determine where you want to store your assets</span></span>](use-office-365-cdn-with-spo.md#CDNStoreAssets)
  - [<span data-ttu-id="98e13-143">選擇 [每個原始來源是否應該是公用或私用</span><span class="sxs-lookup"><span data-stu-id="98e13-143">Choose whether each origin should be public or private</span></span>](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)

### <a name="determine-which-static-assets-you-want-to-host-on-the-cdn"></a><span data-ttu-id="98e13-144">決定您想要在 CDN 上裝載的靜態資產</span><span class="sxs-lookup"><span data-stu-id="98e13-144">Determine which static assets you want to host on the CDN</span></span>
<a name="CDNAssets"> </a>

<span data-ttu-id="98e13-145">在 [一般] Cdn 是以架設_靜態資產_或未經常變更的資產最為有用。</span><span class="sxs-lookup"><span data-stu-id="98e13-145">In general, CDNs are most effective for hosting _static assets_, or assets that don't change very often.</span></span> <span data-ttu-id="98e13-146">好用的經驗法則是找出符合部分或所有的這些條件的檔案：</span><span class="sxs-lookup"><span data-stu-id="98e13-146">A good rule of thumb is to identify files that meet some or all of these conditions:</span></span>

- <span data-ttu-id="98e13-147">靜態檔案內嵌在頁面 （例如指令碼和圖像），可能會造成重大的累加影響的頁面載入時間</span><span class="sxs-lookup"><span data-stu-id="98e13-147">Static files embedded in a page (like scripts and images) that may have a significant incremental impact on page load times</span></span>
- <span data-ttu-id="98e13-148">大型檔案一樣的可執行檔和安裝檔案</span><span class="sxs-lookup"><span data-stu-id="98e13-148">Large files like executables and installation files</span></span>
- <span data-ttu-id="98e13-149">資料流的媒體檔案</span><span class="sxs-lookup"><span data-stu-id="98e13-149">Streaming media files</span></span>
- <span data-ttu-id="98e13-150">支援用戶端程式碼的資源庫</span><span class="sxs-lookup"><span data-stu-id="98e13-150">Resource libraries that support client-side code</span></span>

<span data-ttu-id="98e13-151">例如，便會重複替換要求網站圖像和指令碼等的小型檔案可以大幅改善網站呈現效能，而逐漸減少在 SharePoint Online 網站上的負載，當您將它們新增至 CDN 原點。</span><span class="sxs-lookup"><span data-stu-id="98e13-151">For example, small files that are repeatedly requested like site images and scripts can significantly improve site rendering performance and incrementally reduce the load on your SharePoint Online sites when you add them to a CDN origin.</span></span> <span data-ttu-id="98e13-152">可以下載較大的檔案，例如安裝可執行檔或視訊檔案，或從 CDN，即使未經常存取它們傳遞誤判的效能影響和後續降低您的 SharePoint Online 網站上的負載以串流方式傳送。</span><span class="sxs-lookup"><span data-stu-id="98e13-152">Larger files such as installation executables or video files can be downloaded or streamed from the CDN, delivering a positive performance impact and subsequent reduction of the load on your SharePoint Online site, even if they are not accessed as often.</span></span>

<span data-ttu-id="98e13-153">每個檔案為基礎的效能改進是取決於許多因素，包括至最接近的 CDN 端點，用戶端的近似值暫時性條件的區域網路，依此類推。</span><span class="sxs-lookup"><span data-stu-id="98e13-153">Performance improvement on a per-file basis is dependent on many factors, including the client's proximity to the nearest CDN endpoint, transient conditions on the local network, and so forth.</span></span> <span data-ttu-id="98e13-154">許多靜態檔案很小，且可從 Office 365 下載少於一秒。</span><span class="sxs-lookup"><span data-stu-id="98e13-154">Many static files are quite small, and can be downloaded from Office 365 in less than a second.</span></span> <span data-ttu-id="98e13-155">不過，網頁可能包含許多嵌入的檔案，並幾秒鐘的累計下載時間。</span><span class="sxs-lookup"><span data-stu-id="98e13-155">However, a web page may contain many embedded files with a cumulative download time of several seconds.</span></span> <span data-ttu-id="98e13-156">從 CDN 提供這些檔案，可大幅降低整體的頁面載入時間。</span><span class="sxs-lookup"><span data-stu-id="98e13-156">Serving these files from the CDN can significantly reduce the overall page load time.</span></span> <span data-ttu-id="98e13-157">請參閱[，可提升何種效能沒有 CDN 提供？](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide)範例。</span><span class="sxs-lookup"><span data-stu-id="98e13-157">See [What performance gains does a CDN provide?](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide) for an example.</span></span>

### <a name="determine-where-you-want-to-store-your-assets"></a><span data-ttu-id="98e13-158">決定您想要用來儲存您的資產</span><span class="sxs-lookup"><span data-stu-id="98e13-158">Determine where you want to store your assets</span></span>
<a name="CDNStoreAssets"> </a>

<span data-ttu-id="98e13-159">CDN 擷取您資產從呼叫_原點_的位置。</span><span class="sxs-lookup"><span data-stu-id="98e13-159">The CDN fetches your assets from a location called an _origin_.</span></span> <span data-ttu-id="98e13-160">原始來源可以是 SharePoint 網站、 文件庫或資料夾可供存取的 URL。</span><span class="sxs-lookup"><span data-stu-id="98e13-160">An origin can be a SharePoint site, document library or folder that is accessible by a URL.</span></span> <span data-ttu-id="98e13-161">當您指定原點為您的組織，您會有很大的彈性。</span><span class="sxs-lookup"><span data-stu-id="98e13-161">You have great flexibility when you specify origins for your organization.</span></span> <span data-ttu-id="98e13-162">例如，您可以指定多個原點或想要將所有的 CDN 資產單一原點。</span><span class="sxs-lookup"><span data-stu-id="98e13-162">For example, you can specify multiple origins or a single origin where you want to put all your CDN assets.</span></span> <span data-ttu-id="98e13-163">您可以選擇讓組織的公用或私人原點。</span><span class="sxs-lookup"><span data-stu-id="98e13-163">You can choose to have both public or private origins for your organization.</span></span> <span data-ttu-id="98e13-164">大多數組織會選擇實作兩者的組合。</span><span class="sxs-lookup"><span data-stu-id="98e13-164">Most organizations will choose to implement a combination of the two.</span></span>

<span data-ttu-id="98e13-165">您可以為您原點資料夾或文件庫，例如建立新的容器，並新增您想要提供從 CDN 的檔案。</span><span class="sxs-lookup"><span data-stu-id="98e13-165">You can create new container for your origins such as folders or document libraries, and add files you want to make available from the CDN.</span></span> <span data-ttu-id="98e13-166">如果您有一組特定的資產您想要從 CDN，可用，而且想要限制只有在容器檔案 CDN 資產的集合，這是一個好的方法。</span><span class="sxs-lookup"><span data-stu-id="98e13-166">This is a good approach if you have a specific set of assets you want to be available from the CDN, and want to restrict the set of CDN assets to only those files in the container.</span></span>

<span data-ttu-id="98e13-167">您也可以設定現有網站集合、 網站、 文件庫或資料夾為原點，會讓所有合格的資產容器中可從 CDN。</span><span class="sxs-lookup"><span data-stu-id="98e13-167">You can also configure an existing site collection, site, library or folder as an origin, which will make all eligible assets in the container available from the CDN.</span></span> <span data-ttu-id="98e13-168">您將現有的容器新增為原始來源之前，請務必確定您是知道其內容和權限，所以您不小心公開資產的匿名存取或未經授權的使用者。</span><span class="sxs-lookup"><span data-stu-id="98e13-168">Before you add an existing container as an origin, it's important to make sure you are aware of its contents and permissions so you do not inadvertently expose assets to anonymous access or unauthorized users.</span></span>

<span data-ttu-id="98e13-169">您可以定義_CDN 原則_，以從 CDN 排除您原點中的內容。</span><span class="sxs-lookup"><span data-stu-id="98e13-169">You can define _CDN policies_ to exclude content in your origins from the CDN.</span></span> <span data-ttu-id="98e13-170">CDN 原則排除_檔案類型_及_網站分類_，例如屬性中公用或私人原點資產，且會套用至所有原點的原則中指定 CdnType （私人或公用）。</span><span class="sxs-lookup"><span data-stu-id="98e13-170">CDN policies exclude assets in public or private origins by attributes such as _file type_ and _site classification_, and are applied to all origins of the CdnType (private or public) you specify in the policy.</span></span> <span data-ttu-id="98e13-171">例如，如果您新增包含多個子網站的網站所組成的私用原始來源，您可以定義要排除標示為 [ **2 私人 3 機密**因此內容從站台分類套用從 CDN 將不會服務的站台的原則。</span><span class="sxs-lookup"><span data-stu-id="98e13-171">For example, if you add a private origin consisting of a site that contains multiple subsites, you can define a policy to exclude sites marked as **Confidential** so content from sites with that classification applied will not be served from the CDN.</span></span> <span data-ttu-id="98e13-172">此原則會套用到內容，從_所有_在您新增至 CDN 的私用原點。</span><span class="sxs-lookup"><span data-stu-id="98e13-172">The policy will apply to content from _all_ private origins you have added to the CDN.</span></span>
  
<span data-ttu-id="98e13-173">請記住，原點數目愈大，時間影響也愈大花費 CDN 服務來處理要求。</span><span class="sxs-lookup"><span data-stu-id="98e13-173">Keep in mind that the greater the number of origins, the greater the impact on the time it takes the CDN service to process requests.</span></span> <span data-ttu-id="98e13-174">我們建議您盡可能原點的數目限制。</span><span class="sxs-lookup"><span data-stu-id="98e13-174">We recommend that you limit the number of origins as much as possible.</span></span>
  
### <a name="choose-whether-each-origin-should-be-public-or-private"></a><span data-ttu-id="98e13-175">選擇 [每個原始來源是否應該是公用或私用</span><span class="sxs-lookup"><span data-stu-id="98e13-175">Choose whether each origin should be public or private</span></span>
<a name="CDNOriginChoosePublicPrivate"> </a>

<span data-ttu-id="98e13-176">當您識別來源時，指定是否應該讓它成為_公用_或_私人_。</span><span class="sxs-lookup"><span data-stu-id="98e13-176">When you identify an origin, you specify whether it should be made _public_ or _private_.</span></span> <span data-ttu-id="98e13-177">存取在公用的原點的 CDN 資產為匿名，並在私人原點的 CDN 內容受到動態產生的語彙基元的較高的安全性。</span><span class="sxs-lookup"><span data-stu-id="98e13-177">Access to CDN assets in public origins is anonymous, and CDN content in private origins is secured by dynamically generated tokens for greater security.</span></span> <span data-ttu-id="98e13-178">不論您選擇哪個選項，Microsoft 會所有工作都為您談到 CDN 本身的管理。</span><span class="sxs-lookup"><span data-stu-id="98e13-178">Regardless of which option you choose, Microsoft does all the heavy lifting for you when it comes to administration of the CDN itself.</span></span> <span data-ttu-id="98e13-179">此外，您可以稍後改變心意之後您已設定 CDN 並找出您原點。</span><span class="sxs-lookup"><span data-stu-id="98e13-179">Also, you can change your mind later, after you've set up the CDN and identified your origins.</span></span>

<span data-ttu-id="98e13-180">公用及私人選項提供類似的效能提升，但每個具有唯一的屬性及優點。</span><span class="sxs-lookup"><span data-stu-id="98e13-180">Both public and private options provide similar performance gains, but each has unique attributes and advantages.</span></span>

<span data-ttu-id="98e13-181">匿名，都可以存取**公用**原點 CDN 將 Office 365 內，且主控的資產可以存取資產之 url 的任何人。</span><span class="sxs-lookup"><span data-stu-id="98e13-181">**Public** origins within the Office 365 CDN are accessible anonymously, and hosted assets can be accessed by anyone who has the URL to the asset.</span></span> <span data-ttu-id="98e13-182">因為對公用來源中內容的存取是匿名的，您應該只使用公用來源來快取非敏感性的一般內容，例如 javascript 檔案、指令碼、圖示和影像。</span><span class="sxs-lookup"><span data-stu-id="98e13-182">Because access to content in public origins is anonymous, you should only use them to cache non-sensitive generic content such as javascript files, scripts, icons and images.</span></span>

<span data-ttu-id="98e13-183">Office 365 CDN 內的**私人**來源可提供使用者內容 (例如 SharePoint Online 文件庫、網站和視訊等媒體) 的私人存取。</span><span class="sxs-lookup"><span data-stu-id="98e13-183">**Private** origins within the Office 365 CDN provide private access to user content such as SharePoint Online document libraries, sites and media such as videos.</span></span> <span data-ttu-id="98e13-184">私用原點中內容的存取權受到以動態方式產生的 token，讓其可以只存取與原始文件的文件庫或儲存位置的權限的使用者。</span><span class="sxs-lookup"><span data-stu-id="98e13-184">Access to content in private origins is secured by dynamically generated tokens so it can only be accessed by users with permissions to the original document library or storage location.</span></span> <span data-ttu-id="98e13-185">CDN 將 Office 365 中的私人原點僅可用於 SharePoint Online 內容，您只可以存取透過重新導向私人原點的資產，從您的 SharePoint Online 租用戶。</span><span class="sxs-lookup"><span data-stu-id="98e13-185">Private origins in the Office 365 CDN can only be used for SharePoint Online content, and you can only access assets in private origins through redirection from your SharePoint Online tenant.</span></span>

<span data-ttu-id="98e13-186">您可以閱讀需 CDN 如何存取私用的原始來源中的資產中[使用資產私人原點中的](use-office-365-cdn-with-spo.md#using-assets-in-private-origins)運作。</span><span class="sxs-lookup"><span data-stu-id="98e13-186">You can read more about how CDN access to assets in a private origin works in [Using assets in private origins](use-office-365-cdn-with-spo.md#using-assets-in-private-origins).</span></span>

#### <a name="attributes-and-advantages-of-hosting-assets-in-public-origins"></a><span data-ttu-id="98e13-187">屬性和裝載在公用的原點的資產的優點</span><span class="sxs-lookup"><span data-stu-id="98e13-187">Attributes and advantages of hosting assets in public origins</span></span>
  
- <span data-ttu-id="98e13-188">在公用的原點中公開的資產皆可存取所有人匿名。</span><span class="sxs-lookup"><span data-stu-id="98e13-188">Assets exposed in a public origin are accessible by everyone anonymously.</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="98e13-189">您應該永遠不會將含有使用者資訊或會被視為機密至您的組織中公用的原始來源資源。</span><span class="sxs-lookup"><span data-stu-id="98e13-189">You should never place resources that contain user information or are considered sensitive to your organization in a public origin.</span></span>
- <span data-ttu-id="98e13-190">如果您移除公用原點的資產，資產可能可繼續運作最多 30 天從快取;不過，我們會在 15 分鐘內失效 CDN 中資產的連結。</span><span class="sxs-lookup"><span data-stu-id="98e13-190">If you remove an asset from a public origin, the asset may continue to be available for up to 30 days from the cache; however, we will invalidate links to the asset in the CDN within 15 minutes.</span></span>
- <span data-ttu-id="98e13-191">當您裝載在公用的原始來源中的樣式表 （CSS 檔案） 時，您可以使用程式碼內的相對路徑與 Uri。</span><span class="sxs-lookup"><span data-stu-id="98e13-191">When you host style sheets (CSS files) in a public origin, you can use relative paths and URIs within the code.</span></span> <span data-ttu-id="98e13-192">這表示您可以參照背景影像及其他物件呼叫它的資產的位置相對的位置。</span><span class="sxs-lookup"><span data-stu-id="98e13-192">This means that you can reference the location of background images and other objects relative to the location of the asset that's calling it.</span></span>
- <span data-ttu-id="98e13-193">雖然您可以硬式編碼公用原始來源的 URL，這種做法所以不建議。</span><span class="sxs-lookup"><span data-stu-id="98e13-193">While you can hard code a public origin's URL, doing so is not recommended.</span></span> <span data-ttu-id="98e13-194">這是如果存取 CDN 變成無法使用，URL 不會自動解決您在 SharePoint Online 中的組織，可能會導致中斷的連結和其他錯誤。</span><span class="sxs-lookup"><span data-stu-id="98e13-194">The reason for this is that if access to the CDN becomes unavailable, the URL will not automatically resolve to your organization in SharePoint Online and might result in broken links and other errors.</span></span>
- <span data-ttu-id="98e13-195">預設檔案類型，可供公用原點的.css、.eot、.gif、.ico、.jpeg、.jpg、.js、.map、.png、.svg、.ttf 和.woff。</span><span class="sxs-lookup"><span data-stu-id="98e13-195">The default file types that are included for public origins are .css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, and .woff.</span></span> <span data-ttu-id="98e13-196">您可以指定其他檔案類型。</span><span class="sxs-lookup"><span data-stu-id="98e13-196">You can specify additional file types.</span></span>
- <span data-ttu-id="98e13-197">您可以設定要排除的已識別由您所指定網站分類資產的原則。</span><span class="sxs-lookup"><span data-stu-id="98e13-197">You can configure a policy to exclude assets that have been identified by site classifications that you specify.</span></span> <span data-ttu-id="98e13-198">例如，您可以選擇要排除所有的資產，即使他們所允許的檔案類型，並位於公用原點標示為 「 機密 」 或 「 限制 」。</span><span class="sxs-lookup"><span data-stu-id="98e13-198">For example, you can choose to exclude all assets that are marked as "confidential" or "restricted" even if they are an allowed file type and are located in a public origin.</span></span>

#### <a name="attributes-and-advantages-of-hosting-assets-in-private-origins"></a><span data-ttu-id="98e13-199">屬性和裝載在私人原點的資產的優點</span><span class="sxs-lookup"><span data-stu-id="98e13-199">Attributes and advantages of hosting assets in private origins</span></span>

- <span data-ttu-id="98e13-200">私用原點只能用於 SharePoint Online 的資產。</span><span class="sxs-lookup"><span data-stu-id="98e13-200">Private origins can only be used for SharePoint Online assets.</span></span>
- <span data-ttu-id="98e13-201">如果他們有權限來存取容器使用者僅可從私人原點存取資產。</span><span class="sxs-lookup"><span data-stu-id="98e13-201">Users can only access the assets from a private origin if they have permissions to access the container.</span></span> <span data-ttu-id="98e13-202">無法對這些資產的匿名存取。</span><span class="sxs-lookup"><span data-stu-id="98e13-202">Anonymous access to these assets is prevented.</span></span>
- <span data-ttu-id="98e13-203">在私人原點的資產必須參照從 SharePoint Online 租用戶。</span><span class="sxs-lookup"><span data-stu-id="98e13-203">Assets in private origins must be referred from the SharePoint Online tenant.</span></span> <span data-ttu-id="98e13-204">直接存取私人 CDN 資產無法運作。</span><span class="sxs-lookup"><span data-stu-id="98e13-204">Direct access to private CDN assets does not work.</span></span>
- <span data-ttu-id="98e13-205">如果您從私人原點移除資產，資產可能會繼續以供最多一個小時的時間從快取;不過，我們將會失效中 CDN 資產的連結的資產的移除 15 分鐘內。</span><span class="sxs-lookup"><span data-stu-id="98e13-205">If you remove an asset from the private origin, the asset may continue to be available for up to an hour from the cache; however, we will invalidate links to the asset in the CDN within 15 minutes of the asset's removal.</span></span>
- <span data-ttu-id="98e13-206">.Gif、.ico、.jpeg、.jpg、.js、 和.png，就會是針對私人原點所包含的預設檔案類型。</span><span class="sxs-lookup"><span data-stu-id="98e13-206">The default file types that are included for private origins are .gif, .ico, .jpeg, .jpg, .js, and .png.</span></span> <span data-ttu-id="98e13-207">您可以指定其他檔案類型。</span><span class="sxs-lookup"><span data-stu-id="98e13-207">You can specify additional file types.</span></span>
- <span data-ttu-id="98e13-208">就像公用原點，您可以設定要排除已透過網站分類，即使您使用萬用字元來包含所有的資產資料夾或文件庫內指定識別的資產的原則。</span><span class="sxs-lookup"><span data-stu-id="98e13-208">Just like with public origins, you can configure a policy to exclude assets that have been identified by site classifications that you specify even if you use wildcards to include all assets within a folder or document library.</span></span>

<span data-ttu-id="98e13-209">如需為使用 Office 365 CDN、 一般 CDN 概念，以及您可以使用與 Office 365 租用戶其他 Microsoft Cdn 原因的詳細資訊，請參閱 <<c0>內容傳遞網路。</span><span class="sxs-lookup"><span data-stu-id="98e13-209">For more information about why to use the Office 365 CDN, general CDN concepts, and other Microsoft CDNs you can use with your Office 365 tenant, see [Content Delivery Networks](content-delivery-networks.md).</span></span>

### <a name="default-cdn-origins"></a><span data-ttu-id="98e13-210">預設 CDN 原點</span><span class="sxs-lookup"><span data-stu-id="98e13-210">Default CDN origins</span></span>

<span data-ttu-id="98e13-211">除非另有指定，Office 365 會設定某些預設原點您當您啟用 Office 365 CDN。</span><span class="sxs-lookup"><span data-stu-id="98e13-211">Unless you specify otherwise, Office 365 sets up some default origins for you when you enable the Office 365 CDN.</span></span> <span data-ttu-id="98e13-212">如果您最初選擇不適用於佈建它們，您可以在您完成設定後新增這些原點。</span><span class="sxs-lookup"><span data-stu-id="98e13-212">If you initially opt not to provision them, you can add these origins after you complete setup.</span></span> <span data-ttu-id="98e13-213">除非您了解的略過的預設原點安裝方法的結果，並有這樣的特定原因，您應允許他們要建立當您啟用 CDN。</span><span class="sxs-lookup"><span data-stu-id="98e13-213">Unless you understand the consequences of skipping the setup of default origins and have a specific reason for doing so, you should allow them to be created when you enable the CDN.</span></span>
  
<span data-ttu-id="98e13-214">私人 CDN 原點預設值：</span><span class="sxs-lookup"><span data-stu-id="98e13-214">Default private CDN origins:</span></span>
  
- <span data-ttu-id="98e13-215">\*/userphoto.aspx</span><span class="sxs-lookup"><span data-stu-id="98e13-215">\*/userphoto.aspx</span></span>
- <span data-ttu-id="98e13-216">\*/siteassets</span><span class="sxs-lookup"><span data-stu-id="98e13-216">\*/siteassets</span></span>

<span data-ttu-id="98e13-217">公用 CDN 原點預設值：</span><span class="sxs-lookup"><span data-stu-id="98e13-217">Default public CDN origins:</span></span>
  
- <span data-ttu-id="98e13-218">\*/masterpage</span><span class="sxs-lookup"><span data-stu-id="98e13-218">\*/masterpage</span></span>
- <span data-ttu-id="98e13-219">\*/style 文件庫</span><span class="sxs-lookup"><span data-stu-id="98e13-219">\*/style library</span></span>
- <span data-ttu-id="98e13-220">\*/clientsideassets</span><span class="sxs-lookup"><span data-stu-id="98e13-220">\*/clientsideassets</span></span>

> [!NOTE]
> <span data-ttu-id="98e13-221">_clientsideassets_是已在 2017 年 12 月加到 Office 365 CDN 服務預設公用原點。</span><span class="sxs-lookup"><span data-stu-id="98e13-221">_clientsideassets_ is a default public origin that was added to the Office 365 CDN service in December 2017.</span></span> <span data-ttu-id="98e13-222">此來源必須要有 SharePoint 架構中以解決方案 CDN 工作的順序。</span><span class="sxs-lookup"><span data-stu-id="98e13-222">This origin must be present in order for SharePoint Framework solutions in the CDN to work.</span></span> <span data-ttu-id="98e13-223">如果您啟用 Office 365 CDN 年 12 月 2017 年之前，或當您啟用 CDN 略過的預設原點的安裝程式，您可以手動新增此原點。</span><span class="sxs-lookup"><span data-stu-id="98e13-223">If you enabled the Office 365 CDN prior to December 2017, or if you skipped setup of default origins when you enabled the CDN, you can manually add this origin.</span></span> <span data-ttu-id="98e13-224">如需詳細資訊，請參閱[我的用戶端網頁組件或 SharePoint 架構解決方案無法正常運作](use-office-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working)。</span><span class="sxs-lookup"><span data-stu-id="98e13-224">For more information, see [My client-side web part or SharePoint Framework solution isn't working](use-office-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working).</span></span>

## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a><span data-ttu-id="98e13-225">設定及使用 SharePoint Online 管理命令介面來設定 Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="98e13-225">Set up and configure the Office 365 CDN by using the SharePoint Online Management Shell</span></span>
<a name="CDNSetupinPShell"> </a>

<span data-ttu-id="98e13-226">本節中的程序需要您使用 SharePoint Online 管理命令介面來連線至 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="98e13-226">The procedures in this section require you to use the SharePoint Online Management Shell to connect to SharePoint Online.</span></span> <span data-ttu-id="98e13-227">如需相關指示，請參閱[連線到 SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)。</span><span class="sxs-lookup"><span data-stu-id="98e13-227">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>
  
<span data-ttu-id="98e13-228">完成下列步驟來安裝及設定以裝載您在 SharePoint Online 使用 SharePoint Online 管理命令介面中的資產 CDN。</span><span class="sxs-lookup"><span data-stu-id="98e13-228">Complete these steps to set up and configure the CDN to host your assets in SharePoint Online using the SharePoint Online Management Shell.</span></span>
  
### <a name="enable-your-organization-to-use-the-office-365-cdn"></a><span data-ttu-id="98e13-229">啟用您的組織使用 Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="98e13-229">Enable your organization to use the Office 365 CDN</span></span>

<span data-ttu-id="98e13-230">您的租用戶 CDN 設定進行變更之前，您應該在您的 Office 365 租用戶中擷取私人 CDN 組態的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="98e13-230">Before you make changes to the tenant CDN settings, you should retrieve the current status of the private CDN configuration in your Office 365 tenant.</span></span> <span data-ttu-id="98e13-231">連線至您的租用戶使用 SharePoint Online 管理命令介面：</span><span class="sxs-lookup"><span data-stu-id="98e13-231">Connect to your tenant using the SharePoint Online Management Shell:</span></span>

``` powershell
Connect-SPOService -Url https://contoso-admin.sharepoint.com
```

<span data-ttu-id="98e13-232">現在可用於**取得 SPOTenantCdnEnabled**指令程式從租用戶擷取 CDN 狀態設定：</span><span class="sxs-lookup"><span data-stu-id="98e13-232">Now use the **Get-SPOTenantCdnEnabled** cmdlet to retrieve the CDN status settings from the tenant:</span></span>

``` powershell
Get-SPOTenantCdnEnabled -CdnType <Public | Private>
```

<span data-ttu-id="98e13-233">針對指定 CdnType CDN 的狀態將會輸出至畫面。</span><span class="sxs-lookup"><span data-stu-id="98e13-233">The status of the CDN for the specified CdnType will output to the screen.</span></span>

<span data-ttu-id="98e13-234">使用**設定 SPOTenantCdnEnabled**指令程式來啟用您的組織使用 Office 365 CDN。</span><span class="sxs-lookup"><span data-stu-id="98e13-234">Use the **Set-SPOTenantCdnEnabled** cmdlet to enable your organization to use the Office 365 CDN.</span></span> <span data-ttu-id="98e13-235">您可以啟用您的組織，一次使用公用原點、 私人原點，或兩者。</span><span class="sxs-lookup"><span data-stu-id="98e13-235">You can enable your organization to use public origins, private origins, or both at once.</span></span> <span data-ttu-id="98e13-236">您也可以設定略過的預設原點安裝程式，當您啟用 CDN。</span><span class="sxs-lookup"><span data-stu-id="98e13-236">You can also configure the CDN to skip the setup of default origins when you enable it.</span></span> <span data-ttu-id="98e13-237">您隨時可以稍後在本主題中所述加入這些原點。</span><span class="sxs-lookup"><span data-stu-id="98e13-237">You can always add these origins later as described in this topic.</span></span>
  
<span data-ttu-id="98e13-238">在 SharePoint Online 的 Windows Powershell:</span><span class="sxs-lookup"><span data-stu-id="98e13-238">In Windows Powershell for SharePoint Online:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

<span data-ttu-id="98e13-239">例如，若要啟用您的組織使用公開及私密原點，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="98e13-239">For example, to enable your organization to use both public and private origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

<span data-ttu-id="98e13-240">若要啟用您的組織使用公開及私密原點，但略過預設原點的設定，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="98e13-240">To enable your organization to use both public and private origins but skip setting up the default origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

<span data-ttu-id="98e13-241">當您啟用 Office 365 CDN，並略過的預設原點安裝的潛在影響預設佈建原點的相關資訊，請參閱[預設 CDN 原點](use-office-365-cdn-with-spo.md#default-cdn-origins)。</span><span class="sxs-lookup"><span data-stu-id="98e13-241">See [Default CDN origins](use-office-365-cdn-with-spo.md#default-cdn-origins) for information about the origins that are provisioned by default when you enable the Office 365 CDN, and the potential impact of skipping the setup of default origins.</span></span>

<span data-ttu-id="98e13-242">若要啟用您的組織使用公用原點，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="98e13-242">To enable your organization to use public origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

<span data-ttu-id="98e13-243">若要啟用您的組織使用私人的原點，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="98e13-243">To enable your organization to use private origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

<span data-ttu-id="98e13-244">如需此 cmdlet 的詳細資訊，請參閱 <<c0>設定 SPOTenantCdnEnabled。</span><span class="sxs-lookup"><span data-stu-id="98e13-244">For more information about this cmdlet, see [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span></span>
  
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a><span data-ttu-id="98e13-245">變更要在 Office 365 CDN （選用） 中包含檔案類型的清單</span><span class="sxs-lookup"><span data-stu-id="98e13-245">Change the list of file types to include in the Office 365 CDN (Optional)</span></span>
<a name="Office365CDNforSPOFileType"> </a>

> [!TIP]
> <span data-ttu-id="98e13-246">當您使用**組 SPOTenantCdnPolicy** cmdlet 定義的檔案類型時，您覆寫目前所定義的清單。</span><span class="sxs-lookup"><span data-stu-id="98e13-246">When you define file types by using the **Set-SPOTenantCdnPolicy** cmdlet, you overwrite the currently defined list.</span></span> <span data-ttu-id="98e13-247">如果您想要新增其他檔案類型至清單時，指令程式先使用來找出哪些檔案類型已允許納入以及您新的清單。</span><span class="sxs-lookup"><span data-stu-id="98e13-247">If you want to add additional file types to the list, use the cmdlet first to find out what file types are already allowed and include them in the list along with your new ones.</span></span>
  
<span data-ttu-id="98e13-248">使用**設定 SPOTenantCdnPolicy**指令程式來定義可由公用和私人原點 CDN 中主控的靜態檔案類型。</span><span class="sxs-lookup"><span data-stu-id="98e13-248">Use the **Set-SPOTenantCdnPolicy** cmdlet to define static file types that can be hosted by public and private origins in the CDN.</span></span> <span data-ttu-id="98e13-249">根據預設，常見的資產類型為何，允許範例.css、.gif、.jpg、 及.js。</span><span class="sxs-lookup"><span data-stu-id="98e13-249">By default, common asset types are allowed, for example .css, .gif, .jpg, and .js.</span></span>

<span data-ttu-id="98e13-250">在 SharePoint Online 的 Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="98e13-250">In Windows PowerShell for SharePoint Online:</span></span>

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

<span data-ttu-id="98e13-251">例如，若要啟用 CDN 主機.css 和.png 檔案，您輸入此命令：</span><span class="sxs-lookup"><span data-stu-id="98e13-251">For example, to enable the CDN to host .css and .png files, you would enter the command:</span></span>

``` powershell
Set-SPOTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

<span data-ttu-id="98e13-252">若要查看 CDN 目前允許哪些檔案類型，請使用**Get SPOTenantCdnPolicies** cmdlet:</span><span class="sxs-lookup"><span data-stu-id="98e13-252">To see what file types are currently allowed by the CDN, use the **Get-SPOTenantCdnPolicies** cmdlet:</span></span>

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="98e13-253">如需這些 cmdlet 的詳細資訊，請參閱[設定 SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx)和[取得 SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx)。</span><span class="sxs-lookup"><span data-stu-id="98e13-253">For more information about these cmdlets, see [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) and [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span></span>
  
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a><span data-ttu-id="98e13-254">變更您想要排除在 Office 365 CDN （選用） 的網站分類的清單</span><span class="sxs-lookup"><span data-stu-id="98e13-254">Change the list of site classifications you want to exclude from the Office 365 CDN (Optional)</span></span>
<a name="Office365CDNforSPOSiteClassification"> </a>

> [!TIP]
> <span data-ttu-id="98e13-255">您可以使用**組 SPOTenantCdnPolicy**指令程式，以排除網站分類，當您覆寫目前所定義的清單。</span><span class="sxs-lookup"><span data-stu-id="98e13-255">When you exclude site classifications by using the **Set-SPOTenantCdnPolicy** cmdlet, you overwrite the currently defined list.</span></span> <span data-ttu-id="98e13-256">如果您想要排除其他網站分類，使用以找出已被排除哪些分類並再將其新增以及您新的第一次的指令程式進行。</span><span class="sxs-lookup"><span data-stu-id="98e13-256">If you want to exclude additional site classifications, use the cmdlet first to find out what classifications are already excluded and then add them along with your new ones.</span></span>

<span data-ttu-id="98e13-257">使用**組 SPOTenantCdnPolicy**指令程式來排除不想要提供透過 CDN 的網站分類。</span><span class="sxs-lookup"><span data-stu-id="98e13-257">Use the **Set-SPOTenantCdnPolicy** cmdlet to exclude site classifications that you do not want to make available over the CDN.</span></span> <span data-ttu-id="98e13-258">根據預設，會不排除任何網站分類。</span><span class="sxs-lookup"><span data-stu-id="98e13-258">By default, no site classifications are excluded.</span></span>

<span data-ttu-id="98e13-259">在 SharePoint Online 的 Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="98e13-259">In Windows PowerShell for SharePoint Online:</span></span>

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

<span data-ttu-id="98e13-260">若要查看哪些網站分類目前受到限制，請使用**Get SPOTenantCdnPolicies** cmdlet:</span><span class="sxs-lookup"><span data-stu-id="98e13-260">To see what site classifications are currently restricted, use the **Get-SPOTenantCdnPolicies** cmdlet:</span></span>

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="98e13-261">會傳回的屬性，而_IncludeFileExtensions_、 _ExcludeRestrictedSiteClassifications_ _ExcludeIfNoScriptDisabled_。</span><span class="sxs-lookup"><span data-stu-id="98e13-261">The properties that will be returned are _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ and _ExcludeIfNoScriptDisabled_.</span></span>

<span data-ttu-id="98e13-262">_IncludeFileExtensions_屬性包含將服務從 CDN 的副檔名清單。</span><span class="sxs-lookup"><span data-stu-id="98e13-262">The _IncludeFileExtensions_ property contains the list of file extensions that will be served from the CDN.</span></span>

> [!NOTE]
> <span data-ttu-id="98e13-263">預設的副檔名的方式不同公用和私人之間。</span><span class="sxs-lookup"><span data-stu-id="98e13-263">The default file extensions are different between public and private.</span></span>

<span data-ttu-id="98e13-264">_ExcludeRestrictedSiteClassifications_屬性會包含您想要排除從 CDN 網站分類。</span><span class="sxs-lookup"><span data-stu-id="98e13-264">The _ExcludeRestrictedSiteClassifications_ property contains the site classifications that you want to exclude from the CDN.</span></span> <span data-ttu-id="98e13-265">例如，您可以排除標示為 [ **2 私人 3 機密**因此內容從站台分類套用從 CDN 將不會服務的網站。</span><span class="sxs-lookup"><span data-stu-id="98e13-265">For example, you can exclude sites marked as **Confidential** so content from sites with that classification applied will not be served from the CDN.</span></span>

<span data-ttu-id="98e13-266">_ExcludeIfNoScriptDisabled_屬性會從網站層級_NoScript_屬性設定為基礎的 CDN 排除內容。</span><span class="sxs-lookup"><span data-stu-id="98e13-266">The _ExcludeIfNoScriptDisabled_ property excludes content from the CDN based on the site-level _NoScript_ attribute settings.</span></span> <span data-ttu-id="98e13-267">根據預設， _NoScript_屬性設為 [**已啟用**_新式_網站和**已停用**的_傳統_網站。</span><span class="sxs-lookup"><span data-stu-id="98e13-267">By default, the _NoScript_ attribute is set to **Enabled** for _Modern_ sites and **Disabled** for _Classic_ sites.</span></span> <span data-ttu-id="98e13-268">這取決於您的租用戶設定。</span><span class="sxs-lookup"><span data-stu-id="98e13-268">This depends on your tenant settings.</span></span>

<span data-ttu-id="98e13-269">如需這些 cmdlet 的詳細資訊，請參閱[設定 SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx)和[取得 SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx)。</span><span class="sxs-lookup"><span data-stu-id="98e13-269">For more information about these cmdlets, see [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) and [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span></span>
  
### <a name="add-an-origin-for-your-assets"></a><span data-ttu-id="98e13-270">新增您資產的原始來源</span><span class="sxs-lookup"><span data-stu-id="98e13-270">Add an origin for your assets</span></span>
<a name="Office365CDNforSPOOrigin"> </a>

<span data-ttu-id="98e13-271">使用**Add SPOTenantCdnOrigin**指令程式來定義原點。</span><span class="sxs-lookup"><span data-stu-id="98e13-271">Use the **Add-SPOTenantCdnOrigin** cmdlet to define an origin.</span></span> <span data-ttu-id="98e13-272">您可以定義多個原點。</span><span class="sxs-lookup"><span data-stu-id="98e13-272">You can define multiple origins.</span></span> <span data-ttu-id="98e13-273">原點是指向 SharePoint 文件庫或資料夾，其中包含您想要裝載的 CDN 資產的 URL。</span><span class="sxs-lookup"><span data-stu-id="98e13-273">The origin is a URL that points to a SharePoint library or folder that contains the assets that you want to be hosted by the CDN.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="98e13-274">您應該永遠不會將含有使用者資訊或會被視為機密至您的組織中公用的原始來源資源。</span><span class="sxs-lookup"><span data-stu-id="98e13-274">You should never place resources that contain user information or are considered sensitive to your organization in a public origin.</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

<span data-ttu-id="98e13-275">_路徑_的值是文件庫或資料夾，其中包含資產的路徑。</span><span class="sxs-lookup"><span data-stu-id="98e13-275">The value of _path_ is the path to the library or folder that contains the assets.</span></span> <span data-ttu-id="98e13-276">您可以使用萬用字元，除了相對路徑。</span><span class="sxs-lookup"><span data-stu-id="98e13-276">You can use wildcards in addition to relative paths.</span></span> <span data-ttu-id="98e13-277">原點支援加至 URL 的萬用字元。</span><span class="sxs-lookup"><span data-stu-id="98e13-277">Origins support wildcards prepended to the URL.</span></span> <span data-ttu-id="98e13-278">這可讓您建立橫跨多個站台的原點。</span><span class="sxs-lookup"><span data-stu-id="98e13-278">This allows you to create origins that span multiple sites.</span></span> <span data-ttu-id="98e13-279">例如，若要包含在所有網站的 masterpages 資料夾中的所有資產內 CDN 公開原點，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="98e13-279">For example, to include all of the assets in the masterpages folder for all of your sites as a public origin within the CDN, type the following command:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

- <span data-ttu-id="98e13-280">萬用字元修飾詞 \***/** 只用於起點處的路徑，並會比對 [指定 URL] 下的所有 URL 區段。</span><span class="sxs-lookup"><span data-stu-id="98e13-280">The wildcard modifier \***/** can only be used at the beginning of the path, and will match all URL segments under the specified URL.</span></span>
- <span data-ttu-id="98e13-281">路徑可以指向文件庫、 資料夾或網站。</span><span class="sxs-lookup"><span data-stu-id="98e13-281">The path can point to a document library, folder or site.</span></span> <span data-ttu-id="98e13-282">例如，路徑 _\* / site1_會比對網站下的所有文件庫。</span><span class="sxs-lookup"><span data-stu-id="98e13-282">For example, the path _\*/site1_ will match all the document libraries under the site.</span></span>

<span data-ttu-id="98e13-283">您可以新增原點搭配使用的完整路徑或相對路徑的特定路徑。</span><span class="sxs-lookup"><span data-stu-id="98e13-283">You can add an origin with a specific path using either a relative path or a full path.</span></span>

<span data-ttu-id="98e13-284">本範例會使用相對路徑的特定網站新增私人原點 siteassets 文件庫：</span><span class="sxs-lookup"><span data-stu-id="98e13-284">This example adds a private origin of the siteassets library on a specific site using a relative path:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

<span data-ttu-id="98e13-285">本範例會在網站集合的網站資產使用的完整路徑的文件庫中新增私人原點_folder1_資料夾：</span><span class="sxs-lookup"><span data-stu-id="98e13-285">This example adds a private origin of the _folder1_ folder in the site collection's site assets library using the full path:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl “https://contoso.sharepoint.com/sites/test/siteassets/folder1”
```

<span data-ttu-id="98e13-286">如需這個命令和語法的詳細資訊，請參閱 < <b0>Add SPOTenantCdnOrigin</b0>。</span><span class="sxs-lookup"><span data-stu-id="98e13-286">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>

> [!NOTE]
> <span data-ttu-id="98e13-287">在私人原點共用從原點的資產必須發佈之前他們可從 CDN 的主要版本。</span><span class="sxs-lookup"><span data-stu-id="98e13-287">In private origins, assets being shared from an origin must have a major version published before they can be accessed from the CDN.</span></span>
  
<span data-ttu-id="98e13-288">一旦您已經執行此命令，系統會設定同步處理跨資料中心。</span><span class="sxs-lookup"><span data-stu-id="98e13-288">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="98e13-289">這可能需要長達 15 分鐘。</span><span class="sxs-lookup"><span data-stu-id="98e13-289">This can take up to 15 minutes.</span></span>
  
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a><span data-ttu-id="98e13-290">範例： 設定您的主版頁面和樣式庫公用原點的 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="98e13-290">Example: Configure a public origin for your master pages and for your style library for SharePoint Online</span></span>
<a name="ExamplePublicOrigin"> </a>

<span data-ttu-id="98e13-291">一般而言，這些原點是為您設定預設當您啟用 Office 365 CDN。</span><span class="sxs-lookup"><span data-stu-id="98e13-291">Normally, these origins are set up for you by default when you enable the Office 365 CDN.</span></span> <span data-ttu-id="98e13-292">不過，如果您想要手動啟用，請遵循下列步驟。</span><span class="sxs-lookup"><span data-stu-id="98e13-292">However, if you want to enable them manually, follow these steps.</span></span>
  
- <span data-ttu-id="98e13-293">使用**Add SPOTenantCdnOrigin** cmdlet 來定義樣式庫為公用的原點而言。</span><span class="sxs-lookup"><span data-stu-id="98e13-293">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the style library as a public origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

- <span data-ttu-id="98e13-294">使用**Add SPOTenantCdnOrigin** cmdlet 來定義為公用的原始來源的主版頁面。</span><span class="sxs-lookup"><span data-stu-id="98e13-294">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the master pages as a public origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

<span data-ttu-id="98e13-295">如需這個命令和語法的詳細資訊，請參閱 < <b0>Add SPOTenantCdnOrigin</b0>。</span><span class="sxs-lookup"><span data-stu-id="98e13-295">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>

<span data-ttu-id="98e13-296">一旦您已經執行此命令，系統會設定同步處理跨資料中心。</span><span class="sxs-lookup"><span data-stu-id="98e13-296">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="98e13-297">這可能需要長達 15 分鐘。</span><span class="sxs-lookup"><span data-stu-id="98e13-297">This can take up to 15 minutes.</span></span>

### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a><span data-ttu-id="98e13-298">範例： 設定您的網站資產、 網站頁面和發佈的映像私人原點的 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="98e13-298">Example: Configure a private origin for your site assets, site pages, and publishing images for SharePoint Online</span></span>
<a name="ExamplePrivateOrigin"> </a>

- <span data-ttu-id="98e13-299">使用**Add SPOTenantCdnOrigin** cmdlet 來定義為私人的原始來源的 [網站資產] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="98e13-299">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the site assets folder as a private origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

- <span data-ttu-id="98e13-300">使用**Add SPOTenantCdnOrigin** cmdlet 來定義網站的 [頁面] 資料夾為私人的原點而言。</span><span class="sxs-lookup"><span data-stu-id="98e13-300">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the site pages folder as a private origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

- <span data-ttu-id="98e13-301">使用**Add SPOTenantCdnOrigin** cmdlet 來定義為私人的原始來源的發佈的 [圖像] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="98e13-301">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the publishing images folder as a private origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

<span data-ttu-id="98e13-302">如需這個命令和語法的詳細資訊，請參閱 < <b0>Add SPOTenantCdnOrigin</b0>。</span><span class="sxs-lookup"><span data-stu-id="98e13-302">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>

<span data-ttu-id="98e13-303">一旦您已經執行此命令，系統會設定同步處理跨資料中心。</span><span class="sxs-lookup"><span data-stu-id="98e13-303">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="98e13-304">這可能需要長達 15 分鐘。</span><span class="sxs-lookup"><span data-stu-id="98e13-304">This can take up to 15 minutes.</span></span>

### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a><span data-ttu-id="98e13-305">範例： 設定 SharePoint online 網站集合的私用原始來源</span><span class="sxs-lookup"><span data-stu-id="98e13-305">Example: Configure a private origin for a site collection for SharePoint Online</span></span>
<a name="ExamplePrivateOriginSiteCollection"> </a>

<span data-ttu-id="98e13-306">若要定義為私人的原始來源的網站集合使用**Add SPOTenantCdnOrigin** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="98e13-306">Use the **Add-SPOTenantCdnOrigin** cmdlet to define a site collection as a private origin.</span></span> <span data-ttu-id="98e13-307">例如：</span><span class="sxs-lookup"><span data-stu-id="98e13-307">For example:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

<span data-ttu-id="98e13-308">如需這個命令和語法的詳細資訊，請參閱 < <b0>Add SPOTenantCdnOrigin</b0>。</span><span class="sxs-lookup"><span data-stu-id="98e13-308">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>
  
<span data-ttu-id="98e13-309">一旦您已經執行此命令，系統會設定同步處理跨資料中心。</span><span class="sxs-lookup"><span data-stu-id="98e13-309">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="98e13-310">您可能會看到 SharePoint Online 租用戶連線到 CDN 服務如預期_設定擱置_郵件。</span><span class="sxs-lookup"><span data-stu-id="98e13-310">You may see a _Configuration pending_ message which is expected as the SharePoint Online tenant connects to the CDN service.</span></span> <span data-ttu-id="98e13-311">這可能需要長達 15 分鐘。</span><span class="sxs-lookup"><span data-stu-id="98e13-311">This can take up to 15 minutes.</span></span>

### <a name="manage-the-office-365-cdn"></a><span data-ttu-id="98e13-312">管理 Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="98e13-312">Manage the Office 365 CDN</span></span>
<a name="CDNManage"> </a>

<span data-ttu-id="98e13-313">一旦您已設定好 CDN，您可以變更您的組態更新內容，或為您的需求改變時，這一節所述。</span><span class="sxs-lookup"><span data-stu-id="98e13-313">Once you've set up the CDN, you can make changes to your configuration as you update content or as your needs change, as described in this section.</span></span>
  
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a><span data-ttu-id="98e13-314">新增、 更新或移除 Office 365 CDN 資產</span><span class="sxs-lookup"><span data-stu-id="98e13-314">Add, update, or remove assets from the Office 365 CDN</span></span>
<a name="Office365CDNforSPOaddremoveasset"> </a>

<span data-ttu-id="98e13-315">當您完成設定步驟時，您可以新增新的資產，並更新或移除現有的資產，每當您想要。</span><span class="sxs-lookup"><span data-stu-id="98e13-315">Once you've completed the setup steps, you can add new assets, and update or remove existing assets whenever you want.</span></span> <span data-ttu-id="98e13-316">只要變更您的資料夾或識別為原始來源的 SharePoint 文件庫中資產。</span><span class="sxs-lookup"><span data-stu-id="98e13-316">Just make your changes to the assets in the folder or SharePoint library that you identified as an origin.</span></span> <span data-ttu-id="98e13-317">如果您新增新的資產，它是透過 CDN 立即。</span><span class="sxs-lookup"><span data-stu-id="98e13-317">If you add a new asset, it is available through the CDN immediately.</span></span> <span data-ttu-id="98e13-318">不過，如果您更新資產，它將會需要最多 15 分鐘的傳播並成為 CDN 中可用的新複本。</span><span class="sxs-lookup"><span data-stu-id="98e13-318">However, if you update the asset, it will take up to 15 minutes for the new copy to propagate and become available in the CDN.</span></span>
  
<span data-ttu-id="98e13-319">如果您需要擷取原點的位置，您可以使用**Get-SPOTenantCdnOrigins**指令程式。</span><span class="sxs-lookup"><span data-stu-id="98e13-319">If you need to retrieve the location of the origin, you can use the **Get-SPOTenantCdnOrigins** cmdlet.</span></span> <span data-ttu-id="98e13-320">如需如何使用此指令程式的資訊，請參閱 < <b0>Get SPOTenantCdnOrigins</b0>。</span><span class="sxs-lookup"><span data-stu-id="98e13-320">For information on how to use this cmdlet, see [Get-SPOTenantCdnOrigins](https://technet.microsoft.com/en-us/library/mt790770.aspx).</span></span>
  
#### <a name="remove-an-origin-from-the-office-365-cdn"></a><span data-ttu-id="98e13-321">從 CDN 將 Office 365 中移除原始來源</span><span class="sxs-lookup"><span data-stu-id="98e13-321">Remove an origin from the Office 365 CDN</span></span>
<a name="Office365CDNforSPORemoveOrigin"> </a>

<span data-ttu-id="98e13-322">您可以移除資料夾或識別為原始來源的 SharePoint 文件庫的存取權。</span><span class="sxs-lookup"><span data-stu-id="98e13-322">You can remove access to a folder or SharePoint library that you identified as an origin.</span></span> <span data-ttu-id="98e13-323">若要這麼做，請使用**Remove SPOTenantCdnOrigin**指令程式。</span><span class="sxs-lookup"><span data-stu-id="98e13-323">To do this, use the **Remove-SPOTenantCdnOrigin** cmdlet.</span></span>

``` powershell
Remove-SPOTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

<span data-ttu-id="98e13-324">如需如何使用此指令程式的資訊，請參閱 <<c0>移除 SPOTenantCdnOrigin。</span><span class="sxs-lookup"><span data-stu-id="98e13-324">For information on how to use this cmdlet, see [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx).</span></span>
  
#### <a name="modify-an-origin-in-the-office-365-cdn"></a><span data-ttu-id="98e13-325">修改 CDN 將 Office 365 中的原始來源</span><span class="sxs-lookup"><span data-stu-id="98e13-325">Modify an origin in the Office 365 CDN</span></span>
<a name="Office365CDNforSPORemoveOrigin"> </a>

<span data-ttu-id="98e13-326">您無法修改已建立的原始來源。</span><span class="sxs-lookup"><span data-stu-id="98e13-326">You cannot modify an origin you've created.</span></span> <span data-ttu-id="98e13-327">相反地，移除原始來源，然後加入一個新。</span><span class="sxs-lookup"><span data-stu-id="98e13-327">Instead, remove the origin and then add a new one.</span></span> <span data-ttu-id="98e13-328">如需詳細資訊，請參閱[移除從 Office 365 CDN 原始來源](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin)及[新增您資產的原點而言](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin)。</span><span class="sxs-lookup"><span data-stu-id="98e13-328">For more information, see [To remove an origin from the Office 365 CDN](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) and [To add an origin for your assets](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).</span></span>
  
#### <a name="disable-the-office-365-cdn"></a><span data-ttu-id="98e13-329">停用 Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="98e13-329">Disable the Office 365 CDN</span></span>
<a name="Office365CDNforSPODisable"> </a>

<span data-ttu-id="98e13-330">若要停用組織 CDN 使用**組 SPOTenantCdnEnabled**指令程式。</span><span class="sxs-lookup"><span data-stu-id="98e13-330">Use the **Set-SPOTenantCdnEnabled** cmdlet to disable the CDN for your organization.</span></span> <span data-ttu-id="98e13-331">如果您有兩個公用和私人原點啟用 CDN，您需要執行的指令程式兩次，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="98e13-331">If you have both the public and private origins enabled for the CDN, you need to run the cmdlet twice as shown in the following examples.</span></span>
  
<span data-ttu-id="98e13-332">若要停用使用的公用原點 CDN 中，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="98e13-332">To disable use of public origins in the CDN, enter the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

<span data-ttu-id="98e13-333">若要停用的私用的原點 CDN 中使用，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="98e13-333">To disable use of the private origins in the CDN, enter the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

<span data-ttu-id="98e13-334">如需此 cmdlet 的詳細資訊，請參閱 <<c0>設定 SPOTenantCdnEnabled。</span><span class="sxs-lookup"><span data-stu-id="98e13-334">For more information about this cmdlet, see [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span></span>

## <a name="set-up-and-configure-the-office-365-cdn-using-the-office-365-cli"></a><span data-ttu-id="98e13-335">安裝及設定 Office 365 CDN 使用 Office 365 CLI</span><span class="sxs-lookup"><span data-stu-id="98e13-335">Set up and configure the Office 365 CDN using the Office 365 CLI</span></span>
<a name="CDNSetupinCLI"> </a>

<span data-ttu-id="98e13-336">本節中的程序需要您已安裝[Office 365 CLI](https://aka.ms/o365cli)。</span><span class="sxs-lookup"><span data-stu-id="98e13-336">The procedures in this section require that you have installed the [Office 365 CLI](https://aka.ms/o365cli).</span></span> <span data-ttu-id="98e13-337">接下來，連線到 SharePoint Online 租用戶使用[spo 連線](https://pnp.github.io/office365-cli/cmd/spo/connect/)] 命令。</span><span class="sxs-lookup"><span data-stu-id="98e13-337">Next, connect to your SharePoint Online tenant using the [spo connect](https://pnp.github.io/office365-cli/cmd/spo/connect/) command.</span></span>

<span data-ttu-id="98e13-338">完成下列步驟來安裝及設定以裝載您在 SharePoint Online 中使用 Office 365 CLI 資產 CDN。</span><span class="sxs-lookup"><span data-stu-id="98e13-338">Complete these steps to set up and configure the CDN to host your assets in SharePoint Online using the Office 365 CLI.</span></span>

### <a name="enable-the-office-365-cdn"></a><span data-ttu-id="98e13-339">啟用 Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="98e13-339">Enable the Office 365 CDN</span></span>

<span data-ttu-id="98e13-340">您可以使用[spo cdn set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-set/)命令租用戶中管理 Office 365 CDN 的狀態。</span><span class="sxs-lookup"><span data-stu-id="98e13-340">You can manage the state of the Office 365 CDN in your tenant using the [spo cdn set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-set/) command.</span></span>

<span data-ttu-id="98e13-341">若要啟用 Office 365 公用 CDN 租用戶中執行：</span><span class="sxs-lookup"><span data-stu-id="98e13-341">To enable the Office 365 Public CDN in your tenant execute:</span></span>

```sh
spo cdn set --type Public --enabled true
```

<span data-ttu-id="98e13-342">若要啟用 Office 365 SharePoint CDN，請執行：</span><span class="sxs-lookup"><span data-stu-id="98e13-342">To enable the Office 365 SharePoint CDN, execute:</span></span>

```sh
spo cdn set --type Private --enabled true
```

#### <a name="view-the-current-status-of-the-office-365-cdn"></a><span data-ttu-id="98e13-343">檢視 Office 365 CDN 的目前狀態</span><span class="sxs-lookup"><span data-stu-id="98e13-343">View the current status of the Office 365 CDN</span></span>

<span data-ttu-id="98e13-344">若要檢查 Office 365 CDN 的特定類型是啟用還是停用，請使用[spo cdn get](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-get/)命令。</span><span class="sxs-lookup"><span data-stu-id="98e13-344">To check if the particular type of Office 365 CDN is enabled or disabled, use the [spo cdn get](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-get/) command.</span></span>

<span data-ttu-id="98e13-345">若要檢查 Office 365 公用 CDN 是否已啟用，請執行：</span><span class="sxs-lookup"><span data-stu-id="98e13-345">To check if the Office 365 Public CDN is enabled, execute:</span></span>

```sh
spo cdn get --type Public
```

### <a name="view-the-office-365-cdn-origins"></a><span data-ttu-id="98e13-346">檢視 Office 365 CDN 原點</span><span class="sxs-lookup"><span data-stu-id="98e13-346">View the Office 365 CDN origins</span></span>

<span data-ttu-id="98e13-347">若要檢視目前設定的 Office 365 公用 CDN 原點執行：</span><span class="sxs-lookup"><span data-stu-id="98e13-347">To view the currently configured Office 365 Public CDN origins execute:</span></span>

```sh
spo cdn origin list --type Public
```

<span data-ttu-id="98e13-348">當您啟用 Office 365 CDN 預設佈建原點的相關資訊，請參閱[預設 CDN 原點](use-office-365-cdn-with-spo.md#default-cdn-origins)。</span><span class="sxs-lookup"><span data-stu-id="98e13-348">See [Default CDN origins](use-office-365-cdn-with-spo.md#default-cdn-origins) for information about the origins that are provisioned by default when you enable the Office 365 CDN.</span></span>

### <a name="add-an-office-365-cdn-origin"></a><span data-ttu-id="98e13-349">新增 Office 365 CDN 原始來源</span><span class="sxs-lookup"><span data-stu-id="98e13-349">Add an Office 365 CDN origin</span></span>

> [!NOTE]
> <span data-ttu-id="98e13-350">您應該永遠不會將會被視為機密的 SharePoint 文件庫設定為公用的原始來源組織的資源。</span><span class="sxs-lookup"><span data-stu-id="98e13-350">You should never place resources that are considered sensitive to your organization in a SharePoint document library configured as a public origin.</span></span>

<span data-ttu-id="98e13-351">使用[spo cdn 原點 add](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-add/)命令來定義 CDN 原點。</span><span class="sxs-lookup"><span data-stu-id="98e13-351">Use the [spo cdn origin add](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-add/) command to define a CDN origin.</span></span> <span data-ttu-id="98e13-352">您可以定義多個原點。</span><span class="sxs-lookup"><span data-stu-id="98e13-352">You can define multiple origins.</span></span> <span data-ttu-id="98e13-353">原點是指向 SharePoint 文件庫或資料夾，其中包含您想要裝載的 CDN 資產的 URL。</span><span class="sxs-lookup"><span data-stu-id="98e13-353">The origin is a URL that points to a SharePoint library or folder that contains the assets that you want to be hosted by the CDN.</span></span>

```sh
spo cdn origin add --type [Public | Private] --origin <path>
```

<span data-ttu-id="98e13-354">其中`path`是包含資產的資料夾路徑。</span><span class="sxs-lookup"><span data-stu-id="98e13-354">Where `path` is the path to the folder that contains the assets.</span></span> <span data-ttu-id="98e13-355">您可以使用萬用字元，除了相對路徑。</span><span class="sxs-lookup"><span data-stu-id="98e13-355">You can use wildcards in addition to relative paths.</span></span>

<span data-ttu-id="98e13-356">若要為公用的原始來源的所有網站**主版頁面圖庫**中包含所有的資產，請執行：</span><span class="sxs-lookup"><span data-stu-id="98e13-356">To include all assets in the **Master Page Gallery** of all sites as a public origin, execute:</span></span>

```sh
spo cdn origin add --type Public --origin */masterpage
```

<span data-ttu-id="98e13-357">若要設定特定網站集合的私用原始來源，請執行：</span><span class="sxs-lookup"><span data-stu-id="98e13-357">To configure a private origin for a specific site collection, execute:</span></span>

```sh
spo cdn origin add --type Private --origin sites/site1/siteassets
```

> [!NOTE]
> <span data-ttu-id="98e13-358">新增 CDN 原點之後, 可能需要 15 分鐘的時間，您就能夠擷取透過 CDN 服務的檔案。</span><span class="sxs-lookup"><span data-stu-id="98e13-358">After adding a CDN origin, it might take up to 15 minutes for you to be able to retrieve files via the CDN service.</span></span> <span data-ttu-id="98e13-359">您可以驗證是否已經使用[spo cdn 原點清單](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/)命令已啟用的特定的原點而言。</span><span class="sxs-lookup"><span data-stu-id="98e13-359">You can verify if the particular origin has already been enabled using the [spo cdn origin list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) command.</span></span>

### <a name="remove-an-office-365-cdn-origin"></a><span data-ttu-id="98e13-360">移除 Office 365 CDN 原始來源</span><span class="sxs-lookup"><span data-stu-id="98e13-360">Remove an Office 365 CDN origin</span></span>

<span data-ttu-id="98e13-361">使用[spo cdn 原點移除](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-remove/)命令來移除指定的 CDN 類型 CDN 原點。</span><span class="sxs-lookup"><span data-stu-id="98e13-361">Use the [spo cdn origin remove](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-remove/) command to remove a CDN origin for the specified CDN type.</span></span>

<span data-ttu-id="98e13-362">若要從 CDN 組態移除公用的原點而言，請執行：</span><span class="sxs-lookup"><span data-stu-id="98e13-362">To remove a public origin from the CDN configuration, execute:</span></span>

```sh
spo cdn origin remove --type Public --origin */masterpage
```

> [!NOTE]
> <span data-ttu-id="98e13-363">移除 CDN 原點不會影響比對該原點任何文件庫中所儲存的檔案。</span><span class="sxs-lookup"><span data-stu-id="98e13-363">Removing a CDN origin doesn't affect the files stored in any document library matching that origin.</span></span> <span data-ttu-id="98e13-364">如果已使用其 SharePoint URL 已參考這些資產，SharePoint 會自動切換回原始 URL 指向文件庫。</span><span class="sxs-lookup"><span data-stu-id="98e13-364">If these assets have been referenced using their SharePoint URL, SharePoint will automatically switch back to the original URL pointing to the document library.</span></span> <span data-ttu-id="98e13-365">如果不過，您必須使用公用 CDN URL 已參照資產，然後移除原始會中斷連結，並將必須手動將它們變更。</span><span class="sxs-lookup"><span data-stu-id="98e13-365">If, however, assets have been referenced using a public CDN URL, then removing the origin will break the link and you will need to manually change them.</span></span>

### <a name="modify-an-office-365-cdn-origin"></a><span data-ttu-id="98e13-366">修改 Office 365 CDN 原始來源</span><span class="sxs-lookup"><span data-stu-id="98e13-366">Modify an Office 365 CDN origin</span></span>

<span data-ttu-id="98e13-367">您不能修改現有的 CDN 原點。</span><span class="sxs-lookup"><span data-stu-id="98e13-367">It's not possible to modify an existing CDN origin.</span></span> <span data-ttu-id="98e13-368">相反地，您應該移除先前定義的 CDN 原點使用`spo cdn origin remove`命令，並新增新一個使用`spo cdn origin add`命令。</span><span class="sxs-lookup"><span data-stu-id="98e13-368">Instead, you should remove the previously defined CDN origin using the `spo cdn origin remove` command and add a new one using the `spo cdn origin add` command.</span></span>

### <a name="change-the-types-of-files-to-include-in-the-office-365-cdn"></a><span data-ttu-id="98e13-369">變更要在 Office 365 CDN 中包含檔案的類型</span><span class="sxs-lookup"><span data-stu-id="98e13-369">Change the types of files to include in the Office 365 CDN</span></span>

<span data-ttu-id="98e13-370">根據預設，下列檔案類型中隨附的 CDN: _.css、.eot、.gif、.ico、.jpeg、.jpg、.js、.map、.png、.svg、.ttf 和.woff_。</span><span class="sxs-lookup"><span data-stu-id="98e13-370">By default, the following file types are included in the CDN: _.css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, and .woff_.</span></span> <span data-ttu-id="98e13-371">如果您需要在 CDN 中包含其他檔案類型，您可以變更 CDN 組態使用[spo cdn 原則設定](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/)] 指令。</span><span class="sxs-lookup"><span data-stu-id="98e13-371">If you need to include additional file types in the CDN, you can change the CDN configuration using the [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) command.</span></span>

> [!NOTE]
> <span data-ttu-id="98e13-372">在變更的檔案類型清單，請您覆寫目前所定義的清單。</span><span class="sxs-lookup"><span data-stu-id="98e13-372">When changing the list of file types, you overwrite the currently defined list.</span></span> <span data-ttu-id="98e13-373">如果您想要包含其他檔案類型，先使用[spo cdn 原則] 清單中](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/)命令，以找出目前設定的檔案類型。</span><span class="sxs-lookup"><span data-stu-id="98e13-373">If you want to include additional file types, first use the [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) command to find out which file types are currently configured.</span></span>

<span data-ttu-id="98e13-374">若要將_JSON_檔案類型新增至公用 CDN 中包含的檔案類型的預設清單，請執行：</span><span class="sxs-lookup"><span data-stu-id="98e13-374">To add the _JSON_ file type to the default list of file types included in the public CDN, execute:</span></span>

```sh
spo cdn policy set --type Public --policy IncludeFileExtensions --value "CSS,EOT,GIF,ICO,JPEG,JPG,JS,MAP,PNG,SVG,TTF,WOFF,JSON"
```

### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a><span data-ttu-id="98e13-375">變更網站分類您想要從 Office 365 CDN 排除清單</span><span class="sxs-lookup"><span data-stu-id="98e13-375">Change the list of site classifications you want to exclude from the Office 365 CDN</span></span>

<span data-ttu-id="98e13-376">使用[spo cdn 原則設定](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/)命令中排除不想要提供透過 CDN 的網站分類。</span><span class="sxs-lookup"><span data-stu-id="98e13-376">Use the [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) command to exclude site classifications that you do not want to make available over the CDN.</span></span> <span data-ttu-id="98e13-377">根據預設，會不排除任何網站分類。</span><span class="sxs-lookup"><span data-stu-id="98e13-377">By default, no site classifications are excluded.</span></span>

> [!NOTE]
> <span data-ttu-id="98e13-378">在變更排除的網站分類的清單，請您覆寫目前所定義的清單。</span><span class="sxs-lookup"><span data-stu-id="98e13-378">When changing the list of excluded site classifications, you overwrite the currently defined list.</span></span> <span data-ttu-id="98e13-379">如果您想要排除其他分類，先使用[spo cdn 原則] 清單中](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-list/)命令，以找出目前設定的分類。</span><span class="sxs-lookup"><span data-stu-id="98e13-379">If you want to exclude additional classifications, first use the [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-list/) command to find out which classifications are currently configured.</span></span>

<span data-ttu-id="98e13-380">若要排除歸類為_HBI_從公用 CDN 的網站，請執行</span><span class="sxs-lookup"><span data-stu-id="98e13-380">To exclude sites classified as _HBI_ from the public CDN, execute</span></span>

```sh
spo cdn policy set --type Public --policy ExcludeRestrictedSiteClassifications --value "HBI"
```

### <a name="disable-the-office-365-cdn"></a><span data-ttu-id="98e13-381">停用 Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="98e13-381">Disable the Office 365 CDN</span></span>

<span data-ttu-id="98e13-382">若要停用 Office 365 CDN 使用`spo cdn set`命令，例如：</span><span class="sxs-lookup"><span data-stu-id="98e13-382">To disable the Office 365 CDN use the `spo cdn set` command, for example:</span></span>

```sh
spo cdn set --type Public --enabled false
```

## <a name="using-your-cdn-assets"></a><span data-ttu-id="98e13-383">使用 CDN 資產</span><span class="sxs-lookup"><span data-stu-id="98e13-383">Using your CDN assets</span></span>

<span data-ttu-id="98e13-384">既然您已啟用 CDN 與設定的原點和原則，您可以開始使用 CDN 資產。</span><span class="sxs-lookup"><span data-stu-id="98e13-384">Now that you have enabled the CDN and configured origins and policies, you can begin using your CDN assets.</span></span>

<span data-ttu-id="98e13-385">本節將協助您了解如何使用 CDN Url 中您的 SharePoint 頁面和內容，以便 SharePoint 會在公用和私人原點的資產的要求重新導向至 CDN。</span><span class="sxs-lookup"><span data-stu-id="98e13-385">This section will help you understand how to use CDN URLs in your SharePoint pages and content so that SharePoint redirects requests for assets in both public and private origins to the CDN.</span></span>

- [<span data-ttu-id="98e13-386">更新連結至 CDN 資產</span><span class="sxs-lookup"><span data-stu-id="98e13-386">Updating links to CDN assets</span></span>](use-office-365-cdn-with-spo.md#updating-links-to-cdn-assets)
- [<span data-ttu-id="98e13-387">在公用的原點中使用資產</span><span class="sxs-lookup"><span data-stu-id="98e13-387">Using assets in public origins</span></span>](use-office-365-cdn-with-spo.md#using-assets-in-public-origins)
- [<span data-ttu-id="98e13-388">在私人原點中使用資產</span><span class="sxs-lookup"><span data-stu-id="98e13-388">Using assets in private origins</span></span>](use-office-365-cdn-with-spo.md#using-assets-in-private-origins)

<span data-ttu-id="98e13-389">如需如何使用 CDN 裝載用戶端網頁組件的資訊，請參閱主題[主機用戶端網頁組件從 Office 365 CDN （Hello World 第 4 部分）](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)。</span><span class="sxs-lookup"><span data-stu-id="98e13-389">For information on how to use the CDN for hosting client-side web parts, see the topic [Host your client-side web part from Office 365 CDN (Hello World part 4)](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn).</span></span>

### <a name="updating-links-to-cdn-assets"></a><span data-ttu-id="98e13-390">更新連結至 CDN 資產</span><span class="sxs-lookup"><span data-stu-id="98e13-390">Updating links to CDN assets</span></span>

<span data-ttu-id="98e13-391">若要使用您新增至原始來源的資產，您只需更新連結到原始的檔案取代為來源中的檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="98e13-391">To use assets that you have added to an origin, you simply update links to the original file with the path to the file in the origin.</span></span>

- <span data-ttu-id="98e13-392">編輯頁面或包含連結至您新增至原始來源的資產的內容。</span><span class="sxs-lookup"><span data-stu-id="98e13-392">Edit the page or content that contains links to assets you have added to an origin.</span></span> <span data-ttu-id="98e13-393">您也可以使用幾種方法之一，以全域搜尋，並取代連結跨 enter 網站或網站集合，如果您想要顯示的每個地方指定資產更新連結。</span><span class="sxs-lookup"><span data-stu-id="98e13-393">You can also use one of several methods to globally search and replace links across an enter site or site collection if you want to update the link to a given asset everywhere it appears.</span></span>
- <span data-ttu-id="98e13-394">每個連結中原點資產，取代 CDN 原始來源中的檔案的路徑中的路徑。</span><span class="sxs-lookup"><span data-stu-id="98e13-394">For each link to an asset in an origin, replace the path with the path to the file in the CDN origin.</span></span> <span data-ttu-id="98e13-395">您可以使用相對路徑。</span><span class="sxs-lookup"><span data-stu-id="98e13-395">You can use relative paths.</span></span>
- <span data-ttu-id="98e13-396">儲存在頁面或內容。</span><span class="sxs-lookup"><span data-stu-id="98e13-396">Save the page or content.</span></span>

<span data-ttu-id="98e13-397">例如，假設影像 _/site/SiteAssets/images/image.png_，其中已複製到文件庫資料夾_讀/網站/CDN_origins/公開 /_。</span><span class="sxs-lookup"><span data-stu-id="98e13-397">For example, consider the image _/site/SiteAssets/images/image.png_, which you have copied to the document library folder _/site/CDN_origins/public/_.</span></span> <span data-ttu-id="98e13-398">若要使用 CDN 資產，取代若要讓新的 URL _/site/CDN_origins/public/image.png_原始來源的路徑中的影像檔案位置的原始路徑。</span><span class="sxs-lookup"><span data-stu-id="98e13-398">To use the CDN asset, replace the original path to the image file location with the path to the origin to make the new URL _/site/CDN_origins/public/image.png_.</span></span>

<span data-ttu-id="98e13-399">如果您想要使用資產的完整 URL，而不是相對路徑，建構連結仿照下列所示：</span><span class="sxs-lookup"><span data-stu-id="98e13-399">If you want to use the full URL to the asset instead of a relative path, construct the link like so:</span></span>

`https://<TenantHostName>.sharepoint.com/sites/site/CDN_origins/public/image.png`

> [!NOTE]
> <span data-ttu-id="98e13-400">一般而言，您應該不硬 Url 直接在 CDN 資產。</span><span class="sxs-lookup"><span data-stu-id="98e13-400">In general, you should not hardcode URLs directly to assets in the CDN.</span></span> <span data-ttu-id="98e13-401">不過，您可以手動建構 Url 中公開的原點的資產視。</span><span class="sxs-lookup"><span data-stu-id="98e13-401">However, you can manually construct URLs for assets in public origins if needed.</span></span> <span data-ttu-id="98e13-402">如需詳細資訊，請參閱 <<c0>公用資產的硬式編碼 CDN Url。</span><span class="sxs-lookup"><span data-stu-id="98e13-402">For more information, see [Hardcoding CDN URLs for public assets](use-office-365-cdn-with-spo.md#hardcoding-cdn-urls-for-public-assets).</span></span>

<span data-ttu-id="98e13-403">若要深入了解如何確認，正在從 CDN 提供資產，請參閱[如何確認資產，由 CDN？](use-office-365-cdn-with-spo.md#CDNConfirm) [疑難排解 Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) ] 區段中。</span><span class="sxs-lookup"><span data-stu-id="98e13-403">To learn about how to verify that assets are being served from the CDN, see [How do I confirm that assets are being served by the CDN?](use-office-365-cdn-with-spo.md#CDNConfirm) in the [Troubleshooting the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) section.</span></span>

### <a name="using-assets-in-public-origins"></a><span data-ttu-id="98e13-404">在公用的原點中使用資產</span><span class="sxs-lookup"><span data-stu-id="98e13-404">Using assets in public origins</span></span>

<span data-ttu-id="98e13-405">**發佈功能**在 SharePoint Online 中自動修正儲存在公用的原點至 CDN 相等，以便從 CDN 服務，而不是 SharePoint 提供資產的資產的 Url。</span><span class="sxs-lookup"><span data-stu-id="98e13-405">The **Publishing feature** in SharePoint Online automatically rewrites URLs of assets stored in public origins to their CDN equivalents so that assets are served from the CDN service instead of SharePoint.</span></span>

<span data-ttu-id="98e13-406">如果您的原始來源與發佈網站中啟用功能，且您想要卸載到 CDN 的資產處於下列類別之一，SharePoint 會自動修正 Url 資產的原點而言，假設資產已不被排除的 CDN 原則。</span><span class="sxs-lookup"><span data-stu-id="98e13-406">If your origin is in a site with the Publishing feature enabled, and the assets you want to offload to the CDN are in one of the following categories, SharePoint will automatically rewrite URLs for assets in the origin, provided that the asset has not been excluded by a CDN policy.</span></span>

<span data-ttu-id="98e13-407">以下是一種連結會自動修正的 SharePoint 發佈功能的概觀：</span><span class="sxs-lookup"><span data-stu-id="98e13-407">The following is an overview of which links are automatically rewritten by the SharePoint Publishing feature:</span></span>

- <span data-ttu-id="98e13-408">在傳統的發佈頁面 HTML 回應中的 IMG/連結/CSS Url</span><span class="sxs-lookup"><span data-stu-id="98e13-408">IMG/LINK/CSS URLs in classic publishing page HTML responses</span></span>
  - <span data-ttu-id="98e13-409">這包括內] 頁面上的 HTML 內容作者所加入的影像</span><span class="sxs-lookup"><span data-stu-id="98e13-409">This includes images added by authors within the HTML content of a page</span></span>
- <span data-ttu-id="98e13-410">圖片庫投影片放映： 網頁組件圖像 Url</span><span class="sxs-lookup"><span data-stu-id="98e13-410">Picture Library SlideShow webpart image URLs</span></span>
- <span data-ttu-id="98e13-411">SPList REST API (RenderListDataAsStream) 結果中的圖像欄位</span><span class="sxs-lookup"><span data-stu-id="98e13-411">Image fields in SPList REST API (RenderListDataAsStream) results</span></span>
  - <span data-ttu-id="98e13-412">使用新屬性_ImageFieldsToTryRewriteToCdnUrls_來提供的欄位以逗號分隔清單</span><span class="sxs-lookup"><span data-stu-id="98e13-412">Use the new property _ImageFieldsToTryRewriteToCdnUrls_ to provide a comma separated list of fields</span></span>
  - <span data-ttu-id="98e13-413">支援的超連結欄位和 PublishingImage 欄位</span><span class="sxs-lookup"><span data-stu-id="98e13-413">Supports hyperlink fields and PublishingImage fields</span></span>
- <span data-ttu-id="98e13-414">SharePoint 影像轉譯</span><span class="sxs-lookup"><span data-stu-id="98e13-414">SharePoint image renditions</span></span>

<span data-ttu-id="98e13-415">下圖說明工作流程，當 SharePoint 收到包含從公用原點的資產頁面要求。</span><span class="sxs-lookup"><span data-stu-id="98e13-415">The following diagram illustrates the workflow when SharePoint receives a request for a page containing assets from a public origin.</span></span>

<span data-ttu-id="98e13-416">![工作流程圖表： 從公用的原始來源擷取 Office 365 CDN 資產](media/O365-CDN/o365-cdn-public-steps-transparent.svg "工作流程： 從公用的原始來源擷取 Office 365 CDN 資產")</span><span class="sxs-lookup"><span data-stu-id="98e13-416">![Workflow diagram: Retrieving Office 365 CDN assets from a public origin](media/O365-CDN/o365-cdn-public-steps-transparent.svg "Workflow: Retrieving Office 365 CDN assets from a public origin")</span></span>

> [!TIP]
> <span data-ttu-id="98e13-417">如果您想要停用自動修正的頁面上的特定 Url，您可以取出頁面，並新增查詢字串參數 **?NoAutoReWrites = true**至您想要停用每個連結的結尾。</span><span class="sxs-lookup"><span data-stu-id="98e13-417">If you want to disable auto-rewriting for specific URLs on a page, you can check out the page and add the query string parameter **?NoAutoReWrites=true** to the end of each link you want to disable.</span></span>

#### <a name="hardcoding-cdn-urls-for-public-assets"></a><span data-ttu-id="98e13-418">公用資產的硬式編碼 CDN Url</span><span class="sxs-lookup"><span data-stu-id="98e13-418">Hardcoding CDN URLs for public assets</span></span>

<span data-ttu-id="98e13-419">如果公用的原點而言，未啟用_發佈_功能，或資產不是其中一個 CDN 服務的自動修正功能所支援的連結類型，可以手動建構資產 CDN 位置的 Url，並在您的內容中使用這些 Url。</span><span class="sxs-lookup"><span data-stu-id="98e13-419">If the _Publishing_ feature is not enabled for a public origin, or the asset is not one of the link types supported by the auto-rewrite feature of the CDN service, you can manually construct URLs to the CDN location of the assets and use these URLs in your content.</span></span>

> [!NOTE]
> <span data-ttu-id="98e13-420">您不能硬 CDN Url 中私人原點的資產，因為表單 URL 的最後一個區段的必要的存取權杖產生要求資源的時間。</span><span class="sxs-lookup"><span data-stu-id="98e13-420">You cannot hardcode CDN URLs to assets in a private origin because the required access token that forms the last section of the URL is generated at the time the resource is requested.</span></span>

<span data-ttu-id="98e13-421">公用 CDN 資產，URL 格式看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="98e13-421">For public CDN assets, the URL format will look like the following:</span></span>

``` html
https://publiccdn.sharepointonline.com/<TenantHostName>/sites/site/library/asset.png
```

<span data-ttu-id="98e13-422">**TenantHostName**取代為您的租用戶名稱。</span><span class="sxs-lookup"><span data-stu-id="98e13-422">Replace **TenantHostName** with your tenant name.</span></span> <span data-ttu-id="98e13-423">範例：</span><span class="sxs-lookup"><span data-stu-id="98e13-423">Example:</span></span>

``` html
https://publiccdn.sharepointonline.com/contoso.sharepoint.com/sites/site/library/asset.png
```

### <a name="using-assets-in-private-origins"></a><span data-ttu-id="98e13-424">在私人原點中使用資產</span><span class="sxs-lookup"><span data-stu-id="98e13-424">Using assets in private origins</span></span>

<span data-ttu-id="98e13-425">無需額外設定，才能在私人原點中使用資產。</span><span class="sxs-lookup"><span data-stu-id="98e13-425">No additional configuration is required to use assets in private origins.</span></span> <span data-ttu-id="98e13-426">SharePoint Online 自動修正 Url 中私人原點的資產讓這些資產的要求永遠都會服務從 CDN。</span><span class="sxs-lookup"><span data-stu-id="98e13-426">SharePoint Online automatically rewrites URLs for assets in private origins so requests for those assets will always be served from the CDN.</span></span> <span data-ttu-id="98e13-427">因為這些 Url 包含必須要求資產時間是由 SharePoint Online 自動產生的語彙基元，無法以手動方式中私人原點的 CDN 資產建置 Url。</span><span class="sxs-lookup"><span data-stu-id="98e13-427">You cannot manually build URLs to CDN assets in private origins because these URLs contain tokens that must be auto-generated by SharePoint Online at the time the asset is requested.</span></span>

<span data-ttu-id="98e13-428">私用原點中的資產的存取受保護的動態產生的語彙基元根據使用者在起點的權限與下列各節所述出現警告。</span><span class="sxs-lookup"><span data-stu-id="98e13-428">Access to assets in private origins is protected by dynamically generated tokens based on user permissions to the origin, with the caveats described in the following sections.</span></span> <span data-ttu-id="98e13-429">使用者必須至少具有**讀取**存取權來呈現內容 CDN 的原點。</span><span class="sxs-lookup"><span data-stu-id="98e13-429">Users must have at least **read** access to the origins for the CDN to render content.</span></span>

<span data-ttu-id="98e13-430">下圖說明工作流程，當 SharePoint 收到包含從私人原點的資產頁面要求。</span><span class="sxs-lookup"><span data-stu-id="98e13-430">The following diagram illustrates the workflow when SharePoint receives a request for a page containing assets from a private origin.</span></span>

<span data-ttu-id="98e13-431">![工作流程圖表： 從私人的原始來源擷取 Office 365 CDN 資產](media/O365-CDN/o365-cdn-private-steps-transparent.svg "工作流程： 從私人的原始來源擷取 Office 365 CDN 資產")</span><span class="sxs-lookup"><span data-stu-id="98e13-431">![Workflow diagram: Retrieving Office 365 CDN assets from a private origin](media/O365-CDN/o365-cdn-private-steps-transparent.svg "Workflow: Retrieving Office 365 CDN assets from a private origin")</span></span>

#### <a name="token-based-authorization-in-private-origins"></a><span data-ttu-id="98e13-432">在私人原點語彙基元為基礎的授權</span><span class="sxs-lookup"><span data-stu-id="98e13-432">Token-based authorization in private origins</span></span>

<span data-ttu-id="98e13-433">SharePoint Online 所產生的語彙基元是授與存取權 CDN 將 Office 365 中的私人原點的資產。</span><span class="sxs-lookup"><span data-stu-id="98e13-433">Access to assets in private origins in the Office 365 CDN is granted by tokens generated by SharePoint Online.</span></span> <span data-ttu-id="98e13-434">已存取至資料夾或指定原始文件庫的權限的使用者會自動授與允許使用者存取檔案是根據其權限等級的權杖。</span><span class="sxs-lookup"><span data-stu-id="98e13-434">Users who already have permission to access to the folder or library designated by the origin are automatically granted tokens that permit the user to access the file based on their permission level.</span></span> <span data-ttu-id="98e13-435">這些存取權杖是有效 30 至 90 分鐘後它們會產生以協助防止權杖重新執行攻擊。</span><span class="sxs-lookup"><span data-stu-id="98e13-435">These access tokens are valid for 30 to 90 minutes after they are generated to help prevent token replay attacks.</span></span>

<span data-ttu-id="98e13-436">一旦產生的存取權杖，SharePoint Online 會傳回自訂 URI 包含兩個授權參數_吃_（edge 授權權杖） 和_oat_ （原點授權權杖） 用戶端。</span><span class="sxs-lookup"><span data-stu-id="98e13-436">Once the access token is generated, SharePoint Online returns a custom URI to the client containing two authorization parameters _eat_ (edge authorization token) and _oat_ (origin authorization token).</span></span> <span data-ttu-id="98e13-437">每個語彙基元的結構是 _< '到期時間期間時間格式 '>_<' 安全簽章中的' >_。</span><span class="sxs-lookup"><span data-stu-id="98e13-437">The structure of each token is _<'expiration time in Epoch time format'>__<'secure signature'>_.</span></span> <span data-ttu-id="98e13-438">例如：</span><span class="sxs-lookup"><span data-stu-id="98e13-438">For example:</span></span>

``` html
https://privatecdn.sharepointonline.com/contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg?eat=1486154359_cc59042c5c55c90b26a2775323c7c8112718431228fe84d568a3795a63912840&oat=1486154359_7d73c2e3ba4b7b1f97242332900616db0d4ffb04312
```

> [!NOTE]
> <span data-ttu-id="98e13-439">語彙基元的持有的任何人都可以存取資源的 CDN。</span><span class="sxs-lookup"><span data-stu-id="98e13-439">Anyone in possession of the token can access the resource in the CDN.</span></span> <span data-ttu-id="98e13-440">不過，包含這些存取 token 只共用透過 HTTPS 的 Url，因此除非權杖到期之前，使用者明確地共用 URL 資產不會是未經授權的使用者可以存取。</span><span class="sxs-lookup"><span data-stu-id="98e13-440">However, URLs containing these access tokens are only shared over HTTPS, so unless the URL is explicitly shared by an end user before the token expires, the asset won’t be accessible to unauthorized users.</span></span>

#### <a name="item-level-permissions-are-not-supported-for-assets-in-private-origins"></a><span data-ttu-id="98e13-441">在私人原點的資產不支援項目層級權限</span><span class="sxs-lookup"><span data-stu-id="98e13-441">Item-level permissions are not supported for assets in private origins</span></span>

<span data-ttu-id="98e13-442">請務必注意，SharePoint Online 不支援項目層級權限在私人原點的資產。</span><span class="sxs-lookup"><span data-stu-id="98e13-442">It is important to note that SharePoint Online does not support item-level permissions for assets in private origins.</span></span> <span data-ttu-id="98e13-443">例如，針對檔案位於`https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`，使用者具有有效的存取權給予符合下列條件的檔案：</span><span class="sxs-lookup"><span data-stu-id="98e13-443">For example, for a file located at `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`, users have effective access to the file given the following conditions:</span></span>

|<span data-ttu-id="98e13-444">使用者</span><span class="sxs-lookup"><span data-stu-id="98e13-444">User</span></span>  |<span data-ttu-id="98e13-445">權限</span><span class="sxs-lookup"><span data-stu-id="98e13-445">Permissions</span></span>  |<span data-ttu-id="98e13-446">有效的存取</span><span class="sxs-lookup"><span data-stu-id="98e13-446">Effective access</span></span>  |
|---------|---------|---------|
|<span data-ttu-id="98e13-447">使用者 1</span><span class="sxs-lookup"><span data-stu-id="98e13-447">User 1</span></span>     |<span data-ttu-id="98e13-448">有權存取 folder1</span><span class="sxs-lookup"><span data-stu-id="98e13-448">Has access to folder1</span></span>         |<span data-ttu-id="98e13-449">可以存取 image1.jpg 從 CDN</span><span class="sxs-lookup"><span data-stu-id="98e13-449">Can access image1.jpg from the CDN</span></span>         |
|<span data-ttu-id="98e13-450">使用者 2</span><span class="sxs-lookup"><span data-stu-id="98e13-450">User 2</span></span>     |<span data-ttu-id="98e13-451">沒有存取權 folder1</span><span class="sxs-lookup"><span data-stu-id="98e13-451">Does not have access to folder1</span></span>         |<span data-ttu-id="98e13-452">無法存取 image1.jpg 從 CDN</span><span class="sxs-lookup"><span data-stu-id="98e13-452">Cannot access image1.jpg from the CDN</span></span>         |
|<span data-ttu-id="98e13-453">使用者 3</span><span class="sxs-lookup"><span data-stu-id="98e13-453">User 3</span></span>     |<span data-ttu-id="98e13-454">沒有存取權 folder1，但是會授與存取 SharePoint Online 中的 image1.jpg 明確權限</span><span class="sxs-lookup"><span data-stu-id="98e13-454">Does not have access to folder1, but is granted explicit permission to access image1.jpg in SharePoint Online</span></span>         |<span data-ttu-id="98e13-455">可以存取資產 image1.jpg，直接從 SharePoint Online 中，但不是從 CDN</span><span class="sxs-lookup"><span data-stu-id="98e13-455">Can access the asset image1.jpg directly from SharePoint Online, but not from the CDN</span></span>         |
|<span data-ttu-id="98e13-456">使用者 4</span><span class="sxs-lookup"><span data-stu-id="98e13-456">User 4</span></span>     |<span data-ttu-id="98e13-457">有權存取 folder1，但已明確拒絕存取 SharePoint Online 中的 image1.jpg</span><span class="sxs-lookup"><span data-stu-id="98e13-457">Has access to folder1, but has been explicitly denied access to image1.jpg in SharePoint Online</span></span>         |<span data-ttu-id="98e13-458">無法從 SharePoint Online 中，存取資產，但可以存取資產從 CDN 而不管遭拒絕存取 SharePoint Online 中的檔案</span><span class="sxs-lookup"><span data-stu-id="98e13-458">Cannot access the asset from SharePoint Online, but can access the asset from the CDN despite being denied access to the file in SharePoint Online</span></span>         |

## <a name="troubleshooting-the-office-365-cdn"></a><span data-ttu-id="98e13-459">疑難排解 Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="98e13-459">Troubleshooting the Office 365 CDN</span></span>
<a name="CDNTroubleshooting"> </a>

### <a name="how-do-i-confirm-that-assets-are-being-served-by-the-cdn"></a><span data-ttu-id="98e13-460">如何確認資產，由 CDN？</span><span class="sxs-lookup"><span data-stu-id="98e13-460">How do I confirm that assets are being served by the CDN?</span></span>
<a name="CDNConfirm"> </a>

<span data-ttu-id="98e13-461">一旦您已新增連結] 頁面上的 CDN 資產，您可以確認的資產由從 CDN 瀏覽至 [] 頁面上、 滑鼠右鍵按一下 [影像後已轉譯及檢閱的影像 URL。</span><span class="sxs-lookup"><span data-stu-id="98e13-461">Once you have added links to CDN assets to a page, you can confirm that the asset is being served from the CDN by browsing to the page, right clicking on the image once it has rendered and reviewing the image URL.</span></span>

<span data-ttu-id="98e13-462">您也可以使用瀏覽器的開發人員工具，在頁面上，檢視每個資產的 URL，或使用 3rd 廠商網路追蹤工具。</span><span class="sxs-lookup"><span data-stu-id="98e13-462">You can also use your browser's developer tools to view the URL for each asset on a page, or use a 3rd party network trace tool.</span></span>

> [!NOTE]
> <span data-ttu-id="98e13-463">如果您使用 Fiddler 之類的網路來測試您資產外轉譯資產從 SharePoint] 頁面上，您必須手動新增查閱者標頭 」 查閱者： `https://yourdomain.sharepoint.com`」 至其中的 URL 是您的 SharePoint Online 租用戶的根 URL GET 要求。</span><span class="sxs-lookup"><span data-stu-id="98e13-463">If you use a network tool such as Fiddler to test your assets outside of rendering the asset from a SharePoint page, you must manually add the referrer header “Referrer: `https://yourdomain.sharepoint.com`” to the GET request where the URL is the root URL of your SharePoint Online tenant.</span></span>

<span data-ttu-id="98e13-464">您無法直接在網頁瀏覽器中測試 CDN Url，因為您必須具有來自 SharePoint Online 查閱者。</span><span class="sxs-lookup"><span data-stu-id="98e13-464">You cannot test CDN URLs directly in a web browser because you must have a referrer coming from SharePoint Online.</span></span> <span data-ttu-id="98e13-465">不過，如果您將 CDN 資產 URL 新增至 SharePoint] 頁面上，然後在瀏覽器中開啟] 頁面上，您會看到在頁面上呈現 CDN 資產。</span><span class="sxs-lookup"><span data-stu-id="98e13-465">However, if you add the CDN asset URL to a SharePoint page and then open the page in a browser, you will see the CDN asset rendered on the page.</span></span>

<span data-ttu-id="98e13-466">如需有關如何在 Microsoft Edge 瀏覽器中使用的開發人員工具的詳細資訊，請參閱 < <b0>Microsoft Edge 開發人員工具</b0>。</span><span class="sxs-lookup"><span data-stu-id="98e13-466">For more information on using the developer tools in the Microsoft Edge browser, see [Microsoft Edge Developer Tools](https://docs.microsoft.com/en-us/microsoft-edge/devtools-guide).</span></span>

### <a name="why-are-assets-from-a-new-origin-unavailable"></a><span data-ttu-id="98e13-467">為何無法使用的新的原點從資產？</span><span class="sxs-lookup"><span data-stu-id="98e13-467">Why are assets from a new origin unavailable?</span></span>
<span data-ttu-id="98e13-468">資產中新的原點會立即無法可供使用，因為所花的時間才能傳播到 CDN 註冊並從原點上載至 CDN 儲存資產。</span><span class="sxs-lookup"><span data-stu-id="98e13-468">Assets in new origins will not immediately be available for use, as it takes time for the registration to propagate through the CDN and for the assets to be uploaded from the origin to CDN storage.</span></span> <span data-ttu-id="98e13-469">可在 CDN 資產所需的時間取決於多少資產和檔案大小。</span><span class="sxs-lookup"><span data-stu-id="98e13-469">The time required for assets to be available in the CDN depends on how many assets and the files sizes.</span></span>

### <a name="my-client-side-web-part-or-sharepoint-framework-solution-isnt-working"></a><span data-ttu-id="98e13-470">我的用戶端網頁組件或 SharePoint 架構解決方案無法正常運作</span><span class="sxs-lookup"><span data-stu-id="98e13-470">My client-side web part or SharePoint Framework solution isn't working</span></span>

<span data-ttu-id="98e13-471">當您啟用公用原點 CDN 將 Office 365 時，CDN 服務會自動建立這些預設原點：</span><span class="sxs-lookup"><span data-stu-id="98e13-471">When you enable the Office 365 CDN for public origins, the CDN service automatically creates these default origins:</span></span>

- <span data-ttu-id="98e13-472">\* / 主版頁面</span><span class="sxs-lookup"><span data-stu-id="98e13-472">\*/MASTERPAGE</span></span>
- <span data-ttu-id="98e13-473">\* / 樣式庫</span><span class="sxs-lookup"><span data-stu-id="98e13-473">\*/STYLE LIBRARY</span></span>
- <span data-ttu-id="98e13-474">\* / CLIENTSIDEASSETS</span><span class="sxs-lookup"><span data-stu-id="98e13-474">\*/CLIENTSIDEASSETS</span></span>

<span data-ttu-id="98e13-475">如果 \* / clientsideassets 原點遺漏、 SharePoint 架構解決方案會失敗，而且會產生任何警告或錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="98e13-475">If the \*/clientsideassets origin is missing, SharePoint Framework solutions will fail, and no warning or error messages are generated.</span></span> <span data-ttu-id="98e13-476">此原點可能遺失，因為 CDN 已啟用與 _-NoDefaultOrigins_參數設為 **$true**，或是手動刪除原點。</span><span class="sxs-lookup"><span data-stu-id="98e13-476">This origin may be missing either because the CDN was enabled with the _-NoDefaultOrigins_ parameter set to **$true**, or because the origin was manually deleted.</span></span>

<span data-ttu-id="98e13-477">您可以檢查看看是否 \* / CLIENTSIDEASSETS 原點有搭配下列 PowerShell 命令：</span><span class="sxs-lookup"><span data-stu-id="98e13-477">You can check to see if the \*/CLIENTSIDEASSETS origin is present with the following PowerShell command:</span></span>

``` powershell
Get-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

<span data-ttu-id="98e13-478">或者，您可以檢查與 Office 365 CLI:</span><span class="sxs-lookup"><span data-stu-id="98e13-478">Or you can check with the Office 365 CLI:</span></span>

``` powershell
spo cdn origin list
```

<span data-ttu-id="98e13-479">若要新增原始 PowerShell 中：</span><span class="sxs-lookup"><span data-stu-id="98e13-479">To add the origin in PowerShell:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

<span data-ttu-id="98e13-480">若要在 Office 365 CLI 新增來源：</span><span class="sxs-lookup"><span data-stu-id="98e13-480">To add the origin in the Office 365 CLI:</span></span>

``` powershell
spo cdn origin add --origin */CLIENTSIDEASSETS
```

### <a name="what-powershell-modules-and-cli-shells-do-i-need-to-work-with-the-office-365-cdn"></a><span data-ttu-id="98e13-481">查看 PowerShell 模組與 CLI 殼層我需要為搭配 Office 365 CDN？</span><span class="sxs-lookup"><span data-stu-id="98e13-481">What PowerShell modules and CLI shells do I need to work with the Office 365 CDN?</span></span>

<span data-ttu-id="98e13-482">您可以選擇為搭配 Office 365 CDN 使用**SharePoint Online 管理命令介面**的 PowerShell 模組] 或 [ **Office 365 CLI**。</span><span class="sxs-lookup"><span data-stu-id="98e13-482">You can choose to work with the Office 365 CDN using either the **SharePoint Online Management Shell** PowerShell module or the **Office 365 CLI**.</span></span>

- [<span data-ttu-id="98e13-483">開始使用 SharePoint Online 管理命令介面</span><span class="sxs-lookup"><span data-stu-id="98e13-483">Getting started with SharePoint Online Management Shell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)
- [<span data-ttu-id="98e13-484">安裝 Office 365 CLI</span><span class="sxs-lookup"><span data-stu-id="98e13-484">Installing the Office 365 CLI</span></span>](https://pnp.github.io/office365-cli/user-guide/installing-cli/)

## <a name="see-also"></a><span data-ttu-id="98e13-485">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98e13-485">See also</span></span>

[<span data-ttu-id="98e13-486">內容傳遞網路</span><span class="sxs-lookup"><span data-stu-id="98e13-486">Content Delivery Networks</span></span>](https://aka.ms/o365cdns)

[<span data-ttu-id="98e13-487">Office 365 的網路規劃和效能調整</span><span class="sxs-lookup"><span data-stu-id="98e13-487">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)

