---
title: 資料移動一般常見問題集
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/20/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 1f01bc6f-5d37-4d14-bdd3-9d94a1e23e14
f1.keywords:
- NOCSH
description: 以下是對一般問題的回答關於將核心資料移至新的資料中心地理位置。
ms.openlocfilehash: 3dcdb17bff899caa8d72799c9b3c4bb7d74c9e96
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840600"
---
# <a name="data-move-general-faq"></a>資料移動一般常見問題集

以下是對一般問題的回答關於將核心資料移至新的資料中心地理位置。
  
## <a name="what-customers-are-eligible-to-request-a-move"></a>合格要求移動何種客戶？
  
現有 Office 365 商業客戶選取合格新的資料中心地理位置的國家/地區都能夠要求移動。  將靜態適用於合格的工作負載的核心客戶資料移轉至對應的 Office 365 資料中心地理位置指派給 Office 365 租用戶合格的國家/地區碼存在僅適用於租用戶的程式。  請參閱[如何要求資料移動](request-your-data-move.md)頁面上，確認國家/地區資格。   

## <a name="how-do-we-define-core-customer-data"></a>我們要如何定義核心客戶資料？
 
核心客戶資料 」 一詞指的是[Microsoft 線上服務條款](https://aka.ms/ost)中所定義的客戶資料的子集： 
- Exchange Online 信箱內容 （電子郵件內文、 行事曆項目和電子郵件附件的內容）
- SharePoint Online 站台內容和儲存在該站台內的檔案
- 上傳到商務用 OneDrive 檔案 

## <a name="at-what-point-is-my-migration-complete-so-that-my-tenants-core-customer-data-is-being-stored-at-rest-in-my-new-geo"></a>在哪些點是我移轉完成，讓我的租用戶核心客戶資料儲存在我新的地理位置中的靜態嗎？

因為 Exchange Online 和 SharePoint Online/商務用 OneDrive 之間共用的相依性，任何移轉無法視為完成這兩項服務會完成移轉為止。  Exchange Online 和 SharePoint Online/商務用 OneDrive 通常移轉在不同的時間和分別從另一個。  當每個服務移轉已完成，並在系統管理中心可以檢視的資料位置卡片，確認每個服務 rest 位置的核心客戶資料的任何時候，租用戶系統管理員會收到確認訊息中心。

## <a name="will-my-tenant-automatically-be-moved-to-the-new-datacenter-geo"></a>將我的租用戶自動移至新的資料中心地理位置？
 
有兩個租用戶系統管理員身分，您可以採取的動作。

- 選擇集。註冊 Office 365 移動計劃中，會收到您的服務，將靜態的核心客戶資料移轉至新的資料中心地理位置的認可的期限。如何在選擇加入的計劃，請參閱[如何要求資料移動](request-your-data-move.md)頁面上的指示。
- 不執行任何動作。不採取任何動作，這會使 Microsoft 能夠將核心客戶資料移至新的資料中心地理位置的靜態經過一段時間服務管理和最佳化的一部分。您的資料只可能可以移至您的新資料中心地理，不適用於任何其他地理位置。我們透過訊息中心時通知這類服務管理移動完成。

## <a name="how-do-you-make-sure-my-customer-data-is-safe-during-the-move-and-that-i-wont-experience-downtime"></a>您如何確定我客戶資料在移動期間的安全且我將不會遇到停機時間？
  
資料移動是使用者的影響降至最低的後端服務作業。 可能會受到影響的功能會列在[期間和之後資料移動](during-and-after-your-data-move.md)。 我們將遵守[Microsoft Online Services 服務層級協議 (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897)可用性讓沒有任何客戶需要準備，或在移動期間監視的項目。 
  
所有 Office 365 服務中的資料中心，都執行相同的版本，因此您可以確定的一致的功能。 整個程序完全支援您的服務。

## <a name="what-is-in-scope-for-teams-migration"></a>什麼是在範圍內的 Teams 移轉？

除了 Exchange Online、 SharePoint Online 和商務用 OneDrive;Microsoft 會將 Teams 資料移轉至本機資料中心。  
- 小組聊天訊息，包括私人郵件和通道訊息。 
- 小組聊天中所用的圖像。 

Teams 檔案會儲存在 SharePoint Online 與小組聊天檔案會儲存在商務用 OneDrive。  語音信箱、 行事曆、 聊天歷程記錄，以及連絡人會儲存在 Exchange Online。  在許多情況下，Exchange Online、 SharePoint Online 和商務用 OneDrive 已由在本機的資料中心地理位置中客戶和也是 Office 365 移轉程式合格客戶的國家/地區的一部分。
  
## <a name="what-is-the-impact-of-having-different-services-located-in-different-geos"></a>具有不同服務位於不同 geos 的影響為何？

Office 365 服務的一些可能位於不同 geos 一些現有的客戶和正在移動程序的客戶。  我們的服務執行彼此獨立，如果是這樣就不會影響使用者經驗。不過，僅供資料落地，租用戶移轉無法被視為完成直到 Exchange Online 和 SharePoint Online/商務用 OneDrive 移轉到相同的資料中心地理位置。
  
## <a name="will-new-office-365-customers-be-automatically-provisioned-in-the-new-datacenter-geos"></a>將新的 Office 365 客戶可自動佈建中新的資料中心 geos 嗎？
  
是。 提供新的資料中心地理位置之後，新的 Office 365 的商務客戶選取作為其國家/地區的合格的新的地理位置的國家/地區註冊期間會有存放在新的資料中心地理位置中其核心客戶資料。
  
 ## <a name="where-is-my-core-customer-data-is-located"></a>其中是我核心客戶資料所在？

租用戶系統管理員可以檢視資料位置卡在系統管理中心來確認每個服務，特別針對其租用戶 rest 位置的核心客戶資料的任何時候。我們也將發佈的資料中心 geos、 資料中心及在新租用戶的 rest 位置目前的預設核心客戶資料的參照的位置上的 [Office 365 互動式資料中心對應](https://office.com/datamaps)的 Office 365 客戶資料的位置。  您可以在您的組織設定檔，Microsoft 365 系統管理中心中確認透過 [資料位置] 區段中的靜態客戶資料的位置。  
 
## <a name="when-will-i-be-able-to-request-a-move"></a>何時我能夠要求的移動？
  
請參閱[如何要求資料移動](request-your-data-move.md)頁面上的支援項資料中心地理位置。
  
## <a name="how-can-i-request-to-be-moved"></a>如何要求要移動？
  
合格客戶會看到其[Office 365 系統管理入口網站](https://portal.office.com/)中的頁面。 請如需如何移動要求相關指示，參閱[如何要求資料移動](request-your-data-move.md)。 
  
## <a name="can-i-change-my-selection-after-requesting-a-move"></a>可以變更我選取項目後要求移動嗎？
  
您不能為我們之後您提交要求您移除程序。
  
## <a name="what-happens-if-i-do-not-request-a-move-before-the-deadline"></a>如果我不要求之前期限移動發生什麼情況？
  
 我們可能會無法接受要求例外狀況為基礎來授與您的租用戶完成移動認可的期限。請 連絡[Office 365 支援人員](https://go.microsoft.com/fwlink/p/?LinkID=522459)來提出要求。  某些工作負載可能會移到您新的地理位置，即使沒有加入要求中做為不採取任何動作結果能夠將核心客戶資料移至新的資料中心地理位置的靜態經過一段時間一部分服務管理和最佳化的 Microsoft 中的重新叫用。您的資料只可能可以移至您的新資料中心地理，不適用於任何其他地理位置。  我們透過訊息中心時通知這類服務管理移動完成。
  
 ## <a name="what-if-i-want-to-move-my-data-in-order-to-get-better-network-performance"></a>如果我想要移動以取得較佳的網路效能的我的資料？
  
關閉 Office 365 資料中心正在並不保證郵件的較佳的網路效能。 有許多因素與影響使用者和 Office 365 服務之間的網路效能的元件。 如需有關此資訊和效能調整請參閱[網路規劃和效能調整的 Office 365](network-planning-and-performance.md)。
  
 ## <a name="do-all-the-services-move-their-data-on-the-same-day"></a>所有服務在同一天都移動其資料嗎？
 
每項服務分別移動，並可能會移動其資料在不同的時間。
  
 ## <a name="can-i-choose-when-i-want-my-data-to-be-moved"></a>可以選擇當我想要移動我資料？
 
 客戶可以選取特定日期，他們無法延遲其移動，且我們無法共用的特定日期或時間範圍結束前的移動。
  
 ## <a name="can-you-share-when-my-data-will-be-be-moved"></a>您可以共用我的資料將會被移動時？
  
資料移動是使用者的影響降至最低的後端作業。 複雜性，精確度和小我們要執行全域操作和自動化環境內的資料移動禁止我們共用時的資料移動預計需要完成您的租用戶或任何其他單一租用戶。 客戶會收到一個確認訊息中心中每個參與服務時已完成其資料移動。 
  
 ## <a name="what-happens-if-users-access-services-while-the-data-is-being-moved"></a>如果移動資料時，使用者會存取服務，會發生什麼事？

在某些部分的每個服務的資料移動期間可能有限的功能的完整清單，請參閱[期間和之後資料移動](during-and-after-your-data-move.md)。 
  
 ## <a name="how-do-i-know-the-move-is-complete"></a>如何知道移動作業就會完成？
  
觀看 Office 365 訊息中心，確認每個服務資料的移動作業完成。 每個服務的資料移動時，我們就會張貼完成通知，讓您會看到三個完成通知： 的一對每個 Exchange Online、 SharePoint Online 和商務用 Skype。  您也可以在您的組織設定檔，Microsoft 365 系統管理中心中確認您透過 [資料位置] 區段中的靜態的客戶資料的位置。  
  
## <a name="i-am-an-office-365-customer-in-one-of-the-new-datacenter-geos-but-when-i-signed-up-i-selected-a-different-country-how-can-i-be-moved-to-the-new-datacenter-geo"></a>我是下列其中一個新的資料中心 geos，Office 365 客戶，但當我註冊，我選取不同的國家/地區。 如何可以我要移至新的資料中心地理位置？

您不能變更您的租用戶相關聯的註冊國家/地區。 相反地，您需要使用新的訂閱建立新的 Office 365 租用戶，並以手動方式將您的使用者和資料移至新的租用戶。
  
## <a name="what-happens-if-we-are-in-process-of-email-data-migration-to-office-365-during-the-exchange-online-move"></a>如果我們 in process of 電子郵件資料移轉到 Office 365 Exchange Online 的移動作業期間發生什麼情況？

這是很常見的案例，並完全支援。  雲端移轉資料中心 geos 之間不會干擾任何上-premisis 到雲端信箱移轉。
  
 ## <a name="can-i-pilot-some-users"></a>我可以試驗部分使用者嗎？
  
您可以建立不同的試用版租用戶來測試連線，但不能與您現有的租用戶以任何方式結合試用版租用戶。

## <a name="i-dont-want-to-wait-for-microsoft-to-move-my-data-can-i-just-create-a-new-tenant-and-move-myself"></a>我不想要等候 Microsoft，以移動我的資料。 可以只建立新的租用戶和移動自行嗎？
  
是的不過，將無法完美彿 Microsoft 就執行資料移動程序。
  
如果可以使用新的資料中心地理位置之後，您會建立新租用戶，在新租用戶會裝載於新的地理位置。 這個新的租用戶是完全獨立於您舊的租用戶，您就是負責移動所有使用者信箱、 網站內容、 網域名稱，與其他任何資料。 請注意，您無法到另一個租用戶移動租用戶名稱。 我們建議您等候 Microsoft 所提供，因為我們會負責移動所有設定、 資料和使用者的訂閱移動程式。
  
 ## <a name="im-not-ready-to-be-moved-can-i-pick-a-specific-move-date"></a>我已經不可以移動，我可以挑選特定移動日期嗎？
  
否，不能為您要變更時將會移動的每個服務的核心客戶資料。
  
 ## <a name="my-customer-data-has-already-been-moved-to-a-new-datacenter-geo-can-i-move-back"></a>我的客戶資料已被移至新的資料中心地理位置。 可以我移回嗎？
 
否，這是不可行。 已移至新的地理資料中心的客戶無法移回。 身為任何地理位置的客戶，您會遇到服務、 效能及安全性控制的相同品質之前所顯示的一樣。  [Office 365 多地理位置](https://aka.ms/multi-geo)當作附加元件會有些客戶可以使用，並讓單一租用戶建立多個衛星 geos，並將使用者資料移至這些 geos 與資料落地承諾。
  
 ## <a name="do-the-new-datacenter-geos-use-the-same-versions-of-office-365-services-as-the-current-datacenter-geos"></a>新的資料中心 geos 是否為目前的資料中心 geos 使用相同版本的 Office 365 服務？

是。
  
## <a name="will-office-365-tenants-hosted-in-the-new-datacenters-be-available-to-users-outside-of-the-country"></a>Office 365 租用戶中新的資料中心主控可以外的國家/地區的使用者？
  
答： 是的。 Microsoft 的維護大型的全球網路與在具有多個 2700 網際網路服務提供者 (Isp) 的對等協議與世界各地 35 國家/地區的多個 130 位置中的公用網際網路連線。 使用者無法從任何地方網際網路上存取的資料中心。

## <a name="my-tenant-is-configured-for-office-365-multi-geohttpsakamsmulti-geo--can-i-still-enroll-in-my-tenant-in-the-office-365-move-program-to-change-my-default-geo-and-move-any-user-not-in-a-satellite-region-to-the-new-default-geo"></a>我的租用戶已針對[Office 365 多地理位置](https://aka.ms/multi-geo)。  我還是註冊 Office 365 移動在程式中變更我的預設地理位置，並將任何使用者，而不是以衛星區域移至新的預設地理我租用戶中可以嗎？

是，您的租用戶是合格註冊。  我們將會從目前的預設地理所有 EXO 信箱都移至新的本機資料中心地理位置。  我們不會移動到持續採用衛星地區資料落地預期已在多地理衛星地區設定任何 EXO 信箱。  SharePoint Online 和商務用 OneDrive 無法移轉至新的資料中心地理位置一部分移動的程式，但是您可以設定 OneDrive for Business 共用透過多地理位置程式移至您想任何區域。
  
## <a name="related-topics"></a>相關主題

[將核心資料移至新的 Office 365 資料中心 geos](moving-data-to-new-datacenter-geos.md)

[如何要求資料移動](request-your-data-move.md)

[Office 365 多地理位置](https://aka.ms/multi-geo)

[Office 365 互動式資料中心地圖](https://office.com/datamaps)

[Office 365 支援人員](https://go.microsoft.com/fwlink/p/?LinkID=522459)

[Microsoft Dynamics CRM online 的新資料中心 geos](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[依地區的 azure 服務](https://azure.microsoft.com/regions/)
