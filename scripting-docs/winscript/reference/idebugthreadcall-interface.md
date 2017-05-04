---
title: "IDebugThreadCall (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugThreadCall (interfaz)"
ms.assetid: 9a9a9892-f310-4ef3-8db2-4f868be52d7e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugThreadCall (Interfaz)
La interfaz de `IDebugThreadCall` implementan normalmente por un componente que realice llamadas entre subprocesos con `IDebugThread` que constituye la implementación proporcionada por el administrador de proceso \(PDM\) de depuración.  
  
 El PDM llama a la interfaz de `IDebugThreadCall` en el subproceso deseado, y la interfaz de `IDebugThreadCall` envía la llamada a la implementación deseada.  La interfaz de `IDebugThreadCall` convierte la información de parámetros pasada a los parámetros a la parte superior adecuada.  
  
 La interfaz de `IDebugThreadCall` es un objeto libre\- con.  
  
## Métodos  
 Además de los métodos heredados de `IUnknown`, la interfaz `IDebugThreadCall` expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugThreadCall::ThreadCallHandler](../../winscript/reference/idebugthreadcall-threadcallhandler.md)|Llamadas de identificadores para ejecutar código en otro subproceso.|