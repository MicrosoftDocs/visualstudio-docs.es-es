---
title: IDebugMethodField::EnumLocals ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 08872160860d0d442f9807705dea70190dff9b28
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727206"
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
Crea un enumerador para las variables locales seleccionadas del método.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EnumLocals(
    IDebugAddress*     pAddress,
    IEnumDebugFields** ppLocals
);
```

```csharp
int EnumLocals(
    IDebugAddress        pAddress,
    out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>Parámetros
`pAddress`\
[en] Un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objeto que representa la dirección de depuración que selecciona el contexto o ámbito desde el que se obtienen los locales.

`ppLocals`\
[fuera] Devuelve un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa una lista de los locales; de lo contrario, devuelve un valor nulo si no hay valores locales.

## <a name="return-value"></a>Valor devuelto
Si se realiza correctamente, S_OK o devuelve S_FALSE si no hay locales. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
Solo se enumeran las variables definidas dentro del bloque que contiene la dirección de depuración dada. Si se necesitan todas las configuraciones regionales, incluidas las configuraciones regionales generadas por el compilador, llame al método [EnumAllLocals.](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)

Un método puede contener varios contextos o bloques de ámbito. Por ejemplo, el siguiente método inventado contiene tres ámbitos, los dos bloques internos y el propio cuerpo del método.

```csharp
public void func(int index)
{
    // Method body scope
    int a = 0;
    if (index == 1)
    {
        // Inner scope 1
        int temp1 = a;
    }
    else
    {
        // Inner scope 2
        int temp2 = a;
    }
}
```

El [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) objeto `func` representa el propio método. Llamar `EnumLocals` al método con un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) establecido en la `Inner Scope 1` dirección devuelve una enumeración que contiene la `temp1` variable, por ejemplo.

## <a name="see-also"></a>Vea también
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
