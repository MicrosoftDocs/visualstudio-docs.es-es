---
title: 'IDebugObject:: SetReferenceValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cc0db8ee7f0581a4c336111d3876c24f0e5c12d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726377"
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

## <a name="see-also"></a>Vea también
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
