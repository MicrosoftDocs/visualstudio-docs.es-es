---
title: "IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp"
ms.assetid: 30975973-acb1-48f4-8266-5e097a57db22
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
Este método co\- crea la clase cuyo id. se pasa con `rclsid` mediante `dwClsContext`.  Esto es similar a la manera en que funciona [IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md) , salvo que en el caso de `CreateObjectWithSiteAtWebApp` el objeto se crea de forma asincrónica en el subproceso de la interfaz de usuario de la aplicación Web.  El objeto especificado por el id. de la clase debe implementar [IWebAppDiagnosticsObjectInitialization \(Interfaz\)](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md).  Después de crear el objeto, [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) lleva una referencia a la aplicación de depuración de PDM y el parámetro de `hPassToObject` de `CreateObjectWithSiteAtWebApp`.  Puede utilizar este método para pasar la aplicación un identificador a una canalización anónima [DuplicateHandle](http://go.microsoft.com/fwlink/?LinkId=232450)de que haya copiado.  
  
> [!IMPORTANT]
>  [IWebAppDiagnosticsSetup \(Interfaz\)](../../winscript/reference/iwebappdiagnosticssetup-interface.md) es implementado por PDM v11.0 y mayor.  Encontrado en activdbg100.h.  
  
## Sintaxis  
  
```cpp  
HRESULT CreateObjectWithSiteAtWebApp(  
        [in] REFCLSID rclsid,   
        [in] DWORD dwClsContext,   
        [in] REFIID riid,   
        [in] DWORD_PTR hPassToObject  
        );  
  
```  
  
#### Parámetros  
 `rclsid`  
 El id. de clase de la clase a crear.  
  
 `dwClsContext`  
 El contexto en el que el código se ejecutará.  En la mayoría de los casos es CLSCTX\_INPROC\_SERVER.  
  
 `riid`  
 No se utiliza.  
  
 `hPassToObject`  
 Un valor que se pasa al objeto una vez que se crea en el subproceso de la interfaz de usuario, si el objeto implementa [IWebAppDiagnosticsObjectInitialization \(Interfaz\)](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md).