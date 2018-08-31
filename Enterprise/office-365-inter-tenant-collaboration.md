---
title: Office 365 租用戶間共同作業
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 6/28/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- MOE150
ms.assetid: eb45fd8b-1d5d-4b0c-9c5a-479dbb176e7d
description: 了解 Office 365 共同作業租用戶及組織間的運作方式。
ms.openlocfilehash: 932c837f9dc09dd0469a17ad4e6a05f09966d29c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539993"
---
# <a name="office-365-inter-tenant-collaboration"></a>Office 365 租用戶間共同作業

本文說明兩種 Office 365 租用戶之間進行共同作業的數種方式。擬 for Office 365 系統管理員。
  
假設兩個組織 Fabrikam 與 Contoso，每個具有 Office 365 的企業租用戶和他們想要數個專案;部份只執行有限的時間和部份只會進行中。如何可以 Fabrikam 與 Contoso 啟用其人員以及小組進行共同作業更有效率地其不同 Office 365 租用戶之間以安全方式？Office 365 中，搭配 Azure Active Directory B2B 共同作業、 提供數種選項。本文說明 Fabrikam 與 Contoso 可納入考量的幾個主要案例。
  
Office 365 之間的租用戶共同作業選項包括使用的集中位置的檔案和對話、 共用行事曆、 使用 IM、 音訊/視訊通話的通訊，以及保護存取資源和應用程式。選取 [解決方案]，深入了解，請使用下列表格。
  
## <a name="exchange-online-collaboration-options"></a>Exchange Online 的共同作業選項

|**共用目標**|**系統管理巨集指令**|**用法資訊**|
|:-----|:-----|:-----|
|與另一個 Office 365 組織共用行事曆  <br/> |系統管理員可以設定不同的行事曆存取層級在 Exchange Online 可與其他人共同作業與其他企業與可讓使用者共用排程 （空閒/忙碌資訊） 的企業版  <br/> |[在 Exchange Online 中共用](https://technet.microsoft.com/en-us/library/jj916670%28v=exchg.150%29.aspx) <br/> [Exchange Online 中的組織關係](https://technet.microsoft.com/en-us/library/jj916658%28v=exchg.150%29.aspx) <br/> [在 Exchange Online 中建立組織關聯性](https://technet.microsoft.com/en-us/library/jj916671%28v=exchg.150%29.aspx) <br/> [修改與 Exchange Online 中的組織關係](https://technet.microsoft.com/en-us/library/jj916659%28v=exchg.150%29.aspx) <br/> [Exchange Online 中移除組織關係](https://technet.microsoft.com/en-us/library/jj916657%28v=exchg.150%29.aspx) <br/> [與外部使用者共用行事曆](https://support.office.com/article/fb00dd4e-2d5f-4e8d-8ff4-94b2cf002bdd) <br/> |
|控制使用者與組織外部人員共用其行事曆的方式  <br/> |系統管理員將共用原則套用至使用者信箱來控制誰可以與共用和存取權授與的層級  <br/> |[共用 Exchange Online 中的原則](https://technet.microsoft.com/en-us/library/jj916673%28v=exchg.150%29.aspx) <br/> [在 Exchange Online 中建立共用原則](https://technet.microsoft.com/en-us/library/jj916676%28v=exchg.150%29.aspx) <br/> [將共用原則套用至 Exchange Online 中的信箱](https://technet.microsoft.com/en-us/library/jj916672%28v=exchg.150%29.aspx) <br/> [修改、 停用或移除 Exchange Online 中的共用原則](https://technet.microsoft.com/en-us/library/jj916674%28v=exchg.150%29.aspx) <br/> |
|設定安全的電子郵件通道及控制與協力廠商組織的郵件流程  <br/> |系統管理員建立套用至與協力廠商組織或服務提供者的郵件交換安全性的連接器。連接器以及允許的網域名稱限制強制加密透過傳輸層安全性 (TLS) 或 IP 位址範圍從協力廠商傳送電子郵件。  <br/> |[Exchange Online 如何使用 TLS 來保護 Office 365 中的電子郵件連線](https://technet.microsoft.com/en-us/library/mt163898.aspx) <br/> [Configure mail flow using connectors in Office 365](https://technet.microsoft.com/en-us/library/ms.exch.eac.connectorselection%28v=exchg.150%29.aspx) <br/> [Exchange Online 中的遠端網域](https://technet.microsoft.com/en-us/library/jj966211%28v=exchg.150%29.aspx) <br/> [設定與協力廠商組織的安全郵件流程的連接器](https://technet.microsoft.com/en-us/library/dn751021%28v=exchg.150%29.aspx) <br/> [郵件流程的最佳作法 Exchange Online 與 Office 365 （概觀）](https://technet.microsoft.com/en-us/library/0e6cd9d5-ad3e-418a-8ea9-3bf33332c491%28v=exchg.150%29) <br/> |
   
## <a name="sharepoint-online-and-onedrive-for-business-collaboration-options"></a>SharePoint Online 和 OneDrive for Business 共同作業選項

|**共用目標**|**系統管理巨集指令**|**用法資訊**|
|:-----|:-----|:-----|
|與外部使用者共用網站和文件  <br/> |管理員可設定承租人，請參閱共用或 Microsoft 帳戶驗證、 工作或學校的網站集合層級帳戶已驗證或來賓帳戶  <br/> |
  [管理您的 SharePoint Online 環境外部共用](https://support.office.com/en-US/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> [受限制的網域共用 Office 365 中的 SharePoint Online 和 OneDrive for Business](https://support.office.com/en-US/article/Restricted-Domains-Sharing-in-Office-365-SharePoint-Online-and-OneDrive-for-Business-5d7589cd-0997-4a00-a2ba-2320ec49c4e9) <br/> [為企業企業 (B2B) 外部網路方案中使用 [SharePoint Online](https://support.office.com/article/7b087413-165a-4e94-8871-4393e0b9c037) <br/> |
|追蹤及控制使用者的外部共用  <br/> |OneDrive for Business 檔案擁有者和 SharePoint Online 的使用者設定網站和文件共用及建立追蹤共用的通知  <br/> |[設定外部共用 OneDrive for Business 的通知](https://support.office.com/en-US/article/Configure-notifications-for-external-sharing-for-OneDrive-for-Business-b640c693-f170-4227-b8c1-b0a7e0fa876b) <br/> [在 Office 365 中共用 SharePoint 檔案或資料夾](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) (機器翻譯) <br/> |
   
## <a name="skype-for-business-collaboration-options"></a>Skype 的商務共同作業選項

|**共用目標**|**系統管理巨集指令**|**用法資訊**|
|:-----|:-----|:-----|
|Skype 商務 online-IM、 通話及顯示狀態與商務使用者的其他 Skype  <br/> |系統管理員可以啟用其 Skype 商務 Online 使用者 IM、 進行音訊/視訊通話及請參閱其他 Office 365 租用戶中的使用者的目前狀態。  <br/> |[允許使用者商務使用者的連絡人外部 Skype](https://support.office.com/article/b414873a-0059-4cd5-aea1-e5d0857dbc94) <br/> |
|Skype 商務 online-IM、 通話及顯示狀態與 Skype （消費者） 的使用者  <br/> |系統管理員可以讓商務 Online IM 使用者及其 Skype、 進行通話，並查看與 Skype （消費者） 使用者的目前狀態。  <br/> |[讓商務使用者的 Skype 新增 Skype 連絡人](https://support.office.com/article/08666236-1894-42ae-8846-e49232bbc460) <br/> |
   
## <a name="azure-ad-b2b-collaboration-options"></a>Azure AD B2B 共同作業選項

|**共用目標**|**系統管理巨集指令**|**用法資訊**|
|:-----|:-----|:-----|
|Azure AD B2B 共同作業-將外部使用者新增至組織的目錄中的群組共用的內容  <br/> |一個 Office 365 租用戶的全域系統管理員可以邀請人員加入其目錄的另一個 Office 365 租用戶中將這些外部的使用者新增至群組，並授與內容，例如 SharePoint 網站和文件庫群組的存取權。  <br/> |[Azure AD B2B 共同作業預覽為何？](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) <br/> [Azure AD B2B： 新更新方便跨商業協同](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/01/azure-ad-b2b-new-updates-make-cross-business-collab-easy/) <br/> [外部共用 office 365 和 Azure Active Directory B2B 共同作業](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-o365-external-user) <br/> [Azure Active Directory B2B 共同作業 API 與自訂](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-api) <br/> [Azure AD 和身分識別 Show： Azure AD B2B 共同作業 （針對企業](https://channel9.msdn.com/Series/Azure-AD-Identity/AzureADB2B) <br/> |
   
## <a name="office-365-collaboration-options"></a>Office 365 共同作業選項

|**共用目標**|**系統管理巨集指令**|**用法資訊**|
|:-----|:-----|:-----|
|Office 365 群組-電子郵件、 行事曆、 OneNote 和集中一處共用的檔案  <br/> |在商務 Essentials、 企業進階版、 教育和企業版 E1、 E3 和 E5 計劃支援群組。一個 Office 365 租用戶中的人員可以建立的群組和邀請另一個 Office 365 租用戶中的人員來賓使用者一樣。也適用於 Dynamics CRM。  <br/> |[了解 Office 365 群組](https://support.office.com/article/b565caa1-5c40-40ef-9915-60fdb2d97fa2) <br/> [Office 365 群組中的來賓存取](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6) <br/> [部署 Office 365 群組](https://technet.microsoft.com/en-us/library/dn896591.aspx) <br/> |
   
## <a name="yammer-collaboration-options"></a>Yammer 共同作業選項

|**共用目標**|**系統管理巨集指令**|**用法資訊**|
|:-----|:-----|:-----|
|Yammer-透過企業社交 medium 的共同作業  <br/> |建立外部群組的功能已停用 Yammer 管理員，除非使用者可以建立外部進行共同作業 Yammer 中透過能夠想要遵循的文章、 共用檔案、 與線上聊天室的交談群組。  <br/> |[建立及管理外部 Yammer 中的群組](https://support.office.com/article/9ccd15ce-0efc-4dc1-81bc-4a424ab6f92a) <br/> |
   
## <a name="teams-collaboration-options"></a>小組共同作業選項

|**共用目標**|**系統管理巨集指令**|**用法資訊**|
|:-----|:-----|:-----|
|與組織外部的使用者在小組共同作業  <br/> |邀請的 Office 365 租用戶的全域系統管理員必須啟用小組中的外部共同作業。全域系統管理員和小組擁有者現在可以邀請進行共同作業的小組電子郵件地址的任何人。  <br/> 系統管理員也可以管理和編輯來賓其租用戶中已經存在。  <br/> |[授權來賓存取](https://docs.microsoft.com/en-us/microsoftteams/teams-dependencies) <br/> [開啟或關閉開啟來賓存取小組中](https://docs.microsoft.com/en-us/microsoftteams/set-up-guests) <br/> [使用 PowerShell 來控制來賓存取](https://docs.microsoft.com/en-us/microsoftteams/guest-access-powershell) <br/> [來賓存取檢查清單](https://docs.microsoft.com/en-us/microsoftteams/guest-access-checklist) <br/> [檢視來賓使用者](https://docs.microsoft.com/en-us/microsoftteams/view-guests) <br/> [編輯來賓使用者資訊](https://docs.microsoft.com/en-us/microsoftteams/edit-guests-information) <br/> |
|小組擁有者可以邀請和管理來賓內其小組的共同作業。  <br/> |小組擁有者可在來賓可執行其小組內的其他控制項。  <br/> |[新增來賓](https://support.office.com/en-us/article/teams-and-channels-df38ae23-8f85-46d3-b071-cb11b9de5499?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_addingguests&amp;ID0EAABAAA=Add_guests) <br/> [新增至小組的來賓](https://docs.microsoft.com/en-us/microsoftteams/add-guests) <br/> [管理小組中的來賓存取](https://docs.microsoft.com/en-us/microsoftteams/manage-guests) <br/> [看誰在小組或通道中](https://support.office.com/en-us/article/see-who-s-on-a-team-or-in-a-channel-5c6be9be-9c45-4a0f-a1a0-f332b23cb6b7?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> |
|從其他租用戶的來賓可在小組中檢視內容並與其他成員共同作業  <br/> |無。  <br/> |[來賓存取經驗](https://docs.microsoft.com/en-us/microsoftteams/guest-experience) <br/> |
   
## <a name="points-to-be-aware-of-about-office-365-inter-tenant-collaboration"></a>指向要知道 Office 365 之間的租用戶共同作業的相關

### <a name="sharing-of-user-accounts-licenses-subscriptions-and-storage"></a>共用的使用者帳戶、 授權、 訂閱及儲存

每個組織維護其自己的使用者帳戶、 身分識別、 安全性群組、 訂閱、 授權及存放區。人員使用的共同作業功能在 Office 365 與共用原則和安全性設定來提供同時又不控制的公司資產所需資訊的存取權。
  
- **使用者帳戶：** 無法共用帳戶及帳戶不能重複之間的租用戶或內部部署 Active Directory 目錄服務中的分割區。 
    
- **授權&amp;訂閱：** 在 Office 365 授權的授權方案 （也稱為的 Sku 或 Office 365 計劃） 讓使用者能夠存取 Office 365 服務所定義的那些計劃。 
    
- **儲存：** Office 365 計劃中的軟體界限和限制的 SharePoint Online 管理分別從信箱儲存限制。信箱儲存限制會設定使用及管理 Exchange Online。在這兩個案例中無法儲存共用跨租用戶。 
    
### <a name="can-we-share-domain-namespaces-across-office-365-tenants"></a>我們可以在不同 Office 365 租用戶共用網域命名空間吗？

[否]。虛名網域，如 fabrikam.com 或 tailspintoys.com，只可關聯及次搭配一個承租人。每個承租人必須擁有自己的命名空間;無法跨承租人共用 UPN、 SMTP 和 SIP 命名空間。
  
### <a name="what-about-hybrid-components-and-office-365-inter-tenant-collaboration"></a>何謂混合元件和 Office 365 之間的租用戶共同作業？

無法跨多個承租人分割內部部署混合式元件，例如 Exchange 組織與 Azure AD 連線]。
  

