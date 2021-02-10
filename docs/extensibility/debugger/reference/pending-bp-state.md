---
title: PENDING_BP_STATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE
helpviewer_keywords:
- PENDING_BP_STATE enumeration
ms.assetid: ac04ad72-fa92-4a15-ade2-0d0bbbadfc7f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 12a1dfd610c86966aa22444924098051c4b50d21
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934095"
---
# <a name="pending_bp_state"></a>PENDING_BP_STATE
Especifica el estado de un punto de interrupción pendiente (un punto de interrupción que todavía no se ha enlazado).

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_PENDING_BP_STATE { 
   PBPS_NONE     = 0x0000,
   PBPS_DELETED  = 0x0001,
   PBPS_DISABLED = 0x0002,
   PBPS_ENABLED  = 0x0003
};
typedef DWORD PENDING_BP_STATE;
```

```csharp
public enum enum_PENDING_BP_STATE { 
   PBPS_NONE     = 0x0000,
   PBPS_DELETED  = 0x0001,
   PBPS_DISABLED = 0x0002,
   PBPS_ENABLED  = 0x0003
};
```

## <a name="fields"></a>Campos
 `PBPS_NONE`\
 Marcador de posición para cero. Nunca se devuelve este valor.

 `PBPS_DELETED`\
 Indica que se ha eliminado el punto de interrupción pendiente.

 `PBPS_DISABLED`\
 Indica que el punto de interrupción pendiente está deshabilitado.

 `PBPS_ENABLED`\
 Indica que el punto de interrupción pendiente está habilitado.

## <a name="remarks"></a>Notas
 Use como `state` miembro de la estructura [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) .

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)
