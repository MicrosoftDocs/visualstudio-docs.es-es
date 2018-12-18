---
title: BP_UNBOUND_REASON | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1e1e344ff5adb51d118370f81de10ba01c8950e1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49904224"
---
# <a name="bpunboundreason"></a>BP_UNBOUND_REASON
Proporciona la razón que no está enlazado a un punto de interrupción.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
typedef DWORD BP_UNBOUND_REASON;  
```  
  
```csharp  
public enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
```  
  
## <a name="members"></a>Miembros  
 BPUR_UNKNOWN  
 El motivo es desconocido.  
  
 BPUR_CODE_UNLOADED  
 El código que contiene el punto de interrupción se ha descargado.  
  
 BPUR_BREAKPOINT_REBIND  
 Se han vuelto a enlazar el punto de interrupción en una ubicación diferente. Esto puede ocurrir después de editar y continuar con las operaciones cuando se mueve el punto de interrupción o cuando el punto de interrupción se enlaza a un archivo con una ruta de acceso que ya no es válido.  
  
 BPUR_ BREAKPOINT_ERROR  
 El punto de interrupción se determina como error después de que está enlazado. Esto sucede a los puntos de interrupción administrados cuyas condiciones ya no son válidos.  
  
## <a name="remarks"></a>Comentarios  
 Devuelto por la [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)