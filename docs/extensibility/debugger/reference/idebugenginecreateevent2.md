---
description: El motor DE depuración (DE) envía esta interfaz al administrador de depuración de la sesión (SDM) cuando se crea una instancia de de.
title: IDebugEngineCreateEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineCreateEvent2
helpviewer_keywords:
- IDebugEngineCreateEvent2 interface
ms.assetid: 37c0a841-1c8d-4802-a990-36b54bca3ef7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6155324150b963a5fd26ccecc1244e0792f448bc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153656"
---
# <a name="idebugenginecreateevent2"></a>IDebugEngineCreateEvent2
El motor DE depuración (DE) envía esta interfaz al administrador de depuración de la sesión (SDM) cuando se crea una instancia de de.

## <a name="syntax"></a>Syntax

```
IDebugEngineCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El DE implementa esta interfaz como parte de sus operaciones normales. La interfaz [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) debe implementarse en el mismo objeto que esta interfaz (el SDM usa el `QueryInterface` método para tener acceso a la `IDebugEvent2` interfaz).

## <a name="notes-for-callers"></a>Notas para llamadores
 El DE crea y envía este objeto de evento cuando se ha creado una instancia DE. El evento se envía mediante la función de devolución de llamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) proporcionada por el SDM cuando se adjunta al programa que se está depurando.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugEngineCreateEvent2` .

|Método|Descripción|
|------------|-----------------|
|[GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)|Recupera el objeto que representa el motor DE depuración recién creado (DE).|

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
