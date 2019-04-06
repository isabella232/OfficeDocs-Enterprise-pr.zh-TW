---
title: 適用於 Office 365 和 Dynamics 365 開發/測試環境的 Exchange Online 整合
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 499c5823-427a-4ba2-8fc1-9553bc2ff2d3
description: 摘要：使用此測試實驗室指南，在 Office 365 試用版訂閱中啟用適用於 Exchange Online 的 Dynamics 365 整合。
ms.openlocfilehash: 47153f9321284d0bb30f59645dfe56ab40cb7982
ms.sourcegitcommit: 201d3338d8bbc6da9389e62e2add8a17384fab4d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "31037997"
---
# <a name="exchange-online-integration-for-your-office-365-and-dynamics-365-devtest-environment"></a>適用於 Office 365 和 Dynamics 365 開發/測試環境的 Exchange Online 整合

 **摘要：** 使用此測試實驗室指南，在 Office 365 試用版訂閱中啟用適用於 Exchange Online 的 Dynamics 365 整合。
  
Microsoft Dynamics 365 的重要用途是將所有的客戶通訊儲存在同一個位置，以便有適當的權限任何人都可以查看所有的相關客戶記錄。例如，檢視與特定連絡人、帳戶、機會或案例相關聯的所有電子郵件。
  
若要在 Dynamics 365 中儲存電子郵件和其他訊息記錄，您必須將電子郵件系統與 Dynamics 365 進行同步。伺服器端同步處理就是電子郵件同步處理的選擇方法。
  
使用這項測試實驗室指南來設定及說明 Exchange Online 和 Outlook Online 用戶端可以如何利用 Dynamics 365 中儲存的資訊。 
  
## <a name="phase-1-build-out-the-office-365-and-dynamics-365-devtest-environment"></a>階段 1：建置 Office 365 和 Dynamics 365 開發/測試環境

請使用 [Office 365 和 Dynamics 365 開發/測試環境](office-365-and-dynamics-365-dev-test-environment.md)中的指示，建立 Office 365 和 Dynamics 365 開發/測試環境的輕量型或模擬企業版本。
  
> [!NOTE]
> 本文中的設定不需要模擬的企業版開發/測試環境，其中包含連線至網際網路的模擬內部網路和目錄同步處理的 Active Directory 網域服務 (AD DS) 樹系。 它提供了此選項，讓您可以在環境中，代表的典型組織體驗的 Office 365 和 Dynamics 365 
  
## <a name="phase-2-configure-and-demonstrate-dynamics-365-integration-in-exchange-online"></a>階段 2：在 Exchange Online 中設定及示範 Dynamics 365 整合

若要設定全域系統管理員的信箱將 Dynamics 365 與 Exchange Online 整合，請使用這些步驟：
  
1. 使用瀏覽器的私人工作階段移至[http://admin.microsoft.com](http://admin.microsoft.com)並使用您的 Office 365 全域系統管理員帳戶登入。
    
2. 在 [Microsoft Office Home]**** 頁面上，按一下 [郵件]**** 磚。
    
3. 在 [新**郵件**] 索引標籤瀏覽器中，按一下 [**新增**]，請注意的方塊中輸入訊息] 下的窗格的右下角的 「 我的範本所具有的圖示。
    
     ![不與 Dynamics 365 整合的全新空白電子郵件訊息。](media/879b54fd-a68f-4581-9f89-d5050df6f4de.png)
  
4. 按一下 [捨棄]****，並將 [郵件]**** 索引標籤保持開啟。
    
5. 按一下瀏覽器中的 [Microsoft Office Home]**** 索引標籤，然後按一下 [系統管理員]**** 磚。
    
6. 在 [Office 系統管理中心]**** 索引標籤的左側導覽窗格中，按一下 [系統管理中心 > Dynamics 365]****。
    
7. 在瀏覽器中新 [Dynamics 365]**** 索引標籤的 Dynamics 365 執行個體清單中，按一下 [開啟]****。
    
8. 在瀏覽器中新 [管理]**** 索引標籤的瀏覽列上，按一下 [設定]**** 旁的向下箭號，然後按一下 [系統]**** 下的 [電子郵件設定]****。
    
9.  在 [電子郵件設定]**** 頁面上，按一下 [電子郵件設定]****。
    
10. 在 [系統設定]**** 對話方塊的 [電子郵件]**** 索引標籤上，將 [約會、連絡人及工作]**** 變更為 [伺服器端同步處理]****，然後按一下 [確定]****。
    
11. 在 [電子郵件設定]**** 頁面上，按一下 [信箱]****。
    
12. 選取左側核取記號欄中的 Office 365 全域系統管理員名稱，按一下工具列中的 [套用預設的電子郵件設定]****，然後按一下 [確定]****。
    
13. 在工具列中按一下 [核准電子郵件]****，然後按一下 [確定]****。
    
14. 選取左側核取記號欄中的 Office 365 全域系統管理員名稱，按一下工具列中的 [測試及啟用信箱]**&amp;**，然後按一下 [確定]****。
    
15. 按一下 [開啟郵件]**** 索引標籤，並確認全域管理員接收到測試訊息。
    
16. 在瀏覽器中返回 [信箱 > 我的作用中信箱]**** 索引標籤，然後重新整理頁面。全域系統管理員帳戶名稱的 [內送電子郵件狀態]**** 與 [外寄電子郵件狀態]**** 欄應設定為 [成功]**** 。請注意，需花費 15 分鐘的時間才能完成這兩個測試。
    
使用下列步驟，在全域系統管理員的信箱中安裝 Dynamics 365 App for Outlook，並示範 Dynamics 365 的功能：
  
1. 在瀏覽器的 [信箱 > 我的作用中信箱]**** 索引標籤上，按一下 [設定]**** 旁的向下箭號，然後按一下 [系統]**** 下的 [Dynamics 365 App for Outlook]****。
    
2. 在 [開始使用 Microsoft Dynamics 365 App for Outlook]**** 頁面中，按一下全域系統管理員名稱，然後按一下 [將應用程式新增至 Outlook]****。[狀態]**** 欄會變更為 [擱置]****。
    
3. 重新整理頁面，直到狀態變更為 [已新增至 Outlook]**** 為止。請注意，需花費 15 分鐘的時間才能完成這項設定。
    
4. 按一下瀏覽器中的 [郵件]**** 索引標籤，然後將其關閉。
    
5. 按一下瀏覽器中的 [Microsoft Office Home]**** 索引標籤，然後按一下 [郵件]**** 磚。
    
6. 在新**郵件**] 索引標籤瀏覽器中，按一下 [**新增**]。 請注意現在輸入一個訊息方塊下方窗格的右下角的 Dynamics 365 有圖示。
    
     ![與 Dynamics 365 整合的全新空白電子郵件訊息，顯示新的圖示。](media/ecb822e1-45fe-4481-99a1-294317d1d2de.png)
  
7. 按一下 [Dynamics 365] 圖示。您應該會看到 [Dynamics 365]**** 窗格，可從這裡追蹤此電子郵件或存取範本、銷售資料或文章。
    
8. 在電子郵件訊息的 [收件者]**** 欄位中，輸入 **alex.y.wu@outlook.com**，然後按一下 [Dynamics 365]**** 窗格中的 [重試]****。您應該會在 [Dynamics 365]**** 窗格中看到包含 Alex Wu 相關資訊的 [收件者]**** 區段，這是銷售應用程式中的連絡人，隨試用版訂閱的範例資料所提供。
    
     ![儲存於 Dynamics 365 中銷售連絡人的 Dynamics 365 資訊窗格。](media/a010fa5f-3f1b-47d4-ab5e-d00d85a24a3f.png)
  
9. 按一下 [捨棄]****。

> [!TIP]
> 按一下[這裡](http://aka.ms/catlgstack)，可查看 One Microsoft Cloud 測試實驗室指南堆疊中文件的所有視覺對應。
    
## <a name="see-also"></a>請參閱

[Office 365 和 Dynamics 365 開發/測試環境](office-365-and-dynamics-365-dev-test-environment.md)
  
[雲端採用測試實驗室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基底組態開發/測試環境](base-configuration-dev-test-environment.md)
  
[Office 365 開發/測試環境](office-365-dev-test-environment.md)
  
[Office 365 開發/測試環境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)

[Dynamics 365 訂閱管理 (線上)](https://technet.microsoft.com/library/jj679903.aspx)
  
[管理 Dynamics 365](https://technet.microsoft.com/library/dn531101.aspx)


