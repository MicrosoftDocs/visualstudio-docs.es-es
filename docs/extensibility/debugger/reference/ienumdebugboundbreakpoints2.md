---
description: Esta interfaz enumera los puntos de interrupción enlazados asociados a un punto de interrupción pendiente o a un evento enlazado de punto de interrupción.
title: IEnumDebugBoundBreakpoints2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugBoundBreakpoints2
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2
ms.assetid: ea03e7e1-28d6-40b7-8097-bbb61d3b7caa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d6942bb8388afd596221325f86c3934b684af6f9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080195"
---
# <a name="ienumdebugboundbreakpoints2"></a>IEnumDebugBoundBreakpoints2
Esta interfaz enumera los puntos de interrupción enlazados asociados a un punto de interrupción pendiente o a un evento enlazado de punto de interrupción.

## <a name="syntax"></a>Sintaxis

```
IEnumDebugBoundBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración (DE) implementa esta interfaz como parte de su compatibilidad con los puntos de interrupción. Se debe implementar esta interfaz si se admiten puntos de interrupción.

## <a name="notes-for-callers"></a>Notas para llamadores
 Llamadas de Visual Studio:

- [EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) para obtener esta interfaz que representa una lista de todos los puntos de interrupción que se han desencadenado.

- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) para obtener esta interfaz que representa una lista de todos los puntos de interrupción enlazados.

- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) para obtener esta interfaz que representa una lista de todos los puntos de interrupción enlazados a ese punto de interrupción pendiente.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IEnumDebugBoundBreakpoints2` .

|Método|Descripción|
|------------|-----------------|
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)|Recupera un número especificado de puntos de interrupción enlazados en una secuencia de enumeración.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-skip.md)|Omite un número especificado de puntos de interrupción enlazados en una secuencia de enumeración.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-reset.md)|Restablece una secuencia de enumeración al principio.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-getcount.md)|Obtiene el número de puntos de interrupción enlazados en un enumerador.|

## <a name="remarks"></a>Observaciones
 Visual Studio usa los puntos de interrupción enlazados que representa esta interfaz para actualizar la presentación de los puntos de interrupción en el IDE.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
