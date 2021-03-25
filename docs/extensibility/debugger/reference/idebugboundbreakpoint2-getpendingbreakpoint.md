---
description: Obtiene el punto de interrupción pendiente en el que se creó el punto de interrupción enlazado especificado.
title: 'IDebugBoundBreakpoint2:: GetPendingBreakpoint | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::GetPendingBreakpoint
helpviewer_keywords:
- IDebugBoundBreakpoint2::GetPendingBreakpoint method
- GetPendingBreakpoint method
ms.assetid: 22f94f81-f8d9-46de-96e9-fae6f3c24903
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 15b053515268c16bfacdeee08e40390950542e38
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095841"
---
# <a name="idebugboundbreakpoint2getpendingbreakpoint"></a>IDebugBoundBreakpoint2::GetPendingBreakpoint
Obtiene el punto de interrupción pendiente en el que se creó el punto de interrupción enlazado especificado.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetPendingBreakpoint( 
    IDebugPendingBreakpoint2** ppPendingBreakpoint
);
```

```csharp
int GetPendingBreakpoint( 
    out IDebugPendingBreakpoint2 ppPendingBreakpoint
);
```

## <a name="parameters"></a>Parámetros
`ppPendingBreakpoint`\
enuncia Devuelve el objeto [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) que representa el punto de interrupción pendiente que se usó para crear este punto de interrupción enlazado.

## <a name="return-value"></a>Valor devuelto
Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
Un punto de interrupción pendiente puede considerarse como una colección de toda la información necesaria para enlazar un punto de interrupción al código que se puede aplicar a uno o varios programas.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra cómo implementar este método para un `CBoundBreakpoint` objeto simple que expone la interfaz [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) .

```
HRESULT CBoundBreakpoint::GetPendingBreakpoint(
    IDebugPendingBreakpoint2** ppPendingBreakpoint)
{
    HRESULT hr;

    // Check for valid IDebugPendingBreakpoint2 interface pointer.
    if (ppPendingBreakpoint)
    {
        // Be sure that the bound breakpoint has not been deleted. If
        // deleted, then return hr = E_BP_DELETED.
        if (m_state != BPS_DELETED)
        {
            // Query for the IDebugPendingBreakpoint2 interface.
            hr = m_pPendingBP->QueryInterface(IID_IDebugPendingBreakpoint2,
                                              (void**)ppPendingBreakpoint);
        }
        else
        {
            hr = E_BP_DELETED;
        }
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>Consulte también
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
