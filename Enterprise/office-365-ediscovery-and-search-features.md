---
title: Office 365 eDiscovery 和搜尋功能概觀
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: EDiscovery 功能，以及其他搜尋功能在 Office 365 稽核使用和透明度的概觀。
ms.openlocfilehash: e9a120f717c04d5e5570e341aa5d3d93f85f80cb
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067331"
---
# <a name="ediscovery-and-search-features"></a>電子文件探索與搜尋功能 

## <a name="ediscovery"></a>eDiscovery

「 EDiscovery 」 功能讓系統管理員、 法務人員，提供單一位置和授權的其他使用者進行完整調查 Office 365 使用者活動。 具有適當權限的安全性人員執行搜尋和就地保留的內容。 搜尋的結果是您要取得從內容搜尋中，除了 eDiscovery 案例所建立的任何套用的保留相同的結果。 EDiscovery 搜尋的結果加密的安全性，，您可以分析使用[進階電子文件探索](https://support.office.com/article/office-365-advanced-ediscovery-fd53438a-a760-45f6-9df4-861b50161ae4)匯出的資料。

## <a name="content-search"></a>內容搜尋

[內容搜尋](https://support.office.com/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a)是透過先前的 eDiscovery 搜尋工具提供改良的縮放比例的 eDiscovery 搜尋工具和效能功能。 您可以使用內容搜尋來搜尋信箱、 公用資料夾、 SharePoint Online 網站和 OneDrive for Business 位置。 內容搜尋支援大型搜尋。 您可以搜尋的信箱和網站數目沒有限制。 也有上同時執行的搜尋數目沒有限制。 執行搜尋之後，會在 [搜尋] 頁面上的 [詳細資料] 窗格中顯示的內容來源數和預估的搜尋結果數目。 您可預覽結果，或將其匯出至本機電腦。 如果您的組織有 Office 365 企業版 E5 訂閱，您可以[準備的結果](https://support.office.com/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a#prepare)以供分析使用[Office 365 進階電子文件探索](http://go.microsoft.com/fwlink/p/?LinkID=620116)的功能強大的分析功能。

## <a name="audit-log-search"></a>稽核記錄搜尋

除了追蹤其 Office 365 組織中的變更，您可以檢視稽核報告和匯出稽核記錄。 一旦啟用 Office 365 租用戶的稽核，使用者和系統管理活動記錄在事件記錄檔中且可供搜尋。 例如，您可以使用信箱稽核記錄來追蹤信箱擁有者以外的使用者信箱上執行的動作。 法務人員可以使用特定使用者活動的搜尋和篩選功能。 例如，來識別使用者檢視或下載特定文件中，如果系統管理員已執行使用者管理活動，或檢視中的變更租用戶中過去 90 天的組態。 搜尋結果包含重要資訊鑑識調查特定使用者或系統管理員所進行的活動。 使用者和登入 Office 365 管理活動的描述，請參閱[在 Office 365 中的稽核活動](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c#auditlogevents)。

從 SharePoint Online 和商務用 OneDrive 的事件會出現的 30 分鐘內顯示記錄檔中。 從 Exchange Online 的事件會出現在稽核記錄項目的 24 小時內。 從 Azure AD 登入事件可用的實例，分鐘內，從 Azure AD 其他目錄事件可用相符項目的 24 小時內。 您可以匯出稽核記錄搜尋結果中的通風孔，以便進一步分析。 最大值為 50000 單一稽核記錄搜尋的項目會匯出。 若要匯出多個項目，此限制，縮小日期範圍，或執行多個的稽核記錄搜尋。

下表詳述某些活動報告中顯示的資訊。 請參閱[在 Office 365 的詳細的內容稽核記錄，](https://support.office.com/article/detailed-properties-in-the-office-365-audit-log-ce004100-9e7f-443e-942b-9b04098fcfc3)如需每個 Office 365 工作負載所收集的屬性。

| 屬性	 | 描述 |
|----------------|----------------------------------------------------------------------------------------------------------------------|
| 日期 | 事件的日期和時間 |
| 使用者 | 執行巨集指令的使用者 |
| ClientIP | 活動已記錄時所使用的裝置 IPv4 或 IPv6 位址。 |
| CreationTime | 日期和時間以 Coordinated Universal Time (UTC) 使用者執行活動時。 |
| EventSource | 識別事件發生。 可能值是 SharePoint 及 ObjectModel。 |
| ID | 報告項目的識別碼。 識別碼可唯一識別的報告項目。 |
| 作業 | 使用者或活動，對應到此使用者活動的顯示結果中選取值的名稱。 |
| OrganizationId | 組織的 Office 365 服務發生事件的 GUID。 |
| UserAgent | 使用者的瀏覽器，提供瀏覽器的相關資訊。 |
| UserId | 執行的巨集指令 （在 [作業] 屬性中指定），造成正在記錄之記錄中的使用者。 |
| UserType | 執行此作業的使用者類型。 下列的值可指出使用者類型。 |
|  | 0 代表一般使用者。 |
|  | 2 表示您 Office 365 組織中的系統管理員。 |
|  | 3 表示 Microsoft 資料中心系統管理員或資料中心系統帳戶。 |
| 工作量 | Office 365 服務發生的活動。 此屬性的可能值包括： |
|  | Exchange Online |
|  | SharePoint Online |
|  | 商務用 OneDrive |
|  | Azure Active Directory 報告 |

如需詳細步驟，來搜尋 Office 365 稽核記錄，請參閱[Office 365 中的搜尋稽核記錄](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c)。

## <a name="search-unified-audit-log"></a>整合的稽核記錄檔中搜尋

使用稽核記錄搜尋功能來搜尋稽核記錄。 Office 365 還提供使用遠端 PowerShell 此記錄檔中搜尋的能力。 [Search-unifiedauditlog 指令程式](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-audit/Search-UnifiedAuditLog?view=exchange-ps)在 Exchange Online PowerShell 中用於搜尋事件與相關使用者作業從 Exchange Online、 SharePoint Online、 OneDrive for Business 和 Azure AD 整合的稽核記錄。 

您可以搜尋指定的日期範圍內的所有事件，或您可以篩選根據特定條件，例如特定巨集指令，執行巨集指令或目標物件之使用者的結果。 系統管理員可以使用最多三個同時執行的 Exchange Online PowerShell 工作階段來分割大型的日期範圍的搜尋設定。