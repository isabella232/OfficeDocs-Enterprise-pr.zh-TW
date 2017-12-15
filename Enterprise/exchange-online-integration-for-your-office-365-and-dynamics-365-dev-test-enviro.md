---
title: "Office 365 和 Dynamics 365 開發人員/測試環境的 Exchange Online 整合"
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
- Ent_O365_Hybrid
- Ent_O365_Top
ms.custom:
- apr17entnews
- DecEntMigration
- mar17entnews
- Ent_TLGs
ms.assetid: 499c5823-427a-4ba2-8fc1-9553bc2ff2d3
description: "摘要： 使用此測試實驗室指南啟用 Exchange Online 的 Office 365 試用版訂閱中的 Dynamics 365 整合。"
ms.openlocfilehash: 9cecd13f0ffc3c2822ac6c66a3bde9c9e6a3c798
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="exchange-online-integration-for-your-office-365-and-dynamics-365-devtest-environment"></a>Office 365 和 Dynamics 365 開發人員/測試環境的 Exchange Online 整合

 **摘要：**使用此測試實驗室指南，讓您的 Office 365 試用版訂閱中的 Dynamics 365 整合的 Exchange Online。
  
Microsoft Dynamics 365 價值使用，以儲存集中一處的所有客戶通訊，因此具備適當權限的任何人都可以看到所有相關的客戶記錄。例如，檢視與特定連絡人、 帳戶、 商機、 或案例相關聯的所有電子郵件。
  
若要儲存電子郵件及其他訊息記錄 Dynamics 365，您需要與 Dynamics 365 同步處理您的電子郵件系統。伺服器端同步處理是一種選擇電子郵件同步處理的方法。
  
使用此測試實驗室指南設定與示範 Exchange Online 與 Outlook Online 用戶端可以運用 Dynamics 365 中儲存的資訊。 
  
## <a name="phase-1-build-out-the-office-365-and-dynamics-365-devtest-environment"></a>階段 1： 建立 Office 365 和 Dynamics 365 開發人員/測試環境

使用[Office 365 和 Dynamics 365 開發人員/測試環境](office-365-and-dynamics-365-dev-test-environment.md)中的指示來建立 Office 365 和 Dynamics 365 開發人員/測試環境的任一輕量型或模擬的企業版。
  
> [!NOTE]
> 本文中的設定不需要模擬的 enterprise 開發人員/測試環境中，其中包含連線至網際網路模擬內部網路和 Windows Server Active Directory (AD) 樹系目錄同步處理。它會提供這裡是做為選項，讓您可以代表的典型組織的環境中與 Office 365 和 Dynamics 365 試驗 
  
## <a name="phase-2-configure-and-demonstrate-dynamics-365-integration-in-exchange-online"></a>階段 2： 設定與示範 Dynamics 365 整合在 Exchange Online

使用下列步驟來設定 Dynamics 365 和 Exchange Online 的整合全域系統管理員的信箱：
  
1. 使用的私用的工作階段的瀏覽器，前往[http://portal.office.com](http://portal.office.com)並使用您的 Office 365 全域管理員帳戶登入。
    
2. 按一下 [ **Microsoft Office Home** ] 索引標籤的 [**郵件**並排顯示]。
    
3. 在 [新**郵件**] 索引標籤在瀏覽器中按一下 [**新增**]，請注意的輸入訊息方塊下方窗格下方角落的 「 我的範本所包含的圖示。
    
     ![不與 Dynamics 365 整合的全新空白電子郵件訊息。](images/879b54fd-a68f-4581-9f89-d5050df6f4de.png)
  
4. 按一下 [**放棄**，[**郵件**] 索引標籤保持在開啟狀態。
    
5. [在瀏覽器中的 [ **Microsoft Office Home** ] 索引標籤和 [**系統管理**並排顯示。
    
6. 在 [ **Office 系統管理中心**] 索引標籤的左方導覽，按一下 [**系統中心 > Dynamics 365**。
    
7. 在瀏覽器上 Dynamics 365 執行個體的清單中新增的**Dynamics 365** ] 索引標籤上按一下 [**開啟**]。
    
8. 新的 [**管理**] 索引標籤中瀏覽器中的導覽列上，按一下 [**設定**] 旁的向下箭頭和 [**電子郵件設定下**系統**。**
    
9.  在 [**電子郵件設定**] 頁面上按一下 [**電子郵件設定**]。
    
10. 在 [**電子郵件**] 索引標籤上 [**系統設定**] 對話方塊中**伺服器端同步處理**，以變更**約會、 連絡人及工作**並再按一下 [**確定]**。
    
11. 按一下 [**電子郵件設定**] 頁面的 [**信箱**]。
    
12. 選取左邊的核取記號表示] 欄中的 Office 365 全域管理員名稱、 按一下 [工具] 列中的 [**套用預設的電子郵件設定**，然後按一下 [**確定]**。
    
13. 按一下 [工具] 列中的 [**核准電子郵件**並再按一下 [**確定]**。
    
14. 選取 [Office 365 全域管理員名稱左側的核取記號表示] 欄中，按一下 [**測試&amp;啟用信箱**工具中長條，並再按一下 [**確定]**。
    
15. 按一下 [開啟**郵件**] 索引標籤並確認 [全域管理員接收測試郵件。
    
16. 在瀏覽器中的 [**我作用中信箱的信箱**] 索引標籤會傳回與重新整理頁面。**內送電子郵件狀態**] 和 [**外寄電子郵件狀態**欄應設為**成功**的全域管理員帳戶名稱。請注意其可能需要 15 分鐘的時間才能完成這兩個測試。
    
使用下列步驟安裝 Dynamics 365 Outlook 的應用程式及示範 Dynamics 365 全域管理員的信箱內的功能：
  
1. 在瀏覽器中的 [**我作用中信箱的信箱**] 索引標籤上按一下 [**設定**] 旁的向下箭頭和 [ **Dynamics 365 Outlook 的應用程式**下**系統**。
    
2. 在**開始使用 Outlook 的 Microsoft Dynamics 365 應用程式**] 頁面上按一下 [全域管理員名稱] 中，和 [**新增至 Outlook 的應用程式**。[**狀態**] 欄變更為**擱置**。
    
3. 直到狀態變更為 [**已新增至 Outlook**重新整理頁面。請注意其可能需要 15 分鐘的時間才能完成此設定。
    
4. 按一下 [在瀏覽器中的 [**郵件**] 索引標籤，然後關閉它。
    
5. [在瀏覽器中的 [ **Microsoft Office Home** ] 索引標籤和 [**郵件**並排顯示。
    
6. 在 [新**郵件**] 索引標籤在瀏覽器中按一下 [**新增]**。注意到的現在輸入訊息方塊下方窗格下方角落的 Dynamics 365 包含圖示。
    
     ![與 Dynamics 365 整合的全新空白電子郵件訊息，顯示新的圖示。](images/ecb822e1-45fe-4481-99a1-294317d1d2de.png)
  
7. 按一下 [Dynamics 365 圖示。您應該會看到 [ **Dynamics 365** ] 窗格中，您可以從中追蹤此電子郵件或 access 範本、 銷售文獻或文章。
    
8. **以**欄位中的電子郵件訊息，輸入**alex.y.wu@outlook.com**，和 [**重試** **Dynamics 365**窗格中。您應該會看到的資訊**Dynamics 365**窗格中**的收件者**] 區段上 Alex Wu、 銷售應用程式的範例資料提供給您的試用版訂閱的連絡人。
    
     ![儲存於 Dynamics 365 中銷售連絡人的 Dynamics 365 資訊窗格。](images/a010fa5f-3f1b-47d4-ab5e-d00d85a24a3f.png)
  
9. 按一下 [**放棄**。

> [!TIP]
> 按一下[這裡](http://aka.ms/catlgstack)一個 Microsoft Cloud 測試實驗室指南堆疊中的文章的所有視覺地圖。
    
## <a name="see-also"></a>See Also

[Office 365 和 Dynamics 365 開發人員/測試環境](office-365-and-dynamics-365-dev-test-environment.md)
  
[雲端採用測試實驗室指南 (Tlg)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基本組態開發/測試環境](base-configuration-dev-test-environment.md)
  
[Office 365 開發人員/測試環境](office-365-dev-test-environment.md)
  
[Office 365 開發人員/測試環境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)

[訂閱管理 Dynamics 365 （線上）](https://technet.microsoft.com/library/jj679903.aspx)
  
[管理 Dynamics 365](https://technet.microsoft.com/library/dn531101.aspx)


