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
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 073433ca-3511-4db9-b173-7a2edca57691
description: 摘要：說明用來連線至 Office 365 之網路容量、WAN 加速器及負載平衡裝置的考慮。
ms.openlocfilehash: 9776611aa64f8783a22252a2c4182e63bda1093a
ms.sourcegitcommit: bb5b7bd241f58491198de2d74dbdce76f7bb8f62
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "44419371"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a><span data-ttu-id="f86c3-103">連線到 Office 365 服務的網路裝置的計劃</span><span class="sxs-lookup"><span data-stu-id="f86c3-103">Plan for network devices that connect to Office 365 services</span></span>

<span data-ttu-id="f86c3-104">*本文適用於 Office 365 企業版和 Microsoft 365 企業版。*</span><span class="sxs-lookup"><span data-stu-id="f86c3-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>
  
<span data-ttu-id="f86c3-105">**摘要**：說明用來連線至 Office 365 之網路容量、WAN 加速器及負載平衡裝置的考慮。</span><span class="sxs-lookup"><span data-stu-id="f86c3-105">**Summary**: Describes considerations for network capacity, WAN accelerators, and load balancing devices that are used to connect to Office 365.</span></span>

<span data-ttu-id="f86c3-106">有些網路硬體可能會限制支援的並行會話數目。</span><span class="sxs-lookup"><span data-stu-id="f86c3-106">Some network hardware may have limitations on the number of concurrent sessions that are supported.</span></span> <span data-ttu-id="f86c3-107">對於擁有超過2000使用者的組織，建議他們監視其網路裝置，以確保它們能夠處理其他 Office 365 服務流量。</span><span class="sxs-lookup"><span data-stu-id="f86c3-107">For organizations having more than 2,000 users, we recommend that they monitor their network devices to ensure they are capable of handling the additional Office 365 service traffic.</span></span> <span data-ttu-id="f86c3-108">簡易網路管理通訊協定（SNMP）監視軟體可協助您執行這項作業。</span><span class="sxs-lookup"><span data-stu-id="f86c3-108">Simple Network Management Protocol (SNMP) monitoring software can help you do this.</span></span>

||
|:-----|
| <span data-ttu-id="f86c3-109">本文是 [Office 365 的網路規劃與效能調整](https://aka.ms/tune)的一部分。</span><span class="sxs-lookup"><span data-stu-id="f86c3-109">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

<span data-ttu-id="f86c3-110">內部部署外寄網際網路 proxy 設定也會影響用戶端應用程式的 Office 365 服務連線能力。</span><span class="sxs-lookup"><span data-stu-id="f86c3-110">On-premises outgoing Internet proxy settings also affect connectivity to Office 365 services for your client applications.</span></span> <span data-ttu-id="f86c3-111">您也必須設定網路 proxy 裝置，以允許 Microsoft cloud services URLs 和應用程式的連線。</span><span class="sxs-lookup"><span data-stu-id="f86c3-111">You must also configure your network proxy devices to allow connections for Microsoft cloud services URLs and applications.</span></span> <span data-ttu-id="f86c3-112">每個組織都不同。</span><span class="sxs-lookup"><span data-stu-id="f86c3-112">Every organization is different.</span></span> <span data-ttu-id="f86c3-113">若要瞭解 Microsoft 如何管理此程式以及我們提供的頻寬量，請[閱讀案例分析](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365)。</span><span class="sxs-lookup"><span data-stu-id="f86c3-113">To get an idea for how Microsoft manages this process and the amount of bandwidth we provision, [read the case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).</span></span>
  
<span data-ttu-id="f86c3-114">下列商務用 Skype 說明文章具有商務用 Skype 設定的詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="f86c3-114">The following Skype for Business Help articles have more information about Skype for Business settings:</span></span>
  
- [<span data-ttu-id="f86c3-115">疑難排解系統管理員的商務用 Skype Online 登入錯誤</span><span class="sxs-lookup"><span data-stu-id="f86c3-115">Troubleshooting Skype for Business Online sign-in errors for administrators</span></span>](https://docs.microsoft.com/skypeforbusiness/set-up-skype-for-business-online/troubleshooting-sign-in-errors-for-admins)

- [<span data-ttu-id="f86c3-116">您無法連線至商務用 Skype，或某些功能無法運作，因為內部部署防火牆會封鎖連線</span><span class="sxs-lookup"><span data-stu-id="f86c3-116">You cannot connect to Skype for Business, or certain features do not work, because an on-premises firewall blocks the connection</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> <span data-ttu-id="f86c3-117">雖然這些設定中有許多是商務用 Skype，但網路設定的一般指導也適用于所有 Office 365 服務。</span><span class="sxs-lookup"><span data-stu-id="f86c3-117">While many of these settings are Skype for Business-specific, the general guidance on network configuration is useful for all Office 365 services.</span></span>
  
## <a name="determining-network-capacity"></a><span data-ttu-id="f86c3-118">決定網路容量</span><span class="sxs-lookup"><span data-stu-id="f86c3-118">Determining Network Capacity</span></span>

<span data-ttu-id="f86c3-119">連接上的每個網路裝置都有其容量限制。</span><span class="sxs-lookup"><span data-stu-id="f86c3-119">Every network device that exists on a connection has its capacity limit.</span></span> <span data-ttu-id="f86c3-120">這些裝置包含用戶端和伺服器網路介面卡、路由器、交換器，以及與其互連的中樞。</span><span class="sxs-lookup"><span data-stu-id="f86c3-120">These devices include the client and server network adapters, routers, switches, and hubs that interconnect them.</span></span> <span data-ttu-id="f86c3-121">足夠的網路容量表示沒有任何飽和。</span><span class="sxs-lookup"><span data-stu-id="f86c3-121">Adequate network capacity means that none of them are saturated.</span></span> <span data-ttu-id="f86c3-122">監視網路活動非常重要，以協助確保所有網路裝置上的實際負載小於其容量上限。</span><span class="sxs-lookup"><span data-stu-id="f86c3-122">Monitoring network activity is essential to help ensure that the actual loads on all network devices are less than their maximum capacity.</span></span> <span data-ttu-id="f86c3-123">網路容量會影響 proxy 裝置效能。</span><span class="sxs-lookup"><span data-stu-id="f86c3-123">Network capacity affects proxy device performance.</span></span>
  
<span data-ttu-id="f86c3-124">在大多數情況下，網際網路連線頻寬會設定流量的數量限制。</span><span class="sxs-lookup"><span data-stu-id="f86c3-124">In most situations, the Internet connection bandwidth sets the limit for the amount of traffic.</span></span> <span data-ttu-id="f86c3-125">峰值流量峰值的效能可能是由於過度使用網際網路連結所造成。</span><span class="sxs-lookup"><span data-stu-id="f86c3-125">Weak performance during peak traffic hours is probably caused by excessive use of the Internet link.</span></span> <span data-ttu-id="f86c3-126">這種情況也適用于分公司，其中分支 office proxy 伺服器電腦透過慢速廣域網路（WAN）連結連接至分支總部的 proxy 裝置。</span><span class="sxs-lookup"><span data-stu-id="f86c3-126">This situation also applies to a branch office scenario, where branch office proxy server computers are connected to the proxy device at the branch's headquarters over a slow Wide Area Network (WAN) link.</span></span>
  
<span data-ttu-id="f86c3-127">若要測試網路容量，請在 proxy 網路介面上監視網路活動。</span><span class="sxs-lookup"><span data-stu-id="f86c3-127">To test network capacity, monitor the network activity on the proxy network interface.</span></span> <span data-ttu-id="f86c3-128">如果是任何網路介面的最大頻寬超過75%，請考慮增加不充分之網路基礎結構的頻寬。</span><span class="sxs-lookup"><span data-stu-id="f86c3-128">If it's more than 75 percent of the maximum bandwidth of any network interface, consider increasing the bandwidth of the network infrastructure that's inadequate.</span></span> <span data-ttu-id="f86c3-129">或者，請考慮使用高級功能（例如 HTTP 壓縮）。</span><span class="sxs-lookup"><span data-stu-id="f86c3-129">Or, consider using advanced features, such as HTTP compression.</span></span>
  
## <a name="wan-accelerators"></a><span data-ttu-id="f86c3-130">WAN 加速器</span><span class="sxs-lookup"><span data-stu-id="f86c3-130">WAN Accelerators</span></span>

<span data-ttu-id="f86c3-131">如果您的組織使用廣域網路絡（WAN）加速度 proxy 裝置，當您存取 Office 365 服務時，可能會發生問題。</span><span class="sxs-lookup"><span data-stu-id="f86c3-131">If your organization uses wide area network (WAN) acceleration proxy appliances, you may encounter issues when you access the Office 365 services.</span></span> <span data-ttu-id="f86c3-132">您可能需要優化網路裝置或裝置，以確保您的使用者在存取 Office 365 時有一致的經驗。</span><span class="sxs-lookup"><span data-stu-id="f86c3-132">You may need to optimize your network device or devices to ensure that your users have a consistent experience when accessing Office 365.</span></span> <span data-ttu-id="f86c3-133">例如，Office 365 服務會加密某些 Office 365 內容和 TCP 標頭。</span><span class="sxs-lookup"><span data-stu-id="f86c3-133">For example, Office 365 services encrypt some Office 365 content and the TCP header.</span></span> <span data-ttu-id="f86c3-134">您的裝置可能無法處理這類流量。</span><span class="sxs-lookup"><span data-stu-id="f86c3-134">Your device may not be able to handle this kind of traffic.</span></span>
  
<span data-ttu-id="f86c3-135">如需[使用 WAN 優化控制器或流量/檢查裝置與 Office 365 的支援聲明，請](https://support.microsoft.com/kb/2690045)參閱。</span><span class="sxs-lookup"><span data-stu-id="f86c3-135">Read our support statement about [Using WAN Optimization Controller or Traffic/Inspection devices with Office 365](https://support.microsoft.com/kb/2690045).</span></span>
  
## <a name="hardware-and-software-load-balancing-devices"></a><span data-ttu-id="f86c3-136">硬體與軟體負載平衡裝置</span><span class="sxs-lookup"><span data-stu-id="f86c3-136">Hardware and Software Load-balancing Devices</span></span>

<span data-ttu-id="f86c3-137">您的組織必須使用硬體負載平衡器（HLB）或網路負載平衡（NLB）方案，將要求散佈至 Active Directory Federation Services （AD FS）伺服器和（或） Exchange 混合伺服器。</span><span class="sxs-lookup"><span data-stu-id="f86c3-137">Your organization needs to use a hardware load balancer (HLB) or a Network Load Balancing (NLB) solution to distribute requests to your Active Directory Federation Services (AD FS) servers and/or your Exchange hybrid servers.</span></span> <span data-ttu-id="f86c3-138">負載平衡裝置可控制內部部署伺服器的網路流量。</span><span class="sxs-lookup"><span data-stu-id="f86c3-138">Load-balancing devices control the network traffic to the on-premises servers.</span></span> <span data-ttu-id="f86c3-139">這些伺服器對於協助確保單一登入與 Exchange 混合式部署的可用性非常重要。</span><span class="sxs-lookup"><span data-stu-id="f86c3-139">These servers are crucial in helping to ensure the availability of single sign-on and Exchange hybrid deployment.</span></span>
  
<span data-ttu-id="f86c3-140">我們提供 Windows Server 內建的軟體型 NLB 解決方案。</span><span class="sxs-lookup"><span data-stu-id="f86c3-140">We provide a software-based NLB solution built into Windows Server.</span></span> <span data-ttu-id="f86c3-141">Office 365 支援此解決方案，以達到負載平衡。</span><span class="sxs-lookup"><span data-stu-id="f86c3-141">Office 365 supports this solution to achieve load balancing.</span></span>
  
## <a name="firewalls-and-proxies"></a><span data-ttu-id="f86c3-142">防火牆和代理</span><span class="sxs-lookup"><span data-stu-id="f86c3-142">Firewalls and proxies</span></span>

<span data-ttu-id="f86c3-143">如需設定防火牆和代理伺服器以連線至 Office 365 的詳細資訊，請參閱[管理 office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)、[評估 Office 365 網路](assessing-network-connectivity.md)連線，以及[office 365 端點常見問題](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)以深入瞭解裝置和電路選項。</span><span class="sxs-lookup"><span data-stu-id="f86c3-143">For more details on configuring firewalls and proxies to connect to Office 365, read [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [Assessing Office 365 network connectivity](assessing-network-connectivity.md), and [Office 365 endpoints FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) to learn more about devices and circuit selection.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f86c3-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f86c3-144">See also</span></span>

[<span data-ttu-id="f86c3-145">Office 365 服務的安裝指南</span><span class="sxs-lookup"><span data-stu-id="f86c3-145">Setup guides for Office 365 services</span></span>](setup-guides-for-office-365.md)

[<span data-ttu-id="f86c3-146">Microsoft 365 企業版概觀</span><span class="sxs-lookup"><span data-stu-id="f86c3-146">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
