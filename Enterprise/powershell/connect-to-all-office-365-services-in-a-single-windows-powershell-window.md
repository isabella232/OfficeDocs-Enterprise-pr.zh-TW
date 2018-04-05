---
title: 在單一 Windows PowerShell 視窗中連線至所有 Office 365 服務
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/04/2018
ms.audience: ITPro
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
description: 摘要： 連線至單一 Windows PowerShell 視窗中的所有 Office 365 服務的 Windows PowerShell。
ms.openlocfilehash: ccd8ed1dc53d306aa77d79ac0270f5bd24dd9298
ms.sourcegitcommit: 21cc62118b78b76d16ef12e2c3eff2c0c789e3d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2018
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a>在單一 Windows PowerShell 視窗中連線至所有 Office 365 服務

 **摘要：**而不是管理在個別的 PowerShell 主控台視窗中的不同 Office 365 服務，您可以連線至 Office 365 的所有服務和管理它們從單一主控台視窗。
  
當您使用 PowerShell 管理 Office 365 時，有可能有最多可以有五個不同 Windows PowerShell 工作階段，同時對應至 Office 365 系統管理中心、 SharePoint Online、 Exchange Online、 商務 online Skype 及安全性&amp;規範中心。使用個別的 Windows PowerShell 工作階段中的五個不同的連接方法，您的桌面可能看起來如下：
  
![一次執行五個 Windows PowerShell 主控台](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
這不是因為您不能交換資料之間的跨服務管理那些五個 windows 管理 Office 365 的最佳。本主題說明如何使用單一執行個體您可以從中管理 Office 365、 商務 Online、 Exchange Online、 SharePoint online、 Skype 和安全性的 Windows PowerShell&amp;規範中心。

>[!Note]
>本文是程序正在更新，以使用 Azure Active Directory V2 PowerShell 模組及多重要素驗證 (MFA)。
>
  
## <a name="before-you-begin"></a>開始之前
<a name="BeforeYouBegin"> </a>

您可以從單一執行個體的 Windows PowerShell 管理 Office 365 的所有之前，請考慮下列先決條件：
  
- Office 365 搭配使用或學校您使用這些程序需求是 Office 365 系統管理員角色成員的帳戶。如需詳細資訊，請參閱 ＜[關於 Office 365 系統管理員角色](https://go.microsoft.com/fwlink/p/?LinkId=532367)。此為 Office 365 PowerShell、 不一定所有其他 Office 365 服務的需求。
    
- 您可以使用下列 Windows 64 位元版本：
    
  - Windows 10
    
  - Windows 8.1 或 Windows 8
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 或 Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    * 您需要安裝 Microsoft.NET Framework 4.5。*x* ，然後任一 Windows Management Framework 3.0 或 Windows Management Framework 4.0。如需詳細資訊，請參閱[安裝.NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868)和[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757)或[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)。
    
    您需要用於 64 位元版本的 Windows 因為 Skype 的需求而商務線上模組及其中一個 Office 365 模組。
    
- 您必須安裝所需的 Office 365、 SharePoint Online 和 Skype 的商務 Online 模組：
    
   - [Microsoft Online Services 登入小幫手，適用於 IT 專業人員 RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152)
   - Windows Azure Active Directory Module for Windows PowerShell （64 位元版本） 具有較高的 PowerShell 命令提示字元處**安裝模組 MSOnline**命令。
   - [SharePoint Online 管理命令介面](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [Skype Online，企業版 Windows PowerShell 模組](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  Windows PowerShell 需要為 Skype 的已簽署的指令碼執行商務 Online、 Exchange Online 與安全性設定&amp;規範中心。若要這樣做，請執行下列命令在提升權限的 Windows PowerShell 工作階段 （您可以選取 [**執行系統管理員身分**開啟 Windows PowerShell 視窗）。
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps"></a>連線步驟
<a name="BeforeYouBegin"> </a>

以下是連線至單一 PowerShell 視窗中的所有服務的步驟。
  
1. （使用**系統管理員身分執行**） 以管理員身分開啟 Windows PowerShell。
    
2. 執行此命令中，並輸入您的 Office 365 工作或學校帳戶認證。
    
  ```
  $credential = Get-Credential
  ```

3. 執行下列命令以連線至 Office 365。
    
  ```
  Import-Module MsOnline
  Connect-MsolService -Credential $credential
  ```

4. 執行下列命令以連接至 SharePoint Online。取代_\<domainhost >_網域的實際值。例如，用於`litwareinc.onmicrosoft.com`、 _ \<domainhost >_值是`litwareinc`。
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. 執行下列命令以連線至 Skype 商務線上。增加的警告`WSMan NetworkDelayms`值預期會在第一次連線和應忽略。
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. 執行下列命令以連線至 Exchange Online。
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

7. 執行下列命令以連線至安全性&amp;規範中心。
    
  ```
  $ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
  Import-PSSession $ccSession -Prefix cc
  ```
> [!NOTE]
> 文字前置詞"cc"新增至*所有*安全性&amp;規範中心指令程式名稱，可以執行指令程式可讓存在於 Exchange Online 與安全性&amp;規範中心] 中相同的 Windows PowerShell 工作階段。例如， **Get-rolegroup**變成**Get ccRoleGroup**安全性&amp;規範中心。
  
以下是單一區塊中的所有命令。指定您的網域主機名稱和一次執行所有它們。
  
```
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Import-Module MsOnline
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
Import-PSSession $ccSession -Prefix cc
```
當您準備好關閉 Windows PowerShell 視窗時，執行此命令以移除 Skype 作用中的工作階段的商務 Online、 Exchange Online、 SharePoint Online 和安全性&amp;規範中心：
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $ccSession ; Disconnect-SPOService
```

## <a name="new-to-office-365"></a>初次使用 Office 365 嗎？
<a name="LongVersion"> </a>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>另請參閱

- [使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
- [開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)
- [使用 Office 365 PowerShell 管理 SharePoint Online](manage-sharepoint-online-with-office-365-powershell.md)
- [使用 Office 365 PowerShell 管理使用者帳戶](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [使用 Windows PowerShell 在 Office 365 中建立報告](use-windows-powershell-to-create-reports-in-office-365.md)
