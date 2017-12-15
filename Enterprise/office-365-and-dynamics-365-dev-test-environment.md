---
title: "Office 365 和 Dynamics 365 開發/測試環境"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- jan17entnews
- Strat_O365_Enterprise
- Ent_TLGs
ms.assetid: 098c1a1d-83a1-40eb-bbc9-47de7af8bb23
description: "摘要： 將 Dynamics 365 新增至 Office 365 開發人員/測試環境用於此測試實驗室指南。"
ms.openlocfilehash: 49648dd357d23eaee2d08d35252e18edf6a5d2ec
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="office-365-and-dynamics-365-devtest-environment"></a>Office 365 和 Dynamics 365 開發/測試環境

 **摘要：**將 Dynamics 365 新增至 Office 365 開發人員/測試環境中使用此測試實驗室指南。
  
使用本文中的指示，新增 [Dynamics 365 試用版訂閱至 Office 365 開發人員/測試環境中，相同的組織建立 Office 365 和 Dynamics 365 開發人員/測試環境。
  
您可以使用 Dynamics 365 試用版訂閱示範 Dynamics 365 的特性與功能。下列的解決方案所含 Dynamics 365 計劃 1，Enterprise Edition 試用版：
  
- [Microsoft Dynamics 365 的銷售量](https://www.microsoft.com/dynamics365/sales)。增加您銷售自動化及數位智慧協助您保持著重並聰明工作的銷售人員。
    
- [Microsoft Dynamics 365 客戶服務](https://www.microsoft.com/dynamics365/customer-service)。獲得忠誠，讓您代理程式的完整資訊及數位智慧需要提供一致的服務。
    
- [Microsoft Dynamics 365 欄位服務](https://www.microsoft.com/dynamics365/field-service)。最佳化您的排程、 equipping 工作團隊，並使用預測的工具來增加利潤主機服務通話。
    
- [Microsoft Dynamics 365 的 Project 服務自動化](https://www.microsoft.com/en-us/dynamics365/project-service-automation)。成功完成專案並建立與提高工作效率的員工和智慧型工具獲利關係。
    
您可以探索一或多個以上的 Dynamics 365 試用版訂閱。
  
![Microsoft 雲端中的測試實驗室指南](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> 按一下[此處](http://aka.ms/catlgstack)的視覺對應至一個 Microsoft Cloud 測試實驗室指南堆疊中所有的文章。
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>階段 1：建置輕量型或模擬的企業 Office 365 開發/測試環境

如果您只是要測試的基本需求的輕量型方式的 Office 365 和 Dynamics 365，請在階段 2 和 3 的[Office 365 開發人員/測試環境](office-365-dev-test-environment.md)中遵循的指示。
  
如果您想要測試的模擬企業的 Office 365 和 Dynamics 365，請遵循[DirSync Office 365 開發人員/測試環境](dirsync-for-your-office-365-dev-test-environment.md)中的指示。
  
> [!NOTE]
> 本文中的設定不需要模擬的 enterprise 開發人員/測試環境中，其中包含連線至網際網路模擬內部網路和 Windows Server AD 樹系目錄同步處理。它會提供這裡是做為選項，讓您可以試驗 Office 365 和 Dynamics 365 代表的典型組織的環境中。 
  
## <a name="phase-2-add-a-dynamics-365-trial-subscription"></a>階段 2： 新增 Dynamics 365 試用版訂閱

在此階段中，您註冊 Dynamics 365 試用版訂閱並將其新增至您的 Office 365 試用版訂閱相同的組織。
  
### <a name="sign-up-for-a-dynamics-365-trial-subscription"></a>註冊 Dynamics 365 試用版訂閱

1. 在 [您的桌上型電腦 （輕量型） 使用瀏覽器或從 CLIENT1 （模擬企業） 登入[https://portal.office.com](https://portal.office.com)全域管理員帳戶的認證與 Office 365 入口網站。
    
2. 按一下 [**系統**] 磚。
    
3. 在**Office 系統管理中心**] 索引標籤的 [在左導覽列中，按一下 [**帳務 > 購買服務**。
    
4. 在 [**購買服務**] 頁面上尋找**Dynamics 365 計劃 1 Enterprise Edition**項目。滑鼠指標停留並按一下 [**開始免費試用版**。
    
5. 在 [**確認您的訂單**] 頁面上按一下 [**立即試用**。
    
6. 在 [**順序回條**] 頁面上按一下 [**繼續**]。
    
> [!NOTE]
> Dynamics 365 計劃 1 Enterprise Edition 試用訂閱是 30 天。您可以輕鬆地擴充另一個 30 天的軌跡訂閱。在永久的開發人員測試環境中建立新付費少量的授權與訂閱。 
  
## <a name="phase-3-assign-dynamics-365-licenses-and-system-administrators"></a>階段 3： 指派 Dynamics 365 授權和系統管理員

在此階段中，您將 Dynamics 365 授權指派給全域管理員、 使用者 2 及 3 使用者帳戶，並使其系統管理員。
  
使用下列步驟來指派 Dynamics 365 授權。
  
1. 在 [ **Office 系統管理中心**] 索引標籤上按一下 [**使用者 > 作用中使用者**。
    
2. 在作用中使用者清單中，按一下您的全域管理員帳戶] 和 [**編輯****產品**授權。
    
3. 在**產品授權**] 窗格中，開啟**Dynamics 365 計劃 1 Enterprise Edition** **上**至產品授權、 按一下 [**儲存]**及 [**關閉**兩次。
    
4. 使用者 2 和 3 使用者帳戶執行步驟 2 和 3。
    
5. 關閉**Office 系統管理中心**] 索引標籤。
    
使用下列步驟來設定使用者 2 和 3 使用者帳戶為 Dynamics 365 系統管理員。
  
1. 從**Microsoft Office Home** ] 索引標籤上，按一下 [**管理**]。
    
2. 在**Office 系統管理中心**] 索引標籤的左方導覽，按一下 [**系統中心**，和 [ **Dynamics 365**。
    
    您可能需要等候 Dynamics 365 完成佈建之前 Dynamics 365 出現的功能表中。
    
3. 在 [Dynamics 365] 索引標籤上按一下 [**全部都**、] 和 [**完成安裝。**
    
    等候安裝程式完成。
    
    當安裝完成後時，它會顯示根據屬於軌跡訂閱資料範例銷售活動儀表板。需要一些時間來檢視**您的試用版歡迎使用**視訊。關閉 [視訊] 視窗時完成。
    
4. 在頂端工具列上，按一下 [**銷售**] 旁的向下箭號、 按一下 [**設定**] 及 [**安全性**。
    
5. 按一下 [**安全性**] 索引標籤的 [**使用者**]。
    
6. 在使用者清單中，按一下 [**使用者 2**。
    
7. 在 [工具] 列中，按一下 [**管理角色**。
    
8. 在**管理角色**、 按一下 [**系統管理員**，並再按一下 [**確定]**。
    
9. 在上方的 [工具] 列中按一下 [**安全性**]。
    
10. 使用者 3 帳戶重複步驟 5-8。
    
11. 關閉**使用者： User3** ] 索引標籤。
    
> [!NOTE]
> 您的 Office 365 全域管理員帳戶會自動指派 Dynamics 365 系統管理員角色。 
  
Office 365 和 Dynamics 365 開發人員/測試環境現在有：
  
- Office 365 E5 Enterprise 和 Dynamics 365 試用版訂閱共用相同的組織與相同的 Azure AD 租用戶與您的使用者帳戶的清單。
    
- 您的全域企業系統管理員、 使用者 2 和 3 使用者帳戶能夠使用 Office 365 E5 Enterprise 和 Dynamics 365 且 Dynamics 365 系統管理員。
    
## <a name="next-step"></a>下一步

設定及示範 [Office 365 與 Dynamics 365 共同運作方式與[Office 365 和 Dynamics 365 開發人員/測試環境的 Exchange Online 整合](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)的 Exchange Online 信箱。
  
## <a name="see-also"></a>See Also

[雲端採用測試實驗室指南 (Tlg)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基本組態開發/測試環境](base-configuration-dev-test-environment.md)
  
[Office 365 開發人員/測試環境](office-365-dev-test-environment.md)
  
[Office 365 開發人員/測試環境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)

[訂閱管理 Dynamics 365 （線上）](https://technet.microsoft.com/library/jj679903.aspx)
  
[管理 Dynamics 365](https://technet.microsoft.com/library/dn531101.aspx)


