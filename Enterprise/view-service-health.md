---
title: 如何檢查 Office 365 服務健康情況
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- O365P_ServiceHealthModern
- O365M_ServiceHealthModern
- O365E_ViewStatusServices
- O365E_ServiceHealthModern
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
- IWA160
ms.assetid: 932ad3ad-533c-418a-b938-6e44e8bc33b0
description: 連絡支援服務以查看是否解決的服務中斷之前，請先檢視 Office 365 服務的健康狀態
ms.openlocfilehash: 67595bddaed23222d09c0e7f6f5353b764722f83
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071219"
---
# <a name="how-to-check-office-365-service-health"></a>如何檢查 Office 365 服務健康情況

您可以在[Microsoft 365 系統管理中心](https://admin.microsoft.com)的 Office 365**服務健康情況**] 頁面上檢視 Office 365、 Yammer、 Microsoft Dynamics CRM 和 Microsoft Intune 雲端服務的健康狀況。 如果雲端服務發生問題，在您連絡支援人員或花時間進行疑難排解之前，可以查看服務健康情況，以確定是否為正在開發解決方法的已知問題。 

如果您無法登入服務入口網站，您可以使用[服務狀態] 頁面上](https://status.office365.com)，若要檢查是否有已知問題使您無法登入您的租用戶。
  
### <a name="how-to-check-service-health"></a>如何查看服務健康情況

1. 移至 [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage)，並以系統管理員帳戶登入。 
    
    > [!NOTE]
    > 被指派全域系統管理員或服務系統管理員角色的人員方可檢視服務健康情況。若要允許 Exchange、SharePoint 以及商務用 Skype 管理員檢視服務健康情況，必須同時將服務系統管理員角色指派給他們。
  
2. 若要開啟服務健康情況，在系統管理中心，移至 [**健康情況** > **服務健康情況**，或按一下 [**首頁儀表板**上的**服務健康情況] 卡片**。 儀表板卡片會指出是否有未解決的服務問題，並可連結至詳細的服務健康情況頁面。
    
    ![Dashboard card for service health](media/8ae3de43-7bd5-4ee9-90ed-8b5ba5f9b474.png)
  
3. 各個雲端服務的健康情況狀態是以表格格式呈現，並以圖示代表該服務的可能狀態。
    
> [!TIP]
> 您也可以在行動裝置上使用 [Office 365 Admin App](https://go.microsoft.com/fwlink/p/?linkid=627216) 來檢視服務健康情況，這是藉由推播通知掌握即時資訊的絕佳方式。 
  
### <a name="view-details-of-posted-service-health"></a>檢視已張貼的服務健康情況詳細資料

在預設的檢視中，系統會顯示所有的服務及其目前健康情況狀態。 若要篩選檢視以顯示目前發生事件的服務，請從左側深色列中選取**事件**。 **如果**您選取 [將會顯示目前已張貼建議的服務。 從 [**所有服務**] 檢視中，按一下顯示的服務狀態將會開啟該項建議或事件摘要檢視。 
  
![View of current issues in service health](media/f829a3af-1aca-4dc2-97eb-15d805349b24.png)
  
建議或事件摘要會提供下列資訊： 
  
![螢幕擷取畫面標示服務摘要報告中的欄位](media/0dd6065c-1381-4a5c-8ca0-854c3e043a5c.png)
  
1. 問題識別碼和問題的摘要敘述。
    
2. 目前的狀態。請參閱本文的狀態定義以取得各個可能狀態的說明。
    
3. 描述此問題對使用者造成的影響。
    
4. 此問題開始發生的時間，以及服務健康情況訊息的上次更新時間。在問題發生期間，我們會持續張貼訊息，讓您知道目前套用解決方案的進度。
    
5. 選取 [**顯示詳細資料**] 連結，以查看關於該問題，包括所有已張貼的訊息我們解決方案上工作時的歷程記錄的詳細。 
    
### <a name="translate-service-health-details"></a>翻譯服務健康情況詳細資料

服務健康情況說明都是即時張貼的資訊，因此不會自動翻譯成您的語言，且服務事件的詳細資料僅提供英文版。若要翻譯說明，請依照以下步驟進行：
  
1. 移至 [Translator](https://www.bing.com/translator/)。
    
2. 在 [**服務健康情況**] 頁面上，選取事件或建議。 在 [**顯示詳細資料**，複製有關該問題的文字。
    
3. 在 Translator 中，貼上文字，並選擇 [**翻譯**。
    
### <a name="definitions"></a>定義

在大多數的情況下，服務都會顯示為健康情況良好，沒有進一步的資訊。如果服務發生問題，系統就會以建議或事件的方式表示發生問題，並顯示目前的狀態。
  
> [!TIP]
> 預定維修事件不會顯示在服務健康情況中。 您可以保持最新**訊息中心**，以追蹤預定的維修事件。 篩選至歸類為「規劃變更」 的訊息，即可了解何時要進行變更、變更的作用以及如何準備因應。 如需詳細資料，請參閱 [Office 365 中的訊息中心](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) (機器翻譯)。 
  
### <a name="incidents-and-advisories"></a>事件和建議

|||
|:-----|:-----|
|![Information icon for advisory](media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|如果系統針對某個服務顯示「建議」，表示我們發現了會對部分使用者造成影響的問題，但該服務仍可使用。建議中通常會提供問題的因應措施，且該問題可能是間歇發生，或其波及範圍和對使用者造成的影響並不大。  <br/> |
|![Exclamation point icon for incident](media/a636db57-6083-44dc-bbd5-556850804f17.png)|如果系統針對某個服務顯示有作用中的「事件」，代表這是一個重大問題，且該服務或其主要功能無法使用。例如，使用者可能無法傳送和接收電子郵件，或者無法登入。事件會對使用者造成明顯影響。當有進行中的事件時，我們會在服務健康情況儀表板中提供更新資訊，讓您掌握調查和移轉作業的進度，以及確認解決方案。  <br/> |
   
### <a name="status-definitions"></a>狀態定義

|**狀態**|**定義**|
|:-----|:-----|
|**調查中** | 我們已發現潛在問題，正在收集關於其原因和影響範圍的詳細資訊。 |
|**服務效能下降** | 我們已確認某個問題可能會對服務或功能的使用造成影響。舉例來說，如果某個服務的執行速度比平常慢、出現間歇性中斷，或者某個功能無法正常運作，您就會看見此狀態。 |
|**服務中斷** | 如果我們判斷某個問題會影響使用者存取服務的能力，您就會看見此狀態。這種情況表示問題相當嚴重，且在相同條件下會固定發生。 |
|**正在恢復服務** | 我們已經找出問題的成因，知道要採取什麼修正動作，且正在讓服務恢復到健康情況良好的狀態。 |
|**擴充的復原** | 此狀態表示我們正在進行矯正措施，以便為大多數使用者恢復服務，但需要一些時間才能讓所有受影響的系統恢復正常運作。如果我們在尚未進行永久修復期間先採用暫時修正方法以降低影響，您也可能會看到此狀態。 |
|**調查暫停** | 在我們詳細調查潛在問題後，如果需要客戶提供額外資訊以進行更深入的調查，您就會看到此狀態。如果我們需要您採取行動，我們會告知您我們所需的資料或記錄。 |
|**服務已恢復** | 我們確認矯正措施已解決根本問題，且服務也已恢復為健康情況良好的狀態。如需了解何處發生錯誤，請檢視問題詳細資料。 |
|**發佈後附隨報告** | 我們已發佈之特定問題，其中包含根原因資訊與下一個步驟，以確保不再發生類似的問題張貼附隨報告。 |
   
## <a name="history"></a>歷程記錄

服務健康情況可讓您查看目前的健康狀態，並檢視所有服務建議和有影響您的租用戶中過去 30 天的事件的歷程記錄。 若要檢視所有服務的過去健康情況，請在 [**服務健康情況**] 頁面上選取**檢視歷程記錄**。 
  
![Show link to health history](media/12a3e484-1eb4-497f-8cab-8064bccc2ef5.png)
  
系統就會以清單顯示在所選時間範圍內張貼的所有服務健康情況訊息，如下所示：
  
![View service health history](media/5ed20247-121c-4abe-9fe7-9025e26a2d0e.png)
  
您可能檢視的健康情況歷程記錄的過去 7 天或前 30 天。 選取任何列若要檢視有關該問題的更多詳細資料。
  
如需我們致力於上線時間的詳細資訊，請參閱[從 Office 365 的透明化作業](https://go.microsoft.com/fwlink/?linkid=848695)。
  
## <a name="leave-feedback"></a>提供意見反應

我們的目標是為您提供關於當前問題最及時、正確且實用的資訊。請選取星級評等，告訴我們做得好不好。在您以 1 到 5 顆星給我們評分之後，您可以針對任何特定詳細資料提供意見反應。我們將會根據您的意見反應來微調服務健康情況系統。
  
## <a name="see-also"></a>另請參閱

[在 Microsoft 365 系統管理中心的活動報告](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)