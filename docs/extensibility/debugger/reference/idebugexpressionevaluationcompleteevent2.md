---
description: El motor DE depuración (DE) envía esta interfaz al administrador de depuración de la sesión (SDM) cuando se completa la evaluación de la expresión asincrónica.
title: IDebugExpressionEvaluationCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2
ms.assetid: d538fc19-55bf-4231-9595-eb01e84fd1d8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b30b61c0b7a9a9f3e06465a6b194c882213afb34
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092207"
---
# <a name="idebugexpressionevaluationcompleteevent2"></a>IDebugExpressionEvaluationCompleteEvent2
El motor DE depuración (DE) envía esta interfaz al administrador de depuración de la sesión (SDM) cuando se completa la evaluación de la expresión asincrónica.

## <a name="syntax"></a>Sintaxis

```
IDebugExpressionEvaluationCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El DE implementa esta interfaz para notificar la finalización de una evaluación de expresión iniciada por una llamada a [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). La interfaz [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) debe implementarse en el mismo objeto que esta interfaz. El SDM usa [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la `IDebugEvent2` interfaz.

## <a name="notes-for-callers"></a>Notas para llamadores
 Crea y envía este objeto de evento para notificar la finalización de una evaluación de expresión. El evento se envía mediante la función de devolución de llamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) proporcionada por el SDM cuando se adjunta al programa que se está depurando.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugExpressionEvaluationCompleteEvent2` .

|Método|Descripción|
|------------|-----------------|
|[GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)|Obtiene la expresión original.|
|[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)|Obtiene el resultado de la evaluación de la expresión.|

## <a name="remarks"></a>Observaciones
 El DE debe enviar este evento, independientemente de si la evaluación se realizó correctamente o no.

 Si la evaluación no se realizó correctamente, `DEBUG_PROPINFO_VALUE` las `DEBUG_PROPINFO_ATTRIB` marcas y no se establecerán en la estructura [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) devuelta por [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) (el objeto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) crea el objeto y se devuelve en el `IDebugExpressionEvaluationCompleteEvent2` evento si se produjo un error en la evaluación).

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
