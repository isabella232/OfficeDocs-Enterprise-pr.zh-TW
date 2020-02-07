---
title: 在 Microsoft 365 中限制共用
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: SPO_Content
ms.custom: ''
localization_priority: Priority
description: 了解如何在 Microsoft 365 中限制共用。
ms.openlocfilehash: dd2705aefd4f91c4ce8773019f94acf53afea6c8
ms.sourcegitcommit: 4f465f690c6563cfa9f6029d3e7e9e3cace96671
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "41658747"
---
# <a name="limit-sharing-in-microsoft-365"></a>在 Microsoft 365 中限制共用

雖然您無法完全將內部共用停用，或移除網站的 [共用] 按鈕，但您可以透過多種方式在 Microsoft 365 中限制共用，以符合貴組織的需求。

下表列出共用檔案的方法。 如需詳細資訊，請按一下 **[共用方法]** 欄中的連結。

|共用方法|描述|限制選項|
|:-------------|:----------|:-------------|
|[Office 365 群組或團隊](#office-365-group-or-team)|獲授與 Microsoft Teams 團隊或 Office 365 群組存取權的人員對於相關聯 SharePoint 網站中的檔案具有編輯存取權。|如果群組或團隊是私人的，加入團隊的共用邀請會送往擁有者以進行核准。 系統管理員可以停用來賓存取，以防止組織外部的人員存取。|
|[SharePoint 網站](#sharepoint-site)|人員可以獲授與擁有 SharePoint 網站的擁有者、成員或來賓存取，並將擁有網站中檔案的該層級存取權。|您可以限制網站權限，以便只有網站擁有者可以共用網站。|
|[與特定人員共用](#sharing-with-specific-people)|網站成員與擁有編輯權限的人員可以提供檔案和資料夾的直接權限，或使用 *[特定人員]* 連結來共用檔案和資料夾。|您可以限制網站權限，以便只有網站擁有者可以共用檔案和資料夾。 在此情況下，由網站成員共用的直接存取和 *[特定人員]* 連結會送往網站擁有者以進行核准。|
|[SharePoint 來賓共用](#sharepoint-guest-sharing)|SharePoint 網站擁有者和成員可以與組織外部人員共用檔案和資料夾。|您可以為整個組織或個別網站停用來賓共用。|
|[[貴組織中的人員]** 共用連結](#people-in-your-organization-sharing-links)|SharePoint 網站擁有者和成員可以使用 *[貴組織中的人員]* 連結來共用檔案，此功能適用於組織內部的任何人。|可在網站層級停用 *[貴組織中的人員]* 連結。|
|[電子郵件](#email)|具有檔案存取權的人員可以透過電子郵件將檔案傳送給其他人。|系統管理員可以使用敏感度標籤來加密檔案，以防止將檔案與未經授權的人員共用。|
|[下載或檔案複製](#download-or-file-copy)|具有檔案存取權的人員可以下載或複製檔案，並與 Microsoft 365 以外的其他人共用檔案。|系統管理員可以使用敏感度標籤來加密檔案，以防止將檔案與未經授權的人員共用。|

雖然您可以使用本文所述的系統管理控制項來限制貴組織中的共用，我們高度建議您考慮使用 Microsoft 365 中提供的安全性與合規性功能，以建立安全的共用環境。 如需詳細資訊，請參閱[在 SharePoint 中使用 Microsoft 365 進行檔案共同作業](https://docs.microsoft.com/sharepoint/deploy-file-collaboration)和[適用於高度管制資料的 Teams](https://docs.microsoft.com/microsoft-365/enterprise/secure-teams-highly-regulated-data-scenario)。

若要了解貴組織使用共用功能的方式，請[執行有關檔案和資料夾共用的報告](https://docs.microsoft.com/sharepoint/sharing-reports)。

## <a name="office-365-group-or-team"></a>Office 365 群組或團隊

如果想要限制 Office 365 群組或 Microsoft Teams 團隊中的共用，請務必將群組或團隊設為私人。 貴組織內部的人員可以隨時加入公開群組或團隊。 除非群組或團隊是私人的，否則無法限制在組織內共用團隊或其檔案。

### <a name="guest-sharing"></a>來賓共用

如果想要在 Teams 中防止來賓存取，您可以在 Teams 系統管理中心中關閉來賓共用。

關閉 Teams 的來賓共用
1. 在 Teams 系統管理中心中，展開 **[全組織設定]**，然後按一下 **[來賓存取]**。
2. 關閉 **[在 Teams 中允許來賓存取]**。
3. 按一下 **[儲存]**。

如果想要在 Office 365 群組中防止來賓存取，您可以在 Microsoft 365 系統管理中心中關閉群組來賓存取設定。

關閉 Office 365 群組中的來賓共用
1. 在 Microsoft 365 系統管理中心中，按一下 **[設定]**，然後按一下 **[設定]**。
2. 在 **[服務]** 索引標籤上，按一下 **[Office 365 群組]**。
3. 清除 **[讓貴組織外部的群組成員存取群組內容]** 和 **[讓群組擁有者將貴組織外部的人員新增到群組]** 核取方塊。
4. 按一下 **[儲存變更]**。

    ![Microsoft 365 系統管理中心中 Office 365 群組共用設定的螢幕擷取畫面](media/office-365-groups-guest-settings-off.png)

> [!NOTE]
> 如果想要防止特定群組或團隊的來賓共用，您可以使用 Microsoft PowerShell 來執行此動作。 如需詳細資料，請參閱[允許或封鎖來自特定群組的來賓使用者](https://docs.microsoft.com/office365/admin/create-groups/manage-guest-access-in-groups?view=o365-worldwide#block-guest-users-from-a-specific-group)。

在 Azure Active Directory 中允許或封鎖網域，即可限制對來自特定網域的使用者進行來賓共用。 如果您已啟用 [SharePoint 和 OneDrive 與 Azure AD B2B 整合](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview)，則這也會影響 SharePoint 中的來賓共用。

僅允許從指定網域共用邀請
1. 在 Azure Active Directory 的 [概觀] 頁面上，按一下 **[組織關聯]**。
2. 按一下 **[設定]**。
3. 在 **[共同作業限制]** 底下，選取 **[拒絕指定網域的邀請]** 或 **[僅對指定的網域允許邀請]**，然後輸入您要使用的網域。
4. 按一下 **[儲存]**。

    ![Azure Active Directory 中共同作業限制設定的螢幕擷取畫面](media/azure-ad-allow-only-specified-domains.png)

## <a name="sharepoint-site"></a>SharePoint 網站

您可以將 SharePoint 網站共用限制於僅限網站擁有者。 這麼做會防止網站成員共用網站。 請記住，如果網站連接至 Office 365 群組，群組成員可以邀請其他人加入群組，而這些使用者將擁有網站存取權。

限制擁有者的網站共用
1. 在網站中，按一下齒輪圖示，然後按一下 **[網站權限]**。
2. 按一下 **[共用設定]** 下的 **[變更共用設定]**。
3. 選取 **[網站擁有者和成員，以及擁有編輯權限的人員可以共用檔案與資料夾，但只有網站擁有者可以共用網站]**。
4. 按一下 **[儲存]**。

    ![SharePoint 網站中共用權限設定的螢幕擷取畫面](media/sharepoint-site-sharing-permissions-level-two.png)

您可以關閉存取要求，以防止不是網站成員的使用者要求存取權。

關閉存取要求
1. 在網站中，按一下齒輪圖示，然後按一下 **[網站權限]**。
2. 按一下 **[共用設定]** 下的 **[變更共用設定]**。
3. 關閉 **[允許存取要求]**，然後按一下 **[儲存]**。

您可以允許或封鎖網站的網域，以限制對特定網域的網站共用。

依網域限制網站共用
1. 在 SharePoint 系統管理中心的 **[網站]** 底下，按一下 **[使用中網站]**。
2. 按一下您要設定的網站。
3. 在 **[原則]** 索引標籤的 **[外部共用]** 底下，按一下 **[編輯]**。
4. 在 **[外部共用的進階設定]** 底下，選取 **[依網域限制共用]**。
5. 新增您想要允許或封鎖的網域，然後按一下 **[儲存]**。
6. 按一下 **[儲存]**。

    ![允許的網域網站層級設定的螢幕擷取畫面](media/limit-site-sharing-by-domain.png)

## <a name="sharing-with-specific-people"></a>與特定人員共用

如果想要限制網站或其內容的共用，可以將網站設定為僅允許網站擁有者共用檔案、資料夾和網站。 設定此設定之後，網站成員若嘗試使用 *[特定人員]* 連結共用檔案或資料夾，即會送往網站擁有者以進行核准。

將網站、檔案和資料夾共用限制在擁有者
1. 在網站中，按一下齒輪圖示，然後按一下 **[網站權限]**。
2. 按一下 **[共用設定]** 下的 **[變更共用設定]**。
3. 選取 **[只有網站擁有者可以共用檔案、資料夾和網站]**。
4. 按一下 **[儲存]**。

    ![SharePoint 網站中共用權限設定的螢幕擷取畫面](media/sharepoint-site-only-site-owners-can-share.png)

## <a name="sharepoint-guest-sharing"></a>SharePoint 來賓共用

如果想要防止與組織外部人員共用 SharePoint 或 OneDrive 檔案和資料夾，您可以關閉整個組織或個別網站的來賓共用。

關閉組織的 SharePoint 來賓共用
1. 在 SharePoint 系統管理中心的 **[原則]** 底下，按一下 **[共用]**。
2. 在 **[外部共用]** 底下，將 SharePoint 滑桿向下拖曳到 **[只有貴組織中的人員]**。
3. 按一下 **[儲存]**。

    ![SharePoint 組織層級共用設定的螢幕擷取畫面](media/sharepoint-tenant-sharing-off.png)


關閉網站的來賓共用
1. 在 SharePoint 系統管理中心的 **[網站]** 底下，按一下 **[使用中網站]**。
2. 按一下您要設定的網站。
3. 在 **[原則]** 索引標籤的 **[外部共用]** 底下，按一下 **[編輯]**。
4. 在 **[外部共用]** 底下，選擇 **[只有貴組織中的人員]**，然後按一下 **[儲存]**。

    ![SharePoint 網站層級共用設定的螢幕擷取畫面](media/sharepoint-site-external-sharing-settings-off.png)

如果想要與組織外部人員共用，但想要確保每個人都能驗證，您可以停用整個組織或個別網站的 *[任何人]* (匿名共用) 連結。

關閉組織層級的 *[任何人]* 連結
1. 在 SharePoint 系統管理中心的 **[原則]** 底下，按一下 **[共用]**。
2. 在 **[外部共用]** 底下，將 SharePoint 滑桿向下拖曳至 **[新的及現有的來賓]**。
3. 按一下 **[儲存]**。

    ![SharePoint 網站層級共用設定的螢幕擷取畫面](media/sharepoint-guest-sharing-new-and-existing-guests.png)

關閉網站的 *[任何人]* 連結
1. 在 SharePoint 系統管理中心的 **[網站]** 底下，按一下 **[使用中網站]**。
2. 按一下您要設定的網站。
3. 在 **[原則]** 索引標籤的 **[外部共用]** 底下，按一下 **[編輯]**。
4. 在 **[外部共用]** 底下，選擇 **[新的及現有的來賓]**，然後按一下 **[儲存]**。

    ![SharePoint 網站層級共用設定的螢幕擷取畫面](media/sharepoint-site-external-sharing-settings-new-and-existing-guests.png)

## <a name="people-in-your-organization-sharing-links"></a>*[貴組織中的人員]* 共用連結

根據預設，網站的成員可以使用 *[貴組織中的人員]* 連結來與組織中的其他人員共用檔案和資料夾。 您可以使用 PowerShell 停用 *[貴組織中的人員]* 連結：

`Set-SPOSite -Identity <site> -DisableCompanyWideSharingLinks`

例如：

`Set-SPOSite -Identity https://contoso.sharepoint.com -DisableCompanyWideSharingLinks`

## <a name="email"></a>電子郵件

您可以使用加密來防止非必要地共用電子郵件。 這麼做會防止將電子郵件轉寄或以其他方式與未經授權的使用者共用。 您可以使用敏感度標籤來啟用電子郵件加密。 如需詳細資料，請參閱[使用敏感度標籤中的加密來限制內容的存取](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels)。

## <a name="download-or-file-copy"></a>下載或檔案複製

擁有 Microsoft 365 中檔案和資料夾存取權的使用者可以下載檔案，並將檔案複製到外部媒體。 若要降低非必要檔案共用的風險，您可以使用敏感度標籤來加密內容。

## <a name="see-also"></a>另請參閱

[Microsoft 365 來賓共用設定參考](microsoft-365-guest-settings.md)