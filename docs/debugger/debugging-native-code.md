---
title: Depuración de código nativo | Microsoft Docs
description: Obtenga información sobre problemas comunes de depuración y técnicas de alto nivel para aplicaciones nativas en Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 4fee3044e4eaa1e7dd3549923082f9b843951b28
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728322"
---
# <a name="debugging-native-code"></a>Depuración de código nativo
Esta sección trata algunos problemas y técnicas de depuración comunes para aplicaciones nativas. Las técnicas descritas en esta sección son técnicas de alto nivel. Para más información sobre cómo usar el depurador de Visual Studio, vea [Primer vistazo al depurador de Visual Studio](../debugger/debugger-feature-tour.md).

## <a name="in-this-section"></a>En esta sección
 [Cómo: Depurar código optimizado](../debugger/how-to-debug-optimized-code.md) Ofrece sugerencias para depurar código optimizado. En concreto, algunas de estas sugerencias son: por qué debería depurar una versión no optimizada del programa, opciones de optimización predeterminadas para configuraciones Debug y Release, y sugerencias para detectar errores de programación que sólo se manifiestan en el código optimizado (al activar la optimización en una configuración de compilación Debug).

 [DebugBreak and __debugbreak](../debugger/debugbreak-and-debugbreak.md) Describe la función `DebugBreak` de Win32 y proporciona un vínculo a su tema de referencia en Platform SDK. También describe el `__debugbreak` intrínseco.

 [Aserciones de C/C++](../debugger/c-cpp-assertions.md) Analiza las instrucciones relativas a las aserciones, cómo funcionan, las ventajas de usarlas (capturar errores lógicos, comprobar resultados de una operación y probar situaciones de error), su interacción con `_DEBUG` y cuáles son los tipos de aserciones admitidas en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

 [Cómo: Depurar código de ensamblado insertado](../debugger/how-to-debug-inline-assembly-code.md) Proporciona instrucciones breves sobre cómo usar la ventana Desensamblado para ver las instrucciones en lenguaje de ensamblado, y la ventana Registros para ver el contenido de los registros; también proporciona vínculos a temas relacionados con esas ventanas.

 [Técnicas de depuración de MFC](../debugger/mfc-debugging-techniques.md) Proporciona vínculos a técnicas de depuración para programas MFC, tales como: afxDebugBreak, la macro TRACE, detección de pérdidas de memoria en MFC, aserciones MFC y reducción del tamaño de las versiones de depuración de MFC.

 [Técnicas de depuración de CRT](../debugger/crt-debugging-techniques.md) Proporciona vínculos a técnicas de depuración para la biblioteca en tiempo de ejecución de C, tales como: uso de la Biblioteca de depuración de CRT, macros para informes, diferencias entre malloc y _malloc_dbg, creación de funciones de enlace de depuración, y la pila de depuración de CRT.

 [Preguntas más frecuentes sobre depuración de código nativo](../debugger/debugging-native-code-faqs.md) Proporciona respuestas a las preguntas más frecuentes sobre la depuración de programas C++.

 [Depuración COM y ActiveX](../debugger/com-and-activex-debugging.md) Proporciona información sobre cómo depurar aplicaciones COM y ActiveX, incluyendo las herramientas que puede utilizar para depuración COM y ActiveX.

 [Cómo: Depurar código insertado](../debugger/how-to-debug-injected-code.md) Proporciona orientación para depurar código que usa atributos. Se incluyen instrucciones sobre cómo activar la anotación del código fuente, cómo ver código insertado y cómo ver el código de desensamblado en el punto de ejecución actual.

 [Tutorial: Depurar una aplicación paralela](../debugger/walkthrough-debugging-a-parallel-application.md) Describe cómo se usan las ventanas de herramientas **Tareas paralelas** y **Pilas paralelas** para depurar una aplicación paralela.

## <a name="related-sections"></a>Secciones relacionadas
 [Preparación para depurar proyectos C++](../debugger/debugging-preparation-visual-cpp-project-types.md) Proporciona vínculos a temas que describen cómo depurar los tipos de proyectos nativos creados mediante las plantillas de proyecto de C++.

 [Depuración de proyectos DLL](../debugger/debugging-dll-projects.md) Proporciona información sobre cómo depurar archivos DLL nativos y administrados.

 [Primer vistazo al depurador](../debugger/debugger-feature-tour.md) Proporciona vínculos a secciones más amplias de la documentación relativa a la depuración. La información incluye novedades del depurador, configuración y preparación, puntos de interrupción, control de excepciones, editar y continuar, depuración de código administrado, depuración de código nativo, depuración de SQL y referencias a la interfaz de usuario.

## <a name="see-also"></a>Vea también

- [Seguridad del depurador](../debugger/debugger-security.md)
- [Depurar en Visual Studio](../debugger/index.yml)