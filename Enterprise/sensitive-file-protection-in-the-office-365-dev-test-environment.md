---
title: Office 365 開發/測試環境中的敏感檔案保護
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/01/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: 摘要： 設定並示範如何 Office 365 資訊版權管理保護機密檔案，即使公佈到錯誤的 SharePoint Online 網站集合。
ms.openlocfilehash: 3fa771d63ca30fb53ac2c77466546cf3a2098deb
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031568"
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a>Office 365 開發/測試環境中的敏感檔案保護

 **摘要：** 設定並示範如何 Office 365 資訊版權管理保護機密檔案，即使公佈到錯誤的 SharePoint Online 網站集合。
  
資訊版權管理 (IRM) 設定 Office 365 是一組的功能來保護 SharePoint Online 文件庫和清單從下載的文件。 下載的檔案加密儲存，包含開啟的複本，並列印反映 SharePoint Online 的文件庫中所儲存的權限。
  
透過本文中的指示，您可以啟用並測試 Office 365 中的 IRM，包含可能在您的 Office 365 試用版訂閱中的敏感資訊的檔案。
  
> [!TIP]
> 按一下[這裡](https://aka.ms/catlgstack)，可查看 Office 365 測試實驗室指南堆疊中文章的所有視覺對應。
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>階段 1： 建置 Office 365 開發/測試環境

如果您只想以具有最小需求的輕量型方式測試敏感性檔案保護，請遵循指示，以在階段 2 和 3 的[Office 365 開發/測試環境](office-365-dev-test-environment.md)中。
  
如果您想要在模擬的企業中測試敏感性檔案保護，請遵循[Office 365 開發/測試環境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)中的指示。
  
> [!NOTE]
> 測試敏感性檔案保護不需要模擬的企業版開發/測試環境，其中包含連線至網際網路的模擬內部網路和目錄同步處理 Active Directory 網域服務 (AD DS) 樹系中。 它提供了此選項，讓您可以測試敏感性檔案保護與代表典型組織的環境中實驗。 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a>階段 2： 展示如何可以遺漏文件中的權限受保護的網站

在這個階段，您會示範某人可以用來從權限保護的網站下載文件，並再將其上傳至網站，具有廣泛開放的權限。
  
首先，您會新增三個新的使用者帳戶代表主管和對其指派 Office 365 E5 授權。
  
使用[連線到 Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx)中的指示，安裝 PowerShell 模組 （如果需要），並連線至您從新的 Office 365 訂閱：
  
- 您的電腦 (適用於輕量型 Office 365 開發/測試環境)。
    
- CLIENT1 虛擬機器 (適用於模擬的企業 Office 365 開發/測試環境)。
    
在 [ **Windows PowerShell 認證要求**] 對話方塊中，輸入 Office 365 全域系統管理員名稱 (範例： jdoe@contosotoycompany.onmicrosoft.com) 和 Office 365 試用版訂閱的密碼。
  
填入您的組織名稱 (範例： contosotoycompany) 和兩個字元國家/地區適用於您位置中，程式碼，然後在 Windows Azure Active Directory 模組的 Windows PowerShell 提示字元執行下列命令：
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

從**New-msoluser**命令的顯示畫面，請注意 CEO 帳戶產生的密碼並且將密碼記錄在安全的位置。
  
從適用於 Windows PowerShell 的 Windows Azure Active Directory 模組提示字元中執行下列命令︰
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

從**New-msoluser**命令的顯示畫面，請注意 CFO 帳戶產生的密碼並且將密碼記錄在安全的位置。
  
從適用於 Windows PowerShell 的 Windows Azure Active Directory 模組提示字元中執行下列命令︰
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

從**New-msoluser**命令的顯示畫面，請注意 COO 帳戶產生的密碼並且將密碼記錄在安全的位置。
  
接下來，您建立私人的主管群組，並將新的高階主管帳戶新增至它。
  
1. 在瀏覽器中，移至 Office 入口網站，網址[https://admin.microsoft.com](https://admin.microsoft.com)並登入 Office 365 試用訂閱以全域管理員帳戶。
    
  - 如果您使用輕量型 Office 365 開發/測試環境，開啟 Internet Explorer 或您的瀏覽器的私人工作階段，並從您本機電腦登入。
    
  - 如果您使用模擬的企業 Office 365 開發/測試環境，使用 Azure 入口網站連線至 CLIENT1 虛擬機器，然後從 CLIENT1 登入。
    
2. 在 [ **Microsoft Office 的首頁**] 索引標籤中，按一下 [**系統 > 群組 > 群組**，然後按一下 [**新增群組**。
    
3. 在**加入群組**]，選取**Office 365 群組**的群組類型、 輸入**主管**[**名稱**] 及 [**群組識別碼**，選取 [**私用****的隱私權**、，然後按一下 [**選取擁有者**。
    
4. 在清單中，按一下 [您的全域系統管理員帳戶名稱。
    
5. Click **Add**, and then click **Close**.
    
6. 在 [群組] 清單中，按一下 [**主管**]。
    
7. 按一下 [**編輯成員**]。
    
8. 按一下 [新增成員]****。 在 [成員] 清單中，選取下列使用者帳戶：
    
  - 執行長
    
  - 主要的財務長
    
  - 首席作業長
    
9. 按一下 [儲存]****，然後按一下 [關閉]****。
    
10. 關閉 [ **Office 系統管理中心**] 索引標籤。
    
接下來，建立主管網站集合，並允許只對其進行存取的主管群組的成員。
  
1. 在**Microsoft Office 的首頁**] 索引標籤上，按一下 [**管理**] 磚。
    
2. 在 [ **Office 系統管理中心**] 索引標籤中，按一下 [**系統管理中心 > SharePoint**。
    
3. 在**SharePoint 系統管理中心**] 索引標籤上，按一下 [**新 > 私用網站集合**。
    
4. 在 [新網站集合] 窗格中，**標題**，主管在 [URL] 方塊中輸入**高階主管**指定的全域管理員帳戶名稱在**系統管理員**，，然後按一下 [**確定]**。
    
5. 請稍候，直到已建立新的網站集合。 完成時，複製新主管網站集合的 URL，並將它貼到您的瀏覽器的新索引標籤。
    
6. 在右上角的**主管**網站集合中，按一下 [設定] 圖示，然後按一下**與共用]**。
    
7. 在 [**共用 '高階主管]**，按一下 [**進階**]。
    
8. 在 SharePoint 群組的清單中，按一下 [**高階主管成員**。
    
9. 在 [人員與群組]**** 頁面上，按一下 [新增]****。
    
10. 在 [**共用 '高階主管]**，輸入**高階主管**，按一下 [**主管**] 群組中，，然後按一下**共用**。
    
11. 關閉 [**人員與群組**] 索引標籤。
    
接下來，您允許所有人存取業務部網站集合。
  
1. 從**SharePoint 系統管理中心**] 索引標籤上，複製業務部網站集合的 URL，並將它貼到您的瀏覽器的新索引標籤..
    
2. 在右上方，按一下 [設定] 圖示，然後按一下**與共用]**。
    
3. 在 [**共用 '業務部網站集合]**，按一下 [**進階**]。
    
4. 在 SharePoint 群組的清單中，按一下 [**銷售網站集合的成員**。
    
5. 在 [人員與群組]**** 頁面上，按一下 [新增]****。
    
6. 在**共用 '業務部網站集合]**，輸入**Everyone**、 按一下 [**外部使用者以外的所有人**，，然後按一下 [**共用**。
    
7. 關閉 [**銷售網站集合**和**SharePoint**索引標籤。
    
接下來，您使用高階主管的帳戶登入和主管網站集合中建立文件。
  
1. 在 [ **Microsoft Office 的首頁**] 索引標籤中，按一下右上角的使用者圖示，然後按一下 [**登出]**。
    
2. 請移至 [https://admin.microsoft.com](https://admin.microsoft.com)。
    
3. 在**Office 365 登入**] 頁面上，按一下 [**使用另一個帳戶**。
    
4. 輸入**CEO**帳戶名稱和密碼，然後再按一下 [**登入**。
    
5. 在瀏覽器的新索引標籤上，輸入 [高階主管的網站集合的 URL ( **https://**\<組織名稱>**.sharepoint.com/sites/executives**)。
    
6. 按一下 [**文件**，按一下 [**新增]** ，然後按一下 [ **Word 文件**。
    
7. 按一下標題列中，輸入**SensitiveData BeforeIRM**。
    
8. 按一下 [文件內文中並輸入**從最新協調會議的分鐘**，，然後按一下 [**主管**。
    
     您應該會看到**SensitiveData BeforeIRM.docx** **Documents**資料夾中。
    
接下來，您下載 SensitiveData BeforeIRM.docx 文件的本機複本，並再不小心張貼至業務部網站集合。
  
1. 在您的本機電腦上建立新的資料夾 (例如 c:\\Tlg\\SensitiveDataTestFiles)。
    
2. 在瀏覽器的 [**文件**] 索引標籤中，選取**SensitiveData BeforeIRM.docx**文件，請按一下省略符號，和 [**下載**。
    
3. **SensitiveData BeforeIRM.docx**文件儲存在步驟 1 中建立的資料夾中。
    
4. 在瀏覽器的新索引標籤上，輸入 [業務部網站集合的 URL ( **https://**\<組織名稱>**.sharepoint.com/sites/sales**)。
    
5. 按一下 [**銷售網站集合**的**文件**資料夾。
    
6. 按一下 [**上傳**，並再指定在步驟 1 所建立的資料夾中的 [ **SensitiveData BeforeIRM.docx**文件，然後按一下 [**確定]**。
    
7. 確認**SensitiveData BeforeIRM.docx**文件中的**文件**資料夾。
    
8. 關閉 [**銷售**及**SharePoint**索引標籤。
    
接下來，您 User5 身分，登入，並嘗試開啟 SensitiveData BeforeIRM.docx 該文件業務部網站集合。
  
1. 在 [ **Microsoft Office 的首頁**] 索引標籤中，按一下右上角的使用者圖示，然後按一下 [**登出]**。
    
2. 請移至 [https://admin.microsoft.com](https://admin.microsoft.com)。
    
3. 在**Office 365 登入**] 頁面上，按一下 [**使用另一個帳戶**。
    
4. 輸入 User5 帳戶名稱和密碼，然後再按一下 [**登入**。
    
5. 在瀏覽器的新索引標籤上，輸入業務部網站集合的 URL。
    
6. 在 [**銷售網站集合**的**文件**資料夾，按一下 [ **SensitiveData BeforeIRM.docx**文件。
    
    您應該會看到其內容。
    
7. 關閉**文件**和**銷售網站集合**] 索引標籤。
    
藉由不小心張貼 SensitiveData BeforeIRM.docx 文件上業務部網站集合，CEO 略過主管網站集合的權限安全性。
  
若要準備階段 3 和 4 的 Office 365，請針對 SharePoint Online 中啟用 IRM。
  
1. 在 [ **Microsoft Office 的首頁**] 索引標籤中，按一下右上角的使用者圖示，然後按一下 [**登出]**。
    
2. 請移至 [https://admin.microsoft.com](https://admin.microsoft.com)。
    
3. 在**Office 365 登入**頁面上，按一下 [全域管理員帳戶名稱，輸入其密碼，然後按一下 [**登入**。
    
4. 在 [ **Microsoft Office 的首頁**] 索引標籤中，按一下 [**系統 > 系統管理員中心 > SharePoint**。
    
5. 在**SharePoint 系統管理中心**] 索引標籤上，按一下 [**設定**]。
    
6. 在頁面上，在 [**資訊版權管理 (IRM)** ] 區段中，選取 [**使用在您的組態中指定的 IRM 服務**]，然後選取 [**重新整理 IRM 設定**。
    
7. 關閉 [ **SharePoint 系統管理中心**] 索引標籤。
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a>階段 3： 使用 SharePoint 資訊版權管理與 Office 365 私人群組

在這個階段，您使用 SharePoint 資訊版權管理與 Office 365 私人群組保護敏感資訊，與文件存取的即使它開啟的權限與網站上張貼。
  
首先，您會啟用，並將 IRM 設定主管網站集合的文件庫。 
  
1. 在瀏覽器的新索引標籤上，輸入高階主管的網站集合的 URL。
    
2. 按一下 [文件]****。
    
3. 在右上角，按一下 [設定] 圖示，然後按一下**文件庫設定**。
    
4. 在 [**設定**] 頁面上的**權限與管理**] 下按一下 [**資訊版權管理**]。
    
5. 在 [**資訊版權管理設定**] 頁面上：
    
  - 選取 [**限制下載此文件庫中的文件的權限**]。
    
  - **建立權限原則標題**]，輸入 [**主管**]。
    
  - [**新增權限原則描述**] 中，輸入**高階主管的 IRM**。
    
6. 按一下 [顯示選項]****。
    
7. **設定其他 IRM 文件庫設定**] 下選取 [**不允許使用者上傳文件，並不支援 IRM**。
    
8. [**設定文件的存取權限**，選取**要列印的允許檢視**和**寫入在下載文件的複本上的允許檢視**。
    
9. **設定群組保護和認證間隔**] 下選取 [**允許群組保護]。預設群組**，然後輸入**高階主管**。
    
10. 按一下 [確定]****。
    
接下來，做為 CEO，您將新的文件上傳至行政人員文件資料夾，下載，然後不小心將其上傳到銷售文件資料夾。
  
1. 開啟您儲存**SensitiveData BeforeIRM.docx**文件的本機資料夾。
    
2. **SensitiveData BeforeIRM.docx**，以滑鼠右鍵按一下，然後按一下 [**複製]**。
    
3. 在資料夾中，以滑鼠右鍵按一下，然後按一下 [**貼**。
    
4. 新的**SensitiveData-BeforeIRM-Copy.docx**檔案重新命名為**SensitiveData AfterIRM.docx**。
    
5. 從瀏覽器的 [ **Microsoft Office 的首頁**] 索引標籤按一下右上角的使用者圖示，然後按一下 [**登出]**。
    
6. 請移至 [https://admin.microsoft.com](https://admin.microsoft.com)。
    
7. 在**Office 365 登入**頁面上，按一下 [CEO 帳戶名稱，輸入其密碼，然後按一下 [**登入**。
    
8. 在瀏覽器的新索引標籤上，輸入高階主管的網站集合的 URL。
    
9. 在 [**文件**] 頁面上，按一下 [**上傳**、 指定**SensitiveData AfterIRM.docx**文件在本機資料夾中，，然後按一下 [**開啟**。
    
10. 選取新**SensitiveData AfterIRM.docx**文件中**的文件**] 頁面上，按一下 [功能表列中的省略符號 （...），然後按一下 [**下載**。
    
11. 出現提示時，將**SensitiveData AfterIRM.docx**文件儲存您的本機資料夾，並覆寫原始版本。
    
12. 關閉 [**文件**] 頁面上的索引標籤。
    
13. 在瀏覽器的新索引標籤上，輸入業務部網站集合的 URL。
    
14. 按一下 [文件]****。
    
15. 在 [**文件**] 頁面上，按一下 [**上傳**、 指定**SensitiveData AfterIRM.docx**文件在本機資料夾中，，然後按一下 [**開啟**。
    
16. 關閉 [**銷售網站集合**和**SharePoint**索引標籤。
    
接下來，做為一般使用者，您嘗試存取**SensitiveData AfterIRM.docx**文件中的銷售文件資料夾。
  
1. 從瀏覽器的 [ **Microsoft Office 的首頁**] 索引標籤按一下右上角的使用者圖示，然後按一下 [**登出]**。
    
2. 請移至 [https://admin.microsoft.com](https://admin.microsoft.com)。
    
3. 在**Office 365 登入**頁面上，按一下 [User5 帳戶名稱，輸入其密碼，然後按一下 [**登入**。
    
4. 在瀏覽器的新索引標籤上，輸入業務部網站集合的 URL。
    
5. 按一下 [文件]****。
    
6. 在 [**文件**] 頁面上，開啟**SensitiveData AfterIRM.docx**文件。
    
    您應該會看到訊息指出，「 很抱歉，Word 無法開啟這份文件，因為它受到資訊版權管理 (IRM) 保護。 」 
    
7. 按一下 [**在 Word 中編輯**]。 如果您想要開啟的檔案，會提示您。 按一下 [是]****。
    
8. 系統提示您登入。 輸入帳戶的 User5 帳戶名稱，然後再按 [**下一步**。
    
9. 系統會提示您提供的密碼。 輸入 User5 帳戶的密碼，然後按一下 [**登入**。 
    
    您應該會看到訊息，說明如下: 「 您沒有可讓您開啟此文件的認證。 」
    
10. 按一下 [**否**]。
    
若要查看的 IRM 保護的另一個方式是要查看您的本機資料夾中的檔案。 **SensitiveData AfterIRM.docx**應該遠大於**SensitiveData BeforeIRM.docx**檔案。 **SensitiveData AfterIRM.docx**檔案進行加密，並已新增的 IRM 保護資訊。
  
## <a name="see-also"></a>另請參閱

[雲端採用測試實驗室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基底組態開發/測試環境](base-configuration-dev-test-environment.md)
  
[Office 365 開發/測試環境](office-365-dev-test-environment.md)
  
[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)


