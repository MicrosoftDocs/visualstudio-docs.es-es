---
title: Depurar código nativo | Microsoft Docs
ms.date: 04/11/2017
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging native code
- debugging [C++], native code
- debugging [Visual Studio], native code
- native code, debugging
ms.assetid: d94eee90-7e0d-4cac-88c1-9831030daa5e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: f98b99a31d9215d661879aa7fa52d4b671024496
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738164"
---
# <a name="debugging-native-code"></a>Depuración de código nativo
Esta sección trata algunos problemas y técnicas de depuración comunes para aplicaciones nativas. Las técnicas descritas en esta sección son técnicas de alto nivel. Para ver los mecanismos del uso del depurador de Visual Studio, vea [primer vistazo al depurador](../debugger/debugger-feature-tour.md)).

## <a name="in-this-section"></a>En esta sección
 [Cómo: depurar código optimizado](../debugger/how-to-debug-optimized-code.md) Proporciona sugerencias para depurar código optimizado, en concreto, por qué debe depurar una versión no optimizada del programa, la configuración de optimización predeterminada para las configuraciones de depuración y lanzamiento y sugerencias para buscar errores que solo aparecen en código optimizado (activación optimización en una configuración de compilación de depuración).

 [DebugBreak y __debugbreak](../debugger/debugbreak-and-debugbreak.md) Describe la función `DebugBreak` de Win32 y proporciona un vínculo a su tema de referencia en el SDK de la plataforma. También describe el `__debugbreak` intrínseco.

 [C/C++ aserciones](../debugger/c-cpp-assertions.md) Describe las instrucciones de aserción, cómo funcionan, las ventajas de usarlas (detectar errores lógicos, comprobar los resultados de una operación y probar condiciones de error), su interacción con `_DEBUG` y los tipos de aserciones que se admiten en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

 [Cómo: depurar código de ensamblado alineado](../debugger/how-to-debug-inline-assembly-code.md) Proporciona instrucciones breves sobre cómo usar la ventana Desensamblado para ver las instrucciones de ensamblado y la ventana registros para ver el contenido de los registros y proporciona vínculos a temas relacionados con dichas ventanas.

 [Técnicas de depuración de MFC](../debugger/mfc-debugging-techniques.md) Proporciona vínculos a técnicas de depuración para programas MFC, entre los que se incluyen: afxDebugBreak, la macro TRACE, la detección de pérdidas de memoria en MFC, aserciones MFC y la reducción del tamaño de las compilaciones de depuración de MFC.

 [Técnicas de depuración de CRT](../debugger/crt-debugging-techniques.md) Proporciona vínculos a técnicas de depuración para la biblioteca en tiempo de ejecución de C, incluido el uso de la biblioteca de depuración de CRT, macros para informes, diferencias entre malloc y _ malloc_dbg, escribir funciones de enlace de depuración y el montón de depuración de CRT.

 [Preguntas más frecuentes sobre depuración de código nativo](../debugger/debugging-native-code-faqs.md) Proporciona respuestas a las preguntas más frecuentes sobre la C++ depuración de programas

 [Depuración com y ActiveX](../debugger/com-and-activex-debugging.md) Proporciona información sobre la depuración de aplicaciones COM y ActiveX, incluidas las herramientas que puede usar para la depuración COM y ActiveX.

 [Cómo: depurar código insertado](../debugger/how-to-debug-injected-code.md) Proporciona instrucciones sobre cómo depurar el código que utiliza atributos. Se incluyen instrucciones sobre cómo activar la anotación del código fuente, cómo ver código insertado y cómo ver el código de desensamblado en el punto de ejecución actual.

 [Tutorial: depurar una aplicación paralela](../debugger/walkthrough-debugging-a-parallel-application.md) Describe cómo usar las ventanas de herramientas **tareas paralelas** y **pilas paralelas** para depurar una aplicación paralela.

## <a name="related-sections"></a>Secciones relacionadas
 [Preparar la depuración C++ de proyectos](../debugger/debugging-preparation-visual-cpp-project-types.md) proporciona vínculos a temas que describen cómo depurar los tipos de C++ proyecto nativos creados por las plantillas de proyecto.

 [Depurar proyectos dll](../debugger/debugging-dll-projects.md) Proporciona información sobre cómo depurar archivos DLL nativos y administrados.

 [Primer vistazo al depurador](../debugger/debugger-feature-tour.md) Proporciona vínculos a las secciones más grandes de la documentación de depuración. La información incluye novedades del depurador, configuración y preparación, puntos de interrupción, control de excepciones, editar y continuar, depuración de código administrado, depuración de código nativo, depuración de SQL y referencias a la interfaz de usuario.

## <a name="see-also"></a>Vea también

- [Seguridad del depurador](../debugger/debugger-security.md)
- [Depurar en Visual Studio](../debugger/index.yml)