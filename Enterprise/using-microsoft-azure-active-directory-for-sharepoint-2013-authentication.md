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
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Solutions
ms.assetid: bef810a4-53f6-4962-878e-e20b5019baeb
description: "摘要： 了解如何使用 Azure Access Control Service 來驗證您的 SharePoint Server 2013 使用者利用 Azure Active Directory。"
ms.openlocfilehash: 85db8376aeb06ef6f291b563410c991ea24351d5
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="using-microsoft-azure-active-directory-for-sharepoint-2013-authentication"></a><span data-ttu-id="8717b-103">使用 Microsoft Azure Active Directory 的 SharePoint 2013 驗證</span><span class="sxs-lookup"><span data-stu-id="8717b-103">Using Microsoft Azure Active Directory for SharePoint 2013 authentication</span></span>

 <span data-ttu-id="8717b-104">**摘要：**了解如何使用 Azure Access Control Service 來驗證您的 SharePoint Server 2013 使用者利用 Azure Active Directory。</span><span class="sxs-lookup"><span data-stu-id="8717b-104">**Summary:** Learn how to use the Azure Access Control Service to authenticate your SharePoint Server 2013 users with Azure Active Directory.</span></span>
  
<span data-ttu-id="8717b-p101">它可以更輕鬆地管理您的使用者藉由驗證這些不同的身分識別提供者。請考量如何方便可以使用您信任的身分識別提供者，但其他人管理。例如，您可以有一種驗證的使用者存取雲端中的 SharePoint Server 2013 與另一個用於內部部署環境中的 SharePoint 2013 使用者類型。Azure Access Control Service 讓這些選擇變得可能。</span><span class="sxs-lookup"><span data-stu-id="8717b-p101">It can be easier to manage your users by authenticating them with different identity providers. Consider how convenient it can be to use an identity provider that you trust, but someone else manages. For example, you could have one type of authentication for users who access SharePoint Server 2013 in the cloud and another for SharePoint 2013 users in your on-premises environment. The Azure Access Control Service makes these choices possible.</span></span> 
  
<span data-ttu-id="8717b-p102">本文說明如何使用 Azure Access Control Service 向您的 SharePoint 2013 使用者與 Azure AD 驗證而不是您在內部部署 Active Directory。在此組態中，Azure AD 會成為 SharePoint 2013 的信任的身分識別提供者。此設定會新增不同本身的 SharePoint 2013 安裝所使用的 Active Directory 驗證使用者驗證方法。若要善加利用本文章，您應該熟悉 WS-同盟。如需詳細資訊，請參閱[了解 WS-同盟](https://go.microsoft.com/fwlink/p/?linkid=188052)。</span><span class="sxs-lookup"><span data-stu-id="8717b-p102">This article explains how you can use the Azure Access Control Service to authenticate your SharePoint 2013 users with Azure AD, instead of your on-premises Active Directory. In this configuration, Azure AD becomes a trusted identity provider for SharePoint 2013. This configuration adds a user authentication method that is separate from Active Directory authentication used by the SharePoint 2013 installation itself. To benefit from this article, you should be familiar with WS-Federation. For more information, see [Understanding WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052).</span></span>
  
<span data-ttu-id="8717b-114">下圖顯示在此組態中的 SharePoint 2013 使用者的驗證運作方式。</span><span class="sxs-lookup"><span data-stu-id="8717b-114">The following figure shows how authentication works for SharePoint 2013 users in this configuration.</span></span>
  
![使用者經過 Azure Active Directory 驗證](images/SP_AzureAD.png)
  
<span data-ttu-id="8717b-116">使用本文中的範例是由吳 Evans、 Azure 卓越中心的 Microsoft 架構師所提供。</span><span class="sxs-lookup"><span data-stu-id="8717b-116">The example used in this article is provided by Kirk Evans, Microsoft Architect for the Azure Center of Excellence.</span></span> 
  
<span data-ttu-id="8717b-117">如需 SharePoint 2013 的協助工具資訊，請參閱 ＜ [SharePoint 2013 的協助工具](https://go.microsoft.com/fwlink/p/?LinkId=393123)。</span><span class="sxs-lookup"><span data-stu-id="8717b-117">For information about SharePoint 2013 accessibility, see [Accessibility for SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=393123).</span></span>
  
## <a name="configuration-overview"></a><span data-ttu-id="8717b-118">設定概觀</span><span class="sxs-lookup"><span data-stu-id="8717b-118">Configuration overview</span></span>

<span data-ttu-id="8717b-119">請遵循下列一般步驟來設定您的環境使用 Azure AD 做為 SharePoint 2013 身分識別提供者。</span><span class="sxs-lookup"><span data-stu-id="8717b-119">Follow these general steps to set up your environment to use Azure AD as a SharePoint 2013 identity provider.</span></span>
  
1. <span data-ttu-id="8717b-120">建立新 Azure AD 租用戶和命名空間。</span><span class="sxs-lookup"><span data-stu-id="8717b-120">Create a new Azure AD tenant and namespace.</span></span>
    
2. <span data-ttu-id="8717b-121">新增 WS-同盟身分識別提供者。</span><span class="sxs-lookup"><span data-stu-id="8717b-121">Add a WS-Federation identity provider.</span></span>
    
3. <span data-ttu-id="8717b-122">新增 SharePoint 做為信賴憑證者的廠商應用程式。</span><span class="sxs-lookup"><span data-stu-id="8717b-122">Add SharePoint as a relying party application.</span></span>
    
4. <span data-ttu-id="8717b-123">建立使用 ssl 的自我簽署的憑證。</span><span class="sxs-lookup"><span data-stu-id="8717b-123">Create a self-signed certificate to use for SSL.</span></span>
    
5. <span data-ttu-id="8717b-124">建立宣告式驗證的規則群組。</span><span class="sxs-lookup"><span data-stu-id="8717b-124">Create a rule group for claims-based authentication.</span></span>
    
6. <span data-ttu-id="8717b-125">設定的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="8717b-125">Configure the X.509 certificate.</span></span>
    
7. <span data-ttu-id="8717b-126">建立的宣告對應。</span><span class="sxs-lookup"><span data-stu-id="8717b-126">Create a claim mapping.</span></span>
    
8. <span data-ttu-id="8717b-127">設定 SharePoint 進行新的身分識別提供者。</span><span class="sxs-lookup"><span data-stu-id="8717b-127">Configure SharePoint for the new identity provider.</span></span>
    
9. <span data-ttu-id="8717b-128">設定的權限。</span><span class="sxs-lookup"><span data-stu-id="8717b-128">Set the permissions.</span></span>
    
10. <span data-ttu-id="8717b-129">確認新的提供者。</span><span class="sxs-lookup"><span data-stu-id="8717b-129">Verify the new provider.</span></span>
    
## <a name="create-azure-ad-tenant-and-namespace"></a><span data-ttu-id="8717b-130">建立 Azure AD 租用戶和命名空間</span><span class="sxs-lookup"><span data-stu-id="8717b-130">Create Azure AD tenant and namespace</span></span>

<span data-ttu-id="8717b-p103">使用下列步驟來建立新的 Azure AD 租用戶和相關聯的命名空間。在這個範例中，我們會使用 namespace"blueskyabove"。</span><span class="sxs-lookup"><span data-stu-id="8717b-p103">Use the following steps to create a new Azure AD tenant and an associated namespace. In this example, we use the namespace "blueskyabove."</span></span> 
  
1. <span data-ttu-id="8717b-133">在 Azure 管理入口網站，按一下 [ **Active Directory**]，然後建立 [新 Azure AD 租用戶。</span><span class="sxs-lookup"><span data-stu-id="8717b-133">In the Azure Management Portal, click **Active Directory**, and then create a new Azure AD tenant.</span></span>
    
2. <span data-ttu-id="8717b-134">按一下 [**存取控制命名空間**，並建立新的命名空間。</span><span class="sxs-lookup"><span data-stu-id="8717b-134">Click **Access Control Namespaces**, and create a new namespace.</span></span> 
    
3. <span data-ttu-id="8717b-p104">按一下 [下方列上的 [**管理**]。這應該會開啟此位置 https://blueskyabove.accesscontrol.windows.net/v2/mgmt/web。</span><span class="sxs-lookup"><span data-stu-id="8717b-p104">Click **Manage** on the bottom bar. This should open this location, https://blueskyabove.accesscontrol.windows.net/v2/mgmt/web.</span></span>
    
4. <span data-ttu-id="8717b-p105">開啟 [Windows PowerShell]。使用 Microsoft Online Services 模組的 Windows PowerShell，這是安裝 Windows PowerShell cmdlet 的 Azure 的必要條件。</span><span class="sxs-lookup"><span data-stu-id="8717b-p105">Open Windows PowerShell. Use the Microsoft Online Services Module for Windows PowerShell, which is a prerequisite for installing the Azure for Windows PowerShell cmdlets.</span></span>
    
5. <span data-ttu-id="8717b-139">在 Windows PowerShell 命令提示字元處輸入命令： `Connect-Msolservice`，然後輸入您的認證。</span><span class="sxs-lookup"><span data-stu-id="8717b-139">From the Windows PowerShell command prompt, type the command:  `Connect-Msolservice`, and then type your credentials.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="8717b-140">如需如何使用 Windows PowerShell cmdlet 的 Azure 的其他資訊，請參閱 ＜ [Manage 使用 Windows PowerShell 的 Azure AD](https://go.microsoft.com/fwlink/p/?LinkId=393124)。</span><span class="sxs-lookup"><span data-stu-id="8717b-140">For additional information about how to use Azure for Windows PowerShell cmdlets, see [Manage Azure AD using Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=393124).</span></span> 
  
6. <span data-ttu-id="8717b-141">Windows PowerShell 命令提示字元處輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="8717b-141">From a Windows PowerShell command prompt, type the following commands:</span></span>
    
  ```
  Import-Module MSOnlineExtended -Force
  ```

  ```
  $replyUrl = New-MsolServicePrincipalAddresses -Address "https://blueskyabove.accesscontrol.windows.net/"
  ```

  ```
  New-MsolServicePrincipal -ServicePrincipalNames @("https://blueskyabove.accesscontrol.windows.net/") -DisplayName "BlueSkyAbove ACS Namespace" -Addresses $replyUrl
  ```

    <span data-ttu-id="8717b-142">下圖說明輸出結果。</span><span class="sxs-lookup"><span data-stu-id="8717b-142">The following figure illustrates the output result.</span></span>
    
     ![建立服務主體名稱](images/ServicePrincipalNames.jpg)
  
## <a name="add-a-ws-federation-identity-provider-to-the-namespace"></a><span data-ttu-id="8717b-144">命名空間新增 WS-同盟身分識別提供者</span><span class="sxs-lookup"><span data-stu-id="8717b-144">Add a WS-Federation identity provider to the namespace</span></span>

<span data-ttu-id="8717b-145">使用下列步驟將新的 WS-同盟身分識別提供者新增至 blueskyabove 命名空間。</span><span class="sxs-lookup"><span data-stu-id="8717b-145">Use the following steps to add a new WS-Federation identity provider to the blueskyabove namespace.</span></span>
  
1. <span data-ttu-id="8717b-146">從 Azure 管理入口網站中，移至 [ **Active Directory** > **存取控制命名空間**，按一下 [**建立新的執行個體**] 和 [**管理**。</span><span class="sxs-lookup"><span data-stu-id="8717b-146">From the Azure management portal, go to **Active Directory** > **Access Control Namespaces**, click **Create a new instance**, and then click **Manage**.</span></span>
    
2. <span data-ttu-id="8717b-147">Azure Access Control 入口網站中，按一下 [**身分識別提供者** > **新增**]，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="8717b-147">From the Azure Access Control portal, click **Identity Providers** > **Add**, as illustrated in the following figure.</span></span>
    
     ![Azure 中的 [身分識別提供者] 對話方塊](images/Identity.jpg)
  
3. <span data-ttu-id="8717b-149">按一下 [ **WS-同盟身分識別提供者**，如下圖所示圖，並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="8717b-149">Click **WS-Federation identity provider**, as illustrated in the following figure, and then click **Next**.</span></span>
    
     ![「新增身分識別提供者」設定](images/AddIdentity.jpg)
  
4. <span data-ttu-id="8717b-p106">填寫 [顯示名稱和登入連結文字，和 [**儲存**。WS-同盟中繼資料 URL 輸入 https://accounts.accesscontrol.windows.net/blueskyabove.onmicrosoft.com/FederationMetadata/2007-06/FederationMetadata.xml。下圖說明設定。</span><span class="sxs-lookup"><span data-stu-id="8717b-p106">Fill out the display name and logon link text, and then click **Save**. For the WS-Federation metadata URL, type https://accounts.accesscontrol.windows.net/blueskyabove.onmicrosoft.com/FederationMetadata/2007-06/FederationMetadata.xml. The following figure illustrates the setting.</span></span>
    
     ![同盟身分識別提供者](images/FederationIdentity.jpg)
  
## <a name="add-sharepoint-as-a-relying-party-application"></a><span data-ttu-id="8717b-155">新增 SharePoint 做為信賴憑證者的廠商應用程式</span><span class="sxs-lookup"><span data-stu-id="8717b-155">Add SharePoint as a relying party application</span></span>

<span data-ttu-id="8717b-156">信賴憑證者的廠商應用程式中加入 SharePoint 中使用下列步驟。</span><span class="sxs-lookup"><span data-stu-id="8717b-156">Use the following steps to add SharePoint as a relying party application.</span></span>
  
<span data-ttu-id="8717b-157">如需信賴憑證者應用程式設定的其他資訊，請參閱[信賴憑證者方應用程式](https://go.microsoft.com/fwlink/p/?LinkId=393125)。</span><span class="sxs-lookup"><span data-stu-id="8717b-157">For additional information about relying party application settings, see [Relying Party Applications](https://go.microsoft.com/fwlink/p/?LinkId=393125).</span></span>
  
1. <span data-ttu-id="8717b-158">從 Azure Access Control 入口網站中，按一下 [**信賴憑證者方應用程式**，並再按一下 [**新增**]，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="8717b-158">From the Azure Access Control portal, click **Relying party applications**, and then click **Add**, as illustrated in the following figure.</span></span>
    
     ![信賴憑證者方應用程式設定](images/RelyingPartyApplications.jpg)
  
## <a name="create-a-self-signed-certificate-to-use-for-ssl"></a><span data-ttu-id="8717b-160">建立自我簽署的憑證，以使用 ssl</span><span class="sxs-lookup"><span data-stu-id="8717b-160">Create a self-signed certificate to use for SSL</span></span>

<span data-ttu-id="8717b-161">使用下列步驟來建立新的自我簽署憑證，以使用安全通訊的 ssl。</span><span class="sxs-lookup"><span data-stu-id="8717b-161">Use the following steps to create a new, self-signed certificate to use for secure communications over SSL.</span></span>
  
1. <span data-ttu-id="8717b-162">擴充 web 應用程式使用相同的 URL 為 PublishingSite，但使用 SSL 搭配連接埠 443，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="8717b-162">Extend the web application to use the same URL as PublishingSite, but use SSL with port 443, as illustrated in the following figure.</span></span>
    
     ![擴充應用程式的設定](images/ExtendWebApp.jpg)
  
2. <span data-ttu-id="8717b-164">在 IIS 管理員中，按兩下 [**伺服器憑證**]。</span><span class="sxs-lookup"><span data-stu-id="8717b-164">In IIS Manager, double-click **Server Certificates**.</span></span>
    
3. <span data-ttu-id="8717b-p107">在 [**動作**] 窗格中，按一下 [**建立自我簽署憑證**。在 [**指定憑證的易記名稱**] 方塊中輸入憑證的易記名稱及 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="8717b-p107">In the **Actions** pane, click **Create Self-Signed Certificate**. Type a friendly name for the certificate in the **Specify a friendly name for the certificate** box, and then click **OK**.</span></span>
    
4. <span data-ttu-id="8717b-167">從 [**編輯網站繫結**] 對話方塊中，確定主機名稱的好記的名稱相同下圖所示。</span><span class="sxs-lookup"><span data-stu-id="8717b-167">From the **Edit Site Binding** dialog box, ensure the host name is the same as the friendly name, as illustrated in the following figures.</span></span>
    
     ![[自我簽署憑證] 精靈](images/SelfSignedCert.jpg)
  
     ![[編輯繫結] 方塊中的主機名稱](images/SelfSignedCert1.jpg)
  
5. <span data-ttu-id="8717b-170">從 Azure 管理入口網站中，按一下您要設定的虛擬機器] 和 [**端點**。</span><span class="sxs-lookup"><span data-stu-id="8717b-170">From the Azure management portal, click the virtual machine that you want to configure, and then click **Endpoints**.</span></span>
    
6. <span data-ttu-id="8717b-171">按一下 [**新增**] 和 [ **-->** （適用於下一步）。</span><span class="sxs-lookup"><span data-stu-id="8717b-171">Click **Add**, and then click **-->** (for Next).</span></span>
    
7. <span data-ttu-id="8717b-172">在 [**名稱**] 中輸入端點的名稱。</span><span class="sxs-lookup"><span data-stu-id="8717b-172">In **Name**, type a name for the endpoint.</span></span>
    
8. <span data-ttu-id="8717b-p108">在**公用連接埠**和**私人連接埠**，輸入您要使用的連接埠號碼和 [完成] 核取記號。這些數字可能會不同。本文目的，我們使用 443，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="8717b-p108">In **Public Port** and **Private Port**, type the port numbers that you want to use, and then click the check mark to complete. These numbers can be different. For the purposes of this article, we are using 443, as illustrated in the following figure.</span></span>
    
     ![Azure 中的「端點」設定](images/AddEndpoint.jpg)
  
    > [!NOTE]
    > <span data-ttu-id="8717b-177">如需如何將端點加入在 Azure 虛擬機器的其他資訊，請參閱[如何設定 「 端點虛擬機器](https://go.microsoft.com/fwlink/p/?LinkId=393126)。</span><span class="sxs-lookup"><span data-stu-id="8717b-177">For additional information about how to add an endpoint to a virtual machine in Azure, see [How to Set Up Endpoints to a Virtual Machine](https://go.microsoft.com/fwlink/p/?LinkId=393126).</span></span> 
  
9. <span data-ttu-id="8717b-178">從 [存取控制服務入口網站中，新增信賴憑證者，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="8717b-178">From the Access Control services portal, add a relying party, as illustrated in the following figure.</span></span>
    
     ![「新增信賴憑證者應用程式」設定](images/AddRelyingParty.jpg)
  
## <a name="create-a-rule-group-for-claims-based-authentication"></a><span data-ttu-id="8717b-180">建立宣告式驗證的規則群組</span><span class="sxs-lookup"><span data-stu-id="8717b-180">Create a rule group for claims-based authentication</span></span>

<span data-ttu-id="8717b-181">使用下列步驟來建立新規則群組來控制宣告式驗證。</span><span class="sxs-lookup"><span data-stu-id="8717b-181">Use the following steps to create a new rule group to control claims-based authentication.</span></span>
  
1. <span data-ttu-id="8717b-182">在左窗格中，按一下 [**規則群組**] 和 [**新增**。</span><span class="sxs-lookup"><span data-stu-id="8717b-182">In the left pane, click **Rule groups**, and then click **Add**.</span></span>
    
2. <span data-ttu-id="8717b-p109">輸入規則群組的名稱、 按一下 [**儲存**] 和 [**產生**。本文目的，我們使用**預設規則群組 for...in spvms.cloudapp.net**，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="8717b-p109">Type a name for the rule group, click **Save**, and then click **Generate**. For the purposes of this article, we are using **Default Rule Group for. spvms.cloudapp.net**, as illustrated in the following figure.</span></span>
    
     ![Azure 中的「規則群組」設定](images/RuleGroup.jpg)
  
     ![選擇 [產生] 之後的規則](images/GenerateRules.jpg)
  
    > [!NOTE]
    > <span data-ttu-id="8717b-187">如需如何建立規則群組的其他資訊，請參閱[規則群組和規則](https://go.microsoft.com/fwlink/p/?LinkId=393128)。</span><span class="sxs-lookup"><span data-stu-id="8717b-187">For additional information about how to create rule groups, see [Rule Groups and Rules](https://go.microsoft.com/fwlink/p/?LinkId=393128).</span></span> 
  
3. <span data-ttu-id="8717b-p110">按一下您想要變更的規則群組，然後按一下 [您想要變更的宣告規則。本文的目的，我們將宣告規則新增群組**名稱**傳遞為**upn**、 圖，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="8717b-p110">Click the rule group that you want to change, and then click the claim rule that you want to change. For the purposes of this article, we add a claim rule to the group to pass **name** as **upn**, as illustrated by the following figure.</span></span>
    
     ![Azure Access Control 中的宣告規則](images/ClaimRules.jpg)
  
4. <span data-ttu-id="8717b-191">刪除現有的宣告規則名為 [ **upn**]，並保持**UPN 宣告名稱**規則、 圖，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="8717b-191">Delete the existing claim rule named **upn**, and leave the **Name Claim to UPN** rule, as illustrated by the following figure.</span></span>
    
     ![Azure Access Control 中的規則設定](images/ClaimToUPN.jpg)
  
## <a name="configure-the-x509-certificate"></a><span data-ttu-id="8717b-193">設定的 X.509 憑證</span><span class="sxs-lookup"><span data-stu-id="8717b-193">Configure the X.509 certificate</span></span>

<span data-ttu-id="8717b-194">使用下列步驟來設定要用於 token 簽署的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="8717b-194">Use the following steps to configure the X.509 certificate to use for token signing.</span></span>
  
1. <span data-ttu-id="8717b-195">在 [存取控制服務] 窗格中的 [**開發**、 按一下 [**應用程式整合**。</span><span class="sxs-lookup"><span data-stu-id="8717b-195">In the Access Control Service pane, under **Development**, click **Application integration**.</span></span>
    
2. <span data-ttu-id="8717b-196">在**端點參考 （英文)**、 找出關聯租用 Azure **Federation.xml** ，然後在網址列中的瀏覽器中複製的位置。</span><span class="sxs-lookup"><span data-stu-id="8717b-196">In **Endpoint Reference**, locate the **Federation.xml** that is associated with your Azure tenant, and then copy the location in the address bar of a browser.</span></span>
    
3. <span data-ttu-id="8717b-197">在**Federation.xml**檔案中，找出**RoleDescriptor** ] 區段中，並將複製的資訊_<X509Certificate>_元素，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="8717b-197">In the **Federation.xml** file, locate the **RoleDescriptor** section, and copy the information from the _<X509Certificate>_ element, as illustrated in the following figure.</span></span>
    
     ![Federation.xml 檔案的 X509 憑證元素](images/X509Cert.jpg)
  
4. <span data-ttu-id="8717b-199">從 c 磁碟機根目錄\\，建立名為**憑證**的資料夾。</span><span class="sxs-lookup"><span data-stu-id="8717b-199">From the root of drive C:\\, create a folder named **Certificates**.</span></span>
    
5. <span data-ttu-id="8717b-200">X509Certificate 資訊儲存到資料夾 c:\\憑證檔案名稱， **AcsTokenSigning.cer**。</span><span class="sxs-lookup"><span data-stu-id="8717b-200">Save the X509Certificate information to the folder C:\\Certificates with the file name, **AcsTokenSigning.cer**.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="8717b-201">必須具有.cer 副檔名儲存的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="8717b-201">The file name must be saved with a .cer extension.</span></span> 
  
     ![將 X509Certificate 元素儲存為檔案](images/X509Cert_Save.jpg)
  
## <a name="create-a-claim-mapping-by-using-windows-powershell"></a><span data-ttu-id="8717b-203">使用 Windows PowerShell 建立的宣告對應</span><span class="sxs-lookup"><span data-stu-id="8717b-203">Create a claim mapping by using Windows PowerShell</span></span>

<span data-ttu-id="8717b-204">使用下列步驟來使用 Windows PowerShell 建立宣告對應。</span><span class="sxs-lookup"><span data-stu-id="8717b-204">Use the following steps to create a claim mapping by using Windows PowerShell.</span></span>
  
<span data-ttu-id="8717b-205">確認您具備下列成員資格：</span><span class="sxs-lookup"><span data-stu-id="8717b-205">Verify that you have the following memberships:</span></span>
  
1. <span data-ttu-id="8717b-206">SQL Server 執行個體上的**securityadmin**固定伺服器角色。</span><span class="sxs-lookup"><span data-stu-id="8717b-206">**securityadmin** fixed server role on the SQL Server instance.</span></span>
    
2. <span data-ttu-id="8717b-207">將更新的所有資料庫上的**db_owner**固定的資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="8717b-207">**db_owner** fixed database role on all databases that will be updated.</span></span>
    
3. <span data-ttu-id="8717b-208">在執行 Windows PowerShell cmdlet 的伺服器上的管理員群組。</span><span class="sxs-lookup"><span data-stu-id="8717b-208">Administrators group on the server on which you are running the Windows PowerShell cmdlets.</span></span>
    
<span data-ttu-id="8717b-209">系統管理員可以使用**Add-spshelladmin** cmdlet 授與使用 SharePoint 2013 cmdlet 的權限。</span><span class="sxs-lookup"><span data-stu-id="8717b-209">An administrator can use the **Add-SPShellAdmin** cmdlet to grant permissions to use SharePoint 2013 cmdlets.</span></span>
  
> [!NOTE]
> <span data-ttu-id="8717b-p111">如果您沒有權限，請連絡您的安裝程式系統管理員或 SQL Server 系統管理員以要求權限。如需 Windows PowerShell 的權限的其他資訊，請參閱 ＜ [Add-spshelladmin ＞](http://technet.microsoft.com/library/2ddfad84-7ca8-409e-878b-d09cb35ed4aa.aspx)。</span><span class="sxs-lookup"><span data-stu-id="8717b-p111">If you do not have permissions, contact your Setup administrator or SQL Server administrator to request permissions. For additional information about Windows PowerShell permissions, see [Add-SPShellAdmin](http://technet.microsoft.com/library/2ddfad84-7ca8-409e-878b-d09cb35ed4aa.aspx).</span></span> 
  
1. <span data-ttu-id="8717b-212">從 [**開始**] 功能表按一下 [**所有程式**]。</span><span class="sxs-lookup"><span data-stu-id="8717b-212">From the **Start** menu, click **All Programs**.</span></span>
    
2. <span data-ttu-id="8717b-213">按一下 [ **Microsoft SharePoint 2013 產品**]。</span><span class="sxs-lookup"><span data-stu-id="8717b-213">Click **Microsoft SharePoint 2013 Products**.</span></span>
    
3. <span data-ttu-id="8717b-214">按一下 [ **SharePoint 2013 管理命令介面**]。</span><span class="sxs-lookup"><span data-stu-id="8717b-214">Click **SharePoint 2013 Management Shell**.</span></span>
    
4. <span data-ttu-id="8717b-215">在 Windows PowerShell 命令提示字元處輸入下列命令來建立的宣告對應：</span><span class="sxs-lookup"><span data-stu-id="8717b-215">At the Windows PowerShell command prompt, type the following commands to create a claim mapping:</span></span>
    
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

## <a name="configure-sharepoint-for-the-new-identity-provider"></a><span data-ttu-id="8717b-216">設定 SharePoint 進行新的身分識別提供者</span><span class="sxs-lookup"><span data-stu-id="8717b-216">Configure SharePoint for the new identity provider</span></span>

<span data-ttu-id="8717b-217">使用下列步驟來設定您的 SharePoint 安裝至新的身分識別提供者的 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="8717b-217">Use the following steps to configure your SharePoint installation to the new identity provider for Azure AD.</span></span>
  
1. <span data-ttu-id="8717b-218">確認執行此程序的使用者帳戶為 SharePoint 伺服器陣列管理員群組的成員。</span><span class="sxs-lookup"><span data-stu-id="8717b-218">Verify that the user account that is performing this procedure is a member of the Farm Administrators SharePoint group.</span></span>
    
2. <span data-ttu-id="8717b-219">在管理中心首頁上，按一下 [**應用程式管理**。</span><span class="sxs-lookup"><span data-stu-id="8717b-219">In Central Administration, on the home page, click **Application Management**.</span></span>
    
3. <span data-ttu-id="8717b-220">按一下 [**應用程式管理**] 頁面上的 [ **Web 應用程式**] 區段中的 [**管理 web 應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="8717b-220">On the **Application Management** page, in the **Web Applications** section, click **Manage web applications**.</span></span>
    
4. <span data-ttu-id="8717b-221">按一下適當的 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="8717b-221">Click the appropriate web application.</span></span>
    
5. <span data-ttu-id="8717b-222">功能區上，按一下 [**驗證提供者**]。</span><span class="sxs-lookup"><span data-stu-id="8717b-222">From the ribbon, click **Authentication Providers**.</span></span>
    
6. <span data-ttu-id="8717b-p112">在 [**區域**] 按一下 [區域名稱。例如，**預設值**。</span><span class="sxs-lookup"><span data-stu-id="8717b-p112">Under **Zone**, click the name of the zone. For example, **Default**.</span></span>
    
7. <span data-ttu-id="8717b-p113">在 [**編輯驗證**] 頁面上的 [**宣告驗證類型**] 區段中選取 [**信任的身分識別提供者**，和 [提供者，即為本文目的**ACS 提供者**的名稱。按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="8717b-p113">On the **Edit Authentication** page, in the **Claims Authentication Types** section, select **Trusted Identity provider**, and then click the name of your provider, which for purposes of this article is **ACS Provider**. Click **OK**.</span></span>
    
8. <span data-ttu-id="8717b-227">下圖說明 「**信任的提供者**設定。</span><span class="sxs-lookup"><span data-stu-id="8717b-227">The following figure illustrates the **Trusted Provider** setting.</span></span>
    
![Web 應用程式中的「信任提供者」設定](images/AddProvider_Azure.jpg)
  
## <a name="set-the-permissions"></a><span data-ttu-id="8717b-229">設定的權限</span><span class="sxs-lookup"><span data-stu-id="8717b-229">Set the permissions</span></span>

<span data-ttu-id="8717b-230">使用下列步驟來設定存取 web 應用程式的權限。</span><span class="sxs-lookup"><span data-stu-id="8717b-230">Use the following steps to set the permissions to access the web application.</span></span>
  
1. <span data-ttu-id="8717b-231">在管理中心首頁上，按一下 [**應用程式管理**。</span><span class="sxs-lookup"><span data-stu-id="8717b-231">In Central Administration, on the home page, click **Application Management**.</span></span>
    
2. <span data-ttu-id="8717b-232">按一下 [**應用程式管理**] 頁面上的 [ **Web 應用程式**] 區段中的 [**管理 web 應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="8717b-232">On the **Application Management** page, in the **Web Applications** section, click **Manage web applications**.</span></span>
    
3. <span data-ttu-id="8717b-233">按一下適當的 web 應用程式] 和 [**使用者原則**。</span><span class="sxs-lookup"><span data-stu-id="8717b-233">Click the appropriate web application, and then click **User Policy**.</span></span>
    
4. <span data-ttu-id="8717b-234">在 [ **Web 應用程式的原則**中，按一下 [**新增使用者**]。</span><span class="sxs-lookup"><span data-stu-id="8717b-234">In **Policy for Web Application**, click **Add Users**.</span></span>
    
5. <span data-ttu-id="8717b-235">在 [**新增使用者**] 對話方塊中按一下適當的區域中**的區域**]，並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="8717b-235">In the **Add Users** dialog box, click the appropriate zone in **Zones**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="8717b-236">在 [**新增使用者**] 對話方塊中，typeuser2@blueskyabove.onmicrosoft.com （ACS 提供者）。</span><span class="sxs-lookup"><span data-stu-id="8717b-236">In the **Add Users** dialog box, typeuser2@blueskyabove.onmicrosoft.com (ACS Provider).</span></span>
    
7. <span data-ttu-id="8717b-237">在 [**權限**，按一下 [**完全控制**]。</span><span class="sxs-lookup"><span data-stu-id="8717b-237">In **Permissions**, click **Full Control**.</span></span>
    
8. <span data-ttu-id="8717b-238">按一下 [完成]，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="8717b-238">Click **Finish**, and then click **OK**.</span></span>
    
<span data-ttu-id="8717b-239">下圖說明 [**新增使用者**] 區段中的現有 web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="8717b-239">The following figure illustrates the **Add Users** section of an existing web application.</span></span>
  
![將使用者新增至現有 Web 應用程式](images/AddUsers_Azure.jpg)
  
## <a name="verify-the-new-provider"></a><span data-ttu-id="8717b-241">確認新的提供者</span><span class="sxs-lookup"><span data-stu-id="8717b-241">Verify the new provider</span></span>

<span data-ttu-id="8717b-242">使用下列步驟以確認新的身分識別提供者正常運作來確保新的驗證提供者會出現在 [登入提示。</span><span class="sxs-lookup"><span data-stu-id="8717b-242">Use the following steps to verify that the new identity provider is working by ensuring that the new authentication provider appears on the sign-in prompt.</span></span>
  
1. <span data-ttu-id="8717b-243">登入使用名為**藍色天空上方**，新的提供者，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="8717b-243">Sign in by using the new provider named **Blue Sky Above**, as illustrated in the following figure.</span></span>
    
     ![顯示新受信任提供者的登入對話方塊](images/BlueSkyAbove.jpg)
  
## <a name="additional-resources"></a><span data-ttu-id="8717b-245">其他資源</span><span class="sxs-lookup"><span data-stu-id="8717b-245">Additional resources</span></span>

[<span data-ttu-id="8717b-246">了解 WS-同盟</span><span class="sxs-lookup"><span data-stu-id="8717b-246">Understanding WS-Federation</span></span>](https://go.microsoft.com/fwlink/p/?linkid=188052)
  
[<span data-ttu-id="8717b-247">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="8717b-247">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
## <a name="join-the-discussion"></a><span data-ttu-id="8717b-248">參與討論</span><span class="sxs-lookup"><span data-stu-id="8717b-248">Join the discussion</span></span>

|<span data-ttu-id="8717b-249">**與我們連絡**</span><span class="sxs-lookup"><span data-stu-id="8717b-249">**Contact us**</span></span>|<span data-ttu-id="8717b-250">**描述**</span><span class="sxs-lookup"><span data-stu-id="8717b-250">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="8717b-251">**雲端採用內容您是否需要吗？**</span><span class="sxs-lookup"><span data-stu-id="8717b-251">**What cloud adoption content do you need?**</span></span> <br/> |<span data-ttu-id="8717b-p114">我們會建立橫跨多個 Microsoft cloud 平台及服務的雲端採用的內容。我們知道什麼構思我們雲端採用內容，或藉由傳送電子郵件給[cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20)要求特定的內容。</span><span class="sxs-lookup"><span data-stu-id="8717b-p114">We are creating content for cloud adoption that spans multiple Microsoft cloud platforms and services. Let us know what you think about our cloud adoption content, or ask for specific content by sending email to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).  </span></span><br/> |
|<span data-ttu-id="8717b-254">**加入雲端採用討論**</span><span class="sxs-lookup"><span data-stu-id="8717b-254">**Join the cloud adoption discussion**</span></span> <br/> |<span data-ttu-id="8717b-p115">如果您是找到他們需雲端式解決方案，請考慮加入雲端採用 Advisory 董 (CAAB) 與 Microsoft 內容的開發人員、 產業專業人員和客戶的從遍更大型、 加上鮮豔社群連線。若要加入，新增您自己的 Microsoft 技術社群[CAAB （雲端採用諮詢委員會） 空間](https://aka.ms/caab)的成員身分並在[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!)快速的電子郵件傳送意見。任何人都可以讀取上[CAAB 部落格](https://blogs.technet.com/b/solutions_advisory_board/)社群相關內容。不過，CAAB 成員取得說明新雲端採用資源和解決方案的私人研討會的邀請。</span><span class="sxs-lookup"><span data-stu-id="8717b-p115">If you are passionate about cloud-based solutions, consider joining the Cloud Adoption Advisory Board (CAAB) to connect with a larger, vibrant community of Microsoft content developers, industry professionals, and customers from around the globe. To join, add yourself as a member of the [CAAB (Cloud Adoption Advisory Board) space](https://aka.ms/caab) of the Microsoft Tech Community and send us a quick email at [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Anyone can read community-related content on the [CAAB blog](https://blogs.technet.com/b/solutions_advisory_board/). However, CAAB members get invitations to private webinars that describe new cloud adoption resources and solutions.  </span></span><br/> |
|<span data-ttu-id="8717b-258">**取得您在此處看到美工圖案**</span><span class="sxs-lookup"><span data-stu-id="8717b-258">**Get the art you see here**</span></span> <br/> |<span data-ttu-id="8717b-p116">如果您想編輯您在本文中看到藝術複本，我們樂於傳送給您。您的要求，包含 URL 及標題的圖案、 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20)的電子郵件。</span><span class="sxs-lookup"><span data-stu-id="8717b-p116">If you want an editable copy of the art you see in this article, we'll be glad to send it to you. Email your request, including the URL and title of the art, to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  </span></span><br/> |
   

