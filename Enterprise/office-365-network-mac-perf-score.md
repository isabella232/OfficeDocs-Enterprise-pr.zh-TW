---
title: Office 365 網路評估 （預覽）
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 02/04/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Office 365 網路評估 （預覽）
ms.openlocfilehash: f919eeb2771095502865b4a5079b91eb8d7efe36
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106281"
---
# <a name="office-365-network-assessment-preview"></a>Office 365 網路評估 （預覽）

Office 365 網路評估會指出從客戶網路連線相對的使用者體驗的影響。 任何 Microsoft 的影響所擁有的網路連線能力排除此選項可讓客戶能夠最佳化他們所負責的網路設計。

它是影響使用者經驗中重要的 Office 365 工作負載的度量單位從計算並顯示為 0 到 100 個範圍的百分比表示。

非常低的網路分數建議 Office 365 用戶端會有連線或剩餘使用者回應的重大問題。 分數的 80%表示網路連線，您應該不預期會有接收使用者抱怨您的 Office 365 使用者體驗由於網路效能。 對網路連線能力增強功能，此分數會增加以及使用者體驗。

>[!IMPORTANT]
>網路效能建議、 深入了解 Microsoft 365 系統管理中心中的評估目前處於預覽狀態，並只適用於具有已註冊功能預覽計畫的 Office 365 租用戶。

## <a name="exchange-online"></a>Exchange Online

Exchange online TCP 被測量至 Exchange 前端伺服器與用戶端機器延遲。 這會受到網路，透過 LAN 及 WAN 的客戶的距離。 它可以也會受到網路介裝置或服務延遲連線或會造成重新傳送的封包。

## <a name="sharepoint-online"></a>SharePoint Online

SharePoint Online 的計算，供使用者存取的文件的下載速度。 這可以在用戶端電腦與 Microsoft 的網路之間的網路電路上可用的頻寬受到影響。 通常也會受到網路壅塞存在於中不佳的涵蓋範圍 Wi-fi 區域或複雜的網路裝置中的瓶頸。

## <a name="microsoft-teams"></a>Microsoft Teams

對於 Microsoft Teams 的網路品質被測量 UDP 延遲、 UDP 抖動和 UDP 封包遺失。 UDP 用於通話和會議的音訊和視訊媒體連線，對於 Microsoft Teams。 這會受到與除了網路 UDP 支援的連線間隔的延遲和下載速度的相同因素自 UDP 分別設定為較常見的 TCP 通訊協定。

## <a name="tenant-network-score-and-office-location-network-score"></a>租用戶網路分數和辦公室位置網路分數

網路分數測量的周邊網路與 Microsoft 的網路辦公室位置的設計。 在每個辦公室的位置，最好的做法周邊網路的改善，是或其中彙總的網路連線可能會影響多個位置的增強功能。
我們會顯示在 [網路效能概觀] 頁面上整個的 Office 365 租用戶的網路分數並在該位置的摘要] 頁面上每個偵測到的辦公室位置的特定網路分數。

## <a name="network-score-panel"></a>網路分數面板

是否針對租用戶或特定 office 位置會顯示與詳細資料，分數的面板，每個網路分數。 此面板顯示分數的橫條圖的百分比，為每個元件工作負載，包括僅工作負載的總點收到度量單位的資料。 對於 office 位置網路分數我們也會顯示這是報告中為您的辦公室位置的相同市/鎮資料的所有 Office 365 用戶端的中位數的基準。

分數分解為面板中的顯示每個元件工作負載的分數。

分數歷程記錄會顯示分數和基準在過去 30 天。

## <a name="related-topics"></a>相關主題

[在 Microsoft 365 系統管理中心 （預覽） 的網路效能建議](office-365-network-mac-perf-overview.md)

[Office 365 網路效能觀點 （預覽）](office-365-network-mac-perf-insights.md)

[Office 365 網路上架工具 M365 系統管理中心 （預覽）](office-365-network-mac-perf-onboarding-tool.md)
