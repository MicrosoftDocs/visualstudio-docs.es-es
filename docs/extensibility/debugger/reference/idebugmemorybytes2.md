---
title: "IDebugMemoryBytes2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryBytes2"
helpviewer_keywords: 
  - "Interfaz IDebugMemoryBytes2"
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugMemoryBytes2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

esta interfaz representa bytes de memoria.  
  
## Sintaxis  
  
```  
IDebugMemoryBytes2 : IUnknown  
```  
  
## Notas para los implementadores  
 El motor de depuración \(DE\) implementa esta interfaz para representar bytes en memoria.  
  
## Notas para los llamadores  
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) devuelve esta interfaz para proporcionar acceso a la memoria del sistema.  [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) y [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) devuelven esta interfaz para proporcionar acceso a los bytes de un objeto.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugMemoryBytes2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|Lee una secuencia de bytes, comenzando en una ubicación determinada.|  
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|escribe los bytes de `dwCount` , comenzando en `pStartContext`.|  
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|Obtiene el tamaño, en bytes, de memoria representada por esta interfaz.|  
  
## Comentarios  
 Para las propiedades, una interfaz de [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que representa una matriz proporciona una interfaz de `IDebugMemoryBytes2` para tener acceso a los valores de esa matriz.  
  
 **Vista de memoria** de Visual Studio llama [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) para recuperar una interfaz de `IDebugMemoryBytes2` para la memoria del sistema de acceso.  Evaluar obtiene la dirección se alcance analizando la expresión especificada como dirección en la vista de memoria y la expresión analizada mediante [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) para obtener una interfaz de `IDebugProperty2` .  Una llamada a [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) devuelve [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) que describe la dirección de memoria.  Este contexto de memoria se pasa a [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) y a [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md).  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)