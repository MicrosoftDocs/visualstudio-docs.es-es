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
ms.openlocfilehash: 4184ae40a91e05b1110aed8d3e9b9c9edc64a06d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321474"
---
# <a name="visual-studio-debugger-extensibility"></a>Extensibilidad del depurador de Visual Studio
Visual Studio incluye a un depurador de código fuente totalmente interactivas, que proporciona una herramienta eficaz y fácil de usar para localizar errores en el programa. El depurador tiene compatibilidad completa con Visual Basic, C#, C/C++ y JavaScript. Sin embargo, con el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], que se disponibles desde el [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=214453), pueden admitir otros lenguajes de programación en el depurador con las mismas características enriquecidas.

 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurador es el front-end común (es decir, la interfaz de usuario) para los componentes de depuración que son, a su vez, específica del lenguaje que se está depurando. Para nuevos idiomas, todo lo necesario para admitir por los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurador consiste en crear los componentes necesarios de back-end, por ejemplo, un motor de depuración (DE). Este punto es donde el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] entra en juego.

 El [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] incluye una referencia completa a todos los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] elementos necesarios para crear un DE nuevo. Además, hay ejemplos y tutoriales que le ayudarán a comenzar.

 Para obtener un ejemplo completo de un sistema de proyectos de lenguaje con compatibilidad con la depuración, vea el [ejemplo de IronPython](https://www.microsoft.com/download/details.aspx?id=55984).

 Las secciones siguientes describen cómo ampliar el depurador mediante el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].

## <a name="in-this-section"></a>En esta sección
 [Introducción a](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) describe qué [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ofertas y cómo instalar el SDK de depuración.

 [Crear un motor de depuración](../../extensibility/debugger/creating-a-custom-debug-engine.md) documenta el proceso DE personalizado, desde la preparación de su programa para un DE para separar la DE.

 [Escribir un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) explica si debe escribir un evaluador de expresiones.

 [Elegir una estrategia de implementación del motor de depuración](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) se explica cómo implementar su DE.

 [Referencia](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) documentos la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] API de depuración.

 [Ejemplos de](../../extensibility/debugger/visual-studio-debugging-samples.md) contiene vínculos a un ejemplo de common language runtime expresión del evaluador de expresiones y un ejemplo de motor de depuración.
