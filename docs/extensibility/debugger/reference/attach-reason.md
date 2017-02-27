---
title: "ATTACH_REASON | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATTACH_REASON"
helpviewer_keywords: 
  - "Enumeración ATTACH_REASON"
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# ATTACH_REASON
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica la razón del motor \(DE\) de depuración para asociar un nodo del programa.  
  
## Sintaxis  
  
```cpp#  
enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
typedef DWORD ATTACH_REASON;  
```  
  
```c#  
public enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
```  
  
## Members  
 ATTACH\_REASON\_AUTO  
 Asociar porque el proceso ya se encuentra en modo de depuración.  
  
 ATTACH\_REASON\_LAUNCH  
 Asociar porque se ha iniciará el proceso.  
  
 ATTACH\_REASON\_USER  
 Asociar debido a una solicitud de usuario.  
  
## Comentarios  
 estos valores se utilizan como parámetro a los métodos de [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) y de [Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md) .  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)