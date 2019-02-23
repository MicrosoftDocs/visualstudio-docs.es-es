---
title: IDebugObject2::GetBackingFieldForProperty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 080af74ee83c5a2816cc5e7a89f29c59d2b75c7c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56696134"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
Obtiene el campo o variable (si existe) que puede realizar copias de la propiedad representada por este objeto.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetBackingFieldForProperty(
   IDebugObject2** ppObject
);
```

```csharp
int GetBackingFieldForProperty(
   out IDebugObject2 ppObject
);
```

#### <a name="parameters"></a>Parámetros
 `ppObject`

 [out] Un [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) objeto que describe el campo de respaldo.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 El [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) objeto representa una propiedad de clase de código administrado, es decir, un método con un método get o establecer el descriptor de acceso. Estas propiedades normalmente necesitan una variable que contiene el valor que se manipula mediante la propiedad. Esta variable se conoce como el campo de respaldo. Si no hay ningún campo de respaldo para el objeto, asegúrese de que se devuelve un valor null: algunos autores de llamadas no se puede prestar atención al valor devuelto, pero tendrá un aspecto en su lugar para ver si se devolvió un valor null en `ppObject`.

## <a name="see-also"></a>Vea también
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)