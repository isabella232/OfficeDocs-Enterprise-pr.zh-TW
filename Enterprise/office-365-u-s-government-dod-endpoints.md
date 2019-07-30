---
title: Office 365 美國政府 DoD 端點
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/29/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
search.appverid:
- OGA150
- OGC150
- OGD150
- MOE150
ms.assetid: 5d7dce60-4892-4b58-b45e-ee42fe8a907f
description: 摘要： Office 365 需要連線至網際網路。 下面的端點應該是客戶使用 Office 365 美國政府 DoD 計劃僅連至。
hideEdit: true
ms.openlocfilehash: 93df3f23cbe63ba6956a0724fda9a62b39b36bed
ms.sourcegitcommit: b9ddc5bf47e4c47c7883180db9ef5ad286d6e2fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2019
ms.locfileid: "35925092"
---
# <a name="office-365-us-government-dod-endpoints"></a>Office 365 美國政府 DoD 端點

*適用於： Office 365 系統管理*

 **摘要：** Office 365 需要連線至網際網路。 下面的端點應該是客戶使用 Office 365 美國政府 DoD 計劃僅連至。
  
> [!NOTE]
> Microsoft 發行了以 REST 為基礎且適用於此頁面上的 IP 位址和 FQDN 項目的 Web 服務。這項新服務可協助您設定及更新網路周邊裝置，例如防火牆和 Proxy 伺服器。您可以下載端點的清單、最新版的清單，或是特定變更。這項服務取代了從此頁面連結的 XML 文件，該文件於 2018 年 10 月 2 日被取代。若要嘗試這項新服務，請移至 [Web 服務](office-365-ip-web-service.md)。
  
 **Office 365 端點：** [全球 (包括 GCC)](urls-and-ip-address-ranges.md) | [21 Vianet 提供的 Office 365](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 德國](office-365-germany-endpoints.md) |  *Office 365 美國政府 DoD* | [Office 365 美國政府 GCC High](office-365-u-s-government-gcc-high-endpoints.md) |
  
|||
|:-----|:-----|
|**上次更新：** 07/29/2019- ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [變更記錄訂閱](https://endpoints.office.com/version/USGOVDoD?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |**下載：** 以[JSON 格式](https://endpoints.office.com/endpoints/USGOVDoD?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)的完整清單 <br/> |
   
 若要了解我們的建議管理網路連線使用此資料的開頭[管理 Office 365 端點](managing-office-365-endpoints.md)。 起點處的新 IP 位址和 Url 發佈最遲作用在 30 天每月更新端點資料。 這可讓客戶不尚未有自動更新至新的連線，則需要先完成其處理程序。 端點只有地址支援擴大、 安全性事件或其他即時的操作需求所需的情況下，也可能與月份期間中更新。 所有產生 rest web 服務下此頁面上所顯示的資料。 如果您使用指令碼或網路裝置來存取此資料，您應該直接移至[Web 服務](office-365-ip-web-service.md)。

下列端點資料列出使用者的電腦到 Office 365 的連線需求。這不包括從 Microsoft 到客戶網路的網路連線，有時稱為混合式或輸入網路連線。

端點會分成四個服務區域。 第三個服務區域可個別選取的連線。 第四個服務區域是常見的相依性 （稱為 Microsoft 365 一般及 Office），且必須一律有網路連線。

所顯示的資料行為︰

- **識別碼**：資料列的識別碼，也就是端點設定。此 ID 與端點設定的 web 服務所傳回的相同。

- **類別**：顯示端點設定是否分類為「最佳」、「允許」或「預設」。您可以在[http://aka.ms/pnc](http://aka.ms/pnc)讀取這些類別和在其中管理的指導方針。此欄也會列出網路連線需要哪些端點設定。對於不需要有網路連線的端點設定，我們會在這個欄位中提供附註，表示如果端點設定受到封鎖，將會遺失什麼功能。如果您不包含整個服務區域，視需要列出的端點設定將不需要連線能力。

- **增**： 這是 **[是]** 如果透過 Azure ExpressRoute 支援的端點集，則將它與 Office 365 路由前置詞。 包含所顯示的路由首碼 BGP 社群對齊所列的 [服務] 區域。 當增為 [**否**] 時，這表示，ExpressRoute 不支援此端點集。 不過，它不應該假定沒有路由會通告增所在**否**端點集。 如果您打算使用 Azure AD Connect，讀取[特殊考量一節，](https://docs.microsoft.com/azure/active-directory/connect/active-directory-AADconnect-instances#microsoft-azure-government-cloud)以確定您有適當的 Azure AD Connect 組態。

- **地址**：列出端點設定的 FQDN 或萬用字元網域名稱及 IP 位址範圍。請注意，IP 位址範圍為 CIDR 格式，且在指定的網路中可能包含讓多個個別的 IP 位址。
 
- **連接埠**：列出與地址結合以形成網路端點的 TCP 或 UDP 連接埠。您可能會注意到列出不同連接埠的某些 IP 位址範圍中有重複項目。
 
[!INCLUDE [Office 365 U.S. Government DoD endpoints](./includes/office-365-u.s.-government-dod-endpoints.md)]
  
本表附註：

- 安全性與合規性中心 (SCC) 提供 Azure ExpressRoute 支援的 Office 365。 相同適用於透過例如報告、 稽核、 進階電子文件、 整合 DLP 時，以及資料控管 SCC 公開的許多功能。 兩個特定的功能，PST 匯入和 eDiscovery 匯出目前不支援 Azure ExpressRoute 只有 Office 365 路由篩選器，因為其相依性 Azure Blob 儲存體。 若要使用這些功能，您需要使用任何可支援 Azure 的連線選項，其中包含 Azure 公用路由篩選器的網際網路連線能力或 Azure ExpressRoute 的 Azure Blob 儲存體的不同連線。 您必須評估為這兩個這些功能建立這類連線。 Office 365 資訊保護小組所知的這項限制，以及目前正在運作，以兩個這些功能將 Azure ExpressRoute 支援的 Office 365 為有限帶到 Office 365 路由篩選器。

- 有其他選用的端點 Office 365 專業增強版未列出，且不需要使用者啟動 Office 365 專業增強版的應用程式和編輯文件。 選用的端點裝載於 Microsoft 資料中心和不要處理、 傳輸，或儲存客戶資料。 建議的預設網際網路輸出周邊導向使用者連線至這些端點。
