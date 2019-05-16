---
title: 從商務用 Skype 與 Exchange 移除或停用混合式新式驗證
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 11/3/2017
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5a91b9e3-1508-475b-93e0-710fa5d5cd2d
ms.collection:
- M365-security-compliance
description: 如果您已啟用混合式新式驗證 (HMA)，找出它並不適合您目前的環境，您可以停用 HMA。 本文說明如何。
ms.openlocfilehash: 011e24c546fede11177e49ce8b36599d7d81d121
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070979"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>從商務用 Skype 與 Exchange 移除或停用混合式新式驗證

如果您已啟用混合式新式驗證 (HMA)，找出它並不適合您目前的環境，您可以停用 HMA。 本文說明如何。
  
## <a name="who-is-this-article-for"></a>本文是誰？

如果您已針對商務 Online 或內部及/或 Exchange Online 或內部部署啟用 Skype 中的新式驗證，並找到您要停用 HMA，這些步驟適用於您。

> [!IMPORTANT]
> 如果您是商務用 Skype 商務 Online 或內部部署中，請參閱 '[Skype for Business 拓撲支援新式驗證](https://technet.microsoft.com/en-us/library/mt803262.aspx)' 文章、 有混合拓撲 HMA，而且需要查看支援的拓撲，在您開始之前。
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>如何停用混合式新式驗證 (Exchange)

1. **Exchange 內部部署**： 開啟 Exchange 管理命令介面，並執行下列命令： 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. **Exchange Online**： 使用遠端 PowerShell[連線到 Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) 。 執行下列命令，以開啟為 'false' 您*OAuth2ClientProfileEnabled*標幟：

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>如何停用混合式新式驗證 (商務用 Skype)

1. **企業內部部署商務用 Skype**： 執行下列命令在 Skype for Business 管理命令介面：

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. **線上商務用 Skype**： 使用遠端 PowerShell[連線到商務用 Skype](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) 。 執行下列命令，以停用新式驗證：

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

[新式驗證概觀連結](hybrid-modern-auth-overview.md)。 
  

