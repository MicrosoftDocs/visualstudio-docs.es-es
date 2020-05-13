---
title: IDebugThread2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2
helpviewer_keywords:
- IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1965ff1b4cfa89e4584c194942dec7ae486473ff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718582"
---
# <a name="idebugthread2"></a>IDebugThread2
Esta interfaz representa un subproceso que se ejecuta en un programa.

## <a name="syntax"></a>Sintaxis

```
IDebugThread2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración (DE) implementa esta interfaz para representar un subproceso de ejecución en un solo programa.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Llame a [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md) para obtener esta interfaz que representa el subproceso activo actualmente.

 Esta interfaz también se utiliza en la creación de una solicitud de punto de interrupción (consulte [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)).

 Esta interfaz también se devuelve al resolver un punto de interrupción de límite o error (consulte [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) y [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)).

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IDebugThread2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|Recupera una lista de los marcos de pila para este subproceso.|
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|Obtiene el nombre del subproceso.|
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|Establece el nombre del subproceso.|
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|Obtiene el programa en el que se ejecuta un subproceso.|
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|Determina si la siguiente instrucción se puede establecer en el marco de pila y el contexto de código especificados.|
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|Establece la siguiente instrucción en el marco de pila y el contexto de código especificados.|
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|Obtiene el identificador de subproceso del sistema.|
|[Suspender](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|Suspende un subproceso.|
|[Reanudación](../../../extensibility/debugger/reference/idebugthread2-resume.md)|Reanuda un subproceso.|
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|Obtiene propiedades que describen un subproceso.|
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|Obtiene el subproceso lógico asociado a este subproceso físico.|

## <a name="remarks"></a>Observaciones
 Dado que un único subproceso físico se `IDebugThread2` puede ejecutar en varios programas, más de uno de más de un programa puede representar el mismo subproceso físico.

 Cuando se produce un punto de interrupción o una excepción, se envía un evento llamando a [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md). Uno de los argumentos de `IDebugThread2` este método es una interfaz que representa el subproceso actual. [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) se utiliza para obtener la interfaz [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) para el marco de pila actual.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
