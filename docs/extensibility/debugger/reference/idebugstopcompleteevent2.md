---
description: El motor DE depuración (DE) puede enviar este evento opcional al administrador de depuración de sesión (SDM) cuando se ha detenido un programa.
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8e4fd1826f44cb1d830ef45874b1c41c21a34895
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087150"
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
