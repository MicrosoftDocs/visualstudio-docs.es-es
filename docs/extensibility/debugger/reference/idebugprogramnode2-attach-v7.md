---
title: IDebugProgramNode2::Attach_V7 Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bdee5b224ae38c3474009aeaf26e783ebc5dd139
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722140"
---
# <a name="idebugprogramnode2attach_v7"></a>IDebugProgramNode2::Attach_V7

> [!Note]
> Obsoleto. NO USAR.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Attach_V7 (
   IDebugProgram2*       pMDMProgram,
   IDebugEventCallback2* pCallback,
   DWORD                 dwReason
);
```

```csharp
int Attach_V7 (
   IDebugProgram2       pMDMProgram,
   IDebugEventCallback2 pCallback,
   uint                 dwReason
);
```

## <a name="parameters"></a>Parámetros

`pMDMProgram`\
[en] El [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaz que representa el programa que se va a adjuntar a.

`pCallback`\
[en] El [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) interfaz que se usará para enviar eventos de depuración al SDM.

`dwReason`\
[en] Valor de la [enumeración ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) que especifica el motivo de la asociación.

## <a name="return-value"></a>Valor devuelto

Una implementación `E_NOTIMPL`siempre debe devolver .

## <a name="remarks"></a>Observaciones

> [!WARNING]
> A partir de Visual Studio 2005, este método `E_NOTIMPL`ya no se usa y siempre debe devolver . Consulte la interfaz [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) para obtener un enfoque alternativo si el nodo del programa debe indicar `GUID`que no se puede asociar o si el nodo de programa simplemente está configurando el programa . De lo contrario, implemente el método [Attach.](../../../extensibility/debugger/reference/idebugengine2-attach.md)

## <a name="prior-to-visual-studio-2005"></a>Antes de Visual Studio 2005

Este método solo debe implementarse si la DE se ejecuta en el espacio de direcciones del programa que se está depurando. De lo contrario, `S_FALSE`este método debe devolver .

Cuando se llama a este método, el DE debe enviar el [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) objeto de evento, si aún no se ha enviado para esta instancia de la [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) interfaz, así como el [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) y [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) objetos de evento. A continuación, se envía el objeto de `dwReason` evento `ATTACH_REASON_LAUNCH` [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) si el parámetro es .

El DE debe llamar a la [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) método en el [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto proporcionado por el [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) `IDebugProgram2` objeto de evento y debe almacenar el GUID de ese programa en los datos de instancia para el objeto implementado por el DE.

## <a name="see-also"></a>Vea también

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
- [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)
- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
