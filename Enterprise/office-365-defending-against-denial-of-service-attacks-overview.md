---
title: 防禦 Microsoft 365 中的拒絕服務攻擊
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
description: 拒絕服務（DoS）攻擊的概覽。
ms.openlocfilehash: 2cbe5eb86402fd7b7888f39440a58935604c90eb
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998417"
---
# <a name="defend-against-denial-of-service-attacks-in-microsoft-365"></a><span data-ttu-id="04ec7-103">防禦 Microsoft 365 中的拒絕服務攻擊</span><span class="sxs-lookup"><span data-stu-id="04ec7-103">Defend Against Denial-of-Service Attacks in Microsoft 365</span></span>

## <a name="introduction"></a><span data-ttu-id="04ec7-104">簡介</span><span class="sxs-lookup"><span data-stu-id="04ec7-104">Introduction</span></span>

<span data-ttu-id="04ec7-105">Microsoft 為超過100個資料中心的全球雲端基礎結構中所主控的超過200雲端服務提供信賴的基礎結構。</span><span class="sxs-lookup"><span data-stu-id="04ec7-105">Microsoft delivers a trustworthy infrastructure for more than 200 cloud services hosted in a global cloud infrastructure of more than 100 datacenters.</span></span> <span data-ttu-id="04ec7-106">包括：</span><span class="sxs-lookup"><span data-stu-id="04ec7-106">These include:</span></span>

- <span data-ttu-id="04ec7-107">Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="04ec7-107">Microsoft Azure</span></span>
- <span data-ttu-id="04ec7-108">Microsoft Bing</span><span class="sxs-lookup"><span data-stu-id="04ec7-108">Microsoft Bing</span></span>
- <span data-ttu-id="04ec7-109">Microsoft Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="04ec7-109">Microsoft Dynamics 365</span></span>
- <span data-ttu-id="04ec7-110">Microsoft 365 和 Office 365</span><span class="sxs-lookup"><span data-stu-id="04ec7-110">Microsoft 365 and Office 365</span></span>
- <span data-ttu-id="04ec7-111">Microsoft OneDrive</span><span class="sxs-lookup"><span data-stu-id="04ec7-111">Microsoft OneDrive</span></span>
- <span data-ttu-id="04ec7-112">Skype</span><span class="sxs-lookup"><span data-stu-id="04ec7-112">Skype</span></span>
- <span data-ttu-id="04ec7-113">Xbox Live</span><span class="sxs-lookup"><span data-stu-id="04ec7-113">Xbox Live</span></span>

<span data-ttu-id="04ec7-114">作為具有大量 Internet 平臺的全球性組織，以及提供雲端服務的許多醒目 Internet 屬性，Microsoft 是駭客和其他惡意人員的大型常見目標。</span><span class="sxs-lookup"><span data-stu-id="04ec7-114">As a global organization with a significant Internet presence and many prominent Internet properties that provide cloud services, Microsoft is a large, common target for hackers and other malicious individuals.</span></span> <span data-ttu-id="04ec7-115">用戶端與 Microsoft 雲端之間的網路通訊層是最大的惡意攻擊目標之一。</span><span class="sxs-lookup"><span data-stu-id="04ec7-115">The network communication layer between clients and the Microsoft Cloud is one of the biggest targets of malicious attacks.</span></span> <span data-ttu-id="04ec7-116">實際上，Microsoft 會持續而且持久地以某種形式的網路 cyberattack 為基礎。</span><span class="sxs-lookup"><span data-stu-id="04ec7-116">In fact, Microsoft is continuously and persistently under some form of network-based cyberattack.</span></span> <span data-ttu-id="04ec7-117">根據此，Microsoft 會使用深層防禦安全性原則來保護其雲端服務和網路。</span><span class="sxs-lookup"><span data-stu-id="04ec7-117">In line with this, Microsoft uses defense-in-depth security principles to protect its cloud services and networks.</span></span> <span data-ttu-id="04ec7-118">若沒有防禦這些攻擊的可靠且持久的緩解系統，則 Microsoft 的雲端服務會離線且無法供客戶使用。</span><span class="sxs-lookup"><span data-stu-id="04ec7-118">Without reliable and persistent mitigation systems that defend against these attacks, Microsoft's cloud services would be offline and unavailable to customers.</span></span>

## <a name="definition-and-symptoms-of-denial-of-service-attacks"></a><span data-ttu-id="04ec7-119">拒絕服務攻擊的定義和徵兆</span><span class="sxs-lookup"><span data-stu-id="04ec7-119">Definition and Symptoms of Denial-of-Service Attacks</span></span>

<span data-ttu-id="04ec7-120">攻擊網路服務的其中一種方法，就是針對服務主機建立許多要求，讓網路和伺服器不堪重負，以拒絕對合法使用者的服務。</span><span class="sxs-lookup"><span data-stu-id="04ec7-120">One way to attack network services is to create many requests against service hosts to overwhelm the network and servers to deny service to legitimate users.</span></span> <span data-ttu-id="04ec7-121">這稱為「拒絕服務」（DoS）攻擊。</span><span class="sxs-lookup"><span data-stu-id="04ec7-121">This is referred to as a denial-of-service (DoS) attack.</span></span> <span data-ttu-id="04ec7-122">當多個主角、端點和/或向量執行攻擊時，會將其稱為「分散式阻斷服務」（DDoS）攻擊。</span><span class="sxs-lookup"><span data-stu-id="04ec7-122">When the attack is performed by multiple actors, endpoints, and/or vectors, it is referred to as a distributed denial-of-service (DDoS) attack.</span></span> <span data-ttu-id="04ec7-123">雖然這種方式不同，但 DoS 和 DDoS 攻擊通常是為了避免網際網路網站或服務無法正常運作，或暫時或無限的努力所組成。</span><span class="sxs-lookup"><span data-stu-id="04ec7-123">Although the means, motives, and targets vary, DoS and DDoS attacks generally consist of efforts to prevent an Internet site or service from functioning correctly or at all, either temporarily or indefinitely.</span></span>

<span data-ttu-id="04ec7-124">[美國電腦緊急就緒小組](https://www.us-cert.gov/)（US CERT）定義要包含的 DoS 攻擊的徵兆：</span><span class="sxs-lookup"><span data-stu-id="04ec7-124">The [United States Computer Emergency Readiness Team](https://www.us-cert.gov/) (US-CERT) defines symptoms of DoS attacks to include:</span></span>

- <span data-ttu-id="04ec7-125">網路效能緩慢（開啟檔案或存取網際網路網站時）</span><span class="sxs-lookup"><span data-stu-id="04ec7-125">Unusually slow network performance (when opening files or accessing Internet sites)</span></span>
- <span data-ttu-id="04ec7-126">網站不可用</span><span class="sxs-lookup"><span data-stu-id="04ec7-126">Unavailability of a Web site</span></span>
- <span data-ttu-id="04ec7-127">無法存取網站</span><span class="sxs-lookup"><span data-stu-id="04ec7-127">Inability to access a Web site</span></span>
- <span data-ttu-id="04ec7-128">收到的垃圾郵件大幅增加</span><span class="sxs-lookup"><span data-stu-id="04ec7-128">Dramatic increase in received spam</span></span>
- <span data-ttu-id="04ec7-129">斷開無線或有線網際網路連線</span><span class="sxs-lookup"><span data-stu-id="04ec7-129">Disconnection of a wireless or wired Internet connection</span></span>
- <span data-ttu-id="04ec7-130">長期失去存取網頁或任何網際網路服務的許可權</span><span class="sxs-lookup"><span data-stu-id="04ec7-130">Long-term loss of access to the Web or any Internet services</span></span>

## <a name="related-topics"></a><span data-ttu-id="04ec7-131">相關主題</span><span class="sxs-lookup"><span data-stu-id="04ec7-131">Related Topics</span></span>

- [<span data-ttu-id="04ec7-132">防禦阻斷服務攻擊的核心原則</span><span class="sxs-lookup"><span data-stu-id="04ec7-132">Core Principles of Defense Against Denial-of-Service Attacks</span></span>](office-365-core-principles-of-defense-against-dos-attacks.md)
- [<span data-ttu-id="04ec7-133">Microsoft 的拒絕服務防禦策略</span><span class="sxs-lookup"><span data-stu-id="04ec7-133">Microsoft's Denial-of-Service Defense Strategy</span></span>](office-365-microsoft-dos-defense-strategy.md)
- [<span data-ttu-id="04ec7-134">防禦拒絕服務攻擊的 Microsoft 雲端服務</span><span class="sxs-lookup"><span data-stu-id="04ec7-134">Defending Microsoft Cloud Services Against Denial-of-Service Attacks</span></span>](office-365-defending-cloud-services-against-dos-attacks.md)
