---
title: Tareas de depuración | Microsoft Docs
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 070068853d962bdf9b209edb9410d33d46ccf853
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85903553"
---
# <a name="debug-tasks"></a>Tareas de depuración
Para depurar un programa, se debe iniciar y se le debe adjuntar un motor de depuración (DE), o bien el motor de depuración se debe adjuntar a un programa iniciado previamente. Después de adjuntarlo, el DE debe generar determinados eventos de inicio. Como respuesta, el paquete de depuración intenta enlazar los puntos de interrupción establecidos en el IDE. Cuando el programa llega a un punto de interrupción enlazado, se detiene y espera la entrada del usuario.

## <a name="in-this-section"></a>En esta sección
 [Problemas de seguridad](../../extensibility/debugger/security-issues.md) Se describen los pasos de seguridad necesarios para depurar un programa.

 [Inicio de un programa](../../extensibility/debugger/launching-a-program.md) Se proporcionan instrucciones paso a paso sobre cómo especificar un DE, que llama al sistema operativo para iniciar el programa.

 [Conexión directa a un programa](../../extensibility/debugger/attaching-directly-to-a-program.md) Se describe el proceso que se usa para depurar un programa en un proceso que ya está en ejecución.

 [Envío de eventos de inicio después de un inicio](../../extensibility/debugger/sending-startup-events-after-a-launch.md) Se enumeran los eventos que tienen lugar una vez que se ha adjuntado el motor de depuración al programa, hasta que el programa se encuentra en su punto de entrada principal y está listo para la depuración.

 [Control de la ejecución](../../extensibility/debugger/control-of-execution.md) Se explica cómo el motor de depuración suele enviar un evento de punto de entrada, de carga completa o de detención, en función de las circunstancias.

 [Enlace de puntos de interrupción](../../extensibility/debugger/binding-breakpoints.md) Si el usuario establece un punto de interrupción, se describe cómo el IDE formula la solicitud y solicita la sesión de depuración para crear el punto de interrupción.

 [Evaluación de expresiones](../../extensibility/debugger/evaluating-expressions.md) Se explica cómo se crean las expresiones y lo que ocurre cuando se evalúa una expresión.

 [Visualización de los datos](../../extensibility/debugger/visualizing-and-viewing-data.md) Se explica cómo se admiten los visualizadores de tipos y los visores personalizados en el evaluador de expresiones (EE).

## <a name="related-sections"></a>Secciones relacionadas
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md) Se describen los principales conceptos de la arquitectura de depuración.

 [Componentes del depurador](../../extensibility/debugger/debugger-components.md) Se proporciona información general sobre los componentes de depuración de Visual Studio, entre los que se incluyen el DE, EE y el controlador de símbolos (SH).

 [Contextos del depurador](../../extensibility/debugger/debugger-contexts.md) Se explica cómo funciona el motor de depuración simultáneamente dentro de los contextos de código, documentación y evaluación de expresiones. Para cada uno de los tres contextos, se describen la ubicación, la posición o la evaluación correspondientes.

## <a name="see-also"></a>Consulte también
 [Introducción](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
