---
title: IDebugManagedObject::SetFromManagedObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::SetFromManagedObject
helpviewer_keywords:
- IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c56ccea9847cc23e45f9877f3d331be723293ee7
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56712195"
---
# <a name="idebugmanagedobjectsetfrommanagedobject"></a>IDebugManagedObject::SetFromManagedObject
Establece el valor de la instancia del objeto de clase de valor de la instancia de la clase de valor que se proporciona como un parámetro.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT SetFromManagedObject( 
   IUnknown* pManagedObject
);
```

```csharp
int SetFromManagedObject(
   object pManagedObject
);
```

#### <a name="parameters"></a>Parámetros
 `pManagedObject`

 [in] Una interfaz que representa el objeto administrado que contiene el nuevo valor.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Este método se utiliza para cambiar el objeto administrado, tal como está representada por la [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) objeto.

## <a name="see-also"></a>Vea también
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)