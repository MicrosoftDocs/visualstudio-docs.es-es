---
title: IDebugExceptionEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3fd2a449c71b69c654cd19846990f7b722f706de
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325993"
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
El motor de depuración (DE) envía esta interfaz para el Administrador de depuración de la sesión (SDM) cuando se produce una excepción en el programa que se está ejecutando actualmente.

## <a name="syntax"></a>Sintaxis

```
IDebugExceptionEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 La DE implementa esta interfaz para el informe que se ha producido una excepción en el programa que se está depurando. El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaz debe implementarse en el mismo objeto que esta interfaz. Usa el SDM [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la `IDebugEvent2` interfaz.

## <a name="notes-for-callers"></a>Notas para los llamadores
 La DE crea y envía este objeto de evento para notificar una excepción. El evento se envía mediante la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) función de devolución de llamada que proporciona el SDM cuando adjunta al programa que se está depurando.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 La tabla siguiente muestran los métodos de `IDebugExceptionEvent2`.

|Método|Descripción|
|------------|-----------------|
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|Obtiene información detallada sobre la excepción que se desencadena este evento.|
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Obtiene una descripción inteligible de la excepción que se desencadena este evento.|
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Determina si el motor de depuración (DE) es compatible con la opción de pasar esta excepción al programa que se está depurando cuando se reanuda la ejecución.|
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Especifica si se debe pasar la excepción el programa que se está depurando cuando se reanuda la ejecución, o si debe descartarse la excepción.|

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Comentarios
 Antes de enviar el evento, la DE comprueba si se ha designado una excepción de primera oportunidad o segunda oportunidad a este evento de excepción mediante una llamada anterior a [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md). Si se ha designado como una excepción de primera oportunidad, el `IDebugExceptionEvent2` se envía el evento para el SDM. Si no es así, ofrece a la DE la aplicación una oportunidad para controlar la excepción. Si no se proporciona ningún controlador de excepción y la excepción se ha designado como una excepción de la segunda oportunidad, el `IDebugExceptionEvent2` se envía el evento para el SDM. En caso contrario, la DE reanuda la ejecución del programa y el sistema operativo o en tiempo de ejecución controla la excepción.

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)