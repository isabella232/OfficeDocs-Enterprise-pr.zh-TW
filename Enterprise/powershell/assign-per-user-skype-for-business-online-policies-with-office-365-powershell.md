---
title: 指派個別使用者 Skype 線上商務原則與 Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: 摘要：使用 Office 365 PowerShell，將每一使用者的通訊設定指派給商務用 Skype Online 原則。
ms.openlocfilehash: 0b95c993c3795bdbe9a68e23e107ea745c15f71b
ms.sourcegitcommit: 88ede20888e2db0bb904133c0bd97726d6d65ee2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2020
ms.locfileid: "44719964"
---
# <a name="assign-per-user-skype-for-business-online-policies-with-office-365-powershell"></a><span data-ttu-id="853d7-103">指派個別使用者 Skype 線上商務原則與 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="853d7-103">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>

<span data-ttu-id="853d7-104">使用 Office 365 PowerShell 是將每一使用者通訊設定指派給商務用 Skype Online 原則的有效方式。</span><span class="sxs-lookup"><span data-stu-id="853d7-104">Using Office 365 PowerShell is an efficient way to assign per-user communication settings with Skype for Business Online policies.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="853d7-105">開始之前</span><span class="sxs-lookup"><span data-stu-id="853d7-105">Before you begin</span></span>

<span data-ttu-id="853d7-106">使用這些指示設定執行命令（略過您已完成的步驟）：</span><span class="sxs-lookup"><span data-stu-id="853d7-106">Use these instructions to get set up to run the commands (skip the steps you have already completed):</span></span>
  
1. <span data-ttu-id="853d7-107">下載及安裝[商務用 Skype Online 連接器模組](https://www.microsoft.com/download/details.aspx?id=39366)。</span><span class="sxs-lookup"><span data-stu-id="853d7-107">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366).</span></span>
    
2. <span data-ttu-id="853d7-108">開啟 Windows PowerShell 命令提示字元，並執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="853d7-108">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
```powershell
Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
```

<span data-ttu-id="853d7-109">出現提示時，請輸入您的商務用 Skype Online 系統管理員帳戶名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="853d7-109">When prompted, enter your Skype for Business Online administrator account name and password.</span></span>
    
## <a name="updating-external-communication-settings-for-a-user-account"></a><span data-ttu-id="853d7-110">更新使用者帳戶的外部通訊設定</span><span class="sxs-lookup"><span data-stu-id="853d7-110">Updating external communication settings for a user account</span></span>

<span data-ttu-id="853d7-111">假設您想要變更使用者帳戶上的外部通訊設定。</span><span class="sxs-lookup"><span data-stu-id="853d7-111">Suppose you want to change external communication settings on a user account.</span></span> <span data-ttu-id="853d7-112">例如，您想要允許 Alex 與同盟使用者通訊（EnableFederationAccess 等於 True），但不是與 Windows Live 使用者進行通訊（EnablePublicCloudAccess 等於 False）。</span><span class="sxs-lookup"><span data-stu-id="853d7-112">For example, you want to allow Alex to communicate with federated users (EnableFederationAccess is equal to True) but not with Windows Live users (EnablePublicCloudAccess equals False).</span></span> <span data-ttu-id="853d7-113">若要這麼做，您必須執行下列兩項動作：</span><span class="sxs-lookup"><span data-stu-id="853d7-113">To do that, you need to do two things:</span></span>
  
1. <span data-ttu-id="853d7-114">尋找符合我們準則的外部存取原則。</span><span class="sxs-lookup"><span data-stu-id="853d7-114">Find an external access policy that meets our criteria.</span></span>
    
2. <span data-ttu-id="853d7-115">將該外部存取原則指派給 Alex。</span><span class="sxs-lookup"><span data-stu-id="853d7-115">Assign that external access policy to Alex.</span></span>
    
<span data-ttu-id="853d7-116">如何判斷哪個外部存取原則要指派 Alex？</span><span class="sxs-lookup"><span data-stu-id="853d7-116">How do you determine which external access policy to assign Alex?</span></span> <span data-ttu-id="853d7-117">下列命令會傳回 EnableFederationAccess 設定為 True 且 EnablePublicCloudAccess 設定為 False 的所有外部存取原則：</span><span class="sxs-lookup"><span data-stu-id="853d7-117">The following command returns all the external access policies where EnableFederationAccess is set to True and EnablePublicCloudAccess is set to False:</span></span>
  
```powershell
Get-CsExternalAccessPolicy -Include All| Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

<span data-ttu-id="853d7-118">除非您已建立 Microsoft.rtc.management.writableconfig.policy.externalaccess.externalaccesspolicy 的任何自訂實例，否則該命令會傳回符合我們準則的一個原則（FederationOnly）。</span><span class="sxs-lookup"><span data-stu-id="853d7-118">Unless you have created any custom instances of ExternalAccessPolicy, that command returns one policy that meets our criteria (FederationOnly).</span></span> <span data-ttu-id="853d7-119">範例如下：</span><span class="sxs-lookup"><span data-stu-id="853d7-119">Here is an example:</span></span>
  
```powershell
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

<span data-ttu-id="853d7-120">現在，您知道要將哪一個原則指派給 Alex，我們可以使用[授與 get-csexternalaccesspolicy](https://go.microsoft.com/fwlink/?LinkId=523974) Cmdlet 指派該原則。</span><span class="sxs-lookup"><span data-stu-id="853d7-120">Now that you know which policy to assign to Alex, we can assign that policy by using the [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974) cmdlet.</span></span> <span data-ttu-id="853d7-121">範例如下：</span><span class="sxs-lookup"><span data-stu-id="853d7-121">Here is an example:</span></span>
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

<span data-ttu-id="853d7-122">指派原則非常簡單：您只需指定使用者的身分識別及要指派之原則的名稱即可。</span><span class="sxs-lookup"><span data-stu-id="853d7-122">Assigning a policy is pretty simple: you simply specify the Identity of the user and the name of the policy to be assigned.</span></span> 
  
<span data-ttu-id="853d7-123">在原則和原則指派方面，您並不局限于每次使用使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="853d7-123">And when it comes to policies and policy assignments, you're not limited to working with user accounts one a time.</span></span> <span data-ttu-id="853d7-124">例如，假設您需要可與同盟夥伴和 Windows Live 使用者進行通訊的所有使用者清單。</span><span class="sxs-lookup"><span data-stu-id="853d7-124">For example, suppose you need a list of all the users who are allowed to communicate with federated partners and with Windows Live users.</span></span> <span data-ttu-id="853d7-125">我們已經知道這些使用者均被指派外部使用者存取原則 FederationAndPICDefault。</span><span class="sxs-lookup"><span data-stu-id="853d7-125">We already know that those users have been assigned the external user access policy FederationAndPICDefault.</span></span> <span data-ttu-id="853d7-126">因為我們知道這一點，您可以執行一個簡易命令來顯示所有這些使用者的清單。</span><span class="sxs-lookup"><span data-stu-id="853d7-126">Because we know that, you can display a list of all those users by running one simple command.</span></span> <span data-ttu-id="853d7-127">命令如下：</span><span class="sxs-lookup"><span data-stu-id="853d7-127">Here is the command:</span></span>
  
```powershell
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

<span data-ttu-id="853d7-128">換句話說，向我們展示 Microsoft.rtc.management.writableconfig.policy.externalaccess.externalaccesspolicy 屬性設定為 FederationAndPICDefault 的所有使用者。</span><span class="sxs-lookup"><span data-stu-id="853d7-128">In other words, show us all the users where the ExternalAccessPolicy property is set to FederationAndPICDefault.</span></span> <span data-ttu-id="853d7-129">（為了限制螢幕上顯示的資訊數量，您可以使用 Select-Object Cmdlet 來顯示 [只顯示每位使用者的顯示名稱]。）</span><span class="sxs-lookup"><span data-stu-id="853d7-129">(And, in order to limit the amount of information that appears onscreen, use the Select-Object cmdlet to display show us only each user's display name.)</span></span> 
  
<span data-ttu-id="853d7-130">若要將所有使用者帳戶設定為使用相同原則，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="853d7-130">To configure all our user accounts to use that same policy, use this command:</span></span>
  
```powershell
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

<span data-ttu-id="853d7-131">這個命令會使用 Get-CsOnlineUser 傳回已啟用 Lync 的所有使用者的集合，然後將所有該資訊傳送至授與 Get-csexternalaccesspolicy，這會將 FederationAndPICDefault 原則指派給集合中的每個使用者和每個使用者。</span><span class="sxs-lookup"><span data-stu-id="853d7-131">This command uses Get-CsOnlineUser to return a collection of all the users who have been enabled for Lync, then sends all that information to Grant-CsExternalAccessPolicy, which assigns the FederationAndPICDefault policy to each and every user in the collection.</span></span>
  
<span data-ttu-id="853d7-132">另一個範例是，假設您先前已指派 Alex FederationAndPICDefault 原則，而現在您已變更了您的想法，而且想要由全域外部存取原則來管理。</span><span class="sxs-lookup"><span data-stu-id="853d7-132">As an additional example, suppose you've previously assigned Alex the FederationAndPICDefault policy and now you've changed your mind and would like him to be managed by the global external access policy.</span></span> <span data-ttu-id="853d7-133">您無法將全域原則明確指派給任何人。</span><span class="sxs-lookup"><span data-stu-id="853d7-133">You can't explicitly assign the global policy to anyone.</span></span> <span data-ttu-id="853d7-134">相反地，如果沒有任何個別使用者原則指派給該使用者，就會將全域原則用於指定的使用者。</span><span class="sxs-lookup"><span data-stu-id="853d7-134">Instead, the global policy is used for a given user if no per-user policy is assigned to that user.</span></span> <span data-ttu-id="853d7-135">因此，如果我們想要透過全域原則來管理 Alex，您必須*取消*指派先前指派給他的任何個別使用者原則。</span><span class="sxs-lookup"><span data-stu-id="853d7-135">Therefore, if we want Alex to be managed by the global policy, you need to  *unassign*  any per-user policy previously assigned to him.</span></span> <span data-ttu-id="853d7-136">範例命令如下：</span><span class="sxs-lookup"><span data-stu-id="853d7-136">Here is an example command:</span></span>
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

<span data-ttu-id="853d7-137">這個命令會將指派給 Alex 的外部存取原則名稱設為 null 值（$Null）。</span><span class="sxs-lookup"><span data-stu-id="853d7-137">This command sets the name of the external access policy assigned to Alex to a null value ($Null).</span></span> <span data-ttu-id="853d7-138">Null 表示 "nothing"。</span><span class="sxs-lookup"><span data-stu-id="853d7-138">Null means "nothing".</span></span> <span data-ttu-id="853d7-139">換句話說，也就是沒有任何外部存取原則指派給 Alex。</span><span class="sxs-lookup"><span data-stu-id="853d7-139">In other words, no external access policy is assigned to Alex.</span></span> <span data-ttu-id="853d7-140">當沒有任何外部存取原則指派給使用者時，該使用者就會受到全域原則的管理。</span><span class="sxs-lookup"><span data-stu-id="853d7-140">When no external access policy is assigned to a user, that user then gets managed by the global policy.</span></span>
  

## <a name="managing-large-numbers-of-users"></a><span data-ttu-id="853d7-141">管理大量使用者</span><span class="sxs-lookup"><span data-stu-id="853d7-141">Managing large numbers of users</span></span>

<span data-ttu-id="853d7-142">若要管理大量的使用者（1000或更多），您必須使用[Invoke-Command](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-7) Cmdlet，透過腳本區塊批次處理命令。</span><span class="sxs-lookup"><span data-stu-id="853d7-142">To manage large numbers of users (1000 or more), you need to batch the commands via a script block using the [Invoke-Command](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-7) cmdlet.</span></span>  <span data-ttu-id="853d7-143">在先前的範例中，每次執行 Cmdlet 時，必須先設定此呼叫，然後等候結果，再將其傳送回來。</span><span class="sxs-lookup"><span data-stu-id="853d7-143">In previous examples, each time a cmdlet is executed, it must set up the call and then wait for the result before sending it back.</span></span>  <span data-ttu-id="853d7-144">使用腳本區塊時，這可讓 Cmdlet 以遠端方式執行，並在完成之後傳送資料回來。</span><span class="sxs-lookup"><span data-stu-id="853d7-144">When using a script block, this allows the cmdlets to be executed remotely, and once completed, send the data back.</span></span> 

```powershell
Import-Module LyncOnlineConnector
$sfbSession = New-CsOnlineSession
$users = Get-CsOnlineUser -Filter { ClientPolicy -eq $null } -ResultSize 500

$batch = 50
$filter = ''
$total = $users.Count
$count = 0
    $users | ForEach-Object {
    $upn = $_.UserPrincipalName
    $filter += "(UserPrincipalName -eq '$upn')"
    $batch--
    $count++
    if (($batch -eq 0) -or ($count -eq $total)) {
        $filterSB=[ScriptBlock]::Create($filter)
        Invoke-Command -Session $s -ScriptBlock {param($f) Get-CsOnlineUser -filter $f | Grant-CsClientPolicy -PolicyName "ClientPolicyNoIMURL" -Passthru | Grant-CsExternalAccessPolicy -PolicyName "FederationAndPICDefault"} -ArgumentList $filterSB

        # Reset
        $batch = 50
        $filter = ''
    } else {
        $filter += " -or "
    }
}
```

<span data-ttu-id="853d7-145">這會在不具備用戶端原則的時刻找到500使用者。</span><span class="sxs-lookup"><span data-stu-id="853d7-145">This will find 500 users at a time who do not have a client policy.</span></span> <span data-ttu-id="853d7-146">它會授與他們用戶端原則 "ClientPolicyNoIMURL" 和外部存取原則 "FederationAndPicDefault"。</span><span class="sxs-lookup"><span data-stu-id="853d7-146">It will grant them the client policy "ClientPolicyNoIMURL" and the external access policy "FederationAndPicDefault".</span></span> <span data-ttu-id="853d7-147">結果會批分為50群組，而每批次50都會傳送至遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="853d7-147">The results are batched into groups of 50 and each batch of 50 is then sent to the remote machine.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="853d7-148">也請參閱</span><span class="sxs-lookup"><span data-stu-id="853d7-148">See also</span></span>

[<span data-ttu-id="853d7-149">使用 Office 365 PowerShell 管理商務用 Skype Online</span><span class="sxs-lookup"><span data-stu-id="853d7-149">Manage Skype for Business Online with Office 365 PowerShell</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)
  
[<span data-ttu-id="853d7-150">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="853d7-150">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="853d7-151">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="853d7-151">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
