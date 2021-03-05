---
description: Esta interfaz representa un subproceso que se ejecuta en un programa.
title: IDebugThread2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2
helpviewer_keywords:
- IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d8b09aa546e4711b1c11623a3596ba0e385b2a14
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164427"
---
# <a name="idebugthread2"></a>IDebugThread2
Esta interfaz representa un subproceso que se ejecuta en un programa.

## <a name="syntax"></a>Syntax

```
IDebugThread2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración (DE) implementa esta interfaz para representar un subproceso de ejecución en un único programa.

## <a name="notes-for-callers"></a>Notas para llamadores
 Llame a [GetThread (](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md) para obtener esta interfaz que representa el subproceso activo actualmente.

 Esta interfaz también se usa para crear una solicitud de punto de interrupción (vea [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)).

 También se devuelve esta interfaz al resolver un punto de interrupción enlazado o de error (vea [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) y [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)).

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugThread2` .

|Método|Descripción|
|------------|-----------------|
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|Recupera una lista de los marcos de pila para este subproceso.|
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|Obtiene el nombre del subproceso.|
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|Establece el nombre del subproceso.|
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|Obtiene el programa en el que se está ejecutando un subproceso.|
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|Determina si la instrucción siguiente se puede establecer en el marco de pila y el contexto de código especificados.|
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|Establece la siguiente instrucción en el marco de pila y el contexto de código especificados.|
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|Obtiene el identificador del subproceso del sistema.|
|[Suspender](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|Suspende un subproceso.|
|[Reanudar](../../../extensibility/debugger/reference/idebugthread2-resume.md)|Reanuda un subproceso.|
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|Obtiene las propiedades que describen un subproceso.|
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|Obtiene el subproceso lógico asociado a este subproceso físico.|

## <a name="remarks"></a>Observaciones
 Dado que un único subproceso físico puede ejecutarse en varios programas, más de un `IDebugThread2` programa puede representar el mismo subproceso físico.

 Cuando se produce un punto de interrupción o una excepción, se envía un evento mediante una llamada al [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md). Uno de los argumentos de este método es una `IDebugThread2` interfaz que representa el subproceso actual. [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) se usa para obtener la interfaz [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) para el marco de pila actual.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
