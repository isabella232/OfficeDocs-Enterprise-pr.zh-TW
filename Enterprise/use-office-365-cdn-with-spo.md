---
title: 使用 Office 365 內容傳遞網路 (CDN) 搭配 SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/2/2019
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
description: 說明如何使用 Office 365 內容傳遞網路 (CDN) 來加快 SharePoint Online 的資產傳遞至您的所有使用者不論它們的所在位置，或使用者如何存取您的內容。
ms.openlocfilehash: a718c30a40209a8ee0c8e78700ed3eae72c8347c
ms.sourcegitcommit: 43d2b7e1d9932182c6cca5164d4d9096dcf4ed36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "31039500"
---
# <a name="use-the-office-365-content-delivery-network-cdn-with-sharepoint-online"></a>使用 Office 365 內容傳遞網路 (CDN) 搭配 SharePoint Online

您可以使用內建的 Office 365 內容傳遞網路 (CDN) 來主控靜態資產，為您的 SharePoint網頁提供更佳的效能。 Office 365 CDN 透過將靜態資產快取到更靠近提出要求之瀏覽器的位置 (這有助於加速下載以及減少延遲)，藉此改善效能。 此外，Office 365 CDN 改善的壓縮和 HTTP 管線使用[HTTP/2 通訊協定](https://en.wikipedia.org/wiki/HTTP/2)。 Office 365 CDN 服務包含在 SharePoint Online 訂閱的一部分。

Office 365 CDN 是由可讓您在多個位置或_來源_主控靜態資產的多個 CDN 組成，並透過全球高速網路提供資產。 根據您要在 Office 365 CDN 中主控的內容類型而定，您可以新增**公用**來源、**私人**來源或兩者。 如需公用和私人原點之間的差異的詳細資訊，請參閱[選擇每個原始來源是否應該是公用或私人](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)。

![Office 365 CDN 概念圖](media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN 概念圖")

如果您已熟悉 Cdn 的方式，您只需要完成啟用 CDN 將 Office 365 租用戶的幾個步驟。 本主題說明如何。 閱讀如何開始主控您的靜態資產的相關資訊。

> [!TIP]
> 有其他 Microsoft 主控的 Cdn 可用於 Office 365 的特殊的使用情況，但會在因為他們屬於超出 Office 365 CDN 的範圍不在本主題討論。 如需詳細資訊，請參閱 <<c0>其他 Microsoft Cdn。

 **Head 回[網路規劃和效能調整的 Office 365](https://aka.ms/tune)。**

## <a name="overview-of-working-with-the-office-365-cdn-in-sharepoint-online"></a>使用 SharePoint Online 中 CDN 將 Office 365 的概觀

若要設定為您的組織 CDN 將 Office 365，您可以遵循下列基本步驟：

- [規劃部署 Office 365 CDN](use-office-365-cdn-with-spo.md#plan-for-deployment-of-the-office-365-cdn)

  - [決定您想要在 CDN 上裝載的靜態資產](use-office-365-cdn-with-spo.md#CDNAssets)。
  - [決定您想要用來儲存您的資產](use-office-365-cdn-with-spo.md#CDNStoreAssets)。 此位置可以是 SharePoint 網站、 文件庫或資料夾，並呼叫_原點_。
  - [選擇 [每個原始來源是否應該是公用或私人](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)。 您可以新增多個公用和私人類型的原點。

- 安裝及設定 CDN，使用 PowerShell 或 SharePoint Online CLI

  - [安裝及使用 SharePoint Online 管理命令介面設定 CDN](use-office-365-cdn-with-spo.md#CDNSetupinPShell)
  - [安裝及使用 Office 365 CLI 設定 CDN](use-office-365-cdn-with-spo.md#CDNSetupinCLI)

  當您完成此步驟時，您必須：

  - 啟用組織 CDN。
  - 新增您的原點，用來識別為公用或私人每個原始來源。

一旦您完成安裝程式，您可以[管理 Office 365 CDN](use-office-365-cdn-with-spo.md#CDNManage)經過一段時間的：
  
- 新增、 更新及移除資產
- 新增及移除原點
- 設定 CDN 原則
- 如有必要，停用 CDN

最後，請參閱 < 若要了解公用及私人原點從存取 CDN 資產<b0>使用 CDN 資產</b0>。

如需解決一般問題的指導，請參閱[疑難排解 Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) 。

## <a name="plan-for-deployment-of-the-office-365-cdn"></a>規劃部署 Office 365 CDN

您的 Office 365 租用戶部署 Office 365 CDN 之前，您應該考量下列因素規劃程序的一部分。

  - [決定您想要在 CDN 上裝載的靜態資產](use-office-365-cdn-with-spo.md#CDNAssets)
  - [決定您想要用來儲存您的資產](use-office-365-cdn-with-spo.md#CDNStoreAssets)
  - [選擇 [每個原始來源是否應該是公用或私用](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)

### <a name="determine-which-static-assets-you-want-to-host-on-the-cdn"></a>決定您想要在 CDN 上裝載的靜態資產
<a name="CDNAssets"> </a>

在 [一般] Cdn 是以架設_靜態資產_或未經常變更的資產最為有用。 好用的經驗法則是找出符合部分或所有的這些條件的檔案：

- 靜態檔案內嵌在頁面 （例如指令碼和圖像），可能會造成重大的累加影響的頁面載入時間
- 大型檔案一樣的可執行檔和安裝檔案
- 資料流的媒體檔案
- 支援用戶端程式碼的資源庫

例如，便會重複替換要求網站圖像和指令碼等的小型檔案可以大幅改善網站呈現效能，而逐漸減少在 SharePoint Online 網站上的負載，當您將它們新增至 CDN 原點。 可以下載較大的檔案，例如安裝可執行檔或視訊檔案，或從 CDN，即使未經常存取它們傳遞誤判的效能影響和後續降低您的 SharePoint Online 網站上的負載以串流方式傳送。

每個檔案為基礎的效能改進是取決於許多因素，包括至最接近的 CDN 端點，用戶端的近似值暫時性條件的區域網路，依此類推。 許多靜態檔案很小，且可從 Office 365 下載少於一秒。 不過，網頁可能包含許多嵌入的檔案，並幾秒鐘的累計下載時間。 從 CDN 提供這些檔案，可大幅降低整體的頁面載入時間。 請參閱[，可提升何種效能沒有 CDN 提供？](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide)範例。

### <a name="determine-where-you-want-to-store-your-assets"></a>決定您想要用來儲存您的資產
<a name="CDNStoreAssets"> </a>

CDN 擷取您資產從呼叫_原點_的位置。 原始來源可以是 SharePoint 網站、 文件庫或資料夾可供存取的 URL。 當您指定原點為您的組織，您會有很大的彈性。 例如，您可以指定多個原點或想要將所有的 CDN 資產單一原點。 您可以選擇讓組織的公用或私人原點。 大多數組織會選擇實作兩者的組合。

您可以為您原點資料夾或文件庫，例如建立新的容器，並新增您想要提供從 CDN 的檔案。 如果您有一組特定的資產您想要從 CDN，可用，而且想要限制只有在容器檔案 CDN 資產的集合，這是一個好的方法。

您也可以設定現有網站集合、 網站、 文件庫或資料夾為原點，會讓所有合格的資產容器中可從 CDN。 您將現有的容器新增為原始來源之前，請務必確定您是知道其內容和權限，所以您不小心公開資產的匿名存取或未經授權的使用者。

您可以定義_CDN 原則_，以從 CDN 排除您原點中的內容。 CDN 原則排除_檔案類型_及_網站分類_，例如屬性中公用或私人原點資產，且會套用至所有原點的原則中指定 CdnType （私人或公用）。 例如，如果您新增包含多個子網站的網站所組成的私用原始來源，您可以定義要排除標示為 [ **2 私人 3 機密**因此內容從站台分類套用從 CDN 將不會服務的站台的原則。 此原則會套用到內容，從_所有_在您新增至 CDN 的私用原點。
  
請記住，原點數目愈大，時間影響也愈大花費 CDN 服務來處理要求。 我們建議您盡可能原點的數目限制。
  
### <a name="choose-whether-each-origin-should-be-public-or-private"></a>選擇 [每個原始來源是否應該是公用或私用
<a name="CDNOriginChoosePublicPrivate"> </a>

當您識別來源時，指定是否應該讓它成為_公用_或_私人_。 存取在公用的原點的 CDN 資產為匿名，並在私人原點的 CDN 內容受到動態產生的語彙基元的較高的安全性。 不論您選擇哪個選項，Microsoft 會所有工作都為您談到 CDN 本身的管理。 此外，您可以稍後改變心意之後您已設定 CDN 並找出您原點。

公用及私人選項提供類似的效能提升，但每個具有唯一的屬性及優點。

匿名，都可以存取**公用**原點 CDN 將 Office 365 內，且主控的資產可以存取資產之 url 的任何人。 因為對公用來源中內容的存取是匿名的，您應該只使用公用來源來快取非敏感性的一般內容，例如 javascript 檔案、指令碼、圖示和影像。

Office 365 CDN 內的**私人**來源可提供使用者內容 (例如 SharePoint Online 文件庫、網站和視訊等媒體) 的私人存取。 私用原點中內容的存取權受到以動態方式產生的 token，讓其可以只存取與原始文件的文件庫或儲存位置的權限的使用者。 CDN 將 Office 365 中的私人原點僅可用於 SharePoint Online 內容，您只可以存取透過重新導向私人原點的資產，從您的 SharePoint Online 租用戶。

您可以閱讀需 CDN 如何存取私用的原始來源中的資產中[使用資產私人原點中的](use-office-365-cdn-with-spo.md#using-assets-in-private-origins)運作。

#### <a name="attributes-and-advantages-of-hosting-assets-in-public-origins"></a>屬性和裝載在公用的原點的資產的優點
  
- 在公用的原點中公開的資產皆可存取所有人匿名。
    > [!IMPORTANT]
    > 您應該永遠不會將含有使用者資訊或會被視為機密至您的組織中公用的原始來源資源。
- 如果您移除公用原點的資產，資產可能可繼續運作最多 30 天從快取;不過，我們會在 15 分鐘內失效 CDN 中資產的連結。
- 當您裝載在公用的原始來源中的樣式表 （CSS 檔案） 時，您可以使用程式碼內的相對路徑與 Uri。 這表示您可以參照背景影像及其他物件呼叫它的資產的位置相對的位置。
- 雖然您可以硬式編碼公用原始來源的 URL，這種做法所以不建議。 這是如果存取 CDN 變成無法使用，URL 不會自動解決您在 SharePoint Online 中的組織，可能會導致中斷的連結和其他錯誤。
- 預設檔案類型，可供公用原點的.css、.eot、.gif、.ico、.jpeg、.jpg、.js、.map、.png、.svg、.ttf 和.woff。 您可以指定其他檔案類型。
- 您可以設定要排除的已識別由您所指定網站分類資產的原則。 例如，您可以選擇要排除所有的資產，即使他們所允許的檔案類型，並位於公用原點標示為 「 機密 」 或 「 限制 」。

#### <a name="attributes-and-advantages-of-hosting-assets-in-private-origins"></a>屬性和裝載在私人原點的資產的優點

- 私用原點只能用於 SharePoint Online 的資產。
- 如果他們有權限來存取容器使用者僅可從私人原點存取資產。 無法對這些資產的匿名存取。
- 在私人原點的資產必須參照從 SharePoint Online 租用戶。 直接存取私人 CDN 資產無法運作。
- 如果您從私人原點移除資產，資產可能會繼續以供最多一個小時的時間從快取;不過，我們將會失效中 CDN 資產的連結的資產的移除 15 分鐘內。
- .Gif、.ico、.jpeg、.jpg、.js、 和.png，就會是針對私人原點所包含的預設檔案類型。 您可以指定其他檔案類型。
- 就像公用原點，您可以設定要排除已透過網站分類，即使您使用萬用字元來包含所有的資產資料夾或文件庫內指定識別的資產的原則。

如需為使用 Office 365 CDN、 一般 CDN 概念，以及您可以使用與 Office 365 租用戶其他 Microsoft Cdn 原因的詳細資訊，請參閱 <<c0>內容傳遞網路。

### <a name="default-cdn-origins"></a>預設 CDN 原點

除非另有指定，Office 365 會設定某些預設原點您當您啟用 Office 365 CDN。 如果您最初選擇不適用於佈建它們，您可以在您完成設定後新增這些原點。 除非您了解的略過的預設原點安裝方法的結果，並有這樣的特定原因，您應允許他們要建立當您啟用 CDN。
  
私人 CDN 原點預設值：
  
- \*/userphoto.aspx
- \*/siteassets

公用 CDN 原點預設值：
  
- \*/masterpage
- \*/style 文件庫
- \*/clientsideassets

> [!NOTE]
> _clientsideassets_是已在 2017 年 12 月加到 Office 365 CDN 服務預設公用原點。 此來源必須要有 SharePoint 架構中以解決方案 CDN 工作的順序。 如果您啟用 Office 365 CDN 年 12 月 2017 年之前，或當您啟用 CDN 略過的預設原點的安裝程式，您可以手動新增此原點。 如需詳細資訊，請參閱[我的用戶端網頁組件或 SharePoint 架構解決方案無法正常運作](use-office-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working)。

## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a>設定及使用 SharePoint Online 管理命令介面來設定 Office 365 CDN
<a name="CDNSetupinPShell"> </a>

本節中的程序需要您使用 SharePoint Online 管理命令介面來連線至 SharePoint Online。 如需相關指示，請參閱[連線到 SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)。
  
完成下列步驟來安裝及設定以裝載您在 SharePoint Online 使用 SharePoint Online 管理命令介面中的資產 CDN。
  
### <a name="enable-your-organization-to-use-the-office-365-cdn"></a>啟用您的組織使用 Office 365 CDN

您的租用戶 CDN 設定進行變更之前，您應該在您的 Office 365 租用戶中擷取私人 CDN 組態的目前狀態。 連線至您的租用戶使用 SharePoint Online 管理命令介面：

``` powershell
Connect-SPOService -Url https://contoso-admin.sharepoint.com
```

現在可用於**取得 SPOTenantCdnEnabled**指令程式從租用戶擷取 CDN 狀態設定：

``` powershell
Get-SPOTenantCdnEnabled -CdnType <Public | Private>
```

針對指定 CdnType CDN 的狀態將會輸出至畫面。

使用**設定 SPOTenantCdnEnabled**指令程式來啟用您的組織使用 Office 365 CDN。 您可以啟用您的組織，一次使用公用原點、 私人原點，或兩者。 您也可以設定略過的預設原點安裝程式，當您啟用 CDN。 您隨時可以稍後在本主題中所述加入這些原點。
  
在 SharePoint Online 的 Windows Powershell:

``` powershell
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

例如，若要啟用您的組織使用公開及私密原點，請輸入下列命令：

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

若要啟用您的組織使用公開及私密原點，但略過預設原點的設定，請輸入下列命令：

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

當您啟用 Office 365 CDN，並略過的預設原點安裝的潛在影響預設佈建原點的相關資訊，請參閱[預設 CDN 原點](use-office-365-cdn-with-spo.md#default-cdn-origins)。

若要啟用您的組織使用公用原點，請輸入下列命令：

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

若要啟用您的組織使用私人的原點，請輸入下列命令：

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

如需此 cmdlet 的詳細資訊，請參閱 <<c0>設定 SPOTenantCdnEnabled。
  
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a>變更要在 Office 365 CDN （選用） 中包含檔案類型的清單
<a name="Office365CDNforSPOFileType"> </a>

> [!TIP]
> 當您使用**組 SPOTenantCdnPolicy** cmdlet 定義的檔案類型時，您覆寫目前所定義的清單。 如果您想要新增其他檔案類型至清單時，指令程式先使用來找出哪些檔案類型已允許納入以及您新的清單。
  
使用**設定 SPOTenantCdnPolicy**指令程式來定義可由公用和私人原點 CDN 中主控的靜態檔案類型。 根據預設，常見的資產類型為何，允許範例.css、.gif、.jpg、 及.js。

在 SharePoint Online 的 Windows PowerShell:

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

例如，若要啟用 CDN 主機.css 和.png 檔案，您輸入此命令：

``` powershell
Set-SPOTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

若要查看 CDN 目前允許哪些檔案類型，請使用**Get SPOTenantCdnPolicies** cmdlet:

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

如需這些 cmdlet 的詳細資訊，請參閱[設定 SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx)和[取得 SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx)。
  
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a>變更您想要排除在 Office 365 CDN （選用） 的網站分類的清單
<a name="Office365CDNforSPOSiteClassification"> </a>

> [!TIP]
> 您可以使用**組 SPOTenantCdnPolicy**指令程式，以排除網站分類，當您覆寫目前所定義的清單。 如果您想要排除其他網站分類，使用以找出已被排除哪些分類並再將其新增以及您新的第一次的指令程式進行。

使用**組 SPOTenantCdnPolicy**指令程式來排除不想要提供透過 CDN 的網站分類。 根據預設，會不排除任何網站分類。

在 SharePoint Online 的 Windows PowerShell:

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

若要查看哪些網站分類目前受到限制，請使用**Get SPOTenantCdnPolicies** cmdlet:

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

會傳回的屬性，而_IncludeFileExtensions_、 _ExcludeRestrictedSiteClassifications_ _ExcludeIfNoScriptDisabled_。

_IncludeFileExtensions_屬性包含將服務從 CDN 的副檔名清單。

> [!NOTE]
> 預設的副檔名的方式不同公用和私人之間。

_ExcludeRestrictedSiteClassifications_屬性會包含您想要排除從 CDN 網站分類。 例如，您可以排除標示為 [ **2 私人 3 機密**因此內容從站台分類套用從 CDN 將不會服務的網站。

_ExcludeIfNoScriptDisabled_屬性會從網站層級_NoScript_屬性設定為基礎的 CDN 排除內容。 根據預設， _NoScript_屬性設為 [**已啟用**_新式_網站和**已停用**的_傳統_網站。 這取決於您的租用戶設定。

如需這些 cmdlet 的詳細資訊，請參閱[設定 SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx)和[取得 SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx)。
  
### <a name="add-an-origin-for-your-assets"></a>新增您資產的原始來源
<a name="Office365CDNforSPOOrigin"> </a>

使用**Add SPOTenantCdnOrigin**指令程式來定義原點。 您可以定義多個原點。 原點是指向 SharePoint 文件庫或資料夾，其中包含您想要裝載的 CDN 資產的 URL。
  
> [!IMPORTANT]
> 您應該永遠不會將含有使用者資訊或會被視為機密至您的組織中公用的原始來源資源。

``` powershell
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

_路徑_的值是文件庫或資料夾，其中包含資產的路徑。 您可以使用萬用字元，除了相對路徑。 原點支援加至 URL 的萬用字元。 這可讓您建立橫跨多個站台的原點。 例如，若要包含在所有網站的 masterpages 資料夾中的所有資產內 CDN 公開原點，輸入下列命令：

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

- 萬用字元修飾詞 ***/** 只用於起點處的路徑，並會比對 [指定 URL] 下的所有 URL 區段。
- 路徑可以指向文件庫、 資料夾或網站。 例如，路徑 _* / site1_會比對網站下的所有文件庫。

您可以新增原點搭配使用的完整路徑或相對路徑的特定路徑。

本範例會使用相對路徑的特定網站新增私人原點 siteassets 文件庫：

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

本範例會在網站集合的網站資產使用的完整路徑的文件庫中新增私人原點_folder1_資料夾：

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl “https://contoso.sharepoint.com/sites/test/siteassets/folder1”
```

如需這個命令和語法的詳細資訊，請參閱 < <b0>Add SPOTenantCdnOrigin</b0>。

> [!NOTE]
> 在私人原點共用從原點的資產必須發佈之前他們可從 CDN 的主要版本。
  
一旦您已經執行此命令，系統會設定同步處理跨資料中心。 這可能需要長達 15 分鐘。
  
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>範例： 設定您的主版頁面和樣式庫公用原點的 SharePoint Online
<a name="ExamplePublicOrigin"> </a>

一般而言，這些原點是為您設定預設當您啟用 Office 365 CDN。 不過，如果您想要手動啟用，請遵循下列步驟。
  
- 使用**Add SPOTenantCdnOrigin** cmdlet 來定義樣式庫為公用的原點而言。

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

- 使用**Add SPOTenantCdnOrigin** cmdlet 來定義為公用的原始來源的主版頁面。

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

如需這個命令和語法的詳細資訊，請參閱 < <b0>Add SPOTenantCdnOrigin</b0>。

一旦您已經執行此命令，系統會設定同步處理跨資料中心。 這可能需要長達 15 分鐘。

### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>範例： 設定您的網站資產、 網站頁面和發佈的映像私人原點的 SharePoint Online
<a name="ExamplePrivateOrigin"> </a>

- 使用**Add SPOTenantCdnOrigin** cmdlet 來定義為私人的原始來源的 [網站資產] 資料夾。

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

- 使用**Add SPOTenantCdnOrigin** cmdlet 來定義網站的 [頁面] 資料夾為私人的原點而言。

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

- 使用**Add SPOTenantCdnOrigin** cmdlet 來定義為私人的原始來源的發佈的 [圖像] 資料夾。

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

如需這個命令和語法的詳細資訊，請參閱 < <b0>Add SPOTenantCdnOrigin</b0>。

一旦您已經執行此命令，系統會設定同步處理跨資料中心。 這可能需要長達 15 分鐘。

### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>範例： 設定 SharePoint online 網站集合的私用原始來源
<a name="ExamplePrivateOriginSiteCollection"> </a>

若要定義為私人的原始來源的網站集合使用**Add SPOTenantCdnOrigin** cmdlet。 例如：

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

如需這個命令和語法的詳細資訊，請參閱 < <b0>Add SPOTenantCdnOrigin</b0>。
  
一旦您已經執行此命令，系統會設定同步處理跨資料中心。 您可能會看到 SharePoint Online 租用戶連線到 CDN 服務如預期_設定擱置_郵件。 這可能需要長達 15 分鐘。

### <a name="manage-the-office-365-cdn"></a>管理 Office 365 CDN
<a name="CDNManage"> </a>

一旦您已設定好 CDN，您可以變更您的組態更新內容，或為您的需求改變時，這一節所述。
  
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a>新增、 更新或移除 Office 365 CDN 資產
<a name="Office365CDNforSPOaddremoveasset"> </a>

當您完成設定步驟時，您可以新增新的資產，並更新或移除現有的資產，每當您想要。 只要變更您的資料夾或識別為原始來源的 SharePoint 文件庫中資產。 如果您新增新的資產，它是透過 CDN 立即。 不過，如果您更新資產，它將會需要最多 15 分鐘的傳播並成為 CDN 中可用的新複本。
  
如果您需要擷取原點的位置，您可以使用**Get-SPOTenantCdnOrigins**指令程式。 如需如何使用此指令程式的資訊，請參閱 < <b0>Get SPOTenantCdnOrigins</b0>。
  
#### <a name="remove-an-origin-from-the-office-365-cdn"></a>從 CDN 將 Office 365 中移除原始來源
<a name="Office365CDNforSPORemoveOrigin"> </a>

您可以移除資料夾或識別為原始來源的 SharePoint 文件庫的存取權。 若要這麼做，請使用**Remove SPOTenantCdnOrigin**指令程式。

``` powershell
Remove-SPOTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

如需如何使用此指令程式的資訊，請參閱 <<c0>移除 SPOTenantCdnOrigin。
  
#### <a name="modify-an-origin-in-the-office-365-cdn"></a>修改 CDN 將 Office 365 中的原始來源
<a name="Office365CDNforSPORemoveOrigin"> </a>

您無法修改已建立的原始來源。 相反地，移除原始來源，然後加入一個新。 如需詳細資訊，請參閱[移除從 Office 365 CDN 原始來源](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin)及[新增您資產的原點而言](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin)。
  
#### <a name="disable-the-office-365-cdn"></a>停用 Office 365 CDN
<a name="Office365CDNforSPODisable"> </a>

若要停用組織 CDN 使用**組 SPOTenantCdnEnabled**指令程式。 如果您有兩個公用和私人原點啟用 CDN，您需要執行的指令程式兩次，如下列範例所示。
  
若要停用使用的公用原點 CDN 中，輸入下列命令：

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

若要停用的私用的原點 CDN 中使用，請輸入下列命令：

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

如需此 cmdlet 的詳細資訊，請參閱 <<c0>設定 SPOTenantCdnEnabled。

## <a name="set-up-and-configure-the-office-365-cdn-using-the-office-365-cli"></a>安裝及設定 Office 365 CDN 使用 Office 365 CLI
<a name="CDNSetupinCLI"> </a>

本節中的程序需要您已安裝[Office 365 CLI](https://aka.ms/o365cli)。 接下來，連線到 SharePoint Online 租用戶使用[spo 連線](https://pnp.github.io/office365-cli/cmd/spo/connect/)] 命令。

完成下列步驟來安裝及設定以裝載您在 SharePoint Online 中使用 Office 365 CLI 資產 CDN。

### <a name="enable-the-office-365-cdn"></a>啟用 Office 365 CDN

您可以使用[spo cdn set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-set/)命令租用戶中管理 Office 365 CDN 的狀態。

若要啟用 Office 365 公用 CDN 租用戶中執行：

```sh
spo cdn set --type Public --enabled true
```

若要啟用 Office 365 SharePoint CDN，請執行：

```sh
spo cdn set --type Private --enabled true
```

#### <a name="view-the-current-status-of-the-office-365-cdn"></a>檢視 Office 365 CDN 的目前狀態

若要檢查 Office 365 CDN 的特定類型是啟用還是停用，請使用[spo cdn get](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-get/)命令。

若要檢查 Office 365 公用 CDN 是否已啟用，請執行：

```sh
spo cdn get --type Public
```

### <a name="view-the-office-365-cdn-origins"></a>檢視 Office 365 CDN 原點

若要檢視目前設定的 Office 365 公用 CDN 原點執行：

```sh
spo cdn origin list --type Public
```

當您啟用 Office 365 CDN 預設佈建原點的相關資訊，請參閱[預設 CDN 原點](use-office-365-cdn-with-spo.md#default-cdn-origins)。

### <a name="add-an-office-365-cdn-origin"></a>新增 Office 365 CDN 原始來源

> [!NOTE]
> 您應該永遠不會將會被視為機密的 SharePoint 文件庫設定為公用的原始來源組織的資源。

使用[spo cdn 原點 add](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-add/)命令來定義 CDN 原點。 您可以定義多個原點。 原點是指向 SharePoint 文件庫或資料夾，其中包含您想要裝載的 CDN 資產的 URL。

```sh
spo cdn origin add --type [Public | Private] --origin <path>
```

其中`path`是包含資產的資料夾路徑。 您可以使用萬用字元，除了相對路徑。

若要為公用的原始來源的所有網站**主版頁面圖庫**中包含所有的資產，請執行：

```sh
spo cdn origin add --type Public --origin */masterpage
```

若要設定特定網站集合的私用原始來源，請執行：

```sh
spo cdn origin add --type Private --origin sites/site1/siteassets
```

> [!NOTE]
> 新增 CDN 原點之後, 可能需要 15 分鐘的時間，您就能夠擷取透過 CDN 服務的檔案。 您可以驗證是否已經使用[spo cdn 原點清單](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/)命令已啟用的特定的原點而言。

### <a name="remove-an-office-365-cdn-origin"></a>移除 Office 365 CDN 原始來源

使用[spo cdn 原點移除](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-remove/)命令來移除指定的 CDN 類型 CDN 原點。

若要從 CDN 組態移除公用的原點而言，請執行：

```sh
spo cdn origin remove --type Public --origin */masterpage
```

> [!NOTE]
> 移除 CDN 原點不會影響比對該原點任何文件庫中所儲存的檔案。 如果已使用其 SharePoint URL 已參考這些資產，SharePoint 會自動切換回原始 URL 指向文件庫。 如果不過，您必須使用公用 CDN URL 已參照資產，然後移除原始會中斷連結，並將必須手動將它們變更。

### <a name="modify-an-office-365-cdn-origin"></a>修改 Office 365 CDN 原始來源

您不能修改現有的 CDN 原點。 相反地，您應該移除先前定義的 CDN 原點使用`spo cdn origin remove`命令，並新增新一個使用`spo cdn origin add`命令。

### <a name="change-the-types-of-files-to-include-in-the-office-365-cdn"></a>變更要在 Office 365 CDN 中包含檔案的類型

根據預設，下列檔案類型中隨附的 CDN: _.css、.eot、.gif、.ico、.jpeg、.jpg、.js、.map、.png、.svg、.ttf 和.woff_。 如果您需要在 CDN 中包含其他檔案類型，您可以變更 CDN 組態使用[spo cdn 原則設定](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/)] 指令。

> [!NOTE]
> 在變更的檔案類型清單，請您覆寫目前所定義的清單。 如果您想要包含其他檔案類型，先使用[spo cdn 原則] 清單中](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/)命令，以找出目前設定的檔案類型。

若要將_JSON_檔案類型新增至公用 CDN 中包含的檔案類型的預設清單，請執行：

```sh
spo cdn policy set --type Public --policy IncludeFileExtensions --value "CSS,EOT,GIF,ICO,JPEG,JPG,JS,MAP,PNG,SVG,TTF,WOFF,JSON"
```

### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a>變更網站分類您想要從 Office 365 CDN 排除清單

使用[spo cdn 原則設定](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/)命令中排除不想要提供透過 CDN 的網站分類。 根據預設，會不排除任何網站分類。

> [!NOTE]
> 在變更排除的網站分類的清單，請您覆寫目前所定義的清單。 如果您想要排除其他分類，先使用[spo cdn 原則] 清單中](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-list/)命令，以找出目前設定的分類。

若要排除歸類為_HBI_從公用 CDN 的網站，請執行

```sh
spo cdn policy set --type Public --policy ExcludeRestrictedSiteClassifications --value "HBI"
```

### <a name="disable-the-office-365-cdn"></a>停用 Office 365 CDN

若要停用 Office 365 CDN 使用`spo cdn set`命令，例如：

```sh
spo cdn set --type Public --enabled false
```

## <a name="using-your-cdn-assets"></a>使用 CDN 資產

既然您已啟用 CDN 與設定的原點和原則，您可以開始使用 CDN 資產。

本節將協助您了解如何使用 CDN Url 中您的 SharePoint 頁面和內容，以便 SharePoint 會在公用和私人原點的資產的要求重新導向至 CDN。

- [更新連結至 CDN 資產](use-office-365-cdn-with-spo.md#updating-links-to-cdn-assets)
- [在公用的原點中使用資產](use-office-365-cdn-with-spo.md#using-assets-in-public-origins)
- [在私人原點中使用資產](use-office-365-cdn-with-spo.md#using-assets-in-private-origins)

如需如何使用 CDN 裝載用戶端網頁組件的資訊，請參閱主題[主機用戶端網頁組件從 Office 365 CDN （Hello World 第 4 部分）](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)。

### <a name="updating-links-to-cdn-assets"></a>更新連結至 CDN 資產

若要使用您新增至原始來源的資產，您只需更新連結到原始的檔案取代為來源中的檔案的路徑。

- 編輯頁面或包含連結至您新增至原始來源的資產的內容。 您也可以使用幾種方法之一，以全域搜尋，並取代連結跨 enter 網站或網站集合，如果您想要顯示的每個地方指定資產更新連結。
- 每個連結中原點資產，取代 CDN 原始來源中的檔案的路徑中的路徑。 您可以使用相對路徑。
- 儲存在頁面或內容。

例如，假設影像 _/site/SiteAssets/images/image.png_，其中已複製到文件庫資料夾_讀/網站/CDN_origins/公開 /_。 若要使用 CDN 資產，取代若要讓新的 URL _/site/CDN_origins/public/image.png_原始來源的路徑中的影像檔案位置的原始路徑。

如果您想要使用資產的完整 URL，而不是相對路徑，建構連結仿照下列所示：

`https://<TenantHostName>.sharepoint.com/sites/site/CDN_origins/public/image.png`

> [!NOTE]
> 一般而言，您應該不硬 Url 直接在 CDN 資產。 不過，您可以手動建構 Url 中公開的原點的資產視。 如需詳細資訊，請參閱 <<c0>公用資產的硬式編碼 CDN Url。

若要深入了解如何確認，正在從 CDN 提供資產，請參閱[如何確認資產，由 CDN？](use-office-365-cdn-with-spo.md#CDNConfirm) [疑難排解 Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) ] 區段中。

### <a name="using-assets-in-public-origins"></a>在公用的原點中使用資產

**發佈功能**在 SharePoint Online 中自動修正儲存在公用的原點至 CDN 相等，以便從 CDN 服務，而不是 SharePoint 提供資產的資產的 Url。

如果您的原始來源與發佈網站中啟用功能，且您想要卸載到 CDN 的資產處於下列類別之一，SharePoint 會自動修正 Url 資產的原點而言，假設資產已不被排除的 CDN 原則。

以下是一種連結會自動修正的 SharePoint 發佈功能的概觀：

- 在傳統的發佈頁面 HTML 回應中的 IMG/連結/CSS Url
  - 這包括內] 頁面上的 HTML 內容作者所加入的影像
- 圖片庫投影片放映： 網頁組件圖像 Url
- SPList REST API (RenderListDataAsStream) 結果中的圖像欄位
  - 使用新屬性_ImageFieldsToTryRewriteToCdnUrls_來提供的欄位以逗號分隔清單
  - 支援的超連結欄位和 PublishingImage 欄位
- SharePoint 影像轉譯

下圖說明工作流程，當 SharePoint 收到包含從公用原點的資產頁面要求。

![工作流程圖表： 從公用的原始來源擷取 Office 365 CDN 資產](media/O365-CDN/o365-cdn-public-steps-transparent.svg "工作流程： 從公用的原始來源擷取 Office 365 CDN 資產")

> [!TIP]
> 如果您想要停用自動修正的頁面上的特定 Url，您可以取出頁面，並新增查詢字串參數 **?NoAutoReWrites = true**至您想要停用每個連結的結尾。

#### <a name="hardcoding-cdn-urls-for-public-assets"></a>公用資產的硬式編碼 CDN Url

如果公用的原點而言，未啟用_發佈_功能，或資產不是其中一個 CDN 服務的自動修正功能所支援的連結類型，可以手動建構資產 CDN 位置的 Url，並在您的內容中使用這些 Url。

> [!NOTE]
> 您不能硬 CDN Url 中私人原點的資產，因為表單 URL 的最後一個區段的必要的存取權杖產生要求資源的時間。

公用 CDN 資產，URL 格式看起來如下所示：

``` html
https://publiccdn.sharepointonline.com/<TenantHostName>/sites/site/library/asset.png
```

**TenantHostName**取代為您的租用戶名稱。 範例：

``` html
https://publiccdn.sharepointonline.com/contoso.sharepoint.com/sites/site/library/asset.png
```

### <a name="using-assets-in-private-origins"></a>在私人原點中使用資產

無需額外設定，才能在私人原點中使用資產。 SharePoint Online 自動修正 Url 中私人原點的資產讓這些資產的要求永遠都會服務從 CDN。 因為這些 Url 包含必須要求資產時間是由 SharePoint Online 自動產生的語彙基元，無法以手動方式中私人原點的 CDN 資產建置 Url。

私用原點中的資產的存取受保護的動態產生的語彙基元根據使用者在起點的權限與下列各節所述出現警告。 使用者必須至少具有**讀取**存取權來呈現內容 CDN 的原點。

下圖說明工作流程，當 SharePoint 收到包含從私人原點的資產頁面要求。

![工作流程圖表： 從私人的原始來源擷取 Office 365 CDN 資產](media/O365-CDN/o365-cdn-private-steps-transparent.svg "工作流程： 從私人的原始來源擷取 Office 365 CDN 資產")

#### <a name="token-based-authorization-in-private-origins"></a>在私人原點語彙基元為基礎的授權

SharePoint Online 所產生的語彙基元是授與存取權 CDN 將 Office 365 中的私人原點的資產。 已存取至資料夾或指定原始文件庫的權限的使用者會自動授與允許使用者存取檔案是根據其權限等級的權杖。 這些存取權杖是有效 30 至 90 分鐘後它們會產生以協助防止權杖重新執行攻擊。

一旦產生的存取權杖，SharePoint Online 會傳回自訂 URI 包含兩個授權參數_吃_（edge 授權權杖） 和_oat_ （原點授權權杖） 用戶端。 每個語彙基元的結構是 _< '到期時間期間時間格式 '>_<' 安全簽章中的' >_。 例如：

``` html
https://privatecdn.sharepointonline.com/contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg?eat=1486154359_cc59042c5c55c90b26a2775323c7c8112718431228fe84d568a3795a63912840&oat=1486154359_7d73c2e3ba4b7b1f97242332900616db0d4ffb04312
```

> [!NOTE]
> 語彙基元的持有的任何人都可以存取資源的 CDN。 不過，包含這些存取 token 只共用透過 HTTPS 的 Url，因此除非權杖到期之前，使用者明確地共用 URL 資產不會是未經授權的使用者可以存取。

#### <a name="item-level-permissions-are-not-supported-for-assets-in-private-origins"></a>在私人原點的資產不支援項目層級權限

請務必注意，SharePoint Online 不支援項目層級權限在私人原點的資產。 例如，針對檔案位於`https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`，使用者具有有效的存取權給予符合下列條件的檔案：

|使用者  |權限  |有效的存取  |
|---------|---------|---------|
|使用者 1     |有權存取 folder1         |可以存取 image1.jpg 從 CDN         |
|使用者 2     |沒有存取權 folder1         |無法存取 image1.jpg 從 CDN         |
|使用者 3     |沒有存取權 folder1，但是會授與存取 SharePoint Online 中的 image1.jpg 明確權限         |可以存取資產 image1.jpg，直接從 SharePoint Online 中，但不是從 CDN         |
|使用者 4     |有權存取 folder1，但已明確拒絕存取 SharePoint Online 中的 image1.jpg         |無法從 SharePoint Online 中，存取資產，但可以存取資產從 CDN 而不管遭拒絕存取 SharePoint Online 中的檔案         |

## <a name="troubleshooting-the-office-365-cdn"></a>疑難排解 Office 365 CDN
<a name="CDNTroubleshooting"> </a>

### <a name="how-do-i-confirm-that-assets-are-being-served-by-the-cdn"></a>如何確認資產，由 CDN？
<a name="CDNConfirm"> </a>

一旦您已新增連結] 頁面上的 CDN 資產，您可以確認的資產由從 CDN 瀏覽至 [] 頁面上、 滑鼠右鍵按一下 [影像後已轉譯及檢閱的影像 URL。

您也可以使用瀏覽器的開發人員工具，在頁面上，檢視每個資產的 URL，或使用 3rd 廠商網路追蹤工具。

> [!NOTE]
> 如果您使用 Fiddler 之類的網路來測試您資產外轉譯資產從 SharePoint] 頁面上，您必須手動新增查閱者標頭 」 查閱者： `https://yourdomain.sharepoint.com`」 至其中的 URL 是您的 SharePoint Online 租用戶的根 URL GET 要求。

您無法直接在網頁瀏覽器中測試 CDN Url，因為您必須具有來自 SharePoint Online 查閱者。 不過，如果您將 CDN 資產 URL 新增至 SharePoint] 頁面上，然後在瀏覽器中開啟] 頁面上，您會看到在頁面上呈現 CDN 資產。

如需有關如何在 Microsoft Edge 瀏覽器中使用的開發人員工具的詳細資訊，請參閱 < <b0>Microsoft Edge 開發人員工具</b0>。

### <a name="why-are-assets-from-a-new-origin-unavailable"></a>為何無法使用的新的原點從資產？
資產中新的原點會立即無法可供使用，因為所花的時間才能傳播到 CDN 註冊並從原點上載至 CDN 儲存資產。 可在 CDN 資產所需的時間取決於多少資產和檔案大小。

### <a name="my-client-side-web-part-or-sharepoint-framework-solution-isnt-working"></a>我的用戶端網頁組件或 SharePoint 架構解決方案無法正常運作

當您啟用公用原點 CDN 將 Office 365 時，CDN 服務會自動建立這些預設原點：

- * / 主版頁面
- * / 樣式庫
- * / CLIENTSIDEASSETS

如果 * / clientsideassets 原點遺漏、 SharePoint 架構解決方案會失敗，而且會產生任何警告或錯誤訊息。 此原點可能遺失，因為 CDN 已啟用與 _-NoDefaultOrigins_參數設為 **$true**，或是手動刪除原點。

您可以檢查看看是否 * / CLIENTSIDEASSETS 原點有搭配下列 PowerShell 命令：

``` powershell
Get-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

或者，您可以檢查與 Office 365 CLI:

``` powershell
spo cdn origin list
```

若要新增原始 PowerShell 中：

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

若要在 Office 365 CLI 新增來源：

``` powershell
spo cdn origin add --origin */CLIENTSIDEASSETS
```

### <a name="what-powershell-modules-and-cli-shells-do-i-need-to-work-with-the-office-365-cdn"></a>查看 PowerShell 模組與 CLI 殼層我需要為搭配 Office 365 CDN？

您可以選擇為搭配 Office 365 CDN 使用**SharePoint Online 管理命令介面**的 PowerShell 模組] 或 [ **Office 365 CLI**。

- [開始使用 SharePoint Online 管理命令介面](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)
- [安裝 Office 365 CLI](https://pnp.github.io/office365-cli/user-guide/installing-cli/)

## <a name="see-also"></a>另請參閱

[內容傳遞網路](https://aka.ms/o365cdns)

[Office 365 的網路規劃和效能調整](https://aka.ms/tune)

