---
title: Office 365 協力廠商的 SSL 憑證的計劃
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 10/24/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: b48cdf63-07e0-4cda-8c12-4871590f59ce
description: 摘要：說明 Exchange 內部和混合部署、使用 AD FS 的 SSO、Exchange Online 服務及 Exchange Web 服務所需的 SSL 憑證。
ms.openlocfilehash: 1746cf5059ba83e225e4a2d55c8eebc082366362
ms.sourcegitcommit: bdd0083dc9dc62994de29421a1f4056ebe27f15f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "29952469"
---
# <a name="plan-for-third-party-ssl-certificates-for-office-365"></a><span data-ttu-id="dafc5-103">Office 365 協力廠商的 SSL 憑證的計劃</span><span class="sxs-lookup"><span data-stu-id="dafc5-103">Plan for third-party SSL certificates for Office 365</span></span>

 <span data-ttu-id="dafc5-104">**摘要：** 說明 Exchange 內部和混合部署、 使用 AD FS 的 SSO 所需的 SSL 憑證 Exchange Online 服務及 Exchange Web 服務。</span><span class="sxs-lookup"><span data-stu-id="dafc5-104">**Summary:** Describes the SSL certificates needed for Exchange on-premises and hybrid, SSO using AD FS, Exchange Online services, and Exchange Web Services.</span></span> 
  
<span data-ttu-id="dafc5-105">若要將用戶端與 Office 365 環境之間的通訊加密，必須基礎結構伺服器上安裝協力廠商安全通訊端層 (SSL) 憑證。</span><span class="sxs-lookup"><span data-stu-id="dafc5-105">To encrypt communications between your clients and the Office 365 environment, third-party Secure Socket Layer (SSL) certificates must be installed on your infrastructure servers.</span></span>

||
|:-----|
| <span data-ttu-id="dafc5-106">本文是[網路規劃和 Office 365 的效能調整](https://aka.ms/tune)的一部分。</span><span class="sxs-lookup"><span data-stu-id="dafc5-106">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|
   
<span data-ttu-id="dafc5-107">下列 Office 365 元件需要憑證：</span><span class="sxs-lookup"><span data-stu-id="dafc5-107">Certificates are required for the following Office 365 components:</span></span>
  
- <span data-ttu-id="dafc5-108">Exchange 內部部署</span><span class="sxs-lookup"><span data-stu-id="dafc5-108">Exchange on-premises</span></span>
    
- <span data-ttu-id="dafc5-109">單一登入 (SSO) (針對 Active Directory Federation Services (AD FS) 同盟伺服器和 AD FS 同盟伺服器 Proxy)</span><span class="sxs-lookup"><span data-stu-id="dafc5-109">Single sign-on (SSO) (for both the Active Directory Federation Services (AD FS) federation servers and AD FS federation server proxies)</span></span>
    
- <span data-ttu-id="dafc5-110">Exchange Online 服務，例如自動探索、 「 Outlook 無所不在 」，以及 Exchange Web 服務</span><span class="sxs-lookup"><span data-stu-id="dafc5-110">Exchange Online services, such as Autodiscover, Outlook Anywhere, and Exchange Web Services</span></span>
    
- <span data-ttu-id="dafc5-111">Exchange 混合伺服器</span><span class="sxs-lookup"><span data-stu-id="dafc5-111">Exchange hybrid server</span></span>
    
## <a name="certificates-for-exchange-on-premises"></a><span data-ttu-id="dafc5-112">Exchange 內部部署的憑證</span><span class="sxs-lookup"><span data-stu-id="dafc5-112">Certificates for Exchange On-Premises</span></span>

<span data-ttu-id="dafc5-113">如需如何使用數位憑證保護內部部署 Exchange 組織與 Exchange Online 之間的通訊安全，請參閱 TechNet 文章[了解憑證需求](https://go.microsoft.com/fwlink/p/?LinkID=243657)的概觀。</span><span class="sxs-lookup"><span data-stu-id="dafc5-113">For an overview about how to use digital certificates to make the communication between the on-premises Exchange organization and Exchange Online secure, see the TechNet article [Understanding Certificate Requirements](https://go.microsoft.com/fwlink/p/?LinkID=243657).</span></span>
  
## <a name="certificates-for-single-sign-on"></a><span data-ttu-id="dafc5-114">單一登入的憑證</span><span class="sxs-lookup"><span data-stu-id="dafc5-114">Certificates for Single Sign-On</span></span>

<span data-ttu-id="dafc5-p101">簡化單一登入經驗，包含完善的安全性提供您的使用者，在同盟伺服器或同盟伺服器 proxy 需要下表所示憑證。下表重點在於 Active Directory Federation Services (AD FS)，我們也可以使用[協力廠商身分識別提供者](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-fed-compatibility)的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="dafc5-p101">To provide your users with a simplified single sign-on experience that includes robust security, the certificates shown in the following table are required on either the federation servers or the federation server proxies. The table below focuses on Active Directory Federation Services (AD FS), we also have more information on [using third-party identity providers](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-fed-compatibility).</span></span>
  
||||
|:-----|:-----|:-----|
|<span data-ttu-id="dafc5-117">**憑證類型**</span><span class="sxs-lookup"><span data-stu-id="dafc5-117">**Certificate Type**</span></span> <br/> |<span data-ttu-id="dafc5-118">**描述**</span><span class="sxs-lookup"><span data-stu-id="dafc5-118">**Description**</span></span> <br/> |<span data-ttu-id="dafc5-119">**開始部署之前您必須了解的資訊**</span><span class="sxs-lookup"><span data-stu-id="dafc5-119">**What you need to know before you deploy**</span></span> <br/> |
|<span data-ttu-id="dafc5-120">**SSL 憑證 (也稱為伺服器驗證憑證)**</span><span class="sxs-lookup"><span data-stu-id="dafc5-120">**SSL certificate (also called a server authentication certificate)**</span></span> <br/> |<span data-ttu-id="dafc5-121">這是一個標準 SSL 憑證，用來保護同盟伺服器、用戶端及同盟伺服器 Proxy 電腦之間的通訊安全。</span><span class="sxs-lookup"><span data-stu-id="dafc5-121">This is a standard SSL certificate that is used to make communications between federation servers, clients, and federation server proxy computers secure.</span></span>  <br/> |<span data-ttu-id="dafc5-p102">AD FS 需要 SSL 憑證。根據預設，AD FS 會使用預設網站在網際網路資訊服務 (IIS) 設定 SSL 憑證。</span><span class="sxs-lookup"><span data-stu-id="dafc5-p102">AD FS requires an SSL certificate. By default, AD FS uses the SSL certificate that is configured for the default website in Internet Information Services (IIS).  </span></span><br/> <span data-ttu-id="dafc5-p103">這個 SSL 憑證的主體名稱用於判斷每個您所部署的 AD FS 執行個體的同盟服務 (FS) 名稱。請考慮選擇任何新的憑證授權單位 (CA) 的主體名稱-發出憑證適合代表公司或組織至 Office 365 的名稱。此名稱必須是網際網路可路由。</span><span class="sxs-lookup"><span data-stu-id="dafc5-p103">The subject name of this SSL certificate is used to determine the Federation Service (FS) name for each instance of AD FS that you deploy. Consider choosing a subject name for any new certification authority (CA)-issued certificates that best represents the name of your company or organization to Office 365. This name must be Internet-routable.  </span></span><br/><span data-ttu-id="dafc5-127">**小心：** AD FS 會要求這個 SSL 憑證沒有無點 （簡短名稱） 的主體名稱。</span><span class="sxs-lookup"><span data-stu-id="dafc5-127">**Caution:** AD FS requires that this SSL certificate have no dotless (short-name) subject name.</span></span>          <br/> <span data-ttu-id="dafc5-128">**建議：** 因為此憑證必須由用戶端的 AD FS 信任，建議您依照公用 （第三方） CA 或公開受信任的根; 從屬於 CA 所發出的 SSL 憑證例如，VeriSign 或 Thawte。</span><span class="sxs-lookup"><span data-stu-id="dafc5-128">**Recommendation:** Because this certificate must be trusted by clients of AD FS, we recommend that you use an SSL certificate issued by a public (third-party) CA or by a CA that is subordinate to a publicly trusted root; for example, VeriSign or Thawte.</span></span>  <br/> |
|<span data-ttu-id="dafc5-129">**權杖簽署憑證**</span><span class="sxs-lookup"><span data-stu-id="dafc5-129">**Token-signing certificate**</span></span> <br/> |<span data-ttu-id="dafc5-130">這是標準的 X.509 憑證，用來安全地簽署同盟伺服器問題以及 Office 365 所接受並驗證的所有 token。</span><span class="sxs-lookup"><span data-stu-id="dafc5-130">This is a standard X.509 certificate that's used for securely signing all tokens that the federation server issues and that Office 365 accepts and validates.</span></span>  <br/> |<span data-ttu-id="dafc5-p104">權杖簽署憑證必須包含鏈結到受信任的根 FS 中的私密金鑰。根據預設，AD FS 會建立自我簽署的憑證。不過，根據組織的需求，您可以變更此憑證 CA 發行的憑證來使用 AD FS 管理] 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="dafc5-p104">The token-signing certificate must contain a private key that chains to a trusted root in the FS. By default, AD FS creates a self-signed certificate. However, depending on the needs of your organization, you can change this certificate to a CA-issued certificate by using the AD FS management snap-in.  </span></span><br/><span data-ttu-id="dafc5-p105">**小心：** 權杖簽署憑證是重要的 FS 穩定性。如果變更憑證，Office 365 必須通知的變更。如果未提供通知使用者無法登入其 Office 365 服務方案。</span><span class="sxs-lookup"><span data-stu-id="dafc5-p105">**Caution:** The token-signing certificate is critical to the stability of the FS. If the certificate is changed, Office 365 must be notified of the change. If notification is not provided, users can't sign in to their Office 365 service offerings.</span></span><br/><span data-ttu-id="dafc5-p106">**建議：** 我們建議您使用自我簽署的權杖簽署憑證產生的 AD FS。如此一來，它會管理此憑證您預設。例如，此憑證即將到期時，AD FS 將會產生新的自我簽署的憑證。</span><span class="sxs-lookup"><span data-stu-id="dafc5-p106">**Recommendation:** We recommend that you use the self-signed token-signing certificate that is generated by AD FS. By doing so, it manages this certificate for you by default. For example, when this certificate is about to expire, AD FS will generate a new self-signed certificate.  </span></span><br/> |
   
<span data-ttu-id="dafc5-140">同盟伺服器 Proxy 需要下表中所述的憑證。</span><span class="sxs-lookup"><span data-stu-id="dafc5-140">Federation server proxies require the certificate that is described in the following table.</span></span>
  
||||
|:-----|:-----|:-----|
|<span data-ttu-id="dafc5-141">**憑證類型**</span><span class="sxs-lookup"><span data-stu-id="dafc5-141">**Certificate Type**</span></span> <br/> |<span data-ttu-id="dafc5-142">**描述**</span><span class="sxs-lookup"><span data-stu-id="dafc5-142">**Description**</span></span> <br/> |<span data-ttu-id="dafc5-143">**開始部署之前您必須了解的資訊**</span><span class="sxs-lookup"><span data-stu-id="dafc5-143">**What you need to know before you deploy**</span></span> <br/> |
|<span data-ttu-id="dafc5-144">SSL 憑證</span><span class="sxs-lookup"><span data-stu-id="dafc5-144">SSL certificate</span></span>  <br/> |<span data-ttu-id="dafc5-145">這是一個標準 SSL 憑證，用來保護同盟伺服器、同盟伺服器 Proxy 及網際網路用戶端電腦之間的通訊安全。</span><span class="sxs-lookup"><span data-stu-id="dafc5-145">This is a standard SSL certificate that is used for securing communications between a federation server, a federation server proxy, and Internet client computers.</span></span>  <br/> |<span data-ttu-id="dafc5-146">這個 SSL 憑證必須繫結至 IIS 中的預設網站才可成功執行 [AD FS 同盟伺服器 Proxy 設定精靈]。</span><span class="sxs-lookup"><span data-stu-id="dafc5-146">This SSL certificate must be bound to the default website in IIS before you can successfully run the AD FS Federation Server Proxy Configuration wizard.</span></span>  <br/> <span data-ttu-id="dafc5-147">這個憑證的主體名稱必須與公司網路中同盟伺服器上設定之 SSL 憑證的主體名稱相同。</span><span class="sxs-lookup"><span data-stu-id="dafc5-147">This certificate must have the same subject name as the SSL certificate that was configured on the federation server in the corporate network.</span></span>  <br/> <span data-ttu-id="dafc5-148">**建議：** 建議您使用此同盟伺服器 Proxy 所連線之同盟伺服器上設定的同一個伺服器驗證憑證。</span><span class="sxs-lookup"><span data-stu-id="dafc5-148">**Recommendation:** We recommend that you use the same server authentication certificate that is configured on the federation server that this federation server proxy connects to.</span></span>  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a><span data-ttu-id="dafc5-149">自動探索 」、 「 Outlook 無所不在 」 及 「 Active Directory 同步處理的憑證</span><span class="sxs-lookup"><span data-stu-id="dafc5-149">Certificates for Autodiscover, Outlook Anywhere, and Active Directory Synchronization</span></span>

<span data-ttu-id="dafc5-p107">向外 Exchange 2013、 Exchange 2010、 Exchange 2007 與 Exchange 2003 用戶端存取伺服器 （類別） 需要第三方 SSL 憑證的自動探索、 Outlook 無所不在，與 Active Directory 同步處理服務的安全連線。您可能已安裝在您的內部部署環境中此憑證。</span><span class="sxs-lookup"><span data-stu-id="dafc5-p107">Your external-facing Exchange 2013, Exchange 2010, Exchange 2007, and Exchange 2003 Client Access servers (CASs) require a third-party SSL certificate for secure connections for Autodiscover, Outlook Anywhere, and Active Directory synchronization services. You may already have this certificate installed in your on-premises environment.</span></span>
  
## <a name="certificate-for-an-exchange-hybrid-server"></a><span data-ttu-id="dafc5-152">適用於 Exchange 混合式伺服器的憑證</span><span class="sxs-lookup"><span data-stu-id="dafc5-152">Certificate for an Exchange Hybrid Server</span></span>

<span data-ttu-id="dafc5-p108">向外 Exchange 混合伺服器需要安全連線與 Exchange Online 服務的第三方 SSL 憑證。您需要從您的第三方 SSL 提供者取得此憑證。</span><span class="sxs-lookup"><span data-stu-id="dafc5-p108">Your external-facing Exchange hybrid server or servers require a third-party SSL certificate for secure connectivity with the Exchange Online service. You need to get this certificate from your third-party SSL provider.</span></span>
  
## <a name="office-365-certificate-chains"></a><span data-ttu-id="dafc5-155">Office 365 憑證鏈結</span><span class="sxs-lookup"><span data-stu-id="dafc5-155">Office 365 Certificate Chains</span></span>

<span data-ttu-id="dafc5-p109">本文說明您可能需要在您的基礎結構上安裝的憑證。如需有關我們 Office 365 的伺服器上已安裝的憑證的詳細資訊，請參閱[Office 365 憑證鏈結](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb)。</span><span class="sxs-lookup"><span data-stu-id="dafc5-p109">This article describes the certificates you may need to install on your infrastructure. For more information on the certificates installed on our Office 365 servers, see [Office 365 Certificate Chains](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb).</span></span>
  

