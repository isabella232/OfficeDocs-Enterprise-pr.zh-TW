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
f1.keywords:
- NOCSH
description: 本文是圖表的名為 SharePoint 2013 網際網路網站，在 Microsoft Azure 中易於存取的文字版本。
ms.openlocfilehash: a68c5f8a0e92c45e3c33caaca77be0d841aa6003
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843894"
---
# <a name="accessible-diagram---internet-sites-in-microsoft-azure-for-sharepoint-2013"></a><span data-ttu-id="b0383-103">易於存取的圖表-Microsoft Azure 中的 SharePoint 2013 的網際網路網站</span><span class="sxs-lookup"><span data-stu-id="b0383-103">Accessible diagram - Internet sites in Microsoft Azure for SharePoint 2013</span></span>

<span data-ttu-id="b0383-104">**摘要：** 本文是圖表的名為 SharePoint 2013 網際網路網站，在 Microsoft Azure 中易於存取的文字版本。</span><span class="sxs-lookup"><span data-stu-id="b0383-104">**Summary:** This article is an accessible text version of the diagram named Internet sites in Microsoft Azure for SharePoint 2013.</span></span>
  
<span data-ttu-id="b0383-105">此海報說明，並說明如何公開網際網路網站權益從雲端彈性和客戶帳戶的 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="b0383-105">This poster describes and illustrates how public-facing Internet sites benefit from cloud elasticity and Azure AD for customer accounts.</span></span> <span data-ttu-id="b0383-106">有六個不同的案例，說明網際網路網站受益於 Azure 的方式：</span><span class="sxs-lookup"><span data-stu-id="b0383-106">There are six different scenarios that describe how Internet sites benefit from Azure:</span></span> 
  
- <span data-ttu-id="b0383-107">設計和大小的伺服器陣列拓撲。</span><span class="sxs-lookup"><span data-stu-id="b0383-107">Design and size the farm topology.</span></span> 
    
- <span data-ttu-id="b0383-108">微調 azure。</span><span class="sxs-lookup"><span data-stu-id="b0383-108">Fine-tune for Azure.</span></span> 
    
- <span data-ttu-id="b0383-109">選擇 [Active Directory 模型。</span><span class="sxs-lookup"><span data-stu-id="b0383-109">Choose the Active Directory model.</span></span> 
    
- <span data-ttu-id="b0383-110">針對身分識別管理、 區域及驗證所設計。</span><span class="sxs-lookup"><span data-stu-id="b0383-110">Design for identity management, zones, and authentication.</span></span> 
    
- <span data-ttu-id="b0383-111">設計站台和跨網站發佈的 Url。</span><span class="sxs-lookup"><span data-stu-id="b0383-111">Design sites and URLs for cross-site publishing.</span></span> 
    
- <span data-ttu-id="b0383-112">設計 Azure 環境。</span><span class="sxs-lookup"><span data-stu-id="b0383-112">Design the Azure environment.</span></span> 
    
## <a name="design-and-size-the-farm-topology"></a><span data-ttu-id="b0383-113">設計和大小的伺服器陣列拓撲</span><span class="sxs-lookup"><span data-stu-id="b0383-113">Design and size the farm topology</span></span>

<span data-ttu-id="b0383-114">用於 TechNet 上的 SharePoint 2013 的拓撲、 容量及效能的指引來設計伺服器陣列拓撲。</span><span class="sxs-lookup"><span data-stu-id="b0383-114">Use the topology, capacity, and performance guidance for SharePoint 2013 on TechNet to design the farm topology.</span></span> 
  
<span data-ttu-id="b0383-115">請確定您在設計伺服器陣列符合容量和效能目標。</span><span class="sxs-lookup"><span data-stu-id="b0383-115">Ensure the farm you design meets the objectives for capacity and performance.</span></span> 
  
### <a name="example-medium-internet-sites-farm-85-page-views-per-second"></a><span data-ttu-id="b0383-116">範例： 中型網際網路網站 」 伺服器陣列 （~ 85] 頁面上每秒的檢視表）</span><span class="sxs-lookup"><span data-stu-id="b0383-116">Example: Medium Internet Sites farm (~85 page views per second)</span></span>

<span data-ttu-id="b0383-117">此伺服器陣列提供容錯 SharePoint 2013 伺服器陣列之搜尋拓撲最適合的主體包含 3400000 項目。</span><span class="sxs-lookup"><span data-stu-id="b0383-117">This farm provides a fault-tolerant SharePoint 2013 search farm topology that is optimized for a corpus that contains 3,400,000 items.</span></span> 
  
<span data-ttu-id="b0383-118">範例伺服器陣列處理根據語言，每秒 100-200 份文件，其可容納 85 每秒的第二個和 100 個查詢的網頁檢視。</span><span class="sxs-lookup"><span data-stu-id="b0383-118">The example farm processes 100-200 documents per second, depending on the language, and it accommodates 85 page views per second and 100 queries per second.</span></span> 
  
<span data-ttu-id="b0383-119">隨附圖顯示中型網際網路網站 」 伺服器陣列與伺服器的三種：</span><span class="sxs-lookup"><span data-stu-id="b0383-119">The accompanying diagram shows a medium internet sites farm with three types of servers:</span></span> 
  
- <span data-ttu-id="b0383-120">網頁伺服器</span><span class="sxs-lookup"><span data-stu-id="b0383-120">Web servers</span></span> 
    
- <span data-ttu-id="b0383-121">應用程式伺服器</span><span class="sxs-lookup"><span data-stu-id="b0383-121">Application servers</span></span> 
    
- <span data-ttu-id="b0383-122">資料庫伺服器</span><span class="sxs-lookup"><span data-stu-id="b0383-122">Database servers</span></span> 
    
#### <a name="web-servers"></a><span data-ttu-id="b0383-123">網頁伺服器</span><span class="sxs-lookup"><span data-stu-id="b0383-123">Web servers</span></span>

<span data-ttu-id="b0383-124">在 [web 伺服器] 區段中，有三部網頁伺服器、 主機 A、 主機 B 和主機 c。每部網頁伺服器包含分散式快取、 使用者設定檔、 受管理中繼資料，以及查詢處理功能。</span><span class="sxs-lookup"><span data-stu-id="b0383-124">In the web servers section, there are three web servers, Host A, Host B, and Host C. Each web server contains a distributed cache, user profiles, managed metadata, and query processing capabilities.</span></span> <span data-ttu-id="b0383-125">它們也包含索引分割區複本中每一部伺服器。</span><span class="sxs-lookup"><span data-stu-id="b0383-125">They also contain an index partition replica that is in each server.</span></span> 
  
<span data-ttu-id="b0383-126">若要向外延展，新增額外的網頁伺服器的相同功能，可以針對其他 28] 頁面上檢視每秒。</span><span class="sxs-lookup"><span data-stu-id="b0383-126">To scale out, add an additional web server with the same capabilities, which allows for an additional 28 page views per second.</span></span> 
  
#### <a name="application-servers"></a><span data-ttu-id="b0383-127">應用程式伺服器</span><span class="sxs-lookup"><span data-stu-id="b0383-127">Application servers</span></span>

<span data-ttu-id="b0383-128">在 [應用程式伺服器] 區段中，有三個應用程式伺服器主機 D 主機 E、 及主機 F.主機 D 包含編目、 管理、 分析及內容處理元件。</span><span class="sxs-lookup"><span data-stu-id="b0383-128">In the application servers section, there are three application servers, Host D, Host E, and Host F. Host D contains Crawl, Admin, Analytics, and Content processing components.</span></span> <span data-ttu-id="b0383-129">主機 E 包含編目、 系統管理員及內容處理元件。</span><span class="sxs-lookup"><span data-stu-id="b0383-129">Host E contains Crawl, Admin, and Content processing components.</span></span> <span data-ttu-id="b0383-130">主機 F 包含編目和內容處理元件。</span><span class="sxs-lookup"><span data-stu-id="b0383-130">Host F contains Crawl and Content processing components.</span></span> 
  
<span data-ttu-id="b0383-131">若要向外擴充，新增編目元件與內容處理元件來處理每秒額外 40 文件的一部應用程式伺服器。</span><span class="sxs-lookup"><span data-stu-id="b0383-131">To scale out, add one application server with a crawl component and a content processing component to process an additional 40 documents per second.</span></span> 
  
#### <a name="database-servers"></a><span data-ttu-id="b0383-132">資料庫伺服器</span><span class="sxs-lookup"><span data-stu-id="b0383-132">Database servers</span></span>

<span data-ttu-id="b0383-133">在 [資料庫伺服器] 區段中，有兩部伺服器，主機 G、 H 主機資料庫伺服器位於成對的主應用程式的容錯能力。</span><span class="sxs-lookup"><span data-stu-id="b0383-133">In the database servers section, there are two servers, Host G and Host H. The database servers are in paired hosts for fault tolerance.</span></span> 
  
<span data-ttu-id="b0383-134">主機 G 包含所有 SharePoint 資料庫，包括搜尋管理資料庫、 連結 」 資料庫、 兩個編目資料庫、 分析資料庫及其他所有 SharePoint 資料庫。</span><span class="sxs-lookup"><span data-stu-id="b0383-134">Host G contains all SharePoint database, including Search admin database, Link database, two Crawl databases, an Analytics database, and all other SharePoint databases.</span></span> <span data-ttu-id="b0383-135">主機 H 包含所有 SharePoint 資料庫，包括使用 SQL 叢集、 鏡像或 SQL Server 2012 AlwaysOn 的所有資料庫的備援副本。</span><span class="sxs-lookup"><span data-stu-id="b0383-135">Host H contains all SharePoint databases, including redundant copies of all databases using SQL clustering, mirroring, or SQL Server 2012 AlwaysOn.</span></span> 
  
## <a name="fine-tune-for-azure"></a><span data-ttu-id="b0383-136">Azure 微調</span><span class="sxs-lookup"><span data-stu-id="b0383-136">Fine-tune for Azure</span></span>

<span data-ttu-id="b0383-137">在 SharePoint 伺服器陣列可能需要微調的 Azure 的平台] 中的可用性設定組。</span><span class="sxs-lookup"><span data-stu-id="b0383-137">The SharePoint farm might need to be fine-tuned for availability sets in the Azure platform.</span></span> <span data-ttu-id="b0383-138">若要確保所有元件的高可用性，請確定所有具有相同設定的伺服器角色。</span><span class="sxs-lookup"><span data-stu-id="b0383-138">To ensure high availability of all components, ensure that the server roles are all identically configured.</span></span> 
  
<span data-ttu-id="b0383-139">在圖表中的範例拓撲：</span><span class="sxs-lookup"><span data-stu-id="b0383-139">In the example topology in the diagram:</span></span> 
  
- <span data-ttu-id="b0383-140">具有相同設定網頁伺服器和資料庫伺服器。</span><span class="sxs-lookup"><span data-stu-id="b0383-140">The web servers and the database servers are identically configured.</span></span> 
    
- <span data-ttu-id="b0383-141">不具有相同設定三個應用程式伺服器。</span><span class="sxs-lookup"><span data-stu-id="b0383-141">The three application servers are not identically configured.</span></span> <span data-ttu-id="b0383-142">這些伺服器角色需要在 Azure 中的可用性微調設定。</span><span class="sxs-lookup"><span data-stu-id="b0383-142">These server roles require fine tuning for availability sets in Azure.</span></span> 
    
### <a name="before"></a><span data-ttu-id="b0383-143">之前</span><span class="sxs-lookup"><span data-stu-id="b0383-143">Before</span></span>

<span data-ttu-id="b0383-144">圖表的上半部會顯示在 Azure 中設定 SharePoint 伺服器陣列之前具有已微調可用性。</span><span class="sxs-lookup"><span data-stu-id="b0383-144">The top portion of the diagram shows the SharePoint farm before it has been fine-tuned for availability sets in Azure.</span></span> <span data-ttu-id="b0383-145">在圖表中，三個主機應用程式伺服器都不具有相同設定。</span><span class="sxs-lookup"><span data-stu-id="b0383-145">In the diagram, the three host application servers are not identically configured.</span></span> <span data-ttu-id="b0383-146">元件數目取決於伺服器陣列的效能與容量目標。</span><span class="sxs-lookup"><span data-stu-id="b0383-146">The number of components is determined by the performance and capacity targets for the farm.</span></span> <span data-ttu-id="b0383-147">三部伺服器設定如下：</span><span class="sxs-lookup"><span data-stu-id="b0383-147">The three servers are configured as follows:</span></span> 
  
- <span data-ttu-id="b0383-148">設定主機 D 應用程式伺服器是編目、 管理、 分析及內容處理角色。</span><span class="sxs-lookup"><span data-stu-id="b0383-148">Host D application server is configured with Crawl, Admin, Analytics, and Content processing roles.</span></span> 
    
- <span data-ttu-id="b0383-149">設定主機 E 應用程式伺服器是編目、 系統管理員及內容處理角色。</span><span class="sxs-lookup"><span data-stu-id="b0383-149">Host E application server is configured with Crawl, Admin, and Content processing roles.</span></span> 
    
- <span data-ttu-id="b0383-150">設定主機 F 應用程式伺服器是編目和內容處理角色。</span><span class="sxs-lookup"><span data-stu-id="b0383-150">Host F application server is configured with Crawl and Content processing roles.</span></span> 
    
### <a name="after"></a><span data-ttu-id="b0383-151">之後</span><span class="sxs-lookup"><span data-stu-id="b0383-151">After</span></span>

<span data-ttu-id="b0383-152">這部分的圖表顯示在 Azure 中設定 SharePoint 伺服器陣列之後有已微調可用性。</span><span class="sxs-lookup"><span data-stu-id="b0383-152">This part of the diagram shows the SharePoint farm after it has been fine-tuned for availability sets in Azure.</span></span> <span data-ttu-id="b0383-153">Azure 能否這種架構，我們將所有的三部伺服器上複寫的四個元件。</span><span class="sxs-lookup"><span data-stu-id="b0383-153">To adapt this architecture for Azure, we'll replicate the four components across all three servers.</span></span> <span data-ttu-id="b0383-154">這會增加以外的功能所需的效能與容量的元件數目。</span><span class="sxs-lookup"><span data-stu-id="b0383-154">This increases the number of components beyond what is necessary for performance and capacity.</span></span> <span data-ttu-id="b0383-155">缺點是這種設計可確保當這些三部虛擬機器會指派給一個可用性設定組 Azure 的平台] 中的所有四個元件的高可用性。</span><span class="sxs-lookup"><span data-stu-id="b0383-155">The tradeoff is that this design ensures high availability of all four components in the Azure platform when these three virtual machines are assigned to an availability set.</span></span> 
  
<span data-ttu-id="b0383-156">三部伺服器都設定為所有具有編目、 管理、 分析及內容處理角色。</span><span class="sxs-lookup"><span data-stu-id="b0383-156">The three servers are configured to all have the Crawl, Admin, Analytics, and Content processing roles.</span></span> 
  
## <a name="choose-the-active-directory-model"></a><span data-ttu-id="b0383-157">選擇 [Active Directory 模型</span><span class="sxs-lookup"><span data-stu-id="b0383-157">Choose the Active Directory model</span></span>

<span data-ttu-id="b0383-158">所有的 SharePoint 解決方案需要 Windows Active Directory 網域服務 (AD DS)。</span><span class="sxs-lookup"><span data-stu-id="b0383-158">All SharePoint solutions require Windows Active Directory Domain Services (AD DS).</span></span> <span data-ttu-id="b0383-159">在這個階段中，有兩個選項可在 Azure 中的 SharePoint 解決方案。</span><span class="sxs-lookup"><span data-stu-id="b0383-159">At this time, there are two options for SharePoint solutions in Azure.</span></span> 
  
- <span data-ttu-id="b0383-160">選項 1： 專用的網域，您可對支援 SharePoint 伺服器陣列的 Azure 部署專用和隔離網域。</span><span class="sxs-lookup"><span data-stu-id="b0383-160">Option 1: Dedicated domain — You can deploy a dedicated and isolated domain to Azure to support a SharePoint farm.</span></span> <span data-ttu-id="b0383-161">這是很好的選擇的公用對向網際網路網站。</span><span class="sxs-lookup"><span data-stu-id="b0383-161">This is a good choice for public-facing Internet sites.</span></span> 
    
- <span data-ttu-id="b0383-162">選項 2： 擴充透過站台對站 VPN 連線的內部部署網域。</span><span class="sxs-lookup"><span data-stu-id="b0383-162">Option 2: Extend the on-premises domain through a site-to-site VPN connection.</span></span> <span data-ttu-id="b0383-163">當您擴充透過站台對站 VPN 連線的內部部署網域時，使用者會存取 SharePoint 伺服器陣列，好像它是裝載於內部。</span><span class="sxs-lookup"><span data-stu-id="b0383-163">When you extend the on-premises domain through a site-to-site VPN connection, users access the SharePoint farm as if it were hosted on-premises.</span></span> <span data-ttu-id="b0383-164">您可以利用您現有的 Active Directory 和 DNS 實作。</span><span class="sxs-lookup"><span data-stu-id="b0383-164">You can take advantage of your existing Active Directory and DNS implementations.</span></span> 
    
## <a name="design-for-identity-management-zones-and-authentication"></a><span data-ttu-id="b0383-165">設計的身分識別管理、 區域及驗證</span><span class="sxs-lookup"><span data-stu-id="b0383-165">Design for identity management, zones, and authentication</span></span>

### <a name="design-for-accounts-and-authentication"></a><span data-ttu-id="b0383-166">帳戶和驗證的設計</span><span class="sxs-lookup"><span data-stu-id="b0383-166">Design for accounts and authentication</span></span>

<span data-ttu-id="b0383-167">決定如何將受管理帳戶和將使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="b0383-167">Determine how accounts will be managed and which type of authentication will be used.</span></span> 
  
#### <a name="accounts-for-site-developers-and-authors"></a><span data-ttu-id="b0383-168">網站開發人員和作者帳戶</span><span class="sxs-lookup"><span data-stu-id="b0383-168">Accounts for site developers and authors</span></span>

- <span data-ttu-id="b0383-169">將帳戶新增至 Azure 中的網域。</span><span class="sxs-lookup"><span data-stu-id="b0383-169">Add accounts to the domain in Azure.</span></span> 
    
- <span data-ttu-id="b0383-170">使用內部部署 Active Directory Federation Services (AD FS) 同盟內部 Azure 中的網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="b0383-170">Use Active Directory Federation Services (AD FS) on premises to federate the internal accounts to the domain in Azure.</span></span> 
    
- <span data-ttu-id="b0383-171">如果設計包含站台對站 VPN 連線，請使用內部帳戶。</span><span class="sxs-lookup"><span data-stu-id="b0383-171">If the design includes a site-to-site VPN connection, use the internal accounts.</span></span> 
    
#### <a name="accounts-for-customers"></a><span data-ttu-id="b0383-172">客戶的帳戶</span><span class="sxs-lookup"><span data-stu-id="b0383-172">Accounts for customers</span></span>

- <span data-ttu-id="b0383-173">使用 Azure Active Directory。</span><span class="sxs-lookup"><span data-stu-id="b0383-173">Use Azure Active Directory.</span></span> 
    
- <span data-ttu-id="b0383-174">使用不同的 SAML 型提供者。</span><span class="sxs-lookup"><span data-stu-id="b0383-174">Use a different SAML-based provider.</span></span> 
    
### <a name="design-for-zones"></a><span data-ttu-id="b0383-175">設計的區域</span><span class="sxs-lookup"><span data-stu-id="b0383-175">Design for zones</span></span>

<span data-ttu-id="b0383-176">在 SharePoint 2013 中的身分識別管理是作為因素納入的區域及驗證設定。</span><span class="sxs-lookup"><span data-stu-id="b0383-176">In SharePoint 2013, identity management is factored into the configuration of zones and authentication.</span></span> 
  
<span data-ttu-id="b0383-177">此設計中提供清楚的區隔的客戶帳戶從所有其他帳戶。</span><span class="sxs-lookup"><span data-stu-id="b0383-177">This design provides clear separation of customer accounts from all other accounts.</span></span> 
  
- <span data-ttu-id="b0383-178">此設計如果您想使用客戶帳戶被處理完全不同的內部帳戶作者和網站開發。</span><span class="sxs-lookup"><span data-stu-id="b0383-178">Use this design if you want customer accounts to be treated entirely different from the internal accounts for authors and site developers.</span></span> 
    
- <span data-ttu-id="b0383-179">藉由使用此設計中，您可以使用區域原則，以限制 web 應用程式內的客戶動作。</span><span class="sxs-lookup"><span data-stu-id="b0383-179">By using this design, you can use zone policies to limit customer actions within a web application.</span></span> 
    
- <span data-ttu-id="b0383-180">這項設計會導致客戶帳戶和內部帳戶不同的 Url。</span><span class="sxs-lookup"><span data-stu-id="b0383-180">This design results in different URLs for customer accounts and internal accounts.</span></span> 
    
<span data-ttu-id="b0383-181">在此範例中：</span><span class="sxs-lookup"><span data-stu-id="b0383-181">In this example:</span></span> 
  
- <span data-ttu-id="b0383-182">設定內部帳戶的 「 預設 」 區域。</span><span class="sxs-lookup"><span data-stu-id="b0383-182">Configure the default zone for internal accounts.</span></span> 
    
- <span data-ttu-id="b0383-183">設定已驗證的客戶存取的外部網路區域。</span><span class="sxs-lookup"><span data-stu-id="b0383-183">Configure the extranet zone for customer authenticated access.</span></span> <span data-ttu-id="b0383-184">使用 Azure Active Directory (AD) 客戶帳戶，或使用不同的 SAML 型提供者。</span><span class="sxs-lookup"><span data-stu-id="b0383-184">Use Azure Active Directory (AD) for customer accounts, or use a different SAML-based provider.</span></span> 
    
- <span data-ttu-id="b0383-185">設定匿名存取的網際網路區域。</span><span class="sxs-lookup"><span data-stu-id="b0383-185">Configure the Internet zone for anonymous access.</span></span> 
    
<span data-ttu-id="b0383-186">請勿使用所有已驗證的使用者設定為使用 「 預設 」 區域中的兩個區域設計。</span><span class="sxs-lookup"><span data-stu-id="b0383-186">Don't use a two-zone design in which all authenticated users are configured to use the default zone.</span></span> 
  
<span data-ttu-id="b0383-187">隨附的圖顯示內部的中間三個區域設計和客戶帳戶。</span><span class="sxs-lookup"><span data-stu-id="b0383-187">The accompanying diagram shows a three-zone design with separation of internal and customer accounts.</span></span> 
  
<span data-ttu-id="b0383-188">訪客和客戶透過其中一個兩個區域的 web 應用程式來存取 SharePoint 2013 伺服器陣列中的 Azure AD 租用戶。</span><span class="sxs-lookup"><span data-stu-id="b0383-188">Visitors and customers access the Azure AD Tenant in the SharePoint 2013 farm through web applications in one of two zones.</span></span> <span data-ttu-id="b0383-189">兩個區域包含：</span><span class="sxs-lookup"><span data-stu-id="b0383-189">The two zones include:</span></span> 
  
- <span data-ttu-id="b0383-190">匿名使用者的區域： 網際網路</span><span class="sxs-lookup"><span data-stu-id="b0383-190">Zone: Internet for anonymous users</span></span> 
    
- <span data-ttu-id="b0383-191">區域： 已驗證使用者的外部網路</span><span class="sxs-lookup"><span data-stu-id="b0383-191">Zone: Extranet for authenticated users</span></span> 
    
<span data-ttu-id="b0383-192">使用內部帳戶的使用者會存取 Azure Active Directory 租用戶從 AD DS 並在內部部署環境透過 VPN 通道中的 AD FS 到 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="b0383-192">Users with internal accounts access the Azure Active Directory Tenant from AD DS and AD FS in the on-premises environment through the VPN tunnel to Azure AD.</span></span> <span data-ttu-id="b0383-193">「 預設 」 區域提供 Windows 驗證 (NTLM)。</span><span class="sxs-lookup"><span data-stu-id="b0383-193">The Default zone provides Windows Authentication (NTLM).</span></span> 
  
### <a name="design-for-connecting-to-azure-ad"></a><span data-ttu-id="b0383-194">設計以連線到 Azure AD</span><span class="sxs-lookup"><span data-stu-id="b0383-194">Design for connecting to Azure AD</span></span>

 <span data-ttu-id="b0383-195">Azure AD 提供雲端服務的身分識別管理及存取控制功能。</span><span class="sxs-lookup"><span data-stu-id="b0383-195">Azure AD provides identity management and access control capabilities for cloud services.</span></span> <span data-ttu-id="b0383-196">功能包括目錄資料和一組核心的身分識別服務，包括使用者登入程序、 驗證服務，並使用 AD FS 的雲端式存放區。</span><span class="sxs-lookup"><span data-stu-id="b0383-196">Capabilities include a cloud-based store for directory data and a core set of identity services, including user logon processes, authentication services, and AD FS.</span></span> <span data-ttu-id="b0383-197">隨附於 Azure AD 輕易地識別服務整合內部部署 AD DS 和完全支援協力廠商身分識別提供者。</span><span class="sxs-lookup"><span data-stu-id="b0383-197">The identity services that are included with Azure AD easily integrate with your on-premises AD DS deployments and fully support third-party identity providers.</span></span>
  
<span data-ttu-id="b0383-198">隨附的圖會顯示下列案例：</span><span class="sxs-lookup"><span data-stu-id="b0383-198">The accompanying diagram shows the following scenario:</span></span> 
  
<span data-ttu-id="b0383-199">當與 Azure Active Directory 整合 SharePoint 2013，Azure 存取控制服務 (ACS) 會有兩種用途：</span><span class="sxs-lookup"><span data-stu-id="b0383-199">When integrating SharePoint 2013 with Azure Active Directory, an Azure Access Control Service (ACS) serves two purposes:</span></span> 
  
-  <span data-ttu-id="b0383-200">Azure AD 使用 SAML 2.0 及 SharePoint 只適用於 SAML 1.1 版。</span><span class="sxs-lookup"><span data-stu-id="b0383-200">Azure AD uses SAML 2.0, and SharePoint only works with SAML 1.1.</span></span> <span data-ttu-id="b0383-201">ACS 瞭解這兩種格式，並做為轉換 SharePoint 和 Azure AD 之間的 token 格式媒介。</span><span class="sxs-lookup"><span data-stu-id="b0383-201">ACS understands both formats and serves as the intermediary to transform the token formats between SharePoint and Azure AD.</span></span>
    
- <span data-ttu-id="b0383-202">ACS 會取代身分識別提供者 security token service (IP-STS) 此 SAML 案例的需求。</span><span class="sxs-lookup"><span data-stu-id="b0383-202">ACS replaces the need for the identity provider security token service (IP-STS) for this SAML scenario.</span></span> 
    
<span data-ttu-id="b0383-203">如需詳細資訊，請參閱 TechNet library 中的設定 Azure AD 中使用 SharePoint 2013。</span><span class="sxs-lookup"><span data-stu-id="b0383-203">For more information, see Configure Azure AD with SharePoint 2013 in the TechNet library.</span></span> 
  
## <a name="design-sites-and-urls-for-cross-site-publishing"></a><span data-ttu-id="b0383-204">設計適用於跨網站發佈功能的網站與 Url</span><span class="sxs-lookup"><span data-stu-id="b0383-204">Design sites and URLs for cross-site publishing</span></span>

<span data-ttu-id="b0383-205">一個 web 應用程式的設計建議發佈案例。</span><span class="sxs-lookup"><span data-stu-id="b0383-205">A one web-application design is recommended for publishing scenarios.</span></span> 
  
- <span data-ttu-id="b0383-206">製作與發佈網站位於相同的 web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="b0383-206">Both authoring and publishing sites are in the same web application.</span></span> 
    
- <span data-ttu-id="b0383-207">跨網站發佈用來發佈資產。</span><span class="sxs-lookup"><span data-stu-id="b0383-207">Cross-site publishing is used to publish assets.</span></span> 
    
<span data-ttu-id="b0383-208">使用路徑型與主機命名型網站集合。</span><span class="sxs-lookup"><span data-stu-id="b0383-208">Use path-based and host-named site collections.</span></span> 
  
- <span data-ttu-id="b0383-209">一個根網站集合是必要條件。</span><span class="sxs-lookup"><span data-stu-id="b0383-209">A root site collection is a requirement.</span></span> <span data-ttu-id="b0383-210">建立為路徑型網站的 [此網站]。</span><span class="sxs-lookup"><span data-stu-id="b0383-210">Create this site as a path-based site.</span></span> 
    
- <span data-ttu-id="b0383-211">建立為主機命名型網站集合的所有其他網站集合。</span><span class="sxs-lookup"><span data-stu-id="b0383-211">Create all other site collections as host-named site collections.</span></span> 
    
<span data-ttu-id="b0383-212">Web 應用程式和根網站 Url</span><span class="sxs-lookup"><span data-stu-id="b0383-212">Web application and root site URLs</span></span> 
  
- <span data-ttu-id="b0383-213">使用 web 應用程式 URL 的內部名稱。</span><span class="sxs-lookup"><span data-stu-id="b0383-213">Use an internal name for the web application URL.</span></span> <span data-ttu-id="b0383-214">除非指定不同的名稱，SharePoint 會使用本機電腦名稱做為預設名稱。</span><span class="sxs-lookup"><span data-stu-id="b0383-214">SharePoint uses the local machine name as the default name unless a different name is specified.</span></span> <span data-ttu-id="b0383-215">您可以使用網域名稱保留內部網路環境。</span><span class="sxs-lookup"><span data-stu-id="b0383-215">You can use a domain name that is reserved for the internal network environment.</span></span> 
    
- <span data-ttu-id="b0383-216">建立 web 應用程式時，SharePoint 會將指派非標準連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="b0383-216">SharePoint assigns a nonstandard port number when the web application is created.</span></span> <span data-ttu-id="b0383-217">使用此連接埠號碼，而不是連接埠 80 或連接埠 443。</span><span class="sxs-lookup"><span data-stu-id="b0383-217">Use this port number instead of port 80 or port 443.</span></span> <span data-ttu-id="b0383-218">或使用不同，但非標準連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="b0383-218">Or use a different but nonstandard port number.</span></span> 
    
- <span data-ttu-id="b0383-219">根網站集合，也就是在路徑型網站集合使用相同的名稱和連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="b0383-219">Use the same name and port number for the root site collection, which is a path-based site collection.</span></span> 
    
<span data-ttu-id="b0383-220">隨附的圖顯示應用程式集區服務，例如搜尋與網站集合使用的 web 應用程式互動。</span><span class="sxs-lookup"><span data-stu-id="b0383-220">The accompanying diagram shows application pool services such as Search interacting with site collections using web applications.</span></span> <span data-ttu-id="b0383-221">顯示網站集合包括：</span><span class="sxs-lookup"><span data-stu-id="b0383-221">The site collections shown include:</span></span> 
  
- <span data-ttu-id="b0383-222">路徑型網站集合位於https://internal:8000（根網站）。</span><span class="sxs-lookup"><span data-stu-id="b0383-222">Path-based site collection located at https://internal:8000 (root site).</span></span> 
    
- <span data-ttu-id="b0383-223">編目： 主機命名型網站集合位於位址例如https://authoring.contoso.com:8000。</span><span class="sxs-lookup"><span data-stu-id="b0383-223">Crawl: Host-named site collections located at an address such as https://authoring.contoso.com:8000.</span></span> 
    
- <span data-ttu-id="b0383-224">查詢： 2 不同的主機命名型網站集合位於地址如下：</span><span class="sxs-lookup"><span data-stu-id="b0383-224">Queries: 2 separate Host-named site collections located at addresses such as:</span></span> 
    
  - https://www.contoso.com 
    
  - https://secure.contoso.com 
    
  - https://www.contoso.com:8000 
    
  - https://assets.contoso.com 
    
  - https://secureassets.contoso.com 
    
  - https://assets.contoso.com:8000 
    
## <a name="design-the-azure-environment"></a><span data-ttu-id="b0383-225">設計 Azure 環境</span><span class="sxs-lookup"><span data-stu-id="b0383-225">Design the Azure environment</span></span>

<span data-ttu-id="b0383-226">此範例架構包括下列元素：</span><span class="sxs-lookup"><span data-stu-id="b0383-226">This example architecture includes the following elements:</span></span> 
  
- <span data-ttu-id="b0383-227">站台對站 VPN 連線是選擇性的並延伸至 azure 虛擬網路的 DNS 環境與內部部署 Windows AD DS。</span><span class="sxs-lookup"><span data-stu-id="b0383-227">A site-to-site VPN connection is optional and extends the on-premises Windows AD DS and DNS environment to the virtual network in Azure.</span></span> 
    
- <span data-ttu-id="b0383-228">（選擇性） 用於在 Azure 中的專用的網域支援的 SharePoint 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="b0383-228">Optionally, use a dedicated domain in Azure to support the SharePoint farm.</span></span> 
    
- <span data-ttu-id="b0383-229">伺服器會分割到 Azure 的雲端服務角色為基礎。</span><span class="sxs-lookup"><span data-stu-id="b0383-229">Servers are split across Azure cloud services based on role.</span></span> 
    
- <span data-ttu-id="b0383-230">可用性設定組確保設定相同的伺服器角色的高的可用性。</span><span class="sxs-lookup"><span data-stu-id="b0383-230">Availability sets ensure high availability of identically configured server roles.</span></span> 
    
<span data-ttu-id="b0383-231">如需詳細資訊，請參閱下文 technet: Azure Architectures for SharePoint 解決方案。</span><span class="sxs-lookup"><span data-stu-id="b0383-231">For more information, see the following article on TechNet: Azure Architectures for SharePoint Solutions.</span></span> 
  
<span data-ttu-id="b0383-232">隨附圖與 Azure 虛擬網路連線內部部署環境的範例。</span><span class="sxs-lookup"><span data-stu-id="b0383-232">The accompanying diagram shows an example of an on-premises environment connecting with an Azure virtual network.</span></span> 
  
<span data-ttu-id="b0383-233">內部部署環境中，為 Azure 環境的選用性元素，包括下列元件：</span><span class="sxs-lookup"><span data-stu-id="b0383-233">Included in the on-premises environment, which is an optional element of the Azure environment, are the following components:</span></span> 
  
- <span data-ttu-id="b0383-234">Windows Server 2012 RRAS</span><span class="sxs-lookup"><span data-stu-id="b0383-234">Windows Server 2012 RRAS</span></span> 
    
- <span data-ttu-id="b0383-235">AD DS</span><span class="sxs-lookup"><span data-stu-id="b0383-235">AD DS</span></span> 
    
- <span data-ttu-id="b0383-236">從 Windows Server 及 AD DS VPN 閘道至作用中的 VPN 閘道子網路</span><span class="sxs-lookup"><span data-stu-id="b0383-236">A VPN gateway from Windows Server and AD DS to the Active VPN Gateway subnet</span></span> 
    
<span data-ttu-id="b0383-237">在 Azure 虛擬網路環境包含下列元件：</span><span class="sxs-lookup"><span data-stu-id="b0383-237">The Azure virtual network environment includes the following components:</span></span> 
  
- <span data-ttu-id="b0383-238">作用中的 VPN 閘道子網路 （重疊的內部部署環境，如果有的話）</span><span class="sxs-lookup"><span data-stu-id="b0383-238">The Active VPN Gateway subnet (overlapping with the on-premises environment, if applicable)</span></span> 
    
- <span data-ttu-id="b0383-239">雲端服務，包含 AD DS 和 DNS 可用性設定 （兩部伺服器）</span><span class="sxs-lookup"><span data-stu-id="b0383-239">Cloud service that includes AD DS and DNS availability set (two servers)</span></span> 
    
- <span data-ttu-id="b0383-240">雲端服務，包括前端伺服器的可用性設定 (三個 SharePoint server)，且應用程式伺服器的可用性設定 (三個 SharePoint server)</span><span class="sxs-lookup"><span data-stu-id="b0383-240">Cloud service that include the front-end server availability set (three SharePoint servers) and the App server availability set (three SharePoint servers)</span></span> 
    
- <span data-ttu-id="b0383-241">含有兩個資料庫可用性雲端服務設定</span><span class="sxs-lookup"><span data-stu-id="b0383-241">Cloud service that contains two database availability sets</span></span> 
    

