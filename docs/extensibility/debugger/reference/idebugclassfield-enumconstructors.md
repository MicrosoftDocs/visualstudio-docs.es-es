---
title: 'IDebugClassField:: EnumConstructors | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumConstructors
helpviewer_keywords:
- IDebugClassField::EnumConstructors method
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 05226572d7f1b708745887338c654674e71d0f5d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947087"
---
# <a name="idebugclassfieldenumconstructors"></a>IDebugClassField::EnumConstructors
Crea un enumerador para los constructores de esta clase.

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
de Un valor de la enumeración [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) que especifica el tipo de constructores que se va a enumerar.

`ppEnum`\
enuncia Devuelve un objeto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que representa la lista de constructores. Devuelve un valor NULL si no hay ningún constructor.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, Devuelve S_OK o devuelve S_FALSE si no hay ningún constructor. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
 Cada elemento de la enumeración es un objeto [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) que describe un método de constructor.

 La lista de constructores normalmente no incluye los constructores predeterminados proporcionados por un compilador.

## <a name="see-also"></a>Vea también
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)
