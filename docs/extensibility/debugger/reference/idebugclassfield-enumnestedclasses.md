---
description: Crea un enumerador para las clases anidadas en esta clase.
title: 'IDebugClassField:: EnumNestedClasses | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedClasses
helpviewer_keywords:
- IDebugClassField::EnumNestedClasses method
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 87538db39df590fd3885f545e5442c7dafecb9a1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164271"
---
# <a name="idebugclassfieldenumnestedclasses"></a>IDebugClassField::EnumNestedClasses
Crea un enumerador para las clases anidadas en esta clase.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EnumNestedClasses(
    IEnumDebugFields** ppEnum
);
```

```csharp
int EnumNestedClasses(
    out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parámetros
`ppEnum`\
enuncia Devuelve un objeto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que representa la lista de clases anidadas. Devuelve un valor NULL si no hay ninguna clase anidada.

## <a name="return-value"></a>Valor devuelto
Si es correcto, Devuelve S_OK o devuelve S_FALSE si no hay ninguna clase anidada. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
Cada elemento de la enumeración es un objeto [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) que describe una clase anidada.

Una clase anidada es una clase definida dentro de otra clase. Por ejemplo:

```
class RootClass {
   class NestedClass { }
};
```

La enumeración [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) contiene un objeto que representa la `NestedClass` clase.

## <a name="see-also"></a>Consulte también
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
