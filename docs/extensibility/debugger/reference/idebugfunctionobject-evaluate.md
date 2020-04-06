---
title: IDebugFunctionObject::Evaluate ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::Evaluate
helpviewer_keywords:
- IDebugFunctionObject::Evaluate method
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 529a5f67c808efa258bc0cb9899f546dbb90d431
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728512"
---
# <a name="idebugfunctionobjectevaluate"></a>IDebugFunctionObject::Evaluate
Llama a la función y devuelve el valor resultante como un objeto.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Evaluate( 
   IDebugObject** ppParams,
   DWORD          dwParams,
   DWORD          dwTimeout,
   IDebugObject** ppResult
);
```

```csharp
int Evaluate(
   IDebugObject[]   ppParams,
   IntPtr           dwParams,
   uint             dwTimeout,
   out IDebugObject ppResult
);
```

## <a name="parameters"></a>Parámetros
`ppParams`\
[en] Matriz de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objetos que representan los parámetros de entrada. Cada uno de estos parámetros `Create` se creó con uno de los métodos de la [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfaz.

`dwParams`\
[en] El número de `ppParams` parámetros de la matriz.

`dwTimeout`\
[en] Especifica el tiempo máximo, en milisegundos, que se debe esperar antes de volver de este método. Se `INFINITE` usa para esperar indefinidamente.

`ppResult`\
[fuera] Devuelve un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa el valor de la función como un objeto.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Este método configura y ejecuta una llamada a la función representada por el [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) objeto.

## <a name="see-also"></a>Vea también
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
