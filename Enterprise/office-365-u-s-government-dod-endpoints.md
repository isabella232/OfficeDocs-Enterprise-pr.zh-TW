---
title: Office 365 美國政府 DoD 端點
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- OGA150
- OGC150
- OGD150
- MOE150
ms.assetid: 5d7dce60-4892-4b58-b45e-ee42fe8a907f
description: 摘要： Office 365 需要網際網路連線。下面的端點應該是客戶使用 Office 365 美國政府 DoD 計劃僅連至。
hideEdit: true
ms.openlocfilehash: 3faca62176b1467829f0333b76a57ce0d5124a96
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539944"
---
# <a name="office-365-us-government-dod-endpoints"></a>Office 365 美國政府 DoD 端點

*適用於： Office 365 系統管理*

 **摘要：** Office 365 需要網際網路連線。下面的端點應該是客戶使用 Office 365 美國政府 DoD 計劃僅連至。
  
> [!NOTE]
> Microsoft 已開發 rest web 服務 IP 位址及 FQDN 此頁面上的項目。此新服務可協助您設定及更新例如防火牆及 proxy 伺服器的網路周邊裝置。您可以下載端點、 清單或特定變更的目前版本的清單。XML 文件、 RSS 摘要、 和 IP 位址及 FQDN 此頁面上的項目最後會取代此服務。若要嘗試取出這個新的服務，請移至[Web 服務](managing-office-365-endpoints.md#webservice)。
  
 **Office 365 端點：**[全球網站 （包括 GCC）](urls-and-ip-address-ranges.md) |  [Office 365 21vianet 來 21 Vianet](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 德國](office-365-germany-endpoints.md) | *Office 365 美國政府 DoD* | [Office 365 美國政府 GCC 高](office-365-u-s-government-gcc-high-endpoints.md) |
  
|||
|:-----|:-----|
|**上次更新：** 8/1/2018- ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [變更記錄訂閱](https://aka.ms/dodendpointrss) <br/> |**下載：** 以[XML 格式](https://aka.ms/usdodendpoints)的完整清單 <br/> |
   
 若要了解我們建議管理使用此資料的網路連線的開頭[管理 Office 365 端點](managing-office-365-endpoints.md)。端點資料更新每個月利用新的 IP 位址及發佈前正在使用中的 30 天的 Url 的開頭。這可讓客戶不要尚未有自動更新以完成其程序，才需要的新連線。如果地址支援呈報、 安全性事件或其他立即操作需求所需的端點可能也更新期間月。以下這個頁面上顯示的資料會從 rest web 服務產生。如果您使用指令碼或網路裝置存取此資料，您應直接移至[Web 服務](managing-office-365-endpoints.md#webservice)。

以下的端點資料是從使用者的電腦連線到 Office 365 需求。它不包含使用 microsoft 的網路連線到客戶網路、 有時稱為的混合或傳入的網路連線。

端點是由四個服務區域所組成。第三個服務區域可以單獨選取進行連線。第四個服務區域是常見的相依性 （稱為 Microsoft 365 一般與 Office Online） 且必須一律網路連線。

資料行所示︰

- **ID**： 識別碼號碼] 列中，也稱為端點設定。此識別碼為相同的 web 服務的端點組所傳回。

- **類別**： 顯示端點集是否分類為 「 最佳化"、"Allow"或"Default"。您可以閱讀這些類別和指引適用於管理放在[http://aka.ms/pnc](http://aka.ms/pnc)。此欄也會列出哪些端點集所需具備網路連線。不需要有網路連線的端點組，我們提供在此欄位表示如果封鎖端點集功能就是遺失的附註。如果您要排除整個服務] 區域中，列出所需的端點組不需要連線。

- **增**： 這是 **[是]** 如果端點組支援 Azure ExpressRoute 透過 Office 365 路由前置詞。包含所示的路由前置詞 BGP 社群對齊 [服務] 區域中所列。**無**增時，這表示 ExpressRoute 不支援此端點組。不過，它不應該假定任何路由已通告增為 [**否**] 所在集的端點。如果您打算使用 Azure AD 連線，請閱讀[特殊考量] 區段中](https://docs.microsoft.com/azure/active-directory/connect/active-directory-AADconnect-instances#microsoft-azure-government-cloud)，確定您具有適當 Azure AD 連線設定。

- **地址**： 列出的 Fqdn 或萬用字元網域名稱和 IP 位址範圍的結束點組。請注意 IP 位址範圍新增一個 CIDR 格式而可能會在指定的網路中包含許多個別的 IP 位址。
 
- **連接埠**： 列出會結合表單網路端點位址的 TCP 或 UDP 連接埠。您可能會注意到一些重複 IP 位址範圍中的沒有列出不同的連接埠。
 
[!INCLUDE [Office 365 U.S. Government DoD endpoints](./includes/office-365-u.s.-government-dod-endpoints.md)]
  
本表附註：

- 安全性及規範中心 」 (SCC) 提供的 Azure ExpressRoute for Office 365 的支援。相同適用於透過例如報表、 稽核、 進階的 eDiscovery、 整合 DLP 及資料控管 SCC 公開的許多功能。兩個特定功能 PST 匯入和 eDiscovery 匯出目前不支援 Azure ExpressRoute 僅 Office 365 路由篩選因其 Azure Blob 存放區的相依性。若要使用這些功能，您需要使用任何可支援 Azure 連線] 選項，包括網際網路連線或 Azure ExpressRoute Azure 公用路由篩選 Azure Blob 儲存的不同連線。您必須評估為這兩個這些功能建立這類連線。Office 365 資訊保護小組所知的這項限制和主動使用兩者這些功能將支援 Azure ExpressRoute for Office 365 身分有限移到 Office 365 路由篩選。

- 還有其他選用的 Office 365 ProPlus 的端點未列出並不需要使用者啟動 Office 365 ProPlus 的應用程式及編輯文件。選用的端點裝載於 Microsoft 資料中心及請勿處理、 傳輸，或將客戶資料儲存。建議的預設網際網路輸出周邊會進入使用者連線到這些端點。
