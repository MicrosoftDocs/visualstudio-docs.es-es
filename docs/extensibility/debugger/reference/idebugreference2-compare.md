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
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: df878cc59a47a8d3cc7079f8b919f87d9bb60f43
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457484"
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

## <a name="parameters"></a>Parámetros
 `dwCompare`\

 [in] Un valor de la [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md) enumeración que especifica la operación de comparación, por ejemplo, igual a, menor que o mayor que.

 `pReference`\

 [in] Un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objeto que representa la referencia que se comparará.

## <a name="return-value"></a>Valor devuelto
 Siempre devuelve `E_NOTIMPL`.

## <a name="see-also"></a>Vea también
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)