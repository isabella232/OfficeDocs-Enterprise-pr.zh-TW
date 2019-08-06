---
title: 線上商務原則與 Office 365 PowerShell 管理 Skype
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/26/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: 摘要： 使用 Office 365 PowerShell 來管理您的 Skype 線上商務原則的使用者帳戶內容。
ms.openlocfilehash: ed09b117d2de805e2ae28f05d734ced303db2405
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2019
ms.locfileid: "35782593"
---
# <a name="manage-skype-for-business-online-policies-with-office-365-powershell"></a>線上商務原則與 Office 365 PowerShell 管理 Skype

 **摘要：** 使用 Office 365 PowerShell 來管理您的 Skype 線上商務原則的使用者帳戶內容。
  
若要管理商務用 Skype 使用者帳戶的許多屬性，您必須將它們指定為屬性的原則與 Office 365 PowerShell。
  
## <a name="before-you-begin"></a>開始之前

使用這些指示以取得設定，請執行命令 （略過您已經完成的步驟）：
  
1. 下載並安裝[商務用 Skype 商務 Online 連接器模組](https://www.microsoft.com/download/details.aspx?id=39366)。
    
2. 開啟 Windows PowerShell 命令提示字元並執行下列命令： 
    
```
Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```

出現提示時，輸入您 Skype 商務 Online 系統管理員帳戶名稱和密碼。
    
## <a name="manage-user-account-policies"></a>管理使用者帳戶原則

許多 Skype for Business Online 的使用者帳戶屬性會設定使用原則。 原則是只可套用至一或多個使用者的設定集合。 若要查看如何原則已設定，您可以執行此範例命令，FederationAndPICDefault 原則：
  
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

在這個範例中，此原則內的值會判斷使用可以或提到與同盟使用者進行通訊時，無法執行。 例如，EnableOutsideAccess 屬性必須設為 True，使用者能夠與組織外的人員進行通訊。 請注意，此屬性不會出現在 Microsoft 365 系統管理中心。 相反地，屬性會自動設為 True 或 False 基於其他您所做的選擇。 會感興趣的其他兩個屬性：
  
- **EnableFederationAccess** 指出使用者是否可以與同盟網域的使用者進行通訊。
    
- **EnablePublicCloudAccess** 指出使用者是否可以與 Windows Live 使用者進行通訊。
    
因此，您不直接變更使用者帳戶 (例如， **Set-csuser-EnableFederationAccess $True**) 上的同盟相關的屬性。 相反地，您指派給帳戶已預先設定的所需的屬性值的外部存取原則。 如果我們希望使用者能夠與同盟使用者並與 Windows Live 使用者進行通訊時，該使用者帳戶必須被指派的原則，可讓這些類型的通訊。
  
如果您想要知道有人可以與彼此來自組織外部的使用者，您必須：
  
- 判斷已指派哪個外部存取原則給該使用者。
    
- 判斷該原則允許或不允許哪些功能。
    
例如，您可以這麼做藉由使用此命令：
  
```
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

這個命令尋找指派給使用者，然後尋找功能啟用或停用該原則內的原則。
  
若要管理 Skype 線上商務原則與 PowerShell，請參閱 < 的 cmdlet:

- [用戶端原則](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#client-policy-cmdlets)
- [會議原則](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#conferencing-policy-cmdlets)
- [行動原則](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#mobile-policy-cmdlets)
- [線上語音信箱原則](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#online-voicemail-policy-cmdlets)
- [語音路由原則](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#voice-routing-policy-cmdlets)


> [!NOTE]
> Skype 商務 Online 撥號對應表是在每個方面，除了名稱的原則。 而不是，說: 「 撥號原則 」 選擇名稱 」 撥號對應表 」，是為了提供回溯相容性與 Office Communications Server 和 Exchange。 
  
例如，若要查看所有可供您使用的語音原則執行此命令：
  
```
Get-CsVoicePolicy
```

> [!NOTE]
> 這會傳回所有可用的語音原則清單。 請記住，不過，並非所有原則可以指派給所有使用者。 這是因為涉及授權和地理位置的各種限制。 （所謂 」 的[使用狀況的位置](https://msdn.microsoft.com/en-us/library/azure/dn194136.aspx)。 」）如果您想要知道的外部存取原則和可指派給特定使用者的會議原則，請使用類似如下的命令： 

```
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

[ApplicableTo] 參數會對可指派給特定使用者 (例如，Alex Darrow) 的原則限制傳回的資料。根據授權及使用位置的限制，這可能代表所有可用原則的子集。 
  
在某些情況下，屬性的原則不會使用與 Office 365，而其他人只能管理由 Microsoft 支援人員。 
  
與 Skype for Business Online，使用者必須受管理的某種類型的原則。 如果有效原則相關的屬性是空白的這表示有問題的使用者由全域原則，也就是除非他或她特別指派個別使用者原則會自動套用至使用者的原則。 我們看不到所列出的使用者帳戶的用戶端原則，因為它被管理由全域原則。 您可以決定全域的用戶端原則中使用此命令：
  
```
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a>另請參閱

#### 

[使用 Office 365 PowerShell 管理商務用 Skype Online](manage-skype-for-business-online-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)

