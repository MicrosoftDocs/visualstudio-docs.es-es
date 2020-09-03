---
title: Depurar tareas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f4a8a9879bce6d91448bb4f29b842328ab56bb97
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200611"
---
# <a name="debugging-tasks"></a>Tareas de depuración
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Para depurar un programa, debe iniciarse y se debe adjuntar un motor de depuración (DE), o bien se debe adjuntar a un programa iniciado previamente. Una vez conectado, el DE debe generar determinados eventos DE Inicio. En respuesta, el paquete de depuración intenta enlazar los puntos de interrupción establecidos en el IDE. Cuando el programa llega a un punto de interrupción enlazado, se detiene y espera la entrada del usuario.  
  
## <a name="in-this-section"></a>En esta sección  
 [Problemas de seguridad](../../extensibility/debugger/security-issues.md)  
 Describe los pasos de seguridad necesarios para depurar un programa.  
  
 [Inicio de un programa](../../extensibility/debugger/launching-a-program.md)  
 Proporciona instrucciones paso a paso sobre cómo especificar un DE, que llama al sistema operativo para iniciar el programa.  
  
 [Asociación directamente a un programa](../../extensibility/debugger/attaching-directly-to-a-program.md)  
 Describe el proceso que se usa para depurar un programa en un proceso que ya se está ejecutando.  
  
 [Envío de eventos de inicio después de un lanzamiento](../../extensibility/debugger/sending-startup-events-after-a-launch.md)  
 Enumera los eventos que tienen lugar una vez que el DE se adjunta al programa, hasta que el programa se encuentra en su punto de entrada principal y está listo para la depuración.  
  
 [Control de ejecución](../../extensibility/debugger/control-of-execution.md)  
 Explica cómo el DE suele enviar un evento de punto de entrada, un evento de carga completa o un evento de detención, en función de las circunstancias.  
  
 [Enlace de puntos de interrupción](../../extensibility/debugger/binding-breakpoints.md)  
 Describe cómo, si el usuario establece un punto de interrupción, el IDE formula la solicitud y solicita la sesión de depuración para crear el punto de interrupción.  
  
 [Evaluar expresiones](../../extensibility/debugger/evaluating-expressions.md)  
 Explica cómo se crean las expresiones y lo que ocurre cuando se evalúa una expresión.  
  
 [Visualización de datos](../../extensibility/debugger/visualizing-and-viewing-data.md)  
 Explica cómo el evaluador de expresiones (EE) admite visualizadores de tipos y visores personalizados.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)  
 Describe los conceptos principales de la arquitectura de depuración.  
  
 [Componentes del depurador](../../extensibility/debugger/debugger-components.md)  
 Proporciona información general sobre los componentes de depuración de Visual Studio, entre los que se incluyen el DE, el y el controlador DE símbolos (SH).  
  
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)  
 Explica cómo funciona simultáneamente dentro de los contextos de código, documentación y evaluación de expresiones. Describe, para cada uno de los tres contextos, la ubicación, la posición o la evaluación relevantes para él.  
  
## <a name="see-also"></a>Consulte también  
 [Introducción](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
