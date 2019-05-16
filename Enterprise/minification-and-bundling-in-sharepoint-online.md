---
title: 縮製及統合在 SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 3/1/2017
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 87a52468-994e-43a2-b155-7229ed659291
description: 本文說明如何使用縮製及統合技術搭配 Web Essentials 來減少 HTTP 要求數目，並降低 SharePoint Online 中載入頁面所花費的時間。
ms.openlocfilehash: d73bc6cc86ea1ea4ecba5395f22a20befdc64b13
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070259"
---
# <a name="minification-and-bundling-in-sharepoint-online"></a>縮製及統合在 SharePoint Online

本文說明如何使用縮製及統合技術搭配 Web Essentials 來減少 HTTP 要求數目，並降低 SharePoint Online 中載入頁面所花費的時間。
  
當您自訂您的網站時您可以最終將大量的額外檔案新增至伺服器，以支援自訂。 新增額外的 JavaScript、 CSS 及影像會增加接著會增加的時間的伺服器就會出現在網頁上的 HTTP 要求數目。 如果您有多個相同類型的檔案，您可以將彙整這些檔案以進行更快速地下載這些檔案。
  
對於 JavaScript 和 CSS 檔案，您也可以使用稱為縮製，其中移除空白字元和其他不必要的字元以減少檔案的總大小方法。
  
## <a name="minification-and-bundling-javascript-and-css-files-with-web-essentials"></a>縮製及統合 JavaScript 和 CSS 檔案搭配 Web Essentials

您可以使用協力廠商軟體如 Web Essentials 來統合 CSS 和 JavaScript 檔案。
  
> [!IMPORTANT]
> Web Essentials 是協力廠商、 開放原始碼、 社群為基礎的專案。 軟體會延伸至 Visual Studio 2012 和 Visual Studio 2013 和 Microsoft 並不支援。 若要下載 Web Essentials，請瀏覽網站， [http://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629)。 
  
Web Essentials 提供兩種統合形式：
  
- .bundle: CSS 和 JavaScript 檔案
    
- .sprite： 影像 （僅適用於 Visual Studio 2013）
    
您可以使用 Web Essentials，如果您有現有的功能含有一些內自訂的主版頁面，例如參考的品牌元素：
  
![自訂主版頁面中的品牌元素螢幕擷取畫面](media/3a6eba36-973d-482b-8556-a9394b8ba19f.png)
  
 **若要在 Web Essentials 中建立 TE000127218 和 CSS 統合包**
  
1. 在 Visual Studio 中，在 [方案總管] 中，選取您想要併入統合包檔案。
    
2. 以滑鼠右鍵按一下選取的檔案，然後選取 [ **Web Essentials** \> **建立 JavaScript 統合包檔案**從快顯功能表。 例如： 
    
    ![顯示 Web 基本功能功能表選項的螢幕擷取畫面](media/41aac84c-4538-4f78-b454-46e651f868a3.png)
  
## <a name="viewing-the-results-of-bundling-javascript-and-css-files"></a>檢視統合 JavaScript 和 CSS 檔案的結果

當您建立 JavaScript 和 CSS 統合包時，Web Essentials 會建立名為識別 JavaScript 及 CSS 檔案，以及一些其他組態資訊配方檔的 XML 檔案： 
  
![JavaScript 和 CSS 配方檔的螢幕擷取畫面](media/7ba891f8-52d8-467b-a0f6-b062dd1137a4.png)
  
此外，如果 minify 旗標設定為 true 中統合配方檔的大小，以及一起降低。 這表示已建立您可以參照您主版頁面中的 JavaScript 檔案的新、 minified 版本。
  
![Minify 旗標設定為 true 的螢幕擷取畫面](media/50523af2-6412-4117-ac3d-5bd26f6d562e.png)
  
當您從網站載入頁面時，您可用於開發人員工具從網頁瀏覽器，例如 Internet Explorer 11，請參閱傳送至伺服器] 與 [多久每個檔案所需載入的要求數目。
  
下圖是載入 JavaScript 和 CSS 檔案的縮製前的結果。
  
![顯示正在下載 80 個項目的螢幕擷取畫面](media/e2df3912-1923-46e6-8cf2-3015a31554e1.png)
  
之後一起統合 CSS 和 JavaScript 檔案，要求數目下降至 74 與每個檔案只需要稍微超過個別下載原始檔案：
  
![顯示正在下載 74 個項目的螢幕擷取畫面](media/686c4387-70e8-4a74-9d45-059f33a91184.png)
  
統合後，JavaScript 統合包檔案會從 815kb 大幅減少到 365KB:
  
![顯示降低下載大小的螢幕擷取畫面](media/5e7dbd98-faff-4f68-b320-108fb252e395.png)
  
## <a name="bundling-images-by-creating-an-image-sprite"></a>建立影像精靈來統合影像

類似於如何將彙整 JavaScript 及 CSS 檔案，您可以將許多小型圖示和其他一般影像合併到較大的小精靈工作表，然後使用 CSS 來顯示個別的影像。 而非下載每個個別的影像，使用者的網頁瀏覽器一次下載精靈工作表，並再將其快取的本機電腦上。 這是透過剪下向下的下載套件和網頁伺服器的來回行程數目改善頁面載入效能。
  
 **若要在 Web Essentials 中建立影像精靈**
  
1. 在 Visual Studio 中，在 [方案總管] 中，選取您想要併入統合包檔案。
    
2. 以滑鼠右鍵按一下選取的檔案，然後選取 [ **Web Essentials** \> **建立影像精靈**從快顯功能表。 例如： 
    
    ![顯示如何建立影像精靈的螢幕擷取畫面](media/de0fe741-4ef7-4e3b-bafa-ef9f4822dac6.png)
  
3. 選擇 [儲存精靈檔案的位置。 .Sprite 檔案是說明設定 XML 檔案和小精靈中的檔案。 下列圖表顯示小精靈 PNG 檔案和其對應的.sprite XML 檔案的範例。
    
    ![精靈檔案的螢幕擷取畫面](media/0876bb2a-d1b9-4169-8e95-9c290d628d90.png)
  
    ![精靈 XML 檔案的螢幕擷取畫面](media/d1f94776-280d-4d56-abb5-384f145d9989.png)
  

