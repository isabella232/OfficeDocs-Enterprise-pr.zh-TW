---
title: "使用 Microsoft Azure Active Directory 的 SharePoint 2013 驗證"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: bef810a4-53f6-4962-878e-e20b5019baeb
description: "摘要： 了解如何使用 Azure Access Control Service 來驗證您的 SharePoint Server 2013 使用者利用 Azure Active Directory。"
ms.openlocfilehash: 9025eb53f4d8e37403c48416f41adbe35fa9fa01
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2018
---
# <a name="using-microsoft-azure-active-directory-for-sharepoint-2013-authentication"></a>使用 Microsoft Azure Active Directory 的 SharePoint 2013 驗證

 **摘要：**了解如何使用 Azure Access Control Service 來驗證您的 SharePoint Server 2013 使用者利用 Azure Active Directory。
  
它可以更輕鬆地管理您的使用者藉由驗證這些不同的身分識別提供者。請考量如何方便可以使用您信任的身分識別提供者，但其他人管理。例如，您可以有一種驗證的使用者存取雲端中的 SharePoint Server 2013 與另一個用於內部部署環境中的 SharePoint 2013 使用者類型。Azure Access Control Service 讓這些選擇變得可能。 
  
本文說明如何使用 Azure Access Control Service 向您的 SharePoint 2013 使用者與 Azure AD 驗證而不是您在內部部署 Active Directory。在此組態中，Azure AD 會成為 SharePoint 2013 的信任的身分識別提供者。此設定會新增不同本身的 SharePoint 2013 安裝所使用的 Active Directory 驗證使用者驗證方法。若要善加利用本文章，您應該熟悉 WS-同盟。如需詳細資訊，請參閱[了解 WS-同盟](https://go.microsoft.com/fwlink/p/?linkid=188052)。
  
下圖顯示在此組態中的 SharePoint 2013 使用者的驗證運作方式。
  
![使用者經過 Azure Active Directory 驗證](images/SP_AzureAD.png)
  
使用本文中的範例是由吳 Evans、 Azure 卓越中心的 Microsoft 架構師所提供。 
  
如需 SharePoint 2013 的協助工具資訊，請參閱 ＜ [SharePoint 2013 的協助工具](https://go.microsoft.com/fwlink/p/?LinkId=393123)。
  
## <a name="configuration-overview"></a>設定概觀

請遵循下列一般步驟來設定您的環境使用 Azure AD 做為 SharePoint 2013 身分識別提供者。
  
1. 建立新 Azure AD 租用戶和命名空間。
    
2. 新增 WS-同盟身分識別提供者。
    
3. 新增 SharePoint 做為信賴憑證者的廠商應用程式。
    
4. 建立使用 ssl 的自我簽署的憑證。
    
5. 建立宣告式驗證的規則群組。
    
6. 設定的 X.509 憑證。
    
7. 建立的宣告對應。
    
8. 設定 SharePoint 進行新的身分識別提供者。
    
9. 設定的權限。
    
10. 確認新的提供者。
    
## <a name="create-azure-ad-tenant-and-namespace"></a>建立 Azure AD 租用戶和命名空間

使用下列步驟來建立新的 Azure AD 租用戶和相關聯的命名空間。在這個範例中，我們會使用 namespace"blueskyabove"。 
  
1. 在 Azure 管理入口網站，按一下 [ **Active Directory**]，然後建立 [新 Azure AD 租用戶。
    
2. 按一下 [**存取控制命名空間**，並建立新的命名空間。 
    
3. 按一下 [下方列上的 [**管理**]。這應該會開啟此位置 https://blueskyabove.accesscontrol.windows.net/v2/mgmt/web。
    
4. 開啟 [Windows PowerShell]。使用 Microsoft Online Services 模組的 Windows PowerShell，這是安裝 Windows PowerShell cmdlet 的 Azure 的必要條件。
    
5. 在 Windows PowerShell 命令提示字元處輸入命令： `Connect-Msolservice`，然後輸入您的認證。
    
    > [!NOTE]
    > 如需如何使用 Windows PowerShell cmdlet 的 Azure 的其他資訊，請參閱 ＜ [Manage 使用 Windows PowerShell 的 Azure AD](https://go.microsoft.com/fwlink/p/?LinkId=393124)。 
  
6. Windows PowerShell 命令提示字元處輸入下列命令：
    
  ```
  Import-Module MSOnlineExtended -Force
  ```

  ```
  $replyUrl = New-MsolServicePrincipalAddresses -Address "https://blueskyabove.accesscontrol.windows.net/"
  ```

  ```
  New-MsolServicePrincipal -ServicePrincipalNames @("https://blueskyabove.accesscontrol.windows.net/") -DisplayName "BlueSkyAbove ACS Namespace" -Addresses $replyUrl
  ```

    下圖說明輸出結果。
    
     ![建立服務主體名稱](images/ServicePrincipalNames.jpg)
  
## <a name="add-a-ws-federation-identity-provider-to-the-namespace"></a>命名空間新增 WS-同盟身分識別提供者

使用下列步驟將新的 WS-同盟身分識別提供者新增至 blueskyabove 命名空間。
  
1. 從 Azure 管理入口網站中，移至 [ **Active Directory** > **存取控制命名空間**，按一下 [**建立新的執行個體**] 和 [**管理**。
    
2. Azure Access Control 入口網站中，按一下 [**身分識別提供者** > **新增**]，如下圖所示。
    
     ![Azure 中的 [身分識別提供者] 對話方塊](images/Identity.jpg)
  
3. 按一下 [ **WS-同盟身分識別提供者**，如下圖所示圖，並再按 [**下一步**。
    
     ![「新增身分識別提供者」設定](images/AddIdentity.jpg)
  
4. 填寫 [顯示名稱和登入連結文字，和 [**儲存**。WS-同盟中繼資料 URL 輸入 https://accounts.accesscontrol.windows.net/blueskyabove.onmicrosoft.com/FederationMetadata/2007-06/FederationMetadata.xml。下圖說明設定。
    
     ![同盟身分識別提供者](images/FederationIdentity.jpg)
  
## <a name="add-sharepoint-as-a-relying-party-application"></a>新增 SharePoint 做為信賴憑證者的廠商應用程式

信賴憑證者的廠商應用程式中加入 SharePoint 中使用下列步驟。
  
如需信賴憑證者應用程式設定的其他資訊，請參閱[信賴憑證者方應用程式](https://go.microsoft.com/fwlink/p/?LinkId=393125)。
  
1. 從 Azure Access Control 入口網站中，按一下 [**信賴憑證者方應用程式**，並再按一下 [**新增**]，如下圖所示。
    
     ![信賴憑證者方應用程式設定](images/RelyingPartyApplications.jpg)
  
## <a name="create-a-self-signed-certificate-to-use-for-ssl"></a>建立自我簽署的憑證，以使用 ssl

使用下列步驟來建立新的自我簽署憑證，以使用安全通訊的 ssl。
  
1. 擴充 web 應用程式使用相同的 URL 為 PublishingSite，但使用 SSL 搭配連接埠 443，如下圖所示。
    
     ![擴充應用程式的設定](images/ExtendWebApp.jpg)
  
2. In IIS Manager, double-click **Server Certificates**.
    
3. 在 [**動作**] 窗格中，按一下 [**建立自我簽署憑證**。在 [**指定憑證的易記名稱**] 方塊中輸入憑證的易記名稱及 [**確定]**。
    
4. 從 [**編輯網站繫結**] 對話方塊中，確定主機名稱的好記的名稱相同下圖所示。
    
     ![[自我簽署憑證] 精靈](images/SelfSignedCert.jpg)
  
     ![[編輯繫結] 方塊中的主機名稱](images/SelfSignedCert1.jpg)
  
5. From the Azure management portal, click the virtual machine that you want to configure, and then click **Endpoints**.
    
6. 按一下 [**新增**] 和 [ **-->** （適用於下一步）。
    
7. 在 [**名稱**] 中輸入端點的名稱。
    
8. 在**公用連接埠**和**私人連接埠**，輸入您要使用的連接埠號碼和 [完成] 核取記號。這些數字可能會不同。本文目的，我們使用 443，如下圖所示。
    
     ![Azure 中的「端點」設定](images/AddEndpoint.jpg)
  
    > [!NOTE]
    > 如需如何將端點加入在 Azure 虛擬機器的其他資訊，請參閱[如何設定 「 端點虛擬機器](https://go.microsoft.com/fwlink/p/?LinkId=393126)。 
  
9. From the Access Control services portal, add a relying party, as illustrated in the following figure.
    
     ![「新增信賴憑證者應用程式」設定](images/AddRelyingParty.jpg)
  
## <a name="create-a-rule-group-for-claims-based-authentication"></a>建立宣告式驗證的規則群組

使用下列步驟來建立新規則群組來控制宣告式驗證。
  
1. 在左窗格中，按一下 [**規則群組**] 和 [**新增**。
    
2. 輸入規則群組的名稱、 按一下 [**儲存**] 和 [**產生**。本文目的，我們使用**預設規則群組 for...in spvms.cloudapp.net**，如下圖所示。
    
     ![Azure 中的「規則群組」設定](images/RuleGroup.jpg)
  
     ![選擇 [產生] 之後的規則](images/GenerateRules.jpg)
  
    > [!NOTE]
    > 如需如何建立規則群組的其他資訊，請參閱[規則群組和規則](https://go.microsoft.com/fwlink/p/?LinkId=393128)。 
  
3. 按一下您想要變更的規則群組，然後按一下 [您想要變更的宣告規則。本文的目的，我們將宣告規則新增群組**名稱**傳遞為**upn**、 圖，如下圖所示。
    
     ![Azure Access Control 中的宣告規則](images/ClaimRules.jpg)
  
4. Delete the existing claim rule named **upn**, and leave the **Name Claim to UPN** rule, as illustrated by the following figure.
    
     ![Azure Access Control 中的規則設定](images/ClaimToUPN.jpg)
  
## <a name="configure-the-x509-certificate"></a>Configure the X.509 certificate

使用下列步驟來設定要用於 token 簽署的 X.509 憑證。
  
1. 在 [存取控制服務] 窗格中的 [**開發**、 按一下 [**應用程式整合**。
    
2. 在**端點參考 （英文)**、 找出關聯租用 Azure **Federation.xml** ，然後在網址列中的瀏覽器中複製的位置。
    
3. 在**Federation.xml**檔案中，找出**RoleDescriptor** ] 區段中，並將複製的資訊_<X509Certificate>_元素，如下圖所示。
    
     ![Federation.xml 檔案的 X509 憑證元素](images/X509Cert.jpg)
  
4. From the root of drive C:\\, create a folder named **Certificates**.
    
5. X509Certificate 資訊儲存到資料夾 c:\\憑證檔案名稱， **AcsTokenSigning.cer**。
    
    > [!NOTE]
    > 必須具有.cer 副檔名儲存的檔案名稱。 
  
     ![將 X509Certificate 元素儲存為檔案](images/X509Cert_Save.jpg)
  
## <a name="create-a-claim-mapping-by-using-windows-powershell"></a>Create a claim mapping by using Windows PowerShell

使用下列步驟來使用 Windows PowerShell 建立宣告對應。
  
確認您具備下列成員資格：
  
1. **securityadmin** fixed server role on the SQL Server instance.
    
2. **db_owner** fixed database role on all databases that will be updated.
    
3. 在執行 Windows PowerShell cmdlet 的伺服器上的管理員群組。
    
系統管理員可以使用**Add-spshelladmin** cmdlet 授與使用 SharePoint 2013 cmdlet 的權限。
  
> [!NOTE]
> 如果您沒有權限，請連絡您的安裝程式系統管理員或 SQL Server 系統管理員以要求權限。如需 Windows PowerShell 的權限的其他資訊，請參閱 ＜ [Add-spshelladmin ＞](http://technet.microsoft.com/library/2ddfad84-7ca8-409e-878b-d09cb35ed4aa.aspx)。 
  
1. 從 [**開始**] 功能表按一下 [**所有程式**]。
    
2. Click **Microsoft SharePoint 2013 Products**.
    
3. Click **SharePoint 2013 Management Shell**.
    
4. 在 Windows PowerShell 命令提示字元處輸入下列命令來建立的宣告對應：
    
  ```
  $cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2("c:\\certificates\\AcsTokenSigning.cer")
  ```

  ```
  New-SPTrustedRootAuthority -Name "ACS BlueSkyAbove Token Signing" -Certificate $cert
  ```

  ```
  $map = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn" -IncomingClaimTypeDisplayName "UPN" -SameAsIncoming
  ```

  ```
  $map2 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname" -IncomingClaimTypeDisplayName "GivenName" -SameAsIncoming
  ```

  ```
  $map3 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname" -IncomingClaimTypeDisplayName "SurName" -SameAsIncoming
  ```

  ```
  $realm = "urn:sharepoint:spvms"
  ```

  ```
  $ap = New-SPTrustedIdentityTokenIssuer -Name "ACS Provider" -Description "SharePoint secured by SAML in ACS" -realm $realm -ImportTrustCertificate $cert -ClaimsMappings $map,$map2,$map3 -SignInUrl "https://blueskyabove.accesscontrol.windows.net/v2/wsfederation" -IdentifierClaim "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"
  ```

## <a name="configure-sharepoint-for-the-new-identity-provider"></a>設定 SharePoint 進行新的身分識別提供者

Use the following steps to configure your SharePoint installation to the new identity provider for Azure AD.
  
1. 確認執行此程序的使用者帳戶為 SharePoint 伺服器陣列管理員群組的成員。
    
2. In Central Administration, on the home page, click **Application Management**.
    
3. On the **Application Management** page, in the **Web Applications** section, click **Manage web applications**.
    
4. 按一下適當的 Web 應用程式。
    
5. From the ribbon, click **Authentication Providers**.
    
6. Under **Zone**, click the name of the zone. For example, **Default**.
    
7. On the **Edit Authentication** page, in the **Claims Authentication Types** section, select **Trusted Identity provider**, and then click the name of your provider, which for purposes of this article is **ACS Provider**. Click **OK**.
    
8. The following figure illustrates the **Trusted Provider** setting.
    
![Web 應用程式中的「信任提供者」設定](images/AddProvider_Azure.jpg)
  
## <a name="set-the-permissions"></a>Set the permissions

Use the following steps to set the permissions to access the web application.
  
1. In Central Administration, on the home page, click **Application Management**.
    
2. On the **Application Management** page, in the **Web Applications** section, click **Manage web applications**.
    
3. Click the appropriate web application, and then click **User Policy**.
    
4. In **Policy for Web Application**, click **Add Users**.
    
5. In the **Add Users** dialog box, click the appropriate zone in **Zones**, and then click **Next**.
    
6. In the **Add Users** dialog box, typeuser2@blueskyabove.onmicrosoft.com (ACS Provider).
    
7. In **Permissions**, click **Full Control**.
    
8. 按一下 [完成]，然後按一下 [確定]。
    
The following figure illustrates the **Add Users** section of an existing web application.
  
![將使用者新增至現有 Web 應用程式](images/AddUsers_Azure.jpg)
  
## <a name="verify-the-new-provider"></a>Verify the new provider

Use the following steps to verify that the new identity provider is working by ensuring that the new authentication provider appears on the sign-in prompt.
  
1. Sign in by using the new provider named **Blue Sky Above**, as illustrated in the following figure.
    
     ![顯示新受信任提供者的登入對話方塊](images/BlueSkyAbove.jpg)
  
## <a name="additional-resources"></a>其他資源

[Understanding WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052)
  
[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)
  
## <a name="join-the-discussion"></a>參與討論

|**Contact us**|**描述**|
|:-----|:-----|
|**What cloud adoption content do you need?** <br/> |We are creating content for cloud adoption that spans multiple Microsoft cloud platforms and services. Let us know what you think about our cloud adoption content, or ask for specific content by sending email to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).  <br/> |
|**Join the cloud adoption discussion** <br/> |If you are passionate about cloud-based solutions, consider joining the Cloud Adoption Advisory Board (CAAB) to connect with a larger, vibrant community of Microsoft content developers, industry professionals, and customers from around the globe. To join, add yourself as a member of the [CAAB (Cloud Adoption Advisory Board) space](https://aka.ms/caab) of the Microsoft Tech Community and send us a quick email at [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Anyone can read community-related content on the [CAAB blog](https://blogs.technet.com/b/solutions_advisory_board/). However, CAAB members get invitations to private webinars that describe new cloud adoption resources and solutions.  <br/> |
|**Get the art you see here** <br/> |If you want an editable copy of the art you see in this article, we'll be glad to send it to you. Email your request, including the URL and title of the art, to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  <br/> |
   

