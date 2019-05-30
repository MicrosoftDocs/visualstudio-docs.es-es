---
title: IDebugBinder::GetFunctionObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::GetFunctionObject
helpviewer_keywords:
- IDebugBinder::GetFunctionObject method
ms.assetid: 8fb789df-8f30-420d-8ca5-bb496a6738f1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 03078a09de94b886a659059192a5b67430cb5137
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337662"
---
# <a name="idebugbindergetfunctionobject"></a>IDebugBinder::GetFunctionObject
Este método obtiene una [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) objeto utilizado para crear parámetros de función.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetFunctionObject( 
   IDebugFunctionObject **ppFunction
);
```

```csharp
int GetFunctionObject(
   out IDebugFunctionObject ppFunction
);
```

## <a name="parameters"></a>Parámetros
`ppFunction`\
[out] Devuelve el [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfaz que se usa para crear parámetros de función.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)