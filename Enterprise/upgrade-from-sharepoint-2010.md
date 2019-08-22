---
title: 從 SharePoint 2010 升級
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 08/21/2019
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
description: 支援結束 for SharePoint 2010 和 SharePoint Server 2010 結束於 2020 年 10 月 13。 使用本文做為指南，升級至 SharePoint Online 或 SharePoint Server 內部部署的較新版本。
ms.openlocfilehash: 944dd4a2980097611de1fa9239acbfca46517960
ms.sourcegitcommit: 756f1713cab2e46be948f91f6dd87fd60197c4a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "36491322"
---
# <a name="upgrading-from-sharepoint-2010"></a>從 SharePoint 2010 升級

Microsoft SharePoint 2010 和 SharePoint Server 2010 會達到**2020 年 10 月 13，** 支援的結尾。 本文詳述資源以協助您將您現有的 SharePoint Server 2010 資料移轉至 Office 365 中 SharePoint Online 或升級您的內部部署 SharePoint Server 2010 環境。
  
## <a name="what-is-end-of-support"></a>終止支援是什麼？

當您 SharePoint Server 2010 和 SharePoint Foundation 2010 的軟體達到其支援週期 （在這期間 Microsoft 提供的新功能、 錯誤修正程式、 安全性修正程式、 等等的時間） 的結尾時，這就稱為 「 軟體 '終止支援'，或者，有時候，其 ' 退休 '。 在產品支援 （或 EOS） 結束時，則是 nothing 實際關機或停止運作;不過，在軟體支援的結束時，Microsoft 不再提供：
  
- 技術支援問題，可能會發生;
    
- 錯誤修正問題，會發現及，可能會影響 exchange 的穩定性與可用性的伺服器;
    
- 安全性問題修正，會發現及，可能會讓伺服器受到安全性弱點; 的弱點
    
- 時間的時區更新。
    
這表示，會有任何進一步修補程式、 更新或修正會出貨產品 （包括安全性修補程式/修正），以及 Microsoft 支援服務將會有完全移位，其支援人員的協助以較新版本。 為支援 SharePoint Server 2010 的結尾方式，您應該利用機會修剪您不再需要升級、 產品及/或重要資料移轉前的資料。
  
> [!NOTE]
> 從產品的最初發行版本的日期 10 年通常會持續軟體生命週期。 您可以搜尋提供者與升級至您的軟體，下一版或 Office 365 移轉 （或兩者） 可協助[Microsoft 解決方案提供者](https://go.microsoft.com/fwlink/?linkid=841249)。 先確定您知道的結尾，重要基礎技術支援日期尤其是您正在使用 SharePoint 的 SQL Server 的版本。 
  
## <a name="what-are-my-options"></a>我的選項為何？

首先，請在 [[產品生命週期站台](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202010)上支援結束日期。 接下來，請務必規劃升級或移轉知曉此日期與時間。 請記住，您產品*不會停止運作*於日期列出，且您可以繼續使用，但是，由於不再將該日期之後安裝您安裝的補充程式，您會想將協助您更順暢地轉換到下一個版本的策略在產品。 
  
這個矩陣可協助繪製課程過濾移轉產品功能及使用者資料：
  
|**支援產品的結尾**|**良好**|**最佳**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013 （內部）  <br/> |SharePoint Online  <br/> |
||使用 SharePoint Online 的 SharePoint Server 2013 混合式  <br/> |SharePoint Server 2016 （內部）  <br/> |
|||SharePoint 雲端混合式搜尋  <br/> |
   
如果您選擇在低的小數位數 （[好的選項]） 選項，您需要開始在從 SharePoint Server 2010 的移轉完成後，另一個升級的規劃。 

以下是三個避免支援 SharePoint Server 2010 的結尾時，可採取的路徑。

![SharePoint Server 2010 升級路徑](./media/upgrade-from-sharepoint-2010/upgrade-from-sharepoint-2010-paths.png)

>[!Note]
>支援 SharePoint Server 2010 和 SharePoint Foundation 2010 的結尾被排定 2020 年 10 月 13，但*請注意*，您應該一律檢查[產品生命週期網站](https://support.microsoft.com/en-us/lifecycle)的最新的日期。
>

  
## <a name="where-should-i-go-next"></a>其中應該我進入下一個？

SharePoint Server 2013 和 SharePoint Foundation 2013 可以安裝在內部上您自己的伺服器。 否則，您可以使用 SharePoint Online，也就是屬於 Microsoft Office 365 線上服務。 您可以選擇：
  
- 移轉至 SharePoint Online
    
- 升級 SharePoint Server 或 SharePoint Foundation 內部部署
    
- 執行這兩個以上
    
- 實作[SharePoint 混合式](https://docs.microsoft.com/sharepoint/hybrid/hybrid)解決方案 
    
請注意的隱藏的成本與維護接下來，在伺服器陣列相關聯維護或移轉自訂項目，並升級 SharePoint Server 所依存的硬體。 如果您知道，具有所有這些列入，它會繼續升級內部的工作變得更容易。 否則，如果您不需要大量的自訂的舊版 SharePoint 伺服器上執行您的伺服器陣列，您可受惠於計劃性遷移到 SharePoint Online。 它也可能是，針對內部部署 SharePoint Server 環境，您可能會選擇將一些資料放入 SharePoint Online 以減少硬體管理保留之所有資料內部牽涉到數量。 它可能會更經濟將部分資料移至 SharePoint Online。
  
> [!NOTE]
> SharePoint 系統管理員可能會[建立 Office 365 訂閱](https://go.microsoft.com/fwlink/?linkid=843152)，請設定全新的 SharePoint Online 網站，，然後執行全新，地從 SharePoint Server 2010，剪下只最重要的文件帶到最新的 SharePoint Online 網站。 從那裡，其餘的任何資料可能會耗盡從 SharePoint Server 2010 網站到內部部署封存。 
  
|**SharePoint Online**|**SharePoint Server 內部部署**|
|:-----|:-----|
|高成本的時間 (計劃 / 執行 / 驗證)  <br/> |高成本的時間 (計劃 / 執行 / 驗證)  <br/> |
|成本較低的資金 （沒有硬體購買）  <br/> |較高成本的資金 （硬體購買）  <br/> |
|在移轉的一次性成本  <br/> |未來移轉每重複的一次性成本  <br/> |
|低的整體擁有成本 / 維護  <br/> |高的整體擁有成本 / 維護  <br/> |
   
當您移轉到 Office 365 時，一次移動會有時間粗成本所花費的規劃、 購置 （雖然您正在組織資料，並決定要採取至雲端的項目以及要留下項目）。 不過，一旦您的資料會移轉，升級會自動從該點，因為您不再需要管理的硬體和軟體更新，並執行時間的伺服器陣列會備份由 Microsoft 服務層級協議 ([SLA](https://go.microsoft.com/fwlink/?linkid=843153))。
  
### <a name="migrate-to-sharepoint-online"></a>移轉至 SharePoint Online

請務必 SharePoint Online 提供您需要檢閱其[服務描述](https://docs.microsoft.com/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-service-description)的所有功能。
  
目前沒有的方法，依據您可以直接從移轉 SharePoint Server 2010 （或 SharePoint Foundation 2010） 至 SharePoint Online，因此部分工作是手動。 這並可讓您封存和党資料與不再需要在移動前的網站。 您可以封存其他資料儲存成。 另請記住，SharePoint Server 2010 和 SharePoint Foundation 2010 都不會停止運作結尾的支援，讓系統管理員可以有一段期間 SharePoint 仍在執行若客戶忘記移動部分其資料。
  
如果您升級至 SharePoint Server 2013 或 SharePoint Server 2016，並決定要將資料放入 SharePoint Online，移動可能也需要使用[SharePoint 移轉 API](https://support.office.com/en-us/article/Upload-on-premises-content-to-SharePoint-Online-using-PowerShell-cmdlets-555049c6-15ef-45a6-9a1f-a1ef673b867c?ui=en-US&amp;rs=en-US&amp;ad=US) （移轉到商務用 OneDrive 的資訊）。 
  
|**SharePoint Online 的優點**|**SharePoint Online 的缺點**|
|:-----|:-----|
|Microsoft 提供 SPO 硬體和所有硬體管理。  <br/> |可用的功能可能會不同 SharePoint Server 內部部署和 SPO 之間。  <br/> |
|您已訂閱的全域系統管理員，並可能會將系統管理員指派給 SPO 網站。  <br/> |在 SharePoint Server 內部部署伺服器陣列管理員可某些動作不存在 （或不是必要的） 在 Office 365，但 SharePoint 管理 SharePoint 系統管理員角色，網站集合管理] 和網站擁有權是本機貴  <br/> |
|Microsoft 會套用修補程式、 修正和更新為基礎的硬體和軟體 （包括 SharePoint Online 會執行所在的 SQL 伺服器）。  <br/> |因為無法存取服務中的基礎檔案系統，有一些自訂項目。  <br/> |
|Microsoft 會發佈[服務層級協議](https://go.microsoft.com/fwlink/?linkid=843153)，並快速地移到解決服務層級事件。  <br/> |備份及還原其他復原選項會自動完成的 SharePoint Online 中的服務-備份會覆寫如果沒有提供使用。  <br/> |
|安全性測試及伺服器的效能調整會持續在服務中由執行 Microsoft。  <br/> |變更使用者介面與其他 SharePoint 功能會安裝服務，以及可能需要重新開啟或關閉切換。  <br/> |
|Office 365 符合許多業界標準： [Office 365 合規性](https://go.microsoft.com/fwlink/?linkid=843165)。  <br/> |僅限於[FastTrack](https://go.microsoft.com/fwlink/?linkid=518597)協助進行移轉。  <br/> 大部分的升級會手動，或透過 SPO 移轉 API 所述的[SharePoint Online 和 OneDrive 移轉內容藍圖](https://go.microsoft.com/fwlink/?linkid=843184)。  <br/> |
|Microsoft 技術支援工程師和資料中心內的員工都有不受限制系統管理員存取您的訂閱。  <br/> |如果要升級以支援較新版本的 SharePoint，就必須硬體基礎結構或次要伺服器陣列是需要升級時，則可以是其他成本。  <br/> |
|解決方案提供者可協助進行一次性作業的資料移轉至 SharePoint Online。  <br/> |SharePoint Online 不是所有變更都都會在控制項中。 在移轉之後，設計差異功能表、 文件庫及其他功能可能會暫時影響可用性。  <br/> |
|線上產品會自動更新，這可能會取代功能，但是沒有沒有，則為 true 終止支援週期的服務。  <br/> |Read 基礎 SQL 伺服器沒有支援週期的 SharePoint Server （或 SharePoint Foundation） 的結尾。  <br/> |
   
如果您已決定要建立新的 Office 365 網站，並會以手動方式將資料移轉至其所需，您可以查看您的[Office 365 方案選項](https://go.microsoft.com/fwlink/?linkid=843151)。
  

  
### <a name="upgrade-sharepoint-server-on-premises"></a>升級 SharePoint Server 內部部署

為最新版本的 SharePoint 內部部署產品 (SharePoint Server 2016)，必須*依序*進入 SharePoint Server 升級，這表示沒有任何方法可以從 SharePoint Server 2010 升級至 SharePoint Server 2016，直接。 
  
|||
|:-----|:-----|
||序列升級路徑 * * *: SharePoint Server 2010 **\>** SharePoint Server 2013 **\>** SharePoint Server 2016 |
   
如果您選擇要從 SharePoint 2010 遵循 SharePoint Server 2016 的完整路徑，這將帶時間與計劃。 升級牽涉到方面 （請注意 SQL 伺服器也必須升級） 的升級的硬體、 軟體和管理成本。 此外，自訂項目可能需要升級，或甚至是放棄。 請務必先升級您的 SharePoint 伺服器陣列備忘稿收集所有您要徑的自訂項目上。
  
> [!NOTE]
> 很可能維持您結尾支援 SharePoint 2010 伺服器陣列、 在新硬體上 （因此不同的伺服器陣列執行並排顯示），安裝 SharePoint Server 2016 伺服器陣列並再計劃和執行內容 （適用於下載與重新上傳內容，如手動移轉範例）。 有潛在的問題 （例如文件即將從 2010年具有執行手動移動之帳戶的別名與目前的上次修改的帳戶），這些手動移動到，且必須事先完成某些工作 (重新建立網站、 子網站、 權限和清單的結構）。 它是正是時候考慮的資料您可以移到存放區，或不再需要的項目。 這可減少移轉的影響。 無論如何，清除您要升級的環境之前。 是您現有的伺服器陣列正常運作，再升級，您和您解除委任 （確定） 之前 ！ 
  
檢閱**支援與不支援的升級路徑**，請記得： 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
如果您有**自訂項目**，則務必您的移轉路徑中有計劃升級每個步驟： 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**內部部署的優點**|**內部部署的缺點**|
|:-----|:-----|
|從伺服器硬體的完整控制您的 SharePoint 伺服器陣列 （和其 SQL） 的所有層面的設定。  <br/> |所有符號和修正都是貴公司的責任 （但如果您的產品不支援的結尾，您可以邀請付費的 Microsoft 支援服務）：  <br/> |
|SharePoint Server 內部部署與您的內部部署伺服器陣列連線到 SharePoint Online 訂閱透過混合式選項的完整功能集。  <br/> |升級、 修補程式、 安全性修正程式、 硬體升級及 SharePoint Server 和它的 SQL 伺服器陣列的所有維護為受管理的內部部署。  <br/> |
|比更大的自訂選項，與 SharePoint Online 的完整存取權。  <br/> |[Office 365 所支援的合規性標準](https://go.microsoft.com/fwlink/?linkid=843165)必須以手動方式設定內部部署。  <br/> |
|測試安全性，與伺服器效能調整，執行您內部部署 （在您的控制項）。  <br/> |Office 365 可能提供功能給 SharePoint Online 無法搭配 SharePoint Server 內部交互操作  <br/> |
|解決方案提供者可協助進行移轉至下一個版本的 SharePoint Server （以及超過） 的資料。  <br/> |SharePoint Server 網站不會自動使用[SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167)憑證視為是 SharePoint Online 中。  <br/> |
|完整的命名慣例、 備份及還原 SharePoint Server 內部部署中的其他復原選項的控制項。  <br/> |SharePoint Server 內部部署是機密產品週期。  <br/> |
   
### <a name="upgrade-resources"></a>升級的資源

開始藉由比較硬體和軟體需求。 如果您不符合目前的硬體上升級的基本需求，這代表您要在伺服器陣列或 SQL server 的硬體先升級，或您可能決定要將某些百分比網站移至 SharePoint online 的 evergreen' 硬體。 一旦您已進行評估，請遵循支援的升級路徑和方法。
  
- **軟硬體需求**： 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)
    
- **軟體界限及限制**： 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)
    
- **升級程序概觀**： 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-sharepoint-server-on-premises"></a>建立 SharePoint Online 和 SharePoint Server 內部部署之間的 SharePoint 混合式解決方案

另一個選項 （可能是內部部署和線上世界部分移轉最佳的其中一個需要） 是混合式，您可以連接到 SharePoint Server 2013 或 2016年伺服器陣列 SharePoint Online 建立 SharePoint 混合式：[了解有關 SharePoint 混合式解決方案](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).
  
如果您決定混合式 SharePoint Server 伺服器陣列是您的移轉目標，請務必規劃哪些網站和使用者應移至線上，以及需要保持內部部署。 檢閱和排名 （決定何種資料高、 中或低影響您的公司） 的 SharePoint 伺服器陣列的內容很有幫助這個決策。 它可能是，您需要使用 SharePoint Online 共用的唯一事項是 （a） 使用者帳戶登入，並 （b） 在 SharePoint Server 搜尋索引-這可能無法清除直到您查看如何使用您的網站。 如果貴公司稍後決定要將所有的內容移轉至 SharePoint Online，您可以線上移動所有其餘的帳戶和資料和解除委任內部部署伺服器陣列，而且/管理 SharePoint 伺服器陣列會透過 Office 365從該點上的主控台。
  
請務必熟悉現有的混合式以及如何設定您的內部部署 SharePoint 伺服器陣列與 Office 365 訂閱之間的連線類型。
  
若要查看混合式 SharePoint 伺服器陣列的運作方式的其中一個好方法是藉由建立[Office 365 開發/測試環境](https://go.microsoft.com/fwlink/?linkid=843152)。 一旦您有試用或購買 Office 365 訂閱，您就可以在您要在 SharePoint Online 中的您可以將資料移轉建立的網站集合、 web、 及文件庫 ([以手動方式，藉由使用移轉 API，或-如果您想要移轉我網站內容，商務用 OneDrive-透過混合式精靈使用）。
  
> [!NOTE]
> 請記住，您的 SharePoint Server 2010 伺服器陣列必須先升級，在內部部署、 SharePoint Server 2013 或 SharePoint Server 2016 使用 [混合] 選項。 SharePoint Foundation 2010 與 SharePoint Foundation 2013 無法建立與 SharePoint Online 的混合式連線。 

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>Office 2010 用戶端和伺服器和 Windows 7 的選項摘要

視覺升級摘要移轉，並以雲端移動選項 Office 2010 用戶端和伺服器和 Windows 7，下載[服務海報的結尾](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/enterprise/media/migration-microsoft-365-enterprise-workload/Office2010Windows7EndOfService.pdf)。

![](./media/upgrade-from-office-2010-servers-and-products/office2010-windows7-end-of-service.png)

這一頁海報是了解可防止 Office 2010 用戶端與伺服器產品及 Windows 7 達到結尾的慣用的路徑與反白顯示的 Microsoft 365 企業版中的選項支援服務，可採取的各種路徑的快速方法。

您可以列印此海報以字母、 法律或 tabloid (11 x 17) 格式。
  
## <a name="related-topics"></a>相關主題

[資源可以幫助您升級從 Office 2007 或 2010年伺服器和用戶端](upgrade-from-office-2010-servers-and-products.md)
  
[Overview of the upgrade process from SharePoint 2010 to SharePoint 2013](https://technet.microsoft.com/en-us/library/mt493301%28v=office.16%29.aspx)
  
[從 SharePoint 2010 升級至 SharePoint 2013 的最佳作法](https://technet.microsoft.com/en-us/library/mt493305%28v=office.16%29.aspx)
  
[在 SharePoint 2013 中針對資料庫的升級問題進行疑難排解](https://go.microsoft.com/fwlink/?linkid=843195)
  
[搜尋 Microsoft 解決方案提供者，以協助您的升級](https://go.microsoft.com/fwlink/?linkid=841249)
  
[已更新 SharePoint 2013 的產品服務原則](https://technet.microsoft.com/en-us/library/mt493253%28v=office.16%29.aspx)
  
[已更新 SharePoint Server 2016 的產品服務原則](https://technet.microsoft.com/en-us/library/mt782882%28v=office.16%29.aspx)
  

