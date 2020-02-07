---
title: Office 365 中的系統管理存取控制
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
f1.keywords:
- NOCSH
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: 摘要： Office 365 系統管理存取控制及資料分類的概觀。
ms.openlocfilehash: f902b123b26f2c71cb6597f66fc47142e2f2b44c
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844534"
---
# <a name="administrative-access-controls-in-office-365"></a>Office 365 中的系統管理存取控制 

Microsoft 已頻繁投資系統和自動化 Office 365 的大部分作業時刻意限制存取 microsoft 的客戶內容的控制項。 人類，進而管理服務，及軟體的運作該服務。 這可讓 Microsoft，以管理 Office 365 規模和管理的客戶內容的內部威脅風險。

根據預設，Microsoft 工程師會有零常設系統管理權限和客戶內容零常設存取 Office 365 中。 Microsoft 工程師可以有限制、 稽核、 及安全的客戶內容存取權的有限的時間。 只在需要的服務作業時，並核准由 Microsoft 資深管理的成員時，才存取。 授權的客戶加密箱客戶，客戶可以提供對裝載於 Office 365 其內容的存取權核准。

Microsoft 提供使用的雲端傳遞多份表單的線上服務：

- **公用定域機組：** 包含多租用戶版本的 Office 365、 Azure 及裝載於 「 北美地區 」、 南美洲、 歐洲、 亞洲、 澳洲等其他服務。
- **國家雲中：** 包含所有統領和協力廠商運作定域機組外美國 （除了和先前所述），例如 （由 21Vianet 運作的），由中國的 Office 365 和 Office 365 Germany （21vianet 運作的 microsoft，但在德國資料受託人，Deutsche Telekom 控制及監視 Microsoft 客戶資料與存取權的系統，包含客戶資料模型下） 中。
- **政府定域機組：** 包含可用於美國政府版客戶的 Office 365 與 Azure 服務。

基於本文的詳細資訊，包括 Office 365 服務：

- [Exchange Online](https://docs.microsoft.com/Exchange/exchange-online)
- [Exchange Online Protection](https://docs.microsoft.com/Office365/SecurityCompliance/eop/exchange-online-protection-overview)
- [SharePoint Online](https://docs.microsoft.com/sharepoint/sharepoint-online)
- [商務用 OneDrive](https://docs.microsoft.com/OneDrive/onedrive)
- [商務用 Skype](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-online)
- [Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/Teams-overview)
- [Yammer](https://docs.microsoft.com/yammer/yammer-landing-page)

## <a name="office-365-access-controls"></a>Office 365 的存取控制

以存取控制項來說，Microsoft 將分類為 「 客戶資料或其他類型的資料的 Office 365 資料。

### <a name="customer-data"></a>客戶資料

客戶資料是由或提供代表客戶使用 Office 365 服務時的所有資料。 這是客戶內容直接建立或上傳的 Office 365 使用者使用，包括：

- 電子郵件
- SharePoint Online 內容
- 立即訊息
- 行事曆項目
- 文件
- Contacts
- 使用者識別資訊 (EUII) （這是唯一的使用者，或資料，是連結至個別使用者，但不包含客戶內容）。

### <a name="other-types-of-data"></a>其他類型的資料

其他的資料類型包括：

- **帳戶資料：** 包含管理資料 (由系統管理員所提供的資訊時他們註冊或購買服務)，以及付款資料 （付款儀器，例如信用卡的詳細資訊的相關資訊）。
- **家識別資訊：** 包含用來識別租用戶、 使用狀況資料，以及未連結至個別使用者或客戶內容中包含的資料。
- **系統中繼資料：** 包括含有組態設定、 系統狀態、 Microsoft IP 位址和訂用帳戶及租用戶的技術資訊的服務記錄檔。

Microsoft 已經建立存取控制機制，以確保沒有其他有未核准的存取客戶資料或存取控制資料。 存取控制資料管理其他類型的資料或在函數中的環境，包括存取客戶內容或 EUII、 Microsoft 密碼、 安全性憑證，以及其他驗證相關的資料存取。 存取控制機制也會防止未核准實體、 邏輯、 或遠端存取 Office 365 實際執行環境。

有三種類別的存取控制 Microsoft 用於操作 Office 365:

- 隔離控制措施
- 人員控制措施
- 技術控制措施

當組合時，這些控制項協助防止，並在 Office 365 中偵測惡意的動作。 除了隔離、 人員及使用 Microsoft 技術控制措施，沒有控制項的第四個類別： 所實作的客戶。

Office 365 可讓您管理資料的相同的方式受管理的內部部署環境中的資料。 註冊組織 Office 365 自動的人員會成為全域系統管理員。 全域系統管理員有權存取管理入口網站和可以中的所有功能：

- 建立或編輯使用者
- 指派系統管理員角色給其他人
- 重設使用者密碼
- 管理使用者授權
- 管理的網域
- 核准客戶加密箱要求

我們建議每個組織設定至少兩個系統管理員帳戶。 對於大型企業組織中，我們建議提供不同功能的特定的系統管理員帳戶。

如需指派系統管理員角色和權限的資訊，請參閱[指派 Office 365 中的系統管理員角色](https://support.office.com/article/Assigning-admin-roles-in-Office-365-eac4d046-1afd-4f1a-85fc-8219c79e1504)和[關於 Office 365 系統管理員角色](https://support.office.com/article/Permissions-in-Office-365-DA585EEA-F576-4F55-A1E0-87090B6AAA9D)。

## <a name="related-links"></a>相關連結

- [隔離控制措施](office-365-isolation-controls.md)
- [人員控制措施](office-365-personnel-controls.md)
- [技術控制措施](office-365-technology-controls.md)
- [監視及稽核的存取控制](office-365-monitoring-and-auditing-access-controls.md)
- [Yammer 企業存取控制](office-365-yammer-enterprise-access-controls.md)