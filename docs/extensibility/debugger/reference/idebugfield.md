---
description: Esta interfaz representa un campo, es decir, una descripción de un símbolo o un tipo.
title: IDebugField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 175f9a329a93587873db7c76b53757ba715ace67
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151849"
---
# <a name="idebugfield"></a>IDebugField
Esta interfaz representa un campo, es decir, una descripción de un símbolo o un tipo.

## <a name="syntax"></a>Syntax

```
IDebugField : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un proveedor de símbolos implementa esta interfaz como la clase base para todos los campos.

## <a name="notes-for-callers"></a>Notas para llamadores
 Esta interfaz es la clase base para todos los campos. Según el valor devuelto de [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md), esta interfaz puede devolver interfaces más especializadas mediante [QueryInterface](/cpp/atl/queryinterface). Además, muchas interfaces devuelven `IDebugField` objetos de diversos métodos.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugField` .

|Método|Descripción|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Obtiene información que se pueda mostrar sobre el símbolo o tipo.|
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Obtiene el tipo de campo.|
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Obtiene el tipo de campo.|
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Obtiene el contenedor del campo.|
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Obtiene la dirección del campo.|
|[GetSize (](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Obtiene el tamaño de un campo, en bytes.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Obtiene información extendida sobre un campo.|
|[Igual](../../../extensibility/debugger/reference/idebugfield-equal.md)|Compara dos campos.|
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Obtiene información independiente del tipo sobre el símbolo o tipo.|

## <a name="remarks"></a>Observaciones
 Un tipo es equivalente a un lenguaje C `typedef` .

 En el siguiente ejemplo del lenguaje C++, `weather` es un tipo de clase, y `sunny` y `stormy` son símbolos:

```cpp
class weather;
weather sunny;
weather stormy;
```

 Si un campo representa un símbolo o un tipo se puede determinar llamando a [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) y examinando el resultado de la [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) . Si `FIELD_KIND_TYPE` se establece el bit, el campo es un tipo y, si `FIELD_KIND_SYMBOL` se establece el bit, es un símbolo.

## <a name="requirements"></a>Requisitos
 Encabezado: SH. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
