---
description: Determina si el objeto es un proxy transparente.
title: 'IDebugObject:: IsProxy | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugObject::IsProxy
- IsProxy
ms.assetid: 06c66b87-db95-4400-ab26-5d33e743a439
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f66c8f460e284776f15e393a4adbc8bfd0ea9076
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054145"
---
# <a name="idebugobjectisproxy"></a>IDebugObject::IsProxy
Determina si el objeto es un proxy transparente.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT IsProxy (
   BOOL* pfIsProxy
);
```

```csharp
int IsProxy (
   out bool pfIsProxy
);
```

## <a name="parameters"></a>Parámetros
`pfIsProxy`\
[out] `TRUE` Si el objeto es un proxy transparente; en caso contrario, `FALSE` .

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Este método lo implementa el motor de depuración de C++ predeterminado.

## <a name="see-also"></a>Consulte también
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
