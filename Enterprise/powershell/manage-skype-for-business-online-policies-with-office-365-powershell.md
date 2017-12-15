---
title: "線上商務原則與 Office 365 PowerShell 管理 Skype"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: "摘要： 使用 Office 365 PowerShell 來管理您 Skype 商務線上與原則的使用者帳戶屬性。"
ms.openlocfilehash: 9b3877d2680b2b36d155cb5dd2a69fa21c972fe3
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="manage-skype-for-business-online-policies-with-office-365-powershell"></a>線上商務原則與 Office 365 PowerShell 管理 Skype

 **摘要：**使用 Office 365 PowerShell 來管理您 Skype 商務線上與原則的使用者帳戶屬性。
  
商務 online 中管理 Skype 的使用者帳戶的許多屬性，則必須將其指定為原則與 Office 365 PowerShell 的屬性。
  
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
    
## <a name="manage-user-account-policies"></a>管理使用者帳戶原則

使用原則來設定許多 Skype 商務線上的使用者帳戶屬性。原則是只可套用至一或多個使用者的設定集合。若要看看如何設定的原則，您可以執行此命令範例 FederationAndPICDefault 原則：
  
```
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

接著，您應該會得到類似：
  
```
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

在這個範例中，此原則內的數值決定使用的可以或無法執行專職與同盟使用者進行通訊的作業。例如，EnableOutsideAccess 屬性必須設定為 True 的使用者能夠與組織外部的人員通訊。請注意，這個屬性不會出現在 Office 365 系統管理中心。而屬性會自動設為 True 或 False 根據所做的選擇。會感興趣的其他兩個屬性：
  
- **EnableFederationAccess**指出使用者是否可以與來自同盟網域的人通訊。
    
- **EnablePublicCloudAccess**指出使用者是否可以與 Windows Live 使用者進行通訊。
    
因此，您不直接變更的使用者帳戶 (例如， **Set-csuser-EnableFederationAccess $True**) 上的同盟相關屬性。而是您指派帳戶已預先設定的所需的屬性值的外部存取原則。如果我們希望使用者能夠與同盟使用者及 Windows Live 使用者通訊，該使用者帳戶必須被指派可讓通訊這些類型的原則。
  
如果您想要知道某人可與組織外部的使用者通訊，您必須：
  
- 判斷已指派哪個外部存取原則給該使用者。
    
- 判斷該原則允許或不允許哪些功能。
    
例如，您可以使用此命令執行的：
  
```
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

此命令會找出指派給使用者，則會找出功能已啟用或停用該原則內的原則。
  
請注意任何 cmdlet 建立或修改的原則。您必須使用前 Office 365 所提供的原則。如果您想要查看如何在不同的原則，您可以使用下列命令：
  
- Get-csclientpolicy       
- Get-csconferencingpolicy        
- Get-csdialplan            
- Get-csexternalaccesspolicy                         
- Get-cshostedvoicemailpolicy                        
- Get-cspresencepolicy                               
- Get-csvoicepolicy                                  

> [!NOTE]
> 線上商務撥號 Skype 是在每個方面除了名稱的原則。名稱"撥號對應表"的選擇而不是，假設"撥號原則 」 以使用 Office Communications Server 與 Exchange 提供回溯相容性。 
  
例如，若要查看所有可供您使用的語音原則執行此命令：
  
```
Get-CsVoicePolicy
```

> [!NOTE]
> 會傳回所有語音原則清單提供給您。請記住，但不是所有原則可以指派給所有使用者。這是因為各種有關授權和地理位置的限制。（所謂 」 的[使用狀況位置](https://msdn.microsoft.com/en-us/library/azure/dn194136.aspx)。"）如果您想要知道的外部存取原則及可以指派給特定使用者的會議原則、 使用類似以下的命令： 

```
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

[ApplicableTo] 參數會對可指派給特定使用者 (例如，Alex Darrow) 的原則限制傳回的資料。根據授權及使用位置的限制，這可能代表所有可用原則的子集。 
  
在某些情況下，屬性的原則不使用 Office 365 時其他人只能管理 Microsoft 支援人員。 
  
具有商務 online Skype，使用者還必須管理某種類型的原則影響。如果是有效的原則相關屬性是空白的這表示有問題的使用者會受全域原則，這是除非他就會指派個別使用者原則會自動套用到使用者的原則。因為我們未看見列出的使用者帳戶的用戶端原則，它會由通用原則管理。您可以決定此命令的通用用戶端原則：
  
```
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a>See also

#### 

[使用 Office 365 PowerShell 管理商務用 Skype Office](manage-skype-for-business-online-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)

