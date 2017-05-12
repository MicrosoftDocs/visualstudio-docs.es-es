---
title: "IWebAppDiagnosticsObjectInitialization (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IWebAppDiagnosticsObjectInitialization (Interfaz)"
ms.assetid: 32847838-01d9-4205-a811-3043d8c7a917
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IWebAppDiagnosticsObjectInitialization (Interfaz)
Esta interfaz se puede implementar en las clases que implementan [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md).  [IWebAppDiagnosticsSetup \(Interfaz\)](../../winscript/reference/iwebappdiagnosticssetup-interface.md) es implementado por el objeto que implementa [IDebugApplication \(Interfaz\)](../../winscript/reference/idebugapplication-interface.md).  En la mayoría de los casos este objeto es el PDM.  
  
 Después de crear el objeto, [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) lleva una referencia a la aplicación de depuración de PDM y el parámetro de `hPassToObject` de `CreateObjectWithSiteAtWebApp`.  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsObjectInitialization` se encuentra en activdbg100.h.  
  
## Métodos  
 Esta interfaz expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md)|Inicializa el objeto.|