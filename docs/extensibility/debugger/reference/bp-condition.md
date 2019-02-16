---
title: BP_CONDITION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_CONDITION
helpviewer_keywords:
- BP_CONDITION structure
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b7cc7231e218af855d3cc24eebe694b21ba1b40a
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315474"
---
# <a name="bpcondition"></a>BP_CONDITION
Describe las condiciones en las que se desencadena un punto de interrupción.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct _BP_CONDITION {
    IDebugThread2* pThread;
    BP_COND_STYLE  styleCondition;
    BSTR           bstrContext;
    BSTR           bstrCondition;
    UINT           nRadix;
} BP_CONDITION;
```

```csharp
public struct BP_CONDITION {
    public IDebugThread2 pThread;
    public uint          styleCondition;
    public string        bstrContext;
    public string        bstrCondition;
    public uint          nRadix;
};
```

## <a name="members"></a>Miembros
`pThread`  
El [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa el subproceso activo para la aplicación que contiene el punto de interrupción.

`styleCondition`  
Un valor de la [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md) enumeración que describe el estilo de esta condición de punto de interrupción.

`bstrContext`  
La ubicación del punto de interrupción.

`bstrCondition`  
La condición de activación del punto de interrupción.

`nRadix`  
Base que se utiliza para evaluar cualquier información numérica.

## <a name="remarks"></a>Comentarios
Esta estructura es un miembro de la [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) y [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) estructuras.

Esta estructura también se pasa como parámetro a la [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md) y [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md) métodos.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
[Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)  
[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)  
[BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)  
[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)  
[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)  
[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)  
[BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)
