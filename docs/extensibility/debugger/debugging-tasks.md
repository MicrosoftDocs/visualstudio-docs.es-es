---
title: "Tareas de depuraci&#243;n | Microsoft Docs"
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
  - "depurar [SDK de depuración], tareas"
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# Tareas de depuraci&#243;n
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Para depurar un programa, debe ser iniciada y un motor de depuración \(DE\) se debe asociar el, o bien el OF debe estar asociada a un programa previamente iniciará.  Una vez que está asociado, el OF debe generar ciertos eventos de inicio.  En respuesta, el paquete de depuración intenta enlazar los puntos de interrupción establecidos en el IDE.  Cuando el programa llega a un punto de interrupción enlazado, se detiene y espera los datos proporcionados por el usuario.  
  
## En esta sección  
 [Problemas de seguridad](../../extensibility/debugger/security-issues.md)  
 Describe los pasos de seguridad necesarios para depurar un programa.  
  
 [Iniciar un programa](../../extensibility/debugger/launching-a-program.md)  
 Proporciona instrucciones paso a paso sobre cómo especificar un OF, que llama al sistema operativo para iniciar el programa.  
  
 [Asociar directamente a un programa](../../extensibility/debugger/attaching-directly-to-a-program.md)  
 Describe el proceso utilizado para depurar un programa en un proceso que está ejecutando.  
  
 [Enviar eventos de inicio después de un lanzamiento](../../extensibility/debugger/sending-startup-events-after-a-launch.md)  
 Se muestran los eventos que tienen lugar el OF se asocian una vez al programa, hasta que el programa está en el punto de entrada principal y está listo para depurar.  
  
 [Control de ejecución](../../extensibility/debugger/control-of-execution.md)  
 Explica cómo el OF envía los eventos de punto, evento carga\-completado, o un evento que detiene, dependiendo de las circunstancias.  
  
 [Enlazar puntos de interrupción](../../extensibility/debugger/binding-breakpoints.md)  
 Describe cómo, si el usuario establece un punto de interrupción, el IDE formulan la solicitud y pide confirmación para la sesión de depuración crear el punto de interrupción.  
  
 [Evaluación de expresiones](../../extensibility/debugger/evaluating-expressions.md)  
 Explica cómo se crean las expresiones y qué ocurre cuando se evalúa una expresión.  
  
 [Visualizar y visualización de datos](../../extensibility/debugger/visualizing-and-viewing-data.md)  
 Explica cómo los visualizadores de tipos y los visores personalizados son compatibles con el evaluador de \(EE\) expresiones.  
  
## Secciones relacionadas  
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)  
 Describe los conceptos arquitectónicos de depuración principal.  
  
 [Componentes del depurador](../../extensibility/debugger/debugger-components.md)  
 Proporciona información general sobre los componentes de depuración de Visual Studio, que incluyen el OF, aa, y el controlador de símbolos \(SH\).  
  
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)  
 Explica cómo el OF funciona simultáneamente en el código, de la documentación, y de contextos de la evaluación de la expresión.  Describe, para cada uno de los tres contextos, location, de la posición, o de evaluación relevante para el.  
  
## Vea también  
 [Introducción](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)