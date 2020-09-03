---
title: 'IDebugObject2:: GetBackingFieldForProperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b5b9fed9b071f34c119c8e4a5af12c1df7990f4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726246"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
Obtiene el campo o la variable (si existe) que puede estar respaldando la propiedad representada por este objeto.

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

## <a name="parameters"></a>Parámetros
`ppObject`\
enuncia Un objeto [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) que describe el campo de respaldo.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 El objeto [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) representa una propiedad de clase de código administrado, es decir, un método con un descriptor de acceso get o set. Por lo general, estas propiedades requieren una variable que contenga el valor manipulado por la propiedad. Esta variable se conoce como el campo de respaldo. Si no hay ningún campo de respaldo para el objeto, asegúrese de devolver un valor nulo: es posible que algunos autores de llamadas no presten atención al valor devuelto, pero en su lugar verán si se devolvió un valor null en `ppObject` .

## <a name="see-also"></a>Vea también
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
