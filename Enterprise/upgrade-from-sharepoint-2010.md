---
title: 從 SharePoint 2010 升級
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 04/13/2020
audience: ITPro
ms.topic: conceptual
ms.prod: office-online-server
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
search.appverid:
- MET150
- WSU140
- OSU140
ms.assetid: 985a357f-6db7-401f-bf7a-1bafdf1f312c
f1.keywords:
- NOCSH
description: 支援在2010年4月13日在 2021 SharePoint 和 SharePoint Server 2010 結束。 使用本文做為升級至 SharePoint 線上或更新版本 SharePoint 伺服器內部部署的指南。
ms.openlocfilehash: 8f55b55b84b2bd4d967822dea137a8cea4f40906
ms.sourcegitcommit: 27a04304475f9c33accd4c0498726f074eef7c48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "43532289"
---
# <a name="upgrading-from-sharepoint-2010"></a>從 SharePoint 2010 升級

*本文適用於 Office 365 企業版和 Microsoft 365 企業版。*

Microsoft SharePoint 2010 和 SharePoint Server 2010 會在**年4月 13 2021 日**到達支援的支援。 本文詳述可協助您將現有的 SharePoint Server 2010 資料移轉至 Office 365 中 SharePoint 線上的資源，或升級內部部署 SharePoint Server 2010 環境。
  
## <a name="what-is-end-of-support"></a>什麼是支援終止？

當您的 SharePoint Server 2010 和 SharePoint Foundation 2010 軟體達到其支援週期的結尾（Microsoft 提供新功能、bug 修正、安全性修正等）時，這稱為軟體的「支援終止」，或有時候是「退休」。 在產品的支援（或 EOS）結束時，實際上沒有任何實際關機或停止運作;不過，軟體支援結束時，Microsoft 不再提供：
  
- 可能發生之任何問題的技術支援；
    
- 所發現且可能會影響伺服器穩定性及可用性之問題的錯誤修正。
    
- 所發現且可能會讓伺服器容易受到安全性威脅之弱點的安全性修正。
    
- 時區更新。
    
這表示，將不會為產品（包括安全性修補程式/修正程式）提供進一步的更新、修補程式或修正程式，而且 Microsoft 支援人員已完全將其支援工作移至較新的版本。 在支援 SharePoint Server 2010 方法之後，您應該充分利用機會，以在升級產品及/或遷移重要資料之前，裁切您不再需要的資料。
  
> [!NOTE]
> 軟體生命週期一般會從產品的初始發行日期起10年。 您可以搜尋可協助升級至下一版軟體或搭配 Office 365 遷移（或兩者）的[Microsoft 解決方案供應商](https://go.microsoft.com/fwlink/?linkid=841249)。 請務必注意，您已知道重要基礎技術的支援日期，尤其是您用 SharePoint 所用的 SQL Server 版本。 請參閱[固定生命週期原則](https://support.microsoft.com/help/14085)，以瞭解產品生命週期的詳細資料。
  
## <a name="what-are-my-options"></a>我有哪些選擇？

首先，檢查[產品生命週期網站](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010)上的支援結束日期。 接下來，請務必在此日期的知識中規劃升級或遷移時間。 請記住，您的產品不會在列出的日期*停止運作*，而且您可以繼續使用，但由於在該日期之後將不再修補您的安裝，因此您將需要可協助您更順利轉換至產品的下一版本的策略。 
  
此矩陣可協助您在遷移產品功能和使用者資料時，繪製課程：
  
|**支援產品的結束**|**良好**|**最佳**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013 （內部部署）  <br/> |SharePoint Online  <br/> |
||SharePoint Server 2013 與 SharePoint 線上混合  <br/> |SharePoint Server 2016 （內部部署）  <br/> |
|||SharePoint 雲端混合式搜尋  <br/> |
   
如果您選擇規模低端的選項（良好的選項），您必須在從 SharePoint Server 2010 遷移完成之後，立即開始規劃另一個升級。 

您可以採取三個路徑，以避免 SharePoint Server 2010 的支援結束。

![SharePoint Server 2010 升級路徑](./media/upgrade-from-sharepoint-2010/upgrade-from-sharepoint-2010-paths.png)

>[!Note]
>SharePoint Server 2010 和 SharePoint Foundation 2010 的支援終止于4月13日的2021，但*請注意*，您應該時刻檢查[產品生命週期網站](https://support.microsoft.com/lifecycle)的最新日期。
>

  
## <a name="where-should-i-go-next"></a>下一步應該在哪裡？

SharePoint Server 2013 和 SharePoint Foundation 2013 可以在您自己的伺服器上安裝內部部署。 否則，您可以使用 SharePoint 線上，也就是 Microsoft Office 365 的一部分線上服務。 您可以選擇：
  
- 線上遷移至 SharePoint
    
- 升級 SharePoint Server 或 SharePoint Foundation 內部部署
    
- 進行上述兩種操作
    
- 實施[SharePoint 的混合](https://docs.microsoft.com/sharepoint/hybrid/hybrid)式解決方案 
    
請留意相關的隱藏成本，以維護伺服器陣列繼續進行、維護或遷移自訂專案，以及升級 SharePoint Server 所依賴的硬體。 如果您已意識到以上所有事項，則繼續升級內部部署會比較容易。 否則，如果您在舊版的 SharePoint 伺服器上執行伺服器陣列，但沒有大量自訂，您可以從規劃的遷移受益至線上 SharePoint。 您也可以在內部部署 SharePoint 伺服器環境中，將一些資料放在 SharePoint Online 中，以減少保留所有內部部署資料的硬體管理數量。 將一些資料移至 SharePoint 線上時可能更經濟。
  
> [!NOTE]
> SharePoint 系統管理員可以[建立 Office 365 訂閱](https://go.microsoft.com/fwlink/?linkid=843152)、設定全新 SharePoint Online 網站，然後完全從 SharePoint Server 2010 移離 Server （完全不只是將最基本的檔放到全新的 SharePoint 線上網站）。 從這裡開始，任何剩餘的資料都可能從 SharePoint Server 2010 網站耗盡為內部部署封存。 
  
|**SharePoint Online**|**SharePoint Server 內部部署**|
|:-----|:-----|
|高成本的時間（規劃/執行/驗證）  <br/> |高成本的時間（規劃/執行/驗證）  <br/> |
|更低的基金成本（未購買硬體）  <br/> |更高的基金成本（硬體購買）  <br/> |
|遷移時成本為一次  <br/> |每個未來遷移重複的單一時間成本  <br/> |
|低擁有權總成本/維護  <br/> |高擁有權總成本/維護  <br/> |
   
當您遷移至 Office 365 時，一次的移動會有較高的成本的時間花在規劃中（當您在組織資料時進行組織，並決定要對雲端採取的功能和留下的功能）。 不過，當您的資料移轉後，就會從該點自動進行升級，因為您不再需要管理軟硬體更新，所以您的伺服器陣列時間將會受到 Microsoft 服務等級協定（[SLA](https://go.microsoft.com/fwlink/?linkid=843153)）的支援。
  
### <a name="migrate-to-sharepoint-online"></a>線上遷移至 SharePoint

請確定 SharePoint 線上提供您所需的所有功能，方法是檢查其[服務描述](https://docs.microsoft.com/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-service-description)。
  
目前沒有一種方式可以直接從 SharePoint Server 2010 （或 SharePoint Foundation 2010）進行遷移，以 SharePoint 線上，所以許多工作是手動進行的。 這可讓您有機會在移動之前封存及修剪不再需要的資料和網站。 您可以將其他資料封存到儲存體。 另外請記住，SharePoint Server 2010 和 SharePoint Foundation 2010 都不會在支援結束時停止運作，所以管理員可以有一個句點，在此期間，如果客戶忘記移動某些資料，SharePoint 仍會執行。
  
如果您升級為 SharePoint Server 2013 或 SharePoint Server 2016，並決定將資料放入 SharePoint 線上，您的移動也可能會涉及使用[SharePoint 遷移 API](https://support.office.com/article/Upload-on-premises-content-to-SharePoint-Online-using-PowerShell-cmdlets-555049c6-15ef-45a6-9a1f-a1ef673b867c?ui=en-US&amp;rs=en-US&amp;ad=US) （將資訊遷移至 OneDrive for Business）。 
  
|**SharePoint 線上優勢**|**SharePoint 線上缺點**|
|:-----|:-----|
|Microsoft 提供 SPO 硬體和所有硬體管理。  <br/> |SharePoint Server 內部部署和 SPO 之間可用的功能可能會有所不同。  <br/> |
|您是訂閱的全域系統管理員，而且可能會指派管理員來 SPO 網站。  <br/> |在 Office 365 的「SharePoint 系統管理員」角色中，不會存在（或不需要）在 Office 的「系統管理員」角色中使用的部分動作（或不需要），但是 SharePoint 管理、網站集合管理及網站擁有權是您的組織當地的 SharePoint。  <br/> |
|Microsoft 會套用修補程式、修復和更新底層的硬體和軟體（包括 SharePoint 線上執行的 SQL server）。  <br/> |由於服務沒有存取基礎檔案系統，因此某些自訂專案有限。  <br/> |
|Microsoft 發佈[服務等級協定](https://go.microsoft.com/fwlink/?linkid=843153)，並快速移動以解決服務等級事件。  <br/> |備份與還原和其他修復選項會透過服務自動覆寫 SharePoint 線上備份會覆寫（如果不使用）。  <br/> |
|安全性測試和伺服器效能調整是由 Microsoft 在服務中持續執行。  <br/> |變更使用者介面及其他 SharePoint 功能會由服務安裝，而且可能需要切換開啟或關閉。  <br/> |
|Office 365 符合許多行業標準： [office 365 相容性](https://go.microsoft.com/fwlink/?linkid=843165)。  <br/> |遷移的[FastTrack](https://go.microsoft.com/fwlink/?linkid=518597)協助是有限的。  <br/> 大部分的升級是手動或透過[SharePoint 線上和 OneDrive 遷移內容藍圖](https://go.microsoft.com/fwlink/?linkid=843184)中所述的 SPO 遷移 API。  <br/> |
|Microsoft 支援工程師和資料中心內的員工都沒有無限制的系統管理員存取您的訂閱。  <br/> |若需要升級硬體基礎結構以支援較新版本的 SharePoint，或若升級需要次要伺服器陣列，可能會有額外的成本。  <br/> |
|解決方案供應商可以協助一次將您的資料移轉至 SharePoint 線上的工作。  <br/> |您的控制項內並未 SharePoint 線上的所有變更。 遷移後，功能表、文件庫和其他功能的設計差異可能會暫時影響可用性。  <br/> |
|線上產品會自動更新整個服務的意義，但功能可能會取代，而且不會有真正的支援生命週期的結束。  <br/> |SharePoint Server （或 SharePoint Foundation）和基礎 SQL server 的支援週期已結束。  <br/> |
   
如果您決定建立新的 Office 365 網站，並在需要時手動將資料移轉到它，您可以查看您的[Office 365 方案選項](https://go.microsoft.com/fwlink/?linkid=843151)。
  

  
### <a name="upgrade-sharepoint-server-on-premises"></a>升級 SharePoint 伺服器內部部署

從 SharePoint 的內部部署產品（SharePoint Server 2019）最新版本開始，SharePoint 伺服器升級必須*連續*進行，這表示您無法從 SharePoint server 2010 升級至 SharePoint Server 2016，也無法直接 SharePoint 2019。 
  
|||
|:-----|:-----|
||串列升級路徑 * * * *： SharePoint Server 2010 **\>** SharePoint server 2013 **\>** SharePoint server 2016 |
   
如果您選擇追蹤從 SharePoint 2010 到 SharePoint 伺服器2016的整個路徑，這將需要一些時間與進行規劃。 升級包含升級的硬體方面的成本（請注意，也就是必須升級的 SQL server）、軟體和管理。 此外，可能需要升級自訂專案，或甚至放棄自訂專案。 請務必先收集所有重要自訂專案的附注，再升級 SharePoint 伺服器陣列。
  
> [!NOTE]
> 您可以維持 SharePoint 2010 伺服器陣列的支援，在新的硬體上安裝 SharePoint 伺服器2016伺服器陣列（如此個別的伺服器陣列會並列執行），然後規劃並執行手動的內容遷移（例如，下載及重新上載內容）。 這些手動移動的潛在缺陷包括：來自2010的檔具有目前最後一個修改過的帳戶，且具有執行手動移動的帳號別名，而且某些工作必須提前完成（重新建立網站、子網站、許可權和清單結構）。 最好是考慮哪些資料可以移至儲存區，或不再需要。 這可減少遷移的影響。 無論是哪種方式，在升級之前先清理您的環境。 請務必確定您的現有伺服器陣列在您升級之前是正常運作的，在解除委任之前（確定）！ 
  
請記得查看**支援和不支援的升級路徑**： 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
如果您有**自訂**，請務必為遷移路徑中的每個步驟規劃升級： 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**內部部署優勢**|**內部部署缺點**|
|:-----|:-----|
|從伺服器硬體向上完全控制 SharePoint 伺服器陣列的所有層面（及其 SQL）。  <br/> |所有中斷和修正都是貴公司的責任（但是如果您的產品並非支援，您可以接洽付費的 Microsoft 支援服務）：  <br/> |
|SharePoint Server 內部部署的完整功能集合，具有透過混合方式將內部部署伺服器陣列連線至 SharePoint Online 訂閱的選項。  <br/> |升級、修補程式、安全性修正程式、硬體升級，以及 SharePoint 伺服器的所有維護，而且其 SQL 伺服器陣列都是在內部部署管理。  <br/> |
|自訂選項的完整存取權，與 SharePoint 線上的功能更高。  <br/> |[Office 365 支援的相容性標準](https://go.microsoft.com/fwlink/?linkid=843165)必須手動設定內部部署。  <br/> |
|在您的內部部署（在您的控制之下）進行安全性測試和伺服器效能調整。  <br/> |Office 365 可能使 SharePoint 線上使用的功能，無法與內部部署 SharePoint 伺服器互動  <br/> |
|解決方案供應商可以協助將資料移轉至下一版的 SharePoint Server （和之後）。  <br/> |您的 SharePoint 伺服器網站不會自動使用 SharePoint Online 中所看到[SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167)憑證。  <br/> |
|在內部部署中 SharePoint Server 內部部署命名慣例、備份與還原及其他復原選項的完整控制權。  <br/> |SharePoint Server 內部部署對產品生命週期保密。  <br/> |
   
### <a name="upgrade-resources"></a>升級資源

請先比較硬體和軟體需求。 如果您在目前的硬體上沒有符合升級的基本需求，這可能表示您必須先升級伺服器陣列或 SQL server 中的硬體，否則您可能會決定將部分的網站移至 SharePoint 線上的「長綠」硬體。 進行評估之後，請遵循支援的升級路徑和方法。
  
- **硬體/軟體需求**： 
    
    [SharePoint server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [SharePoint server 2016](https://go.microsoft.com/fwlink/?linkid=843207)
    
- **軟體界限和限制**： 
    
    [SharePoint server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [SharePoint server 2016](https://go.microsoft.com/fwlink/?linkid=843249)
    
- 下列專案**的升級程式概述**： 
    
    [SharePoint server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [SharePoint server 2016](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-sharepoint-server-on-premises"></a>在 SharePoint 線上和 SharePoint 伺服器內部部署之間建立 SharePoint 的混合式解決方案

另一個選項（可能是內部部署和線上世界的最佳作法）是混合式，您可以將 SharePoint Server 2013 或2016或2019伺服器陣列連線至 SharePoint 線上，以建立 SharePoint 混合式：[瞭解 SharePoint 的混合式解決方案](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)。
  
如果您決定混合式 SharePoint 伺服器陣列是您的遷移目標，請務必規劃應該在線上中移動的網站和使用者，以及必須保留內部部署的網站和使用者。 檢查和排名您的 SharePoint 伺服器陣列內容（決定貴公司的高、中或低影響的資料）可能有助於作出這項決策。 您可能需要與 SharePoint 線上共用的唯一一件事是（a）使用者帳戶用於登入，（b） SharePoint 伺服器搜尋索引--在您查看網站的使用方式之前，這可能不是必須明確的。 如果您的公司後來決定將您的所有內容遷移至 SharePoint 線上，您可以將所有剩餘的帳戶和資料線上移動，並解除委任您的內部部署伺服器陣列，而且 SharePoint 伺服器陣列的管理/管理將透過從該點開始的 Office 365 主控台進行。
  
請務必熟悉現有的混合式類型，以及如何設定內部部署 SharePoint 伺服器陣列與 Office 365 訂閱之間的連線。
  
若要查看混合式 SharePoint 伺服器陣列如何運作，一種很好的方式是建立[Office 365 開發/測試環境](https://go.microsoft.com/fwlink/?linkid=843152)。 當您有試用版或已購買的 Office 365 訂閱後，您就可以在 SharePoint Online 中建立網站集合、網站及文件庫，以供您遷移資料（手動、利用遷移 API）或-如果您想要透過混合式嚮導將「我的網站」內容遷移至 OneDrive。
  
> [!NOTE]
> 請記住，您的 SharePoint 伺服器2010伺服器陣列即將第一次升級、內部部署，以 SharePoint 伺服器2013或 SharePoint Server 2016，以使用 [混合] 選項。 SharePoint Foundation 2010 和 SharePoint Foundation 2013 無法建立與 SharePoint 線上的混合連接。 

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>適用於 Office 2010 用戶端與伺服器和 Windows 7 的選項摘要

如需適用於 Office 2010 用戶端與伺服器和 Windows 7 的升級、移轉和移至雲端選項的視覺摘要，請參閱[終止支援海報](./media/upgrade-from-office-2010-servers-and-products/Office2010Windows7EndOfSupport.pdf)。

[![Office 2010 用戶端與伺服器和 Windows 7 終止支援海報的影像](./media/upgrade-from-office-2010-servers-and-products/office2010-windows7-end-of-support.png)](./media/upgrade-from-office-2010-servers-and-products/Office2010Windows7EndOfSupport.pdf)

這張單頁海報可讓您快速了解可以採取的各種方法，以防止Office 2010 用戶端與伺服器產品以及 Windows 7 進入終止支援，而海報上也會強調顯示 Microsoft 365 企業版中慣用的方式和選項支援。

您可以[下載](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/migration-microsoft-365-enterprise-workload/Office2010Windows7EndOfSupport.pdf)此海報，並以 Letter、Legal 或 Tabloid (11 x 17) 格式列印此海報。
        
## <a name="related-topics"></a>相關主題

[協助您從 Office 2007 或2010伺服器及用戶端升級的資源](upgrade-from-office-2010-servers-and-products.md)
  
[Overview of the upgrade process from SharePoint 2010 to SharePoint 2013](https://technet.microsoft.com/library/mt493301%28v=office.16%29.aspx)
  
[從 SharePoint 2010 升級至 SharePoint 2013 的最佳作法](https://technet.microsoft.com/library/mt493305%28v=office.16%29.aspx)
  
[在 SharePoint 2013 中針對資料庫的升級問題進行疑難排解](https://go.microsoft.com/fwlink/?linkid=843195)
  
[搜尋 Microsoft 解決方案供應商以協助您升級](https://go.microsoft.com/fwlink/?linkid=841249)
  
[已更新 SharePoint 2013 的產品服務原則](https://technet.microsoft.com/library/mt493253%28v=office.16%29.aspx)
  
[已更新 SharePoint Server 2016 的產品服務原則](https://technet.microsoft.com/library/mt782882%28v=office.16%29.aspx)
  

