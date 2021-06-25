---
title: Contextos del depurador | Microsoft Docs
description: 'Obtenga información sobre cómo funciona Visual Studio de depuración en contextos distintos: contexto de código, contexto o posición de documentación y contexto de evaluación de expresiones.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5103561a420c3836f60a22790335522a83798966
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903676"
---
# <a name="debugger-contexts"></a>Contextos del depurador
En la depuración, el motor de depuración (DE) funciona simultáneamente dentro de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] varios contextos distintos, como se muestra a continuación:

- Contexto de código, que describe la ubicación actual en el flujo de ejecución de un programa.

- Contexto o posición de documentación, que describe la posición actual dentro de un documento de origen.

- Contexto de evaluación de expresiones, que describe el contexto en el que se llevará a cabo la evaluación de expresiones.

## <a name="in-this-section"></a>En esta sección
 [Contexto de código](../../extensibility/debugger/code-context.md) Describe el contexto de código como una dirección en el flujo de instrucciones de un programa en las arquitecturas en tiempo de ejecución actuales frente a los lenguajes no transaccionales, donde el código puede no representarse mediante instrucciones, pero otros medios.

 [Posición del documento](../../extensibility/debugger/document-position.md) Define la posición del documento Visual Studio depuración mediante una abstracción de una posición en un archivo de código fuente, tal y como conoce el IDE.

 [Contexto del documento](../../extensibility/debugger/document-context.md) Describe qué contexto de documento representa en Visual Studio depuración en relación con un archivo de código fuente. También se describe cómo el controlador de símbolos asigna un contexto de código al contexto de documentación.

 [Contexto de evaluación de expresiones](../../extensibility/debugger/expression-evaluation-context.md) Proporciona información sobre un contexto de evaluación de expresiones en Visual Studio. Por ejemplo, un contexto de evaluación de expresión asociado a un marco de pila proporciona el contexto para evaluar variables locales, parámetros de método y miembros de clase.

## <a name="related-sections"></a>Secciones relacionadas
 [Conceptos de depuración](../../extensibility/debugger/debugger-concepts.md) Describe los principales conceptos de arquitectura de depuración.

 [Depuración de componentes](../../extensibility/debugger/debugger-components.md) Proporciona información general sobre los Visual Studio de depuración, que incluyen el motor de depuración (DE), el evaluador de expresiones (EE) y el controlador de símbolos (SH).

 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md) Contiene vínculos a varias tareas de depuración, como iniciar un programa y evaluar expresiones.
