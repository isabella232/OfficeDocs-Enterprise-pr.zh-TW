---
title: "指派個別使用者 Skype 線上商務原則與 Office 365 PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: 
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: "摘要： 使用 Office 365 PowerShell 指派個別使用者線上商務原則與 Skype 通訊設定。"
ms.openlocfilehash: 7f819b619c5b3607c98c10791fe30c3944e862a4
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2018
---
# <a name="assign-per-user-skype-for-business-online-policies-with-office-365-powershell"></a>指派個別使用者 Skype 線上商務原則與 Office 365 PowerShell

 **摘要：**使用 Office 365 PowerShell 指派個別使用者的通訊設定與 Skype 線上商務原則。
  
使用 Office 365 PowerShell 是要指派個別使用者線上商務原則與 Skype 通訊設定的有效方法。
  
## <a name="before-you-begin"></a>開始之前

使用這些指示來取得設定設定來執行命令 （略過您已經完成的步驟）：
  
1. 下載並安裝[Skype for Business Online 連接器模組](https://www.microsoft.com/en-us/download/details.aspx?id=39366)。
    
2. 開啟 Windows PowerShell 命令提示字元並執行下列命令： 
    
  ```
  Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```
出現提示時，輸入您 Skype 線上商務系統管理員帳戶名稱及密碼。
    
## <a name="updating-external-communication-settings-for-a-user-account"></a>更新使用者帳戶的外部通訊的設定

假設您想要變更的使用者帳戶上的外部通訊設定。例如，您要允許與同盟使用者 （EnableFederationAccess 等於 True），但不是與 （EnablePublicCloudAccess 等於 False） 的 Windows Live 的使用者進行通訊的 Alex。若要這樣做，您需要執行兩件事：
  
1. 尋找符合我們準則的外部存取原則。
    
2. 將該外部存取原則指派給 Alex。
    
> [!NOTE]
>  您無法建立所有的自訂原則我們自己。那是因為 Skype 商務 online 不允許您建立自訂原則。而是必須指派一個特別針對 Office 365 所建立的原則。這些預先建立的原則包含： 4 個不同的用戶端原則、 224 個不同的會議原則、 5 個不同的撥號計劃、 5 個不同的外部存取原則、 1 個託管語音信箱原則及 4 個不同的語音原則。
  
您要那要如何決定要指派 Alex 哪個外部存取原則？下列命令會傳回所有外部存取原則其中 EnableFederationAccess 設為 True，而 EnablePublicCloudAccess 設為 False：
  
```
Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

此命令的沒有會傳回所有符合兩個準則的原則： EnableFederationAccess 屬性設為 True，且 EnablePublicCloudAccess 原則設為 False。接著，該命令會傳回一個符合我們準則 (FederationOnly) 的原則。以下是範例：
  
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
> 原則 Identity 表示 Tag: FederationOnly。顯示出 Tag： 前置詞是從 Microsoft Lync 2013 已完成的最早發行前工作 carryover。若要將原則指派給使用者而言，您應該刪除 Tag： 首碼] 和 [使用只是原則名稱： FederationOnly。 
  
既然您知道哪個原則將指派給 alex 之後，我們可以使用[Grant-csexternalaccesspolicy](https://go.microsoft.com/fwlink/?LinkId=523974)指令程式來指派該原則。以下是範例：
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

指派原則是很簡單： 只要指定使用者的身分識別和原則的名稱指派。 
  
與原則和原則指派至而言，您不限於處理的使用者帳戶一次。例如，假設您需要的所有允許與同盟協力廠商及 Windows Live 使用者通訊的使用者清單。我們已經知道這些使用者所獲指派的外部使用者存取原則 FederationAndPICDefault。因為我們知道的您可以執行一個簡單的命令來顯示所有這些使用者的清單。以下是此命令：
  
```
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

換句話說，顯示我們的所有使用者所在的 externalaccesspolicy 才屬性設定為 FederationAndPICDefault。（和，以縮短顯示於螢幕上的資訊，請使用 Select-object 指令程式，以顯示顯示我們每位使用者的顯示名稱）。 
  
若要設定所有使用者帳戶使用該相同的原則，請使用此命令：
  
```
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

此命令會使用 Get-csonlineuser 來傳回已啟用 Lync，然後再將所有該資訊傳送到 Grant-csexternalaccesspolicy，此 FederationAndPICDefault 原則指派給集合中的每個使用者的所有使用者的集合。
  
做為額外的範例，假設您已先前指派給 Alex FederationAndPICDefault 原則和現在改變心意並想他變成由通用外部存取原則。您無法明確地將通用原則指派給任何人。它時才使用其他的個別使用者原則指派。因此，如果我們想 Alex 至變成由通用原則、 您要*取消指派*先前已指派給他的任何個別使用者原則。以下是範例命令：
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

此命令會設定為 null 值 ($Null) 指派給 Alex 的外部存取原則的名稱。Null 表示 「 不 」。換句話說，沒有外部存取原則指派給 Alex。當沒有外部存取原則指派給使用者時，該使用者，則取得管理通用原則。
  
若要停用使用 Windows PowerShell 的使用者帳戶，請使用 Azure Active Directory cmdlet 來移除 Alex 的 Skype 商務 Online 授權。如需詳細資訊，請參閱 ＜[停用 Office 365 powershell 的服務存取權](assign-licenses-to-user-accounts-with-office-365-powershell.md)。
  
## <a name="see-also"></a>另請參閱

#### 

[使用 Office 365 PowerShell 管理商務用 Skype Office](manage-skype-for-business-online-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)

