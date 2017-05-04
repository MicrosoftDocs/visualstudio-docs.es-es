---
title: "IWebAppDiagnosticsSetup (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IWebAppDiagnosticsSetup (Interfaz)"
ms.assetid: ec7359f2-633e-4d59-b64b-9cab0134dfd0
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IWebAppDiagnosticsSetup (Interfaz)
Esta interfaz se implementa mediante una aplicación de depuración de PDM para crear objetos COM en el proceso que se está depurando y habilitar diagnósticos web.  Si instrumenta [IObjectWithSite](http://go.microsoft.com/fwlink/?LinkId=232438)del objeto application de depuración de PDM, llamadas [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) de Internet Explorer en él después de haber creado y los pasos de una referencia a [IWebBrowser2](http://go.microsoft.com/fwlink/?LinkId=232449).  Las llamadas [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) y los pasos de una aplicación de WWA en el WWA comunican IWebApplicationHost en su lugar.  Si [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) se ha denominado con un valor NULL, [IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) devuelve true.  De lo contrario, devuelve false y las llamadas a [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) darán error.  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsSetup` es implementado por PDM v11.0 y mayor.  Encontrado en activdbg100.h.  
  
## Métodos  
 Esta interfaz expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|Obtiene los documentos de texto que son ocultados por el filtro especificado.|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|Determina si el documento especificado pertenece a uno de los nodos secundarios de este nodo.|