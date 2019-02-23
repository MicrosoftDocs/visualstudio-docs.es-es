---
title: IDebugObject::SetReferenceValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5cf00fc85a2b3f3dc09704227f84fa5b2e90ee6f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56704506"
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

#### <a name="parameters"></a>Parámetros
 `pObject`

 [in] Un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto que representa el nuevo valor de referencia.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Este método realiza esto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto una referencia al valor del objeto dado en el `pObject` parámetro, eliminando cualquier referencia anterior. Tenga en cuenta que este `IDebugObject` objeto ya debe ser un tipo de referencia.

## <a name="see-also"></a>Vea también
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)