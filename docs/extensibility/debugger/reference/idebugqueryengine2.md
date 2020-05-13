---
title: IDebugQueryEngine2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31b1784055c54c9243237c81edb708e13de9bc5b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720652"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
Esta interfaz permite que el administrador de depuración de sesión (SDM) recupere una interfaz que represente el motor de depuración (DE).

## <a name="syntax"></a>Sintaxis

```
IDebugQueryEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El DE implementa esta interfaz en los objetos que implementan las interfaces DE más comunes (como [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md), [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)y [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)) para permitir el acceso a la [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) interfaz de la DE sí mismo.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Llame a [QueryInterface](/cpp/atl/queryinterface) en una interfaz DE típica para obtener esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IDebugQueryEngine2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Obtiene una interfaz de motor de depuración (DE) personalizada.|

## <a name="remarks"></a>Observaciones
 Esta interfaz se implementa normalmente en el objeto que implementa el [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaz con el fin de admitir causalidad ordenada paso a través de funciones; es decir, cuando el depurador sale de una función, la siguiente función que se ejecuta puede no ser la función anterior en la pila, sino una función en otro subproceso por completo. Para obtener una definición de "causalidad", vea el [glosario](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md)del depurador de Visual Studio .

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
