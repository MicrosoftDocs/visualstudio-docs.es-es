---
description: Esta interfaz indica al administrador de depuración de la sesión (SDM) que una interrupción asincrónica se ha completado correctamente.
title: IDebugBreakEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8d2369b2219d155b2210fb2860cc868ec3813bad
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088801"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
Esta interfaz indica al administrador de depuración de la sesión (SDM) que una interrupción asincrónica se ha completado correctamente.

## <a name="syntax"></a>Sintaxis

```
IDebugBreakEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El DE implementa esta interfaz para admitir los saltos de usuario en un programa. La interfaz [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) debe implementarse en el mismo objeto que esta interfaz (el SDM usa [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la `IDebugEvent2` interfaz).

## <a name="notes-for-callers"></a>Notas para llamadores
 El SDM llama a [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) cuando el usuario ha solicitado que el programa que se está depurando esté en pausa. Cuando el programa se ha pausado correctamente, el DE envía el `IDebugBreakEvent2` evento. Este evento se envía mediante la función de devolución de llamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) proporcionada por el SDM cuando se adjunta al programa que se está depurando.

## <a name="remarks"></a>Observaciones
 Por ejemplo, un usuario puede seleccionar el comando **interrumpir todo** en el menú **depurar** para salir de un programa que ejecuta un bucle infinito. El SDM indica al programa que se detenga llamando a [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md). El DE envía `IDebugBreakEvent2` cuando finalmente se detiene el programa.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
