---
title: IDebugField ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c7a25246f42d288020481330fe60e312849862d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728755"
---
# <a name="idebugfield"></a>IDebugField
Esta interfaz representa un campo, es decir, una descripción de un símbolo o tipo.

## <a name="syntax"></a>Sintaxis

```
IDebugField : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un proveedor de símbolos implementa esta interfaz como la clase base para todos los campos.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Esta interfaz es la clase base para todos los campos. En función del valor devuelto de [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md), esta interfaz puede devolver interfaces más especializadas mediante [QueryInterface](/cpp/atl/queryinterface). Además, muchas `IDebugField` interfaces devuelven objetos de varios métodos.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IDebugField`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Obtiene información que se puede mostrar sobre el símbolo o el tipo.|
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Obtiene el tipo de campo.|
|[Gettype](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Obtiene el tipo de campo.|
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Obtiene el contenedor del campo.|
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Obtiene la dirección del campo.|
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Obtiene el tamaño de un campo, en bytes.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Obtiene información ampliada sobre un campo.|
|[Igual](../../../extensibility/debugger/reference/idebugfield-equal.md)|Compara dos campos.|
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Obtiene información independiente del tipo sobre el símbolo o el tipo.|

## <a name="remarks"></a>Observaciones
 Un tipo es equivalente `typedef`a un lenguaje C .

 En el siguiente ejemplo de `weather` lenguaje C++, es un tipo de clase y `sunny` `stormy` son símbolos:

```cpp
class weather;
weather sunny;
weather stormy;
```

 Si un campo representa un símbolo o tipo se puede determinar llamando a [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) y examinando el [resultado FIELD_KIND.](../../../extensibility/debugger/reference/field-kind.md) Si `FIELD_KIND_TYPE` se establece el bit, el campo `FIELD_KIND_SYMBOL` es un tipo, y si el bit está establecido, es un símbolo.

## <a name="requirements"></a>Requisitos
 Encabezado: sh.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
