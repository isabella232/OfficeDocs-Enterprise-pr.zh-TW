---
title: 高可用性同盟的驗證 Office 365 的階段 5 設定同盟驗證
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
description: 摘要： 設定您的 Office 365 的高可用性同盟驗證的 Azure AD Connect in Microsoft Azure。
ms.openlocfilehash: 797429e508a0a0c2b91d837e5475e840ca26b3d8
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915358"
---
# <a name="high-availability-federated-authentication-phase-5-configure-federated-authentication-for-office-365"></a><span data-ttu-id="6ca99-103">高可用性同盟驗證階段 5：設定 Office 365 的同盟驗證</span><span class="sxs-lookup"><span data-stu-id="6ca99-103">High availability federated authentication Phase 5: Configure federated authentication for Office 365</span></span>

 <span data-ttu-id="6ca99-104">**摘要：** 設定您的 Office 365 的高可用性同盟驗證的 Azure AD Connect in Microsoft Azure。</span><span class="sxs-lookup"><span data-stu-id="6ca99-104">**Summary:** Configure Azure AD Connect for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
 
<span data-ttu-id="6ca99-p101">此部署高可用性同盟的驗證 Office 365 Azure 基礎結構服務中的最後階段中，在您取得並安裝的公用憑證授權單位所發出的憑證、 驗證您的設定，然後安裝並執行 Azure AD連線的目錄同步處理伺服器上。Azure AD 連線設定您的 Office 365 訂閱和您的 Active Directory Federation Services (AD FS) 和同盟驗證的 web 應用程式 proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="6ca99-p101">In this final phase of deploying high availability federated authentication for Office 365 in Azure infrastructure services, you get and install a certificate issued by a public certification authority, verify your configuration, and then install and run Azure AD Connect on the directory synchronization server. Azure AD Connect configures your Office 365 subscription and your Active Directory Federation Services (AD FS) and web application proxy servers for federated authentication.</span></span>
  
<span data-ttu-id="6ca99-107">請參閱[在 Azure 中的 Office 365 的部署高可用性同盟的驗證](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)的所有階段。</span><span class="sxs-lookup"><span data-stu-id="6ca99-107">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="get-a-public-certificate-and-copy-it-to-the-directory-synchronization-server"></a><span data-ttu-id="6ca99-108">取得公用憑證並將它複製到目錄同步處理伺服器</span><span class="sxs-lookup"><span data-stu-id="6ca99-108">Get a public certificate and copy it to the directory synchronization server</span></span>

<span data-ttu-id="6ca99-109">從具有下列內容的公用憑證授權單位取得數位憑證：</span><span class="sxs-lookup"><span data-stu-id="6ca99-109">Get a digital certificate from a public certification authority with the following properties:</span></span>
  
- <span data-ttu-id="6ca99-110">適用於建立 SSL 連線的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="6ca99-110">An X.509 certificate suitable for creating SSL connections.</span></span>
    
- <span data-ttu-id="6ca99-111">主體替代名稱 (SAN) 擴充屬性設定為同盟服務 FQDN (範例： fs.contoso.com)。</span><span class="sxs-lookup"><span data-stu-id="6ca99-111">The Subject Alternative Name (SAN) extended property is set to your federation service FQDN (example: fs.contoso.com).</span></span>
    
- <span data-ttu-id="6ca99-112">憑證必須具備私密金鑰和 PFX 格式儲存。</span><span class="sxs-lookup"><span data-stu-id="6ca99-112">The certificate must have the private key and be stored in PFX format.</span></span>
    
<span data-ttu-id="6ca99-p102">此外，您的組織電腦和裝置必須信任會發出數位憑證的公用憑證授權單位。從安裝在您的電腦和裝置上的受信任的根憑證授權單位存放區中的公用憑證授權單位的根憑證藉由建立此信任。通常執行 Microsoft Windows 的電腦必須安裝從常用的憑證授權單位的憑證這些類型的一組。如果尚未安裝從您的公用憑證授權單位的根憑證，則必須將此部署至電腦與您組織的裝置。</span><span class="sxs-lookup"><span data-stu-id="6ca99-p102">Additionally, your organization computers and devices must trust the public certification authority that is issuing the digital certificate. This trust is established by having a root certificate from the public certification authority installed in the trusted root certification authorities store on your computers and devices. Computers running Microsoft Windows typically have a set of these types of certificates installed from commonly-used certification authorities. If the root certificate from your public certification authority is not already installed, you must deploy this to the computers and devices of your organization.</span></span>
  
<span data-ttu-id="6ca99-117">如需同盟驗證的憑證需求的詳細資訊，請參閱[federation 安裝與設定的必要條件](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-prerequisites#prerequisites-for-federation-installation-and-configuration)。</span><span class="sxs-lookup"><span data-stu-id="6ca99-117">For more information about certificate requirements for federated authentication, see [Prerequisites for federation installation and configuration](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-prerequisites#prerequisites-for-federation-installation-and-configuration).</span></span>
  
<span data-ttu-id="6ca99-p103">當您收到憑證時，請將它複製到 c： 磁碟機的目錄同步處理伺服器上的資料夾。例如 SSL.pfx 的檔案名稱和儲存在 c:\\目錄同步處理伺服器上的 [憑證] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="6ca99-p103">When you receive the certificate, copy it to a folder on the C: drive of the directory synchronization server. For example, name the file SSL.pfx and store it in the C:\\Certs folder on the directory synchronization server.</span></span>
  
## <a name="verify-your-configuration"></a><span data-ttu-id="6ca99-120">確認您的設定</span><span class="sxs-lookup"><span data-stu-id="6ca99-120">Verify your configuration</span></span>

<span data-ttu-id="6ca99-p104">您現在應該準備好設定 Azure AD 連線] 及 [Office 365 同盟的驗證。若要確保您，以下是檢查清單：</span><span class="sxs-lookup"><span data-stu-id="6ca99-p104">You should now be ready to configure Azure AD Connect and federated authentication for Office 365. To ensure that you are, here is a checklist:</span></span>
  
- <span data-ttu-id="6ca99-123">您的組織部署公用網域新增至您的 Office 365 訂閱。</span><span class="sxs-lookup"><span data-stu-id="6ca99-123">Your organization's public domain is added to your Office 365 subscription.</span></span>
    
- <span data-ttu-id="6ca99-124">貴組織的 Office 365 使用者帳戶設定為您的組織部署公用網域名稱，且可以成功登入。</span><span class="sxs-lookup"><span data-stu-id="6ca99-124">Your organization's Office 365 user accounts are configured to your organization's public domain name and can successfully sign in.</span></span>
    
- <span data-ttu-id="6ca99-125">您已決定同盟服務 FQDN 型公用網域名稱。</span><span class="sxs-lookup"><span data-stu-id="6ca99-125">You have determined a federation service FQDN based your public domain name.</span></span>
    
- <span data-ttu-id="6ca99-126">在同盟服務 FQDN 指向公用 IP 位址的網際網路 Azure 的公用 DNS A 記錄負載平衡器的 web 應用程式 proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="6ca99-126">A public DNS A record for your federation service FQDN points to the public IP address of the Internet-facing Azure load balancer for the web application proxy servers.</span></span>
    
- <span data-ttu-id="6ca99-127">您同盟服務 FQDN 點的私人 IP 位址的內部 Azure 的負載平衡器的 AD FS 伺服器私人的 DNS A 記錄。</span><span class="sxs-lookup"><span data-stu-id="6ca99-127">A private DNS A record for your federation service FQDN points to the private IP address of the internal Azure load balancer for the AD FS servers.</span></span>
    
- <span data-ttu-id="6ca99-128">公用憑證授權單位 isssued 數位憑證合適與 SAN 設為同盟服務的 SSL 連線 FQDN 是 PFX 檔案儲存在您的目錄同步處理伺服器上。</span><span class="sxs-lookup"><span data-stu-id="6ca99-128">A public certification authority-isssued digital certificate suitable for SSL connections with the SAN set to your federation service FQDN is a PFX file stored on your directory synchronization server.</span></span>
    
- <span data-ttu-id="6ca99-129">公用憑證授權單位的根憑證安裝在信任的根憑證授權儲存在您的電腦和裝置。</span><span class="sxs-lookup"><span data-stu-id="6ca99-129">The root certificate for the public certification authority is installed in the Trusted Root Certification Authorities store on your computers and devices.</span></span>
    
<span data-ttu-id="6ca99-130">以下是範例 Contoso 組織：</span><span class="sxs-lookup"><span data-stu-id="6ca99-130">Here is an example for the Contoso organization:</span></span>
  
<span data-ttu-id="6ca99-131">**高可用性的範例設定同盟 Azure 中的驗證基礎結構**</span><span class="sxs-lookup"><span data-stu-id="6ca99-131">**An example configuration for a high availability federated authentication infrastructure in Azure**</span></span>

![Azure 中高可用性 Office 365 同盟驗證基礎結構的範例設定](media/ac1a6a0d-0156-4407-9336-6e4cd6db8633.png)
  
## <a name="run-azure-ad-connect-to-configure-federated-authentication"></a><span data-ttu-id="6ca99-133">執行設定同盟的驗證的 Azure AD 連線</span><span class="sxs-lookup"><span data-stu-id="6ca99-133">Run Azure AD Connect to configure federated authentication</span></span>

<span data-ttu-id="6ca99-134">「 Azure AD 連線工具設定 AD FS 伺服器、 web 應用程式 proxy 伺服器及 Office 365 同盟驗證進行這些步驟：</span><span class="sxs-lookup"><span data-stu-id="6ca99-134">The Azure AD Connect tool configures the AD FS servers, the web application proxy servers, and Office 365 for federated authentication with these steps:</span></span>
  
1. <span data-ttu-id="6ca99-135">使用具有本機系統管理員權限的網域帳戶建立您的目錄同步處理伺服器的遠端桌面連線。</span><span class="sxs-lookup"><span data-stu-id="6ca99-135">Create a remote desktop connection to your directory synchronization server with a domain account that has local administrator privileges.</span></span>
    
2. <span data-ttu-id="6ca99-136">從目錄同步處理伺服器的桌面，開啟 Internet Explorer，並移至[https://aka.ms/aadconnect](https://aka.ms/aadconnect)。</span><span class="sxs-lookup"><span data-stu-id="6ca99-136">From the desktop of the directory synchronization server, open Internet Explorer and go to [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span></span>
    
3. <span data-ttu-id="6ca99-137">在 [ **Microsoft Azure Active Directory 連線**] 頁面上，按一下 [**下載**] 及 [**執行**。</span><span class="sxs-lookup"><span data-stu-id="6ca99-137">On the **Microsoft Azure Active Directory Connect** page, click **Download**, and then click **Run**.</span></span>
    
4. <span data-ttu-id="6ca99-138">在 [**歡迎使用 Azure AD 連線**] 頁面上按一下 [**我同意**] 和 [**繼續。**</span><span class="sxs-lookup"><span data-stu-id="6ca99-138">On the **Welcome to Azure AD Connect** page, click **I agree**, and then click **Continue.**</span></span>
    
5. <span data-ttu-id="6ca99-139">按一下 [ **Express 設定**] 頁面上的 [**自訂**]。</span><span class="sxs-lookup"><span data-stu-id="6ca99-139">On the **Express Settings** page, click **Customize**.</span></span>
    
6. <span data-ttu-id="6ca99-140">按一下 [**安裝所需的元件**] 頁面的 [**安裝**]。</span><span class="sxs-lookup"><span data-stu-id="6ca99-140">On the **Install required components** page, click **Install**.</span></span>
    
7. <span data-ttu-id="6ca99-141">在 [使用者登入]**** 頁面上，按一下 [和 AD FS 的同盟]****，然後按 [下一步]****。</span><span class="sxs-lookup"><span data-stu-id="6ca99-141">On the **User sign-in** page, click **Federation with AD FS**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="6ca99-142">在 [**連接到 Azure AD** ] 頁面輸入名稱與您的 Office 365 訂閱的全域管理員帳戶的密碼並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="6ca99-142">On the **Connect to Azure AD** page, type the name and password of a global administrator account for your Office 365 subscription, and then click **Next**.</span></span>
    
9. <span data-ttu-id="6ca99-143">在**您的目錄連線**] 頁面上確認**樹系**中已選取您的內部部署 Windows Server AD 樹系、 輸入的名稱與網域管理員帳戶的密碼、 按一下 [**新增目錄**]，然後按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="6ca99-143">On the **Connect your directories** page, ensure that your on-premises Windows Server AD forest is selected in **Forest**, type the name and password of a domain administrator account, click **Add Directory**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="6ca99-144">在**Azure AD 登入設定**] 頁面上，按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="6ca99-144">On the **Azure AD sign-in configuration** page, click **Next**.</span></span>
    
11. <span data-ttu-id="6ca99-145">按一下 [**網域及 OU 篩選**] 頁面的 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="6ca99-145">On the **Domain and OU filtering** page, click **Next**.</span></span>
    
12. <span data-ttu-id="6ca99-146">**唯一識別您的使用者**] 頁面上按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="6ca99-146">On the **Uniquely identifying your users** page, click **Next**.</span></span>
    
13. <span data-ttu-id="6ca99-147">按一下 [**篩選使用者和裝置**] 索引標籤的 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="6ca99-147">On the **Filter users and devices** page, click **Next**.</span></span>
    
14. <span data-ttu-id="6ca99-148">在 [**選用功能**] 頁面上按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="6ca99-148">On the **Optional features** page, click **Next**.</span></span>
    
15. <span data-ttu-id="6ca99-149">按一下 [ **AD FS 伺服器陣列**] 頁面的 [**設定新的 AD FS 伺服器陣列**]。</span><span class="sxs-lookup"><span data-stu-id="6ca99-149">On the **AD FS farm** page, click **Configure a new AD FS farm**.</span></span>
    
16. <span data-ttu-id="6ca99-150">按一下 [**瀏覽**並指定的位置和來自公用憑證授權單位的 SSL 憑證的名稱。</span><span class="sxs-lookup"><span data-stu-id="6ca99-150">Click **Browse** and specify the location and name of the SSL certificate from the public certification authority.</span></span>
    
17. <span data-ttu-id="6ca99-151">出現提示時，輸入憑證的密碼，並再按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="6ca99-151">When prompted, type the certificate password, and then click **OK**.</span></span>
    
18. <span data-ttu-id="6ca99-152">確認的**主體名稱**和**同盟服務名稱**設定為同盟服務 FQDN]，然後按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="6ca99-152">Verify that the **Subject Name** and **Federation Service Name** are set to your federation service FQDN, and then click **Next**.</span></span>
    
19. <span data-ttu-id="6ca99-153">在**AD FS 伺服器**] 頁面上輸入第一部 AD FS 伺服器的名稱 （表格 M-項目 4-虛擬機器名稱] 欄中），並再按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="6ca99-153">On the **AD FS servers** page, type your first AD FS server's name (Table M - Item 4 - Virtual machine name column), and then click **Add**.</span></span>
    
20. <span data-ttu-id="6ca99-154">輸入第二個 AD FS 伺服器的名稱 （表格 M-項目 5-虛擬機器名稱] 欄中）、 按一下 [**新增**]，並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="6ca99-154">Type your second AD FS server's name (Table M - Item 5 - Virtual machine name column), click **Add**, and then click **Next**.</span></span>
    
21. <span data-ttu-id="6ca99-155">在 [ **Web 應用程式 Proxy 伺服器**] 頁面上輸入第一個 web 應用程式 proxy 伺服器的名稱 （表格 M-項目 6-虛擬機器名稱] 欄中），並再按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="6ca99-155">On the **Web Application Proxy servers** page, type your first web application proxy server's name (Table M - Item 6 - Virtual machine name column), and then click **Add**.</span></span>
    
22. <span data-ttu-id="6ca99-156">輸入第二個 web 應用程式 proxy 伺服器的名稱 （表格 M-項目 7-虛擬機器名稱] 欄中）、 按一下 [**新增**]，並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="6ca99-156">Type your second web application proxy server's name (Table M - Item 7 - Virtual machine name column), click **Add**, and then click **Next**.</span></span>
    
23. <span data-ttu-id="6ca99-157">在 [**網域系統管理員認證**] 頁面上輸入使用者名稱和密碼的網域管理員帳戶，並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="6ca99-157">On the **Domain Administrator credentials** page, type the user name and password of a domain administrator account, and then click **Next**.</span></span>
    
24. <span data-ttu-id="6ca99-158">在**AD FS 服務帳戶**] 頁面上輸入使用者名稱和密碼的企業系統管理員帳戶，並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="6ca99-158">On the **AD FS service account** page, type the user name and password of an enterprise administrator account, and then click **Next**.</span></span>
    
25. <span data-ttu-id="6ca99-159">在**Azure AD 網域**] 頁面的 [**網域**] 中，選取您的組織 DNS 網域名稱，並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="6ca99-159">On the **Azure AD Domain** page, in **Domain**, select your organization's DNS domain name, and then click **Next**.</span></span>
    
26. <span data-ttu-id="6ca99-160">在 [準備設定]**** 頁面上，按一下 [安裝]****。</span><span class="sxs-lookup"><span data-stu-id="6ca99-160">On the **Ready to configure** page, click **Install**.</span></span>
    
27. <span data-ttu-id="6ca99-p105">按一下 [**安裝完成**] 頁面的 [**驗證**]。您應該在內部網路和網際網路看到兩個訊息，指出已順利驗證組態。</span><span class="sxs-lookup"><span data-stu-id="6ca99-p105">On the **Installation complete** page, click **Verify**. You should see two messages indicating that both the intranet and Internet configuration was successfully verified.</span></span>
    
  - <span data-ttu-id="6ca99-163">內部網路訊息應列出您的 Azure 內部負載平衡器 AD FS 伺服器的私人 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="6ca99-163">The intranet message should list the private IP address of your Azure internal load balancer for your AD FS servers.</span></span>
    
  - <span data-ttu-id="6ca99-164">網際網路訊息應列出 web 應用程式 proxy 伺服器您 Azure 網際網路對向負載平衡器的公用 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="6ca99-164">The Internet message should list the public IP address of your Azure Internet-facing load balancer for your web application proxy servers.</span></span>
    
28. <span data-ttu-id="6ca99-165">在 [安裝完成]**** 頁面上，按一下 [結束]****。</span><span class="sxs-lookup"><span data-stu-id="6ca99-165">On the **Installation complete** page, click **Exit**.</span></span>
    
<span data-ttu-id="6ca99-166">以下是與伺服器的版面配置區名稱的最後一個設定。</span><span class="sxs-lookup"><span data-stu-id="6ca99-166">Here is the final configuration, with placeholder names for the servers.</span></span>
  
<span data-ttu-id="6ca99-167">**階段 5： 高可用性的最後一個設定同盟 Azure 中的驗證基礎結構**</span><span class="sxs-lookup"><span data-stu-id="6ca99-167">**Phase 5: The final configuration of a high availability federated authentication infrastructure in Azure**</span></span>

![Azure 中高可用性 Office 365 同盟驗證基礎結構的最後設定](media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
<span data-ttu-id="6ca99-169">您在 Azure 中的 Office 365 的高可用性同盟的驗證基礎架構即完成。</span><span class="sxs-lookup"><span data-stu-id="6ca99-169">Your high availability federated authentication infrastructure for Office 365 in Azure is complete.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6ca99-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ca99-170">See Also</span></span>

[<span data-ttu-id="6ca99-171">Azure 中的 Office 365 高可用性同盟驗證</span><span class="sxs-lookup"><span data-stu-id="6ca99-171">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="6ca99-172">Office 365 開發人員/測試環境的同盟身分識別</span><span class="sxs-lookup"><span data-stu-id="6ca99-172">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="6ca99-173">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="6ca99-173">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="6ca99-174">Office 365 的同盟身分識別</span><span class="sxs-lookup"><span data-stu-id="6ca99-174">Federated identity for Office 365</span></span>](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


