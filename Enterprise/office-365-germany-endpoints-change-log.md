---
title: Office 365 德國端點變更記錄檔
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid: MOE150
ms.assetid: 980041c9-7984-44b2-95f0-af66743543a1
ms.openlocfilehash: e77d6fc3b8136f39ed75ef21b0ff417a4ad6465a
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540166"
---
# <a name="office-365-germany-endpoints-change-log"></a>Office 365 德國端點變更記錄檔

*適用於： Office 365 系統管理*

## <a name="list-of-changes-to-the-endpoints-required-for-office-365-germany"></a>變更所需的 Office 365 德國之端點的清單

下表列出[Office 365 德國端點](office-365-germany-endpoints.md)的變更。
  
|**日期**|**變更**|
|:-----|:-----|
|1/24/2017  <br/> |文章的初步的內容。  <br/> |
|2/28/2017  <br/> |新增 3 Fqdn ；1 / [有效 4/1/2017。必要： Office 365 入口網站和共用。ExpressRoute： [否]。www.office.de] 2 / [有效 4/1/2017。必要： Office 365 入口網站和共用。ExpressRoute： [否]。office.de]、 3 / [有效 4/1/2017。必要： Office 365 入口網站和共用。ExpressRoute： [否]。officehome.msocdn.de]。 附註： 新增其他入口網站 Fqdn。 新增 2 IP_Sets;1 / [有效 4/1/2017。必要： Office 365 入口網站和共用。ExpressRoute： 否 51.5.245.67/32]、 2 / [有效 4/1/2017。必要： Office 365 入口網站和共用。ExpressRoute： 否 51.4.227.178/32]。附註： 新增其他的入口網站端點。新增 2 IP_Sets;1 / [有效 4/1/2017。必要： Office 365 入口網站和共用。ExpressRoute： 否 2a01:4180:2001::92]、 2 / [有效 4/1/2017。必要： Office 365 入口網站和共用。ExpressRoute： 否 2a01:4180:2401::11f]。附註： 新增其他的入口網站端點。  <br/> |
|3/8/2017  <br/> |新增 1 Fqdn ；1 / [有效 3/8/2017。必要： OneDrive for Business。ExpressRoute： [否]。spoprod-a.akamaihd.net]、。附註： 新增其他 CDN 端點。  <br/> |
|3/31/2017  <br/> |新增 3 Fqdn ；1 / [有效 5/1/2017。必要： SharePoint Online 混合式。\*。 search.production.de.azuretrafficmanager.de]、 2 / [有效 5/1/2017。必要： SharePoint Online 混合式。login.microsoftonline.de]、 3 / [有效 5/1/2017。必要： SharePoint Online 混合式。provisioningapi.microsoftonline.de]。 附註： 新增 Sharepoint 混合式 Fqdn。  <br/> |
|6/1/2017  <br/> |新增 2 Fqdn 有效 7/1/2017年  <br/> shellprod.msocdn.de  <br/> r1.res.office365.com  <br/> |
|6/26/2017  <br/> |取代自動探索\*。 Autodiscover.outlook.de 和自動探索 outlook.office.de outlook.de。  <br/> |
|9/29/2017  <br/> |新增 3 Fqdn ；1 / [有效 11/1/2017。  <br/> cegsignup.microsoft.de  <br/> negsignup.microsoft.de  <br/> \*。 svc.ms  <br/> |
|1/16/2018  <br/> |新增 1 Fqdn ；1 / [有效 2/1/2018。必要： Office 365 入口網站。ExpressRoute： [否]。webshell.suite.office.de]。 附註： 新增其他 Office 365 套裝軟體命令介面的 FQDN。新增 4 IP_Sets;1 / [有效 2/1/2018。必要： Office 365 入口網站。ExpressRoute： 否 51.5.242.163/32]、 2 / [有效 2/1/2018。必要： Office 365 入口網站。ExpressRoute： 否 51.4.226.115/32]、 3 / [有效 2/1/2018。必要： Office 365 入口網站。ExpressRoute： 否 2a01:4180:2401::33b / 4 / [有效 2/1/2018。必要： Office 365 入口網站。ExpressRoute： 否 2a01:4180:2001::234 / 附註： 新增其他 Office 365 套裝軟體命令介面的 IP 位址。  <br/> |
|2/5/2018  <br/> |新增 1 FQDN ； 1 / [有效 3/1/2018。必要： 入口網站和共用。ExpressRoute: [是]。webshell.suite.office.de]。 附註： 入口網站與共用的 Fqdn。 新增 2 IP_Sets; 新增 URL1 / [有效 3/1/2018。必要： 入口網站和共用。ExpressRoute: [是]。51.5.242.163/32]。、 2 / [有效 3/1/2018。必要： 入口網站和共用。ExpressRoute: [是]。51.4.226.115/32]。附註： 新增新的入口網站字首和共用。新增 2 IP_Sets;1 / [有效 3/1/2018。必要： 入口網站和共用。ExpressRoute: [是]。2a01:4180:2401::33b / 128]。、 2 / [有效 3/1/2018。必要： 入口網站和共用。ExpressRoute: [是]。2a01:4180:2001::234 / 128]。附註： 新增新的入口網站字首和共用。新增 1 IP_Sets;1 / [有效 3/1/2018。必要： Office Online。ExpressRoute: [是]。51.18.16.0/23]。附註： 新增 Office Online 的新的前置詞。  <br/> |
|3/15/2018  <br/> |新增 1 IP_Set;1 / [有效 4/15/2018。必要： Office 365 ProPlus。ExpressRoute： 否 51.18.0.0/21]。附註： 新增 Office 365 ProPlus 的端點。  <br/> |
|7/2/2018  <br/> |移除 1 FQDN ；1 / [有效 8/1/2018。必要： OneDrive for Business。ExpressRoute： [否]。login.microsoftonline.de]。 附註： 移除 OneDrive for Business 端點。移除 11 Fqdn ；1 / [有效 8/1/2018。必要： Office Mobile。ExpressRoute： 否https://excelps.osi.office.de/exlps/excelprint.svc/exlPrint]、 2 / [有效 8/1/2018。必要： Office Mobile。ExpressRoute： 否https://wordps.osi.office.de/wrdps/wordprint.svc/wrdprint]、 3 / [有效 8/1/2018。必要： Office Mobile。ExpressRoute： 否https://wordcs.osi.office.de/wordauto/wordautomation.svc/wordautomation]、 4 / [有效 8/1/2018。必要： Office Mobile。ExpressRoute： 否https://wordcs.osi.office.de/wordauto/wordautomation.svc/rest]、 5 / [有效 8/1/2018。必要： Office Mobile。ExpressRoute： 否https://pptps.osi.office.de/pptps/powerpointprint.svc/PptPrint]、 6 / [有效 8/1/2018。必要： Office Mobile。ExpressRoute： 否https://pptcs.osi.office.de/pptauto/PowerpointAutomation.svc/PptAutomation]、 7 / [有效 8/1/2018。必要： Office Mobile。ExpressRoute： 否https://pptcs.osi.office.de/pptauto/PowerpointAutomation.svc/rest]、 8 / [有效 8/1/2018。必要： Office Mobile。ExpressRoute： 否https://ols.osi.office.de/]、 9 / [有效 8/1/2018。必要： Office Mobile。ExpressRoute： 否https://ols.osi.office.de/olsc/OlsClient.svc/OlsClient]、 10 / [有效 8/1/2018。必要： Office Mobile。ExpressRoute： 否https://excelcs.osi.office.de/xlauto/excelautomation.svc/XlAutomation]、 11 / [有效 8/1/2018。必要： Office Mobile。ExpressRoute： 否https://excelcs.osi.office.de/xlauto/excelautomation.svc/rest]。附註： 移除 Office Mobile 端點。  <br/> |
   

