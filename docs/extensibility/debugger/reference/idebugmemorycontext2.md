---
title: "IDebugMemoryContext2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryContext2"
helpviewer_keywords: 
  - "Interfaz IDebugMemoryContext2"
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugMemoryContext2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz representa una posición en el espacio de direcciones del equipo que ejecuta el programa que se depura.  
  
## Sintaxis  
  
```  
IDebugMemoryContext2 : IUnknown  
```  
  
## Notas para los implementadores  
 El motor de depuración \(DE\) implementa esta interfaz para representar una dirección en memoria.  
  
## Notas para los llamadores  
 una llamada a [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) o a [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) devuelve esta interfaz.  Además, las llamadas copias de retorno de [Add](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) y de [Restar](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) a nuevas de esta interfaz después de la operación aritmética adecuada se han aplicado.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugMemoryContext2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|obtiene el nombre usuario\-mostrable para este contexto.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Obtiene información que describe este contexto.|  
|[Add](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Agrega un valor especificado a la dirección actual de contexto para crear un nuevo contexto.|  
|[Restar](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Resta un valor especificado de la dirección actual de contexto para crear un nuevo contexto.|  
|[Comparar](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|Compara dos contextos de la manera indicada por comparan los marcadores.|  
  
## Comentarios  
 La ventana de **Memoria** de Visual Studio llama [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) para obtener la interfaz de `IDebugMemoryContext2` que contiene la expresión evaluada utilizada para la dirección de memoria.  Este contexto se pasa a [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) y a [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) para especificar la dirección de lectura o escritura.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)   
 [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)   
 [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)