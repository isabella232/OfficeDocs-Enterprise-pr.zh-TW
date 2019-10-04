---
title: 與文件上的 guests 共同作業
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: 了解如何在 SharePoint 和 OneDrive 文件上的 guests 與共同作業。
ms.openlocfilehash: ebb887e4fc337b4c0e94e85e0a08e87be0e74490
ms.sourcegitcommit: c16ab90d0b9902228ce4337f1c64900592936cce
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "37108223"
---
# <a name="collaborate-with-guests-on-a-document"></a>與文件上的 guests 共同作業

如果您需要在 SharePoint 或 OneDrive 中的文件上的 guests 與共同作業，您可以傳送這些共用連結至文件。 在本文中，我們會逐步設定您的組織需求的共用連結 SharePoint 和 OneDrive 所需的 Microsoft 365 組態步驟。

## <a name="azure-organizational-relationships-settings"></a>Azure 的組織關聯性設定

Microsoft 365 中共用是由控管最高層級 Azure Active Directory 中的組織關聯性設定。 如果共用的來賓已停用，或限制在 Azure AD 中，這會覆寫任何您在 Microsoft 365 中設定的共用設定。

檢查以確保未封鎖來賓與共用的組織關聯性設定。

![螢幕擷取畫面的 Azure Active Directory 組織關聯性設定頁面](media/azure-ad-organizational-relationships-settings.png)

若要設定組織關聯性設定

1. 登入 Microsoft Azure 在[https://portal.azure.com](https://portal.azure.com)。
2. 在左導覽中，按一下 [ **Azure Active Directory**]。
3. 在 [**概觀**] 窗格中，按一下 [**組織關聯性**。
4. 在**組織關聯性**] 窗格中，按一下 [**設定**]。
5. 確保**系統管理員和來賓邀請者角色中的使用者可以邀請**和**成員可以邀請**都會設**為 [是]**。
6. 如果您所做的變更，請按一下 [**儲存**]。

請注意 [**共同作業限制**] 區段中的設定。 請確定不封鎖的網域的來賓，您想要與共同作業。

## <a name="sharepoint-organization-level-sharing-settings"></a>共用設定的 SharePoint 組織層級

為了讓訪客能夠存取 SharePoint 或 OneDrive 中的文件，SharePoint 和 OneDrive 組織層級共用設定必須允許與來賓共用。

SharePoint 的組織層級設定會決定哪些設定可供個別的 SharePoint 網站。 網站設定不能更寬鬆比組織層級的設定。 OneDrive 的組織層級設定會決定在使用者的 OneDrive 文件庫中時可用的共用層級。

對於 SharePoint 和 OneDrive，如果您想要允許的檔案和資料夾與匿名使用者共用，選擇 [**任何人**。 如果您想要確定所有來賓都需要驗證，請選擇 [**新增] 和 [現有的來賓**。 *任何人*連結是最簡單的共用： 來賓可以開啟未經驗證的連結，並且可以自由地將其傳遞給其他人。

For SharePoint，選擇 [將您的組織中任何網站所需的最寬鬆] 設定。

![螢幕擷取畫面的 SharePoint 組織層級共用設定](media/sharepoint-organization-external-sharing-controls.png)


若要設定共用設定的 SharePoint 組織層級

1. 在 Microsoft 365 系統管理中心，在左側導覽中，[**系統管理中心**中，按一下 [ **SharePoint**]。
2. 在 SharePoint 系統管理中心中，在左側導覽中，按一下 [**共用**]。
3. 確定 SharePoint 或 OneDrive 外部共用設定為**任何人**或**新增和現有的來賓**。 （請注意 [OneDrive] 設定不能更寬鬆比 SharePoint 設定）。
4. 如果您所做的變更，請按一下 [**儲存**]。

## <a name="sharepoint-organization-level-default-link-settings"></a>SharePoint 組織層級預設連結設定

預設檔案和資料夾連結設定會決定哪一個連結選項向使用者顯示預設情況下使用者共用的檔案或資料夾時。 使用者可以將連結類型變更為下列其中一個其他選項共用視之前。

請記住，此設定會影響您的組織，以及 OneDrive 中的 SharePoint 網站。

選擇 [當使用者共用檔案及資料夾，依預設會選取連結的類型：

- **任何人] 連結**-如果您預期在具有匿名使用者共用檔案和資料夾的許多選擇此選項。 如果您想要允許*任何人*的連結，但擔心意外匿名共用，請考慮下列其中一個其他選項為預設值。 如果您已啟用**的任何人**共用，此連結類型只有。
- **只有在您的組織中的人員**-如果您預期大部分的檔案和資料夾共用您的組織內的人員都必須選擇此選項。
- **特定人員**-如果您預期執行許多檔案和資料夾與來賓共用，請考慮此選項。 這種類型的連結與來賓運作，以及需要進行驗證。
 
![螢幕擷取畫面的 SharePoint 組織層級檔案和資料夾共用設定](media/sharepoint-organization-files-folders-sharing-settings.png)


若要設定 SharePoint 和 OneDrive 組織層級預設值] 連結

1. 瀏覽至 SharePoint 系統管理中心的 [共用] 頁面上。
2. [**檔案] 和 [資料夾] 連結**，選取預設共用您想要使用的連結。
3. 如果您所做的變更，請按一下 [**儲存**]。

## <a name="sharepoint-site-level-sharing-settings"></a>SharePoint 網站層級共用設定

如果您要共用檔案和 fodlers SharePoint 網站中，您也需要檢查該網站的網站層級共用設定。

![螢幕擷取畫面的 SharePoint 網站外部共用設定](media/sharepoint-site-external-sharing-settings.png)

若要設定網站層級共用設定
1. 在 SharePoint 系統管理中心中，在左側導覽中，展開 [**站台**，按一下 [**作用中網站**。
2. 選取您剛建立的網站。
3. 在功能區中，按一下 [**共用**]。
4. 請確定該共用設為**任何人**或**新增和現有的來賓**。
5. 如果您所做的變更，請按一下 [**儲存**]。

## <a name="invite-users"></a>邀請使用者

來賓共用設定現在會進行設定，讓使用者可以立即與共用檔案和資料夾來賓。 如需詳細資訊，請參閱[共用 OneDrive 檔案及資料夾](https://support.office.com/article/9fcc2f7d-de0c-4cec-93b0-a82024800c07)和[共用 SharePoint 檔案或資料夾](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c)。

## <a name="see-also"></a>另請參閱