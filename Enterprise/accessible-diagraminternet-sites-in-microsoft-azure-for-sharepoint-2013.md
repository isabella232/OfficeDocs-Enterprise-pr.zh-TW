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
# <a name="accessible-diagram---internet-sites-in-microsoft-azure-for-sharepoint-2013"></a><span data-ttu-id="5a7a1-103">存取圖表-Microsoft Azure 中的 SharePoint 2013 的網際網路網站</span><span class="sxs-lookup"><span data-stu-id="5a7a1-103">Accessible diagram - Internet sites in Microsoft Azure for SharePoint 2013</span></span>

<span data-ttu-id="5a7a1-104">**摘要：** 本文是圖表的名為 Microsoft Azure 中的網際網路網站的 SharePoint 2013 可存取的文字版本。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-104">**Summary:** This article is an accessible text version of the diagram named Internet sites in Microsoft Azure for SharePoint 2013.</span></span>
  
<span data-ttu-id="5a7a1-p101">此海報說明及圖解如何公開網際網路網站福利從雲端 elasticity 和客戶帳戶的 Azure AD。有六個不同的案例說明網際網路網站獲益 Azure 的方式：</span><span class="sxs-lookup"><span data-stu-id="5a7a1-p101">This poster describes and illustrates how public-facing Internet sites benefit from cloud elasticity and Azure AD for customer accounts. There are six different scenarios that describe how Internet sites benefit from Azure:</span></span> 
  
- <span data-ttu-id="5a7a1-107">設計及調整大小的伺服器陣列拓撲。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-107">Design and size the farm topology.</span></span> 
    
- <span data-ttu-id="5a7a1-108">微調 azure。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-108">Fine-tune for Azure.</span></span> 
    
- <span data-ttu-id="5a7a1-109">選擇 [Active Directory 模型。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-109">Choose the Active Directory model.</span></span> 
    
- <span data-ttu-id="5a7a1-110">設計的身分識別管理、 區域及驗證。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-110">Design for identity management, zones, and authentication.</span></span> 
    
- <span data-ttu-id="5a7a1-111">設計網站和跨網站發佈的 Url。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-111">Design sites and URLs for cross-site publishing.</span></span> 
    
- <span data-ttu-id="5a7a1-112">設計 Azure 環境。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-112">Design the Azure environment.</span></span> 
    
## <a name="design-and-size-the-farm-topology"></a><span data-ttu-id="5a7a1-113">設計及調整大小的伺服器陣列拓撲</span><span class="sxs-lookup"><span data-stu-id="5a7a1-113">Design and size the farm topology</span></span>

<span data-ttu-id="5a7a1-114">使用設計的伺服器陣列拓撲 TechNet 上的 SharePoint 2013 的拓撲、 容量及效能指導。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-114">Use the topology, capacity, and performance guidance for SharePoint 2013 on TechNet to design the farm topology.</span></span> 
  
<span data-ttu-id="5a7a1-115">確定您設計的伺服器陣列符合容量和效能目標。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-115">Ensure the farm you design meets the objectives for capacity and performance.</span></span> 
  
### <a name="example-medium-internet-sites-farm-85-page-views-per-second"></a><span data-ttu-id="5a7a1-116">範例： 中型網際網路網站伺服器陣列 （~ 85 每秒網頁檢視）</span><span class="sxs-lookup"><span data-stu-id="5a7a1-116">Example: Medium Internet Sites farm (~85 page views per second)</span></span>

<span data-ttu-id="5a7a1-117">此伺服器陣列提供包含 3,400,000 的項目主體的功能已最佳化容錯 SharePoint 2013 搜尋伺服器陣列拓撲。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-117">This farm provides a fault-tolerant SharePoint 2013 search farm topology that is optimized for a corpus that contains 3,400,000 items.</span></span> 
  
<span data-ttu-id="5a7a1-118">範例伺服器陣列處理 100-200 每秒文件、 語言，並加以可容納每第二個和 100 個每秒查詢 85 網頁檢視。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-118">The example farm processes 100-200 documents per second, depending on the language, and it accommodates 85 page views per second and 100 queries per second.</span></span> 
  
<span data-ttu-id="5a7a1-119">隨附的圖顯示具有三種伺服器類型中型網際網路網站伺服器陣列：</span><span class="sxs-lookup"><span data-stu-id="5a7a1-119">The accompanying diagram shows a medium internet sites farm with three types of servers:</span></span> 
  
- <span data-ttu-id="5a7a1-120">網頁伺服器</span><span class="sxs-lookup"><span data-stu-id="5a7a1-120">Web servers</span></span> 
    
- <span data-ttu-id="5a7a1-121">應用程式伺服器</span><span class="sxs-lookup"><span data-stu-id="5a7a1-121">Application servers</span></span> 
    
- <span data-ttu-id="5a7a1-122">資料庫伺服器</span><span class="sxs-lookup"><span data-stu-id="5a7a1-122">Database servers</span></span> 
    
#### <a name="web-servers"></a><span data-ttu-id="5a7a1-123">網頁伺服器</span><span class="sxs-lookup"><span data-stu-id="5a7a1-123">Web servers</span></span>

<span data-ttu-id="5a7a1-p102">Web 伺服器] 區段中，有三部網頁伺服器、 主機 A、 主機 B 和 c 主機。在每部網頁伺服器包含分散式快取、 使用者設定檔、 受管理的中繼資料及查詢處理功能。他們也包含索引分割區複本中每一部伺服器。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-p102">In the web servers section, there are three web servers, Host A, Host B, and Host C. Each web server contains a distributed cache, user profiles, managed metadata, and query processing capabilities. They also contain an index partition replica that is in each server.</span></span> 
  
<span data-ttu-id="5a7a1-126">向外延展，新增額外的網頁伺服器使用相同的功能，允許其他 28] 頁面上檢視每秒。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-126">To scale out, add an additional web server with the same capabilities, which allows for an additional 28 page views per second.</span></span> 
  
#### <a name="application-servers"></a><span data-ttu-id="5a7a1-127">應用程式伺服器</span><span class="sxs-lookup"><span data-stu-id="5a7a1-127">Application servers</span></span>

<span data-ttu-id="5a7a1-p103">在 [應用程式伺服器] 區段中有三個應用程式伺服器主機 D 主機 E、 與主機 F.主機 D 包含編目、 管理、 分析及內容處理元件。主機 E 包含編目、 管理員及內容處理元件。主機 F 包含編目及內容處理元件。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-p103">In the application servers section, there are three application servers, Host D, Host E, and Host F. Host D contains Crawl, Admin, Analytics, and Content processing components. Host E contains Crawl, Admin, and Content processing components. Host F contains Crawl and Content processing components.</span></span> 
  
<span data-ttu-id="5a7a1-131">若要向外延展，新增一部應用程式伺服器與編目元件及內容處理元件處理額外 40 每秒文件。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-131">To scale out, add one application server with a crawl component and a content processing component to process an additional 40 documents per second.</span></span> 
  
#### <a name="database-servers"></a><span data-ttu-id="5a7a1-132">資料庫伺服器</span><span class="sxs-lookup"><span data-stu-id="5a7a1-132">Database servers</span></span>

<span data-ttu-id="5a7a1-133">在 [資料庫伺服器] 區段中有兩部伺服器的主機 G 和主機 h資料庫伺服器是在容錯方面的成對主機。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-133">In the database servers section, there are two servers, Host G and Host H. The database servers are in paired hosts for fault tolerance.</span></span> 
  
<span data-ttu-id="5a7a1-p104">主機 G 包含所有 SharePoint 資料庫，包括搜尋管理資料庫、 連結資料庫、 兩個編目資料庫、 分析資料庫及其他所有 SharePoint 資料庫。主機 H 包含所有 SharePoint 資料庫，包括備援副本的所有資料庫使用 SQL 叢集、 鏡像或 SQL Server 2012 AlwaysOn。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-p104">Host G contains all SharePoint database, including Search admin database, Link database, two Crawl databases, an Analytics database, and all other SharePoint databases. Host H contains all SharePoint databases, including redundant copies of all databases using SQL clustering, mirroring, or SQL Server 2012 AlwaysOn.</span></span> 
  
## <a name="fine-tune-for-azure"></a><span data-ttu-id="5a7a1-136">Azure 微調</span><span class="sxs-lookup"><span data-stu-id="5a7a1-136">Fine-tune for Azure</span></span>

<span data-ttu-id="5a7a1-p105">SharePoint 伺服器陣列可能會需要微調的可用性設定於 Azure 平台。若要確保高可用性的所有元件，請確定所有同名設定的伺服器角色。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-p105">The SharePoint farm might need to be fine-tuned for availability sets in the Azure platform. To ensure high availability of all components, ensure that the server roles are all identically configured.</span></span> 
  
<span data-ttu-id="5a7a1-139">在圖表中的範例拓撲：</span><span class="sxs-lookup"><span data-stu-id="5a7a1-139">In the example topology in the diagram:</span></span> 
  
- <span data-ttu-id="5a7a1-140">同名設定網頁伺服器和資料庫伺服器。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-140">The web servers and the database servers are identically configured.</span></span> 
    
- <span data-ttu-id="5a7a1-p106">未同名設定三個應用程式伺服器。這些伺服器角色都需要在 Azure 中的可用性的可調整設定。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-p106">The three application servers are not identically configured. These server roles require fine tuning for availability sets in Azure.</span></span> 
    
### <a name="before"></a><span data-ttu-id="5a7a1-143">之前</span><span class="sxs-lookup"><span data-stu-id="5a7a1-143">Before</span></span>

<span data-ttu-id="5a7a1-p107">圖表的上半部會顯示在 Azure 中設定 SharePoint 伺服器陣列之前有已微調可用性。在圖表中，三個主機應用程式伺服器未同名設定。元件數目是由伺服器陣列的效能與容量目標所決定。三部伺服器設定如下：</span><span class="sxs-lookup"><span data-stu-id="5a7a1-p107">The top portion of the diagram shows the SharePoint farm before it has been fine-tuned for availability sets in Azure. In the diagram, the three host application servers are not identically configured. The number of components is determined by the performance and capacity targets for the farm. The three servers are configured as follows:</span></span> 
  
- <span data-ttu-id="5a7a1-148">具有編目、 管理、 分析及內容處理角色已主機 D 應用程式伺服器。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-148">Host D application server is configured with Crawl, Admin, Analytics, and Content processing roles.</span></span> 
    
- <span data-ttu-id="5a7a1-149">具有編目、 管理員及內容處理角色已主機 E 應用程式伺服器。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-149">Host E application server is configured with Crawl, Admin, and Content processing roles.</span></span> 
    
- <span data-ttu-id="5a7a1-150">具有編目及內容處理角色已主機 F 應用程式伺服器。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-150">Host F application server is configured with Crawl and Content processing roles.</span></span> 
    
### <a name="after"></a><span data-ttu-id="5a7a1-151">之後</span><span class="sxs-lookup"><span data-stu-id="5a7a1-151">After</span></span>

<span data-ttu-id="5a7a1-p108">此部分的圖表顯示在 Azure 中設定 SharePoint 伺服器陣列之後具有已微調可用性。Azure 能否此架構，我們將所有三部伺服器上複寫的四個元件。這會增加超過功能時所需的效能與容量的元件數目。取捨是此設計可確保當下列三個虛擬機器時指派給可用性設定 Azure 平台中所有的四個元件的高可用性。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-p108">This part of the diagram shows the SharePoint farm after it has been fine-tuned for availability sets in Azure. To adapt this architecture for Azure, we'll replicate the four components across all three servers. This increases the number of components beyond what is necessary for performance and capacity. The tradeoff is that this design ensures high availability of all four components in the Azure platform when these three virtual machines are assigned to an availability set.</span></span> 
  
<span data-ttu-id="5a7a1-156">三部伺服器設定為所有具有編目、 管理、 分析及內容處理角色。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-156">The three servers are configured to all have the Crawl, Admin, Analytics, and Content processing roles.</span></span> 
  
## <a name="choose-the-active-directory-model"></a><span data-ttu-id="5a7a1-157">選擇 [Active Directory 模型</span><span class="sxs-lookup"><span data-stu-id="5a7a1-157">Choose the Active Directory model</span></span>

<span data-ttu-id="5a7a1-p109">所有的 SharePoint 解決方案需要 Windows Active Directory 網域服務 (AD DS)。在此階段中，有兩個 Azure 中的 SharePoint 解決方案的選項。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-p109">All SharePoint solutions require Windows Active Directory Domain Services (AD DS). At this time, there are two options for SharePoint solutions in Azure.</span></span> 
  
- <span data-ttu-id="5a7a1-p110">做法 1： 專用的網域-您可對 Azure 支援的 SharePoint 伺服器陣列部署專用及隔離網域。這是不錯的選擇的公用對向網際網路網站。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-p110">Option 1: Dedicated domain — You can deploy a dedicated and isolated domain to Azure to support a SharePoint farm. This is a good choice for public-facing Internet sites.</span></span> 
    
- <span data-ttu-id="5a7a1-p111">選項 2： 擴充至網站 VPN 連線到內部網域。當您擴充至網站 VPN 連線到內部網域時、 使用者會存取 SharePoint 伺服器陣列主控內部部署一樣。您可以運用您現有的 Active Directory 和 DNS 實作。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-p111">Option 2: Extend the on-premises domain through a site-to-site VPN connection. When you extend the on-premises domain through a site-to-site VPN connection, users access the SharePoint farm as if it were hosted on-premises. You can take advantage of your existing Active Directory and DNS implementations.</span></span> 
    
## <a name="design-for-identity-management-zones-and-authentication"></a><span data-ttu-id="5a7a1-165">設計的身分識別管理、 區域及驗證</span><span class="sxs-lookup"><span data-stu-id="5a7a1-165">Design for identity management, zones, and authentication</span></span>

### <a name="design-for-accounts-and-authentication"></a><span data-ttu-id="5a7a1-166">帳戶和驗證設計</span><span class="sxs-lookup"><span data-stu-id="5a7a1-166">Design for accounts and authentication</span></span>

<span data-ttu-id="5a7a1-167">決定如何將受管理帳戶和將使用的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-167">Determine how accounts will be managed and which type of authentication will be used.</span></span> 
  
#### <a name="accounts-for-site-developers-and-authors"></a><span data-ttu-id="5a7a1-168">網站開發人員和作者的帳戶</span><span class="sxs-lookup"><span data-stu-id="5a7a1-168">Accounts for site developers and authors</span></span>

- <span data-ttu-id="5a7a1-169">將帳戶新增至 Azure 中的網域。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-169">Add accounts to the domain in Azure.</span></span> 
    
- <span data-ttu-id="5a7a1-170">使用內部部署 Active Directory Federation Services (AD FS) 同盟內部 Azure 中的網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-170">Use Active Directory Federation Services (AD FS) on premises to federate the internal accounts to the domain in Azure.</span></span> 
    
- <span data-ttu-id="5a7a1-171">如果設計包含的網站 VPN 連線，請使用內部的帳戶。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-171">If the design includes a site-to-site VPN connection, use the internal accounts.</span></span> 
    
#### <a name="accounts-for-customers"></a><span data-ttu-id="5a7a1-172">客戶的帳戶</span><span class="sxs-lookup"><span data-stu-id="5a7a1-172">Accounts for customers</span></span>

- <span data-ttu-id="5a7a1-173">使用 Azure Active Directory。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-173">Use Azure Active Directory.</span></span> 
    
- <span data-ttu-id="5a7a1-174">使用不同的 saml 提供者。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-174">Use a different SAML-based provider.</span></span> 
    
### <a name="design-for-zones"></a><span data-ttu-id="5a7a1-175">設計的區域</span><span class="sxs-lookup"><span data-stu-id="5a7a1-175">Design for zones</span></span>

<span data-ttu-id="5a7a1-176">在 SharePoint 2013 中的身分識別管理會納入區域和驗證的設定。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-176">In SharePoint 2013, identity management is factored into the configuration of zones and authentication.</span></span> 
  
<span data-ttu-id="5a7a1-177">此設計提供清楚的區隔客戶帳戶的所有其他帳戶。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-177">This design provides clear separation of customer accounts from all other accounts.</span></span> 
  
- <span data-ttu-id="5a7a1-178">此設計如果您想使用客戶帳戶被處理完全不同的內部帳戶作者和網站開發人員。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-178">Use this design if you want customer accounts to be treated entirely different from the internal accounts for authors and site developers.</span></span> 
    
- <span data-ttu-id="5a7a1-179">使用此設計，您可以使用區域原則以限制 web 應用程式中的客戶動作。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-179">By using this design, you can use zone policies to limit customer actions within a web application.</span></span> 
    
- <span data-ttu-id="5a7a1-180">此設計產生客戶帳戶和內部帳戶不同的 Url。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-180">This design results in different URLs for customer accounts and internal accounts.</span></span> 
    
<span data-ttu-id="5a7a1-181">在此範例中：</span><span class="sxs-lookup"><span data-stu-id="5a7a1-181">In this example:</span></span> 
  
- <span data-ttu-id="5a7a1-182">設定內部帳戶之預設區域。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-182">Configure the default zone for internal accounts.</span></span> 
    
- <span data-ttu-id="5a7a1-p112">設定驗證的客戶存取的外部網路區域。使用 Azure Active Directory (AD) 客戶帳戶，或使用不同的 saml 提供者。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-p112">Configure the extranet zone for customer authenticated access. Use Azure Active Directory (AD) for customer accounts, or use a different SAML-based provider.</span></span> 
    
- <span data-ttu-id="5a7a1-185">設定網際網路區域的匿名存取。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-185">Configure the Internet zone for anonymous access.</span></span> 
    
<span data-ttu-id="5a7a1-186">請勿使用所有經過驗證的使用者設定為使用預設區域中的兩個區域設計。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-186">Don't use a two-zone design in which all authenticated users are configured to use the default zone.</span></span> 
  
<span data-ttu-id="5a7a1-187">隨附的圖表顯示三個區域設計與區分內部和客戶帳戶。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-187">The accompanying diagram shows a three-zone design with separation of internal and customer accounts.</span></span> 
  
<span data-ttu-id="5a7a1-p113">訪客和客戶透過其中兩個區域的 web 應用程式來存取在 SharePoint 2013 伺服器陣列中的 Azure AD 租用戶。兩個區域包括：</span><span class="sxs-lookup"><span data-stu-id="5a7a1-p113">Visitors and customers access the Azure AD Tenant in the SharePoint 2013 farm through web applications in one of two zones. The two zones include:</span></span> 
  
- <span data-ttu-id="5a7a1-190">匿名使用者的區域： 網際網路</span><span class="sxs-lookup"><span data-stu-id="5a7a1-190">Zone: Internet for anonymous users</span></span> 
    
- <span data-ttu-id="5a7a1-191">區域： 已驗證使用者的外部網路</span><span class="sxs-lookup"><span data-stu-id="5a7a1-191">Zone: Extranet for authenticated users</span></span> 
    
<span data-ttu-id="5a7a1-p114">具有內部的帳戶使用者的存取 Azure Active Directory 租用戶從 AD DS 和透過 VPN 通道內部部署環境中的 AD FS Azure AD。「 預設 」 區域提供 Windows 驗證 (NTLM)。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-p114">Users with internal accounts access the Azure Active Directory Tenant from AD DS and AD FS in the on-premises environment through the VPN tunnel to Azure AD. The Default zone provides Windows Authentication (NTLM).</span></span> 
  
### <a name="design-for-connecting-to-azure-ad"></a><span data-ttu-id="5a7a1-194">連線至 Azure AD 的設計</span><span class="sxs-lookup"><span data-stu-id="5a7a1-194">Design for connecting to Azure AD</span></span>

 <span data-ttu-id="5a7a1-p115">Azure AD 提供雲端服務的身分識別管理和存取控制功能。功能包括目錄資料與一組核心身分識別服務，包括使用者登入程序、 驗證服務及 AD FS 的雲端存放區。身分識別服務隨附的 Azure AD 輕鬆地整合在內部部署 AD DS 及完全支援協力廠商身分識別提供者。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-p115">Azure AD provides identity management and access control capabilities for cloud services. Capabilities include a cloud-based store for directory data and a core set of identity services, including user logon processes, authentication services, and AD FS. The identity services that are included with Azure AD easily integrate with your on-premises AD DS deployments and fully support third-party identity providers.</span></span>
  
<span data-ttu-id="5a7a1-198">隨附的圖顯示下列案例：</span><span class="sxs-lookup"><span data-stu-id="5a7a1-198">The accompanying diagram shows the following scenario:</span></span> 
  
<span data-ttu-id="5a7a1-199">使用 Azure Active Directory 整合 SharePoint 2013、 時 Azure Access Control Service (ACS) 有兩種用途：</span><span class="sxs-lookup"><span data-stu-id="5a7a1-199">When integrating SharePoint 2013 with Azure Active Directory, an Azure Access Control Service (ACS) serves two purposes:</span></span> 
  
-  <span data-ttu-id="5a7a1-p116">Azure AD 使用 SAML 2.0 及 SharePoint 僅適用於 SAML 1.1。ACS 了解這兩種格式及做為轉換 SharePoint 與 Azure AD 之間的 token 格式中介者。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-p116">Azure AD uses SAML 2.0, and SharePoint only works with SAML 1.1. ACS understands both formats and serves as the intermediary to transform the token formats between SharePoint and Azure AD.</span></span>
    
- <span data-ttu-id="5a7a1-202">ACS 會取代需要藉助的身分識別提供者 security token service (IP-STS) 這個 SAML 案例。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-202">ACS replaces the need for the identity provider security token service (IP-STS) for this SAML scenario.</span></span> 
    
<span data-ttu-id="5a7a1-203">如需詳細資訊，請參閱 TechNet library 中的設定與 SharePoint 2013 的 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-203">For more information, see Configure Azure AD with SharePoint 2013 in the TechNet library.</span></span> 
  
## <a name="design-sites-and-urls-for-cross-site-publishing"></a><span data-ttu-id="5a7a1-204">設計網站和跨網站發佈的 Url</span><span class="sxs-lookup"><span data-stu-id="5a7a1-204">Design sites and URLs for cross-site publishing</span></span>

<span data-ttu-id="5a7a1-205">一個 web 應用程式的設計建議發佈案例。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-205">A one web-application design is recommended for publishing scenarios.</span></span> 
  
- <span data-ttu-id="5a7a1-206">同時製作及發佈網站位於相同的 web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-206">Both authoring and publishing sites are in the same web application.</span></span> 
    
- <span data-ttu-id="5a7a1-207">跨網站發佈用以發佈資產。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-207">Cross-site publishing is used to publish assets.</span></span> 
    
<span data-ttu-id="5a7a1-208">使用路徑型與主機命名型網站集合。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-208">Use path-based and host-named site collections.</span></span> 
  
- <span data-ttu-id="5a7a1-p117">根網站集合是需求。建立此站台作為路徑型網站。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-p117">A root site collection is a requirement. Create this site as a path-based site.</span></span> 
    
- <span data-ttu-id="5a7a1-211">為主機命名型網站集合中建立的所有其他網站集合。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-211">Create all other site collections as host-named site collections.</span></span> 
    
<span data-ttu-id="5a7a1-212">Web 應用程式和根網站 Url</span><span class="sxs-lookup"><span data-stu-id="5a7a1-212">Web application and root site URLs</span></span> 
  
- <span data-ttu-id="5a7a1-p118">使用 web 應用程式 URL 的內部名稱。除非指定不同的名稱 SharePoint 所使用的預設名稱為本機電腦名稱。您可以使用保留的網域名稱的內部網路環境。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-p118">Use an internal name for the web application URL. SharePoint uses the local machine name as the default name unless a different name is specified. You can use a domain name that is reserved for the internal network environment.</span></span> 
    
- <span data-ttu-id="5a7a1-p119">SharePoint 將非標準連接埠號碼時建立的 web 應用程式。使用此連接埠號碼，而非連接埠 80 或連接埠 443。或使用不同但非標準連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-p119">SharePoint assigns a nonstandard port number when the web application is created. Use this port number instead of port 80 or port 443. Or use a different but nonstandard port number.</span></span> 
    
- <span data-ttu-id="5a7a1-219">使用相同的名稱及連接埠號碼是路徑型網站集合根網站集合。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-219">Use the same name and port number for the root site collection, which is a path-based site collection.</span></span> 
    
<span data-ttu-id="5a7a1-p120">隨附的圖表顯示應用程式集區服務，例如搜尋與網站集合使用的 web 應用程式互動。顯示網站集合包括：</span><span class="sxs-lookup"><span data-stu-id="5a7a1-p120">The accompanying diagram shows application pool services such as Search interacting with site collections using web applications. The site collections shown include:</span></span> 
  
- <span data-ttu-id="5a7a1-222">位於 http://internal:8000 （根網站） 的路徑型網站集合。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-222">Path-based site collection located at http://internal:8000 (root site).</span></span> 
    
- <span data-ttu-id="5a7a1-223">編目： 主機命名型網站集合位於 https://authoring.contoso.com:8000 等的地址。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-223">Crawl: Host-named site collections located at an address such as https://authoring.contoso.com:8000.</span></span> 
    
- <span data-ttu-id="5a7a1-224">查詢： 2 的不同的主機命名型網站集合位於位址例如：</span><span class="sxs-lookup"><span data-stu-id="5a7a1-224">Queries: 2 separate Host-named site collections located at addresses such as:</span></span> 
    
  - <span data-ttu-id="5a7a1-225">http://www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="5a7a1-225">http://www.contoso.com</span></span> 
    
  - <span data-ttu-id="5a7a1-226">https://secure.contoso.com</span><span class="sxs-lookup"><span data-stu-id="5a7a1-226">https://secure.contoso.com</span></span> 
    
  - <span data-ttu-id="5a7a1-227">http://www.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="5a7a1-227">http://www.contoso.com:8000</span></span> 
    
  - <span data-ttu-id="5a7a1-228">http://assets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="5a7a1-228">http://assets.contoso.com</span></span> 
    
  - <span data-ttu-id="5a7a1-229">https://secureassets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="5a7a1-229">https://secureassets.contoso.com</span></span> 
    
  - <span data-ttu-id="5a7a1-230">http://assets.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="5a7a1-230">http://assets.contoso.com:8000</span></span> 
    
## <a name="design-the-azure-environment"></a><span data-ttu-id="5a7a1-231">設計 Azure 環境</span><span class="sxs-lookup"><span data-stu-id="5a7a1-231">Design the Azure environment</span></span>

<span data-ttu-id="5a7a1-232">此範例架構包含下列元素：</span><span class="sxs-lookup"><span data-stu-id="5a7a1-232">This example architecture includes the following elements:</span></span> 
  
- <span data-ttu-id="5a7a1-233">網站 VPN 連線是選用的步驟及延伸的內部 Windows AD DS 與在 Azure 虛擬網路的 DNS 環境。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-233">A site-to-site VPN connection is optional and extends the on-premises Windows AD DS and DNS environment to the virtual network in Azure.</span></span> 
    
- <span data-ttu-id="5a7a1-234">（選用） 使用 Azure 中的專屬的網域支援的 SharePoint 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-234">Optionally, use a dedicated domain in Azure to support the SharePoint farm.</span></span> 
    
- <span data-ttu-id="5a7a1-235">伺服器會跨角色為基礎的 Azure 雲端服務分割。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-235">Servers are split across Azure cloud services based on role.</span></span> 
    
- <span data-ttu-id="5a7a1-236">可用性設定確保高可用性的設定相同的伺服器角色。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-236">Availability sets ensure high availability of identically configured server roles.</span></span> 
    
<span data-ttu-id="5a7a1-237">如需詳細資訊，請參閱下文 technet： Azure Architectures for SharePoint 解決方案。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-237">For more information, see the following article on TechNet: Azure Architectures for SharePoint Solutions.</span></span> 
  
<span data-ttu-id="5a7a1-238">隨附圖與 Azure 虛擬網路連線的內部部署環境的範例。</span><span class="sxs-lookup"><span data-stu-id="5a7a1-238">The accompanying diagram shows an example of an on-premises environment connecting with an Azure virtual network.</span></span> 
  
<span data-ttu-id="5a7a1-239">在內部部署環境中，這是選用的元素的 Azure 環境，包括下列元件：</span><span class="sxs-lookup"><span data-stu-id="5a7a1-239">Included in the on-premises environment, which is an optional element of the Azure environment, are the following components:</span></span> 
  
- <span data-ttu-id="5a7a1-240">Windows Server 2012 RRAS</span><span class="sxs-lookup"><span data-stu-id="5a7a1-240">Windows Server 2012 RRAS</span></span> 
    
- <span data-ttu-id="5a7a1-241">AD DS</span><span class="sxs-lookup"><span data-stu-id="5a7a1-241">AD DS</span></span> 
    
- <span data-ttu-id="5a7a1-242">從 Windows Server 和 AD DS VPN 閘道作用中的 VPN 閘道子網路</span><span class="sxs-lookup"><span data-stu-id="5a7a1-242">A VPN gateway from Windows Server and AD DS to the Active VPN Gateway subnet</span></span> 
    
<span data-ttu-id="5a7a1-243">Azure 虛擬網路環境包含下列元件：</span><span class="sxs-lookup"><span data-stu-id="5a7a1-243">The Azure virtual network environment includes the following components:</span></span> 
  
- <span data-ttu-id="5a7a1-244">作用中的 VPN 閘道子網路 （重疊的內部部署環境中，如果有的話）</span><span class="sxs-lookup"><span data-stu-id="5a7a1-244">The Active VPN Gateway subnet (overlapping with the on-premises environment, if applicable)</span></span> 
    
- <span data-ttu-id="5a7a1-245">雲端服務，包含 AD DS 與 DNS 的可用性設定 （兩部伺服器）</span><span class="sxs-lookup"><span data-stu-id="5a7a1-245">Cloud service that includes AD DS and DNS availability set (two servers)</span></span> 
    
- <span data-ttu-id="5a7a1-246">雲端服務包含前端伺服器的可用性設定 （三個 SharePoint 伺服器） 和應用程式伺服器的可用性設定 （三個 SharePoint 伺服器）</span><span class="sxs-lookup"><span data-stu-id="5a7a1-246">Cloud service that include the front-end server availability set (three SharePoint servers) and the App server availability set (three SharePoint servers)</span></span> 
    
- <span data-ttu-id="5a7a1-247">包含兩個資料庫可用性的雲端服務設定</span><span class="sxs-lookup"><span data-stu-id="5a7a1-247">Cloud service that contains two database availability sets</span></span> 
    

