---
title: "安全的 SharePoint Online 網站及檔案"
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
- Strat_O365_Enterprise
- Ent_Architecture
ms.assetid: 1d51bd87-17bf-457c-b698-61821de3afa0
description: "摘要： 設定建議保護 SharePoint Online 和 Office 365 中的檔案。"
ms.openlocfilehash: 035c3e69a430269b382ab032387a44cc3cbbbfd6
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="secure-sharepoint-online-sites-and-files"></a>安全的 SharePoint Online 網站及檔案

 **摘要：**設定建議的保護 SharePoint Online 和 Office 365 中的檔案。
  
本文提供設定 SharePoint Online 小組網站及檔案保護，簡化共同作業與平衡安全性建議。本文定義四個不同的設定，啟動與公用網站最開啟的共用原則與組織內。每個額外的設定向上代表有意義的步驟中保護，但可存取及進行共同作業的資源的能力降低至相關的一組使用者。使用這些建議當做起點並調整以符合組織需求的設定。 
  
三層的保護資料、 身分識別、 和裝置的 Microsoft 的建議最符合本文中的設定：
  
- [比較基準保護
    
- 機密保護
    
- 高度機密保護
    
如需這些層與建議的每一層的功能的詳細資訊，請參閱下列資源。 
  
- [Office 365 的身分識別與裝置保護](microsoft-cloud-it-architecture-resources.md#BKMK_O365IDP)
    
- [Office 365 的檔案保護方案](microsoft-cloud-it-architecture-resources.md#BKMK_O365fileprotect)
    
## <a name="capability-overview"></a>功能概觀 （英文)

在 Office 365 功能的各種上繪製 SharePoint Online 小組網站的建議。高度機密網站的建議 Azure 資訊保護。這包含在企業行動性 + 安全性 （EMS）。 
  
下圖顯示四個 SharePoint Online 小組網站的建議的設定。
  
![SharePoint 網站的建議設定](images/ad0dcd70-f6f5-465c-8d16-1889481ca07a.png)
  
如下所示：
  
- [比較基準保護包含 SharePoint Online 小組網站的兩個選項-公用及私人網站。可以探索和組織中的任何人存取公用網站。私用網站可以只探索和存取網站的成員。這兩個這些站台組態允許共用外的群組。 
    
- 機密和高度機密保護功能的網站是私人的網站具有存取僅限於特定群組的成員。
    
- Office 365 標籤提供一種方式來分類資料以所需的保護層級。每個 SharePoint Online 小組網站設定成自動 label 的預設標籤與文件庫中的網站的檔案。對應的四個網站設定，在此範例中的標籤是內部公用、 私人、 機密、 和高度機密。使用者可以變更標籤，但此設定可確保所有檔案都接收的預設標籤。
    
- 資料外洩防護 (DLP) 原則設定為警告或其嘗試傳送這些類型的組織外的檔案時防止使用者之機密與高度機密 Office 365 的標籤。
    
- 使用高度機密保護設定的網站、 Azure 資訊保護加密並授與權限的檔案。
    
## <a name="tenant-wide-settings-for-sharepoint-online-and-onedrive-for-business"></a>SharePoint Online 和 OneDrive for Business 的租用戶整體設定

SharePoint Online 和 OneDrive for Business 包含整個租用戶的設定會影響所有網站及使用者。這些設定的一些也可以在網站層級設為更嚴格 （但不是小於） 調整。本章節將討論影響安全性及共同作業的租用戶整體設定。 
  
### <a name="sharing"></a>共用

此解決方案，我們建議下列整個租用戶的設定：
  
- 保留預設共用原則允許與所有的帳戶類型，包括匿名共用的所有共用。
    
- 如果想要設定到期，匿名連結。
    
- 變更預設的連結類型共用為 Internal。這有助於防止組織外部的意外資料外洩。
    
儘管可能有些直覺式允許外部共用，這個方法會提供更多控制權檔案共用相較於傳送電子郵件中的檔案。SharePoint Online 和 Outlook 共同運作來提供安全共同作業的檔案。 
  
- 根據預設，Outlook 會共用檔案而不是電子郵件中傳送之檔案的連結。 
    
- SharePoint Online 和 OneDrive for Business 輕鬆與所組織內外的參與者共用檔案的連結
    
您也可以協助管理外部共用的控制項。例如，您可以：
  
- 停用匿名來賓連結。
    
- 撤銷使用者對網站的存取。
    
- 查看哪些人員擁有特定網站或文件的存取權。
    
- 設定匿名共用到期 （租用戶設定） 的連結。
    
- 可以共用 （租用戶設定） 您組織外部的限制。
    
### <a name="use-external-sharing-together-with-data-loss-prevention-dlp"></a>使用 [資料外洩防護 (DLP) 以及外部共用

如果您不允許外部共用，請使用商務使用者需要找到替代工具和方法。Microsoft 建議您將合併與 DLP 原則，以保護機密和高度機密檔案的外部共用。
  
### <a name="device-access-settings"></a>裝置存取設定

SharePoint Online 和 OneDrive for Business 的裝置存取設定可讓您判斷是否限制為僅使用瀏覽器存取 （無法下載檔案） 或如果封鎖存取。這些設定是目前正在第一個版本及套用租用戶全。即將推出的是能夠在網站層級設定裝置存取原則。此解決方案，建議您不使用適用於整個租用戶的裝置存取設定。
  
若要使用這些是在第一個版本時的裝置存取設定：[設定 [一般] 或 [Office 365 中的第一個版本選項](https://support.office.com/article/Set-up-the-Standard-or-First-Release-options-in-Office-365-3B3ADFA4-1777-4FF0-B606-FB8732101F47)。
  
### <a name="onedrive-for-business"></a>商務用 OneDrive

瀏覽這些設定決定想要變更 OneDrive for Business 的網站的預設設定。目前的共用和裝置存取的設定重複從 SharePoint Online 系統管理中心並套用至這兩個環境。
  
## <a name="sharepoint-team-site-configuration"></a>SharePoint 小組網站設定

下表摘要說明本文稍早所述的小組網站的每個設定。使用這些設定作為起始點的建議及調整網站類型和設定以符合組織的需求。不是每個的組織需要每一種網站。只有少數組織需要高度機密保護。
  
||||||
|:-----|:-----|:-----|:-----|:-----|
||**[比較基準保護 #1** <br/> |**[比較基準保護 #2** <br/> |**機密保護** <br/> |**高度機密** <br/> |
|描述  <br/> |開啟搜索與組織內的共同作業。  <br/> |私人的網站與使用共用允許外部群組的群組。  <br/> |隔離的網站的存取層級定義的特定群組的成員資格。只允許的網站成員共用。DLP 警告使用者嘗試傳送組織外的檔案時。  <br/> |隔離的網站 + 檔案加密和權限與 Azure 資訊保護。DLP 可防止使用者傳送組織外的檔案。  <br/> |
|私人或公開的小組網站  <br/> |公用  <br/> |私人  <br/> |私人  <br/> |私人  <br/> |
|已經有存取權？  <br/> |大家包括 B2B 使用者及來賓使用者的組織中。  <br/> |僅限網站的成員。其他人可以要求存取。  <br/> |僅限網站的成員。其他人可以要求存取。  <br/> |僅限成員。其他人無法要求存取。  <br/> |
|網站層級共用的控制項  <br/> |允許與共用任何人。預設設定。  <br/> |允許與共用任何人。預設設定。  <br/> |成員無法共用網站的存取權。  <br/> 非成員可以要求存取網站，但這些要求需要定址的網站管理員。  <br/> |成員無法共用網站的存取權。  <br/> 非成員無法要求網站或內容的存取權。  <br/> |
|網站層級裝置存取控制項  <br/> |沒有任何額外的控制項。  <br/> |沒有任何額外的控制項。  <br/> |網站層級控制項即將推出，進而使得使用者無法下載檔案至非相容或非網域加入裝置。這可讓您僅供瀏覽器存取所有其他裝置。  <br/> |網站層級控制項即將推出，以封鎖的非相容或非網域加入裝置檔案下載。  <br/> |
|Office 365 標籤  <br/> |內部公用  <br/> |私人  <br/> |機密  <br/> |高度機密  <br/> |
|DLP 原則  <br/> |||將檔案標示為機密傳送組織外時警告使用者。  <br/> 若要封鎖外部共用機密資料類型，例如信用卡號或其他個人資料，您可以設定 （包括您所設定的自訂資料類型） 這些資料類型的額外的 DLP 原則。  <br/> |封鎖使用者傳送會標示為高度機密組織外部的檔案。允許使用者覆寫此設定以提供對齊，包括誰共用與檔案。  <br/> |
|Azure 資訊保護  <br/> ||||使用 Azure 資訊保護自動加密，並授與權限的檔案。萬一他們洩露與檔案一起出差此保護。  <br/> Office 365 無法讀取使用 Azure 資訊保護加密的檔案。此外，DLP 原則可以只使用中繼資料 （包括標籤），但不是 （例如檔案內的信用卡號碼） 這些檔案的內容。  <br/> |
   
如需部署這個解決方案中的 SharePoint Online 小組網站的四種不同類型的步驟，請參閱[部署 SharePoint Online 網站的三層的保護](deploy-sharepoint-online-sites-for-three-tiers-of-protection.md)。如需建立開發/測試環境，請參閱[Secure SharePoint Online 網站的開發人員/測試環境中](secure-sharepoint-online-sites-in-a-dev-test-environment.md)的步驟。 
  
## <a name="office-365-classification-and-labels"></a>Office 365 分類及標籤

使用 Office 365 標籤建議與機密資料的環境。後設定並發佈 Office 365 標籤：
  
- 您可以將預設標籤套用至 SharePoint Online 小組網站、 文件庫使所有文件的文件庫中取得的預設標籤。 
    
- 您可以套用標籤內容自動是否符合特定條件。
    
- 您可以套用 Office 365 標籤為基礎的 DLP 原則。
    
- 在組織中的人員可以套用標籤手動在 web 上的 Outlook 中的內容 Outlook 2010 及更新版本、 OneDrive for Business、 SharePoint Online 和 Office 365 的群組。使用者經常知道最佳的內容類型他們正在處理，讓他們可以用它來分類及已套用適當的 DLP 原則。
    
![SharePoint 網站的建議設定](images/7fed0126-ab4a-4480-922c-681970642339.png)
  
如下圖所，此解決方案包含建立下列標籤：
  
- 高度機密
    
- 機密
    
- 私人
    
- 內部公用
    
這些標籤會對應至在圖例中建議的網站和本文稍早的圖表。此解決方案建議設定 DLP 原則，以協助防止檔案標示為機密和高度機密外的洩。
  
如需設定此解決方案中的 Office 365 標籤和 DLP 原則的步驟，請參閱 ＜[保護 SharePoint Online 與 Office 365 標籤和 DLP 的檔案](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)。
  
## <a name="azure-information-protection"></a>Azure 資訊保護

使用 Azure 資訊保護套用標籤和儘向哪個部門請求追蹤檔案的保護設定。此解決方案，建議您使用範圍的 Azure 資訊保護原則和子標籤的高度機密標籤加密及授與權限需要最高層級的安全性與保護的檔案。 
  
請注意當 Azure 資訊保護加密套用至檔案儲存在 Office 365 服務無法處理這些檔案的內容。共同撰寫 」、 「 eDiscovery 」、 「 搜尋 」、 「 Delve、 和 「 其他共同作業功能無法運作。DLP 原則僅可用於 （包括 Office 365 標籤） 的中繼資料，但不是 （例如檔案內的信用卡號碼） 這些檔案的內容。
  
![Azure 資訊保護設定於 Azure 中，且標籤顯示在用戶端工具列中](images/1266a7a0-5078-49ab-bbf1-b0cf41451f62.png)
  
如下所示：
  
- 您在 Microsoft Azure 入口網站中設定 Azure 資訊保護原則和標籤。建議設定子範圍的 Azure 資訊保護原則的標籤。
    
- Azure 的資訊保護會向上顯示標籤為 Office 應用程式中的**資訊保護**長條。
    
### <a name="adding-permissions-for-external-users"></a>新增外部使用者的權限

有兩種方式可授與外部使用者存取權與 Azure 資訊保護受保護的檔案。在這兩個這些情況下，外部使用者必須具備 Azure AD 帳戶。如果外部使用者不會使用 Azure AD 組織中的成員，他們可以使用此註冊頁面為個別取得 Azure AD 帳戶： [https://aka.ms/aip-signup](https://aka.ms/aip-signup)。
  
- 將外部使用者新增至可用來設定標籤保護 Azure AD 群組
    
     必須先將帳戶新增為 B2B 使用者您的目錄中。可能需要幾個小時的[群組成員資格的 Azure Rights Management 快取](https://docs.microsoft.com/information-protection/plan-design/prepare#group-membership-caching-by-azure-rights-management)。使用此方法之後，權限會授與所有受保護的標籤 （偶數之前將使用者新增至 Azure AD 群組受保護的檔案） 與現有的檔案。
    
- 外部使用者直接新增至標籤保護
    
     您可以新增所有使用者的組織 (例如 Fabrikam.com)、 Azure AD 的群組 （如 finance 組織內的群組） 或個別使用者。例如，您可以新增以及外部小組來保護標籤。使用此方法之後，權限會授與僅外部的實體新增至 [保護之後標籤以受保護的檔案。
    
### <a name="deploying-and-using-azure-information-protection"></a>部署及使用 Azure 資訊保護

如需設定 Azure 資訊保護此解決方案，請參閱[Azure 資訊保護檔案保護 SharePoint Online](protect-sharepoint-online-files-with-azure-information-protection.md)的步驟。
  
## <a name="see-also"></a>請參閱

[Microsoft 安全性指導政治活動、 非營利機構，以及其他靈活的組織](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[安全性解決方案](security-solutions.md)
  
[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)
  
[安全的開發人員/測試環境中的 SharePoint Online 網站](secure-sharepoint-online-sites-in-a-dev-test-environment.md)



