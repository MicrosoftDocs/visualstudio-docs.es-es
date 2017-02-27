---
title: "IDebugExceptionEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExceptionEvent2"
helpviewer_keywords: 
  - "Interfaz IDebugExceptionEvent2"
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExceptionEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

El motor de depuración \(DE\) envía esta interfaz al administrador \(SDM\) de depuración de la sesión cuando se produce una excepción en el programa que se está ejecutando actualmente.  
  
## Sintaxis  
  
```  
IDebugExceptionEvent2 : IUnknown  
```  
  
## Notas para los implementadores  
 El OF implementa esta interfaz para indicar que se ha producido una excepción en el programa que se depura.  la interfaz de [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) se debe implementar en el mismo objeto que esta interfaz.  El SDM utiliza [QueryInterface](/visual-cpp/atl/queryinterface) para tener acceso a la interfaz de `IDebugEvent2` .  
  
## Notas para los llamadores  
 El OF crea y envía este objeto event para señalar una excepción.  El evento se envía mediante la función de devolución de llamada de [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) proporcionada por el SDM cuando adjuntó el programa que se depura.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugExceptionEvent2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|Recopila información detallada sobre la excepción que desencadenó este evento.|  
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Obtiene una descripción legible de la excepción que desencadenó este evento.|  
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Determina si el motor de depuración \(DE\) admite la opción de pasar esta excepción al programa que se está depurando cuando la ejecución se reanuda.|  
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Especifica si la excepción se debe pasar al programa que se está depurando cuando la ejecución se reanuda, o si se descarta la excepción.|  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Comentarios  
 Antes de enviar el evento, las comprobaciones de para ver si este evento de excepción se ha señalado una oportunidad o una excepción de segunda oportunidad por una llamada anterior a [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md).  Si se ha señalado sea una excepción de primera oportunidad, el evento de `IDebugExceptionEvent2` se envía al SDM.  Si no, el OF da a la aplicación la oportunidad de controlar la excepción.  Si no se proporciona ningún controlador de excepciones, y si la excepción se ha designado como una excepción de segunda mano, el evento de `IDebugExceptionEvent2` se envía al SDM.  Si no, el OF reanuda la ejecución del programa, y el sistema operativo o el tiempo de ejecución controla la excepción.  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)