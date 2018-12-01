---
title: Microsoft SaaS (Office 365) 混合式雲端案例
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: 摘要： 瞭解混合架構與案例的 Microsoft 的 saas 和型雲端方案 (Office 365)。
ms.openlocfilehash: 063cbd03a2cc65a6cd278ab2efcea235079f801b
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123410"
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a>Microsoft SaaS (Office 365) 混合式雲端案例

 **摘要：** 了解混合式架構與案例的 Microsoft 的 saas 和型雲端方案 (Office 365)。
  
合併與與其對應的雲端移轉或長期整合策略的一部分的 Office 365 中的內部部署 Exchange、 SharePoint、 或 Skype for Business。
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a>Microsoft saas 和混合式案例的架構

圖 1 顯示的 Office 365 Microsoft SaaS 為基礎的混合式案例的架構。
  
**圖 1： Office 365 的 Microsoft SaaS 為基礎的混合式案例**

![Office 365 的 Microsoft IaaS 型混合式案例](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS.png)
  
之架構的每個圖層：
  
- 應用程式與案例
    
    有各種 saas 和型混合式案例，對齊繞 Office Server 產品和其 Office 365 對應項目：
    
  - Exchange Server 結合與 Exchange Online （Exchange Server 混合）
    
  - Skype Business server 與 Skype 結合商務線上和新的雲端 PBX 與雲端連接器 Edition 案例
    
  - SharePoint Server 2019、 SharePoint Server 2016、 或 SharePoint Server 2013 與 SharePoint Online （多個案例） 合併
    
    也有 Exchange Online 與 Skype for Business Server 內部部署、 跨產品混合式案例。
    
- 身分識別
    
    可以包含與內部部署 Windows Server AD 目錄同步處理。或者，您可以設定和協力廠商身分識別提供者結盟的 Azure AD。
    
- 工作列最右邊的網路
    
    與 Microsoft Office 365 或 Dynamics 365 對等包含您現有的網際網路管道或 ExpressRoute 連線。
    
- 內部部署
    
    可以包含現有伺服器的 Exchange、 SharePoint 及 Skype for Business，應該更新其最新版本。您可以結合它們與 Office 365 與對應的混合式案例。
    
設定您的 Office 365 開發人員/測試環境，請參閱[Office 365 測試實驗室指南](cloud-adoption-test-lab-guides-tlgs.md)。
  
## <a name="skype-for-business-hybrid"></a>Skype 商務混合式

Skype 商務混合式可讓您將現有的內部部署與 Skype 合併商務 online。某些使用者位於的內部和某些使用者的主伺服器皆線上，但使用者共用相同的工作階段初始通訊協定 (SIP) 網域，例如 contoso.com。您可以使用此混合式組態移轉從內部部署到 Office 365 一段時間，在您的排程。也可以與[Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint)整合 Skype for Business。
  
**圖 2： Skype 商務混合組態**

![Skype 商務混合設定](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB.png)
  
圖 2 顯示組成商務前端集區與 edge server 通訊的 Skype 商務 Online 在 Office 365 中的內部部署 Skype Skype 商務混合式設定。
  
如需詳細資訊，請參閱 ＜ [Plan Business Server 和 Skype 的商務 Online Skype 之間的混合式連線](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity)。
    
## <a name="cloud-pbx-with-skype-for-business-server"></a>含商務用 Skype Server 的雲端 PBX

雲端 PBX 與 Skype Business server 可讓您轉換 Business Server 內部部署拓撲的現有 Skype 與內部部署公用交換電話網路 (PSTN) 連線。 
  
**圖 3: Cloud PBX 與 Skype Business server**

![含商務用 Skype Server 的雲端 PBX](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB-CloudPBX.png)
  
圖 3 是雲端 PBX 與 Skype Business Server 設定、 組成的內部現有的 PBX 或電話閘道、 Skype 商務伺服器和 PSTN 連線至 Office 365，其中包含 Skype for Business 中 Microsoft Cloud PBX線上。
  
位於雲端組織中的使用者可以接收專用交換機 (pbx) 服務從 Microsoft cloud 包含訊號和語音信箱，但可 PSTN 連線能力 （撥號音） 透過提供企業語音從內部Skype 商務伺服器部署。
  
這是更好的範例可讓您逐步移轉至雲端架構服務的混合式組態。您可以在您開始進行商務 Online 將其移至 Skype 保留使用者的語音功能。您可以移動使用者在自己步調，了解其語音功能會繼續否專家隸屬的。 
  
如需詳細資訊，請參閱 ＜ [Plan Business Server 和 Skype 的商務 Online Skype 之間的混合式連線](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity)。
  
如果您已經沒有現有的 Lync Server 或 Skype 商務伺服器部署，您可以使用 Skype Business Cloud 連接器 edition、 封裝的虛擬機器 (Vm) 實作內部部署 PSTN 連線能力與雲端 PBX 的一組。
  
如需詳細資訊，請參閱 ＜ [Plan for Business Cloud 連接器 edition Skype](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition)。

  
## <a name="sharepoint-hybrid"></a>SharePoint 混合式

SharePoint 混合式應 SharePoint Online 在 Office 365 搭配內部部署 SharePoint 伺服器陣列的最佳運用這兩者的、 連線經驗。
  
**圖 4： SharePoint 混合式設定**

![SharePoint 混合式組態](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SP.png)
  
圖 4 顯示組成通訊的 SharePoint Online 在 Office 365 中內部部署 SharePoint 伺服器陣列的 SharePoint 混合式組態。
  
SharePoint 混合式案例：
  
- [混合式商務用 OneDrive](https://docs.microsoft.com/SharePoint/hybrid/configure-hybrid-onedrive-for-businessroadmap)
    
- [混合式外部網路 B2B](https://docs.microsoft.com/sharepoint/create-b2b-extranet)
    
- [混合搜尋](https://docs.microsoft.com/SharePoint/hybrid/configure-cloud-hybrid-searchroadmap)
    
- [混合式設定檔](https://docs.microsoft.com/SharePoint/hybrid/plan-hybrid-profiles)
    
- [混合式選擇器](https://docs.microsoft.com/SharePoint/hybrid/hybrid-picker-in-the-sharepoint-online-admin-center)
    
    很容易啟用使用自動化可從 SharePoint Online 系統管理中心在 Office 365 的混合式組態精靈的混合式案例。
    
- [可延伸混合式 App 啟動器](https://docs.microsoft.com/SharePoint/hybrid/the-extensible-hybrid-app-launcher)
    
    可讓使用者檢視及使用 Office 365 影片和 Delve 應用程式與經驗內其內部部署 SharePoint 伺服器陣列的頁面。
    
這些 SharePoint 混合式案例，可延伸的混合式應用程式啟動器、 以外的所有可用的 SharePoint 2016 與 SharePoint 2013 的使用者。
  
## <a name="exchange-server-2016-hybrid"></a>Exchange Server 2016 混合式

與 Exchange Server 2016 混合，您可以了解 online 使用者的 Exchange Online Office 365 的優點時的內部使用者繼續使用現有的 Exchange Server 基礎結構。 
  
**圖 5： Exchange 2016 混合組態**

![Exchange 2016 混合式組態](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-EX.png)
  
圖 5 顯示通訊與 Exchange Online Protection 和 Office 365 中的信箱的內部部署 Exchange 信箱伺服器所組成的 Exchange 2016 混合式組態。
  
某些使用者擁有的內部部署電子郵件伺服器及某些使用者使用 Exchange Online 中，但所有使用者都共用相同的電子郵件地址空間。 
  
此混合式組態：
  
- 當您移轉至 Exchange Online 一段時間，在您的排程上時如何運用現有的 Exchange Server 基礎結構。
    
- 可讓您以支援遠端站台不含演變在分公司的基礎結構。
    
- 可讓您透過 Exchange Online Protection 的內送網際網路電子郵件路由 Office 365 中。
    
- 您能跨國子公司需要資料至位於內部部署組織的需求。
    
您也可以與其他 Microsoft Office 365 應用程式，包括 Skype 商務 Online 與 SharePoint Online 整合此混合式組態。
  
如需詳細資訊，請參閱[Exchange Server 混合式部署](https://docs.microsoft.com/exchange/exchange-hybrid)。
  
## <a name="see-also"></a>請參閱

[Microsoft Hybrid Cloud for Enterprise Architects](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)

