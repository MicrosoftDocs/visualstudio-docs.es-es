---
title: PENDING_BP_STATE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE_INFO
helpviewer_keywords:
- PENDING_BP_STATE_INFO structure
ms.assetid: 4d73ceff-43f9-4e95-8dba-88e1fab2def3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5d08e2ec34f153e984ea158eaca4ca282652e67e
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/09/2019
ms.locfileid: "65460893"
---
# <a name="pendingbpstateinfo"></a>PENDING_BP_STATE_INFO
Contiene información sobre el estado de un punto de interrupción que está listo para enlazar a una ubicación del código.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct _tagPENDING_BP_STATE_INFO { 
   PENDING_BP_STATE       state;
   PENDING_BP_STATE_FLAGS flags;
} PENDING_BP_STATE_INFO;
```

```csharp
public struct PENDING_BP_STATE_INFO { 
   public uint state;
   public uint flags;
};
```

## <a name="members"></a>Miembros
 `state`\
 Un valor de la [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md) enumeración que especifica el estado del punto de interrupción pendiente.

 `flags`\
 Una combinación de marcas de la [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md) enumeración que especifica si el punto de interrupción está virtualizado.

## <a name="remarks"></a>Comentarios
 Esta estructura se pasa a la [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md) método donde se rellena.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)
- [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)
- [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)