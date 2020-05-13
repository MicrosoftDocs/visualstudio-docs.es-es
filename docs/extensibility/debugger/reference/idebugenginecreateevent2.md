---
title: IDebugEngineCreateEvent2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineCreateEvent2
helpviewer_keywords:
- IDebugEngineCreateEvent2 interface
ms.assetid: 37c0a841-1c8d-4802-a990-36b54bca3ef7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 41a964f1e08fc2e88ac9a1d211e4b3e36b32c5b8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730602"
---
# <a name="idebugenginecreateevent2"></a>IDebugEngineCreateEvent2
El motor de depuración (DE) envía esta interfaz al administrador de depuración de sesión (SDM) cuando se crea una instancia del DE.

## <a name="syntax"></a>Sintaxis

```
IDebugEngineCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El DE implementa esta interfaz como parte de sus operaciones normales. El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaz debe implementarse en el mismo objeto `QueryInterface` que esta `IDebugEvent2` interfaz (el SDM utiliza el método para tener acceso a la interfaz).

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 La DE crea y envía este objeto de evento cuando se ha creado una instancia de DE. El evento se envía mediante la función de devolución de llamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) proporcionada por el SDM cuando se adjunta al programa que se está depurando.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IDebugEngineCreateEvent2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)|Recupera el objeto que representa el motor de depuración (DE) recién creado.|

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
