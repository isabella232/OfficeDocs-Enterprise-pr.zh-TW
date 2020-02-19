---
title: 在 Microsoft 365 系統管理中心 （預覽） 的網路效能建議
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
description: 在 Microsoft 365 系統管理中心 （預覽） 的網路效能建議的概觀
ms.openlocfilehash: d944814effc62956d5047bad1f3088d0919793ee
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106282"
---
# <a name="network-performance-recommendations-in-the-microsoft-365-admin-center-preview"></a>在 Microsoft 365 系統管理中心 （預覽） 的網路效能建議

網路效能] 頁面上，Microsoft 365 系統管理中心中的顯示企業客戶網路見解和網路分數。 網路觀點特有建議網路架構設計來改善網路連線至 Office 365 與網路分數與相關的使用者經驗的變更顯示的網路連線能力如何影響使用者經驗允許的比較不同的使用者位置網路連線。 [Office 365，或以修復網路效能問題其初始上架期間發現與使用量包含多個辦公室的位置和非一般的網路周邊架構可以受益於這使用 Office 365 企業版成長。 這通常是不需要使用 Office 365 或任何企業已簡單且直接的網路連線的小型企業。 企業超過 500 位使用者與多個辦公室的位置都應該最獲益。

>[!IMPORTANT]
>網路效能建議、 深入了解 Microsoft 365 系統管理中心中的評估目前處於預覽狀態，並只適用於具有已註冊功能預覽計畫的 Office 365 租用戶。

## <a name="enterprise-network-connectivity-challenges"></a>企業網路連線能力的挑戰

![客戶網路到雲端](Media/m365-mac-perf/m365-mac-perf-first-last-mile.png)

許多企業的網路周邊設定以已成長到一段時間，以及主要是專為容納員工的網際網路網站存取其中大部分的網站不事先知道，而不受信任。 主流和必要焦點時避免惡意程式碼，並漁船攻擊從這些未知的網站。 此網路組態的策略，雖然很有幫助基於安全性考量，可能會導致 Office 365 使用者效能及提升使用者經驗降低。 企業可以提升使用者經驗，但也會繼續對安全的下列[Office 365 連線能力原則](https://aka.ms/pnc)以及使用新的 Microsoft 365 系統管理中心網路效能功能推出其環境。 這項功能可協助網路架構設計的配合 Office 365 連線能力原則，而且應該會導致連線到 Office 365 的最佳化的網路效能。

## <a name="how-we-can-solve-these-challenges"></a>我們可以在如何解決這些挑戰

Microsoft 有時要求的大型企業客戶調查 Office 365 的網路效能問題，這些經常有關於客戶網路輸出基礎結構的根本原因。 常見的根本原因的客戶網路周邊問題找到我們 seek 識別簡單的測試度量單位時，會識別它。 測試與識別特定問題的度量單位閾值很有用，因為我們可以測試的任何位置的同一個度量、 告訴是否此根本原因在於有及與管理員共用作為網路深入解析。 某些網路觀點只會指出需要進一步調查問題。 我們有足夠的測試，以顯示特定的補救動作來修正的根本原因的其中網路深入了解被列為建議的動作。 這些網路深入了解根據度量單位從過去預定的臨界值會比一般的最佳作法建議更重要，因為您不需要在詢問是否特定的最佳作法適用於，並且會導致相當數量的使用者經驗改進或不.

## <a name="network-performance-overview-in-the-microsoft-365-admin-center"></a>在 Microsoft 365 系統管理中心中的網路效能概觀

Microsoft 有現有的網路度量單位從包含數個 Office 桌面和網頁用戶端支援 Office 365 的作業。 現在，這些度量單位從正在可用來提供網路架構設計深入解析和網路效能分數所顯示的網路效能] 頁面上，在 Microsoft 365 系統管理中心。

網路度量單位從相關聯的大約位置資訊可以識別用戶端裝置的所在位置的市/鎮。 這用來顯示客戶辦公室的位置和網路度量單位會分組為該辦公室位置提供網路觀點。 在每個位置的網路分數會顯示含有色彩和相對的每個位置的使用者數目由圓形的大小。 [概觀] 頁面上也會顯示網路分數客戶的加權平均值為跨所有辦公室的位置。

## <a name="specific-office-location-network-performance-summary-and-insights"></a>特定辦公室位置網路效能摘要和深入解析

選取 [辦公室位置會開啟位置特定摘要] 頁面。 我們顯示已識別該辦公室地點的度量單位從網路輸出的詳細的資料。

辦公室位置的 [摘要] 頁面此外顯示位置網路分數，網路分數歷程記錄，這個位置分數的比較其他客戶在相同位置的城市，以及特定的見解和客戶可以進行若要建議的清單改善其網路連線能力。 在相同的縣/市客戶之間的比較取決於所有客戶都必須等於存取網路服務提供者，電信基礎結構，以及附近的 Microsoft 網路點的目前狀態的期望。

辦公室位置] 頁面上的 [詳細資料] 索引標籤會顯示已用於有人任何深入資訊、 建議和網路分數特定的度量單位結果。 這被提供，使網路工程師可以驗證建議和納入任何條件約束或其環境中的特定內容。
對於想要改善 office 的精確度的客戶提供位置和建議提供我們允許輸入更特定的資訊。 這藉由編輯探索到的位置資訊，並可減少中可用的網路度量單位的位置資訊固有近似值。

## <a name="faq"></a>常見問題集

### <a name="what-is-office-365-service-front-door"></a>什麼是 Office 365 服務的前哨？

Office 365 服務的前哨是在 Office 用戶端和服務終止其網路連線的 Microsoft 全球網路上的進入點。 為 Office 365 最佳化網路連線，建議您的網路連線會終止到最接近 Office 365 的前哨縣/市或 metro 中。
附註： Office 365 服務的前哨在 Azure marketplace 中有可用的 「 Azure Front Door 服務 」 產品並沒有直接關聯性。

### <a name="what-is-an-optimal-office-365-service-front-door"></a>什麼是最佳的 Office 365 服務前哨？

最佳的 Office 365 服務前哨就是最靠近您的網路輸出，通常在您的縣/市] 或 [metro 區域。 使用 Office 365 網路效能工具來判斷您正在使用 Office 365 服務的前哨及最佳服務的前哨的位置。 此工具會決定您正在使用的前哨是最佳選擇，然後在完備連接到 Microsoft 全球網路。

### <a name="what-is-an-internet-egress-location"></a>網際網路的輸出位置為何？

網際網路輸出位置是您的網路流量結束企業網路和連線到網際網路的位置。 這也被視為位置，您必須在網路位址轉譯 (NAT) 裝置，而且通常連線與網際網路服務提供者 (ISP)。 如果您看到長途電話您的位置和您網際網路輸出位置之間，這可能會識別重大的 WAN backhaul。

## <a name="related-topics"></a>相關主題

[Office 365 網路效能觀點 （預覽）](office-365-network-mac-perf-insights.md)

[Office 365 網路評估 （預覽）](office-365-network-mac-perf-score.md)

[Office 365 網路上架工具 M365 系統管理中心 （預覽）](office-365-network-mac-perf-onboarding-tool.md)
