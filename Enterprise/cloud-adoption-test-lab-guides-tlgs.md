---
title: 使用雲端採用測試實驗室指南 (TLG) 測試 Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/09/2019
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
description: 摘要：使用這些雲端採用測試實驗室指南 (TLG) 以設定 Office 365 的展示版本、概念證明或開發/測試環境。
ms.openlocfilehash: a61716ae34d8dbe3f710696570c46cefd0f4aa4c
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068139"
---
# <a name="test-office-365-with-cloud-adoption-test-lab-guides-tlgs"></a>使用雲端採用測試實驗室指南 (TLG) 測試 Office 365

 **摘要：** 使用這些雲端採用測試實驗室指南 (TLG) 以設定 Office 365 的展示版本、概念證明或開發/測試環境。
  
TLG 可協助您快速學習 Microsoft 各項產品。它們非常適合在決定是否適合您，以及在開始設計、規劃和推出給使用者使用之前，用來評估技術或組態的情況。「我自己建置它且可以運作」的實際經驗有助您了解新產品或解決方案的部署需求，因此您可以更妥善地規劃在生產環境中進行裝載。
  
TLG 也會針對應用程式開發和測試建立具有代表性的環境，亦稱為開發/測試環境。
  
![Microsoft Cloud 中的測試實驗室指南](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
按一下[這裡](http://aka.ms/catlgstack)，可查看 Office 365 測試實驗室指南堆疊中文章的所有視覺對應。
    
## <a name="office-365-devtest-environment"></a>Office 365 開發/測試環境

使用這些文章來建置您的 Office 365 開發/測試環境︰
  
- [基底組態開發/測試環境](base-configuration-dev-test-environment.md)
    
    建立在 Microsoft Azure 基礎結構服務中執行的簡化內部網路。如果您想要建置模擬的企業組態，這是選擇性的步驟。
    
- [Office 365 開發/測試環境](office-365-dev-test-environment.md)
    
    建立 Office 365 企業版 E5 試用訂閱，該訂閱可從您的電腦，或從在 Azure 基礎結構服務中執行的簡化內部網路來建立。
    
- [Office 365 開發/測試環境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)
    
    安裝和設定 Azure AD Connect 以進行目錄同步作業及密碼雜湊同步化。如果您想要建置模擬的企業組態，這是選擇性的步驟。
    
針對 Office 365 開發/測試環境，使用這些文章來示範 Office 365 的企業版功能︰
  
- [適用於您的 Office 365 開發/測試環境的多重要素驗證](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    使用傳送至您智慧型手機的簡訊為您的 Office 365 訂閱帳戶設定並測試次要驗證。
    
- [Office 365 開發人員/測試環境的同盟身分識別](federated-identity-for-your-office-365-dev-test-environment.md)
    
    使用 Active Directory Domain Services (AD DS) 網域的帳戶設定並示範同盟驗證。
    
- [Office 365 開發人員/測試環境的雲端 App 安全性](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
    設定並示範 Office 365 雲端應用程式安全性，它可讓您建立原則來監視並通知 Office 365 訂閱中的可疑活動。
    
- [適用於 Office 365 開發/測試環境的進階威脅防護](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    設定並示範進階威脅防護，這是 Exchange Online Protection (EOP) 的一個功能，可協助防止惡意軟體攻擊您的電子郵件。
    
- [適用於 Office 365 開發/測試環境的進階電子文件探索](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
    新增範例資料並示範進階電子文件探索，它可讓您快速地尋找和分析 Office 365 中儲存的資料，包括電子郵件和文件。
    
- [Office 365 開發/測試環境中的機密檔案保護](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
    示範如何使用 Office 365 資訊版權管理保護機密文件中的資料，即使資料不小心張貼在錯誤的文件資料夾中。
    
- [Office 365 開發/測試環境中的資料分類和標示](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
    示範 Azure 資訊保護用戶端如何用來分類不同安全性等級的文件。
    
- [獨立的 SharePoint Online 小組網站開發/測試環境](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
    示範如何建立 SharePoint Online 小組網站，該網站針對高度機密的資源，獨立於組織的其他網站。
    

## <a name="simulated-cross-premises-devtest-environments"></a>模擬的跨單位部署開發/測試環境

透過這些文章，您可以建立一個跨單位部署開發/測試環境，它包含 Azure 虛擬網路和模擬的內部部署網路︰
  
- [Azure 中模擬的跨單位部署虛擬網路](simulated-cross-premises-virtual-network-in-azure.md)
    
    在混合雲端組態中，建立連線到 Azure 虛擬網路的模擬內部網路。
    
- [Azure 開發/測試環境中的內部網路 SharePoint Server 2016](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)
    
    在 Azure 虛擬網路中建立單一伺服器 SharePoint Server 2016 陣列，並從模擬的內部部署網路測試連線能力和管理。
    
## <a name="sharepoint-server-2016-devtest-environments"></a>SharePoint Server 2016 開發/測試環境

以下是您可以在 Azure 基礎結構服務中建立的 SharePoint Server 2016 開發/測試環境︰
  
- [Azure 中的 SharePoint Server 2016 開發/測試環境](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-dev-test-environment-in-azure)
    
    在 Azure 基礎結構服務中建置單一伺服器 SharePoint Server 2016 伺服器陣列。

- [Azure 開發/測試環境中的內部網路 SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment)
    
    在 Azure 基礎結構服務中建置單一伺服器 SharePoint Server 2016 伺服器陣列並從模擬的內部網路存取。


## <a name="the-microsoft-365-enterprise-devtest-environments"></a>Microsoft 365 企業版開發/測試環境

使用[以下文章](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides)，建立 [Microsoft 365 企業版](https://docs.microsoft.com/microsoft-365-enterprise/)的開發/測試環境。  
    
## <a name="see-also"></a>另請參閱

[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)
  
[適用於 SharePoint、Exchange、商務用 Skype 和 Lync 的架構模型](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[混合式解決方案](hybrid-solutions.md)
