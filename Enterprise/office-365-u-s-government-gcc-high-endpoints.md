---
title: Office 365 美國政府版高端點
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/09/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid: MET150
ms.assetid: cbd2369c-fd96-464c-bf48-c99826b459ee
description: 如果您的組織使用 Office 365 並限制網路上的電腦連線至網際網路，則在下列情況下，您將會發現應該包含在輸出允許清單中的端點 (Fqdn、埠、URLs、IPv4 和 IPv6 位址) 範圍，以確保您的電腦可以成功使用 Office 365。
hideEdit: true
ms.openlocfilehash: eee2b9fc3c0e1b25843806573811d333adcdec7a
ms.sourcegitcommit: 338e3bcf0a62842fbbb17145b67a4a93f3b90aac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "45091180"
---
# <a name="office-365-us-government-gcc-high-endpoints"></a>Office 365 美國政府版高端點

 *適用版本： Office 365 系統管理員*

Office 365 需要連接至網際網路。 下列端點應可供使用 Office 365 美國政府版高方案的客戶使用。
  
> [!NOTE]
> Microsoft has released a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service replaces the XML document linked from this page, which was deprecated on October 2, 2018. To try out this new service, go to [Web service](office-365-ip-web-service.md).
  
 **Office 365 端點：** [全球 (包括 GCC)](urls-and-ip-address-ranges.md) | [21 Vianet 提供的 Office 365](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 德國](office-365-germany-endpoints.md)  |  [Office 365 美國政府 DoD](office-365-u-s-government-dod-endpoints.md) | *Office 365 美國政府 GCC High* |
  
|||
|:-----|:-----|
|**上次更新：** 07/09/2020- ![ RSS ](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [變更記錄訂閱](https://endpoints.office.com/version/USGOVGCCHigh?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |**下載：** [JSON 格式](https://endpoints.office.com/endpoints/USGOVGCCHigh?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)的完整清單 <br/> |

 請從[管理 Office 365 端點](managing-office-365-endpoints.md)開始，以瞭解如何使用此資料來管理網路連線的建議。 端點資料會在每月開始時更新，並以新的 IP 位址和 URLs 在使用中之前發佈30天。 這樣一來，客戶就可以在需要新的連線之前，尚未有自動更新，就能完成他們的處理常式。 如果需要解決支援上報、安全性事件或其他立即運作需求，也可以在當月期間更新端點。 以下顯示在此頁面上的資料都是由 REST web 服務所產生。 如果您使用腳本或網路裝置來存取此資料，您應該直接前往[Web 服務](office-365-ip-web-service.md)。

Endpoint data below lists requirements for connectivity from a user’s machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections.

The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office) and must always have network connectivity.

所顯示的資料行為︰

- **ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.

- **Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [https://aka.ms/pnc](https://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.

- **ER**：如果端點集是透過 Azure ExpressRoute 與 Office 365 路由首碼一起支援，則為 **[是]** 。 包含路由首碼的 BGP 群組，會與所列的服務區域對齊。 當 ER 為**No**時，這表示此端點組不支援 ExpressRoute。 不過，不應假設在 ER 為**no**的端點集未宣告任何路由。 如果您打算使用 Azure AD Connect，請閱讀[特殊考慮區段](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-instances#microsoft-azure-government)，以確保您具有適當的 Azure ad connect 設定。

- **Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.
 
- **Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.
 
[!INCLUDE [Office 365 U.S. Government GCC High endpoints](./includes/office-365-u.s.-government-gcc-high-endpoints.md)]

本表附註：

- 安全與合規性中心 (SCC) 為 Office 365 提供 Azure ExpressRoute 的支援。 這同樣適用于透過 SCC 公開的許多功能，例如報告、審核、高級 eDiscovery、整合 DLP 和資料管理。 兩個特定功能（PST 匯入和 eDiscovery 匯出）目前不支援只有 Office 365 路由篩選器的 Azure ExpressRoute，因為它們對 Azure Blob 儲存區有相依的依賴性。 若要使用這些功能，您需要使用任何可支援的 Azure 連線選項（包括網際網路連線或 azure 公用路由篩選器的 Azure ExpressRoute），以個別的方式連接至 Azure Blob 儲存。 您必須評估這兩種功能的建立這類連線能力。 Office 365 資訊保護小組已注意到這項限制，而且目前正致力於為 Office 365 提供 Azure ExpressRoute 的支援，這些功能限制于 Office 365 的路由篩選器。

- Microsoft 365 應用程式的其他選用端點未列出，而且不需要讓使用者啟動 Microsoft 365 應用程式以供企業應用程式和編輯檔。 選用端點主控于 Microsoft 資料中心，不會處理、傳送或儲存客戶資料。 建議您將這些端點的使用者連線導向預設的網際網路出局周邊。

