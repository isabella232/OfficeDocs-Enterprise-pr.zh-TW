---
title: "連線至 Office 365 PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/02/2018
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
description: "摘要：使用 Office 365 PowerShell 連線到您的 Office 365 組織，以從命令列執行 Office 365 系統管理中心工作。"
ms.openlocfilehash: 2f51c68acf55239c7d47f9b617a8a72965ead79d
ms.sourcegitcommit: 7ed9108846227ca883cb5113543a165704d9bbc8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2018
---
# <a name="connect-to-office-365-powershell"></a>連線至 Office 365 PowerShell

 **摘要：**使用 Office 365 PowerShell 連線到您的 Office 365 組織，以從命令列執行 Office 365 系統管理工作。
  
Office 365 PowerShell 可讓您從命令列管理 Office 365 的設定。Office 365 PowerShell 是包含三個步驟的簡單程序，您可以在其中安裝必要的軟體、執行必要的軟體，然後連線至您的 Office 365 組織。 

請注意，這些連線指示與 [Azure ActiveDirectory (MSOnline)](https://go.microsoft.com/fwlink/p/?LinkId=528113) 主題中的指示相同。
  
> [!TIP]
> **第一次使用 PowerShell？**請參閱 LinkedIn Learning 為您提供的 [PowerShell 概觀影片](http://technet.microsoft.com/library/https://support.office.com/zh-TW/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx)。 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>開始之前有哪些須知？

- 預估完成時間：5 分鐘
    
- 您可以使用下列 Windows 版本：
    
  - Windows 10、Windows 8.1、Windows 8 或 Windows 7 Service Pack 1 (SP1) 
    
  - Windows Server 2016、Windows Server 2012 R2、Windows Server 2012 或 Windows Server 2008 R2 SP1
    
    > [!NOTE]
    >請使用 64 位元的 Windows 版本。對 Windows PowerShell 的 Microsoft Azure Active Directory 模組 32 位元版本的支援已在 2014 年 10 月終止。
    
-  您用於這些程序的 Office 365工作或學校帳戶必須是 Office 365 系統管理員角色的成員。如需詳細資訊，請參閱[關於 Office 365 系統管理員角色](https://go.microsoft.com/fwlink/p/?LinkId=532367)。

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>與適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組連線

在適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組中，命令的 Cmdlet 名稱會包含 **Msol**。
    
### <a name="step-1-install-required-software"></a>步驟 1：安裝必要的軟體

這些步驟只需您在電腦上執行一次，而不必在每次連線時執行。不過，您可能需要定期安裝較新的軟體版本。
  
1.  安裝 64 位元版本的 Microsoft Online Services 登入小幫手：[適用於 IT 專業人員的 Microsoft Online Services 登入小幫手 RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152)。
    
2. 以下列步驟安裝適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組：
    
  - 開啟管理員層級的 PowerShell 命令提示字元。
  - 執行 **Install-Module MSOnline** 命令。
  - 如果系統提示您安裝 NuGet 提供者，請輸入 **Y**，然後按 ENTER 鍵。
  - 如果系統提示您從 PSGallery 安裝模組，請輸入 **Y**，然後按 ENTER 鍵。
  - 安裝完成後，請關閉 PowerShell 命令視窗。
    
### <a name="step-2-connect-to-your-office-365-subscription"></a>步驟 2：連線至您的 Office 365 訂用帳戶
<a name="step3"> </a>

若要僅以*帳戶名稱和密碼*進行連線：
  
1. 執行 Windows PowerShell 命令提示字元。
2. 在 [Windows PowerShell]**** 命令視窗中，執行下列命令：
    
```
$UserCredential = Get-Credential
Connect-MsolService -Credential $UserCredential
```

3. 在 [Windows PowerShell 認證要求] ****對話方塊中，輸入您的 Office 365工作或學校帳戶 使用者名稱和密碼，然後按一下 [確定]****。
    
若要以*多重要素驗證 (MFA)* 進行連線：
  
1. 執行 Windows PowerShell 命令提示字元。
2. 在 [Windows PowerShell 的 Microsoft Azure Active Directory 模組]**** 命令視窗中，執行下列命令。
    
```
Connect-MsolService
```

3. 在 [Azure Active Directory PowerShell] ****對話方塊中，鍵入您的 Office 365工作或學校帳戶 使用者名稱和密碼，然後按一下 [登入]****。
    
4. 遵循 [Azure Active Directory PowerShell] 對話方塊中的指示，提供其他驗證資訊 (例如驗證碼)，然後按一下 [登入]。
    
### <a name="how-do-you-know-this-worked"></a>如何知道這是否正常運作？
<a name="step3"> </a>

如果您未收到任何錯誤，便已順利連線。若要做快速測試，您可以執行一個 Office 365 Cmdlet (例如 **Get-MsolUser** )，然後檢視結果。
  
如果出現錯誤，請檢查下列需求：
  
- **密碼錯誤是常見的問題** 。再次執行步驟 3，並密切注意您輸入的使用者名稱和密碼。
    
- **Windows PowerShell 的 Microsoft Azure Active Directory 模組 要求在您的電腦上啟用 Microsoft .NET Framework 3.5. _x_ 功能** 。您的電腦可能已安裝了較新的版本 (例如 4 或 4.5. _x_)，但可以啟用或停用舊版 .NET Framework 的回溯相容性。如需相關資訊，請參閱下列主題：
    
  - 針對 Windows Server 2012 或 Windows Server 2012 R2，請參閱[使用新增角色及功能精靈來啟用 .NET Framework 3.5](https://go.microsoft.com/fwlink/p/?LinkId=532368)
    
  - 針對 Windows 8 或 Windows 8.1，請參閱[在 Windows 8 或 8.1 上安裝 .NET Framework 3.5](https://go.microsoft.com/fwlink/p/?LinkId=532369)
    
  - 針對 Windows 7 或 Windows Server 2008 R2，請參閱[您無法開啟 Windows PowerShell 的 Azure Active Directory 模組](https://go.microsoft.com/fwlink/p/?LinkId=532370)
    
- **您的 Windows PowerShell 的 Microsoft Azure Active Directory 模組 版本可能已過期。** 若要檢查，請在 Office 365 PowerShell 或 Windows PowerShell 的 Microsoft Azure Active Directory 模組中執行下列命令：
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    如果傳回的版本號碼低於 1.0.8070.2 值，請將 Windows PowerShell 的 Microsoft Azure Active Directory 模組 解除安裝，然後從步驟 1 中的連結安裝最新版本。
    
- **如果您收到連線錯誤，請參閱本主題：** [「Connect-MsolService：擲回類型例外狀況」錯誤](https://go.microsoft.com/fwlink/p/?LinkId=532377)。
    
## <a name="connect-with-the-azure-active-directory-v2-powershell-module"></a>與 Azure Active Directory V2 PowerShell 模組連接
<a name="ConnectV2"> </a>

在 Azure Active Directory V2 PowerShell 模組中，命令的 Cmdlet 名稱會包含 "AzureAD"。

如果執行程序時需要 [Azure Active Directory V2 PowerShell 模組](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)中的新 Cmdlet，請使用下列步驟來安裝模組，並連線至您的 Office 365 訂用帳戶：

### <a name="step-1-install-required-software"></a>步驟 1：安裝必要的軟體

這些步驟只需您在電腦上執行一次，而不必在每次連線時執行。不過，您可能需要定期安裝較新的軟體版本。

  
1. 開啟提升權限的 Windows PowerShell 命令提示字元 (以系統管理員身分執行 Windows PowerShell)。
    
2. 在 [系統管理員：Windows PowerShell] 命令視窗中，執行下列命令：
    
  ```
  Install-Module -Name AzureAD 
  ```

如果出現提示，指出需安裝來自不受信任存放庫的模組，請輸入 **Y**，然後按 ENTER 鍵。


### <a name="step-2-connect-to-office-365"></a>步驟 2：連線至 Office 365

若要以*帳戶名稱和密碼*連線至您的 Office 365 訂用帳戶：
    
```
$UserCredential = Get-Credential
Connect-AzureAD -Credential $UserCredential
```

在 [Windows PowerShell 認證要求] ****對話方塊中，輸入您的 Office 365工作或學校帳戶 使用者名稱和密碼，然後按一下 [確定]****。
    
若要以*多重要素驗證 (MFA)* 連線至您的 Office 365 訂用帳戶：

```
Connect-AzureAD
```

在 [Azure Active Directory PowerShell] ****對話方塊中，鍵入您的 Office 365工作或學校帳戶 使用者名稱和密碼，然後按一下 [登入]****。
    
遵循 [Azure Active Directory PowerShell] 對話方塊中的指示，提供其他驗證資訊 (例如驗證碼)，然後按一下 [登入]。
    
連線之後，您可以對 [Azure Active Directory V2 PowerShell 模組](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)使用新的 Cmdlet。
  
## <a name="see-also"></a>另請參閱

[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)
  
[在單一 Windows PowerShell 視窗中連線至所有 Office 365 服務](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)

[Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
  
[Connect-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375)

