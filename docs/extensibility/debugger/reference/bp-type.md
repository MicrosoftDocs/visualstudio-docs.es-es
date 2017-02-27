---
title: "BP_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_TYPE"
helpviewer_keywords: 
  - "Enumeración BP_TYPE"
ms.assetid: ef07191e-7966-43ab-96fb-1a0b1db3115d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica si el punto de interrupción está en una ubicación del código, es una ubicación de los datos, o es otro tipo de punto de interrupción.  
  
## Sintaxis  
  
```cpp#  
enum enum_BP_TYPE {   
   BPT_NONE    = 0x0000,  
   BPT_CODE    = 0x0001,  
   BPT_DATA    = 0x0002,  
   BPT_SPECIAL = 0x0003  
};  
typedef DWORD BP_TYPE;  
```  
  
```c#  
public enum enum_BP_TYPE {   
   BPT_NONE    = 0x0000,  
   BPT_CODE    = 0x0001,  
   BPT_DATA    = 0x0002,  
   BPT_SPECIAL = 0x0003  
};  
```  
  
## Members  
 BPT\_NONE  
 No especifica ningún tipo de punto de interrupción.  
  
 BPT\_CODE  
 Especifica un punto de interrupción del código.  
  
 BPT\_DATA  
 Especifica un punto de interrupción de datos.  
  
 BPT\_SPECIAL  
 Especifica un punto de interrupción que no sea ni un código ni un tipo de datos.  Desusados y no debe usarse a este tipo.  
  
## Comentarios  
 pasado como parámetro a los métodos de [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md) y de [GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md) .  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)   
 [GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)