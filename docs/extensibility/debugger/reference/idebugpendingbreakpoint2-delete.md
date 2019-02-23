---
title: IDebugPendingBreakpoint2::Delete | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::Delete
helpviewer_keywords:
- IDebugPendingBreakpoint2::Delete method
- Delete method
ms.assetid: 4cb5ed81-6f0c-41ce-a770-5adb6b4bf5d9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ae9b35ba47b08acd2623a3d28c9e634b1ffaa76
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56694132"
---
# <a name="idebugpendingbreakpoint2delete"></a>IDebugPendingBreakpoint2::Delete
Elimina este punto de interrupción pendiente y todos los puntos de interrupción enlazados a partir de él.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Delete(
    void
);
```

```csharp
int Delete();
```

## <a name="return-value"></a>Valor devuelto
Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. Devuelve `E_BP_DELETED` si se ha eliminado el punto de interrupción.

## <a name="example"></a>Ejemplo
El ejemplo siguiente muestra cómo implementar este método para una sencilla `CPendingBreakpoint` objeto que implementa el [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interfaz.

```cpp
HRESULT CPendingBreakpoint::Delete(void)
{
    HRESULT hr;

    // Verify that the pending breakpoint has not been deleted. If deleted,
    // then return hr = E_BP_DELETED.
    if (m_state.state != PBPS_DELETED)
    {
        // If the pending breakpoint has bound and has an associated bound
        // breakpoint, delete and release the bound breakpoint and set the
        // pointer to NULL.
        if (m_pBoundBP)
        {
            m_pBoundBP->Delete();
            m_pBoundBP->Release();
            m_pBoundBP = NULL;
        }
        // If the pending breakpoint did not bind and has an associated
        // error breakpoint, release the error breakpoint and set the
        // pointer to NULL.
        if (m_pErrorBP)
        {
            m_pErrorBP->Release();
            m_pErrorBP = NULL;
        }

        // Set the PENDING_BP_STATE in the PENDING_BP_STATE_INFO structure
        // to deleted.
        m_state.state = PBPS_DELETED;
    }
    else
    {
        hr = E_BP_DELETED;
    }

    return hr;
}
```

## <a name="see-also"></a>Vea también
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
