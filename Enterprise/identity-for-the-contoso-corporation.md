---
title: Contoso Corporation 的身分識別
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 78a407e4-2d8b-4561-b308-b22c95f60eeb
description: 摘要： 了解如何利用 IDaaS Contoso，並提供地理位置分散變得多餘的和驗證其使用者。
ms.openlocfilehash: 25e708147bda51fa8f8b4d0ea5e83eb4a9cd10b0
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915438"
---
# <a name="identity-for-the-contoso-corporation"></a><span data-ttu-id="b75df-103">Contoso Corporation 的身分識別</span><span class="sxs-lookup"><span data-stu-id="b75df-103">Identity for the Contoso Corporation</span></span>

 <span data-ttu-id="b75df-104">**摘要：** 了解如何利用 IDaaS Contoso，並提供地理位置分散變得多餘的和驗證其使用者。</span><span class="sxs-lookup"><span data-stu-id="b75df-104">**Summary:** Understand how Contoso takes advantage of IDaaS and provides geographically distributed and redundant authentication for its users.</span></span>
  
<span data-ttu-id="b75df-p101">Microsoft 會提供跨其雲端方案以服務 (IDaaS) 的身分識別。若要採用雲端 （含） 的基礎結構，Contoso 的 IDaaS 解決方案必須並用其內部身分識別提供者並包括使用其現有的受信任、 協力廠商身分識別提供者同盟的驗證。</span><span class="sxs-lookup"><span data-stu-id="b75df-p101">Microsoft provides an Identity as a Service (IDaaS) across its cloud offerings. To adopt a cloud-inclusive infrastructure, Contoso's IDaaS solution must leverage their on-premises identity provider and include federated authentication with their existing trusted, third-party identity providers.</span></span>
  
## <a name="contosos-windows-server-ad-forest"></a><span data-ttu-id="b75df-107">Contoso 的 Windows Server AD 樹系</span><span class="sxs-lookup"><span data-stu-id="b75df-107">Contoso's Windows Server AD forest</span></span>

<span data-ttu-id="b75df-p102">Contoso 會使用單一 Windows Server Active Directory (AD) 樹系與另一個適用於每個區域的全球的七個網域 contoso.com。Headquarters、 區域 hub 辦公室和衛星辦公室包含本機驗證和授權的網域控制站。</span><span class="sxs-lookup"><span data-stu-id="b75df-p102">Contoso uses a single Windows Server Active Directory (AD) forest for contoso.com with seven domains, one for each region of the world. The headquarters, regional hub offices, and satellite offices contain domain controllers for local authentication and authorization.</span></span>
  
<span data-ttu-id="b75df-110">**圖 1： Contoso 的樹系及網域組成的全球**</span><span class="sxs-lookup"><span data-stu-id="b75df-110">**Figure 1: Contoso's forest and domains worldwide**</span></span>

![Contoso 的 Windows Server AD 樹系和世界各地的網域](media/Contoso-Poster/Contoso-WW-ID.png)
  
<span data-ttu-id="b75df-112">圖 1 顯示與區域不同組件的全球包含區域的集線器網域 Contoso 樹系。</span><span class="sxs-lookup"><span data-stu-id="b75df-112">Figure 1 shows the Contoso forest with regional domains for the different parts of the world that contain regional hubs.</span></span>
  
<span data-ttu-id="b75df-113">Contoso 想要使用的帳戶和群組 contoso.com 樹系中的驗證與授權其雲端應用程式及工作負載。</span><span class="sxs-lookup"><span data-stu-id="b75df-113">Contoso wants to use the accounts and groups in the contoso.com forest for authentication and authorization for its cloud-based apps and workloads.</span></span>
  
## <a name="contosos-federated-authentication-infrastructure"></a><span data-ttu-id="b75df-114">Contoso 的同盟的驗證基礎結構</span><span class="sxs-lookup"><span data-stu-id="b75df-114">Contoso's federated authentication infrastructure</span></span>

<span data-ttu-id="b75df-115">Contoso 可讓：</span><span class="sxs-lookup"><span data-stu-id="b75df-115">Contoso allows:</span></span>
  
- <span data-ttu-id="b75df-116">客戶使用其 Microsoft、 Facebook、 或 Google Mail 的帳戶登入其公用網站。</span><span class="sxs-lookup"><span data-stu-id="b75df-116">Customers to use their Microsoft, Facebook, or Google Mail accounts to sign in to their public web site.</span></span>
    
- <span data-ttu-id="b75df-117">廠商與協力廠商使用其 LinkedIn、 Salesforce、 或 Google Mail 的帳戶登入網路之協力廠商。</span><span class="sxs-lookup"><span data-stu-id="b75df-117">Vendors and partners to use their LinkedIn, Salesforce, or Google Mail accounts to sign in to the partner extranet.</span></span>
    
<span data-ttu-id="b75df-118">**圖 2： Contoso 的驗證支援的同盟的客戶與合作夥伴**</span><span class="sxs-lookup"><span data-stu-id="b75df-118">**Figure 2: Contoso's support for federated authentication for customers and partners**</span></span>

![Contoso 現有的基礎結構，用以支援客戶和合作夥伴同盟驗證](media/Contoso-Poster/Federated-ID.png)
  
<span data-ttu-id="b75df-p103">圖 2 顯示包含公用網站、 外部網路是合作夥伴與 AD FS 伺服器的一組 Contoso DMZ。DMZ 被連線至網際網路包含客戶和合作夥伴與網際網路服務。</span><span class="sxs-lookup"><span data-stu-id="b75df-p103">Figure 2 shows the Contoso DMZ containing a public web site, a partner extranet, and a set of AD FS servers. The DMZ is connected to the Internet that contains customers and partners and Internet services.</span></span>
  
<span data-ttu-id="b75df-122">客戶認證以存取公用網站及合作夥伴外部存取的協力廠商認證進行驗證 DMZ 中的 active Directory Federation Services (AD FS) 伺服器。</span><span class="sxs-lookup"><span data-stu-id="b75df-122">Active Directory Federation Services (AD FS) servers in the DMZ authenticate customer credentials for access to the public web site and partner credentials for access to the partner extranet.</span></span>
  
<span data-ttu-id="b75df-p104">當 Contoso 轉換至 Azure Web 應用程式與合作夥伴外部 Dynamics 365 至其公用網站時，他們想要繼續使用其客戶和合作夥伴這些協力廠商身分識別提供者。這會藉由設定 Contoso Azure AD 租用戶與這些協力廠商身分識別提供者之間的同盟。</span><span class="sxs-lookup"><span data-stu-id="b75df-p104">When Contoso transitions its public web site to an Azure Web App and partner extranet to Dynamics 365, they want to continue to use these third-party identity providers for their customers and partners. This will be accomplished by configuring federation between Contoso Azure AD tenants and these third-party identity providers.</span></span>
  
## <a name="directory-synchronization-for-contosos-windows-server-ad-forest"></a><span data-ttu-id="b75df-125">Contoso 的 Windows Server AD 樹系目錄同步處理</span><span class="sxs-lookup"><span data-stu-id="b75df-125">Directory synchronization for Contoso's Windows Server AD forest</span></span>

<span data-ttu-id="b75df-p105">Contoso 已部署在其 Paris 資料中心伺服器的叢集上 「 Azure AD 連線工具。Azure AD 連線同步處理與共用的 Contoso 的 Office 365、 EMS、 Dynamics 365 和 Azure 訂閱 Azure AD 租用 contoso.com Windows Server AD 樹系的變更。如需訂閱、 授權、 使用者帳戶及租用戶的詳細資訊，請參閱[訂閱、 授權及使用者帳戶為 Contoso Corporation](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md)。</span><span class="sxs-lookup"><span data-stu-id="b75df-p105">Contoso has deployed the Azure AD Connect tool on a cluster of servers in its Paris datacenter. Azure AD Connect synchronizes changes to the contoso.com Windows Server AD forest with the Azure AD tenant shared by Contoso's Office 365, EMS, Dynamics 365, and Azure subscriptions. For more information about subscriptions, licenses, user accounts, and tenants, see [Subscriptions, licenses, and user accounts for the Contoso Corporation](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md).</span></span>
  
<span data-ttu-id="b75df-129">**圖 3： Contoso 的目錄同步處理基礎結構**</span><span class="sxs-lookup"><span data-stu-id="b75df-129">**Figure 3: Contoso's directory synchronization infrastructure**</span></span>

![Contoso 的目錄同步處理基礎結構](media/Contoso-Poster/DirSync.png)
  
<span data-ttu-id="b75df-131">圖 3 是執行使用 Azure AD 租用戶同步處理 Contoso Windows Server AD 樹系的 Azure AD 連線的伺服器叢集。</span><span class="sxs-lookup"><span data-stu-id="b75df-131">Figure 3 shows a cluster of servers running Azure AD Connect synchronizing the Contoso Windows Server AD forest with the Azure AD tenant.</span></span>
  
<span data-ttu-id="b75df-p106">Contoso 已設定的同盟的驗證，Contoso 的工作者提供單一登入。當使用者已經登入 contoso.com Windows Server AD 樹系存取 Microsoft SaaS 或 PaaS 雲端資源時，他們便不會提示密碼。</span><span class="sxs-lookup"><span data-stu-id="b75df-p106">Contoso has configured federated authentication, which provides single sign-on for Contoso's workers. When a user that has already signed in to the contoso.com Windows Server AD forest accesses a Microsoft SaaS or PaaS cloud resource, they will not be prompted for a password.</span></span>
  
## <a name="geographical-distribution-of-contoso-authentication-traffic"></a><span data-ttu-id="b75df-134">Contoso 驗證流量的地理位置分布</span><span class="sxs-lookup"><span data-stu-id="b75df-134">Geographical distribution of Contoso authentication traffic</span></span>

<span data-ttu-id="b75df-p107">若要更妥善地支援其行動電話和遠端工作團隊，Contoso 已部署在其區域辦公室驗證伺服器的設定。此基礎結構負載分散每個，並使用一般的 Azure AD 租用戶的 Microsoft cloud 方案存取的使用者認證進行驗證時提供備援和更高的效能。</span><span class="sxs-lookup"><span data-stu-id="b75df-p107">To better support its mobile and remote workforce, Contoso has deployed sets of authentication servers in its regional offices. This infrastructure distributes the load and provides redundancy and higher performance when authenticating user credentials for access to Microsoft cloud offerings that use the common Azure AD tenant.</span></span>
  
<span data-ttu-id="b75df-137">若要將驗證要求的負載，Contoso 已設定 Azure 流量管理員具有設定檔使用路由方法，這是指地域最接近的一組驗證伺服器驗證的用戶端的效能。</span><span class="sxs-lookup"><span data-stu-id="b75df-137">To distribute the load of authentication requests, Contoso has configured Azure Traffic Manager with a profile that uses the performance routing method, which refers authenticating clients to the regionally closest set of authentication servers.</span></span> 
  
<span data-ttu-id="b75df-138">**圖 4： 地區分公司的驗證流量的地理位置分布**</span><span class="sxs-lookup"><span data-stu-id="b75df-138">**Figure 4: Geographical distribution of authentication traffic for regional offices**</span></span>

![地區辦公室 Contoso 驗證流量的地理分配](media/Contoso-Poster/Auth-GeoDist.png)
  
<span data-ttu-id="b75df-p108">圖 4 顯示區域辦公室的用戶端電腦、 Azure 流量管理員和驗證伺服器層級。每個區域的 office 會使用 web proxy 伺服器和 AD FS 伺服器來驗證使用者認證與 Windows Server AD 網域控制站。</span><span class="sxs-lookup"><span data-stu-id="b75df-p108">Figure 4 shows the layers of client computers, Azure Traffic Manager, and authentication servers in regional offices. Each regional office uses web proxies and AD FS servers to authenticate user credentials with Windows Server AD domain controllers.</span></span>
  
<span data-ttu-id="b75df-142">驗證程序範例：</span><span class="sxs-lookup"><span data-stu-id="b75df-142">Authentication process example:</span></span>
  
1. <span data-ttu-id="b75df-143">用戶端電腦起始通訊網頁與 Office 365 租用中的歐洲 （例如 sharepoint.contoso.com)。</span><span class="sxs-lookup"><span data-stu-id="b75df-143">The client computer initiates communication with a web page in the Office 365 tenancy in Europe (such as sharepoint.contoso.com).</span></span>
    
2. <span data-ttu-id="b75df-p109">Office 365 後將要求傳送至傳送證明驗證。要求包含連絡人進行驗證的 URL。</span><span class="sxs-lookup"><span data-stu-id="b75df-p109">Office 365 sends back a request to send proof of authentication. The request contains the URL to contact for authentication.</span></span>
    
3. <span data-ttu-id="b75df-146">用戶端電腦嘗試在 URL 中的 DNS 名稱解析為 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="b75df-146">The client computer attempts to resolve the DNS name in the URL to an IP address.</span></span>
    
4. <span data-ttu-id="b75df-147">Azure 流量管理員收到的 DNS 查詢和用戶端電腦與用戶端電腦最接近地區性 office 中的 web 應用程式 proxy 伺服器的 IP 位址的回應。</span><span class="sxs-lookup"><span data-stu-id="b75df-147">Azure Traffic Manager receives the DNS query and responds to the client computer with the IP address of a web application proxy server in the regional office that is closest to the client computer.</span></span>
    
5.  <span data-ttu-id="b75df-148">用戶端電腦將驗證要求傳送至轉寄至 AD FS 伺服器要求的 web 應用程式 proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="b75df-148">The client computer sends an authentication request to a web application proxy server, which forwards the request to an AD FS server.</span></span>
    
6. <span data-ttu-id="b75df-149">AD FS 伺服器要求用戶端電腦的使用者認證。</span><span class="sxs-lookup"><span data-stu-id="b75df-149">The AD FS server requests the user credentials from the client computer.</span></span>
    
7. <span data-ttu-id="b75df-150">用戶端電腦而不提示使用者傳送使用者認證。</span><span class="sxs-lookup"><span data-stu-id="b75df-150">The client computer sends the user credentials without prompting the user.</span></span>
    
8. <span data-ttu-id="b75df-151">AD FS 伺服器會驗證與區域 office 中的 Windows Server AD 網域控制站的認證，並傳回用戶端電腦的安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="b75df-151">The AD FS server validates the credentials with a Windows Server AD domain controller in the regional office and returns a security token to the client computer.</span></span>
    
9. <span data-ttu-id="b75df-152">用戶端電腦將安全性權杖傳送至 Office 365。</span><span class="sxs-lookup"><span data-stu-id="b75df-152">The client computer sends the security token to Office 365.</span></span>
    
10. <span data-ttu-id="b75df-153">在驗證成功之後 Office 365 的安全性權杖快取及傳送要求用戶端電腦的步驟 1 中的網頁。</span><span class="sxs-lookup"><span data-stu-id="b75df-153">After successful validation, Office 365 caches the security token and sends the web page requested in step 1 to the client computer.</span></span>
    
## <a name="redundancy-for-the-headquarters-authentication-infrastructure-in-azure-iaas"></a><span data-ttu-id="b75df-154">在 Azure IaaS headquarters 驗證基礎結構的備援</span><span class="sxs-lookup"><span data-stu-id="b75df-154">Redundancy for the headquarters authentication infrastructure in Azure IaaS</span></span>

<span data-ttu-id="b75df-155">若要提供包含 15000 工作者 Paris headquarters 遠端和行動工作者備援，Contoso 已部署應用程式 proxy 與 AD FS 伺服器中的 Azure IaaS 第二組。</span><span class="sxs-lookup"><span data-stu-id="b75df-155">To provide redundancy for the remote and mobile workers of the Paris headquarters that contains 15,000 workers, Contoso has deployed a second set of application proxies and AD FS servers in Azure IaaS.</span></span>
  
<span data-ttu-id="b75df-156">**圖 5： Azure IaaS 變得多餘的驗證基礎結構**</span><span class="sxs-lookup"><span data-stu-id="b75df-156">**Figure 5: Redundant authentication infrastructure in Azure IaaS**</span></span>

![巴黎總部 Azure IaaS 中的備援驗證基礎結構](media/Contoso-Poster/Paris-Auth-Redun.png)
  
<span data-ttu-id="b75df-158">圖 5 顯示 web proxy 伺服器和 AD FS 伺服器中 DMZ 以及跨部署 Azure 中的每個其他設定虛擬網路。</span><span class="sxs-lookup"><span data-stu-id="b75df-158">Figure 5 shows web proxies and AD FS servers in the DMZ and an additional set of each in a cross-premises Azure virtual network.</span></span>
  
<span data-ttu-id="b75df-p110">Headquarters DMZ 中主要的驗證伺服器變成無法使用，IT 人員切換至部署在 Azure IaaS 備援組 」。後續的驗證要求從 Paris office 電腦會使用組中 Azure IaaS 直到更正可用性問題。</span><span class="sxs-lookup"><span data-stu-id="b75df-p110">When the primary authentication servers in the headquarters DMZ become unavailable, IT staff switch over to the redundant set deployed in Azure IaaS. Subsequent authentication requests from Paris office computers use the set in Azure IaaS until the availability problem is corrected.</span></span>
  
<span data-ttu-id="b75df-161">切換和回、 交換器 Contoso 更新要用於 web 應用程式 proxy 的一組不同的 IP 位址的 Paris 區域的 Azure 流量管理員設定檔：</span><span class="sxs-lookup"><span data-stu-id="b75df-161">To switch over and switch back, Contoso updates the Azure Traffic Manager profile for the Paris region to use a different set of IP addresses for the web application proxies:</span></span>
  
- <span data-ttu-id="b75df-162">DMZ 驗證伺服器可用、 DMZ 中使用之伺服器的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="b75df-162">When the DMZ authentication servers are available, use the IP addresses of the servers in the DMZ.</span></span>
    
- <span data-ttu-id="b75df-163">當 DMZ 驗證伺服器無法使用，在 Azure IaaS 中使用之伺服器的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="b75df-163">When the DMZ authentication servers are not available, use the IP addresses of the servers in Azure IaaS.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="b75df-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b75df-164">See Also</span></span>

[<span data-ttu-id="b75df-165">Microsoft 雲端中的 Contoso</span><span class="sxs-lookup"><span data-stu-id="b75df-165">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="b75df-166">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="b75df-166">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="b75df-167">Microsoft Cloud Identity for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="b75df-167">Microsoft Cloud Identity for Enterprise Architects</span></span>](http://aka.ms/cloudarchidentity)
  
[<span data-ttu-id="b75df-168">Office 365 的身分識別與裝置保護</span><span class="sxs-lookup"><span data-stu-id="b75df-168">Identity and Device Protection for Office 365</span></span>](http://aka.ms/o365protect_device)
  
[<span data-ttu-id="b75df-169">Microsoft 的 Enterprise Cloud 藍圖：IT 決策者的資源</span><span class="sxs-lookup"><span data-stu-id="b75df-169">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



