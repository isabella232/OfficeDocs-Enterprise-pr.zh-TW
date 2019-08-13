---
title: 線上商務原則與 Office 365 PowerShell 管理 Skype
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/26/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: 摘要： 使用 Office 365 PowerShell 來管理您的 Skype 線上商務原則的使用者帳戶內容。
ms.openlocfilehash: 4b0d45e89910c7fb1a215f78690cfc2fdb17c472
ms.sourcegitcommit: d58cdc7b2296df12f7a05d14ba05ab224ffb3e0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "36302725"
---
# <a name="manage-skype-for-business-online-policies-with-office-365-powershell"></a><span data-ttu-id="d5c78-103">線上商務原則與 Office 365 PowerShell 管理 Skype</span><span class="sxs-lookup"><span data-stu-id="d5c78-103">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>

 <span data-ttu-id="d5c78-104">**摘要：** 使用 Office 365 PowerShell 來管理您的 Skype 線上商務原則的使用者帳戶內容。</span><span class="sxs-lookup"><span data-stu-id="d5c78-104">**Summary:** Use Office 365 PowerShell to manage your Skype for Business Online user account properties with policies.</span></span>
  
<span data-ttu-id="d5c78-105">若要管理商務用 Skype 使用者帳戶的許多屬性，您必須將它們指定為屬性的原則與 Office 365 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d5c78-105">To manage many properties of user account for Skype for Business Online, you must specify them as properties of policies with Office 365 PowerShell.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="d5c78-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="d5c78-106">Before you begin</span></span>

<span data-ttu-id="d5c78-107">使用這些指示以取得設定，請執行命令 （略過您已經完成的步驟）：</span><span class="sxs-lookup"><span data-stu-id="d5c78-107">Use these instructions to get set up to run the commands (skip the steps you have already completed):</span></span>
  
1. <span data-ttu-id="d5c78-108">下載並安裝[商務用 Skype 商務 Online 連接器模組](https://www.microsoft.com/download/details.aspx?id=39366)。</span><span class="sxs-lookup"><span data-stu-id="d5c78-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366).</span></span>
    
2. <span data-ttu-id="d5c78-109">開啟 Windows PowerShell 命令提示字元並執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="d5c78-109">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
```
Import-Module SkypeOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```

<span data-ttu-id="d5c78-110">出現提示時，輸入您 Skype 商務 Online 系統管理員帳戶名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="d5c78-110">When prompted, enter your Skype for Business Online administrator account name and password.</span></span>
    
## <a name="manage-user-account-policies"></a><span data-ttu-id="d5c78-111">管理使用者帳戶原則</span><span class="sxs-lookup"><span data-stu-id="d5c78-111">Manage user account policies</span></span>

<span data-ttu-id="d5c78-112">許多 Skype for Business Online 的使用者帳戶屬性會設定使用原則。</span><span class="sxs-lookup"><span data-stu-id="d5c78-112">Many Skype for Business Online user account properties are configured by using policies.</span></span> <span data-ttu-id="d5c78-113">原則是只可套用至一或多個使用者的設定集合。</span><span class="sxs-lookup"><span data-stu-id="d5c78-113">Policies are simply collections of settings that can be applied to one or more users.</span></span> <span data-ttu-id="d5c78-114">若要查看如何原則已設定，您可以執行此範例命令，FederationAndPICDefault 原則：</span><span class="sxs-lookup"><span data-stu-id="d5c78-114">To take a look at how the a policy has been configured, you can run this example command for the FederationAndPICDefault policy:</span></span>
  
```
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

<span data-ttu-id="d5c78-115">接著，您應該會得到類似：</span><span class="sxs-lookup"><span data-stu-id="d5c78-115">In turn, you should get back something similar to this:</span></span>
  
```
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

<span data-ttu-id="d5c78-116">在這個範例中，此原則內的值會判斷使用可以或提到與同盟使用者進行通訊時，無法執行。</span><span class="sxs-lookup"><span data-stu-id="d5c78-116">In this example, the values within this policy determine what a use can or cannot do when it comes to communicating with federated users.</span></span> <span data-ttu-id="d5c78-117">例如，EnableOutsideAccess 屬性必須設為 True，使用者能夠與組織外的人員進行通訊。</span><span class="sxs-lookup"><span data-stu-id="d5c78-117">For example, the EnableOutsideAccess property must be set to True for a user to be able to communicate with people outside the organization.</span></span> <span data-ttu-id="d5c78-118">請注意，此屬性不會出現在 Microsoft 365 系統管理中心。</span><span class="sxs-lookup"><span data-stu-id="d5c78-118">Note that this property does not appear in the Microsoft 365 admin center.</span></span> <span data-ttu-id="d5c78-119">相反地，屬性會自動設為 True 或 False 基於其他您所做的選擇。</span><span class="sxs-lookup"><span data-stu-id="d5c78-119">Instead, the property is automatically set to True or False based on the other selections that you make.</span></span> <span data-ttu-id="d5c78-120">會感興趣的其他兩個屬性：</span><span class="sxs-lookup"><span data-stu-id="d5c78-120">The other two properties of interest are:</span></span>
  
- <span data-ttu-id="d5c78-121">**EnableFederationAccess** 指出使用者是否可以與同盟網域的使用者進行通訊。</span><span class="sxs-lookup"><span data-stu-id="d5c78-121">**EnableFederationAccess** indicates whether the user can communicate with people from federated domains.</span></span>
    
- <span data-ttu-id="d5c78-122">**EnablePublicCloudAccess** 指出使用者是否可以與 Windows Live 使用者進行通訊。</span><span class="sxs-lookup"><span data-stu-id="d5c78-122">**EnablePublicCloudAccess** indicates whether the user can communicate with Windows Live users.</span></span>
    
<span data-ttu-id="d5c78-123">因此，您不直接變更使用者帳戶 (例如， **Set-csuser-EnableFederationAccess $True**) 上的同盟相關的屬性。</span><span class="sxs-lookup"><span data-stu-id="d5c78-123">Therefore, you don't directly change federation-related properties on user accounts (for example, **Set-CsUser -EnableFederationAccess $True**).</span></span> <span data-ttu-id="d5c78-124">相反地，您指派給帳戶已預先設定的所需的屬性值的外部存取原則。</span><span class="sxs-lookup"><span data-stu-id="d5c78-124">Instead, you assign an account an external access policy that has the desired property values preconfigured.</span></span> <span data-ttu-id="d5c78-125">如果我們希望使用者能夠與同盟使用者並與 Windows Live 使用者進行通訊時，該使用者帳戶必須被指派的原則，可讓這些類型的通訊。</span><span class="sxs-lookup"><span data-stu-id="d5c78-125">If we want a user to be able to communicate with federated users and with Windows Live users, that user account must be assigned a policy that allows those types of communication.</span></span>
  
<span data-ttu-id="d5c78-126">如果您想要知道有人可以與彼此來自組織外部的使用者，您必須：</span><span class="sxs-lookup"><span data-stu-id="d5c78-126">If you want to know whether or not someone can communicate with users from outside the organization, you have to:</span></span>
  
- <span data-ttu-id="d5c78-127">判斷已指派哪個外部存取原則給該使用者。</span><span class="sxs-lookup"><span data-stu-id="d5c78-127">Determine which external access policy has been assigned to that user.</span></span>
    
- <span data-ttu-id="d5c78-128">判斷該原則允許或不允許哪些功能。</span><span class="sxs-lookup"><span data-stu-id="d5c78-128">Determine which capabilities are or are not allowed by that policy.</span></span>
    
<span data-ttu-id="d5c78-129">例如，您可以這麼做藉由使用此命令：</span><span class="sxs-lookup"><span data-stu-id="d5c78-129">For example, you can do that by using this command:</span></span>
  
```
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

<span data-ttu-id="d5c78-130">這個命令尋找指派給使用者，然後尋找功能啟用或停用該原則內的原則。</span><span class="sxs-lookup"><span data-stu-id="d5c78-130">This command finds the policy assigned to the user, then finds the capabilities enabled or disabled within that policy.</span></span>
  
<span data-ttu-id="d5c78-131">若要管理 Skype 線上商務原則與 PowerShell，請參閱 < 的 cmdlet:</span><span class="sxs-lookup"><span data-stu-id="d5c78-131">To manage Skype for Business Online policies with PowerShell, see the cmdlets for:</span></span>

- <span data-ttu-id="d5c78-132">[用戶端原則](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#client-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="d5c78-132">[Client policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#client-policy-cmdlets)</span></span>
- <span data-ttu-id="d5c78-133">[會議原則](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#conferencing-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="d5c78-133">[Conferencing policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#conferencing-policy-cmdlets)</span></span>
- <span data-ttu-id="d5c78-134">[行動原則](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#mobile-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="d5c78-134">[Mobile policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#mobile-policy-cmdlets)</span></span>
- <span data-ttu-id="d5c78-135">[線上語音信箱原則](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#online-voicemail-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="d5c78-135">[Online Voicemail policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#online-voicemail-policy-cmdlets)</span></span>
- <span data-ttu-id="d5c78-136">[語音路由原則](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#voice-routing-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="d5c78-136">[Voice Routing policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#voice-routing-policy-cmdlets)</span></span>


> [!NOTE]
> <span data-ttu-id="d5c78-137">Skype 商務 Online 撥號對應表是在每個方面，除了名稱的原則。</span><span class="sxs-lookup"><span data-stu-id="d5c78-137">A Skype for Business Online dial plan is a policy in every respect except the name.</span></span> <span data-ttu-id="d5c78-138">而不是，說: 「 撥號原則 」 選擇名稱 」 撥號對應表 」，是為了提供回溯相容性與 Office Communications Server 和 Exchange。</span><span class="sxs-lookup"><span data-stu-id="d5c78-138">The name "dial plan" was chosen instead of, say, "dialing policy" in order to provide backward compatibility with Office Communications Server and with Exchange.</span></span> 
  
<span data-ttu-id="d5c78-139">例如，若要查看所有可供您使用的語音原則執行此命令：</span><span class="sxs-lookup"><span data-stu-id="d5c78-139">For example, to look at all the voice policies available for your use, run this command:</span></span>
  
```
Get-CsVoicePolicy
```

> [!NOTE]
> <span data-ttu-id="d5c78-140">這會傳回所有可用的語音原則清單。</span><span class="sxs-lookup"><span data-stu-id="d5c78-140">That returns a list of all the voice policies available to you.</span></span> <span data-ttu-id="d5c78-141">請記住，不過，並非所有原則可以指派給所有使用者。</span><span class="sxs-lookup"><span data-stu-id="d5c78-141">Keep in mind, however, that not all policies can be assigned to all users.</span></span> <span data-ttu-id="d5c78-142">這是因為涉及授權和地理位置的各種限制。</span><span class="sxs-lookup"><span data-stu-id="d5c78-142">This is due to various restrictions involving licensing and geographic location.</span></span> <span data-ttu-id="d5c78-143">（所謂 」 的[使用狀況的位置](https://msdn.microsoft.com/en-us/library/azure/dn194136.aspx)。 」）如果您想要知道的外部存取原則和可指派給特定使用者的會議原則，請使用類似如下的命令：</span><span class="sxs-lookup"><span data-stu-id="d5c78-143">(The so-called "[usage location](https://msdn.microsoft.com/en-us/library/azure/dn194136.aspx).") If you want to know the external access policies and the conferencing policies that can be assigned to a particular user, use commands similar to these:</span></span> 

```
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

<span data-ttu-id="d5c78-p106">[ApplicableTo] 參數會對可指派給特定使用者 (例如，Alex Darrow) 的原則限制傳回的資料。根據授權及使用位置的限制，這可能代表所有可用原則的子集。</span><span class="sxs-lookup"><span data-stu-id="d5c78-p106">The ApplicableTo parameter limits the returned data to policies that can be assigned to the specified user (for example, Alex Darrow). Depending on licensing and usage location restrictions, that might represent a subset of all the available policies.</span></span> 
  
<span data-ttu-id="d5c78-146">在某些情況下，屬性的原則不會使用與 Office 365，而其他人只能管理由 Microsoft 支援人員。</span><span class="sxs-lookup"><span data-stu-id="d5c78-146">In some cases, properties of policies are not used with Office 365, while others can only be managed by Microsoft support personnel.</span></span> 
  
<span data-ttu-id="d5c78-147">與 Skype for Business Online，使用者必須受管理的某種類型的原則。</span><span class="sxs-lookup"><span data-stu-id="d5c78-147">With Skype for Business Online, users must be managed by a policy of some kind.</span></span> <span data-ttu-id="d5c78-148">如果有效原則相關的屬性是空白的這表示有問題的使用者由全域原則，也就是除非他或她特別指派個別使用者原則會自動套用至使用者的原則。</span><span class="sxs-lookup"><span data-stu-id="d5c78-148">If a valid policy-related property is blank, that means that the user in question is being managed by a global policy, which is a policy that is automatically applied to a user unless he or she is specifically assigned a per-user policy.</span></span> <span data-ttu-id="d5c78-149">我們看不到所列出的使用者帳戶的用戶端原則，因為它被管理由全域原則。</span><span class="sxs-lookup"><span data-stu-id="d5c78-149">Because we don't see a client policy listed for a user account, it is managed by the global policy.</span></span> <span data-ttu-id="d5c78-150">您可以決定全域的用戶端原則中使用此命令：</span><span class="sxs-lookup"><span data-stu-id="d5c78-150">You can determine the global client policy with this command:</span></span>
  
```
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a><span data-ttu-id="d5c78-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5c78-151">See also</span></span>

#### 

[<span data-ttu-id="d5c78-152">使用 Office 365 PowerShell 管理商務用 Skype Online</span><span class="sxs-lookup"><span data-stu-id="d5c78-152">Manage Skype for Business Online with Office 365 PowerShell</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)
  
[<span data-ttu-id="d5c78-153">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="d5c78-153">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="d5c78-154">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5c78-154">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

