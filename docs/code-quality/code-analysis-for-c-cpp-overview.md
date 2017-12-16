---
title: "Análisis de código para información general de C/c ++ | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- annotations, code analysis
- build integration, code analysis
- C/C++ code analysis
- IDE, code analysis
- pragma directive, code analysis
- code analysis, C/C++
- code analysis tool
- command line, code analysis
- C++, code analysis
- check-in policies, code analysis
- '#pragma directives, code analysis'
- C, code analysis
ms.assetid: 81f0c9e8-f471-4de5-aac4-99db336a8809
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f1634250d97e83b21cccd3ada90933fc0806d35f
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2017
---
# <a name="code-analysis-for-cc-overview"></a>Análisis de código para obtener información general de C/C++
La herramienta Análisis de código de C/C++ proporciona a los desarrolladores información sobre posibles defectos en su código fuente de C/C++. Entre los errores de codificación más comunes detectados por esta herramienta, destacan las saturaciones de búfer, los casos de memoria no inicializada, la desreferenciación del puntero NULL, así como las pérdidas de memoria y recursos.  
  
## <a name="ide-integrated-development-environment-integration"></a>Integración del entorno de desarrollo integrado (IDE)  
 Para que resulte natural a los desarrolladores usar la herramienta de análisis, está totalmente integrado en el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE. Durante el proceso de compilación, las advertencias generadas para el código fuente aparecen en la lista de errores. Puede navegar al código fuente que produjo la advertencia, y también puede ver información adicional sobre la causa y las posibles soluciones del problema.  
  
## <a name="pragma-support"></a>compatibilidad con #pragma  
 Los desarrolladores pueden usar el `#pragma` directiva para tratar advertencias como errores; habilitar o deshabilitar las advertencias y suprimir las advertencias para líneas individuales de código. Para obtener más información, consulte [Cómo: establecer propiedades de análisis de código para proyectos de C/C ++ ](how-to-set-code-analysis-properties-for-c-cpp-projects.md).  
  
## <a name="annotation-support"></a>Compatibilidad con las anotaciones  
 Las anotaciones mejoran la exactitud del análisis de código. Las anotaciones proporcionan información adicional sobre condiciones previas y posteriores en los parámetros de función y tipos de valor devuelto. Para obtener más información, vea [Cómo: especificar información de código adicional mediante __analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)  
  
## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Ejecutar la herramienta de análisis como parte de la directiva de protección  
 Puede exigir que todas las origen código protecciones cumplan determinadas directivas. En concreto, desea asegurarse de que se ejecutan un análisis como un paso de la compilación local más reciente. Para obtener más información acerca de cómo habilitar una directiva de protección de análisis de código, vea [crear y usar directivas análisis de código en el repositorio](../code-quality/creating-and-using-code-analysis-check-in-policies.md)  
  
## <a name="team-build-integration"></a>Integración de Team Build  
 Puede utilizar las características integradas del sistema de compilación para ejecutar la herramienta de análisis de código como un paso de la [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] proceso de compilación. Para obtener más información, consulte [Compilar la aplicación](http://msdn.microsoft.com/Library/a971b0f9-7c28-479d-a37b-8fd7e27ef692).  
  
## <a name="command-line-support"></a>Compatibilidad de línea de comandos  
 Además de la integración completa en el entorno de desarrollo, los desarrolladores también pueden utilizar la herramienta de análisis desde la línea de comandos, tal como se muestra en el ejemplo siguiente:  
  
 `C:\>cl /analyze Sample.cpp`