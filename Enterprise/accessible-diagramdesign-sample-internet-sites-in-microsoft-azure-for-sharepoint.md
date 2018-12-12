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
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a><span data-ttu-id="e87aa-103">存取圖表-設計範例： Microsoft Azure 中的 SharePoint 2013 的網際網路網站</span><span class="sxs-lookup"><span data-stu-id="e87aa-103">Accessible diagram - Design sample: Internet sites in Microsoft Azure for SharePoint 2013</span></span>

<span data-ttu-id="e87aa-104">**摘要：** 本文是名為設計範例中的圖表可存取的文字版本： Microsoft Azure 中的 SharePoint 2013 的網際網路網站。</span><span class="sxs-lookup"><span data-stu-id="e87aa-104">**Summary:** This article is an accessible text version of the diagram named Design sample: Internet sites in Microsoft Azure for SharePoint 2013.</span></span>
  
<span data-ttu-id="e87aa-105">使用此設計範例為起點在 Azure 中使用 SharePoint 2013 的網際網路對向網站。</span><span class="sxs-lookup"><span data-stu-id="e87aa-105">Use this design example as a starting point for an Internet-facing site in Azure using SharePoint 2013.</span></span>
  
<span data-ttu-id="e87aa-106">此海報顯示如何設計 SharePoint 2013 的下列方面的範例：</span><span class="sxs-lookup"><span data-stu-id="e87aa-106">This poster shows an example of how to design the following aspects of SharePoint 2013:</span></span>
  
- <span data-ttu-id="e87aa-107">使用者</span><span class="sxs-lookup"><span data-stu-id="e87aa-107">Users</span></span>
    
- <span data-ttu-id="e87aa-108">區域及驗證</span><span class="sxs-lookup"><span data-stu-id="e87aa-108">Zones and authentication</span></span>
    
- <span data-ttu-id="e87aa-109">伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="e87aa-109">Server farm</span></span>
    
- <span data-ttu-id="e87aa-110">管理網站</span><span class="sxs-lookup"><span data-stu-id="e87aa-110">Administration site</span></span>
    
- <span data-ttu-id="e87aa-111">服務</span><span class="sxs-lookup"><span data-stu-id="e87aa-111">Services</span></span>
    
- <span data-ttu-id="e87aa-112">應用程式集區和 web 應用程式</span><span class="sxs-lookup"><span data-stu-id="e87aa-112">Application pools and web applications</span></span>
    
- <span data-ttu-id="e87aa-113">網站集合</span><span class="sxs-lookup"><span data-stu-id="e87aa-113">Site collections</span></span>
    
- <span data-ttu-id="e87aa-114">網站</span><span class="sxs-lookup"><span data-stu-id="e87aa-114">Sites</span></span>
    
- <span data-ttu-id="e87aa-115">內容資料庫</span><span class="sxs-lookup"><span data-stu-id="e87aa-115">Content databases</span></span>
    
- <span data-ttu-id="e87aa-116">區域及 URL</span><span class="sxs-lookup"><span data-stu-id="e87aa-116">Zones and URLs</span></span>
    
## <a name="users-zones-and-authentication"></a><span data-ttu-id="e87aa-117">使用者、 區域及驗證</span><span class="sxs-lookup"><span data-stu-id="e87aa-117">Users, zones and authentication</span></span>

<span data-ttu-id="e87aa-p101">有四種類型的這個設計中的使用者帳戶。每種類型的帳戶相關聯的存取網站以及使用特定類型的驗證的區域。</span><span class="sxs-lookup"><span data-stu-id="e87aa-p101">There are four types of user accounts in this design. Each type of account is associated with a site for access and with a zone that uses a specific type of authentication.</span></span> 
  
- <span data-ttu-id="e87aa-120">匿名客戶 — 匿名客戶可以透過例如 http://www.contoso.com 網站的存取。他們使用的區域是"網際網路區域 / 匿名"，其中會使用匿名驗證。</span><span class="sxs-lookup"><span data-stu-id="e87aa-120">Anonymous customers — Anonymous customers have access through a site such as http://www.contoso.com. The zone they use is the "Internet zone / anonymous", which uses anonymous authentication.</span></span>
    
- <span data-ttu-id="e87aa-121">驗證客戶 — 驗證客戶可以透過例如 https://secure.contoso.com 網站的存取。他們使用的區域是"Extranet 區域 / SAML"，以使用 SAML 驗證使用 Azure Active Directory。</span><span class="sxs-lookup"><span data-stu-id="e87aa-121">Authenticated customers — Authenticated customers have access through a site such as https://secure.contoso.com. The zone they use is the "Extranet zone / SAML", which uses Azure Active Directory with SAML authentication.</span></span>
    
- <span data-ttu-id="e87aa-p102">網站作者和開發人員 — 網站作者及開發人員可以透過如 http://authoring.contoso.com:8000 或 http://www.contoso.com:8000 網站存取。他們使用的區域是"預設區域 / Windows 整合式"，這會使用 Active Directory 網域服務 (AD DS)。</span><span class="sxs-lookup"><span data-stu-id="e87aa-p102">Site authors and developers — Site authors and developers have access through sites such as http://authoring.contoso.com:8000 or http://www.contoso.com:8000. The zone they use is the "Default zone / Windows integrated", which uses Active Directory Domain Services (AD DS).</span></span>
    
- <span data-ttu-id="e87aa-p103">搜尋編目帳戶-搜尋編目帳戶有權透過 http://authoring.contoso.com:8000 或 http://www.contoso.com:8000 的網站。它會使用的區域是"預設區域 / Windows 整合式"，這會使用 AD DS 與 Windows NTLM 驗證。</span><span class="sxs-lookup"><span data-stu-id="e87aa-p103">Search Crawl Account — The search crawl account has access through sites such as http://authoring.contoso.com:8000 or http://www.contoso.com:8000. The zone it uses is the "Default zone / Windows integrated", which uses AD DS with Windows NTLM authentication.</span></span>
    
## <a name="server-farm"></a><span data-ttu-id="e87aa-126">伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="e87aa-126">Server farm</span></span>

<span data-ttu-id="e87aa-p104">使用者透過 Azure 存取伺服器陣列。伺服器陣列包含一個或多個網頁伺服器。</span><span class="sxs-lookup"><span data-stu-id="e87aa-p104">The users access the server farm through Azure. The server farm contains one or more Web servers.</span></span>
  
## <a name="administration-site"></a><span data-ttu-id="e87aa-129">管理網站</span><span class="sxs-lookup"><span data-stu-id="e87aa-129">Administration site</span></span>

<span data-ttu-id="e87aa-p105">管理網站包含數個與使用管理中心網站的 web 應用程式的應用程式集區 (在此範例應用程式集區 1) 通訊的應用程式伺服器。管理中心網站提供組織內的網站集合的存取。</span><span class="sxs-lookup"><span data-stu-id="e87aa-p105">The administration site contains several application servers, which communicate with an Application Pool (Application Pool 1 in the example) that uses the web application Central Administration Site. The Central Administration Site provides access to site collections within the organization.</span></span>
  
<span data-ttu-id="e87aa-132">管理網站也包含會以支援 SQL 叢集、 鏡像或 AlwaysOn 安裝及設定的 SQL Server 資料庫伺服器的 SQL 資料庫伺服器 （AlwaysOn 僅適用於 SQL Server 2012）。</span><span class="sxs-lookup"><span data-stu-id="e87aa-132">The administration site also contains SQL Database servers, which are database servers with SQL Server installed and configured to support SQL clustering, mirroring, or AlwaysOn (AlwaysOn applies to SQL Server 2012 only).</span></span>
  
## <a name="services"></a><span data-ttu-id="e87aa-133">服務</span><span class="sxs-lookup"><span data-stu-id="e87aa-133">Services</span></span>

<span data-ttu-id="e87aa-p106">設計範例會顯示 SharePoint Web 服務網際網路資訊服務 (IIS) 網站。SharePoint Web 服務包含三個服務、 使用者設定檔、 搜尋和受管理的中繼資料的應用程式集區 (應用程式集區 2)。</span><span class="sxs-lookup"><span data-stu-id="e87aa-p106">The design example shows an Internet Information Services (IIS) website, SharePoint Web Services. SharePoint Web Services contains an application pool (Application Pool 2) with three services, User Profile, Search, and Managed Metadata.</span></span>
  
<span data-ttu-id="e87aa-136">在服務的網際網路網站上的附註：</span><span class="sxs-lookup"><span data-stu-id="e87aa-136">Notes on Services for Internet sites:</span></span>
  
> <span data-ttu-id="e87aa-137">受管理的中繼資料-請確定已選取 [**此服務應用程式是欄特定字詞組的預設儲存位置**。</span><span class="sxs-lookup"><span data-stu-id="e87aa-137">Managed Metadata — Be sure to select **This service application is the default storage location for column specific term sets**.</span></span>
    
> <span data-ttu-id="e87aa-138">應用程式管理--我們不建議在 Azure 中的公用對向網際網路網站中使用的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e87aa-138">App Management — We do not recommend using apps in a public-facing Internet site in Azure.</span></span>
    
## <a name="application-pools-and-web-applications"></a><span data-ttu-id="e87aa-139">應用程式集區和 web 應用程式</span><span class="sxs-lookup"><span data-stu-id="e87aa-139">Application pools and web applications</span></span>

<span data-ttu-id="e87aa-p107">在 Azure 中的 [預設] 群組會顯示應用程式集區 3 中，其中包含名為 Contoso 網站的 web 應用程式。此路徑型網站集合位於 http://internal:8000。</span><span class="sxs-lookup"><span data-stu-id="e87aa-p107">The Default Group in Azure shows Application Pool 3, which contains a web application named Contoso Sites. This path-based site collection is located at http://internal:8000.</span></span>
  
## <a name="site-collections-and-sites"></a><span data-ttu-id="e87aa-142">網站集合與網站</span><span class="sxs-lookup"><span data-stu-id="e87aa-142">Site collections and sites</span></span>

<span data-ttu-id="e87aa-143">應用程式集區中所包含的網站集合包括：</span><span class="sxs-lookup"><span data-stu-id="e87aa-143">The site collections contained in the application pool include:</span></span>
  
- <span data-ttu-id="e87aa-144">編目 （範例位置 http://authoring.contoso.com:8000） 的主機命名型網站集合 1</span><span class="sxs-lookup"><span data-stu-id="e87aa-144">Host-named site collection 1 for crawling (example location http://authoring.contoso.com:8000)</span></span>
    
- <span data-ttu-id="e87aa-145">主機命名型網站集合 2 （範例位置 http://www.contoso.com、 https://secure.contoso.com、 http://www.contoso.com:8000） 的查詢</span><span class="sxs-lookup"><span data-stu-id="e87aa-145">Host-named site collection 2 for queries (sample locations http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000)</span></span>
    
- <span data-ttu-id="e87aa-146">主機命名型網站集合 3 的查詢 （範例位置 http://assets.contoso.com、 https://secureassets.contoso.com、 http://assets.contoso.com:8000）</span><span class="sxs-lookup"><span data-stu-id="e87aa-146">Host-named site collection 3 for queries (sample locations http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000)</span></span>
    
## <a name="content-databases"></a><span data-ttu-id="e87aa-147">內容資料庫</span><span class="sxs-lookup"><span data-stu-id="e87aa-147">Content databases</span></span>

<span data-ttu-id="e87aa-p108">此範例會顯示兩個內容資料庫。一個是網站集合 1 用於編目 (http://authoring.contoso.com:8000)。另一個是兩個網站集合 2 和 3 用於查詢 （http://www.contoso.com、 https://secure.contoso.com、 http://www.contoso.com:8000 或 http://assets.contoso.com、 https://secureassets.contoso.com、 http://assets.contoso.com:8000）。</span><span class="sxs-lookup"><span data-stu-id="e87aa-p108">The example shows two content databases. One is for the site collection 1 used for crawling (http://authoring.contoso.com:8000). The other is for the two site collections 2 and 3 used for queries (http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000, or http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000).</span></span>
  
## <a name="zones-and-urls"></a><span data-ttu-id="e87aa-151">區域及 URL</span><span class="sxs-lookup"><span data-stu-id="e87aa-151">Zones and URLs</span></span>

<span data-ttu-id="e87aa-152">此範例顯示三個區域相關聯負載平衡的 url 會使用不同的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="e87aa-152">The example shows three zones with the associated load-balanced URLs that are used by different user accounts.</span></span> 
  
<span data-ttu-id="e87aa-153">第一個清單中的 [區域及 Url 相關網站集合 1，並包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="e87aa-153">The first list of zones and URLs is related to site collection 1, and it contains the following information:</span></span>
  
- <span data-ttu-id="e87aa-154">使用者層網站作者</span><span class="sxs-lookup"><span data-stu-id="e87aa-154">Users - Site authors</span></span>
    
- <span data-ttu-id="e87aa-155">區域-預設值</span><span class="sxs-lookup"><span data-stu-id="e87aa-155">Zone - Default</span></span>
    
- <span data-ttu-id="e87aa-156">負載平衡 URL-http://authoring.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="e87aa-156">Load-balanced URL - http://authoring.contoso.com:8000</span></span>
    
<span data-ttu-id="e87aa-p109">區域及 Url 的第二個清單中三個不同的區域有三種不同類型的使用者。相關網站集合 2 中，並包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="e87aa-p109">The second list of zones and URLs has three different types of users in three different zones. It is related to site collection 2, and it contains the following information:</span></span>
  
<span data-ttu-id="e87aa-159">第一個區域：</span><span class="sxs-lookup"><span data-stu-id="e87aa-159">First zone:</span></span>
  
- <span data-ttu-id="e87aa-160">使用者層網站作者</span><span class="sxs-lookup"><span data-stu-id="e87aa-160">Users - Site authors</span></span>
    
- <span data-ttu-id="e87aa-161">區域-預設值</span><span class="sxs-lookup"><span data-stu-id="e87aa-161">Zone - Default</span></span>
    
- <span data-ttu-id="e87aa-162">負載平衡 URL-http://www.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="e87aa-162">Load-balanced URL - http://www.contoso.com:8000</span></span>
    
<span data-ttu-id="e87aa-163">第二個區域：</span><span class="sxs-lookup"><span data-stu-id="e87aa-163">Second zone:</span></span>
  
- <span data-ttu-id="e87aa-164">使用者-匿名的客戶</span><span class="sxs-lookup"><span data-stu-id="e87aa-164">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="e87aa-165">區域-網際網路</span><span class="sxs-lookup"><span data-stu-id="e87aa-165">Zone - Internet</span></span>
    
- <span data-ttu-id="e87aa-166">負載平衡 URL-http://www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="e87aa-166">Load-balanced URL - http://www.contoso.com</span></span>
    
<span data-ttu-id="e87aa-167">第三個區域：</span><span class="sxs-lookup"><span data-stu-id="e87aa-167">Third zone:</span></span>
  
- <span data-ttu-id="e87aa-168">使用者-已驗證的客戶</span><span class="sxs-lookup"><span data-stu-id="e87aa-168">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="e87aa-169">區域-外部網路</span><span class="sxs-lookup"><span data-stu-id="e87aa-169">Zone - Extranet</span></span>
    
- <span data-ttu-id="e87aa-170">負載平衡 URL-https://secure.contoso.com</span><span class="sxs-lookup"><span data-stu-id="e87aa-170">Load-balanced URL - https://secure.contoso.com</span></span>
    
<span data-ttu-id="e87aa-p110">區域及 Url 的第三個清單中三個不同的區域有三種不同類型的使用者。相關網站集合 3，並包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="e87aa-p110">The third list of zones and URLs has three different types of users in three different zones. It is related to site collection 3, and it contains the following information:</span></span>
  
<span data-ttu-id="e87aa-173">第一個區域：</span><span class="sxs-lookup"><span data-stu-id="e87aa-173">First zone:</span></span>
  
- <span data-ttu-id="e87aa-174">使用者層網站作者</span><span class="sxs-lookup"><span data-stu-id="e87aa-174">Users - Site authors</span></span>
    
- <span data-ttu-id="e87aa-175">區域-網際網路</span><span class="sxs-lookup"><span data-stu-id="e87aa-175">Zone - Internet</span></span>
    
- <span data-ttu-id="e87aa-176">負載平衡 URL-http://assets.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="e87aa-176">Load-balanced URL - http://assets.contoso.com:8000</span></span>
    
<span data-ttu-id="e87aa-177">第二個區域：</span><span class="sxs-lookup"><span data-stu-id="e87aa-177">Second zone:</span></span>
  
- <span data-ttu-id="e87aa-178">使用者-匿名的客戶</span><span class="sxs-lookup"><span data-stu-id="e87aa-178">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="e87aa-179">區域-網際網路</span><span class="sxs-lookup"><span data-stu-id="e87aa-179">Zone - Internet</span></span>
    
- <span data-ttu-id="e87aa-180">負載平衡 URL-http://assets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="e87aa-180">Load-balanced URL - http://assets.contoso.com</span></span>
    
<span data-ttu-id="e87aa-181">第三個區域：</span><span class="sxs-lookup"><span data-stu-id="e87aa-181">Third zone:</span></span>
  
- <span data-ttu-id="e87aa-182">使用者-已驗證的客戶</span><span class="sxs-lookup"><span data-stu-id="e87aa-182">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="e87aa-183">區域-外部網路</span><span class="sxs-lookup"><span data-stu-id="e87aa-183">Zone - Extranet</span></span>
    
- <span data-ttu-id="e87aa-184">負載平衡 URL-http://secureassets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="e87aa-184">Load-balanced URL - http://secureassets.contoso.com</span></span>
    

