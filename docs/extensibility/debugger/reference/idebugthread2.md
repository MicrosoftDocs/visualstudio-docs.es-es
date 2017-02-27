---
title: "IDebugThread2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThread2"
helpviewer_keywords: 
  - "Interfaz IDebugThread2"
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugThread2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz representa un subproceso que se está ejecutando en un programa.  
  
## Sintaxis  
  
```  
IDebugThread2 : IUnknown  
```  
  
## Notas para los implementadores  
 El motor de depuración \(DE\) implementa esta interfaz para representar un subproceso de ejecución en un único programa.  
  
## Notas para los llamadores  
 Llame a [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md) para obtener esta interfaz que representa actualmente el subproceso activo.  
  
 Esta interfaz también se utiliza en crear una solicitud de punto de interrupción \(vea [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)\).  
  
 Esta interfaz también se devuelve al resolver un punto de interrupción del límite o de error \(vea [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) y [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)\).  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugThread2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|recupera una lista de los marcos de pila para este subproceso.|  
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|Obtiene el nombre del subproceso.|  
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|Establece el nombre del subproceso.|  
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|Obtiene el programa en la que se está ejecutando un subproceso.|  
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|Determina si la instrucción siguiente se puede establecer el contexto determinado del marco de pila y el código.|  
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|Establece la instrucción siguiente al contexto determinado del marco de pila y el código.|  
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|Obtiene el identificador de subproceso del sistema.|  
|[Suspender](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|suspende un subproceso.|  
|[Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)|Reanudar un subproceso.|  
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|obtiene las propiedades que describen un subproceso.|  
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|Obtiene el subproceso lógico asociado a este subproceso físico.|  
  
## Comentarios  
 Puesto que un único subproceso físico puede ejecutarse en programas múltiples, más de un `IDebugThread2` de más de un programa puede representar el mismo subproceso físico.  
  
 Cuando un punto de interrupción o una excepción, un evento es enviado llamando a [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  Uno de los argumentos de este método es una interfaz de `IDebugThread2` que representa el subproceso actual.  [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) se utiliza para obtener la interfaz de [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) para el marco de pila actual.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)