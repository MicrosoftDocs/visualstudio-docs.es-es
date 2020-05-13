---
title: Introducción a la extensibilidad del depurador ( Debugger Extensibility ) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738594"
---
# <a name="get-started-with-debugger-extensibility"></a>Comience con la extensibilidad del depurador
Proporciona [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] la información que necesita para crear y personalizar los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] componentes del depurador que se usan para depurar programas desde el entorno.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]depuración ha agregado mejoras derivadas de las extensas pruebas de usabilidad realizadas en depuradores anteriores. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Puede usar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la depuración para recorrer paso a paso una aplicación en varios idiomas, o puede implementar la edición sobre la marcha de variables durante la depuración de aplicaciones y soluciones multilenguaje.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]la depuración se ejecuta fuera de proceso con el programa que se está depurando y, por lo tanto, es menos intrusiva en el espacio de proceso de la aplicación. Por lo tanto, es más fácil escribir componentes que interactúan con el depurador sin afectar al programa de depuración.

 Para utilizar [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]mejor el , debe estar familiarizado con los siguientes elementos:

- El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno de desarrollo integrado (IDE)

- El lenguaje de programación C++

- ATL COM

## <a name="in-this-section"></a>En esta sección
 [Hoja de ruta para ampliar el depurador](../../extensibility/debugger/roadmap-for-extending-the-debugger.md) Describe el proceso de implementación de la depuración en el producto, según el compilador y su salida.

 [Componentes del depurador](../../extensibility/debugger/debugger-components.md) Proporciona información general [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sobre los componentes de depuración, que incluyen el motor de depuración (DE), el evaluador de expresiones (EE) y el controlador de símbolos (SH).

 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md) Describe los principales conceptos arquitectónicos de depuración.

 [Contextos del depurador](../../extensibility/debugger/debugger-contexts.md) Explica cómo funciona el motor de depuración (DE) simultáneamente dentro de los contextos de evaluación de código, documentación y expresión. Describe, para cada uno de los tres contextos, la ubicación, la posición o la evaluación relevantes para ella.

 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md) Contiene vínculos a varias tareas de depuración, como iniciar un programa y evaluar expresiones.
