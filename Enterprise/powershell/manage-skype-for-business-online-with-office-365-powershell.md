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
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 摘要︰使用 Office 365 PowerShell 來管理 商務用 Skype Online 原則、每一使用者原則和會議的設定。
ms.openlocfilehash: 699f799e823df6192a65147210130ae6493f52eb
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844224"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a><span data-ttu-id="f72e0-103">使用 Office 365 PowerShell 管理商務用 Skype Office</span><span class="sxs-lookup"><span data-stu-id="f72e0-103">Manage Skype for Business Online with Office 365 PowerShell</span></span>

<span data-ttu-id="f72e0-104">任何 商務用 Skype Online 系統管理員的其中一個主要工作是管理原則。</span><span class="sxs-lookup"><span data-stu-id="f72e0-104">One of the primary tasks of any Skype for Business Online administrator is managing policies.</span></span> <span data-ttu-id="f72e0-105">雖然您可以在 Microsoft 365 系統管理中心中完成其中一些工作，但是使用 Office 365 PowerShell 可以更快速、更輕鬆地完成其他工作。</span><span class="sxs-lookup"><span data-stu-id="f72e0-105">Although you can accomplish some of these tasks in the Microsoft 365 admin center, other tasks are much quicker and easier in Office 365 PowerShell.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="f72e0-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="f72e0-106">Before you start</span></span>

<span data-ttu-id="f72e0-107">下載並安裝[商務用 Skype 商務 Online 連接器模組](https://www.microsoft.com/download/details.aspx?id=39366)中，，然後重新啟動電腦，如果系統提示。</span><span class="sxs-lookup"><span data-stu-id="f72e0-107">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366), and then restart your computer if prompted.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a><span data-ttu-id="f72e0-108">使用 Skype 商務 Online 系統管理員帳戶名稱和密碼連線</span><span class="sxs-lookup"><span data-stu-id="f72e0-108">Connect using a Skype for Business Online administrator account name and password</span></span>

1. <span data-ttu-id="f72e0-109">開啟 Windows PowerShell 命令提示字元並執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="f72e0-109">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="f72e0-110">在 [ **Windows PowerShell 認證要求**] 對話方塊中，輸入您商務用 Skype 商務 Online 系統管理員帳戶名稱和密碼，，然後按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="f72e0-110">In the **Windows PowerShell Credential Request** dialog box, type your Skype for Business Online administrator account name and password, and then click **OK**.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a><span data-ttu-id="f72e0-111">使用 Skype 商務 Online 系統管理員帳戶具有多重要素驗證連線</span><span class="sxs-lookup"><span data-stu-id="f72e0-111">Connect using a Skype for Business Online administrator account with multifactor authentication</span></span>

1. <span data-ttu-id="f72e0-112">開啟 Windows PowerShell 命令提示字元並執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="f72e0-112">Open a Windows PowerShell command prompt and run the following commands:</span></span>

  ```powershell
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="f72e0-113">出現提示時**新增 CsOnlineSession**命令，輸入您 Skype 商務 Online 系統管理員帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="f72e0-113">When prompted by the **New-CsOnlineSession** command, enter your Skype for Business Online administrator account name.</span></span>

3. <span data-ttu-id="f72e0-114">在**您的帳戶登入**] 對話方塊中，輸入您的 Skype 商務 Online 系統管理員密碼，，然後按一下 [**登入**。</span><span class="sxs-lookup"><span data-stu-id="f72e0-114">In the **Sign in to your account** dialog box, type your Skype for Business Online administrator password, and then click **Sign in**.</span></span>

4. <span data-ttu-id="f72e0-115">請遵循**您的帳戶登入**] 對話方塊中的指示，提供其他驗證資訊，例如驗證碼，，然後按一下 [**驗證**。</span><span class="sxs-lookup"><span data-stu-id="f72e0-115">Follow the instructions in the **Sign in to your account** dialog box to provide additional authentication information, such as a verification code, and then click **Verify**.</span></span>

<span data-ttu-id="f72e0-116">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="f72e0-116">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="f72e0-117">線上商務原則與 Office 365 PowerShell 管理 Skype</span><span class="sxs-lookup"><span data-stu-id="f72e0-117">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [<span data-ttu-id="f72e0-118">指派個別使用者 Skype 線上商務原則與 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f72e0-118">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a><span data-ttu-id="f72e0-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f72e0-119">See also</span></span>

[<span data-ttu-id="f72e0-120">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="f72e0-120">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="f72e0-121">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f72e0-121">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

[<span data-ttu-id="f72e0-122">Skype 商務 PowerShell cmdlet 參考資料</span><span class="sxs-lookup"><span data-stu-id="f72e0-122">Skype for Business PowerShell cmdlet references</span></span>](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

