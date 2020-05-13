---
title: IDebugCanStopEvent2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0a3710756f02d7c622be94bab6c3056fb051827
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734512"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
Esta interfaz se utiliza para preguntar al administrador de depuración de sesión (SDM) si se debe parar en la ubicación de código actual.

## <a name="syntax"></a>Sintaxis

```
IDebugCanStopEvent2 : IUknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración (DE) implementa esta interfaz para admitir el paso a paso a través del código fuente. El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaz debe implementarse en el mismo objeto que esta `IDebugEvent2` interfaz (el SDM utiliza [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la interfaz).

 La implementación de esta interfaz debe comunicar la llamada de [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) del SDM al motor de depuración. Por ejemplo, esto se puede hacer con un mensaje publicado en el subproceso de control de mensajes del motor de depuración o el `IDebugCanStopEvent2::CanStop`objeto que implementa esta interfaz podría contener una referencia al motor de depuración y volver a llamar al motor de depuración con la marca pasada.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 El DE puede enviar este método cada vez que se pide a des -des para continuar la ejecución y el DE está paso a través del código. Este evento se envía mediante el [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) función de devolución de llamada proporcionada por el SDM cuando se adjunta al programa que se está depurando.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IDebugCanStopEvent2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Obtiene el motivo de este evento.|
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Especifica si el programa que se está depurando debe detenerse en la ubicación de este evento (y enviar un evento que describe el motivo de la detención) o simplemente continuar la ejecución.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Obtiene el contexto del documento que describe la ubicación de este evento.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Obtiene el contexto de código que describe la ubicación de este evento.|

## <a name="remarks"></a>Observaciones
 El DE envía esta interfaz si el usuario entra en una función y el DE no encuentra ninguna información de depuración allí o la información de depuración existe pero el DE no sabe si el código fuente se puede mostrar para esa ubicación.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
