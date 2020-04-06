---
title: IDebugProperty2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2
helpviewer_keywords:
- IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4b04abdac135143ccbbd1b8e5632bf85c974f29d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721225"
---
# <a name="idebugproperty2"></a>IDebugProperty2
Esta interfaz representa una propiedad de marco de pila, una propiedad de documento de programa o alguna otra propiedad. La propiedad suele ser el resultado de una evaluación de expresiones.

> [!NOTE]
> Este uso de "propiedad" no debe confundirse con ese significado `IDebugProperty2` una variable miembro de una clase, aunque un puede representar tal entidad.

## <a name="syntax"></a>Sintaxis

```
IDebugProperty2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 La DE implementa esta interfaz para representar un tipo particular de valor. Por ejemplo, el valor podría ser un valor numérico como resultado de una evaluación de expresión, un contexto de memoria utilizado para mostrar memoria o una lista de registros y sus valores.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Llame a [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) para obtener esta interfaz, que representa el resultado de una evaluación. `IDebugExpression2::EvaluateAsync`devuelve esta interfaz mediante el envío de un [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) interfaz al SDM, que a su vez llama a [GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) para recuperar la propiedad.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) devuelve esta interfaz para proporcionar el documento de script asociado.

- [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) devuelve esta interfaz para representar el valor devuelto de una función.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) devuelve esta interfaz para representar varias propiedades del programa, como un nombre o un contexto de memoria.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) devuelve esta interfaz para representar varias propiedades del marco de pila, como variables locales.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IDebugProperty2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|Rellena una [estructura DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) que describe una propiedad.|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|Establece el valor de una propiedad de una cadena.|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|Establece el valor de la propiedad a partir del valor de una referencia determinada.|
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|Enumera los elementos secundarios de una propiedad.|
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|Devuelve el elemento primario de una propiedad.|
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|Devuelve la propiedad que describe la propiedad más derivada de una propiedad.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|Devuelve los bytes de memoria que componen el valor de una propiedad.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|Devuelve el contexto de memoria para un valor de propiedad.|
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|Devuelve el tamaño, en bytes, del valor de propiedad.|
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|Devuelve una referencia al valor de esta propiedad.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|Devuelve la información extendida de una propiedad.|

## <a name="remarks"></a>Observaciones
 Una propiedad, representada por `IDebugProperty2` una interfaz, se puede considerar como un valor con un nombre, un tipo y una dirección. En términos más `IDebugProperty2` generales, un puede representar cualquier cosa que tenga una estructura jerárquica, con los padres y los nodos secundarios.

 Una propiedad suele ser transitoria, que dura solo el tiempo que el marco de pila actual, por ejemplo. Por otro lado, una referencia, representada por un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) interfaz, dura siempre que el valor permanece en la memoria.

 El IDE puede `IDebugProperty2` usar la interfaz para permitir a los usuarios examinar y modificar propiedades en tiempo de ejecución.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
