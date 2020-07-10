---
title: Microsoft 365 多地理位置租用戶組態
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: Strat_SP_gtc
f1.keywords:
- NOCSH
ms.custom: ''
localization_priority: Priority
description: 了解如何設定 Microsoft 365 多地理位置。
ms.openlocfilehash: 928033dcbec0ad0b52f24bd0bec4dd6b9f9331bc
ms.sourcegitcommit: c6a2256f746f55d1cfb739649ffeee1f2f2152aa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "45052566"
---
# <a name="microsoft-365-multi-geo-tenant-configuration"></a>Microsoft 365 多地理位置租用戶組態

為您的租用戶設定 Microsoft 365 多地理位置之前，請確定您已閱讀[規劃 Microsoft 365 多地理位置](plan-for-multi-geo.md)。 若要按照本文中的步驟操作，您需要一個要啟用為衛星位置的地理位置清單，以及您要在這些位置佈建的測試使用者。

## <a name="add-the-multi-geo-capabilities-in-your-microsoft-365-plan-to-your-tenant"></a>將 Microsoft 365 方案中的多地理位置功能新增到您的租用戶

若要使用 Microsoft 365 多地理位置，您需要「Microsoft 365 中的多地理位置功能」__ 方案。 請與您的帳戶小組合作，將此方案新增到您的租用戶。 您的帳戶小組會協助您聯繫適當的授權專員，讓您完成租用戶設定。

Note that the _Multi-Geo Capabilities in Microsoft 365_ plan are a user-level service plan. You need a license for each user that you want to host in a satellite location. You can add more licenses over time as you add users in satellite locations.

在租用戶佈建「Microsoft 365 的多地理位置功能」__ 方案後，OneDrive 和 SharePoint 系統管理中心的 [地理位置]**** 索引標籤會變成可用。

## <a name="add-satellite-locations-to-your-tenant"></a>將衛星位置新增至您的租用戶

您必須為要儲存資料的每個地理位置新增衛星位置。 下表提供可用的地理位置：

[!INCLUDE [Microsoft 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

![SharePoint 系統管理中心中地理位置頁面的螢幕擷取畫面](media/sharepoint-multi-geo-admin-center.png)

新增衛星位置

1. 開啟 SharePoint 系統管理中心。

2. 瀏覽至 [地理位置]**** 索引標籤。

3. 按一下 [新增位置]****。

4. 選取您要新增的位置，然後按一下 [下一步]****。

5. 輸入您要搭配地理位置使用的網域，然後按一下 [新增]****。

6. 按一下 [關閉]****。

Provisioning may take from a few hours up to 72 hours, depending on the size of your tenant. Once provisioning of a satellite location has completed, you will receive an email confirmation. When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo location. 

> [!IMPORTANT]
> Your new satellite location will be set up with default settings. This will allow you to configure that satellite location as appropriate for your local compliance needs.

## <a name="setting-users-preferred-data-location"></a>設定使用者的慣用資料位置
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

Once you enable the needed satellite locations, you can update your user accounts to use the appropriate preferred data location. We recommend that you set a preferred data location for every user, even if that user is staying in the central location.

> [!IMPORTANT]
> 如果使用者的慣用資料位置設定為尚未設定衛星位置或中央位置的位置，當佈建 OneDrive 和 SharePoint 網站和群組信箱時，系統將預設其為中央位置。

> [!TIP]
> 建議您從測試使用者或一小群使用者開始進行驗證，再向整個組織推出多地理位置。

在 Azure Active Directory (Azure AD) 中有兩種使用者物件：雲端專用使用者和同步處理的使用者。 請依照您的使用者類型採取相應指示。

### <a name="synchronize-users-preferred-data-location-using-azure-ad-connect"></a>使用 Azure AD Connect 同步處理使用者的慣用資料位置 

如果貴公司的使用者已從內部部署的 Active Directory 系統同步處理到 Azure AD，則必須在 AD 中填入 PreferredDataLocation，並同步處理到 Azure AD。

請依照 [Azure Active Directory Connect 同步處理：設定 Microsoft 365 資源的慣用資料位置](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation)中的程序，將慣用資料位置從您的內部部署 Active Directory Domain Services (AD DS) 同步處理到 Azure AD。

建議您將設定使用者的慣用資料位置納入標準使用者建立工作流程的一部分。

> [!IMPORTANT]
> 對於未佈建 OneDrive 的新使用者，請在使用者的 PDL 與 Azure AD 同步後至少等待 24 小時，以便在使用者登入商務用 OneDrive 之前傳播變更。 (在使用者登入來佈建其商務用 OneDrive 之前設定慣用資料位置，可確保使用者的新 OneDrive 佈建在正確的位置。)

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>為雲端專用使用者設定慣用的資料位置 

如果貴公司的使用者不是從內部部署 Active Directory 系統同步處理到 Azure AD，這表示使用者是在 Microsoft 365 或 Azure AD 中建立，則必須使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組設定 PDL。

此章節的程序需要[適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0)。 如果您已安裝此模組，請確認更新到最新的版本。

1.  使用租用戶的全域系統管理員認證，[連線並登入](/powershell/connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

2.  Use the [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users. For example:

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet. For example:

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![顯示 set-msoluser 的 PowerShell 視窗螢幕擷取畫面](media/multi-geo-tenant-configuration-image3.png)

建議您將設定使用者的慣用資料位置納入標準使用者建立工作流程的一部分。

> [!IMPORTANT]
> 對於未佈建 OneDrive 的新使用者，請在使用者的 PDL 設定後至少等待 24 小時，以便在使用者登入 OneDrive 之前傳播變更。 (在使用者登入來佈建其商務用 OneDrive 之前設定慣用資料位置，可確保使用者的新 OneDrive 佈建在正確的位置。)

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a>OneDrive 佈建及 PDL 的影響

如果使用者的租用戶中已建立 OneDrive 網站，設定其 PDL 不會自動移動其現有的 OneDrive。 若要移動使用者的 OneDrive，請參閱[商務用 OneDrive 的地理位置移動](move-onedrive-between-geo-locations.md)，並遵照「在地理位置之間移動 OneDrive」中的指示。 (請注意，當您設定使用者的 PDL 後，使用者的 Exchange 信箱即會自動移動)。

如果使用者在租用戶中沒有 OneDrive 網站，OneDrive 會根據其 PDL 值進行佈建，並假設使用者的 PDL 符合公司的其中一個衛星位置。

## <a name="configuring-multi-geo-search"></a>設定多地理位置搜尋

多地理位置租用戶具有彙總搜尋功能，可讓搜尋查詢從租用戶中的任何位置傳回結果。

根據預設，從這些進入點搜尋會傳回彙總的結果，即使每個搜尋索引都位於其相關的地理位置內：

- 商務用 OneDrive

- Delve

- SharePoint 首頁

- 搜尋中心

此外，多地理位置搜尋功能可針對使用 SharePoint 搜尋 API 的自訂搜尋應用程式進行設定。

請檢閱[為商務用 OneDrive 多地理位置設定搜尋](configure-search-for-multi-geo.md)以取得相關指示，包括任何限制與差異。

## <a name="validating-the-microsoft-365-multi-geo-configuration"></a>驗證 Microsoft 365 多地理位置組態

以下是在將 Microsoft 365 多地理位置在貴公司廣泛推出之前，您可能希望在驗證計劃中包含的一些基本使用案例。 完成這些測試以及與貴公司相關的任何其他使用案例後，您可以選擇繼續新增使用者到一開始的試驗組。

**商務用 OneDrive**

從 Microsoft 365 應用程式啟動器中選取 OneDrive，並根據使用者的 PDL 確認您將自動導向到使用者的相應地理位置。 商務用 OneDrive 現在應該開始佈建到該位置。 佈建之後，請嘗試上傳和下載一些文件。

**OneDrive 行動應用程式**

使用您的測試帳號憑證登入 OneDrive 行動裝置應用程式。 確認您可以看到您的商務用 OneDrive 檔案，並可從行動裝置與檔案互動。

**OneDrive 同步處理用戶端**

Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.

**Office 應用程式**

Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word. Open the Office application and select "OneDrive – <TenantName>". Office will detect your OneDrive location and show you the files that you can open.

**共用**

Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint online users regardless of their geo location.
