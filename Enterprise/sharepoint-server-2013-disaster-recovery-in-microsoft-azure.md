---
title: Microsoft Azure 中的 SharePoint Server 2013 災害復原
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 04/17/2018
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Deployment
ms.assetid: e9d14cb2-ff28-4a18-a444-cebf891880ea
description: 摘要： 使用 Azure，您可以建立的災害復原環境的內部部署 SharePoint 伺服器陣列。 本文說明如何設計和實作本解決方案。
ms.openlocfilehash: a302f86e97cd7b61236a92f51a043258882991f7
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070439"
---
# <a name="sharepoint-server-2013-disaster-recovery-in-microsoft-azure"></a>Microsoft Azure 中的 SharePoint Server 2013 災害復原

 **摘要：** 使用 Azure，您可以建立的災害復原環境的內部部署 SharePoint 伺服器陣列。 本文說明如何設計和實作本解決方案。

 **觀賞 SharePoint Server 2013 災害復原概觀影片**
> [!VIDEO https://www.microsoft.com/videoplayer/embed/1b73ec8f-29bd-44eb-aa3a-f7932784bfd9?autoplay=false]
  
 當發生災害事件 SharePoint 內部部署環境時，您的首要是為了讓執行一次迅速系統。 與 SharePoint 嚴重損壞修復時更快且更容易必須已在 Microsoft Azure 中執行的備份環境。 這段影片說明 SharePoint 暖容錯移轉環境的主要概念，並輔助本文中提供的完整詳細資料。
  
下列方案模型搭配使用這篇文章：**在 Microsoft Azure 中的 SharePoint 嚴重損壞修復**。
  
[![SharePoint 到 Azure 的災害復原程序](media/SP-DR-Azure.png)](https://go.microsoft.com/fwlink/p/?LinkId=392555)
  
 [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555) |  [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)
  
本文內容：
  
- [使用 Azure 基礎結構服務的嚴重損壞修復](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#AZ)
    
- [解決方案說明](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#SOL)
    
- [詳細架構](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#arch)
    
- [嚴重損壞修復藍圖](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#RDmap)
    
- [階段 1： 設計災害復原環境](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase1)
    
- [階段 2： 建立 Azure 虛擬網路和 VPN 連線](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase2)
    
- [階段 3： 將 Active Directory 和網域名稱服務部署到 Azure 虛擬網路](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase3)
    
- [階段 4： 部署在 Azure 中的 SharePoint 復原伺服器陣列](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase4)
    
- [階段 5： 設定伺服器陣列之間 DFSR](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase5)
    
- [階段 6： 設定記錄傳送至復原伺服器陣列](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase6)
    
- [階段 7： 驗證容錯移轉和復原](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase7)
    
- [Microsoft 概念證明的環境](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#POC)
    
- [疑難排解提示](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Troubleshooting)
    
## <a name="use-azure-infrastructure-services-for-disaster-recovery"></a>使用 Azure 基礎結構服務的嚴重損壞修復

許多組織不需要在災害復原環境 for SharePoint，可以是昂貴來建置及維護內部部署。 Azure 基礎結構服務提供完美選項災害復原環境，且更有彈性的內部部署替代方式成本低於。
  
使用 Azure 基礎結構服務的優點包括：
  
- **較少的高成本資源**維護及支付資源少於內部災害復原環境。 資源數目取決於哪些嚴重損壞修復環境在您選擇： 冷待命、 暖待命或熱待命。
    
- **更好的資源彈性**發生災害時，輕易地向外擴充復原 SharePoint 伺服器陣列以符合負載需求。 當您不再需要資源中比例調整。
    
- **較低的資料中心承諾**使用 Azure 基礎結構服務，而非投資位於不同地區的次要資料中心內。
    
有較不複雜組織只快速入門災害復原選項和進階選項具有高可靠度需求的組織。 在雲端平台上主控環境時，有點不同冷、 暖，及熱待命環境的定義。 下表說明這些環境建置在 Azure 中的 SharePoint 復原伺服器陣列。
  
**表格： 復原環境**

|**復原環境的類型**|**描述**|
|:-----|:-----|
|熱  <br/> |完全調整大小的伺服器陣列已佈建、 更新，並執行處於待命狀態。  <br/> |
|暖  <br/> |內建在伺服器陣列和虛擬機器執行及更新。  <br/> 復原作業包含附加內容資料庫、 佈建服務應用程式，以及編目的內容。  <br/> 在伺服器陣列可以是實際執行伺服器陣列較小版本，且再向外延展到完整的使用者提供服務。  <br/> |
|冷  <br/> |完全建置在伺服器陣列，但會停止虛擬機器。  <br/> 維護環境包含隨時啟動虛擬機器、 修補程式、 更新及驗證環境。  <br/> 啟動完整的環境發生嚴重損壞。  <br/> |
   
請務必評估貴組織的復原時間目標 (Rto) 和復原點目標 (Rpo)。 這些需求，決定哪些環境是最適合貴組織的投資。
  
本文中的指引說明如何實作暖待命環境。 您可以也適應它冷待命環境中，雖然您必須遵循額外的程序，以支援這類環境。 本文不會說明如何實作熱待命環境。
  
如需災害復原解決方案的詳細資訊，請參閱[高可用性和 SharePoint 2013 的災害復原概念](https://go.microsoft.com/fwlink/p/?LinkID=393114)和[選擇 SharePoint 2013 的災害復原策略](https://go.microsoft.com/fwlink/p/?linkid=203228)。
  
## <a name="solution-description"></a>解決方案說明

暖待命災害復原解決方案需要下列環境：
  
- 內部部署 SharePoint 實際執行伺服器陣列
    
- 在 Azure 中復原 SharePoint 伺服器陣列
    
- 兩個環境之間的站台對站 VPN 連線
    
下圖說明這三個元素。
  
**圖： 在 Azure 中暖待命解決方案的項目**

![Azure 中 SharePoint 暖待命解決方案的元素](media/AZarch-AZWarmStndby.png)
  
SQL Server 記錄傳送與分散式檔案系統複寫 (DFSR) 用於將資料庫備份和交易記錄檔複製到在 Azure 中的復原伺服器陣列： 
  
- DFSR 會將記錄從實際執行環境傳送至復原環境。 在 WAN 案例中，DFSR 比直接將記錄傳送至 Azure 中的次要伺服器更為有效率。
    
- 記錄檔會重新顯示到 Azure 中在復原環境中的 SQL Server。
    
- 除非執行復原練習，否則，您不附加記錄傳送 SharePoint 內容資料庫在復原環境中。
    
執行下列步驟，以復原伺服器陣列：
  
1. 停止記錄傳送。
    
2. 停止接受主要伺服器陣列的流量。
    
3. 重新顯示的最後一筆交易記錄檔。
    
4. 將內容資料庫附加至伺服器陣列。
    
5. 複寫的服務資料庫還原服務應用程式。
    
6. 更新以指到復原伺服器陣列的網域名稱系統 (DNS) 記錄。
    
7. 開始完整編目。
    
我們建議您定期排練這些步驟，並記錄以協助確保您 live 復原順暢執行。 附加內容資料庫並還原服務應用程式可能需要一些時間，而且通常牽涉到某些手動設定。
  
執行復原之後，此解決方案會提供下列表格所列出的項目。
  
**表格： 方案復原目標**

|**項目**|**描述**|
|:-----|:-----|
|網站和內容  <br/> |網站和內容可在復原環境中。  <br/> |
|搜尋的新執行個體  <br/> |在此暖待命解決方案，不會從搜尋資料庫還原搜尋。 復原伺服器陣列中的搜尋元件設定為 [同樣地，儘可能在實際執行伺服器陣列。 還原網站與內容後，啟動完整編目時將搜尋索引重建。 您不需要等待完成要提供的網站和內容編目。  <br/> |
|服務  <br/> | 從記錄傳送的資料庫還原資料儲存在資料庫的服務。 只要啟動服務，請勿在資料庫中儲存的資料。 <br/>  並非所有的服務與資料庫需要進行還原。 下列服務不需要還原的資料庫，且只可以啟動容錯移轉後： <br/>  Usage and Health Data Collection <br/>  State service <br/>  Word automation <br/>  不使用資料庫的任何其他服務 <br/> |
   
您可以使用 Microsoft 諮詢服務 (MCS) 或協力廠商地址較複雜復原目標。 下表摘要說明。
  
**表格： 其他項目可以 MCS 或協力廠商所提到**

|**項目**|**描述**|
|:-----|:-----|
|同步處理自訂伺服器陣列解決方案  <br/> |理想狀況下，復原伺服器陣列設定為相同的實際執行伺服器陣列。 您可以使用顧問或協力廠商評估自訂伺服器陣列解決方案會複寫以及是否程序已經保持同步處理兩個環境準備就緒。  <br/> |
|連線至資料來源內部部署  <br/> |它可能不是實際複寫至後端資料系統，例如備份網域控制站 (BDC) 連線及搜尋內容來源的連線。  <br/> |
|搜尋還原案例  <br/> |企業搜尋部署通常是相當唯一且複雜，因為從資料庫還原搜尋需要更多投資。 您可以使用顧問或協力廠商，以找出並實作您的組織可能需要的搜尋還原案例。  <br/> |
   
本文中提供的指導假設在內部部署伺服器陣列已設計及部署。
  
## <a name="detailed-architecture"></a>詳細架構

理想狀況下，在 Azure 中的復原伺服器陣列設定為相同的實際執行伺服器陣列上部署，包括下列：
  
- 伺服器角色之相同的表示法
    
- 自訂項目的相同的設定
    
- 搜尋元件的相同的設定
    
在 Azure 中的環境可以是實際執行伺服器陣列較小版本。 如果您打算向外擴充的復原伺服器陣列容錯移轉之後，請務必最初以表示每一種伺服器角色。
  
某些組態中可能不是實際容錯移轉環境中複寫。 請務必測試環境，以協助確保容錯移轉伺服器陣列提供預期的服務層級與容錯移轉程序。
  
此方案，不會擬定 SharePoint 伺服器陣列的特定拓撲。 此解決方案的重點是 Azure 用於容錯移轉伺服器陣列，並實作在兩個環境之間的記錄傳送和 DFSR。
  
### <a name="warm-standby-environments"></a>暖待命環境

在暖待命環境中，執行的 Azure 環境中的所有虛擬機器。 環境可供容錯移轉執行或事件。
  
下圖說明從內部部署 SharePoint 伺服器陣列已設定為暖待命環境，以 Azure 為基礎的 SharePoint 伺服器陣列的災害復原解決方案。
  
**圖： 拓撲和重要元素的實際執行伺服器陣列和暖待命復原伺服器陣列**

![SharePoint 伺服器陣列和暖待命復原伺服器陣列的拓撲](media/AZarch-AZWarmStndby.png)
  
在此圖表中：
  
- 並排說明兩個環境： 內部部署 SharePoint 伺服器陣列以及 Azure 中的暖待命伺服器陣列。
    
- 每個環境都包括檔案共用。
    
- 每個伺服器陣列包含四個層級。 若要達到高可用性，每一層包含兩個伺服器或特定角色，例如前端服務、 分散式快取、 後端服務，以及資料庫的設定都相同的虛擬機器。 它不重要對外特定元件呼叫此圖例中。 兩個伺服器陣列的設定都相同。
    
- 第四個層是資料庫層。 記錄傳送用來將記錄從內部部署環境中的次要資料庫伺服器複製到相同的環境中的檔案共用。
    
- DFSR 會將檔案從內部部署環境中的檔案共用複製至 Azure 環境中的檔案共用。
    
- 記錄傳送會將記錄從 Azure 環境中的檔案共用重新執行至復原環境的 SQL Server AlwaysOn 可用性群組中的主要複本。
    
### <a name="cold-standby-environments"></a>冷待命環境

在冷待命環境中，大部分的 SharePoint 伺服器陣列虛擬機器可以關閉。 （建議有時會啟動虛擬機器，例如每兩週或月，一次，讓每個虛擬機器可以與網域同步處理）。在 Azure 復原環境中的下列虛擬機器必須保持執行以協助確保記錄傳送及 DFSR 連續作業：
  
- 檔案共用
    
- 主要資料庫伺服器
    
- 執行 Windows Server Active Directory 網域服務和 DNS 的至少一部虛擬機器
    
下圖顯示 Azure 容錯移轉環境中執行檔案共用虛擬機器和主要的 SharePoint 資料庫虛擬機器。 所有其他 SharePoint 虛擬機器會停止。 正在執行 Windows Server Active Directory 和 DNS 虛擬機器時不會顯示。
  
**圖： 冷待命復原伺服器陣列與執行虛擬機器**

![Azure 中 SharePoint 冷待命解決方案的元素](media/AZarch-AZColdStndby.png)
  
容錯移轉之後以冷待命環境，並啟動所有虛擬機器，和方法來達到高可用性的資料庫伺服器必須設定，例如 SQL Server AlwaysOn 可用性群組。
  
如果已實作多個儲存群組 （資料庫分散於多個 SQL Server 高可用性設定組），每個儲存群組的主要資料庫都必須執行接受其儲存群組相關聯的記錄檔。
  
### <a name="skills-and-experience"></a>技能與經驗

在這個災害復原解決方案可用多重技術。 為了協助確保這些技術互動如預期般，必須安裝並正確設定內部部署和 Azure 環境中的每個元件。 建議的人員或團隊會設定此解決方案，使用下列文章所述的技術也有的強式工作知識與實機操作技能：
  
- [分散式的檔案系統 (DFS) 複寫服務](https://go.microsoft.com/fwlink/p/?LinkId=392698)
    
- [Windows Server 容錯移轉叢集 (WSFC) 和 SQL Server](https://go.microsoft.com/fwlink/p/?LinkId=392701)
    
- [AlwaysOn 可用性群組 (SQL Server)](https://go.microsoft.com/fwlink/p/?LinkId=392725)
    
- [備份及還原的 SQL Server 資料庫](https://go.microsoft.com/fwlink/p/?LinkId=392728)
    
- [SharePoint Server 2013 安裝和伺服器陣列部署](https://go.microsoft.com/fwlink/p/?LinkId=393119)
    
- [Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=392729)
    
最後，我們建議指令碼，您可以使用這些技術相關聯的工作自動化的技術。 就可以使用可用的使用者介面來完成此解決方案所述的所有工作。 不過，手動的方式可耗用的時間和出錯，並將傳遞不一致的結果。
  
除了 Windows PowerShell 中，也有 SQL Server、 SharePoint Server 中，和 Azure 的 Windows PowerShell 文件庫。 別忘了 T-SQL，這也有助於減少來設定和維護您的災害復原環境的時間。
  
## <a name="disaster-recovery-roadmap"></a>嚴重損壞修復藍圖

![SharePoint 嚴重損壞修復藍圖的視覺表示法。](media/Azure-DRroadmap.png)
  
此藍圖假設您已部署在生產環境中的 SharePoint Server 2013 伺服器陣列。
  
<b0>表格: < Roadmap for 嚴重損壞修復</b0>

|**階段**|**描述**|
|:-----|:-----|
|階段 1  <br/> |設計災害復原環境。  <br/> |
|階段 2  <br/> |建立 Azure 虛擬網路和 VPN 連線。  <br/> |
|階段 3  <br/> |將 Windows Active Directory 和網域名稱服務部署到 Azure 虛擬網路。  <br/> |
|階段 4  <br/> |部署在 Azure 中的 SharePoint 復原伺服器陣列。  <br/> |
|階段 5  <br/> |設定伺服器陣列之間的 DFSR。  <br/> |
|階段 6  <br/> |設定記錄傳送至復原伺服器陣列。  <br/> |
|第 7 階段  <br/> | 驗證容錯移轉和復原解決方案。 這包括下列程序和技術： <br/>  停止記錄傳送。 <br/>  還原的備份。 <br/>  編目內容。 <br/>  復原服務。 <br/>  管理 DNS 記錄。 <br/> |
   
## <a name="phase-1-design-the-disaster-recovery-environment"></a>階段 1： 設計災害復原環境

使用[Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)中的指導方針，來設計嚴重損壞修復環境，包括 SharePoint 復原伺服器陣列。 您可以使用[Azure 中的 SharePoint 災害復原解決方案](https://go.microsoft.com/fwlink/p/?LinkId=392554)Visio 檔案中的圖形，開始設計程序。 我們建議您設計整個環境再開始 Azure 環境中的任何工作。
  
除了設計虛擬網路、 VPN 連線、 Active Directory，以及 SharePoint 伺服器陣列的[Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)中提供的指導，請務必將檔案共用角色新增至 Azure 環境。
  
若要支援災害復原解決方案中的記錄傳送，檔案共用虛擬機器新增至資料庫角色的所在位置的子網路。 檔案共用也可以做為 SQL Server AlwaysOn 可用性群組節點多數 」 的第三個節點。 這是使用 SQL Server AlwaysOn 可用性群組的標準 SharePoint 伺服器陣列的建議的組態。 
  
> [!NOTE]
> 請務必檢閱資料庫以參與的 SQL Server AlwaysOn 可用性群組的必要條件。 如需詳細資訊，請參閱[必要條件、 限制和建議 AlwaysOn 可用性群組](https://go.microsoft.com/fwlink/p/?LinkId=510870)。 
  
**圖： 用於災害復原解決方案的檔案伺服器的位置**

![顯示新增至含有 SharePoint 資料庫伺服器角色之相同雲端服務的檔案共用 VM。](media/AZenv-FSforDFSRandWSFC.png)
  
在此圖表中，在檔案共用虛擬機器新增至相同的子網路，在 Azure 中含有資料庫伺服器角色。 不要將檔案共用虛擬機器加入的可用性設定組與其他伺服器角色，例如 SQL Server 角色。
  
如果您擔心記錄檔的高可用性，請考慮使用[SQL Server 備份及還原與 Azure Blob 儲存體服務](https://go.microsoft.com/fwlink/p/?LinkId=393113)採取不同的方法。 這是記錄直接儲存到 blob 存放區 URL 的 Azure 中的新功能。 此解決方案不包括使用這項功能的相關指引。
  
當您設計的復原伺服器陣列時，請記住，成功的災害復原環境才會正確反映實際執行伺服器陣列，您想要復原。 復原伺服器陣列的大小不是最重要的是在復原伺服器陣列設計、 部署及測試。 伺服器陣列規模而異從組織中，根據商務需求的組織。 它可能會出現短暫的中斷，或直到效能和容量需求需要擴充伺服器陣列使用縮小的伺服器陣列。
  
至實際執行伺服器陣列儘可能具有相同設定復原伺服器陣列，使其符合您的服務等級協定 (SLA) 需求，並提供您需要支援貴公司的功能。 當您設計損毀修復環境時，也請查看變更管理處理程序，為您的實際執行環境。 我們建議您延伸至復原環境的變更管理程序來更新在復原環境的同一個的間隔為實際執行環境。 變更管理程序的一部分，建議您維護詳細的清查您的伺服器陣列設定、 應用程式和使用者。 
  
## <a name="phase-2-create-the-azure-virtual-network-and-vpn-connection"></a>階段 2： 建立 Azure 虛擬網路和 VPN 連線

[Microsoft Azure 虛擬網路的連線內部部署網路](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)說明如何規劃及部署 Azure 虛擬網路，以及如何建立的 VPN 連線。 請依照下列完成下列程序主題中的指引：
  
- 規劃虛擬網路的私人 IP 位址空間。
    
- 規劃虛擬網路的路由基礎結構的變更。
    
- 規劃將與從內部部署 VPN 裝置的流量的防火牆規則。
    
- 在 Azure 中建立跨單位部署虛擬網路。
    
- 設定內部網路和虛擬網路間的路由。
    
## <a name="phase-3-deploy-active-directory-and-domain-name-services-to-the-azure-virtual-network"></a>階段 3： 將 Active Directory 和網域名稱服務部署到 Azure 虛擬網路

此階段包含 Windows Server Active Directory 和 DNS 部署虛擬網路中的混合式案例，並在[Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)中所述，如下圖所示。
  
**圖： 混合式 Active Directory 網域組態**

![STwo 虛擬機器部署到 Azure 虛擬網路和 SharePoint 伺服器陣列子網路是複本網域控制站和 DNS 伺服器](media/AZarch-HyADdomainConfig.png)
  
在圖中，兩部虛擬機器部署至相同的子網路。 這些虛擬機器是每部主控的兩個角色： Active Directory 和 DNS。
  
之前部署在 Azure 中的 Active Directory，請參閱[部署 Windows Server Active Directory Azure 虛擬機器上的指導方針](https://go.microsoft.com/fwlink/p/?linkid=392681)。 這些指導方針可協助您判斷您是否需要不同的架構或不同的組態設定您的解決方案。
  
在 Azure 中的網域控制站設定的詳細指引，請參閱[安裝複本 Active Directory 網域控制站的 Azure 虛擬網路](https://go.microsoft.com/fwlink/p/?LinkId=392687)。
  
在這個階段中之前, 您未部署虛擬機器至虛擬網路。 虛擬機器來架設 Active Directory 和 DNS 不可能最大的虛擬機器，您需要的解決方案。 部署這些虛擬機器之前，先建立想要使用您的虛擬網路中的最大虛擬機器。 這有助於確保您的解決方案落在可讓您需要的最大的 Azure 中的標記。 您不需要這一次設定此虛擬機器。 只需建立，並將它放在一旁設定。 如果不這麼做，您可能會遇到當您嘗試更新版本中，建立較大的虛擬機器時的限制這是此問題： 在撰寫本文時的時間。 
  
## <a name="phase-4-deploy-the-sharepoint-recovery-farm-in-azure"></a>階段 4： 部署在 Azure 中的 SharePoint 復原伺服器陣列

部署您根據設計計劃的虛擬網路中的 SharePoint 伺服器陣列。 它可能會有幫助您部署在 Azure 中 SharePoint 角色之前，先檢閱[Planning for SharePoint 2013 在 Azure 基礎結構服務上](https://go.microsoft.com/fwlink/p/?LinkId=400984)。
  
請考慮下列我們學會建置我們概念證明環境的作法：
  
- 使用 Azure 入口網站或 PowerShell 建立虛擬機器。
    
- Azure 和 HYPER-V 不支援動態記憶體。 請確定這作為因素納入您的效能與容量計劃。
    
- 重新啟動虛擬機器，透過 Azure 介面，而不是由本身的虛擬機器登入。 使用 Azure 介面更妥善地運作，則較容易預測。
    
- 如果您想要關閉虛擬機器儲存成本，使用 Azure 的介面。 如果您從關閉虛擬機器登入，費用繼續累算。
    
- 使用虛擬機器的命名慣例。
    
- 請的注意到哪一個資料中心位置部署虛擬機器。
    
- SharePoint 角色不支援在 Azure 中的自動調整功能。
    
- 不會還原，例如網站集合之伺服器陣列中設定的項目。 
    
## <a name="phase-5-set-up-dfsr-between-the-farms"></a>階段 5： 設定伺服器陣列之間 DFSR

若要設定檔複寫使用 DFSR，使用 [DNS 管理] 嵌入式管理單元。 不過，DFSR 安裝程式之前登入您的內部部署檔案伺服器和 Azure 檔案伺服器並啟用 Windows 中的服務。
  
從 [伺服器管理員儀表板中，完成下列步驟：
  
- 設定本機伺服器。
    
- 啟動 [**新增角色及功能精靈**]。
    
- 開啟 [**檔案和存放服務**] 節點。
    
- 選取 [ **DFS 命名空間**和**DFS 複寫**。
    
- 按 [**下一步**完成精靈的步驟。
    
下表提供 DFSR 參考文章和部落格文章的連結。
  
**表格： DFSR 的參考文章**

|**標題**|**描述**|
|:-----|:-----|
|[複寫](https://go.microsoft.com/fwlink/p/?LinkId=392732) <br/> |DFS 管理 TechNet 主題的連結進行複寫  <br/> |
|[DFS 複寫： 生存指南](https://go.microsoft.com/fwlink/p/?LinkId=392737) <br/> |Wiki DFS 資訊的連結  <br/> |
|[DFS 複寫： 常見問題集](https://go.microsoft.com/fwlink/p/?LinkId=392738) <br/> |DFS 複寫 TechNet 主題  <br/> |
|[Jose Barreto 部落格](https://go.microsoft.com/fwlink/p/?LinkId=392739) <br/> |寫入由主體 Program Manager microsoft 在檔案伺服器小組部落格  <br/> |
|[在 Microsoft-檔案封包部落格儲存小組](https://go.microsoft.com/fwlink/p/?LinkId=392740) <br/> |檔案服務和 Windows Server 中的儲存空間功能相關的部落格  <br/> |
   
## <a name="phase-6-set-up-log-shipping-to-the-recovery-farm"></a>階段 6： 設定記錄傳送至復原伺服器陣列

記錄傳送是設定在此環境中的嚴重損壞修復的重要元件。 您可以使用記錄傳送至自動從主要資料庫伺服器執行個體的資料庫交易記錄檔傳送至次要資料庫伺服器執行個體。 若要設定記錄傳送，請參閱 <<c0>在 SharePoint 2013 中傳送設定記錄檔。 
  
> [!IMPORTANT]
> 記錄傳送支援 SharePoint Server 中受限於特定資料庫。 如需詳細資訊，請參閱[支援的高可用性和災害復原 SharePoint 資料庫 (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=393121)。 
  
## <a name="phase-7-validate-failover-and-recovery"></a>階段 7： 驗證容錯移轉和復原

此最終階段的目標是確認災害復原解決方案規劃般運作。 若要這麼做，請建立容錯移轉事件，關閉 [實際執行伺服器陣列，並啟動復原伺服器陣列的替代文字。 您可以開始在容錯移轉案例，以手動方式或使用指令碼。
  
第一個步驟是以停止傳入的使用者要求的伺服器陣列服務或內容。 藉由停用 DNS 項目或關閉前端網頁伺服器，您可以這麼做。 「 向下 」 伺服器陣列之後，您可以在容錯移轉到復原伺服器陣列。
  
### <a name="stop-log-shipping"></a>停止記錄傳送

您必須停止伺服器陣列復原之前的記錄傳送。 停止記錄前，傳送在 Azure 中的次要伺服器，然後停止在主要伺服器的內部。 使用下列指令碼上第一個次要伺服器，然後在主要伺服器上停止記錄傳送。 指令碼中的資料庫名稱可能不同，根據您的環境。
  
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

備份必須還原中所建立的順序。 您可以還原特定的交易記錄備份之前，您必須先沒有回復未認可的交易還原下列先前的備份 (也就使用`WITH NORECOVERY`):
  
- 完整資料庫備份和上次的差異備份對這些備份還原，如果有的話，在特定交易記錄備份之前進行。 已建立的最新的完整或差異資料庫備份之前，資料庫所使用的完整復原模式或大量記錄復原模式。
    
- 所有的交易記錄備份的還原採取之後的完整資料庫備份或差異備份 （如果您還原一個），並在特定交易記錄檔之前備份任何交易記錄檔備份。 記錄檔備份必須在其中建立它們沒有任何間距記錄鏈結中的順序套用。
    
若要使網站轉譯，請復原次要伺服器上的內容資料庫，移除所有資料庫連線之前修復。 若要還原的資料庫，請執行下列 SQL 陳述式。
  
```
restore database WSS_Content with recovery

```

> [!IMPORTANT]
> 當您使用 T-SQL 明確時，指定 [ **WITH NORECOVERY** ] 或 [ **WITH RECOVERY**中每個還原陳述式，以消除模稜兩可 — 撰寫指令碼時，這是非常重要。 還原完整及差異備份之後，可以還原的交易記錄檔在 SQL Server Management Studio。 此外，因為已經停止記錄傳送，內容資料庫是處於待命狀態，因此您必須將狀態變更為完整存取權。
  
在 SQL Server Management Studio 中，以滑鼠右鍵按一下 [ **WSS_Content** ] 資料庫，指向 [**工作** > **還原**，然後按一下 [**交易記錄檔**（如果您無法還原完整備份，這是不提供）。 如需詳細資訊，請參閱 <<c0>還原交易記錄檔備份 (SQL Server)>。
  
### <a name="crawl-the-content-source"></a>編目內容來源

您必須啟動完整編目每個內容來源，以還原搜尋服務。 請注意，您會失去從內部部署伺服器陣列，例如搜尋建議某些分析資訊。 在您開始完整編目，使用 Windows PowerShell cmdlet **Restore-spenterprisesearchserviceapplication**並指定記錄傳送和複製的搜尋管理資料庫之前, **Search_Service__DB_<GUID>**。 此 cmdlet 可讓搜尋組態、 結構描述、 受管理的內容、 規則和來源，並建立一組預設的其他元件。
  
若要啟動完整編目，請完成下列步驟：
  
1. 在 SharePoint 2013 管理中心，移至 [**應用程式管理** > **服務應用程式** > **管理服務應用程式**，然後按一下 [您想要編目的 Search Service 應用程式。
    
2. 在 [**搜尋管理**] 頁面上，按一下 [**內容來源**]，指向您想，按一下箭號，，然後按一下 [**啟動完整編目**的內容來源。
    
### <a name="recover-farm-services"></a>復原伺服器陣列服務

下表顯示如何復原具有記錄傳送資料庫，資料庫但不建議還原記錄傳送，並沒有資料庫的服務與服務的服務。
  
> [!IMPORTANT]
> 內部部署 SharePoint 資料庫還原至 Azure 環境將不會復原您沒有已安裝在 Azure 中手動任何 SharePoint 服務。 
  
**表格： 服務應用程式資料庫參考**

|**記錄傳送資料庫還原這些服務**|**這些服務有資料庫，但是我們建議您啟動這些服務，但不還原其資料庫**|**這些服務未執行動作將資料儲存在資料庫;容錯移轉後啟動這些服務**|
|:-----|:-----|:-----|
| 機器翻譯服務 <br/>  Managed Metadata Service <br/>  Secure Store Service <br/>  使用者設定檔。 （僅限設定檔及社交標記資料庫可支援。 同步處理資料庫不支援。） <br/>  Microsoft SharePoint Foundation 訂閱設定服務 <br/> | Usage and Health Data Collection <br/>  State service <br/>  Word automation <br/> | Excel Services <br/>  PerformancePoint Services <br/>  PowerPoint 轉換 <br/>  Visio Graphics Service <br/>  Work Management <br/> |
   
下列範例會示範如何從資料庫還原 Managed Metadata service。
  
這是使用現有的 Managed_Metadata_DB 資料庫。 此資料庫是記錄傳送，但沒有作用中服務應用程式次要伺服器陣列上，因此需要的服務應用程式已經準備就緒之後會保持連線。
  
首先，使用`New-SPMetadataServiceApplication`，並指定`DatabaseName`切換的已還原的資料庫名稱。
  
接下來，設定次要伺服器上的新的 Managed Metadata Service 應用程式，如下所示：
  
- 名稱： Managed Metadata Service
    
- 資料庫伺服器： 從運送的交易記錄檔的資料庫名稱
    
- 資料庫名稱： Managed_Metadata_DB
    
- 應用程式集區： SharePoint 服務應用程式 
    
### <a name="manage-dns-records"></a>管理 DNS 記錄

您必須手動建立 DNS 記錄以指向 SharePoint 伺服器陣列。
  
在大多數情況下您有多部前端網頁伺服器的位置，合理的利用 Windows Server 2012 或硬體負載平衡器來散發要求在伺服器陣列中的 web 前端伺服器之間的網路負載平衡功能。 網路負載平衡還可協助降低風險散發要求送至其他伺服器，如果其中一部 web 前端伺服器失敗。 
  
一般而言，當您設定網路負載平衡，您的叢集指派單一 IP 位址。 您然後建立 DNS 主機記錄的 DNS 提供者中為您指向叢集的網路。 （此專案中，我們將放的 DNS 伺服器在 Azure 中的恢復能力以防內部部署資料中心失敗。）比方說，您可以建立 DNS 記錄，在 「 DNS 管理員在 Active Directory，例如，名為`http://sharepoint.contoso.com`，，指向您的負載平衡叢集的 IP 位址。
  
外部存取您的 SharePoint 伺服器陣列，您可以建立主機記錄在外部 DNS 伺服器與用戶端使用內部網路的相同 URL (例如， `http://sharepoint.contoso.com`)，指向您的防火牆的外部 IP 位址。 (的最佳作法是，使用這個範例中，是要設定分割 DNS，以便將內部 DNS 伺服器的授權`contoso.com`並將要求路由傳送直接對 SharePoint 伺服器陣列叢集中，而不是路由的 DNS 要求至外部 DNS 伺服器。)您然後可以將的外部 IP 位址對應至您的內部部署叢集的內部 IP 位址，讓用戶端找到他們要尋找的資源。
  
從這裡開始，您可能會遇到幾個不同的災害復原案例：
  
 **範例案例： 在內部部署 SharePoint 伺服器陣列是無法使用，因為在內部部署 SharePoint 伺服器陣列的硬體故障。** 在此情況下，您已完成容錯移轉至 Azure 的 SharePoint 伺服器陣列的步驟之後，您可以設定網路上的負載平衡復原 SharePoint 伺服器陣列的 web 前端伺服器，您並未與內部部署伺服器陣列的方式相同。 然後可以將主機記錄重新導向到復原伺服器陣列的叢集 IP 位址指向內部 DNS 提供者。 請注意，它可能需要一些時間之前快取的 DNS 記錄在用戶端上會重新整理，並指向 [復原伺服器陣列。
  
 **範例案例： 在內部部署資料中心是完全遺失。** 此案例中可能會因自然災害，例如火災或濫記而發生。 在此情況下，適用於企業，您可能必須裝載於另一個區域，以及有它自己的目錄服務和 DNS 您 Azure 子網路的次要資料中心。 如同先前的災害案例中，您可以重新導向內部和外部 DNS 記錄以指向 Azure SharePoint 伺服器陣列。 同樣地，記下的 DNS 記錄傳播可能需要一些時間。
  
如果您使用主機命名型網站集合，[主機命名型網站集合架構與部署 (SharePoint 2013)](https://docs.microsoft.com/SharePoint/administration/host-named-site-collection-architecture-and-deployment)中建議的方式，您可能必須在 SharePoint 伺服器陣列，以唯一相同 web 應用程式所裝載的數個網站集合DNS 名稱 (例如，`http://sales.contoso.com`和`http://marketing.contoso.com`)。 在此情況下，您可以建立指向您的叢集 IP 位址的 DNS 記錄每個網站集合。 要求達到您的 SharePoint web 前端伺服器之後，他們會處理路由到適當的網站集合的每個要求。
  
## <a name="microsoft-proof-of-concept-environment"></a>Microsoft 概念證明的環境

我們所設計，並測試此解決方案的概念證明的環境。 我們的測試環境的設計目標是要部署和復原我們可能會發現在客戶的環境中的 SharePoint 伺服器陣列。 我們有幾項假設，但是我們知道伺服器陣列所需的所有沒有任何自訂的方塊擴充功能提供。 拓樸的高可用性設計，藉由從欄位及產品群組中的最佳作法指導。
  
下表說明 HYPER-V 虛擬機器，我們已建立並設定適用於內部部署測試環境。
  
**表格： 虛擬機器內部部署測試**

|**伺服器名稱**|**Role**|**設定**|
|:-----|:-----|:-----|
|DC1  <br/> |與 Active Directory 網域控制站。  <br/> |2 個處理器  <br/> 從 512 MB 到 4 GB 的 RAM  <br/> 1 x 127 GB 硬碟  <br/> |
|RRAS  <br/> |設定路由及遠端存取服務 (RRAS) 角色的伺服器。  <br/> |2 個處理器  <br/> 2-8 GB 的 RAM  <br/> 1 x 127 GB 硬碟  <br/> |
|FS1  <br/> |要備份的共用位置與 DFSR 結束點的檔案伺服器。  <br/> |四個處理器  <br/> 2-12 GB 的 RAM  <br/> 1 x 127 GB 硬碟  <br/> 1 x 1 TB 的硬碟 (SAN)  <br/> 1 x 750 GB 硬碟  <br/> |
|SP-WFE1，SP-WFE2  <br/> |前端網頁伺服器。  <br/> |四個處理器  <br/> 16 GB RAM  <br/> |
|SP-APP1，SP-APP2 SP APP3  <br/> |應用程式伺服器。  <br/> |四個處理器  <br/> 2-16 GB 的 RAM  <br/> |
|SP-SQL-HA1，SP-SQL-HA2  <br/> |使用 SQL Server 2012 AlwaysOn 可用性群組，以提供高可用性設定的資料庫伺服器。 此設定會使用預存程序-sql-ha1 和 SP sql-ha2 作為主要和次要複本。  <br/> |四個處理器  <br/> 2-16 GB 的 RAM  <br/> |
   
下表說明 HYPER-V 虛擬機器，我們已建立並設定的前端網頁伺服器和內部部署測試環境的應用程式伺服器的磁碟機組態。
  
**表格： 虛擬機器的磁碟機需求 Front End 網頁和應用程式伺服器與內部測試**

|**磁碟機代號**|**大小**|**目錄名稱**|**Path**|
|:-----|:-----|:-----|:-----|
|C  <br/> |80  <br/> |系統磁碟機  <br/> |<DriveLetter>:\\程式檔案\\Microsoft SQL Server\\  <br/> |
|E  <br/> |80  <br/> |記錄檔磁碟 (40 GB)  <br/> |<DriveLetter>:\\程式檔案\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\資料  <br/> |
|F  <br/> |80  <br/> |頁面 (36 GB)  <br/> |<DriveLetter>:\\程式檔案\\Microsoft SQL Server\\MSSQL\\資料  <br/> |
   
下表說明 HYPER-V 虛擬機器建立並設定做為內部部署資料庫伺服器的磁碟機組態。 在 [**資料庫引擎組態**] 頁面上，存取**資料目錄**] 索引標籤來設定，並確認，如下表所示的設定。
  
**表格： 內部部署的資料庫伺服器的虛擬機器的磁碟機需求測試**

|**磁碟機代號**|**大小**|**目錄名稱**|**Path**|
|:-----|:-----|:-----|:-----|
|C  <br/> |80  <br/> |資料根目錄  <br/> |<DriveLetter>:\\程式檔案\\Microsoft SQL Server\\  <br/> |
|E  <br/> |500  <br/> |使用者資料庫目錄  <br/> |<DriveLetter>:\\程式檔案\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\資料  <br/> |
|F  <br/> |500  <br/> |使用者資料庫記錄檔目錄  <br/> |<DriveLetter>:\\程式檔案\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\資料  <br/> |
|G  <br/> |500  <br/> |Temp DB 目錄  <br/> |<DriveLetter>:\\程式檔案\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\資料  <br/> |
|H  <br/> |500  <br/> |Temp DB 記錄檔目錄  <br/> |<DriveLetter>:\\程式檔案\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\資料  <br/> |
   
### <a name="setting-up-the-test-environment"></a>設定測試環境

在不同的部署階段，測試小組通常正常運作的第一個的內部部署架構上，然後在對應的 Azure 環境。 這會反映在一般的真實世界情況下，選擇其中內部實際執行伺服器陣列已在執行。 什麼是更重要的是您應該了解目前的生產工作負載、 容量及一般的效能。 除了建置災害復原模式可以符合業務需求，您應該大小復原伺服器陣列的伺服器以傳遞服務的最低層級。 在冷或暖待命環境中，復原伺服器陣列是一般會小於實際執行伺服器陣列。 之後復原伺服器陣列的穩定性及在生產中，在伺服器陣列可以擴充出，並以符合工作負載的需求。
  
我們部署了我們的測試環境中下列三個階段：
  
- 設定混合式基礎結構
    
- 佈建伺服器
    
- 部署為 SharePoint 伺服器陣列
    
#### <a name="set-up-the-hybrid-infrastructure"></a>設定混合式基礎結構

此階段牽涉到內部部署伺服器陣列和在 Azure 中的復原伺服器陣列的網域環境的設定。 除了設定 Active Directory 相關聯的一般工作，測試小組會實作路由解決方案和兩個環境之間的 VPN 連線。
  
#### <a name="provision-the-servers"></a>佈建伺服器

除了伺服器陣列的伺服器，它是所需的網域控制站佈建伺服器，且設定來處理 RRAS 為站台對站 VPN 伺服器。 兩個檔案伺服器已佈建 DFSR 服務，以及數個用戶端電腦已佈建測試人員。
  
#### <a name="deploy-the-sharepoint-farms"></a>部署為 SharePoint 伺服器陣列

為 SharePoint 伺服器陣列已為了簡化環境穩定性及疑難排解帳戶部署在兩個階段中如有必要。 在第一階段中，每個伺服器陣列已部署在每一層的拓撲以支援所需的功能的伺服器的最小數目。
  
我們建立之前建立的 SharePoint 2013 伺服器已安裝的 SQL Server 資料庫伺服器。 因為這是新的部署，我們會建立可用性群組，再部署 SharePoint。 我們建立最佳作法指導 MCS 為基礎的三個群組。 
  
> [!NOTE]
> 建立版面配置區資料庫，以便您可以建立可用性群組在安裝 SharePoint 之前。 如需詳細資訊，請參閱 <<c0>設定 SQL Server 2012 AlwaysOn 可用性群組的 SharePoint 2013
  
我們會建立伺服器陣列，並加入額外的伺服器，依下列順序：
  
- 佈建 SP-sql-ha1 和 SP sql-ha2。
    
- 將 AlwaysOn 設定，並建立伺服器陣列的三個可用性群組。 
    
- 佈建 sp-app1 到主機管理中心。
    
- 佈建 SP WFE1 和 SP WFE2 裝載分散式快取。 
    
我們在命令列執行**psconfig.exe**時，我們會使用_skipRegisterAsDistributedCachehost_參數。 如需詳細資訊，請參閱 <<c0>規劃摘要及 SharePoint Server 2013 中的分散式快取服務。 
  
我們重複在復原環境中的下列步驟：
  
- 佈建亞利桑那州-sql-ha1 和亞利桑那州 sql-ha2。
    
- 將 AlwaysOn 設定，並建立伺服器陣列的三個可用性群組。
    
- 佈建亞利桑那州-APP1 架設管理中心網站。
    
- 佈建亞利桑那州 WFE1 和亞利桑那州 WFE2 裝載分散式快取。
    
我們設定分散式快取及新增的測試使用者，以及測試內容之後，我們會啟動第二個階段的部署。 這需要向外延展層及設定伺服器陣列的伺服器可支援在伺服器陣列架構中所述的高可用性拓撲。
  
下表說明虛擬機器、 子網路，以及我們為我們的復原伺服器陣列設定的可用性設定組。
  
**表格： 復原伺服器陣列基礎結構**

|**伺服器名稱**|**Role**|**設定**|**子網路**|**可用性設定組**|
|:-----|:-----|:-----|:-----|:-----|
|spDRAD  <br/> |使用 Active Directory 網域控制站  <br/> |2 個處理器  <br/> 從 512 MB 到 4 GB 的 RAM  <br/> 1 x 127 GB 硬碟  <br/> |sp ADservers  <br/> ||
|亞利桑那州-SP-FS  <br/> |要備份的共用位置與 DFSR 端點的檔案伺服器  <br/> | A5 組態： <br/>  2 個處理器 <br/>  14 GB 的 RAM <br/>  1 x 127 GB 硬碟 <br/>  1 x 135 GB 硬碟 <br/>  1 x 127 GB 硬碟 <br/>  1 x 150 GB 的硬碟 <br/> |sp databaseservers  <br/> |DATA_SET  <br/> |
|亞利桑那州 WFE1、 亞利桑那州-WFE2  <br/> |Front End 網頁伺服器  <br/> | A5 組態： <br/>  2 個處理器 <br/>  14 GB 的 RAM <br/>  1 x 127 GB 硬碟 <br/> |sp webservers  <br/> |WFE_SET  <br/> |
|亞利桑那州-APP1、 亞利桑那州-APP2、 亞利桑那州-APP3  <br/> |應用程式伺服器  <br/> | A5 組態： <br/>  2 個處理器 <br/>  14 GB 的 RAM <br/>  1 x 127 GB 硬碟 <br/> |sp applicationservers  <br/> |APP_SET  <br/> |
|亞利桑那州-SQL-HA1，亞利桑那州-SQL-HA2  <br/> |資料庫伺服器和 AlwaysOn 可用性群組的主要和次要複本  <br/> | A5 組態： <br/>  2 個處理器 <br/>  14 GB 的 RAM <br/> |sp databaseservers  <br/> |DATA_SET  <br/> |
   
### <a name="operations"></a>營運

這些測試小組穩定的伺服器陣列環境，並完成功能測試之後，開始下列作業來設定內部復原環境所需的工作：
  
- 設定完整及差異備份。
    
- 在內部部署環境與 Azure 環境之間傳送交易記錄檔的檔案伺服器上設定 DFSR。
    
- 設定記錄傳送之主要資料庫伺服器上。
    
- 穩定、 驗證及疑難排解記錄傳送，視需要。 這包含用來識別和記載任何可能會造成問題，例如網路延遲造成記錄傳送或 DFSR 檔案同步處理失敗的行為。
    
### <a name="databases"></a>資料庫

容錯移轉測試涉及下列資料庫： 
  
- WSS_Content
    
- ManagedMetadata
    
- 設定檔資料庫
    
- 同步處理資料庫
    
- 社交資料庫
    
- 內容類型中樞 （專用的內容類型整合中樞的資料庫）
    
## <a name="troubleshooting-tips"></a>疑難排解提示

本節說明我們在我們的測試和其解決方案期間遇到的問題。 
  
### <a name="using-the-term-store-management-tool-caused-the-error-the-managed-metadata-store-or-connection-is-currently-not-available"></a>使用字詞庫管理工具造成錯誤，「 受管理中繼資料儲存區或連線目前無法使用。 」

確定 web 應用程式所使用的應用程式集區帳戶具有字詞儲存區權限的讀取權限。
  
### <a name="custom-term-sets-are-not-available-in-the-site-collection"></a>自訂字詞組中沒有提供網站集合

檢查遺失的服務應用程式相關聯，您的內容的網站集合與內容類型中樞之間。 此外，[**受管理的中繼資料-<site collection name>連線**屬性畫面中，確定已啟用此選項：**此服務應用程式是特定詞彙集的預設儲存位置。**
  
### <a name="the-get-adforest-windows-powershell-command-generates-the-error-the-term-get-adforest-is-not-recognized-as-the-name-of-a-cmdlet-function-script-file-or-operable-program"></a>取得 ADForest Windows PowerShell 命令將會產生錯誤、 」 字詞 ' Get-ADForest' 無法辨識為指令程式、 函式、 指令碼檔案或可執行的程式名稱 」。

當設定使用者設定檔，您會需要 Active Directory 樹系名稱。 在 [新增角色及功能精靈，請確定您已啟用 Active Directory 模組的 Windows PowerShell （在 [**遠端伺服器管理 Tools>Role 管理 Tools>AD DS 與 AD LDS 工具**] 區段中）。 此外，執行下列命令，以協助確保您會在載入相依性的軟體使用**Get-ADForest**之前。
  
```
Import-module servermanager
Import-module activedirectory

```

### <a name="availability-group-creation-fails-at-starting-the-alwaysonhealth-xevent-session-on-server-name"></a>建立可用性群組在啟動 'AlwaysOn_health' XEvent 工作階段失敗 '<server name>'

請確定您的容錯移轉叢集的兩個節點的中] 狀態 」 最多 」 和未 「 暫停 」 或 「 已停止 」。 
  
### <a name="sql-server-log-shipping-job-fails-with-access-denied-error-trying-to-connect-to-the-file-share"></a>SQL Server 記錄傳送工作會失敗並拒絕存取嘗試連接到的檔案共用的錯誤

確定您的 SQL Server 代理程式正在執行網路認證，而不是預設的認證。
  
### <a name="sql-server-log-shipping-job-indicates-success-but-no-files-are-copied"></a>SQL Server 記錄傳送工作表示成功，但不會複製檔

這是因為可用性群組的預設備份喜好設定為**次要偏好**。 請確定您從可用性群組，而不是主要; 的次要伺服器執行記錄傳送工作否則，工作會以無訊息方式失敗。 
  
### <a name="managed-metadata-service-or-other-sharepoint-service-fails-to-start-automatically-after-installation"></a>受管理的中繼資料服務 （或其他 SharePoint 服務） 失敗安裝後會自動啟動

服務可能需要數分鐘才能啟動，請根據效能及目前的 SharePoint Server 的負載。 以手動方式 service 按一下 [**開始]** ，並提供適當時間為啟動時偶爾會重新整理伺服器] 畫面上的服務，來監視其狀態。 萬一服務仍然維持停止，啟用 SharePoint 診斷記錄，請嘗試再次啟動服務，然後再查看錯誤記錄檔。 如需詳細資訊，請參閱 < <b0>SharePoint 2013 中設定診斷記錄</b0>
  
### <a name="after-changing-dns-to-the-azure-failover-environment-client-browsers-continue-to-use-the-old-ip-address-for-the-sharepoint-site"></a>變更後 DNS 至 Azure 的容錯移轉環境，用戶端瀏覽器繼續使用舊的 IP 位址的 SharePoint 網站

您的 DNS 變更可能不會顯示所有的用戶端立即。 測試用戶端上從提升權限的命令提示字元執行下列命令，嘗試再次存取網站。
  
```
Ipconfig /flushdns
```

## <a name="additional-resources"></a>其他資源

[SharePoint 資料庫支援的高可用性和災害復原選項](https://docs.microsoft.com/sharepoint/administration/supported-high-availability-and-disaster-recovery-options-for-sharepoint-databas)
  
[設定 SQL Server 2012 AlwaysOn 可用性群組的 SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=393122)
  
## <a name="see-also"></a>另請參閱

[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)



