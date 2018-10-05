---
title: 修正 Office 365 的目錄同步處理問題
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: 說明 Office 365 中目錄同步處理的常見問題原因，並提供許多方法來協助疑難排解和解決它們。
ms.openlocfilehash: a1ccf7aa8c6d450cdd3d658ef0bc8d9ed6d25753
ms.sourcegitcommit: 6a4611bb474c783efd361890fe6f41c26c5aeeb3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "25405126"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a>修正 Office 365 的目錄同步處理問題

使用目錄同步處理，您可以繼續以管理使用者與群組的內部和同步處理新增、 刪除及雲端的變更。但設定更複雜，有時很難識別問題的來源。我們已資源以協助您找出潛在的問題並修正它們。
  
## <a name="how-do-i-know-if-something-is-wrong"></a>如何知道某個項目是否錯誤？

在 Office 365 系統管理中心 DirSync 狀態並排顯示指出有問題時有問題的第一個指示：
  
![DirSync 狀態磚 admin center preview](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
您也會收到 （備用電子郵件部署與管理電子郵件） 郵件來自 Office 365，指出您的租用戶發生目錄同步作業錯誤。如需詳細資訊請參閱[Office 365 中的身分識別目錄同步處理錯誤](identify-directory-synchronization-errors.md)。
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>如何取得 Azure [Active Directory 連線工具？

在 Office 365 系統管理中心中，瀏覽至 [* * 使用者 * * \> **作用中使用者**。按一下 [**更多**] 功能表並選取 [**目錄同步處理**。 
  
![在 [更多] 功能表中選擇 [目錄同步處理](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
在舊的 Office 365 系統管理中心中，瀏覽至**使用者** \> **作用中使用者**，並選取 [**設定** **Active Directory 同步處理**] 旁。 
  
![按一下 [Active Directory 同步處理中選擇 [設定](media/bd95492b-d65e-4072-a6ee-e562f5f566c3.png)
  
依照[精靈中的指示](set-up-directory-synchronization.md)下載 Azure AD 連線。 
  
如果您仍會使用 Azure Active Directory 同步處理 (DirSync)，請查看[如何疑難排解 Azure Active Directory 同步作業工具安裝和設定精靈] 在 Office 365 中的錯誤訊息](https://go.microsoft.com/fwlink/p/?LinkId=396717)的安裝的系統需求的相關資訊dirsync、 您需要的權限及如何疑難排解常見的錯誤。 
  
若要從 Azure Active Directory 同步處理更新 Azure AD 連線，請參閱[的升級指示](https://go.microsoft.com/fwlink/p/?LinkId=733240)。
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a>Office 365 中目錄同步處理問題的解決常見原因

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>**同步處理的物件未出現或線上、 更新或 I 從服務取得同步處理錯誤報告。**

- [身分識別同步處理及 duplicate 屬性恢復能力](https://go.microsoft.com/fwlink/p/?LinkID=798300)

### <a name="i-have-an-alert-in-the-office-365-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>**我的 Office 365 系統管理中心中，有通知或正在接收尚未在最近的同步處理事件的自動化電子郵件**
- [疑難排解 Azure AD 連線的連線問題](https://go.microsoft.com/fwlink/p/?LinkId=820597)
- [Azure AD 連線帳戶和權限](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [Azure AD 連線同步處理： 如何管理 Azure AD 的服務帳戶](https://go.microsoft.com/fwlink/p/?LinkId=820599)
- [Azure Active Directory 停駐點或您的目錄同步作業是同步處理尚未在多個一天中註冊也警告](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-office-365-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>**密碼雜湊不同步處理，或 I 看不到 Office 365 系統管理中心尚未最近的密碼雜湊同步處理的通知**
- [實作密碼雜湊同步處理與 Azure AD 連線同步處理](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>**我正在看不到物件配額超出提醒**
- 我們具有內建物件配額可協助保護服務。如果您有您需要將資料庫同步至 Office 365 的目錄中有太多物件，您必須以增加您配額[連絡人商務產品的支援](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)。

### <a name="i-need-to-know-which-attributes-are-synchronized"></a>**我需要知道哪些屬性已同步處理**
- 您可以找到所有內部部署與雲端[右以下](https://go.microsoft.com/fwlink/p/?LinkId=396719)之間的同步處理的屬性的清單。

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a>**我無法管理或移除已同步處理至雲端的物件**
- 已準備好要在僅限雲端中管理物件或是否有已刪除的內部，但在雲端的物件？請查看此[同步處理期間疑難排解錯誤](https://go.microsoft.com/fwlink/p/?linkid=842044)和指引[支援文章](https://go.microsoft.com/fwlink/p/?LinkId=396720)如何解決這些問題。

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a>**我收到公司超出可同步處理之物件數目的錯誤訊息**
- 您可以閱讀更多關於此問題[此處](https://go.microsoft.com/fwlink/p/?LinkId=396721)。
   
## <a name="other-resources"></a>其他資源

- [指令碼以修正重複使用者主要名稱](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [如何準備目錄同步作業非路由傳送的網域 （例如.local 網域）](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [計算同步處理的物件總數的指令碼](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [疑難排解 AD FS 2.0](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [使用 PowerShell 修正擁有郵件功能的群組的空 DisplayName 屬性](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [使用 PowerShell 修正重複 UPN](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [使用 PowerShell 修正重複電子郵件地址](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a>診斷工具

[IDFix 工具](prepare-directory-attributes-for-synch-with-idfix.md)用來準備進行移轉至 Office 365 中的內部部署 Active Directory 環境中執行探索及補救 identity 物件和其屬性。IDFix 適合負責 Office 365 服務使用 DirSync 的 Active Directory 系統管理員。 

[下載 IDFix 工具](https://go.microsoft.com/fwlink/p/?LinkId=396718)從 Microsoft 下載中心。