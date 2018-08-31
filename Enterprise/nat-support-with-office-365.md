---
title: Office 365 的 NAT 支援
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 1/24/2017
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: 摘要：提供如何約略算出使用網路位址轉譯 (NAT) 的組織內每個 IP 位址所能使用的正確用戶端數目的詳細資訊。
ms.openlocfilehash: 733d591bded599cfaece988a624baa7a3c0d4b06
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539912"
---
# <a name="nat-support-with-office-365"></a><span data-ttu-id="a5bb9-103">Office 365 的 NAT 支援</span><span class="sxs-lookup"><span data-stu-id="a5bb9-103">NAT support with Office 365</span></span>

 <span data-ttu-id="a5bb9-104">**摘要：** 提供如何約略算出使用網路位址轉譯 (NAT) 的組織內每個 IP 位址所能使用的正確用戶端數目的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="a5bb9-104">**Summary:** Provides details about how to approximate the correct number of clients you can use per IP address within your organization using Network Address Translation (NAT).</span></span> 
  
<span data-ttu-id="a5bb9-105">先前、 指引建議您應該使用每個 IP 位址來連線至 Office 365 的 Exchange 用戶端的數目上限是每個網路連接埠約 2000 個用戶端。</span><span class="sxs-lookup"><span data-stu-id="a5bb9-105">Previously, guidance suggested that the maximum number of Exchange clients you should use per IP address to connect to Office 365 was about 2,000 clients per network port.</span></span>
  
## <a name="why-use-nat"></a><span data-ttu-id="a5bb9-106">為什麼要使用 NAT？</span><span class="sxs-lookup"><span data-stu-id="a5bb9-106">Why use NAT?</span></span>

<span data-ttu-id="a5bb9-107">藉由使用 NAT，公司網路上的數以千計可以 「 共用 」 一些可公開路由傳送的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="a5bb9-107">By using NAT, thousands of people on a corporate network can "share" a few publicly routable IP addresses.</span></span>
  
<span data-ttu-id="a5bb9-p101">大部分的公司網路都使用私人 (RFC1918) IP 位址空間。私人位址空間是由網際網路指定編號機構 (IANA) 配置的，其僅供與全球網際網路未直接路由傳送的網路使用。</span><span class="sxs-lookup"><span data-stu-id="a5bb9-p101">Most corporate networks use private (RFC1918) IP address space. Private address space is allocated by the Internet Assigned Numbers Authority (IANA) and intended solely for networks that do not route directly to and from the global Internet.</span></span>
  
<span data-ttu-id="a5bb9-p102">若要提供裝置存取網際網路上的私人 IP 位址空間，組織會使用閘道技術防火牆及 proxy 提供網路位址轉譯 (NAT) 或連接埠位址轉譯 (PAT) 服務。這些閘道進行來自內部流量裝置 （包括 Office 365） 網際網路似乎來自一或多個可公開路由傳送的 IP 位址。每個來自內部裝置的輸出連線會轉譯為不同的來源 TCP 連接埠上的公用 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="a5bb9-p102">To provide Internet access to devices on a private IP address space, organizations use gateway technologies like firewalls and proxies that provide network address translation (NAT) or port address translation (PAT) services. These gateways make traffic from internal devices to the Internet (including Office 365) appear to be coming from one or more publicly routable IP addresses. Each outbound connection from an internal device translates to a different source TCP port on the public IP address.</span></span> 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a><span data-ttu-id="a5bb9-113">為何需要有太同時開啟至 Office 365 的連線？</span><span class="sxs-lookup"><span data-stu-id="a5bb9-113">Why do you need to have so many connections open to Office 365 at the same time?</span></span>

<span data-ttu-id="a5bb9-p103">Outlook 可能會開啟 8 個以上的連線 (在有增益集、共用行事曆、信箱等等的情況下)。由於以 Windows 為基礎的 NAT 裝置最多有 64,000 個連接埠，因此在耗盡連接埠之前，每個 IP 位址背後最多能有 8,000 名使用者。請注意，如果客戶使用以非 Windows 作業系統為基礎的 NAT 裝置，可用的連接埠總數將取決於使用的 NAT 裝置或軟體。在這種情況下，連接埠數目上限可能會小於 64,000 個。連接埠的可用性也會受到其他因素影響，例如，Windows 限制必須保留 4,000 個連接埠供其使用，導致可用的連接埠總數減少為 60,000 個。另外，其他應用程式 (如 Internet Explorer) 可能會同時連線，導致需要更多的連接埠。</span><span class="sxs-lookup"><span data-stu-id="a5bb9-p103">Outlook may open eight or more connections (in situations where there are add-ins, shared calendars, mailboxes, etc.). Because there are a maximum of 64,000 ports available on a Windows-based NAT device, there can be a maximum of 8,000 users behind an IP address before the ports are exhausted. Note that if customers are using non-Windows OS-based devices for NAT, the total available ports are dependent on what NAT device or software is being used. In this scenario, the maximum number of ports could be less than 64,000. Availability of ports is also affected by other factors such as Windows restricting 4,000 ports for its own use, which reduces the total number of available ports to 60,000.There may be other applications, such as Internet Explorer, that could connect at the same time, requiring additional ports.</span></span>
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a><span data-ttu-id="a5bb9-119">計算支援的裝置數目上限與 Office 365 搭配單一公用 IP 位址</span><span class="sxs-lookup"><span data-stu-id="a5bb9-119">Calculating maximum supported devices behind a single public IP address with Office 365</span></span>

<span data-ttu-id="a5bb9-p104">若要決定單一公用 IP 位址的裝置數目上限，您應該監視來決定將連接埠消耗尖峰每個用戶端的網路流量。此外，峰值因數應用於連接埠使用狀況 (最小 4)。</span><span class="sxs-lookup"><span data-stu-id="a5bb9-p104">To determine the maximum number of devices behind a single public IP address, you should monitor network traffic to determine peak port consumption per client. Also, a peak factor should be used for the port usage (minimum 4).</span></span> 
  
 <span data-ttu-id="a5bb9-122">**使用下列公式可計算的每個 IP 位址支援的裝置數：**</span><span class="sxs-lookup"><span data-stu-id="a5bb9-122">**Use the following formula to calculate the number of supported devices per IP address:**</span></span>
  
<span data-ttu-id="a5bb9-123">支援的單一公用 IP 位址的裝置上限 = (64000-限制的連接埠) / （連接埠消耗尖峰 + 峰值因數）</span><span class="sxs-lookup"><span data-stu-id="a5bb9-123">Maximum supported devices behind a single public IP address = (64,000 - restricted ports)/(Peak port consumption + peak factor)</span></span>
  
 <span data-ttu-id="a5bb9-124">**例如，如果下列則為 true：**</span><span class="sxs-lookup"><span data-stu-id="a5bb9-124">**For example, if the following were true:**</span></span>
  
- <span data-ttu-id="a5bb9-125">**限制的連接埠：** 4000 的作業系統</span><span class="sxs-lookup"><span data-stu-id="a5bb9-125">**Restricted ports:** 4,000 for the operating system</span></span> 
    
- <span data-ttu-id="a5bb9-126">每個裝置的**尖峰連接埠消耗：** 6</span><span class="sxs-lookup"><span data-stu-id="a5bb9-126">**Peak port consumption:** 6 per device</span></span> 
    
- <span data-ttu-id="a5bb9-127">**峰值因數：** 4</span><span class="sxs-lookup"><span data-stu-id="a5bb9-127">**Peak factor:** 4</span></span> 
    
<span data-ttu-id="a5bb9-128">然後，支援的裝置上限單一公用 IP 位址 = (64000 4000) / （6 + 4） = 6000</span><span class="sxs-lookup"><span data-stu-id="a5bb9-128">Then, the maximum supported devices behind a single public IP address = (64,000 - 4,000)/(6 + 4) = 6,000</span></span>
  
<span data-ttu-id="a5bb9-p105">與 Office 365 主控套件，包含在從 Microsoft Office Outlook 2007 年 9 月 2011年或年 11 月 2011 for Microsoft Outlook 2010、 更新或更新版本的更新，從 Outlook (這兩種 Office Outlook 2007 與服務的連線數目的版本Pack 2 與 Outlook 2010) 至 Exchange 可以是 2 部。您將需要不同的作業系統使用者行為，依此類推來判斷您的網路需要在尖峰時段的連接埠最小和最大數目的因素。</span><span class="sxs-lookup"><span data-stu-id="a5bb9-p105">With the release of Office 365 hosting pack, included in the updates from September 2011 for Microsoft Office Outlook 2007, or November 2011 for Microsoft Outlook 2010, or a later update, the number of connections from Outlook (both Office Outlook 2007 with Service Pack 2 and Outlook 2010) to Exchange can be as few as 2. You'll need to factor in the different operating systems, user behaviors, and so on to determine the minimum and maximum number of ports that your network will require at peak.</span></span>
  
<span data-ttu-id="a5bb9-131">如果您想要支援多個裝置背後的單一公用 IP 位址，請遵循下列步驟，評估可以支援的裝置數目上限：</span><span class="sxs-lookup"><span data-stu-id="a5bb9-131">If you want to support more devices behind a single public IP address, follow the steps outlined to assess the maximum number of devices that can be supported:</span></span>
  
<span data-ttu-id="a5bb9-p106">監視來決定將連接埠消耗尖峰每個用戶端的網路流量。您應收集此資料：</span><span class="sxs-lookup"><span data-stu-id="a5bb9-p106">Monitor network traffic to determine peak port consumption per client. You should collect this data:</span></span>
  
- <span data-ttu-id="a5bb9-134">來自多個位置</span><span class="sxs-lookup"><span data-stu-id="a5bb9-134">From multiple locations</span></span>
    
- <span data-ttu-id="a5bb9-135">來自多部裝置</span><span class="sxs-lookup"><span data-stu-id="a5bb9-135">From multiple devices</span></span>
    
- <span data-ttu-id="a5bb9-136">在多個時間</span><span class="sxs-lookup"><span data-stu-id="a5bb9-136">At multiple times</span></span>
    
<span data-ttu-id="a5bb9-137">使用前述公式來計算環境中每個 IP 位址可以支援的使用者上限。</span><span class="sxs-lookup"><span data-stu-id="a5bb9-137">Use the preceding formula to calculate the maximum users per IP address that can be supported in their environment.</span></span>
  
<span data-ttu-id="a5bb9-p107">有各種方法將用戶端負載分散到其他公用 IP 位址。可用的策略而定的公司閘道解決方案功能。最簡單的解決方案是分割您使用者位址空間和靜態"號碼指派給"的 IP 位址至每個閘道。提供許多閘道裝置的另一個替代項是使用的 IP 位址的集區的能力。地址集區的優點是它是更動態和幾乎需要調整為您的使用者群成長。</span><span class="sxs-lookup"><span data-stu-id="a5bb9-p107">There are various methods for distributing client load across additional public IP addresses. Strategies available depend on the capabilities of the corporate gateway solution. The simplest solution is to segment your user address space and statically "assign" a number of IP addresses to each gateway. Another alternative that many gateway devices offer is the ability to use a pool of IP addresses. The benefit of the address pool is that it is much more dynamic and less likely to require adjustment as your user base grows.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a5bb9-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5bb9-143">See also</span></span>

[<span data-ttu-id="a5bb9-144">管理 Office 365 端點</span><span class="sxs-lookup"><span data-stu-id="a5bb9-144">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="a5bb9-145">Office 365 端點常見問題集</span><span class="sxs-lookup"><span data-stu-id="a5bb9-145">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

