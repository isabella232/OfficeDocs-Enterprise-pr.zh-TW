---
title: 在網站中與來賓共同作業
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: 了解如何在 SharePoint 網站中的來賓與共同作業。
ms.openlocfilehash: 746e592a027c05f489e9f5dfe819cfb107c6b1f5
ms.sourcegitcommit: 7e65640fb1a86858a95c9ef0edbb58d0f171c5ee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/06/2019
ms.locfileid: "39886482"
---
# <a name="collaborate-with-guests-in-a-site"></a>在網站中與來賓共同作業

如果您需要整個文件、 資料和清單與來賓共同作業，您可以使用 SharePoint 網站。 新式的 SharePoint 網站連線到 Office 365 群組以管理站台成員資格，並提供其他共同作業工具，例如共用的信箱和行事曆。

在本文中，我們會逐步設定來賓與共同作業的 SharePoint 網站所需的 Microsoft 365 組態步驟。

## <a name="video-demonstration"></a>影片示範

這段影片顯示本文所述的設定步驟。</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE44Llg?autoplay=false]

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

## <a name="office-365-groups-guest-settings"></a>Office 365 群組的來賓設定

新式的 SharePoint 網站使用 Office 365 群組來控制網站存取權。 Office 365 群組的來賓設定必須開啟 SharePoint 網站中的來賓存取工作的順序。

![Microsoft 365 系統管理中心中 Office 365 群組來賓設定的螢幕擷取畫面](media/office-365-groups-guest-settings.png)

若要設定 Office 365 群組的來賓

1. 在 Microsoft 365 系統管理中心，在左側導覽中，展開 [**設定**]。
2. 按一下 [**服務 & 增益集**]。
3. 在清單中，按一下 [ **Office 365 群組**。
4. 請確定，**讓外部組織存取群組內容的群組成員**，**讓群組擁有者新增至群組在組織外的人員**] 核取方塊會同時檢查。
5. 如果您所做的變更，按一下 [**儲存變更**。


## <a name="sharepoint-organization-level-sharing-settings"></a>共用設定的 SharePoint 組織層級

為了讓訪客能夠存取 SharePoint 網站，SharePoint 組織層級共用設定必須允許與來賓共用。

組織層級設定會決定哪些設定可供個別的網站。 網站設定不能更寬鬆比組織層級的設定。

如果您想要允許未經驗證的檔案及資料夾共用，選擇 [**任何人**]。 如果您想要確定所有來賓都需要驗證，請選擇 [**新增] 和 [現有的來賓**。 選擇 [將您的組織中任何網站所需的最寬鬆] 設定。

![SharePoint 組織層級共用設定的螢幕擷取畫面](media/sharepoint-organization-external-sharing-controls.png)


若要設定共用設定的 SharePoint 組織層級

1. 在 Microsoft 365 系統管理中心，在左側導覽中，[**系統管理中心**中，按一下 [ **SharePoint**]。
2. 在 SharePoint 管理中心中，按一下左側導覽窗格中的 [共用]****。
3. 請確定該外部共用 SharePoint 設為**任何人**或**新增和現有的來賓**。
4. 如果您做了任何變更，請按一下 [儲存]****。

## <a name="create-a-site"></a>建立網站

下一步是建立您計劃要用於來賓與共同作業網站。

若要建立網站
1. 在 SharePoint 系統管理中心中，[**網站**]，按一下 [**作用中網站**。
2. 按一下 **[建立]**。
3. 按一下 [**小組網站**。
4. 輸入網站名稱，然後輸入群組擁有者 （網站擁有者） 的名稱。
5. [**進階設定**]，選擇 [是否您想要這是公用或私用網站。
6. 按 [下一步]****。
7. 按一下 **[完成]**。

我們將稍後邀請使用者。 接下來，務必要檢查此網站的網站層級共用設定。

## <a name="sharepoint-site-level-sharing-settings"></a>SharePoint 網站層級共用設定

請檢查以確保它們允許您要用於此網站的存取類型的網站層級共用設定。 例如，如果您設定組織層級設定為**任何人**，但您想要驗證這個網站的所有來賓，然後進行確認網站層級共用設定設為 [**新增] 和 [現有的來賓**。

請注意，不能與未驗證的人員 （**任何人都**設定），共用網站，但是可以個別檔案和資料夾。

![SharePoint 網站外部共用設定的螢幕擷取畫面](media/sharepoint-site-external-sharing-settings.png)

若要設定網站層級共用設定
1. 在 SharePoint 管理中心中，在左側導覽窗格中展開 [網站]****，然後按一下 [使用中網站]****。
2. 選取您剛建立的網站。
3. 在功能區中，按一下 [共用]****。
4. 請確定該共用設為**任何人**或**新增和現有的來賓**。
5. 如果您做了任何變更，請按一下 [儲存]****。

## <a name="invite-users"></a>邀請使用者

來賓共用設定現在會進行設定，讓您可以開始將內部使用者和訪客新增至您的網站。 讓我們將持續加入那里使用者網站存取權是透過相關聯的 Office 365 群組，來控制。

若要邀請內部使用者至群組
1. 瀏覽至您要新增使用者的網站。
2. 按一下右上角的 [**成員**]。
3. 按一下 [新增成員]****。
4. 輸入的名稱或電子郵件地址，您想要邀請至網站的使用者，然後按一下 [**儲存**。

來賓使用者無法新增從站台。 您必須將它們新增使用網頁型 Outlook。

若要邀請來賓至網站
1. 在 Outlook 網頁版、 在 [**群組**] 中按一下您要新增成員的群組。
2. 開啟群組連絡人卡片、，然後按一下 [**更多選項]** （...）] 下的 [**新增成員**。
3. 輸入您想要邀請，來賓電子郵件地址，然後按一下 [**新增]**。
4. 按一下 [關閉]****。

## <a name="see-also"></a>另請參閱

[最佳做法與未驗證的使用者共用檔案和資料夾](best-practices-anonymous-sharing.md)

[與來賓共用時限制意外暴露檔案](sharing-limit-accidental-exposure.md)

[建立安全的來賓共用環境](create-a-secure-guest-sharing-environment.md)）

