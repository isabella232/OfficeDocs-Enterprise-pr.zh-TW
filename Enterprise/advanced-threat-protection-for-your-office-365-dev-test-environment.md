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
ms.openlocfilehash: 07411600db11c8eea825c0ef5b82ea1206d20e11
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914958"
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a>用於 Office 365 開發/測試環境的進階威脅防護

 **摘要：** 設定並示範 Office 365 開發/測試環境中的 Office 365 進階威脅防護。
  
Office 365 進階威脅保護 (ATP) 是一種功能的 Exchange Online Protection (EOP) 可協助保留惡意程式碼不在您的電子郵件。您可以使用 ATP、 建立原則來在 Exchange 系統管理中心 (EAC) 或安全性&amp;規範中心有助於確保您的使用者存取僅或連結會被識別為不是惡意的電子郵件中的附件。如需詳細資訊，請參閱 ＜[進階的威脅保護安全附件及安全的連結](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx)。
  
透過本文中的指示，您會設定並測試您 Office 365 試用版訂閱中的 ATP。
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>階段 1：建置輕量型或模擬的企業 Office 365 開發/測試環境

如果您只想要測試 ATP 的基本需求的輕量型方式，請在階段 2 和 3 的[Office 365 開發人員/測試環境](office-365-dev-test-environment.md)中遵循的指示。
  
如果您想要測試 ATP 模擬 enterprise 中，請遵循[DirSync Office 365 開發人員/測試環境](dirsync-for-your-office-365-dev-test-environment.md)中的指示。
  
> [!NOTE]
> 測試 ATP 不需要模擬的企業開發/測試環境，其中包括模擬的內部網路 (連線到網際網路) 和 Windows Server AD 樹系中的目錄同步處理。它在這裡提供作為選項，讓您可以在代表典型組織的環境中測試和試驗 ATP。 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a>階段 2： 示範 Office 365 的預設電子郵件傳遞行為

在此階段中，您會示範未建立 ATP 原則時，潛在惡意電子郵件如何在沒有檢測或緩和措施的情況下傳遞至 Office 365 信箱。
  
1. 開啟 Internet Explorer 並登入您在階段 2 的[Office 365 開發人員/測試環境](office-365-dev-test-environment.md)中建立的 Outlook 帳戶。
    
  - 如果您使用輕量型 Office 365 開發/測試環境，請開啟 Internet Explorer 的私密工作階段，並從本機電腦登入。
    
  - 如果您使用模擬的企業版 Office 365 開發人員/測試環境，使用[Azure 入口網站](https://portal.azure.com)連線到 CLIENT1 虛擬機器，並從 CLIENT1 登入。
    
2. 執行「記事本」並輸入一些文字。
    
3. 將檔案儲存為 **getKeys.js** 並放置於「文件」資料夾。
    
4. 從 Internet Explorer 的 [Outlook 信箱] 索引標籤中，按一下 [**新增**]。
    
5. 在 [**至**] 輸入您的試用版訂閱 Office 365 全域管理員名稱的電子郵件地址。
    
6. 主旨請輸入**您的新金鑰**。
    
7. 在本文中輸入**檔案在此**。
    
8. 按一下 [**附加**、 連按兩下 [文件] 資料夾中的**getKeys.js** 、 按一下 [**附加複本**，和 [**傳送**。
    
9. 按一下 [ **新增**]。
    
10. 在 [**至**] 輸入您的試用版訂閱 Office 365 全域管理員名稱的電子郵件地址。
    
11. 主旨請輸入**新的旅遊網站**。
    
12. 在本文中輸入**有人轉寄此網站給我**。
    
13. 選取本文中的「**此網站**」文字，然後按一下工具列中的超連結按鈕。
    
14. 在**URL**] 中輸入**http://www.spamlink.contoso.com/**、 按一下 [**確定**] 和 [**傳送**。
    
15. 開啟 Internet Explorer 的私用的瀏覽模式中的個別執行個體移至 Office 365 入口網站 ([https://portal.office.com](https://portal.office.com))，並登入您的 Office 365 試用版訂閱以全域管理員帳戶。
    
16. 從主要的入口網站] 頁面上，按一下 [應用程式] 磚和 [**郵件**。
    
17. 在收件匣中，按一下主旨為**您的新金鑰**的訊息。
    
18. 在 [垃圾郵件] 資料夾中，按一下 [**新增旅行社網站**主旨的郵件。在郵件中按一下**此網站**連結。您應該會看到 「 Oops ！Internet Explorer 找不到 spamlink.contoso.com。 」 頁面。這會是正確的結果是因為在該位置上沒有任何網頁。
    
請注意，這些潛在惡意電子郵件皆已傳遞成功。**您的新金鑰**電子郵件可能包含未偵測到的惡意軟體，且使用者可以點按**新的旅遊網站**電子郵件中的潛在惡意連結。
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a>階段 3：設定 ATP 的安全附件和安全連結原則

在此階段中，您會建立並設定安全附件原則來阻止傳遞包含惡意附件的電子郵件，以及建立和設定連結原則來防止使用者瀏覽可能不安全的 URL。
  
1. 在 Internet Explorer 的 [ **Microsoft Office Home** ] 索引標籤中，按一下 [**系統**並排顯示。
    
2. 在左導覽列中，按一下 [**系統中心**，然後**Exchange**。
    
3. 在 [Exchange 系統管理中心] 索引標籤的左方導覽，按一下 [**進階的威脅**。
    
4. [**安全的附件**] 索引標籤和 [加號。
    
5. 在**新的安全附件原則**] 視窗的 [**名稱**] 中輸入 [**安全的附件原則-區塊**。
    
6. 針對**安全附件未知的惡意程式碼回應**] 按一下 [**封鎖**]。
    
7. **重新導向附件偵測上的**，按一下 [**啟用重新導向**，輸入您的 Office 365 全域管理員帳戶的電子郵件地址。
    
8. 針對**適**，按一下向下箭號，和 [**收件者的網域是**。在視窗中，按一下您的組織名稱 （例如 contoso.onmicrosoft.com) 及 [**確定]**。
    
9. 按一下 [**儲存**]。更新之後您應該會看見新並啟用**安全的附件原則-區塊**。
    
10. [**安全的連結**] 索引標籤和 [加號。
    
11. 在 [**新的安全連結原則**] 視窗的 [**名稱**] 中輸入**安全連結原則**。
    
12. **選取訊息中的未知可能的惡意 url 的巨集指令**，請**上**，按一下 [，然後選取 [**不允許使用者透過按一下以原始 URL**。
    
13. 針對**適**，按一下向下箭號，和 [**收件者的網域是**。在視窗中，按一下您的組織名稱 （例如 contoso.onmicrosoft.com) 及 [**確定]**。
    
14. 按一下 [**儲存**]。您應該會看見新並啟用**安全連結原則**。
    
## <a name="phase-4-show-atp-in-action"></a>階段 4：顯示作用中的 ATP

在這個階段中，您可以試做 ATP 處理潛在惡意電子郵件的方式。
  
1. 從您用來在階段 2，傳送電子郵件的左方導覽中的 Internet Explorer 的執行個體，按一下 [**傳送的項目。**
    
2. 按一下標題為**新的金鑰**的電子郵件、 按一下向下箭號圖示，和 [**正向**。
    
3. 新郵件，在 [**至**] 輸入您的試用版訂閱 Office 365 全域管理員名稱的電子郵件地址，然後按一下 [**傳送**。
    
4. 按一下 [電子郵件標題**新增旅行社網站**、 [向下箭號圖示、 按一下 [**全部回覆**，和 [**傳送**。
    
5. 您用來設定 ATP 原則在階段 3 中的 Internet Explorer 的執行個體，從 [Exchange 系統管理中心] 索引標籤、 按一下 [應用程式] 磚和 [**郵件**。您應該會看到兩個新電子郵件訊息收件匣：
    
  - 一個名為**轉寄：您的新金鑰**
    
  - 一個名為**轉寄：新的旅遊網站**
    
6. 開啟電子郵件標題**Fw： 新的旅行網站**並按一下 [**此網站**] 連結。您應該會看到 「 這個網站具有已分類為惡意。 」 頁面。此示範 ATP 防止您存取可能的惡意網站。
    
7. Exchange admin center] 索引標籤中的 Internet Explorer 中，在左導覽列中，按一下 [**郵件流程**]。
    
8. [**郵件追蹤**] 索引標籤和 [**搜尋**。
    
9. 在**郵件追蹤結果**視窗中，按兩下 [郵件主旨**新的金鑰**]。此郵件已成功傳遞至收件匣。關閉此視窗。
    
10. 按兩下 [**新增旅行社網站**之主旨的郵件。此郵件已成功傳遞至收件匣。關閉此視窗。
    
11. 按兩下 [郵件主旨**Fw： 新的金鑰**。記下此訊息已由 ATP 處理與然後傳遞至收件匣方式。關閉此視窗。
    
    > [!NOTE]
    > 安全的附件原則的目的是以開始掃描附件的惡意程式碼。無法決定要惡意已允許 getKeys.js 附件。此步驟會顯示 ATP 並未執行附件的掃描。 
  
12. 按兩下 [郵件主旨**Fw： 新的旅行網站**。請注意此郵件已成功傳遞至收件匣。
    
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


