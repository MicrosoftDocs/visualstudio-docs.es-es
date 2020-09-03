---
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da3eb33d76f55310e6428a34dd09cabbc271aa68
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719447"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

El motor DE depuración (DE) puede enviar este evento opcional al administrador de depuración de sesión (SDM) cuando se ha detenido un programa.

## <a name="syntax"></a>Sintaxis

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores

Esta interfaz se incorporó con Visual Studio 2005. Las versiones anteriores no admiten la detención asincrónica.

- El SDM llama a [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) en escenarios de varios procesos o de varios programas. Cuando un programa envía un evento de detención al SDM, el SDM solicita también que se detengan otros programas.

STOP se usa para informar de forma asincrónica al SDM de que se ha detenido un programa. Informar al SDM es útil para un motor de depuración del intérprete, donde a veces no se ejecuta código dentro del programa depurado, por lo que no se puede completar la [detención](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) de forma sincrónica. Si un motor de depuración desea emplear esta notificación asincrónica, debe devolver `S_ASYNC_STOP` de [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).

## <a name="requirements"></a>Requisitos

Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
