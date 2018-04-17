---
title: 設定搜尋 onedrive for Business 多重地理位置
ms.author: tlarsen
author: tklarsen
manager: arnek
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: 了解如何在多個地理位置環境中設定搜尋。
ms.openlocfilehash: 5cf155c2c5bd2e27a54d84c4d5411e5b1afce568
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="configure-search-for-onedrive-for-business-multi-geo"></a>設定搜尋 onedrive for Business 多重地理位置

在多個地理位置 SharePoint Online (SPO) 環境中，組織可以有一個 Office 365 租用戶，但其 SharePoint 內容儲存在多個地理位置-一個集中位置及一或多衛星地理位置。

每個地理位置有其專屬的搜尋索引和搜尋中心。當使用者搜尋時，查詢扇形至所有索引，並傳回的結果會合併。

例如地理位置中的使用者可以搜尋的內容儲存在另一個地理位置，或限制到不同地理位置的 SharePoint 網站上的內容。如果使用者可以存取此內容，搜尋會顯示結果。

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a>其中中的搜尋用戶端的多重地理位置環境？

這些用戶端可以從所有地理位置傳回的結果：

-   OneDrive for Business

-   Delve

-   SharePoint 首頁

-   搜尋中心

-   使用 SharePoint 搜尋 API 的自訂搜尋應用程式

### <a name="onedrive-for-business"></a>OneDrive for Business

多個地理位置環境已設定，如搜尋 OneDrive 中的使用者會從所有地理位置取得結果。

### <a name="delve"></a>Delve

多個地理位置環境已設定，如搜尋 Delve 中的使用者會從所有地理位置取得結果。

Delve 摘要與設定檔卡片只會顯示儲存在**中央**位置的檔案的預覽。衛星地理位置中儲存的檔案，該檔案類型的圖示顯示改用。

### <a name="the-sharepoint-home-page"></a>SharePoint 首頁

為多個地理位置環境已設定，使用者會看到新聞、 從在其 SharePoint 首頁] 頁面上的多個地理位置的最新和追蹤網站。如果他們在 SharePoint 首頁] 頁面上使用 [搜尋] 方塊中，他們將來自多個地理位置取得合併後的結果。

### <a name="the-search-center"></a>搜尋中心

在多個地理位置之後環境具有已設定從他們自己的地理位置的每個搜尋中心會繼續只顯示結果。系統管理員必須從所有地理位置取得結果的 [[變更每個搜尋中心的設定](#_Set_up_a_1)。之後，在搜尋中心搜尋使用者從所有地理位置取得結果。

### <a name="custom-search-applications"></a>自訂搜尋應用程式

像平常一樣自訂搜尋應用程式互動的搜尋索引使用現有的 SharePoint 搜尋 REST Api。若要從所有或部分的地理位置取得結果，將應用程式必須[呼叫 API 並加入新的多個地理位置查詢參數](#_Get_custom_search)要求中。這會觸發風扇移出所有地理位置的查詢。

## <a name="whats-different-about-search-in-a-multi-geo-environment"></a>什麼是關於多個地理位置環境中的搜尋不同？

您可能會先熟悉、 部分搜尋功能以不同方式運作多重地理位置環境中。

<table>
<thead>
<tr class="header">
<th align="left"><strong>功能</strong></th>
<th align="left"><strong>它的運作方式</strong></th>
<th align="left"><strong>因應措施</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">升級的結果</td>
<td align="left">您可以建立查詢規則升級的結果的不同層級： 整個租用戶、 網站集合或網站。在多個地理位置環境中，定義<strong>租用戶</strong>層級升級的結果如果您想要升級到<strong>所有</strong>地理位置中的搜尋中心的結果。如果您<strong>只</strong>想要提升結果在搜尋中心網站集合或網站的地理位置中，定義結果在<strong>網站集合</strong>或<strong>網站</strong>層級。</td>
<td align="left">如果您不需要不同升級的結果每個地理位置，例如不同的規則出差，建議您定義升級的租用戶層級的結果。</td>
</tr>
<tr class="even">
<td align="left">搜尋精簡器</td>
<td align="left">搜尋傳回從租用戶的所有地理位置的精簡器與然後彙總。彙總為最佳的能力，這表示精簡器計數可能不正確的 100%。對於大部分搜尋導向的情況，此正確性 」 即足以。</td>
<td align="left">搜尋導向應用程式相依於精簡器完整性的查詢每個地理位置單獨而不需使用多個地理位置送出。</td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left">多個地理位置搜尋不支援動態值區數值精簡器。</td>
<td align="left"><a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">"Discretize"參數</a>使用的數字的精簡器。</td>
</tr>
<tr class="even">
<td align="left">文件識別碼</td>
<td align="left">如果您正在開發搜尋導向的應用程式的文件識別碼而定，請注意在多個地理位置環境中的文件識別碼不唯一所有地理位置，他們是唯一的每個地理位置。</td>
<td align="left">我們已新增欄可識別的地理位置。若要達到重複使用此資料行。此欄名為"GeoLocationSource"。</td>
</tr>
<tr class="odd">
<td align="left">結果數目</td>
<td align="left">[搜尋結果] 頁面上顯示合併的結果的地理位置，但不能超過 500 結果] 頁面上。</td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a>在多個地理位置環境中的搜尋不支援項目？

一些您可能會先熟悉、 搜尋功能不支援多個地理位置環境中。

<table>
<thead>
<tr class="header">
<th align="left"><strong>搜尋功能</strong></th>
<th align="left"><strong>注意事項</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">僅限應用程式的驗證</td>
<td align="left">僅限應用程式的驗證 （從服務的權限存取） 不支援在多個地理位置搜尋。</td>
</tr>
<tr class="even">
<td align="left">訪客使用者</td>
<td align="left">訪客使用者只取得的地理位置，它們從搜尋結果。</td>
</tr>
</tbody>
</table>

## <a name="how-does-search-work-in-a-multi-geo-environment"></a>實務搜尋的運作方式在多個地理位置環境中

**所有**搜尋用戶端使用現有的 SharePoint 搜尋 REST Api 互動搜尋索引。
<img src="media/configure-search-for-multi-geo_image1-1.png" />

1. 搜尋用戶端會呼叫 EnableMultiGeoSearch 查詢屬性的搜尋 REST 端點 = true。
2. 查詢會傳送到租用戶中的所有地理位置。
3. 每個地理位置的搜尋結果會合併並排名。
4. 用戶端取得整合的搜尋結果。



<span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>請注意我們不合併搜尋結果直到我們已收到來自所有地理位置的結果。這表示多個地理位置的搜尋具有額外的延遲比較在只有一部地理位置的環境中的搜尋。

<span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
## <a name="get-a-search-center-to-show-results-from-all-geo-locations"></a>要取得以顯示所有地理位置的結果在搜尋中心

每個搜尋中心具有數個區域且您可以個別設定每個類別。

1.  請確定您執行這些步驟以具有編輯搜尋結果頁面和搜尋結果網頁組件的權限的帳戶。

2.  瀏覽至 [搜尋結果頁面 （請參閱[清單中](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213)的搜尋結果頁面）

3.  選取 [垂直若要設定，按一下 [**設定**齒輪圖示右上角，然後按一下 [**編輯頁面]**。在編輯模式中開啟的搜尋結果頁面。

     ![](media/configure-search-for-multi-geo_image2.png)
1.  在搜尋結果網頁組件，將滑鼠指標移至左上右上角的 [網頁組件按一下箭頭，然後再按一下其功能表上的 [**編輯網頁組件**。搜尋結果網頁組件工具窗格隨即開啟 [功能區中頂端右上方的頁面。![](media/configure-search-for-multi-geo_image3.png)

1.  在網頁組件] 工具窗格的 [**設定**] 區段的 [**結果控制設定**，請在選取**顯示多個地理位置結果**來取得搜尋結果網頁組件以顯示所有地理位置的結果。

2.  按一下**[確定]**以儲存變更並關閉 [網頁組件工具窗格。

3.  檢查您的變更搜尋結果網頁組件至主功能表的 [頁面] 索引標籤上按一下 [**存回**。

4.  使用中頁面頂端的附註所提供的連結發佈所做的變更。

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
## <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a>取得要顯示的所有或部分的地理位置結果的自訂搜尋應用程式

自訂搜尋應用程式與 SharePoint 搜尋 REST API 來要求指定查詢參數從所有或一些、 地理位置取得結果。根據的查詢參數，該查詢會扇形的所有地理位置，或某些地理位置。例如，如果您只需要查詢以尋找相關資訊的地理位置的子集，您可以控制延展至只有這些風扇。如果要求成功，SharePoint 搜尋 REST API 傳回回應資料。

### <a name="query-parameters"></a>查詢參數

EnableMultiGeoSearch-這是 Boolean 值，會指定是否查詢應扇形的其他地理位置的多個地理位置租用戶的索引。將它設為**true**可扇形查詢;**false**不扇形查詢。預設值為**false**。如果您未包含此參數，查詢是**不**扇形的其他地理位置。如果您不是多重地理位置環境中使用此參數，則會忽略此參數。

ClientType-這是一個字串。輸入每個搜尋應用程式的唯一用戶端名稱。如果您未包含此參數，查詢是**不**扇形的其他地理位置。

MultiGeoSearchConfiguration-這是選用清單中的哪個地理位置中多個地理位置承租人查詢扇形至**EnableMultiGeoSearch**時**，則為 true**。如果您未加上此參數，或保留空白，查詢被扇形所有地理位置的。針對每個地理位置 JSON 格式來輸入下列項目：

<table>
<thead>
<tr class="header">
<th align="left">項目</th>
<th align="left">描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">DataLocation</td>
<td align="left">地理位置，例如名稱。</td>
</tr>
<tr class="even">
<td align="left">端點</td>
<td align="left">連線至，例如端點https://contoso.sharepoint.com</td>
</tr>
<tr class="odd">
<td align="left">SourceId</td>
<td align="left">結果來源，例如 B81EAB55-3140-4312-B0F4-9459D1B4FFEE 的 GUID。</td>
</tr>
</tbody>
</table>

若您省略 DataLocation 或端點，或重複 DataLocation、 要求就會失敗。[您可以取得的使用 Microsoft Graph 租用戶地理位置端點的相關資訊](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery)。

### <a name="response-data"></a>回應資料

MultiGeoSearchStatus – 這是 「 SharePoint 搜尋 API 傳回以回應要求的屬性。屬性的值是一個字串並提供下列有關 SharePoint 搜尋 API 傳回結果的資訊：

<table>
<thead>
<tr class="header">
<th align="left">值</th>
<th align="left">描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">完整</td>
<td align="left">完整的<strong>所有</strong>結果的地理位置。</td>
</tr>
<tr class="even">
<td align="left">部分</td>
<td align="left">從一或多個地理位置的部分結果。結果就是暫時性錯誤導致未完成。</td>
</tr>

</tbody>
</table>

### <a name="query-using-the-rest-service"></a>使用 REST 服務的查詢

與 GET 要求，您可以指定查詢參數的 URL。與 POST 要求，您可以傳遞查詢參數的內文中 JavaScript Object Notation (JSON) 格式。

#### <a name="request-headers"></a>要求標頭

<table>
<thead>
<tr class="header">
<th align="left">名稱</th>
<th align="left">值</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Content-Type</td>
<td align="left">應用程式/json ； odata = 詳細資訊</td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a>扇形**所有**地理位置的範例 GET 要求

https://\<租用戶\>/\_api/搜尋/query?querytext = 'sharepoint' 屬性 = 'EnableMultiGeoSearch:true' & ClientType =' 我\_用戶端\_識別碼 '

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a>範例 GET 要求來扇形**一些**地理位置

https:// <tenant>/_api/search/query?querytext = '網站' & ClientType = 'my_client_id' 屬性 ='EnableMultiGeoSearch:true、 MultiGeoSearchConfiguration: [{DataLocation\:"名稱"\,端點\:"https\:contosoNAM.sharepoint.com"\,SourceId\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\,{DataLocation\:"可以"\,端點\:"https\://contosoCAN.sharepoint-df.com"}]'

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a>扇形**所有**地理位置的範例 POST 要求

    {
        "request": {
            "__metadata": {
            "type": "Microsoft.Office.Server.Search.REST.SearchRequest"
        },
        "Querytext": "sharepoint",
        "Properties": {
            "results": [
                {
                    "Name": "EnableMultiGeoSearch",
                    "Value": {
                        "QueryPropertyValueTypeIndex": 3,
                        "BoolVal": true
                    }
                }
            ]
        },
        "ClientType": "my_client_id"
        }
    }


#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a>扇形**一些**地理位置的範例 POST 要求


    {
        "request": {
            "Querytext": "SharePoint",
            "ClientType": "my_client_id",
            "Properties": {
                "results": [
                    {
                        "Name": "EnableMultiGeoSearch",
                        "Value": {
                            "QueryPropertyValueTypeIndex": 3,
                            "BoolVal": true
                        }
                    },
                    {
                        "Name": "MultiGeoSearchConfiguration",
                        "Value": {
                        "StrVal": "[{\"DataLocation\":\"NAM\",\"Endpoint\":\"https://contoso.sharepoint.com\",\"SourceId\":\"B81EAB55-3140-4312-B0F4-9459D1B4FFEE\"},{\"DataLocation\":\"CAN\",\"Endpoint\":\"https://contosoCAN.sharepoint.com\"}]",
                            "QueryPropertyValueTypeIndex": 1
                        }
                    }
                ]
            }
        }
    }

### <a name="query-using-csom"></a>使用 CSOM 的查詢

以下是對**所有**地理位置扇形範例 CSOM 查詢：

    var keywordQuery = new KeywordQuery(ctx);
    keywordQuery.QueryText = query.SearchQueryText;
    keywordQuery.ClientType = <enter a string here>;
    keywordQuery["EnableMultiGeoSearch"] = true;

