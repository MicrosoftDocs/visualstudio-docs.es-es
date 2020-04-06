---
title: Control de ejecución ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e2d338c5470611a5eea0c6279404c4eaddebb2d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739079"
---
# <a name="control-of-execution"></a>Control de ejecución
El motor de depuración (DE) normalmente envía uno de los siguientes eventos como el último evento de inicio:

- El evento de punto de entrada, si se adjunta a un programa recién lanzado

- El evento load complete, si se adjunta a un programa que ya se está ejecutando

  Ambos eventos detienen eventos, lo que significa que el DE espera una respuesta del usuario mediante el IDE. Para obtener más información, consulte [Modos operativos](../../extensibility/debugger/operational-modes.md).

## <a name="stopping-event"></a>Detener el evento
 Cuando se envía un evento de detención a la sesión de depuración:

1. El programa y el subproceso que contienen el puntero de instrucción actual se pueden obtener desde la interfaz de eventos.

2. El IDE determina el archivo de código fuente actual y la posición, que se muestra como resaltado en el editor.

3. La sesión de depuración normalmente responde a este primer evento de detención llamando al método **Continue** del programa.

4. A continuación, el programa se ejecuta hasta que encuentra una condición de detención, como golpear un punto de interrupción. En ese caso, el DE envía un evento de punto de interrupción a la sesión de depuración. El evento de punto de interrupción es un evento de detención y el DE espera de nuevo una respuesta del usuario.

5. Si el usuario elige entrar, pasar o salir de una función, el IDE solicita `Step` a la sesión de depuración que llame al método del programa. A continuación, el IDE pasa la unidad de paso (instrucción, instrucción o línea) y el tipo de paso (ya sea para entrar, superar o salir de la función). Cuando se completa el paso, el DE envía un evento complete del paso a la sesión de depuración, que es un evento de detención.

    o bien

    Si el usuario elige continuar la ejecución desde el puntero de instrucción actual, el IDE solicita a la sesión de depuración que llame al método **Execute** del programa. El programa reanuda la ejecución hasta que encuentra la siguiente condición de detención.

    o bien

    Si la sesión de depuración debe omitir un evento de detención determinado, la sesión de depuración llama al método **Continue** del programa. Si el programa entraba, entraba o salía de una función cuando se encontraba con la condición de detención, continúa el paso.

   Mediante programación, cuando el DE encuentra una condición de detención, envía eventos de detención como [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) o [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) al administrador de depuración de sesión (SDM) mediante una [interfaz IDebugEventCallback2.](../../extensibility/debugger/reference/idebugeventcallback2.md) El DE pasa el [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) y [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) interfaces que representan el programa y el subproceso que contiene el puntero de instrucción actual. El SDM llama a [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) para obtener el marco de pila superior y llama a [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) para obtener el contexto de documento asociado con el puntero de instrucción actual. Este contexto de documento suele ser un nombre de archivo de código fuente, una línea y un número de columna. El IDE los usa para resaltar el código fuente que contiene el puntero de instrucción actual.

   El SDM normalmente responde a este primer evento de detención llamando a [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). A continuación, el programa se ejecuta hasta que encuentra una condición de detención, como golpear un punto de interrupción, en cuyo caso la DE envía una [interfaz IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) al SDM. El evento de punto de interrupción es un evento de detención y el DE espera de nuevo una respuesta del usuario.

   Si el usuario elige entrar, pasar o salir de una función, el IDE solicita al SDM que llame a [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md). A continuación, el IDE pasa [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) (instrucción, instrucción o línea) y [STEPKIND](../../extensibility/debugger/reference/stepkind.md), es decir, si se debe entrar, superar o salir de la función. Cuando se completa el paso, el DE envía un [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) interfaz al SDM, que es un evento de detención.

   Si el usuario decide continuar la ejecución desde el puntero de instrucción actual, el IDE pide al SDM que llame a [IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md). El programa reanuda la ejecución hasta que encuentra la siguiente condición de detención.

   Si el paquete de depuración debe omitir un evento de detención determinado, el paquete de depuración llama al SDM, que llama a [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Si el programa entraba, entraba o salía de una función cuando se encontraba con la condición de detención, continúa el paso. Esto implica que el programa mantiene un estado de paso a paso, para que sepa cómo continuar.

   Las llamadas que `Step`realiza el SDM a , **Execute**y **Continue** son asincrónicas, lo que significa que el SDM espera que la llamada vuelva rápidamente. Si el DE envía el SDM un evento `Step`de detención en el mismo subproceso antes de que , **Ejecutar**o **Continuar** devuelve, el SDM se bloquea.

## <a name="see-also"></a>Vea también
- [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)
