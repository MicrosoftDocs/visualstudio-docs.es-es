---
title: "BP_FLAGS90 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BP_FLAGS90 (enumeración)"
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_FLAGS90
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Muestra los valores válidos para las marcas opcionales.  Las marcas opcionales permiten especificar información adicional cuando se establece un punto de interrupción.  esta enumeración extiende la enumeración de [BP\_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) .  
  
## Sintaxis  
  
```cpp#  
enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE               = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION    = 0x0001,  
   BP90_FLAG_DONT_STOP          = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
typedef DWORD BP_FLAGS90;  
```  
  
```c#  
public enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE                = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION     = 0x0001,  
   BP90_FLAG_DONT_STOP           = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
```  
  
#### Parámetros  
 BP90\_FLAG\_NONE  
 No especifica ningún indicador de punto de interrupción.  
  
 BP90\_FLAG\_MAP\_DOCPOSITION  
 Especifica que el motor de depuración \(DE\) debe asignar el punto de interrupción mediante la posición del documento.  Esto sólo es aplicable a los puntos de interrupción establecidos en archivos de código fuente script\-orientados como páginas Active \(ASP\) Server.  
  
 \_STOP OF BP90\_FLAG\_DO NO  
 Especifica que el punto de interrupción se debe procesar por el motor de depuración, pero que el motor de depuración no debe detener en última instancia allí; es decir, un objeto de evento de [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) no debe ser enviados.  Este marcador está diseñado para usarse principalmente con los puntos de seguimiento.  
  
 BP90\_FLAG\_TRACEPOINT\_CONTINUE  
 Utilizado por el motor de depuración nativo para determinar si el estado de entrada debe estar desactivada.  diferencia de BP90\_FLAG\_DONT\_STOP porque BP90\_FLAG\_DONT\_STOP no se establece si el punto de seguimiento ejecuta una macro.  
  
## Requisitos  
 encabezado: Msdbg90.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)