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
ms.openlocfilehash: 5a7cf0b150c45037941010bf7e611f4bc21252c7
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "57870420"
---
# <a name="debugging-native-code"></a>Depuración de código nativo
Esta sección trata algunos problemas y técnicas de depuración comunes para aplicaciones nativas. Las técnicas descritas en esta sección son técnicas de alto nivel. Para la forma de usar el depurador de Visual Studio, consulte [primero analicemos el depurador](../debugger/debugger-feature-tour.md)).

## <a name="in-this-section"></a>En esta sección
 [Cómo: depurar código optimizado](../debugger/how-to-debug-optimized-code.md) ofrece sugerencias para depurar código optimizado, específicamente, ¿por qué debería depurar una versión no optimizada del programa, opciones de optimización predeterminadas para configuraciones Debug y Release y sugerencias para buscar errores solo aparecen en código optimizado (al activar la optimización en una configuración de compilación de depuración).

 [DebugBreak y __debugbreak](../debugger/debugbreak-and-debugbreak.md) describe Win32 `DebugBreak` de función y proporciona un vínculo a su tema de referencia en Platform SDK. También describe el `__debugbreak` intrínseco.

 [Las aserciones de C/C ++](../debugger/c-cpp-assertions.md) analiza las instrucciones de aserción, cómo funcionan, las ventajas de utilizarlas (capturar errores lógicos, comprobar resultados de una operación y probar condiciones de error), su interacción con `_DEBUG`y los tipos de aserciones admitidas en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

 [Cómo: depurar código ensamblador en línea](../debugger/how-to-debug-inline-assembly-code.md) proporciona instrucciones breves sobre el uso de la ventana Desensamblado para ver las instrucciones de ensamblado y la ventana registros para ver el contenido del registro y proporciona vínculos a temas relacionados con esas ventanas.

 [Técnicas de depuración de MFC](../debugger/mfc-debugging-techniques.md) proporciona vínculos a técnicas de depuración para programas MFC, como: afxDebugBreak, la macro TRACE, detección de memoria pérdidas en MFC, MFC, aserciones y reducir el tamaño de la depuración de MFC se basa.

 [Técnicas de depuración de CRT](../debugger/crt-debugging-techniques.md) proporciona vínculos a técnicas de depuración para la biblioteca de tiempo de ejecución de C, incluido el uso de la biblioteca de depuración de CRT, macros para informes, diferencias entre malloc y _malloc_dbg, creación de funciones de enlace de depuración y el montón de depuración de CRT.

 [Preguntas más frecuentes de código nativo de depuración](../debugger/debugging-native-code-faqs.md) se ofrecen respuestas a las preguntas más frecuentes sobre la depuración de programas de Visual C++

 [Depurar COM y ActiveX](../debugger/com-and-activex-debugging.md) proporciona información sobre la depuración de aplicaciones COM y ActiveX, incluidas herramientas que puede usar para COM y ActiveX de depuración.

 [Cómo: depurar código insertado](../debugger/how-to-debug-injected-code.md) proporciona orientación para depurar el código que utiliza atributos. Se incluyen instrucciones sobre cómo activar la anotación del código fuente, cómo ver código insertado y cómo ver el código de desensamblado en el punto de ejecución actual.

 [Tutorial: Depurar una aplicación paralela](../debugger/walkthrough-debugging-a-parallel-application.md) se describe cómo usar el **tareas paralelas** y **pilas paralelas** ventanas para depurar una aplicación paralela.

## <a name="related-sections"></a>Secciones relacionadas
 [Tipos de proyecto de Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md) proporciona vínculos a temas que describen cómo depurar los tipos de proyectos nativos creados mediante las plantillas de proyecto de Visual C++.

 [Depurar proyectos DLL](../debugger/debugging-dll-projects.md) proporciona información sobre cómo depurar archivos DLL nativos y administrados.

 [En primer lugar, examine el depurador](../debugger/debugger-feature-tour.md) proporciona vínculos a secciones más amplias de la documentación de depuración. La información incluye novedades del depurador, configuración y preparación, puntos de interrupción, control de excepciones, editar y continuar, depuración de código administrado, depuración de código nativo, depuración de SQL y referencias a la interfaz de usuario.

## <a name="see-also"></a>Vea también

- [Seguridad del depurador](../debugger/debugger-security.md)
- [Depurar en Visual Studio](../debugger/index.md)