---
title: 從商務用 Skype 與 Exchange 移除或停用混合式新式驗證
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 11/3/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5a91b9e3-1508-475b-93e0-710fa5d5cd2d
description: 如果您已啟用混合現代驗證 (HMA)，僅來尋找它並不適合您目前的環境，您可以停用 HMA。本文說明如何。
ms.openlocfilehash: fff9599641630386183ab9e1a0b8f597f0ba6e5b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540171"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>從商務用 Skype 與 Exchange 移除或停用混合式新式驗證

如果您已啟用混合現代驗證 (HMA)，僅來尋找它並不適合您目前的環境，您可以停用 HMA。本文說明如何。
  
## <a name="who-is-this-article-for"></a>本文是誰？

如果您已啟用經過驗證的 Skype 線上商務或內部，和/或 Exchange Online 或內部部署並找到您要停用 HMA，這些步驟就是您。
  
 **重要**如果您正處於 Skype 線上商務或內部看到 '[現代驗證支援商務拓撲 Skype](https://technet.microsoft.com/en-us/library/mt803262.aspx)' 文章、 有混合拓撲 HMA，且需要之前查看支援的拓撲。
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>如何停用混合現代驗證 (Exchange)

1. **Exchange 內部部署**： 開啟 Exchange 管理命令介面，並執行下列命令。 
    
1. Set-organizationconfig-OAuth2ClientProfileEnabled $false
    
2. Set-authserver-Identity evoSTS-IsDefaultAuthorizationEndpoint $false
    
2. **Exchange Online**： 連線至遠端 PowerShell 與 Exchange Online。執行下列命令來開啟為 'false' 您*OAuth2ClientProfileEnabled*旗標。 
    
1. Set-organizationconfig-OAuth2ClientProfileEnabled: $false
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>如何停用混合現代驗證 (Skype 企業版)

1. **企業內部的 Skype**: Skype 中執行下列命令商務管理命令介面。
    
1. Set-csoauthconfiguration ClientAuthorizationOAuthServerIdentity""
    
2. **線上商務的 Skype**: for Business 線上使用遠端 PowerShell 連線至 Skype。執行下列命令以停用摩登的驗證。 
    
1. Set-csoauthconfiguration ClientAdalAuthOverride 不允許
    
[現代驗證概觀連結](hybrid-modern-auth-overview.md)。 
  

