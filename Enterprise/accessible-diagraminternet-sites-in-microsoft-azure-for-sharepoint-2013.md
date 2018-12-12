---
title: 存取圖表-Microsoft Azure 中的 SharePoint 2013 的網際網路網站
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 71636974-fb99-487c-ac67-f15e9401acba
description: 本文是圖表的名為 Microsoft Azure 中的網際網路網站的 SharePoint 2013 可存取的文字版本。
ms.openlocfilehash: 59c84e34ab4d748a80ab0a597817ae4d3464a43c
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
ms.locfileid: "17503046"
---
# <a name="accessible-diagram---internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>存取圖表-Microsoft Azure 中的 SharePoint 2013 的網際網路網站

**摘要：** 本文是圖表的名為 Microsoft Azure 中的網際網路網站的 SharePoint 2013 可存取的文字版本。
  
此海報說明及圖解如何公開網際網路網站福利從雲端 elasticity 和客戶帳戶的 Azure AD。有六個不同的案例說明網際網路網站獲益 Azure 的方式： 
  
- 設計及調整大小的伺服器陣列拓撲。 
    
- 微調 azure。 
    
- 選擇 [Active Directory 模型。 
    
- 設計的身分識別管理、 區域及驗證。 
    
- 設計網站和跨網站發佈的 Url。 
    
- 設計 Azure 環境。 
    
## <a name="design-and-size-the-farm-topology"></a>設計及調整大小的伺服器陣列拓撲

使用設計的伺服器陣列拓撲 TechNet 上的 SharePoint 2013 的拓撲、 容量及效能指導。 
  
確定您設計的伺服器陣列符合容量和效能目標。 
  
### <a name="example-medium-internet-sites-farm-85-page-views-per-second"></a>範例： 中型網際網路網站伺服器陣列 （~ 85 每秒網頁檢視）

此伺服器陣列提供包含 3,400,000 的項目主體的功能已最佳化容錯 SharePoint 2013 搜尋伺服器陣列拓撲。 
  
範例伺服器陣列處理 100-200 每秒文件、 語言，並加以可容納每第二個和 100 個每秒查詢 85 網頁檢視。 
  
隨附的圖顯示具有三種伺服器類型中型網際網路網站伺服器陣列： 
  
- 網頁伺服器 
    
- 應用程式伺服器 
    
- 資料庫伺服器 
    
#### <a name="web-servers"></a>網頁伺服器

Web 伺服器] 區段中，有三部網頁伺服器、 主機 A、 主機 B 和 c 主機。在每部網頁伺服器包含分散式快取、 使用者設定檔、 受管理的中繼資料及查詢處理功能。他們也包含索引分割區複本中每一部伺服器。 
  
向外延展，新增額外的網頁伺服器使用相同的功能，允許其他 28] 頁面上檢視每秒。 
  
#### <a name="application-servers"></a>應用程式伺服器

在 [應用程式伺服器] 區段中有三個應用程式伺服器主機 D 主機 E、 與主機 F.主機 D 包含編目、 管理、 分析及內容處理元件。主機 E 包含編目、 管理員及內容處理元件。主機 F 包含編目及內容處理元件。 
  
若要向外延展，新增一部應用程式伺服器與編目元件及內容處理元件處理額外 40 每秒文件。 
  
#### <a name="database-servers"></a>資料庫伺服器

在 [資料庫伺服器] 區段中有兩部伺服器的主機 G 和主機 h資料庫伺服器是在容錯方面的成對主機。 
  
主機 G 包含所有 SharePoint 資料庫，包括搜尋管理資料庫、 連結資料庫、 兩個編目資料庫、 分析資料庫及其他所有 SharePoint 資料庫。主機 H 包含所有 SharePoint 資料庫，包括備援副本的所有資料庫使用 SQL 叢集、 鏡像或 SQL Server 2012 AlwaysOn。 
  
## <a name="fine-tune-for-azure"></a>Azure 微調

SharePoint 伺服器陣列可能會需要微調的可用性設定於 Azure 平台。若要確保高可用性的所有元件，請確定所有同名設定的伺服器角色。 
  
在圖表中的範例拓撲： 
  
- 同名設定網頁伺服器和資料庫伺服器。 
    
- 未同名設定三個應用程式伺服器。這些伺服器角色都需要在 Azure 中的可用性的可調整設定。 
    
### <a name="before"></a>之前

圖表的上半部會顯示在 Azure 中設定 SharePoint 伺服器陣列之前有已微調可用性。在圖表中，三個主機應用程式伺服器未同名設定。元件數目是由伺服器陣列的效能與容量目標所決定。三部伺服器設定如下： 
  
- 具有編目、 管理、 分析及內容處理角色已主機 D 應用程式伺服器。 
    
- 具有編目、 管理員及內容處理角色已主機 E 應用程式伺服器。 
    
- 具有編目及內容處理角色已主機 F 應用程式伺服器。 
    
### <a name="after"></a>之後

此部分的圖表顯示在 Azure 中設定 SharePoint 伺服器陣列之後具有已微調可用性。Azure 能否此架構，我們將所有三部伺服器上複寫的四個元件。這會增加超過功能時所需的效能與容量的元件數目。取捨是此設計可確保當下列三個虛擬機器時指派給可用性設定 Azure 平台中所有的四個元件的高可用性。 
  
三部伺服器設定為所有具有編目、 管理、 分析及內容處理角色。 
  
## <a name="choose-the-active-directory-model"></a>選擇 [Active Directory 模型

所有的 SharePoint 解決方案需要 Windows Active Directory 網域服務 (AD DS)。在此階段中，有兩個 Azure 中的 SharePoint 解決方案的選項。 
  
- 做法 1： 專用的網域-您可對 Azure 支援的 SharePoint 伺服器陣列部署專用及隔離網域。這是不錯的選擇的公用對向網際網路網站。 
    
- 選項 2： 擴充至網站 VPN 連線到內部網域。當您擴充至網站 VPN 連線到內部網域時、 使用者會存取 SharePoint 伺服器陣列主控內部部署一樣。您可以運用您現有的 Active Directory 和 DNS 實作。 
    
## <a name="design-for-identity-management-zones-and-authentication"></a>設計的身分識別管理、 區域及驗證

### <a name="design-for-accounts-and-authentication"></a>帳戶和驗證設計

決定如何將受管理帳戶和將使用的驗證類型。 
  
#### <a name="accounts-for-site-developers-and-authors"></a>網站開發人員和作者的帳戶

- 將帳戶新增至 Azure 中的網域。 
    
- 使用內部部署 Active Directory Federation Services (AD FS) 同盟內部 Azure 中的網域帳戶。 
    
- 如果設計包含的網站 VPN 連線，請使用內部的帳戶。 
    
#### <a name="accounts-for-customers"></a>客戶的帳戶

- 使用 Azure Active Directory。 
    
- 使用不同的 saml 提供者。 
    
### <a name="design-for-zones"></a>設計的區域

在 SharePoint 2013 中的身分識別管理會納入區域和驗證的設定。 
  
此設計提供清楚的區隔客戶帳戶的所有其他帳戶。 
  
- 此設計如果您想使用客戶帳戶被處理完全不同的內部帳戶作者和網站開發人員。 
    
- 使用此設計，您可以使用區域原則以限制 web 應用程式中的客戶動作。 
    
- 此設計產生客戶帳戶和內部帳戶不同的 Url。 
    
在此範例中： 
  
- 設定內部帳戶之預設區域。 
    
- 設定驗證的客戶存取的外部網路區域。使用 Azure Active Directory (AD) 客戶帳戶，或使用不同的 saml 提供者。 
    
- 設定網際網路區域的匿名存取。 
    
請勿使用所有經過驗證的使用者設定為使用預設區域中的兩個區域設計。 
  
隨附的圖表顯示三個區域設計與區分內部和客戶帳戶。 
  
訪客和客戶透過其中兩個區域的 web 應用程式來存取在 SharePoint 2013 伺服器陣列中的 Azure AD 租用戶。兩個區域包括： 
  
- 匿名使用者的區域： 網際網路 
    
- 區域： 已驗證使用者的外部網路 
    
具有內部的帳戶使用者的存取 Azure Active Directory 租用戶從 AD DS 和透過 VPN 通道內部部署環境中的 AD FS Azure AD。「 預設 」 區域提供 Windows 驗證 (NTLM)。 
  
### <a name="design-for-connecting-to-azure-ad"></a>連線至 Azure AD 的設計

 Azure AD 提供雲端服務的身分識別管理和存取控制功能。功能包括目錄資料與一組核心身分識別服務，包括使用者登入程序、 驗證服務及 AD FS 的雲端存放區。身分識別服務隨附的 Azure AD 輕鬆地整合在內部部署 AD DS 及完全支援協力廠商身分識別提供者。
  
隨附的圖顯示下列案例： 
  
使用 Azure Active Directory 整合 SharePoint 2013、 時 Azure Access Control Service (ACS) 有兩種用途： 
  
-  Azure AD 使用 SAML 2.0 及 SharePoint 僅適用於 SAML 1.1。ACS 了解這兩種格式及做為轉換 SharePoint 與 Azure AD 之間的 token 格式中介者。
    
- ACS 會取代需要藉助的身分識別提供者 security token service (IP-STS) 這個 SAML 案例。 
    
如需詳細資訊，請參閱 TechNet library 中的設定與 SharePoint 2013 的 Azure AD。 
  
## <a name="design-sites-and-urls-for-cross-site-publishing"></a>設計網站和跨網站發佈的 Url

一個 web 應用程式的設計建議發佈案例。 
  
- 同時製作及發佈網站位於相同的 web 應用程式。 
    
- 跨網站發佈用以發佈資產。 
    
使用路徑型與主機命名型網站集合。 
  
- 根網站集合是需求。建立此站台作為路徑型網站。 
    
- 為主機命名型網站集合中建立的所有其他網站集合。 
    
Web 應用程式和根網站 Url 
  
- 使用 web 應用程式 URL 的內部名稱。除非指定不同的名稱 SharePoint 所使用的預設名稱為本機電腦名稱。您可以使用保留的網域名稱的內部網路環境。 
    
- SharePoint 將非標準連接埠號碼時建立的 web 應用程式。使用此連接埠號碼，而非連接埠 80 或連接埠 443。或使用不同但非標準連接埠號碼。 
    
- 使用相同的名稱及連接埠號碼是路徑型網站集合根網站集合。 
    
隨附的圖表顯示應用程式集區服務，例如搜尋與網站集合使用的 web 應用程式互動。顯示網站集合包括： 
  
- 位於 http://internal:8000 （根網站） 的路徑型網站集合。 
    
- 編目： 主機命名型網站集合位於 https://authoring.contoso.com:8000 等的地址。 
    
- 查詢： 2 的不同的主機命名型網站集合位於位址例如： 
    
  - http://www.contoso.com 
    
  - https://secure.contoso.com 
    
  - http://www.contoso.com:8000 
    
  - http://assets.contoso.com 
    
  - https://secureassets.contoso.com 
    
  - http://assets.contoso.com:8000 
    
## <a name="design-the-azure-environment"></a>設計 Azure 環境

此範例架構包含下列元素： 
  
- 網站 VPN 連線是選用的步驟及延伸的內部 Windows AD DS 與在 Azure 虛擬網路的 DNS 環境。 
    
- （選用） 使用 Azure 中的專屬的網域支援的 SharePoint 伺服器陣列。 
    
- 伺服器會跨角色為基礎的 Azure 雲端服務分割。 
    
- 可用性設定確保高可用性的設定相同的伺服器角色。 
    
如需詳細資訊，請參閱下文 technet： Azure Architectures for SharePoint 解決方案。 
  
隨附圖與 Azure 虛擬網路連線的內部部署環境的範例。 
  
在內部部署環境中，這是選用的元素的 Azure 環境，包括下列元件： 
  
- Windows Server 2012 RRAS 
    
- AD DS 
    
- 從 Windows Server 和 AD DS VPN 閘道作用中的 VPN 閘道子網路 
    
Azure 虛擬網路環境包含下列元件： 
  
- 作用中的 VPN 閘道子網路 （重疊的內部部署環境中，如果有的話） 
    
- 雲端服務，包含 AD DS 與 DNS 的可用性設定 （兩部伺服器） 
    
- 雲端服務包含前端伺服器的可用性設定 （三個 SharePoint 伺服器） 和應用程式伺服器的可用性設定 （三個 SharePoint 伺服器） 
    
- 包含兩個資料庫可用性的雲端服務設定 
    

