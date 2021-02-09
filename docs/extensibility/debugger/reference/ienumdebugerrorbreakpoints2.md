---
title: IEnumDebugErrorBreakpoints2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugErrorBreakpoints2
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2
ms.assetid: ffdad73d-969a-45ef-9ad1-7f5d3b814018
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 33ff6805537327b29b1d43b1bf4009b431452fc1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896978"
---
# <a name="ienumdebugerrorbreakpoints2"></a>IEnumDebugErrorBreakpoints2
Esta interfaz enumera los puntos de interrupción de error asociados a un punto de interrupción pendiente.

## <a name="syntax"></a>Sintaxis

```
IEnumDebugErrorBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración (DE) implementa esta interfaz como parte de su compatibilidad con los puntos de interrupción.

## <a name="notes-for-callers"></a>Notas para llamadores
 Visual Studio llama a [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) para obtener esta interfaz que representa una lista de puntos de interrupción que no se pueden enlazar, o [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) para obtener esta interfaz que representa una lista de puntos de interrupción no enlazados.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IEnumDebugErrorBreakpoints2` .

|Método|Descripción|
|------------|-----------------|
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)|Recupera un número especificado de puntos de interrupción de error en una secuencia de enumeración.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-skip.md)|Omite un número especificado de puntos de interrupción de error en una secuencia de enumeración.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-reset.md)|Restablece una secuencia de enumeración al principio.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-getcount.md)|Obtiene el número de puntos de interrupción de error en un enumerador.|

## <a name="remarks"></a>Notas
 Esta interfaz contiene una lista de interfaces [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) , cada una de las cuales describe un punto de interrupción que no se pudo enlazar y por qué no se pudo enlazar. Visual Studio usa la `IEnumDebugErrorBreakpoint2` interfaz para actualizar los puntos de interrupción que se muestran en el IDE.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
