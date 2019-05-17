---
title: Office 365 的混合式身分識別與目錄同步處理
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: 說明 Office 365、 Active Directory 網域服務清除與 Azure Active Directory Connect 工具的目錄同步處理。
ms.openlocfilehash: 31fcd8baaccabf5d3f4f0cf47c7573c43f7cd40b
ms.sourcegitcommit: 47c6156c0038745103b71f44b2a3b103c62e5d6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2019
ms.locfileid: "34102486"
---
# <a name="hybrid-identity-and-directory-synchronization-for-office-365"></a><span data-ttu-id="32c48-103">Office 365 的混合式身分識別與目錄同步處理</span><span class="sxs-lookup"><span data-stu-id="32c48-103">Hybrid identity and directory synchronization for Office 365</span></span>

<span data-ttu-id="32c48-104">根據業務需求與技術需求，混合式身分識別模型與目錄同步處理之後會採用 Office 365 的企業客戶的常見選擇。</span><span class="sxs-lookup"><span data-stu-id="32c48-104">Depending on business needs and technical requirements, the hybrid identity model and directory synchronization is the most common choice for enterprise customers who are adopting Office 365.</span></span> <span data-ttu-id="32c48-105">目錄同步處理可讓您管理您 Active Directory 網域服務 (AD DS) 中的身分識別和所有更新將使用者帳戶、 群組及連絡人同步都處理至 Office 365 訂閱的 Azure Active Directory (Azure AD) 租用戶。</span><span class="sxs-lookup"><span data-stu-id="32c48-105">Directory synchronization allows you to manage identities in your Active Directory Domain Services (AD DS) and all updates to user accounts, groups, and contacts are synchronized to the Azure Active Directory (Azure AD) tenant of your Office 365 subscription.</span></span>


>[!Note]
><span data-ttu-id="32c48-106">第一次同步處理 AD DS 使用者帳戶，它們都不會自動指派 Office 365 授權，而無法存取 Office 365 服務，例如電子郵件。</span><span class="sxs-lookup"><span data-stu-id="32c48-106">When AD DS user accounts are synchronized for the first time, they are not automatically assigned an Office 365 license and cannot access Office 365 services, such as email.</span></span> <span data-ttu-id="32c48-107">您必須透過群組成員資格，個別或動態指派授權給這些使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="32c48-107">You must assign a license to these user accounts, either individually or dynamically through group membership.</span></span>
>

## <a name="authentication-for-hybrid-identity"></a><span data-ttu-id="32c48-108">驗證混合式身分識別</span><span class="sxs-lookup"><span data-stu-id="32c48-108">Authentication for hybrid identity</span></span>

<span data-ttu-id="32c48-109">使用混合式身分識別模型時，有兩種驗證類型：</span><span class="sxs-lookup"><span data-stu-id="32c48-109">There are two types of authentication when using the hybrid identity model:</span></span>

- <span data-ttu-id="32c48-110">管理的驗證</span><span class="sxs-lookup"><span data-stu-id="32c48-110">Managed authentication</span></span>

  <span data-ttu-id="32c48-111">Azure AD 處理的驗證程序，使用本機儲存的密碼雜湊的版本，或將認證傳送至內部軟體代理程式來驗證內部部署的 AD DS。</span><span class="sxs-lookup"><span data-stu-id="32c48-111">Azure AD handles the authentication process by using a locally stored hashed version of the password or sends the credentials to an on-premises software agent to be authenticated by the on-premises AD DS.</span></span>

- <span data-ttu-id="32c48-112">同盟的驗證</span><span class="sxs-lookup"><span data-stu-id="32c48-112">Federated authentication</span></span>

  <span data-ttu-id="32c48-113">Azure AD 會重新導向的用戶端電腦要求驗證連絡另一個身分識別提供者。</span><span class="sxs-lookup"><span data-stu-id="32c48-113">Azure AD redirects the client computer requesting authentication to contact another identity provider.</span></span>

### <a name="managed-authentication"></a><span data-ttu-id="32c48-114">管理的驗證</span><span class="sxs-lookup"><span data-stu-id="32c48-114">Managed authentication</span></span>

<span data-ttu-id="32c48-115">有兩種類型的受管理的驗證：</span><span class="sxs-lookup"><span data-stu-id="32c48-115">There are two types of managed authentication:</span></span>

- <span data-ttu-id="32c48-116">密碼雜湊同步處理 (PHS)</span><span class="sxs-lookup"><span data-stu-id="32c48-116">Password hash synchronization (PHS)</span></span>

  <span data-ttu-id="32c48-117">Azure AD 會執行本身的驗證。</span><span class="sxs-lookup"><span data-stu-id="32c48-117">Azure AD performs the authentication itself.</span></span>

- <span data-ttu-id="32c48-118">傳遞驗證 (PTA)</span><span class="sxs-lookup"><span data-stu-id="32c48-118">Pass-through authentication (PTA)</span></span>

  <span data-ttu-id="32c48-119">Azure AD 具有 AD DS 執行驗證。</span><span class="sxs-lookup"><span data-stu-id="32c48-119">Azure AD has AD DS perform the authentication.</span></span>


#### <a name="password-hash-synchronization"></a><span data-ttu-id="32c48-120">密碼雜湊同步處理</span><span class="sxs-lookup"><span data-stu-id="32c48-120">Password hash synchronization</span></span>

<span data-ttu-id="32c48-121">使用密碼雜湊同步處理 (PHS)，您可以與 Office 365 同步處理 AD DS 使用者帳戶及管理您內部使用者。</span><span class="sxs-lookup"><span data-stu-id="32c48-121">With password hash synchronization (PHS), you synchronize your AD DS user accounts with Office 365 and manage your users on-premises.</span></span> <span data-ttu-id="32c48-122">使用者密碼雜湊同步處理從 AD DS 到 Azure AD 如此，使用者擁有相同的密碼與內部及雲端中。</span><span class="sxs-lookup"><span data-stu-id="32c48-122">Hashes of user passwords are synchronized from your AD DS to Azure AD so that the users have the same password on-premises and in the cloud.</span></span> <span data-ttu-id="32c48-123">這是最簡單的方式，以啟用 Azure AD 中的 AD DS 身分識別驗證。</span><span class="sxs-lookup"><span data-stu-id="32c48-123">This is the simplest way to enable authentication for AD DS identities in Azure AD.</span></span> 

![](./media/plan-for-directory-synchronization/phs-authentication.png)

<span data-ttu-id="32c48-124">當密碼已變更，或重設為內部時，新的密碼雜湊同步處理到 Azure AD，讓您的使用者一定可以使用相同的密碼雲端資源和內部部署資源。</span><span class="sxs-lookup"><span data-stu-id="32c48-124">When passwords are changed or reset on-premises, the new password hashes are synchronized to Azure AD so that your users can always use the same password for cloud resources and on-premises resources.</span></span> <span data-ttu-id="32c48-125">使用者密碼永遠不會傳送到 Azure AD 或儲存在 Azure AD 以純文字。</span><span class="sxs-lookup"><span data-stu-id="32c48-125">The user passwords are never sent to Azure AD or stored in Azure AD in clear text.</span></span> <span data-ttu-id="32c48-126">Azure AD，例如 Identity Protection 的部分進階功能需要的 PHS 不論其選取驗證方法。</span><span class="sxs-lookup"><span data-stu-id="32c48-126">Some premium features of Azure AD, such as Identity Protection, require PHS regardless of which authentication method is selected.</span></span>
  
<span data-ttu-id="32c48-127">請參閱 <<c0>選擇 PHS了解更多。</span><span class="sxs-lookup"><span data-stu-id="32c48-127">See [choosing PHS](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) to learn more.</span></span>
  
#### <a name="pass-through-authentication"></a><span data-ttu-id="32c48-128">傳遞驗證</span><span class="sxs-lookup"><span data-stu-id="32c48-128">Pass-through authentication</span></span>

<span data-ttu-id="32c48-129">通過驗證 (PTA) 提供用來驗證使用者直接與您的 AD DS 的一或多個內部部署伺服器上執行的軟體代理程式的 Azure AD 驗證服務的簡單密碼驗證。</span><span class="sxs-lookup"><span data-stu-id="32c48-129">Pass-through authentication (PTA) provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your AD DS.</span></span> <span data-ttu-id="32c48-130">使用傳遞驗證 (PTA)，您可以與 Office 365 同步處理 AD DS 使用者帳戶及管理您內部使用者。</span><span class="sxs-lookup"><span data-stu-id="32c48-130">With pass-through authentication (PTA), you synchronize AD DS user accounts with Office 365 and manage your users on-premises.</span></span> 

![](./media/plan-for-directory-synchronization/pta-authentication.png)

<span data-ttu-id="32c48-131">PTA 可讓您的使用者登入內部部署和 Office 365 資源並使用其內部部署帳戶和密碼的應用程式。</span><span class="sxs-lookup"><span data-stu-id="32c48-131">PTA allows your users to sign in to both on-premises and Office 365 resources and applications using their on-premises account and password.</span></span> <span data-ttu-id="32c48-132">此組態會驗證使用者密碼，直接對您內部部署 AD DS，而不儲存在 Azure AD 中的密碼雜湊。</span><span class="sxs-lookup"><span data-stu-id="32c48-132">This configuration validates users passwords directly against your on-premises AD DS without storing password hashes in Azure AD.</span></span> 

<span data-ttu-id="32c48-133">PTA 也適用於組織的安全性需求來立即強制執行內部部署使用者帳戶狀態、 密碼原則和登入時間。</span><span class="sxs-lookup"><span data-stu-id="32c48-133">PTA is also for organizations with a security requirement to immediately enforce on-premises user account states, password policies, and logon hours.</span></span> 
  
<span data-ttu-id="32c48-134">請參閱 <<c0>選擇 PTA了解更多。</span><span class="sxs-lookup"><span data-stu-id="32c48-134">See [choosing PTA](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) to learn more.</span></span>
  
### <a name="federated-authentication"></a><span data-ttu-id="32c48-135">同盟的驗證</span><span class="sxs-lookup"><span data-stu-id="32c48-135">Federated authentication</span></span>

<span data-ttu-id="32c48-136">同盟的驗證是主要使用於大型企業組織更複雜的驗證需求。</span><span class="sxs-lookup"><span data-stu-id="32c48-136">Federated authentication is primarily for large enterprise organizations with more complex authentication requirements.</span></span> <span data-ttu-id="32c48-137">使用 Office 365 同步處理 AD DS 身分識別和使用者帳戶為受管理的內部部署。</span><span class="sxs-lookup"><span data-stu-id="32c48-137">AD DS identities are synchronized with Office 365 and users accounts are managed on-premises.</span></span> <span data-ttu-id="32c48-138">利用同盟驗證，使用者有相同的密碼與內部及雲端中並不需要再次登入才能使用 Office 365。</span><span class="sxs-lookup"><span data-stu-id="32c48-138">With federated authentication, users have the same password on-premises and in the cloud and they do not have to sign in again to use Office 365.</span></span> 

<span data-ttu-id="32c48-139">同盟的驗證可支援其他驗證需求，例如智慧卡型驗證或協力廠商的多重要素驗證時，則通常需要組織尚未驗證需求原生支援 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="32c48-139">Federated authentication can support additional authentication requirements, such as smartcard-based authentication or a third-party multi-factor authentication and is typically required when organizations have an authentication requirement not natively supported by Azure AD.</span></span>
 
<span data-ttu-id="32c48-140">請參閱 < 若要了解更多的 [<b0>選擇同盟的驗證</b0>。</span><span class="sxs-lookup"><span data-stu-id="32c48-140">See [choosing federated authentication](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) to learn more.</span></span>
  
#### <a name="third-party-authentication-and-identity-providers"></a><span data-ttu-id="32c48-141">協力廠商驗證與身分識別提供者</span><span class="sxs-lookup"><span data-stu-id="32c48-141">Third-party authentication and identity providers</span></span>

<span data-ttu-id="32c48-142">內部部署目錄物件可能會同步至 Office 365 和雲端資源存取主要是由協力廠商身分識別提供者 (Isp)。</span><span class="sxs-lookup"><span data-stu-id="32c48-142">On-premises directory objects may be synchronized to Office 365 and cloud resource access is primarily managed by a third-party identity provider (IdP).</span></span> <span data-ttu-id="32c48-143">如果您的組織使用同盟協力廠商解決方案，您可以設定登入與該解決方案搭配運作的 Office 365 提供協力廠商同盟解決方案會與 Azure AD 相容。</span><span class="sxs-lookup"><span data-stu-id="32c48-143">If your organization uses a third-party federation solution, you can configure sign-on with that solution for Office 365 provided that the third-party federation solution is compatible with Azure AD.</span></span>
  
<span data-ttu-id="32c48-144">若要了解更多的[Azure AD 同盟相容性](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility)，請參閱。</span><span class="sxs-lookup"><span data-stu-id="32c48-144">See [Azure AD federation compatibility](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) to learn more.</span></span>
  
## <a name="ad-ds-cleanup"></a><span data-ttu-id="32c48-145">AD DS 清理</span><span class="sxs-lookup"><span data-stu-id="32c48-145">AD DS Cleanup</span></span>

<span data-ttu-id="32c48-146">為了協助確保順暢地轉換到 Office 365 使用同步處理，您必須在 Office 365 目錄同步處理部署之前準備您的 AD DS 樹系。</span><span class="sxs-lookup"><span data-stu-id="32c48-146">To help ensure a seamless transition to Office 365 by using synchronization, you must prepare your AD DS forest before you begin your Office 365 directory synchronization deployment.</span></span>
  
<span data-ttu-id="32c48-147">當您[設定 Office 365 中的目錄同步處理](set-up-directory-synchronization.md)，其中一個步驟是[下載並執行 IdFix 工具](install-and-run-idfix.md)。</span><span class="sxs-lookup"><span data-stu-id="32c48-147">When you [set up directory synchronization in Office 365](set-up-directory-synchronization.md), one of the steps is to [download and run the IdFix tool](install-and-run-idfix.md).</span></span> <span data-ttu-id="32c48-148">您可以使用 IdFix 工具以協助進行[目錄清理](prepare-directory-attributes-for-synch-with-idfix.md)。</span><span class="sxs-lookup"><span data-stu-id="32c48-148">You can use the IdFix tool to help with [directory cleanup](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  
<span data-ttu-id="32c48-149">目錄清理應該要著重於下列工作：</span><span class="sxs-lookup"><span data-stu-id="32c48-149">Your directory cleanup should focus on the following tasks:</span></span>

- <span data-ttu-id="32c48-150">移除重複的**proxyAddress**和**userPrincipalName**屬性。</span><span class="sxs-lookup"><span data-stu-id="32c48-150">Remove duplicate **proxyAddress** and **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="32c48-151">使用有效的**userPrincipalName**屬性更新空白及無效的**userPrincipalName**屬性。</span><span class="sxs-lookup"><span data-stu-id="32c48-151">Update blank and invalid **userPrincipalName** attributes with valid **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="32c48-152">**GivenName**、 姓氏 ( **sn** )、 **sAMAccountName**、 **displayName**、**郵件**、 **proxyAddresses**、 **mailNickname**和**userPrincipalName**中移除無效，且有疑問的字元屬性。</span><span class="sxs-lookup"><span data-stu-id="32c48-152">Remove invalid and questionable characters in the **givenName**, surname ( **sn** ), **sAMAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname**, and **userPrincipalName** attributes.</span></span> <span data-ttu-id="32c48-153">如需準備屬性的詳細資訊，請參閱 <<c0>清單的屬性，會同步處理的 Azure Active Directory 同步作業工具。</span><span class="sxs-lookup"><span data-stu-id="32c48-153">For details about preparing attributes, see [List of attributes that are synced by the Azure Active Directory Sync Tool](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

    > [!NOTE]
    > <span data-ttu-id="32c48-154">這些都是相同 Azure AD Connect 同步處理的屬性。</span><span class="sxs-lookup"><span data-stu-id="32c48-154">These are the same attributes that Azure AD Connect synchronizes.</span></span> 
  
## <a name="multi-forest-deployment-considerations"></a><span data-ttu-id="32c48-155">多樹系部署考量</span><span class="sxs-lookup"><span data-stu-id="32c48-155">Multi-forest deployment considerations</span></span>

<span data-ttu-id="32c48-156">針對多個樹系與 SSO 選項，使用[自訂安裝的 Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430)。</span><span class="sxs-lookup"><span data-stu-id="32c48-156">For multiple forests and SSO options, use [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>
  
<span data-ttu-id="32c48-157">如果您的組織有多個樹系進行驗證 （登入樹系），我們強烈建議如下：</span><span class="sxs-lookup"><span data-stu-id="32c48-157">If your organization has multiple forests for authentication (logon forests), we highly recommend the following:</span></span>
  
- <span data-ttu-id="32c48-158">**請考慮將合併在樹系。**</span><span class="sxs-lookup"><span data-stu-id="32c48-158">**Consider consolidating your forests.**</span></span> <span data-ttu-id="32c48-159">一般而言，沒有更多維護多個樹系所需的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="32c48-159">In general, there's more overhead required to maintain multiple forests.</span></span> <span data-ttu-id="32c48-160">除非您的組織有安全性限制，指示不同樹系的需求，否則請簡化您的內部部署環境。</span><span class="sxs-lookup"><span data-stu-id="32c48-160">Unless your organization has security constraints that dictate the need for separate forests, consider simplifying your on-premises environment.</span></span>
- <span data-ttu-id="32c48-161">**只有在您的主要登入樹系中使用。**</span><span class="sxs-lookup"><span data-stu-id="32c48-161">**Use only in your primary logon forest.**</span></span> <span data-ttu-id="32c48-162">請考慮部署只能在您的 Office 365 在首度發行的主要登入樹系中的 Office 365。</span><span class="sxs-lookup"><span data-stu-id="32c48-162">Consider deploying Office 365 only in your primary logon forest for your initial rollout of Office 365.</span></span> 

<span data-ttu-id="32c48-163">如果您無法合併您多樹系的 AD DS 部署，或使用其他目錄服務管理身分識別，您可能無法同步處理這些 Microsoft 或合作夥伴的協助。</span><span class="sxs-lookup"><span data-stu-id="32c48-163">If you can't consolidate your multi-forest AD DS deployment or are using other directory services to manage identities, you may be able to synchronize these with the help of Microsoft or a partner.</span></span>
  
<span data-ttu-id="32c48-164">如需詳細資訊，請參閱[使用單一登入案例的多樹系目錄同步](https://go.microsoft.com/fwlink/p/?LinkId=525321)。</span><span class="sxs-lookup"><span data-stu-id="32c48-164">See [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=525321) for more information.</span></span>
  
## <a name="features-that-are-dependent-on-directory-synchronization"></a><span data-ttu-id="32c48-165">取決於目錄同步作業的功能</span><span class="sxs-lookup"><span data-stu-id="32c48-165">Features that are dependent on directory synchronization</span></span>
  
<span data-ttu-id="32c48-166">目錄同步作業所需的下列特性與功能：</span><span class="sxs-lookup"><span data-stu-id="32c48-166">Directory synchronization is required for the following features and functionality:</span></span>
  
- <span data-ttu-id="32c48-167">Azure AD 無縫單一登入 (SSO)</span><span class="sxs-lookup"><span data-stu-id="32c48-167">Azure AD Seamless Single Sign-On (SSO)</span></span>
- <span data-ttu-id="32c48-168">Skype 共存</span><span class="sxs-lookup"><span data-stu-id="32c48-168">Skype coexistence</span></span>
- <span data-ttu-id="32c48-169">Exchange 混合式部署，包括：</span><span class="sxs-lookup"><span data-stu-id="32c48-169">Exchange hybrid deployment, including:</span></span>
  - <span data-ttu-id="32c48-170">您在內部部署 Exchange 環境與 Office 365 之間的完全共用全域通訊清單 (GAL)。</span><span class="sxs-lookup"><span data-stu-id="32c48-170">Fully shared global address list (GAL) between your on-premises Exchange environment and Office 365.</span></span>
  - <span data-ttu-id="32c48-171">從不同的郵件系統的同步處理 GAL 資訊。</span><span class="sxs-lookup"><span data-stu-id="32c48-171">Synchronizing GAL information from different mail systems.</span></span>
  - <span data-ttu-id="32c48-172">將使用者加入及移除使用者從 Office 365 服務方案的能力。</span><span class="sxs-lookup"><span data-stu-id="32c48-172">The ability to add users to and remove users from Office 365 service offerings.</span></span> <span data-ttu-id="32c48-173">這需要下列項目：</span><span class="sxs-lookup"><span data-stu-id="32c48-173">This requires the following:</span></span>
  - <span data-ttu-id="32c48-174">目錄同步處理安裝期間，必須設定雙向同步處理。</span><span class="sxs-lookup"><span data-stu-id="32c48-174">Two-way synchronization must be configured during directory synchronization setup.</span></span> <span data-ttu-id="32c48-175">根據預設，目錄同步處理工具的目錄資訊寫入僅雲端。</span><span class="sxs-lookup"><span data-stu-id="32c48-175">By default, directory synchronization tools write directory information only to the cloud.</span></span> <span data-ttu-id="32c48-176">當您設定雙向同步處理時，以便有限的數量的物件的屬性會複製從雲端，並覆寫這些回本機的 AD DS 啟用回寫功能。</span><span class="sxs-lookup"><span data-stu-id="32c48-176">When you configure two-way synchronization, you enable write-back functionality so that a limited number of object attributes are copied from the cloud, and then written them back to your local AD DS.</span></span> <span data-ttu-id="32c48-177">回寫也稱為 Exchange 混合式模式。</span><span class="sxs-lookup"><span data-stu-id="32c48-177">Write-back is also referred to as Exchange hybrid mode.</span></span> 
  - <span data-ttu-id="32c48-178">內部部署 Exchange 混合式部署</span><span class="sxs-lookup"><span data-stu-id="32c48-178">An on-premises Exchange hybrid deployment</span></span>
  - <span data-ttu-id="32c48-179">在保留其他使用者信箱在內部將部分使用者信箱移至 Office 365 功能。</span><span class="sxs-lookup"><span data-stu-id="32c48-179">The ability to move some user mailboxes to Office 365 while keeping other user mailboxes on-premises.</span></span>
  - <span data-ttu-id="32c48-180">安全的寄件者和封鎖寄件者的內部會複寫至 Office 365。</span><span class="sxs-lookup"><span data-stu-id="32c48-180">Safe senders and blocked senders on-premises are replicated to Office 365.</span></span>
  - <span data-ttu-id="32c48-181">基本委派及代理傳送的電子郵件功能。</span><span class="sxs-lookup"><span data-stu-id="32c48-181">Basic delegation and send-on-behalf-of email functionality.</span></span>
  - <span data-ttu-id="32c48-182">您有內部整合式的智慧卡或多重要素驗證方案。</span><span class="sxs-lookup"><span data-stu-id="32c48-182">You have an integrated on-premises smart card or multi-factor authentication solution.</span></span>
- <span data-ttu-id="32c48-183">相片、 縮圖、 會議室及安全性群組同步處理</span><span class="sxs-lookup"><span data-stu-id="32c48-183">Synchronization of photos, thumbnails, conference rooms, and security groups</span></span>

## <a name="next-step"></a><span data-ttu-id="32c48-184">下一步</span><span class="sxs-lookup"><span data-stu-id="32c48-184">Next step</span></span>

<span data-ttu-id="32c48-185">當您準備好要部署混合式身分識別時，請參閱 <<c0>準備佈建使用者。</span><span class="sxs-lookup"><span data-stu-id="32c48-185">When you are ready to deploy hybrid identity, see [prepare to provision users](prepare-for-directory-synchronization.md).</span></span>
  

