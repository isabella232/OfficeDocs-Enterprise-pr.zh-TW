---
title: 保護與 Azure 資訊保護的 SharePoint Online 檔案
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
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: 摘要： 適用於 Azure 資訊保護保護高度機密的 SharePoint Online 小組網站中的檔案。
ms.openlocfilehash: 84bd1f48c7051f945e7b851f829421364de2a557
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a>保護與 Azure 資訊保護的 SharePoint Online 檔案

 **摘要：**適用於 Azure 資訊保護保護高度機密的 SharePoint Online 小組網站中的檔案。
  
使用本文中的步驟來設定 Azure 資訊保護提供加密和權限高度機密的 SharePoint Online 小組網站中的檔案。從網站下載時，即使與檔案一起出差加密和權限保護。如需高度機密的 SharePoint Online 小組網站的詳細資訊，請參閱[Secure SharePoint Online 網站及檔案](secure-sharepoint-online-sites-and-files.md)。
  
> [!NOTE]
> 將 Azure 資訊保護加密套用至儲存於 Office 365 中的檔案時，服務會無法處理這些檔案的內容。 共同撰寫、eDiscovery、搜尋、Delve 和其他共同作業功能無法運作。 此外，資料外洩防護 (DLP) 原則只可用於中繼資料 (包括 Office 365 標籤)，但無法用於這些檔案的內容 (例如檔案中的信用卡號碼)。 
  
首先，使用中[與 Office 365 系統管理中心啟動 Azure RMS](https://docs.microsoft.com/information-protection/deploy-use/activate-office365)的指示為您的 Office 365 訂閱。
  
接下來，設定新範圍的原則與保護和高度機密 SharePoint Online 小組網站的權限的子標籤 Azure 資訊保護。
  
1. Office 365 入口網站與有安全性管理員或公司管理員角色的帳戶登入。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 在瀏覽器中的個別] 索引標籤移至 Azure 入口網站 ([https://portal.azure.com](https://portal.azure.com))。
    
3. 如果這是您要設定 Azure 資訊保護第一次，請參閱這些[指示](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time)。
    
4. 在 [清單] 窗格中，按一下 [**更多的服務**、 輸入**資訊**，和 [ **Azure 資訊保護**。
    
5. **Azure 資訊保護**blade、 上，按一下 [**範圍設定的原則 > + 新增原則**。
    
6. 在 [原則名稱] 中鍵入新原則的名稱，並在 [描述] 中鍵入描述。
    
7. 按一下 [選取取得此原則的使用者或群組] > [使用者/群組]，然後選取極機密 SharePoint Online 小組網站的網站成員存取群組。 
    
8. 按一下 [選取] > [確定]。
    
9. 針對 [高度機密] 標籤，按一下省略符號 (...)，然後再按一下 [新增子標籤]。
    
10. 在 [名稱] 中鍵入子標籤的名稱，並在 [描述] 中鍵入標籤的描述。
    
11. 在 [為包含此標籤的文件與電子郵件設定權限] 中，按一下 [保護]。
    
12. 在 [保護] 區段中，按一下 [Azure (雲端金鑰)]。
    
13. 在 [保護] 刀鋒視窗中，按一下 [保護設定] 下的 [+ 新增權限]。
    
14. 在 [新增權限] 刀鋒視窗中，按一下 [指定使用者與群組] 下的 [+ 瀏覽目錄]。
    
15. 在**AAD 使用者與群組**] 窗格中，選取您極高機密的 SharePoint Online 小組網站、 網站成員存取群組及 [**選取**。
    
16. 在**預設選擇權限**] 下方清除**列印**、**複製及擷取內容**以及**轉寄**] 核取方塊。
    
17. 按兩次 [**確定]** 。
    
18. 在 [子標籤] 刀鋒視窗中，按一下 [儲存]。
    
19. 關閉新的限域原則刀鋒視窗。
    
20. 在**Azure 資訊保護-範圍的原則**blade 中，按一下 [**發佈**]。
    
這是您所產生的設定以便高度機密 SharePoint Online 小組網站。
  
![適用於隔離 SharePoint Online 小組網站的 Azure 資訊保護。](images/8cc92aa4-e7bc-4c2f-a4a4-3b034b21aebf.png)
  
現在您已可開始建立文件，並利用 Azure 資訊保護和新標籤進行保護。
  
您必須[安裝 Azure 資訊保護用戶端](https://docs.microsoft.com/information-protection/rms-client/install-client-app)裝置或 Windows 電腦上。您可以使用指令碼及自動化安裝，或使用者可以手動安裝用戶端。請參閱下列資源：
  
- [Azure 資訊保護的用戶端](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [安裝 Azure 資訊保護用戶端](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [手動安裝的下載頁面](https://www.microsoft.com/download/details.aspx?id=53018)
    
安裝之後，您的使用者執行並再登入的 Office 應用程式 （例如 Microsoft Word) 以其 Office 365 帳戶。將新的**資訊保護**列可讓使用者選取新的標籤。請確定您的使用者了解 SharePoint Online 小組網站和其標籤使用，來保護其高度機密檔案。
  
> [!NOTE]
> 如果您有多個極機密 SharePoint Online 小組網站，應利用上述設定來建立多個 Azure 資訊保護限域原則，並設定子標籤，再將每個子標籤的權限設為特定 SharePoint Online 小組網站的網站成員存取群組。 
  
## <a name="see-also"></a>請參閱

[安全的 SharePoint Online 網站及檔案](secure-sharepoint-online-sites-and-files.md)
  
[在開發/測試環境中保護 SharePoint Online 網站](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[適用於政治活動、非營利組織和其他彈性組織的 Microsoft 安全性指南](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)




