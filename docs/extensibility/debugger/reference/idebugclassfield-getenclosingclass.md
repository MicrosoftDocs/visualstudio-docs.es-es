---
title: 'IDebugClassField:: GetEnclosingClass | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 91a4e04e26a57247a541c565ea4f0f392a413d39
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925047"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
Obtiene la clase que incluye esta clase.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetEnclosingClass(
    IDebugClassField** ppClassField
);
```

```csharp
int GetEnclosingClass(
    out IDebugClassField ppClassField
);
```

## <a name="parameters"></a>Parámetros
`ppClassField`\
enuncia Devuelve un objeto [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) que representa la clase envolvente. Devuelve un valor NULL si no hay ninguna clase envolvente.

## <a name="return-value"></a>Valor devuelto
Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
Si la clase representada por este objeto [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) es una clase anidada, el `ppClassField` parámetro devuelve un `IDebugClassField` objeto que representa la clase envolvente. Por ejemplo, dada esta definición de clase:

```
class RootClass {
    class NestedClass { }
};
```

Al llamar al `GetEnclosingClass` método en el `IDebugClassField` objeto que representa la clase, se `NestedClass` devuelve un `IDebugClassField` objeto que representa la clase `RootClass` .

## <a name="see-also"></a>Vea también
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
