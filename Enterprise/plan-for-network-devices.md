---
title: 連線到 Office 365 服務的網路裝置的計劃
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
ms.audience: ITPro
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
description: 摘要：說明連線到 Office 365 時所用之網路容量、WAN 加速器和負載平衡裝置的注意事項。
ms.openlocfilehash: 023eb3f5ed4d81d1d49d18c69ef8c81032fd5851
ms.sourcegitcommit: 317c2753be2aedb60698e94606ba59b63c962328
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "25933120"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a><span data-ttu-id="cb25b-103">連線到 Office 365 服務的網路裝置的計劃</span><span class="sxs-lookup"><span data-stu-id="cb25b-103">Plan for network devices that connect to Office 365 services</span></span>

 <span data-ttu-id="cb25b-104">**摘要**：說明連線到 Office 365 時所用之網路容量、WAN 加速器和負載平衡裝置的注意事項。</span><span class="sxs-lookup"><span data-stu-id="cb25b-104">**Summary**: Describes considerations for network capacity, WAN accelerators, and load balancing devices that are used to connect to Office 365.</span></span>
  
<span data-ttu-id="cb25b-p101">某些網路硬體可能會有限制同時支援的工作階段的數目而定。對於擁有超過 2000 位使用者的組織而言，我們建議他們監視網路裝置以確保它們能夠處理的其他 Office 365 服務流量。簡易網路管理通訊協定 (SNMP) 監視軟體可協助您達成此目的。</span><span class="sxs-lookup"><span data-stu-id="cb25b-p101">Some network hardware may have limitations on the number of concurrent sessions that are supported. For organizations having more than 2,000 users, we recommend that they monitor their network devices to ensure they are capable of handling the additional Office 365 service traffic. Simple Network Management Protocol (SNMP) monitoring software can help you do this.</span></span>

||
|:-----|
| <span data-ttu-id="cb25b-108">本文是[網路規劃和 Office 365 的效能調整](https://aka.ms/tune)的一部分。</span><span class="sxs-lookup"><span data-stu-id="cb25b-108">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

<span data-ttu-id="cb25b-p102">內部傳出網際網路 proxy 設定也會影響連線到 Office 365 服務的用戶端應用程式。您也必須設定網路 proxy 裝置，允許 Microsoft 雲端服務 Url 和應用程式的連線。每個組織的不同。若要取得 Microsoft 管理此程序及頻寬量的方式粗略我們佈建、[讀取案例研究](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365)。</span><span class="sxs-lookup"><span data-stu-id="cb25b-p102">On-premises outgoing Internet proxy settings also affect connectivity to Office 365 services for your client applications. You must also configure your network proxy devices to allow connections for Microsoft cloud services URLs and applications. Every organization is different. To get an idea for how Microsoft manages this process and the amount of bandwidth we provision, [read the case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).</span></span>
  
<span data-ttu-id="cb25b-113">商務說明文章的下列 Skype 具備商務設定 Skype 的詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="cb25b-113">The following Skype for Business Help articles have more information about Skype for Business settings:</span></span>
  
- [<span data-ttu-id="cb25b-114">疑難排解商務 Online 登入錯誤 Skype 系統管理員</span><span class="sxs-lookup"><span data-stu-id="cb25b-114">Troubleshooting Skype for Business Online sign-in errors for administrators</span></span>](https://docs.microsoft.com/skypeforbusiness/set-up-skype-for-business-online/troubleshooting-sign-in-errors-for-admins)

- [<span data-ttu-id="cb25b-115">您無法連線至 Skype for Business，或某些功能無法運作，因為在內部部署防火牆封鎖連線</span><span class="sxs-lookup"><span data-stu-id="cb25b-115">You cannot connect to Skype for Business, or certain features do not work, because an on-premises firewall blocks the connection</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> <span data-ttu-id="cb25b-116">雖然這些設定的許多商務特有的 Skype，網路設定的一般指導的適用於所有的 Office 365 服務。</span><span class="sxs-lookup"><span data-stu-id="cb25b-116">While many of these settings are Skype for Business-specific, the general guidance on network configuration is useful for all Office 365 services.</span></span>
  
## <a name="determining-network-capacity"></a><span data-ttu-id="cb25b-117">判斷網路容量</span><span class="sxs-lookup"><span data-stu-id="cb25b-117">Determining Network Capacity</span></span>

<span data-ttu-id="cb25b-p103">連線上存在的每一個網路裝置都有自己的容量限制。這些裝置包括用戶端與伺服器，以及將其互連的網路介面卡、路由器、交換器和集線器。適當的網路容量是指以上裝置都尚未飽和。監視網路活動是確保所有網路裝置的實際負載低於其最高容量的必要工作。網路容量會影響 Proxy 裝置的效能。</span><span class="sxs-lookup"><span data-stu-id="cb25b-p103">Every network device that exists on a connection has its capacity limit. These devices include the client and server network adapters, routers, switches, and hubs that interconnect them. Adequate network capacity means that none of them are saturated. Monitoring network activity is essential to help ensure that the actual loads on all network devices are less than their maximum capacity. Network capacity affects proxy device performance.</span></span>
  
<span data-ttu-id="cb25b-p104">在大多數情況下，網際網路連線的頻寬設定預設流量限制。弱式離峰流量的效能可能造成過度使用的 [網際網路] 連結。Branch office proxy 伺服器電腦連線到 proxy 裝置在該分支 headquarters 透過慢速廣域網路 (WAN) 連結其中 branch office 案例也適用於此情況。</span><span class="sxs-lookup"><span data-stu-id="cb25b-p104">In most situations, the Internet connection bandwidth sets the limit for the amount of traffic. Weak performance during peak traffic hours is probably caused by excessive use of the Internet link. This situation also applies to a branch office scenario, where branch office proxy server computers are connected to the proxy device at the branch's headquarters over a slow Wide Area Network (WAN) link.</span></span>
  
<span data-ttu-id="cb25b-p105">若要測試的網路容量，監視上 proxy 網路介面的網路活動。如果是多個 75%的任何網路介面的最大頻寬，請考慮增加不足的網路基礎結構的頻寬。或者，請考慮使用進階的功能，例如 HTTP 壓縮。</span><span class="sxs-lookup"><span data-stu-id="cb25b-p105">To test network capacity, monitor the network activity on the proxy network interface. If it's more than 75 percent of the maximum bandwidth of any network interface, consider increasing the bandwidth of the network infrastructure that's inadequate. Or, consider using advanced features, such as HTTP compression.</span></span>
  
## <a name="wan-accelerators"></a><span data-ttu-id="cb25b-129">廣域網路 (WAN) 加速器</span><span class="sxs-lookup"><span data-stu-id="cb25b-129">WAN Accelerators</span></span>

<span data-ttu-id="cb25b-p106">如果貴組織使用廣域網路 (wan) 加速 proxy 設備、 存取 Office 365 服務時可能會遇到問題。您可能需要最佳化您的網路裝置或裝置能夠確定您的使用者存取 Office 365 時有一致的體驗。例如，Office 365 服務加密某些 Office 365 內容和 TCP 標頭。您的裝置可能無法處理這種流量。</span><span class="sxs-lookup"><span data-stu-id="cb25b-p106">If your organization uses wide area network (WAN) acceleration proxy appliances, you may encounter issues when you access the Office 365 services. You may need to optimize your network device or devices to ensure that your users have a consistent experience when accessing Office 365. For example, Office 365 services encrypt some Office 365 content and the TCP header. Your device may not be able to handle this kind of traffic.</span></span>
  
<span data-ttu-id="cb25b-134">閱讀有關[使用 WAN 的最佳化控制器或流量/檢查裝置搭配 Office 365](https://support.microsoft.com/kb/2690045)我們支援陳述式。</span><span class="sxs-lookup"><span data-stu-id="cb25b-134">Read our support statement about [Using WAN Optimization Controller or Traffic/Inspection devices with Office 365](https://support.microsoft.com/kb/2690045).</span></span>
  
## <a name="hardware-and-software-load-balancing-devices"></a><span data-ttu-id="cb25b-135">硬體和軟體負載平衡裝置</span><span class="sxs-lookup"><span data-stu-id="cb25b-135">Hardware and Software Load-balancing Devices</span></span>

<span data-ttu-id="cb25b-p107">您的組織需要使用硬體負載平衡器 (HLB) 或網路負載平衡 (NLB) 解決方案，以將要求發佈至 Active Directory Federation Services (AD FS) 伺服器和/或 Exchange 混合伺服器。負載平衡裝置會控制前往內部部署伺服器的網路流量。這些伺服器對於確保單一登入和 Exchange 混合部署的可用性很重要。</span><span class="sxs-lookup"><span data-stu-id="cb25b-p107">Your organization needs to use a hardware load balancer (HLB) or a Network Load Balancing (NLB) solution to distribute requests to your Active Directory Federation Services (AD FS) servers and/or your Exchange hybrid servers. Load-balancing devices control the network traffic to the on-premises servers. These servers are crucial in helping to ensure the availability of single sign-on and Exchange hybrid deployment.</span></span>
  
<span data-ttu-id="cb25b-p108">我們提供內建於 Windows Server 軟體為基礎的 NLB 解決方案。Office 365 支援此解決方案以達到負載平衡。</span><span class="sxs-lookup"><span data-stu-id="cb25b-p108">We provide a software-based NLB solution built into Windows Server. Office 365 supports this solution to achieve load balancing.</span></span>
  
## <a name="firewalls-and-proxies"></a><span data-ttu-id="cb25b-141">防火牆及 proxy</span><span class="sxs-lookup"><span data-stu-id="cb25b-141">Firewalls and proxies</span></span>

<span data-ttu-id="cb25b-142">如需設定防火牆及 proxy 連線至 Office 365，請閱讀[管理 Office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)、[網路連線至 Office 365](network-connectivity.md)和[Office 365 端點常見問題集](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)若要深入了解裝置和電路選取範圍的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="cb25b-142">For more details on configuring firewalls and proxies to connect to Office 365, read [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [Network connectivity to Office 365](network-connectivity.md), and [Office 365 endpoints FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) to learn more about devices and circuit selection.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="cb25b-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb25b-143">See also</span></span>

[<span data-ttu-id="cb25b-144">Office 365 服務的部署建議</span><span class="sxs-lookup"><span data-stu-id="cb25b-144">Deployment advisors for Office 365 services</span></span>](deployment-advisors-for-office-365.md)
