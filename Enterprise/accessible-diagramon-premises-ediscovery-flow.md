---
title: 易於存取的圖表-內部 eDiscovery 流程
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b9dcd692-0485-4eec-870d-87ab6b89d97b
f1.keywords:
- NOCSH
description: 本文是名為內部部署 eDiscovery 流程圖表易於存取的文字版本。
ms.openlocfilehash: ec9ecf7d3663503f2da412364d919a6c70032e23
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843854"
---
# <a name="accessible-diagram---on-premises-ediscovery-flow"></a>易於存取的圖表-內部 eDiscovery 流程

**摘要：** 本文是名為內部部署 eDiscovery 流程圖表易於存取的文字版本。
  
此海報提供數個伺服器產品的詳細資訊架構及資料流。 
  
## <a name="across-sharepoint-exchange-lync-and-file-shares"></a>跨 SharePoint、 Exchange、 Lync 與檔案共用

此圖顯示使用者傳送的查詢來存取兩個伺服器陣列、 SharePoint 2013 企業應用程式伺服器陣列，並在 SharePoint 2013 服務伺服器陣列。 SharePoint 2013 服務伺服器陣列與 SharePoint 2013 內容伺服器陣列，Exchange Server 2013 （這會與 Lync 2013 通訊） 進行通訊及 Windows 檔案共用。 
  
EDiscovery 流程清單說明資料和哪些 eDisovery 查詢動作發生跨 SharePoint、 Exchange、 Lync 和檔案共用的順序的流程。 
  
EDiscovery 流程清單會詳細說明首先，後面接著在圖表中所述的功能的詳細說明。 
  
### <a name="ediscovery-flow-list"></a>eDiscovery 流程清單

每個步驟中此清單所述的號碼適用於在圖表中所述的步驟。 本文件稍後詳細說明圖表。 
  
1. 建立、 管理和 eDiscovery 中心 (EDC) 中使用 eDiscovery 案例。 EDC 是 SharePoint 2013 網站集合。 這是其中定義案例、 要追蹤的來源識別、 發出查詢、 檢閱查詢結果，以及進行內容保留或移除暫停。 
    
2. EDiscovery 查詢或動作，例如就地保留、 ReleaseHold 或 GetStatus，從轉送 EDC 至企業應用程式伺服器陣列中的 Search Service 應用程式 (SSA) proxy。 SSA proxy 再轉送至服務應用程式伺服器陣列中的 SSA 的流量。 在這個範例中，要求在具有 「 CONTOSO 」 的 SharePoint 內容伺服器陣列中放置的任何項目會保留的檔案名稱中。 
    
3. 如果要求来查詢的情況下，SSA 查閱搜尋索引。 然後，eDiscovery 查詢結果集傳回給使用者透過 EDC。 
    
4. 如果要求的動作，例如就地保留或 ReleaseHold，該巨集指令寫入 Actions_Table SSA 管理資料庫中。 在這個範例中，在具有 「 CONTOSO 」 的 SharePoint 內容伺服器陣列中的任何項目保留要求會寫入 Actions_Table。 
    
5. 在固定間隔內容伺服器陣列 eDiscovery 就地保留計時器工作喚醒要求擱置中的動作將會產生並將狀態更新，透過 SSA proxy 傳送到 SSA。 
    
6. 擱置中的動作的查詢轉送至中央的 SSA 查閱 Action_Table 以取得任何擱置中的內容伺服器陣列的動作。 內容伺服器陣列的就地保留計時器工作也會傳送狀態更新的物件和它已收到，寫入至 ActionsTable 的動作。 
    
7. 「 CONTOSO 」 與 SharePoint 2013 內容伺服器陣列中的名稱中的所有內容保留要求是由 SSA 傳送給內容伺服器陣列中的 eDiscovery 就地保留計時器工作。 
    
8. EDiscovery 就地保留計時器工作位置上的 「 CONTOSO 內容 」 與 「 CONTOSO 網站 」 保留。 
    
9. 若要檢查探索動作的狀態，並更新狀態企業應用程式伺服器陣列中定期執行 eDiscovery 就地保留計時器工作。 
    
10. 狀態查詢轉送至 SharePoint Services 伺服器陣列 SSA 的企業應用程式伺服器陣列 SSA proxy 透過。 
    
11. SSA 動作資料表中擷取狀態，並傳回的狀態更新發送至 EDC 企業應用程式伺服器陣列中的計時器工作。 
    
12. 當 eDiscovery 使用者搜尋 （或執行巨集指令） 對於 Exchange 來源，例如信箱或封存的 Lync 內容，中央 SSA 使用查詢 Exchange Web 服務的 Exchange Web 服務 (EWS) proxy。 Exchange 有其專屬搜尋和 eDiscovery 的基礎結構，並在內部管理電子文件探索的所有呼叫。 
    
13. Exchange Web 服務回應 SSA 與 eDiscovery 搜尋結果或查詢式保留，其中，接下來取得轉送至 EDC 狀態要求的回應。 
    
#### <a name="prerequisites"></a>必要條件

- SharePoint 企業搜尋必須設定，成功出現在 [內容來源 （SharePoint 及 Windows 檔案共用） 上的搜尋編目和索引中有所有內容來源。 
    
- SharePoint Services 伺服器陣列與 Exchange 之間，以及 Exchange 與 Lync 之間，必須設定伺服器對伺服器信任和驗證。 
    
### <a name="description-of-components-in-the-diagram"></a>元件圖表中的描述

此圖顯示使用者傳送的查詢時，會存取兩個伺服器陣列，在 SharePoint 2013 企業應用程式伺服器陣列與 SharePoint 2013 服務伺服器陣列。 SharePoint 服務伺服器陣列介面與 SharePoint 2013 內容伺服器陣列，Exchange Server 2013 （這介面搭配 Lync 2013），及 Windows 檔案共用。 
  
#### <a name="sharepoint-2013-enterprise-app-farm"></a>SharePoint 2013 企業應用程式伺服器陣列

在 SharePoint 2013 企業應用程式伺服器陣列包含下列元件： 
  
- EDC
    
- SSA proxy 
    
- 計時器作業 
    
以查詢或使用者所傳送的巨集指令會傳送至企業應用程式伺服器陣列中 EDC。 會發生下列動作： 
  
- 查詢或巨集指令移至 SSA proxy。 
    
- SSA proxy 傳送企業應用程式伺服器陣列中的狀態查詢或回應的計時器工作，它也會傳送狀態以查詢或 SSA 服務回應 SharePoint Services 伺服器陣列中。 動作所產生的這一節所述有關 SharePoint 服務伺服器陣列。 
    
- 它會收到回應，計時器工作會傳送 SSA proxy，並 EDC 回應。 
    
- 任何來自查詢或巨集指令的結果是從 EDC 傳送給使用者。 
    
#### <a name="sharepoint-2013-services-farm"></a>SharePoint 2013 服務伺服器陣列

SharePoint 2013 服務伺服器陣列包含下列元件： 
  
- SSA 服務 
    
- 搜尋索引資料庫 
    
- SSA admin_db 資料庫。 此資料庫中的 [動作] 表格包含： 保留版本保留 GetStatus 
    
- EWS proxy 
    
當 SharePoint 企業應用程式伺服器陣列中的 SSA proxy 會將狀態查詢傳送至 SharePoint Services 伺服器陣列中的 SSA 時，就會發生下列動作： 
  
- 如果要求的查詢，SSA 查閱搜尋索引。 探索會將回應傳回至 SSA，然後透過 EDC 使用者。 
    
- 如果要求是寫入巨集指令，SSA 服務會將寫入巨集指令傳送至 SSA admin_db。 
    
- 編目和回應結果要求會從 SSA 傳送至 SharePoint 2013 內容伺服器陣列，並將回應傳回至 SSA。 
    
- 編目和回應結果要求會從 SSA 傳送至 Windows 檔案共用，並將回應傳回至 SSA。 
    
- 暫止的動作、 回覆或狀態更新的查詢 SSA 從傳送至 SharePoint 內容伺服器陣列中的 SSA proxy 並將回應傳回至 SSA。 
    
- Exchange 巨集指令/狀態要求會從 SSA 傳送到 EWS proxy，將 Exchange 查詢巨集指令/狀態要求傳送至 Exchange 2013 伺服器上的 Exchange Web 服務。 
    
- 狀態查詢回應從 SSA 傳送至 SSA admin_db，而且會傳回至 SSA。 
    
- 擱置中的巨集指令查詢回應從 SSA 傳送至 SSA admin_db，而且會傳回至 SSA。 
    
#### <a name="sharepoint-2013-content-farm"></a>SharePoint 2013 內容伺服器陣列

在 SharePoint 2013 內容伺服器陣列包含下列元件： 
  
- SSA proxy 
    
- 計時器作業 
    
- Contoso SharePoint 網站 
    
- Contoso SharePoint 內容 
    
當 SharePoint Services 伺服器陣列中的 SSA 將狀態查詢傳送至 SharePoint 內容伺服器陣列中的 SSA Proxy 時，則會發生下列動作： 
  
- SharePoint 內容伺服器陣列中的 SSA proxy 會將查詢傳送暫止的動作/狀態回應計時器工作。 
    
- 計時器工作將要求傳送至 Contoso SharePoint 網站中，檢閱 Contoso SharePoint 內容。 
    
- 回應等候中的動作狀態查詢從計時器工作傳送到 SharePoint 內容伺服器陣列中的 SSA proxy，然後它會傳送至 SharePoint Services 伺服器陣列中的 SSA 服務 
    
#### <a name="exchange-2013"></a>Exchange 2013

Exchange 2013 伺服器元件包含 Exchange Web 服務，並提供下列功能： 
  
- 伺服器對伺服器信任/OAuth 是 Exchange 2013 與 SharePoint 2013 內容伺服器陣列之間進行處理。 
    
- 伺服器對伺服器信任/OAuth 是 Exchange 2013 和 Lync 2013 之間進行處理。 
    
#### <a name="lync-2013"></a>Lync 2013

Lync 2013 元件封存在 Exchange 2013 的 Lync 內容。 
  
#### <a name="windows-file-shares"></a>Windows 檔案共用

Windows 檔案共用元件提供 SharePoint Services 伺服器陣列中的 SSA 編目結果。 
  
### <a name="legend"></a>圖例

這個圖表的圖例以圖形方式顯示不同類型的流量所描述之不同的彩色行中元件之間，如下所示： 
  
- 淺藍色線條： 查詢/動作-eDiscovery 查詢或巨集指令的資料 
    
- 橘色線條： eDisovery 回應-eDiscovery 查詢回應資料 
    
- 綠色線條： 狀態查詢/回應-eDiscovery 狀態查詢/回應資料 
    
- 紫色線條： Exchange 巨集指令/狀態要求-eDiscovery 要求 Exchange 流量的巨集指令狀態。 
    
- 紅色列： Exchange 資料/狀態回應-從 Exchange 的 eDiscovery 查詢或狀態回應。 
    
- 點狀黑色線條： 伺服器對伺服器信任/Oauth 
    
- 黑色實線： 編目/結果 
    

