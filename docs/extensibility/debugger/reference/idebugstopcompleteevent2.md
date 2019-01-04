---
title: IDebugStopCompleteEvent2 | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 39da50c17d4d4b8b02390e0d2960d5696b93b1f2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53932902"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

El motor de depuración (DE) puede enviar este evento opcional para el Administrador de depuración de la sesión (SDM) cuando se ha detenido un programa.

## <a name="syntax"></a>Sintaxis

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores

Esta interfaz se introdujo con Visual Studio 2005. Las versiones anteriores no eran compatibles con la detención asincrónica.

[Detener](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) llama el SDM en escenarios de varios procesos o de varios programas. Cuando un programa envía un evento de detención en el SDM, el SDM solicita otros programas para detener, demasiado.

Detención se usa para informar de forma asincrónica el SDM que se ha detenido un programa. Que informa el SDM es útil para un motor de depuración del intérprete, que a veces no se ejecuta ningún código dentro del depurado de programa, lo [detener](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) no se puede completar de forma sincrónica. Si un motor de depuración desea emplear esta notificación asincrónica, debe devolver `S_ASYNC_STOP` desde [detener](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).

## <a name="requirements"></a>Requisitos

Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll