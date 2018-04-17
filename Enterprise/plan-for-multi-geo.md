---
title: 規劃 OneDrive for Business 多重地理位置
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: 了解 OneDrive 商務多重地理位置、 多個地理位置的運作方式，且何種地理位置可供資料存放區。
ms.openlocfilehash: d7d6cfbbff4cf0ec2516f2506946c2832d96b3f2
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a>規劃 OneDrive for Business 多重地理位置

本指南旨在協助系統管理員的人員，供其準備其展開至 「 公司的平台服務以滿足資料 residency 需求的其他地理位置的 SharePoint Online 租用戶的多重國民公司 (MNCs)。

在 OneDrive 多重地理位置設定中，您的 Office 365 租用戶包含一個集中的位置 （也稱為預設位置） 和一或多個衛星地理位置。這是跨多個地理位置之間的單一租用戶。在 OneDrive 多-地理位置，您的租用戶資訊，包括地理位置對應中 Azure Active Directory (AAD)。 

以下是一些重要的多個地理位置詞彙協助您了解設定的基本概念：

-   **租用戶**– Office 365 雲端通常具有與它相關聯的一或多個網域中的組織的表示法 (例如http://contoso.sharepoint.com)。 

-   **地理位置**– 主控您的租用戶資料的地理位置。多個地理位置承租人跨越多個地理位置，例如 「 北美地區 」 和 「 歐洲。

-   **允許資料位置 (ADL)** – 的租用戶已設定主機 OneDrive 及 SharePoint 資料的地理位置。

-   **慣用的資料位置 (PDL)** -儲存個別使用者的 OneDrive 資料的地理位置。這可以是任何允許資料位置已設定為承租人管理員設定。請注意是否您變更 PDL 已經有 OneDrive 站台的使用者，他們 OneDrive 資料為未移至新的地理位置自動。如需詳細資訊，請參閱[移到不同地理位置的 OneDrive 文件庫](move-onedrive-between-geo-locations.md)。

啟用多個地理位置需要四個主要步驟：

1.  若要新增_多個地理位置功能的 Office 365_服務計劃帳戶小組與搭配使用。

2.  選擇您想要的衛星地理位置並將其新增至您的租用戶。

3.  設定使用者的偏好的資料位置所需的衛星地理位置。當新 OneDrive 網站佈建的使用者時，它已佈建至其 PDL。

4.  使用者的現有 OneDrive 將網站移轉從首頁位置到視其偏好的資料位置。

請參閱[設定 OneDrive for Business 多-地理位置](multi-geo-tenant-configuration.md)的每個這些步驟的詳細資訊。

> [!IMPORTANT]
> 請注意針對效能最佳化案例旨在不到 Office 365 的多重地理位置功能，其設計用來符合資料 residency 需求。如需效能最佳化 Office 365 的詳細資訊，請參閱[網路規劃和 Office 365 的效能調整](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848)或連絡支援群組。

您可以設定任何要裝載 OneDrive 檔案的採衛星地理位置的下列位置。當您規劃多個地理位置，進行您想要新增至 Office 365 租用戶的位置清單。我們建議具有一或兩個衛星位置開始逐漸擴充到多個地理位置，視。

<table>
<thead>
<tr class="header">
<th align="left"><strong>位置</strong></th>
<th align="left"><strong>程式碼</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">亞太地區</td>
<td align="left">APC</td>
</tr>
<tr class="even">
<td align="left">歐洲 / 東部正 / 非洲</td>
<td align="left">EUR</td>
</tr>
<tr class="odd">
<td align="left">北美</td>
<td align="left">名稱</td>
</tr>
<tr class="even">
<td align="left">澳大利亞</td>
<td align="left">澳洲</td>
</tr>
<tr class="odd">
<td align="left">加拿大</td>
<td align="left">可以</td>
</tr>
<tr class="odd">
<td align="left">日本</td>
<td align="left">日文</td>
</tr>
<tr class="even">
<td align="left">韓國</td>
<td align="left">韓文</td>
</tr>
<tr class="odd">
<td align="left">英國</td>
<td align="left">GBR</td>
</tr>
</tbody>
</table>

即將推出的地理位置：
  
- 法國
- 印度

當您設定多個地理位置時，請考慮將您的內部部署基礎結構時移轉至 Office 365 機會。例如，如果您有內部部署伺服器陣列中新加坡和馬來西亞，然後您可以合併它們到 APC 衛星位置提供資料 residency 需求允許您這麼。

## <a name="best-practices"></a>最佳做法

我們建議您執行一些初始測試的 Office 365 中建立測試使用者。我們將逐步解說一些測試及驗證步驟與此使用者才可繼續進行內建的實際執行使用者到 OneDrive 多重地理位置功能。

一旦您已經完成測試的測試使用者，選取試驗群組 – 或許從您的 IT 部門 – 設為使用 OneDrive 在新的地理位置中之第一個。這個第一個群組中，選取尚未沒有 OneDrive 的使用者。我們建議使用不得超過五個此初始群組中的人員以及逐步展開 [追蹤批次導入方法。

每位使用者應可在*慣用的資料位置*(PDL) 設定可讓判斷 Office 365 中佈建其 OneDrive 的地理位置。使用者的偏好的資料位置必須符合其中一個您所選擇的衛星位置或您集中的位置。雖然 PDL 欄位不是必要的但是建議 PDL 為所有使用者的設定。在集中管理位置上的多個地理位置邏輯架構中佈建 PDL 沒有使用者的工作負載。   

建立您的使用者清單，並包括其使用者主要名稱 (UPN) 與適當的慣用的資料位置的位置程式碼。開始使用包括測試使用者與您的初始試驗群組。如需設定程序需要此清單。

如果您的使用者會從同步處理內部部署 Active Directory (AD) 系統以 Azure Active Directory (AAD)，您必須使用 Azure [Active Directory 連線設定同步處理使用者的偏好的資料位置。您無法直接設定使用 Azure AD PowerShell 的同步處理使用者的偏好的資料位置。在 AD PDL 設定並將它同步處理步驟涵蓋在[Azure [Active Directory 連線同步處理： 設定 Office 365 資源的慣用的資料位置](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)。

從非多重地理承租人，請為許多 SharePoint 和 OneDrive 設定而異的多個地理位置租用戶管理及服務的多個地理注意。我們建議您檢閱[管理多個地理位置環境](administering-a-multi-geo-environment.md)您才可以繼續使用您的設定。

如需在多個地理位置環境中的一般使用者經驗的詳細資訊，請閱讀[multgeo 環境中的使用者體驗](multi-geo-user-experience.md)。

若要開始設定 OneDrive for Business 多-地理位置，請參閱 ＜[設定 OneDrive for Business 多-地理位置](multi-geo-tenant-configuration.md)。

視要取得您的使用者使用其偏好的資料位置從一旦您已經完成設定，請記得移轉[使用者的 OneDrive 文件庫](move-onedrive-between-geo-locations.md)。
