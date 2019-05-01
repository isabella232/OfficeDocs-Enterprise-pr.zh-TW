---
title: 指派個別使用者 Skype 線上商務原則與 Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: 摘要： 使用 Office 365 PowerShell 來指派個別使用者 Skype 線上商務原則通訊設定。
ms.openlocfilehash: 7f819b619c5b3607c98c10791fe30c3944e862a4
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33492019"
---
# <a name="assign-per-user-skype-for-business-online-policies-with-office-365-powershell"></a>指派個別使用者 Skype 線上商務原則與 Office 365 PowerShell

 **摘要：** 使用 Office 365 PowerShell 來指派個別使用者 Skype 線上商務原則通訊設定。
  
使用 Office 365 PowerShell 是要指派個別使用者 Skype 線上商務原則通訊設定的有效方法。
  
## <a name="before-you-begin"></a>開始之前

使用這些指示以取得設定，請執行命令 （略過您已經完成的步驟）：
  
1. 下載並安裝[商務用 Skype 商務 Online 連接器模組](https://www.microsoft.com/en-us/download/details.aspx?id=39366)。
    
2. 開啟 Windows PowerShell 命令提示字元並執行下列命令： 
    
  ```
  Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```
出現提示時，輸入您 Skype 商務 Online 系統管理員帳戶名稱和密碼。
    
## <a name="updating-external-communication-settings-for-a-user-account"></a>更新的使用者帳戶的外部通訊設定

假設您想要變更的使用者帳戶上的外部通訊設定。 例如，您想要允許 Alex 通訊與同盟使用者 （EnableFederationAccess 等於 True），但未與 Windows Live 的使用者 （EnablePublicCloudAccess 等於 False）。 若要這麼做，您必須執行下列兩件事：
  
1. 尋找符合我們準則的外部存取原則。
    
2. 將該外部存取原則指派給 Alex。
    
> [!NOTE]
>  您無法建立所有的自訂原則我們自己。 這是因為 Skype for Business Online 不允許您建立自訂原則。 相反地，您必須指派其中一個特別針對 Office 365 所建立的原則。 預先建立原則包含： 4 個不同的用戶端原則、 224 不同的會議原則、 5 個不同撥號對應表、 5 個不同的外部存取原則、 1 個託管語音信箱原則，以及 4 個不同的語音原則。
  
您要如何判斷哪個外部存取原則指派 Alex？ 下列命令會傳回 EnableFederationAccess 設定為 True 且 EnablePublicCloudAccess 設定為 False 的所有外部存取原則：
  
```
Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

此命令的作用是傳回所有符合這兩項條件的原則： EnableFederationAccess 屬性設為 True，且 EnablePublicCloudAccess 原則設為 False。 接著，該命令會傳回一個符合我們準則 (FederationOnly) 的原則。 範例如下：
  
```
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

> [!NOTE]
> 原則 Identity 說標記： FederationOnly。 的確，Tag:前置詞沿襲自 Microsoft Lync 2013 已完成的發行前版本。 要將原則指派給使用者時，您應該刪除 Tag:前置詞，且直接使用原則名稱：FederationOnly。 
  
既然您知道哪個原則將指派給 alex 之後，我們可以使用[Grant-csexternalaccesspolicy](https://go.microsoft.com/fwlink/?LinkId=523974) cmdlet 指派該原則。 範例如下：
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

指派原則是很簡單： 只要指定使用者的身分識別和原則的名稱指派給。 
  
及過濾原則和原則工作分派的範例，您不限於運用使用者帳戶一次。 例如，假設您需要可與同盟夥伴和 Windows Live 使用者進行通訊的所有使用者清單。 我們已經知道這些使用者均被指派外部使用者存取原則 FederationAndPICDefault。 由於我們知道，，您可以執行一個簡單的命令來顯示所有這些使用者的清單。 命令如下：
  
```
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

換句話說，告訴我們所有的使用者所在的 ExternalAccessPolicy 屬性設為 FederationAndPICDefault。 （和，以縮短螢幕上所顯示的資訊，請使用 Select-object cmdlet 來顯示告訴我們每位使用者的顯示名稱）。 
  
若要設定所有使用者帳戶使用相同的原則，請使用此命令：
  
```
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

這個命令會使用 Get-csonlineuser 傳回的所有使用者都已啟用 Lync，然後將所有該資訊傳送至 Grant-csexternalaccesspolicy，它會 FederationAndPICDefault 原則指派給集合中的每個使用者的集合。
  
做為其他範例，假設您已先前指派給 Alex FederationAndPICDefault 原則，現在您改變心意，但想他由全域外部存取原則來管理。 您明確不能將全域原則指派給任何人。 只有在不指派任何其他的個別使用者原則時，它才會使用。 因此，如果我們想要由全域原則來管理 alex 之後，您必須*取消指派*先前已指派給他任何個別使用者原則。 範例命令如下：
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

此命令會設定設為 null 值 ($Null) 指派給 alex 之後的外部存取原則的名稱。 Null 表示"nothing"。 換句話說，任何外部存取原則不指派給 alex 之後。 沒有外部存取原則指派給使用者後，該使用者再取得管理由全域原則。
  
若要停用使用 Windows PowerShell 的使用者帳戶，請使用 Azure Active Directory 指令程式來移除 Alex Skype for Business Online 授權。 如需詳細資訊，請參閱[停用 Office 365 PowerShell 與服務存取權](assign-licenses-to-user-accounts-with-office-365-powershell.md)。
  
## <a name="see-also"></a>另請參閱

#### 

[使用 Office 365 PowerShell 管理商務用 Skype Online](manage-skype-for-business-online-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)

