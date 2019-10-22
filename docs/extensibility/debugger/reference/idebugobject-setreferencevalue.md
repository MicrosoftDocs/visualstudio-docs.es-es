---
title: IDebugObject::SetReferenceValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aaef4eb96942789bd3f574e6eeddcd3500ae6ee9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349953"
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
[in] Un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto que representa el nuevo valor de referencia.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Este método realiza esto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto una referencia al valor del objeto dado en el `pObject` parámetro, eliminando cualquier referencia anterior. Tenga en cuenta que este `IDebugObject` objeto ya debe ser un tipo de referencia.

## <a name="see-also"></a>Vea también
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)