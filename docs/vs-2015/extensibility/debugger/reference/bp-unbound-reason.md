---
title: BP_UNBOUND_REASON | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ddff6130e2243d10c00cefec160d057516d60932
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153279"
---
# <a name="bp_unbound_reason"></a>BP_UNBOUND_REASON
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Proporciona la razón por la que se desenlaza un punto de interrupción.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
typedef DWORD BP_UNBOUND_REASON;  
```  
  
```csharp  
public enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
```  
  
## <a name="members"></a>Miembros  
 BPUR_UNKNOWN  
 La razón es desconocida.  
  
 BPUR_CODE_UNLOADED  
 Se ha descargado el código que contiene el punto de interrupción.  
  
 BPUR_BREAKPOINT_REBIND  
 El punto de interrupción se ha reenlazado a una ubicación diferente. Esto puede ocurrir después de las operaciones de editar y continuar cuando se mueve el punto de interrupción, o cuando el punto de interrupción se enlaza a un archivo con una ruta de acceso que ya no es válida.  
  
 BPUR_ BREAKPOINT_ERROR  
 El punto de interrupción se determina como erróneo una vez enlazado. Esto sucede con los puntos de interrupción administrados cuyas condiciones ya no son válidas.  
  
## <a name="remarks"></a>Comentarios  
 Devuelto por el método [GetReason (](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) .  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)
