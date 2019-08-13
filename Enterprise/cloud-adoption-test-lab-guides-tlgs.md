---
title: 使用測試實驗室指南 (TLG) 測試 Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/12/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: 摘要：使用這些測試實驗室指南 (TLG) 以設定 Office 365 的展示版本、概念證明或開發/測試環境。
ms.openlocfilehash: 32675683846789f1e7be0e398e5b140d25d7ba80
ms.sourcegitcommit: d58cdc7b2296df12f7a05d14ba05ab224ffb3e0c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "36302735"
---
# <a name="test-office-365-with-test-lab-guides-tlgs"></a>使用測試實驗室指南 (TLG) 測試 Office 365

 **摘要：** 使用這些文章以設定 Office 365 的展示版本、概念證明或開發/測試環境。
  
TLG 可協助您快速學習 Microsoft 各項產品。它們非常適合在決定是否適合您，以及在開始設計、規劃和推出給使用者使用之前，用來評估技術或組態的情況。「我自己建置它且可以運作」的實際經驗有助您了解新產品或解決方案的部署需求，因此您可以更妥善地規劃在生產環境中進行裝載。
  
TLG 也會針對應用程式開發和測試建立具有代表性的環境，亦稱為開發/測試環境。
  
![Microsoft Cloud 中的測試實驗室指南](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
## <a name="office-365-devtest-environment"></a>Office 365 開發/測試環境

使用這些文章來建置您的 Office 365 開發/測試環境︰
  
- [基底組態開發/測試環境](base-configuration-dev-test-environment.md)
    
    建立在 Microsoft Azure 基礎結構服務中執行的簡化內部網路。如果您想要建置模擬的企業組態，這是選擇性的步驟。
    
- [Office 365 開發/測試環境](office-365-dev-test-environment.md)
    
    建立 Office 365 企業版 E5 試用訂閱，該訂閱可從您的電腦，或從在 Azure 基礎結構服務中執行的簡化內部網路來建立。
    
- [目錄同步處理](dirsync-for-your-office-365-dev-test-environment.md)
    
    安裝和設定 Azure AD Connect 以進行目錄同步作業及密碼雜湊同步化。如果您想要建置模擬的企業組態，這是選擇性的步驟。
    
針對 Office 365 開發/測試環境，使用這些文章來示範 Office 365 的企業版功能︰
  
- [多重要素驗證](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    使用傳送至您智慧型手機的簡訊為您的 Office 365 訂閱中的帳戶設定並測試次要驗證。
    
- [同盟識別身分](federated-identity-for-your-office-365-dev-test-environment.md)
    
    使用 Active Directory 網域服務 (AD DS) 網域的帳戶設定並示範同盟驗證。
    
- [進階威脅防護](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    設定並示範進階威脅防護，這是 Exchange Online Protection (EOP) 的一個功能，可協助防止惡意軟體攻擊您的電子郵件。

## <a name="simulated-cross-premises-devtest-environment"></a>模擬的跨單位部署開發/測試環境

在混合雲端組態中，建立連線到 Azure 虛擬網路的[模擬內部網路](simulated-cross-premises-virtual-network-in-azure.md)。
    
## <a name="sharepoint-server-2016-devtest-environment"></a>SharePoint Server 2016 開發/測試環境

在 Azure 基礎結構服務中建置[單一伺服器 SharePoint Server 2016 伺服器陣列](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-dev-test-environment-in-azure)。

## <a name="microsoft-365-enterprise-devtest-environment"></a>Microsoft 365 企業版開發/測試環境

為 [Microsoft 365 企業版](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides)建立開發/測試環境。  
    
## <a name="see-also"></a>另請參閱

[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)
  
[適用於 SharePoint、Exchange、商務用 Skype 和 Lync 的架構模型](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[混合式解決方案](hybrid-solutions.md)
