---
title: IDebugBreakpointResolution2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointResolution2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 451d5bce-b9c1-48ff-beaa-2b4c3e1ceea0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 256ea48b20f9bc91b73b94e6a7b9c285166e62a0
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56716134"
---
# <a name="idebugbreakpointresolution2"></a>IDebugBreakpointResolution2
Esta interfaz representa la información que describe un punto de interrupción enlazado.

## <a name="syntax"></a>Sintaxis

```
IDebugBreakpointResolution2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración (DE) implementa esta interfaz como parte de su compatibilidad con los puntos de interrupción. Esta interfaz proporciona una descripción de un punto de interrupción enlazado que utiliza el Administrador de depuración de sesión cuando un usuario ve las propiedades de un punto de interrupción.

## <a name="notes-for-callers"></a>Notas para los llamadores
 Una llamada a [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) devuelve esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 La tabla siguiente muestran los métodos de `IDebugBreakpointResolution2`.

|Método|Descripción|
|------------|-----------------|
|[GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Obtiene el tipo del punto de interrupción representado por esta resolución.|
|[GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Obtiene la información de resolución de punto de interrupción que describe este punto de interrupción.|

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)