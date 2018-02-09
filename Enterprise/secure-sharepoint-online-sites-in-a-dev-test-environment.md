---
title: "安全的開發人員/測試環境中的 SharePoint Online 網站"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.custom: Strat_O365_Enterprise
ms.assetid: 06af70f3-e7dc-4ee2-a385-fb4d61a5e93b
description: "摘要： 建立公用、 私人、 機密、 和高度機密的 SharePoint Online 小組網站的開發人員/測試環境中。"
ms.openlocfilehash: 55adc5f7cdbf197acf3ca68623139c01912c602f
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="secure-sharepoint-online-sites-in-a-devtest-environment"></a>安全的開發人員/測試環境中的 SharePoint Online 網站

 **摘要：**開發/測試環境中建立公用、 私人、 機密、 和高度機密的 SharePoint Online 小組網站。
  
本文提供逐步指示以建立包含四種不同類型的[安全 SharePoint Online 網站及檔案](secure-sharepoint-online-sites-and-files.md)解決方案的 SharePoint Online 小組網站的開發人員/測試環境。
  
![安全的 SharePoint Online 開發/測試環境中的所有四個小組網站。](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
開發/測試環境用於實驗的資訊保護行為和微調您的特定需求才能部署在生產環境中的 SharePoint Online 小組網站的設定。
  
## <a name="phase-1-create-your-devtest-environment"></a>階段 1： 建立您的開發人員/測試環境

在此階段中，您可以取得試用版訂閱的 Office 365 和 Enterprise 行動性 + 安全性為虛構的組織。
  
首先，請遵循**階段 2**的[Office 365 開發人員/測試環境](office-365-dev-test-environment.md)中的指示。
  
接下來，註冊 EMS 試用訂閱並將其新增至您的 Office 365 試用版訂閱相同的組織。
  
1. 必要時，登入 Office 365 入口網站與您的試用版訂閱的全域管理員帳戶的認證。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 按一下 [**系統**] 磚。
    
3. 在**Office 系統管理中心**] 索引標籤中瀏覽器中，在左導覽列中，按一下 [**帳務 > 購買服務**。
    
4. 在 [**購買服務**] 頁面上尋找**企業行動性 + 安全性 E5**項目。滑鼠指標停留並按一下 [**開始免費試用版**。
    
5. 在 [**確認您的訂單**] 頁面上按一下 [**立即試用**。
    
6. 在 [**順序回條**] 頁面上按一下 [**繼續**]。
    
接下來，可讓企業行動性 + 全域管理員帳戶的安全性 E5 授權。
  
1. 在**Office 365 系統管理中心**] 索引標籤中瀏覽器中，在左導覽列中，按一下 [**使用者 > 作用中使用者**。
    
2. 按一下 [您的全域管理員帳戶] 和 [**編輯****產品**授權。
    
3. 在**產品授權**] 窗格中，開啟**企業行動性 + 安全性 E5** **上**至產品授權、 按一下 [**儲存]**及 [**關閉**兩次。
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups-and-users"></a>階段 2： 建立及設定您的 Azure Active Directory (AD) 群組及使用者

在此階段中，您可以建立及設定 Azure AD 群組及使用者虛構組織的。
  
首先，建立一組群組的典型組織的 Azure 入口網站。
  
1. 在瀏覽器中，建立不同的索引標籤並前往[https://portal.azure.com](https://portal.azure.com)Azure 入口網站。必要時，登入的全域管理員帳戶認證的 Office 365 E5 試用版訂閱。
    
2. 在 Azure 入口網站中，按一下 [ **Azure Active Directory > 使用者和群組 > 的所有群組**。
    
3. 在**所有群組**blade 中，按一下 [ **+ 新群組**。
    
4. 在**群組**blade 中：
    
  - 在 [**名稱**類型**C 套件**。
    
  - 選取**指派**中的**成員資格**。
    
  - 按一下 [**是]**以**啟用 Office**功能。
    
5. 按一下 [**建立**]，然後關閉 [**群組**blade。
    
6. 針對下列群組的名稱重複步驟 3-5：
    
  - IT 人員
    
  - [參考資料的人員
    
  - 一般的人員
    
  - 行銷人員
    
  - 銷售人員
    
7. 在瀏覽器開啟保留 Azure 的入口網站] 索引標籤。
    
接下來，設定自動授權，讓您群組的成員會自動指派授權 Office 365 和 EMS 訂閱。
  
1. 在 Azure 入口網站中，按一下 [ **Azure Active Directory > 授權 > 所有產品**。
    
2. 在清單中，選取 [**企業行動性 + 安全性 E5**和**Office 365 企業版 E5**、] 和 [**指派**。
    
3. 在**指派授權給**blade，按一下 [**使用者與群組**]。
    
4. 在群組清單中，選取下列項目：
    
  - C 套件
    
  - IT 人員
    
  - [參考資料的人員
    
  - 一般的人員
    
  - 行銷人員
    
  - 銷售人員
    
5. 按一下 [**選取**] 和 [**指派**。
    
6. 關閉瀏覽器中的 Azure 入口網站] 索引標籤。
    
接著，您[使用 Azure Active Directory V2 PowerShell 模組的連線](https://go.microsoft.com/fwlink/?linkid=842218)。
  
填入您的組織名稱、 您位置及常見的密碼，然後從 PowerShell 命令提示字元處或建立使用者帳戶並將它們新增至其群組的整合式指令碼環境 (ISE) 執行這些命令：
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$groupName="C-Suite"
$userNames=@("CEO","CFO","CIO") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Research staff"
$userNames=@("Researcher1") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Regular staff"
$userNames=@("Regular1", "Regular2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Marketing staff"
$userNames=@("Marketing1", "Marketing2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Sales staff"
$userNames=@("SalesPerson1") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
```

> [!NOTE]
> 自動化及簡化開發人員/測試環境是密碼的設定的使用一般。這是不建議使用實際執行訂閱。 
  
使用下列步驟以確認群組型授權正常運作正常。
  
1. 從您的瀏覽器的 [ **Microsoft Office Home** ] 索引標籤中，按一下 [**系統**] 磚。
    
2. 從 [新**Office 系統管理中心**] 索引標籤的瀏覽器中按一下 [**使用者**]。
    
3. 在使用者清單中，按一下 [**執行長**。
    
4. 在列出**CEO**使用者帳戶內容窗格中，確認它已被指派 （在**產品授權**）**企業行動性 + 安全性 E5**和**Office 365 企業版 E5**授權。
    
## <a name="phase-3-create-office-365-labels"></a>階段 3： 建立 Office 365 標籤

在此階段中，您可以建立不同的層級的 SharePoint Online 小組網站的文件資料夾的安全性的標籤。
  
1. 必要時，使用專用的網際網路瀏覽器並登入 Office 365 入口網站與您的 Office 365 E5 試用版訂閱的全域管理員帳戶。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 從**Microsoft Office Home** ] 索引標籤上，按一下 [**系統**] 磚。
    
3. 從 [新**Office 系統管理中心**] 索引標籤的瀏覽器中，按一下 [**系統中心 > 安全性&amp;規範**。
    
4. 從新**首頁-安全性&amp;規範**] 索引標籤的瀏覽器中，按一下 [**分類 > 標籤**。
    
5. 從**首頁 > 標籤**] 窗格中，按一下 [**建立] 標籤**。
    
6. 在**您標籤名稱**] 窗格中，輸入**內部公用**，然後再按 [**下一步**。
    
7. 在 [**標籤設定**] 窗格中，按一下 [**下一步**]。
    
8. 在**檢閱您的設定**] 窗格中，按一下 [**建立此標籤**] 及 [**關閉**。
    
9. 針對這些額外的標籤重複步驟 5-8：
    
  - 私人
    
  - 機密
    
  - 高度機密
    
10. 從**首頁 > 標籤**] 窗格中，按一下 [**發佈標籤**。
    
11. 在 [**選擇要發佈的標籤**] 窗格中，按一下 [**選擇標籤發佈**。
    
12. 在 [**選擇標籤**] 窗格中，按一下 [**新增**] 並選取所有的四個標籤。
    
13. 按一下 [**完成**]。
    
14. 在 [**選擇要發佈的標籤**] 窗格中，按一下 [**下一步**]。
    
15. 在 [**選擇位置**] 窗格中，按一下 [**下一步**]。
    
16. 在**您的原則名稱**] 窗格中，輸入**範例組織**在 [**名稱**] 然後再按 [**下一步**。
    
17. 在**檢閱您的設定**] 窗格中，按一下 [**發佈標籤**] 及 [**關閉**。
    
## <a name="phase-4-create-your-sharepoint-online-team-sites"></a>階段 4： 建立 SharePoint Online 小組網站

在此階段中，您可以建立及設定 SharePoint Online 小組網站的四種類型的範例組織。
  
### <a name="organization-wide-team-site"></a>組織整體小組網站

若要建立基準公用 SharePoint Online 小組網站，請執行下列動作：
  
1. 必要時，您的本機電腦上使用瀏覽器並登入 Office 365 入口網站使用全域管理員帳戶。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 在 [並排顯示] 清單中按一下 [ **SharePoint**]。
    
3. 在 [新增**SharePoint** ] 索引標籤在瀏覽器中按一下 [ **+ 建立網站**。
    
4. 在 [**建立網站**] 頁面上，按一下 [**小組網站**。
    
5. 在**站台名稱**] 中輸入**整個組織**。 
    
6. 在**小組網站描述**] 中，輸入**SharePoint 網站的整個組織**。
    
7. **隱私權設定**] 中選取**公用位在組織中的任何人都可以存取此站台**，並再按 [**下一步**。
    
8. 在**您要新增誰？** ] 窗格中，按一下 [**完成]**。
    
接下來，設定組織整體小組網站內部公用標籤的 [文件] 資料夾。
  
1. 在瀏覽器的**組織整體首頁**] 索引標籤中按一下 [**文件**]。
    
2. 按一下 [設定] 圖示，並再按一下 [**文件庫設定**]。
    
3. 在 [**權限與管理**] 按一下 [**套用此文件庫中的項目標籤**。
    
4. 在**套用設定的標籤**、 選取 [**內部公用**、] 和 [**儲存**。
    
以下是您產生的組態。
  
![用於整個組織之公用 SharePoint Online 小組網站的基準層級保護。](images/25c86847-a38d-49ad-bb5f-c7c04206b6dc.png)
  
### <a name="project-1-team-site"></a>專案 1 小組網站

若要建立基準私人 SharePoint Online 小組網站組織內的專案，請執行下列動作：
  
1. 必要時，您的本機電腦上使用瀏覽器並登入 Office 365 入口網站使用全域管理員帳戶。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 在 [並排顯示] 清單中按一下 [ **SharePoint**]。
    
3. 在 [新增**SharePoint** ] 索引標籤在瀏覽器中按一下 [ **+ 建立網站**。
    
4. 在 [**建立網站**] 頁面上，按一下 [**小組網站**。
    
5. 在**站台名稱**] 中輸入**專案 1**。 
    
6. 在**小組網站描述] 中，**輸入**SharePoint 網站的專案 1**。
    
7. **隱私權設定**] 中選取 [**私人-只有成員可以存取此站台**，然後按一下 [**下一步**。
    
8. 在**您要新增誰？** ] 窗格中，按一下 [**完成]**。
    
接下來，設定專案 1 小組網站私人標籤的 [文件] 資料夾。
  
1. **專案 1 首頁**] 索引標籤中的瀏覽器中，按一下 [**文件**]。
    
2. 按一下 [設定] 圖示，並再按一下 [**文件庫設定**]。
    
3. 在 [**權限與管理**] 按一下 [**套用此文件庫中的項目標籤**。
    
4. 在**套用設定的標籤**、 選取 [**私人**] 和 [**儲存**。
    
以下是您產生的組態。
  
![用於 Project1 私人 SharePoint Online 小組網站的基準層級保護。](images/ecd96376-b5dc-4042-9cbd-b3765507ace7.png)
  
### <a name="marketing-campaigns-team-site"></a>行銷活動小組網站

若要建立機密層級隔離的 SharePoint Online 小組網站行銷活動全方位的資源，執行下列動作：
  
1. 本機電腦上使用瀏覽器，登入 Office 365 入口網站使用全域管理員帳戶。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 在 [並排顯示] 清單中按一下 [ **SharePoint**]。
    
3. 在 [新增**SharePoint** ] 索引標籤在瀏覽器中按一下 [ **+ 建立網站**。
    
4. 在 [**建立網站**] 頁面上，按一下 [**小組網站**。
    
5. 在**小組網站名稱**] 中輸入**行銷活動**。
    
6. 在**小組網站描述**] 中，輸入**SharePoint 網站的行銷活動全方位資源 （機密）**。
    
7.  **隱私權設定**] 中選取 [**私人-只有成員可以存取此站台**，然後按一下 [**下一步**。
    
8. 在**您要新增誰？** ] 窗格中，按一下 [**完成]**。
    
9. 在瀏覽器中的 [工具] 列中新的**行銷活動**] 索引標籤上按一下 [設定] 圖示，和 [**網站權限**。
    
10. 在 [**網站權限**] 窗格中，按一下 [**進階權限設定**。
    
11. 在 [新**的權限**] 索引標籤在瀏覽器中按一下 [**存取要求的設定**。
    
12. 在 [**存取要求設定**] 對話方塊中，清除**允許成員] 共用網站和個別的檔案及資料夾**並**邀請其他人的網站成員群組允許成員**] 核取方塊中，輸入**ITAdmin1 @**\<您組織名稱 >**。 onmicrosoft.com**中**傳送所有要求存取**]，然後按一下 [**確定]**。
    
13. 按一下清單中的**行銷活動成員**。
    
14. 在 [**人員與群組**] 頁面上按一下 [**新增**]。
    
15. 在 [**共用**] 對話方塊中，輸入**行銷人員**、 選取它，，然後按一下 [**共用**。
    
16. 重複步驟 14 與 15 **Researcher1**使用者帳戶。
    
17. 按一下瀏覽器上的 [上一頁] 按鈕。
    
18. 按一下 [**行銷活動擁有者**] 清單中。
    
19. 在 [**人員與群組**] 頁面上按一下 [**新增**]。
    
20. 在 [**共用**] 對話方塊中，輸入**IT 人員**、 選取它，，然後按一下 [**共用**]。
    
21. 按一下瀏覽器上的 [上一頁] 按鈕。
    
22. 關閉瀏覽器中的 [**人員與群組**] 索引標籤、 [瀏覽器中的 [**行銷活動首頁**] 索引標籤，然後關閉 [**網站權限**] 窗格。
    
設定權限的結果如下︰
  
- **行銷活動成員**SharePoint 群組包含只**行銷活動**群組 （其中包含全域管理員使用者帳戶）、**行銷人員**群組 （其中包含 [Marketing1 及 Marketing2 使用者帳戶） 及**Researcher1**的使用者帳戶。
    
- **行銷活動擁有者**SharePoint 群組包含只**IT 人員**群組 （其中包含只 ITAdmin1 與 ITAdmin2 使用者帳戶）。
    
- **行銷活動訪客**SharePoint 群組沒有包含群組或使用者帳戶。
    
- 成員無法修改站台層級權限 （這可以只來完成**行銷活動擁有人**群組的成員）。
    
- 其他使用者帳戶無法存取之網站或其資源，但可以要求網站，會將電子郵件傳送至 ITAdmin1 使用者帳戶信箱的存取權。
    
接下來，設定行銷活動小組網站機密標籤的 [文件] 資料夾。
  
1. **行銷活動首頁**] 索引標籤中的瀏覽器中，按一下 [**文件**]。
    
2. 按一下 [設定] 圖示，並再按一下 [**文件庫設定**]。
    
3. 在 [**權限與管理**] 按一下 [**套用此文件庫中的項目標籤**。
    
4. 在**套用設定的標籤**、 選取**機密**、] 和 [**儲存**。
    
下一步] 設定時階級機密標籤，其中包含組織外的行銷活動網站與 SharePoint Online 小組網站上的文件會通知使用者資料外洩防護 (DLP) 原則。
  
1. 從您的瀏覽器的 [ **Microsoft Office Home** ] 索引標籤按一下 [**安全性&amp;規範**並排顯示。
    
2. 在新**安全性&amp;規範**在瀏覽器] 索引標籤中按一下 [**資料遺失防護 > 原則**。
    
3. 在 [**資料外洩防護**] 窗格中，按一下 [ **+ 建立原則**。
    
4. 在**開始使用範本建立自訂原則或**] 窗格中，按一下**自訂**，然後再按一下 [**下一步**。
    
5. 在**您的原則名稱**] 窗格中，輸入**機密標籤 SharePoint Online 小組網站**在 [**名稱**]，然後按 [**下一步**。
    
6. 中**選擇位置**] 窗格中，按一下 [**讓我選擇特定位置**] 和 [**下一步**。
    
7. 在清單中的位置，停用的**Exchange 電子郵件**和**OneDrive 帳戶**的位置，並再按 [**下一步**。
    
8. 在**自訂您想要保護敏感資訊類型**] 窗格中，按一下 [**編輯**]。
    
9. 在 [**選擇要保護的內容類型**] 窗格中，按一下 [**新增**] 的下拉式方塊中，和 [**標籤**。
    
10. [**標籤**] 窗格中按一下 [ **+ 新增**、 選取**機密**標籤、 按一下 [**新增**] 和 [**完成**。
    
11. 在 [**選擇要保護的內容類型**] 窗格中，按一下 [**儲存**]。
    
12. 在**自訂您想要保護敏感資訊類型**] 窗格中，按一下 [**下一步**]。
    
13. 在**您想要如果我們偵測敏感資訊吗？** ] 窗格中，按一下 [**自訂提示] 及 [電子郵件**。
    
14. 在**自訂原則提示及電子郵件通知**] 窗格中，按一下 [**自訂原則提示文字**。
    
15. [文字] 方塊中輸入或貼上下列：
    
  - 與組織外部使用者共用，下載檔案，然後開啟它。按一下 [檔案]，然後保護文件，並使用密碼，然後加密，然後指定強式密碼。以不同的電子郵件或其他通訊的方式傳送密碼。
    
16. 按一下 [確定]****。
    
17. 在**您想要如果我們偵測敏感資訊吗？** ] 窗格中，清除**封鎖來自共用、 人員及限制共用內容的存取權**] 核取方塊，然後再按一下 [**下一步**。
    
18. 在**您要開啟 [先取出的原則或測試事項？** ] 窗格中，按一下**[是]，開啟立即**，並再按 [**下一步**。
    
19. 在**檢閱您的設定**] 窗格中，按一下 [**建立**] 和 [**關閉**。
    
以下是您產生的組態。
  
![用於行銷活動隔離之 SharePoint Online 小組網站的敏感性層級保護。](images/33992bd5-96ee-4bfb-9ecf-c8a6736dd100.png)
  
### <a name="company-strategy-team-site"></a>公司策略小組網站

若要建立隔離的 SharePoint Online 小組網站的組織的首席高階主管的策略性公司資源之高度機密層級，執行下列動作：
  
1. 必要時，您的本機電腦上使用瀏覽器並登入 Office 365 入口網站使用全域管理員帳戶。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 在 [並排顯示] 清單中按一下 [ **SharePoint**]。
    
3. 在 [新增**SharePoint** ] 索引標籤在瀏覽器中按一下 [ **+ 建立網站**。
    
4. 在 [**建立網站**] 頁面上，按一下 [**小組網站**。
    
5. 在**小組網站名稱**] 中輸入**公司策略**。
    
6. 在**小組網站描述**] 中，輸入**SharePoint 網站的公司策略 （高度機密）**。
    
7.  **隱私權設定**] 中選取 [**私人-只有成員可以存取此站台**，然後按一下 [**下一步**。
    
8. 在**您要新增誰？** ] 窗格中，按一下 [**完成]**。
    
9. 在瀏覽器中的 [工具] 列中新的**公司策略**] 索引標籤上按一下 [設定] 圖示，和 [**網站權限**。
    
10. 在 [**網站權限**] 窗格中，按一下 [**進階權限設定**。
    
11. 在 [新**的權限**] 索引標籤在瀏覽器中按一下 [**存取要求的設定**。
    
12. **存取要求設定**] 對話方塊中，清除 [**允許成員] 共用網站和個別的檔案及資料夾**並**允許邀請其他人網站成員 」 群組的成員**（使已取消選取所有的三個核取方塊），然後按一下 [ **確定**。
    
13. 清單中的 [**公司策略成員**。
    
14. 在 [**人員與群組**] 頁面上按一下 [**新增**]。
    
15. 在 [**共用**] 對話方塊中，輸入**C 套件**、 選取它，，然後按一下 [**共用**]。
    
16. 按一下 [**公司策略擁有者**] 清單中。
    
17. 在 [**人員與群組**] 頁面上按一下 [**新增**]。
    
18. 在 [**共用**] 對話方塊中，輸入**IT 人員**、 選取它，，然後按一下 [**共用**]。
    
19. 按一下瀏覽器上的 [上一頁] 按鈕。
    
20. 關閉瀏覽器上的 [**人員與群組**] 索引標籤按一下 [瀏覽器上的 [**公司策略首頁**] 索引標籤，然後關閉 [**網站權限**] 窗格。
    
設定權限的結果如下︰
  
- **公司策略成員**SharePoint 群組包含只**C 套件**群組 （其中包含只 CEO、 CFO、 及 CIO 使用者帳戶） 和**公司策略**群組 （其中包含只有一個全域管理員使用者帳戶）。
    
- **公司策略擁有者**SharePoint 群組包含只**IT 人員**群組 （其中包含只 ITAdmin1 與 ITAdmin2 使用者帳戶）。
    
- **公司策略訪客**SharePoint 群組沒有包含群組或使用者帳戶。
    
- 成員無法修改站台層級權限 （這可以只來完成**公司策略擁有人**群組的成員）。
    
- 其他使用者帳戶無法存取之網站或其資源的更新或要求網站的存取權。全域管理員或**公司策略擁有者**群組的成員必須完成網站的其他權限。
    
接下來，設定高度機密標籤公司策略小組網站的 [文件] 資料夾。
  
1. 在瀏覽器的**公司策略首頁**] 索引標籤中按一下 [**文件**]。
    
2. 按一下 [設定] 圖示，並再按一下 [**文件庫設定**]。
    
3. 在 [**權限與管理**] 按一下 [**套用此文件庫中的項目標籤**。
    
4. 在**套用設定的標籤**、 選取**高度機密**、] 和 [**儲存**。
    
接下來，設定 DLP 原則，封鎖使用者時階級具有高度機密標籤，其中包含組織外的公司策略網站 SharePoint Online 小組網站上的文件。
  
1. 必要時，您的本機電腦上使用瀏覽器並登入 Office 365 入口網站與有安全性管理員或公司管理員角色的帳戶。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 從您的瀏覽器的 [ **Microsoft Office Home** ] 索引標籤按一下 [**安全性&amp;規範**並排顯示。
    
3. 在新**安全性&amp;規範**在瀏覽器] 索引標籤中按一下 [**資料遺失防護 > 原則**。
    
4. 在 [**資料外洩防護**] 窗格中，按一下 [ **+ 建立原則**。
    
5. 在**開始使用範本建立自訂原則或**] 窗格中，按一下**自訂**，然後再按一下 [**下一步**。
    
6. 在**您的原則名稱**] 窗格中，輸入**高度機密標籤 SharePoint Online 小組網站**在 [**名稱**]，然後按 [**下一步**。
    
7. 中**選擇位置**] 窗格中，按一下 [**讓我選擇特定位置**] 和 [**下一步**。
    
8. 在清單中的位置，停用的**Exchange 電子郵件**和**OneDrive 帳戶**的位置，並再按 [**下一步**。
    
9. 在**自訂您想要保護敏感資訊類型**] 窗格中，按一下 [**編輯**]。
    
10. 在 [**選擇要保護的內容類型**] 窗格中，按一下 [**新增**] 的下拉式方塊中，和 [**標籤**。
    
11. [**標籤**] 窗格中按一下 [ **+ 新增**、 選取**高度機密**的標籤、 按一下 [**新增**] 和 [**完成**。
    
12. 在 [**選擇要保護的內容類型**] 窗格中，按一下 [**儲存**]。
    
13. 在**自訂您想要保護敏感資訊類型**] 窗格中，按一下 [**下一步**]。
    
14. 在**您想要如果我們偵測敏感資訊吗？** ] 窗格中，按一下 [**自訂提示] 及 [電子郵件**。
    
15. 在**自訂原則提示及電子郵件通知**] 窗格中，按一下 [**自訂原則提示文字**。
    
16. [文字] 方塊中輸入或貼上下列：
    
  - 與組織外部使用者共用，下載檔案，然後開啟它。按一下 [檔案]，然後保護文件，並使用密碼，然後加密，然後指定強式密碼。以不同的電子郵件或其他通訊的方式傳送密碼。
    
17. 按一下 [確定]****。
    
18. 在**您想要如果我們偵測敏感資訊吗？** ] 窗格中，選取**需要覆寫業務上理由**，然後再按一下 [**下一步**。
    
19. 在**您要開啟 [先取出的原則或測試事項？** ] 窗格中，按一下**[是]，開啟立即**，並再按 [**下一步**。
    
20. 在**檢閱您的設定**] 窗格中，按一下 [**建立**] 和 [**關閉**。
    
接下來，遵循[與 Office 365 系統管理中心啟動 Azure RMS](https://docs.microsoft.com/information-protection/deploy-use/activate-office365)中的指示。
  
接下來，設定 Azure 資訊保護與新範圍的原則和子標籤保護和權限的下列步驟：
  
1. Office 365 入口網站與有安全性管理員或公司管理員角色的帳戶登入。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 在瀏覽器中的個別] 索引標籤移至 Azure 入口網站 ([https://portal.azure.com](https://portal.azure.com))。
    
3. 如果這是您要設定 Azure 資訊保護第一次，請參閱這些[指示](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time)。
    
4. 在 [清單] 窗格中，按一下 [**更多的服務**、 輸入**資訊**，和 [ **Azure 資訊保護**。
    
5. **Azure 資訊保護**blade、 上，按一下 [**範圍設定的原則 > + 新增原則**。
    
6. 輸入**CompanyStrategy** [**原則名稱**] 及 [**標籤公司策略小組網站中的文件**中**描述**。
    
7. 按一下 [**選取哪些使用者或群組取得此原則 > 使用者/群組**，然後選取 [ **C 套件**。
    
8. 按一下 [**選取 > [確定]**。
    
9. **高度機密**標籤中，按一下省略符號 （...）] 和 [**新增子標籤**。
    
10. 輸入**名稱**與**描述**標籤的描述的子標籤名稱。
    
11. 在**設定文件及包含此標籤的電子郵件的權限**，請按一下 [**保護**]。
    
12. 在 [**保護**] 區段中，按一下 [ **Azure （雲端索引鍵）**。
    
13. 在**保護**blade，**保護設定**] 下按一下 [ **+ 新增權限**。
    
14. 在**新增權限**blade 中，**指定使用者與群組**] 下按一下 [ **+ 瀏覽目錄]**。
    
15. 在**AAD 使用者與群組**] 窗格中，選取**C 套件**，然後再按一下 [**選取**。
    
16. 在**預設選擇權限**] 下方清除**列印**、**複製及擷取內容**以及**轉寄**] 核取方塊。
    
17. 按兩次 [**確定]** 。
    
18. 在**子標籤**blade 中，按一下 [**儲存**]。
    
19. 關閉新範圍的原則 blade。
    
20. 在**Azure 資訊保護-範圍的原則**blade 中，按一下 [**發佈**] 及 [ **[是]**。
    
若要保護與 Azure 資訊保護及這個新的標籤文件，您必須在測試電腦上的 [[安裝 Azure 資訊保護用戶端](https://docs.microsoft.com/information-protection/rms-client/install-client-app)、 從 Office 365 入口網站安裝 Office 並再登入從 Microsoft Word 中**帳戶C 套件**您試用版訂閱的群組。
  
以下是您產生的組態。
  
![用於公司策略隔離之 SharePoint Online 小組網站的高度機密層級保護。](images/c22695f9-50a1-4abf-a0dd-344b0c92cf94.png)
  
您現在可以開始建立下列四個網站中的文件並測試您的試用版訂閱具有不同的使用者帳戶給他們的存取權。
  
以下是所有的四個 SharePoint Online 小組網站的整體設定。
  
![安全的 SharePoint Online 開發/測試環境中的所有四個小組網站。](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
## <a name="next-step"></a>下一步

當您準備好實際執行部署的安全的 SharePoint Online 網站時，請參閱[安全 SharePoint Online 網站及檔案](secure-sharepoint-online-sites-and-files.md)的詳細的資訊以及逐步說明的部署文章的連結。
  
## <a name="see-also"></a>請參閱

[安全的 SharePoint Online 網站及檔案](secure-sharepoint-online-sites-and-files.md)
  
[安全性解決方案](security-solutions.md)
  
[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)
  
[Microsoft 安全性指導政治活動、 非營利機構，以及其他靈活的組織](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)




