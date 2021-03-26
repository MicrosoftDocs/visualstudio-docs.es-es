---
description: Crea un enumerador para los enumeradores anidados de esta clase.
title: 'IDebugClassField:: EnumNestedEnums | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b2e0d908c88b82e9ed706ab919050e1f4943df0c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088567"
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
Crea un enumerador para los enumeradores anidados de esta clase.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EnumNestedEnums(
    IEnumDebugFields** ppEnum
);
```

```csharp
int EnumNestedEnums(
    out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parámetros
`ppEnum`\
enuncia Devuelve un objeto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que representa la lista de enumeraciones anidadas. Devuelve un valor NULL si no hay enumeraciones anidadas.

## <a name="return-value"></a>Valor devuelto
Si es correcto, Devuelve S_OK o devuelve S_FALSE si no hay enumeradores anidados. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
Cada elemento de la enumeración es un objeto [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) que describe una enumeración anidada.

Una enumeración declarada dentro de una clase se considera una enumeración anidada. Por ejemplo, dado:

```
class RootClass {
    enum NestedEnum { EnumValue = 0 }
};
```

El `EnumNestedEnums` método devuelve un objeto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que contiene un objeto [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) que representa la `NestedEnum` enumeración.

## <a name="see-also"></a>Consulte también
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
