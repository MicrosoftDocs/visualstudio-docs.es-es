---
title: IDebugCanStopEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab364b426005c838072fabc1a3c7ed2f7d64ac6a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337343"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
Esta interfaz se usa para formular al administrador de depuración de la sesión (SDM) si se debe detener en la ubicación actual del código.

## <a name="syntax"></a>Sintaxis

```
IDebugCanStopEvent2 : IUknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración (DE) implementa esta interfaz para admitir la ejecución paso a paso por el código fuente. El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaz debe implementarse en el mismo objeto que esta interfaz (usa el SDM [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la `IDebugEvent2` interfaz).

 La implementación de esta interfaz debe comunicar la llamada de SDM de [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) al motor de depuración. Por ejemplo, esto puede hacerse con un mensaje que se registran en el subproceso de control de mensajes del motor de depuración o el objeto que implementa esta interfaz podría contener una referencia al motor de depuración y devuelva la llamada al motor de depuración con el indicador pasado a `IDebugCanStopEvent2::CanStop`.

## <a name="notes-for-callers"></a>Notas para los llamadores
 Puede enviar la DE este método cada vez que la DE se le pide que continúe la ejecución y la DE es recorrer el código. Este evento se envía mediante la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) función de devolución de llamada proporcionada por el SDM cuando adjunta al programa que se está depurando.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 La tabla siguiente muestran los métodos de `IDebugCanStopEvent2`.

|Método|Descripción|
|------------|-----------------|
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Obtiene el motivo de este evento.|
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Especifica si el programa que se está depurando debe detenerse en la ubicación de este evento (y enviar un evento que describe el motivo para detener) o simplemente continuar la ejecución.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Obtiene el contexto del documento que describe la ubicación de este evento.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Obtiene el contexto del código que describe la ubicación de este evento.|

## <a name="remarks"></a>Comentarios
 La DE envía esta interfaz si los pasos de usuario en una función y la DE no encuentra que no existe ninguna información de depuración o existe información de depuración, pero la DE no sabe si se puede mostrar el código fuente para esa ubicación.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)