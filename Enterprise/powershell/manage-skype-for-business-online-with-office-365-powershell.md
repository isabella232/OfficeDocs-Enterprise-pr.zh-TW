---
title: 使用 Office 365 PowerShell 管理商務用 Skype Office
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/28/2018
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 摘要︰使用 Office 365 PowerShell 來管理 商務用 Skype Online 原則、每一使用者原則和會議的設定。
ms.openlocfilehash: f1a5df3802d43755e81465743b81c5fbb9fff7e0
ms.sourcegitcommit: 6c7cc6aca8713e280ae6ff51226dde9db4497401
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "44415935"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a>使用 Office 365 PowerShell 管理商務用 Skype Office

任何 商務用 Skype Online 系統管理員的其中一個主要工作是管理原則。 雖然您可以在 Microsoft 365 系統管理中心中完成其中一些工作，但是使用 Office 365 PowerShell 可以更快速、更輕鬆地完成其他工作。 

## <a name="before-you-start"></a>開始之前

下載並安裝[商務用 Skype Online 連接器模組](https://www.microsoft.com/download/details.aspx?id=39366)，然後重新開機您的電腦。


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a>使用商務用 Skype Online 系統管理員帳戶名稱和密碼進行連接

1. 開啟 Windows PowerShell 命令提示字元，並執行下列命令： 
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. 在 [ **Windows PowerShell 憑證要求**] 對話方塊中，輸入您的商務用 Skype Online 系統管理員帳戶名稱和密碼，然後按一下 **[確定]**。


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multi-factor-authentication"></a>使用含多重要素驗證的商務用 Skype Online 系統管理員帳戶進行連線

1. 開啟 Windows PowerShell 命令提示字元，並執行下列命令：

  ```powershell
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. 當**CsOnlineSession**命令提示時，請輸入您的商務用 Skype Online 系統管理員帳戶名稱。

3. 在 [登**入您的帳戶**] 對話方塊中，輸入您的商務用 Skype Online 系統管理員密碼，然後按一下 [登**入**]。

4. 依照 [登**入您的帳戶**] 對話方塊中的指示，提供其他驗證資訊（例如驗證碼），然後按一下 [**驗證**]。

如需詳細資訊，請參閱下列主題：
  
- [線上商務原則與 Office 365 PowerShell 管理 Skype](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [指派個別使用者 Skype 線上商務原則與 Office 365 PowerShell](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a>另請參閱

[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)

[商務用 Skype PowerShell Cmdlet 參考](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

