---
title: 存取圖表-Microsoft Azure 中的 SharePoint 2013 設計範例網際網路網站
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.collection: Ent_O365
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b91124bc-c7ec-4929-b77c-d6293db9f15e
description: 本文是名為設計範例中的圖表可存取的文字版本： Microsoft Azure 中的 SharePoint 2013 的網際網路網站。
ms.openlocfilehash: 0d42a96f80d47b360084557fea47c4155d106d30
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
ms.locfileid: "17502756"
---
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>存取圖表-設計範例： Microsoft Azure 中的 SharePoint 2013 的網際網路網站

**摘要：** 本文是名為設計範例中的圖表可存取的文字版本： Microsoft Azure 中的 SharePoint 2013 的網際網路網站。
  
使用此設計範例為起點在 Azure 中使用 SharePoint 2013 的網際網路對向網站。
  
此海報顯示如何設計 SharePoint 2013 的下列方面的範例：
  
- 使用者
    
- 區域及驗證
    
- 伺服器陣列
    
- 管理網站
    
- 服務
    
- 應用程式集區和 web 應用程式
    
- 網站集合
    
- 網站
    
- 內容資料庫
    
- 區域及 URL
    
## <a name="users-zones-and-authentication"></a>使用者、 區域及驗證

有四種類型的這個設計中的使用者帳戶。每種類型的帳戶相關聯的存取網站以及使用特定類型的驗證的區域。 
  
- 匿名客戶 — 匿名客戶可以透過例如 http://www.contoso.com 網站的存取。他們使用的區域是"網際網路區域 / 匿名"，其中會使用匿名驗證。
    
- 驗證客戶 — 驗證客戶可以透過例如 https://secure.contoso.com 網站的存取。他們使用的區域是"Extranet 區域 / SAML"，以使用 SAML 驗證使用 Azure Active Directory。
    
- 網站作者和開發人員 — 網站作者及開發人員可以透過如 http://authoring.contoso.com:8000 或 http://www.contoso.com:8000 網站存取。他們使用的區域是"預設區域 / Windows 整合式"，這會使用 Active Directory 網域服務 (AD DS)。
    
- 搜尋編目帳戶-搜尋編目帳戶有權透過 http://authoring.contoso.com:8000 或 http://www.contoso.com:8000 的網站。它會使用的區域是"預設區域 / Windows 整合式"，這會使用 AD DS 與 Windows NTLM 驗證。
    
## <a name="server-farm"></a>伺服器陣列

使用者透過 Azure 存取伺服器陣列。伺服器陣列包含一個或多個網頁伺服器。
  
## <a name="administration-site"></a>管理網站

管理網站包含數個與使用管理中心網站的 web 應用程式的應用程式集區 (在此範例應用程式集區 1) 通訊的應用程式伺服器。管理中心網站提供組織內的網站集合的存取。
  
管理網站也包含會以支援 SQL 叢集、 鏡像或 AlwaysOn 安裝及設定的 SQL Server 資料庫伺服器的 SQL 資料庫伺服器 （AlwaysOn 僅適用於 SQL Server 2012）。
  
## <a name="services"></a>服務

設計範例會顯示 SharePoint Web 服務網際網路資訊服務 (IIS) 網站。SharePoint Web 服務包含三個服務、 使用者設定檔、 搜尋和受管理的中繼資料的應用程式集區 (應用程式集區 2)。
  
在服務的網際網路網站上的附註：
  
> 受管理的中繼資料-請確定已選取 [**此服務應用程式是欄特定字詞組的預設儲存位置**。
    
> 應用程式管理--我們不建議在 Azure 中的公用對向網際網路網站中使用的應用程式。
    
## <a name="application-pools-and-web-applications"></a>應用程式集區和 web 應用程式

在 Azure 中的 [預設] 群組會顯示應用程式集區 3 中，其中包含名為 Contoso 網站的 web 應用程式。此路徑型網站集合位於 http://internal:8000。
  
## <a name="site-collections-and-sites"></a>網站集合與網站

應用程式集區中所包含的網站集合包括：
  
- 編目 （範例位置 http://authoring.contoso.com:8000） 的主機命名型網站集合 1
    
- 主機命名型網站集合 2 （範例位置 http://www.contoso.com、 https://secure.contoso.com、 http://www.contoso.com:8000） 的查詢
    
- 主機命名型網站集合 3 的查詢 （範例位置 http://assets.contoso.com、 https://secureassets.contoso.com、 http://assets.contoso.com:8000）
    
## <a name="content-databases"></a>內容資料庫

此範例會顯示兩個內容資料庫。一個是網站集合 1 用於編目 (http://authoring.contoso.com:8000)。另一個是兩個網站集合 2 和 3 用於查詢 （http://www.contoso.com、 https://secure.contoso.com、 http://www.contoso.com:8000 或 http://assets.contoso.com、 https://secureassets.contoso.com、 http://assets.contoso.com:8000）。
  
## <a name="zones-and-urls"></a>區域及 URL

此範例顯示三個區域相關聯負載平衡的 url 會使用不同的使用者帳戶。 
  
第一個清單中的 [區域及 Url 相關網站集合 1，並包含下列資訊：
  
- 使用者層網站作者
    
- 區域-預設值
    
- 負載平衡 URL-http://authoring.contoso.com:8000
    
區域及 Url 的第二個清單中三個不同的區域有三種不同類型的使用者。相關網站集合 2 中，並包含下列資訊：
  
第一個區域：
  
- 使用者層網站作者
    
- 區域-預設值
    
- 負載平衡 URL-http://www.contoso.com:8000
    
第二個區域：
  
- 使用者-匿名的客戶
    
- 區域-網際網路
    
- 負載平衡 URL-http://www.contoso.com
    
第三個區域：
  
- 使用者-已驗證的客戶
    
- 區域-外部網路
    
- 負載平衡 URL-https://secure.contoso.com
    
區域及 Url 的第三個清單中三個不同的區域有三種不同類型的使用者。相關網站集合 3，並包含下列資訊：
  
第一個區域：
  
- 使用者層網站作者
    
- 區域-網際網路
    
- 負載平衡 URL-http://assets.contoso.com:8000
    
第二個區域：
  
- 使用者-匿名的客戶
    
- 區域-網際網路
    
- 負載平衡 URL-http://assets.contoso.com
    
第三個區域：
  
- 使用者-已驗證的客戶
    
- 區域-外部網路
    
- 負載平衡 URL-http://secureassets.contoso.com
    

