---
title: 'IDebugPortEvents2:: Event | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2::Event
helpviewer_keywords:
- IDebugPortEvents2::Event
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bcf8a827f09c1b8d0e83b92f7729635cbb0f7f18
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896180"
---
# <a name="idebugportevents2event"></a>IDebugPortEvents2::Event
Este método envía eventos que indican la creación y destrucción de procesos y programas en un puerto.

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
de Un objeto [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) que representa el servidor de depuración (existe uno para cada instancia de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ) en el que se produjo el evento.

`pPort`\
de Un objeto [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) que representa el puerto en el que se produjo el evento.

`pProcess`\
de Objeto [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) que representa el proceso en el que se produjo el evento.

`pProgram`\
de Objeto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que representa el programa en el que se produjo el evento.

`pEvent`\
de Un objeto [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) que identifica el evento. Los posibles eventos son los siguientes:

- [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)

- [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)

- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)

`riidEvent`\
de GUID del evento. Dado que el evento se convierte en [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) antes de llamar a este método, este identificador facilita la determinación del evento que se envía.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
