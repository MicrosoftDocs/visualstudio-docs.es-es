---
description: Los nodos de programa utilizan esta interfaz para especificar todos los motores de depuración posibles (DE) que pueden depurar este programa.
title: IDebugProgramEngines2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2
helpviewer_keywords:
- IDebugProgramEngines2 interface
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e0202185d760a1e3334996906807e5922fe61e0a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084225"
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
Los nodos de programa utilizan esta interfaz para especificar todos los motores de depuración posibles (DE) que pueden depurar este programa.

## <a name="syntax"></a>Sintaxis

```
IDebugProgramEngines2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un DE o un proveedor DE puerto personalizado implementa esta interfaz en el mismo objeto que implementa [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) para permitir el establecimiento DE un de un determinado de para su uso en un programa determinado.

## <a name="notes-for-callers"></a>Notas para llamadores
 Llame a [QueryInterface](/cpp/atl/queryinterface) en una `IDebugProgramNode2` interfaz para obtener esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugProgramEngines2` .

|Método|Descripción|
|------------|-----------------|
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|Indica todo el posible DEs que puede depurar este programa.|
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|Selecciona el DE que se va a usar para depurar este programa.|

## <a name="remarks"></a>Observaciones
 Una vez que el usuario elige un DE, esa opción se registra con el nodo del programa mediante una llamada a [SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md). El motor seleccionado se convierte en el motor devuelto por [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md).

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)
