---
description: Esta interfaz se envía mediante el motor de depuración (DE) al administrador de depuración de la sesión (SDM) cuando el programa que se está depurando completa paso a paso por instrucciones, paso a paso por procedimientos o paso a paso para salir de una línea de código fuente, instrucción o instrucción.
title: IDebugStepCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStepCompleteEvent2
helpviewer_keywords:
- IDebugStepCompleteEvent2 interface
ms.assetid: eba2b76e-f90d-486b-ae5c-c47f1b8ba2e5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f366b9eb1d9406ba5207016ca97ea40d1fd48529
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149540"
---
# <a name="idebugstepcompleteevent2"></a>IDebugStepCompleteEvent2
Esta interfaz se envía mediante el motor de depuración (DE) al administrador de depuración de la sesión (SDM) cuando el programa que se está depurando completa paso a paso por instrucciones, paso a paso por procedimientos o paso a paso para salir de una línea de código fuente, instrucción o instrucción.

## <a name="syntax"></a>Syntax

```
IDebugStepCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El DE implementa esta interfaz para notificar la finalización de una operación de paso. La interfaz [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) debe implementarse en el mismo objeto que esta interfaz. El SDM usa [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la `IDebugEvent2` interfaz.

## <a name="notes-for-callers"></a>Notas para llamadores
 El DE crea y envía este objeto de evento para notificar la finalización de una operación de paso. El evento se envía mediante la función de devolución de llamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) proporcionada por el SDM cuando se adjunta al programa que se está depurando.

## <a name="remarks"></a>Observaciones
 Una vez completado el paso, el programa que se está depurando se pausa una vez más y el IDE actualiza todas sus ventanas.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
