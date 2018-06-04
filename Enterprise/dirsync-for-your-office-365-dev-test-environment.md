---
title: 適用於 Office 365 開發/測試環境的目錄同步作業
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: e6b27e25-74ae-4b54-9421-c8e911aef543
description: 摘要：設定適用於 Office 365 開發/測試環境的目錄同步作業
ms.openlocfilehash: d1c48bcf4018088b527c3f85f8923413f9ffd268
ms.sourcegitcommit: 8fcf6fd9f0c45a5445654ef811410fca3f4f5512
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2018
ms.locfileid: "19193533"
---
# <a name="directory-synchronization-for-your-office-365-devtest-environment"></a>適用於 Office 365 開發/測試環境的目錄同步作業

 **摘要：** 設定適用於 Office 365 開發/測試環境的目錄同步作業
  
許多組織使用 Azure AD Connect 和目錄同步作業，將其內部部署 Windows Server Active Directory (AD) 樹系中的帳戶集同步處理至 Office 365 中的帳戶集。本文說明如何使用密碼雜湊同步作業將目錄同步作業新增至 Office 365 開發/測試環境，進而產生下列組態。
  
![具有目錄同步作業的 Office 365 開發/測試環境](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
此組態組成為： 
  
- Office 365 E5 試用訂閱，從您建立的 30 天後到期。
- 簡化的組織內部網路與網際網路連線，由 Azure 虛擬網路的子網路上的三部虛擬機器 (DC1、APP1 及 CLIENT1) 組成。在 APP1 上執行的 Azure AD Connect 會將 Windows Server AD 網域同步處理至 Office 365。
    
設定此開發/測試環境有兩個主要階段︰
  
1. 建立 Office 365 開發/測試環境 (Azure 虛擬網路中具有 Office 365 E5 試用訂閱的 DC1、APP1 及 CLIENT1 虛擬機器)。
2. 在 APP1 上安裝及設定 Azure AD Connect。
    
> [!TIP]
> 按一下[這裡](http://aka.ms/catlgstack)，可查看 One Microsoft Cloud 測試實驗室指南堆疊中文件的所有視覺對應。
  
## <a name="phase-1-create-an-office-365-devtest-environment"></a>階段 1：建立 Office 365 開發/測試環境

遵循＜[Office 365 開發/測試環境](office-365-dev-test-environment.md)＞一文階段 1、2、3 中的指示。以下是所產生的組態。
  
![Office 365 開發/測試環境](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
此組態組成為： 
  
- Office 365 E5 試用訂閱。
- 簡化的組織內部網域與網際網路的連線，由 Azure 虛擬網路的子網路上的 DC1、APP1 及 CLIENT1 虛擬機器組成
    
## <a name="phase-2-install-azure-ad-connect-on-app1"></a>階段 2：在 APP1 上安裝及設定 Azure AD Connect

一旦安裝及設定，Azure AD Connect 就會將 CORP Windows Server AD 網域中的帳戶集與您的 Office 365 試用訂閱中的帳戶集同步處理。下列程序會逐步引導您在 APP1 上安裝 Azure AD Connect，並且驗證它可以運作。
  
### <a name="install-and-configure-azure-ad-connect-on-app1"></a>在 APP1 上安裝及設定 Azure AD Connect

1. 使用 CORP\\User1 帳戶，從 [Azure 入口網站](https://portal.azure.com)連線到 APP1。
    
2. 從 APP1 開啟系統管理員層級 Windows PowerShell 命令提示字元，然後執行下列命令：
    
  ```
  Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force

  ```

3. 從工作列按一下 [Internet Explorer]****，然後移至 [https://aka.ms/aadconnect](https://aka.ms/aadconnect)。
    
4. 在 [Microsoft Azure Active Directory Connect] 頁面上，按一下 [下載]****，然後按一下 [執行]****。
    
5. 在 [歡迎使用 Azure AD Connect]**** 頁面上，按一下 [我同意]****，然後按一下 [繼續]****。
    
6. 在 [快速設定]**** 頁面上，按一下 [使用快速設定]****。
    
7. 在 [連線到 Azure AD]**** 頁面上，在 [使用者名稱]**** 中輸入您的全域系統管理員帳戶名稱，在 [密碼]**** 中輸入其密碼，然後按 [下一步]****。
    
8. 在 [連線到 AD DS]**** 頁面上，在 [使用者名稱]**** 中輸入「**CORP\\User1**」，在 [密碼]**** 中輸入其密碼，然後按 [下一步]****。
    
9. 在 [Azure AD 登入設定]**** 頁面上，按一下 [在不具任何已驗證網域的情況下繼續執行]****，然後按 [下一步]****。
    
10. 在 [準備設定]**** 頁面上，按一下 [安裝]****。
    
11. 在 [組態完成]**** 頁面上，按一下 [結束]****。
    
12. 在 Internet Explorer 中，移至 Office 365 入口網站 ([https://portal.office.com](https://portal.office.com))，然後使用您的全域系統管理員帳戶登入 Office 365 試用訂閱。
    
13. 從主要的入口網站頁面中，按一下 [管理]****。
    
14. 在左方的瀏覽區域中，按一下 [使用者] > [作用中的使用者]****。
    
    請注意名稱為 **User1** 的帳戶。此帳戶是來自 CORP Windows Server AD 網域，且經過證明目錄同步作業可以運作。
    
15. 按一下 [User1]**** 帳戶。針對產品授權，按一下 [編輯]****。
    
16. 在 [產品授權]**** 中，選取您的國家/地區，然後針對 **Office 365 企業版 E5** 按一下 [關閉]**** 控制項 (切換至 [開啟]****)。按一下頁面底部的 [儲存]****，然後按一下 [關閉]****。
    
這是所產生的組態。
  
![具有目錄同步作業的 Office 365 開發/測試環境](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
此組態組成為： 
  
- Office 365 E5 試用訂閱。
- 簡化的組織內部網路與網際網路連線，由 Azure 虛擬網路的子網路上的 DC1、APP1 及 CLIENT1 虛擬機器組成。在 APP1 上執行的 Azure AD Connect 會每隔 30 分鐘將 CORP Windows Server AD 網域同步處理至 Office 365。
    
## <a name="next-step"></a>下一步

當您準備好要為您的組織部署目錄同步作業時，請參閱＜[在 Microsoft Azure 中部署 Office 365 目錄同步處理](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md)＞。

## <a name="see-also"></a>另請參閱

[雲端採用測試實驗室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)

[基底組態開發/測試環境](base-configuration-dev-test-environment.md)

[Office 365 開發/測試環境](office-365-dev-test-environment.md)

[Office 365 開發人員/測試環境的雲端 App 安全性](cloud-app-security-for-your-office-365-dev-test-environment.md)

[適用於 Office 365 開發/測試環境的進階威脅防護](advanced-threat-protection-for-your-office-365-dev-test-environment.md)

[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)




