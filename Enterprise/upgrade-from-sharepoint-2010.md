---
title: 從 SharePoint 2010 升級
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 06/04/2019
audience: ITPro
ms.topic: conceptual
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- WSU140
- OSU140
ms.assetid: 985a357f-6db7-401f-bf7a-1bafdf1f312c
description: SharePoint 2010 和 SharePoint Server 2010 的支援端點會于2020年10月13日結束。 使用本文作為升級至 SharePoint Online 或更新版本 SharePoint Server 內部部署的指南。
ms.openlocfilehash: d2114baf03d19c6be818139a08ed93ff3b64f664
ms.sourcegitcommit: b4c82c0bf61f50386e534ad23479b5cf84f4e2ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2019
ms.locfileid: "35203612"
---
# <a name="upgrading-from-sharepoint-2010"></a>從 SharePoint 2010 升級

Microsoft SharePoint 2010 和 SharePoint Server 2010 將在**年10月 13 2020 日**到達支援的結尾。 本文詳細說明可協助您將現有的 SharePoint Server 2010 資料移轉至 Office 365 中的 SharePoint Online 的資源, 或升級您的內部部署 SharePoint Server 2010 環境。
  
## <a name="what-is-end-of-support"></a>什麼是支援結束？

當您的 SharePoint Server 2010 和 SharePoint Foundation 2010 軟體達到其支援生命週期的結尾 (Microsoft 提供新功能的時間、錯誤修正程式、安全性修正程式等等), 這稱為軟體的「支援結束」, 或有時是它的「退休」。 在產品的支援 (或 EOS) 結束時, 什麼不會真正關閉或停止運作;不過, 在軟體支援的結尾, Microsoft 不再提供:
  
- 可能發生的問題的技術支援;
    
- 針對探索的問題修正, 以及可能會影響伺服器穩定性和可用性的錯誤修正程式。
    
- 受到探索的安全修補程式, 可能會使伺服器受到安全性違規的影響;
    
- 時區更新。
    
也就是說, 產品 (包括安全性修補程式/修補程式) 將不會隨附任何進一步的更新、修補程式或修正程式, 而且 Microsoft 支援人員會將其支援工作完全移至較新的版本。 在 SharePoint Server 2010 方法的支援結束時, 您應該在升級產品之前, 充分利用機會來裁切您不再需要的資料, 以及/或遷移您的重要資料。
  
> [!NOTE]
> 軟體生命週期通常是從產品初始發行的日期起10年。 您可以搜尋可協助升級至下一版軟體的[Microsoft 解決方案提供者](https://go.microsoft.com/fwlink/?linkid=841249), 或使用 Office 365 遷移 (或兩者)。 請務必注意, 在重要基礎技術上的支援日期結束, 尤其是您在 SharePoint 中使用的 SQL Server 版本。 
  
## <a name="what-are-my-options"></a>我的選項是什麼？

首先, 檢查[產品生命週期網站](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202010)上的支援結束日期。 下一步, 請務必使用此日期的知識來規劃升級或遷移時間。 請記住, 您的產品將不會在列出的日期*停止運作*, 但您可以繼續使用, 因為在該日期之後將不會再修補您的安裝, 您會想要一種可協助您更順利轉換至下一個版本的策略。產品。 
  
此矩陣會在遷移產品功能和使用者資料時, 協助繪製課程:
  
|**支援產品結束**|**良好**|**最佳**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013 (內部部署)  <br/> |SharePoint Online  <br/> |
||SharePoint Server 2013 與 SharePoint Online 混合  <br/> |SharePoint Server 2016 (內部部署)  <br/> |
|||SharePoint Cloud 混合式搜尋  <br/> |
   
如果您選擇規模低端的選項 (良好的選項), 您必須在從 SharePoint Server 2010 完成遷移後, 立即開始規劃其他升級。 

>[!Note]
>SharePoint Server 2010 和 SharePoint Foundation 2010 的支援工作已排程于 Oct 13, 2020, 但*請注意*, 您應該隨時檢查[產品生命週期網站](https://support.microsoft.com/en-us/lifecycle)的最新日期。
>


 
  
## <a name="where-should-i-go-next"></a>下一步應該到哪裡？

SharePoint Server 2013 和 SharePoint Foundation 2013 可以安裝在您自己的伺服器上內部部署。 否則, 您可以使用 SharePoint Online, 這是 Microsoft Office 365 的一部分線上服務。 您可以選擇:
  
- 遷移至 SharePoint Online
    
- 升級 SharePoint Server 或 SharePoint Foundation 內部部署
    
- 執行上述兩項作業
    
- 實施[SharePoint 混合](https://docs.microsoft.com/sharepoint/hybrid/hybrid)式解決方案 
    
請注意與維護伺服器陣列有關的隱藏成本, 以繼續、維護或遷移自訂專案, 以及升級 SharePoint Server 所需的硬體。 如果您知道並已考慮所有這些, 則繼續升級內部部署會比較容易。 否則, 如果您在舊版的 SharePoint 伺服器上執行伺服器陣列, 而不需要大量自訂, 您可以從規劃遷移到 SharePoint Online 中獲益。 此外, 在您的內部部署 SharePoint Server 環境中, 您可能會選擇將某些資料放在 SharePoint Online 中, 以減少硬體管理的數量, 讓您的所有資料可供內部部署所涉及。 將部分資料移至 SharePoint Online 可能會比較經濟。
  
> [!NOTE]
> SharePoint 系統管理員可以[建立 Office 365 訂閱](https://go.microsoft.com/fwlink/?linkid=843152)、設定全新的 sharepoint Online 網站, 然後從 SharePoint Server 2010 完全剪下, 僅將最重要的檔移至新的 SharePoint online 網站。 從這裡開始, 任何剩餘的資料可能會從 SharePoint Server 2010 網站耗盡到內部部署封存。 
  
|**SharePoint Online**|**SharePoint Server 內部部署**|
|:-----|:-----|
|高成本的時間 (規劃/執行/驗證)  <br/> |高成本的時間 (規劃/執行/驗證)  <br/> |
|更低的基金成本 (不購買硬體)  <br/> |更高的基金成本 (硬體購買)  <br/> |
|遷移的一次成本  <br/> |每個未來遷移重複的一次成本  <br/> |
|低擁有權總成本/維護  <br/> |高擁有權/維護的整體擁有成本  <br/> |
   
當您遷移到 Office 365 時, 一次性移動會有較長的時間花在規劃、上一次 (當您正在組織資料時, 決定要對雲端進行的內容, 以及留下的內容)。 不過, 一旦遷移資料, 就會從該點自動進行升級, 因為您將不再需要管理軟硬體和軟體更新, 而且您的伺服器陣列將會受到 Microsoft 服務等級協定 ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)) 的支援。
  
### <a name="migrate-to-sharepoint-online"></a>遷移至 SharePoint Online

請確定 SharePoint Online 透過您的[服務說明](https://docs.microsoft.com/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-service-description)來提供您所需的所有功能。
  
目前沒有一種方法可以直接從 SharePoint Server 2010 (或 SharePoint Foundation 2010) 遷移至 SharePoint Online, 因此大部分工作是手動的。 這可讓您有機會在移動之前封存和修剪不再需要的資料和網站。 您可以將其他資料封存到儲存區。 此外, 請記住, SharePoint Server 2010 和 SharePoint Foundation 2010 都不會在支援結束時停止運作, 因此系統管理員可能會有一段時間, 在此期間, 如果客戶忘記移動部分資料, SharePoint 仍會繼續執行。
  
如果您升級至 SharePoint Server 2013 或 SharePoint Server 2016, 並決定將資料放入 SharePoint Online, 您的移動也可能涉及使用[SharePoint 遷移 API](https://support.office.com/en-us/article/Upload-on-premises-content-to-SharePoint-Online-using-PowerShell-cmdlets-555049c6-15ef-45a6-9a1f-a1ef673b867c?ui=en-US&amp;rs=en-US&amp;ad=US) (將資訊遷移到商務用 OneDrive 中)。 
  
|**SharePoint Online 優勢**|**SharePoint Online 的缺點**|
|:-----|:-----|
|Microsoft 提供 SPO 硬體和所有硬體管理。  <br/> |SharePoint Server 內部部署和 SPO 中可用的功能可能會有所不同。  <br/> |
|您是訂閱的全域系統管理員, 而且可能會將管理員指派給 SPO 網站。  <br/> |在 SharePoint Server 內部部署中, 伺服器陣列管理員可以使用的某些動作, 在 Office 365 的 SharePoint 系統管理員角色中不存在 (或不需要), 但 SharePoint 管理、網站集合管理及網站擁有權是本機的您的組織。  <br/> |
|Microsoft 會套用修補程式、修補程式及更新至基本硬體和軟體 (包括 SharePoint Online 執行所在的 SQL server)。  <br/> |因為在服務中無法存取基礎檔案系統, 部分自訂專案會受到限制。  <br/> |
|Microsoft 發佈[服務等級協定](https://go.microsoft.com/fwlink/?linkid=843153), 並快速移動以解決服務等級事件。  <br/> |備份與還原及其他復原選項會由 SharePoint Online 中的服務自動進行, 如果不使用, 則會覆寫備份。  <br/> |
|安全性測試和伺服器效能調整是在 Microsoft 的服務中持續執行。  <br/> |使用者介面和其他 SharePoint 功能的變更會由服務安裝, 而且可能需要開啟或關閉。  <br/> |
|Office 365 符合許多行業標準: [office 365 合規性](https://go.microsoft.com/fwlink/?linkid=843165)。  <br/> |[FastTrack](https://go.microsoft.com/fwlink/?linkid=518597)的遷移協助是有限的。  <br/> 大部分的升級都是手動, 或是透過[SharePoint Online 和 OneDrive 遷移內容藍圖](https://go.microsoft.com/fwlink/?linkid=843184)中說明的 SPO 遷移 API 進行。  <br/> |
|Microsoft 支援工程師和資料中心的員工都沒有對您訂閱的無限制的系統管理員存取權。  <br/> |如果需要升級硬體基礎結構以支援較新版本的 SharePoint, 或若升級需要次要伺服器陣列, 可能會有額外的成本。  <br/> |
|解決方案提供者可以協助您將資料移轉至 SharePoint Online 的單一時間工作。  <br/> |並非所有對 SharePoint Online 的變更都在您的控制項內。 遷移之後, 功能表、文件庫及其他功能的設計差異可能會暫時影響可用性。  <br/> |
|線上產品會自動更新服務的意義表示, 雖然功能可能取代, 但並沒有真正的支援週期。  <br/> |SharePoint Server (或 SharePoint Foundation) 和基礎 SQL server 都有支援週期的結尾。  <br/> |
   
如果您決定建立新的 Office 365 網站, 並將資料手動遷移至所需的位置, 您可以查看您的[Office 365 方案選項](https://go.microsoft.com/fwlink/?linkid=843151)。
  

  
### <a name="upgrade-sharepoint-server-on-premises"></a>升級 SharePoint Server 內部部署

從最新版的 SharePoint 內部部署產品 (SharePoint Server 2016) 開始, SharePoint Server 升級必須*串列*, 這表示無法直接從 sharepoint server 2010 升級至 sharepoint server 2016。 
  
|||
|:-----|:-----|
||串列升級路徑 * * * *: SharePoint Server 2010 **\>** sharepoint server 2013 **\>** sharepoint server 2016 |
   
如果您選擇遵循從 SharePoint 2010 到 SharePoint Server 2016 的完整路徑, 將需要一些時間並進行規劃。 升級涉及升級硬體的成本 (請注意, SQL server 也必須升級)、軟體及管理。 此外, 自訂專案也可能需要升級, 甚至會被放棄。 升級 SharePoint Server 伺服器陣列之前, 請確定您已在所有重要自訂專案上收集記事。
  
> [!NOTE]
> 您可以維護 SharePoint 2010 伺服器陣列的結尾, 在新的硬體上安裝 SharePoint Server 2016 伺服器陣列 (讓個別的伺服器陣列並存執行), 然後規劃及執行內容的手動遷移 (以下載和重新載入內容)。範例)。 這些手動移動有可能的缺陷 (例如, 來自2010的檔具有執行手動移動之帳戶的目前最後修改過的帳戶), 且某些工作必須提前完成 (重新建立網站、子網站、許可權和清單結構)。 請考慮您可以移至儲存區的資料, 或不再需要的時間。 這會降低遷移的影響。 無論是哪一種方式, 在升級前請清理環境。 請確定您的現有伺服器陣列在您升級之前都能正常運作, 並在您解除委任之前 (確認)! 
  
請記得查看**支援與不支援的升級路徑**: 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
如果您有**自訂**, 請務必為遷移路徑中的每個步驟規劃升級: 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**內部部署優勢**|**內部部署劣勢**|
|:-----|:-----|
|從伺服器硬體完全控制 SharePoint 伺服器陣列的所有層面 (及其 SQL)。  <br/> |所有中斷和修正都是貴公司的責任 (但是, 如果您的產品不受支援, 您可以接洽付費的 Microsoft 支援):  <br/> |
|SharePoint Server 內部部署的完整功能集, 具有透過混合將內部部署伺服器陣列連線至 SharePoint Online 訂閱的選項。  <br/> |升級、修補程式、安全性修正程式、硬體升級, 以及 SharePoint Server 的所有維護, 且其 SQL 伺服器陣列是在內部部署管理。  <br/> |
|與 SharePoint Online 更高的自訂選項的完整存取權。  <br/> |[Office 365 支援的規範標準](https://go.microsoft.com/fwlink/?linkid=843165)必須手動設定內部部署。  <br/> |
|安全性測試和伺服器效能調整, 會在您的內部部署 (在您的控制項之下) 執行。  <br/> |Office 365 可能會讓 SharePoint Online 無法與 SharePoint Server 內部部署交互操作的功能。  <br/> |
|解決方案提供者可協助將資料移轉至下一版的 SharePoint Server (和之後)。  <br/> |您的 SharePoint Server 網站不會自動使用[SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167)憑證, 如 sharepoint Online 中所示。  <br/> |
|在 SharePoint Server 內部部署中, 完全控制命名慣例、備份及還原以及其他復原選項。  <br/> |SharePoint Server 內部部署對產品生命週期而言是敏感的。  <br/> |
   
### <a name="upgrade-resources"></a>升級資源

請先比較硬體與軟體需求。 如果您不符合目前硬體上升級的基本需求, 可能表示您必須先升級伺服器陣列或 SQL server 中的硬體, 或決定將部分網站的一部分移動至 SharePoint Online 的「長綠」硬體。 進行評估之後, 請遵循支援的升級路徑和方法。
  
- **硬體/軟體需求**: 
    
    [Sharepoint server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [sharepoint server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [sharepoint server 2016](https://go.microsoft.com/fwlink/?linkid=843207)
    
- **軟體界限及限制**: 
    
    [Sharepoint server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [sharepoint server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [sharepoint server 2016](https://go.microsoft.com/fwlink/?linkid=843249)
    
- **升級程式概述**: 
    
    [Sharepoint server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [sharepoint server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [sharepoint server 2016](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-sharepoint-server-on-premises"></a>在 SharePoint Online 與 SharePoint Server 內部部署之間建立 SharePoint 混合式解決方案

另一個選項 (可能是內部部署和線上世界的最優秀) 是一種混合式, 您可以將 SharePoint Server 2013 或2016伺服器陣列連線至 SharePoint Online, 以建立 SharePoint 混合式:[瞭解 sharepoint 混合式解決方案](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).
  
如果您決定混合式 SharePoint Server 伺服器陣列是您的遷移目標, 請務必規劃應該移至線上的網站和使用者, 以及需要保留內部部署的使用者。 對您的 SharePoint Server 伺服器陣列內容進行檢查和排名, 以判斷哪些資料對貴公司的高、中或低影響很有説明。 您可能會想要與 SharePoint Online 共用的唯一事情是 (a) 使用者帳戶進行登入, 以及 (b) SharePoint Server 搜尋索引--在您查看網站的使用方式之前, 可能不會清楚。 如果您的公司稍後決定要將所有內容遷移至 SharePoint Online, 您可以移動所有剩餘的帳戶和資料, 並解除委任您的內部部署伺服器陣列, 而且 SharePoint 伺服器陣列的管理/管理將透過 Office 365 完成來自該點的主控台。
  
請務必熟悉現有的混合式類型, 以及如何設定您的內部部署 SharePoint 伺服器陣列與 Office 365 訂閱之間的連線。
  
透過建立[Office 365 開發/測試環境](https://go.microsoft.com/fwlink/?linkid=843152), 查看混合式 SharePoint 伺服器陣列運作方式的一種好方法。 一旦您擁有試用版或購買的 Office 365 訂閱, 您就可以在 SharePoint Online 中建立網站集合、網站和文件庫, 以供您遷移資料 (手動、使用遷移 API), 或-如果您想要遷移我的商務用 OneDrive 的網站內容-透過混合式嚮導)。
  
> [!NOTE]
> 請記住, 您的 SharePoint Server 2010 伺服器陣列必須先升級、內部部署、SharePoint Server 2013 或 SharePoint Server 2016, 才能使用 [混合] 選項。 SharePoint Foundation 2010 和 SharePoint Foundation 2013 無法建立與 SharePoint Online 的混合連線。 
  
## <a name="related-topics"></a>相關主題

[可協助您從 Office 2007 或2010伺服器和用戶端升級的資源](upgrade-from-office-2010-servers-and-products.md)
  
[Overview of the upgrade process from SharePoint 2010 to SharePoint 2013](https://technet.microsoft.com/en-us/library/mt493301%28v=office.16%29.aspx)
  
[從 SharePoint 2010 升級至 SharePoint 2013 的最佳作法](https://technet.microsoft.com/en-us/library/mt493305%28v=office.16%29.aspx)
  
[在 SharePoint 2013 中針對資料庫的升級問題進行疑難排解](https://go.microsoft.com/fwlink/?linkid=843195)
  
[搜尋 Microsoft 解決方案提供者以協助您升級](https://go.microsoft.com/fwlink/?linkid=841249)
  
[已更新 SharePoint 2013 的產品服務原則](https://technet.microsoft.com/en-us/library/mt493253%28v=office.16%29.aspx)
  
[已更新 SharePoint Server 2016 的產品服務原則](https://technet.microsoft.com/en-us/library/mt782882%28v=office.16%29.aspx)
  

