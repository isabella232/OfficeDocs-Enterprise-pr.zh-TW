---
title: "Office 365 開發/測試環境"
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
- Ent_TLGs
ms.assetid: 4f6035b8-2da3-4cf9-9657-5284d6364f7a
description: "摘要： 使用此測試實驗室指南建立評估或開發人員/測試的 Office 365 試用版訂閱。"
ms.openlocfilehash: 734bc694c8be45a92cabc82aebe7a83726247e3b
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="office-365-devtest-environment"></a>Office 365 開發/測試環境

 **摘要：**使用此測試實驗室指南建立評估或開發人員/測試的 Office 365 試用版訂閱。
  
您可以使用 Office 365 試用版訂閱及建立 Office 365 開發人員/測試環境的應用程式或示範 Office 365 的特性與功能。有兩種版本：
  
- 輕量型 Office 365 開發人員/測試環境包含您從主要的電腦存取 Office 365 試用版訂閱。
    
    當您想要快速示範功能使用此環境。輕量型 Office 365 開發人員/測試環境中，完成階段 2 和 3 的本文。
    
- 模擬的企業版 Office 365 開發人員/測試環境包含 Office 365 試用版訂閱] 與 [連線至網際網路，則會在 Microsoft Azure 基礎結構服務裝載簡化的組織內部網路。您可以建立 Microsoft 雲端中完全這個設定。
    
    使用此環境時要示範格式類似於連線至網際網路、 或功能需要這種類型的環境的典型組織網路環境中的應用程式或功能。模擬企業版 Office 365 開發人員/測試環境中，完成階段 1、 2 及 3 的本文。
    
> [!NOTE]
> 您可能會想要列印本文章來記錄您需要對此環境的 Office 365 試用版訂閱 30 天的特定值。您可以輕鬆地擴充另一個 30 天的軌跡訂閱。在永久的開發人員測試環境中建立新付費少量的授權與訂閱。 
  
![Microsoft 雲端中的測試實驗室指南](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> 按一下[此處](http://aka.ms/catlgstack)的視覺對應至一個 Microsoft Cloud 測試實驗室指南堆疊中所有的文章。
  
## <a name="phase-1-create-the-base-configuration-in-azure"></a>階段 1： 在 Azure 中建立基本組態

請遵循[基本設定開發/測試環境](base-configuration-dev-test-environment.md)中的指示。
  
您將需要 Azure 訂閱。您可以使用[Azure 免費試用版](https://azure.microsoft.com/pricing/free-trial/)這個設定。如果您有 MSDN 或 Visual Studio 訂閱，請參閱[Visual Studio 訂閱者的每月 Azure 信用](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/)。
  
以下是所產生的設定。
  
![Azure 基底組態開發/測試環境](images/63108214-f716-46ae-9974-072ff15b44a2.png)
  
此設定是由 DC1、 APP1 和 CLIENT1 虛擬機器上的 Azure 虛擬網路子網路所組成。
  
## <a name="phase-2-create-an-office-365-trial-subscription"></a>階段 2： 建立 Office 365 試用版訂閱

若要啟動您的 Office 365 E5 試用版訂閱，您首先需要虛構公司名稱和新的 Microsoft 帳戶。
  
1. 我們建議您的公司名稱 Contoso variant 用於您公司的名稱，也就是使用中 Microsoft 範例內容虛構公司，但並非必要。記錄您的虛構公司名稱： ___
    
2. 若要註冊新的 Microsoft 帳戶，移至[https://outlook.com](https://outlook.com)並建立新的電子郵件帳戶和地址的帳戶。此帳戶會用於註冊 Office 365。
    
  - 您新增的帳戶的第一個及最後一個名稱記錄： ___
    
  - 記錄的新電子郵件帳戶地址這裡： ___@outlook.com
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a>註冊 Office 365 E5 試用訂閱

1. 輕量型 Office 365 開發人員/測試環境中，開啟您電腦上的 [網際網路瀏覽器並移至[https://aka.ms/e5trial](https://aka.ms/e5trial)。 
    
    模擬企業版 Office 365 開發人員/測試環境中：
    
  - 從[Azure 入口網站](https://portal.azure.com)連線到與公司 CLIENT1\\User1 帳戶。
    
  - 開啟系統管理員層級 Windows PowerShell 命令提示字元處，並再執行下列命令：
    
  ```
  Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force
  ```

    > [!TIP]
    > 按一下[這裡](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34)以取得包含在本文中的所有 PowerShell 命令的文字檔案。
  
  - 從 [開始] 畫面中，按一下 [ **Internet Explorer** ，並移至[https://aka.ms/e5trial](https://aka.ms/e5trial)。
    
2. 在 [**歡迎使用，讓我們知道您取得**] 頁面上指定：
    
  - 實體位置
    
  - 在新的 Microsoft 帳戶的第一個及最後一個名稱
    
  - 新的電子郵件帳戶地址
    
  - 商務電話號碼
    
  - 虛構公司名稱
    
  - 組織大小 250 999 人
    
3. 按一下 [**只是一個詳細步驟**。
    
4. 在 [**建立您的使用者識別碼**] 頁面上輸入您新的電子郵件地址之後, 虛構公司為基礎的使用者名稱 @ 符號 （移除所有分隔名稱中），後面接著密碼 （按兩次） 這個新的 Office 365 帳戶。
    
    記錄您在安全的位置中輸入密碼。
    
    記錄您虛構公司名稱，以作為**組織名稱**，此處參照： ___
    
5. 按一下 [**建立我的帳號**。
    
6. 在**證明。您正在文章。不。A.機器人。**] 頁面上，輸入您文字可使用電話的電話號碼和 [**文字我**。
    
7. 輸入從已接收之的文字郵件驗證碼，然後按 [**下一步**。
    
8. 登入頁面 URL 記錄以下 （選取和複本）： ___
    
9. 記錄使用者識別碼此處 （選取和複本）： ___.onmicrosoft.com
    
    這個值將被稱為**Office 365 全域管理員名稱**。
    
10. 當您看到**您準備好要移**時，請按一下它。
    
11. 在 [下一步] 頁面上等到 Office 365 設定完成設定和所有並排顯示可用。
    
您應該會看到您可以從中存取 Office Online 服務及 Office 365 系統管理中心的主要 Office 365 入口網站頁面。
  
模擬的企業版 Office 365 開發人員/測試環境，以下是您所產生的設定。
  
![Office 365 開發/測試環境](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
此組態組成為： 
  
- DC1、 APP1 和 CLIENT1 虛擬機器上的 Azure 虛擬網路子網路。
    
- Office 365 E5 列印試用訂閱。
    
## <a name="phase-3-configure-your-office-365-trial-subscription"></a>階段 3： 設定您的 Office 365 試用版訂閱

在此階段中，您可以設定您的 Office 365 訂閱與其他使用者和 SharePoint Online 小組網站。
  
首先，您新增四個新的使用者並指派它們 E5 授權。
  
使用[Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx)中的指示安裝的 PowerShell 模組並連線至您從新的 Office 365 訂閱：
  
- 您的電腦 (適用於輕量型 Office 365 開發/測試環境)。
    
- CLIENT1 虛擬機器 （適用於模擬的企業版 Office 365 開發人員/測試環境中）。
    
 在 [Windows PowerShell 認證要求] 對話方塊中，輸入 Office 365 全域管理員名稱 (範例： jdoe@contosotoycompany.onmicrosoft.com) 和密碼。
  
填入您的組織名稱 (範例︰contosotoycompany)，位置的兩個字元國家/地區代碼，再從適用於 Windows PowerShell 的 Windows Azure Active Directory 模組提示字元中執行下列命令︰
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "user2@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 2" -FirstName User -LastName 2 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

從**New-msoluser**命令顯示，記下所產生的使用者 2 帳戶的密碼並將其記錄在安全的位置。
  
從適用於 Windows PowerShell 的 Windows Azure Active Directory 模組提示字元中執行下列命令︰
  
```
$userName= "user3@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 3" -FirstName User -LastName 3 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

從**New-msoluser**命令顯示，記下所產生的使用者 3 帳戶的密碼並將其記錄在安全的位置。
  
從適用於 Windows PowerShell 的 Windows Azure Active Directory 模組提示字元中執行下列命令︰
  
```
$userName= "user4@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 4" -FirstName User -LastName 4 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

從**New-msoluser**命令顯示，記下所產生的使用者 4 帳戶的密碼並將其記錄在安全的位置。
  
從適用於 Windows PowerShell 的 Windows Azure Active Directory 模組提示字元中執行下列命令︰
  
```
$userName= "user5@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 5" -FirstName User -LastName 5 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

從**New-msoluser**命令顯示，記下所產生的使用者 5 帳戶的密碼並將其記錄在安全的位置。
  
接下來，您建立三個新的 SharePoint Online 小組網站的銷售、 實際執行，並支援部門。
  
### <a name="create-three-new-sharepoint-online-team-sites"></a>建立三個新的 SharePoint Online 小組網站

1. 安裝[SharePoint Online 管理命令介面](https://go.microsoft.com/fwlink/p/?LinkId=255251)(x64 版)。
    
2. 按一下 [**開始]**、 輸入**sharepoint**、 及 [ **SharePoint Online 管理命令介面**。
    
3. 填入您的組織名稱 (範例： contosotoycompany)，然後連線至 SharePoint Online 服務在 SharePoint Online 管理命令介面提示字元處執行下列命令
```
$orgName="<organization name>"
$spURL="https://" + $orgName + "-admin.sharepoint.com"
Connect-SPOService -Url $spURL
```

4. 在 [ **Microsoft SharePoint Online 管理命令介面**] 對話方塊中，輸入 Office 365 全域管理員名稱 (範例： jdoe@contosotoycompany.onmicrosoft.com) 和密碼，然後按一下 [**登入**。
    
5. 若要建立三個新的小組網站 （銷售、 實際執行與支援） 填滿 Office 365 全域管理員名稱] 中，並從 SharePoint Online 管理命令介面提示字元執行下列命令：
    
  ```
  $owner = "<global administrator account name>"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/sales"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Sales site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/production"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Production site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/support"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Support site collection" -Template "STS#0"
  ```

6. 執行此命令以列出這些新網站的 Url：
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

7. 在 Internet Explorer 中，輸入來查看預設 SharePoint Online 小組網站的實際執行部門實際執行網站的 URL。
    
## <a name="record-values-for-future-reference"></a>以供未來參照的記錄值

記錄使用或其他測試實驗室指南此測試環境中部署這些值：
  
- Office 365 全域管理員名稱： ___.onmicrosoft.com （從階段 2 的步驟 9）
    
    也在安全的位置記錄此帳戶的密碼。
    
- 您的試用版訂閱的組織名稱： ___ （從步驟 4 的階段 2）
    
- 若要列出之帳戶的使用者 2、 3 使用者、 使用者 4 和使用者 5，請在 Windows Azure Active Directory Module for Windows PowerShell 提示字元處執行下列命令：
    
  ```
  Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    記錄的帳戶名稱：
    
  - 使用者 2 帳戶名稱： user2@___.onmicrosoft.com
    
  - 3 的使用者帳戶名稱： user3@___.onmicrosoft.com
    
  - 4 的使用者帳戶名稱： user4@___.onmicrosoft.com
    
  - 5 的使用者帳戶名稱： user5@___.onmicrosoft.com
    
    也在安全的位置記錄這些帳戶的密碼。
    
- 若要列出的 Url 的銷售、 實際執行，並支援小組網站，執行下列命令從 SharePoint Online 管理命令介面提示：
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

  - 實際執行網站 URL： https://___.sharepoint.com/sites/production
    
  - 銷售網站 URL： https://___.sharepoint.com/sites/sales
    
  - 支援的網站 URL： https://___.sharepoint.com/sites/support
    
## <a name="next-steps"></a>後續步驟

Office 365 開發人員/測試環境中使用這些額外的文章：
  
- [Office 365 開發/測試環境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)
    
- [Office 365 開發人員/測試環境的多重要素驗證](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
- [Office 365 開發人員/測試環境的同盟身分識別](federated-identity-for-your-office-365-dev-test-environment.md)
    
- [Office 365 開發人員/測試環境的雲端應用程式安全性](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
- [Office 365 開發人員/測試環境的進階威脅保護](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
- [Office 365 開發人員/測試環境的進階的 eDiscovery](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
- [Office 365 開發人員/測試環境中的機密檔案保護](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
- [隔離的 SharePoint Online 小組網站開發/測試環境](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
- [資料分類和 Office 365 開發人員/測試環境中顯示標籤](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
擴充 Office 365 開發人員/測試環境包含其他 Microsoft cloud 方案：
  
- [Microsoft 365 Enterprise 開發人員/測試環境](the-microsoft-365-enterprise-dev-test-environment.md)
    
- [Office 365 和 Dynamics 365 開發/測試環境](office-365-and-dynamics-365-dev-test-environment.md)
    
## <a name="see-also"></a>請參閱

[雲端採用測試實驗室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[Office 365 和 Dynamics 365 開發/測試環境](office-365-and-dynamics-365-dev-test-environment.md)
  
[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)


