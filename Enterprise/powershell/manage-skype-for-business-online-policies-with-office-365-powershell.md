---
title: "線上商務原則與 Office 365 PowerShell 管理 Skype"
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
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: "摘要： 使用 Office 365 PowerShell 來管理您 Skype 商務線上與原則的使用者帳戶屬性。"
ms.openlocfilehash: 9b3877d2680b2b36d155cb5dd2a69fa21c972fe3
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="manage-skype-for-business-online-policies-with-office-365-powershell"></a><span data-ttu-id="2c2cd-103">線上商務原則與 Office 365 PowerShell 管理 Skype</span><span class="sxs-lookup"><span data-stu-id="2c2cd-103">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>

 <span data-ttu-id="2c2cd-104">**摘要：**使用 Office 365 PowerShell 來管理您 Skype 商務線上與原則的使用者帳戶屬性。</span><span class="sxs-lookup"><span data-stu-id="2c2cd-104">**Summary:** Use Office 365 PowerShell to manage your Skype for Business Online user account properties with policies.</span></span>
  
<span data-ttu-id="2c2cd-105">商務 online 中管理 Skype 的使用者帳戶的許多屬性，則必須將其指定為原則與 Office 365 PowerShell 的屬性。</span><span class="sxs-lookup"><span data-stu-id="2c2cd-105">To manage many properties of user account for Skype for Business Online, you must specify them as properties of policies with Office 365 PowerShell.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="2c2cd-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="2c2cd-106">Before you begin</span></span>

<span data-ttu-id="2c2cd-107">使用這些指示來取得設定設定來執行命令 （略過您已經完成的步驟）：</span><span class="sxs-lookup"><span data-stu-id="2c2cd-107">Use these instructions to get set up to run the commands (skip the steps you have already completed):</span></span>
  
1. <span data-ttu-id="2c2cd-108">下載並安裝[Skype for Business Online 連接器模組](https://www.microsoft.com/en-us/download/details.aspx?id=39366)。</span><span class="sxs-lookup"><span data-stu-id="2c2cd-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/en-us/download/details.aspx?id=39366).</span></span>
    
2. <span data-ttu-id="2c2cd-109">開啟 Windows PowerShell 命令提示字元並執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="2c2cd-109">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
```
Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```

<span data-ttu-id="2c2cd-110">出現提示時，輸入您 Skype 線上商務系統管理員帳戶名稱及密碼。</span><span class="sxs-lookup"><span data-stu-id="2c2cd-110">When prompted, enter your Skype for Business Online administrator account name and password.</span></span>
    
## <a name="manage-user-account-policies"></a><span data-ttu-id="2c2cd-111">管理使用者帳戶原則</span><span class="sxs-lookup"><span data-stu-id="2c2cd-111">Manage user account policies</span></span>

<span data-ttu-id="2c2cd-p101">使用原則來設定許多 Skype 商務線上的使用者帳戶屬性。原則是只可套用至一或多個使用者的設定集合。若要看看如何設定的原則，您可以執行此命令範例 FederationAndPICDefault 原則：</span><span class="sxs-lookup"><span data-stu-id="2c2cd-p101">Many Skype for Business Online user account properties are configured by using policies. Policies are simply collections of settings that can be applied to one or more users. To take a look at how the a policy has been configured, you can run this example command for the FederationAndPICDefault policy:</span></span>
  
```
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

<span data-ttu-id="2c2cd-115">接著，您應該會得到類似：</span><span class="sxs-lookup"><span data-stu-id="2c2cd-115">In turn, you should get back something similar to this:</span></span>
  
```
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

<span data-ttu-id="2c2cd-p102">在這個範例中，此原則內的數值決定使用的可以或無法執行專職與同盟使用者進行通訊的作業。例如，EnableOutsideAccess 屬性必須設定為 True 的使用者能夠與組織外部的人員通訊。請注意，這個屬性不會出現在 Office 365 系統管理中心。而屬性會自動設為 True 或 False 根據所做的選擇。會感興趣的其他兩個屬性：</span><span class="sxs-lookup"><span data-stu-id="2c2cd-p102">In this example, the values within this policy determine what a use can or cannot do when it comes to communicating with federated users. For example, the EnableOutsideAccess property must be set to True for a user to be able to communicate with people outside the organization. Note that this property does not appear in the Office 365 Admin center. Instead, the property is automatically set to True or False based on the other selections that you make. The other two properties of interest are:</span></span>
  
- <span data-ttu-id="2c2cd-121">**EnableFederationAccess**指出使用者是否可以與來自同盟網域的人通訊。</span><span class="sxs-lookup"><span data-stu-id="2c2cd-121">**EnableFederationAccess** indicates whether the user can communicate with people from federated domains.</span></span>
    
- <span data-ttu-id="2c2cd-122">**EnablePublicCloudAccess**指出使用者是否可以與 Windows Live 使用者進行通訊。</span><span class="sxs-lookup"><span data-stu-id="2c2cd-122">**EnablePublicCloudAccess** indicates whether the user can communicate with Windows Live users.</span></span>
    
<span data-ttu-id="2c2cd-p103">因此，您不直接變更的使用者帳戶 (例如， **Set-csuser-EnableFederationAccess $True**) 上的同盟相關屬性。而是您指派帳戶已預先設定的所需的屬性值的外部存取原則。如果我們希望使用者能夠與同盟使用者及 Windows Live 使用者通訊，該使用者帳戶必須被指派可讓通訊這些類型的原則。</span><span class="sxs-lookup"><span data-stu-id="2c2cd-p103">Therefore, you don't directly change federation-related properties on user accounts (for example, **Set-CsUser -EnableFederationAccess $True**). Instead, you assign an account an external access policy that has the desired property values preconfigured. If we want a user to be able to communicate with federated users and with Windows Live users, that user account must be assigned a policy that allows those types of communication.</span></span>
  
<span data-ttu-id="2c2cd-126">如果您想要知道某人可與組織外部的使用者通訊，您必須：</span><span class="sxs-lookup"><span data-stu-id="2c2cd-126">If you want to know whether or not someone can communicate with users from outside the organization, you have to:</span></span>
  
- <span data-ttu-id="2c2cd-127">判斷已指派哪個外部存取原則給該使用者。</span><span class="sxs-lookup"><span data-stu-id="2c2cd-127">Determine which external access policy has been assigned to that user.</span></span>
    
- <span data-ttu-id="2c2cd-128">判斷該原則允許或不允許哪些功能。</span><span class="sxs-lookup"><span data-stu-id="2c2cd-128">Determine which capabilities are or are not allowed by that policy.</span></span>
    
<span data-ttu-id="2c2cd-129">例如，您可以使用此命令執行的：</span><span class="sxs-lookup"><span data-stu-id="2c2cd-129">For example, you can do that by using this command:</span></span>
  
```
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

<span data-ttu-id="2c2cd-130">此命令會找出指派給使用者，則會找出功能已啟用或停用該原則內的原則。</span><span class="sxs-lookup"><span data-stu-id="2c2cd-130">This command finds the policy assigned to the user, then finds the capabilities enabled or disabled within that policy.</span></span>
  
<span data-ttu-id="2c2cd-p104">請注意任何 cmdlet 建立或修改的原則。您必須使用前 Office 365 所提供的原則。如果您想要查看如何在不同的原則，您可以使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="2c2cd-p104">Note that there are no cmdlets for creating or for modifying policies. You must use the policies pre-supplied by Office 365. If you want to take a look at the different policies available, you can use these commands:</span></span>
  
- <span data-ttu-id="2c2cd-134">Get-csclientpolicy</span><span class="sxs-lookup"><span data-stu-id="2c2cd-134">Get-CsClientPolicy</span></span>       
- <span data-ttu-id="2c2cd-135">Get-csconferencingpolicy</span><span class="sxs-lookup"><span data-stu-id="2c2cd-135">Get-CsConferencingPolicy</span></span>        
- <span data-ttu-id="2c2cd-136">Get-csdialplan</span><span class="sxs-lookup"><span data-stu-id="2c2cd-136">Get-CsDialPlan</span></span>            
- <span data-ttu-id="2c2cd-137">Get-csexternalaccesspolicy</span><span class="sxs-lookup"><span data-stu-id="2c2cd-137">Get-CsExternalAccessPolicy</span></span>                         
- <span data-ttu-id="2c2cd-138">Get-cshostedvoicemailpolicy</span><span class="sxs-lookup"><span data-stu-id="2c2cd-138">Get-CsHostedVoicemailPolicy</span></span>                        
- <span data-ttu-id="2c2cd-139">Get-cspresencepolicy</span><span class="sxs-lookup"><span data-stu-id="2c2cd-139">Get-CsPresencePolicy</span></span>                               
- <span data-ttu-id="2c2cd-140">Get-csvoicepolicy</span><span class="sxs-lookup"><span data-stu-id="2c2cd-140">Get-CsVoicePolicy</span></span>                                  

> [!NOTE]
> <span data-ttu-id="2c2cd-p105">線上商務撥號 Skype 是在每個方面除了名稱的原則。名稱"撥號對應表"的選擇而不是，假設"撥號原則 」 以使用 Office Communications Server 與 Exchange 提供回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="2c2cd-p105">A Skype for Business Online dial plan is a policy in every respect except the name. The name "dial plan" was chosen instead of, say, "dialing policy" in order to provide backward compatibility with Office Communications Server and with Exchange.</span></span> 
  
<span data-ttu-id="2c2cd-143">例如，若要查看所有可供您使用的語音原則執行此命令：</span><span class="sxs-lookup"><span data-stu-id="2c2cd-143">For example, to look at all the voice policies available for your use, run this command:</span></span>
  
```
Get-CsVoicePolicy
```

> [!NOTE]
> <span data-ttu-id="2c2cd-p106">會傳回所有語音原則清單提供給您。請記住，但不是所有原則可以指派給所有使用者。這是因為各種有關授權和地理位置的限制。（所謂 」 的[使用狀況位置](https://msdn.microsoft.com/en-us/library/azure/dn194136.aspx)。"）如果您想要知道的外部存取原則及可以指派給特定使用者的會議原則、 使用類似以下的命令：</span><span class="sxs-lookup"><span data-stu-id="2c2cd-p106">That returns a list of all the voice policies available to you. Keep in mind, however, that not all policies can be assigned to all users. This is due to various restrictions involving licensing and geographic location. (The so-called "[usage location](https://msdn.microsoft.com/en-us/library/azure/dn194136.aspx).") If you want to know the external access policies and the conferencing policies that can be assigned to a particular user, use commands similar to these:</span></span> 

```
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

<span data-ttu-id="2c2cd-p107">[ApplicableTo] 參數會對可指派給特定使用者 (例如，Alex Darrow) 的原則限制傳回的資料。根據授權及使用位置的限制，這可能代表所有可用原則的子集。</span><span class="sxs-lookup"><span data-stu-id="2c2cd-p107">The ApplicableTo parameter limits the returned data to policies that can be assigned to the specified user (for example, Alex Darrow). Depending on licensing and usage location restrictions, that might represent a subset of all the available policies.</span></span> 
  
<span data-ttu-id="2c2cd-150">在某些情況下，屬性的原則不使用 Office 365 時其他人只能管理 Microsoft 支援人員。</span><span class="sxs-lookup"><span data-stu-id="2c2cd-150">In some cases, properties of policies are not used with Office 365, while others can only be managed by Microsoft support personnel.</span></span> 
  
<span data-ttu-id="2c2cd-p108">具有商務 online Skype，使用者還必須管理某種類型的原則影響。如果是有效的原則相關屬性是空白的這表示有問題的使用者會受全域原則，這是除非他就會指派個別使用者原則會自動套用到使用者的原則。因為我們未看見列出的使用者帳戶的用戶端原則，它會由通用原則管理。您可以決定此命令的通用用戶端原則：</span><span class="sxs-lookup"><span data-stu-id="2c2cd-p108">With Skype for Business Online, users must be managed by a policy of some kind. If a valid policy-related property is blank, that means that the user in question is being managed by a global policy, which is a policy that is automatically applied to a user unless he or she is specifically assigned a per-user policy. Because we don't see a client policy listed for a user account, it is managed by the global policy. You can determine the global client policy with this command:</span></span>
  
```
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a><span data-ttu-id="2c2cd-155">See also</span><span class="sxs-lookup"><span data-stu-id="2c2cd-155">See also</span></span>

#### 

[<span data-ttu-id="2c2cd-156">使用 Office 365 PowerShell 管理商務用 Skype Office</span><span class="sxs-lookup"><span data-stu-id="2c2cd-156">Manage Skype for Business Online with Office 365 PowerShell</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)
  
[<span data-ttu-id="2c2cd-157">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="2c2cd-157">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="2c2cd-158">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2c2cd-158">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

