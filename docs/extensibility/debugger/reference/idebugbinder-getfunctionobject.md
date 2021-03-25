---
description: Este método obtiene un objeto IDebugFunctionObject que se usa para crear parámetros de función.
title: 'IDebugBinder:: GetFunctionObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::GetFunctionObject
helpviewer_keywords:
- IDebugBinder::GetFunctionObject method
ms.assetid: 8fb789df-8f30-420d-8ca5-bb496a6738f1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7bbcb8dba1593de824a5a0bb2d4d31f7602eb879
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067470"
---
# <a name="idebugbindergetfunctionobject"></a>IDebugBinder::GetFunctionObject
Este método obtiene un objeto [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) que se usa para crear parámetros de función.

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
enuncia Devuelve la interfaz [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) que se usa para crear parámetros de función.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Consulte también
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
