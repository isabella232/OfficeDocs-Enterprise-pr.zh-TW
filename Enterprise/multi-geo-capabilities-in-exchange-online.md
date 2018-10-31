---
title: Exchange Online 中的多個地理位置功能
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Normal
ms.assetid: ''
description: Exchange Online 中的多個地理位置功能的多個地理區域展開您的 Office 365 目前狀態。
ms.openlocfilehash: 5f34a2da47b9767aa9dfe22c6be7237951128960
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849919"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a>Exchange Online 中的多個地理位置功能

Office 365 的多重地理位置功能啟用單一租用戶至跨多個地理位置。啟用多個地理位置時，客戶可以選取 Exchange Online 信箱內容 （靜態資料） 的位置每位使用者為基礎。

初始租用戶位置 （稱為集中管理位置） 決定帳單地址為基礎。啟用多個地理位置時，您可以利用信箱中的其他衛星位置：

- 直接在衛星位置中建立新的 Exchange Online 信箱。

- 將現有的 Exchange Online 信箱移至衛星位置。

- Onboarding 將信箱從內部部署 Exchange 組織直接將衛星位置。

下列的地理位置都可供使用的多個地理位置設定：

- 亞太地區

- 澳大利亞

- 加拿大

- 歐盟

- 法國

- 印度 (目前僅供客戶在印度計費地址)

- 日本

- 韓國

- 英國

- 美國

## <a name="prerequisite-configuration"></a>必要的設定
您可以開始使用多個地理位置功能在 Exchange Online 之前，Microsoft 需要設定多個地理位置支援 Exchange Online 租用。排序 [Office 365 多重地理位置和授權在顯示您的租用戶之後觸發此單次設定程序。此單次設定程序通常應該採取早於 30 天才能完成。若要排序 Office 365 多重地理位置、 連絡 Microsoft 代表。如需詳細資訊，請參閱https://aka.ms/Multi-Geo。

將會收到通知在[Office 365 郵件內](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093)完成您的設定之後。設定自動觸發之後在您的租用戶中顯示多個地理位置授權。

## <a name="mailbox-placement-and-moves"></a>信箱位置及移動
Microsoft 完成必要的多個地理位置的設定步驟之後，Exchange Online 會受限於使用者物件上呼叫的**PreferredDataLocation**屬性在 Azure AD。

Exchange Online 進行同步處理來自 Azure AD 的**PreferredDataLocation**屬性到 Exchange Online 的目錄服務中的**MailboxRegion**屬性。**MailboxRegion**的值會決定要放置使用者信箱及任何相關聯的封存信箱地理位置。您不可以設定使用者的主要信箱和封存信箱來位於不同地理位置。只有一個地理位置可以設定每個使用者物件。

- 當**PreferredDataLocation**設定與現有的信箱使用者上時，信箱會放入佇列中重新配置和自動移到指定的地理位置。 

- 當**PreferredDataLocation**設定上沒有現有信箱的使用者時，將信箱佈建到指定的地理位置中。 

- 當使用者未指定**PreferredDataLocation**時，信箱將會被放置在集中管理位置。

- 如果**PreferredDataLocation**程式碼不正確 （例如一種 NAN 而不是名稱），信箱將會被放置在集中管理位置。

**請注意**： 多重地理位置功能和 Skype 的商務線上地域主控會議這兩個使用者物件上使用**PreferredDataLocation**屬性來尋找服務。如果您在地域託管會議的使用者物件上設定**PreferredDataLocation**值，這些使用者的信箱將會自動移到指定的地理位置之後在 Office 365 租用戶上啟用多個地理位置。

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a>功能會受到限制的多個地理位置 in Exchange Online
1. 使用者信箱、 資源信箱 （會議室及器材信箱） 和共用的信箱支援多個地理位置功能。公用資料夾信箱與 Office 365 群組保持在中央位置。
 
2. 安全性和符合性功能 （例如稽核和 eDiscovery） 所能使用 Exchange 系統管理中心 (EAC) 中不提供多個地理位置的組織。而被必須使用[Office 365 的安全性與規範中心](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8)設定安全性和符合性功能。

3. Outlook for Mac 使用者可能會遇到存取其線上封存資料夾暫時遺失時將他們的信箱移至新的地理位置。此條件可時發生使用者的主要和封存信箱皆位於不同地理位置，因為跨地理信箱移動可能會在不同時間完成。

4. 使用者無法跨地理位置 （前身為 Outlook Web App 或 OWA） 在 web 上的 Outlook 中共用*信箱資料夾*。例如，歐盟使用者無法使用網路上的 Outlook 開啟共用的資料夾位於美國信箱中。不過，Outlook Web 使用者可以開啟*其他信箱*中不同 Geos 使用另一個瀏覽器視窗中[開啟另一個人信箱在 Outlook Web App 的另一個瀏覽器視窗中](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362)所述。

    **請注意**： 跨地理信箱資料夾共用支援 windows 在 Outlook 中。

## <a name="administration"></a>系統管理 
遠端 PowerShell 才可檢視及 Office 365 環境中設定多個地理屬性。如需不同用來管理 Office 365，請參閱[管理 Office 365 和 Exchange Online 使用 Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6)的 PowerShell 模組。

- 您需要的[Microsoft Azure Active Directory PowerShell 模組](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx)v1.1.166.0 或更新版本中以 v1.x 使用者物件，請參閱 ＜ **PreferredDataLocation**屬性。透過 AAD 連線到 AAD 進行同步處理的 user 物件不能有直接修改透過 AAD PowerShell 其**PreferredDataLocation**值。僅限雲端使用者物件可以透過 AAD PowerShell 修改。若要連線至 Azure AD PowerShell，請參閱 ＜ [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)。 

- 若要連線至 Exchange Online PowerShell，請參閱[Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)。 

### <a name="connect-directly-to-a-specific-geo-using-exchange-online-powershell"></a>直接連接到使用 Exchange Online PowerShell 特定地理位置
一般而言，Exchange Online PowerShell 會連線至預設的地理位置。但是，您也可以直接對非預設地理位置連線。因為效能改良功能，建議您直接連線至非預設地理位置僅管理該地理位置中的使用者時。

若要連線至特定的地理位置，*來指定 ConnectionUri*參數是不同於一般連線指示。其餘的命令和值都相同。步驟包括：

1. 在您的本機電腦上開啟 Windows PowerShell 並執行下列命令：
    
    ```
    $UserCredential = Get-Credential
    ```
   在**Windows PowerShell 認證要求**] 對話方塊中，輸入您的公司或學校帳戶和密碼，並再按一下 [**確定]**。
    
2. 取代`<emailaddress>`與**任何**目標地理位置和執行下列命令中的信箱的電子郵件地址。您的權限的信箱與關聯至您在步驟 1 中的認證不是因素;電子郵件地址只會告知 Exchange Online 連線的位置。
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   例如，如果您想要連線的地理位置中的有效信箱的電子郵件地址 olga@contoso.onmicrosoft.com，執行下列命令：

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. 執行下列命令：
    
    ```
    Import-PSSession $Session
    ```

### <a name="azure-ad-connect-version-requirements"></a>Azure AD 連接版本需求
AAD 連線版本 1.1.524.0 或更新版本進行同步處理的使用者物件上設定**PreferredDataLocation**屬性從內部部署 Active Directory 是唯一支援的方法。透過 AAD 連線到 AAD 進行同步處理的 user 物件不能有直接修改透過 AAD PowerShell 其**PreferredDataLocation**值。僅限雲端使用者物件可以透過 AAD PowerShell 修改。如需詳細指示，請參閱[Azure [Active Directory 連線同步處理： 設定 Office 365 資源的慣用的資料位置](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)。

### <a name="geo-codes"></a>地理位置代碼
您可以使用三個字母代碼**PreferredDataLocation**屬性中指定的地理位置。下表列出可用的 Geos 程式碼：

|地理 |代碼 |
|---------|---------|
|亞太地區 / |APC |
|澳大利亞 |AUS |
|加拿大 |CAN |
|歐盟 |EUR |
|法國 |FRA|
|印度 |尋找 |
|日本 |JPN |
|韓國 |韓國 |
|英國 |GBR |
|美國 |NAM |

**請注意**： 在**PreferredDataLocation**和**MailboxRegion**屬性是字串沒有錯誤檢查。如果您輸入了無效的值 (例如 NAN) 信箱將會被放置在預設的地理位置。

### <a name="view-the-available-geos-that-are-configured-in-your-exchange-online-organization"></a>檢視設定於 Exchange Online 組織中使用 Geos
若要查看在 Exchange Online 組織中設定 Geos 的清單，請執行下列命令在 Exchange Online PowerShell：

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

此命令的輸出看起來像這樣：

```
APC
AUS
CAN
EUR
FRA
GBR
JPN
KOR
NAM
```

### <a name="view-the-default-geo-for-your-exchange-online-organization"></a>Exchange Online 組織的地理位置預設檢視
若要檢視您的 Exchange Online 組織的預設地理位置，請執行下列命令在 Exchange Online PowerShell：

```
Get-OrganizationConfig | Select DefaultMailboxRegion
```

此命令的輸出看起來像這樣：

```
DefaultMailboxRegion
--------------------
NAM
```


### <a name="find-the-geo-location-of-a-mailbox"></a>尋找信箱的地理位置
**Get-mailbox**指令程式在 Exchange Online PowerShell 會顯示下列多重地理位置相關的信箱上的屬性：

- **資料庫**： 資料庫名稱的前 3 字母會對應至地理位置的程式碼會告訴您信箱所在目前。線上封存信箱**ArchiveDatabase**應使用屬性。

- **MailboxRegion**： 指定已設定 （已從**PreferredDataLocation**在 Azure AD 的同步處理） 系統的地理位置程式碼。

- **MailboxRegionLastUpdateTime**： 指出當 MailboxRegion 最近更新 （自動或手動）。

如需這些信箱的內容，請使用下列語法：

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

例如，若要查看信箱 chris@contoso.onmicrosoft.com 地理資訊，請執行下列命令：

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

此命令的輸出看起來像這樣：

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> **附註：** 如果在 [資料庫名稱的地理位置程式碼不符合**MailboxRegion**值，信箱將會自動被放入佇列中重新配置和移至**MailboxRegion**值所指定的地理位置 (Exchange Online 尋找不符這些屬性值）。

### <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo"></a>將現有的僅限雲端信箱移至特定的地理位置
僅限雲端使用者是不透過 AAD 連線租用戶兩者。此使用者建立直接在 Azure AD。使用 Windows PowerShell 的 Azure AD 模組中的**Get-msoluser**和**Set-msoluser** cmdlet 可以檢視或指定要儲存僅限雲端使用者信箱的地理位置。

若要檢視使用者的**PreferredDataLocation**值，請在 Azure AD PowerShell 中使用下列語法：

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

例如，若要查看使用者 michelle@contoso.onmicrosoft.com **PreferredDataLocation**值，請執行下列命令：

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

此命令的輸出看起來像這樣：

```
UserPrincipalName     : michelle@contoso.onmicrosoft.com
PreferredDataLocation : EUR
```

若要修改的僅限雲端使用者物件的**PreferredDataLocation**值，請 Azure AD PowerShell 中使用下列語法：

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

例如，若要將**PreferredDataLocation**值設為使用者 michelle@contoso.onmicrosoft.com 歐盟 (EUR) 地理位置，執行下列命令：

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

**附註**：

- 為提及之先前您無法使用此程序從內部部署 Active Directory 同步處理的使用者物件。您需要變更**PreferredDataLocation**值使用 AAD 連線。如需詳細資訊，請參閱[Azure [Active Directory 連線同步處理： 設定 Office 365 資源的慣用的資料位置](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)。 

- 需花費重新放置 mailboxfrom 其目前的地理位置至新的所需的地理位置會視數個因素而定：
 
  - 信箱的類型及大小。
 
  - 要移動的信箱數目。
 
  - 移動資源的可用性。

#### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a>移動停用信箱上訴訟暫止狀態
停用信箱訴訟暫止狀態的 ediscovery （英文） 用途不能移來變更其已停用狀態及其**PreferredDataLocation**值會保留。已停用將信箱移入訴訟資料暫留：

1. 暫時將授權指派給信箱。

2. 變更**PreferredDataLocation**。

3. 其授權移除信箱後它已移至所選的地理位置以使其回到停用狀態。

### <a name="create-new-cloud-mailboxes-in-a-specific-geo"></a>在特定地理位置中建立新的雲端信箱 
若要建立新的信箱中的特定地理位置，您需要執行這些步驟的任一項：

- 舊區段*之前*的信箱已建立在 Exchange Online 中所述，設定**PreferredDataLocation**值。例如，設定**PreferredDataLocation**值是以使用者之前將授權指派。 

- 將授權指派同時設定**PreferredDataLocation**值。

若要建立新僅限雲端授權的使用者 （不 AAD 連線同步處理） 中特定的地理位置，請 Azure AD PowerShell 中使用下列語法：

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
本範例會為伊莉莎白 Brunner 建立新的使用者帳戶具有下列值：

- 使用者主體名稱： ebrunner@contoso.onmicrosoft.com

- 名字： 伊莉莎白

- 姓氏： Brunner

- 顯示名稱伊莉莎白 Brunner

- 密碼： 隨機產生所示命令的結果 （因為我們未使用*Password*參數）

- 授權： contoso:ENTERPRISEPREMIUM (E5)

- 位置： 澳洲 （澳洲）

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

如需建立新的使用者帳戶和 Azure AD PowerShell 中尋找 LicenseAssignment 值的詳細資訊，請參閱[Office 365 PowerShell 建立使用者帳戶](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)和[檢視授權和 Office 365 powershell 的服務](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell)。

> **附註：** 如果您使用 Exchange Online PowerShell 啟用信箱並必須直接在所指定的**PreferredDataLocation**地理位置中建立信箱，您需要使用 Exchange Online 指令程式，如**啟用信箱**或**New-mailbox**直接對雲端服務。如果您使用**Enable-remotemailbox**內部部署 Exchange 指令程式，信箱會建立在預設的地理位置。

### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo"></a>設定現有的內建內部部署信箱的特定地理位置
您可以使用標準的 onboarding 工具與程序將信箱從內部部署 Exchange 組織移轉至 Exchange Online，包括[在 EAC 中的遷移儀表板](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)和[New-migrationbatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch)指令程式在 Exchange OnlinePowerShell。

第一個步驟是驗證的使用者物件存在是 onboarded，並確認正確的**PreferredDataLocation**值已設定在 Azure AD 的每個信箱。Onboarding 工具會來**PreferredDataLocation**值並將信箱遷移直接至指定的地理位置。

或者，您可以使用下列步驟以直接在 Exchange Online PowerShell 中使用[New-moverequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest)指令程式的特定地理位置中的內建信箱。

1. 確認每個信箱設為 onboarded 和**PreferredDataLocation**設為所需的值在 Azure AD 存在於使用者物件。**PreferredDataLocation**的值會同步處理至相對應的郵件使用者物件的**MailboxRegion**屬性在 Exchange Online。

2. 直接連接到特定的衛星連線指示從使用本主題中前面的地理位置。

3. 在 Exchange Online PowerShell 中儲存內部部署系統管理員認證是用以執行信箱移轉的變數中執行下列命令：

    ```
    $RC = Get-Credential
    ```

4. 在 Exchange Online PowerShell 中建立新的**New-moverequest**類似下列的範例： 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. 重複執行步驟 #4 您需要從內部部署 Exchange 移轉至衛星位置目前連線至每個信箱。

6. 如果您需要額外的信箱移轉至不同的衛星位置，請針對每個特定衛星位置重複步驟 2 到 4。

### <a name="multi-geo-reporting"></a>多個地理位置報告
在 Office 365 系統管理中心中的**多個地理位置流量報告**顯示依地理位置的使用者人數。報表會顯示目前月份的使用者通訊群組並提供過去 6 個月的歷程資料。
