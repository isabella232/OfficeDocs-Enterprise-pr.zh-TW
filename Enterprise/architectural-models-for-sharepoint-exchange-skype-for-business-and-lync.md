---
title: "適用於 SharePoint、Exchange、Skype for Business 和 Lync 的架構模型"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Strat_O365_Enterprise
- Ent_Architecture
ms.assetid: 5b49fa68-f8f2-4705-af96-5f5475e8539a
description: "摘要： 取得 IT 海報說明架構模型、 部署及 SharePoint、 Exchange、 Skype for Business 和 Lync 的平台選項。"
ms.openlocfilehash: d50a3eae1e5fe308d71afaef398fe97e2d37f9cb
ms.sourcegitcommit: 38001ca323a60126fcf31667393c31322044cedc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2018
---
# <a name="architectural-models-for-sharepoint-exchange-skype-for-business-and-lync"></a>適用於 SharePoint、Exchange、Skype for Business 和 Lync 的架構模型

 **摘要：**取得 IT 海報說明架構模型、 部署及 SharePoint、 Exchange、 Skype for Business 和 Lync 的平台選項。
  
這些 IT 海報描述適用於 SharePoint、Exchange、商務用 Skype 和 Lync 的結構模型和部署選項，並提供在 Microsoft Azure 內部署 SharePoint 的設計資訊。
  
與 Office 365，您可以提供使用者熟悉以雲端式服務的共同作業及通訊服務。有幾個例外的使用者經驗維持不變是否要維護的內部部署或使用 Office 365。此整合的使用者經驗會決定要放置每個工作負載較簡單和例如會導致問題：
  
- 當為您的個別工作負載選擇平台時，您會如何判斷？
    
- 是否應該保留任何內部部署服務？
    
- 擁有適當混合式部署的案例是怎麼樣的？
    
- Microsoft Azure 如何配合的圖片中？
    
- 在 Azure 內 Office Sever 工作負載的支援組態為何？
    
> [!TIP]
> 此頁面上的海報大多提供多種語言版本，包括中文、英文、法文、德文、義大利文、日文、韓文、葡萄牙文、俄文和西班牙文。若要下載以上其中一種語言的海報，請按一下該海報的 [更多語言] 連結。讓我們知道您的想法！
  
讓我們知道您的心得！請傳送電子郵件給我們：[cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com)。 
  
此頁面可讓您連結到下列的海報︰
  
- **架構模型海報 （英文）**您可以使用這些資源來判斷您的理想的平台和設定 SharePoint 2016 和 Skype 的商務 2015年。
    
  - [Microsoft SharePoint 2016 架構模型](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_ArchModel)
    
  - [在 Office 365 的 OneDrive 的多個地理位置預覽](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#MultiGeoO365ODB)
    
  - [SharePoint Server 2016 資料庫](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_Databases)
    
  - [Microsoft Skype 商務 2015年架構模型](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SfB2015_ArchModel)
    
- **平台選項海報 （英文）**您可以使用這些資源來判斷您的理想的平台和 SharePoint 2013、 Exchange 2013 和 Lync 2013 的設定。
    
  - [SharePoint 2013 平台選項](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2013_Options)
    
  - [Exchange 2013 平台選項](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Exch2013_options)
    
  - [Lync 2013 平台選項](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Lync2013_Options)
    
- **SharePoint Server 2013 in Azure 解決方案海報 （英文）**您可以使用這些 IT 海報 （英文） 決定的設計與 SharePoint Server 2013 工作量 Azure 基礎結構服務中的設定。
    
  - [Microsoft Azure using SharePoint Server 2013 中的網際網路網站](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Azure_sharepoint2013)
    
  - [設計範例： Microsoft Azure 中的 SharePoint 2013 的網際網路網站](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#DesignSampleInternetSites)
    
  - [以 Microsoft Azure 的 SharePoint 災害復原](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#sharepoint_recovery_Azure)
    
## <a name="architectural-models-posters"></a>架構模型海報

這些新推出的 SharePoint 2016 和商務用 Skype 2015 IT 海報會以方便列印的格式，提供方法來比較不同的部署方法。每份海報會提供一份清單，內含所有可用的組態或平台，並提供每個選項的下列資訊︰
  
- **概觀 （英文)**平台，包括概念圖表簡短摘要。
    
- **適合**在理想狀況下適合特定的平台的常見案例。
    
- **授權需求**您必須部署的授權。
    
- **架構工作**您必須制定作為架構師決策。
    
- **IT 專業人員的任務或責任**您的 IT 人員需要規劃的每日的責任。
    
### <a name="microsoft-sharepoint-2016-architectural-models"></a>Microsoft SharePoint 2016 架構模型
<a name="SP2016_ArchModel"> </a>

|**項目**|**描述**|
|:-----|:-----|
|[![SharePoint 2016 架構模型海報的縮圖](images/7d3e590c-1f3b-42cf-920d-9edac8fa3e04.png)          ](https://www.microsoft.com/download/details.aspx?id=52650) <br/> ![PDF 檔案](images/ITPro_Other_PDFicon.png)[PDF](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.pdf)  \| ![Visio 檔案](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.vsdx)  \| ![請參閱其他語言版本的頁面](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[更多語言](https://www.microsoft.com/download/details.aspx?id=52650) <br/> | 此 IT 海報描述商務決策者和解決方案架構設計人員需了解的 SharePoint Online、Microsoft Azure 和 SharePoint 內部部署組態。 <br/><br/> - **SharePoint Online (SaaS)** -取用 SharePoint 透過軟體即服務 (SaaS) 訂閱模型。 <br/> - **SharePoint 混合式**-將您的 SharePoint 網站和應用程式移至您自己的腳步雲端。 <br/> - **Azure (IaaS) 中的 SharePoint** -您擴充 Microsoft Azure 到內部部署環境及部署 SharePoint 2016 伺服器發生。（這是高可用性/嚴重損壞修復及開發人員/測試環境的建議）。<br/> - **SharePoint 內部**-規劃、 部署、 維護及自訂 SharePoint 環境中您維護資料中心。 <br/> |
   
### <a name="multi-geo-preview-for-onedrive-in-office-365"></a>在 Office 365 的 OneDrive 的多個地理位置預覽
<a name="MultiGeoO365ODB"> </a>

|**項目**|**描述**|
|:-----|:-----|
|[![Office 365 模型中的多個地理位置 OneDrive](images/c6c1b7cd-7833-46fb-9eec-c12150c260d9.png)          ](http://download.microsoft.com/download/0/5/9/0594634F-7893-4201-938A-C2FF2F21B655/Multi-Geo-ODB.pdf) <br/> ![PDF 檔案](images/ITPro_Other_PDFicon.png)[PDF](http://download.microsoft.com/download/0/5/9/0594634F-7893-4201-938A-C2FF2F21B655/Multi-Geo-ODB.pdf)  \| ![Visio 檔案](images/ITPro_Other_VisioIcon.jpg)[Visio](http://download.microsoft.com/download/0/5/9/0594634F-7893-4201-938A-C2FF2F21B655/Multi-Geo-ODB.vsdx) <br/> | 此模型是在 Office 365，仍在私人 preview 中的多個地理位置 OneDrive 的一個頁面概觀。此模型包含：<br/><br/> -優點 <br/> -部署步驟 <br/> -設定範例 <br/><br/>  在 Office 365 的 OneDrive 的多個地理位置 Preview 的相關資訊，請按一下[這裡](https://aka.ms/onedrivemultigeo)。  <br/> |
   
### <a name="sharepoint-server-2016-databases"></a>SharePoint Server 2016 資料庫
<a name="SP2016_Databases"> </a>

|**項目**|**描述**|
|:-----|:-----|
|[![SharePoint Server 2016 資料庫海報的縮圖](images/c53e9de7-3bf8-446d-8766-e6700c8dd8e1.png)          ](https://www.microsoft.com/download/details.aspx?id=55041) <br/> ![PDF 檔案](images/ITPro_Other_PDFicon.png)[PDF](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.pdf)  \| ![Visio 檔案](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.vsdx)  \| ![請參閱其他語言版本的頁面](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[更多語言](https://www.microsoft.com/download/details.aspx?id=55041) <br/> | 此 IT 海報是適用於 SharePoint Server 2016 資料庫的快速參考指南。每個資料庫均會有以下詳細資料：<br/><br/> 半形 <br/> -調整指導 <br/> -I/O 模式 <br/> -需求 <br/><br/>  第一頁包含 SharePoint 系統資料庫和擁有多個資料庫的服務應用程式。第二個頁面會顯示所有具有單一資料庫的服務應用程式。<br/><br/>  如需 SharePoint Server 2016 資料庫的詳細資訊，請參閱[資料庫類型與描述在 SharePoint Server 2016](https://technet.microsoft.com/en-us/library/cc678868%28v=office.16%29.aspx) <br/> |
   
### <a name="microsoft-skype-for-business-2015-architectural-models"></a>Microsoft 商務用 Skype 2015 架構模型
<a name="SfB2015_ArchModel"> </a>

|**項目**|**描述**|
|:-----|:-----|
|[![Skype for Business 架構模型海報的縮圖](images/132288c0-6ae4-4394-88ab-b57dae367714.png)          ](https://www.microsoft.com/download/details.aspx?id=55022) <br/> ![PDF 檔案](images/ITPro_Other_PDFicon.png)[PDF](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.pdf)  \| ![Visio 檔案](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.vsd)  \| ![請參閱其他語言版本的頁面](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[更多語言](https://www.microsoft.com/download/details.aspx?id=55022) <br/> |此海報說明 Skype 商務 Online、 內部部署、 混合、 雲端 PBX 與整合 Exchange 和 SharePoint 設定該商務決策者適用及解決方案架構師需要了解。 <br/><br/> 擬引發傳達方式的不同的基礎架構模型透過商務 online Skype 和 Skype 的內部部署商務可供 IT 專業人員的對象。 <br/><br/>開始使用最佳無論設定符合貴組織的需求和未來的計劃。請考慮並視需要使用其他人。例如，您可能要考慮整合 Exchange 和 SharePoint 或 Microsoft Cloud PBX 可以利用的解決方案。  <br/> |
   
## <a name="platform-options-posters"></a>平台選項海報

這些適用於 SharePoint 2013、Exchange 2013 和 Lync 2013 的 IT 海報，會以大型海報格式，來比較不同的部署方法，讓差異一目了然。每份海報會提供一份清單，內含所有可用的組態或平台，並提供每個選項的下列資訊︰
  
- **概觀 （英文)**平台，包括概念圖表簡短摘要。
    
- **適合**在理想狀況下適合特定的平台的常見案例。
    
- **授權需求**您必須部署的授權。
    
- **架構工作**您必須制定作為架構師決策。
    
- **IT 專業人員的任務或責任**您的 IT 人員需要規劃的每日的責任。
    
## <a name="sharepoint-2013-platform-options"></a>SharePoint 2013 平台選項
<a name="SP2013_Options"> </a>

****

|**項目**|**描述**|
|:-----|:-----|
|[![SharePoint 2013 Platform Options 的縮圖影像](images/SP_PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=40332) <br/> ![PDF 檔案](images/ITPro_Other_PDFicon.png)[PDF](http://go.microsoft.com/fwlink/p/?LinkId=324594)  \| ![Visio 檔案](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=324593)  \| ![請參閱其他語言版本的頁面](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[更多語言](https://www.microsoft.com/download/details.aspx?id=40332) <br/> |如需商務決策者 (Bdm) 和架構師，此模型說明 SharePoint 2013、 Office 365、 Office 365、 Azure、 與內部部署僅部署的內部部署混合式中的 SharePoint 平台選項。包含每個架構、 建議、 授權需求及架構師和 IT 專業人員必須針對每個平台的工作清單的概觀。會醒目提示的數個 Azure 上的 SharePoint 解決方案。<br/><br/>此海報可存取的文字版本，請參閱 ＜[存取圖表-Microsoft SharePoint 2013 Platform Options](accessible-diagrammicrosoft-sharepoint-2013-platform-options.md)。  <br/> |
   
## <a name="exchange-2013-platform-options"></a>Exchange 2013 平台選項
<a name="Exch2013_options"> </a>

****

|**項目**|**描述**|
|:-----|:-----|
|[![Exchange Platform Options 的縮圖影像](images/ITPro_Other_Exchange2013PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=42676) <br/> ![PDF 檔案](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkID=398740)  \| ![Visio 檔案](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkID=398742)  \| ![請參閱其他語言版本的頁面](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[更多語言](https://www.microsoft.com/download/details.aspx?id=42676) <br/> |Bdm 及架構師，此模型說明 Exchange 2013 可用的平台選項。客戶可以從 Exchange Online 與 Office 365，混合式 Exchange，Exchange Server 內部部署和裝載 Exchange 選擇。海報包含每個架構] 選項，包括每個、 授權需求以及 IT 專業人員的責任最理想的情況的詳細資訊。<br/><br/>此海報可存取的文字版本，請參閱 ＜[存取圖表-Microsoft Exchange 2013 平台選項](accessible-diagrammicrosoft-exchange-2013-platform-options.md)。  <br/> |
   
## <a name="lync-2013-platform-options"></a>Lync 2013 平台選項
<a name="Lync2013_Options"> </a>

****

|**項目**|**描述**|
|:-----|:-----|
|[![Lync Platform Options 的縮圖影像](images/Lync_PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41677) <br/> ![PDF 檔案](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkID=391837)  \| ![Visio 檔案](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkID=391839)  \| ![請參閱其他語言版本的頁面](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[更多語言](https://www.microsoft.com/download/details.aspx?id=41677) <br/> |對於 BDM 和架構設計人員，這種模型會描述 Exchange 2013 可用的平台選項。客戶可以從 Office 365 中的 Exchange Online、混合式 Exchange、內部部署 Exchange Server 和 Exchange 託管中選擇。IT 海報包含每個架構的選項，包括最理想的情況下，每一個授權需求以及 IT 專業人員的責任。    <br/> |
   
## <a name="sharepoint-in-azure-solutions-posters"></a>Azure 解決方案海報內的 SharePoint
<a name="Lync2013_Options"> </a>

這些 IT 海報 （英文） 會顯示使用中的大型海報格式的 SharePoint Server 2013 的 Azure 型解決方案。
  
### <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a>Microsoft Azure 中使用 SharePoint Server 2013 的網際網路網站
<a name="Azure_sharepoint2013"> </a>

****

|**項目**|**描述**|
|:-----|:-----|
|[![在 Azure 中使用 SharePoint 的網際網路網站的影像](images/MS_AZ_SPInternetSites.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41992) <br/> ![PDF 檔案](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)  \| ![Visio 檔案](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)  \| ![請參閱其他語言版本的頁面](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[更多語言](https://www.microsoft.com/download/details.aspx?id=41992) <br/> |此海報概述重要的設計活動和建議的網際網路 Azure 中的網站架構選項。此海報可存取的文字版本，請參閱 ＜[存取圖表-Microsoft Azure 中的 SharePoint 2013 的網際網路網站](accessible-diagraminternet-sites-in-microsoft-azure-for-sharepoint-2013.md)。<br/><br/> 如需詳細資訊，請參閱下列文章：  <br/><br/> - [Microsoft Azure using SharePoint Server 2013 中的網際網路網站](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) <br/> |
   
### <a name="design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>設計範例：Microsoft Azure 中的 SharePoint 2013 網際網路網站
<a name="DesignSampleInternetSites"> </a>

****

|**項目**|**描述**|
|:-----|:-----|
|[![圖像的設計範例： Microsoft Azure 中的 SharePoint 2013 的網際網路網站](images/MS_AZ_InternetSitesDesignSample.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41991) <br/> ![PDF 檔案](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| ![Visio 檔案](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)  \| ![請參閱其他語言版本的頁面](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[更多語言](https://www.microsoft.com/download/details.aspx?id=41991) <br/> |使用此設計範例為起點網際網路對向網站架構在 Azure 中使用 SharePoint Server 2013。此海報可存取的文字版本，請參閱 ＜[存取圖表-設計範例： Microsoft Azure 中的 SharePoint 2013 的網際網路網站](accessible-diagramdesign-sample-internet-sites-in-microsoft-azure-for-sharepoint.md)。<br/><br/> 如需詳細資訊，請參閱下列文章：  <br/><br/> - [Microsoft Azure using SharePoint Server 2013 中的網際網路網站](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) <br/> |
   
### <a name="sharepoint-disaster-recovery-to-microsoft-azure"></a>對於 Microsoft Azure 的 SharePoint 嚴重損壞修復
<a name="sharepoint_recovery_Azure"> </a>

****

|**項目**|**描述**|
|:-----|:-----|
|[![Azure 的 SharePoint 災害復原程序](images/SP_DR_Azure.png)          ](https://www.microsoft.com/download/details.aspx?id=41993) <br/> ![PDF 檔案](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555)  \| ![Visio 檔案](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)  \| ![請參閱其他語言版本的頁面](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[更多語言](https://www.microsoft.com/download/details.aspx?id=41993) <br/> |此 IT 海報說明 Azure 中的災害復原環境的架構原則。此海報可存取的文字版本，請參閱 ＜[存取圖表-至 Microsoft Azure 的 SharePoint 災害復原](accessible-diagramsharepoint-disaster-recovery-to-microsoft-azure.md)。<br/><br/> 如需詳細資訊，請參閱下列文章：  <br/><br/> - [SharePoint Server 2013 Disaster Recovery in Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md) <br/> - [Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) <br/> |
   
## <a name="see-also"></a>請參閱

<a name="Lync2013_Options"> </a>

[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)
  
[雲端採用測試實驗室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[混合式解決方案](hybrid-solutions.md)




