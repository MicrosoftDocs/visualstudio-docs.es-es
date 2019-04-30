---
title: IDebugMethodField::EnumLocals | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6e8c39adaca6c394b631542d57d74ed4818501b4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62872929"
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

#### <a name="parameters"></a>Parámetros
`pAddress`

 [in] Un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objeto que representa la dirección de depuración que selecciona el contexto o ámbito desde el que se va a obtener las variables locales.

`ppLocals`

 [out] Devuelve un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa una lista de las variables locales; de lo contrario, devuelve un valor null si no hay ningún variables locales.

## <a name="return-value"></a>Valor devuelto
Si se realiza correctamente, devuelve S_OK o devuelve S_FALSE si no hay ningún variables locales. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
Se enumeran solo las variables definidas dentro del bloque que contiene la dirección de depuración especificado. Si se necesitan todas las variables locales incluyendo las variables locales generadas por el compilador, llame a la [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) método.

Un método puede contener varios contextos o bloques de ámbito. Por ejemplo, el siguiente método inventado contiene tres ámbitos, los dos bloques internos y el cuerpo del método.

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

El [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) objeto representa el `func` propio método. Una llamada a la `EnumLocals` método con un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) establecido en el `Inner Scope 1` dirección devuelve una enumeración que contiene el `temp1` variable, por ejemplo.

## <a name="see-also"></a>Vea también
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
