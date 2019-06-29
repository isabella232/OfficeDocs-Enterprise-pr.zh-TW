---
title: 將核心資料移至新的 Office 365 資料中心 geos
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 06/28/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 0a35176a-e585-4dec-a90b-36be8314667f
description: '新的資料中心 geos 新增容量及計算資源, 以支援我們持續的客戶需求和使用量增長。 此外, 新的資料中心 geos 為核心客戶資料提供了地理位置資料派駐服務。 核心客戶資料是指 Microsoft Online Services 條款中所定義的客戶資料子集的字詞: Exchange Online 信箱內容 (電子郵件內文、行事曆專案和電子郵件附件的內容), 以及 SharePoint Online 網站內容和檔案儲存在該網站, 以及上傳至商務用 OneDrive 的檔案。'
ms.openlocfilehash: 63b094772fc5e199124251e204b116e74cedec0a
ms.sourcegitcommit: aca382b615ce79c9f707f74cda6d90fbe87bb626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2019
ms.locfileid: "35392343"
---
# <a name="moving-core-data-to-new-office-365-datacenter-geos"></a>將核心資料移至新的 Office 365 資料中心 geos

我們會繼續開啟 Office 365 for business services 的新資料中心 geos。 這些新的資料中心 geos 新增容量及計算資源, 以支援我們持續的客戶需求和使用量增長。 此外, 新的資料中心 geos 為核心客戶資料提供了地理位置資料派駐服務。 

核心客戶資料是指[Microsoft Online Services 條款](https://go.microsoft.com/fwlink/p/?LinkID=249048)中所定義的客戶資料子集的字詞: 
- Exchange Online 信箱內容 (電子郵件內文、行事曆專案和電子郵件附件的內容)
- SharePoint Online 網站內容和儲存在該網站中的檔案
- 檔案上傳至商務用 OneDrive 
  
已在現有資料中心地理位置中儲存其核心客戶資料的現有客戶, 不會受到新資料中心地理位置的啟動影響。 我們不會對新的資料中心地理位置引入獨特的功能、功能或規範認證。 在這兩個 geos 的任何一種客戶中, 您會遇到與之前相同的服務品質、效能及安全性控制。 我們會提供下表所列的現有客戶, 以要求將組織中的核心客戶資料提前遷移至新的資料中心地理位置。
  
|擁有帳單位址的客戶 * * * *|舊資料中心地理位置 * * * *|新資料中心地理位置 * * * *|地理位置 (自 * * * *)|
|:-----|:-----|:-----|:-----|
|日本 * * * *| 亞洲/太平洋 | 日本 | 2014 年 12 月 |
|澳大利亞、紐西蘭、斐濟 * * * *| 亞洲/太平洋 | 澳大利亞 | 2015 年 3 月 |
|印度 * * * *| 亞洲/太平洋 | 印度 | 2015 年 10 月 |
|加拿大 * * * *| 北美 | 加拿大 | 2016 年 5 月 |
|英國 * * * *| 歐洲 | 英國 | 2016 年 9 月 |
|韓國 * * * *| 亞洲/太平洋 | 韓國 | 2017 年 4 月 |
|法國 * * * *| 歐洲 | 法國 | 2018 年 3 月 |
|阿拉伯聯合大公國 * * * *| 歐洲 | 阿拉伯聯合大公國 | 宣稱 |
|南非 * * * *| 歐洲 | 南非 | 宣稱 |
  
新客戶或 Office 365 租使用者在新資料中心地理位置的可用性後所建立的租使用者, 會自動將其核心客戶資料儲存在新的資料中心地理位置。
  
[互動式資料中心地圖](https://office.com/datamaps)的一部分是所有資料中心 geos、資料中心及客戶資料位置的完整清單。 
  
## <a name="data-residency-option"></a>資料派駐選項

我們針對上表所列的資料中心 geos 所涵蓋的現有 Office 365 客戶提供資料派駐選項。 使用此選項時, 具有資料派駐需求的客戶可以要求將其組織的核心客戶資料提前遷移至新的資料中心地理位置。  Microsoft 會在註冊視窗期間, 為要求早期遷移的所有合格客戶提供認可的截止期限。  請查看[如何要求資料移動](request-your-data-move.md)頁面, 以取得有關您地理位置之註冊時段的詳細資訊, 以及註冊至程式的步驟。  在要求期間內, 資料移動最多可能需要24個月才能完成。

不採取任何動作會導致 Microsoft 能夠將您的核心客戶資料同時移到新的資料中心地理位置, 作為服務管理和優化的一部分。您的核心客戶資料只可能會移至新的資料中心地理位置, 而不是任何其他地理位置。當這類服務管理移動完成並更新系統管理中心的資料位置時, 我們會透過訊息中心通知租使用者系統管理員。
   
我們不會對新的資料中心地理位置引入獨特的功能、功能或規範認證。
    
在全域運作且自動化的環境中, 我們需要執行資料移動的複雜性、精確度和規模, 可防止當資料移動對您的租使用者或任何其他單一租使用者完成時, 無法進行共用。 客戶在資料移動完成時, 會在訊息中心中收到一則確認。 
    
資料移動是一種後端服務作業, 對使用者的影響最小。 在[資料移動頁面的期間和之後,](during-and-after-your-data-move.md)會列出受影響的功能。 我們遵守[Microsoft Online Services 服務等級協定 (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897)的可用性, 讓客戶無需準備或在移動期間進行監視。 如有需要, 請進行任何服務維護的通知。 

將資料移至新的資料中心地理位置, 則不需要額外購買客戶。
    
## <a name="related-topics"></a>相關主題 
 
[如何要求資料移動](request-your-data-move.md)
    
[資料移動一般常見問題集](data-move-faq.md)
  
[Microsoft Dynamics CRM Online 的新資料中心 geos](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[依地區的 Azure 服務](https://azure.microsoft.com/en-us/regions/)
