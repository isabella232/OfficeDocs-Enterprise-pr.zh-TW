---
title: 使用 Office 365 PowerShell 管理商務用 Skype Office
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/13/2018
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 摘要︰使用 Office 365 PowerShell 來管理 商務用 Skype Online 原則、每一使用者原則和會議的設定。
ms.openlocfilehash: a91803316972337aa31e2b979f841ac1cfbe8566
ms.sourcegitcommit: 053db5479f93478a65d4c36ffe44c6a7bcb60e3c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "23965190"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a>使用 Office 365 PowerShell 管理商務用 Skype Office

 **摘要︰** 使用 Office 365 PowerShell 來管理 商務用 Skype Online 原則、每一使用者原則和會議的設定。
  
其中一個主要商務 Online 管理員任何 Skype 工作管理原則。雖然您可以完成這些工作在 Office 365 系統管理中心，其他工作會更加更快速且更輕鬆地在 Office 365 PowerShell。 

## <a name="before-you-start"></a>開始之前

下載並安裝[Skype for Business Online 連接器模組](https://www.microsoft.com/en-us/download/details.aspx?id=39366)，並再如果系統提示重新啟動電腦。


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a>使用 Skype 線上商務系統管理員帳戶名稱及密碼的連線

1. 開啟 Windows PowerShell 命令提示字元並執行下列命令： 
    
  ```
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. 在**Windows PowerShell 認證要求**] 對話方塊中，輸入 Business Online 系統管理員帳戶名稱和密碼，您 Skype，然後按一下 [**確定]**。


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a>使用 Skype 與多重要素驗證商務 Online 管理員帳戶的連線

1. 開啟 Windows PowerShell 命令提示字元並執行下列命令：

  ```
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. 當系統提示**新增 CsOnlineSession**命令，請輸入您 Skype 線上商務系統管理員帳戶名稱。

3. 在**您的帳戶登入**] 對話方塊中，輸入您的業務 Online 系統管理員密碼，Skype 和 [**登入**。

4. 依照**您的帳戶登入**] 對話方塊中的指示以提供額外的驗證資訊，例如驗證碼，並再按一下 [**驗證**。

如需詳細資訊，請參閱下列主題：
  
- [線上商務原則與 Office 365 PowerShell 管理 Skype](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [指派個別使用者 Skype 線上商務原則與 Office 365 PowerShell](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a>另請參閱

[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)

[Skype 商務 PowerShell cmdlet 參考](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

