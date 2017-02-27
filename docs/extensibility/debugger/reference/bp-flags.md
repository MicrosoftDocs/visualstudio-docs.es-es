---
title: "BP_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_FLAGS"
helpviewer_keywords: 
  - "Enumeración BP_FLAGS"
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Proporciona las marcas opcionales que se pueden utilizar para especificar información adicional al establecer un punto de interrupción.  
  
## Sintaxis  
  
```cpp#  
enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
typedef DWORD BP_FLAGS;  
```  
  
```c#  
public enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
```  
  
## Members  
 BP\_FLAG\_NONE  
 No especifica ningún indicador de punto de interrupción.  
  
 BP\_FLAG\_MAP\_DOCPOSITION  
 Especifica que el motor de depuración \(DE\) debe asignar el punto de interrupción mediante la posición del documento.  Esto sólo es aplicable a los puntos de interrupción establecidos en archivos de código fuente script\-orientados como páginas Active \(ASP\) Server.  
  
 \_STOP OF BP\_FLAG\_DO NO  
 Especifica que el punto de interrupción se debe procesar por el motor de depuración, pero que el motor de depuración no debe detener en última instancia allí \(es decir, un objeto de evento de [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) no debe enviarse\).  Este marcador está diseñado para usarse principalmente con los puntos.  
  
## Comentarios  
 Utilizado para el miembro de `dwFlags` de estructuras de [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) y de [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .  
  
 estos valores se pueden combinar con `OR`bit a bit.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)