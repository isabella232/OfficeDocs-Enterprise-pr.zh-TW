---
title: Office 365 開發/測試環境
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/02/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 4f6035b8-2da3-4cf9-9657-5284d6364f7a
description: 摘要：使用此測試實驗室指南來建立 Office 365 試用訂閱以進行評估或開發/測試。
ms.openlocfilehash: 3e7aafc847b28ad7a81373539c2ea30ce304725a
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487585"
---
# <a name="office-365-devtest-environment"></a>Office 365 開發/測試環境

 **摘要：** 使用此測試實驗室指南來建立 Office 365 試用訂閱以進行評估或開發/測試。
  
您可以使用 Office 365 試用訂閱，並建立適用於應用程式的 Office 365 開發/測試環境或示範 Office 365 功能及能力。有兩種版本：
  
- 輕量型 Office 365 開發/測試環境包含您從主要電腦存取的 Office 365 試用訂閱。
    
    當您想要快速地示範一項功能時，請使用此環境。針對輕量型 Office 365 開發/測試環境，僅需完成這篇文章中的階段 2 和 3。
    
- 模擬的企業 Office 365 開發/測試環境包含 Office 365 試用訂閱，以及連線到網際網路的簡化組織之內部網路，此會在 Microsoft Azure 基礎結構服務中進行主控。您可以在 Microsoft 雲端中完整建置此組態。
    
    當您想要在與連接至網際網路之一般組織網路類似的環境中，或是針對需要此類環境的功能示範某項功能或某個應用程式時，請使用此環境。針對模擬企業 Office 365 開發/測試環境，請完成此文章的階段 1、2 和 3。
    
> [!NOTE]
> 您可能會想要列印此文章來記錄此環境在 Office 365 試用訂閱的 30 天期間所需的特定值。您可以輕鬆地延長試用訂閱額外 30 天的時間。針對永久開發/測試環境，新建含少量授權的付費訂閱。 
  
![Microsoft Cloud 中的測試實驗室指南](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> 按一下[這裡](http://aka.ms/catlgstack)，可查看 Office 365 測試實驗室指南堆疊中文章的所有視覺對應。
  
## <a name="phase-1-create-the-base-configuration-in-azure"></a>階段 1：Azure 中建立基本設定

遵循在[基底組態開發/測試環境](base-configuration-dev-test-environment.md)中的指示。
  
您將需要 Azure 訂閱。您可以將 [Azure 免費試用版](https://azure.microsoft.com/pricing/free-trial/)用於此組態。如果您擁有 MSDN 或 Visual Studio 訂閱，請參閱 [Visual Studio 訂閱者的每月 Azure 點數](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/)。
  
以下是所產生的組態。
  
![Azure 基底組態開發/測試環境](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)


  
此組態包含 DC1、APP1 和在 Azure 虛擬網路子網路上的 CLIENT1 虛擬機器。
  
## <a name="phase-2-create-an-office-365-trial-subscription"></a>階段 2：建立 Office 365 試用訂閱

若要開始 Office 365 E5 試用訂閱，您需要虛構的公司名稱和新 Microsoft 帳戶。
  
1. 我們建議您使用公司名稱 Contoso 的變種作為公司名稱，也就是 Microsoft 範例內容中使用的虛構公司，但此為非必要的動作。在此處記錄您虛構公司名稱：![](./media/Common-Images/TableLine.png)
    
2. 若要註冊新 Microsoft 帳戶，請移至 [https://outlook.com ](https://outlook.com)，並使用新電子郵件帳戶以及地址建立帳戶。您會使用這個帳戶來登入 Office 365。
    
  - 在此處記錄您新帳戶的名字和姓氏：![](./media/Common-Images/TableLine.png)
    
  - 在此處記錄新電子郵件帳戶地址：![](./media/Common-Images/TableLine.png)@outlook.com
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a>註冊 Office 365 E5 試用訂閱

1. 針對輕量型 Office 365 開發/測試環境，開啟您電腦上的網際網路瀏覽器，然後移至 [https://aka.ms/e5trial](https://aka.ms/e5trial)。 
    
    針對模擬的企業 Office 365 開發/測試環境，使用來自 Azure 入口網站的 CORP\User1 帳戶連接至 CLIENT1。

    從 [開始] 畫面中，執行 Microsoft Edge，然後移至 [https://aka.ms/e5trial](https://aka.ms/e5trial)。
    
2. 在 [歡迎，讓我們認識您]**** 頁面上，指定：
    
  - 您的實際位置
    
  - 新 Microsoft 帳戶的名字和姓氏
    
  - 新電子郵件帳戶地址
    
  - 公司電話號碼
    
  - 虛構公司名稱
    
  - 250-999 名人員的組織規模
    
3. 按一下 [再多一個步驟]****。
    
4. 在 [建立使用者識別碼]**** 頁面上，根據新電子郵件地址輸入使用者名稱、在 @ 符號之後接上虛構公司 (移除名稱中的所有空格)，接著是此新 Office 365 帳戶的密碼 (兩次)。
    
    在安全位置中記錄您輸入的密碼。
    
    在這裡輸入虛構公司的名稱：![](./media/Common-Images/TableLine.png) (此將稱為**組織名稱**)
    
5. 按一下 [建立我的帳戶] ****。
    
6. 在 [證明您不是機器人。]**** 頁面中，輸入能夠傳送簡訊的手機號碼，然後按一下 [傳送簡訊給我]****。
    
7. 輸入已接收簡訊訊息中的驗證代碼，然後按 [下一步]****。
    
8. 在此記錄登入頁面 URL (選取並複製)：![](./media/Common-Images/TableLine.png)
    
9. 在此記錄使用者識別碼 (選取與複製)：![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
    此值將被稱為 **Office 365 全域系統管理員名稱**。
    
10. 當您看到 [您已準備就緒]****，對其按一下。
    
11. 在下一頁中，請稍候直到 Office 365 完成設定且所有的圖標皆可供使用。
    
您應會看到主要 Office 365 入口網站頁面，您可以從其中存取 Office Online 服務和 Microsoft 365 系統管理中心。
  
針對模擬的企業 Office 365 開發/測試環境，此為產生的組態。
  
![Office 365 開發/測試環境](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
此組態組成為： 
  
- DC1、APP1 和在 Azure 虛擬網路子網路上的 CLIENT1 虛擬機器。
    
- Office 365 E5 試用訂閱。
    
## <a name="phase-3-configure-your-office-365-trial-subscription"></a>階段 3：設定 Office 365 試用訂閱

在這個階段中，您可以設定其他使用者使用您的 Office 365 訂閱，並指派他們 Office 365 E5 授權。
  
使用[連線到 Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-azure-active-directory-powershell-for-graph-module) 中的指示，透過以下方式將 Azure Active Directory PowerShell for Graph 模組連線到您的 Office 365 訂閱：
  
- 您的電腦 (適用於輕量型 Office 365 開發/測試環境)。
    
- CLIENT1 虛擬機器 (適用於模擬的企業 Office 365 開發/測試環境)。
    
 在 [Windows PowerShell 認證要求] 對話方塊中，輸入 Office 365 全域管理員帳戶的使用者名稱 (例如：jdoe@contosotoycompany.onmicrosoft.com) 和密碼。
  
填入您的組織名稱 (範例︰contosotoycompany)，代表位置的兩個字元國家/地區代碼、常用帳戶密碼，再從 PowerShell 命令提示字元中執行下列命令：

```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$commonPW="<common user account password>"
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPW

$userUPN= "user2@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 2" -GivenName User -SurName 2 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user2"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign

$userUPN= "user3@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 3" -GivenName User -SurName 3 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user3"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign

$userUPN= "user4@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 4" -GivenName User -SurName 4 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user4"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

<!--
> [!TIP]
> Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34) to get a text file that has all the PowerShell commands in this article.
-->

  
## <a name="phase-4-create-three-new-sharepoint-online-team-sites-optional"></a>階段 4：建立三個新 SharePoint Online 小組網站 (選擇性)

您可以在這個階段設定一組 Sharepoint 小組網站。
  
1. 安裝 [SharePoint Online 管理命令介面](https://go.microsoft.com/fwlink/p/?LinkId=255251) (x64 版本)。
    
2. 按一下 [開始]****，輸入 [sharepoint]****，然後按一下 [SharePoint Online 管理命令介面]****。
    
3. 填入您組織名稱 (範例：contosotoycompany)，然後從 SharePoint Online 管理命令介面提示字元中執行下列命令，以連線至 SharePoint Online 服務
```
$orgName="<organization name>"
$spURL="https://" + $orgName + "-admin.sharepoint.com"
Connect-SPOService -Url $spURL
```

4. 在 [Microsoft SharePoint Online 管理命令介面] **** 對話方塊中，輸入 Office 365 全域管理員帳戶名稱 (例如：jdoe@contosotoycompany.onmicrosoft.com) 和密碼，然後按一下 [登入]****。
    
5. 若要建立三個新的小組網站 (銷售、產品和支援)，請填寫 Office 365 全域系統管理員名稱，並再從 SharePoint Online 管理命令介面提示字元中執行下列命令：
    
  ```
  $owner = "<global administrator account name>"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/sales"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Sales site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/production"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Production site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/support"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Support site collection" -Template "STS#0"
  ```

6. 執行此命令以列出這些新網站的 URL：
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

7. 在 Internet Explorer 中，輸入產品網站的 URL　以查看生產部門的預設 Sharepoint Online 小組網站。
    
## <a name="record-values-for-future-reference"></a>記錄值，以便日後參考

記錄這些值，以便在此測試環境中處理或部署其他測試實驗室指南：
  
- Office 365 全域系統管理員名稱：![](./media/Common-Images/TableLine.png).onmicrosoft.com (在階段 2 的步驟 9)
    
    將此帳戶的密碼記錄在安全的位置。
    
- 您的試用訂閱組織名稱：![](./media/Common-Images/TableLine.png) (從階段 2 的步驟 4)
    
- 若要列出使用者 2、使用者 3、使用者 4 和使用者 5 的帳戶，從適用於 Windows PowerShell 的 Windows Azure Active Directory 模組提示字元中執行下列命令︰
    
  ```
  Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    在此記錄帳戶名稱：
    
  - 使用者 2 的帳戶名稱：user2 @![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
  - 使用者 3 的帳戶名稱：user3 @![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
  - 使用者 4 的帳戶名稱：user4 @![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
  - 使用者 5 的帳戶名稱：user5 @![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
    將這些帳戶的密碼記錄於安全的位置。
    
- (選擇性) 若要列出銷售、生產和支援小組網站的 URL，請從 SharePoint Online 管理命令介面提示字元執行下列命令：
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

  - 產品網站 URL：https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/production
    
  - 銷售網站 URL：https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/sales
    
  - 支援網站 URL：https://![](./media/Common-Images/TableLine.png)
    
## <a name="next-steps"></a>後續步驟

在 Office 365 開發/測試環境中使用這些額外文章：
  
- [適用於 Office 365 開發/測試環境的目錄同步作業](dirsync-for-your-office-365-dev-test-environment.md)
    
- [適用於您的 Office 365 開發/測試環境的多重要素驗證](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
- [Office 365 開發人員/測試環境的同盟身分識別](federated-identity-for-your-office-365-dev-test-environment.md)
    
- [Office 365 開發人員/測試環境的雲端 App 安全性](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
- [適用於 Office 365 開發/測試環境的進階威脅防護](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
- [適用於 Office 365 開發/測試環境的進階電子文件探索](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
- [Office 365 開發/測試環境中的機密檔案保護](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
- [獨立的 SharePoint Online 小組網站開發/測試環境](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
- [Office 365 開發/測試環境中的資料分類和標示](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
## <a name="see-also"></a>另請參閱

- [雲端採用測試實驗室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
- [雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)


