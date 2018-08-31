---
title: 修正 Office 365 的目錄同步處理問題
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: 說明 Office 365 中目錄同步處理的常見問題原因，並提供許多方法來協助疑難排解和解決它們。
ms.openlocfilehash: ad3b6e27439354a2ede9b1a4b100e0f9e06148d3
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540000"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a><span data-ttu-id="0e6b2-103">修正 Office 365 的目錄同步處理問題</span><span class="sxs-lookup"><span data-stu-id="0e6b2-103">Fixing problems with directory synchronization for Office 365</span></span>

<span data-ttu-id="0e6b2-p101">使用目錄同步處理，您可以繼續以管理使用者與群組的內部和同步處理新增、 刪除及雲端的變更。但設定更複雜，有時很難識別問題的來源。我們已資源以協助您找出潛在的問題並修正它們。</span><span class="sxs-lookup"><span data-stu-id="0e6b2-p101">With directory synchronization, you can continue to manage users and groups on-premises and synchronize additions, deletions, and changes to the cloud. But setup is a little complicated and it can sometimes be difficult to identify the source of problems. We have resources to help you identify potential issues and fix them.</span></span>
  
## <a name="how-do-i-know-if-something-is-wrong"></a><span data-ttu-id="0e6b2-107">如何知道某個項目是否錯誤？</span><span class="sxs-lookup"><span data-stu-id="0e6b2-107">How do I know if something is wrong?</span></span>

<span data-ttu-id="0e6b2-108">在 Office 365 系統管理中心 DirSync 狀態並排顯示指出有問題時有問題的第一個指示：</span><span class="sxs-lookup"><span data-stu-id="0e6b2-108">The first indication that something is wrong is when the DirSync Status tile in the Office 365 admin center indicates there is a problem:</span></span>
  
![DirSync 狀態磚 admin center preview](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
<span data-ttu-id="0e6b2-p102">您也會收到 （備用電子郵件部署與管理電子郵件） 郵件來自 Office 365，指出您的租用戶發生目錄同步作業錯誤。如需詳細資訊請參閱[Office 365 中的身分識別目錄同步處理錯誤](identify-directory-synchronization-errors.md)。</span><span class="sxs-lookup"><span data-stu-id="0e6b2-p102">You will also receive a mail (to the alternate email and to your admin email) from Office 365 that indicates your tenant has encountered directory synchronization errors. For details see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a><span data-ttu-id="0e6b2-112">如何取得 Azure [Active Directory 連線工具？</span><span class="sxs-lookup"><span data-stu-id="0e6b2-112">How do I get Azure Active Directory Connect tool?</span></span>

<span data-ttu-id="0e6b2-p103">在 Office 365 系統管理中心中，瀏覽至 [* * 使用者 * * \> **作用中使用者**。按一下 [**更多**] 功能表並選取 [**目錄同步處理**。</span><span class="sxs-lookup"><span data-stu-id="0e6b2-p103">In the Office 365 admin center, navigate to ** Users ** \> **Active users**. Click the **More** menu and select **Directory synchronization**.</span></span> 
  
![在 [更多] 功能表中選擇 [目錄同步處理](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
<span data-ttu-id="0e6b2-116">在舊的 Office 365 系統管理中心中，瀏覽至**使用者** \> **作用中使用者**，並選取 [**設定** **Active Directory 同步處理**] 旁。</span><span class="sxs-lookup"><span data-stu-id="0e6b2-116">In the old Office 365 admin center, navigate to **USERS** \> **Active Users**, and select **Set up** next to **Active Directory synchronization**.</span></span> 
  
![按一下 [Active Directory 同步處理中選擇 [設定](media/bd95492b-d65e-4072-a6ee-e562f5f566c3.png)
  
<span data-ttu-id="0e6b2-118">依照[精靈中的指示](set-up-directory-synchronization.md)下載 Azure AD 連線。</span><span class="sxs-lookup"><span data-stu-id="0e6b2-118">Follow the [instructions in the wizard](set-up-directory-synchronization.md) to download Azure AD Connect.</span></span> 
  
<span data-ttu-id="0e6b2-119">如果您仍會使用 Azure Active Directory 同步處理 (DirSync)，請查看[如何疑難排解 Azure Active Directory 同步作業工具安裝和設定精靈] 在 Office 365 中的錯誤訊息](https://go.microsoft.com/fwlink/p/?LinkId=396717)的安裝的系統需求的相關資訊dirsync、 您需要的權限及如何疑難排解常見的錯誤。</span><span class="sxs-lookup"><span data-stu-id="0e6b2-119">If you are still using Azure Active Directory Sync (DirSync), take a look at [How to troubleshoot Azure Active Directory Sync Tool installation and Configuration Wizard error messages in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) for information about the system requirements to install dirsync, the permissions you need, and how to troubleshoot common errors.</span></span> 
  
<span data-ttu-id="0e6b2-120">若要從 Azure Active Directory 同步處理更新 Azure AD 連線，請參閱[的升級指示](https://go.microsoft.com/fwlink/p/?LinkId=733240)。</span><span class="sxs-lookup"><span data-stu-id="0e6b2-120">To update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a><span data-ttu-id="0e6b2-121">Office 365 中目錄同步處理問題的解決常見原因</span><span class="sxs-lookup"><span data-stu-id="0e6b2-121">Resolving common causes of problems with directory synchronization in Office 365</span></span>

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a><span data-ttu-id="0e6b2-122">**同步處理的物件未出現或線上、 更新或 I 從服務取得同步處理錯誤報告。**</span><span class="sxs-lookup"><span data-stu-id="0e6b2-122">**Synchronized objects aren't appearing or updating online, or I'm getting synchronization error reports from the Service.**</span></span>

- [<span data-ttu-id="0e6b2-123">身分識別同步處理及 duplicate 屬性恢復能力</span><span class="sxs-lookup"><span data-stu-id="0e6b2-123">Identity synchronization and duplicate attribute resiliency</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=798300)

### <a name="i-have-an-alert-in-the-office-365-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a><span data-ttu-id="0e6b2-124">**我的 Office 365 系統管理中心中，有通知或正在接收尚未在最近的同步處理事件的自動化電子郵件**</span><span class="sxs-lookup"><span data-stu-id="0e6b2-124">**I have an alert in the Office 365 admin center, or am receiving automated emails that there hasn't been a recent synchronization event**</span></span>
- [<span data-ttu-id="0e6b2-125">疑難排解 Azure AD 連線的連線問題</span><span class="sxs-lookup"><span data-stu-id="0e6b2-125">Troubleshoot connectivity issues with Azure AD Connect</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820597)
- [<span data-ttu-id="0e6b2-126">Azure AD 連線帳戶和權限</span><span class="sxs-lookup"><span data-stu-id="0e6b2-126">Azure AD Connect Accounts and permissions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [<span data-ttu-id="0e6b2-127">Azure AD 連線同步處理： 如何管理 Azure AD 的服務帳戶</span><span class="sxs-lookup"><span data-stu-id="0e6b2-127">Azure AD Connect sync: How to manage the Azure AD service account</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820599)
- [<span data-ttu-id="0e6b2-128">Azure Active Directory 停駐點或您的目錄同步作業是同步處理尚未在多個一天中註冊也警告</span><span class="sxs-lookup"><span data-stu-id="0e6b2-128">Directory synchronization to Azure Active Directory stops or you're warned that sync hasn't registered in more than a day</span></span>](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-office-365-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a><span data-ttu-id="0e6b2-129">**密碼雜湊不同步處理，或 I 看不到 Office 365 系統管理中心尚未最近的密碼雜湊同步處理的通知**</span><span class="sxs-lookup"><span data-stu-id="0e6b2-129">**Password hashes aren't synchronizing, or I'm seeing an alert in the Office 365 admin center that there hasn't been a recent password hash synchronization**</span></span>
- [<span data-ttu-id="0e6b2-130">實作密碼雜湊同步處理與 Azure AD 連線同步處理</span><span class="sxs-lookup"><span data-stu-id="0e6b2-130">Implementing password hash synchronization with Azure AD Connect sync</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820600)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a><span data-ttu-id="0e6b2-131">**我正在看不到物件配額超出提醒**</span><span class="sxs-lookup"><span data-stu-id="0e6b2-131">**I'm seeing an alert that Object quota exceeded**</span></span>
- <span data-ttu-id="0e6b2-p104">我們具有內建物件配額可協助保護服務。如果您有您需要將資料庫同步至 Office 365 的目錄中有太多物件，您必須以增加您配額[連絡人商務產品的支援](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)。</span><span class="sxs-lookup"><span data-stu-id="0e6b2-p104">We have a built-in object quota to help protect the service. If you have too many objects in your directory that need to sync to Office 365, you'll have to [Contact support for business products](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) to increase your quota.</span></span>

### <a name="i-need-to-know-which-attributes-are-synchronized"></a><span data-ttu-id="0e6b2-134">**我需要知道哪些屬性已同步處理**</span><span class="sxs-lookup"><span data-stu-id="0e6b2-134">**I need to know which attributes are synchronized**</span></span>
- <span data-ttu-id="0e6b2-135">您可以找到所有內部部署與雲端[右以下](https://go.microsoft.com/fwlink/p/?LinkId=396719)之間的同步處理的屬性的清單。</span><span class="sxs-lookup"><span data-stu-id="0e6b2-135">You can find a list of all the attributes that are synced between on-premises and the cloud [right here](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a><span data-ttu-id="0e6b2-136">**我無法管理或移除已同步處理至雲端的物件**</span><span class="sxs-lookup"><span data-stu-id="0e6b2-136">**I can't manage or remove objects that were synchronized to the cloud**</span></span>
- <span data-ttu-id="0e6b2-p105">已準備好要在僅限雲端中管理物件或是否有已刪除的內部，但在雲端的物件？請查看此[同步處理期間疑難排解錯誤](https://go.microsoft.com/fwlink/p/?linkid=842044)和指引[支援文章](https://go.microsoft.com/fwlink/p/?LinkId=396720)如何解決這些問題。</span><span class="sxs-lookup"><span data-stu-id="0e6b2-p105">Are you ready to manage objects in the cloud only? Or is there an object that was deleted on-premises, but is stuck in the cloud? Take a look at this [Troubleshooting Errors during synchronization](https://go.microsoft.com/fwlink/p/?linkid=842044) and [support article](https://go.microsoft.com/fwlink/p/?LinkId=396720) for guidance on how to resolve these issues.</span></span>

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a><span data-ttu-id="0e6b2-140">**我收到公司超出可同步處理之物件數目的錯誤訊息**</span><span class="sxs-lookup"><span data-stu-id="0e6b2-140">**I got an error message that my company has exceeded the number of objects that can be synchronized**</span></span>
- <span data-ttu-id="0e6b2-141">您可以閱讀更多關於此問題[此處](https://go.microsoft.com/fwlink/p/?LinkId=396721)。</span><span class="sxs-lookup"><span data-stu-id="0e6b2-141">You can read more about this issue [here](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span></span>
   
## <a name="other-resources"></a><span data-ttu-id="0e6b2-142">其他資源</span><span class="sxs-lookup"><span data-stu-id="0e6b2-142">Other resources</span></span>

- [<span data-ttu-id="0e6b2-143">指令碼以修正重複使用者主要名稱</span><span class="sxs-lookup"><span data-stu-id="0e6b2-143">Script to fix duplicate user principal names</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [<span data-ttu-id="0e6b2-144">如何準備目錄同步作業非路由傳送的網域 （例如.local 網域）</span><span class="sxs-lookup"><span data-stu-id="0e6b2-144">How to prepare a non-routable domain (such as .local domain) for directory synchronization</span></span>](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [<span data-ttu-id="0e6b2-145">計算同步處理的物件總數的指令碼</span><span class="sxs-lookup"><span data-stu-id="0e6b2-145">Script to count total synchronized objects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [<span data-ttu-id="0e6b2-146">疑難排解 AD FS 2.0</span><span class="sxs-lookup"><span data-stu-id="0e6b2-146">Troubleshoot AD FS 2.0</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [<span data-ttu-id="0e6b2-147">使用 PowerShell 修正擁有郵件功能的群組的空 DisplayName 屬性</span><span class="sxs-lookup"><span data-stu-id="0e6b2-147">Use PowerShell to fix empty DisplayName attributes for mail-enabled groups</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [<span data-ttu-id="0e6b2-148">使用 PowerShell 修正重複 UPN</span><span class="sxs-lookup"><span data-stu-id="0e6b2-148">Use PowerShell to fix duplicate UPN</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [<span data-ttu-id="0e6b2-149">使用 PowerShell 修正重複電子郵件地址</span><span class="sxs-lookup"><span data-stu-id="0e6b2-149">Use PowerShell to fix duplicate email addresses</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a><span data-ttu-id="0e6b2-150">診斷工具</span><span class="sxs-lookup"><span data-stu-id="0e6b2-150">Diagnostic tools</span></span>

<span data-ttu-id="0e6b2-p106">[IDFix 工具](prepare-directory-attributes-for-synch-with-idfix.md)用來準備進行移轉至 Office 365 中的內部部署 Active Directory 環境中執行探索及補救 identity 物件和其屬性。IDFix 適合負責 Office 365 服務使用 DirSync 的 Active Directory 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="0e6b2-p106">[IDFix tool](prepare-directory-attributes-for-synch-with-idfix.md) is used to perform discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration to Office 365. IDFix is intended for the Active Directory administrators responsible for DirSync with the Office 365 service.</span></span> 

<span data-ttu-id="0e6b2-153">[下載 IDFix 工具](https://go.microsoft.com/fwlink/p/?LinkId=396718)從 Microsoft 下載中心。</span><span class="sxs-lookup"><span data-stu-id="0e6b2-153">[Download the IDFix tool](https://go.microsoft.com/fwlink/p/?LinkId=396718) from the Microsoft download center.</span></span>