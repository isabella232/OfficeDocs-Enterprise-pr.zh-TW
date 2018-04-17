---
title: 保護 SharePoint Online 網站與檔案
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Architecture
ms.assetid: 1d51bd87-17bf-457c-b698-61821de3afa0
description: 摘要： 設定建議保護 SharePoint Online 和 Office 365 中的檔案。
ms.openlocfilehash: 800d81d657164b2a936b95764d57fd092cfa21cc
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="secure-sharepoint-online-sites-and-files"></a>保護 SharePoint Online 網站與檔案

 **摘要：**設定建議的保護 SharePoint Online 和 Office 365 中的檔案。
  
本文提供設定 SharePoint Online 小組網站及檔案保護，簡化共同作業與平衡安全性建議。本文定義四個不同的設定，啟動與公用網站最開啟的共用原則與組織內。每個額外的設定向上代表有意義的步驟中保護，但可存取及進行共同作業的資源的能力降低至相關的一組使用者。使用這些建議當做起點並調整以符合組織需求的設定。 
  
本文的設定符合 Microsoft 針對資料、身分識別和裝置的下列三層保護建議：
  
- 基準保護
    
- 敏感性保護
    
- 高度機密保護
    
如需這些層級和每道層級的建議功能詳細資訊，請參閱下列資源。 
  
- [Office 365 的身分識別與裝置保護](microsoft-cloud-it-architecture-resources.md#BKMK_O365IDP)
    
- [Office 365 的檔案保護解決方案](microsoft-cloud-it-architecture-resources.md#BKMK_O365fileprotect)
    
## <a name="capability-overview"></a>功能概觀

建議的 SharePoint Online 小組網站依據各種不同 Office 365 功能而定。 針對高度機密的網站，建議您使用 Azure 資訊保護。 Enterprise Mobility + Security (EMS) 包含這項功能。 
  
下圖顯示四個 SharePoint Online 小組網站的建議的設定。
  
![SharePoint 網站的建議設定](images/ad0dcd70-f6f5-465c-8d16-1889481ca07a.png)
  
如圖例所示：
  
- 基準保護包括公用網站與私用網站這兩個 SharePoint Online 小組網站的選項。 公用網站可供組織中的任何人探索及存取。 私用網站則僅供網站成員探索及存取。 這兩個網站的設定都允許群組外部共用。 
    
- 設有敏感性與高度機密保護的網站為私用網站，其存取權僅限於特定群組的成員。
    
- Office 365 標籤可提供您分類資料的方法及所需的保護層級。 系統會將每個 SharePoint Online 小組網站設為自動替文件庫中的檔案加上該網站的預設標籤。 此範例的標籤對應到這四種網站設定，分別是「內部公用」、「私用」、「敏感性」與「高度機密」。 使用者可以變更標籤，但這種設定可確保所有檔案都收到預設標籤。
    
- 系統會針對「敏感性」和「高度機密」的 Office 365 標籤設定資料外洩防護 (DLP) 原則，以在使用者嘗試將這類檔案傳送到組織外部時，對他們發出警告或阻止此動作。
    
- 如果網站設有高度機密的保護，Azure 資訊保護會進行加密，並授與檔案的權限。
    
## <a name="tenant-wide-settings-for-sharepoint-online-and-onedrive-for-business"></a>SharePoint Online 和商務用 OneDrive 的租用戶整體設定

SharePoint Online 和商務用 OneDrive 包含的租用戶整體設定會影響所有網站與使用者。 其中某些設定可以於網站層級進行調整，使其更加嚴格 (但不能更寬鬆)。 本節說明會影響安全性與共同作業的租用戶整體設定。 
  
### <a name="sharing"></a>共用

針對這個解決方案，我們建議下列的租用戶整體設定：
  
- 保留預設共用原則，以允許所有帳戶類型的共用作業，包括匿名共用。
    
- 您可視需要將匿名的連結設為過期。
    
- 將共用的預設連結類型變更為「內部」。 這有助於防止資料不慎洩漏到組織外部。
    
雖然允許外部共用似乎有悖常理，但相較於以電子郵件傳送檔案，此方法可以更充分地掌控檔案共用情況。 SharePoint Online 與 Outlook 一起運作，以提供安全的檔案共同作業。 
  
- 根據預設，Outlook 會共用檔案的連結，而非以電子郵件傳送檔案。 
    
- SharePoint Online 和 OneDrive for Business 輕鬆與所組織內外的參與者共用檔案的連結
    
您也可以使用相關控制來協助控管外部共用。 例如，您可以：
  
- 停用匿名訪客的連結。
    
- 撤銷使用者的網站存取權。
    
- 查看誰具有特定網站或文件的存取權。
    
- 將匿名共用連結設為過期 (租用戶設定)。
    
- 限制可在組織外部共用的人員 (租用戶設定)。
    
### <a name="use-external-sharing-together-with-data-loss-prevention-dlp"></a>搭配使用外部共用與資料外洩防護 (DLP)

如果您不允許外部共用，請使用商務使用者需要找到替代工具和方法。Microsoft 建議您將合併與 DLP 原則，以保護機密和高度機密檔案的外部共用。
  
### <a name="device-access-settings"></a>裝置存取設定

SharePoint Online 和 OneDrive for Business 的裝置存取設定可讓您判斷是否限制為僅使用瀏覽器存取 （無法下載檔案） 或如果封鎖存取。這些設定是目前正在第一個版本及套用租用戶全。即將推出的是能夠在網站層級設定裝置存取原則。此解決方案，建議您不使用適用於整個租用戶的裝置存取設定。
  
若要使用初次發行的裝置存取設定：[在 Office 365 中設定標準或初次發行選項](https://support.office.com/article/Set-up-the-Standard-or-First-Release-options-in-Office-365-3B3ADFA4-1777-4FF0-B606-FB8732101F47)。
  
### <a name="onedrive-for-business"></a>商務用 OneDrive

請瀏覽這些設定，以決定是否要變更商務用 OneDrive 的網站預設設定。 目前，會複製 SharePoint Online 系統管理中心的共用和裝置存取設定，並套用到這兩個環境。
  
## <a name="sharepoint-team-site-configuration"></a>SharePoint 小組網站設定

下表摘要說明本文稍早所述之每個小組網站的設定。 您可以使用這些設定作為建議的起點，並依據組織需求調整網站類型與設定。 並非每個組織都需要所有類型的網站。 只有少數的組織需要高度機密的保護。
  
||||||
|:-----|:-----|:-----|:-----|:-----|
||**基準保護 #1** <br/> |**基準保護 #2** <br/> |**敏感性保護** <br/> |**高度機密** <br/> |
|說明  <br/> |開啟組織內的探索及共同作業。  <br/> |私用網站和群組，其可在群組外部共用。  <br/> |隔離的網站，其存取層級會依據特定群組的成員資格而定義。 只允許網站的成員共用。 當使用者嘗試將檔案傳送到組織外部時，DLP 會對其發出警告。  <br/> |使用 Azure 資訊保護的隔離網站 + 檔案加密與權限。 DLP 可防止使用者將檔案傳送到組織外部。  <br/> |
|私用或公用的小組網站  <br/> |公用  <br/> |Private  <br/> |Private  <br/> |Private  <br/> |
|誰可以存取？  <br/> |組織中所有人，包括 B2B 使用者和訪客使用者。  <br/> |僅限網站的成員。 其他人可以要求存取權。  <br/> |僅限網站的成員。 其他人可以要求存取權。  <br/> |僅限成員。 其他人無法要求存取權。  <br/> |
|網站層級的共用控制  <br/> |允許與任何人共用。 預設設定。  <br/> |允許與任何人共用。 預設設定。  <br/> |成員無法共用網站的存取權。  <br/> 非成員可以要求存取網站，但這些要求需要網站系統管理員處理。  <br/> |成員無法共用網站的存取權。  <br/> 非成員無法要求存取網站或內容。  <br/> |
|網站層級的裝置存取控制  <br/> |無額外控制。  <br/> |無額外控制。  <br/> |網站層級的控制功能即將推出，其可防止使用者下載檔案到不相容或非加入網域的裝置。 如此一來，所有其他裝置僅可進行瀏覽器存取。  <br/> |網站層級的控制功能即將推出，其會封鎖檔案下載到不相容或非加入網域的裝置。  <br/> |
|Office 365 標籤  <br/> |內部公用  <br/> |Private  <br/> |敏感性  <br/> |高度機密  <br/> |
|DLP 原則  <br/> |||當使用者將標記為「敏感性」的檔案傳送到組織外部時，會對其發出警告。  <br/> 若要封鎖敏感性資料類型的外部共用，例如信用卡號碼或其他個人資料，您可以為這些資料類型 (包括您設定的自訂資料類型) 設定額外的 DLP 原則。  <br/> |封鎖使用者，使其無法將標示為高度機密的檔案傳送到組織外部。 允許使用者提供理由來覆寫這項預設，包括共用檔案的對象。  <br/> |
|Azure 資訊保護  <br/> ||||使用 Azure 資訊保護自動加密，並授與權限的檔案。萬一他們洩露與檔案一起出差此保護。  <br/> Office 365 無法讀取使用 Azure 資訊保護加密的檔案。此外，DLP 原則可以只使用中繼資料 （包括標籤），但不是 （例如檔案內的信用卡號碼） 這些檔案的內容。  <br/> |
   
如需部署這個解決方案中的 SharePoint Online 小組網站的四種不同類型的步驟，請參閱[部署 SharePoint Online 網站的三層的保護](deploy-sharepoint-online-sites-for-three-tiers-of-protection.md)。如需建立開發/測試環境，請參閱[Secure SharePoint Online 網站的開發人員/測試環境中](secure-sharepoint-online-sites-in-a-dev-test-environment.md)的步驟。 
  
## <a name="office-365-classification-and-labels"></a>Office 365 分類和標籤

使用 Office 365 標籤建議與機密資料的環境。後設定並發佈 Office 365 標籤：
  
- 您可以將預設標籤套用至 SharePoint Online 小組網站、 文件庫使所有文件的文件庫中取得的預設標籤。 
    
- 您可以套用標籤內容自動是否符合特定條件。
    
- 您可以套用 Office 365 標籤為基礎的 DLP 原則。
    
- 在組織中的人員可以套用標籤手動在 web 上的 Outlook 中的內容 Outlook 2010 及更新版本、 OneDrive for Business、 SharePoint Online 和 Office 365 的群組。使用者經常知道最佳的內容類型他們正在處理，讓他們可以用它來分類及已套用適當的 DLP 原則。
    
![SharePoint 網站的建議設定](images/7fed0126-ab4a-4480-922c-681970642339.png)
  
如圖例所示，此解決方案包括建立下列標籤：
  
- 高度機密
    
- 敏感性
    
- Private
    
- 內部公用
    
這些標籤會對應至在圖例中建議的網站和本文稍早的圖表。此解決方案建議設定 DLP 原則，以協助防止檔案標示為機密和高度機密外的洩。
  
如需在此解決方案中設定 Office 365 標籤和 DLP 原則的步驟，請參閱[使用 Office 365 標籤與 DLP 來保護 SharePoint Online 檔案](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)。
  
## <a name="azure-information-protection"></a>Azure 資訊保護

您可以使用 Azure 資訊保護，來套用與檔案隨行的標籤和保護。 建議您為此解決方案使用限域的 Azure 資訊保護原則以及高度機密標籤的子標籤，來加密需要以最高安全性等級保護的檔案，和為其授予權限。 
  
請留意，若將 Azure 資訊保護套用至儲存於 Office 365 中的檔案，服務就無法處理這些檔案的內容。 共同撰寫、eDiscovery、搜尋、Delve 和其他共同作業功能無法運作。 此外，DLP 原則只可用於中繼資料 (包括 Office 365 標籤)，但不可用於這些檔案的內容 (例如檔案中的信用卡號碼)。
  
![Azure 資訊保護設定於 Azure 中，且標籤顯示在用戶端工具列中](images/1266a7a0-5078-49ab-bbf1-b0cf41451f62.png)
  
如圖例所示：
  
- 您在 Microsoft Azure 入口網站中設定 Azure 資訊保護原則和標籤。建議設定子範圍的 Azure 資訊保護原則的標籤。
    
- Azure 的資訊保護會向上顯示標籤為 Office 應用程式中的**資訊保護**長條。
    
### <a name="adding-permissions-for-external-users"></a>新增外部使用者的權限

有兩種方式可授與外部使用者存取權與 Azure 資訊保護受保護的檔案。在這兩個這些情況下，外部使用者必須具備 Azure AD 帳戶。如果外部使用者不會使用 Azure AD 組織中的成員，他們可以使用此註冊頁面為個別取得 Azure AD 帳戶： [https://aka.ms/aip-signup](https://aka.ms/aip-signup)。
  
- 將外部使用者新增至可用來設定標籤保護 Azure AD 群組
    
     必須先將帳戶新增為 B2B 使用者您的目錄中。可能需要幾個小時的[群組成員資格的 Azure Rights Management 快取](https://docs.microsoft.com/information-protection/plan-design/prepare#group-membership-caching-by-azure-rights-management)。使用此方法之後，權限會授與所有受保護的標籤 （偶數之前將使用者新增至 Azure AD 群組受保護的檔案） 與現有的檔案。
    
- 外部使用者直接新增至標籤保護
    
     您可以新增所有使用者的組織 (例如 Fabrikam.com)、 Azure AD 的群組 （如 finance 組織內的群組） 或個別使用者。例如，您可以新增以及外部小組來保護標籤。使用此方法之後，權限會授與僅外部的實體新增至 [保護之後標籤以受保護的檔案。
    
### <a name="deploying-and-using-azure-information-protection"></a>部署並使用 Azure 資訊保護

如需在此解決方案中設定 Azure 資訊保護的步驟，請參閱[使用 Azure 資訊保護來保護 SharePoint Online 檔案](protect-sharepoint-online-files-with-azure-information-protection.md)。
  
## <a name="see-also"></a>請參閱

[適用於政治活動、非營利組織和其他彈性組織的 Microsoft 安全性指南](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[安全性解決方案](security-solutions.md)
  
[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)
  
[在開發/測試環境中保護 SharePoint Online 網站](secure-sharepoint-online-sites-in-a-dev-test-environment.md)



