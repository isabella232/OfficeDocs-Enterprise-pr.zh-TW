---
title: Office 365 身分識別模型和 Azure Active Directory
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
- M365-security-compliance
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: 了解如何在 Office 365 中管理使用者身分識別。
ms.openlocfilehash: cd7fb1db2d5372097f3da0e6a2521335d7933015
ms.sourcegitcommit: 47c6156c0038745103b71f44b2a3b103c62e5d6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2019
ms.locfileid: "34102456"
---
# <a name="office-365-identity-models-and-azure-active-directory"></a><span data-ttu-id="b29ad-103">Office 365 身分識別模型和 Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="b29ad-103">Office 365 identity models and Azure Active Directory</span></span>

<span data-ttu-id="b29ad-104">Office 365 使用 Azure Active Directory (Azure AD)、 隨附於 Office 365 訂閱，來管理身分識別和驗證 Office 365 雲端型使用者身分識別與驗證服務。</span><span class="sxs-lookup"><span data-stu-id="b29ad-104">Office 365 uses Azure Active Directory (Azure AD), a cloud-based user identity and authentication service that is included with your Office 365 subscription, to manage identities and authentication for Office 365.</span></span> <span data-ttu-id="b29ad-105">取得您正確設定的身分識別基礎結構是管理 Office 365 使用者存取權和權限為您的組織很重要。</span><span class="sxs-lookup"><span data-stu-id="b29ad-105">Getting your identity infrastructure configured correctly is vital to managing Office 365 user access and permissions for your organization.</span></span>

<span data-ttu-id="b29ad-106">開始之前，請觀賞這段影片的身分識別模型的概觀和 Office 365 和 Microsoft 365 的驗證。</span><span class="sxs-lookup"><span data-stu-id="b29ad-106">Before you begin, watch this video for an overview of identity models and authentication for both Office 365 and Microsoft 365.</span></span>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2Pjwu]

<span data-ttu-id="b29ad-107">Office 365 身分識別模型是您第一個的規劃選擇。</span><span class="sxs-lookup"><span data-stu-id="b29ad-107">Your first planning choice is the Office 365 identity model.</span></span>

## <a name="office-365-identity-models"></a><span data-ttu-id="b29ad-108">Office 365 身分識別模型</span><span class="sxs-lookup"><span data-stu-id="b29ad-108">Office 365 identity models</span></span>

<span data-ttu-id="b29ad-109">若要規劃使用者帳戶，必須先了解 Microsoft 365 中的兩種身分識別模型。</span><span class="sxs-lookup"><span data-stu-id="b29ad-109">To plan for user accounts, you first need to understand the two identity models in Microsoft 365.</span></span> <span data-ttu-id="b29ad-110">您可以維護貴組織的雲端設定身分識別只，或您可以維護您的內部部署 Active Directory 網域服務 (AD DS) 身分識別，並將其用於驗證的使用者存取 Microsoft 365 雲端服務時。</span><span class="sxs-lookup"><span data-stu-id="b29ad-110">You can maintain your organization's identities only in the cloud, or you can maintain your on-premises Active Directory Domain Services (AD DS) identities and use them for authentication when users access Microsoft 365 cloud services.</span></span>  

<span data-ttu-id="b29ad-111">以下是兩種類型的身分識別和其最佳配合及福利。</span><span class="sxs-lookup"><span data-stu-id="b29ad-111">Here are the two types of identity and their best fit and benefits.</span></span>

|||
|:-------|:-----|:-----|
|  | <span data-ttu-id="b29ad-112">僅限雲端身分識別</span><span class="sxs-lookup"><span data-stu-id="b29ad-112">Cloud-only identity</span></span> | <span data-ttu-id="b29ad-113">混合式身分識別</span><span class="sxs-lookup"><span data-stu-id="b29ad-113">Hybrid identity</span></span> |
| <span data-ttu-id="b29ad-114">定義</span><span class="sxs-lookup"><span data-stu-id="b29ad-114">Definition</span></span> | <span data-ttu-id="b29ad-115">使用者帳戶只存在於 Microsoft 365 訂用帳戶的 Azure Active Directory (Azure AD) 租用戶。</span><span class="sxs-lookup"><span data-stu-id="b29ad-115">User account only exists in the Azure Active Directory (Azure AD) tenant for your Microsoft 365 subscription.</span></span> | <span data-ttu-id="b29ad-116">在 AD DS 中有使用者帳戶和複本也是在您的 Microsoft 365 訂閱的 Azure AD 租用戶中。</span><span class="sxs-lookup"><span data-stu-id="b29ad-116">User account exists in AD DS and a copy is also in the Azure AD tenant for your Microsoft 365 subscription.</span></span> <span data-ttu-id="b29ad-117">在 Azure AD 中的使用者帳戶也可能包含使用者帳戶密碼雜湊的版本。</span><span class="sxs-lookup"><span data-stu-id="b29ad-117">The user account in Azure AD might also include a hashed version of the user account password.</span></span> |
| <span data-ttu-id="b29ad-118">Microsoft 365 如何驗證使用者認證</span><span class="sxs-lookup"><span data-stu-id="b29ad-118">How Microsoft 365 authenticates user credentials</span></span> | <span data-ttu-id="b29ad-119">Microsoft 365 訂用帳戶的 Azure AD 租用戶會執行與雲端身分識別帳戶驗證。</span><span class="sxs-lookup"><span data-stu-id="b29ad-119">The Azure AD tenant for your Microsoft 365 subscription performs the authentication with the cloud identity account.</span></span> | <span data-ttu-id="b29ad-120">Microsoft 365 訂用帳戶的 Azure AD 租用戶處理的驗證程序，或是將使用者重新導向至另一個身分識別提供者。</span><span class="sxs-lookup"><span data-stu-id="b29ad-120">The Azure AD tenant for your Microsoft 365 subscription either handles the authentication process or redirects the user to another identity provider.</span></span> |
| <span data-ttu-id="b29ad-121">適合...]</span><span class="sxs-lookup"><span data-stu-id="b29ad-121">Best for…</span></span> | <span data-ttu-id="b29ad-122">組織沒有或不需要內部部署 AD DS。</span><span class="sxs-lookup"><span data-stu-id="b29ad-122">Organizations that do not have or need an on-premises AD DS.</span></span> | <span data-ttu-id="b29ad-123">使用 AD DS 或另一個身分識別提供者的組織。</span><span class="sxs-lookup"><span data-stu-id="b29ad-123">Organizations using AD DS or another identity provider.</span></span> |
| <span data-ttu-id="b29ad-124">最大優點</span><span class="sxs-lookup"><span data-stu-id="b29ad-124">Greatest benefit</span></span> | <span data-ttu-id="b29ad-125">易於使用。</span><span class="sxs-lookup"><span data-stu-id="b29ad-125">Simple to use.</span></span> <span data-ttu-id="b29ad-126">沒有額外的目錄工具或所需的伺服器。</span><span class="sxs-lookup"><span data-stu-id="b29ad-126">No extra directory tools or servers required.</span></span> | <span data-ttu-id="b29ad-127">存取內部部署或雲端式資源時，使用者可以使用相同的認證。</span><span class="sxs-lookup"><span data-stu-id="b29ad-127">Users can use the same credentials when accessing on-premises or cloud-based resources.</span></span> |
||||

### <a name="cloud-only-identity"></a><span data-ttu-id="b29ad-128">僅限雲端身分識別</span><span class="sxs-lookup"><span data-stu-id="b29ad-128">Cloud-only identity</span></span>

<span data-ttu-id="b29ad-129">僅限雲端身分識別使用只能在 Azure AD 中存在的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="b29ad-129">A cloud-only identity uses user accounts that exist only in Azure AD.</span></span> <span data-ttu-id="b29ad-130">不需要在內部部署伺服器或不使用 AD DS 管理本機的身分識別的小型組織通常會使用雲端身分識別。</span><span class="sxs-lookup"><span data-stu-id="b29ad-130">Cloud identity is typically used by small organizations that do not have on-premises servers or do not use AD DS to manage local identities.</span></span> 

<span data-ttu-id="b29ad-131">以下是僅限雲端身分識別的基本元件。</span><span class="sxs-lookup"><span data-stu-id="b29ad-131">Here are the basic components of cloud-only identity.</span></span>
 
![](./media/about-office-365-identity/cloud-only-identity.png)

<span data-ttu-id="b29ad-132">在內部和遠端 （線上） 的使用者使用其 Azure AD 使用者帳戶和密碼來存取 Office 365 雲端服務。</span><span class="sxs-lookup"><span data-stu-id="b29ad-132">Both on-premises and remote (online) users use their Azure AD user accounts and passwords to access Office 365 cloud services.</span></span> <span data-ttu-id="b29ad-133">Azure AD 驗證根據其儲存的使用者帳戶和密碼的使用者認證。</span><span class="sxs-lookup"><span data-stu-id="b29ad-133">Azure AD authenticates user credentials based on its stored user accounts and passwords.</span></span>

#### <a name="administration"></a><span data-ttu-id="b29ad-134">系統管理</span><span class="sxs-lookup"><span data-stu-id="b29ad-134">Administration</span></span>
<span data-ttu-id="b29ad-135">因為使用者帳戶只會儲存在 Azure AD 中，您可以管理雲端身分識別，例如[Microsoft 365 系統管理中心](https://admin.microsoft.com)和 Windows PowerShell 與 PowerShell 的 Azure Active Directory 針對 Graph 模組的工具。</span><span class="sxs-lookup"><span data-stu-id="b29ad-135">Because user accounts are only stored in Azure AD, you manage cloud identities with tools such as the [Microsoft 365 admin center](https://admin.microsoft.com) and Windows PowerShell with the Azure Active Directory PowerShell for Graph module.</span></span> 

## <a name="hybrid-identity"></a><span data-ttu-id="b29ad-136">混合式身分識別</span><span class="sxs-lookup"><span data-stu-id="b29ad-136">Hybrid identity</span></span>

<span data-ttu-id="b29ad-137">混合式身分識別使用的帳戶，源自內部部署 AD DS 並在 Microsoft 365 訂閱下 Azure AD 租用戶中有複本。</span><span class="sxs-lookup"><span data-stu-id="b29ad-137">Hybrid identity uses accounts that originate in an on-premises AD DS and have a copy in the Azure AD tenant of a Microsoft 365 subscription.</span></span> <span data-ttu-id="b29ad-138">不過，大多數變更僅流程其中一種方式。</span><span class="sxs-lookup"><span data-stu-id="b29ad-138">However, most changes only flow one way.</span></span> <span data-ttu-id="b29ad-139">您所做變更 AD DS 使用者帳戶同步處理至其複本在 Azure AD 中。</span><span class="sxs-lookup"><span data-stu-id="b29ad-139">Changes that you make to AD DS user accounts are synchronized to their copy in Azure AD.</span></span> <span data-ttu-id="b29ad-140">但是，在 Azure AD，新的使用者帳戶，例如至雲端架構帳戶所做的變更不會與 AD DS 同步。</span><span class="sxs-lookup"><span data-stu-id="b29ad-140">But changes made to cloud-based accounts in Azure AD, such as new user accounts, are not synchronized with AD DS.</span></span>

<span data-ttu-id="b29ad-141">Azure AD Connect 提供持續的帳戶同步處理。</span><span class="sxs-lookup"><span data-stu-id="b29ad-141">Azure AD Connect provides the ongoing account synchronization.</span></span> <span data-ttu-id="b29ad-142">它會在內部部署伺服器上，檢查有變更在 AD DS 中，執行，並將這些變更轉寄到 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="b29ad-142">It runs on an on-premises server, checks for changes in the AD DS, and forwards those changes to Azure AD.</span></span> <span data-ttu-id="b29ad-143">Azure AD Connect 提供要篩選已同步處理的帳戶，以及是否要同步處理的使用者密碼，又稱為密碼雜湊同步處理 (PHS) 雜湊的版本的能力。</span><span class="sxs-lookup"><span data-stu-id="b29ad-143">Azure AD Connect provides the ability to filter which accounts are synchronized and whether to synchronize a hashed version of user passwords, known as password hash synchronization (PHS).</span></span>

<span data-ttu-id="b29ad-144">當您實作混合式身分識別，您內部部署 AD DS 是帳戶資訊的授權來源。</span><span class="sxs-lookup"><span data-stu-id="b29ad-144">When you implement hybrid identity, your on-premises AD DS is the authoritative source for account information.</span></span> <span data-ttu-id="b29ad-145">這表示您執行管理工作大部分內部，它會再同步到 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="b29ad-145">This means that you perform administration tasks mostly on-premises, which are then synchronized to Azure AD.</span></span> 

<span data-ttu-id="b29ad-146">以下是混合式身分識別的元件。</span><span class="sxs-lookup"><span data-stu-id="b29ad-146">Here are the components of hybrid identity.</span></span>

![](./media/about-office-365-identity/hybrid-identity.png)

<span data-ttu-id="b29ad-147">Azure AD 租用戶都有一份 AD DS 帳戶。</span><span class="sxs-lookup"><span data-stu-id="b29ad-147">The Azure AD tenant has a copy of the AD DS accounts.</span></span> <span data-ttu-id="b29ad-148">在此組態中，在內部和遠端使用者存取 Microsoft 365 雲端服務驗證 Azure AD rms。</span><span class="sxs-lookup"><span data-stu-id="b29ad-148">In this configuration, both on-premises and remote users accessing Microsoft 365 cloud services authenticate against Azure AD.</span></span>

>[!Note]
><span data-ttu-id="b29ad-149">您一定要使用 Azure AD Connect 同步處理的混合式身分識別的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="b29ad-149">You always need to use Azure AD Connect to synchronize user accounts for hybrid identity.</span></span> <span data-ttu-id="b29ad-150">您需要的同步處理的使用者帳戶以執行授權工作分派和群組管理、 設定權限，並包含使用者帳戶的其他管理工作的 Azure AD 中。</span><span class="sxs-lookup"><span data-stu-id="b29ad-150">You need the synchronized user accounts in Azure AD to perform license assignment and group management, configure permissions, and other administrative tasks that involve user accounts.</span></span>
>

#### <a name="administration"></a><span data-ttu-id="b29ad-151">系統管理</span><span class="sxs-lookup"><span data-stu-id="b29ad-151">Administration</span></span>

<span data-ttu-id="b29ad-152">因為原始與授權的使用者帳戶儲存在內部部署 AD DS 管理 AD DS 中，例如 [Active Directory 使用者及電腦] 工具為相同的工具與您設定身分識別。</span><span class="sxs-lookup"><span data-stu-id="b29ad-152">Because the original and authoritative user accounts are stored in the on-premises AD DS, you manage your identities with the same tools as AD DS, such as the Active Directory Users and Computers tool.</span></span> 

<span data-ttu-id="b29ad-153">您不使用 Microsoft 365 系統管理中心或 Windows PowerShell 管理 Azure AD 中的同步處理的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="b29ad-153">You don’t use the Microsoft 365 admin center or Windows PowerShell to manage synchronized user accounts in Azure AD.</span></span>


## <a name="next-step"></a><span data-ttu-id="b29ad-154">下一步</span><span class="sxs-lookup"><span data-stu-id="b29ad-154">Next step</span></span>

<span data-ttu-id="b29ad-155">如果您需要的混合式身分識別模型，請參閱[規劃您的同步處理的身分識別和驗證方法](plan-for-directory-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="b29ad-155">If you need the hybrid identity model, see [planning for your synchronized identities and authentication methods](plan-for-directory-synchronization.md).</span></span>
  

## <a name="video-training"></a><span data-ttu-id="b29ad-156">影片訓練課程</span><span class="sxs-lookup"><span data-stu-id="b29ad-156">Video training</span></span>

<span data-ttu-id="b29ad-157">請參閱影片課程[Office 365： 管理身分識別使用 Azure AD Connect](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx)，由 LinkedIn Learning 帶您。</span><span class="sxs-lookup"><span data-stu-id="b29ad-157">See the video course [Office 365: Manage Identities Using Azure AD Connect](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx), brought to you by LinkedIn Learning.</span></span>
