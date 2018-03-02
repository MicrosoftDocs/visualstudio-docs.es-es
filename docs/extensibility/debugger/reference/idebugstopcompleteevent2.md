---
title: IDebugStopCompleteEvent2 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: aa8941decfb4e64906c57b719df711ce8779df9c
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/28/2018
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

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll