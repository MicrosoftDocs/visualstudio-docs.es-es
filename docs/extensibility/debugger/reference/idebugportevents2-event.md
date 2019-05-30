---
title: IDebugPortEvents2::Event | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2::Event
helpviewer_keywords:
- IDebugPortEvents2::Event
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6ede9055f97a796e4e007914f68e370d4ff81420
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326761"
---
# <a name="idebugportevents2event"></a>IDebugPortEvents2::Event
Este método envía los eventos que indican la creación y destrucción de procesos y programas en un puerto.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Event(
   IDebugCoreServer2* pServer,
   IDebugPort2*       pPort,
   IDebugProcess2*    pProcess,
   IDebugProgram2*    pProgram,
   IDebugEvent2*      pEvent,
   REFIID             riidEvent
);
```

```csharp
int Event(
   IDebugCoreServer2 pServer,
   IDebugPort2       pPort,
   IDebugProcess2    pProcess,
   IDebugProgram2    pProgram,
   IDebugEvent2      pEvent,
   ref Guid          riidEvent
);
```

## <a name="parameters"></a>Parámetros
`pMachine`\
[in] Un [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) objeto que representa el servidor de depuración (hay uno para cada instancia de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]) en que se ha producido el evento.

`pPort`\
[in] Un [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) objeto que representa el puerto en el que se produjo el evento.

`pProcess`\
[in] Un [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) objeto que representa el proceso en el que se produjo el evento.

`pProgram`\
[in] Un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa el programa en el que se produjo el evento.

`pEvent`\
[in] Un [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) objeto que identifica el evento. Los posibles eventos son los siguientes:

- [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)

- [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)

- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)

`riidEvent`\
[in] El GUID del evento. Dado que el evento se convierte en [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) antes de llamar a este método, este identificador facilita determinar qué eventos se envían.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)