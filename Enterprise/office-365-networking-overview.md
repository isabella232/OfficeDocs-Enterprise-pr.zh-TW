---
title: Office 365 網路連線能力概觀
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/12/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: 討論網路最佳化是重要的 SaaS 服務，Office 365 網路功能的目標為何，而且 SaaS 需要不同的網路功能與其他工作負載的方式。
ms.openlocfilehash: 4acaee86136c88e5ac5b3c795f594fb056d15204
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491902"
---
# <a name="office-365-network-connectivity-overview"></a>Office 365 網路連線能力概觀

Office 365 是提供一套多樣化的微型服務和應用程式透過生產力和共同作業案例分散式的軟體為-服務 (SaaS) 雲端。 用戶端元件，例如 Outlook、 Word 和 PowerPoint 的 Office 365 的使用者電腦上執行，並連線至 Office 365 的 Microsoft 資料中心中執行的其他元件。 決定 Office 365 使用者體驗品質的最重要因素是網路可靠性與 Office 365 用戶端與 Office 365 服務前方門之間的低延遲。

在本文中，您將了解 Office 365 網路的目標，為什麼 Office 365 網路功能需要不同的方法，以比一般網際網路流量最佳化。

## <a name="office-365-networking-goals"></a>Office 365 網路目標

Office 365 網路的最終目標是讓用戶端與最接近的 Office 365 端點之間的最嚴格存取權，即可發揮最佳使用者經驗。 使用者體驗的品質直接相關的效能和回應的應用程式的使用者使用。 例如，Microsoft Teams 依賴低延遲，讓使用者電話、 會議及共用的畫面教學空閒問題，且 Outlook 依賴立即搜尋功能，可運用伺服器端編製索引和 AI 很棒的網路連線功能。

網路設計中的主要目標應該是以延遲降至最低，藉由減少的來回行程時間 (RTT) 從用戶端機器 Microsoft 全球網路，具有低延遲連接所有 Microsoft 資料中心的 Microsoft 的公用網路骨幹擴張世界各地的高可用性雲端應用程式的進入點。 您可以深入了解在[如何 Microsoft 建置其快速且可靠的全球網路](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)Microsoft 全球網路。

Office 365 網路效能最佳化不需要複雜。 您可以透過下列幾個關鍵獲得最佳效能：

- 找出 Office 365 的網路流量
- 允許 Office 365 的網路流量的本機分支的輸出至網際網路，從每個使用者連線到 Office 365 的位置
- 允許略過 proxy 和封包檢查裝置的 Office 365 流量

如需有關 Office 365 網路連線原則的詳細資訊，請參閱 < <b0>Office 365 網路連線原則</b0>。

## <a name="traditional-network-architectures-and-saas"></a>傳統的網路架構和 SaaS

傳統的網路架構原則適用於用戶端/伺服器工作負載的設計是繞其用戶端與端點之間的流量不會將公司網路外的假設。 此外，在許多企業網路中，所有輸出網際網路連線周遊公司網路，並從中央位置的輸出。

傳統網路架構，針對一般網際網路流量較高的延遲是必要的缺點為了維持網路周邊安全性，並升級或向外延展，通常牽涉到的網際網路流量最佳化效能在網路輸出點設備。 不過，這種方法並未涵蓋 SaaS 服務，例如 Office 365 的最佳化網路效能的需求。

## <a name="identifying-office-365-network-traffic"></a>識別 Office 365 的網路流量

我們正在使其成為容易識別 Office 365 的網路流量，並使其成為容易管理網路識別。

- 若要從其不會受到網際網路延遲的網路流量區分相當重要的網路流量的網路端點的新類別。 有只是少數幾個 Url 和最重要的 「 最佳化 」 類別中支援的 IP 位址。
- 用於指令碼分派狀況] 或 [直接裝置組態和變更管理 Office 365 網路識別 web 服務。 變更可從 web 服務，或 RSS 格式，或使用 Microsoft Flow 範本的電子郵件。
- [Office 365 網路合作夥伴方案](http://aka.ms/Office365NPP)與 Microsoft 合作夥伴提供的裝置或服務，請遵循 Office 365 網路連線原則，並有簡單的設定。

## <a name="securing-office-365-connections"></a>保護 Office 365 連線

傳統的網路安全性的目標是來強化公司網路周邊抵禦入侵和惡意攻擊。 大部分的企業網路強制執行網路安全性的網際網路流量使用如 proxy 伺服器、 防火牆、 SSL 符號的技術，並檢查，深層封包檢查，以及資料外洩防護系統。 這些技術提供重要的風險降低一般網際網路要求，但是可以大幅降低效能、 延展性，以及套用至 Office 365 端點時的使用者體驗的品質。

Office 365 協助符合您的組織對於內容的安全性和資料使用狀況與合規性設計特別針對 Office 365 的功能和工作量的內建的安全性和控管功能需求。 如需有關 Office 365 安全性與合規性的詳細資訊，請參閱[Office 365 安全性藍圖](https://docs.microsoft.com/en-us/office365/securitycompliance/security-roadmap)。 如需 Microsoft 的建議與支援位置上執行進階層級處理 Office 365 流量的進階的網路解決方案，請參閱[使用協力廠商的網路裝置或在 Office 365 流量的解決方案](https://support.microsoft.com/en-us/help/2690045)。

## <a name="why-is-office-365-networking-different"></a>原因 Office 365 網路不同？

Office 365 專為使用端點安全性和加密的網路連線，以減少需要周邊安全性強制的最佳效能。 Office 365 資料中心位於遍佈全球和服務的設計是要使用的用戶端連線到最佳可用的服務端點的各種方法。 因為使用者資料，以及處理為分散式許多 Microsoft 資料中心之間，機器可連線至用戶端沒有單一網路端點。 事實上，動態經過最佳化的資料與 Office 365 租用戶中的服務由 Microsoft 全球網路能否從中他們由使用者存取的地理位置。

Office 365 流量受限於封包檢查和集中式的輸出時會建立某些常見的效能問題：

- 高延遲造成視訊和音訊資料流的效能非常不佳及擷取資料、 搜尋、 即時共同作業、 行事曆空閒/忙碌資訊、 產品內的內容及其他服務的回應緩慢
- Egressing 從中央位置擊敗動態路由功能的 Office 365 全球網路的連線、 新增延遲和來回行程時間
- 解密受 SSL 安全 Office 365 的網路流量，並重新加密可能會造成通訊協定錯誤，且此安全性風險

藉由使用輸出至其地理位置盡可能關閉用戶端流量縮短 Office 365 進入點的網路路徑可改善連線 Office 365 中的效能及一般使用者體驗。 它也可以協助減少對 Office 365 效能與可靠性的網路架構未來的變更的影響。 一律會提供使用者的位置，不論是否將公司網路或遠端位置，例如 home、 飯店、 咖啡廳及機場上的網路輸出為最佳 connectivity 模型。 一般網際網路流量和 WAN 基礎公司網路流量會分別路由傳送，而不使用本機直接輸出模型。 下圖中表示此本機直接輸出模型。

![本機輸出網路架構](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)

本機輸出架構具有下列優點針對 Office 365 的網路流量透過傳統模型：
  
- 提供 Office 365 的最佳效能最佳化路由長度。 使用者連線以動態方式路由傳送至最接近的 Office 365 進入點由 Microsoft 全球網路_分散式服務 Front Door_基礎結構，及流量然後路由傳送內部資料與服務端點透過 Microsoft 的高可用性深光纖極端低延遲。
- 藉由使用 Office 365 流量，略過 proxy 和流量檢查裝置的本機輸出，可減少在公司網路基礎結構上的負載。
- 利用用戶端端點安全性和雲端安全性功能，避免應用程式的備援網路安全性技術來保護上兩個端點的連線。

> [!NOTE]
> _分散式服務 Front Door_基礎結構是 Microsoft 全球網路高度可用且擴充度佳的網路邊緣搭配地理位置分散的位置。 它會終止使用者連線和有效率地將它們路由傳送 Microsoft 全球網路內。 您可以深入了解在[如何 Microsoft 建置其快速且可靠的全球網路](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)Microsoft 全球網路。

如需有關了解及套用 Office 365 網路連線原則的詳細資訊，請參閱 < <b0>Office 365 網路連線原則</b0>。

## <a name="conclusion"></a>總結

Office 365 網路效能最佳化確實說到底就是要移除不必要的障礙。 藉由將 Office 365 連線視為受信任的流量，您可以避免延遲機型封包檢查及 proxy 頻寬競爭。 允許用戶端電腦與 Office 365 端點之間的本機連線啟用以動態方式路由傳送到 Microsoft 全球網路流量。

## <a name="related-topics"></a>相關主題

[Office 365 網路連線原則](office-365-network-connectivity-principles.md)

[Office 365 IP 位址和 URL Web 服務](office-365-ip-web-service.md)

[管理 Office 365 端點](managing-office-365-endpoints.md)

[Office 365 IP 位址和 URL Web 服務](office-365-ip-web-service.md)

[對 Office 365 的網路連線](network-connectivity.md)

[Office 365 網路與效能調整](network-planning-and-performance.md)

[使用基準與效能歷程記錄進行 Office 365 效能調整](performance-tuning-using-baselines-and-history.md)

[Office 365 的效能疑難排解規劃](performance-troubleshooting-plan.md)

[Microsoft 如何建置其快速且可靠的全球網路](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)
