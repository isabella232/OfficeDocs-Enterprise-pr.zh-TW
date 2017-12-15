---
title: "設定群組及使用者政治 campaign 開發/測試環境"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: None
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
ms.assetid: 0e22bcf3-bad3-42a4-b44f-276e0cf4790f
description: "摘要： 建立 Office 365 和 Enterprise 行動性 + 安全性 （EMS） 試用版訂閱使用者和群組政治 campaign 開發/測試環境。"
ms.openlocfilehash: 7faf428fc2225d3f31297ba6bf83a10a7682009a
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="configure-groups-and-users-for-a-political-campaign-devtest-environment"></a>設定群組及使用者政治 campaign 開發/測試環境

 **摘要：**使用使用者和群組政治 campaign 開發/測試環境中建立 Office 365 和 Enterprise 行動性 + 安全性 （EMS） 試用版訂閱。
  
若要建立包含簡化的使用者帳戶和群組[政治活動、 非營利機構，與其他靈活組織的 Microsoft 安全性指引](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)解決方案的開發人員/測試環境中使用本文中的指示。
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a>階段 1：建立 Office 365 開發/測試環境

在此階段中，您可以取得 Office 365 E5 和 Enterprise 行動性 + 代表政治 campaign 虛構組織的安全性 (EMS) E5 試用版的訂閱。
  
首先，請遵循**階段 2**的[Office 365 開發人員/測試環境](office-365-dev-test-environment.md)中的指示。
  
接下來，註冊 EMS E5 試用訂閱並將其新增至您的 Office 365 試用版訂閱相同的組織。
  
1. 必要時，登入 Office 365 入口網站與您的試用版訂閱的全域管理員帳戶的認證。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 按一下 [**系統**] 磚。
    
3. 在**Office 系統管理中心**] 索引標籤中瀏覽器中，在左導覽列中，按一下 [**帳務 > 購買服務**。
    
4. 在 [**購買服務**] 頁面上尋找**企業行動性 + 安全性 E5**項目。滑鼠指標停留並按一下 [**開始免費試用版**。
    
5. 在 [**確認您的訂單**] 頁面上按一下 [**立即試用**。
    
6. 在 [**順序回條**] 頁面上按一下 [**繼續**]。
    
接下來，可讓您的全域管理員帳戶 EMS E5 授權。
  
1. 在**Office 365 系統管理中心**] 索引標籤中瀏覽器中，在左導覽列中，按一下 [**使用者 > 作用中使用者**。
    
2. 按一下 [您的全域管理員帳戶] 和 [**編輯****產品**授權。
    
3. 在**產品授權**] 窗格中，開啟**企業行動性 + 安全性 E5** **上**至產品授權、 按一下 [**儲存]**及 [**關閉**兩次。
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups"></a>階段 2： 建立及設定您的 Azure Active Directory (AD) 群組

在此階段中，您建立及設定您的行銷活動的 Azure AD 群組。
  
首先，建立一組群組的一般政治行銷活動的 Azure 入口網站。
  
1. 在瀏覽器中個別] 索引標籤上移至[https://portal.azure.com](https://portal.azure.com)Azure 入口網站。必要時，登入的全域管理員帳戶認證的 Office 365 E5 試用版訂閱。
    
2. 在 Azure 入口網站中，按一下 [ **Azure Active Directory > 使用者和群組 > 的所有群組**。
    
3. 不要在此清單中每個群組名稱的下列步驟：
    
  - 資深和策略的人員
    
  - IT 人員
    
  - 分析的人員
    
  - 一般核心人員
    
  - 作業人員
    
  - 欄位的人員
    
1. 在**所有群組**blade 中，按一下 [ **+ 新群組**。
    
2. 在 [**名稱**輸入從清單中的群組名稱。
    
3. 在 [**成員資格**選取**動態的使用者**。
    
4. 按一下 [**是]**以**啟用 Office**功能。
    
5. 按一下 [**新增動態查詢**。
    
6. 在**將使用者新增其中**、 選取**部門**。
    
7. 在下一步] 欄位中，選取 [**等於**]。
    
8. 在 [下一步] 欄位中輸入從清單中的群組名稱。
    
9. 按一下 [**新增查詢**，並再按一下 [**建立**。
    
10. 按一下 [**使用者和群組-所有群組**。
    
接下來，設定群組使成員會自動指派 Office 365 E5 以及 EMS E5 授權。
  
1. 在 Azure 入口網站中，按一下 [ **Azure Active Directory > 授權 > 所有產品**。
    
2. 在清單中，選取 [**企業行動性 + 安全性 E5**和**Office 365 企業版 E5**、] 和 [ **+ 指派**。
    
3. 在**指派授權給**blade，按一下 [**使用者與群組**]。
    
4. 在群組清單中，選取下列項目：
    
  - 分析的人員
    
  - 欄位的人員
    
  - IT 人員
    
  - 作業人員
    
  - 一般核心人員
    
  - 資深和策略的人員
    
5. 按一下 [**選取**] 和 [**指派**。
    
6. 關閉瀏覽器中的 Azure 入口網站] 索引標籤。
    
## <a name="phase-3-add-your-user-accounts"></a>階段 3： 新增您的使用者帳戶

在此階段中，您將範例中的使用者帳戶新增政治的活動。
  
首先，您[使用 Azure Active Directory V2 PowerShell 模組的連線](https://go.microsoft.com/fwlink/?linkid=842218)。
  
下一步] 您填入您的組織名稱、 您位置及常見的密碼，並再從 PowerShell 命令提示字元處或整合式指令碼環境 (ISE) 中執行下列命令：
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$deptName="Senior and strategic staff"
$userNames=@("Candidate","ChiefOfStaff","Strategic1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Analytics staff"
$userNames=@("DataScientist1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Regular core staff"
$userNames=@("Regular1","Regular2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Operations staff"
$userNames=@("Operations1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Field staff"
$userNames=@("FieldConsultant1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }

```

> [!IMPORTANT]
> 自動化及簡化開發人員/測試環境是密碼的設定的使用一般。這是不建議使用實際執行訂閱。當您使用每個這些新的使用者帳戶登入，系統會提示您變更密碼。 
  
使用下列步驟以確認動態群組成員資格與群組型授權均運作正常。
  
1. 從您的瀏覽器的 [ **Microsoft Office Home** ] 索引標籤中，按一下 [**系統**] 磚。
    
2. 從 [新**Office 系統管理中心**] 索引標籤的瀏覽器中按一下 [**使用者**]。
    
3. 在使用者清單中，按一下 [**應徵者**]。
    
4. 在列出**應徵者**的使用者帳戶內容窗格中，確認：
    
  - 它是**資深和策略性人員**（中**群組的成員資格**） 群組的成員。
    
  - 已被指派**企業行動性 + 安全性 E5**和**Office 365 企業版 E5** （中的授權**產品授權**）。
    
5. 關閉 [**應徵者**使用者帳戶] 窗格中。
    
## <a name="record-values-for-future-reference"></a>以供未來參照的記錄值

記錄使用 Office 365 與 EMS 此開發/測試環境的試用版訂閱這些值：
  
- 您的試用版訂閱的組織名稱： ___ 
    
    例如，contoso.onmicrosoft.com 試用訂閱網域名稱、 組織名稱為"contoso"。
    
- Office 365 全域管理員名稱： ___.onmicrosoft.com
    
    此帳戶的密碼和其他使用者帳戶的常見初始密碼記錄在安全的位置。
    
## <a name="next-step"></a>下一步

建置[在政治 campaign 開發/測試環境中的建立小組網站](create-team-sites-in-a-political-campaign-dev-test-environment.md)與此開發/測試環境中的 SharePoint Online 小組網站的四種不同類型。
  
## <a name="see-also"></a>See Also

[Microsoft 安全性指導政治活動、 非營利機構，以及其他靈活的組織](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[政治 campaign 開發/測試環境中建立小組網站](create-team-sites-in-a-political-campaign-dev-test-environment.md)
  
[雲端採用測試實驗室指南 (Tlg)](cloud-adoption-test-lab-guides-tlgs.md)
  
[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)




