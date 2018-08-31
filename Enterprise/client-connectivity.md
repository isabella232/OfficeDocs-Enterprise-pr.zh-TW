---
title: 用戶端連線
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
description: 摘要：說明用戶端電腦如何連線至 Office 365 租用戶 (視用戶端電腦和 Office 365 租用戶資料中心的位置而定)。
ms.openlocfilehash: 9455147e70a391619e1602f2e36d9162ff2c0928
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223035"
---
# <a name="client-connectivity"></a><span data-ttu-id="50980-103">用戶端連線</span><span class="sxs-lookup"><span data-stu-id="50980-103">Client connectivity</span></span>

 <span data-ttu-id="50980-104">**摘要：** 說明用戶端電腦如何連線至 Office 365 租用戶 (視用戶端電腦和 Office 365 租用戶資料中心的位置而定)。</span><span class="sxs-lookup"><span data-stu-id="50980-104">**Summary:** Explains how client computers connect to Office 365 tenants, depending on the location of the client computer and Office 365 tenant datacenter.</span></span>
  
<span data-ttu-id="50980-p101">Office 365 位於 Microsoft 資料中心全球各地以協助保護設定服務] 和 [執行即使地震或電源中斷一個區域中有重大問題。當您連線至 Office 365 租用戶時，用戶端連線會將您導向至適當的資料中心託管租用戶。決定可以主控您的租用戶的規則是由您同意 Microsoft 所定義。決定您的用戶端如何取得該資料中心位置中的資料的規則取決於您正在使用之服務的架構。</span><span class="sxs-lookup"><span data-stu-id="50980-p101">Office 365 resides in Microsoft datacenters around the world which help keep the service up and running even when there's a major problem in one region, such as an earthquake or a power outage. When you connect to your Office 365 tenant, the client connection will be directed to the appropriate datacenter where your tenant is being hosted. The rules that determine where your tenant can be hosted are defined by your agreement with Microsoft. The rules that determine how your client acquires the data from that datacenter location depend on the architecture of the service you're using.</span></span>
  
<span data-ttu-id="50980-p102">例如，當您登入 Office 365 入口網站時，正在通常是連線至用戶端最接近的資料中心，然後依據服務導向您使用下一步]。如果您啟動電子郵件] 來顯示使用者介面的初始連線可能仍是來自於最接近的資料中心，但第二個連線可能會開啟最接近的資料中心與您的租用戶位於何處顯示新的電子郵件中功能您閱讀的資料中心之間。Microsoft 可運作中快速非常 fast 資料中心來 datacenter 連線中所產生的世界上方十個網路的其中一個。</span><span class="sxs-lookup"><span data-stu-id="50980-p102">For example, when you log on to the Office 365 portal, you're usually connected to the closest datacenter to the client and then directed depending on the service you use next. If you launch email, the initial connection to display the UI may still come from the nearest datacenter, but a second connection might be opened between the nearest datacenter and the datacenter where your tenant is located to show you what's in the emails you read. Microsoft operates one of the top ten networks in the world resulting in incredibly fast datacenter-to-datacenter connections fast.</span></span>
  
<span data-ttu-id="50980-112">請閱讀下列文章之後，您可能將瞭解為什麼我們不提供[Office 365 Url 和 IP 位址範圍](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)每個資料中心，他們是只要太互連和依賴彼此進行的合適。</span><span class="sxs-lookup"><span data-stu-id="50980-112">After you read the article, you'll likely understand why we don't provide [Office 365 URLs and IP address ranges](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) per datacenter, they are simply too interconnected and reliant on each other to make that feasible.</span></span>
  
<span data-ttu-id="50980-p103">如果您使用 Azure ExpressRoute for Office 365，在大多數情況下您連線會傳送透過私人連線至 Office 365，而不是此處所述的公用連線。關於如何用戶端連線原則是仍然正確。深入了解[Office 365 的 Azure ExpressRoute](azure-expressroute.md)。</span><span class="sxs-lookup"><span data-stu-id="50980-p103">If you're using Azure ExpressRoute for Office 365, in most cases your connectivity will go over a private connection to Office 365 instead of the public connection described here. The principles about how clients connect are still accurate. Learn more about [Azure ExpressRoute for Office 365](azure-expressroute.md).</span></span>
  
<span data-ttu-id="50980-116">商務網路要求上 Skype 深度，請閱讀下列文章[的媒體品質和 Skype 的商務 Online 中的網路連線效能](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)。</span><span class="sxs-lookup"><span data-stu-id="50980-116">For more depth on Skype for Business network requests, read the article [Media Quality and Network Connectivity Performance in Skype for Business Online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).</span></span>

||
|:-----|
| <span data-ttu-id="50980-117">本文是[網路規劃和 Office 365 的效能調整](https://aka.ms/tune)的一部分。</span><span class="sxs-lookup"><span data-stu-id="50980-117">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

> [!NOTE]
> <span data-ttu-id="50980-p104">我們採用小心以安全並私用在我們的資料中心管理客戶資料。[信任中心](https://go.microsoft.com/fwlink/?LinkID=397383)中所包含有關管理隱私權我們採取哪些的步驟的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="50980-p104">We take great care to manage customer data so it's secure and private in our datacenters. Details about the steps we take to manage privacy are included in the [Trust Center](https://go.microsoft.com/fwlink/?LinkID=397383).</span></span>
  
## <a name="connecting-to-the-nearest-datacenter"></a><span data-ttu-id="50980-120">連線到最接近的資料中心</span><span class="sxs-lookup"><span data-stu-id="50980-120">Connecting to the nearest datacenter</span></span>

<span data-ttu-id="50980-p105">這是最常見的連線、 類型及使用 Office 365 入口網站與 Exchange Online。在此情況下，當用戶端嘗試連線至 Office 365，其電腦的 DNS 查詢會決定來自其電腦，全球的地區與 Office 365 將要求重新導向至最接近的資料中心。</span><span class="sxs-lookup"><span data-stu-id="50980-p105">This is the most common type of connection, and it's used by both the Office 365 portal and Exchange Online. In this situation, when clients attempt to connect to Office 365, their computer's DNS query determines the region of the world their computer is coming from, and Office 365 redirects the request to the nearest datacenter.</span></span>
  
<span data-ttu-id="50980-123">停止在最接近的資料中心的連線至入口網站及用戶端電腦呈現用戶端的租用戶從該位置的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="50980-123">Connections to the portal stop at the nearest datacenter, and the client computer is presented with information about the client's tenant from that location.</span></span>
  
<span data-ttu-id="50980-p106">Exchange Online 會移步驟進一步。一旦用戶端電腦連線到最接近的資料中心，在該資料中心的 Exchange 伺服器連線到資料中心租用戶所在實際上如下圖所示*如何執行此動作處理] 區段中*下方。Exchange Online 中最接近的資料中心則 proxy 伺服器的用戶端電腦的要求至信箱伺服器。所移動的擷取電子郵件和行事曆項目至 Microsoft network 粗活加快用戶端電腦的體驗。</span><span class="sxs-lookup"><span data-stu-id="50980-p106">Exchange Online goes a step further. Once the client computer is connected to the nearest datacenter, an Exchange server in that datacenter connects to the datacenter where the tenant is actually located as illustrated in the  *How does this work section*  below. The Exchange Online servers in the nearest datacenter then proxy the requests from the client computer to the mailbox server. This speeds up the experience for the client computer by moving the heavy lifting of retrieving emails and calendar items to the Microsoft network.</span></span>
  
## <a name="how-does-this-work-for-standard-cloud-offerings"></a><span data-ttu-id="50980-128">這如何運作的標準雲端方案？</span><span class="sxs-lookup"><span data-stu-id="50980-128">How does this work for standard cloud offerings?</span></span>

<span data-ttu-id="50980-p107">這個連線程序是高流量的標準高價值的 web 應用程式 like Office 365。在本節，我們及大綱說明程序中的步驟。當用戶端電腦不會為承租人的相同區域中時，會尋找更加不同根據用戶端連線至服務連線。</span><span class="sxs-lookup"><span data-stu-id="50980-p107">This connection process is standard for high traffic, high value web applications like Office 365. In this section, we outline and illustrate the steps in the process. When the client computer is not in the same region as the tenant, the connection looks much different depending on the service the client is connecting to.</span></span>
  
 <span data-ttu-id="50980-p108">此圖說明客戶使用標準的 Office 365 可以與 「 北美地區 」 中的租用戶。在此案例中，進行要求的人員旅行 Europe 已經過及使用 Office 365 從該位置。</span><span class="sxs-lookup"><span data-stu-id="50980-p108">This diagram depicts a customer using a standard Office 365 offering with a tenant in North America. In this scenario, the person making the request has traveled to Europe and is using Office 365 from that location.</span></span>
  
1. <span data-ttu-id="50980-134">用戶端電腦向本機 DNS 伺服器詢問與 Office 365 關聯的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="50980-134">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="50980-135">用戶端電腦的本機 DNS 伺服器會向 Microsoft DNS 伺服器詢問與 Office 365 相關聯的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="50980-135">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="50980-136">Microsoft 的 DNS 伺服器傳回區域性伺服器名稱 （根據用戶端的 DNS 伺服器的位置），而且用戶端電腦會重複步驟 1 和 2 來取得地區的 Office 365 資料中心的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="50980-136">Microsoft's DNS servers return the regional server name (based on the location of the client's DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="50980-137">用戶端電腦連線到地區資料中心 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="50980-137">The client computer connects to the regional datacenter IP address.</span></span>

5. <span data-ttu-id="50980-138">Exchange Online 伺服器連線到客戶的租用戶所在的作用中資料中心。</span><span class="sxs-lookup"><span data-stu-id="50980-138">The Exchange Online servers establish a connection to the active datacenter where the customer's tenant resides.</span></span>

![最接近地區性資料中心](media/4ea108e9-a299-4e3d-b0d3-469b434ff899.png)
  
## <a name="how-does-this-work-for-sovereign-cloud-offerings"></a><span data-ttu-id="50980-140">這項工作的 sovereign 如何雲端方案？</span><span class="sxs-lookup"><span data-stu-id="50980-140">How does this work for sovereign cloud offerings?</span></span>

<span data-ttu-id="50980-p109">此連線的例如 Office 365 21vianet 來 21 Vianet 統領雲端方案稍微不同。與 Office 365 統領執行個體中承租人，請將接受入口網站連線的最接近 Office 365 伺服器為統領租用戶所在的區域中的伺服器。同樣地，存取 SharePoint Online 我們統領雲端或標準版方案中的客戶會導向到租用戶所在的前端伺服器。請參閱連線到使用中的資料中心下。</span><span class="sxs-lookup"><span data-stu-id="50980-p109">This connection is slightly different for sovereign cloud offerings such as Office 365 operated by 21 Vianet. With the tenant in a sovereign instance of Office 365, the nearest Office 365 servers that will accept portal connections are the servers within the sovereign region where the tenant resides. Similarly, customers accessing SharePoint Online in our sovereign cloud or standard offerings will be directed to front end servers where the tenant resides. See connecting to the active datacenter below.</span></span>
  
1. <span data-ttu-id="50980-145">用戶端電腦向本機 DNS 伺服器詢問與 Office 365 關聯的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="50980-145">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="50980-146">用戶端電腦的本機 DNS 伺服器會向 Microsoft DNS 伺服器詢問與 Office 365 相關聯的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="50980-146">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="50980-147">Microsoft 的 DNS 伺服器傳回區域性伺服器名稱 （根據用戶端的 DNS 伺服器的位置），而且用戶端電腦會重複步驟 1 和 2 來取得地區的 Office 365 資料中心的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="50980-147">Microsoft's DNS servers return the regional server name (based on the location of the client's DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="50980-148">用戶端電腦連線到地區資料中心 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="50980-148">The client computer connects to the regional datacenter IP address.</span></span>

5. <span data-ttu-id="50980-149">Exchange Online 伺服器連線到客戶的租用戶所在的作用中資料中心。</span><span class="sxs-lookup"><span data-stu-id="50980-149">The Exchange Online servers establish a connection to the active datacenter where the customer's tenant resides.</span></span>

![最接近地區性 US 資料中心](media/c0628c54-0059-48c5-8a0f-41bf392ee182.png)
  
## <a name="connecting-to-the-active-datacenter"></a><span data-ttu-id="50980-151">連線到使用中的資料中心</span><span class="sxs-lookup"><span data-stu-id="50980-151">Connecting to the active datacenter</span></span>

<span data-ttu-id="50980-p110">連線到使用中的資料中心的粗資料傳輸工作負載的設計與目前使用的 SharePoint Online。在此情況下，當用戶端嘗試連線至 Office 365 其瀏覽器會重新導向至使用中的資料中心其 SharePoint Online 的租用戶。</span><span class="sxs-lookup"><span data-stu-id="50980-p110">Connecting to the active datacenter is designed for heavier data transfer workloads and is currently used by SharePoint Online. In this situation, when clients attempt to connect to Office 365, their browser is redirected to the active datacenter for their SharePoint Online tenant.</span></span>
  
## <a name="how-does-this-work"></a><span data-ttu-id="50980-154">這如何運作？</span><span class="sxs-lookup"><span data-stu-id="50980-154">How does this work?</span></span>

<span data-ttu-id="50980-p111">當用戶端電腦從不同的地區連線到 SharePoint Online 時，連線會重新導向至使用中的 SharePoint Online 資料中心。在此案例中，客戶使用標準提供、 產生本機剩餘的入口網站連線和 SharePoint Online 被導向到使用中的資料中心的連線。</span><span class="sxs-lookup"><span data-stu-id="50980-p111">When the client computer is connecting to SharePoint Online from a different region, the connection is redirected to the active SharePoint Online datacenter. In this scenario, the customer is using a standard offering, resulting in the portal connections remaining local and the SharePoint Online connections being directed to the active datacenter.</span></span>
  
1. <span data-ttu-id="50980-157">用戶端電腦向本機 DNS 伺服器詢問與 Office 365 關聯的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="50980-157">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="50980-158">用戶端電腦的本機 DNS 伺服器會向 Microsoft DNS 伺服器詢問與 Office 365 相關聯的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="50980-158">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="50980-159">Microsoft 的 DNS 伺服器傳回使用中的 SharePoint Online 資料中心 （根據用戶端的 Office 365 租用戶的位置，） 的伺服器名稱和用戶端電腦會重複步驟 1 和 2 來取得使用中的 Office 365 資料中心的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="50980-159">Microsoft's DNS servers return the server name of the active SharePoint Online datacenter (based on the location of the client's Office 365 tenant), and the client computer repeats steps 1 and 2 to obtain the IP address of the active Office 365 datacenter.</span></span>

4. <span data-ttu-id="50980-160">用戶端電腦連線到使用中資料中心 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="50980-160">The client computer connects to the active datacenter IP address.</span></span>

![使用中 US 資料中心](media/c6d2933f-49cb-4536-bea7-c868707755ae.png)
  
## <a name="connecting-over-virtual-private-networks-vpns"></a><span data-ttu-id="50980-162">透過虛擬私人網路 (VPN) 連線</span><span class="sxs-lookup"><span data-stu-id="50980-162">Connecting over Virtual Private Networks (VPNs)</span></span>

<span data-ttu-id="50980-p112">這種連線類型適用於使用時才虛擬私人網路 (VPN) 用戶端電腦。在現實、 Office 365 行為不只是變更因為使用 VPN 時，但 Vpn 通常用來控制用戶端電腦的效能降低體驗所建立的連線至 Office 365 和通常結果，因此請務必涵蓋。</span><span class="sxs-lookup"><span data-stu-id="50980-p112">This type of connection applies only when a virtual private network (VPN) is used by client computers. In reality, Office 365 behavior isn't changed simply because a VPN is used, but VPNs are commonly used to control how client computers establish connections to Office 365 and usually results in a degraded experience, so it's important to cover.</span></span>
  
## <a name="how-does-this-work"></a><span data-ttu-id="50980-165">這如何運作？</span><span class="sxs-lookup"><span data-stu-id="50980-165">How does this work?</span></span>

<span data-ttu-id="50980-p113">當用戶端電腦建立不同的區域中的公司辦公室的 VPN 連線時，該 office 中的 DNS 伺服器可用，而不是在用戶端電腦的位置之 DNS 伺服器。在大多數情況下，透過 VPN 此額外連線將會降低的 Office 365 經驗。Office 365 服務已最佳化來做為接近儘可能將一般使用者的服務客戶連線。許多服務利用 Azure 邊緣網路、 內容傳遞網路，與 Microsoft network 可靠的網路容量將接近用戶端電腦位置進行 Office 365 服務的網路要求時傳送最佳可能的使用者經驗儘可能。</span><span class="sxs-lookup"><span data-stu-id="50980-p113">When the client computer establishes a VPN connection to a corporate office in a different region, the DNS servers at that office are used instead of the DNS servers at the client computer's location. In most cases, this extra connection over the VPN will degrade the Office 365 experience. The Office 365 services are optimized to service customer connections as close to the end user as possible. Many services leverage the Azure edge network, Content Delivery Networks, and the reliable network capacity on the Microsoft network to deliver the best possible user experience when network requests for Office 365 services are made as close to the client computer as possible.</span></span>
  
1. <span data-ttu-id="50980-170">用戶端電腦 VPN 向 DNS 伺服器詢問與 Office 365 關聯的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="50980-170">The client computer asks the VPN DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="50980-171">用戶端電腦的 VPN DNS 伺服器會向 Microsoft DNS 伺服器詢問與 Office 365 相關聯的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="50980-171">The client computer's VPN DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="50980-172">Microsoft 的 DNS 伺服器傳回區域性伺服器名稱 （根據 VPN DNS 伺服器的位置），而且用戶端電腦會重複步驟 1 和 2 來取得地區的 Office 365 資料中心的 IP 位址資訊。</span><span class="sxs-lookup"><span data-stu-id="50980-172">Microsoft's DNS servers return the regional server name (based on the location of the VPN DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address information of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="50980-173">用戶端電腦連線到資料中心最接近的公司辦公室他們使用 VPN 連線的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="50980-173">The client computer connects to the datacenter IP address that's closest to the corporate office they established a VPN connection with.</span></span>

![VPN 資料中心連線性](media/b5f4c06c-65a3-462d-aae8-9a4602dd8d9e.png)
  
<span data-ttu-id="50980-175">以下是您可以使用回來的簡短連結：[https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)</span><span class="sxs-lookup"><span data-stu-id="50980-175">Here's a short link you can use to come back: [https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="50980-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50980-176">See also</span></span>

[<span data-ttu-id="50980-177">管理 Office 365 端點</span><span class="sxs-lookup"><span data-stu-id="50980-177">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="50980-178">對 Office 365 的網路連線</span><span class="sxs-lookup"><span data-stu-id="50980-178">Network connectivity to Office 365</span></span>](network-connectivity.md)
