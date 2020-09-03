---
title: PENDING_BP_STATE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE
helpviewer_keywords:
- PENDING_BP_STATE enumeration
ms.assetid: ac04ad72-fa92-4a15-ade2-0d0bbbadfc7f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 15ac788bf81ce83c2658b8a88a68ac5281020373
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205080"
---
# <a name="pending_bp_state"></a>PENDING_BP_STATE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Especifica el estado de un punto de interrupción pendiente (un punto de interrupción que todavía no se ha enlazado).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 Marcador de posición para cero. Nunca se devuelve este valor.  
  
 PBPS_DELETED  
 Indica que se ha eliminado el punto de interrupción pendiente.  
  
 PBPS_DISABLED  
 Indica que el punto de interrupción pendiente está deshabilitado.  
  
 PBPS_ENABLED  
 Indica que el punto de interrupción pendiente está habilitado.  
  
## <a name="remarks"></a>Observaciones  
 Use como `state` miembro de la estructura [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) .  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)
