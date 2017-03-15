---
title: "DISASSEMBLY_STREAM_SCOPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DISASSEMBLY_STREAM_SCOPE"
helpviewer_keywords: 
  - "Enumeración DISASSEMBLY_STREAM_SCOPE"
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# DISASSEMBLY_STREAM_SCOPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica el ámbito de la secuencia de desensamblado.  
  
## Sintaxis  
  
```cpp#  
enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
typedef DWORD DISASSEMBLY_STREAM_SCOPE;  
```  
  
```c#  
public enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
```  
  
## Members  
 DSS\_HUGE  
 Especifica que se desensambla el contexto del código generaría más la salida que un cliente quiera normalmente para recuperar en una única llamada.  
  
 DSS\_FUNCTION  
 Especifica que la función contenida por el contexto del código debe ser desensamblada.  Especifica que la secuencia de desensamblado representa una función, cuando se cambia por el método de [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) .  
  
 DSS\_MODULE  
 Cuando se cambia por el método de `IDebugDisassemblyStream2::GetScope` , especifica que la secuencia de desensamblado representa un módulo.  
  
 DSS\_ALL  
 Especifica el desensamblado del espacio de direcciones completo.  
  
## Comentarios  
 Pasado como argumento al método de [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) y devuelto por el método de [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) .  
  
 estos valores se pueden combinar con `OR`bit a bit.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)