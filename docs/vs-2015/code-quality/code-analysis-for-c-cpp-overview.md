---
title: Análisis de código para obtener información general de C/C++ | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: overview
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
caps.latest.revision: 27
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: bc84b3f89aa819755a689a0798aea7fbb8147510
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54805653"
---
# <a name="code-analysis-for-cc-overview"></a>Análisis de código para obtener información general de C/C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La herramienta Análisis de código de C/C++ proporciona a los desarrolladores información sobre posibles defectos en su código fuente de C/C++. Entre los errores de codificación más comunes detectados por esta herramienta, destacan las saturaciones de búfer, los casos de memoria no inicializada, la desreferenciación del puntero NULL, así como las pérdidas de memoria y recursos.  
  
## <a name="ide-integrated-development-environment-integration"></a>Integración del entorno de desarrollo integrado (IDE)  
 Para que a los desarrolladores les resulte natural usar la herramienta de análisis, esta se ha integrado por completo en el IDE de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Durante el proceso de compilación, las advertencias generadas para el código fuente aparecen en la lista de errores. Puede navegar al código fuente que causó la advertencia y ver información adicional sobre la causa y las posibles soluciones del problema.  
  
## <a name="pragma-support"></a>Compatibilidad con #pragma  
 Los desarrolladores pueden usar la directiva `#pragma` para tratar advertencias como errores, habilitar o deshabilitar advertencias y suprimir advertencias de líneas de código individuales. Para obtener más información, vea [Cómo: Habilitar y deshabilitar advertencias específicas de análisis de código de C/C++](http://msdn.microsoft.com/910b8518-71f1-4b2e-b012-70647795642a).  
  
## <a name="annotation-support"></a>Compatibilidad con la anotación  
 Las anotaciones mejoran la precisión del análisis de código. Las anotaciones proporcionan información adicional sobre las condiciones previas y posteriores en los parámetros de función y los tipos de valor devuelto. Para obtener más información, vea [Cómo: Especificar información de código adicional mediante __analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)  
  
## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Ejecución de la herramienta de análisis como parte de la directiva de inserción en el repositorio  
 Puede que sea necesario exigir que todas las inserciones en el repositorio de código fuente cumplan determinadas directivas. En concreto, le conviene asegurarse de que se ejecutó un análisis como un paso de la compilación local más reciente. Para más información sobre cómo habilitar una directiva de inserción en el repositorio con análisis de código, vea [Creación y uso de directivas de inserción en el repositorio con análisis de código](../code-quality/creating-and-using-code-analysis-check-in-policies.md).  
  
## <a name="team-build-integration"></a>Integración de Team Build  
 Puede usar las características integradas del sistema de compilación para ejecutar la herramienta de análisis como parte del proceso de compilación de [!INCLUDE[esprtfs](../includes/esprtfs-md.md)]. Para obtener más información, consulte [Compilar la aplicación](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692).  
  
## <a name="command-line-support"></a>Compatibilidad con la línea de comandos  
 Además de la integración completa en el entorno de desarrollo, los desarrolladores también pueden usar la herramienta de análisis desde la línea de comandos, como se muestra en este ejemplo:  
  
 `C:\>cl /analyze Sample.cpp`
