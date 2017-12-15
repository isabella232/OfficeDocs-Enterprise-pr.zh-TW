---
title: "使用 Office 365 PowerShell 停用服務存取權"
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
- Ent_Office_Other
- PowerShell
- LIL_Placement
- DecEntMigration
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: "說明如何使用 Office 365 PowerShell 新增或移除組織中的 Office 365 服務使用者的存取權。"
ms.openlocfilehash: a371e6adc482a3f21ebfacac08aff02daf4fd5b2
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="disable-access-to-services-with-office-365-powershell"></a>使用 Office 365 PowerShell 停用服務存取權

**摘要：**說明如何使用 Office 365 PowerShell 新增或移除組織中的 Office 365 服務使用者的存取權。
  
當 Office 365 帳戶已指派授權的授權方案時、 Office 365 服務是供使用者從該授權。不過，您可以控制使用者可以存取 Office 365 服務。例如，即使授權允許存取 SharePoint Online，您可以停用其存取權。事實上，您可以使用 Office 365 PowerShell 停用的存取權的服務之任何數字：
- 個別帳戶。
    
- 一組帳戶。
    
- 您組織中的所有帳戶。
    
 **內容：**[簡短的版本 （不含說明指示）](disable-access-to-services-with-office-365-powershell.md#ShortVersion)[長版本 （詳細說明與指示）](disable-access-to-services-with-office-365-powershell.md#LongVersion)[另請參閱](disable-access-to-services-with-office-365-powershell.md#SeeAlso)
## <a name="before-you-begin"></a>開始之前
<a name="RTT"> </a>

- 本主題中的程序需要您連線到 Office 365 PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。
    
- 您可以使用**Get-msolaccountsku**指令程式來檢視您可用的授權方案，以及這些計劃中可用的 Office 365 服務。如需詳細資訊，請參閱[檢視授權和 Office 365 powershell 的服務](view-licenses-and-services-with-office-365-powershell.md)。
    
- 若要查看前後本主題中的程序的結果，請參閱[檢視帳戶授權及服務的詳細資訊與 Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md)。
    
- PowerShell 指令碼是可用的可本主題所述的程序。主要是針對指令碼可讓您檢視和停用 Office 365 組織中包括 Sway 服務。如需詳細資訊，請參閱 ＜[停用 Office 365 powershell Sway 存取](disable-access-to-sway-with-office-365-powershell.md)。
    
- 如果您使用 **Get-MsolUser** Cmdlet，而不使用 _All_ 參數，則只會傳回前 500 個帳戶。
    
## <a name="the-short-version-instructions-without-explanations"></a>簡短版本 (不含說明的指示)
<a name="ShortVersion"> </a>

本節僅呈現程序，但不提供詳盡或多餘的說明。如果您有任何問題或需要詳細資訊，您可以閱讀本主題的其餘部分。
  
若要停用 Office 365 服務讓使用者從單一的授權方案，請執行下列步驟：
  
1. 識別授權的計劃中的非預期的服務使用下列語法：
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    此範例會建立名為授權計劃中停用的 Office Online 和 SharePoint Online 服務**LicenseOptions**物件`litwareinc:ENTERPRISEPACK`(Office 365 企業版 E3)。
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. 使用步驟 1 中的**LicenseOptions**物件上一或多個使用者。
    
  - 若要建立已停用服務的新帳戶，請使用下列語法：
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    本範例會為指派授權及停用步驟 1 所述服務的 Allie Bellew 建立新帳戶。
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    如需在 Office 365 PowerShell 中建立使用者帳戶的詳細資訊，請參閱[Office 365 PowerShell 建立使用者帳戶](create-user-accounts-with-office-365-powershell.md)。
    
  - 若要停用現有授權使用者的服務，請使用下列語法：
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    本範例會停用使用者 BelindaN@litwareinc.com 的服務。
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - 若要停用的所有現有的授權使用者在步驟 1 中所述的服務，指定您的 Office 365 計劃中的**Get-msolaccountsku**指令程式 （例如**litwareinc: enterprisepack** )，顯示名稱，然後執行下列命令：
    
  ```
  $acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -LicenseOptions $LO}
  ```

  - 若要為一組現有的使用者停用服務，請使用下列其中一種方法來識別使用者：
    
  - **篩選根據現有的帳戶屬性的帳戶**為達成此目的，使用下列語法：
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    此範例會為美國境內銷售部門中的使用者停用服務。
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - **使用特定帳戶的清單**若要這樣做，執行下列步驟：
    
1. 建立一個文字檔，其中每一行上都包含一個帳戶，如下所示：
    
  ```
  akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

    在此範例中的文字檔案是 c:\\我的文件\\Accounts.txt。
    
2. 執行下列命令：
    
  ```
  Get-Content "C:\\My Documents\\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

當您要指派它們至授權計劃停用 Office 365 服務的使用者，請參閱 ＜[停用時指派使用者授權的服務存取權](disable-access-to-services-while-assigning-user-licenses.md)。
  
若要停用使用者的 Office 365 服務中所有可用的授權方案，請執行下列步驟：
  
1. 複製此指令碼，並將其貼入 [記事本]。
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
    Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $O365Licences
}
  ```

2. 為您的環境自訂下列值：
    
  -  _<UndesirableService>_在這個範例中，我們將使用 Office Online 和 SharePoint Online。
    
  -  _<Account>_在這個範例中，我們將使用 belindan@litwareinc.com。
    
    自訂的指令碼如下所示：
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
    Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $O365Licences
}
  ```

3. 儲存為指令碼`RemoveO365Services.ps1`中更容易尋找的位置。此範例中，我們將儲存在檔案" `C:\\O365 Scripts`"。
    
4. 使用下列命令在 Office 365 PowerShell 中執行指令碼。
    
  ```
  &amp; "C:\\O365 Scripts\\RemoveO365Services.ps1"
  ```

> [!NOTE]
> 若要反向的任何這些程序 (亦即重新啟用已停用的服務)、 重新執行此程序，但使用值`$null` _DisabledPlans_參數。
  
[返回頁首](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="the-long-version-instructions-with-detailed-explanations"></a>冗長版本 (包含詳細說明的指示)
<a name="LongVersion"> </a>

根據預設，當您使用 Office 365 PowerShell 發出授權啟用所有服務。與這通常是很好的事： 也就是說您可以快速又輕鬆地將授權指派給使用者而不指定每個服務能夠隨時。
  
具有說的但它也是如此您可能會想要將您的部分使用者 ； 限制可用服務例如，也許某些使用者應該可以存取 Office Professional Plus] Skype 商務 Online 和 Exchange Online 中，但這些相同的使用者不應該具有存取 SharePoint Online 或 Office Online。您可以限制的方式中的帳戶吗？顯示，您還可以。為了說明此的運作方式，讓我們採取兩步驟方法來處理這個問題：
  
1. 指派給使用者的所有服務會自動都啟用 Office 365 授權。
    
2. 執行兩個停用該使用者的指定的服務的 Office 365 PowerShell 命令。
    
我們已經已經處理的步驟 1： 我們使用者 (Belinda Newman) 具有存取所有的 Office 365 服務會提供她的 Office 365 授權。不過，我們想要使其沒有 access to SharePoint Online 修改 Belinda 的帳戶 ( `SHAREPOINTENTERPRISE`) 或 Office Online ( `SHAREPOINTWAC`)。但如何我們會假設若要這樣做？
  
以下是如何。首先，我們會使用**新 MsolLicenseOptions**指令程式來建立**LicenseOption**物件包含我們想要停用的服務。我們想要停用 Belinda 的案例中`SHAREPOINTENTERPRISE`和`SHAREPOINTWAC`，因此我們會使用此命令：
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

請參閱如何運作？指定授權方案 ( `litwareinc:ENTERPRISEPACK`)，然後指出每個服務您想要停用，請使用逗號分隔這些服務。
  
> [!NOTE]
> 請確定您儲存新的**LicenseOption**物件的變數。在上述範例中，我們使用`$x`、 雖然您可以使用任何有效的 Windows PowerShell 變數的名稱。 
  
此時我們可以使用下列命令以停用 Belinda 的存取權的兩個服務：
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

不太新潮 here 任一： 我們只要呼叫**Set-msoluserlicense** cmdlet，並包含_LicenseOptions_參數，以及變數 ( `$x`) 包含我們想要停用的計劃。與執行我們看到的內容現在是否我們看一下 Belinda 的授權資訊執行命令： `(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus`？我們可以看到：
  
```
ServicePlan                              ProvisioningStatus
-----------                              ------------------
SWAY                                     Success
INTUNE_O365                              Success
YAMMER_ENTERPRISE                        PendingInput
RMS_S_ENTERPRISE                         Success
OFFICESUBSCRIPTION                       Success
MCOSTANDARD                              Success
SHAREPOINTWAC                            Disabled
SHAREPOINTENTERPRISE                     Disabled
EXCHANGE_S_ENTERPRISE                    Success
```

很酷吧吗？然後當然，我們可以執行這個相同的事情給多位使用者如果我們想要。例如，下列命令停用相同的兩項服務的所有我們已獲授權使用者。指定您的 Office 365 計劃中的**Get-msolaccountsku**指令程式 （例如**litwareinc: enterprisepack** )，顯示的名稱，然後執行它們。
  
```
$acctSKU="<AccountSKU ID>"
Get-MsolUser | Where {$_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1) -and $_.IsLicensed -eq $True} | Set-MsolUserLicense -LicenseOptions $x
```

請記住 Belinda 仍有有效的 Office 365 授權;它是便是這麼做現在她具有較少的服務存取權。我們停用這兩項服務之前，Belinda 那新聞、 OneDrive 及 SharePoint Online 網站：
  
![具有 SharePoint 存取權的使用者。](images/o365_powershell_with_sharepoint.png)
  
現在，她則無法再使用這些選項：
  
![沒有 SharePoint 存取權的使用者。](images/o365_powershell_without_sharepoint.png)
  
這正是我們預期會發生的情況。
  
如果我們稍後變更適用下列事項： 有可能重新啟用這些服務吗？您答案是肯定。若要重新啟用使用者的所有服務，只是使用此命令來建立下列**LicenseOption**物件：
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

該命令做什麼？若要開始使用 Windows PowerShell 常數`$null`表示 「 不 」。（或稍有更多技術語言，就表示"null 值"。）為您重新叫用，當我們使用**New MsolLicenseOptions** cmdlet 我們已指定我們想要停用的服務。在此例中，我們不想要任何要停用服務。可能會導致您相信我們可以使用下列項目，我們沒有在此指定_DisabledPlans_參數的值的命令如下命令：
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans ""
```

但是，將無法運作。但是，則會產生錯誤訊息：
  
 `Set-MsolUserLicense : Cannot bind parameter 'LicenseOptions'. Cannot convert the "" value of type "System.String" to type "Microsoft.Online.Administration.LicenseOption".`
  
幸運地是，將參數值設定為`$null`確實有用：
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

這些明白表示，當我們執行**Set-msoluserlicense** cmdlet 時，我們告訴**Set-msoluserlicense**我們不想要將任何服務停用 Belinda 的：
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

並且，相當符合邏輯地，如果沒有任何服務遭到停用，就必定表示所有服務皆已啟用。
  
既然您了解這一切的運作方式，讓我們為您示範如何您可以選擇發行授權並停用指定服務及所有具有相同的命令。很酷的聲音，但要不需要真正它： 只在同一個命令中包含_AddLicenses_和_LicenseOptions_參數。換句話說，您先建立**LicenseOption**物件：
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

而且然後如先前所述，使用_AddLicenses_和_LicenseOptions_參數在您的命令：
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -AddLicenses "litwareinc:ENTERPRISEPACK" -LicenseOptions $x
```

該命令會發給 Belinda Newman 一個新的授權，但是在哪些 Skype 授權的商務 Online ( `SHAREPOINTWAC`) 和 SharePoint Online ( `SHAREPOINTENTERPRISE`) 這兩個停用。
  
[返回頁首](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="new-to-office-365"></a>初次使用 Office 365 嗎？
<a name="LongVersion"> </a>

||
|:-----|
|![簡短 LinkedIn 學習圖示](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png)**新增至 Office 365？**        **Office 365 系統管理員及 IT 專業人員**，傳送給您的 LinkedIn 學習探索免費的視訊課程。 |
   
## <a name="see-also"></a>See also
<a name="SeeAlso"> </a>

請參閱下列有關透過 Office 365 PowerShell 管理使用者的其他主題：
  
- [使用 Office 365 PowerShell 刪除及還原使用者帳戶](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 刪除及還原使用者帳戶](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 封鎖使用者帳戶](block-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 指派授權至使用者帳戶](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 建立使用者帳戶](create-user-accounts-with-office-365-powershell.md)
    
如需這些程序中所使用之 Cmdlet 的相關資訊，請參閱下列主題：
  
- [Get-content](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [Get-msolaccountsku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [新 MsolLicenseOptions](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [Get-msoluser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [New-msoluser](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [Set-msoluserlicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [Foreach-object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
[返回頁首](disable-access-to-services-with-office-365-powershell.md#RTT)
  

