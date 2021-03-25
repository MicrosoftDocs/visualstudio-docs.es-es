---
description: El motor de depuración (DE) envía esta interfaz al administrador de depuración de la sesión (SDM) cuando se crea un subproceso en un programa que se está depurando.
title: IDebugThreadCreateEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThreadCreateEvent2
helpviewer_keywords:
- IDebugThreadCreateEvent2
ms.assetid: aee34a14-4f9c-4ad3-845f-c96ee938cefd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 054163732d0ca4a2b818acf948da0490ebe0f8e6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086968"
---
# <a name="idebugthreadcreateevent2"></a>IDebugThreadCreateEvent2
El motor de depuración (DE) envía esta interfaz al administrador de depuración de la sesión (SDM) cuando se crea un subproceso en un programa que se está depurando.

## <a name="syntax"></a>Sintaxis

```
IDebugThreadCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El DE implementa esta interfaz para informar de que se ha creado un subproceso. La interfaz [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) debe implementarse en el mismo objeto que esta interfaz. El SDM usa [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la `IDebugEvent2` interfaz.

## <a name="notes-for-callers"></a>Notas para llamadores
 Crea y envía este objeto DE evento para informar de que se ha creado un subproceso. El evento se envía mediante la función de devolución de llamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) proporcionada por el SDM cuando se adjunta al programa que se está depurando.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
