---
title: Contoso Corporation 的安全性
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 8f6f9894-5394-4110-8b0a-b8765028c10b
description: 摘要： 了解如何 Contoso 其安全性需求對應至 Microsoft cloud 方案中的功能和取決於雲端安全性整備的路徑。
ms.openlocfilehash: 722c01995c95c36b9975b0682858c38063f79d2c
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914828"
---
# <a name="security-for-the-contoso-corporation"></a><span data-ttu-id="df5aa-103">Contoso Corporation 的安全性</span><span class="sxs-lookup"><span data-stu-id="df5aa-103">Security for the Contoso Corporation</span></span>

 <span data-ttu-id="df5aa-104">**摘要：** 了解如何 Contoso 其安全性需求對應至 Microsoft cloud 方案中的功能和取決於雲端安全性整備的路徑。</span><span class="sxs-lookup"><span data-stu-id="df5aa-104">**Summary:** Understand how Contoso mapped their security requirements to features in Microsoft's cloud offerings and determined a path to cloud security readiness.</span></span>
  
<span data-ttu-id="df5aa-p101">Contoso 是嚴重其資訊安全性和保護相關。轉換至雲端內含一個其 IT 基礎結構，他們進行確認其內部安全性需求所支援及 Microsoft cloud 方案中實作。</span><span class="sxs-lookup"><span data-stu-id="df5aa-p101">Contoso is serious about their information security and protection. When transitioning their IT infrastructure to a cloud-inclusive one, they made sure that their on-premises security requirements were supported and implemented in Microsoft's cloud offerings.</span></span>
  
## <a name="contosos-security-requirements-in-the-cloud"></a><span data-ttu-id="df5aa-107">在雲端 Contoso 的安全性需求</span><span class="sxs-lookup"><span data-stu-id="df5aa-107">Contoso's security requirements in the cloud</span></span>

<span data-ttu-id="df5aa-108">以下是雲端 Contoso 的安全性需求：</span><span class="sxs-lookup"><span data-stu-id="df5aa-108">Here are Contoso's security requirements for the cloud:</span></span>
  
- <span data-ttu-id="df5aa-109">對雲端資源的強式驗證</span><span class="sxs-lookup"><span data-stu-id="df5aa-109">Strong authentication to cloud resources</span></span>
    
    <span data-ttu-id="df5aa-110">雲端資源存取必須獲得驗證，請儘可能運用多重要素驗證。</span><span class="sxs-lookup"><span data-stu-id="df5aa-110">Cloud resource access must be authenticated and, where possible, leverage multi-factor authentication.</span></span>
    
- <span data-ttu-id="df5aa-111">經由網際網路的流量的加密</span><span class="sxs-lookup"><span data-stu-id="df5aa-111">Encryption for traffic across the Internet</span></span>
    
    <span data-ttu-id="df5aa-p102">經由網際網路傳送不含資料是純文字格式。一律使用 HTTPS 連線、 IPsec 或其他端對端資料加密方法。</span><span class="sxs-lookup"><span data-stu-id="df5aa-p102">No data sent across the Internet is in plain text form. Always use HTTPS connections, IPsec, or other end-to-end data encryption methods.</span></span>
    
- <span data-ttu-id="df5aa-114">在雲端中的靜態資料的加密</span><span class="sxs-lookup"><span data-stu-id="df5aa-114">Encryption for data at rest in the cloud</span></span>
    
    <span data-ttu-id="df5aa-115">加密的格式必須是儲存在磁碟上或其他地方雲端中的所有資料。</span><span class="sxs-lookup"><span data-stu-id="df5aa-115">All data stored on disks or elsewhere in the cloud must be in an encrypted form.</span></span>
    
- <span data-ttu-id="df5aa-116">Acl 的最低權限存取</span><span class="sxs-lookup"><span data-stu-id="df5aa-116">ACLs for least privilege access</span></span>
    
    <span data-ttu-id="df5aa-117">帳戶權限存取雲端中的資源與允許執行必須遵循最低指導方針。</span><span class="sxs-lookup"><span data-stu-id="df5aa-117">Account permissions to access resources in the cloud and what they are allowed to do must follow least-privilege guidelines.</span></span>
    
## <a name="contosos-data-sensitivity-classification"></a><span data-ttu-id="df5aa-118">Contoso 的資料敏感度分類</span><span class="sxs-lookup"><span data-stu-id="df5aa-118">Contoso's data sensitivity classification</span></span>

<span data-ttu-id="df5aa-119">使用 Microsoft 的[資料分類 Toolkit](https://msdn.microsoft.com/library/hh204743.aspx)中的資訊，Contoso 執行其資料分析與取決於下列層級。</span><span class="sxs-lookup"><span data-stu-id="df5aa-119">Using the information in Microsoft's [Data Classification Toolkit](https://msdn.microsoft.com/library/hh204743.aspx), Contoso performed an analysis of their data and determined the following levels.</span></span>
  
|<span data-ttu-id="df5aa-120">**層級 1： 低商業價值**</span><span class="sxs-lookup"><span data-stu-id="df5aa-120">**Level 1: Low business value**</span></span>|<span data-ttu-id="df5aa-121">**層級 2： 中型企業價值**</span><span class="sxs-lookup"><span data-stu-id="df5aa-121">**Level 2: Medium business value**</span></span>|<span data-ttu-id="df5aa-122">**層級 3： 高商業價值**</span><span class="sxs-lookup"><span data-stu-id="df5aa-122">**Level 3: High business value**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="df5aa-123">資料會加密，僅適用於已驗證的使用者</span><span class="sxs-lookup"><span data-stu-id="df5aa-123">Data is encrypted and available only to authenticated users</span></span>  <br/> <span data-ttu-id="df5aa-p103">提供在內部部署和雲端儲存空間和工作量，例如 Office 365 中所儲存的所有資料。當它所在服務中與傳輸服務與用戶端裝置之間的資料會經過加密。</span><span class="sxs-lookup"><span data-stu-id="df5aa-p103">Provided for all data stored on premises and in cloud-based storage and workloads, such as Office 365. Data is encrypted while it resides in the service and in transit between the service and client devices.</span></span>  <br/> <span data-ttu-id="df5aa-126">層級 1 資料的範例是一般商務通訊 (email) 和檔案系統管理、 銷售和支援工作者。</span><span class="sxs-lookup"><span data-stu-id="df5aa-126">Examples of Level 1 data are normal business communications (email) and files for administrative, sales, and support workers.</span></span>  <br/> |<span data-ttu-id="df5aa-127">層級 1 加上強式驗證與資料遺失保護</span><span class="sxs-lookup"><span data-stu-id="df5aa-127">Level 1 plus strong authentication and data loss protection</span></span>  <br/> <span data-ttu-id="df5aa-p104">強式驗證包含 SMS 驗證的多重要素驗證。資料外洩防護可確保機密或關鍵資訊不會不旅行社內部網路之外。</span><span class="sxs-lookup"><span data-stu-id="df5aa-p104">Strong authentication includes multi-factor authentication with SMS validation. Data loss prevention ensures that sensitive or critical information does not travel outside the on-premises network.</span></span>  <br/> <span data-ttu-id="df5aa-130">層級 2 資料的範例是財務和法律資訊及參考資料與開發的新產品的資料。</span><span class="sxs-lookup"><span data-stu-id="df5aa-130">Examples of Level 2 data are financial and legal information and research and development data for new products.</span></span>  <br/> |<span data-ttu-id="df5aa-131">層級 2 加上最高層級的加密、 驗證及稽核</span><span class="sxs-lookup"><span data-stu-id="df5aa-131">Level 2 plus the highest levels of encryption, authentication, and auditing</span></span>  <br/> <span data-ttu-id="df5aa-132">最高層級的加密資料靜態與雲端中，區域法規符合結合使用智慧卡及更精細稽核與警示的多重要素驗證。</span><span class="sxs-lookup"><span data-stu-id="df5aa-132">The highest levels of encryption for data at rest and in the cloud, compliant with regional regulations, combined with multi-factor authentication with smart cards and granular auditing and alerting.</span></span>  <br/> <span data-ttu-id="df5aa-133">層級 3 資料的範例是客戶與合作夥伴的個人識別資訊及產品工程規格與專屬製造流程技術 （英文）。</span><span class="sxs-lookup"><span data-stu-id="df5aa-133">Examples of Level 3 data are customer and partner personally identifiable information and product engineering specifications and proprietary manufacturing techniques.</span></span>  <br/> |
   
## <a name="mapping-microsoft-cloud-offerings-and-features-to-contosos-data-levels"></a><span data-ttu-id="df5aa-134">對應至 Contoso 的資料層級的 Microsoft cloud 方案和功能</span><span class="sxs-lookup"><span data-stu-id="df5aa-134">Mapping Microsoft cloud offerings and features to Contoso's data levels</span></span>

<span data-ttu-id="df5aa-135">下表顯示 Microsoft cloud 版方案的 Contoso 的資料層級功能對應：</span><span class="sxs-lookup"><span data-stu-id="df5aa-135">The following table shows the mapping of Contoso's data levels to features in Microsoft's cloud offerings:</span></span>
  
||<span data-ttu-id="df5aa-136">**Saas 和**</span><span class="sxs-lookup"><span data-stu-id="df5aa-136">**SaaS**</span></span>|<span data-ttu-id="df5aa-137">**Azure PaaS**</span><span class="sxs-lookup"><span data-stu-id="df5aa-137">**Azure PaaS**</span></span>|<span data-ttu-id="df5aa-138">**Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="df5aa-138">**Azure IaaS**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="df5aa-139">層級 1： 低商業價值</span><span class="sxs-lookup"><span data-stu-id="df5aa-139">Level 1: Low business value</span></span>  <br/> | <span data-ttu-id="df5aa-140">所有連線的 HTTPS</span><span class="sxs-lookup"><span data-stu-id="df5aa-140">HTTPS for all connections</span></span> <br/>  <span data-ttu-id="df5aa-141">靜態加密</span><span class="sxs-lookup"><span data-stu-id="df5aa-141">Encryption at rest</span></span> <br/> | <span data-ttu-id="df5aa-142">只支援 HTTPS 連線</span><span class="sxs-lookup"><span data-stu-id="df5aa-142">Support only HTTPS connections</span></span> <br/>  <span data-ttu-id="df5aa-143">加密儲存在 Azure 中的檔案</span><span class="sxs-lookup"><span data-stu-id="df5aa-143">Encrypt files stored in Azure</span></span> <br/> | <span data-ttu-id="df5aa-144">需要 HTTPS 或 IPsec 伺服器存取權</span><span class="sxs-lookup"><span data-stu-id="df5aa-144">Require HTTPS or IPsec for server access</span></span> <br/>  <span data-ttu-id="df5aa-145">Azure 磁碟加密</span><span class="sxs-lookup"><span data-stu-id="df5aa-145">Azure disk encryption</span></span> <br/> |
|<span data-ttu-id="df5aa-146">層級 2： 中型企業價值</span><span class="sxs-lookup"><span data-stu-id="df5aa-146">Level 2: Medium business value</span></span>  <br/> | <span data-ttu-id="df5aa-147">含 SMS 的 azure AD 多重要素驗證 (MFA)</span><span class="sxs-lookup"><span data-stu-id="df5aa-147">Azure AD multi-factor authentication (MFA) with SMS</span></span> <br/> | <span data-ttu-id="df5aa-148">使用 Azure 機碼存放庫的加密金鑰</span><span class="sxs-lookup"><span data-stu-id="df5aa-148">Use Azure Key Vault for encryption keys</span></span> <br/>  <span data-ttu-id="df5aa-149">含 SMS 的 azure AD MFA</span><span class="sxs-lookup"><span data-stu-id="df5aa-149">Azure AD MFA with SMS</span></span> <br/> | <span data-ttu-id="df5aa-150">含 SMS 的 MFA</span><span class="sxs-lookup"><span data-stu-id="df5aa-150">MFA with SMS</span></span> <br/> |
|<span data-ttu-id="df5aa-151">層級 3： 高商業價值</span><span class="sxs-lookup"><span data-stu-id="df5aa-151">Level 3: High business value</span></span>  <br/> | <span data-ttu-id="df5aa-152">Azure 版權管理系統 (RMS)</span><span class="sxs-lookup"><span data-stu-id="df5aa-152">Azure Rights Management System (RMS)</span></span> <br/>  <span data-ttu-id="df5aa-153">Azure AD MFA 智慧卡</span><span class="sxs-lookup"><span data-stu-id="df5aa-153">Azure AD MFA with smart cards</span></span> <br/>  <span data-ttu-id="df5aa-154">Intune 條件式存取</span><span class="sxs-lookup"><span data-stu-id="df5aa-154">Intune conditional access</span></span> <br/> | <span data-ttu-id="df5aa-155">Azure RMS</span><span class="sxs-lookup"><span data-stu-id="df5aa-155">Azure RMS</span></span> <br/>  <span data-ttu-id="df5aa-156">Azure AD MFA 智慧卡</span><span class="sxs-lookup"><span data-stu-id="df5aa-156">Azure AD MFA with smart cards</span></span> <br/> | <span data-ttu-id="df5aa-157">使用智慧卡 MFA</span><span class="sxs-lookup"><span data-stu-id="df5aa-157">MFA with smart cards</span></span> <br/> |
   
## <a name="contosos-information-policies"></a><span data-ttu-id="df5aa-158">Contoso 的資訊原則</span><span class="sxs-lookup"><span data-stu-id="df5aa-158">Contoso's information policies</span></span>

<span data-ttu-id="df5aa-159">下表列出 Contoso 的資訊原則。</span><span class="sxs-lookup"><span data-stu-id="df5aa-159">The following table lists Contoso's information policies.</span></span>
  
||<span data-ttu-id="df5aa-160">**Access**</span><span class="sxs-lookup"><span data-stu-id="df5aa-160">**Access**</span></span>|<span data-ttu-id="df5aa-161">**資料保留**</span><span class="sxs-lookup"><span data-stu-id="df5aa-161">**Data retention**</span></span>|<span data-ttu-id="df5aa-162">**資訊保護**</span><span class="sxs-lookup"><span data-stu-id="df5aa-162">**Information protection**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="df5aa-163">層級 1： 低商業價值</span><span class="sxs-lookup"><span data-stu-id="df5aa-163">Level 1: Low business value</span></span>  <br/> | <span data-ttu-id="df5aa-164">允許所有的存取權</span><span class="sxs-lookup"><span data-stu-id="df5aa-164">Allow access to all</span></span> <br/> |<span data-ttu-id="df5aa-165">6 個月</span><span class="sxs-lookup"><span data-stu-id="df5aa-165">6 months</span></span>  <br/> |<span data-ttu-id="df5aa-166">使用加密</span><span class="sxs-lookup"><span data-stu-id="df5aa-166">Use encryption</span></span>  <br/> |
|<span data-ttu-id="df5aa-167">層級 2： 中型企業價值</span><span class="sxs-lookup"><span data-stu-id="df5aa-167">Level 2: Medium business value</span></span>  <br/> | <span data-ttu-id="df5aa-168">允許存取 Contoso 員工、 承包商，與協力廠商</span><span class="sxs-lookup"><span data-stu-id="df5aa-168">Allow access to Contoso employees, subcontractors, and partners</span></span> <br/>  <span data-ttu-id="df5aa-169">使用 MFA]、 [TLS] 和 [MAM</span><span class="sxs-lookup"><span data-stu-id="df5aa-169">Use MFA, TLS, and MAM</span></span> <br/> |<span data-ttu-id="df5aa-170">2 年</span><span class="sxs-lookup"><span data-stu-id="df5aa-170">2 years</span></span>  <br/> |<span data-ttu-id="df5aa-171">使用雜湊值的資料完整性</span><span class="sxs-lookup"><span data-stu-id="df5aa-171">Use hash values for data integrity</span></span>  <br/> |
|<span data-ttu-id="df5aa-172">層級 3： 高商業價值</span><span class="sxs-lookup"><span data-stu-id="df5aa-172">Level 3: High business value</span></span>  <br/> | <span data-ttu-id="df5aa-173">允許行政人員及引進工程和製造流程存取權</span><span class="sxs-lookup"><span data-stu-id="df5aa-173">Allow access to executives and leads in engineering and manufacturing</span></span> <br/>  <span data-ttu-id="df5aa-174">僅限受管理的網路裝置與 RMS</span><span class="sxs-lookup"><span data-stu-id="df5aa-174">RMS with managed network devices only</span></span> <br/> |<span data-ttu-id="df5aa-175">7 年</span><span class="sxs-lookup"><span data-stu-id="df5aa-175">7 years</span></span>  <br/> |<span data-ttu-id="df5aa-176">用於不可否認性的數位簽章</span><span class="sxs-lookup"><span data-stu-id="df5aa-176">Use digital signatures for non-repudiation</span></span>  <br/> |
   
## <a name="contosos-path-to-cloud-security-readiness"></a><span data-ttu-id="df5aa-177">雲端安全性整備 Contoso 的路徑</span><span class="sxs-lookup"><span data-stu-id="df5aa-177">Contoso's path to cloud security readiness</span></span>

<span data-ttu-id="df5aa-178">Contoso 以備妥 Microsoft cloud 其安全性使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="df5aa-178">Contoso used the following steps to ready their security for the Microsoft cloud:</span></span>
  
1. <span data-ttu-id="df5aa-179">最佳化雲端的系統管理員帳戶</span><span class="sxs-lookup"><span data-stu-id="df5aa-179">Optimize administrator accounts for the cloud</span></span>
    
    <span data-ttu-id="df5aa-180">Contoso 未現有的 Windows Server AD 管理員帳戶廣泛檢閱，and set up 一系列的雲端系統管理員帳戶和群組。</span><span class="sxs-lookup"><span data-stu-id="df5aa-180">Contoso did an extensive review of the existing Windows Server AD administrator accounts and set up a series of cloud administrator accounts and groups.</span></span>
    
2. <span data-ttu-id="df5aa-181">將三個層級執行資料分類分析</span><span class="sxs-lookup"><span data-stu-id="df5aa-181">Perform data classification analysis into three levels</span></span>
    
    <span data-ttu-id="df5aa-182">Contoso 執行小心檢閱並決定三層是用來決定 Microsoft cloud 提供功能來保護 Contoso 的最有價值的資料。</span><span class="sxs-lookup"><span data-stu-id="df5aa-182">Contoso performed a careful review and determined the three levels, which was used to determine the Microsoft cloud offering features to protect Contoso's most valuable data.</span></span>
    
3. <span data-ttu-id="df5aa-183">決定資料層級的存取、 保留和資訊保護原則</span><span class="sxs-lookup"><span data-stu-id="df5aa-183">Determine access, retention, and information protection policies for data levels</span></span>
    
    <span data-ttu-id="df5aa-184">根據資料層級，Contoso 取決於將用來限定未來要移至雲端的 IT 工作量的詳細的需求。</span><span class="sxs-lookup"><span data-stu-id="df5aa-184">Based on the data levels, Contoso determined detailed requirements, which will be used to qualify future IT workloads being moved to the cloud.</span></span>
    
## <a name="contosos-use-of-office-365-security-best-practices"></a><span data-ttu-id="df5aa-185">Contoso 的使用的 Office 365 安全性的最佳作法</span><span class="sxs-lookup"><span data-stu-id="df5aa-185">Contoso's use of Office 365 security best practices</span></span>

<span data-ttu-id="df5aa-186">符合 Office 365 安全性最佳作法，Contoso 的安全性管理員及 IT 部門已部署下列：</span><span class="sxs-lookup"><span data-stu-id="df5aa-186">In accordance with Office 365 security best practices, Contoso's security administrators and IT department have deployed the following:</span></span>
  
- <span data-ttu-id="df5aa-187">**專用非常強式密碼全域管理員帳戶**</span><span class="sxs-lookup"><span data-stu-id="df5aa-187">**Dedicated global administrator accounts with very strong passwords**</span></span>
    
    <span data-ttu-id="df5aa-p105">而是比指派全域管理員角色日常的使用者帳戶，Contoso 已建立三個，專用全域管理員帳戶具有極強式密碼。特定管理工作的僅限完成簽署以全域管理員帳戶及密碼只已知至指定的人員。Contoso 的安全性管理員已指派給所適用於該 IT 人員的工作函數與責任帳戶的系統管理員角色。</span><span class="sxs-lookup"><span data-stu-id="df5aa-p105">Rather than assign the global admin role to everyday user accounts, Contoso has create three, dedicated global administrator accounts with very strong passwords. Signing in with a global administrator account is only done for specific administrative tasks and the passwords are only known to designated staff. Contoso's security administrators have assigned admin roles to accounts that are appropriate to that IT person's job function and responsibility.</span></span>
    
    <span data-ttu-id="df5aa-191">如需詳細資訊，請參閱 ＜[關於 Office 365 系統管理員角色](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)。</span><span class="sxs-lookup"><span data-stu-id="df5aa-191">For more information, see [About Office 365 admin roles](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span>
    
- <span data-ttu-id="df5aa-192">**重要的使用者帳戶的多重要素驗證 (MFA)**</span><span class="sxs-lookup"><span data-stu-id="df5aa-192">**Multi-factor authentication (MFA) for important user accounts**</span></span>
    
    <span data-ttu-id="df5aa-p106">MFA 要求使用者確認電話、 文字訊息或應用程式通知他們的智慧型手機上正確地輸入密碼之後，登入程序新增額外的保護層級。MFA，與 Office 365 使用者帳戶受到對抗未經授權登入即使危害帳戶密碼。</span><span class="sxs-lookup"><span data-stu-id="df5aa-p106">MFA adds an additional layer of protection to the sign-in process by requiring users to acknowledge a phone call, text message, or an app notification on their smart phone after correctly entering their password. With MFA, Office 365 user accounts are protected against unauthorized sign-in even if an account password is compromised.</span></span>
    
  - <span data-ttu-id="df5aa-195">若要保護的 Office 365 訂閱危害，Contoso 啟用 MFA 所有三個全域管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="df5aa-195">To protect against a compromise of the Office 365 subscription, Contoso enabled MFA on all three global administrator accounts.</span></span>
    
  - <span data-ttu-id="df5aa-196">網路釣魚攻擊攻擊者危及受信任的人員在組織中的認證並傳送惡意的電子郵件保護 Contoso MFA 上啟用所有使用者帳戶的管理員、 包括高階主管人員。</span><span class="sxs-lookup"><span data-stu-id="df5aa-196">To protect against phishing attacks, in which an attacker compromises the credentials of a trusted person in the organization and sends malicious emails, Contoso enabled MFA on all user accounts for managers, including the executive staff.</span></span>
    
    <span data-ttu-id="df5aa-197">如需詳細資訊，請參閱 ＜ [Plan for Office 365 部署的多重要素驗證](https://support.office.com/article/Plan-for-multifactor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)</span><span class="sxs-lookup"><span data-stu-id="df5aa-197">For more information, see [Plan for multi-factor authentication for Office 365 Deployments](https://support.office.com/article/Plan-for-multifactor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)</span></span>
    
- <span data-ttu-id="df5aa-198">**進階的安全性管理 (ASM)**</span><span class="sxs-lookup"><span data-stu-id="df5aa-198">**Advanced Security Management (ASM)**</span></span>
    
    <span data-ttu-id="df5aa-p107">ASM 使用設定的原則，以監視異常活動。It 專業人員適用的不尋常或 risky 使用者活動，例如下載大量的資料、 通知設定提醒與 ASM Contoso 安全性管理員多無法登入嘗試次數或從未知或危險的 IP 位址的登入</span><span class="sxs-lookup"><span data-stu-id="df5aa-p107">ASM uses configured policies to monitor for anomalous activity. Contoso security administrators set up alerts with ASM so that IT administrators are notified of unusual or risky user activity, such as downloading large amounts of data, multiple failed sign-in attempts, or sign-ins from unknown or dangerous IP addresses</span></span>
    
    <span data-ttu-id="df5aa-201">如需詳細資訊，請參閱[概觀 （英文） 的進階安全性管理 Office 365 中](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)。</span><span class="sxs-lookup"><span data-stu-id="df5aa-201">For more information, see [Overview of Advanced Security Management in Office 365 ](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span></span>
    
- <span data-ttu-id="df5aa-202">**安全的電子郵件流程及信箱稽核記錄**</span><span class="sxs-lookup"><span data-stu-id="df5aa-202">**Secure email flow and mailbox audit logging**</span></span>
    
    <span data-ttu-id="df5aa-p108">Contoso 安全性專家使用 Exchange Online Protection 和進階威脅保護 (ATP) 以防止未知的惡意程式碼、 病毒和惡意透過電子郵件傳輸的 Url。Contoso 也有已啟用的信箱稽核記錄來決定誰登入使用者信箱，傳送訊息和其他信箱擁有者、 委派的使用者或系統管理員所執行的活動。</span><span class="sxs-lookup"><span data-stu-id="df5aa-p108">Contoso security specialists are using Exchange Online Protection and Advanced Threat Protection (ATP) to protect against unknown malware, viruses, and malicious URLs transmitted through emails. Contoso has also enabled mailbox audit logging to determine who has logged into user mailboxes, sent messages, and other activities performed by the mailbox owner, a delegated user, or an administrator.</span></span>
    
    <span data-ttu-id="df5aa-205">如需詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="df5aa-205">For more information, see:</span></span> 
    
  - [<span data-ttu-id="df5aa-206">Office 365 電子郵件反垃圾郵件保護</span><span class="sxs-lookup"><span data-stu-id="df5aa-206">Office 365 Email Anti-Spam Protection</span></span>](https://support.office.com/article/Office-365-Email-AntiSpam-Protection-6a601501-a6a8-4559-b2e7-56b59c96a586)
    
  - [<span data-ttu-id="df5aa-207">安全附件和安全連結的進階威脅防護</span><span class="sxs-lookup"><span data-stu-id="df5aa-207">Advanced threat protection for safe attachments and safe links</span></span>](https://technet.microsoft.com/library/mt148491.aspx)
    
  - [<span data-ttu-id="df5aa-208">啟用 Office 365中的信箱稽核</span><span class="sxs-lookup"><span data-stu-id="df5aa-208">Enable mailbox auditing in Office 365</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=626109)
    
- <span data-ttu-id="df5aa-209">**資料外洩防護 (DLP)**</span><span class="sxs-lookup"><span data-stu-id="df5aa-209">**Data Loss Prevention (DLP)**</span></span>
    
    <span data-ttu-id="df5aa-210">Contoso 已識別出其機密資料並設定 DLP 原則的 Exchange Online、 SharePoint Online 和 OneDrive 以協助防止使用者有意或無意之間共用資料。</span><span class="sxs-lookup"><span data-stu-id="df5aa-210">Contoso has identified its sensitive data and configured DLP policies for Exchange Online, SharePoint Online, and OneDrive to help prevent users from accidentally or intentionally sharing the data.</span></span> 
    
    <span data-ttu-id="df5aa-211">如需詳細資訊，請參閱[資料外洩防護原則概觀](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e)。</span><span class="sxs-lookup"><span data-stu-id="df5aa-211">For more information, see [Overview of data loss prevention policies](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e).</span></span>
    
## <a name="see-also"></a><span data-ttu-id="df5aa-212">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df5aa-212">See Also</span></span>

[<span data-ttu-id="df5aa-213">Microsoft 雲端中的 Contoso</span><span class="sxs-lookup"><span data-stu-id="df5aa-213">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="df5aa-214">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="df5aa-214">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="df5aa-215">Microsoft 的 Enterprise Cloud 藍圖：IT 決策者的資源</span><span class="sxs-lookup"><span data-stu-id="df5aa-215">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)
  
[<span data-ttu-id="df5aa-216">Office 365 的安全性最佳做法</span><span class="sxs-lookup"><span data-stu-id="df5aa-216">Security best practices for Office 365</span></span>](https://support.office.com/article/Security-best-practices-for-Office-365-9295e396-e53d-49b9-ae9b-0b5828cdedc3)




