---
title: IDebugQueryEngine2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbe3444d5bcdb31a4ef7619b123041f459a09852
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62916414"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
Esta interfaz permite que la sesión de depuración manager (SDM) recuperar una interfaz que representa el motor de depuración (DE).

## <a name="syntax"></a>Sintaxis

```
IDebugQueryEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 La DE implementa esta interfaz en los objetos que implementan las interfaces DE más comunes (como [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md), [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md), y [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)) en a fin de permitir el acceso a la [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) interfaz de la DE sí mismo.

## <a name="notes-for-callers"></a>Notas para los llamadores
 Llame a [QueryInterface](/cpp/atl/queryinterface) en una interfaz DE típica para obtener esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 La tabla siguiente muestran los métodos de `IDebugQueryEngine2`.

|Método|Descripción|
|------------|-----------------|
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Obtiene una interfaz de motor DE depuración personalizado.|

## <a name="remarks"></a>Comentarios
 Esta interfaz se implementa normalmente en el objeto que implementa el [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaz con el fin de admitir ordenados de causalidad ejecución paso a paso a través de funciones, es decir, cuando el depurador salir de una función, el Para ejecutar la función Next no puede ser la función anterior en la pila, pero una función en otro subproceso por completo. Para obtener una definición de "causalidad", consulte el [Glosario del depurador de Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)