---
title: IDebugStopCompleteEvent2 ? Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719447"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

El motor de depuración (DE) puede enviar este evento opcional al administrador de depuración de sesión (SDM) cuando un programa se ha detenido.

## <a name="syntax"></a>Sintaxis

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores

Esta interfaz se introdujo con Visual Studio 2005. Las versiones anteriores no admiten la detención asincrónica.

- [El](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) SDM llama a Stop en escenarios de varios procesos o de varios programas. Cuando un programa envía un evento de detención al SDM, el SDM solicita que otros programas se detengan también.

Stop se utiliza para informar de forma asincrónica al SDM que un programa se ha detenido. Informar al SDM es útil para un motor de depuración de intérprete, donde a veces no se ejecuta ningún código dentro del programa depurado, por lo que [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) no se puede completar sincrónicamente. Si un motor de depuración desea emplear `S_ASYNC_STOP` esta notificación asincrónica, debe devolver desde [Detener](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).

## <a name="requirements"></a>Requisitos

Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
