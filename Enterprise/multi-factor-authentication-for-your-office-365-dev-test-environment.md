---
title: "Office 365 開發人員/測試環境的多重要素驗證"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: e2b354b9-7f18-4da0-9107-6245eae0f33f
description: "摘要： 設定多重要素驗證使用文字訊息傳送給 Office 365 開發人員/測試環境中的智慧型手機。"
ms.openlocfilehash: 66b0fadd097e6df940754c28cd7b95549eb3a761
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2018
---
# <a name="multi-factor-authentication-for-your-office-365-devtest-environment"></a>Office 365 開發人員/測試環境的多重要素驗證

 **摘要：**設定使用文字訊息傳送給 Office 365 開發人員/測試環境中的智慧型電話的多重要素驗證。
  
登入您的 Office 365 訂閱的安全性其他層級，您可以啟用 Azure 需要超過剛使用者名稱和密碼，確認帳戶的多重要素驗證。與 Office 365 的多重要素驗證的使用者所需確認電話、 輸入驗證碼傳送文字郵件內或智慧型電話上指定的應用程式密碼後正確地輸入其密碼。未滿足此第二個驗證因素之後才可以登入。 
  
本文說明如何啟用並測試文字郵件驗證特定的 Office 365 帳戶。
  
有兩個階段來設定 Office 365 的開發人員/測試環境中的多重要素驗證：
  
1. 建立 Office 365 開發人員/測試環境。
    
2. 啟用並測試使用者 2 帳戶的多重要素驗證。
    
> [!TIP]
> 按一下[此處](http://aka.ms/catlgstack)的視覺對應至一個 Microsoft Cloud 測試實驗室指南堆疊中所有的文章。
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>階段 1：建置輕量型或模擬的企業 Office 365 開發/測試環境

如果您只想要測試多重要素驗證的最低需求的輕量型方式，請在階段 2 和 3 的[Office 365 開發人員/測試環境](office-365-dev-test-environment.md)中遵循的指示。
  
如果您想要測試模擬企業中的多重要素驗證，請遵循[DirSync Office 365 開發人員/測試環境](dirsync-for-your-office-365-dev-test-environment.md)中的指示。
  
> [!NOTE]
> 測試多重要素驗證不需要模擬的 enterprise 開發人員/測試環境中，其中包含連線至網際網路模擬內部網路和 Windows Server AD 樹系目錄同步處理。它會提供這裡是做為選項可以測試多重要素驗證和代表的典型組織的環境中實驗。 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a>階段 2： 啟用並測試使用者 2 帳戶的多重要素驗證

啟用多重要素驗證使用者 2 帳戶進行這些步驟：
  
1. 開啟瀏覽器中的個別執行個體、 移至 Office 365 入口網站 ([https://portal.office.com](https://portal.office.com))，並再登入您的 Office 365 試用版訂閱以全域管理員帳戶。
    
2. 從主要的入口網站] 頁面上，按一下 [**管理**]。
    
3. 在左導覽列中，按一下 [**使用者 > 作用中使用者**。
    
4. 在 [作用中使用者] 窗格中，按一下 [**更多 > 安裝 Azure 多重要素驗證**。
    
5. 在清單中，按一下 [**使用者 2**帳戶]。
    
6. **使用者 2** ] 區段中的 [**快速步驟**，按一下 [**啟用**。
    
7. **如何啟用多重要素驗證**] 對話方塊中，按一下 [**啟用多重要素驗證**]。
    
8. 在**更新成功**] 對話方塊中，按一下 [**關閉**]。
    
9. 在 [ **Microsoft Office Home** ] 索引標籤上按一下 [使用者帳戶中的圖示右上方，和 [**登出**。
    
10. 關閉瀏覽器執行個體。
    
完成設定使用者 2 帳戶使用的文字訊息的驗證和測試這些步驟：
  
1. 開啟瀏覽器中的新執行個體。
    
2. 移至 Office 365 入口網站 ([https://portal.office.com](https://portal.office.com)) 和登入的使用者 2 帳戶 (user2 @\<組織名稱 >。 onmicrosoft.com) 和密碼。
    
3. 登入之後, 會提示您設定的其他安全性驗證的帳戶。按一下 [**立即設定**]。
    
4. 在 [**其他安全性驗證**] 頁面上：
    
  - 選取 [國家或地區。
    
  - 輸入要接收文字訊息智慧型手機電話號碼。
    
  - 選取 [**傳送我的文字訊息的程式碼**。
    
5. 按一下 [**連絡人自己**。
    
6. 輸入驗證碼從智慧型手機上接收的文字訊息，然後按一下**確認**。
    
7. 在**步驟 3： 保留現有的應用程式**頁面、 使用者 2 帳戶將顯示應用程式密碼記錄在安全的位置，然後再按一下 [**完成**。
    
8. 在 [登入] 頁面上，輸入使用者 2 帳戶的密碼，按一下 [**登入**。
    
9. 輸入驗證碼從智慧型手機上接收的文字訊息和 [**登入**。
    
10. 如果這是第一次您登入的使用者 2 帳戶後，系統提示您變更密碼。按兩次，輸入原始密碼] 和 [新密碼] 和 [**更新密碼，登入**。安全的位置記錄的新密碼。
    
    您應該會看到 Office 365 入口網站的使用者 2。
    
## <a name="see-also"></a>請參閱

[雲端採用測試實驗室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基底組態開發/測試環境](base-configuration-dev-test-environment.md)
  
[Office 365 開發/測試環境](office-365-dev-test-environment.md)
  
[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)

[規劃 Office 365 部署的多重要素驗證](https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

