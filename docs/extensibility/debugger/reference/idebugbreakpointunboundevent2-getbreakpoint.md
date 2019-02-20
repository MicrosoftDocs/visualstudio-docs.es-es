---
title: IDebugBreakpointUnboundEvent2::GetBreakpoint | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBreakpointUnboundEvent2::GetBreakpoint
helpviewer_keywords:
- IDebugBreakpointUnboundEvent2::GetBreakpoint
ms.assetid: ad73a207-b778-4dc5-b645-5ec668a63333
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2519e919a9140d881b6323b0ecfc2aacc657306c
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "56412882"
---
# <a name="idebugbreakpointunboundevent2getbreakpoint"></a>IDebugBreakpointUnboundEvent2::GetBreakpoint
Obtiene el punto de interrupción se desvinculó.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetBreakpoint(
    IDebugBoundBreakpoint2** ppBP
);
```

```csharp
int GetBreakpoint(
    out IDebugBoundBreakpoint2 ppBP
);
```

#### <a name="parameters"></a>Parámetros
`ppBP`  
[out] Devuelve un [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) objeto que representa el punto de interrupción se desvinculó.

## <a name="return-value"></a>Valor devuelto
Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="example"></a>Ejemplo
El ejemplo siguiente muestra cómo implementar este método para un **CBreakpointUnboundDebugEventBase** objeto que expone el [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md) interfaz.

```cpp
STDMETHODIMP CBreakpointUnboundDebugEventBase::GetBreakpoint(
    IDebugBoundBreakpoint2 **ppbp)
{
    HRESULT hRes = E_FAIL;

    if ( ppbp )
    {
        if ( m_pbp )
        {
            IDebugBoundBreakpoint2 *pibp;

            hRes = m_pbp->QueryInterface(IID_IDebugBoundBreakpoint2, (void **) & pibp);

            if ( S_OK == hRes )
                *ppbp = pibp;
        }
        else
            hRes = E_FAIL;
    }
    else
        hRes = E_INVALIDARG;

    return ( hRes );
}
```

## <a name="see-also"></a>Vea también
[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)  
[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
