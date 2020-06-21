---
title: 設定 Microsoft 365 的網路
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/19/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_TLGs
ms.assetid: ''
description: 摘要：請參閱下列文章，以瞭解 Microsoft 365 的網路。
ms.openlocfilehash: 4c414d8cbf597af9165e991a71e5d6a6a330e33a
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2020
ms.locfileid: "44735653"
---
# <a name="set-up-your-network-for-microsoft-365"></a>設定 Microsoft 365 的網路

*本文適用于 Microsoft 365 Enterprise 和 Office 365 企業版。*

An important part of your Microsoft 365 onboarding is to ensure that your network and Internet connections are set up for optimized access. Configuring your on-premises network to access a globally distributed Software-as-a-Service (SaaS) cloud is different from a traditional network that is optimized for traffic to on-premises datacenters and a central Internet connection. 

參閱這些文章以了解主要差異，並修改您的邊緣裝置、用戶端電腦與內部部署網路，以為您的內部使用者取得最佳的效能。

## <a name="how-microsoft-365-networking-works"></a>Microsoft 365 網路的運作方式

請參閱下列文章，以瞭解 Microsoft 365 的連線能力：

- [Microsoft 365 網路連線能力概觀](office-365-networking-overview.md)
- [Microsoft 365 網路連接原則](office-365-network-connectivity-principles.md)
- [評估 Microsoft 365 網路連線能力](assessing-network-connectivity.md)

如需增強效能的建議，請參閱[Microsoft 365 的網路規劃和效能調整](network-planning-and-performance.md)。

## <a name="support-microsoft-365-networking-as-a-network-equipment-vendor"></a>支援 Microsoft 365 網路作為網路設備廠商

If you are a network equipment vendor, join the [Office 365 Networking Partner Program](office-365-networking-partner-program.md). Enroll in the program to build Office 365 network connectivity principles into your products and solutions. 

## <a name="office-365-endpoints"></a>Office 365 端點

端點為一組目的地 IP 位址、DNS 網域名稱，以及網際網路上 Office 365 流量的 URL。 

To optimize performance to Office 365 cloud-based services, some endpoints need special handling by your client browsers and the devices in your edge network. These devices include firewalls, SSL Break and Inspect and packet inspection devices, and data loss prevention systems.

請參閱[管理 Office 365 端點](managing-office-365-endpoints.md)以取得詳細資訊。

There are currently five different Office 365 clouds. This table takes you to the list of endpoints for each one.

|||
|:-------|:-----|
| [全球端點](urls-and-ip-address-ranges.md) | 全球 Office 365 訂閱的端點，包括美國政府社群雲端 (GCC)。 |
| [美國政府 DoD 端點](office-365-u-s-government-dod-endpoints.md) | 適用於美國國防部 (DoD) 訂閱的端點。 |
| [美國政府 GCC High 端點](office-365-u-s-government-gcc-high-endpoints.md) | 適用於美國政府社群雲端高 (GCC High) 訂閱的端點。 |
| [由 21Vianet 營運的 Office 365 端點](urls-and-ip-address-ranges-21vianet.md) | 由 21Vianet 營運的 Office 365 端點，其目的是為了符合中國的 Office 365 需求。 |
| [Office 365 Germany 端點](office-365-germany-endpoints.md) | 針對德國、歐盟 (EU) 以及歐洲自由貿易聯盟 (EFTA) 中受管制客戶的歐洲個別雲端端點。 |
|||

若要自動取得您 Office 365 雲端的最新端點清單，請參閱 [Office 365 IP 位址和 URL Web 服務](office-365-ip-web-service.md)。

如需其他端點，請參閱下列文章：

- [未包含在 Web 服務中的其他端點](additional-office365-ip-addresses-and-urls.md)
- [Mac 版 Office 2016 中的網路要求](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-microsoft-365-networking"></a>Microsoft 365 網路的其他主題

請參閱下列文章，瞭解 Microsoft 365 網路中的特殊主題：

- [內容傳遞網路](content-delivery-networks.md)
- [Office 365 服務中的 IPv6 支援](ipv6-support.md)
- [Office 365 的 NAT 支援](nat-support-with-office-365.md)

## <a name="expressroute-for-microsoft-365"></a>適用於 Microsoft 365 的 ExpressRoute

請參閱下列文章，了解針對 Office 365 流量使用 ExpressRoute 的相關資訊：

- [Azure ExpressRoute for Office 365](azure-expressroute.md)
- [實作 ExpressRoute for Office 365](implementing-expressroute.md)
- [使用 ExpressRoute for Office 365 進行網路規劃](network-planning-with-expressroute.md)
- [使用 ExpressRoute for Office 365 進行路由傳送](routing-with-expressroute.md)
