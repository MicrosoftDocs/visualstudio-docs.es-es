---
title: IDebugEngine2::Adjuntar á Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::Attach
helpviewer_keywords:
- IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 93890885dbbdfd3cc26984590955681487977200
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731208"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
Asocia un motor de depuración (DE) a un programa o programas. Llamado por el administrador del debug de la sesión (SDM) cuando el DE se está ejecutando en el proceso al SDM.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Attach( 
   IDebugProgram2**      pProgram,
   IDebugProgramNode2**  rgpProgramNodes,
   DWORD                 celtPrograms,
   IDebugEventCallback2* pCallback,
   ATTACH_REASON         dwReason
);
```

```csharp
int Attach( 
   IDebugProgram2[]     pProgram,
   IDebugProgramNode2[] rgpProgramNodes,
   uint                 celtPrograms,
   IDebugEventCallback2 pCallback,
   Enum_ATTACH_REASON   dwReason
);
```

## <a name="parameters"></a>Parámetros
`pProgram`\
[en] Matriz de [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objetos que representan programas que se van a adjuntar. Estos son programas portuarios.

`rgpProgramNodes`\
[en] Matriz de [objetos IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) que representan nodos de programa, uno para cada programa. Los nodos de programa de esta `pProgram`matriz representan los mismos programas que en . Los nodos del programa se dan para que el DE pueda identificar los programas a los que se va a adjuntar.

`celtPrograms`\
[en] Número de programas y/o `pProgram` nodos `rgpProgramNodes` de programa en los arreglos de discos.

`pCallback`\
[en] El [objeto IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) que se usará para enviar eventos de depuración al SDM.

`dwReason`\
[en] Valor de la [enumeración ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) que especifica el motivo de la asociación de estos programas. Para obtener más información, vea la sección Comentarios.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Hay tres razones para adjuntar a un programa, de la siguiente manera:

- `ATTACH_REASON_LAUNCH`indica que el DE se está adjuntando al programa porque el usuario inició el proceso que lo contiene.

- `ATTACH_REASON_USER`indica que el usuario ha solicitado explícitamente a la DE que se adjunte a un programa (o al proceso que contiene un programa).

- `ATTACH_REASON_AUTO`indica que el DE se está adjuntando a un programa en particular porque ya está depurando otros programas en un proceso determinado. Esto también se denomina auto-conexión.

  Cuando se llama a este método, el DE necesita enviar estos eventos en secuencia:

1. [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (si aún no se ha enviado para una instancia determinada del motor de depuración)

2. [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

3. [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)

   Además, si el motivo `ATTACH_REASON_LAUNCH`de la asociación es , la DE debe enviar el [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) eventos.

   Una vez que el DE obtiene el [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objeto correspondiente al programa que se está depurando, se puede consultar para cualquier interfaz privada.

   Antes de llamar a los métodos de `pProgram` `rgpProgramNodes`un nodo de programa en la matriz `IDebugProgram2` dada por o , suplantación, si es necesario, debe estar habilitado en la interfaz que representa el nodo de programa. Normalmente, sin embargo, este paso no es necesario. Para obtener más información, consulte Problemas de [seguridad](../../../extensibility/debugger/security-issues.md).

## <a name="see-also"></a>Vea también
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
- [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
- [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)
