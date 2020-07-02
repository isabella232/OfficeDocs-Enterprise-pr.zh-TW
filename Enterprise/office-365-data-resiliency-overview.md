---
title: Microsoft 365 的資料恢復功能
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: 瞭解 Microsoft Microsoft 365 中的資料恢復能力。
ms.openlocfilehash: 368f1d56ef2b4f4c9677b53122e58453ff627335
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998467"
---
# <a name="data-resiliency-in-microsoft-365"></a><span data-ttu-id="f87d1-103">Microsoft 365 的資料恢復功能</span><span class="sxs-lookup"><span data-stu-id="f87d1-103">Data Resiliency in Microsoft 365</span></span>

## <a name="introduction"></a><span data-ttu-id="f87d1-104">簡介</span><span class="sxs-lookup"><span data-stu-id="f87d1-104">Introduction</span></span>

<span data-ttu-id="f87d1-105">考慮到雲端計算的複雜性質，Microsoft 很注意，如果發生問題，則不是這樣。</span><span class="sxs-lookup"><span data-stu-id="f87d1-105">Given the complex nature of cloud computing, Microsoft is mindful that it's not a case of if things will go wrong, but rather when.</span></span> <span data-ttu-id="f87d1-106">我們設計雲端服務，以最大化可靠性，並在發生錯誤時將負面影響降至最低。</span><span class="sxs-lookup"><span data-stu-id="f87d1-106">We design our cloud services to maximize reliability and minimize the negative effects on customers when things do go wrong.</span></span> <span data-ttu-id="f87d1-107">我們已超越信賴複雜實體基礎結構的傳統策略，而且我們已直接在雲端服務中建立冗余。</span><span class="sxs-lookup"><span data-stu-id="f87d1-107">We have moved beyond the traditional strategy of relying on complex physical infrastructure, and we have built redundancy directly into our cloud services.</span></span> <span data-ttu-id="f87d1-108">我們採用複雜的實體基礎結構和更多智慧軟體的組合，將資料恢復到我們的服務中，並為我們的客戶提供高可用性。</span><span class="sxs-lookup"><span data-stu-id="f87d1-108">We use a combination of less complex physical infrastructure and more intelligent software that builds data resiliency into our services and delivers high availability to our customers.</span></span> 

## <a name="resiliency-and-recoverability-are-built-in"></a><span data-ttu-id="f87d1-109">恢復功能和可恢復性是內建</span><span class="sxs-lookup"><span data-stu-id="f87d1-109">Resiliency and Recoverability Are Built-in</span></span> 

<span data-ttu-id="f87d1-110">以恢復性和復原的方式開始，假設基礎基礎結構和程式在某些情況下會失敗：硬體（基礎結構）將會失敗、人工會犯錯誤，軟體也會有錯誤。</span><span class="sxs-lookup"><span data-stu-id="f87d1-110">Building in resiliency and recovery starts with the assumption that the underlying infrastructure and processes will fail at some point: hardware (infrastructure) will fail, humans will make mistakes, and software will have bugs.</span></span> <span data-ttu-id="f87d1-111">雖然軟體發展人員不會考慮到雲端之前未考慮到這些事項，但在典型的 IT 實施中處理這些問題的方式，在雲端之前是非常不同的：</span><span class="sxs-lookup"><span data-stu-id="f87d1-111">While it would be incorrect to say that software developers were not thinking about these things before the cloud, how these issues were handled in a typical IT implementation was very different before the cloud:</span></span>

- <span data-ttu-id="f87d1-112">首先，硬體和基礎結構保護非常重要。</span><span class="sxs-lookup"><span data-stu-id="f87d1-112">First, hardware and infrastructure protections were significant.</span></span> <span data-ttu-id="f87d1-113">這意味著具有99.99% 可靠性的資料中心需要大量的電源和網路冗余，而且伺服器是以硬體型集群、雙電源、雙網路介面，以及類似的方式來執行。</span><span class="sxs-lookup"><span data-stu-id="f87d1-113">This meant having datacenters with 99.99% reliability required significant power and network redundancy, and servers were implemented with hardware-based clustering, dual power supplies, dual network interfaces, and the like.</span></span> 
- <span data-ttu-id="f87d1-114">其次，處理常式是極其重要的。</span><span class="sxs-lookup"><span data-stu-id="f87d1-114">Second, process was paramount.</span></span> <span data-ttu-id="f87d1-115">運作小組維護嚴格的程式、對 windows 的變更所採用的工作，而且經常會產生大量的專案管理工作負載。</span><span class="sxs-lookup"><span data-stu-id="f87d1-115">Operations teams maintained rigorous procedures, change windows were employed, and there was often significant project management overhead.</span></span> 
- <span data-ttu-id="f87d1-116">第三，部署是以 glacial 節奏進行。</span><span class="sxs-lookup"><span data-stu-id="f87d1-116">Third, deployment took place at a glacial pace.</span></span> <span data-ttu-id="f87d1-117">部署不含來源的程式碼表示要等候修補程式版本，主要版本版本則涉及硬體取代和大量的資本 outlay。</span><span class="sxs-lookup"><span data-stu-id="f87d1-117">Deploying code without owning the source meant waiting for patch releases, and major version releases involved hardware replacement and significant capital outlay.</span></span> <span data-ttu-id="f87d1-118">此外，修正問題的唯一方法是回復。</span><span class="sxs-lookup"><span data-stu-id="f87d1-118">Moreover, the only way to correct a problem was to roll back.</span></span> <span data-ttu-id="f87d1-119">因此，大部分的 IT 組織只會部署主要版本，以避免工作保持最新狀態。</span><span class="sxs-lookup"><span data-stu-id="f87d1-119">Thus, most IT organizations would deploy only major releases to avoid the work to keep up-to-date.</span></span> 
- <span data-ttu-id="f87d1-120">最後，已部署系統的規模，以及其 interconnectedness 的層級，都比現在更小。</span><span class="sxs-lookup"><span data-stu-id="f87d1-120">Finally, the scale of deployed systems, as well as the level of their interconnectedness was historically much smaller than it is now.</span></span> 

<span data-ttu-id="f87d1-121">目前，客戶預期來自 Microsoft 的連續創新，但不會降低品質，這是 Microsoft 的服務和軟體以恢復性和恢復為基礎而建立的原因之一。</span><span class="sxs-lookup"><span data-stu-id="f87d1-121">Today, customers expect continuous innovation from Microsoft without compromising quality, and this is one of the reasons why Microsoft's services and software are built with resiliency and recoverability in mind.</span></span> 

## <a name="microsoft-365-data-resiliency-principles"></a><span data-ttu-id="f87d1-122">Microsoft 365 資料恢復原則</span><span class="sxs-lookup"><span data-stu-id="f87d1-122">Microsoft 365 Data Resiliency Principles</span></span>

<span data-ttu-id="f87d1-123">恢復性指的是雲端架構服務可經受某些類型的失敗的能力，但在客戶的觀點上仍然能完全運作。</span><span class="sxs-lookup"><span data-stu-id="f87d1-123">Resiliency refers to the ability of a cloud-based service to withstand certain types of failures and yet remain fully-functional from the customers' perspective.</span></span> <span data-ttu-id="f87d1-124">資料恢復意味著不論 Microsoft 365 中發生的失敗為何，重要的客戶資料會保持不變且不會受到影響。</span><span class="sxs-lookup"><span data-stu-id="f87d1-124">Data resiliency means that no matter what failures occur within Microsoft 365, critical customer data remains intact and unaffected.</span></span> <span data-ttu-id="f87d1-125">為做到這一點，Microsoft 365 服務的設計是圍繞五個特定的恢復原則：</span><span class="sxs-lookup"><span data-stu-id="f87d1-125">To that end, Microsoft 365 services have been designed around five specific resiliency principles:</span></span>

- <span data-ttu-id="f87d1-126">有重要且非重要的資料。</span><span class="sxs-lookup"><span data-stu-id="f87d1-126">There is critical and non-critical data.</span></span> <span data-ttu-id="f87d1-127">非重要資料（例如，是否已讀取郵件）可以在少見的失敗案例中刪除。</span><span class="sxs-lookup"><span data-stu-id="f87d1-127">Non-critical data (for example, whether a message was read) can be dropped in rare failure scenarios.</span></span> <span data-ttu-id="f87d1-128">重要資料（例如，電子郵件訊息等客戶資料）應以極高成本進行保護。</span><span class="sxs-lookup"><span data-stu-id="f87d1-128">Critical data (for example, customer data such as email messages) should be protected at extreme cost.</span></span> <span data-ttu-id="f87d1-129">在設計目標中，傳遞的郵件訊息永遠很重要，也就是郵件已讀取的情況不重要。</span><span class="sxs-lookup"><span data-stu-id="f87d1-129">As a design goal, delivered mail messages are always critical, and things like whether a message has been read is non-critical.</span></span> 
- <span data-ttu-id="f87d1-130">客戶資料的複本必須分割成不同的容錯區域或盡可能多的容錯網域（例如，資料中心可透過單一認證（處理常式、伺服器或操作員）），以提供失敗隔離。</span><span class="sxs-lookup"><span data-stu-id="f87d1-130">Copies of customer data must be separated into different fault zones or as many fault domains as possible (e.g., datacenters, accessible by single credentials (process, server, or operator)) to provide failure isolation.</span></span> 
- <span data-ttu-id="f87d1-131">重要的客戶資料必須受到監視，以失敗任何原子性、一致性、隔離性、持續性（ACID）的部分。</span><span class="sxs-lookup"><span data-stu-id="f87d1-131">Critical customer data must be monitored for failing any part of Atomicity, Consistency, Isolation, Durability (ACID).</span></span> 
- <span data-ttu-id="f87d1-132">客戶資料必須受到保護，避免損毀。</span><span class="sxs-lookup"><span data-stu-id="f87d1-132">Customer data must be protected from corruption.</span></span> <span data-ttu-id="f87d1-133">必須主動掃描或監視、修復和恢復。</span><span class="sxs-lookup"><span data-stu-id="f87d1-133">It must be actively scanned or monitored, repairable, and recoverable.</span></span> 
- <span data-ttu-id="f87d1-134">客戶動作中大部分的資料遺失結果，讓客戶可以使用 GUI 自行進行復原，讓他們能夠還原意外刪除的專案。</span><span class="sxs-lookup"><span data-stu-id="f87d1-134">Most data loss results from customer actions, so allow customers to recover on their own using a GUI that enables them to restore accidentally deleted items.</span></span> 
 
<span data-ttu-id="f87d1-135">透過將我們的雲端服務組建至這些原則，並結合可靠的測試和驗證，Microsoft 365 可以符合和超過客戶的需求，同時可確保平臺的持續創新和改進。</span><span class="sxs-lookup"><span data-stu-id="f87d1-135">Through the building of our cloud services to these principles, coupled with robust testing and validation, Microsoft 365 is able to meet and exceed the requirements of customers while ensuring a platform for continuous innovation and improvement.</span></span> 

## <a name="related-links"></a><span data-ttu-id="f87d1-136">相關連結</span><span class="sxs-lookup"><span data-stu-id="f87d1-136">Related Links</span></span>

- [<span data-ttu-id="f87d1-137">處理資料損毀</span><span class="sxs-lookup"><span data-stu-id="f87d1-137">Dealing with Data Corruption</span></span>](office-365-dealing-with-data-corruption.md)
- [<span data-ttu-id="f87d1-138">惡意程式碼與勒索軟體防護</span><span class="sxs-lookup"><span data-stu-id="f87d1-138">Malware and Ransomware Protection</span></span>](office-365-malware-and-ransomware-protection.md)
- [<span data-ttu-id="f87d1-139">監視及自我修復</span><span class="sxs-lookup"><span data-stu-id="f87d1-139">Monitoring and Self-Healing</span></span>](office-365-monitoring-and-self-healing.md)
- [<span data-ttu-id="f87d1-140">Exchange 資料恢復功能</span><span class="sxs-lookup"><span data-stu-id="f87d1-140">Exchange Data Resiliency</span></span>](office-365-exchange-data-resiliency.md)