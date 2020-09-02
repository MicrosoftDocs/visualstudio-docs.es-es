---
title: Contextos del depurador | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56825fe299147e60c5ed9dfcefa491a427ab59e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738974"
---
# <a name="debugger-contexts"></a>Contextos del depurador
En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la depuración, el motor de depuración (de) funciona simultáneamente en varios contextos distintos, como se indica a continuación:

- Contexto de código, que describe la ubicación actual en la secuencia de ejecución de un programa.

- Contexto o posición de la documentación, que describe la posición actual dentro de un documento de origen.

- Contexto de evaluación de la expresión, que describe el contexto en el que tendrá lugar la evaluación de expresiones.

## <a name="in-this-section"></a>En esta sección
 [Contexto de código](../../extensibility/debugger/code-context.md) Describe el contexto de código como una dirección en el flujo de instrucciones de un programa en las arquitecturas en tiempo de ejecución de hoy en comparación con los lenguajes no tradicionales, donde el código no se puede representar mediante instrucciones, pero otros medios.

 [Posición del documento](../../extensibility/debugger/document-position.md) Define la posición del documento en la depuración de Visual Studio por medio de una abstracción de una posición en un archivo de código fuente que se conoce en el IDE.

 [Contexto del documento](../../extensibility/debugger/document-context.md) Describe qué contexto de documento representa en la depuración de Visual Studio con respecto a un archivo de código fuente. También describe cómo el controlador de símbolos asigna un contexto de código al contexto de la documentación.

 [Contexto de evaluación de expresiones](../../extensibility/debugger/expression-evaluation-context.md) Proporciona información sobre un contexto de evaluación de expresiones en Visual Studio. Por ejemplo, un contexto de evaluación de expresión asociado a un marco de pila proporciona el contexto para evaluar las variables locales, los parámetros de método y los miembros de clase.

## <a name="related-sections"></a>Secciones relacionadas
 [Conceptos de depuración](../../extensibility/debugger/debugger-concepts.md) Describe los conceptos principales de la arquitectura de depuración.

 [Componentes de depuración](../../extensibility/debugger/debugger-components.md) Proporciona información general sobre los componentes de depuración de Visual Studio, entre los que se incluyen el motor DE depuración (DE), el evaluador DE expresiones (EE) y el controlador de símbolos (SH).

 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md) Contiene vínculos a diversas tareas de depuración, como el inicio de un programa y la evaluación de expresiones.
