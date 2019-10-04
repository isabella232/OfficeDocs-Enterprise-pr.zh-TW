---
title: Office 365 Exchange Online 資料刪除
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
description: 如何虛硬式資料刪除處理及 Exchange Online 內。
ms.openlocfilehash: f25f2416778f19f8b2e464e31e6116a81eb872cc
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067338"
---
# <a name="exchange-online-data-deletion-in-office-365"></a>Office 365 中的 Exchange Online 資料刪除
在 Exchange Online 中，有兩種類型的刪除： 虛刪除和實刪除。 這適用於信箱和信箱內的項目。

## <a name="soft-deleted-and-hard-deleted-mailboxes"></a>虛刪除和實刪除信箱
「 虛刪除的使用者信箱 」 是已使用 Microsoft 365 系統管理中心或 Remove-mailbox cmdlet 刪除且仍在 Azure Active Directory 資源回收筒小於 30 天的信箱。 信箱可成為虛刪除任何下列的方式：
- 使用者信箱的相關聯的使用者帳戶是虛刪除的 Azure Active Directory （使用者物件會超出範圍或資源回收筒] 容器中）。
- 使用者信箱的相關聯的 Azure Active Directory 使用者帳戶已實刪除，但 Exchange Online 信箱在訴訟資料暫留或 eDiscovery 保留。
- 使用者信箱的相關聯的使用者帳戶已清除在過去 30 天內; 內的 Azure Active Directory這是 Exchange Online 的最大保留長度會保留信箱中虛刪除 」 狀態之前就永久清除且無法復原。

實刪除使用者信箱位於信箱已刪除下列方法之一：
- 使用者信箱已虛刪除超過 30 天，以及相關聯的 Azure Active Directory 使用者已實刪除。 永久刪除所有的信箱內容，例如電子郵件、 連絡人及檔案。
- 實刪除從 Azure Active Directory 已與使用者信箱相關聯的使用者帳戶。 使用者信箱現在是虛刪除 Exchange Online 中，而且會停留在虛刪除 」 狀態，30 天。 如果在 30 天內新的 Azure Active Directory 使用者從同步處理具有相同的**ExchangeGuid**或**ArchiveGuid**，原始的收件者帳戶及新的帳戶是 Exchange online 授權，這樣會導致實刪除原始的使用者信箱。 永久刪除所有的信箱內容，例如電子郵件、 連絡人及檔案。
- 使用**Remove-mailbox PermanentlyDelete**刪除虛刪除的信箱。

上述的刪除案例假設使用者信箱不在任何的保留狀態，例如訴訟資料暫留或 eDiscovery 保留。 如果沒有任何類型的保留在信箱上，不能刪除信箱。 對於所有郵件使用者收件者類型，任何[保留](https://support.office.com/article/manage-legal-investigations-in-office-365-2e5fbe9f-ee4d-4178-8ff8-4356bc1b168e?ui=en-US&rs=en-US&ad=US)設定和會忽略實刪除或虛刪除上沒有作用。

## <a name="soft-deleted-and-hard-deleted-items"></a>虛刪除和實刪除的項目
當使用者刪除的信箱項目 （例如電子郵件、 連絡人、 行事曆約會或工作） 時，項目移至 [可復原的項目] 資料夾中，並插入名為 「 刪除 」 子資料夾。 這稱為 「 虛刪除 」。 多久已刪除的項目會保留在刪除資料夾取決於信箱設定的刪除項目保留期間。 Exchange Online 信箱會保留已刪除項目 14 天依預設，但 Exchange Online 系統管理員可以變更此設定會增加最多個最大值為 30 天的期間。 （如增加 Exchange Online 信箱的刪除項目保留期間的詳細步驟，請參閱[變更多久永久刪除項目會保留 Exchange Online 信箱](https://docs.microsoft.com/exchange/recipients-in-exchange-online/manage-user-mailboxes/change-deleted-item-retention)。）使用者可以復原或清除刪除的項目保留時間到期之前刪除的項目。 若要這麼做，他們可以使用 Microsoft Outlook 或網頁型 Outlook 中的 [復原刪除的項目] 功能。

如果使用者使用 Outlook 或網頁型 Outlook 中的 [復原刪除的項目] 功能清除已刪除的項目，這就是所謂實刪除。 在 Exchange Online 中，單一項目復原時會啟用預設會建立新的信箱，讓系統管理員仍然可以[復原](https://docs.microsoft.com/Exchange/recipients/user-mailboxes/recover-deleted-messages)實刪除的項目已刪除的項目保留期間到期之前。 此外，如果郵件由使用者或處理程序變更，原始項目的複本時，會也保留在啟用單一項目復原。

## <a name="page-zeroing"></a>清空分頁
*Zeroing*是零或二進位模式覆寫已刪除的資料，以便更難復原已刪除的資料的安全性機制。 在 Exchange Online 中，信箱資料庫*頁面*作為其單位存放區，並實作稱為 「*分頁清空*覆寫程序。 根據預設，會啟用分頁清空，不能由客戶或 Microsoft 停用。 分頁清空作業會記錄在交易記錄檔中，以便指定資料庫所有副本頁面-都清空的類似的方式。 清空主動資料庫副本上的頁面會導致頁面清空會在資料庫的被動副本上。

分頁清空會以二進位模式透過實刪除記錄。 分頁清空模式是專屬於 （內部資料庫引擎的名稱伺服器使用在 Exchange Online） 的可延伸儲存引擎 (ESE) 作業，並而言是不同的執行階段作業與背景資料庫維護作業。 （背景資料庫維護是連續總和檢查和掃描每個資料庫的程序。 其主要功能是總和檢查碼資料庫頁面，但它也會處理清除空間，並清空記錄和已不出清空由於儲存區損毀的頁面）。

下表列出對應至特定執行階段作業的填滿圖樣。

| ESE 執行階段作業   | 填滿圖樣 |
|--------------------------|--------------|
| 取代                  | R            |
| 記錄/長數值刪除 | D            |
| 釋放的頁面空間         | H            |


下表列出對應至特定作業的填滿圖樣，這些作業是在 ESE 背景資料庫維護期間進行。

| ESE 背景資料庫維護作業 | 填滿圖樣 |
|-----------------------------------------------|--------------|
| 記錄刪除                                 | D            |
| 長數值刪除                             | L            |
| 部分使用頁面的已釋放頁面空間       | Z            |
| 未使用頁面的已釋放頁面空間               | U            |


### <a name="page-zeroing-process"></a>頁面清空的處理程序
分頁清空的程序取決於刪除案例。 下表討論資料庫刪除案例，以及分頁清空功能發生的時間。

| 資料庫刪除案例 | 清空資料庫資料 的 ESE 處理程序和時段 |
|-----------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 項目過期取決於已刪除的項目保留期間。 | 非同步執行緒會以二進位模式覆寫刪除的資料。 此動作會在記錄刪除的幾毫秒內發生。 背景資料庫維護處理該區段的資料庫時，如果非同步清空工作是仍未執行 （或版本儲存區清理取消由於版本儲存區成長） 時，發生當機儲存程序，清空已完成。 |
| 檢視案例： 上的項目從 Outlook/Outlook web 資料夾檢視 （例如，交談] 檢視） 的到期日 | 資料清空會在背景資料庫維護處理該區段的資料庫時進行。 |
| 移動信箱/刪除信箱案例： 刪除來源信箱 （刪除的信箱到期） | 資料清空會在背景資料庫維護處理該區段的資料庫時進行。 |

### <a name="mailbox-data-types-without-page-zeroing"></a>不清空分頁的信箱資料類型
下列信箱資料類型有無佈建分頁清空：
- **信箱資料庫交易記錄檔**-當交易記錄檔會正常作業的一部分刪除時，就會發生的區塊清空儲存已刪除的記錄檔的檔案系統中沒有程序。 很可能檔案系統會快速重新利用該可用空間供新建立的記錄，但不保證，則會發生。
- **內容索引類別目錄檔案**-Exchange Online 會使用 Search Foundation (也就是 FAST) 來執行搜尋檢索功能。 搜尋索引類別目錄是由儲存在信箱資料庫檔案所在的磁碟區上的數個幾十檔案所組成。 從信箱資料庫實刪除郵件時，不會立即刪除搜尋類別目錄中關聯的內容。 當 Search Foundation 執行時，便會刪除內容許多小型類別目錄檔案中的單一較大檔案陰影 （或主要合併）。 完成主要合併後，便會將較小的類別目錄檔案刪除。 沒有任何程序可將儲存已刪除之類別目錄檔案的區塊清空。

## <a name="continuous-replication"></a>連續複寫
連續複寫 （也稱為記錄傳送及重新顯示） 是 Exchange Online 中，會建立及維護以提供高可用性、 站台恢復和嚴重損壞修復每個信箱資料庫副本的技術。 連續複寫利用 Exchange Server 資料庫損毀修復 」 支援，以提供執行非同步方式更新一或多個信箱資料庫副本的技術。 每個信箱伺服器會記錄在作用中的資料庫 （例如，使用者的電子郵件活動） 上所做的資料庫更新為 1 MB 的交易記錄檔的循序集中的記錄。 這一組檔案稱為記錄資料流。 在連續複寫的記錄資料流是也用於以非同步方式更新一或多個資料庫副本。 這透過傳輸記錄檔包含主動資料庫的被動副本，然後重新執行其中一個被動資料庫副本的位置。 如果從主動資料庫的所有記錄都對應資料庫的被動副本，然後兩個資料庫是相等的而且經由這個程序作用中資料庫所做的任何實體變更會複寫至該資料庫的所有被動副本。

從信箱資料庫，任何刪除的信箱項目或整個信箱，以及是否虛刪除或實刪除，代表實體變更作用中的資料庫。 分頁清空也會需要變更實體作用中的資料庫。 這些變更會寫入到稱為連續複寫程序之記錄檔和相同的實體變更時這些記錄檔已對應資料庫的被動副本，會對這些被動的資料庫。