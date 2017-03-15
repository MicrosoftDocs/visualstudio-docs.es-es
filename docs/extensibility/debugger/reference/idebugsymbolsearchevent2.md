---
title: "IDebugSymbolSearchEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolSearchEvent2"
helpviewer_keywords: 
  - "IDebugSymbolSearchEvent2"
ms.assetid: 9b946d55-ff85-44eb-b40a-efbf8282eafd
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugSymbolSearchEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz es enviada por el motor de depuración \(DE\) para indicar que los símbolos de depuración para un módulo que se estaba depurando cargados.  
  
## Sintaxis  
  
```  
IDebugSymbolSearchEvent2 : IUnknown  
```  
  
## Notas para los implementadores  
 El OF implementa esta interfaz para indicar que los símbolos de un módulo cargados.  la interfaz de [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) se debe implementar en el mismo objeto que esta interfaz.  El SDM utiliza [QueryInterface](/visual-cpp/atl/queryinterface) para tener acceso a la interfaz de `IDebugEvent2` .  
  
## Notas para los llamadores  
 El OF crea y envía este objeto event para indicar que los símbolos de un módulo cargados.  El evento se envía mediante la función de devolución de llamada de [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) proporcionada por el SDM cuando adjuntó el programa que se depura.  
  
## métodos en el orden de Vtable  
 la interfaz de `IDebugSymbolSearchEvent2` expone el método siguiente.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)|Información de recupera sobre los resultados de una búsqueda de símbolos.|  
  
## Comentarios  
 Este evento se enviará aunque los símbolos no pueden cargar.  La llamada `IDebugSymbolSearchEvent2::GetSymbolSearchInfo` permite al controlador de este evento determine si el módulo tiene realmente los símbolos.  
  
 Visual Studio utiliza normalmente este evento para actualizar el estado de símbolos cargados en la ventana de **Módulos** .  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)