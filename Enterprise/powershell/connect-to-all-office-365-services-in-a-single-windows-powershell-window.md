---
title: 在單一 Windows PowerShell 視窗中連線至所有 Office 365 服務
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: 摘要：將 Windows PowerShell 連線到單一 Windows PowerShell 視窗中的所有 Office 365 服務。
ms.openlocfilehash: 47fd2be814b446cf12b136e359cdadc9374a7ab6
ms.sourcegitcommit: dce58576a61f2c8efba98657b3f6e277a12a3a7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "44208804"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a>在單一 Windows PowerShell 視窗中連線至所有 Office 365 服務

當您使用 PowerShell 來管理 Office 365 時，最多可以同時開啟五個不同的 Windows PowerShell 會話，其對應于 Microsoft 365 系統管理中心、SharePoint 線上、Exchange Online、商務用 Skype Online、Microsoft 團隊及安全性與 &amp; 合規性中心。 您的桌面可以在不同的 Windows PowerShell 會話中使用五種不同的連接方法，如下所示：
  
![一次執行五個 Windows PowerShell 主控台](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
這在管理 Office 365 時並不是最佳的，因為您無法在這五個 windows 間交換資料，以進行跨服務管理。 本主題說明如何使用單一 Windows PowerShell 實例，從中管理 Office 365、商務用 Skype Online、Exchange Online、SharePoint 線上、Microsoft 團隊及安全性與 &amp; 合規性中心。

>[!Note]
>本文目前只包含連接到 Office 365 全球（+ GCC）雲端的命令。 其他附注提供與其他 Office 365 雲端相關之相關資訊的文章連結。
>

## <a name="before-you-begin"></a>開始之前

在您可以從單一 Windows PowerShell 實例管理所有 Office 365 之前，請考慮下列必要條件：
  
- 您用於這些程序的 Office 365工作或學校帳戶 必須是 Office 365 系統管理員角色的成員。 如需詳細資訊，請參閱[關於 Office 365 系統管理員角色](https://go.microsoft.com/fwlink/p/?LinkId=532367)。 這是 Office 365 PowerShell 的需求，不一定是所有其他 Office 365 服務。
    
- 您可以使用下列 Windows 64 位元版本：
    
  - Windows 10
    
  - Windows 8.1 或 Windows 8
    
  - Windows Server 2019
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 或 Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    \*您必須安裝 Microsoft .NET Framework 4.5。*x* ，然後是 Windows management framework 3.0 或 Windows management framework 4.0。 如需詳細資訊，請參閱[安裝 .Net Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868)和[windows management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757)或[windows management framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)。
    
    您必須使用64位版本的 Windows，因為商務用 Skype Online 模組和其中一個 Office 365 模組的需求。
    
- 您需要安裝 Azure Active Directory （Azure AD）、Exchange Online、SharePoint 線上、商務用 Skype Online 及小組所需的模組：
    
   - [Azure Active Directory V2](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [SharePoint 線上管理命令介面](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [商務用 Skype Online、Windows PowerShell 模組](https://go.microsoft.com/fwlink/p/?LinkId=532439)
   - [Exchange Online PowerShell V2](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell-v2/exchange-online-powershell-v2?view=exchange-ps#install-and-maintain-the-exchange-online-powershell-v2-module)
   - [小組 PowerShell 概述](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
    
-  Windows PowerShell 必須設定為為商務用 Skype Online 和安全性與合規性中心執行已簽署的腳本 &amp; 。 若要這麼做，請在已提升許可權的 Windows PowerShell 會話中執行下列命令（您可以選取 [以**系統管理員身分執行**] 視窗 PowerShell 視窗）。
    
  ```powershell
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a>使用密碼時的連接步驟

以下是連接至單一 PowerShell 視窗中所有服務的步驟。
  
1. 開啟 [Windows PowerShell]。
    
2. 執行這個命令，並輸入您的 Office 365 工作或學校帳號憑證。
    
  ```powershell
  $credential = Get-Credential
  ```

3. 使用此命令，使用適用于 Graph 模組的 Azure Active Directory PowerShell，連接至 Azure AD。
    
  ```powershell
  Connect-AzureAD -Credential $credential
  ```
  
  或者，如果您是使用 Microsoft Azure Active Directory Module for Windows PowerShell module，請執行此命令。
      
  ```powershell
  Connect-MsolService -Credential $credential
 ```

>[!Note]
>PowerShell Core 不支援適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組和名稱有 **Msol** 的 Cmdlet。 若要繼續使用這些 Cmdlet，您必須從 Windows PowerShell 執行。
>

4. 執行這些命令，以連線至 SharePoint 線上。 以您的網域的實際值取代_ \< domainhost>_ 。 例如，若為 "litwareinc.onmicrosoft.com"，則_ \< domainhost>_ 值為 "litwareinc"。
    
  ```powershell
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. 執行這些命令，以連線至商務用 Skype Online。 `WSMan NetworkDelayms`您第一次連線時預計會增加值，而且應該忽略此警告。
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. 執行下列命令以連線至 Exchange Online。
    
  ```powershell
  Connect-ExchangeOnline -Credential $credential -ShowProgress $true
  ```

>[!Note]
>若要連接至全球以外的 Office 365 雲端的 Exchange Online，請使用 **-ExchangeEnvironmentName**參數。 如需詳細資訊，請參閱[Connect-ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps) 。
>

7. 執行這些命令，以連線至小組 PowerShell。
    
  ```powershell
  Import-Module MicrosoftTeams
  Connect-MicrosoftTeams -Credential $credential
  ```
  
>[!Note]
>若要連線至全球以外的 Microsoft 團隊雲彩，請參閱[MicrosoftTeams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps)。
>

8. 執行這些命令，以連線至安全性與 &amp; 合規性中心。
    
  ```powershell
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
>若要連接至全球以外的 Office 365 雲端的安全性與 &amp; 合規性中心，請參閱[Connect to Office 365 Security & 合規性中心 PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell)。
>

以下是使用適用于 Graph 模組的 Azure Active Directory PowerShell 時，單一區塊中的所有命令。 指定您的功能變數名稱主機名稱稱，然後一次執行一次。
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
Connect-ExchangeOnline -Credential $credential -ShowProgress $true
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

此外，在使用 Microsoft Azure Active Directory Module for Windows PowerShell Module 時，以下是單一區塊中的所有命令。 指定您的功能變數名稱主機名稱稱，然後一次執行一次。
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
Connect-ExchangeOnline -Credential $credential -ShowProgress $true
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

當您準備好關閉 [Windows PowerShell] 視窗時，請執行下列命令，以移除使用中的商務用 Skype Online、SharePoint 線上、安全性與 &amp; 合規性中心及小組的會話：
  
```powershell
Remove-PSSession $sfboSession ; Remove-PSSession $SccSession ; Disconnect-SPOService ; Disconnect-MicrosoftTeams 
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a>使用多重要素驗證時的連接步驟

以下是單一區塊中的所有命令，可透過使用圖形模組之 Azure Active Directory PowerShell，在單一視窗中使用多重要素驗證連線至 Azure AD、SharePoint 線上、商務用 Skype、Exchange Online 和團隊。 指定使用者帳戶的使用者主要名稱（UPN）名稱和您的網域主機名稱，然後一次執行全部。

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
#Exchange Online
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Teams
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

或者，您也可以使用 Microsoft Azure Active Directory Module for Windows PowerShell module] 模組時使用的所有命令。

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
#Exchange Online
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Teams
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

如需安全 &amp; 規範中心，請參閱[Connect to Office 365 Security & 合規性中心 PowerShell 使用多重要素驗證](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)連線以使用多重要素驗證：

## <a name="see-also"></a>另請參閱

- [連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)
- [使用 Office 365 PowerShell 管理 SharePoint Online](manage-sharepoint-online-with-office-365-powershell.md)
- [使用 Office 365 管理使用者帳戶、授權和群組 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [使用 Windows PowerShell 在 Office 365 中建立報告](use-windows-powershell-to-create-reports-in-office-365.md)
