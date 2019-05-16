---
title: 易於存取的圖表-網路整合的 Microsoft Office 伺服器產品
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 89f564eb-95c3-4077-bb92-75bf71b51270
description: 本文是圖表的名為網路整合的 Microsoft Office Server 產品易於存取的文字版本。
ms.openlocfilehash: d63b3b581a03840676393657d6ed641e11046ef9
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068559"
---
# <a name="accessible-diagram---network-integration-of-microsoft-office-server-products"></a><span data-ttu-id="bef0e-103">易於存取的圖表-網路整合的 Microsoft Office 伺服器產品</span><span class="sxs-lookup"><span data-stu-id="bef0e-103">Accessible diagram - Network Integration of Microsoft Office Server Products</span></span>

<span data-ttu-id="bef0e-104">**摘要：** 本文是圖表的名為網路整合的 Microsoft Office Server 產品易於存取的文字版本。</span><span class="sxs-lookup"><span data-stu-id="bef0e-104">**Summary:** This article is an accessible text version of the diagram named Network Integration of Microsoft Office Server Products.</span></span>
  
<span data-ttu-id="bef0e-105">此海報提供網路環境，其中包含 Lync Server 2013、 SharePoint 2013 和 Exchange Server 2013 一般圖例。</span><span class="sxs-lookup"><span data-stu-id="bef0e-105">This poster provides a general illustration of a network environment that includes Lync Server 2013, SharePoint 2013, and Exchange Server 2013.</span></span> <span data-ttu-id="bef0e-106">它也會說明下列都是通用這些產品的網路元素： 遠端和內部存取、 驗證、 用戶端流量，以及路由流量通過共用的裝置。</span><span class="sxs-lookup"><span data-stu-id="bef0e-106">It also illustrates the following networking elements that are common across these products: remote and internal access, authentication, client traffic, and routing traffic through shared devices.</span></span> 
  
## <a name="high-level-concepts-for-lync-exchange-sharepoint-server-and-office-web-apps"></a><span data-ttu-id="bef0e-107">Lync、 Exchange、 SharePoint Server 和 Office Web Apps 的高層級概念</span><span class="sxs-lookup"><span data-stu-id="bef0e-107">High-level concepts for Lync, Exchange, SharePoint Server, and Office Web Apps</span></span>

### <a name="about-the-design"></a><span data-ttu-id="bef0e-108">關於設計</span><span class="sxs-lookup"><span data-stu-id="bef0e-108">About the design</span></span>

#### <a name="streamlined-network-design"></a><span data-ttu-id="bef0e-109">簡化的網路規劃</span><span class="sxs-lookup"><span data-stu-id="bef0e-109">Streamlined network design</span></span>

<span data-ttu-id="bef0e-110">這種拓撲說明 SharePoint 2013、 Exchange Server 2013 和 Lync Server 2013 的內部網路部署。</span><span class="sxs-lookup"><span data-stu-id="bef0e-110">This topology illustrates an on-premises network deployment of SharePoint 2013, Exchange Server 2013, and Lync Server 2013.</span></span> <span data-ttu-id="bef0e-111">它也會顯示使用 Microsoft 雲端式服務，Exchange Online Protection，提供來自網際網路的內送簡易郵件傳送通訊協定 (SMTP) 流量的垃圾郵件和惡意程式碼保護。</span><span class="sxs-lookup"><span data-stu-id="bef0e-111">It also shows the use of the Microsoft cloud-based service, Exchange Online Protection, which provides spam and malware protection for inbound Simple Mail Transfer Protocol (SMTP) traffic from the Internet.</span></span> 
  
<span data-ttu-id="bef0e-112">此網路設計被精簡到最小的一段的網路功能。</span><span class="sxs-lookup"><span data-stu-id="bef0e-112">This network design is streamlined to a minimum set of network features.</span></span> <span data-ttu-id="bef0e-113">設計不會考慮帳戶額外安全性或基礎結構功能，有些組織可能需要。</span><span class="sxs-lookup"><span data-stu-id="bef0e-113">The design does not take into account additional security or infrastructure features that some organizations might require.</span></span> 
  
<span data-ttu-id="bef0e-114">此圖中：</span><span class="sxs-lookup"><span data-stu-id="bef0e-114">This diagram:</span></span> 
  
- <span data-ttu-id="bef0e-115">提供說明輸入和輸出流量通過閘道路由器和負載平衡的用戶端工作階段的流量 （外部及內部） 至適當的 SharePoint、 Exchange 和 Lync 伺服器層範例網路拓撲。</span><span class="sxs-lookup"><span data-stu-id="bef0e-115">Provides an example network topology illustrating inbound and outbound traffic through a gateway router and load balancing of client session traffic (external and internal) to the appropriate SharePoint, Exchange, and Lync server tiers.</span></span> 
    
- <span data-ttu-id="bef0e-116">顯示使用選用的遠端存取伺服器，例如協力廠商 VPN 閘道或 DirectAccess 伺服器，以提供漫遊或遠端員工的安全通訊。</span><span class="sxs-lookup"><span data-stu-id="bef0e-116">Shows the use of optional remote access servers, such as a third-party VPN gateway or DirectAccess server, to provide secure communication for roaming or remote employees.</span></span> 
    
- <span data-ttu-id="bef0e-117">詳細說明 SharePoint、 Exchange 和 Lync 流量從用戶端至每個平台伺服器層。</span><span class="sxs-lookup"><span data-stu-id="bef0e-117">Details the SharePoint, Exchange, and Lync traffic flow from the client to each platform server tier.</span></span> 
    
- <span data-ttu-id="bef0e-118">會識別根據用戶端 （例如合作夥伴或員工），以及使用的驗證方法的遠端或內部存取連線的類型。</span><span class="sxs-lookup"><span data-stu-id="bef0e-118">Identifies the type of remote or internal access connection based on client (such as partner or employee), and the authentication method used.</span></span> 
    
- <span data-ttu-id="bef0e-119">細分 SharePoint、 Exchange 和 Lync 平台所需的伺服器角色，用來識別前端、 應用程式、 資料庫及其他層級。</span><span class="sxs-lookup"><span data-stu-id="bef0e-119">Breaks down the SharePoint, Exchange, and Lync platforms by required server roles, identifying the front end, application, database, and other levels.</span></span> 
    
<span data-ttu-id="bef0e-120">架構以下用於 SharePoint、 Lync 和 Exchange 不會建議實作這些平台的慣用的方法。</span><span class="sxs-lookup"><span data-stu-id="bef0e-120">The architecture used here for SharePoint, Lync, and Exchange does not suggest a preferred way of implementing these platforms.</span></span> <span data-ttu-id="bef0e-121">這只是提供範例為根據唯一的網路需求及安全性考量拓撲而有所不同。</span><span class="sxs-lookup"><span data-stu-id="bef0e-121">It merely provides an example as topologies differ based on unique network requirements and security considerations.</span></span> 
  
#### <a name="gateway-router"></a><span data-ttu-id="bef0e-122">閘道路由器</span><span class="sxs-lookup"><span data-stu-id="bef0e-122">Gateway router</span></span>

<span data-ttu-id="bef0e-123">此拓撲中，閘道路由器位於網路邊緣，並將所有內送和外寄流量的路由傳送到及傳送自內部網路。</span><span class="sxs-lookup"><span data-stu-id="bef0e-123">For this topology, the gateway router sits at the edge of the network and routes all incoming and outgoing traffic to and from the intranet.</span></span> <span data-ttu-id="bef0e-124">或者，也有可能閘道路由器，以及負載平衡器所示，例如多層的防火牆之間的差距其他元件。</span><span class="sxs-lookup"><span data-stu-id="bef0e-124">Alternatively, there could also be other components that bridge the gap between the gateway router and the load balancer shown, such as multiple layers of firewalls.</span></span> <span data-ttu-id="bef0e-125">這種拓撲代表只是一種方式來部署您的網路出許多。</span><span class="sxs-lookup"><span data-stu-id="bef0e-125">This topology represents just one way to deploy your network out of many.</span></span> <span data-ttu-id="bef0e-126">在此組態中，以允許非常特定傳入和傳出 IP 式傳輸的路由器介面上的存取控制清單 (Acl) 設定的閘道。</span><span class="sxs-lookup"><span data-stu-id="bef0e-126">In this configuration, the gateway is configured with access control lists (ACLs) to permit very specific incoming and outgoing IP-based traffic on the router interfaces.</span></span> <span data-ttu-id="bef0e-127">Acl、 進階的檢查或網路位址轉譯 (NAT) 也可以在其他裝置，例如防火牆，整個網路上執行。</span><span class="sxs-lookup"><span data-stu-id="bef0e-127">ACLs, advanced inspection, or Network Address Translation (NAT) can also be performed on other devices, such as firewalls, throughout your network.</span></span> 
  
#### <a name="load-balancer-and-reverse-proxy-devices"></a><span data-ttu-id="bef0e-128">負載平衡器和反向 proxy 裝置</span><span class="sxs-lookup"><span data-stu-id="bef0e-128">Load balancer and reverse proxy devices</span></span>

<span data-ttu-id="bef0e-129">您可以使用硬體或軟體負載平衡解決方案來將區段包括 SharePoint 前端網頁伺服器和 Exchange Client Access Server （凱） 流量重新導向。</span><span class="sxs-lookup"><span data-stu-id="bef0e-129">You can use hardware or software load balancing solutions to redirect traffic for segments including SharePoint front-end web servers and Exchange Client Access Servers (CASs).</span></span> <span data-ttu-id="bef0e-130">在某些情況下最好是因為它可以更妥善地執行要求，例如 cookie 或標頭中使用資訊第 7 層硬體型負載平衡器用於持續性需求。</span><span class="sxs-lookup"><span data-stu-id="bef0e-130">In some cases it's optimal to use a layer 7 hardware-based load balancer for persistence requirements as it can perform better by using information in the request, such as cookies or headers.</span></span> <span data-ttu-id="bef0e-131">不過，因素，像是成本及增加的使用率，並從這類解決方案的工作負載可能不適合您的特定需求。</span><span class="sxs-lookup"><span data-stu-id="bef0e-131">However, factors like cost and increased utilization and workload from such a solution might not be desirable for your specific needs.</span></span> <span data-ttu-id="bef0e-132">請考慮下列重點為跨 SharePoint、 Exchange 和 Lync 的負載平衡：</span><span class="sxs-lookup"><span data-stu-id="bef0e-132">Consider the following points for load balancing across SharePoint, Exchange, and Lync:</span></span> 
  
- <span data-ttu-id="bef0e-133">SharePoint-針對 SharePoint 2013，您不需要啟用親和性的前端網頁伺服器。</span><span class="sxs-lookup"><span data-stu-id="bef0e-133">SharePoint - For SharePoint 2013, you do not need to enable affinity for your front-end web servers.</span></span> <span data-ttu-id="bef0e-134">一般而言，這會用於建立自黏工作階段，以及避免多個驗證來自用戶端要求每一部前端網頁伺服器。</span><span class="sxs-lookup"><span data-stu-id="bef0e-134">Normally, this would be used for creating sticky sessions and avoiding multiple authentication requests from clients to each front-end web server.</span></span> <span data-ttu-id="bef0e-135">在 SharePoint 2013 中新的分散式快取服務儲存及 SharePoint 伺服器陣列的網頁伺服器間分散登入權杖。</span><span class="sxs-lookup"><span data-stu-id="bef0e-135">The new Distributed Cache service in SharePoint 2013 stores and distributes logon tokens across the web servers of the SharePoint farm.</span></span> 
    
- <span data-ttu-id="bef0e-136">Exchange 位在 Exchange 2013 中，CAS 角色被設計來使用第 4 層負載平衡，分散於傳輸層的要求。</span><span class="sxs-lookup"><span data-stu-id="bef0e-136">Exchange - In Exchange 2013, the CAS role is designed to use layer 4 load balancing, distributing requests at the transport layer.</span></span> <span data-ttu-id="bef0e-137">這會大幅降低負載平衡器使用率和工作負載。</span><span class="sxs-lookup"><span data-stu-id="bef0e-137">This can significantly decrease load balancer utilization and workload.</span></span> 
    
- <span data-ttu-id="bef0e-138">Lync-Lync 集區的工作階段初始通訊協定 (SIP) 流量，建議使用網域名稱系統 (DNS) 負載平衡。</span><span class="sxs-lookup"><span data-stu-id="bef0e-138">Lync - Domain Name System (DNS) load balancing is recommended for Session Initiation Protocol (SIP) traffic for Lync pools.</span></span> <span data-ttu-id="bef0e-139">硬體負載平衡 (HLB) 有 Lync Web (HTTPS) 流量。</span><span class="sxs-lookup"><span data-stu-id="bef0e-139">Hardware load balancing (HLB) is required for Lync Web (HTTPS) traffic.</span></span> 
    
### <a name="remote-access-options"></a><span data-ttu-id="bef0e-140">遠端存取選項</span><span class="sxs-lookup"><span data-stu-id="bef0e-140">Remote access options</span></span>

<span data-ttu-id="bef0e-141">有幾個選項可以發佈內部網路資源的網際網路上的合作夥伴或遠端或漫遊員工提供安全的遠端存取。</span><span class="sxs-lookup"><span data-stu-id="bef0e-141">There are several options that can publish intranet resources for partners on the Internet or provide secure remote access for remote or roaming employees.</span></span> <span data-ttu-id="bef0e-142">這類範例包括反向 proxy、 DirectAccess，與協力廠商 VPN 閘道。</span><span class="sxs-lookup"><span data-stu-id="bef0e-142">Such examples include reverse proxies, DirectAccess, and third-party VPN gateways.</span></span> <span data-ttu-id="bef0e-143">本節稍後討論的遠端存取解決方案是可以用於 SharePoint、 Lync 和 Exchange 或在內部部署中的這些伺服器的任何組合。</span><span class="sxs-lookup"><span data-stu-id="bef0e-143">The remote access solutions discussed later in this section are possibilities for SharePoint, Lync, and Exchange, or any combination of these servers in an on-premises deployment.</span></span> <span data-ttu-id="bef0e-144">不過，某些遠端選項可能無法使用特定的解決方案。</span><span class="sxs-lookup"><span data-stu-id="bef0e-144">However, some remote options might not work with a particular solution.</span></span> 
  
<span data-ttu-id="bef0e-145">反向 Proxy-反向 proxy 支援流量加密，例如安全通訊端層 (SSL)，並與其您可以發佈內部網路應用程式和 web 資源，以驗證使用者與網際網路上的合作夥伴。</span><span class="sxs-lookup"><span data-stu-id="bef0e-145">Reverse Proxy - A reverse proxy supports traffic encryption, such as Secure Sockets Layer (SSL), and with it you can publish intranet applications and web resources to authenticated users and partners on the Internet.</span></span> <span data-ttu-id="bef0e-146">例如，Microsoft Forefront Unified Access Gateway (UAG)。</span><span class="sxs-lookup"><span data-stu-id="bef0e-146">An example is Microsoft Forefront Unified Access Gateway (UAG).</span></span> <span data-ttu-id="bef0e-147">許多硬體負載平衡器也支援反向 proxy 功能。</span><span class="sxs-lookup"><span data-stu-id="bef0e-147">Many hardware load balancers also support reverse proxy functionality.</span></span> <span data-ttu-id="bef0e-148">不過，有仍然有效使用根據您的需求和需求，例如流量隔離、 安全性分隔和效能最佳化獨立方案的案例。</span><span class="sxs-lookup"><span data-stu-id="bef0e-148">However, there are still valid scenarios for using a standalone solution based on your needs and requirements, such as traffic isolation, security compartmentalization, and performance optimization.</span></span> 
  
<span data-ttu-id="bef0e-149">反向 proxy 的優勢及考量：</span><span class="sxs-lookup"><span data-stu-id="bef0e-149">Reverse-proxy benefits and considerations:</span></span> 
  
- <span data-ttu-id="bef0e-150">提供已驗證和安全存取協力廠商或使用者存取內部網路資源 （使用在用戶端和反向 proxy 伺服器之間的 SSL (TCP 443)）。</span><span class="sxs-lookup"><span data-stu-id="bef0e-150">Provides authenticated and secured access for partners or users accessing intranet resources (uses SSL (TCP 443) between the client and reverse proxy server).</span></span> 
    
- <span data-ttu-id="bef0e-151">Exchange，使用例如 Forefront UAG 的反向 proxy 的好處是預先驗證存取 Exchange 用戶端存取伺服器之前。</span><span class="sxs-lookup"><span data-stu-id="bef0e-151">For Exchange, a benefit of using a reverse proxy such as Forefront UAG is pre-authentication before accessing the Exchange Client access server.</span></span> <span data-ttu-id="bef0e-152">使用的遠端存取使用者發佈應用程式，例如 Outlook Web Access (OWA) 可以使用驗證的基本、 NTLM 或 Kerberos 方法之前到達內部網路。</span><span class="sxs-lookup"><span data-stu-id="bef0e-152">Remote access users using published applications such as Outlook Web Access (OWA) can authenticate with the basic, NTLM, or Kerberos methods before they reach the internal network.</span></span> 
    
- <span data-ttu-id="bef0e-153">Exchange 和 SharePoint，像是 Forefront UAG 的解決方案可以終止 SSL 連線，並減少網路資源伺服器的負載時提供的憑證管理的單一資料點。</span><span class="sxs-lookup"><span data-stu-id="bef0e-153">For Exchange and SharePoint, solutions like Forefront UAG can terminate SSL connections and decrease the load of the intranet resources server while providing a single point of management for certificates.</span></span> 
    
- <span data-ttu-id="bef0e-154">Lync，網站 (HTTPS) 流量會通過反向 proxy (TCP 443) 的用戶端通訊。</span><span class="sxs-lookup"><span data-stu-id="bef0e-154">For Lync, Web (HTTPS) traffic goes through the reverse proxy (TCP 443) for client communication.</span></span> <span data-ttu-id="bef0e-155">反向 proxy proxy HTTPS 連線至 Lync Web 服務、 Exchange CAS 和 Office Web Apps。</span><span class="sxs-lookup"><span data-stu-id="bef0e-155">The reverse proxy proxies the HTTPS connection to Lync Web Services, Exchange CAS, and Office Web Apps.</span></span> <span data-ttu-id="bef0e-156">Lync Server 2013 不支援 UAG。</span><span class="sxs-lookup"><span data-stu-id="bef0e-156">Lync Server 2013 does not support UAG.</span></span> 
    
<span data-ttu-id="bef0e-157">DirectAccess-依賴網際網路通訊協定安全性 (IPsec) 進行驗證和加密 DirectAccess 用戶端與伺服器之間的流量的遠端存取的技術。</span><span class="sxs-lookup"><span data-stu-id="bef0e-157">DirectAccess - A remote access technology that relies on Internet Protocol security (IPsec) for authentication and for encrypting traffic between the DirectAccess client and server.</span></span> <span data-ttu-id="bef0e-158">DirectAccess 提供不必初始連線漫遊及遠端員工同時存取網際網路和內部網路資源。</span><span class="sxs-lookup"><span data-stu-id="bef0e-158">DirectAccess provides simultaneous access to both Internet and intranet resources for roaming and remote employees without having to initiate a connection.</span></span> 
  
<span data-ttu-id="bef0e-159">DirectAccess 要考慮的事項：</span><span class="sxs-lookup"><span data-stu-id="bef0e-159">DirectAccess points to consider:</span></span> 
  
- <span data-ttu-id="bef0e-160">DirectAccess 使用 IPsec 保護流量 （通訊協定 50 51 和 UDP 500） DirectAccess 用戶端與伺服器之間。</span><span class="sxs-lookup"><span data-stu-id="bef0e-160">DirectAccess uses IPsec protected traffic (protocol 50 and 51 and UDP 500) between the DirectAccess client and server.</span></span> 
    
- <span data-ttu-id="bef0e-161">Windows Server 2012 的 DirectAccess 和 Windows 8 不需要公開金鑰基礎結構 (PKI) 部署的伺服器和用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="bef0e-161">DirectAccess for Windows Server 2012 and Windows 8 does not need a public key infrastructure (PKI) deployment for server and client authentication.</span></span> 
    
- <span data-ttu-id="bef0e-162">我們建議您不要使用 Lync Server 2013 中的 DirectAccess，因為 IPsec 加密和解密相關聯的音訊和視訊延遲問題。</span><span class="sxs-lookup"><span data-stu-id="bef0e-162">We recommend against using DirectAccess with Lync Server 2013 because of audio and video latency issues associated with IPsec encryption and decryption.</span></span> 
    
    <span data-ttu-id="bef0e-163">VPN 閘道-一般 VPN 閘道提供遠端存取連線中的遠端存取用戶端電腦以邏輯方式投射通道及使用者起始連線到內部網路。</span><span class="sxs-lookup"><span data-stu-id="bef0e-163">VPN Gateway - Typical VPN gateways provide a remote access connection in which a remote access client computer is logically projected onto the intranet through a tunneled and user-initiated connection.</span></span> <span data-ttu-id="bef0e-164">您可以使用整合 Windows Server 2012 或幾個協力廠商解決方案中的遠端存取提供安全的存取內部網路的漫遊或遠端員工。</span><span class="sxs-lookup"><span data-stu-id="bef0e-164">You can use Unified Remote Access in Windows Server 2012 or several third-party solutions to provide secured access to the intranet for roaming or remote employees.</span></span> <span data-ttu-id="bef0e-165">Lync 不建議 VPN。</span><span class="sxs-lookup"><span data-stu-id="bef0e-165">VPN is not recommended for Lync.</span></span> <span data-ttu-id="bef0e-166">遠端 Lync 流量應該使用 Edge Server，並將 split 通道。</span><span class="sxs-lookup"><span data-stu-id="bef0e-166">Remote Lync traffic should use the Edge Servers and split tunneling.</span></span> 
    
### <a name="domain-name-system-dns-considerations"></a><span data-ttu-id="bef0e-167">網域名稱系統 (DNS) 考量</span><span class="sxs-lookup"><span data-stu-id="bef0e-167">Domain Name System (DNS) considerations</span></span>

<span data-ttu-id="bef0e-168">您需要規劃的一組 DNS 記錄，可讓網際網路和內部網路 DNS 名稱解析為適當的 IP 位址的使用者。</span><span class="sxs-lookup"><span data-stu-id="bef0e-168">You need to plan for the set of DNS records that allow both Internet and intranet users to resolve DNS names to the appropriate IP addresses.</span></span> 
  
- <span data-ttu-id="bef0e-169">為網際網路型合作夥伴和漫遊或遠端員工，註冊網際網路 DNS 伺服器的 DNS 記錄提供一組公用 IP 位址對應至閘道路由器，Lync Edge Server，一組虛擬 IP 位址 (Vip) 的解析度負載平衡器，並視 DirectAccess 或 VPN 閘道。</span><span class="sxs-lookup"><span data-stu-id="bef0e-169">For Internet-based partners and roaming or remote employees, DNS records registered with Internet DNS servers provide resolution to the set of public IP addresses corresponding to the gateway router, the Lync Edge Server, the set of virtual IP addresses (VIPs) on the load balancer, and the DirectAccess or VPN gateway as needed.</span></span> 
    
- <span data-ttu-id="bef0e-170">對於內部網路為基礎的使用者，註冊內部網路 DNS 伺服器的 DNS 記錄提供的虛擬 IP 位址 (Vip) 的解析度負載平衡器上 SharePoint、 Lync 和 Exchange 資源的存取權。</span><span class="sxs-lookup"><span data-stu-id="bef0e-170">For intranet-based users, DNS records registered with intranet DNS servers provide resolution to the set of virtual IP addresses (VIPs) on the load balancer for access to SharePoint, Lync, and Exchange resources.</span></span> 
    
- <span data-ttu-id="bef0e-171">DirectAccess 用戶端會使用內部網路 DNS 伺服器名稱對應至內部網路 DNS 命名空間和網際網路 DNS 伺服器的名稱，則否。</span><span class="sxs-lookup"><span data-stu-id="bef0e-171">DirectAccess clients use intranet DNS servers for names corresponding to the intranet DNS name space and Internet DNS servers for names that do not.</span></span> <span data-ttu-id="bef0e-172">為了簡化 DirectAccess 的作業，請考慮使用內部網路和網際網路型的名稱會使用不同的 DNS 命名空間的分割 DNS 實作。</span><span class="sxs-lookup"><span data-stu-id="bef0e-172">To simplify the operation of DirectAccess, consider the use of a split DNS implementation that uses different DNS namespaces for intranet and Internet-based names.</span></span> <span data-ttu-id="bef0e-173">例如，使用網際網路命名空間和命名空間的內部網路 corp.contoso.com contoso.com。</span><span class="sxs-lookup"><span data-stu-id="bef0e-173">For example, use contoso.com for Internet namespace and corp.contoso.com for the intranet namespace.</span></span> 
    
- <span data-ttu-id="bef0e-174">Exchange 會使用分割 DNS 模型 IP 解析度的主機上可公開路由傳送流量從公司網路上的不同位置。</span><span class="sxs-lookup"><span data-stu-id="bef0e-174">Exchange uses a split DNS model where host to IP resolution differs on publicly routed traffic from that on the corporate network.</span></span> <span data-ttu-id="bef0e-175">在最低限度下，您需要有的 OWA、 自動探索、 ActiveSync Url 的 DNS 記錄，用戶端流量和輸入郵件的 MX 記錄。</span><span class="sxs-lookup"><span data-stu-id="bef0e-175">At a minimum, you need to have DNS records for OWA, Autodiscover, ActiveSync URLs for client traffic, and an MX record for inbound mail.</span></span> 
    
- <span data-ttu-id="bef0e-176">如果您使用 Exchange Online Protection (EOP)，您的 MX 記錄會指向該服務，而不是您的 Exchange 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="bef0e-176">If you are using Exchange Online Protection (EOP), your MX record points to that service instead of your Exchange farm.</span></span> 
    
- <span data-ttu-id="bef0e-177">Exchange，則必須證明擁有權 TXT 記錄您在公用 DNS，以及同盟組織識別碼來設定同盟共用。</span><span class="sxs-lookup"><span data-stu-id="bef0e-177">For Exchange, you need a proof of ownership TXT record in your public DNS, and a Federation Org ID to set up federated sharing.</span></span> 
    
- <span data-ttu-id="bef0e-178">遠端存取 VPN 用戶端可以設定成使用僅限內部網路 DNS 伺服器，當 VPN 連線的遠端存取為作用中。</span><span class="sxs-lookup"><span data-stu-id="bef0e-178">Remote access VPN clients can be configured to use only intranet DNS servers when the remote access VPN connection is active.</span></span> 
    
### <a name="diagram-description"></a><span data-ttu-id="bef0e-179">圖表描述</span><span class="sxs-lookup"><span data-stu-id="bef0e-179">Diagram Description</span></span>

<span data-ttu-id="bef0e-180">此圖提供說明輸入和輸出流量通過閘道路由器和負載平衡的用戶端工作階段的流量 （外部及內部） 至適當的 SharePoint、 Exchange 和 Lync 伺服器層範例網路拓撲。</span><span class="sxs-lookup"><span data-stu-id="bef0e-180">This diagram provides an example network topology illustrating inbound and outbound traffic through a gateway router and load balancing of client session traffic (external and internal) to the appropriate SharePoint, Exchange, and Lync server tiers.</span></span> <span data-ttu-id="bef0e-181">此圖說明可分成兩個部分：</span><span class="sxs-lookup"><span data-stu-id="bef0e-181">The description of this diagram is divided into two parts:</span></span> 
  
- <span data-ttu-id="bef0e-182">元件圖所示的描述</span><span class="sxs-lookup"><span data-stu-id="bef0e-182">Description of components shown in the diagram</span></span> 
    
- <span data-ttu-id="bef0e-183">描述如何流量進入元件至 SharePoint、 Exchange、 Lync 與 Office Web Apps server 層級。</span><span class="sxs-lookup"><span data-stu-id="bef0e-183">Description of how traffic moves through the components to the SharePoint, Exchange, Lync, and Office Web Apps server tiers.</span></span> 
    
#### <a name="description-of-components-shown-in-the-diagram"></a><span data-ttu-id="bef0e-184">元件圖所示的描述</span><span class="sxs-lookup"><span data-stu-id="bef0e-184">Description of components shown in the diagram</span></span>

#### <a name="user-types"></a><span data-ttu-id="bef0e-185">使用者類型</span><span class="sxs-lookup"><span data-stu-id="bef0e-185">User types</span></span>

<span data-ttu-id="bef0e-186">有四種不同類型的使用者、 外的網路和雲端服務的三個，一個內部，其中包括：</span><span class="sxs-lookup"><span data-stu-id="bef0e-186">There are four different types of users, three outside the network and cloud services and one internal, which include:</span></span> 
  
- <span data-ttu-id="bef0e-187">合作夥伴公司 （企業對企業）-外部</span><span class="sxs-lookup"><span data-stu-id="bef0e-187">Partner companies (business-to-business)-external</span></span> 
    
- <span data-ttu-id="bef0e-188">個別合作夥伴 （SharePoint 和匿名 (Lync)）-外部</span><span class="sxs-lookup"><span data-stu-id="bef0e-188">Individual partners (SharePoint and anonymous (Lync))-external</span></span> 
    
- <span data-ttu-id="bef0e-189">漫遊及遠端員工外部</span><span class="sxs-lookup"><span data-stu-id="bef0e-189">Roaming and remote employees-external</span></span> 
    
- <span data-ttu-id="bef0e-190">內部員工</span><span class="sxs-lookup"><span data-stu-id="bef0e-190">Internal employees</span></span> 
    
#### <a name="cloud-based-email-traffic"></a><span data-ttu-id="bef0e-191">雲端式電子郵件流量</span><span class="sxs-lookup"><span data-stu-id="bef0e-191">Cloud-based email traffic</span></span>

<span data-ttu-id="bef0e-192">沒有 SMTP 型電子郵件流量，網際網路郵件主機或 Exchange Online Protection 的基於雲端的元件。</span><span class="sxs-lookup"><span data-stu-id="bef0e-192">There is a cloud-based component for SMTP-based email traffic, either Internet Mail Hosts or Exchange Online Protection.</span></span> 
  
#### <a name="authentication-for-external-access"></a><span data-ttu-id="bef0e-193">外部存取認證</span><span class="sxs-lookup"><span data-stu-id="bef0e-193">Authentication for external access</span></span>

<span data-ttu-id="bef0e-194">沒有一組特定的 Lync、 SharePoint 和 Exchange 的每個使用者類型的驗證程序。</span><span class="sxs-lookup"><span data-stu-id="bef0e-194">There is a specific set of authentication procedures for Lync, SharePoint, and Exchange for each of the user types.</span></span> <span data-ttu-id="bef0e-195">在本文件稍後詳細說明他們。</span><span class="sxs-lookup"><span data-stu-id="bef0e-195">They are described in more detail later in this document.</span></span> 
  
#### <a name="gateway-router-with-acls"></a><span data-ttu-id="bef0e-196">Acl 的閘道路由器</span><span class="sxs-lookup"><span data-stu-id="bef0e-196">Gateway router with ACLs</span></span>

<span data-ttu-id="bef0e-197">閘道路由器位於網路邊緣，並將所有內送和外寄流量的路由傳送到及傳送自內部網路。</span><span class="sxs-lookup"><span data-stu-id="bef0e-197">The gateway router sits at the edge of the network and routes all incoming and outgoing traffic to and from the intranet.</span></span> 
  
#### <a name="remote-access-servers-for-lync-and-sharepoint"></a><span data-ttu-id="bef0e-198">Lync 和 SharePoint 的遠端存取伺服器</span><span class="sxs-lookup"><span data-stu-id="bef0e-198">Remote access servers for Lync and SharePoint</span></span>

<span data-ttu-id="bef0e-199">此拓撲包含 Lync Edge server，以及 SharePoint VPN 閘道或 DirectAccess 伺服器。</span><span class="sxs-lookup"><span data-stu-id="bef0e-199">This topology includes a Lync Edge server, and a SharePoint VPN gateway or DirectAccess server.</span></span> 
  
#### <a name="load-balancer-and-reverse-proxy-device"></a><span data-ttu-id="bef0e-200">負載平衡器和反向 proxy 裝置</span><span class="sxs-lookup"><span data-stu-id="bef0e-200">Load balancer and reverse proxy device</span></span>

<span data-ttu-id="bef0e-201">您可以使用硬體或軟體負載平衡解決方案來將區段包括 SharePoint 前端網頁伺服器和 Exchange Client Access Server （凱） 流量重新導向。</span><span class="sxs-lookup"><span data-stu-id="bef0e-201">You can use hardware or software load balancing solutions to redirect traffic for segments including SharePoint front-end web servers and Exchange Client Access Servers (CASs).</span></span> <span data-ttu-id="bef0e-202">這種拓撲在負載平衡器中顯示 Lync VIP、 SharePoint VIP 和 Exchange VIP 元件。</span><span class="sxs-lookup"><span data-stu-id="bef0e-202">This topology shows Lync VIP, SharePoint VIP, and Exchange VIP components in the load balancer.</span></span> 
  
#### <a name="servers"></a><span data-ttu-id="bef0e-203">伺服器</span><span class="sxs-lookup"><span data-stu-id="bef0e-203">Servers</span></span>

<span data-ttu-id="bef0e-204">有四部伺服器： Lync、 SharePoint、 Exchange 和 Office Web Apps Server。</span><span class="sxs-lookup"><span data-stu-id="bef0e-204">There are four servers: Lync, SharePoint, Exchange, and Office Web Apps Server.</span></span> <span data-ttu-id="bef0e-205">每一部伺服器可以有三種層級： 前端、 用戶端存取層、 應用程式層與資料庫/儲存層。</span><span class="sxs-lookup"><span data-stu-id="bef0e-205">Each server can have three tiers: a front-end, client-access tier, an application tier, and a database/storage tier.</span></span>
  
#### <a name="front-end-client-access-tier"></a><span data-ttu-id="bef0e-206">前端、 用戶端存取層</span><span class="sxs-lookup"><span data-stu-id="bef0e-206">Front-end, client-access tier</span></span>

<span data-ttu-id="bef0e-207">這一層具有四個的所有伺服器上的元件：</span><span class="sxs-lookup"><span data-stu-id="bef0e-207">This tier has components on all four servers:</span></span> 
  
- <span data-ttu-id="bef0e-208">Lync 集區 （前端）。</span><span class="sxs-lookup"><span data-stu-id="bef0e-208">Lync pool (front end).</span></span> <span data-ttu-id="bef0e-209">此圖顯示兩個 Lync 資料庫。</span><span class="sxs-lookup"><span data-stu-id="bef0e-209">The diagram shows two Lync databases.</span></span> 
    
- <span data-ttu-id="bef0e-210">SharePoint 前端和分散式快取。</span><span class="sxs-lookup"><span data-stu-id="bef0e-210">SharePoint front end and distributed cache.</span></span> <span data-ttu-id="bef0e-211">此圖顯示三個 SharePoint 資料庫。</span><span class="sxs-lookup"><span data-stu-id="bef0e-211">The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="bef0e-212">Exchange CAS。</span><span class="sxs-lookup"><span data-stu-id="bef0e-212">Exchange CAS.</span></span> <span data-ttu-id="bef0e-213">此圖顯示兩個 Exchange 資料庫。</span><span class="sxs-lookup"><span data-stu-id="bef0e-213">The diagram shows two Exchange databases.</span></span> 
    
- <span data-ttu-id="bef0e-214">Office Web Apps Server。</span><span class="sxs-lookup"><span data-stu-id="bef0e-214">Office Web Apps Server.</span></span> <span data-ttu-id="bef0e-215">此圖顯示兩個 Office Web 應用程式資料庫。</span><span class="sxs-lookup"><span data-stu-id="bef0e-215">The diagram shows two Office Web Apps databases.</span></span> 
    
#### <a name="application-tier"></a><span data-ttu-id="bef0e-216">應用程式層</span><span class="sxs-lookup"><span data-stu-id="bef0e-216">Application tier</span></span>

<span data-ttu-id="bef0e-217">這一層只能在 SharePoint 伺服器上有元件：</span><span class="sxs-lookup"><span data-stu-id="bef0e-217">This tier has components only on the SharePoint server:</span></span> 
  
- <span data-ttu-id="bef0e-218">搜尋查詢、 索引 （系統）。</span><span class="sxs-lookup"><span data-stu-id="bef0e-218">Search (query, index, admin).</span></span> <span data-ttu-id="bef0e-219">此圖顯示三個 SharePoint 資料庫。</span><span class="sxs-lookup"><span data-stu-id="bef0e-219">The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="bef0e-220">批次處理程序。</span><span class="sxs-lookup"><span data-stu-id="bef0e-220">Batch processing.</span></span> <span data-ttu-id="bef0e-221">此圖顯示三個 SharePoint 資料庫。</span><span class="sxs-lookup"><span data-stu-id="bef0e-221">The diagram shows three SharePoint databases.</span></span> 
    
#### <a name="databasestorage-tier"></a><span data-ttu-id="bef0e-222">資料庫/儲存層</span><span class="sxs-lookup"><span data-stu-id="bef0e-222">Database/storage tier</span></span>

<span data-ttu-id="bef0e-223">這一層 Lync、 SharePoint 和 Exchange 伺服器上有元件：</span><span class="sxs-lookup"><span data-stu-id="bef0e-223">This tier has components on the Lync, SharePoint, and Exchange servers:</span></span> 
  
- <span data-ttu-id="bef0e-224">Lync 資料庫 （後端）。</span><span class="sxs-lookup"><span data-stu-id="bef0e-224">Lync Database (backend).</span></span> <span data-ttu-id="bef0e-225">此圖顯示三個 Lync 資料庫。</span><span class="sxs-lookup"><span data-stu-id="bef0e-225">The diagram shows three Lync databases.</span></span> 
    
- <span data-ttu-id="bef0e-226">SharePoint 資料庫。</span><span class="sxs-lookup"><span data-stu-id="bef0e-226">SharePoint Database.</span></span> <span data-ttu-id="bef0e-227">此圖顯示三個 SharePoint 資料庫。</span><span class="sxs-lookup"><span data-stu-id="bef0e-227">The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="bef0e-228">Exchange 信箱伺服器。</span><span class="sxs-lookup"><span data-stu-id="bef0e-228">Exchange Mailbox server.</span></span> <span data-ttu-id="bef0e-229">此圖顯示兩個 Exchange 信箱伺服器。</span><span class="sxs-lookup"><span data-stu-id="bef0e-229">The diagram shows two Exchange Mailbox servers.</span></span> 
    
<span data-ttu-id="bef0e-230">如需安裝在每個 SharePoint 伺服器角色上元件的詳細資訊，請參閱 < <b0>SharePoint 2013 的簡化拓撲</b0>。</span><span class="sxs-lookup"><span data-stu-id="bef0e-230">For more information about components installed on each of the SharePoint server roles, see [Streamlined Topologies for SharePoint 2013](https://aka.ms/Ma5cgk).</span></span> 
  
#### <a name="description-of-how-traffic-moves-through-the-components-to-the-different-server-tiers"></a><span data-ttu-id="bef0e-231">如何流量進入元件至不同的伺服器層級的描述</span><span class="sxs-lookup"><span data-stu-id="bef0e-231">Description of how traffic moves through the components to the different server tiers</span></span>

<span data-ttu-id="bef0e-232">本章節說明使用者要求瀏覽的網路拓撲的方式。</span><span class="sxs-lookup"><span data-stu-id="bef0e-232">This section describes how user requests move through the network topology.</span></span> 
  
#### <a name="authentication-and-routing-for-external-access"></a><span data-ttu-id="bef0e-233">驗證和外部存取的路由</span><span class="sxs-lookup"><span data-stu-id="bef0e-233">Authentication and routing for external access</span></span>

<span data-ttu-id="bef0e-234">有三種不同的網路和雲端服務，其中包含外的用戶端：</span><span class="sxs-lookup"><span data-stu-id="bef0e-234">There are three different types of clients outside the network and cloud services, which include:</span></span> 
  
- <span data-ttu-id="bef0e-235">合作夥伴公司 （企業對企業）-外部</span><span class="sxs-lookup"><span data-stu-id="bef0e-235">Partner companies (business-to-business)-external</span></span> 
    
- <span data-ttu-id="bef0e-236">個別合作夥伴 （SharePoint 和匿名 (Lync)）-外部</span><span class="sxs-lookup"><span data-stu-id="bef0e-236">Individual partners (SharePoint and anonymous (Lync))-external</span></span> 
    
- <span data-ttu-id="bef0e-237">漫遊及遠端員工外部</span><span class="sxs-lookup"><span data-stu-id="bef0e-237">Roaming and remote employees-external</span></span> 
    
<span data-ttu-id="bef0e-238">是個別說明的驗證及路由的程序的每個外部使用者類型。</span><span class="sxs-lookup"><span data-stu-id="bef0e-238">The authentication and routing process for each external user type is described individually.</span></span> 
  
#### <a name="partner-companies-business-to-business-httpspartnerwebcontosocom"></a><span data-ttu-id="bef0e-239">合作夥伴公司 （企業對企業） (https://partnerweb.contoso.com)</span><span class="sxs-lookup"><span data-stu-id="bef0e-239">Partner companies (business-to-business) (https://partnerweb.contoso.com)</span></span>

- <span data-ttu-id="bef0e-240">Lync： 與 Skype 和搭配 AOL 的公用 IM 連線能力 (PIC) 其他組織的同盟信任。</span><span class="sxs-lookup"><span data-stu-id="bef0e-240">Lync: federation trust with other organizations, Skype and Public IM Connectivity (PIC) with AOL.</span></span> <span data-ttu-id="bef0e-241">Lync 同盟流量通過閘道路由器至 Lync Edge Server、 Lync vip （負載平衡器/反向 proxy 伺服器），然後再到 Lync Server。</span><span class="sxs-lookup"><span data-stu-id="bef0e-241">The Lync federation traffic goes through the gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="bef0e-242">SharePoint 的安全： 信任的協力廠商身分識別提供者使用 SAML 驗證。</span><span class="sxs-lookup"><span data-stu-id="bef0e-242">SharePoint: Trusted partner identity provider with SAML authentication.</span></span> <span data-ttu-id="bef0e-243">SharePoint 用戶端流量會通過閘道路由器，SharePoint vip （負載平衡器/反向 proxy 伺服器），然後再到 SharePoint Server。</span><span class="sxs-lookup"><span data-stu-id="bef0e-243">The SharePoint client traffic goes through the Gateway router to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="bef0e-244">Exchange： 相互驗證 TLS 郵件流量，SAML 驗證的同盟共用。</span><span class="sxs-lookup"><span data-stu-id="bef0e-244">Exchange: Mutual Auth TLS for mail traffic, SAML authentication for Federated Sharing.</span></span> <span data-ttu-id="bef0e-245">Exchange 用戶端流量會通過閘道路由器，Exchange vip （負載平衡器/反向 proxy 伺服器），然後再向 Exchange 伺服器。</span><span class="sxs-lookup"><span data-stu-id="bef0e-245">The Exchange client traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="bef0e-246">SMTP 流量會透過閘道路由器，以及透過 Exchange VIP （負載平衡器/反向 proxy 伺服器） 向 Exchange 伺服器。</span><span class="sxs-lookup"><span data-stu-id="bef0e-246">SMTP traffic goes through the Gateway router and through the Exchange VIP (load balancer/reverse proxy server) to the Exchange server.</span></span> 
    
#### <a name="individual-partners-sharepoint-and-anonymous-lync-httpspartnerwebcontosocom-and-httpsmeetcontosocom"></a><span data-ttu-id="bef0e-247">個別合作夥伴 (SharePoint) 和匿名 (Lync) (https://partnerweb.contoso.com和https://meet.contoso.com)</span><span class="sxs-lookup"><span data-stu-id="bef0e-247">Individual partners (SharePoint) and anonymous (Lync) (https://partnerweb.contoso.com and https://meet.contoso.com)</span></span>

- <span data-ttu-id="bef0e-248">Lync： 匿名使用者只可以加入依員工的 Lync 會議。</span><span class="sxs-lookup"><span data-stu-id="bef0e-248">Lync: anonymous users can only join Lync meetings organized by employees.</span></span> <span data-ttu-id="bef0e-249">Lync 同盟流量通過閘道路由器至 Lync Edge Server、 Lync vip （負載平衡器/反向 proxy 伺服器），然後再到 Lync Server。</span><span class="sxs-lookup"><span data-stu-id="bef0e-249">The Lync federation traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="bef0e-250">SharePoint 的安全： 使用 SAML 驗證或表單型驗證的信任的合作夥伴身分識別提供者。</span><span class="sxs-lookup"><span data-stu-id="bef0e-250">SharePoint: Trusted partner identity provider with SAML authentication or forms-based authentication.</span></span> <span data-ttu-id="bef0e-251">SharePoint 用戶端流量會通過閘道路由器，SharePoint vip （負載平衡器/反向 proxy 伺服器），然後再到 SharePoint Server。</span><span class="sxs-lookup"><span data-stu-id="bef0e-251">The SharePoint client traffic goes through the Gateway router to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="bef0e-252">Exchange： 不適用。</span><span class="sxs-lookup"><span data-stu-id="bef0e-252">Exchange: Does not apply.</span></span> 
    
- <span data-ttu-id="bef0e-253">Lync Web 流量會通過閘道路由器至 Lync Edge Server，Lync vip （負載平衡器/反向 proxy 伺服器），硬體負載平衡器，也就是必要的 HTTPS 流量，並再 Lync Server。</span><span class="sxs-lookup"><span data-stu-id="bef0e-253">Lync Web traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="roaming-and-remote-employees"></a><span data-ttu-id="bef0e-254">漫遊及遠端員工</span><span class="sxs-lookup"><span data-stu-id="bef0e-254">Roaming and remote employees</span></span>

1. https://intranet.contoso.com 
    
2. https://teams.contoso.com 
    
3. https://my.contoso.com
    
4. https://partnerweb.contoso.com 
    
5. https://mail.contoso.com* 
    
6. https://dial.contoso.com*
    
7. https://meet.contoso.com*
    
* <span data-ttu-id="bef0e-255">Exchange URL 有下列虛擬目錄： 自動探索、 ecp，EWS、 Microsoft Server ActiveSync、 OAB，owa，PowerShell</span><span class="sxs-lookup"><span data-stu-id="bef0e-255">The Exchange URL has the following virtual directories: Autodiscover, ecp, EWS, Microsoft-Server-ActiveSync, OAB, owa, PowerShell</span></span> 
  
- <span data-ttu-id="bef0e-256">Lync: TLS DSK] 或 [NTLM 驗證。</span><span class="sxs-lookup"><span data-stu-id="bef0e-256">Lync: TLS-DSK or NTLM authentication.</span></span> <span data-ttu-id="bef0e-257">Lync 用戶端流量通過閘道路由器至 Lync Edge Server、 Lync vip （負載平衡器/反向 proxy 伺服器），然後再到 Lync Server。</span><span class="sxs-lookup"><span data-stu-id="bef0e-257">The Lync client traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="bef0e-258">SharePoint: Active Directory 網域服務 (AD DS)、 表單型驗證或 SAML 驗證。</span><span class="sxs-lookup"><span data-stu-id="bef0e-258">SharePoint: Active Directory Domain Services (AD DS), forms-based authentication, or SAML authentication.</span></span> <span data-ttu-id="bef0e-259">SharePoint 用戶端流量會通過 VPN 閘道或 DirectAccess 伺服器至 SharePoint VIP （負載平衡器/反向 proxy 伺服器），然後再到 SharePoint server。</span><span class="sxs-lookup"><span data-stu-id="bef0e-259">The SharePoint client traffic goes through the VPN gateway or the DirectAccess server to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint server.</span></span> 
    
- <span data-ttu-id="bef0e-260">Exchange： 透過 SSL (ActiveSync 自動探索)、 表單型驗證 (OWA) 的基本驗證。</span><span class="sxs-lookup"><span data-stu-id="bef0e-260">Exchange: Basic authentication over SSL (ActiveSync, Autodiscover), forms-based authentication (OWA).</span></span> <span data-ttu-id="bef0e-261">Exchange 用戶端流量會通過閘道路由器，Exchange vip （負載平衡器/反向 proxy 伺服器），然後再向 Exchange 伺服器。</span><span class="sxs-lookup"><span data-stu-id="bef0e-261">The Exchange client traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="bef0e-262">Lync 用戶端流量會通過閘道路由器 Lync vip （負載平衡器/反向 proxy 伺服器） 至硬體負載平衡器，也就是必要的 HTTPS 流量，然後再到 Lync Server。</span><span class="sxs-lookup"><span data-stu-id="bef0e-262">Lync client traffic goes through the Gateway router to the Lync VIP (load balancer/reverse proxy server) to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="authentication-for-internal-access"></a><span data-ttu-id="bef0e-263">供內部存取的驗證</span><span class="sxs-lookup"><span data-stu-id="bef0e-263">Authentication for internal access</span></span>

#### <a name="internal-employees"></a><span data-ttu-id="bef0e-264">內部員工</span><span class="sxs-lookup"><span data-stu-id="bef0e-264">Internal employees</span></span>

> https://intranet.contoso.com 
    
> https://teams.contoso.com 
    
> https://my.contoso.com
    
> https://partnerweb.contoso.com
    
> https://mail.contoso.com* 
    
> https://dial.contoso.com 
    
> https://meet.contoso.com
    
> https://admin.contoso.com
    
- <span data-ttu-id="bef0e-265">Lync: Kerberos]、 [TLS DSK 或 [NTLM 驗證。</span><span class="sxs-lookup"><span data-stu-id="bef0e-265">Lync: Kerberos, TLS-DSK, or NTLM authentication.</span></span> <span data-ttu-id="bef0e-266">Lync 用戶端流量會移至 Lync VIP （負載平衡器/反向 proxy 伺服器），然後再到 Lync Server。</span><span class="sxs-lookup"><span data-stu-id="bef0e-266">The Lync client traffic goes to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="bef0e-267">SharePoint: Active Directory 網域服務 (AD DS)、 表單型驗證或 SAML 驗證。</span><span class="sxs-lookup"><span data-stu-id="bef0e-267">SharePoint: Active Directory Domain Services (AD DS), forms-based authentication, or SAML authentication.</span></span> <span data-ttu-id="bef0e-268">SharePoint 用戶端流量會移至 SharePoint VIP （負載平衡器/反向 proxy 伺服器），然後再到 SharePoint Server。</span><span class="sxs-lookup"><span data-stu-id="bef0e-268">The SharePoint client traffic goes to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="bef0e-269">Exchange: AD DS 中，表單型驗證。</span><span class="sxs-lookup"><span data-stu-id="bef0e-269">Exchange: AD DS, forms-based authentication.</span></span> <span data-ttu-id="bef0e-270">Exchange 用戶端流量會移至 Exchange VIP （負載平衡器/反向 proxy 伺服器），然後再向 Exchange 伺服器。</span><span class="sxs-lookup"><span data-stu-id="bef0e-270">The Exchange client traffic goes to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="bef0e-271">Lync 用戶端流量會移到 Lync VIP （負載平衡器/反向 proxy 伺服器） 至硬體負載平衡器，也就是必要的 HTTPS 流量，然後再到 Lync Server。</span><span class="sxs-lookup"><span data-stu-id="bef0e-271">Lync client traffic goes to the Lync VIP (load balancer/reverse proxy server) to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="cloud-based-email-traffic"></a><span data-ttu-id="bef0e-272">雲端式電子郵件流量</span><span class="sxs-lookup"><span data-stu-id="bef0e-272">Cloud-based email traffic</span></span>

<span data-ttu-id="bef0e-273">SMTP 型電子郵件流量的雲端架構元件是由網際網路郵件主機或 Exchange Online Protection 所組成。</span><span class="sxs-lookup"><span data-stu-id="bef0e-273">The cloud-based component for SMTP-based email traffic consists of either Internet Mail Hosts or Exchange Online Protection.</span></span>
  
<span data-ttu-id="bef0e-274">這些元件會使用 SMTP 在網路上移動電子郵件流量。</span><span class="sxs-lookup"><span data-stu-id="bef0e-274">These components move email traffic over the network using SMTP.</span></span> <span data-ttu-id="bef0e-275">流量會通過閘道路由器，Exchange vip （負載平衡器/反向 proxy 伺服器），然後再向 Exchange 伺服器。</span><span class="sxs-lookup"><span data-stu-id="bef0e-275">The traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
  
### <a name="network-traffic-legend"></a><span data-ttu-id="bef0e-276">網路流量圖例</span><span class="sxs-lookup"><span data-stu-id="bef0e-276">Network traffic legend</span></span>

<span data-ttu-id="bef0e-277">[圖例] 方塊以圖形方式顯示不同類型的流量，如下所示的圖表中不同的彩色行上所述：</span><span class="sxs-lookup"><span data-stu-id="bef0e-277">The legend box graphically shows the different types of traffic depicted on the graph in different colored lines as follows:</span></span> 
  
- <span data-ttu-id="bef0e-278">綠色線條： Lync SIP 流量</span><span class="sxs-lookup"><span data-stu-id="bef0e-278">Green line: Lync SIP traffic</span></span> 
    
- <span data-ttu-id="bef0e-279">藍色線條： Lync Web 流量</span><span class="sxs-lookup"><span data-stu-id="bef0e-279">Blue line: Lync Web traffic</span></span> 
    
- <span data-ttu-id="bef0e-280">紫色線條： SharePoint 用戶端流量</span><span class="sxs-lookup"><span data-stu-id="bef0e-280">Purple line: SharePoint client traffic</span></span> 
    
- <span data-ttu-id="bef0e-281">橘色線條： Exchange 用戶端流量</span><span class="sxs-lookup"><span data-stu-id="bef0e-281">Orange line: Exchange client traffic</span></span> 
    
- <span data-ttu-id="bef0e-282">灰色列： Exchange 內部部署與 Exchange Online Protection 之間的 Exchange 郵件伺服器流量。</span><span class="sxs-lookup"><span data-stu-id="bef0e-282">Gray line: Exchange Mail Server traffic between Exchange on-premises and Exchange Online Protection.</span></span> 
    
<span data-ttu-id="bef0e-283">在 [圖例] 方塊中也說明不同類型的流量以及它們所使用的連接埠。</span><span class="sxs-lookup"><span data-stu-id="bef0e-283">The different types of traffic and the ports that they use are also described in the legend box.</span></span> 
  
#### <a name="lync-sip-traffic-and-lync-web-traffic"></a><span data-ttu-id="bef0e-284">Lync SIP 流量和 Lync web 流量</span><span class="sxs-lookup"><span data-stu-id="bef0e-284">Lync SIP traffic and Lync web traffic</span></span>

<span data-ttu-id="bef0e-285">Lync Edge Server 會使用下列連接埠的外部使用者通訊：</span><span class="sxs-lookup"><span data-stu-id="bef0e-285">The Lync Edge Server uses the following ports for external user communication:</span></span> 
  
- <span data-ttu-id="bef0e-286">IM 訊號流量 （SIP/簡單）： TCP 連接埠 443 （輸入流量開啟）</span><span class="sxs-lookup"><span data-stu-id="bef0e-286">Signaling/IM traffic (SIP/SIMPLE): TCP port 443 (open for inbound traffic)</span></span> 
    
- <span data-ttu-id="bef0e-287">Web 會議流量 (PSOM): TCP 443 （輸入流量的 [開啟]）</span><span class="sxs-lookup"><span data-stu-id="bef0e-287">Web conferencing traffic (PSOM): TCP 443 (open for inbound traffic)</span></span> 
    
- <span data-ttu-id="bef0e-288">A / V 流量 (SRTP): TCP 443、 UDP 3478 和 TCP 50000-59999 （選用） （開放輸入和輸出流量）</span><span class="sxs-lookup"><span data-stu-id="bef0e-288">A/V traffic (SRTP): TCP 443, UDP 3478 and TCP 50000-59999 (optional) (open for inbound and outbound traffic)</span></span> 
    
<span data-ttu-id="bef0e-289">Lync Edge Server 同盟的通訊使用下列連接埠：</span><span class="sxs-lookup"><span data-stu-id="bef0e-289">Lync Edge Server uses the following ports for federation communication:</span></span> 
  
- <span data-ttu-id="bef0e-290">TCP 連接埠 5061 (SIP)、 5269 (XMPP)，443 和 UDP 3478 (SRTP) （開放輸入和輸出流量）</span><span class="sxs-lookup"><span data-stu-id="bef0e-290">TCP ports 5061 (SIP), 5269 (XMPP), 443 and UDP 3478 (SRTP) (open for inbound and outbound traffic)</span></span> 
    
#### <a name="sharepoint-client-traffic"></a><span data-ttu-id="bef0e-291">SharePoint 用戶端流量</span><span class="sxs-lookup"><span data-stu-id="bef0e-291">SharePoint client traffic</span></span>

<span data-ttu-id="bef0e-292">SharePoint 可以使用 TCP 連接埠 443 (SSL) 加密通訊用戶端與負載平衡器。</span><span class="sxs-lookup"><span data-stu-id="bef0e-292">SharePoint can use TCP port 443 (SSL) for encrypted communication between the client and the load balancer.</span></span> <span data-ttu-id="bef0e-293">來自網際網路的外部存取，此連接埠必須開啟閘道路由器 （或外部防火牆） 上的輸入和輸出流量。</span><span class="sxs-lookup"><span data-stu-id="bef0e-293">For external access from the Internet, this port needs to be opened for inbound and outbound traffic on the gateway router (or external firewall).</span></span> 
  
#### <a name="exchange-client-traffic-and-exchange-mail-server-traffic"></a><span data-ttu-id="bef0e-294">Exchange 用戶端流量，且 Exchange 郵件伺服器流量</span><span class="sxs-lookup"><span data-stu-id="bef0e-294">Exchange client traffic and Exchange mail server traffic</span></span>

<span data-ttu-id="bef0e-295">Exchange 會使用 TCP 連接埠 25 (SMTP) 伺服器對伺服器通訊。</span><span class="sxs-lookup"><span data-stu-id="bef0e-295">Exchange uses TCP port 25 (SMTP) for server-to-server communications.</span></span> <span data-ttu-id="bef0e-296">連接埠 443 (HTTPS) 上會處理大部分的用戶端流量 （OWA、 ActiveSync、 自動探索、 Outlook 無所不在）。</span><span class="sxs-lookup"><span data-stu-id="bef0e-296">Most client traffic (OWA, ActiveSync, Autodiscover, Outlook Anywhere) is handled over port 443 (HTTPS).</span></span> <span data-ttu-id="bef0e-297">如果您有 POP 或 IMAP 用戶端，連接埠 110 (POP3)，995 (加密 POP3)、 143 (IMAP4)，993 (加密 IMAP4)、 及 587 (SMTP) 也可用來支援這些用戶端。</span><span class="sxs-lookup"><span data-stu-id="bef0e-297">If you have POP or IMAP clients, ports 110 (POP3), 995 (encrypted POP3), 143 (IMAP4), 993 (encrypted IMAP4), and 587 (SMTP) are also used to support these clients.</span></span> 
  
#### <a name="more-on-lync-network-traffic"></a><span data-ttu-id="bef0e-298">開啟 Lync 網路流量？</span><span class="sxs-lookup"><span data-stu-id="bef0e-298">More on Lync network traffic?</span></span>

<span data-ttu-id="bef0e-299">了解如何 Lync Server 可以協助您的組織提供立即訊息、 web 會議、 應用程式共用，以及語音通訊。</span><span class="sxs-lookup"><span data-stu-id="bef0e-299">Learn how Lync Server can help your organization provide instant messaging, web conferencing, application sharing, and voice communication.</span></span> <span data-ttu-id="bef0e-300">如需詳細資訊，請參閱 < <b0>Microsoft Lync Server 2013 通訊協定的工作負載海報</b0>。</span><span class="sxs-lookup"><span data-stu-id="bef0e-300">For more information, see [Microsoft Lync Server 2013 Protocol Workloads Poster](https://aka.ms/G5jzjo).</span></span> 
  
<span data-ttu-id="bef0e-301">海報也包含 QR 碼，來存取這項資訊。</span><span class="sxs-lookup"><span data-stu-id="bef0e-301">The poster also includes a QR code to access this information.</span></span> 
  

