---
title: 從 SharePoint 2010 升級
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 2/2/2018
ms.audience: ITPro
ms.topic: conceptual
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- WSU140
- OSU140
ms.assetid: 985a357f-6db7-401f-bf7a-1bafdf1f312c
description: SharePoint 2010 與 SharePoint Server 2010 所接近支援結束。使用本文做指南升級為 SharePoint Online 或較新版的 SharePoint Server 的內部。
ms.openlocfilehash: c88c6010aa398d8076fce59976bf6f5c0aa1a743
ms.sourcegitcommit: a9c84d02e94c99ff6b1099b4a9ae695be08210e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2018
ms.locfileid: "21169865"
---
# <a name="upgrading-from-sharepoint-2010"></a>從 SharePoint 2010 升級

在 2020 Oct 13、 Microsoft Office SharePoint Server 2010 達到支援結束。本文詳細說明資源以協助其現有的 SharePoint Server 2010 資料移轉至 SharePoint Online、 或升級 SharePoint Server 內部的人員。
  
## <a name="what-is-end-of-support"></a>什麼是支援結束？

在 SharePoint Server 2010 與 SharePoint Foundation 2010 的軟體達到其支援生命週期 （Microsoft 提供的新功能、 修正錯誤、 安全性修正程式等等的期間的時間） 的結尾時這會呼叫該軟體 '支援結束'，或，有時，其 ' 退休 '。於產品支援 （或 EOS） 的結尾，則是 nothing 實際上關機或會停止運作;但軟體支援的結尾 Microsoft 不再提供：
  
- 技術支援問題，可能會發生;
    
- 錯誤修正的問題會發現及，可能會影響穩定性及可用性的伺服器;
    
- 安全性弱點的探索和可能會提出伺服器安全性缺口; 容易受到的修正
    
- 時間的時區更新。
    
也就是說，會有沒有進一步更新、 修補程式、 或修正項目將會傳送 （包括安全性修補程式修正程式） 的產品與 Microsoft 技術支援人員會有完全移位及其支援的努力較新版本。SharePoint Server 2010 的支援結束愈來愈您應利用機會修剪您不再需要升級、 產品及/或重要資料移轉前的資料。
  
> [!NOTE]
> 從產品的初始版本日期 10 年通常會持續軟體生命週期。您可以搜尋[Microsoft 合作夥伴](https://go.microsoft.com/fwlink/?linkid=841249)可協助您的軟體的下一版升級或 Office 365 遷移 （或兩者）。先確定您知道的結尾，以及要徑基礎技術支援日期特別您使用與 SharePoint 的 SQL server 的版本。 
  
## <a name="what-are-my-options"></a>我的選項為何？

首先，查看哪些支援兩端[產品生命週期網站](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202010)上的日期。接下來，請務必規劃升級或移轉知識的此日期與時間。請記住您產品*不會停止運作*當日列出與您可以繼續其使用，但是由於您的安裝不會再將該日期之後修補時，建議您將協助您更順暢地轉換到下一版的策略在產品。 
  
此矩陣可協助繪製課程而言移轉產品功能及使用者資料：
  
|**支援產品的結尾**|**良好**|**最佳**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013  <br/> |SharePoint Online  <br/> |
||SharePoint 混合式  <br/> |SharePoint Server、 2016、 （內部）  <br/> |
|||SharePoint 雲端混合式搜尋  <br/> |
   
如果您選擇在低的向外 （良好選項） 結尾的選項，您需要開始從 SharePoint Server 2010 的移轉完成後立即另一個升級計劃。（支援結束的 SharePoint Server 2010 與 SharePoint Foundation 2010 排定時間 2020 Oct 13，但是*請注意*您應一律檢查[產品生命週期網站](https://support.microsoft.com/en-us/lifecycle)最精準的日期 ！） 
  
## <a name="where-should-i-go-next"></a>其中應到下一步？

SharePoint Server 2013 和 SharePoint Foundation 2013 可安裝於內部您自己的伺服器上。否則，您可以使用 SharePoint Online，這是一種線上服務是 Microsoft Office 365 的一部分。您可以選擇：
  
- 移轉至 SharePoint Online
    
- 升級 SharePoint Server 或 SharePoint Foundation 內部部署
    
- 執行兩個以上
    
- 實作[SharePoint 混合式](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)解決方案 
    
請注意的隱藏成本相關聯維護伺服器陣列移往前，維護或移轉自訂和升級 SharePoint Server 所依存的硬體。如果您知道且已有所有這些，它會繼續升級內部部署的工作變得更容易。否則，如果您沒有頻繁自訂舊版的 SharePoint 伺服器上執行伺服器陣列，您無法特地列出計劃移轉至 SharePoint Online。它也有可能的內部部署 SharePoint Server 商店可能會選擇將部分資料放在 SharePoint Online 以減少量保持其資料內部部署涉及所有硬體管理。可能會更經濟將部分資料移至 SharePoint Online。
  
> [!NOTE]
> SharePoint 管理員可能會[建立 Office 365 訂閱](https://go.microsoft.com/fwlink/?linkid=843152)，請設定全新的 SharePoint Online 網站，並執行全新、 cut 從 SharePoint Server 2010、 僅限最重要的文件帶全新的 SharePoint Online 網站。如此，任何剩餘的資料可能會清空從 SharePoint Server 2010 網站將內部部署封存。 
  
|**SharePoint Online (SPO)**|**SharePoint Server 的內部**|
|:-----|:-----|
|高成本的時間 (計劃 / 執行 / 驗證)  <br/> |高成本的時間 (計劃 / 執行 / 驗證)  <br/> |
|資金 （沒有硬體購買） 中較低成本  <br/> |資金 （硬體購買） 中的較高成本  <br/> |
|在移轉一次性成本  <br/> |一次性成本重複每未來移轉  <br/> |
|低的整體擁有成本 / 維護  <br/> |高的整體擁有成本 / 維護  <br/> |
   
當您移轉至 Office 365 時、 一次性移動會有時間加重成本所花費的規劃、 先期 （雖然您正在將組織內的資料並決定要採用至雲端的項目以及留下的項目）。不過，一旦移轉資料時，升級會自動從這時看到當您不再需要管理的硬體和軟體更新，並且將會由 Microsoft 服務層級協議 ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)) 在備份伺服器陣列最多時間。
  
### <a name="migrate-to-sharepoint-online"></a>移轉至 SharePoint Online

請務必 SharePoint Online 提供您需要透過檢閱相關聯的服務描述的所有功能。以下是所有的 Office 365 服務說明連結：
  
[Office 365 服務說明](https://go.microsoft.com/fwlink/?linkid=272060)
  
目前沒有的方法所依據您可以直接從移轉 SharePoint Server 2010 （或 SharePoint Foundation 2010） 至 SharePoint Online，因此太多的工作是手動。這沒有提供您有機會封存和党資料與不再需要、 移動前的網站。您可以將儲存封存其他資料。另請記住未加入 SharePoint Server 2010 和 SharePoint Foundation 2010 會停止運作結尾的支援，讓系統管理員可以有一段的期間 SharePoint 仍在執行如果其客戶忘記移動一些自己的資料。
  
如果您升級為 SharePoint Server 2013 或 SharePoint Server 2016，並決定將資料放入 SharePoint Online 時，您移動也可能會涉及使用[SharePoint 移轉 API](https://support.office.com/en-us/article/Upload-on-premises-content-to-SharePoint-Online-using-PowerShell-cmdlets-555049c6-15ef-45a6-9a1f-a1ef673b867c?ui=en-US&amp;rs=en-US&amp;ad=US) （移轉至 OneDrive for Business 的資訊）。 
  
|**線上專業人員**|**線上詐騙**|
|:-----|:-----|
|Microsoft 提供給 SPO 硬體及所有硬體管理。  <br/> |可用的功能可能會不同 SharePoint Server 的內部和 SPO 之間。  <br/> |
|您在訂閱的全域管理員，且可能會指派 SPO 網站的管理員。  <br/> |部分可在 SharePoint Server 的內部伺服器陣列管理員動作不存在 （或不需要） Office 365 中，但 SharePoint 管理的 SharePoint 管理員角色、 網站集合管理] 和網站擁有權會以本機您的組織  <br/> |
|Microsoft 套用修補程式、 修正及更新為基礎的硬體和軟體 （包括在 SharePoint Online 執行 SQL 伺服器）。  <br/> |因為沒有存取權之服務中的基礎檔案系統，所以部分自訂功能會受到限制。  <br/> |
|Microsoft 發佈[服務等級協定](https://go.microsoft.com/fwlink/?linkid=843153)書寫快速解決服務層級事件。  <br/> |備份及還原及其他復原選項會自動在 SharePoint Online 服務-備份是以覆寫若不使用。  <br/> |
|安全性測試及伺服器效能調整會持續在服務中來執行 Microsoft。  <br/> |使用者介面和其他 SharePoint 功能所安裝的服務和切換開啟或關閉可能需要變更。  <br/> |
|Office 365 符合許多產業標準： [Office 365 規範](https://go.microsoft.com/fwlink/?linkid=843165)。  <br/> |僅限於[FastTrack](https://go.microsoft.com/fwlink/?linkid=518597)協助進行移轉。  <br/> 有多少升級將會是手動，或透過 SPO 移轉 API 所述的[SharePoint Online 和 OneDrive 移轉內容藍圖](https://go.microsoft.com/fwlink/?linkid=843184)。  <br/> |
|Microsoft 支援工程師和員工資料中心都有不受限制系統存取您的訂閱。  <br/> |如果需要升級以支援較新版的 SharePoint、 硬體基礎結構或次要伺服器陣列所需的升級，可以是其他的成本。  <br/> |
|協力廠商可協助進行資料移轉至 SharePoint Online 的單次工作。  <br/> |SharePoint Online 不是所有變更都會在控制項內。移轉之後，設計之間的差異功能表、 文件庫和其他功能可能會暫時影響和可用性。  <br/> |
|線上產品會自動更新跨表示功能可能會取代，雖然有支援生命週期沒有，則為 true 結束的服務。  <br/> |基礎 SQL 伺服器以及有支援生命週期的 SharePoint 伺服器 （或 SharePoint Foundation） 的結尾。  <br/> |
   
如果您已決定建立新的 Office 365 網站，並會以手動方式將資料移轉至其會視，您可以查看您的 Office 365 選項權限：
  
[Office 365 方案選項](https://go.microsoft.com/fwlink/?linkid=843151)
  
### <a name="upgrade-sharepoint-server-on-premises"></a>升級 SharePoint Server 的內部

為最新版本的 SharePoint 內部部署產品 (SharePoint Server 2016)、 SharePoint Server 升級必須*依序*移，這表示沒有以從 SharePoint Server 2010 升級至 SharePoint Server 2016、 直接方法。 
  
|||
|:-----|:-----|
||序列升級路徑 * * *： SharePoint Server 2010 **\>** SharePoint Server 2013 **\>** SharePoint Server 2016 |
   
如果您選擇所要遵循 SharePoint Server 2016 from SharePoint 2010 的整個路徑，這會花時間和規劃。升級涉及方面 （請注意也必須升級 SQL 伺服器） 的已升級的硬體、 軟體和管理成本。此外，自訂項目可能需要升級，或甚至是讓放棄不用。請確定您收集所有重大自訂項目上備忘稿才升級 SharePoint 伺服器陣列。
  
> [!NOTE]
> 可以維護您結尾支援 SharePoint 2010 伺服器陣列、 安裝 SharePoint Server 2016 伺服器陣列在新硬體上 （讓不同的伺服器陣列執行並排顯示），並再規劃及執行內容 （如下載並重新上傳內容、 手動移轉範例）。並潛在妥善給這些手動移動 （例如文件來自 2010年擁有別名為的帳戶執行手動移動目前的上次修改的帳戶），且必須隨時完成某些工作 (重新建立網站、 子網站的權限和清單結構）。是要考慮的資料您可以移到儲存或不再需要哪方面的良好時間。這可減少移轉的影響。無論如何，清除您環境前的升級。是您現有的伺服器陣列可正常運作升級之前和解除委任 （確定） 之前 ！ 
  
檢閱**支援及不支援的升級路徑**，請記得： 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
如果您有**自訂項目**，則十分重要計劃升級每個步驟中有移轉路徑： 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**內部專業人員**|**在內部詐騙**|
|:-----|:-----|
|從伺服器硬體的完整控制您的 SharePoint 伺服器陣列 （和它的 SQL） 的所有層面的設定。  <br/> |所有符號與修正項目都是貴公司的責任 （但您可以連絡付費的 Microsoft 支援人員如果您的產品不支援的結尾處）：  <br/> |
|SharePoint Server 的內部使用 [連線至 SharePoint Online 混合式透過訂閱的內部部署伺服器陣列] 選項的完整的功能集。  <br/> |升級、 修補程式、 安全性修正程式、 硬體升級及 SharePoint Server 及它的 SQL 伺服器陣列的所有維護是受管理的內部。  <br/> |
|大於自訂選項比使用 SharePoint Online 的完整存取。  <br/> |[規範標準支援的 Office 365](https://go.microsoft.com/fwlink/?linkid=843165)必須手動設定內部部署。  <br/> |
|安全性測試及伺服器效能調整實現您內部部署 （在您的控制項）。  <br/> |Office 365 可能會讓功能可供 SharePoint Online 的不能與 SharePoint Server 的內部互通  <br/> |
|協力廠商可協助進行移轉的 SharePoint Server （和超過） 的下一版的資料。  <br/> |SharePoint Server 網站不會自動使用[SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167)憑證視為是 SharePoint Online 中。  <br/> |
|命名慣例、 備份及還原 SharePoint Server 的內部其他復原選項的完全控制。  <br/> |SharePoint Server 的內部會受到產品生命週期。  <br/> |
   
### <a name="upgrade-resources"></a>升級的資源

開始進行比較的硬體及軟體的需求。如果您不符合目前的硬體上升級的基本需求，這代表必須先升級伺服器陣列或 SQL server 的硬體或您可能會決定將一些百分比您的網站移至 SharePoint online 的 '長青' 硬體。一旦您已進行您評估，請遵循支援的升級路徑及方法。
  
- **硬體/軟體需求**： 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)
    
- **軟體界限和限制**： 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)
    
- **的升級程序概觀**： 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-sharepoint-server-on-premises"></a>建立 SharePoint Online 和 SharePoint Server 內部部署之間的 SharePoint 混合式解決方案

（也可能是內部部署與線上世界一些移轉最佳的需求） 的另一個作法是混合式、 SharePoint Server 2013 或 2016年伺服器陣列連線至 SharePoint Online 建立 SharePoint 混合式：[了解 SharePoint 混合式解決方案](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).
  
如果您決定混合式 SharePoint 伺服器陣列已移轉的目標，請務必規劃網站及使用者應將 online 中，移至為何，這需要保留在內部。檢閱及 SharePoint 伺服器陣列的內容 （判斷哪些資料已為您的公司高、 Medium 或低影響） 的排名很有幫助至這個決策。可能需要共用與 SharePoint Online 的唯一項重點是 （a） 使用者帳戶的登入，並 （b） SharePoint Server 搜尋索引-可能不是純直到您查看您的網站的使用方式。如果您的公司稍後決定將所有內容移轉至 SharePoint Online，您可以將所有剩餘的帳戶和資料移動線上解除委任內部部署伺服器陣列，並/管理 SharePoint 伺服器陣列會透過 Office 365同時從該點上。
  
請務必先熟悉現有的混合式以及如何設定內部部署 SharePoint 伺服器陣列與您的 Office 365 訂閱之間的連線類型。
  
請參閱混合式 SharePoint 伺服器陣列的運作方式的其中一個好方法是建立[Office 365 開發人員/測試環境](https://go.microsoft.com/fwlink/?linkid=843152)。一旦您有試用版或購買 Office 365 訂閱，您必須在您的方式來建立網站集合、 web、 與文件庫的 SharePoint Online 可移轉資料 (其中一個手動，藉由使用移轉 API 或-如果您想要移轉我網站內容至 OneDrive for Business-透過混合精靈]）。
  
> [!NOTE]
> 請記得在 SharePoint Server 2010 伺服器陣列將首先需要升級，內部部署、 SharePoint Server 2013 或 SharePoint Server 2016 使用 [混合] 選項。SharePoint Foundation 2010 和 SharePoint Foundation 2013 無法建立與 SharePoint Online 的混合式連線。 
  
## <a name="related-topics"></a>相關主題

[可協助您升級從 Office 2007 或 2010年伺服器和用戶端的資源](upgrade-from-office-2010-servers-and-products.md)
  
[Overview of the upgrade process from SharePoint 2010 to SharePoint 2013](https://technet.microsoft.com/en-us/library/mt493301%28v=office.16%29.aspx)
  
[從 SharePoint 2010 升級至 SharePoint 2013 的最佳作法](https://technet.microsoft.com/en-us/library/mt493305%28v=office.16%29.aspx)
  
[在 SharePoint 2013 中針對資料庫的升級問題進行疑難排解](https://go.microsoft.com/fwlink/?linkid=843195)
  
[搜尋功能可協助升級 Microsoft 合作夥伴](https://go.microsoft.com/fwlink/?linkid=841249)
  
[已更新 SharePoint 2013 的產品服務原則](https://technet.microsoft.com/en-us/library/mt493253%28v=office.16%29.aspx)
  
[已更新 SharePoint Server 2016 的產品服務原則](https://technet.microsoft.com/en-us/library/mt782882%28v=office.16%29.aspx)
  

