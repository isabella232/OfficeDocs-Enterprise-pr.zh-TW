---
title: 了解 Office 365 身分識別和 Azure Active Directory
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: 了解如何在 Office 365 中管理使用者身分識別。
ms.openlocfilehash: 14d1ec8a3ebc4620a72f831c0ec80253f7b3072c
ms.sourcegitcommit: dcb57859ad40090cf70586ac350472eb0fc8d9c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2018
ms.locfileid: "25639632"
---
# <a name="understanding-office-365-identity-and-azure-active-directory"></a><span data-ttu-id="eccf8-103">了解 Office 365 身分識別和 Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="eccf8-103">Understanding Office 365 identity and Azure Active Directory</span></span>

<span data-ttu-id="eccf8-p101">Office 365 管理使用者使用的雲端使用者身分識別與驗證服務 Azure Active Directory (Azure AD)。選擇的身分識別管理設定內部部署組織與 Office 365 之間是其中一個雲端基礎結構的基礎早期決策。因為變更此設定稍後可能很難，所以請謹慎考慮選項以判斷什麼最適用於您組織的需求。您可以選擇設定及管理使用者帳戶 ； 在 Office 365 中的兩個主要的驗證模型**雲端驗證**和**同盟的驗證**。</span><span class="sxs-lookup"><span data-stu-id="eccf8-p101">Office 365 uses the cloud-based user identity and authentication service Azure Active Directory (Azure AD) to manage users. Choosing if identity management is configured between your on-premises organization and Office 365 is an early decision that is one of the foundations of your cloud infrastructure. Because changing this configuration later can be difficult, carefully consider the options to determine what works best for the needs of your organization. You can choose from two main authentication models in Office 365 to set up and manage user accounts; **cloud authentication** and **federated authentication**.</span></span>
  
<span data-ttu-id="eccf8-p102">很重要謹慎考慮其中一種驗證及身分識別的模型以用來取得及執行。思考時間、 現有複雜度和成本實作及維護每個驗證及身分識別選項。這些因素之差異的每一個組織;與您應了解您想要使用您的部署的重要概念的身分識別選項可協助您選擇的驗證及身分識別模型。</span><span class="sxs-lookup"><span data-stu-id="eccf8-p102">It's important to carefully consider which of these authentication and identity models to use to get up and running. Think about the time, existing complexity, and cost to implement and maintain each of the authentication and identity options. These factors are different for every organization; and you should understand the key concepts for the identity options to help you choose the authentication and identity model you want to use for your deployment.</span></span>
  
## <a name="cloud-authentication"></a><span data-ttu-id="eccf8-111">雲端驗證</span><span class="sxs-lookup"><span data-stu-id="eccf8-111">Cloud authentication</span></span>

<span data-ttu-id="eccf8-112">這取決於如果您有或沒有現有 Active Directory 環境內部部署，您有數個選項來管理 Office 365 使用者的驗證及身分識別服務。</span><span class="sxs-lookup"><span data-stu-id="eccf8-112">Depending if you have or don't have an existing Active Directory environment on-premises, you have several options to manage authentication and identity services for your users with Office 365.</span></span>
  
### <a name="cloud-only"></a><span data-ttu-id="eccf8-113">僅雲端</span><span class="sxs-lookup"><span data-stu-id="eccf8-113">Cloud-only</span></span>

<span data-ttu-id="eccf8-p103">僅限雲端模型，管理 [Office 365 中的您使用者帳戶僅]。無內部伺服器所需;它是所有在雲端中由處理 Azure AD。建立及管理 Office 365 系統管理中心中的使用者或使用 Windows PowerShell [PowerShell cmdlet](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-with-office-365-powershell)和身分識別與驗證處理完全在雲端中的 Azure AD。僅限雲端模型通常是不錯的選擇是否：</span><span class="sxs-lookup"><span data-stu-id="eccf8-p103">With the cloud-only model, you manage your user accounts in Office 365 only. No on-premises servers are required; it's all handled in the cloud by Azure AD. You create and manage users in the Office 365 admin center or by using Windows PowerShell [PowerShell cmdlets](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-with-office-365-powershell) and identity and authentication are handled completely in the cloud by Azure AD. The cloud-only model is typically a good choice if:</span></span> 
  
- <span data-ttu-id="eccf8-118">您有任何其他內部部署使用者目錄。</span><span class="sxs-lookup"><span data-stu-id="eccf8-118">You have no other on-premises user directory.</span></span>
    
- <span data-ttu-id="eccf8-119">您有非常複雜內部部署目錄並只想要避免整合其工作。</span><span class="sxs-lookup"><span data-stu-id="eccf8-119">You have a very complex on-premises directory and simply want to avoid the work to integrate with it.</span></span>
    
- <span data-ttu-id="eccf8-p104">您已在現有的內部部署目錄，但您想要執行的試用版或 Office 365 試驗。稍後，您可以比對內部使用者的雲端使用者當您準備好連線到您的內部部署目錄。</span><span class="sxs-lookup"><span data-stu-id="eccf8-p104">You have an existing on-premises directory, but you want to run a trial or pilot of Office 365. Later, you can match the cloud users to on-premises users when you are ready to connect to your on-premises directory.</span></span>
    
<span data-ttu-id="eccf8-122">若要開始使用雲端身分識別，請參閱 ＜[設定 Office 365 企業版](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa)。</span><span class="sxs-lookup"><span data-stu-id="eccf8-122">To get started with cloud identity, see [Set up Office 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa).</span></span>
  
### <a name="password-hash-sync-with-seamless-single-sign-on"></a><span data-ttu-id="eccf8-123">使用順暢單一登入的密碼雜湊同步處理</span><span class="sxs-lookup"><span data-stu-id="eccf8-123">Password hash sync with seamless single sign-on</span></span>

<span data-ttu-id="eccf8-p105">若要啟用內部部署目錄物件在 Azure AD 驗證最簡單的方法。使用密碼雜湊同步處理 (PHS)，與 Office 365 同步處理內部部署 Active Directory 使用者帳戶物件及管理您的使用者在內部。使用者密碼雜湊已同步處理從內部部署 Active Directory 至 Azure AD，讓使用者有相同的密碼內部部署與雲端中。密碼已變更或重設為內部，新的密碼雜湊就進行同步處理至 Azure AD 使您的使用者可以雲端資源和內部部署資源一律使用相同的密碼。密碼永遠不會傳送到 Azure AD 或儲存在 Azure AD 以純文字。Azure AD，例如身分識別保護部分 premium 功能需要的 PHS 不論其選取驗證方法。以順暢單一登入，使用者會自動登入時位於其公司裝置並連線至公司網路的 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="eccf8-p105">The simplest way to enable authentication for on-premises directory objects in Azure AD. With password hash sync (PHS), you synchronize your on-premises Active Directory user account objects with Office 365 and manage your users on-premises. Hashes of user passwords are synchronized from your on-premises Active Directory to Azure AD so that the users have the same password on-premises and in the cloud. When passwords are changed or reset on-premises, the new password hashes are synchronized to Azure AD so that your users can always use the same password for cloud resources and on-premises resources. The passwords are never sent to Azure AD or stored in Azure AD in clear text. Some premium features of Azure AD, such as Identity Protection, require PHS regardless of which authentication method is selected. With seamless single sign-on, users are automatically signed in to Azure AD when they are on their corporate devices and connected to your corporate network.</span></span>
  
<span data-ttu-id="eccf8-131">深入了解[選擇密碼雜湊同步處理](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)及[順暢單一登入](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso)。</span><span class="sxs-lookup"><span data-stu-id="eccf8-131">Learn more about [choosing password hash sync](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) and [seamless single sign-on](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso).</span></span>
  
### <a name="pass-through-authentication-with-seamless-single-sign-on"></a><span data-ttu-id="eccf8-132">通過驗證與順暢單一登入</span><span class="sxs-lookup"><span data-stu-id="eccf8-132">Pass-through authentication with seamless single sign-on</span></span>

<span data-ttu-id="eccf8-p106">提供使用一或多個內部部署伺服器上執行的軟體代理程式驗證的使用者直接與您在內部部署 Active Directory 的 Azure AD 驗證服務的簡單密碼驗證。與通過驗證 (PTA) 與 Office 365 同步處理內部部署 Active Directory 使用者帳戶物件及管理您的使用者在內部。可讓使用者登入內部部署和 Office 365 資源和使用其內部部署帳戶及密碼的應用程式。此設定會對您的內部部署 Active Directory 直接使用者密碼驗證而不傳送給 Office 365 的密碼雜湊。會指出與安全性需求來立即強制執行內部部署使用者帳戶的公司、 密碼原則和登入時間可使用此驗證方法。以順暢單一登入，使用者會自動登入時位於其公司裝置並連線至公司網路的 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="eccf8-p106">Provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your on-premises Active Directory. With pass-through authentication (PTA), you synchronize on-premises Active Directory user account objects with Office 365 and manage your users on-premises. Allows your users to sign in to both on-premises and Office 365 resources and applications using their on-premises account and password. This configuration validates users passwords directly against your on-premises Active Directory without sending password hashes to Office 365. Companies with a security requirement to immediately enforce on-premises user account states, password policies, and logon hours would use this authentication method. With seamless single sign-on, users are automatically signed in to Azure AD when they are on their corporate devices and connected to your corporate network.</span></span>
  
<span data-ttu-id="eccf8-139">深入了解[選擇通過驗證](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)和[順暢單一登入](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso)。</span><span class="sxs-lookup"><span data-stu-id="eccf8-139">Learn more about [choosing pass-through authentication](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) and [seamless single sign-on](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso).</span></span>
  
## <a name="federated-authentication-options"></a><span data-ttu-id="eccf8-140">同盟的驗證選項</span><span class="sxs-lookup"><span data-stu-id="eccf8-140">Federated authentication options</span></span>

<span data-ttu-id="eccf8-141">如果您有現有 Active Directory 環境內部部署，您可以透過使用同盟的驗證來管理 Office 365 中使用者的驗證及身分識別服務與您的目錄整合 Office 365。</span><span class="sxs-lookup"><span data-stu-id="eccf8-141">If you have an existing Active Directory environment on-premises, you can integrate Office 365 with your directory by using federated authentication to manage authentication and identity services for your users in Office 365.</span></span>
  
### <a name="federated-identity-with-active-directory-federation-services-ad-fs"></a><span data-ttu-id="eccf8-142">同盟身分識別與 Active Directory Federation Services (AD FS)</span><span class="sxs-lookup"><span data-stu-id="eccf8-142">Federated identity with Active Directory Federation Services (AD FS)</span></span>

<span data-ttu-id="eccf8-p107">主要針對具有較複雜的驗證需求的大型企業組織、 內部部署與 Office 365 同步處理目錄物件和使用者帳戶是受管理的內部。使用 AD FS 使用者有相同的密碼內部部署與雲端中並不需要登入一次使用 Office 365。此同盟的驗證模型可提供額外的驗證需求，例如智慧卡型驗證或協力廠商多重要素驗證時，為通常是必要的組織已驗證需求。原本就不支援 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="eccf8-p107">Primarily for large enterprise organizations with more complex authentication requirements, on-premises directory objects are synchronized with Office 365 and users accounts are managed on-premises. With AD FS, users have the same password on-premises and in the cloud and they do not have to sign in again to use Office 365. This federated authentication model can provide additional authentication requirements, such as smartcard-based authentication or a third-party multi-factor authentication and is typically required when organizations have an authentication requirement not natively supported by Azure AD.</span></span>
  
<span data-ttu-id="eccf8-146">深入了解[選擇 with AD FS 同盟身分識別](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)。</span><span class="sxs-lookup"><span data-stu-id="eccf8-146">Learn more about [choosing federated identity with AD FS](https://docs.microsoft.com/azure/security/azure-ad-choose-authn).</span></span>
  
### <a name="third-party-authentication-and-identity-providers"></a><span data-ttu-id="eccf8-147">協力廠商驗證及身分識別提供者</span><span class="sxs-lookup"><span data-stu-id="eccf8-147">Third-party authentication and identity providers</span></span>

<span data-ttu-id="eccf8-p108">在內部部署目錄物件可能會同步至 Office 365 與雲端資源存取主要受管理的協力廠商身分識別提供者 (IdP)。如果貴組織使用的同盟協力廠商解決方案，您可以設定登入該解決方案的 Office 365 同盟協力廠商解決方案是相容於 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="eccf8-p108">On-premises directory objects may be synchronized to Office 365 and cloud resource access is primarily managed by a third-party identity provider (IdP). If your organization uses a third-party federation solution, you can configure sign-on with that solution for Office 365 provided that the third-party federation solution is compatible with Azure AD.</span></span>
  
<span data-ttu-id="eccf8-150">深入了解[Azure AD 同盟相容性](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility)。</span><span class="sxs-lookup"><span data-stu-id="eccf8-150">Learn more about [Azure AD federation compatibility](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility).</span></span>
  
## <a name="configuring-identity-and-authentication-with-office-365"></a><span data-ttu-id="eccf8-151">使用 Office 365 設定身分識別與驗證</span><span class="sxs-lookup"><span data-stu-id="eccf8-151">Configuring identity and authentication with Office 365</span></span>

<span data-ttu-id="eccf8-p109">將您的內部部署目錄整合與 Office 365 和 Azure AD 簡化了[Azure AD 連線](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)。Azure AD 連線是最適合您的目錄連線] 及 [是 Microsoft 的組織中的建議來同步處理至雲端使用者。</span><span class="sxs-lookup"><span data-stu-id="eccf8-p109">Integrating your on-premises directories with Office 365 and Azure AD has been simplified with [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect). Azure AD Connect is the best way to connect your directories and is Microsoft's recommendation for organizations to sync their users to the cloud.</span></span>
  
<span data-ttu-id="eccf8-154">您也可以使用 Azure AD 顧問： [Azure AD Connect 顧問](https://aka.ms/aadconnectpwsync)、 [AD FS 部署顧問](https://aka.ms/adfsguidance)，以及[Azure AD Premium 安裝指南](https://aka.ms/aadpguidance)。</span><span class="sxs-lookup"><span data-stu-id="eccf8-154">You can also use the Azure AD advisors: the [Azure AD Connect advisor](https://aka.ms/aadconnectpwsync), the [AD FS deployment advisor](https://aka.ms/adfsguidance), and the [Azure AD Premium setup guide](https://aka.ms/aadpguidance).</span></span>
  
## <a name="video-training"></a><span data-ttu-id="eccf8-155">影片訓練</span><span class="sxs-lookup"><span data-stu-id="eccf8-155">Video training</span></span>

<span data-ttu-id="eccf8-156">如需詳細資訊，請參閱視訊課程[Office 365： 管理身分識別使用 Azure AD 連接](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx)、 LinkedIn 學習由致力提供給您。</span><span class="sxs-lookup"><span data-stu-id="eccf8-156">For more information, see the video course [Office 365: Manage Identities Using Azure AD Connect](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx), brought to you by LinkedIn Learning.</span></span>
