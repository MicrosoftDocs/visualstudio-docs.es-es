---
title: IDebugBreakEvent2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1af6ce13de529fef5e16b3bc1be7053f0e1347b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735393"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
Esta interfaz indica al administrador de depuración de sesión (SDM) que se ha completado correctamente una interrupción asincrónica.

## <a name="syntax"></a>Sintaxis

```
IDebugBreakEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 La DE implementa esta interfaz para admitir saltos de usuario en un programa. El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaz debe implementarse en el mismo objeto que esta `IDebugEvent2` interfaz (el SDM utiliza [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la interfaz).

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 El SDM llama [a CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) cuando el usuario ha solicitado que el programa que se está depurando se detenga. Cuando el programa se ha pausado correctamente, la DE envía el `IDebugBreakEvent2` evento. Este evento se envía mediante el [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) función de devolución de llamada proporcionada por el SDM cuando se adjunta al programa que se está depurando.

## <a name="remarks"></a>Observaciones
 Por ejemplo, un usuario puede seleccionar el comando **Romper todo** en el menú **Depurar** para salir de un programa que ejecuta un bucle infinito. El SDM indica al programa que se detenga llamando a [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md). El DE `IDebugBreakEvent2` envía cuando el programa finalmente se detiene.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
