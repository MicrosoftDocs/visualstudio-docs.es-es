---
title: IDebugProgramNode2::Attach_V7 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e77acd4091abd7da5c9d302fb4c4dd6eb66af379
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122995"
---
# <a name="idebugprogramnode2attachv7"></a>IDebugProgramNode2::Attach_V7

> [!Note]
> EN DESUSO. NO UTILICE.

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

#### <a name="parameters"></a>Parámetros

`pMDMProgram` [in] El [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaz que representa el programa que se va a conectar a.

 `pCallback` [in] El [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) interfaz que se usará para enviar eventos de depuración para el SDM.

 `dwReason` [in] Un valor de la [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) enumeración que especifica la razón para adjuntar.

## <a name="return-value"></a>Valor devuelto

Siempre debe devolver una implementación `E_NOTIMPL`.

## <a name="remarks"></a>Comentarios

> [!WARNING]
> A partir de Visual Studio 2005, este método ya no se utiliza y siempre debe devolver `E_NOTIMPL`. Consulte la [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) interfaz sobre un enfoque alternativo si el nodo de programa necesita indicar no se puede adjuntar a o si el nodo de programa simplemente es establecer el programa `GUID`. En caso contrario, implementar la [adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md) método.

## <a name="prior-to-visual-studio-2005"></a>Antes de Visual Studio 2005

Este método debe implementarse solo si la DE se ejecuta en el espacio de direcciones del programa que se está depurando. En caso contrario, este método debe devolver `S_FALSE`.

Cuando se llama a este método, debe enviar la DE la [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) objeto de evento, si no la ha enviado para esta instancia de la [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) interfaz, así como el [ IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) y [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) objetos de evento. El [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) , a continuación, se envía el objeto de evento si la `dwReason` parámetro es `ATTACH_REASON_LAUNCH`.

Debe llamar la DE la [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) método en el [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto proporcionado por el [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) eventos objeto y debe almacenar el GUID del programa en los datos de instancia para el `IDebugProgram2` objeto implementado por el DE.

## <a name="see-also"></a>Vea también

[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)  
[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)  
[Asociar](../../../extensibility/debugger/reference/idebugengine2-attach.md)  
[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)  
[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)  
[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)  
[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)  
[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)  
[ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)