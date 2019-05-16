---
title: Azure PaaS 的混合式雲端案例
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 5f4f5d0d-4638-48e8-a517-bd804856b617
description: 摘要： 了解混合式架構與案例的 Microsoft 平台即服務 (PaaS)-以 Azure 中的雲端供應項目。
ms.openlocfilehash: fcc335d0e53463dea4e7ac73c3885b39734db38e
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067529"
---
# <a name="hybrid-cloud-scenarios-for-azure-paas"></a>Azure PaaS 的混合式雲端案例

 **摘要：** 了解混合式架構與案例 Microsoft 平台即服務 (PaaS)-以 Azure 中的雲端供應項目。
  
組合內部的資料或運算資源與新的或已轉換的應用程式可以善加利用的 Azure PaaS 中執行雲端效能、 可靠性和小數位數及為行動使用者提供較佳的支援。 
  
## <a name="azure-paas-hybrid-scenario-architecture"></a>Azure PaaS 混合案例結構

圖 1 顯示在 Azure 中的 Microsoft PaaS 型混合式案例的架構。
  
**圖 1: Microsoft PaaS 型混合式案例，在 Azure 中**

![Azure 中的 Microsoft PaaS 型混合式案例](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS.png)
  
每個圖層的架構：
  
- 應用程式和案例
    
    混合式 PaaS 應用程式會在 Azure 中執行，並使用內部 compute 或儲存資源。
    
- 身分識別
    
    包含目錄同步處理或同盟協力廠商身分識別提供者。
    
- 網路
    
    包含您現有的網際網路管道或與公用對等以 Azure PaaS 的 ExpressRoute 連線。 您必須包含 Azure PaaS 應用程式存取內部部署 compute 或存放裝置資源的方式。
    
- 內部部署
    
    身分識別與安全性基礎結構和企業營運 (LOB) 應用程式或資料庫伺服器、 Azure PaaS 應用程式可以安全地存取現有行所組成。
    
## <a name="azure-paas-hybrid-application"></a>Azure PaaS 混合應用程式

圖 2 顯示在 Azure 中執行混合式應用程式的設定。
  
**圖 2: Azure PaaS 型混合式應用程式**

![Azure PaaS 型混合式應用程式](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps.png)
  
圖 2 內部部署網路主控存放裝置或應用程式伺服器和 DMZ 包含 proxy 伺服器上。 它會保持連線至 Azure PaaS 服務透過網際網路或 ExpressRoute 連線。
  
組織可以進行計算或存放裝置資源可在 Azure PaaS 混合應用程式：
  
- 主控 DMZ 中的伺服器上的資源。
    
- 主控 DMZ 中的反向 proxy 伺服器，讓已驗證、 輸入、 HTTPS 型要求送至位於內部部署的資源。
    
Azure 應用程式可以使用認證：
  
- Azure AD，可向內部部署身分識別提供者，例如 Active Directory 網域服務 (AD DS) 同步處理。
    
- 協力廠商身分識別提供者。
    
### <a name="example-azure-paas-hybrid-application"></a>範例 Azure PaaS 混合應用程式

圖 3 顯示在 Azure 中執行範例混合式應用程式。
  
**圖 3: 範例 Azure PaaS 型混合式應用程式**

![Azure PaaS 型混合式應用程式的範例](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps-Ex.png)
  
圖 3 中，在內部部署網路主控 LOB 應用程式。 Azure PaaS 主控自訂的行動應用程式。 智慧型手機在網際網路上的存取 Azure，將資料要求傳送至內部部署 LOB 應用程式中的自訂行動應用程式。
  
這則範例 Azure PaaS 混合應用程式是自訂的行動應用程式上的員工提供最新的連絡人資訊。 端對端混合式案例所組成：
  
- 智慧型手機應用程式需要驗證，內部部署認證來執行。
    
- 自訂的行動裝置 app，要求從使用者的智慧型手機 app 查詢為基礎的特定員工的相關資訊的 Azure PaaS 中執行。
    
- 驗證自訂的行動應用程式，並將要求轉寄 DMZ 中的反向 proxy 伺服器。
    
- 連絡人的要求，使用者帳戶的權限受到服務 LOB 應用程式伺服器陣列。
    
因為已與 Azure AD 同步處理內部部署身分識別提供者，自訂的行動應用程式和 LOB 應用程式可以驗證提出要求的使用者帳戶名稱。
  
## <a name="see-also"></a>另請參閱

[Microsoft Hybrid Cloud for Enterprise Architects](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)

