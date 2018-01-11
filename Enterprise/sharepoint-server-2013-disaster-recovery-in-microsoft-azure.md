---
title: SharePoint Server 2013 Disaster Recovery in Microsoft Azure
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Deployment
ms.assetid: e9d14cb2-ff28-4a18-a444-cebf891880ea
description: "摘要： 使用 Azure，您可以為您的內部部署 SharePoint 伺服器陣列建立嚴重損壞修復環境。本文說明如何設計及實作此解決方案。"
ms.openlocfilehash: be1a369bb87a5a63d9c266977c32c64fc55f3630
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2018
---
# <a name="sharepoint-server-2013-disaster-recovery-in-microsoft-azure"></a>SharePoint Server 2013 Disaster Recovery in Microsoft Azure

 **摘要：**使用 Azure，您可以為您的內部部署 SharePoint 伺服器陣列建立嚴重損壞修復環境。本文說明如何設計及實作此解決方案。
  
 發生災害事件 SharePoint 內部部署環境，您最高的優先順序時若要取得執行一次迅速系統。與 SharePoint 的嚴重損壞修復時更快速且更容易必須已在執行 Microsoft Azure 中的備份環境。本影片說明 SharePoint 暖容錯移轉環境的主要概念及補充本文中提供的完整詳細資料。
  
![視訊 (播放按鈕) 圖示](images/mod_icon_video_M.png)
  
使用本文使用下列解決方案模型： **SharePoint Disaster Recovery in Microsoft Azure**。
  
[![SharePoint 到 Azure 的災害復原程序](images/SP_DR_Azure.png)
  
] (https://go.microsoft.com/fwlink/p/?LinkId=392555)
  
![PDF 檔案](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555) |![Visio 檔案](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)
  
本文內容：
  
- [使用 Azure 基礎結構服務的嚴重損壞修復](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#AZ)
    
- [解決方案描述](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#SOL)
    
- [詳細的架構](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#arch)
    
- [嚴重損壞復原藍圖](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#RDmap)
    
- [階段 1： 設計嚴重損壞修復環境](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase1)
    
- [階段 2： 建立 Azure 虛擬網路和 VPN 連線](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase2)
    
- [階段 3： 部署 Active Directory 及網域名稱服務以 Azure 虛擬網路](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase3)
    
- [階段 4： 部署在 Azure 中的 SharePoint 復原伺服器陣列](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase4)
    
- [階段 5： 設定伺服器陣列之間 DFSR](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase5)
    
- [階段 6： 設定記錄傳送至修復伺服器陣列](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase6)
    
- [階段 7： 驗證容錯移轉及復原](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase7)
    
- [Microsoft 概念證明環境](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#POC)
    
- [疑難排解秘訣](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Troubleshooting)
    
## <a name="use-azure-infrastructure-services-for-disaster-recovery"></a>使用 Azure 基礎結構服務的嚴重損壞修復
<a name="AZ"> </a>

許多組織沒有損毀修復環境 for SharePoint，可以是昂貴建立及維護的內部。Azure 基礎結構服務提供強大嚴重損壞復原環境的更多彈性、 較不昂貴比內部替代項目。
  
使用 Azure 基礎結構服務的優點包括：
  
- **較少的高成本資源**維護及工資資源少於內部嚴重損壞修復環境。資源數目取決於您選擇的嚴重損壞修復環境： 冷待命、 暖待命或熱待命。
    
- **更好的資源彈性**在發生災害時輕鬆地向外延展負載要求修復 SharePoint 伺服器陣列。當您不再需要資源的向外。
    
- **較低的資料中心承諾**使用 Azure 基礎結構服務而不是在不同的區域中的次要資料中心內演變。
    
有較不複雜組織剛入門嚴重損壞修復選項及進階具有高可靠度需求的組織的選項。在雲端平台上主控環境時，有點不同冷、 暖，以及熱待命環境中的定義。下表說明這些建置在 Azure 中的 SharePoint 復原伺服器陣列的環境。
  
**表格： 復原環境**

|**復原環境的類型**|**描述**|
|:-----|:-----|
|熱  <br/> |完全大小的伺服器陣列已佈建、 更新及執行處於待命狀態。  <br/> |
|暖  <br/> |在伺服器陣列內建和虛擬機器都在執行並更新。  <br/> 復原作業包含附加內容資料庫、 佈建服務應用程式和編目的內容。  <br/> 在伺服器陣列可以是實際執行伺服器陣列較小版本，然後向外延展到完整的使用者提供服務。  <br/> |
|冷  <br/> |在伺服器陣列完全建置基礎，但已停止虛擬機器。  <br/> 維護環境包含隨時啟動虛擬機器、 修補、 更新及驗證環境。  <br/> 開始在發生災害時完整的環境。  <br/> |
   
請務必評估貴組織的復原時間目標 (Rto) 及復原點目標 (RPOs)。這些需求決定哪些環境是最適合組織的投資。
  
本文的指示說明如何實作暖待命環境。您可以也適應該冷待命環境中，但您必須遵循以支援這種環境的其他程序。本文不會說明如何實作熱待命環境。
  
如需嚴重損壞修復解決方案的詳細資訊，請參閱[高可用性和災害復原概念 in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkID=393114)和[選擇 SharePoint 2013 的災害復原策略](https://go.microsoft.com/fwlink/p/?linkid=203228)。
  
## <a name="solution-description"></a>解決方案描述
<a name="SOL"> </a>

暖待命嚴重損壞修復解決方案需要下列環境：
  
- 內部部署 SharePoint 實際執行伺服器陣列
    
- 在 Azure 中復原 SharePoint 伺服器陣列
    
- 兩個環境之間的網站 VPN 連線
    
下圖說明下列三個元素。
  
**圖： 元素的 Azure 中暖待命解決方案**

![Azure 中 SharePoint 暖待命解決方案的元素](images/AZarch_AZWarmStndby.png)
  
SQL Server 記錄傳送與分散式檔案系統複寫 (DFSR) 用於將資料庫備份和交易記錄檔複製到 Azure 中的復原伺服器陣列： 
  
- DFSR 會傳送到復原環境的實際執行環境中的記錄檔。在 WAN 案例中，DFSR 會比在 Azure 中傳送直接至次要伺服器的記錄檔更有效率。
    
- 記錄檔會在 Azure 中的復原環境的 SQL server 重新顯示。
    
- 除非執行復原練習，未附加傳送記錄 SharePoint 內容資料庫復原環境中。
    
執行下列步驟來復原伺服器陣列：
  
1. 停止記錄傳送。
    
2. 停止接受主要伺服器陣列的流量。
    
3. 重新顯示的最後一個交易記錄檔。
    
4. 將內容資料庫附加至伺服器陣列。
    
5. 複寫的服務資料庫還原服務應用程式。
    
6. 更新為指向的復原伺服器陣列的網域名稱系統 (DNS) 記錄。
    
7. 開始完整編目。
    
我們建議您定期排練這些步驟與文件它們可以協助確保您 live 復原順利執行。附加內容資料庫還原服務應用程式可能需要一些時間和通常需要一些手動設定。
  
執行復原後，此解決方案會提供下表列出的項目。
  
**表格： 解決方案復原目標**

|**項目**|**描述**|
|:-----|:-----|
|網站和內容  <br/> |網站和內容都可以在復原環境。  <br/> |
|搜尋的新執行個體  <br/> |此暖待命解決方案，不會從搜尋資料庫還原搜尋。復原伺服器陣列中的搜尋元件設定為 [同樣盡可能實際執行伺服器陣列。還原網站與內容之後，搜尋索引重建啟動完整編目。您不需要等候完成提供網站及內容編目。  <br/> |
|服務  <br/> | 從記錄傳送資料庫還原資料儲存在資料庫的服務。只被啟動請勿在資料庫中儲存資料的服務。 <br/>  並非所有的服務與資料庫必須還原。下列服務不必從資料庫還原並只可啟動容錯移轉後： <br/>  Usage and Health Data Collection <br/>  State Service <br/>  Word automation <br/>  不會使用資料庫的任何其他服務 <br/> |
   
您可以使用 Microsoft 諮詢服務 (ATL-MCS-001) 或協力廠商工具來處理更複雜復原目標。下表摘要說明這些。
  
**表格： 其他項目可以定址的 ATL-MCS-001 或協力廠商**

|**項目**|**描述**|
|:-----|:-----|
|同步處理自訂伺服器陣列方案  <br/> |理想狀況下，復原伺服器陣列設定為與實際執行伺服器陣列相同。您可以使用顧問或協力廠商用來評估已複寫自訂伺服器陣列方案以及是否為位置保持同步的兩個環境的程序。  <br/> |
|連線至資料來源內部  <br/> |它可能不是實際複寫至後端資料系統，如備份網域控制站 (BDC) 連線及搜尋內容來源的連線。  <br/> |
|搜尋還原案例  <br/> |企業搜尋部署往往許多唯一和複雜，因為還原搜尋資料庫需要更大的投資。您可以使用識別及實作您的組織可能需要的搜尋還原案例 （英文） 或協力廠商。  <br/> |
   
本文中提供的指導假設內部部署伺服器陣列已設計及部署。
  
## <a name="detailed-architecture"></a>詳細架構
<a name="arch"> </a>

理想狀況下，在 Azure 中的復原伺服器陣列設定為實際執行伺服器陣列上部署，包括下列與相同：
  
- 伺服器角色相同的表示法
    
- 相同的設定的自訂項目
    
- 搜尋元件的相同的設定
    
在 Azure 環境可以是實際執行伺服器陣列較小版本。如果您打算容錯移轉後的向外延展的復原伺服器陣列，務必要最初代表每一種伺服器角色。
  
某些組態中可能不是實際複寫容錯移轉環境中。請務必測試容錯移轉程序和環境以協助確保容錯移轉伺服器陣列提供預期的服務層級。
  
此解決方案不擬定特定拓撲的 SharePoint 伺服器陣列。此解決方案的重點是使用 Azure 容錯移轉伺服器陣列並實作記錄傳送和 DFSR 兩個環境之間。
  
### <a name="warm-standby-environments"></a>暖待命環境

在暖待命環境中，執行 Azure 環境中的所有虛擬機器。環境已備妥可供容錯移轉練習或事件。
  
下圖說明從內部部署 SharePoint 伺服器陣列至 Azure 型 SharePoint 伺服器陣列設定為暖待命環境的災害復原解決方案。
  
**圖： 拓撲和實際執行伺服器陣列及暖待命復原伺服器陣列的主要元素**

![顯示 SharePoint 實際執行伺服器陣列和暖待命復原伺服器陣列的拓撲和重要元素。](images/AZarchWarmStndby.gif)
  
在此圖表中：
  
- 並排說明兩個環境： 內部部署 SharePoint 伺服器陣列和 Azure 中的暖待命伺服器陣列。
    
- 每個環境都包括檔案共用。
    
- 每個伺服器陣列包含四個層。若要達到高可用性，每一層包含兩個伺服器或針對特定角色，例如前端服務、 分散式快取、 後端伺服器的服務，以及資料庫進行完全相同設定的虛擬機器。未在此圖中以圖說文字特定元件的重要。設定兩個伺服器陣列進行完全相同。
    
- 第四層是資料庫層。記錄傳送用來將記錄從內部部署環境中的次要資料庫伺服器複製至相同的環境中的檔案共用。
    
- DFSR 會將檔案從內部部署環境中的檔案共用複製到 Azure 環境中的檔案共用。
    
- 記錄傳送會重新執行至復原環境中的 SQL Server AlwaysOn 可用性群組的主要複本 Azure 環境中的記錄從檔案共用。
    
### <a name="cold-standby-environments"></a>冷待命環境

在冷待命環境中，大部分的 SharePoint 伺服器陣列虛擬機器可以為關閉。（建議有時會啟動虛擬機器，例如每兩週或一個月一次使每部虛擬機器可以與網域同步處理。）Azure 復原環境中的下列虛擬機器必須保持執行以協助確保記錄傳送和 DFSR 連續作業：
  
- 檔案共用
    
- 主要的資料庫伺服器
    
- 至少一個執行 Windows Server Active Directory 網域服務與 DNS 的虛擬機器
    
下圖顯示 Azure 容錯移轉環境中執行檔案共用虛擬機器和主要的 SharePoint 資料庫虛擬機器。所有其他 SharePoint 虛擬機器已停止。Windows Server Active Directory 和 DNS 執行的虛擬機器時不會顯示。
  
**圖： 使用虛擬機器中執行的冷待命復原伺服器陣列**

![Azure 中 SharePoint 冷待命解決方案的元素](images/AZarch_AZColdStndby.png)
  
容錯移轉之後冷待命環境中，所有虛擬機器已都啟用，且方法，以達到高可用性的資料庫伺服器必須設定，例如 SQL Server AlwaysOn 可用性群組。
  
如果已實作多個儲存群組 （資料庫遍佈多個 SQL Server 高可用性設定），每個儲存群組的主要資料庫必須執行接受其儲存群組相關聯的記錄檔。
  
### <a name="skills-and-experience"></a>技能與經驗

此嚴重損壞復原解決方案使用多個技術。為了協助確保這些技術互動如預期般運作，必須安裝並已正確設定內部部署和 Azure 環境中的每個元件。建議的人員或小組會設定此解決方案的強式使用知識與實機操作技巧與下列文章所述的技術：
  
- [分散式的檔案系統 (DFS) 複寫服務](https://go.microsoft.com/fwlink/p/?LinkId=392698)
    
- [Windows Server 容錯移轉叢集 (WSFC) 與 SQL Server](https://go.microsoft.com/fwlink/p/?LinkId=392701)
    
- [AlwaysOn 可用性群組 (SQL Server)](https://go.microsoft.com/fwlink/p/?LinkId=392725)
    
- [備份及還原的 SQL Server 資料庫](https://go.microsoft.com/fwlink/p/?LinkId=392728)
    
- [SharePoint Server 2013 的安裝與伺服器陣列部署](https://go.microsoft.com/fwlink/p/?LinkId=393119)
    
- [Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=392729)
    
最後，我們建議指令碼可用來自動化工作與這些技術相關聯的技巧。有可能使用可用的使用者介面完成此解決方案所述的所有工作。不過，手動方法時間取用及出錯可與提供一致的結果。
  
除了 Windows PowerShell 中也有 SQL Server、 SharePoint Server 及 Azure 的 Windows PowerShell 文件庫。記得 T-SQL，這也有助於減少設定及維護嚴重損壞修復環境的時間。
  
## <a name="disaster-recovery-roadmap"></a>嚴重損壞復原藍圖
<a name="RDmap"> </a>

![SharePoint 嚴重損壞修復藍圖的視覺表示法。](images/Azure_DRroadmap.png)
  
此藍圖假設您已在生產環境中部署的 SharePoint Server 2013 伺服器陣列。
  
**表格： 藍圖嚴重損壞修復**

|**階段**|**描述**|
|:-----|:-----|
|階段 1  <br/> |設計嚴重損壞修復環境。  <br/> |
|階段 2  <br/> |建立 Azure 虛擬網路和 VPN 連線。  <br/> |
|階段 3  <br/> |Azure 虛擬網路中部署 Windows Active Directory 及網域名稱服務。  <br/> |
|階段 4  <br/> |部署在 Azure 中的 SharePoint 復原伺服器陣列。  <br/> |
|第 5 階段  <br/> |設定伺服器陣列之間的 DFSR。  <br/> |
|階段 6  <br/> |設定記錄傳送至修復伺服器陣列。  <br/> |
|第 7 階段  <br/> | 驗證容錯移轉和復原解決方案。這包括下列程序和技術： <br/>  停止記錄傳送。 <br/>  將備份還原。 <br/>  內容編目時間。 <br/>  復原服務。 <br/>  管理 DNS 記錄。 <br/> |
   
## <a name="phase-1-design-the-disaster-recovery-environment"></a>階段 1： 設計嚴重損壞修復環境
<a name="Phase1"> </a>

若要設計嚴重損壞修復環境，包括 SharePoint 復原伺服器陣列中使用[Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)中的指導。您可以使用[Azure 中的 SharePoint 災害復原解決方案](https://go.microsoft.com/fwlink/p/?LinkId=392554)Visio 檔案中的圖形開始設計程序。我們建議您在開始 Azure 環境中的任何工作之前設計整個環境。
  
除了[Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)設計虛擬網路、 VPN 連線、 Active Directory 及 SharePoint 伺服器陣列所提供的指導，請務必將檔案共用角色新增至 Azure 環境。
  
若要支援記錄傳送的嚴重損壞修復解決方案，檔案共用虛擬機器新增至所在的資料庫角色的子網路。檔案共用也做為 SQL Server AlwaysOn 可用性群組的節點多數 」 的第三個節點。這是建議使用 SQL Server AlwaysOn 可用性群組的標準 SharePoint 伺服器陣列的設定。 
  
> [!NOTE]
> 請務必檢閱資料庫以參與的 SQL Server AlwaysOn 可用性群組的必要條件。如需詳細資訊，請參閱[必要條件、 限制和 Recommendations for AlwaysOn Availability Groups](https://go.microsoft.com/fwlink/p/?LinkId=510870)。 
  
**圖： 位置的嚴重損壞復原解決方案所使用的檔案伺服器**

![顯示新增至含有 SharePoint 資料庫伺服器角色之相同雲端服務的檔案共用 VM。](images/AZenv_FSforDFSRandWSFC.png)
  
在此圖表、 檔案共用虛擬機器新增至包含資料庫伺服器角色的 Azure 中相同的子網路。請勿加檔案共用虛擬機器設定與其他伺服器角色，例如 SQL Server 角色的可用性。
  
如果您擔心記錄檔的高可用性，請考慮使用[SQL Server 備份與還原 Azure Blob Storage service](https://go.microsoft.com/fwlink/p/?LinkId=393113)考慮以不同的方法。這是記錄檔會直接儲存到 blob 存放區 URL 的 Azure 中的新功能。此解決方案不包括使用這項功能的相關指引。
  
當您設計的復原伺服器陣列時，請記住，成功損毀修復環境正確地反映實際執行伺服器陣列要復原。復原伺服器陣列的大小不是最重要的是在復原伺服器陣列的設計、 部署及測試。伺服器陣列規模而異從組織根據業務需求的組織。它可能會出現短暫的中斷或效能和容量需求需要擴充伺服器陣列之前使用劍橋伺服器陣列。
  
設定復原伺服器陣列至實際執行伺服器陣列盡可能同名使其符合您的服務層次協議 (SLA) 需求並提供您需要以支援您的業務的功能。當您設計嚴重損壞修復環境時，也查看您的變更管理程序的實際執行環境。我們建議您擴充至復原環境的變更管理程序來更新在相同的時間間隔的復原環境與實際執行環境。變更管理程序的一部分，建議您維護伺服器陣列設定、 應用程式和使用者的詳細的清查。 
  
## <a name="phase-2-create-the-azure-virtual-network-and-vpn-connection"></a>階段 2： 建立 Azure 虛擬網路和 VPN 連線
<a name="Phase2"> </a>

[Microsoft Azure 虛擬網路的連線與內部網路](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)教您如何規劃及部署在 Azure 虛擬網路以及如何建立 VPN 連線。請遵循，才可完成下列程序主題中的指引：
  
- 規劃虛擬網路的私人 IP 位址空間。
    
- 規劃虛擬網路的路由的基礎結構變更。
    
- 規劃內部部署 VPN 裝置的流量的防火牆規則。
    
- 在 Azure 中建立跨內部虛擬網路。
    
- 設定您的內部網路和虛擬網路間的路由。
    
## <a name="phase-3-deploy-active-directory-and-domain-name-services-to-the-azure-virtual-network"></a>階段 3： 部署 Active Directory 及網域名稱服務以 Azure 虛擬網路
<a name="Phase3"> </a>

此階段包括部署 Windows Server Active Directory 和 DNS 中混合式案例的虛擬網路和[Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)中所述，如下圖所示。
  
**圖： 混合式 Active Directory 網域組態**

![STwo 虛擬機器部署到 Azure 虛擬網路和 SharePoint 伺服器陣列子網路是複本網域控制站和 DNS 伺服器](images/AZarch_HyADdomainConfig.png)
  
在圖中，兩個虛擬機器部署至相同的子網路。這些虛擬機器時的每個主控的兩種角色： Active Directory 和 DNS。
  
部署在 Azure 中的 Active Directory 之前，先閱讀[部署 Windows Server Active directory Azure 虛擬機器上的指導方針](https://go.microsoft.com/fwlink/p/?linkid=392681)。這些指導方針可協助您決定您是否需要不同的架構或不同的組態設定的解決方案。
  
如需詳細指導設定 Azure 中的網域控制站的詳細資訊，請參閱[安裝複本 Active Directory 網域控制站在 Azure 虛擬網路](https://go.microsoft.com/fwlink/p/?LinkId=392687)。
  
此階段中之前, 沒有將虛擬機器部署至虛擬網路。虛擬機器架設 Active Directory 和 DNS 不可能是最大的虛擬機器所需的解決方案。您將這些虛擬機器的部署之前，請先建立想要使用虛擬網路的最大虛擬機器。這有助於確保您的解決方案落在可讓您需要的最大大小的 Azure 中的標籤。您不需要在此時間設定此虛擬機器。只需建立，而使用它。如果不這麼做，您可能會執行到當您嘗試更新版本、 建立較大的虛擬機器時的限制這在本文撰寫時的問題。 
  
## <a name="phase-4-deploy-the-sharepoint-recovery-farm-in-azure"></a>階段 4： 部署在 Azure 中的 SharePoint 復原伺服器陣列
<a name="Phase4"> </a>

部署 SharePoint 伺服器陣列的虛擬網路根據您的設計計劃。可能是部署在 Azure 中的 SharePoint 角色之前，先檢閱[Planning for SharePoint 2013 在 Azure 基礎結構服務上](https://go.microsoft.com/fwlink/p/?LinkId=400984)幫助。
  
請考慮下列我們所建置我們證明概念環境學到的作法：
  
- 使用 Azure 入口網站或 PowerShell 建立虛擬機器。
    
- Azure 和 HYPER-V 不支援動態記憶體。請確定此納入效能與容量計劃。
    
- 重新啟動虛擬機器透過 Azure 介面，不會從虛擬機器登入本身擷取。使用 Azure 介面更妥善地運作且更容易預測。
    
- 如果您想要關閉虛擬機器儲存成本，使用 Azure 介面。如果您關閉從虛擬機器登入、 費繼續累。
    
- 使用虛擬機器的命名慣例。
    
- 請的注意到哪一個資料中心位置部署虛擬機器。
    
- SharePoint 角色不支援在 Azure 中的自動縮放比例功能。
    
- 請勿將會還原，例如網站集合之伺服器陣列中設定的項目。 
    
## <a name="phase-5-set-up-dfsr-between-the-farms"></a>階段 5： 設定伺服器陣列之間 DFSR
<a name="Phase5"> </a>

若要使用 DFSR 設定檔複寫，使用 [DNS 管理] 嵌入式管理單元。不過，DFSR 安裝程式之前登入您的內部部署檔案伺服器和 Azure 檔案伺服器並啟用 Windows 中的服務。
  
從 [伺服器管理員儀表板中，完成下列步驟：
  
- 設定本機伺服器。
    
- 啟動 [**新增角色及功能精靈]**。
    
- 開啟 [**檔案與存放服務**] 節點。
    
- 選取 [ **DFS 命名空間**和**DFS 複寫**。
    
- 按 [**下一步**完成精靈指示的步驟。
    
下表提供 DFSR 參考文章與部落格文章的連結。
  
**表格： DFSR 的參考文章**

|**標題**|**描述**|
|:-----|:-----|
|[複寫](https://go.microsoft.com/fwlink/p/?LinkId=392732) <br/> |DFS 管理 TechNet 主題的連結複寫  <br/> |
|[DFS 複寫： 生存指南](https://go.microsoft.com/fwlink/p/?LinkId=392737) <br/> |使用 DFS 資訊的連結 wiki （英文)  <br/> |
|[DFS 複寫： 常見問題集](https://go.microsoft.com/fwlink/p/?LinkId=392738) <br/> |DFS 複寫 TechNet 主題  <br/> |
|[曼 Barreto 部落格](https://go.microsoft.com/fwlink/p/?LinkId=392739) <br/> |撰寫由主要程式總監 microsoft 檔案伺服器團隊部落格  <br/> |
|[在 Microsoft-檔案封包部落格儲存區小組](https://go.microsoft.com/fwlink/p/?LinkId=392740) <br/> |檔案服務和 Windows Server 中的儲存功能的相關部落格  <br/> |
   
## <a name="phase-6-set-up-log-shipping-to-the-recovery-farm"></a>階段 6： 設定記錄傳送至修復伺服器陣列
<a name="Phase6"> </a>

記錄傳送是設定此環境中的嚴重損壞修復的重要元件。您可以使用記錄傳送會自動將資料庫的交易記錄檔從主要資料庫伺服器執行個體傳送到次要資料庫伺服器執行個體。若要設定記錄傳送，請參閱 ＜[設定記錄在 SharePoint 2013 中傳送](http://technet.microsoft.com/library/482aeb81-e2aa-419f-a269-5b349a6c4721.aspx)。 
  
> [!IMPORTANT]
> 記錄傳送支援 SharePoint Server 中僅限於特定資料庫。如需詳細資訊，請參閱[支援的高可用性和嚴重損壞修復 SharePoint 資料庫 (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=393121)。 
  
## <a name="phase-7-validate-failover-and-recovery"></a>階段 7： 驗證容錯移轉及復原
<a name="Phase7"> </a>

此階段中最後的目標是驗證嚴重損壞復原解決方案運作如預期進行。若要這樣做，建立容錯移轉事件關閉實際執行伺服器陣列並啟動取代的復原伺服器陣列。您可以啟動容錯移轉案例以手動方式或使用指令碼。
  
第一個步驟是以停止傳入伺服器陣列服務或內容的使用者要求。停用 DNS 項目或關閉前端網頁伺服器您可以這麼做。在伺服器陣列已 「 關閉 」 之後，您可以容錯移轉的復原伺服器陣列。
  
### <a name="stop-log-shipping"></a>停止記錄傳送

您必須先停止在伺服器陣列復原之前的記錄傳送。停止記錄前，傳送 Azure 中的次要伺服器上，並再停止於主要伺服器內部。若要停止記錄傳送次要的第一部伺服器上，然後在主要伺服器上使用下列指令碼。指令碼中的資料庫名稱可能會不同，根據您的環境。
  
```
-- This script removes log shipping from the server.
-- Commands must be executed on the secondary server first and then on the primary server.

SET NOCOUNT ON
DECLARE  @PriDB nvarchar(max)
,@SecDB nvarchar(250)
,@PriSrv nvarchar(250)
,@SecSrv nvarchar(250)

Set @PriDB= ''
SET @PriDB = UPPER(@PriDB)
SET @PriDB = REPLACE(@PriDB, ' ', '')
SET @PriDB = '''' + REPLACE(@PriDB, ',', ''', ''') + ''''

Set @SecDB = @PriDB

Exec ( 'Select  ''exec master..sp_delete_log_shipping_secondary_database '' + '''''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_primary_secondary '' + '''''''' + prm.Primary_Database + '''''', '''''' + sec.Secondary_Server + '''''', '''''' + sec.Secondary_database + ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_primary_database '' + '''''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_secondary_primary '' + '''''''' + prm.primary_server + '''''', '''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

```

### <a name="restore-the-backups"></a>還原的備份

備份必須還原他們所建立的順序。您可以還原至特定的交易記錄檔備份之前，您必須先不含回復未認可的交易還原下列先前的備份 (也就使用`WITH NORECOVERY`)：
  
- 完整資料庫備份和上次的差異備份-如果有的話之前的特定交易記錄備份, 進行還原這些備份。建立最近的完整或差異資料庫備份之前，資料庫所使用的完整復原模式或大量記錄的復原模式。
    
- 所有交易記錄備份-都還原所需的完整資料庫備份或差異備份 （如果您都還原一個） 之後和之前的特定的交易記錄檔的備份所有交易記錄檔。記錄檔備份必須在其中建立時，不含任何間距記錄鏈結中順序套用。
    
若要使網站轉譯復原次要伺服器上的內容資料庫，移除在復原之前的所有資料庫連線。若要還原之資料庫，請執行下列 SQL 陳述式。
  
```
restore database WSS_Content with recovery

```

> [!IMPORTANT]
> 當您明確地使用 T-SQL 時，指定 [ **WITH NORECOVERY** ] 或 [ **WITH RECOVERY**以消除模稜兩可每個還原陳述式 — 這是非常重要撰寫指令碼時。還原完整及差異備份之後，可以在 SQL Server Management Studio 還原的交易記錄檔。此外，因為已經停止記錄傳送，內容資料庫是處於待命狀態，因此您必須將狀態變更為完整存取權。
  
在 SQL Server Management Studio 中，以滑鼠右鍵按一下 [ **WSS_Content** ] 資料庫、 指向 [**工作** > **還原**，然後按一下 [**交易記錄檔**（如果您不具有還原完整備份，這不是使用）。如需詳細資訊，請參閱[還原交易記錄備份 (SQL Server)](https://go.microsoft.com/fwlink/p/?LinkId=392778)。
  
### <a name="crawl-the-content-source"></a>編目的內容來源

您必須啟動還原搜尋服務的每個內容來源的完整編目。請注意您會失去從內部部署伺服器陣列，例如搜尋建議一些分析資訊。開始完整編目、 使用 Windows PowerShell cmdlet **Restore-spenterprisesearchserviceapplication**及指定的記錄傳送資料庫並複製搜尋管理資料庫之前**Search_Service__DB_<GUID>**。此指令程式提供搜尋組態、 結構描述、 managed 的屬性、 規則及來源，並建立一組預設其他元件。
  
若要啟動完整編目，請完成下列步驟：
  
1. 在 SharePoint 2013 管理中心，移至 [**應用程式管理** > **服務應用程式** > **管理服務應用程式**，然後按一下 [您要編目之搜尋服務應用程式。
    
2. 在 [**搜尋管理**] 頁面上，按一下 [**內容來源**]，指向您想，請按一下的箭頭，然後再按一下 [**啟動完整編目**的內容來源。
    
### <a name="recover-farm-services"></a>復原伺服器陣列服務
<a name="Reco"> </a>

下表顯示如何復原有記錄傳送資料庫、 服務資料庫但不建議還原與記錄傳送和不具有資料庫的服務的服務。
  
> [!IMPORTANT]
> 內部部署 SharePoint 資料庫還原至 Azure 環境會無法復原您沒有已安裝在 Azure 中手動任何 SharePoint 服務。 
  
**表格： 服務應用程式資料庫參考 （英文）**

|**記錄傳送資料庫還原這些服務**|**這些服務已在資料庫，但建議您在不含還原其資料庫啟動這些服務**|**這些服務不資料儲存在資料庫 ；容錯移轉後啟動這些服務**|
|:-----|:-----|:-----|
| 機器翻譯服務 <br/>  Managed Metadata Service <br/>  Secure Store Service <br/>  使用者設定檔。（僅限設定檔及社交標記資料庫的支援。同步處理資料庫不支援。） <br/>  Microsoft SharePoint Foundation 訂閱設定服務 <br/> | Usage and Health Data Collection <br/>  State Service <br/>  Word automation <br/> | Excel Services <br/>  PerformancePoint Services <br/>  PowerPoint 轉換 <br/>  Visio Graphics Service <br/>  Work Management <br/> |
   
下列範例會示範如何將資料庫還原的受管理的中繼資料服務。
  
使用現有的 Managed_Metadata_DB 資料庫。此資料庫會記錄傳送、 但有任何作用中 service 應用程式次要伺服器陣列，因此它需要後的服務應用程式中進行連線。
  
首先，使用`New-SPMetadataServiceApplication`，並指定`DatabaseName`切換還原資料庫的名稱。
  
下一步]，如下所示的次要伺服器上，設定新的受管理的中繼資料服務應用程式：
  
- 名稱： 受管理的中繼資料服務
    
- 資料庫伺服器： 從隨附的交易記錄檔的資料庫名稱
    
- 資料庫名稱： Managed_Metadata_DB
    
- 應用程式集區： SharePoint Service 應用程式 
    
### <a name="manage-dns-records"></a>管理 DNS 記錄
<a name="DNS"> </a>

您必須手動建立 DNS 記錄以指向 SharePoint 伺服器陣列。
  
在大多數情況下包含多部前端網頁伺服器，其合理利用 Windows Server 2012 或硬體負載平衡器分散要求在伺服器陣列中 web 前端伺服器之間的網路負載平衡功能。網路負載平衡也可以協助減少風險如果其中一部 web 前端伺服器失敗散佈到其他伺服器的要求。 
  
一般而言，當您設定好的網路負載平衡，您的叢集指派單一 IP 位址。您再建立 DNS 主機記錄中的 DNS 提供者為您指向叢集中的網路。（這個專案中，我們放入的 DNS 伺服器 Azure 中的 [恢復能力以防內部部署資料中心失敗。）例如，您可以在其中建立 DNS 記錄，在 DNS 管理員中 Active Directory 中，例如呼叫`http://sharepoint.contoso.com`、 指引您負載平衡叢集中的 IP 位址。
  
外部存取您的 SharePoint 伺服器陣列，您可以用戶端使用防火牆的外部 IP 位址會指向內部網路 (例如 http://sharepoint.contoso.com) 的相同 URL 的外部 DNS 伺服器上建立主機記錄。（最佳作法是使用此範例中，是設定分割 DNS，讓內部 DNS 伺服器會直接與 SharePoint 伺服器陣列叢集中的 contoso.com 和路由要求進行系統授權而不是外部 DNS 伺服器路由的 DNS 要求）。外部 IP 位址然後可以對應內部 IP 位址的內部部署叢集，讓用戶端找到他們所尋找的資源。
  
從這裡，您可能會執行到幾個不同的嚴重損壞修復案例：
  
 **範例案例： 內部部署 SharePoint 伺服器陣列是無法使用，因為在內部部署 SharePoint 伺服器陣列的硬體故障。**在此例中完成 Azure SharePoint 伺服器陣列的容錯移轉的步驟之後，您可以設定網路上的負載平衡復原 SharePoint 伺服器陣列的 web 前端伺服器，您並未與內部部署伺服器陣列的方式相同。然後可以將主機記錄重新導向內部 DNS 提供者以指向復原伺服器陣列的叢集 IP 位址。請注意，它可能需要一些時間快取的 DNS 記錄之前用戶端上會重新整理並指向 [復原伺服器陣列。
  
 **範例案例： 內部部署資料中心是完全遺失。**此案例中可能會由於天然災害時，例如消防或泛光 」。在此例中為 enterprise 中，您可能必須裝載於另一個區域，以及您有其專屬的目錄服務和 DNS 的 Azure 子網路的次要資料中心。如同前一個災害案例中，您可以重新導向內部和外部 DNS 記錄以指向 Azure SharePoint 伺服器陣列。同樣地，記下的 DNS 記錄傳播可能需要一些時間。
  
如果您的[主機命名型網站集合架構與部署 (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=393120)建議使用主機命名型網站集合，您可能必須在 SharePoint 伺服器陣列，以唯一相同的 web 應用程式所主控的數個網站集合DNS 名稱 （例如 http://sales.contoso.com 和 http://marketing.contoso.com）。在此例中，您可以建立指向您的叢集 IP 位址的 DNS 記錄每個網站集合。要求達到您的 SharePoint web 前端伺服器之後，他們處理每個要求路由到適當的網站集合。
  
## <a name="microsoft-proof-of-concept-environment"></a>Microsoft 概念證明環境
<a name="POC"> </a>

我們設計及測試此解決方案的概念證明環境。我們測試環境的設計目標是部署和復原我們可能會發現客戶環境中的 SharePoint 伺服器陣列。我們所做的數個假設，但我們知道伺服器陣列所需提供的所有不含任何自訂的方塊 （英文） 功能。拓撲的設計是高可用性使用從欄位和產品] 群組中的最佳作法指導。
  
下表說明我們建立及設定內部部署測試環境的 HYPER-V 虛擬機器。
  
**表格： 虛擬機器的內部部署測試**

|**伺服器名稱**|**角色**|**設定**|
|:-----|:-----|:-----|
|DC1  <br/> |使用 Active Directory 網域控制站。  <br/> |2 個處理器  <br/> 從 512 MB 透過 4 GB 的 RAM  <br/> 1 x 127 GB 硬碟  <br/> |
|RRAS  <br/> |設定與路由及遠端存取服務 (RRAS) 角色的伺服器。  <br/> |2 個處理器  <br/> 2-8 GB 的 RAM  <br/> 1 x 127 GB 硬碟  <br/> |
|FS1  <br/> |檔案伺服器與共用的備份和 DFSR 結束點。  <br/> |四個處理器  <br/> 2-12 GB 的 RAM  <br/> 1 x 127 GB 硬碟  <br/> 1 x 1 TB 硬碟 (SAN)  <br/> 1 x 750 GB 硬碟  <br/> |
|SP-WFE1，SP-WFE2  <br/> |前端網頁伺服器。  <br/> |四個處理器  <br/> 16 GB RAM  <br/> |
|SP-SP-APP2 APP1 SP APP3  <br/> |應用程式伺服器。  <br/> |四個處理器  <br/> 2-16 GB 的 RAM  <br/> |
|SP-SQL-HA1，SP-SQL-HA2  <br/> |設定 SQL Server 2012 AlwaysOn 可用性群組來提供高可用性的資料庫伺服器。這個設定使用 SP-sql-ha1 和 SP-SQL-HA2 做為主要和次要複本。  <br/> |四個處理器  <br/> 2-16 GB 的 RAM  <br/> |
   
下表說明我們建立及設定的前端網頁伺服器和應用程式伺服器的內部測試環境的 HYPER-V 虛擬機器的磁碟機設定。
  
**表格： Front End 網頁的虛擬機器的磁碟機需求與內部部署的應用程式伺服器測試**

|**磁碟機代號**|**大小**|**目錄名稱**|**路徑**|
|:-----|:-----|:-----|:-----|
|C  <br/> |80  <br/> |系統磁碟機  <br/> |<DriveLetter>：\\程式檔案\\Microsoft SQL Server\\  <br/> |
|E  <br/> |80  <br/> |記錄檔磁碟 (40 GB)  <br/> |<DriveLetter>：\\程式檔案\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\資料  <br/> |
|F  <br/> |80  <br/> |頁面 (36 GB)  <br/> |<DriveLetter>：\\程式檔案\\Microsoft SQL Server\\MSSQL\\資料  <br/> |
   
下表說明 HYPER-V 虛擬機器建立及設定以做為內部資料庫伺服器的磁碟機設定。在 [**資料庫引擎組態**] 頁面存取**資料目錄**] 索引標籤來設定並加以確認，如下表所示的設定。
  
**表格： 內部部署的資料庫伺服器的虛擬機器的磁碟機需求測試**

|**磁碟機代號**|**大小**|**目錄名稱**|**路徑**|
|:-----|:-----|:-----|:-----|
|C  <br/> |80  <br/> |資料根目錄  <br/> |<DriveLetter>：\\程式檔案\\Microsoft SQL Server\\  <br/> |
|E  <br/> |500 個  <br/> |使用者資料庫目錄  <br/> |<DriveLetter>：\\程式檔案\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\資料  <br/> |
|F  <br/> |500 個  <br/> |使用者資料庫記錄檔目錄  <br/> |<DriveLetter>：\\程式檔案\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\資料  <br/> |
|G  <br/> |500 個  <br/> |Temp DB 目錄  <br/> |<DriveLetter>：\\程式檔案\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\資料  <br/> |
|H  <br/> |500 個  <br/> |Temp DB 記錄檔目錄  <br/> |<DriveLetter>：\\程式檔案\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\資料  <br/> |
   
### <a name="setting-up-the-test-environment"></a>設定測試環境

不同的部署階段測試小組通常正常運作之第一個的內部部署架構，然後在相對應的 Azure 環境。這會反映已執行內部的實際執行伺服器陣列的一般真實世界案例。什麼是更重要的是您應知道目前實際作業工作量、 容量及一般效能。除了建立符合業務需求嚴重損壞復原模式，您應該大小復原伺服器陣列的伺服器來傳送服務的最低層級。冷或暖待命環境中，復原伺服器陣列是一般會小於實際執行伺服器陣列。之後復原伺服器陣列的穩定性及實際執行，伺服器陣列可以擴充向上及向外延展來滿足工作量需求。
  
我們部署了我們的測試環境中下列三個階段：
  
- 設定混合式基礎結構
    
- 佈建伺服器
    
- 部署 SharePoint 伺服器陣列
    
#### <a name="set-up-the-hybrid-infrastructure"></a>設定混合式基礎結構

此階段牽涉到內部部署伺服器陣列和 Azure 中的復原伺服器陣列在網域環境的設定。設定 Active Directory 相關聯的一般工作，以及測試小組會實作路由的方案和兩個環境之間的 VPN 連線。
  
#### <a name="provision-the-servers"></a>佈建伺服器

伺服器陣列的伺服器，以及遭到所需的網域控制站佈建伺服器並設定來處理 RRAS 為網站 VPN 伺服器。兩個檔案伺服器已佈建 DFSR 服務與數個用戶端電腦已佈建測試人員。
  
#### <a name="deploy-the-sharepoint-farms"></a>部署 SharePoint 伺服器陣列

SharePoint 伺服器陣列是為了簡化環境穩定和疑難排解、 帳戶部署在兩個階段中如有需要。在第一階段中，每個伺服器陣列已部署在各層的拓撲以支援所需的功能的伺服器數目最小值。
  
我們建立之前建立的 SharePoint 2013 伺服器安裝 SQL Server 資料庫伺服器。因為這是新部署時，我們會建立可用性群組才能部署 SharePoint。我們建立三個群組依據 ATL-MCS-001 最佳作法指導。 
  
> [!NOTE]
> 建立版面配置區的資料庫，讓您可以建立可用性群組安裝 SharePoint 之前。如需詳細資訊，請參閱 ＜[設定 SQL Server 2012 AlwaysOn 可用性群組的 SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=517626)
  
我們建立伺服器陣列，並依下列順序加入額外的伺服器：
  
- 佈建 SP-sql-ha1 和 SP-SQL-HA2。
    
- 設定 AlwaysOn 並建立伺服器陣列的三個可用性群組。 
    
- 佈建 SP-APP1 以主控管理中心。
    
- 佈建 SP WFE1 及 SP WFE2 主機分散式快取。 
    
我們使用_skipRegisterAsDistributedCachehost_參數在命令列執行**psconfig.exe**時。如需詳細資訊，請參閱[規劃摘要及 SharePoint Server 2013 中的分散式快取服務](https://go.microsoft.com/fwlink/p/?linkid=270985)。 
  
我們重複復原環境中的下列步驟：
  
- 佈建亞利桑那州-sql-ha1 和亞利桑那州-SQL-HA2。
    
- 設定 AlwaysOn 並建立伺服器陣列的三個可用性群組。
    
- 佈建亞利桑那州-APP1 以主控管理中心。
    
- 佈建亞利桑那州 WFE1 及亞利桑那州 WFE2 主機分散式快取。
    
我們設定分散式快取及新增的測試使用者和測試內容後，我們會啟動之部署的兩個階段。此支援所需向外延展層和設定伺服器陣列的伺服器陣列架構中所述的高可用性拓撲。
  
下表說明虛擬機器、 子網路及我們設定復原伺服器陣列的可用性設定。
  
**表格： 復原伺服器陣列基礎結構**

|**伺服器名稱**|**角色**|**設定**|**子網路**|**可用性設定**|
|:-----|:-----|:-----|:-----|:-----|
|spDRAD  <br/> |使用 Active Directory 網域控制站  <br/> |2 個處理器  <br/> 從 512 MB 透過 4 GB 的 RAM  <br/> 1 x 127 GB 硬碟  <br/> |sp ADservers  <br/> ||
|亞利桑那州-SP-FS  <br/> |檔案伺服器與共用的備份和 DFSR 的端點  <br/> | A5 組態： <br/>  2 個處理器 <br/>  14 GB 的 RAM <br/>  1 x 127 GB 硬碟 <br/>  1 x 135 GB 硬碟 <br/>  1 x 127 GB 硬碟 <br/>  1 x 150 GB 硬碟 <br/> |sp databaseservers  <br/> |DATA_SET  <br/> |
|亞利桑那州 WFE1、 亞利桑那州-WFE2  <br/> |Front End 網頁伺服器  <br/> | A5 組態： <br/>  2 個處理器 <br/>  14 GB 的 RAM <br/>  1 x 127 GB 硬碟 <br/> |sp webservers  <br/> |WFE_SET  <br/> |
|亞利桑那州-APP1、 亞利桑那州-APP2、 亞利桑那州-APP3  <br/> |應用程式伺服器  <br/> | A5 組態： <br/>  2 個處理器 <br/>  14 GB 的 RAM <br/>  1 x 127 GB 硬碟 <br/> |sp applicationservers  <br/> |APP_SET  <br/> |
|亞利桑那州-SQL-HA1、 亞利桑那州-SQL HA2  <br/> |資料庫伺服器和 AlwaysOn 可用性群組的主要和次要複本  <br/> | A5 組態： <br/>  2 個處理器 <br/>  14 GB 的 RAM <br/> |sp databaseservers  <br/> |DATA_SET  <br/> |
   
### <a name="operations"></a>Operations

這些測試小組穩定的伺服器陣列環境並完成功能測試之後，啟動下列作業設定在內部復原環境所需的工作：
  
- 設定完整及差異備份。
    
- 在內部部署環境及 Azure 環境之間傳送交易記錄檔的檔案伺服器上設定 DFSR。
    
- 設定記錄傳送的主要資料庫伺服器上。
    
- 穩定、 驗證及疑難排解所需的記錄傳送。這包含用來識別並記錄任何可能造成問題，例如網路延遲造成記錄傳送或 DFSR 檔案同步處理失敗的行為。
    
### <a name="databases"></a>資料庫

容錯移轉測試涉及下列資料庫： 
  
- WSS_Content
    
- ManagedMetadata
    
- 設定檔資料庫
    
- 同步處理資料庫
    
- 社交資料庫
    
- 內容類型中樞 （專用的內容類型整合中樞的資料庫）
    
## <a name="troubleshooting-tips"></a>疑難排解提示
<a name="Troubleshooting"> </a>

本節說明我們我們測試和其解決方案過程中遇到的問題。 
  
### <a name="using-the-term-store-management-tool-caused-the-error-the-managed-metadata-store-or-connection-is-currently-not-available"></a>使用字詞庫管理工具會導致錯誤發生、 」 的受管理的中繼資料存放區或連線目前無法使用。 」

確定 web 應用程式所使用的應用程式集區帳戶具有字詞儲存區權限的讀取權限。
  
### <a name="custom-term-sets-are-not-available-in-the-site-collection"></a>自訂的字詞組中沒有提供網站集合

檢查您的內容的網站集合與內容類型中樞之間遺失服務應用程式關聯。此外下,**受管理的中繼資料-<site collection name>連線**屬性螢幕，確定已啟用此選項：**此服務應用程式是欄特定字詞組的預設儲存位置。**
  
### <a name="the-get-adforest-windows-powershell-command-generates-the-error-the-term-get-adforest-is-not-recognized-as-the-name-of-a-cmdlet-function-script-file-or-operable-program"></a>取得 ADForest Windows PowerShell 命令將會產生錯誤、"字詞 ' Get-ADForest' 不會被視為指令程式、 函數、 指令碼檔案或可執行的程式的名稱"。

設定經過使用者設定檔時，您需要 Active Directory 樹系名稱。在 [新增角色及功能精靈]，請確認您是否已啟用 Active Directory 的 Windows PowerShell 模組 (底下**遠端伺服器管理工具] > 角色系統管理工具] > AD DS 與 AD LDS 工具**] 區段中)。此外，執行下列命令，然後再使用**Get ADForest**以協助確保您會載入相依性的軟體。
  
```
Import-module servermanager
Import-module activedirectory

```

### <a name="availability-group-creation-fails-at-starting-the-alwaysonhealth-xevent-session-on-server-name"></a>在啟動上的 'AlwaysOn_health' XEvent 工作階段失敗的可用性群組建立 '<server name>'

確保這兩個節點的容錯移轉叢集狀態"最多"並不"Paused"或"已停止 」。 
  
### <a name="sql-server-log-shipping-job-fails-with-access-denied-error-trying-to-connect-to-the-file-share"></a>SQL Server 記錄傳送工作失敗，拒絕存取錯誤嘗試連線的檔案共用

確定您的 SQL Server Agent 正在執行網路認證，而不是預設的認證。
  
### <a name="sql-server-log-shipping-job-indicates-success-but-no-files-are-copied"></a>SQL Server 記錄傳送工作表示成功，但沒有檔案複製

這是因為可用性群組的預設備份喜好設定為**次要偏好**。請確定您從可用性群組，而不是主要; 的次要伺服器執行記錄傳送工作否則，工作會以無訊息方式失敗。 
  
### <a name="managed-metadata-service-or-other-sharepoint-service-fails-to-start-automatically-after-installation"></a>若要安裝後自動啟動失敗的受管理的中繼資料服務 （或其他 SharePoint service）

服務可能需要數分鐘才能啟動，請根據的效能和目前的 SharePoint Server 的負載。手動服務中按一下 [**開始]** ，並提供適當時間啟動時有時會重新整理 [伺服器] 畫面上的服務監視其狀態。此服務會維持已停止，以免讓 SharePoint 診斷記錄、 嘗試重新啟動服務，然後檢查錯誤的記錄檔。如需詳細資訊，請參閱 ＜[Configure diagnostic logging in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=510884)
  
### <a name="after-changing-dns-to-the-azure-failover-environment-client-browsers-continue-to-use-the-old-ip-address-for-the-sharepoint-site"></a>變更 DNS Azure 容錯移轉環境之後的, 用戶端瀏覽器繼續使用舊的 IP 位址的 SharePoint 網站

您的 DNS 變更可能不是所有用戶端可以看到立即。在測試用戶端上從提升權限的命令提示字元執行下列命令並嘗試再次存取網站。
  
```
Ipconfig /flushdns
```

## <a name="additional-resources"></a>其他資源
<a name="Troubleshooting"> </a>

[高可用性和嚴重損壞修復資料庫支援的 SharePoint (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=393121)
  
[設定 SQL Server 2012 AlwaysOn 可用性群組的 SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=393122)
  
## <a name="see-also"></a>請參閱

<a name="Troubleshooting"> </a>

[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)



