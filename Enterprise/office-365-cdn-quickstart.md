---
title: Office 365 內容傳遞網路（CDN）快速入門
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 06/04/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
description: Office 365 內容傳遞網路（CDN）快速入門
ms.openlocfilehash: 4abaaa5545bc807c4da297c66fd9ad1fb188adc7
ms.sourcegitcommit: 576c3dbdef535f952a861197dea5348908da9504
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "44561917"
---
# <a name="office-365-content-delivery-network-cdn-quickstart"></a><span data-ttu-id="3f0e8-103">Office 365 內容傳遞網路（CDN）快速入門</span><span class="sxs-lookup"><span data-stu-id="3f0e8-103">Office 365 Content Delivery Network (CDN) Quickstart</span></span>

<span data-ttu-id="3f0e8-104">您可以使用內建**Office 365 內容傳遞網路（CDN）** 來裝載靜態資產（影像、JavaScript、樣式單、WOFF 檔案），以提供更佳的 SharePoint 線上頁面效能。</span><span class="sxs-lookup"><span data-stu-id="3f0e8-104">You can use the built-in **Office 365 Content Delivery Network (CDN)** to host static assets (images, JavaScript, Stylesheets, WOFF files) to provide better performance for your SharePoint Online pages.</span></span> <span data-ttu-id="3f0e8-105">Office 365 CDN 透過將靜態資產快取到更靠近提出要求之瀏覽器的位置 (這有助於加速下載以及減少延遲)，藉此改善效能。</span><span class="sxs-lookup"><span data-stu-id="3f0e8-105">The Office 365 CDN improves performance by caching static assets closer to the browsers requesting them, which helps to speed up downloads and reduce latency.</span></span> <span data-ttu-id="3f0e8-106">此外，Office 365 CDN 使用 HTTP/2 通訊協定，以提升壓縮和 HTTP 流水線。</span><span class="sxs-lookup"><span data-stu-id="3f0e8-106">Also, the Office 365 CDN uses the HTTP/2 protocol for improved compression and HTTP pipelining.</span></span> <span data-ttu-id="3f0e8-107">Office 365 CDN 服務包含在 SharePoint Online 訂閱的一部分。</span><span class="sxs-lookup"><span data-stu-id="3f0e8-107">The Office 365 CDN service is included as part of your SharePoint Online subscription.</span></span>

<span data-ttu-id="3f0e8-108">如需詳細資訊指引，請參閱[Use The Office 365 Content 傳遞網路（CDN）與 SharePoint Online](use-office-365-cdn-with-spo.md)。</span><span class="sxs-lookup"><span data-stu-id="3f0e8-108">For more detailed information guidance see [Use the Office 365 Content Delivery Network (CDN) with SharePoint Online](use-office-365-cdn-with-spo.md).</span></span>

>[!NOTE]
><span data-ttu-id="3f0e8-109">Office 365 CDN 只可用於實際執行（全球）雲端的承租人。</span><span class="sxs-lookup"><span data-stu-id="3f0e8-109">The Office 365 CDN is only available to tenants in the production (worldwide) cloud.</span></span> <span data-ttu-id="3f0e8-110">美國政府、中國和德國雲彩中的承租人目前不支援 Office 365 CDN。</span><span class="sxs-lookup"><span data-stu-id="3f0e8-110">Tenants in the US Government, China and Germany clouds do not currently support the Office 365 CDN.</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-identify-items-not-in-cdn"></a><span data-ttu-id="3f0e8-111">使用 SharePoint 工具的頁面診斷來識別不在 CDN 中的專案</span><span class="sxs-lookup"><span data-stu-id="3f0e8-111">Use the Page Diagnostics for SharePoint tool to identify items not in CDN</span></span>

<span data-ttu-id="3f0e8-112">您可以使用**網頁診斷程式 SharePoint 工具**瀏覽器延伸名，輕鬆列出可以新增至 CDN 來源的 SharePoint 線上頁面中的資產。</span><span class="sxs-lookup"><span data-stu-id="3f0e8-112">You can use the **Page Diagnostics for SharePoint tool** browser extension to easily list assets in your SharePoint Online pages that can be added to a CDN origin.</span></span>

<span data-ttu-id="3f0e8-113">**SharePoint 工具的頁面診斷**功能是新 Microsoft Edge 的瀏覽器擴充（ https://www.microsoft.com/edge) 以及分析 SharePoint 線上新式入口網站和傳統發佈網站頁面的 Chrome 瀏覽器）。</span><span class="sxs-lookup"><span data-stu-id="3f0e8-113">The **Page Diagnostics for SharePoint tool** is a browser extension for the new Microsoft Edge (https://www.microsoft.com/edge) and Chrome browsers that analyzes both SharePoint Online modern portal and classic publishing site pages.</span></span> <span data-ttu-id="3f0e8-114">該工具會針對每個分析頁面提供一份報告，顯示頁面如何針對定義的效能準則組執行。</span><span class="sxs-lookup"><span data-stu-id="3f0e8-114">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="3f0e8-115">若要安裝及了解「適用於 SharePoint 的頁面診斷」工具，請造訪[使用適用於 SharePoint Online 的頁面診斷工具](https://aka.ms/perftool)。</span><span class="sxs-lookup"><span data-stu-id="3f0e8-115">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](https://aka.ms/perftool).</span></span>

<span data-ttu-id="3f0e8-116">當您在 SharePoint Online 頁面上為 SharePoint 工具執行頁面診斷時，您可以按一下 [**診斷測試**] 索引標籤，以查看 CDN 未裝載的資產清單。</span><span class="sxs-lookup"><span data-stu-id="3f0e8-116">When you run the Page Diagnostics for SharePoint tool on a SharePoint Online page, you can click the **Diagnostic Tests** tab to see a list of assets not being hosted by the CDN.</span></span> <span data-ttu-id="3f0e8-117">這些資產會列在「標題**內容傳遞網路（CDN）」檢查**底下，如下列螢幕擷取畫面所示。</span><span class="sxs-lookup"><span data-stu-id="3f0e8-117">These assets will be listed under the heading **Content Delivery Network (CDN) check** as shown in the screenshot below.</span></span>

![頁面診斷](media/page-diagnostics-for-spo/pagediag-results-general.PNG)

>[!NOTE]
><span data-ttu-id="3f0e8-119">網頁診斷工具只能用於 SharePoint Online，且無法在 SharePoint 系統頁面使用。</span><span class="sxs-lookup"><span data-stu-id="3f0e8-119">The Page Diagnostics tool only works for SharePoint Online, and cannot be used on a SharePoint system page.</span></span>

## <a name="cdn-overview"></a><span data-ttu-id="3f0e8-120">CDN 概述</span><span class="sxs-lookup"><span data-stu-id="3f0e8-120">CDN Overview</span></span>

<span data-ttu-id="3f0e8-121">Office 365 CDN 的設計是透過將經常存取的物件（例如影像和 javascript 檔案）散佈于一種高速通用網路上，減少頁面載入時間，並盡可能將主控物件的存取權盡可能接近使用者。</span><span class="sxs-lookup"><span data-stu-id="3f0e8-121">The Office 365 CDN is designed to optimize performance for users by distributing frequently accessed objects like images and javascript files over a high-speed global network, reducing page load time and providing access to hosted objects as close as possible to the user.</span></span> <span data-ttu-id="3f0e8-122">CDN 會從一個稱為_來源_的位置提取您的資產。</span><span class="sxs-lookup"><span data-stu-id="3f0e8-122">The CDN fetches your assets from a location called an _origin_.</span></span> <span data-ttu-id="3f0e8-123">來源可以是可透過 URL 存取的 SharePoint 網站、文件庫或資料夾。</span><span class="sxs-lookup"><span data-stu-id="3f0e8-123">An origin can be a SharePoint site, document library or folder that is accessible by a URL.</span></span>

<span data-ttu-id="3f0e8-124">Office 365 CDN 分分為兩種基本類型：</span><span class="sxs-lookup"><span data-stu-id="3f0e8-124">The Office 365 CDN is separated into two basic types:</span></span>

- <span data-ttu-id="3f0e8-125">**公用 CDN**是專門設計用於 .js （JavaScript）、CSS （StyleSheets）、網頁字型檔案（WOFF、WOFF2）和非專有圖像（如公司標誌）。</span><span class="sxs-lookup"><span data-stu-id="3f0e8-125">**Public CDN** is designed to be used for JS (JavaScript), CSS (StyleSheets), Web Font File (WOFF, WOFF2) and non-proprietary images like company logos.</span></span>
- <span data-ttu-id="3f0e8-126">**專用 CDN**是專門設計用來進行影像（PNG、JPG、JPEG 等）。</span><span class="sxs-lookup"><span data-stu-id="3f0e8-126">**Private CDN** is designed to be used for images (PNG, JPG, JPEG, etc.).</span></span>

<span data-ttu-id="3f0e8-127">您可以選擇同時包含組織的公開來源或私人來源。</span><span class="sxs-lookup"><span data-stu-id="3f0e8-127">You can choose to have both public or private origins for your organization.</span></span> <span data-ttu-id="3f0e8-128">大多陣列織會選擇實現兩者的組合。</span><span class="sxs-lookup"><span data-stu-id="3f0e8-128">Most organizations will choose to implement a combination of the two.</span></span> <span data-ttu-id="3f0e8-129">公用和私人選項都提供類似的效能提升，但各項都有獨特的屬性和優點。</span><span class="sxs-lookup"><span data-stu-id="3f0e8-129">Both public and private options provide similar performance gains, but each has unique attributes and advantages.</span></span> <span data-ttu-id="3f0e8-130">如需公用和私人 CDN 來源的詳細資訊，請參閱[選擇每個來源應該是公用還是私人](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)。</span><span class="sxs-lookup"><span data-stu-id="3f0e8-130">For more information about public and private CDN origins, see [Choose whether each origin should be public or private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate).</span></span>

## <a name="how-to-enable-public-and-private-cdn-with-the-default-configuration"></a><span data-ttu-id="3f0e8-131">如何啟用具有預設設定的公用和私人 CDN</span><span class="sxs-lookup"><span data-stu-id="3f0e8-131">How to enable Public and Private CDN with the default configuration</span></span>
<span data-ttu-id="3f0e8-132">在您變更租使用者 CDN 設定之前，您應該確認其符合組織的合規性、安全性和隱私權原則。</span><span class="sxs-lookup"><span data-stu-id="3f0e8-132">Before you make changes to the tenant CDN settings, you should verify that it meets compliance, security and privacy policies of your organization.</span></span>

<span data-ttu-id="3f0e8-133">如需詳細的設定設定，或者您已啟用 CDN，並想要新增其他位置（來源），請參閱[使用 SharePoint 線上管理命令介面設定 Office 365 CDN](use-office-365-cdn-with-spo.md#set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell)一節。</span><span class="sxs-lookup"><span data-stu-id="3f0e8-133">For more detailed configuration settings, or if you have already enabled CDN and want to add additional locations (origins), please see the section [Set up and configure the Office 365 CDN by using the SharePoint Online Management Shell](use-office-365-cdn-with-spo.md#set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell)</span></span>

<span data-ttu-id="3f0e8-134">使用 SharePoint Online 管理命令介面來連線至您的租使用者：</span><span class="sxs-lookup"><span data-stu-id="3f0e8-134">Connect to your tenant using the SharePoint Online Management Shell:</span></span>

```PowerShell
Connect-SPOService -Url https://<YourTenantName>-admin.sharepoint.com
```

<span data-ttu-id="3f0e8-135">若要讓您的組織使用預設設定的公開和私人來源，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="3f0e8-135">To enable your organization to use both public and private origins with the default configuration, type the following command:</span></span>

```PowerShell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

<span data-ttu-id="3f0e8-136">這些 Cmdlet 的輸出應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="3f0e8-136">Output of these cmdlets should look like the following:</span></span>

![SPOTenantCdnEnabled 的輸出](media/O365-CDN/o365-cdn-enable-output.png)

## <a name="see-also"></a><span data-ttu-id="3f0e8-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f0e8-138">See also</span></span>

[<span data-ttu-id="3f0e8-139">使用 Sharepoint Online 網頁診斷工具</span><span class="sxs-lookup"><span data-stu-id="3f0e8-139">Use the Page Diagnostics tool for SharePoint Online</span></span>](https://aka.ms/perftool)

[<span data-ttu-id="3f0e8-140">使用 Office 365 內容傳遞網路 (CDN) 搭配 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="3f0e8-140">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-office-365-cdn-with-spo.md)

[<span data-ttu-id="3f0e8-141">內容傳遞網路</span><span class="sxs-lookup"><span data-stu-id="3f0e8-141">Content Delivery Networks</span></span>](https://aka.ms/o365cdns)

[<span data-ttu-id="3f0e8-142">Office 365 的網路規劃和效能調整</span><span class="sxs-lookup"><span data-stu-id="3f0e8-142">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)

[<span data-ttu-id="3f0e8-143">SharePoint 效能系列-Office 365 CDN 影片系列</span><span class="sxs-lookup"><span data-stu-id="3f0e8-143">SharePoint Performance Series - Office 365 CDN video series</span></span>](https://www.youtube.com/playlist?list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA)
