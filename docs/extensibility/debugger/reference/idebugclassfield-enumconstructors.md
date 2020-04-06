---
title: IDebugClassField::EnumConstructors ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumConstructors
helpviewer_keywords:
- IDebugClassField::EnumConstructors method
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 607f4f4af3021389628fcc1be446ebbe95628b7c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734457"
---
# <a name="idebugclassfieldenumconstructors"></a>IDebugClassField::EnumConstructors
Crea un enumerador para los constructores para esta clase.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EnumConstructors( 
   CONSTRUCTOR_ENUM   cMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumConstructors(
   CONSTRUCTOR_ENUM     cMatch,
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parámetros
`cMatch`\
[en] Valor de la [enumeración CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) que especifica el tipo de constructores que se va a enumeración.

`ppEnum`\
[fuera] Devuelve un [objeto IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que representa la lista de constructores. Devuelve un valor nulo si no hay constructores.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, S_OK o devuelve S_FALSE si no hay constructores. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Cada elemento de la enumeración es un [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) objeto que describe un constructor método.

 La lista de constructores normalmente no incluye los constructores predeterminados proporcionados por un compilador.

## <a name="see-also"></a>Vea también
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)
