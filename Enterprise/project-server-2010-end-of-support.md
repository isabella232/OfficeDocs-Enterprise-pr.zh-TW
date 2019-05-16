---
title: Project Server 2010 結束的支援藍圖
ms.author: efrene
author: efrene
manager: pamg
ms.date: 10/12/2018
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
description: 在 2020 年 10 月 13，支援結束 for Project Server 2010。 使用本文以規劃升級現在。
ms.openlocfilehash: 1c8e6eab592e2974c334367e7931395e867ad97e
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071039"
---
# <a name="project-server-2010-end-of-support-roadmap"></a>Project Server 2010 終止支援藍圖

支援的結束時 Office 2010 伺服器和應用程式在 2010 中，而您需要考慮遷移計劃。 如果您目前使用 Project Server 2010，請注意，它和其他相關的產品會有下列結尾支援日期：
  
|**產品**|**支援日期的結尾**|
|:-----|:-----|
|Project Server 2010  <br/> |2020 年 10 月 13 日  <br/> |
|Project Portfolio Server 2010  <br/> |2020 年 10 月 13 日  <br/> |
|Project 2010 標準版  <br/> |2020 年 10 月 13 日  <br/> |
|Project 2010 Professional  <br/> |2020 年 10 月 13 日  <br/> |
   
如需有關 Office 2010 伺服器達到淘汰網站的詳細資訊，請參閱[從 Office 2010 伺服器和用戶端產品升級](https://docs.microsoft.com/office365/enterprise/plan-upgrade-previous-versions-office)。
  
## <a name="what-does-end-of-support-mean"></a>支援平均數的哪些並結束？

Project Server，像是幾乎所有的 Microsoft 產品中，有支援週期，我們會提供新功能、 錯誤修正程式、 安全性修正程式、 等等。 此生命週期通常會持續 10 年起的產品的初始版本，與此生命週期結束稱為 「 支援的產品的結尾。 因為 Project Server 2010 已達到其結尾支援 2020 年 10 月 10，Microsoft 將不再提供：
  
- 技術支援，可能發生的問題。
    
- 錯誤修正問題，會發現及，可能會影響 exchange 的穩定性與伺服器的可用性。
    
- 安全性問題修正所發現和，可能會讓伺服器受到安全性弱點的弱點。
    
- 時間的時區更新。
    
Project Server 2010 安裝會繼續執行此日期之後。 不過，由於上述的變更，我們強烈建議您儘速移轉從 Project Server 2010。
  
## <a name="what-are-my-options"></a>我的選項為何？

如果您正在使用 Project Server 2010，您需要瀏覽您的遷移選項，也就是：
  
- 移轉至 Project Online
    
- 移轉至較新的內部部署版本的 Project Server (最好是 Project Server 2019)。
    
|**為什麼要移轉至 Project Online**|**為什麼要移轉至 Project Server 2019**|
|:-----|:-----|
| 我有行動使用者。  <br/>  若要移轉的成本是重要的考量 （硬體、 軟體、 時間和精力實作，等等。）。  <br/>  在移轉之後，維持我環境的成本是重要的考量 （例如，自動更新，保證上線時間等等。）。  <br/> | 商務規則限制我操作我公司在雲端中。  <br/>  我需要更新的控制我的環境。  <br/> |
   
> [!NOTE]
> 如需從您的 Office 2010 伺服器移動選項的詳細資訊，請參閱 <<c0>資源可以幫助您升級從 Office 2010 伺服器和用戶端。 請注意，Project Server 不支援混合式組態自 Project Server 和 Project Online 無法共用相同的資源集區。 
  
## <a name="important-considerations-you-need-to-make-when-planning-to-migrate-from-project-server-2010"></a>您必須先從 Project Server 2010 移轉計劃時的重要考量

您必須從 Project Server 2010 移轉計劃時，請考慮下列：
  
- **取得從 Microsoft 合作夥伴的協助**-從 Project Server 2010 升級可以是一項挑戰，需要更準備並規劃。 如果您未安裝及設定 Project Server 2010 原本的一個，它可以是特別具挑戰性。 幸好，有 Microsoft 合作夥伴可以轉至這麼做什麼的是否打算移轉至 Project Server 2019 或 Project Online。 您可以搜尋 Microsoft 合作夥伴來協助您的[Microsoft 合作夥伴中心](https://go.microsoft.com/fwlink/p/?linkid=841249)上的移轉。 您可以藉由搜尋字詞*金色專案與產品組合管理*提取專業知識與所有的 Microsoft 合作夥伴，專案中的清單。 
    
- **規劃您的自訂內容**-請注意，您有 Project Server 2010 環境中的 [使用自訂的許多可能無法運作移轉至 Project Server 2019 或 Project Online 時。 有之間版本，以及必要的作業系統、 資料庫伺服器和用戶端網頁瀏覽器支援以使用較新版本的 Project Server 架構的重大差異。 有計劃中有關如何測試或重建自訂項目，視需要在新環境中的位置。 規劃升級也會是很好的機會，若要確認您中向前移動，是否確實需要特定的自訂。 [建立升級到 SharePoint 2013 期間的現有自訂計畫](https://go.microsoft.com/fwlink/p/?linkid=842061)有一些很棒的一般資訊評估和規劃升級時您目前的自訂項目。 
    
- **時間和耐心**-升級規劃、 執行和測試需要多時間和精力，尤其是如果您要升級為 Project Server 2019。 例如，如果您從 Project Server 2010 移轉至 Project Server 2019，您將首先必須從 Project Server 2010 移轉至 Project Server 2013，然後再檢查您的資料，並再執行相同的動作，當您移轉至每個後續版本 （專案Server 2016，然後 Project Server 2019）。 您可能想要檢查與 Microsoft 合作夥伴比較您的估計的成本，以及其預估它將需要花費多少時間為他們這樣做，並在什麼成本。 
    
## <a name="migrate-to-project-online"></a>移轉至 Project Online

如果您選擇從 Project Server 2010 移轉至 Project Online，您可以執行下列命令以手動方式移轉您的專案計劃資料：
  
1. 從 Project Server 2010 以儲存您的專案計劃。MPP 格式。
    
2. 使用 Project Professional 2016、 Project 專業版 2019年或 Project Online 桌面用戶端，請開啟每個.mpp 檔案，然後儲存並將它發佈至 Project Online。
    
您可以手動在 Project Online 中建立 PWA 組態 （例如，重新建立任何所需的自訂欄位或企業行事曆）。 Microsoft 合作夥伴也可以協助您使用這個。
  
重要資源：
  
|**資源**|**描述**|
|:-----|:-----|
|[Project Online 快速入門](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |如何安裝及使用 Project Online。  <br/> |
|[Project Online 服務說明](https://go.microsoft.com/fwlink/p/?linkid=829088) <br/> |您可以使用不同 Project Online 計劃的相關資訊。  <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>移轉至較新的內部部署版本的 Project Server

雖然我們強烈相信您可透過移轉至 Project Online 來達到最佳的值與使用者經驗，我們也了解某些組織需要保留在內部部署環境中的專案資料。 如果您選擇要保留的專案資料內部，您可以將 Project Server 2010 環境移轉至 Project Server 2013、 Project Server 2016 或 Project Server 2019。
  
我們建議您移轉至 Project Server 2019，如果您不能將移轉至 Project Online。 Project Server 2019 包含大部分的索引鍵的功能和進步隨附於舊版的 Project Server，以及其最符合使用 Project Online 可用的體驗 （雖然某些功能都只能在 Project Online）。
  
完成後每個移轉，您應該檢查您的資料，請確定已順利移轉。
  
> [!NOTE]
> 如果您考慮只移轉至 Project Server 2013 如果您有內部部署解決方案，，務必請注意，僅有多個多年的左的支援。 Project Server 2013 Service Pack 2 的支援日期結尾是 10/13/2023年。 如需有關支援日期結尾的詳細資訊，請參閱 < <b0>Microsoft 產品生命週期原則</b0>。 
  
### <a name="how-do-i-migrate-to-project-server-2019"></a>如何移轉至 Project Server 2019？

Project Server 2010 與 Project Server 2019 架構的差異，可防止直接的移轉路徑。 這表示您想要將 Project Server 2010 資料移轉至 Project Server 的下一個後續版本中，直到您升級至 Project Server 2019。
  
您必須執行升級至 Project Server 2019 下列動作：
  
1. 步驟 1： 會將資料從 Project Server 2010 移轉至 Project Server 2013。
    
2. 步驟 2： 會將您的資料從 Project 做 2013年移轉至 Project Server 2016。
    
3. 步驟 3： 會將資料從 Project Server 2016 移轉至 Project Server 2019。
    
完成後每個移轉，您應該檢查您的資料，請確定已順利移轉。
  
    
### <a name="step-1-migrate-to-project-server-2013"></a>步驟 1： 移轉至 Project Server 2013

Project Server 2010 資料移轉至 Project Server 2019 的第一步是將第一次移轉至 Project Server 2013。 
  
針對您要從 Project Server 2010 升級至 Project Server 2013 做全面了解，請參閱 TechNet 上的[升級為 Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841822)的內容集。 
  
重要資源：
  
|**資源**|**描述**|
|:-----|:-----|
|[概觀 Project Server 2013 升級程序](https://go.microsoft.com/fwlink/p/?linkid=841822) <br/> |取得您要從 Project Server 2010 升級至 Project Server 2013 做概略了解。  <br/> |
|[規劃升級至 Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841823) <br/> |看一下規劃您需要從 Project Server 2010 升級至 Project Server 2013，包括系統需求的必需考量。  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>關於升級至這個版本的相關須知

[What's new in Project Server 2013 升級](https://go.microsoft.com/fwlink/p/?linkid=841824)，告訴您針對此版本中，最重要的正在升級的一些重要變更： 
  
- 沒有為 Project Server 2013 在就地升級。 資料庫附加方法是從 Project Server 2010 升級至 Project Server 2013 的唯一支援的方法。
    
- 升級程序不會只將轉換您的 Project Server 2010 資料至 Project Server 2013 的格式，但也會合併成一個 Project Web App 資料庫的四個 Project Server 2010 資料庫。
    
- SharePoint Server 2013 和 Project Server 2013 變更為宣告式驗證從先前版本。 您必須升級如果您使用傳統驗證必需考量。 如需詳細資訊，請參閱＜[在 SharePoint 2013 中從傳統模式移轉至宣告式驗證](https://go.microsoft.com/fwlink/p/?linkid=841825)＞。
    
其他資源：
  
- [Project Server 2013 升級程序概觀](https://go.microsoft.com/fwlink/p/?linkid=841274)
    
- [升級您的資料庫與 Project Web App 網站集合 (Project Server 2013)](https://go.microsoft.com/fwlink/p/?linkid=841272)
    
- [Microsoft Project Server 升級程序圖](https://go.microsoft.com/fwlink/p/?linkid=841270)
    
- [絕佳資料庫合併彙算，8 簡單的步驟中的 Project Server 2010 到 2013年移轉](https://go.microsoft.com/fwlink/p/?linkid=841271)
    
### <a name="step-2-migrate-to-project-server-2016"></a>步驟 2 移轉至 Project Server 2016

移轉至 Project Server 2013，並確認已順利移轉您的資料之後, 的下一個步驟是將您的資料移轉至 Project Server 2016。
  
如您所要從 Project Server 2013 升級至 Project Server 2016 做全面了解，請參閱 <<c0>升級到 Project Server 2016的內容集。
  
重要資源：
  
|**資源**|**描述**|
|:-----|:-----|
|[Project Server 2016 升級程序概觀](https://docs.microsoft.com/Project/overview-of-the-project-server-2016-upgrade-process) <br/> |取得您要從 Project Server 2013 升級至 Project Server 2016 做概略了解。  <br/> |
|[規劃升級到 Project Server 2016](https://docs.microsoft.com/Project/plan-for-upgrade-to-project-server-2016) <br/> |查看您需要進行從 Project Server 2013 升級到 Project Server 2016 時的規劃考量。  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>關於升級至這個版本的相關須知

[您必須了的解關於 Project Server 2016 升級](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2016#thingknow)，告訴您升級此版本中，其中包含一些重要變更： 
  
- 當您建立您要將移轉 Project Server 2013 資料的 Project Server 2016 環境時，請注意在 SharePoint Server 2016 中包含的 Project Server 2016 安裝檔案。 如需詳細資訊，請參閱 <<c0>部署 Project Server 2016。
    
- 資源計劃是 Project Server 2016 中已被取代。 Project Server 2013 資源計劃將會移轉至資源預訂的 Project Server 2016 和 Project Online 中。 請參閱[概觀： 資源預訂](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870)如需詳細資訊。 
    
### <a name="step-3-migrate-to-project-server-2019"></a>步驟 3 移轉至 Project Server 2019

移轉至 Project Server 2016，並確認已順利移轉您的資料之後, 的下一個步驟是將您的資料移轉至 Project Server 2019。
  
如您所要從 Project Server 2016 升級至 Project Server 2019 做全面了解，請參閱 <<c0>升級至 Project Server 2019的內容集。
  
重要資源：
  
|**資源**|**描述**|
|:-----|:-----|
|[概觀 Project Server 2019 升級程序](https://docs.microsoft.com/project/overview-of-the-project-server-2019-upgrade-process) <br/> |取得您要從 Project Server 2013 升級至 Project Server 2016 做概略了解。  <br/> |
|[規劃升級到 Project Server 2019](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2019) <br/> |查看您需要進行從 Project Server 2016 升級至 Project Server 2019 的規劃考量。  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>關於升級至這個版本的相關須知

[您必須了的解關於 Project Server 2019 升級](https://go.microsoft.com/fwlink/p/?linkid=841827)，告訴您升級此版本中，其中包含一些重要變更： 
  
- 升級程序會將您的資料從 Project Server 2016 資料庫移轉至 SharePoint Server 2019 內容資料庫。  Project Server 2019 不長時間將會建立擁有 SharePoint 伺服器陣列中的 Project Server 資料庫。

- 升級之後，要知道的 Project Web App 中的數項變更。  如需說明這些，請參閱 < <b0>What's new in Project Server 2019</b0>。


## <a name="migrate-from-portfolio-server-2010"></a>從 Portfolio Server 2010 移轉

Project Portfolio Server 2010 的產品組合策略、 優先順序，以及最佳化 Project Server 2010 搭配使用。 此版本後所建立 Project Portfolio Server 沒有其他版本。 不過，產品組合管理功能可在更新 Project Server 版本和 Project Online 進階版版本。 從 Project Portfolio Server 2010 的資料無法移轉至下列一項。 例如業務推動因素的資料將會需要重新建立。
  
其他資源：
  
- [Project Online 服務說明](https://go.microsoft.com/fwlink/p/?linkid=841280)： 請參閱隨附 Project Server 2016 和 Project Online 進階版的產品組合管理功能。
    
- [Microsoft Office Project Portfolio Server 2010 移轉指南](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>相關主題

[從 SharePoint 2010 升級](upgrade-from-sharepoint-2010.md)
  
[資源可以幫助您升級從 Office 2010 伺服器和用戶端](upgrade-from-office-2010-servers-and-products.md)
  

