---
title: IDebugReference2::Comparar ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::Compare
helpviewer_keywords:
- IDebugReference2::Compare
ms.assetid: 3361c495-2673-4b7c-82e3-dee74e1fa58d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0d293fcb89c92a19acc4f5a3910015914ef4231a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720640"
---
# <a name="idebugreference2compare"></a>IDebugReference2::Compare
Compara una referencia con otra. Reservado para uso futuro.

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

## <a name="parameters"></a>Parámetros
`dwCompare`\
[en] Valor de la [enumeración REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md) que especifica la operación de comparación, por ejemplo, igual a, menor o mayor que.

`pReference`\
[en] Un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objeto que representa la referencia que se va a comparar con.

## <a name="return-value"></a>Valor devuelto
 Siempre devuelve `E_NOTIMPL`.

## <a name="see-also"></a>Vea también
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)
