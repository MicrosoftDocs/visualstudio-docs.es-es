---
title: "Modos de funcionamiento | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "motores de depuración, modos"
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Modos de funcionamiento
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Hay tres modos en los que el IDE puede trabajar, como sigue:  
  
-   [Modo de diseño](#vsconoperationalmodesanchor1)  
  
-   [modo de ejecución](#vsconoperationalmodesanchor2)  
  
-   [Modo de interrupción](#vsconoperationalmodesanchor3)  
  
 Cómo las transiciones personalizadas del \(DE\) motor de depuración entre estos modos son una decisión de implementación que requiere estar familiarizado con los mecanismos de transición.  El OF puede o no puede implementar directamente estos modos.  Estos modos son realmente los modos de paquete de depuración que intercambian basándose en la acción del usuario o eventos de.  Por ejemplo, el cambio de modo de ejecución en modo de interrupción es instigada por un evento que detiene de.  La transición de la interrupción el modo de ejecución o el modo de paso es instigada por el usuario que realiza operaciones como paso o se ejecuta.  Para obtener más información acerca DE transitions, vea [Control de ejecución](../../extensibility/debugger/control-of-execution.md).  
  
##  <a name="vsconoperationalmodesanchor1"></a> Modo de diseño  
 El modo de diseño es el estado nonrunning de depuración de Visual Studio, mientras tanto puede establecer características de depuración de la aplicación.  
  
 Sólo algunas características de depuración se utilizan durante el modo de diseño.  Un desarrollador puede decidir establecer puntos de interrupción o para crear expresiones de inspección.  El OF nunca se carga o denominado mientras el IDE está en modo de diseño.  La interacción con el OF tiene lugar durante la ejecución y modos de interrupción sólo.  
  
##  <a name="vsconoperationalmodesanchor2"></a> modo de ejecución  
 El modo de ejecución se produce cuando se ejecuta un programa en una sesión de depuración en el IDE.  La aplicación ejecuta hasta la finalización, hasta que un punto de interrupción se alcanza, o hasta que se produce una excepción.  Cuando la aplicación ejecuta a la finalización, el OF transitions en modo de diseño.  Cuando se alcance un punto de interrupción o se produce una excepción, el OF transitions el modo de interrupción.  
  
##  <a name="vsconoperationalmodesanchor3"></a> Modo de interrupción  
 El modo de interrupción aparece cuando la ejecución del programa de depuración se suspende.  El modo de interrupción proporciona al desarrollador de software una instantánea de la aplicación en el momento de la interrupción y permite al programador analizar el estado de la aplicación y cambia cómo se ejecutará la aplicación.  El programador puede ver y editar código, para examinar o modificar datos, reiniciar la aplicación, finalizar la ejecución, o continuar la ejecución el mismo punto.  
  
 Escriba el modo de interrupción cuando el OF envía un evento que detiene sincrónico.  Los eventos que detienen sincrónicos, también denominados eventos de parada, notifican al administrador de depuración de la sesión \(SDM\) y el IDE que la aplicación que se depure ha detenido la ejecución de código.  Las interfaces de [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) y de [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) son ejemplos de eventos de parada.  
  
 Los eventos de parada son continuados por una llamada a uno de los métodos siguientes, que transición el depurador en modo de interrupción a ejecutar o el modo de paso:  
  
-   [Ejecutar](../../extensibility/debugger/reference/idebugprocess3-execute.md)  
  
-   [Paso](../../extensibility/debugger/reference/idebugprocess3-step.md)  
  
-   [Continuar](../../extensibility/debugger/reference/idebugprocess3-continue.md)  
  
###  <a name="vsconoperationalmodesanchor4"></a> Modo de paso  
 El modo de paso aparece cuando los pasos de programa a la línea siguiente de código, o en, en, o fuera de una función.  Un paso se ejecuta llamando al método [Paso](../../extensibility/debugger/reference/idebugprocess3-step.md).  Este método requiere s para `DWORD`que especifica las enumeraciones de [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) y de [STEPKIND](../../extensibility/debugger/reference/stepkind.md) como parámetros de entrada.  
  
 Cuando el programa los pasos correctamente a la línea siguiente de código o en una función, o se ejecuta en el cursor o a un punto de interrupción concreto, de las transiciones automáticamente a modo de interrupción.  
  
## Vea también  
 [Control de ejecución](../../extensibility/debugger/control-of-execution.md)