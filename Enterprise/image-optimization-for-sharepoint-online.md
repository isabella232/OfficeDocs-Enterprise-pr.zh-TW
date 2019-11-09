---
title: SharePoint Online 傳統的發佈網站的影像最佳化
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/18/2019
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c7edb02a-fdab-4f91-9a20-cba01dad28ef
description: 了解如何使用轉譯和精靈加快來改善 SharePoint Online 傳統發佈網站上的影像效能。
ms.openlocfilehash: a3dbfeaa238f8c12f8ecc3afaa3a45942d665599
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2019
ms.locfileid: "38077616"
---
# <a name="image-optimization-for-sharepoint-online-classic-publishing-sites"></a>SharePoint Online 傳統的發佈網站的影像最佳化

網頁載入執行速度取決於呈現包括影像、 HTML、 JavaScript 和 CSS] 頁面上所需要的所有元件的總計大小。 影像很棒的方法讓您的網站更吸引人，但其大小可能會影響效能。 最佳化您的影像壓縮和調整大小，以及使用精靈加快，您可以位移龐大的影像的效果。 使用 SharePoint 影像轉譯，您可以上傳單一大型圖像，並顯示讓它可重複使用，而非重新載入之圖像的章節。

>[!NOTE]
>本主題適用於 SharePoint Online 傳統的發佈網站，不新式的入口網站。 在 SharePoint Online 的新式入口網站中的影像最佳化的相關資訊，請參閱[SharePoint Online 的新式入口網站頁面中的最佳化影像](modern-image-optimization.md)。
  
## <a name="using-sprites-to-speed-up-image-loading"></a>使用精靈加快影像載入速度

|||
|:-----|:-----|
| 影像精靈包含多個較小的圖像。 使用 CSS 您選取要與絕對位置] 頁面上的特定組件上顯示的複合圖像的一部分。 基本上，您將移動的單一的圖像，而不是載入多個影像，頁面四周並對該圖像的一小部分可見透過其中精靈影像的必要組件會顯示在小型視窗使用者。 SharePoint Online 使用精靈加快其各種圖示中顯示精靈 spcommon.png。  <br/>  涵蓋了以下：  <br/>  影像壓縮  <br/>  影像最佳化  <br/>  SharePoint 影像轉譯  <br/> |![Spcommon 的螢幕擷取畫面](media/cc5cdee1-8e54-4537-9a8a-8854f4ee849f.png)|
   
這可以提升效能，因為您下載只有一個圖像，而不是數個然後快取和重複使用該影像。 即使映像不維持不快取，所需要的單一的圖像，而不是多個影像，此方法可減少伺服器來減少頁面載入時間的 HTTP 要求總數。 這確實是一種統合影像。 這是很有用技術如果影像不會變更通常，例如圖示，上面所提供的 SharePoint 範例所示。 您可以如何使用[Web Essentials](https://vswebessentials.com/)，來達成這個目的輕鬆地在 Microsoft Visual Studio 中的第三方、 開放原始碼、 社群式專案。 如需詳細資訊，請參閱[縮製及統合在 SharePoint Online 中](https://go.microsoft.com/fwlink/?LinkId=708698)。
  
## <a name="using-image-compression-and-optimization-to-speed-up-page-loading"></a>使用影像壓縮和最佳化，加快頁面載入

影像壓縮和最佳化是關於減少您網站使用的影像的檔案大小。 通常，減少圖像的大小最佳的技巧，就是調整為它將可在網站上檢視之最大尺寸圖像的大小。 在具有比以往可檢視較大圖像是沒有意義。 確定影像屬於正確使用影像這類編輯器中的維度是頁面的快速又簡單的方法，以減少您大小。
  
圖像會正確的大小下, 一步是以最佳化這些映像的壓縮。 有各種工具可供您使用壓縮和最佳化，包括相片藝廊和協力廠商工具。 壓縮的關鍵在於減少檔案大小儘可能不會遺失任何辨別品質的使用者。 請確定您測試以確定它們仍好看高畫質顯示在您壓縮的檔案。
  
## <a name="speed-up-page-downloads-by-using-sharepoint-image-renditions"></a>使用 SharePoint 影像轉譯加快頁面下載速度

影像轉譯是 SharePoint Online 中，可讓您以提供不同版本的映像根據預先定義的影像維度功能。 沒有使用者產生的圖像內容或影像維度，例如寬度和高度所修正網站上的 CSS 時，這是特別重要。 即使所 CSS 修正映像，完整的解析度影像是仍載入。 在此情況下可藉由使用影像轉譯降低檔案大小。
  
> [!NOTE]
> 啟用發佈功能時，僅適用於 SharePoint 轉譯。 您可以啟用 [設定] 下的發佈\>站台設定\>管理網站功能\>SharePoint Server 發佈。 否則不會出現 [] 選項。
  
您定義的最小維度 = 389917 調整 works 影像轉譯，不論是寬度或高度與然後調整影像大小，以便與其他維度自動調整大小根據鎖定長寬比例。 根據預設，它將剩餘的維度裁剪圖像的中心點。 例如，如果您定義 100px 寬及 50px 高及您原始映像的轉譯為 1000px 寬及 800px 高，它將會調整大小，使 800px 維度現在是 50px 和 1000px 維度 (現在 62.5px) 裁剪之圖像的中心。
  
是相當簡單的步驟，但若要使用的轉譯的影像，轉譯需要在 SharePoint 網站上，才能新增影像。 此外，您也需要有開啟的 SharePoint Server 發佈 （網站層級） 功能與 SharePoint Server 發佈基礎結構 （網站集合層級）。
  
### <a name="add-an-image-rendition-to-speed-up-page-loading"></a>新增影像轉譯以加快載入頁面
  
1. 確認執行此程序的使用者帳戶具備，在最低限度下，最上層網站的 「 設計 」 權限，網站集合，並且網站要發佈至網頁。

2. 在網頁瀏覽器中，移至發佈網站集合的頂層網站。

3. 選擇 [**設定**] 圖示。

4. 在**網站設定**] 頁面的 [**外觀與風格**] 區段中，您會看到內建的影像轉譯。

    您可以使用現成可用的轉譯或選擇 [**影像轉譯**] 來建立一個新。

    ![影像轉譯的螢幕擷取畫面](media/eaae0d53-657d-47ef-b687-65c5167eae4d.PNG)
  
5. 在 [**影像轉譯**] 頁面上，選擇 [**新增項目**。

    ![新增項目的螢幕擷取畫面](media/8cede22e-52bf-4d9d-99cb-162f2f6ce92b.PNG)
  
6. 在 [**新影像轉譯**] 頁面上，在 [**名稱**] 方塊中，輸入轉譯名稱。

7. 中**寬度**和**高度**] 文字方塊中，輸入的寬度和高度，以像素，轉譯，然後選擇 [**儲存**。

    ![影像轉譯名稱的螢幕擷取畫面](media/5a6119ed-c163-40df-a4db-ec629d15607d.PNG)
  
## <a name="custom-cropping-with-image-renditions"></a>影像轉譯的自訂裁剪

根據預設，從之圖像的中心產生影像轉譯。 您可以調整個別圖像影像轉譯的部分您想要使用之圖像的裁剪。 您可以裁剪個別，每個轉譯的影像。 裁剪影像會加快頁面載入藉由使用 SharePoint 的 blob 快取建立的每個轉譯的影像版本。 如此一來伺服器負載會減少，因為圖像只調整大小時一次，並再已準備好要提供給使用者多次。 如需有關如何裁剪影像轉譯的詳細資訊，請參閱[裁剪影像轉譯](https://go.microsoft.com/fwlink/p/?LinkId=525626)。
  

