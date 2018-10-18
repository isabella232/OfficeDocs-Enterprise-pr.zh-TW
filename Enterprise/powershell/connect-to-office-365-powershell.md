---
title: 連線至 Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: 摘要： 連線至 Office 365 組織使用 Office 365 PowerShell 從命令列執行 admin center 工作。
ms.openlocfilehash: 2ea9c3eaa9a589bed6bf7ac575ffd241b7a72f01
ms.sourcegitcommit: 8cacedcba4627042d4bd17f1a94fddcfd87f77b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2018
ms.locfileid: "25601637"
---
# <a name="connect-to-office-365-powershell"></a>連線至 Office 365 PowerShell

 **摘要：** 連線至 Office 365 組織使用 Office 365 PowerShell 從命令列執行管理工作。
  
Office 365 PowerShell 可讓您可以從命令列管理您的 Office 365 設定。連線至 Office 365 PowerShell 是您安裝的必要的軟體，然後連線至 Office 365 組織簡單的程序。 

有兩個版本的您用來連線至 Office 365 及管理使用者帳戶、 群組及授權的 PowerShell 模組：

- Azure Active Directory PowerShell 圖表 （指令程式會包含在其名稱**AzureAD** ） 
- Microsoft Azure Active Directory Module for Windows PowerShell （指令程式會包含在其名稱**MSol** ） 

本文章的日期，Azure Active Directory PowerShell 圖模組的並非完全取代指令程式的使用者、 群組及授權管理的 Microsoft Azure Active Directory Module for Windows PowerShell 模組中的功能.在許多情況下，您需要使用兩個版本。您安全地可以安裝在同一部電腦上的兩個版本。

> [!TIP]
> **第一次使用 PowerShell？** 請參閱 LinkedIn Learning 為您提供的 [PowerShell 概觀影片](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx)。 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>開始之前有哪些須知？

- 預估完成時間：5 分鐘
    
- 您可以使用下列 Windows 版本：
    
  - Windows 10、 Windows 8.1、 Windows 8 或 Windows 7 Service Pack 1 (SP1) 
    
  - Windows Server 2019、 Windows Server 2016、 Windows Server 2012 R2、 Windows Server 2012 或 Windows Server 2008 R2 SP1
    
    > [!NOTE]
    >請使用 64 位元的 Windows 版本。對 Windows PowerShell 的 Microsoft Azure Active Directory 模組 32 位元版本的支援已在 2014 年 10 月終止。
    
-  這些程序適用於使用者的 Office 365 系統管理員角色的成員。如需詳細資訊，請參閱 ＜[關於 Office 365 系統管理員角色](https://go.microsoft.com/fwlink/p/?LinkId=532367)。


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a>使用 Azure Active Directory PowerShell 圖模組的連線

[圖表 Azure Active Directory PowerShell](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)模組中的命令會有**AzureAD**在其指令程式名稱。

如圖模組的需要在 Azure Active Directory PowerShell 中的新 cmdlet 的程序，使用下列步驟來安裝此模組，並連線至您的 Office 365 訂閱。

>[!Note]
>請參閱[Azure Active Directory PowerShell 圖模組的](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)不同版本的 Microsoft Windows 支援的相關資訊。
>

### <a name="step-1-install-required-software"></a>步驟 1：安裝必要的軟體

這些步驟只需您在電腦上執行一次，而不必在每次連線時執行。不過，您可能需要定期安裝較新的軟體版本。
  
1. 開啟提升權限的 Windows PowerShell 命令提示字元 (以系統管理員身分執行 Windows PowerShell)。
    
2. 在 [系統管理員：Windows PowerShell] 命令視窗中，執行下列命令：
    
  ```
  Install-Module -Name AzureAD
  ```

如果出現提示，指出需安裝來自不受信任存放庫的模組，請輸入 **Y**，然後按 ENTER 鍵。

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>步驟 2： 連線至 Office 365 訂閱的 Azure AD

若要連線至您的 Office 365 訂閱使用的帳戶名稱及密碼或*多重要素驗證 (MFA)* 的 Azure AD，請從 Windows PowerShell 命令提示字元 （它沒有要提高權限） 執行此命令：
    
```
Connect-AzureAD
```

在 [**登入您的帳戶**] 對話方塊中，輸入您的 Office 365 工作或學校帳戶使用者名稱和密碼，並再按一下 [**確定]**。

如果您使用 MFA，請遵循在 [其他] 對話方塊中的指示以提供更多的驗證資訊，例如驗證碼。

>[!Tip]
>若要連線至 Office 365 德國，請參閱[Connect to 使用 PowerShell 的 Azure 德國。](https://docs.microsoft.com/azure/germany/germany-get-started-connect-with-ps)
>
    
連接之後，您可以使用的新 cmdlet 的[Azure Active Directory PowerShell 圖模組的](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)。
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>與適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組連線

在適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組中，命令的 Cmdlet 名稱會包含 **Msol**。
    
### <a name="step-1-install-required-software"></a>步驟 1：安裝必要的軟體

這些步驟只需您在電腦上執行一次，而不必在每次連線時執行。不過，您可能需要定期安裝較新的軟體版本。
  
1.  安裝 64 位元版本的 Microsoft Online Services 登入小幫手：[適用於 IT 專業人員的 Microsoft Online Services 登入小幫手 RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152)。
    
2. 以下列步驟安裝適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組：
    
  - 開啟提升權限的 Windows PowerShell 命令提示字元 (以系統管理員身分執行 Windows PowerShell)。
  - 執行 **Install-Module MSOnline** 命令。
  - 如果系統提示您安裝 NuGet 提供者，請輸入 **Y**，然後按 ENTER 鍵。
  - 如果系統提示您從 PSGallery 安裝模組，請輸入 **Y**，然後按 ENTER 鍵。
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>步驟 2： 連線至 Office 365 訂閱的 Azure AD

若要連線至您的 Office 365 訂閱使用的帳戶名稱及密碼或*多重要素驗證 (MFA)* 的 Azure AD，請從 Windows PowerShell 命令提示字元 （它沒有要提高權限） 執行此命令：
    
```
Connect-MsolService
```

在 [**登入您的帳戶**] 對話方塊中，輸入您的 Office 365 工作或學校帳戶使用者名稱和密碼，並再按一下 [**確定]**。

如果您使用 MFA，請遵循在 [其他] 對話方塊中的指示以提供更多的驗證資訊，例如驗證碼。

>[!Tip]
>若要連線至 Office 365 德國，請參閱[Connect to 使用 PowerShell 的 Azure 德國。](https://docs.microsoft.com/azure/germany/germany-get-started-connect-with-ps)
>
    
### <a name="how-do-you-know-this-worked"></a>如何知道這是否正常運作？

如果您未收到任何錯誤，便已順利連線。若要做快速測試，您可以執行一個 Office 365 Cmdlet (例如 **Get-MsolUser** )，然後檢視結果。
  
如果出現錯誤，請檢查下列需求：
  
- **密碼錯誤是常見的問題** 。再次執行步驟 3，並密切注意您輸入的使用者名稱和密碼。
    
- * *Microsoft Azure Active Directory Module for Windows PowerShell 需要的 Microsoft.NET Framework 3.5。* 在您電腦 * * 啟用 x * 功能。很有可能您的電腦已安裝的較新版本 (例如 4 或 4.5。* x *），但回溯相容性與較舊版本的.NET Framework 可以啟用或停用。如需詳細資訊，請參閱下列主題：
    
  - 針對 Windows Server 2012 或 Windows Server 2012 R2，請參閱[使用新增角色及功能精靈來啟用 .NET Framework 3.5](https://go.microsoft.com/fwlink/p/?LinkId=532368)
    
  - 針對 Windows 7 或 Windows Server 2008 R2，請參閱[您無法開啟 Windows PowerShell 的 Azure Active Directory 模組](https://go.microsoft.com/fwlink/p/?LinkId=532370)

  - Windows 10、 Windows 8.1 及 Windows 8，請參閱[安裝 Windows 10、 Windows 8.1 及 Windows 8 上.NET Framework 3.5](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)

  
- **您的 Windows PowerShell 的 Microsoft Azure Active Directory 模組 版本可能已過期。** 若要檢查，請在 Office 365 PowerShell 或 Windows PowerShell 的 Microsoft Azure Active Directory 模組 中執行下列命令：
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    如果傳回的版本號碼低於 1.0.8070.2 值，請將 Windows PowerShell 的 Microsoft Azure Active Directory 模組 解除安裝，然後從步驟 1 中的連結安裝最新版本。
    
- **如果您收到連線錯誤，請參閱本主題：** [「Connect-MsolService：擲回類型例外狀況」錯誤](https://go.microsoft.com/fwlink/p/?LinkId=532377)。
    

## <a name="see-also"></a>另請參閱

- [使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
- [開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)
- [在單一 Windows PowerShell 視窗中連線至所有 Office 365 服務](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [Connect-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375)

