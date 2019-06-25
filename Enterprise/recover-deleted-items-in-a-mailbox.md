---
title: 復原使用者信箱中刪除的郵件 - 系統管理說明
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 6/29/2018
audience: Admin
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
description: '本文適用於系統管理員。 使用者是否永久刪除其 Outlook 信箱中的專案？ 使用者想要回復但無法復原。 如果已清除的專案尚未從使用者的信箱中永久移除, 您可能會將它們復原。 '
ms.openlocfilehash: d4be48d6166d970572dd1cb343ccd83f22330e12
ms.sourcegitcommit: b4c82c0bf61f50386e534ad23479b5cf84f4e2ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2019
ms.locfileid: "35203652"
---
<a name="__top"></a>
# <a name="recover-deleted-items-in-a-user-mailbox---admin-help"></a>復原使用者信箱中刪除的郵件 - 系統管理說明

**本文適用于系統管理員。您是否嘗試復原您自己信箱中已刪除的郵件？** 請嘗試下列其中一項:
- [在 Windows 版 Outlook 復原已刪除的項目](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
- [復原 Outlook Web App 中刪除的郵件或電子郵件](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
- [在網頁版 Outlook 中還原已刪除的電子郵件](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
- [Outlook.com](https://go.microsoft.com/fwlink/p/?LinkID=623435)
   
使用者是否永久刪除其 Outlook 信箱中的專案？ 使用者想要回復但無法復原。 如果已清除的專案尚未從使用者的信箱中永久移除, 您可能會將它們復原。 您可以在 Exchange Online 中使用就地 eDiscovery 工具, 搜尋使用者信箱中已刪除的電子郵件和其他專案, 例如連絡人、行事曆約會及工作。 如果您發現已刪除的專案, 您可以將其匯出至 PST 檔案 (也稱為 Outlook 資料檔案), 使用者可以使用該檔案將專案還原回其信箱。
  
以下是復原使用者信箱中已刪除郵件的步驟。 這會花費多久時間？ 第一次可能需要20或30分鐘, 以完成所有步驟, 視您嘗試復原的專案數而定。
  
> [!NOTE]
> 您必須是 Office 365 中的**Exchange 系統管理員**或**全域系統管理員**, 或是 Exchange Online 中的組織管理角色群組的成員, 才可執行本文中的步驟。 如需詳細資訊，請參閱[關於 Office 365 系統管理員角色](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d)。 
  
## <a name="step-1-assign-yourself-ediscovery-permissions"></a>步驟 1: 指派自己的 eDiscovery 許可權
<a name="step1"> </a>

第一步是在 Exchange Online 中為自己指派必要的許可權, 讓您可以使用就地 eDiscovery 工具來搜尋使用者的信箱。 您只需執行這項操作一次。 如果您必須在未來搜尋其他信箱, 您可以略過此步驟。
  
1. 找不到您要的 App 嗎？請從應用程式啟動器選取 [所有 App] 以查看依字母順序排序的可用 Office 365 App 清單。您可從該處搜尋特定的 App。 
    
2. 在左上方的 Office ![365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png)中選取應用程式啟動器圖示, 然後按一下 [**管理**]。
    
3. 在 Office 365 系統管理中心的左側導覽中, 展開 [系統**管理中心**], 然後按一下 [ **Exchange**]。
    
    ![系統管理中心清單](media/7d308eb7-ba63-4156-a845-3770facc5de4.PNG)
  
4. 在 Exchange 系統管理中心, 按一下 [**許可權**], 然後按一下 [**管理角色**]。
    
5. 在清單視圖中, 選取 [**探索管理**], 然後按一下 [**編輯**![編輯圖示](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif)]。
    
    ![將自己新增至 EAC 中的 [探索管理] 角色群組](media/e5c98e93-d6a0-40c5-a143-bac956eedaa7.png)
  
6. 在 **[角色群組**] 的 [**成員**] 下,](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)按一下 [**新增**![] 圖示。
    
7. 在 [**選取成員**] 中, 從名稱清單中選取您自己, 然後按一下 [**新增**], 然後按一下 **[確定]**。
    
    > [!NOTE]
    > 您也可以新增您是其成員的群組, 例如「組織管理」或「TenantAdmins」。 如果您新增群組, 將會為群組的其他成員指派執行就地 eDiscovery 工具所需的許可權。 
  
8. 在 [**角色群組**] 中, 按一下 [**儲存**]。
    
9. 登出 Office 365。
    
    您必須先登出, 才可開始下一個步驟, 讓新許可權生效。
    
> [!CAUTION]
> 探索管理角色群組的成員可存取機密訊息內容。 這包括搜尋組織中的所有信箱、預覽搜尋結果 (和其他信箱專案)、將結果複製到探索信箱, 以及將搜尋結果匯出至 PST 檔案。 
  
[回到頁首](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-2-search-the-users-mailbox-for-deleted-items"></a>步驟 2: 在使用者的信箱中搜尋刪除的專案
<a name="step2"> </a>

當您執行就地 eDiscovery 搜尋時, 您搜尋的信箱中的 [可復原的專案] 資料夾會自動包含在搜尋中。 [可復原的專案] 資料夾會儲存永久刪除的專案, 直到清除 (永久移除) 信箱為止。 因此, 如果專案尚未清除, 您應該可以使用就地 eDiscovery 工具來找到。
  
1. 找不到您要的 App 嗎？請從應用程式啟動器選取 [所有 App] 以查看依字母順序排序的可用 Office 365 App 清單。您可從該處搜尋特定的 App。 
    
2. 在左上方的 Office ![365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png)中選取應用程式啟動器圖示, 然後按一下 [**管理**]。
    
3. 在 Office 365 系統管理中心的左側導覽中, 展開 [**管理員**], 然後按一下 [ **Exchange**]。
    
4. 在 Exchange 系統管理中心中, 按一下 [**規範管理**], 按一下 [**就地&amp; eDiscovery 保留**], 然後按一下 [**新增**![] 圖示](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)。
    
    ![在 EAC 的 [規範管理] 頁面上, 按一下 [就地 eDiscovery 和保留]](media/9d9ff0f5-b9be-45b8-8b5e-6037a856b0a8.png)
  
5. 在 [**名稱與描述**] 頁面上, 輸入搜尋的名稱 (例如您要復原電子郵件的使用者名稱), 選擇性描述, 然後按 **[下一步]**。
    
6. 在 [**信箱**] 頁面上, 按一下 [**指定要搜尋的信箱**], 然後](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)按一下 [**新增**![] 圖示。
    
    ![按一下 [指定要搜尋的信箱] 搜尋 specifc 信箱](media/83879a40-5e5c-49a8-be3b-c0023d197588.png)
  
7. 尋找並選取您要復原已刪除電子郵件的使用者名稱, 然後按一下 [**新增**], 然後按一下 **[確定]**。
    
8. 按 [下一步]****。
    
    隨即會顯示 [**搜尋查詢**] 頁面。 您可以在這裡定義搜尋準則, 以協助您找出使用者信箱中遺失的專案。 
    
9. 在 [**搜尋查詢**] 頁面上, 完成下欄欄位: 
    
  - **包含所有內容**選取此選項可將使用者信箱中的所有內容包含在搜尋結果中。 如果選取這個選項，便無法指定其他搜尋準則。 
    
  - **根據準則篩選**選取此選項以指定搜尋準則, 包括關鍵字、開始與結束日期、寄件者和收件者位址, 以及郵件類型。 
    
    ![根據諸如關鍵字、日期範圍、收件者和郵件類型之類的準則建立搜索](media/ee47b833-9122-46a0-85e6-fcbe25be0dd5.png)
  
|**Field**|**使用此 .。。**|
|:-----|:-----|
|![粉紅色圓圈中的數字 1](media/a4da261d-2516-48c5-b58a-9c452b9086b8.png)           <br/> |指定關鍵字、日期範圍、收件者和郵件類型。  <br/> |
|![粉紅色圓圈中的數字 2。](media/de3c1ab4-4f01-4026-b1ba-3265bdb32a89.png)           <br/> |搜尋含有關鍵詞或片語的郵件, 並使用邏輯運算子 (例如**and**或**or**)。  <br/> |
|![粉紅色圓圈中的數字 3。](media/60fa378c-6ac1-4cbd-a782-2fa7ca619dc6.png)           <br/> |搜尋在日期範圍內傳送或接收的郵件。  <br/> |
|![粉紅色圓圈中的數字 4。](media/1a0ff2ce-0942-405a-94e3-9bfeb1e5059e.png)           <br/> |搜尋收到或傳送給特定人員的郵件。  <br/> |
|![粉紅色圓圈中的數位5。](media/878cc815-0165-49ba-a1ee-9236e5980403.png)           <br/> |搜尋所有郵件類型或選取特定的郵件類型。  <br/> |
   
    > [!TIP]
    >  Here's a few tips about how to build a search query to find missing items. Try to get as much information from the user to help you create a search query so you can find what you're looking for. >  If you not sure how to find a missing message, consider using the **Include all content** option. The search results will include all items in the user's Recoverable Items folder, including the hidden folder (called the Purges folder) that contain items that have been purged by the user. Then you can go to Step 3, copy the results to a discovery mailbox, and look at the message in the hidden folder. >  If you know approximately when the missing message was originally sent or received by the user, use the **Specify start date** and **Specify end date** options to provide a date range. This will return all messages sent or received by the user within that date range. Specifying a date range is a really good way to narrow the search results. >  If you know who sent the missing email, use the **From** box to specify this sender. >  If you want to narrow the search results to different types of mailbox items, click **Select message types**, click **Select the message types to search**, and then choose a specific message type to search for. For example, you can search only for calendar items or contacts. Here's a screenshot of the different message types you can search for; the default is to search for all message types. 
  
    Click **Next** when you've completed the **Search query** page. 
    
10. 在 [**就地保留設定**] 頁面上, 按一下 **[完成]** 以啟動搜尋。 若要復原已刪除的電子郵件, 沒有理由將使用者的信箱保留在暫止狀態。 
    
    開始搜尋之後, Exchange 會根據您指定的準則, 顯示搜尋所傳回的總大小和專案數。
    
11. 選取您剛建立的搜尋, 然後****![按一下 [](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png)重新整理重新整理] 以更新顯示在詳細資料窗格中的資訊。 [**評估成功**] 的狀態表示已完成搜尋。 Exchange 也會根據您在步驟9中指定的搜尋準則, 來顯示搜尋所找到的總專案數 (及其大小)。 
    
12. 在詳細資料窗格中, 按一下 [**預覽搜尋結果**] 以查看找到的專案。 這可能會協助您識別所要尋找的專案。 如果您發現要嘗試復原的專案, 請移至步驟 4, 將搜尋結果匯出至 PST 檔案。 
    
    ![按一下 [預覽搜尋結果] 以查看您要嘗試復原的專案](media/a2cea921-dafa-45d6-97d4-ae45a226b8d3.png)
  
13. 如果您找不到所要尋找的專案, 可以選取搜尋, 按一下 [**編輯**![編輯] 圖示](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif), 然後按一下 [**搜尋查詢**], 以修正您的搜尋準則。 變更搜尋準則, 然後重新執行搜尋。
    
[回到頁首](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="optional-step-3-copy-the-search-results-to-a-discovery-mailbox"></a>步驟步驟 3: 將搜尋結果複製到探索信箱
<a name="step3"> </a>

如果您無法透過預覽搜尋結果找到專案, 或想要查看使用者的 [可復原的專案] 資料夾中的專案, 則可以將搜尋結果複製到特殊信箱 (稱為探索信箱), 然後在 web 的 Outlook 中開啟該信箱o 查看實際專案。 複製搜尋結果的最佳原因是, 您可以在使用者的 [可復原的專案] 資料夾中查看專案。 您嘗試復原的專案可能會位於 [清除] 子資料夾中。 
  
1. 在 Exchange 系統管理中心, 移至 [**規範管理** \>就地**eDiscovery &amp;保留**]。
    
2. 在搜尋清單中, 選取您在步驟2中建立的搜尋。
    
3. 按一下****![[搜尋](media/c94e8591-7044-4650-a0d1-c57c0633ab4f.png)搜尋], 然後按一下下拉式清單中的 [**複製搜尋結果**]。 
    
    ![按一下 [搜尋], 然後按一下 [複製搜尋結果]。](media/7888df82-94b4-4e44-8a53-f66854dc7c86.png)
  
4. 在 [**複製搜尋結果**] 頁面上, 按一下 **[流覽]**。
    
    ![復原刪除的郵件時, 保持核取方塊為未選取狀態](media/37f27999-a5b2-4fed-87e2-bad6dc23cdae.png)
  
5. 在 [**顯示名稱**] 下, 按一下 [**探索搜尋信箱**], 然後按一下 **[確定]**。
    
    ![將搜尋結果複製到預設的探索搜尋信箱](media/36e8ef47-0035-4982-9ed6-426719c5f9ec.png)
  
    > [!NOTE]
    > 探索搜尋信箱是在您的 Office 365 組織中自動建立的預設探索信箱。 
  
6. 回到 [**複製搜尋結果**] 頁面上, 按一下 [**複製**] 以開始將搜尋結果複製到 [探索搜尋信箱] 的程式。 
    
    ![按一下 [複製], 將搜尋結果複製到探索搜尋信箱](media/71307a9d-f7a1-4e01-ae37-1d49040cc3fd.png)
  
7. 按一下 [重新](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png)整理重新整理] 以更新詳細資料窗格中所顯示之複製狀態的相關資訊。 **** ![ 
    
8. 當複製完成時, 按一下 [**開啟**] 以開啟 [探索搜尋] 信箱以查看搜尋結果。 
    
    ![按一下 [開啟] 以移至探索搜尋信箱以查看搜尋結果](media/6cc81e0f-ceed-4464-9040-79b6f920de35.png)
  
    複製到探索搜尋信箱的搜尋結果, 會放在與就地 eDiscovery 搜尋具有相同名稱的資料夾中。 您可以按一下資料夾, 以顯示該資料夾中的專案。
    
    ![搜尋搜尋信箱中的搜尋結果;[清除] 資料夾中的專案只能由系統管理員復原](media/2ef8e5fb-3e63-4f62-938e-307efe9f6998.gif)
  
    當您執行搜尋時, 也會搜尋使用者的 [可復原的專案] 資料夾。 這表示, 如果 [可復原的專案] 資料夾中的專案符合搜尋準則, 則會包含在搜尋結果中。 [刪除專案] 資料夾中的專案是指使用者會永久刪除的專案 (透過從 [刪除的郵件] 資料夾中刪除專案, 或選取並按下**Shift + Delete**即可)。 使用者可以使用 Outlook 或 Outlook 網頁版中的 [復原刪除的郵件] 工具, 復原 [刪除] 資料夾中的專案。 [清除] 資料夾中的專案是指使用者使用 [復原刪除的郵件] 工具清除的專案, 或已套用至信箱的原則所自動清除的專案。 在這兩種情況下, 只有系統管理員可以復原 [清除] 資料夾中的專案。 
    
    > [!TIP]
    > 如果使用者無法使用 [可復原的專案] 工具找到已刪除的專案, 但該專案仍可復原 (表示尚未從信箱中永久移除), 則它很可能是位於 [清除] 資料夾中。 因此, 請務必在 [清除] 資料夾中尋找您要為使用者復原的已刪除專案。 
  
[回到頁首](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-4-export-the-search-results-to-a-pst-file"></a>步驟 4: 將搜尋結果匯出至 PST 檔案
<a name="step4"> </a>

在您找到您要為使用者復原的專案之後, 下一步是從您在步驟2中執行的搜尋, 將結果匯出至 PST 檔案。 使用者會在下一個步驟中使用此 PST 檔案, 將刪除的專案還原至其信箱。
  
1. 在 Exchange 系統管理中心, 移至 [**規範管理** \>就地**eDiscovery &amp;保留**]。
    
2. 在搜尋清單中, 選取您在步驟2中建立的搜尋。
    
3. 按一下 [**匯出為 PST**檔案]。
    
    ![按一下 [匯出為 PST 檔案]](media/4e59ae17-4541-43f4-a6d1-1f8b9ba9404b.png)
  
4. 如果系統提示您安裝 eDiscovery 匯出工具, 請按一下 [**執行**]。
    
5. 在 [eDiscovery PST 匯出工具] 中, 按一下 **[流覽]** 以指定您要下載 PST 檔案的位置。 
    
    ![EDiscovery PST 匯出工具](media/17274d27-992e-4034-8133-8f793f554e6c.png)
  
    您可以忽略選項啟用重復資料刪除, 並包含無法搜尋的專案。
    
6. 按一下 [**開始**], 將 PST 檔案下載至您的電腦。 
    
    **EDISCOVERY PST 匯出工具**會顯示匯出程式的狀態資訊。 匯出完成時, 您可以在下載檔案的位置存取該檔案。 
    
[回到頁首](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-5-restore-the-recovered-items-to-the-users-mailbox"></a>步驟 5: 將復原的專案還原至使用者的信箱
<a name="step5"> </a>

最後一個步驟是使用在步驟4中匯出的 PST 檔案, 將復原的專案還原至使用者的信箱。 在您將 PST 檔案傳送給使用者之後, 這個步驟的其餘部分是由使用者執行, 以開啟 PST 檔案, 然後將復原的專案移至其信箱中的另一個資料夾。 如需逐步指示, 您也可以將本主題的連結傳送給使用者:[開啟和關閉 Outlook 資料檔案 (.pst)](https://support.office.com/article/381b776d-7511-45a0-953a-0935c79d24f2)。 或者, 您可以使用下面的 [PST 檔案] 區段, 將 [[還原已刪除的郵件](recover-deleted-items-in-a-mailbox.md#restoredeleteditems)] 連結傳送至信箱, 並要求他們執行這些步驟。 
  
 **將 PST 檔案傳送給使用者**
  
您需要執行的最後一個步驟是將在步驟4中匯出的 PST 檔案傳送給使用者。 有幾種方式可以這麼做:
  
- 將 PST 檔案附加到電子郵件。 如果 Outlook 設定為封鎖 PST 檔案, 您必須先壓縮該檔案, 然後將它附加至郵件。 方法如下：
    
1. 在 [Windows Explorer] 或 [檔案瀏覽器] 中, 流覽至 PST 檔案。
    
2. 以滑鼠右鍵按一下檔案, 然後選取 [**傳送至** \> **壓縮 (zipped) 資料夾**]。 Windows 會建立新的 zip 檔案, 並將其命名為與 PST 檔案相同的名稱。
    
3. 將壓縮的 PST 檔案附加到電子郵件, 並將其傳送給使用者, 然後按一下該檔案即可將檔案解壓縮。
    
- 將 PST 檔案複製到使用者可以存取及取得的共用資料夾。
    
下一節中的步驟是由使用者執行, 以將刪除的專案還原至其信箱。
  
 <a name="restoredeleteditems"></a>
**使用 PST 檔案將刪除的郵件還原至信箱**
  
您必須使用 Outlook 桌面應用程式, 以使用 PST 檔案還原已刪除的專案。 您不能在網頁上使用 Outlook Web App 或 Outlook 來開啟 PST 檔案。
  
1. 在 Outlook 2013 或 Outlook 2016 中, 按一下**** [檔案] 索引標籤。 
    
2. 按一下 **[ &amp;開啟匯出**], 然後按一下 [**開啟 Outlook 資料檔案**]。
    
3. 流覽至您儲存系統管理員傳送的 PST 檔案的位置。
    
4. 選取 PST, 然後按一下 [**開啟**]。
    
    PST 檔案會出現在 Outlook 的左巡覽列中。
    
    ![PST 檔案會出現在 Outlook 的左導覽列中](media/c9389392-d08a-4aa7-848c-4986d448b0f2.png)
  
5. 按一下箭頭以展開 PST 檔案及其下的資料夾, 以找出您想要復原的專案。
    
    ![在 [清除] 資料夾中, 尋找您要復原的專案](media/d4e372d9-ac23-4e95-8639-d8da690fefa7.png)
  
    > [!TIP]
    > 在 [清除] 資料夾中, 尋找您要復原的專案。 這是已清除專案移至的隱藏資料夾。 您的系統管理員可能會在此資料夾中復原您的專案。 
  
6. 以滑鼠右鍵按一下您要復原的專案, 然後按一下 [**移動** \> **其他資料夾**]。
    
    ![按一下 [移動], 然後選取 [其他資料夾]](media/090063df-2aa0-444a-8e47-abd6fe6cf7a8.png)
  
7. 若要將專案移到收件匣, 請按一下 [**收件**匣], 然後按一下 **[確定]**。
    
    **秘訣:** 若要復原其他類型的專案, 請執行下列其中一項操作: 
    
  - 若要復原行事曆專案, 請以滑鼠右鍵按一下它, 然後按一下 [**移動** \> **其他資料夾** \>行事**曆**]。
    
  - 若要復原連絡人, 請以滑鼠右鍵按一下該連絡人, 然後按一下 [**移動** \> **其他資料夾** \> **連絡人**]。
    
  - 若要復原任務, 請以滑鼠右鍵按一下它, 然後按一下 [**移動** \> **其他資料夾** \> **** 工作]。
    
![選取資料夾以移動其他類型的專案](media/f8290131-43f2-46f1-bc07-228c2d83b96c.png)
  
    Note that calendar items, contacts, and tasks are located directly in the Purges folder, and not in a Calendar, Contacts, or Tasks subfolder. However, you can sort by **Type** to group similar types of items. 
    
8. 當您已完成復原刪除的專案時, 請以滑鼠右鍵按一下左導覽列中的 PST 檔案, 然後選取 **[關閉] [pst 檔案名稱]**。
    
[回到頁首](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="more-information"></a>其他資訊
<a name="moreinfo"> </a>

- 如果專案的已刪除專案保留期間尚未過期, 則使用者可能會復原永久刪除的專案。 以系統管理員身分, 您可能會指定 [可復原的專案] 資料夾中的專案可用於復原的時間。 例如, 可能會有一項原則可刪除在使用者的 [刪除的郵件] 資料夾中有30天的任何專案, 以及可讓使用者將 [可復原的專案] 資料夾中的專案復原至其他14天的其他原則。 不過, 在這14天之後, 您可以使用本主題中的程式, 復原使用者信箱中的專案。
    
- 使用者可以復原已刪除的專案 (如果尚未清除), 以及該專案的已刪除專案保留期間尚未過期。 若要協助使用者復原其信箱中已刪除的郵件, 請指向下列其中一個主題:
    
  - [在 Windows 版 Outlook 復原已刪除的項目](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
    
  - [復原 Outlook 2010 中已刪除的專案](https://support.office.com/article/cd9dfe12-8e8c-4a21-bbbf-4bd103a3f1fe)
    
  - [復原 Outlook Web App 中刪除的郵件或電子郵件](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
    
  - [在網頁版 Outlook 中還原已刪除的電子郵件](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
    
  - [在 Outlook 中復原刪除的連絡人](https://support.office.com/article/51c83288-6888-4dcd-8c99-4932daabf643)
    
  - [還原 Outlook.com 中已刪除的電子郵件](https://go.microsoft.com/fwlink/p/?LinkID=623435)
    
[返回頁首](recover-deleted-items-in-a-mailbox.md#__top)
  

