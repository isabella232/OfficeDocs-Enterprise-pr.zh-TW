---
title: Office 365 服務中的 IPv6 支援
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/10/2018
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
ms.assetid: c08786fb-298e-437c-8222-dab7625fc815
description: 摘要： 說明在 Microsoft Office 365 元件和 Office 365 政府版方案的 IPv6 支援。
ms.openlocfilehash: ed06f1eac3c6a3d631445db1d623bd25c62a309c
ms.sourcegitcommit: ae7f2087d51698d3c5ef371888278544a7046205
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/10/2018
ms.locfileid: "25493828"
---
# <a name="ipv6-support-in-office-365-services"></a><span data-ttu-id="97659-103">Office 365 服務中的 IPv6 支援</span><span class="sxs-lookup"><span data-stu-id="97659-103">IPv6 support in Office 365 services</span></span>

 <span data-ttu-id="97659-104">**摘要**： 說明在 Microsoft Office 365 元件和 Office 365 政府版方案的 IPv6 支援。</span><span class="sxs-lookup"><span data-stu-id="97659-104">**Summary**: Describes IPv6 support in Microsoft Office 365 components and in Office 365 government offerings.</span></span>
  
<span data-ttu-id="97659-p101">Office 365 支援 IPv6 和 IPv4;不過，不是所有的 Office 365 功能已完全啟用 ipv6。這表示您必須連線到 Office 365 使用 IPv4 和 IPv6。如果您篩選至 Office 365 您輸出流量、 支援的 Office 365 的 IPv6 位址的完整清單可以找到文章[Office 365 Url 和 IP 位址範圍](https://go.microsoft.com/fwlink/?LinkId=293744)中。設定您的網路，並允許使用適當的 IPv6 位址之後，您可以下載[Office 365 IPv6 測試計劃](https://go.microsoft.com/fwlink/?LinkId=293447)從 Microsoft 下載中心。</span><span class="sxs-lookup"><span data-stu-id="97659-p101">Office 365 supports both IPv6 and IPv4; however, not all Office 365 features are fully enabled with IPv6. This means that you must use both IPv4 and IPv6 to connect to Office 365. If you are filtering your outbound traffic to Office 365, the full list of IPv6 addresses that are supported by Office 365 can be found in the article [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/?LinkId=293744). After your network is configured and the appropriate IPv6 addresses are allowed, you can download the [Office 365 IPv6 test plan](https://go.microsoft.com/fwlink/?LinkId=293447) from the Microsoft Download Center.</span></span>
  
||
|:-----|
| <span data-ttu-id="97659-109">本文是[網路規劃和 Office 365 的效能調整](https://aka.ms/tune)的一部分。</span><span class="sxs-lookup"><span data-stu-id="97659-109">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

## <a name="ipv6-support-in-office-365-subscription-service"></a><span data-ttu-id="97659-110">Office 365 訂閱服務中的 IPv6 支援</span><span class="sxs-lookup"><span data-stu-id="97659-110">IPv6 support in Office 365 subscription service</span></span>

### <a name="exchange-online-and-ipv6"></a><span data-ttu-id="97659-111">Exchange Online 和 IPv6</span><span class="sxs-lookup"><span data-stu-id="97659-111">Exchange Online and IPv6</span></span>

<span data-ttu-id="97659-p102">如果您用來連線至 Exchange Online 的程式支援 IPv6，它會在有線和無線網路上的預設使用 IPv6。如果您想要控制至 Exchange Online 的通訊，請在[Office 365 Url 和 IP 位址範圍](https://go.microsoft.com/fwlink/?LinkId=293744)使用 IP 位址範圍。</span><span class="sxs-lookup"><span data-stu-id="97659-p102">If the program that you use to connect to Exchange Online supports IPv6, it will use IPv6 by default on both wired and wireless networks. If you want to control communications to Exchange Online, use the IP address ranges in [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/?LinkId=293744).</span></span>
  
### <a name="sharepoint-online-and-ipv6"></a><span data-ttu-id="97659-114">SharePoint Online 和 IPv6</span><span class="sxs-lookup"><span data-stu-id="97659-114">SharePoint Online and IPv6</span></span>

 <span data-ttu-id="97659-115">**Office 365 政府版 G1/G3/G4/K1**如果您用來連線至 SharePoint Online 的程式支援 IPv6，它會嘗試使用預設的 IPv6。</span><span class="sxs-lookup"><span data-stu-id="97659-115">**Office 365 Government G1/G3/G4/K1** If the program that you use to connect to SharePoint Online supports IPv6, it will attempt to use IPv6 by default.</span></span>
  
 <span data-ttu-id="97659-p103">**公用多承租人雲端**Microsoft 在您要求時才啟用 SharePoint Online IPv6。您需要提供 CIDR 表示您的組織 DNS 基礎結構的 IP 位址。請記住您的租用戶要啟用 IPv6 的其他組織無法共用此 DNS 基礎結構。啟用 IPv6，如果您用來連線至 SharePoint Online 的程式支援 IPv6 後，它會使用預設的 IPv6。</span><span class="sxs-lookup"><span data-stu-id="97659-p103">**Public multi-tenant cloud** Microsoft enables SharePoint Online IPv6 at your request. You need to provide the CIDR notated IP addresses for your organization's DNS infrastructure. Keep in mind that this DNS infrastructure can't be shared by other organizations for IPv6 to be enabled for your tenant. After IPv6 is enabled, if the program that you use to connect to SharePoint Online supports IPv6, it uses IPv6 by default.</span></span>
  
<span data-ttu-id="97659-p104">如果您用來連線至 SharePoint Online 的程式支援 IPv6，它會在有線和無線網路上的預設使用 IPv6。如果您想要控制 to SharePoint Online 的通訊，請在[Office 365 Url 和 IP 位址範圍](https://go.microsoft.com/fwlink/?LinkId=293744)使用 IP 位址範圍。</span><span class="sxs-lookup"><span data-stu-id="97659-p104">If the program that you use to connect to SharePoint Online supports IPv6, it will use IPv6 by default on both wired and wireless networks. If you want to control communications to SharePoint Online, use the IP address ranges in [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/?LinkId=293744).</span></span>
  
 <span data-ttu-id="97659-122">**Office 365 政府版 G1/G3/G4/K1**如果您用來連線至 SharePoint Online 的程式支援 IPv6，它會嘗試使用預設的 IPv6。</span><span class="sxs-lookup"><span data-stu-id="97659-122">**Office 365 Government G1/G3/G4/K1** If the program that you use to connect to SharePoint Online supports IPv6, it will attempt to use IPv6 by default.</span></span>
  
### <a name="skype-for-business-and-ipv6"></a><span data-ttu-id="97659-123">Skype 商務和 IPv6</span><span class="sxs-lookup"><span data-stu-id="97659-123">Skype for Business and IPv6</span></span>

<span data-ttu-id="97659-p105">Microsoft 將在您要求公用多承租人 cloud 與 Office 365 政府版 G1/G3/G4/K1 訂閱啟用 IPv6 Skype for Business 的。已啟用，如果您用來連線至 Skype for Business 的程式支援 IPv6 後，它會依預設使用 IPv6。如果您想要控制 Skype for Business 的通訊，請在[Office 365 Url 和 IP 位址範圍](https://go.microsoft.com/fwlink/?LinkId=293744)使用 IP 位址範圍。</span><span class="sxs-lookup"><span data-stu-id="97659-p105">Microsoft will enable IPv6 for Skype for Business at your request in the public multi-tenant cloud and in Office 365 Government G1/G3/G4/K1 subscriptions. After it's enabled, if the program that you use to connect to Skype for Business supports IPv6, it will use IPv6 by default. If you want to control communications to Skype for Business, use the IP address ranges in [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/?LinkId=293744).</span></span>
  
<span data-ttu-id="97659-127">請注意 IPv6 不提供中的所有區域和 Microsoft 可能無法針對您的租用戶啟動這一次。</span><span class="sxs-lookup"><span data-stu-id="97659-127">Please be aware IPv6 is not available in all regions and Microsoft may not be able to activate it for your Tenant at this time.</span></span>
  
### <a name="exchange-online-protection-and-ipv6"></a><span data-ttu-id="97659-128">Exchange Online Protection 和 IPv6</span><span class="sxs-lookup"><span data-stu-id="97659-128">Exchange Online Protection and IPv6</span></span>

<span data-ttu-id="97659-p106">Exchange Online Protection (EOP) 傳輸發生透過傳輸層安全性通訊協定時才支援 IPv6。EOP 範圍內的使用[Office 365 Url 和 IP 位址範圍](https://go.microsoft.com/fwlink/?LinkId=293744)。</span><span class="sxs-lookup"><span data-stu-id="97659-p106">Exchange Online Protection (EOP) supports IPv6 if the transmission occurs over Transport Layer Security Protocol. For the EOP range, use [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/?LinkId=293744).</span></span>
  
### <a name="ipv6-support-for-office-365-government-offerings"></a><span data-ttu-id="97659-131">Office 365 政府版方案的 IPv6 支援</span><span class="sxs-lookup"><span data-stu-id="97659-131">IPv6 support for Office 365 government offerings</span></span>

<span data-ttu-id="97659-p107">Office 365 政府版方案的 IPv6 支援的資訊長的部門行政人員及行政機關，以及聯邦政府採用的網際網路通訊協定第 6 版 (IPv6 符合管理 Office 和預算 (OMB) 備忘錄) 備忘錄。[Microsoft Office 365 for Government](https://go.microsoft.com/fwlink/p/?LinkId=325414)是我們政府資料儲存在單獨分開的社群雲端中的多重租用戶服務。像其他 Office 365 方案，它可提供產能及共同作業服務，包括 Exchange Online、 Skype for Business、 SharePoint Online 和 Office Professional Plus。Microsoft Office 365 政府版方案套用僅針對 2013年及更新版本。如需 Office 365 政府版方案的詳細資訊，請參閱[公告 Office 365 for Government: 美國政府社群雲端](https://go.microsoft.com/fwlink/p/?LinkId=325414)。國際流量中召集令規定 (ITAR) 是一組美國政府法規控制匯出及匯入的防禦相關文章及[美國軍火清單 (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415)上的服務。適用於企業的 Microsoft Office 365 提供 Microsoft 安全性、 隱私權和規範需求的支援我們需要美國聯邦資訊安全聯邦機構的產能解決方案的專用裝載的服務管理 (FISMA) 憑證和商業實體主旨至 ITAR。</span><span class="sxs-lookup"><span data-stu-id="97659-p107">Office 365 IPv6 support for government offerings conforms to the Office of Management and Budget (OMB) Memorandum for Chief Information Officers of Executive Departments and Agencies, as well as the Federal Government Adoption of Internet Protocol Version 6 (IPv6) memorandum. [Microsoft Office 365 for Government](https://go.microsoft.com/fwlink/p/?LinkId=325414) is a multi-tenant service that stores US government data in a segregated community cloud. Like other Office 365 offerings, it provides productivity and collaboration services, including Exchange Online, Skype for Business, SharePoint Online, and Office Professional Plus. The Microsoft Office 365 government offerings apply only for 2013 and later. For more information about the Office 365 government offerings, see [Announcing Office 365 for Government: A US Government Community Cloud](https://go.microsoft.com/fwlink/p/?LinkId=325414). International Traffic in Arms Regulations (ITAR) is a set of US government regulations that control the export and import of defense-related articles and services on the [United States Munitions List (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415). Microsoft Office 365 for Enterprises provides dedicated hosting services for Microsoft productivity solutions that support the security, privacy, and regulatory compliance requirements for US federal agencies requiring Federal Information Security Management (FISMA) certification and commercial entities subject to ITAR.</span></span>
  
## <a name="things-to-consider-when-using-ipv6-and-office-365"></a><span data-ttu-id="97659-139">使用 IPv6 和 Office 365 時的考慮事項</span><span class="sxs-lookup"><span data-stu-id="97659-139">Things to consider when using IPv6 and Office 365</span></span>

<span data-ttu-id="97659-p108">我們建議您不要停用 IPv6。如需詳細資訊，請參閱[Microsoft windows 的 IPv6： 常見問題集](https://go.microsoft.com/fwlink/p/?LinkId=325418)。若要判斷您的網路上正在使用哪些 IP 版本，請考慮下列事項：</span><span class="sxs-lookup"><span data-stu-id="97659-p108">We recommend that you do not disable IPv6. For more information, see [IPv6 for Microsoft Windows: Frequently Asked Questions](https://go.microsoft.com/fwlink/p/?LinkId=325418). To determine what IP versions are being used on your network, consider the following:</span></span>
  
- <span data-ttu-id="97659-143">如果顯示的命令提示字元的 IPConfig 命令包含名為"IPv6 Address"Temporary IPv6 Address"的列，您的環境中有 IPv6。</span><span class="sxs-lookup"><span data-stu-id="97659-143">If the display of the IPConfig command at the command prompt contains rows named "IPv6 Address" or "Temporary IPv6 Address," you have IPv6 in your environment.</span></span>

- <span data-ttu-id="97659-144">如果所有 IPv6 位址以"fe80"開頭並對應至名為"Link-local IPv6 Address"的列，您不需要在環境中的 IPv6。</span><span class="sxs-lookup"><span data-stu-id="97659-144">If all the IPv6 addresses begin with "fe80" and correspond to rows named "Link-Local IPv6 Address," you don't have IPv6 in your environment.</span></span>

<span data-ttu-id="97659-145">這些考慮事項可能適用於您的網路：</span><span class="sxs-lookup"><span data-stu-id="97659-145">These considerations might apply to your network:</span></span>
  
- <span data-ttu-id="97659-p109">公用訂閱服務不支援透過 IPv6 進行信用卡購物。這不適用於政府社群雲端 (GCC)，因為政府具有 Enterprise 合約 (EA) 授權。</span><span class="sxs-lookup"><span data-stu-id="97659-p109">The public subscription service does not support purchase by credit card over IPv6. This does not apply to the Government Community Cloud (GCC) because governments have Enterprise Agreement (EA) licensing.</span></span>

- <span data-ttu-id="97659-148">IPv6 不支援某些 Rights Management Services (RMS) 案例。</span><span class="sxs-lookup"><span data-stu-id="97659-148">IPv6 does not support some Rights Management Services (RMS) scenarios.</span></span>

- <span data-ttu-id="97659-149">IPv6 不支援 BlackBerry® Enterprise Server (BES) 因為 BlackBerry 不支援 IPv6。</span><span class="sxs-lookup"><span data-stu-id="97659-149">IPv6 does not support BlackBerry® Enterprise Server (BES) because BlackBerry doesn't support IPv6.</span></span>

- <span data-ttu-id="97659-p110">如果您使用 Active Directory Federation Services (AD FS) 與 Office 365 時，通知您的 AD FS 網路結束點至 Office 365 IPv6 不支援使用。您不應該包含 AAAA 記錄中的 AD FS DNS 項目時使用 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="97659-p110">If you use Active Directory Federation Services (AD FS) with Office 365, advertising your AD FS network endpoint to Office 365 using IPv6 is not supported. You should not include AAAA records in the AD FS DNS entry when using Exchange Online.</span></span> 

<span data-ttu-id="97659-152">您可以使用下列短連結返回這裡：[https://aka.ms/o365ip6](https://aka.ms/o365ip6)</span><span class="sxs-lookup"><span data-stu-id="97659-152">Here's a short link you can use to come back: [https://aka.ms/o365ip6](https://aka.ms/o365ip6)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="97659-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97659-153">See also</span></span>

[<span data-ttu-id="97659-154">Microsoft 技術位置紙張</span><span class="sxs-lookup"><span data-stu-id="97659-154">Microsoft Technology Position Paper</span></span>](https://go.microsoft.com/fwlink/p/?linkid=525743)
  
[<span data-ttu-id="97659-155">TCP/IP v4 和 v6</span><span class="sxs-lookup"><span data-stu-id="97659-155">TCP/IP v4 and v6</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=211898)
  
[<span data-ttu-id="97659-156">IPv6 生存指南</span><span class="sxs-lookup"><span data-stu-id="97659-156">IPv6 Survival Guide</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=237480)
