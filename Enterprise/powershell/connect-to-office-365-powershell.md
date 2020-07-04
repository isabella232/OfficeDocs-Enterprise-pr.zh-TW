---
title: 連線至 Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/30/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: 使用 Office 365 PowerShell 連線至您的 Office 365 組織，以從命令列執行系統管理中心工作。
ms.openlocfilehash: 0906da2b8773973236bc8cb6ef273d1a14528bfd
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997419"
---
# <a name="connect-to-office-365-powershell"></a>連線至 Office 365 PowerShell

Office 365 PowerShell 可讓您從命令列管理 Office 365 的設定。 連線至 Office 365 PowerShell 是簡單的程序，您可以在其中安裝必要的軟體，然後連線至您的 Office 365 組織。 

您用來連線至 Office 365 及管理使用者帳戶、群組和授權的 PowerShell 模組有兩個版本：

- Azure Active Directory PowerShell for Graph (名稱中包含 **AzureAD** 的 Cmdlet)
- 適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組 (名稱中包含 **MSol** 的 Cmdlet) 

自本文發行日期起，Azure Active Directory PowerShell for Graph 模組無法完全取代適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組中針對使用者、群組和授權管理的 Cmdlet 功能。 在許多情況下，您需要同時使用這兩個版本。 您可以在同一部電腦上安全地安裝這兩個版本。

## <a name="what-do-you-need-to-know-before-you-begin"></a>開始之前有哪些須知？

您可以使用下列 Windows 版本：
    
  - Windows 10、Windows 8.1、Windows 8 或 Windows 7 Service Pack 1 (SP1) 
    
  - Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012 或 Windows Server 2008 R2 SP1

    > [!NOTE]
    > 針對 Azure Active Directory PowerShell 的圖表模組，請務必使用 PowerShell 版本 5.1 或更新版本。 針對適用於 Windows PowerShell 模組的 Microsoft Azure Active Directory 模組，請務必使用 PowerShell 版本 5.1 或更新版本 (最多可至 PowerShell 版本 6)。 無法使用 PowerShell 版本 7。 若為 Windows 8.1、Windows 8、Windows 7 Service Pack 1 (SP1)、Windows Server 2012 R2、Windows Server 2012 和 Windows Server 2008 R2 SP1，請下載並安裝 [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616). 
    
    > [!NOTE]
    > Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.
    
這些程序適用於屬於 Office 365 系統管理員角色成員的使用者。 如需詳細資訊，請參閱[關於 Office 365 系統管理員角色](https://go.microsoft.com/fwlink/p/?LinkId=532367)。


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a>與 Azure Active Directory PowerShell for Graph 模組連線

在Azure Active Directory PowerShell 圖表模組中的命令，其 Cmdlet 名稱中會包含 **AzureAD**。 您可以安裝 [Azure Active Directory PowerShell 的圖表](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)或 [Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-az-ps?view=azps-3.6.1)。

針對需要 Azure Active Directory PowerShell for Graph 模組中新 Cmdlet 的程序，請使用下列步驟來安裝模組，並連線至您的 Office 365 訂用帳戶。

>[!Note]
>如需支援不同版本的 Microsoft Windows 的詳細資訊，請參閱 [Azure Active Directory PowerShell for Graph 模組](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)。
>

### <a name="step-1-install-required-software"></a>步驟 1：安裝必要的軟體

These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.
  
1. 開啟提升權限的 Windows PowerShell 命令提示字元 (以系統管理員身分執行 Windows PowerShell)。
    
2. 在 [系統管理員：Windows PowerShell] 命令視窗中，執行下列命令：
    
  ```powershell
  Install-Module -Name AzureAD
  ```

如果出現提示，指出需安裝來自不受信任存放庫的模組，請輸入 **Y**，然後按 ENTER 鍵。

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>步驟 2：連接到您的 Office 365 訂閱的 Azure AD

若要使用帳戶名稱和密碼或使用多重要素驗證 (MFA) 連接到您的 Office 365 訂閱的 Azure AD，請從 Windows PowerShell 命令提示字元(不需提升權限) 執行下列其中一個命令。

|||
|:-------|:-----|
| **Office 365 雲端** | **命令** |
| Office 365 全球 (+GCC) | `Connect-AzureAD` |
| 21 Vianet 運作的 Office 365 | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| Office 365 Germany | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| Office 365 美國政府 DoD 和 Office 365 美國政府 GCC High | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

在 [登入您的帳戶]**** 對話方塊中，輸入您的 Office 365 公司或學校帳戶使用者名稱和密碼，然後按一下 [確定]****。

如果您使用 MFA，請遵循其他對話方塊中的指示，提供更多的驗證資訊，例如驗證碼。

連線之後，您可以對 [Azure Active Directory PowerShell for Graph 模組](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)使用這些 Cmdlet。
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>與適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組連線

在適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組中，命令的 Cmdlet 名稱會包含 **Msol**。

PowerShell 版本 7 和更新版本不支援適用於 Windows PowerShell 模組的 Microsoft Azure Active Directory 模組和名稱有 **Msol** 的 Cmdlet。 針對 PowerShell 版本 7 和更高版本，請務必使用 Azure Active Directory PowerShell 的圖表模組或 Azure PowerShell。

PowerShell Core 不支援適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組和名稱有 **Msol** 的 Cmdlet。 若要繼續使用這些 Cmdlet，您必須從 Windows PowerShell 執行。 
    
### <a name="step-1-install-required-software"></a>步驟 1：安裝必要的軟體

These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.
  
1.  如果您不是執行 Windows 10，請安裝64位版本的 Microsoft Online Services 登入小幫手：[適用于 IT 專業人員的 Microsoft Online services 登入](https://go.microsoft.com/fwlink/p/?LinkId=286152)小幫手幫手 rtw。
    
2. 以下列步驟安裝適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組：
    
  - 開啟提升權限的 Windows PowerShell 命令提示字元 (以系統管理員身分執行 Windows PowerShell)。
  - 執行 **Install-Module MSOnline** 命令。
  - 如果系統提示您安裝 NuGet 提供者，請輸入 **Y**，然後按 ENTER 鍵。
  - 如果系統提示您從 PSGallery 安裝模組，請輸入 **Y**，然後按 ENTER 鍵。
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>步驟 2：連接到您的 Office 365 訂閱的 Azure AD

若要使用帳戶名稱和密碼或使用多重要素驗證 (MFA) 連接到您的 Office 365 訂閱的 Azure AD，請從 Windows PowerShell 命令提示字元(不需提升權限) 執行下列其中一個命令。

|||
|:-------|:-----|
| **Office 365 雲端** | **命令** |
| Office 365 全球 (+GCC) | `Connect-MsolService` |
| 21 Vianet 運作的 Office 365 | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| Office 365 Germany | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| Office 365 美國政府 DoD 和 Office 365 美國政府 GCC High | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

在 [登入您的帳戶]**** 對話方塊中，輸入您的 Office 365 公司或學校帳戶使用者名稱和密碼，然後按一下 [確定]****。

如果您使用 MFA，請遵循其他對話方塊中的指示，提供更多的驗證資訊，例如驗證碼。

### <a name="how-do-you-know-this-worked"></a>如何知道這是否正常運作？

If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.
  
如果出現錯誤，請檢查下列需求：
  
- **密碼錯誤是常見的問題**。 再次執行步驟 2。 並密切注意您輸入的使用者名稱和密碼。
    
- **Microsoft Azure Active Directory Module for Windows PowerShell 要求在您的電腦上啟用 Microsoft .NET Framework 3.5.* x* 功能**。您的電腦可能已安裝了較新的版本 (例如 4 或 4.5.* x*)，但可以啟用或停用舊版 .NET Framework 的回溯相容性。 如需詳細資訊，請參閱下列主題：
    
  - 針對 Windows Server 2012 或 Windows Server 2012 R2，請參閱[使用新增角色及功能精靈來啟用 .NET Framework 3.5](https://go.microsoft.com/fwlink/p/?LinkId=532368)
    
  - 針對 Windows 7 或 Windows Server 2008 R2，請參閱[您無法開啟 Windows PowerShell 的 Azure Active Directory 模組](https://go.microsoft.com/fwlink/p/?LinkId=532370)

  - 若為 Windows 10、Windows 8.1 和 Windows 8，請參閱[在 Windows 10、Windows 8.1 以及 Windows 8 上安裝 .NET Framework 3.5](https://docs.microsoft.com/dotnet/framework/install/dotnet-35-windows-10)

  
- **Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:
    
  ```powershell
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    若傳回的版本號碼低於低於1.0.8070.2 的值，請卸載 Windows PowerShell 的 Microsoft Azure Active Directory 模組，並從上面的步驟1安裝。

- **如果您收到連線錯誤，請參閱本主題：** [「Connect-MsolService：擲回類型例外狀況」錯誤](https://go.microsoft.com/fwlink/p/?LinkId=532377)。
    
- **如果您收到「Get-Item：找不到路徑」錯誤，請使用以下命令：** 

```powershell
  (dir "C:\Program Files\WindowsPowerShell\Modules\MSOnline").Name
```

## <a name="see-also"></a>請參閱

- [使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
- [開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)
- [在單一 Windows PowerShell 視窗中連線至所有 Office 365 服務](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
