---
description: El motor DE depuración (DE) envía esta interfaz al administrador de depuración de la sesión (SDM) cuando un programa se detiene en un punto de interrupción.
title: IDebugBreakpointEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointEvent2
helpviewer_keywords:
- IDebugBreakpointEvent2 interface
ms.assetid: 50b3a7a7-331b-42c8-922c-ff3522ebe1da
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 29dd8aa27c6b73d09036905a8c6e43af878419eb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054548"
---
# <a name="idebugbreakpointevent2"></a>IDebugBreakpointEvent2
El motor DE depuración (DE) envía esta interfaz al administrador de depuración de la sesión (SDM) cuando un programa se detiene en un punto de interrupción.

## <a name="syntax"></a>Sintaxis

```
IDebugBreakpointEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El DE implementa esta interfaz como parte de su compatibilidad con los puntos de interrupción. La interfaz [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) debe implementarse en el mismo objeto que esta interfaz (el SDM usa [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la `IDebugEvent2` interfaz).

## <a name="notes-for-callers"></a>Notas para llamadores
 Crea y envía este objeto DE evento cuando se encuentra al menos un punto de interrupción en el programa. El evento se envía mediante la función de devolución de llamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) proporcionada por el SDM cuando se adjunta al programa que se está depurando.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugBreakpointEvent2` .

|Método|Descripción|
|------------|-----------------|
|[EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md)|Crea un enumerador para todos los puntos de interrupción que se han desencadenado en la ubicación del código actual.|

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
