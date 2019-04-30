---
title: IDebugReference2::Compare | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::Compare
helpviewer_keywords:
- IDebugReference2::Compare
ms.assetid: 3361c495-2673-4b7c-82e3-dee74e1fa58d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d3ca4e944125f6673ca66accdb78742f693def77
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62869131"
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
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)