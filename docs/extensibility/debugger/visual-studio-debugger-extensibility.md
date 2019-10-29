---
title: Extensibilidad del depurador de Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 58bfec6fa09f6450afb8170d60acad39edacd590
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2019
ms.locfileid: "72982452"
---
# <a name="visual-studio-debugger-extensibility"></a>Extensibilidad del depurador de Visual Studio
Visual Studio incluye un depurador de código fuente completamente interactivo, que proporciona una herramienta eficaz y fácil de usar para realizar un seguimiento de los errores del programa. El depurador es totalmente compatible con Visual Basic C#,, CC++/y JavaScript. Sin embargo, con el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], que está disponible en el [centro de descarga de Microsoft](https://www.microsoft.com/download/details.aspx?id=21835), se pueden admitir otros lenguajes de programación en el depurador con las mismas características enriquecidas.

 El depurador de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] es el front-end común (es decir, la interfaz de usuario) para los componentes de depuración que, a su vez, son específicos del lenguaje que se depura. En el caso de los nuevos idiomas, todo lo que se necesita para la compatibilidad con el depurador de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] es crear los componentes de back-end necesarios, como un motor DE depuración (DE). Este punto es donde entra el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].

 El [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] incluye una referencia completa a todos los elementos [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] necesarios para crear un nuevo DE. Además, hay ejemplos y tutoriales que le ayudarán a empezar.

 Para obtener un ejemplo completo de un sistema de proyectos de lenguaje con compatibilidad para la depuración, consulte el [ejemplo de IronPython](https://www.microsoft.com/download/details.aspx?id=55984).

 En las secciones siguientes se describe cómo extender el depurador mediante el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].

## <a name="in-this-section"></a>En esta sección
 [Introducción](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) Describe qué ofrece [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] las ofertas de depuración y cómo instalar el SDK.

 [Crear un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md) Documenta el proceso personalizado DE, desde preparar el programa para un DE para desasociar DE.

 [Escribir un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) Explica si debe escribir un evaluador de expresiones.

 [Elegir una estrategia de implementación del motor de depuración](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) Describe cómo implementar su DE.

 [Referencia](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) de Documenta la API de depuración de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 [Ejemplos](../../extensibility/debugger/visual-studio-debugging-samples.md) de Contiene vínculos a un ejemplo del evaluador de expresiones Common Language Runtime y un ejemplo del motor de depuración.
