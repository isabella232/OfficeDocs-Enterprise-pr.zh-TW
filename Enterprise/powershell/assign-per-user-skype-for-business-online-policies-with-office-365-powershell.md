---
title: "指派個別使用者 Skype 線上商務原則與 Office 365 PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: "摘要： 使用 Office 365 PowerShell 指派個別使用者線上商務原則與 Skype 通訊設定。"
ms.openlocfilehash: 91916b41ba420a204ecabb27eea2e451a91f6f25
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="assign-per-user-skype-for-business-online-policies-with-office-365-powershell"></a><span data-ttu-id="5de8e-103">指派個別使用者 Skype 線上商務原則與 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5de8e-103">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>

 <span data-ttu-id="5de8e-104">**摘要：**使用 Office 365 PowerShell 指派個別使用者的通訊設定與 Skype 線上商務原則。</span><span class="sxs-lookup"><span data-stu-id="5de8e-104">**Summary:** Use Office 365 PowerShell to assign per-user communication settings with Skype for Business Online policies.</span></span>
  
<span data-ttu-id="5de8e-105">使用 Office 365 PowerShell 是要指派個別使用者線上商務原則與 Skype 通訊設定的有效方法。</span><span class="sxs-lookup"><span data-stu-id="5de8e-105">Using Office 365 PowerShell is an efficient way to assign per-user communication settings with Skype for Business Online policies.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="5de8e-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="5de8e-106">Before you begin</span></span>

<span data-ttu-id="5de8e-107">使用這些指示來取得設定設定來執行命令 （略過您已經完成的步驟）：</span><span class="sxs-lookup"><span data-stu-id="5de8e-107">Use these instructions to get set up to run the commands (skip the steps you have already completed):</span></span>
  
1. <span data-ttu-id="5de8e-108">下載並安裝[Skype for Business Online 連接器模組](https://www.microsoft.com/en-us/download/details.aspx?id=39366)。</span><span class="sxs-lookup"><span data-stu-id="5de8e-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/en-us/download/details.aspx?id=39366).</span></span>
    
2. <span data-ttu-id="5de8e-109">開啟 Windows PowerShell 命令提示字元並執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="5de8e-109">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```
  Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```
<span data-ttu-id="5de8e-110">出現提示時，輸入您 Skype 線上商務系統管理員帳戶名稱及密碼。</span><span class="sxs-lookup"><span data-stu-id="5de8e-110">When prompted, enter your Skype for Business Online administrator account name and password.</span></span>
    
## <a name="updating-external-communication-settings-for-a-user-account"></a><span data-ttu-id="5de8e-111">更新使用者帳戶的外部通訊的設定</span><span class="sxs-lookup"><span data-stu-id="5de8e-111">Updating external communication settings for a user account</span></span>

<span data-ttu-id="5de8e-p101">假設您想要變更的使用者帳戶上的外部通訊設定。例如，您要允許與同盟使用者 （EnableFederationAccess 等於 True），但不是與 （EnablePublicCloudAccess 等於 False） 的 Windows Live 的使用者進行通訊的 Alex。若要這樣做，您需要執行兩件事：</span><span class="sxs-lookup"><span data-stu-id="5de8e-p101">Suppose you want to change external communication settings on a user account. For example, you want to allow Alex to communicate with federated users (EnableFederationAccess is equal to True) but not with Windows Live users (EnablePublicCloudAccess equals False). To do that, you need to do two things:</span></span>
  
1. <span data-ttu-id="5de8e-115">尋找符合我們準則的外部存取原則。</span><span class="sxs-lookup"><span data-stu-id="5de8e-115">Find an external access policy that meets our criteria.</span></span>
    
2. <span data-ttu-id="5de8e-116">將該外部存取原則指派給 Alex。</span><span class="sxs-lookup"><span data-stu-id="5de8e-116">Assign that external access policy to Alex.</span></span>
    
> [!NOTE]
>  <span data-ttu-id="5de8e-p102">您無法建立所有的自訂原則我們自己。那是因為 Skype 商務 online 不允許您建立自訂原則。而是必須指派一個特別針對 Office 365 所建立的原則。這些預先建立的原則包含： 4 個不同的用戶端原則、 224 個不同的會議原則、 5 個不同的撥號計劃、 5 個不同的外部存取原則、 1 個託管語音信箱原則及 4 個不同的語音原則。</span><span class="sxs-lookup"><span data-stu-id="5de8e-p102">You can't create a custom policy all our own. That's because Skype for Business Online does not allow you to create custom policies. Instead, you must assign one of the policies that were created specifically for Office 365. Those pre-created policies include: 4 different client policies, 224 different conferencing policies, 5 different dial plans, 5 different external access policies, 1 hosted voicemail policy, and 4 different voice policies.</span></span>
  
<span data-ttu-id="5de8e-p103">您要那要如何決定要指派 Alex 哪個外部存取原則？下列命令會傳回所有外部存取原則其中 EnableFederationAccess 設為 True，而 EnablePublicCloudAccess 設為 False：</span><span class="sxs-lookup"><span data-stu-id="5de8e-p103">So how do you determine which external access policy to assign Alex? The following command returns all the external access policies where EnableFederationAccess is set to True and EnablePublicCloudAccess is set to False:</span></span>
  
```
Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

<span data-ttu-id="5de8e-p104">此命令的沒有會傳回所有符合兩個準則的原則： EnableFederationAccess 屬性設為 True，且 EnablePublicCloudAccess 原則設為 False。接著，該命令會傳回一個符合我們準則 (FederationOnly) 的原則。以下是範例：</span><span class="sxs-lookup"><span data-stu-id="5de8e-p104">What the command does is return all the policies that meet two criteria: the EnableFederationAccess property is set to True, and the EnablePublicCloudAccess policy is set to False. In turn, that command returns one policy that meets our criteria (FederationOnly). Here is an example:</span></span>
  
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
> <span data-ttu-id="5de8e-p105">原則 Identity 表示 Tag: FederationOnly。顯示出 Tag： 前置詞是從 Microsoft Lync 2013 已完成的最早發行前工作 carryover。若要將原則指派給使用者而言，您應該刪除 Tag： 首碼] 和 [使用只是原則名稱： FederationOnly。</span><span class="sxs-lookup"><span data-stu-id="5de8e-p105">The policy Identity says Tag:FederationOnly. As it turns out, the Tag: prefix is a carryover from the early pre-release work done on Microsoft Lync 2013. When it comes to assigning policies to users, you should delete the Tag: prefix and use just the policy name: FederationOnly.</span></span> 
  
<span data-ttu-id="5de8e-p106">既然您知道哪個原則將指派給 alex 之後，我們可以使用[Grant-csexternalaccesspolicy](https://go.microsoft.com/fwlink/?LinkId=523974)指令程式來指派該原則。以下是範例：</span><span class="sxs-lookup"><span data-stu-id="5de8e-p106">Now that you know which policy to assign to Alex, we can assign that policy by using the [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974) cmdlet. Here is an example:</span></span>
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

<span data-ttu-id="5de8e-131">指派原則是很簡單： 只要指定使用者的身分識別和原則的名稱指派。</span><span class="sxs-lookup"><span data-stu-id="5de8e-131">Assigning a policy is pretty simple: you simply specify the Identity of the user and the name of the policy to be assigned.</span></span> 
  
<span data-ttu-id="5de8e-p107">與原則和原則指派至而言，您不限於處理的使用者帳戶一次。例如，假設您需要的所有允許與同盟協力廠商及 Windows Live 使用者通訊的使用者清單。我們已經知道這些使用者所獲指派的外部使用者存取原則 FederationAndPICDefault。因為我們知道的您可以執行一個簡單的命令來顯示所有這些使用者的清單。以下是此命令：</span><span class="sxs-lookup"><span data-stu-id="5de8e-p107">And when it comes to policies and policy assignments, you're not limited to working with user accounts one a time. For example, suppose you need a list of all the users who are allowed to communicate with federated partners and with Windows Live users. We already know that those users have been assigned the external user access policy FederationAndPICDefault. Because we know that, you can display a list of all those users by running one simple command. Here is the command:</span></span>
  
```
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

<span data-ttu-id="5de8e-p108">換句話說，顯示我們的所有使用者所在的 externalaccesspolicy 才屬性設定為 FederationAndPICDefault。（和，以縮短顯示於螢幕上的資訊，請使用 Select-object 指令程式，以顯示顯示我們每位使用者的顯示名稱）。</span><span class="sxs-lookup"><span data-stu-id="5de8e-p108">In other words, show us all the users where the ExternalAccessPolicy property is set to FederationAndPICDefault. (And, in order to limit the amount of information that appears onscreen, use the Select-Object cmdlet to display show us only each user's display name.)</span></span> 
  
<span data-ttu-id="5de8e-139">若要設定所有使用者帳戶使用該相同的原則，請使用此命令：</span><span class="sxs-lookup"><span data-stu-id="5de8e-139">To configure all our user accounts to use that same policy, use this command:</span></span>
  
```
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

<span data-ttu-id="5de8e-140">此命令會使用 Get-csonlineuser 來傳回已啟用 Lync，然後再將所有該資訊傳送到 Grant-csexternalaccesspolicy，此 FederationAndPICDefault 原則指派給集合中的每個使用者的所有使用者的集合。</span><span class="sxs-lookup"><span data-stu-id="5de8e-140">This command uses Get-CsOnlineUser to return a collection of all the users who have been enabled for Lync, then sends all that information to Grant-CsExternalAccessPolicy, which assigns the FederationAndPICDefault policy to each and every user in the collection.</span></span>
  
<span data-ttu-id="5de8e-p109">做為額外的範例，假設您已先前指派給 Alex FederationAndPICDefault 原則和現在改變心意並想他變成由通用外部存取原則。您無法明確地將通用原則指派給任何人。它時才使用其他的個別使用者原則指派。因此，如果我們想 Alex 至變成由通用原則、 您要*取消指派*先前已指派給他的任何個別使用者原則。以下是範例命令：</span><span class="sxs-lookup"><span data-stu-id="5de8e-p109">As an additional example, suppose you've previously assigned Alex the FederationAndPICDefault policy and now you've changed your mind and would like him to be managed by the global external access policy. You can't explicitly assign the global policy to anyone. It is only used if no other per-user policy is assigned. Therefore, if we want Alex to be managed by the global policy, you need to  *unassign*  any per-user policy previously assigned to him. Here is an example command:</span></span>
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

<span data-ttu-id="5de8e-p110">此命令會設定為 null 值 ($Null) 指派給 Alex 的外部存取原則的名稱。Null 表示 「 不 」。換句話說，沒有外部存取原則指派給 Alex。當沒有外部存取原則指派給使用者時，該使用者，則取得管理通用原則。</span><span class="sxs-lookup"><span data-stu-id="5de8e-p110">This command sets the name of the external access policy assigned to Alex to a null value ($Null). Null means "nothing". In other words, no external access policy is assigned to Alex. When no external access policy is assigned to a user, that user then gets managed by the global policy.</span></span>
  
<span data-ttu-id="5de8e-p111">若要停用使用 Windows PowerShell 的使用者帳戶，請使用 Azure Active Directory cmdlet 來移除 Alex 的 Skype 商務 Online 授權。如需詳細資訊，請參閱 ＜[停用 Office 365 powershell 的服務存取權](assign-licenses-to-user-accounts-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="5de8e-p111">To disable a user account using Windows PowerShell, use the Azure Active Directory cmdlets to remove Alex's Skype for Business Online license. For more information, see [Disable access to services with Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5de8e-152">See also</span><span class="sxs-lookup"><span data-stu-id="5de8e-152">See also</span></span>

#### 

[<span data-ttu-id="5de8e-153">使用 Office 365 PowerShell 管理商務用 Skype Office</span><span class="sxs-lookup"><span data-stu-id="5de8e-153">Manage Skype for Business Online with Office 365 PowerShell</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)
  
[<span data-ttu-id="5de8e-154">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="5de8e-154">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="5de8e-155">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5de8e-155">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

