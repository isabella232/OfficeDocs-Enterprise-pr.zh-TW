---
title: Office 365 Germany 端點
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 8a113a50-0071-4155-bb8e-eba5a8dbd4c8
description: 如果您的組織會使用 Office 365 及限制您網路上的電腦連線至網際網路，以下您會發現端點 （Fqdn、 連接埠、 Url 及 IPv4 和 IPv6 位址範圍），您應該包含在您輸出允許清單以確保您電腦可以成功地使用 Office 365。
hideEdit: true
ms.openlocfilehash: fa5133391a24a3b9bb82a9dc5065e4dd10bb5bfe
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539922"
---
# <a name="office-365-germany-endpoints"></a><span data-ttu-id="f94bb-103">Office 365 Germany 端點</span><span class="sxs-lookup"><span data-stu-id="f94bb-103">Office 365 Germany endpoints</span></span>

 <span data-ttu-id="f94bb-104">*適用於： Office 365 系統管理*</span><span class="sxs-lookup"><span data-stu-id="f94bb-104">*Applies To: Office 365 Admin*</span></span>

<span data-ttu-id="f94bb-p101">**摘要：** Office 365 需要網際網路連線。下面的端點應該是客戶使用**Office 365 德國**計劃僅連至。</span><span class="sxs-lookup"><span data-stu-id="f94bb-p101">**Summary:** Office 365 requires connectivity to the Internet. The endpoints below should be reachable for customers using **Office 365 Germany** plans only.</span></span>
  
> [!NOTE]
> <span data-ttu-id="f94bb-p102">Microsoft 已開發 rest web 服務 IP 位址及 FQDN 此頁面上的項目。此新服務可協助您設定及更新例如防火牆及 proxy 伺服器的網路周邊裝置。您可以下載端點、 清單或特定變更的目前版本的清單。XML 文件、 RSS 摘要、 和 IP 位址及 FQDN 此頁面上的項目最後會取代此服務。若要嘗試取出這個新的服務，請移至[Web 服務](managing-office-365-endpoints.md#webservice)。</span><span class="sxs-lookup"><span data-stu-id="f94bb-p102">Microsoft is developing a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service will eventually replace the XML document, RSS feed, and the IP address and FQDN entries on this page. To try out this new service, go to [Web service](managing-office-365-endpoints.md#webservice).</span></span> 
  
 <span data-ttu-id="f94bb-112">**Office 365 端點：**[全球網站 （包括 GCC）](urls-and-ip-address-ranges.md)  |  [Office 365 21vianet 來 21 Vianet](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 德國* | [Office 365 美國政府 DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 美國政府 GCC 高](office-365-u-s-government-gcc-high-endpoints.md)  |</span><span class="sxs-lookup"><span data-stu-id="f94bb-112">**Office 365 endpoints:** [Worldwide (including GCC)](urls-and-ip-address-ranges.md)  | [Office 365 operated by 21 Vianet](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 Germany* | [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md)  |</span></span>
  
|||
|:-----|:-----|
|<span data-ttu-id="f94bb-113">**上次更新：** 7/2/2018- ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [清單中的 Office 365 德國端點的變更](office-365-germany-endpoints-change-log.md)</span><span class="sxs-lookup"><span data-stu-id="f94bb-113">**Last updated:** 7/2/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [List of changes to the Office 365 Germany endpoints](office-365-germany-endpoints-change-log.md)</span></span>||

<span data-ttu-id="f94bb-p103">若要了解我們建議管理使用此資料的網路連線的開頭[管理 Office 365 端點](managing-office-365-endpoints.md)。端點資料更新每個月利用新的 IP 位址及發佈前正在使用中的 30 天的 Url 的開頭。這可讓客戶不要尚未有自動更新以完成其程序，才需要的新連線。如果地址支援呈報、 安全性事件或其他立即操作需求所需的端點可能也更新期間月。您一律可以參照[的變更到 Office 365 德國端點清單](office-365-germany-endpoints-change-log.md)。</span><span class="sxs-lookup"><span data-stu-id="f94bb-p103">Start with [Managing Office 365 endpoints](managing-office-365-endpoints.md) to understand our recommendations for managing network connectivity using this data. Endpoints data is updated at the beginning of each month with new IP Addresses and URLs published 30 days in advance of being active. This allows for customers who do not yet have automated updates to complete their processes before new connectivity is required. Endpoints may also be updated during the month if needed to address support escalations, security incidents, or other immediate operational requirements. You can always refer to the [list of changes to the Office 365 Germany endpoints](office-365-germany-endpoints-change-log.md).</span></span>

<span data-ttu-id="f94bb-p104">以下這個頁面上顯示的資料會從 rest web 服務產生。如果您使用指令碼或網路裝置存取此資料，您應直接移至[Web 服務](managing-office-365-endpoints.md#webservice)。</span><span class="sxs-lookup"><span data-stu-id="f94bb-p104">The data shown on this page below is all generated from the REST-based web services. If you are using a script or a network device to access this data, you should go to the [Web service](managing-office-365-endpoints.md#webservice) directly.</span></span>

<span data-ttu-id="f94bb-p105">以下的端點資料是從使用者的電腦連線到 Office 365 需求。它不包含使用 microsoft 的網路連線到客戶網路、 有時稱為的混合或傳入的網路連線。</span><span class="sxs-lookup"><span data-stu-id="f94bb-p105">Endpoint data below lists requirements for connectivity from a user’s machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections.</span></span>

<span data-ttu-id="f94bb-p106">端點是由四個服務區域所組成。第三個服務區域可以單獨選取進行連線。第四個服務區域是常見的相依性 （稱為 Microsoft 365 一般與 Office Online） 且必須一律網路連線。</span><span class="sxs-lookup"><span data-stu-id="f94bb-p106">The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office Online) and must always have network connectivity.</span></span>

<span data-ttu-id="f94bb-126">資料行所示︰</span><span class="sxs-lookup"><span data-stu-id="f94bb-126">Data columns shown are:</span></span>

- <span data-ttu-id="f94bb-p107">**ID**： 識別碼號碼] 列中，也稱為端點設定。此識別碼為相同的 web 服務的端點組所傳回。</span><span class="sxs-lookup"><span data-stu-id="f94bb-p107">**ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.</span></span>

- <span data-ttu-id="f94bb-p108">**類別**： 顯示端點集是否分類為 「 最佳化"、"Allow"或"Default"。您可以閱讀這些類別和指引適用於管理放在[http://aka.ms/pnc](http://aka.ms/pnc)。此欄也會列出哪些端點集所需具備網路連線。不需要有網路連線的端點組，我們提供在此欄位表示如果封鎖端點集功能就是遺失的附註。如果您要排除整個服務] 區域中，列出所需的端點組不需要連線。</span><span class="sxs-lookup"><span data-stu-id="f94bb-p108">**Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [http://aka.ms/pnc](http://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.</span></span>

- <span data-ttu-id="f94bb-p109">**增**： 這是 **[是]** 如果端點組支援 Azure ExpressRoute 透過 Office 365 路由前置詞。包含所示的路由前置詞 BGP 社群對齊 [服務] 區域中所列。**無**增時，這表示 ExpressRoute 不支援此端點組。不過，它不應該假定任何路由已通告增為 [**否**] 所在集的端點。</span><span class="sxs-lookup"><span data-stu-id="f94bb-p109">**ER**: This is **Yes** if the endpoint set is supported over Azure ExpressRoute with Office 365 route prefixes. The BGP community that includes the route prefixes shown aligns with the service area listed. When ER is **No**, this means that ExpressRoute is not supported for this endpoint set. However, it should not be assumed that no routes are advertised for an endpoint set where ER is **No**.</span></span>

- <span data-ttu-id="f94bb-p110">**地址**： 列出的 Fqdn 或萬用字元網域名稱和 IP 位址範圍的結束點組。請注意 IP 位址範圍新增一個 CIDR 格式而可能會在指定的網路中包含許多個別的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="f94bb-p110">**Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.</span></span>
 
- <span data-ttu-id="f94bb-p111">**連接埠**： 列出會結合表單網路端點位址的 TCP 或 UDP 連接埠。您可能會注意到一些重複 IP 位址範圍中的沒有列出不同的連接埠。</span><span class="sxs-lookup"><span data-stu-id="f94bb-p111">**Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.</span></span>

[!INCLUDE [Office 365 Germany endpoints](./includes/office-365-germany-endpoints.md)]

 

