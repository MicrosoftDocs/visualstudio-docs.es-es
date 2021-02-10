---
title: 'IDebugEventCallback2:: Event | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 54f53132f0a1f4769386874118d24f7e77a95f71
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933315"
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
Envía la notificación de eventos de depuración.

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
de Un objeto [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) que representa el motor de depuración (de) que está enviando este evento. Se requiere un DE para rellenar este parámetro.

`pProcess`\
de Objeto [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) que representa el proceso en el que se produce el evento. Este parámetro se rellena mediante el administrador de depuración de sesión (SDM). Un DE siempre pasa un valor null para este parámetro.

`pProgram`\
de Objeto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que representa el programa en el que se produce este evento. Para la mayoría de los eventos, este parámetro no es un valor nulo.

`pThread`\
de Objeto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa el subproceso en el que se produce este evento. Para detener eventos, este parámetro no puede ser un valor null, ya que el marco de pila se obtiene de este parámetro.

`pEvent`\
de Objeto [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) que representa el evento de depuración.

`riidEvent`\
de GUID que identifica la interfaz de eventos que se va a obtener del `pEvent` parámetro.

`dwAttrib`\
de Combinación de marcas de la enumeración [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) .

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
 Al llamar a este método, el `dwAttrib` parámetro debe coincidir con el valor devuelto desde el método [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) como se llama en el objeto de evento pasado en el `pEvent` parámetro.

 Todos los eventos de depuración se publican de forma asincrónica, independientemente de si un evento es asincrónico o no. Cuando un DE llama a este método, el valor devuelto no indica si se ha procesado el evento, solo si se ha recibido el evento. De hecho, en la mayoría de los casos, el evento no se ha procesado cuando este método devuelve.

## <a name="see-also"></a>Vea también
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
