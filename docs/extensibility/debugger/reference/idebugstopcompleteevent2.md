---
description: El motor DE depuración (DE) puede enviar este evento opcional al administrador de depuración de sesión (SDM) cuando se ha detenido un programa.
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4d96aa335c8951b9dfc80517bf797338cd590b48
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159750"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

El motor DE depuración (DE) puede enviar este evento opcional al administrador de depuración de sesión (SDM) cuando se ha detenido un programa.

## <a name="syntax"></a>Syntax

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
