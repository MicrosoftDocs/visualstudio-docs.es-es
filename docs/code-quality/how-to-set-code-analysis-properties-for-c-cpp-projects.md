---
title: Procedimiento Establecer las propiedades de análisis de código de proyectos de C/C++
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.native
- VC.Project.VCCLCompilerTool.EnablePrefast
- VC.Project.VCFxCopTool.EnablePREfast
- VC.Project.VCFxCopTool.IgnoreGeneratedCode
helpviewer_keywords:
- properties, C/C++ Code Analysis
- properties, Code Analysis
- code analysis properties
- C/C++ code analysis properties
ms.assetid: 7af52097-6d44-4785-9b9f-43b7a7d447d7
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 4c27300244998765d13d485d617c17c5032bad7b
ms.sourcegitcommit: e95dd8cedcd180e0bce6a75c86cf861757918290
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2019
ms.locfileid: "72163046"
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>Procedimiento Establecer las propiedades de análisis de código de proyectos de C/C++

Puede configurar las reglas que utiliza la herramienta de análisis de código para analizar el código en cada configuración del proyecto. Además, puede dirigir el análisis de código para suprimir las advertencias del código generado y agregado al proyecto mediante una herramienta de terceros.

## <a name="code-analysis-property-page"></a>Página de propiedades análisis de código

La página de propiedades **análisis de código** contiene todas las opciones de configuración de análisis de código para un proyecto de MSBuild. Para abrir la página de propiedades análisis de código de un proyecto de **Explorador de soluciones**, haga clic con el botón secundario en el proyecto y, a continuación, haga clic en **propiedades**. A continuación, expanda **propiedades de configuración** y seleccione la pestaña **análisis de código** .

## <a name="project-configuration-and-platform"></a>Configuración y plataforma del proyecto

La lista de **configuración** y la lista de **plataformas** de la parte superior de la ventana le permiten aplicar una configuración de análisis de código diferente a distintas combinaciones de plataforma y configuración de proyecto. Por ejemplo, puede dirigir el análisis de código para aplicar un conjunto de reglas al proyecto para las compilaciones de depuración y un conjunto diferente para las compilaciones de versión.

## <a name="enabling-code-analysis"></a>Habilitar el análisis de código

Puede habilitar el análisis de código para el proyecto; para ello, alterne las opciones **Habilitar análisis de código de Microsoft** y **habilitar Clang** y, después, configure si se ejecuta en la compilación seleccionando **Habilitar análisis de código al compilar**. En combinación con la lista de **configuración** , puede, por ejemplo, decidir deshabilitar el análisis de código para las compilaciones de depuración y habilitarlo para las compilaciones de versión.

El análisis de código está diseñado para ayudarle a mejorar la calidad del código y evitar errores comunes. Por lo tanto, considere detenidamente si desea deshabilitar el análisis de código. Normalmente es mejor deshabilitar conjuntos de reglas, reglas individuales o comprobaciones individuales que no desea que se apliquen al proyecto.

## <a name="cmake-configuration"></a>Configuración de CMake

En los proyectos de CMake, cambie el valor de las claves `enableMicrosoftCodeAnalysis` y `enableClangTidyCodeAnalysis` dentro de `CMakeSettings.json` para habilitar o deshabilitar el análisis de código. Consulte [uso de Clang en Visual Studio](../code-quality/clang-tidy.md) para obtener más información.

## <a name="see-also"></a>Vea también

- [Analizar la calidad del código administrado](../code-quality/code-analysis-for-managed-code-overview.md)
- [Análisis de código para advertencias de C/C++](../code-quality/code-analysis-for-c-cpp-warnings.md)
- [Conjuntos de reglas C++ para el código](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [Usar Clang-ordenado](../code-quality/clang-tidy.md)