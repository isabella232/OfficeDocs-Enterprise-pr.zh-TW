---
title: >
  Microsoft 雲端供應項目的訂用帳戶、授權、帳戶及租用戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/12/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Architecture
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
description: 摘要：了解所有 Microsoft 雲端供應項目上的組織、訂用帳戶、授權、使用者帳戶、租用戶之間的關係。
ms.openlocfilehash: 5f434fef42777034d32970dd55e15be35b76961e
ms.sourcegitcommit: d0f1f34b1702e304fec85ca72f1f660e9b328dd5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2018
ms.locfileid: "24022072"
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a>Microsoft 雲端供應項目的訂用帳戶、授權、帳戶及租用戶


 **摘要：** 了解所有 Microsoft 雲端供應項目上的組織、訂用帳戶、授權、使用者帳戶、租用戶之間的關係。
  
Microsoft 提供了組織、訂用帳戶、授權、使用者帳戶的階層，讓您在所有雲端供應項目中能使用一致的身分識別和計費方式：

  
- Microsoft Office 365
    
    詳細資訊請參閱[企業方案與價格](https://products.office.com/business/compare-office-365-for-business-plans)。
    
- Microsoft Azure
    
    詳細資訊請參閱 [Azure 價格](https://azure.microsoft.com/pricing/)。
    
- Microsoft Intune 與 Enterprise Mobility + Security (EMS)
    
    詳細資訊請參閱 [Intune 價格](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing)。
    
- Microsoft Dynamics 365
    
    詳細資訊請參閱 [Dynamics 365 價格](https://dynamics.microsoft.com/)。
    
## <a name="elements-of-the-hierarchy"></a>階層的元素

以下是階層的元素：
  
### <a name="organization"></a>組織

組織代表正在使用 Microsoft 雲端供應項目的商業實體，通常是用一個或多個公用網域名稱 (DNS)，例如 contoso.com 加以識別。組織是訂用帳戶的容器。
  
### <a name="subscriptions"></a>訂用帳戶

訂用帳戶是與 Microsoft 的協議，同意使用一或多個 Microsoft 雲端平台或服務，並根據每個使用者授權費用或雲端資源耗用量來累算費用。Microsoft 的「軟體即服務」(SaaS) 雲端供應項目 (Office 365、Intune/EMS、Dynamics 365) 會依據每個使用者授權費用收費。Microsoft 的「平台即服務」(PaaS) 和「基礎結構即服務」(IaaS) 雲端供應項目 (Azure) 會依據雲端資源耗用量收費。
  
您也可以使用試用版的訂用帳戶，但在使用特定一段時間或耗用量之後，訂用帳戶便到期。您可以將試用版訂用帳戶轉換為付費訂用帳戶。
  
組織可有多個訂用帳戶，用於 Microsoft 的多個雲端供應項目。圖 1 為其範例。
  
**圖 1：組織的多個訂用帳戶範例**

![具有多個 Microsoft 雲端供應項目訂用帳戶的組織範例。](media/Subscriptions/Subscriptions-Fig1.png)

  
圖 1 顯示單一組織有多個 Office 365 訂用帳戶、一個 Intune 訂用帳戶、一個 Dynamics 365 訂用帳戶、多個 Azure 訂用帳戶。
  
### <a name="licenses"></a>授權

使用 Microsoft 的 SaaS 雲端供應項目時，授權允許特定使用者帳戶使用該雲端供應項目的服務。固定的每月費用是訂用帳戶的其中一環。系統管理員將授權指派給訂用帳戶中的個別使用者帳戶。在圖 2 的範例中，Contoso 公司有 100 個 Office 365 企業版 E5 的授權， 可讓最多 100 個個別使用者帳戶使用企業版 E5 的功能與服務。
  
**圖 2：SaaS 型訂用帳戶中的組織授權**

![Microsoft SaaS 型雲端供應項目訂用帳戶中多個授權的範例。](media/Subscriptions/Subscriptions-Fig2.png)
  
使用 Azure PaaS 型雲端服務時，服務費用已包含軟體授權。
  
使用 Azure IaaS  型虛擬機器時，可能會需要額外的授權來使用安裝在虛擬機器映像上的軟體或應用程式。部分虛擬機器映像已安裝軟體的授權版本，費用是由伺服器的每一分鐘費率涵蓋。例如 SQL Server 2014 和 SQL Server 2016 的虛擬機器映像。 
  
部分虛擬機器映像已安裝試用版應用程式，在試用期間過後需要額外的軟體應用程式授權。例如，SharePoint Server 2016 試用版的虛擬機器映像包含預先安裝的 SharePoint Server 2016 試用版。若要在試用到期日之後繼續使用 SharePoint Server 2016，您必須向 Microsoft 購買 SharePoint Server 2016 授權和用戶端授權。這些費用和 Azure 訂用帳戶是分開的，且仍需支付執行虛擬機器的每一分鐘費率。
  
### <a name="user-accounts"></a>使用者帳戶

所有 Microsoft 雲端供應項目的使用者帳戶都儲存在 Azure Active Directory (AD) 租用戶，此租用戶包含使用者帳戶和群組。Azure AD Connect 是 Windows 的伺服器型服務，可以將 Azure AD 租用戶與您的現有 Windows Server AD 帳戶同步。這就是所謂的目錄同步處理 (DirSync)。
  
圖 3 顯示組織的多個訂用帳戶使用同一個 Azure AD 租用戶，租用戶包含組織的帳戶。
  
**圖 3：組織的多個訂用帳戶使用相同 Azure AD 租用戶的範例。**

![多個訂用帳戶皆使用相同 Azure AD 租用戶的組織範例。](media/Subscriptions/Subscriptions-Fig3.png)
  
### <a name="tenants"></a>租用戶

使用 SaaS 雲端供應項目時，租用戶是指存放提供雲端服務的伺服器的區域位置。例如，Contoso 公司選擇以歐洲區域來裝載它的 Office 365、EMS、Dynamics 365 租用戶，供其巴黎總公司的 15,000 名員工使用。
  
Azure PaaS 服務和虛擬機器的工作負載裝載於 Azure IaaS 中，可以將租用戶放在世界各地的 Azure 資料中心內。當您建立 Azure PaaS 應用程式或服務或 IaaS 工作負載的元素時，由您指定 Azure 資料中心 (稱為「位置」)。
  
Azure AD 租用戶是包含帳戶和群組的 Azure AD 的特定執行個體。付費版或試用版的 Office 365、Dynamics 365 或 Intune/EMS 訂用帳戶包含一個免費 Azure AD 租用戶。這個 Azure AD 租用戶不包含其他 Azure 服務，和 Azure 試用版或付費版訂用帳戶不同。
  
### <a name="summary-of-the-hierarchy"></a>階層摘要

以下是重點複習：
  
- 組織可以有多個訂用帳戶。
    
  - 訂用帳戶可以有多個授權。
    
  - 授權可以指派給個別使用者帳戶。
    
  - 使用者帳戶儲存在 Azure AD 租用戶。
    
以下是組織、訂用帳戶、授權、使用者帳戶的關係範例：
  
- 組織由其公用網域名稱加以識別。

    
  - Office 365 企業版 E3 訂用帳戶包含使用者授權。
    
    Office 365 企業版 E5 訂用帳戶包含使用者授權。
    
    EMS 訂用帳戶包含使用者授權。
    
    Dynamics 365 訂用帳戶包含使用者授權。
    
    多個 Azure 訂用帳戶。

    
  - 組織的使用者帳戶在同一 Azure AD 租用戶中。
    
多個 Microsoft 雲端供應項目的訂用帳戶可以使用相同 Azure AD 租用戶作為共同的身分識別提供者。集中的 Azure AD 租用戶包含內部部署 Windows Server AD 同步處理的帳戶，可為組織提供雲端上的身分識別即服務 (IDaaS)。如圖 4 所示。
  
**圖 4： 組織同步處理的內部部署帳戶和 IDaaS**

![組織的身分識別即服務 (IaaS) IDaaS。](media/Subscriptions/Subscriptions-Fig4.png)
  
在圖 4 中，Microsoft 的 SaaS 雲端供應項目、Azure PaaS 應用程式、使用 Azure AD 網域服務的 Azure IaaS 中的虛擬機器，三者使用同一個 Azure AD 租用戶。Azure AD Connect 將內部部署的 Windows Server AD 樹系和 Azure AD 租用戶同步。
  
有關 Microsoft 雲端供應項目的身分識別整合，詳細資訊請參閱[企業架構的 Microsoft 雲端身分識別](https://aka.ms/cloudarchidentity)。
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a>合併多個 Microsoft 雲端供應項目的訂用帳戶

下表說明如何以已有的一種雲端供應項目的一個訂用帳戶為本，合併多個 Microsoft 雲端供應項目 (表中的第一個直列)，以及如何為不同的雲端供應項目新增訂用帳戶 (表中的橫行)。
  
||**Office 365**|**Azure**|**Intune/EMS**|**Dynamics 365**|
|:-----|:-----|:-----|:-----|:-----|
|**Office 365** <br/> |NA  <br/> |您在 Azure 入口網站中為組織新增 Azure 訂用帳戶。  <br/> |您在  Office 365 入口網站中為組織新增 Intune/EMS 訂用帳戶。  <br/> |您在  Office 365 入口網站中為組織新增 Dynamics 365 訂用帳戶。  <br/> |
|**Azure** <br/> |您為組織新增 Office 365 訂用帳戶。  <br/> |NA  <br/> |您為組織新增 Intune/EMS 訂用帳戶。  <br/> |您為組織新增 Dynamics 365 訂用帳戶。  <br/> |
|**Intune/EMS** <br/> |您為組織新增 Office 365 訂用帳戶。  <br/> |您在 Azure 入口網站中為組織新增 Azure 訂用帳戶。  <br/> |NA  <br/> |您為組織新增 Dynamics 365 訂用帳戶。  <br/> |
|**Dynamics 365** <br/> |您為組織新增 Office 365 訂用帳戶。  <br/> |您在 Azure 入口網站中為組織新增 Azure 訂用帳戶。  <br/> |您為組織新增 Intune/EMS 訂用帳戶。  <br/> |NA  <br/> |
   
要將 Microsoft SaaS 服務的訂用帳戶新增到組織，簡單的做法是透過 Office 365 管理中心：
  
1. 使用全域系統管理員帳戶登入 Office 365 入口網站 ([https://portal.office.com](https://portal.office.com))，然後按一下 [管理]****。
    
2. 在 [管理中心]**** 首頁的導覽窗格中，按一下 [計費]****，然後按一下 [購買服務]****。
    
3. 在 [購買服務]**** 頁面上，購買新的訂用帳戶。
    
Office 365 管理中心會將組織和 Office 365 訂用帳戶的 Azure AD 租用戶，指派給 SaaS 雲端供應項目的新訂用帳戶。
  
使用與 Office 365 訂用帳戶相同的組織和 Azure AD 租用戶進行新增：
  
1. 使用 Office 365 全域管理員帳戶登入 Azure 入口網站 ([https://portal.azure.com](https://portal.azure.com))。
    
2. 在左側導覽窗格中，按一下 [訂用帳戶]****，然後按一下 [新增]****。
    
3. 在 [新增訂用帳戶]**** 頁面上，選取供應項目，並填寫付款資訊和合約。
    
如果您已另外購買 Azure 與 Office 365 訂用帳戶，想要從您的 Azure 訂用帳戶存取 Office 365 Azure AD 租用戶，請參閱[建立 Office 365 租用戶與 Azure 訂用帳戶的關聯](https://channel9.msdn.com/Series/Microsoft-Azure-Tutorials/Associate-an-Office-365-tenant-with-an-Azure-subscription)中的指示。
  
## <a name="see-also"></a>另請參閱

[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)
  
[雲端採用測試實驗室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[適用於 SharePoint、Exchange、商務用 Skype 和 Lync 的架構模型](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[混合式解決方案](hybrid-solutions.md)
  
