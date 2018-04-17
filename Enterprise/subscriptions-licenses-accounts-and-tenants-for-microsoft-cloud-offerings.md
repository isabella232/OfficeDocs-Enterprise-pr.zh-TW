---
title: 訂閱、 授權、 帳戶、 及承租人 Microsoft cloud 方案
ms.author: josephd
author: JoeDavies-MSFT
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
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
description: 摘要： 了解 Microsoft cloud 方案跨組織、 訂閱、 授權、 使用者帳戶和租用戶的關係。
ms.openlocfilehash: ff4854bc66f9a500715bbcd2da696b9a4519aa82
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a>訂閱、 授權、 帳戶、 及承租人 Microsoft cloud 方案

 **摘要：**跨 Microsoft cloud 方案瞭解組織、 訂閱、 授權、 使用者帳戶和租用戶的關係。
  
Microsoft 提供跨其雲端方案的身分識別和帳務使用一致的組織、 訂閱、 授權及使用者帳戶階層：
  
- Microsoft Office 365
    
    請參閱[商業計畫和定價](https://products.office.com/business/compare-office-365-for-business-plans)的詳細資訊。
    
- Microsoft Azure
    
    請參閱[Azure 定價](https://azure.microsoft.com/pricing/)的詳細資訊。
    
- Microsoft Intune 和 Enterprise 行動性 + 安全性 （EMS）
    
    請參閱[Intune 定價](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing)的詳細資訊。
    
- Microsoft Dynamics 365
    
    請參閱[Dynamics 365 定價](https://dynamics.microsoft.com/)的詳細資訊。
    
## <a name="elements-of-the-hierarchy"></a>階層的元素

以下是階層中的元素：
  
### <a name="organization"></a>組織

組織代表使用 Microsoft cloud 方案，通常是由公用網域名稱系統 (DNS) 網域名稱等 contoso.com 識別商務實體。組織已訂閱的容器。
  
### <a name="subscriptions"></a>訂閱

訂閱是與 Microsoft 合約，以使用下列一個或多個 Microsoft cloud 平台或服務，其費用累根據每個使用者授權費用或雲端式資源已消耗。Microsoft 的軟體即服務 (SaaS)-根據的雲端方案 （Office 365、 Intune/EMS 和 Dynamics 365） 收費每個使用者授權手續費。Microsoft 的平台服務 (PaaS) 和基礎架構以根據雲端資源已消耗服務 (IaaS) 雲端方案 (Azure) 收費。
  
您也可以使用試用版訂閱，但是訂閱到期時間或已消耗收費的特定時間之後。您可以將試用訂閱轉換為付費訂閱。
  
組織可以有多個訂閱 Microsoft cloud 方案。圖 1 顯示的範例。
  
**圖 1： 範例中的多個訂閱的組織**

![具有多個 Microsoft 雲端供應項目訂閱的組織範例。](images/Subscriptions/Subscriptions_Fig1.png)

  
圖 1 顯示單一組織中具有多個 Office 365 訂閱、 Intune 訂閱、 Dynamics 365 訂閱及多個 Azure 訂閱的。
  
### <a name="licenses"></a>授權

Microsoft 的 saas 和雲端方案、 授權可讓特定的使用者帳戶使用的雲端服務提供。您會為您的訂閱的一部分內固定的月費。系統管理員會將授權指派給訂閱中的個別使用者帳戶。圖 2 中的範例，Contoso Corporation 有 100 授權 Office 365 企業版 E5 訂閱允許最多 100 個個別的使用者帳戶使用企業 E5 功能與服務。
  
**Saas 和型訂閱的組織內的圖 2： 授權**

![Microsoft SaaS 型雲端供應項目的訂閱中多個授權的範例。](images/Subscriptions/Subscriptions_Fig2.png)
  
Azure PaaS 型 cloud services 軟體授權是內建服務定價。
  
Azure IaaS 式虛擬機器時的其他授權，可使用 「 軟體 」 或 「 虛擬機器映像上安裝的應用程式可能就需要。某些虛擬機器映像已授權版本的軟體安裝和成本隨附之伺服器的每分鐘速率。以下範例列出 SQL Server 2014 和 SQL Server 2016 虛擬機器映像。 
  
某些虛擬機器映像已安裝的應用程式的試用版本需要和其他軟體應用程式授權的超過試驗期間使用。例如，SharePoint Server 2016 試用版虛擬機器映像包含預先安裝的 SharePoint Server 2016 試用版。若要繼續使用 SharePoint Server 2016 記錄到期日期之後，您必須購買 microsoft 的 SharePoint Server 2016 授權和用戶端授權。這些費用是分開的 Azure 訂閱及仍適用於執行虛擬機器的每分鐘速率。
  
### <a name="user-accounts"></a>使用者帳戶

Microsoft 雲端方案的所有使用者帳戶都儲存在 Azure Active Directory (AD) 租用戶，其中包含使用者帳戶和群組。Azure AD 租用戶可以與現有的 Windows Server AD 帳戶使用 Azure AD 連接中的 Windows server 型服務同步處理。這就是所謂目錄同步處理 (DirSync)。
  
圖 3 顯示的多個訂閱使用包含組織帳戶的一般 Azure AD 租用戶組織的範例。
  
**圖 3： 多個訂閱的組織使用相同的 Azure AD 租用戶**

![具有全部使用相同 Azure AD 租用戶的多個訂閱的組織範例。](images/Subscriptions/Subscriptions_Fig3.png)
  
### <a name="tenants"></a>承租人

Saas 和雲端方案、 租用戶是提供雲端服務伺服器設施區域性位置。例如，Contoso Corporation 選擇來裝載在其 Paris headquarters 15000 工作者其 Office 365、 EMS 及 Dynamics 365 租用戶的歐洲地區。
  
Azure PaaS 服務和虛擬機器型工作量架設在 Azure IaaS 可以在任何 Azure 資料中心內的租用在全世界。您指定當您建立 Azure PaaS 應用程式或服務或 IaaS 工作量的元素稱為位置的 Azure 資料中心。
  
Azure AD 租用戶是含有帳戶和群組的 Azure AD 的特定執行個體。Office 365、 Dynamics 365 或 Intune/EMS 付費或試用版訂閱包括免費 Azure AD 租用戶。此 Azure AD 租用戶不包括其他 Azure 服務且並非 Azure 試用版或付費訂閱相同。
  
### <a name="summary-of-the-hierarchy"></a>摘要階層。

以下是快速回顧：
  
- 組織可以有多個訂閱
    
  - 訂閱可以有多個授權
    
  - 授權可指派給個別使用者帳戶
    
  - Azure AD 租用戶中儲存的使用者帳戶
    
以下是關係的範例組織、 訂閱、 授權及使用者帳戶：
  
- 由其公用網域名稱識別組織。
    
  - 使用者授權與 Office 365 企業版 E3 訂閱。
    
    使用者授權與 Office 365 企業版 E5 訂閱。
    
    使用者授權 EMS 訂閱。
    
    Dynamics 365 使用者授權與訂閱。
    
    多個 Azure 訂閱。
    
  - 中常見的 Azure AD 租用戶組織的使用者帳戶。
    
多個 Microsoft cloud 提供訂閱可以使用相同的 Azure AD 租用戶，做為一般的身分識別提供者。管理中心 Azure AD 租用戶包含內部部署 Windows Server AD 同步處理的帳戶以服務 (IDaaS) 提供雲端式身分識別您的組織。這是由圖 4 所示。
  
**圖 4： 同步處理內部部署帳戶和 IDaaS 組織**

![貴組織的識別即服務 (IaaS)。](images/Subscriptions/Subscriptions_Fig4.png)
  
圖 4 顯示一般的 Azure AD 租用戶使用 Microsoft 的 saas 和雲端方案、 Azure PaaS 應用程式]，並使用 Azure AD 網域服務的 Azure IaaS 中的虛擬機器的方式。Azure AD 連線將內部部署 Windows Server AD 樹系同步處理與 Azure AD 租用。
  
如需 Microsoft cloud 方案不同的身分識別整合的詳細資訊，請參閱[Microsoft 雲端身分識別的企業架構師](https://aka.ms/cloudarchidentity)。
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a>結合多個 Microsoft cloud 方案訂閱

下表說明如何將合併已經有訂閱為基礎的多個 Microsoft cloud 方案的一種雲端提供 （往第一欄的標籤） 及新增其他雲端的訂閱類型 （不必跨可以資料行）。
  
||**Office 365**|**Azure**|**Intune/EMS**|**Dynamics 365**|
|:-----|:-----|:-----|:-----|:-----|
|**Office 365** <br/> |NA  <br/> |您新增至您組織的 Azure 訂閱從 Azure 入口網站。  <br/> |從 Office 365 入口網站的 Intune/EMS 訂閱加入您的組織中。  <br/> |從 Office 365 入口網站會新增 Dynamics 365 訂閱至您的組織。  <br/> |
|**Azure** <br/> |Office 365 訂閱新增至您的組織。  <br/> |NA  <br/> |Intune/EMS 訂閱新增至您的組織。  <br/> |會新增 Dynamics 365 訂閱至您的組織。  <br/> |
|**Intune/EMS** <br/> |Office 365 訂閱新增至您的組織。  <br/> |您新增至您組織的 Azure 訂閱從 Azure 入口網站。  <br/> |NA  <br/> |會新增 Dynamics 365 訂閱至您的組織。  <br/> |
|**Dynamics 365** <br/> |Office 365 訂閱新增至您的組織。  <br/> |您新增至您組織的 Azure 訂閱從 Azure 入口網站。  <br/> |Intune/EMS 訂閱新增至您的組織。  <br/> |NA  <br/> |
   
簡單的方法來將訂閱新增至 Microsoft SaaS 式服務的組織是透過 Office 365 系統管理中心：
  
1. 登入 Office 365 入口網站 ([https://portal.office.com](https://portal.office.com)) 與您的全域管理員帳戶，並按一下 [**管理**。
    
2. 左導覽列中的 [**管理中心**] 首頁上，按一下 [**計費**，然後**購買服務**]。
    
3. 在 [**購買服務**] 頁面上購買新訂閱。
    
Office 365 系統管理中心會將新的訂閱 saas 和型雲端版方案的組織與 Office 365 訂閱的 Azure AD 租用戶。
  
若要為您的 Office 365 訂閱新增 Azure AD 租用戶的相同組織與 Azure 訂閱：
  
1. 登入 Azure 入口網站 ([https://portal.azure.com](https://portal.azure.com)) 與您的 Office 365 全域管理員帳戶。
    
2. 在左導覽列中，[**訂閱**，和 [**新增]**。
    
3. 在 [**新增訂閱**] 頁面上選取產品項目並完成付款資訊及合約。
    
如果您另外購買 Azure 和 Office 365 訂閱而且想要從您的 Azure 訂閱存取 Office 365 Azure AD 租用戶，請參閱[建立關聯的 Azure 訂閱與 Office 365 租用戶](https://channel9.msdn.com/Series/Microsoft-Azure-Tutorials/Associate-an-Office-365-tenant-with-an-Azure-subscription)中的指示。
  
## <a name="see-also"></a>請參閱

[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)
  
[雲端採用測試實驗室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[適用於 SharePoint、Exchange、Skype for Business 和 Lync 的架構模型](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[混合式解決方案](hybrid-solutions.md)
  
[訂閱、 授權及使用者帳戶為 Contoso Corporation](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md)



