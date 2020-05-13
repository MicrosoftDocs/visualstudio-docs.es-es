---
title: IDebugBreakpointErrorEvent2::GetErrorBreakpoint ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointErrorEvent2::GetErrorBreakpoint
helpviewer_keywords:
- IDebugBreakpointErrorEvent2::GetErrorBreakpoint
ms.assetid: e5acfd19-ac17-47f3-a31a-b2aa8baca36d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe22f18d4574ffde48cea975bff8d8f5801ca465
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735073"
---
# <a name="idebugbreakpointerrorevent2geterrorbreakpoint"></a>IDebugBreakpointErrorEvent2::GetErrorBreakpoint
Obtiene un [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) objeto que describe el motivo por el que no se enlaza un punto de interrupción.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetErrorBreakpoint( 
    IDebugErrorBreakpoint2** ppErrorBP
);
```

```csharp
int GetErrorBreakpoint( 
    out IDebugErrorBreakpoint2 ppErrorBP
);
```

## <a name="parameters"></a>Parámetros
`ppErrorBP`\
[fuera] Devuelve un [objeto IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) que describe la advertencia o el error.

## <a name="return-value"></a>Valor devuelto
Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
Después `IDebugErrorBreakpoint2` de obtener la interfaz, llame a la [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) método para obtener un [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md) objeto. A continuación, el [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) método se puede usar para determinar una ubicación no válida, una expresión no válida o razones por las que el punto de interrupción pendiente no se ha enlazado, como el código no cargado todavía, y así sucesivamente.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra cómo implementar este método para un **CBreakpointSetDebugEventBase** objeto que expone el [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) interfaz.

```cpp
STDMETHODIMP CBreakpointErrorDebugEventBase::GetErrorBreakpoint(
    IDebugErrorBreakpoint2 **ppbp)
{
    HRESULT hRes = E_FAIL;

    if ( ppbp )
    {
        if ( m_pError )
        {
            *ppbp = m_pError;

            m_pError->AddRef();

            hRes = S_OK;
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
- [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)
- [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
