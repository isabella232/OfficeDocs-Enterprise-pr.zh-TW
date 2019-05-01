---
title: Office 365 服務中的 IPv6 支援
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/10/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c08786fb-298e-437c-8222-dab7625fc815
description: 摘要： 說明 Office 365 政府版方案和 Microsoft Office 365 元件中的 IPv6 支援。
ms.openlocfilehash: 82af5c7659b3c16c8e92b45b65b6868a404eca23
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487750"
---
# <a name="ipv6-support-in-office-365-services"></a>Office 365 服務中的 IPv6 支援

 **摘要**： 說明 Office 365 政府版方案和 Microsoft Office 365 元件中的 IPv6 支援。
  
Office 365 支援 IPv6 和 IPv4;不過，並非所有 Office 365 功能都可以完整都啟用使用 IPv6。 這表示您必須連線至 Office 365 使用 IPv4 和 IPv6。 如果您正在篩選您 Office 365 的輸出流量，Office 365 所支援的 IPv6 位址的完整清單可以找到[Office 365 Url 和 IP 位址範圍](urls-and-ip-address-ranges.md)」 文件中。 設定您的網路，並允許適當的 IPv6 位址之後，您可以下載[Office 365 IPv6 測試計劃](https://go.microsoft.com/fwlink/?LinkId=293447)從 Microsoft 下載中心找到。
  
||
|:-----|
| 本文是[網路規劃和效能調整的 Office 365](https://aka.ms/tune)的一部分。|

## <a name="ipv6-support-in-office-365-subscription-service"></a>Office 365 訂閱服務中的 IPv6 支援

### <a name="exchange-online-and-ipv6"></a>Exchange Online 和 IPv6

如果您用來連線至 Exchange Online 的程式支援 IPv6，則會在有線和無線網路上的預設使用 IPv6。 如果您想要控制 Exchange Online 的通訊，請在[Office 365 Url 和 IP 位址範圍](urls-and-ip-address-ranges.md)中使用的 IP 位址範圍。
  
### <a name="sharepoint-online-and-ipv6"></a>SharePoint Online 和 IPv6

 **Office 365 政府版 G1/G3/G4/K1**如果您用來連線到 SharePoint Online 的程式支援 IPv6，它會嘗試使用預設的 IPv6。
  
 **公用的多重租用戶雲端**Microsoft 可讓 SharePoint Online IPv6，在您的要求。 您需要提供 CIDR 表示貴組織的 DNS 基礎結構的 IP 位址。 請記住，為您的租用戶啟用 IPv6 的其他組織無法共用此 DNS 基礎結構。 啟用 IPv6 時，如果您用來連線到 SharePoint Online 的程式支援 IPv6 之後，它會使用預設的 IPv6。
  
如果您用來連線到 SharePoint Online 的程式支援 IPv6，則會在有線和無線網路上的預設使用 IPv6。 如果您想要控制 SharePoint Online 的通訊，請在[Office 365 Url 和 IP 位址範圍](urls-and-ip-address-ranges.md)中使用的 IP 位址範圍。
  
 **Office 365 政府版 G1/G3/G4/K1**如果您用來連線到 SharePoint Online 的程式支援 IPv6，它會嘗試使用預設的 IPv6。
  
### <a name="skype-for-business-and-ipv6"></a>Skype for Business 和 IPv6

請注意 IPv6 不支援在商務用 Skype 和不再已啟用。
  
### <a name="exchange-online-protection-and-ipv6"></a>Exchange Online Protection 和 IPv6

Exchange Online Protection (EOP) 會支援 IPv6，如果傳輸發生透過傳輸層安全性通訊協定。 EOP 的範圍，請使用[Office 365 Url 和 IP 位址範圍](urls-and-ip-address-ranges.md)。
  
### <a name="ipv6-support-for-office-365-government-offerings"></a>Office 365 政府版方案的 IPv6 支援

Office 365 政府版方案的 IPv6 支援的資訊長 Executive 部門和行政機關，以及聯邦政府採用的網際網路通訊協定第 6 版 (IPv6 符合 Office 的管理和預算 (OMB) 備忘錄) 備忘錄。 [政府適用於 Microsoft Office 365](https://go.microsoft.com/fwlink/p/?LinkId=325414)是一種多承租人服務，我們政府資料儲存在單獨分開的社群雲端。 像其他 Office 365 供應項目，它提供生產力和共同作業服務，包括 Exchange Online、 Skype for Business、 SharePoint Online 和 Office 專業增強版。 

僅適用於 2013年和更新版本，適用於 Microsoft Office 365 政府版方案。 如需有關 Office 365 政府版方案的詳細資訊，請參閱[宣佈政府用 Office 365: 美國政府社群雲端](https://go.microsoft.com/fwlink/p/?LinkId=325414)。 國際流量中武器法規 (ITAR) 是一組的美國政府法規，以控制匯出和匯入防禦相關文章和[美國武器清單 (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415)上的服務。 

適用於企業的 Microsoft Office 365 提供的 Microsoft 產能支援解決方案安全性、 隱私權和法規遵循需求為我們需要聯邦資訊安全的聯邦機構專用主控的服務管理 (FISMA) 憑證和 ITAR 受到商業實體。
  
## <a name="things-to-consider-when-using-ipv6-and-office-365"></a>使用 IPv6 和 Office 365 時的考量事項

我們建議您不要停用 IPv6。 如需詳細資訊，請參閱本[指南的文章](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users)。 若要判斷您網路上正在使用何種 IP 版本，請考慮下列各項：
  
- 如果顯示的**IPConfig**命令，在命令提示字元中包含名為"IPv6 Address"Temporary IPv6 Address"列，您已在您的環境中有 IPv6。

- 如果所有 IPv6 位址開頭都是"fe80"並且對應到名為"Link-local IPv6 Address"列，您不需要在您的環境中的 IPv6。

這些考慮事項可能適用於您的網路：
  
- 在公用訂閱服務不支援購買以信用卡透過 IPv6。 因為政府有 Enterprise Agreement (EA) 授權，這不適用政府社群雲端 (GCC)。

- IPv6 不支援某些 Rights Management Services (RMS) 案例。

- IPv6 不支援 BlackBerry® Enterprise Server (BES)，因為 BlackBerry 不支援 IPv6。

- 如果您使用 Active Directory Federation Services (AD FS) 與 Office 365 時，通知您 Office 365 的 AD FS 網路端點 IPv6 不支援使用。 您不應該包含 AAAA 記錄中的 AD FS DNS 項目時使用 Exchange Online。 

您可以使用下列短連結返回這裡：[https://aka.ms/o365ip6](https://aka.ms/o365ip6)
  
## <a name="see-also"></a>另請參閱

[IPv6 學習藍圖](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))
  
[IPv6 生存指南](https://social.technet.microsoft.com/wiki/contents/articles/1728.ipv6-survival-guide.aspx)
