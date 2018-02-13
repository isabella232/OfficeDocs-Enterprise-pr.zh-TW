---
title: "Office 365 開發人員/測試環境的雲端應用程式安全性"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: TLG, Ent_TLGs
ms.assetid: 22248f2f-b370-435e-b6ac-0ae0cae36b96
description: "摘要： 設定及示範 Office 365 開發人員/測試環境中的 Office 365 雲端應用程式安全性。"
ms.openlocfilehash: a1a7269b5ac9bff949d9f7d31775bdaa2c4d3d3a
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2018
---
# <a name="cloud-app-security-for-your-office-365-devtest-environment"></a>Office 365 開發人員/測試環境的雲端應用程式安全性

 **摘要：**設定及示範 Office 365 開發人員/測試環境中的 Office 365 雲端應用程式安全性。
  
Office 365 雲端應用程式安全性] 先前稱為 「 Office 365 進階安全性管理，可讓您建立的監控和通知您在 Office 365 訂閱中可疑的活動，讓您可以調查並採取可能的原則修復動作。如需詳細資訊，請參閱[概觀 （英文) 的雲端應用程式 Office 365 的安全性](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)。
  
使用本文中的指示，您可以啟用並測試您的 Office 365 試用版訂閱中的雲端應用程式安全性。
  
> [!TIP]
> 按一下[此處](http://aka.ms/catlgstack)的視覺對應至一個 Microsoft Cloud 測試實驗室指南堆疊中所有的文章。
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>階段 1：建置輕量型或模擬的企業 Office 365 開發/測試環境

如果您只想要測試雲端應用程式安全性的基本需求的輕量型方式，請在階段 2 和 3 的[Office 365 開發人員/測試環境](office-365-dev-test-environment.md)中遵循的指示。
  
如果您想要測試模擬企業中的雲端應用程式安全性，請遵循[DirSync Office 365 開發人員/測試環境](dirsync-for-your-office-365-dev-test-environment.md)中的指示。
  
> [!NOTE]
> 測試的雲端應用程式安全性不需要模擬的 enterprise 開發人員/測試環境中，其中包含連線至網際網路模擬內部網路和 Windows Server AD 樹系目錄同步處理。它會提供這裡是做為選項可以測試雲端應用程式安全性和代表的典型組織的環境中實驗。 
  
## <a name="phase-2-before-enabling-cloud-app-security-and-creating-a-policy"></a>階段 2： 啟用雲端應用程式安全性及之前建立的原則

在此程序，您示範才能啟用雲端應用程式安全性、 變更使用者的角色提供沒有電子郵件通知給全域系統管理員。
  
### <a name="test-the-default-notification-behavior-of-office-365"></a>測試 Office 365 的預設通知行為

1. 移至 Office 365 入口網站 ([https://portal.office.com](https://portal.office.com)) 並登入您的 Office 365 試用版訂閱以全域管理員帳戶。
    
  - 如果您使用輕量型 Office 365 開發/測試環境，請從本機電腦登入。
    
  - 如果您使用模擬的企業版 Office 365 開發人員/測試環境，使用[Azure 入口網站](https://portal.azure.com)連線到 CLIENT1 虛擬機器，並從 CLIENT1 登入。
    
2. 從主要的入口網站] 頁面上，按一下 [**管理**]。
    
3. 在左導覽列中，按一下 [**使用者 > 作用中使用者**。
    
4. 按一下 [**使用者 4**帳戶。
    
5. **使用者 4** ] 索引標籤上按一下 [**角色**] 列中的 [**編輯**]。
    
6. 在 [**編輯使用者角色**] 頁面上按一下 [**全域管理員**、**替代電子郵件地址**中，輸入**user4@contoso.com**和 [**儲存**。按一下 [**關閉**] 兩次。
    
7. 選取的應用程式啟動器圖示的左上角，選擇 [**郵件**。
    
8. 等待 30 分鐘。在通知您變更全域管理員身分的使用者 4 角色中的收件匣中有沒有電子郵件通知。
    
## <a name="phase-3-enable-cloud-app-security-and-create-a-policy"></a>階段 3： 啟用雲端應用程式安全性及建立的原則

在此程序，您可以啟用雲端應用程式安全性並建立新的原則傳送電子郵件通知給您的全域管理員帳戶的使用者帳戶角色中的變更。此程序需要：
  
- Office 365 試用版訂閱的全域管理員帳戶名稱與密碼。
    
- Office 365 試用版訂閱使用者 5 帳戶的名稱與密碼。
    
### <a name="enable-and-configure-cloud-app-security"></a>啟用及設定雲端應用程式安全性

1. 移至 Office 365 入口網站 ([https://portal.office.com](https://portal.office.com)) 並登入您的 Office 365 試用版訂閱以全域管理員帳戶。
    
2. 按一下 [**安全性&amp;規範**並排顯示。
    
3. 在左側的導覽窗格中，按一下 [**提醒 > 管理進階提醒**。
    
4. **進階提醒的管理**] 頁面上按一下 [**開啟 Office 365 雲端應用程式安全性**] 和 [**移至 Office 365 雲端應用程式安全性**。
    
5. 在 [新的**儀表板**] 索引標籤，按一下 [**控制項 > 原則**。
    
6. 在 [**原則**] 頁面上按一下 [**建立原則**] 和 [**活動原則**。
    
7. 在 [**原則名稱**輸入**系統管理的活動**。
    
8. 在**原則嚴重性**，按一下 [**高**]。
    
9. 在 [**類別**] 中，按一下 [**權限的帳戶**。
    
10. 在**建立篩選器原則**中**符合下列所有的活動**，按一下 [**系統管理的活動**。
    
11. 在**警告**中，按一下 [**傳送做為電子郵件通知**。在 [**至**] 輸入您的全域管理員帳戶的電子郵件地址。
    
12. 在頁面的底端，按一下 [**建立**]。
    
## <a name="phase-4-show-cloud-app-security-in-action"></a>階段 4： 顯示雲端應用程式安全性的巨集指令

在此程序，您將示範如何雲端應用程式安全性建立提醒及時使用者 4 讓使用者 5 密碼] 和 [使用者管理管理員傳送給全域系統管理員帳戶的電子郵件通知。
  
### <a name="demonstrate-email-notification-for-a-change-in-user-account-roles"></a>示範變更使用者帳戶角色時的電子郵件通知

1. 在右上角中按一下 [使用者] 圖示，和 [**登出**。
    
2. 移至[https://portal.office.com](https://portal.office.com)。
    
3. 在 Office 365 登入頁面中，按一下 [**使用另一個帳戶**。
    
4. 輸入使用者 4 帳戶名稱和它的密碼，然後按一下 [**登入**。
    
5. 如果需要變更使用者 4 帳戶密碼，然後再按一下 [**更新密碼，登入**。
    
6. 在 Office 365 入口網站] 頁面上，按一下 [**管理**]。
    
7. 必要時，按一下 [**取消**當系統提示您輸入來更新您的系統管理連絡人資訊。
    
8. 從主要的入口網站] 頁面上，按一下 [**管理**]。
    
9. 在左導覽列中，按一下 [**使用者 > 作用中使用者**。
    
10. 按一下 [**使用者 5**帳戶。
    
11. **使用者 5** ] 索引標籤上按一下 [**角色**] 列中的 [**編輯**]。
    
12. 在 [**編輯使用者角色**] 頁面上按一下**[自訂管理員**、 [**密碼管理員**及**使用者管理管理員**、**替代電子郵件地址**中，輸入**user5@contoso.com**和 [**儲存**。按一下 [**關閉**] 兩次。
    
13. 按一下右上角中的 [使用者] 圖示] 和 [**登出**。 
    
14. 移至[https://portal.office.com](https://portal.office.com)。
    
15. 在 [ **Office 365 登入**] 頁面上，按一下 [全域管理員帳戶名稱。
    
16. 輸入密碼，然後按一下 [**登入**。
    
17. 從主要的入口網站] 頁面上，按一下 [**管理**]。
    
18. 按一下 [**安全性&amp;規範**並排顯示。
    
19. 在左側的導覽窗格中，按一下 [**提醒 > 管理進階提醒**。
    
20. 按一下 [**管理進階提醒**] 頁面的 [**移至 Office 365 雲端應用程式安全性**]。
    
21. 在 [新的**儀表板**] 索引標籤，注意到**系統管理活動**的兩個新的提醒。
    
22. 從**Microsoft Office Home** ] 索引標籤上，按一下 [**郵件**]。等候長達 30 分鐘。 
    
    您應該會看到兩個新電子郵件訊息收件匣職稱**Microsoft Azure AD 通知服務**。一個訊息會指出使用者 5 帳戶已新增至**密碼管理員**角色與另一則訊息會指出使用者 5 帳戶已新增至**使用者系統管理員**角色 (等於中的使用者管理管理員角色Office 365 系統管理中心）。
    
您現在可以使用此環境中建立新的原則及進一步實驗 Office 365 雲端應用程式安全性。請參閱[備妥可供 Office 365 雲端應用程式安全性](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a)的其他設定的文章連結。
  
## <a name="see-also"></a>請參閱

[雲端採用測試實驗室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[Office 365 開發/測試環境](office-365-dev-test-environment.md)
  
[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)

[Office 365 中的雲端應用程式安全性概觀](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)


