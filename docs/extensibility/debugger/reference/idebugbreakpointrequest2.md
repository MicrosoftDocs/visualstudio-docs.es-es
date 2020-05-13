---
title: IDebugBreakpointRequest2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f30f9698c9c81322edd6935b40c16cad6f46024c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734913"
---
# <a name="idebugbreakpointrequest2"></a>IDebugBreakpointRequest2
Esta interfaz representa la información necesaria para crear y enlazar cualquier tipo de punto de interrupción.

## <a name="syntax"></a>Sintaxis

```
IDebugBreakpointRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El administrador de depuración de sesión (SDM) implementa típicamente esta interfaz.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 El motor de depuración (DE) recibe esta interfaz a través de una llamada a [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) para crear un punto de interrupción pendiente. Una llamada a [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) puede recuperar esta interfaz de la DE.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IDebugBreakpointRequest2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|Obtiene el tipo de ubicación de punto de interrupción de esta solicitud de punto de interrupción.|
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|Obtiene la información de solicitud de punto de interrupción que describe esta solicitud de punto de interrupción.|

## <a name="remarks"></a>Observaciones
 Una vez cargado el programa que se está depurando, una llamada a [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) enlaza un punto de interrupción pendiente a la ubicación solicitada en el programa.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)
- [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
