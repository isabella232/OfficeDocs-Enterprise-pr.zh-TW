---
title: 適用於 Office 365 開發人員/測試環境的雲端 App 安全性
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/05/2018
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
ms.assetid: 22248f2f-b370-435e-b6ac-0ae0cae36b96
description: 摘要： 設定並示範 Office 365 開發/測試環境中的 Office 365 雲端 App 安全性。
ms.openlocfilehash: aa6fada78ada2f97242ffe8f60c9032d618f3b9b
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490119"
---
# <a name="cloud-app-security-for-your-office-365-devtest-environment"></a>適用於 Office 365 開發人員/測試環境的雲端 App 安全性

 **摘要：** 設定並示範 Office 365 開發/測試環境中的 Office 365 雲端 App 安全性。
  
Office 365 雲端 App 安全性，先前稱為 Office 365 進階安全性管理，可讓您建立原則來監視並通知您的 Office 365 訂閱中的可疑活動，讓您進行調查，並採取可能的補救措施巨集指令。 如需詳細資訊，請參閱 <<c0>概觀的雲端 App 安全性中 Office 365。
  
透過本文中的指示，您可以啟用並測試您 Office 365 試用版訂閱中的 Cloud App Security。
  
> [!TIP]
> 按一下[這裡](http://aka.ms/catlgstack)，可查看 Office 365 測試實驗室指南堆疊中文章的所有視覺對應。
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>階段 1：建置輕量型或模擬的企業 Office 365 開發/測試環境

如果您只想以具有最小需求的輕量型方式測試 Cloud App Security，請遵循指示，以在階段 2 和 3 的[Office 365 開發/測試環境](office-365-dev-test-environment.md)中。
  
如果您想要在模擬的企業中測試 Cloud App Security，請遵循[Office 365 開發/測試環境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)中的指示。
  
> [!NOTE]
> 測試的 Cloud App Security 不需要模擬的企業版開發/測試環境，其中包含連線至網際網路的模擬內部網路和目錄同步處理的 Active Directory 網域服務 (AD DS) 樹系。 它提供了此選項，讓您可以測試 Cloud App Security 與代表典型組織的環境中實驗。 
  
## <a name="phase-2-before-enabling-cloud-app-security-and-creating-a-policy"></a>階段 2： 啟用 Cloud App Security 和建立原則前

在此程序，您會示範，才能啟用 Cloud App Security，變更使用者角色並提供沒有電子郵件通知給全域系統管理員。
  
### <a name="test-the-default-notification-behavior-of-office-365"></a>測試 Office 365 的預設通知行為

1. 移至 Microsoft 365 系統管理中心 ([https://admin.microsoft.com](https://admin.microsoft.com)) 並登入 Office 365 試用訂閱以全域管理員帳戶。
    
  - 如果您使用輕量型 Office 365 開發/測試環境，請從本機電腦登入。
    
  - 如果您使用模擬的企業 Office 365 開發/測試環境，使用[Azure 入口網站](https://portal.azure.com)連線至 CLIENT1 虛擬機器，然後從 CLIENT1 登入。
    
2. 從主要的入口網站頁面中，按一下 [管理]****。
    
3. 在左方的瀏覽區域中，按一下 [使用者] > [作用中的使用者]****。
    
4. 	按一下 [使用者 4]**** 帳戶。
    
5. 在 [使用者 4]**** 頁面上按一下 [角色] **** 列的 [編輯]****。
    
6. 在 [編輯使用者角色]**** 頁面上按一下 [全域管理員]****，並在 [備用電子郵件地址]**** 中輸入 **user4@contoso.com**，然後按一下 [儲存]****。按兩次 [關閉]****。
    
7. 	選取左上角的應用程式啟動器圖示 ，然後選擇 [郵件]****。
    
8. 等候 30 分鐘。 請注意在通知您的全域系統管理員身分的使用者 4 的角色中變更收件匣中沒有任何電子郵件訊息。
    
## <a name="phase-3-enable-cloud-app-security-and-create-a-policy"></a>階段 3： 啟用 Cloud App Security，並建立原則

在此程序，您可以啟用 Cloud App Security，並建立新的原則，以傳送電子郵件通知給全域管理員帳戶的使用者帳戶角色變更。 此程序需要︰
  
- Office 365 試用版訂閱的全域管理員帳戶名稱與密碼。
    
- Office 365 試用版訂閱使用者 5 帳戶的名稱與密碼。
    
### <a name="enable-and-configure-cloud-app-security"></a>啟用和設定雲端 App 安全性

1. 移至 Microsoft 365 系統管理中心 ([https://admin.microsoft.com](https://admin.microsoft.com)) 並登入 Office 365 試用訂閱以全域管理員帳戶。
    
2. 按一下 [管理]**** 磚。 在 [ **Office 系統管理中心**] 索引標籤中，按一下 [**系統管理中心 > 安全性 & 合規性**。
    
3. 在左側的導覽窗格中，按一下 [**提醒 > 管理進階提醒**]。
    
4. 在 [**管理進階提醒**] 頁面上，按一下 [**開啟 Office 365 雲端 App 安全性**]，然後按一下 [**移至 Office 365 雲端 App 安全性**。
    
5. 在 [新的**儀表板**] 索引標籤，按一下 [**控制項 > 原則**。
    
6. 在 [**原則**] 頁面上，按一下 [**建立原則**]，然後按一下**活動原則**。
    
7. 在 [**原則名稱**] 中，輸入**管理活動**。
    
8. 在 [原則嚴重性]**** 中按一下 [高]****。
    
9. 在 [**類別**中，按一下 [**特殊權限的帳戶**]。
    
10. 在 [**建立篩選器原則**中**符合下列所有的活動**，按一下 [**系統管理活動**。
    
11. 在 [警示]**** 中按一下 [透過電子郵件傳送警示]****。在 [收件者]**** 中輸入全域管理員帳戶的電子郵件地址。
    
12. 在頁面底部按一下 [建立]****。
    
## <a name="phase-4-show-cloud-app-security-in-action"></a>階段 4： 顯示雲端 App 安全性中巨集指令

在此程序，您會示範如何雲端 App 安全性建立提醒，並傳送電子郵件通知給全域系統管理員帳戶，當使用者 4 為使用者 5 的密碼] 和 [使用者管理系統管理員。
  
### <a name="demonstrate-email-notification-for-a-change-in-user-account-roles"></a>示範變更使用者帳戶角色時的電子郵件通知

1. 按一下右上角的使用者圖示，然後按一下 [登出]****。
    
2. 請移至 [https://www.office.com](https://www.office.com)。
    
3. 在 Office 365 登入頁面上按一下 [使用其他帳戶]****。
    
4. 輸入使用者 4 的帳戶名稱與密碼，然後按一下 [登入]****。
    
5. 如有需要，變更使用者 4 的帳戶密碼，然後按一下 [更新密碼並登入]****。
    
6. 從 Office 365 入口網站頁面，按一下 [管理]****。
    
7. 如有需要，當系統提示您更新管理員連絡資訊時，請按一下 [取消]****。
    
8. 從主要的入口網站頁面中，按一下 [管理]****。
    
9. 在左方的瀏覽區域中，按一下 [使用者] > [作用中的使用者]****。
    
10. 按一下 [使用者 5]**** 帳戶。
    
11. 在 [使用者 5]**** 頁面上按一下 [角色] **** 列的 [編輯]****。
    
12. 在 [編輯使用者角色]**** 頁面上按一下 [自訂的系統管理員]****，再按一下 [密碼管理員]**** 和 [使用者管理管理員]****，在 [備用電子郵件地址]**** 中輸入 **user5@contoso.com**，然後按一下 [儲存]****。按兩次 [關閉]****。
    
13. 按一下右上角的使用者圖示，然後按一下 [登出]****。 
    
14. 請移至 [https://www.office.com](https://www.office.com)。
    
15. 在 [Office 365 登入]**** 頁面上按一下您的全域系統管理員帳戶名稱。
    
16. 輸入密碼，然後按一下 [登入]****。
    
17. 從 Office 365 入口網站] 頁面上，按一下 [**系統**]。
    
18. 按一下 [**安全性&amp;規範**並排顯示。
    
19. 在左側的導覽窗格中，按一下 [**提醒 > 管理進階提醒**]。
    
20. 在 [**管理進階提醒**] 頁面上，按一下 [**移至 Office 365 雲端 App 安全性**。
    
21. 在 [新的**儀表板**] 索引標籤，請注意**管理**活動的兩個新的警示。
    
22. 從**Microsoft Office 的首頁**] 索引標籤上，按一下 [**郵件**]。 等待 30 分鐘。 
    
    您應該會看到兩個新電子郵件訊息中使用**Microsoft Azure AD 通知服務**的標題收件匣。 一個訊息指出使用者 5 帳戶已新增至**密碼系統管理員**角色，而另一則訊息會指出使用者 5 帳戶已新增至**使用者系統管理員**角色 (等於中的使用者管理系統管理員角色Office 365 系統管理中心）。
    
您現在可以使用此環境建立新的原則並進一步試驗 Office 365 雲端 App 安全性。 請參閱[準備好 Office 365 雲端 App 安全性](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a)的其他設定的文章連結。
  
## <a name="see-also"></a>另請參閱

[雲端採用測試實驗室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[Office 365 開發/測試環境](office-365-dev-test-environment.md)
  
[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)

[在 Office 365 雲端 App 安全性概觀](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)


