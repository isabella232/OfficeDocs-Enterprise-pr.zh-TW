---
title: Office 365 Germany 端點
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/29/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 8a113a50-0071-4155-bb8e-eba5a8dbd4c8
description: 如果您的組織使用 Office 365 並限制網路上的電腦連線至網際網路，則在下列情況下，您將會發現應該包含在輸出允許清單中的端點（Fqdn、埠、URLs 及 IPv4 和 IPv6 位址範圍），以確保您的電腦可以成功使用 Office 365。
hideEdit: true
ms.openlocfilehash: 89c9cf212e1101af222a915e60b0e1f82a3e5f26
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998282"
---
# <a name="office-365-germany-endpoints"></a>Office 365 Germany 端點

 *適用版本： Office 365 系統管理員*

Office 365 需要連接至網際網路。 下列端點應可供使用**Office 365 德國**方案的客戶使用。
  
> [!NOTE]
> Microsoft has released a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service replaces the XML document linked from this page, which was deprecated on October 2, 2018. To try out this new service, go to [Web service](office-365-ip-web-service.md).
 
 **Office 365 端點：** [全球 (包括 GCC)](urls-and-ip-address-ranges.md)  | [21 Vianet 提供的 Office 365](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 德國* |  [Office 365 美國政府 DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 美國政府 GCC High](office-365-u-s-government-gcc-high-endpoints.md)  |
  
|||
|:-----|:-----|
|**上次更新：** 06/29/2020- ![ RSS ](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [變更記錄訂閱](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) |**下載：** 一個 [JSON 格式](https://endpoints.office.com/endpoints/Germany?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)清單中所有必要與選用的目的地。  <br/> |

請從[管理 Office 365 端點](managing-office-365-endpoints.md)開始，以瞭解如何使用此資料來管理網路連線的建議。 端點資料會在每月開始時更新，並以新的 IP 位址和 URLs 在使用中之前發佈30天。 這樣一來，客戶就可以在需要新的連線之前，尚未有自動更新，就能完成他們的處理常式。 如果需要解決支援上報、安全性事件或其他立即運作需求，也可以在當月期間更新端點。 您可以一直參考[變更記錄訂閱](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)。

以下顯示在此頁面上的資料都是由 REST web 服務所產生。 如果您使用腳本或網路裝置來存取此資料，您應該直接前往[Web 服務](office-365-ip-web-service.md)。

Endpoint data below lists requirements for connectivity from a user’s machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections.

The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office) and must always have network connectivity.

所顯示的資料行為︰

- **ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.

- **Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [https://aka.ms/pnc](https://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.

- **ER**: This is **Yes** if the endpoint set is supported over Azure ExpressRoute with Office 365 route prefixes. The BGP community that includes the route prefixes shown aligns with the service area listed. When ER is **No**, this means that ExpressRoute is not supported for this endpoint set. However, it should not be assumed that no routes are advertised for an endpoint set where ER is **No**.

- **Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.
 
- **Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.

[!INCLUDE [Office 365 Germany endpoints](./includes/office-365-germany-endpoints.md)]

 

