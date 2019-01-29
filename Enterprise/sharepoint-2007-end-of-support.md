---
title: SharePoint Server 2007 終止支援藍圖
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 01/28/2019
ms.audience: ITPro
ms.topic: conceptual
f1_keywords:
- vsemail
- MS_WSS_DirectoryManagement
- MS_WSS_ConfigEmail
- globalemailconfig
- configssc
- AppDefToBDC
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- OFU120
- SPS150
- OSU140
- WSU120
- OSR120
- SPO160
- PJW120
- SPB160
- OSI150
- OSI160
- BSA160
- OSU160
ms.assetid: ba124775-d5c0-4d68-b88d-8458ad4c3717
description: 在 2017 年 10 月 10、 支援的結束 for SharePoint Server 2007。閱讀本文以了解您的升級選項、 疑難排解、 最佳作法、 系統需求、 升級步驟及如何從 Microsoft 協力廠商取得協助。
ms.openlocfilehash: b0d3eda690733b45ee82054e145642a5c76125d5
ms.sourcegitcommit: 792fe2ccc860517fe3dcbc9c668bae97f39ae7c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2019
ms.locfileid: "29604514"
---
# <a name="sharepoint-server-2007-end-of-support-roadmap"></a>SharePoint Server 2007 終止支援藍圖

**2017 年 10 月 10，**，在 Microsoft Office SharePoint Server 2007 達到支援結束。如果您尚未開始從 SharePoint Server 2007 移轉至 Office 365 或較新版本的 SharePoint Server 的內部，現在是以開始規劃的時間。本文詳細說明可協助人員將資料移轉至 SharePoint Online、 或升級 SharePoint Server 內部的資源。 
  
## <a name="what-does-end-of-support-mean"></a>支援平均數何種實務結尾？

SharePoint Server 幾乎所有的 Microsoft 產品，例如有支援週期的期間 Microsoft 提供的新功能、 修正錯誤、 安全性修正程式等等。此技術支援週期通常是一個工期 10 年度從產品的初始版本，日期的此技術支援週期的結尾就所謂的產品支援結束。支援的結尾，Microsoft 不再提供：
  
- 技術支援問題，可能會發生;
    
- 錯誤修正的問題會發現及，可能會影響穩定性及可用性的伺服器;
    
- 安全性弱點的探索和可能會提出伺服器安全性缺口; 容易受到的修正與 
    
- 時間的時區更新。
    
不過您的 SharePoint Server 2007 伺服器陣列仍能運作後年 10 月 10，2017，沒有進一步更新、 修補程式、 或修正項目將會傳送 （包括安全性修補程式修正程式） 的產品與 Microsoft 技術支援人員會完全移位及其支援致力於較新版的產品。因為您的安裝將不再支援或修補時，做為結尾的支援方法您應該升級、 產品或移轉重要資料。
  
> [!TIP]
> 如果您已經尚未升級或移轉計劃，請參閱： [SharePoint 2007 要考慮的移轉選項](sharepoint-2007-migration-options.md)，以開始的所在位置的一些範例。您也可以搜尋適用於[Microsoft 合作夥伴](https://go.microsoft.com/fwlink/?linkid=841249)可以協助升級或 Office 365 遷移 （或兩者）。 
  
如需即將達到支援結束的 Office 2007 伺服器的詳細資訊，請參閱[資源以協助您升級從 Office 2007 的伺服器和用戶端](upgrade-from-office-2007-servers-and-products.md)。
  
## <a name="what-are-my-options"></a>我的選項為何？

在第一個停駐點應[產品生命週期網站](https://go.microsoft.com/fwlink/?linkid=843148)。如果您有已過時的內部部署 Microsoft 產品，就應該檢查其結尾支援日期的因此，一年或賣出層或只要您移轉通常需要-您可以排程升級或移轉。當選擇 [下一步，它可協助認為就會是很好足夠、 搭配成效更佳、 以及最佳而言產品功能。以下是範例：
  
|**良好**|**更好**|**最佳**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013  <br/> |SharePoint Online  <br/> |
||SharePoint 混合式  <br/> |SharePoint Server 2016  <br/> |
|||SharePoint 混合式  <br/> |
   
如果您選擇低結尾 （良好足夠） 刻度的選項，請記得才能開始規劃升級非常推出從 SharePoint Server 2007 的移轉後已完成。（SharePoint Server 2007 結束是支援的 2017 年 10 月 10。請注意下列日期如有變更恕並檢查[產品生命週期網站](https://support.microsoft.com/en-us/lifecycle)）。
  
## <a name="where-can-i-go-next"></a>我移出下一步？

SharePoint Server 可以是安裝於內部您自己的伺服器上也可以使用 SharePoint Online，這是一種線上服務是 Microsoft Office 365 的一部分。您可以選擇：
  
- 移轉至 SharePoint Online
    
- 升級 SharePoint Server 的內部
    
- 執行兩個以上
    
- 實作[SharePoint 混合式](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)解決方案 
    
請注意的隱藏成本相關聯維護伺服器陣列移往前，維護或移轉自訂和升級 SharePoint Server 所依存的硬體。具有內部部署 SharePoint 伺服器陣列棒嗎如果它是必要性;否則，如果您沒有頻繁自訂舊版 SharePoint 伺服器上執行伺服器陣列您可以特地列出計劃移轉至 SharePoint Online。
  
> [!IMPORTANT]
> 如果不常使用 SharePoint 2007 中的內容，有另一個選項。某些 SharePoint 管理員可以選擇[建立 Office 365 訂閱](https://go.microsoft.com/fwlink/?linkid=843152)，設定全新的 SharePoint Online 網站，並執行全新、 cut 從 SharePoint 2007、 僅限最重要的文件帶全新的 SharePoint Online 網站。從該處、 資料可能會清空從 SharePoint 2007 網站將封存。授與使用者的運作方式與資料 SharePoint 2007 安裝的思考。可能會有小小寫的方式來解決這個問題 ！ 
  
|**SharePoint Online (SPO)**|**SharePoint Server 的內部**|
|:-----|:-----|
|高成本的時間 (計劃 / 執行 / 驗證)  <br/> |高成本的時間 (計劃 / 執行 / 驗證)  <br/> |
|資金 （沒有硬體購買） 中較低成本  <br/> |在資金的較高成本 (硬體 + 適用於開發人員 / 系統管理員)  <br/> |
|在移轉一次性成本  <br/> |一次性成本重複每未來移轉  <br/> |
|低的整體擁有成本 / 維護  <br/> |高的整體擁有成本 / 維護  <br/> |
   
當您移轉至 Office 365 時，單次移動時，將能夠先期、 加重成本您正在將組織內的資料並決定要採用至雲端的項目以及留下的項目。不過，升級將會自動從這時、 您不再需要管理硬體和軟體更新並將由 Microsoft 服務層級協議 ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)) 備份伺服器陣列最多時間。
  
### <a name="migrate-to-sharepoint-online"></a>移轉至 SharePoint Online

請確定 SharePoint Online 有您需要透過檢閱相關聯的服務描述的所有功能。以下是所有的 Office 365 服務說明連結：
  
[Office 365 服務描述](https://go.microsoft.com/fwlink/?linkid=272060)
  
沒有直接從 SharePoint 2007 移轉至 SharePoint Online; 方法在移至 SharePoint Online 會手動完成。如果您升級至 SharePoint Server 2013 或 SharePoint Server 2016、 您移動也可能會涉及使用 SharePoint 移轉 API （例如移轉至 OneDrive for Business，資訊）。
  
|**線上專業人員**|**線上詐騙**|
|:-----|:-----|
|Microsoft 提供給 SPO 硬體及所有硬體管理。  <br/> |可用的功能可能會不同 SharePoint Server 的內部和 SPO 之間。  <br/> |
|您在訂閱的全域管理員，且可能會指派 SPO 網站的管理員。  <br/> |SharePoint Server 的內部不存在 （或不需要） 中的伺服器陣列管理員提供某些動作包含在 Office 365 中的 SharePoint 管理員角色。  <br/> |
|Microsoft 套用修補程式、 修正及更新為基礎的硬體和軟體。  <br/> |因為沒有存取權之服務中的基礎檔案系統，所以部分自訂功能會受到限制。  <br/> |
|Microsoft 發佈[服務等級協定](https://go.microsoft.com/fwlink/?linkid=843153)書寫快速解決服務層級事件。  <br/> |備份及還原及其他復原選項會自動在 SharePoint Online 服務-備份是以覆寫若不使用。  <br/> |
|安全性測試及伺服器效能調整會持續在服務中來執行 Microsoft。  <br/> |使用者介面和其他 SharePoint 功能所安裝的服務和切換開啟或關閉可能需要變更。  <br/> |
|Office 365 符合許多產業標準： [Office 365 規範](https://go.microsoft.com/fwlink/?linkid=843165)。  <br/> |僅限於[FastTrack](https://go.microsoft.com/fwlink/?linkid=518597)協助進行移轉。  <br/> 有多少升級將會是手動，或透過 SPO 移轉 API 所述的[SharePoint Online 和 OneDrive 移轉內容藍圖](https://go.microsoft.com/fwlink/?linkid=843184)。  <br/> |
|Microsoft 支援工程師和員工資料中心都有不受限制系統存取您的訂閱。  <br/> |如果需要升級以支援較新版的 SharePoint、 硬體基礎結構或次要伺服器陣列所需的升級，可以是其他的成本。  <br/> |
|協力廠商可協助進行資料移轉至 SharePoint Online 的單次工作。  <br/> ||
|線上產品會自動更新跨表示功能可能會取代，雖然有支援無則為 true 結束的服務。  <br/> ||
   
如果您已決定建立新的 Office 365 網站，並會以手動方式將資料移轉至其會視，您可以查看您的 Office 365 選項權限：
  
[Office 365 方案選項](https://go.microsoft.com/fwlink/?linkid=843151)
  
### <a name="upgrade-sharepoint-server-on-premises"></a>升級 SharePoint Server 的內部

沒有在過去略過中 SharePoint 升級的版本至少到版本的 SharePoint Server 2016 方法。這表示升級移依序：
  
|||
|:-----|:-----|
||SharePoint 2007 | SharePoint Server 2010 | SharePoint Server 2013 | SharePoint Server 2016 |
   
要從 SharePoint 2007 的整個路徑 SharePoint Server 2016 表示可大幅投資的時間和成本方面 （請注意也必須升級 SQL 伺服器） 的已升級硬體、 軟體和管理時需要。自訂項目將會需要升級或放棄，根據功能的重要性。
  
> [!NOTE]
> 可以維護您的一般生命週期 SharePoint 2007 伺服器陣列、 新硬體 （讓不同的伺服器陣列執行並排顯示） 上安裝 SharePoint Server 2016 伺服器陣列，然後規劃及執行內容 （如下載並重新上傳內容、 手動移轉範例）。請注意部分 （例如移動文件的上次修改的帳戶取代執行手動移動之帳戶的別名） 手動移動和必須完成時間 （例如重新建立網站、 子網站、 權限及清單在內工時 」 的問題結構）。同樣地，這是移轉的考量您可以將移至存放區，或不再需要、 動作可能會降低影響哪些資料的時間。
  
無論如何，清除您環境前的升級。是您現有的伺服器陣列可正常運作升級之前和解除委任 （確定） 之前 ！ 
  
檢閱**支援及不支援的升級路徑**，請記得： 
  
- 
  [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
如果您有**自訂項目**，則十分重要計劃升級每個步驟中有移轉路徑： 
  
- [SharePoint 2007](https://go.microsoft.com/fwlink/?linkid=843158)
    
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**內部專業人員**|**在內部詐騙**|
|:-----|:-----|
|SharePoint 伺服器陣列，從伺服器硬體設定的所有層面的完全控制。  <br/> |所有符號與修正項目都是 （可參與付費的 Microsoft 技術支援人員如果您的產品不支援的結尾處） 貴公司的責任：  <br/> |
|SharePoint Server 的內部使用 [連線至 SharePoint Online 混合式透過訂閱的內部部署伺服器陣列] 選項的完整的功能集。  <br/> |升級、 修補程式、 安全性修正程式及所有維護 SharePoint Server 的受管理的內部。  <br/> |
|針對更大的自訂的完整存取。  <br/> |[規範標準支援的 Office 365](https://go.microsoft.com/fwlink/?linkid=843165)必須手動設定內部部署。  <br/> |
|安全性測試及伺服器效能調整實現在您內部部署 （是由您控制）。  <br/> |Office 365 可能會讓功能可供 SharePoint Online 的不能與 SharePoint Server 的內部互通  <br/> |
|協力廠商可協助進行移轉的 SharePoint Server （和超過） 的下一版的資料。  <br/> |SharePoint Server 網站不會自動使用[SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167)憑證視為是 SharePoint Online 中。  <br/> |
|命名慣例、 備份及還原 SharePoint Server 的內部其他復原選項的完全控制。  <br/> |SharePoint Server 的內部會受到產品生命週期。  <br/> |
   
### <a name="upgrade-resources"></a>升級的資源

先了解您是否符合硬體和軟體需求，然後遵循支援的升級方法。
  
- **硬體/軟體需求**： 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)
    
- **軟體界限和限制**： 
    
    [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843245) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)
    
- **的升級程序概觀**： 
    
    [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843250) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>建立 SharePoint Online 和內部部署之間的 SharePoint 混合式解決方案

如果移轉需求的答案某處之間提供內部部署，並提供 SharePoint Online 的擁有權的較低成本並非指自我控制，您可以連線 SharePoint Server 2013 或 2016年伺服器陣列至 SharePoint Online、 混合透過。[了解 SharePoint 混合式解決方案](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)
  
如果您決定將混合式 SharePoint 伺服器陣列的業務好處，熟悉現有的混合式以及如何設定內部部署 SharePoint 伺服器陣列與您的 Office 365 訂閱之間的連線類型。
  
請參閱這的運作方式的其中一個好方法是建立[Office 365 開發人員/測試環境](https://go.microsoft.com/fwlink/?linkid=843152)。一旦您有試用版或購買 Office 365 訂閱，您必須在您的方式來建立網站集合、 web、 與文件庫的 SharePoint Online 可移轉資料 (其中一個手動，藉由使用移轉 API 或-如果您想要移轉我網站內容至 OneDrive for Business-透過混合精靈]）。
  
> [!NOTE]
> 請記得在 SharePoint 2007 伺服器陣列需要升級，內部部署、 SharePoint Server 2013 或 SharePoint Server 2016 來使用混合選項 
  
## <a name="related-topics"></a>相關主題

[疑難排解與繼續升級 (Office SharePoint Server 2007)](https://go.microsoft.com/fwlink/?linkid=843192)
  
[疑難排解升級問題 (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkid=843194)
  
[在 SharePoint 2013 中針對資料庫的升級問題進行疑難排解](https://go.microsoft.com/fwlink/?linkid=843195)
  
[搜尋功能可協助升級 Microsoft 合作夥伴](https://go.microsoft.com/fwlink/?linkid=841249)
  
[可協助您升級從 Office 2007 的伺服器和用戶端的資源](upgrade-from-office-2007-servers-and-products.md)
  

