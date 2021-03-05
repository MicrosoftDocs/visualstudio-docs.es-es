---
description: El motor DE depuración (DE) envía esta interfaz al administrador de depuración de la sesión (SDM) cuando se produce una excepción en el programa que se está ejecutando actualmente.
title: IDebugExceptionEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e171154d933ac533f6a63469321b5a0d22e8651b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152773"
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
El motor DE depuración (DE) envía esta interfaz al administrador de depuración de la sesión (SDM) cuando se produce una excepción en el programa que se está ejecutando actualmente.

## <a name="syntax"></a>Syntax

```
IDebugExceptionEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El DE implementa esta interfaz para notificar que se ha producido una excepción en el programa que se está depurando. La interfaz [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) debe implementarse en el mismo objeto que esta interfaz. El SDM usa [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la `IDebugEvent2` interfaz.

## <a name="notes-for-callers"></a>Notas para llamadores
 Crea y envía este objeto DE evento para notificar una excepción. El evento se envía utilizando la función de devolución de llamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) proporcionada por el SDM cuando se adjunta al programa que se está depurando.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugExceptionEvent2` .

|Método|Descripción|
|------------|-----------------|
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|Obtiene información detallada sobre la excepción que desencadenó este evento.|
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Obtiene una descripción inteligible de la excepción que se produjo al desencadenar este evento.|
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Determina si el motor de depuración (DE) admite o no la opción de pasar esta excepción al programa que se está depurando cuando se reanuda la ejecución.|
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Especifica si la excepción se debe pasar al programa que se está depurando cuando se reanuda la ejecución o si se debe descartar la excepción.|

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Observaciones
 Antes DE enviar el evento, el método DE realiza una comprobación para ver si este evento de excepción se ha designado como una excepción de primera o segunda oportunidad mediante una llamada anterior a [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md). Si se ha designado como una excepción de primera oportunidad, el `IDebugExceptionEvent2` evento se envía al SDM. DE lo contrario, el DE proporciona a la aplicación una oportunidad para controlar la excepción. Si no se proporciona ningún controlador de excepciones y la excepción se ha designado como una excepción de segunda oportunidad, el `IDebugExceptionEvent2` evento se envía al SDM. De lo contrario, el DE reanuda la ejecución del programa y el sistema operativo o el tiempo DE ejecución controla la excepción.

## <a name="see-also"></a>Consulte también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
