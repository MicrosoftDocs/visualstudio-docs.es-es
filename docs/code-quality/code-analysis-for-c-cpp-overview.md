---
title: "An&#225;lisis de c&#243;digo para obtener informaci&#243;n general de C/C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "#pragma (directivas), análisis de código"
  - "anotaciones, análisis de código"
  - "integración de compilación, análisis de código"
  - "C, análisis de código"
  - "análisis de código C/C++"
  - "C++, análisis de código"
  - "directivas de protección, análisis de código"
  - "herramienta de análisis de código"
  - "análisis de código, C/C++"
  - "línea de comandos, análisis de código"
  - "IDE, análisis de código"
  - "pragma (directiva), análisis de código"
ms.assetid: 81f0c9e8-f471-4de5-aac4-99db336a8809
caps.latest.revision: 25
caps.handback.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# An&#225;lisis de c&#243;digo para obtener informaci&#243;n general de C/C++
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La herramienta Análisis de código de C\/C\+\+ proporciona a los desarrolladores información sobre posibles defectos en su código fuente de C\/C\+\+.  Entre los errores de codificación más comunes detectados por esta herramienta, destacan las saturaciones de búfer, los casos de memoria no inicializada, la desreferenciación del puntero NULL, así como las pérdidas de memoria y recursos.  
  
## Integración del entorno de desarrollo integrado \(IDE\)  
 La herramienta de análisis se encuentra totalmente integrada en el IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para que a los desarrolladores les resulte natural utilizarla.  Durante el proceso de compilación, cualquier advertencia relativa al código fuente aparecerá en la Lista de errores.  Puede navegar hasta el código fuente que produjo la advertencia y ver la información adicional sobre la causa y las posibles soluciones del problema.  
  
## Compatibilidad con \#pragma  
 Los desarrolladores de software pueden utilizar la directiva `#pragma` para tratar las advertencias como errores; habilite o deshabilite las advertencias y suprima las advertencias para líneas individuales de código.  Para obtener más información, vea [How to: Enable and Disable Code Analysis for Specific C\/C\+\+ Warnings](http://msdn.microsoft.com/es-es/910b8518-71f1-4b2e-b012-70647795642a).  
  
## Compatibilidad con las anotaciones  
 Las anotaciones mejoran la exactitud del análisis de código.  Las anotaciones proporcionan información adicional sobre condiciones previas y posteriores en los parámetros de función y en los tipos de valor devueltos.  Para obtener más información, vea [Cómo: Especificar información de código adicional mediante \_\_analysis\_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)  
  
## Ejecutar la herramienta de análisis como parte de las directivas de protección  
 Puede ser necesario exigir que todas las protecciones del código fuente cumplan determinadas directivas.  En especial conviene asegurarse de que el análisis se ejecutó como un paso de la compilación local más reciente.  Para obtener más información sobre cómo habilitar una directiva de protección de análisis de código, vea [Crear y usar directivas de protección del análisis de código](../code-quality/creating-and-using-code-analysis-check-in-policies.md)  
  
## Integración de Team Build  
 Puede utilizar las características integradas del sistema de generación para ejecutar la herramienta de análisis de código como parte del proceso de compilación de [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)].  Para obtener más información, vea [Compilar la aplicación](../Topic/Build%20the%20application.md).  
  
## Compatibilidad con la línea de comandos  
 Aparte de la integración total en el entorno de desarrollo, los desarrolladores pueden utilizar la herramienta de análisis desde la línea de comandos, como se indica en el ejemplo siguiente.  
  
 `C:\>cl /analyze Sample.cpp`