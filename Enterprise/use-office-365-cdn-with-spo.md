---
title: 使用 Office 365 內容傳遞網路 (CDN) 搭配 SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/3/2019
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
ms.openlocfilehash: ceb66b3e17baf25a292b4903c569b931f9448f71
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33492203"
---
# <a name="use-the-office-365-content-delivery-network-cdn-with-sharepoint-online"></a><span data-ttu-id="c520b-103">使用 Office 365 內容傳遞網路 (CDN) 搭配 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="c520b-103">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>

<span data-ttu-id="c520b-104">您可以使用內建的 Office 365 內容傳遞網路 (CDN) 來主控靜態資產，為您的 SharePoint網頁提供更佳的效能。</span><span class="sxs-lookup"><span data-stu-id="c520b-104">You can use the built-in Office 365 Content Delivery Network (CDN) to host static assets to provide better performance for your SharePoint Online pages.</span></span> <span data-ttu-id="c520b-105">Office 365 CDN 透過將靜態資產快取到更靠近提出要求之瀏覽器的位置 (這有助於加速下載以及減少延遲)，藉此改善效能。</span><span class="sxs-lookup"><span data-stu-id="c520b-105">The Office 365 CDN improves performance by caching static assets closer to the browsers requesting them, which helps to speed up downloads and reduce latency.</span></span> <span data-ttu-id="c520b-106">此外，Office 365 CDN 改善的壓縮和 HTTP 管線使用[HTTP/2 通訊協定](https://en.wikipedia.org/wiki/HTTP/2)。</span><span class="sxs-lookup"><span data-stu-id="c520b-106">Also, the Office 365 CDN uses the [HTTP/2 protocol](https://en.wikipedia.org/wiki/HTTP/2) for improved compression and HTTP pipelining.</span></span> <span data-ttu-id="c520b-107">Office 365 CDN 服務包含在 SharePoint Online 訂閱的一部分。</span><span class="sxs-lookup"><span data-stu-id="c520b-107">The Office 365 CDN service is included as part of your SharePoint Online subscription.</span></span>

<span data-ttu-id="c520b-108">Office 365 CDN 是由可讓您在多個位置或_來源_主控靜態資產的多個 CDN 組成，並透過全球高速網路提供資產。</span><span class="sxs-lookup"><span data-stu-id="c520b-108">The Office 365 CDN is composed of multiple CDNs that allow you to host static assets in multiple locations, or _origins_, and serve them from global high-speed networks.</span></span> <span data-ttu-id="c520b-109">根據您要在 Office 365 CDN 中主控的內容類型而定，您可以新增**公用**來源、**私人**來源或兩者。</span><span class="sxs-lookup"><span data-stu-id="c520b-109">Depending on the kind of content you want to host in the Office 365 CDN, you can add **public** origins, **private** origins or both.</span></span> <span data-ttu-id="c520b-110">如需公用和私人原點之間的差異的詳細資訊，請參閱[選擇每個原始來源是否應該是公用或私人](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)。</span><span class="sxs-lookup"><span data-stu-id="c520b-110">See [Choose whether each origin should be public or private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate) for more information on the difference between public and private origins.</span></span>

<span data-ttu-id="c520b-111">![Office 365 CDN 概念圖](media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN 概念圖")</span><span class="sxs-lookup"><span data-stu-id="c520b-111">![Office 365 CDN conceptual diagram](media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN conceptual diagram")</span></span>

<span data-ttu-id="c520b-112">如果您已熟悉 Cdn 的方式，您只需要完成啟用 CDN 將 Office 365 租用戶的幾個步驟。</span><span class="sxs-lookup"><span data-stu-id="c520b-112">If you are already familiar with the way that CDNs work, you only need to complete a few steps to enable the Office 365 CDN for your tenant.</span></span> <span data-ttu-id="c520b-113">本主題說明如何。</span><span class="sxs-lookup"><span data-stu-id="c520b-113">This topic describes how.</span></span> <span data-ttu-id="c520b-114">閱讀如何開始主控您的靜態資產的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c520b-114">Read on for information about how to get started hosting your static assets.</span></span>

> [!TIP]
> <span data-ttu-id="c520b-115">有其他 Microsoft 主控的 Cdn 可用於 Office 365 的特殊的使用情況，但會在因為他們屬於超出 Office 365 CDN 的範圍不在本主題討論。</span><span class="sxs-lookup"><span data-stu-id="c520b-115">There are other Microsoft-hosted CDNs that can be used with Office 365 for specialized usage scenarios, but are not discussed in this topic because they fall outside the scope of the Office 365 CDN.</span></span> <span data-ttu-id="c520b-116">如需詳細資訊，請參閱 <<c0>其他 Microsoft Cdn。</span><span class="sxs-lookup"><span data-stu-id="c520b-116">For more information, see [Other Microsoft CDNs](content-delivery-networks.md#other-microsoft-cdns).</span></span>

 <span data-ttu-id="c520b-117">**Head 回[網路規劃和效能調整的 Office 365](https://aka.ms/tune)。**</span><span class="sxs-lookup"><span data-stu-id="c520b-117">**Head back to [Network planning and performance tuning for Office 365](https://aka.ms/tune).**</span></span>

## <a name="overview-of-working-with-the-office-365-cdn-in-sharepoint-online"></a><span data-ttu-id="c520b-118">使用 SharePoint Online 中 CDN 將 Office 365 的概觀</span><span class="sxs-lookup"><span data-stu-id="c520b-118">Overview of working with the Office 365 CDN in SharePoint Online</span></span>

<span data-ttu-id="c520b-119">若要設定為您的組織 CDN 將 Office 365，您可以遵循下列基本步驟：</span><span class="sxs-lookup"><span data-stu-id="c520b-119">To set up the Office 365 CDN for your organization, you follow these basic steps:</span></span>

- [<span data-ttu-id="c520b-120">規劃部署 Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="c520b-120">Plan for deployment of the Office 365 CDN</span></span>](use-office-365-cdn-with-spo.md#plan-for-deployment-of-the-office-365-cdn)

  - <span data-ttu-id="c520b-121">[決定您想要在 CDN 上裝載的靜態資產](use-office-365-cdn-with-spo.md#CDNAssets)。</span><span class="sxs-lookup"><span data-stu-id="c520b-121">[Determine which static assets you want to host on the CDN](use-office-365-cdn-with-spo.md#CDNAssets).</span></span>
  - <span data-ttu-id="c520b-122">[決定您想要用來儲存您的資產](use-office-365-cdn-with-spo.md#CDNStoreAssets)。</span><span class="sxs-lookup"><span data-stu-id="c520b-122">[Determine where you want to store your assets](use-office-365-cdn-with-spo.md#CDNStoreAssets).</span></span> <span data-ttu-id="c520b-123">此位置可以是 SharePoint 網站、 文件庫或資料夾，並呼叫_原點_。</span><span class="sxs-lookup"><span data-stu-id="c520b-123">This location can be a SharePoint site, library or folder and is called an _origin_.</span></span>
  - <span data-ttu-id="c520b-124">[選擇 [每個原始來源是否應該是公用或私人](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)。</span><span class="sxs-lookup"><span data-stu-id="c520b-124">[Choose whether each origin should be public or private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate).</span></span> <span data-ttu-id="c520b-125">您可以新增多個公用和私人類型的原點。</span><span class="sxs-lookup"><span data-stu-id="c520b-125">You can add multiple origins of both public and private types.</span></span>

- <span data-ttu-id="c520b-126">安裝及設定 CDN，使用 PowerShell 或 SharePoint Online CLI</span><span class="sxs-lookup"><span data-stu-id="c520b-126">Set up and configure the CDN, using either PowerShell or the SharePoint Online CLI</span></span>

  - [<span data-ttu-id="c520b-127">安裝及使用 SharePoint Online 管理命令介面設定 CDN</span><span class="sxs-lookup"><span data-stu-id="c520b-127">Set up and configure the CDN by using the SharePoint Online Management Shell</span></span>](use-office-365-cdn-with-spo.md#CDNSetupinPShell)
  - [<span data-ttu-id="c520b-128">安裝及使用 Office 365 CLI 設定 CDN</span><span class="sxs-lookup"><span data-stu-id="c520b-128">Set up and configure the CDN by using the Office 365 CLI</span></span>](use-office-365-cdn-with-spo.md#CDNSetupinCLI)

  <span data-ttu-id="c520b-129">當您完成此步驟時，您必須：</span><span class="sxs-lookup"><span data-stu-id="c520b-129">When you complete this step, you will have:</span></span>

  - <span data-ttu-id="c520b-130">啟用組織 CDN。</span><span class="sxs-lookup"><span data-stu-id="c520b-130">Enabled the CDN for your organization.</span></span>
  - <span data-ttu-id="c520b-131">新增您的原點，用來識別為公用或私人每個原始來源。</span><span class="sxs-lookup"><span data-stu-id="c520b-131">Added your origins, identifying each origin as public or private.</span></span>

<span data-ttu-id="c520b-132">一旦您完成安裝程式，您可以[管理 Office 365 CDN](use-office-365-cdn-with-spo.md#CDNManage)經過一段時間的：</span><span class="sxs-lookup"><span data-stu-id="c520b-132">Once you're done with setup, you can [Manage the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNManage) over time by:</span></span>
  
- <span data-ttu-id="c520b-133">新增、 更新及移除資產</span><span class="sxs-lookup"><span data-stu-id="c520b-133">Adding, updating, and removing assets</span></span>
- <span data-ttu-id="c520b-134">新增及移除原點</span><span class="sxs-lookup"><span data-stu-id="c520b-134">Adding and removing origins</span></span>
- <span data-ttu-id="c520b-135">設定 CDN 原則</span><span class="sxs-lookup"><span data-stu-id="c520b-135">Configuring CDN policies</span></span>
- <span data-ttu-id="c520b-136">如有必要，停用 CDN</span><span class="sxs-lookup"><span data-stu-id="c520b-136">If necessary, disabling the CDN</span></span>

<span data-ttu-id="c520b-137">最後，請參閱 < 若要了解公用及私人原點從存取 CDN 資產<b0>使用 CDN 資產</b0>。</span><span class="sxs-lookup"><span data-stu-id="c520b-137">Finally, see [Using your CDN assets](use-office-365-cdn-with-spo.md#using-your-cdn-assets) to learn about accessing your CDN assets from both public and private origins.</span></span>

<span data-ttu-id="c520b-138">如需解決一般問題的指導，請參閱[疑難排解 Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) 。</span><span class="sxs-lookup"><span data-stu-id="c520b-138">See [Troubleshooting the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) for guidance on resolving common issues.</span></span>

## <a name="plan-for-deployment-of-the-office-365-cdn"></a><span data-ttu-id="c520b-139">規劃部署 Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="c520b-139">Plan for deployment of the Office 365 CDN</span></span>

<span data-ttu-id="c520b-140">您的 Office 365 租用戶部署 Office 365 CDN 之前，您應該考量下列因素規劃程序的一部分。</span><span class="sxs-lookup"><span data-stu-id="c520b-140">Before you deploy the Office 365 CDN for your Office 365 tenant, you should consider the following factors as part of your planning process.</span></span>

  - [<span data-ttu-id="c520b-141">決定您想要在 CDN 上裝載的靜態資產</span><span class="sxs-lookup"><span data-stu-id="c520b-141">Determine which static assets you want to host on the CDN</span></span>](use-office-365-cdn-with-spo.md#CDNAssets)
  - [<span data-ttu-id="c520b-142">決定您想要用來儲存您的資產</span><span class="sxs-lookup"><span data-stu-id="c520b-142">Determine where you want to store your assets</span></span>](use-office-365-cdn-with-spo.md#CDNStoreAssets)
  - <span data-ttu-id="c520b-143">[選擇 [每個原始來源是否應該是公用或私用](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)</span><span class="sxs-lookup"><span data-stu-id="c520b-143">[Choose whether each origin should be public or private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)</span></span>

### <a name="determine-which-static-assets-you-want-to-host-on-the-cdn"></a><span data-ttu-id="c520b-144">決定您想要在 CDN 上裝載的靜態資產</span><span class="sxs-lookup"><span data-stu-id="c520b-144">Determine which static assets you want to host on the CDN</span></span>
<span data-ttu-id="c520b-145"><a name="CDNAssets"> </a></span><span class="sxs-lookup"><span data-stu-id="c520b-145"></span></span>

<span data-ttu-id="c520b-146">在 [一般] Cdn 是以架設_靜態資產_或未經常變更的資產最為有用。</span><span class="sxs-lookup"><span data-stu-id="c520b-146">In general, CDNs are most effective for hosting _static assets_, or assets that don't change very often.</span></span> <span data-ttu-id="c520b-147">好用的經驗法則是找出符合部分或所有的這些條件的檔案：</span><span class="sxs-lookup"><span data-stu-id="c520b-147">A good rule of thumb is to identify files that meet some or all of these conditions:</span></span>

- <span data-ttu-id="c520b-148">靜態檔案內嵌在頁面 （例如指令碼和圖像），可能會造成重大的累加影響的頁面載入時間</span><span class="sxs-lookup"><span data-stu-id="c520b-148">Static files embedded in a page (like scripts and images) that may have a significant incremental impact on page load times</span></span>
- <span data-ttu-id="c520b-149">大型檔案一樣的可執行檔和安裝檔案</span><span class="sxs-lookup"><span data-stu-id="c520b-149">Large files like executables and installation files</span></span>
- <span data-ttu-id="c520b-150">資料流的媒體檔案</span><span class="sxs-lookup"><span data-stu-id="c520b-150">Streaming media files</span></span>
- <span data-ttu-id="c520b-151">支援用戶端程式碼的資源庫</span><span class="sxs-lookup"><span data-stu-id="c520b-151">Resource libraries that support client-side code</span></span>

<span data-ttu-id="c520b-152">例如，便會重複替換要求網站圖像和指令碼等的小型檔案可以大幅改善網站呈現效能，而逐漸減少在 SharePoint Online 網站上的負載，當您將它們新增至 CDN 原點。</span><span class="sxs-lookup"><span data-stu-id="c520b-152">For example, small files that are repeatedly requested like site images and scripts can significantly improve site rendering performance and incrementally reduce the load on your SharePoint Online sites when you add them to a CDN origin.</span></span> <span data-ttu-id="c520b-153">可以下載較大的檔案，例如安裝可執行檔或視訊檔案，或從 CDN，即使未經常存取它們傳遞誤判的效能影響和後續降低您的 SharePoint Online 網站上的負載以串流方式傳送。</span><span class="sxs-lookup"><span data-stu-id="c520b-153">Larger files such as installation executables or video files can be downloaded or streamed from the CDN, delivering a positive performance impact and subsequent reduction of the load on your SharePoint Online site, even if they are not accessed as often.</span></span>

<span data-ttu-id="c520b-154">每個檔案為基礎的效能改進是取決於許多因素，包括至最接近的 CDN 端點，用戶端的近似值暫時性條件的區域網路，依此類推。</span><span class="sxs-lookup"><span data-stu-id="c520b-154">Performance improvement on a per-file basis is dependent on many factors, including the client's proximity to the nearest CDN endpoint, transient conditions on the local network, and so forth.</span></span> <span data-ttu-id="c520b-155">許多靜態檔案很小，且可從 Office 365 下載少於一秒。</span><span class="sxs-lookup"><span data-stu-id="c520b-155">Many static files are quite small, and can be downloaded from Office 365 in less than a second.</span></span> <span data-ttu-id="c520b-156">不過，網頁可能包含許多嵌入的檔案，並幾秒鐘的累計下載時間。</span><span class="sxs-lookup"><span data-stu-id="c520b-156">However, a web page may contain many embedded files with a cumulative download time of several seconds.</span></span> <span data-ttu-id="c520b-157">從 CDN 提供這些檔案，可大幅降低整體的頁面載入時間。</span><span class="sxs-lookup"><span data-stu-id="c520b-157">Serving these files from the CDN can significantly reduce the overall page load time.</span></span> <span data-ttu-id="c520b-158">請參閱[，可提升何種效能沒有 CDN 提供？](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide)範例。</span><span class="sxs-lookup"><span data-stu-id="c520b-158">See [What performance gains does a CDN provide?](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide) for an example.</span></span>

### <a name="determine-where-you-want-to-store-your-assets"></a><span data-ttu-id="c520b-159">決定您想要用來儲存您的資產</span><span class="sxs-lookup"><span data-stu-id="c520b-159">Determine where you want to store your assets</span></span>
<span data-ttu-id="c520b-160"><a name="CDNStoreAssets"> </a></span><span class="sxs-lookup"><span data-stu-id="c520b-160"></span></span>

<span data-ttu-id="c520b-161">CDN 擷取您資產從呼叫_原點_的位置。</span><span class="sxs-lookup"><span data-stu-id="c520b-161">The CDN fetches your assets from a location called an _origin_.</span></span> <span data-ttu-id="c520b-162">原始來源可以是 SharePoint 網站、 文件庫或資料夾可供存取的 URL。</span><span class="sxs-lookup"><span data-stu-id="c520b-162">An origin can be a SharePoint site, document library or folder that is accessible by a URL.</span></span> <span data-ttu-id="c520b-163">當您指定原點為您的組織，您會有很大的彈性。</span><span class="sxs-lookup"><span data-stu-id="c520b-163">You have great flexibility when you specify origins for your organization.</span></span> <span data-ttu-id="c520b-164">例如，您可以指定多個原點或想要將所有的 CDN 資產單一原點。</span><span class="sxs-lookup"><span data-stu-id="c520b-164">For example, you can specify multiple origins or a single origin where you want to put all your CDN assets.</span></span> <span data-ttu-id="c520b-165">您可以選擇讓組織的公用或私人原點。</span><span class="sxs-lookup"><span data-stu-id="c520b-165">You can choose to have both public or private origins for your organization.</span></span> <span data-ttu-id="c520b-166">大多數組織會選擇實作兩者的組合。</span><span class="sxs-lookup"><span data-stu-id="c520b-166">Most organizations will choose to implement a combination of the two.</span></span>

<span data-ttu-id="c520b-167">您可以為您原點資料夾或文件庫，例如建立新的容器，並新增您想要提供從 CDN 的檔案。</span><span class="sxs-lookup"><span data-stu-id="c520b-167">You can create new container for your origins such as folders or document libraries, and add files you want to make available from the CDN.</span></span> <span data-ttu-id="c520b-168">如果您有一組特定的資產您想要從 CDN，可用，而且想要限制只有在容器檔案 CDN 資產的集合，這是一個好的方法。</span><span class="sxs-lookup"><span data-stu-id="c520b-168">This is a good approach if you have a specific set of assets you want to be available from the CDN, and want to restrict the set of CDN assets to only those files in the container.</span></span>

<span data-ttu-id="c520b-169">您也可以設定現有網站集合、 網站、 文件庫或資料夾為原點，會讓所有合格的資產容器中可從 CDN。</span><span class="sxs-lookup"><span data-stu-id="c520b-169">You can also configure an existing site collection, site, library or folder as an origin, which will make all eligible assets in the container available from the CDN.</span></span> <span data-ttu-id="c520b-170">您將現有的容器新增為原始來源之前，請務必確定您是知道其內容和權限，所以您不小心公開資產的匿名存取或未經授權的使用者。</span><span class="sxs-lookup"><span data-stu-id="c520b-170">Before you add an existing container as an origin, it's important to make sure you are aware of its contents and permissions so you do not inadvertently expose assets to anonymous access or unauthorized users.</span></span>

<span data-ttu-id="c520b-171">您可以定義_CDN 原則_，以從 CDN 排除您原點中的內容。</span><span class="sxs-lookup"><span data-stu-id="c520b-171">You can define _CDN policies_ to exclude content in your origins from the CDN.</span></span> <span data-ttu-id="c520b-172">CDN 原則排除_檔案類型_及_網站分類_，例如屬性中公用或私人原點資產，且會套用至所有原點的原則中指定 CdnType （私人或公用）。</span><span class="sxs-lookup"><span data-stu-id="c520b-172">CDN policies exclude assets in public or private origins by attributes such as _file type_ and _site classification_, and are applied to all origins of the CdnType (private or public) you specify in the policy.</span></span> <span data-ttu-id="c520b-173">例如，如果您新增包含多個子網站的網站所組成的私用原始來源，您可以定義要排除標示為 [ **2 私人 3 機密**因此內容從站台分類套用從 CDN 將不會服務的站台的原則。</span><span class="sxs-lookup"><span data-stu-id="c520b-173">For example, if you add a private origin consisting of a site that contains multiple subsites, you can define a policy to exclude sites marked as **Confidential** so content from sites with that classification applied will not be served from the CDN.</span></span> <span data-ttu-id="c520b-174">此原則會套用到內容，從_所有_在您新增至 CDN 的私用原點。</span><span class="sxs-lookup"><span data-stu-id="c520b-174">The policy will apply to content from _all_ private origins you have added to the CDN.</span></span>
  
<span data-ttu-id="c520b-175">請記住，原點數目愈大，時間影響也愈大花費 CDN 服務來處理要求。</span><span class="sxs-lookup"><span data-stu-id="c520b-175">Keep in mind that the greater the number of origins, the greater the impact on the time it takes the CDN service to process requests.</span></span> <span data-ttu-id="c520b-176">我們建議您盡可能原點的數目限制。</span><span class="sxs-lookup"><span data-stu-id="c520b-176">We recommend that you limit the number of origins as much as possible.</span></span>
  
### <a name="choose-whether-each-origin-should-be-public-or-private"></a><span data-ttu-id="c520b-177">選擇 [每個原始來源是否應該是公用或私用</span><span class="sxs-lookup"><span data-stu-id="c520b-177">Choose whether each origin should be public or private</span></span>
<span data-ttu-id="c520b-178"><a name="CDNOriginChoosePublicPrivate"> </a></span><span class="sxs-lookup"><span data-stu-id="c520b-178"></span></span>

<span data-ttu-id="c520b-179">當您識別來源時，指定是否應該讓它成為_公用_或_私人_。</span><span class="sxs-lookup"><span data-stu-id="c520b-179">When you identify an origin, you specify whether it should be made _public_ or _private_.</span></span> <span data-ttu-id="c520b-180">存取在公用的原點的 CDN 資產為匿名，並在私人原點的 CDN 內容受到動態產生的語彙基元的較高的安全性。</span><span class="sxs-lookup"><span data-stu-id="c520b-180">Access to CDN assets in public origins is anonymous, and CDN content in private origins is secured by dynamically generated tokens for greater security.</span></span> <span data-ttu-id="c520b-181">不論您選擇哪個選項，Microsoft 會所有工作都為您談到 CDN 本身的管理。</span><span class="sxs-lookup"><span data-stu-id="c520b-181">Regardless of which option you choose, Microsoft does all the heavy lifting for you when it comes to administration of the CDN itself.</span></span> <span data-ttu-id="c520b-182">此外，您可以稍後改變心意之後您已設定 CDN 並找出您原點。</span><span class="sxs-lookup"><span data-stu-id="c520b-182">Also, you can change your mind later, after you've set up the CDN and identified your origins.</span></span>

<span data-ttu-id="c520b-183">公用及私人選項提供類似的效能提升，但每個具有唯一的屬性及優點。</span><span class="sxs-lookup"><span data-stu-id="c520b-183">Both public and private options provide similar performance gains, but each has unique attributes and advantages.</span></span>

<span data-ttu-id="c520b-184">匿名，都可以存取**公用**原點 CDN 將 Office 365 內，且主控的資產可以存取資產之 url 的任何人。</span><span class="sxs-lookup"><span data-stu-id="c520b-184">**Public** origins within the Office 365 CDN are accessible anonymously, and hosted assets can be accessed by anyone who has the URL to the asset.</span></span> <span data-ttu-id="c520b-185">因為對公用來源中內容的存取是匿名的，您應該只使用公用來源來快取非敏感性的一般內容，例如 javascript 檔案、指令碼、圖示和影像。</span><span class="sxs-lookup"><span data-stu-id="c520b-185">Because access to content in public origins is anonymous, you should only use them to cache non-sensitive generic content such as javascript files, scripts, icons and images.</span></span>

<span data-ttu-id="c520b-186">Office 365 CDN 內的**私人**來源可提供使用者內容 (例如 SharePoint Online 文件庫、網站和視訊等媒體) 的私人存取。</span><span class="sxs-lookup"><span data-stu-id="c520b-186">**Private** origins within the Office 365 CDN provide private access to user content such as SharePoint Online document libraries, sites and media such as videos.</span></span> <span data-ttu-id="c520b-187">私用原點中內容的存取權受到以動態方式產生的 token，讓其可以只存取與原始文件的文件庫或儲存位置的權限的使用者。</span><span class="sxs-lookup"><span data-stu-id="c520b-187">Access to content in private origins is secured by dynamically generated tokens so it can only be accessed by users with permissions to the original document library or storage location.</span></span> <span data-ttu-id="c520b-188">CDN 將 Office 365 中的私人原點僅可用於 SharePoint Online 內容，您只可以存取透過重新導向私人原點的資產，從您的 SharePoint Online 租用戶。</span><span class="sxs-lookup"><span data-stu-id="c520b-188">Private origins in the Office 365 CDN can only be used for SharePoint Online content, and you can only access assets in private origins through redirection from your SharePoint Online tenant.</span></span>

<span data-ttu-id="c520b-189">您可以閱讀需 CDN 如何存取私用的原始來源中的資產中[使用資產私人原點中的](use-office-365-cdn-with-spo.md#using-assets-in-private-origins)運作。</span><span class="sxs-lookup"><span data-stu-id="c520b-189">You can read more about how CDN access to assets in a private origin works in [Using assets in private origins](use-office-365-cdn-with-spo.md#using-assets-in-private-origins).</span></span>

#### <a name="attributes-and-advantages-of-hosting-assets-in-public-origins"></a><span data-ttu-id="c520b-190">屬性和裝載在公用的原點的資產的優點</span><span class="sxs-lookup"><span data-stu-id="c520b-190">Attributes and advantages of hosting assets in public origins</span></span>
  
- <span data-ttu-id="c520b-191">在公用的原點中公開的資產皆可存取所有人匿名。</span><span class="sxs-lookup"><span data-stu-id="c520b-191">Assets exposed in a public origin are accessible by everyone anonymously.</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="c520b-192">您應該永遠不會將含有使用者資訊或會被視為機密至您的組織中公用的原始來源資源。</span><span class="sxs-lookup"><span data-stu-id="c520b-192">You should never place resources that contain user information or are considered sensitive to your organization in a public origin.</span></span>
- <span data-ttu-id="c520b-193">如果您移除公用原點的資產，資產可能可繼續運作最多 30 天從快取;不過，我們會在 15 分鐘內失效 CDN 中資產的連結。</span><span class="sxs-lookup"><span data-stu-id="c520b-193">If you remove an asset from a public origin, the asset may continue to be available for up to 30 days from the cache; however, we will invalidate links to the asset in the CDN within 15 minutes.</span></span>
- <span data-ttu-id="c520b-194">當您裝載在公用的原始來源中的樣式表 （CSS 檔案） 時，您可以使用程式碼內的相對路徑與 Uri。</span><span class="sxs-lookup"><span data-stu-id="c520b-194">When you host style sheets (CSS files) in a public origin, you can use relative paths and URIs within the code.</span></span> <span data-ttu-id="c520b-195">這表示您可以參照背景影像及其他物件呼叫它的資產的位置相對的位置。</span><span class="sxs-lookup"><span data-stu-id="c520b-195">This means that you can reference the location of background images and other objects relative to the location of the asset that's calling it.</span></span>
- <span data-ttu-id="c520b-196">雖然您可以硬式編碼公用原始來源的 URL，這種做法所以不建議。</span><span class="sxs-lookup"><span data-stu-id="c520b-196">While you can hard code a public origin's URL, doing so is not recommended.</span></span> <span data-ttu-id="c520b-197">這是如果存取 CDN 變成無法使用，URL 不會自動解決您在 SharePoint Online 中的組織，可能會導致中斷的連結和其他錯誤。</span><span class="sxs-lookup"><span data-stu-id="c520b-197">The reason for this is that if access to the CDN becomes unavailable, the URL will not automatically resolve to your organization in SharePoint Online and might result in broken links and other errors.</span></span>
- <span data-ttu-id="c520b-198">預設檔案類型，可供公用原點的.css、.eot、.gif、.ico、.jpeg、.jpg、.js、.map、.png、.svg、.ttf 和.woff。</span><span class="sxs-lookup"><span data-stu-id="c520b-198">The default file types that are included for public origins are .css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, and .woff.</span></span> <span data-ttu-id="c520b-199">您可以指定其他檔案類型。</span><span class="sxs-lookup"><span data-stu-id="c520b-199">You can specify additional file types.</span></span>
- <span data-ttu-id="c520b-200">您可以設定要排除的已識別由您所指定網站分類資產的原則。</span><span class="sxs-lookup"><span data-stu-id="c520b-200">You can configure a policy to exclude assets that have been identified by site classifications that you specify.</span></span> <span data-ttu-id="c520b-201">例如，您可以選擇要排除所有的資產，即使他們所允許的檔案類型，並位於公用原點標示為 「 機密 」 或 「 限制 」。</span><span class="sxs-lookup"><span data-stu-id="c520b-201">For example, you can choose to exclude all assets that are marked as "confidential" or "restricted" even if they are an allowed file type and are located in a public origin.</span></span>

#### <a name="attributes-and-advantages-of-hosting-assets-in-private-origins"></a><span data-ttu-id="c520b-202">屬性和裝載在私人原點的資產的優點</span><span class="sxs-lookup"><span data-stu-id="c520b-202">Attributes and advantages of hosting assets in private origins</span></span>

- <span data-ttu-id="c520b-203">私用原點只能用於 SharePoint Online 的資產。</span><span class="sxs-lookup"><span data-stu-id="c520b-203">Private origins can only be used for SharePoint Online assets.</span></span>
- <span data-ttu-id="c520b-204">如果他們有權限來存取容器使用者僅可從私人原點存取資產。</span><span class="sxs-lookup"><span data-stu-id="c520b-204">Users can only access the assets from a private origin if they have permissions to access the container.</span></span> <span data-ttu-id="c520b-205">無法對這些資產的匿名存取。</span><span class="sxs-lookup"><span data-stu-id="c520b-205">Anonymous access to these assets is prevented.</span></span>
- <span data-ttu-id="c520b-206">在私人原點的資產必須參照從 SharePoint Online 租用戶。</span><span class="sxs-lookup"><span data-stu-id="c520b-206">Assets in private origins must be referred from the SharePoint Online tenant.</span></span> <span data-ttu-id="c520b-207">直接存取私人 CDN 資產無法運作。</span><span class="sxs-lookup"><span data-stu-id="c520b-207">Direct access to private CDN assets does not work.</span></span>
- <span data-ttu-id="c520b-208">如果您從私人原點移除資產，資產可能會繼續以供最多一個小時的時間從快取;不過，我們將會失效中 CDN 資產的連結的資產的移除 15 分鐘內。</span><span class="sxs-lookup"><span data-stu-id="c520b-208">If you remove an asset from the private origin, the asset may continue to be available for up to an hour from the cache; however, we will invalidate links to the asset in the CDN within 15 minutes of the asset's removal.</span></span>
- <span data-ttu-id="c520b-209">.Gif、.ico、.jpeg、.jpg、.js、 和.png，就會是針對私人原點所包含的預設檔案類型。</span><span class="sxs-lookup"><span data-stu-id="c520b-209">The default file types that are included for private origins are .gif, .ico, .jpeg, .jpg, .js, and .png.</span></span> <span data-ttu-id="c520b-210">您可以指定其他檔案類型。</span><span class="sxs-lookup"><span data-stu-id="c520b-210">You can specify additional file types.</span></span>
- <span data-ttu-id="c520b-211">就像公用原點，您可以設定要排除已透過網站分類，即使您使用萬用字元來包含所有的資產資料夾或文件庫內指定識別的資產的原則。</span><span class="sxs-lookup"><span data-stu-id="c520b-211">Just like with public origins, you can configure a policy to exclude assets that have been identified by site classifications that you specify even if you use wildcards to include all assets within a folder or document library.</span></span>

<span data-ttu-id="c520b-212">如需為使用 Office 365 CDN、 一般 CDN 概念，以及您可以使用與 Office 365 租用戶其他 Microsoft Cdn 原因的詳細資訊，請參閱 <<c0>內容傳遞網路。</span><span class="sxs-lookup"><span data-stu-id="c520b-212">For more information about why to use the Office 365 CDN, general CDN concepts, and other Microsoft CDNs you can use with your Office 365 tenant, see [Content Delivery Networks](content-delivery-networks.md).</span></span>

### <a name="default-cdn-origins"></a><span data-ttu-id="c520b-213">預設 CDN 原點</span><span class="sxs-lookup"><span data-stu-id="c520b-213">Default CDN origins</span></span>

<span data-ttu-id="c520b-214">除非另有指定，Office 365 會設定某些預設原點您當您啟用 Office 365 CDN。</span><span class="sxs-lookup"><span data-stu-id="c520b-214">Unless you specify otherwise, Office 365 sets up some default origins for you when you enable the Office 365 CDN.</span></span> <span data-ttu-id="c520b-215">如果您最初選擇不適用於佈建它們，您可以在您完成設定後新增這些原點。</span><span class="sxs-lookup"><span data-stu-id="c520b-215">If you initially opt not to provision them, you can add these origins after you complete setup.</span></span> <span data-ttu-id="c520b-216">除非您了解的略過的預設原點安裝方法的結果，並有這樣的特定原因，您應允許他們要建立當您啟用 CDN。</span><span class="sxs-lookup"><span data-stu-id="c520b-216">Unless you understand the consequences of skipping the setup of default origins and have a specific reason for doing so, you should allow them to be created when you enable the CDN.</span></span>
  
<span data-ttu-id="c520b-217">私人 CDN 原點預設值：</span><span class="sxs-lookup"><span data-stu-id="c520b-217">Default private CDN origins:</span></span>
  
- <span data-ttu-id="c520b-218">\*/userphoto.aspx</span><span class="sxs-lookup"><span data-stu-id="c520b-218">\*/userphoto.aspx</span></span>
- <span data-ttu-id="c520b-219">\*/siteassets</span><span class="sxs-lookup"><span data-stu-id="c520b-219">\*/siteassets</span></span>

<span data-ttu-id="c520b-220">公用 CDN 原點預設值：</span><span class="sxs-lookup"><span data-stu-id="c520b-220">Default public CDN origins:</span></span>
  
- <span data-ttu-id="c520b-221">\*/masterpage</span><span class="sxs-lookup"><span data-stu-id="c520b-221">\*/masterpage</span></span>
- <span data-ttu-id="c520b-222">\*/style 文件庫</span><span class="sxs-lookup"><span data-stu-id="c520b-222">\*/style library</span></span>
- <span data-ttu-id="c520b-223">\*/clientsideassets</span><span class="sxs-lookup"><span data-stu-id="c520b-223">\*/clientsideassets</span></span>

> [!NOTE]
> <span data-ttu-id="c520b-224">_clientsideassets_是已在 2017 年 12 月加到 Office 365 CDN 服務預設公用原點。</span><span class="sxs-lookup"><span data-stu-id="c520b-224">_clientsideassets_ is a default public origin that was added to the Office 365 CDN service in December 2017.</span></span> <span data-ttu-id="c520b-225">此來源必須要有 SharePoint 架構中以解決方案 CDN 工作的順序。</span><span class="sxs-lookup"><span data-stu-id="c520b-225">This origin must be present in order for SharePoint Framework solutions in the CDN to work.</span></span> <span data-ttu-id="c520b-226">如果您啟用 Office 365 CDN 年 12 月 2017 年之前，或當您啟用 CDN 略過的預設原點的安裝程式，您可以手動新增此原點。</span><span class="sxs-lookup"><span data-stu-id="c520b-226">If you enabled the Office 365 CDN prior to December 2017, or if you skipped setup of default origins when you enabled the CDN, you can manually add this origin.</span></span> <span data-ttu-id="c520b-227">如需詳細資訊，請參閱[我的用戶端網頁組件或 SharePoint 架構解決方案無法正常運作](use-office-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working)。</span><span class="sxs-lookup"><span data-stu-id="c520b-227">For more information, see [My client-side web part or SharePoint Framework solution isn't working](use-office-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working).</span></span>

## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a><span data-ttu-id="c520b-228">設定及使用 SharePoint Online 管理命令介面來設定 Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="c520b-228">Set up and configure the Office 365 CDN by using the SharePoint Online Management Shell</span></span>
<span data-ttu-id="c520b-229"><a name="CDNSetupinPShell"> </a></span><span class="sxs-lookup"><span data-stu-id="c520b-229"></span></span>

<span data-ttu-id="c520b-230">本節中的程序需要您使用 SharePoint Online 管理命令介面來連線至 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="c520b-230">The procedures in this section require you to use the SharePoint Online Management Shell to connect to SharePoint Online.</span></span> <span data-ttu-id="c520b-231">如需相關指示，請參閱[連線到 SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)。</span><span class="sxs-lookup"><span data-stu-id="c520b-231">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>
  
<span data-ttu-id="c520b-232">完成下列步驟來安裝及設定以裝載您在 SharePoint Online 使用 SharePoint Online 管理命令介面中的資產 CDN。</span><span class="sxs-lookup"><span data-stu-id="c520b-232">Complete these steps to set up and configure the CDN to host your assets in SharePoint Online using the SharePoint Online Management Shell.</span></span>
  
### <a name="enable-your-organization-to-use-the-office-365-cdn"></a><span data-ttu-id="c520b-233">啟用您的組織使用 Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="c520b-233">Enable your organization to use the Office 365 CDN</span></span>

<span data-ttu-id="c520b-234">您的租用戶 CDN 設定進行變更之前，您應該在您的 Office 365 租用戶中擷取私人 CDN 組態的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="c520b-234">Before you make changes to the tenant CDN settings, you should retrieve the current status of the private CDN configuration in your Office 365 tenant.</span></span> <span data-ttu-id="c520b-235">連線至您的租用戶使用 SharePoint Online 管理命令介面：</span><span class="sxs-lookup"><span data-stu-id="c520b-235">Connect to your tenant using the SharePoint Online Management Shell:</span></span>

``` powershell
Connect-SPOService -Url https://contoso-admin.sharepoint.com
```

<span data-ttu-id="c520b-236">現在可用於**取得 SPOTenantCdnEnabled**指令程式從租用戶擷取 CDN 狀態設定：</span><span class="sxs-lookup"><span data-stu-id="c520b-236">Now use the **Get-SPOTenantCdnEnabled** cmdlet to retrieve the CDN status settings from the tenant:</span></span>

``` powershell
Get-SPOTenantCdnEnabled -CdnType <Public | Private>
```

<span data-ttu-id="c520b-237">針對指定 CdnType CDN 的狀態將會輸出至畫面。</span><span class="sxs-lookup"><span data-stu-id="c520b-237">The status of the CDN for the specified CdnType will output to the screen.</span></span>

<span data-ttu-id="c520b-238">使用**設定 SPOTenantCdnEnabled**指令程式來啟用您的組織使用 Office 365 CDN。</span><span class="sxs-lookup"><span data-stu-id="c520b-238">Use the **Set-SPOTenantCdnEnabled** cmdlet to enable your organization to use the Office 365 CDN.</span></span> <span data-ttu-id="c520b-239">您可以啟用您的組織，一次使用公用原點、 私人原點，或兩者。</span><span class="sxs-lookup"><span data-stu-id="c520b-239">You can enable your organization to use public origins, private origins, or both at once.</span></span> <span data-ttu-id="c520b-240">您也可以設定略過的預設原點安裝程式，當您啟用 CDN。</span><span class="sxs-lookup"><span data-stu-id="c520b-240">You can also configure the CDN to skip the setup of default origins when you enable it.</span></span> <span data-ttu-id="c520b-241">您隨時可以稍後在本主題中所述加入這些原點。</span><span class="sxs-lookup"><span data-stu-id="c520b-241">You can always add these origins later as described in this topic.</span></span>
  
<span data-ttu-id="c520b-242">在 SharePoint Online 的 Windows Powershell:</span><span class="sxs-lookup"><span data-stu-id="c520b-242">In Windows Powershell for SharePoint Online:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

<span data-ttu-id="c520b-243">例如，若要啟用您的組織使用公開及私密原點，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="c520b-243">For example, to enable your organization to use both public and private origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

<span data-ttu-id="c520b-244">若要啟用您的組織使用公開及私密原點，但略過預設原點的設定，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="c520b-244">To enable your organization to use both public and private origins but skip setting up the default origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

<span data-ttu-id="c520b-245">當您啟用 Office 365 CDN，並略過的預設原點安裝的潛在影響預設佈建原點的相關資訊，請參閱[預設 CDN 原點](use-office-365-cdn-with-spo.md#default-cdn-origins)。</span><span class="sxs-lookup"><span data-stu-id="c520b-245">See [Default CDN origins](use-office-365-cdn-with-spo.md#default-cdn-origins) for information about the origins that are provisioned by default when you enable the Office 365 CDN, and the potential impact of skipping the setup of default origins.</span></span>

<span data-ttu-id="c520b-246">若要啟用您的組織使用公用原點，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="c520b-246">To enable your organization to use public origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

<span data-ttu-id="c520b-247">若要啟用您的組織使用私人的原點，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="c520b-247">To enable your organization to use private origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

<span data-ttu-id="c520b-248">如需此 cmdlet 的詳細資訊，請參閱 <<c0>設定 SPOTenantCdnEnabled。</span><span class="sxs-lookup"><span data-stu-id="c520b-248">For more information about this cmdlet, see [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span></span>
  
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a><span data-ttu-id="c520b-249">變更要在 Office 365 CDN （選用） 中包含檔案類型的清單</span><span class="sxs-lookup"><span data-stu-id="c520b-249">Change the list of file types to include in the Office 365 CDN (Optional)</span></span>
<span data-ttu-id="c520b-250"><a name="Office365CDNforSPOFileType"> </a></span><span class="sxs-lookup"><span data-stu-id="c520b-250"></span></span>

> [!TIP]
> <span data-ttu-id="c520b-251">當您使用**組 SPOTenantCdnPolicy** cmdlet 定義的檔案類型時，您覆寫目前所定義的清單。</span><span class="sxs-lookup"><span data-stu-id="c520b-251">When you define file types by using the **Set-SPOTenantCdnPolicy** cmdlet, you overwrite the currently defined list.</span></span> <span data-ttu-id="c520b-252">如果您想要新增其他檔案類型至清單時，指令程式先使用來找出哪些檔案類型已允許納入以及您新的清單。</span><span class="sxs-lookup"><span data-stu-id="c520b-252">If you want to add additional file types to the list, use the cmdlet first to find out what file types are already allowed and include them in the list along with your new ones.</span></span>
  
<span data-ttu-id="c520b-253">使用**設定 SPOTenantCdnPolicy**指令程式來定義可由公用和私人原點 CDN 中主控的靜態檔案類型。</span><span class="sxs-lookup"><span data-stu-id="c520b-253">Use the **Set-SPOTenantCdnPolicy** cmdlet to define static file types that can be hosted by public and private origins in the CDN.</span></span> <span data-ttu-id="c520b-254">根據預設，常見的資產類型為何，允許範例.css、.gif、.jpg、 及.js。</span><span class="sxs-lookup"><span data-stu-id="c520b-254">By default, common asset types are allowed, for example .css, .gif, .jpg, and .js.</span></span>

<span data-ttu-id="c520b-255">在 SharePoint Online 的 Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="c520b-255">In Windows PowerShell for SharePoint Online:</span></span>

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

<span data-ttu-id="c520b-256">例如，若要啟用 CDN 主機.css 和.png 檔案，您輸入此命令：</span><span class="sxs-lookup"><span data-stu-id="c520b-256">For example, to enable the CDN to host .css and .png files, you would enter the command:</span></span>

``` powershell
Set-SPOTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

<span data-ttu-id="c520b-257">若要查看 CDN 目前允許哪些檔案類型，請使用**Get SPOTenantCdnPolicies** cmdlet:</span><span class="sxs-lookup"><span data-stu-id="c520b-257">To see what file types are currently allowed by the CDN, use the **Get-SPOTenantCdnPolicies** cmdlet:</span></span>

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="c520b-258">如需這些 cmdlet 的詳細資訊，請參閱[設定 SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx)和[取得 SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx)。</span><span class="sxs-lookup"><span data-stu-id="c520b-258">For more information about these cmdlets, see [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) and [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span></span>
  
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a><span data-ttu-id="c520b-259">變更您想要排除在 Office 365 CDN （選用） 的網站分類的清單</span><span class="sxs-lookup"><span data-stu-id="c520b-259">Change the list of site classifications you want to exclude from the Office 365 CDN (Optional)</span></span>
<span data-ttu-id="c520b-260"><a name="Office365CDNforSPOSiteClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="c520b-260"></span></span>

> [!TIP]
> <span data-ttu-id="c520b-261">您可以使用**組 SPOTenantCdnPolicy**指令程式，以排除網站分類，當您覆寫目前所定義的清單。</span><span class="sxs-lookup"><span data-stu-id="c520b-261">When you exclude site classifications by using the **Set-SPOTenantCdnPolicy** cmdlet, you overwrite the currently defined list.</span></span> <span data-ttu-id="c520b-262">如果您想要排除其他網站分類，使用以找出已被排除哪些分類並再將其新增以及您新的第一次的指令程式進行。</span><span class="sxs-lookup"><span data-stu-id="c520b-262">If you want to exclude additional site classifications, use the cmdlet first to find out what classifications are already excluded and then add them along with your new ones.</span></span>

<span data-ttu-id="c520b-263">使用**組 SPOTenantCdnPolicy**指令程式來排除不想要提供透過 CDN 的網站分類。</span><span class="sxs-lookup"><span data-stu-id="c520b-263">Use the **Set-SPOTenantCdnPolicy** cmdlet to exclude site classifications that you do not want to make available over the CDN.</span></span> <span data-ttu-id="c520b-264">根據預設，會不排除任何網站分類。</span><span class="sxs-lookup"><span data-stu-id="c520b-264">By default, no site classifications are excluded.</span></span>

<span data-ttu-id="c520b-265">在 SharePoint Online 的 Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="c520b-265">In Windows PowerShell for SharePoint Online:</span></span>

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

<span data-ttu-id="c520b-266">若要查看哪些網站分類目前受到限制，請使用**Get SPOTenantCdnPolicies** cmdlet:</span><span class="sxs-lookup"><span data-stu-id="c520b-266">To see what site classifications are currently restricted, use the **Get-SPOTenantCdnPolicies** cmdlet:</span></span>

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="c520b-267">會傳回的屬性，而_IncludeFileExtensions_、 _ExcludeRestrictedSiteClassifications_ _ExcludeIfNoScriptDisabled_。</span><span class="sxs-lookup"><span data-stu-id="c520b-267">The properties that will be returned are _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ and _ExcludeIfNoScriptDisabled_.</span></span>

<span data-ttu-id="c520b-268">_IncludeFileExtensions_屬性包含將服務從 CDN 的副檔名清單。</span><span class="sxs-lookup"><span data-stu-id="c520b-268">The _IncludeFileExtensions_ property contains the list of file extensions that will be served from the CDN.</span></span>

> [!NOTE]
> <span data-ttu-id="c520b-269">預設的副檔名的方式不同公用和私人之間。</span><span class="sxs-lookup"><span data-stu-id="c520b-269">The default file extensions are different between public and private.</span></span>

<span data-ttu-id="c520b-270">_ExcludeRestrictedSiteClassifications_屬性會包含您想要排除從 CDN 網站分類。</span><span class="sxs-lookup"><span data-stu-id="c520b-270">The _ExcludeRestrictedSiteClassifications_ property contains the site classifications that you want to exclude from the CDN.</span></span> <span data-ttu-id="c520b-271">例如，您可以排除標示為 [ **2 私人 3 機密**因此內容從站台分類套用從 CDN 將不會服務的網站。</span><span class="sxs-lookup"><span data-stu-id="c520b-271">For example, you can exclude sites marked as **Confidential** so content from sites with that classification applied will not be served from the CDN.</span></span>

<span data-ttu-id="c520b-272">_ExcludeIfNoScriptDisabled_屬性會從網站層級_NoScript_屬性設定為基礎的 CDN 排除內容。</span><span class="sxs-lookup"><span data-stu-id="c520b-272">The _ExcludeIfNoScriptDisabled_ property excludes content from the CDN based on the site-level _NoScript_ attribute settings.</span></span> <span data-ttu-id="c520b-273">根據預設， _NoScript_屬性設為 [**已啟用**_新式_網站和**已停用**的_傳統_網站。</span><span class="sxs-lookup"><span data-stu-id="c520b-273">By default, the _NoScript_ attribute is set to **Enabled** for _Modern_ sites and **Disabled** for _Classic_ sites.</span></span> <span data-ttu-id="c520b-274">這取決於您的租用戶設定。</span><span class="sxs-lookup"><span data-stu-id="c520b-274">This depends on your tenant settings.</span></span>

<span data-ttu-id="c520b-275">如需這些 cmdlet 的詳細資訊，請參閱[設定 SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx)和[取得 SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx)。</span><span class="sxs-lookup"><span data-stu-id="c520b-275">For more information about these cmdlets, see [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) and [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span></span>
  
### <a name="add-an-origin-for-your-assets"></a><span data-ttu-id="c520b-276">新增您資產的原始來源</span><span class="sxs-lookup"><span data-stu-id="c520b-276">Add an origin for your assets</span></span>
<span data-ttu-id="c520b-277"><a name="Office365CDNforSPOOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="c520b-277"></span></span>

<span data-ttu-id="c520b-278">使用**Add SPOTenantCdnOrigin**指令程式來定義原點。</span><span class="sxs-lookup"><span data-stu-id="c520b-278">Use the **Add-SPOTenantCdnOrigin** cmdlet to define an origin.</span></span> <span data-ttu-id="c520b-279">您可以定義多個原點。</span><span class="sxs-lookup"><span data-stu-id="c520b-279">You can define multiple origins.</span></span> <span data-ttu-id="c520b-280">原點是指向 SharePoint 文件庫或資料夾，其中包含您想要裝載的 CDN 資產的 URL。</span><span class="sxs-lookup"><span data-stu-id="c520b-280">The origin is a URL that points to a SharePoint library or folder that contains the assets that you want to be hosted by the CDN.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="c520b-281">您應該永遠不會將含有使用者資訊或會被視為機密至您的組織中公用的原始來源資源。</span><span class="sxs-lookup"><span data-stu-id="c520b-281">You should never place resources that contain user information or are considered sensitive to your organization in a public origin.</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

<span data-ttu-id="c520b-282">_路徑_的值是文件庫或資料夾，其中包含資產的相對路徑。</span><span class="sxs-lookup"><span data-stu-id="c520b-282">The value of _path_ is the relative path to the library or folder that contains the assets.</span></span> <span data-ttu-id="c520b-283">您可以使用萬用字元，除了相對路徑。</span><span class="sxs-lookup"><span data-stu-id="c520b-283">You can use wildcards in addition to relative paths.</span></span> <span data-ttu-id="c520b-284">原點支援加至 URL 的萬用字元。</span><span class="sxs-lookup"><span data-stu-id="c520b-284">Origins support wildcards prepended to the URL.</span></span> <span data-ttu-id="c520b-285">這可讓您建立橫跨多個站台的原點。</span><span class="sxs-lookup"><span data-stu-id="c520b-285">This allows you to create origins that span multiple sites.</span></span> <span data-ttu-id="c520b-286">例如，若要包含在所有網站的 masterpages 資料夾中的所有資產內 CDN 公開原點，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="c520b-286">For example, to include all of the assets in the masterpages folder for all of your sites as a public origin within the CDN, type the following command:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

- <span data-ttu-id="c520b-287">萬用字元修飾詞 \***/** 只用於起點處的路徑，並會比對 [指定 URL] 下的所有 URL 區段。</span><span class="sxs-lookup"><span data-stu-id="c520b-287">The wildcard modifier \***/** can only be used at the beginning of the path, and will match all URL segments under the specified URL.</span></span>
- <span data-ttu-id="c520b-288">路徑可以指向文件庫、 資料夾或網站。</span><span class="sxs-lookup"><span data-stu-id="c520b-288">The path can point to a document library, folder or site.</span></span> <span data-ttu-id="c520b-289">例如，路徑 _\* / site1_會比對網站下的所有文件庫。</span><span class="sxs-lookup"><span data-stu-id="c520b-289">For example, the path _\*/site1_ will match all the document libraries under the site.</span></span>

<span data-ttu-id="c520b-290">您可以新增與特定的相對路徑的原點而言。</span><span class="sxs-lookup"><span data-stu-id="c520b-290">You can add an origin with a specific relative path.</span></span> <span data-ttu-id="c520b-291">您無法新增使用的完整路徑原點。</span><span class="sxs-lookup"><span data-stu-id="c520b-291">You cannot add an origin using the full path.</span></span>

<span data-ttu-id="c520b-292">本範例會新增 siteassets 文件庫私人原點特定站台：</span><span class="sxs-lookup"><span data-stu-id="c520b-292">This example adds a private origin of the siteassets library on a specific site:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

<span data-ttu-id="c520b-293">本範例會在網站集合的網站資產文件庫中新增私人原點_folder1_資料夾：</span><span class="sxs-lookup"><span data-stu-id="c520b-293">This example adds a private origin of the _folder1_ folder in the site collection's site assets library:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl “/sites/test/siteassets/folder1”
```

<span data-ttu-id="c520b-294">如需這個命令和語法的詳細資訊，請參閱 < <b0>Add SPOTenantCdnOrigin</b0>。</span><span class="sxs-lookup"><span data-stu-id="c520b-294">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>

> [!NOTE]
> <span data-ttu-id="c520b-295">在私人原點共用從原點的資產必須發佈之前他們可從 CDN 的主要版本。</span><span class="sxs-lookup"><span data-stu-id="c520b-295">In private origins, assets being shared from an origin must have a major version published before they can be accessed from the CDN.</span></span>
  
<span data-ttu-id="c520b-296">一旦您已經執行此命令，系統會設定同步處理跨資料中心。</span><span class="sxs-lookup"><span data-stu-id="c520b-296">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="c520b-297">這可能需要長達 15 分鐘。</span><span class="sxs-lookup"><span data-stu-id="c520b-297">This can take up to 15 minutes.</span></span>
  
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a><span data-ttu-id="c520b-298">範例： 設定您的主版頁面和樣式庫公用原點的 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="c520b-298">Example: Configure a public origin for your master pages and for your style library for SharePoint Online</span></span>
<span data-ttu-id="c520b-299"><a name="ExamplePublicOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="c520b-299"></span></span>

<span data-ttu-id="c520b-300">一般而言，這些原點是為您設定預設當您啟用 Office 365 CDN。</span><span class="sxs-lookup"><span data-stu-id="c520b-300">Normally, these origins are set up for you by default when you enable the Office 365 CDN.</span></span> <span data-ttu-id="c520b-301">不過，如果您想要手動啟用，請遵循下列步驟。</span><span class="sxs-lookup"><span data-stu-id="c520b-301">However, if you want to enable them manually, follow these steps.</span></span>
  
- <span data-ttu-id="c520b-302">使用**Add SPOTenantCdnOrigin** cmdlet 來定義樣式庫為公用的原點而言。</span><span class="sxs-lookup"><span data-stu-id="c520b-302">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the style library as a public origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

- <span data-ttu-id="c520b-303">使用**Add SPOTenantCdnOrigin** cmdlet 來定義為公用的原始來源的主版頁面。</span><span class="sxs-lookup"><span data-stu-id="c520b-303">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the master pages as a public origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

<span data-ttu-id="c520b-304">如需這個命令和語法的詳細資訊，請參閱 < <b0>Add SPOTenantCdnOrigin</b0>。</span><span class="sxs-lookup"><span data-stu-id="c520b-304">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>

<span data-ttu-id="c520b-305">一旦您已經執行此命令，系統會設定同步處理跨資料中心。</span><span class="sxs-lookup"><span data-stu-id="c520b-305">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="c520b-306">這可能需要長達 15 分鐘。</span><span class="sxs-lookup"><span data-stu-id="c520b-306">This can take up to 15 minutes.</span></span>

### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a><span data-ttu-id="c520b-307">範例： 設定您的網站資產、 網站頁面和發佈的映像私人原點的 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="c520b-307">Example: Configure a private origin for your site assets, site pages, and publishing images for SharePoint Online</span></span>
<span data-ttu-id="c520b-308"><a name="ExamplePrivateOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="c520b-308"></span></span>

- <span data-ttu-id="c520b-309">使用**Add SPOTenantCdnOrigin** cmdlet 來定義為私人的原始來源的 [網站資產] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c520b-309">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the site assets folder as a private origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

- <span data-ttu-id="c520b-310">使用**Add SPOTenantCdnOrigin** cmdlet 來定義網站的 [頁面] 資料夾為私人的原點而言。</span><span class="sxs-lookup"><span data-stu-id="c520b-310">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the site pages folder as a private origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

- <span data-ttu-id="c520b-311">使用**Add SPOTenantCdnOrigin** cmdlet 來定義為私人的原始來源的發佈的 [圖像] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c520b-311">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the publishing images folder as a private origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

<span data-ttu-id="c520b-312">如需這個命令和語法的詳細資訊，請參閱 < <b0>Add SPOTenantCdnOrigin</b0>。</span><span class="sxs-lookup"><span data-stu-id="c520b-312">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>

<span data-ttu-id="c520b-313">一旦您已經執行此命令，系統會設定同步處理跨資料中心。</span><span class="sxs-lookup"><span data-stu-id="c520b-313">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="c520b-314">這可能需要長達 15 分鐘。</span><span class="sxs-lookup"><span data-stu-id="c520b-314">This can take up to 15 minutes.</span></span>

### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a><span data-ttu-id="c520b-315">範例： 設定 SharePoint online 網站集合的私用原始來源</span><span class="sxs-lookup"><span data-stu-id="c520b-315">Example: Configure a private origin for a site collection for SharePoint Online</span></span>
<span data-ttu-id="c520b-316"><a name="ExamplePrivateOriginSiteCollection"> </a></span><span class="sxs-lookup"><span data-stu-id="c520b-316"></span></span>

<span data-ttu-id="c520b-317">若要定義為私人的原始來源的網站集合使用**Add SPOTenantCdnOrigin** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c520b-317">Use the **Add-SPOTenantCdnOrigin** cmdlet to define a site collection as a private origin.</span></span> <span data-ttu-id="c520b-318">例如：</span><span class="sxs-lookup"><span data-stu-id="c520b-318">For example:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

<span data-ttu-id="c520b-319">如需這個命令和語法的詳細資訊，請參閱 < <b0>Add SPOTenantCdnOrigin</b0>。</span><span class="sxs-lookup"><span data-stu-id="c520b-319">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>
  
<span data-ttu-id="c520b-320">一旦您已經執行此命令，系統會設定同步處理跨資料中心。</span><span class="sxs-lookup"><span data-stu-id="c520b-320">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="c520b-321">您可能會看到 SharePoint Online 租用戶連線到 CDN 服務如預期_設定擱置_郵件。</span><span class="sxs-lookup"><span data-stu-id="c520b-321">You may see a _Configuration pending_ message which is expected as the SharePoint Online tenant connects to the CDN service.</span></span> <span data-ttu-id="c520b-322">這可能需要長達 15 分鐘。</span><span class="sxs-lookup"><span data-stu-id="c520b-322">This can take up to 15 minutes.</span></span>

### <a name="manage-the-office-365-cdn"></a><span data-ttu-id="c520b-323">管理 Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="c520b-323">Manage the Office 365 CDN</span></span>
<span data-ttu-id="c520b-324"><a name="CDNManage"> </a></span><span class="sxs-lookup"><span data-stu-id="c520b-324"></span></span>

<span data-ttu-id="c520b-325">一旦您已設定好 CDN，您可以變更您的組態更新內容，或為您的需求改變時，這一節所述。</span><span class="sxs-lookup"><span data-stu-id="c520b-325">Once you've set up the CDN, you can make changes to your configuration as you update content or as your needs change, as described in this section.</span></span>
  
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a><span data-ttu-id="c520b-326">新增、 更新或移除 Office 365 CDN 資產</span><span class="sxs-lookup"><span data-stu-id="c520b-326">Add, update, or remove assets from the Office 365 CDN</span></span>
<span data-ttu-id="c520b-327"><a name="Office365CDNforSPOaddremoveasset"> </a></span><span class="sxs-lookup"><span data-stu-id="c520b-327"></span></span>

<span data-ttu-id="c520b-328">當您完成設定步驟時，您可以新增新的資產，並更新或移除現有的資產，每當您想要。</span><span class="sxs-lookup"><span data-stu-id="c520b-328">Once you've completed the setup steps, you can add new assets, and update or remove existing assets whenever you want.</span></span> <span data-ttu-id="c520b-329">只要變更您的資料夾或識別為原始來源的 SharePoint 文件庫中資產。</span><span class="sxs-lookup"><span data-stu-id="c520b-329">Just make your changes to the assets in the folder or SharePoint library that you identified as an origin.</span></span> <span data-ttu-id="c520b-330">如果您新增新的資產，它是透過 CDN 立即。</span><span class="sxs-lookup"><span data-stu-id="c520b-330">If you add a new asset, it is available through the CDN immediately.</span></span> <span data-ttu-id="c520b-331">不過，如果您更新資產，它將會需要最多 15 分鐘的傳播並成為 CDN 中可用的新複本。</span><span class="sxs-lookup"><span data-stu-id="c520b-331">However, if you update the asset, it will take up to 15 minutes for the new copy to propagate and become available in the CDN.</span></span>
  
<span data-ttu-id="c520b-332">如果您需要擷取原點的位置，您可以使用**Get-SPOTenantCdnOrigins**指令程式。</span><span class="sxs-lookup"><span data-stu-id="c520b-332">If you need to retrieve the location of the origin, you can use the **Get-SPOTenantCdnOrigins** cmdlet.</span></span> <span data-ttu-id="c520b-333">如需如何使用此指令程式的資訊，請參閱 < <b0>Get SPOTenantCdnOrigins</b0>。</span><span class="sxs-lookup"><span data-stu-id="c520b-333">For information on how to use this cmdlet, see [Get-SPOTenantCdnOrigins](https://technet.microsoft.com/en-us/library/mt790770.aspx).</span></span>
  
#### <a name="remove-an-origin-from-the-office-365-cdn"></a><span data-ttu-id="c520b-334">從 CDN 將 Office 365 中移除原始來源</span><span class="sxs-lookup"><span data-stu-id="c520b-334">Remove an origin from the Office 365 CDN</span></span>
<span data-ttu-id="c520b-335"><a name="Office365CDNforSPORemoveOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="c520b-335"></span></span>

<span data-ttu-id="c520b-336">您可以移除資料夾或識別為原始來源的 SharePoint 文件庫的存取權。</span><span class="sxs-lookup"><span data-stu-id="c520b-336">You can remove access to a folder or SharePoint library that you identified as an origin.</span></span> <span data-ttu-id="c520b-337">若要這麼做，請使用**Remove SPOTenantCdnOrigin**指令程式。</span><span class="sxs-lookup"><span data-stu-id="c520b-337">To do this, use the **Remove-SPOTenantCdnOrigin** cmdlet.</span></span>

``` powershell
Remove-SPOTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

<span data-ttu-id="c520b-338">如需如何使用此指令程式的資訊，請參閱 <<c0>移除 SPOTenantCdnOrigin。</span><span class="sxs-lookup"><span data-stu-id="c520b-338">For information on how to use this cmdlet, see [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx).</span></span>
  
#### <a name="modify-an-origin-in-the-office-365-cdn"></a><span data-ttu-id="c520b-339">修改 CDN 將 Office 365 中的原始來源</span><span class="sxs-lookup"><span data-stu-id="c520b-339">Modify an origin in the Office 365 CDN</span></span>
<span data-ttu-id="c520b-340"><a name="Office365CDNforSPORemoveOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="c520b-340"></span></span>

<span data-ttu-id="c520b-341">您無法修改已建立的原始來源。</span><span class="sxs-lookup"><span data-stu-id="c520b-341">You cannot modify an origin you've created.</span></span> <span data-ttu-id="c520b-342">相反地，移除原始來源，然後加入一個新。</span><span class="sxs-lookup"><span data-stu-id="c520b-342">Instead, remove the origin and then add a new one.</span></span> <span data-ttu-id="c520b-343">如需詳細資訊，請參閱[移除從 Office 365 CDN 原始來源](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin)及[新增您資產的原點而言](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin)。</span><span class="sxs-lookup"><span data-stu-id="c520b-343">For more information, see [To remove an origin from the Office 365 CDN](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) and [To add an origin for your assets](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).</span></span>
  
#### <a name="disable-the-office-365-cdn"></a><span data-ttu-id="c520b-344">停用 Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="c520b-344">Disable the Office 365 CDN</span></span>
<span data-ttu-id="c520b-345"><a name="Office365CDNforSPODisable"> </a></span><span class="sxs-lookup"><span data-stu-id="c520b-345"></span></span>

<span data-ttu-id="c520b-346">若要停用組織 CDN 使用**組 SPOTenantCdnEnabled**指令程式。</span><span class="sxs-lookup"><span data-stu-id="c520b-346">Use the **Set-SPOTenantCdnEnabled** cmdlet to disable the CDN for your organization.</span></span> <span data-ttu-id="c520b-347">如果您有兩個公用和私人原點啟用 CDN，您需要執行的指令程式兩次，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="c520b-347">If you have both the public and private origins enabled for the CDN, you need to run the cmdlet twice as shown in the following examples.</span></span>
  
<span data-ttu-id="c520b-348">若要停用使用的公用原點 CDN 中，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="c520b-348">To disable use of public origins in the CDN, enter the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

<span data-ttu-id="c520b-349">若要停用的私用的原點 CDN 中使用，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="c520b-349">To disable use of the private origins in the CDN, enter the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

<span data-ttu-id="c520b-350">如需此 cmdlet 的詳細資訊，請參閱 <<c0>設定 SPOTenantCdnEnabled。</span><span class="sxs-lookup"><span data-stu-id="c520b-350">For more information about this cmdlet, see [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span></span>

## <a name="set-up-and-configure-the-office-365-cdn-using-the-office-365-cli"></a><span data-ttu-id="c520b-351">安裝及設定 Office 365 CDN 使用 Office 365 CLI</span><span class="sxs-lookup"><span data-stu-id="c520b-351">Set up and configure the Office 365 CDN using the Office 365 CLI</span></span>
<span data-ttu-id="c520b-352"><a name="CDNSetupinCLI"> </a></span><span class="sxs-lookup"><span data-stu-id="c520b-352"></span></span>

<span data-ttu-id="c520b-353">本節中的程序需要您已安裝[Office 365 CLI](https://aka.ms/o365cli)。</span><span class="sxs-lookup"><span data-stu-id="c520b-353">The procedures in this section require that you have installed the [Office 365 CLI](https://aka.ms/o365cli).</span></span> <span data-ttu-id="c520b-354">接下來，連線到 SharePoint Online 租用戶使用[spo 連線](https://pnp.github.io/office365-cli/cmd/spo/connect/)] 命令。</span><span class="sxs-lookup"><span data-stu-id="c520b-354">Next, connect to your SharePoint Online tenant using the [spo connect](https://pnp.github.io/office365-cli/cmd/spo/connect/) command.</span></span>

<span data-ttu-id="c520b-355">完成下列步驟來安裝及設定以裝載您在 SharePoint Online 中使用 Office 365 CLI 資產 CDN。</span><span class="sxs-lookup"><span data-stu-id="c520b-355">Complete these steps to set up and configure the CDN to host your assets in SharePoint Online using the Office 365 CLI.</span></span>

### <a name="enable-the-office-365-cdn"></a><span data-ttu-id="c520b-356">啟用 Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="c520b-356">Enable the Office 365 CDN</span></span>

<span data-ttu-id="c520b-357">您可以使用[spo cdn set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-set/)命令租用戶中管理 Office 365 CDN 的狀態。</span><span class="sxs-lookup"><span data-stu-id="c520b-357">You can manage the state of the Office 365 CDN in your tenant using the [spo cdn set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-set/) command.</span></span>

<span data-ttu-id="c520b-358">若要啟用 Office 365 公用 CDN 租用戶中執行：</span><span class="sxs-lookup"><span data-stu-id="c520b-358">To enable the Office 365 Public CDN in your tenant execute:</span></span>

```sh
spo cdn set --type Public --enabled true
```

<span data-ttu-id="c520b-359">若要啟用 Office 365 SharePoint CDN，請執行：</span><span class="sxs-lookup"><span data-stu-id="c520b-359">To enable the Office 365 SharePoint CDN, execute:</span></span>

```sh
spo cdn set --type Private --enabled true
```

#### <a name="view-the-current-status-of-the-office-365-cdn"></a><span data-ttu-id="c520b-360">檢視 Office 365 CDN 的目前狀態</span><span class="sxs-lookup"><span data-stu-id="c520b-360">View the current status of the Office 365 CDN</span></span>

<span data-ttu-id="c520b-361">若要檢查 Office 365 CDN 的特定類型是啟用還是停用，請使用[spo cdn get](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-get/)命令。</span><span class="sxs-lookup"><span data-stu-id="c520b-361">To check if the particular type of Office 365 CDN is enabled or disabled, use the [spo cdn get](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-get/) command.</span></span>

<span data-ttu-id="c520b-362">若要檢查 Office 365 公用 CDN 是否已啟用，請執行：</span><span class="sxs-lookup"><span data-stu-id="c520b-362">To check if the Office 365 Public CDN is enabled, execute:</span></span>

```sh
spo cdn get --type Public
```

### <a name="view-the-office-365-cdn-origins"></a><span data-ttu-id="c520b-363">檢視 Office 365 CDN 原點</span><span class="sxs-lookup"><span data-stu-id="c520b-363">View the Office 365 CDN origins</span></span>

<span data-ttu-id="c520b-364">若要檢視目前設定的 Office 365 公用 CDN 原點執行：</span><span class="sxs-lookup"><span data-stu-id="c520b-364">To view the currently configured Office 365 Public CDN origins execute:</span></span>

```sh
spo cdn origin list --type Public
```

<span data-ttu-id="c520b-365">當您啟用 Office 365 CDN 預設佈建原點的相關資訊，請參閱[預設 CDN 原點](use-office-365-cdn-with-spo.md#default-cdn-origins)。</span><span class="sxs-lookup"><span data-stu-id="c520b-365">See [Default CDN origins](use-office-365-cdn-with-spo.md#default-cdn-origins) for information about the origins that are provisioned by default when you enable the Office 365 CDN.</span></span>

### <a name="add-an-office-365-cdn-origin"></a><span data-ttu-id="c520b-366">新增 Office 365 CDN 原始來源</span><span class="sxs-lookup"><span data-stu-id="c520b-366">Add an Office 365 CDN origin</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c520b-367">您應該永遠不會將會被視為機密的 SharePoint 文件庫設定為公用的原始來源組織的資源。</span><span class="sxs-lookup"><span data-stu-id="c520b-367">You should never place resources that are considered sensitive to your organization in a SharePoint document library configured as a public origin.</span></span>

<span data-ttu-id="c520b-368">使用[spo cdn 原點 add](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-add/)命令來定義 CDN 原點。</span><span class="sxs-lookup"><span data-stu-id="c520b-368">Use the [spo cdn origin add](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-add/) command to define a CDN origin.</span></span> <span data-ttu-id="c520b-369">您可以定義多個原點。</span><span class="sxs-lookup"><span data-stu-id="c520b-369">You can define multiple origins.</span></span> <span data-ttu-id="c520b-370">原點是指向 SharePoint 文件庫或資料夾，其中包含您想要裝載的 CDN 資產的 URL。</span><span class="sxs-lookup"><span data-stu-id="c520b-370">The origin is a URL that points to a SharePoint library or folder that contains the assets that you want to be hosted by the CDN.</span></span>

```sh
spo cdn origin add --type [Public | Private] --origin <path>
```

<span data-ttu-id="c520b-371">其中`path`是包含資產的資料夾的相對路徑。</span><span class="sxs-lookup"><span data-stu-id="c520b-371">Where `path` is the relative path to the folder that contains the assets.</span></span> <span data-ttu-id="c520b-372">您可以使用萬用字元，除了相對路徑。</span><span class="sxs-lookup"><span data-stu-id="c520b-372">You can use wildcards in addition to relative paths.</span></span>

<span data-ttu-id="c520b-373">若要為公用的原始來源的所有網站**主版頁面圖庫**中包含所有的資產，請執行：</span><span class="sxs-lookup"><span data-stu-id="c520b-373">To include all assets in the **Master Page Gallery** of all sites as a public origin, execute:</span></span>

```sh
spo cdn origin add --type Public --origin */masterpage
```

<span data-ttu-id="c520b-374">若要設定特定網站集合的私用原始來源，請執行：</span><span class="sxs-lookup"><span data-stu-id="c520b-374">To configure a private origin for a specific site collection, execute:</span></span>

```sh
spo cdn origin add --type Private --origin sites/site1/siteassets
```

> [!NOTE]
> <span data-ttu-id="c520b-375">新增 CDN 原點之後, 可能需要 15 分鐘的時間，您就能夠擷取透過 CDN 服務的檔案。</span><span class="sxs-lookup"><span data-stu-id="c520b-375">After adding a CDN origin, it might take up to 15 minutes for you to be able to retrieve files via the CDN service.</span></span> <span data-ttu-id="c520b-376">您可以驗證是否已經使用[spo cdn 原點清單](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/)命令已啟用的特定的原點而言。</span><span class="sxs-lookup"><span data-stu-id="c520b-376">You can verify if the particular origin has already been enabled using the [spo cdn origin list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) command.</span></span>

### <a name="remove-an-office-365-cdn-origin"></a><span data-ttu-id="c520b-377">移除 Office 365 CDN 原始來源</span><span class="sxs-lookup"><span data-stu-id="c520b-377">Remove an Office 365 CDN origin</span></span>

<span data-ttu-id="c520b-378">使用[spo cdn 原點移除](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-remove/)命令來移除指定的 CDN 類型 CDN 原點。</span><span class="sxs-lookup"><span data-stu-id="c520b-378">Use the [spo cdn origin remove](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-remove/) command to remove a CDN origin for the specified CDN type.</span></span>

<span data-ttu-id="c520b-379">若要從 CDN 組態移除公用的原點而言，請執行：</span><span class="sxs-lookup"><span data-stu-id="c520b-379">To remove a public origin from the CDN configuration, execute:</span></span>

```sh
spo cdn origin remove --type Public --origin */masterpage
```

> [!NOTE]
> <span data-ttu-id="c520b-380">移除 CDN 原點不會影響比對該原點任何文件庫中所儲存的檔案。</span><span class="sxs-lookup"><span data-stu-id="c520b-380">Removing a CDN origin doesn't affect the files stored in any document library matching that origin.</span></span> <span data-ttu-id="c520b-381">如果已使用其 SharePoint URL 已參考這些資產，SharePoint 會自動切換回原始 URL 指向文件庫。</span><span class="sxs-lookup"><span data-stu-id="c520b-381">If these assets have been referenced using their SharePoint URL, SharePoint will automatically switch back to the original URL pointing to the document library.</span></span> <span data-ttu-id="c520b-382">如果不過，您必須使用公用 CDN URL 已參照資產，然後移除原始會中斷連結，並將必須手動將它們變更。</span><span class="sxs-lookup"><span data-stu-id="c520b-382">If, however, assets have been referenced using a public CDN URL, then removing the origin will break the link and you will need to manually change them.</span></span>

### <a name="modify-an-office-365-cdn-origin"></a><span data-ttu-id="c520b-383">修改 Office 365 CDN 原始來源</span><span class="sxs-lookup"><span data-stu-id="c520b-383">Modify an Office 365 CDN origin</span></span>

<span data-ttu-id="c520b-384">您不能修改現有的 CDN 原點。</span><span class="sxs-lookup"><span data-stu-id="c520b-384">It's not possible to modify an existing CDN origin.</span></span> <span data-ttu-id="c520b-385">相反地，您應該移除先前定義的 CDN 原點使用`spo cdn origin remove`命令，並新增新一個使用`spo cdn origin add`命令。</span><span class="sxs-lookup"><span data-stu-id="c520b-385">Instead, you should remove the previously defined CDN origin using the `spo cdn origin remove` command and add a new one using the `spo cdn origin add` command.</span></span>

### <a name="change-the-types-of-files-to-include-in-the-office-365-cdn"></a><span data-ttu-id="c520b-386">變更要在 Office 365 CDN 中包含檔案的類型</span><span class="sxs-lookup"><span data-stu-id="c520b-386">Change the types of files to include in the Office 365 CDN</span></span>

<span data-ttu-id="c520b-387">根據預設，下列檔案類型中隨附的 CDN: _.css、.eot、.gif、.ico、.jpeg、.jpg、.js、.map、.png、.svg、.ttf 和.woff_。</span><span class="sxs-lookup"><span data-stu-id="c520b-387">By default, the following file types are included in the CDN: _.css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, and .woff_.</span></span> <span data-ttu-id="c520b-388">如果您需要在 CDN 中包含其他檔案類型，您可以變更 CDN 組態使用[spo cdn 原則設定](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/)] 指令。</span><span class="sxs-lookup"><span data-stu-id="c520b-388">If you need to include additional file types in the CDN, you can change the CDN configuration using the [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) command.</span></span>

> [!NOTE]
> <span data-ttu-id="c520b-389">在變更的檔案類型清單，請您覆寫目前所定義的清單。</span><span class="sxs-lookup"><span data-stu-id="c520b-389">When changing the list of file types, you overwrite the currently defined list.</span></span> <span data-ttu-id="c520b-390">如果您想要包含其他檔案類型，先使用[spo cdn 原則] 清單中](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/)命令，以找出目前設定的檔案類型。</span><span class="sxs-lookup"><span data-stu-id="c520b-390">If you want to include additional file types, first use the [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) command to find out which file types are currently configured.</span></span>

<span data-ttu-id="c520b-391">若要將_JSON_檔案類型新增至公用 CDN 中包含的檔案類型的預設清單，請執行：</span><span class="sxs-lookup"><span data-stu-id="c520b-391">To add the _JSON_ file type to the default list of file types included in the public CDN, execute:</span></span>

```sh
spo cdn policy set --type Public --policy IncludeFileExtensions --value "CSS,EOT,GIF,ICO,JPEG,JPG,JS,MAP,PNG,SVG,TTF,WOFF,JSON"
```

### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a><span data-ttu-id="c520b-392">變更網站分類您想要從 Office 365 CDN 排除清單</span><span class="sxs-lookup"><span data-stu-id="c520b-392">Change the list of site classifications you want to exclude from the Office 365 CDN</span></span>

<span data-ttu-id="c520b-393">使用[spo cdn 原則設定](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/)命令中排除不想要提供透過 CDN 的網站分類。</span><span class="sxs-lookup"><span data-stu-id="c520b-393">Use the [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) command to exclude site classifications that you do not want to make available over the CDN.</span></span> <span data-ttu-id="c520b-394">根據預設，會不排除任何網站分類。</span><span class="sxs-lookup"><span data-stu-id="c520b-394">By default, no site classifications are excluded.</span></span>

> [!NOTE]
> <span data-ttu-id="c520b-395">在變更排除的網站分類的清單，請您覆寫目前所定義的清單。</span><span class="sxs-lookup"><span data-stu-id="c520b-395">When changing the list of excluded site classifications, you overwrite the currently defined list.</span></span> <span data-ttu-id="c520b-396">如果您想要排除其他分類，先使用[spo cdn 原則] 清單中](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-list/)命令，以找出目前設定的分類。</span><span class="sxs-lookup"><span data-stu-id="c520b-396">If you want to exclude additional classifications, first use the [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-list/) command to find out which classifications are currently configured.</span></span>

<span data-ttu-id="c520b-397">若要排除歸類為_HBI_從公用 CDN 的網站，請執行</span><span class="sxs-lookup"><span data-stu-id="c520b-397">To exclude sites classified as _HBI_ from the public CDN, execute</span></span>

```sh
spo cdn policy set --type Public --policy ExcludeRestrictedSiteClassifications --value "HBI"
```

### <a name="disable-the-office-365-cdn"></a><span data-ttu-id="c520b-398">停用 Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="c520b-398">Disable the Office 365 CDN</span></span>

<span data-ttu-id="c520b-399">若要停用 Office 365 CDN 使用`spo cdn set`命令，例如：</span><span class="sxs-lookup"><span data-stu-id="c520b-399">To disable the Office 365 CDN use the `spo cdn set` command, for example:</span></span>

```sh
spo cdn set --type Public --enabled false
```

## <a name="using-your-cdn-assets"></a><span data-ttu-id="c520b-400">使用 CDN 資產</span><span class="sxs-lookup"><span data-stu-id="c520b-400">Using your CDN assets</span></span>

<span data-ttu-id="c520b-401">既然您已啟用 CDN 與設定的原點和原則，您可以開始使用 CDN 資產。</span><span class="sxs-lookup"><span data-stu-id="c520b-401">Now that you have enabled the CDN and configured origins and policies, you can begin using your CDN assets.</span></span>

<span data-ttu-id="c520b-402">本節將協助您了解如何使用 CDN Url 中您的 SharePoint 頁面和內容，以便 SharePoint 會在公用和私人原點的資產的要求重新導向至 CDN。</span><span class="sxs-lookup"><span data-stu-id="c520b-402">This section will help you understand how to use CDN URLs in your SharePoint pages and content so that SharePoint redirects requests for assets in both public and private origins to the CDN.</span></span>

- [<span data-ttu-id="c520b-403">更新連結至 CDN 資產</span><span class="sxs-lookup"><span data-stu-id="c520b-403">Updating links to CDN assets</span></span>](use-office-365-cdn-with-spo.md#updating-links-to-cdn-assets)
- [<span data-ttu-id="c520b-404">在公用的原點中使用資產</span><span class="sxs-lookup"><span data-stu-id="c520b-404">Using assets in public origins</span></span>](use-office-365-cdn-with-spo.md#using-assets-in-public-origins)
- [<span data-ttu-id="c520b-405">在私人原點中使用資產</span><span class="sxs-lookup"><span data-stu-id="c520b-405">Using assets in private origins</span></span>](use-office-365-cdn-with-spo.md#using-assets-in-private-origins)

<span data-ttu-id="c520b-406">如需如何使用 CDN 裝載用戶端網頁組件的資訊，請參閱主題[主機用戶端網頁組件從 Office 365 CDN （Hello World 第 4 部分）](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)。</span><span class="sxs-lookup"><span data-stu-id="c520b-406">For information on how to use the CDN for hosting client-side web parts, see the topic [Host your client-side web part from Office 365 CDN (Hello World part 4)](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn).</span></span>

### <a name="updating-links-to-cdn-assets"></a><span data-ttu-id="c520b-407">更新連結至 CDN 資產</span><span class="sxs-lookup"><span data-stu-id="c520b-407">Updating links to CDN assets</span></span>

<span data-ttu-id="c520b-408">若要使用您新增至原始來源的資產，您只需更新連結到原始的檔案取代為來源中的檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="c520b-408">To use assets that you have added to an origin, you simply update links to the original file with the path to the file in the origin.</span></span>

- <span data-ttu-id="c520b-409">編輯頁面或包含連結至您新增至原始來源的資產的內容。</span><span class="sxs-lookup"><span data-stu-id="c520b-409">Edit the page or content that contains links to assets you have added to an origin.</span></span> <span data-ttu-id="c520b-410">您也可以使用幾種方法之一，以全域搜尋，並取代連結跨 enter 網站或網站集合，如果您想要顯示的每個地方指定資產更新連結。</span><span class="sxs-lookup"><span data-stu-id="c520b-410">You can also use one of several methods to globally search and replace links across an enter site or site collection if you want to update the link to a given asset everywhere it appears.</span></span>
- <span data-ttu-id="c520b-411">每個連結中原點資產，取代 CDN 原始來源中的檔案的路徑中的路徑。</span><span class="sxs-lookup"><span data-stu-id="c520b-411">For each link to an asset in an origin, replace the path with the path to the file in the CDN origin.</span></span> <span data-ttu-id="c520b-412">您可以使用相對路徑。</span><span class="sxs-lookup"><span data-stu-id="c520b-412">You can use relative paths.</span></span>
- <span data-ttu-id="c520b-413">儲存在頁面或內容。</span><span class="sxs-lookup"><span data-stu-id="c520b-413">Save the page or content.</span></span>

<span data-ttu-id="c520b-414">例如，假設影像 _/site/SiteAssets/images/image.png_，其中已複製到文件庫資料夾_讀/網站/CDN_origins/公開 /_。</span><span class="sxs-lookup"><span data-stu-id="c520b-414">For example, consider the image _/site/SiteAssets/images/image.png_, which you have copied to the document library folder _/site/CDN_origins/public/_.</span></span> <span data-ttu-id="c520b-415">若要使用 CDN 資產，取代若要讓新的 URL _/site/CDN_origins/public/image.png_原始來源的路徑中的影像檔案位置的原始路徑。</span><span class="sxs-lookup"><span data-stu-id="c520b-415">To use the CDN asset, replace the original path to the image file location with the path to the origin to make the new URL _/site/CDN_origins/public/image.png_.</span></span>

<span data-ttu-id="c520b-416">如果您想要使用資產的完整 URL，而不是相對路徑，建構連結仿照下列所示：</span><span class="sxs-lookup"><span data-stu-id="c520b-416">If you want to use the full URL to the asset instead of a relative path, construct the link like so:</span></span>

`https://<TenantHostName>.sharepoint.com/sites/site/CDN_origins/public/image.png`

> [!NOTE]
> <span data-ttu-id="c520b-417">一般而言，您應該不硬 Url 直接在 CDN 資產。</span><span class="sxs-lookup"><span data-stu-id="c520b-417">In general, you should not hardcode URLs directly to assets in the CDN.</span></span> <span data-ttu-id="c520b-418">不過，您可以手動建構 Url 中公開的原點的資產視。</span><span class="sxs-lookup"><span data-stu-id="c520b-418">However, you can manually construct URLs for assets in public origins if needed.</span></span> <span data-ttu-id="c520b-419">如需詳細資訊，請參閱 <<c0>公用資產的硬式編碼 CDN Url。</span><span class="sxs-lookup"><span data-stu-id="c520b-419">For more information, see [Hardcoding CDN URLs for public assets](use-office-365-cdn-with-spo.md#hardcoding-cdn-urls-for-public-assets).</span></span>

<span data-ttu-id="c520b-420">若要深入了解如何確認，正在從 CDN 提供資產，請參閱[如何確認資產，由 CDN？](use-office-365-cdn-with-spo.md#CDNConfirm) [疑難排解 Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) ] 區段中。</span><span class="sxs-lookup"><span data-stu-id="c520b-420">To learn about how to verify that assets are being served from the CDN, see [How do I confirm that assets are being served by the CDN?](use-office-365-cdn-with-spo.md#CDNConfirm) in the [Troubleshooting the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) section.</span></span>

### <a name="using-assets-in-public-origins"></a><span data-ttu-id="c520b-421">在公用的原點中使用資產</span><span class="sxs-lookup"><span data-stu-id="c520b-421">Using assets in public origins</span></span>

<span data-ttu-id="c520b-422">**發佈功能**在 SharePoint Online 中自動修正儲存在公用的原點至 CDN 相等，以便從 CDN 服務，而不是 SharePoint 提供資產的資產的 Url。</span><span class="sxs-lookup"><span data-stu-id="c520b-422">The **Publishing feature** in SharePoint Online automatically rewrites URLs of assets stored in public origins to their CDN equivalents so that assets are served from the CDN service instead of SharePoint.</span></span>

<span data-ttu-id="c520b-423">如果您的原始來源與發佈網站中啟用功能，且您想要卸載到 CDN 的資產處於下列類別之一，SharePoint 會自動修正 Url 資產的原點而言，假設資產已不被排除的 CDN 原則。</span><span class="sxs-lookup"><span data-stu-id="c520b-423">If your origin is in a site with the Publishing feature enabled, and the assets you want to offload to the CDN are in one of the following categories, SharePoint will automatically rewrite URLs for assets in the origin, provided that the asset has not been excluded by a CDN policy.</span></span>

<span data-ttu-id="c520b-424">以下是一種連結會自動修正的 SharePoint 發佈功能的概觀：</span><span class="sxs-lookup"><span data-stu-id="c520b-424">The following is an overview of which links are automatically rewritten by the SharePoint Publishing feature:</span></span>

- <span data-ttu-id="c520b-425">在傳統的發佈頁面 HTML 回應中的 IMG/連結/CSS Url</span><span class="sxs-lookup"><span data-stu-id="c520b-425">IMG/LINK/CSS URLs in classic publishing page HTML responses</span></span>
  - <span data-ttu-id="c520b-426">這包括內] 頁面上的 HTML 內容作者所加入的影像</span><span class="sxs-lookup"><span data-stu-id="c520b-426">This includes images added by authors within the HTML content of a page</span></span>
- <span data-ttu-id="c520b-427">圖片庫投影片放映： 網頁組件圖像 Url</span><span class="sxs-lookup"><span data-stu-id="c520b-427">Picture Library SlideShow webpart image URLs</span></span>
- <span data-ttu-id="c520b-428">SPList REST API (RenderListDataAsStream) 結果中的圖像欄位</span><span class="sxs-lookup"><span data-stu-id="c520b-428">Image fields in SPList REST API (RenderListDataAsStream) results</span></span>
  - <span data-ttu-id="c520b-429">使用新屬性_ImageFieldsToTryRewriteToCdnUrls_來提供的欄位以逗號分隔清單</span><span class="sxs-lookup"><span data-stu-id="c520b-429">Use the new property _ImageFieldsToTryRewriteToCdnUrls_ to provide a comma separated list of fields</span></span>
  - <span data-ttu-id="c520b-430">支援的超連結欄位和 PublishingImage 欄位</span><span class="sxs-lookup"><span data-stu-id="c520b-430">Supports hyperlink fields and PublishingImage fields</span></span>
- <span data-ttu-id="c520b-431">SharePoint 影像轉譯</span><span class="sxs-lookup"><span data-stu-id="c520b-431">SharePoint image renditions</span></span>

<span data-ttu-id="c520b-432">下圖說明工作流程，當 SharePoint 收到包含從公用原點的資產頁面要求。</span><span class="sxs-lookup"><span data-stu-id="c520b-432">The following diagram illustrates the workflow when SharePoint receives a request for a page containing assets from a public origin.</span></span>

<span data-ttu-id="c520b-433">![工作流程圖表： 從公用的原始來源擷取 Office 365 CDN 資產](media/O365-CDN/o365-cdn-public-steps-transparent.svg "工作流程： 從公用的原始來源擷取 Office 365 CDN 資產")</span><span class="sxs-lookup"><span data-stu-id="c520b-433">![Workflow diagram: Retrieving Office 365 CDN assets from a public origin](media/O365-CDN/o365-cdn-public-steps-transparent.svg "Workflow: Retrieving Office 365 CDN assets from a public origin")</span></span>

> [!TIP]
> <span data-ttu-id="c520b-434">如果您想要停用自動修正的頁面上的特定 Url，您可以取出頁面，並新增查詢字串參數 **?NoAutoReWrites = true**至您想要停用每個連結的結尾。</span><span class="sxs-lookup"><span data-stu-id="c520b-434">If you want to disable auto-rewriting for specific URLs on a page, you can check out the page and add the query string parameter **?NoAutoReWrites=true** to the end of each link you want to disable.</span></span>

#### <a name="hardcoding-cdn-urls-for-public-assets"></a><span data-ttu-id="c520b-435">公用資產的硬式編碼 CDN Url</span><span class="sxs-lookup"><span data-stu-id="c520b-435">Hardcoding CDN URLs for public assets</span></span>

<span data-ttu-id="c520b-436">如果公用的原點而言，未啟用_發佈_功能，或資產不是其中一個 CDN 服務的自動修正功能所支援的連結類型，可以手動建構資產 CDN 位置的 Url，並在您的內容中使用這些 Url。</span><span class="sxs-lookup"><span data-stu-id="c520b-436">If the _Publishing_ feature is not enabled for a public origin, or the asset is not one of the link types supported by the auto-rewrite feature of the CDN service, you can manually construct URLs to the CDN location of the assets and use these URLs in your content.</span></span>

> [!NOTE]
> <span data-ttu-id="c520b-437">您不能硬 CDN Url 中私人原點的資產，因為表單 URL 的最後一個區段的必要的存取權杖產生要求資源的時間。</span><span class="sxs-lookup"><span data-stu-id="c520b-437">You cannot hardcode CDN URLs to assets in a private origin because the required access token that forms the last section of the URL is generated at the time the resource is requested.</span></span>

<span data-ttu-id="c520b-438">公用 CDN 資產，URL 格式看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="c520b-438">For public CDN assets, the URL format will look like the following:</span></span>

``` html
https://publiccdn.sharepointonline.com/<TenantHostName>/sites/site/library/asset.png
```

<span data-ttu-id="c520b-439">**TenantHostName**取代為您的租用戶名稱。</span><span class="sxs-lookup"><span data-stu-id="c520b-439">Replace **TenantHostName** with your tenant name.</span></span> <span data-ttu-id="c520b-440">範例：</span><span class="sxs-lookup"><span data-stu-id="c520b-440">Example:</span></span>

``` html
https://publiccdn.sharepointonline.com/contoso.sharepoint.com/sites/site/library/asset.png
```

### <a name="using-assets-in-private-origins"></a><span data-ttu-id="c520b-441">在私人原點中使用資產</span><span class="sxs-lookup"><span data-stu-id="c520b-441">Using assets in private origins</span></span>

<span data-ttu-id="c520b-442">無需額外設定，才能在私人原點中使用資產。</span><span class="sxs-lookup"><span data-stu-id="c520b-442">No additional configuration is required to use assets in private origins.</span></span> <span data-ttu-id="c520b-443">SharePoint Online 自動修正 Url 中私人原點的資產讓這些資產的要求永遠都會服務從 CDN。</span><span class="sxs-lookup"><span data-stu-id="c520b-443">SharePoint Online automatically rewrites URLs for assets in private origins so requests for those assets will always be served from the CDN.</span></span> <span data-ttu-id="c520b-444">因為這些 Url 包含必須要求資產時間是由 SharePoint Online 自動產生的語彙基元，無法以手動方式中私人原點的 CDN 資產建置 Url。</span><span class="sxs-lookup"><span data-stu-id="c520b-444">You cannot manually build URLs to CDN assets in private origins because these URLs contain tokens that must be auto-generated by SharePoint Online at the time the asset is requested.</span></span>

<span data-ttu-id="c520b-445">私用原點中的資產的存取受保護的動態產生的語彙基元根據使用者在起點的權限與下列各節所述出現警告。</span><span class="sxs-lookup"><span data-stu-id="c520b-445">Access to assets in private origins is protected by dynamically generated tokens based on user permissions to the origin, with the caveats described in the following sections.</span></span> <span data-ttu-id="c520b-446">使用者必須至少具有**讀取**存取權來呈現內容 CDN 的原點。</span><span class="sxs-lookup"><span data-stu-id="c520b-446">Users must have at least **read** access to the origins for the CDN to render content.</span></span>

<span data-ttu-id="c520b-447">下圖說明工作流程，當 SharePoint 收到包含從私人原點的資產頁面要求。</span><span class="sxs-lookup"><span data-stu-id="c520b-447">The following diagram illustrates the workflow when SharePoint receives a request for a page containing assets from a private origin.</span></span>

<span data-ttu-id="c520b-448">![工作流程圖表： 從私人的原始來源擷取 Office 365 CDN 資產](media/O365-CDN/o365-cdn-private-steps-transparent.svg "工作流程： 從私人的原始來源擷取 Office 365 CDN 資產")</span><span class="sxs-lookup"><span data-stu-id="c520b-448">![Workflow diagram: Retrieving Office 365 CDN assets from a private origin](media/O365-CDN/o365-cdn-private-steps-transparent.svg "Workflow: Retrieving Office 365 CDN assets from a private origin")</span></span>

#### <a name="token-based-authorization-in-private-origins"></a><span data-ttu-id="c520b-449">在私人原點語彙基元為基礎的授權</span><span class="sxs-lookup"><span data-stu-id="c520b-449">Token-based authorization in private origins</span></span>

<span data-ttu-id="c520b-450">SharePoint Online 所產生的語彙基元是授與存取權 CDN 將 Office 365 中的私人原點的資產。</span><span class="sxs-lookup"><span data-stu-id="c520b-450">Access to assets in private origins in the Office 365 CDN is granted by tokens generated by SharePoint Online.</span></span> <span data-ttu-id="c520b-451">已存取至資料夾或指定原始文件庫的權限的使用者會自動授與允許使用者存取檔案是根據其權限等級的權杖。</span><span class="sxs-lookup"><span data-stu-id="c520b-451">Users who already have permission to access to the folder or library designated by the origin are automatically granted tokens that permit the user to access the file based on their permission level.</span></span> <span data-ttu-id="c520b-452">這些存取權杖是有效 30 至 90 分鐘後它們會產生以協助防止權杖重新執行攻擊。</span><span class="sxs-lookup"><span data-stu-id="c520b-452">These access tokens are valid for 30 to 90 minutes after they are generated to help prevent token replay attacks.</span></span>

<span data-ttu-id="c520b-453">一旦產生的存取權杖，SharePoint Online 會傳回自訂 URI 包含兩個授權參數_吃_（edge 授權權杖） 和_oat_ （原點授權權杖） 用戶端。</span><span class="sxs-lookup"><span data-stu-id="c520b-453">Once the access token is generated, SharePoint Online returns a custom URI to the client containing two authorization parameters _eat_ (edge authorization token) and _oat_ (origin authorization token).</span></span> <span data-ttu-id="c520b-454">每個語彙基元的結構是 _< '到期時間期間時間格式 '>_<' 安全簽章中的' >_。</span><span class="sxs-lookup"><span data-stu-id="c520b-454">The structure of each token is _<'expiration time in Epoch time format'>__<'secure signature'>_.</span></span> <span data-ttu-id="c520b-455">例如：</span><span class="sxs-lookup"><span data-stu-id="c520b-455">For example:</span></span>

``` html
https://privatecdn.sharepointonline.com/contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg?eat=1486154359_cc59042c5c55c90b26a2775323c7c8112718431228fe84d568a3795a63912840&oat=1486154359_7d73c2e3ba4b7b1f97242332900616db0d4ffb04312
```

> [!NOTE]
> <span data-ttu-id="c520b-456">語彙基元的持有的任何人都可以存取資源的 CDN。</span><span class="sxs-lookup"><span data-stu-id="c520b-456">Anyone in possession of the token can access the resource in the CDN.</span></span> <span data-ttu-id="c520b-457">不過，包含這些存取 token 只共用透過 HTTPS 的 Url，因此除非權杖到期之前，使用者明確地共用 URL 資產不會是未經授權的使用者可以存取。</span><span class="sxs-lookup"><span data-stu-id="c520b-457">However, URLs containing these access tokens are only shared over HTTPS, so unless the URL is explicitly shared by an end user before the token expires, the asset won’t be accessible to unauthorized users.</span></span>

#### <a name="item-level-permissions-are-not-supported-for-assets-in-private-origins"></a><span data-ttu-id="c520b-458">在私人原點的資產不支援項目層級權限</span><span class="sxs-lookup"><span data-stu-id="c520b-458">Item-level permissions are not supported for assets in private origins</span></span>

<span data-ttu-id="c520b-459">請務必注意，SharePoint Online 不支援項目層級權限在私人原點的資產。</span><span class="sxs-lookup"><span data-stu-id="c520b-459">It is important to note that SharePoint Online does not support item-level permissions for assets in private origins.</span></span> <span data-ttu-id="c520b-460">例如，針對檔案位於`https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`，使用者具有有效的存取權給予符合下列條件的檔案：</span><span class="sxs-lookup"><span data-stu-id="c520b-460">For example, for a file located at `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`, users have effective access to the file given the following conditions:</span></span>

|<span data-ttu-id="c520b-461">使用者</span><span class="sxs-lookup"><span data-stu-id="c520b-461">User</span></span>  |<span data-ttu-id="c520b-462">權限</span><span class="sxs-lookup"><span data-stu-id="c520b-462">Permissions</span></span>  |<span data-ttu-id="c520b-463">有效的存取</span><span class="sxs-lookup"><span data-stu-id="c520b-463">Effective access</span></span>  |
|---------|---------|---------|
|<span data-ttu-id="c520b-464">使用者 1</span><span class="sxs-lookup"><span data-stu-id="c520b-464">User 1</span></span>     |<span data-ttu-id="c520b-465">有權存取 folder1</span><span class="sxs-lookup"><span data-stu-id="c520b-465">Has access to folder1</span></span>         |<span data-ttu-id="c520b-466">可以存取 image1.jpg 從 CDN</span><span class="sxs-lookup"><span data-stu-id="c520b-466">Can access image1.jpg from the CDN</span></span>         |
|<span data-ttu-id="c520b-467">使用者 2</span><span class="sxs-lookup"><span data-stu-id="c520b-467">User 2</span></span>     |<span data-ttu-id="c520b-468">沒有存取權 folder1</span><span class="sxs-lookup"><span data-stu-id="c520b-468">Does not have access to folder1</span></span>         |<span data-ttu-id="c520b-469">無法存取 image1.jpg 從 CDN</span><span class="sxs-lookup"><span data-stu-id="c520b-469">Cannot access image1.jpg from the CDN</span></span>         |
|<span data-ttu-id="c520b-470">使用者 3</span><span class="sxs-lookup"><span data-stu-id="c520b-470">User 3</span></span>     |<span data-ttu-id="c520b-471">沒有存取權 folder1，但是會授與存取 SharePoint Online 中的 image1.jpg 明確權限</span><span class="sxs-lookup"><span data-stu-id="c520b-471">Does not have access to folder1, but is granted explicit permission to access image1.jpg in SharePoint Online</span></span>         |<span data-ttu-id="c520b-472">可以存取資產 image1.jpg，直接從 SharePoint Online 中，但不是從 CDN</span><span class="sxs-lookup"><span data-stu-id="c520b-472">Can access the asset image1.jpg directly from SharePoint Online, but not from the CDN</span></span>         |
|<span data-ttu-id="c520b-473">使用者 4</span><span class="sxs-lookup"><span data-stu-id="c520b-473">User 4</span></span>     |<span data-ttu-id="c520b-474">有權存取 folder1，但已明確拒絕存取 SharePoint Online 中的 image1.jpg</span><span class="sxs-lookup"><span data-stu-id="c520b-474">Has access to folder1, but has been explicitly denied access to image1.jpg in SharePoint Online</span></span>         |<span data-ttu-id="c520b-475">無法從 SharePoint Online 中，存取資產，但可以存取資產從 CDN 而不管遭拒絕存取 SharePoint Online 中的檔案</span><span class="sxs-lookup"><span data-stu-id="c520b-475">Cannot access the asset from SharePoint Online, but can access the asset from the CDN despite being denied access to the file in SharePoint Online</span></span>         |

## <a name="troubleshooting-the-office-365-cdn"></a><span data-ttu-id="c520b-476">疑難排解 Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="c520b-476">Troubleshooting the Office 365 CDN</span></span>
<span data-ttu-id="c520b-477"><a name="CDNTroubleshooting"> </a></span><span class="sxs-lookup"><span data-stu-id="c520b-477"></span></span>

### <a name="how-do-i-confirm-that-assets-are-being-served-by-the-cdn"></a><span data-ttu-id="c520b-478">如何確認資產，由 CDN？</span><span class="sxs-lookup"><span data-stu-id="c520b-478">How do I confirm that assets are being served by the CDN?</span></span>
<span data-ttu-id="c520b-479"><a name="CDNConfirm"> </a></span><span class="sxs-lookup"><span data-stu-id="c520b-479"></span></span>

<span data-ttu-id="c520b-480">一旦您已新增連結] 頁面上的 CDN 資產，您可以確認的資產由從 CDN 瀏覽至 [] 頁面上、 滑鼠右鍵按一下 [影像後已轉譯及檢閱的影像 URL。</span><span class="sxs-lookup"><span data-stu-id="c520b-480">Once you have added links to CDN assets to a page, you can confirm that the asset is being served from the CDN by browsing to the page, right clicking on the image once it has rendered and reviewing the image URL.</span></span>

<span data-ttu-id="c520b-481">您也可以使用瀏覽器的開發人員工具，在頁面上，檢視每個資產的 URL，或使用 3rd 廠商網路追蹤工具。</span><span class="sxs-lookup"><span data-stu-id="c520b-481">You can also use your browser's developer tools to view the URL for each asset on a page, or use a 3rd party network trace tool.</span></span>

> [!NOTE]
> <span data-ttu-id="c520b-482">如果您使用 Fiddler 之類的網路來測試您資產外轉譯資產從 SharePoint] 頁面上，您必須手動新增查閱者標頭 」 查閱者： `https://yourdomain.sharepoint.com`」 至其中的 URL 是您的 SharePoint Online 租用戶的根 URL GET 要求。</span><span class="sxs-lookup"><span data-stu-id="c520b-482">If you use a network tool such as Fiddler to test your assets outside of rendering the asset from a SharePoint page, you must manually add the referrer header “Referrer: `https://yourdomain.sharepoint.com`” to the GET request where the URL is the root URL of your SharePoint Online tenant.</span></span>

<span data-ttu-id="c520b-483">您無法直接在網頁瀏覽器中測試 CDN Url，因為您必須具有來自 SharePoint Online 查閱者。</span><span class="sxs-lookup"><span data-stu-id="c520b-483">You cannot test CDN URLs directly in a web browser because you must have a referrer coming from SharePoint Online.</span></span> <span data-ttu-id="c520b-484">不過，如果您將 CDN 資產 URL 新增至 SharePoint] 頁面上，然後在瀏覽器中開啟] 頁面上，您會看到在頁面上呈現 CDN 資產。</span><span class="sxs-lookup"><span data-stu-id="c520b-484">However, if you add the CDN asset URL to a SharePoint page and then open the page in a browser, you will see the CDN asset rendered on the page.</span></span>

<span data-ttu-id="c520b-485">如需有關如何在 Microsoft Edge 瀏覽器中使用的開發人員工具的詳細資訊，請參閱 < <b0>Microsoft Edge 開發人員工具</b0>。</span><span class="sxs-lookup"><span data-stu-id="c520b-485">For more information on using the developer tools in the Microsoft Edge browser, see [Microsoft Edge Developer Tools](https://docs.microsoft.com/en-us/microsoft-edge/devtools-guide).</span></span>

### <a name="why-are-assets-from-a-new-origin-unavailable"></a><span data-ttu-id="c520b-486">為何無法使用的新的原點從資產？</span><span class="sxs-lookup"><span data-stu-id="c520b-486">Why are assets from a new origin unavailable?</span></span>
<span data-ttu-id="c520b-487">資產中新的原點會立即無法可供使用，因為所花的時間才能傳播到 CDN 註冊並從原點上載至 CDN 儲存資產。</span><span class="sxs-lookup"><span data-stu-id="c520b-487">Assets in new origins will not immediately be available for use, as it takes time for the registration to propagate through the CDN and for the assets to be uploaded from the origin to CDN storage.</span></span> <span data-ttu-id="c520b-488">可在 CDN 資產所需的時間取決於多少資產和檔案大小。</span><span class="sxs-lookup"><span data-stu-id="c520b-488">The time required for assets to be available in the CDN depends on how many assets and the files sizes.</span></span>

### <a name="my-client-side-web-part-or-sharepoint-framework-solution-isnt-working"></a><span data-ttu-id="c520b-489">我的用戶端網頁組件或 SharePoint 架構解決方案無法正常運作</span><span class="sxs-lookup"><span data-stu-id="c520b-489">My client-side web part or SharePoint Framework solution isn't working</span></span>

<span data-ttu-id="c520b-490">當您啟用公用原點 CDN 將 Office 365 時，CDN 服務會自動建立這些預設原點：</span><span class="sxs-lookup"><span data-stu-id="c520b-490">When you enable the Office 365 CDN for public origins, the CDN service automatically creates these default origins:</span></span>

- <span data-ttu-id="c520b-491">\* / 主版頁面</span><span class="sxs-lookup"><span data-stu-id="c520b-491">\*/MASTERPAGE</span></span>
- <span data-ttu-id="c520b-492">\* / 樣式庫</span><span class="sxs-lookup"><span data-stu-id="c520b-492">\*/STYLE LIBRARY</span></span>
- <span data-ttu-id="c520b-493">\* / CLIENTSIDEASSETS</span><span class="sxs-lookup"><span data-stu-id="c520b-493">\*/CLIENTSIDEASSETS</span></span>

<span data-ttu-id="c520b-494">如果 \* / clientsideassets 原點遺漏、 SharePoint 架構解決方案會失敗，而且會產生任何警告或錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="c520b-494">If the \*/clientsideassets origin is missing, SharePoint Framework solutions will fail, and no warning or error messages are generated.</span></span> <span data-ttu-id="c520b-495">此原點可能遺失，因為 CDN 已啟用與 _-NoDefaultOrigins_參數設為 **$true**，或是手動刪除原點。</span><span class="sxs-lookup"><span data-stu-id="c520b-495">This origin may be missing either because the CDN was enabled with the _-NoDefaultOrigins_ parameter set to **$true**, or because the origin was manually deleted.</span></span>

<span data-ttu-id="c520b-496">您可以檢查看看是否 \* / CLIENTSIDEASSETS 原點有搭配下列 PowerShell 命令：</span><span class="sxs-lookup"><span data-stu-id="c520b-496">You can check to see if the \*/CLIENTSIDEASSETS origin is present with the following PowerShell command:</span></span>

``` powershell
Get-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

<span data-ttu-id="c520b-497">或者，您可以檢查與 Office 365 CLI:</span><span class="sxs-lookup"><span data-stu-id="c520b-497">Or you can check with the Office 365 CLI:</span></span>

``` powershell
spo cdn origin list
```

<span data-ttu-id="c520b-498">若要新增原始 PowerShell 中：</span><span class="sxs-lookup"><span data-stu-id="c520b-498">To add the origin in PowerShell:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

<span data-ttu-id="c520b-499">若要在 Office 365 CLI 新增來源：</span><span class="sxs-lookup"><span data-stu-id="c520b-499">To add the origin in the Office 365 CLI:</span></span>

``` powershell
spo cdn origin add --origin */CLIENTSIDEASSETS
```

### <a name="what-powershell-modules-and-cli-shells-do-i-need-to-work-with-the-office-365-cdn"></a><span data-ttu-id="c520b-500">查看 PowerShell 模組與 CLI 殼層我需要為搭配 Office 365 CDN？</span><span class="sxs-lookup"><span data-stu-id="c520b-500">What PowerShell modules and CLI shells do I need to work with the Office 365 CDN?</span></span>

<span data-ttu-id="c520b-501">您可以選擇為搭配 Office 365 CDN 使用**SharePoint Online 管理命令介面**的 PowerShell 模組] 或 [ **Office 365 CLI**。</span><span class="sxs-lookup"><span data-stu-id="c520b-501">You can choose to work with the Office 365 CDN using either the **SharePoint Online Management Shell** PowerShell module or the **Office 365 CLI**.</span></span>

- [<span data-ttu-id="c520b-502">開始使用 SharePoint Online 管理命令介面</span><span class="sxs-lookup"><span data-stu-id="c520b-502">Getting started with SharePoint Online Management Shell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)
- [<span data-ttu-id="c520b-503">安裝 Office 365 CLI</span><span class="sxs-lookup"><span data-stu-id="c520b-503">Installing the Office 365 CLI</span></span>](https://pnp.github.io/office365-cli/user-guide/installing-cli/)

## <a name="see-also"></a><span data-ttu-id="c520b-504">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c520b-504">See also</span></span>

[<span data-ttu-id="c520b-505">內容傳遞網路</span><span class="sxs-lookup"><span data-stu-id="c520b-505">Content Delivery Networks</span></span>](https://aka.ms/o365cdns)

[<span data-ttu-id="c520b-506">Office 365 的網路規劃和效能調整</span><span class="sxs-lookup"><span data-stu-id="c520b-506">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)

