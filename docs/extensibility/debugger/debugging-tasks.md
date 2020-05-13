---
title: Tareas de depuración ( Debugging Tasks) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d41f53ab1392ea3c31908faf65a871fa100fbb3f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738958"
---
# <a name="debug-tasks"></a>Tareas de depuración
Para depurar un programa, debe iniciarse y debe adjuntarse un motor de depuración (DE) o, de lo contrario, el DE debe adjuntarse a un programa iniciado anteriormente. Una vez asociado, el DE debe generar ciertos eventos de inicio. En respuesta, el paquete de depuración intenta enlazar los puntos de interrupción establecidos en el IDE. Cuando el programa alcanza un punto de interrupción enlazado, se detiene y espera la entrada del usuario.

## <a name="in-this-section"></a>En esta sección
 [Problemas de seguridad](../../extensibility/debugger/security-issues.md) Describe los pasos de seguridad necesarios para depurar un programa.

 [Iniciar un programa](../../extensibility/debugger/launching-a-program.md) Proporciona instrucciones paso a paso sobre cómo especificar un DE, que llama al sistema operativo para iniciar el programa.

 [Adjuntar directamente a un programa](../../extensibility/debugger/attaching-directly-to-a-program.md) Describe el proceso utilizado para depurar un programa en un proceso que ya se está ejecutando.

 Enviar eventos de [inicio después](../../extensibility/debugger/sending-startup-events-after-a-launch.md) de un lanzamiento Enumera los eventos que tienen lugar una vez que la DE se adjunta al programa, hasta que el programa está en su punto de entrada principal y está listo para la depuración.

 [Control de ejecución](../../extensibility/debugger/control-of-execution.md) Explica cómo el DE normalmente envía un evento de punto de entrada, un evento load-complete o un evento de detención, dependiendo de las circunstancias.

 [Enlazar puntos de interrupción](../../extensibility/debugger/binding-breakpoints.md) Describe cómo, si el usuario establece un punto de interrupción, el IDE formula la solicitud y solicita a la sesión de depuración que cree el punto de interrupción.

 [Evaluar expresiones](../../extensibility/debugger/evaluating-expressions.md) Explica cómo se crean las expresiones y qué sucede cuando se evalúa una expresión.

 [Visualizar y ver datos](../../extensibility/debugger/visualizing-and-viewing-data.md) Explica cómo el evaluador de expresiones (EE) admite visualizadores de tipos y visores personalizados.

## <a name="related-sections"></a>Secciones relacionadas
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md) Describe los principales conceptos arquitectónicos de depuración.

 [Componentes del depurador](../../extensibility/debugger/debugger-components.md) Proporciona información general de los componentes de depuración de Visual Studio, que incluyen el DE, EE y el controlador de símbolos (SH).

 [Contextos del depurador](../../extensibility/debugger/debugger-contexts.md) Explica cómo funciona la DE simultáneamente dentro de los contextos de evaluación de código, documentación y expresión. Describe, para cada uno de los tres contextos, la ubicación, la posición o la evaluación relevantes para ella.

## <a name="see-also"></a>Vea también
 [Introducción](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
