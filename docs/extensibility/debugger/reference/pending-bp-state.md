---
title: PENDING_BP_STATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- PENDING_BP_STATE
helpviewer_keywords:
- PENDING_BP_STATE enumeration
ms.assetid: ac04ad72-fa92-4a15-ade2-0d0bbbadfc7f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff1315b2af395e8d809c2cbcbf9f642ac1c93557
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55029887"
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
  
## <a name="members"></a>Miembros  
 PBPS_NONE  
 Marcador de posición cero. Este valor no se devuelve nunca.  
  
 PBPS_DELETED  
 Indica que se ha eliminado el punto de interrupción pendiente.  
  
 PBPS_DISABLED  
 Indica que el punto de interrupción pendiente está deshabilitada.  
  
 PBPS_ENABLED  
 Indica que está habilitado el punto de interrupción pendiente.  
  
## <a name="remarks"></a>Comentarios  
 Usar como el `state` miembro de la [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) estructura.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)