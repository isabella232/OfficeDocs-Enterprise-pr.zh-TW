---
title: 用戶端連線
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
description: 摘要：說明用戶端電腦如何連線至 Office 365 租用戶 (視用戶端電腦和 Office 365 租用戶資料中心的位置而定)。
ms.openlocfilehash: 9455147e70a391619e1602f2e36d9162ff2c0928
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223035"
---
# <a name="client-connectivity"></a>用戶端連線

 **摘要：** 說明用戶端電腦如何連線至 Office 365 租用戶 (視用戶端電腦和 Office 365 租用戶資料中心的位置而定)。
  
Office 365 位於 Microsoft 資料中心全球各地以協助保護設定服務] 和 [執行即使地震或電源中斷一個區域中有重大問題。當您連線至 Office 365 租用戶時，用戶端連線會將您導向至適當的資料中心託管租用戶。決定可以主控您的租用戶的規則是由您同意 Microsoft 所定義。決定您的用戶端如何取得該資料中心位置中的資料的規則取決於您正在使用之服務的架構。
  
例如，當您登入 Office 365 入口網站時，正在通常是連線至用戶端最接近的資料中心，然後依據服務導向您使用下一步]。如果您啟動電子郵件] 來顯示使用者介面的初始連線可能仍是來自於最接近的資料中心，但第二個連線可能會開啟最接近的資料中心與您的租用戶位於何處顯示新的電子郵件中功能您閱讀的資料中心之間。Microsoft 可運作中快速非常 fast 資料中心來 datacenter 連線中所產生的世界上方十個網路的其中一個。
  
請閱讀下列文章之後，您可能將瞭解為什麼我們不提供[Office 365 Url 和 IP 位址範圍](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)每個資料中心，他們是只要太互連和依賴彼此進行的合適。
  
如果您使用 Azure ExpressRoute for Office 365，在大多數情況下您連線會傳送透過私人連線至 Office 365，而不是此處所述的公用連線。關於如何用戶端連線原則是仍然正確。深入了解[Office 365 的 Azure ExpressRoute](azure-expressroute.md)。
  
商務網路要求上 Skype 深度，請閱讀下列文章[的媒體品質和 Skype 的商務 Online 中的網路連線效能](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)。

||
|:-----|
| 本文是[網路規劃和 Office 365 的效能調整](https://aka.ms/tune)的一部分。|

> [!NOTE]
> 我們採用小心以安全並私用在我們的資料中心管理客戶資料。[信任中心](https://go.microsoft.com/fwlink/?LinkID=397383)中所包含有關管理隱私權我們採取哪些的步驟的詳細資訊。
  
## <a name="connecting-to-the-nearest-datacenter"></a>連線到最接近的資料中心

這是最常見的連線、 類型及使用 Office 365 入口網站與 Exchange Online。在此情況下，當用戶端嘗試連線至 Office 365，其電腦的 DNS 查詢會決定來自其電腦，全球的地區與 Office 365 將要求重新導向至最接近的資料中心。
  
停止在最接近的資料中心的連線至入口網站及用戶端電腦呈現用戶端的租用戶從該位置的相關資訊。
  
Exchange Online 會移步驟進一步。一旦用戶端電腦連線到最接近的資料中心，在該資料中心的 Exchange 伺服器連線到資料中心租用戶所在實際上如下圖所示*如何執行此動作處理] 區段中*下方。Exchange Online 中最接近的資料中心則 proxy 伺服器的用戶端電腦的要求至信箱伺服器。所移動的擷取電子郵件和行事曆項目至 Microsoft network 粗活加快用戶端電腦的體驗。
  
## <a name="how-does-this-work-for-standard-cloud-offerings"></a>這如何運作的標準雲端方案？

這個連線程序是高流量的標準高價值的 web 應用程式 like Office 365。在本節，我們及大綱說明程序中的步驟。當用戶端電腦不會為承租人的相同區域中時，會尋找更加不同根據用戶端連線至服務連線。
  
 此圖說明客戶使用標準的 Office 365 可以與 「 北美地區 」 中的租用戶。在此案例中，進行要求的人員旅行 Europe 已經過及使用 Office 365 從該位置。
  
1. 用戶端電腦向本機 DNS 伺服器詢問與 Office 365 關聯的 IP 位址。

2. 用戶端電腦的本機 DNS 伺服器會向 Microsoft DNS 伺服器詢問與 Office 365 相關聯的 IP 位址。

3. Microsoft 的 DNS 伺服器傳回區域性伺服器名稱 （根據用戶端的 DNS 伺服器的位置），而且用戶端電腦會重複步驟 1 和 2 來取得地區的 Office 365 資料中心的 IP 位址。

4. 用戶端電腦連線到地區資料中心 IP 位址。

5. Exchange Online 伺服器連線到客戶的租用戶所在的作用中資料中心。

![最接近地區性資料中心](media/4ea108e9-a299-4e3d-b0d3-469b434ff899.png)
  
## <a name="how-does-this-work-for-sovereign-cloud-offerings"></a>這項工作的 sovereign 如何雲端方案？

此連線的例如 Office 365 21vianet 來 21 Vianet 統領雲端方案稍微不同。與 Office 365 統領執行個體中承租人，請將接受入口網站連線的最接近 Office 365 伺服器為統領租用戶所在的區域中的伺服器。同樣地，存取 SharePoint Online 我們統領雲端或標準版方案中的客戶會導向到租用戶所在的前端伺服器。請參閱連線到使用中的資料中心下。
  
1. 用戶端電腦向本機 DNS 伺服器詢問與 Office 365 關聯的 IP 位址。

2. 用戶端電腦的本機 DNS 伺服器會向 Microsoft DNS 伺服器詢問與 Office 365 相關聯的 IP 位址。

3. Microsoft 的 DNS 伺服器傳回區域性伺服器名稱 （根據用戶端的 DNS 伺服器的位置），而且用戶端電腦會重複步驟 1 和 2 來取得地區的 Office 365 資料中心的 IP 位址。

4. 用戶端電腦連線到地區資料中心 IP 位址。

5. Exchange Online 伺服器連線到客戶的租用戶所在的作用中資料中心。

![最接近地區性 US 資料中心](media/c0628c54-0059-48c5-8a0f-41bf392ee182.png)
  
## <a name="connecting-to-the-active-datacenter"></a>連線到使用中的資料中心

連線到使用中的資料中心的粗資料傳輸工作負載的設計與目前使用的 SharePoint Online。在此情況下，當用戶端嘗試連線至 Office 365 其瀏覽器會重新導向至使用中的資料中心其 SharePoint Online 的租用戶。
  
## <a name="how-does-this-work"></a>這如何運作？

當用戶端電腦從不同的地區連線到 SharePoint Online 時，連線會重新導向至使用中的 SharePoint Online 資料中心。在此案例中，客戶使用標準提供、 產生本機剩餘的入口網站連線和 SharePoint Online 被導向到使用中的資料中心的連線。
  
1. 用戶端電腦向本機 DNS 伺服器詢問與 Office 365 關聯的 IP 位址。

2. 用戶端電腦的本機 DNS 伺服器會向 Microsoft DNS 伺服器詢問與 Office 365 相關聯的 IP 位址。

3. Microsoft 的 DNS 伺服器傳回使用中的 SharePoint Online 資料中心 （根據用戶端的 Office 365 租用戶的位置，） 的伺服器名稱和用戶端電腦會重複步驟 1 和 2 來取得使用中的 Office 365 資料中心的 IP 位址。

4. 用戶端電腦連線到使用中資料中心 IP 位址。

![使用中 US 資料中心](media/c6d2933f-49cb-4536-bea7-c868707755ae.png)
  
## <a name="connecting-over-virtual-private-networks-vpns"></a>透過虛擬私人網路 (VPN) 連線

這種連線類型適用於使用時才虛擬私人網路 (VPN) 用戶端電腦。在現實、 Office 365 行為不只是變更因為使用 VPN 時，但 Vpn 通常用來控制用戶端電腦的效能降低體驗所建立的連線至 Office 365 和通常結果，因此請務必涵蓋。
  
## <a name="how-does-this-work"></a>這如何運作？

當用戶端電腦建立不同的區域中的公司辦公室的 VPN 連線時，該 office 中的 DNS 伺服器可用，而不是在用戶端電腦的位置之 DNS 伺服器。在大多數情況下，透過 VPN 此額外連線將會降低的 Office 365 經驗。Office 365 服務已最佳化來做為接近儘可能將一般使用者的服務客戶連線。許多服務利用 Azure 邊緣網路、 內容傳遞網路，與 Microsoft network 可靠的網路容量將接近用戶端電腦位置進行 Office 365 服務的網路要求時傳送最佳可能的使用者經驗儘可能。
  
1. 用戶端電腦 VPN 向 DNS 伺服器詢問與 Office 365 關聯的 IP 位址。

2. 用戶端電腦的 VPN DNS 伺服器會向 Microsoft DNS 伺服器詢問與 Office 365 相關聯的 IP 位址。

3. Microsoft 的 DNS 伺服器傳回區域性伺服器名稱 （根據 VPN DNS 伺服器的位置），而且用戶端電腦會重複步驟 1 和 2 來取得地區的 Office 365 資料中心的 IP 位址資訊。

4. 用戶端電腦連線到資料中心最接近的公司辦公室他們使用 VPN 連線的 IP 位址。

![VPN 資料中心連線性](media/b5f4c06c-65a3-462d-aae8-9a4602dd8d9e.png)
  
以下是您可以使用回來的簡短連結：[https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)
  
## <a name="see-also"></a>另請參閱

[管理 Office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[對 Office 365 的網路連線](network-connectivity.md)
