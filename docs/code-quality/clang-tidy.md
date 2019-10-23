---
title: Uso de Clang-ordenado en Visual Studio
ms.date: 10/04/2019
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.clangtidy
author: frozenpandaman
ms.author: efessler
ms.workload:
- cplusplus
ms.openlocfilehash: e226ac6c83839474b9d8ac6be7fb57e376de4a4f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745993"
---
# <a name="using-clang-tidy-in-visual-studio"></a>Uso de Clang-ordenado en Visual Studio

El análisis de código admite de forma nativa [Clang](https://clang.llvm.org/extra/clang-tidy/) para proyectos de MSBuild y CMake, ya sea mediante conjuntos de herramientas Clang o MSVC. Las comprobaciones Clangbles pueden ejecutarse como parte del análisis de código en segundo plano, aparecen como advertencias en el editor (zigzag) y se muestran en el Lista de errores.

Para usar Clang-ordenado, el componente "C++ Clang Tools para Windows" debe instalarse a través del instalador de Visual Studio.

Clang es la herramienta de análisis predeterminada cuando se usa el conjunto de herramientas LLVM/Clang-cl, disponible tanto en MSBuild como en CMake. Puede configurarlo para que se ejecute junto con o reemplazar la experiencia de análisis de código estándar al usar un conjunto de herramientas de MSVC. Si usa el conjunto de herramientas Clang-cl, el análisis de código de Microsoft no estará disponible.

Clang: se ejecuta después de la compilación correcta; es posible que tenga que resolver los errores de código fuente para obtener resultados Clang.


## <a name="msbuild"></a>MSBuild

Puede configurar Clang-ordenado para que se ejecute como parte del análisis de código y compilar en la página **análisis de código**  > **General** en el ventana Propiedades del proyecto. Las opciones para configurar la herramienta se pueden encontrar en el submenú Clang-ordenado.

Para obtener más información, vea [Cómo: establecer propiedades de análisis de código paraC++ proyectos de C/](../code-quality/how-to-set-code-analysis-properties-for-c-cpp-projects.md).

## <a name="cmake"></a>CMake

En los proyectos de CMake, puede configurar las comprobaciones de Clang en `CMakeSettings.json`. Una vez abierto, haga clic en "editar JSON" en la esquina superior derecha del editor de configuración del proyecto CMake. Se reconocen las claves siguientes:

- `enableMicrosoftCodeAnalysis`: habilita el análisis de código de Microsoft
- `enableClangTidyCodeAnalysis`: habilita el análisis Clang
- `clangTidyChecks`: configuración Clang, especificada como una lista separada por comas, es decir, las comprobaciones para habilitar o deshabilitar

Si no se especifica ninguna de las opciones "habilitar", Visual Studio seleccionará la herramienta de análisis que coincida con el conjunto de herramientas de la plataforma que se usa.

## <a name="warning-display"></a>Pantalla de advertencia

Clang: las ejecuciones no ordenadas provocan que se muestren advertencias en el Lista de errores y como líneas de subrayado en el editor bajo las secciones de código pertinentes. Use la columna "categoría" en el Lista de errores para ordenar y organizar las advertencias de Clang. Puede configurar las advertencias en el editor activando la opción "deshabilitar subrayados de análisis de código" en **herramientas**  > **Opciones**.

## <a name="clang-tidy-configuration"></a>Clang: configuración ordenada

Puede configurar las comprobaciones que Clang se ejecuta dentro de Visual Studio a través de la opción **de comprobaciones Clang** . Esta entrada se proporciona al argumento **--Checks** de la herramienta. Cualquier configuración adicional se puede incluir en los archivos **. Clang** . Consulte la [documentación de Clang en LLVM.org](https://clang.llvm.org/extra/clang-tidy/) para obtener más información.

## <a name="see-also"></a>Vea también

- [Compatibilidad de Clang/LLVM con proyectos de MSBuild](https://aka.ms/cpp/clangmsbuild)
- [Compatibilidad de Clang/LLVM con proyectos de CMake](https://aka.ms/cpp/clangcmake)
