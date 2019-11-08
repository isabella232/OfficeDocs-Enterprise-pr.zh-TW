---
title: 易於存取的圖表-Microsoft Azure 中的 SharePoint 2013 設計範例網際網路網站
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.collection: Ent_O365
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b91124bc-c7ec-4929-b77c-d6293db9f15e
description: 本文是名為設計範例圖表的易於存取的文字版本： 在 Microsoft Azure for SharePoint 2013 的網際網路網站。
ms.openlocfilehash: 52ae615cbdc6a355155e54e36bc6a3d733d84869
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "38027627"
---
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a><span data-ttu-id="e633c-103">易於存取的圖表-設計範例： 在 Microsoft Azure for SharePoint 2013 的網際網路網站</span><span class="sxs-lookup"><span data-stu-id="e633c-103">Accessible diagram - Design sample: Internet sites in Microsoft Azure for SharePoint 2013</span></span>

<span data-ttu-id="e633c-104">**摘要：** 本文是名為設計範例圖表的易於存取的文字版本： 在 Microsoft Azure for SharePoint 2013 的網際網路網站。</span><span class="sxs-lookup"><span data-stu-id="e633c-104">**Summary:** This article is an accessible text version of the diagram named Design sample: Internet sites in Microsoft Azure for SharePoint 2013.</span></span>
  
<span data-ttu-id="e633c-105">使用此設計範例做為起點，適用於網際網路對向網站在 Azure 中使用 SharePoint 2013。</span><span class="sxs-lookup"><span data-stu-id="e633c-105">Use this design example as a starting point for an Internet-facing site in Azure using SharePoint 2013.</span></span>
  
<span data-ttu-id="e633c-106">此海報顯示如何設計 SharePoint 2013 的下列層面的範例：</span><span class="sxs-lookup"><span data-stu-id="e633c-106">This poster shows an example of how to design the following aspects of SharePoint 2013:</span></span>
  
- <span data-ttu-id="e633c-107">使用者</span><span class="sxs-lookup"><span data-stu-id="e633c-107">Users</span></span>
    
- <span data-ttu-id="e633c-108">區域及驗證</span><span class="sxs-lookup"><span data-stu-id="e633c-108">Zones and authentication</span></span>
    
- <span data-ttu-id="e633c-109">伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="e633c-109">Server farm</span></span>
    
- <span data-ttu-id="e633c-110">管理網站</span><span class="sxs-lookup"><span data-stu-id="e633c-110">Administration site</span></span>
    
- <span data-ttu-id="e633c-111">服務</span><span class="sxs-lookup"><span data-stu-id="e633c-111">Services</span></span>
    
- <span data-ttu-id="e633c-112">應用程式集區和 web 應用程式</span><span class="sxs-lookup"><span data-stu-id="e633c-112">Application pools and web applications</span></span>
    
- <span data-ttu-id="e633c-113">網站集合</span><span class="sxs-lookup"><span data-stu-id="e633c-113">Site collections</span></span>
    
- <span data-ttu-id="e633c-114">網站</span><span class="sxs-lookup"><span data-stu-id="e633c-114">Sites</span></span>
    
- <span data-ttu-id="e633c-115">內容資料庫</span><span class="sxs-lookup"><span data-stu-id="e633c-115">Content databases</span></span>
    
- <span data-ttu-id="e633c-116">區域及 URL</span><span class="sxs-lookup"><span data-stu-id="e633c-116">Zones and URLs</span></span>
    
## <a name="users-zones-and-authentication"></a><span data-ttu-id="e633c-117">使用者、 區域及驗證</span><span class="sxs-lookup"><span data-stu-id="e633c-117">Users, zones and authentication</span></span>

<span data-ttu-id="e633c-118">有四種類型的這個設計中的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="e633c-118">There are four types of user accounts in this design.</span></span> <span data-ttu-id="e633c-119">每種類型是驗證的帳戶的網站，以供存取與對使用特定類型一個區域相關聯。</span><span class="sxs-lookup"><span data-stu-id="e633c-119">Each type of account is associated with a site for access and with a zone that uses a specific type of authentication.</span></span> 
  
- <span data-ttu-id="e633c-120">匿名客戶 — 匿名客戶可以存取網站透過例如https://www.contoso.com。</span><span class="sxs-lookup"><span data-stu-id="e633c-120">Anonymous customers — Anonymous customers have access through a site such as https://www.contoso.com.</span></span> <span data-ttu-id="e633c-121">他們使用的區域是 「 網際網路區域 / 匿名 」，這會使用匿名驗證。</span><span class="sxs-lookup"><span data-stu-id="e633c-121">The zone they use is the "Internet zone / anonymous", which uses anonymous authentication.</span></span>
    
- <span data-ttu-id="e633c-122">驗證客戶 — 驗證客戶可以存取網站透過例如https://secure.contoso.com。</span><span class="sxs-lookup"><span data-stu-id="e633c-122">Authenticated customers — Authenticated customers have access through a site such as https://secure.contoso.com.</span></span> <span data-ttu-id="e633c-123">他們使用的區域是 「 外部網路區域 / SAML 」，可使用 SAML 驗證使用 Azure Active Directory。</span><span class="sxs-lookup"><span data-stu-id="e633c-123">The zone they use is the "Extranet zone / SAML", which uses Azure Active Directory with SAML authentication.</span></span>
    
- <span data-ttu-id="e633c-124">網站作者及開發人員-網站作者和開發人員可以存取網站透過例如https://authoring.contoso.com:8000或https://www.contoso.com:8000。</span><span class="sxs-lookup"><span data-stu-id="e633c-124">Site authors and developers — Site authors and developers have access through sites such as https://authoring.contoso.com:8000 or https://www.contoso.com:8000.</span></span> <span data-ttu-id="e633c-125">它們使用的區域是 「 預設 」 區域 / Windows 整合 」，可使用 Active Directory 網域服務 (AD DS)。</span><span class="sxs-lookup"><span data-stu-id="e633c-125">The zone they use is the "Default zone / Windows integrated", which uses Active Directory Domain Services (AD DS).</span></span>
    
- <span data-ttu-id="e633c-126">搜尋編目帳戶-搜尋編目帳戶具有存取網站透過例如https://authoring.contoso.com:8000或https://www.contoso.com:8000。</span><span class="sxs-lookup"><span data-stu-id="e633c-126">Search Crawl Account — The search crawl account has access through sites such as https://authoring.contoso.com:8000 or https://www.contoso.com:8000.</span></span> <span data-ttu-id="e633c-127">它會使用的區域是 「 預設 」 區域 / Windows 整合 」，可使用 Windows NTLM 驗證使用 AD DS。</span><span class="sxs-lookup"><span data-stu-id="e633c-127">The zone it uses is the "Default zone / Windows integrated", which uses AD DS with Windows NTLM authentication.</span></span>
    
## <a name="server-farm"></a><span data-ttu-id="e633c-128">伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="e633c-128">Server farm</span></span>

<span data-ttu-id="e633c-129">使用者透過 Azure 存取伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="e633c-129">The users access the server farm through Azure.</span></span> <span data-ttu-id="e633c-130">伺服器陣列包含一或多個網頁伺服器。</span><span class="sxs-lookup"><span data-stu-id="e633c-130">The server farm contains one or more Web servers.</span></span>
  
## <a name="administration-site"></a><span data-ttu-id="e633c-131">管理網站</span><span class="sxs-lookup"><span data-stu-id="e633c-131">Administration site</span></span>

<span data-ttu-id="e633c-132">「 管理 」 網站包含數個應用程式伺服器，與使用管理中心網站的 web 應用程式的應用程式集區 (在範例應用程式集區 1) 通訊。</span><span class="sxs-lookup"><span data-stu-id="e633c-132">The administration site contains several application servers, which communicate with an Application Pool (Application Pool 1 in the example) that uses the web application Central Administration Site.</span></span> <span data-ttu-id="e633c-133">管理中心網站提供組織內的網站集合的存取。</span><span class="sxs-lookup"><span data-stu-id="e633c-133">The Central Administration Site provides access to site collections within the organization.</span></span>
  
<span data-ttu-id="e633c-134">「 管理 」 網站也包含 SQL 資料庫伺服器，也就是具有 SQL Server 安裝與設定為支援 SQL 叢集、 鏡像或 AlwaysOn 的資料庫伺服器 （AlwaysOn 僅適用於 SQL Server 2012）。</span><span class="sxs-lookup"><span data-stu-id="e633c-134">The administration site also contains SQL Database servers, which are database servers with SQL Server installed and configured to support SQL clustering, mirroring, or AlwaysOn (AlwaysOn applies to SQL Server 2012 only).</span></span>
  
## <a name="services"></a><span data-ttu-id="e633c-135">服務</span><span class="sxs-lookup"><span data-stu-id="e633c-135">Services</span></span>

<span data-ttu-id="e633c-136">設計範例網際網路資訊服務 (IIS) 網站，SharePoint Web 服務。</span><span class="sxs-lookup"><span data-stu-id="e633c-136">The design example shows an Internet Information Services (IIS) website, SharePoint Web Services.</span></span> <span data-ttu-id="e633c-137">SharePoint Web 服務包含三個服務、 使用者設定檔、 搜尋和受管理的中繼資料的應用程式集區 (應用程式集區 2)。</span><span class="sxs-lookup"><span data-stu-id="e633c-137">SharePoint Web Services contains an application pool (Application Pool 2) with three services, User Profile, Search, and Managed Metadata.</span></span>
  
<span data-ttu-id="e633c-138">在服務的網際網路網站的附註：</span><span class="sxs-lookup"><span data-stu-id="e633c-138">Notes on Services for Internet sites:</span></span>
  
> <span data-ttu-id="e633c-139">受管理的中繼資料，請務必選取 [**此服務應用程式是特定詞彙集的預設儲存位置**。</span><span class="sxs-lookup"><span data-stu-id="e633c-139">Managed Metadata — Be sure to select **This service application is the default storage location for column specific term sets**.</span></span>
    
> <span data-ttu-id="e633c-140">應用程式管理--我們不建議在 Azure 中的公用對向網際網路網站中使用應用程式。</span><span class="sxs-lookup"><span data-stu-id="e633c-140">App Management — We do not recommend using apps in a public-facing Internet site in Azure.</span></span>
    
## <a name="application-pools-and-web-applications"></a><span data-ttu-id="e633c-141">應用程式集區和 web 應用程式</span><span class="sxs-lookup"><span data-stu-id="e633c-141">Application pools and web applications</span></span>

<span data-ttu-id="e633c-142">在 Azure 中的 [預設] 群組會顯示應用程式集區 3 中，其中包含名為 Contoso 網站的 web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e633c-142">The Default Group in Azure shows Application Pool 3, which contains a web application named Contoso Sites.</span></span> <span data-ttu-id="e633c-143">此路徑型網站集合位於https://internal:8000。</span><span class="sxs-lookup"><span data-stu-id="e633c-143">This path-based site collection is located at https://internal:8000.</span></span>
  
## <a name="site-collections-and-sites"></a><span data-ttu-id="e633c-144">網站集合與網站</span><span class="sxs-lookup"><span data-stu-id="e633c-144">Site collections and sites</span></span>

<span data-ttu-id="e633c-145">應用程式集區中所包含的網站集合包括：</span><span class="sxs-lookup"><span data-stu-id="e633c-145">The site collections contained in the application pool include:</span></span>
  
- <span data-ttu-id="e633c-146">編目 （範例位置的主機命名型網站集合 1https://authoring.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="e633c-146">Host-named site collection 1 for crawling (example location https://authoring.contoso.com:8000)</span></span>
    
- <span data-ttu-id="e633c-147">主機命名型網站集合 2 的查詢 (範例位置https://www.contoso.com、 https://secure.contoso.com，https://www.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="e633c-147">Host-named site collection 2 for queries (sample locations https://www.contoso.com, https://secure.contoso.com, https://www.contoso.com:8000)</span></span>
    
- <span data-ttu-id="e633c-148">查詢的主機命名型網站集合 3 (範例位置https://assets.contoso.com、 https://secureassets.contoso.com，https://assets.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="e633c-148">Host-named site collection 3 for queries (sample locations https://assets.contoso.com, https://secureassets.contoso.com, https://assets.contoso.com:8000)</span></span>
    
## <a name="content-databases"></a><span data-ttu-id="e633c-149">內容資料庫</span><span class="sxs-lookup"><span data-stu-id="e633c-149">Content databases</span></span>

<span data-ttu-id="e633c-150">此範例顯示兩個內容資料庫。</span><span class="sxs-lookup"><span data-stu-id="e633c-150">The example shows two content databases.</span></span> <span data-ttu-id="e633c-151">另一個做為網站集合用於編目的 1 (https://authoring.contoso.com:8000)。</span><span class="sxs-lookup"><span data-stu-id="e633c-151">One is for the site collection 1 used for crawling (https://authoring.contoso.com:8000).</span></span> <span data-ttu-id="e633c-152">另一個是這兩個網站集合 2 和 3 用於查詢的 (https://www.contoso.com、 https://secure.contoso.com、 https://www.contoso.com:8000，或https://assets.contoso.com、 https://secureassets.contoso.com， https://assets.contoso.com:8000)。</span><span class="sxs-lookup"><span data-stu-id="e633c-152">The other is for the two site collections 2 and 3 used for queries (https://www.contoso.com, https://secure.contoso.com, https://www.contoso.com:8000, or https://assets.contoso.com, https://secureassets.contoso.com, https://assets.contoso.com:8000).</span></span>
  
## <a name="zones-and-urls"></a><span data-ttu-id="e633c-153">區域及 URL</span><span class="sxs-lookup"><span data-stu-id="e633c-153">Zones and URLs</span></span>

<span data-ttu-id="e633c-154">此範例顯示具有相關聯負載平衡 Url 所使用的不同使用者帳戶的三個區域。</span><span class="sxs-lookup"><span data-stu-id="e633c-154">The example shows three zones with the associated load-balanced URLs that are used by different user accounts.</span></span> 
  
<span data-ttu-id="e633c-155">區域及 Url 的第一個清單與網站集合 1，並包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="e633c-155">The first list of zones and URLs is related to site collection 1, and it contains the following information:</span></span>
  
- <span data-ttu-id="e633c-156">使用者對網站作者</span><span class="sxs-lookup"><span data-stu-id="e633c-156">Users - Site authors</span></span>
    
- <span data-ttu-id="e633c-157">區域的預設值</span><span class="sxs-lookup"><span data-stu-id="e633c-157">Zone - Default</span></span>
    
- <span data-ttu-id="e633c-158">負載平衡 URL-https://authoring.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="e633c-158">Load-balanced URL - https://authoring.contoso.com:8000</span></span>
    
<span data-ttu-id="e633c-159">區域及 Url 的第二個清單三個不同的區域中有三種不同類型的使用者。</span><span class="sxs-lookup"><span data-stu-id="e633c-159">The second list of zones and URLs has three different types of users in three different zones.</span></span> <span data-ttu-id="e633c-160">它與網站集合 2，並包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="e633c-160">It is related to site collection 2, and it contains the following information:</span></span>
  
<span data-ttu-id="e633c-161">第一個區域中：</span><span class="sxs-lookup"><span data-stu-id="e633c-161">First zone:</span></span>
  
- <span data-ttu-id="e633c-162">使用者對網站作者</span><span class="sxs-lookup"><span data-stu-id="e633c-162">Users - Site authors</span></span>
    
- <span data-ttu-id="e633c-163">區域的預設值</span><span class="sxs-lookup"><span data-stu-id="e633c-163">Zone - Default</span></span>
    
- <span data-ttu-id="e633c-164">負載平衡 URL-https://www.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="e633c-164">Load-balanced URL - https://www.contoso.com:8000</span></span>
    
<span data-ttu-id="e633c-165">第二個區域：</span><span class="sxs-lookup"><span data-stu-id="e633c-165">Second zone:</span></span>
  
- <span data-ttu-id="e633c-166">使用者-匿名的客戶</span><span class="sxs-lookup"><span data-stu-id="e633c-166">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="e633c-167">區域-網際網路</span><span class="sxs-lookup"><span data-stu-id="e633c-167">Zone - Internet</span></span>
    
- <span data-ttu-id="e633c-168">負載平衡 URL-https://www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="e633c-168">Load-balanced URL - https://www.contoso.com</span></span>
    
<span data-ttu-id="e633c-169">第三個區域：</span><span class="sxs-lookup"><span data-stu-id="e633c-169">Third zone:</span></span>
  
- <span data-ttu-id="e633c-170">使用者-已驗證的客戶</span><span class="sxs-lookup"><span data-stu-id="e633c-170">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="e633c-171">區域的外部網路</span><span class="sxs-lookup"><span data-stu-id="e633c-171">Zone - Extranet</span></span>
    
- <span data-ttu-id="e633c-172">負載平衡 URL-https://secure.contoso.com</span><span class="sxs-lookup"><span data-stu-id="e633c-172">Load-balanced URL - https://secure.contoso.com</span></span>
    
<span data-ttu-id="e633c-173">區域及 Url 的第三個清單三個不同的區域中有三種不同類型的使用者。</span><span class="sxs-lookup"><span data-stu-id="e633c-173">The third list of zones and URLs has three different types of users in three different zones.</span></span> <span data-ttu-id="e633c-174">它與網站集合第 3，它會包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="e633c-174">It is related to site collection 3, and it contains the following information:</span></span>
  
<span data-ttu-id="e633c-175">第一個區域中：</span><span class="sxs-lookup"><span data-stu-id="e633c-175">First zone:</span></span>
  
- <span data-ttu-id="e633c-176">使用者對網站作者</span><span class="sxs-lookup"><span data-stu-id="e633c-176">Users - Site authors</span></span>
    
- <span data-ttu-id="e633c-177">區域-網際網路</span><span class="sxs-lookup"><span data-stu-id="e633c-177">Zone - Internet</span></span>
    
- <span data-ttu-id="e633c-178">負載平衡 URL-https://assets.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="e633c-178">Load-balanced URL - https://assets.contoso.com:8000</span></span>
    
<span data-ttu-id="e633c-179">第二個區域：</span><span class="sxs-lookup"><span data-stu-id="e633c-179">Second zone:</span></span>
  
- <span data-ttu-id="e633c-180">使用者-匿名的客戶</span><span class="sxs-lookup"><span data-stu-id="e633c-180">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="e633c-181">區域-網際網路</span><span class="sxs-lookup"><span data-stu-id="e633c-181">Zone - Internet</span></span>
    
- <span data-ttu-id="e633c-182">負載平衡 URL-https://assets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="e633c-182">Load-balanced URL - https://assets.contoso.com</span></span>
    
<span data-ttu-id="e633c-183">第三個區域：</span><span class="sxs-lookup"><span data-stu-id="e633c-183">Third zone:</span></span>
  
- <span data-ttu-id="e633c-184">使用者-已驗證的客戶</span><span class="sxs-lookup"><span data-stu-id="e633c-184">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="e633c-185">區域的外部網路</span><span class="sxs-lookup"><span data-stu-id="e633c-185">Zone - Extranet</span></span>
    
- <span data-ttu-id="e633c-186">負載平衡 URL-https://secureassets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="e633c-186">Load-balanced URL - https://secureassets.contoso.com</span></span>
    

