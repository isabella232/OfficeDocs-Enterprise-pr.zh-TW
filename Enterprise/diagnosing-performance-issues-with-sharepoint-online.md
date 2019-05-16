---
title: 診斷 SharePoint Online 的效能問題
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 2/23/2018
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 3c364f9e-b9f6-4da4-a792-c8e8c8cd2e86
description: 本文將告訴您如何診斷常見的問題，以及在 SharePoint Online 網站使用 Internet Explorer 開發人員工具。
ms.openlocfilehash: dfc66822a98ce26bfd9fd94d9d58882b8b140831
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067859"
---
# <a name="diagnosing-performance-issues-with-sharepoint-online"></a>診斷 SharePoint Online 的效能問題

本文將告訴您如何診斷常見的問題，以及在 SharePoint Online 網站使用 Internet Explorer 開發人員工具。
  
有三個不同的方式，您可以識別 SharePoint Online 網站上的頁面，具有自訂效能問題。
  
- F12 工具列網路監視器
    
- 非自訂基準比較
    
- SharePoint Online 回應標頭度量
    
本主題說明如何使用這些方法來診斷效能問題。 一旦您已猜問題的原因，您就能使用文章提升 SharePoint 效能，您可以在找到解決方案聚集http://aka.ms/tune。
  
## <a name="using-the-f12-tool-bar-to-diagnose-performance-in-sharepoint-online"></a>使用 F12 工具列來診斷 SharePoint Online 中的效能
<a name="F12ToolInfo"> </a>

在本文中，我們使用 Internet Explorer 11。 版本的 F12 開發人員工具，在其他瀏覽器上具有類似的功能，但是它們看起來可能稍有不同。 F12 開發人員工具的詳細資訊，請參閱：
  
- [What's new in F12 工具](https://go.microsoft.com/fwlink/p/?LinkId=522545)
    
- [使用 F12 開發人員工具](https://go.microsoft.com/fwlink/p/?LinkId=522546)
    
若要顯示開發人員工具按**F12** ，，然後按一下 Wi-fi 圖示： 
  
![F12 開發人員工具 WIFI 圖示的螢幕擷取畫面](media/27acacbb-5688-459a-aa2f-5c8c5f17b76e.png)
  
在 [**網路**] 索引標籤上按下綠色播放按鈕載入頁面。 此工具會傳回所有瀏覽器要求以取得您要求] 頁面上的檔案。 下列螢幕擷取畫面顯示一個這類清單。 
  
![使用頁面要求所傳回之檔案清單的螢幕擷取畫面。](media/247a9422-76da-4b0c-bed3-ce77b05e4560.png)
  
這個螢幕擷取畫面所示，您也可以查看在右側的檔案下載時間。
  
![圖表顯示從 SharePoint 載入要求頁面所需的時間](media/d71ad1fa-9018-4fae-82eb-c1838e7db0ff.png)
  
這可以讓您多久檔案所需載入的視覺表示法。 綠色行代表可由瀏覽器轉譯頁面時。 這可讓您快速檢視的可能原因包括速度很慢的頁面載入網站的不同檔案。
  
## <a name="setting-up-a-non-customized-baseline-for-sharepoint-online"></a>設定 SharePoint Online 的非自訂基準
<a name="F12ToolInfo"> </a>

若要判斷您的網站效能弱式點的最佳方式是設定在 SharePoint Online 中完全--現成的網站集合。 如此一來，您可以比較與將得到的結果頁面上沒有自訂網站的所有的各個方面。 OneDrive for Business 首頁頁面是很好的範例不太可能會有任何自訂個別網站集合。
  
## <a name="viewing-sharepoint-response-header-information"></a>檢視 SharePoint 回應標頭資訊
<a name="F12ToolInfo"> </a>

在 SharePoint Online 和 SharePoint Server 2013 中，您可以存取傳送回的瀏覽器中的每個檔案的回應標頭的資訊。 SPRequestDuration 和 X SharePointHealthScore 診斷效能問題的兩個最有用值︰
  
- **SPRequestDuration**
    
    這是時間的要求在伺服器進行處理量。 這可協助判斷要求是否非常大量和大量的資源。 這是最佳的深入解析到多少工作有 server 服務] 頁面上所做的動作。
    
- **X-SharePointHealthScore**
    
    這表示伺服器或您的 SharePoint 執行個體執行所在的 CPU 的使用率。 此數字的範圍從 0 到 10，其中 0 表示伺服器處於閒置狀態而 10 表示伺服器是非常忙碌。 持續 9 或 10 HealthScore 可能會指出與伺服器進行中的效能問題。 其他任何數字表示該伺服器作業系統預期的範圍內。
    
 **若要檢視 SharePoint 回應標頭資訊**
  
1. 請確定您已安裝 F12 工具。 如需有關下載並安裝這些工具的詳細資訊，請參閱 < <b0>What's new in F12 工具</b0>。
    
2. 在 F12 工具，在 [**網路**] 索引標籤上按綠色播放按鈕載入頁面。 
    
3. 按一下下列其中一個工具所傳回的.aspx 檔案，然後按一下 [**詳細資料**。 
    
    ![顯示回應標頭的詳細資料](media/1f8a044a-caf8-4613-be2b-7e064141ac8a.png)
  
4. 按一下 [**回應標頭**]。 
    
    ![圖表顯示回應標頭的 URL](media/efc7076e-447e-447e-882a-ae3aa721e2c3.png)
  
## <a name="whats-causing-performance-issues-in-sharepoint-online"></a>什麼 SharePoint Online 中導致效能問題？
<a name="F12ToolInfo"> </a>

[SharePoint Online 的導覽選項](navigation-options-for-sharepoint-online.md)的文章顯示至判斷複雜的結構式導覽所造成要花很長的時間處理程序在伺服器上的頁面使用 SPRequestDuration 值的範例。 = 389917 的值 （不含自訂） 的基準網站，很可能至判斷指定的任何檔案是否正在載入很長的時間。 [SharePoint Online 的導覽選項](navigation-options-for-sharepoint-online.md)中所使用的範例是主要的.aspx 檔案。 該檔案包含大部分的 ASP.NET 程式碼執行您] 頁面上的負載。 根據您使用的網站範本，這可能是 start.aspx、 home.aspx、 default.aspx 或另一個名稱如果您自訂 [首頁] 頁面。 如果此數字是相當高於基準網站，它是很好的指標，還有一些複雜您會造成效能問題的頁面中。 
  
一旦您已識別您網站特有的問題，以找出項目會導致效能不佳的建議的方式是消除所有可能的原因，像是頁面自訂項目，，然後將其新增回網站逐一。 一旦您已移除足夠良好執行 [] 頁面上的自訂，接著您可以新增回特定自訂項目的一個接著一個。
  
例如，如果您有非常複雜的導覽會嘗試變更瀏覽至未顯示子網站，然後檢查以查看是否會有不同的開發人員工具。 如果您有大量的內容彙總套件或嘗試移除程式] 頁面上，並查看如果這樣可以改善項目。 如果您關閉所有可能的原因，並將其新增中一次，您可以輕易地識別哪些功能的最大問題以及然後使用向解決方案。
  

