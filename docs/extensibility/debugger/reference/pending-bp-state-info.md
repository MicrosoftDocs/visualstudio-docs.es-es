---
description: Contiene información sobre el estado de un punto de interrupción que está listo para enlazarse a una ubicación del código.
title: PENDING_BP_STATE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE_INFO
helpviewer_keywords:
- PENDING_BP_STATE_INFO structure
ms.assetid: 4d73ceff-43f9-4e95-8dba-88e1fab2def3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a4da8892239740c65e1fcbbe618fa1ea76183e96
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079688"
---
# <a name="pending_bp_state_info"></a>PENDING_BP_STATE_INFO
Contiene información sobre el estado de un punto de interrupción que está listo para enlazarse a una ubicación del código.

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
 Un valor de la enumeración [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md) que especifica el estado del punto de interrupción pendiente.

 `flags`\
 Combinación de marcas de la enumeración [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md) que especifica si el punto de interrupción está virtualizado.

## <a name="remarks"></a>Observaciones
 Esta estructura se pasa al método [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md) donde se rellena.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)
- [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)
- [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)
