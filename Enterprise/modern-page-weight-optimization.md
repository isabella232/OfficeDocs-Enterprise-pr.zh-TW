---
title: 在 SharePoint Online 新式網站頁面中最佳化頁面權數
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/18/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: 深入了解如何在 SharePoint Online 新式網站頁面中最佳化頁面權數。
ms.openlocfilehash: 5e2231468363f58faeac1d7b21e06cd4fa790cf8
ms.sourcegitcommit: c7764503422922cb333b05d54e8ebbdb894df2f9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2019
ms.locfileid: "37028210"
---
# <a name="optimize-page-weight-in-sharepoint-online-modern-site-pages"></a>在 SharePoint Online 新式網站頁面中最佳化頁面權數

SharePoint Online 新式網站頁面包含轉譯頁面的頁面內容所需的序列化代碼，頁面內容包括瀏覽/命令列底下內容區域中的影像、文字、物件，以及形成頁面架構的其他 HTML 程式碼。 頁面權數是這個 HTML 程式碼的度量，應加以限制，以確保最佳的頁面載入時間。

本文可協助您了解如何在新式網站頁面中減少頁面權數。

>[!NOTE]
>如需有關 SharePoint Online 新式入口網站效能的詳細資訊，請參閱 [SharePoint 新式體驗中的效能](https://docs.microsoft.com/zh-TW/sharepoint/modern-experience-performance)。

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-page-weight"></a>使用「適用於 SharePoint 的頁面診斷」工具來分析頁面權數

**適用於 SharePoint 的頁面診斷工具**是 Chrome 和 [Microsoft Edge 77 版或更新版本](https://www.microsoftedgeinsider.com/en-us/download?form=MI13E8&OCID=MI13E8)的瀏覽器擴充功能，您可以用來分析 SharePoint 新式與傳統發佈網站頁面。 該工具會針對每個分析頁面提供一份報告，顯示頁面如何針對定義的效能準則組執行。 若要安裝及了解「適用於 SharePoint 的頁面診斷」工具，請造訪[使用適用於 SharePoint Online 的頁面診斷工具](page-diagnostics-for-spo.md)。

當您使用「適用於 SharePoint 的頁面診斷」工具分析 SharePoint 網站頁面時，您可以在 [診斷測試]__ 窗格的 [頁面權數低於 500KB]**** 結果中看到關於頁面的資訊。 如果頁面權數低於基準值，則結果會顯示為綠色，如果頁面權數超過基準值，則會顯示為紅色。

可能的結果包括：

- **需要注意** (紅色)：頁面權數超過 500KB
- **不需要任何動作** (綠色)：頁面權數低於 500KB

如果 [頁面權數低於 500KB]**** 結果顯示在 [需要注意]**** 區段中，您可以按一下結果以取得詳細資訊。

![對 SharePoint 的要求結果](media/modern-portal-optimization/pagediag-page-weight.png)

## <a name="remediate-page-weight-issues"></a>修復頁面權數問題

如果頁面權數超過 500KB，您可以藉由減少網頁組件的數量，並將頁面內容限制在適當的程度，以改善整體頁面載入時間。

降低頁面權數的一般指導方針包括：

- 將頁面內容限制為合理的數量，並且對相關內容使用多個頁面。
- 將具有大型屬性包的網頁組件使用降至最低。
- 盡可能使用非互動式彙總檢視。
- 您可以使用壓縮的影像格式並確保是從 CDN 下載，以適當地調整影像大小。

您可以在下列文章中找到更多關於限制頁面權數的指導方針：

- [在 SharePoint 中最佳化頁面效能](https://docs.microsoft.com/zh-TW/sharepoint/dev/general-development/optimize-page-performance-in-sharepoint) (英文)

在您進行頁面修訂以修復效能問題之前，請記下分析結果中的頁面載入時間。 在修訂後再次執行工具，以查看新結果是否在基準標準內，並檢查新頁面的載入時間，以查看是否有改善。

![頁面載入時間結果](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
>頁面載入時間會根據各種因素而有所不同，例如網路負載、一天的時間及其他暫時條件。 您應該在進行變更前後測試幾次頁面載入時間，以協助您計算結果的平均值。

## <a name="related-topics"></a>相關主題

[調整 SharePoint Online 效能](tune-sharepoint-online-performance.md)

[調整 Office 365 效能](tune-office-365-performance.md)

[SharePoint 新式體驗中的效能](https://docs.microsoft.com/zh-TW/sharepoint/modern-experience-performance.md)

[內容傳遞網路](content-delivery-networks.md)

[使用 Office 365 內容傳遞網路 (CDN) 搭配 SharePoint Online](use-office-365-cdn-with-spo.md)