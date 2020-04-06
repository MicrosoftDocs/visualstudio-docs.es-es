---
title: IDebugEventCallback2::Evento ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0b60c09b21d531326e343dddd2f1cc69cfb0e5d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729897"
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
Envía una notificación de eventos de depuración.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Event( 
   IDebugEngine2*  pEngine,
   IDebugProcess2* pProcess,
   IDebugProgram2* pProgram,
   IDebugThread2*  pThread,
   IDebugEvent2*   pEvent,
   REFIID          riidEvent,
   DWORD           dwAttrib
);
```

```csharp
int Event( 
   IDebugEngine2  pEngine,
   IDebugProcess2 pProcess,
   IDebugProgram2 pProgram,
   IDebugThread2  pThread,
   IDebugEvent2   pEvent,
   ref Guid       riidEvent,
   uint           dwAttrib
);
```

## <a name="parameters"></a>Parámetros
`pEngine`\
[en] Un [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) objeto que representa el motor de depuración (DE) que envía este evento. Se requiere un DE para rellenar este parámetro.

`pProcess`\
[en] Un [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) objeto que representa el proceso en el que se produce el evento. Este parámetro es rellenado por el administrador de depuración de sesión (SDM). Un DE siempre pasa un valor nulo para este parámetro.

`pProgram`\
[en] Un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa el programa en el que se produce este evento. Para la mayoría de los eventos, este parámetro no es un valor nulo.

`pThread`\
[en] Un [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa el subproceso en el que se produce este evento. Para detener eventos, este parámetro no puede ser un valor nulo, ya que el marco de pila se obtiene de este parámetro.

`pEvent`\
[en] Un [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) objeto que representa el evento de depuración.

`riidEvent`\
[en] GUID que identifica qué interfaz `pEvent` de eventos se va a obtener del parámetro.

`dwAttrib`\
[en] Combinación de indicadores de la enumeración [EVENTATTRIBUTES.](../../../extensibility/debugger/reference/eventattributes.md)

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Al llamar a `dwAttrib` este método, el parámetro debe coincidir con el valor devuelto `pEvent` por el [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) método como se llama en el objeto de evento pasado en el parámetro.

 Todos los eventos de depuración se publican de forma asincrónica, independientemente de si un evento en sí es asincrónico o no. Cuando un DE llama a este método, el valor devuelto no indica si se ha procesado el evento, solo si se ha recibido el evento. De hecho, en la mayoría de las circunstancias, el evento no se ha procesado cuando se devuelve este método.

## <a name="see-also"></a>Vea también
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
