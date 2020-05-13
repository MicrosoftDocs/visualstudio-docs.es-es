---
title: IDebugEngine2::CreatePendingBreakpoint ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f88cae3610487b92fed0d8390d44c55d3f536c4b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731116"
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
Crea un punto de interrupción pendiente en el motor de depuración (DE).

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT CreatePendingBreakpoint(
    IDebugBreakpointRequest2*  pBPRequest,
    IDebugPendingBreakpoint2** ppPendingBP
);
```

```csharp
int CreatePendingBreakpoint(
    IDebugBreakpointRequest2     pBPRequest,
    out IDebugPendingBreakpoint2 ppPendingBP
);
```

## <a name="parameters"></a>Parámetros
`pBPRequest`\
[en] Un [objeto IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) que describe el punto de interrupción pendiente que se va a crear.

`ppPendingBP`\
[fuera] Devuelve un [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) objeto que representa el punto de interrupción pendiente.

## <a name="return-value"></a>Valor devuelto
Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. Normalmente `E_FAIL` devuelve `pBPRequest` si el parámetro no coincide con ningún `pBPRequest` idioma admitido por la DE de si el parámetro no es válido o está incompleto.

## <a name="remarks"></a>Observaciones
Un punto de interrupción pendiente es esencialmente una colección de toda la información necesaria para enlazar un punto de interrupción al código. El punto de interrupción pendiente devuelto desde este método no está enlazado al código hasta que el [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) se llama al método.

Para cada punto de interrupción pendiente que establece el usuario, el administrador de depuración de sesión (SDM) llama a este método en cada DE adjunto. Depende de la DE comprobar que el punto de interrupción es válido para los programas que se ejecutan en ese DE.

Cuando el usuario establece un punto de interrupción en una línea de código, la DE es libre de enlazar el punto de interrupción a la línea más cercana en el documento que corresponde a este código. Esto hace posible que el usuario establezca un punto de interrupción en la primera línea de una instrucción de varias líneas, pero enlazarlo en la última línea (donde todo el código se atribuye en la información de depuración).

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra `CProgram` cómo implementar este método para un objeto simple. La implementación de `IDebugEngine2::CreatePendingBreakpoint` la DE podría entonces reenviar todas las llamadas a esta implementación del método en cada programa.

```
HRESULT CProgram::CreatePendingBreakpoint(IDebugBreakpointRequest2* pBPRequest, IDebugPendingBreakpoint2** ppPendingBP)
{
    // Create and initialize the CPendingBreakpoint object.
    CComObject<CPendingBreakpoint> *pPending;
    CComObject<CPendingBreakpoint>::CreateInstance(&pPending);
    pPending->Initialize(pBPRequest, m_pInterp, m_pCallback, m_pEngine);
    return pPending->QueryInterface(ppPendingBP);
}
```

## <a name="see-also"></a>Vea también
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
