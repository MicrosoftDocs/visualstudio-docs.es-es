---
title: BP_PASSCOUNT | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_PASSCOUNT
helpviewer_keywords:
- BP_PASSCOUNT structure
ms.assetid: 791ac175-b897-4c70-873e-240da7e0ac89
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d51e0fc895c104c1a18ef079c6784384e4cedbb4
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2019
ms.locfileid: "56316696"
---
# <a name="bppasscount"></a>BP_PASSCOUNT
Describe el número y las condiciones en el que se desencadena un punto de interrupción condicional.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct _BP_PASSCOUNT {
    DWORD              dwPassCount;
    BP_PASSCOUNT_STYLE stylePassCount;
} BP_PASSCOUNT;
```

```csharp
public struct BP_PASSCOUNT {
    public uint dwPassCount;
    public uint stylePassCount;
};
```

## <a name="members"></a>Miembros
`dwPassCount`  
El número de veces que se sitúe sobre el punto de interrupción antes de activar.

`stylePassCount`  
Un valor de la [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md) recuento de pasos de la enumeración que especifica el estilo del punto de interrupción.

## <a name="remarks"></a>Comentarios
Esta estructura es un miembro de la [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) estructura.

Esta estructura también se pasa como parámetro a la[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md) y[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md) métodos.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
[Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)  
[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)  
[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)  
[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)  
[BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md)
