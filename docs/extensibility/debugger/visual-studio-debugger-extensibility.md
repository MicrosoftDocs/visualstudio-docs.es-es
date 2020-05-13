---
title: Extensibilidad del depurador de Visual Studio ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff4222b555fab73914776725fc79581f29fa5e53
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712508"
---
# <a name="visual-studio-debugger-extensibility"></a>Extensibilidad del depurador de Visual Studio
Visual Studio incluye un depurador de código fuente totalmente interactivo, que proporciona una herramienta eficaz y fácil de usar para realizar el seguimiento de errores en el programa. El depurador tiene compatibilidad completa con Visual Basic, C, C/C++ y JavaScript. Sin embargo, con el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], que está disponible en el Centro de descarga de [Microsoft](https://www.microsoft.com/download/details.aspx?id=21835), otros lenguajes de programación se pueden admitir en el depurador con las mismas características enriquecidas.

 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurador es el front-end común (es decir, la interfaz de usuario) para los componentes de depuración que, a su vez, son específicos del idioma que se está depurando. Para los nuevos idiomas, todo lo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que es necesario para la compatibilidad con el depurador es crear los componentes back-end necesarios, como un motor de depuración (DE). Este punto es [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] donde entra el entrar.

 Incluye [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] una referencia completa [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a todos los elementos necesarios para crear una nueva DE. Además, hay ejemplos y tutoriales que le ayudarán a empezar.

 Para obtener una muestra completa de un sistema de proyecto de lenguaje con compatibilidad con depuración, consulte el [ejemplo IronPython](https://www.microsoft.com/download/details.aspx?id=55984).

 En las secciones siguientes se describe [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]cómo ampliar el depurador mediante el archivo .

## <a name="in-this-section"></a>En esta sección
 [Empezar](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) Describe lo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que ofrece la depuración y cómo instalar el SDK.

 Crear un motor de [depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md) Documenta el proceso DE personalizado, desde la preparación del programa para un DE hasta la desasociación del DE.

 [Escribir un evaluador](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) de expresiones CLR Explica si debe escribir un evaluador de expresiones.

 Elija una estrategia de [implementación del motor](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) de depuración Describe cómo implementar su DE.

 [Referencia](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) Documenta [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la API de depuración.

 [Muestras](../../extensibility/debugger/visual-studio-debugging-samples.md) Contiene vínculos a un ejemplo de evaluador de expresiones de Common Language Runtime y un ejemplo de motor de depuración.
