---
title: 評估 Office 365 網路連線
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/5/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 64b420ef-0218-48f6-8a34-74bb27633b10
description: Office 365 被為了讓使得全球客戶服務使用的網際網路連線的連線。 隨著服務發展，安全性、 效能和可靠性的 Office 365 已獲得改善根據上使用網際網路來建立連線至服務的客戶。
ms.openlocfilehash: 3ea80ddccaf9fabbe158a10f0af1d35dbf3a9889
ms.sourcegitcommit: 0449c6f854c682719cac1bd0d086f2e3b20078b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "34724823"
---
# <a name="assessing-office-365-network-connectivity"></a><span data-ttu-id="9cb96-104">評估 Office 365 網路連線</span><span class="sxs-lookup"><span data-stu-id="9cb96-104">Assessing Office 365 network connectivity</span></span>

<span data-ttu-id="9cb96-105">Office 365 被為了讓使得全球客戶服務使用的網際網路連線的連線。</span><span class="sxs-lookup"><span data-stu-id="9cb96-105">Office 365 is designed to enable customers all over the world to connect to the service using an internet connection.</span></span> <span data-ttu-id="9cb96-106">隨著服務發展，安全性、 效能和可靠性的 Office 365 已獲得改善根據上使用網際網路來建立連線至服務的客戶。</span><span class="sxs-lookup"><span data-stu-id="9cb96-106">As the service evolves, the security, performance, and reliability of Office 365 are improved based on customers using the internet to establish a connection to the service.</span></span>
  
<span data-ttu-id="9cb96-107">規劃使用 Office 365 的客戶應該評估其現有和預測的網際網路連線能力需求作為部署專案的一部分。</span><span class="sxs-lookup"><span data-stu-id="9cb96-107">Customers planning to use Office 365 should assess their existing and forecasted internet connectivity needs as a part of the deployment project.</span></span> <span data-ttu-id="9cb96-108">對於企業類別部署可靠並適當地調整大小的網際網路連線能力屬於重要耗用 Office 365 的功能與案例。</span><span class="sxs-lookup"><span data-stu-id="9cb96-108">For enterprise class deployments reliable and appropriately sized internet connectivity is a critical part of consuming Office 365 features and scenarios.</span></span>
  
<span data-ttu-id="9cb96-109">網路評估可以執行由許多不同的人員或組織根據您的大小和喜好設定。</span><span class="sxs-lookup"><span data-stu-id="9cb96-109">Network evaluations can be performed by many different people and organizations depending on your size and preferences.</span></span> <span data-ttu-id="9cb96-110">評估網路範圍也可以視其中您正在閱讀在您的部署程序而異。</span><span class="sxs-lookup"><span data-stu-id="9cb96-110">The network scope of the assessment can also vary depending on where you're at in your deployment process.</span></span> <span data-ttu-id="9cb96-111">若要可協助您開始的花費執行網路評估更深入了解，我們已產生的網路評估指南，協助您了解您可用的選項。</span><span class="sxs-lookup"><span data-stu-id="9cb96-111">To help you get a better understanding of what it takes to perform a network assessment, we've produced a network assessment guide to help you understand the options available to you.</span></span> <span data-ttu-id="9cb96-112">此評定會決定哪些步驟和資源需要新增至部署專案，使您能夠成功地採用 Office 365。</span><span class="sxs-lookup"><span data-stu-id="9cb96-112">This assessment will determine what steps and resources need to be added to the deployment project to enable you to successfully adopt Office 365.</span></span>
  
<span data-ttu-id="9cb96-113">完整網路評估，像是[Skype 操作架構](https://www.skypeoperationsframework.com/)中所述會提供給網路實作細節以及設計挑戰可能的解決方案。</span><span class="sxs-lookup"><span data-stu-id="9cb96-113">A comprehensive network assessment, like those prescribed in the [Skype Operations Framework](https://www.skypeoperationsframework.com/) will provide possible solutions to networking design challenges along with implementation details.</span></span> <span data-ttu-id="9cb96-114">大部分的網路評估會指出對 Office 365 的網路連線可以容納與[次要的設定] 或 [設計變更](https://aka.ms/manageo365endpoints)現有的網路和網際網路輸出基礎結構。</span><span class="sxs-lookup"><span data-stu-id="9cb96-114">Most network assessments will indicate network connectivity to Office 365 can be accommodated with [minor configuration or design changes](https://aka.ms/manageo365endpoints) to the existing network and internet egress infrastructure.</span></span>

<span data-ttu-id="9cb96-115">某些評估會指出對 Office 365 的網路連線時，需要在 [網路元件的額外投資。</span><span class="sxs-lookup"><span data-stu-id="9cb96-115">Some assessments will indicate network connectivity to Office 365 will require additional investments in networking components.</span></span> <span data-ttu-id="9cb96-116">WAN 頻寬或最佳化的路由基礎結構，以支援網際網路連線到 Office 365 中的例如投資。</span><span class="sxs-lookup"><span data-stu-id="9cb96-116">For example, investments in WAN bandwidth or optimized routing infrastructure to support internet connectivity to Office 365.</span></span> <span data-ttu-id="9cb96-117">有時會評估會指出對 Office 365 的網路連線受到法規或效能需求，例如[Skype for Business Online 媒體品質](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)的案例。</span><span class="sxs-lookup"><span data-stu-id="9cb96-117">Occasionally an assessment will indicate network connectivity to Office 365 is influenced by regulation or performance requirements for scenarios such as [Skype for Business Online media quality](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).</span></span> <span data-ttu-id="9cb96-118">這些額外的需求可能會導致網際網路連線能力基礎結構、 路由最佳化及特殊直接連線的投資。</span><span class="sxs-lookup"><span data-stu-id="9cb96-118">These additional requirements may lead to investments in internet connectivity infrastructure, routing optimization, and specialized direct connectivity.</span></span>
  
> [!NOTE]
> <span data-ttu-id="9cb96-119">Microsoft 授權，才能使用 ExpressRoute for Office 365。</span><span class="sxs-lookup"><span data-stu-id="9cb96-119">Microsoft authorization is required to use ExpressRoute for Office 365.</span></span> <span data-ttu-id="9cb96-120">Microsoft 會檢閱每個客戶要求，並僅授權 ExpressRoute for Office 365 流量，當客戶的法規需求所要求的直接連線。</span><span class="sxs-lookup"><span data-stu-id="9cb96-120">Microsoft reviews every customer request and only authorizes ExpressRoute for Office 365 usage when a customer's regulatory requirement mandates direct connectivity.</span></span> <span data-ttu-id="9cb96-121">如果您有這類需求，請提供規定您解讀表示直接連線需要在[ExpressRoute for Office 365 要求表單](https://aka.ms/O365ERReview)中，若要開始 Microsoft 檢閱其文字摘錄與網頁連結。</span><span class="sxs-lookup"><span data-stu-id="9cb96-121">If you have such requirements, please provide the text excerpt and web link to the regulation which you interpret to mean that direct connectivity is required in the [ExpressRoute for Office 365 Request Form](https://aka.ms/O365ERReview) to begin a Microsoft review.</span></span> <span data-ttu-id="9cb96-122">未經授權嘗試建立 Office 365 路由篩選器的訂用帳戶會收到[錯誤訊息](https://support.microsoft.com/kb/3181709)。</span><span class="sxs-lookup"><span data-stu-id="9cb96-122">Unauthorized subscriptions trying to create route filters for Office 365 will receive an [error message](https://support.microsoft.com/kb/3181709).</span></span>
  
<span data-ttu-id="9cb96-123">規劃您的 Office 365 的網路評估時需要考量重點：</span><span class="sxs-lookup"><span data-stu-id="9cb96-123">Key points to consider when planning your network assessment for Office 365:</span></span>
  
- <span data-ttu-id="9cb96-124">Office 365 是安全、 可靠、 高效能執行的服務，透過公用的網際網路。</span><span class="sxs-lookup"><span data-stu-id="9cb96-124">Office 365 is a secure, reliable, high performance service that runs over the public internet.</span></span> <span data-ttu-id="9cb96-125">我們繼續投入以增強服務的下列層面。</span><span class="sxs-lookup"><span data-stu-id="9cb96-125">We continue to invest to enhance these aspects of the service.</span></span> <span data-ttu-id="9cb96-126">所有 Office 365 服務都可透過網際網路連線能力。</span><span class="sxs-lookup"><span data-stu-id="9cb96-126">All Office 365 services are available via internet connectivity.</span></span>

- <span data-ttu-id="9cb96-127">我們會不斷最佳化的核心的 Office 365 的各個層面，例如可用性、 全域達到，與效能的網際網路連線。</span><span class="sxs-lookup"><span data-stu-id="9cb96-127">We are continually optimizing core aspects of Office 365 such as availability, global reach, and performance for internet based connectivity.</span></span> <span data-ttu-id="9cb96-128">例如，有許多 Office 365 服務利用網際網路對向 edge 節點的延伸集。</span><span class="sxs-lookup"><span data-stu-id="9cb96-128">For example, many Office 365 services leverage an expanding set of internet facing edge nodes.</span></span> <span data-ttu-id="9cb96-129">此 edge 網路提供最佳的近似值和即將透過網際網路連線的效能。</span><span class="sxs-lookup"><span data-stu-id="9cb96-129">This edge network offers the best proximity and performance to connections coming over the internet.</span></span>

- <span data-ttu-id="9cb96-130">考慮使用 Office 365 任何包含服務例如 Skype 商務 Online voice、 視訊或會議功能，客戶必須完成端對端網路評估，並符合使用我們 Skype Operations Framework 的需求。</span><span class="sxs-lookup"><span data-stu-id="9cb96-130">When considering using Office 365 for any of the included services such as Skype for Business Online voice, video, or meeting capabilities, customers must complete an end to end network assessment and meet requirements using our Skype Operations Framework.</span></span> <span data-ttu-id="9cb96-131">這些客戶會有數個選項可以符合雲端連線能力，包括 ExpressRoute 的特定需求。</span><span class="sxs-lookup"><span data-stu-id="9cb96-131">These customers will have several options to meet specific requirements for cloud connectivity, including ExpressRoute.</span></span>

<span data-ttu-id="9cb96-132">看看 Microsoft 的案例研究[的 Microsoft Office 365 的最佳化網路效能](https://msdn.microsoft.com/en-us/library/mt450488.aspx)。</span><span class="sxs-lookup"><span data-stu-id="9cb96-132">Have a look at Microsoft's case study [Optimizing network performance for Microsoft Office 365](https://msdn.microsoft.com/en-us/library/mt450488.aspx).</span></span> <span data-ttu-id="9cb96-133">如果您正在評估 Office 365，並不確定要開始使用您的網路評估或已找到網路設計挑戰，您必須取得協助若要克服，請使用您的 Microsoft 客戶團隊。</span><span class="sxs-lookup"><span data-stu-id="9cb96-133">If you're evaluating Office 365 and aren't sure where to begin with your network assessment or have found network design challenges that you need assistance to overcome, please work with your Microsoft account team.</span></span>
  
<span data-ttu-id="9cb96-134">此外，請閱讀[Office 365 網路連線原則](https://aka.ms/o365networkingprinciples)來了解安全地管理 Office 365 流量，並取得獲得最佳效能的連線能力原則。</span><span class="sxs-lookup"><span data-stu-id="9cb96-134">Also, read [Office 365 Network Connectivity Principles](https://aka.ms/o365networkingprinciples) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span> <span data-ttu-id="9cb96-135">本文可協助您了解安全地最佳化 Office 365 網路連線的最新的指引。</span><span class="sxs-lookup"><span data-stu-id="9cb96-135">This article will help you understand the most recent guidance for securely optimizing Office 365 network connectivity.</span></span>

## <a name="the-office-365-network-onboarding-tool"></a><span data-ttu-id="9cb96-136">Office 365 網路上架工具</span><span class="sxs-lookup"><span data-stu-id="9cb96-136">The Office 365 Network Onboarding tool</span></span>

<span data-ttu-id="9cb96-137">您可以使用[Office 365 網路上架工具](https://aka.ms/netonboard)，新證明 (POC) 的概念工具，來執行基本的連線測試，提供可指定的使用者的位置與 Office 365 之間進行的網路連線能力增強功能的特定指導。</span><span class="sxs-lookup"><span data-stu-id="9cb96-137">You can use the [Office 365 Network Onboarding tool](https://aka.ms/netonboard), a new proof of concept (POC) tool, to run basic connectivity tests that provide specific guidance about networking connectivity improvements that can be made between a given user location and Office 365.</span></span>

<span data-ttu-id="9cb96-138">網路上架工具會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="9cb96-138">The Network Onboarding tool does the following:</span></span>

- <span data-ttu-id="9cb96-139">偵測到您的位置，或者您可以指定要測試的位置</span><span class="sxs-lookup"><span data-stu-id="9cb96-139">Detects your location, or you can specify a location to test</span></span>
- <span data-ttu-id="9cb96-140">檢查您的網路輸出的位置</span><span class="sxs-lookup"><span data-stu-id="9cb96-140">Checks the location of your network egress</span></span>
- <span data-ttu-id="9cb96-141">測試最接近的 Office 365 服務前哨的網路路徑</span><span class="sxs-lookup"><span data-stu-id="9cb96-141">Tests the network path to the nearest Office 365 service front door</span></span>

<span data-ttu-id="9cb96-142">此工具會顯示下列資訊：</span><span class="sxs-lookup"><span data-stu-id="9cb96-142">The tool displays the following information:</span></span>

- <span data-ttu-id="9cb96-143">結果和影響] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="9cb96-143">Results and impact tab</span></span>
  - <span data-ttu-id="9cb96-144">在地圖上的使用中的服務的前哨位置</span><span class="sxs-lookup"><span data-stu-id="9cb96-144">The location on a map of the in-use service front door</span></span>
  - <span data-ttu-id="9cb96-145">在地圖上的其他服務前方門會提供最佳的連線能力的位置</span><span class="sxs-lookup"><span data-stu-id="9cb96-145">The location on a map of other service front doors that would provide optimal connectivity</span></span>
  - <span data-ttu-id="9cb96-146">相較於其他靠近您的 Office 365 客戶的相關效能</span><span class="sxs-lookup"><span data-stu-id="9cb96-146">Relative performance compared to other Office 365 customers near you</span></span>
- <span data-ttu-id="9cb96-147">詳細資料與方案] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="9cb96-147">Details and solutions tab</span></span>
  - <span data-ttu-id="9cb96-148">縣/市以及國家/地區的使用者位置</span><span class="sxs-lookup"><span data-stu-id="9cb96-148">User location by city and country</span></span>
  - <span data-ttu-id="9cb96-149">縣/市、 狀態及國家/地區的網路輸出位置</span><span class="sxs-lookup"><span data-stu-id="9cb96-149">Network egress location by city, state and country</span></span>
  - <span data-ttu-id="9cb96-150">使用者網路輸出距離</span><span class="sxs-lookup"><span data-stu-id="9cb96-150">User to network egress distance</span></span>
  - <span data-ttu-id="9cb96-151">Office 365 Exchange Online 服務的前哨位置</span><span class="sxs-lookup"><span data-stu-id="9cb96-151">Office 365 Exchange Online service front door location</span></span>
  - <span data-ttu-id="9cb96-152">最佳的 Office 365 Exchange Online 服務 front door(s) 使用者位置</span><span class="sxs-lookup"><span data-stu-id="9cb96-152">Optimal Office 365 Exchange Online service front door(s) for user location</span></span>
  - <span data-ttu-id="9cb96-153">在您地鐵] 區域中具有較佳效能的客戶</span><span class="sxs-lookup"><span data-stu-id="9cb96-153">Customers in your metro area with better performance</span></span>

<span data-ttu-id="9cb96-154">您可以了解 Office 365 網路上架工具版本，並提供意見反應在[Office 365 網路效能工具 POC 版本](https://techcommunity.microsoft.com/t5/Office-365-Networking/Office-365-Network-Performance-tool-POC-release/m-p/319579#M102)部落格文章。</span><span class="sxs-lookup"><span data-stu-id="9cb96-154">You can read about the Office 365 Network Onboarding tool release and provide feedback at the [Office 365 Network Performance tool POC release](https://techcommunity.microsoft.com/t5/Office-365-Networking/Office-365-Network-Performance-tool-POC-release/m-p/319579#M102) blog post.</span></span> <span data-ttu-id="9cb96-155">這項工具的未來更新和其他 Office 365 網路更新相關資訊會張貼到[Office 365 網路](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)的部落格。</span><span class="sxs-lookup"><span data-stu-id="9cb96-155">Information about future updates to this tool and other Office 365 networking updates will be posted to the [Office 365 Networking](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking) blog.</span></span>
  
<span data-ttu-id="9cb96-156">以下是您可以使用返回下列短連結： [ https://aka.ms/o365networkconnectivity。](https://aka.ms/o365networkconnectivity)</span><span class="sxs-lookup"><span data-stu-id="9cb96-156">Here's a short link you can use to come back: [https://aka.ms/o365networkconnectivity.](https://aka.ms/o365networkconnectivity)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="9cb96-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9cb96-157">See also</span></span>

[<span data-ttu-id="9cb96-158">Office 365 網路連線能力概觀</span><span class="sxs-lookup"><span data-stu-id="9cb96-158">Office 365 Network Connectivity Overview</span></span>](office-365-networking-overview.md)

[<span data-ttu-id="9cb96-159">Office 365 網路連線原則</span><span class="sxs-lookup"><span data-stu-id="9cb96-159">Office 365 Network Connectivity Principles</span></span>](https://aka.ms/o365networkingprinciples)

[<span data-ttu-id="9cb96-160">管理 Office 365 端點</span><span class="sxs-lookup"><span data-stu-id="9cb96-160">Managing Office 365 endpoints</span></span>](managing-office-365-endpoints.md)

<span data-ttu-id="9cb96-161">[Office 365 URL 與 IP 位址範圍](urls-and-ip-address-ranges.md) (英文)</span><span class="sxs-lookup"><span data-stu-id="9cb96-161">[Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md)</span></span>

[<span data-ttu-id="9cb96-162">Office 365 IP 位址和 URL Web 服務</span><span class="sxs-lookup"><span data-stu-id="9cb96-162">Office 365 IP Address and URL Web service</span></span>](office-365-ip-web-service.md)

[<span data-ttu-id="9cb96-163">Office 365 網路與效能調整</span><span class="sxs-lookup"><span data-stu-id="9cb96-163">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)
