---
title: >
  Microsoft 雲端供應項目的訂用帳戶、授權、帳戶及租用戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/08/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Architecture
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
description: 摘要：了解所有 Microsoft 雲端供應項目上的組織、訂用帳戶、授權、使用者帳戶、租用戶之間的關係。
ms.openlocfilehash: ad4307b2725fa37f6b28540b92895fc78f097c6c
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2020
ms.locfileid: "44735961"
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a>Microsoft 雲端供應項目的訂用帳戶、授權、帳戶及租用戶


 **摘要：** 了解所有 Microsoft 雲端供應項目上的組織、訂用帳戶、授權、使用者帳戶、租用戶之間的關係。
  
Microsoft 提供了組織、訂用帳戶、授權、使用者帳戶的階層，讓您在所有雲端供應項目中能使用一致的身分識別和計費方式：

  
- Microsoft Office 365
- Microsoft Azure
- Microsoft Intune 和 Enterprise 可移動性 + Security （EMS）
- Microsoft Dynamics 365

[Microsoft 365](https://docs.microsoft.com/microsoft-365/) 將 Office 365、EMS 和 Windows 10 企業版整合到單一訂閱和整合式服務集合中。

## <a name="elements-of-the-hierarchy"></a>階層的元素

以下是階層的元素：
  
### <a name="organization"></a>組織

An organization represents a business entity that is using Microsoft cloud offerings, typically identified by one or more public Domain Name System (DNS) domain names, such as contoso.com. The organization is a container for subscriptions.
  
### <a name="subscriptions"></a>訂閱

訂閱是與 Microsoft 簽訂使用一或多個 Microsoft 雲端平台或服務的合約，其費用會根據每位使用者的授權費用或雲端資源使用量而產生。 

- Microsoft 的軟體即服務 (SaaS) 型雲端供應項目 (Office 365、Intune/EMS 和 Dynamics 365) 是依每位使用者授權費用來收費。 
- Microsoft 的平台即服務 (PaaS) 和基礎結構即服務 (IaaS) 雲端供應項目 (Azure) 是根據雲端資源的使用量來收費。
 
You can also use a trial subscription, but the subscription expires after a specific amount of time or consumption charges. You can convert a trial subscription to a paid subscription.
  
組織可有多個訂用帳戶，用於 Microsoft 的多個雲端供應項目。 圖 1 顯示單一組織有多個 Office 365 訂用帳戶、一個 Intune 訂用帳戶、一個 Dynamics 365 訂用帳戶、多個 Azure 訂用帳戶。

**圖 1：組織的多個訂用帳戶範例**

![具有多個 Microsoft 雲端供應項目訂用帳戶的組織範例。](media/Subscriptions/Subscriptions-Fig1.png)

  
### <a name="licenses"></a>授權

針對 Microsoft SaaS 雲端供應項目，授權可讓特定使用者帳戶使用雲端供應項目服務。 會向您收取每月固定的訂閱費用。 系統管理員會將授權指派給訂閱中的個別使用者帳戶。 如圖 2 所示範例，Contoso Corporation 擁有包含 100 個授權的 Office 365 企業版 E5 訂閱，可讓最多 100 個個別使用者帳戶使用 Office 365 企業版 E5 的功能與服務。
  
**圖 2：SaaS 型訂用帳戶中的組織授權**

![Microsoft SaaS 型雲端供應項目訂用帳戶中多個授權的範例。](media/Subscriptions/Subscriptions-Fig2.png)
  
使用 Azure PaaS 型雲端服務時，服務費用已包含軟體授權。
  
For Azure IaaS-based virtual machines, additional licenses to use the software or application installed on a virtual machine image might be required. Some virtual machine images have licensed versions of software installed and the cost is included in the per-minute rate for the server. Examples are the virtual machine images for SQL Server 2014 and SQL Server 2016. 
  
Some virtual machine images have trial versions of applications installed and need additional software application licenses for use beyond the trial period. For example, the SharePoint Server 2016 Trial virtual machine image includes a trial version of SharePoint Server 2016 pre-installed. To continue using SharePoint Server 2016 after the trial expiration date, you must purchase a SharePoint Server 2016 license and client licenses from Microsoft. These charges are separate from the Azure subscription and the per-minute rate to run the virtual machine still applies.
  
### <a name="user-accounts"></a>使用者帳戶

所有 Microsoft 雲端供應項目的使用者帳戶都儲存在 Azure Active Directory (Azure AD) 租用戶中，其中包含使用者帳戶和群組。 Azure AD 租用戶可以使用 Azure AD Connect 這個 Windows 伺服器型服務，與您現有的 Active Directory 網域服務 (AD DS) 帳戶進行同步。 這稱為目錄同步處理。
  
圖 3 顯示組織的多個訂用帳戶使用同一個 Azure AD 租用戶，租用戶包含組織的帳戶。
  
**圖 3：組織的多個訂用帳戶使用相同 Azure AD 租用戶的範例。**

![多個訂用帳戶皆使用相同 Azure AD 租用戶的組織範例。](media/Subscriptions/Subscriptions-Fig3.png)
  
### <a name="tenants"></a>租用戶

For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services. For example, the Contoso Corporation chose the European region to host its Office 365, EMS, and Dynamics 365 tenants for the 15,000 workers in their Paris headquarters.
  
Azure PaaS services and virtual machine-based workloads hosted in Azure IaaS can have tenancy in any Azure datacenter across the world. You specify the Azure datacenter, known as the location, when you create the Azure PaaS app or service or element of an IaaS workload.
  
An Azure AD tenant is a specific instance of Azure AD containing accounts and groups. Paid or trial subscriptions of Office 365, Dynamics 365, or Intune/EMS include a free Azure AD tenant. This Azure AD tenant does not include other Azure services and is not the same as an Azure trial or paid subscription.
  
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
    
多個 Microsoft 雲端供應項目訂用帳戶可以使用作為共同身分識別提供者的相同 Azure AD 租用戶。 內含內部部署 AD DS 的同步處理帳戶的中央 Azure AD 租用戶，可為組織提供雲端型的身分識別即服務 (IDaaS)。 
  
**圖 4： 組織同步處理的內部部署帳戶和 IDaaS**

![組織的身分識別即服務 (IaaS) IDaaS。](media/Subscriptions/Subscriptions-Fig4.png)
  
Figure 4 shows how a common Azure AD tenant is used by Microsoft's SaaS cloud offerings, Azure PaaS apps, and virtual machines in Azure IaaS that use Azure AD Domain Services. Azure AD Connect synchronizes the on-premises AD DS forest with the Azure AD tenant.
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a>合併多個 Microsoft 雲端供應項目的訂用帳戶

下表說明如何以已有的一種雲端供應項目的一個訂用帳戶為本，合併多個 Microsoft 雲端供應項目 (表中的第一個直列)，以及如何為不同的雲端供應項目新增訂用帳戶 (表中的橫行)。
  
||**Office 365**|**Azure**|**Intune/EMS**|**Dynamics 365**|
|:-----|:-----|:-----|:-----|:-----|
|**Office 365** <br/> |NA  <br/> |您在 Azure 入口網站中為組織新增 Azure 訂用帳戶。  <br/> |您可以透過 Microsoft 365 系統管理中心為組織新增 Intune/EMS 訂閱。  <br/> |您可以透過 Microsoft 365 系統管理中心為組織新增 Dynamics 365 訂閱。  <br/> |
|**Azure** <br/> |您為組織新增 Office 365 訂用帳戶。  <br/> |NA  <br/> |您為組織新增 Intune/EMS 訂用帳戶。  <br/> |您為組織新增 Dynamics 365 訂用帳戶。  <br/> |
|**Intune/EMS** <br/> |您為組織新增 Office 365 訂用帳戶。  <br/> |您在 Azure 入口網站中為組織新增 Azure 訂用帳戶。  <br/> |NA  <br/> |您為組織新增 Dynamics 365 訂用帳戶。  <br/> |
|**Dynamics 365** <br/> |您為組織新增 Office 365 訂用帳戶。  <br/> |您在 Azure 入口網站中為組織新增 Azure 訂用帳戶。  <br/> |您為組織新增 Intune/EMS 訂用帳戶。  <br/> |NA  <br/> |
   
要將 Microsoft SaaS 服務的訂用帳戶新增到組織，簡單的做法是透過系統管理中心：
  
1. 使用您的全域系統管理員帳戶登入 Microsoft 365 系統管理中心 ([https://admin.microsoft.com](https://admin.microsoft.com))。
    
2. 在 **[管理中心]** 首頁的導覽窗格中，按一下 **[計費]**，然後按一下 **[購買服務]**。
    
3. 在 **[購買服務]** 頁面上，購買新的訂用帳戶。
    
系統管理中心會將組織和 Office 365 訂用帳戶的 Azure AD 租用戶，指派給 SaaS 雲端供應項目的新訂用帳戶。
  
使用與 Office 365 訂用帳戶相同的組織和 Azure AD 租用戶進行新增：
  
1. 使用 Office 365 全域管理員帳戶登入 Azure 入口網站 ([https://portal.azure.com](https://portal.azure.com))。
    
2. 在左側導覽窗格中，按一下 **[訂用帳戶]**，然後按一下 **[新增]**。
    
3. 在 **[新增訂用帳戶]** 頁面上，選取供應項目，並填寫付款資訊和合約。
    
如果您已另外購買 Azure 與 Office 365 訂閱，並想要從您的 Azure 訂用帳戶存取 Office 365 Azure AD 租用戶，請參閱[將現有的 Azure 訂用帳戶新增到您的 Azure Active Directory 租用戶](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory) 中的指示。
 
## <a name="see-also"></a>請參閱

[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)
  
[適用於 SharePoint、Exchange、商務用 Skype 和 Lync 的架構模型](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[混合式解決方案](hybrid-solutions.md)

## <a name="next-step"></a>下一步

[評估 Office 365 的網路連線能力](assessing-network-connectivity.md)
  
