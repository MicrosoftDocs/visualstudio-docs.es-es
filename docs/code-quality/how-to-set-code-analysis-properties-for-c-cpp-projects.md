---
title: Procedimiento Establecer las propiedades de análisis de código de proyectos de C/C++
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 000b731bffe6b2fe02e34e98ebfd3ce8a21f5bd8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53915635"
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>Procedimiento Establecer las propiedades de análisis de código de proyectos de C/C++
Puede configurar las reglas que usa la herramienta de análisis de código para analizar el código en cada configuración del proyecto. Además, puede dirigir el análisis de código para suprimir las advertencias de código generado y agregado al proyecto mediante una herramienta de terceros.

## <a name="code-analysis-property-page"></a>Página de propiedades de análisis de código
 El **análisis de código** página de propiedades contiene todas las opciones de configuración de análisis de código para un proyecto. Para abrir la página de propiedades de análisis de código para un proyecto en **el Explorador de soluciones**, haga clic en el proyecto y, a continuación, haga clic en **propiedades**. A continuación, expanda **propiedades de configuración** y seleccione el **análisis de código** ficha.

## <a name="project-configuration-and-platform"></a>Plataforma y configuración del proyecto
 El **configuración** lista y **plataforma** lista le permite aplicar la configuración de análisis de código diferente para las combinaciones de configuración y plataforma de proyecto diferente. Por ejemplo, puede dirigir compilaciones de análisis de código para un conjunto de reglas se aplican a su proyecto para la depuración y compila un conjunto diferente de versión.

## <a name="enabling-code-analysis"></a>Habilitar análisis de código
 Puede decidir si desea habilitar el análisis de código para el proyecto seleccionando **Habilitar análisis de código para C ++ al compilar**. En combinación con la **configuración** lista, por ejemplo, podría decidir deshabilitar el análisis de código para las compilaciones de depuración y habilitar para la versión de las compilaciones.

 Si el proyecto contiene código administrado, puede decidir si desea habilitar o deshabilitar el análisis de código seleccionando **Habilitar análisis de código al compilar**.

 Análisis de código está diseñado para ayudarle a mejorar la calidad del código y evitar errores habituales. Por lo tanto, considere detenidamente si desea deshabilitar el análisis de código. Es mejor deshabilitar conjuntos de reglas o reglas individuales que no desea que se aplican a su proyecto.

## <a name="generated-code"></a>Código generado
 Con frecuencia, los desarrolladores usar las herramientas para ayudar a desarrollar aplicaciones rápidamente. Estas herramientas pueden generar código que se agrega al proyecto. Es posible que desea ver las infracciones de regla que detecta el análisis de código en el código generado. Sin embargo, es posible que no desee verlas si no desea mantener el código.

 El **Suprimir resultados del código generado** casilla de verificación en la **General** permite seleccionar si desea ver las advertencias de análisis de código desde el código administrado generado por una herramienta de terceros de la página de propiedades .

## <a name="rule-sets"></a>Conjuntos de reglas
 Si el proyecto contiene código administrado, puede seleccionar las reglas para aplicar en un análisis de código seleccionando un conjunto de reglas de la **ejecutar este conjunto de reglas** lista.

## <a name="see-also"></a>Vea también

- [Analizar la calidad del código administrado](../code-quality/code-analysis-for-managed-code-overview.md)
- [Análisis de código para advertencias de C/C++](../code-quality/code-analysis-for-c-cpp-warnings.md)