---
title: IDebugPortSupplier3 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f015c21f71f064f2302660ebc75ef00a245348c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724441"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
Esta interfaz permite a un llamador determinar si un proveedor de puertos puede conservar los puertos (escribiéndolos en el disco) entre invocaciones del depurador y, a continuación, obtener una lista de esos puertos conservados.

## <a name="syntax"></a>Sintaxis

```
IDebugPortSupplier3 : IDebugPortSupplier2
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un proveedor de puertos personalizado implementa esta interfaz para admitir la conservación o el almacenamiento de información de puerto en el disco. Esta interfaz debe implementarse en el mismo objeto que el [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) interfaz.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Llame a [QueryInterface](/cpp/atl/queryinterface) en la `IDebugPortSupplier2` interfaz para obtener esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden Vtable
 Además de los métodos heredados de la [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) interfaz, esta interfaz admite lo siguiente:

|Método|Descripción|
|------------|-----------------|
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Devuelve si el proveedor de puertos puede conservar los puertos (escribiéndolos en el disco) entre las invocaciones del depurador.|
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Devuelve un objeto que se puede usar para enumerar a través de todos los puertos escritos en el disco por este proveedor de puertos.|

## <a name="remarks"></a>Observaciones
 Si un proveedor de puertos puede conservar puertos entre invocaciones, debe implementar esta interfaz. Los puertos deben cargarse cuando se crea una instancia del proveedor de puertos y escribirse en el disco cuando se destruye el proveedor de puertos.

 Un motor de depuración normalmente no interactúa con un proveedor de puertos y no tendrá ningún uso para esta interfaz.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
