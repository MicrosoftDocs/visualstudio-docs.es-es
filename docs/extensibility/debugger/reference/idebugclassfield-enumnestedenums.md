---
title: IDebugClassField::EnumNestedEnums | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ec2bd27ffdecb41aa60b38dd7b8202c7c6449637
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "56412869"
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

#### <a name="parameters"></a>Parámetros
`ppEnum`  
[out] Devuelve un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa la lista de enumeraciones anidadas. Devuelve un valor null si no hay ningún enumeraciones anidadas.

## <a name="return-value"></a>Valor devuelto
Si se realiza correctamente, devuelve S_OK o devuelve S_FALSE si no hay ningún enumeradores anidados. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
Cada elemento de la enumeración es un [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) objeto que describe una enumeración anidada.

Una enumeración declarada dentro de una clase se considera una enumeración anidada. Por ejemplo, dado:

```
class RootClass {
    enum NestedEnum { EnumValue = 0 }
};
```

El `EnumNestedEnums` método devolvería un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que contiene un [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) objeto que representa el `NestedEnum` enumeración.

## <a name="see-also"></a>Vea también
[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)  
[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)  
[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
