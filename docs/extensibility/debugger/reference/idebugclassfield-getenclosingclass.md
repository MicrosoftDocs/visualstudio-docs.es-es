---
title: IDebugClassField::GetEnclosingClass ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e5a68e32da370d6881eb2b74cbca157f7b899329
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734396"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
Obtiene la clase que encierra esta clase.

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
[fuera] Devuelve un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) objeto que representa la clase envolvente. Devuelve un valor null si no hay ninguna clase envolvente.

## <a name="return-value"></a>Valor devuelto
Si se realiza correctamente, devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
Si la clase representada por este [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) objeto `ppClassField` es una `IDebugClassField` clase anidada, a continuación, el parámetro devuelve un objeto que representa la clase envolvente. Por ejemplo, dada esta definición de clase:

```
class RootClass {
    class NestedClass { }
};
```

Al `GetEnclosingClass` llamar al `IDebugClassField` método `NestedClass` en el `IDebugClassField` objeto que `RootClass`representa la clase devuelve un objeto que representa la clase .

## <a name="see-also"></a>Vea también
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
