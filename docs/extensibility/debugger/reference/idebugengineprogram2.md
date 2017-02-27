---
title: "IDebugEngineProgram2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineProgram2"
helpviewer_keywords: 
  - "Interfaz IDebugEngineProgram2"
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugEngineProgram2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz proporciona compatibilidad multiproceso de depuración.  
  
## Sintaxis  
  
```  
IDebugEngineProgram2 : IUnknown  
```  
  
## Notas para los implementadores  
 Un motor de depuración implementa esta interfaz para admitir la depuración simultánea de varios subprocesos.  esta interfaz se implementa en el mismo objeto que implementa la interfaz de [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) .  
  
## Notas para los llamadores  
 utilice [QueryInterface](/visual-cpp/atl/queryinterface) para obtener esta interfaz de una interfaz de `IDebugProgram2` .  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugEngineProgram2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Detener](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Detiene todos los subprocesos ejecutándose en este programa.|  
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|Observe que la ejecución \(o detención que observa para la ejecución\) aparezcan en el subproceso especificado.|  
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Permite o deniega\) la evaluación de la expresión aparece en el subproceso especificado, incluso si se detiene el programa.|  
  
## Comentarios  
 Visual Studio llama a esta interfaz en respuesta a un evento de [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) y establecer “reloj para el paso del subproceso” y “reloj para la evaluación de expresiones en los estados del subproceso” del programa.  Se llama[Detener](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) siempre que el programa debe detener; este método da al programa una oportunidad de finalizar todos los subprocesos.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)