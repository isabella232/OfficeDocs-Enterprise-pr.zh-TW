---
title: Office 365 網路連線能力概述
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/5/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: 討論為何網路優化對於 SaaS 服務非常重要, Office 365 網路的目標, 以及 SaaS 如何與其他工作負載不同的網路。
ms.openlocfilehash: e1ae446d7a69d0fab83e7dd4aa253bd1120e6c08
ms.sourcegitcommit: 99bf8739dfe1842c71154ed9548ebdd013c7e59e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2019
ms.locfileid: "35017283"
---
# <a name="office-365-network-connectivity-overview"></a>Office 365 網路連線能力概述

Office 365 是分散式的軟體即服務 (SaaS) 雲端, 可透過一組不同的微服務和應用程式提供生產力和共同作業案例。 Office 365 的用戶端元件, 例如 Outlook、Word 和 PowerPoint 在使用者電腦上執行, 並連接到在 Microsoft 資料中心執行的 Office 365 的其他元件。 決定 Office 365 使用者體驗品質的最重要因素, 是 Office 365 用戶端與 Office 365 服務前端之間的網路可靠性和低延遲。

在本文中, 您將瞭解 Office 365 網路的目標, 以及為什麼 Office 365 網路需要不同的方法來優化一般網際網路流量。

## <a name="office-365-networking-goals"></a>Office 365 網路目標

Office 365 網路的最終目標是在用戶端和最接近的 Office 365 端點之間啟用最小限制存取, 以優化使用者體驗。 使用者經驗品質與使用者所使用之應用程式的效能及回應能力直接相關。 例如, Microsoft 團隊依賴低延遲, 讓使用者電話通話、會議和共用螢幕共同作業不會造成任何問題, 而 Outlook 則依賴出色的網路連線來進行即時搜尋功能, 以利用伺服器端的索引和 AI能力.

網路設計的主要目標是將用戶端電腦的往返時間 (RTT) 減少為 Microsoft 全球網路, 並將所有 Microsoft 資料中心與低延遲互連在一起, 以減少延遲時間。, 高可用性雲端應用程式進入點遍佈世界各地。 您可以在[Microsoft 如何建立其快速且可靠的通用網路](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/), 深入瞭解 Microsoft 全球網路。

優化 Office 365 網路效能不需要很複雜。 您可以遵循下列幾個重要的原則, 取得最佳的效能:

- 識別 Office 365 網路流量
- 允許使用者連線至 Office 365 的每個位置, 從每個位置, 允許 Office 365 網路流量的本機分支出口
- 允許 Office 365 流量略過 proxy 與封包檢查裝置

如需 Office 365 網路連線原則的詳細資訊, 請參閱[office 365 網路連線原則](office-365-network-connectivity-principles.md)。

## <a name="traditional-network-architectures-and-saas"></a>傳統的網路架構和 SaaS

用戶端/伺服器工作負載的傳統網路架構原則, 是圍繞用戶端與端點之間的流量所設計, 不會延伸到公司網路周邊之外。 此外, 在許多商業網路中, 所有的輸出網際網路連線都會透過公司網路, 以及從中央位置外出。

在傳統的網路架構中, 一般網際網路流量的較高延遲是維護網路周邊安全性所需的折衷措施, 而且網際網路流量的效能優化通常包括升級或擴充網路出局點的裝置。 不過, 此方法並不會解決 SaaS 服務 (例如 Office 365) 的最佳網路效能需求。

## <a name="identifying-office-365-network-traffic"></a>識別 Office 365 網路流量

我們讓您更容易識別 Office 365 網路流量, 並簡化網路識別的管理。

- 新類別的網路端點, 以區分高重要的網路流量與不受網際網路延遲影響的網路流量。 在最重要的「優化」類別中, 只會有少數 Url 和支援 IP 位址。
- Web 服務以取得腳本使用方式, 或直接裝置設定, 以及 Office 365 網路識別的變更管理。 您可以從 web 服務或 RSS 格式, 或使用 Microsoft 流程範本在電子郵件上進行變更。
- [Office 365 網路合作夥伴計畫](http://aka.ms/Office365NPP), 其中的 Microsoft 合作夥伴提供的裝置或服務遵循 Office 365 網路連線原則並具有簡單的設定。

## <a name="securing-office-365-connections"></a>保護 Office 365 連線的安全

傳統網路安全性的目標是加強公司網路周邊, 防範入侵和惡意攻擊。 大部分的商業網路會使用類似 proxy 伺服器、防火牆、SSL 中斷、檢查、深入封包檢查和資料遺失防護系統等技術, 來強制執行網際網路流量的網路安全性。 這些技術可提供一般網際網路要求的重要風險減輕, 但是可以大幅降低效能、擴充性, 以及套用至 Office 365 端點時的使用者體驗品質。

Office 365 使用專為 Office 365 功能和工作負載而設計的內建安全性和控管功能, 協助滿足您組織的內容安全性和資料使用性的需求。 如需有關 Office 365 安全性和合規性的詳細資訊, 請參閱[Office 365 安全性藍圖](https://docs.microsoft.com/en-us/office365/securitycompliance/security-roadmap)。 如需在執行 Office 365 流量的高級網路解決方案上, Microsoft 建議和支援位置的詳細資訊, 請參閱在[office 365 流量上使用協力廠商網路裝置或解決方案](https://support.microsoft.com/en-us/help/2690045)。

## <a name="why-is-office-365-networking-different"></a>為什麼 Office 365 網路是不同的？

Office 365 的設計是使用端點安全性和加密網路連線來優化效能, 以減少周邊安全性強制執行的需求。 Office 365 資料中心位於全球, 且服務的設計目的是使用各種方法將用戶端連線至最佳可用的服務端點。 因為使用者資料和處理是分散在許多 Microsoft 資料中心, 所以用戶端電腦無法連線的單一網路端點。 事實上, Office 365 租使用者中的資料和服務會透過 Microsoft 全球網路進行動態優化, 以適應使用者存取使用者的地理位置。

當 Office 365 流量受到封包檢查和集中式外出時, 就會建立一些常見的效能問題:

- 高延遲可能會造成影片和音訊資料流程的效能不良, 以及資料檢索、搜尋、即時共同作業、行事曆空閒/忙碌資訊、產品內容及其他服務的回應速度緩慢
- 來自中央位置的 Egressing 連線會破壞 Office 365 通用網路的動態路由功能、新增延遲時間和往返時間
- 解密 SSL 安全的 Office 365 網路流量並重新加密可能會造成通訊協定錯誤, 並有安全性風險

透過讓用戶端流量盡可能接近其地理位置, 以縮短 Office 365 進入點的網路路徑, 可改善連線效能和 Office 365 中的使用者體驗。 它也可協助您降低未來對 Office 365 效能和可靠性的網路架構所造成的影響。 最佳連線模型是在使用者的位置始終提供網路出局, 不論這是在公司網路還是在家、酒店、咖啡店和機場等遠端位置。 一般網際網路流量和 WAN 的公司網路流量將會分開路由, 且不會使用本機直接輸出模式。 此本機直接輸出模型會在下圖中表示。

![本機出局網路架構](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)

本機出局架構針對傳統模型的 Office 365 網路流量有下列優點:
  
- 優化路由長度, 以提供最佳的 Office 365 效能。 使用者連線會透過 Microsoft 全球網路的_分散式服務前端_基礎結構, 動態路由傳送至最接近的 Office 365 進入點, 然後流量會在內部路由傳送至 microsoft 的資料和服務端點。超低延遲高可用性深纖程。
- 透過允許 Office 365 流量的本機出口, 以減少公司網路基礎結構的負載, 略過 proxy 和流量檢查裝置。
- 利用用戶端端點安全性和雲端安全性功能, 以避免應用冗余網路安全性技術, 來保護兩端的連線。

> [!NOTE]
> _分散式服務前端_基礎結構是 Microsoft 全球網路的高度可用和可伸縮網路 edge, 以及地理位置分散的位置。 它會終止使用者連線, 並有效地將它們路由傳送至 Microsoft 全球網路中。 您可以在[Microsoft 如何建立其快速且可靠的通用網路](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/), 深入瞭解 Microsoft 全球網路。

如需瞭解並套用 Office 365 網路連線原則的詳細資訊, 請參閱[office 365 網路連線原則](office-365-network-connectivity-principles.md)。

## <a name="conclusion"></a>總結

優化 Office 365 網路效能實際上會降低移除不必要的障礙。 將 Office 365 連線視為信任的流量, 可防止資料包檢查和競爭的 proxy 頻寬帶來延遲。 允許用戶端機器與 Office 365 端點之間的本機連線可透過 Microsoft 全球網路動態路由傳送流量。

## <a name="related-topics"></a>相關主題

[Office 365 網路連線原則](office-365-network-connectivity-principles.md)

[管理 Office 365 端點](managing-office-365-endpoints.md)

[Office 365 URL 與 IP 位址範圍](urls-and-ip-address-ranges.md) (英文)

[Office 365 IP 位址和 URL Web 服務](office-365-ip-web-service.md)

[評估 Office 365 網路連線能力](assessing-network-connectivity.md)

[Office 365 網路與效能調整](network-planning-and-performance.md)

[評估 Office 365 網路連線能力](assessing-network-connectivity.md)

[使用基準與效能歷程記錄進行 Office 365 效能調整](performance-tuning-using-baselines-and-history.md)

[Office 365 的效能疑難排解規劃](performance-troubleshooting-plan.md)

[內容傳遞網路](content-delivery-networks.md)

[Office 365 網路上架工具](https://aka.ms/netonboard)

[Microsoft 如何建立其快速且可靠的通用網路](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[Office 365 網路博客](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
