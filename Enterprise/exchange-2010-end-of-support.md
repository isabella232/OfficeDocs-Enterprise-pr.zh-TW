---
title: Exchange 2010 終止支援藍圖
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 1/31/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.assetid: e150e7b9-c432-4c8d-a0ae-c11847129a7d
description: Exchange 2010 即將終止支援。 使用此規劃藍圖做為指南，以準備升級至 Exchange Online 或較新版的 Exchange Server 內部部署。
ms.openlocfilehash: f0ff6551f9ef2c0ed57baabacc04293e83d25e13
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067569"
---
# <a name="exchange-2010-end-of-support-roadmap"></a>Exchange 2010 終止支援藍圖

**2020 年 1 月 14，**，在 Exchange Server 2010 會達到終止支援。 如果您已經尚未開始移轉到 Office 365 的 Exchange 2010 或 Exchange 2016，現在是以開始您規劃的時間。

## <a name="what-does-end-of-support-mean"></a>支援平均數的哪些並結束？

Exchange 伺服器，例如幾乎所有的 Microsoft 產品中，有支援週期，我們會提供新功能、 錯誤修正程式、 安全性修正程式、 等等。 此生命週期通常會持續 10 年起的產品的初始版本，與此生命週期結束稱為 「 支援的產品的結尾。
Exchange 2010 達到 2020 年 1 月 14，支援其結束時將不再提供 Microsoft:

- 技術支援問題，可能會發生;
- 錯誤修正問題，會發現及，可能會影響 exchange 的穩定性與可用性的伺服器;
- 安全性問題修正，會發現及，可能會讓伺服器受到安全性弱點; 的弱點
- 時間的時區更新。

您的 Exchange 2010 的安裝會繼續執行此日期之後。 不過，由於上述的變更，我們強烈建議您儘速移轉從 Exchange 2010。

如需接近終止支援的 Office 2010 伺服器的詳細資訊，請參閱 <<c0>資源可以幫助您升級從 Office 2010 伺服器和用戶端。

## <a name="what-are-my-options"></a>我的選項為何？

與到達其終止支援 Exchange 2010，這是很好的時間，瀏覽您的選項，並準備移轉計劃。 您可以：

- 完全移轉到 Office 365。 使用完全移轉、 基本混合式或完整的混合式遷移來遷移信箱，然後移除內部部署 Exchange 伺服器與 Active Directory。
- 移轉到 Exchange 2016 的 Exchange 2010 伺服器，在您的內部部署伺服器上。

> [!IMPORTANT]
> 如果您的組織選擇將信箱移轉到 Office 365，但要繼續從內部部署 Active Directory 管理使用者帳戶就地保留 DirSync 或 Azure AD Connect，您需要保留至少一個 Exchange 伺服器內部部署。 如果移除最後一部 Exchange 伺服器，您無法在 Exchange Online 中的 Exchange 收件者進行變更。 這是授權的因為來源仍會保留在內部部署 Active Directory 中，需要有進行的變更。 在此案例中，您可以使用下列選項：

- （**建議**）如果您可以將信箱移轉到 Office 365 並 2020 年 1 月 14，升級您的伺服器使用 Exchange 2010 來連線到 Office 365，並將信箱移轉。 接下來，將 Exchange 2010 移轉至 Exchange 2016，然後解除委任任何剩餘的 Exchange 2010 伺服器。
- 如果無法完成的信箱移轉，並由 2020 年 1 月 14，內部部署伺服器升級升級您的內部部署 Exchange 2010 伺服器至 Exchange 2016 第一次，然後使用 Exchange 2016 來連線到 Office 365，並將信箱移轉。

> [!NOTE]
> 雖然有點更複雜，您可能也同時移轉至 Exchange 2016 內部部署 Exchange 2010 伺服器將信箱遷移至 Office 365。

下列各節瀏覽更多詳細資料中的每個選項。

## <a name="migrate-to-office-365"></a>移轉至 Office 365

您的電子郵件移轉到 Office 365 是用來幫助您淘汰您的 Exchange 2010 部署您最佳且最簡單選項。 移轉到 Office 365，您可以讓單一一個躍點從舊的技術的 art 狀態功能，例如：

- 相容性功能，例如保留原則，就地與訴訟暫止，就地 eDiscovery，以及其他;
- Microsoft Teams;
- Power BI;
- 焦點收件匣;
- Delve 分析;

Office 365 也取得新功能和體驗第一個及您和您的使用者可以通常開始，立即使用它們。 除了新功能，您不需要擔心：

- 購買和維護硬體;
- 支付加熱和冷卻一部伺服器;
- 在安全性、 產品和時區的修正程式; 保持最新狀態
- 維護儲存空間和軟體，以支援規範需求;
- 升級至新版本的 Exchange-您隨時上最新版的 Office 365 中的 Exchange。

### <a name="how-should-i-migrate-to-office-365"></a>我應該在如何移轉到 Office 365？

依據您的組織，您必須將會協助您前往 Office 365 的一些選項。 在選擇遷移選項時，您需要考慮一些之類的基座或您要移動的信箱、 多久您想要移轉到最後一個，以及您是否需要您的內部部署安裝與 Office 365 期間之間的緊密整合數目移轉。 下表顯示您的遷移選項及將決定您要使用哪一種方法最重要因素。

| **遷移選項**     | **組織規模** | **Duration**        |
|--------------------------|-----------------------|---------------------|
| 完全移轉        | 少於 150 個基座  | 一週或更少      |
| 基本混合式移轉 | 少於 150 個基座  | 幾週或更少 |
| 完整的混合式移轉    | 超過 150 個基座   | 幾週或更多 |

下列各節提供這些方法的概觀。 請參閱[決定移轉路徑](https://support.office.com/en-us/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27)若要了解每一種方法的詳細資料。

### <a name="cutover-migration"></a>完全移轉

完全移轉是一，在預先選取的日期和時間，您將移轉所有您信箱、 通訊群組、 連絡人及等等，Office 365;當您已完成，您將會關閉您的內部部署 Exchange 伺服器並開始使用 Office 365 以獨佔模式。

沒有很多個信箱的小型組織想要快速 Office 365，而不想要處理的一些其他方法的複雜性，完全移轉方法是很好。 不過，有些也限制由於它應該完成一週或更少，而且它需要重新設定其 Outlook 設定檔的使用者。 雖然完全移轉可以處理最多 2000 個信箱，我們強烈建議您移轉 150 個信箱的最多使用此方法。 如果您嘗試移轉超過 150 個信箱，您可以執行超出您到達期限時之前, 傳送的所有信箱的時間，也人員可能會收到您 IT 支援淹沒了幫使用者重新設定 Outlook。

如果您考慮執行完全移轉，以下是一些事項需要考量，請考慮：

- Office 365 會需要連線到 Exchange 2010 伺服器使用 Outlook 無所不在 over TCP 連接埠 443;
- 所有內部部署信箱將會移至 Office 365;
- 您將需要內部部署系統管理員帳戶具有您的使用者信箱; 內容的讀取權限
- Exchange 2010 公認的網域，您想要用於 Office 365 需要新增為服務; 中的已驗證網域
- 之間的時間開始移轉，當您開始的完成階段時，Office 365 會定期同步處理的 Office 365 和內部部署信箱。 這可讓您完成移轉，而不用擔心會被遺留在您的內部部署信箱; 中的電子郵件
- 使用者會收到新的暫時密碼，他們將需要變更當他們登入其信箱的第一次; 其 Office 365 帳戶
- 您將需要包括 Exchange Online 移轉; 每個使用者信箱的 Office 365 授權
- 使用者必須設定每一部裝置上新的 Outlook 設定檔，並再次下載他們的電子郵件。 Outlook 會下載的電子郵件數量而異。 如需詳細資訊，看看[變更要離線保留多少郵件](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&rs=en-US&ad=US&fromAR=1)。

若要深入了解完全移轉，請看一下：

- [您需要了解電子郵件完全移轉到 Office 365](https://support.office.com/en-us/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)
- [執行完全移轉到 Office 365 的電子郵件](https://support.office.com/en-us/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)

### <a name="minimal-hybrid-migration"></a>基本混合式移轉

基本混合式或 express 中，移轉是其中一個必須在想要移轉到 Office 365，可以完成在幾週內移轉並不需要任何進階的混合式移轉功能，例如共用空閒/忙碌行事曆的幾個數百個信箱資訊。

基本混合式移轉是針對所須採取更多的時間，將其信箱移轉到 Office 365，但仍計畫，以完成移轉，在幾週內的組織很好。 您收到沒有許多不同的複雜度更進階的完整的混合式移轉的一些優點。 您可以控制多少，和哪些，信箱在指定的時間; 移轉Office 365 信箱將會建立使用使用者名稱和其內部部署帳戶; 的密碼與不同的是完全移轉，您的使用者不需要重新建立其 Outlook 設定檔。

如果您考慮執行最基本混合式移轉，以下是一些事項：

- 您必須執行一次性的目錄同步處理您的內部部署 Active Directory 伺服器與 Office 365; 之間
- 使用者無法登入其 Office 365 信箱使用相同的使用者名稱和他們已使用其信箱已移轉; 時的密碼
- 您將需要包括 Exchange Online 移轉; 每個使用者信箱的 Office 365 授權
- 使用者不需要設定新的 Outlook 設定檔，在大部分的裝置 （某些較舊的 Android 手機可能需要新的設定檔），且不需要重新下載他們的電子郵件。

若要深入了解基本混合式移轉，看看[使用基本混合式以快速移轉 Exchange 信箱移轉到 Office 365](https://support.office.com/article/Use-Minimal-Hybrid-to-quickly-migrate-Exchange-mailboxes-to-Office-365-fdecceed-0702-4af3-85be-f2a0013937ef)

### <a name="full-hybrid"></a>完整的混合式

完整的混合式移轉是一個您的組織有許多數百，最多數萬個的信箱，而且您想要將部分或全部移至 Office 365。 因為這些移轉會通常更長期，混合式移轉讓您能夠：

- 在 Office 365 中，顯示使用者的空閒/忙碌行事曆資訊在內部部署使用者，反之亦然。
- 請參閱統一的全域通訊清單包含收件者的內部部署和 Office 365;
- 檢視完整的 Outlook 收件者卡不論是否已經在內部或在 Office 365; 中的所有使用者
- 在內部部署 Exchange 伺服器與 Office 365 中，使用 TLS 和憑證; 之間的安全電子郵件通訊
- 將視為之間傳送的郵件在內部部署 Exchange 伺服器與 Office 365 為內部，讓他們能：
- 正確地評估並處理的目標; 的內部郵件的傳輸和符合性代理程式
- 略過反垃圾郵件篩選器。

完整的混合式移轉是最佳的組織而言，預計會停留在多個月或更多的混合式設定。 您會收到先前所述此區段中，加上目錄同步作業、 更佳的整合式的符合性功能及能夠將信箱移至，以及從 Office 365 的功能使用線上信箱移動。 Office 365 會變成內部部署組織的分機號碼。

如果您考慮執行完整的混合式移轉，以下是一些事項：

- 完整的混合式移轉不適合於所有類型的組織。 完整的混合式移轉的複雜度，因為小於幾個數百個信箱的組織通常看不到 justify 人力和一個設定所需的成本效益。 如果這聽您的組織時，我們強烈建議您改為; 考慮完全或基本混合式移轉
- 您需要設定目錄同步處理您的內部部署 Active Directory 伺服器與 Office 365; 之間使用 Azure Active Directory Connect (AADConnect)
- 使用者無法登入其 Office 365 信箱使用相同的使用者名稱和密碼他們使用當他們登入區域網路 （需要 Azure Active Directory Connect 搭配密碼同步處理和/或 Active Directory Federation Services）;
- 您將需要包括 Exchange Online 移轉; 每個使用者信箱的 Office 365 授權
- 使用者不需要設定新的 Outlook 設定檔，在大部分的裝置 （某些較舊的 Android 手機可能需要新的設定檔），且不需要重新下載他們的電子郵件。

> [!IMPORTANT]
> 如果您的組織選擇將信箱移轉到 Office 365，但要繼續從內部部署 Active Directory 管理使用者帳戶就地保留 DirSync 或 Azure AD Connect，您需要保留至少一個 Exchange 伺服器內部部署。 如果移除最後一部 Exchange 伺服器，您無法在 Exchange Online 中的 Exchange 收件者進行變更。 這是授權的因為來源仍會保留在內部部署 Active Directory 中，需要有進行的變更。

如果適合您的完整的混合式移轉聲音，看看下列資源以協助您進行移轉：

- [Exchange 部署助理](https://aka.ms/exdeploy)
- [Exchange Server 混合式部署](https://technet.microsoft.com/en-us/library/jj200581%28v=exchg.150%29.aspx)
- [混合組態精靈](https://technet.microsoft.com/en-us/library/hh529921%28v=exchg.150%29.aspx)
- [混合組態精靈常見問題集](https://technet.microsoft.com/en-us/library/mt488940%28v=exchg.150%29.aspx)
- [混合式部署必要條件](https://technet.microsoft.com/en-us/library/hh534377%28v=exchg.150%29.aspx)

## <a name="upgrade-to-a-newer-version-of-exchange-server-on-premises"></a>升級至較新版本的 Exchange Server 內部部署

雖然我們強烈相信您可以透過完全移轉至 Office 365 來達到最佳的值與使用者經驗，我們也了解某些組織需要保留部分 Exchange 伺服器內部部署。 這可能因法規需求，以保證資料不會儲存在位於另一個國家/地區中，資料中心或它可能是因為您有唯一的設定] 或 [無法在雲端中，符合的需求，或可能只是您需要 Exchange管理雲端信箱，因為您仍然可以使用 Active Directory 的內部。 在任何情況下為您選擇或需要保留 Exchange 內部部署，您應該確定您的 Exchange 2010 環境升級至最少的 Exchange 2013 或 Exchange 2016 和 Exchange 2010 移除支援的結束日期之前。

為最佳使用體驗，我們建議您將剩餘的內部部署環境升級為 Exchange 2016。 您不需要安裝 Exchange Server 2013 中，如果您想要直接從 Exchange Server 2010 移至 Exchange Server 2016。

Exchange 2016 包含所有的功能和隨附的 Exchange，先前版本的進步，其最符合隨附於 Office 365 的體驗 （雖然某些功能只適用於 Office 365）。 取出只是一些您已被錯過的事項：

| **Exchange 版本**                     | **功能**                                                                                                                                                                                                                                         |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Exchange 2013                            | 將伺服器角色的數量減為三個的簡化的架構 (信箱、 用戶端存取，Edge Transport)                                                                                                                                        |
|                                          | 資料外洩防護原則 (DLP) 協助保護敏感資訊洩漏                                                                                                                                                                |
|                                          | 大幅改善的 Outlook Web App 功能                                                                                                                                                                                                    |
| Exchange 2016                            | *從 Exchange 2013 的功能和...]*                                                                                                                                                                                                                   |
|                                          | 進一步簡化的伺服器角色，以只是 Mailbox 和 Edge Transport                                                                                                                                                                                   |
|                                          | 與 SharePoint 整合以及改善的 DLP                                                                                                                                                                                                  |
|                                          | 改善的資料庫復原                                                                                                                                                                                                                         |
|                                          | 線上文件共同作業                                                                                                                                                                                                                        |

| **考量**                        | **更多資訊**                                                                                                                                                                                                                                        |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 支援日期的結尾                     | 類似 Exchange 2010 中，每個 Exchange 版本會有其專屬結尾支援日期：                                                                                                                                                                        |
|                                          | **Exchange 2013**年 4 月 2023                                                                                                                                                                                                                       |
|                                          | **Exchange 2016**年 10 月 2025                                                                                                                                                                                                                     |
|                                          | 稍早的結尾支援日期、 更快您需要執行其他的移轉。 年 4 月 2023年會比您想像的更接近 ！                                                                                                                 |
| 移轉路徑至 Exchange 2013 或 2016  | 不論您選擇的 Exchange 2013 或 Exchange 2016 的較新版本從 Exchange 2010 的移轉路徑都是一樣的：                                                                                                                              |
|                                          | 安裝 Exchange 2013 或 2016年到您現有的 Exchange 2010 組織移動服務和其他基礎結構，以 Exchange 2013 或 2016年移動信箱和公用資料夾移轉至 Exchange 2013 或 2016年解除委任剩餘的 Exchange 2010 伺服器  |
| 版本共存                      | 當移轉至 Exchange 2013 或 Exchange 2016，您可以在現有 Exchange 2010 組織中安裝任一版本。 這可讓您安裝一或多個 Exchange 2013 或 Exchange 2016 伺服器，以及執行移轉。             |
| 伺服器硬體                          | 從 Exchange 2010，已變更伺服器的硬體需求。 您需要確定您要使用的硬體相容。 您可以找到進一步了解如何針對以下每個版本的硬體需求：                                      |
|                                          | [Exchange 2016 系統需求](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx)                                                                                                                                      |
|                                          | [Exchange 2013 系統需求](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx)                                                                                                                                      |
|                                          | 您會發現的顯著的改進功能 Exchange 效能和運算動力與較新的伺服器中的儲存容量，您可能需要較少的伺服器，以支援相同的信箱數目。                       |
| 作業系統版本                 | 每個版本的最小支援的作業系統版本︰                                                                                                                                                                                |
|                                          | **Exchange 2016**Windows Server 2012                                                                                                                                                                                                                |
|                                          | **Exchange 2013**Windows Server 2008 R2 SP1                                                                                                                                                                                                         |
|                                          | 您可以在[Exchange 支援性一覽表](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx)尋找作業系統支援的詳細資訊。                                                                        |
| Active Directory 樹系功能等級 | 最小支援 Active Directory 樹系功能等級每個版本︰                                                                                                                                                                |
|                                          | **Exchange 2016**Windows Server 2008 R2 SP1                                                                                                                                                                                                         |
|                                          | **Exchange 2013**Windows Server 2003                                                                                                                                                                                                                |
|                                          | 您可以在[Exchange 支援性一覽表](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx)尋找樹系功能層級支援的詳細資訊。                                                                 |
| Office 用戶端版本                   | 每個版本的最小支援的 Office 用戶端版本︰                                                                                                                                                                                   |
|                                          | **Exchange 2016**Office 2010 （含最新更新）                                                                                                                                                                                              |
|                                          | **Exchange 2013**Office 2007 SP3                                                                                                                                                                                                                    |
|                                          | 您可以在[Exchange 支援性一覽表](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx)尋找 Office 用戶端支援的詳細資訊。                                                                           |

您可以使用下列資源以協助您進行移轉：

- [Exchange 部署助理](https://aka.ms/exdeploy)
- Exchange [2016年](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.160%29.aspx)、 [2013年](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.150%29.aspx)的 active Directory 架構變更
- Exchange [2016年](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx)、 [2013年](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx)系統需求
- Exchange [2016年](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.160%29.aspx)、 [2013年](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.150%29.aspx)的必要條件

## <a name="what-if-i-need-help"></a>如果我需要協助嗎？

如果您要移轉到 Office 365，您可能可以使用我們的 Microsoft FastTrack 服務。 FastTrack 提供最佳做法、 工具和資源，以便您移轉到 Office 365 盡可能完美。 最棒的您必須實際支援工程師將引導您完成移轉，從規劃和設計一直到您的最後一個信箱移轉。 如果您想要深入了解 FastTrack，看看[Microsoft FastTrack](https://fasttrack.microsoft.com/)。

如果您遇到任何問題期間移轉到 Office 365，而且您不使用 FastTrack 或較新版的 Exchange 伺服器的移轉，我們隨時為您效勞。 以下是一些您可以使用的資源：

- [技術社群](https://social.technet.microsoft.com/Forums/office/en-US/home?category=exchangeserver)
- [客戶支援](https://support.microsoft.com/en-us/gp/support-options-for-business)

## <a name="related-topics"></a>相關主題

[資源可以幫助您升級從 Office 2010 伺服器和用戶端](https://docs.microsoft.com/en-us/office365/enterprise/upgrade-from-office-2010-servers-and-products)

[Office 退休群組 （Microsoft 技術社群）](https://go.microsoft.com/fwlink/?linkid=842065)
