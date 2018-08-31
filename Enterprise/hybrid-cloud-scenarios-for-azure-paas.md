---
title: Azure PaaS 的混合式雲端案例
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 5f4f5d0d-4638-48e8-a517-bd804856b617
description: 摘要： 了解混合式架構與案例的 Microsoft 平台服務 (PaaS)-以 Azure 中的雲端方案。
ms.openlocfilehash: e60bc92eed45e5d29fe0be80320dee65b8325028
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915008"
---
# <a name="hybrid-cloud-scenarios-for-azure-paas"></a><span data-ttu-id="5d15d-103">Azure PaaS 的混合式雲端案例</span><span class="sxs-lookup"><span data-stu-id="5d15d-103">Hybrid cloud scenarios for Azure PaaS</span></span>

 <span data-ttu-id="5d15d-104">**摘要：** 了解混合式架構與案例的 Microsoft 平台做為服務 (PaaS)-以 Azure 中的雲端方案。</span><span class="sxs-lookup"><span data-stu-id="5d15d-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Platform as a Service (PaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="5d15d-105">合併內部資料或運算資源與新的或已轉換應用程式在 Azure PaaS，可以利用雲端效能、 可靠性及向外與行動裝置使用者提供較佳的支援。</span><span class="sxs-lookup"><span data-stu-id="5d15d-105">Combine on-premises data or computing resources with new or converted applications running in Azure PaaS, which can take advantage of cloud performance, reliability, and scale and provide better support for mobile users.</span></span> 
  
## <a name="azure-paas-hybrid-scenario-architecture"></a><span data-ttu-id="5d15d-106">Azure PaaS 混合式案例的架構</span><span class="sxs-lookup"><span data-stu-id="5d15d-106">Azure PaaS hybrid scenario architecture</span></span>

<span data-ttu-id="5d15d-107">圖 1 顯示在 Azure 中的 Microsoft PaaS 為基礎的混合式案例的架構。</span><span class="sxs-lookup"><span data-stu-id="5d15d-107">Figure 1 shows the architecture of Microsoft PaaS-based hybrid scenarios in Azure.</span></span>
  
<span data-ttu-id="5d15d-108">**Azure 中的圖 1： Microsoft PaaS 為基礎的混合式案例**</span><span class="sxs-lookup"><span data-stu-id="5d15d-108">**Figure 1: Microsoft PaaS-based hybrid scenarios in Azure**</span></span>

![Azure 中的 Microsoft PaaS 型混合式案例](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS.png)
  
<span data-ttu-id="5d15d-110">之架構的每個圖層：</span><span class="sxs-lookup"><span data-stu-id="5d15d-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="5d15d-111">應用程式與案例</span><span class="sxs-lookup"><span data-stu-id="5d15d-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="5d15d-112">混合式 PaaS 應用程式執行 Azure 中同時使用內部部署 compute 或儲存資源。</span><span class="sxs-lookup"><span data-stu-id="5d15d-112">A hybrid PaaS application runs in Azure and uses on-premises compute or storage resources.</span></span>
    
- <span data-ttu-id="5d15d-113">身分識別</span><span class="sxs-lookup"><span data-stu-id="5d15d-113">Identity</span></span>
    
    <span data-ttu-id="5d15d-114">包含目錄同步處理或與協力廠商身分識別提供者同盟。</span><span class="sxs-lookup"><span data-stu-id="5d15d-114">Consists of either directory synchronization or federation with a third-party identity provider.</span></span>
    
- <span data-ttu-id="5d15d-115">工作列最右邊的網路</span><span class="sxs-lookup"><span data-stu-id="5d15d-115">Network</span></span>
    
    <span data-ttu-id="5d15d-p101">包含您現有的網際網路管道或具有公用對等以 Azure PaaS ExpressRoute 連線。您必須包含 Azure PaaS 應用程式以存取內部部署 compute 或儲存資源的方式。</span><span class="sxs-lookup"><span data-stu-id="5d15d-p101">Consists of either your existing Internet pipe or an ExpressRoute connection with public peering to Azure PaaS. You must include a way for the Azure PaaS application to access the on-premises compute or storage resource.</span></span>
    
- <span data-ttu-id="5d15d-118">內部部署</span><span class="sxs-lookup"><span data-stu-id="5d15d-118">On-premises</span></span>
    
    <span data-ttu-id="5d15d-119">身分識別與安全性基礎結構和業務 (LOB) 應用程式或 Azure PaaS 應用程式可以安全地存取的資料庫伺服器的現有列所組成。</span><span class="sxs-lookup"><span data-stu-id="5d15d-119">Consists of identity and security infrastructure and existing line of business (LOB) applications or database servers, which an Azure PaaS application can securely access.</span></span>
    
## <a name="azure-paas-hybrid-application"></a><span data-ttu-id="5d15d-120">Azure PaaS 混合式應用程式</span><span class="sxs-lookup"><span data-stu-id="5d15d-120">Azure PaaS hybrid application</span></span>

<span data-ttu-id="5d15d-121">圖 2 顯示在 Azure 中執行的混合式應用程式的設定。</span><span class="sxs-lookup"><span data-stu-id="5d15d-121">Figure 2 shows the configuration of a hybrid application running in Azure.</span></span>
  
<span data-ttu-id="5d15d-122">**圖 2： Azure PaaS 為基礎的混合式應用程式**</span><span class="sxs-lookup"><span data-stu-id="5d15d-122">**Figure 2: Azure PaaS-based hybrid application**</span></span>

![Azure PaaS 型混合式應用程式](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps.png)
  
<span data-ttu-id="5d15d-p102">圖 2] 中的內部網路主控儲存裝置或應用程式伺服器與 DMZ 包含 proxy 伺服器上。它會透過網際網路或 ExpressRoute 連線以連線至 Azure PaaS 服務。</span><span class="sxs-lookup"><span data-stu-id="5d15d-p102">In Figure 2, an on-premises network hosts storage or apps on servers and a DMZ containing a proxy server. It is connected to Azure PaaS services either over the Internet or with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="5d15d-126">組織可以提供其 compute 或儲存的資源由 Azure PaaS 混合式應用程式：</span><span class="sxs-lookup"><span data-stu-id="5d15d-126">An organization can make its compute or storage resources available to the Azure PaaS hybrid application by:</span></span>
  
- <span data-ttu-id="5d15d-127">主控 DMZ 中的伺服器上的資源。</span><span class="sxs-lookup"><span data-stu-id="5d15d-127">Hosting the resource on servers in the DMZ.</span></span>
    
- <span data-ttu-id="5d15d-128">以架設在 DMZ 反向 proxy 伺服器，允許經驗證、 輸入、 HTTPS 型要求送至內部所在的資源。</span><span class="sxs-lookup"><span data-stu-id="5d15d-128">Hosting a reverse proxy server in the DMZ, which allows authenticated, inbound, HTTPS-based requests to the resource that is located on-premises.</span></span>
    
<span data-ttu-id="5d15d-129">Azure 應用程式可以使用認證：</span><span class="sxs-lookup"><span data-stu-id="5d15d-129">The Azure app can use credentials from:</span></span>
  
- <span data-ttu-id="5d15d-130">Azure AD、 以內部身分識別提供者，例如 Windows Server AD 同步處理。</span><span class="sxs-lookup"><span data-stu-id="5d15d-130">Azure AD, which can be synchronized with your on-premises identity provider, such as Windows Server AD.</span></span>
    
- <span data-ttu-id="5d15d-131">協力廠商身分識別提供者。</span><span class="sxs-lookup"><span data-stu-id="5d15d-131">A third-party identity provider.</span></span>
    
### <a name="example-azure-paas-hybrid-application"></a><span data-ttu-id="5d15d-132">範例 Azure PaaS 混合式應用程式</span><span class="sxs-lookup"><span data-stu-id="5d15d-132">Example Azure PaaS hybrid application</span></span>

<span data-ttu-id="5d15d-133">圖 3 是執行 Azure 中的範例混合式應用程式。</span><span class="sxs-lookup"><span data-stu-id="5d15d-133">Figure 3 shows an example hybrid application running in Azure.</span></span>
  
<span data-ttu-id="5d15d-134">**圖 3： 範例 Azure PaaS 為基礎的混合式應用程式**</span><span class="sxs-lookup"><span data-stu-id="5d15d-134">**Figure 3: An example Azure PaaS-based hybrid application**</span></span>

![Azure PaaS 型混合式應用程式的範例](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps-Ex.png)
  
<span data-ttu-id="5d15d-p103">圖 3、 LOB 的內部網路主機 app Azure PaaS 主控自訂的行動裝置應用程式。Smartphone 在網際網路上的存取 Azure、 將資料要求傳送至內部部署 LOB 應用程式中自訂的行動裝置應用程式。</span><span class="sxs-lookup"><span data-stu-id="5d15d-p103">In Figure 3, an on-premises network hosts an LOB app. Azure PaaS hosts a custom mobile app. A smartphone on the Internet accesses the custom mobile app in Azure, which sends data requests to the on-premises LOB app.</span></span>
  
<span data-ttu-id="5d15d-p104">本範例會為 Azure PaaS 混合式應用程式是自訂的行動裝置應用程式上員工提供最新的連絡人資訊。端對端混合式案例所組成：</span><span class="sxs-lookup"><span data-stu-id="5d15d-p104">This example Azure PaaS hybrid application is a custom mobile app that provides up-to-date contact information on employees. The end-to-end hybrid scenario consists of:</span></span>
  
- <span data-ttu-id="5d15d-141">Smartphone 應用程式需要驗證，若要執行的內部部署認證。</span><span class="sxs-lookup"><span data-stu-id="5d15d-141">A smartphone app that requires validated, on-premises credentials to run.</span></span>
    
- <span data-ttu-id="5d15d-142">自訂行動應用程式正在 Azure PaaS、 要求特定使用者的智慧型手機應用程式的查詢為基礎的員工的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5d15d-142">A custom mobile app running in Azure PaaS, which requests information about specific employees based on queries from a user's smartphone app.</span></span>
    
- <span data-ttu-id="5d15d-143">在 DMZ 來驗證自訂的行動裝置應用程式並將要求轉送反向 proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="5d15d-143">A reverse proxy server in the DMZ that validates the custom mobile app and forwards the request.</span></span>
    
- <span data-ttu-id="5d15d-144">連絡人的要求，受限於使用者帳戶的權限服務 LOB 應用程式伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="5d15d-144">An LOB application server farm that services the contact request, subject to the permissions of the user's account.</span></span>
    
<span data-ttu-id="5d15d-145">因為已與 Azure AD 同步處理在內部身分識別提供者，自訂的行動裝置應用程式與 LOB 應用程式可以驗證要求的使用者帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="5d15d-145">Because the on-premises identity provider has been synchronized with Azure AD, both the custom mobile app and the LOB app can validate the requesting user's account name.</span></span>
  
## <a name="stretch-database-with-sql-server-2016"></a><span data-ttu-id="5d15d-146">運用 SQL Server 2016 延展資料庫</span><span class="sxs-lookup"><span data-stu-id="5d15d-146">Stretch Database with SQL Server 2016</span></span>

<span data-ttu-id="5d15d-147">伸展資料庫功能可讓您透明和安全地移動冷資料，例如大型表格包含客戶訂單資訊、 Azure 中的 SQL 拉大資料庫已關閉的商務資料的 SQL Server 2016。</span><span class="sxs-lookup"><span data-stu-id="5d15d-147">Stretch database is a feature of SQL Server 2016 that allows you to transparently and securely move cold data, such as closed business data in a large table that contains customer order information, to a SQL Stretch database in Azure.</span></span>
  
<span data-ttu-id="5d15d-p105">當拉長、 SQL Server 執行個體、 資料庫、 或甚至是一個表格的內容是 SQL Server 2016 伺服器中的本機資料和 Azure 中的遠端資料的組合。如拉長 SQL Server 2016 自動移到 Azure 會變成合格的資料。</span><span class="sxs-lookup"><span data-stu-id="5d15d-p105">When stretched, the contents of a SQL Server instance, a database, or even a single table is the combination of local data in SQL Server 2016 server and remote data in Azure. Data that becomes eligible for stretch is automatically moved to Azure by SQL Server 2016.</span></span>
  
<span data-ttu-id="5d15d-150">圖 4 顯示與 SQL Server 2016 延展資料庫。</span><span class="sxs-lookup"><span data-stu-id="5d15d-150">Figure 4 shows Stretch Database with SQL Server 2016.</span></span>
  
<span data-ttu-id="5d15d-151">**圖 4： 以 SQL Server 2016 伸展的資料庫**</span><span class="sxs-lookup"><span data-stu-id="5d15d-151">**Figure 4: Stretch Database with SQL Server 2016**</span></span>

![運用 SQL Server 2016 延展資料庫](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps-SQL.png)
  
<span data-ttu-id="5d15d-p106">圖 4] 中的內部網路主控執行 SQL Server 2016 使用小型的本機資料庫伺服器。Azure PaaS 主控 Azure SQL Server 拉大資料庫執行個體與資料庫的延伸部分。T-SQL 查詢傳送至內部部署 SQL server 的內部部署使用者安全地轉寄給 Azure SQL 拉大資料庫，將結果傳回給要求的使用者。</span><span class="sxs-lookup"><span data-stu-id="5d15d-p106">In Figure 4, an on-premises network hosts a server running SQL Server 2016 with a small local database. Azure PaaS hosts an instance of Azure SQL Server Stretch Database with the stretched portion of the database. T-SQL queries from an on-premises user sent to the on-premises SQL server are securely forwarded to the Azure SQL Stretch Database, which returns the results to the requesting user.</span></span>
  
 <span data-ttu-id="5d15d-p107">包含的歷程資料的使用者查詢透明轉寄給 Azure SQL 延展資料庫。查詢不需要重新寫入，即使表格會拉長。</span><span class="sxs-lookup"><span data-stu-id="5d15d-p107">User queries that include the historical data are transparently forwarded to Azure SQL Stretch database. The queries do not need to be re-written, even though the table is stretched.</span></span>
  
<span data-ttu-id="5d15d-p108">伸展資料庫提供長期儲存區與透明資料的存取權歷史符合成本效益的選項。它也求解效能及可用性問題發生時表格會變得非常大。</span><span class="sxs-lookup"><span data-stu-id="5d15d-p108">Stretch database provides a cost-effective option for long-term storage and transparent access to historical data. It also solves performance and availability problems that arise when tables become very large.</span></span>
  
<span data-ttu-id="5d15d-160">如需詳細資訊，請參閱[延展資料庫](https://msdn.microsoft.com/library/dn935011.aspx)。</span><span class="sxs-lookup"><span data-stu-id="5d15d-160">For more information, see [Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5d15d-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d15d-161">See Also</span></span>

[<span data-ttu-id="5d15d-162">Microsoft Hybrid Cloud for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="5d15d-162">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="5d15d-163">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="5d15d-163">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="5d15d-164">Microsoft 的 Enterprise Cloud 藍圖：IT 決策者的資源</span><span class="sxs-lookup"><span data-stu-id="5d15d-164">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



