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
ms.openlocfilehash: e57414c3ed5af5c02b719d0c3639542e154be5bf
ms.sourcegitcommit: fbf33e74fd74c4ad6d60b2214329a3bbbdb3cc7c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="using-azure-ad-for-sharepoint-server-authentication"></a><span data-ttu-id="a048e-103">SharePoint Server 驗證使用 Azure AD</span><span class="sxs-lookup"><span data-stu-id="a048e-103">Using Azure AD for SharePoint Server Authentication</span></span>

 <span data-ttu-id="a048e-104">**摘要：**了解如何驗證您的 SharePoint Server 2016 使用者利用 Azure Active Directory。</span><span class="sxs-lookup"><span data-stu-id="a048e-104">**Summary:** Learn how to authenticate your SharePoint Server 2016 users with Azure Active Directory.</span></span>
  
> [!NOTE]
> <span data-ttu-id="a048e-105">本文根據吳 Evans、 Microsoft 首席程式經理的工作。</span><span class="sxs-lookup"><span data-stu-id="a048e-105">This article is based on the work of Kirk Evans, a Microsoft Principal Program Manager.</span></span> 

<blockquote>
<p><span data-ttu-id="a048e-p101">本文是指與 Azure Active Directory 圖表互動的程式碼範例。您可以下載程式碼範例[此處](https://github.com/kaevans/spsaml11/tree/master/scripts)。</span><span class="sxs-lookup"><span data-stu-id="a048e-p101">This article refers to code samples for interacting with Azure Active Directory Graph. You can download the code samples  [here](https://github.com/kaevans/spsaml11/tree/master/scripts).</span></span></p>
</blockquote>

<span data-ttu-id="a048e-p102">SharePoint Server 2016 提供以驗證使用者使用宣告式驗證，使其成為容易管理您的使用者進行其驗證您信任但其他人管理不同的身分識別提供者的能力。例如，而不是管理透過 Active Directory 網域服務 (AD DS) 的使用者驗證，您無法讓使用者使用 Azure Active Directory (Azure AD) 進行驗證。這可讓 onmicrosoft.com 尾碼其使用者名稱中使用的僅限雲端使用者驗證、 使用者與內部部署目錄同步處理及受邀來賓使用者從其他目錄。它也可讓您利用 Azure AD 的功能，例如多重要素驗證和進階的報告功能。</span><span class="sxs-lookup"><span data-stu-id="a048e-p102">SharePoint Server 2016 provides the ability to authenticate users using claims-based authentication, making it easy to manage your users by authenticating them with different identity providers that you trust but someone else manages. For example, instead of managing user authentication through Active Directory Domain Services (AD DS), you could enable users to authenticate using Azure Active Directory (Azure AD). This enables authentication for cloud-only users with the onmicrosoft.com suffix in their username, users synchronized with an on-premises directory, and invited guest users from other directories. It also enables you to take advantage of Azure AD features such as multi-factor authentication and advanced reporting capabilities.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a048e-p103">本文所述的解決方案也可搭配 SharePoint Server 2013;但是請記住 SharePoint Server 2013 已接近主流支援的結尾。如需詳細資訊，請參閱 Microsoft 技術支援週期的[原則](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202013)及[更新產品服務原則 SharePoint 2013](https://technet.microsoft.com/library/684173bb-e90a-4eb7-b268-b8d7458bc802(v=office.16).aspx)。</span><span class="sxs-lookup"><span data-stu-id="a048e-p103">The solution described in this article can also be used with SharePoint Server 2013; however, keep in mind that SharePoint Server 2013 is nearing the end of mainstream support. For more information, see [Microsoft Lifecycle Policy](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202013) and [Updated Product Servicing Policy for SharePoint 2013](https://technet.microsoft.com/library/684173bb-e90a-4eb7-b268-b8d7458bc802(v=office.16).aspx).</span></span>

<span data-ttu-id="a048e-p104">本文說明您可以如何使用 Azure AD 驗證您的使用者，而不是在內部部署 AD DS。在此組態中，Azure AD 會變成在 SharePoint Server 2016 的信任的身分識別提供者。此設定會新增不同本身的 SharePoint Server 2016 安裝所使用的 AD DS 驗證的使用者驗證方法。若要善加利用本文章，您應該熟悉 WS-同盟。如需詳細資訊，請參閱[了解 WS-同盟](https://go.microsoft.com/fwlink/p/?linkid=188052)。</span><span class="sxs-lookup"><span data-stu-id="a048e-p104">This article explains how you can use Azure AD to authenticate your users instead of your on-premises AD DS. In this configuration, Azure AD becomes a trusted identity provider for SharePoint Server 2016. This configuration adds a user authentication method that is separate from the AD DS authentication used by the SharePoint Server 2016 installation itself. To benefit from this article, you should be familiar with WS-Federation. For more information, see [Understanding WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052).</span></span>

![使用 Azure AD 的 SharePoint 驗證](images/SAML11/fig1-architecture.png)

<span data-ttu-id="a048e-p105">之前，此設定會具有必要的同盟服務等 Azure Access Control Service (ACS) 雲端或環境中主控的 Active Directory Federation Services (AD FS) 轉換為 SAML 1.1 從 SAML 2.0 權杖。這個轉換是不再需要 Azure AD 現在可讓發行的 SAML 1.1 權杖。圖表上方顯示 SharePoint 2016 示範已不再才能執行這個轉換的中介者在此組態中，使用者的驗證運作方式。</span><span class="sxs-lookup"><span data-stu-id="a048e-p105">Previously, this configuration would have required a federation service such as Azure Access Control Service (ACS) in the cloud or an environment that hosts Active Directory Federation Services (AD FS) to transform tokens from SAML 2.0 to SAML 1.1. This transformation is no longer required as Azure AD now enables issuing SAML 1.1 tokens. The diagram above shows how authentication works for SharePoint 2016 users in this configuration, demonstrating that there is no longer a requirement for an intermediary to perform this transformation.</span></span>

> [!NOTE]
> <span data-ttu-id="a048e-p106">此設定的運作是否 SharePoint 伺服器陣列架設在 Azure 虛擬機器或內部部署。它不需要開啟額外的防火牆連接埠不確認使用者可以從瀏覽器存取 Azure Active Directory。</span><span class="sxs-lookup"><span data-stu-id="a048e-p106">This configuration works whether the SharePoint farm is hosted in Azure virtual machines or on-premises. It does not require opening additional firewall ports other than ensuring users can access Azure Active Directory from their browser.</span></span>

<span data-ttu-id="a048e-125">如需 SharePoint 2016 協助工具資訊，請參閱 ＜[在 SharePoint Server 2016 中的協助工具指導方針](https://go.microsoft.com/fwlink/p/?LinkId=393123)。</span><span class="sxs-lookup"><span data-stu-id="a048e-125">For information about SharePoint 2016 accessibility, see [Accessibility Guidelines in SharePoint Server 2016](https://go.microsoft.com/fwlink/p/?LinkId=393123).</span></span>

## <a name="configuration-overview"></a><span data-ttu-id="a048e-126">設定概觀</span><span class="sxs-lookup"><span data-stu-id="a048e-126">Configuration overview</span></span>

<span data-ttu-id="a048e-127">請遵循下列一般步驟來設定您的環境使用 Azure AD 做為 SharePoint Server 2016 身分識別提供者。</span><span class="sxs-lookup"><span data-stu-id="a048e-127">Follow these general steps to set up your environment to use Azure AD as a SharePoint Server 2016 identity provider.</span></span>

1. <span data-ttu-id="a048e-128">建立新 Azure AD 目錄或使用現有的目錄。</span><span class="sxs-lookup"><span data-stu-id="a048e-128">Create a new Azure AD directory or use your existing directory.</span></span>
2. <span data-ttu-id="a048e-129">確定您想要安全與 Azure AD 的 web 應用程式的區域設定為使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="a048e-129">Ensure the zone for the web application that you want to secure with Azure AD is configured to use SSL.</span></span>
3. <span data-ttu-id="a048e-130">建立新的企業應用程式在 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="a048e-130">Create a new enterprise application in Azure AD.</span></span>
4. <span data-ttu-id="a048e-131">在 SharePoint Server 2016 設定新的受信任的身分識別提供者。</span><span class="sxs-lookup"><span data-stu-id="a048e-131">Configure a new trusted identity provider in SharePoint Server 2016.</span></span>
5. <span data-ttu-id="a048e-132">設定 web 應用程式的權限。</span><span class="sxs-lookup"><span data-stu-id="a048e-132">Set the permissions for the web application.</span></span>
6. <span data-ttu-id="a048e-133">新增的 SAML 1.1 token 發行原則中 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="a048e-133">Add a SAML 1.1 token issuance policy in Azure AD.</span></span>
7. <span data-ttu-id="a048e-134">確認新的提供者。</span><span class="sxs-lookup"><span data-stu-id="a048e-134">Verify the new provider.</span></span>

<span data-ttu-id="a048e-135">下列各節說明如何執行這些工作。</span><span class="sxs-lookup"><span data-stu-id="a048e-135">The following sections describe how to perform these tasks.</span></span>

## <a name="step-1-create-a-new-azure-ad-directory-or-use-your-existing-directory"></a><span data-ttu-id="a048e-136">步驟 1： 建立新 Azure AD 目錄或使用現有的目錄</span><span class="sxs-lookup"><span data-stu-id="a048e-136">Step 1: Create a new Azure AD directory or use your existing directory</span></span>

<span data-ttu-id="a048e-p107">在 Azure 入口網站 ([https://portal.azure.com](https://portal.azure.com))，建立新目錄。提供組織名稱、 初始網域名稱與國家或地區。</span><span class="sxs-lookup"><span data-stu-id="a048e-p107">In the Azure Portal ([https://portal.azure.com](https://portal.azure.com)), create a new directory. Provide the organization name, initial domain name, and the country or region.</span></span>

![建立目錄](images/SAML11/fig2-createdirectory.png) 

 <span data-ttu-id="a048e-p108">如果您已如 Microsoft Office 365 或 Microsoft Azure 訂閱時所用的目錄，您可以改用該目錄。您必須在目錄中註冊應用程式的權限。</span><span class="sxs-lookup"><span data-stu-id="a048e-p108">If you already have a directory such as the one used for Microsoft Office 365 or your Microsoft Azure subscription, you can use that directory instead. You must have permissions to register applications in the directory.</span></span>

## <a name="step-2-ensure-the-zone-for-the-web-application-that-you-want-to-secure-with-azure-ad-is-configured-to-use-ssl"></a><span data-ttu-id="a048e-142">步驟 2： 請確定您想要安全與 Azure AD 的 web 應用程式的區域設定為使用 SSL</span><span class="sxs-lookup"><span data-stu-id="a048e-142">Step 2: Ensure the zone for the web application that you want to secure with Azure AD is configured to use SSL</span></span>

<span data-ttu-id="a048e-p109">本文是撰寫使用參考架構中[執行高可用性 SharePoint 伺服器 2016 Azure 中的伺服器陣列](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint)。用以部署[這篇文章](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint)所述的解決方案文章的隨附指令碼建立不會使用 SSL 的網站。</span><span class="sxs-lookup"><span data-stu-id="a048e-p109">This article was written using the reference architecture in [Run a high availability SharePoint Server 2016 farm in Azure](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint). The article’s accompanying scripts used to deploy the solution described in [this article](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint) create a site that does not use SSL.</span></span>  

<span data-ttu-id="a048e-p110">使用 SAML 需要使用 SSL 設定應用程式。如果您的 SharePoint web 應用程式未設定成使用 SSL，請使用下列步驟來建立新的自我簽署的憑證來設定 SSL 的 web 應用程式。此設定僅供用於在實驗室環境和不能用於實際執行。實際執行環境應使用的簽署的憑證。</span><span class="sxs-lookup"><span data-stu-id="a048e-p110">Using SAML requires the application be configured to use SSL. If your SharePoint web application is not configured to use SSL, use the following steps to create a new self-signed certificate to configure the web application for SSL. This configuration is only meant for a lab environment and is not intended for production. Production environments should use a signed certificate.</span></span>

1. <span data-ttu-id="a048e-p111">移至 [**管理中心** > **應用程式管理** > **管理 Web 應用程式**，然後選擇 [需要可延伸以使用 SSL 的 web 應用程式。選取 web 應用程式並按一下 [**延伸功能區**] 按鈕。擴充 web 應用程式使用相同的 URL，但使用 SSL 搭配連接埠 443。</span><span class="sxs-lookup"><span data-stu-id="a048e-p111">Go to **Central Administration** > **Application Management** > **Manage Web Applications**, and choose the web application that needs to be extended to use SSL. Select the web application and click the **Extend ribbon** button. Extend the web application to use the same URL but use SSL with port 443.</span></span></br><span data-ttu-id="a048e-152">![擴充至其他 IIS 網站的 web 應用程式](images/SAML11/fig3-extendwebapptoiis.png)</span><span class="sxs-lookup"><span data-stu-id="a048e-152">![Extending the web app to another IIS site](images/SAML11/fig3-extendwebapptoiis.png)</span></span></br>
2. <span data-ttu-id="a048e-153">在 IIS 管理員中，按兩下 [**伺服器憑證**]。</span><span class="sxs-lookup"><span data-stu-id="a048e-153">In IIS Manager, double-click **Server Certificates**.</span></span>
3. <span data-ttu-id="a048e-p112">在 [**動作**] 窗格中，按一下 [**建立自我簽署憑證**。在指定的易記名稱] 的 [憑證] 方塊中輸入憑證的易記名稱及 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="a048e-p112">In the **Actions** pane, click **Create Self-Signed Certificate**. Type a friendly name for the certificate in the Specify a friendly name for the certificate box, and then click **OK**.</span></span>
4. <span data-ttu-id="a048e-156">從 [**編輯網站繫結**] 對話方塊中，確定主機名稱的好記的名稱相同下圖所示。</span><span class="sxs-lookup"><span data-stu-id="a048e-156">From the **Edit Site Binding** dialog box, ensure the host name is the same as the friendly name, as illustrated in the following image.</span></span></br><span data-ttu-id="a048e-157">![在 IIS 中編輯網站繫結](images/SAML11/fig4-editsitebinding.png)</span><span class="sxs-lookup"><span data-stu-id="a048e-157">![Editing site binding in IIS](images/SAML11/fig4-editsitebinding.png)</span></span></br>

<span data-ttu-id="a048e-158">每個 SharePoint 伺服器陣列中的 web 前端伺服器需要在 IIS 中設定網站繫結的憑證。</span><span class="sxs-lookup"><span data-stu-id="a048e-158">Each of the web front end servers in the SharePoint farm will require configuring the certificate for the site binding in IIS.</span></span>


## <a name="step-3-create-a-new-enterprise-application-in-azure-ad"></a><span data-ttu-id="a048e-159">步驟 3： 在 Azure AD 中建立新的企業應用程式</span><span class="sxs-lookup"><span data-stu-id="a048e-159">Step 3: Create a new enterprise application in Azure AD</span></span>

1. <span data-ttu-id="a048e-p113">在 Azure 入口網站 ([https://portal.azure.com](https://portal.azure.com))，開啟您 Azure AD 的目錄。按一下 [**企業應用程式**，然後按一下 [**新的應用程式**。選擇 [**非圖庫應用程式**。提供的名稱，例如*SharePoint SAML 整合*並按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="a048e-p113">In the Azure Portal ([https://portal.azure.com](https://portal.azure.com)), open your Azure AD directory. Click **Enterprise Applications**, then click **New application**. Choose **Non-gallery application**. Provide a name such as *SharePoint SAML Integration* and click **Add**.</span></span></br><span data-ttu-id="a048e-164">![新增新的非圖庫應用程式](images/SAML11/fig5-addnongalleryapp.png)</span><span class="sxs-lookup"><span data-stu-id="a048e-164">![Adding a new non-gallery application](images/SAML11/fig5-addnongalleryapp.png)</span></span></br>
2. <span data-ttu-id="a048e-p114">按一下 [單一登入連結功能窗格設定應用程式中。將 [**單一登入模式**] 下拉式清單變更為**saml 登入**以顯示應用程式的 SAML 設定屬性。設定具有下列內容：</span><span class="sxs-lookup"><span data-stu-id="a048e-p114">Click the Single sign-on link in the navigation pane to configure the application. Change the **Single Sign-on Mode** dropdown to **SAML-based Sign-on** to reveal the SAML configuration properties for the application. Configure with the following properties:</span></span></br>
    - <span data-ttu-id="a048e-168">識別碼：`urn:sharepoint:portal.contoso.local`</span><span class="sxs-lookup"><span data-stu-id="a048e-168">Identifier: `urn:sharepoint:portal.contoso.local`</span></span>
    - <span data-ttu-id="a048e-169">回覆 URL：`https://portal.contoso.local/_trust/default.aspx`</span><span class="sxs-lookup"><span data-stu-id="a048e-169">Reply URL: `https://portal.contoso.local/_trust/default.aspx`</span></span>
    - <span data-ttu-id="a048e-170">登入 URL：`https://portal.contoso.local/_trust/default.aspx`</span><span class="sxs-lookup"><span data-stu-id="a048e-170">Sign-on URL: `https://portal.contoso.local/_trust/default.aspx`</span></span>
    - <span data-ttu-id="a048e-171">使用者識別碼：`user.userprincipalname`</span><span class="sxs-lookup"><span data-stu-id="a048e-171">User Identifier: `user.userprincipalname`</span></span></br>
    - <span data-ttu-id="a048e-172">請注意： 請記得變更 Url 以想要保護的 SharePoint 網站的 URL 取代*portal.contoso.local*的方式。</span><span class="sxs-lookup"><span data-stu-id="a048e-172">Note: Remember to change the URLs by replacing *portal.contoso.local* with the URL of the SharePoint site you want to secure.</span></span></br>
3. <span data-ttu-id="a048e-173">設定包含下列資料列的表格 （類似以下的表格 1）：</span><span class="sxs-lookup"><span data-stu-id="a048e-173">Set up a table (similar to Table 1 below) that includes the following rows:</span></span></br> 
    - <span data-ttu-id="a048e-174">領域</span><span class="sxs-lookup"><span data-stu-id="a048e-174">Realm</span></span>
    - <span data-ttu-id="a048e-175">SAML 簽署憑證檔案的完整路徑</span><span class="sxs-lookup"><span data-stu-id="a048e-175">Full path to SAML signing certificate file</span></span>
    - <span data-ttu-id="a048e-176">SAML 單一登入服務的 URL （將*/saml2*取代*/wsfed*）</span><span class="sxs-lookup"><span data-stu-id="a048e-176">SAML Single Sign-On service URL (replacing */saml2* with */wsfed*)</span></span>
    - <span data-ttu-id="a048e-177">應用程式物件識別碼。</span><span class="sxs-lookup"><span data-stu-id="a048e-177">Application Object ID.</span></span> </br>
<span data-ttu-id="a048e-178">將 [ *Identifier* ] 值複製到插入資料表 (請參閱表 1 下方) 的*領域*屬性。</span><span class="sxs-lookup"><span data-stu-id="a048e-178">Copy the *Identifier* value into the *Realm* property into a table  (See Table 1 below.)</span></span>
4. <span data-ttu-id="a048e-179">儲存變更。</span><span class="sxs-lookup"><span data-stu-id="a048e-179">Save your changes.</span></span>
5. <span data-ttu-id="a048e-180">按一下以存取設定登入] 頁面上的**設定 （應用程式名稱）**連結。</span><span class="sxs-lookup"><span data-stu-id="a048e-180">Click the **Configure (app name)** link to access the Configure sign-on page.</span></span></br><span data-ttu-id="a048e-181">![設定單一登入頁面](images/SAML11/fig7-configssopage.png)</span><span class="sxs-lookup"><span data-stu-id="a048e-181">![Configuring a single-sign on page](images/SAML11/fig7-configssopage.png)</span></span></br> 
    -  <span data-ttu-id="a048e-p115">按一下 [下載為副檔名為.cer 檔的 SAML 簽署憑證的**SAML 簽署憑證-原始**連結。複製並貼到表格的下載檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="a048e-p115">Click the **SAML Signing Certificate - Raw** link to download the SAML Signing Certificate as a file with the .cer extension. Copy and paste the full path to the downloaded file into your table.</span></span>
    - <span data-ttu-id="a048e-184">複製並貼上的 SAML 單一登入服務 URL 連結到您、 取代*/wsfed* */saml2*部分 URL。</span><span class="sxs-lookup"><span data-stu-id="a048e-184">Copy and paste the SAML Single Sign-On Service URL link into your, replacing the */saml2* portion of the URL with */wsfed*.</span></span></br>
6.  <span data-ttu-id="a048e-p116">瀏覽至 [應用程式的 [**內容**] 窗格。複製並貼到您在步驟 3 設定表格的物件 ID 值。</span><span class="sxs-lookup"><span data-stu-id="a048e-p116">Navigate to the **Properties** pane for the application. Copy and paste the Object ID value into the table you set up in Step 3.</span></span></br><span data-ttu-id="a048e-187">![應用程式的 [內容] 窗格](images/SAML11/fig8-propertiespane.png)</span><span class="sxs-lookup"><span data-stu-id="a048e-187">![Properties pane for the application](images/SAML11/fig8-propertiespane.png)</span></span></br>
7. <span data-ttu-id="a048e-188">使用您所擷取的值，請確定您在步驟 3 設定表格的格式類似於下表 1。</span><span class="sxs-lookup"><span data-stu-id="a048e-188">Using the values you captured, make sure the table you set up in Step 3 resembles Table 1 below.</span></span>


| <span data-ttu-id="a048e-189">擷取的表格 1： 值</span><span class="sxs-lookup"><span data-stu-id="a048e-189">Table 1: Values captured</span></span>  |  |
|---------|---------|
|<span data-ttu-id="a048e-190">領域</span><span class="sxs-lookup"><span data-stu-id="a048e-190">Realm</span></span> | `urn:sharepoint:portal.contoso.local` |
|<span data-ttu-id="a048e-191">SAML 簽署憑證檔案的完整路徑</span><span class="sxs-lookup"><span data-stu-id="a048e-191">Full path to SAML signing certificate file</span></span> | `C:/temp/SharePoint SAML Integration.cer`  |
|<span data-ttu-id="a048e-192">SAML 單一登入服務 URL （取代為 /saml2 /wsfed）</span><span class="sxs-lookup"><span data-stu-id="a048e-192">SAML single sign-on service URL (replace /saml2 with /wsfed)</span></span> | `https://login.microsoftonline.com/b1726649-b616-460d-8d20-defab80d476c/wsfed` |
|<span data-ttu-id="a048e-193">應用程式物件識別碼</span><span class="sxs-lookup"><span data-stu-id="a048e-193">Application Object ID</span></span> | `a812f48b-d1e4-4c8e-93be-e4808c8ca3ac` |

> [!IMPORTANT]
> <span data-ttu-id="a048e-p117">在 URL 中的*/saml2*值取代為*/wsfed*。*/Saml2*端點會處理 SAML 2.0 權杖。*/Wsfed*端點啟用處理 SAML 1.1 權杖，並需要 SharePoint 2016 SAML 同盟。</span><span class="sxs-lookup"><span data-stu-id="a048e-p117">Replace the */saml2* value in the URL with */wsfed*. The */saml2* endpoint will process SAML 2.0 tokens. The */wsfed* endpoint enables processing SAML 1.1 tokens and is required for SharePoint 2016 SAML federation.</span></span>

## <a name="step-4-configure-a-new-trusted-identity-provider-in-sharepoint-server-2016"></a><span data-ttu-id="a048e-197">步驟 4： 在 SharePoint Server 2016 中設定新的受信任的身分識別提供者</span><span class="sxs-lookup"><span data-stu-id="a048e-197">Step 4: Configure a new trusted identity provider in SharePoint Server 2016</span></span>

<span data-ttu-id="a048e-p118">登入 SharePoint Server 2016 伺服器並開啟 SharePoint 2016 管理命令介面。填入 $realm、 $wsfedurl、 和 $filepath 表格 1 的值，並執行下列命令以設定新的信任的身分識別提供者。</span><span class="sxs-lookup"><span data-stu-id="a048e-p118">Sign into the SharePoint Server 2016 server and open the SharePoint 2016 Management Shell. Fill in the values of $realm, $wsfedurl, and $filepath from Table 1 and run the following commands to configure a new trusted identity provider.</span></span>

> [!TIP]
> <span data-ttu-id="a048e-200">如果您正在使用 PowerShell 的新或想要深入了解 PowerShell 的運作方式，請參閱[SharePoint PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/overview?view=sharepoint-ps)。</span><span class="sxs-lookup"><span data-stu-id="a048e-200">If you're new to using PowerShell or want to learn more about how PowerShell works, see [SharePoint PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/overview?view=sharepoint-ps).</span></span> 

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

<span data-ttu-id="a048e-201">接下來，請遵循下列步驟以啟用您的應用程式的信任的身分識別提供者：</span><span class="sxs-lookup"><span data-stu-id="a048e-201">Next, follow these steps to enable the trusted identity provider for your application:</span></span>
1. <span data-ttu-id="a048e-202">在管理中心中，瀏覽至 [**管理 Web 應用程式**並選取您想要安全與 Azure AD 的 web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a048e-202">In Central Administration, navigate to **Manage Web Application** and select the web application that you wish to secure with Azure AD.</span></span> 
2. <span data-ttu-id="a048e-203">在功能區上，按一下 [**驗證提供者**並選擇您想要使用的區域。</span><span class="sxs-lookup"><span data-stu-id="a048e-203">In the ribbon, click **Authentication Providers** and choose the zone that you wish to use.</span></span>
3. <span data-ttu-id="a048e-204">選取 [**信任的身分識別提供者**，並選取 [身分識別提供者所註冊名為*AzureAD*。</span><span class="sxs-lookup"><span data-stu-id="a048e-204">Select **Trusted Identity provider** and select the identify provider you just registered named *AzureAD*.</span></span>  
4. <span data-ttu-id="a048e-205">在登入頁面 URL 設定中，選取 [**自訂登入] 頁面上**，並提供"/_trust/"的值。</span><span class="sxs-lookup"><span data-stu-id="a048e-205">On the sign-in page URL setting, select **Custom sign in page** and provide the value “/_trust/”.</span></span> 
5. <span data-ttu-id="a048e-206">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="a048e-206">Click **OK**.</span></span>

![設定驗證提供者](images/SAML11/fig10-configauthprovider.png)

## <a name="step-5-set-the-permissions"></a><span data-ttu-id="a048e-208">步驟 5： 設定的權限</span><span class="sxs-lookup"><span data-stu-id="a048e-208">Step 5: Set the permissions</span></span>

<span data-ttu-id="a048e-209">必須授與使用者會登入 Azure AD 及存取 SharePoint 應用程式的存取。</span><span class="sxs-lookup"><span data-stu-id="a048e-209">The users who will log into Azure AD and access SharePoint must be granted access to the application.</span></span> 

1. <span data-ttu-id="a048e-p119">在 Azure 入口網站中開啟的 Azure AD 目錄。按一下 [**企業應用程式**，然後按一下 [**所有應用程式**。按一下您先前建立的應用程式 （SharePoint SAML 整合）。</span><span class="sxs-lookup"><span data-stu-id="a048e-p119">In the Azure Portal, open the Azure AD directory. Click **Enterprise Applications**, then click **All applications**. Click the application that you created previously (SharePoint SAML Integration).</span></span>
2. <span data-ttu-id="a048e-213">按一下 [**使用者與群組**]。</span><span class="sxs-lookup"><span data-stu-id="a048e-213">Click **Users and Groups**.</span></span> 
3. <span data-ttu-id="a048e-214">按一下 [新增使用者或群組有權限登入 SharePoint 使用 Azure AD 的 [**新增使用者**]。</span><span class="sxs-lookup"><span data-stu-id="a048e-214">Click **Add user** to add a user or group who will have permissions to log into SharePoint using Azure AD.</span></span>
4. <span data-ttu-id="a048e-215">選取使用者或群組然後按一下 [**指派**]。</span><span class="sxs-lookup"><span data-stu-id="a048e-215">Select the user or group then click **Assign**.</span></span>
 
<span data-ttu-id="a048e-p120">使用者已授與 Azure AD 的權限，但也必須授與 SharePoint 中的權限。使用下列步驟來設定存取 web 應用程式的權限。</span><span class="sxs-lookup"><span data-stu-id="a048e-p120">The user has been granted permission in Azure AD, but also must be granted permission in SharePoint. Use the following steps to set the permissions to access the web application.</span></span>

1. <span data-ttu-id="a048e-218">在管理中心中，按一下 [應用程式管理]。</span><span class="sxs-lookup"><span data-stu-id="a048e-218">In Central Administration, click **Application Management**.</span></span>
2. <span data-ttu-id="a048e-219">按一下 [**應用程式管理**] 頁面上的 [ **Web 應用程式**] 區段中的 [**管理 web 應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="a048e-219">On the **Application Management** page, in the **Web Applications** section, click **Manage web applications**.</span></span>
3. <span data-ttu-id="a048e-220">按一下適當的 web 應用程式] 和 [**使用者原則**。</span><span class="sxs-lookup"><span data-stu-id="a048e-220">Click the appropriate web application, and then click **User Policy**.</span></span>
4. <span data-ttu-id="a048e-221">在 [Web 應用程式的原則，按一下 [**新增使用者**]。</span><span class="sxs-lookup"><span data-stu-id="a048e-221">In Policy for Web Application, click **Add Users**.</span></span></br><span data-ttu-id="a048e-222">![搜尋使用者及其名稱宣告](images/SAML11/fig11-searchbynameclaim.png)</span><span class="sxs-lookup"><span data-stu-id="a048e-222">![Searching for a user by their name claim](images/SAML11/fig11-searchbynameclaim.png)</span></span></br>
5. <span data-ttu-id="a048e-223">在 [**新增使用者**] 對話方塊中按一下適當的區域中**的區域**]，並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a048e-223">In the **Add Users** dialog box, click the appropriate zone in **Zones**, and then click **Next**.</span></span>
6. <span data-ttu-id="a048e-224">在 [ **Web 應用程式的原則**] 對話方塊的 [**選擇使用者**] 區段中按一下 [**瀏覽**] 圖示。</span><span class="sxs-lookup"><span data-stu-id="a048e-224">In the **Policy for Web Application** dialog box, in the **Choose Users** section, click the **Browse** icon.</span></span>
7. <span data-ttu-id="a048e-225">在 [**尋找**] 文字方塊中，在您的目錄中輸入使用者的登入名稱並按一下 [**搜尋**]。</span><span class="sxs-lookup"><span data-stu-id="a048e-225">In the **Find** textbox, type the sign-in name for a user in your directory and click **Search**.</span></span> </br><span data-ttu-id="a048e-226">範例： *demouser@blueskyabove.onmicrosoft.com*。</span><span class="sxs-lookup"><span data-stu-id="a048e-226">Example: *demouser@blueskyabove.onmicrosoft.com*.</span></span>
8. <span data-ttu-id="a048e-227">在清單檢視中 AzureAD 標題、 下的 [選取的 name 屬性並按一下 [**新增**] 然後按一下**[確定]**以關閉 [] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a048e-227">Under the AzureAD heading in the list view, select the name property and click **Add** then click **OK** to close the dialog.</span></span>
9. <span data-ttu-id="a048e-228">在權限，按一下 [**完全控制**]。</span><span class="sxs-lookup"><span data-stu-id="a048e-228">In Permissions, click **Full Control**.</span></span></br><span data-ttu-id="a048e-229">![宣告使用者授與完全控制](images/SAML11/fig12-grantfullcontrol.png)</span><span class="sxs-lookup"><span data-stu-id="a048e-229">![Granting full control to a claims user](images/SAML11/fig12-grantfullcontrol.png)</span></span></br>
10. <span data-ttu-id="a048e-230">按一下 [完成]，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="a048e-230">Click **Finish**, and then click **OK**.</span></span>

## <a name="step-6-add-a-saml-11-token-issuance-policy-in-azure-ad"></a><span data-ttu-id="a048e-231">步驟 6： 在 Azure AD 中新增的 SAML 1.1 token 發行原則</span><span class="sxs-lookup"><span data-stu-id="a048e-231">Step 6: Add a SAML 1.1 token issuance policy in Azure AD</span></span>

<span data-ttu-id="a048e-p121">入口網站中建立的 Azure AD 應用程式之後，它會預設為使用 SAML 2.0。SharePoint Server 2016 需要的 SAML 1.1 token 格式。下列指令碼會移除預設 SAML 2.0 原則並將新的原則新增到問題 SAML 1.1 權杖。這段程式碼需要下載隨附的[範例示範互動 Azure Active Directory 圖表](https://github.com/kaevans/spsaml11/tree/master/scripts)。</span><span class="sxs-lookup"><span data-stu-id="a048e-p121">When the Azure AD application is created in the portal, it defaults to using SAML 2.0. SharePoint Server 2016 requires the SAML 1.1 token format. The following script will remove the default SAML 2.0 policy and add a new policy to issue SAML 1.1 tokens. This code requires downloading the accompanying [samples demonstrating interacting with Azure Active Directory Graph](https://github.com/kaevans/spsaml11/tree/master/scripts).</span></span> 


```
Import-Module <file path of Initialize.ps1> 
$objectid = "<Application Object ID from Table 1>"
$saml2policyid = Get-PoliciesAssignedToServicePrincipal -servicePrincipalId $objectid | ?{$_.displayName -EQ "TokenIssuancePolicy"} | select objectId
Remove-PolicyFromServicePrincipal -policyId $saml2policyid -servicePrincipalId $objectid
$policy = Add-TokenIssuancePolicy -DisplayName SPSAML11 -SigningAlgorithm "http://www.w3.org/2001/04/xmldsig-more#rsa-sha256" -TokenResponseSigningPolicy TokenOnly -SamlTokenVersion "1.1"
Set-PolicyToServicePrincipal -policyId $policy.objectId -servicePrincipalId $objectid
```
> <span data-ttu-id="a048e-p122">請注意務必要執行`Import-Module`命令在此範例所示。這會載入包含顯示的命令會在相依模組。您可能需要開啟已提升權限的命令提示字元處成功執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="a048e-p122">Note that it is important to run the `Import-Module` command as shown in this example. This will load a dependent module that contains the commands shown. You may need to open an elevated command prompt to successfully execute these commands.</span></span>

<span data-ttu-id="a048e-p123">這些範例 PowerShell 命令是範例如何對圖表 API 執行查詢。更多個 Azure AD 的 Token 發行原則的詳細資訊，請參閱[圖 API 參考 （英文） 原則上的作業](https://msdn.microsoft.com/en-us/library/azure/ad/graph/api/policy-operations#create-a-policy)。</span><span class="sxs-lookup"><span data-stu-id="a048e-p123">These sample PowerShell commands are examples of how to execute queries against the Graph API. For more details on Token Issuance Policies with Azure AD, see the [Graph API reference for operations on policy](https://msdn.microsoft.com/en-us/library/azure/ad/graph/api/policy-operations#create-a-policy).</span></span>

## <a name="step-7-verify-the-new-provider"></a><span data-ttu-id="a048e-241">步驟 7： 確認新的提供者</span><span class="sxs-lookup"><span data-stu-id="a048e-241">Step 7: Verify the new provider</span></span>

<span data-ttu-id="a048e-p124">開啟瀏覽器中您在先前步驟中設定的 web 應用程式的 url。您要重新導向至登入 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="a048e-p124">Open a browser to the URL of the web application that you configured in the previous steps. You are redirected to sign into Azure AD.</span></span>

![登入設定以進行同盟的 Azure AD](images/SAML11/fig13-examplesignin.png)

<span data-ttu-id="a048e-245">您會詢問您是否要保持已登入。</span><span class="sxs-lookup"><span data-stu-id="a048e-245">You are asked if you want to stay signed in.</span></span>

![維持已登入嗎？](images/SAML11/fig14-staysignedin.png)

<span data-ttu-id="a048e-247">最後，您可以存取您的 Azure Active Directory 租用戶中的使用者身分登入的網站。</span><span class="sxs-lookup"><span data-stu-id="a048e-247">Finally, you can access the site logged in as a user from your Azure Active Directory tenant.</span></span>

![使用者登入 SharePoint](images/SAML11/fig15-signedinsharepoint.png)

## <a name="managing-certificates"></a><span data-ttu-id="a048e-249">管理憑證</span><span class="sxs-lookup"><span data-stu-id="a048e-249">Managing certificates</span></span>
<span data-ttu-id="a048e-p125">請務必了解已設定為在上面的步驟 4 中的信任的身分識別提供者的簽署憑證已到期和必須更新。請參閱資訊的文章[同盟單一登入的 Azure Active Directory 中的管理憑證](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-sso-certs)上的憑證更新。一旦憑證有已更新在 Azure AD，下載至本機檔案並使用下列指令碼來設定信任的身分識別提供者的已更新的簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="a048e-p125">It is important to understand that the signing certificate that was configured for the trusted identity provider in step 4 above has an expiration date and must be renewed. See the article [Manage certificates for federated single sign-on in Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-sso-certs) for information on certificate renewal. Once the certificate has been renewed in Azure AD, download to a local file and use the following script to configure the trusted identity provider with the renewed signing certificate.</span></span> 

```
$filepath="<Full path to renewed SAML signing certificate file>"
$cert= New-Object System.Security.Cryptography.X509Certificates.X509Certificate2($filePath)
New-SPTrustedRootAuthority -Name "AzureAD" -Certificate $cert
Get-SPTrustedIdentityTokenIssuer "AzureAD" | Set-SPTrustedIdentityTokenIssuer -ImportTrustCertificate $cert
```

## <a name="fixing-people-picker"></a><span data-ttu-id="a048e-253">修正 [人員選擇]</span><span class="sxs-lookup"><span data-stu-id="a048e-253">Fixing People Picker</span></span>
<span data-ttu-id="a048e-p126">使用者現在可以登入 SharePoint 2016 使用從 Azure AD 的身分識別，但仍有改進的使用者經驗的機會。在人員選擇]，搜尋使用者呈現，多個搜尋結果。有 3 的宣告類型所建立的宣告對應的每個自訂的搜尋結果。若要選擇使用人員選擇] 的使用者，您必須完全輸入其使用者名稱及選擇**名稱**宣告結果。</span><span class="sxs-lookup"><span data-stu-id="a048e-p126">Users can now log into SharePoint 2016 using identities from Azure AD, but there are still opportunities for improvement to the user experience. For instance, searching for a user presents multiple search results in the people picker. There is a search result for each of the 3 claim types that were created in the claim mapping. To choose a user using the people picker, you must type their user name exactly and choose the **name** claim result.</span></span>

![宣告的搜尋結果](images/SAML11/fig16-claimssearchresults.png)

<span data-ttu-id="a048e-p127">無驗證值搜尋，可能會導致拼字錯誤或意外選擇錯誤的宣告指派例如**姓氏**類型的使用者宣告。這可防止使用者順利存取資源。</span><span class="sxs-lookup"><span data-stu-id="a048e-p127">There is no validation on the values you search for, which can lead to misspellings or users accidentally choosing the wrong claim type to assign such as the **SurName** claim. This can prevent users from successfully accessing resources.</span></span>

<span data-ttu-id="a048e-p128">若要協助進行此案例中，有開啟來源解決方案呼叫[AzureCP](https://yvand.github.io/AzureCP/) for SharePoint 2016 所提供的自訂宣告提供者。它會使用 Azure AD 圖表以解析使用者輸入以及執行驗證。深入瞭解[AzureCP](https://yvand.github.io/AzureCP/)。</span><span class="sxs-lookup"><span data-stu-id="a048e-p128">To assist with this scenario, there is an open-source solution called [AzureCP](https://yvand.github.io/AzureCP/) that provides a custom claims provider for SharePoint 2016. It will use the Azure AD Graph to resolve what users enter and perform validation. Learn more at [AzureCP](https://yvand.github.io/AzureCP/).</span></span> 

## <a name="additional-resources"></a><span data-ttu-id="a048e-264">其他資源</span><span class="sxs-lookup"><span data-stu-id="a048e-264">Additional resources</span></span>

[<span data-ttu-id="a048e-265">了解 WS-同盟</span><span class="sxs-lookup"><span data-stu-id="a048e-265">Understanding WS-Federation</span></span>](https://go.microsoft.com/fwlink/p/?linkid=188052)
  
[<span data-ttu-id="a048e-266">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="a048e-266">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
## <a name="join-the-discussion"></a><span data-ttu-id="a048e-267">參與討論</span><span class="sxs-lookup"><span data-stu-id="a048e-267">Join the discussion</span></span>

|<span data-ttu-id="a048e-268">**與我們連絡**</span><span class="sxs-lookup"><span data-stu-id="a048e-268">**Contact us**</span></span>|<span data-ttu-id="a048e-269">**描述**</span><span class="sxs-lookup"><span data-stu-id="a048e-269">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="a048e-270">**您需要什麼樣的雲端採用內容？**</span><span class="sxs-lookup"><span data-stu-id="a048e-270">**What cloud adoption content do you need?**</span></span> <br/> |<span data-ttu-id="a048e-p129">我們會建立橫跨多個 Microsoft cloud 平台及服務的雲端採用的內容。我們知道什麼構思我們雲端採用內容，或藉由傳送電子郵件給[cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20)要求特定的內容。</span><span class="sxs-lookup"><span data-stu-id="a048e-p129">We are creating content for cloud adoption that spans multiple Microsoft cloud platforms and services. Let us know what you think about our cloud adoption content, or ask for specific content by sending email to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).  </span></span><br/> |
|<span data-ttu-id="a048e-273">**加入雲端採用討論區**</span><span class="sxs-lookup"><span data-stu-id="a048e-273">**Join the cloud adoption discussion**</span></span> <br/> |<span data-ttu-id="a048e-p130">如果您是找到他們需雲端式解決方案，請考慮加入雲端採用 Advisory 董 (CAAB) 與 Microsoft 內容的開發人員、 產業專業人員和客戶的從遍更大型、 加上鮮豔社群連線。若要加入，新增您自己的 Microsoft 技術社群[CAAB （雲端採用諮詢委員會） 空間](https://aka.ms/caab)的成員身分並在[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!)快速的電子郵件傳送意見。任何人都可以讀取上[CAAB 部落格](https://blogs.technet.com/b/solutions_advisory_board/)社群相關內容。不過，CAAB 成員取得說明新雲端採用資源和解決方案的私人研討會的邀請。</span><span class="sxs-lookup"><span data-stu-id="a048e-p130">If you are passionate about cloud-based solutions, consider joining the Cloud Adoption Advisory Board (CAAB) to connect with a larger, vibrant community of Microsoft content developers, industry professionals, and customers from around the globe. To join, add yourself as a member of the [CAAB (Cloud Adoption Advisory Board) space](https://aka.ms/caab) of the Microsoft Tech Community and send us a quick email at [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Anyone can read community-related content on the [CAAB blog](https://blogs.technet.com/b/solutions_advisory_board/). However, CAAB members get invitations to private webinars that describe new cloud adoption resources and solutions.  </span></span><br/> |
|<span data-ttu-id="a048e-277">**取得您在這裡看到的美工圖案**</span><span class="sxs-lookup"><span data-stu-id="a048e-277">**Get the art you see here**</span></span> <br/> |<span data-ttu-id="a048e-p131">如果您想編輯您在本文中看到藝術複本，我們樂於傳送給您。您的要求，包含 URL 及標題的圖案、 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20)的電子郵件。</span><span class="sxs-lookup"><span data-stu-id="a048e-p131">If you want an editable copy of the art you see in this article, we'll be glad to send it to you. Email your request, including the URL and title of the art, to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  </span></span><br/> |
   

