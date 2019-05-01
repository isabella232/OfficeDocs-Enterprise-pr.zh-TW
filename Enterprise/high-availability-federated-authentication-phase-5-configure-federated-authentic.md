---
title: 高可用性同盟的驗證階段 5 設定的 Office 365 的同盟驗證
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
ms.assetid: 0f1dbf52-5bff-44cc-a264-1b48641af98f
description: 摘要： 在 Microsoft Azure 中設定 Office 365 高可用性同盟驗證的 Azure AD Connect。
ms.openlocfilehash: e5a4381b6795a1159c1398f4155b059998a30818
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487925"
---
# <a name="high-availability-federated-authentication-phase-5-configure-federated-authentication-for-office-365"></a><span data-ttu-id="6e0f0-103">高可用性同盟驗證階段 5：設定 Office 365 的同盟驗證</span><span class="sxs-lookup"><span data-stu-id="6e0f0-103">High availability federated authentication Phase 5: Configure federated authentication for Office 365</span></span>

 <span data-ttu-id="6e0f0-104">**摘要：** 在 Microsoft Azure 中設定 Office 365 高可用性同盟驗證的 Azure AD Connect。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-104">**Summary:** Configure Azure AD Connect for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
 
<span data-ttu-id="6e0f0-105">在此部署高可用性同盟的驗證 Office 365 的 Azure 基礎結構服務中的最後一個階段中，您取得並安裝公用憑證授權單位所發出的憑證，確認您的組態，然後安裝和執行 Azure AD連線的目錄同步處理伺服器上。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-105">In this final phase of deploying high availability federated authentication for Office 365 in Azure infrastructure services, you get and install a certificate issued by a public certification authority, verify your configuration, and then install and run Azure AD Connect on the directory synchronization server.</span></span> <span data-ttu-id="6e0f0-106">Azure AD Connect 設定您的 Office 365 訂閱和您的 Active Directory Federation Services (AD FS) 和同盟驗證的 web 應用程式 proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-106">Azure AD Connect configures your Office 365 subscription and your Active Directory Federation Services (AD FS) and web application proxy servers for federated authentication.</span></span>
  
<span data-ttu-id="6e0f0-107">所有階段，請參閱[在 Azure 中的 Office 365 部署高可用性同盟的驗證](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-107">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="get-a-public-certificate-and-copy-it-to-the-directory-synchronization-server"></a><span data-ttu-id="6e0f0-108">取得公用憑證，並將它複製到目錄同步處理伺服器</span><span class="sxs-lookup"><span data-stu-id="6e0f0-108">Get a public certificate and copy it to the directory synchronization server</span></span>

<span data-ttu-id="6e0f0-109">從具有下列內容的公用憑證授權單位取得數位憑證：</span><span class="sxs-lookup"><span data-stu-id="6e0f0-109">Get a digital certificate from a public certification authority with the following properties:</span></span>
  
- <span data-ttu-id="6e0f0-110">適用於建立 SSL 連線的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-110">An X.509 certificate suitable for creating SSL connections.</span></span>
    
- <span data-ttu-id="6e0f0-111">主體替代名稱 (SAN) 擴充屬性設為同盟服務 FQDN (範例： fs.contoso.com)。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-111">The Subject Alternative Name (SAN) extended property is set to your federation service FQDN (example: fs.contoso.com).</span></span>
    
- <span data-ttu-id="6e0f0-112">憑證必須有私密金鑰，並以 PFX 格式儲存。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-112">The certificate must have the private key and be stored in PFX format.</span></span>
    
<span data-ttu-id="6e0f0-113">此外，您的組織電腦和裝置必須信任公用憑證授權單位發出的數位憑證。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-113">Additionally, your organization computers and devices must trust the public certification authority that is issuing the digital certificate.</span></span> <span data-ttu-id="6e0f0-114">此信任會建立具有安裝在電腦和裝置上受信任的根憑證授權單位存放區中的公用憑證授權單位根憑證。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-114">This trust is established by having a root certificate from the public certification authority installed in the trusted root certification authorities store on your computers and devices.</span></span> <span data-ttu-id="6e0f0-115">通常在執行 Microsoft Windows 的電腦有一組的這種常用的憑證授權單位所安裝的憑證。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-115">Computers running Microsoft Windows typically have a set of these types of certificates installed from commonly-used certification authorities.</span></span> <span data-ttu-id="6e0f0-116">如果尚未安裝來自您的公用憑證授權單位的根憑證，您必須部署此電腦和組織的裝置。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-116">If the root certificate from your public certification authority is not already installed, you must deploy this to the computers and devices of your organization.</span></span>
  
<span data-ttu-id="6e0f0-117">如需同盟驗證的憑證需求的詳細資訊，請參閱[同盟安裝和組態必要條件](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-prerequisites#prerequisites-for-federation-installation-and-configuration)。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-117">For more information about certificate requirements for federated authentication, see [Prerequisites for federation installation and configuration](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-prerequisites#prerequisites-for-federation-installation-and-configuration).</span></span>
  
<span data-ttu-id="6e0f0-118">當您收到憑證時，請將它複製到目錄同步處理伺服器的 c： 磁碟機上的資料夾。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-118">When you receive the certificate, copy it to a folder on the C: drive of the directory synchronization server.</span></span> <span data-ttu-id="6e0f0-119">例如，SSL.pfx 的檔案名稱，並將它儲存在 c:\\目錄同步處理伺服器上的 [憑證] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-119">For example, name the file SSL.pfx and store it in the C:\\Certs folder on the directory synchronization server.</span></span>
  
## <a name="verify-your-configuration"></a><span data-ttu-id="6e0f0-120">確認您的設定</span><span class="sxs-lookup"><span data-stu-id="6e0f0-120">Verify your configuration</span></span>

<span data-ttu-id="6e0f0-121">您現在應該可以設定 Azure AD Connect 與 Office 365 同盟的驗證。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-121">You should now be ready to configure Azure AD Connect and federated authentication for Office 365.</span></span> <span data-ttu-id="6e0f0-122">若要確保您，以下是一份檢查清單：</span><span class="sxs-lookup"><span data-stu-id="6e0f0-122">To ensure that you are, here is a checklist:</span></span>
  
- <span data-ttu-id="6e0f0-123">貴組織的公用網域會新增至您的 Office 365 訂閱。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-123">Your organization's public domain is added to your Office 365 subscription.</span></span>
    
- <span data-ttu-id="6e0f0-124">貴組織的 Office 365 使用者帳戶設定為貴組織的公用網域名稱，且可以成功登入。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-124">Your organization's Office 365 user accounts are configured to your organization's public domain name and can successfully sign in.</span></span>
    
- <span data-ttu-id="6e0f0-125">您已決定同盟服務 FQDN 基礎公用網域名稱。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-125">You have determined a federation service FQDN based your public domain name.</span></span>
    
- <span data-ttu-id="6e0f0-126">公用 DNS A 記錄您同盟服務 FQDN 指向公用 IP 位址的網際網路對向 Azure 負載平衡器的 web 應用程式 proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-126">A public DNS A record for your federation service FQDN points to the public IP address of the Internet-facing Azure load balancer for the web application proxy servers.</span></span>
    
- <span data-ttu-id="6e0f0-127">私人 DNS A 記錄您同盟服務 FQDN 指向私人 IP 位址的 AD FS 伺服器內部 Azure 負載平衡器。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-127">A private DNS A record for your federation service FQDN points to the private IP address of the internal Azure load balancer for the AD FS servers.</span></span>
    
- <span data-ttu-id="6e0f0-128">公用憑證授權單位 isssued 數位憑證適用於 SSL 連線與 SAN (英文） 設定為同盟服務 FQDN 是 PFX 檔案儲存在您的目錄同步處理伺服器上。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-128">A public certification authority-isssued digital certificate suitable for SSL connections with the SAN set to your federation service FQDN is a PFX file stored on your directory synchronization server.</span></span>
    
- <span data-ttu-id="6e0f0-129">在受信任的根憑證授權單位安裝公用憑證授權單位根憑證儲存在電腦和裝置上。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-129">The root certificate for the public certification authority is installed in the Trusted Root Certification Authorities store on your computers and devices.</span></span>
    
<span data-ttu-id="6e0f0-130">以下是在 Contoso 組織的範例：</span><span class="sxs-lookup"><span data-stu-id="6e0f0-130">Here is an example for the Contoso organization:</span></span>
  
<span data-ttu-id="6e0f0-131">**高可用性的範例設定同盟驗證基礎結構，在 Azure 中**</span><span class="sxs-lookup"><span data-stu-id="6e0f0-131">**An example configuration for a high availability federated authentication infrastructure in Azure**</span></span>

![高可用性 Office 365 的範例設定同盟驗證基礎結構，在 Azure 中](media/ac1a6a0d-0156-4407-9336-6e4cd6db8633.png)
  
## <a name="run-azure-ad-connect-to-configure-federated-authentication"></a><span data-ttu-id="6e0f0-133">執行 Azure AD Connect，若要設定的同盟的驗證</span><span class="sxs-lookup"><span data-stu-id="6e0f0-133">Run Azure AD Connect to configure federated authentication</span></span>

<span data-ttu-id="6e0f0-134">Azure AD Connect 工具設定 AD FS 伺服器、 web 應用程式 proxy 伺服器，以及 Office 365 同盟驗證，使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="6e0f0-134">The Azure AD Connect tool configures the AD FS servers, the web application proxy servers, and Office 365 for federated authentication with these steps:</span></span>
  
1. <span data-ttu-id="6e0f0-135">使用具備本機系統管理員權限的網域帳戶建立您的目錄同步處理伺服器的遠端桌面連線。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-135">Create a remote desktop connection to your directory synchronization server with a domain account that has local administrator privileges.</span></span>
    
2. <span data-ttu-id="6e0f0-136">從目錄同步處理伺服器的桌面，開啟 Internet Explorer 並移至[https://aka.ms/aadconnect](https://aka.ms/aadconnect)。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-136">From the desktop of the directory synchronization server, open Internet Explorer and go to [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span></span>
    
3. <span data-ttu-id="6e0f0-137">在**Microsoft Azure Active Directory Connect** ] 頁面上，按一下 [**下載**]，然後按一下 [**執行**。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-137">On the **Microsoft Azure Active Directory Connect** page, click **Download**, and then click **Run**.</span></span>
    
4. <span data-ttu-id="6e0f0-138">在 [**歡迎使用 Azure AD Connect** ] 頁面上，按一下 [**我同意**]，然後按一下**繼續。**</span><span class="sxs-lookup"><span data-stu-id="6e0f0-138">On the **Welcome to Azure AD Connect** page, click **I agree**, and then click **Continue.**</span></span>
    
5. <span data-ttu-id="6e0f0-139">在 [**快速設定**] 頁面上，按一下 [**自訂**]。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-139">On the **Express Settings** page, click **Customize**.</span></span>
    
6. <span data-ttu-id="6e0f0-140">在 [**安裝所需的元件**] 頁面上，按一下 [**安裝**]。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-140">On the **Install required components** page, click **Install**.</span></span>
    
7. <span data-ttu-id="6e0f0-141">在 [使用者登入]\*\*\*\* 頁面上，按一下 [和 AD FS 的同盟]\*\*\*\*，然後按 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-141">On the **User sign-in** page, click **Federation with AD FS**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="6e0f0-142">在 [**連線到 Azure AD** ] 頁面上輸入的名稱與您的 Office 365 訂閱的全域系統管理員帳戶的密碼，然後按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-142">On the **Connect to Azure AD** page, type the name and password of a global administrator account for your Office 365 subscription, and then click **Next**.</span></span>
    
9. <span data-ttu-id="6e0f0-143">在 [**連線您的目錄**] 頁面上，確定 [**樹系**中已選取 [您的內部部署 Active Directory 網域服務 (AD DS) 樹系、 輸入的名稱和網域系統管理員帳戶的密碼、 按一下 [**新增目錄**，然後選取按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-143">On the **Connect your directories** page, ensure that your on-premises Active Directory Domain Services (AD DS) forest is selected in **Forest**, type the name and password of a domain administrator account, click **Add Directory**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="6e0f0-144">在**Azure AD 登入設定**] 頁面上，按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-144">On the **Azure AD sign-in configuration** page, click **Next**.</span></span>
    
11. <span data-ttu-id="6e0f0-145">在 [**網域及 OU 篩選**] 頁面上，按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-145">On the **Domain and OU filtering** page, click **Next**.</span></span>
    
12. <span data-ttu-id="6e0f0-146">在**用來唯一識別您的使用者**] 頁面上，按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-146">On the **Uniquely identifying your users** page, click **Next**.</span></span>
    
13. <span data-ttu-id="6e0f0-147">在 [**篩選使用者和裝置**] 頁面上，按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-147">On the **Filter users and devices** page, click **Next**.</span></span>
    
14. <span data-ttu-id="6e0f0-148">在 [**選擇性功能**] 頁面上，按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-148">On the **Optional features** page, click **Next**.</span></span>
    
15. <span data-ttu-id="6e0f0-149">在 [ **AD FS 伺服器陣列**] 頁面上，按一下 [**設定新的 AD FS 伺服器陣列**。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-149">On the **AD FS farm** page, click **Configure a new AD FS farm**.</span></span>
    
16. <span data-ttu-id="6e0f0-150">按一下 [**瀏覽]** 並指定的公用憑證授權單位的 SSL 憑證的名稱與位置。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-150">Click **Browse** and specify the location and name of the SSL certificate from the public certification authority.</span></span>
    
17. <span data-ttu-id="6e0f0-151">出現提示時，輸入憑證的密碼，然後按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-151">When prompted, type the certificate password, and then click **OK**.</span></span>
    
18. <span data-ttu-id="6e0f0-152">確認**同盟服務名稱**與**主體名稱**設定為同盟服務 FQDN，然後按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-152">Verify that the **Subject Name** and **Federation Service Name** are set to your federation service FQDN, and then click **Next**.</span></span>
    
19. <span data-ttu-id="6e0f0-153">在**AD FS 伺服器**] 頁面上，輸入您第一部 AD FS 伺服器的名稱 （資料表 M-項目 4-虛擬機器名稱欄），然後按一下 [**新增]**。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-153">On the **AD FS servers** page, type your first AD FS server's name (Table M - Item 4 - Virtual machine name column), and then click **Add**.</span></span>
    
20. <span data-ttu-id="6e0f0-154">輸入第二個 AD FS 伺服器的名稱 （資料表 M-項目 5-虛擬機器名稱欄），按一下 [**新增**]，然後按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-154">Type your second AD FS server's name (Table M - Item 5 - Virtual machine name column), click **Add**, and then click **Next**.</span></span>
    
21. <span data-ttu-id="6e0f0-155">在**Web 應用程式 Proxy 伺服器**] 頁面中，輸入第一個 web 應用程式 proxy 伺服器的名稱 （資料表 M-項目 6-虛擬機器名稱欄），然後按一下 [**新增]**。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-155">On the **Web Application Proxy servers** page, type your first web application proxy server's name (Table M - Item 6 - Virtual machine name column), and then click **Add**.</span></span>
    
22. <span data-ttu-id="6e0f0-156">輸入第二個 web 應用程式 proxy 伺服器的名稱 （資料表 M-項目 7-虛擬機器名稱欄），按一下 [**新增**]，然後按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-156">Type your second web application proxy server's name (Table M - Item 7 - Virtual machine name column), click **Add**, and then click **Next**.</span></span>
    
23. <span data-ttu-id="6e0f0-157">在**網域系統管理員認證**] 頁面上，輸入使用者名稱和密碼的網域管理員帳戶，然後再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-157">On the **Domain Administrator credentials** page, type the user name and password of a domain administrator account, and then click **Next**.</span></span>
    
24. <span data-ttu-id="6e0f0-158">在**AD FS 服務帳戶**] 頁面上，輸入使用者名稱和企業系統管理員帳戶密碼，然後再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-158">On the **AD FS service account** page, type the user name and password of an enterprise administrator account, and then click **Next**.</span></span>
    
25. <span data-ttu-id="6e0f0-159">在**Azure AD 網域**] 頁面的 [**網域**] 中，選取您組織的 DNS 網域名稱，，然後按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-159">On the **Azure AD Domain** page, in **Domain**, select your organization's DNS domain name, and then click **Next**.</span></span>
    
26. <span data-ttu-id="6e0f0-160">在 [準備設定]\*\*\*\* 頁面上，按一下 [安裝]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-160">On the **Ready to configure** page, click **Install**.</span></span>
    
27. <span data-ttu-id="6e0f0-161">在 [安裝完成]\*\*\*\* 頁面上，按一下 [驗證]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-161">On the **Installation complete** page, click **Verify**.</span></span> <span data-ttu-id="6e0f0-162">您應該在內部網路和網際網路看到兩個訊息，表示已順利驗證組態。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-162">You should see two messages indicating that both the intranet and Internet configuration was successfully verified.</span></span>
    
  - <span data-ttu-id="6e0f0-163">內部網路郵件應列出您的 Azure 內部負載平衡器的 AD FS 伺服器的私人 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-163">The intranet message should list the private IP address of your Azure internal load balancer for your AD FS servers.</span></span>
    
  - <span data-ttu-id="6e0f0-164">網際網路郵件應列出您 web 應用程式 proxy 伺服器您 Azure 網際網路對應負載平衡器的公用 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-164">The Internet message should list the public IP address of your Azure Internet-facing load balancer for your web application proxy servers.</span></span>
    
28. <span data-ttu-id="6e0f0-165">在 [安裝完成]\*\*\*\* 頁面上，按一下 [結束]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-165">On the **Installation complete** page, click **Exit**.</span></span>
    
<span data-ttu-id="6e0f0-166">以下是具有預留位置名稱伺服器的最終組態。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-166">Here is the final configuration, with placeholder names for the servers.</span></span>
  
<span data-ttu-id="6e0f0-167">**階段 5： 的最終組態的高可用性同盟驗證基礎結構，在 Azure 中**</span><span class="sxs-lookup"><span data-stu-id="6e0f0-167">**Phase 5: The final configuration of a high availability federated authentication infrastructure in Azure**</span></span>

![Azure 中高可用性 Office 365 同盟驗證基礎結構的最後設定](media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
<span data-ttu-id="6e0f0-169">完成您的高可用性同盟的驗證基礎結構的 Azure 中 Office 365。</span><span class="sxs-lookup"><span data-stu-id="6e0f0-169">Your high availability federated authentication infrastructure for Office 365 in Azure is complete.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6e0f0-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e0f0-170">See Also</span></span>

[<span data-ttu-id="6e0f0-171">Azure 中的 Office 365 高可用性同盟驗證</span><span class="sxs-lookup"><span data-stu-id="6e0f0-171">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="6e0f0-172">Office 365 開發人員/測試環境的同盟身分識別</span><span class="sxs-lookup"><span data-stu-id="6e0f0-172">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="6e0f0-173">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="6e0f0-173">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="6e0f0-174">Office 365 的同盟身分識別</span><span class="sxs-lookup"><span data-stu-id="6e0f0-174">Federated identity for Office 365</span></span>](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


