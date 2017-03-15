---
title: "EVENTATTRIBUTES | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EVENTATTRIBUTES"
helpviewer_keywords: 
  - "Enumeración EVENTATTRIBUTES"
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# EVENTATTRIBUTES
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica los atributos del evento.  
  
## Sintaxis  
  
```cpp#  
enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
typedef DWORD EVENTATTRIBUTES;  
```  
  
```c#  
public enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
```  
  
## Members  
 EVENT\_ASYNCHRONOUS  
 Indica que el evento es asincrónico y ninguna respuesta al evento es necesario.  
  
 EVENT\_SYNCHRONOUS  
 indica que el evento es sincrónico; respuesta mediante [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md).  
  
 EVENT\_STOPPING  
 Indica que se trata de un evento que detiene.  Debe combinarse con `EVENT_ASYNCHRONOUS` o `EVENT_SYNCHRONOUS`.  
  
 EVENT\_ASYNC\_STOP  
 indica un evento que detiene asincrónico.  Actualmente no hay un evento.  Este mensaje es sólo marcador.  
  
 EVENT\_SYNCHRONIZATION\_STOP  
 indica un evento que detiene sincrónico \(una combinación de `EVENT_SYNCHRONOUS` y de `EVENT_STOPPING`\).  Este valor utiliza un motor de depuración \(DE\) cuando envía un evento que detiene.  la respuesta se hace mediante una llamada a [Ejecutar](../../../extensibility/debugger/reference/idebugprogram2-execute.md), a [Paso](../../../extensibility/debugger/reference/idebugprogram2-step.md), o a [Continuar](../../../extensibility/debugger/reference/idebugprogram2-continue.md).  
  
 EVENT\_IMMEDIATE  
 Indica un evento que se envía inmediatamente y sincrónicamente al IDE.  Este marcador se combina con otros marcadores como `EVENT_ASYNCHRONOUS`, `EVENT_SYNCHRONOUS`, o `EVENT_SYNC_STOP` para indicar el tipo de evento y el hecho de que el mecanismo de respuesta \(si existe\) se conoce.  
  
 EVENT\_EXPRESSION\_EVALUATION  
 El evento es el resultado de la evaluación de la expresión.  
  
## Comentarios  
 Estos valores se pasan en el parámetro de `dwAttrib` del método de [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) .  
  
 estos valores se pueden combinar con `OR`bit a bit.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)