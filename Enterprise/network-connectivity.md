---
title: Office 365 的網路連線能力
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/01/2018
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
ms.openlocfilehash: 4510cb073c0fde64abc4ee796a55d7ef32662f8c
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069869"
---
# <a name="network-connectivity-to-office-365"></a><span data-ttu-id="4be08-104">Office 365 的網路連線能力</span><span class="sxs-lookup"><span data-stu-id="4be08-104">Network connectivity to Office 365</span></span>

<span data-ttu-id="4be08-105">Office 365 被為了讓使得全球客戶服務使用的網際網路連線的連線。</span><span class="sxs-lookup"><span data-stu-id="4be08-105">Office 365 is designed to enable customers all over the world to connect to the service using an internet connection.</span></span> <span data-ttu-id="4be08-106">隨著服務發展，安全性、 效能和可靠性的 Office 365 已獲得改善根據上使用網際網路來建立連線至服務的客戶。</span><span class="sxs-lookup"><span data-stu-id="4be08-106">As the service evolves, the security, performance, and reliability of Office 365 are improved based on customers using the internet to establish a connection to the service.</span></span>
  
<span data-ttu-id="4be08-107">規劃使用 Office 365 的客戶應該評估其現有和預測的網際網路連線能力需求作為部署專案的一部分。</span><span class="sxs-lookup"><span data-stu-id="4be08-107">Customers planning to use Office 365 should assess their existing and forecasted internet connectivity needs as a part of the deployment project.</span></span> <span data-ttu-id="4be08-108">對於企業類別部署可靠並適當地調整大小的網際網路連線能力屬於重要耗用 Office 365 的功能與案例。</span><span class="sxs-lookup"><span data-stu-id="4be08-108">For enterprise class deployments reliable and appropriately sized internet connectivity is a critical part of consuming Office 365 features and scenarios.</span></span>
  
<span data-ttu-id="4be08-109">網路評估可以執行由許多不同的人員或組織根據您的大小和喜好設定。</span><span class="sxs-lookup"><span data-stu-id="4be08-109">Network evaluations can be performed by many different people and organizations depending on your size and preferences.</span></span> <span data-ttu-id="4be08-110">評估網路範圍也可以視其中您正在閱讀在您的部署程序而異。</span><span class="sxs-lookup"><span data-stu-id="4be08-110">The network scope of the assessment can also vary depending on where you're at in your deployment process.</span></span> <span data-ttu-id="4be08-111">若要可協助您開始的花費執行網路評估更深入了解，我們已產生的網路評估指南，協助您了解您可用的選項。</span><span class="sxs-lookup"><span data-stu-id="4be08-111">To help you get a better understanding of what it takes to perform a network assessment, we've produced a network assessment guide to help you understand the options available to you.</span></span> <span data-ttu-id="4be08-112">此評定會決定哪些步驟和資源需要新增至部署專案，使您能夠成功地採用 Office 365。</span><span class="sxs-lookup"><span data-stu-id="4be08-112">This assessment will determine what steps and resources need to be added to the deployment project to enable you to successfully adopt Office 365.</span></span>
  
<span data-ttu-id="4be08-113">完整網路評估，像是[Skype 操作架構](https://www.skypeoperationsframework.com/)中所述會提供給網路實作細節以及設計挑戰可能的解決方案。</span><span class="sxs-lookup"><span data-stu-id="4be08-113">A comprehensive network assessment, like those prescribed in the [Skype Operations Framework](https://www.skypeoperationsframework.com/) will provide possible solutions to networking design challenges along with implementation details.</span></span> <span data-ttu-id="4be08-114">大部分的網路評估會指出對 Office 365 的網路連線可以容納與[次要的設定] 或 [設計變更](https://aka.ms/manageo365endpoints)現有的網路和網際網路輸出基礎結構。</span><span class="sxs-lookup"><span data-stu-id="4be08-114">Most network assessments will indicate network connectivity to Office 365 can be accommodated with [minor configuration or design changes](https://aka.ms/manageo365endpoints) to the existing network and internet egress infrastructure.</span></span>

<span data-ttu-id="4be08-115">某些評估會指出對 Office 365 的網路連線時，需要在 [網路元件的額外投資。</span><span class="sxs-lookup"><span data-stu-id="4be08-115">Some assessments will indicate network connectivity to Office 365 will require additional investments in networking components.</span></span> <span data-ttu-id="4be08-116">WAN 頻寬或最佳化的路由基礎結構，以支援網際網路連線到 Office 365 中的例如投資。</span><span class="sxs-lookup"><span data-stu-id="4be08-116">For example, investments in WAN bandwidth or optimized routing infrastructure to support internet connectivity to Office 365.</span></span> <span data-ttu-id="4be08-117">有時會評估會指出對 Office 365 的網路連線受到法規或效能需求，例如[Skype for Business Online 媒體品質](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)的案例。</span><span class="sxs-lookup"><span data-stu-id="4be08-117">Occasionally an assessment will indicate network connectivity to Office 365 is influenced by regulation or performance requirements for scenarios such as [Skype for Business Online media quality](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).</span></span> <span data-ttu-id="4be08-118">這些額外的需求可能會導致網際網路連線能力基礎結構、 路由最佳化及特殊直接連線的投資。</span><span class="sxs-lookup"><span data-stu-id="4be08-118">These additional requirements may lead to investments in internet connectivity infrastructure, routing optimization, and specialized direct connectivity.</span></span>
  
> [!NOTE]
> <span data-ttu-id="4be08-119">Microsoft 授權，才能使用 ExpressRoute for Office 365。</span><span class="sxs-lookup"><span data-stu-id="4be08-119">Microsoft authorization is required to use ExpressRoute for Office 365.</span></span> <span data-ttu-id="4be08-120">Microsoft 會檢閱每個客戶要求，並僅授權 ExpressRoute for Office 365 流量，當客戶的法規需求所要求的直接連線。</span><span class="sxs-lookup"><span data-stu-id="4be08-120">Microsoft reviews every customer request and only authorizes ExpressRoute for Office 365 usage when a customer's regulatory requirement mandates direct connectivity.</span></span> <span data-ttu-id="4be08-121">如果您有這類需求，請提供規定您解讀表示直接連線需要在[ExpressRoute for Office 365 要求表單](https://aka.ms/O365ERReview)中，若要開始 Microsoft 檢閱其文字摘錄與網頁連結。</span><span class="sxs-lookup"><span data-stu-id="4be08-121">If you have such requirements, please provide the text excerpt and web link to the regulation which you interpret to mean that direct connectivity is required in the [ExpressRoute for Office 365 Request Form](https://aka.ms/O365ERReview) to begin a Microsoft review.</span></span> <span data-ttu-id="4be08-122">未經授權嘗試建立 Office 365 路由篩選器的訂用帳戶會收到[錯誤訊息](https://support.microsoft.com/kb/3181709)。</span><span class="sxs-lookup"><span data-stu-id="4be08-122">Unauthorized subscriptions trying to create route filters for Office 365 will receive an [error message](https://support.microsoft.com/kb/3181709).</span></span>
  
<span data-ttu-id="4be08-123">規劃您的 Office 365 的網路評估時需要考量重點：</span><span class="sxs-lookup"><span data-stu-id="4be08-123">Key points to consider when planning your network assessment for Office 365:</span></span>
  
- <span data-ttu-id="4be08-124">Office 365 是安全、 可靠、 高效能執行的服務，透過公用的網際網路。</span><span class="sxs-lookup"><span data-stu-id="4be08-124">Office 365 is a secure, reliable, high performance service that runs over the public internet.</span></span> <span data-ttu-id="4be08-125">我們繼續投入以增強服務的下列層面。</span><span class="sxs-lookup"><span data-stu-id="4be08-125">We continue to invest to enhance these aspects of the service.</span></span> <span data-ttu-id="4be08-126">所有 Office 365 服務都可透過網際網路連線能力。</span><span class="sxs-lookup"><span data-stu-id="4be08-126">All Office 365 services are available via internet connectivity.</span></span>

- <span data-ttu-id="4be08-127">我們會不斷最佳化的核心的 Office 365 的各個層面，例如可用性、 全域達到，與效能的網際網路連線。</span><span class="sxs-lookup"><span data-stu-id="4be08-127">We are continually optimizing core aspects of Office 365 such as availability, global reach, and performance for internet based connectivity.</span></span> <span data-ttu-id="4be08-128">例如，有許多 Office 365 服務利用網際網路對向 edge 節點的延伸集。</span><span class="sxs-lookup"><span data-stu-id="4be08-128">For example, many Office 365 services leverage an expanding set of internet facing edge nodes.</span></span> <span data-ttu-id="4be08-129">此 edge 網路提供最佳的近似值和即將透過網際網路連線的效能。</span><span class="sxs-lookup"><span data-stu-id="4be08-129">This edge network offers the best proximity and performance to connections coming over the internet.</span></span>

- <span data-ttu-id="4be08-130">考慮使用 Office 365 任何包含服務例如 Skype 商務 Online voice、 視訊或會議功能，客戶必須完成端對端網路評估，並符合使用我們 Skype Operations Framework 的需求。</span><span class="sxs-lookup"><span data-stu-id="4be08-130">When considering using Office 365 for any of the included services such as Skype for Business Online voice, video, or meeting capabilities, customers must complete an end to end network assessment and meet requirements using our Skype Operations Framework.</span></span> <span data-ttu-id="4be08-131">這些客戶會有數個選項可以符合雲端連線能力，包括 ExpressRoute 的特定需求。</span><span class="sxs-lookup"><span data-stu-id="4be08-131">These customers will have several options to meet specific requirements for cloud connectivity, including ExpressRoute.</span></span>

<span data-ttu-id="4be08-132">看看 Microsoft 的案例研究[的 Microsoft Office 365 的最佳化網路效能](https://msdn.microsoft.com/en-us/library/mt450488.aspx)。</span><span class="sxs-lookup"><span data-stu-id="4be08-132">Have a look at Microsoft's case study [Optimizing network performance for Microsoft Office 365](https://msdn.microsoft.com/en-us/library/mt450488.aspx).</span></span> <span data-ttu-id="4be08-133">如果您正在評估 Office 365，並不確定要開始使用您的網路評估或已找到網路設計挑戰，您必須取得協助若要克服，請使用您的 Microsoft 客戶團隊。</span><span class="sxs-lookup"><span data-stu-id="4be08-133">If you're evaluating Office 365 and aren't sure where to begin with your network assessment or have found network design challenges that you need assistance to overcome, please work with your Microsoft account team.</span></span>
  
<span data-ttu-id="4be08-134">此外，請閱讀[Office 365 網路連線原則](https://aka.ms/o365networkingprinciples)來了解安全地管理 Office 365 流量，並取得獲得最佳效能的連線能力原則。</span><span class="sxs-lookup"><span data-stu-id="4be08-134">Also, read [Office 365 Network Connectivity Principles](https://aka.ms/o365networkingprinciples) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span> <span data-ttu-id="4be08-135">本文可協助您了解安全地最佳化 Office 365 網路連線的最新的指引。</span><span class="sxs-lookup"><span data-stu-id="4be08-135">This article will help you understand the most recent guidance for securely optimizing Office 365 network connectivity.</span></span>
  
<span data-ttu-id="4be08-136">以下是您可以使用返回下列短連結： [ https://aka.ms/o365networkconnectivity。](https://aka.ms/o365networkconnectivity)</span><span class="sxs-lookup"><span data-stu-id="4be08-136">Here's a short link you can use to come back: [https://aka.ms/o365networkconnectivity.](https://aka.ms/o365networkconnectivity)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4be08-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4be08-137">See also</span></span>

[<span data-ttu-id="4be08-138">管理 Office 365 端點</span><span class="sxs-lookup"><span data-stu-id="4be08-138">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
<span data-ttu-id="4be08-139">[Office 365 端點常見問題集](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) (機器翻譯)</span><span class="sxs-lookup"><span data-stu-id="4be08-139">[Office 365 endpoints FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)</span></span>
  
[<span data-ttu-id="4be08-140">Office 365 網路與效能調整</span><span class="sxs-lookup"><span data-stu-id="4be08-140">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)
  
[<span data-ttu-id="4be08-141">Azure ExpressRoute for Office 365</span><span class="sxs-lookup"><span data-stu-id="4be08-141">Azure ExpressRoute for Office 365</span></span>](azure-expressroute.md)
  
[<span data-ttu-id="4be08-142">使用 ExpressRoute for Office 365 進行路由傳送</span><span class="sxs-lookup"><span data-stu-id="4be08-142">Routing with ExpressRoute for Office 365</span></span>](routing-with-expressroute.md)
  
[<span data-ttu-id="4be08-143">使用 ExpressRoute for Office 365 進行網路規劃</span><span class="sxs-lookup"><span data-stu-id="4be08-143">Network planning with ExpressRoute for Office 365</span></span>](network-planning-with-expressroute.md)
  
[<span data-ttu-id="4be08-144">使用 BGP 社群中 ExpressRoute for Office 365 案例 （預覽）</span><span class="sxs-lookup"><span data-stu-id="4be08-144">Using BGP communities in ExpressRoute for Office 365 scenarios (preview)</span></span>](bgp-communities-in-expressroute.md)
  
<span data-ttu-id="4be08-145">[商務用 Skype Online 中的媒體品質和網路連線效能](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917) (英文)</span><span class="sxs-lookup"><span data-stu-id="4be08-145">[Media Quality and Network Connectivity Performance in Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)</span></span>
  
<span data-ttu-id="4be08-146">[Office 365 URL 與 IP 位址範圍](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) (英文)</span><span class="sxs-lookup"><span data-stu-id="4be08-146">[Office 365 URLs and IP address ranges](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)</span></span>
  
[<span data-ttu-id="4be08-147">Office 365 網路連線原則</span><span class="sxs-lookup"><span data-stu-id="4be08-147">Office 365 Network Connectivity Principles</span></span>](https://aka.ms/o365networkingprinciples)
