---
description: Adjunta un motor de depuración (DE) a un programa o programas.
title: 'IDebugEngine2:: Attach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::Attach
helpviewer_keywords:
- IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a780ab04e693fd2868579efbf015aef25e0cca32
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160153"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
Adjunta un motor de depuración (DE) a un programa o programas. Llamado por el administrador de depuración de sesión (SDM) cuando el DE se ejecuta en proceso para el SDM.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Attach( 
   IDebugProgram2**      pProgram,
   IDebugProgramNode2**  rgpProgramNodes,
   DWORD                 celtPrograms,
   IDebugEventCallback2* pCallback,
   ATTACH_REASON         dwReason
);
```

```csharp
int Attach( 
   IDebugProgram2[]     pProgram,
   IDebugProgramNode2[] rgpProgramNodes,
   uint                 celtPrograms,
   IDebugEventCallback2 pCallback,
   Enum_ATTACH_REASON   dwReason
);
```

## <a name="parameters"></a>Parámetros
`pProgram`\
de Matriz de objetos [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que representan los programas a los que se va a adjuntar. Estos son los programas de puerto.

`rgpProgramNodes`\
de Matriz de objetos [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) que representan nodos de programa, uno para cada programa. Los nodos de programa de esta matriz representan los mismos programas que en `pProgram` . Los nodos DE programa se proporcionan para que el DE pueda identificar los programas a los que se va a adjuntar.

`celtPrograms`\
de Número de programas y/o nodos de programa en `pProgram` las `rgpProgramNodes` matrices y.

`pCallback`\
de El objeto [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) que se va a usar para enviar eventos de depuración al SDM.

`dwReason`\
de Un valor de la enumeración [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) que especifica el motivo por el que se adjuntan estos programas. Para obtener más información, vea la sección Comentarios.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Hay tres razones para asociar a un programa, como se indica a continuación:

- `ATTACH_REASON_LAUNCH` indica que el DE está adjuntando al programa porque el usuario inició el proceso que lo contiene.

- `ATTACH_REASON_USER` indica que el usuario ha solicitado explícitamente el DE para adjuntar a un programa (o el proceso que contiene un programa).

- `ATTACH_REASON_AUTO` indica que el DE está adjuntando a un programa determinado porque ya está depurando otros programas en un proceso determinado. También se denomina adjuntar automáticamente.

  Cuando se llama a este método, el DE necesita enviar estos eventos en orden:

1. [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (si aún no se ha enviado para una instancia determinada del motor de depuración)

2. [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

3. [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)

   Además, si el motivo de la asociación es `ATTACH_REASON_LAUNCH` , el de necesita enviar el evento [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) .

   Una vez que el obtiene el objeto [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) correspondiente al programa que se está depurando, se puede consultar para cualquier interfaz privada.

   Antes de llamar a los métodos de un nodo de programa en la matriz proporcionada por `pProgram` o `rgpProgramNodes` , la suplantación, si es necesario, debe estar habilitada en la `IDebugProgram2` interfaz que representa el nodo del programa. Sin embargo, normalmente, este paso no es necesario. Para obtener más información, vea [problemas de seguridad](../../../extensibility/debugger/security-issues.md).

## <a name="see-also"></a>Consulte también
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
- [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
- [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)
