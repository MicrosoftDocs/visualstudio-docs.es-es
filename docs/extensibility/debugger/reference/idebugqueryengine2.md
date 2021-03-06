---
description: Esta interfaz permite que el administrador de depuración de la sesión (SDM) recupere una interfaz que representa el motor DE depuración (DE).
title: IDebugQueryEngine2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 899c5dceab16d4783cb28bff31c67e67bf5df774
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083653"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
Esta interfaz permite que el administrador de depuración de la sesión (SDM) recupere una interfaz que representa el motor DE depuración (DE).

## <a name="syntax"></a>Sintaxis

```
IDebugQueryEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El DE implementa esta interfaz en los objetos que implementan las interfaces DE más comunes (como [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md), [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)y [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)) para permitir el acceso a la interfaz [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) del propio.

## <a name="notes-for-callers"></a>Notas para llamadores
 Llame a [QueryInterface](/cpp/atl/queryinterface) en una interfaz de una interfaz típica para obtener esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugQueryEngine2` .

|Método|Descripción|
|------------|-----------------|
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Obtiene una interfaz personalizada del motor DE depuración (DE).|

## <a name="remarks"></a>Observaciones
 Esta interfaz se implementa normalmente en el objeto que implementa la interfaz [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) para admitir la ejecución de paso a través de las funciones con orden de causalidad. es decir, cuando el depurador está saliendo de una función, es posible que la función siguiente que se va a ejecutar no sea la función anterior en la pila, sino que una función de otro subproceso esté totalmente. Para obtener una definición de "causalidad", vea el [Glosario del depurador de Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
