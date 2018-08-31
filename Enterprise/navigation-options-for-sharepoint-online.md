---
title: SharePoint Online 的導覽選項
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/27/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: 本文說明如何藉由使用受管理的導覽或搜尋導向導覽在傳統發佈頁面載入次數的 SharePoint Online 改進。
ms.openlocfilehash: 6b2ee613d0cc6a6df92eb9b53374087a0ac2e5b7
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540196"
---
# <a name="navigation-options-for-sharepoint-online"></a>SharePoint Online 的導覽選項

本文說明如何藉由使用受管理的導覽或搜尋導向導覽在傳統發佈頁面載入次數的 SharePoint Online 改進。
  
SharePoint Online 與傳統啟用的發佈功能有兩種導覽區域;全域導覽與目前導覽。
  
全域導覽功能表會是上方導覽列中的側邊或取決於語言設定和使用的主版頁面的內容中左/右導覽目前導覽時。
  
瀏覽可以效能造成負面影響整個入口網站為其通常會針對整個入口網站的使用與因此為任何 SharePoint 網站的重要元件。
  
結構化導覽不在 SharePoint Online 中的 [建議的瀏覽] 選項隨著它與安全性調整 On 內部部署拓撲設計和這個設計過多的伺服器的通話，且會影響使用時的效能。
  
設計已變更摩登的 SharePoint 網站的現代其中有簡化扁平化的網站階層。這有簡體中文導覽與已移除與導覽相關的效能問題的簡化階層。
  
有兩個主要的方塊 （英文） 導覽選項 SharePoint 以及在第三、 自訂、 搜尋導向的方法。或者，第四及許多常用的選項是建立自訂導覽提供者。請如需自訂導覽提供者的指導，檢閱[的 SharePoint Online 的入口網站的導覽解決方案](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/portal-navigation)。 
  
每個選項具有優缺點下表中所述。
  
|**結構式導覽**|**受管理導覽**|**搜尋導向導覽**||**自訂導覽提供者**|
|:-----|:-----|:-----|:-----|:-----|
| 優點：  <br/>  容易設定  <br/>  安全性調整  <br/>  當新增網站時會自動更新  <br/> | 優點：  <br/>  易於維護  <br/>  建議您選擇  <br/> | 優點：  <br/>  安全性調整  <br/>  當新增網站時會自動更新  <br/>  載入時間快速以及本機快取的導覽結構  <br/> || 優點：  <br/>    <br/>  更廣泛選擇 / 選項可用  <br/>  Fast 載入時快取正確使用  <br/> |
| 缺點：  <br/> **不建議使用** <br/> **效能的影響** <br/> | 缺點：  <br/>  不會自動更新來反映網站結構  <br/>  如果已啟用安全性調整的影響效能  <br/> | 缺點：  <br/>  沒有輕鬆排序網站的能力  <br/>  需要自訂主版頁面 (必須具備技能)  <br/> || 缺點：  <br/>  自訂開發為必要  <br/>  外部資料來源需要儲存快取 / 例如 Azure  <br/> |
   
網站需求及技術的功能取決於您網站的最適當的選項。如果您要知道如何使用自訂主版頁面及維護 SharePoint Online 的預設主版頁面中可能發生的變更組織中有某些功能，搜尋導向] 選項將會產生最佳使用者經驗。如果您想簡單的中間地上之間的方塊 （英文） 結構化導覽和搜尋、 受管理的導覽是非常好] 選項。受管理的導覽選項可以透過維護組態，不包含程式碼自訂檔案，並會大幅較快的方塊 （英文） 結構化導覽。
  
簡化您更加 like 現代的傳統入口網站的整體結構，能協助整體效能和規模，以及完成。這意味著，而不是擁有單一網站集合有數億/千分位的網站 （子網站），以更好的方法有許多網站集合具有很少的子網站 （子網站）。
  
這提供此服務中的其他縮放選項、 可以避免放入一個大資料庫的所有內容和最終可讓導覽及更重要的是安全性彈性。
  
## <a name="using-structural-navigation-in-sharepoint-online"></a>在 SharePoint Online 中使用結構式導覽

這是使用預設的方塊 （英文） 導覽及是最簡單的解決方案但如此具有昂貴的效能取捨。不需要任何自訂以及非使用者的還輕鬆地新增項目、 隱藏項目，從 [設定] 頁面上的管理功能。這是針對受管理導覽所以建議也使用受管理導覽的可以為 true 不過也可輕鬆地管理及控制也。
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a>開啟 SharePoint Online 中的結構式導覽

為了說明如何使用結構化導覽和顯示標準 SharePoint Online 解決方案的效能子網站] 選項開啟。下面是螢幕擷取畫面找到 [**網站設定**] 頁面上設定\>**導覽**。
  
![顯示子網站的螢幕擷取畫面](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a>分析 SharePoint Online 中的結構式導覽效能

若要分析 SharePoint 頁面效能，請在 Internet Explorer 中使用 F12 開發人員工具的 **[網路]** 索引標籤。 
  
![顯示 F12 dev 工具網路索引標籤的螢幕擷取畫面](media/e2aed8af-0843-487a-8b68-4f5260a2685e.png)
  
在 **[網路]** 索引標籤上，按一下正在載入的.aspx 頁面，然後按一下 **[詳細資料]** 索引標籤。 
  
![顯示詳細資料索引標籤的螢幕擷取畫面](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)
  
按一下 **[回應標頭]**。
  
![[詳細資料] 索引標籤的螢幕擷取畫面](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)
  
SharePoint 會在其回應標頭中傳回一些有用的診斷資訊。其中一個最有用的是 **SPRequestDuration**，其為要求在伺服器上處理所需時間的值 (毫秒)。 
  
下列螢幕擷取畫面**顯示子網站**中未核取結構化導覽。這表示全域導覽中是僅限網站集合] 連結： 
  
![將載入時間顯示為要求持續時間的螢幕擷取畫面](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)
  
**SPRequestDuration**金鑰已 245 （毫秒） 的值。這代表傳回要求所花的時間。由於網站上沒有只有一個導覽項目，這會是很好的基準針對如何 SharePoint Online 執行不頻繁的導覽。下一步的螢幕擷取畫面顯示在子網站中新增如何影響此機碼。 
  
![顯示 2502 毫秒要求持續時間的螢幕擷取畫面](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)
  
新增子網站大幅增加傳回頁面要求所需的時間。
  
使用一般的結構化的導覽的優點是您可以輕鬆地組織順序、 隱藏的網站、 新增頁面、 結果的安全性調整您不偏離用於 SharePoint Online 中支援的主版頁面。
  
## <a name="using-managed-navigation-and-managed-metadata-in-sharepoint-online"></a>在 SharePoint Online 中使用受管理的導覽和受管理的中繼資料

受管理的導覽是另一個您可用來將相同功能排序重新建立為結構式導覽的現成可用選項。
  
使用受管理的中繼資料的優點是以擷取資料會比使用內容查詢所建置網站導覽速度快多了。雖然更快速沒有方法安全性修剪結果因此如果使用者沒有存取至指定的網站連結仍會顯示但將會導致錯誤訊息。
  
 **如何實作受管理的導覽和結果**
  
有數個文章 TechNet 上受管理導覽的詳細資訊例如，請參閱[SharePoint Server 2013 中受管理導覽的概觀](https://go.microsoft.com/fwlink/?LinkId=708689)。
  
若要實作受管理的導覽，您必須擁有字詞庫管理員權限。透過使用與網站集合結構相符的 URL 來設定字詞，受管理的導覽可用來取代結構式導覽。例如：
  
![Subsite1 範例的螢幕擷取畫面](media/4155b4da-ccff-4e2a-92de-7803ac62982b.png)
  
下列範例顯示使用受管理導覽的複雜導覽效能。
  
![SPRequestDuration 範例的螢幕擷取畫面](media/72257528-0ec6-48b0-85a5-efeb7432db5b.png)
  
相較於透過查詢結構式導覽方法來使用內容，始終如一地使用受管理的導覽會提高效能。
  
## <a name="using-search-driven-client-side-scripting"></a>使用搜尋導向用戶端指令碼

使用搜尋可讓您利用在背景中以連續編目建立的索引。這表示其中沒有大量內容查詢。搜尋結果會從搜尋索引中提取出來並經過安全性調整。其速度快於使用一般內容查詢。在結構式導覽中使用搜尋 (尤其是網站結構很複雜時) 會大幅加快頁面載入時間。這種方法勝過受管理導覽的主要優勢在於您可受惠於安全性調整。
  
此方法牽涉到建立自訂主版頁面和以自訂 HTML 取代現成可用的導覽程式碼。按照此程序來取代 seattle.html 檔案中的導覽程式碼。
  
在這個範例中，您將會開啟 seattle.html 檔案，並取代整個元素**id ="DeltaTopNavigation"** 具有自訂的 HTML 程式碼。 
  
 **範例：在主版頁面中取代現成可用的導覽程式碼**
  
1. 導覽至 **[網站設定]** 頁面。 
    
2. 按一下 **[主版頁面]** 來開啟主版頁面圖庫。
    
3. 您可以在這裡瀏覽整個圖庫並下載 **seattle.master** 檔案。
    
4. 使用文字編輯器編輯程式碼，刪除下列螢幕擷取畫面中的程式碼區塊。
    
    ![要刪除 DeltaTopNavigation 程式碼的螢幕擷取畫面](media/70db2cd2-660d-4e0d-9d5c-a5df331c73b4.png)
  
5. 移除之間的程式碼\<SharePoint:AjaxDelta id ="DeltaTopNavigation"\>和\<\SharePoint:AjaxDelta\>標記並取代下列程式碼片段：
    
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

6. 取代的 URL 中載入影像開頭包含連結至網站集合中載入影像的錨點標記。進行的變更之後，重新命名檔案並再將其上傳到主版頁面圖庫。這會產生新的以.master 檔案。
    
7. 這個 HTML 都將會填入的搜尋結果傳回從 JavaScript 程式碼的基本標記。您必須編輯下列程式碼變更的值`var root = "site collection URL"`如下列程式碼片段所示： 
    
  ```
  var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
  ```

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
  var query = baseUrl + "'contentClass=\"STS_Web\"+path:" + root + "'&amp;trimduplicates=false&amp;rowlimit=300";
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
              if (cachedNodes &amp;&amp; timeStamp) {
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
              if (elem.children &amp;&amp; elem.children.length > 0) {
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
  
  ```

     $("li.level1").mouseover （函數 （） { 
  
var 位置 = $(this).position();
  
(this) $.find("ul.level2").css ({寬度： 100，left： 最常用的 position.left + 10: 50});
    
     }) 
  
.mouseout （函數 （） {
  
$(this).find("ul.level2").css ({左：-99999、 最佳： 0});
  
});
  
$("li.level2").mouseover （函數 （） {
  
var 位置 = $(this).position();
  
console.log(JSON.stringify(position));
  
$(this).find("ul.level3").css ({寬度： 100，left： 最常用的 position.left + 95、: position.top});
    
     }) 
  
.mouseout （函數 （） {
  
$(this).find("ul.level3").css ({左：-99999、 最佳： 0});
  
});
    
    } _spBodyOnLoadFunctionNames.push("InitCustomNav");
    
    To summarize the code shown above in the jQuery **[$(document).ready]** function there is a **[viewModel]** object created and then the **[loadNavigationNodes()]** function on that object is called. This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function **[queryRemoteInterface()]**. 
    
    **[QueryRemoteInterface()]** builds a request using the **[getRequest()]** function with the query parameter defined earlier in the script and then returns data from the server. This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties. This data is then parsed into the previously defined **[SPO.Models.NavigationNode]** objects which use Knockout.js to create observable properties for use by data binding the values into the HTML that we defined earlier. The objects are then put into a results array. This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads. 
    
8. 接下來，結果會指派給 **[self.nodes]** 陣列及不在使用 linq.js 將輸出指派給陣列 **[self.heirarchy]** 物件的內建階層。此陣列是繫結至 HTML 物件。做法是 **[toggleView()]** 函數中自我物件傳遞至 **[ko.applyBinding()]** 函數。然後這會使要繫結至下列 HTML 的階層陣列： 
    
  ```
  <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
  ```

    最後， **[mouseenter]** 和 **[mouseexit]** 的事件處理常式會新增至最上層導覽處理子網站下拉式清單功能表中的 **[addEventsToElements()]** 函數即可達到此目的。 
    
    瀏覽的結果可以看到的螢幕擷取畫面下方：
    
    ![瀏覽結果的螢幕擷取畫面](media/020d34d2-942a-431b-9b26-6d2c8a6fde30.png)
  
    在我們複雜的導覽範例中，沒有本機快取的全新頁面載入顯示出，在伺服器上所花的時間已較作為基準的結構式導覽來得短，其結果與受管理導覽方法雷同。
    
    ![SPRequestDuration 301 的螢幕擷取畫面](media/307d7caf-e83a-40d9-a551-91d842521d03.png)
  
    此方法的主要好處之一是，藉由使用 HTML5 本機存放區，導覽會儲存在本機供使用者下次載入頁面時使用。
    
透過在結構式導覽中使用搜尋 API，我們大幅提升了效能；然而，想要執行和自訂此功能需要具備一些技術能力。在範例實作中，網站以現成可用結構式導覽的相同方式排序 (英文字母順序)。如果您想要偏離此順序，開發和維護會更加複雜。此外，此方法需要您偏離支援的主版頁面。如果未維護自訂主版頁面，您的網站會遺漏 Microsoft 對主版頁面所做的更新和改進。
  
上面的程式碼具有下列相依性：
  
- jQuery-[http://jquery.com/](http://jquery.com/)
    
- KnockoutJS-[http://knockoutjs.com/](http://knockoutjs.com/)
    
- Linq.js- [http://linqjs.codeplex.com/](http://linqjs.codeplex.com/)，或[github.com/neuecc/linq.js](https://github.com/neuecc/linq.js/)
    
LinqJS 的目前版本不包含在上面的程式碼中使用的 ByHierarchy 方法並將會自動換行導覽程式碼。若要修正此問題，檔案中新增下列方法 Linq.js 一行之前"Flatten： 函數 （）"。
  
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


