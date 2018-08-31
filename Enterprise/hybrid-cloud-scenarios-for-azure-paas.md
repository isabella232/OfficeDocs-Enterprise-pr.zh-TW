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
# <a name="hybrid-cloud-scenarios-for-azure-paas"></a>Azure PaaS 的混合式雲端案例

 **摘要：** 了解混合式架構與案例的 Microsoft 平台做為服務 (PaaS)-以 Azure 中的雲端方案。
  
合併內部資料或運算資源與新的或已轉換應用程式在 Azure PaaS，可以利用雲端效能、 可靠性及向外與行動裝置使用者提供較佳的支援。 
  
## <a name="azure-paas-hybrid-scenario-architecture"></a>Azure PaaS 混合式案例的架構

圖 1 顯示在 Azure 中的 Microsoft PaaS 為基礎的混合式案例的架構。
  
**Azure 中的圖 1： Microsoft PaaS 為基礎的混合式案例**

![Azure 中的 Microsoft PaaS 型混合式案例](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS.png)
  
之架構的每個圖層：
  
- 應用程式與案例
    
    混合式 PaaS 應用程式執行 Azure 中同時使用內部部署 compute 或儲存資源。
    
- 身分識別
    
    包含目錄同步處理或與協力廠商身分識別提供者同盟。
    
- 工作列最右邊的網路
    
    包含您現有的網際網路管道或具有公用對等以 Azure PaaS ExpressRoute 連線。您必須包含 Azure PaaS 應用程式以存取內部部署 compute 或儲存資源的方式。
    
- 內部部署
    
    身分識別與安全性基礎結構和業務 (LOB) 應用程式或 Azure PaaS 應用程式可以安全地存取的資料庫伺服器的現有列所組成。
    
## <a name="azure-paas-hybrid-application"></a>Azure PaaS 混合式應用程式

圖 2 顯示在 Azure 中執行的混合式應用程式的設定。
  
**圖 2： Azure PaaS 為基礎的混合式應用程式**

![Azure PaaS 型混合式應用程式](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps.png)
  
圖 2] 中的內部網路主控儲存裝置或應用程式伺服器與 DMZ 包含 proxy 伺服器上。它會透過網際網路或 ExpressRoute 連線以連線至 Azure PaaS 服務。
  
組織可以提供其 compute 或儲存的資源由 Azure PaaS 混合式應用程式：
  
- 主控 DMZ 中的伺服器上的資源。
    
- 以架設在 DMZ 反向 proxy 伺服器，允許經驗證、 輸入、 HTTPS 型要求送至內部所在的資源。
    
Azure 應用程式可以使用認證：
  
- Azure AD、 以內部身分識別提供者，例如 Windows Server AD 同步處理。
    
- 協力廠商身分識別提供者。
    
### <a name="example-azure-paas-hybrid-application"></a>範例 Azure PaaS 混合式應用程式

圖 3 是執行 Azure 中的範例混合式應用程式。
  
**圖 3： 範例 Azure PaaS 為基礎的混合式應用程式**

![Azure PaaS 型混合式應用程式的範例](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps-Ex.png)
  
圖 3、 LOB 的內部網路主機 app Azure PaaS 主控自訂的行動裝置應用程式。Smartphone 在網際網路上的存取 Azure、 將資料要求傳送至內部部署 LOB 應用程式中自訂的行動裝置應用程式。
  
本範例會為 Azure PaaS 混合式應用程式是自訂的行動裝置應用程式上員工提供最新的連絡人資訊。端對端混合式案例所組成：
  
- Smartphone 應用程式需要驗證，若要執行的內部部署認證。
    
- 自訂行動應用程式正在 Azure PaaS、 要求特定使用者的智慧型手機應用程式的查詢為基礎的員工的相關資訊。
    
- 在 DMZ 來驗證自訂的行動裝置應用程式並將要求轉送反向 proxy 伺服器。
    
- 連絡人的要求，受限於使用者帳戶的權限服務 LOB 應用程式伺服器陣列。
    
因為已與 Azure AD 同步處理在內部身分識別提供者，自訂的行動裝置應用程式與 LOB 應用程式可以驗證要求的使用者帳戶名稱。
  
## <a name="stretch-database-with-sql-server-2016"></a>運用 SQL Server 2016 延展資料庫

伸展資料庫功能可讓您透明和安全地移動冷資料，例如大型表格包含客戶訂單資訊、 Azure 中的 SQL 拉大資料庫已關閉的商務資料的 SQL Server 2016。
  
當拉長、 SQL Server 執行個體、 資料庫、 或甚至是一個表格的內容是 SQL Server 2016 伺服器中的本機資料和 Azure 中的遠端資料的組合。如拉長 SQL Server 2016 自動移到 Azure 會變成合格的資料。
  
圖 4 顯示與 SQL Server 2016 延展資料庫。
  
**圖 4： 以 SQL Server 2016 伸展的資料庫**

![運用 SQL Server 2016 延展資料庫](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps-SQL.png)
  
圖 4] 中的內部網路主控執行 SQL Server 2016 使用小型的本機資料庫伺服器。Azure PaaS 主控 Azure SQL Server 拉大資料庫執行個體與資料庫的延伸部分。T-SQL 查詢傳送至內部部署 SQL server 的內部部署使用者安全地轉寄給 Azure SQL 拉大資料庫，將結果傳回給要求的使用者。
  
 包含的歷程資料的使用者查詢透明轉寄給 Azure SQL 延展資料庫。查詢不需要重新寫入，即使表格會拉長。
  
伸展資料庫提供長期儲存區與透明資料的存取權歷史符合成本效益的選項。它也求解效能及可用性問題發生時表格會變得非常大。
  
如需詳細資訊，請參閱[延展資料庫](https://msdn.microsoft.com/library/dn935011.aspx)。
  
## <a name="see-also"></a>另請參閱

[Microsoft Hybrid Cloud for Enterprise Architects](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)

[Microsoft 的 Enterprise Cloud 藍圖：IT 決策者的資源](https://sway.com/FJ2xsyWtkJc2taRD)



