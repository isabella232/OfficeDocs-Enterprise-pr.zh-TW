---
title: "為基礎而建置"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 84348d0c-d9d1-4a98-9b99-8433f9b70e45
description: "摘要： 取得雲端一組的詳細資料儲存區可用來建立您自己的存放服務或解決方案的建置組塊。"
ms.openlocfilehash: 18aa8cb7fa0dda05302a88487dcc69bdbcb174d5
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="build-from-the-ground-up"></a>為基礎而建置

 **摘要：**取得在雲端的詳細資訊可用來建立您自己的存放服務或解決方案的儲存空間建置組塊。
  
"從頭開始建置"儲存解決方案：
  
- 可讓您從頭開始建立您自己的儲存解決方案。 
    
- 需要使用 REST Api 的程式設計 （英文）。
    
- 提供最終的自訂和彈性。
    
下列各節說明每個"從頭開始建置"存放區選項的詳細資料。
  
## <a name="azure-storage-files"></a>Azure 存放區 （檔案）

### <a name="features"></a>功能

- 容易移至雲端的舊版應用程式
    
- 慣用的新應用程式的 blob 儲存
    
- 可以從 Azure 虛擬機器裝載
    
- 可以裝載內部部署與 SMB 3.0
    
- Linux 與 Windows 運作
    
- 不支援 Azure AD 驗證或 Acl （Azure 儲存帳戶索引鍵可提供驗證和授權的存取權的檔案共用）
    
### <a name="common-uses"></a>一般用途

- 移轉至雲端舊版依賴檔案共用的應用程式
    
- 共用開發及測試工具
    
- 分散式應用程式來儲存記錄檔，診斷資料和損毀傾印
    
### <a name="key-storage-scenarios"></a>主要儲存案例

- 備份檔案
    
### <a name="resources"></a>資源

如需詳細資訊，請按一下[這裡](https://msdn.microsoft.com/library/azure/dn166972.aspx)。
  
成本資訊，請按一下[這裡](http://azure.microsoft.com/pricing/details/storage/)。
  
## <a name="azure-storage-blobs"></a>Azure 存放區 (blob)

### <a name="features"></a>功能

- 儲存的每一個帳戶可以保留最多 500 TB （一個訂閱可以有多個儲存區帳戶）
    
- 儲存帳戶分成容器] 中，可以套用至他們的安全性，並可包含 blob
    
- 封鎖 blob 最佳化的資料流和儲存雲端物件最多 200 GB 的大小
    
- 用來代表 PaaS 磁碟的最佳化頁面 blob 和支援隨機寫入多達 1 TB 的大小
    
- 附加的最佳化 blob 附加作業 195 GB
    
- Premium 儲存體提供更快的 IOPS 透過 SSD 儲存
    
### <a name="common-uses"></a>一般用途

- 檔案、 電腦、 資料庫及裝置影像和文字的 web 應用程式的備份
    
- 雲端應用程式的組態資料
    
- 大的資料，例如記錄及其他大型資料集
    
- Azure 用途 blob 其本身服務，例如 HDInsight 和虛擬機器的磁碟儲存空間
    
### <a name="key-storage-scenarios"></a>主要儲存案例

- 管理資料
    
### <a name="resources"></a>資源

如需詳細資訊，請按一下[這裡](https://msdn.microsoft.com/library/azure/dd179376.aspx)。
  
成本資訊，請按一下[這裡](http://azure.microsoft.com/pricing/details/storage/)。
  
## <a name="azure-storage-queues"></a>Azure 存放區 （佇列）

### <a name="features"></a>功能

- 儲存帳戶可以包含任何數目的佇列
    
- 佇列可以包含任何數目的郵件 （直到儲存帳戶已滿）
    
- 佇列的郵件自動的七天後刪除若未擷取和刪除應用程式
    
- 郵件可能是最多 64 KB 的大小
    
- 安全儲存帳戶層級
    
- 佇列都是要將控制項的郵件未原始資料
    
### <a name="common-uses"></a>一般用途

- 建立傳送處理的非同步處理的工作項目
    
- 處理記錄訊息
    
- 將分離應用程式
    
### <a name="key-storage-scenarios"></a>主要儲存案例

- 散佈事件
    
### <a name="resources"></a>資源

如需詳細資訊，請按一下[這裡](https://msdn.microsoft.com/library/azure/dd179353.aspx)。
  
成本資訊，請按一下[這裡](http://azure.microsoft.com/pricing/details/storage/)。
  
## <a name="azure-storage-tables"></a>Azure 存放區 （表格）

### <a name="features"></a>功能

- 適合半結構化資料集
    
- 繁體中文 SQL 比通常較低成本
    
- 如果查詢值的索引鍵查詢慢的非常快速
    
- 大大可擴充;最多個儲存區帳戶的限制資料表的任何數量
    
- 可透過 REST API、 有限的 oData 通訊協定、.NET
    
- 值必須序列化
    
### <a name="common-uses"></a>一般用途

- Web 應用程式的使用者資料
    
- 通訊錄
    
- 裝置資訊
    
### <a name="key-storage-scenarios"></a>主要儲存案例

- 管理資料
    
### <a name="resources"></a>資源

如需詳細資訊，請按一下[這裡](https://msdn.microsoft.com/library/azure/dd179463.aspx)。
  
成本資訊，請按一下[這裡](http://azure.microsoft.com/pricing/details/storage/)。
  
## <a name="microsoft-azure-storage-recommendations"></a>Microsoft Azure 儲存裝置建議

設計與 Azure 儲存自訂的儲存解決方案時, 請謹記下列事項：
  
- 利用更大的延展性增加大小 (> 100 TB) 或多個輸送量 （每秒 > 5000 個作業） 的多個儲存區帳戶。
    
- 設計新增額外儲存空間帳戶組態變更為而非的程式碼變更的功能。
    
- 謹慎選取來啟用想要的比例就插入及查詢效能的表格儲存的資料分割功能。
    
- 選擇 [表格內容的中繼資料 （屬性名稱） 為簡短的欄名稱是預存頻內 （資料行名稱也 [計算向表格列大小上限 1 mb）。
    
- 請儘可能批次到儲存作業。
    
- 積極地快取設定資料庫中將分散式快取的資訊。
    
- 如果應用程式效能及可靠性是取決於快取中擁有的資料可用的特定區段，您的應用程式應該拒絕傳入的要求之前快取已預先填入。
    
- 在垂直 （由表格） 或水平 （跨多個擊碎線段資料表） 資料分割負載分散到多個資料庫。
    
## <a name="see-also"></a>See Also

[Microsoft 雲端儲存為企業架構師的](microsoft-cloud-storage-for-enterprise-architects.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)

[Microsoft 的 Enterprise Cloud 藍圖：IT 決策者的資源](https://sway.com/FJ2xsyWtkJc2taRD)



