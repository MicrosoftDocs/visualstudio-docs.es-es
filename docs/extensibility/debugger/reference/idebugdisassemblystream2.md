---
title: "IDebugDisassemblyStream2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDisassemblyStream2"
helpviewer_keywords: 
  - "Interfaz IDebugDisassemblyStream2"
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugDisassemblyStream2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

esta interfaz representa una secuencia de instrucciones.  
  
## Sintaxis  
  
```  
IDebugDisassemblyStream2 : IUnknown  
```  
  
## Notas para los implementadores  
 Un motor de depuración implementa esta interfaz para admitir el desensamblado de código de un programa.  
  
## Notas para los llamadores  
 Una llamada al método de [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) devuelve esta interfaz.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugDisassemblyStream2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Leer](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|Lee instrucciones a partir de la posición actual en la secuencia de desensamblado.|  
|[Buscar](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|Mueve el puntero de lectura en el desensamblado transmite un número especificado de instrucciones en relación con una posición especificada.|  
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|Devuelve un identificador de la ubicación del código para un contexto de código determinado.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|Devuelve un objeto de contexto del código correspondiente a un identificador especificado de la ubicación del código.|  
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|Devuelve un identificador de la ubicación del código que representa la ubicación actual del código.|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|Obtiene el documento de origen asociado con esta secuencia de desensamblado.|  
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|Obtiene el ámbito de esta secuencia de desensamblado.|  
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|Obtiene el tamaño de esta secuencia de desensamblado.|  
  
## Comentarios  
 La secuencia de desensamblado se puede crear para representar el espacio de direcciones completo o simplemente una función o un módulo dentro del espacio.  Cada instrucción se representa mediante una estructura de [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) devuelta por una llamada al método de [Leer](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) .  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)