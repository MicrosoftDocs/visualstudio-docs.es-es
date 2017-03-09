---
title: "Soluci&#243;n de problemas de IntelliSense en proyectos de C++ | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "archivos .ncb"
  - "IntelliSense, solución de problemas en proyectos de C++"
  - "archivos ncb"
  - "solucionar problemas de IntelliSense"
  - "solucionar problemas de Visual C++, IntelliSense"
ms.assetid: 72e4eb39-66d3-403d-8da7-00ed288a1899
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de IntelliSense en proyectos de C++
IntelliSense puede dejar de funcionar en determinadas condiciones.  Los siguientes pasos se utilizan para determinar por qué IntelliSense no funciona para los proyectos en C\+\+.  
  
### Para investigar el error de IntelliSense en proyectos de C\+\+  
  
1.  Asegúrese de que el proyecto de Visual C\+\+ no contiene ningún error de compilación.  
  
    1.  Si se trata de un proyecto de archivos Make, vea [Cómo: Habilitar IntelliSense para proyectos de archivos MAKE](../Topic/How%20to:%20Enable%20IntelliSense%20for%20Makefile%20Projects.md).  
  
2.  Asegúrese de que stdafx.h está en la ruta de acceso de inclusión.  Para obtener más información sobre las rutas de acceso de inclusión en proyectos de Visual C\+\+, vea [\#include \(Directiva\)](/visual-cpp/preprocessor/hash-include-directive-c-cpp) y [\/I \(Directorios de inclusión adicionales\)](/visual-cpp/build/reference/i-additional-include-directories).  
  
## Limitaciones de IntelliSense  
 IntelliSense no funciona en proyectos de C\+\+ en las circunstancias siguientes:  
  
-   El cursor se encuentra en comentario del código.  
  
-   Está escribiendo un literal de cadena  
  
-   El error de sintaxis está sobre el cursor.  
  
-   La solución consiste en la sintaxis de C\+\+ administrado o en la sintaxis anterior de las Extensiones administradas para C\+\+.  
  
-   IntelliSense no es totalmente compatible cuando se hace referencia varias veces un archivo de encabezado mediante la directiva `#include`, y el significado del archivo de encabezado cambia debido a los distintos estados de la macro que se definen con la directiva `#define`.  Es decir, cuando se incluye un archivo de encabezado varias veces y el uso del encabezado cambia según los distintos estados de la macro, IntelliSense no siempre funciona.  
  
## Vea también  
 [Troubleshooting IntelliSense](http://msdn.microsoft.com/es-es/c1b3adb9-0d48-4770-a51e-392ed818c484)   
 [Cómo: Organizar archivos de resultados de proyectos para la compilación](../Topic/How%20to:%20Organize%20Project%20Output%20Files%20for%20Builds.md)