---
title: Project Server 2010 的支援結束藍圖
ms.author: efrene
author: efrene
manager: pamg
ms.date: 10/12/2018
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
description: 在 2020 年 10 月 13、 支援至 Project Server 2010。使用本文現在規劃升級。
ms.openlocfilehash: bdfc4dd81dca7fe137be5780e54252eba961910f
ms.sourcegitcommit: e89b5306338ecdb40ad88efcf9cae3b8d5692924
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2018
ms.locfileid: "25549779"
---
# <a name="project-server-2010-end-of-support-roadmap"></a>Project Server 2010 結尾的支援藍圖

您需要考慮計劃移轉和支援的結束時的 Office 2010 伺服器和應用程式在 2010年。如果您目前使用 Project Server 2010，請注意它與這些相關的產品才有下列結尾的支援日期：
  
|**產品**|**支援日期的結尾**|
|:-----|:-----|
|Project Server 2010  <br/> |2020 年 10 月 13 日  <br/> |
|Project Server 2010  <br/> |2020 年 10 月 13 日  <br/> |
|Project 2010 標準版  <br/> |2020 年 10 月 13 日  <br/> |
|Project 2010 Professional  <br/> |2020 年 10 月 13 日  <br/> |
   
如需即將達到退休的 Office 2010 伺服器的詳細資訊，請參閱[從 Office 2010 伺服器與用戶端產品升級](https://docs.microsoft.com/office365/enterprise/plan-upgrade-previous-versions-office)。
  
## <a name="what-does-end-of-support-mean"></a>支援平均數何種實務結尾？

Project Server、 幾乎所有的 Microsoft 產品，例如有支援週期的期間我們提供的新功能、 修正錯誤、 安全性修正程式等等。此技術支援週期通常是一個工期 10 年度從產品的初始版本，日期的此技術支援週期的結尾就所謂的產品支援結束。由於 Project Server 2010 到達其結尾 2020 年 10 月 10 上支援 Microsoft 不再提供：
  
- 技術支援可能發生的問題。
    
- 錯誤修正的問題會發現及，可能會影響穩定性及可用性的伺服器。
    
- 安全性弱點的探索和可能會提出伺服器容易受到安全性缺口的修正。
    
- 時間的時區更新。
    
Project Server 2010 的安裝會繼續執行這個日期之後。但是，由於上述變更，我們強烈建議您盡移轉從 Project Server 2010。
  
## <a name="what-are-my-options"></a>我的選項為何？

如果您使用 Project Server 2010，則需要探索您要的遷移選項：
  
- 移轉至 Project Online
    
- 移轉至內部部署新版 Project Server (最好是 Project Server 2019)。
    
|**為什麼我偏好移轉至 Project Online**|**為什麼我偏好移轉至 Project Server 2019**|
|:-----|:-----|
| 我有行動使用者。  <br/>  移轉的成本是重要的考量 （硬體、 軟體、 時間及實作、 等等的能力。）。  <br/>  移轉之後，維持我環境的成本是重要的考量 （例如，自動更新、 保證執行時間、 等。）。  <br/> | 商務規則限制我操作我的業務雲端中。  <br/>  我的環境需要更新的控制。  <br/> |
   
> [!NOTE]
> 如需從您的 Office 2010 伺服器移動選項的詳細資訊，請參閱[資源以協助您升級從 Office 2010 伺服器和用戶端](https://docs.microsoft.com/office365/enterprise/upgrade-from-office-2010-servers-and-products)。記下 Project Server 不支援混合設定自 Project Server 與 Project Online 無法共用相同的資源集區。 
  
## <a name="important-considerations-you-need-to-make-when-planning-to-migrate-from-project-server-2010"></a>您必須制定規劃從 Project Server 2010 移轉時的重要考量

您必須從 Project Server 2010 移轉計劃時，請考慮下列：
  
- **取得說明從是 Microsoft 合作夥伴**-從 Project Server 2010 升級可以是項挑戰，並需要太多準備並規劃。若未來安裝及設定 Project Server 2010 原本一個它可以是特別面對。幸好有 Microsoft 之協力廠商可以開啟要執行這項作業的活是否您計劃移轉至 Project Server 2019 或 Project Online。您可以搜尋是 Microsoft 合作夥伴，可協助您移轉對[Microsoft 合作夥伴中心](https://go.microsoft.com/fwlink/p/?linkid=841249)。您可以藉由搜尋字詞*金色專案與產品組合管理*上提取設定的所有 Microsoft 合作夥伴與專業知識的專案清單。 
    
- **規劃自訂項目**-要知道的 Project Server 2010 環境中有 [使用的自訂許多可能無法運作時移轉至 Project Server 2019 或 Project Online。有重大差異 Project Server 架構中版本，以及所需的作業系統、 資料庫伺服器及用戶端網頁瀏覽器支援使用較新版本。備妥如何測試或重建自訂項目到新環境中需要有的計劃。規劃升級也會很好的機會確認如果特定自訂的確實需要為向前移動。[為建立目前自訂計畫升級到 SharePoint 2013 期間](https://go.microsoft.com/fwlink/p/?linkid=842061)有一些更好的一般資訊評估及規劃升級時您目前的自訂。 
    
- **時間和耐心**-規劃、 執行及測試升級所需的時間太多的時間和精力，特別是如果您要升級為 Project Server 2019。例如，如果您從 Project Server 2010 移轉至 Project Server 2019，您將首先需要從 Project Server 2010 移轉至 Project Server 2013]，然後檢查您的資料及再執行同樣的事情移轉至每個後續的版本 (Project伺服器 2016年然後 Project Server 2019）。您可能會想要檢查與 Microsoft 合作夥伴合作比較與它將花費其執行動作，並在新成本其評估您預估的成本。 
    
## <a name="migrate-to-project-online"></a>移轉至 Project Online

如果您選擇從 Project Server 2010 移轉至 Project Online，您可以執行下列 cmdlet 以手動方式將專案計劃資料移轉：
  
1. 從 Project Server 2010 to 儲存您的專案計劃。MPP 格式。
    
2. 使用 Project Professional 2016、 Project Professional 2019 或 Project Online 桌面用戶端，開啟每一個.mpp 檔案，然後儲存並發佈至 Project Online。
    
您可以手動在 Project Online 中建立 PWA 組態 （例如，重新建立任何所需的自訂欄位或企業行事曆）。Microsoft 協力廠商也可以協助您與此。
  
重要資源：
  
|**資源**|**描述**|
|:-----|:-----|
|[使用 Project Online 快速入門](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |如何安裝和使用 Project Online。  <br/> |
|[Project Online 服務說明](https://go.microsoft.com/fwlink/p/?linkid=829088) <br/> |您可以使用不同 Project Online 計劃的相關資訊。  <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>移轉至內部部署新版 Project Server

當我們強烈相信您可透過移轉至 Project Online 來獲得最佳的值與使用者經驗時，我們也瞭解某些組織需要保留在內部部署環境中的專案資料。如果您選擇要保留的專案資料內部，您可以在 Project Server 2013、 Project Server 2016、 或 Project Server 2019 移轉 Project Server 2010 環境。
  
我們建議您先移轉至 Project Server 2019 如果無法移轉至 Project Online。Project Server 2019 包括大部分的按鍵的功能和改進隨附於舊版的 Project Server 以及其最符合使用 Project Online 可用的經驗 （雖然某些功能只能在 Project Online）。
  
完成每個移轉之後, 就應該檢查您的資料以確定已順利移轉。
  
> [!NOTE]
> 如果您考慮只移轉至 Project Server 2013 如果您是限制在內部部署解決方案，務必請注意僅有幾個的多個多年的左的支援。Project Server 2013 Service Pack 2 的支援日期結尾是 10/13/2023年。如需支援日期結尾的詳細資訊，請參閱[Microsoft 產品生命週期原則](https://go.microsoft.com/fwlink/p/?linkid=842066)。 
  
### <a name="how-do-i-migrate-to-project-server-2019"></a>如何移轉至 Project Server 2019？

Project Server 2010 與 Project Server 2019 架構的差異禁止直接的移轉路徑。這表示您必須等到升級至 Project Server 2019 移轉至 Project Server 的下一個後續版本的 Project Server 2010 資料。
  
您必須執行下列 cmdlet 以升級至 Project Server 2019：
  
1. 步驟 1： 將資料從 Project Server 2010 移轉到 Project Server 2013。
    
2. 步驟 2： 將資料從 Project 做 2013年移轉至 Project Server 2016。
    
3. 步驟 3： 將資料從 Project Server 2016 移轉至 Project Server 2019。
    
完成每個移轉之後, 就應該檢查您的資料以確定已順利移轉。
  
    
### <a name="step-1-migrate-to-project-server-2013"></a>步驟 1： 移轉至 Project Server 2013

Project Server 2010 資料移轉至 Project Server 2019 您第一個步驟是先移轉至 Project Server 2013。 
  
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
    
### <a name="step-2-migrate-to-project-server-2016"></a>步驟 2 移轉至 Project Server 2016

移轉至 Project Server 2013 確認資料已順利移轉之後下, 一步是將資料移轉至 Project Server 2016。
  
針對您要從 Project Server 2013 升級至 Project Server 2016 執行動作的完整了解，請參閱 ＜ [Upgrade to Project Server 2016](https://docs.microsoft.com/en-us/Project/upgrade-to-project-server-2016)內容組。
  
重要資源：
  
|**資源**|**描述**|
|:-----|:-----|
|[Project Server 2016 升級程序概觀](https://docs.microsoft.com/Project/overview-of-the-project-server-2016-upgrade-process) <br/> |取得您要從 Project Server 2013 升級至 Project Server 2016 執行動作的概略了解。  <br/> |
|[規劃升級到 Project Server 2016](https://docs.microsoft.com/Project/plan-for-upgrade-to-project-server-2016) <br/> |查看您需要從 Project Server 2013 升級至 Project Server 2016 時進行的規劃考量。  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>了解升級為這個版本的事項

[您必須了的解關於 Project Server 2016 升級](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2016#thingknow)會告訴您一些重要變更升級此版本中，其中包括： 
  
- 當您建立會移轉 Project Server 2013 資料的 Project Server 2016 環境時，請注意的 Project Server 2016 安裝檔案都包含在 SharePoint Server 2016。如需詳細資訊，請參閱 ＜[部署 Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841829)。
    
- 資源計劃的 Project Server 2016 中已被取代。Project Server 2013 資源計劃將移轉至資源投入在 Project Server 2016 和 Project Online。請參閱[概觀 （英文)： 資源投入](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870)如需詳細資訊。 
    
### <a name="step-3-migrate-to-project-server-2019"></a>步驟 3 移轉至 Project Server 2019

移轉至 Project Server 2016 確認資料已順利移轉之後下, 一步是將資料移轉至 Project Server 2019。
  
針對您要從 Project Server 2016 升級至 Project Server 2019 執行動作的完整了解，請參閱 ＜ [Upgrade to Project Server 2019](https://docs.microsoft.com/en-us/Project/upgrade-to-project-server-2016)內容組。
  
重要資源：
  
|**資源**|**描述**|
|:-----|:-----|
|[Project Server 2019 概觀升級程序](https://docs.microsoft.com/project/overview-of-the-project-server-2019-upgrade-process) <br/> |取得您要從 Project Server 2013 升級至 Project Server 2016 執行動作的概略了解。  <br/> |
|[規劃升級至 Project Server 2019](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2019) <br/> |查看您需要從 Project Server 2016 升級至 Project Server 2019 時進行的規劃考量。  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>了解升級為這個版本的事項

[您必須了的解關於 Project Server 2019 升級](https://go.microsoft.com/fwlink/p/?linkid=841827)會告訴您一些重要變更升級此版本中，其中包括： 
  
- 升級程序會將資料從 Project Server 2016 資料庫移轉至 SharePoint Server 2019 內容資料庫。 Project Server 2019 不長便會建立擁有 SharePoint 伺服器陣列中的 Project Server 資料庫。

- 升級後，請注意的 Project Web App 中的數項變更。 如需說明這些，請參閱 ＜ [What's new in Project Server 2019](https://docs.microsoft.com/en-us/project/what-s-new-for-it-pros-in-project-server-2019#PWAChanges)。


## <a name="migrate-from-portfolio-server-2010"></a>從 Portfolio Server 2010 移轉

Project Portfolio Server 2010 與 Project Server 2010 使用的產品組合策略、 優先順序以及最佳化。Project Portfolio Server 沒有其他版本所建立此版本後。不過，產品組合管理功能可用更新的 Project Server 版本及 Project Online 的高階版本中。Project Portfolio Server 2010 的資料無法移轉至其中一個。例如業務驅策因素的資料將需要重新建立。
  
其他資源：
  
- [Project Online 服務說明](https://go.microsoft.com/fwlink/p/?linkid=841280)： 請參閱包含在 Project Server 2016 和 Project Online 進階版的產品組合管理功能。
    
- [Microsoft Office Project Portfolio Server 2010 的移轉指南](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>相關主題

[從 SharePoint 2010 升級](upgrade-from-sharepoint-2010.md)
  
[可協助您升級從 Office 2010 伺服器和用戶端的資源](upgrade-from-office-2010-servers-and-products.md)
  

