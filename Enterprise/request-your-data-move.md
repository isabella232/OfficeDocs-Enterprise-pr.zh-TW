---
title: 如何要求資料移動
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 06/28/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5bb64310-36fc-473d-b791-a0176f21707f
description: 現有的 Office 365 客戶必須在他們的國家期限之前提交要求, 才能將參與 Office 365 服務的客戶資料移至新的地理位置。
ms.openlocfilehash: 7558e65672afdb1fa91b8a958472eab00fb89d0c
ms.sourcegitcommit: aca382b615ce79c9f707f74cda6d90fbe87bb626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2019
ms.locfileid: "35392353"
---
# <a name="how-to-request-your-data-move"></a>如何要求資料移動

> [!NOTE]
> 此頁面上的資訊僅適用于已有 Office 365 租使用者在其 geo 中的新資料中心啟動之前的客戶。 
  
現有的 Office 365 客戶有資格在 rest 上要求整個組織的核心客戶資料提前進行遷移。  
  
## <a name="when-can-i-request-a-move"></a>何時可以要求移動？

|**中有帳單位址的客戶**|**要求期間開始**|**要求期限**|
|:-----|:-----|:-----|
|日本  <br/> |2016年8月1日  <br/> |2016年10月31日  <br/> |
|澳大利亞、紐西蘭、斐濟  <br/> |2016年8月1日  <br/> |2016年10月31日  <br/> |
|印度  <br/> |2016年8月1日  <br/> |2016年10月31日  <br/> |
|加拿大  <br/> |2016年8月1日  <br/> |2016年10月31日  <br/> |
|英國  <br/> |2017年3月15日  <br/> |2017年9月15日  <br/> |
|韓國  <br/> |2017年5月1日  <br/> |2017年10月31日  <br/> |
|法國  <br/> |2018年3月14日  <br/> |2018年9月15日  <br/> |
|阿拉伯聯合大公國  <br/> |內  <br/> |內  <br/> |
|南非  <br/> |內  <br/> |內  <br/> |
   
## <a name="how-to-request-a-move"></a>如何要求移動

合格的客戶會在其[Office 365 系統管理中心](https://aka.ms/365admin)看到一頁, 讓他們可以要求他們的核心客戶資料會移至新的資料中心區域。  
  
若要存取 Office 365 系統管理中心的頁面, 請在左側的功能窗格中, 展開 [**設定**], 然後按一下 [**組織設定檔**]。
  
![反白顯示具有組織設定檔的 [設定] 功能表](media/22799fac-32b4-4f79-ae60-3f6ffb7cfbd7.png)
  
在 [**組織設定檔**] 頁面上, 向下滾動至 [**資料派駐選項**] 區段。 
  
![資料常駐卡](media/fdb02cd0-825d-4d9e-bb35-6f806282884f.png)
  
**下列其中一項適用時, 您可能不會看到此區段**:
- 您的租使用者不符合移動程式的資格。  合格取決於租使用者國家/地區。
- 您的所有資料都已位於新的地理位置 (請參閱頁面的 [資料位置] 區段)。 
  
如果您的組織有資料派駐需求, 而且您必須要求提前遷移, 請按一下區段右上方的 [**編輯**]。 螢幕右邊會出現一個新的區段, 說明移動程式的詳細資料。 選取文字旁的切換按鈕, 表示「**是」, 我的組織有資料派駐需求**。 然後按一下 [**儲存**]。
  
![資料中心加入動作畫面](media/f97ab8d2-b0e1-49bf-9d6b-bf75f3081233.png)
  
您應該會看到 [**資料派駐選項**] 區段中的文字變更, 表示**您的組織已要求移動其核心客戶資料。** 您的訊息中心也會有一則確認訊息。 這會確認您已成功要求移動。 


  
## <a name="what-happens-after-requesting-a-move"></a>要求移動後會發生什麼事？

在要求移動之後, 我們會計畫在運作限制允許的情況下快速移動您。 由於許多限制的無法預料的性質, 我們無法分享移動的特定日期或時間範圍。 移動完成後, 您會看到通知。
  
在您的國家/地區的要求期限內, 移動可能需要花費最多24個月才能完成。
  
## <a name="microsoft-teams"></a>Microsoft Teams

Microsoft 小組目前不支援將非地區的客戶內容遷移至國內資料中心, 而您可以在其中提供 Microsoft 小組的資料。  因此, 只有新客戶會將其所有資料都儲存在 Microsoft 團隊支援資料派駐系的新區域中。  若要深入瞭解貴公司位置的 Office 365 資料派駐系,[您的資料位於何處？](https://products.office.com/where-is-your-data-located)   

## <a name="optional-actions-before-you-request-a-move"></a>要求移動之前的選用動作

請視需要執行下列步驟。
  
### <a name="if-you-use-an-ip-based-firewall-add-allow-rules-for-the-new-ip-addresses"></a>如果您使用 IP 型防火牆, 請為新的 IP 位址新增允許規則

建議您對防火牆使用 DNS 篩選, 而不是 IP 位址。 不需要新的 DNS 專案。
  
如果您使用 IP 型防火牆進行網際網路連線, 您必須為目的地資料中心地理位置的新 IP 位址新增允許規則。 除了新伺服器之外, 新的資料中心 geos 的 IP 位址也會持續新增至[Office 365 url 和 IP 位址範圍](https://go.microsoft.com/fwlink/p/?LinkId=229631)。
  
請參閱您的防火牆檔, 以取得如何新增允許規則的相關資訊 (也稱為 whitelisting)。
  
新增 IP 位址之後, 您可能會想要測試新資料中心地理位置的連線能力。 若要這麼做, 建議您在新的資料中心地理位置使用時, 立即建立[新的免費30天試用](https://go.microsoft.com/fwlink/?LinkId=522463)租使用者。 
  
### <a name="test-using-a-new-tenant"></a>使用新租使用者進行測試

如果您想要在移動之前測試連線能力, 您可以在新的資料中心地理位置使用後, 設定[新的免費30天試用租](https://go.microsoft.com/fwlink/?LinkId=522463)使用者, 並使用它來體驗新資料中心地理位置的 Office 365。 
  
試用租使用者無法與您現有的租使用者合併:
  
- 使用者必須使用個別試用帳戶來進行測試。
    
- 沒有任何方法可以在承租人之間移動資料。
    
### <a name="notify-users-to-update-out-of-date-exchange-settings-on-mobile-devices"></a>通知使用者在行動裝置上更新過期的 Exchange 設定

如果使用者有一則將 Exchange 伺服器設為**m.outlook.com**或**podxxxxx.outlook.com**的行動裝置, 建議您在設定行動****[裝置以進行同步處理時, 切換至 outlook.office365.com。使用您的帳戶](https://support.office.com/article/c9139caf-01ab-41a0-827c-3c06ee569ed3)。

## <a name="related-topics"></a>相關主題

[將核心資料移至新的 Office 365 資料中心 geos](moving-data-to-new-datacenter-geos.md)

[資料移動一般常見問題集](data-move-faq.md)

[Microsoft Dynamics CRM Online 的新資料中心 geos](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[依地區的 Azure 服務](https://azure.microsoft.com/en-us/regions/)
  

