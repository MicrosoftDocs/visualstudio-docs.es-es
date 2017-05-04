---
title: "IWebAppDiagnosticsSetup::DiagnosticsSupported | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IWebAppDiagnosticsSetup::DiagnosticsSupported"
ms.assetid: 5bbcd0d0-1460-4cf7-bbb1-f4f4a04f739a
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IWebAppDiagnosticsSetup::DiagnosticsSupported
Determina si los diagnósticos se admiten en esta aplicación.  Si [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) se ha asignado el objeto que implementa esta interfaz con un valor NULL, [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) devuelve `true`.  De lo contrario, devuelve `false` y las llamadas a [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) darán error.  
  
> [!IMPORTANT]
>  [IWebAppDiagnosticsSetup \(Interfaz\)](../../winscript/reference/iwebappdiagnosticssetup-interface.md) es implementado por PDM v11.0 y mayor.  Encontrado en activdbg100.  
  
## Sintaxis  
  
```cpp  
HRESULT DiagnosticsSupported(  
        [out, retval] VARIANT_BOOL* pRetVal  
        );  
```  
  
#### Parámetros  
 `pRetVal`  
 Si [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) se ha asignado el objeto que implementa esta interfaz con un valor NULL, [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) devuelve `true`.  De lo contrario, devuelve `false`, y las llamadas a [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) darán error.