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
# <a name="using-azure-ad-for-sharepoint-server-authentication"></a><span data-ttu-id="ed83f-103">針對 SharePoint Server 驗證使用 Azure AD</span><span class="sxs-lookup"><span data-stu-id="ed83f-103">Using Azure AD for SharePoint Server Authentication</span></span>

 <span data-ttu-id="ed83f-104">**摘要：** 了解如何驗證您的 SharePoint Server 2016 使用者與 Azure Active Directory。</span><span class="sxs-lookup"><span data-stu-id="ed83f-104">**Summary:** Learn how to authenticate your SharePoint Server 2016 users with Azure Active Directory.</span></span> 

<blockquote>
<p><span data-ttu-id="ed83f-105">本文是指與 Azure Active Directory Graph 互動的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="ed83f-105">This article refers to code samples for interacting with Azure Active Directory Graph.</span></span> <span data-ttu-id="ed83f-106">您可以下載的程式碼範例[這裡](https://github.com/kaevans/spsaml11/tree/master/scripts)。</span><span class="sxs-lookup"><span data-stu-id="ed83f-106">You can download the code samples [here](https://github.com/kaevans/spsaml11/tree/master/scripts).</span></span></p>
</blockquote>

<span data-ttu-id="ed83f-107">SharePoint Server 2016 提供的功能來驗證使用者使用宣告式驗證，以方便管理您的使用者進行驗證這些不同的身分識別提供者，您信任，但其他人管理。</span><span class="sxs-lookup"><span data-stu-id="ed83f-107">SharePoint Server 2016 provides the ability to authenticate users using claims-based authentication, making it easy to manage your users by authenticating them with different identity providers that you trust but someone else manages.</span></span> <span data-ttu-id="ed83f-108">例如，而不是管理透過 Active Directory 網域服務 (AD DS) 的使用者驗證，您可以讓使用者能夠使用 Azure Active Directory (Azure AD) 進行驗證。</span><span class="sxs-lookup"><span data-stu-id="ed83f-108">For example, instead of managing user authentication through Active Directory Domain Services (AD DS), you could enable users to authenticate using Azure Active Directory (Azure AD).</span></span> <span data-ttu-id="ed83f-109">這可讓與他們的 username 中的 onmicrosoft.com 後置詞的雲端專用使用者驗證、 使用者與內部部署目錄同步處理，並邀請來賓使用者從其他目錄。</span><span class="sxs-lookup"><span data-stu-id="ed83f-109">This enables authentication for cloud-only users with the onmicrosoft.com suffix in their username, users synchronized with an on-premises directory, and invited guest users from other directories.</span></span> <span data-ttu-id="ed83f-110">它也可讓您利用 Azure AD 功能，例如多重要素驗證和進階的報告功能。</span><span class="sxs-lookup"><span data-stu-id="ed83f-110">It also enables you to take advantage of Azure AD features such as multi-factor authentication and advanced reporting capabilities.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ed83f-111">本文中所述的解決方案也可搭配 SharePoint Server 2013;不過，請記住，SharePoint Server 2013 已接近主流支援的結尾。</span><span class="sxs-lookup"><span data-stu-id="ed83f-111">The solution described in this article can also be used with SharePoint Server 2013; however, keep in mind that SharePoint Server 2013 is nearing the end of mainstream support.</span></span> <span data-ttu-id="ed83f-112">如需詳細資訊，請參閱[Microsoft 週期原則](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202013)及[更新產品服務原則 for SharePoint 2013。](https://technet.microsoft.com/library/684173bb-e90a-4eb7-b268-b8d7458bc802(v=office.16).aspx)</span><span class="sxs-lookup"><span data-stu-id="ed83f-112">For more information, see [Microsoft Lifecycle Policy](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202013) and [Updated Product Servicing Policy for SharePoint 2013](https://technet.microsoft.com/library/684173bb-e90a-4eb7-b268-b8d7458bc802(v=office.16).aspx).</span></span>

<span data-ttu-id="ed83f-113">本文說明如何使用 Azure AD，而不是您內部部署 AD DS 以驗證您的使用者。</span><span class="sxs-lookup"><span data-stu-id="ed83f-113">This article explains how you can use Azure AD instead of your on-premises AD DS to authenticate your users.</span></span> <span data-ttu-id="ed83f-114">此組態中，在 Azure AD 會變成 SharePoint Server 2016 的受信任的身分識別提供者。</span><span class="sxs-lookup"><span data-stu-id="ed83f-114">In this configuration, Azure AD becomes a trusted identity provider for SharePoint Server 2016.</span></span> <span data-ttu-id="ed83f-115">此組態會新增獨立於 SharePoint Server 2016 安裝本身所使用的 AD DS 驗證的使用者驗證方法。</span><span class="sxs-lookup"><span data-stu-id="ed83f-115">This configuration adds a user authentication method that is separate from the AD DS authentication used by the SharePoint Server 2016 installation itself.</span></span> <span data-ttu-id="ed83f-116">若要享有這篇文章，您應該熟悉 WS-同盟。</span><span class="sxs-lookup"><span data-stu-id="ed83f-116">To benefit from this article, you should be familiar with WS-Federation.</span></span> <span data-ttu-id="ed83f-117">如需詳細資訊，請參閱 <<c0>了解 WS-同盟。</span><span class="sxs-lookup"><span data-stu-id="ed83f-117">For more information, see [Understanding WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052).</span></span> <span data-ttu-id="ed83f-118">如需詳細的 SharePoint 內部部署與 Azure Active Directory 整合的詳細資訊，請參閱 <<c0>專用教學課程。</span><span class="sxs-lookup"><span data-stu-id="ed83f-118">For detailed information about integration of SharePoint on-premises with Azure Active Directory, see the [dedicated tutorial](https://docs.microsoft.com/azure/active-directory/saas-apps/sharepoint-on-premises-tutorial).</span></span>

![使用 Azure AD 的 SharePoint 驗證](media/SAML11/fig1-architecture.png)

<span data-ttu-id="ed83f-120">先前，此組態會有需要同盟服務例如 Azure 存取控制服務 (ACS) 雲端或環境中主控 Active Directory Federation Services (AD FS) 轉換為 SAML 1.1 從 SAML 2.0 權杖。</span><span class="sxs-lookup"><span data-stu-id="ed83f-120">Previously, this configuration would have required a federation service such as Azure Access Control Service (ACS) in the cloud or an environment that hosts Active Directory Federation Services (AD FS) to transform tokens from SAML 2.0 to SAML 1.1.</span></span> <span data-ttu-id="ed83f-121">Azure AD 現在可讓發行 SAML 1.1 語彙基元，已不再需要此轉換。</span><span class="sxs-lookup"><span data-stu-id="ed83f-121">This transformation is no longer required as Azure AD now enables issuing SAML 1.1 tokens.</span></span> <span data-ttu-id="ed83f-122">上圖顯示 SharePoint 2016 中的使用者此組態中，示範已不再的中介者若要執行這項轉換需求的驗證運作方式。</span><span class="sxs-lookup"><span data-stu-id="ed83f-122">The diagram above shows how authentication works for SharePoint 2016 users in this configuration, demonstrating that there is no longer a requirement for an intermediary to perform this transformation.</span></span>

> [!NOTE]
> <span data-ttu-id="ed83f-123">此組態的運作是否在 SharePoint 伺服器陣列裝載在 Azure 虛擬機器或內部部署中。</span><span class="sxs-lookup"><span data-stu-id="ed83f-123">This configuration works whether the SharePoint farm is hosted in Azure virtual machines or on-premises.</span></span> <span data-ttu-id="ed83f-124">它不需要開啟額外的防火牆連接埠以外確保使用者可以從他們的瀏覽器存取 Azure Active Directory。</span><span class="sxs-lookup"><span data-stu-id="ed83f-124">It does not require opening additional firewall ports other than ensuring users can access Azure Active Directory from their browser.</span></span>

<span data-ttu-id="ed83f-125">如需 SharePoint 2016 的協助工具資訊，請參閱 <<c0>在 SharePoint Server 2016 中的協助工具指導方針。</span><span class="sxs-lookup"><span data-stu-id="ed83f-125">For information about SharePoint 2016 accessibility, see [Accessibility Guidelines in SharePoint Server 2016](https://go.microsoft.com/fwlink/p/?LinkId=393123).</span></span>

## <a name="configuration-overview"></a><span data-ttu-id="ed83f-126">設定概觀</span><span class="sxs-lookup"><span data-stu-id="ed83f-126">Configuration overview</span></span>

<span data-ttu-id="ed83f-127">遵循下列一般步驟來設定您的環境，以使用 Azure AD 做為 SharePoint Server 2016 的身分識別提供者。</span><span class="sxs-lookup"><span data-stu-id="ed83f-127">Follow these general steps to set up your environment to use Azure AD as a SharePoint Server 2016 identity provider.</span></span>

1. <span data-ttu-id="ed83f-128">建立新的 Azure AD 目錄，或使用您現有的目錄。</span><span class="sxs-lookup"><span data-stu-id="ed83f-128">Create a new Azure AD directory or use your existing directory.</span></span>
2. <span data-ttu-id="ed83f-129">請確定您要保護與 Azure AD 的 web 應用程式的區域設定為使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="ed83f-129">Ensure the zone for the web application that you want to secure with Azure AD is configured to use SSL.</span></span>
3. <span data-ttu-id="ed83f-130">在 Azure AD 中建立新的企業應用程式。</span><span class="sxs-lookup"><span data-stu-id="ed83f-130">Create a new enterprise application in Azure AD.</span></span>
4. <span data-ttu-id="ed83f-131">在 SharePoint Server 2016 中設定新的受信任的身分識別提供者。</span><span class="sxs-lookup"><span data-stu-id="ed83f-131">Configure a new trusted identity provider in SharePoint Server 2016.</span></span>
5. <span data-ttu-id="ed83f-132">設定 web 應用程式的權限。</span><span class="sxs-lookup"><span data-stu-id="ed83f-132">Set the permissions for the web application.</span></span>
6. <span data-ttu-id="ed83f-133">在 Azure AD 中新增 SAML 1.1 token 發行原則。</span><span class="sxs-lookup"><span data-stu-id="ed83f-133">Add a SAML 1.1 token issuance policy in Azure AD.</span></span>
7. <span data-ttu-id="ed83f-134">確認新的提供者。</span><span class="sxs-lookup"><span data-stu-id="ed83f-134">Verify the new provider.</span></span>

<span data-ttu-id="ed83f-135">下列各節說明如何執行這些工作。</span><span class="sxs-lookup"><span data-stu-id="ed83f-135">The following sections describe how to perform these tasks.</span></span>

## <a name="step-1-create-a-new-azure-ad-directory-or-use-your-existing-directory"></a><span data-ttu-id="ed83f-136">步驟 1： 建立新的 Azure AD 目錄，或使用您現有的目錄</span><span class="sxs-lookup"><span data-stu-id="ed83f-136">Step 1: Create a new Azure AD directory or use your existing directory</span></span>

<span data-ttu-id="ed83f-137">在 Azure 入口網站 ([https://portal.azure.com](https://portal.azure.com))，建立新的目錄。</span><span class="sxs-lookup"><span data-stu-id="ed83f-137">In the Azure Portal ([https://portal.azure.com](https://portal.azure.com)), create a new directory.</span></span> <span data-ttu-id="ed83f-138">提供組織名稱、 初始網域名稱和國家/地區或區域。</span><span class="sxs-lookup"><span data-stu-id="ed83f-138">Provide the organization name, initial domain name, and the country or region.</span></span>

![建立目錄](media/SAML11/fig2-createdirectory.png) 

 <span data-ttu-id="ed83f-140">如果您已如用於 Microsoft Office 365 或 Microsoft Azure 訂閱的目錄，您可以改為使用該目錄。</span><span class="sxs-lookup"><span data-stu-id="ed83f-140">If you already have a directory such as the one used for Microsoft Office 365 or your Microsoft Azure subscription, you can use that directory instead.</span></span> <span data-ttu-id="ed83f-141">您必須在目錄中登錄應用程式的權限。</span><span class="sxs-lookup"><span data-stu-id="ed83f-141">You must have permissions to register applications in the directory.</span></span>

## <a name="step-2-ensure-the-zone-for-the-web-application-that-you-want-to-secure-with-azure-ad-is-configured-to-use-ssl"></a><span data-ttu-id="ed83f-142">步驟 2： 確保您要保護與 Azure AD 的 web 應用程式的區域設定為使用 SSL</span><span class="sxs-lookup"><span data-stu-id="ed83f-142">Step 2: Ensure the zone for the web application that you want to secure with Azure AD is configured to use SSL</span></span>

<span data-ttu-id="ed83f-143">本文已寫入使用中[執行的高可用性 SharePoint Server 2016 伺服器陣列在 Azure 中](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint)的參考架構。</span><span class="sxs-lookup"><span data-stu-id="ed83f-143">This article was written using the reference architecture in [Run a high availability SharePoint Server 2016 farm in Azure](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint).</span></span> <span data-ttu-id="ed83f-144">用以部署[這篇文章](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint)所述的解決方案的文章隨附指令碼建立的網站，不會使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="ed83f-144">The article’s accompanying scripts used to deploy the solution described in [this article](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint) create a site that does not use SSL.</span></span>  

<span data-ttu-id="ed83f-145">使用 SAML 需要應用程式設定為使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="ed83f-145">Using SAML requires the application be configured to use SSL.</span></span> <span data-ttu-id="ed83f-146">如果您的 SharePoint web 應用程式未設定成使用 SSL，請使用下列步驟來建立新的自我簽署的憑證，來設定 SSL 的 web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ed83f-146">If your SharePoint web application is not configured to use SSL, use the following steps to create a new self-signed certificate to configure the web application for SSL.</span></span> <span data-ttu-id="ed83f-147">此設定僅供用於在實驗室環境，而不是為了建立生產環境。</span><span class="sxs-lookup"><span data-stu-id="ed83f-147">This configuration is only meant for a lab environment and is not intended for production.</span></span> <span data-ttu-id="ed83f-148">實際執行環境中應使用的簽署的憑證。</span><span class="sxs-lookup"><span data-stu-id="ed83f-148">Production environments should use a signed certificate.</span></span>

1. <span data-ttu-id="ed83f-149">移至**管理中心** > **應用程式管理** > **管理 Web 應用程式**，然後選擇 [需要擴充，以使用 SSL 的 web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ed83f-149">Go to **Central Administration** > **Application Management** > **Manage Web Applications**, and choose the web application that needs to be extended to use SSL.</span></span> <span data-ttu-id="ed83f-150">選取 web 應用程式，然後按一下 [**擴充功能區**按鈕。</span><span class="sxs-lookup"><span data-stu-id="ed83f-150">Select the web application and click the **Extend ribbon** button.</span></span> <span data-ttu-id="ed83f-151">擴充 web 應用程式使用相同的 URL，但使用 SSL 與連接埠 443。</span><span class="sxs-lookup"><span data-stu-id="ed83f-151">Extend the web application to use the same URL but use SSL with port 443.</span></span><br/><span data-ttu-id="ed83f-152">![擴充 web 應用程式至其他 IIS 網站](media/SAML11/fig3-extendwebapptoiis.png)</span><span class="sxs-lookup"><span data-stu-id="ed83f-152">![Extending the web app to another IIS site](media/SAML11/fig3-extendwebapptoiis.png)</span></span><br/>
2. <span data-ttu-id="ed83f-153">在 [IIS 管理員] 中，按兩下 [**伺服器憑證**。</span><span class="sxs-lookup"><span data-stu-id="ed83f-153">In IIS Manager, double-click **Server Certificates**.</span></span>
3. <span data-ttu-id="ed83f-154">在 [動作]\*\*\*\* 窗格中，按一下 [建立自我簽署憑證]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ed83f-154">In the **Actions** pane, click **Create Self-Signed Certificate**.</span></span> <span data-ttu-id="ed83f-155">在 [指定好記名稱] 的 [憑證] 方塊中，輸入憑證的易記名稱，然後按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="ed83f-155">Type a friendly name for the certificate in the Specify a friendly name for the certificate box, and then click **OK**.</span></span>
4. <span data-ttu-id="ed83f-156">從 [**編輯網站繫結**] 對話方塊中，確定主機名稱是相同的好記的名稱，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="ed83f-156">From the **Edit Site Binding** dialog box, ensure the host name is the same as the friendly name, as illustrated in the following image.</span></span><br/><span data-ttu-id="ed83f-157">![在 IIS 中編輯網站繫結](media/SAML11/fig4-editsitebinding.png)</span><span class="sxs-lookup"><span data-stu-id="ed83f-157">![Editing site binding in IIS](media/SAML11/fig4-editsitebinding.png)</span></span><br/>

<span data-ttu-id="ed83f-158">每個 SharePoint 伺服器陣列中的 web 前端伺服器時，需要在 IIS 中設定網站繫結的憑證。</span><span class="sxs-lookup"><span data-stu-id="ed83f-158">Each of the web front end servers in the SharePoint farm will require configuring the certificate for the site binding in IIS.</span></span>


## <a name="step-3-create-a-new-enterprise-application-in-azure-ad"></a><span data-ttu-id="ed83f-159">步驟 3： 在 Azure AD 中建立新的企業應用程式</span><span class="sxs-lookup"><span data-stu-id="ed83f-159">Step 3: Create a new enterprise application in Azure AD</span></span>

1. <span data-ttu-id="ed83f-160">在 Azure 入口網站 ([https://portal.azure.com](https://portal.azure.com))，開啟您的 Azure AD 目錄。</span><span class="sxs-lookup"><span data-stu-id="ed83f-160">In the Azure Portal ([https://portal.azure.com](https://portal.azure.com)), open your Azure AD directory.</span></span> <span data-ttu-id="ed83f-161">按一下 [**企業應用程式**，然後按一下 [**新的應用程式**。</span><span class="sxs-lookup"><span data-stu-id="ed83f-161">Click **Enterprise Applications**, then click **New application**.</span></span> <span data-ttu-id="ed83f-162">選擇 [**非庫應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="ed83f-162">Choose **Non-gallery application**.</span></span> <span data-ttu-id="ed83f-163">提供的名稱，例如*SharePoint SAML 整合*，並按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="ed83f-163">Provide a name such as *SharePoint SAML Integration* and click **Add**.</span></span><br/><span data-ttu-id="ed83f-164">![新增新的非庫應用程式](media/SAML11/fig5-addnongalleryapp.png)</span><span class="sxs-lookup"><span data-stu-id="ed83f-164">![Adding a new non-gallery application](media/SAML11/fig5-addnongalleryapp.png)</span></span><br/>
2. <span data-ttu-id="ed83f-165">按一下 [單一登入連結功能窗格設定應用程式中。</span><span class="sxs-lookup"><span data-stu-id="ed83f-165">Click the Single sign-on link in the navigation pane to configure the application.</span></span> <span data-ttu-id="ed83f-166">將**單一登入模式**] 下拉式清單變更為**SAML 型登入**以顯示應用程式的 SAML 設定屬性。</span><span class="sxs-lookup"><span data-stu-id="ed83f-166">Change the **Single Sign-on Mode** dropdown to **SAML-based Sign-on** to reveal the SAML configuration properties for the application.</span></span> <span data-ttu-id="ed83f-167">設定具有下列內容：</span><span class="sxs-lookup"><span data-stu-id="ed83f-167">Configure with the following properties:</span></span><br/>
    - <span data-ttu-id="ed83f-168">識別碼：`urn:sharepoint:portal.contoso.local`</span><span class="sxs-lookup"><span data-stu-id="ed83f-168">Identifier: `urn:sharepoint:portal.contoso.local`</span></span>
    - <span data-ttu-id="ed83f-169">回覆 URL:`https://portal.contoso.local/_trust/default.aspx`</span><span class="sxs-lookup"><span data-stu-id="ed83f-169">Reply URL: `https://portal.contoso.local/_trust/default.aspx`</span></span>
    - <span data-ttu-id="ed83f-170">登入 URL:`https://portal.contoso.local/_trust/default.aspx`</span><span class="sxs-lookup"><span data-stu-id="ed83f-170">Sign-on URL: `https://portal.contoso.local/_trust/default.aspx`</span></span>
    - <span data-ttu-id="ed83f-171">使用者識別碼：`user.userprincipalname`</span><span class="sxs-lookup"><span data-stu-id="ed83f-171">User Identifier: `user.userprincipalname`</span></span><br/>
    - <span data-ttu-id="ed83f-172">附註： 請記得，變更 Url *portal.contoso.local*取代為您要保護的 SharePoint 網站的 URL。</span><span class="sxs-lookup"><span data-stu-id="ed83f-172">Note: Remember to change the URLs by replacing *portal.contoso.local* with the URL of the SharePoint site you want to secure.</span></span><br/>
3. <span data-ttu-id="ed83f-173">設定表格 （類似下列的表 1），其中包含下列資料列：</span><span class="sxs-lookup"><span data-stu-id="ed83f-173">Set up a table (similar to Table 1 below) that includes the following rows:</span></span><br/> 
    - <span data-ttu-id="ed83f-174">Realm</span><span class="sxs-lookup"><span data-stu-id="ed83f-174">Realm</span></span>
    - <span data-ttu-id="ed83f-175">SAML 簽署的憑證檔案的完整路徑</span><span class="sxs-lookup"><span data-stu-id="ed83f-175">Full path to SAML signing certificate file</span></span>
    - <span data-ttu-id="ed83f-176">SAML 單一登入服務的 URL （取代為 */saml2* */wsfed*）</span><span class="sxs-lookup"><span data-stu-id="ed83f-176">SAML Single Sign-On service URL (replacing */saml2* with */wsfed*)</span></span>
    - <span data-ttu-id="ed83f-177">應用程式的物件 id。</span><span class="sxs-lookup"><span data-stu-id="ed83f-177">Application Object ID.</span></span> <br/>
<span data-ttu-id="ed83f-178">將 [ *Identifier* ] 值複製到資料表 (請參閱表 1 下方) 的*領域*屬性。</span><span class="sxs-lookup"><span data-stu-id="ed83f-178">Copy the *Identifier* value into the *Realm* property into a table  (See Table 1 below.)</span></span>
4. <span data-ttu-id="ed83f-179">儲存變更。</span><span class="sxs-lookup"><span data-stu-id="ed83f-179">Save your changes.</span></span>
5. <span data-ttu-id="ed83f-180">按一下 [**設定 （應用程式名稱）** 連結，以存取設定登入] 頁面。</span><span class="sxs-lookup"><span data-stu-id="ed83f-180">Click the **Configure (app name)** link to access the Configure sign-on page.</span></span><br/><span data-ttu-id="ed83f-181">![設定單一登入] 頁面上](media/SAML11/fig7-configssopage.png)</span><span class="sxs-lookup"><span data-stu-id="ed83f-181">![Configuring a single-sign on page](media/SAML11/fig7-configssopage.png)</span></span><br/> 
    -  <span data-ttu-id="ed83f-182">按一下 [下載 SAML 簽署憑證為副檔名為.cer 檔的**SAML 簽章憑證-原始**連結。</span><span class="sxs-lookup"><span data-stu-id="ed83f-182">Click the **SAML Signing Certificate - Raw** link to download the SAML Signing Certificate as a file with the .cer extension.</span></span> <span data-ttu-id="ed83f-183">複製並貼入表格中的下載的檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="ed83f-183">Copy and paste the full path to the downloaded file into your table.</span></span>
    - <span data-ttu-id="ed83f-184">複製並貼到 SAML 單一登入服務的 URL 連結，以 */wsfed*取代 URL */saml2*部分。</span><span class="sxs-lookup"><span data-stu-id="ed83f-184">Copy and paste the SAML Single Sign-On Service URL link into your, replacing the */saml2* portion of the URL with */wsfed*.</span></span><br/>
6.  <span data-ttu-id="ed83f-185">瀏覽至應用程式的 [**屬性**] 窗格。</span><span class="sxs-lookup"><span data-stu-id="ed83f-185">Navigate to the **Properties** pane for the application.</span></span> <span data-ttu-id="ed83f-186">複製並貼入您在步驟 3 中設定資料表中的物件 ID 值。</span><span class="sxs-lookup"><span data-stu-id="ed83f-186">Copy and paste the Object ID value into the table you set up in Step 3.</span></span><br/><span data-ttu-id="ed83f-187">![應用程式的 [屬性] 窗格](media/SAML11/fig8-propertiespane.png)</span><span class="sxs-lookup"><span data-stu-id="ed83f-187">![Properties pane for the application](media/SAML11/fig8-propertiespane.png)</span></span><br/>
7. <span data-ttu-id="ed83f-188">使用您所擷取的值，請確定您在步驟 3 中設定資料表類似下列的表 1。</span><span class="sxs-lookup"><span data-stu-id="ed83f-188">Using the values you captured, make sure the table you set up in Step 3 resembles Table 1 below.</span></span>


| <span data-ttu-id="ed83f-189">擷取的表 1： 值</span><span class="sxs-lookup"><span data-stu-id="ed83f-189">Table 1: Values captured</span></span>  |  |
|---------|---------|
|<span data-ttu-id="ed83f-190">Realm</span><span class="sxs-lookup"><span data-stu-id="ed83f-190">Realm</span></span> | `urn:sharepoint:portal.contoso.local` |
|<span data-ttu-id="ed83f-191">SAML 簽署的憑證檔案的完整路徑</span><span class="sxs-lookup"><span data-stu-id="ed83f-191">Full path to SAML signing certificate file</span></span> | `C:/temp/SharePoint SAML Integration.cer`  |
|<span data-ttu-id="ed83f-192">SAML 單一登入服務 URL （取代為 /saml2 /wsfed）</span><span class="sxs-lookup"><span data-stu-id="ed83f-192">SAML single sign-on service URL (replace /saml2 with /wsfed)</span></span> | `https://login.microsoftonline.com/b1726649-b616-460d-8d20-defab80d476c/wsfed` |
|<span data-ttu-id="ed83f-193">應用程式物件識別碼</span><span class="sxs-lookup"><span data-stu-id="ed83f-193">Application Object ID</span></span> | `a812f48b-d1e4-4c8e-93be-e4808c8ca3ac` |

> [!IMPORTANT]
> <span data-ttu-id="ed83f-194">取代 */wsfed* */saml2*值在 URL 中。</span><span class="sxs-lookup"><span data-stu-id="ed83f-194">Replace the */saml2* value in the URL with */wsfed*.</span></span> <span data-ttu-id="ed83f-195">*/Saml2*端點會處理 SAML 2.0 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="ed83f-195">The */saml2* endpoint will process SAML 2.0 tokens.</span></span> <span data-ttu-id="ed83f-196">*/Wsfed*端點啟用處理 SAML 1.1 權杖，並且是必要的 SharePoint 2016 SAML 同盟。</span><span class="sxs-lookup"><span data-stu-id="ed83f-196">The */wsfed* endpoint enables processing SAML 1.1 tokens and is required for SharePoint 2016 SAML federation.</span></span>

## <a name="step-4-configure-a-new-trusted-identity-provider-in-sharepoint-server-2016"></a><span data-ttu-id="ed83f-197">步驟 4： 在 SharePoint Server 2016 中設定新的受信任的身分識別提供者</span><span class="sxs-lookup"><span data-stu-id="ed83f-197">Step 4: Configure a new trusted identity provider in SharePoint Server 2016</span></span>

<span data-ttu-id="ed83f-198">登入 SharePoint Server 2016 伺服器，並開啟 [SharePoint 2016 管理命令介面。</span><span class="sxs-lookup"><span data-stu-id="ed83f-198">Sign into the SharePoint Server 2016 server and open the SharePoint 2016 Management Shell.</span></span> <span data-ttu-id="ed83f-199">填寫 $realm、 $wsfedurl 及 $filepath 表格 1 的值，並執行下列命令，以設定新的受信任的身分識別提供者。</span><span class="sxs-lookup"><span data-stu-id="ed83f-199">Fill in the values of $realm, $wsfedurl, and $filepath from Table 1 and run the following commands to configure a new trusted identity provider.</span></span>

> [!TIP]
> <span data-ttu-id="ed83f-200">如果您是使用 PowerShell 新手，或想要深入了解 PowerShell 的運作方式，請參閱 < <b0>SharePoint PowerShell</b0>。</span><span class="sxs-lookup"><span data-stu-id="ed83f-200">If you're new to using PowerShell or want to learn more about how PowerShell works, see [SharePoint PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/overview?view=sharepoint-ps).</span></span> 

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

<span data-ttu-id="ed83f-201">接下來，請遵循下列步驟來啟用您的應用程式的信任的身分識別提供者：</span><span class="sxs-lookup"><span data-stu-id="ed83f-201">Next, follow these steps to enable the trusted identity provider for your application:</span></span>
1. <span data-ttu-id="ed83f-202">在管理中心內，瀏覽至 [**管理 Web 應用程式**，並選取您想要保護與 Azure AD 的 web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ed83f-202">In Central Administration, navigate to **Manage Web Application** and select the web application that you wish to secure with Azure AD.</span></span> 
2. <span data-ttu-id="ed83f-203">在功能區中，按一下 [**驗證提供者**並選擇您想要使用的區域。</span><span class="sxs-lookup"><span data-stu-id="ed83f-203">In the ribbon, click **Authentication Providers** and choose the zone that you wish to use.</span></span>
3. <span data-ttu-id="ed83f-204">選取 [**信任的身分識別提供者**，然後選取 [身分識別提供者只登錄名為*AzureAD*。</span><span class="sxs-lookup"><span data-stu-id="ed83f-204">Select **Trusted Identity provider** and select the identify provider you just registered named *AzureAD*.</span></span>  
4. <span data-ttu-id="ed83f-205">在 [登入頁面 URL] 設定中，選取 [**自訂登入] 頁面上**，並提供 「 /_trust/ 」 的值。</span><span class="sxs-lookup"><span data-stu-id="ed83f-205">On the sign-in page URL setting, select **Custom sign in page** and provide the value "/_trust/".</span></span> 
5. <span data-ttu-id="ed83f-206">按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ed83f-206">Click **OK**.</span></span>

![設定驗證提供者](media/SAML11/fig10-configauthprovider.png)

> [!IMPORTANT]
> <span data-ttu-id="ed83f-208">請務必遵循所有步驟，包括 「 /_trust/ 」 頁面中設定自訂的登入，所示。</span><span class="sxs-lookup"><span data-stu-id="ed83f-208">It is important to follow all steps, including setting the custom sign in page to "/_trust/" as shown.</span></span> <span data-ttu-id="ed83f-209">除非所有步驟都之後，設定將無法正確運作。</span><span class="sxs-lookup"><span data-stu-id="ed83f-209">The configuration will not work correctly unless all steps are followed.</span></span>

## <a name="step-5-set-the-permissions"></a><span data-ttu-id="ed83f-210">步驟 5： 設定的權限</span><span class="sxs-lookup"><span data-stu-id="ed83f-210">Step 5: Set the permissions</span></span>

<span data-ttu-id="ed83f-211">將登入 Azure AD，並存取 SharePoint 使用者必須授與存取應用程式。</span><span class="sxs-lookup"><span data-stu-id="ed83f-211">The users who will log into Azure AD and access SharePoint must be granted access to the application.</span></span> 

1. <span data-ttu-id="ed83f-212">在 Azure 入口網站中，開啟 [Azure AD 目錄]。</span><span class="sxs-lookup"><span data-stu-id="ed83f-212">In the Azure Portal, open the Azure AD directory.</span></span> <span data-ttu-id="ed83f-213">按一下 [**企業應用程式**，然後按一下 [**所有應用程式**。</span><span class="sxs-lookup"><span data-stu-id="ed83f-213">Click **Enterprise Applications**, then click **All applications**.</span></span> <span data-ttu-id="ed83f-214">按一下 [先前建立的應用程式 （SharePoint SAML 整合）。</span><span class="sxs-lookup"><span data-stu-id="ed83f-214">Click the application that you created previously (SharePoint SAML Integration).</span></span>
2. <span data-ttu-id="ed83f-215">按一下 [**使用者和群組**]。</span><span class="sxs-lookup"><span data-stu-id="ed83f-215">Click **Users and Groups**.</span></span> 
3. <span data-ttu-id="ed83f-216">按一下 [新增使用者或群組 southeast offices 登入 SharePoint 使用 Azure AD 的權限的 [**新增使用者**]。</span><span class="sxs-lookup"><span data-stu-id="ed83f-216">Click **Add user** to add a user or group who will have permissions to log into SharePoint using Azure AD.</span></span>
4. <span data-ttu-id="ed83f-217">選取使用者或群組，然後按一下 [**指派**]。</span><span class="sxs-lookup"><span data-stu-id="ed83f-217">Select the user or group then click **Assign**.</span></span>
 
<span data-ttu-id="ed83f-218">使用者已授與 Azure AD 中的權限，但也必須授與 SharePoint 中的權限。</span><span class="sxs-lookup"><span data-stu-id="ed83f-218">The user has been granted permission in Azure AD, but also must be granted permission in SharePoint.</span></span> <span data-ttu-id="ed83f-219">使用下列步驟來設定存取 web 應用程式的權限。</span><span class="sxs-lookup"><span data-stu-id="ed83f-219">Use the following steps to set the permissions to access the web application.</span></span>

1. <span data-ttu-id="ed83f-220">在管理中心中，按一下 [應用程式管理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ed83f-220">In Central Administration, click **Application Management**.</span></span>
2. <span data-ttu-id="ed83f-221">在 [應用程式管理]\*\*\*\* 頁面上，按一下 [Web 應用程式]\*\*\*\* 區段中的 [管理 Web 應用程式]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ed83f-221">On the **Application Management** page, in the **Web Applications** section, click **Manage web applications**.</span></span>
3. <span data-ttu-id="ed83f-222">按一下適當的 web 應用程式]，然後按一下 [**使用者原則**。</span><span class="sxs-lookup"><span data-stu-id="ed83f-222">Click the appropriate web application, and then click **User Policy**.</span></span>
4. <span data-ttu-id="ed83f-223">在 [Web 應用程式的原則，按一下 [**新增使用者**]。</span><span class="sxs-lookup"><span data-stu-id="ed83f-223">In Policy for Web Application, click **Add Users**.</span></span><br/><span data-ttu-id="ed83f-224">![依其名稱宣告使用者搜尋](media/SAML11/fig11-searchbynameclaim.png)</span><span class="sxs-lookup"><span data-stu-id="ed83f-224">![Searching for a user by their name claim](media/SAML11/fig11-searchbynameclaim.png)</span></span><br/>
5. <span data-ttu-id="ed83f-225">在 [**新增使用者**] 對話方塊中，按一下 [**區域**] 中，在適當的區域，然後按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="ed83f-225">In the **Add Users** dialog box, click the appropriate zone in **Zones**, and then click **Next**.</span></span>
6. <span data-ttu-id="ed83f-226">在 [ **Web 應用程式的原則**] 對話方塊中**選擇使用者**] 區段中，按一下 [**瀏覽**] 圖示。</span><span class="sxs-lookup"><span data-stu-id="ed83f-226">In the **Policy for Web Application** dialog box, in the **Choose Users** section, click the **Browse** icon.</span></span>
7. <span data-ttu-id="ed83f-227">在 [**尋找**] 文字方塊中，輸入使用者的登入名稱在您的目錄中，按一下 [**搜尋**。</span><span class="sxs-lookup"><span data-stu-id="ed83f-227">In the **Find** textbox, type the sign-in name for a user in your directory and click **Search**.</span></span> <br/><span data-ttu-id="ed83f-228">範例： *demouser@blueskyabove.onmicrosoft.com*。</span><span class="sxs-lookup"><span data-stu-id="ed83f-228">Example: *demouser@blueskyabove.onmicrosoft.com*.</span></span>
8. <span data-ttu-id="ed83f-229">標題下的 AzureAD 在清單檢視中，選取 name 屬性然後按一下 [**新增**] 然後按一下 **[確定]** 關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ed83f-229">Under the AzureAD heading in the list view, select the name property and click **Add** then click **OK** to close the dialog.</span></span>
9. <span data-ttu-id="ed83f-230">在 [權限，按一下 [**完全控制**]。</span><span class="sxs-lookup"><span data-stu-id="ed83f-230">In Permissions, click **Full Control**.</span></span><br/><span data-ttu-id="ed83f-231">![將宣告使用者授與完全控制](media/SAML11/fig12-grantfullcontrol.png)</span><span class="sxs-lookup"><span data-stu-id="ed83f-231">![Granting full control to a claims user](media/SAML11/fig12-grantfullcontrol.png)</span></span><br/>
10. <span data-ttu-id="ed83f-232">按一下 [完成]，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="ed83f-232">Click **Finish**, and then click **OK**.</span></span>

## <a name="step-6-add-a-saml-11-token-issuance-policy-in-azure-ad"></a><span data-ttu-id="ed83f-233">步驟 6： 在 Azure AD 中新增 SAML 1.1 token 發行原則</span><span class="sxs-lookup"><span data-stu-id="ed83f-233">Step 6: Add a SAML 1.1 token issuance policy in Azure AD</span></span>

<span data-ttu-id="ed83f-234">在入口網站中建立的 Azure AD 應用程式時，它會預設為使用 SAML 2.0。</span><span class="sxs-lookup"><span data-stu-id="ed83f-234">When the Azure AD application is created in the portal, it defaults to using SAML 2.0.</span></span> <span data-ttu-id="ed83f-235">SharePoint Server 2016 需要 SAML 1.1 token 格式。</span><span class="sxs-lookup"><span data-stu-id="ed83f-235">SharePoint Server 2016 requires the SAML 1.1 token format.</span></span> <span data-ttu-id="ed83f-236">下列指令碼將會移除預設的 SAML 2.0 原則，並將新的原則新增至問題 SAML 1.1 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="ed83f-236">The following script will remove the default SAML 2.0 policy and add a new policy to issue SAML 1.1 tokens.</span></span> 

> <span data-ttu-id="ed83f-237">這段程式碼需要下載隨附的[範例示範與 Azure Active Directory Graph 互動](https://github.com/kaevans/spsaml11/tree/master/scripts)。</span><span class="sxs-lookup"><span data-stu-id="ed83f-237">This code requires downloading the accompanying [samples demonstrating interacting with Azure Active Directory Graph](https://github.com/kaevans/spsaml11/tree/master/scripts).</span></span> <span data-ttu-id="ed83f-238">如果您為 Windows 桌面的 ZIP 檔案從 GitHub 下載指令碼，請務必要解除封鎖`MSGraphTokenLifetimePolicy.psm1`指令碼模組檔案和`Initialize.ps1`指令碼檔案 （以滑鼠右鍵按一下屬性、 選擇 [解除封鎖，按一下 [確定]）。</span><span class="sxs-lookup"><span data-stu-id="ed83f-238">If you download the scripts as a ZIP file from GitHub to a Windows desktop, make sure to unblock the `MSGraphTokenLifetimePolicy.psm1` script module file and the `Initialize.ps1` script file (right-click Properties, choose Unblock, click OK).</span></span> 
<span data-ttu-id="ed83f-239">![解除封鎖下載的檔案](media/SAML11/fig17-unblock.png)</span><span class="sxs-lookup"><span data-stu-id="ed83f-239">![Unblocking downloaded files](media/SAML11/fig17-unblock.png)</span></span>

<span data-ttu-id="ed83f-240">一旦下載的範例指令碼，建立新的 PowerShell 指令碼，使用下列程式碼，以下載的檔案路徑取代預留位置`Initialize.ps1`您本機電腦上。</span><span class="sxs-lookup"><span data-stu-id="ed83f-240">Once the sample script is downloaded, create a new PowerShell script using the following code, replacing the placeholder with the file path of the downloaded `Initialize.ps1` on your local machine.</span></span> <span data-ttu-id="ed83f-241">您在表格 1 中輸入應用程式物件識別碼來取代應用程式物件識別碼指定版面配置區。</span><span class="sxs-lookup"><span data-stu-id="ed83f-241">Replace the application object ID placeholder with the application object ID that you entered in Table 1.</span></span> <span data-ttu-id="ed83f-242">建立之後，執行 PowerShell 指令碼。</span><span class="sxs-lookup"><span data-stu-id="ed83f-242">Once created, execute the PowerShell script.</span></span> 

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
> <span data-ttu-id="ed83f-243">未簽署的 PowerShell 指令碼，並可能會提示您設定執行原則。</span><span class="sxs-lookup"><span data-stu-id="ed83f-243">The PowerShell scripts are not signed and you may be prompted to set the execution policy.</span></span> <span data-ttu-id="ed83f-244">如需有關執行原則的詳細資訊，請參閱 <<c0>關於執行原則。</span><span class="sxs-lookup"><span data-stu-id="ed83f-244">For more information on execution policies, see [About Execution Policies](http://go.microsoft.com/fwlink/?LinkID=135170).</span></span> <span data-ttu-id="ed83f-245">此外，您可能需要開啟提高權限的命令提示字元來成功執行中的範例指令碼的命令。</span><span class="sxs-lookup"><span data-stu-id="ed83f-245">Additionally, you may need to open an elevated command prompt to successfully execute the commands contained in the sample scripts.</span></span>

<span data-ttu-id="ed83f-246">這些範例 PowerShell 命令是範例，說明如何對圖形 API 執行查詢。</span><span class="sxs-lookup"><span data-stu-id="ed83f-246">These sample PowerShell commands are examples of how to execute queries against the Graph API.</span></span> <span data-ttu-id="ed83f-247">如需與 Azure AD 權杖發行原則的詳細資訊，請參閱 <<c0>在原則上的作業的 Graph API 參考資料。</span><span class="sxs-lookup"><span data-stu-id="ed83f-247">For more details on Token Issuance Policies with Azure AD, see the [Graph API reference for operations on policy](https://msdn.microsoft.com/en-us/library/azure/ad/graph/api/policy-operations#create-a-policy).</span></span>

## <a name="step-7-verify-the-new-provider"></a><span data-ttu-id="ed83f-248">步驟 7： 確認新的提供者</span><span class="sxs-lookup"><span data-stu-id="ed83f-248">Step 7: Verify the new provider</span></span>

<span data-ttu-id="ed83f-249">開啟瀏覽器並前往您在先前步驟中設定 web 應用程式的 URL。</span><span class="sxs-lookup"><span data-stu-id="ed83f-249">Open a browser to the URL of the web application that you configured in the previous steps.</span></span> <span data-ttu-id="ed83f-250">您會重新導向至登入 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="ed83f-250">You are redirected to sign into Azure AD.</span></span>

![登入 Azure AD 同盟設定](media/SAML11/fig13-examplesignin.png)

<span data-ttu-id="ed83f-252">您會詢問您是否要保持登入。</span><span class="sxs-lookup"><span data-stu-id="ed83f-252">You are asked if you want to stay signed in.</span></span>

![保持登入？](media/SAML11/fig14-staysignedin.png)

<span data-ttu-id="ed83f-254">最後，您可以存取您的 Azure Active Directory 租用戶中的使用者以登入的網站。</span><span class="sxs-lookup"><span data-stu-id="ed83f-254">Finally, you can access the site logged in as a user from your Azure Active Directory tenant.</span></span>

![使用者登入 SharePoint](media/SAML11/fig15-signedinsharepoint.png)

## <a name="managing-certificates"></a><span data-ttu-id="ed83f-256">管理憑證</span><span class="sxs-lookup"><span data-stu-id="ed83f-256">Managing certificates</span></span>
<span data-ttu-id="ed83f-257">請務必了解已針對上述步驟 4 中的信任的身分識別提供者的簽署憑證到期日期，以及必須更新。</span><span class="sxs-lookup"><span data-stu-id="ed83f-257">It is important to understand that the signing certificate that was configured for the trusted identity provider in step 4 above has an expiration date and must be renewed.</span></span> <span data-ttu-id="ed83f-258">在 [憑證更新，請參閱文章[同盟單一登入 Azure Active Directory 中的管理憑證](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-sso-certs)的資訊。</span><span class="sxs-lookup"><span data-stu-id="ed83f-258">See the article [Manage certificates for federated single sign-on in Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-sso-certs) for information on certificate renewal.</span></span> <span data-ttu-id="ed83f-259">一旦憑證已在 Azure AD 中已更新，下載至本機檔案，並使用下列指令碼來設定信任的身分識別提供者與經過更新的簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="ed83f-259">Once the certificate has been renewed in Azure AD, download to a local file and use the following script to configure the trusted identity provider with the renewed signing certificate.</span></span> 

```
$filepath="<Full path to renewed SAML signing certificate file>"
$cert= New-Object System.Security.Cryptography.X509Certificates.X509Certificate2($filePath)
New-SPTrustedRootAuthority -Name "AzureAD" -Certificate $cert
Get-SPTrustedIdentityTokenIssuer "AzureAD" | Set-SPTrustedIdentityTokenIssuer -ImportTrustCertificate $cert
```
## <a name="configuring-one-trusted-identity-provider-for-multiple-web-applications"></a><span data-ttu-id="ed83f-260">設定多個 web 應用程式的一個信任的身分識別提供者</span><span class="sxs-lookup"><span data-stu-id="ed83f-260">Configuring one trusted identity provider for multiple web applications</span></span>
<span data-ttu-id="ed83f-261">設定適用於單一 web 應用程式，但需要其他設定，如果您想要使用多個 web 應用程式相同的信任的身分識別提供者。</span><span class="sxs-lookup"><span data-stu-id="ed83f-261">The configuration works for a single web application, but needs additional configuration if you intend to use the same trusted identity provider for multiple web applications.</span></span> <span data-ttu-id="ed83f-262">例如，假設 [我們已延伸 web 應用程式使用的 URL`https://portal.contoso.local`但現在卻想要驗證使用者，以`https://sales.contoso.local`也。</span><span class="sxs-lookup"><span data-stu-id="ed83f-262">For example, assume we had extended a web application to use the URL `https://portal.contoso.local` and now want to authenticate the users to `https://sales.contoso.local` as well.</span></span> <span data-ttu-id="ed83f-263">若要這麼做，我們需要更新受限於 WReply 參數，並新增回覆 URL 的 Azure AD 中更新的應用程式註冊的身分識別提供者。</span><span class="sxs-lookup"><span data-stu-id="ed83f-263">To do this, we need to update the identity provider to honor the WReply parameter and update the application registration in Azure AD to add a reply URL.</span></span>

1. <span data-ttu-id="ed83f-264">在 Azure 入口網站中，開啟 [Azure AD 目錄]。</span><span class="sxs-lookup"><span data-stu-id="ed83f-264">In the Azure Portal, open the Azure AD directory.</span></span> <span data-ttu-id="ed83f-265">按一下 [**應用程式註冊**，然後按一下 [**檢視所有應用程式**。</span><span class="sxs-lookup"><span data-stu-id="ed83f-265">Click **App registrations**, then click **View all applications**.</span></span> <span data-ttu-id="ed83f-266">按一下 [先前建立的應用程式 （SharePoint SAML 整合）。</span><span class="sxs-lookup"><span data-stu-id="ed83f-266">Click the application that you created previously (SharePoint SAML Integration).</span></span>
2. <span data-ttu-id="ed83f-267">按一下 [**設定**]。</span><span class="sxs-lookup"><span data-stu-id="ed83f-267">Click **Settings**.</span></span>
3. <span data-ttu-id="ed83f-268">在 [設定] 刀鋒視窗中，按一下 [**回覆 Url**。</span><span class="sxs-lookup"><span data-stu-id="ed83f-268">In the settings blade, click **Reply URLs**.</span></span> 
4. <span data-ttu-id="ed83f-269">新增其他 web 應用程式的 URL`/_trust/default.aspx`附加至的 URL (例如`https://sales.contoso.local/_trust/default.aspx`) 並按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="ed83f-269">Add the URL for the additional web application with `/_trust/default.aspx` appended to the URL (such as `https://sales.contoso.local/_trust/default.aspx`) and click **Save**.</span></span> 
5. <span data-ttu-id="ed83f-270">在 SharePoint 伺服器上，開啟**SharePoint 2016 管理命令介面**，並執行下列命令，使用您先前使用信任的身分識別 token 簽署者的名稱。</span><span class="sxs-lookup"><span data-stu-id="ed83f-270">On the SharePoint server, open the **SharePoint 2016 Management Shell** and execute the following commands, using the name of the trusted identity token issuer that you used previously.</span></span>

```
$t = Get-SPTrustedIdentityTokenIssuer "AzureAD"
$t.UseWReplyParameter=$true
$t.Update()
```
6. <span data-ttu-id="ed83f-271">在管理中心內，移至 web 應用程式，然後啟用現有的受信任的身分識別提供者。</span><span class="sxs-lookup"><span data-stu-id="ed83f-271">In Central Administration, go to the web application and enable the existing trusted identity provider.</span></span> <span data-ttu-id="ed83f-272">請記住，也設定為自訂的登入頁面的 [登入頁面 URL `/_trust/`。</span><span class="sxs-lookup"><span data-stu-id="ed83f-272">Remember to also configure the sign-in page URL as a custom sign in page `/_trust/`.</span></span>
7. <span data-ttu-id="ed83f-273">在管理中心中，按一下 [web 應用程式，選擇 [**使用者原則**。</span><span class="sxs-lookup"><span data-stu-id="ed83f-273">In Central Administration, click the web application and choose **User Policy**.</span></span> <span data-ttu-id="ed83f-274">如先前所示範這篇文章，請新增具有適當的權限的使用者。</span><span class="sxs-lookup"><span data-stu-id="ed83f-274">Add a user with the appropriate permissions as demonstrated previously in this article.</span></span>

## <a name="fixing-people-picker"></a><span data-ttu-id="ed83f-275">修正人員選擇</span><span class="sxs-lookup"><span data-stu-id="ed83f-275">Fixing People Picker</span></span>
<span data-ttu-id="ed83f-276">使用者現在可以登入 SharePoint 2016 使用從 Azure AD 的身分識別，但仍有使用者經驗的機會。</span><span class="sxs-lookup"><span data-stu-id="ed83f-276">Users can now log into SharePoint 2016 using identities from Azure AD, but there are still opportunities for improvement to the user experience.</span></span> <span data-ttu-id="ed83f-277">在人員選擇] 中，搜尋的使用者呈現比方說，多個搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="ed83f-277">For instance, searching for a user presents multiple search results in the people picker.</span></span> <span data-ttu-id="ed83f-278">沒有針對每個所建立的宣告對應 3 的宣告類型的搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="ed83f-278">There is a search result for each of the 3 claim types that were created in the claim mapping.</span></span> <span data-ttu-id="ed83f-279">若要選擇使用人員選擇] 的使用者，您必須完全輸入其使用者名稱，然後選擇 [ **name**宣告結果。</span><span class="sxs-lookup"><span data-stu-id="ed83f-279">To choose a user using the people picker, you must type their user name exactly and choose the **name** claim result.</span></span>

![宣告的搜尋結果](media/SAML11/fig16-claimssearchresults.png)

<span data-ttu-id="ed83f-281">沒有驗證值搜尋，可能會導致拼錯或不小心選擇錯誤的宣告類型，例如**姓氏**指派的使用者 」 宣告。</span><span class="sxs-lookup"><span data-stu-id="ed83f-281">There is no validation on the values you search for, which can lead to misspellings or users accidentally choosing the wrong claim type to assign such as the **SurName** claim.</span></span> <span data-ttu-id="ed83f-282">這可防止使用者成功存取資源。</span><span class="sxs-lookup"><span data-stu-id="ed83f-282">This can prevent users from successfully accessing resources.</span></span>

<span data-ttu-id="ed83f-283">若要協助進行這種情況下，沒有開放原始碼解決方案呼叫[AzureCP](https://yvand.github.io/AzureCP/)適用於 SharePoint 2016 提供的自訂宣告提供者。</span><span class="sxs-lookup"><span data-stu-id="ed83f-283">To assist with this scenario, there is an open-source solution called [AzureCP](https://yvand.github.io/AzureCP/) that provides a custom claims provider for SharePoint 2016.</span></span> <span data-ttu-id="ed83f-284">它會使用 Azure AD Graph 若要解決功能的使用者輸入，並進行驗證。</span><span class="sxs-lookup"><span data-stu-id="ed83f-284">It will use the Azure AD Graph to resolve what users enter and perform validation.</span></span> <span data-ttu-id="ed83f-285">深入瞭解[AzureCP](https://yvand.github.io/AzureCP/)。</span><span class="sxs-lookup"><span data-stu-id="ed83f-285">Learn more at [AzureCP](https://yvand.github.io/AzureCP/).</span></span> 

## <a name="additional-resources"></a><span data-ttu-id="ed83f-286">其他資源</span><span class="sxs-lookup"><span data-stu-id="ed83f-286">Additional resources</span></span>

[<span data-ttu-id="ed83f-287">了解 WS-同盟</span><span class="sxs-lookup"><span data-stu-id="ed83f-287">Understanding WS-Federation</span></span>](https://go.microsoft.com/fwlink/p/?linkid=188052)
  
[<span data-ttu-id="ed83f-288">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="ed83f-288">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
## <a name="join-the-discussion"></a><span data-ttu-id="ed83f-289">參與討論</span><span class="sxs-lookup"><span data-stu-id="ed83f-289">Join the discussion</span></span>

|<span data-ttu-id="ed83f-290">**連絡我們**</span><span class="sxs-lookup"><span data-stu-id="ed83f-290">**Contact us**</span></span>|<span data-ttu-id="ed83f-291">**描述**</span><span class="sxs-lookup"><span data-stu-id="ed83f-291">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="ed83f-292">**您需要什麼樣的雲端採用內容？**</span><span class="sxs-lookup"><span data-stu-id="ed83f-292">**What cloud adoption content do you need?**</span></span> <br/> |<span data-ttu-id="ed83f-p136">我們正在建立涵蓋多個 Microsoft 雲端平台及服務的雲端採用內容。請傳送電子郵件至 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20)，讓我們知道您對雲端採用內容的看法或對特定內容的要求。</span><span class="sxs-lookup"><span data-stu-id="ed83f-p136">We are creating content for cloud adoption that spans multiple Microsoft cloud platforms and services. Let us know what you think about our cloud adoption content, or ask for specific content by sending email to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).  </span></span><br/> |
|<span data-ttu-id="ed83f-295">**加入雲端採用討論**</span><span class="sxs-lookup"><span data-stu-id="ed83f-295">**Join the cloud adoption discussion**</span></span> <br/> |<span data-ttu-id="ed83f-p137">如果您熱愛雲端解決方案，請考慮加入雲端採用諮詢委員會 (Cloud Adoption Advisory Board，CAAB)，與更大且活躍的 Microsoft 內容開發人員、產業專業人員及全球的客戶接觸。若要加入，請新增為 Microsoft 技術社群 [CAAB (雲端採用諮詢委員會) 空間](https://aka.ms/caab)的成員，並傳送電子郵件給我們，地址為：[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!)。所有人都可以在 [CAAB 部落格](https://blogs.technet.com/b/solutions_advisory_board/)上讀取社群相關內容。不過，CAAB 成員可獲得新雲端採用資源和解決方案說明的私人網路研討會邀請。</span><span class="sxs-lookup"><span data-stu-id="ed83f-p137">If you are passionate about cloud-based solutions, consider joining the Cloud Adoption Advisory Board (CAAB) to connect with a larger, vibrant community of Microsoft content developers, industry professionals, and customers from around the globe. To join, add yourself as a member of the [CAAB (Cloud Adoption Advisory Board) space](https://aka.ms/caab) of the Microsoft Tech Community and send us a quick email at [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Anyone can read community-related content on the [CAAB blog](https://blogs.technet.com/b/solutions_advisory_board/). However, CAAB members get invitations to private webinars that describe new cloud adoption resources and solutions.  </span></span><br/> |
|<span data-ttu-id="ed83f-300">**取得您在這裡看到的美工圖案**</span><span class="sxs-lookup"><span data-stu-id="ed83f-300">**Get the art you see here**</span></span> <br/> |<span data-ttu-id="ed83f-p138">如果您想要此文章中所看到之美工圖案的可編輯複本，我們很樂於將它傳送給您。請以電子郵件將您的要求 (包括美工圖案的 URL 和標題) 傳送至 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20)。</span><span class="sxs-lookup"><span data-stu-id="ed83f-p138">If you want an editable copy of the art you see in this article, we'll be glad to send it to you. Email your request, including the URL and title of the art, to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  </span></span><br/> |
   

