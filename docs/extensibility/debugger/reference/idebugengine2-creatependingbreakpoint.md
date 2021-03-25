---
description: Crea un punto de interrupción pendiente en el motor DE depuración (DE).
title: 'IDebugEngine2:: CreatePendingBreakpoint | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa06a4c88afecfebbd0b1258d7f1830dfdaad5ac
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105093878"
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
Crea un punto de interrupción pendiente en el motor DE depuración (DE).

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
de Objeto [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) que describe el punto de interrupción pendiente que se va a crear.

`ppPendingBP`\
enuncia Devuelve un objeto [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) que representa el punto de interrupción pendiente.

## <a name="return-value"></a>Valor devuelto
Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. Normalmente devuelve `E_FAIL` si el `pBPRequest` parámetro no coincide con ningún lenguaje compatible con el de de si el `pBPRequest` parámetro no es válido o está incompleto.

## <a name="remarks"></a>Observaciones
Un punto de interrupción pendiente es esencialmente una colección de toda la información necesaria para enlazar un punto de interrupción al código. El punto de interrupción pendiente devuelto por este método no está enlazado al código hasta que se llama al método [BIND](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) .

Para cada punto de interrupción pendiente que establece el usuario, el administrador de depuración de la sesión (SDM) llama a este método en cada asociado DE. Es el DE para comprobar que el punto de interrupción es válido para los programas que se ejecutan en ese DE.

Cuando el usuario establece un punto de interrupción en una línea de código, el DE es libre de enlazar el punto de interrupción a la línea más cercana del documento que corresponde a este código. Esto permite al usuario establecer un punto de interrupción en la primera línea de una instrucción de varias líneas, pero enlazarlo en la última línea (donde se atribuye todo el código en la información de depuración).

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra cómo implementar este método para un `CProgram` objeto simple. A continuación, la implementación de de `IDebugEngine2::CreatePendingBreakpoint` se puede reenviar todas las llamadas a esta implementación del método en cada programa.

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

## <a name="see-also"></a>Consulte también
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [Volver](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
