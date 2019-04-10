---
title: 適用於 Office 365 開發/測試環境的進階電子文件探索
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: d4c49a6f-abfd-4d68-b353-259b4eefb033
description: 摘要： 設定並示範 Office 365 進階 eDiscovery 與 Office 365 開發/測試環境中的範例資料。
ms.openlocfilehash: b1cf2714f79d38e5a3349b331cee0862cd6aac52
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741450"
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a>適用於 Office 365 開發/測試環境的進階電子文件探索

 **摘要：** 設定並示範 Office 365 進階 eDiscovery 與 Office 365 開發/測試環境中的範例資料。
  
Office 365 進階電子文件可讓您快速地尋找和分析跨 Office 365，包括電子郵件和文件中儲存資料的相關資訊。 這可以儲存龐大的時間量和費用，特別是在訴訟資料暫留情況。 如需詳細資訊，請參閱 [Office 365 進階電子搜索](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)。
  
透過本文中的指示，您可以建立一小群的虛構合約爭議資料及分析使用進階電子文件。
  
> [!TIP]
> 按一下[這裡](http://aka.ms/catlgstack)取得 Office 365 測試實驗室指南堆疊中所有文章的視覺對應。
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a>階段 1：建立 Office 365 開發/測試環境

如果您只想以具有最小需求的輕量型方式測試進階電子文件，請依照下列階段 2 和階段 3 中的[Office 365 開發/測試環境](office-365-dev-test-environment.md)中的指示。
  
如果您想要在模擬的企業中測試進階電子文件，請遵循[Office 365 開發/測試環境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)中的指示。
  
> [!NOTE]
> 測試進階電子文件不需要模擬的企業環境，其中包含連線至網際網路的模擬內部網路和目錄同步處理的 Active Directory 網域服務 (AD DS) 樹系。 它提供了此選項，讓您可以代表典型組織環境中執行測試與試驗。 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a>階段 2： 建立進階電子文件探索的範例資料

在此程序，您會建立電子郵件在進階電子文件探索案例中分析稍後將您的郵件。
  
1. 開啟 Internet Explorer 並登入在[https://outlook.com](https://outlook.com)您在[Office 365 開發/測試](office-365-dev-test-environment.md)環境的階段 2 中建立的 Outlook 帳戶。
    
  - 如果您使用輕量型開發/測試環境，請開啟 Internet Explorer 的私密工作階段，並從您本機電腦登入。
    
  - 如果您使用模擬的企業版開發/測試環境，使用 Azure 入口網站 ([https://portal.azure.com](https://portal.azure.com)) 來連接到 CLIENT1 虛擬機器，然後從 CLIENT1 登入。
    
2. 在 [ **Outlook 郵件**] 索引標籤上按一下 [**新增**]。
    
3. 在 [**至**] 輸入您試用版訂閱中 User6 帳戶的電子郵件地址 ( ** user6@。**<organization name> **。 onmicrosoft.com**)。
    
4. 主旨請輸入**測試電子郵件 1**。
    
5. 在本文中，輸入**Tailspin 合約草稿**]，然後按一下 [**傳送**。
    
6. 在 [ **Outlook 郵件**] 索引標籤上按一下 [**新增**]。
    
7. 在 [**至**] 輸入您試用版訂閱中 User6 帳戶的電子郵件地址。
    
8. 主旨請輸入**測試電子郵件 2**。
    
9. 在本文中，輸入**Tailspin 啟動會議**，，然後按一下 [**傳送**。
    
10. 在 [ **Outlook 郵件**] 索引標籤上按一下 [**新增**]。
    
11. 在 [**至**] 輸入您試用版訂閱中 User6 帳戶的電子郵件地址。
    
12. 主旨請輸入**測試電子郵件 3**。
    
13. 在本文中，輸入**Tailspin 合約爭議**，，然後按一下 [**傳送**。
    
14. 按一下右上角的使用者圖示，然後按一下 [**登出]**。
    
15. 開啟新的索引標籤，然後登入 Office 365 入口網站 ([https://www.office.com](https://www.office.com)) 帳戶名稱與試用版訂閱中 User6 帳戶的密碼。
    
16. **Office 365 入口網站**索引標籤上，按一下 [**郵件**]。
    
17. 在 [**郵件-User6-Outlook** ] 索引標籤上，檢查 User6 收到所有三封電子郵件從 Outlook 電子郵件帳戶。
    
18. User6 切換到**Office 365 入口網站索引標籤**。
    
19. 按一下右上角的使用者圖示，然後按一下**登出。**
    
在此程序，您建立兩個 Word 文件的就是您稍後會分析進階電子文件探索案例中。
  
1. 在 [ **Office** ] 頁面上，按一下 [**登入，** 登入您的全域系統管理員帳戶的認證。
    
2. 新索引標籤上，存取生產 SharePoint 網站的 URL: **https://** <fictional organization name> **.sharepoint.com/sites/production**
    
3. 在**實際執行網站集合**] 索引標籤上，[**文件**，按一下 [**新 > Word 文件**。
    
4. 在**Word Online** ] 頁面上，輸入**Tailspin 草稿合約**，等到標題中顯示**已儲存**，然後關閉**Word Online 中**的 [頁面] 索引標籤。
    
5. 在**實際執行網站集合**] 索引標籤上，[**文件**，按一下 [**新 > Word 文件**。
    
6. 在**Word Online** ] 索引標籤中，輸入**Tailspin 合約爭議附註**，等到標題中顯示**已儲存**，然後關閉 [ **Word Online** ] 索引標籤。
    
7. 在**實際執行網站集合**] 索引標籤中，您應該會看到**文件**和**文件 1**的文件清單中。
    
8. 關閉 [**生產環境網站集合**] 索引標籤。
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a>階段 3： 針對法律爭議使用進階的 eDiscovery

不幸的是，您的組織和 Tailspin Toys 之間的合約爭議已達到法律巨集指令的點。 在此程序，您可以建立及設定進階的 eDiscovery 案例來搜尋並分析電子郵件和文件包含文字 「 Tailspin 合約 」。
  
使用進階電子文件的程序如下：
  
- 建立 「 搜尋 」 安全性&amp;合規性中心，分析其結果，然後準備用於進階電子文件探索的結果。
    
- 建立和設定進階電子文件中的案例，分析搜尋結果。
    
在此程序，您可以建立安全性搜尋&amp;合規性管理中心的 「 Tailspin 合約 」，查看在結果中，然後準備用於進階電子文件探索的結果。
  
1. 從**Office 365 入口網站**] 索引標籤上，按一下 [**系統**]。
    
2. 在 [系統管理中心] 索引標籤的左方導覽，按一下 [**系統管理中心 > 合規性**]。
    
3. 在**安全性&amp;規範**索引標籤上，按一下 [**權限**。
    
4. 在 [**權限**] 清單中，按兩下 [**組織管理**]。
    
5. 在 [**角色群組**] 視窗中，[**成員**] 下方按一下加號。
    
6. 在 [**選取成員**] 視窗中，按兩下 [系統管理員帳戶的名稱，然後按一下 [**確定]**。
    
7. 在 [**角色群組**] 視窗中，按一下 [**儲存**]。
    
8. 在 [**權限**] 清單中，按兩下 [ **eDiscovery 管理員**]。
    
9. 在**角色群組**] 視窗中，[ **eDiscovery 系統管理員**]，按一下 [加號] 圖示。
    
10. 在 [**選取成員**] 視窗中，按兩下 [系統管理員帳戶的名稱，然後按一下 [**確定]**。
    
11. 在 [**角色群組**] 視窗中，按一下 [**儲存**]。
    
12. 在左側導覽中，按一下 [**搜尋&amp;調查 > 內容搜尋**。
    
13. 按一下加號圖示以新增搜尋。
    
14. 在 [**新搜尋**] 視窗中，輸入**Tailspin 合約搜尋**的**名稱**。
    
15. 在 [**您希望在哪裡我們在哪裡？**，按一下 [**搜尋各處，** 選取 [ **Exchange**、 **SharePoint**和**公用資料夾**]，然後按一下**下一步。**
    
16. 在 [**什麼您希望我們要尋找的？**，輸入**Tailspin 合約**，然後按一下 [**搜尋**]。
    
17. 在 [搜尋] 清單中按一下 [ **Tailspin 合約搜尋**名稱。
    
18. 在 [ **Tailspin 合約搜尋**] 窗格中，按一下 [**預覽搜尋結果****的結果**下。 您應該會看到列出在實際執行 SharePoint 網站 （**文件**和**文件 1**）] 和 [User6**測試電子郵件 1**和**測試電子郵件 3**電子郵件的兩個文件視窗。 關閉視窗。
    
19. 在 [**內容搜尋**] 窗格中，[**進階電子文件探索分析結果**，請按一下 [**預覽結果進行分析**。
    
20. 在 [**準備搜尋結果 Tailspin 合約搜尋**] 視窗中，按一下 [**準備**並等待其完成。
    
在此程序，您可以建立進階電子文件的新案件並分析 Tailspin 合約搜尋結果。
  
1. 在左導覽中，按一下 [ **eDiscovery**下**搜尋&amp;調查**。
    
2. 在 [ **eDiscovery** ] 窗格中，按一下 [**移至進階電子文件**。
    
3. 在 [**進階電子文件探索**] 索引標籤中，按一下加號圖示以新增案例。
    
4. 在**新增案例**] 窗格中，在 [**名稱**] 中，輸入**Tailspin 合約爭議**，然後按一下 **[確定]**。 等待要建立的案例。
    
5. 連按兩下清單中的**Tailspin 合約爭議**案例。
    
6. 在 [**容器**] 清單中，按一下 [ **Tailspin 合約搜尋**] 容器中，，，然後按一下 [**程序**。 等待完成處理。
    
7. 當**程序： 完成**會出現在視窗的底部，按一下 [**程序摘要**在左側導覽中查看摘要。
    
8. 在上方導覽列中，按一下 [**分析**]。
    
9. 在**安裝程式**] 頁面的 [**佈景主題**]，輸入**3**中**的佈景主題的最大數目**。
    
10. 按一下 [**分析]** 並等候完成分析。 您應該會看到一系列的帶有子橫條圖具有目標母體、 文件、 電子郵件，以及附件的分析。 如需詳細資訊，請參閱 <<c0>檢視分析結果。
    
您現在可以使用此環境建立新的內容、 新的搜尋情況下，並進一步與 Office 365 進階電子文件。
  
## <a name="see-also"></a>另請參閱

[雲端採用測試實驗室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基底組態開發/測試環境](base-configuration-dev-test-environment.md)
  
[Office 365 開發/測試環境](office-365-dev-test-environment.md)
  
[Office 365 開發/測試環境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)
  
[Office 365 開發人員/測試環境的雲端 App 安全性](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)

[Office 365 進階電子文件探索](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


