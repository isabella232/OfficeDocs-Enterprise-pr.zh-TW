---
title: Office 365 網路連線概觀 （英文)
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
description: 討論為何網路最佳化，務必 saas 和服務的目標的 Office 365 網路和 saas 和需要不同的網路中其他工作負載的方式。
ms.openlocfilehash: ebd7410ec5fe421561543f1223e455377e99e625
ms.sourcegitcommit: 09985cb7894725289ef1fc8ddd90b569c285c09e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2018
ms.locfileid: "25002352"
---
# <a name="office-365-network-connectivity-overview"></a>Office 365 網路連線概觀 （英文)

Office 365 是提供透過各式各樣的微服務及應用程式的生產力和共同作業案例分散式的軟體為-a-服務 (SaaS) 雲端。例如 Outlook、 Word 及 PowerPoint 的 Office 365 的用戶端元件在使用者電腦上執行並連線至 Office 365 中 Microsoft 資料中心來執行其他元件。會決定的 Office 365 一般使用者經驗品質的最重要因素是網路可靠性與 Office 365 用戶端與 Office 365 服務前方門之間的低延遲。

在本文中，您將了解 Office 365 網路、 目標與為什麼要選擇 Office 365 網路需要比一般網際網路流量最佳化的不同方法。

## <a name="office-365-networking-goals"></a>Office 365 網路目標

Office 365 網路的最終目標是以啟用用戶端和最接近的 Office 365 端點之間的最低嚴格存取最佳化使用者經驗。一般使用者經驗品質直接相關的效能和回應使用者使用的應用程式。例如，Microsoft 小組依賴低延遲，讓使用者電話、 會議及共用] 畫面上共同作業雜音干擾的且 Outlook 依賴運用伺服器端索引與電腦控制的立即搜尋功能的更好的網路連線功能。

網路設計中的主要目標應該是以延遲降至最低降低的來回時間 (RTT) 從用戶端機器 Microsoft 通用網路、 連接 Microsoft 資料中心的所有具備低延遲的 Microsoft 的公用網路骨幹全球各地擴張高可用性雲端應用程式的進入點。您可以深入了解在[如何 Microsoft 是以其快速且可靠的通用網路](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)Microsoft 通用網路。

Office 365 網路效能最佳化不需要複雜。您可以遵循下列幾個主要原則來取得獲得最佳效能：

- 確認 Office 365 網路流量
- 允許網際網路的 Office 365 網路流量的本機分支輸出從每個使用者連線至 Office 365 的位置
- 允許略過 proxy 和封包檢查裝置的 Office 365 流量

如需有關 Office 365 網路連線原則的詳細資訊，請參閱[Office 365 網路連線原則](office-365-network-connectivity-principles.md)。

## <a name="traditional-network-architectures-and-saas"></a>傳統網路架構和 saas 和

用戶端和端點之間的流量不會將公司網路周邊網路外的假設周圍的設計被用用戶端/伺服器工作量的傳統網路架構原則。另外，許多的企業網路中所有輸出的網際網路連線周遊公司網路，並從集中位置的輸出。

傳統網路架構中較高延遲的一般網際網路流量所需的取捨以維護網路周邊安全性，且網際網路流量的效能最佳化通常需要升級或向外延展在網路輸出點的設備。不過，這個方法並未涵蓋的 saas 和服務，例如 Office 365 的最佳網路效能的需求。

## <a name="identifying-office-365-network-traffic"></a>用來識別 Office 365 網路流量

我們正在進行容易識別 Office 365 網路流量，並使其成為簡化管理網路識別。

- 若要從網際網路延遲不會影響的網路流量區分極重要的網路流量的網路端點的新類別。有剛少數 Url 和最重要的"最佳化"類別中支援的 IP 位址。
- Web 服務的指令碼分派狀況] 或 [Office 365 的直接裝置組態和變更管理網路識別碼。變更可從 web 服務或 RSS 格式或使用 Microsoft 流程範本的電子郵件。
- [Office 365 網路協力廠商程式](http://aka.ms/Office365NPP)與 Microsoft 協力廠商提供裝置或服務，請遵循 Office 365 網路連線準則而有簡單的設定。

## <a name="securing-office-365-connections"></a>保護 Office 365 的連線

傳統網路安全性的目標是強化公司網路周邊對入侵和惡意入侵的狀況。大部分的企業網路強制執行網路使用 proxy 伺服器、 防火牆、 SSL 符號技術的網際網路流量的安全性和檢查、 深入的封包檢查及資料遺失防護系統。這些技術提供一般的網際網路要求降低重要的風險，但可大幅減少效能、 延展性及套用至 Office 365 端點時的使用者體驗的品質。

Office 365 有助於符合貴組織的需求內容安全性及資料流量規範與設計特別針對 Office 365 功能及工作負載的內建安全性和管理功能。如需 Office 365 安全性及規範的詳細資訊，請參閱[Office 365 安全性藍圖](https://docs.microsoft.com/en-us/office365/securitycompliance/security-roadmap)。多個執行進階層級處理程序在 Office 365 流量的進階的網路解決方案上關於 Microsoft 的建議及支援位置資訊，請參閱[使用協力廠商網路裝置或 Office 365 流量的解決方案](https://support.microsoft.com/en-us/help/2690045)。

## <a name="why-is-office-365-networking-different"></a>為什麼要選擇 Office 365 網路不同？

Office 365 的以達最佳效能使用端點安全性和加密的網路連線，以減少需要藉助周邊安全性強制作業的設計。Office 365 資料中心位於不同全球和服務的設計目的在於使用各種方法的用戶端連線到最佳可用的服務端點。由於使用者資料及處理會分散對齊許多 Microsoft 資料中心之間，有哪些用戶端可以連線機器沒有單一網路端點。事實上，資料與您的 Office 365 租用戶中的服務以動態方式最佳化 Microsoft 通用網路能否從中他們不時常存取的使用者的地理位置。

在 Office 365 流量受限於封包檢查和集中式的輸出建立某些常見的效能問題：

- 高延遲可能會造成視訊和音訊資料流的效能非常不佳及資料擷取、 搜尋、 即時共同作業、 行事曆空閒/忙碌資訊、 產品中的內容及其他服務的速度過慢回應
- Egressing 從集中管理位置擊敗動態路由功能之 Office 365 通用網路的連線、 新增延遲和來回時間
- 解密 SSL 安全 Office 365 網路流量並重新加密它可能會造成通訊協定的錯誤與有安全性風險

允許用戶端流量輸出至其地理位置盡關閉縮短 Office 365 的進入點的網路路徑可改善連線效能與使用者體驗 Office 365 中。它也可以協助減少對 Office 365 效能與可靠性的網路架構未來變更的影響。指定連線模型是永遠提供使用者的位置，不論是否將在公司網路或遠端位置，例如 home、 旅館、 咖啡廳及機場網路輸出。一般網際網路流量及 WAN 為主的公司網路流量會分別路由傳送與未使用本機直接輸出模式。在下圖表示此本機直接輸出模型。

![本機輸出網路架構](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)

本機輸出架構會有下列優點針對 Office 365 的網路流量透過傳統模型：
  
- 提供 Office 365 的最佳效能最佳化路由長度。使用者連線動態路由傳送至最接近的 Office 365 進入點的 Microsoft 通用網路_分散式服務前方門_基礎結構、 和流量會路由傳送內部至資料和服務端點透過 Microsoft高可用性深色光纖極端低延遲。
- 允許的 Office 365 流量，略過 proxy 和流量檢查裝置的本機輸出減少公司網路基礎結構的負載。
- 利用用戶端端點的安全性與雲端安全性功能，避免應用程式的備援網路安全性技術保護兩端上的連線。

> [!NOTE]
> _分散式服務前方門_基礎結構的 Microsoft 通用網路高度可用且擴充度佳的網路邊緣的地理位置分散的位置。它會終止使用者連線並有效率地將這些路由傳送 Microsoft 通用網路內。您可以深入了解在[如何 Microsoft 是以其快速且可靠的通用網路](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)Microsoft 通用網路。

如需詳細了解及套用 Office 365 網路連線原則的詳細資訊，請參閱[Office 365 網路連線原則](office-365-network-connectivity-principles#office-365-connectivity-principles)。

## <a name="conclusion"></a>總結

Office 365 網路效能最佳化真正而言向下移除不必要的障礙。藉由將 Office 365 的連線視為信任的流量，您可以防止延遲所引進的封包檢查及 proxy 頻寬的競爭。允許用戶端機器與 Office 365 端點之間的本機連線可讓動態路由傳送到 Microsoft 通用網路流量。

## <a name="related-topics"></a>相關主題

[Office 365 網路連線原則](office-365-network-connectivity-principles.md)

[Office 365 IP 位址和 URL Web 服務](office-365-ip-web-service.md)

[管理 Office 365 端點](managing-office-365-endpoints.md)

[Office 365 IP 位址和 URL Web 服務](office-365-ip-web-service.md)

[對 Office 365 的網路連線](network-connectivity.md)

[Office 365 網路與效能調整](network-planning-and-performance.md)

[使用基準與效能歷程記錄進行 Office 365 效能調整](performance-tuning-using-baselines-and-history.md)

[Office 365 的效能疑難排解規劃](performance-troubleshooting-plan.md)

[Microsoft 如何建立其快速且可靠的通用網路](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)
