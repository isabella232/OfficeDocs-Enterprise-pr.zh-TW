---
title: 如何設定 Exchange Server 內部部署以使用混合式新式驗證
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 09/28/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
description: 混合式現代驗證 (HMA)，是一種方法提供較安全的使用者驗證和授權，以及適用於 Exchange server 內部部署混合部署的身分識別管理。
ms.openlocfilehash: 4267eaff8dfce71461f230310141a98be8a39e80
ms.sourcegitcommit: 9f921c0cae9a5dd4e66ec1a1261cb88284984a91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2018
ms.locfileid: "25347603"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a>如何設定 Exchange Server 內部部署以使用混合式新式驗證

混合式現代驗證 (HMA)，是一種方法提供較安全的使用者驗證和授權，以及適用於 Exchange server 內部部署混合部署的身分識別管理。
  
## <a name="fyi"></a>參考 FYI

我們開始前，我呼叫：
  
- 混合式現代驗證\>HMA
    
- Exchange 內部部署\>NM-EXCH-UM-1ST
    
- Exchange Online \> EXO
    
此外，*本文如果中的圖形具有找出具有 ' 變為 out' 或暗灰色中顯示的項目未包含在 HMA 特有設定說的物件*。 
  
## <a name="enabling-hybrid-modern-authentication"></a>啟用混合現代驗證

表示開啟 HMA：
  
1. 要確定您符合必要條件是之前。
    
1. 自許多**必要條件**都通用的商務與 Exchange[混合式現代驗證概觀及使用它與先決條件內部 Skype 業務與 Exchange 伺服器的](hybrid-modern-auth-overview.md)兩個 Skype。這麼做之前任何本文中的步驟。
    
2. 新增內部 web 服務 Url 為服務主要名稱 (Spn) 的 Azure AD。
    
3. 確保所有虛擬目錄啟用 HMA
    
4. 檢查 EvoSTS 驗證伺服器物件
    
5. 啟用 HMA EXCH.中
    
 **附註**您的 Office 版本是否支援 MA 吗？請參閱 ＜ [Office 2013 與 Office 2016 用戶端應用程式如何經過驗證的運作](modern-auth-for-office-2013-and-2016.md)。
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a>請確定您符合所有之前-需求

由於許多必要條件都通用的商務與 Exchange 的這兩個 Skype、 檢閱[混合現代驗證概觀及使用它與內部部署 Skype 業務與 Exchange 伺服器的先決條件](hybrid-modern-auth-overview.md)。執行此作業此*之前*開始執行任何本文中的步驟。 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>新增內部部署在 Azure AD 為 Spn web 服務 Url

執行命令指派內部 web 服務 Url 為 Azure AD 的 Spn。 Spn 用戶端機器及裝置所使用的驗證和授權期間。可能會用來從內部連線至 Azure Active Directory (AAD) 的所有 Url 必須都登錄於 AAD （包括內部和外部的命名空間）。
  
首先，收集您需要在 AAD 中新增的所有 Url。執行這些命令在內部部署：
  
```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ActiveSyncVirtualDirectory | FL server,*url*
Get-OABVirtualDirectory | FL server,*url*
```
    
確定用戶端可以連線至列為 AAD 中 HTTPS 服務主要名稱的 Url。
  
1. 首先，連線至 AAD[這些指示](https://docs.microsoft.com/en-us/office365/enterprise/powershell/connect-to-office-365-powershell)。
    
2. 針對 Exchange 相關的 Url，輸入下列命令：
    
```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
```

您應該包括 https:// *autodiscover.yourdomain.com*和 https:// *mail.yourdomain.com* URL，但多半包含開頭的 Spn 此命令的輸出採取的附註 （及更新版本比較的螢幕擷取畫面）00000002-0000-0ff1-ce00-000000000000 /。如果有從您的內部，遺漏的 https:// Url 我們必須將這些特定的記錄新增至這份清單。 
  
3. 如果您沒有看到您內部和外部 MAPI/HTTP、 EWS、 ActiveSync、 OAB 和自動探索記錄這份清單中的，您必須新增其使用下列命令 (範例 Url 是 '`mail.corp.contoso.com`'與'`owa.contoso.com`'，但您有**取代與您自己的範例 Url** ): <br/>
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
$x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
$x.ServicePrincipalnames.Add("https://owa.contoso.com/")
$x.ServicePrincipalnames.Add("https://eas.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. 確認新的記錄已新增再次執行步驟 2 的 Get MsolServicePrincipal 命令並尋找透過輸出。將清單進行比較 / 螢幕擷取畫面從之前至新的 Spn （您也可以螢幕擷取畫面新清單的記錄） 清單。如果您已成功，您會看到兩個新的 Url 清單中。不再由我們的範例的 Spn 清單將會立即包含特定 Url`https://mail.corp.contoso.com`和`https://owa.contoso.com`。 
  
## <a name="verify-virtual-directories-are-properly-configured"></a>確認虛擬目錄已正確設定

現在確認中適當地啟用 OAuth 上所有虛擬目錄 Outlook 與 Exchange 可能會使用執行下列命令：

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth* 
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

在每個這些 VDirs 上啟用] 核取輸出至請確定**OAuth** 、 外觀類似如下 （及查看的重點是 'OAuth'）; 

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
  
如果 OAuth 遺漏來自任何伺服器和四個虛擬目錄的任何您需要新增使用相關命令再繼續執行它。
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a>確認 EvoSTS 驗證伺服器物件存在

會傳回此最後一個命令會在內部部署 Exchange 管理命令介面。現在您可以驗證您的內部具有項目 evoSTS 驗證提供者：
  
```powershell
Get-AuthServer | where {$_.Name -eq "EvoSts"}
```

您的輸出應顯示的名稱 EvoSts AuthServer 和 [啟用] 狀態應該是 True。如果您沒有看到此，您應該下載並執行 [混合組態精靈] 的最新版本。
  
 **重要**如果您正在執行 Exchange 2010 環境中，將不會建立 EvoSTS 驗證提供者。 
  
## <a name="enable-hma"></a>啟用 HMA

在 Exchange 管理命令介面，在內部部署中執行下列命令：

```powershell
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a>[驗證]

一旦您啟用 HMA，用戶端的下一個登入將會使用新的驗證流程。請注意剛開啟 HMA 將不會觸發重新驗證的任何用戶端。用戶端重新驗證的驗證 token 及 （或） 憑證有存留期為基礎。
  
您也應該以滑鼠右鍵按一下圖示 Outlook 用戶端 （也是在 Windows 通知紙匣中） 的同時按住 CTRL 鍵並按一下 ' 連線狀態 」。針對 「 驗證 」 類型的用戶端的 SMTP 位址看起來 ' 承載\*'，這代表用於 OAuth 承載 token。
  
 **附註**需要使用 HMA 設定適用於企業的 Skype 吗？您將需要兩篇文章： 一個列出[支援的拓撲](https://technet.microsoft.com/en-us/library/mt803262.aspx)，另一個教您[如何進行的設定](configure-skype-for-business-for-hybrid-modern-authentication.md)。
  

## <a name="related-topics"></a>相關主題

[經過驗證的混合式概觀及使用內部部署 Skype 中的商務與 Exchange 伺服器的先決條件](hybrid-modern-auth-overview.md) 
  

