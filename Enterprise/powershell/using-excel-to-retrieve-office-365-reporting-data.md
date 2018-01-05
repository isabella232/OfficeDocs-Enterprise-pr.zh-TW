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
# <a name="using-excel-to-retrieve-office-365-reporting-data"></a><span data-ttu-id="6f301-103">使用 Excel 擷取 Office 365 報表資料</span><span class="sxs-lookup"><span data-stu-id="6f301-103">Using Excel to Retrieve Office 365 Reporting Data</span></span>

 <span data-ttu-id="6f301-104">**摘要：**使用 Microsoft Excel 中的 oData 功能，來擷取 Office 365 部署的詳細報告資訊。</span><span class="sxs-lookup"><span data-stu-id="6f301-104">Summary: Use the oData feature in Microsoft Excel to retrieve detailed reporting information for your deployment of Office 365</span></span>
  
<span data-ttu-id="6f301-p101">報告是系統管理的重要部分。Office 365 系統管理中心包括幾個預先定義的報告，您可以從左方瀏覽區的 **報告**區段存取。有使用報告和安全性及規範符合性報告。</span><span class="sxs-lookup"><span data-stu-id="6f301-p101">Reporting is a key part of system administration. The Office 365 Admin center includes a number of predefined reports, which you can access from the **Reports** section of the left navigation. There are usage reports and security and compliance reports.</span></span>
  
<span data-ttu-id="6f301-p102">您所使用的 Office 365 版本以及已啟用哪些 Office 365 服務會決定您可以使用哪些報告。如需詳細資訊，請參閱[報告]((https://technet.microsoft.com/zh-TW/library/office-365-reports.aspx))頁面。</span><span class="sxs-lookup"><span data-stu-id="6f301-p102">The reports available to you depend on the version of Office 365 you are using and which Office 365 services you have enabled. For more information, see the [Reports page]((https://technet.microsoft.com/zh-TW/library/office-365-reports.aspx)).</span></span>
  
<span data-ttu-id="6f301-p103">預先定義的系統管理中心報告是絕佳資源，可讓您輕鬆檢視信箱使用量，或使用者在線上會議待了多久時間等資訊。不過，若要對 Office 365 網域進行詳細分析，報告就會面臨一些限制。</span><span class="sxs-lookup"><span data-stu-id="6f301-p103">The pre-defined Admin center reports are an excellent resource. They make it easy to check on such things as mailbox usage or the number of minutes that your users have been spending in online conferences. However, when it comes to detailed analysis of your Office 365 domain, the reports do have their limitations.</span></span>
  
<span data-ttu-id="6f301-p104">有一個方法可解決這些限制，那就是使用 Windows PowerShell 或其他開發語言存取 Office 365 報告服務，並建立自訂報告，藉由自訂報告，您可以規定要從 Office 365 報告服務傳回哪些資料以及傳回的資料量。透過編寫自訂報告，您也可以指定如何排序和分類資料，以及該如何儲存資料 (若適用)，例如您可以將資料儲存為 XML 格式，或是儲存為可方便匯入 Excel 中使用的逗點分隔值格式。</span><span class="sxs-lookup"><span data-stu-id="6f301-p104">One way to work around these limitations is to use Windows PowerShell or another development language to access the Office 365 reporting service and create custom reports; custom reports give you the ability to dictate which data (and how much data) is returned from the Office 365 reporting service. By writing custom reports you can also specify how the data should be sorted and grouped, and, if applicable, how that data should be saved; for example, you can save data in XML format or in a comma-separated values format that can easily be imported in Excel.</span></span> 
  
<span data-ttu-id="6f301-p105">此外，自訂指令碼/應用程式可讓您存取 Office 365 系統管理中心未能提供的報告。例如，系統管理中心可以指出您有多少「過時」信箱，但無法指出在過去 30 天內沒有存取過的信箱。但自訂的 PowerShell 指令碼則可以提供這項資訊。總的來說，這表示雖然您必須撰寫簡短且相對簡單的小型 Windows PowerShell 指令碼，但卻能換得諸多彈性。</span><span class="sxs-lookup"><span data-stu-id="6f301-p105">In addition, custom scripts/applications enable you to access reports that are not available in the Office 365 Admin center. For example, the Admin center can tell you how many stale mailboxes you have, but it can't tell which mailboxes haven't been accessed in the past 30 days. That is something that a custom PowerShell script can tell you. Taken together, this represents an enormous amount of flexibility in return for having to write a short and relatively-simple Windows PowerShell script.</span></span>
  
> [!VISUAL BASIC NOTE]<span data-ttu-id="6f301-119"> 如需詳細資訊，請參閱 Office 365 報告服務的[首頁](https://msdn.microsoft.com/en-us/library/office/jj984325%28v=office.15%29.aspx)。</span><span class="sxs-lookup"><span data-stu-id="6f301-119"> For more information, see the [home page](https://msdn.microsoft.com/en-us/library/office/jj984325%28v=office.15%29.aspx) for the Office 365 reporting service.</span></span>
  
<span data-ttu-id="6f301-p106">為了擷取這項資料，您必須撰寫某種程式碼。如果組織較為龐大，需要限制傳回的資訊數量和類型，這麼做很值得。但如果組織規模較小，並不需要限制傳回的資訊數量和類型，則您可以考慮從 Excel 本身開啟 Office 365 報告。</span><span class="sxs-lookup"><span data-stu-id="6f301-p106">In order to retrieve this data, you do have to write code of some kind. That's worth it if you are a larger organization that needs to limit the amount and the type of information that gets returned. But if you're a smaller organization, and you don't need to limit the amount and type of information that gets returned, you might consider opening the Office 365 reports from within Excel itself.</span></span>
  
<span data-ttu-id="6f301-p107">不過在此有一些限制，最主要的一個限制就是：在資料傳回前，您無法篩選、排序、選取或以其他方式操縱這些資料。相反地，您只會獲得一組報告所預設傳回的資料。在某些狀況下，資料數量可能不足。例如，報告可能只傳回上個月的資料，而不是一整年的資料。反過來說，資料也可能在其他狀況下過量：您可能只需要上個月的資料，卻傳回了一整年的資料。</span><span class="sxs-lookup"><span data-stu-id="6f301-p107">However, there are a few limitations here, the primary one being this: you cannot filter, sort, select, or otherwise manipulate the data that before it gets returned. Instead, you simply get back the default set of data returned by the report. In some cases that might not be enough data. For example, the report might return data for, say, only the previous month and not for the entire year. Conversely, in other cases that might be too much data: you might get back data for the entire year even though you only want data for the previous month.</span></span>
  
<span data-ttu-id="6f301-128">若要直接從 Excel 內開啟 Office 365 報告，請完成下列程序︰</span><span class="sxs-lookup"><span data-stu-id="6f301-128">To open an Office 365 report directly from within Excel, complete the following procedure:</span></span>
  
1. <span data-ttu-id="6f301-p108">先在 Excel 中開啟新的工作表。在工作表中依序按一下 [資料]、[從其他來源] 和 [從 OData 資料摘要]。之後便會出現 [資料連線精靈] 對話方塊：</span><span class="sxs-lookup"><span data-stu-id="6f301-p108">Start by opening a new worksheet in Excel. On that worksheet, click **Data**, click **From Other Sources**, and then click **From OData Data Feed**. That brings up the **Data Connection Wizard** dialog box:</span></span>
    
     ![連線至 [資料連線精靈] 中 [資料摘要] 對話方塊的範例。](images/o365_reporting_connect_data_feed.png)
  
2. <span data-ttu-id="6f301-p109">在 [連線到資料摘要]**** 頁面上，輸入 **https://reports.office365.com/ecp/reportingwebservice/reporting.svc/** 作為資料摘要的位置。請注意，您只能輸入上述的基底 URL；無法新增任何選取、篩選或格式化陳述式。如果輸入基底 URL 以外的內容，就不會傳回任何資料，而只會看到下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="6f301-p109">On the **Connect to a Data Feed** page, enter **https://reports.office365.com/ecp/reportingwebservice/reporting.svc/** as the data feed location. Note that you can only enter the base URL as shown; you cannot add any Select, Filter, or Format statements. If you enter anything but the base URL you won’t get back any data; instead, you’ll simply see the following error message:</span></span>
    
     ![當您新增 Select、Filter 或 Format 陳述式時，錯誤訊息的範例。](images/o365_reporting_incorrect_data_feed.png)
  
3. <span data-ttu-id="6f301-p110">輸入報告服務 URL 後，選取 [登入認證] 底下的 [使用此名稱和密碼]。在 [使用者名稱] 方塊中輸入 Office 365 登入名稱 (例如，admin@litwareinc.onmicrosoft.com)。在 [密碼] 方塊中，輸入 Office 365 登入密碼，然後按 [下一步]。然後 Excel 便會利用提供的認證，嘗試連線到報告服務。</span><span class="sxs-lookup"><span data-stu-id="6f301-p110">After entering the reporting service URL, select **Use this name and password** under **Log on credentials**. In the **User Name** box, enter your Office 365 logon name (for example, admin@litwareinc.onmicrosoft.com). In the **Password** box, enter your Office 365 logon password and then click **Next**. Excel will then attempt to connect to the reporting service using the supplied credentials.</span></span>
    
4. <span data-ttu-id="6f301-p111">通過驗證之後，您會看到 [選取資料表]**** 頁面。選取您想要檢視的報告 (例如，**MailTrafficTop**)，然後按 [下一步]****：</span><span class="sxs-lookup"><span data-stu-id="6f301-p111">After you have been authenticated, you’ll see the **Select Tables** page. Select the report that you’d like to view (for example, **MailTrafficTop**) and then click **Next**:</span></span>
    
     ![[資料連線精靈] 中 [選取資料表] 頁面的範例。](images/o365_reporting_select_tables.png)
  
    > [!NOTE]
    > <span data-ttu-id="6f301-p112">您可以選取多個報告；這麼做會在 Excel 試算表中新增多個資料表/圖表。您甚至可以建立單一資料表/圖表，在其中結合多個報告的資料。不過，本簡介文章不會討論到這部分。</span><span class="sxs-lookup"><span data-stu-id="6f301-p112">It's possible to select multiple reports; that results in multiple tables/charts being added to your Excel spreadsheet. It's even possible to create a single table/chart that combines data from multiple reports. However, we won't discuss that in this introductory article.</span></span> 
  
5. <span data-ttu-id="6f301-147">按 [下一步] 後，就會出現 [儲存資料連線檔案和完成] 頁面：</span><span class="sxs-lookup"><span data-stu-id="6f301-147">After clicking **Next** you'll be presented with the **Save Data Connection File and Finish** page:</span></span>
    
     ![[資料連線精靈] 中 [儲存資料連線檔案和完成] 頁面的範例。](images/o365_reporting_odata_finish.png)
  
    <span data-ttu-id="6f301-p113">您不必在此輸入任何資訊。只需要按一下 [完成] 即可擷取資料。不過，值得注意的是，依預設，Excel 會儲存您所建立的每個資料連線的相關資訊；這些資料儲存在 [我的資料來源] 資料夾：</span><span class="sxs-lookup"><span data-stu-id="6f301-p113">You don't have to enter any information here. All you need to do to retrieve your data is to click **Finish**. However, it's worth noting that, by default, Excel saves information about each data connection you make; this data is stored in your **My Data Sources** folder:</span></span>
    
     ![[我的資料來源] 資料夾的 [儲存檔案] 對話方塊範例。](images/o365_reporting_save_data_source.png)
  
    <span data-ttu-id="6f301-p114">這就是為何對話方塊會包含帶有「好記的名稱」和「搜尋關鍵字」之類標籤的文字方塊；這些選項讓您能夠自訂這些資料連線。如此一來，您就不會到頭來擁有一堆看起來像這樣的資料來源：</span><span class="sxs-lookup"><span data-stu-id="6f301-p114">That's why the dialog box includes text boxes with labels like **Friendly Name** and **Search Keywords**; these options give you the chance to customize these data connections. That way you do not end up with a whole bunch of data sources that look like these:</span></span>
    
  ```
  DataFeed_1_reports-office365-com ClientSoftwareBrowserDetail.odc
DataFeed_1_reports-office365-com MailTrafficTop.odc
DataFeed_1_reports-office365-com Multiple Tables.odc
DataFeed_2_reports-office365-com MailboxActivityWeekly.odc
DataFeed_2_reports-office365-com MailTrafficTop.odc
DataFeed_3_reports-office365-com ClientSoftwareBrowserDetail.odc
  ```

<span data-ttu-id="6f301-p115">如果您選取 [將密碼儲存在檔案中] 核取方塊，您就可以重複使用這些資料摘要。例如，假設您將資料連線儲存為「用戶端瀏覽器報告」。下次您想取得用來存取 Office 365 網域之網頁瀏覽器的相關資訊時，您就不必再次執行資料連線精靈的所有步驟。相反地，您只需要開啟 Excel，按一下 [資料]，然後按一下 [現有來源]。在 [現有連線] 對話方塊中選取想要的資料連線，然後按一下 [確定]：</span><span class="sxs-lookup"><span data-stu-id="6f301-p115">If you select the checkbox **Save password in file**, you'll be able to reuse these data feeds. For example, suppose you save a data connection as **Client Browser Report**. The next time you want information about the web browsers being used to access your Office 365 domain you don't have to walk through the data connection wizard. Instead, all you need to do is open Excel, click **Data**, and then click **Existing Sources**. Select the desired data connection in the **Existing Connections** dialog box and then click **OK**:</span></span>
    
![在 [現有連線] 對話方塊中，選取想要的資料連線的範例。](images/o365_reporting_select_connection.png)
  
<span data-ttu-id="6f301-161">屆時，Excel 就會為您建立連線並擷取資料。</span><span class="sxs-lookup"><span data-stu-id="6f301-161">At that point, Excel will make the connection for you and retrieve the data.</span></span>
    
<span data-ttu-id="6f301-p116">請注意，這些 .ODC 檔案是純文字 XML 檔案。在這些純文字 XML 檔案中所包含的，是您的 Office 365 使用者名稱和密碼︰</span><span class="sxs-lookup"><span data-stu-id="6f301-p116">Note that these .ODC files are plain-text XML files. Included in these plain-text XML files are your Office 365 user name and password:</span></span>
    
<span data-ttu-id="6f301-164">\<odc:ConnectionString>Data Source=https://reports.office365.com/ecp/reportingwebservice/reporting.svc/;Namespaces to Include=*;Max Received Message Size=4398046511104;Integrated Security=Basic; **User ID=admin@litwareinc.onmicrosoft.com;Password=MYpassw0rd!**;Persist Security Info=false;Service Document Url=https://reports.office365.com/ecp/reportingwebservice/reporting.svc/\</odc:ConnectionString></span><span class="sxs-lookup"><span data-stu-id="6f301-164"><odc:ConnectionString>Data Source=https://reports.office365.com/ecp/reportingwebservice/reporting.svc/;Namespaces to Include=*;Max Received Message Size=4398046511104;Integrated Security=Basic; User ID=admin@litwareinc.onmicrosoft.com;Password=MYpassw0rd!;Persist Security Info=false;Service Document Url=https://reports.office365.com/ecp/reportingwebservice/reporting.svc/</odc:ConnectionString></span></span>
    
<span data-ttu-id="6f301-p117">如果您不想要將使用者名稱和密碼儲存在純文字檔案中，請不要勾選標示為 [將密碼儲存在檔案中] 的核取方塊。不過，如果這樣做的話，請記住您將無法重複使用這些資料連線。這是因為如果沒有使用者名稱和密碼，Office 365 將無法對登入服務的嘗試進行驗證。</span><span class="sxs-lookup"><span data-stu-id="6f301-p117">If you don't like the idea of saving your user name and password in a plain-text file, then don't check the box labeled **Save password in file**. If you do that, however, keep in mind that you won't be able to reuse these data connections. That's because, without the user name and password, Office 365 will not be able to authenticate your attempt to log on to the service.</span></span>
    
6. <span data-ttu-id="6f301-168">按一下 [儲存資料連線檔案和完成] 頁面上的 [完成]，將會出現 [匯入資料] 對話方塊：</span><span class="sxs-lookup"><span data-stu-id="6f301-168">Click **Finish** on the **Save Data Connection File and Finish** page you'll be presented with the **Import Data** dialog box:</span></span>
    
     ![[匯入資料] 對話方塊的範例。](images/o365_reporting_import_data.png)
  
7. <span data-ttu-id="6f301-p118">選取檢視選項 (例如 [樞紐分析表])，然後按一下 [確定]。如果一切順利，系統將會匯入資料並以您所選的檢視選項加以呈現。</span><span class="sxs-lookup"><span data-stu-id="6f301-p118">Select your view options (for example, **PivotTable Report** ) and then click **OK**. If all goes well, your data will be imported and be presented in whichever view option you happened to choose:</span></span>
    
     ![資料已成功匯入到 Excel 工作表中的範例。](images/o365_reporting_sample_spreadsheet.png)
  
<span data-ttu-id="6f301-p119">之後您要如何處理這些資料就完全取決於您。如果需要建議，請看一下[使用 OData 資料摘要來建立 Excel Services 儀表板](https://technet.microsoft.com/en-us/library/jj873965%28v=office.15%29.aspx)。雖然這篇文章沒有使用 Office 365 報告服務，但提供了一些對於執行作業有用的提示，例如將篩選器和交叉分析篩選器新增到新儀表板等。</span><span class="sxs-lookup"><span data-stu-id="6f301-p119">What you do with that data is then entirely up to you. For some suggestions. take a look at [Create an Excel Services dashboard using an oData data feed](https://technet.microsoft.com/en-us/library/jj873965%28v=office.15%29.aspx). Although that article doesn't use the Office 365 reporting service, it does provide some handy hints for doing things like adding filters and slicers to your new dashboard.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6f301-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f301-177">See also</span></span>

#### 

[<span data-ttu-id="6f301-178">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="6f301-178">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="6f301-179">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="6f301-179">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="6f301-180">使用 Windows PowerShell 在 Office 365 中建立報告</span><span class="sxs-lookup"><span data-stu-id="6f301-180">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)

