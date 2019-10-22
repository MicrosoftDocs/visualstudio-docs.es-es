---
title: Contextos de depurador | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 011999929fd4cb1508bf4958629e622684f35739
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345992"
---
# <a name="debugger-contexts"></a>Contextos de depurador
En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuración, el motor de depuración (DE) funciona simultáneamente en varios contextos distintos, como sigue:

- El contexto del código, que describe la ubicación actual en la secuencia de ejecución de un programa.

- El contexto de la documentación o la posición, que describe la posición actual dentro de un documento de origen.

- El contexto de evaluación de expresión, que describe el contexto en la expresión de evaluación llevará a cabo.

## <a name="in-this-section"></a>En esta sección
 [Contexto de código](../../extensibility/debugger/code-context.md) trata el contexto de código como una dirección en la secuencia de instrucciones de un programa en arquitecturas de tiempo de ejecución de hoy en comparación con los lenguajes no tradicionales, donde código no puede representarse mediante las instrucciones, pero algunos otros medios.

 [Posición de documento](../../extensibility/debugger/document-position.md) define la posición del documento en la depuración de Visual Studio por medio de una abstracción de una posición en un archivo de código fuente como sabe que el IDE.

 [Contexto de documento](../../extensibility/debugger/document-context.md) explica qué contexto de documento se representa en la depuración de Visual Studio en relación con un archivo de origen. También se explica cómo el controlador de símbolos asigna un contexto de código al contexto de la documentación.

 [Contexto de evaluación de expresión](../../extensibility/debugger/expression-evaluation-context.md) proporciona información sobre un contexto de evaluación de expresión en Visual Studio. Por ejemplo, un contexto de evaluación de expresión asociado a un marco de pila proporciona el contexto para evaluar las variables locales, parámetros de método y los miembros de clase.

## <a name="related-sections"></a>Secciones relacionadas
 [Depurar conceptos](../../extensibility/debugger/debugger-concepts.md) describe los principales conceptos de arquitectura de depuración.

 [Depurar componentes](../../extensibility/debugger/debugger-components.md) proporciona información general sobre la depuración de los componentes, que incluyen el motor de depuración (DE), el evaluador de expresiones (EE) y el controlador de símbolos (SH) de Visual Studio.

 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md) contiene vínculos a diversas tareas de depuración, como iniciar un programa y evaluar expresiones.