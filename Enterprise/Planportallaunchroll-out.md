---
title: 規劃在 SharePoint Online 入口網站啟動推行計劃
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid: SPO160
description: 本文說明如何規劃對入口網站啟動的 SharePoint Online 中，才會成功啟動步驟
ms.openlocfilehash: fca8b4f116510589b83748435f64ccbb3790d7c2
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843764"
---
# <a name="planning-your-portal-launch-roll-out-plan-in-sharepoint-online"></a>規劃在 SharePoint Online 入口網站啟動推行計劃

入口網站是您內部網路上的 SharePoint 網站，擁有大量網站檢視者在該網站上取用內容。 大型組織可能會有多個入口網站；例如公司入口網站和人力資源入口網站。 通常，入口網站建立及撰寫網站和內容的人相對較少。 大部分的訪客來到入口網站只會閱讀並取用內容。

本文說明如何規劃您的部署和 SharePoint online 推行計劃。 它也會提供要遵循的傳統負載測試不允許在 SharePoint Online 上的方式。 SharePoint Online 為雲端服務和 Microsoft 所管理的負載能力、 健康狀況和整體的服務中的負載平衡。

若要協助建立成功的入口網站，請遵循的基本原則、 實務和[建立、 啟動和維護狀況良好的入口網站](https://go.microsoft.com/fwlink/?linkid=2105838)中詳述的建議 

下方已反白的部署方法。

## <a name="overview-of-capacity-planning-in-sharepoint-online"></a>容量規劃在 SharePoint Online 中的概觀
才能有效率地使用容量及處理未預期的成長，任何伺服器陣列中，我們有追蹤特定使用案例的自動化。 雖然確切成長是不可預期的任何一個伺服器陣列中任何一個租用戶，彙總的總和要求，是可預測一段時間。 藉由識別 SharePoint Online 中的成長趨勢，我們可以規劃未來的擴充。 如需有關[容量規劃和負載測試 SharePoint Online](https://docs.microsoft.com/office365/enterprise/capacity-planning-and-load-testing-sharepoint-online)的詳細資訊。

成功啟動的重要部分是 「 波浪 」 或 「 分階段推行 」 方法的詳細資訊如下。 

## <a name="can-i-load-test-sharepoint-online"></a>我可以載入測試 SharePoint Online 嗎？
SharePoint Online 是共用其平衡跨伺服器陣列的多 tenanted 環境和比例調整以持續進行。 負載測試環境，例如 SharePoint Online，其擴充持續變更將不只提供您未預期的結果，但不是允許使用。 

了解更多：[容量規劃和負載測試 SharePoint Online](https://docs.microsoft.com/office365/enterprise/capacity-planning-and-load-testing-sharepoint-online)

## <a name="optimize-pages-by-following-recommended-guidelines"></a>下列建議的指導方針，即可發揮最佳頁面
從內部部署的網頁不應只移動到 SharePoint Online 會不檢閱這些建議的指導方針對 SharePoint Online。 最好的作法是一律最佳化的站台或入口網站在 SharePoint 中，任何首頁因為這是在組織中的大部分使用者會存取的位置為您網站的起始點。

應該考量一些基本因素：
- 內部部署可以利用傳統伺服器端物件快取、 輸出快取和 blob 快取等快取。 與雲端中的拓撲差異，這些選項不一定會提供為真正的小數位數差異使其不可行方法。
- 任何頁面 / 功能 / 用於雲端耗用的自訂項目應針對較高的延遲，以及使用者分配的位置進行最佳化，，讓使用者在不同區域或區域中的有更一致的體驗。 雲端提供最佳化 like 最佳化和新式 SharePoint，最後一個已知良好 (LKG) 以及分散式的使用者群的內容傳遞網路 (CDN) 利用由我們郵件答錄機的方塊 (OOTB) 網頁組件。

### <a name="what-to-do"></a>要執行的動作：
 - 在 SharePoint Online 中的所有網站頁面都使用[] 頁面上診斷工具](https://aka.ms/perftool)，也就是 Chromium 分機號碼可以幫助分析與提供的指導。 這可以使用由網站擁有者、 編輯器、 管理員及開發人員，因為它為了進行分析來最佳化的起始點。
 - 開發人員也應該在新版頁面上使用 F12 瀏覽器開發人員工具，以及 CTRL F12 像在瀏覽器的開發工具。 [Fiddler](https://www.telerik.com/download/fiddler)也可用來檢閱大小權數 （大頁面是以 mb 為單位） 的頁面和通話和影響整體載入頁面的元素數目。 

此區段已最佳化頁面的簡短摘要。  若要了解更多，請參閱：[建立、 啟動和維護狀況良好的入口網站](https://go.microsoft.com/fwlink/?linkid=2105838)。

## <a name="follow-a-wave--phased-roll-out-approach"></a>請遵循波浪 / 分階段推行方法
針對網站啟動的傳統大次方法將不允許驗證該自訂項目、 外部來源、 服務或處理程序測試的右邊的規模。 這並不表示它將會需要幾個月來啟動，但仍建議，至少有幾天取決於您組織的大小。 下列波浪推行計劃因此會讓您選擇以暫停，並解決問題，再繼續進行下一個階段，因此降低潛在的任何問題所影響的使用者人數。 為服務的 SharePoint 比例，調整您根據使用狀況和預測的使用狀況及雖然我們不需要您告知我們您啟動時，您應該遵循的準則，以確保成功的容量。
  
下圖所示，通常是來得高比實際使用網站的受邀的使用者數目。 此圖顯示如何推行發行的策略。 此方法可協助識別改善的 SharePoint 網站，大部分的使用者會看到它之前的方法。
  
![顯示受邀和作用中使用者的圖形](media/0bc14a20-9420-4986-b9b9-fbcd2c6e0fb9.png)
  
在試驗階段中，就是從組織信任，並知道將可讓使用者取得意見反應。 如此一來就能夠控制鈕系統正在使用方式，以及執行的方式。
  
每個階段經，收集使用者意見反應周圍功能，以及在部署的每一波期間的效能。 這有緩慢簡介系統，以及當系統變得更多使用進行改良功能的優點。 這也讓我們來導入越來越多的使用者，加上下列指導方針，如頁面最佳化可確保使用者正體驗網站反應增加的負載。

### <a name="what-to-do"></a>要執行的動作：
- 決定每個階段的時間，並確定您有應變計劃 / 暫停機會，應該要再繼續進行調整
- 規劃您第一組您想要啟用的使用者，您需要以確保您收到的意見反應向前移動。 這表示，有可能，請選取 [作用中的一群使用者提供意見反應及時
- 當您規劃每個波浪時，嘗試開頭少量使用者基底 （小於 5000 使用者），並再增加的群組大小，當您繼續使用每個波浪。 這可協助建立彼此錯開的方法，並允許更容易，可能需要暫停機會。
