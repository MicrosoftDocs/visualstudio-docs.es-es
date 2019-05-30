---
title: IDebugEngine2::Attach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::Attach
helpviewer_keywords:
- IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bc70b27793e722db4a07107d419b383a76207322
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330163"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
Asocia un motor de depuración (DE) a un programa o programas. Llamado por el Administrador de depuración de la sesión (SDM) cuando la DE se está ejecutando en proceso en el SDM.

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
[in] Una matriz de [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objetos que representan los programas que se adjuntará a. Se trata de programas de puerto.

`rgpProgramNodes`\
[in] Una matriz de [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objetos que representan nodos de programa, uno para cada programa. Los nodos de programa en esta matriz representan los mismos programas como en `pProgram`. Los nodos de programa se proporcionan para que la DE pueda identificar los programas para adjuntar a.

`celtPrograms`\
[in] Número de programas o nodos de programa en el `pProgram` y `rgpProgramNodes` matrices.

`pCallback`\
[in] El [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objeto que se usará para enviar eventos de depuración para el SDM.

`dwReason`\
[in] Un valor de la [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) enumeración que especifica la razón para asociar estos programas. Para obtener más información, vea la sección Comentarios.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Existen tres razones para adjuntar a un programa, como sigue:

- `ATTACH_REASON_LAUNCH` indica que la DE está asociando al programa porque el usuario inicia el proceso que lo contiene.

- `ATTACH_REASON_USER` indica que el usuario ha solicitado explícitamente la DE para adjuntar a un programa (o el proceso que contiene un programa).

- `ATTACH_REASON_AUTO` indica que la DE consiste en conectar a un determinado programa porque ya se está depurando otros programas en un proceso determinado. Esto también se denomina asociación automática.

  Cuando se llama a este método, la DE necesita enviar estos eventos en secuencia:

1. [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (si aún no ya se ha enviado para una instancia determinada del motor de depuración)

2. [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

3. [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)

   Además, si es la razón para adjuntar `ATTACH_REASON_LAUNCH`, debe enviar la DE la [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) eventos.

   Una vez que el obtiene DE la [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objeto correspondiente al programa que se está depurando, se puede consultar para cualquier interfaz privada.

   Antes de llamar a los métodos de un nodo de programa en la matriz proporcionada por `pProgram` o `rgpProgramNodes`, suplantación, si es necesario, debe estar habilitada en el `IDebugProgram2` interfaz que representa el nodo del programa. Normalmente, sin embargo, este paso no es necesario. Para obtener más información, consulte [problemas de seguridad](../../../extensibility/debugger/security-issues.md).

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