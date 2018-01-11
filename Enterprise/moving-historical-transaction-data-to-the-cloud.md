---
title: "將歷程交易資料移至雲端"
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
ms.assetid: 3e9c405a-415b-4584-aa7e-f2489299c457
description: "摘要： 如何實作 Contoso SQL Server 伸展以減少其內部部署資料儲存需求及每日執行成本的資料庫。"
ms.openlocfilehash: ef21b00f54fcc6efda2e83cb5952a99c7b8c8f28
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2018
---
# <a name="moving-historical-transaction-data-to-the-cloud"></a><span data-ttu-id="e9405-103">將歷程交易資料移至雲端</span><span class="sxs-lookup"><span data-stu-id="e9405-103">Moving historical transaction data to the cloud</span></span>

 <span data-ttu-id="e9405-104">**摘要：**Contoso 的實作方式以減少其內部部署資料儲存需求及每日執行成本的 SQL Server 延展資料庫。</span><span class="sxs-lookup"><span data-stu-id="e9405-104">**Summary:** How Contoso implemented SQL Server stretch database to reduce its on-premises data storage needs and daily running costs.</span></span>
  
<span data-ttu-id="e9405-p101">Contoso 的企業版的儲存系統儲存大量的嚴格該法規需求與行銷 research 歷史交易資料和 BI 耗費趨勢分析。Contoso 也需要從磁帶、 大量消耗時間的程序還原封存的資料。Contoso 的企業儲存系統中的硬體已接近其週期結束並取代其就是很高。</span><span class="sxs-lookup"><span data-stu-id="e9405-p101">Contoso's enterprise storage system stores a large amount of historical transaction data for adherence with regulatory requirements and for marketing research and BI analysis of spending trends. Contoso also needs to restore archived data from magnetic tape, a time-intensive process. The hardware in Contoso's enterprise storage system was nearing its end of life and replacing it would be very expensive.</span></span> 
  
<span data-ttu-id="e9405-p102">可調整其內部部署資料中心來關閉其業務需求的一部分，Contoso 選擇升級至 SQL Server 2016 因拉大資料庫混合式功能以及與 Azure 其緊密整合。伸展資料庫允許將冷資料其表格中的資料從內部部署移至雲端儲存 Contoso 的本機磁碟空間釋放及降低維護。熱和冷資料位於相同的資料表及一定是適用於維護，例如備份與還原和應用程式和其使用者。圖 1 顯示延展資料庫。</span><span class="sxs-lookup"><span data-stu-id="e9405-p102">As part of its business need to scale down its on-premises datacenters, Contoso chose to upgrade to SQL Server 2016 because of the Stretch Database hybrid feature and its seamless integration with Azure. Stretch Database allows Contoso to move the cold data in its tables from on-premises to cloud storage, freeing up local disk space and reducing maintenance. Both hot and cold data are in the same tables and are always available to applications and their users and for maintenance, such as backups and restores. Figure 1 shows Stretch Database.</span></span>
  
<span data-ttu-id="e9405-112">**圖 1： SQL Server 伸展資料庫**</span><span class="sxs-lookup"><span data-stu-id="e9405-112">**Figure 1: SQL Server Stretch Database**</span></span>

![SQL Server Stretch Database 做為混合式資料解決方案](images/Contoso_Poster/StretchDB01.png)
  
<span data-ttu-id="e9405-114">圖 1 顯示的 SQL 用戶端執行 SQL Server 2016、 將其轉寄到 Azure PaaS Azure SQL 延展資料庫的伺服器所傳送的 T-SQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="e9405-114">Figure 1 shows how a SQL client sends T-SQL queries to a server running SQL Server 2016, which forwards them to an Azure SQL Stretch Database in Azure PaaS.</span></span>
  
<span data-ttu-id="e9405-115">如需詳細資訊，請參閱[延展資料庫](https://msdn.microsoft.com/library/dn935011.aspx)。</span><span class="sxs-lookup"><span data-stu-id="e9405-115">For more information, see [Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx).</span></span>
  
<span data-ttu-id="e9405-116">Contoso 用來將其歷程資料移至雲端的下列步驟：</span><span class="sxs-lookup"><span data-stu-id="e9405-116">Contoso used these steps to move their historical data to the cloud:</span></span>
  
1. <span data-ttu-id="e9405-117">分析資料庫</span><span class="sxs-lookup"><span data-stu-id="e9405-117">Analyze databases</span></span>
    
    <span data-ttu-id="e9405-p103">他們是要移入雲端並修正任何問題的資料庫中執行一個表格的分析。新的拉長資料庫顧問授與它們他們可以預期的 SQL Server 2016，包括哪些表格包含冷資料的可延伸的所有功能的完整概觀。</span><span class="sxs-lookup"><span data-stu-id="e9405-p103">Performed an analysis of the tables in the databases that they intended to move to the cloud and fixed any issues. The new Stretch Database Advisor gave them a full overview of what they can expect from all features in SQL Server 2016, including which tables have cold data that could be stretched.</span></span>
    
2. <span data-ttu-id="e9405-120">升級</span><span class="sxs-lookup"><span data-stu-id="e9405-120">Upgrade</span></span>
    
    <span data-ttu-id="e9405-121">更新現有 SQL 伺服器至 SQL Server 2016 Paris headquarters 資料中心。</span><span class="sxs-lookup"><span data-stu-id="e9405-121">Updated existing SQL servers in the Paris headquarters datacenter to SQL Server 2016.</span></span>
    
3. <span data-ttu-id="e9405-122">冷資料移轉至雲端</span><span class="sxs-lookup"><span data-stu-id="e9405-122">Migrate cold data to the cloud</span></span>
    
    <span data-ttu-id="e9405-p104">使用 SQL Management Studio 中，找出要伸展資料庫和資料表移轉至伸展 Azure 中的資料庫執行個體。一段時間，在背景中 SQL Server 2016 移動的資料庫伸展 Azure 中的歷程資料。</span><span class="sxs-lookup"><span data-stu-id="e9405-p104">Using SQL Management Studio, they identified the databases to stretch and the tables to migrate to instances of Stretch Database in Azure. Over time and in the background, SQL Server 2016 moved the historical data to stretch databases in Azure.</span></span>
    
<span data-ttu-id="e9405-125">以下是執行 SQL Server 2016 Paris headquarters 中的一部伺服器的結果設定。</span><span class="sxs-lookup"><span data-stu-id="e9405-125">Here is the resulting configuration for one server running SQL Server 2016 in the Paris headquarters.</span></span>
  
<span data-ttu-id="e9405-126">**圖 2： 使用延展資料庫中的伺服器 Contoso 的資料中心**</span><span class="sxs-lookup"><span data-stu-id="e9405-126">**Figure 2: Using Stretch Database for a server in Contoso's datacenter**</span></span>

![針對執行 SQL Server 的單一電腦的 Contoso 的組態 SQL Server Stretch Database](images/Contoso_Poster/StretchDB02.png)

  
<span data-ttu-id="e9405-128">圖 2 顯示 Contoso 的資料中心中的應用程式伺服器的使用者查詢成為傳遞至 Azure PaaS Azure SQL 延展資料庫的 SQL 查詢的方式。</span><span class="sxs-lookup"><span data-stu-id="e9405-128">Figure 2 shows how user queries to an application server in Contoso's datacenter become SQL queries that are passed to an Azure SQL Stretch Database in Azure PaaS.</span></span>
  
<span data-ttu-id="e9405-p105">使用者透過現有的應用程式及查詢存取資料。存取原則保持相同。向前移動有磁帶備份不需要。維護備份和還原熱資料所組成。</span><span class="sxs-lookup"><span data-stu-id="e9405-p105">Users access the data through existing apps and queries. Access policies remain the same. Moving forward, there is no need for tape backups. Maintenance consists of backing up and restoring hot data.</span></span>
  
<span data-ttu-id="e9405-133">之後實作 Contoso 拉大資料庫：</span><span class="sxs-lookup"><span data-stu-id="e9405-133">After implementing Stretch Database, Contoso:</span></span>
  
- <span data-ttu-id="e9405-134">85%以減少其內部部署資料儲存需求。</span><span class="sxs-lookup"><span data-stu-id="e9405-134">Reduced its on-premises data storage needs by 85%.</span></span>
    
- <span data-ttu-id="e9405-135">進行不必要的企業版的儲存系統和磁帶封存的依賴的更新。</span><span class="sxs-lookup"><span data-stu-id="e9405-135">Made the update of the enterprise storage system and reliance on magnetic tape archives unnecessary.</span></span>
    
- <span data-ttu-id="e9405-136">大幅減少其每日執行成本。</span><span class="sxs-lookup"><span data-stu-id="e9405-136">Reduced its daily running costs significantly.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="e9405-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="e9405-137">See Also</span></span>

[<span data-ttu-id="e9405-138">Contoso Corporation 的企業案例</span><span class="sxs-lookup"><span data-stu-id="e9405-138">Enterprise scenarios for the Contoso Corporation</span></span>](enterprise-scenarios-for-the-contoso-corporation.md)
  
[<span data-ttu-id="e9405-139">Microsoft Cloud 中的 Contoso</span><span class="sxs-lookup"><span data-stu-id="e9405-139">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="e9405-140">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="e9405-140">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="e9405-141">伸展資料庫</span><span class="sxs-lookup"><span data-stu-id="e9405-141">Stretch Database</span></span>](https://msdn.microsoft.com/library/dn935011.aspx)
  
[<span data-ttu-id="e9405-142">Microsoft 的 Enterprise Cloud 藍圖：IT 決策者的資源</span><span class="sxs-lookup"><span data-stu-id="e9405-142">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)




