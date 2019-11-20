---
title: Office 365 的 NAT 支援
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 1/24/2017
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: 摘要： 提供如何約略算出正確的您可以使用每個 IP 位址使用網路位址轉譯 (NAT) 組織內的用戶端數目的相關詳細資料。
ms.openlocfilehash: 5d252b059661fdd3bad1f86bf552f44b8a747d24
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747897"
---
# <a name="nat-support-with-office-365"></a><span data-ttu-id="e0a03-103">Office 365 的 NAT 支援</span><span class="sxs-lookup"><span data-stu-id="e0a03-103">NAT support with Office 365</span></span>

<span data-ttu-id="e0a03-104">*本文適用於 Office 365 企業版和 Microsoft 365 企業版。*</span><span class="sxs-lookup"><span data-stu-id="e0a03-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="e0a03-105">先前，指導方針建議您應該使用每個 IP 位址來連線到 Office 365 的 Exchange 用戶端數目上限是每個網路連接埠容納約 2000 個用戶端。</span><span class="sxs-lookup"><span data-stu-id="e0a03-105">Previously, guidance suggested that the maximum number of Exchange clients you should use per IP address to connect to Office 365 was about 2,000 clients per network port.</span></span>
  
## <a name="why-use-nat"></a><span data-ttu-id="e0a03-106">為什麼要使用 NAT？</span><span class="sxs-lookup"><span data-stu-id="e0a03-106">Why use NAT?</span></span>

<span data-ttu-id="e0a03-107">藉由使用 NAT，數以千計的人員的公司網路可以 「 共用 」 一些可公開路由的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="e0a03-107">By using NAT, thousands of people on a corporate network can "share" a few publicly routable IP addresses.</span></span>
  
<span data-ttu-id="e0a03-108">最公司網路使用私人 (RFC1918) IP 位址空間。</span><span class="sxs-lookup"><span data-stu-id="e0a03-108">Most corporate networks use private (RFC1918) IP address space.</span></span> <span data-ttu-id="e0a03-109">私人位址空間是配置由網際網路指派數字授權單位 (IANA)，並僅供直接到及傳送自全域網際網路無法路由傳送的網路。</span><span class="sxs-lookup"><span data-stu-id="e0a03-109">Private address space is allocated by the Internet Assigned Numbers Authority (IANA) and intended solely for networks that do not route directly to and from the global Internet.</span></span>
  
<span data-ttu-id="e0a03-110">若要提供的私人 IP 位址空間裝置的網際網路存取，組織會使用閘道技術，例如防火牆及 proxy 會提供網路位址轉譯 (NAT) 或連接埠位址轉譯 (PAT) 服務。</span><span class="sxs-lookup"><span data-stu-id="e0a03-110">To provide Internet access to devices on a private IP address space, organizations use gateway technologies like firewalls and proxies that provide network address translation (NAT) or port address translation (PAT) services.</span></span> <span data-ttu-id="e0a03-111">這些閘道進行從內部流量至網際網路 （包括 Office 365） 的裝置出現似乎來自一或多個可公開路由的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="e0a03-111">These gateways make traffic from internal devices to the Internet (including Office 365) appear to be coming from one or more publicly routable IP addresses.</span></span> <span data-ttu-id="e0a03-112">內部裝置從每個輸出連線會轉譯為不同的來源 TCP 連接埠上的公用 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="e0a03-112">Each outbound connection from an internal device translates to a different source TCP port on the public IP address.</span></span> 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a><span data-ttu-id="e0a03-113">為什麼需要有 Office 365 同時開啟許多連線？</span><span class="sxs-lookup"><span data-stu-id="e0a03-113">Why do you need to have so many connections open to Office 365 at the same time?</span></span>

<span data-ttu-id="e0a03-114">Outlook 可能會開啟八個以上的連線 (的情況下有增益集、 共用行事曆、 信箱等。)。</span><span class="sxs-lookup"><span data-stu-id="e0a03-114">Outlook may open eight or more connections (in situations where there are add-ins, shared calendars, mailboxes, etc.).</span></span> <span data-ttu-id="e0a03-115">因為有可用的最大值的連接埠 64000 Windows 型 NAT 裝置上，可以有最多個 IP 位址背後的 8000 使用者之前的連接埠會耗盡。</span><span class="sxs-lookup"><span data-stu-id="e0a03-115">Because there are a maximum of 64,000 ports available on a Windows-based NAT device, there can be a maximum of 8,000 users behind an IP address before the ports are exhausted.</span></span> <span data-ttu-id="e0a03-116">請注意，如果客戶使用 NAT 非 Windows 作業系統型裝置，可以使用的連接埠總數取決於正在使用何種 NAT 裝置或軟體。</span><span class="sxs-lookup"><span data-stu-id="e0a03-116">Note that if customers are using non-Windows OS-based devices for NAT, the total available ports are dependent on what NAT device or software is being used.</span></span> <span data-ttu-id="e0a03-117">在此案例中，連接埠的最大數目可能是小於 64000。</span><span class="sxs-lookup"><span data-stu-id="e0a03-117">In this scenario, the maximum number of ports could be less than 64,000.</span></span> <span data-ttu-id="e0a03-118">連接埠的可用性也會受到其他因素例如可能是 Windows 限制供自己使用，可使用的連接埠總數減少到 60,000.There 4000 個連接埠，請在其他應用程式，例如 Internet Explorer 中，同時無法連線需要額外的連接埠。</span><span class="sxs-lookup"><span data-stu-id="e0a03-118">Availability of ports is also affected by other factors such as Windows restricting 4,000 ports for its own use, which reduces the total number of available ports to 60,000.There may be other applications, such as Internet Explorer, that could connect at the same time, requiring additional ports.</span></span>
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a><span data-ttu-id="e0a03-119">支援的裝置與 Office 365 單一公用 IP 位址背後計算上限</span><span class="sxs-lookup"><span data-stu-id="e0a03-119">Calculating maximum supported devices behind a single public IP address with Office 365</span></span>

<span data-ttu-id="e0a03-120">若要判斷在單一公用 IP 位址背後的裝置數目上限，您應該監視網路流量，以判斷將連接埠消耗尖峰每個用戶端。</span><span class="sxs-lookup"><span data-stu-id="e0a03-120">To determine the maximum number of devices behind a single public IP address, you should monitor network traffic to determine peak port consumption per client.</span></span> <span data-ttu-id="e0a03-121">此外，峰值因數應使用的連接埠使用狀況 (最小值 4)。</span><span class="sxs-lookup"><span data-stu-id="e0a03-121">Also, a peak factor should be used for the port usage (minimum 4).</span></span> 
  
 <span data-ttu-id="e0a03-122">**使用下列公式可計算每個 IP 位址支援的裝置數目：**</span><span class="sxs-lookup"><span data-stu-id="e0a03-122">**Use the following formula to calculate the number of supported devices per IP address:**</span></span>
  
<span data-ttu-id="e0a03-123">支援的單一公用 IP 位址的裝置上限 = (64000-限制的連接埠) / （尖峰連接埠消耗 + 峰值因數）</span><span class="sxs-lookup"><span data-stu-id="e0a03-123">Maximum supported devices behind a single public IP address = (64,000 - restricted ports)/(Peak port consumption + peak factor)</span></span>
  
 <span data-ttu-id="e0a03-124">**例如，如果下列，則為 true:**</span><span class="sxs-lookup"><span data-stu-id="e0a03-124">**For example, if the following were true:**</span></span>
  
- <span data-ttu-id="e0a03-125">**限制的連接埠：** 4000 operating system</span><span class="sxs-lookup"><span data-stu-id="e0a03-125">**Restricted ports:** 4,000 for the operating system</span></span>

- <span data-ttu-id="e0a03-126">每個裝置的**尖峰連接埠消耗：** 6</span><span class="sxs-lookup"><span data-stu-id="e0a03-126">**Peak port consumption:** 6 per device</span></span>

- <span data-ttu-id="e0a03-127">**峰值因數：** 4</span><span class="sxs-lookup"><span data-stu-id="e0a03-127">**Peak factor:** 4</span></span>

<span data-ttu-id="e0a03-128">然後，支援的裝置上限單一公用 IP 位址背後 = (64000 4000) / （6 + 4） = 6000</span><span class="sxs-lookup"><span data-stu-id="e0a03-128">Then, the maximum supported devices behind a single public IP address = (64,000 - 4,000)/(6 + 4) = 6,000</span></span>
  
<span data-ttu-id="e0a03-129">主控套件，從 Microsoft Office Outlook 2007 年 9 月 2011年或 Microsoft Outlook 2010 年 11 月 2011年更新或更新版本的更新，從 Outlook (這兩個 Office Outlook 2007 與服務的連線數目中包含的 Office 365 版本Pack 2 和 Outlook 2010) 到 Exchange 可以是最少 2。</span><span class="sxs-lookup"><span data-stu-id="e0a03-129">With the release of Office 365 hosting pack, included in the updates from September 2011 for Microsoft Office Outlook 2007, or November 2011 for Microsoft Outlook 2010, or a later update, the number of connections from Outlook (both Office Outlook 2007 with Service Pack 2 and Outlook 2010) to Exchange can be as few as 2.</span></span> <span data-ttu-id="e0a03-130">您需要在不同的作業系統，依此類推至判斷您的網路時，需要在尖峰時段的連接埠的最小值和最大數目的使用者行為因素。</span><span class="sxs-lookup"><span data-stu-id="e0a03-130">You'll need to factor in the different operating systems, user behaviors, and so on to determine the minimum and maximum number of ports that your network will require at peak.</span></span>
  
<span data-ttu-id="e0a03-131">如果您想要支援多個裝置在單一公用 IP 位址，請依照下列步驟所述來評估可以支援的裝置數目上限：</span><span class="sxs-lookup"><span data-stu-id="e0a03-131">If you want to support more devices behind a single public IP address, follow the steps outlined to assess the maximum number of devices that can be supported:</span></span>
  
<span data-ttu-id="e0a03-132">監視網路流量，以判斷將連接埠消耗尖峰每個用戶端。</span><span class="sxs-lookup"><span data-stu-id="e0a03-132">Monitor network traffic to determine peak port consumption per client.</span></span> <span data-ttu-id="e0a03-133">您應收集此資料：</span><span class="sxs-lookup"><span data-stu-id="e0a03-133">You should collect this data:</span></span>
  
- <span data-ttu-id="e0a03-134">從多個位置</span><span class="sxs-lookup"><span data-stu-id="e0a03-134">From multiple locations</span></span>
    
- <span data-ttu-id="e0a03-135">從多個裝置</span><span class="sxs-lookup"><span data-stu-id="e0a03-135">From multiple devices</span></span>
    
- <span data-ttu-id="e0a03-136">在多個時間</span><span class="sxs-lookup"><span data-stu-id="e0a03-136">At multiple times</span></span>
    
<span data-ttu-id="e0a03-137">使用前述公式來計算每個 IP 位址，可以在其環境中支援的最大使用者。</span><span class="sxs-lookup"><span data-stu-id="e0a03-137">Use the preceding formula to calculate the maximum users per IP address that can be supported in their environment.</span></span>
  
<span data-ttu-id="e0a03-138">有各種方法供用戶端負載分散其他公用 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="e0a03-138">There are various methods for distributing client load across additional public IP addresses.</span></span> <span data-ttu-id="e0a03-139">可用的策略取決於公司閘道方案的功能。</span><span class="sxs-lookup"><span data-stu-id="e0a03-139">Strategies available depend on the capabilities of the corporate gateway solution.</span></span> <span data-ttu-id="e0a03-140">最簡單的解決方案是分割您的使用者位址空間及靜態 「 」 號碼指派的 IP 位址給每個閘道。</span><span class="sxs-lookup"><span data-stu-id="e0a03-140">The simplest solution is to segment your user address space and statically "assign" a number of IP addresses to each gateway.</span></span> <span data-ttu-id="e0a03-141">多閘道裝置提供的另一個替代方法為使用的 IP 位址的集區的能力。</span><span class="sxs-lookup"><span data-stu-id="e0a03-141">Another alternative that many gateway devices offer is the ability to use a pool of IP addresses.</span></span> <span data-ttu-id="e0a03-142">地址集區的好處是它是很多動態和較不可能需要調整為您的使用者群規模日益成長。</span><span class="sxs-lookup"><span data-stu-id="e0a03-142">The benefit of the address pool is that it is much more dynamic and less likely to require adjustment as your user base grows.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e0a03-143">請參閱</span><span class="sxs-lookup"><span data-stu-id="e0a03-143">See also</span></span>

[<span data-ttu-id="e0a03-144">管理 Office 365 端點</span><span class="sxs-lookup"><span data-stu-id="e0a03-144">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
<span data-ttu-id="e0a03-145">[Office 365 端點常見問題集](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) (機器翻譯)</span><span class="sxs-lookup"><span data-stu-id="e0a03-145">[Office 365 endpoints FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)</span></span>
