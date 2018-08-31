---
title: 從商務用 Skype 與 Exchange 移除或停用混合式新式驗證
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 11/3/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5a91b9e3-1508-475b-93e0-710fa5d5cd2d
description: 如果您已啟用混合現代驗證 (HMA)，僅來尋找它並不適合您目前的環境，您可以停用 HMA。本文說明如何。
ms.openlocfilehash: fff9599641630386183ab9e1a0b8f597f0ba6e5b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540171"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a><span data-ttu-id="dacae-104">從商務用 Skype 與 Exchange 移除或停用混合式新式驗證</span><span class="sxs-lookup"><span data-stu-id="dacae-104">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>

<span data-ttu-id="dacae-p102">如果您已啟用混合現代驗證 (HMA)，僅來尋找它並不適合您目前的環境，您可以停用 HMA。本文說明如何。</span><span class="sxs-lookup"><span data-stu-id="dacae-p102">If you've enabled Hybrid Modern Authentication (HMA) only to find it's unsuitable for your current environment, you can disable HMA. This article explains how.</span></span>
  
## <a name="who-is-this-article-for"></a><span data-ttu-id="dacae-107">本文是誰？</span><span class="sxs-lookup"><span data-stu-id="dacae-107">Who is this article for?</span></span>

<span data-ttu-id="dacae-108">如果您已啟用經過驗證的 Skype 線上商務或內部，和/或 Exchange Online 或內部部署並找到您要停用 HMA，這些步驟就是您。</span><span class="sxs-lookup"><span data-stu-id="dacae-108">If you've enabled Modern Authentication in Skype for Business Online or On-premises, and/or Exchange Online or On-premises and found you need to disable HMA, these steps are for you.</span></span>
  
 <span data-ttu-id="dacae-109">**重要**如果您正處於 Skype 線上商務或內部看到 '[現代驗證支援商務拓撲 Skype](https://technet.microsoft.com/en-us/library/mt803262.aspx)' 文章、 有混合拓撲 HMA，且需要之前查看支援的拓撲。</span><span class="sxs-lookup"><span data-stu-id="dacae-109">**Important** See the ' [Skype for Business topologies supported with Modern Authentication](https://technet.microsoft.com/en-us/library/mt803262.aspx)' article if you're in Skype for Business Online or On-premises, have a mixed-topology HMA, and need to look at supported topologies before you begin.</span></span>
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a><span data-ttu-id="dacae-110">如何停用混合現代驗證 (Exchange)</span><span class="sxs-lookup"><span data-stu-id="dacae-110">How to disable Hybrid Modern Authentication (Exchange)</span></span>

1. <span data-ttu-id="dacae-111">**Exchange 內部部署**： 開啟 Exchange 管理命令介面，並執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="dacae-111">**Exchange On-premises**: Open the Exchange Management Shell and run the following command.</span></span> 
    
1. <span data-ttu-id="dacae-112">Set-organizationconfig-OAuth2ClientProfileEnabled $false</span><span class="sxs-lookup"><span data-stu-id="dacae-112">Set-OrganizationConfig -OAuth2ClientProfileEnabled $false</span></span>
    
2. <span data-ttu-id="dacae-113">Set-authserver-Identity evoSTS-IsDefaultAuthorizationEndpoint $false</span><span class="sxs-lookup"><span data-stu-id="dacae-113">Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false</span></span>
    
2. <span data-ttu-id="dacae-p103">**Exchange Online**： 連線至遠端 PowerShell 與 Exchange Online。執行下列命令來開啟為 'false' 您*OAuth2ClientProfileEnabled*旗標。</span><span class="sxs-lookup"><span data-stu-id="dacae-p103">**Exchange Online**: Connect to Exchange Online with Remote PowerShell. Run the following command to turn your  *OAuth2ClientProfileEnabled*  flag to 'false'.</span></span> 
    
1. <span data-ttu-id="dacae-116">Set-organizationconfig-OAuth2ClientProfileEnabled: $false</span><span class="sxs-lookup"><span data-stu-id="dacae-116">Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false</span></span>
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a><span data-ttu-id="dacae-117">如何停用混合現代驗證 (Skype 企業版)</span><span class="sxs-lookup"><span data-stu-id="dacae-117">How to disable Hybrid Modern Authentication (Skype for Business)</span></span>

1. <span data-ttu-id="dacae-118">**企業內部的 Skype**: Skype 中執行下列命令商務管理命令介面。</span><span class="sxs-lookup"><span data-stu-id="dacae-118">**Skype for Business On-premises**: Run the following commands in Skype for Business Management Shell.</span></span>
    
1. <span data-ttu-id="dacae-119">Set-csoauthconfiguration ClientAuthorizationOAuthServerIdentity""</span><span class="sxs-lookup"><span data-stu-id="dacae-119">Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""</span></span>
    
2. <span data-ttu-id="dacae-p104">**線上商務的 Skype**: for Business 線上使用遠端 PowerShell 連線至 Skype。執行下列命令以停用摩登的驗證。</span><span class="sxs-lookup"><span data-stu-id="dacae-p104">**Skype for Business Online**: Connect to Skype for Business Online with Remote PowerShell. Run the following command to disable Modern Authentication.</span></span> 
    
1. <span data-ttu-id="dacae-122">Set-csoauthconfiguration ClientAdalAuthOverride 不允許</span><span class="sxs-lookup"><span data-stu-id="dacae-122">Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed</span></span>
    
<span data-ttu-id="dacae-123">[現代驗證概觀連結](hybrid-modern-auth-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="dacae-123">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  

