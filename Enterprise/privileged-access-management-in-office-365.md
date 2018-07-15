---
title: 權限存取 Office 365 中的管理
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 7/13/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Strat_O365_IP
ms.custom: Ent_Solutions
ms.assetid: ''
description: 若要深入了解 Office 365 中的權限的存取管理功能使用本主題
ms.openlocfilehash: b2db3e16e53cca7deb2bf8fbff61b5b981f42fa6
ms.sourcegitcommit: b39b8ae3b4268d6475b54e2fdb62982b2c7d9943
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2018
ms.locfileid: "20319204"
---
# <a name="privileged-access-management-in-office-365"></a><span data-ttu-id="2414f-103">權限存取 Office 365 中的管理</span><span class="sxs-lookup"><span data-stu-id="2414f-103">Privileged access management in Office 365</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2414f-104">本主題涵蓋 beta 公開功能僅在 Office 365 E5 和進階規範 Sku 中目前可用的部署和設定指導。</span><span class="sxs-lookup"><span data-stu-id="2414f-104">This topic covers deployment and configuration guidance for public beta features only currently available in Office 365 E5 and Advanced Compliance SKUs.</span></span>

<span data-ttu-id="2414f-p101">特殊存取權限管理 Office 365 中讓更精細的存取權限的管理工作的控制權。 它可協助保護您的組織中可以使用現有的權限的管理員帳戶具有出位置的存取權機密資料或重要的組態設定的存取權的缺口。啟用權限的存取管理、 之後使用者需要要求剛剛-時間存取完成核准工作流程高度範圍且時間繫結到提高權限與權限工作。這提供使用者剛-充份-存取可執行工作，反之，而不致洩露機密資料或重要的組態設定。啟用 Office 365 中的權限的存取管理可讓您的組織操作以零出位置的權限，並提供一層的防禦措施弱點引起因為這類出位置管理存取。</span><span class="sxs-lookup"><span data-stu-id="2414f-p101">Privileged access management allows granular access control over privileged admin tasks in Office 365.  It can help protect your organization from breaches that may use existing privileged admin accounts with standing access to sensitive data or access to critical configuration settings. After enabling privileged access management, users will need to request just-in-time access to complete elevated and privileged tasks through an approval workflow that is highly scoped and time-bound. This gives users just-enough-access to perform the task at hand, without risking exposure of sensitive data or critical configuration settings. Enabling privileged access management in Office 365 will enable your organization to operate with zero standing privileges and provide a layer of defense against vulnerabilities arising because of such standing administrative access.</span></span> 

<span data-ttu-id="2414f-110">本主題將引導您透過啟用及設定 Office 365 組織中的權限的存取管理並做為參考指南要求、 核准、 和管理功能。</span><span class="sxs-lookup"><span data-stu-id="2414f-110">This topic will guide you through enabling and configuring privileged access management in your Office 365 organization and serve as a reference guide for requesting, approving, and managing the feature.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="2414f-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="2414f-111">Before you begin</span></span>

### <a name="limited-functionality"></a><span data-ttu-id="2414f-112">有限的功能</span><span class="sxs-lookup"><span data-stu-id="2414f-112">Limited functionality</span></span>
<span data-ttu-id="2414f-p102">Beta 公開期間特殊權限存取管理功能可用只能透過 Office 365 中的[Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) 。權限存取管理涵蓋之 Exchange 管理指令程式層級的工作定義。在未來 Office 365 發行、 權限的存取功能可透過系統入口網站與會涵蓋其他 Office 365 工作負載服務。</span><span class="sxs-lookup"><span data-stu-id="2414f-p102">During the public beta, privileged access management features are only available through [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) in Office 365. Privileged access management covers the task definitions at the level of Exchange management cmdlets. In future Office 365 releases, privileged access features will be available through the admin portal and will cover other Office 365 workloads services.</span></span>

### <a name="connecting-to-exchange-online-powershell"></a><span data-ttu-id="2414f-116">連線至 Exchange Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="2414f-116">Connecting to Exchange Online PowerShell</span></span>
<span data-ttu-id="2414f-117">本主題中的設定步驟會引導您透過啟用及使用 Office 365 使用 Exchange Online PowerShell 中的權限的存取。</span><span class="sxs-lookup"><span data-stu-id="2414f-117">The configuration steps in this topic will walk you through enabling and using privileged access in Office 365 using Exchange Online PowerShell.</span></span> 

<span data-ttu-id="2414f-118">請遵循步驟來啟用及設定貴組織的權限的存取 Office 365 認證以連線至 Exchange Online PowerShell[連線至 Exchange Online PowerShell 中使用多重要素驗證](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell?view=exchange-ps)。</span><span class="sxs-lookup"><span data-stu-id="2414f-118">Follow the steps in [Connect to Exchange Online PowerShell using Multi-Factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell?view=exchange-ps) to connect to Exchange Online PowerShell with your Office 365 credentials to enable and configure privileged access for your organization.</span></span>

> [!NOTE]
> <span data-ttu-id="2414f-p103">您不需要啟用的 Office 365 組織使用的步驟來連線至 Exchange Online PowerShell 時啟用權限的存取多重要素驗證。以多重要素驗證連線建立簽署您要求的權限存取所使用的 OAuth 權杖。</span><span class="sxs-lookup"><span data-stu-id="2414f-p103">You do not need to enable multi-factor authentication for your Office 365 organization to use the steps to enable privileged access while connecting to Exchange Online PowerShell. Connecting with multi-factor authentication creates an OAuth token that is used by privileged access for signing your requests.</span></span>

## <a name="enable-and-configure-privileged-access-management"></a><span data-ttu-id="2414f-121">啟用並設定權限的存取管理</span><span class="sxs-lookup"><span data-stu-id="2414f-121">Enable and configure privileged access management</span></span>

### <a name="step-1---create-an-approvers-group"></a><span data-ttu-id="2414f-122">步驟 1-建立核准者群組</span><span class="sxs-lookup"><span data-stu-id="2414f-122">Step 1 - Create an approver's group</span></span>
<span data-ttu-id="2414f-p104">從 Office 365 系統管理入口網站，選取 [**群組** > **加入群組**]，然後建立啟用郵件功能的安全性群組的預設權限存取核准者。完成後，選取 [**新增**] 以建立並儲存核准者群組。</span><span class="sxs-lookup"><span data-stu-id="2414f-p104">From Office 365 Admin Portal, select **Groups** > **Add a group**, then create a mail enabled security group for the default privileged access approvers. When complete, select **Add** to create and save the approver group.</span></span>

![Office 365 系統入口網站的權限的存取核准者畫面](images/privileged-access-approvers-ui.png)

> [!NOTE] 
> <span data-ttu-id="2414f-p105">在此階段中，只有系統管理存取權的使用者可以核准來自 Office 365 造就存取要求。在未來任何已核准者的群組之一部分的使用者將能夠核准存取要求。</span><span class="sxs-lookup"><span data-stu-id="2414f-p105">At this time, only users with administrative access are allowed to approve requests from Office 365 priviledged access. In future any user who is part of the Approvers’ group will be able to approve access requests.</span></span>

### <a name="step-2---enable-privileged-access-in-office-365"></a><span data-ttu-id="2414f-128">步驟 2-啟用 Office 365 中的權限的存取</span><span class="sxs-lookup"><span data-stu-id="2414f-128">Step 2 - Enable privileged access in Office 365</span></span>
<span data-ttu-id="2414f-129">權限的存取必須明確開啟與預設核准者群組且包含一組您想要排除的權限的存取管理存取控制的系統帳戶。</span><span class="sxs-lookup"><span data-stu-id="2414f-129">Privileged access needs to be explicitly turned on with the default approver group and including a set of system accounts that you’d want to be excluded from the privileged access management access control.</span></span> 

<span data-ttu-id="2414f-130">若要啟用權限的存取及核准者群組指派 Exchange Online PowerShell 中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="2414f-130">Run the following command in Exchange Online PowerShell to enable privileged access and to assign the approver's group:</span></span>
```
Enable-ElevatedAccessControl -AdminGroup '<default approver group>' -SystemAccounts @('<systemAccountUPN1>','<systemAccountUPN2>')
```
<span data-ttu-id="2414f-131">範例：</span><span class="sxs-lookup"><span data-stu-id="2414f-131">Example:</span></span>
```
Enable-ElevatedAccessControl -AdminGroup 'pamapprovers@fabrikam.onmicrosoft.com' -SystemAccounts @('sys1@fabrikamorg.onmicrosoft.com', sys2@fabrikamorg.onmicrosoft.com')
```

> [!NOTE]
> <span data-ttu-id="2414f-132">功能可供以確保您的組織內特定 automations 系統帳戶可以不相依性運作權限存取、 但還是建議也是這類排除是例外以及那些允許應該核准和稽核定期。</span><span class="sxs-lookup"><span data-stu-id="2414f-132">System accounts feature is made available to ensure certain automations within your organizations can work without dependency on privileged access, however it is recommended that such exclusions be exceptional and those allowed should be approved and audited regularly.</span></span>

### <a name="step-3---create-an-approval-policy"></a><span data-ttu-id="2414f-133">步驟 3-建立核准原則</span><span class="sxs-lookup"><span data-stu-id="2414f-133">Step 3 - Create an approval policy</span></span>
<span data-ttu-id="2414f-p106">核准原則可讓您定義在個別工作設定範圍的特定核准需求。核准類型選項會**自動**或**手動**。</span><span class="sxs-lookup"><span data-stu-id="2414f-p106">An approval policy allows you to define the specific approval requirements scoped at individual tasks. The approval type options are **Auto** or **Manual**.</span></span> 

<span data-ttu-id="2414f-136">執行下列命令在 Exchange Online PowerShell 來定義核准原則：</span><span class="sxs-lookup"><span data-stu-id="2414f-136">Run the following command in Exchange Online PowerShell to define an approval policy:</span></span>
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\<exchange management cmdlet name>' -ApprovalType <Manual, Auto> -ApproverGroup '<default/custom approver group>'
```
<span data-ttu-id="2414f-137">範例：</span><span class="sxs-lookup"><span data-stu-id="2414f-137">Example:</span></span>
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\New-MoveRequest' -ApprovalType Manual -ApproverGroup 'mbmanagers@fabrikamorg.onmicrosoft.com'
```

## <a name="using-privileged-access-in-your-office-365-organization"></a><span data-ttu-id="2414f-138">在 Office 365 組織中使用特殊權限的存取</span><span class="sxs-lookup"><span data-stu-id="2414f-138">Using privileged access in your Office 365 organization</span></span>

### <a name="requesting-elevation-authorization-to-execute-tasks"></a><span data-ttu-id="2414f-139">若要執行的工作要求的權限提高授權</span><span class="sxs-lookup"><span data-stu-id="2414f-139">Requesting elevation authorization to execute tasks</span></span>
<span data-ttu-id="2414f-p107">一次啟用的權限存取需要核准在執行任何具有相關聯的核准原則所定義的工作。使用者執行工作包含在需要核准原則必須要求並以具有執行工作所需的權限授與存取權核准。</span><span class="sxs-lookup"><span data-stu-id="2414f-p107">Once enabled, privileged access requires approvals for executing any task that has an associated approval policy defined. Users needing to execute tasks included in the an approval policy must request and be granted access approval in order to have permissions necessary to execute the task.</span></span>

<span data-ttu-id="2414f-142">執行下列命令在 Exchange Online PowerShell 建立並送出至核准者群組核准要求：</span><span class="sxs-lookup"><span data-stu-id="2414f-142">Run the following command in Exchange Online PowerShell to create and submit an approval request to the approver's group:</span></span>
```
New-ElevatedAccessRequest -Task 'Exchange\<exchange management cmdlet name>' -Reason '<appropriate reason>' -DurationHours <duration in hours>
```
<span data-ttu-id="2414f-143">範例：</span><span class="sxs-lookup"><span data-stu-id="2414f-143">Example:</span></span>
```
New-ElevatedAccessRequest -Task 'Exchange\New-MoveRequest' -Reason 'Attempting to fix the user mailbox error' -DurationHours 4
```
### <a name="view-status-of-elevation-requests"></a><span data-ttu-id="2414f-144">檢視權限提高要求的狀態</span><span class="sxs-lookup"><span data-stu-id="2414f-144">View status of elevation requests</span></span>
<span data-ttu-id="2414f-145">建立核准要求之後，可以要求識別碼使用關聯檢閱提高權限要求狀態</span><span class="sxs-lookup"><span data-stu-id="2414f-145">After an approval request is created, elevation request status can be reviewed using the associated with request ID.</span></span>

<span data-ttu-id="2414f-146">執行下列命令在 Exchange Online PowerShell 來檢視特定要求識別碼核准要求狀態：</span><span class="sxs-lookup"><span data-stu-id="2414f-146">Run the following command in Exchange Online PowerShell to view a approval request status for a specific request ID:</span></span>
```
Get-ElevatedAccessRequest -Identity <request ID> | select RequestStatus
```
<span data-ttu-id="2414f-147">範例：</span><span class="sxs-lookup"><span data-stu-id="2414f-147">Example:</span></span>
```
Get-ElevatedAccessRequest -Identity 28560ed0-419d-4cc3-8f5b-603911cbd450 | select RequestStatus
```

### <a name="approving-an-elevation-authorization-request"></a><span data-ttu-id="2414f-148">核准權限提高授權要求</span><span class="sxs-lookup"><span data-stu-id="2414f-148">Approving an elevation authorization request</span></span>
<span data-ttu-id="2414f-149">相關的核准者群組的成員時建立核准要求時，會收到的電子郵件通知與可核准要求識別碼相關聯的要求</span><span class="sxs-lookup"><span data-stu-id="2414f-149">When an approval request is created, members of the relevant approver group will receive an email notification and can approve the request associated with the request ID.</span></span> 

<span data-ttu-id="2414f-150">執行下列命令在 Exchange Online PowerShell 核准權限提高授權要求：</span><span class="sxs-lookup"><span data-stu-id="2414f-150">Run the following command in Exchange Online PowerShell to approve an elevation authorization request:</span></span>
```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
<span data-ttu-id="2414f-151">範例：</span><span class="sxs-lookup"><span data-stu-id="2414f-151">Example:</span></span>
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```
### <a name="denying-an-elevation-authorization-request"></a><span data-ttu-id="2414f-152">拒絕權限提高授權要求</span><span class="sxs-lookup"><span data-stu-id="2414f-152">Denying an elevation authorization request</span></span>
<span data-ttu-id="2414f-153">當建立核准要求時，相關的核准者群組的成員可以拒絕要求識別碼相關聯的要求</span><span class="sxs-lookup"><span data-stu-id="2414f-153">When an approval request is created, members of the relevant approver group can deny the request associated with the request ID.</span></span> 

<span data-ttu-id="2414f-154">執行下列命令在 Exchange Online PowerShell 拒絕權限提高授權要求：</span><span class="sxs-lookup"><span data-stu-id="2414f-154">Run the following command in Exchange Online PowerShell to deny an elevation authorization request:</span></span>
```
Deny-ElevatedAccessRequest -RequestId <request id> -Comment '<denial comment>'
```
<span data-ttu-id="2414f-155">範例：</span><span class="sxs-lookup"><span data-stu-id="2414f-155">Example:</span></span>
```
Deny-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<denial comment>'
```

### <a name="running-the-task"></a><span data-ttu-id="2414f-156">執行工作</span><span class="sxs-lookup"><span data-stu-id="2414f-156">Running the task</span></span>
<span data-ttu-id="2414f-p108">會授與核准之後，要求使用者可執行預定的工作及權限的存取將授權及使用者代理執行工作。核准保持有效的要求期間 （預設持續時間為 4 小時） 的期間要求者可執行預定的任務多次。所有這類執行記錄且可供安全性及規範稽核。</span><span class="sxs-lookup"><span data-stu-id="2414f-p108">After approval is granted, the requesting user can execute the intended task and privileged access will authorize and execute the task on users’ behalf. The approval remains valid for the requested duration (default duration is 4 hours), during which the requester can execute the intended task multiple times. All such executions are logged and made available for security and compliance auditing.</span></span> 

### <a name="disable-privileged-access-in-office-365"></a><span data-ttu-id="2414f-160">停用 Office 365 中的權限的存取</span><span class="sxs-lookup"><span data-stu-id="2414f-160">Disable privileged access in Office 365</span></span>
<span data-ttu-id="2414f-p109">必要時，您可以停用 Office 365 中的權限的存取管理。停用權限存取不會刪除任何相關聯的核准原則或核准者群組。</span><span class="sxs-lookup"><span data-stu-id="2414f-p109">If needed, you can disable privileged access management in Office 365. Disabling privileged access does not delete any associated approval policies or approver groups.</span></span>

<span data-ttu-id="2414f-163">執行下列命令在 Exchange Online Powershell 來停用權限的存取：</span><span class="sxs-lookup"><span data-stu-id="2414f-163">Run the following command in Exchange Online Powershell to disable privileged access:</span></span>

```
Disable-ElevatedAccessControl
```
## <a name="managed-access-to-microsoft-graph-in-microsoft-azure"></a><span data-ttu-id="2414f-164">受管理的 Microsoft Graph in Microsoft Azure 存取</span><span class="sxs-lookup"><span data-stu-id="2414f-164">Managed access to Microsoft Graph in Microsoft Azure</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2414f-165">本節涵蓋 beta 公開 Microsoft Graph 功能僅在 Office 365 E5 和進階規範 Sku 中目前可用的部署和設定指導。</span><span class="sxs-lookup"><span data-stu-id="2414f-165">This section covers deployment and configuration guidance for a public beta Microsoft Graph feature only currently available in Office 365 E5 and Advanced Compliance SKUs.</span></span>

<span data-ttu-id="2414f-p110">受管理的存取權 Microsoft Graph in Microsoft Azure 是可幫助組織執行控制其 Office 365 資料細微層級的服務。此 system 允許應用程式開發人員創造見解與該資料。</span><span class="sxs-lookup"><span data-stu-id="2414f-p110">Managed access to Microsoft Graph in Microsoft Azure is a service that helps organizations exert a granular level of control over their Office 365 data. This system allows application developers to forge insights with that data.</span></span> 

<span data-ttu-id="2414f-p111">此系統使用特殊權限的 Office 365 存取來判斷提示透過其核准工作流程、 允許範圍與管理負責監督的 Office 365 資料存取其資料的控制權。應用程式在安裝好且需要存取 Office 365 資料甚至要求的資料。</span><span class="sxs-lookup"><span data-stu-id="2414f-p111">This system uses Office 365 privileged access to assert control over their data through its approval workflow, allowing scoped access to Office 365 data with admin oversight. Requests for data come in when applications are installed and require access to Office 365 data.</span></span>

### <a name="view-request-details"></a><span data-ttu-id="2414f-170">檢視要求詳細資料</span><span class="sxs-lookup"><span data-stu-id="2414f-170">View request details</span></span>
<span data-ttu-id="2414f-171">檢視 Office 365 資料存取權要求的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="2414f-171">View details of the access requests for Office 365 data.</span></span>

<span data-ttu-id="2414f-172">執行下列命令在 Exchange Online Powershell 來檢視資料要求：</span><span class="sxs-lookup"><span data-stu-id="2414f-172">Run the following command in Exchange Online Powershell to view data requests:</span></span>
```
Get-ElevatedAccessRequest | where {$_.RequestedAccess -like '*Data Access Request*'} | select RequestorUPN, Service, RequestedAccess | fl
```
<span data-ttu-id="2414f-173">範例輸出：</span><span class="sxs-lookup"><span data-stu-id="2414f-173">Example output:</span></span>
```
RequestorUPN    : admin@contoso.com
Service         : Office365
RequestedAccess : Data Access Request
```

### <a name="approve-data-access-requests"></a><span data-ttu-id="2414f-174">核准資料存取權要求</span><span class="sxs-lookup"><span data-stu-id="2414f-174">Approve data access requests</span></span>
<span data-ttu-id="2414f-175">所有的資料存取權要求可以核准透過標準的權限的存取核准指令程式。</span><span class="sxs-lookup"><span data-stu-id="2414f-175">All data access requests can be approved through the standard privileged access approval cmdlets.</span></span>

<span data-ttu-id="2414f-176">執行下列命令在 Exchange Online Powershell 核准所有資料要求特定的地方：</span><span class="sxs-lookup"><span data-stu-id="2414f-176">Run the following command in Exchange Online Powershell to approve all data requests for specific requestor:</span></span>

```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
<span data-ttu-id="2414f-177">範例：</span><span class="sxs-lookup"><span data-stu-id="2414f-177">Example:</span></span>
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```

## <a name="getting-help-and-providing-feedback"></a><span data-ttu-id="2414f-178">取得說明並提供意見反應</span><span class="sxs-lookup"><span data-stu-id="2414f-178">Getting help and providing feedback</span></span>
<span data-ttu-id="2414f-p112">我們意識期間 beta 公開您可能會無意中偶發性的 bug 或有意見反應及建議在我們可以提升權限的存取管理的方式。我們值意見反應及鼓勵您與我們分享：</span><span class="sxs-lookup"><span data-stu-id="2414f-p112">We recognize that during the public beta you may come across an occasional bug or have feedback and suggestions on how we can improve privileged access management. We value your feedback and encourage you to share it with us:</span></span>
- <span data-ttu-id="2414f-181">張貼意見反應 ad 建議[Office 預覽 Yammer 群組](https://www.yammer.com/officeenterprisenda/#/threads/inGroup?type=in_group&feedId=14435206)中。</span><span class="sxs-lookup"><span data-stu-id="2414f-181">Post your feedback ad suggestions in the [Office Preview Yammer Group](https://www.yammer.com/officeenterprisenda/#/threads/inGroup?type=in_group&feedId=14435206).</span></span>
- <span data-ttu-id="2414f-182">檔案[Office 預覽 VSO](https://office-previews.visualstudio.com/previews)區域路徑的 「 Office 365 權限存取管理 」 下您錯誤報告。</span><span class="sxs-lookup"><span data-stu-id="2414f-182">File your bug reports under area path “Office 365 Privileged Access Management” on the [Office Preview VSO](https://office-previews.visualstudio.com/previews).</span></span>

## <a name="frequently-asked-questions"></a><span data-ttu-id="2414f-183">常見問題集</span><span class="sxs-lookup"><span data-stu-id="2414f-183">Frequently asked questions</span></span>

### <a name="what-skus-do-i-need-to-use-privileged-access-in-office-365"></a><span data-ttu-id="2414f-184">我需要哪些 Sku 使用特殊權限的存取 Office 365？</span><span class="sxs-lookup"><span data-stu-id="2414f-184">What SKUs do I need to use privileged access in Office 365?</span></span>
<span data-ttu-id="2414f-185">特殊權限存取 Office 365 中的管理只有目前客戶 E5 和進階規範 Sku。</span><span class="sxs-lookup"><span data-stu-id="2414f-185">Privileged access management in Office 365 is currently only available for customers with E5 and Advanced Compliance SKUs.</span></span>

### <a name="when-will-privileged-access-be-available-for-office-365-workloads-beyond-exchange"></a><span data-ttu-id="2414f-186">何時將權限的存取可供使用 Office 365 工作負載超過 Exchange？</span><span class="sxs-lookup"><span data-stu-id="2414f-186">When will privileged access be available for Office 365 workloads beyond Exchange?</span></span>
<span data-ttu-id="2414f-p113">我們想要推出提供這項功能的其他 Office 365 工作負載。當我們已經準備好要共用時間表時，它會提供透過 Office 365 藍圖。</span><span class="sxs-lookup"><span data-stu-id="2414f-p113">We plan to offer this feature in other Office 365 workloads soon. When we’re ready to share a timeline, it will be available through the Office 365 roadmap.</span></span>

### <a name="how-is-this-different-from-azure-active-directorys-privileged-identity-management"></a><span data-ttu-id="2414f-189">如何這是否為 Azure Active Directory 的權限的身分識別管理不同？</span><span class="sxs-lookup"><span data-stu-id="2414f-189">How is this different from Azure Active Directory’s Privileged Identity Management?</span></span>
<span data-ttu-id="2414f-p114">權限存取 Office 365 和[Azure AD 權限的身分識別管理](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure)互補彼此提供存取控制中管理位於不同範圍的剛剛-時間存取權。一起提供強大的一組控制項為保護您的資料。</span><span class="sxs-lookup"><span data-stu-id="2414f-p114">Privileged access management in Office 365 and [Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure) complement each other by providing access control with just-in-time access at different scopes. Together they provide a robust set of controls for protecting your data.</span></span>

<span data-ttu-id="2414f-p115">特殊權限存取 Office 365 中的管理可定義及 Azure AD 權限的身分識別管理層級的角色適用於與能夠執行多個工作時在任務層級設定範圍。 Azure AD 的權限身分識別管理主要是可讓管理 AD 角色和權限時的角色群組的存取 Office 365 中的存取管理會在任務層級套用。</span><span class="sxs-lookup"><span data-stu-id="2414f-p115">Privileged access management in Office 365 can be defined and scoped at the task level, while Azure AD Privileged Identity Management applies at the role level with the ability to execute multiple tasks.  Azure AD Privileged Identity Management primarily allows managing accesses for AD roles and role groups while privileged access management in Office 365 is applied at the task level.</span></span>

 - <span data-ttu-id="2414f-194">**啟用權限存取 Office 365 中的管理已使用 Azure AD 權限的身分識別管理時：** 在 Office 365 中新增權限的存取管理可提供其他細微的圖層的保護及稽核功能的權限存取 Office 365 資料。</span><span class="sxs-lookup"><span data-stu-id="2414f-194">**Enabling privileged access management in Office 365 while already using Azure AD Privileged Identity Management:** Adding privileged access management in Office 365 can provide another granular layer of protection and audit capabilities for privileged access to Office 365 data.</span></span>

- <span data-ttu-id="2414f-195">**已經使用時啟用 Azure AD 權限的身分識別管理特殊權限存取管理 Office 365 中：** 新增至權限的 Azure AD 權限的身分識別管理存取管理 Office 365 中的可以擴充主要使用者的角色或身分識別所定義的 Office 365 外部資料的權限的存取。</span><span class="sxs-lookup"><span data-stu-id="2414f-195">**Enabling Azure AD Privileged Identity Management while already using privileged access management in Office 365:**  Adding Azure AD Privileged Identity Management to privileged access management in Office 365 can extend privileged access to data outside of Office 365 that’s primarily defined by a user’s role or identity.</span></span> 

### <a name="do-i-need-to-be-a-global-admin-to-manage-privileged-access-in-office-365"></a><span data-ttu-id="2414f-196">是否需要是來管理 Office 365 中的權限的存取的全域系統管理員吗？</span><span class="sxs-lookup"><span data-stu-id="2414f-196">Do I need to be a Global Admin to manage privileged access in Office 365?</span></span>
<span data-ttu-id="2414f-p116">預覽期間您必須具備全域管理員能夠管理 Office 365 中的權限的存取的最低權限。包含在核准者群組的使用者不需要是檢閱和核准要求的全域系統管理員。</span><span class="sxs-lookup"><span data-stu-id="2414f-p116">During the preview you need to have Global Admin privilege to be able to manage privileged access in Office 365. Users who are included in an approvers’ group don't need to be a Global Admin to review and approve requests.</span></span> 

### <a name="how-is-privileged-access-management-in-office-365-related-to-customer-lockbox"></a><span data-ttu-id="2414f-199">如何為客戶 Lockbox 相關的 Office 365 中的權限的存取管理？</span><span class="sxs-lookup"><span data-stu-id="2414f-199">How is privileged access management in Office 365 related to Customer Lockbox?</span></span>
<span data-ttu-id="2414f-p117">[客戶 Lockbox](https://support.office.com/article/Office-365-Customer-Lockbox-Requests-36f9cdd1-e64c-421b-a7e4-4a54d16440a2)允許存取控制組織依其服務提供者，例如 Microsoft 資料存取層級。特殊權限存取 Office 365 中的管理允許所有的特殊權限的 Office 365 工作的組織內的更精細的存取控制。</span><span class="sxs-lookup"><span data-stu-id="2414f-p117">[Customer Lockbox](https://support.office.com/article/Office-365-Customer-Lockbox-Requests-36f9cdd1-e64c-421b-a7e4-4a54d16440a2) allows a level of access control for organizations for access to to data by their service provider, i.e. Microsoft. Privileged access management in Office 365 allows granular access control within an organization for all Office 365 privileged tasks.</span></span>