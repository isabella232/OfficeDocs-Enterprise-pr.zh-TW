---
title: Office 365 開發人員/測試環境的目錄同步處理
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/04/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: e6b27e25-74ae-4b54-9421-c8e911aef543
description: 摘要： 設定目錄同步處理 Office 365 開發人員/測試環境。
ms.openlocfilehash: ebb16cb65738e0440b40d0d14550cd1f9c5bb21c
ms.sourcegitcommit: 8ff1cd7733dba438697b68f90189d4da72bbbefd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="directory-synchronization-for-your-office-365-devtest-environment"></a>Office 365 開發人員/測試環境的目錄同步處理

 **摘要：**設定 Office 365 開發人員/測試環境的目錄同步處理。
  
許多組織使用 Azure AD 連線和同步處理至 Office 365 中的帳戶一組其內部部署 Windows Server Active Directory (AD) 樹系中的帳戶的設定目錄同步處理。本文說明如何新增與密碼雜湊同步處理的目錄同步處理至 Office 365 開發人員/測試環境，則產生下列設定。
  
![Office 365 開發人員/測試環境以目錄同步作業](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
此組態組成為： 
  
- Office 365 E5 試用版訂閱，這會從建立時的 30 天到期。
- 簡化的組織內部網路連線至網際網路上的 Azure 虛擬網路 （DC1、 APP1 和 CLIENT1） 子網路的三個虛擬機器所組成。同步處理至 Office 365 的 Windows Server AD 網域在 APP1 上，執行 azure AD 連線。
    
有兩個階段來設定此開發/測試環境：
  
1. 建立 Office 365 開發人員/測試環境 （DC1、 APP1 和 CLIENT1 虛擬機器的 Office 365 E5 試用版訂閱與 Azure 虛擬網路中）。
2. 安裝及設定 Azure AD 連接在 APP1 上。
    
> [!TIP]
> 按一下[此處](http://aka.ms/catlgstack)的視覺對應至一個 Microsoft Cloud 測試實驗室指南堆疊中所有的文章。
  
## <a name="phase-1-create-an-office-365-devtest-environment"></a>階段 1： 建立 Office 365 開發人員/測試環境

階段 1、 2 及 3 的[Office 365 開發人員/test environment](office-365-dev-test-environment.md) ＞ 一文中遵循的指示。以下是所產生的設定。
  
![Office 365 開發/測試環境](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
此組態組成為： 
  
- Office 365 E5 列印試用訂閱。
- 簡化的組織內部網路連線至網際網路，DC1、 APP1 和 CLIENT1 虛擬機器上的 Azure 虛擬網路子網路所組成。
    
## <a name="phase-2-install-azure-ad-connect-on-app1"></a>在 APP1 上的階段 2： 安裝 Azure AD 連線

之後安裝及設定，Azure AD 連線會使用您的 Office 365 試用版訂閱中的帳戶的一組同步處理的公司 Windows Server AD 網域中的帳戶。下列程序步驟您透過在 APP1 上安裝 Azure AD 連線與驗證其運作。
  
### <a name="install-and-configure-azure-ad-connect-on-app1"></a>安裝及設定 Azure AD 連接在 APP1 上

1. 從[Azure 入口網站](https://portal.azure.com)連線到與公司 APP1\\User1 帳戶。
    
2. 從 APP1 開啟系統管理員層級 Windows PowerShell 命令提示字元處，並再執行下列命令：
    
  ```
  Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force

  ```

3. 從 [任務] 列中，按一下 [ **Internet Explorer** ，並移至[https://aka.ms/aadconnect](https://aka.ms/aadconnect)。
    
4. 在 [Microsoft Azure Active Directory 連線] 頁面上，按一下 [**下載**] 及 [**執行**。
    
5. 在 [**歡迎使用 Azure AD 連線**] 頁面上按一下 [**我同意**] 並再按一下 [**繼續]**。
    
6. 在 [**明確設定**] 頁面上按一下 [**使用 express 設定**]。
    
7. 在 [**連接到 Azure AD** ] 頁面全域管理員帳戶名稱在 [**使用者名稱、**類型及其中輸入密碼**密碼**，並再按 [**下一步**。
    
8. 在 [**連接至 AD DS** ] 頁面上輸入**CORP\\User1**的**使用者名稱，**其和中輸入密碼**密碼**，然後按 [**下一步**。
    
9. 在**Azure AD 登入設定**] 頁面上，按一下 [**繼續沒有任何已驗證的網域**，並再按 [**下一步**。
    
10. 在 [**準備好設定**] 頁面上按一下 [**安裝**]。
    
11. 在 [**設定完成**] 頁面上按一下 [**結束**]。
    
12. 在 Internet Explorer 中，移至 Office 365 入口網站 ([https://portal.office.com](https://portal.office.com)) 並登入您的 Office 365 試用版訂閱以全域管理員帳戶。
    
13. 從主要的入口網站] 頁面上，按一下 [**管理**]。
    
14. 在左導覽列中，按一下 [**使用者 > 作用中使用者**。
    
    記下名為**User1**的帳戶。此帳戶是來自公司 Windows Server AD 網域並且目錄同步處理已正常運作的概念。
    
15. 按一下 [ **User1**帳戶。產品授權的按一下 [**編輯**]。
    
16. 在**產品授權**，選取您的國家/地區] 和 [**關**控制項的**Office 365 企業版 E5** （將它切換到**上**）。按一下頁面底部的 [**儲存**並再按一下 [**關閉**]。
    
這是所產生的設定。
  
![Office 365 開發人員/測試環境以目錄同步作業](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
此組態組成為： 
  
- Office 365 E5 列印試用訂閱。
- 簡化的組織內部網路連線至網際網路，DC1、 APP1 和 CLIENT1 虛擬機器上的 Azure 虛擬網路子網路所組成。同步處理至 Office 365 的公司 Windows Server AD 網域每 30 分鐘在 APP1 上，執行 azure AD 連線。
    
## <a name="next-step"></a>下一個步驟

當您準備好要部署目錄同步處理您的組織時，請參閱[Microsoft Azure 中的部署 Office 365 目錄同步處理](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md)。

## <a name="see-also"></a>請參閱

[雲端採用測試實驗室指南 (Tlg)](cloud-adoption-test-lab-guides-tlgs.md)
[基本設定測試開發/環境](base-configuration-dev-test-environment.md)
[Office 365 開發人員/測試環境](office-365-dev-test-environment.md)
[Office 365 開發人員/測試環境的雲端應用程式安全性](cloud-app-security-for-your-office-365-dev-test-environment.md)
 [Office 365 開發人員/測試環境的進階威脅保護](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)




