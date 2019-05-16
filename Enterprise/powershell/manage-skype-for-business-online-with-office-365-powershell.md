---
title: 使用 Office 365 PowerShell 管理商務用 Skype Office
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/13/2018
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 摘要︰使用 Office 365 PowerShell 來管理 商務用 Skype Online 原則、每一使用者原則和會議的設定。
ms.openlocfilehash: 33c7247686cc8eb308b8db6d4900c89f693004fb
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068729"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a><span data-ttu-id="48104-103">使用 Office 365 PowerShell 管理商務用 Skype Office</span><span class="sxs-lookup"><span data-stu-id="48104-103">Manage Skype for Business Online with Office 365 PowerShell</span></span>

 <span data-ttu-id="48104-104">**摘要︰** 使用 Office 365 PowerShell 來管理 商務用 Skype Online 原則、每一使用者原則和會議的設定。</span><span class="sxs-lookup"><span data-stu-id="48104-104">**Summary:** Use Office 365 PowerShell to manage Skype for Business Online policies, per-user policies, and meeting settings.</span></span>
  
<span data-ttu-id="48104-105">任何 商務用 Skype Online 系統管理員的其中一個主要工作是管理原則。</span><span class="sxs-lookup"><span data-stu-id="48104-105">One of the primary tasks of any Skype for Business Online administrator is managing policies.</span></span> <span data-ttu-id="48104-106">雖然您可以完成某些 Office 365 系統管理中心中工作，但其他工作會更加快速且更容易在 Office 365 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="48104-106">Although you can accomplish some of these tasks in the Office 365 Admin center, other tasks are much quicker and easier in Office 365 PowerShell.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="48104-107">開始之前</span><span class="sxs-lookup"><span data-stu-id="48104-107">Before you start</span></span>

<span data-ttu-id="48104-108">下載並安裝[商務用 Skype 商務 Online 連接器模組](https://www.microsoft.com/en-us/download/details.aspx?id=39366)中，，然後重新啟動電腦，如果系統提示。</span><span class="sxs-lookup"><span data-stu-id="48104-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/en-us/download/details.aspx?id=39366), and then restart your computer if prompted.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a><span data-ttu-id="48104-109">使用 Skype 商務 Online 系統管理員帳戶名稱和密碼連線</span><span class="sxs-lookup"><span data-stu-id="48104-109">Connect using a Skype for Business Online administrator account name and password</span></span>

1. <span data-ttu-id="48104-110">開啟 Windows PowerShell 命令提示字元並執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="48104-110">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="48104-111">在 [ **Windows PowerShell 認證要求**] 對話方塊中，輸入您商務用 Skype 商務 Online 系統管理員帳戶名稱和密碼，，然後按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="48104-111">In the **Windows PowerShell Credential Request** dialog box, type your Skype for Business Online administrator account name and password, and then click **OK**.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a><span data-ttu-id="48104-112">使用 Skype 商務 Online 系統管理員帳戶具有多重要素驗證連線</span><span class="sxs-lookup"><span data-stu-id="48104-112">Connect using a Skype for Business Online administrator account with multifactor authentication</span></span>

1. <span data-ttu-id="48104-113">開啟 Windows PowerShell 命令提示字元並執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="48104-113">Open a Windows PowerShell command prompt and run the following commands:</span></span>

  ```
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="48104-114">出現提示時**新增 CsOnlineSession**命令，輸入您 Skype 商務 Online 系統管理員帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="48104-114">When prompted by the **New-CsOnlineSession** command, enter your Skype for Business Online administrator account name.</span></span>

3. <span data-ttu-id="48104-115">在**您的帳戶登入**] 對話方塊中，輸入您的 Skype 商務 Online 系統管理員密碼，，然後按一下 [**登入**。</span><span class="sxs-lookup"><span data-stu-id="48104-115">In the **Sign in to your account** dialog box, type your Skype for Business Online administrator password, and then click **Sign in**.</span></span>

4. <span data-ttu-id="48104-116">請遵循**您的帳戶登入**] 對話方塊中的指示，提供其他驗證資訊，例如驗證碼，，然後按一下 [**驗證**。</span><span class="sxs-lookup"><span data-stu-id="48104-116">Follow the instructions in the **Sign in to your account** dialog box to provide additional authentication information, such as a verification code, and then click **Verify**.</span></span>

<span data-ttu-id="48104-117">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="48104-117">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="48104-118">線上商務原則與 Office 365 PowerShell 管理 Skype</span><span class="sxs-lookup"><span data-stu-id="48104-118">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [<span data-ttu-id="48104-119">指派個別使用者 Skype 線上商務原則與 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="48104-119">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a><span data-ttu-id="48104-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48104-120">See also</span></span>

[<span data-ttu-id="48104-121">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="48104-121">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="48104-122">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="48104-122">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

[<span data-ttu-id="48104-123">Skype 商務 PowerShell cmdlet 參考資料</span><span class="sxs-lookup"><span data-stu-id="48104-123">Skype for Business PowerShell cmdlet references</span></span>](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

