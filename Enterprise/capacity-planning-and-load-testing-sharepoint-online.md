---
title: 容量規劃和負載測試 SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 04/10/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c932bd9b-fb9a-47ab-a330-6979d03688c0
description: 本文說明如何部署至 SharePoint Online 不執行傳統負載測試，因為不允許使用。
ms.openlocfilehash: d62b15be38b3f62c64c2943313b94aa99cbd14ab
ms.sourcegitcommit: 739024fe2862ab646b36e218b57c5cc16ebe7892
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2019
ms.locfileid: "37422140"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a>容量規劃和負載測試 SharePoint Online
本文說明如何部署至 SharePoint Online 沒有傳統負載測試，因為 SharePoint Online 上不允許負載測試。 SharePoint Online 的雲端服務和負載功能，狀況且整體的服務中的負載平衡由 Microsoft 所管理。
  
若要確保成功啟動您的網站的最佳方法是遵循基本原則、 實務和建議的方式反白顯示在[規劃您入口網站啟動推行](https://docs.microsoft.com/office365/enterprise/planportallaunchroll-out)。

## <a name="overview-of-how-sharepoint-online-performs-capacity-planning"></a>如何 SharePoint Online 執行容量規劃的概觀 
透過內部部署的 SharePoint Online 的主要優點是雲端以及最佳化分散式區域中的使用者的彈性。 我們的大型環境設為服務百萬的使用者每日，所以很重要，我們處理容量有效率地平衡，並展開 [伺服器陣列。
  
雖然成長通常是不可預期的任何一個伺服器陣列中任何一個租用戶，要求的彙的總和經過一段時間是可預測。 藉由識別 SharePoint Online 中的成長趨勢，我們可以規劃未來的擴充。
  
才能有效率地使用容量及處理未預期的成長，任何伺服器陣列中，我們有自動化來追蹤及監視服務的各種元素。 利用多個評量，以其中一個主要和正在 CPU 負載，這做為擴充最上層的訊號端伺服器。 此外此建議[分階段 / 揮動方法](https://docs.microsoft.com/office365/enterprise/planportallaunchroll-out)，根據負載及成長經過一段時間，將會縮放 SQL 環境及下列階段與經允許該負載和成長的正確的通訊群組時。 

容量為多個幾乎新增更多的硬體連續為基礎，但它也適用於管理和控制的容量，以確定它會要求提供服務有效的負載。 我們建議客戶遵循建議的指導方針，以確保它們有最佳的體驗。 這也表示我們有節流模式和控制項，以確保我們的服務中不允許 「 粗俗 」 的行為。 而不是所有 「 錯誤 」 的行為是故意的我們沒有以確保我們限制該行為的效果。 如需節流及如何避免在它的進一步資訊，檢閱[如何避免在被節流指南](https://docs.microsoft.com/sharepoint/dev/general-development/how-to-avoid-getting-throttled-or-blocked-in-sharepoint-online)> 一文。

## <a name="why-you-cannot-load-test-sharepoint-online"></a>為什麼無法載入測試 SharePoint Online
與內部部署環境，負載測試用來驗證規模假設和最終尋找伺服器陣列; 分行點藉由飽和它具有負載。 

使用 SharePoint Online，我們需要以不同的方式執行動作，因為縮放比例是相當流暢和調整、 節流處理及控制負載，根據特定啟發學習法。 正在這類大型多承租人環境，我們必須保護所有租用戶中相同的伺服器陣列，因此我們將會自動節流的任何負載測試。 如果您不過嘗試負載測試，除了被節流，您會收到令人失望和因為您今天測試伺服器陣列將可能有鎖縮放變更在測試期間或之後進行測試，小時內可能誤導結果為刻度和平衡動作的伺服器陣列上持續執行。

而不是嘗試載入測試 SharePoint 作為服務，而是著重於下列建議的作法，然後遵循[建立、 啟動和維護狀況良好的入口網站](https://go.microsoft.com/fwlink/?linkid=2105838)指引。
