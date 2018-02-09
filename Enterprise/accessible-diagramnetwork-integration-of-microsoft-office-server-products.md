---
title: "存取圖表-網路整合的 Microsoft Office 伺服器產品"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 89f564eb-95c3-4077-bb92-75bf71b51270
description: "本文是圖表的名為網路整合的 Microsoft Office Server 產品可存取的文字版本。"
ms.openlocfilehash: 3fa27b99bf0babf00c536057b9d21da784b6d94f
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="accessible-diagram---network-integration-of-microsoft-office-server-products"></a><span data-ttu-id="021d4-103">存取圖表-網路整合的 Microsoft Office 伺服器產品</span><span class="sxs-lookup"><span data-stu-id="021d4-103">Accessible diagram - Network Integration of Microsoft Office Server Products</span></span>

<span data-ttu-id="021d4-104">**摘要：**本文是圖表的名為網路整合的 Microsoft Office Server 產品可存取的文字版本。</span><span class="sxs-lookup"><span data-stu-id="021d4-104">**Summary:** This article is an accessible text version of the diagram named Network Integration of Microsoft Office Server Products.</span></span>
  
<span data-ttu-id="021d4-p101">這張海報提供網路環境包含 Lync Server 2013、 SharePoint 2013 與 Exchange Server 2013 一般圖。它也會說明這些產品都通用的下列網路元素： 遠端及內部存取、 驗證、 用戶端流量及共用裝置透過路由流量。</span><span class="sxs-lookup"><span data-stu-id="021d4-p101">This poster provides a general illustration of a network environment that includes Lync Server 2013, SharePoint 2013, and Exchange Server 2013. It also illustrates the following networking elements that are common across these products: remote and internal access, authentication, client traffic, and routing traffic through shared devices.</span></span> 
  
## <a name="high-level-concepts-for-lync-exchange-sharepoint-server-and-office-web-apps"></a><span data-ttu-id="021d4-107">Lync、 Exchange、 SharePoint Server 及 Office Web Apps 的高層級概念</span><span class="sxs-lookup"><span data-stu-id="021d4-107">High-level concepts for Lync, Exchange, SharePoint Server, and Office Web Apps</span></span>

### <a name="about-the-design"></a><span data-ttu-id="021d4-108">關於設計</span><span class="sxs-lookup"><span data-stu-id="021d4-108">About the design</span></span>

#### <a name="streamlined-network-design"></a><span data-ttu-id="021d4-109">簡化的網路設計</span><span class="sxs-lookup"><span data-stu-id="021d4-109">Streamlined network design</span></span>

<span data-ttu-id="021d4-p102">SharePoint 2013、 Exchange Server 2013 及 Lync Server 2013 的內部網路部署進行說明這種拓撲。它也會顯示使用 Microsoft 雲端式服務、 Exchange Online Protection，提供從網際網路輸入簡易郵件傳送通訊協定 (SMTP) 流量的垃圾郵件和惡意程式碼保護。</span><span class="sxs-lookup"><span data-stu-id="021d4-p102">This topology illustrates an on-premises network deployment of SharePoint 2013, Exchange Server 2013, and Lync Server 2013. It also shows the use of the Microsoft cloud-based service, Exchange Online Protection, which provides spam and malware protection for inbound Simple Mail Transfer Protocol (SMTP) traffic from the Internet.</span></span> 
  
<span data-ttu-id="021d4-p103">此網路設計會簡化到最小的一段網路功能。設計不會將列入帳戶額外安全性或基礎結構功能的某些組織可能會需要。</span><span class="sxs-lookup"><span data-stu-id="021d4-p103">This network design is streamlined to a minimum set of network features. The design does not take into account additional security or infrastructure features that some organizations might require.</span></span> 
  
<span data-ttu-id="021d4-114">此圖中：</span><span class="sxs-lookup"><span data-stu-id="021d4-114">This diagram:</span></span> 
  
- <span data-ttu-id="021d4-115">提供說明透過閘道路由器和負載平衡的用戶端工作階段 （外部和內部） 至流量適當 SharePoint、 Exchange 及 Lync server 層的輸入和輸出流量範例網路拓撲。</span><span class="sxs-lookup"><span data-stu-id="021d4-115">Provides an example network topology illustrating inbound and outbound traffic through a gateway router and load balancing of client session traffic (external and internal) to the appropriate SharePoint, Exchange, and Lync server tiers.</span></span> 
    
- <span data-ttu-id="021d4-116">會顯示使用選用的遠端存取伺服器，例如協力廠商 VPN 閘道或 DirectAccess 伺服器，以提供漫遊或遠端員工的安全通訊。</span><span class="sxs-lookup"><span data-stu-id="021d4-116">Shows the use of optional remote access servers, such as a third-party VPN gateway or DirectAccess server, to provide secure communication for roaming or remote employees.</span></span> 
    
- <span data-ttu-id="021d4-117">詳細說明 SharePoint、 Exchange 及 Lync 流量從用戶端至每個平台伺服器層。</span><span class="sxs-lookup"><span data-stu-id="021d4-117">Details the SharePoint, Exchange, and Lync traffic flow from the client to each platform server tier.</span></span> 
    
- <span data-ttu-id="021d4-118">會識別根據用戶端 （例如協力廠商或員工） 和使用的驗證方法的遠端或內部存取連線的類型。</span><span class="sxs-lookup"><span data-stu-id="021d4-118">Identifies the type of remote or internal access connection based on client (such as partner or employee), and the authentication method used.</span></span> 
    
- <span data-ttu-id="021d4-119">細分的 SharePoint、 Exchange 及 Lync 的平台所需的伺服器角色，用來識別前端、 應用程式、 資料庫及其他層級。</span><span class="sxs-lookup"><span data-stu-id="021d4-119">Breaks down the SharePoint, Exchange, and Lync platforms by required server roles, identifying the front end, application, database, and other levels.</span></span> 
    
<span data-ttu-id="021d4-p104">架構以下用於 SharePoint、 Lync 和 Exchange 不會建議的實作這些平台的慣用的方法。它只是提供一個範例為根據唯一的網路需求及安全性考量拓撲而有所不同。</span><span class="sxs-lookup"><span data-stu-id="021d4-p104">The architecture used here for SharePoint, Lync, and Exchange does not suggest a preferred way of implementing these platforms. It merely provides an example as topologies differ based on unique network requirements and security considerations.</span></span> 
  
#### <a name="gateway-router"></a><span data-ttu-id="021d4-122">閘道路由器</span><span class="sxs-lookup"><span data-stu-id="021d4-122">Gateway router</span></span>

<span data-ttu-id="021d4-p105">這種拓撲的閘道路由器置於桌網路邊緣和路由傳送所有內送和外寄流量到與內部網路。或者，也有可能閘道路由器和負載平衡器所示，例如多層的防火牆之間的差距其他元件。這種拓撲代表來部署您的網路移出許多的只是一種方式。在此設定，閘道設定以允許非常特定內送和外寄 IP 型流量路由器介面上的存取控制清單 (Acl)。也可在其他裝置，例如防火牆，整個網路上執行 Acl、 進階的檢查、 或網路位址轉譯 (NAT)。</span><span class="sxs-lookup"><span data-stu-id="021d4-p105">For this topology, the gateway router sits at the edge of the network and routes all incoming and outgoing traffic to and from the intranet. Alternatively, there could also be other components that bridge the gap between the gateway router and the load balancer shown, such as multiple layers of firewalls. This topology represents just one way to deploy your network out of many. In this configuration, the gateway is configured with access control lists (ACLs) to permit very specific incoming and outgoing IP-based traffic on the router interfaces. ACLs, advanced inspection, or Network Address Translation (NAT) can also be performed on other devices, such as firewalls, throughout your network.</span></span> 
  
#### <a name="load-balancer-and-reverse-proxy-devices"></a><span data-ttu-id="021d4-128">負載平衡器和反向 proxy 裝置</span><span class="sxs-lookup"><span data-stu-id="021d4-128">Load balancer and reverse proxy devices</span></span>

<span data-ttu-id="021d4-p106">硬體或軟體負載平衡解決方案可用於將區段包含 SharePoint 前端網頁伺服器和 Exchange Client Access Server （類別） 流量重新導向。在某些情況下它是用於第 7 層硬體為基礎的負載平衡器持續性需求可以更妥善地執行的要求，例如 cookie 或標頭中使用的資訊。不過，因素 like 成本並提升的使用情況和這類方案中的工作負載可能不是您的特定需求的取捨。請考慮下列點跨 SharePoint、 Exchange 及 Lync 的負載平衡：</span><span class="sxs-lookup"><span data-stu-id="021d4-p106">You can use hardware or software load balancing solutions to redirect traffic for segments including SharePoint front-end web servers and Exchange Client Access Servers (CASs). In some cases it's optimal to use a layer 7 hardware-based load balancer for persistence requirements as it can perform better by using information in the request, such as cookies or headers. However, factors like cost and increased utilization and workload from such a solution might not be desirable for your specific needs. Consider the following points for load balancing across SharePoint, Exchange, and Lync:</span></span> 
  
- <span data-ttu-id="021d4-p107">適用於 SharePoint 2013 的 SharePoint-您不需要啟用的前端網頁伺服器的相關性。一般而言，這就用於建立自黏工作階段與避免多個驗證要求用戶端至每部前端網頁伺服器。在 SharePoint 2013 中新的分散式快取服務儲存及分散登入 token 每個 SharePoint 伺服器陣列的網頁伺服器。</span><span class="sxs-lookup"><span data-stu-id="021d4-p107">SharePoint - For SharePoint 2013, you do not need to enable affinity for your front-end web servers. Normally, this would be used for creating sticky sessions and avoiding multiple authentication requests from clients to each front-end web server. The new Distributed Cache service in SharePoint 2013 stores and distributes logon tokens across the web servers of the SharePoint farm.</span></span> 
    
- <span data-ttu-id="021d4-p108">在 Exchange 2013]、 [CAS 角色中的 Exchange 層的設計使用階層 4 負載平衡散佈傳輸層級的要求。這會大幅降低負載平衡器使用量及工作負載。</span><span class="sxs-lookup"><span data-stu-id="021d4-p108">Exchange - In Exchange 2013, the CAS role is designed to use layer 4 load balancing, distributing requests at the transport layer. This can significantly decrease load balancer utilization and workload.</span></span> 
    
- <span data-ttu-id="021d4-p109">Lync-工作階段初始通訊協定 (SIP) 流量 Lync 集區的建議使用網域名稱系統 (DNS) 負載平衡。硬體負載平衡 (HLB) 是必要的 Lync Web (HTTPS) 流量。</span><span class="sxs-lookup"><span data-stu-id="021d4-p109">Lync - Domain Name System (DNS) load balancing is recommended for Session Initiation Protocol (SIP) traffic for Lync pools. Hardware load balancing (HLB) is required for Lync Web (HTTPS) traffic.</span></span> 
    
### <a name="remote-access-options"></a><span data-ttu-id="021d4-140">遠端存取選項</span><span class="sxs-lookup"><span data-stu-id="021d4-140">Remote access options</span></span>

<span data-ttu-id="021d4-p110">有數個選項可以發佈內部網路資源的網際網路上的協力廠商或遠端或漫遊員工提供安全的遠端存取。這類包括反向 proxy、 DirectAccess 及第三方 VPN 閘道。本節稍後討論的遠端存取解決方案為可能性 SharePoint、 Lync 和 Exchange 或在內部部署中的這些伺服器的任何組合。不過，某些遠端選項可能無法運作的特定的解決方案。</span><span class="sxs-lookup"><span data-stu-id="021d4-p110">There are several options that can publish intranet resources for partners on the Internet or provide secure remote access for remote or roaming employees. Such examples include reverse proxies, DirectAccess, and third-party VPN gateways. The remote access solutions discussed later in this section are possibilities for SharePoint, Lync, and Exchange, or any combination of these servers in an on-premises deployment. However, some remote options might not work with a particular solution.</span></span> 
  
<span data-ttu-id="021d4-p111">反向 Proxy-反向 proxy 支援流量加密，例如安全通訊端階層 (SSL)，並與其您可以發佈內部網路應用程式與 web 資源以驗證使用者與在網際網路上的協力廠商。例如，Microsoft Forefront Unified Access Gateway (UAG)。許多硬體負載平衡器也支援反向 proxy 功能。但有使用根據您的需求和需求，例如流量隔離、 安全性劃分和效能最佳化的獨立解決方案仍然有效案例。</span><span class="sxs-lookup"><span data-stu-id="021d4-p111">Reverse Proxy - A reverse proxy supports traffic encryption, such as Secure Sockets Layer (SSL), and with it you can publish intranet applications and web resources to authenticated users and partners on the Internet. An example is Microsoft Forefront Unified Access Gateway (UAG). Many hardware load balancers also support reverse proxy functionality. However, there are still valid scenarios for using a standalone solution based on your needs and requirements, such as traffic isolation, security compartmentalization, and performance optimization.</span></span> 
  
<span data-ttu-id="021d4-149">反向 proxy 的好處及考量：</span><span class="sxs-lookup"><span data-stu-id="021d4-149">Reverse-proxy benefits and considerations:</span></span> 
  
- <span data-ttu-id="021d4-150">提供已驗證及安全存取的協力廠商或使用者存取內部網路資源 （使用用戶端和反向 proxy 伺服器之間的 SSL (TCP 443)）。</span><span class="sxs-lookup"><span data-stu-id="021d4-150">Provides authenticated and secured access for partners or users accessing intranet resources (uses SSL (TCP 443) between the client and reverse proxy server).</span></span> 
    
- <span data-ttu-id="021d4-p112">Exchange 使用例如 Forefront UAG 的反向 proxy 的好處為預先驗證之前存取 Exchange 用戶端存取伺服器。使用的遠端存取使用者在例如 Outlook Web Access (OWA) 驗證的基本、 [NTLM] 或 Kerberos 方法之前達到內部網路發佈應用程式。</span><span class="sxs-lookup"><span data-stu-id="021d4-p112">For Exchange, a benefit of using a reverse proxy such as Forefront UAG is pre-authentication before accessing the Exchange Client access server. Remote access users using published applications such as Outlook Web Access (OWA) can authenticate with the basic, NTLM, or Kerberos methods before they reach the internal network.</span></span> 
    
- <span data-ttu-id="021d4-153">Exchange 和 SharePoint、 like Forefront UAG 的解決方案可以終止 SSL 連線並減少同時提供的憑證管理的單一資料點的內部網路資源伺服器的負載。</span><span class="sxs-lookup"><span data-stu-id="021d4-153">For Exchange and SharePoint, solutions like Forefront UAG can terminate SSL connections and decrease the load of the intranet resources server while providing a single point of management for certificates.</span></span> 
    
- <span data-ttu-id="021d4-p113">For Lync Web (HTTPS) 流量會通過反向 proxy (TCP 443) 的用戶端通訊。反向 proxy proxy HTTPS Lync Web 服務、 Exchange CAS 和 Office Web Apps 的連線。Lync Server 2013 不支援 UAG。</span><span class="sxs-lookup"><span data-stu-id="021d4-p113">For Lync, Web (HTTPS) traffic goes through the reverse proxy (TCP 443) for client communication. The reverse proxy proxies the HTTPS connection to Lync Web Services, Exchange CAS, and Office Web Apps. Lync Server 2013 does not support UAG.</span></span> 
    
<span data-ttu-id="021d4-p114">DirectAccess-依賴網際網路通訊協定安全性 (IPsec) 進行驗證和加密 DirectAccess 用戶端與伺服器之間的流量遠端存取技術。DirectAccess 提供不必起始連線漫遊和遠端員工同時存取網際網路及內部網路的資源。</span><span class="sxs-lookup"><span data-stu-id="021d4-p114">DirectAccess - A remote access technology that relies on Internet Protocol security (IPsec) for authentication and for encrypting traffic between the DirectAccess client and server. DirectAccess provides simultaneous access to both Internet and intranet resources for roaming and remote employees without having to initiate a connection.</span></span> 
  
<span data-ttu-id="021d4-159">DirectAccess 要考慮的事項：</span><span class="sxs-lookup"><span data-stu-id="021d4-159">DirectAccess points to consider:</span></span> 
  
- <span data-ttu-id="021d4-160">DirectAccess 使用受保護的 IPsec 流量 （50 和 51 及 UDP 500 通訊協定） DirectAccess 用戶端與伺服器之間。</span><span class="sxs-lookup"><span data-stu-id="021d4-160">DirectAccess uses IPsec protected traffic (protocol 50 and 51 and UDP 500) between the DirectAccess client and server.</span></span> 
    
- <span data-ttu-id="021d4-161">Windows Server 2012 的 DirectAccess 及 Windows 8 不需要公開金鑰基礎結構 (PKI) 部署的伺服器與用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="021d4-161">DirectAccess for Windows Server 2012 and Windows 8 does not need a public key infrastructure (PKI) deployment for server and client authentication.</span></span> 
    
- <span data-ttu-id="021d4-162">建議您針對 Lync Server 2013 搭配使用 DirectAccess 由於 IPsec 加密與解密相關聯的音訊和視訊延遲問題。</span><span class="sxs-lookup"><span data-stu-id="021d4-162">We recommend against using DirectAccess with Lync Server 2013 because of audio and video latency issues associated with IPsec encryption and decryption.</span></span> 
    
    <span data-ttu-id="021d4-p115">VPN 閘道-一般 VPN 閘道提供在其中的遠端存取用戶端電腦以邏輯方式投射到通道和使用者起始連線到內部網路的遠端存取連線。整合 Windows Server 2012 或數個協力廠商解決方案中的遠端存取可用來提供安全的存取內部網路的漫遊或遠端員工。Lync 不建議使用 VPN。遠端 Lync 流量應使用的 Edge Server，並將 split 通道。</span><span class="sxs-lookup"><span data-stu-id="021d4-p115">VPN Gateway - Typical VPN gateways provide a remote access connection in which a remote access client computer is logically projected onto the intranet through a tunneled and user-initiated connection. You can use Unified Remote Access in Windows Server 2012 or several third-party solutions to provide secured access to the intranet for roaming or remote employees. VPN is not recommended for Lync. Remote Lync traffic should use the Edge Servers and split tunneling.</span></span> 
    
### <a name="domain-name-system-dns-considerations"></a><span data-ttu-id="021d4-167">網域名稱系統 (DNS) 考量</span><span class="sxs-lookup"><span data-stu-id="021d4-167">Domain Name System (DNS) considerations</span></span>

<span data-ttu-id="021d4-168">您需要規劃的允許網際網路及內部網路使用者解析 DNS 名稱為適當的 IP 位址的 DNS 記錄集。</span><span class="sxs-lookup"><span data-stu-id="021d4-168">You need to plan for the set of DNS records that allow both Internet and intranet users to resolve DNS names to the appropriate IP addresses.</span></span> 
  
- <span data-ttu-id="021d4-169">網際網路為基礎的協力廠商和漫遊或遠端員工、 登錄與網際網路 DNS 伺服器的 DNS 記錄提供之公用 IP 位址對應至閘道路由器 Lync Edge Server 的虛擬 IP 位址 (Vip) 集的解決方法在負載平衡器和 DirectAccess 或 VPN 閘道所需。</span><span class="sxs-lookup"><span data-stu-id="021d4-169">For Internet-based partners and roaming or remote employees, DNS records registered with Internet DNS servers provide resolution to the set of public IP addresses corresponding to the gateway router, the Lync Edge Server, the set of virtual IP addresses (VIPs) on the load balancer, and the DirectAccess or VPN gateway as needed.</span></span> 
    
- <span data-ttu-id="021d4-170">內部網路型使用者、 登錄與內部網路的 DNS 伺服器的 DNS 記錄提供解析之虛擬 IP 位址 (Vip) 集負載平衡器上存取 SharePoint、 Lync 和 Exchange 的資源。</span><span class="sxs-lookup"><span data-stu-id="021d4-170">For intranet-based users, DNS records registered with intranet DNS servers provide resolution to the set of virtual IP addresses (VIPs) on the load balancer for access to SharePoint, Lync, and Exchange resources.</span></span> 
    
- <span data-ttu-id="021d4-p116">DirectAccess 用戶端使用的內部網路的 DNS 伺服器的名稱對應的內部網路 DNS 命名空間和網際網路 DNS 伺服器的名稱未執行。為了簡化 DirectAccess 的作業，請考慮使用不同的 DNS 命名空間的內部網路和網際網路式名稱分割 DNS 實作使用。例如，使用 contoso.com 網際網路命名空間和 corp.contoso.com 內部網路命名空間。</span><span class="sxs-lookup"><span data-stu-id="021d4-p116">DirectAccess clients use intranet DNS servers for names corresponding to the intranet DNS name space and Internet DNS servers for names that do not. To simplify the operation of DirectAccess, consider the use of a split DNS implementation that uses different DNS namespaces for intranet and Internet-based names. For example, use contoso.com for Internet namespace and corp.contoso.com for the intranet namespace.</span></span> 
    
- <span data-ttu-id="021d4-p117">Exchange 會使用分割 DNS 模型 IP 解析度主機上可公開路由流量與公司網路上的不同位置。在最低限度下，您需要有 OWA、 自動探索、 ActiveSync Url 的 DNS 記錄的用戶端流量和輸入郵件的 MX 記錄。</span><span class="sxs-lookup"><span data-stu-id="021d4-p117">Exchange uses a split DNS model where host to IP resolution differs on publicly routed traffic from that on the corporate network. At a minimum, you need to have DNS records for OWA, Autodiscover, ActiveSync URLs for client traffic, and an MX record for inbound mail.</span></span> 
    
- <span data-ttu-id="021d4-176">如果您使用的 Exchange Online Protection (EOP)，您的 MX 記錄指向該服務，而不是您的 Exchange 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="021d4-176">If you are using Exchange Online Protection (EOP), your MX record points to that service instead of your Exchange farm.</span></span> 
    
- <span data-ttu-id="021d4-177">Exchange，則必須證明擁有權 TXT 記錄在公用 DNS 中，以及設定同盟組織識別碼同盟共用。</span><span class="sxs-lookup"><span data-stu-id="021d4-177">For Exchange, you need a proof of ownership TXT record in your public DNS, and a Federation Org ID to set up federated sharing.</span></span> 
    
- <span data-ttu-id="021d4-178">遠端存取 VPN 用戶端可以設定為使用中的遠端存取 VPN 連線時使用的內部網路 DNS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="021d4-178">Remote access VPN clients can be configured to use only intranet DNS servers when the remote access VPN connection is active.</span></span> 
    
### <a name="diagram-description"></a><span data-ttu-id="021d4-179">圖表描述</span><span class="sxs-lookup"><span data-stu-id="021d4-179">Diagram Description</span></span>

<span data-ttu-id="021d4-p118">此圖提供範例網路拓撲說明透過閘道路由器和負載平衡的用戶端工作階段 （外部和內部） 至流量適當 SharePoint、 Exchange 及 Lync server 層的輸入和輸出流量。此圖說明可分為兩個部分：</span><span class="sxs-lookup"><span data-stu-id="021d4-p118">This diagram provides an example network topology illustrating inbound and outbound traffic through a gateway router and load balancing of client session traffic (external and internal) to the appropriate SharePoint, Exchange, and Lync server tiers. The description of this diagram is divided into two parts:</span></span> 
  
- <span data-ttu-id="021d4-182">圖所示的元件的描述</span><span class="sxs-lookup"><span data-stu-id="021d4-182">Description of components shown in the diagram</span></span> 
    
- <span data-ttu-id="021d4-183">描述如何流量進入元件至 SharePoint、 Exchange、 Lync 及 Office Web Apps server 層。</span><span class="sxs-lookup"><span data-stu-id="021d4-183">Description of how traffic moves through the components to the SharePoint, Exchange, Lync, and Office Web Apps server tiers.</span></span> 
    
#### <a name="description-of-components-shown-in-the-diagram"></a><span data-ttu-id="021d4-184">圖所示的元件的描述</span><span class="sxs-lookup"><span data-stu-id="021d4-184">Description of components shown in the diagram</span></span>

#### <a name="user-types"></a><span data-ttu-id="021d4-185">使用者類型</span><span class="sxs-lookup"><span data-stu-id="021d4-185">User types</span></span>

<span data-ttu-id="021d4-186">有四種不同類型的使用者、 外部網路和雲端服務的三個與一部內部，其中包括：</span><span class="sxs-lookup"><span data-stu-id="021d4-186">There are four different types of users, three outside the network and cloud services and one internal, which include:</span></span> 
  
- <span data-ttu-id="021d4-187">合作夥伴公司 (business-business)-外部</span><span class="sxs-lookup"><span data-stu-id="021d4-187">Partner companies (business-to-business)-external</span></span> 
    
- <span data-ttu-id="021d4-188">個別合作夥伴 （SharePoint 和匿名 (Lync)）-外部</span><span class="sxs-lookup"><span data-stu-id="021d4-188">Individual partners (SharePoint and anonymous (Lync))-external</span></span> 
    
- <span data-ttu-id="021d4-189">漫遊和遠端員工外部</span><span class="sxs-lookup"><span data-stu-id="021d4-189">Roaming and remote employees-external</span></span> 
    
- <span data-ttu-id="021d4-190">內部員工</span><span class="sxs-lookup"><span data-stu-id="021d4-190">Internal employees</span></span> 
    
#### <a name="cloud-based-email-traffic"></a><span data-ttu-id="021d4-191">雲端式電子郵件流量</span><span class="sxs-lookup"><span data-stu-id="021d4-191">Cloud-based email traffic</span></span>

<span data-ttu-id="021d4-192">有 SMTP 式電子郵件流量架設網際網路郵件或 Exchange Online Protection 的雲端式元件。</span><span class="sxs-lookup"><span data-stu-id="021d4-192">There is a cloud-based component for SMTP-based email traffic, either Internet Mail Hosts or Exchange Online Protection.</span></span> 
  
#### <a name="authentication-for-external-access"></a><span data-ttu-id="021d4-193">進行外部存取的驗證</span><span class="sxs-lookup"><span data-stu-id="021d4-193">Authentication for external access</span></span>

<span data-ttu-id="021d4-p119">有一組特定的 Lync、 SharePoint 及 Exchange 每個使用者所輸入的驗證程序。本文稍後的更詳細地說明它們。</span><span class="sxs-lookup"><span data-stu-id="021d4-p119">There is a specific set of authentication procedures for Lync, SharePoint, and Exchange for each of the user types. They are described in more detail later in this document.</span></span> 
  
#### <a name="gateway-router-with-acls"></a><span data-ttu-id="021d4-196">含 Acl 的閘道路由器</span><span class="sxs-lookup"><span data-stu-id="021d4-196">Gateway router with ACLs</span></span>

<span data-ttu-id="021d4-197">閘道路由器置於桌網路邊緣和路由傳送所有內送和外寄流量到與內部網路。</span><span class="sxs-lookup"><span data-stu-id="021d4-197">The gateway router sits at the edge of the network and routes all incoming and outgoing traffic to and from the intranet.</span></span> 
  
#### <a name="remote-access-servers-for-lync-and-sharepoint"></a><span data-ttu-id="021d4-198">Lync 和 SharePoint 的遠端存取伺服器</span><span class="sxs-lookup"><span data-stu-id="021d4-198">Remote access servers for Lync and SharePoint</span></span>

<span data-ttu-id="021d4-199">此拓撲包含 Lync Edge 伺服器與 SharePoint VPN 閘道或 DirectAccess 伺服器。</span><span class="sxs-lookup"><span data-stu-id="021d4-199">This topology includes a Lync Edge server, and a SharePoint VPN gateway or DirectAccess server.</span></span> 
  
#### <a name="load-balancer-and-reverse-proxy-device"></a><span data-ttu-id="021d4-200">負載平衡器和反向 proxy 裝置</span><span class="sxs-lookup"><span data-stu-id="021d4-200">Load balancer and reverse proxy device</span></span>

<span data-ttu-id="021d4-p120">硬體或軟體負載平衡解決方案可用於將區段包含 SharePoint 前端網頁伺服器和 Exchange Client Access Server （類別） 流量重新導向。這種拓撲的負載平衡器中顯示 Lync VIP、 SharePoint VIP 和 Exchange VIP 元件。</span><span class="sxs-lookup"><span data-stu-id="021d4-p120">You can use hardware or software load balancing solutions to redirect traffic for segments including SharePoint front-end web servers and Exchange Client Access Servers (CASs). This topology shows Lync VIP, SharePoint VIP, and Exchange VIP components in the load balancer.</span></span> 
  
#### <a name="servers"></a><span data-ttu-id="021d4-203">伺服器</span><span class="sxs-lookup"><span data-stu-id="021d4-203">Servers</span></span>

<span data-ttu-id="021d4-p121">有四部伺服器： Lync、 SharePoint、 Exchange 和 Office Web Apps Server。每一個伺服器可以有三層： 前端、 用戶端存取層、 應用程式層與資料庫/儲存層。</span><span class="sxs-lookup"><span data-stu-id="021d4-p121">There are four servers: Lync, SharePoint, Exchange, and Office Web Apps Server. Each server can have three tiers: a front-end, client-access tier, an application tier, and a database/storage tier.</span></span>
  
#### <a name="front-end-client-access-tier"></a><span data-ttu-id="021d4-206">前端、 用戶端存取層</span><span class="sxs-lookup"><span data-stu-id="021d4-206">Front-end, client-access tier</span></span>

<span data-ttu-id="021d4-207">此層有四個的所有伺服器上的元件：</span><span class="sxs-lookup"><span data-stu-id="021d4-207">This tier has components on all four servers:</span></span> 
  
- <span data-ttu-id="021d4-p122">Lync 集區 （前端）。此圖顯示兩個 Lync 資料庫。</span><span class="sxs-lookup"><span data-stu-id="021d4-p122">Lync pool (front end). The diagram shows two Lync databases.</span></span> 
    
- <span data-ttu-id="021d4-p123">SharePoint 前端和分散式快取。此圖顯示三個 SharePoint 資料庫。</span><span class="sxs-lookup"><span data-stu-id="021d4-p123">SharePoint front end and distributed cache. The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="021d4-p124">Exchange CAS。此圖顯示兩個 Exchange 資料庫。</span><span class="sxs-lookup"><span data-stu-id="021d4-p124">Exchange CAS. The diagram shows two Exchange databases.</span></span> 
    
- <span data-ttu-id="021d4-p125">Office Web Apps Server。此圖顯示兩個 Office Web 應用程式資料庫。</span><span class="sxs-lookup"><span data-stu-id="021d4-p125">Office Web Apps Server. The diagram shows two Office Web Apps databases.</span></span> 
    
#### <a name="application-tier"></a><span data-ttu-id="021d4-216">應用程式層</span><span class="sxs-lookup"><span data-stu-id="021d4-216">Application tier</span></span>

<span data-ttu-id="021d4-217">此層 SharePoint 伺服器上只包含元件：</span><span class="sxs-lookup"><span data-stu-id="021d4-217">This tier has components only on the SharePoint server:</span></span> 
  
- <span data-ttu-id="021d4-p126">搜尋查詢、 索引 （系統）。此圖顯示三個 SharePoint 資料庫。</span><span class="sxs-lookup"><span data-stu-id="021d4-p126">Search (query, index, admin). The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="021d4-p127">批次處理。此圖顯示三個 SharePoint 資料庫。</span><span class="sxs-lookup"><span data-stu-id="021d4-p127">Batch processing. The diagram shows three SharePoint databases.</span></span> 
    
#### <a name="databasestorage-tier"></a><span data-ttu-id="021d4-222">資料庫/儲存層</span><span class="sxs-lookup"><span data-stu-id="021d4-222">Database/storage tier</span></span>

<span data-ttu-id="021d4-223">此層 Lync、 SharePoint 及 Exchange 伺服器上有元件：</span><span class="sxs-lookup"><span data-stu-id="021d4-223">This tier has components on the Lync, SharePoint, and Exchange servers:</span></span> 
  
- <span data-ttu-id="021d4-p128">Lync 資料庫 （後端）。此圖顯示三個 Lync 資料庫。</span><span class="sxs-lookup"><span data-stu-id="021d4-p128">Lync Database (backend). The diagram shows three Lync databases.</span></span> 
    
- <span data-ttu-id="021d4-p129">SharePoint 資料庫。此圖顯示三個 SharePoint 資料庫。</span><span class="sxs-lookup"><span data-stu-id="021d4-p129">SharePoint Database. The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="021d4-p130">Exchange 信箱伺服器。此圖顯示兩個的 Exchange 信箱伺服器。</span><span class="sxs-lookup"><span data-stu-id="021d4-p130">Exchange Mailbox server. The diagram shows two Exchange Mailbox servers.</span></span> 
    
<span data-ttu-id="021d4-230">如需在每個 SharePoint 伺服器角色上安裝的元件的詳細資訊，請參閱 ＜ [SharePoint 2013 的簡化拓撲](https://aka.ms/Ma5cgk)。</span><span class="sxs-lookup"><span data-stu-id="021d4-230">For more information about components installed on each of the SharePoint server roles, see [Streamlined Topologies for SharePoint 2013](https://aka.ms/Ma5cgk).</span></span> 
  
#### <a name="description-of-how-traffic-moves-through-the-components-to-the-different-server-tiers"></a><span data-ttu-id="021d4-231">說明的方式流量進入元件至不同的伺服器層</span><span class="sxs-lookup"><span data-stu-id="021d4-231">Description of how traffic moves through the components to the different server tiers</span></span>

<span data-ttu-id="021d4-232">本節說明如何透過網路拓撲移動使用者要求。</span><span class="sxs-lookup"><span data-stu-id="021d4-232">This section describes how user requests move through the network topology.</span></span> 
  
#### <a name="authentication-and-routing-for-external-access"></a><span data-ttu-id="021d4-233">驗證與外部存取的路由</span><span class="sxs-lookup"><span data-stu-id="021d4-233">Authentication and routing for external access</span></span>

<span data-ttu-id="021d4-234">有三種不同的網路和雲端服務，其中包含外部的用戶端：</span><span class="sxs-lookup"><span data-stu-id="021d4-234">There are three different types of clients outside the network and cloud services, which include:</span></span> 
  
- <span data-ttu-id="021d4-235">合作夥伴公司 (business-business)-外部</span><span class="sxs-lookup"><span data-stu-id="021d4-235">Partner companies (business-to-business)-external</span></span> 
    
- <span data-ttu-id="021d4-236">個別合作夥伴 （SharePoint 和匿名 (Lync)）-外部</span><span class="sxs-lookup"><span data-stu-id="021d4-236">Individual partners (SharePoint and anonymous (Lync))-external</span></span> 
    
- <span data-ttu-id="021d4-237">漫遊和遠端員工外部</span><span class="sxs-lookup"><span data-stu-id="021d4-237">Roaming and remote employees-external</span></span> 
    
<span data-ttu-id="021d4-238">驗證並針對每個外部使用者類型的傳閱程序說明個別。</span><span class="sxs-lookup"><span data-stu-id="021d4-238">The authentication and routing process for each external user type is described individually.</span></span> 
  
#### <a name="partner-companies-business-to-business-httpspartnerwebcontosocom"></a><span data-ttu-id="021d4-239">合作夥伴公司 （商務對商務） (https://partnerweb.contoso.com)</span><span class="sxs-lookup"><span data-stu-id="021d4-239">Partner companies (business-to-business) (https://partnerweb.contoso.com)</span></span>

- <span data-ttu-id="021d4-p131">與其他組織 Skype 和 aol 的公用 IM 連線 (PIC) Lync： 同盟信任。Lync 同盟流量會通過閘道路由器 Lync Edge server、 Lync VIP （負載平衡器/反向 proxy 伺服器）]、 [Lync Server。</span><span class="sxs-lookup"><span data-stu-id="021d4-p131">Lync: federation trust with other organizations, Skype and Public IM Connectivity (PIC) with AOL. The Lync federation traffic goes through the gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="021d4-p132">SharePoint： 信任的協力廠商身分識別提供者使用 SAML 驗證。SharePoint 用戶端流量會通過閘道路由器，SharePoint VIP （負載平衡器/反向 proxy 伺服器）]、 [SharePoint 伺服器。</span><span class="sxs-lookup"><span data-stu-id="021d4-p132">SharePoint: Trusted partner identity provider with SAML authentication. The SharePoint client traffic goes through the Gateway router to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="021d4-p133">Exchange： 相互驗證 TLS 的郵件流量、 SAML 驗證同盟共用。Exchange 用戶端流量會通過閘道路由器 Exchange VIP （負載平衡器/反向 proxy 伺服器）]、 [Exchange 伺服器。</span><span class="sxs-lookup"><span data-stu-id="021d4-p133">Exchange: Mutual Auth TLS for mail traffic, SAML authentication for Federated Sharing. The Exchange client traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="021d4-246">SMTP 流量會前往 Exchange server 透過閘道路由器和透過 Exchange VIP （負載平衡器/反向 proxy 伺服器）。</span><span class="sxs-lookup"><span data-stu-id="021d4-246">SMTP traffic goes through the Gateway router and through the Exchange VIP (load balancer/reverse proxy server) to the Exchange server.</span></span> 
    
#### <a name="individual-partners-sharepoint-and-anonymous-lync-httpspartnerwebcontosocom-and-httpsmeetcontosocom"></a><span data-ttu-id="021d4-247">個別合作夥伴 (SharePoint) 和匿名 (Lync) （https://partnerweb.contoso.com 和 https://meet.contoso.com）</span><span class="sxs-lookup"><span data-stu-id="021d4-247">Individual partners (SharePoint) and anonymous (Lync) (https://partnerweb.contoso.com and https://meet.contoso.com)</span></span>

- <span data-ttu-id="021d4-p134">Lync： 匿名使用者只可加入員工所召集的 Lync 會議。Lync 同盟流量會通過閘道路由器 Lync Edge server、 Lync VIP （負載平衡器/反向 proxy 伺服器）]、 [Lync Server。</span><span class="sxs-lookup"><span data-stu-id="021d4-p134">Lync: anonymous users can only join Lync meetings organized by employees. The Lync federation traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="021d4-p135">SharePoint： 搭配 SAML 驗證或表單型驗證的信任的合作夥伴身分識別提供者。SharePoint 用戶端流量會通過閘道路由器，SharePoint VIP （負載平衡器/反向 proxy 伺服器）]、 [SharePoint 伺服器。</span><span class="sxs-lookup"><span data-stu-id="021d4-p135">SharePoint: Trusted partner identity provider with SAML authentication or forms-based authentication. The SharePoint client traffic goes through the Gateway router to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="021d4-252">Exchange： 不適用。</span><span class="sxs-lookup"><span data-stu-id="021d4-252">Exchange: Does not apply.</span></span> 
    
- <span data-ttu-id="021d4-253">Lync Web 流量會通過閘道路由器 Lync Edge server]，以 Lync VIP （負載平衡器/反向 proxy 伺服器），用於 HTTPS 流量所需的硬體負載平衡器]、 [Lync Server。</span><span class="sxs-lookup"><span data-stu-id="021d4-253">Lync Web traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="roaming-and-remote-employees"></a><span data-ttu-id="021d4-254">漫遊和遠端員工</span><span class="sxs-lookup"><span data-stu-id="021d4-254">Roaming and remote employees</span></span>

1. <span data-ttu-id="021d4-255">https://intranet.contoso.com</span><span class="sxs-lookup"><span data-stu-id="021d4-255">https://intranet.contoso.com</span></span> 
    
2. <span data-ttu-id="021d4-256">https://teams.contoso.com</span><span class="sxs-lookup"><span data-stu-id="021d4-256">https://teams.contoso.com</span></span> 
    
3. <span data-ttu-id="021d4-257">https://my.contoso.com</span><span class="sxs-lookup"><span data-stu-id="021d4-257">https://my.contoso.com</span></span>
    
4. <span data-ttu-id="021d4-258">https://partnerweb.contoso.com</span><span class="sxs-lookup"><span data-stu-id="021d4-258">https://partnerweb.contoso.com</span></span> 
    
5. <span data-ttu-id="021d4-259">https://mail.contoso.com \*</span><span class="sxs-lookup"><span data-stu-id="021d4-259">https://mail.contoso.com\*</span></span> 
    
6. <span data-ttu-id="021d4-260">https://dial.contoso.com \*</span><span class="sxs-lookup"><span data-stu-id="021d4-260">https://dial.contoso.com\*</span></span>
    
7. <span data-ttu-id="021d4-261">https://meet.contoso.com \*</span><span class="sxs-lookup"><span data-stu-id="021d4-261">https://meet.contoso.com\*</span></span>
    
* <span data-ttu-id="021d4-262">Exchange URL 有下列的虛擬目錄： 自動探索、 ecp、 EWS、 Microsoft Server ActiveSync、 OAB、 owa、 PowerShell</span><span class="sxs-lookup"><span data-stu-id="021d4-262">The Exchange URL has the following virtual directories: Autodiscover, ecp, EWS, Microsoft-Server-ActiveSync, OAB, owa, PowerShell</span></span> 
  
- <span data-ttu-id="021d4-p136">Lync: TLS DSK] 或 [NTLM 驗證。Lync 用戶端流量會通過閘道路由器 Lync Edge server、 Lync VIP （負載平衡器/反向 proxy 伺服器）]、 [Lync Server。</span><span class="sxs-lookup"><span data-stu-id="021d4-p136">Lync: TLS-DSK or NTLM authentication. The Lync client traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="021d4-p137">SharePoint: Active Directory 網域服務 (AD DS)、 表單型驗證或 SAML 驗證。SharePoint 用戶端流量會通過 VPN 閘道或 DirectAccess 伺服器，SharePoint VIP （負載平衡器/反向 proxy 伺服器）]、 [SharePoint 伺服器。</span><span class="sxs-lookup"><span data-stu-id="021d4-p137">SharePoint: Active Directory Domain Services (AD DS), forms-based authentication, or SAML authentication. The SharePoint client traffic goes through the VPN gateway or the DirectAccess server to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint server.</span></span> 
    
- <span data-ttu-id="021d4-p138">Exchange： 透過 SSL (ActiveSync 自動探索)、 表單型驗證 (OWA) 的基本驗證。Exchange 用戶端流量會通過閘道路由器 Exchange VIP （負載平衡器/反向 proxy 伺服器）]、 [Exchange 伺服器。</span><span class="sxs-lookup"><span data-stu-id="021d4-p138">Exchange: Basic authentication over SSL (ActiveSync, Autodiscover), forms-based authentication (OWA). The Exchange client traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="021d4-269">Lync 用戶端流量會通過至 Lync VIP （負載平衡器/反向 proxy 伺服器），用於 HTTPS 流量所需的硬體負載平衡器]、 [Lync Server 的閘道路由器。</span><span class="sxs-lookup"><span data-stu-id="021d4-269">Lync client traffic goes through the Gateway router to the Lync VIP (load balancer/reverse proxy server) to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="authentication-for-internal-access"></a><span data-ttu-id="021d4-270">內部存取權的驗證</span><span class="sxs-lookup"><span data-stu-id="021d4-270">Authentication for internal access</span></span>

#### <a name="internal-employees"></a><span data-ttu-id="021d4-271">內部員工</span><span class="sxs-lookup"><span data-stu-id="021d4-271">Internal employees</span></span>

> <span data-ttu-id="021d4-272">https://intranet.contoso.com</span><span class="sxs-lookup"><span data-stu-id="021d4-272">https://intranet.contoso.com</span></span> 
    
> <span data-ttu-id="021d4-273">https://teams.contoso.com</span><span class="sxs-lookup"><span data-stu-id="021d4-273">https://teams.contoso.com</span></span> 
    
> <span data-ttu-id="021d4-274">https://my.contoso.com</span><span class="sxs-lookup"><span data-stu-id="021d4-274">https://my.contoso.com</span></span>
    
> <span data-ttu-id="021d4-275">https://partnerweb.contoso.com</span><span class="sxs-lookup"><span data-stu-id="021d4-275">https://partnerweb.contoso.com</span></span>
    
> <span data-ttu-id="021d4-276">https://mail.contoso.com \*</span><span class="sxs-lookup"><span data-stu-id="021d4-276">https://mail.contoso.com\*</span></span> 
    
> <span data-ttu-id="021d4-277">https://dial.contoso.com</span><span class="sxs-lookup"><span data-stu-id="021d4-277">https://dial.contoso.com</span></span> 
    
> <span data-ttu-id="021d4-278">https://meet.contoso.com</span><span class="sxs-lookup"><span data-stu-id="021d4-278">https://meet.contoso.com</span></span>
    
> <span data-ttu-id="021d4-279">https://admin.contoso.com</span><span class="sxs-lookup"><span data-stu-id="021d4-279">https://admin.contoso.com</span></span>
    
- <span data-ttu-id="021d4-p139">Lync: Kerberos]、 [TLS-DSK 或 [NTLM 驗證。Lync 用戶端流量會 Lync VIP （負載平衡器/反向 proxy 伺服器）]、 [Lync Server。</span><span class="sxs-lookup"><span data-stu-id="021d4-p139">Lync: Kerberos, TLS-DSK, or NTLM authentication. The Lync client traffic goes to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="021d4-p140">SharePoint: Active Directory 網域服務 (AD DS)、 表單型驗證或 SAML 驗證。SharePoint 用戶端流量會移至 SharePoint VIP （負載平衡器/反向 proxy 伺服器），然後至 SharePoint 伺服器。</span><span class="sxs-lookup"><span data-stu-id="021d4-p140">SharePoint: Active Directory Domain Services (AD DS), forms-based authentication, or SAML authentication. The SharePoint client traffic goes to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="021d4-p141">Exchange： AD DS 中，表單型驗證。Exchange 用戶端流量會移至 Exchange VIP （負載平衡器/反向 proxy 伺服器），然後 Exchange 伺服器。</span><span class="sxs-lookup"><span data-stu-id="021d4-p141">Exchange: AD DS, forms-based authentication. The Exchange client traffic goes to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="021d4-286">Lync 用戶端流量前往 Lync VIP （負載平衡器/反向 proxy 伺服器），用於 HTTPS 流量所需的硬體負載平衡器]、 [Lync Server。</span><span class="sxs-lookup"><span data-stu-id="021d4-286">Lync client traffic goes to the Lync VIP (load balancer/reverse proxy server) to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="cloud-based-email-traffic"></a><span data-ttu-id="021d4-287">雲端式電子郵件流量</span><span class="sxs-lookup"><span data-stu-id="021d4-287">Cloud-based email traffic</span></span>

<span data-ttu-id="021d4-288">SMTP 式電子郵件流量的雲端架構元件是由架設網際網路郵件或 Exchange Online Protection 所組成。</span><span class="sxs-lookup"><span data-stu-id="021d4-288">The cloud-based component for SMTP-based email traffic consists of either Internet Mail Hosts or Exchange Online Protection.</span></span>
  
<span data-ttu-id="021d4-p142">這些元件移動電子郵件流量網路使用 SMTP。流量會通過閘道路由器 Exchange VIP （負載平衡器/反向 proxy 伺服器）]、 [Exchange 伺服器。</span><span class="sxs-lookup"><span data-stu-id="021d4-p142">These components move email traffic over the network using SMTP. The traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
  
### <a name="network-traffic-legend"></a><span data-ttu-id="021d4-291">網路流量圖例</span><span class="sxs-lookup"><span data-stu-id="021d4-291">Network traffic legend</span></span>

<span data-ttu-id="021d4-292">[圖例] 方塊中以圖形顯示不同類型的流量，如下所示在不同的彩色線條圖所示：</span><span class="sxs-lookup"><span data-stu-id="021d4-292">The legend box graphically shows the different types of traffic depicted on the graph in different colored lines as follows:</span></span> 
  
- <span data-ttu-id="021d4-293">綠色線條： Lync SIP 流量</span><span class="sxs-lookup"><span data-stu-id="021d4-293">Green line: Lync SIP traffic</span></span> 
    
- <span data-ttu-id="021d4-294">藍色線條： Lync Web 流量</span><span class="sxs-lookup"><span data-stu-id="021d4-294">Blue line: Lync Web traffic</span></span> 
    
- <span data-ttu-id="021d4-295">紫色線條： SharePoint 用戶端流量</span><span class="sxs-lookup"><span data-stu-id="021d4-295">Purple line: SharePoint client traffic</span></span> 
    
- <span data-ttu-id="021d4-296">橘色線條： Exchange 用戶端流量</span><span class="sxs-lookup"><span data-stu-id="021d4-296">Orange line: Exchange client traffic</span></span> 
    
- <span data-ttu-id="021d4-297">灰色列： 之間 Exchange 內部部署和 Exchange Online Protection Exchange 信箱伺服器的流量。</span><span class="sxs-lookup"><span data-stu-id="021d4-297">Gray line: Exchange Mail Server traffic between Exchange on-premises and Exchange Online Protection.</span></span> 
    
<span data-ttu-id="021d4-298">[圖例] 方塊中也說明不同類型的流量，所使用的連接埠。</span><span class="sxs-lookup"><span data-stu-id="021d4-298">The different types of traffic and the ports that they use are also described in the legend box.</span></span> 
  
#### <a name="lync-sip-traffic-and-lync-web-traffic"></a><span data-ttu-id="021d4-299">Lync SIP 流量及 Lync web 流量</span><span class="sxs-lookup"><span data-stu-id="021d4-299">Lync SIP traffic and Lync web traffic</span></span>

<span data-ttu-id="021d4-300">Lync Edge Server 會使用下列連接埠的外部使用者通訊：</span><span class="sxs-lookup"><span data-stu-id="021d4-300">The Lync Edge Server uses the following ports for external user communication:</span></span> 
  
- <span data-ttu-id="021d4-301">IM 訊號流量 （SIP/簡易）： TCP 連接埠 443 （輸入流量開放）</span><span class="sxs-lookup"><span data-stu-id="021d4-301">Signaling/IM traffic (SIP/SIMPLE): TCP port 443 (open for inbound traffic)</span></span> 
    
- <span data-ttu-id="021d4-302">Web 會議流量 (PSOM)： TCP 443 （輸入流量的 [開啟]）</span><span class="sxs-lookup"><span data-stu-id="021d4-302">Web conferencing traffic (PSOM): TCP 443 (open for inbound traffic)</span></span> 
    
- <span data-ttu-id="021d4-303">A / V 流量 (SRTP)： TCP 443、 UDP 3478 和 TCP 50000-59999 （選用） （開放的輸入和輸出流量）</span><span class="sxs-lookup"><span data-stu-id="021d4-303">A/V traffic (SRTP): TCP 443, UDP 3478 and TCP 50000-59999 (optional) (open for inbound and outbound traffic)</span></span> 
    
<span data-ttu-id="021d4-304">Lync Edge Server 進行同盟通訊使用下列連接埠：</span><span class="sxs-lookup"><span data-stu-id="021d4-304">Lync Edge Server uses the following ports for federation communication:</span></span> 
  
- <span data-ttu-id="021d4-305">TCP 連接埠 5061 (SIP) 5269 (XMPP) 443 和 UDP 3478 (SRTP) （開放的輸入和輸出流量）</span><span class="sxs-lookup"><span data-stu-id="021d4-305">TCP ports 5061 (SIP), 5269 (XMPP), 443 and UDP 3478 (SRTP) (open for inbound and outbound traffic)</span></span> 
    
#### <a name="sharepoint-client-traffic"></a><span data-ttu-id="021d4-306">SharePoint 用戶端流量</span><span class="sxs-lookup"><span data-stu-id="021d4-306">SharePoint client traffic</span></span>

<span data-ttu-id="021d4-p143">SharePoint 可以用於用戶端與負載平衡器間加密通訊的 TCP 連接埠 443 (SSL)。從網際網路的外部存取，此連接埠必須開啟閘道路由器 （或外部防火牆） 上的輸入和輸出流量。</span><span class="sxs-lookup"><span data-stu-id="021d4-p143">SharePoint can use TCP port 443 (SSL) for encrypted communication between the client and the load balancer. For external access from the Internet, this port needs to be opened for inbound and outbound traffic on the gateway router (or external firewall).</span></span> 
  
#### <a name="exchange-client-traffic-and-exchange-mail-server-traffic"></a><span data-ttu-id="021d4-309">Exchange 用戶端流量及 Exchange 信箱伺服器的流量</span><span class="sxs-lookup"><span data-stu-id="021d4-309">Exchange client traffic and Exchange mail server traffic</span></span>

<span data-ttu-id="021d4-p144">Exchange 會使用 TCP 連接埠 25 (SMTP) 伺服器對伺服器通訊。大部分的用戶端流量 （OWA、 ActiveSync、 自動探索、 「 Outlook 無所不在 」） 會處理透過連接埠 443 (HTTPS)。如果您有 POP 或 IMAP 用戶端，連接埠 110 (POP3)、 995 (加密 POP3)、 143 (IMAP4)、 993 (加密 IMAP4) 及 587 (SMTP) 也可用於支援這些用戶端。</span><span class="sxs-lookup"><span data-stu-id="021d4-p144">Exchange uses TCP port 25 (SMTP) for server-to-server communications. Most client traffic (OWA, ActiveSync, Autodiscover, Outlook Anywhere) is handled over port 443 (HTTPS). If you have POP or IMAP clients, ports 110 (POP3), 995 (encrypted POP3), 143 (IMAP4), 993 (encrypted IMAP4), and 587 (SMTP) are also used to support these clients.</span></span> 
  
#### <a name="more-on-lync-network-traffic"></a><span data-ttu-id="021d4-313">在 Lync 網路流量？</span><span class="sxs-lookup"><span data-stu-id="021d4-313">More on Lync network traffic?</span></span>

<span data-ttu-id="021d4-p145">了解 Lync Server 能如何協助組織提供立即訊息、 web 會議、 應用程式共用和語音通訊。如需詳細資訊，請參閱[Microsoft Lync Server 2013 通訊協定工作量海報 （英文）](https://aka.ms/G5jzjo)。</span><span class="sxs-lookup"><span data-stu-id="021d4-p145">Learn how Lync Server can help your organization provide instant messaging, web conferencing, application sharing, and voice communication. For more information, see [Microsoft Lync Server 2013 Protocol Workloads Poster](https://aka.ms/G5jzjo).</span></span> 
  
<span data-ttu-id="021d4-316">海報也包含說明 QR 程式碼來存取此資訊。</span><span class="sxs-lookup"><span data-stu-id="021d4-316">The poster also includes a QR code to access this information.</span></span> 
  

