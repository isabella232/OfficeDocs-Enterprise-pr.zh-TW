---
title: 修正 Office 365 的目錄同步處理問題
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: 說明 Office 365 中的目錄同步處理問題的常見原因，並提供一些方法，協助疑難排解，並加以解決。
ms.openlocfilehash: a5c4b58dd856158b00605f39d8a66b48488086b2
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001836"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a><span data-ttu-id="3c58f-103">修正 Office 365 的目錄同步處理問題</span><span class="sxs-lookup"><span data-stu-id="3c58f-103">Fixing problems with directory synchronization for Office 365</span></span>

<span data-ttu-id="3c58f-104">目錄同步處理，您可以繼續管理使用者和群組內部部署及同步處理的加入、 刪除及變更至雲端。</span><span class="sxs-lookup"><span data-stu-id="3c58f-104">With directory synchronization, you can continue to manage users and groups on-premises and synchronize additions, deletions, and changes to the cloud.</span></span> <span data-ttu-id="3c58f-105">但安裝程式會有點複雜，而且可以有時候是很難找出問題的來源。</span><span class="sxs-lookup"><span data-stu-id="3c58f-105">But setup is a little complicated and it can sometimes be difficult to identify the source of problems.</span></span> <span data-ttu-id="3c58f-106">我們有資源可以幫助您找出潛在的問題並修正它們。</span><span class="sxs-lookup"><span data-stu-id="3c58f-106">We have resources to help you identify potential issues and fix them.</span></span>
  
## <a name="how-do-i-know-if-something-is-wrong"></a><span data-ttu-id="3c58f-107">如何知道是否有問題？</span><span class="sxs-lookup"><span data-stu-id="3c58f-107">How do I know if something is wrong?</span></span>

<span data-ttu-id="3c58f-108">在 Microsoft 365 系統管理中心的 [目錄同步狀態] 磚指出發生問題時，有問題的第一個指示：</span><span class="sxs-lookup"><span data-stu-id="3c58f-108">The first indication that something is wrong is when the DirSync Status tile in the Microsoft 365 admin center indicates there is a problem:</span></span>
  
![在系統管理中心預覽中並排顯示 DirSync 狀態](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
<span data-ttu-id="3c58f-110">從 Office 365，指出您的租用戶發生目錄同步處理錯誤，也會收到郵件 （的備用電子郵件和您的系統管理員電子郵件）。</span><span class="sxs-lookup"><span data-stu-id="3c58f-110">You will also receive a mail (to the alternate email and to your admin email) from Office 365 that indicates your tenant has encountered directory synchronization errors.</span></span> <span data-ttu-id="3c58f-111">如需詳細資訊，請參閱[在 Office 365 中的身分識別目錄同步處理錯誤](identify-directory-synchronization-errors.md)。</span><span class="sxs-lookup"><span data-stu-id="3c58f-111">For details see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a><span data-ttu-id="3c58f-112">如何取得 Azure Active Directory Connect 工具？</span><span class="sxs-lookup"><span data-stu-id="3c58f-112">How do I get Azure Active Directory Connect tool?</span></span>

<span data-ttu-id="3c58f-113">在[Microsoft 365 系統管理中心](https://admin.microsoft.com)中，瀏覽至 [\* \* 使用者 \* \* \> **作用中的使用者**。</span><span class="sxs-lookup"><span data-stu-id="3c58f-113">In the [Microsoft 365 admin center](https://admin.microsoft.com), navigate to \*\* Users \*\* \> **Active users**.</span></span> <span data-ttu-id="3c58f-114">按一下 [**更多**] 功能表，然後選取 [**目錄同步處理**。</span><span class="sxs-lookup"><span data-stu-id="3c58f-114">Click the **More** menu and select **Directory synchronization**.</span></span> 
  
![在 [更多] 功能表中，選擇 [目錄同步處理](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
<span data-ttu-id="3c58f-116">請遵循[精靈指示](set-up-directory-synchronization.md)下載 Azure AD Connect。</span><span class="sxs-lookup"><span data-stu-id="3c58f-116">Follow the [instructions in the wizard](set-up-directory-synchronization.md) to download Azure AD Connect.</span></span> 
  
<span data-ttu-id="3c58f-117">如果您仍在使用 Azure Active Directory 同步處理 (DirSync)，看看[如何疑難排解 Azure Active Directory 同步處理工具安裝和設定精靈在 Office 365 中的錯誤訊息](https://go.microsoft.com/fwlink/p/?LinkId=396717)的系統需求，以安裝的相關資訊目錄同步，您需要的權限以及如何疑難排解常見錯誤。</span><span class="sxs-lookup"><span data-stu-id="3c58f-117">If you are still using Azure Active Directory Sync (DirSync), take a look at [How to troubleshoot Azure Active Directory Sync Tool installation and Configuration Wizard error messages in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) for information about the system requirements to install dirsync, the permissions you need, and how to troubleshoot common errors.</span></span> 
  
<span data-ttu-id="3c58f-118">若要更新 Azure Active Directory 同步處理從 Azure AD Connect，請參閱 <<c0>的升級指示。</span><span class="sxs-lookup"><span data-stu-id="3c58f-118">To update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a><span data-ttu-id="3c58f-119">Office 365 中的目錄同步處理問題的解決常見原因</span><span class="sxs-lookup"><span data-stu-id="3c58f-119">Resolving common causes of problems with directory synchronization in Office 365</span></span>

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a><span data-ttu-id="3c58f-120">**同步處理的物件未出現 online、 更新或我收到同步處理錯誤報告服務。**</span><span class="sxs-lookup"><span data-stu-id="3c58f-120">**Synchronized objects aren't appearing or updating online, or I'm getting synchronization error reports from the Service.**</span></span>

- [<span data-ttu-id="3c58f-121">身分識別同步處理和重複屬性恢復能力</span><span class="sxs-lookup"><span data-stu-id="3c58f-121">Identity synchronization and duplicate attribute resiliency</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a><span data-ttu-id="3c58f-122">**我在系統管理中心中，有警示或正在接收尚未最近使用的同步處理事件的自動化電子郵件**</span><span class="sxs-lookup"><span data-stu-id="3c58f-122">**I have an alert in the admin center, or am receiving automated emails that there hasn't been a recent synchronization event**</span></span>
- [<span data-ttu-id="3c58f-123">疑難排解連線問題的 Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="3c58f-123">Troubleshoot connectivity issues with Azure AD Connect</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [<span data-ttu-id="3c58f-124">Azure AD Connect 帳戶和權限</span><span class="sxs-lookup"><span data-stu-id="3c58f-124">Azure AD Connect Accounts and permissions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [<span data-ttu-id="3c58f-125">Azure AD Connect 同步處理： 如何管理 Azure AD 服務帳戶</span><span class="sxs-lookup"><span data-stu-id="3c58f-125">Azure AD Connect sync: How to manage the Azure AD service account</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [<span data-ttu-id="3c58f-126">目錄同步處理至 Azure Active Directory 停駐點或您要同步處理未登錄在一天以上警告</span><span class="sxs-lookup"><span data-stu-id="3c58f-126">Directory synchronization to Azure Active Directory stops or you're warned that sync hasn't registered in more than a day</span></span>](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a><span data-ttu-id="3c58f-127">**密碼雜湊未同步處理，或我看到在系統管理中心中尚未最近使用的密碼雜湊同步處理警示**</span><span class="sxs-lookup"><span data-stu-id="3c58f-127">**Password hashes aren't synchronizing, or I'm seeing an alert in the admin center that there hasn't been a recent password hash synchronization**</span></span>
- [<span data-ttu-id="3c58f-128">使用 Azure AD Connect 同步處理實作密碼雜湊同步處理</span><span class="sxs-lookup"><span data-stu-id="3c58f-128">Implementing password hash synchronization with Azure AD Connect sync</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a><span data-ttu-id="3c58f-129">**我看到超過物件配額警示**</span><span class="sxs-lookup"><span data-stu-id="3c58f-129">**I'm seeing an alert that Object quota exceeded**</span></span>
- <span data-ttu-id="3c58f-130">我們有內建物件配額來協助保護服務。</span><span class="sxs-lookup"><span data-stu-id="3c58f-130">We have a built-in object quota to help protect the service.</span></span> <span data-ttu-id="3c58f-131">如果您有太多的物件，您需要同步處理至 Office 365 的目錄中，您必須[連絡商務產品的支援](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)，以增加您的配額。</span><span class="sxs-lookup"><span data-stu-id="3c58f-131">If you have too many objects in your directory that need to sync to Office 365, you'll have to [Contact support for business products](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) to increase your quota.</span></span>

### <a name="i-need-to-know-which-attributes-are-synchronized"></a><span data-ttu-id="3c58f-132">**我還需要知道哪些屬性已同步處理**</span><span class="sxs-lookup"><span data-stu-id="3c58f-132">**I need to know which attributes are synchronized**</span></span>
- <span data-ttu-id="3c58f-133">您可以找到內部部署和雲端[右以下](https://go.microsoft.com/fwlink/p/?LinkId=396719)之間同步處理的所有屬性清單。</span><span class="sxs-lookup"><span data-stu-id="3c58f-133">You can find a list of all the attributes that are synced between on-premises and the cloud [right here](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a><span data-ttu-id="3c58f-134">**我無法管理或移除已同步處理至雲端的物件**</span><span class="sxs-lookup"><span data-stu-id="3c58f-134">**I can't manage or remove objects that were synchronized to the cloud**</span></span>
- <span data-ttu-id="3c58f-135">準備好管理只在雲端中的物件？</span><span class="sxs-lookup"><span data-stu-id="3c58f-135">Are you ready to manage objects in the cloud only?</span></span> <span data-ttu-id="3c58f-136">或者，是否有已刪除的內部，但卡在雲端中的物件？</span><span class="sxs-lookup"><span data-stu-id="3c58f-136">Or is there an object that was deleted on-premises, but is stuck in the cloud?</span></span> <span data-ttu-id="3c58f-137">看看此[同步處理期間疑難排解錯誤](https://go.microsoft.com/fwlink/p/?linkid=842044)和[支援文章](https://go.microsoft.com/fwlink/p/?LinkId=396720)指導方針如何解決這些問題。</span><span class="sxs-lookup"><span data-stu-id="3c58f-137">Take a look at this [Troubleshooting Errors during synchronization](https://go.microsoft.com/fwlink/p/?linkid=842044) and [support article](https://go.microsoft.com/fwlink/p/?LinkId=396720) for guidance on how to resolve these issues.</span></span>

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a><span data-ttu-id="3c58f-138">**我收到公司超出可同步處理的物件數目的錯誤訊息**</span><span class="sxs-lookup"><span data-stu-id="3c58f-138">**I got an error message that my company has exceeded the number of objects that can be synchronized**</span></span>
- <span data-ttu-id="3c58f-139">您可以閱讀關於此問題[以下](https://go.microsoft.com/fwlink/p/?LinkId=396721)。</span><span class="sxs-lookup"><span data-stu-id="3c58f-139">You can read more about this issue [here](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span></span>
   
## <a name="other-resources"></a><span data-ttu-id="3c58f-140">其他資源</span><span class="sxs-lookup"><span data-stu-id="3c58f-140">Other resources</span></span>

- <span data-ttu-id="3c58f-141">[用來修正使用者主體名稱重複問題的指令碼](https://go.microsoft.com/fwlink/p/?LinkId=396725) (英文)</span><span class="sxs-lookup"><span data-stu-id="3c58f-141">[Script to fix duplicate user principal names](https://go.microsoft.com/fwlink/p/?LinkId=396725)</span></span>
    
- [<span data-ttu-id="3c58f-142">如何先準備目錄同步處理非可路由網域 （例如.local 網域）</span><span class="sxs-lookup"><span data-stu-id="3c58f-142">How to prepare a non-routable domain (such as .local domain) for directory synchronization</span></span>](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [<span data-ttu-id="3c58f-143">若要計算總計的同步處理的物件的指令碼</span><span class="sxs-lookup"><span data-stu-id="3c58f-143">Script to count total synchronized objects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [<span data-ttu-id="3c58f-144">疑難排解 AD FS 2.0</span><span class="sxs-lookup"><span data-stu-id="3c58f-144">Troubleshoot AD FS 2.0</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [<span data-ttu-id="3c58f-145">使用 PowerShell 修正擁有郵件功能的群組的空 DisplayName 屬性</span><span class="sxs-lookup"><span data-stu-id="3c58f-145">Use PowerShell to fix empty DisplayName attributes for mail-enabled groups</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [<span data-ttu-id="3c58f-146">使用 PowerShell 修正 upn 重複的問題</span><span class="sxs-lookup"><span data-stu-id="3c58f-146">Use PowerShell to fix duplicate UPN</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [<span data-ttu-id="3c58f-147">使用 PowerShell 修正重複電子郵件地址</span><span class="sxs-lookup"><span data-stu-id="3c58f-147">Use PowerShell to fix duplicate email addresses</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a><span data-ttu-id="3c58f-148">診斷工具</span><span class="sxs-lookup"><span data-stu-id="3c58f-148">Diagnostic tools</span></span>

<span data-ttu-id="3c58f-149">[IDFix 工具](prepare-directory-attributes-for-synch-with-idfix.md)用來準備進行移轉到 Office 365 中內部部署 Active Directory 環境中執行探索和修復的身分識別物件和其屬性。</span><span class="sxs-lookup"><span data-stu-id="3c58f-149">[IDFix tool](prepare-directory-attributes-for-synch-with-idfix.md) is used to perform discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration to Office 365.</span></span> <span data-ttu-id="3c58f-150">IDFix 適用於負責與 Office 365 服務目錄同步的 Active Directory 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="3c58f-150">IDFix is intended for the Active Directory administrators responsible for DirSync with the Office 365 service.</span></span> 

<span data-ttu-id="3c58f-151">[下載 IDFix 工具](https://go.microsoft.com/fwlink/p/?LinkId=396718)從 Microsoft 下載中心找到。</span><span class="sxs-lookup"><span data-stu-id="3c58f-151">[Download the IDFix tool](https://go.microsoft.com/fwlink/p/?LinkId=396718) from the Microsoft download center.</span></span>