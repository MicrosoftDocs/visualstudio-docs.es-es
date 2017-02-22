---
title: "BP_UNBOUND_REASON | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_UNBOUND_REASON"
helpviewer_keywords: 
  - "Enumeración BP_UNBOUND_REASON"
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_UNBOUND_REASON
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Proporciona la razón que un punto de interrupción era independiente.  
  
## Sintaxis  
  
```cpp#  
enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
typedef DWORD BP_UNBOUND_REASON;  
```  
  
```c#  
public enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
```  
  
## Members  
 BPUR\_UNKNOWN  
 la razón es desconocida.  
  
 BPUR\_CODE\_UNLOADED  
 se ha descargado el código que contiene el punto de interrupción.  
  
 BPUR\_BREAKPOINT\_REBIND  
 el punto de interrupción se ha reencuadernado a una ubicación diferente.  Esto puede ocurrir después de operaciones de editar y continuar cuando el punto de interrupción se mueve, o cuando el punto de interrupción se enlaza a un archivo con una ruta que ya no es válida.  
  
 BPUR\_ BREAKPOINT\_ERROR  
 el punto de interrupción se determina para estar en error después de que se enlace.  Esto pasa a los puntos de interrupción administrados cuyas condiciones ya no son válidas.  
  
## Comentarios  
 Devuelto por el método de [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) .  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)