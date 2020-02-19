---
title: Office 365 網路上架工具 M365 系統管理中心 （預覽）
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
description: Office 365 網路上架工具 M365 系統管理中心 （預覽）
ms.openlocfilehash: 7ead201d78c1a6ce971c6ff09d4be9c0d2c76be6
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106283"
---
# <a name="office-365-network-onboarding-tool-in-the-m365-admin-center-preview"></a>Office 365 網路上架工具 M365 系統管理中心 （預覽）

Office 365 網路上架工具位於<https://connectivity.office.com>。 它是附加的工具，以網路深入解析和網路分數資訊，可在 Microsoft 365 系統管理中心在**健康情況下 |網路效能**功能表。

網路深入了解 Microsoft 365 系統管理中心根據您的 Office 365 租用戶的產品內測量值。 相較之下，Office 365 網路上架工具的網路觀點，會在本機上工具中執行。 測試，可在產品完成限制及執行測試使用者的本機更多資料可收集產生更深入的見解。 然後請考慮網路深入了解 Microsoft 365 系統管理中心中的會顯示已運用在特定的辦公室位置上的 Office 365 的網路問題。 Office 365 網路上架工具可協助識別建議的網路效能改進動作而導致該問題的根本原因。

我們建議，這些一起使用可評估為 Microsoft 365 系統管理中心中每個辦公室位置的網路品質狀態，並測試部署之後，可以找到更多細節根據 Office 365 網路上架工具。

>[!IMPORTANT]
>網路效能建議、 深入了解 Microsoft 365 系統管理中心中的評估目前處於預覽狀態，並只適用於具有已註冊功能預覽計畫的 Office 365 租用戶。

## <a name="the-advanced-tests-client-application"></a>進階的測試用戶端應用程式

有兩個組件至 Office 365 網路上架工具。 沒有網站<https://connectivity.office.com>，而且沒有可下載的 Windows 用戶端應用程式。 可下載的用戶端執行進階的網路連線測試，且大多數的測試需要此選項，即可執行。

您可以從網站中，執行進階用戶端測試，它會填入結果回 [web] 頁面上，因為它會執行。

![O365 網路上架工具測試結果範例](Media/m365-mac-perf/m365-mac-perf-onboarding-tool-tests.png)

## <a name="user-office-location"></a>使用者的辦公室位置

使用者網頁瀏覽器中偵測到使用者的辦公室位置。 它用來識別特定的組件的企業周邊網路的網路距離。

[地圖] 檢視會顯示使用者的辦公室位置。

## <a name="distance-to-the-network-egress-location"></a>距離的網路輸出位置

我們找出伺服器端的網路輸出 IP 位址。 位置資料庫用來查閱網路輸出的概略位置，並判斷該位置到的位置之間的距離。 如果超過 500 英哩 （800 公里） 之間的距離，這會顯示為網路深入解析。

網路輸出位置是 [地圖] 檢視會顯示，而連線至指出內部企業 WAN 網路 backhaul 使用者辦公室位置。

從網路輸出 IP 位址進行查閱的位置可能不正確，這會從這項測試會導致為 false 的結果。 若要驗證如果發生此錯誤針對特定的 IP 位址您可以使用可公開存取的網路的 IP 位址位置的網站。

Office 365 網路連線，建議您實作從使用者的辦公室位置的本機和直接的網路輸出至網際網路。 本機和直接輸出的改善，是解決這個網路深入解析的最佳方式。

## <a name="exchange-online-service-front-door"></a>Exchange Online 服務的前哨

在 Outlook 執行此動作，以及我們測量網路給它的 TCP 延遲從使用者的辦公室位置的相同方式來識別正在使用 Exchange Online 服務的前哨。 這些記錄會同時顯示與正在使用 Exchange Online 服務的前哨相較於清單中的目前位置的建議最佳服務前方門。 如果未最佳化 Exchange Online 服務的前哨正在使用中，這會顯示為網路深入解析。

使用非最佳 Exchange Online 服務的前哨可能被因網路 backhaul 公司網路輸出之前在此情況下建議本機和直接的網路輸出。 它也可能被造成所使用的遠端 DNS 遞迴解析程式伺服器在此情況下建議對齊 DNS 遞迴解析程式伺服器具有網路輸出。

我們在 Exchange Online 服務前哨 TCP 延遲計算潛在的改進。 這是透過查看已測試的使用者辦公室位置網路延遲與減去室網路延遲從目前的位置 Exchange Online 服務的前哨。 差異代表改進的潛在機會。

## <a name="comparison-of-performance-of-customers-in-the-area"></a>效能的區域中的客戶的比較

網路 TCP 延遲，Exchange Online 服務前哨之使用者辦公室位置是相較於其他 Office 365 的客戶在相同的地鐵區域。 網路深入了解會顯示 10%或以上的客戶相同地鐵區域中有更好的效能。

此網路深入了解就會產生根據縣/市中的所有使用者都擁有存取權的同一個電訊基礎結構，以及相同鄰近的網際網路電路和 Microsoft 的網路。

## <a name="in-use-default-gateway"></a>在 [使用預設閘道

在 [使用預設閘道是路由器，測試用戶端已針對路由的 TCP/IP 網路連線設定。

這僅提供資訊，而且不會增加任何網路深入解析。

## <a name="in-use-dns-servers"></a>使用 DNS 伺服器

這會顯示在 [執行測試用戶端電腦上設定之 DNS 伺服器。 不過，這並不常見，它可能是 DNS 遞迴解析程式伺服器。 很多可能會為 DNS 轉寄站伺服器的 DNS 結果會快取，並將轉寄至另一部 DNS 伺服器任何未快取的 DNS 要求。

這僅提供資訊，而且不會增加任何網路深入解析。

## <a name="identified-dns-recursive-resolver-server"></a>已識別的 DNS 遞迴解析程式伺服器

在使用 DNS 遞迴解析程式識別的特定的 DNS 要求，然後它會接收來自同一個要求的 IP 位址詢問 DNS 名稱伺服器。 此 IP 位址是 DNS 遞迴解析程式，它會查閱以找出該位置的 IP 位址位置資料庫中。 然後計算使用者的辦公室位置至 DNS 遞迴解析程式伺服器的位置之間的距離。 如果超過 500 英哩 （800 公里） 之間的距離，這會顯示為網路深入解析。

從網路輸出 IP 位址進行查閱的位置可能不正確，這會從這項測試會導致為 false 的結果。 若要驗證如果發生此錯誤針對特定的 IP 位址您可以使用可公開存取的網路的 IP 位址位置的網站。

此網路深入了解特別是會影響 Exchange Online 服務前哨的選取範圍。 若要解決此深入了解本機和直接的網路輸出應該必要條件，然後 DNS 遞迴解析程式應該位於接近該網路輸出。

## <a name="dns-lookup-of-exchange-online-front-end-server-and-sharepoint-online-front-end-server"></a>Exchange Online 的前端伺服器和 SharePoint Online 的前端伺服器的 DNS 查閱

這些顯示服務的前哨適用於下列兩個 Office 365 工作負載的 DNS 記錄。 他們所提供的資訊只且沒有任何關聯的網路深入解析。

## <a name="proxy-server-identification"></a>Proxy 伺服器識別碼

我們找出在本機電腦上設定的 proxy 伺服器。 我們找出任何這些設定中的網路路徑的最佳化類別 Office 365 的網路流量。 我們找出使用者的辦公室位置的 proxy 伺服器之間的距離。 距離在 ICMP ping 中有不同的測試第一次，如果失敗我們測試與 TCP ping 最後如果失敗我們查閱 IP 位址位置資料庫中的 proxy 伺服器的 IP 位址。 我們顯示網路深入見解如果 proxy 伺服器會進一步超過 500 英哩 （800 公里） 開使用者辦公室位置。

## <a name="media-quality-checks"></a>媒體品質檢查

這項測試安裝及執行 Skype for Business 網路評估工具，並解譯結果。 此工具可以在找到[https://www.microsoft.com/download/details.aspx?id=53885](https://www.microsoft.com/download/details.aspx?id=53885)。

因為由 Microsoft Teams 音訊和視訊通話及會議功能，這些是 UDP 通訊協定測試。 我們測試 UDP 封包遺失、 UDP 網路延遲、 UDP 抖動和 UDP 封包重新排列。 網路深入了解會顯示任何安全性是否放在允許的範圍。

## <a name="tcp-connectivity-tests"></a>TCP 連線測試

我們測試從使用者的辦公室位置的 HTTP 連線至所有必要的 Office 365 網路端點。 這些會在這裡發佈[https://aka.ms/o365ip](https://aka.ms/o365ip)。 網路深入了解會顯示它無法連接至任何所需的網路端點。

連線是被封鎖的 proxy 伺服器、 防火牆或另一個網路安全性裝置企業網路周邊網路上或在使用雲端 proxy 為。

## <a name="ssl-interception-tests"></a>SSL 攔截測試

我們測試每個必要的 Office 365 網路端點中最佳化或允許類別所定義在 SSL 憑證[https://aka.ms/o365ip](https://aka.ms/o365ip)。 如果任何測試找不到 Microsoft SSL 憑證，然後連線加密的網路必須有已遭到攔截介的網路裝置。 網路深入了解會顯示任何攔截加密的網路端點。

SSL 憑證找到，不 Microsoft 所提供，我們示範測試並在使用 SSL 憑證擁有者的 FQDN。 此 SSL 憑證擁有者可能是 proxy 伺服器的廠商，或是可能很企業自我簽署的憑證。

## <a name="network-path-diagnostics"></a>網路路徑診斷

本節說明 Exchange Online 服務前哨、 SharePoint Online 服務的前哨，及 Microsoft Teams 服務前哨 ICMP traceroute 的結果。 它僅提供資訊，且沒有任何關聯的網路深入了解。

## <a name="related-topics"></a>相關主題

[在 Microsoft 365 系統管理中心 （預覽） 的網路效能建議](office-365-network-mac-perf-overview.md)

[Office 365 網路效能觀點 （預覽）](office-365-network-mac-perf-insights.md)

[Office 365 網路評估 （預覽）](office-365-network-mac-perf-score.md)
