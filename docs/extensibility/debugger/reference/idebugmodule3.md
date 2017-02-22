---
title: "IDebugModule3 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModule3"
helpviewer_keywords: 
  - "Interfaz IDebugModule3"
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugModule3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz representa un módulo que admite ubicaciones alternativas de símbolos y de los estados de JustMyCode.  
  
## Sintaxis  
  
```  
IDebugModule3 : IDebugModule2  
```  
  
## Notas para los implementadores  
 El motor de depuración \(DE\) implementa esta interfaz para admitir ubicaciones alternativas de símbolos y para trabajar con los estados de JustMyCode \(vea [Glosario del depurador de Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) para una definición de “JustMyCode”\).  
  
## Notas para los llamadores  
 una llamada a [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) devuelve esta interfaz.  El OF envía la interfaz de [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) el administrador de depuración de sesión \(SDM\) mediante el método de [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) .  Además, una llamada a [QueryInterface](/visual-cpp/atl/queryinterface) en una interfaz de [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) devuelve esta interfaz.  
  
## métodos en el orden de Vtable  
 Además de los métodos de la interfaz de [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) , esta interfaz implementa los siguientes métodos:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Devuelve una lista de rutas de búsqueda para los símbolos y los resultados de búsqueda cada ruta.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|Las cargas y se inicializan los símbolos del módulo actual.|  
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Devuelve la marca que especifica si el módulo representa el código de usuario.|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|Especifica si el módulo debe considerarse código de usuario o no.|  
  
## Comentarios  
 Visual Studio es el consumidor típico de esta interfaz.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)   
 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)