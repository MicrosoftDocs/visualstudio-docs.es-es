---
description: Devuelve el siguiente conjunto de elementos DEBUG_REFERENCE_INFO de la enumeración.
title: 'IEnumDebugReferenceInfo2:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2::Next
helpviewer_keywords:
- IEnumDebugReferenceInfo2::Next
ms.assetid: 70b31a57-1701-4757-9e7e-63ec60a71b3c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 42f407054728d2ac4a3ba5b9c04bd48080442f94
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079909"
---
# <a name="ienumdebugreferenceinfo2next"></a>IEnumDebugReferenceInfo2::Next
Devuelve el conjunto de elementos siguiente de la enumeración.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Next(
   ULONG                   celt,
   DEBUG_REFERENCE_INFO ** rgelt,
   ULONG*                  pceltFetched
);
```

```csharp
int Next(
   uint                   celt,
   DEBUG_REFERENCE_INFO[] rgelt,
   ref uint               pceltFetched
);
```

## <a name="parameters"></a>Parámetros
`celt`\
[in] Número de elementos que se van a recuperar. También especifica el tamaño máximo de la `rgelt` matriz.

`rgelt`\
[in, out] Matriz de elementos de [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) que se van a rellenar.

`pceltFetched`\
enuncia Devuelve el número de elementos realmente devueltos en `rgelt` .

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si se puede devolver menos que el número solicitado de elementos; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Consulte también
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
