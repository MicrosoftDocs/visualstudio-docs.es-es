---
title: PENDING_BP_STATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE
helpviewer_keywords:
- PENDING_BP_STATE enumeration
ms.assetid: ac04ad72-fa92-4a15-ade2-0d0bbbadfc7f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6707c09e409e2a04d7afec0322b575a70cea33cf
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349872"
---
# <a name="pendingbpstate"></a>PENDING_BP_STATE
Especifica el estado de un punto de interrupción pendiente (un punto de interrupción que aún no se ha enlazado).

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_PENDING_BP_STATE { 
   PBPS_NONE     = 0x0000,
   PBPS_DELETED  = 0x0001,
   PBPS_DISABLED = 0x0002,
   PBPS_ENABLED  = 0x0003
};
typedef DWORD PENDING_BP_STATE;
```

```csharp
public enum enum_PENDING_BP_STATE { 
   PBPS_NONE     = 0x0000,
   PBPS_DELETED  = 0x0001,
   PBPS_DISABLED = 0x0002,
   PBPS_ENABLED  = 0x0003
};
```

## <a name="fields"></a>Campos
 `PBPS_NONE`\
 Marcador de posición cero. Este valor no se devuelve nunca.

 `PBPS_DELETED`\
 Indica que se ha eliminado el punto de interrupción pendiente.

 `PBPS_DISABLED`\
 Indica que el punto de interrupción pendiente está deshabilitada.

 `PBPS_ENABLED`\
 Indica que está habilitado el punto de interrupción pendiente.

## <a name="remarks"></a>Comentarios
 Usar como el `state` miembro de la [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) estructura.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)