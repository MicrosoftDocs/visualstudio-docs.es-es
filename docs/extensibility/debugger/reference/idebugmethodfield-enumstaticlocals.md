---
title: IDebugMethodField::EnumStaticLocals ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumStaticLocals
helpviewer_keywords:
- IDebugMethodField::EnumStaticLocals method
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e0a89b4c1ac4318b6dd070dc086b86b45ad24fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727156"
---
# <a name="idebugmethodfieldenumstaticlocals"></a>IDebugMethodField::EnumStaticLocals
Crea un enumerador para variables locales estáticas del método.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EnumStaticLocals( 
   IEnumDebugFields** ppLocals
);
```

```csharp
int EnumStaticLocals(
   out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>Parámetros
`ppLocals`\
[fuera] Devuelve un [objeto IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que representa la lista de valores locales estáticos. Devuelve un valor nulo si no hay locales estáticos.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, S_OK o devuelve S_FALSE si no hay locales estáticos. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Cada elemento es un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto que representa diferentes tipos de configuraciones regionales estáticas. Llame a la [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) método en cada objeto para determinar exactamente qué tipo de local estático representa el objeto.

## <a name="see-also"></a>Vea también
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
