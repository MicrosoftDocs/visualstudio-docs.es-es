---
title: IDebugMemoryContext2::Compare | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3eb48c324b5a1a918ab864c5eb4c4ca39eae41ac
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68163431"
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Compara cada contexto en la matriz especificada de la manera indicada por las marcas de comparación, devolviendo un índice del primer contexto que coincida con el contexto de memoria.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Compare(   
   CONTEXT_COMPARE        compare,  
   IDebugMemoryContext2** rgpMemoryContextSet,  
   DWORD                  dwMemoryContextSetLen,  
   DWORD*                 pdwMemoryContext  
);  
```  
  
```csharp  
int Compare(  
   enum_CONTEXT_COMPARE   compare,   
   IDebugMemoryContext2[] rgpMemoryContextSet,   
   uint                   dwMemoryContextSetLen,   
   out uint               pdwMemoryContext  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `compare`  
 [in] Un valor de la [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) enumeración que determina el tipo de comparación.  
  
 `rgpMemoryContextSet`  
 [in] Una matriz de referencias a la [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objetos que se va a comparar.  
  
 `dwMemoryContextSetLen`  
 [in] El número de contextos en los `rgpMemoryContextSet` matriz.  
  
 `pdwMemoryContext`  
 [out] Devuelve el índice del primer contexto de memoria que satisface la comparación.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. Devuelve `E_COMPARE_CANNOT_COMPARE` si no se pueden comparar los dos contextos.  
  
## <a name="remarks"></a>Comentarios  
 Un motor de depuración (DE) no tiene que admitir todos los tipos de comparaciones, pero debe admitir al menos `CONTEXT_EQUAL`, `CONTEXT_LESS_THAN`, `CONTEXT_GREATER_THAN` y `CONTEXT_SAME_SCOPE`.  
  
## <a name="see-also"></a>Vea también  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)
