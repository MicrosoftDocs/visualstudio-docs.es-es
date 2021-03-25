---
description: Crea un objeto de datos primitivo, como un entero simple.
title: 'IDebugFunctionObject:: CreatePrimitiveObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreatePrimitiveObject
helpviewer_keywords:
- IDebugFunctionObject::CreatePrimitiveObject method
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c706d8908f1fa8776d1d7304772a0c5eec03bd2d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073500"
---
# <a name="idebugfunctionobjectcreateprimitiveobject"></a>IDebugFunctionObject::CreatePrimitiveObject
Crea un objeto de datos primitivo, como un entero simple.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT CreatePrimitiveObject( 
   OBJECT_TYPE    ot,
   IDebugObject** ppObject
);
```

```csharp
int CreatePrimitiveObject(
   enum_OBJECT_TYPE ot,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parámetros
`ot`\
de Un valor de la enumeración [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) que representa el tipo de primitivo que se va a crear.

`ppObject`\
enuncia Devuelve un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa el objeto recién creado.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Llame a este método para crear un objeto que represente un objeto primitivo que sea un parámetro de la función representada por la interfaz [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) . Por ejemplo, si la cadena de expresión es "String (5)", este método se utilizaría para crear un objeto que represente el entero 5.

## <a name="see-also"></a>Consulte también
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
