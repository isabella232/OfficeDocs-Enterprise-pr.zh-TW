---
title: 在 Office 365 同時新增多個使用者 - 系統管理協助
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365P_AddUsersCSV
- O365M_AddUsersCSV
- O365E_AddUsersCSV
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOP150
- MOE150
- MED150
- GMA150
- MBS150
- GEA150
- BCS160
ms.assetid: 1f5767ed-e717-4f24-969c-6ea9d412ca88
description: '了解如何新增多位使用者至 Office 365 商務從清單中的試算表或其他 CSV 格式的檔案。 請觀看上說明如何將帳戶新增至 Office 365 的 YouTube 影片。 在此程序結束時，每位使用者的帳戶必須是 Office 365 信箱。 '
ms.openlocfilehash: 1f91821ee552b59201ca01bdbce7edc0406929d6
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491484"
---
# <a name="add-several-users-at-the-same-time-to-office-365---admin-help"></a>在 Office 365 同時新增多位使用者 - 系統管理說明

小組每一個人都需要使用者帳戶，才能登入並存取 Office 365 服務 (例如電子郵件和 Office)。如果您有許多工作人員，您可以從 Excel 試算表或其他以 CSV 格式儲存的檔案，一鼓作氣新增全部的帳戶。[不確定 CSV 檔案是什麼嗎？](add-several-users-at-the-same-time.md#__toc316652088)
  
## <a name="add-multiple-users-to-office-365-in-the-office-365-admin-center"></a>在 Office 365 系統管理中心新增多個使用者至 Office 365

1. 以公司或學校帳戶登入 Office 365。 
    
2. 在 Office 365 系統管理中心中，選擇 [**使用者** \> **作用中的使用者**。
    
    ![In the Admin center choose Users and then Active users](media/12086d98-a8b4-4c48-89cf-b78ad8058ff1.png)
  
3. 在**多個**下拉式清單，選擇 [**匯入多個使用者**。
    
4. 在**匯入多個使用者**] 面板中，您可以選擇性地下載包含或不含範例資料填入範例 CSV 檔案。 
    
    ![In the More drop-down, choose Import multiple users](media/77df8a4a-fd00-4fbe-bf1c-d234fc1d5e93.png)
  
    試算表必須包含一個範例在**完全相同的資料行標題**(使用者名稱、 名字、 等等。..)。如果您使用的範本，在文字編輯工具，例如 [記事本] 中開啟，並且考慮留言來說，第 1 列的所有資料和資料列 2 中，以下只輸入資料。 
    
    您的試算表也必須包含使用者名稱 (例如 bob@contoso.com) 與每個使用者的顯示名稱 (例如「柯百勝」) 這兩個值。 
    
  ```
  User Name,First Name,Last Name,Display Name,Job Title,Department,Office Number,Office Phone,Mobile Phone,Fax,Address,City,State or Province,ZIP or Postal Code,Country or Region
  chris@contoso.com,Chris,Green,Chris Green,IT Manager,Information Technology,123451,123-555-1211,123-555-6641,123-555-9821,1 Microsoft way,Redmond,Wa,98052,United States
  ben@contoso.com,Ben,Andrews,Ben Andrews,IT Manager,Information Technology,123452,123-555-1212,123-555-6642,123-555-9822,1 Microsoft way,Redmond,Wa,98052,United States
  david@contoso.com,David,Longmuir,David Longmuir,IT Manager,Information Technology,123453,123-555-1213,123-555-6643,123-555-9823,1 Microsoft way,Redmond,Wa,98052,United States
  cynthia@contoso.com,Cynthia,Carey,Cynthia Carey,IT Manager,Information Technology,123454,123-555-1214,123-555-6644,123-555-9824,1 Microsoft way,Redmond,Wa,98052,United States
  melissa@contoso.com,Melissa,MacBeth,Melissa MacBeth,IT Manager,Information Technology,123455,123-555-1215,123-555-6645,123-555-9825,1 Microsoft way,Redmond,Wa,98052,United States
  
  ```

5. 在方塊中，輸入檔案路徑，或選擇 [**瀏覽]** 以瀏覽至 CSV 檔案的位置，然後選擇 [**驗證**。
    
    ![Your CSV file is verified](media/a43d49db-b2ab-4200-8ddf-0bc846ac6fe5.png)
  
    如果檔案有任何問題，問題會顯示在面板中。您也可以下載記錄檔。
    
6. 在 [**設定使用者選項**] 對話方塊中，您可以設定登入狀態，並選擇將指派給所有使用者的產品授權。 
    
7. 在 [**檢視您的結果**] 對話方塊，您可以選擇將結果傳送給自己或其他使用者 （密碼會以純文字），您可以看到建立多少個使用者，而且如果您需要購買更多授權指派給新的使用者部分。 
    
## <a name="watch-the-video"></a>觀看影片
<a name="bk_preview"> </a>

 觀看短片以了解如何大量新增使用者。 
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/f4e7f161-8ae6-4264-a429-9297b539a8de?autoplay=false]
  
## <a name="next-steps"></a>後續步驟
<a name="bk_preview"> </a>

- 現在這些人員都擁有帳戶，他們必須[下載並安裝或重新安裝 Office 365 或 Office 2016 在 PC 或 Mac 上](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658)。 您小組內的每位人員最多可以在 5 部 PC 或 Mac 上安裝 Office 365。 
    
- 每位人員也可以[設定 Office app 和行動裝置上的電子郵件](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f)上最多 5 台平板電腦和 5 支電話，例如 Iphone、 Ipad 及 Android 手機和平板電腦。 他們可利用這種方式，從任何地點編輯 Office 檔案。 
    
    設定步驟的端對端清單，請參閱[設定商務用 Office 365](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) 。 
    
## <a name="more-information-about-how-to-add-users-to-office-365"></a>如何新增使用者至 Office 365 的詳細資訊
<a name="bk_preview"> </a>

### <a name="not-sure-what-csv-format-is"></a>不確定 CSV 檔案是什麼嗎？
<a name="__toc316652088"> </a>

CSV 檔案是以逗號區分值的檔案。您可以用任何文字編輯器或試算表程式 (例如 Excel) 來建立或編輯這樣的檔案。
  
您可以從下載[這份樣本試算表](https://www.microsoft.com/en-us/download/details.aspx?id=45485)開始著手。記住，Office 365 規定第一列必須是欄標題，切勿將它換成其他內容。 
  
接著請以新名稱儲存檔案，然後指定 CSV 格式。
  
![說明如何在 Excel 中將檔案儲存為 CSV 格式的圖像](media/35a86ebe-63ab-4b4d-9a92-e177de33ebae.png)
  
儲存檔案時，系統會提示您若儲存為 CSV 格式，將遺失部分活頁簿中的功能。 這沒有關係。 請按一下 [是]**** 繼續。 
  
![Excel 可能會向您顯示的提示圖片，Excel 會詢問您是否真的要將檔案儲存為 CSV 格式](media/51032a81-690c-45ef-bfc5-09ea7f790e98.png)
  
### <a name="tips-for-formatting-your-spreadsheet"></a>格式化試算表的祕訣
<a name="__toc314595848"> </a>

- **欄標題必須與樣本試算表中的欄標題一樣嗎？** 是的。 樣本試算表的第一列是欄標題。 這些標題不能省略。 請針對您要在 Office 365 新增的每一位使用者，在標題下方各建立一列。 如果您新增、變更或刪除任何欄標題，Office 365 可能就無法根據檔案中的資訊建立使用者。 
    
- **若我沒有各使用者的必要資訊會怎麼樣？** 使用者名稱和顯示名稱是必要資訊，缺少的話無法新增新使用者。 若您缺少部分其他資訊 (例如傳真)，可使用空格加上逗號表示此欄位應保留空白。 
    
- * * 如何小型或大型試算表可以？ * * 試算表必須至少兩個資料列。 一列是欄標題 (使用者資料欄標籤)，另一列是使用者。 列數不得超過 251 列。 如果您必須匯入超過 250 位使用者，可以建立多份試算表。 
    
- * * 可以使用哪些語言？ * * 當您建立您的試算表時，您可以輸入使用者的資料欄標籤中的任何語言或字元，但就不得變更之標籤的順序，如範例所示。 接著您可以使用任何語言或字元將項目填入欄位內，並將檔案儲存為 Unicode 或 UTF-8 格式。 
    
- **如果我要新增來自不同國家或地區的使用者，該怎麼做？** 請為每一個地區分別建立一個試算表。 每一個試算表都要執行 [大量新增使用者精靈] 的所有步驟，讓您所用的檔案中，所有的使用者都具備單一位置。 
    
- **我能使用的字元數是否有所限制？** 下表所列的是範例試算表中各使用者資料欄標籤及其字元數上限。 
    
|**使用者 資料 欄 標籤**|**字元數上限**|
|:-----|:-----|
|使用者 名稱 (必填)  <br/> |79 (包含 @ 符號，格式為 name@domain.\<extension\>)。使用者別名不得超過 30 個字元，網域名稱不得超過 48 個字元。  <br/> |
|名字  <br/> |64  <br/> |
|姓氏  <br/> |64  <br/> |
|顯示 名稱 (必填)  <br/> |256  <br/> |
|職稱  <br/> |64  <br/> |
|部門  <br/> |64  <br/> |
|辦公室號碼  <br/> |128  <br/> |
|辦公室電話  <br/> |64  <br/> |
|行動電話  <br/> |64  <br/> |
|傳真  <br/> |64  <br/> |
|地址  <br/> |1023  <br/> |
|城市  <br/> |128  <br/> |
|省/市  <br/> |128  <br/> |
|郵遞區號  <br/> |40  <br/> |
|國家/地區  <br/> |128  <br/> |
   
### <a name="still-having-problems-when-adding-users-to-office-365"></a>仍有在 Office 365 新增使用者的問題嗎？

- **重複檢查試算表格式是否正確。** 檢查欄標題，確認與樣本檔案中的標題相符。 務必遵循字元長度的規則，各欄位均以逗號隔開。 
    
- * * 如果您沒有立刻看到 Office 365 中新的使用者，請稍候幾分鐘的時間。 * * 可能會花費一點的前往 Office 365 中的所有服務的變更。 
    
## <a name="add-multiple-users-to-office-365-in-the-old-office-365-admin-center"></a>在舊版 Office 365 系統管理中心新增多位使用者至 Office 365

1. 下載[此範例試算表](https://www.microsoft.com/en-us/download/details.aspx?id=45485)，並在 Excel 中開啟。 
    
    試算表必須包含一個範例在**完全相同的資料行標題**(使用者名稱、 名字、 等等。..)。如果您使用的範本，請考慮留言來說，第 1 列的所有資料和資料列 2 中，以下只輸入資料。 
    
    您的試算表也必須包含使用者名稱 (例如 bob@contoso.com) 與每個使用者的顯示名稱 (例如「柯百勝」) 這兩個值。若要將其他欄位留白，請在欄位中輸入一個空白和一個逗號，如下圖所示。 
    
    ![指定空白列的範例 CVS 檔案](media/9c596ba1-1053-4687-a46c-c9359e9818c9.png)
  
    如果您有工作人員在不同國家工作，您必須為每一個國家/地區的使用者分別建立一份試算表。例如，一份試算表列出在美國工作的所有工作人員，另一份試算表列出在日本工作的所有工作人員。這是因為每一個地區可用的 Office 365 服務都不盡相同。 
    
    **提示：** 您將多位使用者新增至 Office 365 之前，您可能要與範例試算表的作法。 例如，編輯一份含有部分 (假設 5 或 10 個人) 使用者資料的範例試算表，並以新名稱儲存檔案。 接著逐一執行此程序所述的步驟、檢查結果，然後刪除新帳戶，再從頭開始。 您可使用這個方式，練習將所有資料整理為適合您的狀況。 另外也請參閱[格式化試算表的祕訣](add-several-users-at-the-same-time.md#__toc314595848)。
    
2. 以公司或學校帳戶登入 Office 365。 
    
3. 移至 Office 365 系統管理員中心。
    
4. 對於使用 Office 365 服務的使用者，必須先指派授權給他們。 不過您必須先檢查您是否足夠的授權，可以指派給試算表所列的所有人。 選擇 [**計費** \> **訂用帳戶**]，查看是否您有足夠的授權。 如果您需要購買更多授權，選擇 [* * 變更授權數量 * *。 您可以先執行精靈，指派現有的授權，日後再另外購買其他授權，然後重新執行精靈。 
    
5. 現在移至 [大量新增使用者] 精靈： 選擇 [**使用者**] \> **作用中的使用者**。 選擇 [![新增多位使用者至 Office 365 的圖示](media/3481ffea-d552-4a7f-9a3b-014504e69746.png)，如下圖所示。 
    
    ![Office 365 系統管理中心 [使用者] 區段的圖像](media/2cd5ff86-9c0b-438e-9bb9-13b12a2675de.png)
  
    隨後便會出現 [大量新增使用者] 精靈，逐步引導您在 Office 365 新增一組使用者。 
    
6. 步驟 1 - 選取 CSV 檔案，指定您自己的試算表，如下圖所示。
    
    ![[大量新增使用者] 精靈步驟 1 - 選取 CSV 檔案](media/aeb837ed-1f86-427d-b038-c643c383829c.png)
  
7. 步驟 2 - 驗證，精靈會告訴您試算表中的內容格式是否正確。
    
    ![[大量新增使用者] 精靈步驟 2 - 驗證](media/3fd3cd2c-44d4-4593-b02c-b87c176affb3.png)
  
8. 步驟 3-設定，選擇 [**允許**]，讓您試算表中所列的人員可以使用 Office 365。 另外也請選擇這些人會使用 Office 365 的國家/地區。 請記住，如果組織中的某些人要在其他國家使用 Office 365，請以他們的名稱另外建立一份試算表，然後再次執行 [大量新增使用者] 精靈，新增他們。 
    
    ![[大量新增使用者] 精靈步驟 3 - 設定](media/ff12ad34-5d8b-4e89-a02f-d827a94095b3.png)
  
9. [指派授權] 頁面會告訴您有多少授權可用。 
    
    ![[大量新增使用者] 精靈步驟 4 - 授權](media/161ea34c-c67e-43be-962f-029f5426ff1b.png)
  
    您可以選擇 [**購買更多授權**，但您就會離開 [大量新增使用者] 精靈，然後移至 Office 365 系統管理中心 **] [帳單**。 在購買更多授權後，您必須等待幾分鐘的時間處理訂單，然後從頭開始執行 [大量新增使用者] 精靈。 
    
    如果沒有另外購買其他授權，就不會針對試算表所列的每一個人建立帳戶。 
    
    在這個範例當中，我們不會購買其他任何授權，因此繼續執行 [大量新增使用者] 精靈。
    
10. In Step 5 - Send Results, type the email addresses of the people who you want to get an email that lists  *all*  of the Office 365 user names and temporary passwords for the people in the spreadsheet. 
    
    ![[大量新增使用者] 精靈步驟 5 - 傳送結果](media/5beeb825-4ba7-4ae0-bfb5-a1f8a785ebdb.png)
  
    下面這封電子郵件會傳送到您在步驟 5「傳送結果」所指定的所有電子郵件地址。這封電子郵件會指出已經建立的帳戶。請注意，有些人沒有建立帳戶，是因為他們沒有足夠的授權。 
    
    ![含使用者認證資訊的範例電子郵件](media/0a40c612-2078-4b5b-813e-f99bc53635a6.png)
  
    您可以日後再購買更多授權，並以同一份試算表重新執行 [大量新增使用者] 精靈。精靈會略過已經擁有帳戶的使用者；在結果報告中說明「重複的使用者名稱」，指出已擁有帳戶的人員資訊。
    
11. [大量新增使用者] 精靈的最後一頁會列出使用者名稱和臨時密碼，如下圖所示。
    
    ![[大量新增使用者] 精靈步驟 6 - 傳送結果](media/0cd43832-071b-4b33-b57a-5d07959985ad.png)
  
12. 待您在 Office 365 新增使用者之後，必須告訴這些使用者他們的 Office 365 帳戶資訊。請以正常程序傳達新密碼。
    

