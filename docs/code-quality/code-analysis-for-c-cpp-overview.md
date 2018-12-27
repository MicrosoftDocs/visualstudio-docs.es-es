---
title: Análisis de código para obtener información general de C/C++
ms.date: 04/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: a1aeb3cea738a08850762083929741c082d7ccb6
ms.sourcegitcommit: 159ed9d4f56cdc1dff2fd19d9dffafe77e46cd4e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2018
ms.locfileid: "53739864"
---
# <a name="code-analysis-for-cc-overview"></a>Análisis de código para información general de C/C ++

La herramienta de análisis de código de C/C ++ proporciona información sobre posibles defectos en el código fuente de C o C++. Entre los errores de codificación más frecuentes notificados por esta herramienta se incluyen saturaciones de búfer, memoria sin inicializar, desreferencias de puntero NULL, y pérdidas de memoria y recursos. La herramienta también puede ejecutar las comprobaciones contra la [C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="ide-integrated-development-environment-integration"></a>Integración del IDE (entorno de desarrollo integrado)

La herramienta de análisis de código está totalmente integrada en el IDE de Visual Studio.

Durante el proceso de compilación, las advertencias generadas para el código fuente aparecen en la lista de errores. Puede navegar al código fuente que causó la advertencia, y puede ver información adicional sobre la causa y las posibles soluciones del problema.

## <a name="command-line-support"></a>Compatibilidad con la línea de comandos

También puede usar la herramienta de análisis desde la línea de comandos, tal como se muestra en el ejemplo siguiente:

```cmd
C:\>cl /analyze Sample.cpp
```

**Visual Studio 2017 versión 15.7 y versiones posterior** puede ejecutar la herramienta desde la línea de comandos con cualquier sistema de compilación incluidos CMake.

## <a name="pragma-support"></a>compatibilidad con #pragma

Puede usar el `#pragma` directiva para tratar advertencias como errores; habilitar o deshabilitar las advertencias y suprimir advertencias de líneas de código individuales. Para obtener más información, vea [Cómo: Establecer propiedades de análisis de código para los proyectos de C o C++](how-to-set-code-analysis-properties-for-c-cpp-projects.md).

## <a name="annotation-support"></a>Compatibilidad con la anotación

Las anotaciones de mejoran la precisión del análisis de código. Las anotaciones proporcionan información adicional sobre condiciones previas y posteriores en los parámetros de función y tipos de valor devuelto. Para obtener más información, vea [Cómo: Especificar información de código adicional mediante __analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)

## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Ejecutar la herramienta de análisis como parte de la directiva de protección

Es posible que desee exigir que todas origen código protecciones cumplan determinadas directivas. En concreto, desea asegurarse de que se ejecuten un análisis como un paso de la compilación local más reciente. Para obtener más información acerca de cómo habilitar una directiva de protección de análisis de código, consulte [creación y uso de directivas análisis de código en el repositorio](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)

## <a name="team-build-integration"></a>Integración de Team Build

Puede usar las características integradas del sistema de compilación para ejecutar la herramienta de análisis de código como un paso de la [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] proceso de compilación. Para obtener más información, consulte [Azure Pipelines](/azure/devops/pipelines/index?view=vsts).

## <a name="see-also"></a>Vea también

- [Inicio rápido: Análisis de código para C/C ++](quick-start-code-analysis-for-c-cpp.md)
- [Tutorial: Analizar el código de C/c ++ en previsión de defectos](walkthrough-analyzing-c-cpp-code-for-defects.md)
- [Análisis de código para advertencias de C/C++](code-analysis-for-c-cpp-warnings.md)
- [Usar los comprobadores de C++ Core Guidelines](using-the-cpp-core-guidelines-checkers.md)
- [Referencia de C++ Core Guidelines Comprobador](code-analysis-for-cpp-corecheck.md)
- [Usar conjuntos de reglas para especificar las reglas C++ que se van a ejecutar](using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [Analizar la calidad del controlador mediante herramientas de análisis de código](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)
- [Análisis de código para advertencias de controladores](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)
