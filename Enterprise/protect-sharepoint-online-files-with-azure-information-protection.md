---
title: "保護與 Azure 資訊保護的 SharePoint Online 檔案"
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
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: "摘要： 適用於 Azure 資訊保護保護高度機密的 SharePoint Online 小組網站中的檔案。"
ms.openlocfilehash: 5beba188cadc88c15ec75ed2adb4899d9b41b8ec
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a>保護與 Azure 資訊保護的 SharePoint Online 檔案

 **摘要：**適用於 Azure 資訊保護保護高度機密的 SharePoint Online 小組網站中的檔案。
  
使用本文中的步驟來設定 Azure 資訊保護提供加密和權限高度機密的 SharePoint Online 小組網站中的檔案。從網站下載時，即使與檔案一起出差加密和權限保護。如需高度機密的 SharePoint Online 小組網站的詳細資訊，請參閱[Secure SharePoint Online 網站及檔案](secure-sharepoint-online-sites-and-files.md)。
  
> [!NOTE]
> 當 Azure 資訊保護加密套用至檔案儲存在 Office 365 服務無法處理這些檔案的內容。共同撰寫 」、 「 eDiscovery 」、 「 搜尋 」、 「 Delve、 和 「 其他共同作業功能無法運作。資料外洩防護 (DLP) 原則僅可用於 （包括 Office 365 標籤） 的中繼資料，但不是 （例如檔案內的信用卡號碼） 這些檔案的內容。 
  
首先，使用中[與 Office 365 系統管理中心啟動 Azure RMS](https://docs.microsoft.com/information-protection/deploy-use/activate-office365)的指示為您的 Office 365 訂閱。
  
接下來，設定新範圍的原則與保護和高度機密 SharePoint Online 小組網站的權限的子標籤 Azure 資訊保護。
  
1. Office 365 入口網站與有安全性管理員或公司管理員角色的帳戶登入。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 在瀏覽器中的個別] 索引標籤移至 Azure 入口網站 ([https://portal.azure.com](https://portal.azure.com))。
    
3. 如果這是您要設定 Azure 資訊保護第一次，請參閱這些[指示](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time)。
    
4. 在 [清單] 窗格中，按一下 [**更多的服務**、 輸入**資訊**，和 [ **Azure 資訊保護**。
    
5. **Azure 資訊保護**blade、 上，按一下 [**範圍設定的原則 > + 新增原則**。
    
6. 輸入 [**原則名稱**] 及 [ **Description**中的描述的新原則的名稱。
    
7. 按一下 [**選取哪些使用者或群組取得此原則 > 使用者/群組**，然後選取 [網站成員存取的極高機密 SharePoint Online 小組網站的群組。 
    
8. 按一下 [**選取 > [確定]**。
    
9. **高度機密**標籤中，按一下省略符號 （...）] 和 [**新增子標籤**。
    
10. 輸入**名稱**與**描述**標籤的描述的子標籤名稱。
    
11. 在**設定文件及包含此標籤的電子郵件的權限**，請按一下 [**保護**]。
    
12. 在 [**保護**] 區段中，按一下 [ **Azure （雲端索引鍵）**。
    
13. 在**保護**blade，**保護設定**] 下按一下 [ **+ 新增權限**。
    
14. 在**新增權限**blade 中，**指定使用者與群組**] 下按一下 [ **+ 瀏覽目錄]**。
    
15. 在**AAD 使用者與群組**] 窗格中，選取您極高機密的 SharePoint Online 小組網站、 網站成員存取群組及 [**選取**。
    
16. 在**預設選擇權限**] 下方清除**列印**、**複製及擷取內容**以及**轉寄**] 核取方塊。
    
17. 按兩次 [**確定]** 。
    
18. 在**子標籤**blade 中，按一下 [**儲存**]。
    
19. 關閉新範圍的原則 blade。
    
20. 在**Azure 資訊保護-範圍的原則**blade 中，按一下 [**發佈**]。
    
這是您所產生的設定以便高度機密 SharePoint Online 小組網站。
  
![適用於隔離 SharePoint Online 小組網站的 Azure 資訊保護。](images/8cc92aa4-e7bc-4c2f-a4a4-3b034b21aebf.png)
  
您現在準備開始建立文件及保護其 Azure 資訊保護及新的標籤。
  
您必須[安裝 Azure 資訊保護用戶端](https://docs.microsoft.com/information-protection/rms-client/install-client-app)裝置或 Windows 電腦上。您可以使用指令碼及自動化安裝，或使用者可以手動安裝用戶端。請參閱下列資源：
  
- [Azure 資訊保護用戶端](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [安裝 Azure 資訊保護用戶端](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [下載] 頁面上的手動安裝](https://www.microsoft.com/download/details.aspx?id=53018)
    
安裝之後，您的使用者執行並再登入的 Office 應用程式 （例如 Microsoft Word) 以其 Office 365 帳戶。將新的**資訊保護**列可讓使用者選取新的標籤。請確定您的使用者了解 SharePoint Online 小組網站和其標籤使用，來保護其高度機密檔案。
  
> [!NOTE]
> 如果您有多個極高機密的 SharePoint Online 小組網站，您應該具有上述設定、 使用每個子標籤設為網站成員存取群組的權限子標籤建立多個 Azure 資訊保護範圍的原則特定的 SharePoint Online 小組網站。 
  
## <a name="see-also"></a>請參閱

[安全的 SharePoint Online 網站及檔案](secure-sharepoint-online-sites-and-files.md)
  
[安全的開發人員/測試環境中的 SharePoint Online 網站](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[Microsoft 安全性指導政治活動、 非營利機構，以及其他靈活的組織](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)




