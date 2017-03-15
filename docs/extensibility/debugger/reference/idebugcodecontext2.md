---
title: "IDebugCodeContext2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCodeContext2"
helpviewer_keywords: 
  - "Interfaz IDebugCodeContext2"
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugCodeContext2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz representa la posición inicial de una instrucción de código.  Para la mayoría de las arquitecturas en tiempo de ejecución actual, un contexto del código se puede considerar como dirección en una secuencia de la ejecución del programa.  
  
## Sintaxis  
  
```  
IDebugCodeContext2 : IDebugMemoryContext2  
```  
  
## Notas para los implementadores  
 El motor de depuración implementa esta interfaz para relacionar la posición de una instrucción de código con una posición del documento.  
  
## Notas para los llamadores  
 Los métodos de las interfaces devuelven esta interfaz, lo más normalmente, [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md).  También se usa mayoritariamente con la interfaz de [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) así como en la información de resolución de punto de interrupción.  
  
## métodos en el orden de Vtable  
 Además de los métodos de la interfaz de [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , esta interfaz implementa los siguientes métodos:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Obtiene el contexto del documento que corresponde al contexto activo del código.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Obtiene la información del lenguaje para este contexto de código.|  
  
## Comentarios  
 La diferencia clave entre una interfaz de `IDebugCodeContext2` y una interfaz de [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) es que `IDebugCodeContext2` siempre es instrucción\-alineado.  Esto significa que `IDebugCodeContext2` apunta siempre al principio de una instrucción, mientras que `IDebugMemoryContext2` puede señalar a cualquier byte de memoria en la arquitectura en tiempo de ejecución.  `IDebugCodeContext2` se incrementa en instrucciones en lugar de por el tamaño de almacenamiento básico \(normalmente byte\).  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)   
 [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)   
 [Siguiente](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)