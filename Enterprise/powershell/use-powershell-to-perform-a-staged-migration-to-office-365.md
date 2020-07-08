---
title: 使用 PowerShell 來執行分段移轉至 Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: a20f9dbd-6102-4ffa-b72c-ff813e700930
description: 摘要：了解如何使用 Windows PowerShell 來分段移轉至 Office 365。
ms.openlocfilehash: ca50edd079e17808c46ff5a956ed2efad34eb322
ms.sourcegitcommit: c6a2256f746f55d1cfb739649ffeee1f2f2152aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "45052556"
---
# <a name="use-powershell-to-perform-a-staged-migration-to-office-365"></a><span data-ttu-id="2c392-103">使用 PowerShell 來執行分段移轉至 Office 365</span><span class="sxs-lookup"><span data-stu-id="2c392-103">Use PowerShell to perform a staged migration to Office 365</span></span>

<span data-ttu-id="2c392-104">您可以使用分段移轉，逐漸將使用者信箱的內容從來源電子郵件系統移轉到 Office 365。</span><span class="sxs-lookup"><span data-stu-id="2c392-104">You can migrate the contents of user mailboxes from a source email system to Office 365 over time using a staged migration.</span></span>
  
<span data-ttu-id="2c392-105">This article walks you through the tasks involved with for a staged email migration using Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2c392-105">This article walks you through the tasks involved with for a staged email migration using Exchange Online PowerShell.</span></span> <span data-ttu-id="2c392-106">The topic, [What you need to know about a staged email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536487), gives you an overview of the migration process.</span><span class="sxs-lookup"><span data-stu-id="2c392-106">The topic, [What you need to know about a staged email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536487), gives you an overview of the migration process.</span></span> <span data-ttu-id="2c392-107">When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.</span><span class="sxs-lookup"><span data-stu-id="2c392-107">When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.</span></span>
  
> [!NOTE]
> <span data-ttu-id="2c392-108">You can also use the Exchange admin center to perform staged migration.</span><span class="sxs-lookup"><span data-stu-id="2c392-108">You can also use the Exchange admin center to perform staged migration.</span></span> <span data-ttu-id="2c392-109">See [Perform a staged migration of email to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536687).</span><span class="sxs-lookup"><span data-stu-id="2c392-109">See [Perform a staged migration of email to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536687).</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="2c392-110">開始之前有哪些須知？</span><span class="sxs-lookup"><span data-stu-id="2c392-110">What do you need to know before you begin?</span></span>

<span data-ttu-id="2c392-111">Estimated time to complete this task: 2-5 minutes to create a migration batch.</span><span class="sxs-lookup"><span data-stu-id="2c392-111">Estimated time to complete this task: 2-5 minutes to create a migration batch.</span></span> <span data-ttu-id="2c392-112">After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity.</span><span class="sxs-lookup"><span data-stu-id="2c392-112">After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity.</span></span> <span data-ttu-id="2c392-113">For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span><span class="sxs-lookup"><span data-stu-id="2c392-113">For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span></span>
  
<span data-ttu-id="2c392-114">You need to be assigned permissions before you can perform this procedure or procedures.</span><span class="sxs-lookup"><span data-stu-id="2c392-114">You need to be assigned permissions before you can perform this procedure or procedures.</span></span> <span data-ttu-id="2c392-115">To see what permissions you need, see the "Migration" entry in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span><span class="sxs-lookup"><span data-stu-id="2c392-115">To see what permissions you need, see the "Migration" entry in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span></span>
  
<span data-ttu-id="2c392-116">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session.</span><span class="sxs-lookup"><span data-stu-id="2c392-116">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session.</span></span> <span data-ttu-id="2c392-117">See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span><span class="sxs-lookup"><span data-stu-id="2c392-117">See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
  
<span data-ttu-id="2c392-118">若需要移轉命令的完整清單，請參閱[移動與移轉 Cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)。</span><span class="sxs-lookup"><span data-stu-id="2c392-118">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
## <a name="migration-steps"></a><span data-ttu-id="2c392-119">移轉步驟</span><span class="sxs-lookup"><span data-stu-id="2c392-119">Migration steps</span></span>

### <a name="step-1-prepare-for-a-staged-migration"></a><span data-ttu-id="2c392-120">步驟 1：準備分段移轉</span><span class="sxs-lookup"><span data-stu-id="2c392-120">Step 1: Prepare for a staged migration</span></span>

<span data-ttu-id="2c392-121">使用分段移轉將信箱移轉至 Office 365 之前，您必須對 Exchange 環境進行一些變更。</span><span class="sxs-lookup"><span data-stu-id="2c392-121">Before you migrate mailboxes to Office 365 by using a staged migration, there are a few changes you must make to your Exchange environment.</span></span>
  
 <span data-ttu-id="2c392-122">**Configure Outlook Anywhere on your on-premises Exchange Server** The email migration service uses Outlook Anywhere (also known as RPC over HTTP), to connect to your on-premises Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="2c392-122">**Configure Outlook Anywhere on your on-premises Exchange Server** The email migration service uses Outlook Anywhere (also known as RPC over HTTP), to connect to your on-premises Exchange Server.</span></span> <span data-ttu-id="2c392-123">For information about how to set up Outlook Anywhere for Exchange Server 2007, and Exchange 2003, see the following:</span><span class="sxs-lookup"><span data-stu-id="2c392-123">For information about how to set up Outlook Anywhere for Exchange Server 2007, and Exchange 2003, see the following:</span></span>
  
- [<span data-ttu-id="2c392-124">Exchange 2007：如何啟用 Outlook 無所不在</span><span class="sxs-lookup"><span data-stu-id="2c392-124">Exchange 2007: How to Enable Outlook Anywhere</span></span>](https://go.microsoft.com/fwlink/?LinkID=167210)
    
- [<span data-ttu-id="2c392-125">如何使用 Exchange 2003 設定 Outlook 無所不在</span><span class="sxs-lookup"><span data-stu-id="2c392-125">How to configure Outlook Anywhere with Exchange 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=167209)
    
> [!IMPORTANT]
> <span data-ttu-id="2c392-126">You must use a certificate issued by a trusted certification authority (CA) with your Outlook Anywhere configuration.</span><span class="sxs-lookup"><span data-stu-id="2c392-126">You must use a certificate issued by a trusted certification authority (CA) with your Outlook Anywhere configuration.</span></span> <span data-ttu-id="2c392-127">Outlook Anywhere can't be configured with a self-signed certificate.</span><span class="sxs-lookup"><span data-stu-id="2c392-127">Outlook Anywhere can't be configured with a self-signed certificate.</span></span> <span data-ttu-id="2c392-128">For more information, see [How to configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span><span class="sxs-lookup"><span data-stu-id="2c392-128">For more information, see [How to configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span></span> 
  
 <span data-ttu-id="2c392-129">**選擇性：確認可以使用 Outlook 無所不在**連線至您的 Exchange 組織 嘗試使用下列其中一種方法來測試連線設定。</span><span class="sxs-lookup"><span data-stu-id="2c392-129">**Optional: Verify that you can connect to your Exchange organization using Outlook Anywhere** Try one of the following methods to test your connection settings.</span></span>
  
- <span data-ttu-id="2c392-130">從公司網路之外使用 Outlook 連線至您的內部部署 Exchange 信箱。</span><span class="sxs-lookup"><span data-stu-id="2c392-130">Use Outlook from outside your corporate network to connect to your on-premises Exchange mailbox.</span></span>
    
- <span data-ttu-id="2c392-131">使用[Microsoft Remote Connectivity Analyzer](https://https://testconnectivity.microsoft.com/)來測試您的連線設定。</span><span class="sxs-lookup"><span data-stu-id="2c392-131">Use the [Microsoft Remote Connectivity Analyzer](https://https://testconnectivity.microsoft.com/) to test your connection settings.</span></span> <span data-ttu-id="2c392-132">使用 Outlook 無所不在 (RPC over HTTP) 或 Outlook 自動探索測試。</span><span class="sxs-lookup"><span data-stu-id="2c392-132">Use the Outlook Anywhere (RPC over HTTP) or Outlook Autodiscover tests.</span></span>
    
- <span data-ttu-id="2c392-133">在 Exchange Online PowerShell 中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="2c392-133">Run the following commands in Exchange Online PowerShell:</span></span>
    
  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 <span data-ttu-id="2c392-134">**Set permissions** The on-premises user account that you use to connect to your on-premises Exchange organization (also called the migration administrator) must have the necessary permissions to access the on-premises mailboxes that you want to migrate to Office 365.</span><span class="sxs-lookup"><span data-stu-id="2c392-134">**Set permissions** The on-premises user account that you use to connect to your on-premises Exchange organization (also called the migration administrator) must have the necessary permissions to access the on-premises mailboxes that you want to migrate to Office 365.</span></span> <span data-ttu-id="2c392-135">This user account is used when you connect to your email system by creating a migration endpoint later in this procedure ([Step 3: Create a migration endpoint](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint) ).</span><span class="sxs-lookup"><span data-stu-id="2c392-135">This user account is used when you connect to your email system by creating a migration endpoint later in this procedure ([Step 3: Create a migration endpoint](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint) ).</span></span>
  
<span data-ttu-id="2c392-136">若要移轉信箱，系統管理員必須具備下列其中一組權限：</span><span class="sxs-lookup"><span data-stu-id="2c392-136">To migrate the mailboxes, the admin must have one of the following permission sets:</span></span>
  
- <span data-ttu-id="2c392-137">屬於內部部署組織中 Active Directory 內的 **Domain Admins** 群組成員。</span><span class="sxs-lookup"><span data-stu-id="2c392-137">Be a member of the **Domain Admins** group in Active Directory in the on-premises organization.</span></span>
    
    <span data-ttu-id="2c392-138">或</span><span class="sxs-lookup"><span data-stu-id="2c392-138">or</span></span>
    
- <span data-ttu-id="2c392-139">獲得每個內部部署信箱的 **FullAccess** 權限，以及用來修改內部部署使用者帳戶的 **TargetAddress** 內容的 **WriteProperty** 權限。</span><span class="sxs-lookup"><span data-stu-id="2c392-139">Be assigned the **FullAccess** permission for each on-premises mailbox and the **WriteProperty** permission to modify the **TargetAddress** property on the on-premises user accounts.</span></span>
    
    <span data-ttu-id="2c392-140">或 </span><span class="sxs-lookup"><span data-stu-id="2c392-140">or</span></span>
    
- <span data-ttu-id="2c392-141">獲得儲存使用者信箱的內部部署信箱資料庫的 **Receive As** 權限，以及用來修改內部部署使用者帳戶的 **TargetAddress** 內容的 **WriteProperty** 權限。</span><span class="sxs-lookup"><span data-stu-id="2c392-141">Be assigned the **Receive As** permission on the on-premises mailbox database that stores user mailboxes and the **WriteProperty** permission to modify the **TargetAddress** property on the on-premises user accounts.</span></span>
    
<span data-ttu-id="2c392-142">如需如何設定這些權限的指示，請參閱[指派可將信箱移轉至 Office 365 的權限](https://go.microsoft.com/fwlink/?LinkId=521656)。</span><span class="sxs-lookup"><span data-stu-id="2c392-142">For instructions about how to set these permissions, see [Assign permissions to migrate mailboxes to Office 365](https://go.microsoft.com/fwlink/?LinkId=521656).</span></span>
  
 <span data-ttu-id="2c392-143">**Disable Unified Messaging (UM)** If UM is turned on for the on-premises mailboxes you're migrating, turn off UM before migration.</span><span class="sxs-lookup"><span data-stu-id="2c392-143">**Disable Unified Messaging (UM)** If UM is turned on for the on-premises mailboxes you're migrating, turn off UM before migration.</span></span> <span data-ttu-id="2c392-144">Turn on UM for the mailboxes after migration is complete.</span><span class="sxs-lookup"><span data-stu-id="2c392-144">Turn on UM for the mailboxes after migration is complete.</span></span> <span data-ttu-id="2c392-145">For how-to steps, see[disable unified messaging](https://go.microsoft.com/fwlink/?LinkId=521891).</span><span class="sxs-lookup"><span data-stu-id="2c392-145">For how-to steps, see[disable unified messaging](https://go.microsoft.com/fwlink/?LinkId=521891).</span></span>
  
 <span data-ttu-id="2c392-146">**Use directory synchronization to create new users in Office 365.**</span><span class="sxs-lookup"><span data-stu-id="2c392-146">**Use directory synchronization to create new users in Office 365.**</span></span> <span data-ttu-id="2c392-147">You use directory synchronization to create all the on-premises users in your Office 365 organization.</span><span class="sxs-lookup"><span data-stu-id="2c392-147">You use directory synchronization to create all the on-premises users in your Office 365 organization.</span></span>
  
<span data-ttu-id="2c392-148">You need to license the users after they're created.</span><span class="sxs-lookup"><span data-stu-id="2c392-148">You need to license the users after they're created.</span></span> <span data-ttu-id="2c392-149">You have 30 days to add licenses after the users are created.</span><span class="sxs-lookup"><span data-stu-id="2c392-149">You have 30 days to add licenses after the users are created.</span></span> <span data-ttu-id="2c392-150">For steps to add licenses, see [Step 8: Complete post-migration tasks](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration).</span><span class="sxs-lookup"><span data-stu-id="2c392-150">For steps to add licenses, see [Step 8: Complete post-migration tasks](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration).</span></span>
  
 <span data-ttu-id="2c392-151">您可以使用 Microsoft Azure Active Directory （Azure AD）同步處理工具或 Microsoft Azure AD Sync 服務同步處理，並在 Office 365 中建立內部部署使用者。</span><span class="sxs-lookup"><span data-stu-id="2c392-151">You can use either the Microsoft Azure Active Directory (Azure AD) Synchronization Tool or the Microsoft Azure AD Sync Services  to synchronize and create your on-premises users in Office 365.</span></span> <span data-ttu-id="2c392-152">將信箱移轉至 Office 365 之後，您需要管理內部部署組織中的使用者帳戶，這些帳戶會與您的 Office 365 組織進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="2c392-152">After mailboxes are migrated to Office 365, you manage user accounts in your on-premises organization, and they're synchronized with your Office 365 organization.</span></span> <span data-ttu-id="2c392-153">如需詳細資訊，請參閱[目錄整合](https://go.microsoft.com/fwlink/?LinkId=521788)。</span><span class="sxs-lookup"><span data-stu-id="2c392-153">For more information, see[Directory Integration](https://go.microsoft.com/fwlink/?LinkId=521788) .</span></span>
  
### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a><span data-ttu-id="2c392-154">步驟 2：建立分段移轉批次所需的 CSV 檔案</span><span class="sxs-lookup"><span data-stu-id="2c392-154">Step 2: Create a CSV file for a staged migration batch</span></span>

<span data-ttu-id="2c392-155">After you identify the users whose on-premises mailboxes you want to migrate to Office 365, you use a comma separated value (CSV ) file to create a migration batch.</span><span class="sxs-lookup"><span data-stu-id="2c392-155">After you identify the users whose on-premises mailboxes you want to migrate to Office 365, you use a comma separated value (CSV ) file to create a migration batch.</span></span> <span data-ttu-id="2c392-156">Each row in the CSV file—used by Office 365 to run the migration—contains information about an on-premises mailbox.</span><span class="sxs-lookup"><span data-stu-id="2c392-156">Each row in the CSV file—used by Office 365 to run the migration—contains information about an on-premises mailbox.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="2c392-157">There isn't a limit for the number of mailboxes that you can migrate to Office 365 using a staged migration.</span><span class="sxs-lookup"><span data-stu-id="2c392-157">There isn't a limit for the number of mailboxes that you can migrate to Office 365 using a staged migration.</span></span> <span data-ttu-id="2c392-158">The CSV file for a migration batch can contain a maximum of 2,000 rows.</span><span class="sxs-lookup"><span data-stu-id="2c392-158">The CSV file for a migration batch can contain a maximum of 2,000 rows.</span></span> <span data-ttu-id="2c392-159">To migrate more than 2,000 mailboxes, create additional CSV files and use each file to create a new migration batch.</span><span class="sxs-lookup"><span data-stu-id="2c392-159">To migrate more than 2,000 mailboxes, create additional CSV files and use each file to create a new migration batch.</span></span> 
  
 <span data-ttu-id="2c392-160">**支援的屬性**</span><span class="sxs-lookup"><span data-stu-id="2c392-160">**Supported attributes**</span></span>
  
<span data-ttu-id="2c392-161">The CSV file for a staged migration supports the following three attributes.</span><span class="sxs-lookup"><span data-stu-id="2c392-161">The CSV file for a staged migration supports the following three attributes.</span></span> <span data-ttu-id="2c392-162">Each row in the CSV file corresponds to a mailbox and must contain a value for each of these attributes.</span><span class="sxs-lookup"><span data-stu-id="2c392-162">Each row in the CSV file corresponds to a mailbox and must contain a value for each of these attributes.</span></span>
  
|<span data-ttu-id="2c392-163">**屬性**</span><span class="sxs-lookup"><span data-stu-id="2c392-163">**Attribute**</span></span>|<span data-ttu-id="2c392-164">**描述**</span><span class="sxs-lookup"><span data-stu-id="2c392-164">**Description**</span></span>|<span data-ttu-id="2c392-165">**Required?**</span><span class="sxs-lookup"><span data-stu-id="2c392-165">**Required?**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="2c392-166">EmailAddress</span><span class="sxs-lookup"><span data-stu-id="2c392-166">EmailAddress</span></span>  <br/> |<span data-ttu-id="2c392-167">指定內部部署信箱的主要 SMTP 電子郵件地址，例如 pilarp@contoso.com。</span><span class="sxs-lookup"><span data-stu-id="2c392-167">Specifies the primary SMTP email address, for example, pilarp@contoso.com, for on-premises mailboxes.</span></span>  <br/> <span data-ttu-id="2c392-168">Use the primary SMTP address for on-premises mailboxes and not user IDs from the Office 365.</span><span class="sxs-lookup"><span data-stu-id="2c392-168">Use the primary SMTP address for on-premises mailboxes and not user IDs from the Office 365.</span></span> <span data-ttu-id="2c392-169">For example, if the on-premises domain is named contoso.com but the Office 365 email domain is named service.contoso.com, you would use the contoso.com domain name for email addresses in the CSV file.</span><span class="sxs-lookup"><span data-stu-id="2c392-169">For example, if the on-premises domain is named contoso.com but the Office 365 email domain is named service.contoso.com, you would use the contoso.com domain name for email addresses in the CSV file.</span></span>  <br/> |<span data-ttu-id="2c392-170">必要</span><span class="sxs-lookup"><span data-stu-id="2c392-170">Required</span></span>  <br/> |
|<span data-ttu-id="2c392-171">密碼</span><span class="sxs-lookup"><span data-stu-id="2c392-171">Password</span></span>  <br/> |<span data-ttu-id="2c392-172">The password to be set for the new Office 365 mailbox.</span><span class="sxs-lookup"><span data-stu-id="2c392-172">The password to be set for the new Office 365 mailbox.</span></span> <span data-ttu-id="2c392-173">Any password restrictions that are applied to your Office 365 organization also apply to the passwords included in the CSV file.</span><span class="sxs-lookup"><span data-stu-id="2c392-173">Any password restrictions that are applied to your Office 365 organization also apply to the passwords included in the CSV file.</span></span>  <br/> |<span data-ttu-id="2c392-174">選用</span><span class="sxs-lookup"><span data-stu-id="2c392-174">Optional</span></span>  <br/> |
|<span data-ttu-id="2c392-175">ForceChangePassword</span><span class="sxs-lookup"><span data-stu-id="2c392-175">ForceChangePassword</span></span>  <br/> |<span data-ttu-id="2c392-176">Specifies whether a user must change the password the first time they sign in to their new Office 365 mailbox.</span><span class="sxs-lookup"><span data-stu-id="2c392-176">Specifies whether a user must change the password the first time they sign in to their new Office 365 mailbox.</span></span> <span data-ttu-id="2c392-177">Use **True** or **False** for the value of this parameter.</span><span class="sxs-lookup"><span data-stu-id="2c392-177">Use **True** or **False** for the value of this parameter.</span></span> <br/> <span data-ttu-id="2c392-178">> [!NOTE]> 如果您已在內部部署組織中部署 Active Directory Federation Services (AD FS) 或更新版本來實作單一登入 (SSO) 解決方案，則必須使用 **False** 作為 **ForceChangePassword** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="2c392-178">> [!NOTE]> If you've implemented a single sign-on (SSO) solution by deploying Active Directory Federation Services (AD FS) or greater in your on-premises organization, you must use **False** for the value of the **ForceChangePassword** attribute.</span></span>          |<span data-ttu-id="2c392-179">選用</span><span class="sxs-lookup"><span data-stu-id="2c392-179">Optional</span></span>  <br/> |
   
 <span data-ttu-id="2c392-180">**CSV 檔案格式**</span><span class="sxs-lookup"><span data-stu-id="2c392-180">**CSV file format**</span></span>
  
<span data-ttu-id="2c392-181">Here's an example of the format for the CSV file.</span><span class="sxs-lookup"><span data-stu-id="2c392-181">Here's an example of the format for the CSV file.</span></span> <span data-ttu-id="2c392-182">In this example, three on-premises mailboxes are migrated to Office 365.</span><span class="sxs-lookup"><span data-stu-id="2c392-182">In this example, three on-premises mailboxes are migrated to Office 365.</span></span>
  
<span data-ttu-id="2c392-183">The first row, or header row, of the CSV file lists the names of the attributes, or fields, specified in the rows that follow.</span><span class="sxs-lookup"><span data-stu-id="2c392-183">The first row, or header row, of the CSV file lists the names of the attributes, or fields, specified in the rows that follow.</span></span> <span data-ttu-id="2c392-184">Each attribute name is separated by a comma.</span><span class="sxs-lookup"><span data-stu-id="2c392-184">Each attribute name is separated by a comma.</span></span>
  
```powershell
EmailAddress,Password,ForceChangePassword 
pilarp@contoso.com,Pa$$w0rd,False 
tobyn@contoso.com,Pa$$w0rd,False 
briant@contoso.com,Pa$$w0rd,False 
```

<span data-ttu-id="2c392-185">Each row under the header row represents one user and supplies the information that will be used to migrate the user's mailbox.</span><span class="sxs-lookup"><span data-stu-id="2c392-185">Each row under the header row represents one user and supplies the information that will be used to migrate the user's mailbox.</span></span> <span data-ttu-id="2c392-186">The attribute values in each row must be in the same order as the attribute names in the header row.</span><span class="sxs-lookup"><span data-stu-id="2c392-186">The attribute values in each row must be in the same order as the attribute names in the header row.</span></span> 
  
<span data-ttu-id="2c392-187">Use any text editor, or an application like Excel , to create the CSV file.</span><span class="sxs-lookup"><span data-stu-id="2c392-187">Use any text editor, or an application like Excel , to create the CSV file.</span></span> <span data-ttu-id="2c392-188">Save the file as a .csv or .txt file.</span><span class="sxs-lookup"><span data-stu-id="2c392-188">Save the file as a .csv or .txt file.</span></span>
  
> [!NOTE]
> <span data-ttu-id="2c392-189">If the CSV file contains non-ASCII or special characters, save the CSV file with UTF-8 or other Unicode encoding.</span><span class="sxs-lookup"><span data-stu-id="2c392-189">If the CSV file contains non-ASCII or special characters, save the CSV file with UTF-8 or other Unicode encoding.</span></span> <span data-ttu-id="2c392-190">Depending on the application, saving the CSV file with UTF-8 or other Unicode encoding can be easier when the system locale of the computer matches the language used in the CSV file.</span><span class="sxs-lookup"><span data-stu-id="2c392-190">Depending on the application, saving the CSV file with UTF-8 or other Unicode encoding can be easier when the system locale of the computer matches the language used in the CSV file.</span></span> 
  
### <a name="step-3-create-a-migration-endpoint"></a><span data-ttu-id="2c392-191">步驟 3：建立移轉端點</span><span class="sxs-lookup"><span data-stu-id="2c392-191">Step 3: Create a migration endpoint</span></span>
<span data-ttu-id="2c392-192"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="2c392-192"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="2c392-193">To migrate email successfully, Office 365 needs to connect and communicate with the source email system.</span><span class="sxs-lookup"><span data-stu-id="2c392-193">To migrate email successfully, Office 365 needs to connect and communicate with the source email system.</span></span> <span data-ttu-id="2c392-194">To do this, Office 365 uses a migration endpoint.</span><span class="sxs-lookup"><span data-stu-id="2c392-194">To do this, Office 365 uses a migration endpoint.</span></span> <span data-ttu-id="2c392-195">To create an Outlook Anywhere migration endpoint by using PowerShell, for staged migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="2c392-195">To create an Outlook Anywhere migration endpoint by using PowerShell, for staged migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span></span> 
  
<span data-ttu-id="2c392-196">若需要移轉命令的完整清單，請參閱[移動與移轉 Cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)。</span><span class="sxs-lookup"><span data-stu-id="2c392-196">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="2c392-197">若要在 Exchange Online PowerShell 中建立名為 "StagedEndpoint" 的 Outlook 無所不在移轉端點，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="2c392-197">To create an Outlook Anywhere migration endpoint called "StagedEndpoint" in Exchange Online PowerShell, run the following commands:</span></span>
  
```powershell
$Credentials = Get-Credential
```

```powershell
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name StagedEndpoint -Autodiscover -EmailAddress administrator@contoso.com -Credentials $Credentials
```

<span data-ttu-id="2c392-198">如需 **New-MigrationEndpoint** Cmdlet 的詳細資訊，請參閱[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437)。</span><span class="sxs-lookup"><span data-stu-id="2c392-198">For more information about the **New-MigrationEndpoint** cmdlet, see[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).</span></span>
  
> [!NOTE]
> <span data-ttu-id="2c392-199">The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option.</span><span class="sxs-lookup"><span data-stu-id="2c392-199">The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option.</span></span> <span data-ttu-id="2c392-200">Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.</span><span class="sxs-lookup"><span data-stu-id="2c392-200">Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="2c392-201">確認是否正常運作</span><span class="sxs-lookup"><span data-stu-id="2c392-201">Verify it worked</span></span>

<span data-ttu-id="2c392-202">在 Exchange Online PowerShell 中執行下列命令來顯示 "StagedEndpoint" 移轉端點的資訊：</span><span class="sxs-lookup"><span data-stu-id="2c392-202">In Exchange Online PowerShell, run the following command to display information about the "StagedEndpoint" migration endpoint:</span></span>
  
```powershell
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a><span data-ttu-id="2c392-203">步驟 4：建立並啟動分段移轉批次</span><span class="sxs-lookup"><span data-stu-id="2c392-203">Step 4: Create and start a stage migration batch</span></span>
<span data-ttu-id="2c392-204"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="2c392-204"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="2c392-205">You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration.</span><span class="sxs-lookup"><span data-stu-id="2c392-205">You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration.</span></span> <span data-ttu-id="2c392-206">You can create a migration batch and start it automatically by including the _AutoStart_ parameter.</span><span class="sxs-lookup"><span data-stu-id="2c392-206">You can create a migration batch and start it automatically by including the _AutoStart_ parameter.</span></span> <span data-ttu-id="2c392-207">Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2c392-207">Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet.</span></span> <span data-ttu-id="2c392-208">This example creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step.</span><span class="sxs-lookup"><span data-stu-id="2c392-208">This example creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step.</span></span>
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

<span data-ttu-id="2c392-209">This example also creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step.</span><span class="sxs-lookup"><span data-stu-id="2c392-209">This example also creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step.</span></span> <span data-ttu-id="2c392-210">Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2c392-210">Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet.</span></span> <span data-ttu-id="2c392-211">As previously stated, only one cutover migration batch can exist at a time.</span><span class="sxs-lookup"><span data-stu-id="2c392-211">As previously stated, only one cutover migration batch can exist at a time.</span></span>
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint
```

#### <a name="verify-it-worked"></a><span data-ttu-id="2c392-212">確認是否正常運作</span><span class="sxs-lookup"><span data-stu-id="2c392-212">Verify it worked</span></span>

<span data-ttu-id="2c392-213">在 Exchange Online PowerShell 中執行下列命令來顯示 "StagedBatch1" 的資訊：</span><span class="sxs-lookup"><span data-stu-id="2c392-213">Run the following command in Exchange Online PowerShell to display information about the "StagedBatch1":</span></span>
  
```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List
```

<span data-ttu-id="2c392-214">您也可以執行下列命令來確認批次已啟動：</span><span class="sxs-lookup"><span data-stu-id="2c392-214">You can also verify that the batch has started by running the following command:</span></span>
  
```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List Status
```

<span data-ttu-id="2c392-215">如需 **Get-MigrationBatch** Cmdlet 的詳細資訊，請參閱[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441)。</span><span class="sxs-lookup"><span data-stu-id="2c392-215">For more information about the **Get-MigrationBatch** cmdlet, see[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span></span>
  
### <a name="step-5-convert-on-premises-mailboxes-to-mail-enabled-users"></a><span data-ttu-id="2c392-216">步驟 5：將內部部署信箱轉換成擁有郵件功能的使用者</span><span class="sxs-lookup"><span data-stu-id="2c392-216">Step 5: Convert on-premises mailboxes to mail-enabled users</span></span>
<span data-ttu-id="2c392-217"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="2c392-217"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="2c392-218">After you have successfully migrated a batch of mailboxes, you need some way to let users get to their mail.</span><span class="sxs-lookup"><span data-stu-id="2c392-218">After you have successfully migrated a batch of mailboxes, you need some way to let users get to their mail.</span></span> <span data-ttu-id="2c392-219">A user whose mailbox has been migrated now has both a mailbox on-premises and one in Office 365.</span><span class="sxs-lookup"><span data-stu-id="2c392-219">A user whose mailbox has been migrated now has both a mailbox on-premises and one in Office 365.</span></span> <span data-ttu-id="2c392-220">Users who have a mailbox in Office 365 will stop receiving new mail in their on-premises mailbox.</span><span class="sxs-lookup"><span data-stu-id="2c392-220">Users who have a mailbox in Office 365 will stop receiving new mail in their on-premises mailbox.</span></span> 
  
<span data-ttu-id="2c392-221">Because you are not done with your migrations, you are not yet ready to direct all users to Office 365 for their email.</span><span class="sxs-lookup"><span data-stu-id="2c392-221">Because you are not done with your migrations, you are not yet ready to direct all users to Office 365 for their email.</span></span> <span data-ttu-id="2c392-222">So what do you do for those people who have both?</span><span class="sxs-lookup"><span data-stu-id="2c392-222">So what do you do for those people who have both?</span></span> <span data-ttu-id="2c392-223">What you can do is change the on-premises mailboxes that you've already migrated to mail-enabled users.</span><span class="sxs-lookup"><span data-stu-id="2c392-223">What you can do is change the on-premises mailboxes that you've already migrated to mail-enabled users.</span></span> <span data-ttu-id="2c392-224">When you change from a mailbox to a mail-enabled user, you can direct the user to Office 365 for their email instead of going to their on-premises mailbox.</span><span class="sxs-lookup"><span data-stu-id="2c392-224">When you change from a mailbox to a mail-enabled user, you can direct the user to Office 365 for their email instead of going to their on-premises mailbox.</span></span> 
  
<span data-ttu-id="2c392-225">Another important reason to convert on-premises mailboxes to mail-enabled users is to retain proxy addresses from the Office 365 mailboxes by copying proxy addresses to the mail-enabled users.</span><span class="sxs-lookup"><span data-stu-id="2c392-225">Another important reason to convert on-premises mailboxes to mail-enabled users is to retain proxy addresses from the Office 365 mailboxes by copying proxy addresses to the mail-enabled users.</span></span> <span data-ttu-id="2c392-226">This lets you manage cloud-based users from your on-premises organization by using Active Directory.</span><span class="sxs-lookup"><span data-stu-id="2c392-226">This lets you manage cloud-based users from your on-premises organization by using Active Directory.</span></span> <span data-ttu-id="2c392-227">Also, if you decide to decommission your on-premises Exchange Server organization after all mailboxes are migrated to Office 365, the proxy addresses you've copied to the mail-enabled users will remain in your on-premises Active Directory.</span><span class="sxs-lookup"><span data-stu-id="2c392-227">Also, if you decide to decommission your on-premises Exchange Server organization after all mailboxes are migrated to Office 365, the proxy addresses you've copied to the mail-enabled users will remain in your on-premises Active Directory.</span></span>
    
### <a name="step-6-delete-a-staged-migration-batch"></a><span data-ttu-id="2c392-228">步驟 6：刪除分段移轉批次</span><span class="sxs-lookup"><span data-stu-id="2c392-228">Step 6: Delete a staged migration batch</span></span>
<span data-ttu-id="2c392-229"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="2c392-229"><a name="BK_Endpoint"> </a></span></span>

 <span data-ttu-id="2c392-230">After all mailboxes in a migration batch have been successfully migrated, and you've converted the on-premises mailboxes in the batch to mail-enabled users, you're ready to delete a staged migration batch.</span><span class="sxs-lookup"><span data-stu-id="2c392-230">After all mailboxes in a migration batch have been successfully migrated, and you've converted the on-premises mailboxes in the batch to mail-enabled users, you're ready to delete a staged migration batch.</span></span> <span data-ttu-id="2c392-231">Be sure to verify that mail is being forwarded to the Office 365 mailboxes in the migration batch.</span><span class="sxs-lookup"><span data-stu-id="2c392-231">Be sure to verify that mail is being forwarded to the Office 365 mailboxes in the migration batch.</span></span> <span data-ttu-id="2c392-232">When you delete a staged migration batch, the migration service cleans up any records related to the migration batch and deletes the migration batch.</span><span class="sxs-lookup"><span data-stu-id="2c392-232">When you delete a staged migration batch, the migration service cleans up any records related to the migration batch and deletes the migration batch.</span></span>
  
<span data-ttu-id="2c392-233">若要刪除 Exchange Online PowerShell 中的 "StagedBatch1" 移轉批次，請執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="2c392-233">To delete the "StagedBatch1" migration batch in Exchange Online PowerShell, run the following command.</span></span>
  
```powershell
Remove-MigrationBatch -Identity StagedBatch1
```

<span data-ttu-id="2c392-234">如需 **Remove-MigrationBatch** Cmdlet 的詳細資訊，請參閱[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481)。</span><span class="sxs-lookup"><span data-stu-id="2c392-234">For more information about the **Remove-MigrationBatch** cmdlet, see[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="2c392-235">確認是否正常運作</span><span class="sxs-lookup"><span data-stu-id="2c392-235">Verify it worked</span></span>

<span data-ttu-id="2c392-236">在 Exchange Online PowerShell 中執行下列命令來顯示 "IMAPBatch1" 的資訊：</span><span class="sxs-lookup"><span data-stu-id="2c392-236">Run the following command in Exchange Online PowerShell to display information about the "IMAPBatch1":</span></span>
  
```powershell
Get-MigrationBatch StagedBatch1
```

<span data-ttu-id="2c392-237">此命令會傳回狀態為 **Removing** 的移轉批次，或傳回錯誤，指出找不到移轉批次而需確認該批次是否已刪除。</span><span class="sxs-lookup"><span data-stu-id="2c392-237">The command will return either the migration batch with a status of **Removing**, or it will return an error stating that migration batch couldn't be found, verifying that the batch was deleted.</span></span>
  
<span data-ttu-id="2c392-238">如需 **Get-MigrationBatch** Cmdlet 的詳細資訊，請參閱[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441)。</span><span class="sxs-lookup"><span data-stu-id="2c392-238">For more information about the **Get-MigrationBatch** cmdlet, see[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span></span>
  
### <a name="step7-assign-licenses-to-office-365-users"></a><span data-ttu-id="2c392-239">步驟 7：指派授權給 Office 365 使用者</span><span class="sxs-lookup"><span data-stu-id="2c392-239">Step7: Assign licenses to Office 365 users</span></span>
<span data-ttu-id="2c392-240"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="2c392-240"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="2c392-241">藉由指派授權，為移轉的帳戶啟動 Office 365 使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="2c392-241">Activate Office 365 user accounts for the migrated accounts by assigning licenses.</span></span> <span data-ttu-id="2c392-242">如果您未指派授權，則當寬限期 (30 天) 結束時就會停用信箱。</span><span class="sxs-lookup"><span data-stu-id="2c392-242">If you don't assign a license, the mailbox is disabled when the grace period (30 days) ends.</span></span> <span data-ttu-id="2c392-243">若要在 Microsoft 365 系統管理中心中指派授權，請參閱[指派或解除指派商務用 Office 365 的授權](https://go.microsoft.com/fwlink/?LinkId=536681)。</span><span class="sxs-lookup"><span data-stu-id="2c392-243">To assign a license in the Microsoft 365 admin center, see [Assign or unassign licenses for Office 365 for business](https://go.microsoft.com/fwlink/?LinkId=536681).</span></span>
  
### <a name="step-8-complete-post-migration-tasks"></a><span data-ttu-id="2c392-244">步驟 8：完成移轉後工作</span><span class="sxs-lookup"><span data-stu-id="2c392-244">Step 8: Complete post-migration tasks</span></span>
<span data-ttu-id="2c392-245"><a name="BK_Postmigration"> </a></span><span class="sxs-lookup"><span data-stu-id="2c392-245"><a name="BK_Postmigration"> </a></span></span>

- <span data-ttu-id="2c392-246">**Create an Autodiscover DNS record so users can easily get to their mailboxes.**</span><span class="sxs-lookup"><span data-stu-id="2c392-246">**Create an Autodiscover DNS record so users can easily get to their mailboxes.**</span></span> <span data-ttu-id="2c392-247">After all on-premises mailboxes are migrated to Office 365, you can configure an Autodiscover DNS record for your Office 365 organization to enable users to easily connect to their new Office 365 mailboxes with Outlook and mobile clients.</span><span class="sxs-lookup"><span data-stu-id="2c392-247">After all on-premises mailboxes are migrated to Office 365, you can configure an Autodiscover DNS record for your Office 365 organization to enable users to easily connect to their new Office 365 mailboxes with Outlook and mobile clients.</span></span> <span data-ttu-id="2c392-248">This new Autodiscover DNS record has to use the same namespace that you're using for your Office 365 organization.</span><span class="sxs-lookup"><span data-stu-id="2c392-248">This new Autodiscover DNS record has to use the same namespace that you're using for your Office 365 organization.</span></span> <span data-ttu-id="2c392-249">For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="2c392-249">For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.</span></span>
    
    <span data-ttu-id="2c392-250">Office 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients.</span><span class="sxs-lookup"><span data-stu-id="2c392-250">Office 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients.</span></span> <span data-ttu-id="2c392-251">The Autodiscover CNAME record must contain the following information:</span><span class="sxs-lookup"><span data-stu-id="2c392-251">The Autodiscover CNAME record must contain the following information:</span></span>
    
  - <span data-ttu-id="2c392-252">**別名：** 自動探索</span><span class="sxs-lookup"><span data-stu-id="2c392-252">**Alias:** autodiscover</span></span>
    
  - <span data-ttu-id="2c392-253">**目標：** autodiscover.outlook.com</span><span class="sxs-lookup"><span data-stu-id="2c392-253">**Target:** autodiscover.outlook.com</span></span>
    
    <span data-ttu-id="2c392-254">如需詳細資訊，請參閱[管理 DNS 記錄時為 Office 365 建立 DNS 記錄](https://go.microsoft.com/fwlink/p/?LinkId=535028)。</span><span class="sxs-lookup"><span data-stu-id="2c392-254">For more information, see [Create DNS records for Office 365 when you manage your DNS records](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span></span>
    
- <span data-ttu-id="2c392-255">**Decommission on-premises Exchange servers.**</span><span class="sxs-lookup"><span data-stu-id="2c392-255">**Decommission on-premises Exchange servers.**</span></span> <span data-ttu-id="2c392-256">After you've verified that all email is being routed directly to the Office 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing an SSO solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.</span><span class="sxs-lookup"><span data-stu-id="2c392-256">After you've verified that all email is being routed directly to the Office 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing an SSO solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.</span></span>
    
    <span data-ttu-id="2c392-257">如需詳細資訊，請參閱下列各主題：</span><span class="sxs-lookup"><span data-stu-id="2c392-257">For more information, see the following:</span></span>
    
  - [<span data-ttu-id="2c392-258">修改及移除 Exchange 2010</span><span class="sxs-lookup"><span data-stu-id="2c392-258">Modify or Remove Exchange 2010</span></span>](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [<span data-ttu-id="2c392-259">如何移除 Exchange 2007 組織</span><span class="sxs-lookup"><span data-stu-id="2c392-259">How to Remove an Exchange 2007 Organization</span></span>](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [<span data-ttu-id="2c392-260">如何解除安裝 Exchange Server 2003</span><span class="sxs-lookup"><span data-stu-id="2c392-260">How to Uninstall Exchange Server 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=56561)
    

