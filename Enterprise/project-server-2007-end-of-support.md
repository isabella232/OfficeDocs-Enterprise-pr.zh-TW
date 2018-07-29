---
title: Project Server 2007 終止支援藍圖
ms.author: efrene
author: efrene
manager: laurawi
ms.date: 1/31/2018
ms.audience: ITPro
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
ms.assetid: d379018f-72b7-4284-b40a-6c23c8ae38fe
description: 在 2017 年 10 月 10、 支援的結束 Project Server 2007、 Project Portfolio Server 和 Project 2007。使用本文現在規劃升級。
ms.openlocfilehash: 5b2fb194d4819b5427cb2844a5189b2b03753800
ms.sourcegitcommit: a9c84d02e94c99ff6b1099b4a9ae695be08210e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2018
ms.locfileid: "21169895"
---
# <a name="project-server-2007-end-of-support-roadmap"></a>Project Server 2007 終止支援藍圖

支援的結束時 Office 2007 伺服器和應用程式中 2017，而您需要考慮計劃移轉。如果您目前使用 Project Server 2007，請注意其及其他相關的產品會有下列支援結束日期：
  
|**產品**|**支援日期的結尾**|
|:-----|:-----|
|Project Server 2007  <br/> |2017 年 10 月 10 日  <br/> |
|Project Portfolio Server 2007  <br/> |2017 年 10 月 10 日  <br/> |
|Project 2007 標準版  <br/> |2017 年 10 月 10 日  <br/> |
|Project 2007 專業版  <br/> |2017 年 10 月 10 日  <br/> |
   
如需即將達到退休的 Office 2007 伺服器的詳細資訊，請參閱[從 Office 2007 的伺服器與用戶端產品升級](upgrade-from-office-2007-servers-and-products.md)。
  
## <a name="what-does-end-of-support-mean"></a>支援平均數何種實務結尾？

Project Server、 幾乎所有的 Microsoft 產品，例如有支援週期的期間我們提供的新功能、 修正錯誤、 安全性修正程式等等。此技術支援週期通常是一個工期 10 年度從產品的初始版本，日期的此技術支援週期的結尾就所謂的產品支援結束。Project Server 2007 到達其結尾支援 2017 年 10 月 10，因為 Microsoft 不再提供：
  
- 技術支援可能發生的問題。
    
- 錯誤修正的問題會發現及，可能會影響穩定性及可用性的伺服器。
    
- 安全性弱點的探索和可能會提出伺服器容易受到安全性缺口的修正。
    
- 時間的時區更新。
    
Project Server 2007 的安裝會繼續執行這個日期之後。但是，由於上述變更，我們強烈建議您盡移轉從 Project Server 2007。
  
## <a name="what-are-my-options"></a>我的選項為何？

如果您使用 Project Server 2007，則需要探索您要的遷移選項：
  
- 移轉至 Project Online
    
- 移轉至內部部署新版 Project Server (最好是 Project Server 2016)。
    
|**為什麼我偏好移轉至 Project Online**|**為什麼我偏好移轉至 Project Server 2016**|
|:-----|:-----|
| 我有行動使用者。  <br/>  移轉的成本是重要的考量 （硬體、 軟體、 時間及實作、 等等的能力。）。  <br/>  移轉之後，維持我環境的成本是重要的考量 （例如，自動更新、 保證執行時間、 等。）。  <br/> | 商務規則限制我操作我的業務雲端中。  <br/>  我的環境需要更新的控制。  <br/> |
   
> [!NOTE]
> 如需從您的 Office 2007 伺服器移動選項的詳細資訊，請參閱[資源以協助您升級從 Office 2007 的伺服器和用戶端](upgrade-from-office-2007-servers-and-products.md)。記下 Project Server 不支援混合設定自 Project Server 與 Project Online 無法共用相同的資源集區。 
  
## <a name="important-considerations-you-need-to-make-when-planning-to-migrate-from-project-server-2007"></a>您必須制定規劃從 Project Server 2007 移轉時的重要考量

您必須從 Project Server 2007 移轉計劃時，請考慮下列：
  
- **取得說明從是 Microsoft 合作夥伴**-從 Project Server 2007 升級可以挑戰，並要求許多的準備與規劃。若未安裝及設定 Project Server 2007 原本一個它可以是特別具挑戰性。幸好有 Microsoft 之協力廠商可以開啟要執行這項作業的活是否您計劃移轉至 Project Server 2016 或 Project Online。您可以搜尋是 Microsoft 合作夥伴，可協助您移轉對[Microsoft 合作夥伴中心](https://go.microsoft.com/fwlink/p/?linkid=841249)。您可以藉由搜尋字詞*金色專案與產品組合管理*上提取設定的所有 Microsoft 合作夥伴與專業知識的專案清單。 
    
- **規劃自訂項目**-要知道的 Project Server 2007 環境中有 [使用的自訂許多可能無法運作時移轉至 Project Server 2016 或 Project Online。有重大差異 Project Server 架構中版本，以及所需的作業系統、 資料庫伺服器及用戶端網頁瀏覽器支援使用較新版本。備妥如何測試或重建自訂項目到新環境中需要有的計劃。規劃升級也會很好的機會確認如果特定自訂的確實需要為向前移動。[為建立目前自訂計畫升級到 SharePoint 2013 期間](https://go.microsoft.com/fwlink/p/?linkid=842061)有一些更好的一般資訊評估及規劃升級時您目前的自訂。 
    
- **時間和耐心**-規劃、 執行及測試升級所需的時間許多的時間和精力，特別是如果您要升級為 Project Server 2016。例如，如果您從 Project Server 2007 移轉至 Project Server 2016、 將首先需要從 Project Server 2007 移轉至 Project Server 2010]，然後檢查您的資料並移轉至每個後續的版本時再執行同樣的事情。您可能會想要檢查與 Microsoft 合作夥伴合作比較與它將花費其執行動作，並在新成本其評估您成本。 
    
## <a name="migrate-to-project-online"></a>移轉至 Project Online

如果您選擇從 Project Server 2007 移轉至 Project Online，您可以執行下列 cmdlet 以手動方式將專案計劃資料移轉：
  
1. 從 Project Server 2003 以儲存您的專案計劃。MPP 格式。
    
2. 使用 Project Professional 2013、 Project Professional 2016、 或 Project Online 桌面用戶端，開啟每一個.mpp 檔案，然後儲存並發佈至 Project Online。
    
您可以手動在 Project Online 中建立 PWA 組態 （例如，重新建立任何所需的自訂欄位或企業行事曆）。Microsoft 協力廠商也可以協助您與此。
  
重要資源：
  
|**資源**|**描述**|
|:-----|:-----|
|[使用 Project Online 快速入門](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |如何安裝和使用 Project Online。  <br/> |
|[Project Online 服務說明](https://go.microsoft.com/fwlink/p/?linkid=829088) <br/> |您可以使用不同 Project Online 計劃的相關資訊。  <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>移轉至內部部署新版 Project Server

當我們強烈相信您可透過移轉至 Project Online 來獲得最佳的值與使用者經驗時，我們也瞭解某些組織需要保留在內部部署環境中的專案資料。如果您選擇要保留的專案資料內部，您可以將 Project Server 2007 環境移轉至 Project Server 2010、 Project Server 2013 或 Project Server 2016 中。
  
我們建議您先移轉至 Project Server 2016 如果無法移轉至 Project Online。Project Server 2016 包括所有功能和改進隨附於舊版的 Project Server 以及其最符合使用 Project Online 可用的經驗 （雖然某些功能只能在 Project Online）。
  
完成每個移轉之後, 就應該檢查您的資料以確定已順利移轉。
  
> [!NOTE]
> 如果您考慮只移轉至 Project Server 2010 如果您是限制在內部部署解決方案，務必請注意僅有幾個的多個多年的左的支援。Project Server 2010 Service Pack 2 的支援日期結尾是 10/13/2020年。如需支援日期結尾的詳細資訊，請參閱[Microsoft 產品生命週期原則](https://go.microsoft.com/fwlink/p/?linkid=842066)。 
  
### <a name="how-do-i-migrate-to-project-server-2016"></a>如何移轉至 Project Server 2016？

Project Server 2007 與 Project Server 2016 架構的差異禁止直接的移轉路徑。這表示您必須等到升級至 Project Server 2016 移轉至 Project Server 的下一個後續版本的 Project Server 2007 資料。
  
您必須執行下列 cmdlet 以升級至 Project Server 2016：
  
1. 步驟 1： ＜ Migrate from Project Server 2007 升級至 Project Server 2010。
    
2. 步驟 2： ＜ Migrate from project Server 2013 的 Project 服務 2010年。
    
3. 步驟 3： ＜ Migrate from Project Server 2013 升級至 Project Server 2016。
    
完成每個移轉之後, 就應該檢查您的資料以確定已順利移轉。
  
### <a name="step-1-migrate-from-project-server-2007-to-project-server-2010"></a>步驟 1： 移轉 Project server 2007 與 Project Server 2010

針對您要從 Project Server 2007 升級至 Project Server 2010 執行動作的完整了解，請參閱 TechNet 上的[升級至 Project Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841812)的內容組。 
  
重要資源：
  
|**資源**|**描述**|
|:-----|:-----|
|[Project Server 2010 升級概觀 （英文)](https://go.microsoft.com/fwlink/p/?linkid=841813) <br/> |取得您需要執行從 Project Server 2007 升級至 Project Server 2010 的概略了解。  <br/> |
|[規劃升級至 Project Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841815) <br/> |查看規劃您需要進行從 Project Server 2007 升級至 Project Server 2010，包括系統需求時的考量。  <br/> |
   
#### <a name="how-do-i-upgrade"></a>我該如何升級？

雖然在[升級至 Project Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841812)內容集可以找到如何進行升級的詳細資訊，請務必了解有兩種不同的方法可用來升級： 
  
- **資料庫附加升級：** 此方法僅升級您的環境，並不的組態設定的內容。如果您要從僅支援 32 位元作業系統的硬體上部署 Office Project Server 2007 升級，是必要。有兩種類型的資料庫附加升級方法： 
    
  - **資料庫附加完整升級**-移轉 Office Project Server 2007 資料庫中儲存的專案資料加上儲存的 SharePoint 內容資料庫的 Microsoft Project Web App (PWA) 網站資料。 
    
  - **資料庫附加核心升級**-移轉只能在 Project Server 資料庫中儲存的專案資料。 
    
- **就地升級**： 在現有的硬體，以固定的順序升級伺服器陣列及伺服器陣列上的所有內容的組態資料。啟動時在就地升級程序，安裝程式會離線整個伺服器陣列與網站與 Microsoft Project Web App 網站已無法使用直到完成升級，然後設定重新啟動伺服器。在您開始就地升級後，您不能暫停升級或回復至先前的版本。強烈建議將實際執行環境的鏡像的圖像並執行就地升級至此環境中，並不實際執行環境。 
    
其他資源：
  
- [SuperFlow Microsoft Project Server 2010 升級](https://go.microsoft.com/fwlink/p/?linkid=841277)
    
- [從 project Server 2010 的 Project Server 2007 移轉](https://go.microsoft.com/fwlink/p/?linkid=841278)
    
- [升級 Project Web App 網頁組件的考量](https://go.microsoft.com/fwlink/p/?linkid=841276)
    
- [Project 軟體開發套件 (SDK)](https://go.microsoft.com/fwlink/p/?linkid=841275)
    
### <a name="step-2-migrate-to-project-server-2013"></a>步驟 2： 移轉至 Project Server 2013

移轉至 Project Server 2010 確認資料已順利移轉之後下, 一步是將資料移轉至 Project Server 2013。
  
針對您要從 Project Server 2010 升級至 Project Server 2013 執行動作的完整了解，請參閱 TechNet 上的[升級至 Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841822)的內容組。 
  
重要資源：
  
|**資源**|**描述**|
|:-----|:-----|
|[概觀 （英文） 的 Project Server 2013 升級程序](https://go.microsoft.com/fwlink/p/?linkid=841822) <br/> |取得您需要執行從 Project Server 2010 升級至 Project Server 2013 的概略了解。  <br/> |
|[規劃升級至 Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841823) <br/> |查看規劃的考量您必須制定時從 Project Server 2010 升級至 Project Server 2013，包括系統需求。  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>了解升級為這個版本的事項

[在 Project Server 2013 升級的新功能](https://go.microsoft.com/fwlink/p/?linkid=841824)會告訴您在此版本最顯著正在升級的一些重要變更： 
  
- 沒有在就地升級為 Project Server 2013。資料庫附加方法是從 Project Server 2010 升級至 Project Server 2013 的唯一支援的方法。
    
- 升級程序不就將只轉換 Project Server 2010 資料至 Project Server 2013 格式，但也會合併成一個 Project Web App 資料庫的四個 Project Server 2010 資料庫。
    
- SharePoint Server 2013 和 Project Server 2013 變更為宣告式驗證從舊的版本。您必須進行升級如果您使用傳統驗證時的考量。如需詳細資訊，請參閱[從傳統模式為宣告式驗證在 SharePoint 2013 中的移轉](https://go.microsoft.com/fwlink/p/?linkid=841825)。
    
其他資源：
  
- [升級到 Project Server 2013 的升級程序概觀](https://go.microsoft.com/fwlink/p/?linkid=841274)
    
- [升級您的資料庫與 Project Web App 網站集合 (Project Server 2013)](https://go.microsoft.com/fwlink/p/?linkid=841272)
    
- [Microsoft Project Server 升級程序圖](https://go.microsoft.com/fwlink/p/?linkid=841270)
    
- [更好的資料庫合併、 Project Server 2010 以 2013年移轉 8 簡單的步驟](https://go.microsoft.com/fwlink/p/?linkid=841271)
    
### <a name="step-3-migrate-to-project-server-2016"></a>步驟 3： 移轉至 Project Server 2016

移轉至 Project Server 2013 確認資料已順利移轉之後下, 一步是將資料移轉至 Project Server 2016。
  
您要從 Project Server 2013 升級至 Project Server 2016 執行動作的完整了解，請參閱 TechNet 上設定 Project Server 2016 內容升級。
  
重要資源：
  
|**資源**|**描述**|
|:-----|:-----|
|[Project Server 2016 升級程序概觀](https://go.microsoft.com/fwlink/p/?linkid=841260) <br/> |取得您要從 Project Server 2013 升級至 Project Server 2016 執行動作的概略了解。  <br/> |
|[規劃升級到 Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841826) <br/> |查看規劃您需要進行從 Project Server 2013 升級至 Project Server 2016，包括時的考量。  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>了解升級為這個版本的事項

[您必須了的解關於 Project Server 2016 升級](https://go.microsoft.com/fwlink/p/?linkid=841827)會告訴您一些重要變更升級此版本中，其中包括： 
  
- 當您建立會移轉 Project Server 2013 資料的 Project Server 2016 環境時，請注意的 Project Server 2016 安裝檔案都包含在 SharePoint Server 2016。如需詳細資訊，請參閱 ＜[部署 Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841829)。
    
- 資源計劃的 Project Server 2016 中已被取代。Project Server 2013 資源計劃將移轉至資源投入在 Project Server 2016 和 Project Online。請參閱[概觀 （英文)： 資源投入](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870)如需詳細資訊。 
    
## <a name="migrate-from-portfolio-server-2007"></a>從 Portfolio Server 2007 移轉

Project Portfolio Server 2007 與 Project Server 2007 搭配使用的產品組合策略、 優先順序以及最佳化。Project Portfolio Server 沒有其他版本所建立此版本後。不過，產品組合管理功能可用的 Project Server 2016 和 Project Online 的 Premium 版本。Project Portfolio Server 2007 的資料無法移轉至其中一個。例如業務驅策因素的資料將需要重新建立。
  
其他資源：
  
- [Project Online 服務說明](https://go.microsoft.com/fwlink/p/?linkid=841280)： 請參閱包含在 Project Server 2016 和 Project Online 進階版的產品組合管理功能。
    
- [Microsoft Office Project Portfolio Server 2007 移轉指南](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>相關主題

[SharePoint Server 2007 支援藍圖結束](sharepoint-2007-end-of-support.md)
  
[可協助您升級從 Office 2007 的伺服器和用戶端的資源](upgrade-from-office-2007-servers-and-products.md)
  

