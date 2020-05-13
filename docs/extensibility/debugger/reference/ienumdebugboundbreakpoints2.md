---
title: IEnumDebugBoundBreakpoints2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugBoundBreakpoints2
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2
ms.assetid: ea03e7e1-28d6-40b7-8097-bbb61d3b7caa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 421d46efbef189fd6ffc86812d2bfdd28f5da5ff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717443"
---
# <a name="ienumdebugboundbreakpoints2"></a>IEnumDebugBoundBreakpoints2
Esta interfaz enumera los puntos de interrupción enlazados asociados a un evento enlazado de punto de interrupción o punto de interrupción pendiente.

## <a name="syntax"></a>Sintaxis

```
IEnumDebugBoundBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración (DE) implementa esta interfaz como parte de su compatibilidad con puntos de interrupción. Esta interfaz debe implementarse si se admiten puntos de interrupción.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Llamadas de Visual Studio:

- [EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) para obtener esta interfaz que representa una lista de todos los puntos de interrupción que se desencadenaron.

- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) para obtener esta interfaz que representa una lista de todos los puntos de interrupción enlazados.

- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) para obtener esta interfaz que representa una lista de todos los puntos de interrupción enlazados a ese punto de interrupción pendiente.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IEnumDebugBoundBreakpoints2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)|Recupera un número especificado de puntos de interrupción enlazados en una secuencia de enumeración.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-skip.md)|Omite un número especificado de puntos de interrupción enlazados en una secuencia de enumeración.|
|[Restablecer](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-reset.md)|Restablece una secuencia de enumeración al principio.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-getcount.md)|Obtiene el número de puntos de interrupción enlazados en un enumerador.|

## <a name="remarks"></a>Observaciones
 Visual Studio usa los puntos de interrupción enlazados representados por esta interfaz para actualizar la presentación de puntos de interrupción en el IDE.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
