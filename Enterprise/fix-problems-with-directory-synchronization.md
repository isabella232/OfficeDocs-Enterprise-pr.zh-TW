---
title: 修正 Microsoft 365 的目錄同步處理問題
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: 說明在 Office 365 中目錄同步處理問題的常見原因，並提供一些方法來協助疑難排解及解決問題。
ms.openlocfilehash: d9e390a7230499f724ebbdae592264a850dd9418
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998031"
---
# <a name="fixing-problems-with-directory-synchronization-for-microsoft-365"></a>修正 Microsoft 365 的目錄同步處理問題

透過目錄同步作業，您可以繼續管理內部部署的使用者和群組，並同步處理載入、刪除和變更雲端。 不過，安裝程式有點複雜，有時可能難以識別問題的來源。 我們有助您識別潛在問題並加以修正的資源。
  
## <a name="how-do-i-know-if-something-is-wrong"></a>如何知道問題是否正確？

當 Microsoft 365 系統管理中心中的 DirSync 狀態麻將牌指出發生問題時，第一個指出發生錯誤的第一個指示。
  
您也會收到來自 Microsoft 365 的郵件（到其他電子郵件和您的系統管理員電子郵件），表示您的租使用者遇到目錄同步處理錯誤。 如需詳細資訊，請參閱[識別 Microsoft 365 中的目錄同步處理錯誤](identify-directory-synchronization-errors.md)。
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>如何取得 Azure Active Directory Connect 工具？

在[Microsoft 365 系統管理中心](https://admin.microsoft.com)中，流覽至 [**使用者**] [作用中 \> **使用者**]。 按一下 [**更多**] 功能表（三個點）並選取 **[目錄同步**處理]。 
  
依照[嚮導中的指示](set-up-directory-synchronization.md)下載 Azure AD Connect。 
  
如果您仍在使用 Azure Active Directory （Azure AD）同步處理（DirSync），請參閱[如何疑難排解 Microsoft 365 中的 Azure Active Directory 同步作業工具安裝和設定向導錯誤訊息](https://go.microsoft.com/fwlink/p/?LinkId=396717)，以取得安裝 DirSync 的系統需求相關資訊，您需要的許可權，以及如何疑難排解常見的錯誤。 
  
若要從 Azure AD Sync 更新至 Azure AD Connect，請參閱[升級指示](https://go.microsoft.com/fwlink/p/?LinkId=733240)。
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-microsoft-365"></a>解決 Microsoft 365 中目錄同步問題的常見原因

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>**同步處理的物件不會出現或線上更新，或從服務取得同步處理錯誤報表。**

- [身分識別同步及重複屬性復原](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>**我在系統管理中心有警示，或是收到自動電子郵件，但沒有最近的同步處理事件**
- [針對 Azure AD Connect 的連線問題進行疑難排解](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [Azure AD Connect 帳戶和權限](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [Azure AD Connect 同步：如何管理 Azure AD 服務帳戶](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [Azure Active Directory 目錄同步處理停止，或者系統警告您超過一天未登錄同步處理](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>**未同步處理密碼雜湊，或在系統管理中心中看到未最近密碼雜湊同步處理的警示**
- [使用 Azure AD Connect 同步處理來實作密碼雜湊同步處理](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>**我看到超出物件配額的警示**
- 我們有內建的物件配額，可協助保護服務。 如果您的目錄中有太多物件需要同步處理至 Microsoft 365，您必須[聯繫商務產品支援](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)以增加配額。

### <a name="i-need-to-know-which-attributes-are-synchronized"></a>**我需要知道同步處理的屬性**
- 您可以在[這裡](https://go.microsoft.com/fwlink/p/?LinkId=396719)找到所有在內部部署與雲端之間同步處理之屬性的清單。

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a>**我無法管理或移除同步處理至雲端的物件**
- 您是否準備好只管理雲端中的物件？ 或是存在已在內部部署中刪除，但在雲端中已停滯的物件嗎？ 請參閱同步處理期間的此[疑難排解錯誤](https://go.microsoft.com/fwlink/p/?linkid=842044)及[支援文章](https://go.microsoft.com/fwlink/p/?LinkId=396720)，以取得如何解決這些問題的指導方針。

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a>**我收到的錯誤訊息是我的公司已超過可同步處理的物件數目**
- 您可以在[這裡](https://go.microsoft.com/fwlink/p/?LinkId=396721)閱讀更多關於此問題的資訊。
   
## <a name="other-resources"></a>其他資源

- [用來修正使用者主體名稱重複問題的指令碼](https://go.microsoft.com/fwlink/p/?LinkId=396725) (英文)
    
- [如何為目錄同步處理準備非可路由的網域（例如，局域）](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [計算同步處理的物件總數的腳本](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [疑難排解 AD FS 2。0](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [使用 PowerShell 修正具有郵件功能之群組的空 DisplayName 屬性](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [使用 PowerShell 修正重複的 UPN](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [使用 PowerShell 修正重複的電子郵件地址](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a>診斷工具

[IDFix 工具](prepare-directory-attributes-for-synch-with-idfix.md)可用於在內部部署 Active Directory 環境中執行 identity 物件及其屬性的探索和修正，以準備遷移至 Microsoft 365。 IDFix 是針對與 Microsoft 365 服務的目錄同步處理負責之 Active Directory 系統管理員所設計。 

從 Microsoft 下載中心[下載 IDFix 工具](https://go.microsoft.com/fwlink/p/?LinkId=396718)。