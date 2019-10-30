---
title: Office 365 Germany 端點
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/28/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 8a113a50-0071-4155-bb8e-eba5a8dbd4c8
description: 如果您的組織使用 Office 365，而且會限制您網路上的電腦連線到網際網路，以下您會發現的端點 （Fqdn、 連接埠、 Url 和 IPv4 和 IPv6 位址範圍），您應該在包含連出允許清單，以確保您電腦可以順利使用 Office 365。
hideEdit: true
ms.openlocfilehash: 5b87403f0173567d249e3350ef1913378bf1c358
ms.sourcegitcommit: 653bd752db6be18f2f0d31e5abeb8ad734704772
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2019
ms.locfileid: "37765746"
---
# <a name="office-365-germany-endpoints"></a>Office 365 Germany 端點

 *適用於： Office 365 系統管理*

**摘要：** Office 365 需要連線至網際網路。 下列端點應該使用僅限**Office 365 Germany**方案的客戶可以到達。
  
> [!NOTE]
> Microsoft 發行了以 REST 為基礎且適用於此頁面上的 IP 位址和 FQDN 項目的 Web 服務。這項新服務可協助您設定及更新網路周邊裝置，例如防火牆和 Proxy 伺服器。您可以下載端點的清單、最新版的清單，或是特定變更。這項服務取代了從此頁面連結的 XML 文件，該文件於 2018 年 10 月 2 日被取代。若要嘗試這項新服務，請移至 [Web 服務](office-365-ip-web-service.md)。
 
 **Office 365 端點：** [全球 (包括 GCC)](urls-and-ip-address-ranges.md)  | [21 Vianet 提供的 Office 365](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 德國* |  [Office 365 美國政府 DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 美國政府 GCC High](office-365-u-s-government-gcc-high-endpoints.md)  |
  
|||
|:-----|:-----|
|**上次更新：** 10/28/2019- ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [變更記錄訂閱](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) |**下載：** 一個 [JSON 格式](https://endpoints.office.com/endpoints/Germany?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)清單中所有必要與選用的目的地。  <br/> |

若要了解我們的建議管理網路連線使用此資料的開頭[管理 Office 365 端點](managing-office-365-endpoints.md)。 起點處的新 IP 位址和 Url 發佈最遲作用在 30 天每月更新端點資料。 這可讓客戶不尚未有自動更新至新的連線，則需要先完成其處理程序。 端點只有地址支援擴大、 安全性事件或其他即時的操作需求所需的情況下，也可能與月份期間中更新。 您總是可以參照的[變更記錄訂閱](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)。

所有產生 rest web 服務下此頁面上所顯示的資料。 如果您使用指令碼或網路裝置來存取此資料，您應該直接移至[Web 服務](office-365-ip-web-service.md)。

下列端點資料列出使用者的電腦到 Office 365 的連線需求。這不包括從 Microsoft 到客戶網路的網路連線，有時稱為混合式或輸入網路連線。

端點則被歸類成四個服務區域。前三個服務區域可以個別選取進行連線。第四個服務區域 (稱為 Microsoft 365 Common 與 Office) 的常見相依性，且必須一律具有網路連線能力。

所顯示的資料行為︰

- **識別碼**：資料列的識別碼，也就是端點設定。此 ID 與端點設定的 web 服務所傳回的相同。

- **類別**：顯示端點設定是否分類為「最佳」、「允許」或「預設」。您可以在[http://aka.ms/pnc](http://aka.ms/pnc)讀取這些類別和在其中管理的指導方針。此欄也會列出網路連線需要哪些端點設定。對於不需要有網路連線的端點設定，我們會在這個欄位中提供附註，表示如果端點設定受到封鎖，將會遺失什麼功能。如果您不包含整個服務區域，視需要列出的端點設定將不需要連線能力。

- **ER**：如果端點設定透過 Azure ExpressRoute 使用 Office 365 路由首碼支援，則這是 [是]****。包含所顯示路由首碼的 BGP 社群會對齊所列的服務區域。當 ER 為 [否]**** 時，表示 ExpressRoute 不支援此端點集合。不過，不應假設 ER 為 [否]**** 的端點設定不會通告任何路由。

- **地址**：列出端點設定的 FQDN 或萬用字元網域名稱及 IP 位址範圍。請注意，IP 位址範圍為 CIDR 格式，且在指定的網路中可能包含讓多個個別的 IP 位址。
 
- **連接埠**：列出與地址結合以形成網路端點的 TCP 或 UDP 連接埠。您可能會注意到列出不同連接埠的某些 IP 位址範圍中有重複項目。

[!INCLUDE [Office 365 Germany endpoints](./includes/office-365-germany-endpoints.md)]

 

