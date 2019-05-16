---
title: SharePoint Server 2007 終止支援藍圖
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 01/28/2019
audience: ITPro
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
description: 於 2017 年 10 月 10 日，支援結束 for SharePoint Server 2007。 閱讀本篇文章以了解升級的選項，進行疑難排解，最佳作法、 系統需求、 升級的步驟，以及如何取得 Microsoft 合作夥伴提供的協助。
ms.openlocfilehash: 5e5f697f64c520ec1be2b055be0fd42e1742a9ed
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070719"
---
# <a name="sharepoint-server-2007-end-of-support-roadmap"></a>SharePoint Server 2007 終止支援藍圖

於**2017 年 10 月 10 日**，Microsoft Office SharePoint Server 2007 會達到終止支援。 如果您還沒有開始從 SharePoint Server 2007 移轉至 Office 365 或較新版本的 SharePoint Server 內部部署，現在是以開始規劃的時間。 本文詳述資源以協助將資料移轉至 SharePoint Online，或升級 SharePoint Server 內部的人員。 
  
## <a name="what-does-end-of-support-mean"></a>支援平均數的哪些並結束？

SharePoint Server 一樣幾乎所有的 Microsoft 產品中，有支援週期期間 Microsoft 提供的新功能、 錯誤修正程式、 安全性修正程式、 等等。 此生命週期通常會持續 10 年起的產品的初始版本，與此生命週期結束稱為 「 支援的產品的結尾。 在結尾的支援，Microsoft 不再提供：
  
- 技術支援問題，可能會發生;
    
- 錯誤修正問題，會發現及，可能會影響 exchange 的穩定性與可用性的伺服器;
    
- 安全性問題修正，會發現及，可能會讓伺服器受到安全性弱點; 的弱點和 
    
- 時間的時區更新。
    
雖然您的 SharePoint Server 2007 伺服器陣列還是會正常運作之後年 10 月 10，2017，沒有進一步更新及修補程式，或修正會出貨產品 （包括安全性修補程式/修正），以及 Microsoft 支援服務將會完全移至其支援人員的協助較新版本的產品。 因為不再支援或修補，將會安裝，支援方法的結尾為您應該升級、 產品或移轉重要的資料。
  
> [!TIP]
> 如果您已經尚未規劃升級或移轉，請參閱：[要考慮 SharePoint 2007 移轉選項](sharepoint-2007-migration-options.md)，若要開始的位置的一些範例。 您也可以搜尋[的 Microsoft 合作夥伴](https://go.microsoft.com/fwlink/?linkid=841249)可協助進行升級或 Office 365 移轉 （或兩者）。 
  
如需達到終止支援的 Office 2007 伺服器的詳細資訊，請參閱 <<c0>資源可以幫助您升級從 Office 2007 伺服器和用戶端。
  
## <a name="what-are-my-options"></a>我的選項為何？

您第一張停駐點應是[產品生命週期網站](https://go.microsoft.com/fwlink/?linkid=843148)。 如果您有已過時内部署 Microsoft 產品，您應檢查其支援日期結尾因此，一年或操作出-或，只要您移轉通常都需要-您可以排程升級或移轉。 當選擇 [下一步]，它可能協助認為方面功能可能會不夠好，更好的而且最佳過濾的產品功能。 以下為範例：
  
|**良好**|**更佳**|**最佳**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013  <br/> |SharePoint Online  <br/> |
||SharePoint 混合式  <br/> |SharePoint Server 2016  <br/> |
|||SharePoint 混合式  <br/> |
   
如果您選擇 [選項] 的低刻度的上方 （不夠好），請記得您想要開始從 SharePoint Server 2007 的移轉後很快規劃升級已完成。 （SharePoint Server 2007 支援的結尾是 2017 年 10 月 10 日。 請注意，這些日期會受到變更，並檢查[產品生命週期網站](https://support.microsoft.com/en-us/lifecycle)）。
  
## <a name="where-can-i-go-next"></a>我移其中下一個？

SharePoint Server 可以是安裝於內部上您自己的伺服器，或您可以使用 SharePoint Online，也就是屬於 Microsoft Office 365 線上服務。 您可以選擇：
  
- 移轉至 SharePoint Online
    
- 升級 SharePoint Server 內部部署
    
- 執行這兩個以上
    
- 實作[SharePoint 混合式](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)解決方案 
    
請注意的隱藏的成本與維護接下來，在伺服器陣列相關聯維護或移轉自訂項目，並升級 SharePoint Server 所依存的硬體。 如果是必要性; 具有內部部署 SharePoint Server 伺服器陣列薪水否則，如果您在舊版的 SharePoint 伺服器，不需要大量的自訂，執行您的伺服器陣列您可以受益於計劃性遷移到 SharePoint Online。
  
> [!IMPORTANT]
> 如果不常使用 SharePoint 2007 中的內容，則，沒有另一個選項。 某些 SharePoint 系統管理員可以選擇[建立 Office 365 訂閱](https://go.microsoft.com/fwlink/?linkid=843152)，請設定全新的 SharePoint Online 網站，，然後執行全新，地開 SharePoint 2007 剪下只最重要的文件帶到最新的 SharePoint Online 網站。 從那裡，資料可能會耗盡從 SharePoint 2007 網站到封存。 授與使用者的運作方式與資料 SharePoint 2007 安裝的思考。 可能有創意方法若要解決此問題 ！ 
  
|**SharePoint Online (SPO)**|**SharePoint Server 內部部署**|
|:-----|:-----|
|高成本的時間 (計劃 / 執行 / 驗證)  <br/> |高成本的時間 (計劃 / 執行 / 驗證)  <br/> |
|成本較低的資金 （沒有硬體購買）  <br/> |在 [資金成本較高 (硬體 + 適用於開發人員 / 管理員)  <br/> |
|在移轉的一次性成本  <br/> |未來移轉每重複的一次性成本  <br/> |
|低的整體擁有成本 / 維護  <br/> |高的整體擁有成本 / 維護  <br/> |
   
當您移轉到 Office 365 時，一次移動會有預付，粗成本時您正在組織資料，並決定要採取至雲端的項目以及要留下項目。 不過，就會自動從該點開始升級、 您不再需要管理的硬體和軟體更新，並執行時間的伺服器陣列會備份由 Microsoft 服務層級協議 ([SLA](https://go.microsoft.com/fwlink/?linkid=843153))。
  
### <a name="migrate-to-sharepoint-online"></a>移轉至 SharePoint Online

請確定 SharePoint Online 具有您需要檢閱相關聯的服務描述的所有功能。 以下是所有 Office 365 服務描述的連結：
  
[Office 365 服務描述](https://go.microsoft.com/fwlink/?linkid=272060)
  
沒有直接從 SharePoint 2007 移轉至 SharePoint Online; 方法會以手動方式完成您移至 SharePoint Online。 如果您升級至 SharePoint Server 2013 或 SharePoint Server 2016，您移動可能也需要使用 SharePoint 移轉 API （例如移轉到商務用 OneDrive 的資訊）。
  
|**線上 Pro**|**線上詐騙**|
|:-----|:-----|
|Microsoft 提供 SPO 硬體和所有硬體管理。  <br/> |可用的功能可能會不同 SharePoint Server 內部部署和 SPO 之間。  <br/> |
|您是全域系統管理員的您的訂閱，並可能會將系統管理員指派給 SPO 網站。  <br/> |某些 SharePoint Server 內部部署不存在 （或不是必要的） 中的伺服器陣列管理員可用的動作包含在 Office 365 中的 SharePoint 系統管理員角色。  <br/> |
|Microsoft 會套用修補程式、 修正和更新為基礎的硬體及軟體。  <br/> |因為無法存取服務中的基礎檔案系統，有一些自訂項目。  <br/> |
|Microsoft 會發佈[服務層級協議](https://go.microsoft.com/fwlink/?linkid=843153)，並快速地移到解決服務層級事件。  <br/> |備份及還原其他復原選項會自動完成的 SharePoint Online 中的服務-備份會覆寫如果沒有提供使用。  <br/> |
|安全性測試及伺服器的效能調整會持續在服務中由執行 Microsoft。  <br/> |變更使用者介面與其他 SharePoint 功能會安裝服務，以及可能需要重新開啟或關閉切換。  <br/> |
|Office 365 符合許多業界標準： [Office 365 合規性](https://go.microsoft.com/fwlink/?linkid=843165)。  <br/> |僅限於[FastTrack](https://go.microsoft.com/fwlink/?linkid=518597)協助進行移轉。  <br/> 大部分的升級會手動，或透過 SPO 移轉 API 所述的[SharePoint Online 和 OneDrive 移轉內容藍圖](https://go.microsoft.com/fwlink/?linkid=843184)。  <br/> |
|Microsoft 技術支援工程師和資料中心內的員工都有不受限制系統管理員存取您的訂閱。  <br/> |如果要升級以支援較新版本的 SharePoint，就必須硬體基礎結構或次要伺服器陣列是需要升級時，則可以是其他成本。  <br/> |
|合作夥伴可協助進行一次性作業的資料移轉至 SharePoint Online。  <br/> ||
|線上產品會自動更新，這可能會取代功能，但是沒有支援沒有，則為 true 結束的服務。  <br/> ||
   
如果您已決定要建立新的 Office 365 網站，並會以手動方式將資料移轉至其所需，您可以查看您的 Office 365 選項權限：
  
[Office 365 方案選項](https://go.microsoft.com/fwlink/?linkid=843151)
  
### <a name="upgrade-sharepoint-server-on-premises"></a>升級 SharePoint Server 內部部署

沒有在過去略過至少起版本的 SharePoint Server 2016 中 SharePoint 升級，版本方法。 這表示升級循序移：
  
|||
|:-----|:-----|
||SharePoint 2007 | SharePoint Server 2010 | SharePoint Server 2013 | SharePoint Server 2016 |
   
要從 SharePoint 2007 中取用的完整路徑 SharePoint Server 2016 會表示時間大量投資，並會牽涉成本方面 （請注意 SQL 伺服器也必須升級） 的升級硬體、 軟體和管理。 自訂項目將會需要升級或因此而棄置，根據功能的重要性。
  
> [!NOTE]
> 很可能維護週期結束 SharePoint 2007 伺服器陣列、 在新硬體上 （因此不同的伺服器陣列執行並排顯示），安裝 SharePoint Server 2016 伺服器陣列，然後計劃和執行內容 （適用於下載與重新上傳內容，如手動移轉範例）。 請注意一些問題 （例如移動的文件的上次修改的帳戶取代執行手動移動之帳戶的別名） 手動移動和必須事先 （例如重新建立網站、 子網站、 權限和清單完成的工時結構）。 同樣地，這是要考慮您可以將移至存放區，或不再需要，可以減少移轉的影響動作何種資料的時間。
  
無論如何，清除您要升級的環境之前。 是您現有的伺服器陣列正常運作，再升級，您和您解除委任 （確定） 之前 ！ 
  
檢閱**支援與不支援的升級路徑**，請記得： 
  
- 
  [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
如果您有**自訂項目**，則務必您的移轉路徑中有計劃升級每個步驟： 
  
- [SharePoint 2007](https://go.microsoft.com/fwlink/?linkid=843158)
    
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**內部 Pro**|**在內部詐騙**|
|:-----|:-----|
|SharePoint 伺服器陣列，從備份的伺服器硬體的各個層面的完全控制權。  <br/> |是 （可參與付費的 Microsoft 支援服務如果您的產品不支援的結尾處） 貴公司的責任的所有符號和修正程式：  <br/> |
|SharePoint Server 內部部署與您的內部部署伺服器陣列連線到 SharePoint Online 訂閱透過混合式選項的完整功能集。  <br/> |升級、 修補程式、 安全性修正程式和所有維護 SharePoint Server 受管理的內部。  <br/> |
|更大的自訂的完整存取權。  <br/> |[Office 365 所支援的合規性標準](https://go.microsoft.com/fwlink/?linkid=843165)必須以手動方式設定內部部署。  <br/> |
|測試安全性，與伺服器效能調整，實行您內部部署 （位於您的控制下）。  <br/> |Office 365 可能提供功能給 SharePoint Online 無法搭配 SharePoint Server 內部交互操作  <br/> |
|合作夥伴可協助進行移轉至下一個版本的 SharePoint Server （以及超過） 的資料。  <br/> |SharePoint Server 網站不會自動使用[SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167)憑證視為是 SharePoint Online 中。  <br/> |
|完整的命名慣例、 備份及還原 SharePoint Server 內部部署中的其他復原選項的控制項。  <br/> |SharePoint Server 內部部署是機密產品週期。  <br/> |
   
### <a name="upgrade-resources"></a>升級的資源

先知道您符合硬體和軟體需求，然後遵循支援升級方法。
  
- **軟硬體需求**： 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)
    
- **軟體界限及限制**： 
    
    [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843245) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)
    
- **升級程序概觀**： 
    
    [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843250) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>建立 SharePoint Online 與內部部署之間的 SharePoint 混合式解決方案

如果您的移轉需求的答案某處之間提供內部部署，並提供 SharePoint online 的擁有權的低成本並非指自我控制，您可以連線 SharePoint Server 2013 或 2016年伺服器陣列至 SharePoint Online 中，透過混合。 [了解 SharePoint 混合式解決方案](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)
  
如果您決定混合式 SharePoint Server 伺服器陣列會對您的業務，熟悉現有的混合式以及如何設定您的內部部署 SharePoint 伺服器陣列與 Office 365 訂閱之間的連線類型。
  
若要查看如何進行此作業的一個好方法是藉由建立[Office 365 開發/測試環境](https://go.microsoft.com/fwlink/?linkid=843152)。 一旦您有試用或購買 Office 365 訂閱，您就可以在您要在 SharePoint Online 中的您可以將資料移轉建立的網站集合、 web、 及文件庫 ([以手動方式，藉由使用移轉 API，或-如果您想要移轉我網站內容，商務用 OneDrive-透過混合式精靈使用）。
  
> [!NOTE]
> 請記住，您的 SharePoint 2007 伺服器陣列需要升級，在內部部署、 SharePoint Server 2013 或 SharePoint Server 2016 以使用混合式選項 
  
## <a name="related-topics"></a>相關主題

[疑難排解，並繼續升級 (Office SharePoint Server 2007)](https://go.microsoft.com/fwlink/?linkid=843192)
  
[疑難排解升級問題 (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkid=843194)
  
[在 SharePoint 2013 中針對資料庫的升級問題進行疑難排解](https://go.microsoft.com/fwlink/?linkid=843195)
  
[適用於 Microsoft 合作夥伴以協助進行升級的搜尋](https://go.microsoft.com/fwlink/?linkid=841249)
  
[資源可以幫助您升級從 Office 2007 伺服器和用戶端](upgrade-from-office-2007-servers-and-products.md)
  

