---
title: "用於 Office 365 開發/測試環境的進階電子文件探索"
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
- TLG
- Ent_TLGs
ms.assetid: d4c49a6f-abfd-4d68-b353-259b4eefb033
description: "摘要： 設定與示範 Office 365 進階 eDiscovery 與 Office 365 開發人員/測試環境中的範例資料。"
ms.openlocfilehash: 35ebbe68027d37d2925728005235d3dde62c6248
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a>用於 Office 365 開發/測試環境的進階電子文件探索

 **摘要：**設定與示範 Office 365 進階 eDiscovery 與 Office 365 開發人員/測試環境中的範例資料。
  
Office 365 進階的 eDiscovery 可讓您快速尋找及分析跨 Office 365，包括電子郵件和文件中儲存資料的相關資訊。這可以儲存極大的時間量和費用，特別是在訴訟暫止的情況。如需詳細資訊，請參閱[Office 365 進階 eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)。
  
透過本文中的指示，您可以針對合約爭議建立小型資料集，並使用進階電子文件探索進行分析。
  
> [!TIP]
> 按一下[此處](http://aka.ms/catlgstack)的視覺對應至一個 Microsoft Cloud 測試實驗室指南堆疊中所有的文章。
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a>階段 1：建立 Office 365 開發/測試環境

如果您只想要測試進階的 eDiscovery 的基本需求的輕量型方式，請依照下列階段 2 和[Office 365 開發人員/測試環境](office-365-dev-test-environment.md)的階段 3 中的指示。
  
如果您想要測試進階的 eDiscovery 模擬 enterprise 中，請遵循[DirSync Office 365 開發人員/測試環境](dirsync-for-your-office-365-dev-test-environment.md)中的指示。
  
> [!NOTE]
> 測試進階的 eDiscovery 不需要模擬的企業環境中，其中包含連線至網際網路模擬內部網路和 Windows Server AD 樹系目錄同步處理。它會提供這裡是做為選項，讓您可以執行測試和實驗代表的典型組織的環境中。 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a>階段 2：建立進階電子文件探索的範例資料

在此程序中，您會建立稍後要在進階電子文件探索案例中分析的電子郵件訊息。
  
1. 開啟 Internet Explorer，並在[https://outlook.com](https://outlook.com)您在階段 2 的[Office 365 開發人員/測試環境](office-365-dev-test-environment.md)中建立的 Outlook 帳戶登入]。
    
  - 如果您使用輕量型開發/測試環境，請開啟 Internet Explorer 的私密工作階段，並從本機電腦登入。
    
  - 如果您使用模擬的 enterprise 開發人員/測試環境，使用 Azure 入口網站 ([https://portal.azure.com](https://portal.azure.com)) 連線至 CLIENT1 虛擬機器，並從 CLIENT1 登入。
    
2. 在 [ **Outlook 信箱**] 索引標籤上按一下 [**新增**]。
    
3. 在 [**至**] 輸入您的試用版訂閱 User6 帳戶的電子郵件地址 ( **user6 @。**<organization name> **。 onmicrosoft.com**)。
    
4. 主旨中，輸入**測試電子郵件 1**。
    
5. 本文中，輸入**Tailspin 合約草稿**]，然後按一下 [**傳送**。
    
6. 在 [ **Outlook 信箱**] 索引標籤上按一下 [**新增**]。
    
7. 在 [**至**] 輸入您的試用版訂閱 User6 帳戶的電子郵件地址。
    
8. 主旨中，輸入**測試電子郵件 2**。
    
9. 本文中，輸入**Tailspin lunch 會議**，然後按一下 [**傳送**。
    
10. 在 [ **Outlook 信箱**] 索引標籤上按一下 [**新增**]。
    
11. 在 [**至**] 輸入您的試用版訂閱 User6 帳戶的電子郵件地址。
    
12. 主旨中，輸入**測試電子郵件 3**。
    
13. 本文中，輸入**Tailspin 合約 disagreement**，，然後按一下 [**傳送**。
    
14. 按一下右上角中的 [使用者] 圖示] 和 [**登出**。
    
15. 開啟新的索引標籤並登入 Office 365 入口網站 ([https://portal.office.com](https://portal.office.com)) 帳戶名稱與您的試用版訂閱 User6 帳戶的密碼。
    
16. 按一下 [ **Office 365 入口網站**] 索引標籤的 [**郵件**]。
    
17. **郵件-User6-Outlook**索引標籤上，確認 User6 接收所有的三個電子郵件從 Outlook 電子郵件帳戶。
    
18. 切換回**Office 365 入口網站] 索引標籤**的 User6。
    
19. 按一下右上角中的 [使用者] 圖示] 和 [**登出。**
    
在此程序中，您會建立稍後要在進階電子文件探索案例中分析的兩份 Word 文件。
  
1. 在 [ **Office** ] 頁面上，按一下 [**登入，**登入您的全域管理員帳戶的認證。
    
2. 在 [新增] 索引標籤上存取實際執行 SharePoint 網站的 URL： **https://** <fictional organization name> **.sharepoint.com/sites/production**
    
3. 在**實際執行網站集合**] 索引標籤的 [**文件**上按一下 [**新增 > Word 文件**。
    
4. 在 [ **Word Online** ] 頁面上輸入**Tailspin 草稿合約**、 等到在標題中顯示**Saved** ，然後關閉**Word 線上**的 [頁面] 索引標籤。
    
5. 在**實際執行網站集合**] 索引標籤的 [**文件**上按一下 [**新增 > Word 文件**。
    
6. 在 [ **Word Online** ] 索引標籤上輸入**Tailspin 合約爭議備忘稿**、 等到在標題中顯示**Saved** ，然後關閉**Word Online** ] 索引標籤。
    
7. 在**實際執行網站集合**] 索引標籤中，您應該會看到**文件**及**文件 1**清單中的文件。
    
8. 關閉 [**實際執行網站集合**] 索引標籤。
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a>法律爭議的階段 3： 使用進階的 eDiscovery

不過，您組織與 Tailspin Toys 之間的合約爭議已達到法律巨集指令的點。在此程序，您可以建立和設定搜尋及分析電子郵件和文件包含文字"Tailspin 合約"進階的 eDiscovery 案例。
  
使用進階電子文件探索的程序如下：
  
- 在 [安全性] 中建立搜尋&amp;規範中心分析其結果，並再準備進階 ediscovery （英文） 的 [結果。
    
- 在進階電子文件探索中建立並設定案例，然後分析搜尋結果。
    
在此程序，您會建立安全性搜尋&amp;規範中心的"Tailspin 合約"看結果在與然後準備進階 eDiscovery 結果。
  
1. 從**Office 365 入口網站**] 索引標籤上，按一下 [**管理**]。
    
2. 在 [系統管理中心] 索引標籤的左方導覽，按一下 [**系統中心 > 規範**。
    
3. 在**安全性&amp;規範**] 索引標籤中按一下 [**權限**。
    
4. 在 [**權限**] 清單中，按兩下**組織管理**。
    
5. 在 [**角色群組**] 視窗的 [**成員**、 按一下 [加號。
    
6. 在 [**選取成員**] 視窗中，按兩下 [您的系統管理員帳戶的名稱然後再按一下 [**確定]**。
    
7. 在 [**角色群組**] 視窗中，按一下 [**儲存**]。
    
8. 在 [**權限**] 清單中，按兩下 [ **eDiscovery 管理員**。
    
9. 在 [**角色群組**] 視窗中，[ **eDiscovery 管理員**，按一下 [加號] 圖示。
    
10. 在 [**選取成員**] 視窗中，按兩下 [您的系統管理員帳戶的名稱然後再按一下 [**確定]**。
    
11. 在 [**角色群組**] 視窗中，按一下 [**儲存**]。
    
12. 在左導覽列中，按一下 [**搜尋&amp;調查 > 內容搜尋**。
    
13. 按一下加號圖示以新增搜尋。
    
14. 在 [**新的搜尋**] 視窗中，輸入**Tailspin 合約搜尋**的**名稱**。
    
15. 在**出您想我們要尋找？**、 按一下 [**搜尋寄件人，**選取 [ **Exchange**、 **SharePoint**及**公用資料夾**] 和 [**下一步。**
    
16. 在**您想什麼我們要尋找的？**且輸入**Tailspin 合約**，然後按一下 [**搜尋**]。
    
17. 在 [搜尋] 清單中按一下**Tailspin 合約搜尋**名稱。
    
18. 在 [ **Tailspin 合約搜尋**] 窗格中，按一下**結果****預覽搜尋結果**。您應該會看到列出在實際執行 SharePoint 網站 （**文件**和**文件 1**） 和 User6 來**測試電子郵件 1**和**測試電子郵件 3**電子郵件的兩個文件視窗。關閉視窗。
    
19. 在**內容搜尋**] 窗格中，[**具有進階 eDiscovery 的分析結果**，請按一下 [**預覽結果進行分析**。
    
20. 在 [**準備搜尋結果的 Tailspin 合約搜尋**] 視窗中，按一下 [**準備**並等待其完成。
    
在此程序中，您可以建立進階電子文件探索的新案件並分析 Tailspin 合約搜尋結果。
  
1. 在左導覽列中，按一下 [ **eDiscovery**下**搜尋&amp;調查**。
    
2. 在 [ **eDiscovery** ] 窗格中，按一下 [**移至 [進階 eDiscovery**。
    
3. 在 [**進階 eDiscovery** ] 索引標籤中按一下 [新增新案例 [加號] 圖示。
    
4. 在**新增案例**] 窗格中，輸入**Tailspin 合約爭議**在 [**名稱**]，然後按一下 [**確定]**。等待要建立的大小寫。
    
5. 按兩下 [ **Tailspin 合約爭議**案例清單中。
    
6. 在 [**容器**] 清單中按一下 [ **Tailspin 合約搜尋**] 容器中，和 [**程序**。等待處理完成。
    
7. 當**程序： 完成**會出現在視窗的底端，按一下 [**摘要的程序**在左側導覽中查看摘要。
    
8. 在上方導覽列中，按一下 [**分析**]。
    
9. 在 [**安裝程式**] 頁面上的 [**佈景主題**、 輸入**3**中**的佈景主題的最大數目**。
    
10. 按一下 [**分析**並等待完成分析。您應該會看到一系列的圓形圖與目標母體、 文件、 電子郵件及附件的分析。如需詳細資訊，請參閱[檢視分析結果](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e)。
    
您現在可以使用此環境來建立新的內容、新的搜尋和案例，並進一步在 Office 365 中試驗進階電子文件探索。
  
## <a name="see-also"></a>See Also

[雲端採用測試實驗室指南 (Tlg)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基本組態開發/測試環境](base-configuration-dev-test-environment.md)
  
[Office 365 開發人員/測試環境](office-365-dev-test-environment.md)
  
[Office 365 開發人員/測試環境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)
  
[Office 365 開發人員/測試環境的雲端應用程式安全性](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)

[Office 365 進階的 eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


