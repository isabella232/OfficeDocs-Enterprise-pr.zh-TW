---
title: 內容傳遞網路
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/2/2019
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 0140f704-6614-49bb-aa6c-89b75dcd7f1f
description: 若要深入了解 Office 365 如何使用內容傳遞網路 (Cdn) 來改善效能使用這項資訊。
ms.openlocfilehash: 5d02b28fad0e47473cc6a75948c9dd27e6728bb5
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490421"
---
# <a name="content-delivery-networks-cdns"></a>內容傳遞網路 (Cdn)

Cdn 協助保護使用者的 Office 365 快速且可靠。 Office 365 等雲端服務會使用 Cdn 快取靜態資產更接近要求他們的瀏覽器來加速下載項目，並降低認知的使用者延遲。 本主題中的資訊可協助您了解內容傳遞網路 (Cdn) 以及如何使用 Office 365。

## <a name="what-exactly-is-a-cdn"></a>什麼 CDN 究竟是？

CDN 是由高速骨幹網路連線的資料中心中的 proxy 和檔案伺服器所組成的地理位置分散的網路。 Cdn 可用來減少延遲，並載入指定的檔案和網站或服務中的物件集合的時間。 CDN 可能有數千個適用於從任何位置的傳入要求的最佳服務端點。

Cdn 通常用來提供網站或服務，例如 javascript 檔案、 圖示和影像，加速下載的一般內容，也可以提供使用者內容，例如 SharePoint Online 的文件庫中的檔案資料流媒體檔案的私用存取、 和自訂程式碼。

大部分的企業雲端服務會使用 Cdn。 Office 365 等雲端服務有數百萬份客戶一次下載混合專屬的內容 （例如電子郵件） 和一般內容 （例如圖示）。 它會將所有人使用的圖示，例如影像最接近使用者的電腦，盡可能更有效率。 您不實用的每個雲端服務來建置在每個都會] 區域中，儲存此一般內容的 CDN 資料中心或甚至在世界各地的每個主要網際網路中樞讓這些 Cdn 的一些共用。

## <a name="how-do-cdns-make-services-work-faster"></a>Cdn 如何讓服務運作得更快？

超過再次下載常見的物件，例如圖示，可能會耗費可更妥善地用於下載重要的個人內容，例如電子郵件或文件的網路頻寬。 因為 Office 365 使用架構，包括 Cdn、 圖示、 指令碼，以及其他一般內容可從伺服器更接近下載至用戶端電腦，更快速地進行下載。 這表示您個人的內容，安全地儲存在 Office 365 資料中心的快速存取。

Cdn 以協助改善雲端服務效能以數種方式：

- Cdn 移開雲端服務，服務藉由減少需要靜態資產的要求提供服務的使用者內容和其他服務的 cloud 服務資源以釋放網路和檔案下載負擔的一部分。
- Cdn 會藉由實作高效能網路和檔案伺服器，並利用更新的網路通訊協定例如[HTTP/2](https://en.wikipedia.org/wiki/HTTP/2)高效率壓縮來提供低延遲檔案存取內建的用途，並要求多工。
- CDN 網路使用多個全域分散式的端點來進行內容提供給使用者盡可能關閉。

## <a name="the-office-365-cdn"></a>Office 365 CDN

內建 Office 365 內容傳遞網路 (CDN) 可讓 Office 365 系統管理員，以提供更佳的效能，其組織的 SharePoint Online 頁面的快取靜態的資產更接近的瀏覽器，要求，這樣有助於加快下載並減少延遲。 Office 365 CDN 改善的壓縮及下載速度會使用[HTTP/2 通訊協定](https://en.wikipedia.org/wiki/HTTP/2)。

Office 365 CDN 是由可讓您在多個位置或_來源_主控靜態資產的多個 CDN 組成，並透過全球高速網路提供資產。 根據您要在 Office 365 CDN 中主控的內容類型而定，您可以新增**公用**來源、**私人**來源或兩者。

![Office 365 CDN 概念圖](media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN 概念圖")

Office 365 CDN 內**公用**來源中的內容可透過匿名方式存取，並且可供具有託管資產 URL 的任何人存取。 因為對公用來源中內容的存取是匿名的，您應該只使用公用來源來快取非敏感性的一般內容，例如 javascript 檔案、指令碼、圖示和影像。 預設會使用 Office 365 CDN 來從公開來源下載一般資源資產，例如 Office 365 用戶端應用程式。

Office 365 CDN 內的**私人**來源可提供使用者內容 (例如 SharePoint Online 文件庫、網站和視訊等媒體) 的私人存取。 對私人來源中內容的存取會使用動態產生的權杖來保護，使得它只能供具有原始文件庫或儲存位置權限的使用者存取。 Office 365 CDN 中的私人來源僅能用於 SharePoint Online 內容，並且您只能透過從您的 SharePoint Online 租用戶重新導向來存取資產。

Office 365 CDN 服務包含在 SharePoint Online 訂閱的一部分。

如需如何使用 Office 365 CDN 的詳細資訊，請參閱 <<c0>使用 SharePoint Online 的 Office 365 內容傳遞網路。

## <a name="other-microsoft-cdns"></a>其他 Microsoft Cdn

雖然不 CDN 將 Office 365 的一部分，您可以使用 Office 365 租用戶中的這些 Cdn 存取 SharePoint 開發文件庫、 自訂程式碼和 Office 365 CDN 的範圍以外的其他用途。

### <a name="azure-cdn"></a>Azure CDN

您可以使用**Azure CDN**部署自己 CDN 的執行個體裝載自訂網頁組件、 文件庫和其他資源的資產，可讓您套用至您 CDN 儲存體的便捷鍵，並執行更能掌控 CDN 組態。 使用 Azure CDN 釋出，並不需要 Azure 訂用帳戶。

如需有關如何設定 Azure CDN 執行個體的詳細資訊，請參閱[快速入門： 與 Azure CDN 整合 Azure 儲存體帳戶](https://docs.microsoft.com/en-us/azure/cdn/cdn-create-a-storage-account-with-cdn)。

如需如何使用 Azure CDN，主應用程式 SharePoint 網頁組件的範例，請參閱 < <b0>Deploy SharePoint 用戶端網頁組件至 Azure CDN</b0>。

如需 Azure CDN PowerShell 模組資訊，請參閱[使用 PowerShell 管理 Azure CDN](https://docs.microsoft.com/en-us/azure/cdn/cdn-manage-powershell)。

### <a name="microsoft-ajax-cdn"></a>Microsoft 的 Ajax CDN

Microsoft 的**Ajax CDN**是唯讀的 CDN 提供許多常用開發程式庫，包括 jQuery （及其所有的其他程式庫），ASP.NET Ajax、 Bootstrap、 Knockout.js，和其他人。
  
若要在專案中包含這些指令碼，只要取代任何這些公開提供的文件庫的參照的 CDN 地址，而不是包含在您本身的專案中的參照。 若要連結至 jQuery，例如，使用下列程式碼：

``` html
<script src=http://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

如需如何使用 Microsoft 的 Ajax CDN 的詳細資訊，請參閱 < <b0>Microsoft Ajax CDN</b0>。

## <a name="how-does-office-365-use-content-from-a-cdn"></a>Office 365 如何使用從 CDN 的內容？

不論您設定您的 Office 365 租用戶哪些 CDN，基本資料擷取程序都相同。

1. 您的用戶端 （瀏覽器或 Office 用戶端應用程式） 要求的資料從 Office 365。

2. Office 365 直接對您的用戶端中傳回的資料或是，如果資料屬於一組的 CDN 所主控的內容會 CDN URL 重新導向您的用戶端。

    a. 如果尚未快取中資料_公用_的原點而言，您的用戶端會直接從最接近的 CDN 位置下載資料至您的用戶端中。

    b. 如果尚未快取中資料_私用_的原點而言，CDN 服務會檢查原點的 Office 365 使用者帳戶的權限。 如果您有權限，SharePoint Online 以動態方式產生 CDN 中資產的路徑和兩個存取權杖，所組成的自訂 URL 和自訂 URL 傳回至您的用戶端。 您的用戶端接著會下載直接從最接近的 CDN 位置資料用戶端使用自訂的 URL。

3. 如果資料不在 CDN 快取，CDN 節點要求從 Office 365 的資料，並再為一段時間之後您的用戶端下載資料快取資料。

CDN 找出最接近的資料中心到使用者的瀏覽器，並使用重新導向，從該處下載要求的資料。 CDN 重新導向快速，且可儲存使用者大量下載時間。

## <a name="how-should-i-set-up-my-network-so-that-cdns-work-best-with-office-365"></a>如何應該設定我的網路以便 Cdn 運作起來最順暢與 Office 365？

降低您的網路上的用戶端與 CDN 端點之間的延遲是確保最佳效能的重要考量。 您可以使用[管理 Office 365 端點](managing-office-365-endpoints.md)中所述的最佳作法以確保您的網路組態允許用戶端瀏覽器來存取 CDN 直接，而不是路由 CDN 流量透過管理中心的 proxy，以避免簡介不必要的延遲。

您也可以閱讀[Office 365 網路連線原則](https://aka.ms/o365networkingprinciples)來了解 Office 365 網路效能最佳化的概念。

## <a name="is-there-a-list-of-all-the-cdns-that-office-365-uses"></a>是否有 Office 365 使用的所有 Cdn 的清單？

使用 Office 365 Cdn 永遠都會受到變更，並在許多情況下，有多個 CDN 合作夥伴設定事件中其中一個已無法使用。 主要是由 Office 365 的 Cdn:

|CDN  |Company  |Usage  |連結  |
|---------|---------|---------|---------|
|Office 365 CDN     |Akamai         |在公用的原點，私人原點的 SharePoint 使用者內容中的一般資產         |[使用 SharePoint Online 中使用 Office 365 內容傳遞網路](https://docs.microsoft.com/en-us/office365/enterprise/use-office-365-cdn-with-spo)         |
|Azure CDN     |Microsoft         |自訂程式碼，SharePoint 架構解決方案         |[Microsoft Azure CDN](https://azure.microsoft.com/documentation/services/cdn/)         |
|Microsoft 的 Ajax CDN （唯讀）     |Microsoft         |常見的文件庫的 Ajax，jQuery，ASP.NET、 Bootstrap Knockout.js 等等。         |[Microsoft 的 Ajax CDN](https://docs.microsoft.com/en-us/aspnet/ajax/cdn/overview)         |

## <a name="what-performance-gains-does-a-cdn-provide"></a>提升何種效能沒有 CDN 提供嗎？

有許多因素參與測量特定直接從 Office 365 下載的資料之間的效能差異和下載從特定的 CDN，您的位置，相對於您的租用戶和至最接近的 CDN 端點，例如數目的資料資產頁面上的，會由 CDN，以及暫時性變更網路延遲和頻寬。 不過，簡單的 A / B 測試可協助以顯示特定檔案下載時間的差異。

下列螢幕擷取畫面會說明在 Office 365 中的原生檔案位置和裝載於[Microsoft Ajax 內容傳遞網路](https://docs.microsoft.com/en-us/aspnet/ajax/cdn/overview)上的相同檔案之間的差異下載速度。 下列螢幕擷取畫面會從 Internet Explorer 11 開發人員工具中的 [**網路**] 索引標籤。 下列螢幕擷取畫面顯示常用的文件庫 jQuery 延遲。 若要以相反此畫面中，Internet Explorer 中，按**F12**並選取 Wi-fi 圖示來表示 [**網路**] 索引標籤。
  
![F12 網路的螢幕擷取畫面](media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
這個螢幕擷取畫面顯示文件庫上傳至主版頁面圖庫，SharePoint Online 網站本身。 上傳文件庫所花的時間為 1.51 秒。
  
![載入時間為 1.51 秒的螢幕擷取畫面](media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
第二個螢幕擷取畫面顯示由 Microsoft 傳遞的相同檔案 CDN。 這段時間延遲是大約 496 毫秒。 這是較大型的改善，並顯示整個第二個 shaved 關閉下載物件的總時間。
  
![載入時間為 469 毫秒的螢幕擷取畫面](media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)

## <a name="is-my-data-safe"></a>為我的資料安全嗎？

我們要保護的資料執行貴公司的非常小心。 傳輸中和 rest、 加密 CDN 將 Office 365 中儲存的資料，並在 Office 365 SharePoint CDN 中資料的存取受到 Office 365 使用者權限和權杖的授權。 在 Office 365 SharePoint CDN 資料要求必須參照 （重新導向） 從您的 Office 365 租用戶或將不會產生的授權權杖。

若要確保您的資料會保持安全，我們建議您永遠不會儲存在使用者的內容或其他敏感資料在公用 CDN。 存取公用 CDN 中的資料為匿名，因為公用 Cdn 應該只用於主控 web 指令碼檔案、 圖示、 圖像及其他非機密資產之類的一般內容。

> [!NOTE]
> 3rd 廠商 CDN 提供者可能會有不同於所述的 Office 365 信任中心的承諾的隱私權和法規遵循標準。 透過 CDN 服務快取的資料可能不符合到 Microsoft 資料處理合約 (DPT)，且可能會在 Office 365 信任中心合規性界限之外。

深入資訊的隱私權和資料保護 Office 365 CDN 提供者的詳細資訊，請造訪下列各項：  

- 深入了解 Office 365 的隱私權和資料保護，在[Microsoft 信任中心](https://www.microsoft.com/trustcenter)
- 深入了解 Akamai 的隱私權和資料保護在[Akamai 隱私權信任中心](https://www.akamai.com/us/en/about/compliance/data-protection-at-akamai.jsp)
- 深入了解 Azure 的隱私權和資料保護在[Azure 的 [信任中心](https://azure.microsoft.com/en-us/overview/trusted-cloud/)

## <a name="how-can-i-secure-my-network-with-all-these-3rd-party-services"></a>如何保護我的網路，具有所有這些 3rd 廠商服務？

利用廣泛的協力廠商服務可讓 Office 365 擴充和符合可用性需求，以及使用 Office 365 時強化使用者體驗。 Office 365 採用 3rd 廠商服務包含兩個憑證撤銷清單;例如 crl.microsoft.com 或 sa.symcb.com 和 Cdn;例如 r3.res.outlook.com。 每個 Office 365 所產生的 CDN FQDN 是 Office 365 自訂 FQDN。 如果您正在傳送到 Office 365 要求的 FQDN 您可以確保 CDN 提供者控制 FQDN 並在該位置的基礎內容。
  
客戶，要隔離目的地要求目的地為 3rd 廠商，從 Microsoft 或 Office 365 資料中心的要求我們已在[管理 Office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)上寫向上指引。

## <a name="is-there-a-list-of-all-the-fqdns-that-leverage-cdns"></a>是否有利用 Cdn 的所有 Fqdn 的清單？

Fqdn 的清單，以及它們如何運用 Cdn 變更一段時間。 我們已發佈之參照可以利用 Cdn 的最新 Fqdn 取得最新的[Office 365 Url 和 IP 位址範圍](https://go.microsoft.com/fwlink/p/?LinkID=293744)] 頁面。

您也可以使用[Office 365 IP 位址和 URL Web 服務](https://docs.microsoft.com/en-us/office365/enterprise/office-365-ip-web-service)要求的目前 Office 365 Url 和 IP 位址範圍格式化為 CSV 或 JSON。

## <a name="can-i-use-my-own-cdn-and-cache-content-on-my-local-network"></a>可以在我的區域網路使用我自己 CDN 及快取的內容？

我們不斷正在尋找新的方法來支援我們的客戶的需求，目前瀏覽使用快取 proxy 解決方案和其他在內部部署 CDN 解決方案。

雖然不 CDN 將 Office 365 的一部分，您也可以使用**Azure CDN**主控自訂網頁組件、 文件庫及其他資源的資產，可讓您套用至您 CDN 儲存體的便捷鍵，並執行更能掌控 CDN 組態。 使用 Azure CDN 釋出，並不需要 Azure 訂用帳戶。 如需有關如何設定 Azure CDN 執行個體的詳細資訊，請參閱[快速入門： 與 Azure CDN 整合 Azure 儲存體帳戶](https://docs.microsoft.com/en-us/azure/cdn/cdn-create-a-storage-account-with-cdn)。

## <a name="im-using-azure-expressroute-for-office-365-does-that-change-things"></a>我使用 Azure ExpressRoute for Office 365，不會變更事項嗎？

[Azure ExpressRoute for Office 365](azure-expressroute.md)提供從公用的網際網路專用的連線隔離的 Office 365 基礎結構。 這表示用戶端仍將需要透過非 ExpressRoute 連線以連線到 Cdn 和其他 Microsoft 基礎結構，不明確包含清單中的 ExpressRoute 所支援的服務連線。 如需如何路由傳送特定的流量，例如要求目的地 Cdn 的詳細資訊，請參閱[管理 Office 365 網路流量](routing-with-expressroute.md)。

## <a name="can-i-use-cdns-with-sharepoint-server-on-premises"></a>可以使用 Cdn 與 SharePoint Server 內部部署嗎？

使用 Cdn 僅合理的 SharePoint Online 內容中，但應避免使用，與 SharePoint Server。 這是因為所有周圍的地理位置的優點不保留 true 是表示如果伺服器是位於的內部或地理位置還是關閉。 此外，如果沒有網路連線至架設所在的伺服器，然後網站可能使用的網際網路連線並因此無法擷取 CDN 檔案。 否則，您應該使用 CDN，如果沒有一個可用，而且您的網站需要穩定的文件庫和檔案。
  
您可以使用下列短連結返回這裡：[https://aka.ms/o365cdns](https://aka.ms/o365cdns)
  
## <a name="see-also"></a>另請參閱

[Office 365 網路連線原則](https://aka.ms/o365networkingprinciples)

[對 Office 365 的網路連線](network-connectivity.md)

[管理 Office 365 端點](https://docs.microsoft.com/en-us/office365/enterprise/managing-office-365-endpoints)

[Office 365 URL 與 IP 位址範圍](https://go.microsoft.com/fwlink/p/?LinkID=293744)

[使用 SharePoint Online 中使用 Office 365 內容傳遞網路](https://docs.microsoft.com/en-us/office365/enterprise/use-office-365-cdn-with-spo)

[Microsoft 信任中心](https://www.microsoft.com/trustcenter)