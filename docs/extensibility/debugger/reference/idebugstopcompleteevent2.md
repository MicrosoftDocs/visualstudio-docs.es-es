---
title: IDebugStopCompleteEvent2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ed73821021d3a993507db9925c512119fbb98ca1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

El motor de depuración (Alemania) puede enviar este evento opcional para el Administrador de sesión de depuración (SDM) cuando un programa se ha detenido.

## <a name="syntax"></a>Sintaxis

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores

Esta interfaz se introdujo con Visual Studio 2005. Las versiones anteriores no admitían detención asincrónica.

[Detener](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) llama el SDM en escenarios de varios procesos o programas múltiples. Cuando un programa envía un evento de detención para la SDM, el SDM solicita otros programas para detener, demasiado.

Detención se usa para informar de forma asincrónica el SDM que un programa se ha detenido. Que informa el SDM es útil para un motor de depuración de intérprete, donde a veces no se está ejecutando ningún código dentro de la depuración del programa, por lo que [detener](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) no puede completarse sincrónicamente. Si desea que un motor de depuración emplean esta notificación asincrónica, debe devolver `S_ASYNC_STOP` de [detener](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).

## <a name="requirements"></a>Requisitos

Encabezado: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll