---
title: Tareas de depuración | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8a1d2ae4b05398daa7c42be441cebecb304bf956
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2018
ms.locfileid: "39204172"
---
# <a name="debug-tasks"></a>Tareas de depuración
Para depurar un programa, debe iniciarse y un motor de depuración (DE) debe estar asociado a él, o bien la DE debe asociarse a un programa iniciado anteriormente. Una vez conectado, la DE debe generar ciertos eventos de inicio. En respuesta, el paquete de depuración intenta enlazar los puntos de interrupción establecidos en el IDE. Cuando el programa alcanza un punto de interrupción enlazado, se detiene y espera a que la entrada del usuario.  
  
## <a name="in-this-section"></a>En esta sección  
 [Problemas de seguridad](../../extensibility/debugger/security-issues.md)  
 Describe los pasos de seguridad que son necesarios para depurar un programa.  
  
 [Iniciar un programa](../../extensibility/debugger/launching-a-program.md)  
 Proporciona instrucciones paso a paso sobre cómo especificar una DE, que llama el sistema operativo para iniciar el programa.  
  
 [Asociar directamente a un programa](../../extensibility/debugger/attaching-directly-to-a-program.md)  
 Describe el proceso que se puede utilizado para depurar un programa en un proceso que ya se está ejecutando.  
  
 [Enviar eventos de inicio después de un lanzamiento](../../extensibility/debugger/sending-startup-events-after-a-launch.md)  
 Muestra los eventos que tienen lugar una vez que la DE que está asociada al programa, hasta que el programa se encuentra en su punto de entrada principal y está listo para la depuración.  
  
 [Control de ejecución](../../extensibility/debugger/control-of-execution.md)  
 Explica cómo la DE normalmente envía un evento de punto de entrada, un evento de finalización de carga o un evento de detención, dependiendo de las circunstancias.  
  
 [Enlazar los puntos de interrupción](../../extensibility/debugger/binding-breakpoints.md)  
 Describe cómo, si el usuario establece un punto de interrupción, el IDE formule la solicitud y solicita la sesión de depuración para crear el punto de interrupción.  
  
 [Evaluar expresiones](../../extensibility/debugger/evaluating-expressions.md)  
 Explica cómo se crean expresiones y qué ocurre cuando se evalúa una expresión.  
  
 [Visualizar y ver datos](../../extensibility/debugger/visualizing-and-viewing-data.md)  
 Explica cómo se admiten los visualizadores de tipo y visores personalizados por el evaluador de expresiones (EE).  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)  
 Describe los principales conceptos de arquitectura de depuración.  
  
 [Componentes del depurador](../../extensibility/debugger/debugger-components.md)  
 Proporciona información general de los componentes de depuración de Visual Studio, que incluyen los DE, EE y controlador de símbolos (SH).  
  
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)  
 Explica el funcionamiento de la DE simultáneamente dentro de código, documentación y contextos de evaluación de expresión. Se describen para cada uno de los tres contextos, la ubicación, posición o evaluación pertinente a él.  
  
## <a name="see-also"></a>Vea también  
 [Introducción](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)