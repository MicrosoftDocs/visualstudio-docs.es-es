---
title: "T&#233;cnicas de depuraci&#243;n de CRT | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.runtime.debugging"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "CRT, depurar"
  - "depurar [C++], compatibilidad con la depuración de CRT"
  - "depurar [CRT]"
ms.assetid: 9be561f6-14a8-44ff-925d-d911d5b8e6ff
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# T&#233;cnicas de depuraci&#243;n de CRT
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si está depurando un programa que utiliza la biblioteca en tiempo de ejecución de C, estas técnicas de depuración podrían resultar útiles.  
  
## En esta sección  
 [Uso de la biblioteca de depuración CRT](../debugger/crt-debug-library-use.md)  
 Describe las capacidades de depuración suministradas por la biblioteca en tiempo de ejecución de C y proporciona instrucciones para obtener acceso a las herramientas.  
  
 [Macros para los informes](../debugger/macros-for-reporting.md)  
 Proporciona información sobre las macros **\_RPTn** y **\_RPTFn** \(definidas en CRTDBG.H\), que reemplazan el uso de instrucciones `printf` para la depuración.  
  
 [Versiones de depuración de las funciones de asignación del montón](../debugger/debug-versions-of-heap-allocation-functions.md)  
 Analiza las versiones especiales de depuración de las funciones de asignación del montón: cómo asigna CRT las llamadas, las ventajas de llamarlas explícitamente, cómo evitar la conversión, el seguimiento de los tipos independientes de asignaciones en bloques cliente, y el resultado de no definir \_DEBUG.  
  
 [Detalles del montón de depuración de CRT](../debugger/crt-debug-heap-details.md)  
 Proporciona vínculos a temas de administración de memoria y el montón de depuración, tipos de bloques en el montón de depuración, uso del montón de depuración, funciones que informan del estado del montón y seguimiento de solicitudes de asignación en el montón.  
  
 [Creación de funciones de enlace de depuración](../debugger/debug-hook-function-writing.md)  
 Enumera una lista de vínculos a temas como: funciones de asociación a bloques cliente, funciones de enlace de asignación, enlaces de asignación y asignaciones de memoria de CRT, y funciones de enlace para informes.  
  
 [Buscar pérdidas de memoria con la biblioteca de CRT](../debugger/finding-memory-leaks-using-the-crt-library.md)  
 Explica técnicas para detectar y aislar pérdidas de memoria mediante el depurador y la biblioteca en tiempo de ejecución de C.  
  
## Secciones relacionadas  
 [Depuración de código nativo](../debugger/debugging-native-code.md)  
 Trata algunos problemas y técnicas de depuración comunes para las aplicaciones de C y C\+\+.  
  
 [Seguridad del depurador](../debugger/debugger-security.md)  
 Proporciona recomendaciones para una depuración más segura.