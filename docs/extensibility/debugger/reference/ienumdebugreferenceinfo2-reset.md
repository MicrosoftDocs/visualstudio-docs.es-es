---
description: Restablece la enumeración al primer elemento DEBUG_REFERENCE_INFO.
title: 'IEnumDebugReferenceInfo2:: RESET | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2::Reset
helpviewer_keywords:
- IEnumDebugReferenceInfo2::Reset
ms.assetid: cf8ce649-5ce1-44a6-9d5a-89760021bde4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d85883445eb160c02cde03583b10482bcbfa9d4b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079893"
---
# <a name="ienumdebugreferenceinfo2reset"></a>IEnumDebugReferenceInfo2::Reset
Restablece la enumeración al primer elemento.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Reset(
   void
);
```

```csharp
int Reset();
```

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Después de llamar a este método, la siguiente llamada al método [siguiente](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md) devuelve el primer elemento de la enumeración.

## <a name="see-also"></a>Consulte también
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
