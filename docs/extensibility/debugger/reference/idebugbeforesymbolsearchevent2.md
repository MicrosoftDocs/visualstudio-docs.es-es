---
title: "IDebugBeforeSymbolSearchEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaz IDebugBeforeSymbolSearchEvent2"
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugBeforeSymbolSearchEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

El motor de depuración \(DE\) envía esta interfaz al administrador \(SDM\) de depuración de la sesión para establecer el mensaje de la barra de estado durante carga de símbolos.  
  
## Sintaxis  
  
```  
IDebugBeforeSymbolSearchEvent2 : IUnknown  
```  
  
## Notas para los implementadores  
 El OF implementa esta interfaz cuando debe establecer el mensaje de la barra de estado durante carga de símbolos.  Esta interfaz se implementa únicamente los motores de depuración que ejecutan o es una parte de intérpretes de script.  la interfaz de [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) se debe implementar en el mismo objeto que esta interfaz \(el SDM utiliza **QueryInterface** para tener acceso a la interfaz **IDebugEvent2** \).  
  
## Notas para los llamadores  
 El OF crea y envía este objeto event cuando debe establecer el mensaje de la barra de estado durante carga de símbolos.  El evento se envía mediante la función de devolución de llamada de [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) proporcionada por el SDM cuando adjuntó el programa que se depura.  
  
## Métodos  
 La tabla siguiente se muestran los métodos de `IDebugBeforeSymbolSearchEvent2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|Recupera el nombre del módulo que se está depurando actualmente.|  
  
## Requisitos  
 encabezado: Msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll