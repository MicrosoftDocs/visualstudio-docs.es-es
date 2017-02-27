---
title: "CONTEXT_COMPARE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CONTEXT_COMPARE"
helpviewer_keywords: 
  - "Enumeración CONTEXT_COMPARE"
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# CONTEXT_COMPARE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

especifica los criterios para comparar dos contextos de memoria.  
  
## Sintaxis  
  
```cpp#  
enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
typedef DWORD CONTEXT_COMPARE;  
```  
  
```c#  
public enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
```  
  
## Members  
 CONTEXT\_EQUAL  
 Busque el primer contexto de memoria en la lista que es igual al contexto de memoria de destino.  
  
 CONTEXT\_LESS\_THAN  
 Busque el primer contexto de memoria en la lista que es menor que el contexto de memoria de destino.  
  
 CONTEXT\_GREATER\_THAN  
 Busque el primer contexto de memoria en la lista que es mayor que el contexto de memoria de destino.  
  
 CONTEXT\_LESS\_THAN\_OR\_EQUAL  
 Busque el primer contexto de memoria en la lista que es menor o igual que el contexto de memoria de destino.  
  
 CONTEXT\_GREATER\_THAN\_OR\_EQUAL  
 Busque el primer contexto de memoria en la lista que es mayor o igual que el contexto de memoria de destino.  
  
 CONTEXT\_SAME\_SCOPE  
 Busque el primer contexto de memoria en la lista que está en el mismo ámbito que el contexto de memoria de destino.  
  
 CONTEXT\_SAME\_FUNCTION  
 Busque el primer contexto de memoria en la lista que está en la misma función que el ámbito de memoria de destino.  
  
 CONTEXT\_SAME\_MODULE  
 Busque el primer contexto de memoria en la lista que está en el mismo módulo que el contexto de memoria de destino.  
  
 CONTEXT\_SAME\_PROCESS  
 Busque el primer contexto de memoria en la lista que está en el mismo proceso que el contexto de memoria de destino.  
  
## Comentarios  
 Pasado como argumento al método de [Comparar](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) .  
  
 Estos valores se utilizan para buscar el primer contexto de memoria en una lista que cumple los criterios especificados de la comparación.  Un contexto de memoria se proporciona una lista de los contextos de memoria para compararse con con el método de `IDebugMemoryContext2::Compare` .  El primer contexto de memoria en la lista para la cual el operador de comparación es `true` se devuelve.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Comparar](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)