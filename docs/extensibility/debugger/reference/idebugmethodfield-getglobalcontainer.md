---
title: IDebugMethodField::GetGlobalContainer | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetGlobalContainer
helpviewer_keywords:
- IDebugMethodField::GetGlobalContainer method
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 77f3d82beab43b227dd3beb772dd41353d89b6fe
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324187"
---
# <a name="idebugmethodfieldgetglobalcontainer"></a>IDebugMethodField::GetGlobalContainer
Obtiene el contenedor del método global.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetGlobalContainer(
   IDebugClassField** ppClass
);
```

```csharp
int GetGlobalContainer(
   out IDebugClassField ppClass
);
```

## <a name="parameters"></a>Parámetros
`ppClass`\
[out] Devuelve un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) que representa el módulo en el que se define este método.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 El valor devuelto [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) representa todo el módulo de objeto y es un objeto artificial, es decir, el propio módulo no tiene una clase real pero se puede representar mediante un `IDebugClassField` objeto, lo que permite a los distintos elementos del módulo que se enumeran y se detectan.

## <a name="see-also"></a>Vea también
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)