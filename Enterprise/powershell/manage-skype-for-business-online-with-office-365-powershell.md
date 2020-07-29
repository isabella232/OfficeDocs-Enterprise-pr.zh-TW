---
title: 使用 PowerShell 管理商務用 Skype Online
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 摘要：使用 Microsoft 365 PowerShell 來管理商務用 Skype Online 原則、每一使用者原則和會議設定。
ms.openlocfilehash: 0701fdb8a0a1f588e1c113ad7050ed516638aebc
ms.sourcegitcommit: d9abb99b336170f07b8f3f6d00fac19ad2159d3a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "46502608"
---
# <a name="manage-skype-for-business-online-with-powershell"></a>使用 PowerShell 管理商務用 Skype Online

*本文適用於 Microsoft 365 企業版和 Office 365 企業版。*

任何 商務用 Skype Online 系統管理員的其中一個主要工作是管理原則。 雖然您可以在 Microsoft 365 系統管理中心中完成一些工作，但在 PowerShell 中，其他工作會更快速且更容易。 

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
  
- [使用 PowerShell 管理商務用 Skype Online 原則](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [將每一使用者商務用 Skype Online 原則指派給 PowerShell](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a>另請參閱

[使用 PowerShell 管理 Microsoft 365](manage-office-365-with-office-365-powershell.md)
  
[開始使用適用於 Microsoft 365 的 PowerShell](getting-started-with-office-365-powershell.md)

[商務用 Skype PowerShell Cmdlet 參考](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

