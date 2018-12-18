---
title: Depurar código nativo | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging native code
- debugging [C++], native code
- debugging [Visual Studio], native code
- native code, debugging
ms.assetid: d94eee90-7e0d-4cac-88c1-9831030daa5e
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a8c81efece10fe55dc1cf228a3d0c23e7f5a64af
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51730553"
---
# <a name="debugging-native-code"></a>Depuración de código nativo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta sección trata algunos problemas y técnicas de depuración comunes para aplicaciones nativas. Las técnicas descritas en esta sección son técnicas de alto nivel. Para la forma de usar el depurador de Visual Studio, consulte [guía básica del depurador](../debugger/debugger-basics.md).  
  
## <a name="in-this-section"></a>En esta sección  
 [Cómo: Depurar código optimizado](../debugger/how-to-debug-optimized-code.md)  
 Ofrece sugerencias para depurar código optimizado. En concreto, algunas de estas sugerencias son: por qué debería depurar una versión no optimizada del programa, opciones de optimización predeterminadas para configuraciones Debug y Release, y sugerencias para detectar errores de programación que sólo se manifiestan en el código optimizado (al activar la optimización en una configuración de compilación Debug).  
  
 [DebugBreak y __debugbreak](../debugger/debugbreak-and-debugbreak.md)  
 Describe la función `DebugBreak` de Win32 y proporciona un vínculo a su tema de referencia en Platform SDK. También describe el `__debugbreak` intrínseco.  
  
 [Aserciones de C/C++](../debugger/c-cpp-assertions.md)  
 Analiza las instrucciones relativas a las aserciones, cómo funcionan, las ventajas de utilizarlas (capturar errores lógicos, comprobar resultados de una operación y probar situaciones de error), su interacción con `_DEBUG` y cuáles son los tipos de aserciones admitidas en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 [Cómo: Depurar código de ensamblado en línea](../debugger/how-to-debug-inline-assembly-code.md)  
 Proporciona instrucciones breves sobre cómo utilizar la ventana Desensamblado para ver las instrucciones en lenguaje de ensamblado, y la ventana Registros para ver el contenido de los registros; asimismo, proporciona vínculos a temas relacionados con esas ventanas.  
  
 [Técnicas de depuración de MFC](../debugger/mfc-debugging-techniques.md)  
 Proporciona vínculos a técnicas de depuración para programas MFC, tales como: afxDebugBreak, la macro TRACE, detección de pérdidas de memoria en MFC, aserciones MFC y reducción del tamaño de las versiones de depuración MFC.  
  
 [Técnicas de depuración de CRT](../debugger/crt-debugging-techniques.md)  
 Proporciona vínculos a técnicas de depuración para la biblioteca en tiempo de ejecución de C, tales como: uso de la Biblioteca de depuración de CRT, macros para informes, diferencias entre malloc y _malloc_dbg, creación de funciones de enlace de depuración, y la pila de depuración de CRT.  
  
 [Preguntas más frecuentes sobre la depuración de código nativo](../debugger/debugging-native-code-faqs.md)  
 Proporciona respuestas a preguntas frecuentes sobre la depuración de programas escritos en Visual C++.  
  
 [Depurar COM y ActiveX](../debugger/com-and-activex-debugging.md)  
 Proporciona información sobre cómo depurar aplicaciones COM y ActiveX, incluyendo las herramientas que puede utilizar para depuración COM y ActiveX.  
  
 [Cómo: Depurar DLL nativas](../debugger/how-to-debug-native-dlls.md)  
 Explica cómo preparar la depuración de archivos DLL a partir del código nativo.  
  
 [Cómo: Depurar código insertado](../debugger/how-to-debug-injected-code.md)  
 Proporciona orientación para depurar código que utiliza atributos. Se incluyen instrucciones sobre cómo activar la anotación del código fuente, cómo ver código insertado y cómo ver el código de desensamblado en el punto de ejecución actual.  
  
 [Tutorial: Depurar una aplicación paralela](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Describe cómo utilizar el **tareas paralelas** y **pilas paralelas** ventanas para depurar una aplicación paralela.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Tipos de proyecto de Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)  
 Proporciona vínculos a temas que describen cómo depurar los tipos de proyectos nativos creados mediante las plantillas de proyecto de Visual C++.  
  
 [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md)  
 Proporciona vínculos a secciones más amplias de la documentación relativa a la depuración. La información incluye novedades del depurador, configuración y preparación, puntos de interrupción, control de excepciones, editar y continuar, depuración de código administrado, depuración de código nativo, depuración de SQL y referencias a la interfaz de usuario.  
  
## <a name="see-also"></a>Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md)



