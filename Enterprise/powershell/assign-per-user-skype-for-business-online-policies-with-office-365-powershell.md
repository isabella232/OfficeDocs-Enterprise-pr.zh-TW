---
title: 指派個別使用者 Skype 線上商務原則與 Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: 摘要： 使用 Office 365 PowerShell 來指派個別使用者 Skype 線上商務原則通訊設定。
ms.openlocfilehash: 7f819b619c5b3607c98c10791fe30c3944e862a4
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33492019"
---
# <a name="assign-per-user-skype-for-business-online-policies-with-office-365-powershell"></a><span data-ttu-id="77373-103">指派個別使用者 Skype 線上商務原則與 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="77373-103">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>

 <span data-ttu-id="77373-104">**摘要：** 使用 Office 365 PowerShell 來指派個別使用者 Skype 線上商務原則通訊設定。</span><span class="sxs-lookup"><span data-stu-id="77373-104">**Summary:** Use Office 365 PowerShell to assign per-user communication settings with Skype for Business Online policies.</span></span>
  
<span data-ttu-id="77373-105">使用 Office 365 PowerShell 是要指派個別使用者 Skype 線上商務原則通訊設定的有效方法。</span><span class="sxs-lookup"><span data-stu-id="77373-105">Using Office 365 PowerShell is an efficient way to assign per-user communication settings with Skype for Business Online policies.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="77373-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="77373-106">Before you begin</span></span>

<span data-ttu-id="77373-107">使用這些指示以取得設定，請執行命令 （略過您已經完成的步驟）：</span><span class="sxs-lookup"><span data-stu-id="77373-107">Use these instructions to get set up to run the commands (skip the steps you have already completed):</span></span>
  
1. <span data-ttu-id="77373-108">下載並安裝[商務用 Skype 商務 Online 連接器模組](https://www.microsoft.com/en-us/download/details.aspx?id=39366)。</span><span class="sxs-lookup"><span data-stu-id="77373-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/en-us/download/details.aspx?id=39366).</span></span>
    
2. <span data-ttu-id="77373-109">開啟 Windows PowerShell 命令提示字元並執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="77373-109">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```
  Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```
<span data-ttu-id="77373-110">出現提示時，輸入您 Skype 商務 Online 系統管理員帳戶名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="77373-110">When prompted, enter your Skype for Business Online administrator account name and password.</span></span>
    
## <a name="updating-external-communication-settings-for-a-user-account"></a><span data-ttu-id="77373-111">更新的使用者帳戶的外部通訊設定</span><span class="sxs-lookup"><span data-stu-id="77373-111">Updating external communication settings for a user account</span></span>

<span data-ttu-id="77373-112">假設您想要變更的使用者帳戶上的外部通訊設定。</span><span class="sxs-lookup"><span data-stu-id="77373-112">Suppose you want to change external communication settings on a user account.</span></span> <span data-ttu-id="77373-113">例如，您想要允許 Alex 通訊與同盟使用者 （EnableFederationAccess 等於 True），但未與 Windows Live 的使用者 （EnablePublicCloudAccess 等於 False）。</span><span class="sxs-lookup"><span data-stu-id="77373-113">For example, you want to allow Alex to communicate with federated users (EnableFederationAccess is equal to True) but not with Windows Live users (EnablePublicCloudAccess equals False).</span></span> <span data-ttu-id="77373-114">若要這麼做，您必須執行下列兩件事：</span><span class="sxs-lookup"><span data-stu-id="77373-114">To do that, you need to do two things:</span></span>
  
1. <span data-ttu-id="77373-115">尋找符合我們準則的外部存取原則。</span><span class="sxs-lookup"><span data-stu-id="77373-115">Find an external access policy that meets our criteria.</span></span>
    
2. <span data-ttu-id="77373-116">將該外部存取原則指派給 Alex。</span><span class="sxs-lookup"><span data-stu-id="77373-116">Assign that external access policy to Alex.</span></span>
    
> [!NOTE]
>  <span data-ttu-id="77373-117">您無法建立所有的自訂原則我們自己。</span><span class="sxs-lookup"><span data-stu-id="77373-117">You can't create a custom policy all our own.</span></span> <span data-ttu-id="77373-118">這是因為 Skype for Business Online 不允許您建立自訂原則。</span><span class="sxs-lookup"><span data-stu-id="77373-118">That's because Skype for Business Online does not allow you to create custom policies.</span></span> <span data-ttu-id="77373-119">相反地，您必須指派其中一個特別針對 Office 365 所建立的原則。</span><span class="sxs-lookup"><span data-stu-id="77373-119">Instead, you must assign one of the policies that were created specifically for Office 365.</span></span> <span data-ttu-id="77373-120">預先建立原則包含： 4 個不同的用戶端原則、 224 不同的會議原則、 5 個不同撥號對應表、 5 個不同的外部存取原則、 1 個託管語音信箱原則，以及 4 個不同的語音原則。</span><span class="sxs-lookup"><span data-stu-id="77373-120">Those pre-created policies include: 4 different client policies, 224 different conferencing policies, 5 different dial plans, 5 different external access policies, 1 hosted voicemail policy, and 4 different voice policies.</span></span>
  
<span data-ttu-id="77373-121">您要如何判斷哪個外部存取原則指派 Alex？</span><span class="sxs-lookup"><span data-stu-id="77373-121">So how do you determine which external access policy to assign Alex?</span></span> <span data-ttu-id="77373-122">下列命令會傳回 EnableFederationAccess 設定為 True 且 EnablePublicCloudAccess 設定為 False 的所有外部存取原則：</span><span class="sxs-lookup"><span data-stu-id="77373-122">The following command returns all the external access policies where EnableFederationAccess is set to True and EnablePublicCloudAccess is set to False:</span></span>
  
```
Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

<span data-ttu-id="77373-123">此命令的作用是傳回所有符合這兩項條件的原則： EnableFederationAccess 屬性設為 True，且 EnablePublicCloudAccess 原則設為 False。</span><span class="sxs-lookup"><span data-stu-id="77373-123">What the command does is return all the policies that meet two criteria: the EnableFederationAccess property is set to True, and the EnablePublicCloudAccess policy is set to False.</span></span> <span data-ttu-id="77373-124">接著，該命令會傳回一個符合我們準則 (FederationOnly) 的原則。</span><span class="sxs-lookup"><span data-stu-id="77373-124">In turn, that command returns one policy that meets our criteria (FederationOnly).</span></span> <span data-ttu-id="77373-125">範例如下：</span><span class="sxs-lookup"><span data-stu-id="77373-125">Here is an example:</span></span>
  
```
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

> [!NOTE]
> <span data-ttu-id="77373-126">原則 Identity 說標記： FederationOnly。</span><span class="sxs-lookup"><span data-stu-id="77373-126">The policy Identity says Tag:FederationOnly.</span></span> <span data-ttu-id="77373-127">的確，Tag:前置詞沿襲自 Microsoft Lync 2013 已完成的發行前版本。</span><span class="sxs-lookup"><span data-stu-id="77373-127">As it turns out, the Tag: prefix is a carryover from the early pre-release work done on Microsoft Lync 2013.</span></span> <span data-ttu-id="77373-128">要將原則指派給使用者時，您應該刪除 Tag:前置詞，且直接使用原則名稱：FederationOnly。</span><span class="sxs-lookup"><span data-stu-id="77373-128">When it comes to assigning policies to users, you should delete the Tag: prefix and use just the policy name: FederationOnly.</span></span> 
  
<span data-ttu-id="77373-129">既然您知道哪個原則將指派給 alex 之後，我們可以使用[Grant-csexternalaccesspolicy](https://go.microsoft.com/fwlink/?LinkId=523974) cmdlet 指派該原則。</span><span class="sxs-lookup"><span data-stu-id="77373-129">Now that you know which policy to assign to Alex, we can assign that policy by using the [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974) cmdlet.</span></span> <span data-ttu-id="77373-130">範例如下：</span><span class="sxs-lookup"><span data-stu-id="77373-130">Here is an example:</span></span>
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

<span data-ttu-id="77373-131">指派原則是很簡單： 只要指定使用者的身分識別和原則的名稱指派給。</span><span class="sxs-lookup"><span data-stu-id="77373-131">Assigning a policy is pretty simple: you simply specify the Identity of the user and the name of the policy to be assigned.</span></span> 
  
<span data-ttu-id="77373-132">及過濾原則和原則工作分派的範例，您不限於運用使用者帳戶一次。</span><span class="sxs-lookup"><span data-stu-id="77373-132">And when it comes to policies and policy assignments, you're not limited to working with user accounts one a time.</span></span> <span data-ttu-id="77373-133">例如，假設您需要可與同盟夥伴和 Windows Live 使用者進行通訊的所有使用者清單。</span><span class="sxs-lookup"><span data-stu-id="77373-133">For example, suppose you need a list of all the users who are allowed to communicate with federated partners and with Windows Live users.</span></span> <span data-ttu-id="77373-134">我們已經知道這些使用者均被指派外部使用者存取原則 FederationAndPICDefault。</span><span class="sxs-lookup"><span data-stu-id="77373-134">We already know that those users have been assigned the external user access policy FederationAndPICDefault.</span></span> <span data-ttu-id="77373-135">由於我們知道，，您可以執行一個簡單的命令來顯示所有這些使用者的清單。</span><span class="sxs-lookup"><span data-stu-id="77373-135">Because we know that, you can display a list of all those users by running one simple command.</span></span> <span data-ttu-id="77373-136">命令如下：</span><span class="sxs-lookup"><span data-stu-id="77373-136">Here is the command:</span></span>
  
```
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

<span data-ttu-id="77373-137">換句話說，告訴我們所有的使用者所在的 ExternalAccessPolicy 屬性設為 FederationAndPICDefault。</span><span class="sxs-lookup"><span data-stu-id="77373-137">In other words, show us all the users where the ExternalAccessPolicy property is set to FederationAndPICDefault.</span></span> <span data-ttu-id="77373-138">（和，以縮短螢幕上所顯示的資訊，請使用 Select-object cmdlet 來顯示告訴我們每位使用者的顯示名稱）。</span><span class="sxs-lookup"><span data-stu-id="77373-138">(And, in order to limit the amount of information that appears onscreen, use the Select-Object cmdlet to display show us only each user's display name.)</span></span> 
  
<span data-ttu-id="77373-139">若要設定所有使用者帳戶使用相同的原則，請使用此命令：</span><span class="sxs-lookup"><span data-stu-id="77373-139">To configure all our user accounts to use that same policy, use this command:</span></span>
  
```
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

<span data-ttu-id="77373-140">這個命令會使用 Get-csonlineuser 傳回的所有使用者都已啟用 Lync，然後將所有該資訊傳送至 Grant-csexternalaccesspolicy，它會 FederationAndPICDefault 原則指派給集合中的每個使用者的集合。</span><span class="sxs-lookup"><span data-stu-id="77373-140">This command uses Get-CsOnlineUser to return a collection of all the users who have been enabled for Lync, then sends all that information to Grant-CsExternalAccessPolicy, which assigns the FederationAndPICDefault policy to each and every user in the collection.</span></span>
  
<span data-ttu-id="77373-141">做為其他範例，假設您已先前指派給 Alex FederationAndPICDefault 原則，現在您改變心意，但想他由全域外部存取原則來管理。</span><span class="sxs-lookup"><span data-stu-id="77373-141">As an additional example, suppose you've previously assigned Alex the FederationAndPICDefault policy and now you've changed your mind and would like him to be managed by the global external access policy.</span></span> <span data-ttu-id="77373-142">您明確不能將全域原則指派給任何人。</span><span class="sxs-lookup"><span data-stu-id="77373-142">You can't explicitly assign the global policy to anyone.</span></span> <span data-ttu-id="77373-143">只有在不指派任何其他的個別使用者原則時，它才會使用。</span><span class="sxs-lookup"><span data-stu-id="77373-143">It is only used if no other per-user policy is assigned.</span></span> <span data-ttu-id="77373-144">因此，如果我們想要由全域原則來管理 alex 之後，您必須*取消指派*先前已指派給他任何個別使用者原則。</span><span class="sxs-lookup"><span data-stu-id="77373-144">Therefore, if we want Alex to be managed by the global policy, you need to  *unassign*  any per-user policy previously assigned to him.</span></span> <span data-ttu-id="77373-145">範例命令如下：</span><span class="sxs-lookup"><span data-stu-id="77373-145">Here is an example command:</span></span>
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

<span data-ttu-id="77373-146">此命令會設定設為 null 值 ($Null) 指派給 alex 之後的外部存取原則的名稱。</span><span class="sxs-lookup"><span data-stu-id="77373-146">This command sets the name of the external access policy assigned to Alex to a null value ($Null).</span></span> <span data-ttu-id="77373-147">Null 表示"nothing"。</span><span class="sxs-lookup"><span data-stu-id="77373-147">Null means "nothing".</span></span> <span data-ttu-id="77373-148">換句話說，任何外部存取原則不指派給 alex 之後。</span><span class="sxs-lookup"><span data-stu-id="77373-148">In other words, no external access policy is assigned to Alex.</span></span> <span data-ttu-id="77373-149">沒有外部存取原則指派給使用者後，該使用者再取得管理由全域原則。</span><span class="sxs-lookup"><span data-stu-id="77373-149">When no external access policy is assigned to a user, that user then gets managed by the global policy.</span></span>
  
<span data-ttu-id="77373-150">若要停用使用 Windows PowerShell 的使用者帳戶，請使用 Azure Active Directory 指令程式來移除 Alex Skype for Business Online 授權。</span><span class="sxs-lookup"><span data-stu-id="77373-150">To disable a user account using Windows PowerShell, use the Azure Active Directory cmdlets to remove Alex's Skype for Business Online license.</span></span> <span data-ttu-id="77373-151">如需詳細資訊，請參閱[停用 Office 365 PowerShell 與服務存取權](assign-licenses-to-user-accounts-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="77373-151">For more information, see [Disable access to services with Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="77373-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77373-152">See also</span></span>

#### 

[<span data-ttu-id="77373-153">使用 Office 365 PowerShell 管理商務用 Skype Online</span><span class="sxs-lookup"><span data-stu-id="77373-153">Manage Skype for Business Online with Office 365 PowerShell</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)
  
[<span data-ttu-id="77373-154">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="77373-154">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="77373-155">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="77373-155">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

