---
title: 'IDebugMethodField:: EnumStaticLocals | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumStaticLocals
helpviewer_keywords:
- IDebugMethodField::EnumStaticLocals method
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3af65c60654fd23f88892522142548bf5db87a70
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929802"
---
# <a name="idebugmethodfieldenumstaticlocals"></a>IDebugMethodField::EnumStaticLocals
Crea un enumerador para las variables locales estáticas del método.

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
enuncia Devuelve un objeto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que representa la lista de variables locales estáticas. Devuelve un valor NULL si no hay variables locales estáticas.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, Devuelve S_OK o devuelve S_FALSE si no hay variables locales estáticas. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
 Cada elemento es un objeto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que representa distintos tipos de variables locales estáticas. Llame al método [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) en cada objeto para determinar exactamente qué tipo de local estático representa el objeto.

## <a name="see-also"></a>Vea también
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
