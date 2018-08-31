---
title: 將歷程記錄交易資料移至雲端
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 3e9c405a-415b-4584-aa7e-f2489299c457
description: 摘要： 如何實作 Contoso SQL Server 伸展以減少其內部部署資料儲存需求及每日執行成本的資料庫。
ms.openlocfilehash: 791b5d4f14ba7246221cf9b459c31c9ba1b54099
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915718"
---
# <a name="moving-historical-transaction-data-to-the-cloud"></a>將歷程記錄交易資料移至雲端

 **摘要：** Contoso 的實作方式以減少其內部部署資料儲存需求及每日執行成本的 SQL Server 延展資料庫。
  
Contoso 的企業版的儲存系統儲存大量的嚴格該法規需求與行銷 research 歷史交易資料和 BI 耗費趨勢分析。Contoso 也需要從磁帶、 大量消耗時間的程序還原封存的資料。Contoso 的企業儲存系統中的硬體已接近其週期結束並取代其就是很高。 
  
可調整其內部部署資料中心來關閉其業務需求的一部分，Contoso 選擇升級至 SQL Server 2016 因拉大資料庫混合式功能以及與 Azure 其緊密整合。伸展資料庫允許將冷資料其表格中的資料從內部部署移至雲端儲存 Contoso 的本機磁碟空間釋放及降低維護。熱和冷資料位於相同的資料表及一定是適用於維護，例如備份與還原和應用程式和其使用者。圖 1 顯示延展資料庫。
  
**圖 1： SQL Server 伸展資料庫**

![SQL Server Stretch Database 做為混合式資料解決方案](media/Contoso-Poster/StretchDB01.png)
  
圖 1 顯示的 SQL 用戶端執行 SQL Server 2016、 將其轉寄到 Azure PaaS Azure SQL 延展資料庫的伺服器所傳送的 T-SQL 查詢。
  
如需詳細資訊，請參閱[延展資料庫](https://msdn.microsoft.com/library/dn935011.aspx)。
  
Contoso 用來將其歷程資料移至雲端的下列步驟：
  
1. 分析資料庫
    
    他們是要移入雲端並修正任何問題的資料庫中執行一個表格的分析。新的拉長資料庫顧問授與它們他們可以預期的 SQL Server 2016，包括哪些表格包含冷資料的可延伸的所有功能的完整概觀。
    
2. 升級
    
    更新現有 SQL 伺服器至 SQL Server 2016 Paris headquarters 資料中心。
    
3. 冷資料移轉至雲端
    
    使用 SQL Management Studio 中，找出要伸展資料庫和資料表移轉至伸展 Azure 中的資料庫執行個體。一段時間，在背景中 SQL Server 2016 移動的資料庫伸展 Azure 中的歷程資料。
    
以下是執行 SQL Server 2016 Paris headquarters 中的一部伺服器的結果設定。
  
**圖 2： 使用延展資料庫中的伺服器 Contoso 的資料中心**

![針對執行 SQL Server 的單一電腦的 Contoso 的組態 SQL Server Stretch Database](media/Contoso-Poster/StretchDB02.png)

  
圖 2 顯示 Contoso 的資料中心中的應用程式伺服器的使用者查詢成為傳遞至 Azure PaaS Azure SQL 延展資料庫的 SQL 查詢的方式。
  
使用者透過現有的應用程式及查詢存取資料。存取原則保持相同。向前移動有磁帶備份不需要。維護備份和還原熱資料所組成。
  
之後實作 Contoso 拉大資料庫：
  
- 85%以減少其內部部署資料儲存需求。
    
- 進行不必要的企業版的儲存系統和磁帶封存的依賴的更新。
    
- 大幅減少其每日執行成本。
    
## <a name="see-also"></a>另請參閱

[Contoso Corporation 的企業案例](enterprise-scenarios-for-the-contoso-corporation.md)
  
[Microsoft 雲端中的 Contoso](contoso-in-the-microsoft-cloud.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)

[伸展資料庫](https://msdn.microsoft.com/library/dn935011.aspx)
  
[Microsoft 的 Enterprise Cloud 藍圖：IT 決策者的資源](https://sway.com/FJ2xsyWtkJc2taRD)




