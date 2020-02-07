---
title: 易於存取的圖表-Microsoft Azure 的 SharePoint 嚴重損壞修復
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 4b855224-8e67-4efa-a3a4-908ee0ca6412
f1.keywords:
- NOCSH
description: 本文是圖表的名為 Microsoft Azure 的 SharePoint 嚴重損壞修復易於存取的文字版本。
ms.openlocfilehash: f9bbc62994c1ca36425fa35a4ce294e22596d793
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843841"
---
# <a name="accessible-diagram---sharepoint-disaster-recovery-to-microsoft-azure"></a>易於存取的圖表-Microsoft Azure 的 SharePoint 嚴重損壞修復

**摘要：** 本文是圖表的名為 Microsoft Azure 的 SharePoint 嚴重損壞修復易於存取的文字版本。
  
此海報提供架構的範例建置在 Azure 中的復原環境。 
  
## <a name="on-premises-environment-with-an-azure-recovery-environment"></a>內部部署環境與 Azure 復原環境

此圖顯示用於復原使用 Azure 的內部部署環境的實際執行環境的架構的範例。 
  
### <a name="on-premises-production-environment"></a>內部部署實際執行環境

隨附圖表顯示四個層級的伺服器的實際生產環境中伺服器陣列。 
  
#### <a name="tier-1"></a>第 1 層

有兩部伺服器的前端服務與查詢處理。 沒有提供兩部伺服器複本的索引分割區。 
  
#### <a name="tier-2"></a>第 2 層

有兩部伺服器，在這一層中的分散式快取。 
  
#### <a name="tier-3"></a>第 3 層

在這一層中有三部伺服器。 每一部伺服器會提供下列服務： 
  
- 後端服務 
    
- 管理 
    
- 工作流程管理員 
    
- 編目 
    
- 內容處理 
    
- 分析 
    
#### <a name="tier-4"></a>第 4 層

在這一層中有兩部伺服器。 這兩個伺服器有三個可用性群組，如下所示： 
  
- 可用性群組 #1 提供搜尋功能。 
    
- 可用性群組 #2 提供內容、 設定及服務應用程式。 
    
- 可用性群組 #3 提供內容。 
    
另外還有檔案共用中這一層的伺服器。 第 4 層伺服器使用記錄傳送與此伺服器進行通訊。 此伺服器]，依序進行通訊透過分散式檔案系統複寫 (DFSR) 檔案共用伺服器在 Azure 暖待命復原環境中下, 一節所述。 
  
### <a name="azure-recovery-environment"></a>Azure 復原環境

#### <a name="warm-standby-environment-running-virtual-machines"></a>執行虛擬機器的暖待命環境

隨附圖顯示 Azure 復原環境中完全複寫內部部署環境。 在此環境中的檔案共用伺服器會連結到 DFSR 透過內部部署環境。 DFSR 會將記錄從實際執行環境傳送到透過檔案共用伺服器在復原環境。 
  
### <a name="overview"></a>概觀

內部部署 SharePoint 2013 伺服器陣列的災害復原環境可裝載於 Azure 中。 
  
-  Azure 基礎結構服務提供的次要資料中心。
    
- 僅支付您使用的資源。 
    
- 小型的復原伺服器陣列可以向外延展以滿足擴充與容量目標的嚴重損壞後。 
    
在 Azure 中的復原伺服器陣列已設定為進行完全相同，儘可能在實際執行內部部署伺服器陣列。 
  
- 相同的伺服器角色的表示法。 
    
- 相同的自訂設定的詳細組態。 
    
- 相同的搜尋功能 （這些可以是在實際執行伺服器陣列較小版） 的詳細組態。 
    
記錄傳送和 DFSR 可用來將資料庫備份和交易記錄檔複製到 Azure 的伺服器陣列。 
  
- DFSR 用來從實際執行環境傳送記錄檔，以在復原環境。 在 WAN 案例中，DFSR 比直接將記錄傳送至 Azure 中的次要伺服器更為有效率。 
    
- 記錄檔會重新顯示至以 Azure 為基礎的 SQL Server 電腦。 
    
- 除非執行復原練習，否則，記錄傳送資料庫不會附加至伺服器陣列。 
    
容錯移轉程序： 
  
1. 停止記錄傳送。 
    
2. 停止接受主要伺服器陣列的流量。 
    
3. 重新顯示的最後一筆交易記錄檔。 
    
4. 將內容資料庫附加至伺服器陣列。 
    
5. 開始完整編目。 
    
6. 複寫的服務資料庫還原服務應用程式。 
    
此解決方案所提供的復原目標包括： 
  
- 網站和內容 
    
- 搜尋 （重新編目，沒有搜尋歷程記錄） 
    
- 服務
    
可以 Microsoft 諮詢服務或協力廠商所提到的其他項目： 
  
- 同步處理自訂伺服器陣列解決方案 
    
- 內部部署 （Business Data Connectivity (BDC) 和搜尋內容來源） 的資料來源的連線 
    
- 搜尋還原案例 
    
- 復原時間目標 (RTO) 和復原點目標 (RPO) 
    
#### <a name="cold-standby-environment-running-virtual-machines"></a>執行虛擬機器的冷待命環境

冷待命環境需要較長的時間開始，但會較不昂貴。 
  
- 完全建置在伺服器陣列，但會在建立伺服器陣列之後，會停止虛擬機器。 當執行虛擬機器，但儲存和網路資料傳輸成本套用支付只處理成本。 
    
- 發生災害時，伺服器陣列中的所有虛擬機器已啟動並修正的項目。 
    
- 備份和交易記錄檔會套用至伺服器陣列資料庫。 
    
下列清單說明冷待命環境的其他程序： 
  
- 開啟虛擬機器定期修補程式、 更新及驗證環境。 
    
- 執行程序來重新整理 DNS 和 IP 位址。 
    
- 設定 SQL AlwaysOn 容錯移轉後。 
    
隨附圖表會顯示在虛擬機器上的複寫的復原環境。 容錯移轉之後以冷待命環境，並啟動所有虛擬機器，並使用重新顯示記錄檔若要使用的資料庫伺服器設定可用性群組。 
  
## <a name="sharepoint-recovery-environment-in-azure"></a>Azure 中 SharePoint 復原環境

設計與建置在 Azure 中的容錯移轉環境。 
  
- 在 Azure 中建立虛擬網路。 
    
- 會連接內部部署網路與在 Azure 中的虛擬網路與站台對站 VPN 連線。 這個連線在 Azure 中使用動態的閘道。 
    
- 一或多個網域控制站部署到 Azure 虛擬網路，並設定這些能搭配您的內部部署網域。 這些網域控制站的目錄伺服器。 
    
- 調整雲端服務和可用性設定的 SharePoint 伺服器陣列。 
    
- 將 SharePoint 伺服器陣列加上的檔案伺服器部署至主機檔案共用。 
    
- 設定記錄傳送和 DFSR，內部部署環境與 「 以 Azure 為基礎的復原環境之間。 
    
隨附的圖顯示內部部署環境及 Azure 虛擬網路，包含下列功能： 
  
### <a name="on-premises-environment"></a>內部部署環境

- Windows Server 2012 RRAS 
    
- Active Directory 伺服器 
    
透過虛擬私人網路 (VPN) 閘道的 Azure 虛擬網路與在內部網路介面。 
  
### <a name="azure-virtual-network"></a>Azure 虛擬網路

VPN 閘道介面與作用中的 VPN 閘道子網路。 
  
在 Azure 虛擬網路中有三個雲端服務： 
  
- 第一個雲端服務有兩個 Active Directory 和 DNS 伺服器的可用性與設定。 
    
- 第二個雲端服務有三個一組伺服器： 兩個分散式快取伺服器的可用性設定組。 可用性設定組與兩部前端伺服器。 具有一個可用性設定組的三個後端伺服器。
    
- 第三個雲端服務有三個具有一個可用性設定組的資料庫伺服器。 一種資料庫伺服器是記錄傳送和第三個節點的 SQL Server AlwaysOn 節點多數 」 的檔案共用。 
    
### <a name="build-the-ad-ds-hybrid-environment"></a>建立在 AD DS 混合式環境

針對此解決方案的 AD ds 設定構成了 AD DS 是部分是部署在內部和部分是在 Azure 虛擬機器上部署的混合式部署案例。 
  
重要事項 — 部署在 Azure 中的 AD DS 之前，請閱讀指導方針部署 Windows Server Active directory 上的 Microsoft Azure 虛擬機器 (https://docs.microsoft.com/windows-server/identity/ad-ds/introduction-to-active-directory-domain-services-ad-ds-virtualization-level-100)。 
  
 
本參考架構包含兩部虛擬機器設定為網域控制站。 每個已設定為，如下所示： 
  
- 大小 — 小。 
    
- 作業系統： Windows Server 2012。 
    
- 角色 — AD DS 網域控制站指定為通用類別目錄伺服器。 此組態會減少輸出流量透過 VPN 連線。 在變更速率高的多重網域環境，設定網域控制站上內部與在 Azure 中的通用類別目錄伺服器不同步。 
    
- 資料磁碟 — 將 AD DS 資料庫、 記錄檔及 SYSVOL 放在 Azure 的資料磁碟上。 不放置這些作業系統的磁碟或 Azure 所提供的暫存磁碟上。 這是很重要。 
    
- 角色 — 上安裝及設定 Windows DNS 網域控制站。 
    
- IP 位址-使用動態 IP 位址。 這需要您建立 Azure 虛擬網路。 
    

