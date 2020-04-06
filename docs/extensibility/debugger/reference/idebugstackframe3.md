---
title: IDebugStackFrame3 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d86997d11e124fd5a47981314cf383f5cd8aff7d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719474"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
Esta interfaz extiende [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) para controlar las excepciones interceptadas.

## <a name="syntax"></a>Sintaxis

```
IDebugStackFrame3 : IDebugStackFrame2
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración (DE) implementa esta interfaz en el mismo objeto que implementa la interfaz [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) para admitir excepciones interceptadas.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Llame a [QueryInterface](/cpp/atl/queryinterface) en una `IDebugStackFrame2` interfaz para obtener esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 Además de los métodos heredados `IDebugStackFrame3` de [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md), expone los métodos siguientes.

|Método|Descripción|
|------------|-----------------|
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Controla una excepción para el marco de pila actual antes de cualquier control de excepciones normal.|
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Devuelve un contexto de código si se produce un desenredado de pila.|

## <a name="remarks"></a>Observaciones
 Una excepción interceptada significa que un depurador puede procesar una excepción antes de que el tiempo de ejecución llame a las rutinas normales de control de excepciones. Interceptar una excepción significa esencialmente hacer que el tiempo de ejecución pretenda que hay un controlador de excepciones presente incluso cuando no lo hay.

- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) se llama durante todos los eventos de devolución de llamada de excepción normales (la única excepción a esto es si está depurando código de modo mixto (código administrado y no administrado), en cuyo caso la excepción no se puede interceptar durante la devolución de llamada de última oportunidad). Si la DE no `IDebugStackFrame3`implementa , o la DE devuelve un`InterceptCurrentException` error de `E_NOTIMPL`IDebugStackFrame3:: (como ), el depurador controlará la excepción normalmente.

 Al interceptar una excepción, el depurador puede permitir al usuario realizar cambios en el estado del programa que se está depurando y, a continuación, reanudar la ejecución en el punto donde se inició la excepción.

> [!NOTE]
> Las excepciones interceptadas solo se permiten en código administrado, es decir, en un programa que se ejecuta en Common Language Runtime (CLR).

 Un motor de depuración indica que admite la interceptación de excepciones estableciendo "metricExceptions" en un valor de 1 en tiempo de ejecución mediante la `SetMetric` función. Para obtener más información, consulte Aplicaciones auxiliares del [SDK para la depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [Asistentes de SDK para la depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
