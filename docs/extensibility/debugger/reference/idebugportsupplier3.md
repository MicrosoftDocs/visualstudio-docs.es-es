---
title: "IDebugPortSupplier3 | Microsoft Docs"
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
  - "IDebugPortSupplier3"
helpviewer_keywords: 
  - "Interfaz IDebugPortSupplier3"
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortSupplier3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz permite a un llamador determinar si un proveedor de puerto puede conservar puertos \(escribiéndolos en disco\) entre las invocaciones del depurador y obtener una lista de los puertos conservar.  
  
## Sintaxis  
  
```  
IDebugPortSupplier3 : IDebugPortSupplier2  
```  
  
## Notas para los implementadores  
 Un proveedor de puerto implementa esta interfaz para admitir la persistencia o guardar información de puerto en el disco.  esta interfaz se debe implementar en el mismo objeto que la interfaz de [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) .  
  
## Notas para los llamadores  
 Llame a [QueryInterface](/visual-cpp/atl/queryinterface) en la interfaz de `IDebugPortSupplier2` para obtener esta interfaz.  
  
## métodos en el orden de Vtable  
 Además de los métodos heredados de la interfaz de [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) , esta interfaz admite lo siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Devuelve si el proveedor de puerto puede conservar los puertos \(escribiéndolos en disco\) entre las invocaciones del depurador.|  
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Devuelve un objeto que se puede usar para enumerar en todos los puertos que se escriben en el disco por este proveedor de puerto.|  
  
## Comentarios  
 Si un proveedor de puerto puede conservar los puertos a través de invocación, debe implementar esta interfaz.  Los puertos deben cargarse cuando el proveedor de puerto se crea instancias, y se escribe en el disco cuando se destruye el proveedor de puerto.  
  
 Un motor de depuración no interactúa normalmente con un proveedor de puerto y no tendrá ningún uso en esta interfaz.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)