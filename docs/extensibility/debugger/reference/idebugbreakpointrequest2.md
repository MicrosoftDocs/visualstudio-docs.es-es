---
description: La interfaz IDebugBreakPointRequest2 representa la información necesaria para crear y enlazar cualquier tipo de punto de interrupción.
title: IDebugBreakpointRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8788e7a78bcd4c03567e5d07c96a310fa6970fb1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054457"
---
# <a name="idebugbreakpointrequest2"></a>IDebugBreakpointRequest2
Esta interfaz representa la información necesaria para crear y enlazar cualquier tipo de punto de interrupción.

## <a name="syntax"></a>Sintaxis

```
IDebugBreakpointRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Normalmente, el administrador de depuración de sesión (SDM) implementa esta interfaz.

## <a name="notes-for-callers"></a>Notas para llamadores
 El motor DE depuración (DE) recibe esta interfaz a través de una llamada a [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) para crear un punto de interrupción pendiente. Una llamada a [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) puede recuperar esta interfaz de de.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugBreakpointRequest2` .

|Método|Descripción|
|------------|-----------------|
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|Obtiene el tipo de ubicación del punto de interrupción de esta solicitud de punto de interrupción.|
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|Obtiene la información de solicitud de punto de interrupción que describe esta solicitud de punto de interrupción.|

## <a name="remarks"></a>Observaciones
 Una vez cargado el programa que se está depurando, una llamada a [BIND](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) enlaza un punto de interrupción pendiente a la ubicación solicitada en el programa.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)
- [Volver](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
