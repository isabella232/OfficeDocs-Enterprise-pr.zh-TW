---
title: 在開發/測試環境中保護 SharePoint Online 網站
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/14/2018
ms.audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
ms.custom: ''
ms.assetid: 06af70f3-e7dc-4ee2-a385-fb4d61a5e93b
description: 摘要： 建立公用、 私人、 機密、 和高度機密的 SharePoint Online 小組網站的開發人員/測試環境中。
ms.openlocfilehash: 004a1614330f220b31be640cd822d9fdcbb49b99
ms.sourcegitcommit: 29c8571ca4912549bac55ec9d1642d21eba5b0e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2018
---
# <a name="secure-sharepoint-online-sites-in-a-devtest-environment"></a>在開發/測試環境中保護 SharePoint Online 網站

 **摘要：** 開發/測試環境中建立公用、 私人、 機密、 和高度機密的 SharePoint Online 小組網站。
  
本文提供逐步指示以建立包含四種不同類型的[安全 SharePoint Online 網站及檔案](secure-sharepoint-online-sites-and-files.md)解決方案的 SharePoint Online 小組網站的開發人員/測試環境。
  
![安全的 SharePoint Online 開發/測試環境中的所有四個小組網站。](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
您可以先使用此開發/測試環境，來試驗資訊保護行為，並針對特定需求微調設定，然後再將 SharePoint Online 小組網站部署在生產環境中。
  
## <a name="phase-1-create-your-devtest-environment"></a>階段 1：建立開發/測試環境

在這個階段中，您會為虛構組織取得 Office 365 與 Enterprise Mobility + Security 試用訂閱。
  
首先，請遵循 [Office 365 開發/測試環境](office-365-dev-test-environment.md)的**階段 2** 中的指示進行。
  
接下來，註冊 EMS 試用訂閱並將其新增至您的 Office 365 試用版訂閱相同的組織。
  
1. 必要時，登入 Office 365 入口網站與您的試用版訂閱的全域管理員帳戶的認證。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 按一下 [管理] 磚。
    
3. 在瀏覽器的 [Office 系統管理中心] 索引標籤上，按一下左導覽中的 [計費] > [購買服務]。
    
4. 在 [**購買服務**] 頁面上尋找**企業行動性 + 安全性 E5**項目。滑鼠指標停留並按一下 [**開始免費試用版**。
    
5. 在 [**確認您的訂單**] 頁面上按一下 [**立即試用**。
    
6. 在 [訂單收據] 頁面上，按一下 [繼續]。
    
接下來，啟用全域管理員帳戶的 Enterprise Mobility + Security E5 授權。
  
1. 在瀏覽器的 [Office 365 系統管理中心] 索引標籤上，按一下左導覽中的 [使用者] > [作用中使用者]。
    
2. 按一下 [您的全域管理員帳戶] 和 [**編輯****產品**授權。
    
3. 在**產品授權**] 窗格中，開啟**企業行動性 + 安全性 E5** **上**至產品授權、 按一下 [**儲存]** 及 [**關閉**兩次。
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups-and-users"></a>階段 2：建立和設定 Azure Active Directory (AD) 群組和使用者

在這個階段中，您會為虛構組織建立和設定 Azure AD 群組和使用者。
  
首先，利用 Azure 入口網站建立一組典型組織的群組。
  
1. 在瀏覽器中，建立不同的索引標籤並前往 Azure 入口網站[https://portal.azure.com](https://portal.azure.com)。必要時，登入的全域管理員帳戶認證的 Office 365 E5 試用版訂閱。
    
2. 在 Azure 入口網站中，按一下 [ **Azure Active Directory > 群組**。
    
3. 在**群組-所有群組**blade 中，按一下 [ **+ 新群組**。
    
4. 在 [群組] 刀鋒視窗中：
    
  - 選取**Office 365**中的**群組類型**。
    
  - 在 [**名稱**類型**C 套件**。
    
  - 在 [**成員資格類型**選取**已指派]** 。
      
5. 按一下 [建立]，然後關閉 [群組] 刀鋒視窗。
    
6. 重複步驟 3-5，逐一設定下列群組名稱：
    
  - IT 人員
    
  - 研究人員
    
  - 一般人員
    
  - 行銷人員
    
  - 銷售人員
    
7. 請將瀏覽器中的 [Azure 入口網站] 索引標籤保持開啟。
    
接下來，設定自動授權，讓您群組的成員會自動指派授權 Office 365 和 EMS 訂閱。
  
1. 在 Azure 入口網站中，按一下 [Azure Active Directory] > [授權] > [所有產品]。
    
2. 在清單中，選取 [**企業行動性 + 安全性 E5**和**Office 365 企業版 E5**、] 和 [**指派**。
    
3. 在 [指派授權] 刀鋒視窗中，按一下 [使用者和群組]。
    
4. 在群組清單中，選取下列項目：
    
  - 高層主管
    
  - IT 人員
    
  - 研究人員
    
  - 一般人員
    
  - 行銷人員
    
  - 銷售人員
    
5. 按一下 [**選取**] 和 [**指派**。
    
6. 關閉瀏覽器的 Azure 入口網站索引標籤。
    
接著，[與 Azure Active Directory V2 PowerShell 模組連線](https://go.microsoft.com/fwlink/?linkid=842218)。
  
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
> 這裡會使用常見密碼，以便在開發/測試環境中能自動化並輕鬆進行設定。 這不建議用於實際執行的訂閱。 
  
使用下列步驟以確認群組型授權正常運作正常。
  
1. 從瀏覽器的 [Microsoft Office 的首頁] 索引標籤中，按一下 [管理] 磚。
    
2. 從瀏覽器的新 [Office 系統管理中心] 索引標籤中，按一下 [使用者]。
    
3. 在使用者清單中，按一下 [CEO]。
    
4. 在列出**CEO**使用者帳戶內容窗格中，確認它已被指派 （在**產品授權**）**企業行動性 + 安全性 E5**和**Office 365 企業版 E5**授權。
    
## <a name="phase-3-create-office-365-labels"></a>階段 3：建立 Office 365 標籤

在這個階段中，您會為 SharePoint Online 小組網站的文件資料夾，建立不同安全性層級的標籤。
  
1. 必要時，使用專用的網際網路瀏覽器並登入 Office 365 入口網站與您的 Office 365 E5 試用版訂閱的全域管理員帳戶。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 從 [Microsoft Office 的首頁] 索引標籤中，按一下 [管理] 磚。
    
3. 從 [新**Office 系統管理中心**] 索引標籤的瀏覽器中，按一下 [**系統中心 > 安全性&amp;規範**。
    
4. 從新**首頁-安全性&amp;規範**] 索引標籤的瀏覽器中，按一下 [**分類 > 標籤**。
    
5. 從 [首頁] > [標籤] 窗格中，按一下 [建立標籤]。
    
6. 在**您標籤名稱**] 窗格中，輸入**內部公用**，然後再按 [**下一步**。
    
7. 在 [**標籤設定**] 窗格中，按一下 [**下一步**]。
    
8. 在**檢閱您的設定**] 窗格中，按一下 [**建立此標籤**] 及 [**關閉**。
    
9. 重複步驟 5-8，逐一設定下列其他標籤：
    
  - Private
    
  - 敏感性
    
  - 高度機密
    
10. 從**首頁 > 標籤**] 窗格中，按一下 [**發佈標籤**。
    
11. 在 [**選擇要發佈的標籤**] 窗格中，按一下 [**選擇標籤發佈**。
    
12. 在 [**選擇標籤**] 窗格中，按一下 [**新增**] 並選取所有的四個標籤。
    
13. 按一下 [完成]。
    
14. 在 [**選擇要發佈的標籤**] 窗格中，按一下 [**下一步**]。
    
15. 在 [**選擇位置**] 窗格中，按一下 [**下一步**]。
    
16. 在**您的原則名稱**] 窗格中，輸入**範例組織**在 [**名稱**] 然後再按 [**下一步**。
    
17. 在**檢閱您的設定**] 窗格中，按一下 [**發佈標籤**] 及 [**關閉**。
    
## <a name="phase-4-create-your-sharepoint-online-team-sites"></a>階段 4：建立 SharePoint Online 小組網站

在這個階段中，您會為範例組織建立和設定四種類型的 SharePoint Online 小組網站。
  
### <a name="organization-wide-team-site"></a>整個組織的小組網站

若要建立公用的基準 SharePoint Online 小組網站，請執行下列作業：
  
1. 如果需要，請使用本機電腦上的瀏覽器，並使用全域管理員帳戶登入 Office 365 入口網站。 如需說明，請參閱[在何處登入 Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 在磚清單中，按一下 [SharePoint]。
    
3. 在瀏覽器的新 [SharePoint] 索引標籤上，按一下 [+ 建立網站]。
    
4. 在 [建立網站] 頁面上，按一下 [小組網站]。
    
5. 在 [網站名稱] 中，鍵入「整個組織」。 
    
6. 在 [小組網站描述] 中，鍵入「整個組織的 SharePoint 網站」。
    
7. **隱私權設定**] 中選取**公用位在組織中的任何人都可以存取此站台**，並再按 [**下一步**。
    
8. 在 [您想要新增誰?] 窗格中，按一下 [完成]。
    
接下來，設定組織整體小組網站內部公用標籤的 [文件] 資料夾。
  
1. 在瀏覽器的**組織整體首頁**] 索引標籤中按一下 [**文件**]。
    
2. 按一下設定圖示，然後按一下 [文件庫設定]。
    
3. 在 [**權限與管理**] 按一下 [**套用此文件庫中的項目標籤**。
    
4. 在**套用設定的標籤**、 選取 [**內部公用**、] 和 [**儲存**。
    
以下是您產生的組態。
  
![用於整個組織之公用 SharePoint Online 小組網站的基準層級保護。](images/25c86847-a38d-49ad-bb5f-c7c04206b6dc.png)
  
### <a name="project-1-team-site"></a>專案 1 小組網站

若要為組織內部的專案建立私用的基準 SharePoint Online 小組網站，請執行下列作業：
  
1. 如果需要，請使用本機電腦上的瀏覽器，並使用全域管理員帳戶登入 Office 365 入口網站。 如需說明，請參閱[在何處登入 Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 在磚清單中，按一下 [SharePoint]。
    
3. 在瀏覽器的新 [SharePoint] 索引標籤上，按一下 [+ 建立網站]。
    
4. 在 [建立網站] 頁面上，按一下 [小組網站]。
    
5. 在 [網站名稱] 中，鍵入「專案 1」。 
    
6. 在**小組網站描述] 中，** 輸入**SharePoint 網站的專案 1**。
    
7. **隱私權設定**] 中選取 [**私人-只有成員可以存取此站台**，然後按一下 [**下一步**。
    
8. 在 [您想要新增誰?] 窗格中，按一下 [完成]。
    
接下來，為「專案 1」小組網站的文件資料夾設定「私用」標籤。
  
1. 在瀏覽器的 [Project 1-Home (專案 1 - 首頁)] 索引標籤中，按一下 [文件]。
    
2. 按一下設定圖示，然後按一下 [文件庫設定]。
    
3. 在 [**權限與管理**] 按一下 [**套用此文件庫中的項目標籤**。
    
4. 在**套用設定的標籤**、 選取 [**私人**] 和 [**儲存**。
    
以下是您產生的組態。
  
![用於 Project1 私人 SharePoint Online 小組網站的基準層級保護。](images/ecd96376-b5dc-4042-9cbd-b3765507ace7.png)
  
### <a name="marketing-campaigns-team-site"></a>行銷活動小組網站

若要為行銷活動資源，建立敏感性層級的隔離 SharePoint Online 小組網站，請執行下列作業：
  
1. 本機電腦上使用瀏覽器，登入 Office 365 入口網站使用全域管理員帳戶。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 在磚清單中，按一下 [SharePoint]。
    
3. 在瀏覽器的新 [SharePoint] 索引標籤上，按一下 [+ 建立網站]。
    
4. 在 [建立網站] 頁面上，按一下 [小組網站]。
    
5. 在 [小組網站名稱] 中，鍵入「行銷活動」。
    
6. 在 [小組網站描述] 中，鍵入「行銷活動的 SharePoint 網站 (敏感性)」。
    
7.  **隱私權設定**] 中選取 [**私人-只有成員可以存取此站台**，然後按一下 [**下一步**。
    
8. 在 [您想要新增誰?] 窗格中，按一下 [完成]。
    
9. 在瀏覽器中的 [工具] 列中新的**行銷活動**] 索引標籤上按一下 [設定] 圖示，和 [**網站權限**。
    
10. 在 [網站權限] 窗格中，按一下 [進階權限設定]。
    
11. 在瀏覽器的新 [權限] 索引標籤中，按一下 [存取要求設定]。
    
12. 在 [**存取要求設定**] 對話方塊中，清除**允許成員] 共用網站和個別的檔案及資料夾**並**邀請其他人的網站成員群組允許成員**] 核取方塊中，輸入**ITAdmin1 @**\<您組織名稱 >**。 onmicrosoft.com**中**傳送所有要求存取**]，然後按一下 [**確定]**。
    
13. 按一下清單中的 [Marketing campaigns Members (行銷活動成員)]。
    
14. 在 [人員與群組] 頁面上，按一下 [新增]。
    
15. 在 [**共用**] 對話方塊中，輸入**行銷人員**、 選取它，，然後按一下 [**共用**。
    
16. 重複步驟 14 與 15 **Researcher1**使用者帳戶。
    
17. 按一下瀏覽器上的 [上一頁] 按鈕。
    
18. 按一下 [**行銷活動擁有者**] 清單中。
    
19. 在 [人員與群組] 頁面上，按一下 [新增]。
    
20. 在 [**共用**] 對話方塊中，輸入**IT 人員**、 選取它，，然後按一下 [**共用**]。
    
21. 按一下瀏覽器上的 [上一頁] 按鈕。
    
22. 關閉瀏覽器中的 [**人員與群組**] 索引標籤、 [瀏覽器中的 [**行銷活動首頁**] 索引標籤，然後關閉 [**網站權限**] 窗格。
    
以下是設定權限的結果：
  
- **行銷活動成員**SharePoint 群組包含只**行銷活動**群組 （其中包含全域管理員使用者帳戶）、**行銷人員**群組 （其中包含 [Marketing1 及 Marketing2 使用者帳戶） 及**Researcher1**的使用者帳戶。
    
- 「行銷活動 - 擁有者」的 SharePoint 群組僅包含「IT 人員」群組 (其中僅包含 ITAdmin1 和 ITAdmin2 使用者帳戶)。
    
- 「行銷活動 - 訪客」的 SharePoint 群組未包含任何群組或使用者帳戶。
    
- 成員無法修改網站層級的權限 (這只能由「行銷活動 - 擁有者」群組成員來執行)。
    
- 其他使用者帳戶無法存取之網站或其資源，但可以要求網站，會將電子郵件傳送至 ITAdmin1 使用者帳戶信箱的存取權。
    
接下來，為「行銷活動」小組網站的文件資料夾設定「敏感性」標籤。
  
1. 在瀏覽器的 [Marketing campaigns-Home (行銷活動 - 首頁)] 索引標籤中，按一下 [文件]。
    
2. 按一下設定圖示，然後按一下 [文件庫設定]。
    
3. 在 [**權限與管理**] 按一下 [**套用此文件庫中的項目標籤**。
    
4. 在**套用設定的標籤**、 選取**機密**、] 和 [**儲存**。
    
接下來，設定資料外洩防護 (DLP) 原則；當使用者在組織外部共用具「敏感性」標籤之 SharePoint Online 小組網站 (包含「行銷活動」網站) 上的文件時，即會通知使用者。
  
1. 從您的瀏覽器的 [ **Microsoft Office Home** ] 索引標籤按一下 [**安全性&amp;規範**並排顯示。
    
2. 在新**安全性&amp;規範**在瀏覽器] 索引標籤中按一下 [**資料遺失防護 > 原則**。
    
3. 在 [資料外洩防護] 窗格中，按一下 [+ 建立原則]。
    
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
    
15. 在文字方塊中，鍵入或貼上下列內容：
    
  - 若要與組織外部的使用者共用，請下載檔案，然後將它開啟。 依序按一下 [檔案]、[保護文件] 和 [以密碼加密]，然後指定強式密碼。 以個別電子郵件或其他通訊方式傳送密碼。
    
16. 按一下 [確定]****。
    
17. 在**您想要如果我們偵測敏感資訊吗？** ] 窗格中，清除**封鎖來自共用、 人員及限制共用內容的存取權**] 核取方塊，然後再按一下 [**下一步**。
    
18. 在**您要開啟 [先取出的原則或測試事項？** ] 窗格中，按一下 **[是]，開啟立即**，並再按 [**下一步**。
    
19. 在**檢閱您的設定**] 窗格中，按一下 [**建立**] 和 [**關閉**。
    
以下是您產生的組態。
  
![用於行銷活動隔離之 SharePoint Online 小組網站的敏感性層級保護。](images/33992bd5-96ee-4bfb-9ecf-c8a6736dd100.png)
  
### <a name="company-strategy-team-site"></a>公司策略小組網站

若要為組織執行長的公司策略資源，建立高度機密層級的隔離 SharePoint Online 小組網站，請執行下列作業：
  
1. 如果需要，請使用本機電腦上的瀏覽器，並使用全域管理員帳戶登入 Office 365 入口網站。 如需說明，請參閱[在何處登入 Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 在磚清單中，按一下 [SharePoint]。
    
3. 在瀏覽器的新 [SharePoint] 索引標籤上，按一下 [+ 建立網站]。
    
4. 在 [建立網站] 頁面上，按一下 [小組網站]。
    
5. 在 [小組網站名稱] 中，鍵入「公司策略」。
    
6. 在 [小組網站描述] 中，鍵入「公司策略的 SharePoint 網站 (高度機密)」。
    
7.  **隱私權設定**] 中選取 [**私人-只有成員可以存取此站台**，然後按一下 [**下一步**。
    
8. 在 [您想要新增誰?] 窗格中，按一下 [完成]。
    
9. 在瀏覽器中的 [工具] 列中新的**公司策略**] 索引標籤上按一下 [設定] 圖示，和 [**網站權限**。
    
10. 在 [網站權限] 窗格中，按一下 [進階權限設定]。
    
11. 在瀏覽器的新 [權限] 索引標籤中，按一下 [存取要求設定]。
    
12. **存取要求設定**] 對話方塊中，清除 [**允許成員] 共用網站和個別的檔案及資料夾**並**允許邀請其他人網站成員 」 群組的成員**（使已取消選取所有的三個核取方塊），然後按一下 [ **確定**。
    
13. 清單中的 [**公司策略成員**。
    
14. 在 [人員與群組] 頁面上，按一下 [新增]。
    
15. 在 [**共用**] 對話方塊中，輸入**C 套件**、 選取它，，然後按一下 [**共用**]。
    
16. 按一下 [**公司策略擁有者**] 清單中。
    
17. 在 [人員與群組] 頁面上，按一下 [新增]。
    
18. 在 [**共用**] 對話方塊中，輸入**IT 人員**、 選取它，，然後按一下 [**共用**]。
    
19. 按一下瀏覽器上的 [上一頁] 按鈕。
    
20. 關閉瀏覽器上的 [**人員與群組**] 索引標籤按一下 [瀏覽器上的 [**公司策略首頁**] 索引標籤，然後關閉 [**網站權限**] 窗格。
    
以下是設定權限的結果：
  
- 「公司策略 - 成員」的 SharePoint 群組僅包含「高層主管」群組 (其中僅包含 CEO、CFO 和 CIO 使用者帳戶) 和「公司策略」群組 (其中僅包含全域管理員使用者帳戶)。
    
- **公司策略擁有者**SharePoint 群組包含只**IT 人員**群組 （其中包含只 ITAdmin1 與 ITAdmin2 使用者帳戶）。
    
- 「公司策略 - 訪客」的 SharePoint 群組未包含任何群組或使用者帳戶。
    
- 成員無法修改網站層級的權限 (這只能由「公司策略 - 擁有者」群組成員來執行)。
    
- 其他使用者帳戶無法存取網站或其資源，或要求存取網站。 網站的額外權限必須由全域管理員或「公司策略 - 擁有者」群組成員來執行。
    
接下來，為「公司策略」小組網站的文件資料夾設定「高度機密」標籤。
  
1. 在瀏覽器的 [Company strategy-Home (公司策略 - 首頁)] 索引標籤中，按一下 [文件]。
    
2. 按一下設定圖示，然後按一下 [文件庫設定]。
    
3. 在 [**權限與管理**] 按一下 [**套用此文件庫中的項目標籤**。
    
4. 在**套用設定的標籤**、 選取**高度機密**、] 和 [**儲存**。
    
接下來，設定 DLP 原則；當使用者在組織外部共用具「高度機密」標籤之 SharePoint Online 小組網站 (包含「公司策略」網站) 上的文件時，即會封鎖使用者。
  
1. 必要時，您的本機電腦上使用瀏覽器並登入 Office 365 入口網站與有安全性管理員或公司管理員角色的帳戶。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 從您的瀏覽器的 [ **Microsoft Office Home** ] 索引標籤按一下 [**安全性&amp;規範**並排顯示。
    
3. 在新**安全性&amp;規範**在瀏覽器] 索引標籤中按一下 [**資料遺失防護 > 原則**。
    
4. 在 [資料外洩防護] 窗格中，按一下 [+ 建立原則]。
    
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
    
16. 在文字方塊中，鍵入或貼上下列內容：
    
  - 若要與組織外部的使用者共用，請下載檔案，然後將它開啟。 依序按一下 [檔案]、[保護文件] 和 [以密碼加密]，然後指定強式密碼。 以個別電子郵件或其他通訊方式傳送密碼。
    
17. 按一下 [確定]****。
    
18. 在**您想要如果我們偵測敏感資訊吗？** ] 窗格中，選取**需要覆寫業務上理由**，然後再按一下 [**下一步**。
    
19. 在**您要開啟 [先取出的原則或測試事項？** ] 窗格中，按一下 **[是]，開啟立即**，並再按 [**下一步**。
    
20. 在**檢閱您的設定**] 窗格中，按一下 [**建立**] 和 [**關閉**。
    
接下來，遵循[使用 Office 365 系統管理中心啟用 Azure RMS](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) 中的指示進行。
  
接著，遵循下列步驟，為 Azure 資訊保護設定新的限域原則與子標籤，以提供保護及權限：
  
1. Office 365 入口網站與有安全性管理員或公司管理員角色的帳戶登入。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 在瀏覽器中的個別] 索引標籤移至 Azure 入口網站 ([https://portal.azure.com](https://portal.azure.com))。
    
3. 如果這是您要設定 Azure 資訊保護第一次，請參閱這些[指示](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time)。
    
4. 在 [清單] 窗格中，按一下 [**所有服務**、 輸入**資訊**，和都 [ **Azure 資訊保護**。
    
5. **Azure 資訊保護**blade、 上，按一下 [**範圍設定的原則 > + 新增原則**。
    
6. 輸入**CompanyStrategy** [**原則名稱**] 及 [**標籤公司策略小組網站中的文件**中**描述**。
    
7. 按一下 [選取取得此原則的使用者或群組] > [使用者/群組]，然後選取 [高階主管]。
    
8. 按一下 [選取] > [確定]。
    
9. 針對 [高度機密] 標籤，按一下省略符號 (...)，然後再按一下 [新增子標籤]。
    
10. 在 [名稱] 中鍵入子標籤的名稱，並在 [描述] 中鍵入標籤的描述。
    
11. 在 [為包含此標籤的文件與電子郵件設定權限] 中，按一下 [保護]。
    
12. 在 [保護] 區段中，按一下 [Azure (雲端金鑰)]。
    
13. 在 [保護] 刀鋒視窗中，按一下 [保護設定] 下的 [+ 新增權限]。
    
14. 在 [新增權限] 刀鋒視窗中，按一下 [指定使用者與群組] 下的 [+ 瀏覽目錄]。
    
15. 在**AAD 使用者與群組**] 窗格中，選取**C 套件**，然後再按一下 [**選取**。
    
16. 在**預設選擇權限**] 下方清除**列印**、**複製及擷取內容**以及**轉寄**] 核取方塊。
    
17. 按兩次 [**確定]** 。
    
18. 在 [子標籤] 刀鋒視窗中，按一下 [儲存]。
    
19. 關閉新的限域原則刀鋒視窗。
    
20. 在**Azure 資訊保護-範圍的原則**blade 中，按一下 [**發佈**] 及 [ **[是]**。
    
若要保護與 Azure 資訊保護及這個新的標籤文件，您必須在測試電腦上的 [[安裝 Azure 資訊保護用戶端](https://docs.microsoft.com/information-protection/rms-client/install-client-app)、 從 Office 365 入口網站安裝 Office 並再登入從 Microsoft Word 中**帳戶C 套件**您試用版訂閱的群組。
  
以下是您產生的組態。
  
![用於公司策略隔離之 SharePoint Online 小組網站的高度機密層級保護。](images/c22695f9-50a1-4abf-a0dd-344b0c92cf94.png)
  
您現在準備好建立這四個網站中的文件，以及使用您試用訂用帳戶中的不同使用者帳戶來測試與其的存取。
  
以下是所有四種 SharePoint Online 小組網站的整體設定。
  
![安全的 SharePoint Online 開發/測試環境中的所有四個小組網站。](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
## <a name="next-step"></a>下一步

當您準備好進行安全的 SharePoint Online 網站的生產環境部署時，請參閱[保護 SharePoint Online 網站與檔案](secure-sharepoint-online-sites-and-files.md)，以取得詳細資訊及逐步部署文章的連結。
  
## <a name="see-also"></a>另請參閱

[保護 SharePoint Online 網站與檔案](secure-sharepoint-online-sites-and-files.md)
  
[安全性解決方案](security-solutions.md)
  
[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)
  
[適用於政治活動、非營利組織和其他彈性組織的 Microsoft 安全性指南](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)




