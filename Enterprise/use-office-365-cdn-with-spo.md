---
title: 使用 SharePoint Online 透過使用 Office 365 內容傳遞網路
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: bebb285f-1d54-4f79-90a5-94985afc6af8
description: 說明如何使用 Office 365 內建內容傳遞網路 (CDN) 以加速您的 SharePoint Online 資產傳遞至您的所有使用者不論它們的所在位置或如何存取您的內容。
ms.openlocfilehash: 958f01419a74e4b8cd007b2627585884496bdfdf
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539960"
---
# <a name="use-the-office-365-content-delivery-network-with-sharepoint-online"></a>使用 SharePoint Online 透過使用 Office 365 內容傳遞網路

您可以架設靜態資產在 Office 365 內容傳遞網路 (CDN) 提供較佳的效能的 SharePoint Online 頁面。靜態資產是並不會像圖像、 視訊和音訊、 樣式表、 字型和 JavaScript 檔案非常經常變更的檔案。CDN 運作的地理位置分散的快取 proxy，以透過快取靜態資產更接近來要求他們的瀏覽器。 
  
如果您已熟悉 Cdn 運作的方式，您只需要完成幾個步驟來設定它。本主題說明如何。閱讀 Office 365 CDN 與如何開始架設靜態的資產的資訊。
  
 **標題回[網路規劃和 Office 365 的效能調整](https://aka.ms/tune)。**
  
## <a name="office-365-cdn-basics"></a>Office 365 CDN 基礎 （英文)

Office 365 CDN 是包括作為您的 SharePoint Online 訂閱的一部分。您不需要額外工資它。Office 365 提供的這兩個私用支援與公用存取與可讓您將多個位置或來源中的主機靜態資產。Office 365 CDN 不 Azure CDN 相同。如果您需要有關為何使用 CDN 或 CDN 的一般概念的詳細資訊，請參閱[內容傳遞網路](content-delivery-networks.md)。
  
## <a name="how-the-cdn-grants-access-to-end-users"></a>如何 CDN 授與存取權的使用者

在 Office 365 CDN 靜態資產私人存取被授與所產生的 SharePoint Online 的 token。已經有存取權的資料夾或指定的原始文件庫的權限的使用者將會自動授與 token。SharePoint Online 不支援項目層級權限的 CDN。
  
例如，其位於檔案的`https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`，授與下列：
  
- 使用者 1 具有存取資料夾 1 和 image1.jpg
    
- 使用者 2 沒有存取權資料夾 1
    
- 使用者 3 沒有存取權資料夾 1，但會授與存取 image1.jpg 透過 SharePoint Online 的明確權限
    
- 使用者 4 可存取資料夾 1，但已明確拒絕存取 image1.jpg
    
再下面是，則為 true：
  
- 使用者 1 和使用者 4 將能夠透過 CDN 存取 image1.jpg。
    
- 使用者 2 和 3 使用者將不能夠透過 CDN 存取 image1.jpg。
    
    不過，使用者 3 仍然可以存取資產 image1.jpg 直接透過 SharePoint Online 時使用者 4 無法透過 SharePoint Online 存取資產。
    
## <a name="overview-of-working-with-the-office-365-cdn"></a>使用 Office 365 CDN 的概觀 （英文)

若要設定 Office 365 CDN，您可以遵循下列基本步驟：
  
- 規劃 CDN 部署：
    
  - 決定要架設在 Office 365 CDN 哪些靜態資產。如需如何進行這些選項的詳細資訊，請參閱[內容傳遞網路](content-delivery-networks.md)。
    
  - [決定您要儲存您的資產的位置](use-office-365-cdn-with-spo.md#CDNStoreAssets)。此位置為資料夾或 SharePoint 文件庫及稱為原點而言。
    
  - 決定是否應進行公用或保密資產。執行此當您[選擇每個原點是否應該是公用或是私人](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)。如果您希望您有多個來源部分是公用的且某些私人。
    
- [設定及使用 SharePoint Online 管理命令介面來設定 Office 365 CDN](use-office-365-cdn-with-spo.md#CDNSetupinPShell)。當您完成此步驟時，您必須：
    
  - 啟用您的組織 CDN。
    
  - 新增您的來源。您識別每個公用或私人的原點而言。
    
一次完成設定，[管理 Office 365 CDN](use-office-365-cdn-with-spo.md#CDNManage)一段時間的： 
  
- 新增、 更新及移除資產
    
- 新增和移除來源
    
- 設定 CDN 原則
    
- 必要時，停用 Office 365 CDN
    
## <a name="determine-where-you-want-to-store-your-assets"></a>決定您要儲存您的資產的位置

CDN 擷取您資產從呼叫原點的位置。Office 365 的原點而言是 SharePoint 文件庫或資料夾可存取的 URL。當您指定貴組織來源，您有極大的彈性。例如，您可以指定多個來源或您要將所有的 CDN 資產單一原點而言。您可以選擇讓組織的公用或私人來源。大部分組織會選擇實作兩者的組合。
  
如果您定義數百個來源，則它可能會造成負面影響上處理要求所花費的時間。建議您如果您有 100 個以上約來源可能會想要重新思考您的架構。
  
## <a name="choose-whether-each-origin-should-be-public-or-private"></a>選擇每個原點是否應該是公用或是私人

當您識別的原點而言時，您指定是否應該讓它成為公用或私人。無論您選擇哪個選項，Microsoft 粗活您時執行專職 CDN 本身的管理。此外，您可以稍後改變心意之後您已設定好 CDN 並識別您的來源。
  
公用及私人選項提供效能改良功能，但每個具有唯一的屬性及優點。
  
 **Attributes 及代管公用原點的資產的優點**
  
- 公用原點中公開的資產是匿名存取的所有人。
    
    > [!IMPORTANT]
    > 如果您在您 CDN 識別公用的原點而言，您應該永不放置被視為機密組織公用原點或 SharePoint Online 的文件庫中的資源。 
  
- 如果您從公用原點移除資產，資產可能會繼續可達 30 天的從快取;不過，我們將會失效中 CDN 資產的連結 15 分鐘內。
    
- 當您架設在公用原點的樣式表 （CSS 檔案） 時，您可以使用程式碼內的相對路徑和 Uri。這表示您可以參考背景影像及其他物件呼叫資產的位置相對的位置。
    
- 雖然您可以硬式編碼公用原點的 URL，這麼做讓不建議。這原因是如果存取 CDN 變成無法使用，URL 不會自動解決您在 SharePoint Online 的組織可能會導致中斷的連結及其他錯誤。
    
- 預設的檔案類型所包含的公用來源是.css、.eot、.gif、.ico、.jpeg、.jpg、.js、.map、.png、.svg、.ttf 及.woff。您可以指定其他檔案類型。
    
- 如果您想，您可以設定原則以排除經過識別所指定的網站分類的資產。例如，您可以選擇要排除即使所允許的檔案類型，且位於公用的原點而言標示為"confidential"或"受限"的所有資產。
    
 **Attributes 及架設在私人原點資產的優點**
  
- 如果他們獲得授權所這麼使用者僅可從私人原點存取資產。為避免這些資產的匿名存取。
    
- 如果您移除私人原點的資產，資產可能會繼續以供最多個小時從快取;不過，我們將會失效中 CDN 資產的連結 15 分鐘內。
    
- 預設的檔案類型所包含的私人來源是.gif、.ico、.jpeg、.jpg、.js、 及.png。您可以指定其他檔案類型。
    
- 就像是公用來源，您可以設定原則以排除經過識別由您指定即使您使用萬用字元包含資料夾或網站文件庫內的所有資產的網站分類的資產。
    
## <a name="default-office-365-cdn-origins"></a>預設 Office 365 CDN 來源

除非您指定否則 Office 365 設定某些預設來源您啟用 Office 365 CDN 時。如果您一開始排除它們，您可以新增這些來源之後完成安裝程式。
  
預設私人來源：
  
- \*/userphoto.aspx
    
- \*/siteassets
    
預設公用來源：
  
- \*/masterpage
    
- \*/style 文件庫
    
## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a>安裝及使用 SharePoint Online 管理命令介面來設定 Office 365 CDN

本主題中的程序需要您用來連線至 SharePoint Online 的 SharePoint Online 管理命令介面。指示，請參閱[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)。
  
完成下列步驟來安裝及設定 Office 365 CDN，來裝載您在 SharePoint Online 中的靜態資產。
  
### <a name="to-enable-your-organization-to-use-the-office-365-cdn"></a>若要啟用貴組織要使用 Office 365 CDN

若要啟用貴組織要使用 Office 365 CDN 使用**組 SPOTenantCdnEnabled**指令程式。您可以啟用使用公用來源、 私人來源或兩者 CDN 與貴組織。您也可以設定當您啟用時略過的預設值來源安裝 Office 365 CDN。永遠稍後可以新增這些來源本主題所述。 
  
在 SharePoint Online 的 Windows Powershell：
  
```
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

例如，若要啟用貴組織要 CDN 搭配使用公用及私人來源，請輸入下列命令：
  
```
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

若要啟用您的組織使用 CDN 公用及私人來源，但是略過預設來源設定，請輸入下列命令：
  
```
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

若要讓 CDN 搭配使用公用來源貴組織，請輸入下列命令：
  
```
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

若要啟用貴組織要搭配 CDN 使用私人來源，輸入下列命令：
  
```
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

如需此 cmdlet 的詳細資訊，請參閱 ＜[設定 SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx)。
  
### <a name="optional-to-change-the-list-of-file-types-to-include-in-the-office-365-cdn"></a>（選用）若要變更的 Office 365 CDN 中所包含的檔案類型清單
<a name="Office365CDNforSPOFileType"> </a>

> [!TIP]
> 當您使用**組 SPOTenantCdnPolicy**指令程式定義的檔案類型時，您會覆寫目前所定義的清單。如果您想要新增其他檔案類型至清單，此指令程式先使用來了解新的檔案類型已允許與納入以及在新的清單。 
  
使用此**組 SPOTenantCdnPolicy**指令程式可以定義可以由公用及私人來源 CDN 中主控的靜態檔案類型。根據預設，常見的資產類型允許、 範例.css、.gif、.jpg、 及.js。 
  
在 SharePoint Online 的 Windows PowerShell：
  
```
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

如需依 CDN 目前允許哪些檔案類型，請使用**Get SPOTenantCdnPolicies**指令程式： 
  
```
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

如需這些 cmdlet 的詳細資訊，請參閱[設定 SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx)和[取得 SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx)。
  
### <a name="optional-to-change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a>（選用）若要變更的網站分類您想要從 Office 365 CDN 排除清單
<a name="Office365CDNforSPOSiteClassification"> </a>

> [!TIP]
> 當您使用此**組 SPOTenantCdnPolicy**指令程式來排除網站分類時，覆寫目前所定義的清單。如果您想要排除其他網站分類，指令程式先使用來找出哪些分類已排除和再將它們新增與您新的 api。 
  
使用**組 SPOTenantCdnPolicy**指令程式來排除不想讓 CDN 透過網站分類。根據預設，不排除任何網站分類。 
  
在 SharePoint Online 的 Windows PowerShell：
  
```
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

若要查看哪些網站分類是目前受限制，使用**Get SPOTenantCdnPolicies**指令程式： 
  
```
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

如需這些 cmdlet 的詳細資訊，請參閱[設定 SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx)和[取得 SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx)。
  
### <a name="to-add-an-origin-for-your-assets"></a>若要新增您資產的原點
<a name="Office365CDNforSPOOrigin"> </a>

使用**Add SPOTenantCdnOrigin**指令程式定義的原點而言。您可以定義多個來源。原點是指向 SharePoint 文件庫或資料夾包含您要主控的 CDN 資產的 URL。 
  
> [!IMPORTANT]
> 如果您在您 CDN 識別公用的原點而言，您應該永不放置被視為機密組織公用原點或 SharePoint Online 的文件庫中的資源。 
  
```
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path >
```

其中路徑是包含資產的資料夾路徑。您可以使用萬用字元除了相對路徑。例如，將包含資產的所有網站的所有 masterpages 資料夾中為公用原點 CDN 內，輸入下列命令：
  
```
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

如需此命令和語法的詳細資訊，請參閱 ＜ [Add SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)。
  
一旦您已執行命令，系統會跨資料中心同步處理設定。這需要 15 分鐘。
  
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>範例： 設定用於您的主版頁面和樣式庫公用原點的 SharePoint Online
<a name="ExamplePublicOrigin"> </a>

一般而言，這些來源是設定為您預設時您的 Office 365 CDN 啟用公用的來源。不過，如果您想要手動啟用它們，請遵循下列步驟。
  
- 使用**Add SPOTenantCdnOrigin**指令程式可以定義樣式庫作為 Office 365 CDN 內公用原點而言。 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

- 使用**Add SPOTenantCdnOrigin**指令程式定義為 Office 365 CDN 內公用原點的主版頁面。 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

- 如需此命令和語法的詳細資訊，請參閱 ＜ [Add SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)。
    
    一旦您已執行命令，系統會跨資料中心同步處理設定。這需要 15 分鐘。
    
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>範例： 設定網站資產、 網站頁面及發佈圖像私人原點的 SharePoint Online
<a name="ExamplePrivateOrigin"> </a>

- 使用**Add SPOTenantCdnOrigin**指令程式定義為私人的原點而言 Office 365 CDN 內的 [網站資產] 資料夾。 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

- 使用**Add SPOTenantCdnOrigin**指令程式為 Office 365 CDN 內私人原點定義網站的 [頁面] 資料夾。 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

- 使用**Add SPOTenantCdnOrigin**指令程式定義為 Office 365 CDN 內私人原點的發佈的 [圖像] 資料夾。 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

    如需此命令和語法的詳細資訊，請參閱 ＜ [Add SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)。
    
    一旦您已執行命令，系統會跨資料中心同步處理設定。這需要 15 分鐘。
    
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>範例： 設定網站集合的私人原點的 SharePoint Online
<a name="ExamplePrivateOriginSiteCollection"> </a>

若要定義為 Office 365 CDN 內私人原點的網站集合使用**新增 SPOTenantCdnOrigin**指令程式。例如， 
  
```
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

如需此命令和語法的詳細資訊，請參閱 ＜ [Add SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)。
  
一旦您已執行命令，系統會跨資料中心同步處理設定。這需要 15 分鐘。
  
## <a name="manage-the-office-365-cdn"></a>管理 Office 365 CDN
<a name="CDNManage"> </a>

一旦您已經設定好 CDN，您可以變更您的設定更新的內容或您需要變更，如本節所述。
  
### <a name="to-add-update-or-remove-assets-from-the-office-365-cdn"></a>若要新增、 更新或移除 Office 365 CDN 資產
<a name="Office365CDNforSPOaddremoveasset"> </a>

一旦您已經完成設定步驟，您可以新增新的資產和更新或每當您想要移除現有的資產。只對您識別為原點的 SharePoint 文件庫資料夾中的資產進行變更。如果您新增新的資產，最好是可透過 CDN 立即。不過，如果您更新資產，它會需要最多 15 分鐘傳播及成為 CDN 中可用的新複本的。
  
如果您需要擷取原點的位置，您可以使用**Get SPOTenantCdnOrigins**指令程式。如需如何使用此指令程式，請參閱 ＜ [Get SPOTenantCdnOrigins](https://technet.microsoft.com/en-us/library/mt790770.aspx)。
  
### <a name="to-remove-an-origin-from-the-office-365-cdn"></a>若要從 Office 365 CDN 移除原點
<a name="Office365CDNforSPORemoveOrigin"> </a>

如果您需要，您可以移除資料夾或您已識別為原點的 SharePoint 文件庫的存取權。為達成此目的，使用 [**移除 SPOTenantCdnOrigin**指令程式。如需如何使用此指令程式，請參閱 ＜ [Remove SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx)。
  
### <a name="to-modify-an-origin-in-the-office-365-cdn"></a>若要修改在 Office 365 CDN 原點
<a name="Office365CDNforSPORemoveOrigin"> </a>

您無法修改已建立的原點而言。而移除原點然後再新增一個新。如需詳細資訊，請參閱[移除從 Office 365 CDN 原點](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin)並[新增您資產的原點而言](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin)。
  
### <a name="to-disable-the-office-365-cdn"></a>若要停用 Office 365 CDN
<a name="Office365CDNforSPODisable"> </a>

若要停用組織的 CDN 使用**組 SPOTenantCdnEnabled**指令程式。如果您有兩個公用及私人來源 CDN 啟用，您需要執行此指令程式兩次如下列範例所示。 
  
若要停用使用 CDN 中使用 Windows Powershell for SharePoint Online 中公用來源輸入下列命令：
  
```
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

若要停用使用中 CDN 私用的來源，請輸入下列命令：
  
```
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

如需此 cmdlet 的詳細資訊，請參閱 ＜[設定 SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx)。
  
## <a name="troubleshooting-your-office-365-cdn-configuration"></a>疑難排解 Office 365 CDN 組態
<a name="CDNManage"> </a>

端點會立即無法使用，如下所花的時間傳播到 CDN 註冊的。設定會在 15 分鐘。
  

