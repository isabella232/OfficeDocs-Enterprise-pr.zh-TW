---
title: 21Vianet 運作的 Office 365 的 URL 和 IP 位址範圍
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
search.appverid:
- GMA150
- GPA150
- GEA150
ms.assetid: 5c47c07d-f9b6-4b78-a329-bfdc1b6da7a0
description: 本文適用於由中國 21Vianet 運作的 Office 365。本文章會列出 21Vianet 運作的 Office 365 所使用的 URL 和 IP 位址範圍。
hideEdit: true
ms.openlocfilehash: 83147b27a3237bb7fbb3c63b739a0f3fcb401b92
ms.sourcegitcommit: d07feeba2e886febc6a57a5c33b0df02b3db5631
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "23827181"
---
# <a name="urls-and-ip-address-ranges-for-office-365-operated-by-21vianet"></a><span data-ttu-id="8da71-104">21Vianet 運作的 Office 365 的 URL 和 IP 位址範圍</span><span class="sxs-lookup"><span data-stu-id="8da71-104">URLs and IP address ranges for Office 365 operated by 21Vianet</span></span>

 <span data-ttu-id="8da71-105">*適用於：21Vianet 運作的 Office 365 - 小型企業系統管理員，21Vianet 運作的 Office 365 - 系統管理員*</span><span class="sxs-lookup"><span data-stu-id="8da71-105">*Applies To: Office 365 operated by 21Vianet - Small Business Admin, Office 365 operated by 21Vianet - Admin*</span></span>

<span data-ttu-id="8da71-106">**摘要**：下列端點 (FQDN、 連接埠、URL、IPv4 和 IPv6 前置字元) 適用於 21Vianet 運作的 Office 365，且專門針對只使用這些計畫為組織提供生產力服務所設計。</span><span class="sxs-lookup"><span data-stu-id="8da71-106">**Summary**: The following endpoints (FQDNs, ports, URLs, IPv4, and IPv6 prefixes) apply to Office 365 operated by 21 Vianet and are designed to deliver productivity services to organizations using only these plans.</span></span>
  
> [!NOTE]
> <span data-ttu-id="8da71-p102">Microsoft 正開發以 REST 為基礎且適用於此頁面上的 IP 位址和 FQDN 項目的 Web 服務。這項新服務可協助您設定及更新網路周邊裝置，例如防火牆和 Proxy 伺服器。您可以下載端點的清單、最新版的清單，或是特定變更。這項服務最後會取代此頁面上的 XML 文件。若要嘗試這項新服務，請移至 [Web 服務](office-365-ip-web-service.md)。</span><span class="sxs-lookup"><span data-stu-id="8da71-p102">Microsoft is developing a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service will eventually replace the XML document on this page. To try out this new service, go to [Web service](office-365-ip-web-service.md).</span></span> 
  
 <span data-ttu-id="8da71-112">**Office 365 端點：** [全球 (包括 GCC)](urls-and-ip-address-ranges.md)  | *21 Vianet 提供的 Office 365* | [Office 365 德國](office-365-germany-endpoints.md) |  [Office 365 美國政府 DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 美國政府 GCC High](office-365-u-s-government-gcc-high-endpoints.md) |</span><span class="sxs-lookup"><span data-stu-id="8da71-112">**Office 365 endpoints:** [Worldwide (including GCC)](urls-and-ip-address-ranges.md)  | *Office 365 operated by 21 Vianet* | [Office 365 Germany](office-365-germany-endpoints.md) | [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md) |</span></span>
  
|||
|:-----|:-----|
|<span data-ttu-id="8da71-113">**上次更新：** 8/1/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [變更記錄訂閱](http://go.microsoft.com/fwlink/?LinkId=536386) (英文)</span><span class="sxs-lookup"><span data-stu-id="8da71-113">**Last updated:** 8/1/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Change Log subscription](http://go.microsoft.com/fwlink/?LinkId=536386)</span></span>||

<span data-ttu-id="8da71-p103">開始使用[管理 Office 365 端點](managing-office-365-endpoints.md)了解我們的建議，可使用這項資料來管理網路連線。每個月初都會使用在使用中的 30 天前發行的新 IP 位址和 URL 更新端點資料。這項功能可讓尚未自動化更新的使用者在需要新的連線之前完成其程序。如果提出支援向上呈報、安全性事件或其他立即操作需求需要端點，可能也會在當月期間更新端點。下面這個頁面上所顯示的資料會從 REST 為基礎的 Web 服務產生。如果您使用指令碼或網路裝置來存取這些資料，就應該直接前往 [Web 服務](office-365-ip-web-service.md)。</span><span class="sxs-lookup"><span data-stu-id="8da71-p103">Start with [Managing Office 365 endpoints](managing-office-365-endpoints.md) to understand our recommendations for managing network connectivity using this data. Endpoints data is updated at the beginning of each month with new IP Addresses and URLs published 30 days in advance of being active. This allows for customers who do not yet have automated updates to complete their processes before new connectivity is required. Endpoints may also be updated during the month if needed to address support escalations, security incidents, or other immediate operational requirements. The data shown on this page below is all generated from the REST-based web services. If you are using a script or a network device to access this data, you should go to the [Web service](office-365-ip-web-service.md) directly.</span></span>

<span data-ttu-id="8da71-p104">下列端點資料列出使用者的電腦到 Office 365 的連線需求。這不包括從 Microsoft 到客戶網路的網路連線，有時稱為混合式或輸入網路連線。</span><span class="sxs-lookup"><span data-stu-id="8da71-p104">Endpoint data below lists requirements for connectivity from a user’s machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections.</span></span>

<span data-ttu-id="8da71-p105">端點則被歸類成四個服務區域。前三個服務區域可以個別選取進行連線。第四個服務區域 (稱為 Microsoft 365 Common 與 Office Online) 的常見相依性，且必須一律具有網路連線能力。</span><span class="sxs-lookup"><span data-stu-id="8da71-p105">The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office Online) and must always have network connectivity.</span></span>

<span data-ttu-id="8da71-125">所顯示的資料行為︰</span><span class="sxs-lookup"><span data-stu-id="8da71-125">Data columns shown are:</span></span>

- <span data-ttu-id="8da71-p106">**識別碼**：資料列的識別碼，也就是端點設定。此 ID 與端點設定的 web 服務所傳回的相同。</span><span class="sxs-lookup"><span data-stu-id="8da71-p106">**ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.</span></span>

- <span data-ttu-id="8da71-p107">**類別**：顯示端點設定是否分類為「最佳」、「允許」或「預設」。您可以在[http://aka.ms/pnc](http://aka.ms/pnc)讀取這些類別和在其中管理的指導方針。此欄也會列出網路連線需要哪些端點設定。對於不需要有網路連線的端點設定，我們會在這個欄位中提供附註，表示如果端點設定受到封鎖，將會遺失什麼功能。如果您不包含整個服務區域，視需要列出的端點設定將不需要連線能力。</span><span class="sxs-lookup"><span data-stu-id="8da71-p107">**Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [http://aka.ms/pnc](http://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.</span></span>

- <span data-ttu-id="8da71-p108">**ER**：如果端點設定透過 Azure ExpressRoute 使用 Office 365 路由首碼支援，則這是 [是]\*\*\*\*。包含所顯示路由首碼的 BGP 社群會對齊所列的服務區域。當 ER 為 [否]\*\*\*\* 時，表示 ExpressRoute 不支援此端點集合。不過，不應假設 ER 為 [否]\*\*\*\* 的端點設定不會通告任何路由。</span><span class="sxs-lookup"><span data-stu-id="8da71-p108">**ER**: This is **Yes** if the endpoint set is supported over Azure ExpressRoute with Office 365 route prefixes. The BGP community that includes the route prefixes shown aligns with the service area listed. When ER is **No**, this means that ExpressRoute is not supported for this endpoint set. However, it should not be assumed that no routes are advertised for an endpoint set where ER is **No**.</span></span>

- <span data-ttu-id="8da71-p109">**地址**：列出端點設定的 FQDN 或萬用字元網域名稱及 IP 位址範圍。請注意，IP 位址範圍為 CIDR 格式，且在指定的網路中可能包含讓多個個別的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="8da71-p109">**Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.</span></span>
 
- <span data-ttu-id="8da71-p110">**連接埠**：列出與地址結合以形成網路端點的 TCP 或 UDP 連接埠。您可能會注意到列出不同連接埠的某些 IP 位址範圍中有重複項目。</span><span class="sxs-lookup"><span data-stu-id="8da71-p110">**Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.</span></span>

[!INCLUDE [Office 365 operated by 21Vianet endpoints](./includes/office-365-operated-by-21vianet-endpoints.md)]

