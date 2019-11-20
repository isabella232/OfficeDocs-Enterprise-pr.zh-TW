---
title: Office 365 的 NAT 支援
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 1/24/2017
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: 摘要： 提供如何約略算出正確的您可以使用每個 IP 位址使用網路位址轉譯 (NAT) 組織內的用戶端數目的相關詳細資料。
ms.openlocfilehash: 5d252b059661fdd3bad1f86bf552f44b8a747d24
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747897"
---
# <a name="nat-support-with-office-365"></a>Office 365 的 NAT 支援

*本文適用於 Office 365 企業版和 Microsoft 365 企業版。*

先前，指導方針建議您應該使用每個 IP 位址來連線到 Office 365 的 Exchange 用戶端數目上限是每個網路連接埠容納約 2000 個用戶端。
  
## <a name="why-use-nat"></a>為什麼要使用 NAT？

藉由使用 NAT，數以千計的人員的公司網路可以 「 共用 」 一些可公開路由的 IP 位址。
  
最公司網路使用私人 (RFC1918) IP 位址空間。 私人位址空間是配置由網際網路指派數字授權單位 (IANA)，並僅供直接到及傳送自全域網際網路無法路由傳送的網路。
  
若要提供的私人 IP 位址空間裝置的網際網路存取，組織會使用閘道技術，例如防火牆及 proxy 會提供網路位址轉譯 (NAT) 或連接埠位址轉譯 (PAT) 服務。 這些閘道進行從內部流量至網際網路 （包括 Office 365） 的裝置出現似乎來自一或多個可公開路由的 IP 位址。 內部裝置從每個輸出連線會轉譯為不同的來源 TCP 連接埠上的公用 IP 位址。 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a>為什麼需要有 Office 365 同時開啟許多連線？

Outlook 可能會開啟八個以上的連線 (的情況下有增益集、 共用行事曆、 信箱等。)。 因為有可用的最大值的連接埠 64000 Windows 型 NAT 裝置上，可以有最多個 IP 位址背後的 8000 使用者之前的連接埠會耗盡。 請注意，如果客戶使用 NAT 非 Windows 作業系統型裝置，可以使用的連接埠總數取決於正在使用何種 NAT 裝置或軟體。 在此案例中，連接埠的最大數目可能是小於 64000。 連接埠的可用性也會受到其他因素例如可能是 Windows 限制供自己使用，可使用的連接埠總數減少到 60,000.There 4000 個連接埠，請在其他應用程式，例如 Internet Explorer 中，同時無法連線需要額外的連接埠。
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a>支援的裝置與 Office 365 單一公用 IP 位址背後計算上限

若要判斷在單一公用 IP 位址背後的裝置數目上限，您應該監視網路流量，以判斷將連接埠消耗尖峰每個用戶端。 此外，峰值因數應使用的連接埠使用狀況 (最小值 4)。 
  
 **使用下列公式可計算每個 IP 位址支援的裝置數目：**
  
支援的單一公用 IP 位址的裝置上限 = (64000-限制的連接埠) / （尖峰連接埠消耗 + 峰值因數）
  
 **例如，如果下列，則為 true:**
  
- **限制的連接埠：** 4000 operating system

- 每個裝置的**尖峰連接埠消耗：** 6

- **峰值因數：** 4

然後，支援的裝置上限單一公用 IP 位址背後 = (64000 4000) / （6 + 4） = 6000
  
主控套件，從 Microsoft Office Outlook 2007 年 9 月 2011年或 Microsoft Outlook 2010 年 11 月 2011年更新或更新版本的更新，從 Outlook (這兩個 Office Outlook 2007 與服務的連線數目中包含的 Office 365 版本Pack 2 和 Outlook 2010) 到 Exchange 可以是最少 2。 您需要在不同的作業系統，依此類推至判斷您的網路時，需要在尖峰時段的連接埠的最小值和最大數目的使用者行為因素。
  
如果您想要支援多個裝置在單一公用 IP 位址，請依照下列步驟所述來評估可以支援的裝置數目上限：
  
監視網路流量，以判斷將連接埠消耗尖峰每個用戶端。 您應收集此資料：
  
- 從多個位置
    
- 從多個裝置
    
- 在多個時間
    
使用前述公式來計算每個 IP 位址，可以在其環境中支援的最大使用者。
  
有各種方法供用戶端負載分散其他公用 IP 位址。 可用的策略取決於公司閘道方案的功能。 最簡單的解決方案是分割您的使用者位址空間及靜態 「 」 號碼指派的 IP 位址給每個閘道。 多閘道裝置提供的另一個替代方法為使用的 IP 位址的集區的能力。 地址集區的好處是它是很多動態和較不可能需要調整為您的使用者群規模日益成長。
  
## <a name="see-also"></a>請參閱

[管理 Office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Office 365 端點常見問題集](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) (機器翻譯)
