---
title: 從商務用 Skype 與 Exchange 移除或停用混合式新式驗證
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/3/2017
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5a91b9e3-1508-475b-93e0-710fa5d5cd2d
ms.collection:
- M365-security-compliance
description: 如果您已啟用混合式新式驗證 (HMA)，找出它並不適合您目前的環境，您可以停用 HMA。 本文說明如何。
ms.openlocfilehash: 91373adf590ad9a69880de20897795ced23d98b8
ms.sourcegitcommit: c8acfa57a22d7d055500f2e8b84a9ef252c70e82
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "36493320"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a><span data-ttu-id="1cdb5-104">從商務用 Skype 與 Exchange 移除或停用混合式新式驗證</span><span class="sxs-lookup"><span data-stu-id="1cdb5-104">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>

<span data-ttu-id="1cdb5-105">如果您已啟用混合式新式驗證 (HMA)，找出它並不適合您目前的環境，您可以停用 HMA。</span><span class="sxs-lookup"><span data-stu-id="1cdb5-105">If you've enabled Hybrid Modern Authentication (HMA) only to find it's unsuitable for your current environment, you can disable HMA.</span></span> <span data-ttu-id="1cdb5-106">本文說明如何。</span><span class="sxs-lookup"><span data-stu-id="1cdb5-106">This article explains how.</span></span>
  
## <a name="who-is-this-article-for"></a><span data-ttu-id="1cdb5-107">本文是誰？</span><span class="sxs-lookup"><span data-stu-id="1cdb5-107">Who is this article for?</span></span>

<span data-ttu-id="1cdb5-108">如果您已針對商務 Online 或內部及/或 Exchange Online 或內部部署啟用 Skype 中的新式驗證，並找到您要停用 HMA，這些步驟適用於您。</span><span class="sxs-lookup"><span data-stu-id="1cdb5-108">If you've enabled Modern Authentication in Skype for Business Online or On-premises, and/or Exchange Online or On-premises and found you need to disable HMA, these steps are for you.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1cdb5-109">如果您是商務用 Skype 商務 Online 或內部部署中，請參閱 '[Skype for Business 拓撲支援新式驗證](https://technet.microsoft.com/en-us/library/mt803262.aspx)' 文章、 有混合拓撲 HMA，而且需要查看支援的拓撲，在您開始之前。</span><span class="sxs-lookup"><span data-stu-id="1cdb5-109">See the '[Skype for Business topologies supported with Modern Authentication](https://technet.microsoft.com/en-us/library/mt803262.aspx)' article if you're in Skype for Business Online or On-premises, have a mixed-topology HMA, and need to look at supported topologies before you begin.</span></span>
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a><span data-ttu-id="1cdb5-110">如何停用混合式新式驗證 (Exchange)</span><span class="sxs-lookup"><span data-stu-id="1cdb5-110">How to disable Hybrid Modern Authentication (Exchange)</span></span>

1. <span data-ttu-id="1cdb5-111">**Exchange 內部部署**： 開啟 Exchange 管理命令介面，並執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="1cdb5-111">**Exchange On-premises**: Open the Exchange Management Shell and run the following commands:</span></span> 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. <span data-ttu-id="1cdb5-112">**Exchange Online**： 使用遠端 PowerShell[連線到 Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) 。</span><span class="sxs-lookup"><span data-stu-id="1cdb5-112">**Exchange Online**: [Connect to Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) with Remote PowerShell.</span></span> <span data-ttu-id="1cdb5-113">執行下列命令，以開啟為 'false' 您*OAuth2ClientProfileEnabled*標幟：</span><span class="sxs-lookup"><span data-stu-id="1cdb5-113">Run the following command to turn your  *OAuth2ClientProfileEnabled*  flag to 'false':</span></span>

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a><span data-ttu-id="1cdb5-114">如何停用混合式新式驗證 (商務用 Skype)</span><span class="sxs-lookup"><span data-stu-id="1cdb5-114">How to disable Hybrid Modern Authentication (Skype for Business)</span></span>

1. <span data-ttu-id="1cdb5-115">**企業內部部署商務用 Skype**： 執行下列命令在 Skype for Business 管理命令介面：</span><span class="sxs-lookup"><span data-stu-id="1cdb5-115">**Skype for Business On-premises**: Run the following commands in Skype for Business Management Shell:</span></span>

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. <span data-ttu-id="1cdb5-116">**線上商務用 Skype**： 使用遠端 PowerShell[連線到商務用 Skype](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) 。</span><span class="sxs-lookup"><span data-stu-id="1cdb5-116">**Skype for Business Online**: [Connect to Skype for Business Online](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) with Remote PowerShell.</span></span> <span data-ttu-id="1cdb5-117">執行下列命令，以停用新式驗證：</span><span class="sxs-lookup"><span data-stu-id="1cdb5-117">Run the following command to disable Modern Authentication:</span></span>

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

<span data-ttu-id="1cdb5-118">[新式驗證概觀連結](hybrid-modern-auth-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="1cdb5-118">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  

