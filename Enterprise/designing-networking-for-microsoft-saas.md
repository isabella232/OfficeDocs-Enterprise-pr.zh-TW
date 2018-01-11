---
title: "設計 Microsoft SaaS 的網路"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: "摘要： 了解如何最佳化您的網路存取 Microsoft saas 和服務，包括 Office 365 和 Microsoft Intune Dynamics 365。"
ms.openlocfilehash: 970d27e50e06f4d872de67589295c490aaa6e0e7
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2018
---
# <a name="designing-networking-for-microsoft-saas"></a>設計 Microsoft SaaS 的網路

 **摘要：**了解如何最佳化您的網路存取 Microsoft saas 和服務，包括 Office 365 和 Microsoft Intune Dynamics 365。
  
若要針對 Microsoft SaaS 服務最佳化您的網路，需要仔細分析您的網際網路邊緣、用戶端裝置以及一般 IT 作業。
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a>準備您的網路 Microsoft saas 和服務的步驟

請遵循這些步驟以最佳化您的網路 Microsoft saas 和服務：
  
1. 經歷中[常見的元素 Microsoft cloud 連線的](common-elements-of-microsoft-cloud-connectivity.md)**步驟來準備您的 Microsoft 雲端服務的網路**區段。
    
2. 最佳化 Microsoft saas 和服務使用的 proxy 伺服器建議您網際網路的輸出。
    
3. 最佳化的鄰近和位置建議您網際網路輸送量。
    
4. 最佳化效能的用戶端電腦與內部網路位，都使用的用戶端流量考量。
    
5. 依需要最佳化資料移轉及同步處理使用 IT 作業考量的效能。
    
## <a name="internet-edge-considerations"></a>網際網路 edge 考量

以下是一些考量事項最佳化您的網際網路 edge 和 Microsoft saas 和服務的輸送量。
  
**圖 1： Microsoft saas 和服務的連線選項**

![圖 1：Microsoft SaaS 服務的連線選項](images/Network_Poster/SaaS1.png)
  
圖 1 顯示透過網際網路管道或 ExpressRoute 連線至 Microsoft saas 和服務的內部網路。
  
以下是一些最佳化您的 proxy 伺服器的建議：
  
- 設定 web 用戶端使用 WPAD、 PAC 或 GPO
    
- 不使用 SSL 攔截
    
- 使用 PAC 檔案略過 Microsoft saas 和服務 DNS 名稱的 proxy
    
- 允許 CRL/OCSP 驗證的流量
    
以下是一些要檢查的 proxy 伺服器瓶頸：
  
- 沒有足夠的持續連線 (Outlook)
    
- 沒有足夠的容量
    
- 這麼做關閉網路評估
    
- 需要驗證
    
- 不支援的 UDP 流量 (Skype 企業版)
    
以下是一些鄰近和位置的建議：
  
- 不要在網際網路的流量路由傳送透過私人 WAN
    
- 使用的區域 （英文） 使用者的區域中 DNS 和網際網路流量
    
- ExpressRoute 用於高頻寬至 Office 365 和 Azure 服務並行連線
    
以下是輸出所需的 Office 365 流量的連接埠：
  
- TCP 80 （適用於 CRL/OCSP 檢查）
    
- TCP 443
    
- UDP 3478
    
- TCP 5223
    
- TCP 50000-59999
    
- UDP 50000-59999
    
## <a name="client-usage-considerations"></a>用戶端流量考量

首先，設定一組服務的用戶端將會使用，例如：
  
- Azure Active Directory
    
- Office 365
    
  - Office 用戶端應用程式
    
  - SharePoint Online
    
  - Exchange Online
    
  - 商務用 Skype
    
- Microsoft Intune
    
- Dynamics 365
    
您的用戶端電腦，決定下列項目：
  
- 任何一個時間 （時間日、 虛擬主機、 尖峰流量 troughs） 的數目上限
    
- 尖峰量所需的總頻寬
    
- 延遲到網際網路的輸出裝置
    
- 國家/地區和國家/地區資料中心代管的比較
    
每一種用戶端 （PC、 smartphone 與平板電腦），請確定目前：
  
- 作業系統
    
- 網際網路瀏覽器
    
- TCP/IP 堆疊
    
- 網路硬體
    
- 網路硬體的作業系統驅動程式
    
- 更新及修補程式安裝
    
此外，最佳化內部網路連線輸送量 (有線、 無線、 或 VPN)。
  
如需詳細資訊，請參閱[Office 365 的 NAT 支援](https://support.office.com/article/NAT-support-with-Office-365-170e96ea-d65d-4e51-acac-1de56abe39b9)。
  
搭配 Office 365 使用 ExpressRoute 的最新建議，請參閱[Office 365 ExpressRoute](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd)。
  
最佳化您的內部網路效能，請執行下列動作：
  
- 使用工具來往返時間 (RTTs) 量測貴網際網路 edge 裝置 （PsPing、 Ping、 Tracert、 TraceTCP、 網路監視器）
    
- 執行使用流程通訊協定的輸出路徑分析
    
- 執行中繼裝置 （保留時間下限、 健康情況） 分析
    
如需詳細資訊，請參閱[PsPing 工具](https://technet.microsoft.com/sysinternals/jj729731.aspx)。
  
## <a name="it-operations-considerations"></a>IT 作業考量

以下是一些操作 Microsoft saas 和服務中的 IT 工作負載時要考慮的事項。
  
### <a name="one-time-migrations"></a>一次性移轉

一次性移轉的範例是大量資料傳輸的雲端應用程式] 或 [封存存放區。
  
若要最佳化您的網路上時間移轉：
  
- 避免尖峰網路使用率和修補次數的電腦
    
- 應該已建立基準和來試驗、 評估網路狀況並解決問題才可嘗試實際移轉
    
- 執行事後的未來移轉
    
### <a name="ongoing-synchronizations"></a>進行中的同步處理

進行中的同步處理的範例是目錄資訊、 設定或檔案。
  
若要最佳化您的進行中的同步處理的網路：
  
- 確定已備妥監視系統網路頻寬、 解決或關閉收集的錯誤
    
- 使用以決定需要網路變更 （擴充/向上、 新電路或新增裝置） 的頻寬監控結果
    
如需詳細資訊，請參閱：
  
- [網路與 Office 365 規劃移轉](https://aka.ms/tune)
    
- [Office 365 效能管理 Microsoft 虛擬學院課程 （英文)](https://aka.ms/o365perf)
    
- [Office 365 ExpressRoute](https://aka.ms/expressrouteoffice365)
    
## <a name="see-also"></a>請參閱

[Microsoft Cloud Networking for Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)

[Microsoft 的 Enterprise Cloud 藍圖：IT 決策者的資源](https://sway.com/FJ2xsyWtkJc2taRD)



