---
description: Esta interfaz permite a un llamador determinar si un proveedor de puerto puede conservar los puertos (escribiéndolo en el disco) entre las invocaciones del depurador y, a continuación, obtener una lista de esos puertos conservados.
title: IDebugPortSupplier3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fa17984c9b7f3e87d4a7118188ecc6ca79c5deef
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071940"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
Esta interfaz permite a un llamador determinar si un proveedor de puerto puede conservar los puertos (escribiéndolo en el disco) entre las invocaciones del depurador y, a continuación, obtener una lista de esos puertos conservados.

## <a name="syntax"></a>Sintaxis

```
IDebugPortSupplier3 : IDebugPortSupplier2
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un proveedor de Puerto personalizado implementa esta interfaz para admitir la persistencia o el almacenamiento de la información de puerto en el disco. Esta interfaz se debe implementar en el mismo objeto que la interfaz [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) .

## <a name="notes-for-callers"></a>Notas para llamadores
 Llame a [QueryInterface](/cpp/atl/queryinterface) en la `IDebugPortSupplier2` interfaz para obtener esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden vtable
 Además de los métodos heredados de la interfaz [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) , esta interfaz admite lo siguiente:

|Método|Descripción|
|------------|-----------------|
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Devuelve si el proveedor del puerto puede conservar los puertos (escribiéndolo en el disco) entre las invocaciones del depurador.|
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Devuelve un objeto que se puede usar para enumerar todos los puertos que este proveedor de puerto ha escrito en el disco.|

## <a name="remarks"></a>Observaciones
 Si un proveedor de puertos puede conservar los puertos a través de las invocaciones, debe implementar esta interfaz. Los puertos se deben cargar cuando se crea una instancia del proveedor del puerto y se escriben en el disco cuando se destruye el proveedor del puerto.

 Normalmente, un motor de depuración no interactúa con un proveedor de puerto y no tendrá ningún uso para esta interfaz.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
