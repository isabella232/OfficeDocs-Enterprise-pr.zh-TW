---
title: "訂閱、 授權及使用者帳戶為 Contoso Corporation"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: ec3b08f0-288c-4ba3-b822-dbf6352fa761
description: "摘要： 了解與結構的 Contoso 的雲端訂閱、 授權、 使用者帳戶的承租人。"
ms.openlocfilehash: 0fdd72a697edb312be13c9794e543a81bf9a8e54
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2018
---
# <a name="subscriptions-licenses-and-user-accounts-for-the-contoso-corporation"></a>訂閱、 授權及使用者帳戶為 Contoso Corporation

 **摘要：**了解與結構的 Contoso 的雲端訂閱、 授權、 使用者帳戶的承租人。
  
若要提供用於所有雲端方案一致的身分識別和計費、 Microsoft 提供組織/訂閱/授權/使用者帳戶階層：
  
- 組織
    
    使用 Microsoft cloud 方案，通常是由公用 DNS 網域名稱，例如 contoso.com 識別商務實體。
    
- 訂閱
    
    對於 Microsoft saas 和雲端方案 （Office 365、 Intune/EMS 和 Dynamics 365）、 訂閱會為某項特定產品和使用者授權購買的組。Azure、 訂閱允許組織使用的雲端服務的帳單。
    
- 授權
    
    Microsoft saas 和雲端方案、 授權允許使用雲端服務的特定使用者帳戶。Azure、 軟體授權之內建到服務定價，但是在某些情況下需要購買額外軟體授權。
    
- 使用者帳戶
    
    使用者帳戶儲存在 Azure AD 租用戶和以進行同步處理在內部身分識別提供者的 Windows Server AD 例如。
    
## <a name="contosos-structure"></a>Contoso 的結構

Contoso 取決於組織其訂閱、 授權、 帳戶、 及租用戶的下列結構：
  
**圖 1： Contoso 的組織、 訂閱、 授權、 使用者帳戶及承租人**

![Contoso 的組織、訂用帳戶授權、使用者帳戶及租用戶](images/Contoso_Poster/Subscriptions.png)
  
圖 1 顯示如何 Contoso 組織包含多個訂閱便繫結至一般的 Azure AD 租用戶包含從 contoso.com Windows Server AD 樹系同步處理之使用者帳戶。
  
- **組織**其公用網域名成稱為 contoso.com 可識別的 Contoso Corporation。
    
  - **訂閱和授權**Contoso Corporation 會使用下列：
    
  - 使用 5000 授權 Office 365 企業版 E3 產品
    
  - 使用 200 授權 Office 365 企業版 E5 產品
    
  - 使用 5000 授權 EMS 產品
    
  - 使用 100 授權 Dynamics 365 產品
    
  - 多個 Azure 訂閱根據區域 （英文）
    
  - **使用者帳戶**常見的 Azure AD 租用戶包含使用者帳戶的清單及群組使用的 Contoso 的訂閱，除了開發/測試所有 Azure 訂閱。
    
為 Contoso 的承租人：
  
- Saas 和雲端方案、 租用戶是提供雲端服務伺服器設施區域性位置。Contoso 選擇來裝載其 Office 365、 EMS 及 Dynamics 365 租用戶的歐洲地區。 
    
- Azure PaaS 服務與應用程式及 IaaS IT 工作量可以在任何 Azure 資料中心內租用在全世界。Azure AD 租用戶是含有帳戶和群組的 Azure AD 的特定執行個體。
    
- 常見的 Azure AD 租用戶包含 Contoso Windows Server AD 樹系的同步處理的帳戶提供跨 Microsoft cloud 方案 IDaaS。
    
如需詳細資訊，請參閱[訂閱、 授權、 帳戶、 及 Microsoft cloud 方案的承租人](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md)。
  
## <a name="contosos-azure-subscriptions"></a>Contoso 的 Azure 訂閱

圖 2 顯示 Contoso 的 Azure 訂閱的階層式設計：
  
**圖 2： Azure 訂閱 Contoso 的結構**

![Contoso 的 Azure 訂用帳戶結構](images/Contoso_Poster/Subscriptions_Nested.png)
  
- Contoso 是在上方，根據與 Microsoft 其 Enterprise 合約。
    
- 有一組根據 Contoso 的 Windows Server AD 樹系的網域 Contoso Corporation 在全世界的不同區域對應的帳戶。
    
- 每個區域中，有一或多個區域的開發、 測試及生產部署需求為基礎的訂閱。
    
每個 Azure 訂閱可以與單一相關聯 Azure AD 租用戶包含驗證和授權 Azure 服務的使用者帳戶和群組。實際執行訂閱使用一般的 Contoso Azure AD 租用戶。
  
## <a name="see-also"></a>請參閱

[Microsoft Cloud 中的 Contoso](contoso-in-the-microsoft-cloud.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)

[Microsoft 的 Enterprise Cloud 藍圖：IT 決策者的資源](https://sway.com/FJ2xsyWtkJc2taRD)




