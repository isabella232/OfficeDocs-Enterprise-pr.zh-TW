---
title: 適用於您的 Office 365 開發/測試環境的多重要素驗證
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/20/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: e2b354b9-7f18-4da0-9107-6245eae0f33f
description: 摘要： 設定使用文字訊息傳送到 Office 365 開發/測試環境中的智慧型手機的多重要素驗證。
ms.openlocfilehash: 13dc02cc23d12f6eb6e2898d34271685badd9f5a
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "30573977"
---
# <a name="multi-factor-authentication-for-your-office-365-devtest-environment"></a>適用於您的 Office 365 開發/測試環境的多重要素驗證

 **摘要：** 設定使用文字訊息傳送到 Office 365 開發/測試環境中的智慧型手機的多重要素驗證。
  
安全性登入您的 Office 365 訂閱的其他層級，您可以啟用 Azure 多重要素驗證，需要不只是使用者名稱和密碼，才能進行驗證的帳戶。 透過 Office 365 的多重要素驗證，使用者所認可電話、 輸入傳送文字郵件驗證碼或其智慧型手機上指定應用程式密碼之後正確輸入其密碼。 只有在滿足這個第二次驗證要素之後，他們才可以登入。 
  
本文說明如何啟用及測試文字郵件的驗證為特定的 Office 365 帳戶。
  
有兩個階段，以設定 Office 365 開發/測試環境中的多重要素驗證：
  
1. 建立 Office 365 開發/測試環境。
    
2. 啟用並測試 「 使用者 2 」 帳戶的多重要素驗證。
    
> [!TIP]
> 按一下[這裡](http://aka.ms/catlgstack)，可查看 One Microsoft Cloud 測試實驗室指南堆疊中文件的所有視覺對應。
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>階段 1：建置輕量型或模擬的企業 Office 365 開發/測試環境

如果您只想以具有最小需求的輕量型方式測試多重要素驗證，請遵循指示，以在階段 2 和 3 的[Office 365 開發/測試環境](office-365-dev-test-environment.md)中。
  
如果您想要在模擬的企業中測試多重要素驗證，請遵循[Office 365 開發/測試環境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)中的指示。
  
> [!NOTE]
> 測試多重要素驗證不需要模擬的企業版開發/測試環境，其中包含連線至網際網路的模擬內部網路和 Windows Server AD 樹系中的目錄同步處理。 它提供了此選項，讓您可以測試多重要素驗證與代表典型組織的環境中實驗。 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a>階段 2： 啟用並測試 「 使用者 2 」 帳戶的多重要素驗證

啟用多重要素驗證的 「 使用者 2 」 帳戶使用下列步驟：
  
1. 開啟瀏覽器的個別執行個體，請移至 Office 365 入口網站 ([https://www.office.com](https://www.office.com))，然後登入 Office 365 試用訂閱以全域管理員帳戶。
    
2. 從主要的入口網站頁面中，按一下 [管理]****。
    
3. 在左方的瀏覽區域中，按一下 [使用者] > [作用中的使用者]****。
    
4. 在 [作用中使用者] 窗格中，按一下 [**更多 > 多重要素驗證設定**]。
    
5. 在清單中，選取 「**使用者 2** 」 帳戶。
    
6. 在 [**使用者 2** ] 區段中，[**快速步驟**，按一下 [**啟用**。
    
7. 在 [**關於啟用多重要素驗證**] 對話方塊中，按一下 [**啟用多重要素驗證**]。
    
8. 在**更新成功**] 對話方塊中，按一下 [**關閉**]。
    
9. 在 [ **Microsoft Office 的首頁**] 索引標籤中，按一下右上方，使用者帳戶圖示，然後按一下 [**登出]**。
    
10. 關閉瀏覽器執行個體。
    
完成文字郵件驗證和測試這些步驟的 「 使用者 2 」 帳戶的設定：
  
1. 開啟瀏覽器的新執行個體。
    
2. 移至 Office 365 入口網站 ([https://www.office.com](https://www.office.com)) 並以 「 使用者 2 」 帳戶登入 (user2 @\<組織 name>.onmicrosoft.com) 和密碼。
    
3. 登入後，系統會提示您若要設定之帳戶的其他安全性驗證。 按一下 [**立即進行設定**。
    
4. 在**其他安全性驗證**] 頁面上：
    
  - 選取您的國家/地區或區域。
    
  - 輸入將接收文字訊息智慧型手機的電話號碼。
    
  - 在**方法**中，按一下 [**傳送我透過文字訊息的程式碼**。
    
5. 按 [下一步]****。
    
6. 從智慧型手機上接收簡訊輸入驗證碼，然後按一下 [**驗證**。
    
7. 在**步驟 3： 保留您現有的應用程式**頁面、 使用者 2 」 帳戶的顯示的應用程式密碼記錄於安全的位置，然後再按一下 [**完成**。
    
8. 如果這是第一次您登入的使用者 2 帳戶後，系統會提示您要變更密碼。 按兩次，輸入原始密碼] 和 [新密碼，然後按一下 [**更新密碼並登入**。 新的密碼記錄於安全的位置。
    
    應該會看到 Office 365 入口網站的使用者 2 在瀏覽器的 [ **Microsoft Office 的首頁**] 索引標籤上。
    
## <a name="see-also"></a>另請參閱

[雲端採用測試實驗室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基底組態開發/測試環境](base-configuration-dev-test-environment.md)
  
[Office 365 開發/測試環境](office-365-dev-test-environment.md)
  
[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)

[規劃 Office 365 部署多重要素驗證](https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

