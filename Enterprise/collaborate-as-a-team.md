---
title: 在小組中與來賓共同作業
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: 了解如何在小組中的來賓與共同作業。
ms.openlocfilehash: a3e34431b97e8f565d61470ddd55797981b837c8
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "38029167"
---
# <a name="collaborate-with-guests-in-a-team"></a>在小組中與來賓共同作業

如果您需要整個文件、 工作和交談來賓與共同作業，我們建議使用 Microsoft Teams。 Teams 提供所有的 Office 和 SharePoint 與常設聊天室中可用的共同作業功能和一組可自訂且可擴充的統一的使用者經驗中的共同作業工具。

在本文中，我們會逐步設定來賓與共同作業小組所需的 Microsoft 365 組態步驟。

## <a name="video-demonstration"></a>影片示範

這段影片顯示本文所述的設定步驟。</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE44NTr?autoplay=false]

## <a name="azure-organizational-relationships-settings"></a>Azure 的組織關聯性設定

Microsoft 365 中共用是由控管最高層級 Azure Active Directory 中的組織關聯性設定。 如果共用的來賓已停用，或限制在 Azure AD 中，這會覆寫任何您在 Microsoft 365 中設定的共用設定。

檢查以確保未封鎖來賓與共用的組織關聯性設定。

![Azure Active Directory 組織關聯性設定頁面的螢幕擷取畫面](media/azure-ad-organizational-relationships-settings.png)

若要設定組織關聯性設定

1. 登入 Microsoft Azure 在[https://portal.azure.com](https://portal.azure.com)。
2. 在左導覽中，按一下 [ **Azure Active Directory**]。
3. 在 [**概觀**] 窗格中，按一下 [**組織關聯性**。
4. 在**組織關聯性**] 窗格中，按一下 [**設定**]。
5. 確保**系統管理員和來賓邀請者角色中的使用者可以邀請**和**成員可以邀請**都會設**為 [是]**。
6. 如果您做了任何變更，請按一下 [儲存]****。

請注意 [**共同作業限制**] 區段中的設定。 請確定不封鎖的網域的來賓，您想要與共同作業。

## <a name="teams-guest-access-settings"></a>Teams 來賓存取設定

小組已開啟/關閉的來賓存取，且各種不同的設定可控制來賓可以做什麼小組中切換到主圖形。 主版參數時，**允許小組中的來賓存取**必須**上**的來賓存取在小組中運作。

請檢查可確保 Teams 中的來賓存取已啟用，以根據貴公司的來賓設定任何調整需求。 請記住，這些設定會影響所有的 microsoft teams。

![Teams 來賓存取切換的螢幕擷取畫面](media/teams-guest-access-toggle-on.png)

若要設定 microsoft Teams 來賓存取設定

1. 登入 Microsoft 365 系統管理中心， [https://admin.microsoft.com](https://admin.microsoft.com)。
2. 在左導覽中，按一下 [**全部顯示**]。
3. **系統管理中心**中，按一下 [ **microsoft Teams**。
4. 在 microsoft Teams 系統管理中心中，在左側導覽中，依序展開 [**全組織的設定**，按一下 [**來賓存取**。
5. 確定**允許小組中的來賓存取**設定為**上**。
6. 額外的來賓設定，讓任何想要的變更，然後按一下 [**儲存**。

> [!NOTE]
> 設定後將它開啟成為作用中的 Teams 來賓的可能需要最多 24 個小時。

## <a name="office-365-groups-guest-settings"></a>Office 365 群組的來賓設定

小組會使用 Office 365 群組的小組成員資格。 為了讓小組中的來賓存取運作，必須在開啟 Office 365 群組來賓設定。

![Microsoft 365 系統管理中心中 Office 365 群組來賓設定的螢幕擷取畫面](media/office-365-groups-guest-settings.png)

若要設定 Office 365 群組的來賓

1. 在 Microsoft 365 系統管理中心，在左側導覽中，展開 [**設定**]。
2. 按一下 [**服務 & 增益集**]。
3. 在清單中，按一下 [ **Office 365 群組**。
4. 請確定，**讓外部組織存取群組內容的群組成員**，**讓群組擁有者新增至群組在組織外的人員**] 核取方塊會同時檢查。
5. 如果您所做的變更，按一下 [**儲存變更**。


## <a name="sharepoint-organization-level-sharing-settings"></a>共用設定的 SharePoint 組織層級

所有儲存在 SharePoint 小組例如檔案、 資料夾及清單內容。 為了讓小組中有這些項目的存取權的來賓，SharePoint 組織層級共用設定必須允許與來賓共用。

組織層級設定會決定哪些設定可供個別的網站，包括 microsoft teams 相關聯的網站。 網站設定不能更寬鬆比組織層級的設定。

如果您想要允許的檔案和資料夾與匿名使用者共用，選擇 [**任何人**]。 如果您想要確定所有來賓都需要驗證，請選擇 [**新增] 和 [現有的來賓**。 選擇 [將您的組織中任何網站所需的最寬鬆] 設定。

![SharePoint 組織層級共用設定的螢幕擷取畫面](media/sharepoint-organization-external-sharing-controls.png)


若要設定共用設定的 SharePoint 組織層級

1. 在 Microsoft 365 系統管理中心，在左側導覽中，[**系統管理中心**中，按一下 [ **SharePoint**]。
2. 在 SharePoint 管理中心中，按一下左側導覽窗格中的 [共用]****。
3. 請確定該外部共用 SharePoint 設為**任何人**或**新增和現有的來賓**。
4. 如果您做了任何變更，請按一下 [儲存]****。


## <a name="sharepoint-organization-level-default-link-settings"></a>SharePoint 組織層級預設連結設定

預設檔案和資料夾連結設定會決定哪一個連結選項向使用者顯示預設情況下使用者共用的檔案或資料夾時。 使用者可以將連結類型變更為下列其中一個其他選項共用視之前。

請記住此設定會影響所有的 microsoft teams 和貴組織中的 SharePoint 網站。

選擇 [當使用者共用檔案及資料夾，依預設會選取連結的類型：

- **任何人] 連結**-如果您預期在具有匿名使用者共用檔案和資料夾的許多選擇此選項。 如果您想要允許*任何人*的連結，但擔心意外匿名共用，請考慮下列其中一個其他選項為預設值。 如果您已啟用**的任何人**共用，此連結類型只有。
- **只有在您的組織中的人員**-如果您預期大部分的檔案和資料夾共用您的組織內的人員都必須選擇此選項。
- **特定人員**-如果您預期執行許多檔案和資料夾與來賓共用，請考慮此選項。 這種類型的連結與來賓運作，以及需要進行驗證。
 
![SharePoint 組織層級檔案和資料夾共用設定的螢幕擷取畫面](media/sharepoint-organization-files-folders-sharing-settings.png)


若要設定 SharePoint 組織層級預設值] 連結

1. 瀏覽至 SharePoint 系統管理中心的 [共用] 頁面上。
2. [**檔案] 和 [資料夾] 連結**，選取預設共用您想要使用的連結。
3. 如果您做了任何變更，請按一下 [儲存]****。

## <a name="create-a-team"></a>建立小組

下一步是建立您計劃要用於來賓與共同作業小組。

若要建立小組
1. 在小組，[ **Teams** ] 索引標籤中，按一下 [**加入或建立小組**在左邊窗格的底部。
2. 按一下 [**建立小組**]。
3. 按一下 [**建立從頭小組**]。
4. 選擇 [**私人**或**公開**。
5. 輸入的名稱和描述小組、，然後按一下 [**建立**]。
6. 按一下 [**略過**。

我們將稍後邀請使用者。 接下來，務必檢查小組與相關聯的 SharePoint 網站的網站層級共用設定。

## <a name="sharepoint-site-level-sharing-settings"></a>SharePoint 網站層級共用設定

請檢查以確保它們允許您想要此小組的存取類型的網站層級共用設定。 例如，如果您設定組織層級設定為**任何人**，但您想要為此小組進行驗證的所有來賓，然後進行確認網站層級共用設定設為 [**新增] 和 [現有的來賓**。

![SharePoint 網站外部共用設定的螢幕擷取畫面](media/sharepoint-site-external-sharing-settings.png)


若要設定網站層級共用設定
1. 在 SharePoint 管理中心中，在左側導覽窗格中展開 [網站]****，然後按一下 [使用中網站]****。
2. 為您剛建立的小組選取網站。
3. 在功能區中，按一下 [共用]****。
4. 請確定該共用設為**任何人**或**新增和現有的來賓**。
5. 如果您做了任何變更，請按一下 [儲存]****。

## <a name="invite-users"></a>邀請使用者

來賓共用設定現在會進行設定，讓您可以開始將內部使用者和訪客新增至您的小組。 

若要邀請給小組的內部使用者
1. 在 [小組成員，按一下 [**更多選項]** (**\*\***)，然後按一下 [**新增成員**。
2. 輸入您想要邀請的人員名稱。
3. Click **Add**, and then click **Close**.

若要邀請給小組的來賓
1. 在 [小組成員，按一下 [**更多選項]** (**\*\***)，然後按一下 [**新增成員**。
2. 輸入您想要邀請來賓顯示的電子郵件地址。
3. 按一下 [**編輯來賓資訊**。
4. 輸入來賓顯示的完整名稱，然後按一下 [核取記號。
5. Click **Add**, and then click **Close**.

## <a name="see-also"></a>另請參閱

[與匿名使用者共用檔案和資料夾的最佳做法](best-practices-anonymous-sharing.md)

[與來賓共用時限制意外暴露檔案](sharing-limit-accidental-exposure.md)

[建立安全的來賓共用環境](create-a-secure-guest-sharing-environment.md)）


