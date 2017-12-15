---
title: "有部分組件"
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
ms.assetid: ccf1b8b3-0d50-4c66-b314-f480245fad5e
description: "摘要： 取得可用來建立自訂的儲存解決方案的雲端儲存選項的詳細資料。"
ms.openlocfilehash: bf6f7586b3a890cd25aba314e4892d5e2ac5bb34
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="some-assembly-required"></a>有部分組件

 **摘要：**取得在雲端的詳細資訊可用來建立自訂的儲存解決方案的儲存選項。
  
「 必要部分組件 」 儲存解決方案：
  
- 使用現有的服務為起點儲存解決方案。
    
- 需要一些設定或編碼。
    
- 可以來自訂以符合您的需求。
    
下列各節說明每個"部分所需的組件 」 儲存解決方案的詳細資料。
  
## <a name="azure-content-delivery-network"></a>Azure 內容傳遞網路

### <a name="features"></a>功能

- 進階及真實時間分析
    
- 針對 DDoS 健全的安全性
    
- 取得內容自動從 Azure 網站或 Azure 雲端服務後設定整合
    
- 與 Akamai 新合作關係
    
- 可以處理突發流量暴增和大量負載
    
### <a name="common-uses"></a>一般用途

- 散佈音訊、 視訊、 應用程式、 圖像及其他檔案更快且更可靠的客戶可以使用其最接近的伺服器
    
### <a name="key-storage-scenarios"></a>主要儲存案例

- 管理資料
    
- 管理影片
    
### <a name="resources"></a>資源

如需詳細資訊，請按一下[這裡](https://azure.microsoft.com/services/cdn/)。
  
成本資訊，請按一下[這裡](https://azure.microsoft.com/pricing/details/cdn/)。
  
## <a name="hdinsight"></a>HdInsight

### <a name="features"></a>功能

- 由雲端提供 Apache Hadoop 分配資料湖服務
    
- 擴充為隨選 petabytes
    
- 處理非結構化與半結構化資料的發展中 Java、.NET、 等等
    
- 略過購買和維護硬體
    
- 連接內部部署 Hadoop 叢集與雲端
    
- 若要部署到 (例如 R、 Giraph、 Solr) 的自訂指令碼的任意 Hadoop 專案的彈性
    
### <a name="common-uses"></a>一般用途

- 資料分析工作量
    
- 在記憶體中的資料處理架構大資料 （火花）
    
- 即時資料流處理 （大量）
    
- 大型交易處理 (OLTP) 的非關聯式資料 (HBase)
    
### <a name="key-storage-scenarios"></a>主要儲存案例

- 管理資料
    
### <a name="resources"></a>資源

如需詳細資訊，請按一下[這裡](https://azure.microsoft.com/services/hdinsight/)。
  
成本資訊，請按一下[這裡](https://azure.microsoft.com/pricing/details/hdinsight/)。
  
## <a name="azure-sql-database"></a>Azure SQL Database

### <a name="features"></a>功能

- 最佳化來減少管理和成本
    
- 自動高可用性、 嚴重損壞復原及升級
    
- 組織管理數百或數千個資料庫的大小達 1 TB 的建議
    
- Sharding 技術可以增加儲存的資料庫之間分割資料
    
- 伸展資料庫與 SQL Server 2016
    
### <a name="common-uses"></a>一般用途

- 含有關聯式資料的新雲端設計 applications
    
- 透過相關聯的圖解、 高度結構化資料集的資料處理
    
- 空間資料或豐富的資料類型
    
### <a name="key-storage-scenarios"></a>主要儲存案例

- 管理資料
    
### <a name="elastic-database"></a>彈入資料庫

幾乎不受限制的資源的 Azure SQL 資料庫時使用：
  
- 總資料量值以符合單一資料庫的規定太大。
    
- 整體工作負載的交易輸送量超過單一資料庫的功能。
    
- 承租人都需要實體隔離從彼此，所以不同的資料庫所需的每個租用戶。
    
- 不同的各節將資料庫必須位在不同地理位置的符合性、 效能或地區性的原因。
    
使用垂直調整，您可以變更 Azure database 效能層級/版或使用彈入資料庫集區。
  
![Azure SQL Database 提供的垂直縮放比例。](images/Storage_Poster/CloudStor-VertScale.png)
  
具有水平調整，您可依需要新增新的資料庫。
  
![Azure SQL Database 提供的水平縮放比例。](images/Storage_Poster/CloudStor-HorizScale.png)
  
按一下[這裡](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-scale-introduction)如需詳細資訊。
  
### <a name="stretch-database-with-sql-server-2016"></a>運用 SQL Server 2016 延展資料庫

伸展資料庫功能可讓您透明和安全地移動冷資料，例如大型表格包含客戶訂單資訊、 Azure 中的 SQL 拉大資料庫已關閉的商務資料的 SQL Server 2016。當拉長、 SQL Server 執行個體、 資料庫、 或甚至是一個表格的內容是 SQL Server 2016 伺服器中的本機資料和 Azure 中的遠端資料的組合。如拉長 SQL Server 2016 自動移到 Azure 會變成合格的資料。
  
![運用 SQL Server 2016 的 Stretch Database。](images/Storage_Poster/CloudStor-Stretch.png)
  
包含的歷程資料的使用者查詢透明轉寄給 Azure SQL 延展資料庫。查詢不需要重新寫入，即使表格會拉長。
  
伸展資料庫提供長期儲存區與透明資料的存取權歷史符合成本效益的選項。它也求解效能及可用性問題發生時表格會變得非常大。
  
按一下[這裡](https://msdn.microsoft.com/library/dn935011.aspx)如需詳細資訊。
  
### <a name="resources"></a>資源

如需詳細資訊，請按一下[這裡](http://azure.microsoft.com/services/sql-database/)。
  
成本資訊，請按一下[這裡](http://azure.microsoft.com/pricing/details/sql-database/)。
  
## <a name="azure-cosmos-db"></a>Azure 宇宙 DB

### <a name="features"></a>功能

- 保證低延遲與擁有無限的可能性、 彈入規模的存放區及輸送量 99.99%可用性 SLA
    
- 跨任何數目的區域與容錯移轉和四種定義完善的一致性層級全域複寫所有資料
    
- 自動索引而不需要結構描述或次要索引的所有資料
    
- Rtf SQL 和 JavaScript 查詢及多項交易
    
### <a name="common-uses"></a>一般用途

- IoT、 行動電話和社交
    
- 遊戲
    
- 零售
    
- 內容管理
    
### <a name="key-storage-scenarios"></a>主要儲存案例

- 管理資料
    
### <a name="cosmos-db-vs-azure-tables-vs-azure-sql-database"></a>宇宙 DB 相對於 Azure 表格和比較 Azure SQL 資料庫

通用宇宙 DB、 Azure 表格儲存及 Azure SQL 資料庫的屬性：
  
- 99.99 可用性 SLA
    
- 完全受管理的資料庫服務
    
- ISO 27001、 HIPAA 及歐盟相容
    
下表顯示不尋常的 Azure 宇宙 DB、 Azure 表格儲存及 Azure SQL Database 屬性。
  
![Cosmos DB 的非通用屬性與Azure 資料表與Azure SQL Database](images/Storage_Poster/CloudStor-Table.png)
  
### <a name="resources"></a>資源

如需詳細資訊，請按一下[這裡](http://azure.microsoft.com/services/documentdb/)。
  
成本資訊，請按一下[這裡](http://azure.microsoft.com/pricing/details/documentdb/)。
  
## <a name="azure-media-services"></a>Azure 媒體服務

### <a name="features"></a>功能

- 對現場與視訊上與刻度 (vod) 傳遞
    
- 高度可用的編碼與資料流
    
- 支援 Flash、 iOS、 Android、 HTML5、 和 xbox 應用程式
    
- Studio 認證 DRM 支援
    
- Rtf 內容獲利
    
- 預先整合協力廠商的廣泛生態系統
    
### <a name="common-uses"></a>一般用途

- 編碼、 儲存及 stream 音訊和視訊向外延展
    
- 即時資料流和 VOD
    
- 簡化視訊的內容管理
    
### <a name="key-storage-scenarios"></a>主要儲存案例

- 管理影片
    
### <a name="resources"></a>資源

如需詳細資訊，請按一下[這裡](https://azure.microsoft.com/services/media-services/)。
  
成本資訊，請按一下[這裡](http://azure.microsoft.com/pricing/details/media-services/)。
  
## <a name="azure-redis-cache"></a>Azure 意指快取

### <a name="features"></a>功能

- 具有高可用性與資料複寫與受管理的 microsoft 容錯移轉的安全、 專用意指伺服器
    
- 如有需要高輸送量任何應用程式的建議
    
- 在 [可用大小調整 530 GB 和超越 （有 Premium 和自動 sharding）
    
- 意指保存性依然存在記憶體中快取 Azure 儲存的資料
    
- 意指叢集可讓您以達到最大刻度與輸送量
    
- 增強的安全性和網路隔離與 Azure 虛擬網路支援
    
### <a name="common-uses"></a>一般用途

- 反向查閱 Azure，例如宇宙 DB 與 Azure SQL 資料庫中的任何存放服務中的資料
    
- 與其他資料儲存區同步處理的內容
    
### <a name="key-storage-scenarios"></a>主要儲存案例

- 快取資料
    
- 高輸送量應用程式的訊息 broker
    
### <a name="resources"></a>資源

如需詳細資訊，請按一下[這裡](http://azure.microsoft.com/services/cache/)。
  
成本資訊，請按一下[這裡](http://azure.microsoft.com/pricing/details/cache/)。
  
## <a name="sql-server-on-an-azure-vm"></a>在 Azure 虛擬機器上的 SQL Server

### <a name="features"></a>功能

- 在 Azure 虛擬機器上執行安裝的應用程式的 SQL Server
    
- 使用 with SQL Server 圖庫映像安裝或將您自己的 SQL Server 授權
    
### <a name="common-uses"></a>一般用途

- 管理應用程式的資料
    
### <a name="key-storage-scenarios"></a>主要儲存案例

- 管理資料
    
### <a name="resources"></a>資源

如需詳細資訊，請按一下[這裡](http://azure.microsoft.com/services/virtual-machines/)。
  
成本資訊，請按一下[這裡](http://azure.microsoft.com/pricing/details/virtual-machines/)。
  
## <a name="storsimple"></a>StorSimple

### <a name="features"></a>功能

- 可擴充企業混合 SAN 儲存 SSD 與 HDD 在內部部署混合式存放裝置陣列，與雲端儲存為整合式解決方案的副檔名
    
- 內嵌 deduplication、 壓縮、 自動 tiering、 和加密非結構化及半結構化資料
    
- 使用雲端快照自動化離站資料保護
    
- 高效率、 位置無關的嚴重損壞修復
    
- Azure 中的 StorSimple 虛擬 Appliance 與企業資料的資料行動力
    
### <a name="common-uses"></a>一般用途

- 管理檔案共用、 封存、 和其他資料存放庫相關的資料成長
    
- 離站資料保護和嚴重損壞修復的檔案共用、 虛擬機器、 SQL 和 SharePoint （使用遠端 Blob 存放區）
    
- 運用複製 Azure 中的資料並增加商務彈性雲端快照
    
### <a name="key-storage-scenarios"></a>主要儲存案例

- 管理資料
    
- 共同作業
    
### <a name="resources"></a>資源

如需詳細資訊，請按一下[這裡](http://azure.microsoft.com/services/storsimple/)。
  
成本資訊，請按一下[這裡](http://azure.microsoft.com/pricing/details/storsimple/)。
  
## <a name="azure-sql-data-warehouse"></a>Azure SQL 資料倉儲

### <a name="features"></a>功能

- 可擴充以 petabytes 最多 32 的並行查詢的彈入的資料倉儲
    
- 管理大量 fast 與結構化資料分析動態放大及縮小 compute 秒
    
- 支援透明資料加密
    
- 備份 7 天的每個 8 小時
    
### <a name="common-uses"></a>一般用途

- 銷售報表
    
- 使用情況報告
    
- 大量資料
    
### <a name="key-storage-scenarios"></a>主要儲存案例

- 管理資料
    
### <a name="resources"></a>資源

如需詳細資訊，請按一下[這裡](https://azure.microsoft.com/services/sql-data-warehouse/)。
  
成本資訊，請按一下[這裡](https://azure.microsoft.com/pricing/details/sql-data-warehouse/)。
  
## <a name="azure-data-lake-store"></a>Azure 資料湖存放區

### <a name="features"></a>功能

- 大資料分析工作量超規模存放庫
    
- Hadoop 分散式檔案系統的雲端
    
- 檔案大小沒有固定的限制
    
- 帳戶大小沒有固定的限制
    
- 非結構化與結構化資料以其原生格式
    
- 若要增加分析效能大規模輸送量
    
- 持續性高、 可用性及可靠性 （達 99.9%企業級 SLA 和 24/7 支援）
    
- Azure Active Directory 存取控制
    
### <a name="common-uses"></a>一般用途

- 為儲存每個收集在單一位置中的資料類型的整個企業的存放庫
    
### <a name="key-storage-scenarios"></a>主要儲存案例

- 管理資料
    
### <a name="resources"></a>資源

如需詳細資訊，請按一下[這裡](https://azure.microsoft.com/services/data-lake-store/)。
  
成本資訊，請按一下[這裡](https://azure.microsoft.com/pricing/details/data-lake-store/)。
  
## <a name="next-step"></a>下一步

檢閱[設定為基礎而建置](build-from-the-ground-up.md)雲端儲存選項。
  
## <a name="see-also"></a>See Also

[Microsoft 雲端儲存為企業架構師的](microsoft-cloud-storage-for-enterprise-architects.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)

[Microsoft 的 Enterprise Cloud 藍圖：IT 決策者的資源](https://sway.com/FJ2xsyWtkJc2taRD)



