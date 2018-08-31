---
title: Office 365 美國政府 GCC 高端點
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: MET150
ms.assetid: cbd2369c-fd96-464c-bf48-c99826b459ee
description: 如果您的組織會使用 Office 365 及限制您網路上的電腦連線至網際網路，以下您會發現端點 （Fqdn、 連接埠、 Url、 IPv4 及 IPv6 位址範圍），您應該包含在您輸出允許清單以確保您電腦可以成功地使用 Office 365。
hideEdit: true
ms.openlocfilehash: eb1ac47ad8317b46ce19106e8eeab5dae3c25432
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540168"
---
# <a name="office-365-us-government-gcc-high-endpoints"></a><span data-ttu-id="b9e43-103">Office 365 美國政府 GCC 高端點</span><span class="sxs-lookup"><span data-stu-id="b9e43-103">Office 365 U.S. Government GCC High endpoints</span></span>

 <span data-ttu-id="b9e43-104">*適用於： Office 365 系統管理*</span><span class="sxs-lookup"><span data-stu-id="b9e43-104">*Applies To: Office 365 Admin*</span></span>

<span data-ttu-id="b9e43-p101">**摘要：** Office 365 需要網際網路連線。下面的端點應可使用 Office 365 美國政府 GCC 高計劃的客戶。</span><span class="sxs-lookup"><span data-stu-id="b9e43-p101">**Summary:** Office 365 requires connectivity to the Internet. The endpoints below should be reachable for customers using Office 365 U.S. Government GCC High plans only.</span></span>
  
> [!NOTE]
> <span data-ttu-id="b9e43-p102">Microsoft 已開發 rest web 服務 IP 位址及 FQDN 此頁面上的項目。此新服務可協助您設定及更新例如防火牆及 proxy 伺服器的網路周邊裝置。您可以下載端點、 清單或特定變更的目前版本的清單。XML 文件、 RSS 摘要、 和 IP 位址及 FQDN 此頁面上的項目最後會取代此服務。若要嘗試取出這個新的服務，請移至[Web 服務](managing-office-365-endpoints.md#webservice)。</span><span class="sxs-lookup"><span data-stu-id="b9e43-p102">Microsoft is developing a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service will eventually replace the XML document, RSS feed, and the IP address and FQDN entries on this page. To try out this new service, go to [Web service](managing-office-365-endpoints.md#webservice).</span></span>
  
 <span data-ttu-id="b9e43-112">**Office 365 端點：**[全球網站 （包括 GCC）](urls-and-ip-address-ranges.md) |  [Office 365 21vianet 來 21 Vianet](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 德國](office-365-germany-endpoints.md)  | [Office 365 美國政府 DoD](office-365-u-s-government-dod-endpoints.md) | *Office 365 美國政府 GCC 高* |</span><span class="sxs-lookup"><span data-stu-id="b9e43-112">**Office 365 endpoints:** [Worldwide (including GCC)](urls-and-ip-address-ranges.md) | [Office 365 operated by 21 Vianet](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 Germany](office-365-germany-endpoints.md)  | [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md) | *Office 365 U.S. Government GCC High* |</span></span>
  
|||
|:-----|:-----|
|<span data-ttu-id="b9e43-113">**上次更新：** 7/2/2018- ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [變更記錄訂閱](https://aka.ms/usendpointrss)</span><span class="sxs-lookup"><span data-stu-id="b9e43-113">**Last updated:** 7/2/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Change Log subscription](https://aka.ms/usendpointrss)</span></span> <br/> |<span data-ttu-id="b9e43-114">**下載：** 以[XML 格式](https://aka.ms/usdefenseendpoints)的完整清單</span><span class="sxs-lookup"><span data-stu-id="b9e43-114">**Download:** the full list in [XML format](https://aka.ms/usdefenseendpoints)</span></span> <br/> |
   
 <span data-ttu-id="b9e43-p103">若要了解我們建議管理使用此資料的網路連線的開頭[管理 Office 365 端點](managing-office-365-endpoints.md)。端點資料更新每個月利用新的 IP 位址及發佈前正在使用中的 30 天的 Url 的開頭。這可讓客戶不要尚未有自動更新以完成其程序，才需要的新連線。如果地址支援呈報、 安全性事件或其他立即操作需求所需的端點可能也更新期間月。以下這個頁面上顯示的資料會從 rest web 服務產生。如果您使用指令碼或網路裝置存取此資料，您應直接移至[Web 服務](managing-office-365-endpoints.md#webservice)。</span><span class="sxs-lookup"><span data-stu-id="b9e43-p103">Start with [Managing Office 365 endpoints](managing-office-365-endpoints.md) to understand our recommendations for managing network connectivity using this data. Endpoints data is updated at the beginning of each month with new IP Addresses and URLs published 30 days in advance of being active. This allows for customers who do not yet have automated updates to complete their processes before new connectivity is required. Endpoints may also be updated during the month if needed to address support escalations, security incidents, or other immediate operational requirements. The data shown on this page below is all generated from the REST-based web services. If you are using a script or a network device to access this data, you should go to the [Web service](managing-office-365-endpoints.md#webservice) directly.</span></span>

<span data-ttu-id="b9e43-p104">以下的端點資料是從使用者的電腦連線到 Office 365 需求。它不包含使用 microsoft 的網路連線到客戶網路、 有時稱為的混合或傳入的網路連線。</span><span class="sxs-lookup"><span data-stu-id="b9e43-p104">Endpoint data below lists requirements for connectivity from a user’s machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections.</span></span>

<span data-ttu-id="b9e43-p105">端點是由四個服務區域所組成。第三個服務區域可以單獨選取進行連線。第四個服務區域是常見的相依性 （稱為 Microsoft 365 一般與 Office Online） 且必須一律網路連線。</span><span class="sxs-lookup"><span data-stu-id="b9e43-p105">The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office Online) and must always have network connectivity.</span></span>

<span data-ttu-id="b9e43-126">資料行所示︰</span><span class="sxs-lookup"><span data-stu-id="b9e43-126">Data columns shown are:</span></span>

- <span data-ttu-id="b9e43-p106">**ID**： 識別碼號碼] 列中，也稱為端點設定。此識別碼為相同的 web 服務的端點組所傳回。</span><span class="sxs-lookup"><span data-stu-id="b9e43-p106">**ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.</span></span>

- <span data-ttu-id="b9e43-p107">**類別**： 顯示端點集是否分類為 「 最佳化"、"Allow"或"Default"。您可以閱讀這些類別和指引適用於管理放在[http://aka.ms/pnc](http://aka.ms/pnc)。此欄也會列出哪些端點集所需具備網路連線。不需要有網路連線的端點組，我們提供在此欄位表示如果封鎖端點集功能就是遺失的附註。如果您要排除整個服務] 區域中，列出所需的端點組不需要連線。</span><span class="sxs-lookup"><span data-stu-id="b9e43-p107">**Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [http://aka.ms/pnc](http://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.</span></span>

- <span data-ttu-id="b9e43-p108">**增**： 這是 **[是]** 如果端點組支援 Azure ExpressRoute 透過 Office 365 路由前置詞。包含所示的路由前置詞 BGP 社群對齊 [服務] 區域中所列。**無**增時，這表示 ExpressRoute 不支援此端點組。不過，它不應該假定任何路由已通告增為 [**否**] 所在集的端點。如果您打算使用 Azure AD 連線，請閱讀[特殊考量] 區段中](https://docs.microsoft.com/azure/active-directory/connect/active-directory-AADconnect-instances#microsoft-azure-government-cloud)，確定您具有適當 Azure AD 連線設定。</span><span class="sxs-lookup"><span data-stu-id="b9e43-p108">**ER**: This is **Yes** if the endpoint set is supported over Azure ExpressRoute with Office 365 route prefixes. The BGP community that includes the route prefixes shown aligns with the service area listed. When ER is **No**, this means that ExpressRoute is not supported for this endpoint set. However, it should not be assumed that no routes are advertised for an endpoint set where ER is **No**. If you plan to use Azure AD Connect, read the [special considerations section](https://docs.microsoft.com/azure/active-directory/connect/active-directory-AADconnect-instances#microsoft-azure-government-cloud) to ensure you have the appropriate Azure AD Connect configuration.</span></span>

- <span data-ttu-id="b9e43-p109">**地址**： 列出的 Fqdn 或萬用字元網域名稱和 IP 位址範圍的結束點組。請注意 IP 位址範圍新增一個 CIDR 格式而可能會在指定的網路中包含許多個別的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="b9e43-p109">**Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.</span></span>
 
- <span data-ttu-id="b9e43-p110">**連接埠**： 列出會結合表單網路端點位址的 TCP 或 UDP 連接埠。您可能會注意到一些重複 IP 位址範圍中的沒有列出不同的連接埠。</span><span class="sxs-lookup"><span data-stu-id="b9e43-p110">**Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.</span></span>
 
[!INCLUDE [Office 365 U.S. Government GCC High endpoints](./includes/office-365-u.s.-government-gcc-high-endpoints.md)]

<span data-ttu-id="b9e43-143">本表附註：</span><span class="sxs-lookup"><span data-stu-id="b9e43-143">Notes for this table:</span></span>

- <span data-ttu-id="b9e43-p111">安全性及規範中心 」 (SCC) 提供的 Azure ExpressRoute for Office 365 的支援。相同適用於透過例如報表、 稽核、 進階的 eDiscovery、 整合 DLP 及資料控管 SCC 公開的許多功能。兩個特定功能 PST 匯入和 eDiscovery 匯出目前不支援 Azure ExpressRoute 僅 Office 365 路由篩選因其 Azure Blob 存放區的相依性。若要使用這些功能，您需要使用任何可支援 Azure 連線] 選項，包括網際網路連線或 Azure ExpressRoute Azure 公用路由篩選 Azure Blob 儲存的不同連線。您必須評估為這兩個這些功能建立這類連線。Office 365 資訊保護小組所知的這項限制和主動使用兩者這些功能將支援 Azure ExpressRoute for Office 365 身分有限移到 Office 365 路由篩選。</span><span class="sxs-lookup"><span data-stu-id="b9e43-p111">The Security and Compliance Center (SCC) provides support for Azure ExpressRoute for Office 365. The same applies for many features exposed through the SCC such as Reporting, Auditing, Advanced eDiscovery, Unified DLP, and Data Governance. Two specific features, PST Import and eDiscovery Export, currently do not support Azure ExpressRoute with only Office 365 route filters due to their dependency on Azure Blob Storage. To consume those features, you need separate connectivity to Azure Blob Storage using any supportable Azure connectivity options, which include Internet connectivity or Azure ExpressRoute with Azure Public route filters. You have to evaluate establishing such connectivity for both of those features. The Office 365 Information Protection team is aware of this limitation and is actively working to bring support for Azure ExpressRoute for Office 365 as limited to Office 365 route filters for both of those features.</span></span>

- <span data-ttu-id="b9e43-p112">還有其他選用的 Office 365 ProPlus 的端點未列出並不需要使用者啟動 Office 365 ProPlus 的應用程式及編輯文件。選用的端點裝載於 Microsoft 資料中心及請勿處理、 傳輸，或將客戶資料儲存。建議的預設網際網路輸出周邊會進入使用者連線到這些端點。</span><span class="sxs-lookup"><span data-stu-id="b9e43-p112">There are additional optional endpoints for Office 365 ProPlus that are not listed and are not required for users to launch Office 365 ProPlus applications and edit documents. Optional endpoints are hosted in Microsoft datacenters and do not process, transmit, or store customer data. We recommend that user connections to these endpoints be directed to the default Internet egress perimeter.</span></span>

