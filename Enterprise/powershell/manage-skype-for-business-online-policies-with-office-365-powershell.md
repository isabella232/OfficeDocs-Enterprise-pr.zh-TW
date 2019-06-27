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
description: '摘要: 使用 Office 365 PowerShell 以原則管理商務用 Skype Online 使用者帳戶內容。'
ms.openlocfilehash: f19e262947b40b3e61dc8376b8e2e9c8ec984ff7
ms.sourcegitcommit: c115a3554647167e3770dda6b69dbf5c5de11ed7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2019
ms.locfileid: "35253683"
---
# <a name="manage-skype-for-business-online-policies-with-office-365-powershell"></a><span data-ttu-id="4e1e1-103">線上商務原則與 Office 365 PowerShell 管理 Skype</span><span class="sxs-lookup"><span data-stu-id="4e1e1-103">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>

 <span data-ttu-id="4e1e1-104">**摘要:** 使用 Office 365 PowerShell 以原則管理商務用 Skype Online 使用者帳戶內容。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-104">**Summary:** Use Office 365 PowerShell to manage your Skype for Business Online user account properties with policies.</span></span>
  
<span data-ttu-id="4e1e1-105">若要管理商務用 Skype Online 的許多使用者帳戶屬性, 您必須使用 Office 365 PowerShell 將其指定為原則的屬性。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-105">To manage many properties of user account for Skype for Business Online, you must specify them as properties of policies with Office 365 PowerShell.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="4e1e1-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="4e1e1-106">Before you begin</span></span>

<span data-ttu-id="4e1e1-107">使用這些指示來設定以執行命令 (略過您已完成的步驟):</span><span class="sxs-lookup"><span data-stu-id="4e1e1-107">Use these instructions to get set up to run the commands (skip the steps you have already completed):</span></span>
  
1. <span data-ttu-id="4e1e1-108">下載並安裝[商務用 Skype Online 連接器模組](https://www.microsoft.com/download/details.aspx?id=39366)。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366).</span></span>
    
2. <span data-ttu-id="4e1e1-109">開啟 Windows PowerShell 命令提示字元, 並執行下列命令:</span><span class="sxs-lookup"><span data-stu-id="4e1e1-109">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
```
Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```

<span data-ttu-id="4e1e1-110">出現提示時, 請輸入您的商務用 Skype Online 系統管理員帳戶名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-110">When prompted, enter your Skype for Business Online administrator account name and password.</span></span>
    
## <a name="manage-user-account-policies"></a><span data-ttu-id="4e1e1-111">管理使用者帳戶原則</span><span class="sxs-lookup"><span data-stu-id="4e1e1-111">Manage user account policies</span></span>

<span data-ttu-id="4e1e1-112">許多商務用 Skype Online 使用者帳戶屬性是使用原則來設定。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-112">Many Skype for Business Online user account properties are configured by using policies.</span></span> <span data-ttu-id="4e1e1-113">原則就是可套用至一或多個使用者的設定集合。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-113">Policies are simply collections of settings that can be applied to one or more users.</span></span> <span data-ttu-id="4e1e1-114">若要查看原則的設定方式, 您可以對 FederationAndPICDefault 原則執行這個範例命令:</span><span class="sxs-lookup"><span data-stu-id="4e1e1-114">To take a look at how the a policy has been configured, you can run this example command for the FederationAndPICDefault policy:</span></span>
  
```
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

<span data-ttu-id="4e1e1-115">接著, 您應該會收到如下的內容:</span><span class="sxs-lookup"><span data-stu-id="4e1e1-115">In turn, you should get back something similar to this:</span></span>
  
```
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

<span data-ttu-id="4e1e1-116">在此範例中, 此原則內的值會決定當與同盟使用者通訊時, 可以執行或無法執行的動作。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-116">In this example, the values within this policy determine what a use can or cannot do when it comes to communicating with federated users.</span></span> <span data-ttu-id="4e1e1-117">例如, EnableOutsideAccess 屬性必須設為 True, 使用者才能與組織外部的人員進行通訊。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-117">For example, the EnableOutsideAccess property must be set to True for a user to be able to communicate with people outside the organization.</span></span> <span data-ttu-id="4e1e1-118">請注意, 此屬性不會出現在 Office 365 系統管理中心中。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-118">Note that this property does not appear in the Office 365 Admin center.</span></span> <span data-ttu-id="4e1e1-119">相反地, 屬性會自動設定為 True 或 False 根據您所做的其他選擇。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-119">Instead, the property is automatically set to True or False based on the other selections that you make.</span></span> <span data-ttu-id="4e1e1-120">其他兩個感興趣的屬性為:</span><span class="sxs-lookup"><span data-stu-id="4e1e1-120">The other two properties of interest are:</span></span>
  
- <span data-ttu-id="4e1e1-121">**EnableFederationAccess** 指出使用者是否可以與同盟網域的使用者進行通訊。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-121">**EnableFederationAccess** indicates whether the user can communicate with people from federated domains.</span></span>
    
- <span data-ttu-id="4e1e1-122">**EnablePublicCloudAccess** 指出使用者是否可以與 Windows Live 使用者進行通訊。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-122">**EnablePublicCloudAccess** indicates whether the user can communicate with Windows Live users.</span></span>
    
<span data-ttu-id="4e1e1-123">因此, 您不會直接變更使用者帳戶上的同盟相關屬性 (例如, **get-csuser-EnableFederationAccess $True**)。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-123">Therefore, you don't directly change federation-related properties on user accounts (for example, **Set-CsUser -EnableFederationAccess $True**).</span></span> <span data-ttu-id="4e1e1-124">相反地, 您要指派帳戶具有預先設定之所需屬性值的外部存取原則。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-124">Instead, you assign an account an external access policy that has the desired property values preconfigured.</span></span> <span data-ttu-id="4e1e1-125">如果我們想讓使用者能夠與同盟使用者和 Windows Live 使用者通訊, 則必須將允許通訊類型的原則指派給該使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-125">If we want a user to be able to communicate with federated users and with Windows Live users, that user account must be assigned a policy that allows those types of communication.</span></span>
  
<span data-ttu-id="4e1e1-126">如果您想知道某人是否可以與組織外部的使用者進行通訊, 您必須:</span><span class="sxs-lookup"><span data-stu-id="4e1e1-126">If you want to know whether or not someone can communicate with users from outside the organization, you have to:</span></span>
  
- <span data-ttu-id="4e1e1-127">判斷已指派哪個外部存取原則給該使用者。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-127">Determine which external access policy has been assigned to that user.</span></span>
    
- <span data-ttu-id="4e1e1-128">判斷該原則允許或不允許哪些功能。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-128">Determine which capabilities are or are not allowed by that policy.</span></span>
    
<span data-ttu-id="4e1e1-129">例如, 您可以使用下列命令來執行此動作:</span><span class="sxs-lookup"><span data-stu-id="4e1e1-129">For example, you can do that by using this command:</span></span>
  
```
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

<span data-ttu-id="4e1e1-130">此命令會尋找指派給使用者的原則, 然後尋找該原則中啟用或停用的功能。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-130">This command finds the policy assigned to the user, then finds the capabilities enabled or disabled within that policy.</span></span>
  
<span data-ttu-id="4e1e1-131">若要使用 PowerShell 管理商務用 Skype Online 原則, 請參閱下列 Cmdlet:</span><span class="sxs-lookup"><span data-stu-id="4e1e1-131">To manage Skype for Business Online policies with PowerShell, see the cmdlets for:</span></span>

- <span data-ttu-id="4e1e1-132">[用戶端原則](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#client-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="4e1e1-132">[Client policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#client-policy-cmdlets)</span></span>
- <span data-ttu-id="4e1e1-133">[會議原則](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#conferencing-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="4e1e1-133">[Conferencing policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#conferencing-policy-cmdlets)</span></span>
- <span data-ttu-id="4e1e1-134">[行動原則](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#mobile-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="4e1e1-134">[Mobile policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#mobile-policy-cmdlets)</span></span>
- <span data-ttu-id="4e1e1-135">[線上語音信箱原則](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#online-voicemail-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="4e1e1-135">[Online Voicemail policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#online-voicemail-policy-cmdlets)</span></span>
- <span data-ttu-id="4e1e1-136">[語音路由原則](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#voice-routing-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="4e1e1-136">[Voice Routing policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#voice-routing-policy-cmdlets)</span></span>


> [!NOTE]
> <span data-ttu-id="4e1e1-137">除了名稱之外, 商務用 Skype Online 撥號對應表是每個相關原則。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-137">A Skype for Business Online dial plan is a policy in every respect except the name.</span></span> <span data-ttu-id="4e1e1-138">已選擇名稱「撥號對應表」, 而不是說「撥號原則」, 以便提供與 Office 通訊伺服器和 Exchange 的回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-138">The name "dial plan" was chosen instead of, say, "dialing policy" in order to provide backward compatibility with Office Communications Server and with Exchange.</span></span> 
  
<span data-ttu-id="4e1e1-139">例如, 若要查看所有可用的語音原則, 請執行下列命令:</span><span class="sxs-lookup"><span data-stu-id="4e1e1-139">For example, to look at all the voice policies available for your use, run this command:</span></span>
  
```
Get-CsVoicePolicy
```

> [!NOTE]
> <span data-ttu-id="4e1e1-140">這會傳回所有可用的語音原則清單。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-140">That returns a list of all the voice policies available to you.</span></span> <span data-ttu-id="4e1e1-141">不過請記住, 並非所有原則都可以指派給所有使用者。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-141">Keep in mind, however, that not all policies can be assigned to all users.</span></span> <span data-ttu-id="4e1e1-142">這是因為涉及授權和地理位置的各種限制。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-142">This is due to various restrictions involving licensing and geographic location.</span></span> <span data-ttu-id="4e1e1-143">(所謂的「[使用位置](https://msdn.microsoft.com/en-us/library/azure/dn194136.aspx)」)如果您想知道可以指派給特定使用者的外部存取原則和會議原則, 請使用類似下列的命令:</span><span class="sxs-lookup"><span data-stu-id="4e1e1-143">(The so-called "[usage location](https://msdn.microsoft.com/en-us/library/azure/dn194136.aspx).") If you want to know the external access policies and the conferencing policies that can be assigned to a particular user, use commands similar to these:</span></span> 

```
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

<span data-ttu-id="4e1e1-p106">[ApplicableTo] 參數會對可指派給特定使用者 (例如，Alex Darrow) 的原則限制傳回的資料。根據授權及使用位置的限制，這可能代表所有可用原則的子集。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-p106">The ApplicableTo parameter limits the returned data to policies that can be assigned to the specified user (for example, Alex Darrow). Depending on licensing and usage location restrictions, that might represent a subset of all the available policies.</span></span> 
  
<span data-ttu-id="4e1e1-146">在某些情況下, 不會將原則的屬性與 Office 365 搭配使用, 而有些則只能由 Microsoft 支援人員管理。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-146">In some cases, properties of policies are not used with Office 365, while others can only be managed by Microsoft support personnel.</span></span> 
  
<span data-ttu-id="4e1e1-147">透過商務用 Skype Online, 使用者必須以某種類型的原則來管理。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-147">With Skype for Business Online, users must be managed by a policy of some kind.</span></span> <span data-ttu-id="4e1e1-148">如果有效的原則相關屬性是空白的, 表示有問題的使用者是由全域原則所管理, 除非使用者特別指派個別使用者原則, 否則該原則會自動套用至使用者。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-148">If a valid policy-related property is blank, that means that the user in question is being managed by a global policy, which is a policy that is automatically applied to a user unless he or she is specifically assigned a per-user policy.</span></span> <span data-ttu-id="4e1e1-149">因為我們看不到為使用者帳戶列出的用戶端原則, 所以它是由全域原則管理。</span><span class="sxs-lookup"><span data-stu-id="4e1e1-149">Because we don't see a client policy listed for a user account, it is managed by the global policy.</span></span> <span data-ttu-id="4e1e1-150">您可以使用此命令來決定全域用戶端原則:</span><span class="sxs-lookup"><span data-stu-id="4e1e1-150">You can determine the global client policy with this command:</span></span>
  
```
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a><span data-ttu-id="4e1e1-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e1e1-151">See also</span></span>

#### 

[<span data-ttu-id="4e1e1-152">使用 Office 365 PowerShell 管理商務用 Skype Online</span><span class="sxs-lookup"><span data-stu-id="4e1e1-152">Manage Skype for Business Online with Office 365 PowerShell</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)
  
[<span data-ttu-id="4e1e1-153">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="4e1e1-153">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="4e1e1-154">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="4e1e1-154">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

