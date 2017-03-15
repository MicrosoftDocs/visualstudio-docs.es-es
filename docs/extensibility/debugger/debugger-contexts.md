---
title: "Contextos de depurador | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "depurar [SDK de depuración] y contextos"
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Contextos de depurador
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de depuración, el motor de depuración \(DE\) funciona simultáneamente en varios contextos distintos, como sigue:  
  
-   El contexto del código, que describe la ubicación actual en un flujo de la ejecución del programa.  
  
-   El contexto o la posición de la documentación, que describen la posición actual dentro de un documento de origen.  
  
-   El contexto de la evaluación de la expresión, que describe el contexto en el que la evaluación de la expresión se realizarán.  
  
## En esta sección  
 [Contexto del código](../../extensibility/debugger/code-context.md)  
 Describe el contexto del código como dirección en una instrucción de programa transmitir en arquitecturas de hoy en tiempo de ejecución en los lenguajes no tradicionales, donde el código no se puede representar mediante instrucciones, pero algún otro medio.  
  
 [Posición del documento](../../extensibility/debugger/document-position.md)  
 Define el documento colocar en la depuración de Visual Studio mediante una abstracción de una posición en un archivo de código fuente como conocido al IDE.  
  
 [Contexto del documento](../../extensibility/debugger/document-context.md)  
 Describe lo que representa el contexto del documento en la depuración de Visual Studio en relación con un archivo de código fuente.  También describe cómo el controlador de símbolos asigna un contexto del código en el contexto de la documentación.  
  
 [Contexto de la evaluación de expresiones](../../extensibility/debugger/expression-evaluation-context.md)  
 Proporciona información sobre un contexto de evaluación de expresiones en Visual Studio.  Por ejemplo, un contexto de evaluación de la expresión asociada con un marco de pila proporciona el contexto para las variables locales, los parámetros de método, y los miembros de clase de evaluación.  
  
## Secciones relacionadas  
 [Conceptos de depuración](../../extensibility/debugger/debugger-concepts.md)  
 Describe los conceptos arquitectónicos de depuración principal.  
  
 [Componentes de depuración](../../extensibility/debugger/debugger-components.md)  
 Proporciona información general sobre los componentes de depuración de Visual Studio, que incluyen el motor de depuración \(DE\), el evaluador de \(EE\) expresiones, y el controlador de símbolos \(SH\).  
  
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)  
 Contiene vínculos a las diferentes tareas de depuración, como iniciar un programa y evaluación de expresiones.