---
title: IDebugMethodField::EnumAllLocals ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumAllLocals
helpviewer_keywords:
- IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50da5af616c56276a0299a0d08e6eeb0b88181cc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727333"
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
Crea un enumerador para todas las variables locales del método, incluidas las generadas internamente por un compilador.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EnumAllLocals( 
   IDebugAddress*     pAddress,
   IEnumDebugFields** ppLocals
);
```

```csharp
int EnumAllLocals(
   IDebugAddress        pAddress,
   out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>Parámetros
`pAddress`\
[en] Un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objeto que representa una dirección de depuración dentro del método, que apunta a un ámbito o contexto determinado.

`ppLocals`\
[fuera] Devuelve un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa la lista de todos los valores locales en el ámbito especificado; de lo contrario, devuelve un valor nulo que indica que no hay locales.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, S_OK o devuelve S_FALSE si no hay locales. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Solo se enumeran las variables definidas dentro del bloque que contiene la dirección de depuración dada. Este método incluye cualquier local generado por el compilador. Si todo lo que se necesita son los valores locales definidos explícitamente en el origen, llame a la [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) método.

 Un método puede contener varios contextos o bloques de ámbito.

## <a name="see-also"></a>Vea también
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)
