---
title: "IWebAppDiagnosticsObjectInitialization::Initialize | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IWebAppDiagnosticsObjectInitialization::Initialize"
ms.assetid: 7ccfac28-9f65-4e1c-a0fb-a8a6c7f75b63
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IWebAppDiagnosticsObjectInitialization::Initialize
Inicializan objetos creados con [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md).  
  
> [!IMPORTANT]
>  [IWebAppDiagnosticsObjectInitialization \(Interfaz\)](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md) se encuentra en activdbg100.h.  
  
## Sintaxis  
  
```cpp  
HRESULT Initialize(  
        [in, annotation("__in")] HANDLE_PTR hPassedHandle,  
        [in, annotation("__in")] IUnknown* pDebugApplication  
        );  
```  
  
#### Parámetros  
 `hPassedHandle`  
 El identificador que se pasó al método de [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) en el parámetro de `hPassToObject` .  
  
 `pDebugApplication`  
 La aplicación de PDM con la que se creó el objeto.