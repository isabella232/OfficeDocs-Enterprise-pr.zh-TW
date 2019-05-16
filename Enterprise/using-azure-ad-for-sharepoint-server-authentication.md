---
title: 針對 SharePoint Server 驗證使用 Azure AD
ms.author: tracyp
author: MSFTTracyP
ms.reviewer: kirke, josephd, kirks
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
ms.custom: Ent_Solutions
ms.assetid: ''
description: 摘要： 了解如何略過 Azure Access Control Service 並用 SAML 1.1 來驗證您的 SharePoint Server 使用者與 Azure Active Directory。
ms.openlocfilehash: c2c9f33aa5e095a8b7fdde08e80cb1a61e88f3eb
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070789"
---
# <a name="using-azure-ad-for-sharepoint-server-authentication"></a>針對 SharePoint Server 驗證使用 Azure AD

 **摘要：** 了解如何驗證您的 SharePoint Server 2016 使用者與 Azure Active Directory。 

<blockquote>
<p>本文是指與 Azure Active Directory Graph 互動的程式碼範例。 您可以下載的程式碼範例[這裡](https://github.com/kaevans/spsaml11/tree/master/scripts)。</p>
</blockquote>

SharePoint Server 2016 提供的功能來驗證使用者使用宣告式驗證，以方便管理您的使用者進行驗證這些不同的身分識別提供者，您信任，但其他人管理。 例如，而不是管理透過 Active Directory 網域服務 (AD DS) 的使用者驗證，您可以讓使用者能夠使用 Azure Active Directory (Azure AD) 進行驗證。 這可讓與他們的 username 中的 onmicrosoft.com 後置詞的雲端專用使用者驗證、 使用者與內部部署目錄同步處理，並邀請來賓使用者從其他目錄。 它也可讓您利用 Azure AD 功能，例如多重要素驗證和進階的報告功能。

> [!IMPORTANT]
> 本文中所述的解決方案也可搭配 SharePoint Server 2013;不過，請記住，SharePoint Server 2013 已接近主流支援的結尾。 如需詳細資訊，請參閱[Microsoft 週期原則](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202013)及[更新產品服務原則 for SharePoint 2013。](https://technet.microsoft.com/library/684173bb-e90a-4eb7-b268-b8d7458bc802(v=office.16).aspx)

本文說明如何使用 Azure AD，而不是您內部部署 AD DS 以驗證您的使用者。 此組態中，在 Azure AD 會變成 SharePoint Server 2016 的受信任的身分識別提供者。 此組態會新增獨立於 SharePoint Server 2016 安裝本身所使用的 AD DS 驗證的使用者驗證方法。 若要享有這篇文章，您應該熟悉 WS-同盟。 如需詳細資訊，請參閱 <<c0>了解 WS-同盟。 如需詳細的 SharePoint 內部部署與 Azure Active Directory 整合的詳細資訊，請參閱 <<c0>專用教學課程。

![使用 Azure AD 的 SharePoint 驗證](media/SAML11/fig1-architecture.png)

先前，此組態會有需要同盟服務例如 Azure 存取控制服務 (ACS) 雲端或環境中主控 Active Directory Federation Services (AD FS) 轉換為 SAML 1.1 從 SAML 2.0 權杖。 Azure AD 現在可讓發行 SAML 1.1 語彙基元，已不再需要此轉換。 上圖顯示 SharePoint 2016 中的使用者此組態中，示範已不再的中介者若要執行這項轉換需求的驗證運作方式。

> [!NOTE]
> 此組態的運作是否在 SharePoint 伺服器陣列裝載在 Azure 虛擬機器或內部部署中。 它不需要開啟額外的防火牆連接埠以外確保使用者可以從他們的瀏覽器存取 Azure Active Directory。

如需 SharePoint 2016 的協助工具資訊，請參閱 <<c0>在 SharePoint Server 2016 中的協助工具指導方針。

## <a name="configuration-overview"></a>設定概觀

遵循下列一般步驟來設定您的環境，以使用 Azure AD 做為 SharePoint Server 2016 的身分識別提供者。

1. 建立新的 Azure AD 目錄，或使用您現有的目錄。
2. 請確定您要保護與 Azure AD 的 web 應用程式的區域設定為使用 SSL。
3. 在 Azure AD 中建立新的企業應用程式。
4. 在 SharePoint Server 2016 中設定新的受信任的身分識別提供者。
5. 設定 web 應用程式的權限。
6. 在 Azure AD 中新增 SAML 1.1 token 發行原則。
7. 確認新的提供者。

下列各節說明如何執行這些工作。

## <a name="step-1-create-a-new-azure-ad-directory-or-use-your-existing-directory"></a>步驟 1： 建立新的 Azure AD 目錄，或使用您現有的目錄

在 Azure 入口網站 ([https://portal.azure.com](https://portal.azure.com))，建立新的目錄。 提供組織名稱、 初始網域名稱和國家/地區或區域。

![建立目錄](media/SAML11/fig2-createdirectory.png) 

 如果您已如用於 Microsoft Office 365 或 Microsoft Azure 訂閱的目錄，您可以改為使用該目錄。 您必須在目錄中登錄應用程式的權限。

## <a name="step-2-ensure-the-zone-for-the-web-application-that-you-want-to-secure-with-azure-ad-is-configured-to-use-ssl"></a>步驟 2： 確保您要保護與 Azure AD 的 web 應用程式的區域設定為使用 SSL

本文已寫入使用中[執行的高可用性 SharePoint Server 2016 伺服器陣列在 Azure 中](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint)的參考架構。 用以部署[這篇文章](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint)所述的解決方案的文章隨附指令碼建立的網站，不會使用 SSL。  

使用 SAML 需要應用程式設定為使用 SSL。 如果您的 SharePoint web 應用程式未設定成使用 SSL，請使用下列步驟來建立新的自我簽署的憑證，來設定 SSL 的 web 應用程式。 此設定僅供用於在實驗室環境，而不是為了建立生產環境。 實際執行環境中應使用的簽署的憑證。

1. 移至**管理中心** > **應用程式管理** > **管理 Web 應用程式**，然後選擇 [需要擴充，以使用 SSL 的 web 應用程式。 選取 web 應用程式，然後按一下 [**擴充功能區**按鈕。 擴充 web 應用程式使用相同的 URL，但使用 SSL 與連接埠 443。<br/>![擴充 web 應用程式至其他 IIS 網站](media/SAML11/fig3-extendwebapptoiis.png)<br/>
2. 在 [IIS 管理員] 中，按兩下 [**伺服器憑證**。
3. 在 [動作]**** 窗格中，按一下 [建立自我簽署憑證]****。 在 [指定好記名稱] 的 [憑證] 方塊中，輸入憑證的易記名稱，然後按一下 [**確定]**。
4. 從 [**編輯網站繫結**] 對話方塊中，確定主機名稱是相同的好記的名稱，如下圖所示。<br/>![在 IIS 中編輯網站繫結](media/SAML11/fig4-editsitebinding.png)<br/>

每個 SharePoint 伺服器陣列中的 web 前端伺服器時，需要在 IIS 中設定網站繫結的憑證。


## <a name="step-3-create-a-new-enterprise-application-in-azure-ad"></a>步驟 3： 在 Azure AD 中建立新的企業應用程式

1. 在 Azure 入口網站 ([https://portal.azure.com](https://portal.azure.com))，開啟您的 Azure AD 目錄。 按一下 [**企業應用程式**，然後按一下 [**新的應用程式**。 選擇 [**非庫應用程式**]。 提供的名稱，例如*SharePoint SAML 整合*，並按一下 [**新增**]。<br/>![新增新的非庫應用程式](media/SAML11/fig5-addnongalleryapp.png)<br/>
2. 按一下 [單一登入連結功能窗格設定應用程式中。 將**單一登入模式**] 下拉式清單變更為**SAML 型登入**以顯示應用程式的 SAML 設定屬性。 設定具有下列內容：<br/>
    - 識別碼：`urn:sharepoint:portal.contoso.local`
    - 回覆 URL:`https://portal.contoso.local/_trust/default.aspx`
    - 登入 URL:`https://portal.contoso.local/_trust/default.aspx`
    - 使用者識別碼：`user.userprincipalname`<br/>
    - 附註： 請記得，變更 Url *portal.contoso.local*取代為您要保護的 SharePoint 網站的 URL。<br/>
3. 設定表格 （類似下列的表 1），其中包含下列資料列：<br/> 
    - Realm
    - SAML 簽署的憑證檔案的完整路徑
    - SAML 單一登入服務的 URL （取代為 */saml2* */wsfed*）
    - 應用程式的物件 id。 <br/>
將 [ *Identifier* ] 值複製到資料表 (請參閱表 1 下方) 的*領域*屬性。
4. 儲存變更。
5. 按一下 [**設定 （應用程式名稱）** 連結，以存取設定登入] 頁面。<br/>![設定單一登入] 頁面上](media/SAML11/fig7-configssopage.png)<br/> 
    -  按一下 [下載 SAML 簽署憑證為副檔名為.cer 檔的**SAML 簽章憑證-原始**連結。 複製並貼入表格中的下載的檔案的完整路徑。
    - 複製並貼到 SAML 單一登入服務的 URL 連結，以 */wsfed*取代 URL */saml2*部分。<br/>
6.  瀏覽至應用程式的 [**屬性**] 窗格。 複製並貼入您在步驟 3 中設定資料表中的物件 ID 值。<br/>![應用程式的 [屬性] 窗格](media/SAML11/fig8-propertiespane.png)<br/>
7. 使用您所擷取的值，請確定您在步驟 3 中設定資料表類似下列的表 1。


| 擷取的表 1： 值  |  |
|---------|---------|
|Realm | `urn:sharepoint:portal.contoso.local` |
|SAML 簽署的憑證檔案的完整路徑 | `C:/temp/SharePoint SAML Integration.cer`  |
|SAML 單一登入服務 URL （取代為 /saml2 /wsfed） | `https://login.microsoftonline.com/b1726649-b616-460d-8d20-defab80d476c/wsfed` |
|應用程式物件識別碼 | `a812f48b-d1e4-4c8e-93be-e4808c8ca3ac` |

> [!IMPORTANT]
> 取代 */wsfed* */saml2*值在 URL 中。 */Saml2*端點會處理 SAML 2.0 語彙基元。 */Wsfed*端點啟用處理 SAML 1.1 權杖，並且是必要的 SharePoint 2016 SAML 同盟。

## <a name="step-4-configure-a-new-trusted-identity-provider-in-sharepoint-server-2016"></a>步驟 4： 在 SharePoint Server 2016 中設定新的受信任的身分識別提供者

登入 SharePoint Server 2016 伺服器，並開啟 [SharePoint 2016 管理命令介面。 填寫 $realm、 $wsfedurl 及 $filepath 表格 1 的值，並執行下列命令，以設定新的受信任的身分識別提供者。

> [!TIP]
> 如果您是使用 PowerShell 新手，或想要深入了解 PowerShell 的運作方式，請參閱 < <b0>SharePoint PowerShell</b0>。 

```
$realm = "<Realm from Table 1>"
$wsfedurl="<SAML single sign-on service URL from Table 1>"
$filepath="<Full path to SAML signing certificate file from Table 1>"
$cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2($filepath)
New-SPTrustedRootAuthority -Name "AzureAD" -Certificate $cert
$map = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" -IncomingClaimTypeDisplayName "name" -LocalClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"
$map2 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname" -IncomingClaimTypeDisplayName "GivenName" -SameAsIncoming
$map3 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname" -IncomingClaimTypeDisplayName "SurName" -SameAsIncoming
$ap = New-SPTrustedIdentityTokenIssuer -Name "AzureAD" -Description "SharePoint secured by Azure AD" -realm $realm -ImportTrustCertificate $cert -ClaimsMappings $map,$map2,$map3 -SignInUrl $wsfedurl -IdentifierClaim "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name"
```

接下來，請遵循下列步驟來啟用您的應用程式的信任的身分識別提供者：
1. 在管理中心內，瀏覽至 [**管理 Web 應用程式**，並選取您想要保護與 Azure AD 的 web 應用程式。 
2. 在功能區中，按一下 [**驗證提供者**並選擇您想要使用的區域。
3. 選取 [**信任的身分識別提供者**，然後選取 [身分識別提供者只登錄名為*AzureAD*。  
4. 在 [登入頁面 URL] 設定中，選取 [**自訂登入] 頁面上**，並提供 「 /_trust/ 」 的值。 
5. 按一下 [確定]****。

![設定驗證提供者](media/SAML11/fig10-configauthprovider.png)

> [!IMPORTANT]
> 請務必遵循所有步驟，包括 「 /_trust/ 」 頁面中設定自訂的登入，所示。 除非所有步驟都之後，設定將無法正確運作。

## <a name="step-5-set-the-permissions"></a>步驟 5： 設定的權限

將登入 Azure AD，並存取 SharePoint 使用者必須授與存取應用程式。 

1. 在 Azure 入口網站中，開啟 [Azure AD 目錄]。 按一下 [**企業應用程式**，然後按一下 [**所有應用程式**。 按一下 [先前建立的應用程式 （SharePoint SAML 整合）。
2. 按一下 [**使用者和群組**]。 
3. 按一下 [新增使用者或群組 southeast offices 登入 SharePoint 使用 Azure AD 的權限的 [**新增使用者**]。
4. 選取使用者或群組，然後按一下 [**指派**]。
 
使用者已授與 Azure AD 中的權限，但也必須授與 SharePoint 中的權限。 使用下列步驟來設定存取 web 應用程式的權限。

1. 在管理中心中，按一下 [應用程式管理]****。
2. 在 [應用程式管理]**** 頁面上，按一下 [Web 應用程式]**** 區段中的 [管理 Web 應用程式]****。
3. 按一下適當的 web 應用程式]，然後按一下 [**使用者原則**。
4. 在 [Web 應用程式的原則，按一下 [**新增使用者**]。<br/>![依其名稱宣告使用者搜尋](media/SAML11/fig11-searchbynameclaim.png)<br/>
5. 在 [**新增使用者**] 對話方塊中，按一下 [**區域**] 中，在適當的區域，然後按一下 [**下一步**。
6. 在 [ **Web 應用程式的原則**] 對話方塊中**選擇使用者**] 區段中，按一下 [**瀏覽**] 圖示。
7. 在 [**尋找**] 文字方塊中，輸入使用者的登入名稱在您的目錄中，按一下 [**搜尋**。 <br/>範例： *demouser@blueskyabove.onmicrosoft.com*。
8. 標題下的 AzureAD 在清單檢視中，選取 name 屬性然後按一下 [**新增**] 然後按一下 **[確定]** 關閉對話方塊。
9. 在 [權限，按一下 [**完全控制**]。<br/>![將宣告使用者授與完全控制](media/SAML11/fig12-grantfullcontrol.png)<br/>
10. 按一下 [完成]，然後按一下 [確定]。

## <a name="step-6-add-a-saml-11-token-issuance-policy-in-azure-ad"></a>步驟 6： 在 Azure AD 中新增 SAML 1.1 token 發行原則

在入口網站中建立的 Azure AD 應用程式時，它會預設為使用 SAML 2.0。 SharePoint Server 2016 需要 SAML 1.1 token 格式。 下列指令碼將會移除預設的 SAML 2.0 原則，並將新的原則新增至問題 SAML 1.1 語彙基元。 

> 這段程式碼需要下載隨附的[範例示範與 Azure Active Directory Graph 互動](https://github.com/kaevans/spsaml11/tree/master/scripts)。 如果您為 Windows 桌面的 ZIP 檔案從 GitHub 下載指令碼，請務必要解除封鎖`MSGraphTokenLifetimePolicy.psm1`指令碼模組檔案和`Initialize.ps1`指令碼檔案 （以滑鼠右鍵按一下屬性、 選擇 [解除封鎖，按一下 [確定]）。 
![解除封鎖下載的檔案](media/SAML11/fig17-unblock.png)

一旦下載的範例指令碼，建立新的 PowerShell 指令碼，使用下列程式碼，以下載的檔案路徑取代預留位置`Initialize.ps1`您本機電腦上。 您在表格 1 中輸入應用程式物件識別碼來取代應用程式物件識別碼指定版面配置區。 建立之後，執行 PowerShell 指令碼。 

```
function AssignSaml11PolicyToAppPrincipal
{
    Param(
        [Parameter(Mandatory=$true)]
        [string]$pathToInitializeScriptFile, 
        [Parameter(Mandatory=$true)]
        [string]$appObjectid
    )

    $folder = Split-Path $pathToInitializeScriptFile
    Push-Location $folder

    #Loads the dependent ADAL module used to acquire tokens
    Import-Module $pathToInitializeScriptFile 

    #Gets the existing token issuance policy
    $existingTokenIssuancePolicy = Get-PoliciesAssignedToServicePrincipal -servicePrincipalId $appObjectid | ?{$_.type -EQ "TokenIssuancePolicy"} 
    Write-Host "The following TokenIssuancePolicy policies are assigned to the service principal." -ForegroundColor Green
    Write-Host $existingTokenIssuancePolicy -ForegroundColor White
    $policyId = $existingTokenIssuancePolicy.objectId

    #Removes existing token issuance policy
    Write-Host "Only a single policy can be assigned to the service principal. Removing the existing policy with ID $policyId" -ForegroundColor Green
    Remove-PolicyFromServicePrincipal -policyId $policyId -servicePrincipalId $appObjectid

    #Creates a new token issuance policy and assigns to the service principal
    Write-Host "Adding the new SAML 1.1 TokenIssuancePolicy" -ForegroundColor Green
    $policy = Add-TokenIssuancePolicy -DisplayName SPSAML11 -SigningAlgorithm "http://www.w3.org/2001/04/xmldsig-more#rsa-sha256" -TokenResponseSigningPolicy TokenOnly -SamlTokenVersion "1.1"
    Write-Host "Assigning the new SAML 1.1 TokenIssuancePolicy $policy.objectId to the service principal $appObjectid" -ForegroundColor Green
    Set-PolicyToServicePrincipal -policyId $policy.objectId -servicePrincipalId $appObjectid
    Pop-Location
}

#Only edit the following two variables
$pathToInitializeScriptFile = "<file path of Initialize.ps1>"
$appObjectid = "<Application Object ID from Table 1>"

AssignSaml11PolicyToAppPrincipal $pathToInitializeScriptFile $appObjectid
```
> [!IMPORTANT]
> 未簽署的 PowerShell 指令碼，並可能會提示您設定執行原則。 如需有關執行原則的詳細資訊，請參閱 <<c0>關於執行原則。 此外，您可能需要開啟提高權限的命令提示字元來成功執行中的範例指令碼的命令。

這些範例 PowerShell 命令是範例，說明如何對圖形 API 執行查詢。 如需與 Azure AD 權杖發行原則的詳細資訊，請參閱 <<c0>在原則上的作業的 Graph API 參考資料。

## <a name="step-7-verify-the-new-provider"></a>步驟 7： 確認新的提供者

開啟瀏覽器並前往您在先前步驟中設定 web 應用程式的 URL。 您會重新導向至登入 Azure AD。

![登入 Azure AD 同盟設定](media/SAML11/fig13-examplesignin.png)

您會詢問您是否要保持登入。

![保持登入？](media/SAML11/fig14-staysignedin.png)

最後，您可以存取您的 Azure Active Directory 租用戶中的使用者以登入的網站。

![使用者登入 SharePoint](media/SAML11/fig15-signedinsharepoint.png)

## <a name="managing-certificates"></a>管理憑證
請務必了解已針對上述步驟 4 中的信任的身分識別提供者的簽署憑證到期日期，以及必須更新。 在 [憑證更新，請參閱文章[同盟單一登入 Azure Active Directory 中的管理憑證](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-sso-certs)的資訊。 一旦憑證已在 Azure AD 中已更新，下載至本機檔案，並使用下列指令碼來設定信任的身分識別提供者與經過更新的簽署憑證。 

```
$filepath="<Full path to renewed SAML signing certificate file>"
$cert= New-Object System.Security.Cryptography.X509Certificates.X509Certificate2($filePath)
New-SPTrustedRootAuthority -Name "AzureAD" -Certificate $cert
Get-SPTrustedIdentityTokenIssuer "AzureAD" | Set-SPTrustedIdentityTokenIssuer -ImportTrustCertificate $cert
```
## <a name="configuring-one-trusted-identity-provider-for-multiple-web-applications"></a>設定多個 web 應用程式的一個信任的身分識別提供者
設定適用於單一 web 應用程式，但需要其他設定，如果您想要使用多個 web 應用程式相同的信任的身分識別提供者。 例如，假設 [我們已延伸 web 應用程式使用的 URL`https://portal.contoso.local`但現在卻想要驗證使用者，以`https://sales.contoso.local`也。 若要這麼做，我們需要更新受限於 WReply 參數，並新增回覆 URL 的 Azure AD 中更新的應用程式註冊的身分識別提供者。

1. 在 Azure 入口網站中，開啟 [Azure AD 目錄]。 按一下 [**應用程式註冊**，然後按一下 [**檢視所有應用程式**。 按一下 [先前建立的應用程式 （SharePoint SAML 整合）。
2. 按一下 [**設定**]。
3. 在 [設定] 刀鋒視窗中，按一下 [**回覆 Url**。 
4. 新增其他 web 應用程式的 URL`/_trust/default.aspx`附加至的 URL (例如`https://sales.contoso.local/_trust/default.aspx`) 並按一下 [**儲存**]。 
5. 在 SharePoint 伺服器上，開啟**SharePoint 2016 管理命令介面**，並執行下列命令，使用您先前使用信任的身分識別 token 簽署者的名稱。

```
$t = Get-SPTrustedIdentityTokenIssuer "AzureAD"
$t.UseWReplyParameter=$true
$t.Update()
```
6. 在管理中心內，移至 web 應用程式，然後啟用現有的受信任的身分識別提供者。 請記住，也設定為自訂的登入頁面的 [登入頁面 URL `/_trust/`。
7. 在管理中心中，按一下 [web 應用程式，選擇 [**使用者原則**。 如先前所示範這篇文章，請新增具有適當的權限的使用者。

## <a name="fixing-people-picker"></a>修正人員選擇
使用者現在可以登入 SharePoint 2016 使用從 Azure AD 的身分識別，但仍有使用者經驗的機會。 在人員選擇] 中，搜尋的使用者呈現比方說，多個搜尋結果。 沒有針對每個所建立的宣告對應 3 的宣告類型的搜尋結果。 若要選擇使用人員選擇] 的使用者，您必須完全輸入其使用者名稱，然後選擇 [ **name**宣告結果。

![宣告的搜尋結果](media/SAML11/fig16-claimssearchresults.png)

沒有驗證值搜尋，可能會導致拼錯或不小心選擇錯誤的宣告類型，例如**姓氏**指派的使用者 」 宣告。 這可防止使用者成功存取資源。

若要協助進行這種情況下，沒有開放原始碼解決方案呼叫[AzureCP](https://yvand.github.io/AzureCP/)適用於 SharePoint 2016 提供的自訂宣告提供者。 它會使用 Azure AD Graph 若要解決功能的使用者輸入，並進行驗證。 深入瞭解[AzureCP](https://yvand.github.io/AzureCP/)。 

## <a name="additional-resources"></a>其他資源

[了解 WS-同盟](https://go.microsoft.com/fwlink/p/?linkid=188052)
  
[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)
  
## <a name="join-the-discussion"></a>參與討論

|**連絡我們**|**描述**|
|:-----|:-----|
|**您需要什麼樣的雲端採用內容？** <br/> |我們正在建立涵蓋多個 Microsoft 雲端平台及服務的雲端採用內容。請傳送電子郵件至 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20)，讓我們知道您對雲端採用內容的看法或對特定內容的要求。<br/> |
|**加入雲端採用討論** <br/> |如果您熱愛雲端解決方案，請考慮加入雲端採用諮詢委員會 (Cloud Adoption Advisory Board，CAAB)，與更大且活躍的 Microsoft 內容開發人員、產業專業人員及全球的客戶接觸。若要加入，請新增為 Microsoft 技術社群 [CAAB (雲端採用諮詢委員會) 空間](https://aka.ms/caab)的成員，並傳送電子郵件給我們，地址為：[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!)。所有人都可以在 [CAAB 部落格](https://blogs.technet.com/b/solutions_advisory_board/)上讀取社群相關內容。不過，CAAB 成員可獲得新雲端採用資源和解決方案說明的私人網路研討會邀請。<br/> |
|**取得您在這裡看到的美工圖案** <br/> |如果您想要此文章中所看到之美工圖案的可編輯複本，我們很樂於將它傳送給您。請以電子郵件將您的要求 (包括美工圖案的 URL 和標題) 傳送至 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20)。<br/> |
   

