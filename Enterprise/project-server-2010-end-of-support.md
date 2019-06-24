---
title: Project Server 2010 的支援路線圖
ms.author: efrene
author: efrene
manager: pamg
ms.date: 06/03/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: IT_ProjectAdmin
search.appverid:
- MET150
- ZPJ120
- PJU120
- PJW120
description: Project Server 2010 的支援結束于2020年10月13日。 使用本文做為升級到 Project Online 或更新版本的 Project Server 內部部署的指南。
ms.openlocfilehash: 86ab1534058d49094327c326d8367a08c14d725b
ms.sourcegitcommit: c763b0f28e1ce498aef5d5deb3b6324288da85ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/21/2019
ms.locfileid: "35128700"
---
# <a name="project-server-2010-end-of-support-roadmap"></a>Project Server 2010 的支援藍圖結束

Project Server 2010 將于**2020 年10月13日**到達支援的支援。 如果您目前使用的是 Project Server 2010, 請注意, 這些其他相關產品的支援日期結尾如下:
  
|**產品**|**支援日期結束**|
|:-----|:-----|
|Project Portfolio Server 2010  <br/> |2020年10月13日  <br/> |
|Project 2010 Standard  <br/> |2020年10月13日  <br/> |
|Project 2010 專業版  <br/> |2020年10月13日  <br/> |
   
如需 Office 2010 伺服器到達支援終止的詳細資訊, 請參閱[從 Office 2010 伺服器和用戶端產品升級](https://docs.microsoft.com/office365/enterprise/plan-upgrade-previous-versions-office)。
  
## <a name="what-does-end-of-support-mean"></a>支援的結尾是什麼意思？

Project Server 幾乎就像所有的 Microsoft 產品一樣, 都有一個支援週期, 我們提供了新功能、錯誤修正程式和安全性更新。 此生命週期通常是從產品初始發行日期起10年的時間開始, 而此生命週期的結尾則稱為產品的支援結束。 當 Project Server 2010 達到其在10月 13 2020 日的支援結束時, Microsoft 將不再提供:
  
- 可能發生之問題的技術支援。
    
- 針對所探索問題的錯誤修正程式, 可能會影響伺服器的穩定性和可用性。
    
- 針對所探索之漏洞的安全性修正程式, 可能會使伺服器受到安全性違規的影響。
    
- 時區更新。
    
您的 Project Server 2010 安裝將在此日期之後繼續執行。 不過, 由於以上所列的變更, 強烈建議您儘快從 Project Server 2010 進行遷移。
  
## <a name="what-are-my-options"></a>我的選項是什麼？

如果您使用的是 Project Server 2010, 您必須探索遷移選項, 這些選項包括:
  
- 遷移至 Project Online
    
- 遷移至較新的內部部署版本的 Project Server (最好是 Project Server 2019)。
    
|**為什麼我想要遷移至 Project Online？**|**為什麼我想要遷移至 Project Server 2019？**|
|:-----|:-----|
| 我有行動電話或遠端使用者。  <br/>  遷移內部部署伺服器的成本是很重要的問題 (硬體、軟體、時間和執行的工作, 等等)。  <br/>  遷移之後, 維護我的環境所需的成本是最重要的問題 (例如, 自動更新、保證的執行時間等等)。  <br/> | 商務規則限制我在雲端中運作我的業務。  <br/>  我需要控制環境的更新。  <br/> |
   
> [!NOTE]
> 如需從 Office 2010 伺服器移動的選項的詳細資訊, 請參閱可[協助您從 office 2010 伺服器和用戶端升級的資源](https://docs.microsoft.com/office365/enterprise/upgrade-from-office-2010-servers-and-products)。 請注意, Project Server 不支援混合式設定, 因為 Project Server 和 Project Online 無法共用相同的資源資料庫。 
  
## <a name="important-considerations-you-need-to-make-when-planning-to-migrate-from-project-server-2010"></a>規劃從 Project Server 2010 遷移時, 需注意的重要考慮

規劃從 Project Server 2010 遷移時, 您必須考慮下列事項:
  
- **從 Microsoft 解決方案供應商取得協助**-從 Project Server 2010 升級可能是一項挑戰, 需要進行很多準備和規劃。 如果您不是設定和設定 Project Server 2010, 則特別有挑戰性。 幸運的是, Microsoft 解決方案提供者可以在生活的情況下, 決定您是否打算將遷移至 Project Server 2019 或 Project Online。 您可以搜尋 Microsoft 解決方案提供者, 協助您在[Microsoft 解決方案提供者中心](https://go.microsoft.com/fwlink/p/?linkid=841249)進行遷移。 
    
- **規劃自訂**-請注意, 在 project server 2010 環境中使用的許多自訂專案在遷移至 project server 2019 或 project Online 時, 可能無法運作。 不同版本的 Project Server 架構以及支援的作業系統、資料庫伺服器及用戶端網頁瀏覽器之間有很大的差異, 可與更新的版本搭配使用。 針對您在新環境中所需的自訂進行測試或重建的計畫。 規劃升級時, 也是一種很好的機會, 可以確認在您向前移動時, 確實需要特定的自訂專案。 [在升級至 SharePoint 2013 期間建立目前自訂]( https://docs.microsoft.com/SharePoint/upgrade-and-update/create-a-plan-for-current-customizations-during-upgrade-to-sharepoint-2013)專案的計畫在升級時, 有一些關於評估和規劃目前自訂專案的極佳一般資訊。 
    
- **時間和耐心**升級的規劃、執行及測試需要很長的時間和精力, 尤其是當您升級至 Project Server 2019 時。 例如, 如果您要從 Project Server 2010 遷移至 Project Server 2019, 您必須先從 Project Server 2010 遷移至 Project Server 2013, 然後檢查資料, 然後在遷移至每個後續版本時執行相同的動作 (若為 Project)。伺服器 2016, 然後再到 Project Server 2019)。 您可能會想要與 Microsoft 解決方案提供者進行比較, 以將估計成本與他們的預估成本進行比較, 以達到所需的成本。 
    
## <a name="migrate-to-project-online"></a>遷移至 Project Online

如果您選擇從 Project Server 2010 遷移至 Project Online, 您可以執行下列動作以手動遷移專案計劃資料:
  
1. 將專案計劃從 Project Server 2010 儲存至。MPP 格式。
    
2. 使用 Project Professional 2016、Project Professional 2019 或 Project Online 桌面用戶端, 開啟每個 mpp 檔案, 然後儲存併發布到 Project Online。
    
您可以在 Project Online 中手動建立 PWA 設定 (例如, 重新建立任何所需的自訂欄位或企業行事曆)。 Microsoft 解決方案提供者也可以協助您。
  
主要資源:
  
|**資源**|**描述**|
|:-----|:-----|
|[Project Online 快速入門](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |如何設定和使用 Project Online。  <br/> |
|[Project Online 服務說明](https://go.microsoft.com/fwlink/p/?linkid=829088) <br/> |您可以使用之不同 Project Online 計畫的相關資訊。  <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>遷移至較新的內部部署版本的 Project Server

雖然我們極力相信您可以透過遷移至 Project Online 來達到最佳價值和使用者經驗, 我們也瞭解某些組織必須將專案資料保留在內部部署環境中。 如果您選擇將您的專案資料保留在內部部署中, 您可以將 Project Server 2010 環境遷移至 Project Server 2013、Project Server 2016 或 Project Server 2019。
  
如果您無法遷移至 Project Online, 建議您將升級至 Project Server 2019。 Project Server 2019 包含舊版 Project Server 隨附的功能和增強功能, 而且最符合 Project Online 的使用體驗 (雖然某些功能只能在 Project Online 中使用)。
  
完成每個遷移之後, 您應該檢查資料, 以確定其已成功遷移。
  
> [!NOTE]
> 如果您只想要將遷移至 Project Server 2013 (如果您僅限內部部署解決方案), 請務必注意, 您只需保留幾年以上的支援。 Project Server 2013 Service Pack 2 的支援日期結束日期為10/13/2023。 如需有關支援日期結束的詳細資訊, 請參閱[Microsoft 產品生命週期原則](https://go.microsoft.com/fwlink/p/?linkid=842066)。 
  
### <a name="how-do-i-migrate-to-project-server-2019"></a>如何遷移至 Project Server 2019？

Project Server 2010 與 Project Server 2019 之間的架構差異, 可防止直接的遷移路徑。 這表示, 您必須先將 Project Server 2010 資料移轉至 Project Server 的下一個後續版本, 才可升級至 Project Server 2019。
  
您必須執行下列步驟, 將 Project Server 2010 升級至 Project Server 2019:
  
1. 遷移至 Project Server 2013。
    
2. 從 Project 將2013升級至 Project Server 2016。
    
3. 從 Project Server 2016 遷移至 Project Server 2019。
    
完成每個遷移之後, 您應該檢查資料, 以確定其已成功遷移。
  
    
### <a name="step-1-migrate-to-project-server-2013"></a>步驟 1: 遷移至 Project Server 2013

將 Project Server 2010 資料移轉至 Project Server 2019 的第一步是先遷移至 Project Server 2013。 
  
若要完整瞭解從 Project Server 2010 升級至 Project Server 2013 所需的專案, 請參閱[升級至 Project server 2013](https://go.microsoft.com/fwlink/p/?linkid=841822)。 
  
主要資源:
  
|||
|:-----|:-----|
|[Project Server 2013 升級程式概述](https://go.microsoft.com/fwlink/p/?linkid=841822) <br/> |深入瞭解從 Project Server 2010 升級至 Project Server 2013 所需執行的作業。  <br/> |
|[規劃升級至 Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841823) <br/> |請查看從 Project Server 2010 升級至 Project Server 2013 時所需進行的規劃考慮, 包括系統需求。  <br/> |
   
[Project Server 2013 升級的新功能](https://go.microsoft.com/fwlink/p/?linkid=841824)會告訴您, 此版本升級的一些重要變更, 最明顯的是: 
  
- 沒有就地升級至 Project Server 2013。 資料庫附加方法是從 Project Server 2010 升級至 Project Server 2013 的唯一支援方法。
    
- 升級程式不只會將 Project Server 2010 資料轉換成 Project Server 2013 格式, 但也會將這四個 Project Server 2010 資料庫合併成單一 Project Web App 資料庫。
    
- SharePoint Server 2013 和 Project Server 2013 都會變更為先前版本的宣告式驗證。 如果您使用的是傳統驗證, 則必須考慮進行升級。 如需詳細資訊，請參閱＜[在 SharePoint 2013 中從傳統模式移轉至宣告式驗證]( https://docs.microsoft.com/sharepoint/upgrade-and-update/migrate-from-classic-mode-to-claims-based-authentication-in-sharepoint-2013)＞。
    
主要資源:
  
- [Project Server 2013 升級程序概觀](https://go.microsoft.com/fwlink/p/?linkid=841274)
    
- [升級您的資料庫與 Project Web App 網站集合 (Project Server 2013)](https://go.microsoft.com/fwlink/p/?linkid=841272)
    
- [Microsoft Project Server 升級程式圖](https://go.microsoft.com/fwlink/p/?linkid=841270)
    
- [以8個簡單的步驟進行的最佳資料庫整合、Project Server 2010 至2013遷移](https://go.microsoft.com/fwlink/p/?linkid=841271)
    
### <a name="step-2-migrate-to-project-server-2016"></a>步驟 2: 遷移至 Project Server 2016

在遷移至 Project Server 2013 並確認資料已成功遷移之後, 下一步是將您的資料移轉至 Project Server 2016。
  
若要完整瞭解從 Project Server 2013 升級至 Project Server 2016 所需的專案, 請參閱[升級至 Project server 2016](https://docs.microsoft.com/en-us/Project/upgrade-to-project-server-2016)。
  
主要資源:
  
|||
|:-----|:-----|
|[Project Server 2016 升級程序概觀](https://docs.microsoft.com/Project/overview-of-the-project-server-2016-upgrade-process) <br/> |深入瞭解從 Project Server 2013 升級至 Project Server 2016 所需執行的作業。  <br/> |
|[規劃升級到 Project Server 2016](https://docs.microsoft.com/Project/plan-for-upgrade-to-project-server-2016) <br/> |請查看從 Project Server 2013 升級至 Project Server 2016 時所需進行的規劃考慮。  <br/> |
   
[關於 Project Server 2016 升級, 您需要瞭解的事項](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2016#thingknow), 會告訴您, 升級到此版本的重要變更包括: 
  
- 當您建立要將 Project server 2013 資料移轉到其中的 Project Server 2016 環境時, 請注意, SharePoint Server 2016 中會包含 Project Server 2016 安裝檔案。 如需詳細資訊, 請參閱[Deploy Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841829)。
    
- Project Server 2016 中已被取代的資源計劃。 您的 Project Server 2013 資源計劃將會遷移至 Project Server 2016 和 Project Online 中的資源預訂。 如需詳細資訊, 請參閱[總覽: 資源預訂](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870)。 
    
### <a name="step-3-migrate-to-project-server-2019"></a>步驟 3: 遷移至 Project Server 2019

在遷移至 Project Server 2016 並確認資料已成功遷移之後, 下一步是將您的資料移轉至 Project Server 2019。
  
若要完整瞭解從 Project Server 2016 升級至 Project Server 2019 所需的專案, 請參閱[升級至 Project server 2019](https://docs.microsoft.com/en-us/Project/upgrade-to-project-server-2016)。
  
主要資源:
  
|||
|:-----|:-----|
|[Project Server 2019 升級程式概述](https://docs.microsoft.com/project/overview-of-the-project-server-2019-upgrade-process) <br/> |深入瞭解從 Project Server 2013 升級至 Project Server 2016 所需執行的作業。  <br/> |
|[規劃升級至 Project Server 2019](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2019) <br/> |請查看從 Project Server 2016 升級至 Project Server 2019 時所需進行的規劃考慮。  <br/> |
   
[關於 Project Server 2019 升級, 您需要瞭解的事項](https://go.microsoft.com/fwlink/p/?linkid=841827), 會告訴您, 升級到此版本的重要變更包括: 
  
- 升級程式會將您的資料從 Project Server 2016 資料庫移轉至 SharePoint Server 2019 內容資料庫。  Project Server 2019 將不再在 SharePoint Server 伺服器陣列中建立自己的 Project Server 資料庫。

- 升級之後, 請注意 Project Web App 中的數項變更。  如需這些內容的說明, 請參閱[Project Server 2019 的新功能](https://docs.microsoft.com/en-us/project/what-s-new-for-it-pros-in-project-server-2019#PWAChanges)。

  
其他資源:
  
- [Project Online 服務說明](https://go.microsoft.com/fwlink/p/?linkid=841280): 請參閱 project Server 2016 和 Project Online Premium 隨附的產品群組管理功能。
    
- [Microsoft Office Project 產品群組伺服器2010遷移指南](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>相關主題

[從 SharePoint 2010 升級](upgrade-from-sharepoint-2010.md)
  
[從 Office 2010 伺服器和用戶端升級](upgrade-from-office-2010-servers-and-products.md)
  

