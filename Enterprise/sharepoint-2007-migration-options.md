---
title: SharePoint 2007 的移轉選項考量
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
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
description: SharePoint Server 2007 已到達結尾的支援，因此該是時候來升級。使用本文以協助您建立您的計劃。
ms.openlocfilehash: 4395bc330efd97ae8865e0fb75f93f04fd162ecd
ms.sourcegitcommit: a9c84d02e94c99ff6b1099b4a9ae695be08210e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2018
ms.locfileid: "21169875"
---
# <a name="sharepoint-2007-migration-options-to-consider"></a>SharePoint 2007 的移轉選項考量

SharePoint Server 2007 與 Microsoft SharePoint 2007 已達到支援結束。該是時候來升級 ！本文提供您的移轉選項的相關資訊。
  
## <a name="common-upgrade-strategies-for-sharepoint"></a>SharePoint 一般升級策略

有多個 SharePoint Server 環境升級方法。如果您有 Microsoft Office SharePoint Server 2007 伺服器陣列時，以下是升級方法的一些範例：
  
- 資料庫附加
    
- 並排顯示升級
    
- 就地升級
    
- 混合式升級 (就地升級以卸離資料庫 / 不同資料庫附加)
    
- SharePoint 混合 （連線 online 至內部部署 SharePoint）
    
- 手動移動網站集合或文件庫之間的資料
    
- FastTrack 精靈升級至 Office 365 （[SharePoint Online 部署顧問](https://aka.ms/spoguidance)）
    
- SharePoint Online (SPO) Office 365 中移轉 API
    
項目最適合您？
  
您的伺服器陣列與項目的用於知識專職升級時策略性強度。使用 SharePoint 伺服器陣列的方式可協助您選擇 [從您的選項。
  
> [!TIP]
> Microsoft Office SharePoint Server 2007 也有未涵蓋以下逐步升級。若清單中的特定步驟的升級文章請參閱[SharePoint Server 2007 結尾支援藍圖](sharepoint-2007-end-of-support.md)。 
  
請記得要檢查您正在升級為 SharePoint 列傳版[產品生命週期](https://support.microsoft.com/en-us/lifecycle/search)與系統需求。此為必須知道時下一次升級需要 （例如，如果您在 SharePoint Server 2010 規劃多個升級，請先確定您知道其結尾支援日期像舊版產品暫停），並確定您有支援您的計劃的硬體。 
  
如果您打算要轉換成部分，或的 SharePoint 網站至 Office 365 雲端中的所有這是時間設為書籤[的 Office 365 服務說明](https://technet.microsoft.com/en-us/library/office-365-service-descriptions.aspx)連結。您需要了解 SharePoint Online 功能的相關服務說明及如何與可能會不同內部部署 SharePoint Server。升級功能的 Microsoft Office SharePoint Server 2007 伺服器陣列。如果您的安裝會中斷的網站，修正那些升級前的。
  
## <a name="a-note-about-managing-risk"></a>有關管理風險的附註

Like '--並排 ' 的方法是邏輯的重要的升級配置中。當您升級並排顯示時，您維護在 Microsoft Office SharePoint Server 2007 伺服器陣列但建置在伺服器陣列下一版從其 (SharePoint Server 2010) 於新硬體上。這有助於方式有三種：
  
1. 您必須採取分別進行升級，請使用資料庫附加的 Microsoft Office SharePoint Server 2007 資料庫備份的位置。
    
2. 如果您了解小型數字的重要的文件庫及其他資訊是使用 Microsoft Office SharePoint Server 2007 伺服器陣列中，您可以選擇手動將資料從 Microsoft Office SharePoint Server 2007 移至 SharePoint Server 2010或採取只有特定的網站和 web 的下一版 （這可讓您工作更易於）。
    
3. 較不您執行 Microsoft Office SharePoint Server 2007 伺服器陣列，直接更安全伺服器陣列的資料包含做為升級。
    
像在就地升級方法將會處理直接在 Microsoft Office SharePoint Server 2007 伺服器陣列上，讓您輕鬆選項減少放棄路徑並再次開頭面貌還和環境。盡、 建置在某些 （例如利用和測試原始環境的備份） 的安全措施。例如，如果您的 Microsoft Office SharePoint Server 2007 伺服器陣列虛擬，且重複基於的備份與還原，然後備份和還原您的服務窗口升級前的最新資料庫。了解您可以還原資料庫備份不會選擇只提供保全，它可提供您和平的事項。
  
> [!TIP]
> 升級的最佳做法文件存在[Microsoft Office SharePoint Server 2007](https://technet.microsoft.com/en-us/library/cc261992%28v=office.12%29.aspx)、 [SharePoint Server 2010](https://technet.microsoft.com/en-us/library/cc261992%28v=office.14%29.aspx)、 [SharePoint Server 2013](https://technet.microsoft.com/en-us/library/cc261992%28v=office.15%29.aspx)及[SharePoint Server 2016](https://technet.microsoft.com/en-us/library/cc261992%28v=office.16%29.aspx)。您也可以搜尋適用於[Microsoft 合作夥伴](https://partnercenter.microsoft.com/en-us/pcv/search)具有與升級或 Office 365 移轉經驗。 
  
## <a name="make-your-plan"></a>讓您計劃

如果您需要升級，您需要規劃與所有的這些情況下不會符合其中一個大小。您的計劃可能一樣簡單 '建立 Office 365 訂閱與 SharePoint Online、 註冊的網域和重新導向至儲存其檔案有人員'。而且可能無法。決定其他，而且可相當下您和使用者確實需要什麼。
  
> [!NOTE]
> 它是 risky 在其生命週期結束的軟體上執行。發現問題時不會再修補不支援的產品。這也表示新的安全性威脅發生時，會有任何安全性修補程式或修正因為不再支援的一般生命週期產品。請避免發生該情況下 ！ 
  
### <a name="first-know-your-farm"></a>首先，了解您的伺服器陣列

在升級時，以協助您做決定應該根據您的伺服器陣列沒有您的組織。則沒有滿足為何需要？什麼是其角色？公司內的每個伺服器陣列可能會有不同的角色。SharePoint 伺服器陣列的一些可能*要徑*、 部分可能會部署封存檔案-安全保存該處。或者，如果您的伺服器陣列會一次填滿許多角色，然後您可能需要知道哪些網站集合、 web 或甚至是文件庫，任何自訂項目，以及他們的重要程度。分析您的資料在此層級似乎許多工作，但它會儲存時間與位置，再升級，或移轉，主要網域它。一旦您知道所有移動的組件，以及最重要的位元，您也將知道什麼已 outgrown 和可以留下。該知識僅受益向前移。 
  
如此，使用者說關於在 SharePoint 伺服器陣列最重要？
  
- 內建的 SharePoint 功能
    
- 大型資料主體 （例如封存的檔案）
    
- 可用性
    
- 要徑應用程式、 網頁組件或伺服器陣列 （任務關鍵伺服器陣列） 中的文件
    
- 符合規範標準
    
- 自訂
    
如果要執行的基本業務 SharePoint 伺服器陣列中的某個項目，說它就像用戶端的服務需求的相關的重要資料的大型目錄，您可能會放入旁邊 '關鍵應用程式' 刻度但也就是 '可用性'-亦即您的業務如果您無法使用 SharePoint 一段的，影響。同樣地，您可能會檢查 '自訂' 因為緊急服務提供為基礎的自訂程式碼、 網站定義或數目可以搭配使用的自訂伺服器陣列。
  
如果 SharePoint 符合這些需求而不需要執行任何動作以外的地方使用內建軟體和通常其更新為與執行一般管理與維護、 您選擇 ' 內建 SharePoint'--也可能是您坐在舊版 SharePoint 的原因。換句話說，它已經沒有您需要它和尚未需要升級之前立即、 結尾 Microsoft Office SharePoint Server 2007 的支援。
  
當您項目符號清單您升級的欄位建立準則這些的事項。換句話說，升級程序必須符合必須考量此列。這可讓您能夠在規則出目前不符合您需求的方法。
  
### <a name="a-simple-sample-plan"></a>簡單範例計劃

那里可能會需要較多共識與領導與 SharePoint 升級所需的時間的路徑上其他系統管理員。SharePoint Server 管理員通常與 Microsoft SQL Server 系統管理員合作、 網路與安全性小組及其他與搭配使用。其中有許多的專案關係人，您可能需要建立協議，或調整您的升級與移轉的計劃。例如，如果使您公司的一部分使用 SharePoint Online 在 Office 365 中移轉資料，那里可能必須是效能調整或測試您的網路內。受影響的小組應該隨時通知。
  
在簡單的範例中，我顯示 SharePoint 管理員手冊提案]，然後列出所有專案關係人同意計劃。為避免混淆，文件協議和決策。
  
規劃伺服器陣列中的深入分析後啟動，嘗試找出在伺服器陣列、 設計師點及其他重要的資訊，將會導致某些升級選項關閉縮小角色。認知，升級提案進行 SharePoint 管理員與專案關係人同意動作計劃。
  
我 '最重要' 的項目符號清單：
  
- 可用性、 sharepoint、 內建的功能及規範標準。
    
- 大部分的資料為一個會議工作區及大量使用多個時區中特別重要的開發人員小組所使用全世界加上三個網站集合。
    
- 沒有十七廣泛使用其他網站。
    
- 兩個文件庫 （會議工作區和根網站集合的文件） 的最大 （超過 8000 文件每一個）。我們有大量的封存的文件和清單試算表附件。
    
- 有十四清單包含機密資料必須保持在最符合性中的文件庫。
    
- 我們必須能夠執行保留及電子探索儘我們移。
    
- 此資料的一些必須保持在最內部部署，因為常見規則。
    
 **「 我的升級與移轉的選項：**
  
|||
|:-----|:-----|
|**是** <br/> |**無** <br/> |
|附加資料庫以升級資料庫  <br/> |就地升級  <br/> |
|升級伺服器陣列的並行  <br/> |混合式升級  <br/> |
|移轉 API 至 Office 365 中的 SPO （適用於個人網站資料）  <br/> |SharePoint 混合式 （尚不需要）  <br/> |
|部分的手動資料移轉至 SharePoint Online 的重要資料。  <br/> |FastTrack 精靈] 升級至 Office 365  <br/> |
   
 **我提議的計劃：**
  
升級，以內部 SharePoint-並排，某些虛擬化，如此我們先升級資料庫的版本。從 SharePoint 2007 移至 [SharePoint 2010。系統管理員和適用於開發人員測試所產生的伺服器陣列。使用者測試所產生的伺服器陣列。在這段時間修正任何顯示停止問題。同樣地，並排顯示、 升級 SharePoint 2010 資料庫至 SharePoint 2013。Test 使用者測試/試驗。在這段時間修正任何顯示停止問題。
  
- 請考慮使用 SPO 搜尋同盟混合式是否符合您的需求。
    
- 如果您想要從這裡升級至 SharePoint Online，請考慮[FastTrack 尋求協助](https://fasttrack.microsoft.com)。 
    
- 決定任何網站集合是否可以卸載到 Office 365 訂閱。（office 365 符合許多[規範標準 （英文）](https://technet.microsoft.com/library/office-365-compliance.aspx)。Office 365 具有[eDiscovery](https://support.office.com/article/edea80d6-20a7-40fb-b8c4-5e8c8395f6da)往往可以透過規範中心的 [[保留](https://support.office.com/article/A18F8975-AA7F-43B4-A7D6-001D14744D8E)。） 
    
否則請繼續執行 SharePoint Server 2016 的並排顯示升級。
  
> [!NOTE]
> 規劃系統管理員所做的建議傳來的升級與實際的程序是發生與其他專案關係人在其升級依賴的交談。例如，有時經濟強制管理員變更其計劃。列傳的最終決策是，您應該記錄同意計劃的功能和向前移。它可能具有的外觀類似如下： 
  
 **我巨集指令的計劃：**
  
內部，我們用來建立預設 SharePoint Server 2010 與 2013年的虛擬環境。SharePoint Server 2016 會建立新的 2016年符合系統需求的硬體上。我們將會執行資料庫附加至資料庫從 SharePoint 2007 升級到它與 SharePoint Server 2016 之間的所有版本。核心自訂項目正在重新建立的及測試 SharePoint Server 中 2016年環境在此階段中，如果原生功能已不符合我們的需求。如果我們都成功，我們將會有已升級的資料庫，以在新硬體上的內部部署伺服器陣列及較少的自訂項目。我們將已升級內容資料庫附加至新的網站集合的 SharePoint Server 2013，測試、 使用者測試/試驗並再執行 DNS 剪下容錯移轉至新的 SharePoint Server 2016 環境 live 使用。
  
- 我們不會來說考量同盟混合式 SharePoint Server 2016 與 SharePoint Online 之間。
    
- 我們網站估計的 35%可轉換成與虛名網域的新 SPO 網站或者，最終，成為 OneDrive for Business 存放區。尋找其他需要在轉換的網站，或路由傳送給 o SPO 的新網站。
    
- 此部分的遷移的一些會手動-拖至 OneDrive for Business 的個人網站，並某些由移轉 API。
    
詳細步驟，或特定的升級指示要連結的數目應遵循計劃。MOSS 2007 電腦應該不會解除委任、 和虛擬環境應該維護這是因為比較;不過，將會完成升級時使用者重新導向至 SharePoint Server 2016。
  
選擇方法通常主要因素是升級的總成本和時間 （您會看到有更多 SharePoint 移轉藍圖文章中） 的成本。不過，規劃事先將在方面獲益您大幅設定期望、 選擇 [，和框架何種成功看起來。
  
## <a name="related-links"></a>相關連結

[可協助您升級從 Office 2007 的伺服器和用戶端的資源](upgrade-from-office-2007-servers-and-products.md)
  
[搜尋 Microsoft 技術支援週期原則和生命週期](https://support.microsoft.com/en-us/lifecycle)
  
[Microsoft 合作夥伴可以協助升級或移轉搜尋](https://partnercenter.microsoft.com/en-us/pcv/search)
  

