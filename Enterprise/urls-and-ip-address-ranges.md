---
title: Office 365 URL 和 IP 位址範圍
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- MOM160
- BCS160
ms.assetid: 8548a211-3fe7-47cb-abb1-355ea5aa88a2
description: 摘要：Office 365 需要連線到網際網路。客戶必須可使用 Office 365 方案取得下列端點，包括 Government Community Cloud (GCC)。
hideEdit: true
ms.openlocfilehash: 2e6f5afd097aa85c09847b58fd3166961116b773
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540236"
---
# <a name="office-365-urls-and-ip-address-ranges"></a><span data-ttu-id="1b85e-104">Office 365 URL 和 IP 位址範圍</span><span class="sxs-lookup"><span data-stu-id="1b85e-104">Office 365 URLs and IP address ranges</span></span>

 <span data-ttu-id="1b85e-p102">**摘要：** Office 365 需要連線到網際網路。客戶必須可使用 Office 365 方案取得下列端點，包括 Government Community Cloud (GCC)。</span><span class="sxs-lookup"><span data-stu-id="1b85e-p102">**Summary:** Office 365 requires connectivity to the Internet. The endpoints below should be reachable for customers using Office 365 plans, including Government Community Cloud (GCC).</span></span>
  
> [!NOTE]
> <span data-ttu-id="1b85e-p103">Microsoft 正開發以 REST 為基礎且適用於此頁面上的 IP 位址和 FQDN 項目的 web 服務。這項新服務可協助您設定及更新網路周邊裝置，例如防火牆和 Proxy 伺服器。您可以下載端點的清單、最新版的清單，或是特定變更。這項服務最後會取代從此頁面連結的 XML 文件。若要嘗試這項新服務，請移至 [Web 服務](managing-office-365-endpoints.md#webservice)。</span><span class="sxs-lookup"><span data-stu-id="1b85e-p103">Microsoft is developing a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service will eventually replace the XML document linked from this page. To try out this new service, go to [Web service](managing-office-365-endpoints.md#webservice).</span></span> 
  
<span data-ttu-id="1b85e-112">*Office 365 全球 (+GCC)* | [21 Vianet 提供的 Office 365](urls-and-ip-address-ranges-21vianet.md) | [Office 365 德國](office-365-germany-endpoints.md) | [Office 365 美國政府 DoD](office-365-u-s-government-dod-endpoints.md)  | [Office 365 美國政府 GCC High](office-365-u-s-government-gcc-high-endpoints.md) |</span><span class="sxs-lookup"><span data-stu-id="1b85e-112">*Office 365 Worldwide (+GCC)* | [Office 365 operated by 21 Vianet](urls-and-ip-address-ranges-21vianet.md) | [Office 365 Germany](office-365-germany-endpoints.md) | [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md)  | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md) |</span></span>
  
||||
|:-----|:-----|:-----|
|<span data-ttu-id="1b85e-113">**上次更新：** 8/1/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [變更記錄訂閱](https://go.microsoft.com/fwlink/p/?linkid=236301) (英文)</span><span class="sxs-lookup"><span data-stu-id="1b85e-113">**Last updated:** 8/1/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Change Log subscription](https://go.microsoft.com/fwlink/p/?linkid=236301)</span></span> <br/> |<span data-ttu-id="1b85e-114">**下載：** 所有必要與選用目的地於一個 [XML 格式](https://go.microsoft.com/fwlink/?LinkId=533185)清單。</span><span class="sxs-lookup"><span data-stu-id="1b85e-114">**Download:** all required and optional destinations in one [XML formatted](https://go.microsoft.com/fwlink/?LinkId=533185) list.</span></span>  <br/> | <span data-ttu-id="1b85e-115">**使用：** 我們的 proxy [PAC 檔案](managing-office-365-endpoints.md#pacfiles)</span><span class="sxs-lookup"><span data-stu-id="1b85e-115">**Use:** our proxy [PAC files](managing-office-365-endpoints.md#pacfiles)</span></span> <br/> |
   
 <span data-ttu-id="1b85e-p104">開始使用[管理 Office 365 端點](managing-office-365-endpoints.md)了解我們的建議，可使用這項資料來管理網路連線。每個月初都會使用在使用中的 30 天前發行的新 IP 位址和 URL 更新端點資料。這項功能可讓尚未自動化更新的使用者在需要新的連線之前完成其程序。如果提出支援向上呈報、安全性事件或其他立即操作需求需要端點，可能也會在當月期間更新端點。下面這個頁面上所顯示的資料會從 REST 為基礎的 web 服務產生。如果您使用指令碼或網路裝置來存取這些資料，就應該直接前往 [Web 服務](managing-office-365-endpoints.md#webservice)。</span><span class="sxs-lookup"><span data-stu-id="1b85e-p104">Start with [Managing Office 365 endpoints](managing-office-365-endpoints.md) to understand our recommendations for managing network connectivity using this data. Endpoints data is updated at the beginning of each month with new IP Addresses and URLs published 30 days in advance of being active. This allows for customers who do not yet have automated updates to complete their processes before new connectivity is required. Endpoints may also be updated during the month if needed to address support escalations, security incidents, or other immediate operational requirements. The data shown on this page below is all generated from the REST-based web services. If you are using a script or a network device to access this data, you should go to the [Web service](managing-office-365-endpoints.md#webservice) directly.</span></span>

<span data-ttu-id="1b85e-p105">下列端點資料列出使用者的電腦到 Office 365 的連線需求。這不包括從 Microsoft 到客戶網路的網路連線，有時稱為混合式或輸入網路連線。</span><span class="sxs-lookup"><span data-stu-id="1b85e-p105">Endpoint data below lists requirements for connectivity from a user’s machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections.</span></span>

<span data-ttu-id="1b85e-p106">端點則被歸類成四個服務區域。前三個服務區域可以個別選取進行連線。第四個服務區域 (稱為 Microsoft 365 Common 與 Office Online) 的常見相依性，且必須一律具有網路連線能力。</span><span class="sxs-lookup"><span data-stu-id="1b85e-p106">The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office Online) and must always have network connectivity.</span></span>

<span data-ttu-id="1b85e-127">所顯示的資料行為︰</span><span class="sxs-lookup"><span data-stu-id="1b85e-127">Data columns shown are:</span></span>

- <span data-ttu-id="1b85e-p107">**識別碼**：資料列的識別碼，也就是端點設定。此 ID 與端點設定的 web 服務所傳回的相同。</span><span class="sxs-lookup"><span data-stu-id="1b85e-p107">**ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.</span></span>

- <span data-ttu-id="1b85e-p108">**類別**：顯示端點設定是否分類為「最佳」、「允許」或「預設」。您可以在[http://aka.ms/pnc](http://aka.ms/pnc)讀取這些類別和在其中管理的指導方針。此欄也會列出網路連線需要哪些端點設定。對於不需要有網路連線的端點設定，我們會在這個欄位中提供附註，表示如果端點設定受到封鎖，將會遺失什麼功能。如果您不包含整個服務區域，視需要列出的端點設定將不需要連線能力。</span><span class="sxs-lookup"><span data-stu-id="1b85e-p108">**Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [http://aka.ms/pnc](http://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.</span></span>

- <span data-ttu-id="1b85e-p109">**ER**：如果端點設定透過 Azure ExpressRoute 使用 Office 365 路由首碼支援，則這是 [是]\*\*\*\*。包含所顯示路由首碼的 BGP 社群會對齊所列的服務區域。當 ER 為 [否]\*\*\*\* 時，表示 ExpressRoute 不支援此端點集合。不過，不應假設 ER 為 [否]\*\*\*\* 的端點設定不會通告任何路由。</span><span class="sxs-lookup"><span data-stu-id="1b85e-p109">**ER**: This is **Yes** if the endpoint set is supported over Azure ExpressRoute with Office 365 route prefixes. The BGP community that includes the route prefixes shown aligns with the service area listed. When ER is **No**, this means that ExpressRoute is not supported for this endpoint set. However, it should not be assumed that no routes are advertised for an endpoint set where ER is **No**.</span></span>

- <span data-ttu-id="1b85e-p110">**地址**：列出端點設定的 FQDN 或萬用字元網域名稱及 IP 位址範圍。請注意，IP 位址範圍為 CIDR 格式，且在指定的網路中可能包含讓多個個別的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="1b85e-p110">**Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.</span></span>
 
- <span data-ttu-id="1b85e-p111">**連接埠**：列出與地址結合以形成網路端點的 TCP 或 UDP 連接埠。您可能會注意到列出不同連接埠的某些 IP 位址範圍中有重複項目。</span><span class="sxs-lookup"><span data-stu-id="1b85e-p111">**Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.</span></span>

[!INCLUDE [Office 365 worldwide endpoints](./includes/office-365-worldwide-endpoints.md)]

## <a name="related-topics"></a><span data-ttu-id="1b85e-143">相關主題</span><span class="sxs-lookup"><span data-stu-id="1b85e-143">Related Topics</span></span>

[<span data-ttu-id="1b85e-144">管理 Office 365 端點</span><span class="sxs-lookup"><span data-stu-id="1b85e-144">Office 365 Germany endpoints</span></span>](managing-office-365-endpoints.md)
  
[<span data-ttu-id="1b85e-145">Office 365 連線能力疑難排解</span><span class="sxs-lookup"><span data-stu-id="1b85e-145">Office 365 connectivity limits</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d.aspx)
  
[<span data-ttu-id="1b85e-146">用戶端連線</span><span class="sxs-lookup"><span data-stu-id="1b85e-146">Client connectivity</span></span>](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[<span data-ttu-id="1b85e-147">內容傳遞網路</span><span class="sxs-lookup"><span data-stu-id="1b85e-147">Content delivery networks</span></span>](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[<span data-ttu-id="1b85e-148">Microsoft Azure Datacenter IP 範圍</span><span class="sxs-lookup"><span data-stu-id="1b85e-148">Microsoft Azure Datacenter IP Ranges</span></span>](https://www.microsoft.com/download/details.aspx?id=41653)
  
[<span data-ttu-id="1b85e-149">Microsoft 公用 IP 空間</span><span class="sxs-lookup"><span data-stu-id="1b85e-149">Microsoft Public IP Space</span></span>](https://www.microsoft.com/download/details.aspx?id=53602)

