---
title: Office 365 服務中的 IPv6 支援
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/10/2018
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
ms.assetid: c08786fb-298e-437c-8222-dab7625fc815
description: 摘要： 說明 Office 365 政府版方案和 Microsoft Office 365 元件中的 IPv6 支援。
ms.openlocfilehash: 32e90f0dda9b06d06b6e289b26f640c4ddc79cf3
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41845114"
---
# <a name="ipv6-support-in-office-365-services"></a><span data-ttu-id="48916-103">Office 365 服務中的 IPv6 支援</span><span class="sxs-lookup"><span data-stu-id="48916-103">IPv6 support in Office 365 services</span></span>

<span data-ttu-id="48916-104">*本文適用於 Office 365 企業版和 Microsoft 365 企業版。*</span><span class="sxs-lookup"><span data-stu-id="48916-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="48916-105">Office 365 支援 IPv6 和 IPv4;不過，並非所有 Office 365 功能都可以完整都啟用使用 IPv6。</span><span class="sxs-lookup"><span data-stu-id="48916-105">Office 365 supports both IPv6 and IPv4; however, not all Office 365 features are fully enabled with IPv6.</span></span> <span data-ttu-id="48916-106">這表示您必須連線至 Office 365 使用 IPv4 和 IPv6。</span><span class="sxs-lookup"><span data-stu-id="48916-106">This means that you must use both IPv4 and IPv6 to connect to Office 365.</span></span> <span data-ttu-id="48916-107">如果您正在篩選您 Office 365 的輸出流量，Office 365 所支援的 IPv6 位址的完整清單可以找到[Office 365 Url 和 IP 位址範圍](urls-and-ip-address-ranges.md)」 文件中。</span><span class="sxs-lookup"><span data-stu-id="48916-107">If you are filtering your outbound traffic to Office 365, the full list of IPv6 addresses that are supported by Office 365 can be found in the article [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span> <span data-ttu-id="48916-108">設定您的網路，並允許適當的 IPv6 位址之後，您可以下載[Office 365 IPv6 測試計劃](https://go.microsoft.com/fwlink/?LinkId=293447)從 Microsoft 下載中心找到。</span><span class="sxs-lookup"><span data-stu-id="48916-108">After your network is configured and the appropriate IPv6 addresses are allowed, you can download the [Office 365 IPv6 test plan](https://go.microsoft.com/fwlink/?LinkId=293447) from the Microsoft Download Center.</span></span>
  
## <a name="ipv6-support-in-office-365-subscription-service"></a><span data-ttu-id="48916-109">Office 365 訂閱服務中的 IPv6 支援</span><span class="sxs-lookup"><span data-stu-id="48916-109">IPv6 support in Office 365 subscription service</span></span>

### <a name="exchange-online-and-ipv6"></a><span data-ttu-id="48916-110">Exchange Online 和 IPv6</span><span class="sxs-lookup"><span data-stu-id="48916-110">Exchange Online and IPv6</span></span>

<span data-ttu-id="48916-111">如果您用來連線至 Exchange Online 的程式支援 IPv6，則會在有線和無線網路上的預設使用 IPv6。</span><span class="sxs-lookup"><span data-stu-id="48916-111">If the program that you use to connect to Exchange Online supports IPv6, it will use IPv6 by default on both wired and wireless networks.</span></span> <span data-ttu-id="48916-112">如果您想要控制 Exchange Online 的通訊，請在[Office 365 Url 和 IP 位址範圍](urls-and-ip-address-ranges.md)中使用的 IP 位址範圍。</span><span class="sxs-lookup"><span data-stu-id="48916-112">If you want to control communications to Exchange Online, use the IP address ranges in [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="sharepoint-online-and-ipv6"></a><span data-ttu-id="48916-113">SharePoint Online 和 IPv6</span><span class="sxs-lookup"><span data-stu-id="48916-113">SharePoint Online and IPv6</span></span>

 <span data-ttu-id="48916-114">**Office 365 政府版 G1/G3/G4/K1**如果您用來連線到 SharePoint Online 的程式支援 IPv6，它會嘗試使用預設的 IPv6。</span><span class="sxs-lookup"><span data-stu-id="48916-114">**Office 365 Government G1/G3/G4/K1** If the program that you use to connect to SharePoint Online supports IPv6, it will attempt to use IPv6 by default.</span></span>
  
 <span data-ttu-id="48916-115">**公用的多重租用戶雲端**Microsoft 可讓 SharePoint Online IPv6，在您的要求。</span><span class="sxs-lookup"><span data-stu-id="48916-115">**Public multi-tenant cloud** Microsoft enables SharePoint Online IPv6 at your request.</span></span> <span data-ttu-id="48916-116">您需要提供 CIDR 表示貴組織的 DNS 基礎結構的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="48916-116">You need to provide the CIDR notated IP addresses for your organization's DNS infrastructure.</span></span> <span data-ttu-id="48916-117">請記住，為您的租用戶啟用 IPv6 的其他組織無法共用此 DNS 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="48916-117">Keep in mind that this DNS infrastructure can't be shared by other organizations for IPv6 to be enabled for your tenant.</span></span> <span data-ttu-id="48916-118">啟用 IPv6 時，如果您用來連線到 SharePoint Online 的程式支援 IPv6 之後，它會使用預設的 IPv6。</span><span class="sxs-lookup"><span data-stu-id="48916-118">After IPv6 is enabled, if the program that you use to connect to SharePoint Online supports IPv6, it uses IPv6 by default.</span></span>
  
<span data-ttu-id="48916-119">如果您用來連線到 SharePoint Online 的程式支援 IPv6，則會在有線和無線網路上的預設使用 IPv6。</span><span class="sxs-lookup"><span data-stu-id="48916-119">If the program that you use to connect to SharePoint Online supports IPv6, it will use IPv6 by default on both wired and wireless networks.</span></span> <span data-ttu-id="48916-120">如果您想要控制 SharePoint Online 的通訊，請在[Office 365 Url 和 IP 位址範圍](urls-and-ip-address-ranges.md)中使用的 IP 位址範圍。</span><span class="sxs-lookup"><span data-stu-id="48916-120">If you want to control communications to SharePoint Online, use the IP address ranges in [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>
  
 <span data-ttu-id="48916-121">**Office 365 政府版 G1/G3/G4/K1**如果您用來連線到 SharePoint Online 的程式支援 IPv6，它會嘗試使用預設的 IPv6。</span><span class="sxs-lookup"><span data-stu-id="48916-121">**Office 365 Government G1/G3/G4/K1** If the program that you use to connect to SharePoint Online supports IPv6, it will attempt to use IPv6 by default.</span></span>
  
### <a name="skype-for-business-and-ipv6"></a><span data-ttu-id="48916-122">Skype for Business 和 IPv6</span><span class="sxs-lookup"><span data-stu-id="48916-122">Skype for Business and IPv6</span></span>

<span data-ttu-id="48916-123">請注意 IPv6 不支援在商務用 Skype 和不再已啟用。</span><span class="sxs-lookup"><span data-stu-id="48916-123">Please be aware IPv6 is not supported in Skype for Business and can no longer be enabled.</span></span>
  
### <a name="exchange-online-protection-and-ipv6"></a><span data-ttu-id="48916-124">Exchange Online Protection 和 IPv6</span><span class="sxs-lookup"><span data-stu-id="48916-124">Exchange Online Protection and IPv6</span></span>

<span data-ttu-id="48916-125">Exchange Online Protection (EOP) 會支援 IPv6，如果傳輸發生透過傳輸層安全性通訊協定。</span><span class="sxs-lookup"><span data-stu-id="48916-125">Exchange Online Protection (EOP) supports IPv6 if the transmission occurs over Transport Layer Security Protocol.</span></span> <span data-ttu-id="48916-126">EOP 的範圍，請使用[Office 365 Url 和 IP 位址範圍](urls-and-ip-address-ranges.md)。</span><span class="sxs-lookup"><span data-stu-id="48916-126">For the EOP range, use [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="ipv6-support-for-office-365-government-offerings"></a><span data-ttu-id="48916-127">Office 365 政府版方案的 IPv6 支援</span><span class="sxs-lookup"><span data-stu-id="48916-127">IPv6 support for Office 365 government offerings</span></span>

<span data-ttu-id="48916-128">Office 365 政府版方案的 IPv6 支援的資訊長 Executive 部門和行政機關，以及聯邦政府採用的網際網路通訊協定第 6 版 (IPv6 符合 Office 的管理和預算 (OMB) 備忘錄) 備忘錄。</span><span class="sxs-lookup"><span data-stu-id="48916-128">Office 365 IPv6 support for government offerings conforms to the Office of Management and Budget (OMB) Memorandum for Chief Information Officers of Executive Departments and Agencies, as well as the Federal Government Adoption of Internet Protocol Version 6 (IPv6) memorandum.</span></span> <span data-ttu-id="48916-129">[政府適用於 Microsoft Office 365](https://go.microsoft.com/fwlink/p/?LinkId=325414)是一種多承租人服務，我們政府資料儲存在單獨分開的社群雲端。</span><span class="sxs-lookup"><span data-stu-id="48916-129">[Microsoft Office 365 for Government](https://go.microsoft.com/fwlink/p/?LinkId=325414) is a multi-tenant service that stores US government data in a segregated community cloud.</span></span> <span data-ttu-id="48916-130">像其他 Office 365 供應項目，它提供生產力和共同作業服務，包括 Exchange Online、 Skype for Business、 SharePoint Online 和 Office 專業增強版。</span><span class="sxs-lookup"><span data-stu-id="48916-130">Like other Office 365 offerings, it provides productivity and collaboration services, including Exchange Online, Skype for Business, SharePoint Online, and Office Professional Plus.</span></span> 

<span data-ttu-id="48916-131">僅適用於 2013年和更新版本，適用於 Microsoft Office 365 政府版方案。</span><span class="sxs-lookup"><span data-stu-id="48916-131">The Microsoft Office 365 government offerings apply only for 2013 and later.</span></span> <span data-ttu-id="48916-132">如需有關 Office 365 政府版方案的詳細資訊，請參閱[宣佈政府用 Office 365: 美國政府社群雲端](https://go.microsoft.com/fwlink/p/?LinkId=325414)。</span><span class="sxs-lookup"><span data-stu-id="48916-132">For more information about the Office 365 government offerings, see [Announcing Office 365 for Government: A US Government Community Cloud](https://go.microsoft.com/fwlink/p/?LinkId=325414).</span></span> <span data-ttu-id="48916-133">國際流量中武器法規 (ITAR) 是一組的美國政府法規，以控制匯出和匯入防禦相關文章和[美國武器清單 (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415)上的服務。</span><span class="sxs-lookup"><span data-stu-id="48916-133">International Traffic in Arms Regulations (ITAR) is a set of US government regulations that control the export and import of defense-related articles and services on the [United States Munitions List (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415).</span></span> 

<span data-ttu-id="48916-134">適用於企業的 Microsoft Office 365 提供的 Microsoft 產能支援解決方案安全性、 隱私權和法規遵循需求為我們需要聯邦資訊安全的聯邦機構專用主控的服務管理 (FISMA) 憑證和 ITAR 受到商業實體。</span><span class="sxs-lookup"><span data-stu-id="48916-134">Microsoft Office 365 for Enterprises provides dedicated hosting services for Microsoft productivity solutions that support the security, privacy, and regulatory compliance requirements for US federal agencies requiring Federal Information Security Management (FISMA) certification and commercial entities subject to ITAR.</span></span>
  
## <a name="things-to-consider-when-using-ipv6-and-office-365"></a><span data-ttu-id="48916-135">使用 IPv6 和 Office 365 時的考量事項</span><span class="sxs-lookup"><span data-stu-id="48916-135">Things to consider when using IPv6 and Office 365</span></span>

<span data-ttu-id="48916-136">我們建議您不要停用 IPv6。</span><span class="sxs-lookup"><span data-stu-id="48916-136">We recommend that you do not disable IPv6.</span></span> <span data-ttu-id="48916-137">如需詳細資訊，請參閱本[指南的文章](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users)。</span><span class="sxs-lookup"><span data-stu-id="48916-137">For more information, see this [guidance article](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users).</span></span> <span data-ttu-id="48916-138">若要判斷您網路上正在使用何種 IP 版本，請考慮下列各項：</span><span class="sxs-lookup"><span data-stu-id="48916-138">To determine what IP versions are being used on your network, consider the following:</span></span>
  
- <span data-ttu-id="48916-139">如果顯示的**IPConfig**命令，在命令提示字元中包含名為"IPv6 Address"Temporary IPv6 Address"列，您已在您的環境中有 IPv6。</span><span class="sxs-lookup"><span data-stu-id="48916-139">If the display of the **IPConfig** command at the command prompt contains rows named "IPv6 Address" or "Temporary IPv6 Address," you have IPv6 in your environment.</span></span>

- <span data-ttu-id="48916-140">如果所有 IPv6 位址開頭都是"fe80"並且對應到名為"Link-local IPv6 Address"列，您不需要在您的環境中的 IPv6。</span><span class="sxs-lookup"><span data-stu-id="48916-140">If all the IPv6 addresses begin with "fe80" and correspond to rows named "Link-Local IPv6 Address," you don't have IPv6 in your environment.</span></span>

<span data-ttu-id="48916-141">這些考慮事項可能適用於您的網路：</span><span class="sxs-lookup"><span data-stu-id="48916-141">These considerations might apply to your network:</span></span>
  
- <span data-ttu-id="48916-142">在公用訂閱服務不支援購買以信用卡透過 IPv6。</span><span class="sxs-lookup"><span data-stu-id="48916-142">The public subscription service does not support purchase by credit card over IPv6.</span></span> <span data-ttu-id="48916-143">因為政府有 Enterprise Agreement (EA) 授權，這不適用政府社群雲端 (GCC)。</span><span class="sxs-lookup"><span data-stu-id="48916-143">This does not apply to the Government Community Cloud (GCC) because governments have Enterprise Agreement (EA) licensing.</span></span>

- <span data-ttu-id="48916-144">IPv6 不支援某些 Rights Management Services (RMS) 案例。</span><span class="sxs-lookup"><span data-stu-id="48916-144">IPv6 does not support some Rights Management Services (RMS) scenarios.</span></span>

- <span data-ttu-id="48916-145">IPv6 不支援 BlackBerry® Enterprise Server (BES)，因為 BlackBerry 不支援 IPv6。</span><span class="sxs-lookup"><span data-stu-id="48916-145">IPv6 does not support BlackBerry® Enterprise Server (BES) because BlackBerry doesn't support IPv6.</span></span>

- <span data-ttu-id="48916-146">如果您使用 Active Directory Federation Services (AD FS) 與 Office 365 時，通知您 Office 365 的 AD FS 網路端點 IPv6 不支援使用。</span><span class="sxs-lookup"><span data-stu-id="48916-146">If you use Active Directory Federation Services (AD FS) with Office 365, advertising your AD FS network endpoint to Office 365 using IPv6 is not supported.</span></span> <span data-ttu-id="48916-147">您不應該包含 AAAA 記錄中的 AD FS DNS 項目時使用 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="48916-147">You should not include AAAA records in the AD FS DNS entry when using Exchange Online.</span></span> 

<span data-ttu-id="48916-148">您可以使用下列短連結返回這裡：[https://aka.ms/o365ip6](https://aka.ms/o365ip6)</span><span class="sxs-lookup"><span data-stu-id="48916-148">Here's a short link you can use to come back: [https://aka.ms/o365ip6](https://aka.ms/o365ip6)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="48916-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48916-149">See also</span></span>

<span data-ttu-id="48916-150">[IPv6 學習藍圖](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))</span><span class="sxs-lookup"><span data-stu-id="48916-150">[IPv6 Learning Roadmap](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))</span></span>
  
[<span data-ttu-id="48916-151">IPv6 生存指南</span><span class="sxs-lookup"><span data-stu-id="48916-151">IPv6 Survival Guide</span></span>](https://social.technet.microsoft.com/wiki/contents/articles/1728.ipv6-survival-guide.aspx)
