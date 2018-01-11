---
title: "Office 365 開發人員/測試環境中的機密檔案保護"
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
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: "摘要： 設定及示範如何 Office 365 資訊版權管理會保護敏感性檔案，甚至是當他們會張貼至錯誤的 SharePoint Online 網站集合。"
ms.openlocfilehash: eb456c86b118556abde6a887fe8b9ab68300740b
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2018
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a>Office 365 開發人員/測試環境中的機密檔案保護

 **摘要：**設定及示範如何 Office 365 資訊版權管理會保護敏感性檔案，甚至是當他們會張貼至錯誤的 SharePoint Online 網站集合。
  
資訊版權管理 (IRM) 設定在 Office 365 是一組的保護從 SharePoint Online 的文件庫及清單下載的文件的功能。下載的檔案加密及儲存 」、 「 包含開啟複本，且列印反映已儲存的 SharePoint Online 文件庫的權限。
  
使用本文中的指示，啟用並測試 IRM 在 Office 365 中包含在您的 Office 365 試用版訂閱可能敏感資訊的檔案。
  
> [!TIP]
> 按一下[此處](http://aka.ms/catlgstack)的視覺對應至一個 Microsoft Cloud 測試實驗室指南堆疊中所有的文章。
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>階段 1： 建立 Office 365 開發人員/測試環境

如果您只想要測試機密檔案保護的基本需求的輕量型方式，請在階段 2 和 3 的[Office 365 開發人員/測試環境](office-365-dev-test-environment.md)中遵循的指示。
  
如果您想要測試機密檔案保護模擬 enterprise 中，請遵循[DirSync Office 365 開發人員/測試環境](dirsync-for-your-office-365-dev-test-environment.md)中的指示。
  
> [!NOTE]
> 測試機密檔案保護不需要模擬的 enterprise 開發人員/測試環境中，其中包含連線至網際網路模擬內部網路和 Windows Server AD 樹系目錄同步處理。它會提供這裡是做為選項可以測試機密檔案保護和代表的典型組織的環境中實驗。 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a>階段 2： 示範如何可以洩露從權限保護之網站的文件

在此階段中，您會示範某個人可以從權限保護網站下載文件並再將其上傳至網站具有廣泛開放的權限。
  
首先，您可以新增三個新的使用者帳戶的代表高階主管並且指派 Office 365 E5 授權。
  
使用[Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx)中的指示安裝的 PowerShell 模組 （如果需要） 並連線至您從新的 Office 365 訂閱：
  
- 您的電腦 (適用於輕量型 Office 365 開發/測試環境)。
    
- CLIENT1 虛擬機器 （適用於模擬的企業版 Office 365 開發人員/測試環境中）。
    
在 [ **Windows PowerShell 認證要求**] 對話方塊中，輸入 Office 365 全域管理員名稱 (範例： jdoe@contosotoycompany.onmicrosoft.com) 和 Office 365 試用版訂閱的密碼。
  
填入您的組織名稱 (範例： contosotoycompany) 和雙字元國家位置、 程式碼與 Windows Azure Active Directory Module for Windows PowerShell 提示字元執行下列命令：
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

從**New-msoluser**命令顯示，請注意 CEO 帳戶產生的密碼並將其記錄在安全的位置。
  
從適用於 Windows PowerShell 的 Windows Azure Active Directory 模組提示字元中執行下列命令︰
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

從**New-msoluser**命令顯示，請注意 CFO 帳戶產生的密碼並將其記錄在安全的位置。
  
從適用於 Windows PowerShell 的 Windows Azure Active Directory 模組提示字元中執行下列命令︰
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

從**New-msoluser**命令顯示，請注意 COO 帳戶產生的密碼並將其記錄在安全的位置。
  
接下來，您建立專用的高階主管群組並將新的高階主管帳戶新增至其。
  
1. 在瀏覽器中移至[http://portal.office.com](http://portal.office.com) Office 入口網站並登入您的 Office 365 試用版訂閱以全域管理員帳戶。
    
  - 如果您使用輕量型 Office 365 開發人員/測試環境，開啟 Internet Explorer 或瀏覽器中的私人工作階段並登入從本機電腦。
    
  - 如果您使用模擬的企業版 Office 365 開發人員/測試環境，使用 Azure 入口網站連線到 CLIENT1 虛擬機器，並從 CLIENT1 登入。
    
2. 在 [ **Microsoft Office Home** ] 索引標籤上按一下 [ **Admin > 群組 > 群組**，然後按一下 [**新增群組**。
    
3. 在**加入群組**]，選取**Office 365 群組**的群組類型、 輸入**高階主管**[**名稱**] 及 [**群組識別碼**，針對**隱私權**，選取 [**私人**，然後按一下 [**選取擁有者**。
    
4. 在清單中，按一下 [全域管理員帳戶名稱。
    
5. 按一下 [**新增**] 和 [**關閉**。
    
6. 在 [群組] 清單中，按一下 [**高階主管**。
    
7. 按一下 [**編輯的成員**。
    
8. 按一下 [**新增成員**。在 [成員] 清單中，選取下列的使用者帳戶：
    
  - 執行長
    
  - 主要的財務主管人員
    
  - 首席作業人員
    
9. 按一下 [**儲存**] 及 [**關閉**。
    
10. 關閉**Office 系統管理中心**] 索引標籤。
    
接著，您建立高階主管的網站集合並允許對其進行存取的高階主管群組成員。
  
1. 在 [ **Microsoft Office Home** ] 索引標籤上按一下**系統管理**磚。
    
2. 在 [ **Office 系統管理中心**] 索引標籤上按一下 [**系統中心 > SharePoint**。
    
3. 在**SharePoint 管理中心**] 索引標籤上，按一下 [**新增 > 私用網站集合**。
    
4. 在 [新網站集合] 窗格中輸入**標題**] 中 [URL] 方塊中的高階主管的**高階主管****管理員**中指定全域管理員帳戶的名稱，然後按一下 [**確定]**。
    
5. 等到已建立新的網站集合。完成後，將複製新的高階主管網站集合的 URL 並將它貼到新的索引標籤的瀏覽器。
    
6. 在右上角**高階主管**的網站集合中，按一下 [設定] 圖示，然後按一下 [**共用對象**。
    
7. 在**共用 'Executives'**，按一下 [**進階**]。
    
8. 在 SharePoint 群組的清單中，按一下 [**高階主管成員**。
    
9. 在 [**人員與群組**] 頁面上按一下 [**新增**]。
    
10. 在**共用 'Executives'**輸入**高階主管**、**高階主管**] 群組中，按一下 [，然後按一下 [**共用**。
    
11. 關閉 [**人員與群組**] 索引標籤。
    
接下來，您讓所有人存取業務部網站集合。
  
1. 從 [ **SharePoint 管理中心**] 索引標籤複製業務部網站集合的 URL，並將它貼到新的索引標籤的瀏覽器.
    
2. 在右上方，按一下 [設定] 圖示，和 [**共用對象**。
    
3. 在**共用 'Sales 網站集合'**，按一下 [**進階**]。
    
4. 在 SharePoint 群組的清單中，按一下 [**銷售網站集合的成員**。
    
5. 在 [**人員與群組**] 頁面上按一下 [**新增**]。
    
6. 在**共用 'Sales 網站集合 」**，輸入**所有人**、 按一下 [**所有人以外的外部使用者**，和 [**共用**。
    
7. 關閉 [**銷售網站集合**和**SharePoint** ] 索引標籤。
    
接下來，您使用高階主管的帳戶登入和主管網站集合中建立的文件。
  
1. 在 [ **Microsoft Office Home** ] 索引標籤上按一下 [使用者] 圖示的右上角和 [**登出**。
    
2. 移至[http://portal.office.com](http://portal.office.com)。
    
3. 按一下 [ **Office 365 登入**] 索引標籤的 [**使用其他帳戶**]。
    
4. 輸入**CEO**帳戶名稱和它的密碼，然後按一下 [**登入**。
    
5. 在瀏覽器的新] 索引標籤上輸入高階主管的網站集合的 URL ( **https://**\<組織名稱 >**.sharepoint.com/sites/executives**)。
    
6. 按一下 [**文件**、 按一下 [**新增]**和 [ **Word 文件**。
    
7. 按一下標題列中，輸入**SensitiveData BeforeIRM**。
    
8. 按一下 [內文件和輸入**從最新的佈告欄會議分鐘**，和 [**高階主管**。
    
     您應該會看到**SensitiveData BeforeIRM.docx** **文件**] 資料夾中。
    
接下來，您下載 SensitiveData BeforeIRM.docx 文件的本機複本與意外將張貼至銷售網站集合。
  
1. 在您的本機電腦上建立新的資料夾 (例如 c:\\Tlg\\SensitiveDataTestFiles)。
    
2. 在瀏覽器的**文件**] 索引標籤上選取**SensitiveData BeforeIRM.docx**文件、 按一下省略符號，並再按一下 [**下載**。
    
3. 步驟 1 中建立的資料夾中儲存的**SensitiveData BeforeIRM.docx**文件。
    
4. 新增索引標籤上的瀏覽器中，輸入 [業務部網站集合的 URL ( **https://**\<組織名稱 >**.sharepoint.com/sites/sales**)。
    
5. 按一下 [**文件**] 資料夾的**銷售網站集合**。
    
6. 按一下 [**上傳**，然後指定**SensitiveData BeforeIRM.docx**文件中的步驟 1 中建立的資料夾，然後按一下 [**確定]**。
    
7. 確認**SensitiveData BeforeIRM.docx**文件是在**文件**] 資料夾中。
    
8. 關閉 [**銷售**及**SharePoint**索引標籤。
    
接著，您 User5 身分，登入並嘗試在業務部網站集合中開啟 SensitiveData BeforeIRM.docx 文件。
  
1. 在 [ **Microsoft Office Home** ] 索引標籤上按一下 [使用者] 圖示的右上角和 [**登出**。
    
2. 移至[http://portal.office.com](http://portal.office.com)。
    
3. 按一下 [ **Office 365 登入**] 索引標籤的 [**使用其他帳戶**]。
    
4. 輸入 User5 帳戶名稱和它的密碼，然後按一下 [**登入**。
    
5. 在瀏覽器的新] 索引標籤上輸入業務部網站集合的 URL。
    
6. 在 [**文件**] 資料夾的**銷售網站集合**，按一下 [ **SensitiveData BeforeIRM.docx**文件。
    
    您應該查看其內容。
    
7. 關閉**文件**和**銷售網站集合**] 索引標籤。
    
意外張貼 SensitiveData BeforeIRM.docx 文件業務部網站集合中，執行長略過的高階主管的網站集合的權限安全性。
  
若要準備 Office 365 階段 3 和 4，啟用 IRM 的 SharePoint Online。
  
1. 在 [ **Microsoft Office Home** ] 索引標籤上按一下 [使用者] 圖示的右上角和 [**登出**。
    
2. 移至[http://portal.office.com](http://portal.office.com)。
    
3. 在**Office 365 登入**] 頁面上按一下 [全域管理員帳戶名稱、 並輸入其密碼，然後按一下 [**登入**。
    
4. 在 [ **Microsoft Office Home** ] 索引標籤上按一下 [ **Admin > 系統中心 > SharePoint**。
    
5. 在 [ **SharePoint 管理中心**] 索引標籤上按一下 [**設定**]。
    
6. 在 [**設定**] 頁面上的 [**資訊版權管理 (IRM)** ] 區段中選取 [**使用您的設定中指定的 IRM 服務**]，然後選取**重新整理 IRM 設定**。
    
7. 關閉 [ **SharePoint 管理中心**] 索引標籤。
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a>階段 3： 使用 SharePoint 資訊版權管理與 Office 365 私人群組

在此階段中，您使用 SharePoint 資訊版權管理與 Office 365 私人群組會張貼站台的與開啟的權限，即使保護敏感資訊的文件的存取。
  
首先，啟用並設定 IRM 的高階主管的網站集合的文件庫。 
  
1. 在瀏覽器的新] 索引標籤上輸入高階主管的網站集合的 URL。
    
2. 按一下 [**文件**。
    
3. 右上角的 [設定] 圖示，和 [**文件庫設定**。
    
4. 在 [**設定**] 頁面**的權限與管理**] 下按一下 [**資訊版權管理**。
    
5. 在 [**資訊版權管理設定**] 頁面上：
    
  - 選取 [**限制下載此文件庫中的文件的權限**。
    
  - **建立權限原則標題**、 輸入**高階主管**。
    
  - **新增權限原則描述**]，輸入**IRM 的高階主管**。
    
6. 按一下 [**顯示選項**]。
    
7. **設定其他 IRM 文件庫設定**] 下選取 [**不允許使用者上傳的不支援 IRM 的文件**。
    
8. [**設定文件存取權**，選取**要列印的允許檢視器**並**允許寫入已下載的文件的複本上的檢視器**。
    
9. **設定群組保護和認證的時間間隔**] 下選取 [**允許群組保護**和**預設群組**中，輸入**高階主管**。
    
10. 按一下 [確定]****。
    
下一步] 做為執行長，您將新的文件上傳至高階主管的文件資料夾、 下載、 然後意外將其上傳至銷售文件資料夾。
  
1. 開啟您儲存**SensitiveData BeforeIRM.docx**文件的本機資料夾。
    
2. 以滑鼠右鍵按一下**SensitiveData BeforeIRM.docx**，並再按一下 [**複製**。
    
3. 以滑鼠右鍵按一下資料夾內並再按一下 [**貼**。
    
4. 新**SensitiveData-BeforeIRM-Copy.docx**檔案重新命名**SensitiveData AfterIRM.docx**。
    
5. 從您的瀏覽器的 [ **Microsoft Office Home** ] 索引標籤按一下 [在右上角的 [使用者] 圖示] 和 [**登出**。
    
6. 移至[http://portal.office.com](http://portal.office.com)。
    
7. 在**Office 365 登入**] 頁面上按一下 [CEO 帳戶名稱、 並輸入其密碼，然後按一下 [**登入**。
    
8. 在瀏覽器的新] 索引標籤上輸入高階主管的網站集合的 URL。
    
9. 在 [**文件**] 頁面上，按一下 [**上傳**、 指定**SensitiveData AfterIRM.docx**文件您在本機資料夾、，然後按一下 [**開啟**。
    
10. 在**文件**] 頁面中選取新的**SensitiveData AfterIRM.docx**文件、 按一下 [功能表] 列中的省略符號 （...） 和 [**下載**。
    
11. 出現提示時，將**SensitiveData AfterIRM.docx**文件儲存在本機資料夾，並覆寫原始版本。
    
12. 關閉**文件**頁面] 索引標籤。
    
13. 在瀏覽器的新] 索引標籤上輸入業務部網站集合的 URL。
    
14. 按一下 [**文件**。
    
15. 在 [**文件**] 頁面上，按一下 [**上傳**、 指定**SensitiveData AfterIRM.docx**文件您在本機資料夾、，然後按一下 [**開啟**。
    
16. 關閉 [**銷售網站集合**和**SharePoint** ] 索引標籤。
    
下一步] 做為一般使用者，嘗試存取**SensitiveData AfterIRM.docx**文件的銷售文件資料夾中。
  
1. 從您的瀏覽器的 [ **Microsoft Office Home** ] 索引標籤按一下 [在右上角的 [使用者] 圖示] 和 [**登出**。
    
2. 移至[http://portal.office.com](http://portal.office.com)。
    
3. 在**Office 365 登入**] 頁面上按一下 [User5 帳戶名稱，並輸入其密碼，然後按一下 [**登入**。
    
4. 在瀏覽器的新] 索引標籤上輸入業務部網站集合的 URL。
    
5. 按一下 [**文件**。
    
6. 在 [**文件**] 頁面開啟**SensitiveData AfterIRM.docx**文件。
    
    您應該會看到訊息指出 「 很抱歉，因為它會受到資訊版權管理 (IRM) Word Online 無法開啟此文件。 」 
    
7. 按一下 [**在 Word 中編輯**]。系統提示您若要開啟的檔案。按一下 [**是]**。
    
8. 登入提示您輸入 User5 帳戶的帳戶名稱，然後按 [**下一步**。
    
9. 系統提示您提供密碼。輸入 User5 帳戶的密碼，然後按一下 [**登入**。 
    
    您應該會看到訊息表示： 「 您沒有可讓您開啟此文件的認證。 」
    
10. 按一下 [**否]**。
    
若要查看 IRM 保護的另一種方式是要查看您的本機資料夾中的檔案。**SensitiveData AfterIRM.docx**應該更加大於**SensitiveData BeforeIRM.docx**檔案。加密**SensitiveData AfterIRM.docx**檔案，而且已新增 IRM 保護資訊。
  
## <a name="see-also"></a>請參閱

[雲端採用測試實驗室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基底組態開發/測試環境](base-configuration-dev-test-environment.md)
  
[Office 365 開發/測試環境](office-365-dev-test-environment.md)
  
[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)


