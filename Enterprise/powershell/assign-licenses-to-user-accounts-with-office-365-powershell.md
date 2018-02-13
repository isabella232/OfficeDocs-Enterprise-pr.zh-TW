---
title: "使用 Office 365 PowerShell 指派授權至使用者帳戶"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Office_Other, LIL_Placement, PowerShell, O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: "說明如何使用 Office 365 PowerShell 指派給未授權使用者的 Office 365 授權。"
ms.openlocfilehash: 11724e7f295079b76bbb9006bad1fb5487087bd8
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2018
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>使用 Office 365 PowerShell 指派授權至使用者帳戶

**摘要：** 說明如何使用 Office 365 PowerShell 指派給未授權使用者的 Office 365 授權。
  
授權 Office 365 中的使用者帳戶很重要，因為使用者無法使用任何 Office 365 服務之前已授權其帳戶。您可以使用 Office 365 PowerShell 有效率地將授權指派給未授權的帳戶，特別是多個帳戶。 

## <a name="before-you-begin"></a>開始之前
<a name="RTT"> </a>

- 本主題中的程序需要您連線到 Office 365 PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。
    
- 使用**Get-msolaccountsku**指令程式來檢視您組織中每個計劃中可用的授權方案和可用授權數量。每個計劃中的可用授權數量是**ActiveUnits** - **WarningUnits** - **ConsumedUnits**。如需授權方案、 授權及服務的詳細資訊，請參閱[檢視授權和 Office 365 powershell 的服務](view-licenses-and-services-with-office-365-powershell.md)。
    
- 若要在組織中尋找未授權的帳戶，請執行命令`Get-MsolUser -All -UnlicensedUsersOnly`
    
- 您只能指派授權給**UsageLocation**屬性設定為有效的 ISO 3166-1 alpha-2 國家/地區碼的使用者帳戶。例如，我們美國、 和法國的 FR。某些 Office 365 服務都無法提供在某些國家/地區。如需詳細資訊，請參閱[關於授權限制](https://go.microsoft.com/fwlink/p/?LinkId=691730)。
    
    若要尋找沒有**UsageLocation**值的帳戶，請執行命令`Get-MsolUser -All | where {$_.UsageLocation -eq $null}`。若帳戶上設定**UsageLocation**值，使用語法`Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`。例如， `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`。
    
- 如果您使用**Get-msoluser** cmdlet 而不需使用`-All`參數，傳回前 500 的帳戶。
    
## <a name="the-short-version-instructions-without-explanations"></a>簡短版本 (不含說明的指示)
<a name="ShortVersion"> </a>

本節內容提供不含詳細說明的程序。如果您有任何問題或想要的詳細資訊，您可以閱讀主題的其餘部分。
  
若要將授權指派給使用者，請在 Office 365 PowerShell 中使用下列語法：
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

此範例會將指定的授權從`litwareinc:ENTERPRISEPACK`(Office 365 企業版 E3) 給未授權使用者的授權方案`belindan@litwareinc.com`。
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

若要將授權指派給多位未經授權的使用者，請使用下列語法：
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 **附註**
  
- 您無法將多個授權指派給相同授權計劃中的使用者。
    
- 如果您沒有足夠可用的授權，授權指派給使用者他們正在可用授權執行之前**Get-msoluser** cmdlet 所傳回的順序。
    
本範例會將指派授權從`litwareinc:ENTERPRISEPACK`(Office 365 企業版 E3) 所有未授權使用者的授權方案。
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

本範例會將相同的授權指派給美國境內銷售部門中未經授權的使用者。
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a>冗長版本 (包含詳細說明的指示)
<a name="LongVersion"> </a>

[檢視授權和未授權使用者與 Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md)本文所述，很可能有的使用者擁有有效的 Office 365 使用者帳戶，但誰不已核發給 Office 365 授權。這表示有效的帳戶或沒有有效的帳戶，這些使用者將無法登入 Office 365。與如果您無法登入，您無法利用任何 Office 365 服務。
  
前述文章也提到，我們可以執行下列命令，以傳回未授權的使用者帳戶清單：
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

該命令會傳回目前未授權 Office 365 的任何使用者的相關資訊：
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  False
```

如您所見，有一個授權的使用者： Belinda Newman。我們到有關 Office 365 授權指派 Belinda 那要如何？
  
首先，我們要執行[檢視授權和 services 與 Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md)文章中討論的**Get-msolaccountsku**指令程式：
  
```
Get-MsolAccountSku
```

此命令會傳回如下的資料：
  
```
AccountSkuId               ActiveUnits    WarningUnits   ConsumedUnits
------------               -----------    ------------   -------------
litwareinc:ENTERPRISEPACK  25             0              24
```

為什麼我們並未執行**Get-msolaccountsku** ？（"Sku，"以防您想知道，是簡短的"stock 保存單位。 」對我們來說是剛商務-說話的 「 產品 」。）原因有兩種為什麼我們已執行**Get-msolaccountsku**。首先，我們需要確定我們實際上已指派 Belinda 的授權。有任何我們可以指派她的授權吗？若要判斷我們需要**ActiveUnits**屬性 (25) 的值，並由欄位刪減**WarningUnits** (0) 和**ConsumedUnits** (24) 屬性的值：
  
 `25 - 0 - 24 = 1`
  
**ActiveUnits**屬性會告訴我們多少個授權購買我們，以及**WarningUnits**和**ConsumedUnits**的結合的值告訴我們多少個授權目前正在使用中。如果我們由欄位刪減已經從我們所購買的授權數目讀出的授權數目，我們會知道多少授權仍可用。幸運會有其，我們有一個授權可用的通訊群組：
  
 `25 - 0 - 24 = 1`
  
若要指派我們需要知道我們的授權方案名稱的新授權給 Belinda 的第二個 （也就是我們需要知道**AccountSkuId** ）。在此例中很簡單： 我們只能有單一的授權方案 ( `litwareinc:ENTERPRISEPACK`)。但是請注意是可能的組織有多個授權方案。在此情況下， **Get-msolaccountsku**會傳回兩個不同**AccountSkuIds**且您必須選擇適當的授權方案時指派授權。現在，儘管如此，我們要堅持最簡單的情況下，並假設我們只是一個授權方案。
  
*如何那麼我們要指派給 Belinda Newman 一個新的授權？*類似：
  
```
Set-MsolUserLicense -UserPrincipalName "BelindaN@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

這也是您必須執行動作： 呼叫**Set-msoluserlicense** cmdlet，確定您指定的使用者與適當的授權方案_UserPrincipalName_參數。
  
當**Set-msoluserlicense**執行完成時，您會看到類似此螢幕上：
  
 `PS C:\\windows\\system32>`
  
換句話說，它將不會看起來像是發生的任何項目。若要確認使用者具有已指派授權，執行如下所示的命令：
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com"
```

如果一切都如預期般，您應該會看到 Belinda 的 isLicensed 屬性現在已設為 True：
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  True
```

> [!安全性附註] 不錯的問題： 如果您進行錯誤並嘗試將授權指派給已具有授權的使用者吗？您將會結束向上給單一使用者提供兩個授權吗？> 快速的回答？無;Office 365 將不會讓您將多個授權指派給相同的使用者。（，從相同的授權方案的多個授權，即）。如果您嘗試執行的命令會失敗下列錯誤訊息： > `Set-MsolUserLicense : Unable to assign this license because it is invalid. Use the Get-MsolAccountSku cmdlet to retrieve a list of valid licenses.`> 不可否認，這個錯誤訊息會稍微誤導： 授權不是真正無效、 只被指派給使用者之已連授權 [*具有*。不過，錯誤訊息預留，最重要的一位使用者將不會使用多個授權最後。
  
如您剛才所見，它會是很容易使用 Office 365 PowerShell 將單一授權指派給單一使用者。與之負責人明顯的問題： 有用為一樣簡單、 也許甚至更容易，若要使用 Office 365 系統管理中心來將單一授權指派給單一使用者吗？也許 ； 以及而定，組件，您正在更知道如何使用 Windows PowerShell 或更多知道如何使用 Office 365 系統管理中心。真正發揮功效的 Windows PowerShell，但也將多個授權指派給多位使用者在需要時。例如，此命令會將 Office 365 授權指派給任何您沒有授權的使用者：
  
```
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

在上述命令中，我們使用**Get-msoluser**和_UnlicensedUsersOnly_參數來傳回所有授權的使用者帳戶的集合。然後將該集合傳遞到**Set-msoluserlicense**指令程式 ；接著，**就**會將指派授權 (取自`litwareinc:ENTERPRISEPACK`授權方案) 給集合中每個使用者。
  
不過，如果您有 5 未授權的使用者只有一個可用的授權但吗？在此情況下**就**會將可用授權提供給**Get-msoluser**所傳回的第一個使用者。**Set-msoluserlicense**將然後盡責嘗試將授權指派給四個使用者，但總共四個那些嘗試將會失敗搭配下列錯誤訊息：
  
 `Set-MsolUserLicense : Unable to assign this license because the number of allowed licenses have been assigned.`
  
換句話說，就只是將不會失敗。而它將指派其可以為相同數目的授權。它只會失敗。
  
我們嘗試另一個範例。也許您想要將授權指派給 Sales 部門中的所有使用者。沒有問題：
  
```
Get-MsolUser -All -Department "Sales" | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

或者，如果您想要再有技巧性一點，並且想要儘量減少錯誤訊息和運算處理，那就只要指派授權給業務部門中未授權的使用者即可：
  
```
Get-MsolUser -All -Department "Sales" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

畢竟是無點到已授權的授權使用者嘗試。如我們所見，可將無法運作。
  
以下是另一個範例。也許您想要所有美國目前沒有使用者的 Office 365 授權的授權。在此情況下：
  
```
Get-MsolUser -All -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

等等，依此類推。
  
> [!NOTE]
> 執行命令的說，對所有未授權使用者發出授權需要多久的時間？這是很難說： 定從必須為您的網路連線速度的使用者數目的每個項目。如果您有幾個好幾百種這快速合理預期的授權使用者 （亦即，它不應該採取以上數分鐘或兩個）。如果您有 10000 位使用者來授權它會做了明顯改善時間更長。但想像只要它來採用以使用 Office 365 系統管理中心將授權指派給 10000 位使用者。 
  
只要我們已經在主旨，以下是您要指派授權時需要留意的： 如果使用者沒有**UsageLocation**屬性設定值您不能指派給該使用者的 Office 365 授權。而您會收到錯誤訊息類似：
  
 `Set-MsolUserLicense : You must provide a required property: Parameter name: UsageLocation`
  
在有點圓環易這個錯誤訊息告訴我們的上述的使用者尚未指派**UsageLocation**。當您可能會有猜測、 **UsageLocation**屬性 （這表示地區或國家的使用者通常使用 Office 365） 就變得極為重要。為何？那是因為可用使用者服務取決於您附加元件購買，但也在使用者所在的授權套件不只： 由於本機規則及規定，而某些服務可能會無法使用某些使用者。如果使用者沒有**UsageLocation**，Office 365 就沒有辦法知道哪些服務法律上幫助會公開給該使用者。因此，Office 365 不能提供給任何服務該使用者至少不之前已指定**UsageLocation** 。
  
> [!NOTE]
> 當您設定的使用者帳戶時就會知道立即是否有任何全球的指定部分相關聯的授權限制。例如，如果您變更已獲授權使用者**UsageLocation**伊朗 ( `IR`)，此命令將會失敗與此錯誤訊息： `Set-MsolUser : Unable to update license for this user. One or more of the assigned service plans is not available in this user's country. Prohibited Service Plans: EXCHANGE_S_ENTERPRISE, SHAREPOINTENTERPRISE, SHAREPOINTWAC, MCOSTANDARD, OFFICESUBSCRIPTION, RMS_S_ENTERPRISE. Specific service plans can be disabled for a user by using the licenseoptions parameter.`> 那是因為 Office 365 不是目前可供伊朗的使用者使用。如需詳細資訊，請參閱[關於授權限制](https://go.microsoft.com/fwlink/p/?LinkId=691730)。順便一提，Office 365 使用國際組織所產生的 (ISO) 雙字母國家/地區碼。您可以找到這些代碼[ISO 網站](https://go.microsoft.com/fwlink/p/?LinkId=84073)上。 
  
如果您想要確認指定的使用者有**UsageLocation** ，您可以使用類似的命令：
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com" | Select-Object UsageLocation
```

或者，您可以傳回所有使用此命令沒有**UsageLocation**的使用者的清單：
  
```
Get-MsolUser -All | Where-Object {$_.UsageLocation -eq $null}
```

> [!NOTE]
> 當您將授權指派給使用者的使用者將，根據預設，授與存取權給您的組織具有存取權的所有 Office 365 服務。例如若您的 Office 365 企業版 E3 購買授權，您新授權的使用者會自動授與類似 Exchange Online、 Skype 服務存取權商務 Online 和 SharePoint Online。如果您想要限制使用者的存取這些服務 (例如，您可能會想但*不是*to SharePoint Online 的存取權的使用者至 Exchange Online 和 Skype 的商務 Online) 然後請參閱下列文章[停用服務存取權與 Office 365PowerShell](disable-access-to-services-with-office-365-powershell.md)。 
  
## <a name="new-to-office-365"></a>初次使用 Office 365 嗎？

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>請參閱
<a name="SeeAlso"> </a>

請參閱下列有關透過 Office 365 PowerShell 管理使用者的其他主題：
  
- [使用 Office 365 PowerShell 建立使用者帳戶](create-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 刪除及還原使用者帳戶](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 封鎖使用者帳戶](block-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 移除使用者帳戶中的授權](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
如需這些程序中所使用之 Cmdlet 的相關資訊，請參閱下列主題：
  
- [Get-msolaccountsku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Set-msoluserlicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [選取物件](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

