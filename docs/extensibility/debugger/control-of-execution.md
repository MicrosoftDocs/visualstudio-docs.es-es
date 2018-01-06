---
title: "Control de ejecución | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a76b14f28bdb74345813931fc334f98090abd93c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="control-of-execution"></a>Control de ejecución
El motor de depuración (Alemania) normalmente envía a uno de los siguientes eventos como el último evento de inicio:  
  
-   El evento de punto de entrada, si se asocia a un programa iniciado recientemente  
  
-   El evento complete carga, si se asocia a un programa que ya se está ejecutando  
  
 Ambos estos eventos son eventos de parada, lo que significa que el DE espera una respuesta del usuario mediante el IDE. Para obtener más información, consulte [modos de funcionamiento](../../extensibility/debugger/operational-modes.md).  
  
## <a name="stopping-event"></a>Detención de evento  
 Cuando se envía un evento de detención para la sesión de depuración:  
  
1.  El programa y el subproceso que contienen el puntero de instrucción actual pueden obtenerse de la interfaz de eventos.  
  
2.  El IDE determina el archivo de código fuente actual y la posición, que muestra resaltado en el editor.  
  
3.  La sesión de depuración normalmente responde a este evento de detención primer mediante una llamada del programa **continuar** método.  
  
4.  A continuación, se ejecuta el programa hasta que encuentra una condición de detención, como encontrar un punto de interrupción, en el que la DE caso envía un evento de punto de interrupción a la sesión de depuración. El evento de punto de interrupción es un evento de detención y la DE nuevo espera una respuesta del usuario.  
  
5.  Si el usuario elige paso a paso, en o fuera de una función, el IDE le pide la sesión de depuración para llamar al programa `Step` método y pásele la unidad de paso (instrucción, instrucción o línea) y el tipo de paso, es decir, si se debe depurar paso a paso, en , o fuera de la función. Cuando se completa el paso, la DE envía un evento complete paso a la sesión de depuración, que es un evento de detención.  
  
     O bien  
  
     Si el usuario decide seguir ejecutando desde el puntero de instrucción actual, el IDE le pide la sesión de depuración para llamar al programa **Execute** método. El programa reanuda la ejecución hasta que encuentra la siguiente condición de detención.  
  
     O bien  
  
     Si la sesión de depuración que se va a omitir un evento determinado de detención, llama a la sesión de depuración del programa **continuar** método. Si el programa se ejecución paso a paso en, en o fuera de una función cuando encuentra la condición de detención, continúa el paso.  
  
 Mediante programación, cuando encuentra con la DE una condición de detención, envía los eventos de detención, como [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) o [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) en el Administrador de depuración de sesión (SDM) por medio de un [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) interfaz. Las fases DE la [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) y [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) interfaces que representan el programa y el subproceso que contiene el puntero de instrucción actual. Las llamadas SDM [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) para obtener el marco de pila superior y llamadas [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) para obtener el contexto del documento asociado a la instrucción actual puntero. Este contexto de documento suele ser un número de columna, líneas y nombre del archivo de código de origen. El IDE utiliza con frecuencia para resaltar el código fuente que contiene el puntero de instrucción actual.  
  
 El SDM normalmente responde a este evento de detención primer mediante una llamada a [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). A continuación, se ejecuta el programa hasta que encuentra una condición de detención, como encontrar un punto de interrupción, en el que envía el caso de la DE un [IDebugBreakpointEvent2 interfaz](../../extensibility/debugger/reference/idebugbreakpointevent2.md) para el SDM. El evento de punto de interrupción es un evento de detención y la DE nuevo espera una respuesta del usuario.  
  
 Si el usuario elige paso a paso, en o fuera de una función, el IDE solicitará el SDM para llamar a [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md), pasándole el [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) (instrucción, instrucción o línea) y la [ STEPKIND](../../extensibility/debugger/reference/stepkind.md), es decir, si se debe pasar a través de o fuera de la función. Cuando se completa el paso, se envía la DE un [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) interfaz para el SDM, que es un evento de detención.  
  
 Si el usuario decide seguir ejecutando desde el puntero de instrucción actual, el IDE le pide el SDM para llamar a [IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md). El programa reanuda la ejecución hasta que encuentra la siguiente condición de detención.  
  
 Si el paquete de depuración que se va a omitir un evento de detención determinado, el paquete de depuración llama el SDM, que llama [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Si el programa se ejecución paso a paso en, en o fuera de una función cuando encuentra la condición de detención, continúa el paso. Esto implica que el sistema mantiene un estado de ejecución paso a paso, para que sepa cómo continuar.  
  
 Las llamadas que realiza el SDM en `Step`, **Execute**, y **continuar** son asincrónica, lo que significa que el SDM espera la llamada a volver rápidamente. Si la DE envía el SDM ningún evento de detención en el mismo subproceso antes de `Step`, **Execute**, o **continuar** devuelve, se bloquea el SDM.  
  
## <a name="see-also"></a>Vea también  
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)