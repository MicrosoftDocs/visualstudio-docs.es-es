---
title: Depurar tareas | Microsoft Docs
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
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903553"
---
# <a name="debug-tasks"></a>Tareas de depuración
Para depurar un programa, debe iniciarse y se debe adjuntar un motor de depuración (DE), o bien se debe adjuntar a un programa iniciado previamente. Una vez conectado, el DE debe generar determinados eventos DE Inicio. En respuesta, el paquete de depuración intenta enlazar los puntos de interrupción establecidos en el IDE. Cuando el programa llega a un punto de interrupción enlazado, se detiene y espera la entrada del usuario.

## <a name="in-this-section"></a>En esta sección
 [Problemas de seguridad](../../extensibility/debugger/security-issues.md) Describe los pasos de seguridad necesarios para depurar un programa.

 [Iniciar un programa](../../extensibility/debugger/launching-a-program.md) Proporciona instrucciones paso a paso sobre cómo especificar un DE, que llama al sistema operativo para iniciar el programa.

 [Adjuntar directamente a un programa](../../extensibility/debugger/attaching-directly-to-a-program.md) Describe el proceso que se usa para depurar un programa en un proceso que ya se está ejecutando.

 [Enviar eventos de inicio después de un inicio](../../extensibility/debugger/sending-startup-events-after-a-launch.md) Enumera los eventos que tienen lugar una vez que el DE se adjunta al programa, hasta que el programa se encuentra en su punto de entrada principal y está listo para la depuración.

 [Control de la ejecución](../../extensibility/debugger/control-of-execution.md) Explica cómo el DE suele enviar un evento de punto de entrada, un evento de carga completa o un evento de detención, en función de las circunstancias.

 [Enlazar puntos de interrupción](../../extensibility/debugger/binding-breakpoints.md) Describe cómo, si el usuario establece un punto de interrupción, el IDE formula la solicitud y solicita la sesión de depuración para crear el punto de interrupción.

 [Evaluar expresiones](../../extensibility/debugger/evaluating-expressions.md) Explica cómo se crean las expresiones y lo que ocurre cuando se evalúa una expresión.

 Visualizar [y ver datos](../../extensibility/debugger/visualizing-and-viewing-data.md) Explica cómo el evaluador de expresiones (EE) admite visualizadores de tipos y visores personalizados.

## <a name="related-sections"></a>Secciones relacionadas
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md) Describe los conceptos principales de la arquitectura de depuración.

 [Componentes del depurador](../../extensibility/debugger/debugger-components.md) Proporciona información general sobre los componentes de depuración de Visual Studio, entre los que se incluyen el DE, el y el controlador DE símbolos (SH).

 [Contextos del depurador](../../extensibility/debugger/debugger-contexts.md) Explica cómo funciona simultáneamente dentro de los contextos de código, documentación y evaluación de expresiones. Describe, para cada uno de los tres contextos, la ubicación, la posición o la evaluación relevantes para él.

## <a name="see-also"></a>Vea también
 [Introducción](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
