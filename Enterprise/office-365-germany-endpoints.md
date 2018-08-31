---
title: Office 365 Germany 端點
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 8a113a50-0071-4155-bb8e-eba5a8dbd4c8
description: 如果您的組織會使用 Office 365 及限制您網路上的電腦連線至網際網路，以下您會發現端點 （Fqdn、 連接埠、 Url 及 IPv4 和 IPv6 位址範圍），您應該包含在您輸出允許清單以確保您電腦可以成功地使用 Office 365。
hideEdit: true
ms.openlocfilehash: fa5133391a24a3b9bb82a9dc5065e4dd10bb5bfe
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539922"
---
# <a name="office-365-germany-endpoints"></a>Office 365 Germany 端點

 *適用於： Office 365 系統管理*

**摘要：** Office 365 需要網際網路連線。下面的端點應該是客戶使用**Office 365 德國**計劃僅連至。
  
> [!NOTE]
> Microsoft 已開發 rest web 服務 IP 位址及 FQDN 此頁面上的項目。此新服務可協助您設定及更新例如防火牆及 proxy 伺服器的網路周邊裝置。您可以下載端點、 清單或特定變更的目前版本的清單。XML 文件、 RSS 摘要、 和 IP 位址及 FQDN 此頁面上的項目最後會取代此服務。若要嘗試取出這個新的服務，請移至[Web 服務](managing-office-365-endpoints.md#webservice)。 
  
 **Office 365 端點：**[全球網站 （包括 GCC）](urls-and-ip-address-ranges.md)  |  [Office 365 21vianet 來 21 Vianet](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 德國* | [Office 365 美國政府 DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 美國政府 GCC 高](office-365-u-s-government-gcc-high-endpoints.md)  |
  
|||
|:-----|:-----|
|**上次更新：** 7/2/2018- ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [清單中的 Office 365 德國端點的變更](office-365-germany-endpoints-change-log.md)||

若要了解我們建議管理使用此資料的網路連線的開頭[管理 Office 365 端點](managing-office-365-endpoints.md)。端點資料更新每個月利用新的 IP 位址及發佈前正在使用中的 30 天的 Url 的開頭。這可讓客戶不要尚未有自動更新以完成其程序，才需要的新連線。如果地址支援呈報、 安全性事件或其他立即操作需求所需的端點可能也更新期間月。您一律可以參照[的變更到 Office 365 德國端點清單](office-365-germany-endpoints-change-log.md)。

以下這個頁面上顯示的資料會從 rest web 服務產生。如果您使用指令碼或網路裝置存取此資料，您應直接移至[Web 服務](managing-office-365-endpoints.md#webservice)。

以下的端點資料是從使用者的電腦連線到 Office 365 需求。它不包含使用 microsoft 的網路連線到客戶網路、 有時稱為的混合或傳入的網路連線。

端點是由四個服務區域所組成。第三個服務區域可以單獨選取進行連線。第四個服務區域是常見的相依性 （稱為 Microsoft 365 一般與 Office Online） 且必須一律網路連線。

資料行所示︰

- **ID**： 識別碼號碼] 列中，也稱為端點設定。此識別碼為相同的 web 服務的端點組所傳回。

- **類別**： 顯示端點集是否分類為 「 最佳化"、"Allow"或"Default"。您可以閱讀這些類別和指引適用於管理放在[http://aka.ms/pnc](http://aka.ms/pnc)。此欄也會列出哪些端點集所需具備網路連線。不需要有網路連線的端點組，我們提供在此欄位表示如果封鎖端點集功能就是遺失的附註。如果您要排除整個服務] 區域中，列出所需的端點組不需要連線。

- **增**： 這是 **[是]** 如果端點組支援 Azure ExpressRoute 透過 Office 365 路由前置詞。包含所示的路由前置詞 BGP 社群對齊 [服務] 區域中所列。**無**增時，這表示 ExpressRoute 不支援此端點組。不過，它不應該假定任何路由已通告增為 [**否**] 所在集的端點。

- **地址**： 列出的 Fqdn 或萬用字元網域名稱和 IP 位址範圍的結束點組。請注意 IP 位址範圍新增一個 CIDR 格式而可能會在指定的網路中包含許多個別的 IP 位址。
 
- **連接埠**： 列出會結合表單網路端點位址的 TCP 或 UDP 連接埠。您可能會注意到一些重複 IP 位址範圍中的沒有列出不同的連接埠。

[!INCLUDE [Office 365 Germany endpoints](./includes/office-365-germany-endpoints.md)]

 

