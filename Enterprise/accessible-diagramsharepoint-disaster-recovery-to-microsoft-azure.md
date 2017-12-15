---
title: "存取圖表-至 Microsoft Azure 的 SharePoint 災害復原"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 4b855224-8e67-4efa-a3a4-908ee0ca6412
description: "本文是圖表的名為至 Microsoft Azure 的 SharePoint 災害復原可存取的文字版本。"
ms.openlocfilehash: 2babb1910b0cd8dcbfe4cc0bf32de7c714c05fc0
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="accessible-diagram---sharepoint-disaster-recovery-to-microsoft-azure"></a>存取圖表-至 Microsoft Azure 的 SharePoint 災害復原

**摘要：**本文是圖表的名為至 Microsoft Azure 的 SharePoint 災害復原可存取的文字版本。
  
此海報提供可用以建置 Azure 中的復原環境架構的範例。 
  
## <a name="on-premises-environment-with-an-azure-recovery-environment"></a>使用 Azure 復原環境的內部部署環境

此圖顯示用於復原使用 Azure 的內部部署環境的實際執行環境的架構的範例。 
  
### <a name="on-premises-production-environment"></a>內部部署實際執行環境

隨附顯示 live 實際執行環境的圖表具有四個層的伺服器在伺服器陣列中。 
  
#### <a name="tier-1"></a>第 1 層

有兩部前端服務和查詢處理伺服器。有提供兩部伺服器複本的索引磁碟分割。 
  
#### <a name="tier-2"></a>第 2 層

有兩部伺服器的這一層中的分散式快取。 
  
#### <a name="tier-3"></a>第 3 層

在此層中有三部伺服器。每個 server 提供下列服務： 
  
- 後端服務 
    
- 管理員 
    
- 工作流程管理員 
    
- 編目 
    
- 內容處理 
    
- 分析 
    
#### <a name="tier-4"></a>第 4 層

在此層中有兩部伺服器。這兩個伺服器有三個可用性群組，如下所示： 
  
- 可用性群組 #1 可提供搜尋功能。 
    
- 可用性群組 #2 提供內容、 設定及服務應用程式。 
    
- 可用性群組 #3 提供內容。 
    
也有檔案共用中這一層的伺服器。第 4 層的伺服器使用記錄傳送至與此伺服器通訊。此伺服器依次透過分散式檔案系統複寫 (DFSR) 檔案共用與伺服器通訊時在 Azure 暖待命復原環境中下, 一節所述。 
  
### <a name="azure-recovery-environment"></a>Azure 復原環境

#### <a name="warm-standby-environment-running-virtual-machines"></a>虛擬機器中執行的暖待命環境

隨附圖剛好在 Azure 復原環境中複製的內部部署環境。此環境中的檔案共用伺服器所連結到 DFSR 的內部部署環境。DFSR 會傳送到透過檔案共用伺服器復原環境的實際執行環境中的記錄檔。 
  
### <a name="overview"></a>概觀

在內部部署 SharePoint 2013 伺服器陣列嚴重損壞修復環境可以裝載於 Azure。 
  
-  Azure 基礎結構服務提供次要資料中心。
    
- 僅限工資您使用的資源。 
    
- 小型的復原伺服器陣列可以滿足規模和容量目標嚴重損壞之後向外延展。 
    
在 Azure 中的復原伺服器陣列已設定為 [同名盡可能實際執行內部部署伺服器陣列。 
  
- 相同的伺服器角色的表示法。 
    
- 相同的自訂的設定。 
    
- （這些可以在實際執行伺服器陣列較小版） 的搜尋功能相同的設定。 
    
記錄傳送和 DFSR 可用來將資料庫備份和交易記錄檔複製到 Azure 的伺服器陣列。 
  
- DFSR 用來記錄轉移至復原環境的實際執行環境。在 WAN 案例中，DFSR 會比在 Azure 中傳送直接至次要伺服器的記錄檔更有效率。 
    
- 記錄檔會重新 Azure 型 SQL Server 電腦。 
    
- 除非執行復原練習，記錄傳送資料庫不會附加至伺服器陣列。 
    
容錯移轉程序： 
  
1. 停止記錄傳送。 
    
2. 停止接受主要伺服器陣列的流量。 
    
3. 重新顯示的最後一個交易記錄檔。 
    
4. 將內容資料庫附加至伺服器陣列。 
    
5. 開始完整編目。 
    
6. 複寫的服務資料庫還原服務應用程式。 
    
此解決方案所提供的復原目標包括： 
  
- 網站和內容 
    
- 搜尋 （重新編目，沒有搜尋歷程記錄） 
    
- 服務
    
可以由 Microsoft 諮詢服務或協力廠商定址的其他項目： 
  
- 同步處理自訂伺服器陣列方案 
    
- 在內部部署 （Business Data Connectivity (BDC) 及搜尋的內容來源） 的資料來源的連線 
    
- 搜尋還原案例 
    
- 復原時間目標 (RTO) 及復原點目標 (RPO) 
    
#### <a name="cold-standby-environment-running-virtual-machines"></a>虛擬機器中執行的冷待命環境

冷待命環境需要較長的時間開始，但較不昂貴。 
  
- 在伺服器陣列完全建置基礎，但虛擬機器時處於停止之後建立伺服器陣列。您所僅處理成本時執行的虛擬機器，但是儲存空間及網路資料傳輸成本套用。 
    
- 發生災害時，伺服器陣列中的所有虛擬機器已啟動並修正的項目。 
    
- 備份和交易記錄檔會套用至伺服器陣列資料庫。 
    
下列清單說明冷待命環境中的其他程序： 
  
- 開啟虛擬機器定期修補程式、 更新及驗證環境。 
    
- 執行程序來重新整理 DNS 和 IP 位址。 
    
- 設定 SQL AlwaysOn 容錯移轉後。 
    
隨附圖複寫的復原環境的虛擬機器上。容錯移轉之後冷待命環境中，所有虛擬機器已都啟用，且可用性群組已設定使用重新顯示記錄檔提供資料庫伺服器。 
  
## <a name="sharepoint-recovery-environment-in-azure"></a>Azure 中的 SharePoint 復原環境

設計與建置在 Azure 中的容錯移轉環境。 
  
- 在 Azure 中建立虛擬網路。 
    
- 使用 Azure 中使用的網站 VPN 連線虛擬網路連線與內部網路。此連線使用動態閘道 Azure 中使用。 
    
- 一或多個網域控制站部署至 Azure 虛擬網路，並設定下列使用您的內部網域。這些網域控制站的類別目錄伺服器。 
    
- 採用雲端服務和可用性設定 SharePoint 伺服器陣列。 
    
- 部署 SharePoint 伺服器陣列加上的檔案伺服器至主機檔案共用。 
    
- 設定記錄傳送和 DFSR，之間的內部部署環境及 Azure 型復原環境。 
    
隨附的圖顯示內部部署環境及 Azure 虛擬網路的下列功能： 
  
### <a name="on-premises-environment"></a>內部部署環境

- Windows Server 2012 RRAS 
    
- Active Directory 伺服器 
    
與 Azure 虛擬網路透過虛擬私人網路 (VPN) 閘道的內部網路介面。 
  
### <a name="azure-virtual-network"></a>Azure 虛擬網路

VPN 閘道介面 （英文） 與作用中的 VPN 閘道子網路。 
  
Azure 虛擬網路中有三個雲端服務： 
  
- 第一個雲端服務有兩個 Active Directory 和 DNS 伺服器的可用性與設定。 
    
- 第二個雲端服務有三種設定的伺服器： 兩個分散式快取伺服器的可用性設定。與可用性的兩部前端伺服器設定]。與可用性的三個後端伺服器設定]。
    
- 第三個雲端服務有三個可用性設定的資料庫伺服器。其中一個這些資料庫伺服器是記錄傳送和第三個節點的 SQL Server AlwaysOn 節點多數 」 的檔案共用。 
    
### <a name="build-the-ad-ds-hybrid-environment"></a>建立 AD DS 混合式環境

此解決方案的 AD DS 的組態構成 AD DS 是部分部署在內部和部分 Azure 虛擬機器上部署的混合部署案例。 
  
重要 — 部署在 Azure 中的 AD DS 之前，請閱讀指導方針部署 Windows Server Active directory Microsoft Azure 虛擬機器上 (http://msdn.microsoft.com/en-us/library/windowsazure/jj156090.aspx)。 
  
完成指導設計與部署 Active Directory 環境的詳細資訊，請參閱 http://TechNet.microsoft.com。 
  
本參考架構包含兩個虛擬機器設定為網域控制站。每個設定如下： 
  
- 大小 — 小。 
    
- 作業系統 — Windows Server 2012。 
    
- 角色 — AD DS 網域控制站指定為通用類別目錄伺服器。此設定可透過 VPN 連線減少輸出的流量。在多重網域環境中使用變更速率高，設定網域控制站的內部與 Azure 中的通用類別目錄伺服器不同步。 
    
- 資料磁碟 — 將 AD DS 資料庫、 記錄以及 SYSVOL 放在 Azure 資料磁碟上。不放置這些作業系統磁碟或 Azure 所提供的暫存磁碟上。這點很重要。 
    
- 角色 — 安裝及設定 Windows DNS 網域控制站上。 
    
- IP 位址 — 使用動態 IP 位址。這需要建立 Azure 虛擬網路。 
    

