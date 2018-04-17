---
title: IDebugReference2::Compare | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugReference2::Compare
helpviewer_keywords:
- IDebugReference2::Compare
ms.assetid: 3361c495-2673-4b7c-82e3-dee74e1fa58d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7ede48e5236887e3d8fdb22425d92c8514636f94
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugreference2compare"></a>IDebugReference2::Compare
Compara una referencia a otro. Reservado para un uso futuro.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Compare (   
   REFERENCE_COMPARE dwCompare,  
   IDebugReference2* pReference  
);  
```  
  
```csharp  
int Compare (   
   enum_REFERENCE_COMPARE dwCompare,  
   IDebugReference2       pReference  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwCompare`  
 [in] Un valor de la [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md) enumeración que especifica la operación de comparación, por ejemplo, igual a, menor que o mayor que.  
  
 `pReference`  
 [in] Un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objeto que representa la referencia que se comparará.  
  
## <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `E_NOTIMPL`.  
  
## <a name="see-also"></a>Vea también  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)