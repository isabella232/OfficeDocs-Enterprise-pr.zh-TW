---
title: Office 365 的協力廠商 SSL 憑證計劃
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: b48cdf63-07e0-4cda-8c12-4871590f59ce
description: 摘要： 說明 Exchange 內部部署和混合部署、 使用 AD FS 的 SSO 所需 SSL 憑證的 Exchange 線上服務，以及 Exchange Web 服務。
ms.openlocfilehash: 9b5bcb20272dcaf5c1df39179a4ba4b05fc04a28
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069349"
---
# <a name="plan-for-third-party-ssl-certificates-for-office-365"></a><span data-ttu-id="ab3c7-103">Office 365 的協力廠商 SSL 憑證計劃</span><span class="sxs-lookup"><span data-stu-id="ab3c7-103">Plan for third-party SSL certificates for Office 365</span></span>

 <span data-ttu-id="ab3c7-104">**摘要：** 說明 Exchange 內部部署和混合部署、 使用 AD FS 的 SSO 所需 SSL 憑證的 Exchange 線上服務，以及 Exchange Web 服務。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-104">**Summary:** Describes the SSL certificates needed for Exchange on-premises and hybrid, SSO using AD FS, Exchange Online services, and Exchange Web Services.</span></span> 
  
<span data-ttu-id="ab3c7-105">若要加密您的用戶端與 Office 365 環境之間的通訊，必須基礎結構伺服器上安裝協力廠商安全通訊端層 (SSL) 憑證。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-105">To encrypt communications between your clients and the Office 365 environment, third-party Secure Socket Layer (SSL) certificates must be installed on your infrastructure servers.</span></span>

||
|:-----|
| <span data-ttu-id="ab3c7-106">本文是[網路規劃和效能調整的 Office 365](https://aka.ms/tune)的一部分。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-106">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|
   
<span data-ttu-id="ab3c7-107">憑證所需的下列 Office 365 元件：</span><span class="sxs-lookup"><span data-stu-id="ab3c7-107">Certificates are required for the following Office 365 components:</span></span>
  
- <span data-ttu-id="ab3c7-108">Exchange 內部部署</span><span class="sxs-lookup"><span data-stu-id="ab3c7-108">Exchange on-premises</span></span>
    
- <span data-ttu-id="ab3c7-109">單一登入 (SSO) （針對 Active Directory Federation Services (AD FS) 同盟伺服器和 AD FS 同盟伺服器 proxy）</span><span class="sxs-lookup"><span data-stu-id="ab3c7-109">Single sign-on (SSO) (for both the Active Directory Federation Services (AD FS) federation servers and AD FS federation server proxies)</span></span>
    
- <span data-ttu-id="ab3c7-110">Exchange Online 服務，例如自動探索、 Outlook Anywhere 及 Exchange Web 服務</span><span class="sxs-lookup"><span data-stu-id="ab3c7-110">Exchange Online services, such as Autodiscover, Outlook Anywhere, and Exchange Web Services</span></span>
    
- <span data-ttu-id="ab3c7-111">Exchange 混合伺服器</span><span class="sxs-lookup"><span data-stu-id="ab3c7-111">Exchange hybrid server</span></span>
    
## <a name="certificates-for-exchange-on-premises"></a><span data-ttu-id="ab3c7-112">Exchange 內部部署的憑證</span><span class="sxs-lookup"><span data-stu-id="ab3c7-112">Certificates for Exchange On-Premises</span></span>

<span data-ttu-id="ab3c7-113">如需如何使用數位憑證來讓內部部署 Exchange 組織和 Exchange Online 之間的通訊安全，請參閱 TechNet 文章[了解憑證需求](https://go.microsoft.com/fwlink/p/?LinkID=243657)的概觀。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-113">For an overview about how to use digital certificates to make the communication between the on-premises Exchange organization and Exchange Online secure, see the TechNet article [Understanding Certificate Requirements](https://go.microsoft.com/fwlink/p/?LinkID=243657).</span></span>
  
## <a name="certificates-for-single-sign-on"></a><span data-ttu-id="ab3c7-114">單一登入的憑證</span><span class="sxs-lookup"><span data-stu-id="ab3c7-114">Certificates for Single Sign-On</span></span>

<span data-ttu-id="ab3c7-115">若要為使用者提供的簡化單一登入經驗，安全穩固下, 表所示的憑證所需要的同盟伺服器或同盟伺服器 proxy。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-115">To provide your users with a simplified single sign-on experience that includes robust security, the certificates shown in the following table are required on either the federation servers or the federation server proxies.</span></span> <span data-ttu-id="ab3c7-116">下表著重於 Active Directory Federation Services (AD FS)，我們也有使用[協力廠商身分識別提供者](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-fed-compatibility)的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-116">The table below focuses on Active Directory Federation Services (AD FS), we also have more information on [using third-party identity providers](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-fed-compatibility).</span></span>
  
||||
|:-----|:-----|:-----|
|<span data-ttu-id="ab3c7-117">**憑證類型**</span><span class="sxs-lookup"><span data-stu-id="ab3c7-117">**Certificate Type**</span></span> <br/> |<span data-ttu-id="ab3c7-118">**描述**</span><span class="sxs-lookup"><span data-stu-id="ab3c7-118">**Description**</span></span> <br/> |<span data-ttu-id="ab3c7-119">**您需要知道部署之前**</span><span class="sxs-lookup"><span data-stu-id="ab3c7-119">**What you need to know before you deploy**</span></span> <br/> |
|<span data-ttu-id="ab3c7-120">**SSL 憑證 （也稱為伺服器驗證憑證）**</span><span class="sxs-lookup"><span data-stu-id="ab3c7-120">**SSL certificate (also called a server authentication certificate)**</span></span> <br/> |<span data-ttu-id="ab3c7-121">這是一個標準 SSL 憑證，用來保護同盟伺服器、 用戶端與同盟伺服器 proxy 電腦之間的通訊安全。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-121">This is a standard SSL certificate that is used to make communications between federation servers, clients, and federation server proxy computers secure.</span></span>  <br/> |<span data-ttu-id="ab3c7-122">AD FS 需要 SSL 憑證。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-122">AD FS requires an SSL certificate.</span></span> <span data-ttu-id="ab3c7-123">根據預設，AD FS，請針對預設網站在網際網路資訊服務 (IIS) 設定 SSL 憑證。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-123">By default, AD FS uses the SSL certificate that is configured for the default website in Internet Information Services (IIS).</span></span>  <br/> <span data-ttu-id="ab3c7-124">這個 SSL 憑證的主體名稱用於判斷每個您所部署的 AD FS 執行個體的同盟服務 (FS) 名稱。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-124">The subject name of this SSL certificate is used to determine the Federation Service (FS) name for each instance of AD FS that you deploy.</span></span> <span data-ttu-id="ab3c7-125">選擇任何新的憑證授權單位 (CA) 的主體名稱，請考慮-已發行的憑證適合代表貴公司或組織到 Office 365 的名稱。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-125">Consider choosing a subject name for any new certification authority (CA)-issued certificates that best represents the name of your company or organization to Office 365.</span></span> <span data-ttu-id="ab3c7-126">此名稱必須是網際網路路由傳送。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-126">This name must be Internet-routable.</span></span>  <br/><span data-ttu-id="ab3c7-127">**警告：** AD FS 要求這個 SSL 憑證必須具備任何無點 （簡短名稱） 的主體名稱。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-127">**Caution:** AD FS requires that this SSL certificate have no dotless (short-name) subject name.</span></span>          <br/> <span data-ttu-id="ab3c7-128">**建議：** 因為此憑證必須受到信任的 AD FS 用戶端，我們建議您使用由公用 （協力廠商） CA 或屬於公開受信任的根; CA 所發出的 SSL 憑證例如，VeriSign 或 Thawte。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-128">**Recommendation:** Because this certificate must be trusted by clients of AD FS, we recommend that you use an SSL certificate issued by a public (third-party) CA or by a CA that is subordinate to a publicly trusted root; for example, VeriSign or Thawte.</span></span>  <br/> |
|<span data-ttu-id="ab3c7-129">**權杖簽署憑證**</span><span class="sxs-lookup"><span data-stu-id="ab3c7-129">**Token-signing certificate**</span></span> <br/> |<span data-ttu-id="ab3c7-130">這是標準的 X.509 憑證，用來安全地簽署同盟伺服器問題以及 Office 365 所接受並驗證的所有 token。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-130">This is a standard X.509 certificate that's used for securely signing all tokens that the federation server issues and that Office 365 accepts and validates.</span></span>  <br/> |<span data-ttu-id="ab3c7-131">權杖簽署憑證必須包含私密金鑰的鏈結到 FS 中的受信任的根。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-131">The token-signing certificate must contain a private key that chains to a trusted root in the FS.</span></span> <span data-ttu-id="ab3c7-132">根據預設，AD FS 會建立自我簽署的憑證。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-132">By default, AD FS creates a self-signed certificate.</span></span> <span data-ttu-id="ab3c7-133">不過，根據組織的需求，您可以變更此憑證 CA 發行的憑證來使用 AD FS 管理] 嵌入式管理單元中。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-133">However, depending on the needs of your organization, you can change this certificate to a CA-issued certificate by using the AD FS management snap-in.</span></span>  <br/><span data-ttu-id="ab3c7-134">**警告：** 權杖簽署憑證是重要的 FS 穩定性。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-134">**Caution:** The token-signing certificate is critical to the stability of the FS.</span></span> <span data-ttu-id="ab3c7-135">如果憑證已變更，則必須變更的通知 Office 365。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-135">If the certificate is changed, Office 365 must be notified of the change.</span></span> <span data-ttu-id="ab3c7-136">如果沒有提供通知，使用者無法登入其 Office 365 服務方案。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-136">If notification is not provided, users can't sign in to their Office 365 service offerings.</span></span><br/><span data-ttu-id="ab3c7-137">**建議：** 我們建議您使用自我簽署的權杖簽署憑證所產生的 AD FS。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-137">**Recommendation:** We recommend that you use the self-signed token-signing certificate that is generated by AD FS.</span></span> <span data-ttu-id="ab3c7-138">如此一來，它會管理此憑證為您預設。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-138">By doing so, it manages this certificate for you by default.</span></span> <span data-ttu-id="ab3c7-139">例如，當此憑證即將到期，AD FS 會產生新的自我簽署的憑證。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-139">For example, when this certificate is about to expire, AD FS will generate a new self-signed certificate.</span></span>  <br/> |
   
<span data-ttu-id="ab3c7-140">同盟伺服器 proxy 需要下表所述的憑證。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-140">Federation server proxies require the certificate that is described in the following table.</span></span>
  
||||
|:-----|:-----|:-----|
|<span data-ttu-id="ab3c7-141">**憑證類型**</span><span class="sxs-lookup"><span data-stu-id="ab3c7-141">**Certificate Type**</span></span> <br/> |<span data-ttu-id="ab3c7-142">**描述**</span><span class="sxs-lookup"><span data-stu-id="ab3c7-142">**Description**</span></span> <br/> |<span data-ttu-id="ab3c7-143">**您需要知道部署之前**</span><span class="sxs-lookup"><span data-stu-id="ab3c7-143">**What you need to know before you deploy**</span></span> <br/> |
|<span data-ttu-id="ab3c7-144">SSL 憑證</span><span class="sxs-lookup"><span data-stu-id="ab3c7-144">SSL certificate</span></span>  <br/> |<span data-ttu-id="ab3c7-145">這是一個標準 SSL 憑證，用於保護同盟伺服器、 同盟伺服器 proxy 與網際網路用戶端電腦之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-145">This is a standard SSL certificate that is used for securing communications between a federation server, a federation server proxy, and Internet client computers.</span></span>  <br/> |<span data-ttu-id="ab3c7-146">這個 SSL 憑證必須是繫結至 IIS 中的預設網站，才能成功執行 [AD FS 同盟伺服器 Proxy 組態精靈。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-146">This SSL certificate must be bound to the default website in IIS before you can successfully run the AD FS Federation Server Proxy Configuration wizard.</span></span>  <br/> <span data-ttu-id="ab3c7-147">此憑證必須已在公司網路中同盟伺服器設定 SSL 憑證的主體名稱相同。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-147">This certificate must have the same subject name as the SSL certificate that was configured on the federation server in the corporate network.</span></span>  <br/> <span data-ttu-id="ab3c7-148">**建議：** 我們建議您使用此同盟伺服器 proxy 所連線之同盟伺服器設定的相同伺服器驗證憑證。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-148">**Recommendation:** We recommend that you use the same server authentication certificate that is configured on the federation server that this federation server proxy connects to.</span></span>  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a><span data-ttu-id="ab3c7-149">自動探索、 Outlook 無所不在 」 及 Active Directory 同步處理的憑證</span><span class="sxs-lookup"><span data-stu-id="ab3c7-149">Certificates for Autodiscover, Outlook Anywhere, and Active Directory Synchronization</span></span>

<span data-ttu-id="ab3c7-150">您向外 Exchange 2013、 Exchange 2010、 Exchange 2007 和 Exchange 2003 用戶端存取伺服器 （凱） 需要第三方 SSL 憑證的自動探索、 Outlook Anywhere 和 Active Directory 同步處理服務的安全連線。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-150">Your external-facing Exchange 2013, Exchange 2010, Exchange 2007, and Exchange 2003 Client Access servers (CASs) require a third-party SSL certificate for secure connections for Autodiscover, Outlook Anywhere, and Active Directory synchronization services.</span></span> <span data-ttu-id="ab3c7-151">您可能已在內部部署環境中安裝此憑證。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-151">You may already have this certificate installed in your on-premises environment.</span></span>
  
## <a name="certificate-for-an-exchange-hybrid-server"></a><span data-ttu-id="ab3c7-152">Exchange 混合伺服器的憑證</span><span class="sxs-lookup"><span data-stu-id="ab3c7-152">Certificate for an Exchange Hybrid Server</span></span>

<span data-ttu-id="ab3c7-153">對外 Exchange 混合式或多部伺服器需要第三方 SSL 憑證與 Exchange Online 服務的安全連線。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-153">Your external-facing Exchange hybrid server or servers require a third-party SSL certificate for secure connectivity with the Exchange Online service.</span></span> <span data-ttu-id="ab3c7-154">您必須從您的第三方 SSL 提供者取得此憑證。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-154">You need to get this certificate from your third-party SSL provider.</span></span>
  
## <a name="office-365-certificate-chains"></a><span data-ttu-id="ab3c7-155">Office 365 的憑證鏈結</span><span class="sxs-lookup"><span data-stu-id="ab3c7-155">Office 365 Certificate Chains</span></span>

<span data-ttu-id="ab3c7-156">本文說明您可能需要在您的基礎結構上安裝的憑證。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-156">This article describes the certificates you may need to install on your infrastructure.</span></span> <span data-ttu-id="ab3c7-157">如需有關在我們的 Office 365 伺服器上已安裝的憑證的詳細資訊，請參閱 < <b0>Office 365 的憑證鏈結</b0>。</span><span class="sxs-lookup"><span data-stu-id="ab3c7-157">For more information on the certificates installed on our Office 365 servers, see [Office 365 Certificate Chains](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb).</span></span>
  

