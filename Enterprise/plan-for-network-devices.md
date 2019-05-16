---
title: 連線到 Office 365 服務的網路裝置的計劃
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
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
ms.assetid: 073433ca-3511-4db9-b173-7a2edca57691
description: 摘要： 說明的網路容量、 WAN 加速器和負載平衡裝置用來連線到 Office 365 的考量。
ms.openlocfilehash: 6ff63232d4efe581ed4a6ba0a83730a5362ecff7
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069369"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a><span data-ttu-id="55f63-103">連線到 Office 365 服務的網路裝置的計劃</span><span class="sxs-lookup"><span data-stu-id="55f63-103">Plan for network devices that connect to Office 365 services</span></span>

 <span data-ttu-id="55f63-104">**摘要**： 說明的網路容量、 WAN 加速器和負載平衡裝置用來連線到 Office 365 的考量。</span><span class="sxs-lookup"><span data-stu-id="55f63-104">**Summary**: Describes considerations for network capacity, WAN accelerators, and load balancing devices that are used to connect to Office 365.</span></span>
  
<span data-ttu-id="55f63-105">某些網路硬體可能會有所限制所支援的並行工作階段數目。</span><span class="sxs-lookup"><span data-stu-id="55f63-105">Some network hardware may have limitations on the number of concurrent sessions that are supported.</span></span> <span data-ttu-id="55f63-106">針對具有超過 2000 位使用者的組織，建議他們監視其網路裝置，以確保它們能夠處理其他的 Office 365 服務流量。</span><span class="sxs-lookup"><span data-stu-id="55f63-106">For organizations having more than 2,000 users, we recommend that they monitor their network devices to ensure they are capable of handling the additional Office 365 service traffic.</span></span> <span data-ttu-id="55f63-107">簡易網路管理通訊協定 (SNMP) 監視軟體可協助您執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="55f63-107">Simple Network Management Protocol (SNMP) monitoring software can help you do this.</span></span>

||
|:-----|
| <span data-ttu-id="55f63-108">本文是[網路規劃和效能調整的 Office 365](https://aka.ms/tune)的一部分。</span><span class="sxs-lookup"><span data-stu-id="55f63-108">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

<span data-ttu-id="55f63-109">內部部署的外寄的網際網路 proxy 設定也會影響您的用戶端應用程式的 Office 365 服務的連線。</span><span class="sxs-lookup"><span data-stu-id="55f63-109">On-premises outgoing Internet proxy settings also affect connectivity to Office 365 services for your client applications.</span></span> <span data-ttu-id="55f63-110">您也必須設定網路 proxy 裝置以允許 Microsoft 雲端服務 Url 和應用程式的連線。</span><span class="sxs-lookup"><span data-stu-id="55f63-110">You must also configure your network proxy devices to allow connections for Microsoft cloud services URLs and applications.</span></span> <span data-ttu-id="55f63-111">每個組織是不同。</span><span class="sxs-lookup"><span data-stu-id="55f63-111">Every organization is different.</span></span> <span data-ttu-id="55f63-112">若要取得了解 Microsoft 如何管理這項程序和頻寬量我們佈建，[讀取案例研究](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365)。</span><span class="sxs-lookup"><span data-stu-id="55f63-112">To get an idea for how Microsoft manages this process and the amount of bandwidth we provision, [read the case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).</span></span>
  
<span data-ttu-id="55f63-113">下列的 Skype for Business 說明文章有需 Skype for Business 設定的詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="55f63-113">The following Skype for Business Help articles have more information about Skype for Business settings:</span></span>
  
- [<span data-ttu-id="55f63-114">疑難排解商務用 Skype 系統管理員的商務 Online 登入錯誤</span><span class="sxs-lookup"><span data-stu-id="55f63-114">Troubleshooting Skype for Business Online sign-in errors for administrators</span></span>](https://docs.microsoft.com/skypeforbusiness/set-up-skype-for-business-online/troubleshooting-sign-in-errors-for-admins)

- [<span data-ttu-id="55f63-115">您無法連線至商務用 Skype 或某些功能無法運作，因為內部部署防火牆封鎖連線</span><span class="sxs-lookup"><span data-stu-id="55f63-115">You cannot connect to Skype for Business, or certain features do not work, because an on-premises firewall blocks the connection</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> <span data-ttu-id="55f63-116">許多這些設定都是特定的商務用 Skype，網路設定的一般指導方針是適用於所有 Office 365 服務。</span><span class="sxs-lookup"><span data-stu-id="55f63-116">While many of these settings are Skype for Business-specific, the general guidance on network configuration is useful for all Office 365 services.</span></span>
  
## <a name="determining-network-capacity"></a><span data-ttu-id="55f63-117">判斷網路容量</span><span class="sxs-lookup"><span data-stu-id="55f63-117">Determining Network Capacity</span></span>

<span data-ttu-id="55f63-118">每一個連接存在的網路裝置有其容量限制。</span><span class="sxs-lookup"><span data-stu-id="55f63-118">Every network device that exists on a connection has its capacity limit.</span></span> <span data-ttu-id="55f63-119">這些裝置包括用戶端和伺服器網路介面卡、 路由器、 交換器及 interconnect 它們的中樞。</span><span class="sxs-lookup"><span data-stu-id="55f63-119">These devices include the client and server network adapters, routers, switches, and hubs that interconnect them.</span></span> <span data-ttu-id="55f63-120">適當的網路容量表示沒有任何一個它們飽和。</span><span class="sxs-lookup"><span data-stu-id="55f63-120">Adequate network capacity means that none of them are saturated.</span></span> <span data-ttu-id="55f63-121">監控網路活動是以協助確保所有的網路裝置上實際負載有小於其最大的容量。</span><span class="sxs-lookup"><span data-stu-id="55f63-121">Monitoring network activity is essential to help ensure that the actual loads on all network devices are less than their maximum capacity.</span></span> <span data-ttu-id="55f63-122">網路容量影響 proxy 裝置的效能。</span><span class="sxs-lookup"><span data-stu-id="55f63-122">Network capacity affects proxy device performance.</span></span>
  
<span data-ttu-id="55f63-123">在大部分情況下，網際網路連線的頻寬設定預設流量的限制。</span><span class="sxs-lookup"><span data-stu-id="55f63-123">In most situations, the Internet connection bandwidth sets the limit for the amount of traffic.</span></span> <span data-ttu-id="55f63-124">在尖峰流量時間的弱式效能可能因過度使用的 [網際網路] 連結。</span><span class="sxs-lookup"><span data-stu-id="55f63-124">Weak performance during peak traffic hours is probably caused by excessive use of the Internet link.</span></span> <span data-ttu-id="55f63-125">這種情況下也適用於 branch office 案例中，其中 branch office proxy 伺服器電腦會連線至 proxy 裝置的分支總部慢速廣域網路 (WAN) 連結。</span><span class="sxs-lookup"><span data-stu-id="55f63-125">This situation also applies to a branch office scenario, where branch office proxy server computers are connected to the proxy device at the branch's headquarters over a slow Wide Area Network (WAN) link.</span></span>
  
<span data-ttu-id="55f63-126">若要測試的網路容量，監視 proxy 網路介面的網路活動。</span><span class="sxs-lookup"><span data-stu-id="55f63-126">To test network capacity, monitor the network activity on the proxy network interface.</span></span> <span data-ttu-id="55f63-127">如果它的任何網路介面的最大頻寬超過 75%，請考慮增加的頻寬不足的網路基礎結構。</span><span class="sxs-lookup"><span data-stu-id="55f63-127">If it's more than 75 percent of the maximum bandwidth of any network interface, consider increasing the bandwidth of the network infrastructure that's inadequate.</span></span> <span data-ttu-id="55f63-128">或者，請考慮使用進階的功能，例如 HTTP 壓縮。</span><span class="sxs-lookup"><span data-stu-id="55f63-128">Or, consider using advanced features, such as HTTP compression.</span></span>
  
## <a name="wan-accelerators"></a><span data-ttu-id="55f63-129">WAN 加速器</span><span class="sxs-lookup"><span data-stu-id="55f63-129">WAN Accelerators</span></span>

<span data-ttu-id="55f63-130">如果您的組織使用廣域網路 (wan) 加速器 proxy 設備，可能會遇到問題，當您存取 Office 365 服務中。</span><span class="sxs-lookup"><span data-stu-id="55f63-130">If your organization uses wide area network (WAN) acceleration proxy appliances, you may encounter issues when you access the Office 365 services.</span></span> <span data-ttu-id="55f63-131">您可能需要最佳化您的網路裝置或裝置，以確保您的使用者在存取 Office 365 時，會有一致的體驗。</span><span class="sxs-lookup"><span data-stu-id="55f63-131">You may need to optimize your network device or devices to ensure that your users have a consistent experience when accessing Office 365.</span></span> <span data-ttu-id="55f63-132">例如，Office 365 服務加密某些 Office 365 內容和 TCP 標頭。</span><span class="sxs-lookup"><span data-stu-id="55f63-132">For example, Office 365 services encrypt some Office 365 content and the TCP header.</span></span> <span data-ttu-id="55f63-133">您的裝置可能無法處理這類的流量。</span><span class="sxs-lookup"><span data-stu-id="55f63-133">Your device may not be able to handle this kind of traffic.</span></span>
  
<span data-ttu-id="55f63-134">閱讀有關[使用 WAN 最佳化控制器或與 Office 365 流量/檢查裝置](https://support.microsoft.com/kb/2690045)我們支援陳述式。</span><span class="sxs-lookup"><span data-stu-id="55f63-134">Read our support statement about [Using WAN Optimization Controller or Traffic/Inspection devices with Office 365](https://support.microsoft.com/kb/2690045).</span></span>
  
## <a name="hardware-and-software-load-balancing-devices"></a><span data-ttu-id="55f63-135">硬體與軟體負載平衡裝置</span><span class="sxs-lookup"><span data-stu-id="55f63-135">Hardware and Software Load-balancing Devices</span></span>

<span data-ttu-id="55f63-136">您的組織需要使用硬體負載平衡器 (HLB) 或網路負載平衡 (NLB) 解決方案來散發要求至您的 Active Directory Federation Services (AD FS) 伺服器及/或您的 Exchange 混合式伺服器。</span><span class="sxs-lookup"><span data-stu-id="55f63-136">Your organization needs to use a hardware load balancer (HLB) or a Network Load Balancing (NLB) solution to distribute requests to your Active Directory Federation Services (AD FS) servers and/or your Exchange hybrid servers.</span></span> <span data-ttu-id="55f63-137">負載平衡裝置控制到內部部署伺服器的網路流量。</span><span class="sxs-lookup"><span data-stu-id="55f63-137">Load-balancing devices control the network traffic to the on-premises servers.</span></span> <span data-ttu-id="55f63-138">這些伺服器都很重要，以協助確保單一登入與 Exchange 混合式部署的可用性。</span><span class="sxs-lookup"><span data-stu-id="55f63-138">These servers are crucial in helping to ensure the availability of single sign-on and Exchange hybrid deployment.</span></span>
  
<span data-ttu-id="55f63-139">我們將提供內建於 Windows Server 軟體為基礎的 NLB 解決方案。</span><span class="sxs-lookup"><span data-stu-id="55f63-139">We provide a software-based NLB solution built into Windows Server.</span></span> <span data-ttu-id="55f63-140">Office 365 支援此解決方案，以達到負載平衡。</span><span class="sxs-lookup"><span data-stu-id="55f63-140">Office 365 supports this solution to achieve load balancing.</span></span>
  
## <a name="firewalls-and-proxies"></a><span data-ttu-id="55f63-141">防火牆和 proxy</span><span class="sxs-lookup"><span data-stu-id="55f63-141">Firewalls and proxies</span></span>

<span data-ttu-id="55f63-142">如需設定防火牆和 proxy 連線至 Office 365，請閱讀[管理 Office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)、 [Office 365 的網路連線](network-connectivity.md)性和[Office 365 端點常見問題集](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)若要深入了解裝置和電路選取範圍的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="55f63-142">For more details on configuring firewalls and proxies to connect to Office 365, read [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [Network connectivity to Office 365](network-connectivity.md), and [Office 365 endpoints FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) to learn more about devices and circuit selection.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="55f63-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55f63-143">See also</span></span>

[<span data-ttu-id="55f63-144">Office 365 服務的部署建議</span><span class="sxs-lookup"><span data-stu-id="55f63-144">Deployment advisors for Office 365 services</span></span>](deployment-advisors-for-office-365.md)
