---
title: IDebugThreadNameChangedEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThreadNameChangedEvent2
helpviewer_keywords:
- IDebugThreadNameChangedEvent2
ms.assetid: 34c1652e-f019-48ba-8b26-ace20f8a158c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 169b26a10ffdaf7e6cdf490d83373950f92e769b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319867"
---
# <a name="idebugthreadnamechangedevent2"></a>IDebugThreadNameChangedEvent2
Esta interfaz se envía por el motor de depuración (DE) el Administrador de depuración de la sesión (SDM) cuando cambia el nombre de un subproceso en el programa que se está depurando.

## <a name="syntax"></a>Sintaxis

```
IDebugThreadNameChangedEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 La DE implementa esta interfaz para informar de que ha cambiado el nombre de un subproceso. El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaz debe implementarse en el mismo objeto que esta interfaz. Usa el SDM [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la `IDebugEvent2` interfaz.

## <a name="notes-for-callers"></a>Notas para los llamadores
 La DE crea y envía este objeto event para informar de que ha cambiado el nombre de un subproceso. El evento se envía mediante la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) función de devolución de llamada suministrada por el SDM cuando está conectado al programa que se está depurando.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)