---
description: Esta interfaz extiende IDebugStackFrame2 para controlar las excepciones interceptadas.
title: IDebugStackFrame3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d70095db80b8bbd349509de2858b641c520b0623
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159775"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
Esta interfaz extiende [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) para controlar las excepciones interceptadas.

## <a name="syntax"></a>Syntax

```
IDebugStackFrame3 : IDebugStackFrame2
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor DE depuración (DE) implementa esta interfaz en el mismo objeto que implementa la interfaz [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) para admitir excepciones interceptadas.

## <a name="notes-for-callers"></a>Notas para llamadores
 Llame a [QueryInterface](/cpp/atl/queryinterface) en una `IDebugStackFrame2` interfaz para obtener esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 Además de los métodos heredados de [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md), `IDebugStackFrame3` expone los métodos siguientes.

|Método|Descripción|
|------------|-----------------|
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Controla una excepción para el marco de pila actual antes de cualquier control de excepciones regular.|
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Devuelve un contexto de código si se produjera un desenredado de la pila.|

## <a name="remarks"></a>Observaciones
 Una excepción interceptada significa que un depurador puede procesar una excepción antes de que el tiempo de ejecución llame a las rutinas de control de excepciones normales. La interceptación de una excepción esencialmente significa que el tiempo de ejecución Imagine que hay un controlador de excepciones presente incluso cuando no existe.

- Se llama a [interceptcurrentexception (](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) durante todos los eventos de devolución de llamada de excepción normales (la única excepción es si está depurando código de modo mixto (código administrado y no administrado), en cuyo caso no se puede interceptar la excepción durante la devolución de llamada de última oportunidad). Si el DE no implementa `IDebugStackFrame3` o el de devuelve un error de IDebugStackFrame3:: `InterceptCurrentException` (como `E_NOTIMPL` ), el depurador controlará la excepción con normalidad.

 Al interceptar una excepción, el depurador puede permitir al usuario realizar cambios en el estado del programa que se está depurando y, a continuación, reanudar la ejecución en el punto en el que se produjo la excepción.

> [!NOTE]
> Las excepciones interceptadas solo se permiten en código administrado, es decir, en un programa que se ejecuta en Common Language Runtime (CLR).

 Un motor de depuración indica que admite la interceptación de excepciones estableciendo "metricExceptions" en un valor de 1 en tiempo de ejecución mediante la `SetMetric` función. Para obtener más información, vea [aplicaciones auxiliares de SDK para la depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [Asistentes de SDK para la depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
