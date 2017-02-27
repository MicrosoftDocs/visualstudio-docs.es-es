---
title: "IDebugProgramEngines2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramEngines2"
helpviewer_keywords: 
  - "Interfaz IDebugProgramEngines2"
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProgramEngines2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz es utilizada por nodos de programa para especificar todos los motores \(DE\) posibles de depuración que pueden depurar este programa.  
  
## Sintaxis  
  
```  
IDebugProgramEngines2 : IUnknown  
```  
  
## Notas para los implementadores  
 Un OF o un proveedor de puerto implementa esta interfaz en el mismo objeto que implementa [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) para admitir el establecimiento de un OF específico para un programa concreto.  
  
## Notas para los llamadores  
 Llame a [QueryInterface](/visual-cpp/atl/queryinterface) en una interfaz de `IDebugProgramNode2` para obtener esta interfaz.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugProgramEngines2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|indica todo el DES posible que puede depurar este programa.|  
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|Selecciona el OF utilizar para depurar este programa.|  
  
## Comentarios  
 Una vez que un OF es elegido por el usuario, esa opción es registrada con el nodo del programa llamando a [SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md).  El motor seleccionados se convierte en el motor devuelto por [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md).  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)