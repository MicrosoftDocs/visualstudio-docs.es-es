---
description: Establece el valor de referencia de este objeto.
title: 'IDebugObject:: SetReferenceValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a65c14d4122ac6d877573822b4fa8be1cb6cdd1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054119"
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
Establece el valor de referencia de este objeto.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT SetReferenceValue( 
   IDebugObject* pObject
);
```

```csharp
int SetReferenceValue(
   [In] IDebugObject pObject
);
```

## <a name="parameters"></a>Parámetros
`pObject`\
de Un objeto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa el nuevo valor de referencia.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Este método convierte a este objeto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) en una referencia al valor del objeto especificado en el `pObject` parámetro, lo que produce cualquier referencia anterior. Tenga en cuenta que este `IDebugObject` objeto debe ser ya un tipo de referencia.

## <a name="see-also"></a>Consulte también
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
