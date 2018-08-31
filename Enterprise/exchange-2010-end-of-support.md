---
title: Exchange 2010 結尾的支援藍圖
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.assetid: e150e7b9-c432-4c8d-a0ae-c11847129a7d
description: Exchange 2010 已接近支援結束。用於此規劃藍圖做為指南準備升級到 Exchange Online 或 Exchange Server 內部部署的較新版本。
ms.openlocfilehash: e655edcc38723acd622fc6abc62a00d3f3e36738
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915188"
---
# <a name="exchange-2010-end-of-support-roadmap"></a>Exchange 2010 結尾的支援藍圖

在**2020 年 1 月 14、**、 Exchange Server 2010 會連絡支援結束。如果您已經尚未開始移轉至 Office 365 的 Exchange 2010 或 Exchange 2016、 現在是以啟動您進行規劃的時間。 
  
## <a name="what-does-end-of-support-mean"></a>支援平均數何種實務結尾？

Exchange Server 幾乎所有的 Microsoft 產品，例如有支援週期的期間我們提供的新功能、 修正錯誤、 安全性修正程式等等。此技術支援週期通常是一個工期 10 年度從產品的初始版本，日期的此技術支援週期的結尾就所謂的產品支援結束。Exchange 2010 達到支援 2020 年 1 月 14、 在其結束時將不再提供 Microsoft：
  
- 技術支援問題，可能會發生;
    
- 錯誤修正的問題會發現及，可能會影響穩定性及可用性的伺服器;
    
- 安全性弱點的探索和可能會提出伺服器安全性缺口; 容易受到的修正
    
- 時間的時區更新。
    
Exchange 2010 的安裝會繼續執行這個日期之後。但是，由於上述變更，我們強烈建議您盡移轉從 Exchange 2010。
  
如需接近支援結束的 Office 2010 伺服器的詳細資訊，請參閱[資源以協助您升級從 Office 2010 伺服器和用戶端](upgrade-from-office-2010-servers-and-products.md)。
  
## <a name="what-are-my-options"></a>我的選項為何？

即將達到其結尾支援 Exchange 2010，這是更好的時間來探索您的選項和準備的移轉規劃。您可以：
  
- 移轉至 Office 365 使用轉換、 express 或混合式遷移; 
    
- 將 Exchange 2010 伺服器移轉至新版 Exchange 內部部署伺服器上。
    
下列各節探索更詳細地每個選項。
  
### <a name="migrate-to-office-365"></a>移轉至 Office 365

將您的電子郵件移轉至 Office 365 是您最佳與最簡單的選項可幫助您淘汰 Exchange 2010 部署。使用 Office 365 遷移，可以進行單一一個躍點從舊的技術先進的功能類似：
  
- 規範功能保留原則，就地與訴訟暫止狀態，例如就地 eDiscovery 及多;
    
- Microsoft 小組;
    
- Power BI;
    
- 具有焦點的收件匣;
    
- 探索分析;
    
- 以程式設計方式存取電子郵件、 行事曆、 連絡人、 等等的 REST Api。
    
Office 365 也會取得新功能與經驗第一個和您和使用者可以通常是啟動立即使用這些。除了新功能，您將不會有擔心：
  
- 購買和維護硬體;
    
- 支付加熱及冷卻一部伺服器 ；
    
- 在安全性、 產品及時間的時區修正; 保持最新
    
- 維護儲存空間和軟體以支援規範需求 ；
    
- 升級至新版本的 Exchange-你一律在最新版的 Office 365 中的 Exchange。
    
#### <a name="how-should-i-migrate-to-office-365"></a>我應該在如何移轉至 Office 365？

根據您的組織，您必須將協助您做好至 Office 365 的一些選項。選擇移轉選項、 時需要考慮一些事項 like 基座或您要移動的信箱、 長您想要移轉至最後一個，以及您是否需要內部部署安裝及期間的 Office 365 之間順利整合的數目移轉。下表顯示您的移轉選項和將決定您要使用哪一種方法最重要因素。
  
|**遷移選項**|**組織大小**|**期間**|
|:-----|:-----|:-----|
|轉換移轉  <br/> |少於 150 基座  <br/> |一週或更少  <br/> |
|Express 移轉  <br/> |少於 150 基座  <br/> |幾週或更少  <br/> |
|完整的混合式遷移  <br/> |多個 150 基座  <br/> |幾週或更多  <br/> |
   
下列各節提供這些方法的概觀。取出[決定移轉路徑](https://support.office.com/en-us/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27)以了解各方法的詳細資料。 
  
#### <a name="cutover-migration"></a>轉換移轉

轉換遷移是其中一個位置，在預先選取的日期和時間，您將移轉所有您的信箱、 通訊群組、 連絡人、 等等，至 Office 365;當您已完成，您將會關閉您的內部部署 Exchange 伺服器並開始使用 Office 365 以獨佔模式。
  
一次完成式遷移方法是更好沒有非常許多信箱的小型組織想要快速地取得 Office 365 和不想要處理一些其他方法的複雜性。不過它的也有點受限於因為它應該完成中一週或更少，且因為它需要重新設定其 Outlook 設定檔的使用者。雖然次完成式遷移可以處理最多 2000 個信箱，我們強烈建議您藉由這個方法移轉的 150 信箱的最大值。如果您嘗試將多個 150 信箱遷移、 無法用盡傳輸所有的信箱在到達期限時之前, 的時間和人員可能會得到您 IT 支援被協助使用者重新設定 Outlook。
  
如果您考慮進行一次完成式遷移，以下是一些考量的事項，請考慮：
  
- Office 365 必須連線至 Exchange 2010 伺服器使用 「 Outlook 無所不在 」 over TCP 連接埠 443;
    
- 所有的內部部署信箱要移至 Office 365;
    
- 您將需要內部部署管理員帳戶具有您的使用者信箱 ； 的內容的讀取權限
    
- Exchange 2010 公認的網域想要使用的 Office 365 需要新增為服務 ； 中已驗證網域
    
- 之間的時間開始移轉和時開始完成階段、 Office 365 會定期同步處理 Office 365 與內部部署信箱。這可讓您完成移轉而不用擔心正在留在您的內部部署信箱 ； 電子郵件
    
- 使用者會收到新暫時他們將需要變更登入其信箱的第一次 ； 其 Office 365 帳戶密碼
    
- 您將需要包含 Exchange Online 移轉 ； 每個使用者信箱的 Office 365 授權
    
- 使用者必須設定新的 Outlook 設定檔上每個裝置，然後再下載的電子郵件。將下載 Outlook 的電子郵件數量可能會有所不同。如需詳細資訊，請查看[變更多少郵件保留離線](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1)。
    
若要深入了解完全移轉，請查看：
  
- [您需要了解轉換電子郵件移轉至 Office 365](https://support.office.com/en-us/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)
    
- [執行轉換遷移至 Office 365 的電子郵件](https://support.office.com/en-us/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)
    
#### <a name="express-migration"></a>Express 移轉

Express 移轉是其中包含您要移轉至 Office 365、 可以完成幾個星期內移轉並不需要任何進階的混合式遷移功能，例如共用空閒/忙碌行事曆資訊的一些好幾百種信箱。
  
Express 移轉是更好的組織需要花更多時間來將其信箱遷移至 Office 365 中，但仍要在完成幾個星期內移轉。您要取得沒有許多不同的複雜度更進階的完整的混合式移轉的一些優點。您可以控制多少，且哪一個、 信箱在指定的時間 ； 移轉Office 365 信箱將建立的使用者名稱與密碼的內部部署帳戶 ；與不同轉換遷移使用者不需要重新建立其 Outlook 設定檔。
  
如果您需執行分段的遷移的想法，以下是要考慮的一些事項：
  
- Office 365 必須連線至 Exchange 2010 伺服器使用 「 Outlook 無所不在 」 over TCP 連接埠 443;
    
- 您需要執行一次性目錄之間同步處理您的內部部署 Active Directory 伺服器和 Office 365;
    
- 使用者將能夠登入 Office 365 信箱使用相同的使用者名稱和密碼時使用他們的信箱已移轉;
    
- 您將需要包含 Exchange Online 移轉 ； 每個使用者信箱的 Office 365 授權
    
- 使用者不需要設定新的 Outlook 設定檔在大部分的裝置 （一些較舊的 Android 電話可能會需要新的設定檔） 並不需要重新下載電子郵件。
    
若要深入了解分段遷移，仔細[快速移轉 Exchange 信箱移轉至 Office 365 使用最少的混合式](https://support.office.com/article/Use-Minimal-Hybrid-to-quickly-migrate-Exchange-mailboxes-to-Office-365-fdecceed-0702-4af3-85be-f2a0013937ef)
  
#### <a name="full-hybrid"></a>完整的混合式

完整的混合式遷移是一個其中您的組織有許多百，最多個數萬個、 信箱，而您想要移至 Office 365 的部分或所有這些。因為這些移轉通常長期、 混合移轉可讓您可以：
  
- Office 365 中顯示內部使用者之使用者的空閒/忙碌行事曆資訊，反之亦然;
    
- 請參閱包含在內部部署和 Office 365; 中的收件者的整合全域通訊清單
    
- 檢視完整的 Outlook 收件者卡不論它們是否是在內部或 Office 365; 中的所有使用者
    
- 在內部部署 Exchange 伺服器與 Office 365 使用 TLS 和憑證 ； 之間的安全的電子郵件通訊
    
- 將傳送的郵件在內部部署 Exchange 伺服器和 Office 365 之間作為內部，讓：
    
  - 適當評估並處理目標 ； 的內部郵件的傳輸和規範代理程式
    
  - 略過反垃圾郵件篩選器。
    
完整的混合式遷移是最適合的預計會保持在多個月或更多的混合式組態的組織。您將取得稍早在本節中，加上目錄同步處理、 較佳的整合式的符合性功能和能夠將信箱移到與 Office 365 所列的功能使用線上信箱移動。Office 365 會變成在內部部署組織的副檔名。
  
如果您考慮進行完整的混合式遷移，以下是要考慮的一些事項：
  
- 完整的混合式遷移並不適合組織的所有類型。完整的混合式遷移的複雜性，因為具有小於一些好幾百種信箱組織看不到通常 justify 人力和一個設定所需的成本的優點。若此聲音您的組織，強烈建議您改用; 考慮 Cutover 或分段移轉
    
- Office 365 必須連線到 Exchange 2010 伺服器使用 「 Outlook 無所不在 」 over TCP 連接埠 443;
    
- 您需要設定目錄同步處理內部部署 Active Directory 伺服器與 Office 365; 之間使用 Azure Active Directory 連線 (AADConnect)
    
- 使用者將能夠登入 Office 365 信箱使用相同的使用者名稱和密碼時登入區域網路 （需要 Azure [Active Directory 連線使用密碼同步處理及/或 Active Directory Federation Services）;
    
- 您將需要包含 Exchange Online 移轉 ； 每個使用者信箱的 Office 365 授權
    
- 使用者不需要設定新的 Outlook 設定檔在大部分的裝置 （一些較舊的 Android 電話可能會需要新的設定檔） 並不需要重新下載電子郵件。
    
如果完整的混合式遷移聲音適合您仔細下列資源以協助您進行移轉：
  
- [Exchange server 部署助理](https://aka.ms/exdeploy)
    
- [Exchange Server 混合部署](https://technet.microsoft.com/en-us/library/jj200581%28v=exchg.150%29.aspx)
    
- [混合組態精靈](https://technet.microsoft.com/en-us/library/hh529921%28v=exchg.150%29.aspx)
    
- [混合組態精靈常見問題集](https://technet.microsoft.com/en-us/library/mt488940%28v=exchg.150%29.aspx)
    
- [混合式部署必要條件](https://technet.microsoft.com/en-us/library/hh534377%28v=exchg.150%29.aspx)
    
### <a name="migrate-to-a-newer-version-of-exchange-server"></a>移轉至新版 Exchange Server

當我們強烈相信您可透過移轉至 Office 365 來獲得最佳的值與使用者經驗時，我們也瞭解某些組織需要保留其電子郵件的內部。這可能是因為法規需求、 以保證資料不儲存在資料中心位於另一個國家/地區，依此類推。如果您選擇要保留電子郵件內部，您可以移轉至 Exchange 2013 或 Exchange 2016 的 Exchange 2010 環境。
  
我們建議您先移轉至 Exchange 2016 如果無法移轉至 Office 365。Exchange 2016 包含所有的功能和改進隨附於舊版的 Exchange 和其最符合適用 Office 365 的經驗 （雖然某些功能只適用於 Office 365）。查看只是一些您已被錯過的事項：
  
|**Exchange 版本**|**功能**|
|:-----|:-----|
|Exchange 2013  <br/> | 簡化的架構三降低伺服器角色的數字 (Mailbox、 Client Access Edge Transport)  <br/>  資料外洩防護原則 (DLP) 協助保護機密資訊洩漏  <br/>  大幅改善的 Outlook Web App 功能  <br/> |
|Exchange 2016  <br/> | *從 Exchange 2013 的功能和...]*  <br/>  進一步剛信箱及 Edge Transport 簡化的伺服器角色  <br/>  改善的 DLP 整合及與 SharePoint  <br/>  改良的資料庫台回復性  <br/>  線上文件共同作業  <br/> |
   
#### <a name="which-version-should-i-migrate-to"></a>若要應移轉版本？

我們建議您一開始假設您要移轉至 Exchange 2016。然後，使用下列資訊以確認您假設或出 Exchange 2016 規則。如果您無法移轉至 Exchange 2016 原因之一或另一個，執行相同程序與 Exchange 2013 等等。
  
|**考量**|**其他資訊**|
|:-----|:-----|
|支援日期的結尾  <br/> | 類似 Exchange 2010，每個版本的 Exchange 會有其專屬結尾支援日期：  <br/> **Exchange 2013**年 4 月 2023  <br/> **Exchange 2016**年 10 月 2025  <br/>  稍早結尾的支援日期、 更快您需要執行其他移轉。4 月 2023年會比您想像的還很接近 ！<br/> |
|Exchange 2013 或 2016年的移轉路徑  <br/> |以下是移轉至 Exchange 2013 的一般階段：  <br/> 安裝 Exchange 2013 或 2016年至現有的 Exchange 2010 組織移動服務與 Exchange 2013 或 2016年移動信箱的其他基礎結構與公用資料夾遷移至 Exchange 2013 或 2016年解除委任剩餘的 Exchange 2010 伺服器 |
|版本共存  <br/> |移轉至 Exchange 2013 或 Exchange 2016 時，您可以安裝到現有的 Exchange 2010 組織的其中一個版本。這可讓您安裝一或多個 Exchange 2013 或 Exchange 2016 伺服器以及執行移轉。  <br/> |
|伺服器硬體  <br/> | 伺服器硬體需求已從 Exchange 2010 變更。您將需要確定您要使用的硬體相容。您可以找到更多有關以下每個版本的硬體需求：<br/> [Exchange 2016 系統需求](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx) <br/> [Exchange 2013 系統需求](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx) <br/>  您可以找到大幅改善 Exchange 效能與運算動力和較新的伺服器中的儲存容量，您可能需要較少的伺服器可支援相同的信箱數目。  <br/> |
|作業系統版本  <br/> | 每個版本的最小支援的作業系統版本是：  <br/> **Exchange 2016**Windows Server 2012  <br/> **Exchange 2013**Windows Server 2008 R2 SP1  <br/>  您可以在[Exchange 支援性一覽表](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx)尋找作業系統支援的詳細資訊。  <br/> |
|Active Directory 樹系功能等級  <br/> | 基本支援 Active Directory 樹系功能等級每個版本是：  <br/> **Exchange 2016**Windows Server 2008 R2 SP1  <br/> **Exchange 2013**Windows Server 2003  <br/>  您可以在[Exchange 支援性一覽表](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx)尋找樹系功能層級支援的詳細資訊。  <br/> |
|Office 用戶端版本  <br/> | 每個版本的最小支援的 Office 用戶端版本是：  <br/> **Exchange 2016**Office 2010 （含最新的更新）  <br/> **Exchange 2013**Office 2007 SP3  <br/>  您可以在[Exchange 支援性一覽表](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx)尋找 Office 用戶端支援的詳細資訊。  <br/> |
   
#### <a name="how-do-i-migrate"></a>我該如何移轉？

如果您已決定您要保留電子郵件內部，您可以使用下列資源以協助您進行移轉：
  
- [Exchange server 部署助理](https://aka.ms/exdeploy)
    
- Exchange [2016年](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.160%29.aspx)、 [2013年](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.150%29.aspx)的 active Directory 架構變更
    
- Exchange [2016年](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx)、 [2013年](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx)的系統需求
    
- Exchange [2016年](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.160%29.aspx)、 [2013年](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.150%29.aspx)的必要條件
    
## <a name="what-if-i-need-help"></a>如果我需要說明嗎？

如果您要移轉至 Office 365，您可能會是合格使用我們 Microsoft FastTrack 服務。FastTrack 提供最佳作法、 工具及資源以提升移轉至 Office 365 儘可能以一致。最適合所有，您必須實際支援工程師將會帶領您完成移轉，從規劃及設計到您的最後一個信箱移轉。如果您想要更了解 FastTrack，仔細[Microsoft FastTrack](https://fasttrack.microsoft.com/)。
  
如果您將任何問題期間執行移轉至 Office 365，您不使用 FastTrack 或移轉至新版 Exchange Server 在此為您服務協助。以下是一些您可以使用的資源：
  
- [技術社群](https://social.technet.microsoft.com/Forums/office/en-US/home?category=exchangeserver)
    
- [客戶支援](https://support.microsoft.com/en-us/gp/support-options-for-business)
    
## <a name="related-topics"></a>相關主題

[可協助您升級從 Office 2010 伺服器和用戶端的資源](upgrade-from-office-2010-servers-and-products.md)
  
[Office 退休群組 （Microsoft 技術社群）](https://go.microsoft.com/fwlink/?linkid=842065)
  

