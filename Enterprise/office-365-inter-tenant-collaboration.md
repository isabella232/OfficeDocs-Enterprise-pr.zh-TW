---
title: Office 365 租用戶間共同作業
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 11/08/2018
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-collaboration
- M365-subscription-management
search.appverid:
- MET150
- MOE150
ms.assetid: eb45fd8b-1d5d-4b0c-9c5a-479dbb176e7d
description: 了解 Office 365 共同作業跨租用戶和組織的運作方式。
ms.openlocfilehash: cedeab08cf6daf3817179bcf770eda6598361e67
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069669"
---
# <a name="office-365-inter-tenant-collaboration"></a>Office 365 租用戶間共同作業

本文說明幾種方式可以兩個 Office 365 租用戶間共同作業。 它適用於 Office 365 系統管理員。
  
假設兩個組織中，Fabrikam 和 Contoso，每個有 Office 365 商務版租用戶，而他們想要共同處理多個專案的專案。其中一些有限的時間執行，其中一些是進行中。 如何可以 Fabrikam 和 Contoso 啟用其人員和小組共同作業更有效率地跨越其不同的 Office 365 租用戶以安全方式？ Office 365、 Azure Active Directory B2B 共同作業、 搭配提供數種選項。 本文說明 Fabrikam 和 Contoso 可以考慮的數個關鍵案例。
  
Office 365 租用戶間共同作業選項包括使用中央位置的檔案和交談，共用行事曆，而使用 IM、 音訊/視訊通話的通訊，以及保護存取資源和應用程式。 請使用下列表格選取解決方案，並了解更多。
  
## <a name="exchange-online-collaboration-options"></a>Exchange Online 的共同作業選項

|**共用目標**|**系統管理動作**|**How to 資訊**|
|:-----|:-----|:-----|
|與另一個 Office 365 組織共用行事曆  <br/> |系統管理員可以設定不同層級的行事曆存取在 Exchange Online，讓企業與其他人共同作業與其他企業，並且讓使用者共用的排程 （空閒/忙碌資訊）  <br/> |[Exchange Online 中共用](https://technet.microsoft.com/en-us/library/jj916670%28v=exchg.150%29.aspx) <br/> [Exchange Online 中的組織關聯性](https://technet.microsoft.com/en-us/library/jj916658%28v=exchg.150%29.aspx) <br/> [在 Exchange Online 中建立組織關聯性](https://technet.microsoft.com/en-us/library/jj916671%28v=exchg.150%29.aspx) <br/> [修改與 Exchange Online 中的組織關聯性](https://technet.microsoft.com/en-us/library/jj916659%28v=exchg.150%29.aspx) <br/> [Exchange Online 中移除組織關聯性](https://technet.microsoft.com/en-us/library/jj916657%28v=exchg.150%29.aspx) <br/> [與外部使用者共用行事曆](https://support.office.com/article/fb00dd4e-2d5f-4e8d-8ff4-94b2cf002bdd) <br/> |
|控制使用者如何與組織外部人員共用行事曆  <br/> |系統管理員將共用原則套用到使用者信箱，以控制誰能與共用及授與的存取層級  <br/> |[共用 Exchange Online 中的原則](https://technet.microsoft.com/en-us/library/jj916673%28v=exchg.150%29.aspx) <br/> [在 Exchange Online 中建立共用原則](https://technet.microsoft.com/en-us/library/jj916676%28v=exchg.150%29.aspx) <br/> [將共用原則套用至 Exchange Online 中的信箱](https://technet.microsoft.com/en-us/library/jj916672%28v=exchg.150%29.aspx) <br/> [修改、 停用或移除 Exchange Online 中的共用原則](https://technet.microsoft.com/en-us/library/jj916674%28v=exchg.150%29.aspx) <br/> |
|設定安全的電子郵件通道及控制與夥伴組織的郵件流程  <br/> |系統管理員建立連接器，將安全性套用至與夥伴組織或服務提供者的郵件交換。 連接器以及允許的網域名稱限制強制加密透過傳輸層安全性 (TLS) 或 IP 位址範圍從協力廠商傳送電子郵件。  <br/> |[Exchange Online 如何使用 TLS 來保護 Office 365 中的電子郵件連線](https://technet.microsoft.com/en-us/library/mt163898.aspx) <br/> [Configure mail flow using connectors in Office 365](https://technet.microsoft.com/en-us/library/ms.exch.eac.connectorselection%28v=exchg.150%29.aspx) <br/> [Exchange Online 中的遠端網域](https://technet.microsoft.com/en-us/library/jj966211%28v=exchg.150%29.aspx) <br/> [設定與夥伴組織的安全郵件流程的連接器](https://technet.microsoft.com/en-us/library/dn751021%28v=exchg.150%29.aspx) <br/> [Exchange Online 和 Office 365 (overview) 的郵件流程最佳做法](https://technet.microsoft.com/en-us/library/0e6cd9d5-ad3e-418a-8ea9-3bf33332c491%28v=exchg.150%29) <br/> |
   
## <a name="sharepoint-online-and-onedrive-for-business-collaboration-options"></a>SharePoint Online 和 OneDrive for Business 共同作業選項

|**共用目標**|**系統管理動作**|**How to 資訊**|
|:-----|:-----|:-----|
|與外部使用者共用網站和文件  <br/> |系統管理員設定共用，租用戶或網站集合層級的通過驗證的 Microsoft 帳戶、 公司或學校帳戶已驗證或來賓帳戶  <br/> |
  [管理您的 SharePoint Online 環境外部共用](https://support.office.com/en-US/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> [受限的網域共用 Office 365 中 SharePoint Online 和 OneDrive for Business](https://support.office.com/en-US/article/Restricted-Domains-Sharing-in-Office-365-SharePoint-Online-and-OneDrive-for-Business-5d7589cd-0997-4a00-a2ba-2320ec49c4e9) <br/> [使用 SharePoint Online 做為企業對企業 (B2B) 的外部網路解決方案](https://support.office.com/article/7b087413-165a-4e94-8871-4393e0b9c037) <br/> |
|追蹤及控制使用者的外部共用  <br/> |OneDrive for Business 檔案擁有者和 SharePoint Online 使用者設定的網站和文件共用，並建立追蹤共用通知  <br/> |[設定商務用 OneDrive 外部共用通知](https://support.office.com/en-US/article/Configure-notifications-for-external-sharing-for-OneDrive-for-Business-b640c693-f170-4227-b8c1-b0a7e0fa876b) <br/> [在 Office 365 中共用 SharePoint 檔案或資料夾](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) (機器翻譯) <br/> |
   
## <a name="skype-for-business-collaboration-options"></a>Skype 商務共同作業選項

|**共用目標**|**系統管理動作**|**How to 資訊**|
|:-----|:-----|:-----|
|Skype 商務 Online-IM、 呼叫和目前狀態與其他 Skype 商務使用者  <br/> |系統管理員可以啟用其 Skype for Business Online IM 使用者、 撥打音訊/視訊，並查看與另一個 Office 365 租用戶中使用者的目前狀態。  <br/> |[允許使用者連絡外部商務用 Skype 使用者](https://support.office.com/article/b414873a-0059-4cd5-aea1-e5d0857dbc94) <br/> |
|Skype 商務 Online-IM、 通話，以及與 Skype （消費者） 使用者的目前狀態  <br/> |系統管理員可以啟用其 Skype for Business Online 使用者 IM、 撥打電話，並查看與 Skype （消費者） 使用者的目前狀態。  <br/> |[讓商務用 Skype 商務版使用者加入 Skype 連絡人](https://support.office.com/article/08666236-1894-42ae-8846-e49232bbc460) <br/> |
   
## <a name="azure-ad-b2b-collaboration-options"></a>Azure AD B2B 共同作業選項

|**共用目標**|**系統管理動作**|**How to 資訊**|
|:-----|:-----|:-----|
|Azure AD B2B 共同作業-藉由新增至組織的目錄中的群組的外部使用者共用的內容  <br/> |一個 Office 365 租用戶的全域系統管理員可以邀請人員參加他們的目錄，另一個 Office 365 租用戶中將這些外部使用者新增至群組，並授與存取權的內容，例如 SharePoint 網站和文件庫的群組。  <br/> |[什麼是 Azure AD B2B 共同作業預覽？](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) <br/> [Azure AD B2B： 新的更新很容易跨商業協同](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/01/azure-ad-b2b-new-updates-make-cross-business-collab-easy/) <br/> [Office 365 外部共用和 Azure Active Directory B2B 共同作業](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-o365-external-user) <br/> [Azure Active Directory B2B 共同作業的 API 與自訂](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-api) <br/> [Azure AD 和身分識別放映： Azure AD B2B 共同作業 （企業對企業](https://channel9.msdn.com/Series/Azure-AD-Identity/AzureADB2B) <br/> |
   
## <a name="office-365-collaboration-options"></a>Office 365 共同作業選項

|**共用目標**|**系統管理動作**|**How to 資訊**|
|:-----|:-----|:-----|
|Office 365 群組-電子郵件、 行事曆、 OneNote，以及在集中位置的共用的檔案  <br/> |群組都支援商務基本版、 商務進階版、 教育和企業版 E1、 E3 和 E5 方案。 一個 Office 365 租用戶中的人員可以建立群組，並邀請另一個 Office 365 租用戶中的人員為來賓使用者。 也適用於 Dynamics CRM。  <br/> |[了解 Office 365 群組](https://support.office.com/article/b565caa1-5c40-40ef-9915-60fdb2d97fa2) <br/> [在 Office 365 群組的來賓存取](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6) <br/> [部署 Office 365 群組](https://technet.microsoft.com/en-us/library/dn896591.aspx) <br/> |
   
## <a name="yammer-collaboration-options"></a>Yammer 共同作業選項

|**共用目標**|**系統管理動作**|**How to 資訊**|
|:-----|:-----|:-----|
|Yammer-透過企業社交媒體的共同作業  <br/> |除非外部群組建立能力的 Yammer 系統管理員會停用，使用者可以建立透過交談，能夠 like 遵循文章、 共用檔案，並聊天室線上共同作業 Yammer 中的外部群組。  <br/> |[在 Yammer 建立及管理外部群組](https://support.office.com/article/9ccd15ce-0efc-4dc1-81bc-4a424ab6f92a) (機器翻譯) <br/> |
   
## <a name="teams-collaboration-options"></a>小組共同作業選項

|**共用目標**|**系統管理動作**|**How to 資訊**|
|:-----|:-----|:-----|
|在 [小組與組織外部的使用者進行共同作業  <br/> |邀請其他 Office 365 租用戶的全域系統管理員必須啟用外部小組共同作業。 全域系統管理員和小組擁有者現在無法邀請小組的共同作業的電子郵件地址的任何人。  <br/> 系統管理員也可以管理，並編輯來賓其租用戶中已經存在。  <br/> |[授權的來賓存取](https://docs.microsoft.com/en-us/microsoftteams/teams-dependencies) <br/> [在小組中開啟或關閉開啟的來賓存取](https://docs.microsoft.com/en-us/microsoftteams/set-up-guests) <br/> [使用 PowerShell 來控制來賓存取](https://docs.microsoft.com/en-us/microsoftteams/guest-access-powershell) <br/> [來賓存取檢查清單](https://docs.microsoft.com/en-us/microsoftteams/guest-access-checklist) <br/> [檢視來賓使用者](https://docs.microsoft.com/en-us/microsoftteams/view-guests) <br/> [編輯來賓使用者資訊](https://docs.microsoft.com/en-us/microsoftteams/edit-guests-information) <br/> |
|小組擁有者可以邀請，並管理來賓與其小組的共同作業。  <br/> |小組擁有者具有來賓可進行其小組內的其他控制項。  <br/> |[新增來賓](https://support.office.com/en-us/article/teams-and-channels-df38ae23-8f85-46d3-b071-cb11b9de5499?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_addingguests&amp;ID0EAABAAA=Add_guests) <br/> [將來賓加入到小組](https://docs.microsoft.com/en-us/microsoftteams/add-guests) <br/> [Teams 中管理來賓存取](https://docs.microsoft.com/en-us/microsoftteams/manage-guests) <br/> [看誰在小組成員或通道](https://support.office.com/en-us/article/see-who-s-on-a-team-or-in-a-channel-5c6be9be-9c45-4a0f-a1a0-f332b23cb6b7?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> |
|從其他租用戶的來賓可在小組中檢視內容和共同作業與其他成員  <br/> |無。  <br/> |[來賓存取經驗](https://docs.microsoft.com/en-us/microsoftteams/guest-experience) <br/> |

## <a name="power-bi-collaboration-options"></a>Power BI 共同作業選項

|**共用目標**|**系統管理動作**|**How to 資訊**|
|:-----|:-----|:-----|
|Power BI 可讓外部來賓使用者耗用透過連結共用的內容。 這可讓組織中的使用者內容的安全的方式分散的組織。<br/> | Power BI 系統管理員可以控制使用者是否可以邀請外部使用者能夠檢視組織內的內容。 <br/> |[發佈與 Azure AD B2B 外部來賓使用者的 Power BI 內容](https://docs.microsoft.com/en-us/power-bi/service-admin-azure-ad-b2b) <br/> |
 
## <a name="points-to-be-aware-of-about-office-365-inter-tenant-collaboration"></a>指向要知道關於 Office 365 租用戶間共同作業

### <a name="sharing-of-user-accounts-licenses-subscriptions-and-storage"></a>共用的使用者帳戶、 授權、 訂用帳戶，以及儲存體

每個組織維護自己的使用者帳戶、 身分識別、 安全性群組、 訂用帳戶、 授權及儲存。 人員在 Office 365 中，搭配共用原則和安全性設定提供所需的資訊，同時維護控制的公司資產的存取權，使用的共同作業功能。
  
- **使用者帳戶：** 無法共用帳戶及帳戶不能重複項目之間的租用戶或在內部部署 Active Directory 目錄服務中的分割區。 
    
- **授權&amp;訂用帳戶：** 在 Office 365 授權從授權計劃 （也稱為的 Sku 或 Office 365 計劃） 讓使用者能夠存取 Office 365 服務所定義的那些計劃。 
    
- **儲存體：** Office 365 計劃中的 SharePoint Online 軟體界限及限制為分別管理從信箱儲存限制。 信箱儲存限制會設定並管理，使用 Exchange Online。 在這兩個案例中無法跨租用戶共用儲存。 
    
### <a name="can-we-share-domain-namespaces-across-office-365-tenants"></a>我們可以跨 Office 365 租用戶共用網域命名空間嗎？

否。 虛名網域，例如 fabrikam.com 或 tailspintoys.com，只可關聯及次搭配一個租用戶。 每個租用戶必須有它自己的命名空間。無法跨租用戶共用 UPN、 SMTP 和 SIP 命名空間。
  
### <a name="what-about-hybrid-components-and-office-365-inter-tenant-collaboration"></a>關於混合式元件和 Office 365 租用戶間共同作業功能？

內部部署混合式元件，例如 Exchange 組織與 Azure AD Connect，無法分割到多個承租人。
  

