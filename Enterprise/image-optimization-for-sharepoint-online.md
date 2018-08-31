---
title: SharePoint Online 的影像最佳化
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/19/2018
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c7edb02a-fdab-4f91-9a20-cba01dad28ef
description: 了解如何使用轉譯和小精靈來提升您的 SharePoint Online 網站上的圖像效能。
ms.openlocfilehash: 313046dec885a38062635254699301bcf556d698
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539950"
---
# <a name="image-optimization-for-sharepoint-online"></a>SharePoint Online 的影像最佳化

網頁載入速度轉譯包括圖像和 HTML、 JavaScript、 CSS] 頁面上所需的所有元件的合併大小而定。圖像是更好的方式進行更多吸引網站，但其大小可能會影響效能。藉由最佳化壓縮及調整大小、 和使用小圖像，您可以位移非常大的影像的效果。您可以使用 SharePoint 影像轉譯上, 傳的單一大型圖像，並顯示讓它可重複使用，而重新載入之圖像的章節。
  
## <a name="using-sprites-to-speed-up-image-loading-in-sharepoint-online"></a>使用精靈加快 SharePoint Online 中的影像載入速度

|||
|:-----|:-----|
| 映像小精靈包含許多較小的圖像。使用 CSS 選取要顯示在具有絕對位置] 頁面上的特定部分的複合式圖像的一部分。基本上，您移動單一的圖像，而不是載入多個影像頁面四周並進行該映像小部分可見透過小精靈映像的必要的部分所示的其中一個小視窗以將一般使用者。SharePoint Online 使用小小精靈 spcommon.png 中顯示其各種圖示。  <br/>  此處所涵蓋項目：  <br/>  影像壓縮  <br/>  圖像最佳化  <br/>  SharePoint 圖像轉譯  <br/> |![Spcommon 的螢幕擷取畫面](media/cc5cdee1-8e54-4537-9a8a-8854f4ee849f.png)|
   
因為您下載而不是數個只有一個圖像，然後快取及重複使用的圖像加重效能。即使映像不維持不快取，藉由單一的圖像，而不是多個影像，此方法可減少伺服器來減少頁面載入時間的 HTTP 要求總數。這是真正的圖像正在連結。這是非常有用的技巧如果圖像不變更經常，例如圖示，上面所提供的 SharePoint 範例所示。您可以使用[Web Essentials](http://vswebessentials.com/)，若要達到此輕鬆地在 Microsoft Visual Studio 的協力廠商、 開放原始碼、 社群式專案的方式。如需詳細資訊，請參閱[縮小和 SharePoint Online 中正在連結](https://go.microsoft.com/fwlink/?LinkId=708698)。
  
## <a name="using-image-compression-and-optimization-to-speed-up-page-loading-in-sharepoint"></a>使用影像壓縮和最佳化以加快 SharePoint 中的頁面載入速度

影像壓縮和最佳化是要減少您在網站上使用的影像檔案大小。要縮小影像大小，最好的方法通常是將影像調整為可在網站上看清楚的最大尺寸。讓影像大於可以看清楚的尺寸毫無意義。使用影像編輯器確保影像有正確尺寸是快速又簡單的頁面大小縮減方式。
  
一旦圖像的右邊的大小下, 一步是以最佳化的這些影像壓縮。有各種工具可用於壓縮及最佳化，包括相片藝廊和協力廠商工具。要壓縮的索引鍵是不含適用於使用者遺失任何差別品質降低儘可能的檔案大小。請確定您測試以確定它們仍美觀高畫質顯示您壓縮的檔案。
  
## <a name="speed-up-page-downloads-by-using-sharepoint-image-renditions"></a>使用 SharePoint 影像轉譯加快頁面下載速度

圖像轉譯為 SharePoint Online 中，可讓您以不同版本的預先定義的圖像尺寸為基礎的圖像設定服務的功能。這是特別重要時沒有使用者產生的圖像內容或網站上的 CSS 修正圖像維度例如寬度與高度。即使映像已修正 CSS、 完整的解析度圖像是仍載入。在此例中可藉由使用影像轉譯降低檔案大小。
  
> [!NOTE]
> 啟用發佈時，僅可用於 SharePoint 轉譯。您可以啟用 [設定] 下的發佈\>網站設定\>管理網站功能\>SharePoint Server 發佈。否則不會出現的選項。 
  
影像轉譯在調整大小時，其作用方式會先採用您定義的最小尺寸 (寬度或高度)，然後再調整影像大小，讓另一個尺寸根據鎖定的長寬比自動調整大小。根據預設，它會從影像中心點裁剪下剩餘尺寸大小。例如，如果您定義的轉譯寬 100px、高 50px，而原始影像為寬 1000px、高 800px，那麼影像將會調整大小，原本 800px 的尺寸現在會變成 50px，原本 1000px 的尺寸現在會變成 62.5px，然後從影像中心點裁剪下此大小。
  
步驟相當簡單，但想要讓影像使用轉譯，您必須在新增影像前，先在 SharePoint 網站上定義好轉譯。此外，您也需要開啟 SharePoint Server 發佈基礎結構 (網站集合層級) 和 SharePoint Server 發佈 (網站層級) 功能。
  
 **新增以加速頁面載入影像轉譯**
  
1. 確認執行此程序的使用者帳戶具有，在最小值、 最上層網站的 「 設計 」 權限的網站集合] 並網站要發佈至網頁。
    
2. 在網頁瀏覽器中，移至發佈網站集合的頂層網站。
    
3. 選擇 **[設定]** 圖示。 
    
4. 在 **[網站設定]** 頁面上，您會在 **[外觀與風格]** 區段中看到內建的影像轉譯。 
    
    您可使用現成可用的轉譯或選擇 **[影像轉譯]** 來建立新的轉譯。 
    
    ![圖像轉譯的螢幕擷取畫面](media/eaae0d53-657d-47ef-b687-65c5167eae4d.PNG)
  
5. 在 **[影像轉譯]** 頁面上，選擇 **[新增項目]**。
    
    ![新增項目的螢幕擷取畫面](media/8cede22e-52bf-4d9d-99cb-162f2f6ce92b.PNG)
  
6. 在 **[新影像轉譯]** 頁面上的 **[名稱]** 方塊中輸入轉譯名稱。 
    
7. 在 **[寬度]** 和 **[高度]** 文字方塊中，以像素為單位輸入轉譯的寬度和高度，然後選擇 **[儲存]**。
    
    ![影像轉譯名稱的螢幕擷取畫面](media/5a6119ed-c163-40df-a4db-ec629d15607d.PNG)
  
## <a name="custom-cropping-with-image-renditions-in-sharepoint"></a>SharePoint 中影像轉譯的自訂裁剪

根據預設，從之圖像的中心產生圖像轉譯。您可以調整個別圖像圖像轉譯裁剪您想要使用之圖像的部分。您可以裁剪上個別的基礎，每個轉譯的圖像。裁剪圖像加快載入所建立的每個轉譯影像的版本中使用 SharePoint 的 blob 快取的頁面。如此一來伺服器負載會降低因為映像只調整大小時一次，然後可供多次做為一般使用者。如需如何裁剪圖像轉譯的詳細資訊，請參閱[裁剪圖像轉譯](https://go.microsoft.com/fwlink/p/?LinkId=525626)。
  

