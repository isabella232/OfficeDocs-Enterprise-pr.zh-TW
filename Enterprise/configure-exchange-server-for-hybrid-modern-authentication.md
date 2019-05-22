---
title: 如何設定 Exchange Server 內部部署以使用混合式新式驗證
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 11/16/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
ms.collection:
- M365-security-compliance
description: 混合式新式驗證 (HMA)，是一種方法的身分識別管理，提供更安全的使用者驗證和授權，以及適用於 Exchange server 內部部署混合式部署。
ms.openlocfilehash: c86d794d0952faf59a724976fa2a180084646baa
ms.sourcegitcommit: ffa5c7a2d0e1eaa40b84ea1e9fb6992d1f05aa86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2019
ms.locfileid: "34332620"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a>如何設定 Exchange Server 內部部署以使用混合式新式驗證

混合式新式驗證 (HMA)，是一種方法的身分識別管理，提供更安全的使用者驗證和授權，以及適用於 Exchange server 內部部署混合式部署。
  
## <a name="fyi"></a>參考 FYI

開始之前，我呼叫：
  
- 混合式新式驗證\>HMA
    
- Exchange 內部部署\>NM-EXCH-UM-1ST
    
- Exchange Online \> EXO
    
此外，*本文如果中的圖形具有找出具有 ' 變為 out' 或暗灰色所示的項目不包含在 HMA 特有設定這表示物件*。 
  
## <a name="enabling-hybrid-modern-authentication"></a>啟用混合式新式驗證

表示開啟 HMA:
  
1. 要確定您符合必要條件之前。
    
1. 自許多**必要條件**是很常見的兩個 Skype for Business 和 Exchange[混合式新式驗證概觀及必要條件使用它與內部部署 Skype for Business 和 Exchange 伺服器](hybrid-modern-auth-overview.md)。 開始之前任何本文中的步驟，請執行這項操作。
    
2. 新增內部 web 服務 Url 為服務主要名稱 (Spn) 在 Azure AD 中。
    
3. 確保所有虛擬目錄啟用 HMA
    
4. 檢查 EvoSTS 驗證伺服器物件
    
5. 啟用 HMA EXCH.中
    
 **附註**您的 Office 版本是否支援 MA？ 請參閱 < <b0>Office 2013 和 Office 2016 用戶端應用程式的方式新式驗證運作</b0>。
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a>請確定您符合所有預先-需求

由於許多必要條件是很常見的兩個 Skype for Business 和 Exchange，檢閱[混合式新式驗證概觀及使用它與內部部署 Skype for Business 和 Exchange 伺服器的必要條件](hybrid-modern-auth-overview.md)。 執行此*之前*開始任何本文中的步驟。 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>新增內部 Azure AD 中為 Spn web 服務 Url

執行命令，指派內部 web 服務 Url 為 Azure AD Spn。 用戶端電腦和裝置會使用 Spn 期間驗證和授權。 （這包括內部和外部命名空間） 的 AAD 中必須註冊可能用來從內部連線到 Azure Active Directory (AAD) 的所有 Url。
  
首先，收集您需要新增的 AAD 中的所有 Url。 執行這些命令在內部部署：
  
```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ActiveSyncVirtualDirectory | FL server,*url*
Get-OABVirtualDirectory | FL server,*url*
```
    
確定用戶端可能連線至列為 HTTPS 服務主要名稱的 AAD 中的 Url。
  
1. 首先，連線至 AAD[這些](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)指示。 

 **附註**您要使用此頁面的 [Connect-msolservice 選項無法使用下列命令。 
    
2. 針對您的 Exchange 相關的 Url，輸入下列命令：
    
```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
```

此命令，它應該包括 https:// *autodiscover.yourdomain.com*和 https:// *mail.yourdomain.com* URL，但是大部分所組成的開頭的 Spn 的輸出採取的附註 （和更新版本的比對的螢幕擷取畫面）00000002-0000-0ff1-ce00-000000000000 /。 如果有從您的內部所遺失的 https:// Url 我們將需要這些特定記錄新增到此清單。 
  
3. 如果您沒有看到您內部和外部 MAPI/HTTP、 EWS、 ActiveSync、 OAB 和自動探索記錄此清單中的，您必須新增其使用下列命令 (範例 Url 是 '`mail.corp.contoso.com`'和'`owa.contoso.com`'，但是您必須**取代以您自己的範例 Url** ): <br/>
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
$x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
$x.ServicePrincipalnames.Add("https://owa.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. 確認您新的記錄已新增步驟 2 中取得 MsolServicePrincipal 命令執行，並將輸出中尋找。 比較清單 / 將螢幕擷取畫面從之前的 Spn （您可能也螢幕擷取畫面新清單以供記錄） 新的清單。 如果您已成功，您會看到兩個新的 Url 清單中。 將由我們的範例，此清單的 Spn 將現在包含特定 Url`https://mail.corp.contoso.com`和`https://owa.contoso.com`。 
  
## <a name="verify-virtual-directories-are-properly-configured"></a>確認虛擬目錄設定正確

現在請確認中正確地啟用 OAuth 上所有虛擬目錄 Outlook Exchange 可能會使用藉由執行下列命令：

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth* 
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

核取輸出至請確定**OAuth**啟用每個這些 VDirs 它看起來像這樣 （，若要查看的重點是 'OAuth'）; 

```powershell
Get-MapiVirtualDirectory | fl server,*url*,*auth*
```

```
Server                        : EX1
InternalUrl                   : https://mail.contoso.com/mapi
ExternalUrl                   : https://mail.contoso.com/mapi
IISAuthenticationMethods      : {Ntlm, OAuth, Negotiate}
InternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
ExternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
```
  
如果 OAuth 遺漏來自任何伺服器和四個虛擬目錄的任何您需要新增使用相關的命令，再繼續執行它。
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a>確認 EvoSTS 驗證伺服器物件是展示

會傳回內部部署 Exchange 管理命令介面，此最後一個命令。 現在您可以驗證內部有項目，evoSTS 驗證提供者：
  
```powershell
Get-AuthServer | where {$_.Name -eq "EvoSts"}
```

您的輸出應該會顯示名稱 EvoSts AuthServer 和 [啟用] 狀態應為 True。 如果您沒有看到此，您應該下載並執行混合組態精靈的最新版本。
  
 **重要**如果您正在執行 Exchange 2010 環境中，不會建立 EvoSTS 驗證提供者。 
  
## <a name="enable-hma"></a>啟用 HMA

在 Exchange 管理命令介面，內部部署中執行下列命令：

```powershell
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a>確認

一旦您啟用 HMA，用戶端下次登入時會使用新的驗證流程。 請注意，只開啟 HMA 就不會觸發重新驗證任何用戶端。 用戶端重新驗證為基礎的存留期的驗證權杖及/或他們所擁有的憑證。
  
您也應按住 CTRL 鍵，同時以滑鼠右鍵按一下 [Outlook 用戶端 （也在 Windows 通知紙匣）] 圖示，然後按一下 [' 連線狀態 '。 尋找針對 'Authn' 類型的用戶端的 SMTP 位址 ' 承載\*'，用來表示用於 OAuth 承載 token。
  
 **附註**需要使用 HMA 設定商務用 Skype？ 您將需要兩篇文章： 一個列出[支援的拓撲](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)，而另一個示範[如何進行設定](configure-skype-for-business-for-hybrid-modern-authentication.md)。
  

## <a name="related-topics"></a>相關主題

[混合式新式驗證概觀及使用商務和 Exchange 伺服器內部部署用 Skype 的必要條件](hybrid-modern-auth-overview.md) 
  

