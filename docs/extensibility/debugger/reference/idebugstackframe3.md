---
title: "IDebugStackFrame3 | Microsoft Docs"
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
  - "IDebugStackFrame3"
helpviewer_keywords: 
  - "Interfaz IDebugStackFrame3"
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugStackFrame3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz extiende [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) para controlar excepciones interceptadas.  
  
## Sintaxis  
  
```  
IDebugStackFrame3 : IDebugStackFrame2  
```  
  
## Notas para los implementadores  
 El motor de depuración \(DE\) implementa esta interfaz en el mismo objeto que implementa la interfaz de [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) para admitir excepciones interceptadas.  
  
## Notas para los llamadores  
 Llame a [QueryInterface](/visual-cpp/atl/queryinterface) en una interfaz de `IDebugStackFrame2` para obtener esta interfaz.  
  
## métodos en el orden de Vtable  
 además de los métodos heredados de [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md), `IDebugStackFrame3` expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Controla una excepción para el marco de pila actual antes del control de excepciones regular.|  
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Devuelve un contexto de código si una pila desenredo era aparezca.|  
  
## Comentarios  
 Una excepción intercepta significa que un depurador puede procesar una excepción antes de cualquier excepción normal que administra las rutinas se denomina por el tiempo de ejecución.  La interceptación de una excepción básicamente significa que crear el tiempo de ejecución finja que ya habrá un de controlador de excepciones incluso cuando no hay.  
  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) se denomina durante todos los eventos normales de devolución de llamada de excepción \(la única excepción a esto es si se está depurando el código en modo mixto \(administrado y código no administrado\), en cuyo caso la excepción no se puede interceptar durante la devolución de llamada de pasado\-ocasión\).  Si el OF no implementa `IDebugStackFrame3`, o el OF devuelve un error de IDebugStackFrame3::`InterceptCurrentException` \(como `E_NOTIMPL`\), el depurador controlará la excepción normalmente.  
  
 Interceptando una excepción, el depurador puede permitir que el usuario realice cambios en el estado del programa que se depura y después reanude la ejecución en el punto donde se produjo la excepción.  
  
> [!NOTE]
>  Las excepciones interceptadas sólo se permiten en código administrado, es decir, en un programa que se ejecuta en Common Language \(CLR\) Runtime.  
  
 Un motor de depuración indica que admite las excepciones de interceptación estableciendo “metricExceptions” en un valor de 1 en tiempo de ejecución mediante la función de `SetMetric` .  Para obtener más información, vea [Aplicaciones auxiliares SDK para la depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [Aplicaciones auxiliares SDK para la depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)