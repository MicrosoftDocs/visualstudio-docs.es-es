---
title: IEnumDebugErrorBreakpoints2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugErrorBreakpoints2
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2
ms.assetid: ffdad73d-969a-45ef-9ad1-7f5d3b814018
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea841a095964b71e301e966bfd0a10c8f7c0c65d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716887"
---
# <a name="ienumdebugerrorbreakpoints2"></a>IEnumDebugErrorBreakpoints2
Esta interfaz enumera los puntos de interrupción de error asociados a un punto de interrupción pendiente.

## <a name="syntax"></a>Sintaxis

```
IEnumDebugErrorBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración (DE) implementa esta interfaz como parte de su compatibilidad con puntos de interrupción.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Visual Studio llama a [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) para obtener esta interfaz que representa una lista de puntos de interrupción que no se pueden enlazar, o [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) para obtener esta interfaz que representa una lista de puntos de interrupción que no estaban enlazados.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IEnumDebugErrorBreakpoints2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)|Recupera un número especificado de puntos de interrupción de error en una secuencia de enumeración.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-skip.md)|Omite un número especificado de puntos de interrupción de error en una secuencia de enumeración.|
|[Restablecer](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-reset.md)|Restablece una secuencia de enumeración al principio.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-getcount.md)|Obtiene el número de puntos de interrupción de error en un enumerador.|

## <a name="remarks"></a>Observaciones
 Esta interfaz contiene una lista de [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) interfaces, cada uno de los cuales describe un punto de interrupción que no se pudo enlazar y por qué no se pudo enlazar. Visual Studio `IEnumDebugErrorBreakpoint2` usa la interfaz para actualizar los puntos de interrupción que se muestran en el IDE.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
