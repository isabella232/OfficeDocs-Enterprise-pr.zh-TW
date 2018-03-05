---
title: "SharePoint Server 驗證使用 Azure AD"
ms.author: tracyp
author: MSFTTracyP
ms.reviewer:
- kirke
- josephd
- kirks
manager: laurawi
ms.date: 3/2/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
ms.custom: Ent_Solutions
ms.assetid: 
description: "摘要： 了解如何將略過 Azure Access Control Service 並用 SAML 1.1 來驗證您的 SharePoint Server 使用者利用 Azure Active Directory。"
ms.openlocfilehash: e346a79fae32c19e14ce852257d5643041faf5d4
ms.sourcegitcommit: b1cb876c8a8fca1c2d67b2bc8282f1361066962c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2018
---
# <a name="using-azure-ad-for-sharepoint-server-authentication"></a>SharePoint Server 驗證使用 Azure AD

 **摘要：**了解如何驗證您的 SharePoint Server 2016 使用者利用 Azure Active Directory。
  
> [!NOTE]
> 本文根據吳 Evans、 Microsoft 首席程式經理的工作。 

<blockquote>
<p>本文是指與 Azure Active Directory 圖表互動的程式碼範例。您可以下載程式碼範例[此處](https://1drv.ms/u/s!AuAlJmH2xI6Kg3ItzF78krMFxJu3)。</p>
</blockquote>

SharePoint Server 2016 提供以驗證使用者使用宣告式驗證，使其成為容易管理您的使用者進行其驗證您信任但其他人管理不同的身分識別提供者的能力。例如，而不是管理透過 Active Directory 網域服務 (AD DS) 的使用者驗證，您無法讓使用者使用 Azure Active Directory (Azure AD) 進行驗證。這可讓 onmicrosoft.com 尾碼其使用者名稱中使用的僅限雲端使用者驗證、 使用者與內部部署目錄同步處理及受邀來賓使用者從其他目錄。它也可讓您利用 Azure AD 的功能，例如多重要素驗證和進階的報告功能。

> [!IMPORTANT]
> 本文所述的解決方案也可搭配 SharePoint Server 2013;但是請記住 SharePoint Server 2013 已接近主流支援的結尾。如需詳細資訊，請參閱 Microsoft 技術支援週期的[原則](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202013)及[更新產品服務原則 SharePoint 2013](https://technet.microsoft.com/library/684173bb-e90a-4eb7-b268-b8d7458bc802(v=office.16).aspx)。

本文說明您可以如何使用 Azure AD 驗證您的使用者，而不是在內部部署 AD DS。在此組態中，Azure AD 會變成在 SharePoint Server 2016 的信任的身分識別提供者。此設定會新增不同本身的 SharePoint Server 2016 安裝所使用的 AD DS 驗證的使用者驗證方法。若要善加利用本文章，您應該熟悉 WS-同盟。如需詳細資訊，請參閱[了解 WS-同盟](https://go.microsoft.com/fwlink/p/?linkid=188052)。

![使用 Azure AD 的 SharePoint 驗證](images/SAML11/fig1-architecture.png)

之前，此設定會具有必要的同盟服務等 Azure Access Control Service (ACS) 雲端或環境中主控的 Active Directory Federation Services (AD FS) 轉換為 SAML 1.1 從 SAML 2.0 權杖。這個轉換是不再需要 Azure AD 現在可讓發行的 SAML 1.1 權杖。圖表上方顯示 SharePoint 2016 示範已不再才能執行這個轉換的中介者在此組態中，使用者的驗證運作方式。

> [!NOTE]
> 此設定的運作是否 SharePoint 伺服器陣列架設在 Azure 虛擬機器或內部部署。它不需要開啟額外的防火牆連接埠不確認使用者可以從瀏覽器存取 Azure Active Directory。

如需 SharePoint 2016 協助工具資訊，請參閱 ＜[在 SharePoint Server 2016 中的協助工具指導方針](https://go.microsoft.com/fwlink/p/?LinkId=393123)。

## <a name="configuration-overview"></a>設定概觀

請遵循下列一般步驟來設定您的環境使用 Azure AD 做為 SharePoint Server 2016 身分識別提供者。

1. 建立新 Azure AD 目錄或使用現有的目錄。
2. 確定您想要安全與 Azure AD 的 web 應用程式的區域設定為使用 SSL。
3. 建立新的企業應用程式在 Azure AD。
4. 在 SharePoint Server 2016 設定新的受信任的身分識別提供者。
5. 設定 web 應用程式的權限。
6. 新增的 SAML 1.1 token 發行原則中 Azure AD。
7. 確認新的提供者。

下列各節說明如何執行這些工作。

## <a name="step-1-create-a-new-azure-ad-directory-or-use-your-existing-directory"></a>步驟 1： 建立新 Azure AD 目錄或使用現有的目錄

在 Azure 入口網站 ([https://portal.azure.com](https://portal.azure.com))，建立新目錄。提供組織名稱、 初始網域名稱與國家或地區。

![建立目錄](images/SAML11/fig2-createdirectory.png) 

 如果您已如 Microsoft Office 365 或 Microsoft Azure 訂閱時所用的目錄，您可以改用該目錄。您必須在目錄中註冊應用程式的權限。

## <a name="step-2-ensure-the-zone-for-the-web-application-that-you-want-to-secure-with-azure-ad-is-configured-to-use-ssl"></a>步驟 2： 請確定您想要安全與 Azure AD 的 web 應用程式的區域設定為使用 SSL

本文是撰寫使用參考架構中[執行高可用性 SharePoint 伺服器 2016 Azure 中的伺服器陣列](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint)。用以部署[這篇文章](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint)所述的解決方案文章的隨附指令碼建立不會使用 SSL 的網站。  

使用 SAML 需要使用 SSL 設定應用程式。如果您的 SharePoint web 應用程式未設定成使用 SSL，請使用下列步驟來建立新的自我簽署的憑證來設定 SSL 的 web 應用程式。此設定僅供用於在實驗室環境和不能用於實際執行。實際執行環境應使用的簽署的憑證。

1. 移至 [**管理中心** > **應用程式管理** > **管理 Web 應用程式**，然後選擇 [需要可延伸以使用 SSL 的 web 應用程式。選取 web 應用程式並按一下 [**延伸功能區**] 按鈕。擴充 web 應用程式使用相同的 URL，但使用 SSL 搭配連接埠 443。</br>![擴充至其他 IIS 網站的 web 應用程式](images/SAML11/fig3-extendwebapptoiis.png)</br>
2. 在 IIS 管理員中，按兩下 [**伺服器憑證**]。
3. 在 [**動作**] 窗格中，按一下 [**建立自我簽署憑證**。在指定的易記名稱] 的 [憑證] 方塊中輸入憑證的易記名稱及 [**確定]**。
4. 從 [**編輯網站繫結**] 對話方塊中，確定主機名稱的好記的名稱相同下圖所示。</br>![在 IIS 中編輯網站繫結](images/SAML11/fig4-editsitebinding.png)</br>

每個 SharePoint 伺服器陣列中的 web 前端伺服器需要在 IIS 中設定網站繫結的憑證。


## <a name="step-3-create-a-new-enterprise-application-in-azure-ad"></a>步驟 3： 在 Azure AD 中建立新的企業應用程式

1. 在 Azure 入口網站 ([https://portal.azure.com](https://portal.azure.com))，開啟您 Azure AD 的目錄。按一下 [**企業應用程式**，然後按一下 [**新的應用程式**。選擇 [**非圖庫應用程式**。提供的名稱，例如*SharePoint SAML 整合*並按一下 [**新增**]。</br>![新增新的非圖庫應用程式](images/SAML11/fig5-addnongalleryapp.png)</br>
2. 按一下 [單一登入連結功能窗格設定應用程式中。將 [**單一登入模式**] 下拉式清單變更為**saml 登入**以顯示應用程式的 SAML 設定屬性。設定具有下列內容：</br>
    - 識別碼：`urn:sharepoint:portal.contoso.local`
    - 回覆 URL：`https://portal.contoso.local/_trust/default.aspx`
    - 登入 URL：`https://portal.contoso.local/_trust/default.aspx`
    - 使用者識別碼：`user.userprincipalname`</br>
    - 請注意： 請記得變更 Url 以想要保護的 SharePoint 網站的 URL 取代*portal.contoso.local*的方式。</br>
3. 設定包含下列資料列的表格 （類似以下的表格 1）：</br> 
    - 領域
    - SAML 簽署憑證檔案的完整路徑
    - SAML 單一登入服務的 URL （將*/saml2*取代*/wsfed*）
    - 應用程式物件識別碼。 </br>
將 [ *Identifier* ] 值複製到插入資料表 (請參閱表 1 下方) 的*領域*屬性。
4. 儲存變更。
5. 按一下以存取設定登入] 頁面上的**設定 （應用程式名稱）**連結。</br>![設定單一登入頁面](images/SAML11/fig7-configssopage.png)</br> 
    -  按一下 [下載為副檔名為.cer 檔的 SAML 簽署憑證的**SAML 簽署憑證-原始**連結。複製並貼到表格的下載檔案的完整路徑。
    - 複製並貼上的 SAML 單一登入服務 URL 連結到您、 取代*/wsfed* */saml2*部分 URL。</br>
6.  瀏覽至 [應用程式的 [**內容**] 窗格。複製並貼到您在步驟 3 設定表格的物件 ID 值。</br>![應用程式的 [內容] 窗格](images/SAML11/fig8-propertiespane.png)</br>
7. 使用您所擷取的值，請確定您在步驟 3 設定表格的格式類似於下表 1。


| 擷取的表格 1： 值  |  |
|---------|---------|
|領域 | `urn:sharepoint:portal.contoso.local` |
|SAML 簽署憑證檔案的完整路徑 | `C:/temp/SharePoint SAML Integration.cer`  |
|SAML 單一登入服務 URL （取代為 /saml2 /wsfed） | `https://login.microsoftonline.com/b1726649-b616-460d-8d20-defab80d476c/wsfed` |
|應用程式物件識別碼 | `a812f48b-d1e4-4c8e-93be-e4808c8ca3ac` |

> [!IMPORTANT]
> 在 URL 中的*/saml2*值取代為*/wsfed*。*/Saml2*端點會處理 SAML 2.0 權杖。*/Wsfed*端點啟用處理 SAML 1.1 權杖，並需要 SharePoint 2016 SAML 同盟。

## <a name="step-4-configure-a-new-trusted-identity-provider-in-sharepoint-server-2016"></a>步驟 4： 在 SharePoint Server 2016 中設定新的受信任的身分識別提供者

登入 SharePoint Server 2016 伺服器並開啟 SharePoint 2016 管理命令介面。填入 $realm、 $wsfedurl、 和 $filepath 表格 1 的值，並執行下列命令以設定新的信任的身分識別提供者。

> [!TIP]
> 如果您正在使用 PowerShell 的新或想要深入了解 PowerShell 的運作方式，請參閱[SharePoint PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/overview?view=sharepoint-ps)。 

```
$realm = "<Realm from Table 1>"
$wsfedurl="<SAML single sign-on service URL from Table 1>"
$filepath="<Full path to SAML signing certificate file from Table 1>"
$cert = New-Object 
System.Security.Cryptography.X509Certificates.X509Certificate2($filepath)
New-SPTrustedRootAuthority -Name "AzureAD" -Certificate $cert
$map = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" -IncomingClaimTypeDisplayName "name" -LocalClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"
$map2 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname" -IncomingClaimTypeDisplayName "GivenName" -SameAsIncoming
$map3 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname" -IncomingClaimTypeDisplayName "SurName" -SameAsIncoming
$ap = New-SPTrustedIdentityTokenIssuer -Name "AzureAD" -Description "SharePoint secured by Azure AD" -realm $realm -ImportTrustCertificate $cert -ClaimsMappings $map,$map2,$map3 -SignInUrl $wsfedurl -IdentifierClaim “http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name”
```

接下來，請遵循下列步驟以啟用您的應用程式的信任的身分識別提供者：
1. 在管理中心中，瀏覽至 [**管理 Web 應用程式**並選取您想要安全與 Azure AD 的 web 應用程式。 
2. 在功能區上，按一下 [**驗證提供者**並選擇您想要使用的區域。
3. 選取 [**信任的身分識別提供者**，並選取 [身分識別提供者所註冊名為*AzureAD*。  
4. 在登入頁面 URL 設定中，選取 [**自訂登入] 頁面上**，並提供"/_trust/"的值。 
5. 按一下 [確定]****。

![設定驗證提供者](images/SAML11/fig10-configauthprovider.png)

## <a name="step-5-set-the-permissions"></a>步驟 5： 設定的權限

必須授與使用者會登入 Azure AD 及存取 SharePoint 應用程式的存取。 

1. 在 Azure 入口網站中開啟的 Azure AD 目錄。按一下 [**企業應用程式**，然後按一下 [**所有應用程式**。按一下您先前建立的應用程式 （SharePoint SAML 整合）。
2. 按一下 [**使用者與群組**]。 
3. 按一下 [新增使用者或群組有權限登入 SharePoint 使用 Azure AD 的 [**新增使用者**]。
4. 選取使用者或群組然後按一下 [**指派**]。
 
使用者已授與 Azure AD 的權限，但也必須授與 SharePoint 中的權限。使用下列步驟來設定存取 web 應用程式的權限。

1. 在管理中心按一下 [**應用程式管理**]。
2. 按一下 [**應用程式管理**] 頁面上的 [ **Web 應用程式**] 區段中的 [**管理 web 應用程式**]。
3. 按一下適當的 web 應用程式] 和 [**使用者原則**。
4. 在 [Web 應用程式的原則，按一下 [**新增使用者**]。</br>![搜尋使用者及其名稱宣告](images/SAML11/fig11-searchbynameclaim.png)</br>
5. 在 [**新增使用者**] 對話方塊中按一下適當的區域中**的區域**]，並再按 [**下一步**。
6. 在 [ **Web 應用程式的原則**] 對話方塊的 [**選擇使用者**] 區段中按一下 [**瀏覽**] 圖示。
7. 在 [**尋找**] 文字方塊中，在您的目錄中輸入使用者的登入名稱並按一下 [**搜尋**]。 </br>範例： *demouser@blueskyabove.onmicrosoft.com*。
8. 在清單檢視中 AzureAD 標題、 下的 [選取的 name 屬性並按一下 [**新增**] 然後按一下**[確定]**以關閉 [] 對話方塊。
9. 在權限，按一下 [**完全控制**]。</br>![宣告使用者授與完全控制](images/SAML11/fig12-grantfullcontrol.png)</br>
10. 按一下 [完成]，然後按一下 [確定]。

## <a name="step-6-add-a-saml-11-token-issuance-policy-in-azure-ad"></a>步驟 6： 在 Azure AD 中新增的 SAML 1.1 token 發行原則

入口網站中建立的 Azure AD 應用程式之後，它會預設為使用 SAML 2.0。SharePoint Server 2016 需要的 SAML 1.1 token 格式。下列指令碼會移除預設 SAML 2.0 原則並將新的原則新增到問題 SAML 1.1 權杖。

```
Import-Module <file path of Initialize.ps1> 
$objectid = "<Application Object ID from Table 1>"
$saml2policyid = Get-PoliciesAssignedToServicePrincipal -servicePrincipalId $objectid | ?{$_.displayName -EQ "TokenIssuancePolicy"} | select objectId
Remove-PolicyFromServicePrincipal -policyId $saml2policyid -servicePrincipalId $objectid
$policy = Add-TokenIssuancePolicy -DisplayName SPSAML11 -SigningAlgorithm "http://www.w3.org/2001/04/xmldsig-more#rsa-sha256" -TokenResponseSigningPolicy TokenOnly -SamlTokenVersion "1.1"
Set-PolicyToServicePrincipal -policyId $policy.objectId -servicePrincipalId $objectid
```

## <a name="step-7-verify-the-new-provider"></a>步驟 7： 確認新的提供者

開啟瀏覽器中您在先前步驟中設定的 web 應用程式的 url。您要重新導向至登入 Azure AD。

![登入設定以進行同盟的 Azure AD](images/SAML11/fig13-examplesignin.png)

您會詢問您是否要保持已登入。

![維持已登入嗎？](images/SAML11/fig14-staysignedin.png)

最後，您可以存取您的 Azure Active Directory 租用戶中的使用者身分登入的網站。

![使用者登入 SharePoint](images/SAML11/fig15-signedinsharepoint.png)


## <a name="additional-resources"></a>其他資源

[了解 WS-同盟](https://go.microsoft.com/fwlink/p/?linkid=188052)
  
[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)
  
## <a name="join-the-discussion"></a>參與討論

|**與我們連絡**|**描述**|
|:-----|:-----|
|**您需要什麼樣的雲端採用內容？** <br/> |我們會建立橫跨多個 Microsoft cloud 平台及服務的雲端採用的內容。我們知道什麼構思我們雲端採用內容，或藉由傳送電子郵件給[cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20)要求特定的內容。<br/> |
|**加入雲端採用討論區** <br/> |如果您是找到他們需雲端式解決方案，請考慮加入雲端採用 Advisory 董 (CAAB) 與 Microsoft 內容的開發人員、 產業專業人員和客戶的從遍更大型、 加上鮮豔社群連線。若要加入，新增您自己的 Microsoft 技術社群[CAAB （雲端採用諮詢委員會） 空間](https://aka.ms/caab)的成員身分並在[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!)快速的電子郵件傳送意見。任何人都可以讀取上[CAAB 部落格](https://blogs.technet.com/b/solutions_advisory_board/)社群相關內容。不過，CAAB 成員取得說明新雲端採用資源和解決方案的私人研討會的邀請。<br/> |
|**取得您在這裡看到的美工圖案** <br/> |如果您想編輯您在本文中看到藝術複本，我們樂於傳送給您。您的要求，包含 URL 及標題的圖案、 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20)的電子郵件。<br/> |
   

