---
title: Contextos de depurador | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a9f75167f45b364757326ddb50ef93edfc37104
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55004375"
---
# <a name="debugger-contexts"></a>Contextos de depurador
En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuración, el motor de depuración (DE) funciona simultáneamente en varios contextos distintos, como sigue:  
  
-   El contexto del código, que describe la ubicación actual en la secuencia de ejecución de un programa.  
  
-   El contexto de la documentación o la posición, que describe la posición actual dentro de un documento de origen.  
  
-   El contexto de evaluación de expresión, que describe el contexto en la expresión de evaluación llevará a cabo.  
  
## <a name="in-this-section"></a>En esta sección  
 [Contexto de código](../../extensibility/debugger/code-context.md)  
 Describe el contexto de código como una dirección en la secuencia de instrucciones de un programa en arquitecturas de tiempo de ejecución de hoy en comparación con los lenguajes no tradicionales, donde código no puede representarse mediante las instrucciones, pero algunos otros medios.  
  
 [Posición del documento](../../extensibility/debugger/document-position.md)  
 Define la posición del documento en la depuración de Visual Studio por medio de una abstracción de una posición en un archivo de origen como sabe que el IDE.  
  
 [Contexto de documento](../../extensibility/debugger/document-context.md)  
 Describe qué contexto de documento se representa en la depuración de Visual Studio en relación con un archivo de origen. También se explica cómo el controlador de símbolos asigna un contexto de código al contexto de la documentación.  
  
 [Contexto de evaluación de expresión](../../extensibility/debugger/expression-evaluation-context.md)  
 Proporciona información sobre un contexto de evaluación de expresión en Visual Studio. Por ejemplo, un contexto de evaluación de expresión asociado a un marco de pila proporciona el contexto para evaluar las variables locales, parámetros de método y los miembros de clase.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Conceptos de depuración](../../extensibility/debugger/debugger-concepts.md)  
 Describe los principales conceptos de arquitectura de depuración.  
  
 [Depurar componentes](../../extensibility/debugger/debugger-components.md)  
 Proporciona información general de los componentes de depuración de Visual Studio, que incluyen el motor de depuración (DE), el evaluador de expresiones (EE) y el controlador de símbolos (SH).  
  
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)  
 Contiene vínculos a diversas tareas de depuración, como iniciar un programa y evaluar expresiones.