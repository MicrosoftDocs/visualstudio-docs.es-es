---
title: IDebugBoundBreakpoint2::GetBreakpointResolution ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::GetBreakpointResolution
helpviewer_keywords:
- GetBreakpointResolution method
- IDebugBoundBreakpoint2::GetBreakpointResolution method
ms.assetid: 4479ac61-18a9-4a30-b213-9921c5af9a26
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab88009eb1c1bbbd59bbad2dfcbf62567db3941f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735577"
---
# <a name="idebugboundbreakpoint2getbreakpointresolution"></a>IDebugBoundBreakpoint2::GetBreakpointResolution
Obtiene la resolución de punto de interrupción que describe este punto de interrupción.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetBreakpointResolution( 
    IDebugBreakpointResolution2** ppBPResolution
);
```

```csharp
int GetBreakpointResolution( 
    out IDebugBreakpointResolution2 ppBPResolution
);
```

## <a name="parameters"></a>Parámetros
`ppBPResolution`\
[fuera] Devuelve el [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md) interfaz que representa uno de los siguientes:

- Objeto de resolución de punto de interrupción que describe la ubicación en el código donde se ha enlazado un punto de interrupción de código.

- La ubicación de datos donde se ha enlazado un punto de interrupción de datos.

## <a name="return-value"></a>Valor devuelto
Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. Devuelve `E_BP_DELETED` si el estado del objeto de `BPS_DELETED` punto de interrupción enlazado se establece en (parte de la [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) enumeración).

## <a name="remarks"></a>Observaciones
Llame a la [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md) método para determinar si la resolución de punto de interrupción es para código o datos.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra `CBoundBreakpoint` cómo implementar este método para un objeto simple que expone el [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) interfaz.

```
HRESULT CBoundBreakpoint::GetBreakpointResolution(
    IDebugBreakpointResolution2** ppBPResolution)
{
    HRESULT hr;

    if (ppBPResolution)
    {
        // Verify that the bound breakpoint has not been deleted. If
        // deleted, then return hr = E_BP_DELETED.
        if (m_state != BPS_DELETED)
        {
            // Query for the IDebugBreakpointResolution2 interface.
            hr = m_pBPRes->QueryInterface(IID_IDebugBreakpointResolution2,
                                          (void **)ppBPResolution);
            assert(hr == S_OK);
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

## <a name="see-also"></a>Vea también
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)
- [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)
