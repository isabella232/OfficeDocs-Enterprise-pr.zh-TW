---
title: 用戶端連線能力
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 4232abcf-4ae5-43aa-bfa1-9a078a99c78b
description: 摘要： 說明用戶端電腦如何連線至 Office 365 租用戶，根據用戶端電腦與 Office 365 租用戶資料中心的位置。
ms.openlocfilehash: 9455147e70a391619e1602f2e36d9162ff2c0928
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490561"
---
# <a name="client-connectivity"></a>用戶端連線能力

 **摘要：** 說明用戶端電腦如何連線至 Office 365 租用戶，根據用戶端電腦與 Office 365 租用戶資料中心的位置。
  
Office 365 位於 Microsoft 資料中心世界各地的可協助保護設定的服務，並執行即使在一個區域，例如地震或電源中斷中沒有發生重大的問題。 當您連接至您的 Office 365 租用戶時，用戶端連線會被導向適當的資料中心正在主控您的租用戶。 決定可以主控您的租用戶規則是由 Microsoft 與您合約定義。 規則，判斷您的用戶端如何取得從該資料中心位置的資料會因您正在使用的服務架構而定。
  
例如，當您登入 Office 365 入口網站時，您是通常是連接到最接近的資料中心，用戶端，而且再根據服務導向您使用下一步]。 如果您啟動電子郵件時，顯示 UI 的初始連線可能仍是來自於最接近的資料中心，但可能最接近的資料中心與以顯示您功能的電子郵件您閱讀中位於到您的租用戶資料中心之間開啟第二個連線。 Microsoft 會執行下列其中一個非常快速資料中心到 datacenter 連線速度產生領域中的頂端十個網路。
  
閱讀本文之後，您可能了解為什麼我們不提供[Office 365 Url 和 IP 位址範圍](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)每個資料中心，只要是太互連和依賴彼此進行的可行的情況下。
  
如果您使用 Azure ExpressRoute for Office 365，在大部分情況下您連線會透過私人連線移至 [Office 365 而不是此處所述的公用連線。 有關如何用戶端連線原則仍然正確。 深入了解[Azure ExpressRoute for Office 365](azure-expressroute.md)。
  
針對上深入 Skype for Business 的網路要求，請閱讀 <<c0>媒體品質和網路連線效能 skype for Business Online。

||
|:-----|
| 本文是[網路規劃和效能調整的 Office 365](https://aka.ms/tune)的一部分。|

> [!NOTE]
> 我們小心謹慎來管理客戶資料，所以很安全且私用在我們的資料中心。 我們採取的步驟來管理隱私權詳細隨附[的 [信任中心](https://go.microsoft.com/fwlink/?LinkID=397383)] 中。
  
## <a name="connecting-to-the-nearest-datacenter"></a>連線到最接近的資料中心

這是最常見的連線，類型，它由 Office 365 入口網站和 Exchange Online。 在此情況下，當用戶端嘗試連線到 Office 365，其電腦的 DNS 查詢決定來自他們的電腦，全球的區域和 Office 365 會要求重新導向到最接近的資料中心。
  
連線至入口網站最接近的資料中心，在停止和用戶端電腦呈現用戶端的租用戶，從該位置的相關資訊。
  
Exchange Online 移步驟更進一步。 當用戶端電腦已連接到最接近的資料中心之後時，該資料中心中的 Exchange 伺服器連接到資料中心租用戶所在實際所示*如何執行此工作] 區段中*下方。 Exchange Online 中最接近的資料中心然後 proxy 伺服器的用戶端電腦的要求至 mailbox server。 移動工作都擷取電子郵件和行事曆項目至 Microsoft 網路加快用戶端電腦的體驗。
  
## <a name="how-does-this-work-for-standard-cloud-offerings"></a>此標準的雲端供應項目的運作方式？

這個連線程序是高流量的標準高價值的 web 應用程式像是 Office 365。 在這個部分，我們大綱，並說明程序中的步驟。 當用戶端電腦不在租用戶的相同區域中時，連線會尋找許多不同根據用戶端連線至服務。
  
 此圖說明 「 北美地區 」 中的租用戶中使用標準的 Office 365 提供客戶。 在此案例中，提出要求的人員旅行歐洲已經過，且正在使用 Office 365 從該位置。
  
1. 用戶端電腦向本機 DNS 伺服器詢問與 Office 365 相關聯的 IP 位址。

2. 用戶端電腦的本機 DNS 伺服器向 Microsoft DNS 伺服器詢問與 Office 365 相關聯的 IP 位址。

3. Microsoft 的 DNS 伺服器傳回地區伺服器名稱 （根據用戶端的 DNS 伺服器的位置），而用戶端電腦重複步驟 1 和 2 來取得地區的 Office 365 資料中心的 IP 位址。

4. 用戶端電腦連線到地區資料中心 IP 位址。

5. Exchange Online 的伺服器連線到客戶的租用戶所在的作用中資料中心。

![最接近地區性資料中心](media/4ea108e9-a299-4e3d-b0d3-469b434ff899.png)
  
## <a name="how-does-this-work-for-sovereign-cloud-offerings"></a>這項工作的主權如何雲端供應項目？

此連線是稍有不同的統領雲端供應項目，例如由 21 Vianet 運作的 Office 365。 Office 365 的統領執行個體中的租用戶，最接近的 Office 365 伺服器會接受入口網站的連線，有租用戶所在的統領區域內的伺服器。 同樣地，存取 SharePoint Online 我們統領雲端或標準供應項目中的客戶會導向至租用戶所在的前端伺服器。 請參閱連線到以下作用中的資料中心。
  
1. 用戶端電腦向本機 DNS 伺服器詢問與 Office 365 相關聯的 IP 位址。

2. 用戶端電腦的本機 DNS 伺服器向 Microsoft DNS 伺服器詢問與 Office 365 相關聯的 IP 位址。

3. Microsoft 的 DNS 伺服器傳回地區伺服器名稱 （根據用戶端的 DNS 伺服器的位置），而用戶端電腦重複步驟 1 和 2 來取得地區的 Office 365 資料中心的 IP 位址。

4. 用戶端電腦連線到地區資料中心 IP 位址。

5. Exchange Online 的伺服器連線到客戶的租用戶所在的作用中資料中心。

![最接近地區性 US 資料中心](media/c0628c54-0059-48c5-8a0f-41bf392ee182.png)
  
## <a name="connecting-to-the-active-datacenter"></a>連線到使用中的資料中心

連線到使用中的資料中心針對重型資料傳輸工作負載和目前由 SharePoint Online 使用。 在此情況下，當用戶端嘗試連線至 Office 365，其瀏覽器重新導向至使用中的資料中心其 SharePoint Online 租用戶。
  
## <a name="how-does-this-work"></a>這如何運作？

當用戶端電腦連線到 SharePoint Online 上，從不同的地區時，連線會重新導向至使用中的 SharePoint Online 資料中心。 在此案例中，客戶會使用標準提供、 產生剩餘本機的入口網站連線並被導向到使用中的資料中心的 SharePoint Online 連線。
  
1. 用戶端電腦向本機 DNS 伺服器詢問與 Office 365 相關聯的 IP 位址。

2. 用戶端電腦的本機 DNS 伺服器向 Microsoft DNS 伺服器詢問與 Office 365 相關聯的 IP 位址。

3. Microsoft 的 DNS 伺服器傳回 （根據用戶端的 Office 365 租用戶的位置），在作用中 SharePoint Online 資料中心的伺服器名稱和用戶端電腦重複步驟 1 和 2 來取得使用中的 Office 365 資料中心的 IP 位址。

4. 用戶端電腦連線到使用中的資料中心 IP 位址。

![使用中 US 資料中心](media/c6d2933f-49cb-4536-bea7-c868707755ae.png)
  
## <a name="connecting-over-virtual-private-networks-vpns"></a>透過虛擬私人網路 (Vpn) 連線

此類型的連線適用於僅當虛擬私人網路 (VPN) 由用戶端電腦。 在現實情況下，Office 365 行為不只是變更因為使用 VPN 時，但 Vpn 通常用來控制用戶端電腦如何建立連線至 Office 365 和通常結果降級的經驗，因此請務必涵蓋。
  
## <a name="how-does-this-work"></a>這如何運作？

當用戶端電腦透過 VPN 連線到位於不同地區的公司辦公室時，而不是在用戶端電腦的位置上的 DNS 伺服器使用位於該辦公室的 DNS 伺服器。 在大多數情況下，此額外透過 VPN 連線將會降低 Office 365 體驗。 Office 365 服務已為使用者盡可能接近的服務客戶連線進行最佳化。 有許多服務利用 Azure 的邊緣網路、 內容傳遞網路和 Microsoft 網路上的可靠的網路容量，最接近的用戶端電腦進行 Office 365 服務的網路要求時傳送的最佳的可能的使用者經驗盡可能。
  
1. 用戶端電腦要求 VPN DNS 伺服器與 Office 365 相關聯的 IP 位址。

2. 用戶端電腦的 VPN DNS 伺服器向 Microsoft DNS 伺服器詢問與 Office 365 相關聯的 IP 位址。

3. Microsoft 的 DNS 伺服器傳回地區伺服器名稱 （根據 VPN DNS 伺服器的位置），以及用戶端電腦重複步驟 1 和 2 來取得地區的 Office 365 資料中心的 IP 位址資訊。

4. 用戶端電腦連線到資料中心他們建立與 VPN 連線的公司辦公室最接近的 IP 位址。

![VPN 資料中心連線性](media/b5f4c06c-65a3-462d-aae8-9a4602dd8d9e.png)
  
您可以使用下列短連結返回這裡：[https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)
  
## <a name="see-also"></a>另請參閱

[管理 Office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[對 Office 365 的網路連線](network-connectivity.md)
