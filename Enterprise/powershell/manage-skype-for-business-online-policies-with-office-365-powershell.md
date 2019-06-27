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
description: '摘要: 使用 Office 365 PowerShell 以原則管理商務用 Skype Online 使用者帳戶內容。'
ms.openlocfilehash: f19e262947b40b3e61dc8376b8e2e9c8ec984ff7
ms.sourcegitcommit: c115a3554647167e3770dda6b69dbf5c5de11ed7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2019
ms.locfileid: "35253683"
---
# <a name="manage-skype-for-business-online-policies-with-office-365-powershell"></a>線上商務原則與 Office 365 PowerShell 管理 Skype

 **摘要:** 使用 Office 365 PowerShell 以原則管理商務用 Skype Online 使用者帳戶內容。
  
若要管理商務用 Skype Online 的許多使用者帳戶屬性, 您必須使用 Office 365 PowerShell 將其指定為原則的屬性。
  
## <a name="before-you-begin"></a>開始之前

使用這些指示來設定以執行命令 (略過您已完成的步驟):
  
1. 下載並安裝[商務用 Skype Online 連接器模組](https://www.microsoft.com/download/details.aspx?id=39366)。
    
2. 開啟 Windows PowerShell 命令提示字元, 並執行下列命令: 
    
```
Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```

出現提示時, 請輸入您的商務用 Skype Online 系統管理員帳戶名稱和密碼。
    
## <a name="manage-user-account-policies"></a>管理使用者帳戶原則

許多商務用 Skype Online 使用者帳戶屬性是使用原則來設定。 原則就是可套用至一或多個使用者的設定集合。 若要查看原則的設定方式, 您可以對 FederationAndPICDefault 原則執行這個範例命令:
  
```
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

接著, 您應該會收到如下的內容:
  
```
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

在此範例中, 此原則內的值會決定當與同盟使用者通訊時, 可以執行或無法執行的動作。 例如, EnableOutsideAccess 屬性必須設為 True, 使用者才能與組織外部的人員進行通訊。 請注意, 此屬性不會出現在 Office 365 系統管理中心中。 相反地, 屬性會自動設定為 True 或 False 根據您所做的其他選擇。 其他兩個感興趣的屬性為:
  
- **EnableFederationAccess** 指出使用者是否可以與同盟網域的使用者進行通訊。
    
- **EnablePublicCloudAccess** 指出使用者是否可以與 Windows Live 使用者進行通訊。
    
因此, 您不會直接變更使用者帳戶上的同盟相關屬性 (例如, **get-csuser-EnableFederationAccess $True**)。 相反地, 您要指派帳戶具有預先設定之所需屬性值的外部存取原則。 如果我們想讓使用者能夠與同盟使用者和 Windows Live 使用者通訊, 則必須將允許通訊類型的原則指派給該使用者帳戶。
  
如果您想知道某人是否可以與組織外部的使用者進行通訊, 您必須:
  
- 判斷已指派哪個外部存取原則給該使用者。
    
- 判斷該原則允許或不允許哪些功能。
    
例如, 您可以使用下列命令來執行此動作:
  
```
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

此命令會尋找指派給使用者的原則, 然後尋找該原則中啟用或停用的功能。
  
若要使用 PowerShell 管理商務用 Skype Online 原則, 請參閱下列 Cmdlet:

- [用戶端原則](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#client-policy-cmdlets)
- [會議原則](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#conferencing-policy-cmdlets)
- [行動原則](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#mobile-policy-cmdlets)
- [線上語音信箱原則](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#online-voicemail-policy-cmdlets)
- [語音路由原則](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#voice-routing-policy-cmdlets)


> [!NOTE]
> 除了名稱之外, 商務用 Skype Online 撥號對應表是每個相關原則。 已選擇名稱「撥號對應表」, 而不是說「撥號原則」, 以便提供與 Office 通訊伺服器和 Exchange 的回溯相容性。 
  
例如, 若要查看所有可用的語音原則, 請執行下列命令:
  
```
Get-CsVoicePolicy
```

> [!NOTE]
> 這會傳回所有可用的語音原則清單。 不過請記住, 並非所有原則都可以指派給所有使用者。 這是因為涉及授權和地理位置的各種限制。 (所謂的「[使用位置](https://msdn.microsoft.com/en-us/library/azure/dn194136.aspx)」)如果您想知道可以指派給特定使用者的外部存取原則和會議原則, 請使用類似下列的命令: 

```
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

[ApplicableTo] 參數會對可指派給特定使用者 (例如，Alex Darrow) 的原則限制傳回的資料。根據授權及使用位置的限制，這可能代表所有可用原則的子集。 
  
在某些情況下, 不會將原則的屬性與 Office 365 搭配使用, 而有些則只能由 Microsoft 支援人員管理。 
  
透過商務用 Skype Online, 使用者必須以某種類型的原則來管理。 如果有效的原則相關屬性是空白的, 表示有問題的使用者是由全域原則所管理, 除非使用者特別指派個別使用者原則, 否則該原則會自動套用至使用者。 因為我們看不到為使用者帳戶列出的用戶端原則, 所以它是由全域原則管理。 您可以使用此命令來決定全域用戶端原則:
  
```
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a>另請參閱

#### 

[使用 Office 365 PowerShell 管理商務用 Skype Online](manage-skype-for-business-online-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)

