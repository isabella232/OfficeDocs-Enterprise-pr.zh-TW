---
title: 用於 Office 365 開發/測試環境的進階威脅防護
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
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
ms.assetid: 51019757-20ac-498c-b51e-cae6d41a8c08
description: 摘要：設定並示範 Office 365 開發/測試環境中的 Office 365 進階威脅防護。
ms.openlocfilehash: 4ef057480f0ebfb2e64529f39d0db65031b75010
ms.sourcegitcommit: 201d3338d8bbc6da9389e62e2add8a17384fab4d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "31037937"
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a>用於 Office 365 開發/測試環境的進階威脅防護

 **摘要：** 設定並示範 Office 365 開發/測試環境中的 Office 365 進階威脅防護。
  
Office 365 進階威脅防護 (ATP) 是Exchange Online Protection (EOP) 的一項功能，可協助防止惡意軟體攻擊您的電子郵件。 您可以使用 ATP，建立原則來在 Exchange 系統管理中心 (EAC) 或安全性&amp;協助確保您的使用者存取只有連結或附件會被識別為不是惡意的電子郵件中的合規性中心。 如需詳細資訊，請參閱[安全附件和安全連結的進階威脅防護](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx)。
  
透過本文中的指示，您會設定並測試您 Office 365 試用版訂閱中的 ATP。
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>階段 1：建置輕量型或模擬的企業 Office 365 開發/測試環境

如果您只想以具有最小需求的輕量型方式測試 ATP，請遵循指示，以在階段 2 和 3 的[Office 365 開發/測試環境](office-365-dev-test-environment.md)中。
  
如果您想要在模擬的企業中測試 ATP，請遵循[Office 365 開發/測試環境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)中的指示。
  
> [!NOTE]
> 測試 ATP 不需要模擬的企業版開發/測試環境，其中包含連線至網際網路的模擬內部網路和目錄同步處理的 Active Directory 網域服務 (AD DS) 樹系。 它在這裡提供作為選項，讓您可以在代表典型組織的環境中測試和試驗 ATP。 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a>階段 2： 展示 Office 365 的預設電子郵件傳遞行為

在此階段中，您會示範未建立 ATP 原則時，潛在惡意電子郵件如何在沒有檢測或緩和措施的情況下傳遞至 Office 365 信箱。
  
1. 開啟 Internet Explorer 並登入您的[Office 365 開發/測試環境](office-365-dev-test-environment.md)的階段 2 中建立的 Outlook 帳戶。
    
  - 如果您使用輕量型 Office 365 開發/測試環境，請開啟 Internet Explorer 的私密工作階段，並從本機電腦登入。
    
  - 如果您使用模擬的企業 Office 365 開發/測試環境，使用[Azure 入口網站](https://portal.azure.com)連線至 CLIENT1 虛擬機器，然後從 CLIENT1 登入。
    
2. 執行「記事本」並輸入一些文字。
    
3. 將檔案儲存為 **getKeys.js** 並放置於「文件」資料夾。
    
4. 從 Internet Explorer 的 [Outlook 郵件] 索引標籤中，按一下 [新增]****。
    
5. 在 [收件者]**** 中輸入 Office 365 試用版訂閱中全域管理員名稱的電子郵件地址。
    
6. 主旨請輸入**您的新金鑰**。
    
7. 在本文中輸入**檔案在此**。
    
8. 按一下 [附加檔案]****，然後在「文件」資料夾中的 **getKeys.js** 上連按兩下，並按一下 [附加為副本]****，然後按一下 [傳送]****。
    
9. 按一下 **[新增]**。
    
10. 在 [收件者]**** 中輸入 Office 365 試用版訂閱中全域管理員名稱的電子郵件地址。
    
11. 主旨請輸入**新的旅遊網站**。
    
12. 在本文中輸入**有人轉寄此網站給我**。
    
13. 選取本文中的「**此網站**」文字，然後按一下工具列中的超連結按鈕。
    
14. 在 [ **URL**] 中，輸入**http://www.spamlink.contoso.com/**，按一下 [**確定**]，然後按一下 [**傳送**。
    
15. 開啟 Internet Explorer 的私用瀏覽模式中的個別執行個體移至 Microsoft 365 系統管理中心 ([https://admin.microsoft.com](https://admin.microsoft.com))，並登入 Office 365 試用訂閱以全域管理員帳戶。
    
16. 在主要入口網站頁面上按一下應用程式磚，然後按一下 [郵件]****。
    
17. 在收件匣中，按一下主旨為**您的新金鑰**的訊息。
    
18. 在「垃圾郵件」資料夾中，按一下主旨為**新的旅遊網站**的訊息。 按一下訊息中的「**此網站**」連結。 您應該會看到 「 Oops ！ Internet Explorer 找不到 spamlink.contoso.com。 」 頁面。 這是正確的結果，因為此位置上並沒有網頁。
    
請注意，這些潛在惡意電子郵件皆已傳遞成功。**您的新金鑰**電子郵件可能包含未偵測到的惡意軟體，且使用者可以點按**新的旅遊網站**電子郵件中的潛在惡意連結。
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a>階段 3：設定 ATP 的安全附件和安全連結原則

在此階段中，您會建立並設定安全附件原則來阻止傳遞包含惡意附件的電子郵件，以及建立和設定連結原則來防止使用者瀏覽可能不安全的 URL。
  
1. 在 Internet Explorer 的 [ **Microsoft Office 的首頁**] 索引標籤中，按一下 [**管理**] 磚。
    
2. 在左側導覽窗格中按一下 [系統管理中心]****，然後按一下 [Exchange]****。
    
3. 在 Exchange 系統管理中心的導覽窗格中，按一下 [進階威脅]****。
    
4. 按一下 [安全附件]**** 索引標籤，然後按一下加號。
    
5. 在**新的安全附件原則**] 視窗中，在 [**名稱**] 中輸入**安全附件原則-區塊**。
    
6. **安全附件的未知惡意程式碼回應**，按一下 [**封鎖**]。
    
7. 對於**偵測時重新導向附件**，按一下 [啟用重新導向]****，然後輸入您 Office 365 全域管理員帳戶的電子郵件地址。
    
8. 對於**套用至**，按一下向下箭頭，然後按一下 [收件者的網域是]****。 在視窗中，按一下您的組織名稱 （例如，contoso.onmicrosoft.com)，然後按一下 **[確定]**。
    
9. 按一下 [儲存]****。 之後更新，您應該會看到新，而且可啟用**安全附件原則-區塊**。
    
10. 按一下 [安全連結]**** 索引標籤，然後按一下加號。
    
11. 在 [新增安全連結原則]**** 視窗中，在 [名稱]**** 中輸入**安全連結原則**。
    
12. 對於**針對訊息中的未知潛在惡意 URL 選取動作**，按一下 [開啟]**** 並選取 [不允許使用者點按原始 URL]****。
    
13. 對於**套用至**，按一下向下箭頭，然後按一下 [收件者的網域是]****。 在視窗中，按一下您的組織名稱 （例如，contoso.onmicrosoft.com)，然後按一下 **[確定]**。
    
14. 按一下 [儲存]****。您應該會看到新的且已啟用的**安全連結原則**。
    
## <a name="phase-4-show-atp-in-action"></a>階段 4：顯示作用中的 ATP

在這個階段中，您可以試做 ATP 處理潛在惡意電子郵件的方式。
  
1. 從您用來傳送電子郵件在階段 2 中，在左側導覽中的 Internet Explorer 的執行個體，按一下 [**傳送項目。**
    
2. 按一下標題為**您的新金鑰**的電子郵件、 按一下向下箭號圖示，，然後按一下 [**正向**。
    
3. 在新訊息中的 [收件者]**** 中輸入 Office 365 試用版訂閱中全域管理員名稱的電子郵件地址，然後按一下 [傳送]****。
    
4. 按一下標題為**新的旅遊網站**的電子郵件，按一下向下箭號圖示，按一下 [**全部回覆**，，然後按一下 [**傳送**。
    
5. 從您用來設定階段 3 中 ATP 原則的 Internet Explorer 執行個體，按一下 Exchange 系統管理中心索引標籤，再按一下應用程式磚，然後按一下 [郵件]****。您應該會看到收件匣中有兩則新的電子郵件訊息：
    
  - 一個名為**轉寄：您的新金鑰**
    
  - 一個名為**轉寄：新的旅遊網站**
    
6. 開啟電子郵件訊息標題為**Fw： 新的旅遊網站**，按一下 [**此網站**] 連結。 您應該會看到 「 這個網站被分類為惡意。 」 頁面。 此示範 ATP 會使得您無法存取潛在的惡意的網站。
    
7. 在 Internet Explorer 的 Exchange 系統管理中心索引標籤中，按一下 [郵件流程]****。
    
8. 按一下 [訊息追蹤]**** 索引標籤，然後按一下 [搜尋]****。
    
9. 在 [郵件追蹤結果]**** 視窗中，連按兩下主旨為**您的新金鑰**的訊息。 此郵件已成功傳遞至收件匣。 關閉此視窗。
    
10. 連按兩下主旨為**新的旅行網站**的訊息。 此郵件已成功傳遞至收件匣。 關閉此視窗。
    
11. 連按兩下主旨為**轉寄：您的新金鑰**的訊息。 請注意此郵件已由 ATP 處理，再傳遞到收件匣如何。 關閉此視窗。
    
    > [!NOTE]
    > 安全附件原則的目的是為了開始掃描附件的惡意程式碼。 因為它不被判定為惡意，已允許 getKeys.js 附件。 此步驟會顯示 ATP 並未執行掃描的附件。 
  
12. 連按兩下主旨為**轉寄：新的旅遊網站**的訊息。 請注意，此郵件已成功傳遞至收件匣。
    
您現在可以使用此環境建立新的原則並試驗 ATP。
  
> [!TIP]
> 按一下[這裡](http://aka.ms/catlgstack)，可查看 One Microsoft Cloud 測試實驗室指南堆疊中文件的所有視覺對應。
  
## <a name="see-also"></a>另請參閱

[雲端採用測試實驗室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基底組態開發/測試環境](base-configuration-dev-test-environment.md)
  
[Office 365 開發/測試環境](office-365-dev-test-environment.md)
  
[Office 365 開發/測試環境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)
  
[Office 365 開發人員/測試環境的雲端 App 安全性](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md) 

[安全附件和安全連結的進階威脅防護](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


