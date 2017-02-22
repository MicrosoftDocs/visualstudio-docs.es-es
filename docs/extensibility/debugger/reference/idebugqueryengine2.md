---
title: "IDebugQueryEngine2 | Microsoft Docs"
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
  - "IDebugQueryEngine2"
helpviewer_keywords: 
  - "Interfaz IDebugQueryEngine2"
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugQueryEngine2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz permite al administrador \(SDM\) de depuración de sesión recuperar una interfaz que representa el motor de depuración \(DE\).  
  
## Sintaxis  
  
```  
IDebugQueryEngine2 : IUnknown  
```  
  
## Notas para los implementadores  
 El OF implementa esta interfaz en los objetos que implementan a la mayoría de common OF interfaces \(como [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md), [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md), y [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)\) para permitir el acceso a la interfaz de [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) de sí mismo.  
  
## Notas para los llamadores  
 Llame a [QueryInterface](/visual-cpp/atl/queryinterface) en un OF típico interface para obtener esta interfaz.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugQueryEngine2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Obtiene una interfaz personalizada del \(DE\) motor de depuración.|  
  
## Comentarios  
 Esta interfaz se implementa normalmente en el objeto que implementa la interfaz de [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) para admitir el recorrido causalidad\-ordenado con funciones; es decir, cuando el depurador está pasando de una función, la función siguiente a ejecuta puede no ser la función anterior en la pila pero una función en otro subproceso en conjunto.  Para una definición de “causalidad”, vea [Glosario del depurador de Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)