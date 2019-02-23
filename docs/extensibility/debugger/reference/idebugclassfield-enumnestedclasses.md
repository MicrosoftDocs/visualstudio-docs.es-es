---
title: IDebugClassField::EnumNestedClasses | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedClasses
helpviewer_keywords:
- IDebugClassField::EnumNestedClasses method
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 512329317ce1e9587848edf15c68f57fe112299e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56681926"
---
# <a name="idebugclassfieldenumnestedclasses"></a>IDebugClassField::EnumNestedClasses
Crea un enumerador para las clases anidadas de esta clase.

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

#### <a name="parameters"></a>Parámetros
`ppEnum`

 [out] Devuelve un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa la lista de las clases anidadas. Devuelve un valor null si no hay ninguna clase anidada.

## <a name="return-value"></a>Valor devuelto
Si se realiza correctamente, devuelve S_OK o devuelve S_FALSE si no hay ninguna clase anidada. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
Cada elemento de la enumeración es un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) objeto que describe una clase anidada.

Una clase anidada es una clase definida dentro de otra clase. Por ejemplo:

```
class RootClass {
   class NestedClass { }
};
```

El [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) enumeración contendría un objeto que representa el `NestedClass` clase.

## <a name="see-also"></a>Vea también
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
