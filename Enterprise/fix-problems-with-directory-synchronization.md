---
title: 修正 Microsoft 365 的目錄同步處理問題
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: 說明在 Office 365 中目錄同步處理問題的常見原因，並提供一些方法來協助疑難排解及解決問題。
ms.openlocfilehash: d9e390a7230499f724ebbdae592264a850dd9418
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998031"
---
# <a name="fixing-problems-with-directory-synchronization-for-microsoft-365"></a><span data-ttu-id="c4e14-103">修正 Microsoft 365 的目錄同步處理問題</span><span class="sxs-lookup"><span data-stu-id="c4e14-103">Fixing problems with directory synchronization for Microsoft 365</span></span>

<span data-ttu-id="c4e14-104">透過目錄同步作業，您可以繼續管理內部部署的使用者和群組，並同步處理載入、刪除和變更雲端。</span><span class="sxs-lookup"><span data-stu-id="c4e14-104">With directory synchronization, you can continue to manage users and groups on-premises and synchronize additions, deletions, and changes to the cloud.</span></span> <span data-ttu-id="c4e14-105">不過，安裝程式有點複雜，有時可能難以識別問題的來源。</span><span class="sxs-lookup"><span data-stu-id="c4e14-105">But setup is a little complicated and it can sometimes be difficult to identify the source of problems.</span></span> <span data-ttu-id="c4e14-106">我們有助您識別潛在問題並加以修正的資源。</span><span class="sxs-lookup"><span data-stu-id="c4e14-106">We have resources to help you identify potential issues and fix them.</span></span>
  
## <a name="how-do-i-know-if-something-is-wrong"></a><span data-ttu-id="c4e14-107">如何知道問題是否正確？</span><span class="sxs-lookup"><span data-stu-id="c4e14-107">How do I know if something is wrong?</span></span>

<span data-ttu-id="c4e14-108">當 Microsoft 365 系統管理中心中的 DirSync 狀態麻將牌指出發生問題時，第一個指出發生錯誤的第一個指示。</span><span class="sxs-lookup"><span data-stu-id="c4e14-108">The first indication that something is wrong is when the DirSync Status tile in the Microsoft 365 admin center indicates there is a problem.</span></span>
  
<span data-ttu-id="c4e14-109">您也會收到來自 Microsoft 365 的郵件（到其他電子郵件和您的系統管理員電子郵件），表示您的租使用者遇到目錄同步處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="c4e14-109">You will also receive a mail (to the alternate email and to your admin email) from Microsoft 365 that indicates your tenant has encountered directory synchronization errors.</span></span> <span data-ttu-id="c4e14-110">如需詳細資訊，請參閱[識別 Microsoft 365 中的目錄同步處理錯誤](identify-directory-synchronization-errors.md)。</span><span class="sxs-lookup"><span data-stu-id="c4e14-110">For details see [Identify directory synchronization errors in Microsoft 365](identify-directory-synchronization-errors.md).</span></span>
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a><span data-ttu-id="c4e14-111">如何取得 Azure Active Directory Connect 工具？</span><span class="sxs-lookup"><span data-stu-id="c4e14-111">How do I get Azure Active Directory Connect tool?</span></span>

<span data-ttu-id="c4e14-112">在[Microsoft 365 系統管理中心](https://admin.microsoft.com)中，流覽至 [**使用者**] [作用中 \> **使用者**]。</span><span class="sxs-lookup"><span data-stu-id="c4e14-112">In the [Microsoft 365 admin center](https://admin.microsoft.com), navigate to **Users** \> **Active users**.</span></span> <span data-ttu-id="c4e14-113">按一下 [**更多**] 功能表（三個點）並選取 **[目錄同步**處理]。</span><span class="sxs-lookup"><span data-stu-id="c4e14-113">Click the **More** menu (three dots) and select **Directory synchronization**.</span></span> 
  
<span data-ttu-id="c4e14-114">依照[嚮導中的指示](set-up-directory-synchronization.md)下載 Azure AD Connect。</span><span class="sxs-lookup"><span data-stu-id="c4e14-114">Follow the [instructions in the wizard](set-up-directory-synchronization.md) to download Azure AD Connect.</span></span> 
  
<span data-ttu-id="c4e14-115">如果您仍在使用 Azure Active Directory （Azure AD）同步處理（DirSync），請參閱[如何疑難排解 Microsoft 365 中的 Azure Active Directory 同步作業工具安裝和設定向導錯誤訊息](https://go.microsoft.com/fwlink/p/?LinkId=396717)，以取得安裝 DirSync 的系統需求相關資訊，您需要的許可權，以及如何疑難排解常見的錯誤。</span><span class="sxs-lookup"><span data-stu-id="c4e14-115">If you are still using Azure Active Directory (Azure AD) Sync (DirSync), take a look at [How to troubleshoot Azure Active Directory Sync Tool installation and Configuration Wizard error messages in Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) for information about the system requirements to install dirsync, the permissions you need, and how to troubleshoot common errors.</span></span> 
  
<span data-ttu-id="c4e14-116">若要從 Azure AD Sync 更新至 Azure AD Connect，請參閱[升級指示](https://go.microsoft.com/fwlink/p/?LinkId=733240)。</span><span class="sxs-lookup"><span data-stu-id="c4e14-116">To update from Azure AD Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-microsoft-365"></a><span data-ttu-id="c4e14-117">解決 Microsoft 365 中目錄同步問題的常見原因</span><span class="sxs-lookup"><span data-stu-id="c4e14-117">Resolving common causes of problems with directory synchronization in Microsoft 365</span></span>

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a><span data-ttu-id="c4e14-118">**同步處理的物件不會出現或線上更新，或從服務取得同步處理錯誤報表。**</span><span class="sxs-lookup"><span data-stu-id="c4e14-118">**Synchronized objects aren't appearing or updating online, or I'm getting synchronization error reports from the Service.**</span></span>

- [<span data-ttu-id="c4e14-119">身分識別同步及重複屬性復原</span><span class="sxs-lookup"><span data-stu-id="c4e14-119">Identity synchronization and duplicate attribute resiliency</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a><span data-ttu-id="c4e14-120">**我在系統管理中心有警示，或是收到自動電子郵件，但沒有最近的同步處理事件**</span><span class="sxs-lookup"><span data-stu-id="c4e14-120">**I have an alert in the admin center, or am receiving automated emails that there hasn't been a recent synchronization event**</span></span>
- [<span data-ttu-id="c4e14-121">針對 Azure AD Connect 的連線問題進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="c4e14-121">Troubleshoot connectivity issues with Azure AD Connect</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [<span data-ttu-id="c4e14-122">Azure AD Connect 帳戶和權限</span><span class="sxs-lookup"><span data-stu-id="c4e14-122">Azure AD Connect Accounts and permissions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [<span data-ttu-id="c4e14-123">Azure AD Connect 同步：如何管理 Azure AD 服務帳戶</span><span class="sxs-lookup"><span data-stu-id="c4e14-123">Azure AD Connect sync: How to manage the Azure AD service account</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [<span data-ttu-id="c4e14-124">Azure Active Directory 目錄同步處理停止，或者系統警告您超過一天未登錄同步處理</span><span class="sxs-lookup"><span data-stu-id="c4e14-124">Directory synchronization to Azure Active Directory stops or you're warned that sync hasn't registered in more than a day</span></span>](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a><span data-ttu-id="c4e14-125">**未同步處理密碼雜湊，或在系統管理中心中看到未最近密碼雜湊同步處理的警示**</span><span class="sxs-lookup"><span data-stu-id="c4e14-125">**Password hashes aren't synchronizing, or I'm seeing an alert in the admin center that there hasn't been a recent password hash synchronization**</span></span>
- [<span data-ttu-id="c4e14-126">使用 Azure AD Connect 同步處理來實作密碼雜湊同步處理</span><span class="sxs-lookup"><span data-stu-id="c4e14-126">Implementing password hash synchronization with Azure AD Connect sync</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a><span data-ttu-id="c4e14-127">**我看到超出物件配額的警示**</span><span class="sxs-lookup"><span data-stu-id="c4e14-127">**I'm seeing an alert that Object quota exceeded**</span></span>
- <span data-ttu-id="c4e14-128">我們有內建的物件配額，可協助保護服務。</span><span class="sxs-lookup"><span data-stu-id="c4e14-128">We have a built-in object quota to help protect the service.</span></span> <span data-ttu-id="c4e14-129">如果您的目錄中有太多物件需要同步處理至 Microsoft 365，您必須[聯繫商務產品支援](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)以增加配額。</span><span class="sxs-lookup"><span data-stu-id="c4e14-129">If you have too many objects in your directory that need to sync to Microsoft 365, you'll have to [Contact support for business products](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) to increase your quota.</span></span>

### <a name="i-need-to-know-which-attributes-are-synchronized"></a><span data-ttu-id="c4e14-130">**我需要知道同步處理的屬性**</span><span class="sxs-lookup"><span data-stu-id="c4e14-130">**I need to know which attributes are synchronized**</span></span>
- <span data-ttu-id="c4e14-131">您可以在[這裡](https://go.microsoft.com/fwlink/p/?LinkId=396719)找到所有在內部部署與雲端之間同步處理之屬性的清單。</span><span class="sxs-lookup"><span data-stu-id="c4e14-131">You can find a list of all the attributes that are synced between on-premises and the cloud [right here](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a><span data-ttu-id="c4e14-132">**我無法管理或移除同步處理至雲端的物件**</span><span class="sxs-lookup"><span data-stu-id="c4e14-132">**I can't manage or remove objects that were synchronized to the cloud**</span></span>
- <span data-ttu-id="c4e14-133">您是否準備好只管理雲端中的物件？</span><span class="sxs-lookup"><span data-stu-id="c4e14-133">Are you ready to manage objects in the cloud only?</span></span> <span data-ttu-id="c4e14-134">或是存在已在內部部署中刪除，但在雲端中已停滯的物件嗎？</span><span class="sxs-lookup"><span data-stu-id="c4e14-134">Or is there an object that was deleted on-premises, but is stuck in the cloud?</span></span> <span data-ttu-id="c4e14-135">請參閱同步處理期間的此[疑難排解錯誤](https://go.microsoft.com/fwlink/p/?linkid=842044)及[支援文章](https://go.microsoft.com/fwlink/p/?LinkId=396720)，以取得如何解決這些問題的指導方針。</span><span class="sxs-lookup"><span data-stu-id="c4e14-135">Take a look at this [Troubleshooting Errors during synchronization](https://go.microsoft.com/fwlink/p/?linkid=842044) and [support article](https://go.microsoft.com/fwlink/p/?LinkId=396720) for guidance on how to resolve these issues.</span></span>

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a><span data-ttu-id="c4e14-136">**我收到的錯誤訊息是我的公司已超過可同步處理的物件數目**</span><span class="sxs-lookup"><span data-stu-id="c4e14-136">**I got an error message that my company has exceeded the number of objects that can be synchronized**</span></span>
- <span data-ttu-id="c4e14-137">您可以在[這裡](https://go.microsoft.com/fwlink/p/?LinkId=396721)閱讀更多關於此問題的資訊。</span><span class="sxs-lookup"><span data-stu-id="c4e14-137">You can read more about this issue [here](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span></span>
   
## <a name="other-resources"></a><span data-ttu-id="c4e14-138">其他資源</span><span class="sxs-lookup"><span data-stu-id="c4e14-138">Other resources</span></span>

- <span data-ttu-id="c4e14-139">[用來修正使用者主體名稱重複問題的指令碼](https://go.microsoft.com/fwlink/p/?LinkId=396725) (英文)</span><span class="sxs-lookup"><span data-stu-id="c4e14-139">[Script to fix duplicate user principal names](https://go.microsoft.com/fwlink/p/?LinkId=396725)</span></span>
    
- [<span data-ttu-id="c4e14-140">如何為目錄同步處理準備非可路由的網域（例如，局域）</span><span class="sxs-lookup"><span data-stu-id="c4e14-140">How to prepare a non-routable domain (such as .local domain) for directory synchronization</span></span>](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [<span data-ttu-id="c4e14-141">計算同步處理的物件總數的腳本</span><span class="sxs-lookup"><span data-stu-id="c4e14-141">Script to count total synchronized objects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [<span data-ttu-id="c4e14-142">疑難排解 AD FS 2。0</span><span class="sxs-lookup"><span data-stu-id="c4e14-142">Troubleshoot AD FS 2.0</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [<span data-ttu-id="c4e14-143">使用 PowerShell 修正具有郵件功能之群組的空 DisplayName 屬性</span><span class="sxs-lookup"><span data-stu-id="c4e14-143">Use PowerShell to fix empty DisplayName attributes for mail-enabled groups</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [<span data-ttu-id="c4e14-144">使用 PowerShell 修正重複的 UPN</span><span class="sxs-lookup"><span data-stu-id="c4e14-144">Use PowerShell to fix duplicate UPN</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [<span data-ttu-id="c4e14-145">使用 PowerShell 修正重複的電子郵件地址</span><span class="sxs-lookup"><span data-stu-id="c4e14-145">Use PowerShell to fix duplicate email addresses</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a><span data-ttu-id="c4e14-146">診斷工具</span><span class="sxs-lookup"><span data-stu-id="c4e14-146">Diagnostic tools</span></span>

<span data-ttu-id="c4e14-147">[IDFix 工具](prepare-directory-attributes-for-synch-with-idfix.md)可用於在內部部署 Active Directory 環境中執行 identity 物件及其屬性的探索和修正，以準備遷移至 Microsoft 365。</span><span class="sxs-lookup"><span data-stu-id="c4e14-147">[IDFix tool](prepare-directory-attributes-for-synch-with-idfix.md) is used to perform discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration to Microsoft 365.</span></span> <span data-ttu-id="c4e14-148">IDFix 是針對與 Microsoft 365 服務的目錄同步處理負責之 Active Directory 系統管理員所設計。</span><span class="sxs-lookup"><span data-stu-id="c4e14-148">IDFix is intended for the Active Directory administrators responsible for directory synchronization with the Microsoft 365 service.</span></span> 

<span data-ttu-id="c4e14-149">從 Microsoft 下載中心[下載 IDFix 工具](https://go.microsoft.com/fwlink/p/?LinkId=396718)。</span><span class="sxs-lookup"><span data-stu-id="c4e14-149">[Download the IDFix tool](https://go.microsoft.com/fwlink/p/?LinkId=396718) from the Microsoft download center.</span></span>