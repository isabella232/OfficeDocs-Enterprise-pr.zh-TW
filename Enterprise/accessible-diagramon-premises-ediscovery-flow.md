---
title: "存取圖表-內部部署 eDiscovery 流程"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b9dcd692-0485-4eec-870d-87ab6b89d97b
description: "本文是名為內部部署 eDiscovery 流程圖表可存取的文字版本。"
ms.openlocfilehash: e137a75fb80c9198a332144d82fe405c6884aa52
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="accessible-diagram---on-premises-ediscovery-flow"></a>存取圖表-內部部署 eDiscovery 流程

**摘要：**本文是名為內部部署 eDiscovery 流程圖表可存取的文字版本。
  
此海報提供詳細資訊架構及流程資料的伺服器產品。 
  
## <a name="across-sharepoint-exchange-lync-and-file-shares"></a>整個 SharePoint、 Exchange、 Lync 與檔案共用

此圖顯示使用者傳送存取兩個伺服器陣列、 SharePoint 2013 企業應用程式伺服器陣列，並在 SharePoint 2013 服務伺服器陣列的查詢。SharePoint 2013 服務伺服器陣列與 SharePoint 2013 內容伺服器陣列、 Exchange Server 2013 （這會與 Lync 2013 的通訊）、 通訊及 Windows 檔案共用。 
  
EDiscovery 流程清單說明資料和順序中的 eDisovery 查詢動作發生跨 SharePoint、 Exchange、 Lync 與檔案共用的流程。 
  
EDiscovery 流程清單會詳細描述於第一次，後面所述之圖表中的功能的詳細說明。 
  
### <a name="ediscovery-flow-list"></a>eDiscovery 流程的清單

這份清單中所述的步驟的每個號碼與圖表中所述的步驟。本文稍後的詳細說明圖表。 
  
1. eDiscovery 案例所建立、 管理及 eDiscovery 中心 (EDC) 中所使用。EDC 為 SharePoint 2013 網站集合。這是其中的情況下所定義、 識別來源來追蹤、 發出查詢、 查詢結果的檢閱，以及保留中的內容會置於或移除。 
    
2. EDiscovery 查詢或巨集指令，例如就地保留、 ReleaseHold 或 GetStatus、 從轉送 EDC 至企業應用程式伺服器陣列中的 Search Service 應用程式 (SSA) proxy。然後 SSA proxy 會轉送至服務應用程式伺服器陣列中的 SSA 流量。在這個範例中，要求是將任何項目放入含有"CONTOSO"SharePoint 內容伺服器陣列中保留的檔案名稱。 
    
3. 如果要求，以查詢案例 SSA 查閱搜尋索引。然後，eDiscovery 查詢結果集傳回給 EDC 透過使用者。 
    
4. 如果要求的動作，例如就地保留或 ReleaseHold，該動作會寫入 Actions_Table SSA 管理資料庫中。在這個範例中，保留要求以"CONTOSO"SharePoint 內容伺服器陣列中的任何項目會寫入 Actions_Table。 
    
5. 在固定間隔內容伺服器陣列 eDiscovery 就地保留計時器工作喚醒及產生擱置動作要求並傳送到 SSA proxy 的狀態更新至 SSA。 
    
6. 擱置動作的查詢轉送至中央的 SSA 查閱 Action_Table 以取得所有暫止的內容伺服器陣列的動作。就地保留計時器服務內容的伺服器陣列也會傳送物件和動作已接收到，會寫入至 ActionsTable 的狀態更新。 
    
7. 保留要求的 SharePoint 2013 內容伺服器陣列中的名稱以"CONTOSO"任何內容 SSA 來傳送至內容伺服器陣列中的 eDiscovery 就地保留計時器工作。 
    
8. EDiscovery 就地保留計時器工作 places"CONTOSO Site"和"CONTOSO content"上的保留。 
    
9. 企業應用程式伺服器陣列以檢查探索動作的狀態和更新狀態中定期執行 eDiscovery 就地保留計時器工作。 
    
10. 狀態查詢轉送至 SharePoint Services 伺服器陣列 SSA 的企業應用程式伺服器陣列 SSA proxy 透過。 
    
11. SSA 動作資料表擷取狀態，並傳回將狀態更新至 EDC 推入企業應用程式伺服器陣列中的計時器工作。 
    
12. 當 eDiscovery 使用者會搜尋 （或執行的動作） Exchange 來源，例如信箱或封存的 Lync 內容中央 SSA 使用 Exchange Web 服務 (EWS) 來查詢 Exchange Web 服務的 proxy。Exchange 有其專屬搜尋和 eDiscovery 的基礎結構，以及適用於內部管理 eDiscovery 的所有通話。 
    
13. Exchange Web 服務回應 SSA 與 eDiscovery 搜尋結果或查詢式保留，它會依次取得轉送至 EDC 狀態要求回應。 
    
#### <a name="prerequisites"></a>必要條件

- SharePoint 企業搜尋必須設定、 成功出現在 [內容來源 （SharePoint 及 Windows 檔案共用） 上的搜尋編目及索引中的所有內容來源。 
    
- SharePoint Services 伺服器陣列與 Exchange 之間及 Exchange 與 Lync 之間必須設定伺服器對伺服器信任和驗證。 
    
### <a name="description-of-components-in-the-diagram"></a>圖表中的元件的描述

此圖顯示使用者傳送的查詢時，會存取有關兩個伺服器陣列，在 SharePoint 2013 企業應用程式伺服器陣列與 SharePoint 2013 服務伺服器陣列。SharePoint Services 伺服器陣列介面 （英文） 與 SharePoint 2013 內容伺服器陣列、 Exchange Server 2013 （此介面搭配 Lync 2013） 和 Windows 檔案共用。 
  
#### <a name="sharepoint-2013-enterprise-app-farm"></a>SharePoint 2013 企業應用程式伺服器陣列

SharePoint 2013 企業應用程式伺服器陣列包含下列元件： 
  
- EDC
    
- SSA proxy 
    
- 計時器工作 
    
以查詢或使用者所傳送的動作會傳送至企業應用程式伺服器陣列中 EDC。發生下列動作： 
  
- 以查詢或巨集指令會前往 SSA proxy。 
    
- 企業應用程式伺服器陣列中的 SSA proxy 傳送狀態以查詢或回應的計時器工作及它也會傳送狀態以查詢或 SSA 服務回應 SharePoint Services 伺服器陣列中。動作所產生的這節所述有關 SharePoint Services 伺服器陣列。 
    
- 它會收到回應，計時器工作會傳送 SSA proxy 並 EDC 回應。 
    
- 從 EDC 查詢或巨集指令的任何結果傳送給使用者。 
    
#### <a name="sharepoint-2013-services-farm"></a>SharePoint 2013 服務伺服器陣列

SharePoint 2013 服務伺服器陣列包含下列元件： 
  
- SSA 服務 
    
- 搜尋索引資料庫 
    
- SSA admin_db 資料庫。此資料庫中的 [動作] 表格包含： 保留版本保留 GetStatus 
    
- EWS proxy 
    
當 SharePoint 企業應用程式伺服器陣列中的 SSA proxy 傳送至 SharePoint Services 伺服器陣列中的 SSA 狀態查詢時，便會發生下列動作： 
  
- 如果查詢要求，SSA 查閱搜尋索引。探索回應傳回 SSA]、 [使用者通過 EDC。 
    
- 如果寫入動作要求，SSA 服務會將寫入動作傳送至 SSA admin_db。 
    
- 編目及回應結果要求從 SSA 傳送至 SharePoint 2013 內容伺服器陣列和回應傳回至 SSA。 
    
- 編目及回應結果要求從 SSA 傳送至 Windows 檔案共用，並將回應傳回至 SSA。 
    
- 擱置的動作、 回應或狀態更新的查詢 SSA 從傳送到 SharePoint 內容伺服器陣列中的 SSA proxy 並將回應傳回至 SSA。 
    
- Exchange 巨集指令/狀態要求從 SSA 傳送到 EWS proxy、 將 Exchange 查詢巨集指令/狀態要求傳送至 Exchange 2013 伺服器上的 Exchange Web 服務。 
    
- 狀態查詢回應從 SSA 傳送到 SSA admin_db 並傳回至 SSA。 
    
- 擱置巨集指令查詢回應從 SSA 傳送到 SSA admin_db 並傳回至 SSA。 
    
#### <a name="sharepoint-2013-content-farm"></a>SharePoint 2013 內容伺服器陣列

SharePoint 2013 內容伺服器陣列包含下列元件： 
  
- SSA proxy 
    
- 計時器工作 
    
- Contoso SharePoint 網站 
    
- Contoso SharePoint 內容 
    
當 SharePoint Services 伺服器陣列中的 SSA 將狀態查詢 SSA Proxy SharePoint 內容伺服器陣列中時，會發生下列動作： 
  
- SharePoint 內容伺服器陣列中的 SSA proxy 會擱置的計時器工作狀態動作/回應將查詢傳送。 
    
- 計時器工作會將要求傳送至 Contoso SharePoint 網站中，檢閱 Contoso SharePoint 內容。 
    
- 計時器工作已傳送回應等候中的動作狀態查詢 SSA proxy SharePoint 內容伺服器陣列，然後它會傳送至 SharePoint Services 伺服器陣列中的 SSA 服務 
    
#### <a name="exchange-2013"></a>Exchange 2013

Exchange 2013 伺服器元件包含 Exchange Web 服務並提供下列功能： 
  
- 伺服器對伺服器信任/OAuth 的 SharePoint 2013 內容伺服器陣列與 Exchange 2013 間處理方式。 
    
- 伺服器對伺服器信任/OAuth 會處理 Exchange 2013 和 Lync 2013 之間。 
    
#### <a name="lync-2013"></a>Lync 2013

Lync 2013 元件封存在 Exchange 2013 的 Lync 內容。 
  
#### <a name="windows-file-shares"></a>Windows 檔案共用

[Windows 檔案共用元件提供 SharePoint Services 伺服器陣列中的 SSA 編目結果。 
  
### <a name="legend"></a>圖例

這個圖表的圖例以圖形顯示不同類型的流量所述之不同的彩色行元件之間，如下所示： 
  
- 淺藍色線條： 查詢/動作-eDiscovery 查詢或巨集指令的資料 
    
- 橘色線條： eDisovery 回應-eDiscovery 查詢回應資料 
    
- 綠色線條： 狀態查詢/回應-eDiscovery 狀態查詢/回應資料 
    
- 紫色線條： Exchange 巨集指令/狀態要求 eDiscovery 要求的動作狀態的 Exchange 流量。 
    
- 紅色線： Exchange 資料/狀態回應-從 Exchange 的 eDiscovery 查詢或狀態回應。 
    
- 點線黑色線條： 伺服器對伺服器信任/Oauth 
    
- 黑色實線： 編目/結果 
    

