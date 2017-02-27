---
title: "IDebugProgramNodeAttach2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNodeAttach2"
helpviewer_keywords: 
  - "Interfaz IDebugProgramNodeAttach2"
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
caps.latest.revision: 3
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 3
---
# IDebugProgramNodeAttach2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Permite que un nodo del programa se notifique de un intento de asociar el programa asociado.  
  
## Sintaxis  
  
```  
IDebugProgramNodeAttach2 : IUnknown  
```  
  
## Notas para los implementadores  
 Esta interfaz se implementa en la misma clase que implementa la interfaz de [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) para recibir notificación de una operación attach y proporcionar la oportunidad de cancelar la operación de asociar.  
  
## Notas para los llamadores  
 Obtiene esta interfaz llamando al método de `QueryInterface` en un objeto de [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) .  El método de [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) se debe llamar a antes del método de [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) del nodo de programa una oportunidad de detener el proceso de asociar.  
  
## métodos en el orden de Vtable  
 esta interfaz implementa el método siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Asocia el programa asociado o deja el proceso de asociar al método de [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) .|  
  
## Comentarios  
 Esta interfaz es la alternativa recomendada al método desusado de [Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) .  Todos los motores de depuración siempre se cargan con la función de `CoCreateInstance` , es decir, se crean instancias al espacio de direcciones del programa que se depura.  
  
 Si una implementación anterior del método de `IDebugProgramNode2::Attach_V7` estableciendo simplemente `GUID` de programa que se depura, sólo el método de [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) debe ser implementado.  
  
 Si una implementación anterior del método de `IDebugProgramNode2::Attach_V7` utilizó la interfaz de devolución de llamada proporcionada, después la funcionalidad necesita mover a una implementación del método de [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) y de la interfaz de `IDebugProgramNodeAttach2` no tiene que implementar.  
  
## Requisitos  
 encabezado: Msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)