---
title: Introducción con extensibilidad del depurador | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 153db8889c78890a31a2e8003e6aa95ed24a02eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738594"
---
# <a name="get-started-with-debugger-extensibility"></a>Introducción a la extensibilidad del depurador
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]Proporciona la información necesaria para crear y personalizar los componentes del depurador usados para depurar programas desde dentro del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno de.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la depuración ha agregado mejoras derivadas de las amplias pruebas de uso realizadas en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuradores anteriores. Puede usar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la depuración para recorrer paso a paso una aplicación de varios lenguajes, o puede implementar la edición inmediata de variables durante la depuración de aplicaciones y soluciones de varios lenguajes.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la depuración se ejecuta fuera de proceso con el programa que se está depurando y, por lo tanto, es menos intrusivo en el espacio de proceso de la aplicación. Por consiguiente, es más fácil escribir componentes que interactúen con el depurador sin que ello afecte al programa de depuración.

 Para usar mejor el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , debe estar familiarizado con los siguientes elementos:

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Entorno de desarrollo integrado (IDE)

- Lenguaje de programación de C++

- COM ATL

## <a name="in-this-section"></a>En esta sección
 [Guía básica para extender el depurador](../../extensibility/debugger/roadmap-for-extending-the-debugger.md) Describe el proceso de implementación de la depuración en el producto, dependiendo del compilador y de su salida.

 [Componentes del depurador](../../extensibility/debugger/debugger-components.md) Proporciona información general sobre los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] componentes de depuración, que incluyen el motor de depuración (de), el evaluador de expresiones (EE) y el controlador de símbolos (SH).

 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md) Describe los conceptos principales de la arquitectura de depuración.

 [Contextos del depurador](../../extensibility/debugger/debugger-contexts.md) Explica cómo el motor DE depuración (DE) funciona simultáneamente dentro del código, la documentación y los contextos de evaluación de expresiones. Describe, para cada uno de los tres contextos, la ubicación, la posición o la evaluación relevantes para él.

 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md) Contiene vínculos a diversas tareas de depuración, como el inicio de un programa y la evaluación de expresiones.
