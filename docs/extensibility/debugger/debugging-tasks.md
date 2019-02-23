---
title: Tareas de depuración | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 299db84fb06679bfbf9dff92234c944cbdec6295
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56695211"
---
# <a name="debug-tasks"></a>Tareas de depuración
Para depurar un programa, debe iniciarse y un motor de depuración (DE) debe estar asociado a él, o bien la DE debe asociarse a un programa iniciado anteriormente. Una vez conectado, la DE debe generar ciertos eventos de inicio. En respuesta, el paquete de depuración intenta enlazar los puntos de interrupción establecidos en el IDE. Cuando el programa alcanza un punto de interrupción enlazado, se detiene y espera a que la entrada del usuario.

## <a name="in-this-section"></a>En esta sección
 [Problemas de seguridad](../../extensibility/debugger/security-issues.md) se describen los pasos de seguridad que son necesarios para depurar un programa.

 [Iniciar un programa](../../extensibility/debugger/launching-a-program.md) proporciona instrucciones paso a paso sobre cómo especificar una DE, que llama el sistema operativo para iniciar el programa.

 [Asociar directamente a un programa](../../extensibility/debugger/attaching-directly-to-a-program.md) describe el proceso que se puede utilizado para depurar un programa en un proceso que ya se está ejecutando.

 [Enviar eventos de inicio después de un lanzamiento](../../extensibility/debugger/sending-startup-events-after-a-launch.md) muestra los eventos que tienen lugar una vez que la DE que está asociada al programa, hasta que el programa se encuentra en su punto de entrada principal y está listo para la depuración.

 [Control de ejecución](../../extensibility/debugger/control-of-execution.md) explica cómo la DE normalmente envía un evento de punto de entrada, un evento de finalización de carga o un evento de detención, dependiendo de las circunstancias.

 [Enlazar los puntos de interrupción](../../extensibility/debugger/binding-breakpoints.md) describe cómo, si el usuario establece un punto de interrupción, el IDE formule la solicitud y solicita la sesión de depuración para crear el punto de interrupción.

 [Evaluar expresiones](../../extensibility/debugger/evaluating-expressions.md) explica cómo se crean expresiones y qué ocurre cuando se evalúa una expresión.

 [Visualizar y ver datos](../../extensibility/debugger/visualizing-and-viewing-data.md) explica cómo se admiten los visualizadores de tipo y visores personalizados por el evaluador de expresiones (EE).

## <a name="related-sections"></a>Secciones relacionadas
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md) describe los principales conceptos de arquitectura de depuración.

 [Componentes del depurador](../../extensibility/debugger/debugger-components.md) proporciona información general sobre la depuración de componentes, que se incluyen los DE, EE y controlador de símbolos (SH) de Visual Studio.

 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md) explica el funcionamiento de la DE simultáneamente dentro de los contextos de evaluación de expresión, documentación y código. Se describen para cada uno de los tres contextos, la ubicación, posición o evaluación pertinente a él.

## <a name="see-also"></a>Vea también
 [Introducción](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)