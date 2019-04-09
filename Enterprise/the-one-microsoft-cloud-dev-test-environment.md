---
title: One Microsoft Cloud 開發/測試環境
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: a1370fe4-2fd6-4fea-ad1d-3555433d6d2e
description: 摘要：使用這項測試實驗室指南來建立開發/測試環境，其中包含所有的 Microsoft 雲端供應項目。
ms.openlocfilehash: b8ffd01c9d129d4537c82f0e1f74bd7c1be1388b
ms.sourcegitcommit: 201d3338d8bbc6da9389e62e2add8a17384fab4d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "31037947"
---
# <a name="the-one-microsoft-cloud-devtest-environment"></a>One Microsoft Cloud 開發/測試環境

 **摘要：** 使用這項測試實驗室指南來建立開發/測試環境，其中包含所有的 Microsoft 雲端服務。
  
依照本文所述的指示，您可以在 Microsoft Azure 基礎結構服務中建立模擬的內部網路，然後再新增 Microsoft Office 365、Microsoft Enterprise Mobility + Security (EMS)，與 Microsoft Dynamics 365 訂閱。結果是經簡化的組織在單一開發/測試環境中一次使用所有 Microsoft 雲端供應項目。 
  
![具有 Azure、Office 365、EMS 及 Dynamics 365 之 One Microsoft Cloud 開發/測試環境的階段 3 ](media/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
您可以使用所產生的組態來：
  
- 體驗在 Microsoft 雲端供應項目間的整合 (例如 Azure Active Directory (AD) 所提供的常見身分識別基礎結構)。
    
- 評估包含多個 Microsoft Cloud 供應項目的端對端案例。
    
- 建立示範、概念證明或使用多個 Microsoft Cloud 供應項目的開發/測試組態。
    
- 建置適用於專業開發的 Microsoft Cloud 技能。
    
## <a name="phase-1-create-a-simulated-intranet-and-add-office-365"></a>階段 1：建立模擬的內部網路，並新增 Office 365

遵循在 [ Office 365 開發/測試環境中的 DirSync ](dirsync-for-your-office-365-dev-test-environment.md) 中的指示。
  
圖 1 顯示您產生的組態，其中包括 Office 365 與在 Azure 基礎結構服務中執行模擬內部網路與來自內部部署 Active Directory Domain Services (AD DS) 樹系中的目錄同步處理。
  
**圖 1：含 Office 365 之 Azure 中的模擬內部網路**

![具有 DirSync 的 Office 365 開發/測試環境](media/be5b37b0-f832-4878-b153-436c31546e21.png)
  
> [!NOTE]
> Azure 試用版是 30 天。Office 365 企業版 E5 試用訂閱是 30 天，此可以輕鬆地延長額外 30 天的時間。針對永久開發/測試環境，建立新付費 Azure 訂閱並建立新付費的 Office 365 企業版 E5 訂閱，內含少量的授權。 
  
## <a name="phase-2-add-ems"></a>階段 2：新增 EMS

在這個階段中，您可以註冊 EMS 試用訂閱，並將它新增至與 Office 365 試用訂閱相同的組織。
  
1. 使用電腦上的瀏覽器或是從 CLIENT1，以全域系統管理員帳戶的認證，登入位於 [https://www.office.com](https://www.office.com) 的 Office 365 入口網站。
    
2. 按一下 [管理]**** 磚。
    
3. 在瀏覽器的 [Office 系統管理中心]**** 索引標籤上，按一下左導覽中的 [計費] > [購買服務]****。
    
4. 在 [購買服務]**** 頁面上，尋找 **Enterprise Mobility + Security E5** 項目。將滑鼠指標停留在上面，並且按一下 [開始免費試用]****。
    
5. 在 [確認訂單]**** 頁面上，按一下 [立即試用]****。
    
6. 在 [訂單收據]**** 頁面上，按一下 [繼續]****。
    
> [!NOTE]
> Enterprise Mobility + Security E5 試用訂閱為 90 天。針對永久開發/測試環境，建立具有少數授權的新付費訂閱。 
  
接下來，啟用適用於所有使用者帳戶的 Enterprise Mobility + Security E5 授權。
  
1. 在瀏覽器的 [Office 365 系統管理中心]**** 索引標籤上，按一下左導覽中的 [使用者] > [作用中使用者]****。
    
2. 按一下您的全域系統管理員帳戶，然後按一下 [產品授權]**** 的 [編輯]****。
    
3. 在 [產品授權]**** 窗格中，將 **Enterprise Mobility + Security E5** 的產品授權設為 [開啟]**，按一下 [儲存]，然後按兩次 [關閉]。
    
4. 針對您的所有其他帳戶 (User1、User 2、User 3、User 4 及 User 5) 執行步驟 2 和 3。
    
開發/測試環境現在擁有：
  
- 在 Azure 基礎結構服務中執行的模擬內部網路。
    
- Office 365 E5 Enterprise 和 EMS 試用訂閱會與您的使用者帳戶清單共用相同的組織和相同的 Azure AD 租用戶。
    
- 您的所有使用者帳戶都會啟用以使用 Office 365 E5 Enterprise 和 EMS。
    
圖 2 顯示產生的組態，其中會新增 EMS。
  
**圖 2：含 Office 365 和 EMS 之 Azure 中的模擬內部網路**

![具有 Azure、Office 365 及 EMS 之 One Microsoft Cloud 開發/測試環境的階段 2 ](media/fdb520fe-ebbd-4681-a80e-b60df52f07c5.png)
  
## <a name="phase-3-add-dynamics-365"></a>階段 3：新增 Dynamics 365

在這個階段中，您可以註冊 Dynamics 365 試用訂閱，並將它新增至與 Office 365 與 EMS 試用訂閱的相同組織。
  
1. 使用電腦上的瀏覽器或是從 CLIENT1，以全域系統管理員帳戶的認證，登入位於 [https://www.office.com](https://www.office.com) 的 Office 365 入口網站。
    
2. 按一下 [管理]**** 磚。
    
3. 在 [Microsoft 365 系統管理中心]**** 索引標籤上，按一下左導覽中的 [計費] > [購買服務]****。
    
4. 在 [購買服務]**** 頁面上，尋找 [Dynamics 365 方案 1 企業版]**** 項目。將滑鼠指標停留在上面，並且按一下 [開始免費試用] ****。
    
5. 在 [確認訂單]**** 頁面上，按一下 [立即試用]****。
    
6. 在 [訂單收據]**** 頁面上，按一下 [繼續]****。
    
> [!NOTE]
> Dynamics 365 方案 1 企業版試用訂閱是 30 天。您可以輕鬆地將試用訂閱延長額外 30 天的時間。針對永久開發/測試環境，建立內含少量授權的新付費訂閱。 
  
使用這些步驟，將 Dynamics 365 授權指派給全域系統管理員、使用者 2 和使用者 3 帳戶，並將他們設為系統管理員。
  
1. 在 [Microsoft 365 系統管理中心]**** 索引標籤上，按一下 [使用者] > [作用中的使用者]****。
    
2. 在作用中使用者清單中，按一下全域系統管理員帳戶，然後按一下 [產品授權]**** 的 [編輯] ****。
    
3. 在 [產品授權] **** 窗格中，將 [Dynamics 365 方案 1 企業版]**** 的產品授權設為 [開啟]****，按一下 [儲存]****，然後按兩次 [關閉]****。
    
4. 對使用者 2 和使用者 3 帳戶執行步驟 2 和 3。
    
5. 關閉 [Microsoft 365 系統管理中心]**** 索引標籤。
    
使用這些步驟，將使用者 2 和使用者 3 帳戶設定為 Dynamics 365 系統管理員。
  
1. 在瀏覽器的 [Office 系統管理中心]**** 索引標籤上，依序按一下 [系統管理中心]****、[Dynamics 365]****。
    
    您可能需要等待 Dynamics 365 完成佈建，Dynamics 365 才會顯示在功能表中。
    
2. 在 [Dynamics 365] 索引標籤上，按一下 [這些所有]****，然後按一下 [完成安裝]****。
    
    請等候安裝完成。
    
    安裝完成後，就會根據屬於試用訂閱的範例資料來顯示銷售活動儀表板。請花幾分鐘觀看**歡迎使用試用版**影片。觀看完畢請關閉影片視窗。
    
3. 在頂端的工具列上，按一下 [銷售]**** 旁的向下箭號，按一下 [設定]****，然後按一下 [安全性]****。
    
4. 在 [安全性]**** 頁面，按一下 [使用者] ****。
    
5. 在使用者清單中，按一下 [使用者 2]****。
    
6. 在工具列中，按一下 [管理角色]****。
    
7. 在 [管理角色]****，按一下 [系統管理員]****，然後按一下 [確定]****。
    
8. 在頂部的工具列上按一下 [安全性]****。
    
9. 對使用者 3 帳戶重複步驟 5 到 8。
    
10. 關閉 [使用者：User3]**** 索引標籤。
    
> [!NOTE]
> Office 365 全域系統管理員帳戶已自動指派 Dynamics 365 系統管理員角色。 
  
開發/測試環境現在擁有：
  
- 在 Azure 基礎結構服務中執行的模擬內部網路。
    
- Office 365 E5 Enterprise、EMS 和 Dynamics 365 試用訂閱會與您的使用者帳戶清單共用相同的組織和相同的 Azure AD 租用戶。
    
- 您的所有使用者帳戶都會啟用以使用 Office 365 E5 Enterprise 和 EMS。
    
- 您的全域企業系統管理員、使用者 2 和使用者 3 帳戶已啟用，可使用 Dynamics 365 且為 Dynamics 365 系統管理員。
    
圖 3 顯示產生的組態。
  
**圖 3：含 Office 365、EMS 和 Dynamics 365 之 Azure 中的模擬內部網路**

![具有 Azure、Office 365、EMS 及 Dynamics 365 之 One Microsoft Cloud 開發/測試環境的階段 3 ](media/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
## <a name="next-steps"></a>後續步驟

您現在可以使用 One Microsoft Cloud 開發/測試環境來進行實驗。以下是一些引導經驗的構想：
  
- [在適用於 Office 365 應用程式的 EMS 中設定行動應用程式管理 (MAM) 原則](https://technet.microsoft.com/library/mt764059.aspx)
    
- [在含 Dynamics 365 連絡人的 Office 365 整合中示範 Exchange Online](https://technet.microsoft.com/library/mt798313.aspx)
    
- [在 Azure 基礎結構服務建立模擬的跨部署網路來主控以伺服器為基礎的工作負載](https://technet.microsoft.com/library/mt745150.aspx)
    
## <a name="see-also"></a>另請參閱

[雲端採用測試實驗室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)
  
[混合式解決方案](hybrid-solutions.md)
  
[安全性解決方案](security-solutions.md)





