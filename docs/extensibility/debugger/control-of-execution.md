---
title: "Control de ejecuci&#243;n | Microsoft Docs"
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
  - "depurar [SDK de depuración], control de ejecución"
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Control de ejecuci&#243;n
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El motor de depuración \(DE\) envía normalmente uno de los siguientes eventos con el evento startup último:  
  
-   El evento de punto de entrada, si asocia un programa recién iniciadas  
  
-   La carga completa evento, si asocia un programa que se está ejecutando  
  
 Estos eventos son los eventos de parada, lo que significa que el OF espera una respuesta del usuario mediante el IDE.  Para obtener más información, vea [modos operativos](../../extensibility/debugger/operational-modes.md).  
  
## detener evento  
 Cuando un evento que detiene se envía a la sesión de depuración:  
  
1.  El programa y el subproceso que contienen el puntero de instrucción actual se pueden obtener de la interfaz de eventos.  
  
2.  El IDE determina el archivo y la posición actual del código fuente, que se muestra resaltado en el editor.  
  
3.  La sesión de depuración responden normalmente a este primer evento que detiene llamando al método de **Continuar** del programa.  
  
4.  El programa se ejecuta hasta que encuentra una condición que detiene, como la llegada a un punto de interrupción, en cuyo caso el OF envía un evento de punto de interrupción a la sesión de depuración.  El evento de punto de interrupción es un evento que detiene, y el OF espera de nuevo una respuesta del usuario.  
  
5.  Si el usuario decide entrar en, en, o una función, el IDE pide a la sesión de depuración llamar al método de `Step` de programa, pasando la unidad de paso \(instrucción, instrucción o, línea\) y la clase de paso\-que es, si entrar en, en, o la función.  Cuando se completa el paso, el OF envía un evento completed paso a la sesión de depuración, que es un evento que detiene.  
  
     O bien  
  
     Si el usuario decide seguir ejecutándose el puntero de instrucción actual, el IDE pide a la sesión de depuración llamar al método de **Ejecutar** del programa.  El programa reanuda la ejecución hasta que encuentra la condición que detiene siguiente.  
  
     O bien  
  
     Si la sesión de depuración es omitir un evento que detiene determinado, la sesión de depuración llama al método de **Continuar** del programa.  Si el programa caminaba en, en, o una función cuando encontró la condición que detenía, y continúa el paso.  
  
 Mediante programación, cuando el OF encuentra una condición que detiene, envía los eventos que detienen como [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) o [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) el administrador de depuración de sesión \(SDM\) mediante una interfaz de [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) .  El OF pasa las interfaces de [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) y de [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) que representan el programa y el subproceso que contienen el puntero de instrucción actual.  El SDM llama [IDebugThread2:: EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) para obtener el marco de pila superior y llama a [IDebugStackFrame2:: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) para obtener el contexto del documento asociado al puntero de instrucción actual.  Este contexto de documento es normalmente un nombre de archivo, una línea, y un número de columnas de código fuente.  Usa el IDE esto para resaltar el código fuente que contiene el puntero de instrucción actual.  
  
 El SDM responden normalmente a este primer evento que detiene llamando a [IDebugProgram2:: Continuar](../../extensibility/debugger/reference/idebugprogram2-continue.md).  El programa se ejecuta hasta que encuentra una condición que detiene, como la llegada a un punto de interrupción, en cuyo caso el OF envía [interfaz IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) al SDM.  El evento de punto de interrupción es un evento que detiene, y el OF espera de nuevo una respuesta del usuario.  
  
 Si el usuario decide entrar en, en, o una función, el IDE solicita que el SDM llamar [IDebugProgram2:: paso](../../extensibility/debugger/reference/idebugprogram2-step.md), pasándole [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) \(instrucción, instrucción o, línea\) y [STEPKIND](../../extensibility/debugger/reference/stepkind.md), es decir, si entrar en, en, o la función.  Cuando se completa el paso, el OF envía una interfaz de [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) al SDM, que es un evento que detiene.  
  
 Si el usuario decide seguir ejecutándose el puntero de instrucción actual, el IDE pide al SDM llame a [IDebugProgram2:: Ejecutar](../../extensibility/debugger/reference/idebugprogram2-execute.md).  El programa reanuda la ejecución hasta que encuentra la condición que detiene siguiente.  
  
 Si el paquete de depuración es omitir un evento que detiene determinado, el paquete de depuración llama al SDM, que llama a [IDebugProgram2:: Continuar](../../extensibility/debugger/reference/idebugprogram2-continue.md).  Si el programa caminaba en, en, o una función cuando encontró la condición que detenía, y continúa el paso.  Esto implica que el programa mantiene un estado de entrada, de modo que pueda continuar.  
  
 Las llamadas que el SDM crea a `Step`, **Ejecutar**, y **Continuar** es asincrónico, lo que significa que el SDM espera que vuelva la llamada rápidamente.  Si el OF envía el SDM un evento que se detiene en el mismo subproceso antes de `Step`, **Ejecutar**, o **Continuar** vuelve, el SDM no responder.  
  
## Vea también  
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)