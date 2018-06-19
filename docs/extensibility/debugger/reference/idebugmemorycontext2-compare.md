---
title: IDebugMemoryContext2::Compare | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b9c72120a4153ed6d0d19a2cf2b7d3a9a9943801
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31112475"
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
Compara el contexto de memoria para cada contexto de la matriz de la manera indicada por marcas de comparación, devolver un índice del primer contexto que coincida con determinada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
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
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error. Devuelve `E_COMPARE_CANNOT_COMPARE` si no se pueden comparar los dos contextos.  
  
## <a name="remarks"></a>Comentarios  
 Un motor de depuración (Alemania) no tiene que admitir todos los tipos de comparaciones, pero debe admitir al menos `CONTEXT_EQUAL`, `CONTEXT_LESS_THAN`, `CONTEXT_GREATER_THAN` y `CONTEXT_SAME_SCOPE`.  
  
## <a name="see-also"></a>Vea también  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)