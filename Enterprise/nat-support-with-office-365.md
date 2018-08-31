---
title: Office 365 的 NAT 支援
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 1/24/2017
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: 摘要：提供如何約略算出使用網路位址轉譯 (NAT) 的組織內每個 IP 位址所能使用的正確用戶端數目的詳細資訊。
ms.openlocfilehash: 733d591bded599cfaece988a624baa7a3c0d4b06
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539912"
---
# <a name="nat-support-with-office-365"></a>Office 365 的 NAT 支援

 **摘要：** 提供如何約略算出使用網路位址轉譯 (NAT) 的組織內每個 IP 位址所能使用的正確用戶端數目的詳細資訊。 
  
先前、 指引建議您應該使用每個 IP 位址來連線至 Office 365 的 Exchange 用戶端的數目上限是每個網路連接埠約 2000 個用戶端。
  
## <a name="why-use-nat"></a>為什麼要使用 NAT？

藉由使用 NAT，公司網路上的數以千計可以 「 共用 」 一些可公開路由傳送的 IP 位址。
  
大部分的公司網路都使用私人 (RFC1918) IP 位址空間。私人位址空間是由網際網路指定編號機構 (IANA) 配置的，其僅供與全球網際網路未直接路由傳送的網路使用。
  
若要提供裝置存取網際網路上的私人 IP 位址空間，組織會使用閘道技術防火牆及 proxy 提供網路位址轉譯 (NAT) 或連接埠位址轉譯 (PAT) 服務。這些閘道進行來自內部流量裝置 （包括 Office 365） 網際網路似乎來自一或多個可公開路由傳送的 IP 位址。每個來自內部裝置的輸出連線會轉譯為不同的來源 TCP 連接埠上的公用 IP 位址。 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a>為何需要有太同時開啟至 Office 365 的連線？

Outlook 可能會開啟 8 個以上的連線 (在有增益集、共用行事曆、信箱等等的情況下)。由於以 Windows 為基礎的 NAT 裝置最多有 64,000 個連接埠，因此在耗盡連接埠之前，每個 IP 位址背後最多能有 8,000 名使用者。請注意，如果客戶使用以非 Windows 作業系統為基礎的 NAT 裝置，可用的連接埠總數將取決於使用的 NAT 裝置或軟體。在這種情況下，連接埠數目上限可能會小於 64,000 個。連接埠的可用性也會受到其他因素影響，例如，Windows 限制必須保留 4,000 個連接埠供其使用，導致可用的連接埠總數減少為 60,000 個。另外，其他應用程式 (如 Internet Explorer) 可能會同時連線，導致需要更多的連接埠。
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a>計算支援的裝置數目上限與 Office 365 搭配單一公用 IP 位址

若要決定單一公用 IP 位址的裝置數目上限，您應該監視來決定將連接埠消耗尖峰每個用戶端的網路流量。此外，峰值因數應用於連接埠使用狀況 (最小 4)。 
  
 **使用下列公式可計算的每個 IP 位址支援的裝置數：**
  
支援的單一公用 IP 位址的裝置上限 = (64000-限制的連接埠) / （連接埠消耗尖峰 + 峰值因數）
  
 **例如，如果下列則為 true：**
  
- **限制的連接埠：** 4000 的作業系統 
    
- 每個裝置的**尖峰連接埠消耗：** 6 
    
- **峰值因數：** 4 
    
然後，支援的裝置上限單一公用 IP 位址 = (64000 4000) / （6 + 4） = 6000
  
與 Office 365 主控套件，包含在從 Microsoft Office Outlook 2007 年 9 月 2011年或年 11 月 2011 for Microsoft Outlook 2010、 更新或更新版本的更新，從 Outlook (這兩種 Office Outlook 2007 與服務的連線數目的版本Pack 2 與 Outlook 2010) 至 Exchange 可以是 2 部。您將需要不同的作業系統使用者行為，依此類推來判斷您的網路需要在尖峰時段的連接埠最小和最大數目的因素。
  
如果您想要支援多個裝置背後的單一公用 IP 位址，請遵循下列步驟，評估可以支援的裝置數目上限：
  
監視來決定將連接埠消耗尖峰每個用戶端的網路流量。您應收集此資料：
  
- 來自多個位置
    
- 來自多部裝置
    
- 在多個時間
    
使用前述公式來計算環境中每個 IP 位址可以支援的使用者上限。
  
有各種方法將用戶端負載分散到其他公用 IP 位址。可用的策略而定的公司閘道解決方案功能。最簡單的解決方案是分割您使用者位址空間和靜態"號碼指派給"的 IP 位址至每個閘道。提供許多閘道裝置的另一個替代項是使用的 IP 位址的集區的能力。地址集區的優點是它是更動態和幾乎需要調整為您的使用者群成長。
  
## <a name="see-also"></a>另請參閱

[管理 Office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Office 365 端點常見問題集](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

