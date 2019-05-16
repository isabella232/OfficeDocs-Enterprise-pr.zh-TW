---
title: 易於存取的圖表-Microsoft Azure 中的 SharePoint 2013 的網際網路網站
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 71636974-fb99-487c-ac67-f15e9401acba
description: 本文是圖表的名為 SharePoint 2013 網際網路網站，在 Microsoft Azure 中易於存取的文字版本。
ms.openlocfilehash: 1d18ad73502c7e21c1c0825e3e56e4faac2a4a09
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068639"
---
# <a name="accessible-diagram---internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>易於存取的圖表-Microsoft Azure 中的 SharePoint 2013 的網際網路網站

**摘要：** 本文是圖表的名為 SharePoint 2013 網際網路網站，在 Microsoft Azure 中易於存取的文字版本。
  
此海報說明，並說明如何公開網際網路網站權益從雲端彈性和客戶帳戶的 Azure AD。 有六個不同的案例，說明網際網路網站受益於 Azure 的方式： 
  
- 設計和大小的伺服器陣列拓撲。 
    
- 微調 azure。 
    
- 選擇 [Active Directory 模型。 
    
- 針對身分識別管理、 區域及驗證所設計。 
    
- 設計站台和跨網站發佈的 Url。 
    
- 設計 Azure 環境。 
    
## <a name="design-and-size-the-farm-topology"></a>設計和大小的伺服器陣列拓撲

用於 TechNet 上的 SharePoint 2013 的拓撲、 容量及效能的指引來設計伺服器陣列拓撲。 
  
請確定您在設計伺服器陣列符合容量和效能目標。 
  
### <a name="example-medium-internet-sites-farm-85-page-views-per-second"></a>範例： 中型網際網路網站 」 伺服器陣列 （~ 85] 頁面上每秒的檢視表）

此伺服器陣列提供容錯 SharePoint 2013 伺服器陣列之搜尋拓撲最適合的主體包含 3400000 項目。 
  
範例伺服器陣列處理根據語言，每秒 100-200 份文件，其可容納 85 每秒的第二個和 100 個查詢的網頁檢視。 
  
隨附圖顯示中型網際網路網站 」 伺服器陣列與伺服器的三種： 
  
- 網頁伺服器 
    
- 應用程式伺服器 
    
- 資料庫伺服器 
    
#### <a name="web-servers"></a>網頁伺服器

在 [web 伺服器] 區段中，有三部網頁伺服器、 主機 A、 主機 B 和主機 c。每部網頁伺服器包含分散式快取、 使用者設定檔、 受管理中繼資料，以及查詢處理功能。 它們也包含索引分割區複本中每一部伺服器。 
  
若要向外延展，新增額外的網頁伺服器的相同功能，可以針對其他 28] 頁面上檢視每秒。 
  
#### <a name="application-servers"></a>應用程式伺服器

在 [應用程式伺服器] 區段中，有三個應用程式伺服器主機 D 主機 E、 及主機 F.主機 D 包含編目、 管理、 分析及內容處理元件。 主機 E 包含編目、 系統管理員及內容處理元件。 主機 F 包含編目和內容處理元件。 
  
若要向外擴充，新增編目元件與內容處理元件來處理每秒額外 40 文件的一部應用程式伺服器。 
  
#### <a name="database-servers"></a>資料庫伺服器

在 [資料庫伺服器] 區段中，有兩部伺服器，主機 G、 H 主機資料庫伺服器位於成對的主應用程式的容錯能力。 
  
主機 G 包含所有 SharePoint 資料庫，包括搜尋管理資料庫、 連結 」 資料庫、 兩個編目資料庫、 分析資料庫及其他所有 SharePoint 資料庫。 主機 H 包含所有 SharePoint 資料庫，包括使用 SQL 叢集、 鏡像或 SQL Server 2012 AlwaysOn 的所有資料庫的備援副本。 
  
## <a name="fine-tune-for-azure"></a>Azure 微調

在 SharePoint 伺服器陣列可能需要微調的 Azure 的平台] 中的可用性設定組。 若要確保所有元件的高可用性，請確定所有具有相同設定的伺服器角色。 
  
在圖表中的範例拓撲： 
  
- 具有相同設定網頁伺服器和資料庫伺服器。 
    
- 不具有相同設定三個應用程式伺服器。 這些伺服器角色需要在 Azure 中的可用性微調設定。 
    
### <a name="before"></a>之前

圖表的上半部會顯示在 Azure 中設定 SharePoint 伺服器陣列之前具有已微調可用性。 在圖表中，三個主機應用程式伺服器都不具有相同設定。 元件數目取決於伺服器陣列的效能與容量目標。 三部伺服器設定如下： 
  
- 設定主機 D 應用程式伺服器是編目、 管理、 分析及內容處理角色。 
    
- 設定主機 E 應用程式伺服器是編目、 系統管理員及內容處理角色。 
    
- 設定主機 F 應用程式伺服器是編目和內容處理角色。 
    
### <a name="after"></a>之後

這部分的圖表顯示在 Azure 中設定 SharePoint 伺服器陣列之後有已微調可用性。 Azure 能否這種架構，我們將所有的三部伺服器上複寫的四個元件。 這會增加以外的功能所需的效能與容量的元件數目。 缺點是這種設計可確保當這些三部虛擬機器會指派給一個可用性設定組 Azure 的平台] 中的所有四個元件的高可用性。 
  
三部伺服器都設定為所有具有編目、 管理、 分析及內容處理角色。 
  
## <a name="choose-the-active-directory-model"></a>選擇 [Active Directory 模型

所有的 SharePoint 解決方案需要 Windows Active Directory 網域服務 (AD DS)。 在這個階段中，有兩個選項可在 Azure 中的 SharePoint 解決方案。 
  
- 選項 1： 專用的網域，您可對支援 SharePoint 伺服器陣列的 Azure 部署專用和隔離網域。 這是很好的選擇的公用對向網際網路網站。 
    
- 選項 2： 擴充透過站台對站 VPN 連線的內部部署網域。 當您擴充透過站台對站 VPN 連線的內部部署網域時，使用者會存取 SharePoint 伺服器陣列，好像它是裝載於內部。 您可以利用您現有的 Active Directory 和 DNS 實作。 
    
## <a name="design-for-identity-management-zones-and-authentication"></a>設計的身分識別管理、 區域及驗證

### <a name="design-for-accounts-and-authentication"></a>帳戶和驗證的設計

決定如何將受管理帳戶和將使用的驗證類型。 
  
#### <a name="accounts-for-site-developers-and-authors"></a>網站開發人員和作者帳戶

- 將帳戶新增至 Azure 中的網域。 
    
- 使用內部部署 Active Directory Federation Services (AD FS) 同盟內部 Azure 中的網域帳戶。 
    
- 如果設計包含站台對站 VPN 連線，請使用內部帳戶。 
    
#### <a name="accounts-for-customers"></a>客戶的帳戶

- 使用 Azure Active Directory。 
    
- 使用不同的 SAML 型提供者。 
    
### <a name="design-for-zones"></a>設計的區域

在 SharePoint 2013 中的身分識別管理是作為因素納入的區域及驗證設定。 
  
此設計中提供清楚的區隔的客戶帳戶從所有其他帳戶。 
  
- 此設計如果您想使用客戶帳戶被處理完全不同的內部帳戶作者和網站開發。 
    
- 藉由使用此設計中，您可以使用區域原則，以限制 web 應用程式內的客戶動作。 
    
- 這項設計會導致客戶帳戶和內部帳戶不同的 Url。 
    
在此範例中： 
  
- 設定內部帳戶的 「 預設 」 區域。 
    
- 設定已驗證的客戶存取的外部網路區域。 使用 Azure Active Directory (AD) 客戶帳戶，或使用不同的 SAML 型提供者。 
    
- 設定匿名存取的網際網路區域。 
    
請勿使用所有已驗證的使用者設定為使用 「 預設 」 區域中的兩個區域設計。 
  
隨附的圖顯示內部的中間三個區域設計和客戶帳戶。 
  
訪客和客戶透過其中一個兩個區域的 web 應用程式來存取 SharePoint 2013 伺服器陣列中的 Azure AD 租用戶。 兩個區域包含： 
  
- 匿名使用者的區域： 網際網路 
    
- 區域： 已驗證使用者的外部網路 
    
使用內部帳戶的使用者會存取 Azure Active Directory 租用戶從 AD DS 並在內部部署環境透過 VPN 通道中的 AD FS 到 Azure AD。 「 預設 」 區域提供 Windows 驗證 (NTLM)。 
  
### <a name="design-for-connecting-to-azure-ad"></a>設計以連線到 Azure AD

 Azure AD 提供雲端服務的身分識別管理及存取控制功能。 功能包括目錄資料和一組核心的身分識別服務，包括使用者登入程序、 驗證服務，並使用 AD FS 的雲端式存放區。 隨附於 Azure AD 輕易地識別服務整合內部部署 AD DS 和完全支援協力廠商身分識別提供者。
  
隨附的圖會顯示下列案例： 
  
當與 Azure Active Directory 整合 SharePoint 2013，Azure 存取控制服務 (ACS) 會有兩種用途： 
  
-  Azure AD 使用 SAML 2.0 及 SharePoint 只適用於 SAML 1.1 版。 ACS 瞭解這兩種格式，並做為轉換 SharePoint 和 Azure AD 之間的 token 格式媒介。
    
- ACS 會取代身分識別提供者 security token service (IP-STS) 此 SAML 案例的需求。 
    
如需詳細資訊，請參閱 TechNet library 中的設定 Azure AD 中使用 SharePoint 2013。 
  
## <a name="design-sites-and-urls-for-cross-site-publishing"></a>設計適用於跨網站發佈功能的網站與 Url

一個 web 應用程式的設計建議發佈案例。 
  
- 製作與發佈網站位於相同的 web 應用程式。 
    
- 跨網站發佈用來發佈資產。 
    
使用路徑型與主機命名型網站集合。 
  
- 一個根網站集合是必要條件。 建立為路徑型網站的 [此網站]。 
    
- 建立為主機命名型網站集合的所有其他網站集合。 
    
Web 應用程式和根網站 Url 
  
- 使用 web 應用程式 URL 的內部名稱。 除非指定不同的名稱，SharePoint 會使用本機電腦名稱做為預設名稱。 您可以使用網域名稱保留內部網路環境。 
    
- 建立 web 應用程式時，SharePoint 會將指派非標準連接埠號碼。 使用此連接埠號碼，而不是連接埠 80 或連接埠 443。 或使用不同，但非標準連接埠號碼。 
    
- 根網站集合，也就是在路徑型網站集合使用相同的名稱和連接埠號碼。 
    
隨附的圖顯示應用程式集區服務，例如搜尋與網站集合使用的 web 應用程式互動。 顯示網站集合包括： 
  
- 路徑型網站集合位於http://internal:8000（根網站）。 
    
- 編目： 主機命名型網站集合位於位址例如https://authoring.contoso.com:8000。 
    
- 查詢： 2 不同的主機命名型網站集合位於地址如下： 
    
  - http://www.contoso.com 
    
  - https://secure.contoso.com 
    
  - http://www.contoso.com:8000 
    
  - http://assets.contoso.com 
    
  - https://secureassets.contoso.com 
    
  - http://assets.contoso.com:8000 
    
## <a name="design-the-azure-environment"></a>設計 Azure 環境

此範例架構包括下列元素： 
  
- 站台對站 VPN 連線是選擇性的並延伸至 azure 虛擬網路的 DNS 環境與內部部署 Windows AD DS。 
    
- （選擇性） 用於在 Azure 中的專用的網域支援的 SharePoint 伺服器陣列。 
    
- 伺服器會分割到 Azure 的雲端服務角色為基礎。 
    
- 可用性設定組確保設定相同的伺服器角色的高的可用性。 
    
如需詳細資訊，請參閱下文 technet: Azure Architectures for SharePoint 解決方案。 
  
隨附圖與 Azure 虛擬網路連線內部部署環境的範例。 
  
內部部署環境中，為 Azure 環境的選用性元素，包括下列元件： 
  
- Windows Server 2012 RRAS 
    
- AD DS 
    
- 從 Windows Server 及 AD DS VPN 閘道至作用中的 VPN 閘道子網路 
    
在 Azure 虛擬網路環境包含下列元件： 
  
- 作用中的 VPN 閘道子網路 （重疊的內部部署環境，如果有的話） 
    
- 雲端服務，包含 AD DS 和 DNS 可用性設定 （兩部伺服器） 
    
- 雲端服務，包括前端伺服器的可用性設定 (三個 SharePoint server)，且應用程式伺服器的可用性設定 (三個 SharePoint server) 
    
- 含有兩個資料庫可用性雲端服務設定 
    

