---
title: 評估 Office 365 網路連線能力
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 8/7/2019
audience: ITPro
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
ms.assetid: 64b420ef-0218-48f6-8a34-74bb27633b10
description: Office 365 被為了讓使得全球客戶服務使用的網際網路連線的連線。 隨著服務發展，安全性、 效能和可靠性的 Office 365 已獲得改善根據上使用網際網路來建立連線至服務的客戶。
ms.openlocfilehash: c96cb8aa7341c0749d198e1fa5459433c40e1062
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844694"
---
# <a name="assessing-office-365-network-connectivity"></a><span data-ttu-id="e3ee1-104">評估 Office 365 網路連線能力</span><span class="sxs-lookup"><span data-stu-id="e3ee1-104">Assessing Office 365 network connectivity</span></span>

<span data-ttu-id="e3ee1-105">*本文適用於 Office 365 企業版和 Microsoft 365 企業版。*</span><span class="sxs-lookup"><span data-stu-id="e3ee1-105">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="e3ee1-106">Office 365 被為了讓使得全球客戶服務使用的網際網路連線的連線。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-106">Office 365 is designed to enable customers all over the world to connect to the service using an internet connection.</span></span> <span data-ttu-id="e3ee1-107">隨著服務發展，安全性、 效能和可靠性的 Office 365 已獲得改善根據上使用網際網路來建立連線至服務的客戶。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-107">As the service evolves, the security, performance, and reliability of Office 365 are improved based on customers using the internet to establish a connection to the service.</span></span>
  
<span data-ttu-id="e3ee1-108">規劃使用 Office 365 的客戶應該評估其現有和預測的網際網路連線能力需求作為部署專案的一部分。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-108">Customers planning to use Office 365 should assess their existing and forecasted internet connectivity needs as a part of the deployment project.</span></span> <span data-ttu-id="e3ee1-109">對於企業類別部署可靠並適當地調整大小的網際網路連線能力屬於重要耗用 Office 365 的功能與案例。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-109">For enterprise class deployments reliable and appropriately sized internet connectivity is a critical part of consuming Office 365 features and scenarios.</span></span>
  
<span data-ttu-id="e3ee1-110">網路評估可以執行由許多不同的人員或組織根據您的大小和喜好設定。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-110">Network evaluations can be performed by many different people and organizations depending on your size and preferences.</span></span> <span data-ttu-id="e3ee1-111">評估網路範圍也可以視其中您正在閱讀在您的部署程序而異。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-111">The network scope of the assessment can also vary depending on where you're at in your deployment process.</span></span> <span data-ttu-id="e3ee1-112">若要可協助您開始的花費執行網路評估更深入了解，我們已產生的網路評估指南，協助您了解您可用的選項。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-112">To help you get a better understanding of what it takes to perform a network assessment, we've produced a network assessment guide to help you understand the options available to you.</span></span> <span data-ttu-id="e3ee1-113">此評定會決定哪些步驟和資源需要新增至部署專案，使您能夠成功地採用 Office 365。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-113">This assessment will determine what steps and resources need to be added to the deployment project to enable you to successfully adopt Office 365.</span></span>
  
<span data-ttu-id="e3ee1-114">完整的網路評估會提供可能的解決方案，以及實作詳細資料的網路設計質詢。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-114">A comprehensive network assessment will provide possible solutions to networking design challenges along with implementation details.</span></span> <span data-ttu-id="e3ee1-115">某些網路 「 評估 」 會顯示可容納最佳化網路連線至 Office 365 與次要設定或現有的網路和網際網路輸出基礎結構的設計變更。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-115">Some network assessments will show that optimal network connectivity to Office 365 can be accommodated with minor configuration or design changes to the existing network and internet egress infrastructure.</span></span>

<span data-ttu-id="e3ee1-116">某些評估會指出對 Office 365 的網路連線時，需要在 [網路元件的額外投資。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-116">Some assessments will indicate network connectivity to Office 365 will require additional investments in networking components.</span></span> <span data-ttu-id="e3ee1-117">例如，橫跨分公司和多個地理區域的企業網路可能需要 SD WAN 解決方案或最佳化的路由基礎結構，以支援網際網路連線到 Office 365 中的投資。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-117">For example, enterprise networks that span branch offices and multiple geographic regions may require investments in SD-WAN solutions or optimized routing infrastructure to support internet connectivity to Office 365.</span></span> <span data-ttu-id="e3ee1-118">有時會評估會指出對 Office 365 的網路連線受到法規或效能需求，例如[Skype for Business Online 媒體品質](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)的案例。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-118">Occasionally an assessment will indicate network connectivity to Office 365 is influenced by regulation or performance requirements for scenarios such as [Skype for Business Online media quality](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).</span></span> <span data-ttu-id="e3ee1-119">這些額外的需求可能會導致網際網路連線能力基礎結構、 路由最佳化及特殊直接連線的投資。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-119">These additional requirements may lead to investments in internet connectivity infrastructure, routing optimization, and specialized direct connectivity.</span></span>

<span data-ttu-id="e3ee1-120">若要協助您評估您的網路一些資源：</span><span class="sxs-lookup"><span data-stu-id="e3ee1-120">Some resources to help you assess your network:</span></span>

- <span data-ttu-id="e3ee1-121">如需 Office 365 網路功能概念資訊，請參閱[Office 365 網路連線能力概觀](office-365-networking-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-121">See [Office 365 network connectivity overview](office-365-networking-overview.md) for conceptual information about Office 365 networking.</span></span>
- <span data-ttu-id="e3ee1-122">請參閱[Office 365 網路連線原則](https://aka.ms/o365networkingprinciples)來了解安全地管理 Office 365 流量，並取得獲得最佳效能的連線能力原則。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-122">See [Office 365 Network Connectivity Principles](https://aka.ms/o365networkingprinciples) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span>
- <span data-ttu-id="e3ee1-123">註冊的[Microsoft FastTrack](https://www.microsoft.com/fasttrack)引導式協助 Office 365 的規劃、 設計及部署。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-123">Sign up for [Microsoft FastTrack](https://www.microsoft.com/fasttrack) for guided assistance with Office 365 planning, design and deployment.</span></span> 
- <span data-ttu-id="e3ee1-124">請參閱[Office 365 網路上架工具](assessing-network-connectivity.md#the-office-365-network-onboarding-tool)下一節，以執行基本的連線測試可提供網路連線能力增強功能，可以指定的使用者的位置與 Office 365 之間進行的特定指導。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-124">See the [Office 365 Network Onboarding tool](assessing-network-connectivity.md#the-office-365-network-onboarding-tool) section below to run basic connectivity tests that provide specific guidance about networking connectivity improvements that can be made between a given user location and Office 365.</span></span>

> [!NOTE]
> <span data-ttu-id="e3ee1-125">Microsoft 授權，才能使用 ExpressRoute for Office 365。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-125">Microsoft authorization is required to use ExpressRoute for Office 365.</span></span> <span data-ttu-id="e3ee1-126">Microsoft 會檢閱每個客戶要求，並僅授權 ExpressRoute for Office 365 流量，當客戶的法規需求所要求的直接連線。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-126">Microsoft reviews every customer request and only authorizes ExpressRoute for Office 365 usage when a customer's regulatory requirement mandates direct connectivity.</span></span> <span data-ttu-id="e3ee1-127">如果您有這類需求，請提供規定您解讀表示直接連線需要在[ExpressRoute for Office 365 要求表單](https://aka.ms/O365ERReview)中，若要開始 Microsoft 檢閱其文字摘錄與網頁連結。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-127">If you have such requirements, please provide the text excerpt and web link to the regulation which you interpret to mean that direct connectivity is required in the [ExpressRoute for Office 365 Request Form](https://aka.ms/O365ERReview) to begin a Microsoft review.</span></span> <span data-ttu-id="e3ee1-128">未經授權嘗試建立 Office 365 路由篩選器的訂用帳戶會收到[錯誤訊息](https://support.microsoft.com/kb/3181709)。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-128">Unauthorized subscriptions trying to create route filters for Office 365 will receive an [error message](https://support.microsoft.com/kb/3181709).</span></span>
  
<span data-ttu-id="e3ee1-129">規劃您的 Office 365 的網路評估時需要考量重點：</span><span class="sxs-lookup"><span data-stu-id="e3ee1-129">Key points to consider when planning your network assessment for Office 365:</span></span>
  
- <span data-ttu-id="e3ee1-130">Office 365 是安全、 可靠、 高效能執行的服務，透過公用的網際網路。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-130">Office 365 is a secure, reliable, high performance service that runs over the public internet.</span></span> <span data-ttu-id="e3ee1-131">我們繼續投入以增強服務的下列層面。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-131">We continue to invest to enhance these aspects of the service.</span></span> <span data-ttu-id="e3ee1-132">所有 Office 365 服務都可透過網際網路連線能力。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-132">All Office 365 services are available via internet connectivity.</span></span>

- <span data-ttu-id="e3ee1-133">我們會不斷最佳化的核心的 Office 365 的各個層面，例如可用性、 全域達到，與效能的網際網路連線。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-133">We are continually optimizing core aspects of Office 365 such as availability, global reach, and performance for internet based connectivity.</span></span> <span data-ttu-id="e3ee1-134">例如，有許多 Office 365 服務利用網際網路對向 edge 節點的延伸集。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-134">For example, many Office 365 services leverage an expanding set of internet facing edge nodes.</span></span> <span data-ttu-id="e3ee1-135">此 edge 網路提供最佳的近似值和即將透過網際網路連線的效能。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-135">This edge network offers the best proximity and performance to connections coming over the internet.</span></span>

- <span data-ttu-id="e3ee1-136">考慮使用 Office 365 任何包含服務例如 Teams 或 Skype 商務 Online voice、 視訊或會議功能，客戶應完成端對端網路評估，並符合使用[Microsoft FastTrack](https://www.microsoft.com/fasttrack)的連線能力需求。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-136">When considering using Office 365 for any of the included services such as Teams or Skype for Business Online voice, video, or meeting capabilities, customers should complete an end to end network assessment and meet connectivity requirements using [Microsoft FastTrack](https://www.microsoft.com/fasttrack).</span></span>

<span data-ttu-id="e3ee1-137">如果您正在評估 Office 365，並不確定要開始使用您的網路評估或已找到網路設計挑戰，您必須取得協助若要克服，請使用您的 Microsoft 客戶團隊。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-137">If you're evaluating Office 365 and aren't sure where to begin with your network assessment or have found network design challenges that you need assistance to overcome, please work with your Microsoft account team.</span></span>

## <a name="the-office-365-network-onboarding-tool"></a><span data-ttu-id="e3ee1-138">Office 365 網路上架工具</span><span class="sxs-lookup"><span data-stu-id="e3ee1-138">The Office 365 Network Onboarding tool</span></span>

<span data-ttu-id="e3ee1-139">[Office 365 網路上架工具](https://aka.ms/netonboard)是概念證明 (POC) 網路評定工具執行基本的連線測試對您的 Office 365 租用戶，並讓特定網路設計建議，Office 365 的最佳效能。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-139">The [Office 365 Network Onboarding tool](https://aka.ms/netonboard) is a proof of concept (POC) network assessment tool that runs basic connectivity tests against your Office 365 tenant and makes specific network design recommendations for optimal Office 365 performance.</span></span> <span data-ttu-id="e3ee1-140">此工具會醒目提示一般大型企業網路周邊的設計選擇也就是有用的網際網路網站瀏覽]，但影響大型的 SaaS 應用程式，例如 Office 365 的效能。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-140">The tool highlights common large enterprise network perimeter design choices which are useful for Internet web browsing but impact the performance of large SaaS applications such as Office 365.</span></span>

<span data-ttu-id="e3ee1-141">網路上架工具會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="e3ee1-141">The Network Onboarding tool does the following:</span></span>

- <span data-ttu-id="e3ee1-142">偵測到您的位置，或者您可以指定要測試的位置</span><span class="sxs-lookup"><span data-stu-id="e3ee1-142">Detects your location, or you can specify a location to test</span></span>
- <span data-ttu-id="e3ee1-143">檢查您的網路輸出的位置</span><span class="sxs-lookup"><span data-stu-id="e3ee1-143">Checks the location of your network egress</span></span>
- <span data-ttu-id="e3ee1-144">測試最接近的 Office 365 服務前哨的網路路徑</span><span class="sxs-lookup"><span data-stu-id="e3ee1-144">Tests the network path to the nearest Office 365 service front door</span></span>
- <span data-ttu-id="e3ee1-145">提供進階的測試使用可下載的 Windows 10 應用程式能夠讓相關 proxy 伺服器、 防火牆和 DNS 周邊網路設計建議。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-145">Provides advanced tests using a downloadable Windows 10 application that makes perimeter network design recommendations related to proxy servers, firewalls, and DNS.</span></span> <span data-ttu-id="e3ee1-146">此工具也執行效能測試 skype 商務 Online、 Microsoft Teams、 SharePoint Online 和 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-146">The tool also runs performance tests for Skype for Business Online, Microsoft Teams, SharePoint Online and Exchange Online.</span></span>

<span data-ttu-id="e3ee1-147">此工具有兩個元件： 瀏覽器型的使用者介面，收集基本連線資訊和可下載的 Windows 10 應用程式，就會執行進階的測試並傳回額外的評估資料。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-147">The tool has two components: a browser-based UI that collects basic connectivity information, and a downloadable Windows 10 application that runs advanced tests and returns additional assessment data.</span></span>

<span data-ttu-id="e3ee1-148">瀏覽器型的工具會顯示下列資訊：</span><span class="sxs-lookup"><span data-stu-id="e3ee1-148">The browser-based tool displays the following information:</span></span>

- <span data-ttu-id="e3ee1-149">結果和影響] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="e3ee1-149">Results and impact tab</span></span>
  - <span data-ttu-id="e3ee1-150">在地圖上的使用中的服務的前哨位置</span><span class="sxs-lookup"><span data-stu-id="e3ee1-150">The location on a map of the in-use service front door</span></span>
  - <span data-ttu-id="e3ee1-151">在地圖上的其他服務前方門會提供最佳的連線能力的位置</span><span class="sxs-lookup"><span data-stu-id="e3ee1-151">The location on a map of other service front doors that would provide optimal connectivity</span></span>
  - <span data-ttu-id="e3ee1-152">相較於其他靠近您的 Office 365 客戶的相關效能</span><span class="sxs-lookup"><span data-stu-id="e3ee1-152">Relative performance compared to other Office 365 customers near you</span></span>
- <span data-ttu-id="e3ee1-153">詳細資料與方案] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="e3ee1-153">Details and solutions tab</span></span>
  - <span data-ttu-id="e3ee1-154">縣/市以及國家/地區的使用者位置</span><span class="sxs-lookup"><span data-stu-id="e3ee1-154">User location by city and country</span></span>
  - <span data-ttu-id="e3ee1-155">縣/市、 狀態及國家/地區的網路輸出位置</span><span class="sxs-lookup"><span data-stu-id="e3ee1-155">Network egress location by city, state and country</span></span>
  - <span data-ttu-id="e3ee1-156">使用者網路輸出距離</span><span class="sxs-lookup"><span data-stu-id="e3ee1-156">User to network egress distance</span></span>
  - <span data-ttu-id="e3ee1-157">Office 365 Exchange Online 服務的前哨位置</span><span class="sxs-lookup"><span data-stu-id="e3ee1-157">Office 365 Exchange Online service front door location</span></span>
  - <span data-ttu-id="e3ee1-158">最佳的 Office 365 Exchange Online 服務 front door(s) 使用者位置</span><span class="sxs-lookup"><span data-stu-id="e3ee1-158">Optimal Office 365 Exchange Online service front door(s) for user location</span></span>
  - <span data-ttu-id="e3ee1-159">在您地鐵] 區域中具有較佳效能的客戶</span><span class="sxs-lookup"><span data-stu-id="e3ee1-159">Customers in your metro area with better performance</span></span>

<span data-ttu-id="e3ee1-160">進階測試可下載應用程式提供下列的額外資訊：</span><span class="sxs-lookup"><span data-stu-id="e3ee1-160">The Advanced Tests downloadable application provides the following additional information:</span></span>

- <span data-ttu-id="e3ee1-161">詳細資料和解決方案] 索引標籤 （附加）</span><span class="sxs-lookup"><span data-stu-id="e3ee1-161">Details and solutions tab (appended)</span></span>
  - <span data-ttu-id="e3ee1-162">使用者的預設閘道</span><span class="sxs-lookup"><span data-stu-id="e3ee1-162">User's default gateway</span></span>
  - <span data-ttu-id="e3ee1-163">用戶端 DNS 伺服器</span><span class="sxs-lookup"><span data-stu-id="e3ee1-163">Client DNS Server</span></span>
  - <span data-ttu-id="e3ee1-164">用戶端 DNS 遞迴解析程式</span><span class="sxs-lookup"><span data-stu-id="e3ee1-164">Client DNS Recursive Resolver</span></span>
  - <span data-ttu-id="e3ee1-165">Exchange Online DNS 伺服器</span><span class="sxs-lookup"><span data-stu-id="e3ee1-165">Exchange Online DNS server</span></span>
  - <span data-ttu-id="e3ee1-166">SharePoint Online 的 DNS 伺服器</span><span class="sxs-lookup"><span data-stu-id="e3ee1-166">SharePoint Online DNS server</span></span>
  - <span data-ttu-id="e3ee1-167">Proxy 伺服器識別碼</span><span class="sxs-lookup"><span data-stu-id="e3ee1-167">Proxy server identification</span></span>
  - <span data-ttu-id="e3ee1-168">媒體連線檢查</span><span class="sxs-lookup"><span data-stu-id="e3ee1-168">Media connectivity check</span></span>
  - <span data-ttu-id="e3ee1-169">媒體品質封包遺失</span><span class="sxs-lookup"><span data-stu-id="e3ee1-169">Media quality packet loss</span></span>
  - <span data-ttu-id="e3ee1-170">媒體品質延遲</span><span class="sxs-lookup"><span data-stu-id="e3ee1-170">Media quality latency</span></span>
  - <span data-ttu-id="e3ee1-171">媒體品質抖動</span><span class="sxs-lookup"><span data-stu-id="e3ee1-171">Media quality jitter</span></span>
  - <span data-ttu-id="e3ee1-172">媒體品質封包重新排列</span><span class="sxs-lookup"><span data-stu-id="e3ee1-172">Media quality packet reorder</span></span>
- <span data-ttu-id="e3ee1-173">多個特定功能的端點的連線測試</span><span class="sxs-lookup"><span data-stu-id="e3ee1-173">Connectivity tests to multiple feature-specific endpoints</span></span>
- <span data-ttu-id="e3ee1-174">包含 tracert 及延遲的 Exchange Online、 SharePoint Online 和 microsoft Teams 服務資料的網路路徑診斷</span><span class="sxs-lookup"><span data-stu-id="e3ee1-174">Network path diagnostics that include tracert and latency data for the Exchange Online, SharePoint Online and Teams services</span></span>

<span data-ttu-id="e3ee1-175">您可以了解 Office 365 網路上架工具，並提供意見反應在[更新 Office 365 網路上架工具 POC 新網路設計建議](https://techcommunity.microsoft.com/t5/Office-365-Networking/Updated-Office-365-Network-Onboarding-Tool-POC-with-new-network/m-p/711130#M130)部落格文章。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-175">You can read about the Office 365 Network Onboarding tool and provide feedback at the [Updated Office 365 Network Onboarding Tool POC with new network design recommendations](https://techcommunity.microsoft.com/t5/Office-365-Networking/Updated-Office-365-Network-Onboarding-Tool-POC-with-new-network/m-p/711130#M130) blog post.</span></span> <span data-ttu-id="e3ee1-176">這項工具的未來更新和其他 Office 365 網路更新相關資訊會張貼到[Office 365 網路](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)的部落格。</span><span class="sxs-lookup"><span data-stu-id="e3ee1-176">Information about future updates to this tool and other Office 365 networking updates will be posted to the [Office 365 Networking](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking) blog.</span></span>
  
<span data-ttu-id="e3ee1-177">以下是您可以使用返回下列短連結： [ https://aka.ms/o365networkconnectivity。](https://aka.ms/o365networkconnectivity)</span><span class="sxs-lookup"><span data-stu-id="e3ee1-177">Here's a short link you can use to come back: [https://aka.ms/o365networkconnectivity.](https://aka.ms/o365networkconnectivity)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e3ee1-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3ee1-178">See also</span></span>

[<span data-ttu-id="e3ee1-179">Office 365 網路連線概觀</span><span class="sxs-lookup"><span data-stu-id="e3ee1-179">Office 365 Network Connectivity Overview</span></span>](office-365-networking-overview.md)

[<span data-ttu-id="e3ee1-180">Office 365 網路連線原則</span><span class="sxs-lookup"><span data-stu-id="e3ee1-180">Office 365 Network Connectivity Principles</span></span>](https://aka.ms/o365networkingprinciples)

[<span data-ttu-id="e3ee1-181">管理 Office 365 端點</span><span class="sxs-lookup"><span data-stu-id="e3ee1-181">Managing Office 365 endpoints</span></span>](managing-office-365-endpoints.md)

[<span data-ttu-id="e3ee1-182">Office 365 URL 與 IP 位址範圍</span><span class="sxs-lookup"><span data-stu-id="e3ee1-182">Office 365 URLs and IP address ranges</span></span>](urls-and-ip-address-ranges.md)

[<span data-ttu-id="e3ee1-183">Office 365 IP 位址和 URL Web 服務</span><span class="sxs-lookup"><span data-stu-id="e3ee1-183">Office 365 IP Address and URL Web service</span></span>](office-365-ip-web-service.md)

[<span data-ttu-id="e3ee1-184">Office 365 網路與效能調整</span><span class="sxs-lookup"><span data-stu-id="e3ee1-184">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)

[<span data-ttu-id="e3ee1-185">Microsoft 365 企業版概觀</span><span class="sxs-lookup"><span data-stu-id="e3ee1-185">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
