---
title: CONTEXT_COMPARE | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CONTEXT_COMPARE
helpviewer_keywords: CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 48043375ebdf904a7fafbae5e4193b42d8ba8269
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="contextcompare"></a>CONTEXT_COMPARE
Especifica los criterios para comparar dos contextos de memoria.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_CONTEXT_COMPARE {   
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
  
```csharp  
public enum enum_CONTEXT_COMPARE {   
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
  
## <a name="members"></a>Miembros  
 CONTEXT_EQUAL  
 Busque el primer contexto de memoria en la lista que es igual que el contexto de la memoria de destino.  
  
 CONTEXT_LESS_THAN  
 Busque el primer contexto de memoria en la lista que es menor que el contexto de la memoria de destino.  
  
 CONTEXT_GREATER_THAN  
 Busque el primer contexto de memoria en la lista que es mayor que el contexto de la memoria de destino.  
  
 CONTEXT_LESS_THAN_OR_EQUAL  
 Busque el primer contexto de memoria en la lista que es menor o igual que el contexto de la memoria de destino.  
  
 CONTEXT_GREATER_THAN_OR_EQUAL  
 Busque el primer contexto de memoria en la lista que es mayor o igual que el contexto de la memoria de destino.  
  
 CONTEXT_SAME_SCOPE  
 Busque el primer contexto de memoria en la lista que se encuentra en el mismo ámbito que el contexto de la memoria de destino.  
  
 CONTEXT_SAME_FUNCTION  
 Busque el primer contexto de memoria en la lista que se encuentra en la misma función que el ámbito de la memoria de destino.  
  
 CONTEXT_SAME_MODULE  
 Busque el primer contexto de memoria en la lista que se encuentra en el mismo módulo que el contexto de la memoria de destino.  
  
 CONTEXT_SAME_PROCESS  
 Busque el primer contexto de memoria en la lista que se encuentra en el mismo proceso que el contexto de la memoria de destino.  
  
## <a name="remarks"></a>Comentarios  
 Pasa como un argumento a la [comparar](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) método.  
  
 Estos valores se usan para buscar el primer contexto de memoria en una lista que satisface los criterios de comparación especificadas. Un contexto de la memoria se proporciona una lista de contextos de memoria compararse a sí mismo con respecto a través de la `IDebugMemoryContext2::Compare` método. El primer contexto de memoria en la lista para que el operador de comparación es `true` , a continuación, se devuelve.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)