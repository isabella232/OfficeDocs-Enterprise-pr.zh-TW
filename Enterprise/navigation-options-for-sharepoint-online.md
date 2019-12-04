---
title: SharePoint Online 的導覽選項
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: 本文說明導覽選項網站與 SharePoint 發佈 SharePoint Online 中啟用。 選擇及設定導覽會大幅影響的效能和延展性的 SharePoint Online 中的網站。 本文不適用於傳統的小組網站。
ms.openlocfilehash: ce6bde50d35cdddf28fed4ad6c74a9a2da8193af
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2019
ms.locfileid: "39814191"
---
# <a name="navigation-options-for-sharepoint-online"></a>SharePoint Online 的導覽選項

本文說明導覽選項網站與 SharePoint 發佈 SharePoint Online 中啟用。 選擇及設定導覽會大幅影響的效能和延展性的 SharePoint Online 中的網站。

## <a name="overview"></a>概觀

導覽提供者設定可能大幅影響效能的整個網站，並仔細考量必須採取挑選導覽提供者和組態有效率地調整 SharePoint 網站的需求。 有兩個的方塊出導覽提供者，以及自訂導覽實作。

第一個選項[**（中繼資料） 的受管理導覽**](#using-managed-navigation-and-metadata-in-sharepoint-online)，建議使用，且 SharePoint Online; 中的預設選項的其中一個不過，我們建議，除非有必要，停用安全性調整。 安全性調整啟用安全--預設設定為此導覽提供者;不過，許多網站不需要安全性調整由於導覽元素通常是一致的網站的所有使用者的額外的負荷。 若要停用安全性修剪的建議組態，此導覽提供者不需要列舉網站結構與延展性極高與可接受的效能影響。

第二個選項，[**結構式導覽**](#using-structural-navigation-in-sharepoint-online)，**不在 SharePoint Online 中的建議瀏覽選項**。 這個導覽提供者所設計的內部拓撲有受限於 SharePoint Online 中的支援。 雖然它會提供一些額外組的功能與其他導覽選項，這些功能，包括安全性修剪和網站結構列舉型別，有其代價過多的伺服器的呼叫並影響延展性和效能時使用它。 網站使用結構化的導覽耗用過多的資源，可能會受到節流。

除了的方塊出導覽提供者，許多客戶已成功實作替代自訂導覽實作。 一種常見的自訂巡覽實作類別樂於儲存瀏覽節點的本機快取的用戶端呈現設計圖樣。 （請參閱**[搜尋導向用戶端指令碼](#using-search-driven-client-side-scripting)** 本文中）。

這些導覽提供者有幾個重要的優點：

- 它們通常適用於回應] 頁面上的設計。
- 它們是極延展性和效能低落因為他們可以呈現與任何資源成本 （和重新整理逾時之後在背景中的）。
- 這些導覽提供者可以擷取使用各種不同的策略，範圍從簡單的靜態設定到不同的動態資料提供者的瀏覽資料。

資料提供者的範例為使用**搜尋導向導覽**，可讓列舉瀏覽節點和處理安全性有效率地調整的彈性。

有其他常用的選項來建立**自訂導覽提供者**。 請檢閱[SharePoint Online 入口網站的導覽解決方案](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation)進一步上建置的自訂導覽提供者的指引。
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a>優點和缺點的 SharePoint Online 的導覽選項

下表摘要說明每個選項的優缺點。

|受管理導覽  |結構式導覽  |搜尋導向導覽  |自訂導覽提供者  |
|---------|---------|---------|---------|
|Pros:<br/><br/>易於維護<br/>建議的選項<br/>     |Pros:<br/><br/>容易設定<br/>安全性調整<br/>當內容會新增自動更新<br/>|Pros:<br/><br/>安全性調整<br/>當新增網站時會自動更新<br/>快速載入時間，並在本機上快取的導覽結構<br/>|Pros:<br/><br/>寬的選擇，可用的選項<br/>快速載入時快取正確使用<br/>有許多選項適用於回應頁面設計<br/>|
|缺點：<br/><br/>不會自動更新以反映網站結構<br/>如果已啟用安全性調整的影響效能<br/>|缺點：<br/><br/>**不建議使用**<br/>**影響效能和延展性**<br/>**受到節流限制**<br/>|缺點：<br/><br/>沒有輕鬆排序網站的能力<br/>需要自訂主版頁面 （必須具備技能）<br/>|缺點：<br/><br/>自訂開發，則需要<br/>外部資料來源需要儲存的快取 / 例如 Azure<br/>|

網站需求及您技術的功能取決於您網站的最適當的選項。 如果您想可擴充的方塊出導覽提供者，受管理導覽與停用安全性修剪是很好的選項。

受管理導覽選項可以透過維護組態中，沒有牽涉到程式碼的自訂檔案，而且可大幅比結構式導覽。 如果您需要進行安全性調整習慣使用自訂的主版頁面，並維護的 SharePoint Online 中的預設主版頁面可能發生的變更在組織中有某些功能，然後搜尋導向選項可能會產生更好使用者經驗。 如果您有更複雜的需求，自訂的導覽提供者可能會選擇。 不建議使用結構式導覽。

最後，務必注意，SharePoint 會新增額外的導覽提供者和新式的 SharePoint 網站架構，利用多簡維的網站階層和具有 SharePoint 中樞站台的中樞與支點模型的功能。 這可讓許多案例，以達成不需要使用的 SharePoint 發佈功能，以及這些導覽設定已針對延展性和延遲內 SharePoint Online 進行最佳化。 請注意，套用相同的簡化呈現結構 SharePoint 發佈網站整體結構通常原則有助於整體效能，以及調整。 這表示是，而不是有數百個站台 （子網站） 的單一網站集合，更好的方法有許多具有極少的子網站 （子網站） 的網站集合。

## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a>在 SharePoint Online 中使用受管理的導覽與中繼資料

受管理的導覽是功能的另一個的方塊擴充選項您可以用來重新建立大部分的結構式導覽相同。 受管理的中繼資料可以設定為已啟用或停用安全性修剪。 設定停用的安全性調整，受管理的導覽時很有效率載入常數多個伺服器的呼叫的導覽連結時。 啟用安全性調整，不過，否定受管理導覽的優點，客戶可以選擇瀏覽其中一個自訂導覽解決方案的最佳效能及延展性。

許多網站不需要進行安全性調整，瀏覽結構通常都是一致的網站的所有使用者。 如果已停用安全性修剪和連結新增至導覽並非所有使用者都擁有存取權，連結仍然會顯示，但會導致拒絕存取訊息。 沒有任何不慎內容的存取權的風險。

### <a name="how-to-implement-managed-navigation-and-the-results"></a>如何實作受管理的導覽和結果

有幾篇文章 Docs.Microsoft.com 上受管理導覽的詳細資訊，例如，請參閱[在 SharePoint Server 中受管理導覽的概觀](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)。

為了實作受管理的導覽，您設定條款與 Url 對應至網站的導覽結構。 若要取代在許多情況下的結構式導覽可以甚至是手動 curated 受管理的導覽。 例如：

![SharePoint Online 網站結構](media/SPONavOptionsListOfSites.png)

下列範例會顯示使用受管理的導覽的複雜導覽效能。

![使用受管理的導覽的複雜導覽的效能](media/SPONavOptionsComplexNavPerf.png)

一致地使用受管理的導覽改善效能要優於結構式導覽方法雷同。
  
## <a name="using-structural-navigation-in-sharepoint-online"></a>在 SharePoint Online 中使用結構式導覽

這是使用預設的全新的瀏覽和是最簡單的解決方案，但如此有昂貴的效能的代價。 它不需要任何自訂非技術使用者也可以和也輕鬆新增項目、 隱藏項目，從 [設定] 頁面管理導覽。 這是針對受管理導覽，所以建議使用受管理導覽為 true 也可輕鬆地管理及控制也與不過也改善效能。

![具有顯示選取的子網站的結構式導覽](media/SPONavOptionsStructuredShowSubsites.png)
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a>開啟 SharePoint Online 中的結構式導覽

若要說明如何使用結構式導覽和顯示標準 SharePoint Online 方案中的效能子選項開啟。 以下是設定在 [**網站設定**] 頁面上找到的螢幕擷取畫面\>**導覽**。
  
![顯示子網站的螢幕擷取畫面](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a>分析 SharePoint Online 中的結構式導覽效能

若要分析 SharePoint 網頁的效能，請在 Internet Explorer 中使用 F12 開發人員工具的 [**網路**] 索引標籤。
  
![顯示 F12 dev 工具網路索引標籤的螢幕擷取畫面](media/SPONavOptionsNetworks.png)
  
1. [**網路**] 索引標籤中，按一下正在載入的.aspx 頁面，然後按一下 [**詳細資料**] 索引標籤。<br/> ![顯示詳細資料索引標籤的螢幕擷取畫面](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)<br/>
2. 按一下 [**回應標頭**]。 <br/>![[詳細資料] 索引標籤的螢幕擷取畫面](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)<br/>SharePoint 會在其回應標頭中傳回一些有用的診斷資訊。 
3. 下列其中一項最有用是資訊的**SPRequestDuration**這是資訊的值，以毫秒為單位的時間長度要求所需的伺服器上的程序。 下列螢幕擷取畫面**顯示子網站**未選取的結構式導覽。 這表示在全域導覽是僅限網站集合] 連結：<br/>![將載入時間顯示為要求持續時間的螢幕擷取畫面](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)<br/>
4. **SPRequestDuration**機碼具有值為 245 （毫秒）。 這表示它可傳回要求所花費的時間。 由於在網站上只有一個導覽項目，這會是如何 SharePoint Online 會執行而不頻繁的瀏覽的良好基準。 下一個螢幕擷取畫面顯示如何在子網站中新增影響此機碼。<br/>![顯示 2502 毫秒要求持續時間的螢幕擷取畫面](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)<br/>
  
新增子網站大幅增加傳回此相當簡單的範例網站頁面要求所花費的時間。 複雜的網站階層，其中包括頁面導覽中，以及其他組態和拓撲選項能夠大幅增加此影響更進一步。

## <a name="using-search-driven-client-side-scripting"></a>使用搜尋導向用戶端指令碼

您可以使用搜尋利用背景使用連續編目會內建的索引。 在搜尋結果提取自搜尋索引和結果是經過安全性調整。 需要進行安全性調整時，這是通常較快的方塊出導覽提供者。 使用結構式導覽的搜尋，尤其是如果您的複雜網站結構，會加速的頁面載入時間很。 這段受管理導覽的主要優點是享有安全性調整。

此方法涉及建立自訂的主版頁面及使用自訂的 HTML 取代的全新的瀏覽程式碼。 遵循此程序所述在下列範例中要取代的瀏覽程式碼檔案中`seattle.html`。 在這個範例中，您將會開啟`seattle.html`檔案，並取代整個元素`id=”DeltaTopNavigation”`具有自訂的 HTML 程式碼。

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a>範例： 取代在主版頁面中的全新的瀏覽程式碼

1. 瀏覽至 [網站設定] 頁面上。
2. 按一下 [**主版頁面**，以開啟主版頁面圖庫。
3. 您可以從這裡瀏覽文件庫，並下載檔案`seattle.master`。
4. 編輯程式碼使用文字編輯器，並刪除下列螢幕擷取畫面中的程式碼區塊。<br/>![刪除所示的程式碼區塊](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. 移除之間的程式碼`<SharePoint:AjaxDelta id=”DeltaTopNavigation”>`和`<\SharePoint:AjaxDelta>`標記，並以下列程式碼片段取代：<br/>

```javascript
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
6. 取代中載入的 URL 影像開頭具有網站集合中載入影像連結的錨點標記。 您所做的變更之後，重新命名檔案，然後將其上傳至主版頁面圖庫。 這會產生新的.master 檔案。<br/>
7. 此 HTML 是從 JavaScript 程式碼傳回的搜尋結果會填入的基本標記。 您想要編輯若要變更的值為 var 根程式碼 = 「 網站集合 URL 」 的下列程式碼片段所示：<br/>

```javascript
var root = “https://spperformance.sharepoint.com/sites/NavigationBySearch”;
```
<br/>
8. 結果會指派給 self.nodes 陣列及使用 linq.js 將輸出指派給陣列 self.hierarchy 物件超出內建階層。 此陣列是繫結至 HTML 的物件。 完成此工作的 toggleView() 函式中藉由將自我物件傳遞至 ko.applyBinding() 函式。<br/>然後，這樣會使繫結至下列的 HTML 階層陣列：<br/>

```javascript
<div data-bind=”foreach: hierarchy” class=”noindex ms-core-listMenu-horizontalBox”>
```

事件處理常式`mouseenter`和`mouseexit`新增至最上層的導覽，以處理子網站下拉式功能表中完成`addEventsToElements()`函式。

在我們複雜的導覽的範例，而不從基準的結構式導覽若要取得的受管理的導覽方法類似結果在伺服器上所花費的時間剪本機快取顯示載入新鮮的頁面。

### <a name="about-the-javascript-file"></a>關於 JavaScript 檔案...]

整個 JavaScript 檔案如下所示：

```javascript
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

    // ByHierarchy method breaks the sorting in chrome and firefox
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

若要將摘要說明在上述程式碼`jQuery $(document).ready`函數有`viewModel object`建立，然後`loadNavigationNodes()`來呼叫函式，該物件上的。 此函數可以載入儲存在用戶端瀏覽器 HTML5 本機儲存體中先前內建的導覽階層或它會呼叫函式`queryRemoteInterface()`。

`QueryRemoteInterface()`建置要求使用`getRequest()`函式查詢參數稍早在指令碼中定義並再從伺服器傳回資料。 此資料是基本上是陣列的資料傳輸物件具有各種屬性，以表示網站集合中的所有網站。 

然後剖析此資料到先前定義`SPO.Models.NavigationNode`物件使用這個`Knockout.js`資料值繫結到我們先前定義的 HTML 建立用於觀察到的屬性。 

物件是然後放入結果陣列。 此陣列是剖析成 JSON 使用油墨廓清且儲存在本機瀏覽器儲存在未來的頁面載入改善效能。

### <a name="benefits-of-this-approach"></a>這個方法的優點

[此方法](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)的主要好處之一是，藉由使用 HTML5 本機存放區，導覽會儲存在本機使用者下次載入頁面的下一個時間。 我們會從使用結構式導覽; 搜尋 API 取得主要的效能改進不過，它會採用一些技術的功能，以執行及自訂這項功能。 

在[範例實作](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)，網站會排序的方塊出結構式導覽; 為相同的方式依字母順序排列順序。 如果您想要從這個順序以外，它就會以開發和維護更複雜。 此外，此方法需要您支援的主版頁面以外。 如果自訂主版頁面並不會維護，您的網站會錯過更新和 Microsoft 對主版頁面的增強功能。

[上述程式碼](#about-the-javascript-file)具有下列相依性：

- jQuery-https://jquery.com/
- KnockoutJS-https://knockoutjs.com/
- Linq.js- https://linqjs.codeplex.com/，或 github.com/neuecc/linq.js

目前版本的 LinqJS 不包含在上面的程式碼中使用的 ByHierarchy 方法，並將會中斷瀏覽程式碼。 若要修正此問題，請將下列方法新增至一行之前 Linq.js 檔案`Flatten: function ()`。

```javascript
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
