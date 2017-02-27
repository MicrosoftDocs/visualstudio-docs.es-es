---
title: "BP_STATE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_STATE"
helpviewer_keywords: 
  - "Enumeración BP_STATE"
ms.assetid: 08aa6a3f-3e5f-4c83-8eca-7b7b5f8e208d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_STATE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica la existencia de un punto de interrupción enlazado y también se especifica si se habilita.  
  
## Sintaxis  
  
```cpp#  
enum enum_BP_STATE {   
   BPS_NONE     = 0x0000,  
   BPS_DELETED  = 0x0001,  
   BPS_DISABLED = 0x0002,  
   BPS_ENABLED  = 0x0003  
};  
typedef DWORD BP_STATE;  
```  
  
```c#  
public enum enum_BP_STATE {   
   BPS_NONE     = 0x0000,  
   BPS_DELETED  = 0x0001,  
   BPS_DISABLED = 0x0002,  
   BPS_ENABLED  = 0x0003  
};  
```  
  
## Members  
 BPS\_NONE  
 Especifica que no existe ningún punto de interrupción.  
  
 BPS\_DELETED  
 especifica que se ha eliminado el punto de interrupción.  
  
 BPS\_DISABLED  
 especifica que el punto de interrupción está deshabilitado.  
  
 BPS\_ENABLED  
 especifica que el punto de interrupción está habilitado.  
  
## Comentarios  
 Volver del método de [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md) .  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)