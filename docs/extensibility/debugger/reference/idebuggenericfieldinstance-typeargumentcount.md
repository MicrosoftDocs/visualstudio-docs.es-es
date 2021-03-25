---
description: Devuelve el número de argumentos de parámetro de tipo para esta instancia.
title: 'IDebugGenericFieldInstance:: TypeArgumentCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TypeArgumentCount
- IDebugGenericFieldInstance::TypeArgumentCount
ms.assetid: e662c5ea-a5c1-478e-a268-5980dadffcd1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c7afd914b3880ca1004a319a66b3f4176e15789e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072876"
---
# <a name="idebuggenericfieldinstancetypeargumentcount"></a>IDebugGenericFieldInstance::TypeArgumentCount
Devuelve el número de argumentos de parámetro de tipo para esta instancia.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT TypeArgumentCount(
   ULONG32* pcArgs
);
```

```csharp
int TypeArgumentCount(
   ref uint pcArgs
);
```

## <a name="parameters"></a>Parámetros
`pcArgs`\
[in, out] Número de argumentos de parámetro de tipo para esta instancia.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Por ejemplo, si List \<int> , este método devuelve 1 y, si List, \<int,float2> este método devuelve 2. Este método devuelve 0 si no hay ningún argumento de tipo.

## <a name="see-also"></a>Consulte también
- [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)
