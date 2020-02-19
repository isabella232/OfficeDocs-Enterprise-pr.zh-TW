---
title: Office 365 網路效能觀點 （預覽）
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
description: Office 365 網路效能觀點 （預覽）
ms.openlocfilehash: 2e57ffabec5b2172cb36f10135406ddda95bc1c5
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106288"
---
# <a name="office-365-network-performance-insights-preview"></a>Office 365 網路效能觀點 （預覽）

在 Microsoft 365 系統管理中心網路效能頁會顯示 Office 365 網路 insights，可協助在設計網路周邊的辦公室位置。 有五個可能會顯示每個辦公室地點的特定網路觀點。

>[!IMPORTANT]
>網路效能建議、 深入了解 Microsoft 365 系統管理中心中的評估目前處於預覽狀態，並只適用於具有已註冊功能預覽計畫的 Office 365 租用戶。

## <a name="backhauled-network-egress"></a>Backhauled 網路輸出

從使用者的位置到網路輸出距離大於 500 英哩 （800 公里），這預期會影響效能。 建議使用本機輸出更接近給使用者。

如此可識別的辦公室位置與網路輸出之間的距離是超過 500 英哩。 模糊化的用戶端電腦位置所識別的辦公室位置及網路輸出位置由使用反向的 IP 位址至位置資料庫。 辦公室位置可能不正確，如果 Windows 位置服務已停用在機器上。 網路輸出位置可能有不精準的反向的 IP 位址資料庫資訊不正確。

此深入了解詳細資料包含辦公室地點、 網路輸出位置，以及它們之間的距離。

針對此深入了解我們建議更接近網路輸出的辦公室位置來使連線可以完備傳閱給 Microsoft 的網路上網際網路和到 Office 365 服務前方門。 需要關閉網路輸出辦公室位置也可讓以改善效能在未來為 Microsoft 的使用者在未來展開目前狀態和 Office 365 服務前方門這兩個網路資料的點。

此深入了解是為 「 輸出"縮寫某些摘要檢視中。

## <a name="better-performance-detected-for-customers-near-you"></a>偵測到您附近的客戶獲得較佳效能

自相當數量的地鐵區域中的客戶在組織中有更好的效能，比使用者此辦公室位置。

這會尋找在 Office 365 客戶中為此辦公室位置的相同市/鎮彙總效能。

![相對的網路效能](Media/m365-mac-perf/m365-mac-perf-relative-perf.png)

我們計算較佳效能 bucket 的相同市/鎮中的 Office 365 客戶的百分比。 如果此數字] 如果 10%的多個接著，我們示範網路深入解析。

此深入了解是為 「 對等 」 縮寫某些摘要檢視中。

## <a name="use-of-a-non-optimal-exchange-online-service-front-door"></a>使用的非最佳 Exchange Online 服務的前哨

使用者無法連線至最佳的 Office 365 服務前哨，這預期會影響效能。

我們列出 Exchange Online 服務前方門這是適用於從具有良好效能的辦公室位置市/鎮。 如果目前的測試顯示不在此清單上使用 Exchange Online 服務前哨，我們呼叫出這個建議。

使用非最佳 Exchange Online 服務的前哨可能被因網路 backhaul 公司網路輸出之前在此情況下建議本機和直接的網路輸出。 它也可能被造成所使用的遠端 DNS 遞迴解析程式伺服器在此情況下建議對齊 DNS 遞迴解析程式伺服器具有網路輸出。

此深入了解為某些摘要檢視中會縮寫成 「 路徑 」。

## <a name="use-of-non-optimal-sharepoint-online-service-front-door"></a>使用的非最佳 SharePoint Online 服務的前哨

使用者不連線至最接近 SharePoint Online 服務的前哨。 這被預期會影響效能。

我們找出測試用戶端連線至 SharePoint Online 服務前哨。 然後針對的辦公室位置市/鎮我們比較，必須是 SharePoint Online 服務的前哨針對該縣/市。 如果它不符合，我們做此建議。

此深入了解為某些摘要檢視中會縮寫成 「 Afd 」。

## <a name="low-download-speed-from-sharepoint-front-door"></a>從 SharePoint 前哨低的下載速度

Sub 最佳化網路下載速度偵測到這會影響從商務用 OneDrive 載入文件所需的時間長度。

使用者可以取得從 SharePoint Online 和 OneDrive for Business 服務前方門測量單位為 mb (mbps) 的下載速度。 如果這個值是小於 1 MBps 我們會提供此深入了解。

若要改善下載速度的使用者都可以取得頻寬可能需要增加。 或者，可能是網路壅塞之間的辦公室位置的使用者機器和 SharePoint Online 服務前哨。 這有時稱為 congestive 遺失，而且它將限制可用的下載速度給使用者，即使有足夠的頻寬。

此深入了解為某些摘要檢視中會縮寫成 「 輸送量 」。

## <a name="related-topics"></a>相關主題

[在 Microsoft 365 系統管理中心 （預覽） 的網路效能建議](office-365-network-mac-perf-overview.md)

[Office 365 網路評估 （預覽）](office-365-network-mac-perf-score.md)

[Office 365 網路上架工具 M365 系統管理中心 （預覽）](office-365-network-mac-perf-onboarding-tool.md)
