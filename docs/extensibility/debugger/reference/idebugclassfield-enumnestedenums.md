---
title: IDebugClassField::EnumNestedEnums ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 38ee3ccd1ffd3130bc918da18c631cf08683f064
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734408"
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
[fuera] Devuelve un [objeto IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que representa la lista de enumeraciones anidadas. Devuelve un valor nulo si no hay enumeraciones anidadas.

## <a name="return-value"></a>Valor devuelto
Si se realiza correctamente, devuelve S_OK o devuelve S_FALSE si no hay enumeradores anidados. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
Cada elemento de la enumeración es un [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) objeto que describe una enumeración anidada.

Una enumeración declarada dentro de una clase se considera una enumeración anidada. Por ejemplo, en estas circunstancias:

```
class RootClass {
    enum NestedEnum { EnumValue = 0 }
};
```

El `EnumNestedEnums` método devolvería un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que contiene un [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) objeto que representa la `NestedEnum` enumeración.

## <a name="see-also"></a>Vea también
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
