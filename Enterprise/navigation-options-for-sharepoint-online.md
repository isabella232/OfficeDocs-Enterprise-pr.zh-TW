---
title: SharePoint Online 的導覽選項
ms.author: krowley
author: kccross
manager: laurawi
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: 本文說明與 SharePoint 發佈啟用在 SharePoint Online 中的導覽選項的網站。選擇及導覽的設定會大幅影響效能及延展性的 SharePoint Online 中的網站。
ms.openlocfilehash: 08790dcee343e9e69bbaab149cce8a390470e7d6
ms.sourcegitcommit: 5731dce2440e5a7a261f6360e8e2e9639d339d4e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2018
ms.locfileid: "23957448"
---
# <a name="navigation-options-for-sharepoint-online"></a>SharePoint Online 的導覽選項

本文說明與 SharePoint 發佈啟用在 SharePoint Online 中的導覽選項的網站。選擇及導覽的設定會大幅影響效能及延展性的 SharePoint Online 中的網站。

## <a name="overview"></a>概觀

導覽提供者設定可能大幅影響效能的整個網站，並仔細考慮必須採取挑選導覽提供者與調整有效的 SharePoint 網站需求的設定。有兩個的方塊 （英文） 導覽提供者，如自訂導覽實作。

第一個選項[**（中繼資料） 的受管理導覽**](#using-managed-navigation-and-metadata-in-sharepoint-online)，建議和是其中一個 SharePoint Online; 中的預設選項不過，我們建議除非有必要停用安全性修剪。安全性調整安全--預設設定為啟用此功能提供者 ；不過，許多網站不需要安全性調整自導覽元素通常是一致的所有使用者之網站的額外的負荷。若要停用安全性修剪的建議設定，此導覽提供者不需要列舉網站結構，且是可接受的效能影響具高度。

第二個選項、[**結構化導覽**](#using-structural-navigation-in-sharepoint-online)，**不在 SharePoint Online 中的建議的導覽選項**。這個導覽提供者被設計用於內部部署拓撲有限的 SharePoint Online 支援。當它提供功能與其他導覽選項一些其他設定時，這些功能，包括安全性修剪和網站結構列舉的是有代價過多的伺服器的電話及影響延展性和效能時加以使用。取用過多的資源使用 structed 瀏覽網站可能會受限於節流設定。

除了的方塊 （英文） 導覽提供者許多客戶已成功實作替代自訂導覽實作。一種常見的自訂導覽實作類別包含了前所未見儲存導覽節點本機快取的用戶端呈現設計模式。（請參閱**[搜尋導向的用戶端指令碼](#using-search-driven-client-side-scripting)** 在本文中）。

這些功能提供者有幾個重要優點： 
- 它們通常也與回應頁面設計搭配運作。
- 他們是極佳和效能低落因為他們可以呈現不具資源成本 （及重新整理逾時之後在背景中的）。 
- 這些功能提供者可以擷取使用不同的策略，從簡單的靜態組態延伸到不同的動態資料提供者的瀏覽資料。 

資料提供者的範例是使用**搜尋導向導覽**，讓列舉導覽節點及處理安全性調整有效率的彈性。 

還有其他常用的選項來建立**自訂導覽提供者**。請如需進一步上建置自訂導覽提供者的指導，檢閱[的 SharePoint Online 的入口網站的導覽解決方案](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation)。
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a>專業人員和缺點 SharePoint Online 的導覽選項

下表摘要說明每個選項的優缺點。 


|受管理導覽  |結構式導覽  |搜尋導向導覽  |自訂導覽提供者  |
|---------|---------|---------|---------|
|優點：<br/><br/>易於維護<br/>建議您選擇<br/>     |優點：<br/><br/>容易設定<br/>安全性調整<br/>自動更新為新增內容<br/>|優點：<br/><br/>安全性調整<br/>當新增網站時會自動更新<br/>載入時間快速以及本機快取的導覽結構<br/>|優點：<br/><br/>更廣泛選擇的可用選項<br/>Fast 載入時快取正確使用<br/>許多選項以及使用回應頁面設計<br/>|
|缺點：<br/><br/>不會自動更新來反映網站結構<br/>如果已啟用安全性調整的影響效能<br/>|缺點：<br/><br/>**不建議使用**<br/>**影響效能和延展性**<br/>**受限於節流**<br/>|缺點：<br/><br/>沒有輕鬆排序網站的能力<br/>需要自訂主版頁面 (必須具備技能)<br/>|缺點：<br/><br/>自訂開發為必要<br/>外部資料來源需要儲存快取 / 例如 Azure<br/>|

網站需求及技術的功能取決於您網站的最適當的選項。如果您想可擴充的方塊 （英文） 導覽提供者、 受管理導覽與停用安全性修剪是非常好] 選項。 

受管理導覽選項可以透過維護組態，不包含程式碼的自訂檔案和它會比結構化導覽大幅快。如果您需要安全性修剪和會知道如何使用自訂主版頁面及維護 SharePoint Online 的預設主版頁面中可能發生的變更組織中有某些功能，然後搜尋導向選項可能會產生更好使用者經驗。如果您有較複雜的需求，自訂導覽提供者可能會是正確的選擇。不建議使用結構化導覽。

最後，務必注意 SharePoint 新增其他導覽提供者和現代運用多扁平化的網站階層和中樞與支點模型與 SharePoint 中樞站台的 SharePoint 網站架構的功能。這可讓許多案例，可達到不需要 SharePoint 發佈功能的使用與這些導覽設定最佳化以具備延展性和 SharePoint Online 中的延遲。請注意套用相同的基本原則-簡化呈現的結構、 SharePoint 發佈網站的整體結構通常可以幫助的整體效能及擴充，以及。這意味著，而不是交談含有數百個站台 （子網站） 的單一網站集合，以更好的方法是有許多網站集合具有很少的子網站 （子網站）。


## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a>在 SharePoint Online 中使用受管理的導覽與中繼資料

受管理的導覽是功能的另一個的方塊 （英文） 選項可用來重新建立大部分的結構化導覽相同。受管理的中繼資料可以設定為已啟用或停用安全性修剪。當設定已停用安全性修剪、 受管理的導覽是許多常用它載入和常數之伺服器的電話號碼的所有導覽連結。啟用安全性調整，但是可以取消某些受管理導覽的優點與客戶可以選擇探索其中一個自訂導覽方案的最佳效能及延展性。

許多網站不需要安全性調整為導覽結構通常是一致的網站的所有使用者。如果已停用安全性修剪和連結新增至不是所有使用者都擁有存取權的導覽、 連結仍會顯示但拒絕存取訊息將會導致。沒有由於意外存取內容的風險。

### <a name="how-to-implement-managed-navigation-and-the-results"></a>如何實作受管理的導覽和結果

有數個文章 Docs.Microsoft.com 受管理導覽的詳細資訊例如，請參閱[SharePoint Server 中的受管理導覽的概觀](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)。

若要實作受管理的導覽，您設定合約 url 對應至網站的導覽結構。取代在許多情況下的結構化導覽可以甚至是手動 curated 受管理的導覽。例如：

![SharePoint Online 網站結構](media/SPONavOptionsListOfSites.png)

下列範例顯示使用受管理導覽的複雜導覽效能。

![使用受管理的導覽的複雜導覽的效能](media/SPONavOptionsComplexNavPerf.png)

使用受管理的導覽持續改善效能相較於結構化導覽方法。
  
## <a name="using-structural-navigation-in-sharepoint-online"></a>在 SharePoint Online 中使用結構式導覽

這是使用預設的方塊 （英文） 導覽及是最簡單的解決方案但如此具有昂貴的效能取捨。不需要任何自訂以及非使用者的還輕鬆地新增項目、 隱藏項目，從 [設定] 頁面上的管理功能。這是不過也也可輕鬆地管理及控制也與受管理導覽所以建議使用受管理的導覽為 true 會改善效能。

![具有顯示選取的子網站的結構化導覽](media/SPONavOptionsStructuredShowSubsites.png)
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a>開啟 SharePoint Online 中的結構式導覽

為了說明如何使用結構化導覽和顯示標準 SharePoint Online 解決方案的效能子網站] 選項開啟。以下是設定在 [**網站設定**] 頁面上找到的螢幕擷取畫面\>**導覽**。
  
![顯示子網站的螢幕擷取畫面](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a>分析 SharePoint Online 中的結構式導覽效能

若要分析 SharePoint 網頁的效能，使用 Internet Explorer 中的 F12 開發人員工具的 [**網路**] 索引標籤。 
  
![顯示 F12 dev 工具網路索引標籤的螢幕擷取畫面](media/SPONavOptionsNetworks.png)
  
1. 在 **[網路]** 索引標籤上，按一下正在載入的.aspx 頁面，然後按一下 **[詳細資料]** 索引標籤。<br/> ![顯示詳細資料索引標籤的螢幕擷取畫面](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)<br/>
2. 按一下 **[回應標頭]**。 <br/>![[詳細資料] 索引標籤的螢幕擷取畫面](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)<br/>SharePoint 傳回在其回應標頭中一些有用的診斷資訊。 
3. 其中一項最有用是資訊的**SPRequestDuration**是資訊的值的要求所花的伺服器上的程序 （毫秒）。在下列螢幕擷取畫面**顯示子網站**是未核取結構化導覽。這表示全域導覽中是僅限網站集合] 連結：<br/>![將載入時間顯示為要求持續時間的螢幕擷取畫面](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)<br/>
4. **SPRequestDuration**金鑰已 245 （毫秒） 的值。這代表傳回要求所花的時間。由於網站上沒有只有一個導覽項目，這會是很好的基準針對如何 SharePoint Online 執行不頻繁的導覽。下一步的螢幕擷取畫面顯示在子網站中新增如何影響此機碼。<br/>![顯示 2502 毫秒要求持續時間的螢幕擷取畫面](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)<br/>
  
新增子網站有大幅增加傳回此可以相對簡單範例網站頁面要求所花費的時間。複雜的網站階層，包括頁面導覽，和其他設定及拓撲選項可大幅增加此影響更進一步。

## <a name="using-search-driven-client-side-scripting"></a>使用搜尋導向用戶端指令碼

您可以使用搜尋運用使用連續編目的背景內建的索引。從搜尋索引已取出的搜尋結果與結果的安全性調整。這是第通常較快的方塊 （英文） 導覽提供者安全性調整在必要時。使用搜尋結構化導覽，特別是如果您有複雜網站結構，將會加速頁面載入時間許多。透過受管理導覽的主要優點的這是獲益安全性調整。

這個方法需要建立的自訂主版頁面及以自訂的 HTML 取代的方塊 （英文） 導覽程式碼。請遵循此程序在下列範例中取代導覽中的程式碼檔案概述`seattle.html`。在這個範例中，您將會開啟`seattle.html`檔案和取代整個元素`id=”DeltaTopNavigation”`具有自訂的 HTML 程式碼。

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a>範例： 取代的方塊 （英文） 導覽中的程式碼的主版頁面

1.  導覽至 [網站設定] 頁面。
2.  按一下 **[主版頁面]** 來開啟主版頁面圖庫。
3.  您可以從這裡瀏覽整份文件庫並下載檔案`seattle.master`。
4.  使用文字編輯器編輯程式碼，刪除下列螢幕擷取畫面中的程式碼區塊。<br/>![刪除所示的程式碼區塊](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. 移除之間的程式碼`<SharePoint:AjaxDelta id=”DeltaTopNavigation”>`和`<\SharePoint:AjaxDelta>`標記並取代下列程式碼片段：<br/>

```
<div id="loading">
  <!--Replace with path to loading image.-->
  <div style="background-image: url(''); height: 22px; width: 22px; ">
  </div>
</div>
<!-- Main Content-->
<div id="navContainer" style="display:none">
    <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
        </a>
        <ul id="menu" data-bind="foreach: $data.children" style="padding-left:20px">
            <li class="static dynamic-children level1">
                <a class="static dynamic-children menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
               
                 <!-- ko if: children.length > 0-->
                    <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->
                <!-- ko if: children.length == 0-->   
                    <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->   
                </a>
               
                <!-- ko if: children.length > 0-->                                                       
                <ul id="menu"  data-bind="foreach: children;" class="dynamic  level2" >
                    <li class="dynamic level2">
                        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline  ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
         
          <!-- ko if: children.length > 0-->
          <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>
           <!-- /ko -->
          <!-- ko if: children.length == 0-->
          <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>                 
          <!-- /ko -->   
                        </a>
          <!-- ko if: children.length > 0-->
         <ul id="menu" data-bind="foreach: children;" class="dynamic level3" >
          <li class="dynamic level3">
           <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
           </a>
          </li>
         </ul>
           <!-- /ko -->
                    </li>
                </ul>
                <!-- /ko -->
            </li>
        </ul>
    </div>
</div>
```
<br/>
6. 取代的 URL 中載入影像開頭包含連結至網站集合中載入影像的錨點標記。進行的變更之後，重新命名檔案並再將其上傳到主版頁面圖庫。這會產生新的以.master 檔案。<br/>
7. 這個 HTML 都將會填入的搜尋結果傳回從 JavaScript 程式碼的基本標記。您必須編輯程式碼來變更 var 根值 ="網站集合 URL"如下列程式碼片段所示：<br/>

```
var root = “https://spperformance.sharepoint.com/sites/NavigationBySearch”;
```
<br/>
8. 結果會指派給 self.nodes 陣列和不在使用 linq.js 將輸出指派給陣列 self.heirarchy 物件的內建階層。此陣列是繫結至 HTML 物件。做法是 toggleView() 函數中自我物件傳遞至 ko.applyBinding() 函數。<br/>然後這會使要繫結至下列 HTML 的階層陣列：<br/>

```
<div data-bind=”foreach: hierarchy” class=”noindex ms-core-listMenu-horizontalBox”>
```

事件處理常式的`mouseenter`和`mouseexit`新增至要處理的子網站下拉式清單功能表中完成的最上層導覽`addEventsToElements()`函數。

在我們複雜導覽的範例，沒有基準結構化導覽列中取得的受管理的導覽方法類似結果之伺服器上所花費的時間剪本機快取顯示載入全新的頁面。

### <a name="about-the-javascript-file"></a>關於 JavaScript 檔案...]

整個 JavaScript 檔案如下所示：

```
//Models and Namespaces
var SPOCustom = SPOCustom || {};
SPOCustom.Models = SPOCustom.Models || {}
SPOCustom.Models.NavigationNode = function () {

    this.Url = ko.observable("");
    this.Title = ko.observable("");
    this.Parent = ko.observable("");

};

var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
var baseUrl = root + "/_api/search/query?querytext=";
var query = baseUrl + "'contentClass=\"STS_Web\"+path:" + root + "'&trimduplicates=false&rowlimit=300";

var baseRequest = {
    url: "",
    type: ""
};


//Parses a local object from JSON search result.
function getNavigationFromDto(dto) {
    var item = new SPOCustom.Models.NavigationNode();
    if (dto != undefined) {

        var webTemplate = getSearchResultsValue(dto.Cells.results, 'WebTemplate');

        if (webTemplate != "APP") {
            item.Title(getSearchResultsValue(dto.Cells.results, 'Title')); //Key = Title
            item.Url(getSearchResultsValue(dto.Cells.results, 'Path')); //Key = Path
            item.Parent(getSearchResultsValue(dto.Cells.results, 'ParentLink')); //Key = ParentLink
        }

    }
    return item;
}

function getSearchResultsValue(results, key) {

    for (i = 0; i < results.length; i++) {
        if (results[i].Key == key) {
            return results[i].Value;
        }
    }
    return null;
}

//Parse a local object from the serialized cache.
function getNavigationFromCache(dto) {
    var item = new SPOCustom.Models.NavigationNode();

    if (dto != undefined) {

        item.Title(dto.Title);
        item.Url(dto.Url);
        item.Parent(dto.Parent);
    }

    return item;
}

/* create a new OData request for JSON response */
function getRequest(endpoint) {
    var request = baseRequest;
    request.type = "GET";
    request.url = endpoint;
    request.headers = { ACCEPT: "application/json;odata=verbose" };
    return request;
};

/* Navigation Module*/
function NavigationViewModel() {
    "use strict";
    var self = this;
    self.nodes = ko.observableArray([]);
    self.hierarchy = ko.observableArray([]);;
    self.loadNavigatioNodes = function () {
        //Check local storage for cached navigation datasource.
        var fromStorage = localStorage["nodesCache"];
        if (false) {
            var cachedNodes = JSON.parse(localStorage["nodesCache"]);

            if (cachedNodes && timeStamp) {
                //Check for cache expiration. Currently set to 3 hrs.
                var now = new Date();
                var diff = now.getTime() - timeStamp;
                if (Math.round(diff / (1000 * 60 * 60)) < 3) {

                    //return from cache.
                    var cacheResults = [];
                    $.each(cachedNodes, function (i, item) {
                        var nodeitem = getNavigationFromCache(item, true);
                        cacheResults.push(nodeitem);
                    });

                    self.buildHierarchy(cacheResults);
                    self.toggleView();
                    addEventsToElements();
                    return;
                }
            }
        }
        //No cache hit, REST call required.
        self.queryRemoteInterface();
    };

    //Executes a REST call and builds the navigation hierarchy.
    self.queryRemoteInterface = function () {
        var oDataRequest = getRequest(query);
        $.ajax(oDataRequest).done(function (data) {
            var results = [];
            $.each(data.d.query.PrimaryQueryResult.RelevantResults.Table.Rows.results, function (i, item) {

                if (i == 0) {
                    //Add root element.
                    var rootItem = new SPOCustom.Models.NavigationNode();
                    rootItem.Title("Root");
                    rootItem.Url(root);
                    rootItem.Parent(null);
                    results.push(rootItem);
                }
                var navItem = getNavigationFromDto(item);
                results.push(navItem);
            });
            //Add to local cache
            localStorage["nodesCache"] = ko.toJSON(results);

            localStorage["nodesCachedAt"] = new Date().getTime();
            self.nodes(results);
            if (self.nodes().length > 0) {
                var unsortedArray = self.nodes();
                var sortedArray = unsortedArray.sort(self.sortObjectsInArray);

                self.buildHierarchy(sortedArray);
                self.toggleView();
                addEventsToElements();
            }
        }).fail(function () {
            //Handle error here!!
            $("#loading").hide();
            $("#error").show();
        });
    };
    self.toggleView = function () {
        var navContainer = document.getElementById("navContainer");
        ko.applyBindings(self, navContainer);
        $("#loading").hide();
        $("#navContainer").show();

    };
    //Uses linq.js to build the navigation tree.
    self.buildHierarchy = function (enumerable) {
        self.hierarchy(Enumerable.From(enumerable).ByHierarchy(function (d) {
            return d.Parent() == null;
        }, function (parent, child) {
            if (parent.Url() == null || child.Parent() == null)
                return false;
            return parent.Url().toUpperCase() == child.Parent().toUpperCase();
        }).ToArray());

        self.sortChildren(self.hierarchy()[0]);
    };


    self.sortChildren = function (parent) {

        // sjip processing if no children
        if (!parent || !parent.children || parent.children.length === 0) {
            return;
        }

        parent.children = parent.children.sort(self.sortObjectsInArray2);

        for (var i = 0; i < parent.children.length; i++) {
            var elem = parent.children[i];

            if (elem.children && elem.children.length > 0) {
                self.sortChildren(elem);
            }
        }
    };

    // ByHierarchy method breaks the sorting in chrome and firefix 
    // we need to resort  as ascending
    self.sortObjectsInArray2 = function (a, b) {
        if (a.item.Title() > b.item.Title())
            return 1;
        if (a.item.Title() < b.item.Title())
            return -1;
        return 0;
    };


    self.sortObjectsInArray = function (a, b) {
        if (a.Title() > b.Title())
            return -1;
        if (a.Title() < b.Title())
            return 1;
        return 0;
    }
}

//Loads the navigation on load and binds the event handlers for mouse interaction.
function InitCustomNav() {
    var viewModel = new NavigationViewModel();
    viewModel.loadNavigatioNodes();
}

function addEventsToElements() {
    //events.
      $("li.level1").mouseover(function () {
          var position = $(this).position();
          $(this).find("ul.level2").css({ width: 100, left: position.left + 10, top: 50 });
      })
   .mouseout(function () {
     $(this).find("ul.level2").css({  left: -99999, top: 0 });
   
    });
   
     $("li.level2").mouseover(function () {
          var position = $(this).position();
          console.log(JSON.stringify(position));
          $(this).find("ul.level3").css({ width: 100, left: position.left + 95, top:  position.top});
      })
   .mouseout(function () {
     $(this).find("ul.level3").css({  left: -99999, top: 0 });
    });
} _spBodyOnLoadFunctionNames.push("InitCustomNav");

``` 

若要摘要說明在上面所示的程式碼`jQuery $(document).ready`函數有`viewModel object`建立然後`loadNavigationNodes()`呼叫該物件上的函數。此函數也會載入 HTML5 的本機存放區的用戶端瀏覽器中儲存的先前內建的導覽階層或它會呼叫此函數`queryRemoteInterface()`。

`QueryRemoteInterface()`是以要求使用`getRequest()`函數與查詢參數定義稍早在指令碼，然後傳回從伺服器的 [資料。此資料是基本上以使用各種屬性的資料傳輸物件表示之網站集合中的所有網站的陣列。 

然後剖析此資料至先前定義`SPO.Models.NavigationNode`物件使用`Knockout.js`來建立資料繫結到我們稍早所定義的 HTML 的值可觀察屬性使用。 

物件是然後放入結果陣列。此陣列是剖析至 JSON 使用油墨廓清並儲存在本機瀏覽器儲存在未來的頁面載入改善效能。

### <a name="benefits-of-this-approach"></a>這個方法的優點

[這個方法](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)一主要優點是藉由使用 HTML5 的本機存放區，瀏覽會儲存在本機使用者他們載入頁面，下一次。我們要從使用結構化導覽 ； 搜尋 API 取得主要效能改良功能不過，花費一些技術功能來執行和自訂這項功能。 

以的方塊 （英文） 結構化導覽; 相同的方式來排序[範例實作](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)網站字母順序排列。若您想要此順序以外，是說過更複雜開發及維護。此外，這個方法需要以外支援的主版頁面。如果不保留的自訂主版頁面，您的網站會錯過更新和 Microsoft 對主版頁面的增強功能。

[上面的程式碼](#about-the-javascript-file)具有下列相依性：

- jQuery-http://jquery.com/
- KnockoutJS-http://knockoutjs.com/
- Linq.js- http://linqjs.codeplex.com/，或 github.com/neuecc/linq.js

LinqJS 的目前版本不包含在上面的程式碼中使用的 ByHierarchy 方法並將會自動換行導覽程式碼。若要修正此問題，檔案中新增下列方法 Linq.js 一行之前`Flatten: function ()`。

```
ByHierarchy: function(firstLevel, connectBy, orderBy, ascending, parent) {
     ascending = ascending == undefined ? true : ascending;
     var orderMethod = ascending == true ? 'OrderBy' : 'OrderByDescending';
     var source = this;
     firstLevel = Utils.CreateLambda(firstLevel);
     connectBy = Utils.CreateLambda(connectBy);
     orderBy = Utils.CreateLambda(orderBy);
    
     //Initiate or increase level
     var level = parent === undefined ? 1 : parent.level + 1;

    return new Enumerable(function() {
         var enumerator;
         var index = 0;

        var createLevel = function() {
                 var obj = {
                     item: enumerator.Current(),
                     level : level
                 };
                 obj.children = Enumerable.From(source).ByHierarchy(firstLevel, connectBy, orderBy, ascending, obj);
                 if (orderBy !== undefined) {
                     obj.children = obj.children[orderMethod](function(d) {
                         return orderBy(d.item); //unwrap the actual item for sort to work
                     });
                 }
                 obj.children = obj.children.ToArray();
                 Enumerable.From(obj.children).ForEach(function(child) {
                     child.getParent = function() {
                         return obj;
                     };
                 });
                 return obj;
             };

        return new IEnumerator(

        function() {
             enumerator = source.GetEnumerator();
         }, function() {
             while (enumerator.MoveNext()) {
                 var returnArr;
                 if (!parent) {
                     if (firstLevel(enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }

                } else {
                     if (connectBy(parent.item, enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }
                 }
             }
             return false;
         }, function() {
             Utils.Dispose(enumerator);
         })
     });
 },

```
  
## <a name="related-topics"></a>相關主題

[SharePoint Server 中受管理導覽的概觀](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)

