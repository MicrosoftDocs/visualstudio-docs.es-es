---
title: Extensibilidad del depurador de Visual Studio | Microsoft Docs
description: En este artículo se describe la extensibilidad del depurador de Visual Studio y se proporcionan vínculos a artículos sobre la depuración de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dbc44da3f98555774dd62c2b061bbf3a0799926e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057733"
---
# <a name="visual-studio-debugger-extensibility"></a>Extensibilidad del depurador de Visual Studio
Visual Studio incluye un depurador de código fuente completamente interactivo, que proporciona una herramienta eficaz y fácil de usar para realizar un seguimiento de los errores del programa. El depurador es totalmente compatible con Visual Basic, C#, C/C++ y JavaScript. Sin embargo, con el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , que está disponible en el [centro de descarga de Microsoft](https://www.microsoft.com/download/details.aspx?id=21835), se pueden admitir otros lenguajes de programación en el depurador con las mismas características enriquecidas.

 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurador es el front-end común (es decir, la interfaz de usuario) para los componentes de depuración que, a su vez, son específicos del lenguaje que se depura. En el caso de los nuevos lenguajes, todo lo que se necesita para que el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurador lo admita es crear los componentes de back-end necesarios, como un motor de depuración (de). Este punto es donde [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] entra en.

 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]Incluye una referencia completa a todos los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] elementos necesarios para crear un nuevo de. Además, hay ejemplos y tutoriales que le ayudarán a empezar.

 Para obtener un ejemplo completo de un sistema de proyectos de lenguaje con compatibilidad para la depuración, consulte el [ejemplo de IronPython](https://www.microsoft.com/download/details.aspx?id=55984).

 En las secciones siguientes se describe cómo extender el depurador mediante el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .

## <a name="in-this-section"></a>En esta sección
 [Introducción](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) Describe [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] las ofertas de depuración y cómo instalar el SDK.

 [Crear un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md) Documenta el proceso personalizado DE, desde preparar el programa para un DE para desasociar DE.

 [Escribir un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) Explica si debe escribir un evaluador de expresiones.

 [Elegir una estrategia de implementación del motor de depuración](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) Describe cómo implementar su DE.

 [Referencia](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) de Documenta la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] API de depuración.

 [Ejemplos](../../extensibility/debugger/visual-studio-debugging-samples.md) de Contiene vínculos a un ejemplo del evaluador de expresiones Common Language Runtime y un ejemplo del motor de depuración.
