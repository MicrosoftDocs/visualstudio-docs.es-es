---
title: IDebugInterceptExceptionCompleteEvent2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugInterceptExceptionCompleteEvent2
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2
ms.assetid: 8ebc256b-5428-4ed6-a505-6aedc8242b8e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a07f2808c1aaeca3c1631fce658fdf6e8da32d60
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727764"
---
# <a name="idebuginterceptexceptioncompleteevent2"></a>IDebugInterceptExceptionCompleteEvent2
Esta interfaz es enviada por el motor de depuración (DE) al administrador de depuración de sesión (SDM) cuando el DE ha completado el manejo de un evento interceptado.

## <a name="syntax"></a>Sintaxis

```
IDebugInterceptExceptionCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 La DE implementa esta interfaz para informar de que se ha completado el procesamiento de una excepción interceptada. El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaz debe implementarse en el mismo objeto que esta interfaz. El SDM utiliza [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la `IDebugEvent2` interfaz.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 El DE crea y envía este objeto de evento para informar de la finalización de una excepción interceptada. El evento se envía mediante la función de devolución de llamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) proporcionada por el SDM cuando se adjunta al programa que se está depurando.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 La `IDebugInterceptExceptionCompleteEvent2` interfaz implementa los métodos siguientes.

|Método|Descripción|
|------------|-----------------|
|[GetInterceptCookie](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2-getinterceptcookie.md)|Devuelve el valor único asociado a la excepción controlada.|

## <a name="remarks"></a>Observaciones
 Este evento se enviará mediante [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) cuando ese método haya completado correctamente el control de una excepción interceptada.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
