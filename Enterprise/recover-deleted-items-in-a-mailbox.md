---
title: 復原使用者信箱中刪除的郵件 - 系統管理說明
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: eb15194b-63ec-41b0-8d90-1823d3f558e4
description: '本文適用於系統管理員。沒有使用者永久刪除項目從其 Outlook 信箱吗？使用者想它們後，但不能復原這些。您可以復原已清除的項目如果他們尚未從使用者的信箱永久移除。 '
ms.openlocfilehash: abfc0a1a35d8e694197e12d05a2206dd4e3eb37a
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539992"
---
# <a name="recover-deleted-items-in-a-user-mailbox---admin-help"></a>復原使用者信箱中刪除的郵件 - 系統管理說明

**本文為系統管理員。您嘗試要復原刪除的項目在您自己的信箱吗？** 請嘗試下列其中一項：
- [在 Windows 版 Outlook 復原已刪除的項目](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
- [復原 Outlook Web App 中刪除的郵件或電子郵件](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
- [在網路上的 Outlook 中還原已刪除電子郵件](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
- [Outlook.com](https://go.microsoft.com/fwlink/p/?LinkID=623435)
   
沒有使用者永久刪除項目從其 Outlook 信箱吗？使用者想它們後，但不能復原這些。您可以復原已清除的項目如果他們尚未從使用者的信箱永久移除。達成此目的 Exchange Online 中使用就地 eDiscovery 工具來搜尋的已刪除的電子郵件及其他項目 — 例如連絡人、 行事曆約會和工作和 — 在使用者的信箱。如果您發現已刪除的項目時，您可以將其匯出至 PST 檔案 （也稱為 Outlook 資料檔案），該使用者接著可以使用回復到其信箱還原項目。
  
以下是使用者的信箱中復原刪除的項目使用的步驟。將此時間？第一次可能需要完成所有步驟，視您的多少項目正在嘗試復原 20 或 30 分鐘。
  
> [!NOTE]
> 您必須是**Exchange 系統管理員**或**全域管理員**Office 365 中也是組織管理角色群組的成員在 Exchange Online 才能執行本文中的步驟。如需詳細資訊，請參閱 ＜[關於 Office 365 系統管理員角色](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d)。 
  
## <a name="step-1-assign-yourself-ediscovery-permissions"></a>步驟 1： 指派自行 eDiscovery 權限
<a name="step1"> </a>

第一個步驟是您自己的必要權限 Exchange Online 中指派讓您可以使用就地 eDiscovery 工具來搜尋使用者的信箱。您只能有一次執行這項作業。如果您有未來搜尋另一個信箱，您可以略過此步驟。
  
1. 使用工作或學校帳戶[登入 Office 365 企業版的位置](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4)。 
    
2. 選取 [應用程式啟動器圖示![Office 365 中的應用程式啟動器圖示](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png)中左上角按一下 [**系統管理**。
    
3. 在 Office 365 系統管理中心的左方導覽，依序展開 [**系統置中**，] 和 [ **Exchange**。
    
    ![Admin center 清單](media/7d308eb7-ba63-4156-a845-3770facc5de4.PNG)
  
4. 在 Exchange 系統管理中心中，按一下 [**權限**，和 [**系統管理角色**。
    
5. 在清單檢視中，選取 [**探索管理**，並按一下 [**編輯**![編輯圖示](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif)。
    
    ![將您新增至探索管理角色群組在 EAC 中](media/e5c98e93-d6a0-40c5-a143-bac956eedaa7.png)
  
6. 在**角色群組**中，[**成員**、 按一下 [**新增**![新增圖示](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)。
    
7. 在 [**選取成員]** 中，即可從清單中選取的名稱、 按一下 [**新增**] 和 [**確定]**。
    
    > [!NOTE]
    > 您也可以新增您是的例如組織管理或 TenantAdmins 成員的群組。如果您將群組新增其他群組的成員會指派執行就地 eDiscovery 工具的必要權限。 
  
8. 在**角色群組**中，按一下 [**儲存**]。
    
9. 不在 Office 365 登入。
    
    您必須登出您才能啟動下一個步驟如此新的權限才會生效。
    
> [!CAUTION]
> 探索管理角色群組的成員可存取機密訊息內容。這包括搜尋組織中所有信箱、 預覽搜尋結果 （和其他信箱項目）、 將結果複製到探索信箱，並將搜尋結果匯出至 PST 檔案。 
  
[回到頁首](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-2-search-the-users-mailbox-for-deleted-items"></a>步驟 2： 搜尋使用者的信箱已刪除的項目
<a name="step2"> </a>

當您執行就地 eDiscovery 搜尋時，搜尋信箱的可復原的項目資料夾自動隨附於搜尋。可復原的項目] 資料夾是永久刪除的項目儲存直到他們正在清除 （永久移除） 從信箱。因此，如果項目尚未清除，您應該能夠找到使用就地 eDiscovery 工具。
  
1. 使用工作或學校帳戶[登入 Office 365 企業版的位置](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4)。 
    
2. 選取 [應用程式啟動器圖示![Office 365 中的應用程式啟動器圖示](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png)中左上角按一下 [**系統管理**。
    
3. 在 Office 365 系統管理中心的左方導覽，依序展開 [**系統**] 和 [ **Exchange**。
    
4. 在 Exchange 系統管理中心中，依序按一下 [**規範管理**、**就地 eDiscovery&amp;保留**，然後按一下 [**新增**![新增圖示](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)。
    
    ![在 EAC 中，在 [規範管理] 頁面上按一下 [就地 eDiscovery 和保留](media/9d9ff0f5-b9be-45b8-8b5e-6037a856b0a8.png)
  
5. 在 [**名稱與描述**] 頁面上輸入的名稱 （例如您要復原的電子郵件的使用者名稱） 搜尋、 選擇性描述，以及然後按 [**下一步**。
    
6. 在 [**信箱**] 頁面上 [**搜尋指定信箱**] 和 [**新增**![新增圖示](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)。
    
    ![按一下 [指定信箱搜尋報的信箱搜尋](media/83879a40-5e5c-49a8-be3b-c0023d197588.png)
  
7. 尋找並選取您要復原已刪除的電子郵件的使用者名稱、 按一下 [**新增**]，然後按一下 [**確定]**。
    
8. 按 [下一步]。
    
    會顯示 [**搜尋查詢**] 頁面。這是用來定義可協助您尋找遺失的項目在使用者的信箱中的搜尋準則。 
    
9. 在 [**搜尋查詢**] 頁面上完成下列欄位： 
    
  - **包含的所有內容**選取此選項可在使用者的信箱搜尋結果中包含的所有內容。如果您選取這個選項，您無法指定其他搜尋準則。 
    
  - **篩選依據準則**選取此選項可指定搜尋準則，包含關鍵字、 開始時間和結束日期、 寄件者和收件者的地址和訊息類型。 
    
    ![建立根據例如關鍵字、 日期範圍、 收件者] 和訊息類型的準則搜尋](media/ee47b833-9122-46a0-85e6-fcbe25be0dd5.png)
  
|**欄位**|**使用此選項，即可...]**|
|:-----|:-----|
|![粉紅色圓形中的號碼 1](media/a4da261d-2516-48c5-b58a-9c452b9086b8.png)           <br/> |指定的關鍵字、 日期範圍、 收件者及訊息類型。  <br/> |
|![數個粉紅色圓形有兩個字。](media/de3c1ab4-4f01-4026-b1ba-3265bdb32a89.png)           <br/> |搜尋郵件關鍵字或關鍵詞，並使用如**AND**或**OR**邏輯運算子。  <br/> |
|![數字三粉紅色圓形中。](media/60fa378c-6ac1-4cbd-a782-2fa7ca619dc6.png)           <br/> |搜尋傳送或接收的日期範圍內的郵件。  <br/> |
|![數字 4 粉紅色圓形中。](media/1a0ff2ce-0942-405a-94e3-9bfeb1e5059e.png)           <br/> |搜尋郵件從接收或傳送給特定的人。  <br/> |
|![編號的粉紅色圓形 5。](media/878cc815-0165-49ba-a1ee-9236e5980403.png)           <br/> |搜尋的所有郵件類型或選取特定的錯誤。  <br/> |
   
    > [!TIP]
    >  Here's a few tips about how to build a search query to find missing items. Try to get as much information from the user to help you create a search query so you can find what you're looking for. >  If you not sure how to find a missing message, consider using the **Include all content** option. The search results will include all items in the user's Recoverable Items folder, including the hidden folder (called the Purges folder) that contain items that have been purged by the user. Then you can go to Step 3, copy the results to a discovery mailbox, and look at the message in the hidden folder. >  If you know approximately when the missing message was originally sent or received by the user, use the **Specify start date** and **Specify end date** options to provide a date range. This will return all messages sent or received by the user within that date range. Specifying a date range is a really good way to narrow the search results. >  If you know who sent the missing email, use the **From** box to specify this sender. >  If you want to narrow the search results to different types of mailbox items, click **Select message types**, click **Select the message types to search**, and then choose a specific message type to search for. For example, you can search only for calendar items or contacts. Here's a screenshot of the different message types you can search for; the default is to search for all message types. 
  
    Click **Next** when you've completed the **Search query** page. 
    
10. **就地保留設定**] 頁面上按一下 [**完成**] 以啟動搜尋]。若要復原已刪除的電子郵件，沒有使用者的信箱置於保留理由。 
    
    在您開始搜尋之後，Exchange 會顯示的估計項目總大小和根據您指定的準則搜尋將傳回的項目數。
    
11. 選取您剛建立的搜尋並按一下 [**重新整理**![重新整理](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png)要更新的詳細資料窗格中顯示的資訊。**評估順利完成**狀態表示已完成搜尋。Exchange 也會顯示評估會有項目 （和其大小） 根據您在步驟 9 中指定的搜尋準則搜尋所找到的總數。 
    
12. 在 [詳細資料] 窗格中，按一下 [**預覽搜尋結果**來檢視所找到的項目。這可能會協助您識別您要尋找的項目。如果您尋找您嘗試復原的項目，請前往步驟 4 至搜尋結果匯出至 PST 檔案。 
    
    ![按一下 [檢視您嘗試復原的項目預覽搜尋結果](media/a2cea921-dafa-45d6-97d4-ae45a226b8d3.png)
  
13. 如果您找不到您要尋找項目，您可以修改您的搜尋準則選取 [搜尋] 按一下 [**編輯**![編輯圖示](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif)，然後按一下 [**搜尋查詢**。變更的搜尋準則，然後重新執行搜尋。
    
[回到頁首](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="optional-step-3-copy-the-search-results-to-a-discovery-mailbox"></a>（選用）步驟 3： 將搜尋結果複製到探索信箱
<a name="step3"> </a>

如果您找不到項目來預覽搜尋結果或您想要查看使用者的 [可復原的項目] 資料夾中有哪些項目，然後您可以將搜尋結果複製到特殊信箱 （稱為 「 探索信箱），然後 t 在 web 上的 Outlook 中開啟該信箱o 檢視實際的項目。複製搜尋結果的最佳原因會讓您可以檢視使用者的 [可復原的項目] 資料夾中的項目。多個有可能您嘗試復原的項目位於清除子資料夾中。 
  
1. 在 Exchange 系統管理中心，移至 [**相符性管理** \> **就地 eDiscovery&amp;保留**。
    
2. 在 [搜尋] 清單中選取您在步驟 2 中建立的搜尋。
    
3. 按一下 [**搜尋**]![搜尋](media/c94e8591-7044-4650-a0d1-c57c0633ab4f.png)，然後從下拉式清單中按一下 [**複製搜尋結果**。 
    
    ![按一下 [搜尋] 和 [複製搜尋結果](media/7888df82-94b4-4e44-8a53-f66854dc7c86.png)
  
4. 在**複製搜尋結果**] 頁面上，按一下 [**瀏覽**]。
    
    ![保留未選取時復原刪除的項目] 核取方塊](media/37f27999-a5b2-4fed-87e2-bad6dc23cdae.png)
  
5. **顯示名稱**] 下按一下 [**探索搜尋信箱**，並再按一下 [**確定]**。
    
    ![將搜尋結果複製到預設的探索搜尋信箱](media/36e8ef47-0035-4982-9ed6-426719c5f9ec.png)
  
    > [!NOTE]
    > [探索搜尋信箱會自動建立 Office 365 組織中的預設探索信箱。 
  
6. 在**複製搜尋結果**] 頁面上，按一下 [**複製**到啟動程序來將搜尋結果複製到 [探索搜尋信箱]。 
    
    ![按一下 [複製到搜尋結果複製到 [探索搜尋信箱](media/71307a9d-f7a1-4e01-ae37-1d49040cc3fd.png)
  
7. 按一下 [**重新整理**![重新整理](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png)來更新顯示在 [詳細資料] 窗格中的複製狀態的相關資訊。 
    
8. 複製完成後，請按一下 [開啟探索搜尋信箱來檢視搜尋結果的 [**開啟**]。 
    
    ![按一下 [開啟] 以移至要檢視搜尋結果的探索搜尋信箱](media/6cc81e0f-ceed-4464-9040-79b6f920de35.png)
  
    搜尋結果複製到 [探索搜尋信箱會放在具有相同名稱為 「 就地 eDiscovery 搜尋的資料夾中。您可以按一下 [顯示資料夾中的項目] 資料夾。
    
    ![在 [探索搜尋信箱 ； 搜尋結果[清除] 資料夾中的項目僅可復原的系統管理員](media/2ef8e5fb-3e63-4f62-938e-307efe9f6998.gif)
  
    當您執行搜尋時，也會搜尋使用者的 [可復原的項目] 資料夾。這表示如果可復原的項目] 資料夾中的項目符合搜尋準則，其內含搜尋結果中。在 [刪除] 資料夾中項目是使用者永久刪除 （從 [刪除郵件] 資料夾刪除項目或選取它，並按下**Shift + Delete**項目。使用者可以使用 Outlook 或 Outlook web 上的復原刪除的郵件工具復原刪除資料夾中的項目。[清除] 資料夾中的項目是使用者使用復原刪除的郵件工具將清除的項目或其已自動清除套用至信箱原則的項目。不論執行哪項中的系統管理員可以復原 [清除] 資料夾中的項目。 
    
    > [!TIP]
    > 如果使用者找不到使用可復原的項目工具、 刪除項目但仍可復原的項目 （亦即它尚未永久移除從信箱），它是以上可能位於 [清除] 資料夾。因此，請務必在您嘗試復原使用者的刪除項目清除資料夾中尋找。 
  
[回到頁首](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-4-export-the-search-results-to-a-pst-file"></a>步驟 4： 將搜尋結果匯出至 PST 檔
<a name="step4"> </a>

尋找您嘗試為使用者復原的項目之後下, 一步是匯出至 PST 檔案已執行步驟 2 中的搜尋結果。使用者將會使用此 PST 檔案在下一個步驟中的還原刪除的項目至其信箱。
  
1. 在 Exchange 系統管理中心，移至 [**相符性管理** \> **就地 eDiscovery&amp;保留**。
    
2. 在 [搜尋] 清單中選取您在步驟 2 中建立的搜尋。
    
3. 按一下 [**匯出至 PST 檔案**。
    
    ![按一下 [匯出至 PST 檔](media/4e59ae17-4541-43f4-a6d1-1f8b9ba9404b.png)
  
4. 如果系統提示您安裝 eDiscovery 匯出工具，請按一下 [**執行**]。
    
5. 在 [eDiscovery PST 匯出工具中，按一下 [**瀏覽]** 以指定您要下載 PST 檔案的位置。 
    
    ![EDiscovery PST 匯出工具](media/17274d27-992e-4034-8133-8f793f554e6c.png)
  
    您可以略過選項以啟用 deduplication 及包含無法搜尋的項目。
    
6. 按一下 [**開始**PST 檔案下載到您的電腦。 
    
    **EDiscovery PST 匯出工具**會顯示匯出程序的狀態資訊。在匯出完成時，您可以存取下載位置的位置中的檔案。 
    
[回到頁首](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-5-restore-the-recovered-items-to-the-users-mailbox"></a>步驟 5： 還原至使用者的信箱已復原的項目
<a name="step5"> </a>

最後一個步驟是使用在步驟 4 到使用者的信箱還原已復原的項目已匯出的 PST 檔案。您傳送給使用者的 PST 檔案之後，此步驟的其餘部分是由使用者開啟 PST 檔案，然後再將已復原的項目移至另一個資料夾信箱中執行。如需逐步說明，您也可以傳送使用者連結至本主題：[開啟及關閉 Outlook 資料檔 (.pst)](https://support.office.com/article/381b776d-7511-45a0-953a-0935c79d24f2)。或您可以使用者連結傳送[還原刪除的信箱使用 PST 檔案的項目](recover-deleted-items-in-a-mailbox.md#restoredeleteditems)] 區段下，他可執行這些步驟。 
  
 **將 PST 檔案傳送給使用者**
  
您必須執行的最後一個步驟在步驟 4 中傳送已匯出的 PST 檔案給使用者。有幾種執行這項作業：
  
- 附加至電子郵件訊息的 PST 檔案。如果 Outlook 設定為封鎖 PST 檔案，您會擁有 zip 檔案並再將它附加到郵件。以下是如何：
    
1. 在 Windows 檔案總管或檔案總管] 中，瀏覽至 PST 檔案。
    
2. 以滑鼠右鍵按一下檔案，然後選取 [**傳送至** \> **Compressed (zip) 的資料夾**。Windows 會建立新的 zip 檔案，並為其為 PST 檔案的相同名稱。
    
3. 附加至電子郵件訊息的壓縮的 PST 檔案並將其傳送給使用者，然後按一下滑鼠左鍵來解壓縮的檔案。
    
- 將 PST 檔案複製到使用者可以存取並擷取它的共用資料夾。
    
還原刪除的項目至其信箱之使用者所執行的下一步] 區段中的步驟。
  
 **若要使用 PST 檔案的信箱還原刪除的項目**
  
您必須使用 Outlook 桌面應用程式使用 PST 檔案還原已刪除的項目。您無法使用 Outlook Web App 或 Outlook web 上的開啟 PST 檔案。
  
1. 在 Outlook 2013 或 Outlook 2016 中，按一下 [**檔案**] 索引標籤。 
    
2. 按一下 [**開啟&amp;匯出**，然後按一下 [**開啟 Outlook 資料檔案**。
    
3. 瀏覽至您儲存您的系統管理員傳送 PST 檔案的位置。
    
4. 選取 PST，然後按一下 [**開啟**。
    
    PST 檔案會出現在 Outlook 中的左巡覽列。
    
    ![PST 檔案會出現在 Outlook 中的左巡覽列](media/c9389392-d08a-4aa7-848c-4986d448b0f2.png)
  
5. 按一下箭頭以展開 [PST 檔案及資料夾下它找到您想要復原的項目。
    
    ![在您想要復原的項目清除資料夾中尋找](media/d4e372d9-ac23-4e95-8639-d8da690fefa7.png)
  
    > [!TIP]
    > 尋找您想要復原的項目清除資料夾中。這是隱藏的資料夾清除的項目移到。可能是您復原的系統管理員會在此資料夾中的項目。 
  
6. 以滑鼠右鍵按一下您想要復原，然後按一下 [**移動**項的目\>**其他資料夾**。
    
    ![按一下 [移動，然後選取 [其他] 資料夾](media/090063df-2aa0-444a-8e47-abd6fe6cf7a8.png)
  
7. 若要將項目移至 [收件匣，請按一下 [**收件匣**，然後按一下 [**確定]**。
    
    **提示：** 若要復原其他類型的項目，執行下列其中一項： 
    
  - 若要復原的行事曆項目，以滑鼠右鍵按一下，] 和 [**移動** \> **其他資料夾** \> **行事曆**。
    
  - 若要復原連絡人，以滑鼠右鍵按一下，] 和 [**移動** \> **其他資料夾** \> **連絡人**。
    
  - 若要復原工作，以滑鼠右鍵按一下，] 和 [**移動** \> **其他資料夾** \> **工作**。
    
![選取要移動其他類型的項目資料夾](media/f8290131-43f2-46f1-bc07-228c2d83b96c.png)
  
    Note that calendar items, contacts, and tasks are located directly in the Purges folder, and not in a Calendar, Contacts, or Tasks subfolder. However, you can sort by **Type** to group similar types of items. 
    
8. 完成作業後復原刪除的項目，以滑鼠右鍵按一下左巡覽列並選取 [**關閉"PST 檔案的名稱"** 的 PST 檔案。
    
[回到頁首](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="more-information"></a>其他資訊
<a name="moreinfo"> </a>

- 您可能可能復原永久刪除的項目如果尚未過期的項目已刪除的項目保留期間的使用者。為您可能需要的系統管理員可復原的項目] 資料夾中的指定時間項目可用來復原。例如，可能會有已在 30 天內，使用者的已刪除的項目] 資料夾刪除任何項目的原則和其他原則，可讓使用者復原至另一個 14 天的可復原的項目資料夾中的項目。不過，此的 14 天後您可能仍能復原使用者的信箱中的項目使用本主題中的程序。
    
- 如果尚未被清除，如果尚未過期的項目已刪除的項目保留期間的使用者可以復原刪除的項目。若要可協助使用者復原已刪除的信箱中的項目，其指向其中一個下列主題：
    
  - [在 Windows 版 Outlook 復原已刪除的項目](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
    
  - [Outlook 2010 中復原刪除的郵件](https://support.office.com/article/cd9dfe12-8e8c-4a21-bbbf-4bd103a3f1fe)
    
  - [復原 Outlook Web App 中刪除的郵件或電子郵件](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
    
  - [在網路上的 Outlook 中還原已刪除電子郵件](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
    
  - [復原已刪除的連絡人中的 Outlook](https://support.office.com/article/51c83288-6888-4dcd-8c99-4932daabf643)
    
  - [在 Outlook.com 中還原已刪除電子郵件](https://go.microsoft.com/fwlink/p/?LinkID=623435)
    
[回到頁首](recover-deleted-items-in-a-mailbox.md#__top)
  

