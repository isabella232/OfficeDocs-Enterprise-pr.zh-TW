---
title: "Contoso Corporation 的安全性"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 8f6f9894-5394-4110-8b0a-b8765028c10b
description: "摘要： 了解如何 Contoso 其安全性需求對應至 Microsoft cloud 方案中的功能和取決於雲端安全性整備的路徑。"
ms.openlocfilehash: f7c6667ce96a01771ce4f18339daf4c62173e4d9
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="security-for-the-contoso-corporation"></a>Contoso Corporation 的安全性

 **摘要：**了解如何 Contoso 其安全性需求對應至 Microsoft cloud 方案中的功能和取決於雲端安全性整備的路徑。
  
Contoso 是嚴重其資訊安全性和保護相關。轉換至雲端內含一個其 IT 基礎結構，他們進行確認其內部安全性需求所支援及 Microsoft cloud 方案中實作。
  
## <a name="contosos-security-requirements-in-the-cloud"></a>在雲端 Contoso 的安全性需求

以下是雲端 Contoso 的安全性需求：
  
- 對雲端資源的強式驗證
    
    雲端資源存取必須獲得驗證，請儘可能運用多重要素驗證。
    
- 經由網際網路的流量的加密
    
    經由網際網路傳送不含資料是純文字格式。一律使用 HTTPS 連線、 IPsec 或其他端對端資料加密方法。
    
- 在雲端中的靜態資料的加密
    
    加密的格式必須是儲存在磁碟上或其他地方雲端中的所有資料。
    
- Acl 的最低權限存取
    
    帳戶權限存取雲端中的資源與允許執行必須遵循最低指導方針。
    
## <a name="contosos-data-sensitivity-classification"></a>Contoso 的資料敏感度分類

使用 Microsoft 的[資料分類 Toolkit](https://msdn.microsoft.com/library/hh204743.aspx)中的資訊，Contoso 執行其資料分析與取決於下列層級。
  
|**層級 1： 低商業價值**|**層級 2： 中型企業價值**|**層級 3： 高商業價值**|
|:-----|:-----|:-----|
|資料會加密，僅適用於已驗證的使用者  <br/> 提供在內部部署和雲端儲存空間和工作量，例如 Office 365 中所儲存的所有資料。當它所在服務中與傳輸服務與用戶端裝置之間的資料會經過加密。  <br/> 層級 1 資料的範例是一般商務通訊 (email) 和檔案系統管理、 銷售和支援工作者。  <br/> |層級 1 加上強式驗證與資料遺失保護  <br/> 強式驗證包含 SMS 驗證的多重要素驗證。資料外洩防護可確保機密或關鍵資訊不會不旅行社內部網路之外。  <br/> 層級 2 資料的範例是財務和法律資訊及參考資料與開發的新產品的資料。  <br/> |層級 2 加上最高層級的加密、 驗證及稽核  <br/> 最高層級的加密資料靜態與雲端中，區域法規符合結合使用智慧卡及更精細稽核與警示的多重要素驗證。  <br/> 層級 3 資料的範例是客戶與合作夥伴的個人識別資訊及產品工程規格與專屬製造流程技術 （英文）。  <br/> |
   
## <a name="mapping-microsoft-cloud-offerings-and-features-to-contosos-data-levels"></a>對應至 Contoso 的資料層級的 Microsoft cloud 方案和功能

下表顯示 Microsoft cloud 版方案的 Contoso 的資料層級功能對應：
  
||**Saas 和**|**Azure PaaS**|**Azure IaaS**|
|:-----|:-----|:-----|:-----|
|層級 1： 低商業價值  <br/> | 所有連線的 HTTPS <br/>  靜態加密 <br/> | 只支援 HTTPS 連線 <br/>  加密儲存在 Azure 中的檔案 <br/> | 需要 HTTPS 或 IPsec 伺服器存取權 <br/>  Azure 磁碟加密 <br/> |
|層級 2： 中型企業價值  <br/> | 含 SMS 的 azure AD 多重要素驗證 (MFA) <br/> | 使用 Azure 機碼存放庫的加密金鑰 <br/>  含 SMS 的 azure AD MFA <br/> | 含 SMS 的 MFA <br/> |
|層級 3： 高商業價值  <br/> | Azure 版權管理系統 (RMS) <br/>  Azure AD MFA 智慧卡 <br/>  Intune 條件式存取 <br/> | Azure RMS <br/>  Azure AD MFA 智慧卡 <br/> | 使用智慧卡 MFA <br/> |
   
## <a name="contosos-information-policies"></a>Contoso 的資訊原則

下表列出 Contoso 的資訊原則。
  
||**存取**|**資料保留**|**資訊保護**|
|:-----|:-----|:-----|:-----|
|層級 1： 低商業價值  <br/> | 允許所有的存取權 <br/> |6 個月  <br/> |使用加密  <br/> |
|層級 2： 中型企業價值  <br/> | 允許存取 Contoso 員工、 承包商，與協力廠商 <br/>  使用 MFA]、 [TLS] 和 [MAM <br/> |2 年  <br/> |使用雜湊值的資料完整性  <br/> |
|層級 3： 高商業價值  <br/> | 允許行政人員及引進工程和製造流程存取權 <br/>  僅限受管理的網路裝置與 RMS <br/> |7 年  <br/> |用於不可否認性的數位簽章  <br/> |
   
## <a name="contosos-path-to-cloud-security-readiness"></a>雲端安全性整備 Contoso 的路徑

Contoso 以備妥 Microsoft cloud 其安全性使用下列步驟：
  
1. 最佳化雲端的系統管理員帳戶
    
    Contoso 未現有的 Windows Server AD 管理員帳戶廣泛檢閱，and set up 一系列的雲端系統管理員帳戶和群組。
    
2. 將三個層級執行資料分類分析
    
    Contoso 執行小心檢閱並決定三層是用來決定 Microsoft cloud 提供功能來保護 Contoso 的最有價值的資料。
    
3. 決定資料層級的存取、 保留和資訊保護原則
    
    根據資料層級，Contoso 取決於將用來限定未來要移至雲端的 IT 工作量的詳細的需求。
    
## <a name="contosos-use-of-office-365-security-best-practices"></a>Contoso 的使用的 Office 365 安全性的最佳作法

符合 Office 365 安全性最佳作法，Contoso 的安全性管理員及 IT 部門已部署下列：
  
- **專用非常強式密碼全域管理員帳戶**
    
    而是比指派全域管理員角色日常的使用者帳戶，Contoso 已建立三個，專用全域管理員帳戶具有極強式密碼。特定管理工作的僅限完成簽署以全域管理員帳戶及密碼只已知至指定的人員。Contoso 的安全性管理員已指派給所適用於該 IT 人員的工作函數與責任帳戶的系統管理員角色。
    
    如需詳細資訊，請參閱 ＜[關於 Office 365 系統管理員角色](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)。
    
- **重要的使用者帳戶的多重要素驗證 (MFA)**
    
    MFA 要求使用者確認電話、 文字訊息或應用程式通知他們的智慧型手機上正確地輸入密碼之後，登入程序新增額外的保護層級。MFA，與 Office 365 使用者帳戶受到對抗未經授權登入即使危害帳戶密碼。
    
  - 若要保護的 Office 365 訂閱危害，Contoso 啟用 MFA 所有三個全域管理員帳戶。
    
  - 網路釣魚攻擊攻擊者危及受信任的人員在組織中的認證並傳送惡意的電子郵件保護 Contoso MFA 上啟用所有使用者帳戶的管理員、 包括高階主管人員。
    
    如需詳細資訊，請參閱 ＜ [Plan for Office 365 部署的多重要素驗證](https://support.office.com/article/Plan-for-multifactor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)
    
- **進階的安全性管理 (ASM)**
    
    ASM 使用設定的原則，以監視異常活動。It 專業人員適用的不尋常或 risky 使用者活動，例如下載大量的資料、 通知設定提醒與 ASM Contoso 安全性管理員多無法登入嘗試次數或從未知或危險的 IP 位址的登入
    
    如需詳細資訊，請參閱[概觀 （英文） 的進階安全性管理 Office 365 中](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)。
    
- **安全的電子郵件流程及信箱稽核記錄**
    
    Contoso 安全性專家使用 Exchange Online Protection 和進階威脅保護 (ATP) 以防止未知的惡意程式碼、 病毒和惡意透過電子郵件傳輸的 Url。Contoso 也有已啟用的信箱稽核記錄來決定誰登入使用者信箱，傳送訊息和其他信箱擁有者、 委派的使用者或系統管理員所執行的活動。
    
    如需詳細資訊，請參閱： 
    
  - [Office 365 電子郵件反垃圾郵件保護](https://support.office.com/article/Office-365-Email-AntiSpam-Protection-6a601501-a6a8-4559-b2e7-56b59c96a586)
    
  - [進階的威脅保護安全附件和安全連結](https://technet.microsoft.com/library/mt148491.aspx)
    
  - [啟用信箱稽核在 Office 365](https://go.microsoft.com/fwlink/p/?LinkID=626109)
    
- **資料外洩防護 (DLP)**
    
    Contoso 已識別出其機密資料並設定 DLP 原則的 Exchange Online、 SharePoint Online 和 OneDrive 以協助防止使用者有意或無意之間共用資料。 
    
    如需詳細資訊，請參閱 ＜[資料外洩防護原則的概觀](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e)。
    
## <a name="see-also"></a>See Also

[在 Microsoft Cloud Contoso](contoso-in-the-microsoft-cloud.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)

[Microsoft 的 Enterprise Cloud 藍圖：IT 決策者的資源](https://sway.com/FJ2xsyWtkJc2taRD)
  
[Office 365 的安全性最佳作法](https://support.office.com/article/Security-best-practices-for-Office-365-9295e396-e53d-49b9-ae9b-0b5828cdedc3)




