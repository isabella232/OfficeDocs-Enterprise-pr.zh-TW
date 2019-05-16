---
title: 修正 Office 365 目錄同步處理的問題
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: 說明 Office 365 中的目錄同步處理問題的常見原因，並提供一些方法，協助疑難排解，並加以解決。
ms.openlocfilehash: 3a1cf63122be84dc3e1c60e84a9a3a488f81bc0f
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067669"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a>修正 Office 365 目錄同步處理的問題

目錄同步處理，您可以繼續管理使用者和群組內部部署及同步處理的加入、 刪除及變更至雲端。 但安裝程式會有點複雜，而且可以有時候是很難找出問題的來源。 我們有資源可以幫助您找出潛在的問題並修正它們。
  
## <a name="how-do-i-know-if-something-is-wrong"></a>如何知道是否有問題？

在 Microsoft 365 系統管理中心的 [目錄同步狀態] 磚指出發生問題時，有問題的第一個指示：
  
![在系統管理中心預覽中並排顯示 DirSync 狀態](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
從 Office 365，指出您的租用戶發生目錄同步處理錯誤，也會收到郵件 （的備用電子郵件和您的系統管理員電子郵件）。 如需詳細資訊，請參閱[在 Office 365 中的身分識別目錄同步處理錯誤](identify-directory-synchronization-errors.md)。
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>如何取得 Azure Active Directory Connect 工具？

在[Microsoft 365 系統管理中心](https://admin.microsoft.com)中，瀏覽至 [* * 使用者 * * \> **作用中的使用者**。 按一下 [**更多**] 功能表，然後選取 [**目錄同步處理**。 
  
![在 [更多] 功能表中，選擇 [目錄同步處理](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
請遵循[精靈指示](set-up-directory-synchronization.md)下載 Azure AD Connect。 
  
如果您仍在使用 Azure Active Directory 同步處理 (DirSync)，看看[如何疑難排解 Azure Active Directory 同步處理工具安裝和設定精靈在 Office 365 中的錯誤訊息](https://go.microsoft.com/fwlink/p/?LinkId=396717)的系統需求，以安裝的相關資訊目錄同步，您需要的權限以及如何疑難排解常見錯誤。 
  
若要更新 Azure Active Directory 同步處理從 Azure AD Connect，請參閱 <<c0>的升級指示。
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a>Office 365 中的目錄同步處理問題的解決常見原因

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>**同步處理的物件未出現 online、 更新或我收到同步處理錯誤報告服務。**

- [身分識別同步處理和重複屬性恢復能力](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>**我在系統管理中心中，有警示或正在接收尚未最近使用的同步處理事件的自動化電子郵件**
- [疑難排解連線問題的 Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [Azure AD Connect 帳戶和權限](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [Azure AD Connect 同步處理： 如何管理 Azure AD 服務帳戶](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [目錄同步處理至 Azure Active Directory 停駐點或您要同步處理未登錄在一天以上警告](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>**密碼雜湊未同步處理，或我看到在系統管理中心中尚未最近使用的密碼雜湊同步處理警示**
- [使用 Azure AD Connect 同步處理實作密碼雜湊同步處理](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>**我看到超過物件配額警示**
- 我們有內建物件配額來協助保護服務。 如果您有太多的物件，您需要同步處理至 Office 365 的目錄中，您必須[連絡商務產品的支援](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)，以增加您的配額。

### <a name="i-need-to-know-which-attributes-are-synchronized"></a>**我還需要知道哪些屬性已同步處理**
- 您可以找到內部部署和雲端[右以下](https://go.microsoft.com/fwlink/p/?LinkId=396719)之間同步處理的所有屬性清單。

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a>**我無法管理或移除已同步處理至雲端的物件**
- 準備好管理只在雲端中的物件？ 或者，是否有已刪除的內部，但卡在雲端中的物件？ 看看此[同步處理期間疑難排解錯誤](https://go.microsoft.com/fwlink/p/?linkid=842044)和[支援文章](https://go.microsoft.com/fwlink/p/?LinkId=396720)指導方針如何解決這些問題。

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a>**我收到公司超出可同步處理的物件數目的錯誤訊息**
- 您可以閱讀關於此問題[以下](https://go.microsoft.com/fwlink/p/?LinkId=396721)。
   
## <a name="other-resources"></a>其他資源

- [用來修正使用者主體名稱重複問題的指令碼](https://go.microsoft.com/fwlink/p/?LinkId=396725) (英文)
    
- [如何先準備目錄同步處理非可路由網域 （例如.local 網域）](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [若要計算總計的同步處理的物件的指令碼](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [疑難排解 AD FS 2.0](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [使用 PowerShell 修正擁有郵件功能的群組的空 DisplayName 屬性](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [使用 PowerShell 修正 upn 重複的問題](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [使用 PowerShell 修正重複電子郵件地址](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a>診斷工具

[IDFix 工具](prepare-directory-attributes-for-synch-with-idfix.md)用來準備進行移轉到 Office 365 中內部部署 Active Directory 環境中執行探索和修復的身分識別物件和其屬性。 IDFix 適用於負責與 Office 365 服務目錄同步的 Active Directory 系統管理員。 

[下載 IDFix 工具](https://go.microsoft.com/fwlink/p/?LinkId=396718)從 Microsoft 下載中心找到。