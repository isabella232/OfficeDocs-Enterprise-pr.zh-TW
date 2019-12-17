---
title: 在單一 Windows PowerShell 視窗中連線至所有 Office 365 服務
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/13/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: 摘要： 將 Windows PowerShell 連線到單一的 Windows PowerShell 視窗中的所有 Office 365 服務。
ms.openlocfilehash: ec24914367450e4ff464b3399be9cb2e626dd254
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072505"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a>在單一 Windows PowerShell 視窗中連線至所有 Office 365 服務

當您使用 PowerShell 來管理 Office 365 時，它可能會有最多可以有五個不同 Windows PowerShell 工作階段開啟對應至 Microsoft 365 系統管理中心、 SharePoint Online、 Exchange Online、 商務用 Skype 線上商務和安全性，同時&amp;合規性中心。 使用個別的 Windows PowerShell 工作階段中的五個不同的連線方法，您的桌面可能看起來像這樣：
  
![一次執行五個 Windows PowerShell 主控台](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
這不是最佳的管理 Office 365，因為您不能交換跨服務管理這些五個視窗之間的資料。 本主題說明如何使用 Office 365、 Skype for Business Online、 Exchange Online、 SharePoint Online 和安全性，您可以管理的 Windows PowerShell 的單一執行個體&amp;合規性中心。

>[!Note]
>目前本文僅包含命令，以連線至 Office 365 全球 （+ GCC） 雲端。 其他附註提供連線至其他 Office 365 定域機組的相關資訊的文章連結。
>

## <a name="before-you-begin"></a>開始之前

您可以從 Windows PowerShell 的單一執行個體管理所有 Office 365 之前，請考慮下列必要條件：
  
- 您用於這些程序的 Office 365工作或學校帳戶 必須是 Office 365 系統管理員角色的成員。 如需詳細資訊，請參閱[關於 Office 365 系統管理員角色](https://go.microsoft.com/fwlink/p/?LinkId=532367)。 此 Office 365 powershell，不一定所有其他 Office 365 服務的需求。
    
- 您可以使用下列 Windows 64 位元版本：
    
  - Windows 10
    
  - Windows 8.1 或 Windows 8
    
  - Windows Server 2019
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 或 Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    \*您必須安裝 Microsoft.NET Framework 4.5。*x* ，然後任一 Windows Management Framework 3.0 或 Windows Management Framework 4.0。 如需詳細資訊，請參閱[安裝.NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868)及[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757)或[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)。
    
    您要用於 64 位元版本的 Windows 因為 skype 需求商務 Online 模組和其中一個 Office 365 模組。
    
- 您必須安裝 Azure ad，所需的模組 SharePoint Online 和商務用 Skype:
    
   - [Azure Active Directory V2](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [SharePoint Online 管理命令介面](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [商務用 Skype Online、 商務 Windows PowerShell 模組](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  Windows PowerShell 需要執行簽署的指令碼 skype 商務 Online、 Exchange Online 和安全性設定&amp;合規性中心。 若要這麼做，請在提高權限的 Windows PowerShell 工作階段中執行下列命令 （您選取 [**執行系統管理員身分**開啟 Windows PowerShell 視窗）。
    
  ```powershell
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a>連線步驟時使用的密碼

以下是步驟來連接至單一 PowerShell 視窗中的所有服務。
  
1. 開啟 Windows PowerShell 以系統管理員身分 （使用**系統管理員身分執行**）。
    
2. 執行此命令，並輸入您的 Office 365 工作或學校帳戶認證。
    
  ```powershell
  $credential = Get-Credential
  ```

3. 執行此命令來連接至 Azure Active Directory (AD) 針對 Graph 模組中使用 PowerShell 的 Azure Active Directory。
    
  ```powershell
  Connect-AzureAD -Credential $credential
  ```
  
  或者，如果您使用 Microsoft Azure Active Directory 模組的 Windows PowerShell 模組，執行此命令。
      
  ```powershell
  Connect-MsolService -Credential $credential
 ```

>[!Note]
>PowerShell Core 不支援適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組和名稱有 **Msol** 的 Cmdlet。 若要繼續使用這些 Cmdlet，您必須從 Windows PowerShell 執行。
>

4. 執行這些命令，以連線至 SharePoint Online。 取代_\<domainhost>_ 與您的網域的實際值。 例如，針對 「 litwareinc.onmicrosoft.com 「 _ \<domainhost>_ 值是 「 litwareinc 」。
    
  ```powershell
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. 執行這些命令，以連線至 Skype for Business Online。 關於增加的警告`WSMan NetworkDelayms`值預期會在第一次連線並應忽略。
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. 執行這些命令，以連線至 Exchange Online。
    
  ```powershell
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

>[!Note]
>若要連線至 Exchange Online for Office 365 定域機組以外的全球網站，請參閱[Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)。
>

7. 執行這些命令，以連線至安全性&amp;合規性中心。
    
  ```powershell
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
>若要連接到安全性&amp;合規性中心的 Office 365 clouds 以外全球網站，請參閱[連線到 Office 365 安全性 & 合規性中心 PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell)。
>

針對 Graph 模組中使用 PowerShell 的 Azure Active Directory 時，以下是在單一區塊中的所有命令。 指定您的網域主機名稱，然後再一次執行全部。
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

或者，以下是所有命令在單一區塊時使用 Microsoft Azure Active Directory 模組的 Windows PowerShell 模組。 指定您的網域主機名稱，然後再一次執行全部。
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

當您準備好要關閉 Windows PowerShell 視窗時，執行此命令可移除使用中的工作階段 skype for Business Online、 Exchange Online、 SharePoint Online 和安全性&amp;合規性中心：
  
```powershell
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a>連線步驟時使用多重要素驗證

以下是在單一的區塊，以連線到 Azure AD 中的 [所有命令 SharePoint Online 和商務用 Skype Buiness 針對 Graph 模組中使用 PowerShell 的 Azure Active Directory 在單一視窗中使用多重要素驗證。 指定的使用者帳戶的使用者主要名稱 (UPN) 名稱與您的網域主機名稱，然後再一次執行全部。

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
```

或者，以下是所有命令時使用 Microsoft Azure Active Directory 模組的 Windows PowerShell 模組。

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
```

Exchange Online 和安全性&amp;合規性中心，請參閱下列主題，以使用多重要素驗證連線：

- [使用多重要素驗證連線至 Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell)
- [連線至 Office 365 安全性 & 合規性中心 PowerShell 中使用多重要素驗證](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
請注意，在這兩種情況下，您必須使用不同的工作階段的 Exchange Online 遠端 PowerShell 模組來連線。


## <a name="see-also"></a>另請參閱

- [連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)
- [使用 Office 365 PowerShell 管理 SharePoint Online](manage-sharepoint-online-with-office-365-powershell.md)
- [管理使用者帳戶、 授權及使用 Office 365 PowerShell 的群組](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [使用 Windows PowerShell 在 Office 365 中建立報告](use-windows-powershell-to-create-reports-in-office-365.md)
