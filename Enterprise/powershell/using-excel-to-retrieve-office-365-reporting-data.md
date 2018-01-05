---
title: "使用 Excel 擷取 Office 365 報表資料"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Office_Other
- PowerShell
ms.assetid: 510d5528-ac00-4f54-9d38-75fa043d0a06
description: "概要：使用 Microsoft Excel 中的 oData 功能，來擷取 Office 365 部署的詳細報告資訊。"
ms.openlocfilehash: 72c0fce0a70f5cc3136ab01b48bb178d32a8f64d
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="using-excel-to-retrieve-office-365-reporting-data"></a>使用 Excel 擷取 Office 365 報表資料

 **摘要：**使用 Microsoft Excel 中的 oData 功能，來擷取 Office 365 部署的詳細報告資訊。
  
報告是系統管理的重要部分。Office 365 系統管理中心包括幾個預先定義的報告，您可以從左方瀏覽區的 **報告**區段存取。有使用報告和安全性及規範符合性報告。
  
您所使用的 Office 365 版本以及已啟用哪些 Office 365 服務會決定您可以使用哪些報告。如需詳細資訊，請參閱[報告]((https://technet.microsoft.com/zh-TW/library/office-365-reports.aspx))頁面。
  
預先定義的系統管理中心報告是絕佳資源，可讓您輕鬆檢視信箱使用量，或使用者在線上會議待了多久時間等資訊。不過，若要對 Office 365 網域進行詳細分析，報告就會面臨一些限制。
  
有一個方法可解決這些限制，那就是使用 Windows PowerShell 或其他開發語言存取 Office 365 報告服務，並建立自訂報告，藉由自訂報告，您可以規定要從 Office 365 報告服務傳回哪些資料以及傳回的資料量。透過編寫自訂報告，您也可以指定如何排序和分類資料，以及該如何儲存資料 (若適用)，例如您可以將資料儲存為 XML 格式，或是儲存為可方便匯入 Excel 中使用的逗點分隔值格式。 
  
此外，自訂指令碼/應用程式可讓您存取 Office 365 系統管理中心未能提供的報告。例如，系統管理中心可以指出您有多少「過時」信箱，但無法指出在過去 30 天內沒有存取過的信箱。但自訂的 PowerShell 指令碼則可以提供這項資訊。總的來說，這表示雖然您必須撰寫簡短且相對簡單的小型 Windows PowerShell 指令碼，但卻能換得諸多彈性。
  
> [!VISUAL BASIC NOTE] 如需詳細資訊，請參閱 Office 365 報告服務的[首頁](https://msdn.microsoft.com/en-us/library/office/jj984325%28v=office.15%29.aspx)。
  
為了擷取這項資料，您必須撰寫某種程式碼。如果組織較為龐大，需要限制傳回的資訊數量和類型，這麼做很值得。但如果組織規模較小，並不需要限制傳回的資訊數量和類型，則您可以考慮從 Excel 本身開啟 Office 365 報告。
  
不過在此有一些限制，最主要的一個限制就是：在資料傳回前，您無法篩選、排序、選取或以其他方式操縱這些資料。相反地，您只會獲得一組報告所預設傳回的資料。在某些狀況下，資料數量可能不足。例如，報告可能只傳回上個月的資料，而不是一整年的資料。反過來說，資料也可能在其他狀況下過量：您可能只需要上個月的資料，卻傳回了一整年的資料。
  
若要直接從 Excel 內開啟 Office 365 報告，請完成下列程序︰
  
1. 先在 Excel 中開啟新的工作表。在工作表中依序按一下 [資料]、[從其他來源] 和 [從 OData 資料摘要]。之後便會出現 [資料連線精靈] 對話方塊：
    
     ![連線至 [資料連線精靈] 中 [資料摘要] 對話方塊的範例。](images/o365_reporting_connect_data_feed.png)
  
2. 在 [連線到資料摘要]**** 頁面上，輸入 **https://reports.office365.com/ecp/reportingwebservice/reporting.svc/** 作為資料摘要的位置。請注意，您只能輸入上述的基底 URL；無法新增任何選取、篩選或格式化陳述式。如果輸入基底 URL 以外的內容，就不會傳回任何資料，而只會看到下列錯誤訊息：
    
     ![當您新增 Select、Filter 或 Format 陳述式時，錯誤訊息的範例。](images/o365_reporting_incorrect_data_feed.png)
  
3. 輸入報告服務 URL 後，選取 [登入認證] 底下的 [使用此名稱和密碼]。在 [使用者名稱] 方塊中輸入 Office 365 登入名稱 (例如，admin@litwareinc.onmicrosoft.com)。在 [密碼] 方塊中，輸入 Office 365 登入密碼，然後按 [下一步]。然後 Excel 便會利用提供的認證，嘗試連線到報告服務。
    
4. 通過驗證之後，您會看到 [選取資料表]**** 頁面。選取您想要檢視的報告 (例如，**MailTrafficTop**)，然後按 [下一步]****：
    
     ![[資料連線精靈] 中 [選取資料表] 頁面的範例。](images/o365_reporting_select_tables.png)
  
    > [!NOTE]
    > 您可以選取多個報告；這麼做會在 Excel 試算表中新增多個資料表/圖表。您甚至可以建立單一資料表/圖表，在其中結合多個報告的資料。不過，本簡介文章不會討論到這部分。 
  
5. 按 [下一步] 後，就會出現 [儲存資料連線檔案和完成] 頁面：
    
     ![[資料連線精靈] 中 [儲存資料連線檔案和完成] 頁面的範例。](images/o365_reporting_odata_finish.png)
  
    您不必在此輸入任何資訊。只需要按一下 [完成] 即可擷取資料。不過，值得注意的是，依預設，Excel 會儲存您所建立的每個資料連線的相關資訊；這些資料儲存在 [我的資料來源] 資料夾：
    
     ![[我的資料來源] 資料夾的 [儲存檔案] 對話方塊範例。](images/o365_reporting_save_data_source.png)
  
    這就是為何對話方塊會包含帶有「好記的名稱」和「搜尋關鍵字」之類標籤的文字方塊；這些選項讓您能夠自訂這些資料連線。如此一來，您就不會到頭來擁有一堆看起來像這樣的資料來源：
    
  ```
  DataFeed_1_reports-office365-com ClientSoftwareBrowserDetail.odc
DataFeed_1_reports-office365-com MailTrafficTop.odc
DataFeed_1_reports-office365-com Multiple Tables.odc
DataFeed_2_reports-office365-com MailboxActivityWeekly.odc
DataFeed_2_reports-office365-com MailTrafficTop.odc
DataFeed_3_reports-office365-com ClientSoftwareBrowserDetail.odc
  ```

如果您選取 [將密碼儲存在檔案中] 核取方塊，您就可以重複使用這些資料摘要。例如，假設您將資料連線儲存為「用戶端瀏覽器報告」。下次您想取得用來存取 Office 365 網域之網頁瀏覽器的相關資訊時，您就不必再次執行資料連線精靈的所有步驟。相反地，您只需要開啟 Excel，按一下 [資料]，然後按一下 [現有來源]。在 [現有連線] 對話方塊中選取想要的資料連線，然後按一下 [確定]：
    
![在 [現有連線] 對話方塊中，選取想要的資料連線的範例。](images/o365_reporting_select_connection.png)
  
屆時，Excel 就會為您建立連線並擷取資料。
    
請注意，這些 .ODC 檔案是純文字 XML 檔案。在這些純文字 XML 檔案中所包含的，是您的 Office 365 使用者名稱和密碼︰
    
\<odc:ConnectionString>Data Source=https://reports.office365.com/ecp/reportingwebservice/reporting.svc/;Namespaces to Include=*;Max Received Message Size=4398046511104;Integrated Security=Basic; **User ID=admin@litwareinc.onmicrosoft.com;Password=MYpassw0rd!**;Persist Security Info=false;Service Document Url=https://reports.office365.com/ecp/reportingwebservice/reporting.svc/\</odc:ConnectionString>
    
如果您不想要將使用者名稱和密碼儲存在純文字檔案中，請不要勾選標示為 [將密碼儲存在檔案中] 的核取方塊。不過，如果這樣做的話，請記住您將無法重複使用這些資料連線。這是因為如果沒有使用者名稱和密碼，Office 365 將無法對登入服務的嘗試進行驗證。
    
6. 按一下 [儲存資料連線檔案和完成] 頁面上的 [完成]，將會出現 [匯入資料] 對話方塊：
    
     ![[匯入資料] 對話方塊的範例。](images/o365_reporting_import_data.png)
  
7. 選取檢視選項 (例如 [樞紐分析表])，然後按一下 [確定]。如果一切順利，系統將會匯入資料並以您所選的檢視選項加以呈現。
    
     ![資料已成功匯入到 Excel 工作表中的範例。](images/o365_reporting_sample_spreadsheet.png)
  
之後您要如何處理這些資料就完全取決於您。如果需要建議，請看一下[使用 OData 資料摘要來建立 Excel Services 儀表板](https://technet.microsoft.com/en-us/library/jj873965%28v=office.15%29.aspx)。雖然這篇文章沒有使用 Office 365 報告服務，但提供了一些對於執行作業有用的提示，例如將篩選器和交叉分析篩選器新增到新儀表板等。
  
## <a name="see-also"></a>另請參閱

#### 

[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)
  
[使用 Windows PowerShell 在 Office 365 中建立報告](use-windows-powershell-to-create-reports-in-office-365.md)

