---
title: "IDebugProgram3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaz IDebugProgram3"
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugProgram3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz representa un programa que se ejecuta en un proceso y extiende [Ejecutar](../../../extensibility/debugger/reference/idebugprogram2-execute.md) proporcionando la información del subproceso.  
  
## Sintaxis  
  
```  
IDebugProgram3 : IDebugProgram3  
```  
  
## Notas para los implementadores  
 El motor de depuración \(DE\) y un proveedor de puerto implementan esta interfaz para representar un programa en un proceso.  El administrador de depuración de la sesión \(SDM\) también implementa esta interfaz para proporcionar información a [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md).  
  
## Notas para los llamadores  
 el evento de [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) devuelve esta interfaz para un nuevo programa.  Esta interfaz también se utiliza como parámetro para muchos métodos en varias interfaces.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugProgram3`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|ejecuta el programa.  El subproceso se devuelve del depurador la información en la que el subproceso el usuario está viendo cuando se ejecutan.|  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Comentarios  
 Un programa es una ejecución del contenedor en una arquitectura determinada en tiempo de ejecución, mientras que un proceso consta de uno o más programas.  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)   
 [Siguiente](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)   
 [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)