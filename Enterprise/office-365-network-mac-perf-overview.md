---
title: Microsoft 365 系統管理中心的網路效能建議（預覽）
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/20/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Microsoft 365 系統管理中心的網路效能建議概述（預覽）
ms.openlocfilehash: 16ef23810645bcd9719107b13d32909af25d4766
ms.sourcegitcommit: 1c3aa0654336acec14098241f785ea1d8c6caf50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "42890423"
---
# <a name="network-performance-recommendations-in-the-microsoft-365-admin-center-preview"></a>Microsoft 365 系統管理中心的網路效能建議（預覽）

Microsoft 365 系統管理中心現在包括從您的 Office 365 租使用者收集到的即時效能度量，而且只能在您的承租人中供系統管理使用者查看。 **網路洞察力和效能建議**和**網路評估**會顯示在 Microsoft 365 系統管理中心中<https://portal.microsoft.com/adminportal/home#/networkperformance>。 您可以在功能窗格中的 [狀況 |] 底下找到頁面。 **網路效能**。

![網路效能頁面](Media/m365-mac-perf/m365-mac-perf-page-nav.png)

當您第一次流覽至 [網路性能] 頁面時，您會看到 [一覽表] 窗格，其中包含全域網路效能對應、整個承租人範圍的網路評估，以及目前問題的清單。 您可以從 [概述] 中深入查看特定的網路效能度量和依位置的問題。 如需詳細資訊，請參閱[Microsoft 365 系統管理中心的網路效能概述](#network-performance-overview-in-the-microsoft-365-admin-center)。

## <a name="pre-requisites-for-connectivity-measurements-to-appear"></a>要顯示的連線性度量先決條件

若要顯示連線能力，您必須至少有兩部電腦在支援先決條件的辦公室位置執行。 您必須在每一部電腦上安裝 Business Sync 用戶端版本19.232 或更新版本的 OneDrive。 如需詳細資訊，請參閱[OneDrive 發行附注](https://support.office.com/article/onedrive-release-notes-845dcf18-f921-435e-bf28-4e24b95e5fc0)。

Windows 位置服務必須同意電腦。 您可以執行「**地圖**」應用程式並自行尋找，以測試這種情況。 您可以**在具有** -> 設定**隱私權** -> **位置**的單一電腦上啟用此設定，必須啟用設定「允許應用程式存取您的位置」。 您可以使用 MDM 或群組原則，將 Windows Location 服務同意部署至使用設定_LetAppsAccessLocation_的電腦。

電腦應該有 Wi-Fi 網路，而不是乙太網線。 使用乙太網線的電腦沒有正確的位置資訊。

在符合這些先決條件後，應會在24小時內開始顯示度量範例和辦公室位置。

## <a name="how-do-i-use-this-information"></a>如何使用此資訊？

**網路洞察力**，其相關的效能建議和網路評估是為了協助您為辦公室位置設計網路周邊。 每個真知灼見都會針對使用者存取租使用者時，針對每個地理位置的特定一般問題，提供有關效能特性的實際詳細資料。 每個網路洞察力的**效能建議**提供特定的網路架構設計變更，以改進與 Office 365 網路連接相關的使用者體驗。 網路評估顯示網路連線影響使用者經驗的方式，允許比較不同的使用者位置網路連接。

**網路評估**會將許多網路效能度量的集合提煉成商業網路健康情況的快照，以點數從 1-100。 網路評估同時適用于整個承租人和每個地理位置，使用者會從該位置連線到您的租使用者，並提供 Office 365 系統管理員輕鬆地抓住商業網路健康情況的 gestalt，並快速進行鑽取的方式向內移動至任何全球辦公室位置的詳細報告。

具有多個辦公室位置和非普通網路周邊架構的複雜企業，可在初始上架至 Office 365 時受益，或修復使用狀況成長所發現的網路效能問題。 使用 Office 365 的小型企業或任何已具備簡易及直接網路連線的企業，通常不需要這麼做。 使用超過500個使用者和多個辦公室位置的企業，可獲得最大效益。

>[!IMPORTANT]
>Microsoft 365 系統管理中心的網路洞察力、效能建議和評估目前處於預覽狀態，只適用于已在功能預覽計畫中註冊的 Office 365 承租人。

## <a name="enterprise-network-connectivity-challenges"></a>商業網路連線挑戰

![客戶網路到雲端](Media/m365-mac-perf/m365-mac-perf-first-last-mile.png)

許多企業的網路周邊設定已經成長，主要是用來容納員工網際網路網站存取，而大多數網站卻不會事先知道，而且不受信任。 「主要」和「必要」的重點是避免來自這些未知網站的惡意程式碼和釣魚攻擊。 這個網路設定策略在安全性方面非常有用，可導致 Office 365 使用者效能和使用者體驗的降級。

## <a name="how-we-can-solve-these-challenges"></a>我們可如何解決這些難題

企業可以遵循[Office 365 連線原則](https://aka.ms/pnc)及使用 Microsoft 365 系統管理中心網路效能功能，來改善一般使用者經驗並保護其環境。 在大多數情況下，遵循這些一般原則會對使用者的延遲、服務可靠性和 Office 365 的整體效能產生重大的積極影響。

Microsoft 有時候會要求您調查適用于大型企業客戶的 Office 365 網路效能問題，這些問題通常會與客戶網路出口基礎結構相關的根本原因。 當找到客戶網路周邊問題的常見根本原因時，我們會搜尋識別它所識別的簡單測試度量。 使用識別特定問題的測量臨界值進行測試是非常有價值的，因為我們可以在任何位置測試相同的度量，判斷是否存在此根本原因，並加以共用，以與系統管理員的網路洞察力共用。

有些網路洞察力只會指出需要進一步調查的問題。 網路洞察力：我們有足夠的測試顯示特定的修正動作，以修正根本原因，會列為建議的**動作**。 這些建議是根據即時度量，顯示在預先確定的臨界值以外的值，比一般的最佳作法建議更為重要，因為它們是特定于您的環境，而且會顯示一次實際的改進一次。已進行建議的變更。

## <a name="network-performance-overview-in-the-microsoft-365-admin-center"></a>Microsoft 365 系統管理中心的網路效能一覽表

Microsoft 從數個 Office 桌面和網頁用戶端中的網路度量，可支援 Office 365 的運作。 這些測量現在是用來提供網路架構設計真知灼見和網路效能評估，其顯示在 Microsoft 365 系統管理中心的 [**網路效能**] 頁面中。

根據預設，與網路度量相關聯的大致位置資訊，識別用戶端裝置所在的城市。 每個位置的網路評估會顯示色彩，每個位置的使用者相對數量是以圓形大小來表示。

![網路洞察力綜述對應](Media/m365-mac-perf/m365-mac-perf-overview-map.png)

[一覽表] 頁面也會顯示客戶的網路評估，在所有辦公室位置都是加權平均。

![網路評估](Media/m365-mac-perf/m365-mac-perf-overview-score.png)

## <a name="specific-office-location-network-performance-summary-and-insights"></a>特定的辦公室位置網路效能摘要和洞察力

選取「辦公室位置」會開啟位置特定摘要頁面，顯示已從該辦公室位置度量單位識別的網路出局詳細資料。

![依位置的網路洞察力詳細資料](Media/m365-mac-perf/m365-mac-perf-locations-plan-overview.png)

「Office 位置摘要」頁面也會顯示位置的網路評估、網路評估記錄、此位置的評估與相同城市中的其他客戶的比較，以及您可以使用的特定洞察力和建議清單。採取提升網路效能與可靠性的考慮。 具有特定建議的位置也會包含估計的潛在延遲改進。

在相同城市中的客戶之間的比較，取決於所有客戶都對網路服務提供者、電信基礎結構和目前的 Microsoft 網路點狀態具有相同存取權的預期。

![網路洞察力位置](Media/m365-mac-perf/m365-mac-perf-locations.png)

[Office 位置] 頁面上的 [詳細資料] 索引標籤會顯示用來提出任何真知灼見、建議及網路評估的特定測量結果。 這樣做是為了讓網路工程師能夠驗證其環境中任何限制或細節的建議和因素。

![位置特定詳細資料](Media/m365-mac-perf/m365-mac-perf-locations-plan-details-all.png)

針對想要提高位置特定計量和建議之準確性的客戶，我們允許輸入更特定的資訊。 這可以降低可用於網路測量之位置資訊中的近似值。 若要編輯特定辦公室位置的位址，請<functionality not there yet>使用。

## <a name="import-undiscovered-office-locations"></a>未發現的 office 位置匯入

[網路性能**位置**] 索引標籤會顯示從網路遙測自動探索的 office 位置清單。 這些辦公室位置已探索城市。 您可以在這些城市內手動新增更多特定位置，如果他們不會自動從 CSV 檔案匯入清單中。 如果辦公室位置並未顯示，您應該疑難排解為何未出現網路度量，而不只是在這裡加入地點。 您也可以更新現有辦公室位置的位址值。

在 CSV 檔案中，已發現的城市位置標示為「**城市**」，而手動新增的 office 位置標示為**location**。

1. 在 [主要_連接至 Microsoft 365_ ] 視窗中，按一下 [**位置**] 索引標籤。
1. 按一下 [位置] 清單上方的 [匯**入**] 按鈕。 隨即會顯示 [匯**入 office 位置**] 快顯視窗。

   ![CSV 匯入錯誤訊息](Media/m365-mac-perf/m365-mac-perf-import.png)

1. 按一下 [**下載目前的 office 位置（.csv）** ] 連結，將目前的位置清單匯出至 csv 檔案，並將其儲存到本機硬碟。 這將為您提供正確格式化的 CSV，您可以在其中新增位置。 您可以保留匯出的位置。當您匯入更新的 CSV 時，將不會重複。 如果您想要變更現有位置的位址，當您匯入 CSV 時，它就會更新。 您無法變更所探索之城市的位址。
1. 開啟 CSV 並新增您的位置，方法是針對您想要新增的每個位置，在新行上填上下欄欄位。 保留所有其他欄位為空白;您在其他欄位中輸入的值將會被忽略。
   1. **位址**（必要）： office 的實體位址
   1. **Latitude** （選用）：若為空白，則填入 Bing 地圖 lookup （選用）
   1. **經度**（選用）：若為空白，則填入 Bing 地圖 lookup （選用）
   1. **出局 IP 位址範圍 1-5** （選用）：針對每個範圍，請輸入電路名稱，後面加上以空格分隔的有效 IPv4 或 IPv6 CIDR 地址清單。 僅當您已針對指定的辦公室位置啟用 SDWAN 整合時，才會使用這些值。
1. 當您已新增辦公室位置並儲存檔案後，請按一下 [**上傳完成**] 欄位旁邊的 [**流覽]** 按鈕，然後選取儲存的 CSV 檔案。
1. 檔案將會自動驗證。 如果有驗證錯誤，您會看到錯誤訊息在匯_入檔案中有一些錯誤。請複查錯誤，修正匯入檔，然後再試一次。_ 按一下 [連結] 中的 [**開啟錯誤詳細資料**]，以取得特定欄位驗證錯誤的清單。

   ![CSV 匯入錯誤訊息](Media/m365-mac-perf/m365-mac-perf-import-error.png)

1. 如果檔案中沒有錯誤，您將會看到 _[報告已就緒] 的訊息。找到要新增的 x 位置和要更新的 x 位置。_ 按一下 [匯**入**] 按鈕上傳 CSV。

   ![CSV 匯入準備郵件](Media/m365-mac-perf/m365-mac-perf-import-ready.png)

## <a name="faq"></a>常見問題集

### <a name="what-is-an-office-365-service-front-door"></a>何謂 Office 365 服務的前門？

Office 365 服務的前門是 Microsoft 全球網路上的進入點，Office 用戶端和服務會中斷其網路連線。 若要取得 Office 365 的最佳網路連線，建議您的網路連線中斷為您的城市或地鐵的最接近的 Office 365 前門。

>[!NOTE]
>Office 365 服務前端沒有 azure marketplace 中可用的 Azure 前門服務產品的直接關聯。

### <a name="what-is-an-optimal-office-365-service-front-door"></a>何謂最佳的 Office 365 服務前門？

最佳的 Office 365 服務前端是最接近您的網路出局，通常是在您的城市或大都市區域中。 使用[office 365 網路上架工具](office-365-network-mac-perf-onboarding-tool.md)來判斷您使用中的 office 365 服務前門和最優服務前門的位置。 如果工具判斷您的使用中的前門是最優的，您就會以最優化方式連線至 Microsoft 的全球網路。

### <a name="what-is-an-internet-egress-location"></a>何謂網際網路出口的位置？

網際網路出局位置是網路流量結束商業網路並連接到網際網路的位置。 這也會識別為您具有網路位址轉譯（NAT）裝置的位置，通常是您使用網際網路服務提供者（ISP）進行連線的位置。 如果您看到位置和網際網路出局位置之間有長距離的距離，則這可能表示有重要的 WAN backhaul。

## <a name="related-topics"></a>相關主題

[Office 365 網路洞察力（預覽）](office-365-network-mac-perf-insights.md)

[Office 365 網路評估（預覽）](office-365-network-mac-perf-score.md)

[M365 系統管理中心的 Office 365 網路上架工具（預覽）](office-365-network-mac-perf-onboarding-tool.md)

[Office 365 網路洞察力隱私權和使用條款（預覽）](office-365-network-mac-perf-privacy.md)
