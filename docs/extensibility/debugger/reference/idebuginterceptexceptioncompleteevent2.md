---
description: El motor de depuración (DE) envía esta interfaz al administrador de depuración de la sesión (SDM) cuando el DE ha completado el control de un evento interceptado.
title: IDebugInterceptExceptionCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugInterceptExceptionCompleteEvent2
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2
ms.assetid: 8ebc256b-5428-4ed6-a505-6aedc8242b8e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6902382a94beaa983ee97ebb63223e5bdfa1645f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091817"
---
# <a name="idebuginterceptexceptioncompleteevent2"></a>IDebugInterceptExceptionCompleteEvent2
El motor de depuración (DE) envía esta interfaz al administrador de depuración de la sesión (SDM) cuando el DE ha completado el control de un evento interceptado.

## <a name="syntax"></a>Sintaxis

```
IDebugInterceptExceptionCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El DE implementa esta interfaz para informar de que se ha completado el procesamiento de una excepción interceptada. La interfaz [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) debe implementarse en el mismo objeto que esta interfaz. El SDM usa [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la `IDebugEvent2` interfaz.

## <a name="notes-for-callers"></a>Notas para llamadores
 El DE crea y envía este objeto de evento para notificar la finalización de una excepción interceptada. El evento se envía mediante la función de devolución de llamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) proporcionada por el SDM cuando se adjunta al programa que se está depurando.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 La `IDebugInterceptExceptionCompleteEvent2` interfaz implementa los métodos siguientes.

|Método|Descripción|
|------------|-----------------|
|[GetInterceptCookie](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2-getinterceptcookie.md)|Devuelve el valor único asociado a la excepción controlada.|

## <a name="remarks"></a>Observaciones
 [Interceptcurrentexception (](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) enviará este evento cuando el método haya completado correctamente el control de una excepción interceptada.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)
- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
