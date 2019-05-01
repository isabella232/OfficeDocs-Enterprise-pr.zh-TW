---
title: Exchange 2007 終止支援藍圖
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.assetid: c3024358-326b-404e-9fe6-b618e54d977d
description: 於 2017 年 4 月 11 日，Exchange Server 2007 會達到終止支援。 如果您已經尚未開始從 Exchange 2007 至 Office 365 或 Exchange 2016 移轉，現在是以開始您規劃的時間。
ms.openlocfilehash: 674de8904d03e024a8a75b945b5ef94319214f92
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33488469"
---
# <a name="exchange-2007-end-of-support-roadmap"></a>Exchange 2007 終止支援藍圖

於**2017 年 4 月 11 日**，Exchange Server 2007 會達到終止支援。 如果您已經尚未開始從 Exchange 2007 至 Office 365 或 Exchange 2016 移轉，現在是以開始您規劃的時間。 
  
## <a name="what-does-end-of-support-mean"></a>支援平均數的哪些並結束？

Exchange 伺服器，例如幾乎所有的 Microsoft 產品中，有支援週期，我們會提供新功能、 錯誤修正程式、 安全性修正程式、 等等。 此生命週期通常會持續 10 年起的產品的初始版本，與此生命週期結束稱為 「 支援的產品的結尾。 Exchange 2007 達到其終止於 2017 年 4 月 11 日，支援，因此不再提供 Microsoft:
  
- 技術支援問題，可能會發生;
    
- 錯誤修正問題，會發現及，可能會影響 exchange 的穩定性與可用性的伺服器;
    
- 安全性問題修正，會發現及，可能會讓伺服器受到安全性弱點; 的弱點
    
- 時間的時區更新。
    
Exchange 2007 安裝會繼續執行此日期之後。 不過，由於上述的變更，我們強烈建議您儘速移轉從 Exchange 2007。
  
如需接近終止支援的 Office 2007 伺服器的詳細資訊，請參閱 <<c0>規劃從 Office 2007 伺服器和產品升級。
  
## <a name="what-are-my-options"></a>我的選項為何？

現在，Exchange 2007 已到達其結束位置的支援，我們強烈建議您瀏覽您的選項，並準備移轉計劃。 您可以：
  
- 移轉至 Office 365 使用完全移轉、 分段，或混合式移轉;
    
- 將 Exchange 2007 伺服器遷移至較新版的 Exchange 內部部署伺服器上。
    
下列各節瀏覽更多詳細資料中的每個選項。
  
### <a name="migrate-to-office-365"></a>移轉至 Office 365

您的電子郵件移轉到 Office 365 是用來幫助您淘汰您的 Exchange 2007 部署您最佳且最簡單選項。 移轉至 Office 365 中，可以讓單一一個躍點從 10-年-舊技術先進的功能，例如：
  
- 相容性功能，例如保留原則，就地與訴訟暫止，就地 eDiscovery，以及其他;
    
- Office 365 群組;
    
- 焦點收件匣;
    
- Delve 分析;
    
- 以程式設計方式存取電子郵件、 行事曆、 連絡人、 等等的 REST Api。
    
Office 365 也取得新功能和體驗第一個及您和您的使用者可以通常開始，立即使用它們。 除了新功能，您不需要擔心：
  
- 購買和維護硬體;
    
- 支付加熱和冷卻一部伺服器;
    
- 在安全性、 產品和時區的修正程式; 保持最新狀態
    
- 維護儲存空間和軟體，以支援規範需求;
    
- 升級至新版本的 Exchange-您隨時上最新版的 Office 365 中的 Exchange。
    
#### <a name="how-should-i-migrate-to-office-365"></a>我應該在如何移轉到 Office 365？

依據您的組織，您必須將會協助您前往 Office 365 的一些選項。 在選擇遷移選項時，您需要考慮一些之類的基座或您要移動的信箱、 多久您想要移轉到最後一個，以及您是否需要您的內部部署安裝與 Office 365 期間之間的緊密整合數目移轉。 下表顯示您的遷移選項及將決定您要使用哪一種方法最重要因素。
  
| |
|**遷移選項**|**組織規模**|**Duration**|
|:-----|:-----|:-----|
|完全移轉  <br/> |少於 150 個基座  <br/> |一週或更少  <br/> |
|分段移轉  <br/> |超過 150 個基座  <br/> |幾週  <br/> |
|完整的混合式移轉  <br/> |數百到數千個基座  <br/> |幾個月或更多  <br/> |
   
下列各節提供這些方法的概觀。 請參閱[決定移轉路徑](https://support.office.com/en-us/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27)若要了解每一種方法的詳細資料。 
  
#### <a name="cutover-migration"></a>完全移轉

完全移轉是一，在預先選取的日期和時間，您將移轉所有您信箱、 通訊群組、 連絡人及等等，Office 365;當您已完成，您將會關閉您的內部部署 Exchange 伺服器並開始使用 Office 365 以獨佔模式。
  
沒有很多個信箱的小型組織想要快速 Office 365，而不想要處理的一些其他方法的複雜性，完全移轉方法是很好。 不過，有些也限制由於它應該完成一週或更少，而且它需要重新設定其 Outlook 設定檔的使用者。 雖然完全移轉可以處理最多 2000 個信箱，我們強烈建議您移轉 150 個信箱的最多使用此方法。 如果您嘗試移轉超過 150 個信箱，您可以執行超出您到達期限時之前, 傳送的所有信箱的時間，也人員可能會收到您 IT 支援淹沒了幫使用者重新設定 Outlook。
  
如果您考慮執行完全移轉，以下是一些事項需要考量，請考慮：
  
- Office 365 會需要連線到 Exchange 2007 伺服器從 TCP 通訊埠 443; 使用 Outlook 無所不在
    
- 所有內部部署信箱將會移至 Office 365;
    
- 您將需要內部部署系統管理員帳戶具有您的使用者信箱; 內容的讀取權限
    
- Exchange 2007 公認的網域，您想要用於 Office 365 需要新增為服務; 中的已驗證網域
    
- 之間的時間開始移轉，當您開始的完成階段時，Office 365 會定期同步處理的 Office 365 和內部部署信箱。 這可讓您完成移轉，而不用擔心會被遺留在您的內部部署信箱; 中的電子郵件
    
- 使用者會收到新的暫時密碼，他們將需要變更當他們登入其信箱的第一次; 其 Office 365 帳戶
    
- 您將需要包括 Exchange Online 移轉; 每個使用者信箱的 Office 365 授權
    
- 使用者必須設定每一部裝置上新的 Outlook 設定檔，並再次下載他們的電子郵件。 Outlook 會下載的電子郵件數量而異。 如需詳細資訊，看看[變更要離線保留多少郵件](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1)。
    
若要深入了解完全移轉，請看一下：
  
- [您需要了解電子郵件完全移轉到 Office 365](https://support.office.com/en-us/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)
    
- [執行完全移轉到 Office 365 的電子郵件](https://support.office.com/en-us/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)
    
#### <a name="staged-migration"></a>分段移轉

分段的移轉是其中一個其中您有幾個數百或少數幾個數千個信箱您想要移轉到 Office 365、 所須採取一週或更多] 來完成移轉，而不需要任何進階的混合式移轉功能喜歡共用的空閒/忙碌行事曆資訊rmation。
  
分段的移轉是針對所須採取更多時間來將其信箱移轉到 Office 365，但仍要在完成移轉，在幾週內的組織很好。 您可以 「 批次遷移信箱 」 可讓您以控制數目，以及哪些、 信箱移轉在特定時間。 您可能批次的同一個部門中的使用者信箱，例如，若要確定他們正在所有移動在同一時間。 或者，您可能會使行政人員信箱保留直到上次批次。 為進行完全移轉，您的使用者必須重新建立其 Outlook 設定檔。
  
如果您考慮執行分段的移轉，以下是一些事項：
  
- Office 365 會需要連線到 Exchange 2007 伺服器從 TCP 通訊埠 443; 使用 Outlook 無所不在
    
- 您將需要內部部署系統管理員帳戶具有您的使用者信箱; 內容的讀取權限
    
- Exchange 2007 公認的網域，您想要用於 Office 365 需要新增為服務; 中的已驗證網域
    
- 您需要建立 CSV 檔案的完整名稱和電子郵件地址您想要移轉批次中每個信箱。 您也需要包含您要移轉，每個信箱的新密碼，並再將其密碼傳送給每位使用者。 將會提示使用者登入其新的 Office 365 信箱; 第一次變更密碼
    
- 之間的時間開始移轉批次，當您開始的完成階段時，Office 365 會定期同步處理的批次中包含的 Office 365 和內部部署信箱。 這可讓您完成移轉，而不用擔心會被遺留在您的內部部署信箱; 中的電子郵件
    
- 使用者會收到新的暫時密碼，他們將需要變更第一次; 登入其信箱時其 Office 365 帳戶
    
- 您將需要包括 Exchange Online 移轉; 每個使用者信箱的 Office 365 授權
    
- 使用者必須設定每一部裝置上新的 Outlook 設定檔，並再次下載他們的電子郵件。 Outlook 會下載的電子郵件數量而異。 如需詳細資訊，看看[變更要離線保留多少郵件](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1)。
    
若要深入了解分段移轉，請看一下：
  
- [將電子郵件分段移轉到 Office 365 所需注意的事項](https://support.office.com/en-us/article/What-you-need-to-know-about-a-staged-email-migration-to-Office-365-7e2c82be-5f3d-4e36-bc6b-e5b4d411e207)
    
- [執行電子郵件到 Office 365 的分段的移轉](https://support.office.com/en-us/article/Perform-a-staged-migration-of-email-to-Office-365-83bc0b69-de47-4cc4-a57d-47e478e4894e)
    
#### <a name="full-hybrid"></a>完整的混合式

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
  
- 完整的混合式移轉不適合於所有類型的組織。 完整的混合式移轉的複雜度，因為小於幾個數百個信箱的組織通常看不到 justify 人力和一個設定所需的成本效益。 如果很像是您的組織，我們強烈建議您改為; 考慮完全或分段移轉
    
- 您需要部署 Exchange 2007 組織做為 「 混合式伺服器 」 中的至少一部 Exchange 2013 伺服器。 此伺服器將會與 Office 365 通訊代表 Exchange 2007 伺服器;
    
- Office 365 會需要連線至 「 混合式伺服器 」 over TCP 連接埠 443; 使用 Outlook 無所不在
    
- 您需要設定目錄同步處理您的內部部署 Active Directory 伺服器與 Office 365; 之間使用 Azure Active Directory Connect (AADConnect)
    
- 使用者無法登入其 Office 365 信箱使用相同的使用者名稱和密碼他們使用當他們登入區域網路 （需要 Azure Active Directory Connect 搭配密碼同步處理和/或 Active Directory Federation Services）;
    
- 您將需要包括 Exchange Online 移轉; 每個使用者信箱的 Office 365 授權
    
- 使用者不需要設定新的 Outlook 設定檔，在大部分的裝置 （某些較舊的 Android 手機可能需要新的設定檔），且不需要重新下載他們的電子郵件。
    
如果適合您的完整的混合式移轉聲音，看看下列資源以協助您進行移轉：
  
- [Exchange 部署助理](https://aka.ms/exdeploy)
    
- [Exchange Server 混合式部署](https://technet.microsoft.com/en-us/library/jj200581%28v=exchg.150%29.aspx)
    
- [混合組態精靈](https://technet.microsoft.com/en-us/library/hh529921%28v=exchg.150%29.aspx)
    
- [混合組態精靈常見問題集](https://technet.microsoft.com/en-us/library/mt488940%28v=exchg.150%29.aspx)
    
- [混合式部署必要條件](https://technet.microsoft.com/en-us/library/hh534377%28v=exchg.150%29.aspx)
    
### <a name="migrate-to-a-newer-version-of-exchange-server"></a>遷移至較新版本的 Exchange 伺服器

雖然我們強烈相信您可以透過移轉至 Office 365 來達到最佳的值與使用者經驗，我們也了解某些組織需要保留其電子郵件的內部。 這可能因法規需求，以保證資料不會儲存在資料中心位於另一個國家/地區，依此類推。 如果您選擇要保留電子郵件在內部，您可以將您的 Exchange 2007 環境移轉至 Exchange 2010、 Exchange 2013 或 Exchange 2016。
  
我們建議您移轉到 Exchange 2016，如果您無法移轉至 Office 365。 Exchange 2016 包含所有的功能和隨附的 Exchange，先前版本的進步，其最符合隨附於 Office 365 的體驗 （雖然某些功能只適用於 Office 365）。 取出只是一些您已被錯過的事項：
  
|**Exchange 版本**|**功能**|
|:-----|:-----|
|Exchange 2010  <br/> | 角色型存取控制 （沒有 Acl 的權限）  <br/>  Outlook Web Access 信箱原則  <br/>  共用空閒/忙碌和委派組織之間的行事曆的能力  <br/> |
|Exchange 2013  <br/> | *從 Exchange 2010 的功能和...]*  <br/>  將伺服器角色的數量減為三個的簡化的架構 (信箱、 用戶端存取，Edge Transport)  <br/>  資料外洩防護原則 (DLP) 協助保護敏感資訊洩漏  <br/>  大幅改善的 Outlook Web App 功能  <br/> |
|Exchange 2016  <br/> | *從 Exchange 2013 的功能和...]*  <br/>  進一步簡化的伺服器角色，以只是 Mailbox 和 Edge Transport  <br/>  與 SharePoint 整合以及改善的 DLP  <br/>  改善的資料庫復原  <br/>  線上文件共同作業  <br/> |
   
#### <a name="which-version-should-i-migrate-to"></a>若要應該移轉哪些版本？

我們建議您最初假設您將會遷移至 Exchange 2016。 若要確認您的假設或若要排除 Exchange 2016，然後使用下列資訊。 如果您無法移轉至 Exchange 2016，或另一個原因，執行相同程序與 Exchange 2013 中，依此類推。
  
|**考量**|**更多資訊**|
|:-----|:-----|
|支援日期的結尾  <br/> | Exchange 2007，例如每個 Exchange 版本會有其專屬結尾支援日期：  <br/> **Exchange 2010**年 1 月 2020  <br/> **Exchange 2013**年 4 月 2023  <br/> **Exchange 2016**年 10 月 2025  <br/>  稍早的結尾支援日期、 更快您需要執行其他的移轉。 2020 年 1 月會比您想像的更接近 ！  <br/> |
|Exchange 2010 和 2013年的移轉路徑  <br/> |以下是移轉至 Exchange 2010 或 Exchange 2013 的一般階段：  <br/> 將 Exchange 2010 或 2013年安裝到現有的 Exchange 2007 組織移動服務和其他基礎結構，以 Exchange 2010 或 2013年移動信箱和公用資料夾移轉至 Exchange 2010 或 2013年解除委任剩餘的 Exchange 2007 伺服器 |
|Exchange 2016 移轉路徑  <br/> |以下是移轉至 Exchange 2016 的一般階段：  <br/> Exchange 2013 安裝到現有的 Exchange 2007 組織移動服務和其他基礎結構，以 Exchange 2013 移動信箱和公用資料夾移轉至 Exchange 2013 解除委任剩餘到您現有的 Exchange 2007 伺服器安裝 Exchange 2016Exchange 2013 組織。 將信箱、 公用資料夾、 服務和其他基礎結構移至 Exchange 2016 （順序不會影響）。 解除委任剩餘的 Exchange 2013 伺服器 > [!NOTE]> 從 Exchange 2013 移轉至 Exchange 2016 很簡單。 這兩個版本具有幾乎相同的硬體需求。 此功能及這些版本會所以相容性，表示您可以重新建立您購買的 Exchange 2013 伺服器，並在其上安裝 Exchange 2016 的事實。 並與線上信箱移動，大部分的使用者會永遠不會注意到他們的信箱正在移出伺服器，然後重新開機後您已在 Exchange 2016 以重新建置。           |
|版本共存  <br/> | 當移轉至：  <br/> **Exchange 2016**無法在包含 Exchange 2007 伺服器的組織中安裝 Exchange 2016。 您第一次需要將移轉至 Exchange 2010 或 2013 （我們強烈建議 Exchange 2013）、 移除所有 Exchange 2007 伺服器，並再移轉到 Exchange 2016。  <br/> **Exchange 2010 或 Exchange 2013**您可以在現有 Exchange 2007 組織中安裝 Exchange 2010 或 Exchange 2013。 這可讓您安裝一或多個 Exchange 2010 或 2013年伺服器，並執行移轉。  <br/> |
|伺服器硬體  <br/> | 從 Exchange 2007，已變更伺服器的硬體需求。 您需要確定您要使用的硬體相容。 您可以找到進一步了解如何針對以下每個版本的硬體需求：  <br/> [Exchange 2016 系統需求](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx) <br/> [Exchange 2013 系統需求](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx) <br/> [Exchange 2010 系統需求](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.141%29.aspx) <br/>  您會發現的顯著的改進功能 Exchange 效能和運算動力與較新的伺服器中的儲存容量，您可能需要較少的伺服器，以支援相同的信箱數目。  <br/> |
|作業系統版本  <br/> | 每個版本的最小支援的作業系統版本︰  <br/> **Exchange 2016**Windows Server 2012  <br/> **Exchange 2013**Windows Server 2008 R2 SP1  <br/> **Exchange 2010**Windows Server 2008 SP2  <br/>  您可以在[Exchange 支援性一覽表](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx)尋找作業系統支援的詳細資訊。  <br/> |
|Active Directory 樹系功能等級  <br/> | 最小支援 Active Directory 樹系功能等級每個版本︰  <br/> **Exchange 2016**Windows Server 2008 R2 SP1  <br/> **Exchange 2013**Windows Server 2003  <br/> **Exchange 2010**Windows Server 2003  <br/>  您可以在[Exchange 支援性一覽表](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx)尋找樹系功能層級支援的詳細資訊。  <br/> |
|Office 用戶端版本  <br/> | 每個版本的最小支援的 Office 用戶端版本︰  <br/> **Exchange 2016**Office 2010 （含最新更新）  <br/> **Exchange 2013**Office 2007 SP3  <br/> **Exchange 2010**Office 2003  <br/>  您可以在[Exchange 支援性一覽表](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx)尋找 Office 用戶端支援的詳細資訊。  <br/> |
   
#### <a name="how-do-i-migrate"></a>我該如何移轉？

如果您已決定您想將您的電子郵件的內部，您可以使用下列資源以協助您進行移轉：
  
- [Exchange 部署助理](https://aka.ms/exdeploy)
    
- Exchange [2016年](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.160%29.aspx)、 [2013年](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.150%29.aspx)、 [2010年](https://www.microsoft.com/download/en/details.aspx?displaylang=en&amp;id=5401)的 active Directory 架構變更
    
- Exchange [2016年](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx)、 [2013年](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx)、 [2010年](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.141%29.aspx)系統需求
    
- Exchange [2016年](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.160%29.aspx)、 [2013年](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.150%29.aspx)、 [2010年](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.141%29.aspx)的必要條件
    
## <a name="what-if-i-need-help"></a>如果我需要協助嗎？

如果您要移轉到 Office 365，您可能可以使用我們的 Microsoft FastTrack 服務。 FastTrack 提供最佳做法、 工具和資源，以便您移轉到 Office 365 盡可能完美。 最棒的您必須實際支援工程師將引導您完成移轉，從規劃和設計一直到您的最後一個信箱移轉。 如果您想要深入了解 FastTrack，看看[Microsoft FastTrack](https://fasttrack.microsoft.com/)。
  
如果您遇到任何問題期間移轉到 Office 365，而且您不使用 FastTrack 或較新版的 Exchange 伺服器的移轉，我們隨時為您效勞。 以下是一些您可以使用的資源：
  
- [技術社群](https://social.technet.microsoft.com/Forums/office/en-US/home?category=exchangeserver)
    
- [客戶支援](https://support.microsoft.com/en-us/gp/support-options-for-business)
    
## <a name="related-topics"></a>相關主題

[資源可以幫助您升級您的 Office 2007 伺服器和用戶端](upgrade-from-office-2007-servers-and-products.md)
  
[Office 退休群組 （Microsoft 技術社群）](https://go.microsoft.com/fwlink/?linkid=842065)
  

