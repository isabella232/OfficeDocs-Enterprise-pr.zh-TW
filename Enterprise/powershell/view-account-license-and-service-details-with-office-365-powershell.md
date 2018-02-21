---
title: "使用 Office 365 PowerShell 檢視帳戶授權與服務詳細資料"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: "說明如何使用 Office 365 PowerShell 來判斷已指派給使用者的 Office 365 服務。"
ms.openlocfilehash: 69784b43e6e2b24f776d07a937877e5ae0c74888
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a>使用 Office 365 PowerShell 檢視帳戶授權與服務詳細資料

**摘要：**說明如何使用 Office 365 PowerShell 來判斷已指派給使用者的 Office 365 服務。
  
在 Office 365 授權的授權方案 （也稱為的 Sku 或 Office 365 計劃） 讓使用者能夠存取 Office 365 服務所定義的那些計劃。不過，使用者可能無法存取所有目前已指派給他們的授權中可用的服務。您可以使用 Office 365 PowerShell 檢視的使用者帳戶之服務的狀態。 

## <a name="before-you-begin"></a>開始之前
<a name="RTT"> </a>

- 本主題中的程序需要您連線到 Office 365 PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。
    
- 使用命令`Get-MsolAccountSku`和`(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus`尋找下列資訊：
    
  - 您的組織可用的授權計劃。
    
  - 每個授權計劃中可用的服務，以及其列出的順序 (索引編號)。
    
     如需授權方案、 授權、 及服務的詳細資訊，請參閱[檢視授權和 Office 365 powershell 的服務](view-licenses-and-services-with-office-365-powershell.md)。
    
- 使用命令`Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses`尋找的授權指派給使用者和的順序，其中所列 （索引編號）。
    
- 如果您使用 **Get-MsolUser** Cmdlet，而不使用 _All_ 參數，則只會傳回前 500 個帳戶。
    
## <a name="the-short-version-instructions-without-explanations"></a>簡短版本 (不含說明的指示)
<a name="ShortVersion"> </a>

若要檢視所有使用者有權存取 Office 365 PowerShell 服務，請使用下列語法：
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

此範例會顯示使用者 BelindaN@litwareinc.com 具有存取服務。這會顯示指派至她帳戶的所有授權與相關聯的服務。
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

本範例顯示使用者 BelindaN@litwareinc.com 有權存取的服務，從指派給其帳戶的第一個授權 (索引編號為 0) 開始。
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

若要尋找已啟用或未啟用特定服務的所有授權使用者，使用下列語法：
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled" -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled"...}
```

這些範例使用下列資訊：
  
- 提供我們感興趣的 Office 365 服務的存取授權已指派給 （索引編號為 0） 的所有使用者的第一個授權。
    
- 我們感興趣的 Office 365 服務是 Skype 商務 Online 與 Exchange Online。相關聯的授權方案授權，Skype 商務 online 是 6 列出的服務 （索引編號為 5），與 Exchange Online 是 9th 服務列出 （索引編號為 8）。
    
此範例會傳回所有已獲授權的商務 Online 與 Exchange Online Skype 所啟用的使用者。
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

此範例會傳回所有已獲授權的使用者未啟用 Skype 商務 Online 或 Exchange Online。
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -eq "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a>冗長版本 (包含詳細說明的指示)
<a name="LongVersion"> </a>

### <a name="find-the-office-365-powershell-services-that-a-user-has-access-to"></a>尋找 Office 365 PowerShell 服務使用者有權存取

務必做了明顯改善您知道哪些使用者已核發給 Office 365 授權和哪些使用者尚未。（請參閱[檢視授權和未授權使用者與 Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md)如需詳細資訊）。不過，只要擁有 [Office 365 授權不會告訴您不要有關該使用者可以實際怎麼與 Office 365。可以一次使用 Exchange Online 或 Skype 商務 online 吗？可以這位使用者存取 SharePoint Online 吗？沒有他就可以存取 Office Professional Plus 吗？具有授權只是表示使用者有可能會存取這些服務。不過，使用者可用的功能取決於已啟用其授權的服務。
  
那要如何判斷其 Office 365 功能的使用者具有存取權？若要我們必須執行類似這一個命令：
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Select-Object -ExpandProperty Licenses | Select-Object -ExpandProperty ServiceStatus
```

在此命令中，我們將使用**Get-msoluser** cmdlet 可傳回 BelindaN@litwareinc.com 的帳戶資訊。我們已傳回該資訊，我們再帳戶將資料傳送到**Select-object**指令程式並要求**Select-object**來 「 展開 」**授權**屬性的值：
  
 `Select-Object -ExpandProperty Licenses`
  
為什麼這麼做？依預設，**授權**屬性只能告訴我們授權套件 Belinda 的授權來源的名稱：
  
```
Licenses
--------
{litwareinc:ENTERPRISEPACK}
```

「 展開 」**授權**屬性可為我們一點點的資訊：
  
```
ExtensionData     AccountSku       AccountSkuId ServiceStatus
-------------     ----------       ------------ -------------
System.Runtime... Microsoft.On...  litwarein... {Microsoft.Online.A...
```

然後藉由展開**ServiceStatus**屬性可以收到更多資訊：
  
|服務計劃 * * *|描述 * * *|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure 版權管理 (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office 專業增強版  <br/> |
| `MCOSTANDARD` <br/> |商務用 Skype Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online Plan 2  <br/> |
   
> [!NOTE]
> 您說這樣要輸入太多吗？如果您可以一點的 Windows PowerShell 含糊性，您可以忍受命令的這個精簡的版本改： >`(Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com).Licenses[0].ServiceStatus`
  
您想知道，我們可以 「 展開 」**授權**屬性因為**授權**是多重值的屬性： 它是可儲存多個值的單一屬性。當我們展開屬性值我們只是向下切入至取得這些額外的值，預設不會顯示於螢幕上。
  
> [!NOTE]
> 您應該要知道值是多重值的屬性那要如何？以找出，請嘗試執行如下的命令： > `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Get-Member`> **get-member**指令程式會傳回物件本身 ； 的詳細資訊在此例中屬性的相關資訊值的使用者帳戶物件組成。以下是 [ **Get-member**有**授權**屬性的看法： > `Licenses Property System.Collections.Generic.List[Microsoft.On...`> 如果屬性定義對於合集有一些涵義 (在此例中`System.Collections.Generic.List`) 那麼您會知道您正在處理一個多重值屬性。 
  
所以什麼意思此？若要回答，我們先看另一個**Get-msoluser** cmdlet 所傳回的資訊：
  
```
ServicePlan                       ProvisioningStatus
-----------                       ------------------
SWAY                              Success
INTUNE_O365                       Success
YAMMER_ENTERPRISE                 PendingInput
RMS_S_ENTERPRISE                  Success
OFFICESUBSCRIPTION                Success
MCOSTANDARD                       Success
SHAREPOINTWAC                     Success
SHAREPOINTENTERPRISE              Success
EXCHANGE_S_ENTERPRISE             Success
```

與我們也看看一下表格，這些詭異命名服務計畫確實代表什麼：
  
|服務計劃 * * *|描述 * * *|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure 版權管理 (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office 專業增強版  <br/> |
| `MCOSTANDARD` <br/> |商務用 Skype Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online Plan 2  <br/> |
   
所有的該你吗？ `MCOSTANDARD`剛程式設計的內部名稱 Skype 為線上商務時`OFFICESUSBCRIPTION`只是內部程式設計名稱 Office Professional plus。不在全球的最直覺性項重點但只要您保留此表格方便使用您將不會有許多問題時有使用 Office 365 服務。
  
但等待： 沒有更多。當我們學會文章[檢視授權和 Office 365 powershell 的服務](view-licenses-and-services-with-office-365-powershell.md)，如果**ProvisioningStatus**設為`Success`這表示已完全啟用服務 ；例如如果`MCOSTANDARD`設為`Success`這表示使用者可以存取 Skype 商務 online。如果**ProvisioningStatus**設為`PendingInput`也就是說 Office 365 仍在處理服務要求;不過，使用者通常可以登入並要求完成處理的同時存取服務。(`YAMMER_ENTERPRISE`永遠會顯示為`PendingInput`，但 [確定]： 可將不會停止登入 Yammer 中的使用者)。
  
> [!IMPORTANT]
> 使用者可安裝和啟動新的 Office Professional Plus 安裝時`OFFICESUBSCRIPTION`處於`PendingInput`狀態。
  
與不用說，是 [服務設定為 「 `Disabled` ，表示此服務有問題且無法供使用者。
  

### <a name="find-users-that-have-access-to-specific-office-365-powershell-services"></a>尋找具有特定 Office 365 PowerShell 服務存取權的使用者

在不同的文章，我們看到如何使用 Office 365 PowerShell 停用使用者存取服務。（如果您未接的文章，請參閱[停用 Office 365 powershell 的服務存取權](disable-access-to-services-with-office-365-powershell.md)）。之負責人明顯的問題： 是否有任何方法來決定哪些*使用者*(也就是一個以上的使用者) 已啟用或停用的服務？
  
我們已希望希望有人會。若要回答這個問題，請檢閱我們先看文章[檢視授權和 services 與 Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md)中的我們唯一可用的授權方案的服務的表格`litwareinc:ENTERPRISEPACK`：
  
|服務計劃 * * *|描述 * * *|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure 版權管理 (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office 專業增強版  <br/> |
| `MCOSTANDARD` <br/> |商務用 Skype Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online Plan 2  <br/> |
   
回想一下可能、 服務計劃只不過是一項產品; 內部程式設計名稱例如， `OFFICESUBSCRIPTION`，其中 [名稱] 是 Office Professional Plus 的內部程式設計名稱。如果`OFFICESUBSCRIPTION`顯示成`SUCCESS`於使用者的服務計劃，然後這表示使用者可以存取 Office Professional Plus。如果`EXCHANGE_S_ENTERPRISE`已列為`DISABLED`這表示使用者無法使用 Exchange Online。
  
> [!IMPORTANT]
> 使用者可安裝和啟動新的 Office Professional Plus 安裝時`OFFICESUBSCRIPTION`處於`PendingInput`狀態。
  
現在是時間所在變得極為重要服務的顯示的順序。Windows PowerShell 將每個項目清單中的索引編號。第一個項目是 0 下, 一個項目是 1，依此類推。結果是下表所述：
  
|索引編號 * * *|服務計劃 * * *|
|:-----|:-----|
|0  <br/> | `SWAY` <br/> |
|1  <br/> | `INTUNE_O365` <br/> |
|2  <br/> | `YAMMER_ENTERPRISE` <br/> |
|3  <br/> | `RMS_S_ENTERPRISE` <br/> |
|4  <br/> | `OFFICESUBSCRIPTION` <br/> |
|5  <br/> | `MCOSTANDARD` <br/> |
|6  <br/> | `SHAREPOINTWAC` <br/> |
|7  <br/> | `SHAREPOINTENTERPRISE` <br/> |
|8  <br/> | `EXCHANGE_S_ENTERPRISE` <br/> |
   
如您所見，`SWAY`第一個服務列，讓它會取得指派 0 的索引編號。
  
> [!CAUTION]
> 為什麼要選擇 0 及 1 不？這是程式設計的事。程式設計語言中的索引會告訴您最項目"位移"一開始的陣列。第一個項目陣列的*為*開頭，所以其 offset 為 0。第二個項目是陣列的 1 個項目一開始，所以其位移是陣列的 1。
  
我們嘗試範例。假設我們想尚未啟用 Exchange Online 的所有已獲授權使用者的清單。若要這樣做，我們可以使用下列命令：
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

不可否認，即難懂的外觀的一點命令，讓我們需要數分鐘來說明其運作方式。這是實際上兩組件] 命令，與第一個部分是很簡單： 我們使用**Get-msoluser** cmdlet 可傳回所有適用的 Office 365 使用者的集合 （已獲授權和未授權）：
  
```
Get-MsolUser
```

然後將該資訊傳送到**Where-object**指令程式。**Where-object**會通過的所有使用者帳戶並尋找這些帳戶的同時滿足下列準則：
  
- 會**尋找 isLicensed**內容等於 ( `-eq`) `True` ( `$true`)。這可讓我們快速清除未授權的使用者。
    
- **授權 [0] 的值。ServiceStatus [8]。ProvisioningStatus**屬性等於 ( `-eq`) `Disabled`。基於我們立即，此龐大的屬性名稱的重要部分是：
    
     `ServiceStatus[8]`
    
    `[8]`代表 Exchange Online 的索引編號。（我們知道可從查看表格前幾分鐘）。如果我們想要尋找 Skype 商務 online 啟用的所有使用者吗？Skype 商務 Online 的索引編號是的 5 中，因此我們會使用此語法：
    
     `ServiceStatus[5]`
    
    以此類推。
    
    順便一提，`Licenses[0]`表示我們想要查看的授權方案。由於我們測試網域只能有一個授權方案這不會更加它們。但假設我們有已被指派授權從兩個不同的授權方案的使用者。在此情況下，`Licenses[0]`就代表第一個的授權方案和`Licenses[1]`就代表第二個的授權方案。
    
    若要尋找指派給使用者的授權，以及其列出的順序，請執行下列命令：
    
  ```
  Get-MsolUser -UserPrincipalName <Account>  | Format-List DisplayName,Licenses
  ```

您看到這一切的運作方式？Office Professional plus 的索引編號是 4;因此，此命令會傳回所有尚未啟用 Office Professional plus 的使用者清單：
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -eq "Disabled"}
```

與如果我們想要的已*啟用*Office Professional Plus 的使用者清單吗？如果您已啟用則**ServiceStatus**您將會是以及`PendingInput`或`Success`;換句話說，將會在**ServiceStatus** *不*等於 ( `-ne`) `Disabled`。這表示我們只需要為取得我們上一個命令並再分出分頁出`-eq`運算子`-ne`運算子：
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -ne "Disabled"}
```

此一說移，該程式碼可能不會 win 許多優點競賽。與真偽會告知、 程式碼可以取得更多纏。例如，假設我們要尋找已啟用這兩個 Skype 商務 Online 與 Exchange Online 的使用者：
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses.ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

但不要擔心太多關於如何 gnarly 所可能具有的外觀： 重要的是以較少，您可以擷取此資訊。您無法取得在使用 Office 365 系統管理中心這個相同的資訊嗎？理論上，是但，以實用的字詞、 否]。若要取得這個相同的資訊使用 Office 365 系統管理中心於就必須查看每個使用者的授權資訊、 一次一位使用者與然後手動追蹤誰已啟用的*X*及人員還沒有。會將運作，但事實上： 如果您有超過 10 或 11 使用者，您不些為達成此目的。它是方式太面對那樣既繁瑣又耗時。
  
它會當然，是為什麼我們有 Windows PowerShell： Windows PowerShell 協助讓您免於面對那樣既繁瑣又耗時的工作。
  
我們活躍於它，以下是用於檢視服務資訊的最終命令：
  
```
Get-MsolUser | Select-Object DisplayName, @{Name="Sway";Expression={$_.Licenses[0].ServiceStatus[0].ProvisioningStatus}}, @{Name="MDM";Expression={$_.Licenses[0].ServiceStatus[1].ProvisioningStatus}}, @{Name="Yammer";Expression={$_.Licenses[0].ServiceStatus[2].ProvisioningStatus}}, @{Name="AD RMS";Expression={$_.Licenses[0].ServiceStatus[3].ProvisioningStatus}}, @{Name="OfficePro";Expression={$_.Licenses[0].ServiceStatus[4].ProvisioningStatus}}, @{Name="Skype";Expression={$_.Licenses[0].ServiceStatus[5].ProvisioningStatus}}, @{Name="OfficeWeb";Expression={$_.Licenses[0].ServiceStatus[6].ProvisioningStatus}}, @{Name="SharePoint";Expression={$_.Licenses[0].ServiceStatus[7].ProvisioningStatus}}, @{Name="Exchange";Expression={$_.Licenses[0].ServiceStatus[8].ProvisioningStatus}} | ConvertTo-Html > "C:\\My Documents\\Service Info.html"
```

沒錯，是非常瘋狂尋找命令。但是它會建立 CSV 檔案顯示所有使用者及所有其服務狀態。

  
## <a name="see-also"></a>另請參閱
<a name="SeeAlso"> </a>

請參閱下列有關透過 Office 365 PowerShell 管理使用者的其他主題：
  
- [使用 Office 365 PowerShell 建立使用者帳戶](create-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 刪除及還原使用者帳戶](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 封鎖使用者帳戶](block-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 指派授權至使用者帳戶](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 移除使用者帳戶中的授權](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
如需這些程序中所使用之 Cmdlet 的相關資訊，請參閱下列主題：
  
- [ConvertTo Html](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [格式清單](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [選取物件](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a>初次使用 Office 365 嗎？


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]