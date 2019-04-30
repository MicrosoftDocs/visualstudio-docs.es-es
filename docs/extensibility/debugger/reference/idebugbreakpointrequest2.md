---
title: IDebugBreakpointRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a984634dbba0fc1d732fe98214a07d8d6c339d4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62923389"
---
# <a name="idebugbreakpointrequest2"></a>IDebugBreakpointRequest2
Esta interfaz representa la información necesaria para crear y enlazar cualquier tipo de punto de interrupción.

## <a name="syntax"></a>Sintaxis

```
IDebugBreakpointRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El Administrador de depuración de la sesión (SDM) normalmente implementa esta interfaz.

## <a name="notes-for-callers"></a>Notas para los llamadores
 El motor de depuración (DE) recibe esta interfaz mediante una llamada a [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) con el fin de crear un punto de interrupción pendiente. Una llamada a [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) puede recuperar esta interfaz de la DE.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 La tabla siguiente muestran los métodos de `IDebugBreakpointRequest2`.

|Método|Descripción|
|------------|-----------------|
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|Obtiene el tipo de ubicación de punto de interrupción de esta solicitud de punto de interrupción.|
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|Obtiene la información de solicitud de punto de interrupción que describe esta solicitud de punto de interrupción.|

## <a name="remarks"></a>Comentarios
 Después el programa que se está depurando se han cargado, una llamada a [enlazar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) enlaza un punto de interrupción pendiente a la ubicación solicitada en el programa.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)
- [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)