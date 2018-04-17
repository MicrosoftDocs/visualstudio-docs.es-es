---
title: Contextos del depurador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8a9310512417ac0e24046a1b7bcc1fd92099fe98
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="debugger-contexts"></a>Contextos de depurador
En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuración, el motor de depuración (Alemania) funciona simultáneamente en varios contextos distintos, como se indica a continuación:  
  
-   El contexto del código, que describe la ubicación actual en el flujo de ejecución de un programa.  
  
-   El contexto de la documentación o la posición, que describe la posición actual dentro de un documento de origen.  
  
-   El contexto de evaluación de expresión, que describe el contexto en la expresión de evaluación llevará a cabo.  
  
## <a name="in-this-section"></a>En esta sección  
 [Contexto del código](../../extensibility/debugger/code-context.md)  
 Describe el contexto del código como una dirección de la secuencia de instrucciones de un programa en las arquitecturas de tiempo de ejecución de hoy en día frente a idiomas no tradicionales, donde código no se puede representar mediante instrucciones, pero algunos otros medios.  
  
 [Posición de documento](../../extensibility/debugger/document-position.md)  
 Define la posición del documento en la depuración de Visual Studio por medio de una abstracción de una posición en un archivo de origen tal como se sabe que el IDE.  
  
 [Contexto de documento](../../extensibility/debugger/document-context.md)  
 Describe el contexto del documento se representa en la depuración de Visual Studio en relación con un archivo de origen. También se explica cómo el controlador de símbolos asigna un contexto de código al contexto de la documentación.  
  
 [Contexto de evaluación de expresiones](../../extensibility/debugger/expression-evaluation-context.md)  
 Proporciona información sobre un contexto de evaluación de expresión en Visual Studio. Por ejemplo, un contexto de evaluación de expresión asociado a un marco de pila proporciona el contexto para evaluar las variables locales, los parámetros de método y los miembros de clase.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Conceptos de depuración](../../extensibility/debugger/debugger-concepts.md)  
 Describe los principales conceptos de arquitectura de depuración.  
  
 [Componentes de depuración](../../extensibility/debugger/debugger-components.md)  
 Proporciona una visión general de los componentes de depuración de Visual Studio, que incluyen el motor de depuración (Alemania), el evaluador de expresiones (EE) y el controlador de símbolos (SH).  
  
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)  
 Contiene vínculos a varias tareas de depuración, como iniciar un programa y la evaluación de expresiones.