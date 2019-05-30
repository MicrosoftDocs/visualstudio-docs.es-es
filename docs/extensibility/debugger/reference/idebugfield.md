---
title: IDebugField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 80def3f9c3d270ebd6f2217f6ce39f07ef27b119
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337519"
---
# <a name="idebugfield"></a>IDebugField
Esta interfaz representa un campo, es decir, una descripción de un símbolo o el tipo.

## <a name="syntax"></a>Sintaxis

```
IDebugField : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un proveedor de símbolos implementa esta interfaz como clase base para todos los campos.

## <a name="notes-for-callers"></a>Notas para los llamadores
 Esta interfaz es la clase base para todos los campos. Según el valor devuelto de [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md), esta interfaz puede devolver interfaces más especializadas mediante [QueryInterface](/cpp/atl/queryinterface). Además, muchas interfaces devuelven `IDebugField` objetos desde varios métodos.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 La tabla siguiente muestran los métodos de `IDebugField`.

|Método|Descripción|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Obtiene el que se puede mostrar información sobre el tipo o el símbolo.|
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Obtiene el tipo de campo.|
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Obtiene el tipo de campo.|
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Obtiene el contenedor del campo.|
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Obtiene la dirección del campo.|
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Obtiene el tamaño de un campo, en bytes.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Obtiene información adicional sobre un campo.|
|[Equal](../../../extensibility/debugger/reference/idebugfield-equal.md)|Compara dos campos.|
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Obtiene información independiente del tipo sobre el tipo o el símbolo.|

## <a name="remarks"></a>Comentarios
 Un tipo es equivalente a un lenguaje de C `typedef`.

 En el siguiente ejemplo de lenguaje C++, `weather` es un tipo de clase, y `sunny` y `stormy` son símbolos:

```cpp
class weather;
weather sunny;
weather stormy;
```

 Si un campo representa un símbolo o el tipo se puede determinar mediante una llamada a [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) y examinando el [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) resultado. Si el `FIELD_KIND_TYPE` bit se establece, el campo es un tipo y si el `FIELD_KIND_SYMBOL` bit está establecido, es un símbolo.

## <a name="requirements"></a>Requisitos
 Encabezado: sh.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)