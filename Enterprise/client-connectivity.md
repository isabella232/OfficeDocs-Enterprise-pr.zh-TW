---
title: 用戶端連線能力
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 4232abcf-4ae5-43aa-bfa1-9a078a99c78b
description: 摘要： 說明用戶端電腦如何連線至 Office 365 租用戶，根據用戶端電腦與 Office 365 租用戶資料中心的位置。
ms.openlocfilehash: 9455147e70a391619e1602f2e36d9162ff2c0928
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490561"
---
# <a name="client-connectivity"></a><span data-ttu-id="df7db-103">用戶端連線能力</span><span class="sxs-lookup"><span data-stu-id="df7db-103">Client connectivity</span></span>

 <span data-ttu-id="df7db-104">**摘要：** 說明用戶端電腦如何連線至 Office 365 租用戶，根據用戶端電腦與 Office 365 租用戶資料中心的位置。</span><span class="sxs-lookup"><span data-stu-id="df7db-104">**Summary:** Explains how client computers connect to Office 365 tenants, depending on the location of the client computer and Office 365 tenant datacenter.</span></span>
  
<span data-ttu-id="df7db-105">Office 365 位於 Microsoft 資料中心世界各地的可協助保護設定的服務，並執行即使在一個區域，例如地震或電源中斷中沒有發生重大的問題。</span><span class="sxs-lookup"><span data-stu-id="df7db-105">Office 365 resides in Microsoft datacenters around the world which help keep the service up and running even when there's a major problem in one region, such as an earthquake or a power outage.</span></span> <span data-ttu-id="df7db-106">當您連接至您的 Office 365 租用戶時，用戶端連線會被導向適當的資料中心正在主控您的租用戶。</span><span class="sxs-lookup"><span data-stu-id="df7db-106">When you connect to your Office 365 tenant, the client connection will be directed to the appropriate datacenter where your tenant is being hosted.</span></span> <span data-ttu-id="df7db-107">決定可以主控您的租用戶規則是由 Microsoft 與您合約定義。</span><span class="sxs-lookup"><span data-stu-id="df7db-107">The rules that determine where your tenant can be hosted are defined by your agreement with Microsoft.</span></span> <span data-ttu-id="df7db-108">規則，判斷您的用戶端如何取得從該資料中心位置的資料會因您正在使用的服務架構而定。</span><span class="sxs-lookup"><span data-stu-id="df7db-108">The rules that determine how your client acquires the data from that datacenter location depend on the architecture of the service you're using.</span></span>
  
<span data-ttu-id="df7db-109">例如，當您登入 Office 365 入口網站時，您是通常是連接到最接近的資料中心，用戶端，而且再根據服務導向您使用下一步]。</span><span class="sxs-lookup"><span data-stu-id="df7db-109">For example, when you log on to the Office 365 portal, you're usually connected to the closest datacenter to the client and then directed depending on the service you use next.</span></span> <span data-ttu-id="df7db-110">如果您啟動電子郵件時，顯示 UI 的初始連線可能仍是來自於最接近的資料中心，但可能最接近的資料中心與以顯示您功能的電子郵件您閱讀中位於到您的租用戶資料中心之間開啟第二個連線。</span><span class="sxs-lookup"><span data-stu-id="df7db-110">If you launch email, the initial connection to display the UI may still come from the nearest datacenter, but a second connection might be opened between the nearest datacenter and the datacenter where your tenant is located to show you what's in the emails you read.</span></span> <span data-ttu-id="df7db-111">Microsoft 會執行下列其中一個非常快速資料中心到 datacenter 連線速度產生領域中的頂端十個網路。</span><span class="sxs-lookup"><span data-stu-id="df7db-111">Microsoft operates one of the top ten networks in the world resulting in incredibly fast datacenter-to-datacenter connections fast.</span></span>
  
<span data-ttu-id="df7db-112">閱讀本文之後，您可能了解為什麼我們不提供[Office 365 Url 和 IP 位址範圍](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)每個資料中心，只要是太互連和依賴彼此進行的可行的情況下。</span><span class="sxs-lookup"><span data-stu-id="df7db-112">After you read the article, you'll likely understand why we don't provide [Office 365 URLs and IP address ranges](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) per datacenter, they are simply too interconnected and reliant on each other to make that feasible.</span></span>
  
<span data-ttu-id="df7db-113">如果您使用 Azure ExpressRoute for Office 365，在大部分情況下您連線會透過私人連線移至 [Office 365 而不是此處所述的公用連線。</span><span class="sxs-lookup"><span data-stu-id="df7db-113">If you're using Azure ExpressRoute for Office 365, in most cases your connectivity will go over a private connection to Office 365 instead of the public connection described here.</span></span> <span data-ttu-id="df7db-114">有關如何用戶端連線原則仍然正確。</span><span class="sxs-lookup"><span data-stu-id="df7db-114">The principles about how clients connect are still accurate.</span></span> <span data-ttu-id="df7db-115">深入了解[Azure ExpressRoute for Office 365](azure-expressroute.md)。</span><span class="sxs-lookup"><span data-stu-id="df7db-115">Learn more about [Azure ExpressRoute for Office 365](azure-expressroute.md).</span></span>
  
<span data-ttu-id="df7db-116">針對上深入 Skype for Business 的網路要求，請閱讀 <<c0>媒體品質和網路連線效能 skype for Business Online。</span><span class="sxs-lookup"><span data-stu-id="df7db-116">For more depth on Skype for Business network requests, read the article [Media Quality and Network Connectivity Performance in Skype for Business Online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).</span></span>

||
|:-----|
| <span data-ttu-id="df7db-117">本文是[網路規劃和效能調整的 Office 365](https://aka.ms/tune)的一部分。</span><span class="sxs-lookup"><span data-stu-id="df7db-117">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

> [!NOTE]
> <span data-ttu-id="df7db-118">我們小心謹慎來管理客戶資料，所以很安全且私用在我們的資料中心。</span><span class="sxs-lookup"><span data-stu-id="df7db-118">We take great care to manage customer data so it's secure and private in our datacenters.</span></span> <span data-ttu-id="df7db-119">我們採取的步驟來管理隱私權詳細隨附[的 [信任中心](https://go.microsoft.com/fwlink/?LinkID=397383)] 中。</span><span class="sxs-lookup"><span data-stu-id="df7db-119">Details about the steps we take to manage privacy are included in the [Trust Center](https://go.microsoft.com/fwlink/?LinkID=397383).</span></span>
  
## <a name="connecting-to-the-nearest-datacenter"></a><span data-ttu-id="df7db-120">連線到最接近的資料中心</span><span class="sxs-lookup"><span data-stu-id="df7db-120">Connecting to the nearest datacenter</span></span>

<span data-ttu-id="df7db-121">這是最常見的連線，類型，它由 Office 365 入口網站和 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="df7db-121">This is the most common type of connection, and it's used by both the Office 365 portal and Exchange Online.</span></span> <span data-ttu-id="df7db-122">在此情況下，當用戶端嘗試連線到 Office 365，其電腦的 DNS 查詢決定來自他們的電腦，全球的區域和 Office 365 會要求重新導向到最接近的資料中心。</span><span class="sxs-lookup"><span data-stu-id="df7db-122">In this situation, when clients attempt to connect to Office 365, their computer's DNS query determines the region of the world their computer is coming from, and Office 365 redirects the request to the nearest datacenter.</span></span>
  
<span data-ttu-id="df7db-123">連線至入口網站最接近的資料中心，在停止和用戶端電腦呈現用戶端的租用戶，從該位置的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="df7db-123">Connections to the portal stop at the nearest datacenter, and the client computer is presented with information about the client's tenant from that location.</span></span>
  
<span data-ttu-id="df7db-124">Exchange Online 移步驟更進一步。</span><span class="sxs-lookup"><span data-stu-id="df7db-124">Exchange Online goes a step further.</span></span> <span data-ttu-id="df7db-125">當用戶端電腦已連接到最接近的資料中心之後時，該資料中心中的 Exchange 伺服器連接到資料中心租用戶所在實際所示*如何執行此工作] 區段中*下方。</span><span class="sxs-lookup"><span data-stu-id="df7db-125">Once the client computer is connected to the nearest datacenter, an Exchange server in that datacenter connects to the datacenter where the tenant is actually located as illustrated in the  *How does this work section*  below.</span></span> <span data-ttu-id="df7db-126">Exchange Online 中最接近的資料中心然後 proxy 伺服器的用戶端電腦的要求至 mailbox server。</span><span class="sxs-lookup"><span data-stu-id="df7db-126">The Exchange Online servers in the nearest datacenter then proxy the requests from the client computer to the mailbox server.</span></span> <span data-ttu-id="df7db-127">移動工作都擷取電子郵件和行事曆項目至 Microsoft 網路加快用戶端電腦的體驗。</span><span class="sxs-lookup"><span data-stu-id="df7db-127">This speeds up the experience for the client computer by moving the heavy lifting of retrieving emails and calendar items to the Microsoft network.</span></span>
  
## <a name="how-does-this-work-for-standard-cloud-offerings"></a><span data-ttu-id="df7db-128">此標準的雲端供應項目的運作方式？</span><span class="sxs-lookup"><span data-stu-id="df7db-128">How does this work for standard cloud offerings?</span></span>

<span data-ttu-id="df7db-129">這個連線程序是高流量的標準高價值的 web 應用程式像是 Office 365。</span><span class="sxs-lookup"><span data-stu-id="df7db-129">This connection process is standard for high traffic, high value web applications like Office 365.</span></span> <span data-ttu-id="df7db-130">在這個部分，我們大綱，並說明程序中的步驟。</span><span class="sxs-lookup"><span data-stu-id="df7db-130">In this section, we outline and illustrate the steps in the process.</span></span> <span data-ttu-id="df7db-131">當用戶端電腦不在租用戶的相同區域中時，連線會尋找許多不同根據用戶端連線至服務。</span><span class="sxs-lookup"><span data-stu-id="df7db-131">When the client computer is not in the same region as the tenant, the connection looks much different depending on the service the client is connecting to.</span></span>
  
 <span data-ttu-id="df7db-132">此圖說明 「 北美地區 」 中的租用戶中使用標準的 Office 365 提供客戶。</span><span class="sxs-lookup"><span data-stu-id="df7db-132">This diagram depicts a customer using a standard Office 365 offering with a tenant in North America.</span></span> <span data-ttu-id="df7db-133">在此案例中，提出要求的人員旅行歐洲已經過，且正在使用 Office 365 從該位置。</span><span class="sxs-lookup"><span data-stu-id="df7db-133">In this scenario, the person making the request has traveled to Europe and is using Office 365 from that location.</span></span>
  
1. <span data-ttu-id="df7db-134">用戶端電腦向本機 DNS 伺服器詢問與 Office 365 相關聯的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="df7db-134">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="df7db-135">用戶端電腦的本機 DNS 伺服器向 Microsoft DNS 伺服器詢問與 Office 365 相關聯的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="df7db-135">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="df7db-136">Microsoft 的 DNS 伺服器傳回地區伺服器名稱 （根據用戶端的 DNS 伺服器的位置），而用戶端電腦重複步驟 1 和 2 來取得地區的 Office 365 資料中心的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="df7db-136">Microsoft's DNS servers return the regional server name (based on the location of the client's DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="df7db-137">用戶端電腦連線到地區資料中心 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="df7db-137">The client computer connects to the regional datacenter IP address.</span></span>

5. <span data-ttu-id="df7db-138">Exchange Online 的伺服器連線到客戶的租用戶所在的作用中資料中心。</span><span class="sxs-lookup"><span data-stu-id="df7db-138">The Exchange Online servers establish a connection to the active datacenter where the customer's tenant resides.</span></span>

![最接近地區性資料中心](media/4ea108e9-a299-4e3d-b0d3-469b434ff899.png)
  
## <a name="how-does-this-work-for-sovereign-cloud-offerings"></a><span data-ttu-id="df7db-140">這項工作的主權如何雲端供應項目？</span><span class="sxs-lookup"><span data-stu-id="df7db-140">How does this work for sovereign cloud offerings?</span></span>

<span data-ttu-id="df7db-141">此連線是稍有不同的統領雲端供應項目，例如由 21 Vianet 運作的 Office 365。</span><span class="sxs-lookup"><span data-stu-id="df7db-141">This connection is slightly different for sovereign cloud offerings such as Office 365 operated by 21 Vianet.</span></span> <span data-ttu-id="df7db-142">Office 365 的統領執行個體中的租用戶，最接近的 Office 365 伺服器會接受入口網站的連線，有租用戶所在的統領區域內的伺服器。</span><span class="sxs-lookup"><span data-stu-id="df7db-142">With the tenant in a sovereign instance of Office 365, the nearest Office 365 servers that will accept portal connections are the servers within the sovereign region where the tenant resides.</span></span> <span data-ttu-id="df7db-143">同樣地，存取 SharePoint Online 我們統領雲端或標準供應項目中的客戶會導向至租用戶所在的前端伺服器。</span><span class="sxs-lookup"><span data-stu-id="df7db-143">Similarly, customers accessing SharePoint Online in our sovereign cloud or standard offerings will be directed to front end servers where the tenant resides.</span></span> <span data-ttu-id="df7db-144">請參閱連線到以下作用中的資料中心。</span><span class="sxs-lookup"><span data-stu-id="df7db-144">See connecting to the active datacenter below.</span></span>
  
1. <span data-ttu-id="df7db-145">用戶端電腦向本機 DNS 伺服器詢問與 Office 365 相關聯的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="df7db-145">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="df7db-146">用戶端電腦的本機 DNS 伺服器向 Microsoft DNS 伺服器詢問與 Office 365 相關聯的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="df7db-146">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="df7db-147">Microsoft 的 DNS 伺服器傳回地區伺服器名稱 （根據用戶端的 DNS 伺服器的位置），而用戶端電腦重複步驟 1 和 2 來取得地區的 Office 365 資料中心的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="df7db-147">Microsoft's DNS servers return the regional server name (based on the location of the client's DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="df7db-148">用戶端電腦連線到地區資料中心 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="df7db-148">The client computer connects to the regional datacenter IP address.</span></span>

5. <span data-ttu-id="df7db-149">Exchange Online 的伺服器連線到客戶的租用戶所在的作用中資料中心。</span><span class="sxs-lookup"><span data-stu-id="df7db-149">The Exchange Online servers establish a connection to the active datacenter where the customer's tenant resides.</span></span>

![最接近地區性 US 資料中心](media/c0628c54-0059-48c5-8a0f-41bf392ee182.png)
  
## <a name="connecting-to-the-active-datacenter"></a><span data-ttu-id="df7db-151">連線到使用中的資料中心</span><span class="sxs-lookup"><span data-stu-id="df7db-151">Connecting to the active datacenter</span></span>

<span data-ttu-id="df7db-152">連線到使用中的資料中心針對重型資料傳輸工作負載和目前由 SharePoint Online 使用。</span><span class="sxs-lookup"><span data-stu-id="df7db-152">Connecting to the active datacenter is designed for heavier data transfer workloads and is currently used by SharePoint Online.</span></span> <span data-ttu-id="df7db-153">在此情況下，當用戶端嘗試連線至 Office 365，其瀏覽器重新導向至使用中的資料中心其 SharePoint Online 租用戶。</span><span class="sxs-lookup"><span data-stu-id="df7db-153">In this situation, when clients attempt to connect to Office 365, their browser is redirected to the active datacenter for their SharePoint Online tenant.</span></span>
  
## <a name="how-does-this-work"></a><span data-ttu-id="df7db-154">這如何運作？</span><span class="sxs-lookup"><span data-stu-id="df7db-154">How does this work?</span></span>

<span data-ttu-id="df7db-155">當用戶端電腦連線到 SharePoint Online 上，從不同的地區時，連線會重新導向至使用中的 SharePoint Online 資料中心。</span><span class="sxs-lookup"><span data-stu-id="df7db-155">When the client computer is connecting to SharePoint Online from a different region, the connection is redirected to the active SharePoint Online datacenter.</span></span> <span data-ttu-id="df7db-156">在此案例中，客戶會使用標準提供、 產生剩餘本機的入口網站連線並被導向到使用中的資料中心的 SharePoint Online 連線。</span><span class="sxs-lookup"><span data-stu-id="df7db-156">In this scenario, the customer is using a standard offering, resulting in the portal connections remaining local and the SharePoint Online connections being directed to the active datacenter.</span></span>
  
1. <span data-ttu-id="df7db-157">用戶端電腦向本機 DNS 伺服器詢問與 Office 365 相關聯的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="df7db-157">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="df7db-158">用戶端電腦的本機 DNS 伺服器向 Microsoft DNS 伺服器詢問與 Office 365 相關聯的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="df7db-158">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="df7db-159">Microsoft 的 DNS 伺服器傳回 （根據用戶端的 Office 365 租用戶的位置），在作用中 SharePoint Online 資料中心的伺服器名稱和用戶端電腦重複步驟 1 和 2 來取得使用中的 Office 365 資料中心的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="df7db-159">Microsoft's DNS servers return the server name of the active SharePoint Online datacenter (based on the location of the client's Office 365 tenant), and the client computer repeats steps 1 and 2 to obtain the IP address of the active Office 365 datacenter.</span></span>

4. <span data-ttu-id="df7db-160">用戶端電腦連線到使用中的資料中心 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="df7db-160">The client computer connects to the active datacenter IP address.</span></span>

![使用中 US 資料中心](media/c6d2933f-49cb-4536-bea7-c868707755ae.png)
  
## <a name="connecting-over-virtual-private-networks-vpns"></a><span data-ttu-id="df7db-162">透過虛擬私人網路 (Vpn) 連線</span><span class="sxs-lookup"><span data-stu-id="df7db-162">Connecting over Virtual Private Networks (VPNs)</span></span>

<span data-ttu-id="df7db-163">此類型的連線適用於僅當虛擬私人網路 (VPN) 由用戶端電腦。</span><span class="sxs-lookup"><span data-stu-id="df7db-163">This type of connection applies only when a virtual private network (VPN) is used by client computers.</span></span> <span data-ttu-id="df7db-164">在現實情況下，Office 365 行為不只是變更因為使用 VPN 時，但 Vpn 通常用來控制用戶端電腦如何建立連線至 Office 365 和通常結果降級的經驗，因此請務必涵蓋。</span><span class="sxs-lookup"><span data-stu-id="df7db-164">In reality, Office 365 behavior isn't changed simply because a VPN is used, but VPNs are commonly used to control how client computers establish connections to Office 365 and usually results in a degraded experience, so it's important to cover.</span></span>
  
## <a name="how-does-this-work"></a><span data-ttu-id="df7db-165">這如何運作？</span><span class="sxs-lookup"><span data-stu-id="df7db-165">How does this work?</span></span>

<span data-ttu-id="df7db-166">當用戶端電腦透過 VPN 連線到位於不同地區的公司辦公室時，而不是在用戶端電腦的位置上的 DNS 伺服器使用位於該辦公室的 DNS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="df7db-166">When the client computer establishes a VPN connection to a corporate office in a different region, the DNS servers at that office are used instead of the DNS servers at the client computer's location.</span></span> <span data-ttu-id="df7db-167">在大多數情況下，此額外透過 VPN 連線將會降低 Office 365 體驗。</span><span class="sxs-lookup"><span data-stu-id="df7db-167">In most cases, this extra connection over the VPN will degrade the Office 365 experience.</span></span> <span data-ttu-id="df7db-168">Office 365 服務已為使用者盡可能接近的服務客戶連線進行最佳化。</span><span class="sxs-lookup"><span data-stu-id="df7db-168">The Office 365 services are optimized to service customer connections as close to the end user as possible.</span></span> <span data-ttu-id="df7db-169">有許多服務利用 Azure 的邊緣網路、 內容傳遞網路和 Microsoft 網路上的可靠的網路容量，最接近的用戶端電腦進行 Office 365 服務的網路要求時傳送的最佳的可能的使用者經驗盡可能。</span><span class="sxs-lookup"><span data-stu-id="df7db-169">Many services leverage the Azure edge network, Content Delivery Networks, and the reliable network capacity on the Microsoft network to deliver the best possible user experience when network requests for Office 365 services are made as close to the client computer as possible.</span></span>
  
1. <span data-ttu-id="df7db-170">用戶端電腦要求 VPN DNS 伺服器與 Office 365 相關聯的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="df7db-170">The client computer asks the VPN DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="df7db-171">用戶端電腦的 VPN DNS 伺服器向 Microsoft DNS 伺服器詢問與 Office 365 相關聯的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="df7db-171">The client computer's VPN DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="df7db-172">Microsoft 的 DNS 伺服器傳回地區伺服器名稱 （根據 VPN DNS 伺服器的位置），以及用戶端電腦重複步驟 1 和 2 來取得地區的 Office 365 資料中心的 IP 位址資訊。</span><span class="sxs-lookup"><span data-stu-id="df7db-172">Microsoft's DNS servers return the regional server name (based on the location of the VPN DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address information of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="df7db-173">用戶端電腦連線到資料中心他們建立與 VPN 連線的公司辦公室最接近的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="df7db-173">The client computer connects to the datacenter IP address that's closest to the corporate office they established a VPN connection with.</span></span>

![VPN 資料中心連線性](media/b5f4c06c-65a3-462d-aae8-9a4602dd8d9e.png)
  
<span data-ttu-id="df7db-175">您可以使用下列短連結返回這裡：[https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)</span><span class="sxs-lookup"><span data-stu-id="df7db-175">Here's a short link you can use to come back: [https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="df7db-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df7db-176">See also</span></span>

[<span data-ttu-id="df7db-177">管理 Office 365 端點</span><span class="sxs-lookup"><span data-stu-id="df7db-177">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="df7db-178">對 Office 365 的網路連線</span><span class="sxs-lookup"><span data-stu-id="df7db-178">Network connectivity to Office 365</span></span>](network-connectivity.md)
