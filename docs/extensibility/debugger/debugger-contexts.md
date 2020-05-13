---
title: Contextos del depurador (Debugger Contexts) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738974"
---
# <a name="debugger-contexts"></a>Contextos del depurador
En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la depuración, el motor de depuración (DE) funciona simultáneamente dentro de varios contextos distintos, como se indica a continuación:

- El contexto de código, que describe la ubicación actual en la secuencia de ejecución de un programa.

- El contexto o la posición de la documentación, que describe la posición actual dentro de un documento de origen.

- El contexto de evaluación de expresiones, que describe el contexto en el que se llevará a cabo la evaluación de expresiones.

## <a name="in-this-section"></a>En esta sección
 [Contexto del código](../../extensibility/debugger/code-context.md) Describe el contexto de código como una dirección en la secuencia de instrucciones de un programa en las arquitecturas de tiempo de ejecución de hoy en día frente a los lenguajes no tradicionales, donde el código puede no estar representado por instrucciones, pero algunos otros medios.

 [Posición del documento](../../extensibility/debugger/document-position.md) Define la posición del documento en la depuración de Visual Studio mediante una abstracción de una posición en un archivo de origen como se conoce al IDE.

 [Contexto del documento](../../extensibility/debugger/document-context.md) Describe qué contexto de documento representa en la depuración de Visual Studio en relación con un archivo de origen. También se describe cómo el controlador de símbolos asigna un contexto de código al contexto de documentación.

 Contexto de [evaluación de expresiones](../../extensibility/debugger/expression-evaluation-context.md) Proporciona información sobre un contexto de evaluación de expresiones en Visual Studio. Por ejemplo, un contexto de evaluación de expresiones asociado a un marco de pila proporciona el contexto para evaluar variables locales, parámetros de método y miembros de clase.

## <a name="related-sections"></a>Secciones relacionadas
 [Conceptos de depuración](../../extensibility/debugger/debugger-concepts.md) Describe los principales conceptos arquitectónicos de depuración.

 [Componentes de depuración](../../extensibility/debugger/debugger-components.md) Proporciona información general de los componentes de depuración de Visual Studio, que incluyen el motor de depuración (DE), el evaluador de expresiones (EE) y el controlador de símbolos (SH).

 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md) Contiene vínculos a varias tareas de depuración, como iniciar un programa y evaluar expresiones.
