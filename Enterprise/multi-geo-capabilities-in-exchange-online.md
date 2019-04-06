---
title: Exchange 多地理位置
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: 了解多地理位置功能在 Exchange Online。
ms.openlocfilehash: 60d25cab08ada195d1b189b30bdce8ea505f1d19
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2019
ms.locfileid: "30931772"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a>Exchange Online 中的多地理位置功能

在多地理位置環境中，您可以根據每位使用者選取 Exchange Online 信箱內容 （靜態資料） 的位置。

您可以將信箱置於由衛星位置：

- 直接在衛星位置中建立新的 Exchange Online 信箱

- 將現有的 Exchange Online 信箱移至衛星位置中，藉由變更使用者的慣用的資料位置

- 上架的信箱從內部部署 Exchange 組織直接將衛星位置

## <a name="mailbox-placement-and-moves"></a>信箱位置及移動
Microsoft 完成必要的多地理位置的設定步驟之後，Exchange Online 會受限於使用者物件上的**PreferredDataLocation**屬性在 Azure AD 中。

Exchange Online 會同步處理從 Azure AD 的**PreferredDataLocation**屬性到 Exchange Online 的目錄服務中的**MailboxRegion**屬性。 **MailboxRegion**的值會決定要放置使用者信箱和任何相關聯的封存信箱的地理位置。 您不能設定使用者的主要信箱和封存信箱位於不同地理位置。 只有一個地理位置可能會設定每個使用者物件。

- 當**PreferredDataLocation**設定與現有信箱使用者時，信箱將會放入佇列中重新配置，而且會自動移至指定的地理位置。 

- 當**PreferredDataLocation**設定上沒有現有的信箱，使用者佈建信箱時，將會佈建到指定的地理位置。 

- 當**PreferredDataLocation**上未指定一位使用者，當您佈建信箱時，將會佈建中央位置中。

- 如果是不正確的**PreferredDataLocation**程式碼 （例如類型而不是北美洲 NAN），該信箱佈建中央位置中。

**附註**： 在多地理位置功能與 Skype for Business Online 主辦的會議這兩個使用者物件上使用**PreferredDataLocation**屬性來尋找服務。 如果您的地區主辦裝載會議的使用者物件上設定**PreferredDataLocation**值，這些使用者的信箱將會自動移至指定的地理位置之後的 Office 365 租用戶上啟用多地理位置。

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a>Exchange Online 中的多地理功能會受到限制

1. 安全性與合規性功能 （例如，稽核和 eDiscovery） 可供使用 Exchange 系統管理中心 (EAC) 中無法使用多地理位置組織中。 相反地，您需要使用[Office 365 安全性 & 合規性中心](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8)來設定安全性與合規性功能。

2. 當您將信箱移至新的地理位置，outlook for Mac 使用者可能會遇到暫時遺失其線上封存資料夾存取權。 此條件可發生於使用者的主要和封存信箱皆位於不同地理位置，因為跨地理信箱移動可能會在不同的時間完成。

3. 使用者無法跨 （先前稱為 Outlook Web App 或 OWA） 網頁型 Outlook 中的地理位置間共用*信箱資料夾*。 例如，在歐盟地區的使用者無法用於網頁型 Outlook 開啟的共用的資料夾位於美國境內的信箱中。 不過，Outlook 網頁使用者可以開啟*其他信箱*中不同 Geos 藉由使用不同的瀏覽器視窗中[開啟另一個人的信箱在 Outlook Web App 中的另一個瀏覽器視窗中](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362)所述。

    **附註**： 在 Windows 上的 Outlook 中支援跨地理信箱資料夾共用。

