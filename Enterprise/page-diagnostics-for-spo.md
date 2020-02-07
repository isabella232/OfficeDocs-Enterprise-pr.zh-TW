---
title: 使用 Sharepoint Online 網頁診斷工具
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/19/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
search.appverid:
- MET150
- SPO160
- MOE150
- BSA160
f1.keywords:
- NOCSH
description: 使用頁面診斷 SharePoint 工具來分析 SharePoint Online 的新式入口網站及傳統的發佈頁面，對一組預先定義的效能的準則。
ms.openlocfilehash: 57f8aa86b049701c152e8110f64b418d64250981
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841780"
---
# <a name="use-the-page-diagnostics-for-sharepoint-tool"></a>使用頁面診斷 SharePoint 工具

本文說明如何使用 **] 頁面上診斷 SharePoint 工具**來分析 SharePoint Online 的新式和傳統網站頁面，對一組預先定義的效能的準則。  

>[!TIP]
>**已發行版本 2.0.1 的工具**。 版本**2.0.0**和更新版本包含支援傳統網站頁面除了新式頁面。 如果您不確定您使用哪個版本的工具，您可以選取 [**關於**] 連結或若要確認您的版本的省略符號 （...）。

SharePoint 工具] 頁面上診斷是 Chrome 和[Microsoft Edge 版本 77 和更新版本](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8)，用來分析 SharePoint Online 的新式入口網站及發佈網站頁面的傳統瀏覽器延伸模組。 這項工具僅適用於 SharePoint Online 中，並使用 SharePoint Server 網站頁面上，將會失敗並產生錯誤。

此工具會產生報表的每個分析頁面顯示] 頁面上的執行對一組預先定義的規則和測試的結果落之外的基準值時，會顯示的詳細的資訊。 SharePoint Online 系統管理員和設計者可以使用工具來疑難排解效能問題，並確定新頁面已發佈前進行最佳化。

頁面診斷工具被設計來分析只有 SharePoint 網站頁面，例如*allitems.aspx*或*sharepoint.aspx*不系統頁面。 如果您嘗試執行工具系統] 頁面上或任何其他非網站頁面上，您會收到錯誤訊息，告知該類型] 頁面上，無法在執行此工具。

![必須在 SharePoint 頁面上執行](media/page-diagnostics-for-spo/pagediag-Error-StartPage.png)

在評估文件庫或系統頁面沒有任何值時，這是不工具中的錯誤。 請瀏覽至 SharePoint 網站頁面，以便使用此工具。 如果 SharePoint 頁面上，就會發生此錯誤，請檢查確定尚未移除中繼標籤 SharePoint 的主版頁面。

若要提供意見反應工具，選取 [在工具的右上角的省略符號，然後選取 [[提供意見反應](https://go.microsoft.com/fwlink/?linkid=874109)。

![提供意見](media/page-diagnostics-for-spo/pagediag-feedback.png)
  
## <a name="install-the-page-diagnostics-for-sharepoint-tool"></a>安裝 SharePoint 工具] 頁面上診斷

本節中的安裝程序適用於 Chrome 和 Microsoft Edge 瀏覽器。

> [!IMPORTANT]
> Microsoft 卻無法讀取由 SharePoint 工具] 頁面上診斷分析的資料或頁面內容，我們無法擷取任何個人資訊、 網站或下載的資訊。 僅工具所記錄的資訊是租用戶的名稱，規則計數，以及是否支援記錄選項已啟用時執行此工具。 這項資訊使用 Microsoft 來了解新式的入口網站及發佈網站使用狀況趨勢以及告知產品的改良效能常見問題。

1. 使用_Chrome_或_77 或更新版本的 Microsoft Edge 版本_瀏覽器，請直接開啟[連結至工具](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi)或[Chrome 瀏覽器網站儲存](https://chrome.google.com/webstore/search/page%20diagnostics%20for%20sharepoint)中開啟搜尋並安裝瀏覽器延伸模組。 請檢閱中提供的存放區中的 [描述] 頁面上的使用者隱私權原則。 當將工具新增至您的瀏覽器中，您會看到下列權限會注意到。

    ![延伸權限](media/page-diagnostics-for-spo/pagediag-add-to-edge.png)

    通知是就地，因為頁面可能包含位於 SharePoint 之外根據的網頁組件和自訂項目] 頁面上的位置的內容。 這表示，則工具會讀取要求和回應按下 [開始] 按鈕時，僅適用於使用中的 [SharePoint] 索引標籤上執行此工具。 這項資訊會在本機上擷取由網頁瀏覽器，並可供您透過工具的_網路追蹤_] 索引標籤中的 [**匯出至 JSON** ] 或 [**匯出至哈**] 按鈕**未傳送至或由 Microsoft 擷取資訊。** （此工具會遵守 Microsoft 隱私權原則可存取[此處](https://go.microsoft.com/fwlink/p/?linkid=857875)。）

    _管理您的下載項目_權限涵蓋使用工具的**JSON 的匯出**功能。 請為結果包含 Url 以及共用您的組織外部的 JSON 檔案可歸類為 PII （個人識別資訊） 之前，遵循貴公司專屬的隱私權指導方針。
1. 如果您想要使用的工具 Incognito 或 InPrivate 模式，請遵循您的瀏覽器的程序：
    1. Microsoft Edge 中瀏覽至**擴充**或在 [URL] 列中輸入_edge://extensions_然後選取 [**詳細資料**的副檔名。 在分機號碼設定] 中，選取**允許 InPrivate 中**的核取方塊。
    1. 在 Chrome 中，瀏覽至**擴充**或在 [URL] 列中輸入_chrome://extensions_然後選取 [**詳細資料**的副檔名。 在分機號碼設定] 中，選取滑桿，以**允許 Incognito 中**。
1. 瀏覽至 SharePoint Online 上，您想要檢閱之 SharePoint 網站頁面。 我們已允許 「 延遲載入 「 頁面; 上的項目因此，此工具不會停止自動 （這是經過設計，以容納所有頁面負載案例）。 若要停止集合，請選取 [**停止**]。 請確定頁面載入完畢之前停止資料集合，或您只會擷取部分追蹤。
1. 按一下 [擴充功能的工具列按鈕上 ![頁面診斷 for SharePoint 標誌](media/page-diagnostics-for-spo/pagediag-icon32.png) 若要載入的工具，以及您將會出現下列副檔名快顯視窗：

    ![頁面診斷工具快顯功能表](media/page-diagnostics-for-spo/pagediag-Landing.png)

選取 [**啟動**] 以開始收集資料以供分析。

## <a name="what-youll-see-in-the-page-diagnostics-for-sharepoint-tool"></a>您會看到 SharePoint 工具] 頁面上診斷中

1. **相關**連結，這類似於右上角會提供一般指引，包括連結工具的詳細資料重新對本文的省略符號 （...）。 它還包含 SharePoint 效能建議、 協力廠商通知並提供意見反應工具的相關選項的直接連結。  
1. **相互關聯識別碼、 SPRequestDuration、 SPIISLatency**、**頁面載入時間**，以及**URL**詳細資料會提供資訊，並可用於幾個用途。

    ![頁面診斷詳細資料](media/page-diagnostics-for-spo/pagediag-details.PNG)

   - 使用 Microsoft 支援服務，因為它可讓它們以收集特定] 頁面上的其他診斷資料時， **CorrelationID**是一個重要項目。
   - **SPRequestDuration**是 for SharePoint，以處理] 頁面上所花費的時間。 結構式導覽，大型的影像，大量的 API 呼叫無法所有參與較長的工期。
   - **SPIISLatency**是以毫秒為單位所採取的載入網頁的 SharePoint Online 開始的時間。 此值不包含 web 應用程式，以回應所花費的時間。
   - **頁面載入時間**為所要求的時間從頁面已接收到回應，並將其在瀏覽器中呈現的時間以記錄的總時間。 此值會受到各種因素包括網路延遲、 電腦和瀏覽器中載入網頁所花費的時間的效能。
   - **網頁 URL** （統一資源定位器） 是目前頁面的網頁地址。

1. [**診斷測試**](#how-to-use-the-diagnostic-tests-tab)] 索引標籤中三種類別; 顯示分析結果**不需要執行動作****改進機會**，**需注意**。 下表所述，是以其中一個類別中的項目來表示每個測試結果：

    |類別  |色彩  |描述  |
    |---------|---------|---------|
    |**所需的注意事項** |紅色 |測試結果之外的基準值，並會影響網頁效能。 請遵循修復指引。|
    |**改進機會** |黃色 |測試結果之外的基準值，並可能導致效能問題。 適用於測試的特定準則。|
    |**不需要採取任何動作** |綠色 |測試結果落在測試的比較基準值內。|

    ![頁面診斷](media/page-diagnostics-for-spo/pagediag-results-general.PNG)

1. [**網路追蹤**](#how-to-use-the-network-trace-tab)] 索引標籤提供詳細資料] 頁面上的建立要求和回應。

## <a name="how-to-use-the-diagnostic-tests-tab"></a>如何使用 [診斷測試] 索引標籤

當您分析 SharePoint 新式入口網站頁面或傳統發佈網站] 頁面上，使用 SharePoint 工具] 頁面上診斷，結果會經過分析使用預先定義的規則，比較針對基準值的結果，並針對特定的**診斷測試**] 索引標籤規則中顯示測試可能，請使用不同的基準值的新式的入口網站及傳統的發佈網站，根據特定的效能特性兩者之間的不同方式。

出現在**改進機會**或**需注意**的類別中的測試結果指出應該檢閱建議的作法，針對，可以選取要顯示結果的其他資訊的區域。 每個項目詳細資料包含_了解更多_連結這將帶您直接前往測試與相關的適當指引。 出現在**執行任何動作所需**類別的測試結果指出合規性的相關規則，並不會顯示選取時的其他詳細資料。

診斷測試] 索引標籤中的資訊將不告訴您如何設計頁面，但會醒目提示可能會影響頁面效能的因素。 某些] 頁面上的功能和自訂項目無法避免影響對頁的執行效能，並應該檢閱潛在修復或省略從頁面中，如果其影響可能很大。

紅色或黃色結果也可能表示太常重新整理資料的網頁組件。 例如，公司的新聞不會更新每秒，但通常建立自訂網頁組件的擷取的最新消息而不是實作快取可以提升整體使用者體驗的項目每秒。 請記住，當它的預定用途包括網頁組件頁面上，通常是簡單的方法，以減少其效能影響評估的每個可用的參數，以確保其值適當地設定。

>[!NOTE]
>不需要啟用發佈功能的傳統的小組網站不能使用 Cdn。 當您在這些網站上執行此工具時，CDN 測試預期會失敗，而且可以被忽略，但所有其餘測試都適用。 SharePoint 發佈功能的其他功能可能會增加頁面載入時間，因此不應啟用目的只是為了讓 CDN 功能。

>[!IMPORTANT]
>新增測試規則，以及更新定期如此最新版的目前的規則和測試結果中包含的特定資訊的詳細資料的工具，請參閱。 您可以藉由管理您的擴充功能確認版本和分機號碼將會告知是否有可用的更新。

## <a name="how-to-use-the-network-trace-tab"></a>如何使用網路追蹤] 索引標籤

[**網路追蹤**] 索引標籤提供建立] 頁面上，從 SharePoint 所收到的回應這兩個要求的詳細的資訊。

1. **尋找項目載入時間標示為紅色**。 每個要求和回應的效能會以色彩標示，根據其對整體網頁效能的影響，如下所示：
    - 綠色： \< 500 毫秒
    - 黃色： 500 1000ms
    - 紅色： \> 1000ms

    ![網路追蹤](media/page-diagnostics-for-spo/pagediag-networktrace.png)

    在上面顯示的圖像，紅色的項目相關的預設頁面。 它將一律顯示紅色除非中載入頁面\<1000ms （少於 1 秒）。

2. **測試項目載入時間**。 在某些情況下會沒有時間] 或 [色彩標記因為項目已由瀏覽器快取。 若要正確測試，開啟 [] 頁面上，清除瀏覽器快取，然後按一下**啟動**時，會強制載入 「 寒冷 」 頁面，而且是初始頁面載入，則為 true 反映。 這應該然後比較 」 暖 「 頁面負載時，也可協助判斷哪些項目會在頁面上快取。

3. **共用與他人可以幫助調查問題的相關詳細資料**。 若要共用的詳細資料或資訊與您的開發人員或技術支援人員提供工具中，按一下 [**匯出至 JSON （如上述影像所示）。** 可讓您將結果，檢視使用 JSON 檔案檢視器下載。

    如果您已選擇使用預覽功能，*讓匯出至哈*匯出類型將會顯示為 [**匯出至哈**。

    ![網路追蹤](media/page-diagnostics-for-spo/pagediag-NetworkTraceHAR.PNG)

> [!IMPORTANT]
> 這些結果包含的 Url 和，可以分類為 PII （個人識別資訊）。 請務必遵循貴組織的指導方針之前散佈該資訊。

## <a name="engaging-with-microsoft-support"></a>吸引與 Microsoft 支援服務

我們已包含**Microsoft 的支援層級功能**，您應該只能利用直接對支援案例。 運用這項功能會帶來任何效益，為您提供不支援小組 engagement 中，使用時，可以進行] 頁面上執行大幅速度變慢。 在工具中使用這項功能，當其他資訊新增至服務中的記錄時，沒有其他資訊。

不會變更為可見，不同之處在於您是否已啟用它與您] 頁面上的效能將會大幅降低藉由將會通知您 2-3 次較慢的效能，而啟用。 它只會與相關的特定頁面及該作用中的工作階段。 基於這個理由，這應該謹慎使用，只有當主動投入支援。

### <a name="to-enable-the-microsoft-support-level-feature"></a>若要啟用 Microsoft 的支援層級功能

1. 開啟 [SharePoint 工具] 頁面上診斷]。
2. 在鍵盤上按下**ALT-Shift-L**。 這會顯示**啟用的支援記錄**] 核取方塊。
3. 選取核取方塊，，然後按一下 [**開始**重新載入頁面，並產生詳細資訊記錄。

    ![啟用的支援選項](media/page-diagnostics-for-spo/pagediag-support.png)
  
    您應該記下的相互關聯識別碼 （顯示在工具的頂端），並且提供給您支援人員，以啟用這些收集診斷工作階段相關的其他資訊。

## <a name="related-topics"></a>相關主題

[調整 SharePoint Online 效能](tune-sharepoint-online-performance.md)

[調整 Office 365 效能](tune-office-365-performance.md)

[內容傳遞網路](content-delivery-networks.md)
