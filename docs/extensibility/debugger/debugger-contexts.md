---
title: Contextos del depurador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 809f0f50ace62253371d4fd14425bb870a3be633
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
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