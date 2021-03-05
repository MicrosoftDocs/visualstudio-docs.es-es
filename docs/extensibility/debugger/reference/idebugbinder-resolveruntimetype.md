---
description: Este método determina el tipo en tiempo de ejecución de un objeto.
title: 'IDebugBinder:: ResolveRuntimeType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::ResolveRuntimeType
helpviewer_keywords:
- IDebugBinder::ResolveRuntimeType method
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 19e7285dd25009e7fe4aeb92974c70ce4109502c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143641"
---
# <a name="idebugbinderresolveruntimetype"></a>IDebugBinder::ResolveRuntimeType
Este método determina el tipo en tiempo de ejecución de un objeto.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT ResolveRuntimeType( 
   IDebugObject* pObject,
   IDebugField** ppResolved
);
```

```csharp
int ResolveRuntimeType(
   IDebugObject     pObject,
   out IDebugField  ppResolved
);
```

## <a name="parameters"></a>Parámetros
`pObject`\
de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que se va a resolver.

`ppResolved`\
enuncia Devuelve el tipo del objeto como [IDebugField](../../../extensibility/debugger/reference/idebugfield.md).

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 No siempre se conoce el tipo en tiempo de ejecución de un objeto en tiempo de compilación. Por ejemplo, con el polimorfismo, un argumento se puede pasar a una función como su clase base, como una clase de botón. El argumento real puede ser una clase derivada, como una clase de botón de radio.

## <a name="see-also"></a>Consulte también
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
