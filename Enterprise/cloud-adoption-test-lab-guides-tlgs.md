---
title: 使用雲端採用測試實驗室指南 (TLG) 測試 Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/23/2018
ms.audience: ITPro
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
description: 摘要：使用這些雲端採用測試實驗室指南 (TLG) 以設定 Office 365、Dynamics 365 和 Office Server 產品的展示版本、概念證明或開發/測試環境。
ms.openlocfilehash: 796d34294ef92702214df30ca5553759554996d3
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2018
ms.locfileid: "23041497"
---
# <a name="test-office-365-with-cloud-adoption-test-lab-guides-tlgs"></a>使用雲端採用測試實驗室指南 (TLG) 測試 Office 365

 **摘要：** 使用這些雲端採用測試實驗室指南 (TLG) 以設定 Office 365、Dynamics 365 和 Office Server 產品的展示版本、概念證明或開發/測試環境。
  
TLG 可協助您快速學習 Microsoft 各項產品。它們非常適合在決定是否適合您使用或將其推廣給使用者之前，用來評估技術或組態的情況。「我自己建置它且可以運作」的實際經驗有助您了解新產品或解決方案的部署需求，因此您可以更妥善地規劃在生產環境中進行裝載。
  
TLG 也會針對應用程式開發和測試建立具有代表性的環境，亦稱為開發/測試環境。
  
![Microsoft Cloud 中的測試實驗室指南](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
請在深入之前參閱這些額外資源：
  
- 檢視[使用雲端採用測試實驗室指南來體驗 Microsoft Cloud](https://mva.microsoft.com/en-US/training-courses/experience-the-microsoft-cloud-with-cloud-adoption-test-lab-guides-17960?l=LXNRdhSLE_1000115881 ) Microsoft Virtual Academy 工作階段 (只要 22 分鐘)。
    
- 按一下[這裡](http://aka.ms/catlgstack)，可查看 One Microsoft Cloud 測試實驗室指南堆疊中文件的所有視覺對應。
    
## <a name="office-365-devtest-environment"></a>Office 365 開發/測試環境

使用這些文章來建置您的 Office 365 開發/測試環境︰
  
- [基底組態開發/測試環境](base-configuration-dev-test-environment.md)
    
    建立在 Microsoft Azure 基礎結構服務中執行的簡化內部網路。如果您想要建置模擬的企業組態，這是選擇性的步驟。
    
- [Office 365 開發/測試環境](office-365-dev-test-environment.md)
    
    建立 Office 365 企業版 E5 試用訂閱，該訂閱可從您的電腦，或從在 Azure 基礎結構服務中執行的簡化內部網路來建立。
    
- [Office 365 開發/測試環境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)
    
    安裝和設定 Azure AD Connect 以進行目錄同步作業及密碼同步化。如果您想要建置模擬的企業組態，這是選擇性的步驟。
    
針對 Office 365 開發/測試環境，使用這些文章來示範 Office 365 的企業版功能︰
  
- [適用於您的 Office 365 開發/測試環境的多重要素驗證](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    使用傳送至您智慧型手機的簡訊為您的 Office 365 訂閱帳戶設定並測試次要驗證。
    
- [Office 365 開發人員/測試環境的同盟身分識別](federated-identity-for-your-office-365-dev-test-environment.md)
    
    以 Windows Server Active Directory 網域的帳戶設定並示範同盟驗證。
    
- [Office 365 開發人員/測試環境的雲端 App 安全性](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
    設定並示範 Office 365 雲端 App 安全性，它可讓您建立原則來監視並通知 Office 365 訂閱中的可疑活動。
    
- [適用於 Office 365 開發/測試環境的進階威脅防護](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    設定並示範進階威脅防護，這是 Exchange Online Protection (EOP) 的一個功能，可協助防止惡意軟體攻擊您的電子郵件。
    
- [適用於 Office 365 開發/測試環境的進階電子文件探索](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
    新增範例資料並示範進階電子文件探索，它可讓您快速地尋找和分析 Office 365 中儲存的資料，包括電子郵件和文件。
    
- [Office 365 開發/測試環境中的機密檔案保護](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
    示範如何使用 Office 365 資訊版權管理保護機密文件中的資料，即使資料不小心張貼在錯誤的文件資料夾中。
    
- [Office 365 開發/測試環境中的資料分類和標示](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
    示範 Azure 資訊保護 (AIP) 用戶端如何用來分類不同安全性等級的文件。
    
- [獨立的 SharePoint Online 小組網站開發/測試環境](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
    示範如何建立 SharePoint Online 小組網站，該網站針對高度機密的資源，獨立於組織的其他網站。
    
## <a name="the-microsoft-365-enterprise-test-environment"></a>Microsoft 365 企業版測試環境

使用[以下文章](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides)，建立 [Microsoft 365 企業版](https://docs.microsoft.com/microsoft-365-enterprise/)的測試環境。
 
    
## <a name="office-365-and-dynamics-365-devtest-environment"></a>Office 365 和 Dynamics 365 開發/測試環境

透過這些文章，新增 Dynamics 365 試用版訂閱，並測試 Office 365 和 Dynamics 365 整合式功能與案例︰
  
- [Office 365 和 Dynamics 365 開發/測試環境](office-365-and-dynamics-365-dev-test-environment.md)
    
    將 Dynamics 365 試用版訂閱以及 Dynamics 365 授權和權限新增至您的使用者帳戶。
    
- [適用於 Office 365 和 Dynamics 365 開發/測試環境的 Exchange Online 整合](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)
    
    設定然後示範 Office 365 與 Dynamics 365 如何在 Exchange Online 信箱中共同運作。
    
## <a name="the-one-microsoft-cloud-devtest-environment"></a>One Microsoft Cloud 開發/測試環境

建立開發/測試環境，其中包含所有 Microsoft 的雲端供應項目：Office 365、Azure、EMS 及 Dynamics 365。請參閱 [One Microsoft Cloud 開發/測試環境](the-one-microsoft-cloud-dev-test-environment.md)以取得逐步指示。
  
## <a name="simulated-cross-premises-devtest-environments"></a>模擬的跨單位部署開發/測試環境

透過這些文章，您可以建立一個跨單位部署開發/測試環境，它包含 Azure 虛擬網路和模擬的內部部署網路︰
  
- [Azure 中模擬的跨單位部署虛擬網路](simulated-cross-premises-virtual-network-in-azure.md)
    
    在混合雲端組態中，建立連線到 Azure 虛擬網路的模擬內部網路。
    
- [Azure 開發/測試環境中的內部網路 SharePoint Server 2016](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)
    
    在 Azure 虛擬網路中建立單一伺服器 SharePoint Server 2016 陣列，並從模擬的內部部署網路測試連線能力和管理。
    
## <a name="additional-cloud-based-devtest-environments"></a>其他雲端式開發/測試環境

以下是您可以在 Azure 基礎結構服務中建立的其他雲端式開發/測試環境︰
  
- [Azure 中的 SharePoint Server 2016 開發/測試環境](https://technet.microsoft.com/library/mt723354.aspx)
    
    在 Azure 基礎結構服務中建置單一伺服器 SharePoint Server 2016 伺服器陣列。
    
- [Azure 中的 Exchange 2016 開發/測試環境](https://technet.microsoft.com/library/mt733070%28v=exchg.160%29.aspx)
    
    在 Azure 基礎結構服務中建置單一的 Exchange 2016 伺服器。
    
- [Azure 中的 SharePoint Server 2013 開發/測試環境](http://technet.microsoft.com/library/165de4d5-8fe6-4fbb-a15b-39a8b0a0eb23.aspx)
    
    在 Azure 基礎結構服務中建置基本和高可用性的 SharePoint Server 2013 伺服器陣列。
    
## <a name="see-also"></a>另請參閱

[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)
  
[適用於 SharePoint、Exchange、商務用 Skype 和 Lync 的架構模型](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[混合式解決方案](hybrid-solutions.md)


