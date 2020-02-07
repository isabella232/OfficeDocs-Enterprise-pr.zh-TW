---
title: 若要考慮 SharePoint 2007 遷移選項
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 1/31/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
search.appverid:
- MET150
- SPS150
- OSU140
- SPO160
- SPB160
- OSI150
- OSI160
- BSA160
- OSU160
ms.assetid: 66325a43-5816-4f8e-81ba-c11b71345b7c
f1.keywords:
- NOCSH
description: SharePoint Server 2007 已達到終止支援，及該是時候來升級。 使用這篇文章可協助您建立您的計劃。
ms.openlocfilehash: 607dfeaedb1a63634e08e28f8aef2c6fcce6ce9c
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841150"
---
# <a name="sharepoint-2007-migration-options-to-consider"></a>若要考慮 SharePoint 2007 遷移選項

*本文適用於 Office 365 企業版和 Microsoft 365 企業版。*

Microsoft SharePoint 2007 與 SharePoint Server 2007 已達到終止支援。 該是時候來升級 ！ 本文提供您的遷移選項的相關資訊。
  
## <a name="common-upgrade-strategies-for-sharepoint"></a>SharePoint 的一般升級策略

有多種方法來升級 SharePoint Server 環境。 如果您有 Microsoft Office SharePoint Server 2007 伺服器陣列時，以下是升級方法的一些範例：
  
- 資料庫附加
    
- 並排顯示升級
    
- 就地升級 
    
- 混合式升級 (就地升級以卸離資料庫 / 不同資料庫附加)
    
- SharePoint 混合 （連線至內部部署 SharePoint）
    
- 以手動方式將資料移之間的網站集合或文件庫
    
- FastTrack 精靈升級到 Office 365 ([SharePoint Online 部署建議程式](https://aka.ms/spoguidance))
    
- 移轉至 SharePoint Online (SPO) 中 Office 365 API
    
項目最適合您？
  
您的伺服器陣列的項目並未以及用於知識時提到升級策略強度。 人員使用的 SharePoint 伺服器陣列的方式可協助您選擇的選項。
  
> [!TIP]
> Microsoft Office SharePoint Server 2007 也有未深入涵蓋以下逐步升級。 若要查看特定步驟的升級的文章會看到[SharePoint Server 2007 終止支援藍圖](sharepoint-2007-end-of-support.md)。 
  
請記得檢查任何版本的升級至 SharePoint[產品生命週期](https://support.microsoft.com/lifecycle/search)與系統需求。 這是讓您將會注意時 （例如，如果您在 SharePoint Server 2010 規劃多個升級，請確定您知道其支援日期結尾，如舊版產品暫停），則必須進行下一次升級，以確保您有支援您的計劃的硬體。 
  
如果您計劃轉換部分，或全部，您的 SharePoint 網站至 Office 365，在雲端中，這是書籤連結至[Office 365 服務說明](https://technet.microsoft.com/library/office-365-service-descriptions.aspx)的時間。 您需要的服務描述以深入了解 SharePoint Online 的功能以及它們可能之間的差異從內部部署 SharePoint Server。 升級功能的 Microsoft Office SharePoint Server 2007 伺服器陣列。 如果您安裝已損毀的網站，修正它們，在升級之前。
  
## <a name="a-note-about-managing-risk"></a>附註的相關風險管理

'-並存' 類似的方法很重要的升級的邏輯配置中。 當您升級並排顯示時，您維護您的 Microsoft Office SharePoint Server 2007 伺服器陣列，但建置在伺服器陣列的下一個版本 (SharePoint Server 2010) 從新硬體上。 這三種方式可以幫助：
  
1. 您必須進行 Microsoft Office SharePoint Server 2007 資料庫的備份分開升級，請使用資料庫附加的位置。
    
2. 如果您找出只有少數重要的文件庫及其他資訊會在您的 Microsoft Office SharePoint Server 2007 伺服器陣列上使用，您可以選擇以手動方式將資料從 Microsoft Office SharePoint Server 2007 移至 SharePoint Server 2010否則只有特定的網站與 web 的下一個版本 （這可以讓您的工作更容易）。
    
3. 較少您執行 Microsoft Office SharePoint Server 2007 伺服器陣列，直接，更安全的伺服器陣列的資料包含作為您升級。
    
方法，例如就地升級將擔任直接在 Microsoft Office SharePoint Server 2007 伺服器陣列，提供您放棄路徑，並再次開頭提出環境較少簡單選項。 盡可能，建立一些安全措施，（例如，以及測試原始環境的備份）。 例如，如果您的 Microsoft Office SharePoint Server 2007 伺服器陣列虛擬，且基於備份與還原為重複項目，然後備份和還原您的服務窗口升級前的最新資料庫。 了解您可以還原資料庫備份不會選擇只提供保全，它可讓您的想法和平。
  
> [!TIP]
> 升級的最佳做法文件存在[Microsoft Office SharePoint Server 2007](https://technet.microsoft.com/library/cc261992%28v=office.12%29.aspx)、 [SharePoint Server 2010](https://technet.microsoft.com/library/cc261992%28v=office.14%29.aspx)、 [SharePoint Server 2013](https://technet.microsoft.com/library/cc261992%28v=office.15%29.aspx)和[SharePoint Server 2016](https://technet.microsoft.com/library/cc261992%28v=office.16%29.aspx)。 您也可以搜尋適用於[Microsoft 合作夥伴](https://partnercenter.microsoft.com/pcv/search)擁有升級或 Office 365 移轉的經驗。 
  
## <a name="make-your-plan"></a>讓您的計劃

如果您需要升級，則必須計劃，以及一個大小不符合所有在這些情況下。 您的計劃可能 '與 SharePoint Online 中建立 Office 365 訂閱、 註冊的網域，並重新導向人員來儲存其檔案有' 一樣簡單。 它可能不是。 決定是你，而且下您和您的使用者確實需要的項目。
  
> [!NOTE]
> 它是風險軟體其生命週期結束上執行。 發現問題時，不再被修補超出支援的產品。 這也表示，如果出現新的安全性威脅，會有任何安全性修補程式或修正因為不再支援的生命週期的結束產品。 請避免這種情況 ！ 
  
### <a name="first-know-your-farm"></a>首先，了解您的伺服器陣列

升級時，您做決定應該根據您的伺服器陣列並為您的組織。 它並未滿足哪些需求？ 其角色是什麼？ 在您的公司中每個伺服器陣列可能會有不同的角色。 您的 SharePoint 伺服器陣列的一些可能*重要*，有些可能是檔案封存-以便安全保存該處。 或者，如果您的伺服器陣列會一次填滿多個角色，然後您可能需要知道哪些網站集合、 網站或甚至是文件庫，任何自訂項目，以及它們是重要程度。 分析您的資料，在此層級看起來好像許多工作，但它會儲存時間和精力精通您的網域，再升級，或遷移時，它。 一旦您知道所有移動的組件，並將最重要的位元，也會知道的項目已 outgrown 以及可能會留下。 該知識只會受益您接下來。 
  
因此，哪些使用者說最重要的 SharePoint Server 伺服器陣列的相關？
  
- 內建的 SharePoint 功能
    
- 大型資料主體 （例如封存的檔案）
    
- 可用性
    
- 重要的應用程式、 網頁組件或伺服器陣列 （任務重要伺服器陣列） 中的文件
    
- 符合規範標準
    
- 自訂
    
如果您執行的基本貴公司從 SharePoint 伺服器陣列的某個項目，請說它就像用戶端服務需求的相關重要資料的大型目錄時，您可能會讓刻度旁邊 '重要應用程式'，但也就是 '可用性'-亦即您的業務如果您無法使用 SharePoint 一段時間的，影響。 同樣地，您可能會檢查 '自訂'，因為重要服務伺服器陣列提供取決於自訂程式碼、 網站定義或自訂項目會一起運作的數字。
  
如果 SharePoint 符合這些需求，而不用執行任何外部使用什麼內建至軟體，以及您通常會更新，並執行一般管理以及維護、 您選擇 「 內建的 SharePoint' 的成員，這也可能是您坐在較舊版本的 SharePoint 上的理由。 換句話說，它已經沒有您需要它，且您尚未需要升級直到現在，在 Microsoft Office SharePoint Server 2007 終止支援。
  
當您項目符號清單這些項目，您建立準則您的升級。 換句話說，任何升級必須符合才會視為此列。 這可以讓您用來排除目前不符合您需求的方法。
  
### <a name="a-simple-sample-plan"></a>簡單的範例方案

那里可能需要與領導寬共識和其他系統管理員在 SharePoint 升級將所採取的路徑。 SharePoint Server 系統管理員通常與 Microsoft SQL Server 系統管理員合作，搭配網路與安全性小組，等等。 其中有許多專案關係人，您可能需要建立合約，或調整您的升級與移轉計劃。 例如，如果您要遷移的資料，使您公司的一部分使用 SharePoint Online 的 Office 365 中，那里可能需要為效能調整或測試您的網路內。 受影響的小組應該事先通知。
  
在 「 我的簡單範例中，我會顯示 SharePoint 系統管理員的提案，並再列出所有專案關係人同意計劃。 為了清楚起見，文件協議與決策。
  
規劃伺服器陣列，深入分析後啟動，並嘗試識別角色的伺服器陣列、 痛點及縮小下某些升級選項將會導致其他重要資訊。 之後，由 SharePoint 系統管理員進行升級的提案，以及專案關係人同意的行動計劃。
  
我 '最重要' 的項目符號清單：
  
- 可用性、 內建至 SharePoint 的功能和合規性標準。
    
- 大部分的資料是在三個網站集合，與開發小組特別重要和粗用於多個時區中使用世界各地的一個會議工作區。
    
- 有十七廣泛使用其他網站。
    
- 兩個文件庫 （會議工作區和根網站集合上的文件） 是最大 (超過 8000 docs 每個)。 我們有大量的已封存的文件和試算表附件清單。
    
- 有十四清單有必須保持在合規性的敏感資料的文件庫。
    
- 我們必須能夠執行保留和 e-探索儘我們移。
    
- 有些資料必須保持內部部署，因為常見規則。
    
 **我的升級與移轉選項：**
  
|||
|:-----|:-----|
|**是** <br/> |**否** <br/> |
|附加資料庫的升級資料庫  <br/> |就地升級   <br/> |
|升級伺服器陣列-並存  <br/> |混合式升級  <br/> |
|移轉 API 到 Office 365 中的 SPO （適用於個人網站資料）  <br/> |SharePoint 混合式 （尚未不需要）  <br/> |
|到 SharePoint Online 重要資料的一些手動資料移轉  <br/> |FastTrack 精靈升級至 Office 365  <br/> |
   
 **我提議的計劃：**
  
升級，具有內部版本的 SharePoint-並存，某些虛擬化，以便我們可以先升級資料庫。 從 SharePoint 2007 前往 SharePoint 2010。 系統管理員和適用於開發人員測試所產生的伺服器陣列。 使用者測試所產生的伺服器陣列。 在這段時間修正任何顯示停止問題。 同樣地，並排顯示、 升級 SharePoint 2010 資料庫至 SharePoint 2013。 測試。 使用者測試/試驗。 在這段時間修正任何顯示停止問題。
  
- 請考慮使用 SPO 搜尋同盟混合是否符合您的需求。
    
- 如果您想要從這裡升級至 SharePoint Online，請考慮[FastTrack 協助](https://fasttrack.microsoft.com)。 
    
- 決定任何網站集合是否可以卸載到 Office 365 訂閱。 （office 365 符合許多[合規性標準](https://technet.microsoft.com/library/office-365-compliance.aspx)。 Office 365 具有[eDiscovery](https://support.office.com/article/edea80d6-20a7-40fb-b8c4-5e8c8395f6da)而且可以透過合規性中心的 [[保留](https://support.office.com/article/A18F8975-AA7F-43B4-A7D6-001D14744D8E)。） 
    
否則，請繼續並排顯示升級至 SharePoint Server 2016。
  
> [!NOTE]
> 規劃系統管理員所做的建議傳來升級和實際的程序是發生與升級所仰賴其他專案關係人交談。 例如，有時經濟強制執行系統管理員可以變更其計劃。 任何的最終決策是，您應該記錄同意計劃的是，接下來。 它看起來可能像這樣： 
  
 **我的行動計劃：**
  
內部，我們用來建立預設 SharePoint Server 2010 和 2013年的虛擬環境。 SharePoint Server 2016 會建置 2016 符合系統需求的新硬體上。 我們會執行資料庫附加升級的資料庫從 SharePoint 2007 透過它與 SharePoint Server 2016 之間的所有版本。 核心自訂項目會重新建立為和測試 SharePoint server 2016 環境在這個階段中，如果原生功能已不符合我們的需求。 如果我們已成功，就必須在新硬體上已升級的資料庫，與內部部署伺服器陣列與較少的自訂項目。 我們會將已升級的內容資料庫附加到新的網站集合，在 SharePoint Server 2013 中，測試、 使用者測試/試驗，，然後執行 DNS 剪下移轉至新的 SharePoint Server 2016 環境，供 live 使用。
  
- 我們不會立即考慮同盟混合式 SharePoint Server 2016 和 SharePoint Online 之間。
    
- 我們網站預估的 35%可以轉換成新的 SPO 網站使用虛名網域或者，最終，成為 OneDrive for Business 儲存。 尋找其他機會轉換網站，或將新的站台路由傳送到 SPO。
    
- 這部分的移轉部分將會手動，拖放到 OneDrive for Business 個人網站，以及一些是由移轉 API。
    
詳細步驟，或升級的特定指示的連結的數目應遵循計劃。 MOSS 2007 電腦應該不會解除委任，和虛擬環境維護時，這是因為比較;不過，在升級時，會完整使用者重新導向至 SharePoint Server 2016。
  
在 [選擇方法通常主要因素是升級的總成本和時間 （您會看到有更多 SharePoint 移轉藍圖文章中） 的成本。 不過，規劃向前會受益您大幅中設定期望、 明智，選擇與框架哪些成功看起來像。
  
## <a name="related-links"></a>相關連結

[資源可以幫助您升級從 Office 2007 伺服器和用戶端](upgrade-from-office-2007-servers-and-products.md)
  
[搜尋 Microsoft 週期原則和生命週期](https://support.microsoft.com/lifecycle)
  
[適用於 Microsoft 合作夥伴可以協助進行升級或移轉搜尋](https://partnercenter.microsoft.com/pcv/search)
  

