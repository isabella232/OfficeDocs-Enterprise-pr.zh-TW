---
title: Office 365 和 Dynamics 365 開發/測試環境
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Ent_TLGs
ms.assetid: 098c1a1d-83a1-40eb-bbc9-47de7af8bb23
description: 摘要：您可以使用這個測試實驗室指南將 Dynamics 365 新增到您的 Office 365 開發/測試環境。
ms.openlocfilehash: 195e5ab4fd96d1f238c96d47cc7406a45e0e02b1
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915208"
---
# <a name="office-365-and-dynamics-365-devtest-environment"></a>Office 365 和 Dynamics 365 開發/測試環境

 **摘要：** 您可以使用這個測試實驗室指南將 Dynamics 365 新增到您的 Office 365 開發/測試環境。
  
使用這篇文章中的指示，您可以將 Dynamics 365 試用版訂閱新增到與 Office 365 開發/測試環境相同的組織，建立 Office 365 和 Dynamics 365 開發/測試環境。

![Office 365 和 Dynamics 365 開發/測試環境](media/o365-dynamics365-dev-test.png)
  
  
您可以使用 Dynamics 365 試用訂閱來實作 Dynamics 365 的特色和功能。下列解決方案隨附於 Dynamics 365 方案 1 企業版試用：
  
- [Microsoft Dynamics 365 for Sales](https://www.microsoft.com/dynamics365/sales)。透過自動化和數位智慧，協助銷售人員保持專注並提高工作效率，藉此提升銷售量。
    
- [Microsoft Dynamics 365 for Customer Service](https://www.microsoft.com/dynamics365/customer-service)。讓代理商獲得提供完美服務所需的完整資訊和數位智慧，藉此贏得客戶忠誠度。
    
- [Microsoft Dynamics 365 for Field Service](https://www.microsoft.com/dynamics365/field-service)。將排程最佳化、為員工提供所需工具，以及使用預測工具來增加獲利，藉此打造完美的服務專線。
    
- [Microsoft Dynamics 365 for Project Service Automation](https://www.microsoft.com/zh-TW/dynamics365/project-service-automation)。為專案畫下成功的句點，並與高生產力的員工和智慧工具建立互利的關係。
    
您可以在 Dynamics 365 試用訂閱中探索上述一或多個項目。
  
![Microsoft Cloud 中的測試實驗室指南](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> 按一下[這裡](http://aka.ms/catlgstack)，可查看 One Microsoft Cloud 測試實驗室指南堆疊中文件的所有視覺對應。
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>階段 1：建置輕量型或模擬的企業 Office 365 開發/測試環境

如果您只想以具有最小需求的輕量型方式測試 Office 365 和 Dynamics 365，請遵循 [Office 365 開發/測試環境](office-365-dev-test-environment.md)的階段 2 和階段 3 中的指示。
  
如果您想要針對模擬的企業測試 Office 365 和 Dynamics 365，請遵循[Office 365 開發/測試環境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)中的指示。

![Office 365 開發/測試環境](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
> [!NOTE]
> 這篇文章中的組態不需要模擬的企業開發/測試環境，其中包括模擬的內部網路 (連線到網際網路) 和 Windows Server AD 樹系中的目錄同步處理。它在這裡提供作為選項，讓您可以在代表典型組織的環境中試驗 Office 365 和 Dynamics 365。 
  
## <a name="phase-2-add-a-dynamics-365-trial-subscription"></a>階段 2：新增 Dynamics 365 試用訂閱

在這個階段中，您可以註冊 Dynamics 365 試用訂閱，並將它新增到與 Office 365 試用訂閱的相同組織。
  
### <a name="sign-up-for-a-dynamics-365-trial-subscription"></a>註冊 Dynamics 365 試用訂閱

1. 使用電腦上的瀏覽器 (輕量型) 或是從 CLIENT1 (模擬企業)，以全域系統管理員帳戶的認證，登入位於 [https://portal.office.com](https://portal.office.com) 的 Office 365 入口網站。
    
2. 按一下 [管理]**** 磚。
    
3. 在 [Office 系統管理中心]**** 索引標籤上，按一下左導覽中的 [計費] > [購買服務]****。
    
4. 在 [購買服務]**** 頁面上，尋找 [Dynamics 365 方案 1 企業版]**** 項目。將滑鼠指標停留在上面，並且按一下 [開始免費試用] ****。
    
5. 在 [確認訂單]**** 頁面上，按一下 [立即試用]****。
    
6. 在 [訂單收據]**** 頁面上，按一下 [繼續]****。

![Office 365 和 Dynamics 365 開發/測試環境](media/o365-dynamics365-dev-test.png)
    
> [!NOTE]
> Dynamics 365 方案 1 企業版試用訂閱是 30 天。您可以輕鬆地將試用訂閱延長額外 30 天的時間。針對永久開發/測試環境，建立內含少量授權的新付費訂閱。 
  
## <a name="phase-3-assign-dynamics-365-licenses-and-system-administrators"></a>階段 3：指派 Dynamics 365 授權和系統管理員

在此階段中，您將 Dynamics 365 授權指派給全域系統管理員、使用者 2 和使用者 3 帳戶，並將他們設為系統管理員。
  
使用這些步驟來指派 Dynamics 365 授權。
  
1. 在 [Office 系統管理中心]**** 索引標籤上，按一下 [使用者] > [作用中的使用者]****。
    
2. 在作用中使用者清單中，按一下全域系統管理員帳戶，然後按一下 [產品授權]**** 的 [編輯] ****。
    
3. 在 [產品授權] **** 窗格中，將 [Dynamics 365 方案 1 企業版]**** 的產品授權設為 [開啟]****，按一下 [儲存]****，然後按兩次 [關閉]****。
    
4. 對使用者 2 和使用者 3 帳戶執行步驟 2 和 3。
    
5. 關閉 [Office 系統管理中心]**** 索引標籤。
    
使用這些步驟，將使用者 2 和使用者 3 帳戶設定為 Dynamics 365 系統管理員。
  
1. 從 [Microsoft Office 的首頁]**** 索引標籤中，按一下 [管理]****。
    
2. 在 [Office 系統管理中心]**** 索引標籤上，依序按一下 [系統管理中心]****、[Dynamics 365]****。
    
    您可能需要等待 Dynamics 365 完成佈建，Dynamics 365 才會顯示在功能表中。
    
3. 在 [Dynamics 365] 索引標籤上，按一下 [這些所有]****，然後按一下 [完成安裝]****。
    
    請等候安裝完成。
    
    安裝完成後，就會顯示根據屬於試用訂閱之範例資料的銷售活動儀表板。花幾分鐘來檢視**歡迎使用試用版**影片。完成時關閉 [影片] 視窗。
    
4. 在頂端的工具列上，按一下 [銷售]**** 旁的向下箭號，按一下 [設定]****，然後按一下 [安全性]****。
    
5. 在 [安全性]**** 頁面，按一下 [使用者] ****。
    
6. 在使用者清單中，按一下 [使用者 2]****。
    
7. 在工具列中，按一下 [管理角色]****。
    
8. 在 [管理角色]****，按一下 [系統管理員]****，然後按一下 [確定]****。
    
9. 在頂部的工具列上按一下 [安全性]****。
    
10. 對使用者 3 帳戶重複步驟 5 到 8。
    
11. 關閉 [使用者：User3]**** 索引標籤。
    
> [!NOTE]
> Office 365 全域系統管理員帳戶已自動指派 Dynamics 365 系統管理員角色。 
  
Office 365 和 Dynamics 365 開發/測試環境現在有：
  
- Office 365 E5 企業版和 Dynamics 365 試用訂閱會與您的使用者帳戶清單共用相同的組織和相同的 Azure AD 租用戶。
    
- 您的全域企業系統管理員、使用者 2 和使用者 3 帳戶已啟用，可使用 Office 365 E5 企業版和 Dynamics 365 且為 Dynamics 365 系統管理員。
    
## <a name="next-step"></a>下一步

透過 [Office 365 和 Dynamics 365 開發/測試環境的 Exchange Online 整合](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)，設定然後實作 Office 365 和 Dynamics 365 如何在 Exchange Online 信箱中共同運作。
  
## <a name="see-also"></a>另請參閱

[雲端採用測試實驗室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基底組態開發/測試環境](base-configuration-dev-test-environment.md)
  
[Office 365 開發/測試環境](office-365-dev-test-environment.md)
  
[Office 365 開發/測試環境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)

[Dynamics 365 訂閱管理 (線上)](https://technet.microsoft.com/library/jj679903.aspx)
  
[管理 Dynamics 365](https://technet.microsoft.com/library/dn531101.aspx)


