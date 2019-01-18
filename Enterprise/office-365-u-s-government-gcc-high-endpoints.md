---
title: Office 365 美國政府 GCC 高端點
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/17/2019
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: MET150
ms.assetid: cbd2369c-fd96-464c-bf48-c99826b459ee
description: 如果您的組織會使用 Office 365 及限制您網路上的電腦連線至網際網路，以下您會發現端點 （Fqdn、 連接埠、 Url、 IPv4 及 IPv6 位址範圍），您應該包含在您輸出允許清單以確保您電腦可以成功地使用 Office 365。
hideEdit: true
ms.openlocfilehash: 5c849775c8fd55d9e4196ebad6c55cdf56d2ab60
ms.sourcegitcommit: 0c4f50aa55699b8390038efbb8b50dbe10f3eefe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2019
ms.locfileid: "28723380"
---
# <a name="office-365-us-government-gcc-high-endpoints"></a>Office 365 美國政府 GCC 高端點

 *適用於： Office 365 系統管理*

**摘要：** Office 365 需要網際網路連線。下面的端點應可使用 Office 365 美國政府 GCC 高計劃的客戶。
  
> [!NOTE]
> Microsoft 發行了以 REST 為基礎且適用於此頁面上的 IP 位址和 FQDN 項目的 Web 服務。這項新服務可協助您設定及更新網路周邊裝置，例如防火牆和 Proxy 伺服器。您可以下載端點的清單、最新版的清單，或是特定變更。這項服務取代了從此頁面連結的 XML 文件，該文件於 2018 年 10 月 2 日被取代。若要嘗試這項新服務，請移至 [Web 服務](office-365-ip-web-service.md)。
  
 **Office 365 端點：** [全球 (包括 GCC)](urls-and-ip-address-ranges.md) | [21 Vianet 提供的 Office 365](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 德國](office-365-germany-endpoints.md)  |  [Office 365 美國政府 DoD](office-365-u-s-government-dod-endpoints.md) | *Office 365 美國政府 GCC High* |
  
|||
|:-----|:-----|
|**上次更新：** 01/17/2019- ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [變更記錄訂閱](https://endpoints.office.com/version/USGOVGCCHigh?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |**下載：** [JSON](https://endpoints.office.com/endpoints/USGOVGCCHigh?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)格式的完整清單 <br/> |
   
 若要了解我們建議管理使用此資料的網路連線的開頭[管理 Office 365 端點](managing-office-365-endpoints.md)。端點資料更新每個月利用新的 IP 位址及發佈前正在使用中的 30 天的 Url 的開頭。這可讓客戶不要尚未有自動更新以完成其程序，才需要的新連線。如果地址支援呈報、 安全性事件或其他立即操作需求所需的端點可能也更新期間月。以下這個頁面上顯示的資料會從 rest web 服務產生。如果您使用指令碼或網路裝置存取此資料，您應直接移至[Web 服務](office-365-ip-web-service.md)。

下列端點資料列出使用者的電腦到 Office 365 的連線需求。這不包括從 Microsoft 到客戶網路的網路連線，有時稱為混合式或輸入網路連線。

端點則被歸類成四個服務區域。前三個服務區域可以個別選取進行連線。第四個服務區域 (稱為 Microsoft 365 Common 與 Office Online) 的常見相依性，且必須一律具有網路連線能力。

所顯示的資料行為︰

- **識別碼**：資料列的識別碼，也就是端點設定。此 ID 與端點設定的 web 服務所傳回的相同。

- **類別**：顯示端點設定是否分類為「最佳」、「允許」或「預設」。您可以在[http://aka.ms/pnc](http://aka.ms/pnc)讀取這些類別和在其中管理的指導方針。此欄也會列出網路連線需要哪些端點設定。對於不需要有網路連線的端點設定，我們會在這個欄位中提供附註，表示如果端點設定受到封鎖，將會遺失什麼功能。如果您不包含整個服務區域，視需要列出的端點設定將不需要連線能力。

- **增**： 這是 **[是]** 如果端點組支援 Azure ExpressRoute 透過 Office 365 路由前置詞。包含所示的路由前置詞 BGP 社群對齊 [服務] 區域中所列。**無**增時，這表示 ExpressRoute 不支援此端點組。不過，它不應該假定任何路由已通告增為 [**否**] 所在集的端點。如果您打算使用 Azure AD 連線，請閱讀[特殊考量] 區段中](https://docs.microsoft.com/azure/active-directory/connect/active-directory-AADconnect-instances#microsoft-azure-government-cloud)，確定您具有適當 Azure AD 連線設定。

- **地址**：列出端點設定的 FQDN 或萬用字元網域名稱及 IP 位址範圍。請注意，IP 位址範圍為 CIDR 格式，且在指定的網路中可能包含讓多個個別的 IP 位址。
 
- **連接埠**：列出與地址結合以形成網路端點的 TCP 或 UDP 連接埠。您可能會注意到列出不同連接埠的某些 IP 位址範圍中有重複項目。
 
[!INCLUDE [Office 365 U.S. Government GCC High endpoints](./includes/office-365-u.s.-government-gcc-high-endpoints.md)]

本表附註：

- 安全性及規範中心 」 (SCC) 提供的 Azure ExpressRoute for Office 365 的支援。相同適用於透過例如報表、 稽核、 進階的 eDiscovery、 整合 DLP 及資料控管 SCC 公開的許多功能。兩個特定功能 PST 匯入和 eDiscovery 匯出目前不支援 Azure ExpressRoute 僅 Office 365 路由篩選因其 Azure Blob 存放區的相依性。若要使用這些功能，您需要使用任何可支援 Azure 連線] 選項，包括網際網路連線或 Azure ExpressRoute Azure 公用路由篩選 Azure Blob 儲存的不同連線。您必須評估為這兩個這些功能建立這類連線。Office 365 資訊保護小組所知的這項限制和主動使用兩者這些功能將支援 Azure ExpressRoute for Office 365 身分有限移到 Office 365 路由篩選。

- 還有其他選用的 Office 365 ProPlus 的端點未列出並不需要使用者啟動 Office 365 ProPlus 的應用程式及編輯文件。選用的端點裝載於 Microsoft 資料中心及請勿處理、 傳輸，或將客戶資料儲存。建議的預設網際網路輸出周邊會進入使用者連線到這些端點。

