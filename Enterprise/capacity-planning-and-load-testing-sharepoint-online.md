---
title: 容量規劃和負載測試 SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 04/10/2019
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c932bd9b-fb9a-47ab-a330-6979d03688c0
description: 本文說明如何部署至 SharePoint Online 不執行傳統負載測試，因為不允許使用。
ms.openlocfilehash: 615ad96f4fcf3ac939785e3aafb32956f5661e36
ms.sourcegitcommit: 5e85536a6f53262136acfaac640f5d109a65f643
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/10/2019
ms.locfileid: "31765055"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a>容量規劃與測試 SharePoint Online 的負載。

本文說明如何部署至 SharePoint Online 沒有傳統負載測試，因為 SharePoint Online 上不允許負載測試。 SharePoint Online 是負載的負載能力、 健康情況及整體的服務中平衡，負載的由 Microsoft 雲端服務。
  
若要確保成功啟動您的網站的最佳方法是遵循基本原則，做法與建議的方式反白顯示下方。
  
與內部部署環境，負載測試用來驗證規模假設和最終尋找伺服器陣列; 分行點藉由飽和它具有負載。 使用 SharePoint Online，我們需要以不同的方式執行動作。 要在多承租人環境，我們必須保護所有租用戶中相同的伺服器陣列，因此我們將會自動節流的任何負載測試。 這表示您會收到令人失望，且可能造成誤解結果，如果您嘗試載入測試您的環境。
  
透過內部部署的 SharePoint Online 的主要優點是雲端的彈性。 我們的大型環境設為服務的每日使用者百萬所以很重要，我們處理容量有效率地平衡，並展開 [伺服器陣列。 文章也會涵蓋供您使用不涉及負載測試，但包含下列設定您以為成功啟動準則的方式。 
  
雖然成長是不可預期的任何一個伺服器陣列中任何一個租用戶，彙總的總和要求，是可預測一段時間。 藉由識別 SharePoint Online 中的成長趨勢，我們可以規劃未來的擴充。
  
我們在才能有效率地使用容量及處理未預期的成長，任何伺服器陣列中有自動化來追蹤前端負載及擴充，在需要時。 有多個計量使用具有下列其中一個主要該組正在訊號為用於先行擴充伺服器的 CPU 負載。 此外於此並為您會注意到進一步在文章中，我們建議分階段 / SQL 環境將會縮放根據負載及需求，以及下列階段與經允許正確散發負載及成長的波浪方法。 
  
## <a name="how-do-i-plan-for-a-site-launch"></a>如何規劃網站啟動？

### <a name="optimize-pages-by-following-recommended-guidelines"></a>下列建議的指導方針，即可發揮最佳頁面
從內部部署的網頁應不只是予以以拖曳到 SharePoint Online 不檢閱這些建議的指導方針對 SharePoint Online。

應該考慮幾個重要因素：
- 內部部署可以利用像是物件快取的傳統伺服器端快取，但與雲端中的拓撲差異，這些選項不提供。
- 任何頁面 / 功能 / 用於雲端耗用的自訂項目應針對多個位置進行最佳化，讓使用者在不同區域或區域中的有一致的體驗。 雲端提供最佳化類似內容傳遞網路 (CDN) 最佳化分散式的使用者結構。

在 SharePoint Online 中您可以使用分析主[頁面診斷工具](https://aka.ms/perftool)Chrome 延伸模組可以幫助的傳統發佈頁面的登陸頁面的使用者使用。
在瀏覽器或[Fiddler](https://www.telerik.com/download/fiddler)的 F12 開發人員工具可以用來檢閱] 頁面上的權數，呼叫和影響整體載入頁面的元素的數目應該檢閱，而且最佳化。 包括使用內容傳遞網路和其他最佳化的建議清單可以檢閱[調整 SharePoint Online 效能](https://aka.ms/tuneSPO)文件中。

### <a name="wave--phase-approach"></a>波浪 / 階段方法
針對網站啟動的傳統大次方法不有效率地讓驗證該自訂項目，外部來源、 服務或處理程序測試的右邊的規模。 SharePoint 以服務也調整您根據使用狀況和預測的使用狀況及雖然我們不需要您通知的網站啟動中，您應該遵循以下以確保成功的指導方針的容量。
  
下圖所示，通常是來得高比實際使用網站的受邀的使用者數目。 此圖顯示如何推行發行的策略。 此方法可協助識別改善的 SharePoint 網站，大部分的使用者會看到它之前的方法。 它也可讓暫停導入應該發生問題中任何階段/經進而限制潛在的使用者人數影響。
  
![顯示受邀和作用中使用者的圖形](media/0bc14a20-9420-4986-b9b9-fbcd2c6e0fb9.png)
  
在試驗階段中，就是從組織信任，並知道將可讓使用者取得意見反應。 如此一來就能夠控制鈕系統正在使用方式，以及執行的方式。
  
每個階段經，收集使用者意見反應周圍功能，以及在部署的每一波期間的效能。 這有緩慢簡介系統，以及當系統變得更多使用進行改良功能的優點。 這也讓我們可以為網站已導入多使用者負載增加作出反應。
