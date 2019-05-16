---
title: 為 Office 365 設定您的網路
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/01/2018
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: ''
description: 摘要：請參閱這些文章以了解 Office 365 的網路功能。
ms.openlocfilehash: 6fb1d4d441719f61886b9263b30cdf27cbe7eaf4
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070819"
---
# <a name="set-up-your-network-for-office-365"></a>為 Office 365 設定您的網路

**摘要：** 請參閱這些文章以了解 Office 365 的網路功能。
  
對 Office 365 上線很重要的一點是，要先確定您的網路和網際網路連線已針對最佳化存取進行設定。設定您的內部部署網路以存取全域分散式的軟體即服務 (SaaS) 雲端，與針對內部部署資料中心的流量進行最佳化的傳統網路不同。 

參閱這些文章以了解主要差異，並修改您的邊緣裝置、用戶端電腦與內部部署網路，以取得最佳的使用者效能。

## <a name="how-office-365-networking-works"></a>Office 365 網路功能的運作方式

請參閱下列文章，以取得 Office 365 連線能力概觀：

- [Office 365 網路連線能力概觀](office-365-networking-overview.md)
- [Office 365 網路連線能力原則](office-365-network-connectivity-principles.md)
- [對 Office 365 的網路連線能力](network-connectivity.md)

如需提升效能的建議，請參閱 [Office 365 的網路規劃和效能調整](network-planning-and-performance.md)。

## <a name="support-office-365-networking-as-a-network-equipment-vendor"></a>支援 Office 365 網路為網路設備廠商

如果您是網路設備廠商，請加入 [Office 365 網路合作夥伴計畫](office-365-networking-partner-program.md)。註冊此計畫，將 Office 365 網路連線原則建置到您的產品與解決方案中。 

## <a name="office-365-endpoints"></a>Office 365 端點

端點為一組目的地 IP 位址、DNS 網域名稱，以及網際網路上 Office 365 流量的 URL。 

若要最佳化 Office 365 雲端式服務的效能，這些端點需要由用戶端瀏覽器和邊緣網路中的裝置進行特別處理。這些裝置包括防火牆、SSL 中斷和檢查及封包檢查裝置，以及資料外洩防護系統。

請參閱[管理 Office 365 端點](managing-office-365-endpoints.md)以取得詳細資訊。

目前有五種不同的 Office 365 雲端。下表顯示每種雲端的端點清單。

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


## <a name="additional-topics-for-office-365-networking"></a>Office 365 網路功能的其他主題

請參閱下列文章，了解 Office 365 網路功能中的特定主題：

- [內容傳遞網路](content-delivery-networks.md)
- [Office 365 服務中的 IPv6 支援](ipv6-support.md)
- [Office 365 的 NAT 支援](nat-support-with-office-365.md)

## <a name="expressroute-for-office-365"></a>ExpressRoute for Office 365

請參閱下列文章，了解針對 Office 365 流量使用 ExpressRoute 的相關資訊：

- [Azure ExpressRoute for Office 365](azure-expressroute.md)
- [實作 ExpressRoute for Office 365](implementing-expressroute.md)
- [使用 ExpressRoute for Office 365 進行網路規劃](network-planning-with-expressroute.md)
- [使用 ExpressRoute for Office 365 進行路由傳送](routing-with-expressroute.md)
